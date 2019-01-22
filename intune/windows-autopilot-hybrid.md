---
title: 為混合式 Active Directory 聯結裝置設定註冊 - Windows Autopilot
titleSuffix: ''
description: 使用 Windows Autopilot 在 Microsoft Intune 中註冊混合式 Active Directory 聯結裝置。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 12/06/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 8518d8fa-a0de-449d-89b6-8a33fad7b3eb
ms.reviewer: damionw
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.openlocfilehash: f6a78c6612f98903fcbaa9d33b8037c5ea4a3960
ms.sourcegitcommit: 2ff19c09a43c63556d082966727674120b516d10
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2019
ms.locfileid: "54149656"
---
# <a name="deploy-hybrid-azure-ad-joined-devices-using-intune-and-windows-autopilot-preview"></a>使用 Intune 和 Windows Autopilot 部署混合式 Azure AD 聯結裝置 (預覽)
您將可以透過使用 Intune 和 Windows Autopilot 來設定混合式 Azure Active Directory 聯結裝置。 若要執行此作業，請遵循以下步驟。

## <a name="prerequisites"></a>必要條件

- 成功設定[混合式 Azure Active Directory 聯結裝置](https://docs.microsoft.com/azure/active-directory/devices/hybrid-azuread-join-plan)。
    - 確認[使用 Get-msoldevice cmdlet 來驗證註冊]( https://docs.microsoft.com/azure/active-directory/devices/hybrid-azuread-join-managed-domains#verify-the-registration)。

要註冊的裝置，必須：
- 執行 [2018 年 10 月更新](https://blogs.windows.com/windowsexperience/2018/10/02/how-to-get-the-windows-10-october-2018-update/)的 Windows 10。
- 可存取網際網路。
- 可存取您的 Active Directory (不支援 VPN 連線)。
- 完成全新體驗 (OOBE)。

## <a name="set-up-windows-10-automatic-enrollment"></a>設定 Windows 10 自動註冊

1. 登入 [Azure 入口網站](https://portal.azure.com)，然後選取 [Azure Active Directory]。

   ![Azure 入口網站的螢幕擷取畫面](./media/auto-enroll-azure-main.png)

2. 選取 [行動性 (MDM 與 MAM)]。

   ![Azure 入口網站的螢幕擷取畫面](./media/auto-enroll-mdm.png)

3. 選取 [Microsoft Intune]。

   ![Azure 入口網站的螢幕擷取畫面](./media/auto-enroll-intune.png)

4. 確保使用 Intune 和 Windows 部署Azure Active Directory 聯結裝置的使用者，是 [MDM 使用者範圍] 中包含的群組成員。

   ![Azure 入口網站的螢幕擷取畫面](./media/auto-enroll-scope.png)

5. 使用下列 URL 的預設值：
    - **MDM 使用條款 URL**
    - **MDM 探索 URL**
    - **MDM 合規性 URL**
6. 選擇 [儲存]。

## <a name="increase-the-computer-account-limit-in-the-organizational-unit"></a>增加組織單位中的電腦帳戶限制

適用於 Active Directory 的 Intune 連接器，會在內部部署 Active Directory 網域中建立已註冊 Autopilot 的電腦。 裝載 Intune 連接器的電腦，必須在網域中具有建立電腦物件的權限。 

在某些網域中，電腦不具備建立電腦的權限。 此外，網域有套用至所有使用者和電腦的內建限制 (預設值為 10)，它們無法被委派權限來建立電腦物件。 因此，權限必須委派給在組織單位上裝載 Intune 連接器的電腦 (該組織單位即為建立混合式 Azure AD 聯結裝置的位置)。

授與建立電腦權限的組織單位必須符合：
- 在網域加入設定檔中輸入的組織單位
- 或者，如果未選取設定檔，則為您網域的電腦網域名稱。

1. 開啟 [Active Directory 使用者和電腦] (DSA.msc)。

2. 以滑鼠右鍵按一下您將用來建立混合式 Azure AD 聯結電腦的組織單位 > [委派控制]。

    ![委派控制的螢幕擷取畫面](media/windows-autopilot-hybrid/delegate-control.png)

3. 在 [委派控制精靈] 中，選擇 [下一步] > [新增...] > [物件類型]。

4. 在 [物件類型] 對話方塊中，選取 [電腦]，然後選擇 [確定]。

    ![委派控制的螢幕擷取畫面](media/windows-autopilot-hybrid/object-types-computers.png)

5. 在 [選取使用者、電腦或群組] 對話方塊的 [輸入要選取的物件名稱] 方塊中，輸入要安裝連接器的電腦名稱。

    ![委派控制的螢幕擷取畫面](media/windows-autopilot-hybrid/enter-object-names.png)

6. 選擇 [檢查名稱] 以驗證您的輸入，然後選擇 [確定] > [下一步]。

7. 選擇 [建立自訂工作來委派] > [下一步]。

8. 選擇 [僅包含資料夾中的下列物件] 然後選取下列選項：
    - [電腦物件]
    - [在這個資料夾中建立選取的物件]
    - [在這個資料夾中刪除選取的物件]

    ![委派控制的螢幕擷取畫面](media/windows-autopilot-hybrid/only-following-objects.png)
    
9. 選擇 **[下一步]**。

10. 在 [權限] 下，選取 [完全控制] (這會選取所有其他選項) > [下一步] > [完成]。

    ![委派控制的螢幕擷取畫面](media/windows-autopilot-hybrid/full-control.png)

## <a name="install-the-intune-connector"></a>安裝 Intune 連接器

需要在執行 Windows Server 2016 的電腦上安裝適用於 Active Directory 的Intune 連接器，該電腦需要能夠存取網際網路和 Active Directory。 若要增加規模和可用性，或支援多個 Active Directory 網域，您可以在您的環境中安裝多個連接器。 建議您在未執行任何其他 Intune 連接器的伺服器上安裝連接器。

1. 確定您已安裝語言套件並設定，如 [Intune Connector (預覽版) 語言需求](https://docs.microsoft.com/windows/deployment/windows-autopilot/intune-connector) \(機器翻譯\) 所述。
2. 在 [Intune](https://aka.ms/intuneportal) 中，選擇 [裝置註冊] > [Windows 註冊] > [適用於 Active Directory 的 Intune 連接器 (預覽)] > [新增連接器]。 
3. 遵循指示下載連接器。
4. 開啟下載的連接器安裝程式檔案以安裝連接器 (ODJConnectorBootstrapper.exe)。
5. 在安裝結束時，選擇 [設定]。
6. 選擇 [登入]。
7. 輸入使用者全域管理員或 Intune 系統管理員角色的認證。
8. 前往 [裝置註冊] > [Windows 註冊] > [適用於 Active Directory 的 Intune 連接器 (預覽)] 並確認連接狀態為 [使用中]。

### <a name="configure-web-proxy-settings"></a>設定 Web Proxy 設定

如果在您的網路環境中有 Web Proxy，請遵循此處的指示，讓適用於 Active Directory 的 Intune 連接器正確運作：[使用現有的內部部署 Proxy 伺服器](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy-configure-connectors-with-proxy-servers)。


## <a name="create-a-device-group"></a>建立裝置群組
1. 在 [Intune](https://aka.ms/intuneportal) 中，選擇 [群組] > [新增群組]。
2. 在 [群組] 刀鋒視窗中：
    1. 針對 [群組類型]，請選擇 [安全性]。
    2. 輸入**群組名稱**與**群組描述**。
    3. 選擇 [成員資格類型]。
3. 如果針對上述的 [成員資格類型] 選擇 [動態裝置]，則在 [群組] 刀鋒視窗中，請選擇 [動態裝置成員]，然後在 [進階規則] 方塊中輸入下列任意一項代碼。
    - 若要建立包含所有 Autopilot 裝置的群組，請鍵入 `(device.devicePhysicalIDs -any _ -contains "[ZTDId]")`
    - 若建立的群組要包含具有特定訂單識別碼的所有 Autopilot 裝置，請鍵入：`(device.devicePhysicalIds -any _ -eq "[OrderID]:179887111881") `
    - 若建立的群組要包含具有特定採購單識別碼的所有 Autopilot 裝置，請鍵入：`(device.devicePhysicalIds -any _ -eq "[PurchaseOrderId]:76222342342")`
    
    新增 [進階規則] 代碼後，選擇 [儲存]。
5. 選擇 **[建立]**。  

## <a name="register-your-autopilot-devices"></a>註冊您的 Autopilot 裝置

選擇下列其中一個方式來註冊您的 Autopilot 裝置：

### <a name="register-autopilot-devices-that-are-already-enrolled"></a>註冊已註冊的 Autopilot 裝置

1. 藉由 [將所有鎖定裝置轉換為 Autopilot] 設為 [是]，來建立 Autopilot 部署設定檔。 
2. 將設定檔指派至包含您想要自動註冊到 Autopilot 成員的群組。

如需詳細資訊，請參閱[建立 Autopilot 部署設定檔](enrollment-autopilot.md#create-an-autopilot-deployment-profile)。

### <a name="register-autopilot-devices-that-arent-enrolled"></a>註冊尚未註冊的 Autopilot 裝置

如果您的裝置尚未註冊，您可以自行加以註冊。 如需詳細資訊，請參閱[新增裝置](enrollment-autopilot.md#add-devices)。

### <a name="register-devices-from-an-oem"></a>從 OEM 註冊裝置

如果您要購買新的裝置，某些 OEM 可以為您註冊裝置。 如需詳細資訊，請參閱 [Windows Autopilot 頁面](http://aka.ms/WindowsAutopilot)。

註冊 Autopilot 裝置時 (註冊到 Intune 之前)，您會在三個位置中看到這些裝置 (其名稱會設定為其序號)：
- Azure 入口網站 Intune 中的 Autopilot 裝置刀鋒視窗 ([裝置註冊] > [Windows 註冊] > [裝置])。
- Azure 入口網站 Intune 中的 Azure AD 裝置刀鋒視窗 ([裝置] > [Azure AD 裝置])。
- Azure 入口網站 Azure Active Directory 中的 AAD 所有裝置刀鋒視窗 ([裝置] > [所有裝置])。

在註冊 Autopilot 裝置之後，您可於四個位置中看到這些裝置：
- Azure 入口網站 Intune 中的 Autopilot 裝置刀鋒視窗中 ([裝置註冊] > [Windows 註冊] > [裝置])。
- Azure 入口網站 Intune 中的 Azure AD 裝置刀鋒視窗 ([裝置] > [Azure AD 裝置])。
- Azure 入口網站 Azure Active Directory 中的 AAD 所有裝置刀鋒視窗 ([裝置] > [所有裝置])。
- Azure 入口網站 Intune 中的所有裝置刀鋒視窗 ([裝置] > [所有裝置])。

註冊 Autopilot 裝置後，其裝置名稱將變更為裝置的主機名稱。 根據預設，會以 "DESKTOP-" 開頭。




## <a name="create-and-assign-an-autopilot-deployment-profile"></a>建立並指派 AutoPilot 部署設定檔
Autopilot 部署設定檔會用來設定 Autopilot 裝置。

1. 在 [Intune](https://aka.ms/intuneportal) 中，選擇 [裝置註冊] > [Windows 註冊] > [部署設定檔] > [建立設定檔]。
2. 輸入**名稱**和選擇性的**描述**。
3. 針對 [部署模式] 選擇 [使用者驅動]。
4. 在 [聯結 Azure AD 為] 方塊中，選擇 [混合式 Azure AD 聯結 (預覽)]。
5. 選擇 [全新體驗 (OOBE)]、視需要設定選項，然後選擇 [儲存]。
6. 選擇 [建立] 以建立設定檔。 
7. 在設定檔刀鋒視窗中，選擇 [指派]。
8. 選擇 [選取群組] > 在 [選取群組] 刀鋒視窗中，選擇裝置群組 > [選取]。

裝置設定檔狀態大約需要 15 分鐘才能從**未指派**變更為**指派中**，最後變更為**已指派**。

## <a name="turn-on-the-enrollment-status-page-optional"></a>開啟註冊狀態頁面 (選擇性)

1. 在 [Intune](https://aka.ms/intuneportal) 中，選擇 [裝置註冊] > [Windows 註冊] > [註冊狀態頁面 (預覽)]。
2. 在 [註冊狀態頁面] 刀鋒視窗中，選擇 [預設] > [設定]。
3. 針對 [顯示應用程式和設定檔安裝進度]，選擇 [是]。
4. 視需要設定其他選項。
5. 選擇 [儲存]。

## <a name="create-and-assign-a-domain-join-profile"></a>建立並指派網域加入設定檔

1. 在 [Intune](https://aka.ms/intuneportal) 中，選擇 [裝置設定] > [設定檔] > [建立設定檔]。
2. 輸入下列內容：
   - **名稱**：為新的設定檔輸入描述性名稱。
   - **描述**：輸入設定檔的描述。
   - **平台**：選擇 [Windows 10 及更新版本]。
   - **設定檔類型**：選擇 [網域加入 (預覽)]。
3. 選擇 [設定]，並提供 [電腦名稱前置詞]、[網域名稱] 以及 (選擇性) [DN 格式](https://docs.microsoft.com/windows/desktop/ad/object-names-and-identities#distinguished-name)的 [組織單位]。 
4. 選擇 [確定] > [建立]。 會建立設定檔，而且會出現在清單中。
5. 若要指派設定檔，請遵循[指派裝置設定檔](device-profile-assign.md#assign-a-device-profile)下的步驟。 

## <a name="next-steps"></a>後續步驟

在您設定 Windows Autopilot 之後，請了解如何管理這些裝置。 如需詳細資訊，請參閱[什麼是 Microsoft Intune 裝置管理？](device-management.md)

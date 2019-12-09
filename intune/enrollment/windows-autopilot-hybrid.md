---
title: 註冊混合式 Azure AD 聯結裝置 - Windows Autopilot
titleSuffix: ''
description: 使用 Windows Autopilot 在 Microsoft Intune 中註冊混合式 Azure AD 聯結裝置。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 07/01/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 8518d8fa-a0de-449d-89b6-8a33fad7b3eb
ms.reviewer: priyar
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: dc618f2502647ba33a16cff4305b9f4671e05996
ms.sourcegitcommit: fc4b38660129d615068f34ad4b96b900d73f7b53
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/27/2019
ms.locfileid: "74558192"
---
# <a name="deploy-hybrid-azure-ad-joined-devices-by-using-intune-and-windows-autopilot"></a>使用 Intune 和 Windows Autopilot 部署混合式 Azure AD 聯結裝置
您可以使用 Intune 和 Windows Autopilot 來設定混合式 Azure Active Directory (Azure AD) 聯結裝置。 若要這樣做，請遵循本文中的步驟。

## <a name="prerequisites"></a>必要條件

成功設定您的[混合式 Azure AD 聯結裝置](https://docs.microsoft.com/azure/active-directory/devices/hybrid-azuread-join-plan)。 請務必使用 Get-MsolDevice Cmdlet 來[驗證您的裝置註冊](https://docs.microsoft.com/azure/active-directory/devices/hybrid-azuread-join-managed-domains#verify-the-registration)。

要註冊的裝置，必須：
- 執行 Windows 10 v1809 或更新版本。
- 能夠[遵循記載的 Windows Autopilot 網路需求](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-autopilot-requirements#networking-requirements) \(部分機器翻譯\) 來存取網際網路。
- 能夠存取 Active Directory 網域控制站，因此其必須連線至組織的網路 (以在其中解析 AD 網域和 AD 網域控制站的 DNS 記錄，並與網域控制站通訊來驗證使用者。 目前不支援 VPN 連線)。
- 能夠 ping 您嘗試加入之網域的網域控制站。
- 如果使用 Proxy，必須啟用並設定 WPAD Proxy 設定選項。
- 完成全新體驗 (OOBE)。

## <a name="set-up-windows-10-automatic-enrollment"></a>設定 Windows 10 自動註冊

1. 登入 Azure，然後在左窗格中選取 [Azure Active Directory]  。

   ![Azure 入口網站](./media/windows-autopilot-hybrid/auto-enroll-azure-main.png)

1. 選取 [行動性 (MDM 與 MAM)]  。

   ![[Azure Active Directory] 窗格](./media/windows-autopilot-hybrid/auto-enroll-mdm.png)

1. 選取 [Microsoft Intune]  。

   ![[行動性 (MDM 與 MAM)] 窗格](./media/windows-autopilot-hybrid/auto-enroll-intune.png)

1. 確保使用 Intune 和 Windows 部署 Azure AD 聯結裝置的使用者，是 [MDM 使用者範圍]  中包含的群組成員。

   ![[行動性 (MDM 與 MAM)] 的 [設定] 窗格](./media/windows-autopilot-hybrid/auto-enroll-scope.png)

1. 使用 [MDM 使用條款 URL]  、[MDM 探索 URL]  和 [MDM 合規性 URL]  方塊中的預設值，然後選取 [儲存]  。

## <a name="increase-the-computer-account-limit-in-the-organizational-unit"></a>增加組織單位中的電腦帳戶限制

適用於 Active Directory 的 Intune 連接器，會在內部部署 Active Directory 網域中建立已註冊 Autopilot 的電腦。 裝載 Intune 連接器的電腦，必須在網域中具有建立電腦物件的權限。 

在某些網域中，電腦不具備建立電腦的權限。 此外，網域有套用至所有使用者和電腦的內建限制 (預設為 10)，它們無法被委派權限來建立電腦物件。 因此，權限必須委派給在組織單位上裝載 Intune 連接器的電腦 (該組織單位即為建立混合式 Azure AD 聯結裝置的位置)。

授與建立電腦權限的組織單位必須符合：
- 在網域加入設定檔中輸入的組織單位。
- 如果未選取設定檔，則為您網域的電腦網域名稱。

1. 開啟 [Active Directory 使用者和電腦 (DSA.msc)]  。

1. 以滑鼠右鍵按一下您將用來建立混合式 Azure AD 聯結電腦的組織單位，然後選取 [委派控制]  。

    ![[委派控制] 命令](./media/windows-autopilot-hybrid/delegate-control.png)

1. 在 [委派控制精靈]  中，選取 [下一步]   > [新增]   > [物件類型]  。

1. 在 [物件類型]  窗格中，選取 [電腦]  核取方塊，然後選取 [確定]  。

    ![[物件類型] 窗格](./media/windows-autopilot-hybrid/object-types-computers.png)

1. 在 [選取使用者、電腦或群組]  窗格的 [輸入要選取的物件名稱]  方塊中，輸入要安裝連接器的電腦名稱。

    ![[選取使用者、電腦或群組] 窗格](./media/windows-autopilot-hybrid/enter-object-names.png)

1. 選取 [檢查名稱]  以驗證您的輸入，然後依序選取 [確定]  和 [下一步]  。

1. 選取 [建立自訂工作來委派]   > [下一步]  。

1. 選取 [只有在這個資料夾內的下列物件]  核取方塊，然後依序選取 [電腦物件]  、[將選取的物件建立到這個資料夾中]  和 [刪除在這個資料夾中選取的物件]  核取方塊。

    ![[Active Directory 物件類型] 窗格](./media/windows-autopilot-hybrid/only-following-objects.png)
    
1. 選取 [下一步]  。

1. 在 [權限]  下，選取 [完全控制]  核取方塊。  
    此動作會選取所有其他選項。

    ![[權限] 窗格](./media/windows-autopilot-hybrid/full-control.png)

1. 選取 [下一步]  ，然後選取 [完成]  。

## <a name="install-the-intune-connector"></a>安裝 Intune 連接器

適用於 Active Directory 的 Intune 連接器必須安裝在執行 Windows Server 2016 或更新版本的電腦上。 該電腦也必須能夠存取網際網路和您的 Active Directory。 若要增加規模和可用性，或支援多個 Active Directory 網域，您可以在您的環境中安裝多個連接器。 建議在未執行任何其他 Intune 連接器的伺服器上安裝連接器。

1. 在 [Microsoft 端點管理員系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)中，選取 [裝置]   > [Windows]   > [Windows 註冊]   > [適用於 Active Directory 的 Intune 連接器]   > [新增]  。 
2. 遵循指示下載連接器。
3. 開啟下載的連接器安裝程式檔案 *ODJConnectorBootstrapper.exe* 以安裝連接器。
4. 在安裝結束時，選取 [設定]  。
5. 選取 [登入]  。
6. 輸入使用者全域管理員或 Intune 系統管理員角色的認證。  
   使用者帳戶必須具有已指派的 Intune 授權。
7. 移至 [裝置]   > [Windows]   > [Windows 註冊]   > [適用於 Active Directory 的 Intune 連接器]  ，然後確認連線狀態為 [使用中]  。

> [!NOTE]
> 登入連接器之後，該連接器可能需要數分鐘的時間才會顯示在 [Microsoft Endpoint Manager 系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)內。 只有在順利與 Intune 服務通訊時才會顯示。

### <a name="turn-off-ie-enhanced-security-configuration"></a>關閉 IE 增強式安全性設定
根據預設，Windows Server 已開啟 Internet Explorer 增強式安全性設定。 如果您無法登入適用於 Active Directory 的 Intune 連接器，則需針對管理員關閉 IE 增強式安全性設定。 [如何關閉 Internet Explorer 增強式安全性設定](https://blogs.technet.microsoft.com/chenley/2011/03/10/how-to-turn-off-internet-explorer-enhanced-security-configuration) \(英文\)

### <a name="configure-web-proxy-settings"></a>設定 Web Proxy 設定

如果在您的網路環境中有 Web Proxy，請參閱[使用現有的內部部署 Proxy 伺服器](autopilot-hybrid-connector-proxy.md)，確認適用於 Active Directory 的 Intune 連接器正常運作。


## <a name="create-a-device-group"></a>建立裝置群組
1. 在 [Microsoft Endpoint Manager 系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)內，選取 [群組]   > [新增群組]  。

1. 在 [群組]  窗格中，執行下列動作：

    a. 針對 [群組類型]  ，選取 [安全性]  。

    b. 輸入**群組名稱**與**群組描述**。

    c. 選取 [成員資格類型]  。

1. 如果您針對成員資格類型選取了 [動態裝置]  ，請在 [群組]  窗格中選取 [動態裝置成員]  ，然後在 [進階規則]  方塊中執行下列其中一個動作：
    - 若要建立群組來包含您所有的 Autopilot 裝置，請輸入 `(device.devicePhysicalIDs -any _ -contains "[ZTDId]")`。
    - Intune 的 [群組標籤] 欄位會對應至 Azure AD 裝置上的 OrderID 屬性。 若要建立包含具特定群組標籤 (OrderID) 的所有 Autopilot 裝置的群組，您必須輸入：`(device.devicePhysicalIds -any _ -eq "[OrderID]:179887111881")`
    - 若要建立群組來包含具有特定訂購單識別碼的所有 Autopilot 裝置，請輸入 `(device.devicePhysicalIds -any _ -eq "[PurchaseOrderId]:76222342342")`。
    
1. 選取 [儲存]  。

1. 選取 [建立]  。  

## <a name="register-your-autopilot-devices"></a>註冊您的 Autopilot 裝置

選取下列其中一個方式來註冊您的 Autopilot 裝置。

### <a name="register-autopilot-devices-that-are-already-enrolled"></a>註冊已註冊的 Autopilot 裝置

1. 藉由 [將所有鎖定裝置轉換為 Autopilot]  設為 [是]  ，來建立 Autopilot 部署設定檔。 
2. 將設定檔指派給群組，其中包含您想要使用 Autopilot 自動註冊的成員。

如需詳細資訊，請參閱[建立 Autopilot 部署設定檔](enrollment-autopilot.md#create-an-autopilot-deployment-profile)。

### <a name="register-autopilot-devices-that-arent-enrolled"></a>註冊尚未註冊的 Autopilot 裝置

如果您的裝置尚未註冊，您可以自行加以註冊。 如需詳細資訊，請參閱[新增裝置](enrollment-autopilot.md#add-devices)。

### <a name="register-devices-from-an-oem"></a>從 OEM 註冊裝置

如果您要購買新的裝置，某些 OEM 可以為您註冊裝置。 如需詳細資訊，請參閱 [Windows Autopilot 頁面](https://aka.ms/WindowsAutopilot)。

當您的 Autopilot 裝置「已登錄」  但尚未向 Intune 註冊時，這些裝置會顯示在三個位置 (其名稱會設定為其序號)：
- Azure 入口網站 Intune 中的 [Autopilot 裝置]  窗格。 選取 [裝置註冊]   > [Windows 註冊]   > [裝置]  。
- Azure 入口網站 Intune 中的 [Azure AD 裝置]  窗格。 選取 [裝置]   > [Azure AD 裝置]  。
- Azure 入口網站 Azure Active Directory 中的 [Azure AD 所有裝置]  窗格，方式是選取 [裝置]   > [所有裝置]  。

「註冊」  您的 Autopilot 裝置之後，這些裝置會顯示在四個位置：
- Azure 入口網站 Intune 中的 [Autopilot 裝置]  窗格。 選取 [裝置註冊]   > [Windows 註冊]   > [裝置]  。
- Azure 入口網站 Intune 中的 [Azure AD 裝置]  窗格。 選取 [裝置]   > [Azure AD 裝置]  。
- Azure 入口網站 Azure Active Directory 中的 [Azure AD 所有裝置]  窗格。 選取 [裝置]   > [所有裝置]  。
- Azure 入口網站 Intune 中的 [所有裝置]  窗格。 選取 [裝置]   > [所有裝置]  。

註冊您的 Autopilot 裝置之後，其名稱會變成裝置的主機名稱。 根據預設，主機名稱會以 *DESKTOP-* 開頭。


## <a name="create-and-assign-an-autopilot-deployment-profile"></a>建立並指派 AutoPilot 部署設定檔
Autopilot 部署設定檔會用來設定 Autopilot 裝置。

1. 在 [Microsoft 端點管理員系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)中，選取 [裝置]   > [Windows]   > [Windows 註冊]   > [部署設定檔]   > [建立設定檔]  。
2. 在 [基本]  頁面上，輸入**名稱**和選擇性的**描述**。
3. 若您想指派群組中所有的裝置自動轉換至 Autopilot，請將 [將所有目標裝置轉換至 Autopilot]  設為 [是]  。 指派群組中所有屬公司擁有的非 Autopilot 裝置都會向 Autopilot 部署服務註冊。 個人擁有的裝置將不會轉換成 Autopilot。 等候 48 小時讓註冊處理完畢。 當裝置取消註冊並重設時，Autopilot 將會自動註冊它。 在裝置使用此方式註冊完畢後，停用此選項或是移除設定檔指派也不會從 Autopilot 部署服務移除裝置。 您必須改為[直接移除裝置](enrollment-autopilot.md#delete-autopilot-devices)。
4. 選取 [下一步]  。
5. 在 [首次體驗 (OOBE)]  頁面上，針對 [部署模式]  選取 [使用者驅動]  。
6. 在 [加入 Azure AD 成為]  方塊中，選取 [已加入混合式 Azure AD]  。
7. 視需要在 [首次體驗 (OOBE)]  頁面上設定其餘選項。
8. 選取 [下一步]  。
9. 在 [範圍標籤]  頁面上，選取此設定檔的[範圍標籤](../fundamentals/scope-tags.md)。
10. 選取 [下一步]  。
11. 在 [指派]  頁面上，選取 [選取要納入的群組]  > 搜尋並選取裝置群組 > [選取]  。
12. 選取 [下一步]   > [建立]  。

大約需要 15 分鐘才能從 [未指派]  變更為 [指派中]  ，最後變更為 [已指派]  。

## <a name="optional-turn-on-the-enrollment-status-page"></a>(選擇性) 開啟註冊狀態頁面

1. 在 [Microsoft 端點管理員系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)中，選取 [裝置]   > [Windows]   > [Windows 註冊]   > [註冊狀態頁面]  。
1. 在 [註冊狀態頁面]  窗格中，選取 [預設]   > [設定]  。
1. 在 [顯示應用程式和設定檔安裝進度]  方塊中，選取 [是]  。
1. 視需要設定其他選項。
1. 選取 [儲存]  。

## <a name="create-and-assign-a-domain-join-profile"></a>建立並指派網域加入設定檔

1. 在 [Microsoft 端點管理員系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)中，選取 [裝置]   > [組態設定檔]   > [建立設定檔]  。
1. 輸入下列內容：
   - **名稱**：為新的設定檔輸入描述性名稱。
   - **描述**：輸入設定檔的描述。
   - **平台**：選取 [Windows 10 及更新版本]  。
   - **設定檔類型**：選取 [網域加入 (預覽)]  。
1. 選取 [設定]  ，然後提供 [電腦名稱前置詞]  、[網域名稱]  以及 (選擇性) [DN 格式](https://docs.microsoft.com/windows/desktop/ad/object-names-and-identities#distinguished-name)的 [組織單位]  。 
   > [!NOTE]
   > 不要為 [組織單位]  中的值使用引號。
1. 選取 [確定]   > [建立]  。  
    設定檔隨即建立，並顯示在清單中。
1. 若要指派設定檔，請遵循[指派裝置設定檔](../configuration/device-profile-assign.md#assign-a-device-profile)下的步驟，並將設定檔指派到在[建立裝置群組](windows-autopilot-hybrid.md#create-a-device-group)這個步驟使用的相同群組
   - 部署多個網域加入設定檔
   
     a. 建立動態群組，其中包含具有特定 Autopilot 部署設定檔的所有 Autopilot 裝置，然後輸入 (device.enrollmentProfileName -eq "Autopilot Profile Name")。 
     
     b. 使用在[建立及指派 Autopilot 部署設定檔](windows-autopilot-hybrid.md#create-and-assign-an-autopilot-deployment-profile)下建立的設定檔顯示名稱來取代 'Autopilot Profile Name'。 
     
     c. 建立多個 Autopilot 部署設定檔，並將該裝置指派給在這個動態群組中指定的設定檔。

> [!NOTE]
> 適用於混合式 Azure AD Join 的 Windows Autopilot 命名功能不支援 %SERIAL% 等變數，僅支援電腦名稱的前置詞。

## <a name="next-steps"></a>後續步驟

在您設定 Windows Autopilot 之後，請了解如何管理這些裝置。 如需詳細資訊，請參閱[什麼是 Microsoft Intune 裝置管理？](../remote-actions/device-management.md)

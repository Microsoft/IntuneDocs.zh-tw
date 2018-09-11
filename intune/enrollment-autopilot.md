---
title: 使用 Windows AutoPilot 來註冊裝置
titleSuffix: Microsoft Intune
description: 了解如何使用 Windows AutoPilot 來註冊 Windows 10 裝置。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/25/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: a2dc5594-a373-48dc-ba3d-27aff0c3f944
ms.openlocfilehash: 4c268f9061ae624c1f85e386e5633b14334860b7
ms.sourcegitcommit: 4d314df59747800169090b3a870ffbacfab1f5ed
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/30/2018
ms.locfileid: "43313133"
---
# <a name="enroll-windows-devices-by-using-the-windows-autopilot"></a>使用 Windows AutoPilot 來註冊 Windows 裝置
Windows AutoPilot 可簡化裝置佈建。 建置和維護自訂的作業系統映像需要許多時間。 您也可能會花時間將這些自訂的作業系統映像套用至新的裝置，以在送交使用者之前，先將它們做好使用的準備。 使用 Microsoft Intune 和 AutoPilot，您可以將新的裝置提供給使用者而不需要建置、維護及套用自訂作業系統映像至裝置。 當您使用 Intune 來管理 AutoPilot 裝置時，可以在裝置註冊之後管理原則、設定檔、應用程式等。 如需優點、案例和必要條件的概觀，請參閱 [Overview of Windows AutoPilot](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-10-autopilot) (Windows AutoPilot 概觀)。

## <a name="prerequisites"></a>必要條件
- [已啟用 Windows 自動註冊](https://docs.microsoft.com/intune-classic/deploy-use/set-up-windows-device-management-with-microsoft-intune#enable-windows-10-automatic-enrollment)
- [Azure Active Directory Premium 訂用帳戶](https://docs.microsoft.com/azure/active-directory/active-directory-get-started-premium) <!--&#40;[trial subscription](http://go.microsoft.com/fwlink/?LinkID=816845)&#41;-->

## <a name="add-devices"></a>新增裝置

您可以藉由匯入含 Windows AutoPilot 裝置資訊的 CSV 檔案來新增它們。

1. 在 [Azure 入口網站的 Intune](https://aka.ms/intuneportal) 中，選擇 [裝置註冊] > [Windows 註冊] > [裝置] > [匯入]。

    ![AutoPilot Windows 裝置的螢幕擷取畫面](media/enrollment-autopilot/autopilot-import-device.png)

2. 在 [新增 Windows Autopilot 裝置] 下，瀏覽至列出所要新增裝置的 CSV 檔案。 該文件應包含裝置的序號、Windows 產品識別碼、硬體雜湊和選擇性的訂單識別碼。

    ![新增 AutoPilot Windows 裝置的螢幕擷取畫面](media/enrollment-autopilot/autopilot-import-device2.png)

3. 選擇 [匯入] 開始匯入裝置資訊。 匯入可能需要幾分鐘的時間。

4. 匯入完成後，選擇 [裝置註冊] > [Windows註冊] > [Windows AutoPilot] > [裝置] > [同步處理]。訊息會顯示正在進行同步處理。 程序可能需要幾分鐘才能完成，取決於有多少裝置正在進行同步處理。

5. 重新整理檢視可查看新的裝置。

## <a name="create-an-autopilot-device-group"></a>建立 AutoPilot 裝置群組

1. 在 [Azure 入口網站的 Intune](https://aka.ms/intuneportal) 中，選擇 [群組]。
2. 在 [群組] 刀鋒視窗中：
    1. 針對 [群組類型]，請選擇 [安全性]。
    2. 輸入**群組名稱**與**群組描述**。
    3. 針對 [成員資格類型]，選擇 [已指派] 或是 [動態裝置]。
3. 如果您在上一步中針對 [成員資格類型] 選擇 [已指派]，則在 [群組] 刀鋒視窗中，請選擇 [成員] 並將 AutoPilot 裝置設備新增至群組。
    尚未註冊的 AutoPilot 裝置，其名稱為裝置的序號。
4. 如果針對上述的 [成員資格類型] 選擇 [動態裝置]，則在 [群組] 刀鋒視窗中，請選擇 [動態裝置成員]，然後在 [進階規則] 方塊中輸入下列任意一項代碼。
    - 如果要建立包含所有 AutoPilot 裝置的群組，請輸入 `(device.devicePhysicalIDs -any _ -contains "[ZTDId]")`
    - 若建立的群組要包含具有特定訂單識別碼的所有 AutoPilot 裝置，請輸入：`(device.devicePhysicalIds -any _ -eq "[OrderID]:179887111881") `
    - 若建立的群組要包含具有特定採購單識別碼的所有 AutoPilot 裝置，請輸入：`(device.devicePhysicalIds -any _ -eq "[PurchaseOrderId]:76222342342")`
    
    新增 [進階規則] 代碼後，選擇 [儲存]。
5. 選擇 **[建立]**。



## <a name="create-an-autopilot-deployment-profile"></a>建立 AutoPilot 部署設定檔
AutoPilot 部署設定檔用來設定 AutoPilot 裝置。
1. 在 [Azure 入口網站的 Intune](https://aka.ms/intuneportal) 中，選擇 [裝置註冊] > [Windows 註冊] > [部署設定檔] > [建立設定檔]。
2. 輸入**名稱**和選擇性的**描述**。
3. 針對 [部署模式]，請選擇下列兩個選項的其中一個：
    - **使用者驅動**：具有此設定檔的裝置會與註冊裝置的使用者相關聯。 須要有使用者認證，才能佈建裝置。
    - **自我部署 (預覽)**：(Windows 10 Insider Preview 組建 17672 或更新版本) 具有此設定檔的裝置不會與註冊裝置的使用者建立關聯。 不須有使用者認證，就能佈建裝置。
4. 在 [加入Azure AD] 方塊中，選擇 [已加入 Azure AD]。
5. 選擇 [全新體驗 (OOBE)]、設定下列選項，然後選擇 [儲存]：
    - **語言 (地區)***：選擇要用於裝置的語言。 僅當您針對 [部署模式] 選擇 [自我部署] 時，此選項才可使用。
    - **自動設定鍵盤***：如果選取了 [語言 (區域)]，請選擇 [是] 跳過鍵盤選取頁面。 僅當您針對 [部署模式] 選擇 [自我部署] 時，此選項才可使用。
    - **使用者授權合約 (EULA)**：(Windows 10，版本 1709 或更新版本) 選擇是否向使用者顯示 EULA。
    - **隱私權設定**：選擇是否向使用者顯示隱私權設定。
    - **隱藏變更帳戶選項 (僅限 Windows 測試人員)**：選擇 [隱藏] 以防止在公司登入和網域錯誤頁面上顯示變更帳戶選項。 此選項需要[在 Azure Active Directory 中設定公司商標](https://docs.microsoft.com/azure/active-directory/fundamentals/customize-branding)。
    - **使用者帳戶類型**：選擇使用者的帳戶類型為 [系統管理員] 或 [標準] 使用者。
    - **套用電腦名稱範本 (僅限 Windows 測試人員)**：選擇 [是] 以建立要在佈建期間命名裝置時使用的範本。 名稱必須是 15 個字元或更少，而且可以包含字母、數字和連字號。 名稱不可以全部為數字。 使用 [%SERIAL% 巨集](https://docs.microsoft.com/windows/client-management/mdm/accounts-csp)新增硬體特定序號。 或者，使用 [%RAND:x% 巨集](https://docs.microsoft.com/windows/client-management/mdm/accounts-csp)新增隨機數字字串，其中 x 等於要新增的位數。 

6. 選擇 [建立] 以建立設定檔。 現在可以指派 AutoPilot 部署設定檔給裝置。

*僅在您針對 [部署模式] 選擇 [自我部署 (預覽)] 時，才能使用 [語言 (地區)] 和 [自動設定鍵盤] (Windows 10 Insider Preview 組建 17672 或更新版本)。


## <a name="assign-an-autopilot-deployment-profile-to-a-device-group"></a>指派 AutoPilot 部署設定檔至裝置群組

1. 在 [Azure 入口網站的 Intune](https://aka.ms/intuneportal) 中，選擇 [裝置註冊] > [Windows 註冊] > [部署設定檔] > 選擇設定檔。
2. 在 [特定設定檔] 刀鋒視窗中，選擇 [指派]。 
3. 選擇 [選取群組]，然後在 [選取群組] 刀鋒視窗中，選擇要指派該設定檔的群組，然後選擇 [選取]。

## <a name="edit-an-autopilot-deployment-profile"></a>編輯 AutoPilot 部署設定檔
建立 AutoPilot 部署設定檔之後，您可以編輯部署設定檔的某些部分。   

1. 在 [Azure 入口網站的 Intune](https://aka.ms/intuneportal) 中，選擇 [裝置註冊]。
2. 在 [Windows 註冊] 之下，於 [Windows AutoPilot] 區段中，選擇 [部署設定檔]。
3. 選取您想要編輯的設定檔。
4. 按一下左邊的 [屬性]，變更部署設定檔的名稱或描述。 進行變更之後請按一下 [儲存]。
5. 按一下 [設定] 以變更 OOBE 設定。 進行變更之後請按一下 [儲存]。

> [!NOTE]
> 設定檔的變更會套用至指派給該設定檔的裝置。 不過，更新的設定檔不會套用到已在 Intune 註冊的裝置，直到裝置已重設並重新註冊為止。

## <a name="alerts-for-windows-autopilot-unassigned-devices-----163236---"></a>Windows AutoPilot 未指派裝置的警示 <!-- 163236 -->
您可以檢視警示，以查看有多少 AutoPilot 方案的裝置尚未指派 AutoPilot 部署設定檔。 您可以使用警示中的資訊來建立設定檔，並加以指派至未指派的裝置。 當您按一下警示時，會看到 Windows AutoPilot 裝置的完整清單，以及這些裝置的詳細資訊。

若要查看未指派的裝置的警示，請[在 Azure 入口網站的 Intune 中](https://aka.ms/intuneportal)，選擇 [裝置註冊] > [概觀] > [未指派的裝置]。  


## <a name="assign-a-user-to-a-specific-autopilot-device"></a>將使用者指派給特定 Autopilot 裝置

您可以將使用者指派給特定 Autopilot 裝置。 此指派會在 Windows 安裝期間的[設定公司商標](https://docs.microsoft.com/azure/active-directory/fundamentals/customize-branding)登入頁面上，預先填入 Azure Active Directory 中的使用者。 它也可讓您設定自訂問候語名稱。 這不會預先填入或修改 Windows 登入。 只有具授權的 Intune 使用者可以透過此方式指派。

必要條件：已設定 Azure Active Directory 公司入口網站。

1. 在 [Azure 入口網站的 Intune](https://aka.ms/intuneportal) 中，選擇 [裝置註冊] > [Windows 註冊] > [裝置]> 選擇裝置 > [指派使用者]。
    ![指派使用者的螢幕擷取畫面](media/enrollment-autopilot/assign-user.png)
2. 選擇授權使用 Intune 的 Azure 使用者並選擇 [選取]。
    ![選取使用者的螢幕擷取畫面](media/enrollment-autopilot/select-user.png)
3. 在 [User Friendly Name] \(使用者易記名稱\) 方塊中，鍵入易記名稱或直接接受預設值。 這是使用者在 Windows 安裝期間登入時顯示的易記名稱。
    ![易記名稱的螢幕擷取畫面](media/enrollment-autopilot/friendly-name.png)
4. 選擇 [確定]。


## <a name="delete-autopilot-devices"></a>刪除 AutoPilot 裝置

您可以刪除未註冊的 Windows AutoPilot 裝置。

1. 如果裝置已在 Intune 中註冊，則必須先[從 Azure Active Directory 入口網站中加以刪除](devices-wipe.md#delete-devices-from-the-azure-active-directory-portal)。

2. 在 [Azure 入口網站的 Intune](https://aka.ms/intuneportal) 中，選擇 [裝置註冊] > [Windows 註冊] > [裝置]。

3. 在 [Windows AutoPilot 裝置] 下，選擇您要刪除的裝置，然後選擇 [刪除]。

4. 選擇 [是] 以確認刪除。 可能需要幾分鐘才能刪除。

## <a name="using-autopilot-in-other-portals"></a>在其他入口網站中使用 AutoPilot
如果您對行動裝置管理不感興趣，則可以在商務用 Microsoft Store (舉例而言) 中使用 AutoPilot。 雖然可以選擇使用其他入口網站，我們建議您只使用 Intune 來管理 AutoPilot 部署。 如果您使用 Intune 與另一個入口網站，Intune 將無法：
- 顯示在 Intune 中建立但在另一個入口網站中編輯之設定檔的變更
- 同步處理在另一個入口網站中建立的設定檔
- 顯示在另一個入口網站中進行的設定檔指派變更
- 同步處理在另一個入口網站中進行的設定檔指派
- 顯示在另一個入口網站中完成的裝置清單變更

## <a name="next-steps"></a>接下來的步驟
您為已註冊的 Windows 10 裝置設定 Windows AutoPilot 之後，請了解如何管理這些裝置。 如需詳細資訊，請參閱[什麼是 Microsoft Intune 裝置管理？](https://docs.microsoft.com/intune/device-management)

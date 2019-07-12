---
title: 使用 Microsoft Intune 將 Office 365 應用程式指派給 Windows 10 裝置
titleSuffix: ''
description: 了解如何使用 Microsoft Intune 在 Windows 10 裝置上安裝 Office 365 應用程式。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 04/08/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 3292671a-5f5a-429e-90f7-b20019787d22
ms.reviewer: craigma
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure, seoapril2019
ms.collection: M365-identity-device-management
ms.openlocfilehash: 00712b891790fbf437e9fed024f7610f37fee129
ms.sourcegitcommit: 1b7ee2164ac9490df4efa83c5479344622c181b5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/08/2019
ms.locfileid: "67648703"
---
# <a name="assign-office-365-apps-to-windows-10-devices-with-microsoft-intune"></a>使用 Microsoft Intune 將 Office 365 應用程式指派給 Windows 10 裝置

您必須先將應用程式新增至 Intune，才可以指派、監視、設定或保護它們。 其中一種可用[應用程式類型](apps-add.md#app-types-in-microsoft-intune)是適用於 Windows 10 裝置的 Office 365 應用程式。 藉由在 Intune 中選取此應用程式類型，您可以指派 Office 365 應用程式，並將其安裝到您所管理且執行 Windows 10 的裝置。 若您擁有 Microsoft Project Online 桌面用戶端以及 Microsoft Visio Online 方案 2 的授權，則也可以指派並安裝這兩者的應用程式。 可用 Office 365 應用程式在 Azure 內 Intune 主控台上的應用程式清單中顯示為單一項目。

> [!NOTE]
> 您必須使用 Office 365 專業增強版授權來啟用透過 Microsoft Intune 部署的 Office 365 ProPlus 應用程式。 目前，Intune 不支援 Office 365 Business Edition。

## <a name="before-you-start"></a>開始之前

> [!IMPORTANT]
> 若使用者裝置上有 .msi Office 應用程式，您必須使用**移除 MSI** 功能來安全地解除安裝這些應用程式。 否則，Intune 提供的 Office 365 應用程式將無法安裝。

- 部署這些應用程式的裝置必須執行 Windows 10 Creators Update 或更新版本。
- Intune 僅支援從 Office 365 套件新增 Office 應用程式。
- 如果在 Intune 安裝應用程式套件時開啟任何 Office 應用程式，安裝可能會失敗，且使用者可能會遺失未儲存檔案的資料。
- Windows 10 S、Windows Home、Windows Team、Windows Holographic 或 Windows Holographic for Business 裝置不支援此安裝方法。
- Intune 不支援在已使用 Intune 部署 Office 365 應用程式的裝置上，安裝來自 Microsoft Store 的 Office 365 傳統型應用程式 (又稱為 Office Centennial 應用程式)。 如果您安裝此設定，可能會導致資料遺失或損毀。
- 未附加多個必要或可用的應用程式指派。 較新的應用程式指派會覆寫現有的已安裝應用程式指派。 例如，如果第一組的 Office 應用程式包含 Word，而較新的集合沒有 Word，則 Word 會解除安裝。 此條件不適用於任何 Visio 或 Project 應用程式。
- 目前不支援多個 Office 365 部署。 系統只會向裝置傳遞單一部署
- **Office 版本** - 選擇要指派 32 位元還是 64 位元版本的 Office。 32 位元版本可以安裝在 32 位元和 64 位元的裝置上，但 64 位元版本只能安裝在 64 位元的裝置。
- **從終端使用者裝置移除 MSI** - 選擇是否要從終端使用者裝置移除已有的 Office .MSI 應用程式。 如果終端使用者裝置上已有 .MSI 應用程式，則該安裝不會成功。 要解除安裝的應用程式不限於在 [設定應用程式套件]  中選取要安裝的應用程式，因為它會將所有 Office (MSI) 應用程式從終端使用者裝置移除。 如需詳細資訊，請參閱 [Remove existing MSI versions of Office when upgrading to Office 365 ProPlus](https://docs.microsoft.com/deployoffice/upgrade-from-msi-version) (在升級至 Office 365 專業增強版時，移除 Office 的現有 MSI 版本。 當 Intune 在您終端使用者的電腦上重新安裝 Office 時，終端使用者會自動取得與其先前 .MSI Office 安裝相同的語言套件。

## <a name="get-started"></a>開始使用

1. 登入 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
3. 在 [Intune]  窗格中，選取 [用戶端應用程式]  。
4. 在 [用戶端應用程式]  工作負載窗格中的 [管理]  下，選取 [應用程式]  。
5. 選取 [新增]  。
6. 在 [新增應用程式]  窗格的 [應用程式類型]  清單中，於 [Office 365 Suite]  下，選取 [Windows 10]  。

## <a name="select-settings-format"></a>選取設定格式

您可以選取 [設定格式]  來選擇設定應用程式的方法。 設定格式選項包括：
- 設定設計工具
- 輸入 XML 資料

當您選擇 [設定設計工具]  時，[新增應用程式]  刀鋒視窗將變更為提供兩個額外的設定選項：
- 設定應用程式套件
- 應用程式套件設定

<img alt="Add Office 365 - Configuration designer" src="./media/apps-add-office365/apps-add-office365-02.png" width="700">

當您選擇 [輸入 XML 資料]  時，[新增應用程式]  刀鋒視窗中會顯示 [輸入 XML 資料]  選項。 選取此選項以顯示 [設定檔]  刀鋒視窗。 

![新增 Office 365 設定設計工具](./media/apps-add-office365/apps-add-office365-01.png)
    
如需 [輸入 XML 資料]  選項的詳細資訊，請參閱下方的[輸入 XML 資料](apps-add-office365.md#enter-xml-format)。

## <a name="configure-app-suite-information"></a>設定應用程式套件資訊

在此步驟中，您要提供應用程式套件的相關資訊。 這項資訊可協助您在 Intune 中識別應用程式套件，且能幫助使用者在公司入口網站中尋找應用程式套件。

1. 在 [新增應用程式]  窗格中，選取 [應用程式套件資訊]  。
2. 在 [應用程式套件資訊]  窗格中，執行以下動作：
    - **套件名稱**：輸入應用程式套件在公司入口網站中顯示的名稱。 請確定使用的所有套件名稱都是唯一的。 如果有重複的應用程式套件名稱，使用者只會在公司入口網站中看到其中一個應用程式。
    - **套件描述**：輸入應用程式套件的描述。 例如，您可以列出已選取包含的應用程式。
    - **發行者**：Microsoft 會顯示為發行者。
    - **類別**：(選擇性) 選取一或多個內建的應用程式類別，或選取您建立的類別。 此設定可讓使用者在瀏覽公司入口網站時，更輕鬆地找到應用程式套件。
    - **將此顯示為公司入口網站中的精選應用程式**：若要在使用者瀏覽應用程式時，於公司入口網站的主頁面上以醒目方式顯示應用程式套件，請選取此選項。
    - **資訊 URL**：(選用) 輸入包含此應用程式相關資訊的網站 URL。 使用者會在公司入口網站中看到這個 URL。
    - **隱私權 URL**：(選擇性) 輸入包含這個應用程式之隱私權資訊的網站 URL。 使用者會在公司入口網站中看到這個 URL。
    - **開發人員**：Microsoft 會顯示為開發人員。
    - **擁有者**：Microsoft 會顯示為擁有者。
    - **附註**：輸入要與此應用程式建立關聯的任何附註。
    - **標誌**：當使用者瀏覽公司入口網站時，Office 365 標誌會隨應用程式一起顯示。
3. 選取 [確定]  。

## <a name="configure-app-suite"></a>設定應用程式套件

如果您在 [設定格式]  下拉式方塊底下選取 [設定設計工具]  選項，就會在 [新增應用程式]  刀鋒視窗中看到 [設定應用程式套件]  選項。 選取您想要指派給裝置的 Office 應用程式。

1. 在 [新增應用程式]  窗格中，選取 [設定應用程式套件]  。
2. 在 [設定應用程式套件]  窗格中，選取您想要指派給裝置的標準 Office 應用程式。  
    此外，若您擁有 Microsoft Project Online 桌面用戶端以及 Microsoft Visio Online 方案 2 的授權，您可以安裝其適用的應用程式。
3. 選取 [確定]  。

## <a name="configure-app-suite-settings"></a>設定應用程式套件設定

如果您在 [設定格式]  下拉式方塊底下選取 [設定設計工具]  選項，就會在 [新增應用程式]  刀鋒視窗中看到 [應用程式套件設定]  選項。 在此步驟中，設定應用程式套件的安裝選項。 這些設定適用於您新增至套件的所有應用程式。

1. 在 [新增應用程式]  窗格中，選取 [應用程式套件設定]  。
2. 在 [應用程式套件設定]  窗格中，執行以下動作：
    - **Office 版本**：選擇要指派 32 位元還是 64 位元版本的 Office。 32 位元版本可以安裝在 32 位元和 64 位元的裝置上，但 64 位元版本只能安裝在 64 位元的裝置。
    - **更新通道**：選擇 Office 在裝置上的更新方式。 如需各種更新頻道的相關資訊，請參閱 [Office 365 專業增強版更新頻道概觀](https://docs.microsoft.com/DeployOffice/overview-of-update-channels-for-office-365-proplus) \(機器翻譯\)。 從下列選項進行選擇：
        - **每月**
        - **每月 (目標)**
        - **每半年**
        - **每半年 (目標)**

        在您選取 [通道] 後，您可以選擇性選取 [特定]  ，以在終端使用者裝置上，為所選通道安裝特定 Office 版本。 然後選取要使用之 Office 的 [特定版本]  。
        
        可用的版本將會隨著時間變更。 因此，建立新的部署時，可用的版本可能較新，因此沒有特定較舊版本可用。 目前部署將會繼續部署較舊的版本，但每個通道都會持續更新版本清單。
        
        對於更新已固定版本 (或更新任何其他屬性) 且部署為可用的裝置，若在裝置簽入發生前，該裝置已安裝舊版，則回報狀態會顯示為 [已安裝]。 當裝置簽入發生時，狀態會暫時變更為 [未知]，但不會向使用者顯示。 當使用者起始較新可用版本的安裝時，該使用者會看到狀態變更為 [已安裝]。
        
        如需詳細資訊，請參閱 [Office 365 ProPlus 更新通道的概觀](https://docs.microsoft.com/DeployOffice/overview-of-update-channels-for-office-365-proplus)。

    - **從終端使用者裝置移除 MSI** - 選擇是否要從終端使用者裝置移除已有的 Office .MSI 應用程式。 如果終端使用者裝置上已有 .MSI 應用程式，則該安裝不會成功。 要解除安裝的應用程式不限於在 [設定應用程式套件]  中選取要安裝的應用程式，因為它會將所有 Office (MSI) 應用程式從終端使用者裝置移除。 如需詳細資訊，請參閱 [Remove existing MSI versions of Office when upgrading to Office 365 ProPlus](https://docs.microsoft.com/deployoffice/upgrade-from-msi-version) (在升級至 Office 365 專業增強版時，移除 Office 的現有 MSI 版本。 當 Intune 在您終端使用者的電腦上重新安裝 Office 時，終端使用者會自動取得與其先前 .MSI Office 安裝相同的語言套件。 
    - **自動接受應用程式的使用者授權合約**：如果您不需要使用者接受授權合約，請選取此選項。 Intune 會自動接受合約。
    - **使用共用電腦啟用**：當多個使用者共用一部電腦時，請選取此選項。 如需詳細資訊，請參閱 [Office 365 的共用電腦啟用概觀](https://docs.microsoft.com/DeployOffice/overview-of-shared-computer-activation-for-office-365-proplus)。
    - **語言**：系統會自動以使用者裝置上與 Windows 一起安裝的任何受支援語言安裝 Office。 如果想要使用其他語言安裝應用程式套件，請選取此選項。 <p></p>
    您將可以為透過 Intune 管理的 Office 365 專業增強版應用程式來部署其他語言。 可用的語言清單包括語言套件的**類型** (核心、部分和校訂)。 在 Azure 入口網站中，選取 [Microsoft Intune]   > [用戶端應用程式]   > [應用程式]   > [新增]  。 在 [新增應用程式]  刀鋒視窗的 [應用程式類型]  清單中，選取 [Office 365 套件]  下的 [Windows 10]  。 選取 [應用程式套件設定]  刀鋒視窗中的 [語言]  。 如需詳細資訊，請參閱[在 Office 365 專業增強版中部署語言的概觀](https://docs.microsoft.com/deployoffice/overview-of-deploying-languages-in-office-365-proplus)。

## <a name="select-scope-tags-optional"></a>選取範圍標籤 (選擇性)
您可以使用範圍標籤來決定可在 Intune 中看見用戶端應用程式資訊的人員。 如需範圍標籤的完整詳細資料，請參閱[針對分散式 IT 使用角色型存取控制和範圍標籤](scope-tags.md)。

1. 選取 [範圍 (標籤)]   > [新增]  。
2. 使用 [選取]  方塊來搜尋範圍標籤。
3. 選取您想要指派至此應用程式之範圍標籤旁邊的核取方塊。
4. 選擇 [選取]   > [確定]  。

## <a name="enter-xml-format"></a>輸入 XML 格式

如果您在 [設定格式]  下拉式方塊底下選取 [輸入 XML 資料]  選項，就會在 [新增應用程式]  刀鋒視窗中看到 [輸入 XML 格式]  選項。 如需詳細資訊，請參閱 [Office 部署工具的設定選項](https://docs.microsoft.com/DeployOffice/configuration-options-for-the-office-2016-deployment-tool)。

## <a name="finish-up"></a>完成

當您完成時，在 [新增應用程式]  窗格中，選取 [新增]  。 您已建立的應用程式會顯示在應用程式清單中。

## <a name="troubleshooting"></a>疑難排解
Intune 會使用 [Office 部署工具](https://docs.microsoft.com/DeployOffice/overview-of-the-office-2016-deployment-tool)來透過 [Office 365 CDN](https://docs.microsoft.com/office365/enterprise/content-delivery-networks)\(部分機器翻譯\) 將 Office 365 專業增強版下載並部署至您的用戶端電腦。 請參考[管理 Office 365 端點](https://docs.microsoft.com/office365/enterprise/managing-office-365-endpoints) \(部分機器翻譯\) 中概述的最佳做法，來確保您的網路設定能允許用戶端直接存取 CDN，而非透過中央 Proxy 路由 CDN 流量，以避免產生不必要的延遲。

如果您遇到安裝或執行階段問題，請在目標裝置上執行 [Microsoft Office 365 支援及修復小幫手](https://diagnostics.office.com)。

## <a name="errors-during-installation-of-the-app-suite"></a>應用程式套件安裝期間發生的錯誤

請參閱[如何啟用 Office 365 專業增強版 ULS 記錄](https://blogs.technet.microsoft.com/odsupport/2018/06/18/how-to-enable-office-365-proplus-uls-logging) \(英文\) 來取得如何檢視詳細資訊安裝記錄的相關資訊。

下表列出您可能會遇到的常見錯誤碼及其意義。

### <a name="status-for-office-csp"></a>Office CSP 狀態

| 狀態 | 階段 | 說明 |
|--------------------------------------------------|--------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 1460 (ERROR_TIMEOUT) | 下載 | 無法下載 Office 部署工具 |
| 13 (ERROR_INVALID_DATA) | - | 無法驗證下載的 Office 部署工具簽章 |
| 來自 CertVerifyCertificateChainPolicy 的錯誤碼 | - | 對下載的 Office 部署工具的憑證檢查失敗 |
| 997 | WIP | 安裝 |
| 0 | 安裝後 | 安裝成功 |
| 1603 (ERROR_INSTALL_FAILURE) | - | 進行任何先決條件檢查時失敗，例如：SxS (嘗試在已安裝 2016 MSI 的情況下進行安裝)、版本不符、其他 |
| 0x8000ffff (E_UNEXPECTED) | - | 電腦上沒有隨選即用 Office 時嘗試解除安裝 |
| 17002 | - | 無法完成案例 (安裝)。 可能的原因：使用者取消安裝、另一個安裝取消安裝、安裝期間磁碟空間不足、不明的語言識別碼 |
| 17004 | - | 未知的 SKU |


### <a name="office-deployment-tool-error-codes"></a>Office 部署工具錯誤碼

| 案例 | 傳回碼 | UI | 注意 |
|------------------------------------------------------------------------------------------------------------------|---------------------------------------|----------------------------------------------------|------------------------------------|
| 沒有任何使用中的隨選即用安裝時即解除安裝 | -2147418113、0x8000ffff 或 2147549183 | 錯誤碼：30088-1008 錯誤碼：30125-1011 (404) | Office 部署工具 |
| 已安裝 MSI 版本時安裝 | 1603 | - | Office 部署工具 |
| 使用者或另一個安裝已取消安裝 | 17002 | - | 隨選即用 |
| 嘗試在已安裝 32 位元的裝置上安裝 64 位元。 | 1603 | - | Office 部署工具傳回碼 |
| 嘗試安裝未知的 SKU (Office CSP 的不合法使用案例，因為我們應該只傳遞有效的 SKU) | 17004 | - | 隨選即用 |
| 空間不足 | 17002 | - | 隨選即用 |
| 隨選即用用戶端無法啟動 (非預期) | 17000 | - | 隨選即用 |
| 隨選即用用戶端無法將案例排入佇列 (非預期) | 17001 | - | 隨選即用 |

## <a name="next-steps"></a>後續步驟

- 若要將應用程式指派給您選擇的群組，請參閱[將應用程式指派給群組](/intune-azure/manage-apps/deploy-apps)。

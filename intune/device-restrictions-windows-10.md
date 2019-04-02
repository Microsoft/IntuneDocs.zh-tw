---
title: Microsoft Intune 中 Windows 10 的裝置限制設定 | Microsoft Docs
description: 查看有關在 Windows 10 和更新版本的裝置上建立裝置限制的所有設定及其描述的清單。 使用組態設定檔中的這些設定，在 Microsoft Intune 中控制螢幕擷取畫面、密碼要求、kiosk 設定、商店中的應用程式、Microsoft Edge 瀏覽器、Windows Defender、雲端存取及開始功能表等。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/20/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7ca34826f3a235fe620b5ac0dcb95d57dabf4c71
ms.sourcegitcommit: 1069b3b1ed593c94af725300aafd52610c7d8f04
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 03/22/2019
ms.locfileid: "58394995"
---
# <a name="windows-10-and-newer-device-settings-to-allow-or-restrict-features-using-intune"></a>使用 Intune 來允許或限制功能的 Windows 10 (和更新版本) 裝置設定

本文列出並描述您可以在 Windows 10 和更新版本裝置上控制的所有不同設定。 作為行動裝置管理 (MDM) 解決方案的一部分，請使用這些設定來允許或停用功能、設定密碼規則、自訂鎖定畫面、使用 Windows Defender，以及執行其他作業。

這些設定會新增至 Intune 裝置組態設定檔，然後指派或部署到您的 Windows 10 裝置。

> [!Note]
> 並非所有版本的 Windows 都提供全部選項。 若要查看支援的版本，請參閱[原則 Csp](https://docs.microsoft.com/windows/client-management/mdm/policy-configuration-service-provider) （開啟另一個 Microsoft 網站上）。

## <a name="before-you-begin"></a>開始之前

[建立裝置組態設定檔](device-restrictions-configure.md#create-the-profile)。

## <a name="app-store"></a>App Store

- **App Store (僅限行動裝置)**：啟用或封鎖在 Windows 10 行動裝置上使用 App Store。
- **自動更新來自市集的應用程式** - 允許自動更新從 Microsoft 網上商店安裝的應用程式。
- **安裝信任的應用程式**：允許側載使用受信任憑證簽署的應用程式。
- **開發人員解除鎖定**：允許 Windows 開發人員設定，例如允許使用者修改側載應用程式。
- **共用的使用者應用程式資料**：允許應用程式在相同裝置上的不同使用者之間共用資料。
- **僅使用私人市集**：啟用僅允許終端使用者從您的私人市集下載應用程式。
- **啟動來自市集的應用程式**：用來停用預先安裝於裝置上，或是從 Microsoft 網上商店下載的所有應用程式。
- **將應用程式資料安裝在系統磁碟區**：阻止應用程式將資料儲存在裝置的系統磁碟區上。
- **將應用程式安裝在系統磁碟機**：阻止應用程式將資料儲存在裝置的系統磁碟機上。
- **遊戲 DVR (僅限桌面版)**：設定是否允許錄製和廣播遊戲。
- **僅限來自市集的應用程式** - 設定使用者是否可以從 App Store 以外的地方安裝應用程式。

## <a name="cellular-and-connectivity"></a>行動數據與連線

- **行動數據頻道**：當使用者連線到行動電話通訊網路時，阻止使用者使用資料，如瀏覽網頁。 
- **數據漫遊**：存取資料時允許網路之間的漫遊。
- **透過行動電話通訊網路的 VPN**：控制裝置是否可以在連線到行動電話通訊網路時存取 VPN 連線。
- **透過行動電話通訊網路的 VPN**：控制裝置是否可以在連線到行動電話通訊網路時存取 VPN 連線。
- **藍牙**：控制使用者是否可在裝置上啟用及設定藍牙。
- **藍牙探索**：讓其他藍牙啟用的裝置探索此裝置。
- **藍芽預先配對**：可讓您設定特定的藍芽裝置與主機裝置自動配對。
- **藍牙廣告**：讓藍牙可透過藍牙裝置接收廣告。
- **連線的裝置服務**：讓您選擇允許連線的裝置服務，以便探索並連線到其他藍牙裝置。
- **NFC**：讓使用者可在裝置上啟用及設定近距離無線通訊 (NFC) 功能。
- **Wi-Fi**：讓使用者可在裝置上啟用及設定 Wi-Fi (僅限 Windows 10 行動裝置版)。
- **自動連線至 Wi-Fi 熱點**：讓裝置能自動連線到免費 Wi-Fi 熱點並自動接受任何連線條款和條件。
- **手動設定 Wi-Fi**：控制使用者是否可設定自己的 Wi-Fi 連線，是或只能使用由 Wi-Fi 設定檔所設定的連線 (僅限 Windows 10 行動裝置版)。
- **Wi-Fi 掃描間隔**：輸入裝置掃描 Wi-Fi 網路的頻率。 輸入 1 (最頻繁) 到 500 (最不頻繁) 的值。
- **藍牙允許的服務**：輸入允許之藍牙服務和設定檔的十六進位字串清單。

## <a name="cloud-and-storage"></a>雲端與儲存體

- **Microsoft 帳戶**：讓使用者建立 Microsoft 帳戶與裝置之間的關聯。
- **非 Microsoft 帳戶**：讓使用者將電子郵件帳戶新增至未與 Microsoft 帳戶相關聯的裝置。
- **Microsoft 帳戶的設定同步**：允許與 Microsoft 帳戶相關聯的裝置和應用程式設定在裝置之間進行同步處理。
- **Microsoft 帳戶登入小幫手**：選擇 [停用] 即可防止終端使用者控制 Microsoft 登入小幫手服務 (wlidsvc)，例如手動停止或啟動服務。 設為 [未設定] 時，wlidsvc NT 服務會採用作業系統 (OS) 預設，其可能會讓終端使用者得以啟動或停止服務。 OS 會使用此服務來讓使用者登入他們的 Microsoft 帳戶。

## <a name="cloud-printer"></a>雲端印表機

- **印表機探索 URL**：輸入用於尋找雲端印表機的 URL。
- **印表機存取授權 URL**：輸入用於取得 OAuth 權杖的驗證端點 URL。 例如，輸入類似 `https://login.microsoftonline.com/your Azure AD Tenant ID` 的內容。
- **Azure 原生用戶端應用程式 GUID**：輸入經允許可從 OAuthAuthority 取得 OAuth 權杖的用戶端應用程式 GUID。
- **列印服務資源 URI**：輸入 Azure 入口網站中所設定列印服務的 OAuth 資源 URI。 例如，輸入類似 `http://MicrosoftEnterpriseCloudPrint/CloudPrint` 的內容。
- **要查詢的印表機上限 (僅限行動裝置版)** ：輸入您要接受查詢的印表機數目上限。 例如，輸入 `10`。
- **印表機探索服務資源 URI**：輸入 Azure 入口網站中所設定印表機探索服務的 OAuth 資源 URI。 例如，輸入類似 `http://MopriaDiscoveryService/CloudPrint` 的內容。

> [!TIP]
> 設定 [Windows Server 混合式雲端列印](https://docs.microsoft.com/windows-server/administration/hybrid-cloud-print/hybrid-cloud-print-overview)之後，您可以進行這些設定，再部署到 Windows 裝置。

## <a name="control-panel-and-settings"></a>控制台和設定

- **設定應用程式**：封鎖對 Windows [設定] 應用程式的存取。
  - **系統**：封鎖對 [設定] 應用程式 [系統] 區域的存取。
    - **修改電源及睡眠設定 (僅限桌面版)**：防止使用者變更裝置上的電源及睡眠設定。
  - **裝置**：封鎖對 [設定] 應用程式 [裝置] 區域的存取。
  - **網路網際網路**：封鎖對 [設定] 應用程式 [網路和網際網路] 區域的存取。
  - **個人化**：封鎖對 [設定] 應用程式 [個人化] 區域的存取。
  - **帳戶**：封鎖對 [設定] 應用程式 [帳戶] 區域的存取。
  - **時間與語言**：封鎖對 [設定] 應用程式 [時間與語言] 區域的存取。
    - **修改系統時間**：防止使用者變更裝置日期和時間。
    - **修改區域設定 (僅限桌面版)**：防止使用者變更裝置上的區域設定。
    - **修改語言設定 (僅限桌面版)**：防止使用者變更裝置上的語言設定。
  - **遊戲**：封鎖對 [設定] 中 [遊戲] 應用程式的存取。
  - **輕鬆存取**：封鎖對 [設定] 應用程式 [輕鬆存取] 區域的存取。
  - **隱私權**：封鎖對 [設定] 應用程式 [隱私權] 區域的存取。
  - **更新與安全性**：封鎖對 [設定] 應用程式 [更新與安全性] 區域的存取。

## <a name="display"></a>顯示

- **開啟應用程式的 GDI 調整功能**
- **關閉應用程式的 GDI 調整功能**

  GDI DPI 縮放比例會讓非 DPI 感知的應用程式變成個別監視器 DPI 感知。 請輸入會開啟 GDI DPI 縮放比例的舊版應用程式。 應用程式上的 GDI DPI 縮放比例若設為開啟和關閉，該應用程式的縮放比例功能就會關閉。

## <a name="general"></a>一般

- **螢幕擷取 (僅限行動裝置)**：讓使用者可將裝置螢幕擷取為影像。
- **複製並貼上 (僅限行動裝置)**：允許在裝置上的應用程式之間，進行複製並貼上的動作。
- **手動取消註冊**：讓使用者可從裝置手動刪除工作場所帳戶。
  - 如果電腦已加入 Azure AD，且啟用自動註冊，則不會套用此原則設定。 
  - 此原則設定不適用於執行 Windows 10 家用版的電腦。
- **手動安裝根憑證 (僅限行動裝置)**：阻止使用者手動安裝根憑證及中繼 CAP 憑證。

- **相機**：允許或封鎖在裝置上使用相機。
- **OneDrive 檔案同步**：封鎖裝置將檔案同步處理至 OneDrive。
- **抽取式存放裝置**：指定是否可以與裝置搭配使用 SD 卡等外部存放裝置。
- **地理位置**：指定裝置是否可以使用定位服務資訊。
- **網際網路共用**：允許在裝置上使用網際網路連線共用。
- **重設手機**：控制使用者是否可以抹除其裝置。
- **USB 連線 (僅限行動裝置)**：控制裝置是否可以透過 USB 連接來存取外接式存放裝置。
- **防竊模式 (僅限行動裝置)**：設定是否啟用 Windows 防竊模式。
- **Cortana**：啟用或停用 Cortana 語音助理。
- **錄音 (僅限行動裝置)**：允許或封鎖使用裝置錄音機。
- **修改裝置名稱**：防止終端使用者變更裝置名稱 (僅限 Windows 10 行動裝置版)
- **新增佈建套件**：封鎖安裝佈建套件的執行階段設定代理程式。
- **移除佈建套件**：封鎖移除佈建套件的執行階段設定代理程式。
- **裝置探索**：封鎖裝置以使它無法被其他裝置找到。
- **工作切換器 (僅限行動裝置)**：封鎖裝置上的工作切換器。
- **SIM 卡錯誤對話方塊 (僅限行動裝置)**：封鎖在沒有偵測到 SIM 卡的情況下會顯示於裝置上的錯誤訊息。
- **Ink 工作區**：禁止使用者存取 Ink 工作區。 [未設定] 會啟用 Ink 工作區，並允許使用者在鎖定畫面上使用它。
- **自動重新部署**：允許具有系統管理權限的使用者，在裝置鎖定畫面上使用 **CTRL + Win + R** 來刪除所有使用者資料和設定。 裝置會自動重新設定並重新註冊以納入管理。
- **要求使用者在裝置設定期間連線到網路 (僅限 Windows 測試人員)**：選擇 [需要] 讓裝置連線到網路，再繼續進行 Windows 10 安裝期間的 [網路] 頁面。 此功能尚在預覽階段，需要 Windows 測試人員組建 1809 或更新版本才能使用這項設定。
- **直接記憶體存取**：[封鎖] 會防止所有隨插即用 PCI 下游連接埠的直接記憶體存取 (DMA)，直到使用者登入 Windows 為止。 [啟用] (預設值) 會允許存取 DMA，就算使用者未登入也一樣。

  CSP：[DataProtection/AllowDirectMemoryAccess](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-dataprotection#dataprotection-allowdirectmemoryaccess)

- **結束處理程序在 [工作管理員] 從**： 此設定會決定非系統管理員是否可以使用工作管理員來結束工作。 [封鎖] 可防止標準使用者 (非系統管理員) 使用 [工作管理員] 來結束裝置上的處理序或工作。 [未設定] (預設) 可讓標準使用者使用 [工作管理員] 結束處理序或工作。

## <a name="locked-screen-experience"></a>鎖定畫面體驗

- **控制中心通知 (僅限行動裝置)**：可讓控制中心通知出現在裝置鎖定畫面上 (僅限 Windows 10 行動裝置版)。
- **鎖定畫面圖片 URL (僅限桌面版)**：輸入會作為 Windows 鎖定畫面桌布使用之 JPEG 格式圖片的 URL。 此設定會鎖定影像。 且之後就無法再變更影像。
- **使用者可設定的畫面逾時 (僅限行動裝置)**：可讓使用者設定時間量 
- **鎖定畫面上的 Cortana (僅限桌面版)**：不允許使用者在裝置位於鎖定畫面時與 Cortana 互動 (僅限 Windows 10 桌面版)。
- **鎖定畫面上的快顯通知**：封鎖警示訊息，使其無法顯示在裝置鎖定畫面上。
- **畫面逾時 (僅限行動裝置)**：指定畫面鎖定之後的時間 (以秒為單位)，在該段時間後將會關閉畫面。

## <a name="messaging"></a>訊息傳送

- **訊息同步 (僅限行動裝置版)**：停用訊息中心橋接和文字訊息備份及還原。
- **多媒體訊息 (僅限行動裝置)**：停用裝置上的多媒體訊息傳送/接收功能。
- **RCS (僅限行動裝置)**：停用裝置上的 Rich Communication Services 傳送/接收功能。

## <a name="microsoft-edge-browser"></a>Microsoft Edge 瀏覽器

### <a name="use-microsoft-edge-kiosk-mode"></a>使用 Microsoft Edge 的 kiosk 模式

可用的設定，端視您選擇的項目而有所不同。 選項包括：

- **否**（預設值）： Microsoft 邊緣不在 kiosk 模式中執行。 所有的 Microsoft Edge 設定可供您變更和設定。
- **Digital/Interactive 告示板 (單一應用程式 kiosk)**： 適用於使用只在 Windows 10 單一應用程式的 kiosk 上的數位/Interactive 告示板 Microsoft Edge Kiosk 模式的篩選 Microsoft Edge 設定。 選擇此設定，以開啟 URL 的全螢幕，並只顯示在該網站上的內容。 [設定數位簽署](https://docs.microsoft.com/windows/configuration/setup-digital-signage)提供這項功能的詳細資訊。
- **公用 inprivate (單一應用程式 kiosk)**： 適用於 InPrivate 公用瀏覽 Microsoft Edge 的 Kiosk 模式在 Windows 10 單一應用程式的 kiosk 上使用的篩選 Microsoft Edge 設定。 在執行多重索引標籤版本的 Microsoft Edge。
- **標準模式 (多應用程式 kiosk)**： 適用於一般 Microsoft Edge Kiosk 模式的篩選 Microsoft Edge 設定。 執行完整版的 Microsoft Edge 瀏覽的所有功能。
- **公用的瀏覽 (多應用程式 kiosk)**： 適用於 Windows 10 的多個應用程式 kiosk 上的公用瀏覽篩選 Microsoft Edge 設定。  在執行多索引標籤上的 Microsoft Edge InPrivate 版本。

> [!TIP]
> 如需有關這些選項的作用的詳細資訊，請參閱 < [Microsoft Edge kiosk 模式的組態類型](https://docs.microsoft.com/microsoft-edge/deploy/microsoft-edge-kiosk-mode-deploy#supported-configuration-types)。

此裝置限制設定檔會與直接相關的 kiosk 設定檔使用您所建立[Windows kiosk 設定](kiosk-settings-windows.md)。 總括來說：

1. 建立[Windows kiosk 設定](kiosk-settings-windows.md)kiosk 模式中執行裝置的設定檔。 選取 Microsoft Edge 與應用程式並設定 Microsoft Edge 的 Kiosk 模式 Kiosk 設定檔中。
2. 建立裝置限制設定檔，在本文中所述，並設定特定功能和允許 Microsoft Edge 中的設定。 請務必選擇與您的 kiosk 設定檔中已選取相同的 Microsoft Edge kiosk 模式類型 ([Windows kiosk 設定](kiosk-settings-windows.md))。 

    [支援的 kiosk 模式設定](https://docs.microsoft.com/microsoft-edge/deploy/microsoft-edge-kiosk-mode-deploy#supported-policies-for-kiosk-mode)是絕佳的資源。

> [!IMPORTANT] 
> 請務必將此 Microsoft Edge 設定檔指派給相同的裝置為 kiosk 的設定檔 ([Windows kiosk 設定](kiosk-settings-windows.md))。

[ConfigureKioskMode CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-configurekioskmode)

### <a name="start-experience"></a>[開始] 體驗

- **啟動 Microsoft Edge 並顯示**：選擇 Microsoft Edge 啟動時開啟的頁面。 選項包括：
  - **起始畫面**：Microsoft Edge 以作業系統所定義的預設起始頁面啟動
  - **新的索引標籤頁**: Microsoft Edge 會載入任何定義於**新的索引標籤頁面 URL**設定
  - **最後一個工作階段的頁面**：Microsoft Edge 會載入最後一個工作階段頁面 
  - **自訂起始畫面**：Microsoft Edge 會載入 IT 系統管理員所定義的起始頁面
- **使用者可變更起始畫面**：[允許] 可讓使用者變更起始頁面。 系統管理員可以使用 `EdgeHomepageUrls` 輸入使用者在開啟 Microsoft Edge 時預設看到的起始畫面。 [未設定] 會封鎖使用者變更起始畫面。
- **新索引標籤頁面 URL**：輸入要在新的索引標籤上開啟的 URL。 例如，輸入 `https://www.bing.com`。
- **在 [新索引標籤] 頁面上開啟 Web 內容**：選擇 [封鎖] 以阻止 Microsoft Edge 在新索引標籤上開啟網站。當封鎖時，會以空白頁開啟新的索引標籤。 [未設定] 會使用裝置上的 OS 預設行為，這可能會允許使用者選擇顯示的內容。
- **[首頁] 按鈕**：選擇選取 [首頁] 按鈕時，會發生什麼事。 選項包括：
  - **起始畫面**：開啟您為 [啟動 Microsoft Edge 並顯示] 設定選擇的選項
  - **新索引標籤頁面**：開啟您為 [新索引標籤頁面 URL] 設定選擇的選項
  - **自訂首頁按鈕 URL**：開啟您為 [首頁按鈕 URL] 設定選擇的選項
  - **隱藏首頁按鈕**：隱藏 [首頁] 按鈕
- **使用者可變更首頁按鈕**：[允許] 可讓使用者變更首頁按鈕。 使用者的變更覆寫任何的系統管理員設定，以 [首頁] 按鈕。 [未設定] 會使用裝置上的 OS 預設行為，這可能會禁止使用者變更系統管理員設定主畫面按鈕的方式。
- **顯示首次執行體驗頁面**：[封鎖] 會阻止您第一次執行 Microsoft Edge 時顯示簡介頁面。 這項功能可讓企業 (如註冊零輸出設定的組織) 封鎖這個頁面。 [未設定] 會顯示 [簡介] 頁面。
  - **首次執行體驗 URL**：輸入頁面 URL 以顯示使用者第一次執行 Microsoft Edge (僅限Windows 10 行動裝置版)。
- **在閒置時間後重新整理瀏覽器**： 輸入的瀏覽器重新整理之前，從 0 到 1440年的閒置分鐘數分鐘的時間。 預設值是`5`分鐘的時間。 當設定為`0`（零），瀏覽器不在閒置之後會重新整理。

  執行時，才可以使用這項設定[公開 InPrivate 瀏覽 (單一應用程式 kiosk)](#use-microsoft-edge-kiosk-mode)。

  CSP: [ConfigureKioskResetAfterIdleTimeout](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-configurekioskresetafteridletimeout)

- **快顯視窗**：選擇 [封鎖] 以停止瀏覽器中的快顯視窗。 僅適用於 Windows 10 Desktop。 [未設定] 允許網頁瀏覽器的快顯視窗。
- **將內部網路流量傳送到 Internet Explorer**：[允許] 讓使用者可在 Internet Explorer 而不是 Microsoft Edge 中開啟內部網路網站 (僅限 Windows 10 桌面版)。 [未設定] 允許使用者使用 Microsoft Edge。
- **企業模式網站清單位置**：輸入包含以企業模式開啟之網站清單的 URL。 使用者無法變更此清單。 僅適用於 Windows 10 Desktop。
- **在 Internet Explorer 中開啟網站時出現的訊息**：使用此設定將 Microsoft Edge 設定為在 Internet Explorer 11 中開啟網站之前顯示通知。 選項包括：
  - **未設定**：使用 OS 預設行為，這可能不會顯示訊息。
  - **顯示訊息，但不顯示在 Microsoft Edge 中開啟網站的選項**：在 IE 中開啟網站時顯示訊息。 在 IE 中開啟網站。 無法在 Microsoft Edge 中開啟網站。
  - **在 Microsoft Edge 中開啟網站時顯示訊息**：在 IE 中開啟網站時顯示訊息。 此訊息包含**繼續使用 Microsoft Edge** 連結，因此使用者可以選擇 Microsoft Edge 而非 IE。

  > [!IMPORTANT]
  > 此設定會要求您啟用 [設定企業模式網站清單] 設定、[將所有內部網路網站傳送到 Internet Explorer 11] 設定或兩者。

- **Microsoft 相容性清單**：[封鎖] 可防止 Microsoft Edge 中的 Microsoft 相容性清單。 Microsoft 的此清單可協助 Microsoft Edge 正確顯示具有已知的相容性問題的網站。 [未設定] 允許使用 Microsoft 相容性清單。
- **預先載入起始頁面和新的索引標籤頁面**：選擇 [封鎖] 以防止 Microsoft Edge 預先載入起始頁面和新的索引標籤頁面。 預先載入可將啟動 Microsoft Edge，以及載入新的索引標籤的時間降至最低。[未設定] 會使用 OS 預設行為，這可能表示要預先載入這些頁面。
- **預先啟動起始頁面和新的索引標籤頁面**：選擇 [封鎖] 以防止 Microsoft Edge 預先啟動起始頁面和新的索引標籤頁面。 預先啟動有助於 Microsoft Edge 的效能，並將啟動 Microsoft Edge 所需的時間降至最低。 [未設定] 會使用 OS 預設行為，這可能表示要預先啟動這些頁面。

### <a name="favorites-and-search"></a>我的最愛和搜尋

- **我的最愛列**：選擇在任何 Microsoft Edge 頁面上 [我的最愛] 列的內容。 選項包括：
  - [未設定]：使用 OS 預設行為，這可能表示要在所有頁面上隱藏 [我的最愛] 列。 使用者可以變更此設定。
  - **隱藏**：在所有頁面上隱藏 [我的最愛] 列。 使用者無法變更此設定。
  - **顯示**：在所有頁面上顯示 [我的最愛] 列。 使用者無法變更此設定。
- **我的最愛清單**：將 URL 清單新增至我的最愛檔案。 例如：新增 `http://contoso.com/favorites.html`。
- **限制我的最愛變更**：[封鎖] 以防止使用者新增、匯入、排序或編輯我的最愛清單。 [未設定] 會使用 OS 預設值，這可能會允許使用者變更清單。
- **在 Microsoft 瀏覽器之間同步我的最愛 (僅限桌面版)**：[需要] 可強制 Windows 在 Internet Explorer 與 Microsoft Edge 之間同步我的最愛。 在瀏覽器之間共用對我的最愛的新增、刪除、修改及順序變更。  [未設定] 會使用 OS 預設值，這可能會讓使用者選擇在瀏覽器之間同步處理我的最愛。
- **預設搜尋引擎**：選擇裝置上的預設搜尋引擎。 使用者可以隨時變更此值。 選項包括：
  - 預設
  - Bing
  - Google
  - Yahoo
  - 自訂值
- **搜尋建議**：[未設定] 可讓您的搜尋引擎在您於網址列中輸入搜尋片語時建議網站。 [封鎖] 會防止此功能。
- **允許變更的搜尋引擎**:**是**（預設值） 可讓使用者加入新的搜尋引擎，或變更預設的搜尋引擎在 Microsoft Edge 中。 選擇**No**以防止使用者自訂的搜尋引擎。

  執行時，才可以使用這項設定[正常模式 (多應用程式 kiosk)](#use-microsoft-edge-kiosk-mode)。

  CSP: [AllowSearchEngineCustomization](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-allowsearchenginecustomization)

### <a name="privacy-and-security"></a>隱私權和安全性

- **InPrivate 瀏覽**：[封鎖] 防止使用者開啟 InPrivate 瀏覽工作階段。 [未設定] 允許此功能。
- **儲存瀏覽歷程記錄**：[封鎖] 防止 Microsoft Edge 儲存瀏覽歷程記錄。 [未設定] 允許儲存瀏覽歷程記錄。
- **在結束時清除瀏覽資料**：[需要] 當使用者結束 Microsoft Edge 時，清除歷程記錄和瀏覽資料。 [未設定] 會使用 OS 預設值，這可能會快取瀏覽資料。
- **在使用者裝置之間同步處理瀏覽器設定**：選擇在裝置之間同步處理瀏覽器設定的方式。 選項包括：
  - **允許**：允許在使用者裝置之間同步處理 Microsoft Edge 瀏覽器設定
  - **封鎖並啟用使用者覆寫**：防止在使用者裝置之間同步處理 Microsoft Edge 瀏覽器設定。 使用者可以覆寫此設定。
  - **封鎖**：阻止在使用者裝置之間同步處理 Microsoft Edge 瀏覽器設定。 使用者無法覆寫此設定。
- **密碼管理員**：[封鎖] 會停用 Microsoft Edge [密碼管理員] 功能。 [未設定] 允許此功能。
- **Cookis**：選擇網頁瀏覽器上處理 cookie 的方式。 選項包括：
  - **允許**：Cookie 會儲存在裝置上。
  - **封鎖所有 Cookie**：Cookie 不會儲存在裝置上。
  - **只封鎖第三方 Cookie**：協力廠商或合作對象 Cookie 不會儲存在裝置上。
- **自動填寫**：[封鎖] 會停用裝置上 Safari 中的 [自動填寫] 功能。 [未設定] 允許使用者變更瀏覽器中的自動完成設定 (僅限 Windows 10 桌面版)。
- **傳送不追蹤標頭**：[未設定] 要求裝置向要求追蹤資訊的網站傳送不追蹤標頭 (建議選項)。 選擇 [封鎖] 以防止裝置傳送這些標頭，從而允許網站追蹤使用者。
- **WebRtc localhost IP 位址**：[封鎖] 會防止於使用 Web RTC 通訊協定撥打電話時，顯示使用者的 localhost IP 位址。 [未設定] 可讓使用者在使用此通訊協定通話時顯示 localhost IP 位址。
- **動態磚資料收集**：選擇 [封鎖] 以阻止當網站從 Microsoft Edge 釘選到 [開始] 功能表時，Windows 從動態磚收集資訊。 [未設定] 允許收集這項資訊。
- **使用者可以覆寫憑證錯誤**：[封鎖] 會防止使用者存取具有 SSL 或 TLS 錯誤的網站。 [未設定] 允許使用者存取這些網站。

### <a name="additional"></a>Additional

- **Microsoft Edge 瀏覽器 （僅限行動裝置）**： 選擇**區塊**以防止在裝置上使用 Microsoft Edge。 如果您封鎖 Microsoft Edge，則個別設定僅適用於桌面版。 [未設定] 允許在裝置上使用 Microsoft Edge 網頁瀏覽器。
- **網址列下拉式清單 (僅限桌面版)**：[封鎖] 會阻止 Microsoft Edge 在您鍵入時，於下拉式清單中顯示建議清單。 此選項有助於將 Microsoft Edge 與 Microsoft 服務之間的網路頻寬用量降到最低。 [未設定] 允許 Microsoft Edge 顯示一份建議清單。
- **全螢幕**：選擇 [封鎖] 以防止 Microsoft Edge 僅顯示網頁內容，並隱藏 Microsoft Edge (全螢幕模式)。 [未設定] 會使用 OS 預設值，可使用全螢幕模式的 Microsoft Edge。
- **關於旗標**：[封鎖] 會防止終端使用者存取 Microsoft Edge 中包含開發人員和實驗性設定的 `about:flags` 頁面。 [未設定] 會使用 OS 預設值，這可能會允許存取 `about:flags` 頁面。
- **開發人員工具**：[封鎖] 會防止終端使用者開啟 Microsoft Edge 開發人員工具。 [未設定] 允許使用者開啟開發人員工具。
- **延伸模組**：[未設定] 允許終端使用者在裝置上安裝 Microsoft Edge 延伸模組。 [封鎖] 會防止安裝。
- **正在側載開發人員延伸模組**：[封鎖] 會防止 Microsoft Edge 進行側載，側載會使用**載入延伸模組**功能安裝及執行未經驗證的擴充功能。 [未設定] 會使用 OS 預設值，這可能會允許側載。
- **必要的延伸模組**：選擇 Microsoft Edge 中的終端使用者無法關閉哪些擴充功能。 輸入套件系列名稱，然後選取 [新增]。 [尋找套件系列名稱 (PFN)](https://docs.microsoft.com/sccm/protect/deploy-use/find-a-pfn-for-per-app-vpn) 清單會提供一些指引。

  您也可以**匯入** CSV 檔案，其中包含套件系列名稱。

- **JavaScript**：選擇 [封鎖] 會防止在裝置上執行瀏覽器中的 JavaScript。 [未設定] 允許在 Microsoft Edge 瀏覽器中執行 JavaScript 等指令碼。

## <a name="network-proxy"></a>網路 Proxy

- **自動偵測 Proxy 設定**：啟用時，裝置會嘗試尋找 PAC 指令碼的路徑。
- **使用 Proxy 指令碼**：選取此選項以輸入用於設定 Proxy 伺服器的 PAC 指令碼路徑。
  - **設定指令碼位址 URL**：輸入您想要用於設定 Proxy 伺服器的 PAC 指令碼 URL。
- **使用手動 Proxy 伺服器**：選取此選項以手動輸入 Proxy 伺服器資訊。
  - **位址**：輸入 Proxy 伺服器的名稱或 IP 位址。
  - **連接埠號碼**：輸入 Proxy 伺服器的連接埠號碼。
  - **Proxy 例外狀況**：輸入任何不得使用 Proxy 伺服器的 URL。 請使用分號來分隔每個項目。
  - **為本機位址略過 Proxy 伺服器**：如果您不想要針對內部網路上的本機位址使用 Proxy 伺服器，請啟用此選項。

## <a name="password"></a>密碼

- **密碼**：需要使用者輸入密碼才可存取該裝置。
  - **必要的密碼類型**：指定密碼必須為數字還是英數字元。
  - **密碼長度下限**：僅適用於 Windows 10 行動裝置版。
  - **登入失敗幾次後即抹除裝置**：若為執行 Windows 10 的裝置︰如果裝置已啟用 BitLocker，將會在登入失敗達您所指定的次數時置於 BitLocker 復原模式。 如果裝置未啟用 BitLocker，便不會套用此設定。 若為執行 Windows 10 行動裝置版的裝置︰登入失敗達到您輸入的次數時，就會抹除裝置。
  - **沒有活動最久幾分鐘後鎖定螢幕**：指定裝置必須處於閒置狀態多久的時間，才會鎖住螢幕。
  - **密碼到期 (天)**：指定在多久之後必須變更該裝置的密碼。
  - **避免重複使用以前用過的密碼**：指定裝置記憶先前使用過的密碼數目。
  - **裝置從閒置狀態回復時需要密碼 (僅限行動裝置)**：指定使用者必須輸入密碼才能解除鎖定裝置 (僅限 Windows 10 行動裝置版)。
  - **簡單密碼**：可讓您使用 1111 和 1234 等簡單密碼。 這項設定也會允許或封鎖使用 Windows 圖片密碼。

## <a name="per-app-privacy-exceptions"></a>個別應用程式的隱私權例外狀況

您可以新增隱私權行為應該與您在「預設原則」中所定義之隱私權行為不同的應用程式。

- **套件名稱**：應用程式套件系列名稱。
- **應用程式名稱**：應用程式的名稱。

### <a name="exceptions"></a>例外狀況

- **帳戶資訊**：定義此應用程式能否存取使用者名稱、圖片及其他連絡人資訊。
- **背景應用程式**：定義此應用程式能否在背景執行。
- **行事曆**：定義此應用程式能否存取行事曆。
- **通話記錄**：定義此應用程式能否存取我的通話記錄。
- **相機**：定義此應用程式能否存取網路攝影機。
- **連絡人**：定義此應用程式能否存取連絡人。
- **電子郵件**：定義此應用程式能否存取及傳送電子郵件。
- **位置**：定義此應用程式能否存取位置資訊。
- **訊息中心**：定義此應用程式能否讀取或傳送文字或 MMS 訊息。
- **麥克風**：定義此應用程式能否使用麥克風。
- **動作**：定義此應用程式能否存取裝置動作資訊。
- **通知**：定義此應用程式能否存取通知。
- **電話**：定義此應用程式能否存取手機。
- **無線電**：有些應用程式會在您的裝置上使用無線電波 (例如，藍牙) 來傳送及接收資料，因此必須開啟或關閉這些無線電波。 定義此應用程式能否控制這些無線電波。
- **工作**：定義此應用程式能否存取您的工作。
- **受信任的裝置**： 選擇此應用程式是否可以使用受信任的裝置。 受信任裝置是您已連線的硬體，或隨附於裝置的硬體。 例如，將電視、投影機等作為信任的裝置使用。
- **意見反應與診斷**：定義此應用程式能否存取診斷資訊。
- **與裝置同步** - 選擇此應用程式是否自動與未和該裝置直接配對的無線裝置共用及同步資訊。

## <a name="personalization"></a>個人化

- **桌面背景圖片 URL (僅限桌面版)**：輸入要作為 Windows 桌面桌布使用之 JPEG 格式圖片的 URL。 使用者無法變更此圖片。

## <a name="printer"></a>印表機

- **印表機**：已新增的本機印表機清單。
- **預設印表機**：設定預設印表機。
- **使用者存取新增新印表機**：允許或封鎖使用本機印表機。

## <a name="privacy"></a>隱私權

- **輸入個人化**：不允許為 Cortana、聽寫或 Microsoft 網上商店應用程式使用雲端式語音服務。 如果您允許使用這些服務，Microsoft 可能會收集語音資料來改進服務。
- **自動接受配對及隱私權使用者同意提示**：允許 Windows 在執行應用程式時，自動接受配對及隱私權同意訊息。
- **發佈使用者活動**： [封鎖] 會防止共用體驗以及在工作切換器中探索最近使用的資源。
- **僅限本機活動**： [封鎖] 會防止共用體驗，以及僅根據本機活動，在工作切換器中探索最近使用的資源。

您可以設定可供裝置上所有應用程式存取的資訊。 您也可以使用**個別應用程式隱私權例外狀況**，以個別應用程式為基礎來定義例外狀況。

### <a name="exceptions"></a>例外狀況

- **帳戶資訊**：定義此應用程式能否存取使用者名稱、圖片及其他連絡人資訊。
- **背景應用程式**：定義此應用程式能否在背景執行。
- **行事曆**：定義此應用程式能否存取行事曆。
- **通話記錄**：定義此應用程式能否存取我的通話記錄。
- **相機**：定義此應用程式能否存取網路攝影機。
- **連絡人**：定義此應用程式能否存取連絡人。
- **電子郵件**：定義此應用程式能否存取及傳送電子郵件。
- **位置**：定義此應用程式能否存取位置資訊。
- **訊息中心**：定義此應用程式能否讀取或傳送文字或 MMS 訊息。
- **麥克風**：定義此應用程式能否使用麥克風。
- **動作**：定義此應用程式能否存取裝置動作資訊。
- **通知**：定義此應用程式能否存取通知。
- **電話**：定義此應用程式能否存取手機。
- **無線電**：有些應用程式會在您的裝置上使用無線電波 (例如，藍牙) 來傳送及接收資料，因此必須開啟或關閉這些無線電波。 定義此應用程式能否控制這些無線電波。
- **工作**：定義此應用程式能否存取您的工作。
- **受信任的裝置**： 選擇此應用程式是否可以使用受信任的裝置。 受信任裝置是您已連線的硬體，或隨附於裝置的硬體。 例如，將電視、投影機等作為信任的裝置使用。
- **意見反應與診斷**：選擇此應用程式能否存取診斷資訊。
- **與裝置同步** - 定義此應用程式能否自動與未和此電腦、平板電腦或手機直接配對的無線裝置共用及同步資訊。

## <a name="projection"></a>投影

- **來自無線顯示器接收器的使用者輸入**：封鎖來自無線顯示器接收器的使用者輸入。
- **投影到此電腦**：阻止其他裝置尋找該電腦以進行投影。
- **要求提供 PIN 以進行配對**：於連線至投影裝置時要求 PIN。

## <a name="reporting-and-telemetry"></a>報告與遙測

- **共用使用方式資料**：選擇提交診斷資料的層級。 選項包括：
  - 安全性
  - 基本
  - 增強
  - 完整
- **將Microsoft Edge瀏覽數據發送到Microsoft 365 Analytics** ：若要使用這項功能，請將 [共用使用方式資料] 設定為 [增強] 或是 [完整]。 此功能控制 Microsoft Edge 針對具有設定商業識別碼的企業裝置傳送至 Microsoft 365 Analytics 的資料。 選項包括：
  - [未設定]：會使用 OS 預設值，這可能不會傳送任何瀏覽歷程記錄資料
  - **僅傳送內部網路資料**：允許系統管理員傳送內部網路資料歷程記錄
  - **僅傳送網際網路資料**：允許系統管理員傳送網際網路資料歷程記錄
  - **傳送內部網路與網際網路資料**：允許系統管理員傳送內部網路與網際網路資料歷程記錄
- **遙測 Proxy 伺服器**：輸入要用來轉送「已連線使用者體驗與遙測」要求 (使用安全通訊端層 (SSL) 連線) 之 Proxy 伺服器的完整網域名稱 (FQDN) 或 IP 位址。 此設定的格式是*伺服器*:*連接埠*。 若具名 Proxy 失敗，或若啟用此原則時未輸入 Proxy，則不傳送已連線使用者體驗與遙測資料，並將此資料留在本機裝置上。

  範例格式：

  ```
  IPv4: 192.246.246.106:100
  IPv6: [2001:4898:4010:4013:95c1:a8b2:953c:c633]:100
  FQDN: www.contoso.com:345
  ```

## <a name="search"></a>搜尋

- **安全搜尋 (僅限行動裝置)**：控制 Cortana 在搜尋結果中篩選成人內容的方式。 您可以選取 [嚴格]、[普通]，或允許使用者自行選擇設定。
- **在 [搜尋] 中顯示網頁搜尋結果**：封鎖或允許網頁結果顯示在對裝置進行的搜尋中。

## <a name="start"></a>開始

- **[開始] 功能表配置**：若要自訂電腦裝置上的 [開始] 功能表，您可以上傳 XML 檔案，其中包含您的自訂項目 (包括列出應用程式的順序) 及其他內容。 使用者無法變更您輸入的 [開始] 功能表配置。
- **將網站釘選為 [開始] 功能表中的磚**：從 Microsoft Edge 匯入影像，作為電腦裝置 Windows [開始] 功能表中的連結顯示。
- **從工作列取消釘選應用程式**：選擇 [封鎖] 以阻止使用者從工作列取消釘選應用程式。
- **快速切換使用者**：選擇 [封鎖] 以避免同時登入的使用者未經登出就在使用者之間進行切換。
- **最常使用的應用程式**：選擇 [封鎖] 以隱藏最常使用的應用程式，使其無法顯示在 [開始] 功能表中。 它也會停用「設定」應用程式中相對應的切換。
- **最近新增的應用程式**：選擇 [封鎖] 以隱藏最近新增的應用程式，使其無法顯示在 [開始] 功能表中。 它也會停用「設定」應用程式中相對應的切換。
- **開始畫面模式**：選擇開始畫面的顯示方式。 選擇將它顯示為 [全螢幕] 或 [非全螢幕]。
- **捷徑清單中最近開啟的項目**：選擇 [封鎖] 以隱藏最近的捷徑清單，使其無法顯示在 [開始] 功能表和工作列中。 它也會停用「設定」應用程式中相對應的切換。
- **應用程式清單**：選擇 [設定] 應用程式的顯示方式。 選項包括： 
  - 摺疊
  - 摺疊及停用「設定」應用程式 
  - 移除且停用「設定」應用程式
- **電源按鈕**：選擇 [封鎖] 以隱藏電源按鈕，使其無法顯示在 [開始] 功能表中。
- **使用者磚**：選擇 [封鎖] 以隱藏使用者磚，使其無法顯示在 [開始] 功能表中。
  - **鎖定**：選擇 [封鎖] 以隱藏 `Lock` 選項，使其無法顯示在 [開始] 功能表的使用者磚中。
  - **登出**：選擇 [封鎖] 以隱藏 `Sign out` 選項，使其無法顯示在 [開始] 功能表的使用者磚中。
- **關機**：選擇 [封鎖] 以隱藏 `Update and shut down` 和 `Shut down` 選項，使其無法顯示在 [開始] 功能表的電源按鈕中。
- **睡眠**：選擇 [封鎖] 以隱藏 `Sleep` 選項，使其無法顯示在 [開始] 功能表的電源按鈕中。
- **休眠**：選擇 [封鎖] 以隱藏 `Hibernate` 選項，使其無法顯示在 [開始] 功能表的電源按鈕中。
- **切換帳戶**：選擇 [封鎖] 以隱藏 `Switch account`，使其無法顯示在 [開始] 功能表的使用者磚中。
- **重新啟動選項**：選擇 [封鎖] 以隱藏 `Update and restart` 和 `Restart` 選項，使其無法顯示在 [開始] 功能表的電源按鈕中。
- **[開始] 上的 [文件]**：隱藏或顯示 Windows [開始] 功能表中的 [文件] 資料夾。
- **[開始] 上的 [下載]**：隱藏或顯示 Windows [開始] 功能表中的 [下載] 資料夾。
- **[開始] 上的 [檔案總管]**：隱藏或顯示 Windows [開始] 功能表中的 [檔案總管] 應用程式。
- **[開始] 上的 [家用群組]**：隱藏或顯示 Windows [開始] 功能表中的 [家用群組] 資料夾。
- **[開始] 上的 [音樂]**：隱藏或顯示 Windows [開始] 功能表中的 [音樂] 資料夾。
- **[開始] 上的 [網路]**：隱藏或顯示 Windows [開始] 功能表中的 [網路] 資料夾。
- **[開始] 上的 [個人] 資料夾**：隱藏或顯示 Windows [開始] 功能表中的 [個人] 資料夾。
- **[開始] 上的 [圖片]**：隱藏或顯示 Windows [開始] 功能表中的 [圖片] 資料夾。
- **[開始] 上的 [設定]**：隱藏或顯示 Windows [開始] 功能表中的 [設定] 應用程式。
- **[開始] 上的 [影片]**：隱藏或顯示 Windows [開始] 功能表中的 [影片] 資料夾。

## <a name="windows-defender-smart-screen"></a>Windows Defender SmartScreen 篩選工具

- **適用於 Microsoft Edge 的 SmartScreen 篩選工具**：啟用 Microsoft Edge SmartScreen 以存取網站和檔案下載。
- **惡意網站存取**：禁止使用者略過 Windows Defender SmartScreen 篩選工具警告，並防止他們進入網站。
- **未經驗證的檔案下載**：禁止使用者略過 Windows Defender SmartScreen 篩選工具警告，並防止他們下載未經驗證的檔案。

## <a name="windows-spotlight"></a>Windows 焦點

- **Windows 焦點**：使用此設定可封鎖 Windows 10 裝置上的所有 Windows 焦點功能。 如果您封鎖這項設定，則無法使用下列設定：
  - **鎖定畫面上的 Windows 焦點**：阻止 Windows 焦點在裝置鎖定畫面上顯示資訊。
  - **Windows 焦點中的第三方建議**：阻止 Windows 焦點建議不是由 Microsoft 發佈的內容。
  - **消費者功能**：讓您封鎖如 [開始] 功能表建議和成員資格通知等消費者功能。
  - **Windows 提示**：讓您封鎖快顯提示於 Windows 中顯示。
  - **控制中心的 Windows 焦點**：封鎖 Windows 焦點建議 (如新的應用程式或安全性內容)，使其不要出現在 Windows 控制中心。
  - **Windows 焦點個人化**：阻止 Windows 焦點根據裝置的使用方式將結果個人化。
  - **Windows 歡迎使用體驗**：封鎖 Windows 歡迎使用體驗，該體驗會顯示有關新功能或更新功能的使用者資訊。

## <a name="windows-defender-antivirus"></a>Windows Defender 防毒軟體

- **即時監視**：啟用惡意程式碼、間諜軟體和其他垃圾軟體的即時掃描。
- **行為監視**：讓 Defender 在裝置上檢查某些已知模式的可疑活動。
- **網路檢查系統 (NIS)**：NIS 可協助保護裝置免於遭受網路型入侵。 它會使用 Microsoft Endpoint Protection 中心提供之已知弱點的病毒碼，協助偵測及阻擋惡意流量。
- **掃描所有下載**：控制 Defender 是否掃描從網際網路下載的所有檔案。
- **掃描 Microsoft Web 瀏覽器中所載入的指令碼**：讓 Defender 可掃描 Internet Explorer 中所使用的指令碼。
- **Defender 的使用者存取**：控制是否對使用者隱藏 Windows Defender 使用者介面。 變更此設定後，要在使用者電腦下次重新啟動時才會生效。
- **病毒碼更新間隔 (小時)**：輸入 Defender 查看是否有新病毒碼檔案的間隔。
- **監視檔案與程式活動**：允許 Defender 監視裝置上的檔案和程式活動。
- **多少天之後刪除隔離的惡意程式碼**： 繼續追蹤已解決的惡意程式碼的輸入，這讓您可以手動檢查先前受影響裝置的天數。 如果您將此天數設為 **0**，則惡意程式碼會保留在隔離資料夾中且不會自動移除。
- **掃描期間的 CPU 使用率限制**：限制掃描可以使用的 CPU 數量 (從 **1** 到 **100**)。
- **掃描封存檔**：允許 Defender 掃描封存的檔案，例如 .zip 或 .cab 檔案。
- **掃描內送郵件訊息**：允許 Defender 在電子郵件訊息到達裝置時加以掃描。
- **在完整掃描期間掃描抽取式磁碟機**：讓 Defender 可掃描像是 USB 隨身碟之類的抽取式磁碟機。
- **在完整掃描期間掃描對應的網路磁碟機**：讓 Defender 可掃描對應網路磁碟機上的檔案。
  如果磁碟機上的檔案是唯讀，則 Defender 無法移除在其中發現的任何惡意程式碼。
- **掃描從網路資料夾中開啟的檔案**：讓 Defender 在共用網路磁碟機上掃描檔案 (例如，從 UNC 路徑存取的檔案)。 如果磁碟機上的檔案是唯讀，則 Defender 無法移除在其中發現的任何惡意程式碼。
- **雲端保護**：允許或封鎖 Microsoft Active Protection Service 從您管理的裝置接收惡意程式碼活動的相關資訊。 這項資訊可在未來改善服務。
- **在提交範例之前提示使用者**：控制可能需要進一步分析的潛在惡意檔案，是否自動傳送給 Microsoft。
- **執行每日快速掃描時間**： 選擇要執行每日快速掃描。 **未設定**不會執行每日掃描。 如果您想要更多自訂，設定**要執行的系統掃描類型**設定。

  [Defender ScheduleQuickScanTime CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-schedulequickscantime)
- **要執行的系統掃描類型**： 排程系統掃描，包括層級的掃描，以及日期和時間來執行掃描。 選項包括：
  - **未設定**： 不排程系統掃描的裝置上。 使用者可以手動執行掃描為視需要或想在其裝置上。
  - **停用**： 停用裝置上的掃描任何系統。 如果您將掃描裝置的協力廠商防毒解決方案，請選擇這個選項。
  - **快速掃描**： 探討常見的位置，可能有惡意程式碼註冊，例如登錄機碼，且已知 Windows 啟動資料夾。
    - **排定的日期**： 選擇要執行掃描的日期。
    - **排定的時間**： 選擇要執行掃描。
  - **完整掃描**： 探討常見的位置，可能有惡意程式碼已經註冊，並也會掃描每個檔案和裝置上的資料夾。
    - **排定的日期**： 選擇要執行掃描的日期。
    - **排定的時間**： 選擇要執行掃描。

  這項設定可能會和衝突**執行每日快速掃描時間**設定。 一些建議：

  - 若要執行每日快速掃描，設定**執行每日快速掃描時間**設定。
  - 執行每日快速掃描和完整掃描每週，然後設定**時間來執行每日快速掃描**，並設定**要執行的系統掃描類型**以完整掃描的日期和時間。
  - 未設定**時間來執行每日快速掃描**使用同時設定**要執行的系統掃描的型別**設定為**快速掃描**。 這些設定可能會發生衝突，並可能不會執行掃描。
  - 若要執行快速掃描每個星期二，上午 6，設定**要執行的系統掃描類型**設定。

  [Defender ScanParameter CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-scanparameter)  
  [Defender ScheduleScanDay CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-schedulescanday)  
  [Defender ScheduleScanTime CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-schedulescantime)

- **偵測潛在的不必要應用程式**：選擇 Windows 用以偵測潛在的不必要應用程式的保護層級：
  - **封鎖**
  - **稽核**：如需更多潛在的垃圾應用程式的詳細資訊，請參閱[偵測和封鎖潛在的垃圾應用程式](https://docs.microsoft.com/windows/threat-protection/windows-defender-antivirus/detect-block-potentially-unwanted-apps-windows-defender-antivirus)。
- **對所偵測到惡意程式碼威脅採取的動作**：選擇您希望 Defender 針對它所偵測到每種威脅等級 (低、中、高及嚴重) 所採取的動作。 選項包括：
  - **清除**
  - **隔離**
  - **移除**
  - **允許**
  - **使用者定義**
  - **封鎖**

### <a name="windows-defender-antivirus-exclusions"></a>Windows Defender 防毒軟體排除

- **不進行掃描和即時保護的檔案和資料夾**：將一或多個 **C:\Path** 或 **%ProgramFiles%\Path\filename.exe** 等檔案與資料夾，新增至排除清單。 任何即時或已排程的掃描都不會包含這些檔案和資料夾。
- **不進行掃描和即時保護的副檔名**：新增一或多個檔案副檔名，像是 **jpg** 或 **txt** 至排除清單中。 任何即時掃描或排定的掃描，都不會包含有這些副檔名的任何檔案。
- **排除不進行掃描和即時保護的程序** - 新增一或多個類型為 **.exe**、**.com** 或 **.scr** 等處理序至排除清單中。 任何即時或已排程的掃描都不會包含這些處理序。

## <a name="next-steps"></a>後續步驟

如需每項設定的其他技術詳細資料，以及支援哪些 Windows 版本，請參閱 [Windows 10 Policy CSP Reference](https://docs.microsoft.com/windows/client-management/mdm/policy-configuration-service-provider) (Windows 10 原則 CSP 參考)

---
# required metadata

title: Microsoft Intune 的 Windows 10 原則設定 | Microsoft Intune
description:
keywords:
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 00a602d9-b339-4fd8-ab70-defbf6686855

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Microsoft Intune 的 Windows 10 原則設定

使用本主題中所列的原則設定，以協助您進行已註冊之 Windows 10 Desktop 和 Windows 10 行動裝置的設定。

## 一般組態原則設定

使用 Windows 10 的 Microsoft 一般組態原則來設定已註冊之 Windows 10 Desktop 和 Windows 10 行動裝置的一般設定：


### 密碼

|設定名稱|詳細資料|Windows 10 Desktop|Windows 10 Mobile|
|----------------|----------------------|---------------------|
|**需要密碼才可解除鎖定裝置**|支援的裝置上需要的密碼。|是|是|
|**所需的密碼類型**|指定必要密碼的類型，例如只可包含數字，或必須是英數字元等等|是|是|
|需要的密碼類型 - 最小字元集數|字元集分為小寫字母、大寫字母、數字與符號四種。 此設定指定密碼中必須包含幾種不同的字元集。|是|是|
|**密碼長度下限**|指定裝置密碼必須包含的字元數目下限。|否|是|
|**抹除裝置前允許的重複登入失敗次數**|如果登入嘗試失敗是這個數目即抹除裝置。|是|是|
|**在停止活動幾分鐘後關閉螢幕**|指定裝置必須閒置多久的時間，才會鎖定螢幕。|是|是|
|**密碼到期 (天數)**|指定在多久之後必須變更該裝置的密碼。|是|是|
|**記住密碼歷程記錄**|指定是否要限制使用者建立先前使用過的密碼。|是|是|
|記住密碼歷程記錄 - 不得重複使用以前用過的密碼|指定裝置記憶的先前已使用密碼數目。|是|是|
|**允許圖片密碼和 PIN**|可讓您在圖片上使用簡單的手勢，或使用簡單 PIN 碼進行登入。|是|否|
|**當裝置從閒置狀態返回時，需要密碼。**|如果已啟用，使用者必須輸入密碼將裝置從閒置狀態解除鎖定。|否|是|

### 加密

|設定名稱|詳細資料|Windows 10 Desktop|Windows 10 Mobile|
|----------------|----------------------|---------------------|
|**在行動裝置上要求加密**|在目標裝置上啟用加密。|否|是|

### 系統

|設定名稱|詳細資料|Windows 10 Desktop|Windows 10 Mobile|
|----------------|----------------------|---------------------|
|**允許螢幕擷取**|讓使用者擷取裝置螢幕做為映像。|否|是|
|**允許手動取消註冊**|可讓使用者從裝置手動刪除工作場所帳戶。|是|是|
|**允許手動安裝根憑證**|指定使用者是否可以手動安裝根憑證|否|是|
|**允許將診斷與使用狀況資料傳送給 Microsoft**|決定從裝置傳送到 Microsoft 的診斷和使用資料量。<br>否 - 沒有資料會傳送到 Microsoft<br>基本 - 裝置只會傳送有限的資訊給 Microsoft<br>增強 - 將增強的診斷資料傳送給 Microsoft<br>完整 (建議) - 傳送和增強相同的資料，再加上裝置狀態的相關額外資料|是|是|


### 帳戶和同步處理

|設定名稱|詳細資料|Windows 10 Desktop|Windows 10 Mobile|
|----------------|----------------------|---------------------|
|**允許 Microsoft 帳戶**|讓使用者建立 Microsoft 帳戶與裝置之間的關聯。|是|是|
|**允許手動新增非 Microsoft 帳戶**|讓使用者將電子郵件帳戶新增至未與 Microsoft 帳戶相關聯的裝置。|是|是|
|**允許同步處理 Microsoft 帳戶的設定**|允許裝置和應用程式設定與 Microsoft 帳戶相關聯，以在裝置之間進行同步處理。|是|是|

### 電子郵件設定

|設定名稱|詳細資料|Windows 10 Desktop|Windows 10 Mobile|
|----------------|----------------------|---------------------|
|**讓 Microsoft 帳戶變成 Windows Mail 應用程式的選用帳戶**|進行此設定以在 Windows Mail 中移除 Microsoft 帳戶的需求。|是|否|



### Microsoft Edge

|設定名稱|詳細資料|Windows 10 Desktop|Windows 10 Mobile|
|----------------|----------------------|---------------------|
|**允許網頁瀏覽器**|允許在裝置上使用 Edge 網頁瀏覽器。|否|是|
|**允許網址列中的搜尋建議**|在您輸入搜尋片語時導入您的搜尋引擎建議的網站。|是|是|
|**允許將內部網路流量傳送到 Internet Explorer**|讓使用者在 Internet Explorer 中開啟內部網路網站。|是|否|
|**允許不要追蹤**|設定 Edge 瀏覽器以傳送「不要追蹤」標頭給使用者造訪的網站。|是|是|
|**啟用 SmartScreen**|在裝置上啟用 SmartScreen 瀏覽器設定。|是|是|
|**允許動態指令碼處理**|允許在 Edge 瀏覽器中執行 Javascript 等指令碼。|是|是|
|**允許快顯視窗**|啟用或停用瀏覽器的快顯封鎖程式。|是|否|
|**允許 Cookie**|允許或停用 cookie。|是|是|
|**允許自動填入**|允許使用者變更瀏覽器中的自動完成設定。|是|否|
|**允許密碼管理員**|啟用或停用 Edge 密碼管理員功能。|是|是|
|**企業模式網站清單位置**|指定要尋找將在企業模式下開啟之網站清單的位置。 使用者無法編輯這份清單。|是|否|

### 應用程式

|設定名稱|詳細資料|Windows 10 Desktop|Windows 10 Mobile|
|----------------|----------------------|---------------------|
|**允許應用程式市集**|允許使用者存取裝置上的應用程式市集。|否|是|



### 行動電話通訊

|設定名稱|詳細資料|Windows 10 Desktop|Windows 10 Mobile|
|----------------|----------------------|---------------------|
|**允許數據漫遊**|存取資料時允許網路之間的漫遊。|是|是|
|**允許透過行動電話通訊使用 VPN**|控制裝置是否可以在連線到行動電話通訊網路時存取 VPN 連線。|是|是|
|**允許透過行動電話通訊進行 VPN 漫遊**|控制裝置是否可以在漫遊到行動電話通訊網路時存取 VPN 連線。|是|是|

### 硬體

|設定名稱|詳細資料|Windows 10 Desktop|Windows 10 Mobile|
|----------------|----------------------|---------------------|
|**允許相機**|指定是否可以使用裝置相機。|是|是|
|**允許卸除式存放裝置**|指定是否可以與裝置搭配使用 SD 卡等外部存放裝置。|是|是|
|**允許 Wi-Fi**|允許使用者使用裝置 Wi-Fi 功能。|否|是|
|**允許網際網路共用**|允許在裝置上使用網際網路連線共用。|是|是|
|**允許手動設定 Wi-Fi 組態**|控制使用者是否可以設定自己的 Wi-Fi 連線，或者是否只能使用由 Wi-Fi 設定檔設定的連線。|否|是|
|**允許自動連線到免費的 Wi-Fi 熱點**|讓裝置自動連線到免費 Wi-Fi 熱點並自動接受任何連線條款和條件。|是|是|
|**允許地理位置**|指定裝置是否可以使用定位服務資訊。|是|是|
|**允許 NFC**|允許裝置使用它的近距離無線通訊功能。|是|是|
|**允許藍芽**|啟用裝置上的藍芽功能。|是|是|
|**允許可透過藍牙搜尋的模式**|讓其他藍芽啟用的裝置探索此裝置。|是|是|
|**允許藍牙通知**|允許裝置透過藍牙接收廣告。|是|是|
|允許可透過藍牙連線的模式 重要： |Windows 10 已不再支援此設定，未來將會移除。|是|是|
|**允許重設手機**|控制使用者是否可以將其裝置重設為原廠值。|是|是|
|**允許 USB 連線**|控制裝置是否可以透過 USB 連接來存取外接式存放裝置。|是|是|
|**允許防竊模式**|設定是否啟用 Windows 防竊模式。|是|是|

### 功能

|設定名稱|詳細資料|Windows 10 Desktop|Windows 10 Mobile|
|----------------|----------------------|---------------------|
|**允許複製並貼上**|啟用或停用裝置上的複製和貼上。|否|是|
|**允許錄音**|啟用或停用裝置上的錄音功能。|否|是|
|**允許 Cortana**|啟用或停用 Cortana 語音助理。|是|是|
|**允許重要訊息中心通知**|在裝置鎖定畫面上啟用或停用重要訊息中心通知。|否|是|

### Defender

|設定名稱|詳細資料|Windows 10 Desktop|Windows 10 Mobile|
|-|-|
|**允許即時監視**|啟用惡意程式碼、間諜軟體和其他垃圾軟體的即時掃描。|是|否|
|**允許行為監視**|讓 Defender 在裝置上檢查某些已知模式的可疑活動。|是|否
|**啟用網路檢查系統**|網路檢查系統 (NIS) 可使用 Microsoft Endpoint Protection 中心提供的已知弱點簽章來協助偵測及阻擋惡意流量，以幫助保護電腦不受網路型入侵程式的影響。|是|否
|**掃描所有下載**|控制 Defender 是否掃描從網際網路下載的所有檔案。|是|否
|**允許指令碼掃描**|讓 Defender 掃描 Internet Explorer 中所使用的指令碼。|是|否
|**監視檔案和程式活動**|啟用此設定以允許 Defender 監視裝置上的檔案和程式活動。|是|否
|**追蹤已解決惡意程式碼的天數**|在您指定的天數內，讓 Defender 繼續追蹤已解決的惡意程式碼，讓您可以手動檢查先前受影響的裝置。 如果您將此天數設為 0，惡意程式碼會保留在「隔離」資料夾，而且不會自動移除。 |是|否
|**允許用戶端 UI 存取**|控制是否對使用者隱藏 Windows Defender 使用者介面。<br>變更此設定時，它會在下次重新啟動使用者的電腦時生效。|是|否
|**排程每日快速掃描**|讓您排程每天在您選取的時間進行快速掃描。|是|否
|**排程系統掃描**|讓您排程在您指定的日期和時間定期進行完整或快速系統掃描。|是|否
|**限制掃描期間的 CPU 使用量**|讓您限制允許掃描使用的 CPU 數量 (從 1 至 100)|是|否
|**掃描封存檔**|允許 Defender 掃描封存的檔案，例如 Zip 或 Cab 檔案。|是|否
|**掃描電子郵件訊息**|允許 Defender 在電子郵件訊息到達裝置時加以掃描。|是|否
|**掃描卸除式磁碟機**|讓 Defender 掃描 USB 隨身碟等卸除式磁碟機。|是|否
|**掃描對應的網路磁碟機**|讓 Defender 在對應的網路磁碟機上掃描檔案。<br>如果磁碟機上的檔案是唯讀，Defender 將無法移除在其中發現的任何惡意程式碼。|是|否
|**掃描從網路共用資料夾開啟的檔案**|讓 Defender 在共用網路磁碟機上掃描檔案 (比方說，從 UNC 路徑存取者。<br>如果磁碟機上的檔案是唯讀，Defender 將無法移除在其中發現的任何惡意程式碼。|是|否
|**簽章更新間隔**|指定 Defender 檢查新簽章檔案的間隔。|是|否
|**允許雲端保護**|允許或封鎖 Microsoft Active Protection Service 從您管理的裝置接收惡意程式碼活動的相關資訊。 此資訊未來可用於改善本服務。|是|否
|**提示使用者提交範例**|控制可能需要由 Microsoft 進一步分析以判斷其是否為惡意的檔案，是否自動傳送給 Microsoft。|是|否
|**執行掃描或使用即時保護時所要排除的檔案和資料夾**|將一或多個 C:\Path 或 %ProgramFiles%\Path\filename.exe 等檔案和資料夾新增至排除清單。 這些檔案和資料夾將不會包含在任何即時或已排程的掃描。|是|否
|**執行掃描或使用即時保護時所要排除的副檔名**|將一個或多個 jpg 或 txt 等副檔名新增至排除清單。 任何包含這些副檔名的檔案將不會包含在任何即時或已排程的掃描。|是|否
|**執行掃描或使用即時保護時所要排除的處理程序**|將一或多個 .exe、.com 或 .scr 等類型的處理程序新增至排除清單。 這些處理程序將不會包含在任何即時或已排程的掃描。|是|否| 


### 更新設定

|設定名稱|詳細資料|Windows 10 Desktop|Windows 10 Mobile|
|----------------|---------------|----------------------|---------------------|
|**允許自動更新**|啟用這項設定以允許自動更新。 然後，設定下列其中一項設定來控制更新行為：<br /><br />**通知下載**<br /><br />**在維護時間自動安裝**<br /><br />**在維護時間自動安裝並重新開機**<br /><br />在排程時間自動安裝並重新開機 注意︰選取這個選項時，您也可以進行下列設定：隱藏使用者通知和定義排程更新的安裝日期.|是|否|

## 自訂原則設定
使用適用於 Windows 10 和 Windows 10 Mobile 的 Microsoft Intune 自訂設定原則來部署 OMA-URI (開放行動聯盟的統一資源識別項) 設定，此設定可用來控制 Windows 10 和 Windows 10 Mobile 裝置上的功能。 這些是許多行動裝置製造商用來控制裝置功能的標準設定。

這項功能的目的是讓您部署無法使用 Intune 一般設定原則設定的 Windows 10 設定。 如需可使用這些原則進行設定之設定的資訊，請參閱[透過 Microsoft Intune 原則管理裝置上的設定和功能](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md).

如需您可以在註冊的 Windows 10 裝置上設定的 OMA-URI 設定清單，請參閱本主題稍後的適用於 Windows 10 裝置的自訂 URI 設定。

### 一般設定

|設定名稱|詳細資料|
    |----------------|--------------------|
    |**Name**|輸入原則的唯一名稱，有助於您在 Intune 主控台中識別該原則。|
    |**說明**|提供可給予原則概觀的說明，以及可協助您找到該說明的其他相關資訊。|

### OMA-URI 設定

|設定名稱|詳細資料|
    |--------|--------------------|
    |**設定名稱**|輸入 OMA-URI 設定的唯一名稱，協助您在設定清單中識別該設定。|
    |**設定說明**|提供可給予設定概觀的說明，以及可協助您找到該說明的其他相關資訊。|
    |**資料類型**|選取您要在其中指定這個 OMA-URI 設定的日期類型。 從下列選項進行選擇：<br /><br />-   **字串**<br />-   **字串 (XML)**<br />-   **日期和時間**<br />-   **整數**<br />-   **浮點數**<br />-   **布林值**|
    |**OMA-URI (區分大小寫)**|指定您想要提供設定的 OMA-URI。|
    |**值**|指定要與您先前指定之 OMA-URI 產生關聯的值。|


## 適用於 Windows 10 裝置的自訂 URI 設定
本主題列出您可以在 Microsoft Intune Windows 10 自訂原則中，針對 Windows 10 與 Windows 10 行動裝置設定的設定.


> [!NOTE]
> 在下表的 [支援]  欄中，使用下列值：
> 
> -   桌上型電腦 - 此設定只支援已向 Intune 註冊的 Windows 10 專業版和企業版電腦。
> -   行動裝置 - 此設定只支援 Windows 10 行動裝置版的裝置。
> -   兩者 - 此設定支援桌上型電腦和行動裝置。
> 
> 如果您想要使用 Windows 自訂 URI 原則，所有裝置都必須向 Intune 註冊。

### 原則

|原則名稱|支援|詳細資料|
|---------------|------------|-----------|
|**​允許自動更新**|桌面|URI 完整路徑： ./Vendor/MSFT/Policy/Config/Update/AllowAutoUpdate<br /><br />資料類型： 整數<br /><br />允許的值：0 - 5<br /><br />預設值： 1|
|**排程安裝日期**|兩者|URI 完整路徑： ./Vendor/MSFT/Policy/Config/Update/ScheduledInstallDay<br /><br />資料類型： 整數<br /><br />**允許的值：**<br /><br />0 - 每天。<br /><br />1 - 星期日<br /><br />2 - 星期一<br /><br />3 - 星期二<br /><br />4 - 星期三<br /><br />5 - 星期四<br /><br />6 - 星期五<br /><br />7 - 星期六<br /><br />預設值： 0|
|**排程安裝時間**|兩者|URI 完整路徑： ./Vendor/MSFT/Policy/Config/Update/ScheduledInstallTime<br /><br />資料類型： 整數<br /><br />允許的值：0 – 23 小時 (0 為午夜)<br /><br />預設值： 3|
|**DeviceLock/AllowIdleReturnWithoutPassword**|行動電話|URI 完整路徑： ./Vendor/MSFT/Policy/Config/DeviceLock/AllowIdleReturnWithoutPassword<br /><br />資料類型： 整數<br /><br />**允許的值：**<br /><br />0 - 使用者無法設定密碼寬限期計時器，並將值設定為「每次」<br /><br />1 - 使用者能夠設定密碼寬限期計時器<br /><br />預設值： 1|
|**WiFi/AllowWiFi**|行動電話|URI 完整路徑： ./Vendor/MSFT/Policy/Config/WiFi/AllowWiFi<br /><br />資料類型： 整數<br /><br />**允許的值：**<br /><br />0 - 不允許使用 Wi-Fi 連線.<br /><br />1 - 允許使用 Wi-Fi 連線.<br /><br />預設值： 1|
|**WiFi/AllowInternetSharing**|兩者|URI 完整路徑： ./Vendor/MSFT/Policy/Config/WiFi/AllowInternetSharing<br /><br />資料類型： 整數<br /><br />**允許的值：**<br /><br />0 - 不允許網際網路共用。<br /><br />1 - 允許網際網路共用。<br /><br />預設值： 1|
|**WiFi/AllowAutoConnectToWiFiSenseHotspots**|兩者|URI 完整路徑： ./Vendor/MSFT/Policy/Config/WiFi/AllowAutoConnectToWiFiSenseHotspots<br /><br />資料類型： 整數<br /><br />**允許的值：**<br /><br />0 - 不允許<br /><br />1 - 允許<br /><br />預設值： 1|
|**WiFi/AllowManualWiFiConfiguration**|行動電話|URI 完整路徑： ./Vendor/MSFT/Policy/Config/WiFi/AllowManualWiFiConfiguration<br /><br />資料類型： 整數<br /><br />**允許的值：**<br /><br />0 - 不允許在佈建的 MDM 外部使用 Wi-Fi 連線。<br /><br />1 - 允許在已經佈建的 MDM 外部加入新的網路 SSID。<br /><br />預設值： 1|
|**System/AllowLocation**|兩者|URI 完整路徑： ./Vendor/MSFT/Policy/Config/System/AllowLocation<br /><br />資料類型： 整數<br /><br />**允許的值：**<br /><br />0 - 不允許<br /><br />1 - 允許<br /><br />預設值： 1|
|**System/AllowTelemetry**|兩者|URI 完整路徑： ./Vendor/MSFT/Policy/Config/System/AllowTelemetry<br /><br />資料類型： 整數<br /><br />**允許的值：**<br /><br />0 - 不允許 (僅適用於企業版的設定)<br /><br />1 - 有限<br /><br />2 - 完整<br /><br />3 - 完整和診斷資訊<br /><br />預設值： 2|
|**System/AllowExperimentation**|兩者|URI 完整路徑： ./Vendor/MSFT/Policy/Config/System/AllowExperimentation<br /><br />資料類型： 整數<br /><br />**允許的值：**<br /><br />0 - 不允許<br /><br />1 - 只有設定<br /><br />2 - 設定和試驗<br /><br />預設值： 1|
|**Security/AntiTheftMode**|行動電話|URI 完整路徑： ./Vendor/MSFT/Policy/Config/Security/AntiTheftMode<br /><br />資料類型： 整數<br /><br />**允許的值：**<br /><br />0 - 不允許反竊取模式<br /><br />1 - 使用者喜好設定<br /><br />預設值： 1|
|**Connectivity/AllowUSBConnection**|行動電話|URI 完整路徑： ./Vendor/MSFT/Policy/Config/Connectivity/AllowUSBConnection<br /><br />資料類型： 整數<br /><br />**允許的值：**<br /><br />0 - 不允許<br /><br />1 - 允許<br /><br />預設值： 1|
|**System/AllowUserToResetPhone**|行動電話|URI 完整路徑： ./Vendor/MSFT/Policy/Config/System/AllowUserToResetPhone<br /><br />資料類型： 整數<br /><br />**允許的值：**<br /><br />0 - 不允許<br /><br />1 - 允許<br /><br />預設值： 1|
|**Connectivity/AllowCellularDataRoaming**|兩者|URI 完整路徑： ./Vendor/MSFT/Policy/Config/Connectivity/AllowCellularDataRoaming<br /><br />資料類型： 整數<br /><br />**允許的值：**<br /><br />0 - 不允許<br /><br />1 - 允許<br /><br />預設值： 1|
|**Connectivity/AllowVPNOverCellular**|兩者|URI 完整路徑： ./Vendor/MSFT/Policy/Config/Connectivity/AllowVPNOverCellular<br /><br />資料類型： 整數<br /><br />**允許的值：**<br /><br />0 - 不允許透過行動電話通訊的 VPN<br /><br />1 - VPN 可以使用包括行動電話在內的任何連線。<br /><br />預設值： 1|
|**Connectivity/AllowVPNRoamingOverCellular**|行動電話|URI 完整路徑： ./Vendor/MSFT/Policy/Config/Connectivity/AllowVPNRoamingOverCellular<br /><br />資料類型： 整數<br /><br />**允許的值：**<br /><br />0 - 不允許<br /><br />1 - 允許<br /><br />預設值： 1|
|**Connectivity/AllowVPNRoamingOverCellular**|行動電話|URI 完整路徑： ./Vendor/MSFT/Policy/Config/Connectivity/AllowVPNRoamingOverCellular<br /><br />資料類型： 整數<br /><br />**允許的值：**<br /><br />0 - 不允許<br /><br />1 - 允許<br /><br />預設值： 1|
|**Connectivity/AllowBluetooth**|兩者|URI 完整路徑： ./Vendor/MSFT/Policy/Config/Connectivity/AllowBluetooth<br /><br />資料類型： 整數<br /><br />**允許的值：**<br /><br />0 – 不允許使用者開啟藍芽。<br /><br />1 – 已保留。 使用者可以開啟和設定藍芽 (在 Windows Phone 8.1 for MDM、EAS、Windows 10 desktop 或 Windows 10 Mobile 中不支援)<br /><br />2 - 已允許。 使用者可以開啟並設定藍芽。<br /><br />預設值： 2|
|**Experience/AllowScreenCapture**|行動電話|URI 完整路徑： ./Vendor/MSFT/Policy/Config/Experience/AllowScreenCapture<br /><br />資料類型： 整數<br /><br />**允許的值：**<br /><br />0 - 不允許<br /><br />1 - 允許<br /><br />預設值： 1|
|**Experience/AllowTaskSwitcher**|行動電話|URI 完整路徑： ./Vendor/MSFT/Policy/Config/Experience/AllowTaskSwitcher<br /><br />資料類型： 整數<br /><br />**允許的值：**<br /><br />0 - 不允許<br /><br />1 - 允許<br /><br />預設值： 1|
|**Experience/AllowVoiceRecording**|行動電話|URI 完整路徑： ./Vendor/MSFT/Policy/Config/Experience/AllowVoiceRecording<br /><br />資料類型： 整數<br /><br />**允許的值：**<br /><br />0 - 不允許<br /><br />1 - 允許<br /><br />預設值： 1|
|**Experience/AllowSyncMySettings**|行動電話|URI 完整路徑： ./Vendor/MSFT/Policy/Config/Experience/AllowSyncMySettings<br /><br />資料類型： 整數<br /><br />**允許的值：**<br /><br />0 - 不允許漫遊<br /><br />1 - 允許漫遊<br /><br />預設值： 1|
|**Experience/AllowManualMDMUnenrollment**|兩者|URI 完整路徑： ./Vendor/MSFT/Policy/Config/Experience/AllowManualMDMUnenrollment<br /><br />資料類型： 整數<br /><br />**允許的值：**<br /><br />0 - 不允許<br /><br />1 - 允許<br /><br />預設值： 1|
|**Accounts/AllowMicrosoftAccountConnection**|兩者|URI 完整路徑： ./Vendor/MSFT/Policy/Config/Accounts/AllowMicrosoftAccountConnection<br /><br />資料類型： 整數<br /><br />**允許的值：**<br /><br />0 - 不允許<br /><br />1 - 允許<br /><br />預設值： 1|
|**Accounts/AllowAddingNonMicrosoftAccountsManually**|兩者|URI 完整路徑： ./Vendor/MSFT/Policy/Config/Accounts/AllowAddingNonMicrosoftAccountsManually<br /><br />資料類型： 整數<br /><br />**允許的值：**<br /><br />0 - 不允許<br /><br />1 - 允許<br /><br />預設值： 1|
|**Security/AllowManualRootCertificateInstallation**|行動電話|URI 完整路徑： ./Vendor/MSFT/Policy/Config/Security/AllowManualRootCertificateInstallation<br /><br />資料類型： 整數<br /><br />**允許的值：**<br /><br />0 - 不允許<br /><br />1 - 允許<br /><br />預設值： 1|
|**Security/AllowAddProvisioningPackages**|兩者|URI 完整路徑： ./Vendor/MSFT/Policy/Config/Security/AllowAddProvisioningPackages<br /><br />資料類型： 整數<br /><br />**允許的值：**<br /><br />0 - 不允許<br /><br />1 - 允許<br /><br />預設值： 1|
|**Search/DisableBackoff**|兩者|URI 完整路徑： ./Vendor/MSFT/Policy/Config/Search/DisableBackoff<br /><br />資料類型： 整數<br /><br />**允許的值：**<br /><br />**0**<br /><br />**1**<br /><br />預設值： 0|
|**Search/PreventRemoteQueries**|兩者|URI 完整路徑： ./Vendor/MSFT/Policy/Config/Search/PreventRemoteQueries<br /><br />資料類型： 整數<br /><br />**允許的值：**<br /><br />**0**<br /><br />**1**<br /><br />預設值： 1|
|**Search/AllowUsingDiacritics**|兩者|URI 完整路徑： ./Vendor/MSFT/Policy/Config/Search/AllowUsingDiacritics<br /><br />資料類型： 整數<br /><br />**允許的值：**<br /><br />**0**<br /><br />**1**<br /><br />預設值： 0|
|**Search/AlwaysUseAutoLangDetection**|兩者|URI 完整路徑： ./Vendor/MSFT/Policy/Config/Search/AlwaysUseAutoLangDetection<br /><br />資料類型： 整數<br /><br />**允許的值：**<br /><br />**0**<br /><br />**1**<br /><br />預設值： 0|
|**Search/DisableRemovableDriveIndexing**|兩者|URI 完整路徑： ./Vendor/MSFT/Policy/Config/Search/DisableRemovableDriveIndexing<br /><br />資料類型： 整數<br /><br />**允許的值：**<br /><br />**0**<br /><br />**1**<br /><br />預設值： 0|
|**Search/PreventIndexingLowDiskSpaceMB**|兩者|URI 完整路徑： ./Vendor/MSFT/Policy/Config/Search/PreventIndexingLowDiskSpaceMB<br /><br />資料類型： 整數<br /><br />**允許的值：**<br /><br />**0**<br /><br />**1**<br /><br />預設值： 1|
|**Search/AllowIndexingEncryptedStoresOrItems**|兩者|URI 完整路徑： ./Vendor/MSFT/Policy/Config/Search/AllowIndexingEncryptedStoresOrItems<br /><br />資料類型： 整數<br /><br />**允許的值：**<br /><br />**0**<br /><br />**1**<br /><br />預設值： 0|
|**Security/AllowRemoveProvisioningPackage**|兩者|URI 完整路徑： ./Vendor/MSFT/Policy/Config/Security/AllowRemoveProvisioningPackage<br /><br />資料類型： 整數<br /><br />**允許的值：**<br /><br />0 - 不允許<br /><br />1 - 允許<br /><br />預設值： 1|
|**Security/RequireProvisioningPackageSignature**|兩者|URI 完整路徑： ./Vendor/MSFT/Policy/Config/Security/RequireProvisioningPackageSignature<br /><br />資料類型： 整數<br /><br />**允許的值：**<br /><br />**0**<br /><br />**1**<br /><br />預設值： 0|
|**AboveLock/AllowActionCenterNotifications**|兩者|URI 完整路徑： ./Vendor/MSFT/Policy/Config/AboveLock/AllowActionCenterNotifications<br /><br />資料類型： 整數<br /><br />**允許的值：**<br /><br />0 - 不允許<br /><br />1 - 允許<br /><br />預設值： 1|
|**TextInput/AllowIMENetworkAccess**|桌面|URI 完整路徑： ./Vendor/MSFT/Policy/Config/TextInput/AllowIMENetworkAccess<br /><br />資料類型： 整數<br /><br />**允許的值：**<br /><br />0 - 不允許<br /><br />系統會關閉開放式擴充字典。<br /><br />使用者無法：<br /><br />加入新的開放式擴充字典<br /><br />加入新的搜尋整合設定檔<br /><br />使用雲端候選字功能<br /><br />將註冊的字詞傳送給傳送使用者<br /><br />此外：<br /><br />在啟用此原則設定之前加入的開放式擴充字典不會用來進行轉換。<br /><br />系統不會使用在啟用此原則設定之前安裝的搜尋整合設定檔。<br /><br />1 - 允許<br /><br />預設可加入並使用開放式擴充字典。 此外，預設會使用搜尋整合功能。<br /><br />使用者可以：<br /><br />使用雲端候選字功能<br /><br />將註冊的字詞傳送給傳送使用者<br /><br />**預設值：**|
|**TextInput/AllowKoreanExtendedHanja**|桌面|URI 完整路徑： ./Vendor/MSFT/Policy/Config/TextInput/AllowKoreanExtendedHanja<br /><br />資料類型： 整數<br /><br />**允許的值：**<br /><br />0 - 不允許<br /><br />1 - 允許<br /><br />預設值： 1|
|**TextInput/AllowIMELogging**|桌面|URI 完整路徑： ./Vendor/MSFT/Policy/Config/TextInput/AllowIMELogging<br /><br />資料類型： 整數<br /><br />**允許的值：**<br /><br />0 - 關閉錯誤轉換記錄功能。 自動調整的資料和輸入歷程記錄資料不會儲存到檔案中。<br /><br />1 - 開啟錯誤轉換記錄功能。 自動調整的資料和輸入歷程記錄資料會儲存到檔案中。<br /><br />預設值： 1|
|**TextInput/AllowJapaneseNonPublishingStandardGlyph**|桌面|URI 完整路徑： ./Vendor/MSFT/Policy/Config/TextInput/AllowJapaneseNonPublishingStandardGlyph<br /><br />資料類型： 整數<br /><br />**允許的值：**<br /><br />0 - 不允許<br /><br />1 - 允許<br /><br />預設值： 1|
|**TextInput/AllowJapaneseIVSCharacters**|桌面|URI 完整路徑： ./Vendor/MSFT/Policy/Config/TextInput/AllowJapaneseIVSCharacters<br /><br />資料類型： 整數<br /><br />**允許的值：**<br /><br />0 - 不允許<br /><br />1 - 允許<br /><br />預設值： 1|
|**TextInput/AllowJapaneseUserDictionary**|桌面|URI 完整路徑： ./Vendor/MSFT/Policy/Config/TextInput/AllowJapaneseUserDictionary<br /><br />資料類型： 整數<br /><br />**允許的值：**<br /><br />0 - 不允許<br /><br />1 - 允許<br /><br />預設值： 1|
|**TextInput/AllowJapaneseIMESurrogatePairCharacters**|桌面|URI 完整路徑： ./Vendor/MSFT/Policy/Config/TextInput/AllowJapaneseIMESurrogatePairCharacters<br /><br />資料類型： 整數<br /><br />**允許的值：**<br /><br />0 - 不允許<br /><br />1 - 允許<br /><br />預設值： 1|
|**TextInput/ExcludeJapaneseIMEExceptShiftJIS**|桌面|URI 完整路徑： ./Vendor/MSFT/Policy/Config/TextInput/ExcludeJapaneseIMEExceptShiftJIS<br /><br />資料類型： 整數<br /><br />**允許的值：**<br /><br />0 - 篩選 JIS 字元以外的所有字元<br /><br />1 - 不篩選任何字元<br /><br />預設值： 1|
|**TextInput/ExcludeJapaneseIMEExceptJIS0208**|桌面|URI 完整路徑： ./Vendor/MSFT/Policy/Config/TextInput/ExcludeJapaneseIMEExceptJIS0208<br /><br />資料類型： 整數<br /><br />**允許的值：**<br /><br />0 - 篩選 JIS0208 字元以外的所有字元<br /><br />1 - 不篩選任何字元<br /><br />預設值： 1|
|**TextInput/ExcludeJapaneseIMEExceptJIS0208andEUDC**|桌面|URI 完整路徑： ./Vendor/MSFT/Policy/Config/TextInput/ExcludeJapaneseIMEExceptJIS0208andEUDC<br /><br />資料類型： 整數<br /><br />**允許的值：**<br /><br />0 - 篩選 JIS0208 字元或 EUDC 字元以外的所有字元<br /><br />1 - 不篩選任何字元。<br /><br />預設值： 1|
|**TextInput/AllowInputPanel**|桌面|URI 完整路徑： ./Vendor/MSFT/Policy/Config/TextInput/AllowInputPanel<br /><br />資料類型： 整數<br /><br />**允許的值：**<br /><br />0 - 不允許<br /><br />1 - 允許<br /><br />預設值： 1|
|**Bluetooth/AllowDiscoverableMode**|兩者|URI 完整路徑： ./Vendor/MSFT/Policy/Config/Bluetooth/AllowDiscoverableMode<br /><br />資料類型： 整數<br /><br />**允許的值：**<br /><br />0 - 不允許<br /><br />1 - 允許<br /><br />預設值： 1|
|**Bluetooth/AllowAdvertising**|兩者|URI 完整路徑： ./Vendor/MSFT/Policy/Config/Bluetooth/AllowAdvertising<br /><br />資料類型： 整數<br /><br />**允許的值：**<br /><br />0 - 不允許<br /><br />1 - 允許<br /><br />預設值： 1|
|**Settings/AllowDataSense**|兩者|URI 完整路徑： ./Vendor/MSFT/Policy/Config/Settings/AllowDataSense<br /><br />資料類型： 整數<br /><br />**允許的值：**<br /><br />0 - 不允許<br /><br />1 - 允許<br /><br />預設值： 1|
|**Settings/AllowVPN**|兩者|URI 完整路徑： ./Vendor/MSFT/Policy/Config/Settings/AllowVPN<br /><br />資料類型： 整數<br /><br />**允許的值：**<br /><br />0 - 不允許<br /><br />1 - 允許<br /><br />預設值： 1|
|**Settings/AllowWorkplace**|桌面|URI 完整路徑： ./Vendor/MSFT/Policy/Config/Settings/AllowWorkplace<br /><br />資料類型： 整數<br /><br />**允許的值：**<br /><br />0 - 不允許<br /><br />1 - 允許<br /><br />預設值： 1|
|**Settings/AllowDateTime**|兩者|URI 完整路徑： ./Vendor/MSFT/Policy/Config/Settings/AllowDateTime<br /><br />資料類型： 整數<br /><br />**允許的值：**<br /><br />0 - 不允許<br /><br />1 - 允許<br /><br />預設值： 1|
|**Settings/AllowLanguage**|桌面|URI 完整路徑： ./Vendor/MSFT/Policy/Config/Settings/AllowLanguage<br /><br />資料類型： 整數<br /><br />**允許的值：**<br /><br />0 - 不允許<br /><br />1 - 允許<br /><br />預設值： 1|
|**Settings/AllowRegion**|桌面|URI 完整路徑： ./Vendor/MSFT/Policy/Config/Settings/AllowRegion<br /><br />資料類型： 整數<br /><br />**允許的值：**<br /><br />0 - 不允許<br /><br />1 - 允許<br /><br />預設值： 1|
|**Settings/AllowSignInOptions**|桌面|URI 完整路徑： ./Vendor/MSFT/Policy/Config/Settings/AllowSignInOptions<br /><br />資料類型： 整數<br /><br />**允許的值：**<br /><br />0 - 不允許<br /><br />1 - 允許<br /><br />預設值： 1|
|**Settings/AllowYourAccount**|兩者|URI 完整路徑： ./Vendor/MSFT/Policy/Config/Settings/AllowYourAccount<br /><br />資料類型： 整數<br /><br />**允許的值：**<br /><br />0 - 不允許<br /><br />1 - 允許<br /><br />預設值： 1|
|**Settings/AllowPowerSleep**|桌面|URI 完整路徑： ./Vendor/MSFT/Policy/Config/Settings/AllowPowerSleep<br /><br />資料類型： 整數<br /><br />**允許的值：**<br /><br />0 - 不允許<br /><br />1 - 允許<br /><br />預設值： 1|
|**Settings/AllowAutoPlay**|桌面|URI 完整路徑： ./Vendor/MSFT/Policy/Config/Settings/AllowAutoPlay<br /><br />資料類型： 整數<br /><br />**允許的值：**<br /><br />0 - 不允許<br /><br />1 - 允許<br /><br />預設值： 1|
|**Experience/AllowCortana**|兩者|URI 完整路徑： ./Vendor/MSFT/Policy/Config/Experience/AllowCortana<br /><br />資料類型： 整數<br /><br />**允許的值：**<br /><br />0 - 不允許<br /><br />1 - 允許<br /><br />預設值： 1|
|**Search/SafeSearchPermissions**|行動電話|URI 完整路徑： ./Vendor/MSFT/Policy/Config/Search/SafeSearchPermissions<br /><br />資料類型： 整數<br /><br />**允許的值：**<br /><br />0 - 嚴格，針對成人內容進行最高程度的篩選<br /><br />1 - 中等，針對成人內容進行中等程度的篩選 (將不會篩選有效的搜尋結果)<br /><br />預設值： 1|
|**Experience/AllowCopyPaste**|行動電話|URI 完整路徑： ./Vendor/MSFT/Policy/Config/Experience/AllowCopyPaste<br /><br />資料類型： 整數<br /><br />**允許的值：**<br /><br />0 - 不允許<br /><br />1 - 允許<br /><br />預設值： 1|
|**強制開始大小**|行動電話|URI 完整路徑： ./Vendor/MSFT/Policy/Config/Start/ForceStartSize<br /><br />資料類型： 整數<br /><br />**允許的值：**<br /><br />0 - 允許使用者變更大小<br /><br />1 - 強制執行非全螢幕<br /><br />2 - 強制執行全螢幕<br /><br />預設值： 0|
|**Update/RequireDeferUpgrade**|兩者|URI 完整路徑： ./Vendor/MSFT/Policy/Config/Update/RequireDeferUpgrade<br /><br />資料類型： 整數<br /><br />**允許的值：**<br /><br />0：不延遲升級 (留在最新分支、CB)<br /><br />1：啟用更新且延後升級 (裝置遵循商務、CBB、規則的最新分支)<br /><br />**預設值：0**<br /><br />如需詳細資訊，請參閱：<br /><br />[Windows 10 服務簡介](https://technet.microsoft.com/library/mt598226(v=vs.85).aspx)<br /><br />[規劃 Windows 10 部署](https://technet.microsoft.com/library/mt574241(v=vs.85).aspx)|
|**Update/DeferUpdatePeriod**|兩者|描述：最多延後 4 週進行軟體更新的原則<br /><br />URI 完整路徑： ./Vendor/MSFT/Policy/Config/Update/DeferUpdatePeriod<br /><br />資料類型： 整數<br /><br />允許的值︰ 0︰立即套用更新；1-4︰延遲軟體更新的週數。<br /><br />**預設值：0**<br /><br /><br />如需詳細資訊，請參閱：<br /><br />[Windows 10 服務簡介](https://technet.microsoft.com/library/mt598226(v=vs.85).aspx)<br /><br />[規劃 Windows 10 部署](https://technet.microsoft.com/library/mt574241(v=vs.85).aspx)|
|**Update/DeferUpgradePeriod**|兩者|描述：延遲最多 8 個月進行功能升級的原則<br /><br />URI 完整路徑： ./Vendor/MSFT/Policy/Config/Update/DeferUpgradePeriod<br /><br />資料類型： 整數<br /><br />允許的值︰ 0︰立即套用更新；1-8︰延遲功能升級的月數。<br /><br />**預設值：0**<br /><br />如需詳細資訊，請參閱：<br /><br />[Windows 10 服務簡介](https://technet.microsoft.com/library/mt598226(v=vs.85).aspx)<br /><br />[規劃 Windows 10 部署](https://technet.microsoft.com/library/mt574241(v=vs.85).aspx)|
|**Update/PauseDeferrals**|兩者|描述：允許 CBB 機器停止接收更新及升級 5 週。 在更新發生問題的情況下應使用此。<br /><br />URI 完整路徑： ./Vendor/MSFT/Policy/Config/Update/PauseDeferrals<br /><br />資料類型： 整數<br /><br />**允許的值：**<br /><br />0：立即套用更新 (預設值)<br /><br />1︰暫停更新及升級 (5 週後過期)<br /><br />**預設值：0**|

### Windows Defender

|原則名稱|支援|詳細資料|
|---------------|------------|-----------|
|**AllowRealtimeMonitoring**|桌面|URI 完整路徑： ./Vendor/MSFT/Policy/Config/Defender/AllowRealtimeMonitoring<br /><br />資料類型： 整數<br /><br />**允許的值：**<br /><br />0 - 不允許<br /><br />1 - 允許<br /><br />預設值： 1|
|**AllowBehaviorMonitoring**|桌面|URI 完整路徑： ./Vendor/MSFT/Policy/Config/Defender/AllowBehaviorMonitoring<br /><br />資料類型： 整數<br /><br />**允許的值：**<br /><br />0 - 不允許<br /><br />1 - 允許<br /><br />預設值： 1|
|**AllowIntrusionPreventionSystem**|桌面|URI 完整路徑： ./Vendor/MSFT/Policy/Config/Defender/AllowIntrusionPreventionSystem<br /><br />資料類型： 整數<br /><br />**允許的值：**<br /><br />0 - 不允許<br /><br />1 - 允許<br /><br />預設值： 1|
|**AllowIOAVProtection**|桌面|URI 完整路徑： ./Vendor/MSFT/Policy/Config/Defender/AllowIOAVProtection<br /><br />資料類型： 整數<br /><br />**允許的值：**<br /><br />0 - 不允許<br /><br />1 - 允許<br /><br />預設值： 1|
|**AllowScriptScanning**|桌面|URI 完整路徑： ./Vendor/MSFT/Policy/Config/Defender/AllowScriptScanning<br /><br />資料類型： 整數<br /><br />**允許的值：**<br /><br />0 - 不允許<br /><br />1 - 允許<br /><br />預設值： 1|
|**AllowOnAccessProtection**|桌面|URI 完整路徑： ./Vendor/MSFT/Policy/Config/Defender/AllowOnAccessProtection<br /><br />資料類型： 整數<br /><br />**允許的值：**<br /><br />0 - 不允許<br /><br />1 - 允許<br /><br />預設值： 1|
|**RealTimeScanDirection**|桌面|URI 完整路徑： ./Vendor/MSFT/Policy/Config/Defender/RealTimeScanDirection<br /><br />資料類型： 整數<br /><br />**允許的值：**<br /><br />0 - 監視所有檔案 (雙向)<br /><br />1 - 監視傳入檔案<br /><br />2 - 監視傳出檔案<br /><br />預設值： 0|
|**DaysToRetainCleanedMalware**|桌面|URI 完整路徑： ./Vendor/MSFT/Policy/Config/Defender/DaysToRetainCleanedMalware<br /><br />資料類型： 整數<br /><br />允許的值：0 - 90 – 代表將保留惡意程式碼多長時間<br /><br />預設值： 0 – 一律保留在隔離資料夾中，且不會自動移除|
|**AllowUserUIAccess**|桌面|URI 完整路徑： ./Vendor/MSFT/Policy/Config/Defender/AllowUserUIAccess<br /><br />資料類型： 整數<br /><br />**允許的值：**<br /><br />0 - 不允許<br /><br />1 - 允許<br /><br />預設值： 1|
|**ScanParameter**|桌面|URI 完整路徑： ./Vendor/MSFT/Policy/Config/Defender/ScanParameter<br /><br />資料類型： 整數<br /><br />**允許的值：**<br /><br />1 - 快速掃描<br /><br />2 - 完整掃描<br /><br />預設值： 1|
|**ScheduleScanDay**|桌面|URI 完整路徑： ./Vendor/MSFT/Policy/Config/Defender/ScheduleScanDay<br /><br />資料類型： 整數<br /><br />**允許的值：**<br /><br />0 - 每天<br /><br />1 - 星期一<br /><br />2 - 星期二<br /><br />3 - 星期三<br /><br />4 - 星期四<br /><br />5 - 星期五<br /><br />6 - 星期六<br /><br />7 - 星期日<br /><br />8 - 未排定掃描<br /><br />預設值： 0|
|**ScheduleScanTime**|桌面|URI 完整路徑： ./Vendor/MSFT/Policy/Config/Defender/ScheduleScanTime<br /><br />資料類型： 整數<br /><br />**允許的值：**<br /><br />0 - 12:00 am<br /><br />60 - 1:00 am<br /><br />120 - 2:00 am<br /><br />180 - 3:00 am<br /><br />240 - 4:00 am<br /><br />300 - 5:00 am<br /><br />360 - 6:00 am<br /><br />420 - 7:00 am<br /><br />480 - 8:00 am<br /><br />540 - 9:00 am<br /><br />600 - 10:00 am<br /><br />660 - 11:00 am<br /><br />720 - 12:00 pm<br /><br />780 - 1:00 pm<br /><br />840 - 2:00 pm<br /><br />900 - 3:00 pm<br /><br />960 - 4:00 pm<br /><br />1020 - 5:00 pm<br /><br />1080 - 6:00 pm<br /><br />1140 - 7:00 pm<br /><br />1200 - 8:00 pm<br /><br />1260 - 9:00 pm<br /><br />1320 - 10:00 pm<br /><br />1381 - 維護期間<br /><br />預設值： 120|
|**ScheduleQuickScanTime**|桌面|URI 完整路徑： ./Vendor/MSFT/Policy/Config/Defender/ScheduleQuickScanTime<br /><br />資料類型： 整數<br /><br />**允許的值：**<br /><br />0 - 12:00 am<br /><br />60 - 1:00 am<br /><br />120 - 2:00 am<br /><br />180 - 3:00 am<br /><br />240 - 4:00 am<br /><br />300 - 5:00 am<br /><br />360 - 6:00 am<br /><br />420 - 7:00 am<br /><br />480 - 8:00 am<br /><br />540 - 9:00 am<br /><br />600 - 10:00 am<br /><br />660 - 11:00 am<br /><br />720 - 12:00 pm<br /><br />780 - 1:00 pm<br /><br />840 - 2:00 pm<br /><br />900 - 3:00 pm<br /><br />960 - 4:00 pm<br /><br />1020 - 5:00 pm<br /><br />1080 - 6:00 pm<br /><br />1140 - 7:00 pm<br /><br />1200 - 8:00 pm<br /><br />1260 - 9:00 pm<br /><br />1320 - 10:00 pm<br /><br />1380 - 11:00 pm<br /><br />預設值： 120|
|**AVGCPULoadFactor**|桌面|URI 完整路徑： ./Vendor/MSFT/Policy/Config/Defender/AVGCPULoadFactor<br /><br />資料類型： 整數<br /><br />允許的值：0 - 100<br /><br />預設值： 50|
|**AllowArchiveScanning**|桌面|URI 完整路徑： ./Vendor/MSFT/Policy/Config/Defender/AllowArchiveScanning<br /><br />資料類型： 整數<br /><br />**允許的值：**<br /><br />0 - 不允許<br /><br />1 - 允許<br /><br />預設值： 1|
|**AllowEmailScanning**|桌面|URI 完整路徑： ./Vendor/MSFT/Policy/Config/Defender/AllowEmailScanning<br /><br />資料類型： 整數<br /><br />**允許的值：**<br /><br />0 - 不允許<br /><br />1 - 允許<br /><br />預設值： 0|
|**AllowFullScanRemovableDriveScanning**|桌面|URI 完整路徑： ./Vendor/MSFT/Policy/Config/Defender/AllowFullScanRemovableDriveScanning<br /><br />資料類型： 整數<br /><br />**允許的值：**<br /><br />0 - 不允許<br /><br />1 - 允許<br /><br />預設值： 0|
|**AllowFullScanOnMappedNetworkDrives**|桌面|URI 完整路徑： ./Vendor/MSFT/Policy/Config/Defender/AllowFullScanOnMappedNetworkDrives<br /><br />資料類型： 整數<br /><br />**允許的值：**<br /><br />0 - 不允許<br /><br />1 - 允許<br /><br />預設值： 1|
|**AllowScanningNetworkFiles**|桌面|URI 完整路徑： ./Vendor/MSFT/Policy/Config/Defender/AllowScanningNetworkFiles<br /><br />資料類型： 整數<br /><br />**允許的值：**<br /><br />0 - 不允許<br /><br />1 - 允許<br /><br />預設值： 1 – 當 RTP 開啟時或其設為允許時也會執行|
|**SignatureUpdateInterval**|桌面|URI 完整路徑： ./Vendor/MSFT/Policy/Config/Defender/SignatureUpdateInterval<br /><br />資料類型： 整數<br /><br />**允許的值：**<br /><br />0 - 不會在某個時間間隔檢查簽章<br /><br />1 - 每小時檢查簽章<br /><br />1 - 每 2 小時檢查簽章，依此類推<br /><br />24 - 每天檢查簽章<br /><br />Default value: 8 – 每 8 小時檢查簽章|
|**AllowCloudProtection**|桌面|URI 完整路徑： ./Vendor/MSFT/Policy/Config/Defender/AllowCloudProtection<br /><br />資料類型： 整數<br /><br />**允許的值：**<br /><br />0 - 不允許<br /><br />1 - 允許<br /><br />預設值： 1|
|**SubmitSamplesConsent**|桌面|URI 完整路徑： ./Vendor/MSFT/Policy/Config/Defender/SubmitSamplesConsent<br /><br />資料類型： 整數<br /><br />**允許的值：**<br /><br />0 - 一律要求確認<br /><br />1 - 自動傳送安全的範例<br /><br />2 - 一律不傳送<br /><br />3 - 自動傳送所有的範例<br /><br />預設值： 0|
|**ExcludedExtensions**|桌面|URI 完整路徑： ./Vendor/MSFT/Policy/Config/Defender/ExcludedExtensions<br /><br />資料類型：字串<br /><br />**允許的值：**<br /><br />&lt;以分號分隔的副檔名清單&gt;例如 **obj;lib**<br /><br />預設值： 不排除任何副檔名|
|**ExcludedPaths**|桌面|URI 完整路徑： ./Vendor/MSFT/Policy/Config/Defender/ExcludedPaths<br /><br />資料類型：字串<br /><br />**允許的值：**<br /><br />*&lt;以分號分隔的路徑清單&gt;*<br /><br />範例：c:\test;c:\test1.exe<br /><br />預設值： 不排除任何路徑|
|**ExcludedProcesses**|桌面|URI 完整路徑： ./Vendor/MSFT/Policy/Config/Defender/ExcludedProcesses<br /><br />資料類型：字串<br /><br />**允許的值：**<br /><br />*&lt;以分號分隔的路徑清單&gt;*<br /><br />範例：c:\test.exe;c:\test1.exe<br /><br />預設值： 不排除任何程序|

### Edge 瀏覽器

|原則名稱|支援|詳細資料|
|---------------|------------|-----------|
|**允許瀏覽器**|行動電話|URI 完整路徑： ./Vendor/MSFT/Policy/Config/Browser/AllowBrowser<br /><br />資料類型： 整數<br /><br />允許的值︰0︰關閉瀏覽；1︰開啟瀏覽。<br /><br />預設值： 1|
|**AllowSearchSuggestionsinAddressBar**|兩者|URI 完整路徑： ./Vendor/MSFT/Policy/Config/Browser/AllowSearchSuggestionsinAddressBar<br /><br />資料類型： 整數<br /><br />允許的值：0：不顯示搜尋建議；1：顯示搜尋建議。<br /><br />預設值： 1|
|**SendIntranetTraffictoInternetExplorer**|桌面|URI 完整路徑： ./Vendor/MSFT/Policy/Config/Browser/SendIntranetTraffictoInternetExplorer<br /><br />資料類型： 整數<br /><br />允許的值︰0︰停用 (在 Edge 瀏覽器中開啟內部網路網站)；1：啟用 (在 Internet Explorer 中開啟內部網路網站)。<br /><br />預設值： 0|
|**允許不追蹤**|兩者|URI 完整路徑： ./Vendor/MSFT/Policy/Config/Browser/AllowDoNotTrack<br /><br />資料類型： 整數<br /><br />允許的值︰0 – 停用 (不傳送 DNT)；1 – 啟用 (傳送 DNT)<br /><br />預設值： 0|
|**設定 SmartScreen**|兩者|URI 完整路徑： ./Vendor/MSFT/Policy/Config/Browser/AllowSmartScreen<br /><br />資料類型： 整數<br /><br />允許的值：0 – 不允許；1 – 允許<br /><br />預設值： 1|
|**允許快顯視窗**|桌面|URI 完整路徑： ./Vendor/MSFT/Policy/Config/Browser/AllowPopups<br /><br />資料類型： 整數<br /><br />允許的值：0 – 封鎖快顯視窗；1 – 允許快顯視窗<br /><br />預設值： 0|
|**允許 Cookie**|兩者|URI 完整路徑： ./Vendor/MSFT/Policy/Config/Browser/AllowCookies<br /><br />資料類型： 整數<br /><br />允許的值︰0 – 不封鎖。 允許所有網站的 Cookie；1 – 只封鎖第三方 Cookie；2 – 封鎖所有 Cookie<br /><br />預設值： 0|
|**允許儲存密碼**|兩者|URI 完整路徑： ./Vendor/MSFT/Policy/Config/Browser/AllowPasswordManager<br /><br />資料類型： 整數<br /><br />允許的值：0 – 停用密碼管理員； <br />                        1 – 啟用密碼管理員<br /><br />預設值： 1|
|**允許自動填入**|桌面|URI 完整路徑： ./Vendor/MSFT/Policy/Config/Browser/AllowAutofill<br /><br />資料類型： 整數<br /><br />允許的值︰0 – 停用；1 – 啟用<br /><br />預設值： 0|
|**設定企業站台清單**|桌面|URI 完整路徑： ./Vendor/MSFT/Policy/Config/Browser/EnterpriseModeSiteList<br /><br />資料類型：字串<br /><br />允許的值︰0 – 未設定；1 – 使用 IE 的企業模式網站清單，如已設定；2 – 指定企業網站清單位置<br /><br />預設值： 1|

### 請參閱
[透過 Microsoft Intune 原則管理裝置上的設定和功能](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)



<!--HONumber=May16_HO1-->



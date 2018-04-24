---
title: Windows 10 原則設定
description: 使用本主題中所列的原則設定，以協助您設定已註冊之 Windows 10 桌上型和 Windows 10 行動裝置版裝置的內建與自訂設定。
keywords: ''
author: vhorne
ms.author: victorh
manager: angrobe
ms.date: 09/05/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 00a602d9-b339-4fd8-ab70-defbf6686855
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 202f15766aa740755669ab246739a5331ea328a4
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="intune-policy-settings-for-windows-10-devices-in-microsoft-intune"></a>Microsoft Intune 中 Windows 10 裝置的 Intune 原則設定

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

本主題包含的資訊可協助您了解可用來管理 Windows 10 裝置的 Intune 原則設定。 請搭配閱讀本主題以及[透過 Microsoft Intune 原則管理裝置上的設定和功能](/intune-classic/get-started/windows-pc-management-capabilities-in-microsoft-intune)中的程序。

有兩個原則類型供您選擇：

- **自訂原則**：使用適用於 Windows 10 和 Windows 10 行動裝置版的 Microsoft Intune **自訂原則**來部署 OMA-URI (開放行動聯盟的統一資源識別項) 設定，此設定可用來控制裝置上的功能。 Windows 10 讓許多 CSP 設定可供使用，例如[原則設定服務提供者 (原則 CSP)](https://technet.microsoft.com/itpro/windows/manage/how-it-pros-can-use-configuration-service-providers)。
- **一般設定原則**：當您想要從 Microsoft Intune 提供的內建清單中選取設定時，使用此原則類型。

## <a name="custom-policy-settings"></a>自訂原則設定

在自訂原則中提供下列設定。

### <a name="general-settings"></a>一般設定

輸入名稱，並選擇性地輸入可協助您在 Intune 主控台中識別該原則的描述。

### <a name="oma-uri-settings"></a>OMA-URI 設定

針對要新增的各個 OMA-URI 設定，輸入下列資訊：

- **設定名稱**：輸入 OMA-URI 設定的唯一名稱，協助您在設定清單中識別該設定。 如需有關 URI 設定的詳細資訊，請參閱[原則設定服務提供者 (原則 CSP)](https://technet.microsoft.com/itpro/windows/manage/how-it-pros-can-use-configuration-service-providers)。
- **設定描述**：選擇性地輸入設定的描述。
- **資料類型**︰從下列資料類型中選擇：
    - **字串**
    - **字串 (XML)**
    - **日期和時間**
    - **整數**
    - **浮點數**
    - **布林值**
- **OMA-URI (區分大小寫)**：指定您想要為其提供設定的 OMA-URI。
- **值**：指定要與您輸入的 OMA-URI 產生關聯的值。

### <a name="example"></a>範例
在下列螢幕擷取畫面中，已啟用 **Connectivity/AllowVPNOverCellular** 設定。 這可讓 Windows 10 裝置在行動電話通訊網路上時，開啟 VPN 連線。

> ![包含 VPN 設定的自訂原則範例](./media/custom-policy-example.png)

### <a name="how-to-find-the-policies-you-can-configure"></a>如何尋找可設定的原則

在 Windows 文件庫的[設定服務提供者參考 (英文)](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/configuration-service-provider-reference) 中，可以找到 Windows 10 所支援所有設定服務提供者 (CSP) 的完整清單。

並非所有設定都與所有的 Windows 10 版本相容。 Windows 主題中的表格會顯示每個 CSP 所支援的版本。

此外，Intune 不支援主題中列出的所有設定。 若要了解 Intune 是否支援您想要的設定，請開啟該設定的主題。 每個設定頁面都會顯示它所支援的作業。 若要使用 Intune，該設定必須支援「新增」或「取代」作業。

## <a name="general-configuration-policy-settings"></a>一般設定原則設定

使用 Windows 10 的 Microsoft Intune **一般設定原則**，為已註冊的 Windows 10 Desktop 和 Windows 10 行動裝置版裝置設定內建設定。

### <a name="password"></a>密碼

|設定名稱|其他資訊 (如有需要)|
|----------------|----------------------|
|**需要密碼才可解除鎖定裝置**|-|
|**必要的密碼類型**|指定密碼必須為英數字元，還是只能是數字|
|**需要的密碼類型** - **最小字元集數**| 指定密碼中必須包含多少字元集 (小寫字母、大寫字母、數字與符號)|
|**密碼長度下限**|僅適用於 Windows 10 行動裝置版|
|**抹除裝置前允許的重複登入失敗次數**。|若為執行 Windows 10 的裝置︰如果裝置已啟用 BitLocker，將會在登入失敗達您所指定的次數時置於 BitLocker 復原模式。 如果裝置未啟用 BitLocker，便不會套用此設定。<br>若為執行 Windows 10 行動裝置版的裝置︰登入失敗達您所指定的次數時，就會抹除裝置。|
|**關閉螢幕前的非使用狀態分鐘數**|指定裝置必須閒置多久的時間，才會鎖定螢幕|
|**密碼到期 (天數)**|指定在多久之後必須變更該裝置的密碼|
|**記住密碼歷程記錄**|指定是否要限制使用者建立先前使用過的密碼|
|**記住密碼歷程記錄** - **不得重複使用以前用過的密碼**|指定裝置記憶的先前使用過密碼數目|
|**裝置從閒置狀態恢復時必須輸入密碼**|指定使用者必須輸入密碼才能解除鎖定裝置 (限 Windows 10 行動裝置版)|

### <a name="encryption"></a>加密

|設定名稱|其他資訊 (如有需要)|
|----------------|----------------------|
|**在行動裝置上要求加密**|在目標裝置上啟用加密<br>(僅限 Windows 10 行動裝置版)|

### <a name="system"></a>System (系統)

|設定名稱|其他資訊 (如有需要)|
|----------------|----------------------|
|**允許螢幕擷取**|讓使用者擷取裝置螢幕作為映像 (限 Windows 10 行動裝置版)|
|**允許手動取消註冊**|可讓使用者從裝置手動刪除工作場所帳戶|
|**允許手動安裝根憑證**|適用於 Windows 10 行動裝置版|
|**允許將診斷與使用狀況資料傳送給 Microsoft**|可能的值為：<br><br>**否** - 沒有資料會傳送到 Microsoft<br>**基本** - 將有限資訊傳送給 Microsoft<br>**增強** - 將增強的診斷資料傳送給 Microsoft<br>**完整 (建議)** - 傳送和**增強**相同的資料，再加上裝置狀態的相關額外資料|


### <a name="account-and-synchronization"></a>帳戶和同步處理

|設定名稱|其他資訊 (如有需要)|
|----------------|----------------------|---------------------|
|**允許 Microsoft 帳戶**|讓使用者建立 Microsoft 帳戶與裝置之間的關聯|
|**允許手動新增非 Microsoft 帳戶**|讓使用者將電子郵件帳戶新增至未與 Microsoft 帳戶相關聯的裝置|
|**允許同步處理 Microsoft 帳戶的設定**|允許與 Microsoft 帳戶相關聯的裝置和應用程式設定在裝置之間進行同步處理|

### <a name="microsoft-edge"></a>Microsoft Edge

|設定名稱|其他資訊 (如有需要)|
|----------------|----------------------|
|**允許網頁瀏覽器**|允許在裝置上使用 Microsoft Edge 網頁瀏覽器<br>(僅限 Windows 10 行動裝置版)|
|**允許網址列中的搜尋建議**|讓您的搜尋引擎在您輸入搜尋片語時建議網站|
|**允許將內部網路流量傳送到 Internet Explorer**|讓使用者在 Internet Explorer 中開啟內部網路網站<br>(僅限 Windows 10 Desktop)|
|**允許不要追蹤**|設定 Microsoft Edge 瀏覽器以傳送「不要追蹤」標頭給使用者瀏覽的網站|
|**啟用 SmartScreen**||
|**允許動態指令碼處理**|允許在 Microsoft Edge 瀏覽器中執行 JavaScript 等指令碼|
|**允許快顯視窗**|僅使用於 Windows 10 桌面版|
|**允許 Cookie**||
|**允許自動填入**|可讓使用者變更瀏覽器中的自動完成設定<br>(僅限 Windows 10 Desktop)|
|**允許密碼管理員**|啟用或停用 Edge 密碼管理員功能|
|**企業模式網站清單位置**|指定在何處尋找以企業模式開啟的網站清單。 使用者無法編輯這份清單。<br>(僅限 Windows 10 Desktop)|

### <a name="apps"></a>應用程式

|設定名稱|其他資訊 (如有需要)|
|----------------|----------------------|---------------------|
|**允許應用程式市集**|僅適用於 Windows 10 行動裝置版|



### <a name="cellular"></a>行動電話通訊

|設定名稱|其他資訊 (如有需要)|
|----------------|----------------------|---------------------|
|**允許數據漫遊**|存取資料時允許網路之間的漫遊|
|**允許透過行動數據使用 VPN**|控制裝置是否可以在連線到行動電話通訊網路時存取 VPN 連線|
|**允許透過行動數據進行 VPN 漫遊**|控制裝置是否可以在漫遊到行動電話通訊網路時存取 VPN 連線|

### <a name="hardware"></a>硬體

|設定名稱|其他資訊 (如有需要)|
|----------------|----------------------|
|**允許相機**|-|
|**允許抽取式存放裝置**|指定是否可以與裝置搭配使用 SD 卡等外部存放裝置|
|**允許 Wi-Fi**|僅適用於 Windows 10 行動裝置版|
|**允許網際網路共用**|允許在裝置上使用網際網路連線共用|
|**允許手動設定 Wi-Fi**|控制使用者可以設定自己的 Wi-Fi 連線或只能使用由 Wi-Fi 設定檔設定的連線<br>(僅限 Windows 10 行動裝置版)|
|**允許自動連線到免費的 Wi-Fi 熱點**|讓裝置自動連線到免費 Wi-Fi 熱點並自動接受任何連線條款和條件|
|**允許地理位置**|指定裝置是否可以使用定位服務資訊|
|**允許 NFC**|允許裝置使用它的近距離無線通訊功能|
|**允許藍芽**|-|
|**允許可透過藍牙搜尋的模式**|讓其他藍芽啟用的裝置探索此裝置|
|**允許藍牙通知**|允許裝置透過藍牙接收廣告|
|**允許重設手機**|控制使用者是否可以將裝置重設成出廠預設值|
|**允許 USB 連線**|控制裝置是否可以透過 USB 連接來存取外接式存放裝置|
|**允許防竊模式**|設定是否啟用 Windows 防竊模式|

### <a name="features"></a>功能

|設定名稱|其他資訊 (如有需要)|
|----------------|----------------------|---------------------|
|**允許複製並貼上**|僅適用於 Windows 10 行動裝置版|
|**允許錄音**|僅適用於 Windows 10 行動裝置版|
|**允許 Cortana**|啟用或停用 Cortana 語音助理|
|**允許行動中心通知**|在裝置鎖定畫面上啟用或停用重要訊息中心通知<br>(僅限 Windows 10 行動裝置版)|

### <a name="windows-defender"></a>Windows Defender

所有設定都僅限 Windows 10 Desktop。

|設定名稱|其他資訊 (如有需要)|
|----------------|----------------------|---------------------|
|**允許即時監視**|啟用惡意程式碼、間諜軟體和其他垃圾軟體的即時掃描|
|**允許行為監視**|讓 Defender 在裝置上檢查某些已知模式的可疑活動|
|**啟用網路檢查系統**|網路檢查系統 (NIS) 可使用 Microsoft Endpoint Protection 中心提供的已知弱點簽章來協助偵測及阻擋惡意流量，以幫助保護裝置不受網路型入侵程式的影響|
|**掃描所有下載**|控制 Defender 是否掃描所有從網際網路下載的檔案|
|**允許指令碼掃描**|讓 Defender 掃描 Internet Explorer 中所使用的指令碼|
|**監視檔案和程式活動**|允許 Defender 監視裝置上的檔案和程式活動|
|**追蹤已解決惡意程式碼的天數**|在您指定的天數內，讓 Defender 繼續追蹤已解決的惡意程式碼，讓您可以手動檢查先前受影響的裝置。 如果您將此天數設為 **0**，惡意程式碼會保留在「隔離」資料夾，而且不會自動移除。 |
|**允許用戶端 UI 存取**|控制是否對使用者隱藏 Windows Defender 使用者介面。<br>變更此設定後，要在使用者電腦下次重新啟動時才會生效。|
|**排程每日快速掃描**|讓您排程每天在您選取的時間進行快速掃描|
|**排程系統掃描**|讓您排程在您指定的日期和時間定期進行完整或快速系統掃描|
|**限制掃描期間的 CPU 使用量**|讓您限制掃描可以使用的 CPU 資源數量 (從 **1** 至 **100**)|
|**掃描封存檔**|允許 Defender 掃描封存的檔案，例如 .zip 或 .cab 檔案。|
|**掃描電子郵件訊息**|允許 Defender 在電子郵件訊息到達裝置時加以掃描|
|**掃描卸除式磁碟機**|讓 Defender 掃描 USB 隨身碟等卸除式磁碟機|
|**掃描對應的網路磁碟機**|讓 Defender 在對應的網路磁碟機上掃描檔案。<br>如果磁碟機上的檔案是唯讀檔案，Defender 將無法移除在那些檔案中找到的任何惡意程式碼。|
|**掃描從網路共用資料夾開啟的檔案**|讓 Defender 在共用網路磁碟機上掃描檔案 (例如，從 UNC 路徑存取者)。<br>如果磁碟機上的檔案是唯讀，Defender 將無法移除在其中發現的任何惡意程式碼。|
|**簽章更新間隔**|指定 Defender 檢查新簽章檔案的間隔。|
|**允許雲端保護**|允許或封鎖 Microsoft Active Protection Service 從您管理的裝置接收惡意程式碼活動的相關資訊。 此資訊未來可用於改善本服務。|
|**提示使用者提交範例**|控制可能需要由 Microsoft 進一步分析以判斷其是否為惡意的檔案，是否自動傳送給 Microsoft|
|**偵測潛在垃圾應用程式**|保護已註冊的 Windows 桌上型裝置，以避免執行被 Windows Defender 歸類為潛在垃圾應用程式的軟體。 您可以不執行這些應用程式，也可以使用稽核模式，在安裝潛在垃圾應用程式時回報。|
|**執行掃描或使用即時保護時所要排除的檔案和資料夾**|將一或多個 **C:\Path** 或 **%ProgramFiles%\Path\filename.exe** 等檔案和資料夾新增至排除清單。 任何即時或已排程的掃描都不會包含這些檔案和資料夾。|
|**執行掃描或使用即時保護時所要排除的副檔名**|將一個或多個 **jpg** 或 **txt** 等副檔名新增至排除清單。 任何即時或已排程的掃描都不會包含有這些副檔名的任何檔案。|
|**執行掃描或使用即時保護時所要排除的處理程序**|將一或多個 **.exe**、**.com** 或 **.scr** 等類型的處理程序新增至排除清單。 任何即時或已排程的掃描都不會包含這些處理程序。|


### <a name="updates"></a>Updates

|設定名稱|其他資訊 (如有需要)|
|----------------|---------------|
|**允許自動更新**|允許自動更新。 設定下列其中一項設定來控制更新行為：<br />**通知下載**<br />**在維護時間自動安裝**<br />**在維護時間自動安裝並重新開機**<br />**在排程時間自動安裝並重新開機**︰請注意，選取這個選項時，您也可以進行下列設定：[對使用者隱藏通知] 和 [定義排程更新的安裝日]。<br>(僅限 Windows 10 Desktop)|
|**允許發行前版本功能**|可讓 Microsoft 將發行前版本設定和功能部署至 Windows 10 裝置。 您可以選取只允許設定，或安裝所有預先發行的設定與功能。|

### <a name="see-also"></a>另請參閱
[使用 Microsoft Intune 原則管理裝置的設定及功能](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)

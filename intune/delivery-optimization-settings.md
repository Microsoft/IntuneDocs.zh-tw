---
title: Intune 的 Windows 10 傳遞最佳化設定
titleSuffix: Microsoft Intune
description: 您可以使用 Intune 為 Windows 10 裝置部署的傳遞最佳化設定。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 08/01/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: kerimh
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 11361b65735a7ed7e724a77349e3624e0e35ecaf
ms.sourcegitcommit: 73fbecf7cee4fdfc37d3c30ea2007d2a9a6d2d12
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 08/03/2019
ms.locfileid: "68756557"
---
# <a name="delivery-optimization-settings-for-intune"></a>Intune 的傳遞最佳化設定

本文會列出 Intune 針對執行 Windows 10 及更新版本裝置支援的傳遞最佳化設定。  

Intune 主控台中大多數選項會直接對應到 Windows 文件中深入討論的傳遞最佳化設定，此處會提供相關內容的連結。  Intune 特定設定或選項不包含其他內容的連結。  

下列表格包含：  

- **設定**：Intune 中出現的設定。 若設定為連結，表示會開啟 Windows 文件中[為 Windows 10 更新設定傳遞最佳化](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization)內的相關項目，讓您深入了解設定。

- **Windows 版本**：包含此設定支援的最低 Windows 10 版本。  

- **詳細資料**：Intune 實作設定方式的簡短描述，包括 Intune 預設。 若有的話，其中也會包含[傳遞最佳化原則設定服務提供者](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization) (CSP) 項目的連結。  

若要設定 Intune 使用這些設定，請參閱[傳遞更新](delivery-optimization-windows.md)。  

## <a name="delivery-optimization"></a>傳遞最佳化  

|設定  |Windows 版本  |詳細資料  |
|---------|-----------------|---------|
| [下載模式](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization-reference#download-mode)     | 1511         | 指定傳遞最佳化用來下載內容的下載方法。<br><ul><li>**未設定**：終端使用者以自己的方法更新其裝置，可以使用作業系統提供的 [Windows Updates] 或 [傳遞最佳化]  設定。 </li> <li> **只有 HTTP，沒有任何對等 (0)** ：只從網際網路取得更新。 不要從您網路上的其他電腦取得更新 (對等)。 </li> <li> **混合相同 NAT 後方對等互連的 HTTP (1)** ：從網際網路以及您網路上的其他電腦取得更新。 </li> <li> **混合跨私人群組對等互連的 HTTP (2)** ：在位於相同 Active Directory 站台 (若存在的話) 或相同網域的裝置上進行對等互連。 選取此選項時，會在您的網路位址轉譯 (NAT) IP 位址之間對等互連。 </li> <li> **混合網際網路對等的 HTTP (3)** ：從網際網路且從您網路上的其他電腦取得更新。 </li> <li> **無對等的簡式下載模式 (99)** ：從網際網路直接從更新擁有者 (如 Microsoft) 取得更新。 它不會連絡傳遞最佳化雲端服務。 </li> <li> **略過模式 (100)** ：使用背景智慧型傳送服務 (BITS) 來取得更新。 不使用傳遞最佳化。 </li></ul> **預設**：未設定  <br><br> 原則 CSP：[DODownloadMode](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-dodownloadmode)  <br><br>  |
| [限制對等選取項目](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization-reference#select-a-method-to-restrict-peer-selection)          | 1803        | 要求將 [下載模式]  設為 [混合相同 NAT 後方對等互連的 HTTP (1)]  或 [混合跨私人群組對等互連的 HTTP (2)]  。<br/><br/>將對等選取項目限制在特定裝置群組。<br/><br/>**預設**：未設定 <br/><br/>原則 CSP：[DORestrictPeerSelectionBy](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-dorestrictpeerselectionby)<br><br>      |
| [群組識別碼來源](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization-reference#select-the-source-of-group-ids)     | 1803        | 要求將 [下載模式]  設為 [混合跨私人群組對等互連的 HTTP]  。<br><br>根據來源，將對等選取項目限制在特定裝置群組。<br><br>若您選取 [自訂]  ，您接著便可以設定 [群組識別碼 (GUID)]  。 若您需要針對位於不同網域，或是並未位於相同 LAN 上的分支建立本機網路對等互連的單一群組，請使用 GUID 作為群組識別碼。<br><br>**預設**：未設定 <br><br>原則 CSP：[DOGroupId](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-dogroupid)     |

## <a name="bandwidth"></a>頻寬  

|設定  |Windows 版本  |詳細資料  |
|---------|---------|---------|
|頻寬最佳化類型     | 查看詳細資料         | 選取 Intune 判斷傳遞最佳化針對所有同時下載活動所能使用頻寬上限的方式。<br><br>這些選項包括：<br><ul><li>**未設定**</li><br><li>**絕對** ‒ 指定裝置針對所有同時傳遞最佳化下載活動所能使用的[下載頻寬上限 (KB/秒)](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization-reference#maximum-download-bandwidth) 及[上傳頻寬上限 (KB/秒)](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization-reference#max-upload-bandwidth)。<br><br>需要 Windows 1607<br><br>原則 CSP：[DOMaxDownloadBandwidth](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-domaxdownloadbandwidth) 和 [DOMaxUploadBandwidth](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-domaxuploadbandwidth)</li><br><li>**百分比** ‒ 指定裝置針對所有同時傳遞最佳化下載活動所能使用的[前景下載頻寬上限 (%)](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization-reference#maximum-foreground-download-bandwidth) 及[背景下載頻寬上限 (%)](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization-reference#maximum-foreground-download-bandwidth)。<br><br>需要 Windows 1803<br><br>原則 CSP：[DOPercentageMaxForegroundBandwidth](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-dopercentagemaxforegroundbandwidth) 和 [DOPercentageMaxBackgroundBandwidth](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-dopercentagemaxbackgroundbandwidth)    <br><br><li>**附帶上班時間的百分比** ‒ 針對[前景](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization-reference#set-business-hours-to-limit-foreground-download-bandwidth)下載頻寬上限及[背景](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization-reference#set-business-hours-to-limit-background-download-bandwidth)下載頻寬上限，設定上班時間的開始及結束時間，以及在上班時間期間及該期間之外所使用的頻寬百分比。 <br><br>需要 Windows 1803 <br><br>原則 CSP：[DOSetHoursToLimitBackgroundDownloadBandwidth](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-dosethourstolimitbackgrounddownloadbandwidth) 和 [DOSetHoursToLimitForegroundDownloadBandwidth](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-dosethourstolimitforegrounddownloadbandwidth)<br><br>   |
|[延遲背景 HTTP 下載 (秒)](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization-reference#delay-background-download-from-http-in-secs) | 1803        | 使用此設定來設定延遲透過 HTTP 以背景方式下載內容的時間上限。 此設定僅適用於支援對等下載來源的下載。 在此延遲期間，裝置會搜尋具備可用內容的同儕節點。 在等待對等來源時，下載會向終端使用者顯示為處於停滯狀態。   <br><br>**預設**：不設定任何值   <br><br>**建議**：60 秒   <br><br>原則 CSP：[DODelayBackgroundDownloadFromHttp](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-dodelaybackgrounddownloadfromhttp) <br><br>    |
| [延遲前景 HTTP 下載 (秒)](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization-reference#delay-foreground-download-from-http-in-secs)      | 1803       | 設定延遲透過 HTTP 以前景 (互動) 方式下載內容的時間上限。 此設定僅適用於支援對等下載來源的下載。 在此延遲期間，裝置會搜尋具備可用內容的同儕節點。 在等待對等來源時，下載會向終端使用者顯示為處於停滯狀態。   <br><br>**預設**：不設定任何值   <br><br>**建議**：60 秒   <br><br>原則 CSP：[DODelayForegroundDownloadFromHttp](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-dodelayforegrounddownloadfromhttp) <br><br>         |


## <a name="caching"></a>快取  

|設定  |Windows 版本  |詳細資料  |
|---------|---------|---------|
|[對等快取所需要的最低 RAM (GB)](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization-reference#minimum-ram-inclusive-allowed-to-use-peer-caching)      | 1703        | 指定裝置使用對等快取時必須擁有的 RAM 大小下限 (GB)。 <br><br>**預設**：不設定任何值   <br><br>**建議**：4 GB <br><br>原則 CSP：[DOMinRAMAllowedToPeer](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-dominramallowedtopeer) <br><br>        |
|[對等快取所需要的最低磁碟大小 (GB)](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization-reference#minimum-disk-size-allowed-to-use-peer-caching)      | 1703        | 指定裝置使用對等快取時必須擁有的磁碟大小下限 (GB)。 <br><br>**預設**：不設定任何值   <br><br>**建議**：32 GB   <br><br>原則 CSP：[DOMinDiskSizeAllowedToPeer](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-domindisksizeallowedtopeer) <br><br>    |
|[對等快取的內容檔案大小下限 (MB)](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization-reference#minimum-peer-caching-content-file-size)      | 1703        | 指定使用對等快取時，檔案必須符合或超過的大小下限 (MB)。  <br><br>**預設**：不設定任何值   <br><br>**建議**：10 MB   <br><br>原則 CSP：[DOMinFileSizeToCache](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-dominfilesizetocache)  <br><br>      |
|[上傳所需的電池電量下限 (%)](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization-reference#allow-uploads-while-the-device-is-on-battery-while-under-set-battery-level)      | 1709        | 以百分比指定裝置上傳資料至同儕節點時，必須擁有的電池電量下限。 若電池電量低於指定值，則任何使用中的上傳都會自動暫停。   <br><br>**預設**：不設定任何值   <br><br>**建議**：40%   <br><br>原則 CSP：[DOMinBatteryPercentageAllowedToUpload](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-dominbatterypercentageallowedtoupload) <br><br>        |
|[修改快取磁碟機](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization-reference#modify-cache-drive)        | 1607        | 指定傳遞最佳化用來進行快取的磁碟機。 您可以使用環境變數、磁碟機代號，或是完整路徑。  <br><br>**預設**：%SystemDrive% <br><br>原則 CSP：[DOModifyCacheDrive](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-domodifycachedrive) <br><br>        |
| [快取保留時間上限 (日)](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization-reference#max-cache-age)    | 1511         | 指定每個檔案成功下載該檔案後，要在裝置傳遞最佳化快取上保留的時間長度。   <br><br>使用 Intune，您會以天數指定快取保留時間。 您定義的天數會轉換成適用秒數，這是 Windows 定義此設定的方式。 例如，設為 3 天的 Intune 設定會在裝置上轉換成 259200 秒 (3 天)。  <br><br>**預設**：不設定任何值      <br><br>**建議**：7   <br><br>原則 CSP：[DOMaxCacheAge](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-domaxcacheage)  <br><br>          |
| 最大快取大小類型  | 查看詳細資料     | 選取如何管理裝置上由傳遞最佳化所使用的磁碟空間。 當沒有進行設定時，快取大小預設為可用磁碟空間的 20%。  <br><ul><li>**未設定** (預設)</li><br><li>**絕對** ‒ 指定[絕對快取大小上限 (GB)](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization-reference#absolute-max-cache-size) 來設定裝置可用來進行傳遞最佳化的磁碟空間上限。 設為 0 (零) 時，表示快取大小不受限制，雖然傳遞最佳化仍會在裝置磁碟空間不足時清除快取。 <br><br>需要 Windows 1607<br><br> 原則 CSP：[DOAbsoluteMaxCacheSize](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-doabsolutemaxcachesize) </li><br><li>**百分比** ‒ 指定[快取大小上限 (%)](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization-reference#max-cache-size) 來設定裝置可用來進行傳遞最佳化的磁碟空間上限。 此百分比是可用的磁碟空間百分比，傳遞最佳化會持續評估可用的磁碟空間並會清除快取，以使快取大小上限維持在所設定的百分比之下。 <br><br>需要 Windows 1511<br><br>原則 CSP：[DOMaxCacheAge](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-domaxcachesize)  |
| [VPN 對等快取](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization-reference#enable-peer-caching-while-the-device-connects-via-vpn)  | 1709  | 選取 [啟用]  來設定裝置在由通往網域網路的 VPN 連線時參與對等快取。 啟用此設定的裝置可從其他網域網路裝置下載或上傳至其他網域網路裝置 (透過 VPN 或公司網域網路)。  <br><br>**預設**：未設定  <br><br>原則 CSP：[DOAllowVPNPeerCaching](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-domaxcacheage)    |

## <a name="local-server-caching"></a>本機伺服器快取  

|設定  |Windows 版本  |詳細資料  |
|---------|-----------------|---------|
|快取伺服器主機名稱 | 1809  |指定您的裝置將使用的網路快取伺服器的 IP 位址或 FQDN 以進行傳遞優化, 然後選取 [**新增**] 以將該專案新增至清單。  <br><br>**預設**：未設定  <br><br>原則 CSP: [DOCacheHost](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-docachehost)  |
|[延遲前景下載快取伺服器回退 (以秒為單位)](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization-reference#delay-foreground-download-cache-server-fallback-in-secs) | 1903    |指定時間 (以秒為單位) (0-2592000), 將快取伺服器的回復延遲到的 HTTP 來源, 以進行前景內容下載。 當延遲從 HTTP 進行前景下載的原則時, 它會先套用 (以便先允許來自對等的下載)。 (0-2592000)    <br><br>**預設**：0  <br><br>原則 CSP [DODelayCacheServerFallbackForeground](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-dodelaycacheserverfallbackforeground)  |
|[延遲背景下載快取伺服器回退 (以秒為單位)](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization-reference#delay-background-download-cache-server-fallback-in-secs) | 1903    |指定以秒為單位的時間 (0-2592000), 將快取伺服器的回復延遲到 HTTP 來源, 以取得背景內容下載。 在設定*延遲背景 HTTP 下載 (以秒為單位)* 時, 該設定會先套用以允許來自對等的下載。 (0-2592000)   <br><br>**預設**：0 <br><br>原則 CSP: [DODelayCacheServerFallbackBackground](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-dodelaycacheserverfallbackbackground)  |


## <a name="next-steps"></a>後續步驟

[在 Intune 中設定傳遞最佳化](delivery-optimization-windows.md)

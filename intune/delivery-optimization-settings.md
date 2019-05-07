---
title: Intune 的 Windows 10 的傳遞最佳化設定 |Microsoft Docs
description: 您可以使用 Intune 來部署的 Windows 10 裝置的傳遞最佳化設定。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 03/09/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: kerimh
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: e6e90828da8c209b534b830af7fe522b254374bf
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57695274"
---
# <a name="delivery-optimization-settings-for-intune"></a>Intune 的傳遞最佳化設定

本文章列出 Intune 支援執行 Windows 10 或更新版本之裝置的傳遞最佳化設定。  

在 Intune 主控台中的大部分選項直接對應至涵蓋深入 Windows 文件，提供的相關內容的連結中的傳遞最佳化設定。  設定或特定 intune 選項不會包含其他內容連結。  

下表包括：  

- **設定**： 設定，所以會出現在 Intune 中。 設定連結的開啟中的相關項目[設定傳遞最佳化適用於 Windows 10 更新](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization)Windows 文件，您可以深入了解此設定中。

- **Windows 版本**： 包含此設定支援的 Windows 10 的最小版本。  

- **詳細資料**: Intune 如何實作的設定，包括 Intune 預設的簡短描述。 如果有的話，有連結[傳遞最佳化原則設定服務提供者](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization)(CSP) 的項目。  

若要設定 Intune，以使用這些設定，請參閱[傳遞更新](delivery-optimization-windows.md)。  

## <a name="delivery-optimization"></a>傳遞最佳化  

|設定  |Windows 版本  |詳細資料  |
|---------|-----------------|---------|
| [下載模式](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization#download-mode)     | 1511         | 指定的下載方法的傳遞最佳化使用下載內容。<br><ul><li>**未設定**：終端使用者以自己的方法更新其裝置，可以使用作業系統提供的 [Windows Updates] 或 [傳遞最佳化] 設定。 </li> <li> **只有 HTTP，沒有任何對等 (0)**：只從網際網路取得更新。 不要從您的網路 （若要對等） 上的其他電腦取得更新。 </li> <li> **混合 (1) 的相同 NAT 後對等的 HTTP**： 取得更新，從網際網路和網路上其他電腦。 </li> <li> **混合跨私人群組 (2) 對等互連使用的 HTTP**： 對等互連，就會發生在相同的裝置上 Active Directory 站台 （若有的話） 或相同的網域。 選取此選項時，會在您的網路位址轉譯 (NAT) IP 位址之間對等互連。 </li> <li> **混合網際網路對等的 HTTP (3)**：從網際網路且從您網路上的其他電腦取得更新。 </li> <li> **無對等的簡式下載模式 (99)**：從網際網路直接從更新擁有者 (如 Microsoft) 取得更新。 它不會連絡傳遞最佳化雲端服務。 </li> <li> **略過模式 (100)**：使用背景智慧型傳送服務 (BITS) 來取得更新。 不使用傳遞最佳化。 </li></ul> **預設**： 未設定  <br><br> 原則 CSP: [DODownloadMode](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-dodownloadmode)  <br><br>  |
| [限制對等體選取項目](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization#select-a-method-to-restrict-peer-selection)          | 1803        | 需要**下載模式**設為*混合相同 NAT (1) 後對等互連的 HTTP*或是*混合跨私人群組 (2) 對等互連使用的 HTTP*。<br/><br/>將對等體選取項目限制為特定群組的裝置。<br/><br/>**預設**： 未設定 <br/><br/>原則 CSP: [DORestrictPeerSelectionBy](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-dorestrictpeerselectionby)<br><br>      |
| [群組識別碼來源](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization#select-the-source-of-group-ids)     | 1803        | 需要**下載模式**設為*混合跨私人群組對等互連使用的 HTTP*。<br><br>將對等體選取項目限制為特定裝置群組的來源。<br><br>如果您選取**自訂**，然後設定**群組識別碼 （GUID)**。 如果您需要建立一個群組的本機網路對等互連，位於不同網域，或不在相同的區域網路上的分支，請使用 GUID 做為群組識別碼。<br><br>**預設**： 未設定 <br><br>原則 CSP: [DOGroupId](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-dogroupid)     |

## <a name="bandwidth"></a>頻寬  

|設定  |Windows 版本  |詳細資料  |
|---------|---------|---------|
|頻寬最佳化類型     | 查看詳細資料        | 選取 Intune 如何決定的最大頻寬的傳遞最佳化可以跨所有並行的下載活動使用。<br><br>這些選項包括：<br><ul><li>**未設定**</li><br><li>**絕對**– 指定[將下載頻寬上限 （以 KB/秒）](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization#maximum-download-bandwidth)並[（以 KB/秒） 的最大上傳頻寬](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization#max-upload-bandwidth)裝置可以使用跨所有其並行的傳遞最佳化下載活動。<br><br>需要 Windows 1607<br><br>原則 CSP: [DOMaxDownloadBandwidth](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-domaxdownloadbandwidth)和[DOMaxUploadBandwidth](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-domaxuploadbandwidth)</li><br><li>**百分比**– 指定[上限幕前的下載頻寬 （%）](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization#maximum-foreground-download-bandwidth)並[最大背景下載頻寬 （%）](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization#maximum-foreground-download-bandwidth) ，裝置可以使用跨所有其並行傳送最佳化下載活動。<br><br>需要 Windows 1803<br><br>原則 CSP: [DOPercentageMaxForegroundBandwidth](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-dopercentagemaxforegroundbandwidth)和[DOPercentageMaxBackgroundBandwidth](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-dopercentagemaxbackgroundbandwidth)    <br><br><li>**使用營業時間的百分比**– 適用於最多[前景](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization#set-business-hours-to-limit-foreground-download-bandwidth)下載頻寬和最多[背景](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization#set-business-hours-to-limit-background-download-bandwidth)下載頻寬、 設定營業時間的開始和結束時間，然後若要使用內以及非上班時間的頻寬的百分比。 <br><br>需要 Windows 1803 <br><br>原則 CSP: [DOSetHoursToLimitBackgroundDownloadBandwidth](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-dosethourstolimitbackgrounddownloadbandwidth)和[DOSetHoursToLimitForegroundDownloadBandwidth](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-dosethourstolimitforegrounddownloadbandwidth)<br><br>   |
|[延遲 （以秒為單位） 的背景 HTTP 下載](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization#delay-background-download-from-http-in-secs) | 1803        | 若要設定最長時間延遲的背景下載內容，透過 HTTP 使用此設定。 只適用於支援對等下載來源的下載項目。 在這種延遲，裝置會搜尋具有可用內容的對等。 等候的對等來源，下載似乎會停滯使用者。   <br><br>**預設值**:*不設定任何值*  <br><br>**建議**: 60 秒   <br><br>原則 CSP: [DODelayBackgroundDownloadFromHttp](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-dodelaybackgrounddownloadfromhttp) <br><br>    |
| [延遲 （以秒為單位） 的前景 HTTP 下載](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization#delay-foreground-download-from-http-in-secs)      | 1803       | 設定透過 HTTP 延遲前景 （互動式） 下載內容的最大時間。 只適用於支援對等下載來源的下載項目。 在這種延遲，裝置會搜尋具有可用內容的對等。 等候的對等來源，下載似乎會停滯使用者。   <br><br>**預設值**:*不設定任何值*  <br><br>**建議**: 60 秒   <br><br>原則 CSP: [DODelayForegroundDownloadFromHttp](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-dodelayforegrounddownloadfromhttp) <br><br>         |


## <a name="caching"></a>快取  

|設定  |Windows 版本  |詳細資料  |
|---------|---------|---------|
|[對等快取 （以 gb 為單位） 所需的最小 RAM](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization#minimum-ram-allowed-to-use-peer-caching)      | 1703        | 指定的最小 RAM 大小以 gb 為單位，裝置必須使用對等快取。 <br><br>**預設值**:*不設定任何值*  <br><br>**建議**: 4 GB <br><br>原則 CSP: [DOMinRAMAllowedToPeer](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-dominramallowedtopeer) <br><br>        |
|[對等快取 （以 gb 為單位） 所需的最小的磁碟大小](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization#minimum-disk-size-allowed-to-use-peer-caching)      | 1703        | 指定的最小的磁碟大小以 gb 為單位，裝置必須使用對等快取。 <br><br>**預設值**:*不設定任何值*  <br><br>**建議**: 32 GB   <br><br>原則 CSP: [DOMinDiskSizeAllowedToPeer](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-domindisksizeallowedtopeer) <br><br>    |
|[對等快取 （以 mb 為單位） 的最小的內容檔案大小](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization#minimum-peer-caching-content-file-size)      | 1703        | 指定的最小大小以 mb 為單位，檔案必須符合或超過使用對等快取。  <br><br>**預設值**:*不設定任何值*  <br><br>**建議**: 10 MB   <br><br>原則 CSP: [DOMinFileSizeToCache](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-dominfilesizetocache)  <br><br>      |
|[上傳 （%） 所需的最小電池電量](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization#allow-uploads-while-the-device-is-on-battery-while-under-set-battery-level)      | 1709        | 指定以百分比表示，裝置必須已將資料上傳到對等的最小電池層級。 如果電池電量卸除指定的值，任何使用中的上傳，自動暫停。   <br><br>**預設值**:*不設定任何值*  <br><br>**建議**：40%   <br><br>原則 CSP: [DOMinBatteryPercentageAllowedToUpload](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-dominbatterypercentageallowedtoupload) <br><br>        |
|[修改快取磁碟機](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization#modify-cache-drive)        | 1607        | 指定的磁碟機的傳遞最佳化用於其快取。 您可以使用環境變數、 磁碟機代號或完整路徑。  <br><br>**預設**: %systemdrive% <br><br>原則 CSP: [DOModifyCacheDrive](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-domodifycachedrive) <br><br>        |
| [最大的快取保留時間 （以天為單位）](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization#max-cache-age)    | 1511         | 指定如何許久之後每個檔案已成功下載該檔案會保留在裝置上的傳遞最佳化快取。   <br><br>使用 Intune 中，您可以設定快取保留時間以天為單位。 您所定義的天數會轉換成適用的秒數，這是如何 Windows 定義此此設定。 比方說，Intune 設定為 3 天會轉換為 259200 秒 （3 天） 裝置上。  <br><br>**預設值**:*不設定任何值*     <br><br>**建議**：7   <br><br>原則 CSP: [DOMaxCacheAge](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-domaxcacheage)  <br><br>          |
| 最大快取大小類型  | 查看詳細資料    | 選取如何管理裝置，以供傳遞最佳化的磁碟空間數量。 當未設定，快取大小預設為 20%的可用磁碟空間。  <br><ul><li>**未設定** (預設)</li><br><li>**絕對**– 指定[絕對最大的快取大小 （以 gb 為單位）](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization#absolute-max-cache-size)來設定裝置可用的傳遞最佳化的磁碟機空間的最大數量。 設定為 0 （零） 時，快取大小沒有限制，雖然傳遞最佳化裝置磁碟空間不足時，將會清除快取。 <br><br>需要 Windows 1607<br><br> 原則 CSP: [DOAbsoluteMaxCacheSize](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-doabsolutemaxcachesize) </li><br><li>**百分比**– 指定[快取大小上限 （%）](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization#max-cache-size)來設定裝置可用的傳遞最佳化的磁碟機空間的最大數量。 百分比是可用的磁碟機的空間，並傳遞最佳化持續評估可用的磁碟機空間，並將會清除快取保留下設定的百分比的最大快取大小。 <br><br>需要 Windows 1511<br><br>原則 CSP: [DOMaxCacheSize](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-domaxcachesize)  |
| [VPN 對等快取](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization#enable-peer-caching-while-the-device-connects-via-vpn)  | 1709  | 選取 **已啟用**設定要參與對等快取，透過 VPN 連線到網域網路時的裝置。 已啟用的裝置可以從下載或上傳至其他網域網路裝置上 VPN 或公司網域網路上。  <br><br>**預設**： 未設定  <br><br>原則 CSP: [DOAllowVPNPeerCaching](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deliveryoptimization#deliveryoptimization-domaxcacheage)    |

## <a name="next-steps"></a>後續步驟

[在 Intune 中設定傳遞最佳化](delivery-optimization-windows.md)

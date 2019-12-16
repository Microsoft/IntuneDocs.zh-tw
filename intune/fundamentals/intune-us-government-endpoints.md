---
title: 美國政府部署的網路端點 - Microsoft Intune
titleSuffix: ''
description: 檢閱 Intune 的美國政府端點。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/30/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 5f6682cb-5fcd-4018-b7f7-71768ad3152e
ms.reviewer: kerimh
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: d876c0268f38a09ea3729a7e19ee00b321ae897a
ms.sourcegitcommit: edd06a494a241d198ca9b0d3030c92195976e0d3
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/11/2019
ms.locfileid: "75000392"
---
# <a name="us-government-endpoints-for-microsoft-intune"></a>Microsoft Intune 的美國政府端點

此頁面會列出您 Intune 部署中 Proxy 設定所需要的美國政府端點。

若要管理位於防火牆和 Proxy 伺服器後方的裝置，您必須啟用 Intune 的通訊功能。

- Proxy 伺服器必須同時支援 **HTTP (80)** 和 **HTTPS (443)** ，因為 Intune 用戶端會使用這兩種通訊協定
- 針對某些工作 (例如下載軟體更新)，Intune 會需要未驗證的 Proxy 伺服器存取 manage.microsoft.com

您可以修改個別用戶端電腦上的 Proxy 伺服器設定。 也可以使用群組原則設定，針對位於指定 Proxy 伺服器後方的所有用戶端電腦變更設定。

受管理裝置需要進行可讓 [所有使用者]  穿過防火牆存取服務的設定。

下表列出 Intune 用戶端存取的連接埠和服務：

|**端點**|**IP 位址**|
|---------------------|-----------|
|*.manage.microsoft.us | 52.243.26.209 <br> 52.247.173.11 <br> 52.227.183.12 <br>52.227.180.205 <br> 52.227.178.107 <br> 13.72.185.168 <br> 52.227.173.179 <br> 52.227.175.242 <br> 13.72.39.209 <br> 52.243.26.209 <br> 52.247.173.11 |
| enterpriseregistration.microsoftonline.us | 13.72.188.239 <br> 13.72.55.179 |

## <a name="us-government-customer-designated-endpoints"></a>美國政府客戶指定端點：
- Azure 入口網站：https:\//portal.azure.us/ 
- Office 365：https:\//portal.office365.us/ 
- Intune 公司入口網站：https:\//portal.manage.microsoft.us/ 

## <a name="partner-service-endpoints-that-intune-depends-on"></a>Intune 依賴的合作夥伴服務端點：
- AAD Sync 服務：https:\//syncservice.gov.us.microsoftonline.com/DirectoryService.svc
- Evo STS：https:\//login.microsoftonline.us
- Directory Proxy：https:\//directoryproxy.microsoftazure.us/DirectoryProxy.svc
- AAD Graph：https:\//directory.microsoftazure.us and https:\//graph.microsoftazure.us
- MS Graph：https:\//graph.microsoft.us
- ADRS：https:\//enterpriseregistration.microsoftonline.us

## <a name="windows-push-notification-services"></a>Windows 推播通知服務
在使用行動裝置管理 (MDM) 所管理的 Intune 受控裝置上，需要有 Windows 推播通知服務 (WNS) 才能進行裝置動作和其他立即活動。 如需詳細資訊，請參閱[支援 WNS 流量的企業防火牆和 Proxy 設定](https://docs.microsoft.com/windows/uwp/design/shell/tiles-and-notifications/firewall-allowlist-config) ()

## <a name="apple-device-network-information"></a>Apple 裝置網路資訊

|**使用對象**|**主機名稱 (IP 位址/子網路)**|**通訊協定**|**連接埠**|
|------------|-----------|------------|-----------|
|擷取並顯示來自 Apple 伺服器的內容|itunes.apple.com<br>\*.itunes.apple.com<br>\*.mzstatic.com<br>\*.phobos.apple.com<br>\*.phobos.itunes-apple.com.akadns.net|HTTP|80|
|與 APNS 伺服器通訊|#-courier.push.apple.com<br>'#' 是從 0 至 50 的隨機數字。|TCP|5223 和 443|
|各種功能，包括存取網際網路、iTunes store、macOS App Store、iCloud、傳訊等。|phobos.apple.com<br>ocsp.apple.com<br>ax.itunes.apple.com<br>ax.itunes.apple.com.edgesuite.net|HTTP/HTTPS|80 或 443|

如需詳細資訊，請參閱：

- [Apple 軟體產品使用的 TCP 和 UDP 埠](https://support.apple.com/HT202944)
- [關於 macOS、iOS 和 iTunes 伺服器主機連線與 iTunes 背景程序](https://support.apple.com/HT201999)
- [如果 macOS 和 iOS 用戶端無法取得 Apple 推播通知](https://support.apple.com/HT203609)

## <a name="next-steps"></a>後續步驟
[Microsoft intune 的網路端點](intune-endpoints.md)

[Windows 10 自動註冊和裝置註冊](../enrollment/windows-enroll.md#registration-and-enrollment-cnames)
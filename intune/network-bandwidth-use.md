---
title: Microsoft Intune 的網路需求與頻寬詳細資料
titlesuffix: ''
description: 檢閱 Intune 的網路設定需求與頻寬詳細資料。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 01/24/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 0f737d48-24bc-44cd-aadd-f0a1d59f6893
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic; get-started
ms.openlocfilehash: 243e9602a253fecf2eda1dd73dfb49a488db0974
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2018
ms.locfileid: "52190246"
---
# <a name="intune-network-configuration-requirements-and-bandwidth"></a>Intune 網路設定需求與頻寬

[!INCLUDE [both-portals](./includes/note-for-both-portals.md)]

本指南可協助 Intune 系統管理員了解 Intune 服務的網路需求。 您可以使用這項資訊來了解頻寬需求，以及 Proxy 設定所需的 IP 位址和連接埠設定。

## <a name="average-network-traffic"></a>平均網路流量
此表格列出每個用戶端透過網路傳輸的一般內容的估計大小和頻率。

> [!NOTE]
> 為確保裝置從 Intune 接收更新與內容，它們必須定期連線到網際網路。 接收更新或內容所需要的時間不定，但應保持每天至少 1 小時持續連線到網際網路。

|內容類型|大小近似值|頻率和詳細資料|
|----------------|--------------------|-------------------------|
|Intune 用戶端安裝<br /><br />**以下是除了安裝 Intune 用戶端以外的需求**|125 MB|**一次**<br /><br />用戶端下載的大小會因用戶端電腦的作業系統而不同。|
|用戶端註冊套件|15 MB|**一次**<br /><br />當此內容類型有更新時，可能會進行其他下載。|
|Endpoint Protection 代理程式|65 MB|**一次**<br /><br />當此內容類型有更新時，可能會進行其他下載。|
|Operations Manager 代理程式|11 MB|**一次**<br /><br />當此內容類型有更新時，可能會進行其他下載。|
|原則代理程式|3 MB|**一次**<br /><br />當此內容類型有更新時，可能會進行其他下載。|
|Remote Assistance via Microsoft Easy Assist 代理程式|6 MB|**一次**<br /><br />當此內容類型有更新時，可能會進行其他下載。|
|日常用戶端作業|6 MB|**每日**<br /><br />Intune 用戶端會定期與 Intune 服務通訊，以檢查是否有更新和原則，並將用戶端的狀態回報給服務。|
|Endpoint Protection 惡意程式碼定義更新|不定<br /><br />通常為 40 KB 到 2 MB|**每日**<br /><br />最多一天 3 次。|
|Endpoint Protection 引擎更新|5 MB|**每月**|
|軟體更新|不定<br /><br />大小依您部署的更新而定。|**每月**<br /><br />一般情況下，軟體更新會在每個月的第二個星期二發佈。<br /><br />剛完成註冊或部署的電腦在下載先前發行的整組更新時，可能也會佔用較大的網路頻寬。|
|Service Pack|不定<br /><br />大小會因您部署的每個 Service Pack 而不同。|**不定**<br /><br />視您何時部署 Service Pack 而定。|
|軟體發佈|不定<br /><br />大小依您部署的軟體而定。|**不定**<br /><br />視您何時部署軟體而定。|

## <a name="ways-to-reduce-network-bandwidth-use"></a>減少網路頻寬用量的方式
您可以使用下列其中一或多種方法，減少 Intune 用戶端佔用的網路頻寬。

### <a name="use-a-proxy-server-to-cache-content-requests"></a>使用 Proxy 伺服器快取內容要求
Proxy 伺服器可以快取內容來減少重複的下載，並減少網際網路內容佔用的網路頻寬。

接收用戶端內容要求的快取 Proxy 伺服器可以擷取該內容，並快取網頁回應和下載。 伺服器會使用快取的資料回應用戶端的後續要求。

下列一般設定適用於快取 Intune 用戶端內容的 Proxy 伺服器。


|          設定           |           建議值           |                                                                                                  詳細資料                                                                                                  |
|----------------------------|---------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|         快取大小         |             5 GB 至 30 GB             | 這個值會根據網路中的用戶端電腦數目以及您使用的設定而不同。 為了避免系統太快刪除檔案，請根據您的環境調整快取的大小。 |
| 個別快取檔案大小 |                950 MB                 |                                                                     某些快取 Proxy 伺服器可能沒有提供這項設定。                                                                     |
|   要快取的物件類型    | HTTP<br /><br />HTTPS<br /><br />BITS |                                               Intune 封裝是背景智慧型傳送服務 (BITS) 下載作業透過 HTTP 擷取的 CAB 檔。                                               |

如需有關如何使用 Proxy 伺服器快取內容的詳細資訊，請參閱您的 Proxy 伺服器解決方案的文件。

### <a name="use-background-intelligent-transfer-service-on-computers"></a>在電腦上使用背景智慧型傳送服務
Intune 支援在 Windows 電腦上使用背景智慧型傳送服務 (BITS)，以減少在您設定的期間所使用的網路頻寬。 您可以在 Intune 代理程式原則的 [網路頻寬] 頁面上設定 BITS 的原則。

若要深入了解 BITS 和 Windows 電腦，請參閱 TechNet Library 中的[背景智慧型傳送服務](http://technet.microsoft.com/library/bb968799.aspx)。

### <a name="use-branchcache-on-computers"></a>在電腦上使用 BranchCache
Intune 用戶端可以使用 BranchCache 來減少廣域網路 (WAN) 流量。 下列作業系統支援 BranchCache：

- Windows 7
- Windows 8.0
- Windows 8.1
- Windows 10

若要使用 BranchCache，用戶端電腦必須已啟用 BranchCache，接著再完成**分散式快取模式**的設定。

根據預設，已安裝 Intune 用戶端時，電腦會啟用 BranchCache 和分散式快取模式。 不過，如果群組原則已停用 BranchCache，則 Intune 不會覆寫該原則，且 BranchCache 保持停用。

如果使用 BranchCache，請與組織中其他系統管理員合作管理群組原則和 Intune 防火牆原則。 確認他們沒有部署停用 BranchCache 或防火牆例外的原則。 如需 BranchCache 的詳細資訊，請參閱 [BranchCache 概觀](http://technet.microsoft.com/library/hh831696.aspx)。

## <a name="network-communication-requirements"></a>網路通訊需求

啟用所管理裝置和雲端服務所需網站之間的網路通訊。

Intune 使用內部部署基礎結構 (例如，安裝 Intune 軟體的伺服器)，但會提供選項來使用內部部署基礎結構 (包括 Exchange 和 Active Directory 同步處理工具)。

若要管理位於防火牆和 Proxy 伺服器後方的電腦，您必須啟用 Intune 的通訊。

-   Proxy 伺服器必須同時支援 **HTTP (80)** 和 **HTTPS (443)**，因為 Intune 用戶端會使用這兩種通訊協定
-   Intune 需要存取 manage.microsoft.com 的未驗證 Proxy 伺服器，才能進行某些工作，例如下載軟體和更新。

您可以修改個別用戶端電腦上的 Proxy 伺服器設定，也可以使用群組原則設定來變更所有位於指定之 Proxy 伺服器後方的用戶端電腦設定。


<!--
> [!NOTE] If Windows 8.1 devices haven't cached proxy server credentials, enrollment might fail because the request doesn't prompt for credentials. Enrollment fails without warning as the request wait for a connection. If users might experience this issue, instruct them to open their browser settings and save proxy server settings to enable a connection.   -->

受管理裝置需要進行可讓 [所有使用者] 穿過防火牆存取服務的設定。

下表列出 Intune 用戶端存取的連接埠和服務：

|**網域**|**IP 位址**|
|---------------------|-----------|
|login.microsoftonline.com | 更多資訊請參閱 [Office 365 URL 與 IP 位址範圍](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2) |
|portal.manage.microsoft.com<br> m.manage.microsoft.com |40.86.181.86<br>13.82.59.78<br>13.74.184.100<br>40.68.188.2<br>13.75.42.6<br>52.230.25.184 |
| sts.manage.microsoft.com | 13.93.223.241 <br>52.170.32.182 <br>52.164.224.159 <br>52.174.178.4 <br>13.75.122.143 <br>52.163.120.84|
|Manage.microsoft.com <br>i.manage.microsoft.com <br>r.manage.microsoft.com <br>a.manage.microsoft.com <br>p.manage.microsoft.com <br>EnterpriseEnrollment.manage.microsoft.com <br>EnterpriseEnrollment-s.manage.microsoft.com | 104.40.82.191 <br>13.82.96.212 <br>52.169.9.87 <br>52.174.26.23 <br>40.83.123.72 <br>13.76.177.110 <br>52.234.146.75 |
|portal.fei.msua01.manage.microsoft.com<br>m.fei.msua01.manage.microsoft.com |13.64.196.170|
|fei.msua01.manage.microsoft.com<br> portal.fei.msua01.manage.microsoft.com <br>m.fei.msua01.manage.microsoft.com |40.71.34.120 |
|fei.msua02.manage.microsoft.com<br>portal.fei.msua02.manage.microsoft.com<br>m.fei.msua02.manage.microsoft.com |13.64.198.190|
|fei.msua02.manage.microsoft.com<br>portal.fei.msua02.manage.microsoft.com<br> m.fei.msua02.manage.microsoft.com |  13.64.198.190|
|fei.msua04.manage.microsoft.com<br> portal.fei.msua04.manage.microsoft.com <br>m.fei.msua04.manage.microsoft.com |13.64.188.173|
|fei.msua04.manage.microsoft.com<br> portal.fei.msua04.manage.microsoft.com <br>m.fei.msua04.manage.microsoft.com |40.71.32.174|
|fei.msua05.manage.microsoft.com <br>portal.fei.msua05.manage.microsoft.com <br>m.fei.msua05.manage.microsoft.com |13.64.197.181 |
|fei.msua05.manage.microsoft.com <br>portal.fei.msua05.manage.microsoft.com <br>m.fei.msua05.manage.microsoft.com |40.71.38.205|
|fei.amsua0502.manage.microsoft.com <br>portal.fei.amsua0502.manage.microsoft.com <br>m.fei.amsua0502.manage.microsoft.com |13.64.191.182 |
|fei.amsua0502.manage.microsoft.com <br>portal.fei.amsua0502.manage.microsoft.com <br>m.fei.amsua0502.manage.microsoft.com |40.71.37.51 |
|fei.msua06.manage.microsoft.com <br>portal.fei.msua06.manage.microsoft.com <br>m.fei.msua06.manage.microsoft.com |40.118.250.246 |
|fei.msua06.manage.microsoft.com <br>portal.fei.msua06.manage.microsoft.com <br>m.fei.msua06.manage.microsoft.com |13.90.142.194 |
|fei.amsua0602.manage.microsoft.com <br>portal.fei.amsua0602.manage.microsoft.com <br>m.fei.amsua0602.manage.microsoft.com |13.64.250.226 |
|fei.amsua0602.manage.microsoft.com <br>portal.fei.amsua0602.manage.microsoft.com <br>m.fei.amsua0602.manage.microsoft.com |13.90.151.142 |
|fei.msub01.manage.microsoft.com <br>portal.fei.msub01.manage.microsoft.com <br>m.fei.msub01.manage.microsoft.com |52.169.155.165 |
|fei.msub01.manage.microsoft.com <br>portal.fei.msub01.manage.microsoft.com <br>m.fei.msub01.manage.microsoft.com |52.174.188.97 |
|fei.amsub0102.manage.microsoft.com <br>portal.fei.amsub0102.manage.microsoft.com <br>m.fei.amsub0102.manage.microsoft.com |52.178.190.24 |
|fei.amsub0102.manage.microsoft.com <br>portal.fei.amsub0102.manage.microsoft.com <br>m.fei.amsub0102.manage.microsoft.com |52.174.16.215 |
|fei.msub02.manage.microsoft.com <br>portal.fei.msub02.manage.microsoft.com <br>m.fei.msub02.manage.microsoft.com |40.69.69.27 |
|fei.msub02.manage.microsoft.com <br>portal.fei.msub02.manage.microsoft.com <br>m.fei.msub02.manage.microsoft.com |52.166.196.199 |
|fei.msub03.manage.microsoft.com <br>portal.fei.msub03.manage.microsoft.com <br>m.fei.msub03.manage.microsoft.com |40.69.71.164 |
|fei.msub03.manage.microsoft.com <br>portal.fei.msub03.manage.microsoft.com <br>m.fei.msub03.manage.microsoft.com |52.174.182.102 |
|fei.msub05.manage.microsoft.com <br>portal.fei.msub05.manage.microsoft.com <br>m.fei.msub05.manage.microsoft.com |40.69.78.145 |
|fei.msub05.manage.microsoft.com <br>portal.fei.msub05.manage.microsoft.com <br>m.fei.msub05.manage.microsoft.com |52.174.192.105 |
|fei.msuc01.manage.microsoft.com <br>portal.fei.msuc01.manage.microsoft.com <br>m.fei.msuc01.manage.microsoft.com |13.94.46.250|
|fei.msuc01.manage.microsoft.com <br>portal.fei.msuc01.manage.microsoft.com <br>m.fei.msuc01.manage.microsoft.com |52.163.119.15 |
|fei.msuc02.manage.microsoft.com <br>portal.fei.msuc02.manage.microsoft.com <br>m.fei.msuc02.manage.microsoft.com |13.75.124.145 |
|fei.msuc02.manage.microsoft.com <br>portal.fei.msuc02.manage.microsoft.com <br>m.fei.msuc02.manage.microsoft.com |52.163.119.5|
|fei.msuc03.manage.microsoft.com <br>portal.fei.msuc03.manage.microsoft.com <br>m.fei.msuc03.manage.microsoft.com |52.175.35.226|
|fei.msuc03.manage.microsoft.com <br>portal.fei.msuc03.manage.microsoft.com <br>m.fei.msuc03.manage.microsoft.com |52.163.119.6|
|fei.msuc05.manage.microsoft.com <br>portal.fei.msuc05.manage.microsoft.com <br>m.fei.msuc05.manage.microsoft.com |52.175.38.24|
|fei.msuc05.manage.microsoft.com <br>portal.fei.msuc05.manage.microsoft.com <br>m.fei.msuc05.manage.microsoft.com |52.163.119.3|
|fef.msua01.manage.microsoft.com|138.91.243.97|
|fef.msua02.manage.microsoft.com|52.177.194.236|
|fef.msua04.manage.microsoft.com|23.96.112.28|
|fef.msua05.manage.microsoft.com|138.91.244.151|
|fef.msua06.manage.microsoft.com|13.78.185.97|
|fef.msua07.manage.microsoft.com|52.175.208.218|
|fef.msub01.manage.microsoft.com|137.135.128.214|
|fef.msub02.manage.microsoft.com|137.135.130.29|
|fef.msub03.manage.microsoft.com|23.97.165.17|
|fef.msub05.manage.microsoft.com|23.97.166.52|
|fef.msuc01.manage.microsoft.com|52.230.19.86|
|fef.msuc02.manage.microsoft.com|23.98.66.118|
|fef.msuc03.manage.microsoft.com|23.101.0.100|
|fef.msuc05.manage.microsoft.com|52.230.16.180|
|enterpriseregistration.windows.net|52.175.211.189|

### <a name="apple-device-network-information"></a>Apple 裝置網路資訊

|         主機名稱         |                                        URL (IP 位址/子網路)                                        |  通訊協定  |     Port     |                          Device                           |
|--------------------------|-------------------------------------------------------------------------------------------------------|------------|--------------|-----------------------------------------------------------|
|      管理主控台       |                                  gateway.push.apple.com (17.0.0.0/8)                                  |    TCP     |     2195     |                    Apple iOS 和 macOS                    |
|      管理主控台       |                                  feedback.push.apple.com(17.0.0.0/8)                                  |    TCP     |     2196     |                    Apple iOS 和 macOS                    |
|      管理主控台       | Apple iTunesitunes.apple.com、\*.mzstatic.com、\*.phobos.apple.com、\*.phobos.apple.com.edgesuite.net |    HTTP    |      80      |                    Apple iOS 和 macOS                    |
|        PI 伺服器         |                gateway.push.apple.com(17.0.0.0/8) feedback.push.apple.com(17.0.0.0/8)                 |    TCP     |  2195, 2196  |         適用於 Apple iOS 和 macOS 雲端傳訊。          |
|     裝置服務      |                                        gateway.push.apple.com                                         |    TCP     |     2195     |                           Apple                           |
|     裝置服務      |                                        feedback.push.apple.com                                        |    TCP     |     2196     |                           Apple                           |
|     裝置服務      |   Apple iTunesitunes.apple.com \*.mzstatic.com\*.phobos.apple.com \*.phobos.apple.com.edgesuite.net   |    HTTP    |      80      |                           Apple                           |
| 裝置 (網際網路/Wi-Fi) |                                 #-courier.push.apple.com(17.0.0.0/8)                                  |    TCP     | 5223 和 443 | 僅限 Apple。 &#39;#&#39; 是 0 到 200 之間的亂數。 |
| 裝置 (網際網路/Wi-Fi) |                           phobos.apple.comocsp.apple.comax.itunes.apple.com                           | HTTP/HTTPS |  80 或 443   |                        僅限 Apple                         |


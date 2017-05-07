---
title: "Intune 網路頻寬用量 | Microsoft Docs"
description: "Intune 網路頻寬用量"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 03/07/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0f737d48-24bc-44cd-aadd-f0a1d59f6893
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: c8715f96f532ee6bacda231e1147d03226ecbb48
ms.openlocfilehash: 5211d2222e5e8ef9328f60ed13f0146925194c5f
ms.lasthandoff: 04/26/2017


---

# <a name="intune-network-bandwidth-use"></a>Intune 網路頻寬用量

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

本指南可協助 Intune 系統管理員了解 Intune 服務的網路需求。 您可以使用這項資訊來了解頻寬需求，以及 Proxy 設定所需的 IP 位址和連接埠設定。

## <a name="average-network-traffic"></a>平均網路流量
此表格列出每個用戶端透過網路傳輸的一般內容的估計大小和頻率。

> [!NOTE]
> 若要確保電腦和行動裝置可從 Intune 服務接收必要的更新和內容，它們必須定期連線到網際網路。 接收更新或內容所花費的時間並不固定，但如同指導方針，應保持每天至少 1 小時持續連線到網際網路。

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
您可以使用可快取內容的 Proxy 伺服器來減少重複的下載，並減少從網際網路要求內容的用戶端使用的網路頻寬。

快取 Proxy 伺服器會從網路上的用戶端電腦接收內容的要求、從網際網路擷取該內容，並可以接著快取 HTTP 回應和二進位檔下載。 伺服器會使用快取的資訊來回應 Intune 用戶端電腦的後續要求。

下列一般設定適用於快取 Intune 用戶端內容的 Proxy 伺服器。

|設定|建議值|詳細資料|
|-----------|---------------------|-----------|
|快取大小|5 GB 至 30 GB|這個值會根據網路中的用戶端電腦數目以及您使用的設定而不同。 為了避免系統太快刪除檔案，請根據您的環境調整快取的大小。|
|個別快取檔案大小|950 MB|某些快取 Proxy 伺服器可能沒有提供這項設定。|
|要快取的物件類型|HTTP<br /><br />HTTPS<br /><br />BITS|Intune 封裝是背景智慧型傳送服務 (BITS) 下載作業透過 HTTP 擷取的 CAB 檔。|
如需有關如何使用 Proxy 伺服器快取內容的詳細資訊，請參閱您的 Proxy 伺服器解決方案的文件。

### <a name="use-background-intelligent-transfer-service-on-computers"></a>在電腦上使用背景智慧型傳送服務
Intune 支援在 Windows 電腦上使用背景智慧型傳送服務 (BITS)，以減少在您設定的期間所使用的網路頻寬。 您可以在 Intune 代理程式原則的 [網路頻寬] 頁面上設定 BITS 的原則。

若要深入了解 BITS 和 Windows 電腦，請參閱 TechNet Library 中的[背景智慧型傳送服務](http://technet.microsoft.com/library/bb968799.aspx)。

### <a name="use-branchcache-on-computers"></a>在電腦上使用 BranchCache
Intune 用戶端可以使用 BranchCache 來減少廣域網路 (WAN) 流量。 下列支援作為用戶端的作業系統也支援 BranchCache：

- Windows 7
- Windows 8.0
- Windows 8.1
- Windows 10

若要使用 BranchCache，用戶端電腦必須已啟用 BranchCache，接著再完成**分散式快取模式**的設定。

根據預設，已安裝 Intune 用戶端時電腦會啟用 BranchCache 和分散式快取模式。 不過，如果用戶端已有停用 BranchCache 的群組原則，Intune 不會覆寫該原則，因此 BranchCache 將在該部電腦上維持停用狀態。

如果使用 BranchCache，您應該與組織中負責管理群組原則和 Intune 防火牆原則的其他系統管理員溝通，確認他們沒有部署停用 BranchCache 或防火牆例外的原則。 如需 BranchCache 的詳細資訊，請參閱 [BranchCache 概觀](http://technet.microsoft.com/library/hh831696.aspx)。

## <a name="network-communication-requirements"></a>網路通訊需求

您必須在所管理的裝置和用來管理 Intune 訂閱的裝置，以及雲端服務所需的網站之間，啟用網路通訊。

Intune 使用內部部署基礎結構 (例如，安裝 Intune 軟體的伺服器)，但會提供選項來使用內部部署基礎結構 (包括 Exchange 和 Active Directory 同步處理工具)。

若要管理位於防火牆和 Proxy 伺服器後方的電腦，您必須將防火牆和 Proxy 伺服器設定為允許 Intune 進行通訊。

### <a name="requirements-for-proxy-servers"></a>Proxy 伺服器的需求
若要管理位於 Proxy 伺服器後方的電腦，請注意︰

-   Proxy 伺服器必須同時支援 **HTTP** 和 **HTTPS**，因為 Intune 用戶端會使用這兩種通訊協定
-   Intune 支援未經驗證的 Proxy 伺服器

您可以修改個別用戶端電腦上的 Proxy 伺服器設定，也可以使用群組原則設定來變更所有位於指定之 Proxy 伺服器後方的用戶端電腦設定。

### <a name="requirements-for-firewalls-ports-and-domains"></a>防火牆、連接埠和網域的需求
受管理裝置需要進行可讓 [所有使用者] 穿過防火牆存取服務的設定。

下表列出 Intune 用戶端存取的連接埠和服務。

|**網域**|**連接埠**|**IP 位址**|
|------|----|---|
|manage.microsoft.com<br>a.manage.microsoft.com<br>admin.manage.microsoft.com<br>enterpriseenrollment.manage.microsoft.com<br>enterpriseenrollment-s.manage.microsoft.com<br>i.manage.microsoft.com<br>p.manage.microsoft.com<br>r.manage.microsoft.com|80 和 443|134.170.168.254<br>134.170.51.126
|m.manage.microsoft.com|80 和 443| 13.91.59.243<br>40.68.30.140
|portal.manage.microsoft.com|80 和 443|40.121.50.69<br>52.169.30.159
|account.manage.microsoft.com|80 和 443|157.56.13.59
|fef.msua01.manage.microsoft.com|80 和 443|138.91.243.97
|fef.msua02.manage.microsoft.com|80 和 443|23.96.112.46
|fef.msua04.manage.microsoft.com|80 和 443|23.96.112.28
|fef.msua05.manage.microsoft.com|80 和 443|138.91.244.151
|fef.msub01.manage.microsoft.com|80 和 443|137.135.128.214
|fef.msub02.manage.microsoft.com|80 和 443|137.135.130.29
|fef.msub03.manage.microsoft.com|80 和 443|23.97.165.17
|fef.msub05.manage.microsoft.com|80 和 443|23.97.166.52
|fef.msuc01.manage.microsoft.com|80 和 443|207.46.225.1
|fef.msuc02.manage.microsoft.com|80 和 443|23.98.66.118
|fef.msuc03.manage.microsoft.com|80 和 443|23.101.0.100
|fef.msuc05.manage.microsoft.com|80 和 443|207.46.154.33
|fef.msua06.manage.microsoft.com|80 和 443|104.42.188.1
|fei.msua01.manage.microsoft.com|80 和 443|138.91.240.131
|fei.msua02.manage.microsoft.com|80 和 443|23.96.112.143
|fei.msua04.manage.microsoft.com|80 和 443|23.96.112.147
|fei.msua05.manage.microsoft.com|80 和 443|138.91.240.163
|fei.msub01.manage.microsoft.com|80 和 443|137.135.130.85
|fei.msub02.manage.microsoft.com|80 和 443|137.135.132.149
|fei.msub03.manage.microsoft.com|80 和 443|23.97.160.232
|fei.msub05.manage.microsoft.com|80 和 443|23.97.162.250
|fei.msuc01.manage.microsoft.com|80 和 443|207.46.224.73
|fei.msuc02.manage.microsoft.com|80 和 443|23.98.66.194
|fei.msuc03.manage.microsoft.com|80 和 443|23.101.2.105
|fei.msuc05.manage.microsoft.com|80 和 443|207.46.147.126
|fei.msua06.manage.microsoft.com|80 和 443|138.91.149.190
|m.fei.msua01.manage.microsoft.com|80 和 443|138.91.240.131
|m.fei.msua02.manage.microsoft.com|80 和 443|23.96.112.143
|m.fei.msua04.manage.microsoft.com|80 和 443|23.96.112.147
|m.fei.msua05.manage.microsoft.com|80 和 443|138.91.240.163
|m.fei.msub01.manage.microsoft.com|80 和 443|137.135.130.85
|m.fei.msub02.manage.microsoft.com|80 和 443|137.135.132.149
|m.fei.msub03.manage.microsoft.com|80 和 443|23.97.160.232
|m.fei.msub05.manage.microsoft.com|80 和 443|23.97.162.250
|m.fei.msuc01.manage.microsoft.com|80 和 443|207.46.224.73
|m.fei.msuc02.manage.microsoft.com|80 和 443|23.98.66.194
|m.fei.msuc03.manage.microsoft.com|80 和 443|23.101.2.105
|m.fei.msuc05.manage.microsoft.com|80 和 443|207.46.147.126
|m.fei.msua06.manage.microsoft.com|80 和 443|138.91.149.190
|m.msua01.manage.microsoft.com|80 和 443|157.55.50.182
|m.msua02.manage.microsoft.com|80 和 443|134.170.49.121
|m.msua04.manage.microsoft.com|80 和 443|134.170.49.126
|m.msua05.manage.microsoft.com|80 和 443|157.55.240.190
|m.msua06.manage.microsoft.com|80 和 443|134.170.49.114
|m.msub01.manage.microsoft.com|80 和 443|94.245.121.50
|m.msub02.manage.microsoft.com|80 和 443|94.245.121.58
|m.msub03.manage.microsoft.com|80 和 443|94.245.121.56
|m.msub05.manage.microsoft.com|80 和 443|157.56.113.123
|m.msuc01.manage.microsoft.com|80 和 443|104.44.84.187
|m.msuc02.manage.microsoft.com|80 和 443|104.44.84.188
|m.msuc03.manage.microsoft.com|80 和 443|104.44.84.189
|m.msuc05.manage.microsoft.com|80 和 443|111.221.76.60
|msua01.manage.microsoft.com|80 和 443|157.55.50.182
|msua02.manage.microsoft.com|80 和 443|134.170.49.121
|msua04.manage.microsoft.com|80 和 443|134.170.49.126
|msua05.manage.microsoft.com|80 和 443|157.55.240.190
|msub01.manage.microsoft.com|80 和 443|94.245.121.50
|msub02.manage.microsoft.com|80 和 443|94.245.121.58
|msub03.manage.microsoft.com|80 和 443|94.245.121.56
|msub05.manage.microsoft.com|80 和 443|157.56.113.123
|msuc01.manage.microsoft.com|80 和 443|104.44.84.187
|msuc02.manage.microsoft.com|80 和 443|104.44.84.188
|msuc03.manage.microsoft.com|80 和 443|104.44.84.189
|msuc05.manage.microsoft.com|80 和 443|111.221.76.60
|msua06.manage.microsoft.com|80 和 443|134.170.49.114
|ncufun.account.manage.microsoft.com|80 和 443|157.55.252.224
|neufun.account.manage.microsoft.com|80 和 443|65.52.229.134
|portal.fei.msua01.manage.microsoft.com|80 和 443|138.91.240.131
|portal.fei.msua02.manage.microsoft.com|80 和 443|23.96.112.143
|portal.fei.msua04.manage.microsoft.com|80 和 443|23.96.112.147
|portal.fei.msua05.manage.microsoft.com|80 和 443|138.91.240.163
|portal.fei.msub01.manage.microsoft.com|80 和 443|137.135.130.85
|portal.fei.msub02.manage.microsoft.com|80 和 443|137.135.132.149
|portal.fei.msub03.manage.microsoft.com|80 和 443|23.97.160.232
|portal.fei.msub05.manage.microsoft.com|80 和 443|23.97.162.250
|portal.fei.msuc01.manage.microsoft.com|80 和 443|207.46.224.73
|portal.fei.msuc02.manage.microsoft.com|80 和 443|23.98.66.194
|portal.fei.msuc03.manage.microsoft.com|80 和 443|23.101.2.105
|portal.fei.msuc05.manage.microsoft.com|80 和 443|207.46.147.126
|portal.fei.msua06.manage.microsoft.com|80 和 443|138.91.149.190
|portal.msua01.manage.microsoft.com|80 和 443|157.55.50.182
|portal.msua02.manage.microsoft.com|80 和 443|134.170.49.121
|portal.msua04.manage.microsoft.com|80 和 443|134.170.49.126
|portal.msua05.manage.microsoft.com|80 和 443|157.55.240.190
|portal.msub01.manage.microsoft.com|80 和 443|94.245.121.50
|portal.msub02.manage.microsoft.com|80 和 443|94.245.121.58
|portal.msub03.manage.microsoft.com|80 和 443|94.245.121.56
|portal.msub05.manage.microsoft.com|80 和 443|157.56.113.123
|portal.msuc01.manage.microsoft.com|80 和 443|104.44.84.187
|portal.msuc02.manage.microsoft.com|80 和 443|104.44.84.188
|portal.msuc03.manage.microsoft.com|80 和 443|104.44.84.189
|portal.msuc05.manage.microsoft.com|80 和 443|111.221.76.60
|portal.msua06.manage.microsoft.com|80 和 443|134.170.49.114
|ssu2.manage.microsoft.com|80 和 443|157.55.99.181
|status.manage.microsoft.com|80 和 443|157.55.99.170
|swda01.manage.microsoft.com<br>swda02.manage.microsoft.com<br>swdb01.manage.microsoft.com<br>swdb02.manage.microsoft.com<br>swdc01.manage.microsoft.com<br>swdc02.manage.microsoft.com|80 和 443|93.184.215.200
|*.microsoftonline-p.com|80 和 443||
|has.spserv.microsoft.com<br>裝置健康情況證明服務所需|443||
|*.microsoftonline-p.net|80 和 443||
|*.portal.office.com|80 和 443||
|*.spynet2.microsoft.com|443||
|c.microsoft.com|80 和 443||
|c1.microsoft.com|80 和 443||
|blob.core.windows.net|80 和 443||
|ajax.aspnetcdn.com|80 和 443||
|*.googleapis.com<br>當您使用公司入口網站時，需要有這個網域才能提供 JQuery 支援。|80 和 443||
|wustat.microsoft.com|80 和 443||
|Microsoft Update 服務|\*.update.microsoft.com<br>download.microsoft.com<br>update.microsoft.com<br>\*.download.windowsupdate.com<br>download.windowsupdate.com<br>\*.windowsupdate.com<br>windowsupdate.microsoft.com<br>ntservicepack.microsoft.com|80 和 443|
|DNS 查閱要求|manage.microsoft.com.nsatc.net|80|
|透過防火牆的 Samsung KNOX Standard 裝置通訊|若要啟用 Samsung KNOX Standard 裝置以透過防火牆來連接 KNOX Standard 伺服器，請依照＜Samsung KNOX Standard 常見問題集＞中的指示執行。||
|條件式存取的通訊|443|204.79.197.200|
|文件、說明及支援：</br></br>*.livemeeting.com<br>\*.microsoftonline.com<br>\*.social.technet.microsoft.com<br>blogs.technet.com<br>go.microsoft.com<br>onlinehelp.microsoft.com<br>www.microsoft.com|80|||


>[!div class="step-by-step"]

>[&larr; **必要條件**](what-to-know-before-you-start-microsoft-intune.md)     [**訂閱** &rarr;](start-with-a-paid-subscription-to-microsoft-intune-step-1.md)  


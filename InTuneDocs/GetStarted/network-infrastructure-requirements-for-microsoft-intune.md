---
title: "網路基礎結構需求 | Microsoft Intune"
description: "Intune 防火牆、連接埠、網域和 Proxy 伺服器需求"
keywords: 
author: barlanmsft
manager: angrobe
ms.date: 08/29/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 074de65b-84a5-4a01-a824-18ffd838eab0
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 073e3df63a5de9cf92c739c1ced858e21a9ac351
ms.openlocfilehash: aa4d2219a5962d83b80630ed3a09660a76469764


---

# 適用於 Microsoft Intune 的網路基礎結構需求
設定 Microsoft Intune 之前，請檢閱本主題及[啟動 Microsoft Intune 前的須知事項](what-to-know-before-you-start-microsoft-intune.md)中列示的其他需求。

本主題列出可讓您的網路基礎結構在您所管理並用來管理 Intune 訂用帳戶的裝置，以及網際網路上雲端式服務使用的網站之間傳遞通訊的需求。

雖然此服務並無使用內部部署基礎結構 (例如必須安裝軟體的伺服器) 的需求，但卻提供使用內部部署基礎結構 (包括 Exchange 和 Active Directory 同步處理工具) 的選項。

若要管理位於防火牆和 Proxy 伺服器後方的電腦，您必須將防火牆和 Proxy 伺服器設定為允許 Intune 進行通訊。

## 防火牆、連接埠和網域的需求
受管理裝置需要進行可讓 [所有使用者] 穿過防火牆存取各種服務的組態。

下表列出 Intune 用戶端存取的連接埠和服務。


|**Domain**|**連接埠**|**IP 位址**|
|------|----|---|
|manage.microsoft.com<br>a.manage.microsoft.com<br>admin.manage.microsoft.com<br>enterpriseenrollment.manage.microsoft.com<br>enterpriseenrollment-s.manage.microsoft.com<br>i.manage.microsoft.com<br>m.manage.microsoft.com<br>p.manage.microsoft.com<br>portal.manage.microsoft.com<br>r.manage.microsoft.com|80 和 443|134.170.168.254<br>134.170.51.126
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
|透過防火牆的 Samsung KNOX 裝置通訊|若要啟用 Samsung KNOX 裝置以透過防火牆來連接 KNOX 伺服器，請依照＜Samsung KNOX 常見問題集＞中的指示執行。||
|條件式存取的通訊|443|204.79.197.200|
|文件、說明及支援：</br></br>* livemeeting.com<br>\*.microsoftonline.com<br>\*.social.technet.microsoft.com<br>blogs.technet.com<br>go.microsoft.com<br>onlinehelp.microsoft.com<br>www.microsoft.com|80|||



## Proxy 伺服器的需求
若要管理位於 Proxy 伺服器後方的電腦，請注意︰

-   Proxy 伺服器必須同時支援 **HTTP** 和 **HTTPS**，因為 Intune 用戶端會使用這兩種通訊協定。

-   Intune 支援未經驗證的 Proxy 伺服器。

您可以修改個別用戶端電腦上的 Proxy 伺服器設定，也可以使用群組原則設定來變更所有位於指定之 Proxy 伺服器後方的用戶端電腦設定。

您還可以使用 Proxy 伺服器來快取內容，以減少 Intune 用戶端的[網路頻寬用量](network-bandwidth-use.md)。


### 請參閱
[啟動 Microsoft Intune 前的須知事項](what-to-know-before-you-start-microsoft-intune.md)



<!--HONumber=Sep16_HO2-->



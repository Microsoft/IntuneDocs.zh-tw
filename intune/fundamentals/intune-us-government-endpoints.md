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
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: kerimh
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 490c939e79659baac655cfd7d3d3a2ee10d98382
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2019
ms.locfileid: "71726046"
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

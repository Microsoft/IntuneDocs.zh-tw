---
title: Microsoft Intune 的網路需求與頻寬詳細資料
titleSuffix: ''
description: 檢閱 Intune 的網路設定需求與頻寬詳細資料。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/17/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 0f737d48-24bc-44cd-aadd-f0a1d59f6893
ms.reviewer: kerimh
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5b4983031d0e5d0723e306a1b9cbefadac2f91fe
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2019
ms.locfileid: "71727424"
---
# <a name="intune-network-configuration-requirements-and-bandwidth"></a>Intune 網路設定需求與頻寬

[!INCLUDE [both-portals](../../intune-classic/includes/note-for-both-portals.md)]

您可以使用此資訊來了解 Intune 部署的頻寬需求。

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
> [!NOTE]
> 如果您使用 Proxy 伺服器快取內容要求，此時只會將用戶端到 Proxy 和 Proxy 到 Intune 之間的通訊加密。 用戶端至 Intune 的端至端連線不會加密。

如需有關如何使用 Proxy 伺服器快取內容的詳細資訊，請參閱您的 Proxy 伺服器解決方案的文件。

### <a name="use-background-intelligent-transfer-service-bits-on-computers"></a>在電腦上使用背景智慧型傳送服務 (BITS)
您可以在自己設定的小時時間內，於 Windows 電腦上使用 BITS 以減少網路頻寬。 您可以在 Intune 代理程式原則的 [網路頻寬]  頁面中設定 BITS 原則。

> [!NOTE]
> 對於 Windows 上的 MDM 管理，只有 MobileMSI 應用程式類型的作業系統管理介面會使用 BITS 進行下載。 AppX/MsiX 會使用自己的非 BITS 下載堆疊，而且 Win32 應用程式會透過 Intune 代理程式使用傳遞最佳化，而非 BITS。

若要深入了解 BITS 和 Windows 電腦，請參閱 TechNet Library 中的[背景智慧型傳送服務](https://technet.microsoft.com/library/bb968799.aspx)。

### <a name="delivery-optimization"></a>傳遞最佳化
傳遞最佳化讓您能夠使用 Intune，來減少您的 Windows 10 裝置下載應用程式和更新時的頻寬耗用量。 藉由使用自我組織的分散式快取，您可以從傳統伺服器和替代來源 (例如網路對等) 提取下載。

若要查看傳遞最佳化所支援的 Windows 10 版本和內容類型的完整清單，請參閱[適用於 Windows 10 更新的傳遞最佳化](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization#requirements) \(部分機器翻譯\) 一文。

您可以[設定傳遞最佳化](../configuration/delivery-optimization-settings.md)作為裝置組態設定檔的一部分。


### <a name="use-branchcache-on-computers"></a>在電腦上使用 BranchCache
Intune 用戶端可以使用 BranchCache 來減少廣域網路 (WAN) 流量。 下列作業系統支援 BranchCache：

- Windows 7
- Windows 8.0
- Windows 8.1
- Windows 10

若要使用 BranchCache，用戶端電腦必須已啟用 BranchCache，接著再完成**分散式快取模式**的設定。

在電腦上安裝 Intune 用戶端時，預設會啟用 BranchCache 和分散式快取模式。 但如果群組原則已停用 BranchCache，Intune 不會覆寫該原則，因此 BranchCache 會保持停用。

如果使用 BranchCache，請與組織中其他系統管理員合作管理群組原則和 Intune 防火牆原則。 請確定他們沒有部署停用 BranchCache 或防火牆例外的原則。 如需 BranchCache 的詳細資訊，請參閱 [BranchCache 概觀](https://technet.microsoft.com/library/hh831696.aspx)。

> [!NOTE]
> 您可以使用 Microsoft Intune 來管理 Windows 電腦，以[作為具備行動裝置管理 (MDM) 的行動裝置](../enrollment/windows-enroll.md)或作為具備 Intune 軟體用戶端的電腦。 Microsoft 建議客戶盡可能[使用 MDM 管理解決方案](../enrollment/windows-enroll.md)。 以這種方式管理時，不支援 BranchCache。 如需詳細資訊，請參閱[比較作為電腦或行動裝置來管理 Windows 電腦](../pc-management-comparison.md)。


## <a name="next-steps"></a>後續步驟

[檢閱 Intune 的端點](../intune-endpoints.md)


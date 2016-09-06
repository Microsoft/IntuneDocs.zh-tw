---
title: "Intune 網路頻寬用量 | Microsoft Intune"
description: "Intune 網路頻寬用量"
keywords: 
author: barlanmsft
manager: angrobe
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0f737d48-24bc-44cd-aadd-f0a1d59f6893
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 6d1c7c670341692d4ea0c823e4a9a96746b83067
ms.openlocfilehash: 6534eb7bbff2fba39e1dfa9be4ad01196156cc15


---

# Intune 網路頻寬用量

設定 [!INCLUDE[wit_firstref](../includes/wit_firstref_md.md)] 之前，請檢閱本主題及[啟動 Microsoft Intune 前的須知事項](what-to-know-before-you-start-microsoft-intune.md)中列出的其他需求。

請使用下列各節中的資訊，規劃 [!INCLUDE[wit_firstref](../includes/wit_firstref_md.md)] 用戶端的網路流量。

## 平均網路流量
下表列出每個用戶端透過網路傳輸的一般內容的估計大小和頻率。

> [!NOTE]
> 若要確保電腦和行動裝置從 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 服務接收必要的更新和內容，它們必須定期連線到網際網路。 接收更新或內容所花費的時間並不固定，但如同指導方針，應保持每天至少 1 小時持續連線到網際網路。

|內容類型|大小近似值|頻率和詳細資料|
|----------------|--------------------|-------------------------|
|[!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 用戶端安裝<br /><br />**以下是除了安裝 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 用戶端以外的需求**|125 MB|**一次**<br /><br />用戶端下載的大小會因用戶端電腦的作業系統而不同。|
|用戶端註冊套件|15 MB|**一次**<br /><br />當此內容類型有更新時，可能會進行其他下載。|
|Endpoint Protection 代理程式|65 MB|**一次**<br /><br />當此內容類型有更新時，可能會進行其他下載。|
|Operations Manager 代理程式|11 MB|**一次**<br /><br />當此內容類型有更新時，可能會進行其他下載。|
|原則代理程式|3 MB|**一次**<br /><br />當此內容類型有更新時，可能會進行其他下載。|
|Remote Assistance via Microsoft Easy Assist 代理程式|6 MB|**一次**<br /><br />當此內容類型有更新時，可能會進行其他下載。|
|日常用戶端作業|6 MB|**每日**<br /><br />[!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 用戶端會定期與 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 服務通訊，以檢查是否有更新和原則，並將用戶端的狀態回報給服務。|
|Endpoint Protection 惡意程式碼定義更新|不定<br /><br />通常為 40 KB 到 2 MB|**每日**<br /><br />最多一天 3 次。|
|Endpoint Protection 引擎更新|5 MB|**每月**|
|軟體更新|不定<br /><br />大小依您部署的更新而定。|**每月**<br /><br />一般情況下，軟體更新會在每個月的第二個星期二發佈。<br /><br />剛完成註冊或部署的電腦在下載先前發行的整組更新時，可能也會佔用較大的網路頻寬。|
|Service Pack|不定<br /><br />大小會因您部署的每個 Service Pack 而不同。|**不定**<br /><br />視您何時部署 Service Pack 而定。|
|軟體發佈|不定<br /><br />大小依您部署的軟體而定。|**不定**<br /><br />視您何時部署軟體而定。|

## 減少網路頻寬用量的方式
您可以使用下列其中一種或多種方法，減少 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 用戶端佔用的網路頻寬。

### 使用 Proxy 伺服器快取內容要求
您可以使用可快取內容的 Proxy 伺服器來減少重複的下載，並減少從網際網路要求內容的用戶端使用的網路頻寬。

快取 Proxy 伺服器會從網路上的用戶端電腦接收內容的要求、從網際網路擷取該內容，並可以接著快取 HTTP 回應和二進位檔下載。 伺服器會使用快取的資訊回應 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 用戶端電腦的後續要求。

下列一般設定適用於快取 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 用戶端內容的 Proxy 伺服器。

|設定|建議值|詳細資料|
|-----------|---------------------|-----------|
|快取大小|5 GB 至 30 GB|這個值會根據網路中的用戶端電腦數目以及您使用的設定而不同。 為了避免系統太快刪除檔案，請根據您的環境調整快取的大小。|
|個別快取檔案大小|950 MB|某些快取 Proxy 伺服器可能沒有提供這項設定。|
|要快取的物件類型|HTTP<br /><br />HTTPS<br /><br />BITS|[!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 套件是背景智慧型傳送服務 (BITS) 下載作業透過 HTTP 擷取的 CAB 檔。|
如需有關如何使用 Proxy 伺服器快取內容的詳細資訊，請參閱您的 Proxy 伺服器解決方案的文件。

### 在電腦上使用背景智慧型傳送服務
[!INCLUDE[wit_firstref](../includes/wit_firstref_md.md)] 支援在 Windows 電腦上使用背景智慧型傳送服務 (BITS)，以減少在您設定的期間所使用的網路頻寬。 您可以在 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 代理程式原則的 [網路頻寬] 頁面上設定 BITS 的原則。

若要深入了解 BITS 和 Windows 電腦，請參閱 TechNet Library 中的[背景智慧型傳送服務](http://technet.microsoft.com/library/bb968799.aspx)。

### 在電腦上使用 BranchCache
[!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 用戶端可以使用 BranchCache 來減少廣域網路 (WAN) 流量。 下列支援作為用戶端的作業系統也支援 BranchCache：

-   [!INCLUDE[nextref_client_7](../includes/nextref_client_7_md.md)]

-   [!INCLUDE[win8_client_2](../includes/win8_client_2_md.md)]

-   [!INCLUDE[winblue_client_2](../includes/winblue_client_2_md.md)]

若要使用 BranchCache，用戶端電腦必須已啟用 BranchCache，接著再完成**分散式快取模式**的設定。

根據預設，已安裝 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 用戶端時電腦會啟用 BranchCache 和分散式快取模式。 不過，如果用戶端已有停用 BranchCache 的群組原則，[!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 不會覆寫該原則，因此 BranchCache 將在該部電腦上維持停用狀態。

如果使用 BranchCache，您應該與組織中負責管理群組原則和 [!INCLUDE[wit_firstref](../includes/wit_firstref_md.md)] 防火牆原則的其他系統管理員溝通，確認他們沒有部署停用 BranchCache 或防火牆例外的原則。 如需 BranchCache 的詳細資訊，請參閱 [BranchCache 概觀](http://technet.microsoft.com/library/hh831696.aspx)。

### 請參閱
[啟動 Microsoft Intune 前的須知事項](what-to-know-before-you-start-microsoft-intune.md)



<!--HONumber=Aug16_HO4-->



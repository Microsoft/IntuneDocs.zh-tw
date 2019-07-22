---
title: 應用程式實體的參考
titleSuffix: Microsoft Intune
description: Intune 資料倉儲 API 中的實體集合應用程式類別的參考主題。
keywords: Intune 資料倉儲
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/09/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: A92DEF30-5D01-4774-9917-E26F5F0E2E68
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: a5436de6b972e5cbe8b2b17d42f0974cb38df47e
ms.sourcegitcommit: c3ac858bbadb63d248ed54069e48160d703bbaf2
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 07/18/2019
ms.locfileid: "68313803"
---
# <a name="reference-for-application-entities"></a>應用程式實體的參考

[應用程式]  類別包含的行動裝置實體，可追蹤下列資訊：

- 應用程式的版本
- 應用程式的安裝來源
- 建立應用程式的開發人員類型
- 應用程式的受管理軟體類型，例如 **sidecar** 或**桌面**。
- 應用程式的大量採購方案 (VPP) 狀態

## <a name="apprevisions"></a>appRevisions

**AppRevision** 實體會列出應用程式的所有版本。

| 屬性  | 說明 | 範例 |
|---------|------------|--------|
| appKey |應用程式的唯一識別碼。 |123 |
| applicationId |應用程式的唯一識別碼 - 類似 AppKey，但此金鑰是自然的。 |b66bc706-ffff-7437-0340-032819502773 |
| revision |管理員在上傳二進位檔期間提及的版本。 |2 |
| title |應用程式的標題。 |Excel |
| publisher |應用程式的發行者。 |Microsoft |
| uploadState |應用程式的上傳狀態。 |1 |
| appTypeKey |下節要說明的 AppType 參考。 | |
| vppProgramTypeKey |後文要說明的 VppProgramType 參考。 | |
| creationTime |此修訂建立的時間。 |11/23/2016 12:00:00 AM |
| modifiedTime |此修訂任何相關項目前次變更的時間。 |11/23/2016 12:00:00 AM |
| 大小 |二進位檔的大小。 | |
| startDateInclusiveUTC |此應用程式修訂在資料倉儲中建立的 UTC 日期和時間。 |11/23/2016 12:00:00 AM |
| endDateExclusiveUTC |此應用程式修訂開始淘汰的 UTC 日期和時間。 |11/23/2016 12:00:00 AM |
| isCurrent |指出資料倉儲目前是否有此應用程式版本。 |True/False |
| rowLastModifiedDateTimeUTC |此應用程式修訂前次在資料倉儲中修改的 UTC 日期和時間。 |11/23/2016 12:00:00 AM |

## <a name="apptypes"></a>appTypes

**appType** 實體會列出應用程式的安裝來源。

| 屬性  | 說明 |
|---------|------------|
| appTypeID |類型識別碼 |
| appTypeKey |索引鍵的 Surrogate 索引鍵 |
| appTypeName |應用程式類型 |

### <a name="example"></a>範例

| AppTypeID  | 名稱 | 說明 |
|---------|------------|--------|
| 0 |Android 市集應用程式 | Android 市集應用程式。 |
| 1 |Android LOB 應用程式 | Android 企業營運應用程式。 |
| 2 |受管理的 Android 市集應用程式 (MAM) | 啟用管理的 Android 市集應用程式。 |
| 3 |iOS 市集應用程式 | iOS 市集應用程式。 |
| 4 |iOS LOB 應用程式 | iOS 企業營運應用程式。 |
| 5 |受管理的 iOS 市集應用程式 (MAM？) | 啟用管理的 iOS 市集應用程式。 |
| 6 |O365 Pro Plus 套件 | Office 365 Pro Plus Suite for Windows 10。 |
| 7 |Web 應用程式 | Web 應用程式。 |
| 8 |Windows Phone 8.1 市集應用程式 | Windows Phone 8.1 市集應用程式。 |
| 9 |Windows 市集應用程式 | Windows 市集應用程式。 |
| 10 |Windows LOB 應用程式 | Windows AppX 企業營運應用程式。 |
| 11 |Windows Mobile MSI | MSI 企業營運應用程式。 |
| 12 |Windows Phone LOB 應用程式 | Windows Phone 企業營運應用程式。 |


## <a name="vppprogramtypes"></a>vppProgramTypes

**vppProgramType** 實體會列出應用程式可能的 VPP 方案類型。

| 屬性  | 說明 |
|---------|------------|
| vppProgramTypeID | 類型識別碼。 |
| vppProgramTypeKey | 索引鍵的 Surrogate 索引鍵。 |
| vppProgramTypeName | VPP 方案類型。 |

### <a name="example"></a>範例

| VppProgramID  | 名稱 | 說明 |
|---------|------------|--------|
| 3DDA2474-470B-4503-9830-2665C21C1945 | Microsoft | Microsoft 的 VPP 方案。 |
| 00000000-0000-0000-0000-000000000000 | 尚未提供 | 預設值為 [無 VPP]。 |
| B54814E0-68EA-4BA4-8088-B5AAB58E737B | Apple | Apple 的 VPP 方案。 |



## <a name="applicationinventories"></a>applicationInventories

**applicationInventory** 實體列出清查收集期間在裝置上找到的應用程式。

| 屬性  | 說明 |
|---------|------------|
| deviceKey | 這是包含 Intune 裝置識別碼的裝置資料表參考。 |
| dateKey | 表示清查當日的日期資料表參考。 |
| applicationName | 應用程式的名稱。 |
| applicationVersion | 應用程式的版本。 |
| bundleSize | 以位元組為單位的應用程式大小。 |

## <a name="mobileappinstallstates"></a>mobileAppInstallStates

**mobileAppInstallState** 實體代表行動應用程式在被指派至包含裝置、使用者或兩者的群組之後的安裝狀態。

| 屬性 | 說明 |
|---|---|
| appInstallStateKey | 您帳戶之應用程式安裝狀態的唯一識別碼。 |
| appInstallState | 應用程式安裝狀態的列舉值。 |
| appInstallStateName | 應用程式安裝狀態的名稱。 |




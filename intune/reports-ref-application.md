---
title: 應用程式實體的參考
titlesuffix: Microsoft Intune
description: Intune 資料倉儲 API 中的實體集合應用程式類別的參考主題。
keywords: Intune 資料倉儲
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/06/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: A92DEF30-5D01-4774-9917-E26F5F0E2E68
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: ec227fc3057f80e94ae58ce68c19f06b7dba8bc5
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/07/2019
ms.locfileid: "55848469"
---
# <a name="reference-for-application-entities"></a>應用程式實體的參考

[應用程式] 類別包含的行動裝置實體，可追蹤下列資訊：

  -  應用程式的版本
  -  應用程式的安裝來源
  -  建立應用程式的開發人員類型
  -  應用程式的受管理軟體類型，例如 **sidecar** 或**桌面**。
  -  應用程式的大量採購方案 (VPP) 狀態

## <a name="apprevision"></a>AppRevision

**AppRevision** 實體會列出應用程式的所有版本。

| 屬性  | 說明 | 範例 |
|---------|------------|--------|
| AppKey |應用程式的唯一識別碼。 |123 |
| ApplicationId |應用程式的唯一識別碼 - 類似 AppKey，但此金鑰是自然的。 |b66bc706-ffff-7437-0340-032819502773 |
| 修訂 |管理員在上傳二進位檔期間提及的版本。 |2 |
| 標題 |應用程式的標題。 |Excel |
| 發佈者 |應用程式的發行者。 |Microsoft |
| UploadState |應用程式的上傳狀態。 |1 |
| AppTypeKey |下節要說明的 AppType 參考。 | |
| VppProgramTypeKey |後文要說明的 VppProgramType 參考。 | |
| CreationTime |此修訂建立的時間。 |11/23/2016 12:00:00 AM |
| ModifiedTime |此修訂任何相關項目前次變更的時間。 |11/23/2016 12:00:00 AM |
| Size |二進位檔的大小。 | |
| StartDateInclusiveUTC |此應用程式修訂在資料倉儲中建立的 UTC 日期和時間。 |11/23/2016 12:00:00 AM |
| EndDateExclusiveUTC |此應用程式修訂開始淘汰的 UTC 日期和時間。 |11/23/2016 12:00:00 AM |
| IsCurrent |指出資料倉儲目前是否有此應用程式版本。 |True/False |
| RowLastModifiedDateTimeUTC |此應用程式修訂前次在資料倉儲中修改的 UTC 日期和時間。 |11/23/2016 12:00:00 AM |

## <a name="apptypes"></a>AppTypes

**AppTypes** 實體會列出應用程式的安裝來源。

| 屬性  | 說明 |
|---------|------------|
| AppTypeID |類型識別碼 |
| AppTypeKey |索引鍵的 Surrogate 索引鍵 |
| AppTypeName |應用程式類型 |

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


## <a name="vppprogramtypes"></a>VppProgramTypes

**VppProgramTypes** 實體會列出應用程式可能的 VPP 方案類型。

| 屬性  | 說明 |
|---------|------------|
| VppProgramTypeID | 類型識別碼。 |
| VppProgramTypeKey | 索引鍵的 Surrogate 索引鍵。 |
| VppProgramTypeName | VPP 方案類型。 |

### <a name="example"></a>範例

| VppProgramID  | 名稱 | 說明 |
|---------|------------|--------|
| 3DDA2474-470B-4503-9830-2665C21C1945 | Microsoft | Microsoft 的 VPP 方案。 |
| 00000000-0000-0000-0000-000000000000 | 尚未提供 | 預設值為 [無 VPP]。 |
| B54814E0-68EA-4BA4-8088-B5AAB58E737B | Apple | Apple 的 VPP 方案。 |



## <a name="applicationinventory"></a>ApplicationInventory

**ApplicationInventory** 實體會列出清查收集期間在裝置上找到的應用程式。

| 屬性  | 說明 |
|---------|------------|
| DeviceKey | 這是包含 Intune 裝置識別碼的裝置資料表參考。 |
| DateKey | 表示清查當日的日期資料表參考。 |
| ApplicationName | 應用程式的名稱。 |
| ApplicationVersion | 應用程式的版本。 |
| BundleSize | 以位元組為單位的應用程式大小。 |

## <a name="mobileappinstallstate"></a>MobileAppInstallState

**MobileAppInstallState** 實體代表行動應用程式在被指派至包含裝置或使用者 (或兩者) 的群組之後的安裝狀態。

| 屬性 | 說明 |
|---|---|
| AppInstallStateKey | 您帳戶之應用程式安裝狀態的唯一識別碼。 |
| AppInstallState | 應用程式安裝狀態的列舉值。 |
| AppInstallStateName | 應用程式安裝狀態的名稱。 |

## <a name="mobileappdeviceuserinstallstatus"></a>MobileAppDeviceUserInstallStatus

**MobileAppDeviceUserInstallStatus** 代表針對特定裝置或使用者的行動應用程式安裝狀態。


|      屬性      |                                                         說明                                                         |
|--------------------|-----------------------------------------------------------------------------------------------------------------------------|
|      DateKey       |                                  記錄應用程式安裝狀態之日期的索引鍵。                                  |
|       AppKey       |                             用來識別 AppRevision 執行個體之行動應用程式的索引鍵。                              |
|     DeviceKey      |                              用來識別 Device 執行個體之目標裝置的索引鍵。                               |
|      UserKey       |                                用來識別 User 執行個體之目標使用者的索引鍵。                                 |
| AppInstallStateKey |                     用來識別 MobileAppInstallState 執行個體之應用程式安裝狀態的索引鍵。                     |
|     ErrorCode      | 由與應用程式之安裝相關的應用程式安裝程式、行動平台或服務所傳回的錯誤碼。 |


---
title: "應用程式 | Microsoft Docs"
description: "Intune 資料倉儲 API 中的實體集合應用程式類別的參考主題。"
keywords: "Intune 資料倉儲"
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 07/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: A92DEF30-5D01-4774-9917-E26F5F0E2E68
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 6107059888c8d2fb6227277202a5906491ac9092
ms.sourcegitcommit: b8ef9d8387b4d9b2ea4e6ce937635304771e6532
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/11/2017
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

| 屬性  | 描述 | 範例 |
|---------|------------|--------|
| AppKey |應用程式的唯一識別碼 |123 |
| ApplicationId |應用程式的唯一識別碼 - 類似 AppKey，但此金鑰是自然的。 |b66bc706-ffff-7437-0340-032819502773 |
| 修訂 |管理員在上傳二進位檔期間提及的版本 |2 |
| 標題 |應用程式的標題 |Excel |
| 發佈者 |應用程式的發行者 |Microsoft |
| UploadState |應用程式的上傳狀態 |1 |
| AppTypeKey |下節要說明的 AppType 參考。 | |
| VppProgramTypeKey |後文要說明的 VppProgramType 參考 | |
| CreationTime |這項修訂建立的時間 |11/23/2016 12:00:00 AM |
| ModifiedTime |此修訂任何相關項目前次變更的時間 |11/23/2016 12:00:00 AM |
| Size |二進位檔的大小 | |
| StartDateInclusiveUTC |此應用程式修訂在資料倉儲中建立的 UTC 日期和時間 |11/23/2016 12:00:00 AM |
| EndDateExclusiveUTC |此應用程式修訂開始淘汰的 UTC 日期和時間 |11/23/2016 12:00:00 AM |
| IsCurrent |指出資料倉儲目前是否有此應用程式版本 |True/False |
| RowLastModifiedDateTimeUTC |此應用程式修訂前次在資料倉儲中修改的 UTC 日期和時間 |11/23/2016 12:00:00 AM |

## <a name="apptypes"></a>AppTypes

**AppTypes** 實體會列出應用程式的安裝來源。

| 屬性  | 描述 |
|---------|------------|
| AppTypeID |類型識別碼 |
| AppTypeKey |索引鍵的 Surrogate 索引鍵 |
| AppTypeName |應用程式類型 |

## <a name="example"></a>範例

| AppTypeID  | Name | 描述 |
|---------|------------|--------|
| 0 |Android 市集應用程式 |Android 市集應用程式 |
| 1 |Android LOB 應用程式 |Android 企業營運應用程式 |
| 2 |受管理的 Android 市集應用程式 (MAM) |啟用管理的 Android 市集應用程式 |
| 3 |iOS 市集應用程式 |iOS 市集應用程式 |
| 4 |iOS LOB 應用程式 |iOS 企業營運應用程式 |
| 5 |受管理的 iOS 市集應用程式 (MAM？) |啟用管理的 iOS 市集應用程式 |
| 6 |O365 Pro Plus 套件 |Office 365 Pro Plus Suite for Windows 10 |
| 7 |Web 應用程式 |Web 應用程式 |
| 8 |Windows Phone 8.1 市集應用程式 |Windows Phone 8.1 市集應用程式 |
| 9 |Windows 市集應用程式 |Windows 市集應用程式 |
| 10 |Windows LOB 應用程式 |Windows AppX 企業營運應用程式 |
| 11 |Windows Mobile MSI |MSI 企業營運應用程式 |
| 12 |Windows Phone LOB 應用程式 |Windows Phone 企業營運應用程式 |


## <a name="vppprogramtypes"></a>VppProgramTypes

**VppProgramTypes** 實體會列出應用程式可能的 VPP 方案類型。

| 屬性  | 描述 |
|---------|------------|
| VppProgramTypeID |類型識別碼 |
| VppProgramTypeKey |索引鍵的 Surrogate 索引鍵 |
| VppProgramTypeName |Vpp 方案類型 |

## <a name="example"></a>範例

| VppProgramID  | Name | 描述 |
|---------|------------|--------|
| 3DDA2474-470B-4503-9830-2665C21C1945 |Microsoft |Microsoft 的 VPP 方案 |
| 00000000-0000-0000-0000-000000000000 |尚未提供 |預設值為 [無 VPP] |
| B54814E0-68EA-4BA4-8088-B5AAB58E737B |Apple |Apple 的 VPP 方案 |

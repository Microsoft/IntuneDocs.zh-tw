---
title: Policy | Microsoft Docs
description: "Intune 資料倉儲 API 中 [原則] 類別實體集合的參考主題。"
keywords: "Intune 資料倉儲"
author: Erikre
ms.author: erikre
manager: angrobe
ms.date: 07/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: D5ADB9D8-D46A-43BD-AB0F-D6927508E3F4
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 06c489f8519bda2f3f0359589c3af845ade423fe
ms.sourcegitcommit: 833b1921ced35be140f0107d0b4205ecacd2753b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/04/2018
---
# <a name="reference-for-policy-entities"></a>原則實體的參考

[原則] 類別包含的行動實體，可追蹤下列資訊：

  -  裝置組態設定檔、應用程式組態設定檔和合規性原則的清查  
  -  每日處於成功、擱置、失敗或錯誤狀態的裝置數目  
  -  每日處於成功、擱置、失敗或錯誤狀態的使用者數目  
  -  處於成功、擱置、失敗或錯誤狀態的累積裝置數目  

## <a name="policy"></a>原則

**Policy** 實體列出裝置組態設定檔、應用程式組態設定檔和合規性原則。 您可以將具有行動裝置管理 (MDM) 的原則指派給企業中的群組。

| 屬性  | 說明 | 範例 |
|---------|------------|--------|
| PolicyKey |代表資料倉儲中原則的唯一索引鍵。 |123 |
| PolicyId |資料倉儲中原則的唯一識別碼。 |b66bc706-ffff-7437-0340-032819502773 |
| PolicyName |原則的名稱。 |"Windows 10 Baseline" |
| PolicyVersion |原則的版本。 編輯或變更原則時，會建立較新版本。 |1, 2, 3 |
| IsDeleted |指出是否已更新 [原則] 記錄。  <br>True - 原則具有含已更新欄位的新記錄。 <br>False - 原則的最新記錄。 |True/False |
| StartDateInclusiveUTC |在資料倉儲中建立原則的 UTC 日期和時間。 |11/23/2016 12:00:00 AM |
| DeletedDateUTC |IsDeleted 變更為 True 的 UTC 日期和時間。 |11/23/2016 12:00:00 AM |
| RowLastModifiedDateTimeUTC |前次在資料倉儲中修改原則的 UTC 日期和時間。 |11/23/2016 12:00:00 AM |

## <a name="policytype"></a>PolicyType

**PolicyType** 實體列出裝置組態設定檔、應用程式組態設定檔和合規性原則的類型。 您可以將具有行動裝置管理 (MDM) 的原則指派給企業中的群組。

| 屬性  | 說明 | 範例 |
|---------|------------|--------|
| PolicyTypeId |來源系統中原則的唯一識別碼。 |123 |
| PolicyTypeKey |資料倉儲中原則的唯一識別碼。 |1 |
| PolicyTypeName |原則類型的名稱。 |Windows 10 合規性原則。 |

## <a name="deviceconfiguration"></a>DeviceConfiguration

**DeviceConfigurationProfileDeviceActivity** 實體列出每日處於成功、擱置、失敗或錯誤狀態的裝置數目。 此數目會反映指派給實體的裝置組態設定檔。 例如，如果裝置的所有其指派原則都處於成功狀態，則會將該天的成功計數器往上加一。 如果裝置獲指派兩個設定檔，一個處於成功狀態，另一個則處於錯誤狀態，該實體會遞增成功計數器，並讓裝置處於錯誤狀態。 實體會列出過去 30 天的特定一天有多少裝置處於哪種狀態。

| 屬性  | 說明 | 範例 |
|---------|------------|--------|
| DateKey |將裝置組態設定檔簽入記錄在資料倉儲中的日期索引鍵。 |20160703 |
| Pending |處於擱置狀態的唯一裝置數目。 |123 |
| 已成功 |處於成功狀態的唯一裝置數目。 |12 |
| 錯誤 |處於錯誤狀態的唯一裝置數目。 |10 |
| Failed |處於失敗狀態的唯一裝置數目。 |2 |

## <a name="userconfiguration"></a>UserConfiguration

**UserConfigurationProfileDeviceActivity** 實體列出每日處於成功、擱置、失敗或錯誤狀態的使用者數目。 此數目會反映指派給實體的裝置組態設定檔。 例如，如果使用者的所有其指派原則都處於成功狀態，則會將該天的成功計數器向上加一。 如果使用者獲指派兩個設定檔，一個處於成功狀態，另一個則處於錯誤狀態，我們會將使用者計算為處於錯誤狀態。  **UserConfigurationProfileDeviceActivity** 實體列出過去 30 天的特定一天有多少使用者處於哪種狀態。

| 屬性  | 說明 | 範例 |
|---------|------------|--------|
| DateKey |將裝置組態設定檔簽入記錄在資料倉儲中的日期索引鍵。 |20160703 |
| Pending |處於擱置狀態的唯一使用者數目。 |123 |
| 已成功 |處於成功狀態的唯一使用者數目。 |12 |
| 錯誤 |處於錯誤狀態的唯一使用者數目。 |10 |
| Failed |處於失敗狀態的唯一使用者數目。 |2 |

## <a name="policytypeactivity"></a>PolicyTypeActivity

**PolicyTypeActivity** 實體列出處於成功、擱置、失敗或錯誤狀態的累積裝置數目。 它會列出與每日裝置組態設定檔、應用程式組態設定檔或相容性原則有關的這些狀態。

| 屬性  | 說明 | 範例 |
|---------|------------|--------|
| DateKey |將裝置組態設定檔簽入記錄在資料倉儲中的日期索引鍵。 |20160703 |
| PolicyKey |原則索引鍵，可以與 [原則] 聯結以取得 policyName。 |Windows 10 基準 |
| PolicyTypeKey |原則索引鍵類型，可以與 [原則類型] 聯結以取得原則類型名稱。 |Windows 10 合規性原則 |
| Pending |處於擱置狀態的唯一裝置數目。 |123 |
| 已成功 |處於成功狀態的唯一裝置數目。 |12 |
| 錯誤 |處於錯誤狀態的唯一裝置數目。 |10 |
| 失敗 - |處於失敗狀態的唯一裝置數目。 |2 |
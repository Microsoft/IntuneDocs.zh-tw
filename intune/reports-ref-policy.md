---
title: 原則
titlesuffix: Microsoft Intune
description: Intune 資料倉儲 API 中 [原則] 類別實體集合的參考主題。
keywords: Intune 資料倉儲
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/04/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.openlocfilehash: 046dbe79dbaaee7de97fc83b80c40d5bf902c931
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2018
ms.locfileid: "52183497"
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



**DeviceConfigurationProfileUserActivity** 實體列出每日處於成功、暫止、失敗或錯誤狀態的使用者數目。 此數目會反映指派給實體的裝置組態設定檔。 例如，如果使用者的所有其指派原則都處於成功狀態，則會將該天的成功計數器向上加一。 如果使用者獲指派兩個設定檔，一個處於成功狀態，另一個則處於錯誤狀態，會計算處於錯誤狀態的使用者。  **DeviceConfigurationProfileUserActivity** 實體列出過去 30 天內的某一天，有多少使用者處於哪種狀態。

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
| Failed |處於失敗狀態的唯一裝置數目。 |2 |

## <a name="compliance-policy"></a>相容性原則

合規性政策 API 參考包含實體，其提供指派給裝置的合規性政策相關狀態資訊。

### <a name="compliancepolicystatusdeviceactivities"></a>CompliancePolicyStatusDeviceActivities

下表摘要了裝置的合規性政策指派狀態。 其列出各合規性狀態下發現的裝置計數。


|屬性     |說明  |範例  |
|---------|---------|---------|
|DateKey  |日期索引鍵，時間點為建立合規性政策的摘要時。|20161204 |
|Unknown  |離線或因為其他原因而無法與 Intune 或 Azure AD 通訊的裝置數目。 |5|
|NotApplicable      |管理員設為目標的裝置合規性政策並不適用的裝置數目。|201 |
|符合標準      |一或多項管理員設為目標的裝置合規性政策已成功套用的裝置數目。 |4083 |
|InGracePeriod      |不合規但仍在管理員定義之寬限期內的裝置數目。 |57|
|NonCompliant      |管理員設為目標的裝置合規性政策無法套用，或使用者未予以遵循的裝置數目。|43 |
|錯誤      |無法與 Intune 或 Azure AD 通訊且傳回錯誤訊息的裝置數目。 |3|

### <a name="compliancepolicystatusdeviceperpolicyactivities"></a>CompliancePolicyStatusDevicePerPolicyActivities 

下表摘要了裝置的合規性政策指派狀態，以各原則及各原則類型為基礎。 其列出指派的各項合規性政策各個合規性狀態下發現的裝置計數。



|屬性  |說明  |範例  |
|---------|---------|---------|
|DateKey  |日期索引鍵，時間點為建立合規性政策的摘要時。|20161219|
|PolicyKey     |已建立摘要之合規性政策的索引鍵。 |10178 |
|PolicyPlatformKey      |已建立摘要之合規性政策平台類型的索引鍵。|5|
|Unknown     |離線或因為其他原因而無法與 Intune 或 Azure AD 通訊的裝置數目。|13|
|NotApplicable     |管理員設為目標的裝置合規性政策並不適用的裝置數目。|3|
|符合標準      |一或多項管理員設為目標的裝置合規性政策已成功套用的裝置數目。 |45|
|InGracePeriod      |不合規但仍在管理員定義之寬限期內的裝置數目。 |3|
|NonCompliant      |管理員設為目標的裝置合規性政策無法套用，或使用者未予以遵循的裝置數目。|7|
|錯誤      |無法與 Intune 或 Azure AD 通訊且傳回錯誤訊息的裝置數目。 |3|

### <a name="policyplatformtypes"></a>PolicyPlatformTypes

下表包含所有受指派原則的平台類型。 從未指派給任何裝置的原則平台類型不會出現在此表格中。


|屬性  |說明  |範例  |
|---------|---------|---------|
|PolicyPlatformTypeKey      |原則平台類型的唯一索引鍵。 |20170519 |
|PolicyPlatformTypeId      |原則平台類型的唯一識別碼。|1|
|PolicyPlatformTypeName      |原則平台類型的名稱。|AndroidForWork |

### <a name="policydeviceactivity"></a>PolicyDeviceActivity

下表列出每日處於成功、擱置、失敗或錯誤狀態的裝置數目。 該數目反映每個原則類型設定檔的資料。 例如，如果裝置的所有其指派原則都處於成功狀態，則會將該天的成功計數器往上加一。 如果裝置獲指派兩個設定檔，一個處於成功狀態，另一個則處於錯誤狀態，該實體會遞增成功計數器，並讓裝置處於錯誤狀態。 PolicyDeviceActivity 實體會列出過去 30 天的某一天，有多少裝置處於哪種狀態。

|屬性  |說明  |範例  |
|---------|---------|---------|
|DateKey|將裝置組態設定檔簽入記錄在資料倉儲中的日期索引鍵。|20160703|
|Pending|處於擱置狀態的唯一裝置數目。|123|
|已成功|處於成功狀態的唯一裝置數目。|12|
PolicyKey|原則索引鍵，可以與 [原則] 聯結以取得 policyName。|Windows 10 基準|
|錯誤|處於錯誤狀態的唯一裝置數目。|10|
|Failed|處於失敗狀態的唯一裝置數目。|2|

### <a name="policyuseractivity"></a>PolicyUserActivity 

下表列出每日處於成功、擱置、失敗或錯誤狀態的使用者數目。 該數目反映每個原則類型設定檔的資料。 例如，如果使用者的所有其指派原則都處於成功狀態，則會將該天的成功計數器向上加一。 如果使用者獲指派兩個設定檔，一個處於成功狀態，另一個則處於錯誤狀態，會計算處於錯誤狀態的使用者。 PolicyUserActivity 實體會列出過去 30 天的某一天，有多少使用者處於哪種狀態。


| 屬性  |                                         說明                                         |       範例       |
|-----------|---------------------------------------------------------------------------------------------|---------------------|
|  DateKey  | 將裝置組態設定檔簽入記錄在資料倉儲中的日期索引鍵。 |      20160703       |
|  Pending  |                         處於擱置狀態的唯一裝置數目。                          |         123         |
| 已成功 |                         處於成功狀態的唯一裝置數目。                          |         12          |
| PolicyKey |                原則索引鍵，可以與 [原則] 聯結以取得 policyName。                 | Windows 10 基準 |
|   錯誤   |                          處於錯誤狀態的唯一裝置數目。                           |         10          |


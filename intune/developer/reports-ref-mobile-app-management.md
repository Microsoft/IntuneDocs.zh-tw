---
title: 行動應用程式管理 (MAM)
titleSuffix: Microsoft Intune
description: Intune 資料倉儲 API 中 [行動應用程式管理] 類別實體集合的參考主題。
keywords: Intune 資料倉儲
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/02/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: developer
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 084F11AD-F7BA-45A4-8424-45E6E4564930
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: eb1833a6a54fe0a7f78958e653468921df952b4d
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72505706"
---
# <a name="reference-for-mobile-app-management-mam-entities"></a>行動應用程式管理 (MAM) 實體的參考

[行動應用程式管理]  類別包含行動應用程式的實體，例如：

- 應用程式
- 執行個體
- 簽入狀態
- 健全狀況狀態
- 原則狀態
- 註冊狀態
- 平台類型

## <a name="mamapplications"></a>mamApplications

**mamApplication** 實體列出透過行動應用程式管理 (MAM) 所管理的企業營運 (LOB) 應用程式，而不需要在企業中註冊。

| 屬性 | 說明 | 範例 |
|---------|------------|--------|
| mamApplicationKey |MAM 應用程式的唯一識別碼。 | 432 |
| mamApplicationName |MAM 應用程式的名稱。 |MAM 應用程式範例名稱 |
| mamApplicationId |MAM 應用程式的應用程式識別碼。 | 123 |
| isDeleted |指出是否已更新此 MAM 應用程式記錄。 <br>True - MAM 應用程式具有包含此資料表中已更新欄位的新記錄。 <br>False - 此 MAM 應用程式的最新記錄。 |True/False |
| startDateInclusiveUTC |在資料倉儲中建立此 MAM 應用程式的 UTC 日期和時間。 |11/23/2016 12:00:00 AM |
| deletedDateUTC |IsDeleted 變更為 True 的 UTC 日期和時間。 |11/23/2016 12:00:00 AM |
| rowLastModifiedDateTimeUTC |前次在資料倉儲中修改此 MAM 應用程式的 UTC 日期和時間。 |11/23/2016 12:00:00 AM |


## <a name="mamapplicationinstances"></a>mamApplicationInstances

**mamApplicationInstance** 實體會將受管理行動應用程式管理 (MAM) 應用程式列出每個裝置每位使用者的單一執行個體。 實體中列出的所有使用者和裝置都會受到保護，如下所示，他們至少獲指派一個 MAM 原則。


|          屬性          |                                                                                                  說明                                                                                                  |               範例                |
|----------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------|
|   applicationInstanceKey   |                                                               資料倉儲中 MAM 應用程式執行個體的唯一識別碼 - Surrogate 索引鍵。                                                                |                 123                  |
|           userId           |                                                                              已安裝此 MAM 應用程式之使用者的使用者識別碼。                                                                              | b66bc706-ffff-7437-0340-032819502773 |
|   applicationInstanceId    |                                              MAM 應用程式執行個體的唯一識別碼 - 與 ApplicationInstanceKey 類似，但識別碼是自然索引鍵。                                              | b66bc706-ffff-7437-0340-032819502773 |
| mamApplicationId | 為其建立此 Mam 應用程式執行個體之 Mam 應用程式的應用程式識別碼。   | 11/23/2016 12:00:00 AM   |
|     applicationVersion     |                                                                                     此 MAM 應用程式的應用程式版本。                                                                                      |                  2                   |
|        createdDate         |                                                                 此 MAM 應用程式執行個體記錄的建立日期。 值可以是 Null。                                                                 |        11/23/2016 12:00:00 AM        |
|          平台          |                                                                          此 MAM 應用程式安裝所在裝置的平台。                                                                           |                  2                   |
|      platformVersion       |                                                                      此 MAM 應用程式安裝所在裝置的平台版本。                                                                       |                 2.2                  |
|         sdkVersion         |                                                                            與此 MAM 應用程式包裝在一起的 MAM SDK 版本。                                                                            |                 3.2                  |
| mamDeviceId | 與 MAM 應用程式執行個體建立關聯之裝置的裝置識別碼。   | 11/23/2016 12:00:00 AM   |
| mamDeviceType | 與 MAM 應用程式執行個體建立關聯之裝置的裝置類型。   | 11/23/2016 12:00:00 AM   |
| mamDeviceName | 與 MAM 應用程式執行個體建立關聯之裝置的裝置名稱。   | 11/23/2016 12:00:00 AM   |
|         isDeleted          | 指出是否已更新此 MAM 應用程式執行個體記錄。 <br>True - 此 MAM 應用程式執行個體具有包含此資料表中已更新欄位的新記錄。 <br>False - 此 MAM 應用程式執行個體的最新記錄。 |              True/False              |
|   startDateInclusiveUtc    |                                                              在資料倉儲中建立此 MAM 應用程式執行個體的 UTC 日期和時間。                                                               |        11/23/2016 12:00:00 AM        |
|       deletedDateUtc       |                                                                             IsDeleted 變更為 True 的 UTC 日期和時間。                                                                              |        11/23/2016 12:00:00 AM        |
| rowLastModifiedDateTimeUtc |                                                           前次在資料倉儲中修改此 MAM 應用程式執行個體的 UTC 日期和時間。                                                            |        11/23/2016 12:00:00 AM        |


## <a name="mamcheckins"></a>mamCheckins

**mamCheckin** 實體代表行動應用程式管理 (MAM) 應用程式執行個體已簽入 Intune 服務時所收集的資料。 

> [!Note]  
> 一天簽入應用程式執行個體多次時，資料倉儲會將它儲存為單一簽入。

| 屬性 | 說明 | 範例 |
|---------|------------|--------|
| dateKey |將 MAM 應用程式簽入記錄在資料倉儲中的日期索引鍵。 | 20160703 |
| applicationInstanceKey |與此 MAM 應用程式簽入建立關聯之應用程式執行個體的索引鍵。 | 123 |
| userKey |與此 MAM 應用程式簽入建立關聯之使用者的索引鍵。 | 4323 |
| mamApplicationKey |與 MAM 應用程式簽入建立關聯之應用程式的應用程式金鑰。 | 432 |
| deviceHealthKey |與此 MAM 應用程式簽入建立關聯之 DeviceHealth 的索引鍵。 | 321 |
| platformKey |代表與此 MAM 應用程式簽入建立關聯之裝置的平台。 |123 |
| effectiveAppliedPolicyKey |代表與已簽入 MAM 應用程式建立關聯的有效已套用原則。 合併所有與特定應用程式和使用者相關原則的有效已套用原則結果。 | 322 |
| pastCheckInDate |前次簽入此 MAM 應用程式的日期和時間。 值可以是 Null。 |11/23/2016 12:00:00 AM |


## <a name="mamdevicehealth"></a>mamDeviceHealth

**mamDeviceHealth** 實體代表已部署行動應用程式管理 (MAM) 原則的裝置，即使它們已遭到 JB 破解也是一樣。

| 屬性 | 說明 | 範例 |
|---------|------------|--------|
| deviceHealthKey |資料倉儲中裝置和其關聯健康狀況的唯一識別碼 - Surrogate 索引鍵。 |123 |
| deviceHealth |裝置的唯一識別碼和其關聯健康狀況 - 與 DeviceHealthKey 類似，但識別碼是自然索引鍵。 |b66bc706-ffff-7777-0340-032819502773 |
| deviceHealthName |代表裝置的狀態。 <br>無法使用 - 無此裝置的相關資訊。 <br>狀況良好 - 裝置未進行 JB 破解。 <br>狀況不良 - 裝置已進行 JB 破解。 |無法使用 狀況良好 狀況不良 |
| rowLastModifiedDateTimeUtc |前次在資料倉儲中修改此特定 MAM 裝置健康狀況的 UTC 日期和時間。 |11/23/2016 12:00:00 AM |

## <a name="mameffectivepolicies"></a>mamEffectivePolicies

**mamEffectivePolicy** 實體列出組織中套用的所有行動應用程式管理 (MAM) 有效原則。 合併所有與特定應用程式和使用者相關原則的有效已套用原則結果。

| 屬性 | 說明 | 範例 |
|---------|------------|--------|
| effectivePolicyKey |資料倉儲中 MAM 有效原則的唯一識別碼。 |2 |
| realPolicyKey |IT 專業人員所撰寫之 MAM 原則的唯一識別碼。 |1 |
| rowCreatedDateTimeUtc |在資料倉儲中建立此 MAM 有效原則的 UTC 日期和時間。 |11/23/2016 12:00:00 AM |

## <a name="mamplatforms"></a>mamPlatforms

**mamPlatform** 實體列出已安裝行動應用程式管理 (MAM) 應用程式的平台名稱和類型。


|          屬性          |                                    說明                                    |                         範例                         |
|----------------------------|-----------------------------------------------------------------------------------|---------------------------------------------------------|
|        platformKey         |     資料倉儲中平台的唯一識別碼 - Surrogate 索引鍵。      |                           123                           |
|          平台          | 平台的唯一識別碼 - 與 PlatformKey 類似，但為自然索引鍵。 |                           123                           |
|        platformName        |                                   平台名稱                                   | 無法使用 <br>無 <br>Windows <br>IOS <br>Android。 |
| rowLastModifiedDateTimeUtc | 前次在資料倉儲中修改此平台的 UTC 日期和時間。  |                 11/23/2016 12:00:00 AM                  |


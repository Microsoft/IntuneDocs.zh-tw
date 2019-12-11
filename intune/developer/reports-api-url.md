---
title: Intune 資料倉儲 API 端點
titleSuffix: Microsoft Intune
description: 本參考主題描述 Microsoft Intune 資料倉儲 API URL 結構。 提供篩選條件範例。
keywords: Intune 資料倉儲
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/03/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: developer
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: A7A174EC-109D-4BB8-B460-F53AA2D033E6
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 170ed2fbf300299796401b10a906d875b6f50bf5
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72490455"
---
# <a name="intune-data-warehouse-api-endpoint"></a>Intune 資料倉儲 API 端點

您可以搭配使用 Intune 資料倉儲 API 與具有特定角色型存取控制和 Azure AD 認證的帳戶。 您接著會使用 OAuth 2.0 向 Azure AD 授權 REST 用戶端。 最後，您會形成有意義的 URL 來呼叫資料倉儲資源。

[!INCLUDE [reports-credential-reqs](../includes/reports-credential-reqs.md)]

## <a name="authorization"></a>授權

Azure Active Directory (Azure AD) 採用 OAuth 2.0，可讓您授予 Azure AD 租用戶中之 Web 應用程式和 Web API 的存取權。 本指南與語言無關，並描述如何傳送和接收 HTTP 訊息，而不需要使用任何開放原始碼程式庫。 OAuth 2.0 規格的[第 4.1 節](https://tools.ietf.org/html/rfc6749#section-4.1)描述 OAuth 2.0 授權碼流程。

如需詳細資訊，請參閱[使用 OAuth 2.0 和 Azure Active Directory 授權存取 Web 應用程式](https://docs.microsoft.com/azure/active-directory/develop/active-directory-protocols-oauth-code)。

## <a name="api-url-structure"></a>API URL 結構

資料倉儲 API 端點會讀取每個集合的實體。 API 支援 **GET** HTTP 動詞，以及查詢選項子集。

Intune URL 使用下列格式：  
`https://fef.{location}.manage.microsoft.com/ReportingService/DataWarehouseFEService/{entity-collection}?api-version={api-version}`

> [!NOTE]
> 在上述 URL 中，根據下表中所提供的詳細資料取代 `{location}`、`{entity-collection}` 和 `{api-version}`。

URL 包含下列元素：

| 元素 | 範例 | 說明 |
|-------------------|------------|--------------------------------------------------------------------------------------------------------------------|
| 位置 | msua06 | 在 Azure 入口網站中檢視資料倉儲 API 刀鋒視窗，即可找到基底 URL。 |
| entity-collection | devicePropertyHistories | OData 實體集合的名稱。 如需資料模型中集合和實體的詳細資訊，請參閱[資料模型](reports-ref-data-model.md)。 |
| api-version | beta | 版本是要存取之 API 的版本。 如需詳細資訊，請參閱[版本](reports-api-url.md#api-version-information)。 |
| maxhistorydays | 7 | (選擇性) 記錄取出天數的上限。 此參數可以提供給任何集合，但只會針對包含 `dateKey` 為其索引鍵屬性之一部分的集合生效。 如需詳細資訊，請參閱 [DateKey 範圍篩選條件](reports-api-url.md#datekey-range-filters)。 |

## <a name="api-version-information"></a>API 版本資訊

您現在可以藉由設定查詢參數  `api-version=v1.0` 來使用 Intune 資料倉儲 v1.0 版。 資料倉儲中對集合所進行的更新為附加性質，因此不會破壞現有的案例。

您可以使用搶鮮版 (Beta) 來試用最新資料倉儲功能。 若要使用搶鮮版 (Beta)，URL 必須包含查詢參數  `api-version=beta`。 搶鮮版 (Beta) 能在功能被正式推出為支援的服務之前預先提供它們。 Intune 新增功能時，搶鮮版 (Beta) 可能會變更行為和資料合約。 與搶鮮版 (Beta) 相依的任何自訂程式碼或報告工具都可能會中斷進行中更新。

## <a name="odata-query-options"></a>OData 查詢選項

目前版本支援下列 OData 查詢參數：`$filter`、`$select`、`$skip,` 及 `$top`。 在 `$filter` 中，當資料行適用時只支援 `DateKey` 和 `RowLastModifiedDateTimeUTC`，其他屬性會觸發錯誤的要求。

## <a name="datekey-range-filters"></a>DateKey 範圍篩選條件

`DateKey` 範圍篩選條件可用來針對具有 `dateKey` 作為索引鍵屬性的部分集合，限制要下載的資料量。 `DateKey` 篩選條件可用來藉由提供下列 `$filter` 查詢參數，將服務效能最佳化：

1. 在 `$filter` 中的單獨 `DateKey`，支援 `lt/le/eq/ge/gt` 運算子和使用邏輯運算子 `and` 聯結，可以對應到開始日期和/或結束日期。
2. `maxhistorydays` 提供作為自訂查詢選項。<br>

## <a name="filter-examples"></a>篩選條件範例

> [!NOTE]
> 篩選條件範例假設今天是 2019 年 2 月 21 日。

|                             篩選                             |           效能最佳化           |                                          說明                                          |
|:--------------------------------------------------------------:|:--------------------------------------------:|:---------------------------------------------------------------------------------------------:|
|    `maxhistorydays=7`                                            |    完整                                      |    傳回 `DateKey` 在 20180214 和 20180221 之間的資料。                                     |
|    `$filter=DateKey eq 20180214`                                 |    完整                                      |    傳回 `DateKey` 等於 20180214 的資料。                                                    |
|    `$filter=DateKey ge 20180214 and DateKey lt 20180221`         |    完整                                      |    傳回 `DateKey` 在 20180214 和 20180220 之間的資料。                                     |
|    `maxhistorydays=7&$filter=DateKey eq 20180214`                |    完整                                      |    傳回 `DateKey` 等於 20180214 的資料。 `maxhistorydays` 會被忽略。                            |
|    `$filter=RowLastModifiedDateTimeUTC ge 2018-02-21T23:18:51.3277273Z`                                |    完整                                       |    傳回 `RowLastModifiedDateTimeUTC` 大於或等於 `2018-02-21T23:18:51.3277273Z` 的資料                             |

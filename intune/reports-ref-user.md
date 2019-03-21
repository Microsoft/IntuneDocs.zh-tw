---
title: 使用者 - Intune 資料倉儲
titlesuffix: Microsoft Intune
description: Intune 資料倉儲 API 中 [使用者] 類別實體集合的參考主題。
keywords: Intune 資料倉儲
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/14/2018
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: C29A6EEA-72B7-427E-9601-E05B408F3BB0
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: ccd9a14c29db5039ce0173d0c09fd3d2851755f3
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57566245"
---
# <a name="reference-for-user-entity"></a>使用者實體的參考

**User** 類別包含定義資料模型中使用者屬性的 **User** 實體。

## <a name="user"></a>User

**User** 實體列出企業中具有所指派授權的所有 Azure Active Directory (Azure AD) 使用者。

**User** 實體集合包含了使用者資料。 這些資料列包含資料收集期間的使用者狀態，即使使用者已經被移除。 例如，某個使用者可能在上個月內被新增到 Intune 然後又被移除。 雖然在報告的時候這個使用者不會出現，但使用者和狀態會出現在上個月的資料中。 您可以建立一個報告，其中顯示使用者的歷程記錄在您資料中出現的期間。

| 屬性  | 說明 | 範例 |
|---------|------------|--------|
| UserKey |資料倉儲中使用者的唯一識別碼 - Surrogate 索引鍵。 |123 |
| UserId |使用者的唯一識別碼 - 與 UserKey 類似，但為自然索引鍵。 |b66bc706-ffff-7437-0340-032819502773 |
| UserEmail |使用者的電子郵件地址。 |John@constoso.com |
| UPN | 使用者的使用者主體名稱。 | John@constoso.com |
| DisplayName |使用者的顯示名稱。 |John |
| IntuneLicensed |指定這位使用者是否獲授權使用 Intune。 |True/False |
| IsDeleted | 指出所有使用者的授權是否都已經過期，以及使用者是否因此從 Intune 移除。 對於單一資料列，此旗標不會變更。 反之，系統會針對新的使用者狀態建立新的資料列。 |True/False |
| StartDateInclusiveUTC |如果 IsDeleted = FALSE，是以 UTC 表示的 DateTime，即使用者被指派授權並開始在 Intune 中出現的時間。 如果 IsDeleted = TRUE，是以 UTC 表示的 DateTime，即使用者的授權過期並從 Intune 移除的時間。 |11/23/2016 12:00:00 AM |
| EndDateExclusiveUTC |如果 IsDeleted = FALSE，是以 UTC 表示的 DateTime，即使用者的授權過期並從 Intune 移除的時間。 授權在前一天的某個時間過期。 如果 IsDeleted = TRUE，是以 UTC 表示的 DateTime，即使用者重新取得新的授權並在 Intune 中重新建立的時間。  |11/23/2016 12:00:00 AM |
| IsCurrent |指出此資料列是否代表該使用者的最新狀態。 針對單一使用者可能會有多個資料列存在，但只有其中一個代表目前的狀態。  |True/False |
| RowLastModifiedDateTimeUTC |資料列最近一次在資料倉儲中被修改的 UTC 日期和時間  |11/23/2016 12:00:00 AM |

## <a name="next-steps"></a>後續步驟
 - 您可以使用 **Current User** 實體集合來將使用者資料限制於目前作用中的使用者。 如需詳細資訊，請參閱 [Current User 實體的參考](reports-ref-current-user.md)。
 - 若要深入了解資料倉儲如何在 Intune 中追蹤使用者的存留期，請參閱 [Intune 資料倉儲中的使用者存留期表示法](reports-ref-user-timeline.md)。

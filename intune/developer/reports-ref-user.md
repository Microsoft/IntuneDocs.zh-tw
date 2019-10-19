---
title: 使用者 - Intune 資料倉儲
titleSuffix: Microsoft Intune
description: Intune 資料倉儲 API 中 [使用者] 類別實體集合的參考主題。
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
ms.assetid: C29A6EEA-72B7-427E-9601-E05B408F3BB0
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 996e28f9dceff88637c93e667597e3364215b965
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72505626"
---
# <a name="reference-for-user-entity"></a>使用者實體的參考

**Users** 類別包含定義資料模型中使用者屬性的 **user** 實體。

## <a name="users"></a>使用者

**user** 實體會列出您的企業中具有所指派授權的所有 Azure Active Directory (Azure AD) 使用者。

**user** 實體集合會包含使用者資料。 這些資料列包含資料收集期間的使用者狀態，即使使用者已經被移除。 例如，某個使用者可能在上個月內被新增到 Intune 然後又被移除。 雖然此使用者在報告期間並不存在，但使用者和狀態仍會存在於上個月的資料中。 您可以建立一個報告，其中顯示使用者的歷程記錄在您資料中出現的期間。

|          屬性          |                                                                                                           說明                                                                                                          |                範例               |
|:--------------------------:|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|:------------------------------------:|
| userKey                    | 資料倉儲中使用者的唯一識別碼 - Surrogate 索引鍵。                                                                                                                                                         | 123                                  |
| userId                     | 使用者的唯一識別碼 - 與 UserKey 類似，但為自然索引鍵。                                                                                                                                                    | b66bc706-ffff-7437-0340-032819502773 |
| userEmail                  | 使用者的電子郵件地址。                                                                                                                                                                                                     | John@constoso.com                    |
| userPrincipalName                        | 使用者的使用者主體名稱。                                                                                                                                                                                               | John@constoso.com                    |
| displayName                | 使用者的顯示名稱。                                                                                                                                                                                                      | John                                 |
| intuneLicensed             | 指定這位使用者是否獲授權使用 Intune。                                                                                                                                                                              | True/False                           |
| isDeleted                  | 指出所有使用者的授權是否都已經過期，以及使用者是否因此而自 Intune 中被移除。 針對單一記錄，此旗標不會變更。 相反地，系統會針對新的使用者狀態建立新的記錄。 | True/False                           |
| RowLastModifiedDateTimeUTC | 在資料倉儲中最後一次修改記錄的 UTC 日期和時間                                                                                                                                                 | 11/23/2016 0:00                      |


## <a name="next-steps"></a>後續步驟
- 您可以使用 **Current User** 實體集合來將使用者資料限制於目前作用中的使用者。 如需詳細資訊，請參閱 [Current User 實體的參考](../reports-ref-current-user.md)。
- 若要深入了解資料倉儲如何在 Intune 中追蹤使用者的存留期，請參閱 [Intune 資料倉儲中的使用者存留期表示法](reports-ref-user-timeline.md)。

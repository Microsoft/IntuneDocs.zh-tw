---
title: User | Microsoft Docs
description: "Intune 資料倉儲 API 中 [使用者] 類別實體集合的參考主題。"
keywords: "Intune 資料倉儲"
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 07/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: C29A6EEA-72B7-427E-9601-E05B408F3BB0
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 2b9739299c52c668117116f54c08715f1218d130
ms.sourcegitcommit: addf6a40caa22c22adfd2e2eff7d666cd1877e3c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2017
---
# <a name="reference-for-user-entity"></a>User 實體的參考

[使用者] 類別包含 **User** 實體，以定義資料模型中的使用者和代理程式屬性。

**User**

**User** 實體列出企業中具有所指派授權的所有 Azure Active Directory (Azure AD) 使用者。

| 屬性  | 描述 | 範例 |
|---------|------------|--------|
| UserKey |資料倉儲中使用者的唯一識別碼 - Surrogate 索引鍵 |123 |
| UserId |使用者的唯一識別碼 - 與 UserKey 類似，但為自然索引鍵 |b66bc706-ffff-7437-0340-032819502773 |
| UserEmail |使用者的電子郵件地址 |John@constoso.com |
| DisplayName |使用者的顯示名稱 |John |
| IntuneLicensed |指定這位使用者是否獲授權使用 Intune。 |True/False |
| IsDeleted |指出是否已更新此使用者記錄。  True - 此使用者具有包含此資料表中已更新欄位的新記錄。 False - 此使用者的最新記錄。 |True/False |
| StartDateInclusiveUTC |在資料倉儲中建立此使用者的 UTC 日期和時間 |11/23/2016 12:00:00 AM |
| EndDateExclusiveUTC |IsDeleted 變更為 True 的 UTC 日期和時間 |11/23/2016 12:00:00 AM |
| IsCurrent |指出資料倉儲中目前是否有此使用者記錄 |True/False |
| RowLastModifiedDateTimeUTC |前次在資料倉儲中修改此使用者的 UTC 日期和時間 |11/23/2016 12:00:00 AM |


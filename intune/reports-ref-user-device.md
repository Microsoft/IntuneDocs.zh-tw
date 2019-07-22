---
title: 使用者裝置關聯 - Intune 資料倉儲
titleSuffix: Microsoft Intune
description: UserDeviceAssociation 實體包含您組織中的使用者裝置關聯。
keywords: Intune 資料倉儲
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 04/10/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 777484A7-09CE-4409-987F-76B3F87DFE93
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: c8d24716f65d5ff8afba5fc0a89cfef082712429
ms.sourcegitcommit: c3ac858bbadb63d248ed54069e48160d703bbaf2
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 07/18/2019
ms.locfileid: "68313678"
---
# <a name="reference-for-user-device-association-entity"></a>使用者裝置關聯實體的參考

**userDeviceAssociation** 實體包含您組織中的使用者裝置關聯。

## <a name="userdeviceassociations"></a>userDeviceAssociations


|        名稱        |                                           說明                                            |        範例         |
|--------------------|--------------------------------------------------------------------------------------------------|------------------------|
|      userKey       |              資料倉儲中使用者的唯一識別碼。 (Surrogate 索引鍵)。               |          123           |
|     deviceKey      |                      資料倉儲中裝置的唯一識別碼。                      |          123           |
| createdDateTimeUTC |           建立使用者裝置關聯時的日期和時間。 使用 UTC 格式。           | 11/23/2016 12:00:00 AM |
|     isDeleted      | 指出使用者已取消註冊該裝置，且關聯不再是最新的。 |       True/False       |
|  endedDateTimeUTC  |              IsDeleted 變更為 <strong>True</strong> 的 UTC 日期和時間。               | 06/23/2017 12:00:00 AM |

## <a name="next-steps"></a>後續步驟

- 深入了解 [Intune 資料倉儲](reports-nav-create-intune-reports.md)。

---
title: 使用者裝置關聯 - Intune 資料倉儲
titlesuffix: Microsoft Intune
description: UserDeviceAssociation 實體包含您組織中的使用者裝置關聯。
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
ms.assetid: 777484A7-09CE-4409-987F-76B3F87DFE93
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5d3473b04a1d015f88d27359864a84227215b62a
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57565293"
---
# <a name="reference-for-user-device-association-entity"></a>使用者裝置關聯實體的參考

**UserDeviceAssociation** 實體包含您組織中的使用者裝置關聯。

## <a name="userdeviceassociation"></a>UserDeviceAssociation


|        名稱        |                                           說明                                            |        範例         |
|--------------------|--------------------------------------------------------------------------------------------------|------------------------|
|      UserKey       |              資料倉儲中使用者的唯一識別碼。 (Surrogate 索引鍵)。               |          123           |
|     DeviceKey      |                      資料倉儲中裝置的唯一識別碼。                      |          123           |
| CreatedDateTimeUTC |           建立使用者裝置關聯時的日期和時間。 使用 UTC 格式。           | 11/23/2016 12:00:00 AM |
|     IsDeleted      | 指出使用者已取消註冊該裝置，且關聯不再是最新的。 |       True/False       |
|  EndedDateTimeUTC  |              IsDeleted 變更為 <strong>True</strong> 的 UTC 日期和時間。               | 06/23/2017 12:00:00 AM |

## <a name="next-steps"></a>後續步驟

- 深入了解 [Intune 資料倉儲](reports-nav-create-intune-reports.md)。

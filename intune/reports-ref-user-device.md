---
title: 使用者裝置關聯 - Intune 資料倉儲
titlesuffix: Microsoft Intune
description: Intune 資料倉儲 API 中的變更清單。
keywords: Intune 資料倉儲
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 05/15/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 777484A7-09CE-4409-987F-76B3F87DFE93
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: bd06c4d42de0c4f64ec0c0cfa61d8aa44af7ab95
ms.sourcegitcommit: 34e96e57af6b861ecdfea085acf3c44cff1f3d43
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2018
---
# <a name="user-device-association"></a>使用者裝置關聯

**UserDeviceAssociation** 實體包含您組織中的使用者裝置關聯。


|        名稱        |                                           說明                                            |        範例         |
|--------------------|--------------------------------------------------------------------------------------------------|------------------------|
|      UserKey       |              資料倉儲中使用者的唯一識別碼。 (Surrogate 索引鍵)。               |          123           |
|     DeviceKey      |                      資料倉儲中裝置的唯一識別碼。                      |          123           |
| CreatedDateTimeUTC |           建立使用者裝置關聯時的日期和時間。 使用 UTC 格式。           | 11/23/2016 12:00:00 AM |
|     IsDeleted      | 指出使用者已取消註冊該裝置，且關聯不再是最新的。 |       True/False       |
|  EndedDateTimeUTC  |              IsDeleted 變更為 <strong>True</strong> 的 UTC 日期和時間。               | 06/23/2017 12:00:00 AM |


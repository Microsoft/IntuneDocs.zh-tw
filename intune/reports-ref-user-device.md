---
title: "使用者裝置關聯 - Intune 資料倉儲 | Microsoft Docs"
description: "Intune 資料倉儲 API 中的變更清單。"
keywords: "Intune 資料倉儲"
author: Erikre
ms.author: erikre
manager: angrobe
ms.date: 10/19/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 777484A7-09CE-4409-987F-76B3F87DFE93
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 45c3e14631fdfe74cafea4a0965efac51386524a
ms.sourcegitcommit: 833b1921ced35be140f0107d0b4205ecacd2753b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/04/2018
---
# <a name="user-device-association"></a>使用者裝置關聯

**UserDeviceAssociation** 實體包含您組織中的使用者裝置關聯。

| 名稱               | 說明                                                                                      | 範例                |
|--------------------|--------------------------------------------------------------------------------------------------|------------------------|
| UserKey            | 資料倉儲中使用者的唯一識別碼。 (Surrogate 索引鍵)。                              | 123                    |
| DeviceKey          | 資料倉儲中裝置的唯一識別碼。                                            | 123                    |
| CreatedDateTimeUTC | 建立使用者裝置關聯時的日期和時間。 使用 UTC 格式。                                | 11/23/2016 12:00:00 AM |
| IsDeleted          | 指出使用者已取消註冊該裝置，且關聯不再是最新的。 | True/False             |
| EndedDateTimeUTC   | IsDeleted 變更為 **True** 的 UTC 日期和時間。                                              | 06/23/2017 12:00:00 AM |

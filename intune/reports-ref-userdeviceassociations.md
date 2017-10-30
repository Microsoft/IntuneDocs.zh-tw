---
title: "使用者裝置關聯 | Microsoft Docs"
description: "Intune 資料倉儲 API 中 [使用者裝置關聯] 類別實體集合的參考主題。"
keywords: "Intune 資料倉儲"
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 09/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: BCDBABCB-A7B1-42F2-BDD1-D055E33F2239
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 490e29f87c65875a385472e6abe9400363383f9b
ms.sourcegitcommit: bb2c181fd6de929cf1e5d3856e048d617eb72063
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/20/2017
---
# <a name="reference-for-user-device-association-entity"></a>使用者裝置關聯實體的參考

[使用者裝置關聯] 類別包含 [使用者裝置關聯] 實體，用來定義組織中的裝置關聯。

**使用者裝置關聯**

[使用者裝置關聯] 實體代表組織中的已定義裝置關聯。

| Name               | 說明                                                                                      | 範例                |
|--------------------|--------------------------------------------------------------------------------------------------|------------------------|
| UserKey            | 資料倉儲中使用者的唯一識別碼 - Surrogate 索引鍵。                             | 123                    |
| DeviceKey          | 資料倉儲中裝置的唯一識別碼。                                           | 123                    |
| CreatedDateTimeUTC | 建立使用者裝置關聯之時的 UTC 日期和時間。                               | 11/23/2016 12:00:00 AM |
| IsDeleted          | 指出使用者已取消註冊該裝置，且關聯不再是最新的。 | True                   |
| EndedDateTimeUTC   | IsDeleted 變更為 **True** 的 UTC 日期和時間。                                         | 06/23/2017 12:00:00 AM |
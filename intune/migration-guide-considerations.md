---
title: 特殊移轉考量
titlesuffix: Microsoft Intune
description: 本文提供啟動 Microsoft Intune 的移轉活動之前的特殊移轉考量。
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f29d2894-e98b-4f2c-b444-a8ccc1b7efdd
ms.reviewer: dagerrit
ms.suite: ems
ms.openlocfilehash: bd59cf3a4764cc66d0e7d1f47e69c2ff93352387
ms.sourcegitcommit: 21db583d6a9d3c15a8a8ee5579309dff1cfe1f8b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2018
---
# <a name="special-migration-considerations"></a>特殊移轉考量

有一些特殊移轉考量可能適用於您現有的 MDM 提供者環境。

## <a name="factory-reset-for-apples-device-enrollment-program-dep"></a>針對 Apple 裝置註冊計劃 (DEP) 的原廠重設

Apple 裝置註冊計劃 (DEP) 設定了使用者無法移除的裝置組態。 若要保留 DEP 的進階管理功能，必須透過重設為原廠值將裝置回復成全新狀態以向 Intune 註冊。

若要繼續使用 DEP 管理來 Intune 中的裝置，請[使用裝置註冊計劃來設定 iOS 裝置註冊](device-enrollment-program-enroll-ios.md)。


## <a name="next-steps"></a>接下來的步驟

[階段 2：移轉活動](migration-guide-campaign.md)

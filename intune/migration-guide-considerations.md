---
title: 特殊移轉考量
titleSuffix: Microsoft Intune
description: 本文提供啟動 Microsoft Intune 的移轉活動之前的特殊移轉考量。
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f29d2894-e98b-4f2c-b444-a8ccc1b7efdd
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6f700a93c9640381e33b4b1d1fd442f9442acbe1
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/23/2019
ms.locfileid: "66050529"
---
# <a name="special-migration-considerations"></a>特殊移轉考量

有一些特殊移轉考量可能適用於您現有的 MDM 提供者環境。

## <a name="wipe-for-apples-device-enrollment-program-dep"></a>適用於 Apple 裝置註冊計劃 (DEP) 的抹除

Apple 裝置註冊計劃 (DEP) 設定了使用者無法移除的裝置組態。 若要保留 DEP 的進階管理功能，必須透過抹除將裝置回復成全新狀態以向 Intune 註冊。

若要繼續使用 DEP 管理來 Intune 中的裝置，請[使用裝置註冊計劃來設定 iOS 裝置註冊](device-enrollment-program-enroll-ios.md)。


## <a name="next-steps"></a>後續步驟

[階段 2：移轉活動](migration-guide-campaign.md)

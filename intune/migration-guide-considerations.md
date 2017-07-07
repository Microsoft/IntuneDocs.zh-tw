---
title: "特殊移轉考量"
description: "本文旨在提供客戶開始移轉活動之前的特殊移轉考量。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 06/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f29d2894-e98b-4f2c-b444-a8ccc1b7efdd
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: bc39ffd3a4f11a4c2b32f75dc5befcd8ce42f43e
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2017
---
# <a name="special-migration-considerations"></a>特殊移轉考量

[!INCLUDE[note for both-portals](./includes/note-for-both-portals.md)]

有一些特殊考量可能適用於您現有的 MDM 提供者環境。

## <a name="factory-reset-for-apples-device-enrollment-program-dep"></a>針對 Apple 裝置註冊計劃 (DEP) 的原廠重設

Apple 裝置註冊計劃 (DEP) 設定了使用者無法移除的裝置組態。 若要保留 DEP 的進階管理功能，必須透過重設為原廠值將裝置回復成全新狀態以向 Intune 註冊。

若要繼續使用 DEP 管理來 Intune 中的裝置，請[使用裝置註冊計劃來設定 iOS 裝置註冊](/intune/device-enrollment-program-enroll-ios)。


## <a name="next-steps"></a>後續步驟 

[階段 2：移轉活動](migration-guide-campaign.md)

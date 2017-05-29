---
title: "特殊移轉考量 | Microsoft Docs"
description: "本文旨在提供客戶開始移轉活動之前的特殊移轉考量。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/24/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f29d2894-e98b-4f2c-b444-a8ccc1b7efdd
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 7e0adb862d8c60805b3b34406e193df5a93be381
ms.contentlocale: zh-tw
ms.lasthandoff: 05/23/2017


---

# <a name="phase-1-special-migration-considerations"></a>階段 1︰特殊移轉考量

[!INCLUDE[note for both-portals](../includes/note-for-both-portals.md)]

有一些特殊考量可能適用於您現有的 MDM 提供者環境。

## <a name="factory-reset-for-apples-device-enrollment-program-dep"></a>針對 Apple 裝置註冊計劃 (DEP) 的原廠重設

Apple 裝置註冊計劃 (DEP) 設定了使用者無法移除的裝置組態。 若要保留 DEP 的進階管理功能，必須透過重設為原廠值將裝置回復成全新狀態以向 Intune 註冊。

在 Intune 中繼續使用 DEP 來管理裝置︰

1.  在 [Intune 中註冊 DEP](/intune-classic/deploy-use/ios-device-enrollment-program-in-microsoft-intune)

2.  移至您的 Apple DEP 帳戶，從現有的 MDM 提供者[重新指派 DEP 裝置序號](https://help.apple.com/deployment/business/#/tesf9562af26)給 Intune。

3.  [同步處理](/intune-classic/deploy-use/ios-device-enrollment-program-in-microsoft-intune)您的 DEP 帳戶和 Intune

4.  [建立並指派](/intune-classic/deploy-use/ios-device-enrollment-program-in-microsoft-intune)適當的 DEP 註冊設定檔給 Intune 中的序號。

5.  將裝置重設為原廠值 (透過您目前的 MDM 提供者從遠端進行或在每個裝置上手動進行)

6.  將裝置散發給使用者。

## <a name="next-steps"></a>後續步驟 

[階段 2：移轉活動](/intune-classic/plan-design/migration-phase2-migration-campaign)


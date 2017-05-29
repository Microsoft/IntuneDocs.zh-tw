---
title: "在 Intune 移轉期間設定應用程式保護原則 |Microsoft Docs"
description: "本文旨在提供 Intune 移轉期間設定應用程式保護原則的必要步驟。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/24/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 93cda587-bf56-4d41-b123-9fe203fad788
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: ec990ecdedff0e1b7f4fd6fd9d45fd2edc1571bd
ms.contentlocale: zh-tw
ms.lasthandoff: 05/23/2017


---

# <a name="phase-1-configure-app-protection-policies-optional"></a>階段 1：設定應用程式保護原則 (選用)

[!INCLUDE[note for both-portals](../includes/note-for-both-portals.md)]

應用程式保護原則可讓您加密應用程式、定義存取應用程式時的 PIN、在已進行 JB 或 Root 破解的裝置上封鎖應用程式的執行，此外還有其他許多的保護。 藉由套用行動裝置應用程式保護原則，如果使用者的手機遺失或遭竊，您可以選擇從遠端抹除公司資料，同時保留個人資料。

應用程式保護原則在應用程式層級套用安全性，而且不需註冊裝置。 它可用於已向或未向 Intune 註冊的裝置。 此外，它還可用於已向協力廠商 MDM 提供者註冊的裝置。

## <a name="app-protection-policies-with-lob-apps"></a>應用程式保護原則搭配 LOB 應用程式

您也可以利用 Microsoft Intune App SDK 或 [IOS](https://www.microsoft.com/download/details.aspx?id=45218&751be11f-ede8-5a0c-058c-2ee190a24fa6=True) 和 [Android](https://www.microsoft.com/download/details.aspx?id=47267) 平台適用的 Microsoft Intune App Wrapping Tool，將行動裝置應用程式保護原則擴充到您的企業營運 (LOB) 應用程式。

## <a name="how-do-app-protection-policies-help-during-migration"></a>應用程式保護原則在移轉期間如何提供協助？

移轉需要從舊的 MDM 提供者移除裝置，並將它們註冊到 Intune。 您應該先為此做規劃，並鼓勵使用者離開舊的 MDM 提供者，並立即註冊到 Intune。 不過，在移轉期間，有的使用者可能會延遲完成註冊程序，而且其裝置不受任一個 MDM 提供者所管理。

這段期間如果仍允許存取公司資源，可能會讓您的組織更易面臨裝置遭竊或公司資料遺失的風險，和/或如果封鎖資源的存取，可能造成生產力的損失。

Intune 可以在移轉期間提供公司資料保護，所以在沒有裝置層級的管理時，您的公司資料仍會受到完整保護。

在舊的 MDM 提供者停用條件式存取時，使用者在您將他們移轉到 Intune 的同時仍可維持生產力。

## <a name="task-list-for-app-protection-policies"></a>應用程式保護原則的工作清單

-   工作 1：了解[如何準備好設定行動裝置應用程式保護原則](/intune-classic/deploy-use/get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune)

-   工作 2：了解[如何建立及部署行動裝置應用程式保護原則](/intune-classic/deploy-use/create-and-deploy-mobile-app-management-policies-with-microsoft-intune)

## <a name="next-steps"></a>後續步驟 

[階段 1︰特殊移轉考量](/intune-classic/plan-design/migration-phase1-special-migration-considerations)


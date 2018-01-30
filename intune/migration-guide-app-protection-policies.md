---
title: "在 Intune 移轉期間設定應用程式保護原則"
description: "本文提供 Intune 移轉期間設定應用程式保護原則的必要步驟。"
keywords: 
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 07/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 93cda587-bf56-4d41-b123-9fe203fad788
ms.reviewer: dagerrit
ms.suite: ems
ms.openlocfilehash: d3c176b84a8555de245a1f4014c39885e50ab21d
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2018
---
# <a name="configure-app-protection-policies-optional"></a>設定應用程式保護原則 (選用)


應用程式保護原則可讓您：
* 加密應用程式
* 定義存取應用程式時的 PIN
* 封鎖應用程式使其無法在已破解或取得根權限的裝置上執行，以及許多其他的保護。

如果使用者的手機遺失或遭竊，您可以選擇從遠端抹除公司資料，同時保留個人資料。

應用程式保護原則在應用程式層級套用安全性，而且不需註冊裝置。 您可以將它們與已向或未向 Intune 註冊的裝置搭配使用。 此外，還可以將它們套用到已向協力廠商 MDM 提供者註冊的裝置。

## <a name="app-protection-policies-with-lob-apps"></a>應用程式保護原則搭配 LOB 應用程式

您也可以使用 [Microsoft Intune App SDK](app-sdk-get-started.md) 或 [IOS](https://www.microsoft.com/download/details.aspx?id=45218&751be11f-ede8-5a0c-058c-2ee190a24fa6=True) 和[Android](https://www.microsoft.com/download/details.aspx?id=47267) 平台適用的 Microsoft Intune App Wrapping Tool，將行動裝置應用程式保護原則擴充到您的商務營運 (LOB) 應用程式。

## <a name="how-do-app-protection-policies-help-during-migration"></a>應用程式保護原則在移轉期間如何提供協助？

在移轉中，您必須從舊的 MDM 提供者中移除裝置，並將它們註冊到 Intune。 您應該先為此做規劃，並鼓勵使用者離開舊的 MDM 提供者，並立即註冊到 Intune。 不過，在移轉期間，有的使用者可能會延遲完成註冊程序，而且其裝置不受任一個 MDM 提供者所管理。

這段期間如果仍允許存取公司資源，可能會讓您的組織更易面臨裝置遭竊或公司資料遺失的風險。 如果封鎖公司資源的存取，也可能會造成使用者生產力降低。

Intune 可以在移轉期間提供公司資料保護，所以在沒有裝置層級的管理時，您的公司資料仍會受到完整保護。

在舊的 MDM 提供者停用條件式存取時，使用者在您將他們移轉到 Intune 的同時仍可維持生產力。

## <a name="task-list-for-app-protection-policies"></a>應用程式保護原則的工作清單

1. [建立應用程式保護原則](app-protection-policies.md#create-an-app-protection-policy)
2. [部署原則](app-protection-policies.md#deploy-a-policy-to-users)


## <a name="next-steps"></a>接下來的步驟

[特殊移轉考量](migration-guide-considerations.md)

---
title: 在移轉期間設定應用程式保護原則
titleSuffix: Microsoft Intune
description: 本文提供 Microsoft Intune 移轉期間設定應用程式防護原則的必要步驟。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/09/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 93cda587-bf56-4d41-b123-9fe203fad788
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8c0571eb2a369e440b3c7732b6d55ba05ace2c34
ms.sourcegitcommit: 637375a390b6e34f9c4415c77b99fe2980bbf554
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2020
ms.locfileid: "75839363"
---
# <a name="configure-app-protection-policies-optional"></a>設定應用程式保護原則 (選用)


應用程式保護原則可讓您：
* 加密應用程式
* 定義存取應用程式時的 PIN
* 封鎖應用程式使其無法在已破解或取得根權限的裝置上執行，以及許多其他的保護。

如果使用者的手機遺失或遭竊，您可以選擇從遠端抹除公司資料，同時保留個人資料。

應用程式保護原則在應用程式層級套用安全性，而且不需註冊裝置。 您可以將它們與已向或未向 Intune 註冊的裝置搭配使用。 此外，還可以將它們套用到已向協力廠商 MDM 提供者註冊的裝置。

## <a name="app-protection-policies-with-lob-apps"></a>應用程式保護原則搭配 LOB 應用程式

您也可以使用 [Microsoft Intune App SDK](../developer/app-sdk-get-started.md) 或 iOS 和 Android 平台適用的 Microsoft Intune App Wrapping Tool，將行動裝置應用程式保護原則擴充到您的企業營運 (LOB) 應用程式。 如需詳細資訊，請參閱[適用於 iOS 的 App Wrapping Tool](../developer/app-wrapper-prepare-ios.md) 和[適用於 Android 的 App Wrapping Tool](./../developer/app-wrapper-prepare-android.md)。 此外，請參閱[規劃 LOB 應用程式以進行應用程式保護](../developer/apps-prepare-mobile-application-management.md)。

## <a name="how-do-app-protection-policies-help-during-migration"></a>應用程式保護原則在移轉期間如何提供協助？

在移轉中，您必須從舊的 MDM 提供者中移除裝置，並將它們註冊到 Intune。 您應該先為此做規劃，並鼓勵使用者離開舊的 MDM 提供者，並立即註冊到 Intune。 不過，在移轉期間，有的使用者可能會延遲完成註冊程序，而且其裝置不受任一個 MDM 提供者所管理。

這段期間如果仍允許存取公司資源，可能會讓您的組織更易面臨裝置遭竊或公司資料遺失的風險。 如果封鎖公司資源的存取，也可能會造成使用者生產力降低。

Intune 可以在移轉期間提供公司資料保護，所以在沒有裝置層級的管理時，您的公司資料仍會受到完整保護。

當您在舊的 MDM 提供者中停用條件式存取時，使用者在您將其上線至 Intune 的同時仍能保有生產力。

## <a name="task-list-for-app-protection-policies"></a>應用程式保護原則的工作清單

- [如何建立及部署應用程式保護原則](~/apps/app-protection-policies.md)

## <a name="next-steps"></a>後續步驟

[特殊移轉考量](migration-guide-considerations.md)

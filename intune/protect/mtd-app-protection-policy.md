---
title: 使用 Intune 建立 Mobile Threat Defense (MTD) 應用程式防護原則
titleSuffix: Microsoft Intune
description: 使用 Microsoft Intune 建立 Mobile Threat Defense (MTD) 應用程式防護原則。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/20/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: 900858d9c437f2d2662260ca62534a987446d2b2
ms.sourcegitcommit: 045ca42cad6f86024af9a38a380535f42a6b4bef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2020
ms.locfileid: "77782123"
---
# <a name="create-mobile-threat-defense-app-protection-policy-with-intune"></a>使用 Intune 建立 Mobile Threat Defense 應用程式防護原則

搭配 Mobile Threat Defense (MTD) 的 Intune 可協助偵測行動裝置上的威脅及評估風險。 您可以建立評估風險的 Intune 應用程式保護原則，以決定是否允許裝置存取公司資料。

> [!NOTE]
> 此文章適用於所有支援應用程式防護原則的 Mobile Threat Defense 合作夥伴：
>
> - Better Mobile (Android、iOS/iPadOS)
> - Zimperium (Android、iOS/iPadOS)
> - Lookout for Work (Android、iOS/iPadOS)。

## <a name="before-you-begin"></a>開始之前

在 MTD 的設定過程中，您已在 MTD 夥伴主控台中建立一項原則來將各種威脅分類為高、中和低。 您現在需要在 Intune 應用程式防護則中設定 Mobile Threat Defense 等級。

使用 MTD 建立應用程式防護原則的必要條件：

- 設定 MTD 與 Intune 整合。 若沒有此整合，MTD 應用程式防護原則將不會有作用。

## <a name="to-create-an-mtd-app-protection-policy"></a>建立 MTD 應用程式防護原則

使用此程序來[建立 iOS/iPadOS 或 Android 的應用程式保護原則](../apps/app-protection-policies.md#app-protection-policies-for-iosipados-and-android-apps)，然後在 [應用程式]  、[條件式啟動]  和 [指派]  頁面中使用下列資訊：

- **應用程式**：選取要作為應用程式保護原則目標的應用程式。 針對此功能集，根據您所選 Mobile Threat Defense 廠商的裝置風險評定，以封鎖或選擇性抹除這些應用程式。
- **條件式啟動**：在 [裝置狀況]  下，使用下拉式方塊選取 [允許的最高裝置威脅等級]  。

  威脅等級 [值]  的選項：

  - **安全**：這個層級最安全。 裝置不能在具有任何威脅的同時還能存取公司資源。 發現任何威脅時，即會將裝置評估為不相容。
  - **低**：如果只有低層級的威脅，則會將裝置評估為符合規範。 任何更高等級的威脅都會使裝置處於不相容狀態。
  - **中等**：如果在裝置上發現的威脅為低或中層級，則會將裝置評估為符合規範。 如果偵測到高層級的威脅，則會將裝置判斷為不相容。
  - **高**：此等級最不安全並允許所有威脅等級，且只將 Mobile Threat Defense 作為回報之用。 裝置必須要有使用此裝置啟用的 MTD 應用程式。

  [動作]  的選項：

  - **封鎖存取**
  - **抹除資料**

- **指派**：將原則指派給使用者群組。  透過 Intune 應用程式保護評估群組成員所用的裝置，以在目標應用程式上存取公司資料。

## <a name="next-steps"></a>後續步驟

- 深入了解 Microsoft Intune 中的 [Mobile Threat Defense](~/protect/mobile-threat-defense.md)。

---
title: "防止公司資料從 Office 365 行動應用程式外洩 | Microsoft Docs"
description: "使用 Intune 透過行動應用程式管理 (MAM) 原則，協助避免公司資料從 Office 365 行動應用程式或其他企業營運 (LOB) 應用程式外洩，來保護組織的資料。"
keywords: 
author: jeffgilb
ms.author: jeffgilb
manager: angrobe
ms.date: 11/22/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 19be3de7-539c-49f5-8c46-5363b987fef9
ms.reviewer: pchacon
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: ab6d9b6b296fb4e1fb0aaa9496fede28976728dc
ms.openlocfilehash: 4c13eb3149ea0cc21604a5a05445cfccdc984293
ms.lasthandoff: 04/14/2017


---

# <a name="quick-start-guide-prevent-company-data-leaks-from-office-365-mobile-apps"></a>快速入門指南︰防止公司資料從 Office 365 行動應用程式外洩

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Microsoft Intune 使用行動應用程式管理 (MAM) 原則，避免公司資料從 Office 365 行動應用程式或企業營運 (LOB) 應用程式外洩，協助您保護組織的資料。 使用者不需要在 Intune 行動裝置管理 (MDM) 中註冊其裝置，就能使用 Intune MAM 原則。 因此，如果有使用者不想要將其 BYOD iOS 或 Android 行動裝註冊到 Microsoft MDM 解決方案 (Intune、Configuration Manager 或 EAS)，您想要在不管理使用者裝置的情況下，保護公司資料，或您已在使用非 Microsoft MDM 解決方案，Intune 都能協助您提高公司的資料安全性。   

## <a name="is-this-quick-start-guide-right-for-me"></a>我適合使用此快速入門指南嗎？
您要允許使用者在其 iOS 和 Android 裝置上存取 Office 365 和 LOB 應用程式資料，而不需要在行動裝置管理 (MDM) 解決方案中註冊其裝置，但仍能控制他們可以或不可以對該資料執行哪些工作 (例如複製和貼至個人應用程式) 嗎？

如果是，Microsoft Intune 可讓您為 iOS 與 Android 上的 Office 365 行動應用程式設定 MAM 原則，包括剪下/複製/貼上限制、防止「另存新檔」、設定 PIN 需求，以及能夠從遠端抹除由 MAM 保護的資料。  如此不需要使用者將其裝置註冊到 MDM 解決方案，也能保護公司資料，同時維持絕佳的 Office 行動應用程式終端使用者體驗。

## <a name="how-do-i-do-it"></a>我該怎麼做？
1.    初步了解 [Intune 行動應用程式管理 (MAM) 如何](/intune/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune)運作。
2.    了解您在 Azure 入口網站中[建立 MAM 原則之前所需執行的作業](/intune/deploy-use/get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune)。
3.    使用 Intune [建立和部署 MAM 原則](/intune/deploy-use/get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune)。

### <a name="additional-information"></a>其他資訊：
- 使用 MAM 啟用應用程式的[終端使用者體驗](/intune/deploy-use/end-user-experience-for-mam-enabled-apps-with-microsoft-intune)。
- [使用 Intune 準備 MAM 的 LOB 應用程式](/intune/deploy-use/decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune)
- <a href="https://www.microsoft.com/cloud-platform/microsoft-intune-partners" target="_blank"> Microsoft Intune 應用程式夥伴清單 &rarr;</a> 提供啟用 MAM 的應用程式。

## <a name="what-should-i-do-next"></a>下一步該怎麼做？
[從非 Microsoft MDM 解決方案移轉到 Microsoft Intune](/intune/deploy-use/migrate-to-intune)

[將裝置註冊到 Intune MDM](/intune/deploy-use/enroll-devices-in-microsoft-intune)


---
title: "部署原則和應用程式"
description: "您可以啟用原則設定，以及部署將在註冊裝置以進行管理之後立即套用的應用程式。"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 02/14/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e0d8e98f-7dd8-4cbf-887c-a9af63ffe970
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: cf86d82fe636d2641f82ca951e508bea93abf683
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2017
---
# <a name="create-policies-and-publish-apps"></a>建立原則和發行應用程式

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

本主題將告訴 Intune 系統管理員如何建立原則、發佈應用程式，接著將它們部署到受管理裝置。

開始在 Intune 中註冊應用程式之前，您可以啟用要在將這些裝置納入管理之後立即部署的原則設定及應用程式。 Intune 原則提供設定，協助您控制行動裝置上的安全性設定、維護電腦的 Windows 防火牆和 Endpoint Protection 設定，以及部署應用程式。 您可以設定原則、新增應用程式，以及部署這些應用程式，使裝置在 Intune 中註冊之後就能立即接收設定和應用程式。

原則和應用程式是平台特定的。

## <a name="manage-device-settings"></a>管理裝置設定

 裝置原則設定是根據每個平台來設定和管理的。 下列連結提供其各自平台的可用設定清單︰

- [iOS](/intune-classic/deploy-use/ios-policy-settings-in-microsoft-intune)
- [Android and和 Samsung KNOX Standard](/intune-classic/deploy-use/android-policy-settings-in-microsoft-intune)
- [Android for Work](/intune-classic/deploy-use/android-for-work-policy-settings-in-microsoft-intune)
- [Windows 10 (電腦與行動裝置)](/intune-classic/deploy-use/windows-10-policy-settings-in-microsoft-intune)
- [Windows 8.1](/intune-classic/deploy-use/windows-configuration-policy-settings-in-microsoft-intune)
- [Windows Phone 8.1](/intune-classic/deploy-use/windows-phone-8-1-policy-settings-in-microsoft-intune)
- [Windows 小組](/intune-classic/deploy-use/windows-team-configuration-policy-settings-in-microsoft-intune)
- [執行 Intune 軟體用戶端的 Windows 電腦](/intune-classic/deploy-use/policies-to-protect-windows-pcs-in-microsoft-intune)

您可以深入了解如何[透過 Microsoft Intune 原則管理裝置上的設定和功能](/intune-classic/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies)。

## <a name="add-and-deploy-apps"></a>新增和部署應用程式

您可以將應用程式新增至 Intune，然後以下列兩種方式將它們部署到受管理的裝置：
- **必要安裝** - 應用程式會將該應用程式自動安裝到受管理的裝置
- **可用安裝** - 應用程式會出現在 Intune 公司入口網站中，讓使用者可以選擇是否要在其裝置上安裝它們

### <a name="add-apps"></a>新增應用程式

您必須使用其中一種下列方法，先讓應用程式可以在 Intune 中取得：
- [為已註冊的裝置新增應用程式](/intune-classic/deploy-use/add-apps-for-mobile-devices-in-microsoft-intune)
- [為 Intune 軟體用戶端電腦新增應用程式](/intune-classic/deploy-use/add-apps-for-windows-pcs-in-microsoft-intune)

### <a name="deploy-apps"></a>部署 App

應用程式現在已可在 Intune 中取得，您可將它部署到受管理的裝置：
- [將應用程式部署到裝置](/intune-classic/deploy-use/deploy-use/deploy-apps-in-microsoft-intune)
- 部署大量採購應用程式：
    - [iOS - 大量採購方案](/intune-classic/deploy-use/manage-ios-apps-you-purchased-through-a-volume-purchase-program-with-microsoft-intune)
    - [商務用 Windows 市集](/intune-classic/deploy-use/manage-apps-you-purchased-from-the-windows-store-for-business-with-microsoft-intune)
    - [Android for Work](/intune-classic/deploy-use/android-for-work-apps)

    為部署設定好應用程式後，您就可以[設定應用程式](/intune-classic/deploy-use/monitor-apps-in-microsoft-intune)。

>[!div class="step-by-step"]

>[&larr; **組織使用者和裝置**](.\start-with-a-paid-subscription-to-microsoft-intune-step-5.md)       [**自訂公司入口網站** &rarr;](/intune/company-portal-customize)  

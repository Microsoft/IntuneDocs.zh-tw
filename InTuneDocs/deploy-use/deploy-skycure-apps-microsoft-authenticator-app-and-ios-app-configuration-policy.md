---
title: "部署 Skycure 應用程式、Microsoft Authenticator 應用程式和 iOS 設定原則 | Microsoft Docs"
description: "將 Skycure 應用程式、Microsoft Authenticator 應用程式和 iOS 設定原則部署至 Intune 傳統主控台。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/16/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 45826fbc-6df5-41b2-8e80-d1353f904b43
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: e10453155343bb7fd91a4fd3874d393ef78d0b1a
ms.openlocfilehash: 0b6f9bde77b5b88cc66ab10419b7d6e083f7cb6b
ms.lasthandoff: 04/25/2017


---

# <a name="deploy-skycure-apps-microsoft-authenticator-app-and-ios-app-configuration-policy"></a>部署 Skycure 應用程式、Microsoft Authenticator 應用程式和 iOS 應用程式設定原則

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

## <a name="before-you-begin"></a>開始之前

-   下列步驟必須在 [Intune 傳統主控台](https://manage.microsoft.com/)中完成。

-   使用先前在 Skycure 管理主控台中設定的同一個 Azure AD 帳戶，此帳戶應該與用來登入 Intune 傳統主控台的帳戶相同。

-   確定您已熟悉下列程序：

    -   [使用 Intune 部署應用程式](https://docs.microsoft.com/intune/deploy-use/deploy-apps-in-microsoft-intune)。

    -   [部署 iOS 應用程式設定原則](https://docs.microsoft.com/intune/deploy-use/configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune)。

## <a name="to-deploy-skycure-apps-microsoft-authenticator-app-and-the-ios-app-configuration-policy"></a>部署 Skycure 應用程式、Microsoft Authenticator 應用程式和 iOS 應用程式設定原則

1.  在 Intune 傳統主控台中，選擇 [應用程式] &gt; [應用程式]，以檢視您可以管理的應用程式清單。

2.  選取下列應用程式：

    a.  Microsoft Authenticator

    b。  適用於 Android 的 Skycure 應用程式

    c.  適用於 iOS 的 Skycure 應用程式

       ![Intune 傳統主控台中要部署的所有應用程式](../media/mtp/skycure-deploy-app-1.png)

3.  選擇 [管理部署]、選取含有 Skycure 使用者的 Azure AD 安全性群組，然後按 [下一步]。

4.  在 [部署動作] 頁面上，從 [核准] 下拉式清單中選取 [必要安裝] 選項，然後按 [下一步]。

    ![Intune 傳統主控台的部署動作](../media/mtp/skycure-deploy-app-2.png)

5.  在 [VPN 設定檔] 頁面上，從 [VPN 原則] 下拉式清單中選取 [無] 選項，然後按 [下一步]。

6.  在 [行動裝置應用程式組態] 頁面上，選取先前從 [應用程式設定原則] 下拉式清單中建立的 iOS 應用程式設定原則，然後按一下 [完成]。

    ![Intune 傳統主控台的行動裝置應用程式組態](../media/mtp/skycure-deploy-app-3.png)

## <a name="next-steps"></a>後續步驟

[設定 Skycure 與 Intune 整合](https://docs.microsoft.com/intune/deploy-use/setup-the-skycure-integration-with-Intune)


---
title: "部署 Skycure 應用程式、Microsoft Authenticator 應用程式和 iOS 設定原則"
description: "部署 Skycure 應用程式、Microsoft Authenticator 應用程式與 iOS 設定原則到 Intune 傳統入口網站。"
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
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 47b5010c2e4262f61ca8e67727697493ace54928
ms.sourcegitcommit: 1a54bdf22786aea1cf1b497d54024470e1024aeb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/10/2017
---
# <a name="deploy-skycure-apps-microsoft-authenticator-app-and-ios-app-configuration-policy"></a>部署 Skycure 應用程式、Microsoft Authenticator 應用程式和 iOS 應用程式設定原則

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

## <a name="before-you-begin"></a>開始之前

-   下面的步驟必須在 [Intune 傳統入口網站](https://manage.microsoft.com/)中完成。

-   使用先前在 Skycure 管理主控台中設定的同一個 Azure AD 帳戶，此帳戶應與用於登入 Intune 傳統入口網站的帳戶相同。

-   確定您已熟悉下列程序：

    -   [使用 Intune 部署應用程式](/intune-classic/deploy-use/deploy-apps-in-microsoft-intune)。

    -   [部署 iOS 應用程式設定原則](/intune-classic/deploy-use/configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune)。

## <a name="to-deploy-skycure-apps-microsoft-authenticator-app-and-the-ios-app-configuration-policy"></a>部署 Skycure 應用程式、Microsoft Authenticator 應用程式和 iOS 應用程式設定原則

1.  在 Intune 傳統入口網站中，選擇 [應用程式] &gt;[應用程式]，以檢視您可以管理的應用程式清單。

2.  選取下列應用程式：

    a.  Microsoft Authenticator

    b。  適用於 Android 的 Skycure 應用程式

    c.  適用於 iOS 的 Skycure 應用程式

       ![Intune 傳統入口網站中要部署的所有應用程式](../media/mtp/skycure-deploy-app-1.png)

3.  選擇 [管理部署]、選取含有 Skycure 使用者的 Azure AD 安全性群組，然後按 [下一步]。

4.  在 [部署動作] 頁面上，從 [核准] 下拉式清單中選取 [必要安裝] 選項，然後按 [下一步]。

    ![Intune 傳統入口網站的部署動作](../media/mtp/skycure-deploy-app-2.png)

5.  在 [VPN 設定檔] 頁面上，從 [VPN 原則] 下拉式清單中選取 [無] 選項，然後按 [下一步]。

6.  在 [行動裝置應用程式組態] 頁面上，選取先前從 [應用程式設定原則] 下拉式清單中建立的 iOS 應用程式設定原則，然後按一下 [完成]。

    ![Intune 傳統入口網站的行動裝置應用程式設定](../media/mtp/skycure-deploy-app-3.png)

## <a name="next-steps"></a>後續步驟

[設定 Skycure 與 Intune 整合](/intune-classic/deploy-use/setup-the-skycure-integration-with-Intune)

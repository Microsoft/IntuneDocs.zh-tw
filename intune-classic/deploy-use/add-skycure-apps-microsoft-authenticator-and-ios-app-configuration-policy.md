---
title: "新增 Skycure 應用程式、Microsoft Authenticator 應用程式和 iOS 設定原則"
description: "將 Skycure 應用程式、Microsoft Authenticator 應用程式和 iOS 設定原則新增至 Intune 傳統主控台。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/16/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 018d26f4-4a75-4e27-bb04-54f54106cb2f
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: df3c42d8b52d1a01ddab82727e707639d5f77c16
ms.openlocfilehash: 425b86e92281bb6e3657a6c806be269ccae94311
ms.contentlocale: zh-tw
ms.lasthandoff: 06/08/2017


---

# <a name="add-skycure-apps-microsoft-authenticator-app-and-ios-configuration-policy"></a>新增 Skycure 應用程式、Microsoft Authenticator 應用程式和 iOS 設定原則

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

您必須使用 Intune 來新增及部署 Skycure 應用程式，讓使用者可在其行動裝置上識別出威脅時收到通知，以及收到修復威脅的指引。

此外，您還需要 [Microsoft Authenticator](https://docs.microsoft.com/azure/multi-factor-authentication/end-user/microsoft-authenticator-app-how-to) 和 iOS 應用程式設定原則，前者讓使用者能夠透過 Azure AD 檢查其身分識別，後者會對 Skycure iOS 應用程式發出訊號以使用 Intune 和 Azure AD 單一登入 (SSO)，如此一來，使用者就不需要在每次登入 Skycure 應用程式時輸入使用者名稱和密碼。

## <a name="before-you-begin"></a>開始之前

-   下列步驟必須在 [Intune 傳統主控台](https://manage.microsoft.com/)中完成。

-   使用先前在 Skycure 管理主控台中設定的同一個 Azure AD 帳戶，此帳戶應該與用來登入 Intune 傳統主控台的帳戶相同。

-   您需要備妥 Skycure 整合檔案以供使用。 這是先前從 Skycure 管理主控台下載的 .zip 檔，其中包含 **skycure\_configuration.plist** 檔案以及 iOS 應用程式設定原則參數。

-   確定您已熟悉下列程序：

    -   [將應用程式新增至 Intune](/intune-classic/deploy-use/add-apps)。

    -   [將 iOS 應用程式設定原則新增至 Intune](/intune-classic/deploy-use/configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune)。

## <a name="to-add-the-skycure-app-for-android"></a>新增適用於 Android 的 Skycure 應用程式

1.  在 Intune 傳統主控台中，選擇 [應用程式] &gt; [新增應用程式] 來啟動 Intune 軟體發佈者，然後按 [下一步]。

2.  在 [軟體安裝程式] 頁面上，選擇 [外部連結]，然後在 [指定 URL] 下方貼上[適用於 Android 的 Skycure 應用程式的 URL](https://play.google.com/store/apps/details?id=com.skycure.skycure)。

    ![Intune 軟體發佈者的指定 URL](../media/mtp/skycure-add-apps-1.png)

3.  在 [軟體描述] 頁面上，輸入**發佈者**、**名稱**和**描述**；選取 [在公司入口網站中將此項目顯示為熱門應用程式並將它反白]；然後按 [下一步]。

    ![Intune 軟體發佈者的軟體描述](../media/mtp/skycure-add-apps-2.png)

4.  依序按一下 [上傳] 和 [關閉]。

## <a name="to-add-the-skycure-app-for-ios"></a>新增適用於 iOS 的 Skycure 應用程式

1.  在 Intune 傳統主控台中，選擇 [應用程式] &gt; [新增應用程式] 來啟動 Intune 軟體發佈者，然後按 [下一步]。

2.  在 [軟體安裝程式] 頁面上，選擇 [App Store 中所管理的 iOS 應用程式]，然後在 [指定 URL] 下方貼上[適用於 iOS 的 Skycure 應用程式的 URL](https://itunes.apple.com/us/app/skycure/id695620821?mt=8)。

    ![Intune 軟體發佈者的受管理 iOS 應用程式](../media/mtp/skycure-add-apps-3.png)

3.  在 [軟體描述] 頁面上，輸入**發佈者**、**名稱**和**描述**；選取 [在公司入口網站中將此項目顯示為熱門應用程式並將它反白]；然後按 [下一步]。

    ![Intune 軟體發佈者選項](../media/mtp/skycure-add-apps-4.png)

4.  在 [需求] 頁面上，選取 [行動裝置類型] 下方的 [任何] 選項，然後按 [下一步]。

5.  依序按一下 [上傳] 和 [關閉]。

## <a name="to-add-the-microsoft-authenticator-app-for-ios"></a>新增適用於 iOS 的 Microsoft Authenticator 應用程式

1.  在 Intune 傳統主控台中，選擇 [應用程式] &gt; [新增應用程式] 來啟動 Intune 軟體發佈者，然後按 [下一步]。

2.  在 [軟體安裝程式] 頁面上，選擇 [App Store 中所管理的 iOS 應用程式]，然後在 [指定 URL] 下方貼上[適用於 iOS 的 Microsoft Authenticator 應用程式的 URL](https://itunes.apple.com/us/app/microsoft-authenticator/id983156458?mt=8)。

    ![Intune 軟體發佈者的受管理 iOS 應用程式 2](../media/mtp/skycure-add-apps-5.png)

3.  在 [軟體描述] 頁面上，輸入**發佈者**、**名稱**和**描述**；選取 [在公司入口網站中將此項目顯示為熱門應用程式並將它反白]；然後按 [下一步]。

    ![Intune 軟體發佈者的受管理 iOS 應用程式 3](../media/mtp/skycure-add-apps-6.png)

4.  在 [需求] 頁面上，選取 [行動裝置類型] 下方的 [任何] 選項，然後按 [下一步]。

5.  依序按一下 [上傳] 和 [關閉]。

## <a name="to-add-the-skycure-ios-app-configuration-policy"></a>新增 Skycure iOS 應用程式設定原則

1.  在 Intune 傳統主控台中，選擇 [原則] &gt; [概觀] &gt; [新增原則]。

2.  在原則清單中，展開 [iOS]、選擇 [行動應用程式設定原則 (iOS 8.0 (含) 以上)]，然後選擇 [建立原則]。

    ![iOS 應用程式設定原則](../media/mtp/skycure-add-apps-7.png)

3.  在 [建立原則] 頁面的 [一般] 區段中，為 iOS 應用程式設定原則提供名稱和選擇性描述。

    a.  使用 [記事本] 之類的文字編輯器開啟 **skycure\_configuration.plist** 檔案、將內容複製並貼到 [行動應用程式設定原則] 內容中、選擇 [驗證]，然後選擇 [儲存原則]。

       ![iOS 應用程式設定原則 2](../media/mtp/skycure-add-apps-8.png)

## <a name="next-steps"></a>後續步驟

[部署 Skycure 應用程式、Microsoft Authenticator 應用程式和 iOS 應用程式設定原則](/intune-classic/deploy-use/deploy-skycure-apps-microsoft-authenticator-app-and-ios-app-configuration-policy)


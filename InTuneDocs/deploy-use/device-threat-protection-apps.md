---
title: "部署 Lookout for Work 應用程式 | Microsoft Docs"
description: "設定及部署適用於 Android 的 Lookout for Work 應用程式。"
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 12/20/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 524c4209-ad57-4d35-955e-a00d796bf858
ms.reviewer: sandera
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 6f687a1db84b49bc173d2067ab95598b4485daa8
ms.openlocfilehash: ab94439d9fd5300d61c5991434d41f7fdca693d2


---

# <a name="configure-and-deploy-lookout-for-work-apps"></a>設定及部署 Lookout for Work 應用程式

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

本文說明如何為 Android 和 iOS 裝置，設定和部署 Lookout for Work 應用程式。

## <a name="android-google-play-store-app"></a>Android (Google Play 商店應用程式)

1.    在 [Microsoft Intune 系統管理員主控台](https://manage.microsoft.com)中，移至 [應用程式]，然後選擇 [新增應用程式]。
2.    在發行者的 [軟體安裝程式] 頁面上，選擇 [外部連結]，然後指定下列 URL：https://play.google.com/store/apps/details?id=com.lookout.enterprise
  >[!NOTE]
  >請勿按下要求 Managed Browser 的方塊。

3.    在 [軟體描述] 頁面上，填入下列資訊：
  * **發行者**︰Lookout 行動安全性
  * **名稱**︰Lookout for Work
  * **描述**︰Lookout 提供最佳行動裝置威脅保護，以確保您的裝置安全無虞。 當裝置上安裝 Lookout 應用程式時，該應用程式可為您的裝置提供威脅保護，並在找到任何威脅時，通知您及您公司的系統管理員。
  * **類別**：電腦管理

4. 成功完成時，您會看到「上傳資料至 Microsoft Intune 已順利完成」訊息。

  當您按一下 Intune 主控台中的 [應用程式] 時，現在會在清單 ![在清單中顯示 Lookout for Work 應用程式之 Intune 管理主控台 [應用程式] 頁面的螢幕擷取畫面](../media/mtp/lookout-app-listed-intune-console.png)中看到 [Lookout for Work] 應用程式

5. 若要將應用程式部署給使用者，請選取 Lookout for Work 應用程式，然後選擇 [管理部署]。

  您必須選取加入 Lookout MTP 主控台中 「Enrollment Management」 (註冊管理) 選項的相同使用者。  如需將使用者群組新增至 Lookout MTP 的資訊，請參閱[設定訂用帳戶使用 Lookout MTP](configure-and-deploy-lookout-for-work-apps.md) 一節中的步驟 3。

  >[!IMPORTANT]
  > Intune 應用程式部署精靈未發現 Azure AD 使用者群組，並會改用 Intune 使用者群組。 因此您必須建立以 Lookout MTP 主控台中註冊之 Azure AD 使用者群組為基礎的 Intune 使用者群組，如[這個主題](plan-your-user-and-device-groups.md)中所述。

6. 選擇 [必要安裝] 選項，要求必須在使用者裝置上安裝 Lookout 應用程式。

## <a name="ios-enterprise-signed-version-of-lookout-app"></a>iOS (Lookout 應用程式的企業簽章版本)

1. 確定您的裝置上已設定 **iOS 管理**。 如需如何設定裝置之 iOS 管理的指示，請參閱[設定 iOS 和 Mac 裝置管理](set-up-ios-and-mac-management-with-microsoft-intune.md)。

2. **重新簽署** Lookout for Work iOS 應用程式。 Lookout 會將其 Lookout for Work iOS 應用程式散發到 iOS App Store 之外。 **發佈應用程式之前**，您必須使用 iOS 企業開發人員憑證重新簽署應用程式。 如需重新簽署 Lookout for Work iOS 應用程式的詳細指示，請參閱 Lookout 網站上的 [Lookout for Work iOS App Re-Signing Process](https://personal.support.lookout.com/hc/en-us/articles/114094038714)。

3. 執行下列動作，啟用 iOS 使用者的 Azure Active Directory 驗證：
  1.  登入 [Azure Active Directory 管理入口網站](https://manage.windowsazure.com)，然後巡覽至應用程式頁面。
  2.  新增 **Lookout for Work iOS 應用程式**作為**原生用戶端應用程式**。
  ![顯示 [原生用戶端應用程式] 選項的 [新增應用程式] 對話方塊螢幕擷取畫面](../media/mtp/aad-add-app.png)
  3. 以您簽署 IPA 時所選取的客戶配套識別碼取代 **com.lookout.enterprise.yourcompanyname**。
  4.  新增其他重新導向 URI：**&lt;公司入口網站 ://code/>**，後面接著原始重新導向 URI 的 URL 編碼版本。
  5.  新增**委派的權限**至您的應用程式。

  如需詳細資訊，請參閱[設定原生用戶端應用程式](https://azure.microsoft.com/en-us/documentation/articles/app-service-mobile-how-to-configure-active-directory-authentication/#optional-configure-a-native-client-application)。

4. 上傳重新簽署的 .ipa 檔案，如[在 Microsoft Intune 中新增行動裝置的應用程式](https://docs.microsoft.com/en-us/intune/deploy-use/add-apps-for-mobile-devices-in-microsoft-intune)主題中所述。 將最低作業系統版本設定為 iOS 8.0 或更新版本。

  ![顯示應用程式清單中 Lookout for Work 應用程式之 Intune 系統管理員主控台應用程式頁面的螢幕擷取畫面](../media/mtp/ios-app-uploaded-intune.png)

5. 建立受管理的應用程式設定原則，如[在 Microsoft Intune 中使用行動應用程式設定原則設定 iOS 應用程式](https://docs.microsoft.com/en-us/intune/deploy-use/configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune)主題中所述。

  ![反白顯示 iOS 8.0 或更新版應用程式設定原則之 [建立新原則精靈] 的螢幕擷取畫面](../media/mtp/ios-app-config.png)

6. **若要將應用程式部署給使用者**，請選取 Lookout for Work 應用程式，然後選擇 [管理部署]。

  您必須選取已在 Lookout 主控台中新增至 「Enrollment Management」 (註冊管理) 選項的相同使用者。  如需將使用者群組新增至 Lookout MTP 的資訊，請參閱[設定訂用帳戶使用 Lookout 裝置威脅防護](https://docs.microsoft.com/sccm/protect/deploy-use/configure-and-deploy-lookout-for-work-apps)一節中的步驟 3。

  >[!IMPORTANT]
  > Intune 應用程式部署精靈無法察覺 Azure AD 使用者群組，而會改用 Intune 使用者群組，因此您必須依據 Lookout 主控台中已註冊的 Azure AD 使用者群組，來建立一個 Intune 使用者群組 (如[本主題](plan-your-user-and-device-groups.md)中所述)。

  選擇 [必要安裝] 選項，要求必須在使用者裝置上安裝 Lookout 應用程式。

## <a name="what-happens-when-the-deployed-app-is-opened-on-the-device"></a>在裝置上開啟已部署的應用程式時，會發生什麼事

當使用者在裝置上開啟 Lookout for Work 時，系統會提示他們啟用應用程式，並選擇 [使用 Azure Active Directory 登入] 選項。 您可以在下列主題中找到使用者流程的詳細逐步解說：

* [系統提示您在 Android 裝置上安裝 Lookout for Work](http://docs.microsoft.com/intune/enduser/you-are-prompted-to-install-lookout-for-work-android)

* [您必須解決 Lookout for Work 在 Android 裝置上找到的威脅](http://docs.microsoft.com/intune/enduser/you-need-to-resolve-a-threat-found-by-lookout-for-work-android)

## <a name="next-steps"></a>後續步驟
* [啟用合規性政策中的裝置威脅保護規則](https://docs.microsoft.com/sccm/protect/deploy-use/enable-device-threat-protection-rule-compliance-policy)



<!--HONumber=Feb17_HO4-->



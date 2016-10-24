---
title: "部署 Lookout for Work 應用程式 | Microsoft Intune"
description: "設定及部署適用於 Android 的 Lookout for Work 應用程式。"
author: karthikaraman
manager: angrobe
ms.date: 10/12/2016
ms.topic: article
ms.prod: 
ms.service: 
ms.technology: 
ms.assetid: 524c4209-ad57-4d35-955e-a00d796bf858
ms.reviewer: sandera
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 4a69be67c3ef9f028c77c738de5f1fcbd59a8d33
ms.openlocfilehash: 2c626cb0a36c38c7b5deeca0ff1e902018540634


---

# 設定及部署 Lookout for Work 應用程式
本文說明如何為 Android 和 iOS 裝置，設定和部署 Lookout for Work 應用程式。

## Android (Google Play 商店應用程式)

* **步驟 1**：在 [Microsoft Intune 系統管理員主控台](https://manage.microsoft.com)中上傳 Lookout for Work Android 應用程式，如[在 Microsoft Intune 中新增行動裝置的應用程式](https://docs.microsoft.com/en-us/intune/deploy-use/add-apps-for-mobile-devices-in-microsoft-intune)主題中所述。
>[!NOTE]
> 請勿按下要求 Managed Browser 的方塊。

![顯示清單中 Lookout for Work 應用程式之 Intune 管理主控台應用程式頁面的螢幕擷取畫面](../media/mtp/lookout-app-listed-intune-console.png)

* **步驟 2**：將應用程式部署給使用者。 選取以上畫面中所示的 Lookout for Work 應用程式，然後選取 [管理部署]。

  您必須選取已在 Lookout 主控台中新增至 [Enrollment Management] (註冊管理) 選項的相同使用者。  如需將使用者群組新增至 Lookout MTP 的資訊，請參閱[設定訂用帳戶使用 Lookout 裝置威脅防護](set-up-your-subscription-with-lookout-mtp#configure-your-subscription-with-lookout-mtp)一節中的步驟 3。
>[!IMPORTANT]
> Intune 應用程式部署精靈無法察覺 Azure AD 使用者群組，而會改用 Intune 使用者群組，因此您必須依據 Lookout 主控台中已註冊的 Azure AD 使用者群組，來建立一個 Intune 使用者群組 (如[本主題](plan-your-user-and-device-groups.md)中所述)。

選擇 [必要安裝] 選項，要求必須在使用者裝置上安裝 Lookout 應用程式。


## iOS (Lookout 應用程式的企業簽章版本)

* **步驟 1**：確定您的裝置上已設定 **iOS 管理**。 如需如何設定裝置之 iOS 管理的指示，請參閱[設定 iOS 和 Mac 裝置管理](set-up-ios-and-mac-management-with-microsoft-intune.md)。

* **步驟 2**：**重新簽署** Lookout for Work iOS 應用程式。 Lookout 會將其 Lookout for Work iOS 應用程式散發到 iOS App Store 之外。 **散發應用程式之前**，您必須使用 iOS 企業開發人員憑證重新簽署應用程式。 如需重新簽署 Lookout for Work iOS 應用程式的詳細指示，請參閱 Lookout 網站上的 [Lookout for Work iOS App Re-Signing Process](https://personal.support.lookout.com/hc/en-us/articles/114094038714)。


* **步驟 3**：執行下列動作，啟用 iOS 使用者的 Azure Active Directory 驗證：
  1.  登入 [Azure Active Directory 管理入口網站](https://manage.windowsazure.com)，然後巡覽至應用程式頁面。
  2.  將 **Lookout for Work iOS 應用程式**新增為**原生用戶端應用程式**。
  ![顯示 [原生用戶端應用程式] 選項之 [新增應用程式] 對話方塊的螢幕擷取畫面](../media/mtp/aad-add-app.png)

  3. 將 **com.lookout.enterprise.yourcompanyname** 取代成您簽署 IPA 時所選取的客戶組合識別碼。
  4.  新增額外的重新導向 URI：**&lt;companyportal://code/>**，後面接著原始重新導向 URI 的 URL 編碼版本。
  5.  將**委派的權限**新增至您的應用程式。

  如需詳細資訊，請參閱[設定原生用戶端應用程式](https://azure.microsoft.com/en-us/documentation/articles/app-service-mobile-how-to-configure-active-directory-authentication/#optional-configure-a-native-client-application)。


* **步驟 4**：上傳重新簽署的.ipa 檔案，如[在 Microsoft Intune 中新增行動裝置的應用程式](https://docs.microsoft.com/en-us/intune/deploy-use/add-apps-for-mobile-devices-in-microsoft-intune)主題中所述。 將最低作業系統版本設定為 iOS 8.0 或更新版本。

  ![顯示應用程式清單中 Lookout for Work 應用程式之 Intune 系統管理員主控台應用程式頁面的螢幕擷取畫面](../media/mtp/ios-app-uploaded-intune.png)

* **步驟 5**：建立受管理的應用程式設定原則，如[在 Microsoft Intune 中使用行動應用程式設定原則設定 iOS 應用程式](https://docs.microsoft.com/en-us/intune/deploy-use/configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune)主題中所述。

  ![反白顯示 iOS 8.0 或更新版應用程式設定原則之 [建立新原則精靈] 的螢幕擷取畫面](../media/mtp/ios-app-config.png)

* **步驟 6**：**若要將應用程式部署給使用者**，請選取 Lookout for Work 應用程式，然後選取 [管理部署]。

  您必須選取已在 Lookout 主控台中新增至 [Enrollment Management] (註冊管理) 選項的相同使用者。  如需將使用者群組新增至 Lookout MTP 的資訊，請參閱[設定訂用帳戶使用 Lookout 裝置威脅防護](set-up-your-subscription-with-lookout-mtp#configure-your-subscription-with-lookout-mtp)一節中的步驟 3。
>[!IMPORTANT]
> Intune 應用程式部署精靈無法察覺 Azure AD 使用者群組，而會改用 Intune 使用者群組，因此您必須依據 Lookout 主控台中已註冊的 Azure AD 使用者群組，來建立一個 Intune 使用者群組 (如[本主題](plan-your-user-and-device-groups.md)中所述)。

選擇 [必要安裝] 選項，要求必須在使用者裝置上安裝 Lookout 應用程式。

## 在裝置上開啟已部署的應用程式時，會發生什麼事




當使用者在裝置上開啟 Lookout for Work 時，系統會提示他們啟動應用程式，並選擇 [使用 Azure Active Directory 登入] 選項。 您可以在下列主題中，找到使用者流程的詳細逐步解說：

* [系統提示在您的 Android 裝置上安裝 Lookout for Work](http://docs.microsoft.com/intune/enduser/you-are-prompted-to-install-lookout-for-work-android)

* [您必須解決 Lookout for Work 在 Android 裝置上找到的威脅](http://docs.microsoft.com/intune/enduser/you-need-to-resolve-a-threat-found-by-lookout-for-work-android)

## 後續步驟
* [啟用相容性原則中的裝置威脅保護規則](enable-device-threat-protection-rule-in-compliance-policy.md)



<!--HONumber=Oct16_HO2-->



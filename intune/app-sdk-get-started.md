---
title: "開始使用 Microsoft Intune App SDK"
description: "使用 Microsoft Intune 快速為行動應用程式啟用行動應用程式管理 (MAM)。"
keywords: 
author: mattbriggs
manager: angrobe
ms.author: mabriggs
ms.date: 12/15/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 38ebd3f5-cfcc-4204-8a75-6e2f162cd7c1
ms.reviewer: oydang
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 65350c9a247c5820cb2080d8230d308a37e98d7c
ms.sourcegitcommit: 42a0e4c83e33c1a25506ca75d673e861e9206945
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/26/2017
---
# <a name="get-started-with-the-microsoft-intune-app-sdk"></a>開始使用 Microsoft Intune App SDK

本指南可協助您使用 Microsoft Intune 快速啟用行動應用程式的應用程式保護原則。 若能先了解 [Intune App SDK 概觀](app-sdk.md)中說明的 Intune App SDK 優點，可能會對您很有幫助。

Intune App SDK 支援跨 iOS 和 Android 的類似案例，而且能為 IT 系統管理員建立跨平台的一致體驗。 但是，由於平台限制，因此針對特定功能的支援有些微差異。

## <a name="register-your-store-app-with-microsoft"></a>向 Microsoft 註冊您的市集應用程式

### <a name="if-your-app-is-internal-to-your-organization-and-will-not-be-publicly-available"></a>如果應用程式是無法公開的組織內部應用程式：

您就*不需要* 註冊應用程式。 若是內部企業營運應用程式，IT 系統管理員將會在內部部署這類應用程式。 Intune 可偵測是否已使用 SDK 建置應用程式，並允許 IT 系統管理員對其套用應用程式保護原則。 您可以跳到[啟用 iOS 或 Android 應用程式的應用程式保護原則](#enable-your-iOS-or-Android-app-for-app-protection-policy)這一節。

### <a name="if-your-app-will-be-released-to-a-public-app-store-like-the-apple-app-store-or-google-play"></a>如果您的應用程式將會發行到公開應用程式商店 (例如 Apple App Store 或 Google Play)：

您_**必須**_先向 Microsoft Intune 註冊應用程式，並同意註冊條款。 然後 IT 系統管理員就可以將應用程式保護原則套用至已啟用的應用程式，該應用程式將被列為 Intune 應用程式合作夥伴。

等到註冊已完成且 Microsoft Intune 小組確認之後，Intune 系統管理員就不會有將應用程式保護原則套用至應用程式深層連結的選項。 Microsoft 也會將您的應用程式加到其 [Microsoft Intune Partner 頁面](https://www.microsoft.com/cloud-platform/microsoft-intune-apps)。 應用程式的圖示將會在那裡顯示，以表示該應用程式支援 Intune 應用程式保護原則。

若要開始註冊程序，請填寫 [Microsoft Intune App Partner Questionnaire (Microsoft Intune 應用程式合作夥伴問卷)](https://forms.office.com/Pages/ResponsePage.aspx?id=v4j5cvGGr0GRqy180BHbR6oOVGFZ3pxJmwSN1N_eXwJUQUc5Mkw2UVU0VzI5WkhQOEYyMENWNDBWRS4u)。

我們將會使用問卷回應中列出的電子郵件地址與您連絡，並繼續註冊程序。 此外，如果有任何疑慮，我們也會使用您註冊的電子郵件地址與您連絡。

> [!NOTE]
> 問卷中及透過與 Microsoft Intune 小組的電子郵件通訊收集的所有資訊，皆會遵循 [Microsoft 隱私權聲明](https://www.microsoft.com/privacystatement/default.aspx)中的規定來處理。

**註冊程序的相關作業**：

1. 提交問卷之後，我們將會透過您註冊的電子郵件地址與您連絡，以確認我們成功收到郵件或要求其他資訊以完成註冊。

2. 在收齊您的所有必要資訊之後，我們即會傳送 Microsoft Intune 應用程式夥伴協議給您簽署。 本協議會說明相關條款，您的公司必須先接受這些條款，才能成為 Microsoft Intune 應用程式合作夥伴。

3. 當您的應用程式成功註冊 Microsoft Intune 服務，以及當 [Microsoft Intune 合作夥伴](https://www.microsoft.com/cloud-platform/microsoft-intune-apps)網站上將您的應用程式顯示為精選應用程式時，皆可獲得通知。

4. 最後，您應用程式的深層連結就會包含在下一次的每月 Intune 服務更新中。 例如，如果在 7 月完成註冊資訊，將於 8 月中支援深層連結。

如果未來您應用程式的深層連結有所變更，您將必須重新註冊應用程式。

> [!NOTE]
> 如果您使用新版 Intune App SDK 更新您的應用程式，請通知我們。



## <a name="download-the-sdk-files"></a>下載 SDK 檔案

適用於原生 iOS 和 Android 的 Intune App SDK 會裝載在 Microsoft GitHub 帳戶上。 這些公用存放庫具備分別適用於原生 iOS 和 Android 的 SDK 檔案︰

* [iOS 版 Intune App SDK](https://github.com/msintuneappsdk/ms-intune-app-sdk-ios)
* [Android 版 Intune App SDK](https://github.com/msintuneappsdk/ms-intune-app-sdk-android)

如果您的應用程式是 Xamarin 或 Cordova 應用程式，請使用這些 SDK 變異：

* [Intune App SDK Xamarin 元件](https://github.com/msintuneappsdk/intune-app-sdk-xamarin)
* [Intune App SDK Cordova 外掛程式](https://github.com/msintuneappsdk/cordova-plugin-ms-intune-mam)

建議您註冊一個 GitHub 帳戶，以用來從我們的存放庫執行分支作業及提取作業。 GitHub 可讓開發人員與我們的產品小組進行溝通、開啟問題並接收快速回應、檢視版本資訊，以及將意見提供給 Microsoft。 如有 Intune App SDK GitHub 問題，請連絡 msintuneappsdk@microsoft.com。





## <a name="enable-your-ios-or-android-app-for-app-protection-policy"></a>啟用 iOS 或 Android 應用程式的應用程式保護原則

您需要下列其中一個開發人員指南，協助您將 Intune App SDK 整合到應用程式：

* **[Intune App SDK for iOS 開發人員指南](app-sdk-ios.md)**：本文件將逐步引導您使用 Intune App SDK 啟用原生 iOS 應用程式。

* **[Intune App SDK for Android 開發人員指南](app-sdk-android.md)**：本文件將逐步引導您使用 Intune App SDK 來啟用原生 Android 應用程式。

* **[Intune App SDK Cordova 外掛程式指南](app-sdk-cordova.md)**︰本文件將協助您使用 Cordova for Intune 應用程式保護原則建置 iOS 和 Android 應用程式。

* **[Intune App SDK Xamarin 元件指南](app-sdk-xamarin.md)**︰本文件將協助您使用 Cordova for Intune 應用程式保護原則建置 iOS 和 Android 應用程式。



## <a name="enable-your-ios-or-android-app-for-app-based-conditional-access"></a>針對應用程式型條件式存取啟用 iOS 或 Android 應用程式
 
 除了針對應用程式保護原則啟用您的應用程式之外，您的應用程式也需要符合下列條件才能適當地搭配 Azure ActiveDirectory (AAD) 應用程式型條件式存取運作：
 
 * 應用程式是使用 [Azure Active Directory 驗證程式庫](https://docs.microsoft.com/en-us/azure/active-directory/develop/active-directory-authentication-libraries)所建置並針對 AAD 訊息代理程式驗證啟用。
 
 * 您應用程式的 [AAD 用戶端識別碼](https://docs.microsoft.com/en-us/azure/app-service/app-service-mobile-how-to-configure-active-directory-authentication#optional-configure-a-native-client-application)在 iOS 與 Android 平台上都必須是唯一的。
 
 
 

## <a name="configure-telemetry-for-your-app"></a>設定應用程式的遙測

Microsoft Intune 會收集應用程式使用量統計資料的資料。

* **iOS 的 Intune App SDK**：SDK 預設會記錄使用事件的相關 SDK 遙測資料。 這些資料會傳送到 Microsoft Intune。

    * 如果您選擇不要將 SDK 遙測資料從應用程式傳送至 Microsoft Intune，則必須停用遙測傳輸，方法是在 IntuneMAMSettings 字典中將 `MAMTelemetryDisabled` 屬性設定為 "YES"。


* **適用於 Android 的 Intune App SDK**：不會透過 SDK 記錄遙測資料。

## <a name="next-steps-after-integration"></a>整合後的後續步驟

### <a name="test-your-app"></a>測試應用程式
在您完成整合 iOS 或 Android 應用程式與 Intune App SDK 的必要步驟之後，需要確定使用者和 IT 系統管理員的所有應用程式保護原則皆已啟用且正常運作。若要測試整合式應用程式，您需要下列項目：

* **Microsoft Intune 測試帳戶**：若要對啟用 Intune 的應用程式測試 Intune 應用程式保護功能，您必須具備 Microsoft Intune 帳戶。

    * 如果您是為 iOS 或 Android 市集應用程式啟用 Intune 應用程式保護原則的 ISV，完成註冊步驟中所述的 Microsoft Intune 註冊後，即會收到促銷代碼。 促銷代碼將可讓您註冊 Microsoft Intune 試用版，以獲得 1 年的延長使用時間。

    * 如果您開發的是不會傳送至商店的企業營運應用程式，您應該透過組織來存取 Microsoft Intune。 您也可以在 [Microsoft Intune](https://portal.office.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0) 中註冊以獲得 1 個月免費試用版。

* **Intune 應用程式保護原則**：若要對應用程式測試所有 Intune 應用程式保護原則，您應該知道每個原則設定的預期行為。 請參閱 [iOS 應用程式保護原則](/intune-classic/deploy-use/ios-mam-policy-settings)和 [Android 應用程式保護原則](/intune-classic/deploy-use/android-mam-policy-settings)的描述。

* **疑難排解**︰如果您在手動測試應用程式的使用者體驗時遇到任何問題，請參閱[針對 MAM 進行疑難排解](/intune-classic/troubleshoot/troubleshoot-mam)。 本文提供啟用 Intune 之應用程式中可能會遇到的常見問題、對話方塊和錯誤訊息的協助。 

### <a name="badge-your-app-optional"></a>為應用程式加上徽章 (選擇性)

驗證 Intune 應用程式保護原則在應用程式中運作之後，您可以使用 Intune 應用程式保護標誌為應用程式圖示加上徽章。

這個徽章對 IT 系統管理員、終端使用者和潛在 Intune 客戶表示您的應用程式使用 Intune 應用程式保護原則。 它鼓勵 Intune 客戶使用和採用您的應用程式。

徽章是一個公事包圖示，可以在下面的範例中看到︰

![徽章範例 1](./media/badge-example-1.png) ![徽章範例 2](./media/badge-example-2.png)

**為應用程式加上徽章的必要步驟**：

* 可讀取 **.eps** 檔案的映像操作應用程式，或可讀取 **.ai** 檔案的 Adobe 應用程式。

* 您可以在 Microsoft Intune GitHub 找到 [Intune app badge assets and guidelines](https://github.com/msintuneappsdk/intune-app-partner-badge) (Intune 應用程式徽章資產和指導方針)。

---
title: "開始使用 Microsoft Intune App SDK | Microsoft Intune"
description: 
keywords: 
author: Msmbaldwin
manager: jeffgilb
ms.date: 09/08/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 38ebd3f5-cfcc-4204-8a75-6e2f162cd7c1
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ed1008c786285821c608a8404805c6615c60507f
ms.openlocfilehash: c80868fdee79df62aae0aa64e378be5dcc9664ae


---

# 開始使用 Microsoft Intune App SDK

本入門指南可協助您使用 Microsoft Intune 快速啟用行動應用程式的行動應用程式管理功能。 若能先了解 [Intune App SDK 概觀](intune-app-sdk.md)中所列舉的 Intune App SDK 優點，可能會對您很有幫助。

本指南的主要步驟，可逐步引導您使用 Microsoft Intune 啟用應用程式的行動應用程式管理功能。 Intune App SDK 支援跨平台的類似案例，而且能為 IT 系統管理員建立跨平台的一致體驗。 不過，由於平台限制，因此針對特定功能的支援有些微差異。

# 快速入門

## 向 Microsoft 註冊您的市集應用程式

**如果應用程式是不會在公開應用程式商店中提供的公司內部應用程式**：

您就**不需要** 註冊應用程式。 若是內部企業營運應用程式，IT 系統管理員將會在內部部署這類應用程式。 Intune 可偵測是否已使用 SDK 建置應用程式，並允許 IT 系統管理員對其套用 MAM 原則設定。 您可以跳到[使用 SDK 啟用 iOS 或 Android 行動應用程式的 MAM](#enable-your-ios-or-android-mobile-app-for-mam-with-the-sdk) 這一節。

**如果您的應用程式將會發行到公開應用程式商店 (例如 Apple App Store 或 Google Play)**： 

您**必須**先向 Microsoft Intune 註冊應用程式，並同意註冊條款。 註冊之後，IT 系統管理員可以將 Intune MAM 原則設定套用至已啟用的應用程式，這將會列為 Intune 應用程式合作夥伴。 等到註冊已完成且 Microsoft Intune 小組確認之後，Intune 系統管理員就不會有將 MAM 原則套用至應用程式深層連結的選項。 Microsoft 也會將應用程式新增至其 [Microsoft Intune 合作夥伴](https://www.microsoft.com/en-us/cloud-platform/microsoft-intune-apps)頁面，其中將會顯示應用程式圖示，以顯示此頁面支援 Microsoft Intune MAM 原則。

若要開始註冊程序，請填寫 **[Microsoft Intune App Partner Questionnaire](https://forms.office.com/Pages/ResponsePage.aspx?id=v4j5cvGGr0GRqy180BHbR6oOVGFZ3pxJmwSN1N_eXwJUQUc5Mkw2UVU0VzI5WkhQOEYyMENWNDBWRS4u)**(Microsoft Intune 應用程式合作夥伴問卷)。 

Microsoft 會使用問卷回應中列出的電子郵件地址進行連絡，並繼續註冊程序。 此外，如果有任何疑慮，我們也會使用您註冊的電子郵件地址與您連絡。

> [!NOTE]
> 上述表單中收集的所有資訊，以及與 Microsoft Intune 小組的電子郵件通訊，皆會遵循 [Microsoft 隱私權聲明](https://www.microsoft.com/en-us/privacystatement/default.aspx)中的規定來處理。

**註冊程序的相關作業**： 

1. 提交問卷之後，Microsoft 會透過您註冊的電子郵件地址連絡您，以確認成功回條或要求其他資訊以完成註冊。 
2. 在收齊您的所有必要資訊之後，我們即會傳送 Microsoft Intune 應用程式夥伴協議給您簽署。 本協議說明相關條款，您的公司必須先接受這些條款，才能成為 Microsoft Intune 應用程式合作夥伴。 
3. 當您的應用程式成功註冊 Microsoft Intune 服務，以及當 [Microsoft Intune 合作夥伴](https://www.microsoft.com/en-us/cloud-platform/microsoft-intune-apps)網站上將您的應用程式顯示為精選應用程式時，皆可獲得通知。 
4. 最後，您的應用程式深層連結就會包含在下一次的每月 Intune 服務更新中。 例如，如果在 7 月完成註冊資訊，將於 8 月中支援應用程式深層連結。 

如果未來您的市集應用程式深層連結有所變更，則必須重新註冊應用程式。 此外，如果您使用新版 Intune App SDK 更新您的應用程式，也務必通知我們。



## 下載 SDK 檔案

適用於原生 iOS 和 Android 的 Intune App SDK 會裝載在 Microsoft GitHub 帳戶上。 下面的公用存放庫分別包含適用於 iOS 和 Android 的 SDK 檔案︰

* [適用於 iOS 的 Intune App SDK](https://github.com/msintuneappsdk/ms-intune-app-sdk-ios)
* [適用於 Android 的 Intune App SDK](https://github.com/msintuneappsdk/ms-intune-app-sdk-android)

**如果您的應用程式是 Xamarin 或 Cordova 應用程式，請使用下列開發人員工具**：

* [Intune App SDK Xamarin 元件](https://github.com/msintuneappsdk/intune-app-sdk-xamarin)
* [Intune App SDK Cordova 外掛程式](https://github.com/msintuneappsdk/cordova-plugin-ms-intune-mam)

建議註冊您可以用來從存放庫分叉和提取的 GitHub 帳戶。 GitHub 可讓開發人員與我們的產品小組進行溝通、開啟問題並接收快速回應、檢視版本資訊，以及將意見提供給 Microsoft。 如需 GitHub 帳戶和存放庫的問題，請連絡 msintuneappsdk@microsoft.com。





## 使用 SDK 啟用 iOS 或 Android 行動應用程式的 MAM

若要將 Intune App SDK 整合到原生 iOS 應用程式，您需要下列項目︰ 

* **[Intune App SDK for iOS 開發人員指南](intune-app-sdk-ios.md)**：本文件將逐步引導您使用 Intune App SDK 來啟用 iOS 行動應用程式。 


若要將 Intune App SDK 整合到原生 Android 應用程式，您需要下列項目︰

* **[Intune App SDK for Android 開發人員指南](intune-app-sdk-android.md)**：本文件將逐步引導您使用 Intune App SDK 啟用 Android 行動應用程式。 

Intune App SDK Xamarin 元件和 Intune App SDK Cordova 外掛程式的相關文件，位於其各自的 GitHub 存放庫中。 


## 設定應用程式的遙測

Microsoft Intune 會收集應用程式使用量統計資料的資料。

* **iOS 的 Intune App SDK**：SDK 預設會記錄使用事件的相關 SDK 遙測資料。 這些資料會傳送到 Microsoft Intune。

    * 如果您選擇不要將 SDK 遙測資料從應用程式傳送至 Microsoft Intune，則必須停用遙測傳輸，方法是在 IntuneMAMSettings 字典中將 `MAMTelemetryDisabled` 屬性設定為 "YES"。

* **適用於 Android 的 Intune App SDK**：不會透過 SDK 記錄遙測資料。

## 使用 Microsoft Intune 測試啟用 MAM 的應用程式

當您完成整合 iOS 或 Android 應用程式與 Intune App SDK 的必要步驟之後，需要確定使用者和 IT 系統管理員的所有應用程式管理原則皆已啟用且正常運作。 若要測試整合式應用程式，您需要下列項目：

<!--TODO-->

* **使用 Microsoft Intune 測試啟用 MAM 的應用程式**：本文件將逐步引導您使用 Microsoft Intune 測試啟用 MAM 的 iOS 或 Android 應用程式。 您可以在 SDK 的 GitHub 存放庫中找到這份文件。

* **Microsoft Intune 帳戶**：若要使用 Microsoft Intune 測試啟用 MAM 的應用程式，您必須具備 Microsoft Intune 帳戶。 
    * 如果您是啟用 Intune MAM 的 iOS 或 Android 市集應用程式的 ISV，完成註冊步驟中所述的 Microsoft Intune 註冊後，即會收到促銷代碼。 促銷代碼可讓您註冊 Microsoft Intune 試用版，以延續使用一年。 
    * 如果您開發的是不會傳送至商店的商務應用程式，則應該透過組織來存取 Microsoft intune。 您也可以註冊 [Microsoft Intune](https://portal.office.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0) 以獲得 1 個月免費試用版。




<!--HONumber=Oct16_HO3-->



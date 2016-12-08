---
title: "新功能 | Microsoft Intune"
description: "了解本月 Microsoft Intune 版本的新功能，以及過去的版本"
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 11/30/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: fab51ee0-638d-4dd4-8d8f-1f263bc11e5c
ms.reviewer: priyar
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 8ef3b7e4eec5a520c93fb3f70c8e5b6ee7d2c3aa
ms.openlocfilehash: e0b0c7eb3ddc07f05fc0c2e4caa6726ed052c9d8


---
# <a name="whats-new-in-microsoft-intune---november-2016"></a>Microsoft Intune 的新功能 - 2016 年 11 月
了解此 Microsoft Intune 版本中的新功能。 您也可以了解即將推出且您應該加以規劃的變更，以及過去版本的相關資訊。

> [!Note]
> 混合式客戶部署於未來將會支援這些功能 (具備 Intune 的 Configuration Manager)。 如需新混合式功能的詳細資訊，請查看我們的 [Hybrid What’s New](https://docs.microsoft.com/en-us/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management) (混合式新功能) 頁面。

## <a name="new-capabilities"></a>新功能

<!--### View App States for All Platforms in Real Time
App installation status is now shown in real-time in the console. When you previously deployed an app, you had to wait for a targeted device to report back before the app install status was displayed in the Intune console.

### Streamline iOS App Management for your End Users
Intune can now automatically take over management of the previously installed app and no end user action is required.

Previously, if the end user of an enrolled iOS device installed an app from the App Store before you deployed that same app with a deployment action of __Available__, then the end user had to:

1. Open the __Company Portal__.
2. Select the app.
3. Tap __Install__ to enable Intune to take over management of the app.-->

__可供 Windows 10 裝置使用的新 Microsoft Intune 公司入口網站 __ Microsoft 已經發行 [Windows 10 裝置適用的新 Microsoft Intune 公司入口網站應用程式](https://www.microsoft.com/store/apps/9wzdncrfj3pz)。 利用新的 Windows 10 通用格式的此應用程式，會為使用者提供應用程式內更新的使用者體驗，以及所有 Windows 10 裝置、電腦和類似行動裝置的相同體驗，同時啟用他們目前仍在使用的相同功能。

新的應用程式也可讓使用者運用其他平台功能，例如單一登入 (SSO) 和 Windows 10 裝置上的憑證型驗證。 應用程式會以現有的 Windows 8.1 公司入口網站升級，以及從 Windows 市集安裝的 Windows Phone 8.1 公司入口網站的方式提供。 如需詳細資訊，請前往 [aka.ms/intunecp_universalapp](http://aka.ms/intunecp_universalapp)。

<!--### Support for Windows Store for Business Apps Being Deployed as Available
You can now deploy apps you synchronized from the Windows Store for Business (WSfB) with a deployment action of __Available__ or __Required__. After syncing WSfB apps into Intune, administrators will be able to target those apps as available installs to groups of users. End users will see the deployed WSfB apps as available for install in the Universal Company Portal, where they can choose whether they would like to acquire the apps.

### Conditional Access for MAM with SharePoint Online

You can block apps that are not supported by Intune mobile app management (MAM) policies from accessing SharePoint online.  You can get started in Intune mobile app management via the Azure portal. Look for the  Conditional Access section in the “Settings” blade which now includes the option for SharePoint online.-->

> [!IMPORTANT]

> __Intune 和 Android for Work 的更新__

> 雖然您可以用__必要__動作部署 Android for Work 應用程式，但如果您已將 Intune 群組移轉至新的 Azure AD 群組，就只能將應用程式部署為__可用__。

### <a name="intune-app-sdk-for-cordova-plugin-now-supports-mam-without-enrollment"></a>Intune App SDK for Cordova 外掛程式現在支援 MAM 而不必註冊
應用程式開發人員可以現在使用 Intune App SDK for Cordova 外掛程式啟用 MAM 功能，而不必在其 Android 和 iOS 的 Cordova 應用程式進行裝置註冊。 您可以在[這裡](https://github.com/msintuneappsdk/cordova-plugin-ms-intune-mam)找到 Intune App SDK for Cordova 外掛程式。

### <a name="intune-app-sdk-xamarin-component-now-supports-mam-without-enrollment"></a>Intune App SDK Xamarin 元件現在支援 MAM 而不必註冊
應用程式開發人員可以現在使用 Intune App SDK Xamarin 元件啟用 MAM 功能，而不必在其 Android 和 iOS 的 Xamarin 應用程式進行裝置註冊。 您可以在[這裡](https://github.com/msintuneappsdk/intune-app-sdk-xamarin)找到 Intune App SDK Xamarin 元件。

## <a name="notices"></a>通知

### <a name="symantec-signing-certificate-no-longer-requires-signed-windows-phone-8-company-portal-for-upload"></a>Symantec 簽署憑證不再需要已簽署的 Windows Phone 8 公司入口網站以進行上傳
上傳 Symantec 簽署憑證不再需要已簽署的 Windows Phone 8 公司入口網站應用程式。 可以獨立上傳憑證。

## <a name="deprecations"></a>棄用功能

### <a name="support-for-the-windows-phone-8-company-portal"></a>Windows Phone 8 公司入口網站的支援
對 Windows Phone 8 公司入口網站的支援現在將被取代。 對於 Windows Phone 8 和 WinRT 平台的支援已在 2016 年 10 月被取代。 對於 Windows 8 公司入口網站的支援也已在 2016 年 10 月被取代。


### <a name="see-also"></a>請參閱
* [Microsoft Intune 部落格](http://go.microsoft.com/fwlink/?LinkID=273882)
* [雲端平台藍圖](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)
* [舊版的 Intune](whats-new-archive.md)



<!--HONumber=Dec16_HO1-->



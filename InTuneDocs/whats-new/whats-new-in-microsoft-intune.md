---
title: "新功能 | Microsoft Intune"
description: "了解本月 Microsoft Intune 版本的新功能，以及過去的版本"
keywords: 
author: barlanmsft
manager: angrobe
ms.date: 10/13/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: fab51ee0-638d-4dd4-8d8f-1f263bc11e5c
ms.reviewer: mamoriss
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 503719953031bf5079b2bf5bc84a0497d708f79a
ms.openlocfilehash: 730809e0841a248b90f5fe157f2c6338bfd32b2d


---
# Microsoft Intune 的新功能 -- 2016 年 10 月
了解此 Microsoft Intune 版本中的新功能。 您也可以了解即將推出且您應該加以規劃的變更，以及過去版本的相關資訊。

混合式客戶部署於未來將會支援這些功能 (具備 Intune 的 Configuration Manager)。 如需新混合式功能的詳細資訊，請查看我們的 [Hybrid What’s New](https://technet.microsoft.com/library/mt718155.aspx) (混合式新功能) 頁面。
<!---@Barry, the above blurb stays in each version, but make sure Tyler signs off each time. Also, remember to set the ms.date in the metadata to the sprint release. --->

## 新功能

### 行動應用程式管理的條件式存取
您將可以限制 Exchange Online 的存取，讓存取只能來自支援 Intune 行動應用程式管理原則的應用程式，例如 Outlook。 [這項新功能](/intune/deploy-use/allow-policy-managed-apps-access-to-o365)可完美對應 Intune 行動應用程式管理 (MAM) 原則，讓您可以封鎖存取內建電子郵件用戶端或並未使用 Intune MAM 原則設定的其他應用程式。 這可確保您的使用者是利用使用 Intune MAM 保護的 App 來存取組織的資料。 您可以透過 Azure 入口網站，從 Intune 行動應用程式管理開始。 尋找 [設定] 刀鋒視窗中新的 [條件式存取] 區段。

### Windows 電腦的條件式存取
您現在可以透過 Intune 管理主控台建立條件式存取原則，來封鎖 Windows 電腦存取 [Exchange Online](/intune/deploy-use/restrict-access-to-exchange-online-with-microsoft-intune) 和 [SharePoint Online](/intune/deploy-use/restrict-access-to-sharepoint-online-with-microsoft-intune)。 您也可以建立條件式存取原則來封鎖存取 Office 桌面及通用應用程式。

### Android for Work 支援
Intune 目前是 Android for Work 方案的一部分。 我們將從本月開始推出 intune 的 Android for Work 功能支援。
[請參閱 Microsoft 有關 Android for Work 之 Intune 支援的公告](https://blogs.technet.microsoft.com/enterprisemobility/2016/09/12/microsoft-intune-support-for-android-for-work/)。

下列 Intune 主題是全新主題，或更新的 Android for Work 資訊：

IT 專業人員：
- [設定 Android for Work](/intune/deploy-use/set-up-android-for-work)
<!--- [Nathan Bigman's resource access topics]()-->
- [使用 Intune 限制 Exchange Online 和新版 Exchange Online Dedicated 的電子郵件存取](/intune/deploy-use/restrict-access-to-exchange-online-with-microsoft-intune)
- [使用 Intune 限制 Exchange 內部部署和舊版 Exchange Online Dedicated 的電子郵件存取](/intune/deploy-use/restrict-access-to-exchange-onpremises-with-microsoft-intune)
- [Android for Work 相容性原則設定](/intune/deploy-use/afw-compliance-policy-settings-in-microsoft-intune)
- [如何部署 Android for Work 應用程式](/intune/deploy-use/android-for-work-apps)
- [使用行動應用程式設定原則設定 Android for Work 應用程式](/intune/deploy-use/afw-app-configuration-policy)
- [Android for Work 原則設定](/intune/deploy-use/android-for-work-policy-settings-in-microsoft-intune)

使用者：
- [當您建立工作設定檔時，會發生什麼事](/intune/enduser/what-happens-when-you-create-a-work-profile-android)
- [建立工作設定檔並在 Intune 註冊您的裝置](/intune/enduser/create-a-work-profile-and-enroll-your-device-in-intune-android)

### Lookout 整合以保護 iOS 裝置
在十月，Microsoft 要整合 Lookout 的行動威脅保護解決方案，藉由偵測裝置上的惡意程式碼、高風險 App 等等，以保護 iOS 行動裝置。 Lookout 的解決方案有助於您判斷威脅層級 (可設定)。 您可以根據 Lookout 的風險評估，在 Intune 中建立相容性原則規則，來決定裝置相容性。 您可以利用條件式存取原則，根據裝置相容性狀態，允許或封鎖公司資源的存取。

系統將會提示不相容 iOS 裝置的使用者進行註冊，並且要求使用者在其裝置上安裝 Lookout for Work 應用程式、啟動應用程式，並修復 Lookout for Work 應用程式中所報告的威脅，才能存取公司資料。 了解如何[設定及部署 Lookout for Work 應用程式](/intune/deploy-use/configure-and-deploy-lookout-for-work-apps)。
<!--TFS 1319493-->

<!--### New Microsoft Intune Company Portal available for Windows 10 devices
Microsoft is releasing a new [Microsoft Intune Company Portal for Windows 10 devices](https://go.microsoft.com/fwlink/?linkid=830663). This app, which leverages the new Windows 10 Universal format, will provide the user with an updated user experience within the app and identical experiences across all Windows 10 devices, PC and Mobile alike, while still enabling all the same functionality that they are using today.

The new app will also allow users to leverage additional platform features like single sign-on (SSO) and certificate-based authentication on Windows 10 devices. The app will be made available as an upgrade to the existing Windows 8.1 Company Portal and Windows Phone 8.1 Company Portal installs from the Windows Store.-->

### Intune App Wrapping Tool for Android
您可以使用 Intune App Wrapping Tool，讓應用程式使用 Intune 行動應用程式管理 (MAM) 原則。 現在不需要註冊裝置，即可支援 Intune MAM 原則。

### 從使用 MAM 原則管理的應用程式管理列印
您現在可以防止有 MAM 原則的應用程式列印公司資料。 此設定可於 [Azure 入口網站](/Intune/deploy-use/create-and-deploy-mobile-app-management-policies-with-microsoft-intune)取得，而且 [iOS](/Intune/deploy-use/ios-mam-policy-settings) 和 [Android](/Intune/deploy-use/android-mam-policy-settings) 裝置都支援。
<!--TFS 1014328-->

## 通知

### Intune 的 Android Samsung KNOX 相容性
某些 Samsung Galaxy Ace 手機型號，Intune 無法作為 Samsung KNOX 裝置管理。 當您向 Intune 註冊這些裝置時，它們會作為標準的 Android 裝置管理。

受影響的型號︰

* SM-G313HU
* SM-G313HY
* SM-G313M
* SM-G313MY
* SM-G313U

您和您的使用者不需要採取任何進一步的動作。 如需詳細資訊，請瀏覽 [Samsung KNOX](https://www.samsungknox.com) 網站。

### Windows 8 的公司入口網站應用程式已淘汰，對 Windows Phone 8 和 Windows RT 平台的支援也逐步淘汰。
Microsoft Intune 自 2016 年 10 月起會取代 Windows 8 公司入口網站應用程式的支援。 Microsoft Intune 也會取代 Windows Phone 8 和 Windows RT 平台的支援。 因此，您將無法註冊或更新任何 Windows Phone 8 或 Windows RT 裝置。

您可以繼續管理已註冊的 Windows Phone 8、Windows RT 和 Windows 8 裝置。 將 Windows Phone 8 和 Windows 8 裝置更新為 Windows 8.1 和 Windows Phone 8.1，並使用對應的 Windows 8.1 和 Windows Phone 8.1 公司入口網站應用程式繼續將應用程式發佈至這些裝置，而不受中斷。

我們從 2016 年 11 月開始淘汰對 Windows Phone 8 公司入口網站的支援。
<!--TFS 1255391-->

## 未來動態

### Windows 10 裝置提供新的 Microsoft Intune 公司入口網站
Microsoft 即將發行新的 Windows 10 裝置 Microsoft Intune 公司入口網站。 利用新的 Windows 10 通用格式的此應用程式，會為使用者提供應用程式內更新的使用者體驗，以及所有 Windows 10 裝置、電腦和類似行動裝置的相同體驗，同時啟用他們目前仍在使用的相同功能。

新的應用程式也可讓使用者運用其他平台功能，例如單一登入 (SSO) 和 Windows 10 裝置上的憑證型驗證。 應用程式會以現有的 Windows 8.1 公司入口網站升級，以及從 Windows 市集安裝的 Windows Phone 8.1 公司入口網站的方式提供。 如需詳細資訊，請前往 [aka.ms/intunecp_universalapp](http://aka.ms/intunecp_universalapp)。
<!--TFS 1016502-->

### 請參閱
* [Microsoft Intune 部落格](http://go.microsoft.com/fwlink/?LinkID=273882)
* [雲端平台藍圖](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)
* [舊版 Intune](previous-intune-releases.md)



<!--HONumber=Oct16_HO2-->



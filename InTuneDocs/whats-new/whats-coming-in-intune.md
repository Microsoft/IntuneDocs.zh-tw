---
title: "舊版 | Microsoft Intune"
description: 
keywords: 
author: barlanmsft
manager: angrobe
ms.date: 10/05/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: mamoriss
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: a5c4b0f15456a9f24c95954d669a17c63f96a459
ms.openlocfilehash: 273016d4fe114bbe60e9cebc06e89584c8f91f0b


---

# Microsoft Intune 的未來動態 - 10 月
**舊版**提供 Microsoft Intune 即將發行版本要推出的功能清單。 此資訊以非常有限的基礎在 NDA 下提供，並可能有所變更。 這裡列出的一些功能可能有截止日期，而且可能會延遲到未來的版本。 其他功能正在實驗 (測試) 中進行測試，以確保它們可供客戶使用。 如果你們有任何問題或疑慮，請洽詢 Intune/PM 人員。

此頁面會定期更新。 回頭檢查新的未來動態更新。

下列變更正在 Intune 的開發過程中。 混合式客戶部署於未來將會支援這些功能 (具備 Intune 的 Configuration Manager)。 如需新混合式功能的詳細資訊，請查看我們的 [Hybrid What’s New](https://technet.microsoft.com/en-US/library/mt718155(TechNet.10).aspx) (混合式新功能) 頁面。

### 從使用 MAM 原則管理的應用程式管理列印
您現在可以防止有 MAM 原則的應用程式列印公司資料。 此設定可於 [Azure 入口網站](..deployuse/create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md)取得，而且 [iOS](..deployuse/ios-mam-policy-settings) 和 [Android](..deployuse/android-mam-policy-settings) 裝置都支援。
<!--TFS 1014328-->

### Windows 10 裝置提供新的 Microsoft Intune 公司入口網站
Microsoft 即將發行新的 Windows 10 裝置 Microsoft Intune 公司入口網站。 利用新的 Windows 10 通用格式的此應用程式，會為使用者提供應用程式內更新的使用者體驗，以及所有 Windows 10 裝置、電腦和類似行動裝置的相同體驗，同時啟用他們目前仍在使用的相同功能。

新的應用程式也可讓使用者運用其他平台功能，例如單一登入 (SSO) 和 Windows 10 裝置上的憑證型驗證。 應用程式會以現有的 Windows 8.1 公司入口網站升級，以及從 Windows 市集安裝的 Windows Phone 8.1 公司入口網站的方式提供。
<!--TFS 1016502-->

### Android for Work 支援

Intune 目前是 [Android for Work 方案](https://enterprise.google.com/android/partners/)的一部分。 我們將從本月開始推出 intune 的 Android for Work 功能支援。

[請參閱 Microsoft 有關 Android for Work 之 Intune 支援的公告](https://blogs.technet.microsoft.com/enterprisemobility/2016/09/12/microsoft-intune-support-for-android-for-work/)。

<!---This month, some newly provisioned Intune tenants will start seeing the Android for Work features. We will announce later when existing tenants will begin to see this feature.--->
<!--TFS 1043303-->

### Intune 的 Android Samsung KNOX 相容性

某些 Samsung Galaxy Ace 手機型號，Intune 無法作為 Samsung KNOX 裝置管理。 當您向 Intune 註冊這些裝置時，它們會作為標準的 Android 裝置管理。
受影響的型號︰

* SM-G313HU
* SM-G313HY
* SM-G313M
* SM-G313MY
* SM-G313U

您和您的使用者不需要採取任何進一步的動作。
如需詳細資訊，請瀏覽 [Samsung KNOX](https://www.samsungknox.com) 網站。

<!--TFS 1173566 iX blurb provided by Barry; requires PM signoff

### Multi-factor authentication for Android and iOS enrollment

In addition to Windows 8.1 and later, administrators can now enable multi-factor authentication for Android and iOS devices in the Microsoft Intune Enrollment application. -->    

### Windows 8 的公司入口網站應用程式已淘汰，對 Windows Phone 8 和 Windows RT 平台的支援也逐步淘汰。
Microsoft Intune 自 2016 年 10 月起會取代 Windows 8 公司入口網站應用程式的支援。 Microsoft Intune 也會取代 Windows Phone 8 和 Windows RT 平台的支援。 因此，您將無法註冊或更新任何 Windows Phone 8 或 Windows RT 裝置。

您可以繼續管理已註冊的 Windows Phone 8、Windows RT 和 Windows 8 裝置。 將 Windows Phone 8 和 Windows 8 裝置更新為 Windows 8.1 和 Windows Phone 8.1，並使用對應的 Windows 8.1 和 Windows Phone 8.1 公司入口網站應用程式繼續將應用程式發佈至這些裝置，而不受中斷。

我們從 2016 年 11 月開始淘汰對 Windows Phone 8 公司入口網站的支援。
<!--TFS 1255391-->

### 行動應用程式管理的條件式存取
您現在可以建立條件式存取原則，封鎖不受管理的行動應用程式存取 [Exchange Online](..deployuse/restrict-access-to-exchange-online-with-microsoft-intune.md) 和 [SharePoint Online](..deployuse/restrict-access-to-sharepoint-online-with-microsoft-intune.md)。 您可以使用 Intune App SDK 封鎖內建的郵件用戶端與非 MAM 啟用的應用程式。  這可以透過建立條件式存取原則，以及指定使用 Azure 入口網站存取 Exchange Online 和 SharePoint Online 的應用程式來完成。
<!--TFS 1317673-->

<!--TFS 1318014; awaiting approval in notes as to whether to proceed

### "Default" policy is deprecated

To minimize unintentionally assigned profiles, Intune is removing support for the "default" Corporate Device Enrollment profile for Apple Device Enrollment Program (DEP) device serial numbers in the new Azure console. Serial numbers synchronized from an Apple DEP account will initially have no Corporate Device Enrollment profile assigned.  A profile must be assigned manually after synchronization. This change will apply to the new console only. Until the existing Admin console is retired, no change will take place.
-->

<!--TFS 1318023; awaiting approval in notes as to whether to proceed

### Deprecation of row-by-row iOS Details review for iOS device CSV uploads

In order to streamline uploading IMEI numbers for Corporate devices and Apple serial numbers for Configurator enrollment, Intune is removing the row by row review of hardware identifiers already found in the system. This review allows the IT Pro to accept associated Details from the CSV to overwrite the existing details for a hardware identifier already in the system. The review will be replaced by a single option to automatically overwrite Details for all hardware identifiers or ignore new details for existing identifiers. This change will apply to the new console only. Until the existing Admin console is retired, no change will take place.
-->

### Lookout 整合以保護 iOS 裝置
在十月，Microsoft 要整合 Lookout 的行動威脅保護解決方案，藉由偵測裝置上的惡意程式碼、高風險 App 等等，以保護 iOS 行動裝置。 Lookout 的解決方案有助於您判斷威脅層級 (可設定)。 您可以根據 Lookout 的風險評估，在 Intune 中建立相容性原則規則，來決定裝置相容性。 您可以利用條件式存取原則，根據裝置相容性狀態，允許或封鎖公司資源的存取。

系統將會提示不相容 iOS 裝置的使用者進行註冊，並且要求使用者在其裝置上安裝 Lookout for Work 應用程式、啟動應用程式，並修復 Lookout for Work 應用程式中所報告的威脅，才能存取公司資料。
<!--TFS 1319493-->

### Intune App SDK 和 App Wrapping Tool for Android
您可以使用 Intune App Wrapping Tool 或 Intune App SDK，讓應用程式使用 Intune 行動應用程式管理 (MAM) 原則。 App Wrapping Tool 和 SDK 的新更新包括：

* 支援 Android N
* 支援 Intune MAM 原則，不需要註冊裝置
* 支援 Xamarin 型的 Android 應用程式

您可以在這裡的 Android App Wrapping Tool 公用預覽中，測試不註冊裝置的 MAM 以及 Xamarin 支援：[https://github.com/msintuneappsdk/intune-app-wrapper-android-preview](https://github.com/msintuneappsdk/intune-app-wrapper-android-preview)。
<!--TFS 1319511; please create new TFS entry for WN text associated with this TFS item-->

<!--TFS 1319613; no iX review on PM text blurb

### Private preview customers using MAM Conditional Access will have their policies reset

Due to changes in the policy structure for Conditional Access for Mobile App Management, any existing policies that were set by customers through the private preview will be removed. Customers will need to set new policies once the change is made. The timing will coincide with the October service update.
-->

### 請參閱
如需近期發展的詳細資料，請參閱 [Microsoft Intune 的新功能](whats-new-in-microsoft-intune.md)。



<!--HONumber=Oct16_HO1-->



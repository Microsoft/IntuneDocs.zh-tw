---
title: 將 Mobile Threat Defense 應用程式新增至尚未註冊的裝置
titleSuffix: Microsoft Intune
description: 由裝置使用者將 Mobile Threat Defense 應用程式新增至尚未註冊的裝置。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: f8dd7127594a0e23c85b9f8141ce6d398d9a447a
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72794455"
---
# <a name="add-mobile-threat-defense-apps-to-unenrolled-devices"></a>將 Mobile Threat Defense 應用程式新增至尚未註冊的裝置

根據預設，使用 Intune 應用程式防護原則搭配 Mobile Threat Defense 時，Intune 會引導使用者在其裝置上安裝並登入所有必要應用程式，以啟用與相關服務的連線。

使用者需要 Microsoft Authenticator (iOS) 來註冊其裝置，還需要 Mobile Threat Defense (Android 及 iOS)，當系統在其行動裝置中識別出威脅時才能收到通知，以及收到修復威脅的指導方針。

您也可以選擇使用 Intune 來新增和部署 Microsoft Authenticator 及 Mobile Threat Defense (MTD) 應用程式。

> [!NOTE] 
> 此文章適用於所有支援應用程式防護原則的 Mobile Threat Defense 合作夥伴：Better Mobile (Android)、Zimperium (iOS)、Lookout for Work (Android/iOS)。
> 
> 針對尚未註冊的裝置，您**不需要 iOS 應用程式設定原則**，來為您搭配 Intune 使用的 iOS 應用程式設定 Mobile Threat Defense。 這是相較於 Intune 註冊裝置的主要差異。 

## <a name="configure-microsoft-authenticator-for-ios-via-intune-optional"></a>透過 Intune 設定適用於 iOS 的 Microsoft Authenticator (選擇性)
使用 Intune 應用程式防護原則搭配 Mobile Threat Defense 時，Intune 會引導使用者安裝、登入，並向 Microsoft Authenticator (iOS) 註冊其裝置。

不過，如果您想要透過 Intune 公司入口網站將應用程式提供給使用者，請參閱[將 iOS 市集應用程式新增至 Microsoft Intune](../apps/store-apps-ios.md) 的指示。 當您完成＜設定應用程式資訊＞  一節時，請使用此 [Microsoft Authenticator - iOS App Store URL](https://itunes.apple.com/us/app/microsoft-authenticator/id983156458?mt=8)。 在最後一個步驟中，請記得[使用 Intune 將應用程式指派給群組](../apps/apps-deploy.md)。

> [!NOTE] 
> 針對 iOS 裝置，您需要有 [Microsoft Authenticator](https://docs.microsoft.com/azure/multi-factor-authentication/end-user/microsoft-authenticator-app-how-to)，讓使用者可以透過 Azure AD 檢查其身分識別。 Intune 公司入口網站可作為 Android 裝置上的代理程式，讓使用者可以透過 Azure AD 檢查其身分識別。

## <a name="making-mobile-threat-defense-apps-available-via-intune-optional"></a>透過 Intune 提供 Mobile Threat Defense 應用程式 (選擇性)
使用 Intune 應用程式防護原則搭配 Mobile Threat Defense 時，Intune 會引導使用者安裝並登入所需的 Mobile Threat Defense 用戶端應用程式。 

不過，如果您想要透過 Intune 公司入口網站將應用程式提供給使用者，您可以在 [Azure 入口網站](https://portal.azure.com/)中執行以下步驟。 確定您已熟悉下列程序：

- [將應用程式新增至 Intune](../apps/apps-add.md)。
- [使用 Intune 指派應用程式](../apps/apps-deploy.md)。

### <a name="making-lookout-for-work-available-to-end-users"></a>將 Lookout for Work 提供給使用者
- **Android**  
  - 請參閱[將 Android 市集應用程式新增至 Microsoft Intune](../apps/store-apps-android.md) 的指示。 當您完成＜設定應用程式資訊＞  一節時，請使用此 [Lookout for Work - Play Store URL](https://play.google.com/store/apps/details?id=com.lookout.enterprise)。

- **iOS**
  - 請參閱[將 iOS 市集應用程式新增至 Microsoft Intune](../apps/store-apps-ios.md) 的指示。 當您完成＜設定應用程式資訊＞  一節時，請使用此 [Lookout for Work - iOS App Store URL](https://itunes.apple.com/us/app/lookout-for-work/id997193468?mt=8)。

<!-- ### Making Symantec Endpoint Protection Mobile available to end users
- **Android**
  - See the instructions for [adding Android store apps to Microsoft Intune](../apps/store-apps-android.md). When completing the **Configure app information** section, use this [SEP Mobile app store URL](https://play.google.com/store/apps/details?id=com.skycure.skycure). For **Minimum operating system**, select **Android 4.0 (Ice Cream Sandwich)**.

- **iOS**
  - See the instructions for [adding iOS store apps to Microsoft Intune](../apps/store-apps-ios.md). Use this [SEP Mobile - App Store URL](https://itunes.apple.com/us/app/skycure/id695620821?mt=8) when completing the **Configure app information** section.

### Making Check Point SandBlast Mobile available to end users
- **Android**  
  - See the instructions for [adding Android store apps to Microsoft Intune](../apps/store-apps-android.md). Use this [Check Point SandBlast Mobile - Play Store URL](https://play.google.com/store/apps/details?id=com.lacoon.security.fox) when completing the **Configure app information** section. 

- **iOS**
  - See the instructions for [adding iOS store apps to Microsoft Intune](../apps/store-apps-ios.md). Use this [Check Point SandBlast Mobile - App Store URL](https://apps.apple.com/us/app/sandblast-mobile-protect/id1006390797) when completing the **Configure app information** section. -->

### <a name="making-zimperium-available-to-end-users"></a>將 Zimperium 提供給使用者
<!-- - **Android**
  - See the instructions for [adding Android store apps to Microsoft Intune](../apps/store-apps-android.md). Use this [Zimperium - Play Store URL](https://play.google.com/store/apps/details?id=com.zimperium.zips&hl=en) when completing the **Configure app information** section. -->
- **iOS**
  - 請參閱[將 iOS 市集應用程式新增至 Microsoft Intune](../apps/store-apps-ios.md) 的指示。 當您完成＜設定應用程式資訊＞  一節時，請使用此 [Zimperium - App Store URL](https://itunes.apple.com/us/app/zimperium-zips/id1030924459?mt=8)。
 
<!-- ### Making Pradeo available to end users
- **Android**
  - See the instructions for [adding Android store apps to Microsoft Intune](../apps/store-apps-android.md). Use this [Pradeo - Play Store URL](https://play.google.com/store/apps/details?id=net.pradeo.service&hl=en_US) when completing the **Configure app information** section.

- **iOS**
  - See the instructions for [adding iOS store apps to Microsoft Intune](../apps/store-apps-ios.md). Use this [Pradeo - App Store URL](https://itunes.apple.com/us/app/pradeo-agent/id547979360?mt=8) when completing the **Configure app information** section. -->

### <a name="making-better-mobile-available-to-end-users"></a>將 Better Mobile 提供給使用者 
- **Android**
  - 請參閱[將 Android 市集應用程式新增至 Microsoft Intune](../apps/store-apps-android.md) 的指示。 當您完成＜設定應用程式資訊＞  一節時，請使用此 [Active Shield - Play Store URL](https://play.google.com/store/apps/details?id=com.better.active.shield.enterprise)。
<!-- - **iOS**
  - See the instructions for [adding iOS store apps to Microsoft Intune](../apps/store-apps-ios.md). Use this [ActiveShield - App Store URL](https://itunes.apple.com/us/app/activeshield/id980234260?mt=8&uo=4) when completing the **Configure app information** section. -->

<!-- ### Making Sophos available to end users
- **Android**
  - See the instructions for [adding Android store apps to Microsoft Intune](../apps/store-apps-android.md). Use this [Sophos - Play Store URL](https://play.google.com/store/apps/details?id=com.sophos.smsec) when completing the **Configure app information** section.

- **iOS**
  - See the instructions for [adding iOS store apps to Microsoft Intune](../apps/store-apps-ios.md). Use this [ActiveShield - App Store URL](https://itunes.apple.com/us/app/sophos-mobile-security/id1086924662?mt=8) when completing the **Configure app information** section.

### Making Wandera available to end users
- **Android**
  - See the instructions for [adding Android store apps to Microsoft Intune](../apps/store-apps-android.md). Use this [Wandera Mobile - Play Store URL](https://play.google.com/store/apps/details?id=com.wandera.android) when completing the **Configure app information** section. For **Minimum operating system**, select **Android 5.0**.

- **iOS**
  - See the instructions for [adding iOS store apps to Microsoft Intune](../apps/store-apps-ios.md). Use this [Wandera Mobile - - App Store URL](https://itunes.apple.com/app/wandera/id605469330) when completing the **Configure app information** section. -->

## <a name="next-steps"></a>後續步驟  

- [在 Intune 中針對尚未註冊的裝置啟用 Mobile Threat Defense 連接器](~/protect/mtd-enable-unenrolled-devices.md)


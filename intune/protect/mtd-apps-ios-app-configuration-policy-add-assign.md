---
title: 新增並指派 MTD 應用程式到 Microsoft Intune
titleSuffix: Microsoft Intune
description: 在 Azure 入口網站上使用 Intune 來新增 Mobile Threat Defense (MTD) 應用程式、Microsoft Authenticator 應用程式和 iOS 設定原則。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/18/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 00356258-76a8-4a84-9cf5-64ceedb58e72
ms.reviewer: davera
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: efdb1912fdbb2f28c6859fae4407116173daa99d
ms.sourcegitcommit: 47c9af81c385c7e893fe5a85eb79cf08e69e6831
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/25/2020
ms.locfileid: "77576283"
---
# <a name="add-and-assign-mobile-threat-defense-mtd-apps-with-intune"></a>使用 Intune 新增並指派 Mobile Threat Defense (MTD) 應用程式

您可以使用 Intune 來新增及部署 Mobile Threat Defense (MTD) 應用程式，讓終端使用者可在其行動裝置上識別出威脅時收到通知，以及收到修復威脅的指引。

> [!NOTE]
> 本文適用於所有 Mobile Threat Defense 合作夥伴。

## <a name="before-you-begin"></a>開始之前

在 Intune 中完成下列步驟。 確定您已熟悉下列程序：

- [將應用程式新增至 Intune](../apps/apps-add.md)。
- [將 iOS 應用程式設定原則新增至 Intune](../apps/app-configuration-policies-use-ios.md)。
- [使用 Intune 指派應用程式](../apps/apps-deploy.md)。

> [!TIP]
> Intune 公司入口網站可作為 Android 裝置上的代理程式，讓使用者可以透過 Azure AD 檢查其身分識別。

## <a name="configure-microsoft-authenticator-for-ios"></a>設定適用於 iOS 的 Microsoft Authenticator

針對 iOS 裝置，您需要有 [Microsoft Authenticator](https://docs.microsoft.com/azure/multi-factor-authentication/end-user/microsoft-authenticator-app-how-to)，讓使用者可以透過 Azure AD 檢查其身分識別。 此外，您需要 iOS 應用程式設定原則來設定要搭配 Intune 使用的 MTD iOS 應用程式。

請參閱[將 iOS 市集應用程式新增至 Microsoft Intune](../apps/store-apps-ios.md) 的指示。 設定 [應用程式資訊]  時，請使用此 [Microsoft Authenticator 應用程式市集 URL](https://itunes.apple.com/us/app/microsoft-authenticator/id983156458?mt=8)。

## <a name="configure-mtd-applications"></a>設定 MTD 應用程式

選擇對應至您 MTD 提供者的章節：

- [Lookout for Work](#configure-lookout-for-work-apps)
- [Symantec Endpoint Protection Mobile (SEP Mobile)](#configure-symantec-endpoint-protection-mobile-apps)
- [Check Point SandBlast Mobile](#configure-check-point-sandblast-mobile-apps)
- [Zimperium](#configure-zimperium-apps)
- [Pradeo](#configure-pradeo-apps)
- [Better Mobile](#configure-better-mobile-apps)
- [Sophos Mobile](#configure-sophos-apps)
- [Wandera](#configure-wandera-apps)

### <a name="configure-lookout-for-work-apps"></a>設定 Lookout for Work 應用程式

- **Android**
  - 請參閱[將 Android 市集應用程式新增至 Microsoft Intune](../apps/store-apps-android.md) 的指示。 針對 [Appstore URL]  ，請使用 [Lookout for Work Google 應用程式市集 URL](https://play.google.com/store/apps/details?id=com.lookout.enterprise)。

- **iOS**
  - 請參閱[將 iOS 市集應用程式新增至 Microsoft Intune](../apps/store-apps-ios.md) 的指示。 針對 [Appstore URL]  ，請使用 [Lookout for Work iOS 應用程式市集 URL](https://itunes.apple.com/us/app/lookout-for-work/id997193468?mt=8)。

- **Apple Store 之外的 Lookout for Work 應用程式**
  - 您必須重新簽署 iOS 版的 Lookout for Work 應用程式。 Lookout 會將其 Lookout for Work iOS 應用程式散發到 iOS App Store 之外。 發佈應用程式之前，您必須使用 iOS 企業開發人員憑證重新簽署應用程式。  
  - 如需重新簽署 Lookout for Work iOS 應用程式的詳細指示，請參閱 Lookout 網站上的 [Lookout for Work iOS app re-signing process](https://personal.support.lookout.com/hc/articles/114094038714) (Lookout for Work iOS App 重新簽署程序)。

  - **啟用 Lookout for Work iOS 應用程式使用者的 Azure AD 驗證。**

    1. 移至 [Azure 入口網站](https://portal.azure.com)，使用您的認證登入，然後巡覽至應用程式頁面。

    2. 新增 **Lookout for Work iOS 應用程式**作為**原生用戶端應用程式**。

    3. 以您簽署 IPA 時所選取的客戶配套識別碼取代 **com.lookout.enterprise.yourcompanyname**。

    4. 新增其他重新導向 URI： **&lt;公司入口網站 ://code/>** ，後面接著原始重新導向 URI 的 URL 編碼版本。

    5. 新增**委派的權限**至您的應用程式。

    > [!NOTE]
    > 如需詳細資料，請參閱[使用 Azure AD 設定原生用戶端應用程式](https://azure.microsoft.com/documentation/articles/app-service-mobile-how-to-configure-active-directory-authentication/#optional-configure-a-native-client-application)。

  - **新增 Lookout for Work ipa 檔案。**

    - 上傳重新簽署的 .ipa 檔案，如[使用 Intune 新增 iOS LOB 應用程式](../apps/lob-apps-ios.md)一文中所述。 您也必須將最低作業系統版本設定為 iOS 8.0 或更新版本。

### <a name="configure-symantec-endpoint-protection-mobile-apps"></a>設定 Symantec Endpoint Protection Mobile 應用程式

- **Android**
  - 請參閱[將 Android 市集應用程式新增至 Microsoft Intune](../apps/store-apps-android.md) 的指示。 針對 [Appstore URL]  ，請使用 [SEP Mobile 應用程式市集 URL](https://play.google.com/store/apps/details?id=com.skycure.skycure)。  對於 [最基本的作業系統]  ，選取 [Android 4.0 (Ice Cream Sandwich)]  。

- **iOS**
  - 請參閱[將 iOS 市集應用程式新增至 Microsoft Intune](../apps/store-apps-ios.md) 的指示。 針對 [Appstore URL]  ，請使用 [SEP Mobile 應用程式市集 URL](https://itunes.apple.com/us/app/skycure/id695620821?mt=8)。

### <a name="configure-check-point-sandblast-mobile-apps"></a>設定 Check Point SandBlast Mobile 應用程式

- **Android**  
  - 請參閱[將 Android 市集應用程式新增至 Microsoft Intune](../apps/store-apps-android.md) 的指示。 針對 [Appstore URL]  請使用 [Check Point SandBlast Mobile 應用程式市集 URL](https://play.google.com/store/apps/details?id=com.lacoon.security.fox)。

- **iOS**
  - 請參閱[將 iOS 市集應用程式新增至 Microsoft Intune](../apps/store-apps-ios.md) 的指示。 針對 [Appstore URL]  ，請使用 [Check Point SandBlast Mobile 應用程式市集 URL](https://apps.apple.com/us/app/sandblast-mobile-protect/id1006390797)。  

### <a name="configure-zimperium-apps"></a>設定 Zimperium 應用程式

- **Android**
  - 請參閱[將 Android 市集應用程式新增至 Microsoft Intune](../apps/store-apps-android.md) 的指示。 針對 [Appstore URL]  請使用 [Google Play 的 Zimperium URL](https://play.google.com/store/apps/details?id=com.zimperium.zips&hl=en)。

- **iOS**
  - 請參閱[將 iOS 市集應用程式新增至 Microsoft Intune](../apps/store-apps-ios.md) 的指示。 針對 [Appstore URL]  ，請使用 [Zimperium 應用程式市集 URL](https://itunes.apple.com/us/app/zimperium-zips/id1030924459?mt=8)。  
 
### <a name="configure-pradeo-apps"></a>設定 Pradeo 應用程式

- **Android**
  - 請參閱[將 Android 市集應用程式新增至 Microsoft Intune](../apps/store-apps-android.md) 的指示。 針對 [Appstore URL]  ，請使用 [Pradeo 應用程式市集 URL](https://play.google.com/store/apps/details?id=net.pradeo.service&hl=en_US)。

- **iOS**
  - 請參閱[將 iOS 市集應用程式新增至 Microsoft Intune](../apps/store-apps-ios.md) 的指示。 針對 [Appstore URL]  ，請使用 [Pradeo 應用程式市集 URL](https://itunes.apple.com/us/app/pradeo-agent/id547979360?mt=8)。

### <a name="configure-better-mobile-apps"></a>設定 Better Mobile 應用程式

- **Android**
  - 請參閱[將 Android 市集應用程式新增至 Microsoft Intune](../apps/store-apps-android.md) 的指示。 針對 [Appstore URL]  ，請使用 [Active Shield 應用程式市集 URL](https://play.google.com/store/apps/details?id=com.better.active.shield.enterprise)。

- **iOS**
  - 請參閱[將 iOS 市集應用程式新增至 Microsoft Intune](../apps/store-apps-ios.md) 的指示。 針對 [Appstore URL]  ，請使用 [Active Shield 應用程式市集 URL](https://itunes.apple.com/us/app/activeshield/id980234260?mt=8&uo=4)。

### <a name="configure-sophos-apps"></a>設定 Sophos 應用程式

- **Android**
  - 請參閱[將 Android 市集應用程式新增至 Microsoft Intune](../apps/store-apps-android.md) 的指示。 針對 [Appstore URL]  ，請使用 [Sophos 應用程式市集 URL](https://play.google.com/store/apps/details?id=com.sophos.smsec)。

- **iOS**
  - 請參閱[將 iOS 市集應用程式新增至 Microsoft Intune](../apps/store-apps-ios.md) 的指示。 針對 [Appstore URL]  ，請使用 [ 應用程式市集 URL](https://itunes.apple.com/us/app/sophos-mobile-security/id1086924662?mt=8)。

### <a name="configure-wandera-apps"></a>設定 Wandera 應用程式

- **Android**
  - 請參閱[將 Android 市集應用程式新增至 Microsoft Intune](../apps/store-apps-android.md) 的指示。 針對 [Appstore URL]  ，請使用 [Wandera Mobile 應用程式市集 URL](https://play.google.com/store/apps/details?id=com.wandera.android)。 針對 [最基本的作業系統]  ，選取 [Android 5.0]  。

- **iOS**
  - 請參閱[將 iOS 市集應用程式新增至 Microsoft Intune](../apps/store-apps-ios.md) 的指示。 針對 [Appstore URL]  ，請使用 [Wandera Mobile 應用程式市集 URL](https://itunes.apple.com/app/wandera/id605469330)。

## <a name="configure-your-mtd-apps-with-an-ios-app-configuration-policy"></a>使用 iOS 應用程式設定原則來設定您的 MTD 應用程式

### <a name="lookout-for-work-app-configuration-policy"></a>Lookout for Work 應用程式設定原則

建立 iOS 應用程式設定原則，如[使用 iOS 應用程式設定原則](../apps/app-configuration-policies-use-ios.md)一文中所述。

### <a name="sep-mobile-app-configuration-policy"></a>SEP Mobile 應用程式設定原則

請使用之前已在 [Symantec Endpoint Protection 管理主控台](https://aad.skycure.com)中設定的相同 Azure AD 帳戶，這應該是您登入 Intune 所用的帳戶。

- **下載** iOS 應用程式設定原則檔案：
  - 移至 [Symantec Endpoint Protection Management 主控台](https://aad.skycure.com) \(英文\) 並使用您的系統管理員認證登入。

  - 移至 [設定]  ，然後在 [整合]  ，選擇 [Intune]  。 選擇 [EMM 整合選取]  。 選擇 [Microsoft]  ，然後儲存您的選取項目。

  - 按一下 [整合安裝檔案]  連結，然後儲存所產生的 \*.zip 檔案。 .zip 檔案包含 * **.plist** 檔案，會用來在 Intune 中建立 iOS 應用程式設定原則。

  - 請參閱[使用適用於 iOS 的 Microsoft Intune 應用程式設定原則](../apps/app-configuration-policies-use-ios.md)的指示，以新增 SEP Mobile iOS 應用程式設定原則。

    - 針對 [組態設定格式]  ，請選取 [輸入 XML 資料]  ，然後將所複製的 * **.plist** 檔案內容貼入設定原則本文中。

> [!NOTE]
> 如果您無法擷取檔案，請連絡 [Symantec Endpoint Protection Mobile Enterprise 支援](https://support.symantec.com/en_US/contact-support.html)。

### <a name="check-point-sandblast-mobile-app-configuration-policy"></a>Check Point SandBlast Mobile 應用程式設定原則

請參閱[使用適用於 iOS 的 Microsoft Intune 應用程式設定原則](../apps/app-configuration-policies-use-ios.md)指示，新增 Check Point SandBlast Mobile iOS 應用程式設定原則。

- 針對 [組態設定格式]  ，請選取 [輸入 XML 資料]  ，然後將所複製的下列內容貼入設定原則本文中。

  `<dict><key>MDM</key><string>INTUNE</string></dict>`


### <a name="zimperium-app-configuration-policy"></a>Zimperium 應用程式設定原則

請參閱[使用適用於 iOS 的 Microsoft Intune 應用程式設定原則](../apps/app-configuration-policies-use-ios.md)的指示，以新增 Zimperium iOS 應用程式設定原則。

- 針對 [組態設定格式]  ，請選取 [輸入 XML 資料]  ，然後將所複製的下列內容貼入設定原則本文中。

   ```
   <dict>
   <key>provider</key><string>Intune</string>
   <key>userprincipalname</key><string>{{userprincipalname}}</string>
   <key>deviceid</key>
   <string>{{deviceid}}</string>
   <key>serialnumber</key>
   <string>{{serialnumber}}</string>
   <key>udidlast4digits</key>
   <string>{{udidlast4digits}}</string>
   </dict>
   ```

### <a name="pradeo-app-configuration-policy"></a>Pradeo 應用程式設定原則

Pradeo 在 iOS/iPadOS 上不支援應用程式設定原則。  若要取得設定好的應用程式，請改為使用 Pradeo 來實作已預設偏好設定的自訂 IPA 或 APK 檔案。

### <a name="better-mobile-app-configuration-policy"></a>Better Mobile 應用程式設定原則

請參閱[使用適用於 iOS 的 Microsoft Intune 應用程式設定原則](../apps/app-configuration-policies-use-ios.md)的指示，以新增 Better Mobile iOS 應用程式設定原則。

- 針對 [組態設定格式]  ，請選取 [輸入 XML 資料]  ，然後將所複製的下列內容貼入設定原則本文中。 使用適當的主控台 URL 取代 `https://client.bmobi.net` URL。

   ```
    <dict>
   <key>better_server_url</key>
   <string>https://client.bmobi.net</string>
   <key>better_udid</key>
   <string>{{aaddeviceid}}</string>
   <key>better_user</key>
   <string>{{userprincipalname}}</string>
   </dict>
   ```

### <a name="sophos-mobile-app-configuration-policy"></a>Sophos Mobile 應用程式設定原則

建立 iOS 應用程式設定原則，如[使用 iOS 應用程式設定原則](../apps/app-configuration-policies-use-ios.md)一文中所述。

### <a name="wandera-app-configuration-policy"></a>Wandera 應用程式設定原則

請參閱[使用適用於 iOS 的 Microsoft Intune 應用程式設定原則](../apps/app-configuration-policies-use-ios.md)的指示，以新增 Wandera iOS 應用程式設定原則。

- 針對 [組態設定格式]  ，請選取 [輸入 XML 資料]  。

登入您的 RADAR Wandera 入口網站並瀏覽到 [設定] \(設定\)   > [EMM Integration] \(EMM 整合\)   > [App Push] \(應用程式推播\)  。 選取 [Intune]  ，然後複製下列內容並將它貼到設定原則本文中。  

  ```
  <dict><key>secretKey</key>
  <string>SeeRADAR</string>
  <key>apiKey</key>
  <string> SeeRADAR </string>
  <key>customerId</key>
  <string> SeeRADAR </string>
  <key>email</key>
  <string>{{mail}}</string>
  <key>firstName</key>
  <string>{{username}}</string>
  <key>lastName</key>
  <string></string>
  <key>activationType</key>
  <string>PROVISION_THEN_AWP</string></dict>
  ```

## <a name="assign-apps-to-groups"></a>將應用程式指派給群組

這個步驟適用於所有 MTD 合作夥伴。 請參閱[利用 Intune 將應用程式指派給群組](../apps/apps-deploy.md)的指示。

## <a name="next-steps"></a>後續步驟

- [設定 MTD 的裝置合規性原則](mtd-device-compliance-policy-create.md)

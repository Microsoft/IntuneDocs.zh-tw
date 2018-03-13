---
title: "將 MTD 應用程式新增並指派至 Intune"
titleSuffix: Azure portal
description: "Azure 入口網站上使用 Intune 來新增 MTD 應用程式、Microsoft Authenticator 應用程式和 iOS 設定原則"
keywords: 
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 07/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 00356258-76a8-4a84-9cf5-64ceedb58e72
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 7afe03c635b63053ef0cc0f622bc9324f31ec68b
ms.sourcegitcommit: eac89306d1391a6d3ae1179612b0820b19c2baa6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="add-and-assign-mobile-threat-defense-mtd-apps-with-intune"></a>使用 Intune 新增並指派 Mobile Threat Defense (MTD) 應用程式

> [!NOTE] 
> 此主題適用於所有 Mobile Threat Defense 合作夥伴。

您可以使用 Intune 來新增及部署 MTD 應用程式，讓使用者可在其行動裝置上識別出威脅時收到通知，以及收到修復威脅的指引。

針對 iOS 裝置，您需要有 [Microsoft Authenticator](https://docs.microsoft.com/azure/multi-factor-authentication/end-user/microsoft-authenticator-app-how-to)，讓使用者可以透過 Azure AD 檢查其身分識別。 此外，您需要發出訊號給 MTD iOS 應用程式，以搭配使用 Intune 的 iOS 應用程式組態原則。

> [!TIP]
> Intune 公司入口網站可作為 Android 裝置上的代理程式，讓使用者可以透過 Azure AD 檢查其身分識別。

## <a name="before-you-begin"></a>開始之前

-   下列步驟必須在 [Azure 入口網站](https://portal.azure.com/)中完成。

-   確定您已熟悉下列程序：

    -   [將應用程式新增至 Intune](apps-add.md)。

    -   [將 iOS 應用程式設定原則新增至 Intune](https://docs.microsoft.com/intune/deploy-use/configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune)。

    -   [使用 Intune 指派應用程式](https://docs.microsoft.com/intune/deploy-use/deploy-apps-in-microsoft-intune)。

    -   [新增 iOS 應用程式設定原則](https://docs.microsoft.com/intune/deploy-use/configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune)。

## <a name="to-add-apps"></a>新增應用程式

### <a name="all-mtd-partners"></a>所有 MTD 合作夥伴

#### <a name="microsoft-authenticator-app-for-ios"></a>適用於 iOS 的 Microsoft Authenticator 應用程式

- 請參閱[將 iOS 市集應用程式新增至 Microsoft Intune](store-apps-ios.md) 的指示。 在**設定應用程式資訊**一節下的**步驟 5** 中，使用這個 [Microsoft Authenticator 應用程式市集 URL](https://itunes.apple.com/us/app/microsoft-authenticator/id983156458?mt=8)。

### <a name="lookout"></a>Lookout

#### <a name="android"></a>Android
- 請參閱[將 Android 市集應用程式新增至 Microsoft Intune](store-apps-android.md) 的指示。 在**步驟 7** 中，使用這個 [Lookout for Work Google 應用程式市集 URL](https://play.google.com/store/apps/details?id=com.lookout.enterprise)。

#### <a name="ios"></a>iOS

- 請參閱[將 iOS 市集應用程式新增至 Microsoft Intune](store-apps-ios.md) 的指示。 在**設定應用程式資訊**一節下的**步驟 5** 中，使用這個 [Lookout for Work iOS 應用程式市集 URL](https://itunes.apple.com/us/app/lookout-for-work/id997193468?mt=8)。

#### <a name="lookout-for-work-app-outside-the-apple-store"></a>Apple 市集之外的 Lookout for Work 應用程式

您必須重新簽署 Lookout for Work iOS 應用程式。 Lookout 會將其 Lookout for Work iOS 應用程式散發到 iOS App Store 之外。 發佈應用程式之前，您必須使用 iOS 企業開發人員憑證重新簽署應用程式。

如需重新簽署 Lookout for Work iOS 應用程式的詳細指示，請參閱 Lookout 網站上的 [Lookout for Work iOS app re-signing process](https://personal.support.lookout.com/hc/articles/114094038714) (Lookout for Work iOS App 重新簽署程序)。

##### <a name="enable-azure-ad-authentication-for-lookout-for-work-ios-app"></a>啟用 Lookout for Work iOS 應用程式的 Azure AD 驗證

執行下列動作，啟用 iOS 使用者的 Azure Active Directory 驗證：

1. 移至 [Azure 入口網站](https://portal.azure.com)，使用您的認證登入，然後巡覽至應用程式頁面。
  
2. 新增 **Lookout for Work iOS 應用程式**作為**原生用戶端應用程式**。

3. 以您簽署 IPA 時所選取的客戶配套識別碼取代 **com.lookout.enterprise.yourcompanyname**。

4.  新增其他重新導向 URI：**&lt;公司入口網站 ://code/>**，後面接著原始重新導向 URI 的 URL 編碼版本。

5.  新增**委派的權限**至您的應用程式。

    > [!NOTE] 
    > 如需詳細資料，請參閱[使用 Azure AD 設定原生用戶端應用程式](https://azure.microsoft.com/documentation/articles/app-service-mobile-how-to-configure-active-directory-authentication/#optional-configure-a-native-client-application)。

##### <a name="add-the-lookout-for-work-ipa-file"></a>新增 Lookout for Work ipa 檔案

- 上傳重新簽署的 .ipa 檔案，如[使用 Intune 新增 iOS LOB 應用程式](lob-apps-ios.md)主題中所述。 您也必須將最低作業系統版本設定為 iOS 8.0 或更新版本。

### <a name="skycure"></a>Skycure

#### <a name="android"></a>Android

- 請參閱[將 Android 市集應用程式新增至 Microsoft Intune](store-apps-android.md) 的指示。 在**步驟 7** 中，使用這個 [Skycure 應用程式市集 URL](https://play.google.com/store/apps/details?id=com.skycure.skycure)。

#### <a name="ios"></a>iOS

- 請參閱[將 iOS 市集應用程式新增至 Microsoft Intune](store-apps-ios.md) 的指示。 在**設定應用程式資訊**一節下的**步驟 5** 中，使用這個 [Skycure 應用程式市集 URL](https://itunes.apple.com/us/app/skycure/id695620821?mt=8)。

### <a name="check-point-sandblast-mobile"></a>Check Point SandBlast Mobile

#### <a name="android"></a>Android

- 請參閱[將 Android 市集應用程式新增至 Microsoft Intune](store-apps-android.md) 的指示。 請在**步驟 7**使用此 [Check Point SandBlast Mobile 應用程式市集 URL](https://play.google.com/store/apps/details?id=com.lacoon.security.fox)。

#### <a name="ios"></a>iOS

- 請連絡 [Check Point SandBlast Mobile](https://www.checkpoint.com/products/sandblast-mobile/) 以取得該 iOS 應用程式。 請參閱[將 iOS 商店應用程式新增至 Microsoft Intune](store-apps-ios.md) 的指示，然後使用**設定應用程式資訊**一節下，**步驟 5** 的 Apple 商店 URL。

### <a name="zimperium"></a>Zimperium

#### <a name="android"></a>Android

- 請參閱[將 Android 市集應用程式新增至 Microsoft Intune](store-apps-android.md) 的指示。 在**步驟 7** 中，使用這個 [Zimperium 應用程式市集 URL](https://play.google.com/store/apps/details?id=com.zimperium.zips&hl=en)。

#### <a name="ios"></a>iOS

- 請參閱[將 iOS 市集應用程式新增至 Microsoft Intune](store-apps-ios.md) 的指示。 在**設定應用程式資訊**一節下的**步驟 5** 中，使用這個 [Zimperium 應用程式市集 URL](https://itunes.apple.com/us/app/zimperium-zips/id1030924459?mt=8)。

## <a name="to-associate-the-mtd-app-with-an-ios-app-configuration-policy"></a>建立 MTD 應用程式與 iOS 應用程式設定原則的關聯性

### <a name="for-lookout"></a>若為 Lookout

- 建立 iOS 應用程式設定原則，如[使用 iOS 應用程式設定原則](app-configuration-policies-use-ios.md)主題中所述。

### <a name="for-skycure"></a>若為 Skycure

-   使用先前在 [Skycure 管理主控台](https://aad.skycure.com)中設定的同一個 Azure AD 帳戶，此帳戶應與用於登入 Intune 傳統入口網站的帳戶相同。

-   您必須**下載** iOS 應用程式設定原則檔案： 
    -   前往 [Skycure Management 主控台](https://aad.skycure.com)，並以管理員認證登入。
    
    -   移至 [設定] &gt; [裝置管理整合] &gt; [EMM 整合選項]、選擇 [Microsoft Intune]，然後儲存您的選項。
    
    -   按一下 [整合安裝檔案] 連結，然後儲存所產生的 \*.zip 檔案。 此 .zip 檔案包含 **skycure\_configuration.plist** 檔案，這會用來在 Intune 中建立 iOS 應用程式設定原則。
    
    -   請參閱[使用適用於 iOS 的 Microsoft Intune 應用程式設定原則](app-configuration-policies-use-ios.md)的指示，以新增 Skycure iOS 應用程式設定原則。
    
    - 在**步驟 8** 中，使用選項 [輸入 XML 資料]，從 **skycure_configuration.plist** 檔案複製內容，再將其貼到設定原則本文中。

您也可以從此處複製 **skycure_configuration.plist** 內容：

```
<dict>
    <key>MdmType</key>
    <string>Intune</string>
    <key>UserEmail</key>
    <string>{{userprincipalname}}</string>
</dict>

```
### <a name="for-check-point-sandblast-mobile"></a>適用於 Check Point SandBlast Mobile

- 請參閱[使用適用於 iOS 的 Microsoft Intune 應用程式設定原則](app-configuration-policies-use-ios.md)指示，新增 Check Point SandBlast Mobile iOS 應用程式設定原則。
    - 在**步驟 8** 中，使用選項 [輸入 XML 資料]，複製下方內容，並將其貼到設定原則本文中。

```
<dict><key>MDM</key><string>INTUNE</string></dict>

```

### <a name="for-zimperium"></a>若為 Zimperium

- 請參閱[使用適用於 iOS 的 Microsoft Intune 應用程式設定原則](app-configuration-policies-use-ios.md)的指示，以新增 Zimperium iOS 應用程式設定原則。
    - 在**步驟 8** 中，使用選項 [輸入 XML 資料]，複製下方內容，並將其貼到設定原則本文中。

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

## <a name="to-assign-apps-all-mtd-partners"></a>指派應用程式 (所有 MTD 合作夥伴)

- 請參閱[利用 Intune 將應用程式指派給群組](apps-deploy.md)的指示。

## <a name="next-steps"></a>接下來的步驟

- [新增 MTD 的裝置合規性政策](mtd-device-compliance-policy-create.md)

---
title: Microsoft Intune App SDK for iOS 開發人員指南
description: Microsoft Intune App SDK for iOS 可讓您將 Intune 應用程式保護原則 (也稱為 APP 或 MAM 原則) 併入原生 iOS 應用程式中。
keywords: ''
author: Erikre
manager: dougeby
ms.author: erikre
ms.date: 04/06/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 8e280d23-2a25-4a84-9bcb-210b30c63c0b
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 486ff2d22cb201abc926efc96a83455be98e7536
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="microsoft-intune-app-sdk-for-ios-developer-guide"></a>Microsoft Intune App SDK for iOS 開發人員指南

> [!NOTE]
> 您可能想要先閱讀 [Intune App SDK 快速入門指南](app-sdk-get-started.md)一文，其中說明如何在每個支援的平台上進行整合準備。

Microsoft Intune App SDK for iOS 可讓您將 Intune 應用程式保護原則 (也稱為 **APP** 或 **MAM** 原則) 併入原生 iOS 應用程式中。 啟用 MAM 的應用程式是與 Intune App SDK 整合的應用程式。 IT 系統管理員可在 Intune 主動管理應用程式時，將應用程式保護原則部署至行動應用程式。

## <a name="prerequisites"></a>必要條件

* 您需要執行 OS X 10.8.5 或更新版本的 Mac OS 電腦，並且該電腦已安裝 Xcode 9 或更新版本。

* 您的應用程式必須以 iOS 9.3.5 或更新版本為目標。

* 檢閱[適用於 iOS 的 Intune App SDK 授權條款](https://github.com/msintuneappsdk/ms-intune-app-sdk-ios/blob/master/Microsoft%20License%20Terms%20Intune%20App%20SDK%20for%20iOS%20.pdf)。 列印並保留一份授權條款供您備查。 下載並使用 Intune App SDK for iOS 即表示您同意這些授權條款。  如果您不接受這些條款，請不要使用此軟體。

* 在 [GitHub](https://github.com/msintuneappsdk/ms-intune-app-sdk-ios) 上，下載 Intune App SDK for iOS 的檔案。

## <a name="whats-in-the-sdk"></a>SDK 的功能

Intune App SDK for iOS 包含靜態程式庫、資源檔、API 標頭、偵錯設定 .plist 檔案及設定程式工具。 若要強制執行大部分原則，行動應用程式只需要包含資源檔並以靜態方式連結至程式庫。 進階 Intune MAM 功能則是透過 API 來強制執行。

本指南涵蓋如何使用 Intune App SDK for iOS 的下列元件：

* **libIntuneMAM.a**：Intune App SDK 靜態程式庫。 如果您的應用程式未使用擴充功能，請將這個程式庫連結至專案，讓應用程式進行 Intune 行動應用程式管理。

* **IntuneMAM.framework**：Intune App SDK 架構。 請將這個架構連結至專案，讓應用程式進行 Intune 行動應用程式管理。 如果您的應用程式使用延伸模組，讓您的專案不會建立靜態程式庫的多個複本，請使用架構而不是靜態程式庫。

* **IntuneMAMResources.bundle**：包含 SDK 相依資源的資源配套。

* **標頭**：公開 Intune App SDK API。 如果您使用 API，您必須加入包含 API 的標頭檔。 下列標頭檔包含 API、資料類型及通訊協定，由 Intune App SDK 提供開發人員使用：

    * IntuneMAMAppConfig.h
    * IntuneMAMAppConfigManager.h
    * IntuneMAMDataProtectionInfo.h
    * IntuneMAMDataProtectionManager.h
    * IntuneMAMDefs.h
    * IntuneMAMEnrollmentDelegate.h
    * IntuneMAMEnrollmentManager.h
    * IntuneMAMEnrollmentStatus.h
    * IntuneMAMFileProtectionInfo.h
    * IntuneMAMFileProtectionManager.h
    * IntuneMAMLogger.h
    * IntuneMAMPolicy.h
    * IntuneMAMPolicyDelegate.h
    * IntuneMAMPolicyManager.h
    * IntuneMAMVersionInfo.h

開發人員只要匯入 IntuneMAM.h，即可使用上述標頭的內容


## <a name="how-the-intune-app-sdk-works"></a>Intune App SDK 的運作方式

Intune App SDK for iOS 的目標是以最少的程式碼變更，將管理功能加入 iOS 應用程式中。 程式碼變更越少，上市時間就越短，而不會影響行動應用程式的一致性與穩定性。


## <a name="build-the-sdk-into-your-mobile-app"></a>將 SDK 建置到行動應用程式

若要啟用 Intune App SDK，請遵循下列步驟：

1. **選項 1 (建議)**：將 `IntuneMAM.framework` 連結至您的專案。 將 `IntuneMAM.framework` 拖曳至專案目標的 [內嵌的二進位檔案] 清單。

    > [!NOTE]
    > 如果您使用架構，則必須先手動去除通用架構中的模擬器架構，再將應用程式提交至 App Store。 請參閱[將應用程式提交至 App Store](#Submit-your-app-to-the-App-Store) 以取得詳細資料。

2. **選項 2**︰連結至 `libIntuneMAM.a` 程式庫。 將 `libIntuneMAM.a` 程式庫拖曳至專案目標的 「Linked Frameworks and Libraries」 (連結架構和程式庫) 清單中。

    ![Intune App SDK iOS：連結的架構和程式庫](./media/intune-app-sdk-ios-linked-frameworks-and-libraries.png)

    將 `-force_load {PATH_TO_LIB}/libIntuneMAM.a` 加入下列任一項中，並以 Intune App SDK 位置取代 `{PATH_TO_LIB}` ：
   * 專案的 `OTHER_LDFLAGS` 組建組態設定
   * Xcode UI 的 [Other Linker Flags] \(其他連結器旗標\)

     > [!NOTE]
     > 若要尋找 `PATH_TO_LIB`，請選取 `libIntuneMAM.a` 檔案，然後從 [檔案] 功能表中選擇 [取得資訊]。 從 [資訊] 視窗的 [一般] 區段中，複製並貼上 [位置] 資訊 (路徑)。

     藉由拖曳 「Build Phases」 (建置階段) 的 「Copy Bundle Resources」 (複製配套資源) 下的資源配套，將 `IntuneMAMResources.bundle` 資源配套新增至專案。

     ![Intune App SDK iOS：複製配套資源](./media/intune-app-sdk-ios-copy-bundle-resources.png)

     將下列 iOS 架構新增至專案：  
    * MessageUI.framework  
    * Security.framework  
    * MobileCoreServices.framework  
    * SystemConfiguration.framework  
    * libsqlite3.tbd  
    * libc++.tbd  
    * ImageIO.framework  
    * LocalAuthentication.framework  
    * AudioToolbox.framework  
    * QuartzCore.framework  
    * WebKit.framework

3. 如果尚未啟用 Keychain 共用，請在每個專案目標中選擇 [功能]，然後啟用 「Keychain Sharing」 (Keychain 共用) 參數來加以啟用。 您必須共用 Keychain 才能繼續進行下一個步驟。

   > [!NOTE]
   > 您的佈建設定檔必須能夠支援新的 Keychain 共用值。 Keychain 存取群組應該支援萬用字元。 若要確認這項作業，請在文字編輯器中開啟 .mobileprovision 檔案，並搜尋 **keychain-access-groups**，然後確認是否有萬用字元。 例如：
   >  ```xml
   >  <key>keychain-access-groups</key>
   >  <array>
   >  <string>YOURBUNDLESEEDID.*</string>
   >  </array>
   >  ```

4. 啟用 Keychain 共用之後，請遵循下列步驟建立另一個可供 Intune App SDK 儲存其資料的存取群組。 您可以使用 UI 或權利檔案來建立 Keychain 存取群組。 如果您是使用 UI 來建立 Keychain 存取群組，請務必遵循下列步驟：

   1. 如果您的行動應用程式未定義任何 Keychain 存取群組，請加入應用程式的配套識別碼作為第一個群組。

   2. 將共用 Keychain 群組 `com.microsoft.intune.mam` 新增至現有的存取群組。 Intune App SDK 使用這個存取群組來儲存資料。

   3. 將 `com.microsoft.adalcache` 新增至現有存取群組。

       ![Intune App SDK iOS：Keychain 共用](./media/intune-app-sdk-ios-keychain-sharing.png)

   4. 如果您正在直接編輯權利檔案，而不是使用上方所示的 Xcode UI 來建立 Keychain 存取群組，請將 `$(AppIdentifierPrefix)` 附加到 Keychain 存取群組 (Xcode 會自動處理此動作)。 例如：

           * `$(AppIdentifierPrefix)com.microsoft.intune.mam`
           * `$(AppIdentifierPrefix)com.microsoft.adalcache`

      > [!NOTE]
      > 權利檔案是行動應用程式特有的 XML 檔案， 它用來指定 iOS 應用程式內的特殊權限和功能。 如果您的應用程式之前沒有權利檔案，啟用 Keychain 共用 (步驟 3) 應該會使得 Xcode 為您的應用程式產生一個權利檔案。

5. 請包含應用程式傳遞給應用程式 Info.plist 檔案之 `LSApplicationQueriesSchemes` 陣列中 `UIApplication canOpenURL` 的每個通訊協定。 繼續進行下一個步驟支援，請務必儲存您的變更。

6. 使用 [SDK 存放庫](https://github.com/msintuneappsdk/ms-intune-app-sdk-ios)中包含的 IntuneMAMConfigurator 工具來設定您應用程式的 Info.plist。 此工具有 3 個參數：

   |屬性|用法|
   |---------------|--------------------------------|
   |- i |  `<Path to the input plist>` |
   |- e | `<Path to the entitlements file>` |
   |- o |  (選擇性) `<Path to the output plist>` |

若未指定 '-o' 參數，將就地修改輸入檔案。 此工具是理想的，且應該在應用程式的 Info.plist 或權利變更時重新執行。 更新 Intune SDK 時，您也應該下載並執行此工具的最新版本，以免 Info.plist 設定需求在最新版本中有變更。

## <a name="configure-azure-active-directory-authentication-library-adal"></a>設定 Azure Active Directory Authentication Library (ADAL)

Intune App SDK 針對其驗證和條件式啟動案例使用 [Azure Active Directory Authentication Library (英文)](https://github.com/AzureAD/azure-activedirectory-library-for-objc)。 它也會依賴 ADAL 向 MAM 服務註冊使用者身分識別來進行沒有裝置註冊案例的管理。

一般來說，ADAL 需要應用程式向 Azure Active Directory (AAD) 註冊並取得唯一識別碼 (用戶端識別碼) 及其他識別碼，以確保授與應用程式的權杖安全無虞。 除非另行指定，否則 Intune App SDK 在連絡 Azure AD 時會使用預設登錄值。  

如果您的應用程式已經使用 ADAL 來驗證使用者，該應用程式必須使用其現有的登錄值，並覆寫 Intune App SDK 預設值。 這能確保不會提示使用者驗證兩次 (一次是由 Intune App SDK，另一次是由應用程式)。

### <a name="recommendations"></a>建議

建議您的應用程式連接至 ADAL Master 分支上[最新版本的 ADAL (英文)](https://github.com/AzureAD/azure-activedirectory-library-for-objc/releases)。 Intune App SDK 目前使用 ADAL 的 Broker 分支，以支援需要條件式存取的應用程式。 (因此這些應用程式需要 Microsoft Authenticator 應用程式)。不過，SDK 仍然與主要 ADAL 分支相容。 請使用適合您應用程式的分支。

### <a name="link-to-adal-binaries"></a>連結至 ADAL 二進位檔

請遵循下列步驟以將應用程式連結至 ADAL 二進位檔：

1. 從 GitHub 下載[適用於 Objective-C 的 Azure Active Directory Authentication Library (ADAL) (英文)](https://github.com/AzureAD/azure-activedirectory-library-for-objc)，然後遵循使用 Git 子模組或 CocoaPods 下載 ADAL 的[指示 (英文)](https://github.com/AzureAD/azure-activedirectory-library-for-objc#download)。

2. 將 ADAL 架構 (選項 1) 或靜態程式庫 (選項 2) 新增到您的專案：

    **選項 1 (建議)**：將 `ADAL.framework` 拖曳到專案目標的 [內嵌的二進位檔案] 清單。

    **選項 2**：將 `libADALiOS.a` 程式庫拖曳至專案目標的 [Linked Frameworks and Libraries] \(連結架構和程式庫\) 清單。 將 `-force_load {PATH_TO_LIB}/libADALiOS.a` 新增至專案的 `OTHER_LDFLAGS` 組建組態設定或 Xcode UI 的 [Other Linker Flags] \(其他連結器旗標\) 中。 `PATH_TO_LIB` 應該取代成 ADAL 二進位檔位置。



### <a name="share-the-adal-token-cache-with-other-apps-signed-with-the-same-provisioning-profile"></a>與其他使用相同佈建設定檔簽署的應用程式共用 ADAL 權杖快取？**

如果您想要在使用相同佈建設定檔簽署的應用程式之間共用 ADAL 權杖，請遵循下列指示：

1. 如果您的應用程式未定義任何 Keychain 存取群組，請加入應用程式的配套識別碼作為第一個群組。

2. 透過將 `com.microsoft.adalcache` 新增到 Keychain 存取群組以啟用 ADAL 單一登入 (SSO)。

3. 如果您想要指定自訂 Keychain 群組以取代 `com.microsoft.adalcache`，請在 Info.plist 檔案的 IntuneMAMSettings 下使用 `ADALCacheKeychainGroupOverride` 索引鍵指定該行為。

### <a name="configure-adal-settings-for-the-intune-app-sdk"></a>設定 Intune App SDK 的 ADAL 設定

如果您的應用程式已經使用 ADAL 來進行驗證，並擁有自己的 ADAL 設定，您可以強制 Intune App SDK 在針對 Azure Active Directory 進行驗證期間使用相同的設定。 這能確保應用程式不會重複提示使用者進行驗證。 請參閱[設定 Intune App SDK 的設定](#configure-settings-for-the-intune-app-sdk)，以取得如何填入下列設定的相關資訊：  

* ADALClientId
* ADALAuthority
* ADALRedirectUri
* ADALRedirectScheme
* ADALCacheKeychainGroupOverride

如果您的應用程式已經使用 ADAL，下列設定為必要：

1. 在專案的 Info.plist 檔案中，在 **IntuneMAMSettings** 字典下的索引鍵名稱 `ADALClientId` 處，指定要用於呼叫 ADAL 的用戶端識別碼。

2. 另外在 **IntuneMAMSettings** 字典下的索引鍵名稱 `ADALAuthority` 處，指定 Azure AD 授權。

3. 另外在 **IntuneMAMSettings** 字典下的索引鍵名稱 `ADALRedirectUri` 處，指定要用於呼叫 ADAL 的重新導向 URI。 此外，若應用程式的重新導向 URI 格式為 `scheme://bundle_id`，您也可以改為指定 `ADALRedirectScheme`。


此外，應用程式可以在執行階段覆寫這些 Azure AD 設定。 若要這樣做，請設定 `IntuneMAMPolicyManager` 執行個體上的 `aadAuthorityUriOverride`、`aadClientIdOverride` 與 `aadRedirectUriOverride` 屬性。

> [!NOTE]
> 建議您為靜態且不需要在執行階段決定的所有設定使用 Info.plist 方法。 指派給 `IntuneMAMPolicyManager` 屬性之值的優先順序高於在 Info.plist 中指定的對應值，而且在應用程式重新啟動之後仍然存在。 SDK 將會繼續為原則簽入使用它們，直到使用者取消註冊或值被清除或變更。

### <a name="if-your-app-does-not-use-adal"></a>如果您的應用程式未使用 ADAL

如果您的應用程式未使用 ADAL，Intune App SDK 將會提供 ADAL 參數的預設值，並處理針對 Azure AD 的驗證。 您不需要為上面所列的 ADAL 設定指定任何值。

## <a name="receiving-app-protection-policy"></a>接收應用程式保護原則

### <a name="overview"></a>概觀
若要接收 Intune 應用程式保護原則，應用程式必須向 Intune MAM 服務起始註冊要求。 應用程式可以在 Intune 主控台中設定，以接收應用程式保護原則 (不論是否有裝置註冊)。 無註冊的應用程式保護原則 (亦稱為 **APP-WE** 或 MAM-WE) 可讓 Intune 管理應用程式，而不需要向 Intune 行動裝置管理 (MDM) 註冊裝置。 在這兩種案例中，都必須向 Intune MAM 服務註冊才能接收原則。

### <a name="apps-that-use-adal"></a>使用 ADAL 的應用程式

使用者成功驗證之後，已使用 ADAL 的應用程式應該呼叫 `IntuneMAMEnrollmentManager` 執行個體上的 `registerAndEnrollAccount` 方法：

```objc
/*
 *  This method will add the account to the list of registered accounts.
 *  An enrollment request will immediately be started.
 *  @param identity The UPN of the account to be registered with the SDK
 */

(void)registerAndEnrollAccount:(NSString *)identity;
```

藉由呼叫 `registerAndEnrollAccount` 方法，SDK 將註冊使用者帳戶，並代表這個帳戶嘗試註冊應用程式。 如果註冊因任何原因而失敗，SDK 將自動在 24 個小時之後重新嘗試註冊。 基於偵錯目的，應用程式可以透過委派來接收有關任何註冊要求結果的[通知](#Status-result-and-debug-notifications)。

叫用這個 API 之後，應用程式可以繼續正常運作。 如果註冊成功，SDK 將通知使用者：需要重新啟動應用程式。 此時，使用者可以立即重新啟動應用程式。

```objc
[[IntuneMAMEnrollmentManager instance] registerAndEnrollAccount:@”user@foo.com”];
```

### <a name="apps-that-do-not-use-adal"></a>不使用 ADAL 的應用程式

未使用 ADAL 登入使用者的應用程式，仍然可以從 Intune MAM 服務接收應用程式保護原則，方法是呼叫 API 讓 SDK 處理該驗證。 如果應用程式尚未向 Azure AD 驗證使用者，但仍需要擷取應用程式保護原則以協助保護資料，則應用程式應該使用這項技術。 例如：如果正在使用另一個驗證服務進行應用程式登入，或者，如果應用程式根本不支援登入。 若要這樣做，應用程式應該會呼叫 `IntuneMAMEnrollmentManager` 執行個體上的 `loginAndEnrollAccount` 方法：

```objc
/**
 *  Creates an enrollment request which is started immediately.
 *  If no token can be retrieved for the identity, the user will be prompted
 *  to enter their credentials, after which enrollment will be retried.
 *  @param identity The UPN of the account to be logged in and enrolled.
 */
 (void)loginAndEnrollAccount: (NSString *)identity;
```

藉由呼叫這個方法，SDK 將在找不到現有權杖時提示使用者提供認證。 SDK 接著將會代表所提供的使用者帳戶，嘗試向 Intune MAM 服務註冊應用程式。 這個方法在呼叫時 "nil" 為身分識別。 在這個情況下，SDK 將會使用裝置上現有的受控使用者註冊 (在 MDM 的案例中)，或在找不到任何現有使用者時提示使用者提供使用者名稱。

如果註冊失敗，應用程式應該考慮根據失敗詳細資料，在未來重新呼叫這個 API。 應用程式可以透過委派來接收有關任何註冊要求結果的[通知](#Status-result-and-debug-notifications)。

叫用這個 API 之後，應用程式可以繼續正常運作。 如果註冊成功，SDK 將通知使用者：需要重新啟動應用程式。

範例：
```objc
[[IntuneMAMEnrollmentManager instance] loginAndEnrollAccount:@”user@foo.com”];
```

### <a name="deregister-user-accounts"></a>取消註冊使用者帳戶

將使用者登出應用程式之前，應用程式應該從 SDK 取消註冊使用者。 這確保：

1. 使用者帳戶不再發生註冊重試。

2. 將會移除應用程式保護原則。

3. 如果應用程式起始選擇性抹除 (選擇性)，則會刪除任何公司資料。

將使用者登出之前，應用程式應該呼叫 `IntuneMAMEnrollmentManager` 執行個體上的下列方法：

```objc
/*
 *  This method will remove the provided account from the list of
 *  registered accounts.  Once removed, if the account has enrolled
 *  the application, the account will be un-enrolled.
 *  @note In the case where an un-enroll is required, this method will block
 *  until the Intune MAM AAD token is acquired, then return.  This method must be called before  
 *  the user is removed from the application (so that required AAD tokens are not purged
 *  before this method is called).
 *  @param identity The UPN of the account to be removed.
 *  @param doWipe   If YES, a selective wipe if the account is un-enrolled
 */
(void)deRegisterAndUnenrollAccount:(NSString *)identity withWipe:(BOOL)doWipe;
```

刪除使用者帳戶的 Azure AD 權杖之前，必須呼叫這個方法。 SDK 需要使用者帳戶的 AAD 權杖，才能代表使用者對 Intune MAM 服務提出特定要求。

如果應用程式將自行刪除使用者的公司資料，則 `doWipe` 旗標可以設定為 false。 否則，應用程式可以讓 SDK 起始選擇性抹除。 這樣會呼叫應用程式的選擇性抹除委派。

範例：
```objc
[[IntuneMAMEnrollmentManager instance] deRegisterAndUnenrollAccount:@”user@foo.com” withWipe:YES];
```

## <a name="status-result-and-debug-notifications"></a>狀態、結果和偵錯通知

應用程式可以接收有關向 Intune MAM 服務提出下列要求的狀態、結果和偵錯通知：

 - 註冊要求
 - 原則更新要求
 - 取消註冊要求

透過 `Headers/IntuneMAMEnrollmentDelegate.h` 中的委派方法來呈現通知：

```objc
/**
 *  Called when an enrollment request operation is completed.
 * @param status status object containing debug information
 */

(void)enrollmentRequestWithStatus:(IntuneMAMEnrollmentStatus *)status;

/**
 *  Called when a MAM policy request operation is completed.
 *  @param status status object containing debug information
 */
(void)policyRequestWithStatus:(IntuneMAMEnrollmentStatus *)status;

/**
 *  Called when a un-enroll request operation is completed.
 *  @Note: when a user is un-enrolled, the user is also de-registered with the SDK
 *  @param status status object containing debug information
 */

(void)unenrollRequestWithStatus:(IntuneMAMEnrollmentStatus *)status;
```

這些委派方法傳回 `IntuneMAMEnrollmentStatus` 物件，其中包含下列資訊：

- 與要求相關聯之帳戶的身分識別
- 表示要求結果的狀態碼
- 狀態碼描述的錯誤字串
- `NSError` 物件

這個物件與可傳回的特定狀態碼定義在 `IntuneMAMEnrollmentStatus.h` 中。


### <a name="sample-code"></a>範例程式碼

下列是委派方法的範例實作：

```objc
- (void)enrollmentRequestWithStatus:(IntuneMAMEnrollmentStatus *)status
{
    NSLog(@"enrollment result for identity %@ with status code %ld", status.identity, (unsigned long)status.statusCode);
    NSLog(@"Debug Message: %@", status.errorString);
}


- (void)policyRequestWithStatus:(IntuneMAMEnrollmentStatus *)status
{
    NSLog(@"policy check-in result for identity %@ with status code %ld", status.identity, (unsigned long)status.statusCode);
    NSLog(@"Debug Message: %@", status.errorString);
}

- (void)unenrollRequestWithStatus:(IntuneMAMEnrollmentStatus *)status
{
    NSLog(@"un-enroll result for identity %@ with status code %ld", status.identity, (unsigned long)status.statusCode);
    NSLog(@"Debug Message: %@", status.errorString);
}
```

## <a name="app-restart"></a>應用程式重新啟動

應用程式第一次收到應用程式保護原則時，必須重新啟動，才能套用必要的勾點。 為了通知需要重新啟動的應用程式，SDK 在 Headers/IntuneMAMPolicyDelegate.h 中提供委派方法。

```objc
 - (BOOL) restartApplication
```
這個方法的傳回值會指示 SDK，應用程式是否必須處理必要的重新啟動：   

 - 如果傳回 true，應用程式就必須處理重新啟動。   

 - 如果傳回 false，則 SDK 將在傳回這個方法之後重新啟動應用程式。 SDK 會立即顯示一個對話方塊，指示使用者重新啟動應用程式。

## <a name="customize-your-apps-behavior"></a>自訂您的應用程式行為

Intune 應用程式 SDK 中有多個 API，您可以呼叫以取得部署至應用程式之 Intune 應用程式保護原則的相關資訊。 您可以使用這項資料來自訂您的應用程式行為。 大部分的應用程式保護原則設定會由 SDK 自動強制執行，而不是應用程式。 應用程式應該實作的唯一設定是「另存新檔」控制項。

### <a name="get-app-protection-policy"></a>取得應用程式保護原則

#### <a name="intunemampolicymanagerh"></a>IntuneMAMPolicyManager.h
IntuneMAMPolicyManager 類別會公開部署給應用程式的 Intune 應用程式保護原則。 值得注意的是，它會公開適用於[啟用多重身分識別](#-enable-multi-identity-optional)的 API。

#### <a name="intunemampolicyh"></a>IntuneMAMPolicy.h
IntuneMAMPolicy 類別會公開部署給應用程式的 Intune 應用程式保護原則。 此類別中大部分公開的原則設定會由 SDK 強制執行，但您一律可以根據如何強制執行原則設定來自訂應用程式的行為。

這個類別會公開要實作另存新檔控制項所需的部分 API，如下節中所詳述。

### <a name="implement-save-as-controls"></a>實作另存新檔控制項

Intune 可讓 IT 系統管理員選取受管理的應用程式可儲存資料的儲存位置。 應用程式可以使用 **isSaveToAllowedForLocation** API 向 Intune App SDK 查詢所能使用的儲存位置，如 **IntuneMAMPolicy.h** 中所定義。

應用程式必須先向 **isSaveToAllowedForLocation** API 查詢，確認 IT 系統管理員是否允許將資料另存於其他位置，才能將受管理的資料儲存到雲端儲存體或本機位置。

當應用程式使用 **isSaveToAllowedForLocation** API 時，必須傳遞儲存位置的 UPN (如有使用)。

#### <a name="supported-save-locations"></a>支援的儲存位置

**IsSaveToAllowedForLocation** API 提供常數以確認 IT 系統管理員是否可將資料儲存到 IntuneMAMPolicy.h 中定義的下列位置：

* IntuneMAMSaveLocationOther
* IntuneMAMSaveLocationOneDriveForBusiness
* IntuneMAMSaveLocationSharePoint
* IntuneMAMSaveLocationLocalDrive

應用程式應使用 **isSaveToAllowedForLocation** API 的常數確認是否可以將資料另存於其他被視為「受管理」(例如商務用 OneDrive) 或「個人」的位置。 此外，當應用程式無法確認位置為「受管理」或「個人」的位置時，也應使用 API。

已知為「個人」的位置會以 `IntuneMAMSaveLocationOther` 常數代表。

若應用程式會將資料儲存到本機裝置上的任何位置，則應使用 `IntuneMAMSaveLocationLocalDrive` 常數。

## <a name="configure-settings-for-the-intune-app-sdk"></a>設定 Intune App SDK 的設定

您可以使用應用程式 Info.plist 檔案中的 **IntuneMAMSettings** 字典，以設定 Intune App SDK。 如果 Info.plist 檔案中看不到 IntuneMAMSettings 字典，您應該使用欄位名稱 "IntuneMAMSettings" 在應用程式的 Info.plist 中建立字典。

在 IntuneMAMSettings 字典底下，您可以新增組態設定的索引鍵/值列以設定 SDK。 下表列出所有支援的設定。

其中一些設定可能在前幾節中討論過，而且有些設定並不適用於所有應用程式。

設定  | 類型  | 定義 | 必要？
--       |  --   |   --       |  --
ADALClientId  | 字串  | 應用程式的 Azure AD 用戶端識別碼。 | 如果應用程式使用 ADAL，則為必要項。 |
ADALAuthority | 字串 | 應用程式的使用中 Azure AD 授權單位。 您應該使用已設定 AAD 帳戶的專屬環境。 | 如果應用程式使用 ADAL，則為必要項。 如果此值不存在，則會使用 Intune 預設值。|
ADALRedirectUri  | 字串  | 應用程式的 Azure AD 重新導向 URI。 | 如果應用程式使用 ADAL，則需要 ADALRedirectUri 或 ADALRedirectScheme。  |
ADALRedirectScheme  | 字串  | 應用程式的 Azure AD 重新導向配置。 如果應用程式的重新導向 URI 格式為 `scheme://bundle_id`，則這可以用來代替 ADALRedirectUri。 | 如果應用程式使用 ADAL，則需要 ADALRedirectUri 或 ADALRedirectScheme。 |
ADALLogOverrideDisabled | 布林值  | 指定 SDK 是否會將所有 ADAL 記錄 (包括任何來自應用程式的 ADAL 呼叫) 路由傳送至其本身的記錄檔。 預設為 [否]。 如果應用程式將設定自己的 ADAL 記錄回呼，請設定為 [是]。 | 選擇性。 |
ADALCacheKeychainGroupOverride | 字串  | 指定要用於 ADAL 快取而非 "com.microsoft.adalcache" 的 Keychain 群組。 請注意，這不包含 app-id 前置詞。 這會在執行階段加在所提供字串的前面。 | 選擇性。 |
AppGroupIdentifiers | 字串陣列  | 應用程式之權利 com.apple.security.application-groups 區段中的應用程式群組陣列。 | 如果應用程式使用應用程式群組，則為必要項。 |
ContainingAppBundleId | 字串 | 指定含有應用程式之擴充功能的配套識別碼。 | 對 IOS 擴充功能而言為必要項。 |
DebugSettingsEnabled| 布林值 | 如果設定為 [是]，則可以套用 [設定] 配套內的測試原則。 啟用這個設定時，*不*應該提供應用程式。 | 選擇性。 |
MainNibFile<br>MainNibFile~ipad  | 字串  | 這項設定應該包含應用程式的主要 nib 檔案名稱。  | 如果應用程式在 Info.plist 中定義 MainNibFile，則為必要項。 |
MainStoryboardFile<br>MainStoryboardFile~ipad  | 字串  | 這項設定應該包含應用程式的主要腳本檔案名稱。 | 如果應用程式在 Info.plist 中定義 UIMainStoryboardFile，則為必要項。 |
AutoEnrollOnLaunch| 布林值| 指定如果偵測到現有的受管理身分識別，而且其尚未註冊，應用程式是否要在啟動時嘗試自動註冊。 預設為 [否]。 <br><br> 注意事項：若找不到受管理身分識別，或 ADAL 快取中沒有可用的身分識別有效權杖，除非應用程式也有將 MAMPolicyRequired 設為 [是]，否則註冊嘗試會失敗而不提示輸入認證。 | 選擇性。 |
MAMPolicyRequired| 布林值| 指定應用程式在沒有 Intune 應用程式保護原則時，是否無法予以啟動。 預設為 [否]。 <br><br> 注意事項︰MAMPolicyRequired 設為 [是] 時，無法將應用程式提交至 App Store。 當 MAMPolicyRequired 設定為 [是] 時，AutoEnrollOnLaunch 也應該設定為 [是]。 | 選擇性。 |
MAMPolicyWarnAbsent | 布林值| 指定應用程式在沒有 Intune 應用程式保護原則時，是否將在啟動期間警告使用者。 <br><br> 注意事項︰使用者在關閉警告之後，仍可在沒有原則的情況下使用應用程式。 | 選擇性。 |
MultiIdentity | 布林值| 指定應用程式是否為多重身分識別感知。 | 選擇性。 |
SplashIconFile <br>IntuneMAMSettings | 字串  | 指定 Intune 啟動顯示 (啟動) 畫面的圖示檔。 | 選擇性。 |
SplashDuration | 數字 | Intune 啟動畫面將於應用程式啟動時顯示的最短時間 (以秒為單位)。 預設為 1.5。 | 選擇性。 |
BackgroundColor| 字串| 指定啟動畫面和 PIN 畫面的背景色彩。 接受格式為 #XXXXXX 的十六進位 RGB 字串，其中 X 的範圍可以是 0-9 或 A-F。 可能會省略井字號。   | 選擇性。 預設為淺灰色。 |
ForegroundColor| 字串| 指定啟動畫面和 PIN 畫面的前景色彩，例如文字色彩。 接受格式為 #XXXXXX 的十六進位 RGB 字串，其中 X 的範圍可以是 0-9 或 A-F。 可能會省略井字號。  | 選擇性。 預設為黑色。 |
AccentColor | 字串| 指定 PIN 畫面的輔色，例如按鈕文字色彩和方塊醒目提示色彩。 接受格式為 #XXXXXX 的十六進位 RGB 字串，其中 X 的範圍可以是 0-9 或 A-F。 可能會省略井字號。| 選擇性。 預設為系統藍色。 |
MAMTelemetryDisabled| 布林值| 指定 SDK 是否不會將任何遙測資料傳送至其後端。| 選擇性。 |
WebViewHandledURLSchemes | 字串陣列 | 指定您應用程式的 WebView 所處理的 URL 配置。 | 如果您的應用程式使用透過連結及 (或) JavaScript 處理 URL 的 WebView，則為必要項。 |  

> [!NOTE]
> 如果您的應用程式將發行到 App Store，`MAMPolicyRequired` 必須設為 [否]，這是根據 App Store 的標準。

## <a name="sharing-data-via-uiactivityviewcontroller"></a>透過 UIActivityViewController 共用資料 
從 8.0.2+ 版開始，Intune APP SDK 將可篩選 UIActivityViewController 動作，因此將不能選取非 Intune 共用位置。 此行為將由應用程式資料傳輸原則和即將推出的應用程式功能所控制。 即將推出的功能將在大多數 Microsoft 第一方應用程式 (也就是 Word、Excel、Powerpoint) 進行必要變更，以透過 UIActivityViewController 支援共用資料後啟用。 
 
### <a name="copy-to-actions"></a>「複製到」動作 
當透過 UIActivityViewController 和 UIDocumentInteractionController 共用文件時，iOS 會針對支援開啟已共用文件的每個應用程式，顯示「複製到」動作。 應用程式會透過其 Info.plist 中的 CFBundleDocumentTypes 設定，宣告它們支援的文件類型。 如果原則不允許共用到未受管理的應用程式，那麼此類型的共用將無法再使用。 替代方案是，應用程式必須將非 UI 動作延伸模組新增到其應用程式，並將它連結到適用於 iOS 的 Intune APP SDK。 動作延伸模組就像是虛設常式。 SDK 會實作所有的檔案共用行為。 請遵循上述 SDK 整合步驟以及下列事項： 
 
1. 您的應用程式必須在其 Info.plist CFBundleURLTypes 下至少定義一個 schemeURL。 
2. 您應用程式和動作延伸模組至少必須共用一個應用程式群組，而且應用程式群組必須列在應用程式和延伸模組 IntuneMAMSettings 字典下的 AppGroupIdentifiers 陣列下。 
3. 將動作延伸模組命名為「以 ... 開啟」，其中 ... 是應用程式名稱。 視需要將 Info.plist 當地語系化。 
4. 為延伸模組設計範本圖示，如同 [Apple 開發人員文件](https://developer.apple.com/ios/human-interface-guidelines/extensions/sharing-and-actions/)所述。 或者，可使用 IntuneMAMConfigurator 工具，從應用程式的 .app 目錄中產生這些影像。 執行「IntuneMAMConfigurator-generateOpenInIcons /path/to/app.app-o /path/to/output/directory」 
5. 在延伸模組的 Info.plist 中的 IntuneMAMSettings 下，新增名為 OpenInActionExtension 的布林值設定，且其值為 YES。 
6. 從應用程式的 CFBundleDocumentTypes 加上「com.microsoft.intune.mam」為開頭，設定 NSExtensionActivationRule 以支援單一檔案和所有類型。 例如，如果應用程式支援 public.text 和 public.image，則啟用規則將會是： 

```
SUBQUERY ( 
    extensionItems, 
    $extensionItem, 
    SUBQUERY ( 
        $extensionItem.attachments, 
        $attachment, 
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "com.microsoft.intune.mam.public.text” || 
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "com.microsoft.intune.mam.public.image”).@count == 1 
).@count == 1 
```

### <a name="update-existing-share-and-action-extensions"></a>更新現有的共用和動作延伸模組 
如果您的應用程式中已包含共用或動作延伸模組，那麼必須修改其 NSExtensionActivationRule 以允許 Intune 類型。 針對延伸模組支援的每個類型，額外類型的開頭加上「com.microsoft.intune.mam」。 例如，如果現有的啟用規則是：  

```
SUBQUERY ( 
    extensionItems, 
    $extensionItem, 
    SUBQUERY ( 
        $extensionItem.attachments, 
        $attachment, 
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "public.url" || 
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "public.plain-text" || 
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "public.image" || 
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "public.data" 
    ).@count > 0 
).@count > 0 
 ```

則必須變更為： 

```
SUBQUERY ( 
    extensionItems, 
    $extensionItem, 
    SUBQUERY ( 
        $extensionItem.attachments, 
        $attachment, 
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "public.url" || 
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "public.plain-text" || 
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "public.image" || 
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "public.data" || 
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "com.microsoft.intune.mam.public.url" || 
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "com.microsoft.intune.mam.public.plain-text" || 
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "com.microsoft.intune.mam.public.image" || 
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "com.microsoft.intune.mam.public.data 
    ).@count > 0 
).@count > 0 
 ```

>[!Note] IntuneMAMConfigurator 工具可用來將 Intune 類型新增至啟用規則。 如果您現有的啟用規則使用預先定義的字串常數 (例如 NSExtensionActivationSupportsFileWithMaxCount、NSExtensionActivationSupportsText 等)，那麼述詞語法可能變得相當複雜。 IntuneMAMConfigurator 工具也可用來在新增 Intune 類型時，將啟用規則從字串常數轉換成述詞字串。 IntuneMAMConfigurator 可在我們的 GitHub 儲存機制中找到。 


## <a name="enabling-mam-targeted-configuration-for-your-ios-applications"></a>啟用 iOS 應用程式的 MAM 目標設定
MAM 目標設定可讓應用程式透過 Intune App SDK 接收設定資料。 應用程式擁有者/開發人員必須定義此資料的格式和變化，並向 Intune 客戶溝通。 Intune 系統管理員可以透過 Intune Azure 入口網站為設定資料設定目標並進行部署。 從 Intune App SDK for iOS 7.0.1 版開始，可以透過 MAM 服務提供 MAM 目標設定資料給參與 MAM 目標設定的應用程式。 應用程式設定資料是透過我們的 MAM 服務 (而非透過 MDM 通道) 直接向應用程式發佈。 Intune App SDK 會提供類別來存取從這些主控台擷取的資料。 請將下列各項視為必要條件： <br>
* 應用程式必須向 Intune MAM 服務註冊，您才能存取 MAM 目標設定 UI。 如需詳細資訊，請參閱[接收應用程式保護原則](#receiving-app-protection-policy)。
* 在應用程式的原始程式檔中包含 ```IntuneMAMAppConfigManager.h```。
* 呼叫 ```[[IntuneMAMAppConfigManager instance] appConfigForIdentity:]``` 以取得應用程式設定物件。
* 在 ```IntuneMAMAppConfig``` 物件上呼叫適當的選取器。 例如，如果您的應用程式金鑰是字串，您會想要使用 ```stringValueForKey``` 或 ```allStringsForKey```。 ```IntuneMAMAppConfig.h header``` 檔案是針對傳回值/錯誤狀況。

如需圖形 API 功能的詳細資訊，請參閱[圖形 API 參考](https://developer.microsoft.com/graph/docs/concepts/overview)。 <br>

如需如何在 iOS 建立 MAM 目標應用程式設定原則的詳細資訊，請參閱 [How to use Microsoft Intune app configuration policies for iOS](https://docs.microsoft.com/intune/app-configuration-policies-use-ios) (如何使用適用於 iOS 的 Microsoft Intune 應用程式設定原則) 的＜MAM 目標應用程式設定＞一節。

## <a name="telemetry"></a>遙測

Intune App SDK for iOS 預設會記錄下列使用事件的遙測資料。 這些資料會傳送到 Microsoft Intune。

* **應用程式啟動**：協助 Microsoft Intune 依管理類型了解啟用 MAM 的應用程式使用量 (含 MDM 的 MAM、不含 MDM 註冊的 MAM 等)。

* **註冊呼叫**：協助 Microsoft Intune 了解從用戶端起始的註冊呼叫成功率和其他效能標準。

> [!NOTE]
> 如果您選擇不要將 Intune App SDK 遙測資料從您的行動應用程式傳送至 Microsoft Intune，您必須停用 Intune App SDK 遙測擷取。 在 IntuneMAMSettings 字典中將 `MAMTelemetryDisabled` 屬性設定為 [是]。

## <a name="enable-multi-identity-optional"></a>啟用多重身分識別 (選擇性)

SDK 預設會將原則套用至應用程式整體。 多重身分識別是 MAM 功能，您可啟用以將原則套用至每個身分識別層級。 這需要的應用程式參與高於其他 MAM 功能。

當應用程式想要變更作用中身分識別時，必須通知 APP SDK。 需要身分識別變更時，SDK 也會通知應用程式。 目前僅支援一個受管理的身分識別。 使用者註冊裝置或應用程式之後，SDK 會使用這個身分識別，並將其視為主要受管理身分識別。 應用程式中的其他使用者則會因不受限制原則設定而視為不受管理。

請注意，身分識別只會定義為字串。 身分識別不區分大小寫。 身分識別的 SDK 要求可能不會傳回設定身分識別時原本使用的相同大小寫。

### <a name="identity-overview"></a>身分識別概觀

身分識別就是帳戶的使用者名稱 (例如 user@contoso.com)。 開發人員可以設定應用程式在下列層級的身分識別：

* **處理序身分識別**：設定整個處理序的身分識別，並且主要用於單一身分識別應用程式。 這個身分識別會影響所有工作、檔案和 UI。

* **UI 身分識別**：判斷在主要執行緒上將哪些原則套用至 UI 工作，例如剪下/複製/貼上、PIN、驗證和資料共用。 UI 身分識別不會影響檔案工作，例如加密和備份。

* **執行緒身分識別**：影響在目前執行緒上套用哪些原則。 這個身分識別會影響所有工作、檔案和 UI。

不論使用者是否受管理，應用程式都必須負責適當地設定身分識別。

在任何時間，每個執行緒都會有 UI 工作和檔案工作的有效身分識別。 這是用來確認應該套用哪些原則 (如果有的話) 的身分識別。 如果身分識別是 [沒有身分識別]，或使用者未受管理，則不會套用任何原則。 下列圖表顯示如何決定有效的身分識別。

  ![Intune App SDK iOS：連結的架構和程式庫](./media/ios-thread-identities.png)

### <a name="thread-queues"></a>執行緒佇列

應用程式通常會將非同步和同步工作分派至執行緒佇列。 SDK 會攔截 Grand Central Dispatch (GCD) 呼叫，並產生目前執行緒身分識別與已分派工作的關聯。 完成工作時，SDK 會將執行緒身分識別暫時變更為與工作相關聯的身分識別，並完成工作，然後還原原始執行緒身分識別。


因為 `NSOperationQueue` 的建置基礎是 GCD，所以 `NSOperations` 將會在工作新增至 `NSOperationQueue` 時針對執行緒的身分識別執行。 `NSOperations` 或直接透過 GCD 分派的函數也可以在執行時變更目前執行緒身分識別。 這個身分識別將會覆寫繼承自分派執行緒的身分識別。

### <a name="file-owner"></a>檔案擁有者

SDK 會追蹤本機檔案擁有者的身分識別，並據以套用原則。 建立檔案時，或以截斷模式開啟檔案時，會建立檔案擁有者。 擁有者設為執行工作之執行緒的有效檔案工作身分識別。

或者，應用程式可以使用 `IntuneMAMFilePolicyManager` 明確地設定檔案擁有者身分識別。 應用程式可以使用 `IntuneMAMFilePolicyManager` 來擷取檔案擁有者，並在顯示檔案內容之前設定 UI 身分識別。

### <a name="shared-data"></a>共用資料

如果應用程式建立包含受管理和不受管理使用者之資料的檔案，則應用程式必須負責加密受管理使用者的資料。 您可以使用 `IntuneMAMDataProtectionManager` 中的 `protect` 和 `unprotect` API 來加密資料。

`protect` 方法會接受可以是受管理或不受管理使用者的身分識別。 如果是受管理使用者，則會加密資料。 如果是不受管理使用者，則會將標頭新增至編碼身分識別的資料，但不會加密資料。 您可以使用 `protectionInfo` 方法來擷取資料的擁有者。

### <a name="share-extensions"></a>共用擴充功能

如果應用程式包含共用擴充功能，則可以透過 `IntuneMAMDataProtectionManager` 中的 `protectionInfoForItemProvider` 方法來擷取正在共用之項目的擁有者。 如果共用的項目是檔案，則 SDK 會處理檔案擁有者的設定。 如果共用的項目是資料，則在這項資料保存至檔案時，應用程式必須負責設定檔案擁有者，以及呼叫 `setUIPolicyIdentity` API，再於 UI 中顯示這項資料。

### <a name="turning-on-multi-identity"></a>開啟多重身分識別

預設會將應用程式視為單一身分識別。 SDK 會將處理序身分識別設定為已註冊的使用者。 若要啟用多重身分識別支援，請將名稱為 `MultiIdentity` 且值為 [是] 的布林設定新增至應用程式 Info.plist 檔案中的 IntuneMAMSettings 字典。

> [!NOTE]
> 啟用多重身分識別時，處理序身分識別、UI 身分識別和執行緒身分識別都會設定為 nil。 應用程式必須負責正確設定它們。

### <a name="switching-identities"></a>切換身分識別

* **應用程式起始的身分識別切換**：

    啟動時，會將多重身分識別應用程式視為正在使用未知且不受管理的帳戶執行。 條件式啟動 UI 將不會執行，而且不會對應用程式執行任何原則。 應用程式必須負責在應該變更身分識別時通知 SDK。 一般而言，只要應用程式即將顯示特定使用者帳戶的資料，就會發生這種情形。

    範例是使用者嘗試在筆記本中開啟文件、信箱或索引標籤時。 應用程式需要在實際開啟檔案、信箱或索引標籤之前通知 SDK。 這是透過 `IntuneMAMPolicyManager` 中的 `setUIPolicyIdentity` API 所完成。 不論是否為受管理使用者，都應該呼叫這個 API。 如果使用者是受管理的，SDK 將執行條件式啟動檢查，例如破解偵測、PIN 和驗證。

    身分識別切換的結果是透過完成處理常式，以非同步方式傳回給應用程式。 應用程式應該延後開啟文件、信箱或索引標籤，直到傳回成功結果碼。 如果身分識別切換失敗，應用程式應該取消工作。

* **SDK 起始的身分識別切換**：

    SDK 有時需要要求應用程式切換至特定身分識別。 多重身分識別應用程式必須在 `IntuneMAMPolicyDelegate` 中實作 `identitySwitchRequired` 方法，以處理這個要求。

    呼叫此方法時，如果應用程式可以處理切換至所指定身分識別的要求，則應該將 `IntuneMAMAddIdentityResultSuccess` 傳遞至完成處理常式。 如果無法處理身分識別切換，則應用程式應該將 `IntuneMAMAddIdentityResultFailed` 傳遞至完成處理常式。

    應用程式不需要呼叫 `setUIPolicyIdentity` 來回應這個呼叫。 如果 SDK 需要應用程式切換至未受管理使用者帳戶，則會將空字串傳遞至 `identitySwitchRequired` 呼叫。

* **選擇性抹除**：

    選擇性地抹除應用程式時，SDK 將會在 `IntuneMAMPolicyDelegate` 中呼叫 `wipeDataForAccount` 方法。 應用程式必須負責移除指定的使用者帳戶和其相關聯的任何資料。 SDK 可以移除使用者擁有的所有檔案，並在應用程式從 `wipeDataForAccount` 呼叫傳回 FALSE 時執行。

    請注意，會從背景執行緒呼叫這個方法。 在移除使用者的所有資料之前，應用程式不應該傳回值 (不包括應用程式傳回 FALSE 時的檔案)。

## <a name="ios-best-practices"></a>iOS 最佳做法

以下是用於開發 iOS 的建議最佳做法：

* IOS 檔案系統區分大小寫。 請確定檔案名稱的大小寫正確，例如 `libIntuneMAM.a` 和 `IntuneMAMResources.bundle`。

* 如果 Xcode 在尋找 `libIntuneMAM.a` 時遇到問題，您可以藉由將這個程式庫的路徑加入連結器搜尋路徑中，來修正問題。

## <a name="faqs"></a>常見問題集


**是否可透過原生 Swift 或 Objective-C 以及 Swift 互通性定址所有 API？**

Intune App SDK API 僅限於 Objective-C 且不支援原生 Swift。 必須有 Swift 與 Objective-C 的互通性。


**是否需要向 APP-WE 服務註冊應用程式的所有使用者？**

否。 事實上，只應該向 Intune App SDK 註冊工作或學校帳戶。 應用程式負責決定是否在工作或學校內容中使用帳戶。   

**已登入應用程式的使用者如何？是否需要註冊它們？**

應用程式必須負責註冊已成功通過驗證的使用者。 應用程式也必須負責註冊在應用程式具有較少 MDM 的 MAM 功能之前可能已存在的任何現有帳戶。   

若要這樣做，應用程式應該會使用 `registeredAccounts:` 方法。 這個方法會傳回包含所有已註冊至 Intune MAM 服務之帳戶的 NSDictionary。 如果應用程式中的任何現有帳戶都不在清單中，則應用程式應該透過 `registerAndEnrollAccount:` 來註冊這些帳戶。

**SDK 重試註冊的頻率為何？**

SDK 會依 24 小時間隔自動重試所有先前失敗的註冊。 SDK 這麼做以確保如果使用者的組織已在使用者登入應用程式之後啟用 MAM，則使用者會順利註冊並接收原則。

SDK 將會在偵測到使用者已順利註冊應用程式時停止重試。 原因是只有一位使用者可以在特定時間註冊應用程式。 如果取消註冊使用者，則重試會以相同的 24 小時間隔重新開始。

**為何需要取消註冊使用者？**

SDK 將會在背景定期採取下列動作：

 - 如果尚未註冊應用程式，則會每隔 24 小時嘗試註冊所有已註冊的帳戶。
 - 如果已註冊應用程式，SDK 會每隔 8 小時檢查應用程式保護原則更新。

取消註冊使用者會通知 SDK，使用者無法再使用應用程式，而且 SDK 可以停止該使用者帳戶的任何定期事件。 它也會在必要時觸發應用程式取消註冊和選擇性抹除。

**是否應該將 deregister 方法中的 doWipe 旗標設為 true？**

將使用者登出應用程式之前，應該呼叫這個方法。  如果在登出時於應用程式中刪除使用者的資料，則 `doWipe` 可以設為 false。 不過，如果應用程式未移除使用者的資料，則 `doWipe` 應該設為 true，讓 SDK 可以刪除資料。

**是否有任何其他方式可以取消註冊應用程式？**

是，IT 系統管理員可以將選擇性抹除命令傳送給應用程式， 以取消註冊使用者以及抹除使用者資料。 SDK 會自動處理這種情況，並透過取消註冊委派方法來傳送通知。



## <a name="submit-your-app-to-the-app-store"></a>將應用程式提交至 App Store

Intune App SDK 的靜態程式庫和架構組建是通用二進位檔， 表示它們包含適用於所有裝置和模擬器架構的程式碼。 如果提交至 App Store 的應用程式包含模擬器程式碼，則 Apple 會拒絕提交這些應用程式。 針對僅限裝置組建的靜態程式庫進行編譯時，連結器會自動去除模擬器程式碼。 請遵循下列步驟，確認已移除所有模擬器程式碼，然後再將您的應用程式上傳至 App Store。

1. 確定 `IntuneMAM.framework` 在桌面上。

2. 執行下列命令：

    ```bash
    lipo ~/Desktop/IntuneMAM.framework/IntuneMAM -remove i386 -remove x86_64 -output ~/Desktop/IntuneMAM.device_only
    ```

    ```bash
    cp ~/Desktop/IntuneMAM.device_only ~/Desktop/IntuneMAM.framework/IntuneMAM
    ```
    第一個命令會去除架構 DYLIB 檔案中的模擬器架構。 第二個命令會將僅限裝置 DYLIB 檔案複製回架構目錄。

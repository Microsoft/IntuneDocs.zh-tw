---
title: Microsoft Intune App SDK for iOS 開發人員指南
description: Microsoft Intune App SDK for iOS 可讓您將 Intune 應用程式保護原則 (也稱為 APP 或 MAM 原則) 併入原生 iOS 應用程式中。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/02/2020
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: developer
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 8e280d23-2a25-4a84-9bcb-210b30c63c0b
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: f6edf3fd8d6c6aeefeb1e34c5b390360e7215f21
ms.sourcegitcommit: 822a70c61f5d644216ccc401b8e8949bc39e8d4a
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 01/16/2020
ms.locfileid: "76125288"
---
# <a name="microsoft-intune-app-sdk-for-ios-developer-guide"></a>Microsoft Intune App SDK for iOS 開發人員指南

> [!NOTE]
> 請考慮閱讀 [Intune App SDK 快速入門指南](app-sdk-get-started.md)一文，其中說明如何在每個支援的平台上進行整合準備。

Microsoft Intune App SDK for iOS 可讓您將 Intune 應用程式保護原則 (也稱為 APP 或 MAM 原則) 併入原生 iOS 應用程式中。 啟用 MAM 的應用程式是與 Intune App SDK 整合的應用程式。 IT 系統管理員可在 Intune 主動管理應用程式時，將應用程式保護原則部署至行動應用程式。

## <a name="prerequisites"></a>先決條件

* 您需要執行 OS X 10.8.5 或更新版本的 Mac OS 電腦，且該電腦必須已安裝 Xcode 9 或更新版本。

* 您的應用程式必須以 iOS 11 或更新版本為目標。

* 檢閱[適用於 iOS 的 Intune App SDK 授權條款](https://github.com/msintuneappsdk/ms-intune-app-sdk-ios/blob/master/Microsoft%20License%20Terms%20Intune%20App%20SDK%20for%20iOS.pdf)。 列印並保留一份授權條款供您備查。 下載並使用 Intune App SDK for iOS 即表示您同意這些授權條款。  如果您不接受這些條款，請不要使用此軟體。

* 在 [GitHub](https://github.com/msintuneappsdk/ms-intune-app-sdk-ios) 上，下載 Intune App SDK for iOS 的檔案。

## <a name="whats-in-the-sdk-repository"></a>SDK 存放庫中的內容

下列檔案與不包含 Swift 代碼或以 10.2 版之前的 Xcode 進行編譯的應用程式/延伸模組有關：

* **IntuneMAM.framework**：Intune App SDK 架構。 建議您將此架構連結至您的應用程式/延伸模組，以啟用 Intune 用戶端應用程式管理。 不過，有些開發人員可能會偏好靜態程式庫的效能優勢。 請參閱下列項目。

* **libIntuneMAM.a**：Intune App SDK 靜態程式庫。 開發人員可以選擇連結靜態程式庫，而不是架構。 由於靜態程式庫在建置期間會直接內嵌至應用程式/延伸模組二進位檔中，因此使用靜態程式庫會有一些啟動時間的效能優勢。 不過，將其整合至您的應用程式中，是較複雜的程序。 如果您的應用程式包含任何延伸模組，則將靜態程式庫連結至應用程式和延伸模組時，將會產生較大的應用程式套件組合大小，因為靜態程式庫會內嵌到每個應用程式/延伸模組二進位檔中。 使用架構時，應用程式和延伸模組可共用相同的 Intune SDK 二進位檔，而產生較小的應用程式大小。

* **IntuneMAMResources.bundle**：包含 SDK 相依資源的資源套件組合。 只有整合靜態程式庫 (Libintunemam.a) 的應用程式才需要資源套件組合。

下列檔案與包含 Swift 代碼，並且以 Xcode 10.2+ 進行編譯的應用程式/延伸模組有關：

* **IntuneMAMSwift.framework**：Intune App SDK Swift 架構。 此架構包含您的應用程式所將呼叫之 API 的所有標頭。 請將此架構連結至您的應用程式/延伸模組，以啟用 Intune 用戶端應用程式管理。

* **IntuneMAMSwiftStub.framework**：Intune App SDK Swift Stub 架構。 這是應用程式/擴充功能必須連結的 IntuneMAMSwift.framework 所需的相依性。


下列檔案與所有的應用程式/延伸模組有關：

* **IntuneMAMConfigurator**：這項工具可用來設定應用程式或延伸模組的 Info.plist，且只需針對 Intune 管理進行最低限度的必要變更。 您可能需要對 Info.plist 做進一步的手動變更，視您的應用程式或延伸模組功能而定。

* **標頭**：公開公用 Intune App SDK API。 這些標頭包含在 IntuneMAM/IntuneMAMSwift 架構中，因此使用其中一種架構的開發人員不需要手動將標頭新增至其專案。 選擇要連結靜態程式庫 (libIntuneMAM.a)的開發人員必須在其專案中手動納入這些標頭。

下列標頭檔包含 API、資料類型及通訊協定，由 Intune App SDK 提供開發人員使用：

-  IntuneMAMAppConfig.h
-  IntuneMAMAppConfigManager.h
-  IntuneMAMDataProtectionInfo.h
-  IntuneMAMDataProtectionManager.h
-  IntuneMAMDefs.h
-  IntuneMAMDiagnosticConsole.h
-  IntuneMAMEnrollmentDelegate.h
-  IntuneMAMEnrollmentManager.h
-  IntuneMAMEnrollmentStatus.h
-  IntuneMAMFileProtectionInfo.h
-  IntuneMAMFileProtectionManager.h
-  IntuneMAMLogger.h
-  IntuneMAMPolicy.h
-  IntuneMAMPolicyDelegate.h
-  IntuneMAMPolicyManager.h
-  IntuneMAMVersionInfo.h

開發人員只要匯入 IntuneMAM.h，即可使用先前標頭的內容


## <a name="how-the-intune-app-sdk-works"></a>Intune App SDK 的運作方式

Intune App SDK for iOS 的目標是以最少的程式碼變更，將管理功能加入 iOS 應用程式中。 程式碼變更越少，上市時間就越短，而不會影響行動應用程式的一致性與穩定性。


## <a name="build-the-sdk-into-your-mobile-app"></a>將 SDK 建置到行動應用程式

若要啟用 Intune App SDK，請遵循下列步驟：

1. **選項 1 - 架構 (建議使用)** ：如果您使用 Xcode 10.2+，且您的應用程式/延伸模組包含 Swift 代碼，請將 `IntuneMAMSwift.framework` 和 `IntuneMAMSwiftStub.framework` 連結至您的目標：將 `IntuneMAMSwift.framework` 和 `IntuneMAMSwiftStub.framework` 拖曳到專案目標的 [內嵌二進位檔]  清單。

    否則，請將 `IntuneMAM.framework` 連結至您的目標：將 `IntuneMAM.framework` 拖曳到專案目標的 [內嵌二進位檔]  清單。

   > [!NOTE]
   > 如果您使用架構，則必須先手動去除通用架構中的模擬器架構，再將應用程式提交至 App Store。 請參閱[將應用程式提交至 App Store](#submit-your-app-to-the-app-store) 以取得詳細資料。

   **選項 2 - 靜態程式庫**：此選項僅適用於不包含 Swift 代碼或以 10.2 版之前的 Xcode 建置的應用程式/延伸模組。 連結至 `libIntuneMAM.a` 程式庫。 將 `libIntuneMAM.a` 程式庫拖曳至專案目標的「Linked Frameworks and Libraries」(連結架構和程式庫)  清單中。

    ![Intune App SDK iOS：連結的架構和程式庫](./media/app-sdk-ios/intune-app-sdk-ios-linked-frameworks-and-libraries.png)

    將 `-force_load {PATH_TO_LIB}/libIntuneMAM.a` 新增至下列任一項中，並以 Intune App SDK 位置取代 `{PATH_TO_LIB}`：
   * 專案的 `OTHER_LDFLAGS` 組建組態設定。
   * Xcode UI 的 [Other Linker Flags] \(其他連結器旗標\)  。

     > [!NOTE]
     > 若要尋找 `PATH_TO_LIB`，請選取 `libIntuneMAM.a` 檔案，然後從 [檔案]  功能表中選擇 [取得資訊]  。 從 [資訊]  視窗的 [一般]  區段，複製並貼上 [位置]  資訊 (路徑)。

     拖曳 [Build Phases] (建置階段)  的 [Copy Bundle Resources] (複製配套資源)  下的資源配套，將 `IntuneMAMResources.bundle` 資源配套新增至專案。

     ![Intune App SDK iOS：複製配套資源](./media/app-sdk-ios/intune-app-sdk-ios-copy-bundle-resources.png)
         
2. 將下列 iOS 架構新增至專案：  
-  MessageUI.framework  
-  Security.framework  
-  MobileCoreServices.framework  
-  SystemConfiguration.framework  
-  libsqlite3.tbd  
-  libc++.tbd  
-  ImageIO.framework  
-  LocalAuthentication.framework  
-  AudioToolbox.framework  
-  QuartzCore.framework  
-  WebKit.framework

3. 如果尚未啟用 Keychain 共用，請在每個專案目標中選擇 [功能]  ，然後啟用「Keychain Sharing」(Keychain 共用)  參數來加以啟用。 您必須共用 Keychain 才能繼續進行下一個步驟。

   > [!NOTE]
   > 您的佈建設定檔必須能夠支援新的 Keychain 共用值。 Keychain 存取群組應該支援萬用字元。 若要確認這項作業，請在文字編輯器中開啟 .mobileprovision 檔案，並搜尋 **keychain-access-groups**，然後確認是否有萬用字元。 例如：
   >
   >  ```xml
   >  <key>keychain-access-groups</key>
   >  <array>
   >  <string>YOURBUNDLESEEDID.*</string>
   >  </array>
   >  ```

4. 啟用 Keychain 共用之後，請依照步驟建立另一個可供 Intune App SDK 儲存其資料的存取群組。 您可以使用 UI 或權利檔案來建立 Keychain 存取群組。 如果您是使用 UI 來建立 Keychain 存取群組，請務必遵循這些步驟：

     a. 如果您的行動應用程式未定義任何 Keychain 存取群組，請新增應用程式套件組合識別碼作為 [第一個]  群組。
    
    b. 將共用 Keychain 群組 `com.microsoft.intune.mam` 新增至現有的存取群組。 Intune App SDK 使用這個存取群組來儲存資料。
    
    c. 將 `com.microsoft.adalcache` 新增至現有存取群組。
    
      ![Intune App SDK iOS：Keychain 共用](./media/app-sdk-ios/intune-app-sdk-ios-keychain-sharing.png)
    
    d. 如果您正在直接編輯權利檔案，而不是使用上方所示的 Xcode UI 來建立 Keychain 存取群組，請將 `$(AppIdentifierPrefix)` 附加到 Keychain 存取群組 (Xcode 會自動處理此動作)。 例如：
    
      - `$(AppIdentifierPrefix)com.microsoft.intune.mam`
      - `$(AppIdentifierPrefix)com.microsoft.adalcache`
    
      > [!NOTE]
      > 權利檔案是行動應用程式特有的 XML 檔案。 它用來指定 iOS 應用程式內的特殊權限和功能。 如果您的應用程式之前沒有權利檔案，啟用 Keychain 共用 (步驟 3) 應該會使得 Xcode 為您的應用程式產生一個權利檔案。 請確定應用程式套件組合識別碼是清單中的第一個項目。

5. 請包含應用程式傳遞給應用程式 Info.plist 檔案之 `LSApplicationQueriesSchemes` 陣列中 `UIApplication canOpenURL` 的每個通訊協定。 繼續進行下一個步驟支援，請務必儲存您的變更。

6. 如果您的應用程式尚未使用 FaceID，請務必設定 [NSFaceIDUsageDescription Info.plist 索引鍵](https://developer.apple.com/library/archive/documentation/General/Reference/InfoPlistKeyReference/Articles/CocoaKeys.html#//apple_ref/doc/uid/TP40009251-SW75)的預設訊息。 iOS 需要此設定，才能讓使用者知道應用程式預計如何使用 FaceID。 Intune 應用程式防護原則設定在 IT 系統管理員的設定下，可使用 FaceID 作為應用程式存取方法。

7. 使用 [SDK 存放庫](https://github.com/msintuneappsdk/ms-intune-app-sdk-ios)中包含的 IntuneMAMConfigurator 工具來設定您應用程式的 Info.plist。 此工具有三個參數：

   |屬性|用法|
   |---------------|--------------------------------|
   |- i |  `<Path to the input plist>` |
   |- e | `<Path to the entitlements file>` |
   |- o |  (選擇性) `<Path to the output plist>` |

若未指定 '-o' 參數，將就地修改輸入檔案。 此工具是理想的，且應該在應用程式的 Info.plist 或權利變更時重新執行。 更新 Intune SDK 時，您也應該下載並執行此工具的最新版本，以免 Info.plist 設定需求在最新版本中有變更。

## <a name="configure-adalmsal"></a>設定 ADAL/MSAL

Intune App SDK 可將 [Azure Active Directory 驗證程式庫](https://github.com/AzureAD/azure-activedirectory-library-for-objc)或 [Microsoft 驗證程式庫](https://github.com/AzureAD/microsoft-authentication-library-for-objc)用於其驗證和條件式啟動案例。 針對不註冊裝置的管理情節，它也依賴 ADAL/MSAL 來向 MAM 服務註冊使用者身分識別。

一般而言，ADAL/MSAL 要求應用程式必須向 Azure Active Directory (AAD) 註冊並建立唯一用戶端識別碼與重新導向 URI，以確保授與應用程式的權杖安全無虞。 如果您的應用程式已經使用 ADAL 或 MSAL 來驗證使用者，該應用程式必須使用其現有的登錄值，並覆寫 Intune App SDK 預設值。 這能確保不會提示使用者驗證兩次 (一次是由 Intune App SDK，另一次是由應用程式)。

如果您的應用程式尚未使用 ADAL 或 MSAL，且您不需要存取任何 AAD 資源，當您選擇整合 ADAL 時，將無須在 AAD 中設定用戶端應用程式註冊。 如果您決定整合 MSAL，則必須設定應用程式註冊，並覆寫預設的 Intune 用戶端識別碼和重新導向 URI。  

建議您將應用程式連結至最新版本的 [ADAL](https://github.com/AzureAD/azure-activedirectory-library-for-objc/releases) 或 [MSAL](https://github.com/AzureAD/microsoft-authentication-library-for-objc/releases)。

### <a name="link-to-adal-or-msal-binaries"></a>連結至 ADAL 或 MSAL 二進位檔

**選項 1 -** 依照[這些步驟](https://github.com/AzureAD/azure-activedirectory-library-for-objc#download)，將您的應用程式連結至 ADAL 二進位檔。

**選項 2 -** 或者，您也可以依照[這些指示](https://github.com/AzureAD/microsoft-authentication-library-for-objc#installation)，將您的應用程式連結至 MSAL 二進位檔。

1. 如果您的應用程式未定義任何 Keychain 存取群組，請新增應用程式的配套識別碼作為第一個群組。

2. 透過將 `com.microsoft.adalcache` 新增到 Keychain 存取群組以啟用 ADAL/MSAL 單一登入 (SSO)。

3. 如果您明確地設定 ADAL 共用快取 keychain 群組，請確定它設為 `<appidprefix>.com.microsoft.adalcache`。 除非您覆寫這個項目，否則 ADAL 將為您進行設定。 如果您想要指定自訂 Keychain 群組以取代 `com.microsoft.adalcache`，請在 Info.plist 檔案的 IntuneMAMSettings 下使用 `ADALCacheKeychainGroupOverride` 索引鍵指定該行為。

### <a name="configure-adalmsal-settings-for-the-intune-app-sdk"></a>設定 Intune App SDK 的 ADAL/MSAL 設定

如果您的應用程式已經使用 ADAL 或 MSAL 來進行驗證，且擁有自己的 Azure Active Directory 設定，則您可以強制 Intune App SDK 在對 AAD 進行驗證期間使用相同的設定。 這能確保應用程式不會重複提示使用者進行驗證。 請參閱[設定 Intune App SDK 的設定](#configure-settings-for-the-intune-app-sdk)，以取得如何填入下列設定的相關資訊：  

* ADALClientId
* ADALAuthority
* ADALRedirectUri
* ADALRedirectScheme
* ADALCacheKeychainGroupOverride

如果您的應用程式已經使用 ADAL 或 MSAL，下列設定為必要：

1. 在專案的 Info.plist 檔案中，在 **IntuneMAMSettings** 字典下的索引鍵名稱 `ADALClientId` 處，指定要用於呼叫 ADAL 的用戶端識別碼。

2. 另外在 **IntuneMAMSettings** 字典下的索引鍵名稱 `ADALAuthority` 處，指定 Azure AD 授權。

3. 另外在 **IntuneMAMSettings** 字典下的索引鍵名稱 `ADALRedirectUri` 處，指定要用於呼叫 ADAL 的重新導向 URI。 此外，若應用程式的重新導向 URI 格式為 `scheme://bundle_id`，您也可以改為指定 `ADALRedirectScheme`。

此外，應用程式可以在執行階段覆寫這些 Azure AD 設定。 若要這樣做，請設定 `IntuneMAMPolicyManager` 執行個體上的 `aadAuthorityUriOverride`、`aadClientIdOverride` 與 `aadRedirectUriOverride` 屬性。

4. 請務必遵循將您的 iOS 應用程式權限授與應用程式保護原則 (APP) 服務的步驟。 使用[開始使用 Intune SDK 指南](app-sdk-get-started.md#next-steps-after-integration)中[將您的應用程式存取權授與 Intune 應用程式保護服務 (選擇性)](app-sdk-get-started.md#give-your-app-access-to-the-intune-app-protection-service-optional)中的指示。  

> [!NOTE]
> 建議您為靜態且不需要在執行階段決定的所有設定使用 Info.plist 方法。 指派給 `IntuneMAMPolicyManager` 屬性之值的優先順序高於在 Info.plist 中指定的對應值，而且在應用程式重新啟動之後仍然存在。 SDK 將會繼續為原則簽入使用它們，直到使用者取消註冊或值被清除或變更。

### <a name="if-your-app-does-not-use-adal-or-msal"></a>如果您的應用程式未使用 ADAL 或 MSAL

如前所述，Intune App SDK 可將 [Azure Active Directory 驗證程式庫](https://github.com/AzureAD/azure-activedirectory-library-for-objc)或 [Microsoft 驗證程式庫](https://github.com/AzureAD/microsoft-authentication-library-for-objc)用於其驗證和條件式啟動案例。 針對不註冊裝置的管理情節，它也依賴 ADAL/MSAL 來向 MAM 服務註冊使用者身分識別。 如果**您的應用程式未將 ADAL 或 MSAL 用於其本身的驗證機制**，您就可能必須根據您選擇要整合的驗證程式庫，來設定自訂 AAD 設定：   

ADAL - Intune App SDK 將會為 ADAL 參數提供預設值，並處理向 Azure AD 進行驗證的作業。 開發人員不需要為前述的 ADAL 設定指定任何值。 

MSAL - 開發人員必須在 AAD 中以[此處](https://github.com/AzureAD/microsoft-authentication-library-for-objc/wiki/Migrating-from-ADAL-Objective-C-to-MSAL-Objective-C#app-registration-migration)指定的格式，建立具有自訂重新導向 URI 的應用程式註冊。 開發人員應該設定先前所述的 `ADALClientID` 和 `ADALRedirectUri` 設定，或 `IntuneMAMPolicyManager` 實例上對等的 `aadClientIdOverride` 和 `aadRedirectUriOverride` 屬性。 開發人員也應確實依照上一節中的步驟 4，將其應用程式存取權授與 Intune 應用程式保護服務。

### <a name="special-considerations-when-using-msal"></a>使用 MSAL 時的特殊考量 

1. **檢查您的 Webview** - 建議應用程式不應以 SFSafariViewController、SFAuthSession 或 ASWebAuthSession 作為任何應用程式起始的 MSAL 互動式驗證作業的 Webview。 如果基於某些原因，您的應用程式必須使用其中一個網站進行互動式 MSAL 驗證作業，則它也必須在應用程式的資訊 plist 中，將 `IntuneMAMSettings` 字典下的 `SafariViewControllerBlockedOverride` 設定為 `true`。 警告：這將會關閉 Intune 用來啟用驗證工作階段的 SafariViewController 勾點。 如果應用程式使用 SafariViewController 來檢視公司資料，此做法將會導致應用程式的其他位置出現資料外洩風險，因此應用程式不應以任何此類 Webview 類型顯示公司資料。
2. **同時連結 ADAL 和 MSAL** - 在此情況下，開發人員必須選擇是否要讓 Intune 優先使用 MSAL (而非 ADAL)。 根據預設，如果在執行階段同時連結了支援的 ADAL 版本和支援的 MSAL 版本，Intune 將會優先使用前者。 只有在 `NSUserDefaults` 中的 `IntuneMAMUseMSALOnNextLaunch` 為 `true` 時 (在 Intune 第一次執行驗證作業時)，Intune 才會優先使用支援的 MSAL 版本。 如果 `IntuneMAMUseMSALOnNextLaunch` 為 `false` 或未設定，Intune 將會回復為預設行為。 我們可以從名稱看出，`IntuneMAMUseMSALOnNextLaunch` 的變更將會在下次啟動時生效。


## <a name="configure-settings-for-the-intune-app-sdk"></a>設定 Intune App SDK 的設定

您可以使用應用程式 Info.plist 檔案中的 **IntuneMAMSettings** 字典，以設定 Intune App SDK。 如果 Info.plist 檔案中看不到 IntuneMAMSettings 字典，您應該加以建立。

在 IntuneMAMSettings 字典下，您可以進行下列支援的設定來設定 Intune App SDK。

其中一些設定可能在前幾節中討論過，而且有些設定並不適用於所有應用程式。

設定  | 類型  | 定義 | 必要？
--       |  --   |   --       |  --
ADALClientId  | 字串  | 應用程式的 Azure AD 用戶端識別碼。 | 所有使用 MSAL 的應用程式，以及任何存取非 Intune AAD 資源的 ADAL 應用程式都需要。 |
ADALAuthority | 字串 | 應用程式的使用中 Azure AD 授權單位。 您應該使用已設定 AAD 帳戶的專屬環境。 | 如果應用程式使用 ADAL 或 MSAL 來存取非 Intune AAD 資源，則為必要。 如果此值不存在，則會使用 Intune 預設值。|
ADALRedirectUri  | 字串  | 應用程式的 Azure AD 重新導向 URI。 | 所有使用 MSAL 的應用程式，以及任何存取非 Intune AAD 資源的 ADAL 應用程式，都需要 ADALRedirectUri 或 ADALRedirectScheme。  |
ADALRedirectScheme  | 字串  | 應用程式的 Azure AD 重新導向配置。 如果應用程式的重新導向 URI 格式為 `scheme://bundle_id`，則這可以用來代替 ADALRedirectUri。 | 所有使用 MSAL 的應用程式，以及任何存取非 Intune AAD 資源的 ADAL 應用程式，都需要 ADALRedirectUri 或 ADALRedirectScheme。 |
ADALLogOverrideDisabled | 布林值  | 指定 SDK 是否會將所有 ADAL/MSAL 記錄 (包括任何來自應用程式的 ADAL 呼叫) 路由傳送至自己的記錄檔。 預設為 [否]。 如果應用程式將設定自己的 ADAL/MSAL 記錄回呼，請設定為 [是]。 | 選擇性。 |
ADALCacheKeychainGroupOverride | 字串  | 指定要用於 ADAL/MSAL 快取而非 "com.microsoft.adalcache" 的 Keychain 群組。 請注意，這不包含 app-id 前置詞。 這會在執行階段加在所提供字串的前面。 | 選擇性。 |
AppGroupIdentifiers | 字串陣列  | 應用程式之權利 com.apple.security.application-groups 區段中的應用程式群組陣列。 | 如果應用程式使用應用程式群組，則為必要項。 |
ContainingAppBundleId | 字串 | 指定含有應用程式之擴充功能的配套識別碼。 | 對 IOS 擴充功能而言為必要項。 |
DebugSettingsEnabled| 布林值 | 如果設定為 [是]，則可以套用 [設定] 配套內的測試原則。 啟用這個設定時，*不*應該提供應用程式。 | 選擇性。 預設為 [否]。 |
AutoEnrollOnLaunch| 布林值| 指定如果偵測到現有的受管理身分識別，而且其尚未註冊，應用程式是否要在啟動時嘗試自動註冊。 預設為 [否]。 <br><br> 注意：若找不到受控識別，或 ADAL/MSAL 快取中沒有身分識別的有效權杖，除非應用程式也已經將 MAMPolicyRequired 設定為 [是]，否則註冊嘗試會以無訊息方式失敗且不提示輸入認證。 | 選擇性。 預設為 [否]。 |
MAMPolicyRequired| 布林值| 指定應用程式在沒有 Intune 應用程式保護原則時，是否無法予以啟動。 預設為 [否]。 <br><br> 注意：MAMPolicyRequired 設定為 YES 時，無法將應用程式提交至 App Store。 當 MAMPolicyRequired 設定為 [是] 時，AutoEnrollOnLaunch 也應該設定為 [是]。 | 選擇性。 預設為 [否]。 |
MAMPolicyWarnAbsent | 布林值| 指定應用程式在沒有 Intune 應用程式保護原則時，是否將在啟動期間警告使用者。 <br><br> 附註：在關閉警告之後，將仍允許使用者在沒有原則的情況下使用應用程式。 | 選擇性。 預設為 [否]。 |
MultiIdentity | 布林值| 指定應用程式是否為多重身分識別感知。 | 選擇性。 預設為 [否]。 |
SafariViewControllerBlockedOverride | 布林值| 停用 Intune 透過 SFSafariViewController、SFAuthSession 或 ASWebAuthSession 來啟用 MSAL 驗證的 SafariViewController 勾點。 | 選擇性。 預設為 [否]。 警告：如果使用不當，可能會導致資料外洩。 請在絕對必要時才啟用。 如需詳細資訊，請參閱[使用 MSAL 時的特殊考量](#special-considerations-when-using-msal)。  |
SplashIconFile <br>IntuneMAMSettings | 字串  | 指定 Intune 啟動顯示 (啟動) 畫面的圖示檔。 | 選擇性。 |
SplashDuration | 數字 | Intune 啟動畫面將於應用程式啟動時顯示的最短時間 (以秒為單位)。 預設為 1.5。 | 選擇性。 |
BackgroundColor| 字串| 指定 Intune SDK UI 元件的背景色彩。 接受格式為 #XXXXXX 的十六進位 RGB 字串，其中 X 的範圍可以是 0-9 或 A-F。 可能會省略井字號。   | 選擇性。 預設為系統背景色彩，這可能會隨著 iOS 版本的不同和 iOS 深色模式設定而改變。 |
ForegroundColor| 字串| 指定 Intune SDK UI 元件的前景色彩，例如文字色彩。 接受格式為 #XXXXXX 的十六進位 RGB 字串，其中 X 的範圍可以是 0-9 或 A-F。 可能會省略井字號。  | 選擇性。 預設為系統標籤色彩，這可能會隨著 iOS 版本的不同和 iOS 深色模式設定而改變。 |
AccentColor | 字串| 指定 Intune SDK UI 元件的輔色，例如按鈕文字色彩和 PIN 方塊醒目提示色彩。 接受格式為 #XXXXXX 的十六進位 RGB 字串，其中 X 的範圍可以是 0-9 或 A-F。 可能會省略井字號。| 選擇性。 預設為系統藍色。 |
SupportsDarkMode| 布林值 | 指定在未明確設定 BackgroundColor/ForegroundColor/AccentColor 值的情況下，Intune SDK 的 UI 色彩配置是否應採用系統深色模式設定 | 選擇性。 預設為 Yes。 |
MAMTelemetryDisabled| 布林值| 指定 SDK 是否不會將任何遙測資料傳送至其後端。| 選擇性。 預設為 [否]。 |
MAMTelemetryUsePPE | 布林值 | 指定 MAM SDK 是否會將資料傳送至 PPE 遙測後端。 如果使用 Intune 原則測試應用程式，讓測試遙測資料與客戶資料不混合使用，請使用此選項。 | 選擇性。 預設為 [否]。 |
MaxFileProtectionLevel | 字串 | 選擇性。 允許應用程式指定其可支援的最大 `NSFileProtectionType`。 如果層級高於應用程式可支援的層級，此值會覆寫服務所傳送的原則。 可能的值：`NSFileProtectionComplete`、`NSFileProtectionCompleteUnlessOpen`、`NSFileProtectionCompleteUntilFirstUserAuthentication`、`NSFileProtectionNone`。|
OpenInActionExtension | 布林值 | 設為 [是] 可取得 Open in Action 延伸模組。 如需詳細資訊，請參閱透過＜透過 UIActivityViewController 共用資料＞一節。 |
WebViewHandledURLSchemes | 字串陣列 | 指定您應用程式的 WebView 所處理的 URL 配置。 | 如果您的應用程式使用透過連結及 (或) JavaScript 處理 URL 的 WebView，則為必要項。 |

## <a name="receive-app-protection-policy"></a>接收應用程式保護原則

### <a name="overview"></a>概觀

若要接收 Intune 應用程式保護原則，應用程式必須向 Intune MAM 服務起始註冊要求。 應用程式可以在 Intune 主控台中設定，以接收應用程式保護原則 (不論是否有裝置註冊)。 無註冊的應用程式保護原則 (亦稱為 **APP-WE** 或 MAM-WE) 可讓 Intune 管理應用程式，而不需要向 Intune 行動裝置管理 (MDM) 註冊裝置。 在這兩種案例中，都必須向 Intune MAM 服務註冊才能接收原則。

> [!Important]
> 適用於 iOS 的 Intune App SDK 將會在應用程式保護原則啟用加密時，使用 256 位元的加密金鑰。 所有應用程式都必須有最新的 SDK 版本，才能共用受保護資料。

### <a name="apps-that-already-use-adal-or-msal"></a>已使用 ADAL 或 MSAL 的應用程式

使用者成功驗證之後，已使用 ADAL 或 MSAL 的應用程式應該呼叫 `IntuneMAMEnrollmentManager` 執行個體上的 `registerAndEnrollAccount` 方法：

```objc
/*
 *  This method will add the account to the list of registered accounts.
 *  An enrollment request will immediately be started.
 *  @param identity The UPN of the account to be registered with the SDK
 */

(void)registerAndEnrollAccount:(NSString *)identity;
```

藉由呼叫 `registerAndEnrollAccount` 方法，SDK 將註冊使用者帳戶，並代表這個帳戶嘗試註冊應用程式。 如果註冊因任何原因而失敗，SDK 將自動在 24 個小時之後重新嘗試註冊。 基於偵錯目的，應用程式可以透過委派來接收有關任何註冊要求結果的[通知](#status-result-and-debug-notifications)。

叫用這個 API 之後，應用程式可以繼續正常運作。 如果註冊成功，SDK 將通知使用者：需要重新啟動應用程式。 此時，使用者可以立即重新啟動應用程式。

```objc
[[IntuneMAMEnrollmentManager instance] registerAndEnrollAccount:@”user@foo.com”];
```

### <a name="apps-that-do-not-use-adal-or-msal"></a>不使用 ADAL 或 MSAL 的應用程式

不使用 ADAL 或 MSAL 登入使用者的應用程式，仍然可以從 Intune MAM 服務接收應用程式保護原則，方法是呼叫 API 讓 SDK 處理該驗證。 如果應用程式尚未向 Azure AD 驗證使用者，但仍需要擷取應用程式保護原則以協助保護資料，則應用程式應該使用這項技術。 例如：如果正在使用另一個驗證服務進行應用程式登入，或者，如果應用程式根本不支援登入。 若要這樣做，應用程式可以在 `IntuneMAMEnrollmentManager` 執行個體上呼叫 `loginAndEnrollAccount` 方法：

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

如果註冊失敗，應用程式應該考慮根據失敗詳細資料，在未來重新呼叫這個 API。 應用程式可以透過委派來接收有關任何註冊要求結果的[通知](#status-result-and-debug-notifications)。

叫用這個 API 之後，應用程式可以繼續正常運作。 如果註冊成功，SDK 將通知使用者：需要重新啟動應用程式。

範例：

```objc
[[IntuneMAMEnrollmentManager instance] loginAndEnrollAccount:@”user@foo.com”];
```

### <a name="let-intune-handle-authentication-and-enrollment-at-launch"></a>讓 Intune 處理啟動時的驗證和註冊

如果您想要在應用程式完成啟動之前，讓 Intune SDK 處理所有使用 ADAL/MSAL 的驗證及註冊，而且您的應用程式一律需要應用程式原則，您不需要使用 `loginAndEnrollAccount` API。 只要在應用程式 Info.plist 的 IntuneMAMSettings 字典中，將下列兩項設定設為 [是] 即可。

設定  | 類型  | 定義 |
--       |  --   |   --       |  
AutoEnrollOnLaunch| 布林值| 指定如果偵測到現有的受管理身分識別，而且其尚未註冊，應用程式是否要在啟動時嘗試自動註冊。 預設為 [否]。 <br><br> 附註：若找不到受控識別，或 ADAL/MSAL 快取中沒有身分識別的有效權杖，除非應用程式也已經將 MAMPolicyRequired 設定為 [是]，否則註冊嘗試會以無訊息方式失敗且不提示輸入認證。 |
MAMPolicyRequired| 布林值| 指定應用程式在沒有 Intune 應用程式保護原則時，是否無法予以啟動。 預設為 [否]。 <br><br> 附註：MAMPolicyRequired 設定為 YES 時，無法將應用程式提交至 App Store。 當 MAMPolicyRequired 設定為 [是] 時，AutoEnrollOnLaunch 也應該設定為 [是]。 |

如果您針對應用程式選擇此選項，則不需要在註冊後處理重新啟動您的應用程式。

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
 *  until the Intune APP AAD token is acquired, then return.  This method must be called before  
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

* 註冊要求
* 原則更新要求
* 取消註冊要求

透過 `IntuneMAMEnrollmentDelegate.h` 中的委派方法來呈現通知：

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

* 與要求相關聯之帳戶的身分識別
* 表示要求結果的狀態碼
* 狀態碼描述的錯誤字串
* `NSError` 物件。 這個物件與可傳回的特定狀態碼定義在 `IntuneMAMEnrollmentStatus.h` 中。

### <a name="sample-code"></a>範例程式碼

下列是委派方法的範例實作：

```objc
- (void)enrollmentRequestWithStatus:(IntuneMAMEnrollmentStatus*)status
{
    NSLog(@"enrollment result for identity %@ with status code %ld", status.identity, (unsigned long)status.statusCode);
    NSLog(@"Debug Message: %@", status.errorString);
}

- (void)policyRequestWithStatus:(IntuneMAMEnrollmentStatus*)status
{
    NSLog(@"policy check-in result for identity %@ with status code %ld", status.identity, (unsigned long)status.statusCode);
    NSLog(@"Debug Message: %@", status.errorString);
}

- (void)unenrollRequestWithStatus:(IntuneMAMEnrollmentStatus*)status
{
    NSLog(@"un-enroll result for identity %@ with status code %ld", status.identity, (unsigned long)status.statusCode);
    NSLog(@"Debug Message: %@", status.errorString);
}
```

## <a name="application-restart"></a>應用程式重新啟動

應用程式第一次收到 MAM 原則時，必須重新啟動，才能套用必要的勾點。 為了通知需要重新啟動的應用程式，SDK 在 `IntuneMAMPolicyDelegate.h` 中提供委派方法。

```objc
 - (BOOL) restartApplication
```

這個方法的傳回值會指示 SDK，應用程式是否必須處理必要的重新啟動：

* 如果傳回 true，應用程式就必須處理重新啟動。

* 如果傳回 false，則 SDK 將在傳回這個方法之後重新啟動應用程式。 SDK 會立即顯示一個對話方塊，指示使用者重新啟動應用程式。

## <a name="customize-your-apps-behavior-with-apis"></a>使用 API 自訂您的應用程式行為

Intune App SDK 中有多個 API，您可以呼叫以取得部署至應用程式之 Intune 應用程式原則的相關資訊。 您可以使用這項資料來自訂您的應用程式行為。 下表提供您將使用之一些基本 Intune 類別的相關資訊。

執行個體 | 說明
----- | -----------
IntuneMAMPolicyManager.h | IntuneMAMPolicyManager 類別會公開部署至應用程式的 Intune 應用程式原則。 值得注意的是，它會公開適用於[啟用多重身分識別](app-sdk-ios.md#enable-multi-identity-optional)的 API。 |
IntuneMAMPolicy.h | IntuneMAMPolicy 類別會公開套用至應用程式的一些 MAM 原則設定。 這些原則會公開，讓應用程式可以自訂其 UI。 大多數原則設定是由 SDK 強制執行，而不是應用程式。 應用程式應該實作的唯一設定是「另存新檔」控制項。 這個類別會公開實作另存新檔所需的部分 API。 |
IntuneMAMFileProtectionManager.h | IntuneMAMFileProtectionManager 類別會公開應用程式可用來根據所提供身分識別明確保護檔案和目錄的 API。 身分識別可以受 Intune 管理或未受管理，而且 SDK 會套用適當的 MAM 原則。 使用此類別是選擇性的。 |
IntuneMAMDataProtectionManager.h | IntuneMAMDataProtectionManager 類別會公開應用程式可用來根據所提供身分識別保護資料緩衝區的 API。 身分識別可以受 Intune 管理或未受管理，而且 SDK 會適當地套用加密。 |

## <a name="implement-save-as-and-open-from-controls"></a>實作另存新檔和開啟來源控制項

Intune 可讓 IT 系統管理員選取受管理的應用程式可儲存資料或從中開啟資料的儲存位置。 應用程式可以使用 `IntuneMAMPolicy.h` 中定義的 `isSaveToAllowedForLocation` API 向 Intune MAM SDK 查詢所能使用的儲存目標儲存位置。 應用程式也可以使用 `IntuneMAMPolicy.h` 中定義的 `isOpenFromAllowedForLocation` API 向 Intune MAM SDK 查詢所能使用的開啟來源儲存位置。

應用程式必須先向 `isSaveToAllowedForLocation` API 查詢，確認 IT 系統管理員是否允許將資料另存於其他位置，才能將受管理的資料儲存到雲端儲存體或本機位置。
應用程式必須先向 `isOpenFromAllowedForLocation` API 確認 IT 系統管理員是否允許從雲端儲存體或本機位置開啟資料，才能從該處開啟資料。

應用程式在使用 `isSaveToAllowedForLocation` 或 `isOpenFromAllowedForLocation` API 時，必須傳入儲存位置的 UPN (如有使用)。

### <a name="supported-save-locations"></a>支援的儲存位置

`isSaveToAllowedForLocation` API 提供常數以確認 IT 系統管理員是否可將資料儲存到 `IntuneMAMPolicy.h` 中定義的下列位置：

* IntuneMAMSaveLocationOther
* IntuneMAMSaveLocationOneDriveForBusiness
* IntuneMAMSaveLocationSharePoint
* IntuneMAMSaveLocationLocalDrive
* IntuneMAMSaveLocationAccountDocument

應用程式應使用 `isSaveToAllowedForLocation` 的常數確認是否可以將資料另存於其他被視為「受管理」(例如商務用 OneDrive) 或「個人」的位置。 此外，當應用程式無法確認位置為「受管理」或「個人」的位置時，也應使用 API。

若應用程式會將資料儲存到本機裝置上的任何位置，則應使用 `IntuneMAMSaveLocationLocalDrive` 常數。

如果目的地位置的帳戶不明，則應傳遞 `nil`。 `IntuneMAMSaveLocationLocalDrive` 位置應一律與 `nil` 帳戶配對。

### <a name="supported-open-locations"></a>支援的開啟位置

`isOpenFromAllowedForLocation` API 會提供常數以確認 IT 系統管理員是否允許從 `IntuneMAMPolicy.h` 中定義的下列位置開啟資料。

* IntuneMAMOpenLocationOther
* IntuneMAMOpenLocationOneDriveForBusiness
* IntuneMAMOpenLocationSharePoint
* IntuneMAMOpenLocationCamera
* IntuneMAMOpenLocationLocalStorage
* IntuneMAMOpenLocationAccountDocument

應用程式應使用 `isOpenFromAllowedForLocation` 中的常數，以確認是否可從被視為「受管理」 (例如商務用 OneDrive) 或「個人」的位置開啟資料。 此外，當應用程式無法確認位置是否為「受管理」或「個人」的位置時，也應使用 API。

當應用程式從相機或相簿開啟資料時，應使用 `IntuneMAMOpenLocationCamera` 常數。

當應用程式從本機裝置上的任何位置開啟資料時，應使用 `IntuneMAMOpenLocationLocalStorage` 常數。

當應用程式開啟具有受管理帳戶識別的文件時，應使用 `IntuneMAMOpenLocationAccountDocument` 常數 (請參閱後續的「共用資料」一節)

如果來源位置的帳戶不明，則應傳遞 `nil`。 `IntuneMAMOpenLocationLocalStorage` 和 `IntuneMAMOpenLocationCamera` 位置應一律與 `nil` 帳戶配對。

### <a name="unknown-or-unlisted-locations"></a>不明或未列出的位置

當所需的位置未列在 `IntuneMAMSaveLocation` 或 `IntuneMAMOpenLocation` 列舉中或不明時，應使用兩個位置的其中一個。
* 如果使用受管理的帳戶來存取儲存位置，則應使用 `IntuneMAMSaveLocationAccountDocument` 位置 (開啟位置為 `IntuneMAMOpenLocationAccountDocument`)。
* 否則，請使用 `IntuneMAMSaveLocationOther` 位置 (開啟位置為 `IntuneMAMOpenLocationOther`)。

請務必清楚區分受管理的帳戶與共用受管理帳戶 UPN 的帳戶。 例如，以 UPN "user@contoso.com" 登入 OneDrive 的受管理帳戶，與使用 UPN "user@contoso.com" 登入 Dropbox 的帳戶並不相同。 若藉由登入受管理的帳戶 (例如，登入 OneDrive 的 "user@contoso.com") 來存取不明或未列出的服務，則應以 `AccountDocument` 位置加以表示。 如果不明或未列出的服務透過另一個帳戶 (例如，登入 Dropbox 的 "user@contoso.com") 登入，該服務將不會存取受管理帳戶的位置，而應以 `Other` 位置加以表示。

### <a name="sharing-blocked-alert"></a>封鎖共用警示

在呼叫 `isSaveToAllowedForLocation` 或 `isOpenFromAllowedForLocation` API 時若發現該 API 封鎖了儲存/開啟動作，可以使用 UI Helper 函式。 應用程式若要通知使用者該動作已遭封鎖，可以呼叫 `IntuneMAMUIHelper.h` 中定義的 `showSharingBlockedMessage` API，以顯示含有一般訊息的警示檢視。

## <a name="share-data-via-uiactivityviewcontroller"></a>透過 UIActivityViewController 共用資料

從 8.0.2 版開始，Intune APP SDK 可篩選 `UIActivityViewController` 動作，因此只能選取受 Intune 管理的共用位置。 此行為將由應用程式資料轉送原則所控制。

### <a name="copy-to-actions"></a>「複製到」動作

當透過 `UIActivityViewController` 和 `UIDocumentInteractionController` 共用文件時，iOS 會針對支援開啟已共用文件的每個應用程式，顯示「複製到」動作。 應用程式會透過其 Info.plist 中的 `CFBundleDocumentTypes` 設定，宣告它們支援的文件類型。 如果原則不允許共用到未受控的應用程式，則此類型的共用將無法再使用。 替代方案是，使用者必須將非 UI 動作延伸模組新增至其應用程式，並連結到 Intune App SDK。 動作延伸模組只是虛設常式。 SDK 會實作檔案共用行為。 遵循下列步驟：

1. 您的應用程式必須在其 Info.plist `CFBundleURLTypes` 下至少定義一個 schemeURL。

2. 您的應用程式和動作延伸模組至少必須共用一個應用程式群組，而且應用程式群組必須列在應用程式和延伸模組 IntuneMAMSettings 字典下的 `AppGroupIdentifiers` 陣列下。

3. 將動作延伸模組命名為「以 ... 開啟」，其中 ... 是應用程式名稱。 視需要將 Info.plist 當地語系化。

4. 提供延伸模組的範本圖示，如同 [Apple 開發人員文件](https://developer.apple.com/ios/human-interface-guidelines/extensions/sharing-and-actions/)所述。 或者，可使用 IntuneMAMConfigurator 工具，從應用程式的 .app 目錄中產生這些影像。 若要這樣做，請執行：

    ```bash
    IntuneMAMConfigurator -generateOpenInIcons /path/to/app.app -o /path/to/output/directory
    ```

5. 在延伸模組的 Info.plist 中的 IntuneMAMSettings 下，新增名為 `OpenInActionExtension` 的布林值設定，且其值為 YES。

6. 從應用程式的 `CFBundleDocumentTypes` 加上 `com.microsoft.intune.mam` 為開頭，設定 `NSExtensionActivationRule` 以支援單一檔案和所有類型。 例如，如果應用程式支援 public.text 和 public.image，則啟用規則將會是：

    ```objc
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

如果您的應用程式已包含共用或動作延伸模組，則必須修改其 `NSExtensionActivationRule` 以允許 Intune 類型。 針對延伸模組支援的每個類型，新增開頭加上 `com.microsoft.intune.mam` 的額外類型。 例如，如果現有的啟用規則是：  

```objc
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

```objc
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
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "com.microsoft.intune.mam.public.data"
    ).@count > 0
).@count > 0
```

> [!NOTE]
> IntuneMAMConfigurator 工具可用來將 Intune 類型新增至啟用規則。 如果您現有的啟用規則使用預先定義的字串常數 (例如 NSExtensionActivationSupportsFileWithMaxCount、NSExtensionActivationSupportsText 等)，那麼述詞語法可能變得相當複雜。 IntuneMAMConfigurator 工具也可用來在新增 Intune 類型時，將啟用規則從字串常數轉換成述詞字串。

### <a name="what-the-ui-should-look-like"></a>UI 應該看起來像這樣

舊的 UI：

![共用資料 - iOS 舊的共用 UI](./media/app-sdk-ios/sharing-UI-old.png)

新的 UI：

![共用資料 - iOS 新的共用 UI](./media/app-sdk-ios/sharing-UI-new.png)

## <a name="enable-targeted-configuration-appmam-app-config-for-your-ios-applications"></a>啟用 iOS 應用程式的目標設定 (APP/MAM 應用程式設定)

MAM 目標設定 (也稱為 MAM 應用程式設定) 可讓應用程式透過 Intune SDK 接收設定資料。 應用程式擁有者/開發人員必須定義此資料的格式和變化，並向 Intune 客戶溝通。

Intune 系統管理員可以透過 Intune Azure 入口網站和 Intune Graph API 為設定資料設定目標並進行部署。 從 Intune App SDK for iOS 7.0.1 版開始，可以透過 MAM 服務提供 MAM 目標設定資料給參與 MAM 目標設定的應用程式。 應用程式設定資料是透過我們的 MAM 服務 (而非透過 MDM 通道) 直接向應用程式發佈。 Intune App SDK 會提供類別來存取從這些主控台擷取的資料。 下列項目為必要條件：

* 應用程式必須向 Intune MAM 服務註冊，您才能存取 MAM 目標設定 UI。 如需詳細資訊，請參閱[接收應用程式保護原則](#receive-app-protection-policy)。

* 在應用程式的原始程式檔中包含 `IntuneMAMAppConfigManager.h`。

* 呼叫 `[[IntuneMAMAppConfigManager instance] appConfigForIdentity:]` 以取得應用程式設定物件。

* 在 `IntuneMAMAppConfig` 物件上呼叫適當的選取器。 例如，如果您的應用程式金鑰是字串，您會想要使用 `stringValueForKey` 或 `allStringsForKey`。 如需傳回值和錯誤條件的詳細說明，請參閱 `IntuneMAMAppConfig.h`。

如需圖形 API 功能的詳細資訊，請參閱[圖形 API 參考](https://developer.microsoft.com/graph/docs/concepts/overview)。

如需如何在 iOS 建立 MAM 目標應用程式設定原則的詳細資訊，請參閱 [How to use Microsoft Intune app configuration policies for iOS](../apps/app-configuration-policies-use-ios.md) (如何使用適用於 iOS 的 Microsoft Intune 應用程式設定原則) 的＜MAM 目標應用程式設定＞一節。

## <a name="telemetry"></a>遙測

根據預設，Intune App SDK for iOS 會收集下列事件類型的相關遙測：

* **應用程式啟動**：協助 Microsoft Intune 依管理類型 (含 MDM 的 MAM、不含 MDM 註冊的 MAM 等) 了解啟用 MAM 功能的應用程式使用情況。

* **註冊呼叫**：協助 Microsoft Intune 了解從用戶端起始的註冊呼叫成功率和其他效能計量。

* **Intune 動作**：為了協助診斷問題並確保 Intune 功能，我們會收集 Intune SDK 動作的相關資訊。

> [!NOTE]
> 如果您選擇不要將 Intune App SDK 遙測資料從您的行動應用程式傳送至 Microsoft Intune，您必須停用 Intune App SDK 遙測擷取。 在 IntuneMAMSettings 字典中將 `MAMTelemetryDisabled` 屬性設定為 [是]。

## <a name="enable-multi-identity-optional"></a>啟用多重身分識別 (選擇性)

SDK 預設會將原則套用至應用程式整體。 多重身分識別是 MAM 功能，您可啟用以將原則套用至每個身分識別層級。 這需要的應用程式參與高於其他 MAM 功能。

當應用程式想要變更作用中身分識別時，必須通知 APP SDK。 需要身分識別變更時，SDK 也會通知應用程式。 目前僅支援一個受管理的身分識別。 使用者註冊裝置或應用程式之後，SDK 會使用這個身分識別，並將其視為主要受管理身分識別。 應用程式中的其他使用者則會因不受限制原則設定而視為不受管理。

請注意，身分識別只會定義為字串。 身分識別不區分大小寫。 身分識別的 SDK 要求可能不會傳回設定身分識別時原本使用的相同大小寫。

### <a name="identity-overview"></a>身分識別概觀

身分識別就是帳戶的使用者名稱 (例如 user@contoso.com)。 開發人員可以設定應用程式在下列層級的身分識別：

* **處理序身分識別**：設定全處理序的身分識別，並主要用於單一身分識別應用程式。 這個身分識別會影響所有工作、檔案和 UI。

* **UI 身分識別**：決定在主要執行緒的 UI 工作 (例如剪下/複製/貼上、PIN、驗證和資料共用) 上套用的原則。 UI 身分識別不會影響檔案工作，例如加密和備份。

* **執行緒身分識別**：影響在目前執行緒上套用的原則。 這個身分識別會影響所有工作、檔案和 UI。

不論使用者是否受管理，應用程式都必須負責適當地設定身分識別。

在任何時間，每個執行緒都會有 UI 工作和檔案工作的有效身分識別。 這是用來確認應該套用哪些原則 (如果有的話) 的身分識別。 如果身分識別是 [沒有身分識別]，或使用者未受管理，則不會套用任何原則。 下列圖表顯示如何決定有效的身分識別。

  ![Intune App SDK iOS：身分識別判斷流程](./media/app-sdk-ios/ios-thread-identities.png)

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

### <a name="turn-on-multi-identity"></a>開啟多重身分識別

預設會將應用程式視為單一身分識別。 SDK 會將處理序身分識別設定為已註冊的使用者。 若要啟用多重身分識別支援，請將名稱為 `MultiIdentity` 且值為 [是] 的布林設定新增至應用程式 Info.plist 檔案中的 IntuneMAMSettings 字典。

> [!NOTE]
> 啟用多重身分識別時，處理序身分識別、UI 身分識別和執行緒身分識別都會設定為 nil。 應用程式必須負責正確設定它們。

### <a name="switch-identities"></a>切換身分識別

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

### <a name="are-all-of-the-apis-addressable-through-native-swift-or-the-objective-c-and-swift-interoperability"></a>是否可透過原生 Swift 或 Objective-C 以及 Swift 互通性定址所有 API？

Intune App SDK API 僅限於 Objective-C 且不支援原生  Swift。 必須有 Swift 與 Objective-C 的互通性。

### <a name="do-all-users-of-my-application-need-to-be-registered-with-the-app-we-service"></a>是否需要向 APP-WE 服務註冊應用程式的所有使用者？

否。 事實上，只應該向 Intune App SDK 註冊工作或學校帳戶。 應用程式負責決定是否在工作或學校內容中使用帳戶。

### <a name="what-about-users-that-have-already-signed-in-to-the-application-do-they-need-to-be-enrolled"></a>已登入應用程式的使用者如何？ 是否需要註冊它們？

應用程式必須負責註冊已成功通過驗證的使用者。 應用程式也必須負責註冊在應用程式具有較少 MDM 的 MAM 功能之前可能已存在的任何現有帳戶。

若要這樣做，應用程式應該會使用 `registeredAccounts:` 方法。 這個方法會傳回包含所有已註冊至 Intune MAM 服務之帳戶的 NSDictionary。 如果應用程式中的任何現有帳戶都不在清單中，則應用程式應該透過 `registerAndEnrollAccount:` 來註冊這些帳戶。

### <a name="how-often-does-the-sdk-retry-enrollments"></a>SDK 重試註冊的頻率為何？

SDK 會依 24 小時間隔自動重試所有先前失敗的註冊。 SDK 這麼做以確保如果使用者的組織已在使用者登入應用程式之後啟用 MAM，則使用者會順利註冊並接收原則。

SDK 將會在偵測到使用者已順利註冊應用程式時停止重試。 原因是只有一位使用者可以在特定時間註冊應用程式。 如果取消註冊使用者，則重試會以相同的 24 小時間隔重新開始。

### <a name="why-does-the-user-need-to-be-deregistered"></a>為何需要取消註冊使用者？

SDK 將會在背景定期採取下列動作：

* 如果尚未註冊應用程式，則會每隔 24 小時嘗試註冊所有已註冊的帳戶。
* 如果已註冊應用程式，SDK 會每隔 8 小時檢查 MAM 原則更新。

取消註冊使用者會通知 SDK，使用者無法再使用應用程式，而且 SDK 可以停止該使用者帳戶的任何定期事件。 它也會在必要時觸發應用程式取消註冊和選擇性抹除。

### <a name="should-i-set-the-dowipe-flag-to-true-in-the-deregister-method"></a>是否應該將 deregister 方法中的 doWipe 旗標設為 true？

將使用者登出應用程式之前，應該呼叫這個方法。  如果在登出時於應用程式中刪除使用者的資料，則 `doWipe` 可以設為 false。 不過，如果應用程式未移除使用者的資料，則 `doWipe` 應該設為 true，讓 SDK 可以刪除資料。

### <a name="are-there-any-other-ways-that-an-application-can-be-un-enrolled"></a>是否有任何其他方式可以取消註冊應用程式？

是，IT 系統管理員可以將選擇性抹除命令傳送給應用程式， 以取消註冊使用者以及抹除使用者資料。 SDK 會自動處理這種情況，並透過取消註冊委派方法來傳送通知。

### <a name="is-there-a-sample-app-that-demonstrates-how-to-integrate-the-sdk"></a>是否有示範如何整合 SDK 的範例應用程式？

可以！ 我們最近才剛改造開放原始碼範例應用程式 [Wagr for iOS](https://github.com/Microsoft/Wagr-Sample-Intune-iOS-App)。 使用 Intune App SDK 的應用程式保護原則現在已啟用 Wagr。

### <a name="how-can-i-troubleshoot-my-app"></a>如何對我的應用程式進行疑難排解？

適用於 iOS 9.0.3+ 的 Intune SDK 支援在行動裝置應用程式中新增診斷主控台的功能，用以測試原則和記錄錯誤。 `IntuneMAMDiagnosticConsole.h` 會定義 `IntuneMAMDiagnosticConsole` 類別介面，讓開發人員可以使用它來顯示 Intune 診斷主控台。 這可讓使用者或開發人員在測試期間收集並共用 Intune 記錄，以利診斷他們可能會遇到的任何問題。 此 API 對整合者而言是選擇性的。

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

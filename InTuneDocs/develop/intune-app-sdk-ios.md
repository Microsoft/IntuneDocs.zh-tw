---
title: "Microsoft Intune App SDK for iOS 開發人員指南 | Microsoft Intune"
description: 
keywords: 
author: Msmbaldwin
manager: jeffgilb
ms.date: 09/08/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8e280d23-2a25-4a84-9bcb-210b30c63c0b
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 975708b5204ab83108a9174083bb87dfeb04a063
ms.openlocfilehash: 52ad28686fa279a7ec251d073283c3554d1c81fc


---

# Microsoft Intune App SDK for iOS 開發人員指南

> [!NOTE]
> 您可能想要先閱讀 [Intune App SDK 快速入門指南](intune-app-sdk-get-started.md)，其中說明如何在每個支援的平台上進行整合準備。* 

Microsoft Intune App SDK for iOS 可讓您將 Intune 行動應用程式管理 (MAM) 併入 iOS 應用程式中。 啟用 MAM 的應用程式是與 Intune App SDK 整合的應用程式，可讓 IT 系統管理員在 Intune 主動管理應用程式時將原則部署至行動應用程式。


# SDK 的功能 

Intune App SDK for iOS 包含靜態程式庫、資源檔、API 標頭、偵錯設定 plist 及設定程式工具。 若要強制執行大部分原則，行動應用程式只需要包含資源檔並以靜態方式連結至程式庫。 進階 Intune MAM 功能則是透過 API 來強制執行。

本指南將涵蓋如何使用適用於 iOS 的 Intune App SDK 的下列元件：

* **libIntuneMAM.a**：Intune App SDK 靜態程式庫。 如果您的應用程式未使用擴充功能，請將這個程式庫連結至專案，讓應用程式進行 Intune 行動應用程式管理。 您可以在＜使用 Intune App SDK 建置您的應用程式＞一節中找到相關指示。

* **IntuneMAM.framework**：Intune App SDK 架構。 請將這個架構連結至專案，讓應用程式進行 Intune 行動應用程式管理。 如果您的應用程式使用擴充功能，讓您的專案不會建立靜態程式庫的多個複本，請使用架構而不是靜態程式庫。

* **IntuneMAMResources.bundle**：包含 SDK 相依資源的資源配套。 

* **標頭**：公開 Intune App SDK API。 如果您使用 API，您必須加入包含 API 的標頭檔。 下列標頭檔包含啟用 Intune App SDK 功能所需的 API 函數呼叫。 
    
    * IntuneMAMAsyncResult.h
    * IntuneMAMDataProtectionInfo.h
    * IntuneMAMDataProtectionManager.h
    * IntuneMAMFileProtectionInfo.h
    * IntuneMAMFileProtectionManager.h
    * IntuneMAMPolicyDelegate.h
    * IntuneMAMLogger.h 


# Intune App SDK 的運作方式

Intune App SDK for iOS 的目標是以最少的程式碼變更，將管理功能加入 iOS 應用程式中。 程式碼變更越少，上市時間就越短，但仍然可保證行動應用程式的一致性與穩定性。 

應用程式必須連結至靜態程式庫，而且必須包含資源配套。 MAMDebugSettings.plist 是選擇性檔案，可包含在套件中，以模擬如何將 MAM 原則套用至應用程式，而不必透過 Microsoft Intune 部署應用程式。 此外在偵錯組建中，您還可以透過 iTunes 檔案共用，將 MAMDebugSettings.plist 檔案傳輸至應用程式的 [文件] 目錄，以套用此檔案中的原則。

# 將 SDK 建置至行動應用程式 

請完成下列步驟以啟用 Intune App SDK：

1. **選項 1**：執行下列作業以連結至 `libIntuneMAM.a` 程式庫：

    將 `libIntuneMAM.a` 程式庫拖放至專案目標的 [連結架構和程式庫] 清單中。
    ![Intune App SDK iOS - 連結架構和程式庫](../media/intune-app-sdk-ios-linked-frameworks-and-libraries.png) 

    **注意**：如果您計劃將應用程式發行至 App Store，請使用針對發行所建置的 `libIntuneMAM.a` 版本，而非偵錯版本。 發行版本會在 [發行] 資料夾中。 偵錯版本包含詳細資訊輸出，有助於針對 Intune App SDK 問題進行疑難排解。
    
    **選項 2**：將 `IntuneMAM.framework` 連結至專案。 將 `IntuneMAM.framework` 拖放至專案目標的 [連結架構和程式庫] 清單中。
    
    **注意**：如果您使用架構，則必須先手動去除通用架構中的模擬器架構，再將應用程式提交至 App Store。 請參閱＜將應用程式提交至 App Store＞這一節。

2. 將下列 iOS 架構新增至專案：
    * MessageUI.framework
    * Security.framework
    * MobileCoreServices.framework
    * SystemConfiguration.framework
    * libsqlite3.dylib
    * libc++.dylib
    * ImageIO.framework
    * LocalAuthentication.framework
    * AudioToolbox.framework

    **注意**：如果應用程式是以 iOS 7 為目標，請將 `LocalAuthentication.framework` 的 [狀態] 屬性設定為 [選擇性]。 如果未設定 [狀態]，應用程式將無法在 iOS 7 上啟動。

    **注意**：Xcode 7 已將 `.dylib` 副檔名切換為 `.tbd`。

3. 藉由拖曳 [建置階段] 的 [複製配套資源] 下的資源配套，將 `IntuneMAMResources.bundle` 資源配套新增至專案。
![Intune App SDK iOS - 複製配套資源](../media/intune-app-sdk-ios-copy-bundle-resources.png)
 
4. 將 `-force_load {PATH_TO_LIB}/libIntuneMAM.a` 加入下列任一項中，並以 Intune App SDK 位置取代 `{PATH_TO_LIB}` ：
    * 專案的 `OTHER_LDFLAGS` 組建組態設定 
    * UI 的 [其他連結器旗標]<br>

    **注意**：若要尋找 `PATH_TO_LIB`，請選取 `libIntuneMAM.a` 檔案，然後從 [檔案] 功能表中選擇 [取得資訊]。 從 [資訊] 視窗的 [一般] 區段中，複製並貼上 [位置] 資訊 (路徑)。

5. 如果您的行動應用程式在其 Info.plist 中定義主要 Nib 或腳本，請移除 [Main Storyboard (主要腳本)] 或 [Main Nib file (主要 Nib 檔案)] 欄位。 如果適當的話，請使用下列索引鍵名稱，將您先前移除的腳本或 Nib 值新增至名為 IntuneMAMSettings 的新目錄下：
    * MainStoryboardFile
    * MainStoryboardFile~ipad
    * MainNibFile
    * MainNibFile~ipad
    
   **注意**：如果您的行動應用程式未在其 Info.plist 中定義主要 Nib 或腳本，則**不需要**這些設定。 

    **注意**：您可以在文件本文中的任何位置按一下滑鼠右鍵，然後將檢視類型變更為 [顯示原始索引鍵/值]，來檢視原始格式的 Info.plist (以查看索引鍵名稱)。

6. 如果尚未啟用 Keychain 共用，請在每個專案目標中按一下 [功能]，然後啟用 [Keychain 共用] 參數來加以啟用。 您必須共用 Keychain 才能繼續進行下一個步驟。

    **注意**：您的佈建設定檔必須能夠支援新的 Keychain 共用值。 Keychain 存取群組應該支援萬用字元。 若要驗證這項作業，請在文字編輯器中開啟 .mobileprovision 檔案，並搜尋 'keychain-access-groups'，然後確認是否有萬用字元，例如： 
    ```
    <key>keychain-access-groups</key>
    <array>
    <string>YOURBUNDLESEEDID.*</string>
    </array>
    ```
7. 啟用 Keychain 共用之後，請遵循下列步驟建立另一個用於儲存 Intune App SDK 資料的存取群組。 您可以使用 UI 或權利檔案來建立 Keychain 存取群組：

    使用 UI 建立 Keychain 存取群組： 
    
    * 如果您的行動應用程式未定義任何 Keychain 存取群組，請加入應用程式的配套識別碼作為第一個群組。
    * 新增共用的 Keychain 群組 `com.microsoft.intune.mam`。 Intune App SDK 使用這個存取群組來儲存資料。  
    * 將 `com.microsoft.adalcache` 新增至現有存取群組。 

    ![Intune App SDK iOS - Keychain 共用](../media/intune-app-sdk-ios-keychain-sharing.png) 

    如果您使用權利檔案來建立 Keychain 存取群組，而不是透過一般 UI，則必須在權利檔案中，於 Keychain 存取群組之前加上 `$(AppIdentifierPrefix)` 。 例如：  
    * `$(AppIdentifierPrefix)com.microsoft.intune.mam` 
    * `$(AppIdentifierPrefix)com.microsoft.adalcache`

    **注意**：權利檔案是行動應用程式特有的 XML 檔案，可用來指定 iOS 應用程式內的特殊權限和功能。

8. 如果應用程式在其 Info.plist 檔案中定義 URL 配置，請針對每個 URL 配置新增另一個具有 `-intunemam` 尾碼的配置。

9. 若是針對 iOS 9+ 開發的行動應用程式，您必須包含應用程式傳遞給應用程式 Info.plist 檔案之 `LSApplicationQueriesSchemes` 陣列中 `UIApplication canOpenURL` 的每個通訊協定。 此外，針對每個列出的通訊協定，必須對加入的新通訊協定附加 `-intunemam`。 您也必須在陣列中包含 `http-intunemam`、 `https-intunemam`和 `ms-outlook-intunemam` 。 

10. 如果應用程式在其權利中定義應用程式群組，請將這些群組以字串陣列形式新增至 IntuneMAMSettings 字典的 `AppGroupIdentitifiers` 索引鍵下。

11. 將行動應用程式連結至 Azure Directory Authentication Library (ADAL)。 您可以在 [Github](https://github.com/AzureAD/azure-activedirectory-library-for-objc) 上取得 Objective C 的 ADAL 程式庫。

    **注意**：Intune App SDK 自 2015 年 6 月 19 日起，已經過 ADAL Broker 分支程式碼的測試。 請確定您要連結的版本是最新/有效的 ADAL 程式庫版本。

12. 藉由拖曳 [建置階段] 的 [複製配套資源] 下的資源配套，將 `ADALiOSBundle.bundle` 資源配套包含在專案中。

13. 連結至程式庫時，使用 `-force_load PATH_TO_ADAL_LIBRARY` 連結器選項。

    將 `-force_load {PATH_TO_LIB}/libADALiOS.a` 新增至專案的 `OTHER_LDFLAGS` 組建組態設定或 UI 的 [其他連結器旗標] 中。 `PATH_TO_LIB` 應該取代成 ADAL 二進位檔位置。 

# 在應用程式中進行 Azure Directory Authentication Library (ADAL) 設定 

Intune App SDK 在自我驗證和條件式啟動案例中會使用 ADAL。 它也會依賴 ADAL 向 MAM 服務註冊使用者身分識別來進行沒有裝置註冊案例的管理。 

一般來說，ADAL 需要應用程式登錄並取得稱為 ClientID 的唯一識別碼及其他識別碼，以確保授與應用程式的權杖安全無虞。 Intune App SDK 在連絡 Azure Active Directory 時，會使用預設登錄值。  

如果應用程式本身在自我驗證案例中使用 ADAL，應用程式必須使用其現有的登錄值並覆寫 Intune App SDK 預設值，以確保不會提示使用者驗證兩次 (一次是由 Intune App SDK，另一次是由應用程式)。 

##ADAL 常見問題集

**應該使用什麼 ADAL 二進位檔？** 

Intune App SDK 目前使用 [GitHub 上的 ADAL](https://github.com/AzureAD/azure-activedirectory-library-for-objc) 的 Broker 分支，以支援需要條件式存取的應用程式 (因此取決於 Microsoft 驗證器應用程式的應用程式)。 不過，SDK 仍然與主要 ADAL 分支相容。 請使用適合您應用程式的分支。

**如何連結至 ADAL 二進位檔？**

將 `-force_load {PATH_TO_LIB}/libADALiOS.a` 新增至專案的 `OTHER_LDFLAGS` 組建組態設定或 UI 的 [其他連結器旗標] 中。 `PATH_TO_LIB` 應該取代成 ADAL 二進位檔位置。 也請務必將 ADAL 配套複製至應用程式。  

如需詳細資訊，請參閱 [Github 上的 ADAL](https://github.com/AzureAD/azure-activedirectory-library-for-objc) 中的指示。


**如何與其他使用相同佈建設定檔所簽署的應用程式共用 ADAL 快取？**

如果您的應用程式未定義任何 Keychain 存取群組，請將應用程式的配套識別碼新增為第一個群組。
在 keychain 權利中新增 `com.microsoft.adalcache` 和 `com.microsoft.workplacejoin` 存取群組，以啟用 ADAL SSO。 

如果您明確地設定 ADAL 共用快取 keychain 群組，請確定它設為 `<app_id_prefix>.com.microsoft.adalcache`。 除非您覆寫這個項目，否則 ADAL 將為您進行設定。 如果您想要指定自訂 keychain 群組以取代 `com.microsoft.adalcache`，請在 Info.plist 的 "IntuneMAMSettings" 下使用 `ADALCacheKeychainGroupOverride` 索引鍵指定該行為。

**如何強制 Intune App SDK 使用我的應用程式已使用的 ADAL 設定？** 

如果您的應用程式已經使用 ADAL，請參閱下面有關 IntuneMAMSettings 的區段，以取得如何填入下列設定的相關資訊：  

* ADALClientId
* ADALRedirectUri
* ADALRedirectScheme
* ADALCacheKeychainGroupOverride

**如何切換 AAD 生產環境與內部測試環境？**

`MAMPolicies.plist` 中的 `AadAuthorityURI` 設定可以用來指定用於 ADAL 呼叫的 AAD 環境。 除非予以覆寫，否則它目前預設為使用 AAD 生產前環境 (PPE)。
    
若要針對 PPE 進行測試，您可以使用編譯階段或執行階段參數。 

若是 MAM 服務 URL 和 AAD 的編譯階段環境參數，請在 MAMEnvironment.plist 中將 `UsePPE` 布林旗標設為 true (**注意**：不支援透過 Info.plist 這麼做)。 

若是執行階段環境參數，請將標準使用者預設值中的 `com.microsoft.intune.mam.useppe` 設為 "1" 以使用 PPE。 這會取代現有 `com.microsoft.intune.mam.AADAuthorityEnvironment` 設定。 

**如何將 AAD 授權單位 URL 覆寫為執行階段時所提供的租用戶特定 URL？** 

在 IntuneMAMPolicyManager 執行個體上設定 `aadAuthorityUriOverride` 屬性。

**注意**：在沒有裝置註冊案例的 MAM 中需要有這個項目，才能允許 SDK 重複使用應用程式所擷取的 ADAL 重新整理權杖。

**注意：**除非清除或變更值，否則 SDK 將繼續使用這個授權單位 URL 進行原則重新整理以及任何後續註冊要求。  因此，請務必在公司使用者登出應用程式時清除值，並在新公司使用者重新登入時進行重設。


**如果我的應用程式本身使用 ADAL 進行驗證，應該怎麼做？**

如果應用程式已經使用 ADAL 進行驗證，則需要下列步驟。 如果您的應用程式未依賴 ADAL，則應該檢閱在應用程式未使用 ADAL 時如何向 Intune 服務進行註冊的小節。

* 在專案的 Info.plist 中，於索引鍵名稱為 `ADALClientId` 的 IntuneMAMSettings 字典下，指定要用於呼叫 ADAL 的 ClientID。 

* 在專案的 Info.plist 中，於索引鍵名稱為 `ADALRedirectUri` 的 IntuneMAMSettings 字典下，指定要用於呼叫 ADAL 的重新導向 URI。 根據您應用程式的重新導向 URI 格式，您可能還需要指定 `ADALRedirectScheme` 。



#向 MAM 服務註冊應用程式 

## 使用 API
Intune App SDK 現在可讓 iOS 應用程式從 Intune 接收 MAM 原則，而不需要向 Intune 註冊 MDM。 為了支援這項新功能，SDK 提供新的 API，讓應用程式接收 MAM 原則。 若要使用新的 API，請完成下列步驟：

1. 使用 Intune App SDK 的最新版本，其在註冊或未註冊裝置的情況下支援管理應用程式。 如果您的應用程式已在未使用這項功能的情況下使用舊版 SDK，則必須更新 Intune MAM 程式庫，以及使用最新 SDK 中的標頭來更新 Headers 資料夾。

2. 將 IntuneMAMEnrollment.h 新增至任何將呼叫 API 的檔案 

3. 若要針對 PPE 進行測試，您可以使用編譯階段或執行階段參數。 

    若是 MAM 服務 URL 和 AAD 的編譯階段環境參數，請在 MAMEnvironment.plist 中將 `UsePPE` 布林旗標設為 true (**注意**：不支援透過 Info.plist 這麼做)。 

    若是執行階段環境參數，請將標準使用者預設值中的 `com.microsoft.intune.mam.useppe` 設為 "1" 以使用 PPE。 這會取代現有 `com.microsoft.intune.mam.AADAuthorityEnvironment` 設定。 


##註冊帳戶 

如果代表指定的使用者帳戶註冊應用程式，則應用程式可以從 Intune 服務接收 MAM 原則。  應用程式必須負責向 Intune App SDK 註冊任何新登入的使用者。  驗證新的使用者帳戶之後，應用程式應該呼叫在 Headers/IntuneMAMEnrollment.h 中找到的 `registerAndEnrollAccount` 方法： 

```
/** 


 *  This method will add the account to the list of registered accounts. 
 *  An enrollment request will immediately be started.
 *  @param identity The UPN of the account to be registered with the SDK 
 */ 

(void)registerAndEnrollAccount:(NSString *)identity; 

```
藉由呼叫上述方法，SDK 將註冊使用者帳戶，並代表這個帳戶嘗試註冊應用程式。  如果註冊因任何原因而失敗，SDK 將自動在 24 個小時之後重新嘗試註冊。  基於偵錯目的，應用程式可以透過委派來接收有關任何註冊要求結果的通知 (請參閱下面的詳細資料)。

叫用這個 API 之後，應用程式可以繼續正常運作。  如果註冊確實成功，SDK 將通知使用者：需要重新啟動應用程式。  此時，使用者可以立即重新啟動應用程式。


##取消註冊帳戶 


將使用者登出應用程式之前，應用程式應該從 SDK 取消註冊使用者。  這確保： 

1. 使用者帳戶不再發生註冊重試。 
2. 如果使用者已成功註冊應用程式，則會從 Intune MAM 服務取消註冊使用者和應用程式，並移除 MAM 原則。
3. (選擇性) 可以起始選擇性抹除，確保刪除任何工作或學校相關資料。 

將使用者登出之前，應用程式應該呼叫在 Headers/IntuneMAMEnrollment.h 中找到的下列 API： 

```
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

刪除使用者帳戶的 AAD 權杖之前，必須呼叫這個方法。  SDK 需要使用者應用程式權杖，才能代表使用者對 Intune MAM 服務提出特定要求。 

如果應用程式將自行刪除使用者的工作或學校相關資料，則 `doWipe` 旗標可以設定為 false。  否則，應用程式可以讓 SDK 起始選擇性抹除，這樣會呼叫應用程式的選擇性抹除委派。 

```
[[IntuneMAMEnrollmentManager instance] deRegisterAndUnenrollAccount:@”user@foo.com” withWipe:YES]; 
```


##在沒有先前登入的情況下註冊 

未登入具有 Azure Active Directory 之使用者的應用程式仍然可以從 Intune Service 接收 MAM 原則，方法是呼叫下列 API 讓 SDK 處理該驗證。 如果應用程式尚未向 AAD 驗證使用者，但仍需要擷取 MAM 原則以保護其應用程式中的資料，則應用程式應該使用這個選項 -- 例如︰如果正在使用另一個驗證服務進行應用程式登入，或者，如果應用程式根本不支援登入。 若要這麼做，應用程式應該呼叫在 Headers/IntuneMAMEnrollment.h 中找到的 `loginAndEnrollAccount` 方法：

```
/** 
 *  Creates an enrollment request which is started immediately. 
 *  If no token can be retrieved for the identity, the user will be prompted 
 *  to enter their credentials, after which enrollment will be retried. 
 *  @param identity The UPN of the account to be logged in and enrolled. 
 */ 
 (void)loginAndEnrollAccount: (NSString *)identity; 

```
藉由呼叫這個方法，SDK 將在找不到現有權杖時提示使用者提供認證，然後代表這個帳戶嘗試註冊應用程式。 這個方法在呼叫時 "nil" 為身分識別，在這個情況下，SDK 將在裝置上註冊現有 MAM 使用者，或在找不到任何現有使用者時提示使用者提供使用者名稱。 

如果註冊失敗，應用程式應該考慮根據失敗詳細資料，在未來重新呼叫這個 API。 應用程式可以透過委派來接收有關任何註冊要求結果的通知 (請參閱詳細資料)。 

叫用這個 API 之後，應用程式可以繼續正常運作。  如果註冊確實成功，SDK 將通知使用者：需要重新啟動應用程式 (如有關註冊帳戶的上一節所示)。 

##偵錯資訊 

應用程式可以接收有關向 Intune MAM 服務提出下列要求的偵錯通知︰ 

 - 註冊要求 
 - 原則更新要求 
 - 取消註冊要求 

透過可在 Headers/IntuneMAMEnrollmentDelegate.h 中找到的委派方法來呈現通知： 

```
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

這些委派方法傳回 ```IntuneMAMEnrollmentStatus``` 物件，其中包含下列資訊︰ 

- 與要求相關聯之帳戶的身分識別 
- 表示要求結果的狀態碼 
- 狀態碼描述的錯誤字串 
- NSError 物件 

這個物件與可傳回的特定狀態碼定義在 Headers/IntuneMAMEnrollmentStatus.h 中。 

請務必注意，這項資訊僅供進行偵錯，沒有任何應用程式的商務邏輯應該根據這些通知。  概念是應用程式可以將這項資訊傳送至遙測服務來進行偵錯或監視。 


##範例程式碼 

下列是委派方法的範例實作︰ 

```
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


##應用程式重新啟動 

應用程式第一次收到 MAM 原則時，必須重新啟動，才能套用必要的勾點。  為了通知需要重新啟動的應用程式，SDK 在 Headers/IntuneMAMPolicyDelegate.h 中提供委派方法。 
```
 - (BOOL) restartApplication 
```
這個方法的傳回值將告訴 SDK，應用程式是否將處理必要重新啟動。   

 - 如果傳回 true，應用程式將負責處理重新啟動。   
 - 如果傳回 false，則 SDK 將在傳回這個方法之後重新啟動應用程式。  SDK 會立即顯示一個對話方塊，告訴使用者必須重新啟動應用程式。 



# 進行 Intune App SDK 設定

包含在應用程式 Info.plist 內的 IntuneMAMSettings 字典是用來設定 Intune App SDK。 以下是所有支援的設定清單。 

其中一些設定可能在前幾節中討論過，而且有些設定並不適用於所有應用程式。 

設定  | 類型  | 定義 | 必要？
--       |  --   |   --       |  --
ADALClientId  | 字串  | 應用程式的 AAD 用戶端識別碼。 | 如果應用程式使用 ADAL，則為必要項。
ADALRedirectUri  | 字串  | 應用程式的 AAD 重新導向 URI。 | 如果應用程式使用 ADAL，則需要 ADALRedirectUri 或 ADALRedirectScheme。 
ADALRedirectScheme  | 字串  | 應用程式的 AAD 重新導向配置。 如果應用程式的重新導向 URI 格式為 `scheme://bundle_id`，則這可以用來代替 ADALRedirectUri。 | 如果應用程式使用 ADAL，則需要 ADALRedirectUri 或 ADALRedirectScheme。 
ADALLogOverrideDisabled | 布林值  | 指定 SDK 是否會將所有 ADAL 記錄 (包括任何來自應用程式的 ADAL 呼叫) 路由傳送至其本身的記錄檔。 預設為 [否]。 如果要讓應用程式設定自己的 ADAL 記錄回呼，請設定為 [是]。 | 選擇性。
ADALCacheKeychainGroupOverride | 字串  | 指定要用於 ADAL 快取而非 "com.microsoft.adalcache" 的 keychain 群組。 請注意，這不包含 app-id 前置詞。 這會在執行階段加在所提供字串的前面。 | 選擇性。
AppGroupIdentifiers | 字串陣列  | 應用程式之權利 com.apple.security.application-groups 區段中的應用程式群組陣列。 | 如果應用程式使用應用程式群組，則為必要項。
ContainingAppBundleId | 字串 | 指定含有應用程式之擴充功能的配套識別碼。 | 對 IOS 擴充功能而言為必要項。
DebugSettingsEnabled| 布林值 | 如果設定為 [是]，則可以套用 [設定] 配套內的測試原則。 啟用這個設定時，**不**應該提供應用程式。 | 選擇性。
MainNibFile<br>MainNibFile~ipad  | 字串  | 這項設定應該包含應用程式的主要 nib 檔案名稱。  | 如果應用程式在其 Info.plist 中定義 MainNibFile，則為必要項。
MainStoryboardFile<br>MainStoryboardFile~ipad  | 字串  | 這項設定應該包含應用程式的主要腳本檔案名稱。 | 如果應用程式在其 Info.plist 中定義 UIMainStoryboardFile，則為必要項
MAMPolicyRequired| 布林值| 指定應用程式在沒有 Intune MAM 原則時是否無法予以啟動。 預設為 [否]。 
MAMPolicyWarnAbsent | 布林值| 指定應用程式在沒有 Intune MAM 原則時，是否將在啟動期間警告使用者。 注意︰這個設定設為 [是] 時，無法將應用程式提交至市集 | 選擇性。
MultiIdentity | 布林值| 指定應用程式是否為多重身分識別感知 | 選擇性。
SplashIconFile~ipad <br>IntuneMAMSettings | 字串  | 指定 Intune 啟動顯示畫面的圖示檔。 如需詳細資訊，請參閱本文的＜啟動映像檔＞一節。 | 選擇性。
SplashDuration | 數字 | Intune 啟動顯示畫面將於應用程式啟動時顯示的最短時間 (以秒為單位)。 預設為 1.5。 | 選擇性。
BackgroundColor| 字串| 指定開頭顯示畫面和 PIN 畫面的背景色彩。 接受格式為 ‘#XXXXXX’ 的十六進位 RGB 字串，其中 ‘X’ 的範圍可以是 0-9 或 A-F。 可能會省略井字號。   | 選擇性，預設為淺灰色。
ForegroundColor| 字串| 指定開頭顯示畫面和 PIN 畫面的前景色彩 (例如文字色彩)。 接受格式為 ‘#XXXXXX’ 的十六進位 RGB 字串，其中 ‘X’ 的範圍可以是 0-9 或 A-F。 可能會省略井字號。  | 選擇性，預設為黑色。
AccentColor | 字串| 指定 PIN 畫面的輔色，例如按鈕文字色彩和方塊醒目提示色彩。  接受格式為 ‘#XXXXXX’ 的十六進位 RGB 字串，其中 ‘X’ 的範圍可以是 0-9 或 A-F。 可能會省略井字號。| 選擇性，預設為系統藍色。
MAMTelemetryDisabled| 布林值| 指定 SDK 是否不會將任何遙測資料傳回給其後端| 選擇性。
MAMTelemetryUsePPE | 布林值 | 指定 SDK 是否將資料傳送至預先生產環境 (PPE) 後端。 如果使用 Intune 原則測試應用程式，讓測試遙測資料與客戶資料不混合使用，請使用此選項。 | 選擇性。

## 遙測 

適用於 iOS 的 Intune App SDK 預設會記錄傳送至 Microsoft Intune 之使用事件的遙測資料。 當發生下列使用事件時，會記錄資料： 

1. **應用程式啟動**：協助 Microsoft Intune 依管理類型了解啟用 MAM 的應用程式使用量 (含 MDM 的 MAM、不含 MDM 註冊的 MAM 等)。

2. **EnrollApplication API 呼叫**：協助 Microsoft Intune 了解從用戶端呼叫 `enrollApplication` 的成功率和各種其他效能標準。

**注意**：如果您選擇不要將 Intune App SDK 遙測資料從您的行動應用程式傳送至 Microsoft Intune，則必須停用 Intune App SDK 遙測擷取，方法是在 IntuneMAMSettings 字典中將 `MAMTelemetryDisabled` 屬性設定為 [是]。


## 將 SDK 建置至擴充功能 (選擇性) 

建置擴充功能時，請遵循如本文之＜將 SDK 建置至行動應用程式＞一節所述的相同指示，來建置您的行動應用程式。 此外，請更新每個擴充功能的 Info.plist 檔案，方法是將包含應用程式配套識別碼的值，新增至 IntuneMAMSettings 字典的 `ContainingAppBundleId` 索引鍵下。

## 將 SDK 建置至架構 (選擇性)

有了 Intune App SDK 的最新更新，如果您的行動應用程式包含內嵌應用程式架構，則不需要使用任何特定連結器旗標來編譯行動應用程式。 

## 啟動映像檔 (選擇性)

如果啟用 MAM 的應用程式是由 Microsoft Intune 主動管理，Intune App SDK 會在應用程式啟動時顯示啟動畫面，向使用者表示應用程式已受管理。 您可以選擇性地加入要在 [由您的公司管理] 啟動頁上顯示的映像檔。 請使用下列映像方針：

* 使用索引鍵名稱 `SplashIconFile` 和 `SplashIconFile~ipad`，在應用程式之 Info.plist 的 IntuneMAMSettings 字典下新增檔案名稱。 

* 映像大小和需求：

    * iPhone 6s Plus 和 iPhone 6 Plus 為 180 x 180，其他 iPhone 機型為 120x120，iPad 為 152x152。 
    
    * 從檔案名稱中移除 .png 副檔名。 
    
    * 連結至程式庫時，使用 `@2x` 尾碼，針對 3 倍縮放版本使用 `@3x` 尾碼。 如果映像大小不正確，則會縮放成最適大小。 如果未指定 SplashIconFile 值，Intune App SDK 會選取其中一個應用程式圖示 (iPhones 為 60x60，iPad 為 76x76)。

**注意**：這個畫面會在啟動時觸發，但使用者可永久關閉畫面。



#啟用多重身分識別 (選擇性)

SDK 預設會將原則套用至應用程式整體。 多重身分識別是一個 MAM 功能，可以啟用以允許將原則套用至每個身分識別層級。  這需要的應用程式參與高於其他 MAM 功能。 

需要有應用程式，才能在想要變更使用中身分識別時通知應用程式 SDK。 需要身分識別變更時，SDK 也會通知應用程式。 目前僅支援一個受管理的身分識別。 使用者註冊裝置或應用程式之後，SDK 會使用這個身分識別，並將其視為主要受管理身分識別。 應用程式中的其他使用者則會因不受限制原則設定而視為不受管理。 

請注意，身分識別只會定義為字串。 身分識別不區分大小寫，而且身分識別的 SDK 要求可能不會傳回設定身分識別時原本使用的相同大小寫。


##了解身分識別 
  
身分識別就是帳戶的使用者名稱 (例如 user@contoso.com)。 開發人員可以設定應用程式在下列不同層級的身分識別︰ 

* **處理序身分識別**：處理序身分識別會設定整個處理序的身分識別，並且主要用於單一身分識別應用程式。 這個身分識別會影響所有作業、檔案和 UI。
* **UI 身分識別**：判斷在主要執行緒上將哪些原則套用至 UI 作業 (例如剪下/複製/貼上、PIN、驗證、資料共用等)。UI 身分識別不會影響檔案作業 (加密、備份等)。 
* **執行緒身分識別**：執行緒身分識別會影響在目前執行緒上套用哪些原則。 這會影響所有作業、檔案和 UI。

不論使用者是否受管理，應用程式都必須負責適當地設定身分識別。

在任何時間點，每個執行緒都會有 UI 作業和檔案作業的有效身分識別。 這是用來判斷應該套用哪些原則 (如果有的話) 的身分識別。 如果身分識別是 [沒有身分識別]，或使用者未受管理，則不會套用任何原則。 
 
 

##執行緒佇列
 
應用程式通常會將非同步和同步工作分派至執行緒佇列。 SDK 會攔截 Grand Central Dispatch (GCD) 呼叫，並產生目前執行緒身分識別與已分派工作的關聯。 執行工作時，SDK 會將執行緒身分識別暫時變更為與工作相關聯的身分識別，並執行工作，然後還原原始執行緒身分識別。 因為 `NSOperationQueue` 的建置基礎是 GCD，所以 `NSOperations` 將會在新增至 `NSOperationQueue` 時針對執行緒的身分識別執行。 `NSOperations` 或直接使用 GCD 分配的函數也可以在執行時變更目前執行緒身分識別。 這個身分識別將會覆寫繼承自分派執行緒的身分識別。 

##檔案擁有者
 
SDK 會記錄本機檔案擁有者身分識別，並據以套用原則。 建立檔案時，或以截斷模式開啟檔案時，會建立檔案擁有者。 擁有者設為執行作業之執行緒的有效檔案作業身分識別。 或者，應用程式可以使用 `IntuneMAMFilePolicyManager` 明確地設定檔案擁有者身分識別。 應用程式可以使用 `IntuneMAMFilePolicyManager` 來擷取檔案擁有者，並在顯示檔案內容之前設定 UI 身分識別。


##共用資料檔案
 
如果應用程式建立包含受管理和不受管理使用者之資料的檔案，則應用程式必須負責加密受管理使用者的資料。 資料可以使用 `IntuneMAMDataProtectionManager` 的 `protect` 和 `unprotect` API 進行加密。 `protect` 方法會接受可以是受管理或不受管理使用者的身分識別。 如果是受管理使用者，則會加密資料。 如果是不受管理使用者，則會將標頭新增至編碼身分識別的資料，但不會加密資料。  `protectionInfo` 方法可以用來擷取資料的擁有者。

##共用擴充功能
 
如果應用程式包含共用擴充功能，則可以在 `IntuneMAMDataProtectionManager` 中使用 `protectionInfoForItemProvider` 方法來擷取正在共用之項目的擁有者。 如果共用的項目是檔案，則 SDK 會處理檔案擁有者的設定。 如果共用的項目是資料，則在這項資料保存至檔案時，應用程式必須負責設定檔案擁有者，以及呼叫 `setUIPolicyIdentity` API (如下所述)，再於 UI 中顯示這項資料。
 
#啟用多重身分識別
 
預設會將應用程式視為單一身分識別，而且 SDK 會將處理序身分識別設定為已註冊使用者。 若要啟用多重身分識別支援，名稱 'MultiIdentity' 為值 'YES' 的布林設定應該新增至應用程式之 Info.plist 檔案內的 IntuneMAMSettings 字典。 啟用多重身分識別時，處理序身分識別、UI 身分識別和執行緒身分識別都會設定為 nil，而且應用程式必須負責適當地設定它們。

 
##切換身分識別
 
###應用程式起始的身分識別切換
啟動時，會將多重身分識別應用程式視為正在使用未知且不受管理的帳戶執行。 條件式啟動 UI 將不會執行，而且不會對應用程式執行任何原則。 應用程式必須負責在應該變更身分識別時即通知 SDK。 一般而言，只要應用程式即將顯示特定使用者帳戶的資料，就會發生這種情形。

範例是使用者嘗試在筆記本中開啟文件、信箱或索引標籤時。 應用程式需要在實際開啟檔案、信箱或索引標籤之前通知 SDK。 這是透過 `IntuneMAMPolicyManager` 中的 `setUIPolicyIdentity` API 所完成。 不論是否為受管理使用者，都應該呼叫這個 API。 如果使用者是受管理的，SDK 將執行條件式啟動檢查 (破解偵測、PIN、驗證等)。 身分識別切換的結果是透過完成處理常式，以非同步方式傳回給應用程式。 應用程式應該延後開啟文件、信箱、索引標籤等， 直到傳回成功結果碼。 如果身分識別切換失敗，應用程式應該取消作業。 

###SDK 起始的身分識別切換
會有 SDK 需要要求應用程式切換至特定身分識別的情況。 多重身分識別應用程式必須在 `IntuneMAMPolicyDelegate` 中實作 `identitySwitchRequired` 方法，以處理這個要求。 呼叫時，如果應用程式可以處理切換至所指定身分識別的要求，則應該將 `IntuneMAMAddIdentityResultSuccess` 傳遞至完成處理常式。 如果無法處理身分識別切換，則應用程式應該將 `IntuneMAMAddIdentityResultFailed` 傳遞至完成處理常式。 應用程式不需要呼叫 `setUIPolicyIdentity` 來回應這個呼叫。 如果 SDK 需要應用程式切換至未受管理使用者帳戶，則會將空字串傳遞至 `identitySwitchRequired` 呼叫。 
 
###選擇性抹除
選擇性地抹除應用程式時，SDK 將會在 `IntuneMAMPolicyDelegate` 中呼叫 `wipeDataForAccount` 方法。 應用程式必須負責移除指定的使用者帳戶和其相關聯的任何資料。 SDK 可以移除使用者擁有的所有檔案，並在應用程式從 `wipeDataForAccount` 呼叫傳回 "FALSE" 時執行。 請注意，會從背景執行緒呼叫這個方法，而且除非已移除使用者的所有資料，否則應用程式不應該傳回 (如果應用程式傳回 "FALSE"，則檔案除外)。

# 在 Xcode 中對 Intune App SDK 進行偵錯

使用 Microsoft Intune 手動測試啟用 MAM 的應用程式之前，您可以在 Xcode 中使用 **Settings.bundle** 檔案。 這可讓您設定測試原則，而不需要連線到 Intune。 若要加以啟用：

* 以滑鼠右鍵按一下您專案中的最上層資料夾，來新增 Settings.bundle 檔案。 從功能表選取 [新增] -> [新增檔案]。 選取在 [資源] 下找到之要加入的 [設定配套] 範本。

* 只在偵錯組建上，將 MAMDebugSettings.plist 複製至 Settings.bundle 中。

* 在 Settings.bundle 的 Root.plist 中，新增 "Type" = 子窗格且 "FileName" = MAMDebugSettings 的喜好設定。

* 在 [設定] -> [您的應用程式名稱] 中，開啟 [Enable Test Policies (啟用測試原則)]。

* 在 Xcode 內部或外部啟動應用程式。 

* 在 [設定] -> [您的應用程式名稱] -> [Enable Test Policies (啟用測試原則)] 中，開啟原則，例如"PIN"。

* 在 Xcode 內部或外部啟動應用程式。 確認 PIN 如預期般運作。

> [!NOTE]
> 您現在可以使用 [設定] -> [您的應用程式名稱] -> [Enable Test Policies (啟用測試原則)]，來啟用並切換設定。

# 建議的 iOS 最佳作法

以下是開發 iOS 時建議的一些最佳作法:

IOS 檔案系統區分大小寫。 請確定檔案名稱的大小寫正確，例如 `libIntuneMAM.a` 和 `IntuneMAMResources.bundle`。

如果 Xcode 在尋找 `libIntuneMAM.a`時遇到問題，您可以藉由將這個程式庫的路徑加入連結器搜尋路徑中，來修正問題。



##常見問題集 

 **是否需要向 MAM 服務註冊我應用程式的所有使用者？**

否。  事實上，只應該向 Intune App SDK 註冊工作或學校帳戶。  應用程式負責決定是否在工作或學校內容中使用帳戶。   
 
**已登入應用程式的使用者如何?  是否需要註冊它們？** 

雖然應用程式負責在成功驗證之後註冊使用者，但是應用程式也會負責註冊在應用程式具有較少 MDM 的 MAM 功能之前可能已存在的任何現有帳戶。   


若要這樣做，應用程式應該會使用 `registeredAccounts:` 方法。  這個方法會傳回包含所有已註冊至 Intune MAM 服務之帳戶的 NSDictionary。  如果應用程式中的任何現有帳戶都未出現在清單中，則應用程式應該透過 `registerAndEnrollAccount:` 來註冊這些帳戶。 


 

**SDK 重試註冊的頻率為何？** 

SDK 會依 24 小時間隔自動重試所有先前失敗的註冊。  SDK 這麼做以確保如果使用者的組織已在使用者登入應用程式之後啟用 MAM，則使用者會順利註冊並接收原則。 

SDK 將會在偵測到使用者已順利註冊應用程式時停止重試。  原因是只有 1 位使用者可以在任何指定的時間註冊應用程式。 如果取消註冊使用者，則重試會以相同的 24 小時間隔重新開始。 


 
**為何需要取消註冊使用者？** 

SDK 將會在背景定期採取下列動作：

 - 如果尚未註冊應用程式，則會每隔 24 小時嘗試註冊所有已註冊的帳戶。 
 - 如果已註冊應用程式，SDK 會每隔 8 小時檢查 MAM 原則更新。 

藉由取消註冊使用者，可通知 SDK，使用者無法再使用應用程式，而且可以停止該使用者帳戶的任何上述定期事件。  它也會在必要時觸發應用程式取消註冊和選擇性抹除。 

**是否應該將 deregister 方法中的 doWipe 旗標設為 true？** 將使用者登出應用程式之前，應該呼叫這個方法。  登出時，如果從應用程式刪除使用者資料，則 `doWipe` 可以設為 false。  不過，如果應用程式未實際移除使用者的資料，則這應該設為 true，讓 SDK 可以手動刪除資料本身。 

**是否有任何其他方式可以取消註冊應用程式？** 是，IT 系統管理員可以將選擇性抹除命令傳送給應用程式，以取消註冊使用者以及抹除使用者資料。  SDK 會自動處理這種情況，並透過取消註冊委派方法來傳送通知。 

#將應用程式提交至 App Store
Intune App SDK 的靜態程式庫和架構組建是通用二進位檔，表示它們包含適用於所有裝置和模擬器架構的程式碼。 如果提交至 App Store 的應用程式包含模擬器程式碼，則 Apple 會拒絕提交這些應用程式。 針對僅限裝置組建的靜態程式庫進行編譯時，連結器會自動去除模擬器程式碼。

如果您的應用程式使用 Intune App SDK 的**架構組建**，則必須先手動去除通用架構中的模擬器架構，再將應用程式提交至 App Store。 下面的指示將協助您執行下列作業：

1. 確定 `IntuneMAM.framework` 在桌面上。
2. 執行下列命令：
    
    ```
    lipo ~/Desktop/IntuneMAM.framework/IntuneMAM -remove i386 -remove x86_64 -output ~/Desktop/IntuneMAM.device_only
    ```
    第一個命令會去除架構 dylib 中的模擬器架構。
    ```
    cp ~/Desktop/IntuneMAM.device_only ~/Desktop/IntuneMAM.framework/IntuneMAM 
    ```
    第二個命令會將僅限裝置 dylib 複製回 framework 目錄。



<!--HONumber=Sep16_HO4-->



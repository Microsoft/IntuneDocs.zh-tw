---
title: "Microsoft Intune App SDK for Android 開發人員指南 | Microsoft Intune"
description: 
keywords: 
author: Msmbaldwin
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0100e1b5-5edd-4541-95f1-aec301fb96af
ms.reviewer: jeffgilb
ms.suite: ems
ms.sourcegitcommit: 2915cca314b489bbcb590d01b03a0b38134fa619
ms.openlocfilehash: d2e4b6903d86b79edd9c758b2ce51733831e785a


---

# Android 的 Microsoft Intune App SDK 開發人員指南

> [!NOTE] 您可能想要先閱讀 [Intune App SDK 概觀](intune-app-sdk.md)，其中涵蓋 SDK 目前的功能，並說明如何在每個支援的平台上進行整合準備。 

# SDK 的功能 

Android 的 Microsoft Intune App SDK 是不含外部相依性的標準  Android 程式庫。 
SDK 的組成項目包括：  

* **`Microsoft.Intune MAM.SDK.jar`**：在應用程式中啟用 MAM 所需的介面；除了啟用與 Microsoft Intune 公司入口網站應用程式的互通性外，還需具備此項目。 應用程式必須將其指定為 Android 程式庫參考。

*  **`Microsoft.Intune.MAM.SDK.Support.v4.jar`**：在運用 android v4 支援程式庫的應用程式中啟用 MAM 所需的介面。  需要這項支援的應用程式必須直接參考 jar 檔案。 

* **`Microsoft.Intune.MAM.SDK.Support.v7.jar`**：在運用 Android v7 支援程式庫的應用程式中啟用 MAM 所需的介面。   需要這項支援的應用程式必須直接參考 jar 檔案。

* **資源目錄**：SDK 所依賴的資源 (例如字串)。 

* **`Microsoft.Intune.MAM.SDK.aar`**：SDK 元件 (Support.V4 和 Support.V7 Jar 除外)。 如果您的建置系統支援 AAR 檔案，則可以使用這個檔案來取代個別的元件。

* **`AndroidManifest.xml`**：其他的進入點和程式庫需求。 

* **`THIRDPARTYNOTICES.TXT`**：確認會編譯至應用程式中的協力廠商及/或 OSS 程式碼的屬性通知。 

# 需求 

Intune App SDK 是一種編譯過的 Android 專案。 因此，應用程式可針對其最低或目標 API 版本使用無特定的 Android 版本。 此 SDK 支援 Android API 14 (Android 4.0+) 到 Android 24。 

# Intune App SDK 的運作方式 

Intune App SDK 需要變更應用程式的原始程式碼，以啟用應用程式管理原則。 這是透過將 Android 基底類別取代為對等的 Managed 類別來完成，請參閱前置詞為 `MAM`。 SDK 類別的位置介於 Android 基底類別和應用程式本身針對該類別的衍生版本之間。  以活動為範例來看，最後您得到的繼承階層會像這樣： `Activity ->MAMActivity->AppSpecificActivity`。

當 `AppSpecificActivity` 想要與其父代互動，例如 `super.onCreate())`，則 `MAMActivity` 是超級類別 (雖然它位於繼承階層中並取代數種方法)。 Android 應用程式擁有單一模式，並可透過其內容物件存取整個系統。  另一方面，已經納入 Intune App SDK 的應用程式則具有雙重模式，可以繼續透過內容物件存取系統，但根據使用的基底 Activity，內容物件可能由 Android 提供，或在系統的限制檢視與 Android 所提供的內容之間以智慧方式多工處理。

Android 的 Intune App SDK 必須仰賴裝置上的公司入口網站應用程式來啟用 MAM 原則。 如果沒有公司入口網站應用程式，啟用 MAM 的應用程式就不會改變行為，而會跟任何其他行動應用程式運作方式一樣。 安裝好公司入口網站並具備使用者原則時，即會以非同步方式初始化 SDK 進入點。 僅有在 Android 一開始建立處理序時才需要初始化。 在初始化期間，系統會與公司入口網站應用程式建立連線，並下載應用程式限制原則。  

# 如何整合 Intune App SDK
 
如之前所述，SDK 需要變更應用程式的原始程式碼，以啟用應用程式管理原則。 以下是在應用程式中啟用 MAM 所需的步驟： 

## 將類別、方法和活動取代為其 MAM 對等項目 (必要) 

* 您必須將 Android 基底類別取代為其 MAM 對等項目。 若要這樣做，請找到下表所列類別的所有執行個體，並取代為 Intune App SDK 對等項目。  

    | Android 類別 | Intune App SDK 取代 |
    |--|--|
    | android.app.Activity | MAMActivity |
    | android.app.ActivityGroup | MAMActivityGroup |
    | android.app.AliasActivity | MAMAliasActivity |
    | android.app.Application | MAMApplication |
    | android.app.DialogFragment | MAMDialogFragment |
    | android.app.ExpandableListActivity | MAMExpandableListActivity |
    | android.app.Fragment | MAMFragment |
    | android.app.IntentService | MAMIntentService |
    | android.app.LauncherActivity | MAMLauncherActivity |
    | android.app.ListActivity | MAMListActivity |
    | android.app.NativeActivity | MAMNativeActivity |
    | android.app.PendingIntent | MAMPendingIntent |
    | android.app.Service | MAMService |
    | android.app.TabActivity | MAMTabActivity |
    | android.app.TaskStackBuilder | MAMTaskStackBuilder |
    | android.app.backup.BackupAgent | MAMBackupAgent |
    | android.app.backup.BackupAgentHelper | MAMBackupAgentHelper |
    | android.app.backup.FileBackupHelper | MAMFileBackupHelper |
    | android.app.backup.SharePreferencesBackupHelper | MAMSharedPreferencesBackupHelper |
    | android.content.BroadcastReceiver | MAMBroadcastReceiver |
    | android.content.ContentProvider | MAMContentProvider |
    | android.os.Binder | MAMBinder* |
    | android.provider.DocumentsProvider | MAMDocumentsProvider |
    | android.preference.PreferenceActivity | MAMPreferenceActivity |

    *僅有在 Binder 不是從 AIDL 介面產生時才需要將 Binder 取代為 MAMBinder。

    **Microsoft.Intune.MAM.SDK.Support.v4.jar**：

    | Android 類別 Intune MAM | SDK 取代 |
    |--|--|
    | android.support.v4.app.DialogFragment | MAMDialogFragment
    | android.support.v4.app.FragmentActivity | MAMFragmentActivity
    | android.support.v4.app.Fragment | MAMFragment
    | android.support.v4.app.TaskStackBuilder | MAMTaskStackBuilder
    | android.support.v4.content.FileProvider | MAMFileProvider
    
    **Microsoft.Intune.MAM.SDK.Support.v7.jar**：

    |Android 類別 | Intune MAM SDK 取代 |
    |--|--|
    |android.support.v7.app.ActionBarActivity | MAMActionBarActivity |


* 在使用已覆寫為其 MAM 對等項目的 Android 進入點時，必須使用進入點生命週期的替代版本 (除了類別 `MAMApplication`以外)。

    例如，若是衍生自 `MAMActivity`而不是覆寫 `onCreate` 然後呼叫 `super.onCreate`時，Activity 必須覆寫 `onMAMCreate` 並呼叫`uper.onMAMCreate`。 這可將 Activity 啟動限制在某些情況下。 

# 啟用需要應用程式參與的功能 

SDK 無法自行實作部分原則。 為了讓應用程式控制這些功能的行為，我們已公開多個 API，您可以在下方包含的 `AppPolicy` 介面找到。  

    /**
     * External facing app policies.
     */
    public interface AppPolicy {
        /**
         * Restrict where an app can save personal data.
         * 
         * @return True if the app is allowed to save to personal data stores;
         *         false otherwise.
         */
        boolean getIsSaveToPersonalAllowed();
    
        /**
         * Check if policy prohibits saving to a content provider location.
         * 
         * @param location
         *            a content URI to check
         * @return True if location is not a content URI or if policy does not 
         *         prohibit saving to the content location.
         */
        boolean getIsSaveToLocationAllowed(android.net.Uri location); 
    
        /**
         * Whether the SDK PIN prompt is enlightened for the app.
         * 
         * @return True if the PIN is enabled. False otherwise.
         */
        boolean getIsPinRequired();
        /**
         * Whether the Intune Managed Browser is required to open web links.
         *
         * @return True if the Managed Browser is required, false otherwise
         */
        boolean getIsManagedBrowserRequired();
    }

## 讓 IT 系統管理員可控制應用程式的儲存行為

許多應用程式的實作功能，可讓使用者將檔案儲存於本機或儲存至另一項服務。 Intune App SDK 可讓 IT 系統管理員套用組織適用的原則限制，以防資料外洩。  系統管理員可以控制使用者是否可以儲存至個人資料存放區。 這包括儲存至本機位置、SD 卡或備份服務。 啟用此功能需要應用程式參與。 如果您的應用程式可直接從應用程式儲存至個人位置或雲端位置，您就必須實作此功能，以確保 IT 系統管理員能控制是否允許儲存至某個位置。 下列 API 可讓應用程式知道目前的管理原則是否允許儲存到個人存放區。 接著，應用程式即可強制執行原則，因為它會感知使用者透過應用程式可使用的個人資料存放區。  

為了判斷原則是否要強制執行，應用程式可以進行下列呼叫： 

    MAMComponents.get(AppPolicy.class).getIsSaveToPersonalAllowed();

**注意**：MAMComponents.get(AppPolicy.class) 一律會傳回非 null 的應用程式原則，即使裝置或應用程式不受管理亦同。 

## 可讓應用程式偵測是否需要 PIN 原則
 
 應用程式可能要停用其他原則的某些功能，才不會重複 Intune App SDK 中的功能。 比方說，假設應用程式有自己的 PIN 使用者體驗，若 SDK 已設定為需要使用者輸入 PIN 碼，則應用程式可能需要停用此功能。 

為了判斷是否 PIN 原則已設定為需要定期輸入 PIN 碼，應用程式可以進行下列呼叫： 

    MAMComponents.get(AppPolicy.class).getIsPinRequired();

## 透過 SDK 註冊通知  

當 IT 系統管理員使用特定原則 (例如遠端抹除原則) 時，Intune App SDK 可讓您的應用程式控制相關行為。 若要這樣做，您必須建立 `MAMNotificationReceiver` 類別，將其向 `MAMNotificationReceiverRegistry`。 這是藉由提供接收者以及接收者想要在  `App.onCreate`中接收的通知類型來完成，如下列範例所示：
 
    @Override
      public void onCreate() {
            super.onCreate();
    MAMComponents.get(MAMNotificationReceiverRegistry.class).registerReceiver(
    new ToastNotificationReceiver(), MAMNotificationType.WIPE_USER_DATA);
    }

`MAMNotificationReceiver` 只會接收通知。 有些通知是由 SDK 直接處理，有些則需要應用程式的參與。 應用程式一定會針對通知傳回 true 或 false。 除非基於通知結果，應用程式嘗試採取的某些動作失敗，否則一律會傳回 true。 這類失敗會回報給 Intune 服務，例如，當應用程式指出它無法清除使用者資料時。 您可以放心封鎖 `MAMNotificationReceiver.onReceive`，因為其回呼不會在 UI 執行緒上執行。 

下方包含 `MAMNotificationReceiver 介面，如 SDK 所定義： 

    /**
     * The SDK is signaling that a MAM event has occurred. 
     * 
     */
    public interface MAMNotificationReceiver {
      /**
      * A notification was received.
      * 
      * @param notification
      *            The notification that was received.
    * @return The receiver should return true if it handled the
    *   notification without error (or if it decided to ignore the
    *   notification). If the receiver tried to take some action in 
    *   response to the notification but failed to complete that
      *   action it should return false.
      */
      boolean onReceive(MAMNotification notification);
    }

下列通知會傳送至應用程式，且其中部分通知可能需要應用程式參與： 

* **`WIPE_USER_DATA` 通知**︰這個通知是在 `MAMUserNotification` 類別中傳送。 應用程式收到這項通知時，應該刪除與 `MAMUserNotification`。 這項通知目前會在 Intune 服務取消註冊期間傳送。 使用者主要名稱通常會在註冊程序期間指定。 如果您註冊這項通知，您的應用程式必須確定所有使用者資料都已刪除。 如果您未註冊，就會執行預設的選擇性抹除行為。 

* **`WIPE_USER_AUXILIARY_DATA` 通知**：如果應用程式要 Intune App SDK 執行預設抹除，但仍想要在抹除發生時移除部分輔助資料，則可註冊這個通知。  

* **`REFRESH_POLICY` 通知**：這個通知會在 MAMNotification 中傳送，不含任何其他資訊。 收到此通知時，必須注意任何快取的原則都不再處於失效狀態，因此應檢查是哪一個原則。 通常，SDK 會處理這項作業，不過如果原則是以任何持續性的方式使用，則應該由應用程式來處理。 

## 擱置中的對應方式和方法 

衍生自其中一個 MAM 進入點之後, 您即可以正常方式使用內容，以利用其 `PackageManager`等項目來啟動活動。  `PendingIntents` 是這個規則的例外狀況。 呼叫這種類別時，您需要變更類別名稱。 例如，不使用 `PendingIntent.get*`，必須使用 `MAMPendingIntents.get*`。 

在某些情況下，Android 類別中可用的方法已在 MAM 取代類別中被標示為完稿。 在此情況下，MAM 取代類別會提供類似的具名方法 (通常後置字元為 "MAM")，您應將其覆寫。 例如，您應覆寫 `ContentProvider.query`而不是覆寫 `MAMContentProvider.queryMAM`。 Java 編譯器應該強制執行完稿的限制，以防止意外覆寫原始的方法，而不是 MAM 對等項目。 

# 保護備份資料 

截至 Android Marshmallow (API 23) 止，Android 現提供兩種可讓應用程式備份資料的方法。 您可在應用程式中使用這些選項，但需要不同的步驟以確保妥善套用 MAM 資料保護。 您可以檢閱下表，以取得正確資料保護行為所需之相對應動作的快速概觀。  您也可以在 [Android 開發人員資料備份指南](http://developer.android.com/guide/topics/data/backup.html.)。 

## 自動完整備份

在 Android M 裝置上執行時，不論目標 API 為何，Android 皆已開始提供自動的應用程式完整備份。 只要 `android:allowBackup` 屬性不是 false，應用程式皆可收到其應用程式的未篩選完整備份。 這會造成資料洩漏的風險，因此 SDK 需進行下表所述的變更，以確保妥善套用資料保護。  請務必遵循下列所述的指導方針，以妥善保護客戶資料。  如果您設定 `android:allowBackup=false` ，則作業系統永遠不會將您的應用程式加入備份佇列，既然沒有任何備份，您也不會有進一步的 MAM 動作。
 
 ## 「機碼/值」備份

此選項適用於所有 API，並會使用 `BackupAgent` 和 `BackupAgentHelper`。 

### 使用 BackupAgentHelper

`BackupAgentHelper` 比 `BackupAgent` 容易實作 (從原生 Android 功能和 MAM 整合方面來看)。 `BackupAgentHelper` 可讓開發人員分別向 `FileBackupHelper` 或 `SharedPreferencesBackupHelper` 註冊整個檔案和共用的喜好設定，並在建立 `BackupAgentHelper` 時將其加入。 

### 使用 BackupAgent

`BackupAgent` 可讓您更明確了解備份了哪些資料。 不過，使用此選項表示您將無法利用 Android 備份架構的優勢。  由於您是主要負責實作的人，因此比起 MAM，您必須進行更多的步驟才能確保適當的資料保護效果。 由於大部分工作都落在開發人員 (也就是您) 身上，因此有略多的作業涉及 MAM 的整合。 

#### 應用程式沒有備份代理程式
  
當 `Android:allowbBackup =true`：

##### 根據組態檔，進行完整備份： 

在程式資訊清單中的 `com.microsoft.intune.mam.FullBackupContent` METADATA 標記下方提供資源。 例如：
    `<meta-data android:name="com.microsoft.intune.mam.FullBackupContent" android:resource="@xml/my_scheme" />`

將下列屬性加入 `<application>` 標記中： `android:fullBackupContent="@xml/my_scheme"`，其中 `my_scheme` 是應用程式中的 XML 資源。 

##### 沒有排除項目的完整備份 

提供資訊清單中的標記，例如 `<meta-data android:name="com.microsoft.intune.mam.FullBackupContent" android:value="true" />` 
 
將下列屬性新增至 `<application>` 標記：`android:fullBackupContent="true"`。

#### 應用程式有備份代理程式

請遵循 `BackupAgent` 和 `BackupAgentHelper` 章節中的建議，如上所述。 

請考慮改用我們的 `MAMDefaultFullBackupAgent`，它提供簡易的 Android M 備份功能。 

### 在您備份之前

開始備份之前，您必須確認打算備份的檔案或資料緩衝區確實可以備份。 我們已在 `isBackupAllowed` 和 `MAMFileProtectionManager` 和 `MAMDataProtectionManager` 函式供您判斷。 如果檔案或資料緩衝區不能備份，您就不必在備份中繼續嘗試使用。

在備份期間，如果您想要備份在步驟 1 中檢查過的檔案識別，就必須使用準備擷取其資料的檔案來呼叫 `backupMAMFileIdentity(BackupDataOutput data, File … files)`。 這會自動建立新的備份實體，並將其寫入 `BackupDataOutput` 。 在還原時會自動使用這些實體。 

## 設定 Azure Directory Authentication Library (ADAL)  

SDK 仰賴 ADAL 進行驗證和條件式啟動案例，而應用程式必須具備一定程度的 Azure Active Directory 設定。 設定值會直接透過 `AndroidManifest` 中繼資料傳送給 SDK。 若要設定您的應用程式並啟用適當的驗證，請將下列項目加入 `AndroidManifest`。 一般來說，其中某些設定僅有當您的應用程式會使用 ADAL 來進行驗證時才需要；在此情況下，您必須具備應用程式使用的特定值才能向 AAD 註冊該應用程式。 這為了確保使用者不會因為 AAD 辨識兩個個別登錄值而收到兩次驗證提示：一項來自應用程式，一項則來自 SDK。 

        <meta-data
            android:name="com.microsoft.intune.mam.aad.Authority"
            android:value="https://AAD authority/" />
        <meta-data
            android:name="com.microsoft.intune.mam.aad.ClientID"
            android:value="your-client-ID-GUID" />
        <meta-data
            android:name="com.microsoft.intune.mam.aad.NonBrokerRedirectURI"
            android:value="your-redirect-URI" />
        <meta-data
            android:name="com.microsoft.intune.mam.aad.SkipBroker"
            android:value="[true | false]" />

GUID 不應該有前端或後端的大括弧。

### ADAL 的常見設定 

以下是針對上述說明的值的常見設定。 

#### 應用程式未整合 ADAL

* 必須將授權設為所需的環境，而該環境當中已設定 AAD 帳戶。

* SkipBroker 必須設定為 true。

#### 應用程式已整合 ADAL

* 必須將授權設為所需的環境，而該環境當中已設定 AAD 帳戶。

* 用戶端識別碼必須設為應用程式的用戶端識別碼。

* `NonBrokerRedirectURI` 應設為有效的應用程式重新導向 URI。
    * Or `urn:ietf:wg:oauth:2.0:oob` 必須設為有效的 AAD 重新導向 URI。

* SkipBroker 必須設為 false (或不存在)。

* AAD 必須設為接受代理程式重新導向 URI。

#### 應用程式已整合 ADAL，但不支援 AAD 驗證器應用程式。

* 必須將授權設為所需的環境，而該環境當中已設定 AAD 帳戶。

* 用戶端識別碼必須設為應用程式的用戶端識別碼。

* `NonBrokerRedirectURI` 必須設為有效的應用程式重新導向 URI。

    * Or `urn:ietf:wg:oauth:2.0:oob` 應設為有效的 AAD 重新導向 URI。

## 如何啟用 SDK 中的記錄 

記錄是透過 `java.util.logging` 架構來完成。 若要接收記錄檔，請依照 [Java 技術指南](http://docs.oracle.com/javase/6/docs/technotes/guides/logging/overview.html)。 根據應用程式而定， `App.onCreate` 通常是起始記錄的最佳位置。 請注意，記錄檔訊息是特定於類別名稱，因此可能會有點模糊。

# 已知的平台限制 

## 檔案大小限制 

在 Android 上，Dalvik 可執行檔格式的限制可能會導致在不使用 ProGuard 執行大型程式碼基底時發生問題。 具體來說，可能會發生下列限制： 

* 65K 的欄位限制。

* 65K 的方法限制。

當包含許多專案時，每個 android:package 都會取得一份 R 複本，其會在新增程式庫時大幅增加欄位數目。 下列建議可能有助於解決這項限制：
 
* 所有程式庫專案應盡可能共用相同的 android:package。 這不會偶發性導致欄位失敗，而是純粹的建置時間問題。   此外，較新版本的 Android SDK 會預先處理 DEX 檔案，以移除冗餘部分。 這可更進一步減少欄位之間的距離。

* 使用可用的最新 Android SDK 建置工具。

* 移除所有不必要和未使用的程式庫 (例如 `android.support.v4`)

## 原則強制執行限制

**螢幕擷取**：SDK 無法強制執行 Activity 中已經透過 Activity.onCreate 完成的新螢幕擷取設定值。 這會導致應用程式已設定為停用螢幕擷取畫面一段時間，但仍可取得螢幕擷取畫面。

**使用內容解析程式*：傳送或接收原則可能會封鎖或部分封鎖內容解析程式的使用，不讓其存取另一個應用程式中的內容提供者。 這將導致 ContentResolver 方法傳回 null，或者擲回錯誤值 (例如，若受到封鎖， `openOutputStream` 將會擲回 `FileNotFoundException` )。 應用程式可以藉由呼叫下列項目，判斷透過內容解析程式無法寫入資料是否起因於原則 (或可能由原則造成)：

    MAMComponents.get(AppPolicy.class).getIsSaveToLocationAllowed(contentURI)

**匯出服務**：Intune App SDK 隨附的 `AndroidManifest.xml` 檔案包含 `MAMNotificationReceiverService`，其必須為匯出的服務，才能讓公司入口網站傳送通知給啟用 Intune App SDK 的應用程式。 服務會檢查呼叫者以確保僅允許公司入口網站傳送通知。 

# 建議的 Android 最佳作法 

Intune SDK 會維護由 Android API 所提供的合約，但可能會因為強制執行原則，而更頻繁地觸發失敗狀況。 下列 Android 最佳作法可降低失敗的可能性： 

* Android SDK 函式如果可能會傳回 null，則現在為 null 的可能性更高。  若要將問題降至最低，請確定 null 檢查是在正確的位置。

* 針對可以檢查的功能，必須透過其 SDK API 進行檢查。

* 任何衍生的函式皆必須透過其超級類別版本進行呼叫。

* 避免以模稜兩可的方式使用任何 API。 例如，未檢查 requestCode 的 `Activity.startActivityForResult/onActivityResult` 會導致奇怪的行為。



<!--HONumber=May16_HO2-->



---
title: "Microsoft Intune App SDK for Android 開發人員指南 | Microsoft Intune"
description: 
keywords: SDK
author: Msmbaldwin
manager: jeffgilb
ms.date: 09/08/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0100e1b5-5edd-4541-95f1-aec301fb96af
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: edbc701effb3817c2f9a160f05e7b5bc8ad0070e
ms.openlocfilehash: ee3a668a5415d14eb82e64e6bb16d9621bb13b57


---


# <a name="microsoft-intune-app-sdk-for-android-developer-guide"></a>Android 的 Microsoft Intune App SDK 開發人員指南

> [!NOTE]
> 您可能想要先閱讀 [Intune App SDK 概觀](intune-app-sdk.md)，其中涵蓋 SDK 目前的功能，並說明如何在每個支援的平台上進行整合準備。 

Android 的 Microsoft Intune App SDK 可讓您將 Intune 行動應用程式管理 (MAM) 併入 Android 應用程式中。 啟用 MAM 的應用程式是與 Intune App SDK 整合的應用程式，可讓 IT 系統管理員在 Intune 主動管理應用程式時將原則部署至行動應用程式。

# <a name="whats-in-the-sdk"></a>SDK 的功能 

Android 的 Microsoft Intune App SDK 是不含外部相依性的標準  Android 程式庫。 SDK 的組成項目包括：  

* **Microsoft.Intune.MAM.SDK.jar**：啟用 MAM 並與 Intune 公司入口網站應用程式互通所需的介面。 應用程式必須將其指定為 Android 程式庫參考。

* **Microsoft.Intune.MAM.SDK.Support.v4.jar**：在運用 Android v4 支援程式庫的應用程式中啟用 MAM 所需的介面。  需要這項支援的應用程式必須直接參考 jar 檔案。 

* **Microsoft.Intune.MAM.SDK.Support.v7.jar**：在運用 Android v7 支援程式庫的應用程式中啟用 MAM 所需的介面。 需要這項支援的應用程式必須直接參考 jar 檔案。

* **資源目錄**：SDK 所依賴的資源 (例如字串)。 

* **Microsoft.Intune.MAM.SDK.aar**：SDK 元件 (Support.V4 和 Support.V7 jar 除外)。 如果您的建置系統支援 AAR 檔案，則可以使用這個檔案來取代個別的元件。

* **AndroidManifest.xml**：其他的進入點和程式庫需求。 

* **THIRDPARTYNOTICES.TXT**：確認會編譯至應用程式中的協力廠商及/或 OSS 程式碼的屬性通知。 

# <a name="requirements"></a>需求 

Intune App SDK 是一種編譯過的 Android 專案。 因此，應用程式可針對其最低或目標 API 版本使用無特定的 Android 版本。 此 SDK 支援 Android API 14 (Android 4.0+) 到 Android API 24。 

Android 的 Intune App SDK 必須仰賴裝置上的[公司入口網站](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal)應用程式來啟用 MAM 原則。 針對沒有裝置註冊的 MAM，使用者**不**需要使用公司入口網站註冊裝置。


# <a name="how-the-intune-app-sdk-works"></a>Intune App SDK 的運作方式 

##<a name="entry-points"></a>進入點

Intune App SDK 需要變更應用程式的原始程式碼，以啟用 Intune 應用程式管理原則。 這是透過將 Android 基底類別取代為對等的 Intune 基底類別來完成，其名稱前面會加上 **MAM**。 SDK 類別的位置介於 Android 基底類別和應用程式本身針對該類別的衍生版本之間。  以活動為範例來看，最後您得到的繼承階層會像這樣：Activity > MAMActivity > AppSpecificActivity。

例如，當 **AppSpecificActivity** 與其父代互動時 (例如呼叫 `super.onCreate()`)，**MAMActivity** 是超級類別。 

一般而言，Android 應用程式擁有單一模式，並可透過其 [Context](https://developer.android.com/reference/android/content/Context.html) 物件存取系統。  另一方面，已經納入 Intune App SDK 的應用程式則具有雙重模式。 這些應用程式可以繼續透過 Context 物件存取系統，但根據使用的基底 Activity，Context 物件可能由 Android 提供，或在系統的限制檢視與 Android 所提供的 Context 之間以智慧方式多工處理。

在使用已覆寫為其 MAM 對等項目的 Android [進入點](https://developer.android.com/guide/components/fundamentals.html)時，必須使用進入點生命週期的 MAM 版本 (類別 **MAMApplication** 除外)。

例如，若是衍生自 **MAMActivity** 而不是覆寫 `onCreate` 然後呼叫 `super.onCreate` 時，Activity 必須覆寫 `onMAMCreate` 並呼叫 `super.onMAMCreate`。 這可讓 Intune 在某些情況下限制 Activity 啟動 (及其他項目)。 


##<a name="sdk-permissions"></a>SDK 權限

Intune App SDK 需要在與其整合的應用程式上，具有三個 [Android 系統權限](https://developer.android.com/guide/topics/security/permissions.html)：

* `android.permission.GET_ACCOUNTS`  [如有需要，則會在執行階段要求]
* `android.permission.MANAGE_ACCOUNTS`
* `android.permission.USE_CREDENTIALS`

Azure Active Directory Authentication Library ([ADAL](https://azure.microsoft.com/en-us/documentation/articles/active-directory-authentication-libraries/)) 需要這些權限才能執行代理驗證。 如果未將這些權限授與應用程式或使用者已撤銷這些權限，則會停用需要訊息代理程式 (公司入口網站應用程式) 的驗證流程。


##<a name="company-portal"></a>公司入口網站

為什麼需要公司入口網站應用程式？ 當公司入口網站安裝到裝置上，並已從 Intune 服務擷取使用者的應用程式限制原則時，即會以非同步方式初始化 SDK 進入點。 僅有在 Android 一開始建立處理序時才需要初始化。 在初始化期間，系統會與公司入口網站應用程式建立連線，並從應用程式擷取原則。  

> [!NOTE]
> 如果裝置上沒有公司入口網站應用程式，支援 Intune 的應用程式就不會改變行為，而會跟一般應用程式運作方式一樣。


# <a name="how-to-integrate-with-the-intune-app-sdk"></a>如何整合 Intune App SDK
 
如前所述，SDK 需要變更應用程式的原始程式碼，以啟用應用程式管理原則。 以下是在應用程式中啟用 MAM 所需的步驟： 

## <a name="replace-classes-methods-and-activities-with-their-mam-equivalent-required"></a>將類別、方法和活動取代為其 MAM 對等項目 (必要) 

您必須將 Android 基底類別取代為其各自的 MAM 對等項目。 若要這樣做，請找到下表所列類別的所有執行個體，並取代為 Intune App SDK 對等項目。 

| Android 基底類別 | Intune App SDK 取代 |
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
| android.app.PendingIntent | **MAMPendingIntent** * |
| android.app.Service | MAMService |
| android.app.TabActivity | MAMTabActivity |
| android.app.TaskStackBuilder | MAMTaskStackBuilder |
| android.app.backup.BackupAgent | MAMBackupAgent |
| android.app.backup.BackupAgentHelper | MAMBackupAgentHelper |
| android.app.backup.FileBackupHelper | MAMFileBackupHelper |
| android.app.backup.SharePreferencesBackupHelper | MAMSharedPreferencesBackupHelper |
| android.content.BroadcastReceiver | MAMBroadcastReceiver |
| android.content.ContentProvider | MAMContentProvider |
| android.os.Binder | **MAMBinder** (只有在 Binder 不是從 Android 介面定義語言 (AIDL) 介面產生時才需要) |
| android.provider.DocumentsProvider | MAMDocumentsProvider |
| android.preference.PreferenceActivity | MAMPreferenceActivity |


**Microsoft.Intune.MAM.SDK.Support.v4.jar**：

| Android 類別 Intune MAM | Intune App SDK 取代 |
|--|--|
| android.support.v4.app.DialogFragment | MAMDialogFragment
| android.support.v4.app.FragmentActivity | MAMFragmentActivity
| android.support.v4.app.Fragment | MAMFragment
| android.support.v4.app.TaskStackBuilder | MAMTaskStackBuilder
| android.support.v4.content.FileProvider | MAMFileProvider
    
**Microsoft.Intune.MAM.SDK.Support.v7.jar**：

|Android 類別 | Intune App SDK 取代 |
|--|--|
|android.support.v7.app.ActionBarActivity | MAMActionBarActivity |

>[!NOTE]
>請記住，在使用已覆寫為其 MAM 對等項目的 Android [進入點](https://developer.android.com/guide/components/fundamentals.html)時，必須使用進入點生命週期的 MAM 版本 (類別 **MAMApplication** 除外)。
>
>例如，若是衍生自 **MAMActivity** 而不是覆寫 `onCreate` 然後呼叫 `super.onCreate` 時，Activity 必須覆寫 `onMAMCreate` 並呼叫 `super.onMAMCreate`。 這可讓 Intune 在某些情況下限制 Activity 啟動 (及其他項目)。 

### <a name="pendingintents-and-renamed-methods"></a>PendingIntents 和重新命名的方法 

衍生自其中一個 MAM 進入點之後，即可放心以正常方式使用 Context，以利用其 **PackageManager** 等項目來啟動 Activity。  

此規則的例外是 **PendingIntents**。 呼叫這種類別時，您需要變更類別名稱。 例如，必須使用 `MAMPendingIntents.get*` 方法，而不是 `PendingIntent.get*`。 之後，即可以正常方式使用結果 **PendingIntents**。

在某些情況下，Android 類別中可用的方法已在 MAM 取代類別中被標示為完稿。 在此情況下，MAM 取代類別會提供類似的具名方法 (通常後置字元為 "MAM")，您應將其覆寫。 例如，您應覆寫 `ContentProvider.query`而不是覆寫 `MAMContentProvider.queryMAM`。 Java 編譯器應該強制執行完稿的限制，以防止意外覆寫原始的方法，而不是 MAM 對等項目。 

##<a name="enable-features-that-require-app-participation"></a>啟用需要應用程式參與的功能 

SDK 無法自行實作部分原則。 此應用程式可控制其行為，以使用可在下面包含的 **AppPolicy** 介面中找到的幾個 API，來達成這些功能。  

```
/**
 * External facing application policies.
 */
public interface AppPolicy {

/**
 * Restrict where an app can save personal data.
 * <strong>This function is now deprecated. Please use {@link #getIsSaveToLocationAllowed(SaveLocation, String)} instead</strong>
 * @return True if the app is allowed to save to personal data stores; false otherwise.
 */
@Deprecated
boolean getIsSaveToPersonalAllowed();

/**
 * Check if policy prohibits saving to a content provider location.
 * 
 * @param location
 *            a content URI to check
 * @return True if location is not a content URI or if policy does not prohibit saving to the content location.
 */
boolean getIsSaveToLocationAllowed(Uri location);

/**
 * Determines if the SaveLocation passed in can be saved to by the username associated with the cloud service.
 *
 * @param service
 *           see {@link SaveLocation}.
 * @param username
 *           the username/email associated with the cloud service being saved to. Use null if a mapping between the AAD username and the cloud service username does not exist or the username is not known.
 * @return true if the location can be saved to by the identity, false if otherwise.
 */
boolean getIsSaveToLocationAllowed(SaveLocation service, String username);

/**
 * Whether the SDK PIN prompt is enabled for the app.
 * 
 * @return True if the PIN is enabled. False otherwise.
 */
boolean getIsPinRequired();

/**
 * Whether the Intune Managed Browser is required to open web links.
 * @return True if the Managed Browser is required, false otherwise
 */
boolean getIsManagedBrowserRequired();

/**
 * Check if policy allows Contact sync to local contact list.
 * 
 * @return True if Contact sync is allowed to save to local contact list; false otherwise.
 */
boolean getIsContactSyncAllowed();

/**
 * Return the policy in string format to the app.
 *  
 * @return The string representing the policy.
 */
String toString();


}

```

## <a name="enable-it-control-over-app-saving-behavior"></a>讓 IT 人員可控制應用程式的儲存行為

許多應用程式實作功能，可讓使用者將檔案儲存於本機或儲存至雲端儲存體服務。 Intune App SDK 可讓 IT 系統管理員套用組織適用的原則限制，以防資料外洩。  IT 人員可以控制的其中一項原則是，使用者是否可以儲存至未受管理的「個人」資料存放區。 這包括儲存至本機位置、SD 記憶卡或協力廠商備份服務。 

**啟用此功能需要應用程式參與。** 如果您的應用程式可直接從應用程式儲存至個人或雲端位置，您就必須實作此功能，以確保 IT 系統管理員能控制是否允許儲存至某個位置。 下列 API 可讓應用程式知道目前的 Intune 系統管理員原則是否允許儲存到個人存放區。 接著，應用程式即可強制執行原則，因為它會感知使用者透過應用程式可使用的個人資料存放區。  

為了判斷原則是否要強制執行，應用程式可以進行下列呼叫： 

```
MAMComponents.get(AppPolicy.class).getIsSaveToPersonalAllowed();
```

**注意**：`MAMComponents.get(AppPolicy.class)` 一律會傳回非 null 的應用程式原則，即使裝置或應用程式不受 Intune 管理原則限制亦同。 

## <a name="allow-app-to-detect-if-pin-policy-is-required"></a>可讓應用程式偵測是否需要 PIN 原則
 
針對某些 Intune 應用程式限制，您可能需要讓應用程式停用其中一些功能，才不會重複 Intune App SDK 中的功能。 例如，假設應用程式有自己的 PIN 使用者體驗，若 SDK 已設定為需要使用者輸入 PIN，則應用程式可能需要停用此功能。 

為了判斷 Intune PIN 原則是否已設定為啟動時要求輸入應用程式 PIN，應用程式可以進行下列呼叫： 

```
MAMComponents.get(AppPolicy.class).getIsPinRequired();
```

## <a name="registering-for-notifications-from-the-sdk"></a>透過 SDK 註冊通知  

當 IT 系統管理員部署特定原則時 (例如選擇性抹除)，Intune App SDK 可讓您的應用程式控制其行為。 當 IT 系統管理員部署這類原則時，Intune 服務會傳送通知給 SDK。

您的應用程式必須透過 SDK 註冊通知，方法是建立 **MAMNotificationReceiver** 類別並向 **MAMNotificationReceiverRegistry** 註冊。 這是藉由提供接收者以及想要在 `App.onCreate` 中接收的通知類型來完成，如下列範例所示：

``` 
@Override
public void onCreate() {
    super.onCreate();
    MAMComponents.get(MAMNotificationReceiverRegistry.class)
.registerReceiver(
                new ToastNotificationReceiver(),
MAMNotificationType.WIPE_USER_DATA);
    }
```

**MAMNotificationReceiver** 只會透過 Intune 服務接收通知。 有些通知是由 SDK 直接處理，有些則需要應用程式的參與。 

應用程式**必須**針對通知傳回 true 或 false。 

除非基於通知結果，應用程式嘗試採取的某些動作失敗，否則一律會傳回 true。 

* 這類失敗可能會回報給 Intune 服務。 例如，如果在 IT 系統管理員起始抹除之後，應用程式無法抹除使用者資料，就會進行回報。 

您可以放心封鎖 `MAMNotificationReceiver.onReceive`，因為其回呼不會在 UI 執行緒上執行。 

下方包含 **MAMNotificationReceiver** 介面，如 SDK 所定義： 

```
/**
 * The SDK is signaling that a WG event has occurred. 
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

```

##<a name="types-of-notifications"></a>通知類型
下列通知會傳送至應用程式，且其中部分通知可能需要應用程式參與： 

* **`WIPE_USER_DATA`**︰這項通知是在 **MAMUserNotification** 類別中傳送。 應用程式收到這項通知時，必須刪除與 **MAMUserNotification** 一起傳遞之「公司」身分識別相關聯的所有資料。 這項通知目前會在 Intune 服務取消註冊期間傳送。 使用者主要名稱通常會在註冊程序期間指定。 如果您註冊這項通知，您的應用程式必須確定所有使用者資料都已刪除。 如果您未註冊，就會執行預設的選擇性抹除行為。

* **`WIPE_USER_AUXILIARY_DATA`**：如果應用程式要 Intune App SDK 執行預設選擇性抹除行為，但仍想要在抹除發生時移除部分輔助資料，則可註冊這項通知。  

* **`REFRESH_POLICY`**︰這項通知是在 **MAMUserNotification** 中傳送。 收到這項通知時，所有快取的 Intune 原則都必須處於失效狀態並加以更新。 通常，SDK 會處理這項作業，不過如果原則是以任何持續性的方式使用，則應該由應用程式來處理。 



## <a name="protecting-backup-data"></a>保護備份資料 

截至 Android Marshmallow (API 23) 止，Android 提供兩種可讓應用程式備份資料的方法。 您可在應用程式中使用這些選項，但需要不同的步驟以確保正確實作 Intune 資料保護。 您可以檢閱下表，以了解正確資料保護行為所需的相對應動作。  您可以在 [Android API 指南](http://developer.android.com/guide/topics/data/backup.html)中深入了解備份方法。 

### <a name="auto-backup-for-apps"></a>應用程式的自動備份

Android 開始在 Android Marshmallow 裝置上提供應用程式的[自動完整備份](https://developer.android.com/guide/topics/data/autobackup.html)，而不論應用程式的目標 API 為何。 在您的 AndroidManifest.xml 中，如果您將 `android:allowBackup` 明確設定為 **false**，則 Android 永遠不會將您的應用程式排入佇列進行備份，而且「公司」資料會保留在應用程式內。 在這種情況下，並不需要採取任何進一步的動作。

不過，`android:allowBackup` 屬性預設會設定為 true，即使未在資訊清單檔中指定 `android:allowBackup` 亦然。 這表示所有應用程式資料都會自動備份至使用者的 Google 雲端硬碟帳戶，此預設行為會造成**資料洩漏的風險**。 因此，SDK 需進行下列所述的變更，以確保套用資料保護。  如果您想要讓應用程式在 Android Marshmallow 裝置上執行，請務必遵循下列方針，以妥善保護客戶資料。  

*  如果您尚未撰寫備份代理程式，以使用 **MAMBackupAgent** 或 **MAMBackupAgentHelper** 來備份您的應用程式，則您必須考慮並控制如何透過自動備份來上傳應用程式資料。 Intune 可讓您利用 Android 中可用的所有[自動備份功能](https://developer.android.com/guide/topics/data/autobackup.html)，包括在 XML 中定義自訂規則的功能，但您必須遵循下列步驟來保護資料：

    1. 使用預設 MAMBackupAgent 以允許進行與 Intune 原則相容的自動完整備份。 將 `android:backupAgent="com.microsoft.intune.mam.client.app.backup.MAMDefaultBackupAgent"` 放在您的應用程式資訊清單中。 
    2. 當您決定應用程式應該接收的完整備份類型 (未篩選、已篩選或無) 時，您必須將將屬性 `android:fullBackupContent` 設定為 true、false，或您應用程式中的 XML 資源。 請將您放入 `android:fullBackupContent` 的任何內容複製到名為 `com.microsoft.intune.mam.FullBackupContent` 的 Metadata 標記中

    **範例**︰如果您想要讓應用程式根據 XML 檔案中的自訂規則進行完整備份，請提供資訊清單中 `com.microsoft.intune.mam.FullBackupContent` Metadata 標記下的資源，例如： 
    ```
    <meta-data android:name="com.microsoft.intune.mam.FullBackupContent" android:resource="@xml/my_scheme" />  
    ```



### <a name="keyvalue-backup"></a>金鑰/值備份

此選項適用於所有 API，並會使用 `BackupAgent` 和 `BackupAgentHelper`。 

#### <a name="using-backupagenthelper"></a>使用 BackupAgentHelper

`BackupAgentHelper` 都比 `BackupAgent` 容易實作。 `BackupAgentHelper` 可讓開發人員分別向 `FileBackupHelper` 或 `SharedPreferencesBackupHelper`註冊整個檔案和共用的喜好設定，並在建立 `BackupAgentHelper` 時將其加入。 

#### <a name="using-backupagent"></a>使用 BackupAgent

`BackupAgent` 可讓您更明確了解備份了哪些資料。 不過，使用此選項表示您將無法利用 Android 備份架構的優勢。  由於您是主要負責實作的人，因此比起 MAM，您必須進行更多的步驟才能確保適當的資料保護效果。 由於大部分工作都落在開發人員 (也就是您) 身上，因此有略多的作業涉及 MAM 的整合。 

##### <a name="app-does-not-have-a-backup-agent"></a>應用程式沒有備份代理程式
  
當 `android:allowBackup =true`：

###### <a name="full-back-up-according-to-a-configuration-file"></a>根據組態檔，進行完整備份： 

在程式資訊清單中的 `com.microsoft.intune.mam.FullBackupContent` METADATA 標記下方提供資源。 例如：    `<meta-data android:name="com.microsoft.intune.mam.FullBackupContent" android:resource="@xml/my_scheme" />`

將下列屬性加入 `<application>` 標記中： `android:fullBackupContent="@xml/my_scheme"`，其中 `my_scheme` 是應用程式中的 XML 資源。 

###### <a name="full-back-dup-without-exclusions"></a>沒有排除項目的完整備份 

提供資訊清單中的標記，例如 `<meta-data android:name="com.microsoft.intune.mam.FullBackupContent" android:value="true" />` 
 
將下列屬性新增至 `<application>` 標記：`android:fullBackupContent="true"`。

##### <a name="app-has-a-backup-agent"></a>應用程式有備份代理程式

請遵循 `BackupAgent` 和 `BackupAgentHelper` 章節中的建議，如上所述。 

請考慮改用我們的 `MAMDefaultFullBackupAgent`，它提供簡易的 Android M 備份功能。 

#### <a name="before-your-backup"></a>在您備份之前

開始備份之前，您必須確認打算備份的檔案或資料緩衝區確實可以備份。 我們已在 `isBackupAllowed` 和 `MAMFileProtectionManager` 和 `MAMDataProtectionManager` 函式供您判斷。 如果檔案或資料緩衝區不能備份，您就不必在備份中繼續嘗試使用。

在備份期間，如果您想要備份在步驟 1 中檢查過的檔案識別，就必須使用準備擷取其資料的檔案來呼叫 `backupMAMFileIdentity(BackupDataOutput data, File … files)`。 這會自動建立新的備份實體，並將其寫入 `BackupDataOutput` 。 在還原時會自動使用這些實體。 

### <a name="configure-azure-directory-authentication-library-adal"></a>設定 Azure Directory Authentication Library (ADAL)  

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

#### <a name="common-adal-configurations"></a>ADAL 的常見設定 

以下是針對上述說明的值的常見設定。 

##### <a name="app-does-not-integrate-adal"></a>應用程式未整合 ADAL

* 必須將授權設為所需的環境，而該環境當中已設定 AAD 帳戶。

* SkipBroker 必須設定為 true。

##### <a name="app-integrates-adal"></a>應用程式已整合 ADAL

* 必須將授權設為所需的環境，而該環境當中已設定 AAD 帳戶。

* 用戶端識別碼必須設為應用程式的用戶端識別碼。

* `NonBrokerRedirectURI` 應設為有效的應用程式重新導向 URI。
    * Or `urn:ietf:wg:oauth:2.0:oob` 必須設為有效的 AAD 重新導向 URI。

* SkipBroker 必須設為 false (或不存在)。

* AAD 必須設為接受代理程式重新導向 URI。

##### <a name="app-integrates-adal-but-does-not-support-the-aad-authenticator-app"></a>應用程式已整合 ADAL，但不支援 AAD 驗證器應用程式。

* 必須將授權設為所需的環境，而該環境當中已設定 AAD 帳戶。

* 用戶端識別碼必須設為應用程式的用戶端識別碼。

* `NonBrokerRedirectURI` 必須設為有效的應用程式重新導向 URI。

    * Or `urn:ietf:wg:oauth:2.0:oob` 應設為有效的 AAD 重新導向 URI。

### <a name="how-to-enable-logging-in-the-sdk"></a>如何啟用 SDK 中的記錄 

記錄是透過 `java.util.logging` 架構來完成。 若要接收記錄檔，請依照 [Java 技術指南](http://docs.oracle.com/javase/6/docs/technotes/guides/logging/overview.html)。 根據應用程式而定， `App.onCreate` 通常是起始記錄的最佳位置。 請注意，記錄檔訊息是特定於類別名稱，因此可能會有點模糊。

##<a name="multiidentity"></a>多重身分識別
###<a name="overview"></a>概觀
Intune App SDK 預設會將原則套用至應用程式整體。 多重身分識別是一個 MAM 功能，可以啟用以允許將原則套用至每個身分識別層級。  這需要的應用程式參與明顯高於其他 MAM 功能。 需要有應用程式，才能在想要變更使用中身分識別時通知 App SDK；需要身分識別變更時，SDK 也會通知應用程式。 目前僅支援一個受管理的身分識別。 使用者註冊裝置或應用程式之後，SDK 會使用這個身分識別，並將其視為主要受管理身分識別。 應用程式中的其他使用者則會因不受限制原則設定而視為不受管理。 

請注意，身分識別只會定義為字串。 身分識別不區分大小寫，而且身分識別的 SDK 要求可能不會傳回設定身分識別時原本使用的相同大小寫。

###<a name="enabling-multiidentity"></a>啟用多重身分識別
根據預設，所有應用程式都會視為單一身分識別應用程式。 應用程式會藉由將下列中繼資料放在 Android 資訊清單中，來宣告它可感知多重身分識別。

```
<meta-data
            android:name="com.microsoft.intune.mam.MAMMultiIdentity"
            android:value="true" />
```
###<a name="setting-the-identity"></a>設定身分識別

開發人員可以設定應用程式在下列層級的身分識別： 
1. 處理程序層級 
2. 內容 (通常是活動) 層級 
3. 執行緒層級 

在執行緒層級設定的身分識別會取代內容層級設定的身分識別，而在內容層級設定的身分識別會取代在處理程序層級設定的身分識別。 只有在適當情況下才會使用內容上所設定的身分識別。 例如，檔案 IO 操作沒有相關聯的內容。 MAMPolicyManager 的下列方法可用來設定身分識別，並擷取之前設定的身分識別值。

```
public static void setUIPolicyIdentity(final Context context, final String identity, final MAMSetUIIdentityCallback mamSetUIIdentityCallback);

public static String getUIPolicyIdentity(final Context context);

public static MAMIdentitySwitchResult setProcessIdentity(final String identity);

public static String getProcessIdentity();

public static MAMIdentitySwitchResult setCurrentThreadIdentity(final String identity);

public static String getCurrentThreadIdentity();

/**
 * Get the currently applicable app policy. Same as MAMComponents.get(AppPolicy.class). This method does
    not take the context identity into account.
 */
public static AppPolicy getPolicy();

/**
 * Get the currently applicable app policy, taking the context
 * identity into account.
 */
public static AppPolicy getPolicy(final Context context);


public static AppPolicy getPolicyForIdentity(final String identity);

public static boolean getIsIdentityManaged(final String identity);

```
您也可以清除應用程式的身分識別，方法是將它設定為 null。 使用空字串作為身分識別時永遠都不會有限制。 設定身分識別的所有方法都會透過 ``` MAMIdentitySwitchResult``` 回報結果值。 有四個可能傳回的值：

1.**SUCCEEDED**︰身分識別變更成功 2.**NOT_ALLOWED**︰不允許身分識別變更。 如果嘗試切換至屬於同一家公司的不同公司使用者作為註冊的使用者，就會發生此情況。 如果在目前執行緒上已設定不同身分識別的情況下，嘗試設定 UI (內容) 身分識別，也會發生此情況。
3.**CANCELLED**︰使用者已取消身分識別變更，通常是在出現 PIN/驗證提示時按 [上一頁] 按鈕。
4.**FAILED**︰不明的原因導致身分識別變更失敗。

如果設定內容身分識別，則會以非同步方式報告結果。 如果內容是活動，在執行可能需要使用者輸入 PIN 或其完整公司認證的條件式啟動之前，將無法得知身分識別變更是否成功。 應用程式必須實作 ```MAMSetUIIdentityCallback``` 才能接收此結果，不過它可以傳遞 null 作為此參數。

```
public interface MAMSetUIIdentityCallback {
    void notifyIdentityResult(MAMIdentitySwitchResult identitySwitchResult); 
}
```

您也可以直接透過 MAMActivity 上的方法來設定活動的身分識別，而不是呼叫 ``` MAMPolicyManager.setUIPolicyIdentity```。 您可以使用下列方法來執行這項操作：

 ```public final void switchMAMIdentity(final String newIdentity);```

應用程式也可覆寫 MAMActivity 上的方法，以收到嘗試變更該活動身分識別的結果通知 

```public void onSwitchMAMIdentityComplete(final MAMIdentitySwitchResult result);```

**注意**︰切換身分識別可能需要重新建立活動。 在此情況下，```onSwitchMAMIdentityComplete``` 回呼會傳遞至活動的新執行個體。

###<a name="implicit-identity-changes"></a>隱含身分識別變更

除了應用程式能夠設定身分識別之外，執行緒或內容的身分識別也可能會根據另一個啟用 MAM 之應用程式所輸入的資料而變更。 例如，如果根據另一個 MAM 應用程式所傳送之意圖來啟動活動，就會根據另一個應用程式在送出意圖時的有效身分識別，來設定活動的身分識別。
針對服務，執行緒的身分識別會在 onStart 或 onBind 呼叫期間有類似的設定。 呼叫從 onBind 傳回的 Binder 也會暫時設定執行緒身分識別。
呼叫 ```ContentProvider``` 同樣會在該期間設定執行緒身分識別。
此外，使用者與活動互動可能會導致隱含身分識別切換。
例如，使用者在 ```Resume``` 期間取消授權提示，就會導致隱含切換至空的身分識別。
應用程式有機會注意到這些變更，並在某些情況下視需要禁止變更。 ```MAMService``` 和 ```MAMContentProvider``` 會公開子類別可能覆寫的下列方法：

```
public void onMAMIdentitySwitchRequired(final String identity,
    final AppIdentitySwitchResultCallback callback);
```
如果是 ```MAMActivity```，方法中會出現額外的參數： 
```
public void onMAMIdentitySwitchRequired(final String identity, 
    final AppIdentitySwitchReason reason,
    final AppIdentitySwitchResultCallback callback);
```
```AppIdentitySwitchReason``` 會擷取隱含切換的來源，並可接受 ```CREATE```、```RESUME_CANCELLED``` 和 ```NEW_INTENT``` 值。  當活動繼續導致顯示 PIN、驗證或其他相容性 UI，而且使用者嘗試取消該 UI (通常是透過使用 [上一頁] 按鈕) 時，就會使用 ```RESUME_CANCELLED``` 原因。
```AppIdentitySwitchResultCallback``` 如下所示：
```
public interface AppIdentitySwitchResultCallback {
    /**
     * @param result
     *            whether the identity switch can proceed.
     */
    void reportIdentitySwitchResult(AppIdentitySwitchResult result);
}
```
其中 ```AppIdentitySwitchResult``` 是 ```SUCCESS``` 或 ```FAILURE```。 

針對所有隱含身分識別變更會呼叫 ```onMAMIdentitySwitchRequired``` 方法 (透過從 ```MAMService.onMAMBind``` 傳回的 Binder 進行的變更除外)。 在其他所有情況下，當原因為 ```RESUME_CANCELLED``` 和 ```reportIdentitySwitchResult(SUCCESS)``` 時，```onMAMIdentitySwitchRequired``` 的預設實作會立即呼叫 ```reportIdentitySwitchResult(FAILURE)```。 

大多數應用程式不一定需要透過不同方式來封鎖或延遲身分識別切換，但如果應用程式需要這樣做，則必須考慮下列重點：*如果封鎖身分識別切換，結果會如同共用設定的 ```Receive``` 已禁止資料輸入。*如果服務正在主執行緒上執行，則**必須**同步呼叫 ```reportIdentitySwitchResult```，否則 UI 執行緒將會停止回應。 
*針對 ```Activity``` 建立，在 ```onMAMCreate``` 之前會呼叫 ```onMAMIdentitySwitchRequired```。如果應用程式必須顯示 UI，以判斷是否允許身分識別切換，則必須使用不同的活動顯示該 UI。*在活動中，如果以相當於 ```RESUME_CANCELLED``` 的原因要求切換至空的身分識別，則應用程式必須修改繼續的活動，以顯示與該身分識別切換一致的資料。  如果不可行，應用程式應該拒絕切換，並再次要求使用者符合原則以繼續身分識別 (例如藉由顯示 PIN 輸入畫面)。 

**注意**︰多重身分識別應用程式永遠會從受管理和未受管理的應用程式接收內送資料。 應用程式會負責以受管理的方式來處理受管理身分識別中的資料。 如果要求的身分識別是受管理的 ```(MAMPolicyManager.getIsIdentityManaged)```，但應用程式因必須先在應用程式中設定帳戶 (例如電子郵件帳戶) 而無法使用該帳戶，則應該拒絕身分識別切換。

##<a name="file-protection"></a>檔案保護
每個檔案都有建立時根據執行緒和處理程序身分識別而來的相關聯身分識別。 此身分識別將會用於檔案加密和選擇性抹除。 只有其身分識別具有需要加密之原則的檔案才會進行加密。 SDK 的預設選擇性抹除只會抹除與已要求抹除之身分識別相關聯的檔案。 應用程式可使用 ```MAMFileProtectionManager``` 查詢或變更檔案的身分識別
```
public final class MAMFileProtectionManager {

    /**
     * Protect a file. This will synchronously trigger whatever protection is required for the file, and will tag the file for
     * future protection changes.
     * 
     * @param identity
     *            Identity to set.
     * @param file
     *            File to protect.
     * @throws IOException
     *             If the file cannot be changed.
     */
    public static void protect(final File file, final String identity) throws IOException;

    /**
     * Get the protection info on a file.
     * 
     * @param file
     *            File or directory to get information on.
     * @return File protection info, or null if there is no protection info.
     * @throws IOException
     *             If the file cannot be read or opened.
     */
    public static MAMFileProtectionInfo getProtectionInfo(final File file) throws IOException;
}

public interface MAMFileProtectionInfo {
String getIdentity();
}
```

**注意**︰離線模式需要檔案身分識別標記。 下列各點應該列入考量。
* 如果未安裝公司入口網站，則無法標記檔案的身分識別。 
* 如果已安裝公司入口網站，但應用程式沒有原則，則無法確實標記檔案的身分識別。
* 當檔案身分識別標記變成可用時，所有先前建立的檔案都會視為個人 (屬於空字串身分識別)，除非應用程式之前已安裝為受單一身分識別管理的應用程式，在此情況下則會視為屬於已註冊的使用者。

###<a name="data-protection"></a>資料保護
您無法將檔案標記為屬於多重身分識別。 如果應用程式必須將屬於不同使用者的資料儲存到同一個檔案，則可以使用 ```MAMDataProtectionManager``` 所提供的功能手動執行這項操作。 這可讓應用程式加密資料，並將它繫結至特定的使用者。 加密資料適合存放到磁碟的檔案中。 您可以查詢與身分識別相關聯的資料，並於稍後解密資料。 

```
public final class MAMDataProtectionManager {
    /**
     * Protect a stream. This will return a stream containing the protected 
 * input.
     * 
     * @param identity
     *            Identity to set.
     * @param input
     *            Input data to protect, read sequentially. This function 
 *            will change the position of the stream but may not have
     *            read the entire stream by the time it returns. The 
 *            returned stream will wrap this one. Calls to read on the
     *            returned stream may cause further reads on the original 
 *            input stream. Callers should not expect to read directly
     *            from the input stream after passing it to this method. 
 *            Calling close on the returned stream will close this one.
     * @return Protected input data.
     * @throws IOException
     *             If the data could not be protected
     */
    public static InputStream protect(final InputStream input, final String identity);

    /**
     * Protect a byte array. This will return protected bytes.
     * 
     * @param identity
     *            Identity to set.
     * @param input
     *            Input data to protect.
     * @return Protected input data.
     * @throws IOException
     *             If the data could not be protected
     */
    public static byte[] protect(final byte[] input, final String identity) throws IOException;

    /**
     * Unprotect a stream. This will return a stream containing the 
 * unprotected input.
     * 
     * @param input
     *            Input data to protect, read sequentially.
     * @return Protected input data.
     * @throws IOException
     *             If the data could not be unprotected
     */
    public static InputStream unprotect(final InputStream input) throws IOException;

    /**
     * Unprotect a byte array. This will return unprotected bytes.
     * 
     * @param input
     *            Input data to protect.
     * @return Protected input data.
     * @throws IOException
     *             If the data could not be unprotected
     */
    public static byte[] unprotect(final byte[] input) throws IOException;

    /**
     * Get the protection info on a stream.
     * 
     * @param input
     *            Input stream to get information on. Either this input 
 *            stream must have been returned by a previous call to 
     *            protect OR input.markSupported() must return true. 
 *            Otherwise it will be impossible to get protection info 
 *            without advancing the stream position. The stream must be 
 *            positioned at the beginning of the protected data.
     * @return Data protection info, or null if there is no protection 
 *            info.
     * @throws IOException
     *             If the input cannot be read.
     */
    public static MAMDataProtectionInfo getProtectionInfo(final InputStream input) throws IOException;

    /**
     * Get the protection info on a stream.
     * 
     * @param input
     *            Input bytes to get information on. These must be bytes 
 *            returned by a previous call to protect() or a copy of 
 *            such bytes.
     * @return Data protection info, or null if there is no protection 
 *            info.
     * @throws IOException
     *             If the input cannot be read.
     */
    public static MAMDataProtectionInfo getProtectionInfo(final byte[] input) throws IOException;
}
```
##<a name="content-providers"></a>內容提供者
如果應用程式透過 ```ContentProvider``` 提供 ```ParcelFileDescriptor``` 以外的潛在公司資料，應用程式必須呼叫 ```MAMContentProvider``` 方法 ```isProvideContentAllowed(String)```，並傳遞內容的 ```UPN``` 給擁有者。 如果此函數傳回 false，內容可能不會傳回給呼叫者。 透過內容提供者傳回的檔案描述元會自動根據檔案身分識別進行處理。

##<a name="selective-wipe"></a>選擇性抹除
如果應用程式註冊 ```WIPE_USER_DATA``` 通知，則不會得到 SDK 預設選擇性抹除行為的好處。 針對感知多重身分識別的應用程式，這可能更為明顯，因為 MAM 預設選擇性抹除只會抹除符合要抹除之身分識別的檔案。 如果您要建立感知多重身分識別的應用程式，您可以註冊 ```WIPE_USER_AUXILIARY_DATA```，如此將可讓您利用 SDK 預設抹除行為。 系統會立即傳送這項通知，再執行 SDK 預設選擇性抹除。 請注意，應用程式永遠都不應該同時註冊 ```WIPE_USER_DATA``` 和 ```WIPE_USER_AUXILIARY_DATA```。

## <a name="known-platform-limitations"></a>已知的平台限制 

### <a name="file-size-limitations"></a>檔案大小限制 

在 Android 上，Dalvik 可執行檔格式的限制可能會導致在不使用 ProGuard 執行大型程式碼基底時發生問題。 具體來說，可能會發生下列限制： 

* 65K 的欄位限制。

* 65K 的方法限制。

當包含許多專案時，每個 android:package 都會取得一份 R 複本，其會在新增程式庫時大幅增加欄位數目。 下列建議可能有助於解決這項限制：
 
* 所有程式庫專案應盡可能共用相同的 android:package。 這不會偶發性導致欄位失敗，而是純粹的建置時間問題。   此外，較新版本的 Android SDK 會預先處理 DEX 檔案，以移除冗餘部分。 這可更進一步減少欄位之間的距離。

* 使用可用的最新 Android SDK 建置工具。

* 移除所有不必要和未使用的程式庫 (例如 `android.support.v4`)

### <a name="policy-enforcement-limitations"></a>原則強制執行限制

**螢幕擷取**：SDK 無法強制執行 Activity 中已經透過 Activity.onCreate 完成的新螢幕擷取設定值。 這會導致應用程式已設定為停用螢幕擷取畫面一段時間，但仍可取得螢幕擷取畫面。

使用內容解析程式：*傳送或接收原則可能會封鎖或部分封鎖內容解析程式的使用，不讓其存取另一個應用程式中的內容提供者。 這將導致 ContentResolver 方法傳回 null，或者擲回錯誤值 (例如，若受到封鎖， `openOutputStream` 將會擲回 `FileNotFoundException` )。 應用程式可以藉由呼叫下列項目，判斷透過內容解析程式無法寫入資料是否起因於原則 (或可能由原則造成)：

    MAMComponents.get(AppPolicy.class).getIsSaveToLocationAllowed(contentURI)

**匯出服務**：Intune App SDK 隨附的 `AndroidManifest.xml` 檔案包含 `MAMNotificationReceiverService`，其必須為匯出的服務，才能讓公司入口網站傳送通知給啟用 Intune App SDK 的應用程式。 服務會檢查呼叫者以確保僅允許公司入口網站傳送通知。 

## <a name="recommended-android-best-practices"></a>建議的 Android 最佳作法 

Intune SDK 會維護由 Android API 所提供的合約，但可能會因為強制執行原則，而更頻繁地觸發失敗狀況。 下列 Android 最佳作法可降低失敗的可能性： 

* Android SDK 函式如果可能會傳回 null，則現在為 null 的可能性更高。  若要將問題降至最低，請確定 null 檢查是在正確的位置。

* 針對可以檢查的功能，必須透過其 SDK API 進行檢查。

* 任何衍生的函式皆必須透過其超級類別版本進行呼叫。

* 避免以模稜兩可的方式使用任何 API。 例如，未檢查 requestCode 的 `Activity.startActivityForResult/onActivityResult` 會導致奇怪的行為。






<!--HONumber=Oct16_HO5-->



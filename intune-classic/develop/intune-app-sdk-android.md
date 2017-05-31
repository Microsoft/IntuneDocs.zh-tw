---
title: "Microsoft Intune App SDK for Android 開發人員指南 | Microsoft Docs"
description: "Microsoft Intune App SDK for Android 可讓您將 Intune 行動應用程式管理 (MAM) 併入 Android 應用程式中。"
keywords: SDK
author: mtillman
manager: angrobe
ms.author: mtillman
ms.date: 12/15/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0100e1b5-5edd-4541-95f1-aec301fb96af
ms.reviewer: oydang
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 973e97c7dc5f16df93d2c74546b9a4c6c05a0354
ms.contentlocale: zh-tw
ms.lasthandoff: 05/31/2017


---


# <a name="microsoft-intune-app-sdk-for-android-developer-guide"></a>Microsoft Intune App SDK for Android 開發人員指南

> [!NOTE]
> 您可能想要先閱讀 [Intune App SDK 概觀](intune-app-sdk.md)，其中涵蓋 SDK 目前的功能，並說明如何在每個支援的平台上進行整合準備。

Microsoft Intune App SDK for Android 可讓您將 Intune 應用程式保護原則 (也稱為 **APP** 或 MAM 原則) 併入原生 Android 應用程式中。 「可搭配 Intune 的應用程式」是與 Intune App SDK 整合的應用程式。 Intune 系統管理員可在 Intune 主動管理應用程式時，輕鬆地將應用程式保護原則部署至可搭配 Intune 的應用程式。


## <a name="whats-in-the-sdk"></a>SDK 的功能

Intune App SDK 包含下列檔案：  

* **Microsoft.Intune.MAM.SDK.aar**：SDK 元件 (Support.V4 和 Support.V7 JAR 檔案除外)。 如果您的建置系統支援 AAR 檔案，則可以使用這個檔案來取代個別的元件。
* **Microsoft.Intune.MAM.SDK.Support.v4.jar**：在使用 Android v4 支援程式庫的應用程式中啟用 MAM 所需的介面。 需要這項支援的應用程式必須直接參考 JAR 檔案。
* **Microsoft.Intune.MAM.SDK.Support.v7.jar**：在使用 Android v7 支援程式庫的應用程式中啟用 MAM 所需的介面。 需要這項支援的應用程式必須直接參考 JAR 檔案。
* **proguard.txt**：包含使用 ProGuard 進行建置時必須套用的 ProGuard 規則。
* **CHANGELOG.txt**：提供每個 SDK 版本中的變更記錄。
* **THIRDPARTYNOTICES.TXT**：確認將會編譯至應用程式中的協力廠商及/或 OSS 程式碼的屬性通知。

如果您的建置系統不支援 AAR 檔案，則可以使用下列檔案取代 Microsoft.Intune.MAM.SDK.aar。
* **Microsoft.Intune.MAM.SDK.jar**：啟用 MAM 並與 Intune 公司入口網站應用程式互通所需的介面。 應用程式必須將其指定為 Android 程式庫參考。
* **資源目錄**：SDK 所依賴的資源 (例如字串)。
* **AndroidManifest.xml**：進入點和程式庫需求。


## <a name="requirements"></a>需求

Intune App SDK 是一種編譯過的 Android 專案。 因此，它基本上不會受到應用程式針對其最低或目標 API 版本使用的 Android 版本所影響。 此 SDK 支援 Android API 14 (Android 4.0+) 到 Android API 25 (Android 7.1)。



### <a name="company-portal-app"></a>公司入口網站應用程式
Intune App SDK for Android 必須仰賴裝置上的[公司入口網站](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal)應用程式來啟用應用程式保護原則。 公司入口網站會從 Intune 服務擷取應用程式保護原則。 應用程式初始化時，它會載入原則和程式碼，以從公司入口網站強制執行該原則。

> [!NOTE]
> 當裝置上沒有公司入口網站應用程式時，可搭配 Intune 的應用程式會具有和不支援 Intune 應用程式保護原則的一般應用程式相同的行為。

對於沒有裝置註冊的應用程式保護，使用者「不」__需要使用公司入口網站應用程式註冊裝置。

## <a name="sdk-integration"></a>SDK 整合

### <a name="build-integration"></a>組建整合

Intune App SDK 是不含外部相依性的標準 Android 程式庫。 **Microsoft.Intune.MAM.SDK.jar** 包含啟用應用程式保護原則所需的介面，以及和 Microsoft Intune 公司入口網站應用程式互通所需的程式碼。

**Microsoft.Intune.MAM.SDK.jar** 必須指定為 Android 程式庫參考。 若要這麼做，請在 Android Studio 中開啟應用程式專案，然後移至 [檔案] > [新增] > [新模組]，然後選取 [匯入 .JAR/.AAR 套件]。 請選取我們的 Android 封存套件，Microsoft.Intune.MAM.SDK.aar。

此外，**Microsoft.Intune.MAM.SDK.Support.v4** 和 **Microsoft.Intune.MAM.SDK.Support.v7** 皆個別包含 `android.support.v4` 和 `android.support.v7` 的 Intune 版本。 它們並沒有內建於 Microsoft.Intune.MAM.SDK.aar 之內，以防應用程式並不想要包含支援程式庫。 它們是標準 JAR 檔案，而非 Android 程式庫專案。

#### <a name="proguard"></a>ProGuard

若使用 [ProGuard (英文)](http://proguard.sourceforge.net/) (或任何其他壓縮/混淆機制) 做為建置步驟，便必須排除 Intune SDK 類別。 針對 ProGuard，這可以透過包含隨附於 SDK 之 proguard.txt 中的規則來達成。

Azure Active Directory Authentication Library (ADAL) 可能會有屬於自己的 ProGuard 限制。 如果應用程式整合了 ADAL，則您必須遵循這些限制的相關 ADAL 文件。

### <a name="entry-points"></a>進入點
=======
Azure Active Directory Authentication Library ([ADAL](https://azure.microsoft.com/documentation/articles/active-directory-authentication-libraries/)) 需要這些權限以執行代理驗證。 如果未將這些權限授與應用程式或使用者已撤銷這些權限，則會停用需要訊息代理程式 (公司入口網站應用程式) 的驗證流程。

Intune App SDK 需要變更應用程式的原始程式碼，以啟用 Intune 應用程式保護原則。 這是透過將 Android 基底類別取代為對等的 Intune 基底類別來完成，其名稱前面會加上 **MAM**。 SDK 類別的位置介於 Android 基底類別和應用程式本身針對該類別的衍生版本之間。 以活動為範例來看，最後您得到的繼承階層會像這樣：`Activity` > `MAMActivity` > `AppSpecificActivity`。

例如，當 `AppSpecificActivity` 與父系互動 (例如，呼叫 `super.onCreate()`) 時，`MAMActivity` 是超級類別。

一般而言，Android 應用程式擁有單一模式，並可透過其 [**Context (英文)**](https://developer.android.com/reference/android/content/Context.html) 物件存取系統。 另一方面，已經和 Intune App SDK 整合的應用程式則具有雙重模式。 這些應用程式可以繼續透過 `Context` 物件存取系統。 根據所使用的基底 `Activity`，`Context` 物件將由 Android 提供，或在系統的限制檢視和 Android 提供的 `Context` 之間，以智慧的方式進行多工處理。


## <a name="replace-classes-methods-and-activities-with-their-mam-equivalent"></a>將類別、方法和活動取代為其 MAM 對等項目

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
| android.app.PendingIntent | MAMPendingIntent (請參閱下列附註) |
| android.app.Service | MAMService |
| android.app.TabActivity | MAMTabActivity |
| android.app.TaskStackBuilder | MAMTaskStackBuilder |
| android.app.backup.BackupAgent | MAMBackupAgent |
| android.app.backup.BackupAgentHelper | MAMBackupAgentHelper |
| android.app.backup.FileBackupHelper | MAMFileBackupHelper |
| android.app.backup.SharePreferencesBackupHelper | MAMSharedPreferencesBackupHelper |
| android.content.BroadcastReceiver | MAMBroadcastReceiver |
| android.content.ContentProvider | MAMContentProvider |
| android.os.Binder | MAMBinder (只有在 Binder 不是從 Android Interface Definition Language (AIDL) 介面產生時才需要) |
| android.provider.DocumentsProvider | MAMDocumentsProvider |
| android.preference.PreferenceActivity | MAMPreferenceActivity |


### <a name="microsoftintunemamsdksupportv4jar"></a>Microsoft.Intune.MAM.SDK.Support.v4.jar：

| Android 類別 Intune MAM | Intune App SDK 取代 |
|--|--|
| android.support.v4.app.DialogFragment | MAMDialogFragment
| android.support.v4.app.FragmentActivity | MAMFragmentActivity
| android.support.v4.app.Fragment | MAMFragment
| android.support.v4.app.TaskStackBuilder | MAMTaskStackBuilder
| android.support.v4.content.FileProvider | MAMFileProvider

### <a name="microsoftintunemamsdksupportv7jar"></a>Microsoft.Intune.MAM.SDK.Support.v7.jar：

|Android 類別 | Intune App SDK 取代 |
|--|--|
|android.support.v7.app.ActionBarActivity | MAMActionBarActivity |


### <a name="renamed-methods"></a>重新命名的方法
在您從其中一個 MAM 進入點進行衍生之後，就可以用正常方式安全地使用 `Context`，例如用來啟動 `Activity` 類別和使用 `PackageManager`。

在許多情況下，Android 類別中可用的方法已在 MAM 取代類別中被標示為完稿。 在此情況下，MAM 取代類別會提供您應該覆寫的類似具名方法 (通常後置字元為 `MAM`)。 例如，當衍生自 `MAMActivity`，而不是覆寫 `onCreate()` 然後呼叫 `super.onCreate()` 時，`Activity` 必須覆寫 `onMAMCreate()` 並呼叫 `super.onMAMCreate()`。 Java 編譯器應該強制執行完稿的限制，以防止意外覆寫原始的方法，而不是 MAM 對等項目。

### <a name="pendingintent"></a>PendingIntent
您必須使用 `MAMPendingIntent.get*` 方法，而不是 `PendingIntent.get*`。 之後，您可以像往常一樣使用結果 `PendingIntent`。

### <a name="manifest-replacements"></a>資訊清單取代
請注意，您可能需要在資訊清單及 Java 程式碼中執行部分上述類別取代。 特殊注意事項：
* 針對 `android.support.v4.content.FileProvider` 的資訊清單參考，必須以 `com.microsoft.intune.mam.client.support.v4.content.MAMFileProvider` 取代。


## <a name="sdk-permissions"></a>SDK 權限

Intune App SDK 需要在與其整合的應用程式上，具有三個 [Android 系統權限](https://developer.android.com/guide/topics/security/permissions.html)：

* `android.permission.GET_ACCOUNTS` (如有需要，則會在執行階段要求)

* `android.permission.MANAGE_ACCOUNTS`

* `android.permission.USE_CREDENTIALS`

Azure Active Directory 驗證程式庫 ([ADAL](https://azure.microsoft.com/en-us/documentation/articles/active-directory-authentication-libraries/)) 需要這些權限才能執行代理驗證。 如果未將這些權限授與應用程式或使用者已撤銷這些權限，則會停用需要訊息代理程式 (公司入口網站應用程式) 的驗證流程。

## <a name="logging"></a>記錄

記錄應該要盡早初始化，以取得最豐富的記錄資料。 `Application.onMAMCreate()` 通常是初始化記錄的最佳位置。

若要在應用程式中接收 MAM 記錄，請建立 [Java 處理常式 (英文)](http://docs.oracle.com/javase/7/docs/api/java/util/logging/Handler.html) 並將它新增至 `MAMLogHandlerWrapper`。 這將會針對每個記錄訊息在應用程式處理常式上叫用 `publish()`。

```java
/**
 * Global log handler that enables fine grained PII filtering within MAM logs.  
 *
 * To start using this you should build your own log handler and add it via
 * MAMComponents.get(MAMLogHandlerWrapper.class).addHandler(myHandler, false);  
 *
 * You may also remove the handler entirely via
 * MAMComponents.get(MAMLogHandlerWrapper.class).removeHandler(myHandler);
 */
public interface MAMLogHandlerWrapper {
    /**
     * Add a handler, PII can be toggled.
     *
     * @param handler handler to add.
     * @param wantsPII if PII is desired in the logs.    
     */
    void addHandler(final Handler handler, final boolean wantsPII);

    /**
     * Remove a handler.
     *
     * @param handler handler to remove.
     */
    void removeHandler(final Handler handler);
}
```



## <a name="enable-features-that-require-app-participation"></a>啟用需要應用程式參與的功能

有數個 SDK 無法自行實作的應用程式保護原則。 此應用程式可控制其行為，以使用可在以下 `AppPolicy` 介面中找到的數個 API，實現這些功能。

```java
/**
 * External facing application policies.
 */
public interface AppPolicy {

/**
 * Restrict where an app can save personal data.
 * This function is now deprecated. Please use getIsSaveToLocationAllowed(SaveLocation, String) instead
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
 *           the username/email associated with the cloud service being saved to. Use null if a mapping between
 *           the AAD username and the cloud service username does not exist or the username is not known.
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

> [!NOTE]
> `MAMComponents.get(AppPolicy.class)` 一律會傳回非 null 的應用程式原則，即使裝置或應用程式不受 Intune 管理原則限制，亦是如此。

### <a name="example-determine-if-pin-is-required-for-the-app"></a>範例：判斷應用程式是否需要 PIN

在 IT 系統管理員已設定 SDK 以提示輸入應用程式 PIN 的情況下，如果應用程式有屬於自己的 PIN 使用者體驗，您可能會想要停用它。 若要判斷 IT 系統管理員是否已將應用程式 PIN 原則部署至此應用程式，請針對目前的使用者呼叫下列方法：

```java
MAMComponents.get(AppPolicy.class).getIsPinRequired();
```

### <a name="example-determine-the-primary-intune-user"></a>範例：判斷主要 Intune 使用者

除了在 AppPolicy 中公開的 API 之外，使用者主體名稱 (**UPN**) 也會由在`MAMUserInfo` 中定義的 `getPrimaryUser()` API 公開。 若要取得 UPN，請呼叫下列項目：

```java
MAMUserInfo info = MAMComponents.get(MAMUserInfo.class);
if (info != null) return info.getPrimaryUser();
```

MAMUserInfo 介面的完整定義如下：

```java
/**
 * External facing user informations.
 *
 */
public interface MAMUserInfo {
       /**
        * Get the primary user name.
        *
        * @return the primary user name or null if the device is not enrolled.
        */
       String getPrimaryUser();
}
```

### <a name="example-determine-if-saving-to-device-or-cloud-storage-is-permitted"></a>範例：判斷是否允許儲存至裝置或雲端儲存體

許多應用程式實作功能，可讓使用者將檔案儲存於本機或儲存至雲端儲存體服務。 Intune App SDK 可讓 IT 系統管理員套用組織適用的原則限制，以防資料外洩。  IT 人員可以控制的其中一項原則是，使用者是否可以儲存至未受管理的「個人」資料存放區。 這包括儲存至本機位置、SD 記憶卡或協力廠商備份服務。

**啟用此功能需要應用程式參與。** 如果您的應用程式可直接從應用程式儲存至個人或雲端位置，您就必須實作此功能，以確保 IT 系統管理員能控制是否允許儲存至某個位置。 下列 API 可讓應用程式知道目前的 Intune 系統管理員原則是否允許儲存到個人存放區。 接著，應用程式即可強制執行原則，因為它會感知使用者透過應用程式可使用的個人資料存放區。  

若要判斷是否已強制執行該原則，請進行下列呼叫：

```java
MAMComponents.get(AppPolicy.class).getIsSaveToLocationAllowed(
SaveLocation service, String username);
```

其中 `service` 為下列其中一個 SaveLocations：


    * SaveLocation.ONEDRIVE_FOR_BUSINESS
    * SaveLocation.SHAREPOINT
    * SaveLocation.BOX
    * SaveLocation.DROPBOX
    * SaveLocation.GOOGLE_DRIVE
    * SaveLocation.LOCAL
    * SaveLocation.OTHER

在此之前，能用來判斷使用者的原則是否允許他們將資料儲存至各種位置的方法，為位於相同 **AppPolicy** 類別中的 `getIsSaveToPersonalAllowed()`。 此函數目前已「被取代」，且不應該使用。下列的引動過程等同於 `getIsSaveToPersonalAllowed()`：

```java

MAMComponents.get(AppPolicy.class).getIsSaveToLocationAllowed(SaveLocation.LOCAL, userNameInQuestion);
```

>[!NOTE]
> 若目標位置沒有列於 **SaveLocations** 列舉中，請使用 `SaveLocation.OTHER`。


## <a name="register-for-notifications-from-the-sdk"></a>從 SDK 註冊通知

### <a name="overview"></a>概觀
當 IT 系統管理員部署特定原則時 (例如選擇性抹除)，Intune App SDK 可讓您的應用程式控制其行為。 當 IT 系統管理員部署這類原則時，Intune 服務會傳送通知給 SDK。

您的應用程式必須建立 `MAMNotificationReceiver`，並向 `MAMNotificationReceiverRegistry` 註冊它，才能從 SDK 註冊通知。 這是藉由提供接收者以及想要在 `App.onCreate` 中接收的通知類型來完成，如下列範例所示：

```java
@Override
public void onCreate() {
    super.onCreate();
    MAMComponents.get(MAMNotificationReceiverRegistry.class)
        .registerReceiver(
            new ToastNotificationReceiver(),
            MAMNotificationType.WIPE_USER_DATA);
    }
```

### <a name="mamnotificationreceiver"></a>MAMNotificationReceiver

`MAMNotificationReceiver` 介面只會從 Intune 服務接收通知。 有些通知是由 SDK 直接處理，有些則需要應用程式的參與。 應用程式**必須**針對通知傳回 true 或 false。 除非基於通知結果，應用程式嘗試採取的某些動作失敗，否則一律會傳回 true。

* 這類失敗可能會回報給 Intune 服務。 例如，如果在 IT 系統管理員起始抹除之後，應用程式無法抹除使用者資料，就會進行回報。

>[!NOTE]
> 您可以放心封鎖 `MAMNotificationReceiver.onReceive`，因為其回呼不會在 UI 執行緒上執行。

於 SDK 中定義的 `MAMNotificationReceiver` 介面已包含於下列內容中：

```java
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

```

### <a name="types-of-notifications"></a>通知類型

下列通知會傳送至應用程式，且其中部分通知可能需要應用程式參與：

* **WIPE_USER_DATA**︰這個通知是在 `MAMUserNotification` 類別中傳送。 收到這項通知時，應用程式應該刪除與 `MAMUserNotification` 一起傳遞之「公司」身分識別相關聯的所有資料。 這項通知目前會在 APP-WE 服務取消註冊期間傳送。 使用者主要名稱通常會在註冊程序期間指定。 如果您註冊這項通知，您的應用程式必須確定所有使用者資料都已刪除。 如果您未註冊，就會執行預設的選擇性抹除行為。

* **WIPE_USER_AUXILIARY_DATA**：如果應用程式要 Intune App SDK 執行預設選擇性抹除行為，但仍想要在抹除發生時移除部分輔助資料，則可註冊這項通知。

* **REFRESH_POLICY**︰這項通知是在 `MAMUserNotification` 中傳送。 收到這項通知時，所有快取的 Intune 原則都必須處於失效狀態並加以更新。 通常，SDK 會處理這項作業，不過如果原則是以任何持續性的方式使用，則應該由應用程式來處理。

* **MANAGEMENT_REMOVED**：這項通知是在 `MAMUserNotification` 中傳送，並會通知應用程式它即將成為未受管理。 應用程式成為未受管理之後，它將無法讀取加密的檔案、讀取以 MAMDataProtectionManager 加密的檔案、與加密的剪貼簿互動，或參與受管理應用程式的生態系統。


> [!NOTE]
> 應用程式永遠不得同時註冊 `WIPE_USER_DATA` 和 `WIPE_USER_AUXILIARY_DATA` 通知。


## <a name="configure-azure-active-directory-authentication-library-adal"></a>設定 Azure Active Directory Authentication Library (ADAL)

首先，請參閱 [GitHub 上 ADAL 存放庫 (英文)](https://github.com/AzureAD/azure-activedirectory-library-for-android) 中的 ADAL 整合方針。

SDK 仰賴 [ADAL](https://azure.microsoft.com/en-us/documentation/articles/active-directory-authentication-libraries/) 進行[驗證](https://azure.microsoft.com/en-us/documentation/articles/active-directory-authentication-scenarios/)和條件式啟動案例，其中需要應用程式針對 [Azure Active Directory](https://azure.microsoft.com/en-us/documentation/articles/active-directory-whatis/)進行設定。 設定值會透過 AndroidManifest 中繼資料傳送給 SDK。

若要設定您的應用程式並啟用適當的驗證，請將下列項目加入 AndroidManifest.xml 中的應用程式節點。 一般來說，其中某些設定僅在您的應用程式會使用 ADAL 來進行驗證時才需要；在此情況下，您必須具備應用程式使用的特定值，以向 AAD 註冊該應用程式。 這是為了確保使用者不會因為 AAD 辨識兩個不同的登錄值 (一個來自應用程式，另一個則來自 SDK)，而收到兩次驗證提示。

```xml
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
```

### <a name="adal-metadata"></a>ADAL 中繼資料

* **Authority** 為目前使用的 AAD 授權單位。 若存在，您應該使用自己的環境 (其中已設定 AAD 帳戶)。 如果此值不存在，則會使用 Intune 預設值。

* **ClientID** 為要使用的 AAD ClientID。 如果應用程式的 ClientID 已經向 Azure AD 註冊，您應該使用此 ClientID。 如果此值不存在，則會使用 Intune 預設值。

* **NonBrokerRedirectURI** 為要在無 Broker 的情況下使用的 AAD 重新導向 URI。 如果未指定，就會使用預設值 `urn:ietf:wg:oauth:2.0:oob`。 此預設值適用於大部分的應用程式。

* **SkipBroker** 會在 ClientID 未設定為使用 Broker 重新導向 URI 的情況下使用。 預設值為 "false"。
    * 針對「不會整合 ADAL」及「不想要參與全裝置代理驗證/SSO」的應用程式，此值應設為 "true"。 當此值為 "true" 時，唯一會使用的重新導向 URI 為 NonBrokerRedirectURI。

    * 針對支援全裝置 SSO 代理的應用程式，此值應為 "false"。 當此值為 "false" 時，SDK 將會根據 Broker 在系統上的可用性，於 [`com.microsoft.aad.adal.AuthenticationContext.getRedirectUriForBroker()`](https://github.com/AzureAD/azure-activedirectory-library-for-android) 和 NonBrokerRedirectURI 的結果之間選取 Broker。 一般而言，Broker 將會從公司入口網站應用程式，或 Azure Authenticator 應用程式提供。

### <a name="common-adal-configurations"></a>ADAL 的常見設定

下列為應用程式可以搭配 ADAL 進行設定的常見方式。 尋找您應用程式的設定，並確保 ADAL 中繼資料參數 (如上所述) 已設定為必要的值。

1. **應用程式不會整合 ADAL：**

    | 必要的 ADAL 參數 | 值 |
    |--|--|
    | Authority | 已設定 AAD 帳戶的所需環境 |
    | SkipBroker | True |

2. **應用程式會整合 ADAL：**

    |必要的 ADAL 參數| 值 |
    |--|--|
    | Authority | 已設定 AAD 帳戶的所需環境 |
    | ClientID | 應用程式的 ClientID (由 Azure AD 於應用程式註冊時產生) |
    | NonBrokerRedirectURI | 應用程式的有效重新導向 URI，或是預設值 `urn:ietf:wg:oauth:2.0:oob`。 <br><br> 請務必將值設定為您應用程式 ClientID 可接受的重新導向 URI。
    | SkipBroker | False |


3. **應用程式會整合 ADAL，但不支援代理驗證/全裝置 SSO：**

    |必要的 ADAL 參數| 值 |
    |--|--|
    | Authority | 已設定 AAD 帳戶的所需環境 |
    | ClientID | 應用程式的 ClientID (由 Azure AD 於應用程式註冊時產生) |
    | NonBrokerRedirectURI | 應用程式的有效重新導向 URI，或是預設值 `urn:ietf:wg:oauth:2.0:oob`。 <br><br> 請務必將值設定為您應用程式 ClientID 可接受的重新導向 URI。
    | SkipBroker | **True** |

## <a name="app-protection-policy-without-device-enrollment"></a>無裝置註冊的應用程式保護原則

### <a name="overview"></a>概觀
無裝置註冊的 Intune 應用程式保護原則 (也稱為 APP-WE 或 MAM-WE) 可讓 Intune 管理應用程式，而不需要向 Intune MDM 註冊裝置。 APP-WE 無論是否搭配裝置註冊皆可以運作。 公司入口網站仍然需要安裝於裝置上，但使用者並不需要登入公司入口網站並註冊該裝置。

> [!NOTE]
> 所有應用程式都必須支援無裝置註冊的應用程式保護原則。

### <a name="workflow"></a>工作流程

當應用程式建立新使用者帳戶時，它應該註冊該帳戶以使用 Intune App SDK 進行管理。 SDK 會處理在 APP-WE 服務中註冊應用程式的細節。若有需要，它會在發生失敗的情況下，以適當的時間間隔重試任何註冊。

應用程式也可以向 Intune App SDK 查詢已註冊的使用者，以判斷是否應封鎖該使用者存取公司內容。 您可以註冊多個帳戶以進行管理，但目前一次只能針對 APP-WE 服務註冊一個帳戶。 這代表應用程式上一次只有一個帳戶可以接收應用程式保護原則。

該應用程式必須提供回呼，以代表 SDK 從 Azure Active Directory Authentication Library (ADAL) 取得適當的存取權杖。 它會假設該應用程式已經使用 ADAL 以進行使用者驗證，以及用來取得自己的存取權杖。

當應用程式完全移除某個帳戶時，它應該會取消該帳戶的註冊，以指出應用程式已不再針對該使用者套用原則。 如果該使用者曾註冊 MAM 服務，系統會將他取消註冊並抹除應用程式。


### <a name="overview-of-app-requirements"></a>應用程式需求概觀

若要實作 APP-WE 整合，您的應用程式必須向 MAM SDK 註冊使用者帳戶：

1. 應用程式「必須」實作並註冊 `MAMServiceAuthenticationCallback` 介面的執行個體。 回呼執行個體必須盡早於應用程式的生命週期內進行註冊 (通常是在應用程式類別的 `onMAMCreate()` 方法中)。

2. 在建立使用者帳戶，且使用者成功以 ADAL 登入之後，應用程式「必須」呼叫 `registerAccountForMAM()`。

3. 當使用者帳戶已完全移除之後，應用程式應該呼叫 `unregisterAccountForMAM()` 以將帳戶從 Intune 管理中移除。

    > [!NOTE]
    > 如果使用者暫時登出應用程式，應用程式並不需要呼叫 `unregisterAccountForMAM()`。 呼叫可以初始化抹除，以完全移除該使用者的公司資料。


### <a name="mamenrollmentmanager"></a>MAMEnrollmentManager

所有必要的驗證和註冊 API 都可以在 `MAMEnrollmentManager` 介面中找到。 針對 `MAMEnrollmentManager` 的參考可以透過下列方式取得：

```java
MAMEnrollmentManager mgr = MAMComponents.get(MAMEnrollmentManager.class);

// make use of mgr

```

傳回的 `MAMEnrollmentManager` 執行個體將保證不會為 null。 API 方法會落入兩個類別：「驗證」和「帳戶註冊」。

> [!NOTE]
> `MAMEnrollmentManager` 包含一些即將被取代的 API 方法。 為了清楚呈現，下列程式碼區塊只會顯示相關的方法和結果程式碼。

```java
package com.microsoft.intune.mam.policy;

public interface MAMEnrollmentManager {
    public enum Result {
        AUTHORIZATION_NEEDED,
        NOT_LICENSED,
        ENROLLMENT_SUCCEEDED,
        ENROLLMENT_FAILED,
        WRONG_USER,
        MDM_ENROLLED,
        UNENROLLMENT_SUCCEEDED,
        UNENROLLMENT_FAILED,
        PENDING,
        COMPANY_PORTAL_REQUIRED;
    }

    //Authentication methods
    interface MAMServiceAuthenticationCallback {
        String acquireToken(String upn, String aadId, String resourceId);
    }
    void registerAuthenticationCallback(MAMServiceAuthenticationCallback callback);
    void updateToken(String upn, String aadId, String resourceId, String token);

    //Registration methods
    void registerAccountForMAM(String upn, String aadId, String tenantId);
    void unregisterAccountForMAM(String upn);
    Result getRegisteredAccountStatus(String upn);
}
```

### <a name="account-authentication"></a>帳戶驗證

本節會描述 `MAMEnrollmentManager` 中的驗證 API 方法，以及使用它們的方式。

```java
interface MAMServiceAuthenticationCallback {
        String acquireToken(String upn, String aadId, String resourceId);
}
void registerAuthenticationCallback(MAMServiceAuthenticationCallback callback);
void updateToken(String upn, String aadId, String resourceId, String token);
```

1. 應用程式必須實作 `MAMServiceAuthenticationCallback` 介面，以允許 SDK 針對指定使用者和資源識別碼要求 ADAL 權杖。 回呼執行個體必須提供給 `MAMEnrollmentManager`，方法是呼叫其 `registerAuthenticationCallback()` 方法。 在應用程式生命週期相當早的階段，可能會需要權杖以進行註冊重試或應用程式保護原則重新整理簽入，因此註冊回呼的理想位置是在應用程式 `MAMApplication` 子類別的 `onMAMCreate()` 方法中。

2. `acquireToken()` 方法應該會取得針對指定使用者所要求之資源識別碼的存取權杖。 如果它無法取得要求的權杖，便應該會傳回 null。

3. 在應用程式無法於 SDK 呼叫 `acquireToken()` 時提供權杖的情況下 (例如，如果無訊息驗證失敗，且當時並不方便顯示 UI)，該應用程式可以透過呼叫 `updateToken()` 方法來在稍後提供權杖。 由先前針對 `acquireToken()` 的呼叫所要求的 UPN、AAD 識別碼及資源識別碼，必須連同最終取得的權杖一起傳遞至 `updateToken()`。 應用程式應該在從所提供的回呼傳回 null 之後盡快呼叫此方法。

> [!NOTE]
> SDK 將會定期呼叫 `acquireToken()` 以取得權杖，因此並不一定需要呼叫 `updateToken()`。 不過，我們建議您這麼做，因為這可以協助註冊和應用程式保護原則簽入及時完成。


### <a name="account-registration"></a>帳戶註冊

本節會描述 `MAMEnrollmentManager` 中的帳戶註冊 API 方法，以及使用它們的方式。

```java
void registerAccountForMAM(String upn, String aadId, String tenantId);
void unregisterAccountForMAM(String upn);
Result getRegisteredAccountStatus(String upn);
```

1. 若要註冊帳戶以進行管理，應用程式應呼叫 `registerAccountForMAM()`。 識別使用者帳戶的方式，是透過其 UPN 和 AAD 使用者識別碼。 同時也需要租用戶識別碼，以關聯註冊資料與使用者的 AAD 租用戶。 SDK 可能會嘗試在 MAM 服務中針對指定使用者註冊應用程式。若註冊失敗，它將會定期重試註冊，直到該帳戶已取消註冊為止。 重試的間隔通常是 12-24 小時。 SDK 會透過通知以非同步的方式提供註冊嘗試的狀態。

2. 由於需要 AAD 驗證，註冊使用者帳戶的最佳時間是在使用者登入應用程式，並成功使用 ADAL 進行驗證之後。
    * 做為 [`AuthenticationResult`](https://github.com/AzureAD/azure-activedirectory-library-for-android) 物件的一部分，使用者的 AAD 識別碼和租用戶識別碼會從 ADAL 驗證呼叫傳回。 租用戶識別碼是來自 `AuthenticationResult.getTenantID()` 方法。
    * 有關使用者的資訊是位於來自 `AuthenticationResult.getUserInfo()` 之 `UserInfo` 類型的子物件中，而 AAD 使用者識別碼則是透過呼叫 `UserInfo.getUserId()` 以從該物件中擷取。

3. 若要從 Intune 管理取消註冊某個帳戶，應用程式應呼叫 `unregisterAccountForMAM()`。 若該帳戶已成功註冊並受到管理，SDK 將會取消註冊該帳戶並抹除其資料。 該帳戶的定期註冊重試將會停止。 SDK 會透過通知以非同步的方式提供取消註冊要求的狀態。

### <a name="important-implementation-notes"></a>重要實作附註

#### <a name="authentication"></a>驗證

* 當應用程式呼叫 `registerAccountForMAM()` 時，它可能會在不久之後於其 `MAMServiceAuthenticationCallback` 介面上接收到不同執行緒的回呼。 在理想的情況下，應用程式已在註冊帳戶之前從 ADAL 取得自己的權杖，以加快取得 **MAMService** 權杖的速度。 如果應用程式從回呼傳回有效權杖，則註冊將會繼續，且應用程式將會透過通知取得最終結果。

* 如果應用程式沒有傳回有效的 AAD 權杖，來自註冊嘗試的最終結果將會是 `AUTHENTICATION_NEEDED`。 如果應用程式透過通知接收到此結果，它可以透過取得 **MAMService** 權杖，並呼叫 `updateToken()` 方法以再次初始化註冊程序，來加快註冊程序的速度。 這並「不是」強制的需求，不過由於 SDK 會定期重試註冊並叫用回呼以取得權杖，

* 因此也會呼叫應用程式的已註冊 `MAMServiceAuthenticationCallback`，以取得定期應用程式保護原則重新整理簽入的權杖。 如果應用程式無法在要求時提供權杖，便不會收到通知，不過它應該於下一個適當的時機嘗試取得權杖並呼叫 `updateToken()`，以加速簽入程序。 如果不提供權杖，在下一個簽入嘗試時仍然會呼叫回呼。

#### <a name="registration"></a>註冊

* 為了方便起見，註冊方法將會是等冪，例如 `registerAccountForMAM()` 只會在帳戶尚未註冊的情況下註冊該帳戶並嘗試註冊應用程式，而 `unregisterAccountForMAM()` 只會在帳戶已註冊的情況下將帳戶取消註冊。 後續的呼叫將不會運作，因此多次呼叫這些方法並不會有壞處。 此外，針對這些方法的呼叫及結果通知之間的對應並不是保證的，也就是說，若針對已註冊的身分識別呼叫 `registerAccountForMAM`，便可能不會針對該身分識別再次傳送通知。 已傳送的通知有可能不會與針對這些方法的任何呼叫對應，因為 SDK 可能會定期嘗試在背景進行註冊，且從 Intune 服務接收的抹除要求可能會觸發取消註冊。

* 註冊方法可以針對任何數目的個別身分識別進行呼叫，但目前只能有一個使用者帳戶可以成功註冊。 若有多個已針對 Intune 取得授權，並為應用程式保護原則之目標的使用者帳戶，在相同或相近的時間進行註冊，將無法保證哪一個帳戶會註冊成功。

* 最後，您可以查詢 `MAMEnrollmentManager` 以使用 `getRegisteredAccountStatus` 方法來查看特定帳戶是否已註冊，以及取得其目前的狀態。 若所提供的帳戶尚未註冊，此方法將會傳回 **null**。 若帳戶已註冊，此方法將會以 `MAMEnrollmentManager.Result` 列舉之其中一個成員的方式傳回該帳戶的狀態。

### <a name="result-and-status-codes"></a>結果和狀態碼

當帳戶註冊時，它一開始會處於 `PENDING` 狀態，表示初始 MAM 服務註冊嘗試尚未完成。 在註冊嘗試完成之後，將會傳送具有下表其中一個結果碼的通知。 此外，`getRegisteredAccountStatus()` 方法將會傳回帳戶的狀態，使應用程式可以持續判斷該使用者對公司內容的存取是否已被封鎖。 若註冊嘗試失敗，帳戶的狀態可能會隨著 SDK 於背景重試註冊而變更。

|結果碼 | 說明 |
| -- | -- |
|AUTHORIZATION_NEEDED | 此結果表示應用程式的已註冊 `MAMServiceAuthenticationCallback` 執行個體沒有提供權杖，或是提供的權杖無效。  若可能的話，應用程式應該取得有效的權杖並呼叫 `updateToken()`。 |
| NOT_LICENSED | 使用者沒有針對 Intune 取得授權，或是連絡 Intune MAM 服務的嘗試失敗。  應用程式應該會持續以未受管理 (一般) 的狀態進行，且使用者應該不會被封鎖。  註冊將會定期進行重試，以防使用者於日後取得授權。 |
| ENROLLMENT_SUCCEEDED | 註冊嘗試成功，或是使用者已經註冊。  針對成功註冊的情況，將會在此通知之前傳送原則重新整理的通知。  應用程式應該會允許針對公司資料的存取。 |
| ENROLLMENT_FAILED | 註冊嘗試失敗。  您可以在裝置記錄檔中找到進一步的詳細資料。  在此狀態下，應用程式應該不會允許對公司資料的存取，因為先前已判斷使用者已針對 Intune 取得授權。|
| WRONG_USER | 每個裝置上只能有一個使用者可以將應用程式與 MAM 服務進行註冊。  若要以不同使用者的身分成功進行註冊，所有已註冊的應用程式都必須先取消註冊。  否則，此應用程式必須以主要使用者的身分進行註冊。  此檢查會在授權檢查之後發生，因此在該應用程式成功註冊之前，使用者將無法存取公司資料。|
| UNENROLLMENT_SUCCEEDED | 已順利完成取消註冊。|
| UNENROLLMENT_FAILED | 取消註冊要求失敗。  您可以在裝置記錄檔中找到進一步的詳細資料。 |
| PENDING | 使用者的初始註冊嘗試正在進行中。  應用程式可以 (但非必要) 封鎖對公司資料的存取，直到知道註冊狀態為止。 |
| COMPANY_PORTAL_REQUIRED | 使用者已針對 Intune 取得授權，但在裝置上安裝公司入口網站應用程式之前，將無法註冊應用程式。 Intune App SDK 會嘗試封鎖特定使用者對應用程式的存取，並引導他們安裝公司入口網站應用程式 (請參閱下方以取得詳細資料)。 |


### <a name="company-portal-requirement-prompt-override-optional"></a>公司入口網站需求提示覆寫 (選擇性)

如果接收到 `COMPANY_PORTAL_REQUIRED` 結果，SDK 將會封鎖使用要求註冊之身分識別的活動。 相反地，SDK 將會使那些活動顯示下載公司入口網站的提示。 如果您想要在應用程式中避免此行為，可以讓活動實作 `MAMActivity.onMAMCompanyPortalRequired`。

此方法會在 SDK 顯示其預設封鎖 UI 之前呼叫。 如果應用程式變更活動身分識別，或是將嘗試註冊的使用者取消註冊，SDK 將不會封鎖該活動。 在此情況下，應用程式必須負責避免洩漏公司資料。

### <a name="notifications"></a>通知

已新增 `MAMNotification` 的新類型，以通知應用程式註冊要求已完成。  將會透過 `MAMNotificationReceiver` 介面接收 `MAMEnrollmentNotification`，如[從 SDK 註冊通知](#register-for-notifications-from-the-sdk)一節中所述。

```java
public interface MAMEnrollmentNotification extends MAMUserNotification {
    MAMEnrollmentManager.Result getEnrollmentResult();
}

```

`getEnrollmentResult()` 方法會傳回註冊要求的結果。  由於 `MAMEnrollmentNotification` 會延伸 `MAMUserNotification`，因此也會提供嘗試註冊的使用者身分識別。 應用程式必須實作 `MAMNotificationReceiver` 介面以接收這些通知，這已在[從 SDK 註冊通知](#Register-for-notifications-from-the-SDK)一節中詳述。

已註冊使用者帳戶的狀態在接收註冊通知時可能會變更，但在某些情況下將不會變更，例如，若在接收較具資訊性的結果 (例如 `WRONG_USER`) 之後接收到 `AUTHORIZATION_NEEDED` 通知，則系統將會維持使用較具資訊性的結果做為帳戶的狀態


## <a name="protecting-backup-data"></a>保護備份資料

截至 Android Marshmallow (API 23) 止，Android 提供兩種可讓應用程式備份資料的方法。 您可在應用程式中使用這些選項，但需要不同的步驟以確保正確實作 Intune 資料保護。 您可以檢閱下表，以了解正確資料保護行為所需的相對應動作。  您可以在 [Android API 指南](http://developer.android.com/guide/topics/data/backup.html)中深入了解備份方法。

### <a name="auto-backup-for-apps"></a>應用程式的自動備份

Android 開始針對 Android Marshmallow 裝置上的應用程式提供 Google 雲端硬碟的[自動完整備份 (英文)](https://developer.android.com/guide/topics/data/autobackup.html)，不論應用程式的目標 API 為何。 在您的 AndroidManifest.xml 中，如果您將 `android:allowBackup` 明確設定為 **false**，則 Android 永遠不會將您的應用程式排入佇列進行備份，而且「公司」資料會保留在應用程式內。 在這種情況下，並不需要採取任何進一步的動作。

不過，`android:allowBackup` 屬性預設會設定為 true，即使未在資訊清單檔中指定 `android:allowBackup` 亦然。 這表示所有應用程式資料都會自動備份至使用者的 Google 雲端硬碟帳戶，此預設行為會造成**資料洩漏的風險**。 因此，SDK 需進行下列所述的變更，以確保套用資料保護。  如果您想要讓應用程式在 Android Marshmallow 裝置上執行，請務必遵循下列方針，以妥善保護客戶資料。  

Intune 可讓您利用 Android 中可用的所有[自動備份功能](https://developer.android.com/guide/topics/data/autobackup.html)，包括在 XML 中定義自訂規則的功能，但您必須遵循下列步驟來保護資料：

1. 如果您的應用程式「不會」使用自己的自訂 BackupAgent，請使用預設 MAMBackupAgent 以允許進行符合 Intune 原則的自動完整備份。 如果您這麼做，則可以忽略 `android:fullBackupOnly` 資訊清單屬性，因為它並不適用於我們的備份代理程式。 請將下列內容置於應用程式資訊清單中：

    ```xml
android:backupAgent="com.microsoft.intune.mam.client.app.backup.MAMDefaultBackupAgent"
    ```

2. **[選擇性]** 如果您實作選擇性的自訂 BackupAgent，則必須使用 MAMBackupAgent 或 MAMBackupAgentHelper。 請參閱下列各節。 請考慮改用 Intune 的 **MAMDefaultFullBackupAgent** (已於步驟 1 中詳述)，它能針對 Android M 及更新版本提供簡易的備份功能。

3. 當您決定應用程式應該接收的完整備份類型 (未篩選、已篩選或無) 時，您必須將將屬性 `android:fullBackupContent` 設定為 true、false，或您應用程式中的 XML 資源。

4. 接著，您「必須」__將放入 `android:fullBackupContent` 的任何內容，複製到資訊清單中名為 `com.microsoft.intune.mam.FullBackupContent` 的 Metadata 標記中。

    **範例 1**：如果您想要讓應用程式具有完整備份並不排除任何內容，請將 `android:fullBackupContent` 屬性和 `com.microsoft.intune.mam.FullBackupContent` Metadata 標記設定為 **true**：

    ```xml
    android:fullBackupContent="true"
    ...
    <meta-data android:name="com.microsoft.intune.mam.FullBackupContent" android:value="true" />  
    ```

    **範例 2**：如果您想要讓應用程式使用自己的自訂 BackupAgent，並選擇退出完整且符合 Intune 原則的自動備份，則必須將屬性和 Metadata 標記設定為 **false**：

    ```xml
    android:fullBackupContent="false"
    ...
    <meta-data android:name="com.microsoft.intune.mam.FullBackupContent" android:value="false" />  
    ```

    **範例 3**︰如果您想要讓應用程式根據定義於 XML 檔案中的自訂規則進行完整備份，請將屬性和 Metadata 標記設定為相同的 XML 資源：

    ```xml
    android:fullBackupContent="@xml/my_scheme"
    ...
    <meta-data android:name="com.microsoft.intune.mam.FullBackupContent" android:resource="@xml/my_scheme" />  
    ```


### <a name="keyvalue-backup"></a>金鑰/值備份

[索引鍵/值備份 (英文)](https://developer.android.com/guide/topics/data/keyvaluebackup.html) 選項可供所有 API 8+ 使用，並會將應用程式資料上傳至 [Android Backup Service (英文)](https://developer.android.com/google/backup/index.html)。 您應用程式每個使用者的資料量會限制為 5MB。 如果您使用 [索引鍵/值備份]，則必須使用 **BackupAgentHelper** 或 **BackupAgent**。

### <a name="backupagenthelper"></a>BackupAgentHelper

從原生 Android 功能性和 Intune MAM 整合的角度來看，BackupAgentHelper 都比 BackupAgent 容易實作。 BackupAgentHelper 可讓開發人員分別向 **FileBackupHelper** 和 **SharedPreferencesBackupHelper** 註冊整個檔案和共用的喜好設定，並在建立 BackupAgentHelper 時將其加入。 請遵循下列步驟以搭配 Intune MAM 使用 BackupAgentHelper：

1. 若要利用 BackupAgentHelper 進行多重身分識別備份，請遵循[擴充 BackupAgentHelper (英文)](https://developer.android.com/guide/topics/data/keyvaluebackup.html#BackupAgentHelper) 的 Android 指南。

2. 使您的類別擴充 BackupAgentHelper、FileBackupHelper 及 SharedPreferencesBackupHelper 的 MAM 對等項目。

|Android 類別 | MAM 對等項目 |
|--|--|
|BackupAgentHelper |MAMBackupAgentHelper |
|FileBackupHelper | MAMFileBackupHelper
|SharedPreferencesBackupHelper| MAMSharedPreferencesBackupHelper|

遵循這些指導方針以成功進行多重身分識別備份及還原。

### <a name="backupagent"></a>BackupAgent

BackupAgent 可讓您更明確了解備份了哪些資料。 由於開發人員是主要負責實作的人，因此必須進行更多的步驟才能確保從 Intune 取得適當的資料保護效果。 由於大部分工作都落在開發人員 (也就是您) 身上，因此有略多的作業涉及 Intune 的整合。

**整合 MAM：**

1. 請仔細閱讀[索引鍵/值備份 (英文)](https://developer.android.com/guide/topics/data/keyvaluebackup.html) 的 Android 指南，特別是[擴充 BackupAgent (英文)](https://developer.android.com/guide/topics/data/keyvaluebackup.html#BackupAgent)，以確保您的 BackupAgent 實作能遵循 Android 指導方針。

2. 使您的類別擴充 `MAMBackupAgent`。

**多重身分識別備份：**

1. 在開始備份之前，請確定您計畫備份的檔案或資料緩衝區已確實「由 IT 系統管理員允許在多重身分識別的案例下進行備份」。 我們在 `MAMFileProtectionManager` 和 `MAMDataProtectionManager` 中提供 `isBackupAllowed` 函式以供您進行判斷。 如果檔案或資料緩衝區不能備份，您就不應該繼續將它包含在備份中。

2. 在備份期間，如果想要備份在步驟 1 中檢查過的檔案識別，就必須使用您打算從其中擷取資料的檔案來呼叫 `backupMAMFileIdentity(BackupDataOutput data, File … files)`。 這會自動建立新的備份實體，並將其寫入 `BackupDataOutput` 。 在還原時會自動使用這些實體。

**多重身分識別還原：**

《資料備份》指南在[擴充 BackupAgent (英文)](https://developer.android.com/guide/topics/data/keyvaluebackup.html#BackupAgent) 一節中詳述還原應用程式資料的一般演算法，並提供程式碼範例。 若要成功進行多重身分識別還原，您必須遵循此程式碼範例中所提供的一般結構，並特別注意下列事項：

1.    您必須利用 `while(data.readNextHeader())`* 迴圈以完整瀏覽備份實體。

2.    若 `data.getKey()`* 不符合您於 `onBackup` 中所撰寫的索引鍵，您必須呼叫 `data.skipEntityData()`*。 若沒有執行此步驟，您的還原可能會失敗。

3.    避免在 `while(data.readNextHeader())`* 建構中取用備份實體時進行傳回，因為這會遺失自動寫入的實體。

* 其中 `data` 是在還原時傳遞至您應用程式之 **BackupDataInput** 的區域變數名稱。

## <a name="multi-identity-optional"></a>多重身分識別 (選擇性)

### <a name="overview"></a>概觀
Intune App SDK 預設會將原則套用至應用程式整體。 多重身分識別為選擇性的 Intune 應用程式保護功能，可以啟用以允許將原則套用至每個身分識別。 這需要的應用程式參與明顯高於其他應用程式保護功能。

應用程式在想要變更使用中身分識別時「必須」通知 SDK，SDK 也會在需要進行身分識別變更時通知應用程式。 使用者註冊裝置或應用程式之後，SDK 會註冊這個身分識別，並將其視為主要的 Intune 受管理身分識別。 應用程式中的其他使用者則會被視為未受管理，並具有不受限制的原則設定。

> [!NOTE]
> 目前，每個裝置上僅支援一個 Intune 受管理身分識別。

請注意，身分識別只會定義為字串。 身分識別「不區分大小寫」，而且針對身分識別對 SDK 所做出的要求，可能不會傳回原本設定身分識別時所使用的相同大小寫。


### <a name="enabling-multi-identity"></a>啟用多重身分識別

根據預設，所有應用程式都會視為單一身分識別應用程式。 您可以藉由將下列中繼資料置於 AndroidManifest.xml 中，來宣告該應用程式可感知多重身分識別。

```xml
  <meta-data
      android:name="com.microsoft.intune.mam.MAMMultiIdentity"
      android:value="true" />
```

### <a name="setting-the-identity"></a>設定身分識別

開發人員可以將應用程式使用者的身分識別設定為下列層級 (以遞減的優先順序排列)：

  1. 執行緒層級
  2. 內容 (通常是活動) 層級
  3. 處理程序層級

設定為執行緒層級的身分識別會取代設定為內容層級的身分識別，而設定為內容層級的身分識別則會取代設定為處理程序層級的身分識別。 設定為內容層級的身分識別只會用於適當的相關聯案例，舉例來說，檔案 IO 作業並沒有相關聯的內容。 您可以使用 `MAMPolicyManager` 中的下列方法來設定身分識別，並擷取之前設定的身分識別值。

```java
  public static void setUIPolicyIdentity(final Context context, final String identity, final MAMSetUIIdentityCallback mamSetUIIdentityCallback);

  public static String getUIPolicyIdentity(final Context context);

  public static MAMIdentitySwitchResult setProcessIdentity(final String identity);

  public static String getProcessIdentity();

  public static MAMIdentitySwitchResult setCurrentThreadIdentity(final String identity);

  public static String getCurrentThreadIdentity();

  /**
   * Get the currently applicable app policy. Same as
   * MAMComponents.get(AppPolicy.class). This method does
   * not take the context identity into account.
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

>[!NOTE]
> 您可以透過將它設定為 null 來清除應用程式的身分識別。
>
> 空字串可以做為永遠都不會具有應用程式保護原則的身分識別使用。

#### <a name="results"></a>結果
用來設定身分識別的所有方法都會透過 `MAMIdentitySwitchResult` 回報結果值。 有四個可能傳回的值：

| 傳回值 | 案例 |
|--|--|
| SUCCEEDED | 身分識別變更成功。 |
| NOT_ALLOWED | 不允許身分識別變更。 <br><br>如果嘗試切換至和已註冊使用者屬於相同組織的不同受管理使用者，就會發生此情況。 在目前執行緒上已設定不同身分識別的情況下，嘗試設定 UI (內容) 身分識別，也會發生此情況。 |
| CANCELLED | 使用者已取消身分識別變更，通常是透過於 PIN 或驗證提示上按下 [返回] 按鈕。 |
| FAILED | 不明原因導致身分識別變更失敗。|


如果設定內容身分識別，則會以非同步方式報告結果。 如果內容是活動，在執行條件式啟動之前 (可能需要使用者輸入 PIN 或公司認證)，SDK 將無法得知身分識別變更是否成功。 應用程式必須實作 `MAMSetUIIdentityCallback` 以接收此結果，您可以針對此參數傳遞 null。

```java
    public interface MAMSetUIIdentityCallback {
        void notifyIdentityResult(MAMIdentitySwitchResult identitySwitchResult);
  }
```

您也可以直接透過 `MAMActivity` 中的方法來設定活動的身分識別，而不是呼叫 `MAMPolicyManager.setUIPolicyIdentity`。 請使用下列方法來達成：

```java
     public final void switchMAMIdentity(final String newIdentity);
```

您也可以覆寫 `MAMActivity` 中的方法，以使應用程式能收到嘗試變更該活動身分識別的結果通知。

``` java
    public void onSwitchMAMIdentityComplete(final MAMIdentitySwitchResult result);
```

>[!NOTE]
> 切換身分識別可能會需要重新建立活動。 在此情況下，`onSwitchMAMIdentityComplete` 回呼會傳遞至活動的新執行個體。


### <a name="implicit-identity-changes"></a>隱含身分識別變更

除了應用程式設定身分識別的能力之外，執行緒或內容的身分識別也可能會根據來自另一個具有應用程式保護原則的「可搭配 Intune 的應用程式」的資料輸入而變更。

#### <a name="examples"></a>範例

  1. 如果活動是根據另一個 MAM 應用程式所傳送的 `Intent` 來啟動，就會根據另一個應用程式在傳送 `Intent` 時的有效身分識別，來設定活動的身分識別。

  2.  針對服務，執行緒的身分識別會在 `onStart` 或 `onBind` 呼叫期間以類似的方式進行設定。 針對從 `onBind` 傳回之 `Binder` 的呼叫，也會暫時設定執行緒身分識別。

  3. 呼叫 `ContentProvider` 同樣會在該期間設定執行緒身分識別。


  此外，使用者與活動互動可能會導致隱含身分識別切換。

  **範例：**使用者在 `Resume` 期間取消授權提示，將會導致隱含切換至空的身分識別。

  應用程式會有機會注意到這些變更，並可以在必要的情況下禁止變更。 `MAMService` 和 `MAMContentProvider` 會公開下列可由子類別覆寫的方法：

  ```java
  public void onMAMIdentitySwitchRequired(final String identity,
      final AppIdentitySwitchResultCallback callback);
  ```

  在 `MAMActivity` 類別中，方法中會出現額外的參數：

  ```java
  public void onMAMIdentitySwitchRequired(final String identity,
      final AppIdentitySwitchReason reason,
      final AppIdentitySwitchResultCallback callback);
  ```

  * `AppIdentitySwitchReason` 會擷取隱含切換的來源，並可接受 `CREATE`、`RESUME_CANCELLED` 和 `NEW_INTENT` 值。  當活動繼續導致顯示 PIN、驗證或其他合規性 UI，而且使用者嘗試取消該 UI (通常是透過使用 [上一頁] 按鈕) 時，就會使用 `RESUME_CANCELLED` 原因。


  * `AppIdentitySwitchResultCallback` 如下所示：

      ```java
      public interface AppIdentitySwitchResultCallback {
          /**
           * @param result
           *            whether the identity switch can proceed.
           */
          void reportIdentitySwitchResult(AppIdentitySwitchResult result);
      }
      ```

      其中 ```AppIdentitySwitchResult``` 會是 SUCCESS 或 FAILURE。

針對所有隱含身分識別變更會呼叫 `onMAMIdentitySwitchRequired` 方法 (透過從 `MAMService.onMAMBind` 傳回的 Binder 進行的變更除外)。 `onMAMIdentitySwitchRequired` 的預設實作會立即呼叫：

*  `reportIdentitySwitchResult(FAILURE)` (當原因為 RESUME_CANCELLED 時)。

*  `reportIdentitySwitchResult(SUCCESS)` (針對所有其他情況)。

  大多數應用程式應該不會需要透過不同方式來封鎖或延遲身分識別切換，但如果應用程式需要這樣做，則必須考慮下列重點：

  * 如果身分識別切換遭到封鎖，則結果與 `Receive` 共用設定禁止資料輸入相同。

  * 如果服務正在主執行緒上執行，則「必須」同步呼叫 `reportIdentitySwitchResult`，否則 UI 執行緒將會停止回應。

  * 若要建立「活動」，會在 `onMAMCreate` 之前呼叫 `onMAMIdentitySwitchRequired`。 如果應用程式必須顯示 UI，以判斷是否允許身分識別切換，則必須使用「不同」的活動顯示該 UI。

  * 在「活動」中，如果因 RESUME_CANCELLED 的原因而要求切換至空的身分識別，則應用程式必須修改恢復的活動，以顯示與該身分識別切換一致的資料。  如果不可行，應用程式應該拒絕切換，並會再次要求使用者符合恢復之身分識別的原則 (例如，藉由顯示應用程式 PIN 輸入畫面)。

    > [!NOTE]
    > 多重身分識別應用程式永遠會從受管理和未受管理的應用程式接收內送資料。 應用程式會負責以受管理的方式來處理受管理身分識別中的資料。

  如果要求的身分識別是受管理的 (可使用 `MAMPolicyManager.getIsIdentityManaged` 檢查)，但應用程式無法使用該帳戶 (例如，因為必須先在應用程式中設定如電子郵件帳戶等的帳戶)，則應該拒絕身分識別切換。



  ### <a name="file-protection"></a>檔案保護

  每個檔案都有建立時根據執行緒和處理程序身分識別而來的相關聯身分識別。 此身分識別將會用於檔案加密和選擇性抹除。 只有其身分識別為受管理且具有需要加密之原則的檔案才會進行加密。 SDK 的預設選擇性功能抹除，只會抹除與已要求抹除之受管理身分識別相關聯的檔案。 應用程式可使用 `MAMFileProtectionManager` 類別來查詢或變更檔案的身分識別。

  ```java
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

        /**
         * Get the protection info on a file.
         *
         * @param file
         *            File to get information on.
         * @return File protection info, or null if there is no protection info.
         * @throws IOException
         *             If the file cannot be read or opened.
         */
        public static MAMFileProtectionInfo getProtectionInfo(final ParcelFileDescriptor file) throws IOException;

    }

    public interface MAMFileProtectionInfo {
        String getIdentity();
    }

  ```

離線模式需要檔案身分識別標記。 下列各點應該列入考量：

  * 如果未安裝公司入口網站，則無法標記檔案的身分識別。

  * 如果已安裝公司入口網站，但應用程式沒有 Intune MAM 原則，則檔案將無法確實標記身分識別。

  * 當檔案身分識別標記變成可用時，所有先前建立的檔案都會視為個人/未受管理 (屬於空字串身分識別)，除非應用程式之前已安裝為受單一身分識別管理的應用程式，在此情況下則會將它們視為屬於已註冊的使用者。

### <a name="directory-protection"></a>目錄保護

目錄保護可以使用和保護檔案相同的 `protect` 方法來進行保護。 請注意，目錄保護會以遞迴方式套用至目錄中的所有檔案和子目錄，以及在目錄內新建立的檔案上。 由於目錄保護是以以遞迴方式套用，針對非常大的目錄，`protect` 呼叫可能需要花費一些時間才能完成。 基於那個原因，若應用程式要將保護套用至含有大量檔案的目錄，我們建議在背景執行緒上以非同步方式執行 `protect`。

### <a name="data-protection"></a>資料保護

您無法將檔案標記為屬於多重身分識別。 如果應用程式必須將屬於不同使用者的資料儲存到同一個檔案，則可以使用 `MAMDataProtectionManager` 所提供的功能手動執行這項操作。 這可讓應用程式加密資料，並將它繫結至特定的使用者。 加密資料適合存放到磁碟的檔案中。 您可以查詢與身分識別相關聯的資料，並於稍後解密資料。

會運用 `MAMDataProtectionManager` 的應用程式，應該實作針對 `MANAGEMENT_REMOVED` 通知的接收器。 如果透過此類別獲得保護的緩衝區在受到保護期間有啟用檔案加密，在此通知完成之後，該緩衝區將會無法讀取。 應用程式可以透過在此通知期間於所有緩衝區上呼叫 MAMDataProtectionManager.unprotect 來補救此情況。 請注意，若想要保留身分識別資訊，也可以在此通知期間呼叫保護 (加密在通知期間一定會停用)。

```java

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

### <a name="content-providers"></a>內容提供者

如果應用程式透過 **ContentProvider** 提供 **ParcelFileDescriptor** 以外的公司資料，該應用程式必須在 `MAMContentProvider` 中呼叫 `isProvideContentAllowed(String)` 方法，並針對內容傳遞擁有者身分識別的 UPN (使用者主體名稱)。 如果此函數傳回 false，內容「可能不會」傳回給呼叫者。 透過內容提供者傳回的檔案描述元會自動根據檔案身分識別進行處理。

### <a name="selective-wipe"></a>選擇性抹除

如果應用程式註冊 `WIPE_USER_DATA` 通知，它將無法取得 SDK 預設選擇性抹除行為的好處。 針對感知多重身分識別的應用程式，此影響可能更為明顯，因為 MAM 預設選擇性抹除只會抹除其身分識別為抹除目標的檔案。

若多重身分識別感知應用程式想要執行 MAM 預設選擇性抹除，「且」__想要在抹除上執行自己的動作，便應該註冊 `WIPE_USER_AUXILIARY_DATA` 通知。 SDK 會立即傳送這項通知，再執行 MAM 預設選擇性抹除。 應用程式一律不應同時註冊 WIPE_USER_DATA 和 WIPE_USER_AUXILIARY_DATA。


## <a name="style-customization-optional"></a>樣式自訂 (選擇性)

您可以對由 MAM SDK 產生的檢視進行視覺上的自訂，以使它能更加符合所整合的目標應用程式。 您可以自訂主要、次要及背景色彩，以及應用程式標誌的大小。 此樣式自訂為選擇性，若沒有設定任何自訂樣式，系統將會使用預設值。


### <a name="how-to-customize"></a>如何自訂
若要將樣式變更套用至 Intune MAM 檢視，您必須先建立樣式覆寫 XML 檔案。 此檔案必須置於應用程式的 "/res/xml" 目錄，您可以任意命名檔案。 下列為此檔案必須遵循之格式的範例。

```xml
<?xml version="1.0" encoding="utf-8"?>
<styleOverrides>
    <item
        name="foreground_color"
        resource="@color/red"/>
    <item
        name="accent_color"
        resource="@color/blue"/>
    <item
        name="background_color"
        resource="@color/green"/>
    <item
        name="logo_image"
        resource="@drawable/app_logo"/>
</styleOverrides>

```

您必須重複使用已存在於應用程式內的資源。 例如，您必須在 colors.xml 檔案中定義綠色的色彩，並在此參考它。 您不能使用十六進位色彩代碼 "#0000ff"。 應用程式標誌的大小上限為 110 DIP (DP)。 您可以使用較小的標誌影像，但符合大小上限的影像將能提供最佳的外觀。 如果您超過 110 DIP 的限制，該影像將會縮小並可能變得模糊。

以下為允許的樣式屬性、它們所控制的 UI 元素、其 XML 屬性項目名稱，以及每個屬性所預期之資源類型的完整清單。

|樣式屬性 | 受影響的 UI 元素 | 屬性項目名稱 | 預期的資源類型 |
| -- | -- | -- | -- |
| 背景色彩 | PIN 畫面背景色彩 <Br>PIN 方塊填滿色彩 | background_color | Color |
| 前景色彩 | 前景文字色彩 <br> 預設狀態的 PIN 方塊邊界 <br> 使用者輸入 PIN 時的 PIN 方塊字元 (包含模糊字元)| foreground_color | Color|
| 輔色 | 反白顯示時的 PIN 方塊邊界 <br> 超連結 |accent_color | Color |
| 應用程式標誌 | 顯示在 Intune 應用程式 PIN 畫面的大型標誌 | logo_image | Drawable |

## <a name="limitations"></a>限制

### <a name="file-size-limitations"></a>檔案大小限制

針對沒有搭配 [ProGuard (英文)](http://proguard.sourceforge.net/) 執行的大型程式碼基底，Dalvik 可執行檔格式的限制將會造成問題。 具體來說，可能會發生下列限制：

1.    65K 的欄位限制。
2.    65K 的方法限制。



### <a name="policy-enforcement-limitations"></a>原則強制執行限制

* **螢幕擷取**：SDK 無法強制執行 Activity 中已經透過 Activity.onCreate 完成的新螢幕擷取設定值。 這會導致應用程式已設定為停用螢幕擷取畫面一段時間，但仍可取得螢幕擷取畫面。

* **使用內容解析程式**：「傳送或接收」Intune 原則可能會封鎖或部分封鎖內容解析程式的使用，不讓其存取另一個應用程式中的內容提供者。 這將導致 ContentResolver 方法傳回 null，或者擲回錯誤值 (例如，若受到封鎖， `openOutputStream` 將會擲回 `FileNotFoundException` )。 應用程式可以藉由呼叫下列項目，判斷透過內容解析程式無法寫入資料是否起因於原則 (或可能由原則造成)：

    ```java
    MAMComponents.get(AppPolicy.class).getIsSaveToLocationAllowed(contentURI);
    ```

### <a name="exported-services"></a>匯出服務

 Intune App SDK 隨附的 AndroidManifest.xml 檔案包含 **MAMNotificationReceiverService**，其必須為匯出的服務，才能讓公司入口網站傳送通知給可搭配 Intune 的應用程式。 服務會檢查呼叫者以確保僅允許公司入口網站傳送通知。



## <a name="expectations-of-the-sdk-consumer"></a>SDK 取用者的期望

Intune SDK 會維護由 Android API 所提供的合約，但可能會因為強制執行原則，而更頻繁地觸發失敗狀況。 下列 Android 最佳作法可降低失敗的可能性：

* Android SDK 函式如果可能會傳回 null，則現在為 null 的可能性更高。  若要將問題降至最低，請確定 null 檢查是在正確的位置。

* 針對可以檢查的功能，必須透過其 MAM 取代項目 API 進行檢查。

* 任何衍生的函式皆必須透過其超級類別版本進行呼叫。

* 避免以模稜兩可的方式使用任何 API。 例如，在未檢查 requestCode 的情況下使用 `Activity.startActivityForResult`，將會導致奇怪的行為。

## <a name="recommended-android-best-practices"></a>建議的 Android 最佳作法

* 所有程式庫專案應盡可能共用相同的 android:package。 這不會在執行階段偶發性地發生失敗，而純粹是建置時間問題。 較新版本的 Intune App SDK 將會移除部分的冗餘項目。

* 使用最新的 Android SDK 建置工具。

* 移除所有不必要和未使用的程式庫 (例如 android.support.v4)


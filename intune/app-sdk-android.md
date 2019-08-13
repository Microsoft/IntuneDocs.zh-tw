---
title: Microsoft Intune App SDK for Android 開發人員指南
description: Microsoft Intune App SDK for Android 可讓您將 Intune 行動應用程式管理 (MAM) 併入 Android 應用程式中。
keywords: SDK
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/24/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 0100e1b5-5edd-4541-95f1-aec301fb96af
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: edc193c80960872cc3a0e25438432195de3a7c34
ms.sourcegitcommit: e6edfbfd63dd7c2500ce1123205aa2af9a7e8e2e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2019
ms.locfileid: "68783203"
---
# <a name="microsoft-intune-app-sdk-for-android-developer-guide"></a>Microsoft Intune App SDK for Android 開發人員指南

> [!NOTE]
> 您可能想要先閱讀 [Intune App SDK 概觀](app-sdk.md)，其中涵蓋 SDK 目前的功能，並說明如何在每個支援的平台上進行整合準備。

Microsoft Intune App SDK for Android 可讓您將 Intune 應用程式保護原則 (也稱為 **APP** 或 MAM 原則) 併入原生 Android 應用程式中。 Intune 的受控應用程式是與 Intune App SDK 整合的應用程式。 Intune 系統管理員可在 Intune 主動管理應用程式時，輕鬆地將應用程式保護原則部署至 Intune 的受控應用程式。


## <a name="whats-in-the-sdk"></a>SDK 的功能

Intune App SDK 包含下列檔案：

* **Microsoft.Intune.MAM.SDK.aar**：SDK 元件 (支援程式庫 JAR 檔案除外)。
* **Microsoft.Intune.MAM.SDK.Support.v4.jar**：必要的類別，可在使用 Android v4 支援程式庫的應用程式中啟用 MAM。
* **Microsoft.Intune.MAM.SDK.Support.v7.jar**：必要的類別，可在使用 Android v7 支援程式庫的應用程式中啟用 MAM。
* **Microsoft.Intune.MAM.SDK.Support.v17.jar**：必要的類別，可在使用 Android v17 支援程式庫的應用程式中啟用 MAM。 
* **Microsoft.Intune.MAM.SDK.Support.Text.jar**：必要的類別，可在使用 `android.support.text` 套件 Android 支援程式庫類別的應用程式中啟用 MAM。
* **Microsoft.Intune.MDM.SDK.DownlevelStubs.jar**：這個 jar 包含 Android 系統類別的虛設常式，它們只出現在較新的裝置上，但可由 MAMActivity 中的方法參考。 較新的裝置會忽略這些虛設常式類別。 只有當應用程式對衍生自 MAMActivity 的類別執行反映時，才需要這個 jar，大部分的應用程式並不需要包含它。 如果使用這個 jar，必須仔細排除它所有來自 ProGuard 的類別。 它們全都位在 "android" 根套件下
* **com.microsoft.intune.mam.build.jar**：Gradle 外掛程式，可[輔助整合 SDK](#build-tooling)。
* **CHANGELOG.txt**：提供每個 SDK 版本中的變更記錄。
* **THIRDPARTYNOTICES.TXT**：確認將會編譯至應用程式中的協力廠商及/或 OSS 程式碼的屬性通知。

## <a name="requirements"></a>需求

### <a name="android-versions"></a>Android 版本
SDK 支援 Android API 19 (Android 4.4+) 到 Android API 28 (Android 9.0)。

### <a name="company-portal-app"></a>公司入口網站應用程式
Intune App SDK for Android 必須仰賴裝置上的[公司入口網站](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal)應用程式來啟用應用程式保護原則。 公司入口網站會從 Intune 服務擷取應用程式保護原則。 應用程式初始化時，它會載入原則和程式碼，以從公司入口網站強制執行該原則。

> [!NOTE]
> 當裝置上沒有公司入口網站應用程式時，Intune 的受控應用程式會具有和不支援 Intune 應用程式保護原則的一般應用程式相同的行為。

對於沒有裝置註冊的應用程式保護，使用者「不」 __ 需要使用公司入口網站應用程式註冊裝置。

## <a name="sdk-integration"></a>SDK 整合

### <a name="sample-app"></a>範例應用程式
示範如何適當地與 Intune 應用程式 SDK 整合的範例可在 [GitHub](https://github.com/msintuneappsdk/Taskr-Sample-Intune-Android-App) 上取得。 此範例使用 [Gradle 建置外掛程式](#gradle-build-plugin)。

### <a name="referencing-intune-app-libraries"></a>參考 Intune 應用程式庫

Intune App SDK 是不含外部相依性的標準 Android 程式庫。 **Microsoft.Intune.MAM.SDK.aar** 包含啟用應用程式保護原則所需的介面，以及和 Microsoft Intune 公司入口網站應用程式互通所需的程式碼。

**Microsoft.Intune.MAM.SDK.aar** 必須指定為 Android 程式庫參考。 若要這麼做，請在 Android Studio 中開啟應用程式專案，然後移至 [檔案] > [新增] > [新模組]  ，然後選取 [匯入 .JAR/.AAR 套件]  。 然後選取我們的 Android 封存套件 Microsoft.Intune.MAM.SDK.aar，以為 .AAR 建立模組。 以滑鼠右鍵按一下含有您應用程式程式碼的模組，並移至 [模組設定]   > [相依性] 索引標籤   >  **+ 圖示** > [模組相依性]  > 選取您剛才建立的 MAM SDK AAR 模組 > [確定]  。 這樣可確保當您建置專案時，會使用 MAM SDK 編譯您的模組。

此外，**Microsoft.Intune.MAM.SDK.Support.XXX.jar** 程式庫包含與 `android.support.XXX` 程式庫相對應的 Intune 變體。 並非所有應用程式都需要仰賴支援程式庫，因此 Microsoft.Intune.MAM.SDK.aar 並未內建這些項目。

#### <a name="proguard"></a>ProGuard

如果您將 [ProGuard](http://proguard.sourceforge.net/) (或任何其他壓縮/混淆機制) 作為建置步驟，則必須將 SDK 額外的設定包含在內。 當組建包含 .AAR 時，我們的規則會自動整合至 ProGuard 步驟，並保留必要的類別檔。

Azure Active Directory Authentication Library (ADAL) 可能會有屬於自己的 ProGuard 限制。 如果應用程式整合了 ADAL，則您必須遵循這些限制的相關 ADAL 文件。

### <a name="build-tooling"></a>建置工具
Intune App SDK 是一種 Android 程式庫，可讓您的應用程式支援並參與 Intune 原則的實施。 某些原則會要求[您的應用程式明確參與實施](#enable-features-that-require-app-participation)，不過大部分都是以半自動方式實施。 此自動實施需要應用程式將數個 Android 基底類別的繼承項目取代為 MAM 的對等繼承項目；同樣地，也要將某些 Android 系統服務類別的呼叫取代為 MAM 對等項目的呼叫。 所需的特定取代項目詳述[如下](#class-and-method-replacements)。

手動執行這些取代作業的程序非常繁瑣。 反之，SDK 提供的建置工具 (適用於 Gradle 組建的外掛程式以及適用於非 Gradle 組建的命令列工具) 可自動執行取代作業。 這些工具會轉換 Java 編譯所產生的類別檔案，而不會修改原本的原始程式碼，

這些工具只會執行[直接取代作業](#class-and-method-replacements)。 它們不會執行任何更複雜的 SDK 整合，如[另存新檔原則](#enable-features-that-require-app-participation)、[多重身分識別](#multi-identity-optional)、[APP-WE 註冊](#app-protection-policy-without-device-enrollment)、[AndroidManifest 修改](#manifest-replacements)或 [ADAL 設定](#configure-azure-active-directory-authentication-library-adal)，因此您的應用程式必須完成上述項目後，才能完全啟用 Intune。 請仔細檢閱這份文件與您應用程式相關之整合點的其餘部分。

> [!NOTE]
> 您可以藉由手動取代方式，針對已經執行部分或完整 MAM SDK 來源整合的專案執行這些工具。 您的專案仍然必須將 MAM SDK 列為相依性。

### <a name="gradle-build-plugin"></a>Gradle 建置外掛程式
如果您的應用程式並非使用 Gradle 建置，請跳至[使用命令列工具整合](#command-line-build-tool)。 

App SDK 外掛程式是與 SDK 一起散發，如同 **GradlePlugin/com.microsoft.intune.mam.build.jar**。 若要讓 Gradle 找得到外掛程式，您必須將它新增至 buildscript classpath。 外掛程式相依於 [Javassist](https://jboss-javassist.github.io/javassist/)，因此也必須新增。 若要將它們新增至 classpath，請將下列內容新增至您的根 `build.gradle`

```groovy
buildscript {
    repositories {
        jcenter()
    }
    dependencies {
        classpath "org.javassist:javassist:3.22.0-GA"
        classpath files("$PATH_TO_MAM_SDK/GradlePlugin/com.microsoft.intune.mam.build.jar")
    }
}
```

然後，在 APK 專案的 `build.gradle` 檔案中，直接套用外掛程式

```groovy
apply plugin: 'com.microsoft.intune.mam'
```

根據預設，外掛程式**只會**在 `project` 相依性上運作。
測試編譯不會受到影響。 可提供設定以列出
* 要排除的專案
* [要包含的外部相依性](#usage-of-includeexternallibraries) 
* 要排除處理的特定類別
* 要排除處理的變體。 這些項目可以指完整的變體名稱或單一類別。 例如
  * 如果您的應用程式具有 `debug` 和 `release` 組建類型，搭配 {`savory`、`sweet`} 和 {`vanilla`、`chocolate`} 類別，您可以指定
  * `savory` 以排除所有具有 savory 類別的變體，或 `savoryVanillaRelease` 以僅排除該確切變體。

#### <a name="example-partial-buildgradle"></a>部分 build.gradle 的範例

```groovy

apply plugin: 'com.microsoft.intune.mam'

dependencies {
    implementation project(':product:FooLib')
    implementation project(':product:foo-project')
    implementation fileTree(dir: "libs", include: ["bar.jar"])
    implementation fileTree(dir: "libs", include: ["zap.jar"])
    implementation "com.contoso.foo:zap-artifact:1.0.0"
    implementation "com.microsoft.bar:baz:1.0.0"

    // Include the MAM SDK
    implementation files("$PATH_TO_MAM_SDK/Microsoft.Intune.MAM.SDK.aar")
}
intunemam {
    excludeProjects = [':product:FooLib']
    includeExternalLibraries = ['bar.jar', "com.contoso.foo:zap-artifact", "com.microsoft.*", "!com.microsoft.qux*"]
    excludeClasses = ['com.contoso.SplashActivity']
    excludeVariants=['savory']
}
```

這會造成下列影響：
* `:product:FooLib` 不會重寫，因為它包含在 `excludeProjects` 中
* `:product:foo-project` 會重寫，但會略過 `com.contoso.SplashActivity`，因為它位於 `excludeClasses` 中
* `bar.jar` 會重寫，因為它包含在 `includeExternalLibraries` 中
* `zap.jar` **不會**重寫，因為它不是專案，亦不包含在 `includeExternalLibraries` 中
* `com.contoso.foo:zap-artifact:1.0.0` 會重寫，因為它包含在 `includeExternalLibraries` 中
* `com.microsoft.bar:baz:1.0.0` 會重寫，因為它透過萬用字元 (`com.microsoft.*`) 包含在 `includeExternalLibraries` 中。
* 即使符合與先前項目相同的萬用字元，`com.microsoft.qux:foo:2.0` 也不會遭到重寫，因為已透過否定模式明確地排除它。

#### <a name="usage-of-includeexternallibraries"></a>includeExternalLibraries 的使用方式

因為外掛程式預設只會在 project 相依性上運作 (通常由 `project()` 函式提供)，因此任何 `fileTree(...)` 所指定的相依性或取自 Maven 或其他套件來源 (例如 "`com.contoso.bar:baz:1.2.0`") 的相依性都必須提供給 `includeExternalLibraries` 屬性 (如果它們需要按照下方說明的準則進行 MAM 處理的話)。 支援萬用字元 ("*")。 開頭為 `!` 的項目為否定項目，可用來排除原先會包含在萬用字元範圍內的程式庫。

當使用成品標記法來指定外部相依性時，建議省略 `includeExternalLibraries` 值中的版本元件。 如果您將版本包含在內，它必須是確切的版本。 不支援動態版本規格 (例如 `1.+`)。

當您判斷是否需要在 `includeExternalLibraries` 中包含程式庫時，應該使用的一般規則是以下列兩個問題為依據：
1. 程式庫當中的類別是否具備 MAM 對等項目？ 範例：`Activity`、`Fragment`、`ContentProvider`、`Service` 等。
2. 如果是，您的應用程式會使用這些類別嗎？

如果這兩個問題的答案均為肯定，則您應該在 `includeExternalLibraries` 中包含該程式庫。 

| 案例 | 應該包含嗎？ |
|--|--|
| 您可在應用程式中包含 PDF 檢視器程式庫，並在使用者嘗試檢視 PDF 時，在應用程式中使用檢視器 `Activity` | 是 |
| 您可在應用程式中包含 HTTP 程式庫，以取得增強的 Web 效能 | 否 |
| 您可包含類似 React Native 的程式庫，其中包含衍生自 `Activity`、`Application` 和 `Fragment` 的類別，且您可以在應用程式中使用或進一步衍生這些類別 | 是 |
| 您可包含類似 React Native 的程式庫，其中包含衍生自 `Activity`、`Application` 和 `Fragment` 的類別，但您只能使用靜態協助程式或公用程式類別 | 否 |
| 您可包含具有衍生自 `TextView` 之檢視類別的程式庫，且您可以在應用程式中使用或進一步衍生這些類別 | 是 |

#### <a name="reporting"></a>報告
建置外掛程式可產生其所進行變更的 HTML 報告。 若要要求產生此報告，請在 `report = true` 設定區塊中指定 `intunemam`。 若產生報告，則報告會寫入建置目錄中的 `outputs/logs`。

```groovy
intunemam {
    report = true
}
```

#### <a name="dependencies"></a>相依性

Gradle 外掛程式具有 [Javassist](https://jboss-javassist.github.io/javassist/) 相依性，其必須可供用於 Gradle 的相依性解析 (如上面所述)。 Javassist 僅用於外掛程式執行時的建置時間。 系統不會將任何 Javassist 程式碼新增至您的應用程式。

> [!NOTE] 
> 您必須使用版本 3.0 或更新版本的 Android Gradle 外掛程式和 Gradle 4.1 或更新版本。

### <a name="command-line-build-tool"></a>命令列建置工具
如果您的組建使用 Gradle，請跳至[下一節](#class-and-method-replacements)。

命令列建置工具位於 SDK 的 `BuildTool` 資料夾。 它會執行如以上詳述之 Gradle 外掛程式的相同函式，但是可以整合到自訂或非 Gradle 組建系統。 由於它是比較通用的工具，要叫用時更加複雜，因此建議盡量使用 Gradle 外掛程式。

#### <a name="using-the-command-line-tool"></a>使用命令列工具

您可以使用位於 `BuildTool\bin` 目錄的協助程式指令碼來叫用命令列工具。

工具必須要有下列的參數。

| 參數 | 說明 |
| -- | -- |
| `--input` | 以分號分隔的 jar 檔案與類別檔案目錄清單，以供修改。 這應該包括所有您想要重寫的 jar/目錄。 |
| `--output` | 以分號分隔的 jar 檔案與目錄清單，以儲存修改過的類別。 每個輸入項目都應該要有一個輸出項目，且必須按照順序提列。 |
| `--classpath` | 組建 classpath。 可包含 jar 和類別目錄。 |
| `--excludeClasses`| 以分號分隔的清單，其中包含要排除重寫的類別名稱。 |

除了 `--excludeClasses` 是選用項目以外，所有參數均為必要。

> [!NOTE] 
> 在 UNIX 式系統上，分號是命令的分隔符號。 若要避免殼層將命令分割，請務必使用 \' 逸出每個分號，或使用引號括住完整的參數。

#### <a name="example-command-line-tool-invocation"></a>範例命令列工具引動過程

``` batch
> BuildTool\bin\BuildTool.bat --input build\product-foo-project;libs\bar.jar --output mam-build\product-foo-project;mam-build\libs\bar.jar --classpath build\zap.jar;libs\Microsoft.Intune.MAM.SDK\classes.jar;%ANDROID_SDK_ROOT%\platforms\android-27\android.jar --excludeClasses com.contoso.SplashActivity
```

這會造成下列影響：

* `product-foo-project` 目錄會重寫為 `mam-build\product-foo-project`
* `bar.jar` 會重寫為 `mam-build\libs\bar.jar`
* `zap.jar` **不會**重寫，因為它僅提列於 `--classpath` 中
* `com.contoso.SplashActivity` 類別**不會**重寫，即使它是在 `--input` 中

> [!NOTE] 
> 建置工具目前不支援 aar 檔案。 如果建置系統尚未在處理 aar 檔案時擷取 `classes.jar`，您就必須先加以擷取才能叫用建置工具。


## <a name="class-and-method-replacements"></a>取代類別和方法

您必須將 Android 基底類別取代為其各自的 MAM 對等項目，以啟用 Intune 管理。 SDK 類別的位置介於 Android 基底類別和應用程式本身針對該類別的衍生版本之間。 例如，應用程式活動最後的繼承階層可能如下：`Activity` > `MAMActivity` >
`AppSpecificActivity`。 MAM 層會篩選系統作業的呼叫，以便順暢地提供應用程式的全球受控檢視。

除了基底類別，還有一些是您應用程式不需衍生即可使用的類別 (例如`MediaPlayer`)，這些類別也需要 MAM 對等項目，而[有些方法呼叫也必須進行取代](#wrapped-system-services)。 下面提供精確的詳細資料。

本節詳述的所有取代項目都可由 SDK [建置工具](#build-tooling)自動執行。 



| Android 基底類別 | Intune App SDK 取代 |
|--|--|
| android.app.Activity | MAMActivity |
| android.app.ActivityGroup | MAMActivityGroup |
| android.app.AliasActivity | MAMAliasActivity |
| android.app.Application | MAMApplication |
| android.app.Dialog | MAMDialog |
| android.app.AlertDialog.Builder | MAMAlertDialogBuilder |
| android.app.DialogFragment | MAMDialogFragment |
| android.app.ExpandableListActivity | MAMExpandableListActivity |
| android.app.Fragment | MAMFragment |
| android.app.IntentService | MAMIntentService |
| android.app.LauncherActivity | MAMLauncherActivity |
| android.app.ListActivity | MAMListActivity |
| android.app.ListFragment | MAMListFragment |
| android.app.NativeActivity | MAMNativeActivity |
| android.app.PendingIntent | MAMPendingIntent (請參閱[擱置的意圖](#pendingintent)) |
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
| android.media.MediaPlayer | MAMMediaPlayer |
| android.media.MediaMetadataRetriever | MAMMediaMetadataRetriever |
| android.provider.DocumentsProvider | MAMDocumentsProvider |
| android.preference.PreferenceActivity | MAMPreferenceActivity |
| android.support.multidex.MultiDexApplication | MAMMultiDexApplication |
| android.widget.TextView | MAMTextView |
| android.widget.AutoCompleteTextView | MAMAutoCompleteTextView |
| android.widget.CheckedTextView | MAMCheckedTextView |
| android.widget.EditText | MAMEditText |
| android.inputmethodservice.ExtractEditText | MAMExtractEditText |
| android.widget.MultiAutoCompleteTextView | MAMMultiAutoCompleteTextView |

> [!NOTE]
> 即使您的應用程式不需要自己的衍生 `Application` 類別，[請參閱下文的 `MAMApplication`](#mamapplication)

### <a name="microsoftintunemamsdksupportv4jar"></a>Microsoft.Intune.MAM.SDK.Support.v4.jar：

| Android 類別 | Intune App SDK 取代 |
|--|--|
| android.support.v4.app.DialogFragment | MAMDialogFragment
| android.support.v4.app.FragmentActivity | MAMFragmentActivity
| android.support.v4.app.Fragment | MAMFragment
| android.support.v4.app.JobIntentService | MAMJobIntentService
| android.support.v4.app.TaskStackBuilder | MAMTaskStackBuilder
| android.support.v4.content.FileProvider | MAMFileProvider
| android.support.v4.content.WakefulBroadcastReceiver | MAMWakefulBroadcastReceiver

### <a name="microsoftintunemamsdksupportv7jar"></a>Microsoft.Intune.MAM.SDK.Support.v7.jar：

|Android 類別 | Intune App SDK 取代 |
|--|--|
| android.support.v7.app.AlertDialog.Builder | MAMAlertDialogBuilder |
| android.support.v7.app.AppCompatActivity | MAMAppCompatActivity |
| android.support.v7.widget.AppCompatAutoCompleteTextView | MAMAppCompatAutoCompleteTextView |
| android.support.v7.widget.AppCompatCheckedTextView | MAMAppCompatCheckedTextView |
| android.support.v7.widget.AppCompatEditText | MAMAppCompatEditText |
| android.support.v7.widget.AppCompatMultiAutoCompleteTextView | MAMAppCompatMultiAutoCompleteTextView |
| android.support.v7.widget.AppCompatTextView | MAMAppCompatTextView |

### <a name="microsoftintunemamsdksupportv17jar"></a>Microsoft.Intune.MAM.SDK.Support.v17.jar:
|Android 類別 | Intune App SDK 取代 |
|--|--|
| android.support.v17.leanback.widget.SearchEditText | MAMSearchEditText |

### <a name="microsoftintunemamsdksupporttextjar"></a>Microsoft.Intune.MAM.SDK.Support.Text.jar:
|Android 類別 | Intune App SDK 取代 |
|--|--|
| android.support.text.emoji.widget.EmojiAppCompatEditText | MAMEmojiAppCompatEditText |
| android.support.text.emoji.widget.EmojiAppCompatTextView | MAMEmojiAppCompatTextView |
| android.support.text.emoji.widget.EmojiEditText | MAMEmojiEditText |
| android.support.text.emoji.widget.EmojiTextView | MAMEmojiTextView |

### <a name="renamed-methods"></a>重新命名的方法
在許多情況下，Android 類別中可用的方法已在 MAM 取代類別中被標示為完稿。 在此情況下，MAM 取代類別會提供您應該覆寫的類似具名方法 (通常後置字元為 `MAM`)。 例如，當衍生自 `MAMActivity`，而不是覆寫 `onCreate()` 然後呼叫 `super.onCreate()` 時，`Activity` 必須覆寫 `onMAMCreate()` 並呼叫 `super.onMAMCreate()`。 Java 編譯器應該強制執行完稿的限制，以防止意外覆寫原始的方法，而不是 MAM 對等項目。

### <a name="mamapplication"></a>MAMApplication
如果您的應用程式會建立 `android.app.Application` 的子類別，則您**必須**改為建立 `com.microsoft.intune.mam.client.app.MAMApplication` 的子類別。 如果您的應用程式不會建立 `android.app.Application` 的子類別，則您**必須**將 `"com.microsoft.intune.mam.client.app.MAMApplication"` 設定為 AndroidManifest.xml 之 `<application>` 標記的 `"android:name"` 屬性。

### <a name="pendingintent"></a>PendingIntent
您必須使用 `MAMPendingIntent.get*` 方法，而不是 `PendingIntent.get*`。 之後，您可以像往常一樣使用結果 `PendingIntent`。

### <a name="wrapped-system-services"></a>包裝的系統服務
對於某些系統服務類別來說，您必須在 MAM 包裝函式類別上呼叫靜態方法，而不是直接在服務執行個體上叫用所需的方法。 例如，若要呼叫 `getSystemService(ClipboardManager.class).getPrimaryClip()`，必須變成呼叫 `MAMClipboardManager.getPrimaryClip(getSystemService(ClipboardManager.class)`。 不建議您手動進行這些取代作業。 相反地，請讓 BuildPlugin 代勞。

| Android 類別 | Intune App SDK 取代 |
|--|--|
| android.content.ClipboardManager | MAMClipboard |
| android.content.ContentProviderClient | MAMContentProviderClientManagement |
| android.content.ContentResolver | MAMContentResolverManagement |
| android.content.pm.PackageManager | MAMPackageManagement |
| android.app.DownloadManager | MAMDownloadManagement |
| android.print.PrintManager | MAMPrintManagement |
| android.support.v4.print.PrintHelper | MAMPrintHelperManagement |
| android.view.View | MAMViewManagement |
| android.view.DragEvent | MAMDragEventManagement |

某些類別會包裝大多數的方法 (例如 `ClipboardManager`、`ContentProviderClient`、`ContentResolver` 及 `PackageManager`)，其他類別則可能只會包裝一或兩個方法 (例如 `DownloadManager`、`PrintManager`、`PrintHelper`、`View` 及 `DragEvent`)。 若您沒有使用 BuildPlugin，請參閱 MAM 對等類別公開的 API，來了解確切的方法。 

### <a name="manifest-replacements"></a>資訊清單取代
有可能會需要在資訊清單及 Java 程式碼中執行部分上述類別取代。 特殊注意事項：
* 針對 `android.support.v4.content.FileProvider` 的資訊清單參考，必須以 `com.microsoft.intune.mam.client.support.v4.content.MAMFileProvider` 取代。

## <a name="androidx-libraries"></a>AndroidX 程式庫
除了 Android P，Google 宣告了新 (更名) 的一組支援程式庫 AndroidX，且版本 28 是現有 android.support 程式庫的最後一個主要版本。

不同於 Android 支援程式庫，這次我們不提供 AndroidX 程式庫的 MAM 變體。 相反地，您應將 AndroidX 視為任何其他外部程式庫，並將其設定為由建置外掛程式/工具來重寫。 針對 Gradle 組建，您可以在外掛程式設定的 `includeExternalLibraries` 欄位中包含 `androidx.*` 來進行上述作業。命令列工具的引動過程都必須明確列出所有的 jar 檔案。
## <a name="sdk-permissions"></a>SDK 權限

Intune App SDK 需要在與其整合的應用程式上，具有三個 [Android 系統權限](https://developer.android.com/guide/topics/security/permissions.html)：

* `android.permission.GET_ACCOUNTS` (會在必要時於執行階段要求)

* `android.permission.MANAGE_ACCOUNTS`

* `android.permission.USE_CREDENTIALS`

Azure Active Directory 驗證程式庫 ([ADAL](https://azure.microsoft.com/documentation/articles/active-directory-authentication-libraries/)) 需要這些權限才能執行代理驗證。 如果未將這些權限授與應用程式或使用者已撤銷這些權限，則會停用需要訊息代理程式 (公司入口網站應用程式) 的驗證流程。

## <a name="logging"></a>記錄

記錄應該要盡早初始化，以取得最豐富的記錄資料。 `Application.onMAMCreate()` 通常是初始化記錄的最佳位置。

若要在應用程式中接收 MAM 記錄，請建立 [Java 處理常式 (英文)](https://docs.oracle.com/javase/7/docs/api/java/util/logging/Handler.html) 並將它新增至 `MAMLogHandlerWrapper`。 這將會針對每個記錄訊息在應用程式處理常式上叫用 `publish()`。

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

有數個 SDK 無法自行實作的應用程式保護原則。 此應用程式可控制其行為，以使用可在以下 `AppPolicy` 介面中找到的數個 API，實現這些功能。 若要擷取 `AppPolicy` 執行個體，請使用 `MAMPolicyManager.getPolicy`。

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
 * Checks whether any activities which could handle the given intent are allowed by policy. Returns false only if all
 * activities which could otherwise handle the intent are blocked. If there are no activities which could handle the intent
 * regardless of policy, returns true. If some activities are allowed and others blocked, returns true. Note that it is not
 * necessary to use this method for policy enforcement. If your app attempts to launch an intent for which there are no
 * allowed activities, MAM will display a dialog explaining the situation to the user.
 *
 * @param intent
 *         intent to check
 *
 * @return whether any activities which could handle this intent are allowed.
*/
boolean areIntentActivitiesAllowed(Intent intent);

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
 * This method is intended for diagnostic/telemetry purposes only. It can be used to discover whether
 * file encryption is in use. File encryption is transparent to the app, and the app should not need
 * to make any business logic decisions based on this.
 * 
 * @return True if file encryption is in use.
 */
boolean diagnosticIsFileEncryptionInUse();

/**
 * Return the policy in string format to the app.
 *  
 * @return The string representing the policy.
 */
String toString();

}
```

> [!NOTE]
> `MAMPolicyManager.getPolicy` 一律會傳回非 null 的應用程式原則，即使裝置或應用程式不受 Intune 管理原則限制，亦是如此。

### <a name="example-determine-if-pin-is-required-for-the-app"></a>範例：判斷應用程式是否需要 PIN

在 IT 系統管理員已設定 SDK 以提示輸入應用程式 PIN 的情況下，如果應用程式有屬於自己的 PIN 使用者體驗，您可能會想要停用它。 若要判斷 IT 系統管理員是否已將應用程式 PIN 原則部署至此應用程式，請針對目前的使用者呼叫下列方法：

```java

MAMPolicyManager.getPolicy(currentActivity).getIsPinRequired();
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
MAMPolicyManager.getPolicy(currentActivity).getIsSaveToLocationAllowed(
SaveLocation service, String username);
```

`service` 參數必須為下列其中一個 `SaveLocation` 值：


- `SaveLocation.ONEDRIVE_FOR_BUSINESS`
- `SaveLocation.SHAREPOINT`
- `SaveLocation.LOCAL`
- `SaveLocation.OTHER`

`username` 應為與欲儲存目標雲端服務建立關聯的 UPN/使用者名稱/電子郵件 (「不一定」  會和擁有欲儲存文件的使用者相同)。 若 AAD UPN 和雲端服務使用者名稱間的對應不存在，或使用者名稱未知，請使用 Null。

在此之前，能用來判斷使用者的原則是否允許他們將資料儲存至各種位置的方法，為位於相同 **AppPolicy** 類別中的 `getIsSaveToPersonalAllowed()`。 此函數目前已「被取代」  ，且不應該使用。下列的引動過程等同於 `getIsSaveToPersonalAllowed()`：

```java
MAMPolicyManager.getPolicy(currentActivity).getIsSaveToLocationAllowed(SaveLocation.LOCAL, userNameInQuestion);
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

* **WIPE_USER_AUXILIARY_DATA**：如果應用程式要 Intune App SDK 執行預設選擇性抹除行為，但仍想要在抹除發生時移除部分輔助資料，則可註冊這項通知。 此通知不適用於單一身分識別應用程式，只會傳送至多重身分識別應用程式。

* **REFRESH_POLICY**︰這項通知是在 `MAMUserNotification` 中傳送。 收到這項通知時，任何由您應用程式快取的 Intune 原則決策都必須無效化並進行更新。 若您的應用程式並未儲存任何原則假設，它便不需要為此通知進行登錄。

* **REFRESH_APP_CONFIG**︰這項通知是在 `MAMUserNotification` 中傳送。 收到這項通知時，任何快取的應用程式設定資料都必須無效化並進行更新。

* **MANAGEMENT_REMOVED**：這項通知是在 `MAMUserNotification` 中傳送，並會通知應用程式它即將成為未受管理。 應用程式成為未受管理之後，它將無法讀取加密的檔案、讀取以 MAMDataProtectionManager 加密的檔案、與加密的剪貼簿互動，或參與受管理應用程式的生態系統。 請參閱下列的詳細資料。

* **MAM_ENROLLMENT_RESULT**：這項通知是在 `MAMEnrollmentNotification` 中傳送，用來通知應用程式 APP-WE 註冊嘗試已完成，並可用來提供嘗試的狀態。

* **COMPLIANCE_STATUS**：這項通知是在 `MAMComplianceNotification` 中傳送，用來通知應用程式合規性補救嘗試的結果。

> [!NOTE]
> 應用程式永遠不得同時註冊 `WIPE_USER_DATA` 和 `WIPE_USER_AUXILIARY_DATA` 通知。

### <a name="management_removed"></a>MANAGEMENT_REMOVED

`MANAGEMENT_REMOVED` 通知會指出先前由原則管理的使用者將不再由 Intune MAM 原則管理。 這不需要抹除使用者資料會登出使用者 (若需要抹除，則會傳送 `WIPE_USER_DATA` 通知)。 許多應用程式可能完全不需要處理此通知，但是使用 `MAMDataProtectionManager` 的應用程式應[特別注意此通知](#data-protection)。

當 MAM 呼叫應用程式的 `MANAGEMENT_REMOVED` 接收器時，下列內容將為 True：
* MAM 已解密屬於應用程式並在先前經過加密的檔案 (但不包含受保護的資料緩衝區)。 SD 記憶卡上並非直接屬於應用程式公用位置中的檔案 (例如「文件」或「下載」資料夾) 則不會進行解密。
* 由接受器方法 (或任何其他在接受器啟動後執行的程式碼) 建立的新檔案或受保護資料緩衝區不會進行加密。
* 由於應用程式仍然能夠存取加密金鑰，因此解密資料緩衝區等作業仍然可以成功。

當您應用程式的接受器傳回時，它便無法繼續存取加密金鑰。

## <a name="configure-azure-active-directory-authentication-library-adal"></a>設定 Azure Active Directory Authentication Library (ADAL)

首先，請參閱 [GitHub 上 ADAL 存放庫 (英文)](https://github.com/AzureAD/azure-activedirectory-library-for-android) 中的 ADAL 整合方針。

SDK 仰賴 [ADAL](https://azure.microsoft.com/documentation/articles/active-directory-authentication-libraries/) 進行[驗證](https://azure.microsoft.com/documentation/articles/active-directory-authentication-scenarios/)和條件式啟動案例，其中需要應用程式針對 [Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-whatis/)進行設定。 設定值會透過 AndroidManifest 中繼資料傳送給 SDK。

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

* **Authority** 為使用中的 AAD 授權單位。 如果此值不存在，則會使用 AAD 公用環境。
    > [!NOTE]
    > 如果您的應用程式能感知主權雲端，請勿設定此欄位。

* **ClientID** 是要使用的 AAD ClientID (也稱為應用程式識別碼)。 如果應用程式的 ClientID 已經向 Azure AD 註冊，您應該使用此 ClientID。 如果此值不存在，則會使用 Intune 預設值。

* **NonBrokerRedirectURI** 為要在無 Broker 的情況下使用的 AAD 重新導向 URI。 如果未指定，就會使用預設值 `urn:ietf:wg:oauth:2.0:oob`。 此預設值適用於大部分的應用程式。

  * 只有在 SkipBroker 為 "True" 時，才會使用 NonBrokerRedirectURI。

* **SkipBroker** 會用來覆寫預設的 ADAL SSO 參與行為。 SkipBroker 應只為指定 ClientID 的應用程式指定，**且**不支援代理驗證/全裝置 SSO。 在此情況下，其應設為 "True"。 大多數的應用程式都不應設定 SkipBroker 參數。

  * 您**必須**在資訊清單中指定 ClientID，才能指定 SkipBroker 值。

  * 指定 ClientID 時，預設值為 "False"。

  * 當 SkipBroker 為 "True" 時，便會使用 NonBrokerRedirectURI。 並未與 ADAL 整合 (因此不具有 ClientID) 的應用程式也會預設為 "True"。

### <a name="common-adal-configurations"></a>ADAL 的常見設定

下列為應用程式可以搭配 ADAL 進行設定的常見方式。 尋找您應用程式的設定，並確保 ADAL 中繼資料參數 (如上所述) 已設定為必要的值。 在所有情況下，Authority 可以針對所需的非預設環境指定。 若沒有指定，則會使用公用的生產 AAD 授權單位。

#### <a name="1-app-does-not-integrate-adal"></a>1.應用程式未整合 ADAL
資訊清單中**不得**出現 ADAL 中繼資料。

#### <a name="2-app-integrates-adal"></a>2.應用程式已整合 ADAL

|必要的 ADAL 參數| 值 |
|--|--|
| ClientID | 應用程式的 ClientID (由 Azure AD 於應用程式註冊時產生) |

可視需要指定授權單位。

您必須向 Azure AD 登錄您的應用程式，並讓您的應用程式存取應用程式保護原則服務：
* 請參閱[這裡](https://docs.microsoft.com/azure/active-directory/develop/active-directory-integrating-applications)，以取得向 Azure AD 註冊應用程式的相關資訊。
* 確定您已遵循將 Android 應用程式權限授與應用程式保護原則 (APP) 服務的步驟。 使用[開始使用 Intune SDK 指南](https://docs.microsoft.com/intune/app-sdk-get-started#next-steps-after-integration)中＜將您的應用程式存取權授與 Intune 應用程式保護服務 (選擇性)＞中的指示。 

另請參閱以下的[條件式存取](#conditional-access)需求。


#### <a name="3-app-integrates-adal-but-does-not-support-brokered-authenticationdevice-wide-sso"></a>3.應用程式會整合 ADAL，但不支援代理驗證/全裝置 SSO

|必要的 ADAL 參數| 值 |
|--|--|
| ClientID | 應用程式的 ClientID (由 Azure AD 於應用程式註冊時產生) |
| SkipBroker | **True** |

可以視需要指定 Authority 和 NonBrokerRedirectURI。

### <a name="conditional-access"></a>條件式存取

條件式存取 (CA) 是 Azure Active Directory [功能](https://docs.microsoft.com/azure/active-directory/develop/active-directory-conditional-access-developer)，可用來控制 AAD 資源的存取權。 [Intune 系統管理員可以定義 CA 規則](https://docs.microsoft.com/intune/conditional-access)，允許只能從由 Intune 管理的裝置或應用程式存取資源。 為確保您的應用程式能夠在適當時存取資源，必須遵循下列步驟。 如果您的應用程式不會取得任何 AAD 存取權杖，或是只會存取無法受 CA 保護的資源，您可以略過這些步驟。

1. 請遵循 [ADAL 整合指導方針](https://github.com/AzureAD/azure-activedirectory-library-for-android#how-to-use-this-library)。 
   請特別參閱訊息代理程式使用方式的步驟 11。
2. [向 Azure Active Directory 註冊應用程式](https://docs.microsoft.com/azure/active-directory/active-directory-app-registration) 。 
   重新導向 URI 位於上述的 ADAL 整合指導方針。
3. 設定每個[常見 ADAL 設定](#common-adal-configurations)的資訊清單中繼資料參數，上面的項目 2。
4. 藉由從 [Azure 入口網站](https://portal.azure.com/#blade/Microsoft_Intune_DeviceSettings/ExchangeConnectorMenu/aad/connectorType/2)啟用[以裝置為基礎的 CA](https://docs.microsoft.com/intune/conditional-access-intune-common-ways-use)並確認下列各項，測試所有項目都已正確設定
    - 登入您的應用程式會提示進行安裝和註冊 Intune 公司入口網站
    - 註冊之後，登入應用程式能順利完成。
5. 一旦您的應用程式已送出 Intune APP SDK 整合，請連絡 msintuneappsdk@microsoft.com，以新增至已核准應用程式清單，進行[以應用程式為基礎的條件式存取](https://docs.microsoft.com/intune/conditional-access-intune-common-ways-use#app-based-conditional-access)
6. 一旦您的應用程式新增至核准清單，請藉由[設定應用程式為基礎的 CA](https://docs.microsoft.com/intune/app-based-conditional-access-intune-create)，並確保登入應用程式能順利完成，來進行驗證。

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

1. 應用程式「必須」  實作並註冊 `MAMServiceAuthenticationCallback` 介面的執行個體。 回呼執行個體必須盡早於應用程式的生命週期內進行註冊 (通常是在應用程式類別的 `onMAMCreate()` 方法中)。

2. 在建立使用者帳戶，且使用者成功以 ADAL 登入之後，應用程式「必須」  呼叫 `registerAccountForMAM()`。

3. 當使用者帳戶被移除之後，應用程式應該呼叫 `unregisterAccountForMAM()` 以將該帳戶從 Intune 管理中移除。

    > [!NOTE]
    > 如果使用者暫時登出應用程式，應用程式並不需要呼叫 `unregisterAccountForMAM()`。 呼叫可以初始化抹除，以完全移除該使用者的公司資料。


### <a name="mamenrollmentmanager"></a>MAMEnrollmentManager

所有必要的驗證和註冊 API 都可以在 `MAMEnrollmentManager` 介面中找到。 針對 `MAMEnrollmentManager` 的參考可以透過下列方式取得：

```java
MAMEnrollmentManager mgr = MAMComponents.get(MAMEnrollmentManager.class);

// make use of mgr
```

傳回的 `MAMEnrollmentManager` 執行個體將保證不會為 null。 API 方法會落入兩個類別：「驗證」  和「帳戶註冊」  。

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
    void registerAccountForMAM(String upn, String aadId, String tenantId, String authority);
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

1. 應用程式必須實作 `MAMServiceAuthenticationCallback` 介面，以允許 SDK 針對指定使用者和資源識別碼要求 ADAL 權杖。 回呼執行個體必須提供給 `MAMEnrollmentManager`，方法是呼叫其 `registerAuthenticationCallback()` 方法。 在應用程式生命週期的初期階段可能會需要權杖，以進行註冊重試或應用程式保護原則重新整理簽入，因此註冊回呼的理想位置是在應用程式 `MAMApplication` 子類別的 `onMAMCreate()` 方法中。

2. `acquireToken()` 方法應該會取得針對指定使用者所要求之資源識別碼的存取權杖。 如果它無法取得要求的權杖，便應該會傳回 null。

    > [!NOTE]
    > 請確認您的應用程式利用傳遞至 `acquireToken()` 的 `resourceId` 和 `aadId` 參數，以取得正確的權杖。

    ```java
    class MAMAuthCallback implements MAMServiceAuthenticationCallback {
        public String acquireToken(String upn, String aadId, String resourceId) {
            return mAuthContext.acquireTokenSilentSync(resourceId, ClientID, aadId).getAccessToken();
        }
    }
    ```

3. 在應用程式無法於 SDK 呼叫 `acquireToken()` 時提供權杖的情況下 (例如，如果無訊息驗證失敗，且當時並不方便顯示 UI)，該應用程式可以透過呼叫 `updateToken()` 方法來在稍後提供權杖。 由先前針對 `acquireToken()` 的呼叫所要求的 UPN、AAD 識別碼及資源識別碼，必須連同最終取得的權杖一起傳遞至 `updateToken()`。 應用程式應該在從所提供的回呼傳回 null 之後盡快呼叫此方法。

    > [!NOTE]
    > SDK 將會定期呼叫 `acquireToken()` 以取得權杖，因此並不一定需要呼叫 `updateToken()`。 不過，我們強烈建議您這麼做，因為這可以協助註冊和應用程式保護原則簽入及時完成。


### <a name="account-registration"></a>帳戶註冊

本節會描述 `MAMEnrollmentManager` 中的帳戶註冊 API 方法，以及使用它們的方式。

```java
void registerAccountForMAM(String upn, String aadId, String tenantId);
void registerAccountForMAM(String upn, String aadId, String tenantId, String authority);
void unregisterAccountForMAM(String upn);
Result getRegisteredAccountStatus(String upn);
```

1. 若要註冊帳戶以進行管理，應用程式應呼叫 `registerAccountForMAM()`。 識別使用者帳戶的方式，是透過其 UPN 和 AAD 使用者識別碼。 同時也需要租用戶識別碼，以關聯註冊資料與使用者的 AAD 租用戶。 也可以提供使用者的授權單位以允許針對特定主權雲端進行註冊；如需詳細資訊，請參閱[主權雲端註冊](#sovereign-cloud-registration)。  SDK 可能會嘗試在 MAM 服務中針對指定使用者註冊應用程式。若註冊失敗，它將會定期重試註冊，直到該帳戶已取消註冊為止。 重試的間隔通常是 12-24 小時。 SDK 會透過通知以非同步的方式提供註冊嘗試的狀態。

2. 由於需要 AAD 驗證，登錄使用者帳戶的最佳時間是在使用者登入應用程式，並成功使用 ADAL 進行驗證之後。使用者的 AAD 識別碼和租用戶識別碼會從 ADAL 驗證呼叫，作為 [`AuthenticationResult`](https://github.com/AzureAD/azure-activedirectory-library-for-android) 物件的一部分傳回。
    * 租用戶識別碼是來自 `AuthenticationResult.getTenantID()` 方法。
    * 有關使用者的資訊是位於來自 `AuthenticationResult.getUserInfo()` 之 `UserInfo` 類型的子物件中，而 AAD 使用者識別碼則是透過呼叫 `UserInfo.getUserId()` 以從該物件中擷取。

3. 若要從 Intune 管理取消註冊某個帳戶，應用程式應呼叫 `unregisterAccountForMAM()`。 若該帳戶已成功註冊並受到管理，SDK 將會取消註冊該帳戶並抹除其資料。 該帳戶的定期註冊重試將會停止。 SDK 會透過通知以非同步方式提供取消註冊要求的狀態。

### <a name="sovereign-cloud-registration"></a>主權雲端註冊

[感知主權雲端](https://www.microsoft.com/trustcenter/cloudservices/nationalcloud)的應用程式**必須**提供 `authority` 給 `registerAccountForMAM()`。  這可以藉由 ADAL 的 [1.14.0+](https://github.com/AzureAD/azure-activedirectory-library-for-android/releases/tag/v1.14.0) acquireToken extraQueryParameters 所提供 `instance_aware=true`，後面接著對 AuthenticationCallback AuthenticationResult 叫用 `getAuthority()` 而取得。

```java
mAuthContext.acquireToken(this, RESOURCE_ID, CLIENT_ID, REDIRECT_URI, PromptBehavior.FORCE_PROMPT, "instance_aware=true",
        new AuthenticationCallback<AuthenticationResult>() {
            @Override
            public void onError(final Exception exc) {
                // authentication failed
            }

            @Override
            public void onSuccess(final AuthenticationResult result) {
                mAuthority = result.getAuthority();
                // handle other parts of the result
            }
        });
```

> [!NOTE]
> 請不要在 AndroidManifest.xml 中設定 `com.microsoft.intune.mam.aad.Authority` 中繼資料項目。

> [!NOTE]
> 請確定已在您的 `MAMServiceAuthenticationCallback::acquireToken()` 方法中正確設定授權。

#### <a name="currently-supported-sovereign-clouds"></a>目前支援的主權雲端

1. Arlington

### <a name="important-implementation-notes"></a>重要實作附註

#### <a name="authentication"></a>驗證

* 當應用程式呼叫 `registerAccountForMAM()` 時，它可能會在不久之後於其 `MAMServiceAuthenticationCallback` 介面上接收到不同執行緒的回呼。 在理想的情況下，應用程式已在註冊帳戶前從 ADAL 取得自己的權杖，以加快取得所要求權杖的速度。 如果應用程式從回呼傳回有效權杖，則註冊將會繼續，且應用程式將會透過通知取得最終結果。

* 如果應用程式沒有傳回有效的 AAD 權杖，來自註冊嘗試的最終結果將會是 `AUTHENTICATION_NEEDED`。 若應用程式透過通知接受到此結果，我們強烈建議透過取得使用者的權杖及先前從 `acquireToken()` 要求的資源，並呼叫 `updateToken()` 方法再次啟動註冊流程來加快註冊的流程。

* 因此也會呼叫應用程式的已註冊 `MAMServiceAuthenticationCallback`，以取得定期應用程式保護原則重新整理簽入的權杖。如果應用程式無法在要求時提供權杖，便不會收到通知，不過它應該於下一個適當的時機嘗試取得權杖並呼叫 `updateToken()`，以加速簽入程序。 如果不提供權杖，在下一個簽入嘗試時仍然會呼叫回呼。

* 支援主權雲端需要提供授權單位。

#### <a name="registration"></a>註冊

* 為了方便起見，註冊方法將會是等冪，例如 `registerAccountForMAM()` 只會在帳戶尚未註冊的情況下註冊該帳戶並嘗試註冊應用程式，而 `unregisterAccountForMAM()` 只會在帳戶已註冊的情況下將帳戶取消註冊。 後續的呼叫將不會運作，因此多次呼叫這些方法並不會有壞處。 此外，系統並無法保證針對這些方法的呼叫及結果通知之間的對應，也就是說，若針對已註冊的身分識別呼叫 `registerAccountForMAM`，便可能不會針對該身分識別再次傳送通知。 已傳送的通知有可能不會與針對這些方法的任何呼叫對應，因為 SDK 可能會定期嘗試在背景進行註冊，且從 Intune 服務接收的抹除要求可能會觸發取消註冊。

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

此方法會在 SDK 顯示其預設封鎖 UI 之前呼叫。 如果應用程式變更活動身分識別，或是將嘗試註冊的使用者取消註冊，SDK 將不會封鎖該活動。 在此情況下，應用程式必須負責避免洩漏公司資料。 只有多重身分識別應用程式 (稍後討論) 能變更活動身分識別。

如果您不要明確繼承 `MAMActivity` (因為建置工具會進行該項變更)，但仍然需要處理此通知，您可以改為實作 `MAMActivityBlockingListener`。

### <a name="notifications"></a>通知

若應用程式為 **MAM_ENROLLMENT_RESULT** 類型的通知進行登錄，則會傳送 `MAMEnrollmentNotification` 來通知應用程式已完成註冊要求。 將會透過 `MAMNotificationReceiver` 介面接收 `MAMEnrollmentNotification`，如[從 SDK 註冊通知](#register-for-notifications-from-the-sdk)一節中所述。

```java
public interface MAMEnrollmentNotification extends MAMUserNotification {
    MAMEnrollmentManager.Result getEnrollmentResult();
}
```

`getEnrollmentResult()` 方法會傳回註冊要求的結果。  由於 `MAMEnrollmentNotification` 會延伸 `MAMUserNotification`，因此也會提供嘗試註冊的使用者身分識別。 應用程式必須實作 `MAMNotificationReceiver` 介面以接收這些通知，這已在[從 SDK 註冊通知](#register-for-notifications-from-the-sdk)一節中詳述。

已註冊使用者帳戶的狀態在接收註冊通知時可能會變更，但並非在所有情況下都會變更 (例如，若在接收如 `WRONG_USER` 等較具資訊性的結果之後才接收到 `AUTHORIZATION_NEEDED` 通知，則系統將會維持使用較具資訊性的結果作為帳戶狀態)。  成功註冊帳戶後，狀態會維持在 `ENROLLMENT_SUCCEEDED`，直到帳戶取消註冊或遭到抹除。

已註冊使用者帳戶的狀態在接收註冊通知時可能會變更，但並非在所有情況下都會變更 (例如，若在接收如 `WRONG_USER` 等較具資訊性的結果之後才接收到 `AUTHORIZATION_NEEDED` 通知，則系統將會維持使用較具資訊性的結果作為帳戶狀態)。  成功註冊帳戶後，狀態會維持在 `ENROLLMENT_SUCCEEDED`，直到帳戶取消註冊或遭到抹除。

## <a name="app-ca-with-policy-assurance"></a>具備原則保證的 APP CA

### <a name="overview"></a>概觀
透過具備原則保證的 APP CA (條件式存取)，Intune 應用程式防護原則應用程式上的資源存取便會條件化。  AAD 會藉由要求應用程式先進行註冊並由 APP 管理，才授與存取由具備原則保證 APP CA 保護資源的權杖，來強制執行。  應用程式必須使用 ADAL 代理程式來取得權杖，且其設定過程與[條件式存取](#conditional-access)中描述的相同

### <a name="adal-changes"></a>ADAL 變更
ADAL 程式庫擁有新的錯誤碼，可通知應用程式取得權杖失敗原因是不符合 APP 管理的合規性。  若應用程式收到此錯誤碼，便需要呼叫 SDK 以透過註冊應用程式和套用原則來嘗試補救合規性。 ADAL `AuthenticationCallback` 的 `onError()` 方法會收到例外狀況，且會包含錯誤碼 `ADALError.AUTH_FAILED_INTUNE_POLICY_REQUIRED`。  在此情況下，例外狀況可轉換成 `IntuneAppProtectionPolicyRequiredException`，並可從中擷取額外的參數，以在補救合規性中使用 (請參閱以下的程式碼範例)。 補救成功後，應用程式便可再次嘗試透過 ADAL 取得權杖。

> [!NOTE]
> 這個新錯誤碼及其他具備原則保證 APP CA 之支援需要使用版本 1.15.0 (或更新版本) 的 ADAL 程式庫。

### <a name="mamcompliancemanager"></a>MAMComplianceManager

`MAMComplianceManager` 介面會在從 ADAL 接收到需要原則的錯誤時使用。  它包含嘗試將應用程式置入符合規範狀態時應呼叫的 `remediateCompliance()` 方法。 針對 `MAMComplianceManager` 的參考可以透過下列方式取得：

```java
MAMComplianceManager mgr = MAMComponents.get(MAMComplianceManager.class);

// make use of mgr
```

傳回的 `MAMComplianceManager` 執行個體將保證不會為 null。

```java
package com.microsoft.intune.mam.policy;

public interface MAMComplianceManager {
    void remediateCompliance(String upn, String aadId, String tenantId, String authority, boolean showUX);
}
```

會呼叫 `remediateCompliance()` 方法以嘗試使應用程式受到管理來滿足 AAD 授與所要求權杖的條件。  前四個參數可從 ADAL `AuthenticationCallback.onError()` 方法接收到的例外狀況中擷取 (請參閱以下的程式碼範例)。  最後一個參數是布林值，控制是否要在合規性嘗試期間顯示 UX。  此為簡易的封鎖進度樣式介面，作為不需要在此作業期間顯示自訂 UX 應用程式的預設介面。  它只會在合規性補救正在進行時進行封鎖，且不會顯示最終結果。  應用程式應登錄通知接收器來處理合規性補救嘗試的成功或失敗結果 (如下所示)。

`remediateCompliance()` 方法可進行 MAM 註冊，作為建立合規性的一部分。  若應用程式已針對註冊通知登錄通知接收器，便可能會收到註冊通知。  應用程式登錄的 `MAMServiceAuthenticationCallback` 會呼叫其 `acquireToken()` 方法，來取得 MAM 註冊的權杖。 `acquireToken()` 會在應用程式取得其自身權杖前呼叫，讓應用程式在成功取得權杖後執行的任何記錄或建立帳戶工作都還不會先行執行。  回撥必須要能夠在此情況下取得權杖。  若您無法從 `acquireToken()` 傳回權杖，則合規性補救嘗試將會失敗。  若您稍後針對所要求資源，使用有效的權杖呼叫 `updateToken()`，則合規性補救將會立即使用指定的權杖重試。

> [!NOTE]
> 您仍可以在 `acquireToken()` 中以無訊息的方式取得權杖，因為使用者屆時已會受到指引，在接收到 `ADALError.AUTH_FAILED_INTUNE_POLICY_REQUIRED` 錯誤前安裝代理程式及登錄裝置。  這會使代理程式在其快取中具備有效的重新整理權杖，允許在無訊息的情況下成功取得所要求權杖。

以下是在 `AuthenticationCallback.onError()` 方法中接收到需要原則錯誤，以及呼叫 `MAMComplianceManager` 來處理錯誤的範例。

```java
public void onError(@Nullable Exception exc) {
    if (exc instanceof AuthenticationException && 
        ((AuthenticationException) exc).getCode() == ADALError.AUTH_FAILED_INTUNE_POLICY_REQUIRED) {

        final IntuneAppProtectionPolicyRequiredException policyRequiredException = 
            (IntuneAppProtectionPolicyRequiredException) ex;

        final String upn = policyRequiredException.getAccountUpn();
        final String aadId = policyRequiredException.getAccountUserId();
        final String tenantId = policyRequiredException.getTenantId();
        final String authority = policyRequiredException.getAuthorityURL();

        MAMComplianceManager complianceManager = MAMComponents.get(MAMComplianceManager.class);
        complianceManager.remediateCompliance(upn, aadId, tenantId, authority, showUX);
    }
}
```

### <a name="status-notifications"></a>狀態通知

若應用程式為 **COMPLIANCE_STATUS** 類型的通知進行登錄，則會傳送 `MAMComplianceNotification` 來通知應用程式合規性補救嘗試的最終狀態。 將會透過 `MAMNotificationReceiver` 介面接收 `MAMComplianceNotification`，如[從 SDK 註冊通知](#register-for-notifications-from-the-sdk)一節中所述。

```java
public interface MAMComplianceNotification extends MAMUserNotification {
    MAMCAComplianceStatus getComplianceStatus();
    String getComplianceErrorTitle();
    String getComplianceErrorMessage();
}
```

`getComplianceStatus()` 方法會將合規性補救嘗試的結果，作為 `MAMCAComplianceStatus` 列舉的其中一個值傳回。

|狀態碼 | 說明 |
| -- | -- |
| UNKNOWN | 狀態未知。 這可能表示失敗的原因為非預期原因。 您可以在公司入口網站記錄中找到額外資訊。 |
| COMPLIANT | 合規性補救已成功，且應用程式現在已符合原則的規範。 應重試取得 ADAL 權杖。 |
| NOT_COMPLIANT | 補救合規性的嘗試失敗。  應用程式不符合規範，且在直到修正錯誤條件前不應重試取得 ADAL 權杖。  額外的錯誤資訊會與 MAMComplianceNotification 一同傳送。 |
| SERVICE_FAILURE | 嘗試從 Intune 服務擷取合規性資料時失敗。 您可以在公司入口網站記錄中找到額外資訊。 |
| NETWORK_FAILURE | 連線到 Intune 服務時發生錯誤。 應用程式應在還原網路連線時再次嘗試取得權杖。 |
| CLIENT_ERROR | 嘗試補救合規性時由於用戶端的原因而失敗。  例如沒有權杖或使用者錯誤。 額外的錯誤資訊會與 MAMComplianceNotification 一同傳送。 |
| PENDING | 嘗試補救合規性失敗，因為在超過時間限制時仍未從服務接收到狀態回應。 應用程式應在稍後再次嘗試取得權杖。 |
| COMPANY_PORTAL_REQUIRED | 必須在裝置上安裝公司入口網站，才能使合規性補救成功。  若已在裝置上安裝公司入口網站，應用程式需要重新啟動。  在此情況下，會顯示對話方塊，要求使用者重新啟動應用程式。 |

若合規性狀態為 `MAMCAComplianceStatus.COMPLIANT`，應用程式應重新啟動原先取得權杖的過程 (適用其自身的資源)。 若合規性補救嘗試失敗，`getComplianceErrorTitle()` 和 `getComplianceErrorMessage()` 方法會傳回應用程式可向終端使用者顯示的當地語系化字串 (若其選擇的話)。  大多數的錯誤案例都無法由應用程式進行補救，因此一般情況下，使建立帳戶或登入的過程失敗，並允許使用者稍後再次進行嘗試可能會是最佳的做法。  若失敗持續發生，MAM 記錄可能可以協助判斷原因。  終端使用者可使用[此處](https://docs.microsoft.com/intune-user-help/send-logs-to-your-it-admin-by-email-android "透過電子郵件將記錄寄給您的公司支援人員")提供的指示來提交記錄。

由於 `MAMComplianceNotification` 會延伸 `MAMUserNotification`，因此也會提供嘗試補救的使用者身分識別。

以下是使用匿名類別實作 MAMNotificationReceiver 介面來登錄接受器的範例：

```java
final MAMNotificationReceiverRegistry notificationRegistry = MAMComponents.get(MAMNotificationReceiverRegistry.class);
// create a receiver
final MAMNotificationReceiver receiver = new MAMNotificationReceiver() {
    public boolean onReceive(MAMNotification notification) {
        if (notification.getType() == MAMNotificationType.COMPLIANCE_STATUS) {
            MAMComplianceNotification complianceNotification = (MAMComplianceNotification) notification;
            
            // take appropriate action based on complianceNotification.getComplianceStatus()
            
            // unregister this receiver if no longer needed
            notificationRegistry.unregisterReceiver(this, MAMNotificationType.COMPLIANCE_STATUS);
        }
        return true;
    }
};
// register the receiver
notificationRegistry.registerReceiver(receiver, MAMNotificationType.COMPLIANCE_STATUS);
```

> [!NOTE]
> 通知接收器必須在呼叫 `remediateCompliance()` 前進行登錄，避免可能導致遺漏通知的競爭條件。

### <a name="implementation-notes"></a>實作附註

> [!NOTE]
> 應用程式的 `MAMServiceAuthenticationCallback.acquireToken()` 方法必須針對新的 `forceRefresh` 旗標，將 *true* 傳遞給 `acquireTokenSilentSync()` 來強制從代理程式進行重新整理。  這是為了因應 ADAL 中可能影響 MAM 服務權杖的權杖快取問題。 一般而言，其看起來會與以下內容相似：
>
> ```java
> AuthenticationResult result = acquireTokenSilentSync(resourceId, clientId, userId, /* forceRefresh */ true);
> ```

> [!NOTE]
> 若您想要在補救嘗試期間顯示自訂封鎖 UX，您應針對 showUX 參數，將 *false* 傳遞至 `remediateCompliance()`。 您必須確認您會先行顯示 UX 及登錄您的通知接聽程式，再呼叫 `remediateCompliance()`。  這可避免發生競爭條件，在 `remediateCompliance()` 很快失敗的情況下遺漏通知。  例如，Activity 子類別之 `onCreate()` 或 `onMAMCreate()` 方法便是登錄通知接聽程式及呼叫 `remediateCompliance()` 的理想位置。  `remediateCompliance()` 的參數可傳遞至 UX，作為意圖的額外項目。  接收到合規性狀態通知時，您可以顯示結果或直接完成活動。

> [!NOTE]
> `remediateCompliance()` 會登錄帳戶並嘗試註冊。  一旦取得主要權杖後，便不需要呼叫 `registerAccountForMAM()`，但執行此操作也不會造成傷害。 另一方面，若應用程式無法取得權杖並希望移除使用者帳戶，則它必須呼叫 `unregisterAccountForMAM()` 來移除帳戶並避免在背景重試註冊。

## <a name="protecting-backup-data"></a>保護備份資料

截至 Android Marshmallow (API 23) 止，Android 提供兩種可讓應用程式備份資料的方法。 您可在應用程式中使用這些選項，但需要不同的步驟以確保正確實作 Intune 資料保護。 您可以檢閱下表，以了解正確資料保護行為所需的相對應動作。  您可以在 [Android API 指南](https://developer.android.com/guide/topics/data/backup.html)中深入了解備份方法。

### <a name="auto-backup-for-apps"></a>應用程式的自動備份

Android 開始針對 Android Marshmallow 裝置上的應用程式提供 Google 雲端硬碟的[自動完整備份 (英文)](https://developer.android.com/guide/topics/data/autobackup.html)，不論應用程式的目標 API 為何。 在您的 AndroidManifest.xml 中，如果您將 `android:allowBackup` 明確設定為 **false**，則 Android 永遠不會將您的應用程式排入佇列進行備份，而且「公司」資料會保留在應用程式內。 在這種情況下，並不需要採取任何進一步的動作。

不過，`android:allowBackup` 屬性預設會設定為 true，即使未在資訊清單檔中指定 `android:allowBackup` 亦然。 這表示所有應用程式資料都會自動備份至使用者的 Google 雲端硬碟帳戶，此預設行為會造成**資料洩漏的風險**。 因此，SDK 需進行下列所述的變更，以確保套用資料保護。  如果您想要讓應用程式在 Android Marshmallow 裝置上執行，請務必遵循下列方針，以妥善保護客戶資料。  

Intune 可讓您利用 Android 中可用的所有[自動備份功能](https://developer.android.com/guide/topics/data/autobackup.html)，包括在 XML 中定義自訂規則的功能，但您必須遵循下列步驟來保護資料：

1. 如果您的應用程式「不會」  使用自己的自訂 BackupAgent，請使用預設 MAMBackupAgent 以允許進行符合 Intune 原則的自動完整備份。 請將下列內容置於應用程式資訊清單中：

    ```xml
    android:fullBackupOnly="true"
    android:backupAgent="com.microsoft.intune.mam.client.app.backup.MAMDefaultBackupAgent"
    ```


2. **[選擇性]** 如果您實作選擇性的自訂 BackupAgent，則必須使用 MAMBackupAgent 或 MAMBackupAgentHelper。 請參閱下列各節。 請考慮改用 Intune 的 **MAMDefaultFullBackupAgent** (已於步驟 1 中詳述)，它能針對 Android M 及更新版本提供簡易的備份功能。

3. 當您決定應用程式應該接收的完整備份類型 (未篩選、已篩選或無) 時，您必須將將屬性 `android:fullBackupContent` 設定為 true、false，或您應用程式中的 XML 資源。

4. 接著，您「必須」 __ 將放入 `android:fullBackupContent` 的任何內容，複製到資訊清單中名為 `com.microsoft.intune.mam.FullBackupContent` 的 Metadata 標記中。

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

1. 仔細閱讀[索引鍵/值備份](https://developer.android.com/guide/topics/data/keyvaluebackup.html) \(英文\) 的 Android 指南，特別是[擴充 BackupAgent](https://developer.android.com/guide/topics/data/keyvaluebackup.html#BackupAgent) \(英文\)，以確保您的 BackupAgent 實作能遵循 Android 指導方針。

2. 使您的類別擴充 `MAMBackupAgent`。

**多重身分識別備份：**

1. 在開始備份之前，請確定您計畫備份的檔案或資料緩衝區已確實「由 IT 系統管理員允許在多重身分識別的案例下進行備份」  。 我們在 `MAMFileProtectionManager` 和 `MAMDataProtectionManager` 中提供 `isBackupAllowed` 函式以供您進行判斷。 如果檔案或資料緩衝區不能備份，您就不應該繼續將它包含在備份中。

2. 在備份期間，如果想要備份在步驟 1 中檢查過的檔案識別，就必須使用您打算從其中擷取資料的檔案來呼叫 `backupMAMFileIdentity(BackupDataOutput data, File … files)`。 這會自動建立新的備份實體，並將其寫入 `BackupDataOutput` 。 在還原時會自動使用這些實體。

**多重身分識別還原：**

《資料備份》指南在[擴充 BackupAgent (英文)](https://developer.android.com/guide/topics/data/keyvaluebackup.html#BackupAgent) 一節中詳述還原應用程式資料的一般演算法，並提供程式碼範例。 若要成功進行多重身分識別還原，您必須遵循此程式碼範例中所提供的一般結構，並特別注意下列事項：

1. 您必須利用 `while(data.readNextHeader())`* 迴圈以完整瀏覽備份實體。

2. 若 `data.getKey()`* 不符合您於 `onBackup` 中所撰寫的索引鍵，您必須呼叫 `data.skipEntityData()`*。 若沒有執行此步驟，您的還原可能會失敗。

3. 避免在 `while(data.readNextHeader())`* 建構中取用備份實體時進行傳回，因為這會遺失自動寫入的實體。

* 其中，`data` 是在還原時傳遞至您應用程式的 **MAMBackupDataInput** 區域變數名稱。

## <a name="multi-identity-optional"></a>多重身分識別 (選擇性)

### <a name="overview"></a>概觀
Intune App SDK 預設會將原則套用至應用程式整體。 多重身分識別為選擇性的 Intune 應用程式保護功能，可以啟用以允許將原則套用至每個身分識別。 這需要的應用程式參與明顯高於其他應用程式保護功能。

> [!NOTE]
> 缺乏正確的應用程式參與，會導致資料洩漏和其他安全性問題。

使用者註冊裝置或應用程式之後，SDK 會註冊這個身分識別，並將其視為主要的 Intune 受管理身分識別。 應用程式中的其他使用者則會被視為未受管理，並具有不受限制的原則設定。

> [!NOTE]
> 目前，每個裝置上僅支援一個 Intune 受管理身分識別。

身分識別會定義為字串。 身分識別「不區分大小寫」  ，而且針對身分識別對 SDK 所做出的要求，可能不會傳回原本設定身分識別時所使用的相同大小寫。

當應用程式想要變更作用中身分識別時，「必須」  通知 SDK。 有時候，需要身分識別變更時，SDK 也會通知應用程式。 但在大部分情況下，MAM 無法知道哪些資料會於指定的時間顯示在 UI 中或用在執行緒上，依賴應用程式設定正確的身分識別，才能避免資料洩漏。 在接下來的各節中，會呼叫某些需要應用程式動作的特定案例。

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
  2. `Context` (通常為 `Activity`) 層級
  3. 處理程序層級

在執行緒層級設定的身分識別會取代在 `Context` 層級設定的身分識別，進而取代在處理程序層級設定的身分識別。 只有在適當的相關案例中，才會使用 `Context` 上所設定的身分識別。 例如，檔案 IO 操作沒有相關聯的 `Context`。 最常見的情況是，應用程式會在 `Activity` 上設定 `Context` 身分識別。 應用程式「絕」不  顯示受控身分識別的資料，除非 `Activity` 身分識別設定為相同的身分識別。 一般情況下，只有當應用程式在所有執行緒上一次只處理一名使用者時，處理序層級的身分識別才有用。 許多應用程式可能不需要使用它。

若您的應用程式使用 `Application` 內容來取得系統服務，請確認您已設定執行緒或處理序身分識別，或是您已在應用程式的 `Application` 內容上設定 UI 身分識別。

若要在使用 `setUIPolicyIdentity` 或 `switchMAMIdentity` 更新 UI 身分識別處理特殊案例，您可以將一組 `IdentitySwitchOption` 值傳遞給這兩個方法。

* `IGNORE_INTENT`：若要求應忽略與目前活動建立關聯之意圖的身分識別切換，請使用此選項。
  例如：

  1. 應用程式會從包含受控文件的受控識別接收意圖，且您的應用程式會顯示該文件。
  2. 使用者會切換到他們的個人身分識別，因此您的應用程式要求切換 UI 身分識別。 在個人身分識別中，您的應用程式不再顯示文件，因此您可以在要求切換身分識別時使用 `IGNORE_INTENT`。

  若並未進行設定，則 SDK 會假設應用程式中仍在使用最近的意圖。 這會導致新身分識別的接收原則將意圖視為傳入資料處理，並使用其身分識別。

>[!NOTE]
> 因為 `CLIPBOARD_SERVICE` 會用來進行 UI 作業，所以 SDK 會使用前景活動的 UI 身分識別來進行 `ClipboardManager` 作業。
> 您可以使用 `MAMPolicyManager` 中的下列方法來設定身分識別，並擷取之前設定的身分識別值。

```java
  public static void setUIPolicyIdentity(final Context context, final String identity, final MAMSetUIIdentityCallback mamSetUIIdentityCallback);

  public static String getUIPolicyIdentity(final Context context);

  public static MAMIdentitySwitchResult setProcessIdentity(final String identity);

  public static String getProcessIdentity();

  public static MAMIdentitySwitchResult setCurrentThreadIdentity(final String identity);

  public static String getCurrentThreadIdentity();

/**
   * Get the current app policy. This does NOT take the UI (Context) identity into account.
   * If the current operation has any context (e.g. an Activity) associated with it, use the overload below.
   */
  public static AppPolicy getPolicy();

  /**
  * Get the current app policy. This DOES take the UI (Context) identity into account.
   * If the current operation has any context (e.g. an Activity) associated with it, use this function.
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
| NOT_ALLOWED  | 不允許身分識別變更。 在目前執行緒上已設定不同身分識別的情況下，嘗試設定 UI (內容) 身分識別，就會發生此情況。 |
| CANCELLED | 使用者已取消身分識別變更，通常是透過於 PIN 或驗證提示上按下 [返回] 按鈕。 |
| FAILED | 不明原因導致身分識別變更失敗。|

應用程式應先確保身分識別順利切換，再顯示或使用公司資料。 目前，處理序和執行緒身分識別切換在啟用多身分識別的應用程式上一直都很成功，但我們保留新增失敗狀況的權利。 UI 身分識別切換如果與執行緒身分識別發生衝突，或是使用者將條件式啟動需求取消 (例如按下 PIN 畫面的 [上一步] 按鈕)，則 UI 身分識別切換可能會因無效引數而失敗。


如果設定內容身分識別，則會以非同步方式報告結果。 如果內容是活動，在執行條件式啟動之前 (可能需要使用者輸入 PIN 或公司認證)，SDK 將無法得知身分識別變更是否成功。 應用程式必須實作 `MAMSetUIIdentityCallback` 以接收此結果，您可以針對此參數傳遞 null。

```java
    public interface MAMSetUIIdentityCallback {
        void notifyIdentityResult(MAMIdentitySwitchResult identitySwitchResult);
  }
```

您也可以直接透過 `MAMActivity` 中的方法來設定活動的身分識別，而不是呼叫 `MAMPolicyManager.setUIPolicyIdentity`。 請使用下列方法來達成：

```java
     public final void switchMAMIdentity(final String newIdentity, final EnumSet<IdentitySwitchOption> options);
```

您也可以覆寫 `MAMActivity` 中的方法，以使應用程式能收到嘗試變更該活動身分識別的結果通知。

``` java
    public void onSwitchMAMIdentityComplete(final MAMIdentitySwitchResult result);
```

若您沒有覆寫 `onSwitchMAMIdentityComplete` (或呼叫 `super` 方法)，則在活動上切換身分識別失敗會使活動完成。 若您覆寫該方法，您必須注意在切換身分識別失敗後不會顯示公司資料。

>[!NOTE]
> 切換身分識別可能會需要重新建立活動。 在此情況下，`onSwitchMAMIdentityComplete` 回呼會傳遞至活動的新執行個體。


### <a name="implicit-identity-changes"></a>隱含身分識別變更

除了應用程式設定身分識別的能力之外，執行緒或內容的身分識別也可能會根據來自另一個具有應用程式保護原則的 Intune 受控應用程式的資料輸入而變更。

#### <a name="examples"></a>範例

1. 如果活動是根據另一個 MAM 應用程式所傳送的 `Intent` 來啟動，就會根據另一個應用程式在傳送 `Intent` 時的有效身分識別，來設定活動的身分識別。

2. 針對服務，執行緒的身分識別會在 `onStart` 或 `onBind` 呼叫期間以類似的方式進行設定。 針對從 `onBind` 傳回之 `Binder` 的呼叫，也會暫時設定執行緒身分識別。

3. 呼叫 `ContentProvider` 同樣會在該期間設定執行緒身分識別。


    此外，使用者與活動互動可能會導致隱含身分識別切換。

    **範例：** 使用者在 `Resume` 期間取消授權提示，將會導致隱含切換至空的身分識別。

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

      其中 ```AppIdentitySwitchResult``` 是 `SUCCESS` 或 `FAILURE`。

針對所有隱含身分識別變更會呼叫 `onMAMIdentitySwitchRequired` 方法 (透過從 `MAMService.onMAMBind` 傳回的 Binder 進行的變更除外)。 `onMAMIdentitySwitchRequired` 的預設實作會立即呼叫：

* 當原因為 `reportIdentitySwitchResult(FAILURE)` 時，則為 `RESUME_CANCELLED`。

* `reportIdentitySwitchResult(SUCCESS)` (針對所有其他情況)。

  大多數應用程式應該不會需要透過不同方式來封鎖或延遲身分識別切換，但如果應用程式需要這樣做，則必須考慮下列重點：

  * 如果身分識別切換遭到封鎖，則結果與 `Receive` 共用設定禁止資料輸入相同。

  * 如果服務正在主執行緒上執行，則「必須」  同步呼叫 `reportIdentitySwitchResult`，否則 UI 執行緒將會停止回應。

  * 若要建立 **`Activity`** ，在 `onMAMCreate` 之前會呼叫 `onMAMIdentitySwitchRequired`。 如果應用程式必須顯示 UI，以判斷是否允許身分識別切換，則必須使用「不同」  的活動顯示該 UI。

  * 在 **`Activity`** 中，如果以相當於 `RESUME_CANCELLED` 的原因要求切換至空的身分識別，則應用程式必須修改繼續的活動，以顯示與該身分識別切換一致的資料。  如果不可行，應用程式應該拒絕切換，並會再次要求使用者符合恢復之身分識別的原則 (例如，藉由顯示應用程式 PIN 輸入畫面)。

    > [!NOTE]
    > 多重身分識別應用程式永遠會從受管理和未受管理的應用程式接收內送資料。 應用程式會負責以受管理的方式來處理受管理身分識別中的資料。

  如果要求的身分識別是受管理的 (可使用 `MAMPolicyManager.getIsIdentityManaged` 檢查)，但應用程式無法使用該帳戶 (例如電子郵件帳戶，因為必須先在應用程式中設定該帳戶)，則應該拒絕身分識別切換。

#### <a name="build-plugin--tool-considerations"></a>建置外掛程式/工具的考量
如果您不要明確繼承 `MAMActivity`、`MAMService` 或 `MAMContentProvider` (因為您允許建置工具進行該項變更)，但仍需要處理身分識別切換，您可以改為實作 `MAMActivityIdentityRequirementListener` (適用於 `Activity`) 或 `MAMIdentityRequirementListener` (適用於 `Service` 或 `ContentProviders`)。
您可以藉由呼叫 `MAMActivity.defaultOnMAMIdentitySwitchRequired(activity, identity,
reason, callback)` 靜態方法來存取 `MAMActivity.onMAMIdentitySwitchRequired` 的預設行為。

同樣地，如果您需要覆寫 `MAMActivity.onSwitchMAMIdentityComplete`，您可以實作 `MAMActivityIdentitySwitchListener` 而不明確繼承 `MAMActivity`。

### <a name="preserving-identity-in-async-operations"></a>保留非同步作業中的身分識別
UI 執行緒上的作業通常會將背景工作分派至另一個執行緒。 多重身分識別應用程式會想要確保這些背景工作都以適當的身分識別操作，而這通常是分派它們的活動所使用的相同身分識別。 為方便起見，MAM SDK 提供 `MAMAsyncTask` 和 `MAMIdentityExecutors` 協助保留身分識別。
若非同步作業可能會將公司資料寫入檔案，或是可能會和其他應用程式通訊，則必須使用這些項目。

#### <a name="mamasynctask"></a>MAMAsyncTask

若要使用 `MAMAsyncTask`，只要從其繼承即可，而不用繼承 `AsyncTask`；並分別以 `doInBackgroundMAM` 和 `onPreExecuteMAM` 取代 `doInBackground` 和 `onPreExecute` 的覆寫。 `MAMAsyncTask` 建構函式接受活動內容。 例如：

```java
  AsyncTask<Object, Object, Object> task = new MAMAsyncTask<Object, Object, Object>(thisActivity) {

    @Override
    protected Object doInBackgroundMAM(final Object[] params) {
        // Do operations.
    }

    @Override
    protected void onPreExecuteMAM() {
        // Do setup.
    };
```

### <a name="mamidentityexecutors"></a>MAMIdentityExecutors
`MAMIdentityExecutors` 可讓您以 `wrapExecutor` 和 `wrapExecutorService` 方法，將現有的 `Executor` 或 `ExecutorService` 執行個體包裝為保留身分識別的 `Executor`/`ExecutorService`。 例如

```java
  Executor wrappedExecutor = MAMIdentityExecutors.wrapExecutor(originalExecutor, activity);
  ExecutorService wrappedService = MAMIdentityExecutors.wrapExecutorService(originalExecutorService, activity);
```

### <a name="file-protection"></a>檔案保護

每個檔案都有建立時根據執行緒和處理程序身分識別而來的相關聯身分識別。 此身分識別將會用於檔案加密和選擇性抹除。 只有其身分識別為受管理且具有需要加密之原則的檔案才會進行加密。 SDK 的預設選擇性功能抹除，只會抹除與已要求抹除之受管理身分識別相關聯的檔案。 應用程式可使用 `MAMFileProtectionManager` 類別來查詢或變更檔案的身分識別。

```java
public final class MAMFileProtectionManager {

   /**
    * Protect a file or directory. This will synchronously trigger whatever protection is required for the file, and will tag the
    * file for future protection changes. If an identity is set on a directory, it is set recursively on all files and
    * subdirectories. New files or directories will inherit their parent directory's identity. If MAM is operating in offline mode,
    * this method will silently do nothing.
    *
    * @param identity
    *        Identity to set.
    * @param file
    *        File to protect.
    *
    * @throws IOException
    *         If the file cannot be protected.
    */
   public static void protect(final File file, final String identity) throws IOException;

   /**
     * Protect a file obtained from a content provider. This is intended to be used for
     * sdcard (whether internal or removable) files accessed through the Storage Access Framework.
     * It may also be used with descriptors referring to private files owned by this app.
     * It is not intended to be used for files owned by other apps and such usage will fail. If
     * creating a new file via a content provider exposed by another MAM-integrated app, the new
     * file identity will automatically be set correctly if the ContentResolver in use was
     * obtained via a Context with an identity or if the thread identity is set.
     *
     * This will synchronously trigger whatever protection is required for the file, and will tag
     * the file for future protection changes. If an identity is set on a directory, it is set
     * recursively on all files and subdirectories. If MAM is operating in offline mode, this
     * method will silently do nothing.
     *
     * @param identity
     *            Identity to set.
     * @param file
     *            File to protect.
     *
     * @throws IOException
     *             If the file cannot be protected.
     */
    public static void protect(final ParcelFileDescriptor file, final String identity) throws IOException;

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
    *            File or directory to get information on.
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

#### <a name="app-responsibility"></a>應用程式責任
MAM 無法自動推斷在 `Activity` 中被讀取的檔案和顯示的資料之間的關聯性。 應用程式「必須」  先適當地設定 UI 身分識別，才能顯示公司資料。 這包括從檔案讀取的資料。 如果檔案來自應用程式之外 (來自 `ContentProvider` 或讀取自公開寫入位置)，應用程式「必須」  嘗試先判斷檔案身分識別 (使用 `MAMFileProtectionManager.getProtectionInfo`) 才能顯示從檔案讀取的資訊。 如果 `getProtectionInfo` 回報非 null、非空白的身分識別，則 UI 身分識別「必須」  設定成符合此身分識別 (使用 `MAMActivity.switchMAMIdentity` 或 `MAMPolicyManager.setUIPolicyIdentity`)。 如果身分識別切換失敗，「絕無法」  顯示檔案中的資料。

範例流程可能看起來像這樣：
* 使用者選取要在應用程式中開啟的文件。
* 在開啟流程的過程中，還未從磁碟讀取資料之前，應用程式會確認顯示內容應該使用的身分識別。
  * MAMFileProtectionInfo info = MAMFileProtectionManager.getProtectionInfo(docPath)
  * if(info)   MAMPolicyManager.setUIPolicyIdentity(activity, info.getIdentity(), callback)
  * 應用程式等待回報給回呼的結果
  * 如果報告的結果是失敗，應用程式就不會顯示文件。
* 應用程式會開啟並轉譯檔案。
  
#### <a name="single-identity-to-multi-identity-transition"></a>將單一身分識別轉換為多身分識別
若先前使用單一身分識別 Intune 整合發行的應用程式稍後與多身分識別進行整合，則先前安裝的應用程式便會發生轉換 (使用者看不到，因為沒有相關聯的 UX)。 應用程式「不需要」  明確地執行任何操作來處理此轉換。 所有在轉換前建立的檔案都會繼續視為受控 (因此若有開啟加密原則，則它們仍會維持在加密狀態)。 若需要的話，您可以偵測升級並使用 `MAMFileProtectionManager.protect` 來使用空白身分識別標記特定檔案或目錄 (若檔案和目錄經過加密，這會移除它們的加密)。

#### <a name="offline-scenarios"></a>離線案例

離線模式需要檔案身分識別標記。 下列各點應該列入考量：

* 如果未安裝公司入口網站，則無法標記檔案的身分識別。

* 如果已安裝公司入口網站，但應用程式沒有 Intune MAM 原則，則檔案將無法確實標記身分識別。

* 當檔案身分識別標記變成可用時，所有先前建立的檔案都會視為個人/未受管理 (屬於空字串身分識別)，除非應用程式之前已安裝為受單一身分識別管理的應用程式，在此情況下則會將它們視為屬於已註冊的使用者。

### <a name="directory-protection"></a>目錄保護

目錄保護可以使用和保護檔案相同的 `protect` 方法來進行保護。 目錄保護會以遞迴方式套用至目錄中的所有檔案和子目錄，以及在目錄內新建立的檔案上。 由於目錄保護是以以遞迴方式套用，針對大型目錄，`protect` 呼叫可能需要花費一些時間才能完成。 基於那個原因，若應用程式要將保護套用至含有大量檔案的目錄，我們建議在背景執行緒上以非同步方式執行 `protect`。

### <a name="data-protection"></a>資料保護

您無法將檔案標記為屬於多重身分識別。 如果應用程式必須將屬於不同使用者的資料儲存到同一個檔案，則可以使用 `MAMDataProtectionManager` 所提供的功能手動執行這項操作。 這可讓應用程式加密資料，並將它繫結至特定的使用者。 加密資料適合存放到磁碟的檔案中。 您可以查詢與身分識別相關聯的資料，並於稍後解密資料。

會運用 `MAMDataProtectionManager` 的應用程式，應該針對 `MANAGEMENT_REMOVED` 通知實作接收器。 如果透過此類別獲得保護的緩衝區在受到保護期間有啟用檔案加密，在此通知完成之後，該緩衝區將會無法讀取。 應用程式可以透過在此通知期間於所有緩衝區上呼叫 `MAMDataProtectionManager.unprotect`，來補救此狀況。 若想要保留身分識別資訊，也可以在此通知期間呼叫保護 (加密在通知期間一定會停用)。


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

如果應用程式透過 `ContentProvider` 提供 `ParcelFileDescriptor` 以外的公司資料，該應用程式必須在 `MAMContentProvider` 中呼叫 `isProvideContentAllowed(String)` 方法，並針對內容傳遞擁有者身分識別的 UPN (使用者主體名稱)。 如果此函式傳回 false，內容「絕不能」  傳回給呼叫者。 透過內容提供者傳回的檔案描述元會自動根據檔案身分識別進行處理。

若您沒有明確繼承 `MAMContentProvider`，且改為允許建置工具進行該變更，您可以呼叫相同方法的靜態版本：`MAMContentProvider.isProvideContentAllowed(provider, contentIdentity)`。

### <a name="selective-wipe"></a>選擇性抹除

如果多重身分識別應用程式註冊 `WIPE_USER_DATA` 通知，應用程式應負責移除所有針對要抹除之使用者的資料，包括已將身分識別標記為屬於該使用者的所有檔案。 如果應用程式從檔案移除使用者資料，但想要將其他資料保留在檔案中，它「必須」  變更檔案的身分識別 (透過 `MAMFileProtectionManager.protect` 至個人使用者或空的身分識別)。 如果加密原則正在使用中，屬於抹除中之使用者的任何剩餘檔案都將不會解密，而且會在抹除之後變成無法供應用程式存取。

如果應用程式註冊 `WIPE_USER_DATA`，它將無法取得 SDK 預設選擇性抹除行為的好處。 針對感知多重身分識別的應用程式，此影響可能更為明顯，因為 MAM 預設選擇性抹除只會抹除其身分識別為抹除目標的檔案。 若多重身分識別感知應用程式想要執行 MAM 預設選擇性抹除，「且」 __ 想要在抹除上執行自己的動作，便應該註冊 `WIPE_USER_AUXILIARY_DATA` 通知。 SDK 會立即傳送這項通知，再執行 MAM 預設選擇性抹除。 應用程式永遠不得同時註冊 `WIPE_USER_DATA` 和 `WIPE_USER_AUXILIARY_DATA`。

預設選擇性抹除會順利關閉應用程式、完成活動並終止應用程式處理序。 若您的應用程式覆寫預設選擇性抹除，建議您考慮手動關閉應用程式，避免使用者在發生抹除後存取記憶體內部的資料。


## <a name="enabling-mam-targeted-configuration-for-your-android-applications-optional"></a>啟用 Android 應用程式的 MAM 目標設定 (選擇性)
您可以為 [MAM-WE](https://docs.microsoft.com/intune/app-configuration-policies-managed-app) 和 [Android 工作設定檔應用程式](https://docs.microsoft.com/intune/app-configuration-policies-use-android)，在 Intune 主控台中設定應用程式特定的索引鍵/值組。
Intune 完全不會解譯這些機碼值組，但會將它們傳遞給應用程式。 想要接收這類設定的應用程式可以使用 `MAMAppConfigManager` 和 `MAMAppConfig` 類別來執行作業。 如有多個原則以相同的應用程式為目標，相同的機碼可能會有多個衝突值。

> [!NOTE] 
> 透過 MAM-WE 的傳遞組態設定無法在 `offline` 中傳遞。  在此情況下，只有 Android Enterprise AppRestriction 會透過空白身分識別上的 `MAMUserNotification` 傳遞。

### <a name="example"></a>範例

```java
MAMAppConfigManager configManager = MAMComponents.get(MAMAppConfigManager.class);
String identity = "user@contoso.com"
MAMAppConfig appConfig = configManager.getAppConfig(identity);
LOGGER.info("App Config Data = " + appConfig.getFullData());
String valueToUse = null;
if (appConfig.hasConflict("foo")) {
    List<String> values = appConfig.getAllStringsForKey("foo");
    for (String value : values) {
        if (isCorrectValue(value)) {
            valueToUse = value;
        }
    }
} else {
    valueToUse = appConfig.getStringForKey("foo", MAMAppConfig.StringQueryType.Any);
}
LOGGER.info("Found value " + valueToUse);
```

### <a name="notification"></a>通知
應用程式設定新增新的通知類型：
* **REFRESH_APP_CONFIG**：這個通知是在 `MAMUserNotification` 中傳送，通知應用程式，確定應用程式有新的應用程式設定資料可用。

### <a name="further-reading"></a>深入閱讀
如需圖形 API 功能的詳細資訊，請參閱[圖形 API 參考](https://developer.microsoft.com/graph/docs/concepts/overview)。 <br>

如需如何在 Android 建立 MAM 目標應用程式設定原則的詳細資訊，請參閱[如何使用 Android for Work 適用的 Microsoft Intune 應用程式設定原則](https://docs.microsoft.com/intune/app-configuration-policies-use-android)中有關 MAM 目標應用程式設定的一節。

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

## <a name="default-enrollment-optional"></a>預設註冊 (選用)

以下是針對自動 APP-WE 服務註冊在應用程式啟動時需要有使用者提示的指導方針 (在這一節中稱之為**預設註冊**)，需要有 Intune 應用程式保護原則，才能只允許受 Intune 保護的使用者使用 SDK 整合的 Android LOB 應用程式。 也包含如何啟用 SDK 整合之 Android LOB 應用程式的 SSO 相關內容。 非 Intune 使用者可使用的市集應用程式**不**支援此功能。

> [!NOTE] 
> **預設註冊**的優點包括從 APP-WE 服務為裝置上的應用程式取得原則的簡化方法。

> [!NOTE] 
> **預設註冊**是主權雲端感知的。

使用下列步驟啟用預設註冊：

1. 若您的應用程式與 ADAL 整合，或是您需要啟用 SSO，請在[常見 ADAL 設定](#common-adal-configurations) #2 之後[設定 ADAL](#configure-azure-active-directory-authentication-library-adal)。 若不需要，您可以跳過此步驟。
   
2. 將下列值放在資訊清單中以啟用預設註冊：

   ```xml 
   <meta-data android:name="com.microsoft.intune.mam.DefaultMAMServiceEnrollment" android:value="true" />
   ```

   > [!NOTE] 
   > 這必須是應用程式中唯一的 MAM-WE 整合。 如有呼叫 MAMEnrollmentManager API 的任何其他嘗試，則會發生衝突。

3. 將下列值放在資訊清單中以啟用所需的 MAM 原則：

   ```xml 
   <meta-data android:name="com.microsoft.intune.mam.MAMPolicyRequired" android:value="true" />
   ```

   > [!NOTE] 
   > 這會強制使用者將公司入口網站下載到裝置上，在使用前完成預設註冊流程。


## <a name="limitations"></a>限制

### <a name="file-size-limitations"></a>檔案大小限制

針對沒有搭配 [ProGuard (英文)](http://proguard.sourceforge.net/) 執行的大型程式碼基底，Dalvik 可執行檔格式的限制將會造成問題。 具體來說，可能會發生下列限制：

1. 65-K 的欄位限制。
2. 65-K 的方法限制。

### <a name="policy-enforcement-limitations"></a>原則強制執行限制

* **使用內容解析程式**：「傳送或接收」Intune 原則可能會封鎖或部分封鎖內容解析程式的使用，不讓其存取另一個應用程式中的內容提供者。 這將導致 `ContentResolver` 方法傳回 null，或擲回錯誤值 (例如，`openOutputStream` 會在被封鎖的情況下擲回 `FileNotFoundException`)。 應用程式可以藉由呼叫下列項目，判斷透過內容解析程式無法寫入資料是否起因於原則 (或可能由原則造成)：

    ```java
    MAMPolicyManager.getPolicy(currentActivity).getIsSaveToLocationAllowed(contentURI);
    ```

    或如果沒有相關聯的活動

    ```java
    MAMPolicyManager.getPolicy().getIsSaveToLocationAllowed(contentURI);
    ```

    在第二個案例中，多重身分識別應用程式必須仔細正確設定執行緒身分識別 (或將明確的身分識別傳遞給 `getPolicy` 呼叫)。

### <a name="exported-services"></a>匯出服務

 Intune App SDK 隨附的 AndroidManifest.xml 檔案包含 **MAMNotificationReceiverService**，其必須為匯出的服務，才能讓公司入口網站傳送通知給受控應用程式。 服務會檢查呼叫者以確保僅允許公司入口網站傳送通知。

### <a name="reflection-limitations"></a>反映限制
部分 MAM 基底類別 (例如 MAMActivity、MAMDocumentsProvider) 包含會使用只存在於某些 API 層級以上之參數或傳回類型的方法 (以原始的 Android 基底類別為基礎)。 因此，它不可能一直使用反映來列舉所有的應用程式元件方法。 此限制並不限於 MAM，如果應用程式本身實作這些來自 Android 基底類別的方法，也會套用相同的限制。

### <a name="robolectric"></a>Robolectric
不支援在 Robolectric 下測試 MAM SDK 行為。 在 Robelectric 下執行 MAM SDK 會有一些已知問題，其原因是 Robolectric 下的某些行為無法正確地模擬實際裝置或模擬器上行為。

如果您需要在 Roboelectric 下測試應用程式，建議的因應措施是將應用程式類別邏輯移至協助程式，並使用不是繼承自 MAMApplication 的應用程式類別來產生單元測試 APK。
## <a name="expectations-of-the-sdk-consumer"></a>SDK 取用者的期望

Intune SDK 會維護由 Android API 所提供的合約，但可能會因為強制執行原則，而更頻繁地觸發失敗狀況。 下列 Android 最佳作法可降低失敗的可能性：

* Android SDK 函式如果可能會傳回 null，則現在為 null 的可能性更高。  若要將問題降至最低，請確定 null 檢查是在正確的位置。

* 針對可以檢查的功能，必須透過其 MAM 取代項目 API 進行檢查。

* 任何衍生的函式皆必須透過其超級類別版本進行呼叫。

* 避免以模稜兩可的方式使用任何 API。 例如，在未檢查 requestCode 的情況下使用 `Activity.startActivityForResult`，將會導致奇怪的行為。

## <a name="telemetry"></a>遙測

Intune App SDK for Android 不會控制來自您應用程式的資料收集。 根據預設，公司入口網站應用程式會記錄系統產生的資料。 這些資料會傳送到 Microsoft Intune。 根據 Microsoft 的原則，我們不會收集任何個人資料。

> [!NOTE]
> 如果終端使用者選擇不要傳送此資料，則必須在公司入口網站應用程式的 [設定] 下關閉遙測。 若要深入了解，請參閱[關閉 Microsoft 使用狀況資料收集](https://docs.microsoft.com/intune-user-help/turn-off-microsoft-usage-data-collection-android)。 

## <a name="recommended-android-best-practices"></a>建議的 Android 最佳作法

* 所有程式庫專案應盡可能共用相同的 android:package。 這不會在執行階段偶發性地發生失敗，而純粹是建置時間問題。 較新版本的 Intune App SDK 將會移除部分的冗餘項目。

* 使用最新的 Android SDK 建置工具。

* 移除所有不必要和未使用的程式庫 (例如 android.support.v4)

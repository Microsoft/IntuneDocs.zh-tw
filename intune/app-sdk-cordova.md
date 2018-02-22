---
title: "Microsoft Intune App SDK Cordova 外掛程式"
description: 
keywords: sdk, Cordova, intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/02/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: bb940cb9-d43f-45ca-b065-ac0adc61dc6f
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: d42f8418e2f277dca0fbb2f01248f5a815606cb6
ms.sourcegitcommit: a6fd6b3df8e96673bc2ea48a2b9bda0cf0a875ae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2018
---
# <a name="microsoft-intune-app-sdk-cordova-plugin"></a>Microsoft Intune App SDK Cordova 外掛程式

> [!IMPORTANT]
> Intune 將於 2018 年 5 月 1 日結束對 Microsoft Intune App SDK Cordova 外掛程式的支援。 我們建議您改用 Intune App Wrapping Tool。 如需了解 App Wrapping Tool 的詳細資訊，請參閱[適用於 iOS 的 App Wrapping Tool](app-wrapper-prepare-ios.md) 和[適用於 Android 的 App Wrapping Tool](app-wrapper-prepare-android.md)。 如需這項變更的詳細資訊，請參閱 [Microsoft Intune 的新功能](whats-new.md)的[通知](whats-new.md#notices)區段。

## <a name="overview"></a>概觀

[Intune App SDK Cordova 外掛程式](/intune-classic/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune)能在使用 Cordova 建置的 iOS 和 Android 應用程式中啟用 Intune 行動應用程式保護原則。 外掛程式可讓開發人員將 Intune 應用程式和資料保護功能整合至其 Cordova 應用程式。

> [!NOTE]
> 您可能想要先閱讀 [Intune App SDK 快速入門](app-sdk-get-started.md)文章，其中說明如何在每個支援的平台上進行整合準備。

您會發現您可以啟用 SDK 功能，而不需要變更您應用程式的行為。 當您於 iOS 或 Android 應用程式中建置該外掛程式之後，Microsoft Intune 系統管理員將能部署 Intune 應用程式保護原則，其中包含各種不同的資料保護功能。 該外掛程式已建置為能使大部分的步驟在 Cordova 建置程序中自動執行。 如此一來，您應該能夠快速地啟用應用程式的 Intune 應用程式保護。 若要開始，請根據目標平台遵循下列步驟。

## <a name="supported-platforms"></a>支援的平台

* 外掛程式適用於 Windows、Mac 和 Linux OS
* 外掛程式適用於 `minSdkVersion` >= 14 且 `targetSdkVersion` <= 24 的 Android 應用程式
* 外掛程式適用於以 iOS 9.0 或以上版本為目標的 iOS 應用程式。

## <a name="intune-mobile-application-management-scenarios"></a>Intune 行動應用程式管理案例

* Intune MDM 已註冊的裝置
* 協力廠商 EMM 已註冊的裝置
* 未受管理的裝置 (未使用任何 MDM 註冊)

使用 Intune App SDK Cordova 外掛程式建置的 Cordova 應用程式，現在可以在 Intune 行動裝置管理 (MDM) 註冊裝置和未註冊裝置上，接收 Intune 應用程式保護原則。

## <a name="prerequisites"></a>必要條件

### <a name="android"></a>Android

* 最新的 Microsoft Intune 公司入口網站應用程式一律必須安裝在裝置上。
* 使用外掛程式時，Java 7 至少必須在將執行 Cordova 組建的路徑上。

### <a name="ios"></a>iOS

* 最新的 Microsoft Intune 公司入口網站應用程式必須安裝在裝置上，以取得 MDM 功能。 這對於無裝置註冊功能的 Intune 應用程式保護原則「並非」必要。

### <a name="both-platforms"></a>針對兩個平台

* 需要 0.8.0 版以上的 [Cordova 的 Azure Active Directory 驗證程式庫 (ADAL) 外掛程式](https://github.com/AzureAD/azure-activedirectory-library-for-cordova)。

> [!NOTE]
> 由於[這裡 (英文)](https://issues.apache.org/jira/browse/CB-6227?jql=text%20~%20%22plugin%20dependency%22) 所記載的 Apache Cordova Bug，已經有外掛程式相依性的應用程式將不會把外掛程式自動升級為要求的版本。



## <a name="quickstart"></a>快速入門

1. 更新您的 ADAL 版本︰

  ```shell
  cordova plugin remove cordova-plugin-ms-adal
  cordova plugin add cordova-plugin-ms-adal@0.8.x
  ```

2. 新增 Intune App SDK for Cordova 外掛程式：

  ```shell
  cordova plugin add cordova-plugin-ms-intune-mam
  ```

## <a name="build-the-plugin-into-your-ios-app"></a>將外掛程式建置到 iOS 應用程式中

您必須完成一些步驟，您的應用程式才能針對 Intune 應用程式保護原則進行啟用。 為了方便起見，這些步驟會在 Cordova 建置流程中自動執行，以作為建置前攔截程序。 如此一來，自動化的步驟會修改您的 `*.pbxproj`、`*-Info.plist` 和 `*.entitlements` 等專案組態相關聯檔案。 如果您的專案未包含的 entitlements 檔案，則外掛程式會自動建立一個。

這項設定只支援單一目標，而且將會在有多個目標時於第一個發現的目標上執行設定。 如果此程序失敗，請確認︰

1. 您的應用程式的 Xcode 專案是 `[name].xcodeproj`，其中 `[name]` 是 `config.xml` 中已定義的值
2. 您的專案使用[標準 Cordova 應用程式目錄結構](https://cordova.apache.org/docs/en/latest/reference/cordova-cli/index.html#directory-structure)。

## <a name="build-the-plugin-into-your-android-app"></a>將外掛程式建置到 Android 應用程式中

1. 使用最新的 Cordova 工具匯入此外掛程式。 外掛程式會自動叫用作為 `after_compile` 步驟。

2. 外掛程式會在建置程序的結尾建立建置 APK (Android API 14+) 的啟用 Intune 版本。 建置輸出將會包含 `[Project]-intunewrapped-[Build_Configuration].apk` (例如 `helloWorld-intunewrapped-debug.apk`)。

> [!NOTE]
> 外掛程式只支援 gradle 組建。

由於[這裡](https://issues.apache.org/jira/browse/CB-9434)記載的 Cordova bug，它導致會在 `cordova run` 忽略特定 Cordova 攔截程序。若要從命令列執行包裝的應用程式，您必須執行下列各項︰

```shell
$ cordova build
$ cordova run --nobuild
```

## <a name="sign-your-android-app"></a>登入 Android 應用程式

外掛程式會於下列位置自動識別您提供給 Cordova 的簽署資訊：

* platforms/android/debug-signing.properties
* platforms/android/release-signing.properties
* res/native/android/ant.properties

請參閱 [Cordova gradle 簽署資訊 (英文)](https://cordova.apache.org/docs/en/latest/guide/platforms/android/#using-gradle) 以取得預期格式的詳細資訊。

我們目前不支援以 `build.json` 或透過參數提供的任意位置來為 Cordova 組建提供簽署資訊的能力。

## <a name="debugging-from-visual-studio"></a>從 Visual Studio 偵錯

在第一次啟動應用程式之後，您應該會看到一個對話方塊，通知您應用程式由 Intune 管理。 按一下 [不要再顯示]，然後再從 VS 按一下 [偵錯/執行] 按鈕，以命中中斷點。

## <a name="known-limitations"></a>已知限制

### <a name="android"></a>Android

* MultiDex 支援不完整。
* 應用程式的 `minSdkVersion` 必須為 14，且 `targetSdkVersion` 必須為 24 或以下。 我們目前不支援以 API 25 為目標的應用程式
* 我們無法重新簽署已使用 V2 簽署配置進行簽署的應用程式。 當 V2 簽署的應用程式由外掛程式包裝時，包裝的輸出 .apk 將會移除簽署。
*
  * 您可以將下列內容新增至 `build-extras.gradle` 檔案，來停用 Cordova 的預設 V2 簽署：

  ```gradle
  android {
      signingConfigs {
          release {
              v2SigningEnabled false
          }
          debug {
              v2SigningEnabled false
          }
      }
      buildTypes {
          release {
              signingConfig signingConfigs.release
          }
          debug {
              signingConfig signingConfigs.debug
          }
      }
  }
  ```

### <a name="ios"></a>iOS

* 每當您在 **Info.plist** 檔案的 **CFBundleDocumentTypes** 節點下修改 UTI 清單，都必須在相同 plist 檔案的 [已匯入 UTI] 區段 (**UTImportedTypeDeclarations** 節點) 清除 Intune UTI，然後才再次建置。 所有的 Intune UTI 都會以 `com.microsoft.intune.mam` 前置詞做為開頭。

* 如果您想要從 Cordova 專案移除適用於 Cordova 的 Intune App SDK 外掛程式，則也必須移除 iOS 平台，並且重新新增它，以復原 .xcodeproj 和.plist 檔案中的一些 Intune 設定。

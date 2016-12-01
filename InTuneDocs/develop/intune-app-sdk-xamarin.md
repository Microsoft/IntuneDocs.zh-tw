---
title: "Microsoft Intune App SDK Xamarin 元件 | Microsoft Intune"
description: 
keywords: sdk, Xamarin, intune
author: oydang
manager: karthikaraman
ms.author: oydang
ms.date: 11/15/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 275d574b-3560-4992-877c-c6aa480717f4
ms.reviewer: karthikaraman
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ca4623db80d711f3543b6d688fb1bb1ef228c62c
ms.openlocfilehash: e2d43fff8772046fe7426b267e39d53b278d4e5c


---

# <a name="microsoft-intune-app-sdk-xamarin-component"></a>Microsoft Intune App SDK Xamarin 元件

## <a name="overview"></a>概觀
[Intune App SDK Xamarin 元件](https://components.xamarin.com/view/microsoft.intune.mam)能在使用 Xamarin 建置的 iOS 和 Android 應用程式中啟用 [Intune 行動應用程式管理功能](/intune/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune)。 元件可讓開發人員輕鬆將應用程式內限制及資料保護功能建置到以 Xamarin 為基礎的應用程式。

您會發現，您可以啟用 SDK 功能，而不需要變更您的應用程式行為。 一旦將元件建置到您的 iOS 或 Android 的行動應用程式，IT 系統管理員便可以透過 Microsoft Intune 支援各種啟用資料保護的功能來部署原則。

## <a name="supported-scenarios"></a>支援的案例

### <a name="platforms"></a>平台
* Android
* iOS


### <a name="emm-scenarios"></a>EMM 案例

* Intune MDM 註冊裝置上的 Intune MAM
* 協力廠商 EMM 註冊裝置上的 Intune MAM
* 未註冊、未受管理裝置上的 Intune MAM

使用 Intune App SDK Xamarin 元件建置的 Xamarin 應用程式，現在可以在 Intune 行動裝置管理 (MDM) 註冊裝置和未註冊裝置上，接收 Intune 行動應用程式管理 (MAM) 原則。

## <a name="prerequisites"></a>必要條件

* **[僅限 android]** 最新的 Microsoft Intune 公司入口網站應用程式永遠必須安裝在裝置上。

## <a name="get-started"></a>開始使用

1.  從[這裡](https://components.xamarin.com/submit/xpkg)下載 **Xamarin-component.exe** 並將它解壓縮。

2. 閱讀 Microsoft Intune MAM Xamarin 元件的[授權條款](https://components.xamarin.com/license/microsoft.intune.mam)。

3.  從 [GitHub](https://github.com/msintuneappsdk/intune-app-sdk-xamarin) 或 [Xamarin](https://components.xamarin.com/license/microsoft.intune.mam) 下載 Intune App SDK Xamarin 元件資料夾並將它解壓縮。 從步驟 1 和步驟 2 下載的兩個檔案應該在相同的目錄層級中。

4.  以系統管理員身分在命令列執行 `Xamain.Component.exe install <.xam> file`。

5.  在 Visual Studio 中，以滑鼠右鍵按一下先前所建立 Xamarin 專案中的 [元件]。

6.  選取 [編輯元件] 並在本機將您下載的 Intune App SDK 元件新增到您的電腦。



## <a name="enabling-intune-mam-in-your-ios-mobile-app"></a>在 iOS 行動應用程式中啟用 Intune MAM
1.  為了初始化 Intune App SDK，您需要能夠在 `AppDelegate.cs` 類別中呼叫任何 API。 例如：

      ```csharp
      public override bool FinishedLaunching (UIApplication application, NSDictionary launchOptions)
      {
            Console.WriteLine ("Is Managed: {0}", IntuneMAMPolicyManager.Instance.PrimaryUser != null);
            return true;
      }

      ```

2.  既然已新增並初始化元件，您可以依照將 App SDK 建置成 iOS 行動應用程式所需的一般步驟。 您可以在 [Intune App SDK for iOS 開發人員指南](intune-app-sdk-ios)中找到啟用原生 iOS 應用程式的完整文件。
3. **重要**︰有 Xamarin 為基礎的 iOS 應用程式特有的一些修改。 比方說，當啟用金鑰鏈群組時，您必須新增下列內容，以包含我們在元件中包含的 Xamarin 範例應用程式。 以下是在金鑰鏈存取群組中必須要有的群組範例︰

      ```xml
      <?xml version="1.0" encoding="UTF-8"?>
      <!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
      <plist version="1.0">
            <dict>
                  <key>keychain-access-groups</key>
                  <array>
                        <string>$(AppIdentifierPrefix)com.xamarin.microsoftintunesample</string>
                        <string>$(AppIdentifierPrefix)com.xamarin.microsoftintunesample.intunemam</string>
                        <string>$(AppIdentifierPrefix)com.microsoft.intune.mam</string>
                        <string>$(AppIdentifierPrefix)com.microsoft.adalcache</string>
                  </array>
            </dict>
      </plist>
      ```

您已完成將元件建置成以 Xamarin 為基礎的 iOS 應用程式所需的步驟。 如果您使用 Xcode 來建置您的專案，可以使用 `Intune App SDK Settings.bundle`。 這可讓您在您建置專案來測試和偵錯時，切換開關 Intune 原則設定。 若要利用此套組，請依照 [Intune App SDK for iOS 開發人員指南](intune-app-sdk-ios)中的步驟，並閱讀關於[在 Xcode 中偵錯](intune-app-sdk-ios#debug-information)的小節。

## <a name="enabling-mam-in-your-android-mobile-app"></a>在 Android 行動應用程式中啟用 MAM
若為未使用 UI 架構且以 Xamarin 為基礎的 Android 應用程式，您必須閱讀並遵循 [Intune App SDK for Android 開發人員指南]。 針對您以 Xamarin 為基礎的 Android 應用程式，您必須根據指南中包含的[資料表](intune-app-sdk-android#replace-classes-methods-and-activities-with-their-mam-equivalent-required)，將類別、方法和活動取代為其 MAM 對等項目。 如果您的應用程式未定義 `android.app.Application` 類別，您將需要建立一個，並確定繼承自 `MAMApplication`。

針對 Xamarin 表單和其他 UI 架構，我們提供了稱為 `MAM.Remapper` 的工具。 此工具會為您完成類別取代。 不過，您必須執行下列步驟︰

1.  新增對 ` Microsoft.Intune.MAM.Remapper.Tasks` nuget 套件 0.1.0.0 版或更新版本的參考。

2.  將下行新增至您的 Android csproj：
  ```xml
  <Import
  Project="$(NugetPack)\\Microsoft.Intune.MAM.Remapper.Tasks.0.1.X.X\\build\\MonoAndroid10\\Microsoft.Intune.MAM.Remapper.targets" />
  ```

3.  將新增之 `remapping-config.json` 檔案的建置動作設為 **RemappingConfigFile**。 包含的 `remapping-config.json` 僅適用於 Xamarin.Forms。 若為其他的 UI 架構，請參閱 Remapper nuget 套件所包含的讀我檔案。

## <a name="test-your-app"></a>測試應用程式

您已完成將元件建置成應用程式的基本步驟。 現在您可以依照 Xamarin Android 範例應用程式中的步驟。 我們提供了兩個範例，一個用於 Xamarin.Forms，另一個適用於 Android。



<!--HONumber=Nov16_HO3-->



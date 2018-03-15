---
title: "Microsoft Intune App SDK Xamarin 元件"
description: "Intune App SDK Xamarin 元件可在使用 Xamarin 建置的 iOS 和 Android 應用程式中啟用 Intune 應用程式保護原則。"
keywords: sdk, Xamarin, intune
author: Erikre
manager: dougeby
ms.author: erikre
ms.date: 03/02/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 275d574b-3560-4992-877c-c6aa480717f4
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 9fa0d471f91eeeebd0058417aa437e5469f48e09
ms.sourcegitcommit: 7e5c4d43cbd757342cb731bf691ef3891b0792b5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2018
---
# <a name="microsoft-intune-app-sdk-xamarin-component"></a>Microsoft Intune App SDK Xamarin 元件

> [!NOTE]
> 您可能想要先閱讀 [Intune App SDK 快速入門](app-sdk-get-started.md)文章，其中說明如何在每個支援的平台上進行整合準備。

## <a name="overview"></a>概觀
[Intune App SDK Xamarin 元件](https://github.com/msintuneappsdk/intune-app-sdk-xamarin)能在使用 Xamarin 建置的 iOS 和 Android 應用程式中啟用 [Intune 應用程式保護原則](/intune-classic/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune)。 元件可讓開發人員輕鬆將 Intune 應用程式內資料保護功能建置到以 Xamarin 為基礎的應用程式。

> [!NOTE]
> Xamarin 的 Intune SDK 支援目前可供預覽。 

Microsoft Intune App SDK Xamarin Component 可讓您將 Intune 應用程式保護原則 (也稱為 APP 或 MAM 原則) 併入使用 Xamarin 所開發的應用程式。 啟用 MAM 的應用程式是與 Intune App SDK 整合的應用程式。 IT 系統管理員可在 Intune 主動管理應用程式時，將應用程式保護原則部署至行動應用程式。

## <a name="whats-supported"></a>支援的項目

### <a name="developer-machines"></a>開發人員電腦
* macOS


### <a name="mobile-app-platforms"></a>行動應用程式平台
* Android
* iOS


### <a name="intune-mobile-application-management-scenarios"></a>Intune 行動應用程式管理案例

* Intune MDM 已註冊的裝置
* 協力廠商 EMM 已註冊的裝置
* 未受控裝置 (未使用任何 MDM 註冊)

使用 Intune App SDK Xamarin Component 建置的 Xamarin 應用程式，現在可以在 Intune 行動裝置管理 (MDM) 註冊裝置和未註冊裝置上，接收 Intune 應用程式保護原則。

## <a name="prerequisites"></a>必要條件

* **[僅限 Android]** 最新的 Microsoft Intune 公司入口網站應用程式必須安裝在裝置上。

## <a name="get-started"></a>開始使用

1.  從[這裡](https://components.xamarin.com/submit/xpkg)下載 **Xamarin-component.exe** 並將它解壓縮。

2. 閱讀 Microsoft Intune MAM Xamarin 元件的[授權條款](https://components.xamarin.com/license/microsoft.intune.mam)。

3.  從 [GitHub](https://github.com/msintuneappsdk/intune-app-sdk-xamarin) 或 [Nuget.org](https://www.nuget.org/profiles/msintuneappsdk) 下載 Intune App SDK Xamarin 元件資料夾並將它解壓縮。 從步驟 1 和步驟 3 下載的兩個檔案應該在相同的目錄層級中。

4.  以系統管理員身分在命令列執行 `mono Xamarin.Component.exe install <.xam> file`。

5.  在 Visual Studio 中，以滑鼠右鍵按一下先前所建立 Xamarin 專案中的 [元件]。

6.  選取 [編輯元件] 並在本機將您下載的 Intune App SDK 元件新增到您的電腦。



## <a name="enabling-intune-app-protection-polices-in-your-ios-mobile-app"></a>在 iOS 行動應用程式中啟用 Intune 應用程式保護原則
1.  請遵循將 Intune App SDK 整合至 iOS 行動應用程式所需的一般步驟。 您可以從 [Intune App SDK for iOS 開發人員指南](app-sdk-ios.md#build-the-sdk-into-your-mobile-app)之整合指示的步驟 3 開始。
    **重要**：在 Visual Studio 中針對應用程式啟用金鑰鏈共用的方式與 Xcode 有些許不同。 開啟應用程式的 Entitlements plist，並確保 [啟用金鑰鏈] 選項已啟用，且已將適當的金鑰鏈共用群組新增至該區段。 接著，確保 Entitlements plist 已針對所有適當的設定/平台組合，指定於專案 [iOS 套件組合簽署] 選項的 [自訂權利] 欄位中。
2.  在新增元件且正確設定應用程式之後，您的應用程式便可以開始使用 Intune SDK 的 API。 若要這麼做，您必須包含下列命名空間：

      ```csharp
      using Microsoft.Intune.MAM;
      ```
3.    若要開始接收應用程式保護原則，您的應用程式必須註冊至 Intune MAM 服務。 如果您的應用程式已使用 Azure Active Directory Authentication Library (ADAL) 來驗證使用者，應用程式應該在成功驗證之後，將使用者的 UPN 提供給 IntuneMAMEnrollmentManager 的 registerAndEnrollAccount 方法：
      ```csharp
      IntuneMAMEnrollmentManager.Instance.RegisterAndEnrollAccount(string identity);
      ```
      **重要**：請務必以您應用程式的 ADAL 設定覆寫 Intune App SDK 的預設 ADAL 設定。 若要這麼做，您可以依 [Intune App SDK for iOS 開發人員指南](app-sdk-ios.md#configure-settings-for-the-intune-app-sdk)中所述的方式透過應用程式 Info.plist 中的 IntuneMAMSettings 目錄，或是使用 IntuneMAMPolicyManager 執行個體的 AAD 覆寫屬性來完成。 Info.plist 方法是針對 ADAL 設定為靜態之應用程式的建議選項，而覆寫屬性則是針對會於執行階段決定那些值之應用程式的建議選項。 
      
      如果您的應用程式不使用 ADAL，且想要由 Intune SDK 負責處理驗證，您的應用程式便應呼叫 IntuneMAMEnrollmentManager 的 loginAndEnrollAccount 方法：
      ```csharp
       IntuneMAMEnrollmentManager.Instance.LoginAndEnrollAccount([NullAllowed] string identity);
      ```

## <a name="enabling-app-protection-policies-in-your-android-mobile-app"></a>在 Android 行動應用程式中啟用應用程式保護原則
若為未使用 UI 架構且以 Xamarin 為基礎的 Android 應用程式，您必須閱讀並遵循 [Intune App SDK for Android 開發人員指南](app-sdk-android.md)。 針對您以 Xamarin 為基礎的 Android 應用程式，您必須根據指南中包含的[資料表](app-sdk-android.md#replace-classes-methods-and-activities-with-their-mam-equivalent)，將類別、方法和活動取代為其 MAM 對等項目。 如果您的應用程式未定義 `android.app.Application` 類別，則需要建立一個，並確定繼承自 `MAMApplication`。

針對 Xamarin 表單和其他 UI 架構，我們提供了稱為 `MAM.Remapper` 的工具。 此工具會為您完成類別取代。 不過，您必須執行下列步驟︰

1.  新增對 `Microsoft.Intune.MAM.Remapper.Tasks` NuGet 套件 0.1.0.0 版或更新版本的參考。

2.  將下行新增至您的 Android csproj：
  ```xml
  <Import
  Project="$(NugetPack)\\Microsoft.Intune.MAM.Remapper.Tasks.0.1.X.X\\build\\MonoAndroid10\\Microsoft.Intune.MAM.Remapper.targets" />
  ```

3.  將新增之 `remapping-config.json` 檔案的建置動作設為 **RemappingConfigFile**。 包含的 `remapping-config.json` 僅適用於 Xamarin.Forms。 若為其他 UI 架構，請參閱 Remapper NuGet 套件所包含的讀我檔案。

## <a name="next-steps"></a>後續步驟

您已完成將元件建置成應用程式的基本步驟。 現在您可以依照 Xamarin Android 範例應用程式中的步驟。 我們提供了兩個範例，一個用於 Xamarin.Forms，另一個適用於 Android。

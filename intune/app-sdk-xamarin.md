---
title: Microsoft Intune App SDK Xamarin 繫結
description: 「Intune App SDK Xamarin 繫結」可讓您在以 Xamarin 建置的 iOS 和 Android 應用程式中啟用 Intune 應用程式保護原則。
keywords: sdk, Xamarin, intune
author: Erikre
manager: dougeby
ms.author: erikre
ms.date: 03/19/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 275d574b-3560-4992-877c-c6aa480717f4
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 9f9cc117925f59c9fb7c55d0ff10aedf09d26f93
ms.sourcegitcommit: b727b6bd6f138c5def7ac7bf1658068db30a0ec3
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2018
---
# <a name="microsoft-intune-app-sdk-xamarin-bindings"></a>Microsoft Intune App SDK Xamarin 繫結

> [!NOTE]
> 您可能想要先閱讀 [Intune App SDK 快速入門](app-sdk-get-started.md)文章，其中說明如何在每個支援的平台上進行整合準備。

## <a name="overview"></a>概觀
[Intune App SDK Xamarin 繫結](https://github.com/msintuneappsdk/intune-app-sdk-xamarin)可讓您在以 Xamarin 建置的 iOS 和 Android 應用程式中啟用 [Intune 應用程式保護原則](/intune-classic/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune)。 繫結可讓開發人員輕鬆將 Intune 應用程式內的保護功能建置到以 Xamarin 為基礎的應用程式中。

「Microsoft Intune App SDK Xamarin 繫結」可讓您將 Intune 應用程式保護原則 (也稱為 APP 或 MAM 原則) 合併至以 Xamarin 開發的應用程式中。 啟用 MAM 的應用程式是與 Intune App SDK 整合的應用程式， IT 系統管理員可在 Intune 主動管理應用程式時，將應用程式保護原則部署至行動應用程式。

## <a name="whats-supported"></a>支援的項目

### <a name="developer-machines"></a>開發人員電腦
* Windows
* macOS


### <a name="mobile-app-platforms"></a>行動應用程式平台
* Android
* iOS


### <a name="intune-mobile-application-management-scenarios"></a>Intune 行動應用程式管理案例

* Intune APP-WE (無裝置註冊)
* Intune MDM 已註冊的裝置
* 協力廠商 EMM 已註冊的裝置

使用「Intune App SDK Xamarin 繫結」建置的 Xamarin 應用程式現在於 Intune 行動裝置管理 (MDM) 已註冊裝置和未註冊裝置上，都可接收 Intune 應用程式保護原則。

## <a name="prerequisites"></a>必要條件

檢閱[授權條款](https://github.com/msintuneappsdk/intune-app-sdk-xamarin/blob/master/Microsoft%20License%20Terms%20Intune%20App%20SDK%20Xamarin%20Component.pdf)。 列印並保留一份授權條款供您備查。 下載並使用「Intune App SDK Xamarin 繫結」即表示您同意這些授權條款。 若貴用戶不同意這些授權條款，請不要使用「軟體」。

## <a name="enabling-intune-app-protection-polices-in-your-ios-mobile-app"></a>在 iOS 行動應用程式中啟用 Intune 應用程式保護原則
1. 將 [Microsoft.Intune.MAM.Xamarin.iOS NuGet 套件](https://www.nuget.org/packages/Microsoft.Intune.MAM.Xamarin.iOS)新增至 Xamarin.iOS 專案。
2.  請遵循將 Intune App SDK 整合至 iOS 行動應用程式所需的一般步驟。 您可以從 [Intune App SDK for iOS 開發人員指南](app-sdk-ios.md#build-the-sdk-into-your-mobile-app)之整合指示的步驟 3 開始。 您可以略過執行 IntuneMAMConfigurator 一節中的最後一個步驟，因為此工具隨附於 Microsoft.Intune.MAM.Xamarin.iOS 套件，並會在建置時間自動執行。
    **重要**：在 Visual Studio 中針對應用程式啟用金鑰鏈共用的方式與 Xcode 有些許不同。 開啟應用程式的 Entitlements plist，並確保 [啟用金鑰鏈] 選項已啟用，且已將適當的金鑰鏈共用群組新增至該區段。 接著，確保 Entitlements plist 已針對所有適當的設定/平台組合，指定於專案 [iOS 套件組合簽署] 選項的 [自訂權利] 欄位中。
3.  在新增繫結並正確設定應用程式之後，您的應用程式便可以開始使用 Intune SDK 的 API。 若要這麼做，您必須包含下列命名空間：

      ```csharp
      using Microsoft.Intune.MAM;
      ```
4. 若要開始接收應用程式保護原則，您的應用程式必須註冊至 Intune MAM 服務。 如果您的應用程式已使用 Azure Active Directory Authentication Library (ADAL) 來驗證使用者，應用程式應該在成功驗證之後，將使用者的 UPN 提供給 IntuneMAMEnrollmentManager 的 registerAndEnrollAccount 方法：
      ```csharp
      IntuneMAMEnrollmentManager.Instance.RegisterAndEnrollAccount(string identity);
      ```
      **重要**：請務必以您應用程式的 ADAL 設定覆寫 Intune App SDK 的預設 ADAL 設定。 若要這麼做，您可以依 [Intune App SDK for iOS 開發人員指南](app-sdk-ios.md#configure-settings-for-the-intune-app-sdk)中所述的方式透過應用程式 Info.plist 中的 IntuneMAMSettings 目錄，或是使用 IntuneMAMPolicyManager 執行個體的 AAD 覆寫屬性來完成。 Info.plist 方法是針對 ADAL 設定為靜態之應用程式的建議選項，而覆寫屬性則是針對會於執行階段決定那些值之應用程式的建議選項。 
      
      如果您的應用程式不使用 ADAL，且想要由 Intune SDK 負責處理驗證，您的應用程式便應呼叫 IntuneMAMEnrollmentManager 的 loginAndEnrollAccount 方法：
      ```csharp
       IntuneMAMEnrollmentManager.Instance.LoginAndEnrollAccount([NullAllowed] string identity);
      ```

## <a name="enabling-app-protection-policies-in-your-android-mobile-app"></a>在 Android 行動應用程式中啟用應用程式保護原則
將 [Microsoft.Intune.MAM.Xamarin.Android NuGet 套件](https://www.nuget.org/packages/Microsoft.Intune.MAM.Xamarin.Android)新增至 Xamarin.Android 專案。

針對 Xamarin.Android 應用程式，您必須完整閱讀並依照 [Intune App SDK for Android 開發人員指南](app-sdk-android.md)進行操作，包括根據該指南中所含的[表格](app-sdk-android.md#replace-classes-methods-and-activities-with-their-mam-equivalent)，將類別、方法及活動取代成其 MAM 對等項目。 

> [!NOTE]
> 如果您的應用程式未定義 `android.app.Application` 類別，則需要建立一個，並確定繼承自 `MAMApplication`。

> [!NOTE]
> 嘗試從 [Intune App SDK for Android 開發人員指南](app-sdk-android.md)尋找 `Microsoft.Intune.MAM.Xamarin.Android` 繫結中的對等 API，或從該指南轉換程式碼片段時，請注意 Xamarin 的繫結產生器會以下列顯著的方式修改 Android API：
> * 所有識別碼都會轉換成 Pascal 命名法的大小寫 (com.microsoft.foo -> Com.Microsoft.Foo)
> * 所有 get/set 作業都會轉換成屬性作業 (例如 Foo.getBar() -> Foo.Bar、Foo.setBar("zap") -> Foo.Bar = "zap")
> * 所有介面的名稱前面都會加上 'I' 字元 (FooInterface -> IFooInterface)

針對使用 Xamarin.Forms 或其他 UI 架構的應用程式，我們已提供一個稱為 `Microsoft.Intune.MAM.Remapper` 的工具。 此工具會為您完成類別取代。 若要使用它，請執行下列操作：

1.  將 [Microsoft.Intune.MAM.Remapper.Tasks](https://www.nuget.org/packages/Microsoft.Intune.MAM.Remapper.Tasks) NuGet 套件新增至您的專案。

2.  將 NuGet 套件所隨附 `remapping-config.json` 檔案的建置動作設定為 **RemappingConfigFile**。 包含的 `remapping-config.json` 僅適用於 Xamarin.Forms。 若為其他 UI 架構，請參閱 Remapper NuGet 套件所包含的讀我檔案。

3.  在 MAMApplication 的 OnMAMCreate 函式中，新增對 Xamarin.Forms.Forms.Init(Context, Bundle) 的呼叫，因為使用 Intune 管理時，應用程式可以在處於背景時啟動。

4.  執行 [Intune App SDK for Android 開發人員指南](app-sdk-android.md) 中適用於您應用程式的其餘步驟。

> [!NOTE]
> remapping-config.json 的建置動作有時可能會在更新 Microsoft.Intune.MAM.Remapper.Tasks 套件時重設，這會導致您的建置失敗。

## <a name="next-steps"></a>接下來的步驟

您已完成設定應用程式來進行 Intune 管理的基本步驟。 現在，您可以依照以上所列每個平台整合指南中所含的步驟進行操作。

如果組織是現有的 Intune 客戶，請與您的 Microsoft 支援代表合作，[在 Github 問題頁面](https://github.com/msintuneappsdk/intune-app-sdk-xamarin/issues)上開啟支援票證並建立問題，我們將會儘快提供協助。 
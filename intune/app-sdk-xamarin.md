---
title: Microsoft Intune App SDK Xamarin 繫結
description: 「Intune App SDK Xamarin 繫結」可讓您在以 Xamarin 建置的 iOS 和 Android 應用程式中啟用 Intune 應用程式保護原則。
keywords: sdk, Xamarin, intune
author: Erikre
manager: dougeby
ms.author: erikre
ms.date: 06/08/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 275d574b-3560-4992-877c-c6aa480717f4
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: f8f5e397c314088c7b26edba486f9cbaf9718096
ms.sourcegitcommit: 1eddded65ae9e442dd3bebd16b9428af76a67f34
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2018
ms.locfileid: "35250939"
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
      
> [!NOTE] 
> 沒有 iOS 的 Remapper。 整合到 Xamarin.Forms 應用程式應該與一般 Xamarin.iOS 專案相同。 

## <a name="enabling-intune-app-protection-policies-in-your-android-mobile-app"></a>在 Android 行動應用程式中啟用 Intune 應用程式保護原則

### <a name="xamarinandroid-integration"></a>Xamarin.Android 整合

1. 將最新版的 [Microsoft.Intune.MAM.Xamarin.Android NuGet 套件](https://www.nuget.org/packages/Microsoft.Intune.MAM.Xamarin.Android)新增至 Xamarin.Android 專案。 這會提供您 Intune 的必要參考來啟用應用程式。

2. 徹底閱讀並遵循 [Intune App SDK for Android 開發人員指南](app-sdk-android.md)，並特別注意：
    1. [完整類別和方法取代](app-sdk-android.md#replace-classes-methods-and-activities-with-their-mam-equivalent)一節。 
    2. [MAMApplication ](app-sdk-android.md#mamapplication)。 確定您的子類別已正確地使用 `[Application]` 屬性加以裝飾，並覆寫 `(IntPtr, JniHandleOwnership)` 建構函式。
    3. [ADAL 整合](app-sdk-android.md#configure-azure-active-directory-authentication-library-adal)一節 (如果您的應用程式向 AAD 執行驗證)。
    4. [MAM-WE 註冊](app-sdk-android.md#app-protection-policy-without-device-enrollment)一節 (如果您想從應用程式中的 MAM 服務取得原則)。

> [!NOTE]
> 嘗試從 [Intune App SDK for Android 開發人員指南](app-sdk-android.md)尋找 `Microsoft.Intune.MAM.Xamarin.Android` 繫結中的對等 API，或從該指南轉換程式碼片段時，請注意 Xamarin 的繫結產生器會以下列顯著的方式修改 Android API：
> * 所有識別碼都會轉換成 Pascal 命名法的大小寫 (com.foo.bar -> Com.Foo.Bar)
> * 所有 get/set 作業都會轉換成屬性作業 (例如 Foo.getBar() -> Foo.Bar、Foo.setBar("zap") -> Foo.Bar = "zap")
> * 所有介面的名稱前面都會加上 'I' 字元 (FooInterface -> IFooInterface)

### <a name="xamarinforms-integration"></a>Xamarin.Forms 整合

**除了執行所有上述步驟之外**，我們還針對 `Xamarin.Forms` 應用程式提供 `Microsoft.Intune.MAM.Remapper` 套件。 此套件會將 `MAM` 類別插入常用 `Xamarin.Forms` 類別 (例如 `FormsAppCompatActivity` 和 `FormsApplicationActivity`) 的類別階層中，為您完成類別取代，讓您可以透過提供 MAM 對等功能 (例如 `OnMAMCreate` 和 `OnMAMResume`) 的覆寫來繼續使用這些類別。 若要使用它，請執行下列操作：

1.  將 [Microsoft.Intune.MAM.Remapper.Tasks](https://www.nuget.org/packages/Microsoft.Intune.MAM.Remapper.Tasks) NuGet 套件新增至您的專案。 如果您尚未包含 Intune APP SDK Xamarin 繫結，則會自動新增繫結。

2.  在您於上述步驟 2.2 中建立之 `MAMApplication` 類別的 `OnMAMCreate` 函式中，新增對 `Xamarin.Forms.Forms.Init(Context, Bundle)` 的呼叫。 因為使用 Intune 管理時，應用程式可以在位於背景時啟動，所以需要這樣做。

> [!NOTE]
> 由於此作業會重寫 Visual Studio 用於 IntelliSense 自動完成的相依性，因此您可能需要在第一次執行 Remapper 之後重新啟動 Visual Studio，IntelliSense 才能正確辨識變更。 


## <a name="support"></a>支援

如果組織是現有的 Intune 客戶，請與您的 Microsoft 支援代表合作，[在 Github 問題頁面](https://github.com/msintuneappsdk/intune-app-sdk-xamarin/issues)上開啟支援票證並建立問題，我們將會儘快提供協助。 

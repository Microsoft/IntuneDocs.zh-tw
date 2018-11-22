---
title: Microsoft Intune App SDK Xamarin 繫結
description: 「Intune App SDK Xamarin 繫結」可讓您在以 Xamarin 建置的 iOS 和 Android 應用程式中啟用 Intune 應用程式保護原則。
keywords: sdk, Xamarin, intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/16/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 275d574b-3560-4992-877c-c6aa480717f4
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune
ms.openlocfilehash: 07fe31d8b668d14a51a5c31fa321e4789a0302c0
ms.sourcegitcommit: dec09e9c91322ca347276785aca3c50036956f32
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2018
ms.locfileid: "51859506"
---
# <a name="microsoft-intune-app-sdk-xamarin-bindings"></a>Microsoft Intune App SDK Xamarin 繫結

> [!NOTE]
> 您可能想要先閱讀 [Intune App SDK 快速入門](app-sdk-get-started.md)文章，其中說明如何在每個支援的平台上進行整合準備。

## <a name="overview"></a>概觀
[Intune App SDK Xamarin 繫結](https://github.com/msintuneappsdk/intune-app-sdk-xamarin)可讓您在以 Xamarin 建置的 iOS 和 Android 應用程式中啟用 [Intune 應用程式保護原則](app-protection-policy.md)。 繫結可讓開發人員輕鬆將 Intune 應用程式內的保護功能建置到以 Xamarin 為基礎的應用程式中。

「Microsoft Intune App SDK Xamarin 繫結」可讓您將 Intune 應用程式保護原則 (也稱為 APP 或 MAM 原則) 合併至以 Xamarin 開發的應用程式中。 啟用 MAM 的應用程式是與 Intune App SDK 整合的應用程式， IT 系統管理員可在 Intune 主動管理應用程式時，將應用程式保護原則部署至行動應用程式。

## <a name="whats-supported"></a>支援的項目

### <a name="developer-machines"></a>開發人員電腦
* Windows (Visual Studio 15.7+ 版本)
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

SDK 仰賴 [Active Directory 驗證程式庫 (ADAL)](https://azure.microsoft.com/documentation/articles/active-directory-authentication-libraries/) 進行[驗證](https://azure.microsoft.com/documentation/articles/active-directory-authentication-scenarios/)與條件式啟動案例，其中需要應用程式針對 [Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-whatis/) 進行設定。 

## <a name="enabling-intune-app-protection-polices-in-your-ios-mobile-app"></a>在 iOS 行動應用程式中啟用 Intune 應用程式保護原則
1. 將 [Microsoft.Intune.MAM.Xamarin.iOS NuGet 套件](https://www.nuget.org/packages/Microsoft.Intune.MAM.Xamarin.iOS)新增至 Xamarin.iOS 專案。
2.  請遵循將 Intune App SDK 整合至 iOS 行動應用程式所需的一般步驟。 您可以從 [Intune App SDK for iOS 開發人員指南](app-sdk-ios.md#build-the-sdk-into-your-mobile-app)之整合指示的步驟 3 開始。 您可以略過執行 IntuneMAMConfigurator 一節中的最後一個步驟，因為此工具隨附於 Microsoft.Intune.MAM.Xamarin.iOS 套件，並會在建置時間自動執行。
    **重要**：在 Visual Studio 中針對應用程式啟用金鑰鏈共用的方式與 Xcode 有些許不同。 開啟應用程式的 Entitlements plist，並確保 [啟用金鑰鏈] 選項已啟用，且已將適當的金鑰鏈共用群組新增至該區段。 接著，確保 Entitlements plist 已針對所有適當的設定/平台組合，指定於專案 [iOS 套件組合簽署] 選項的 [自訂權利] 欄位中。
3.  在新增繫結並正確設定應用程式之後，您的應用程式便可以開始使用 Intune SDK 的 API。 若要這麼做，您必須包含下列命名空間：

      ```csharp
      using Microsoft.Intune.MAM;
      ```
4. 若要開始接收應用程式保護原則，您的應用程式必須註冊至 Intune MAM 服務。 如果您的應用程式不會使用 [Azure Active Directory 驗證程式庫](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory) (ADAL) 或 [Microsoft 驗證程式庫](https://www.nuget.org/packages/Microsoft.Identity.Client) (MSAL) 來驗證使用者，而且您想要使用 Intune SDK 來處理驗證，則應用程式應該提供使用者 UPN 給 IntuneMAMEnrollmentManager 的 LoginAndEnrollAccount 方法：
      ```csharp
       IntuneMAMEnrollmentManager.Instance.LoginAndEnrollAccount([NullAllowed] string identity);
      ```
      如果在呼叫時使用者的 UPN 不明，則應用程式可能會傳入 Null。 在此情況下，系統會提示使用者輸入其電子郵件地址和密碼。
      
      如果您的應用程式已使用 ADAL 或 MSAL 來驗證使用者，則可以設定應用程式與 Intune SDK 之間的單一登入 (SSO) 體驗。 首先，您必須設定 ADAL/MSAL，將權杖儲存在 Intune Xamarin Bindings for iOS (com.microsoft.adalcache) 所使用的相同金鑰鏈存取群組中。 針對 ADAL，您可以[設定 AuthenticationContext 的 KeychainSecurityGroup 屬性](https://github.com/AzureAD/azure-activedirectory-library-for-dotnet/wiki/Token-cache-serialization#enable-token-cache-sharing-across-ios-applications)來執行這項作業。 針對 MSAL，您必須[設定 PublicClientApplication 的 KeychainSecurityGroup 屬性](https://github.com/AzureAD/microsoft-authentication-library-for-dotnet/wiki/msal-net-2-released#you-can-now-enable-sso-between-adal-and-msal-apps-on-xamarinios)。 接下來，您必須使用應用程式的預設 AAD 設定覆寫 Intune SDK 所使用的這些設定。 若要這麼做，您可以依 [Intune App SDK for iOS 開發人員指南](app-sdk-ios.md#configure-settings-for-the-intune-app-sdk)中所述的方式透過應用程式 Info.plist 中的 IntuneMAMSettings 目錄，或是使用 IntuneMAMPolicyManager 執行個體的 AAD 覆寫屬性來完成。 Info.plist 方法是針對 ADAL 設定為靜態之應用程式的建議選項，而覆寫屬性則是針對會於執行階段決定那些值之應用程式的建議選項。 一旦完成設定所有的 SSO 設定，您的應用程式就應該在成功驗證之後，將使用者的 UPN 提供給 IntuneMAMEnrollmentManager 的 RegisterAndEnrollAccount 方法：
      ```csharp
      IntuneMAMEnrollmentManager.Instance.RegisterAndEnrollAccount(string identity);
      ```
      應用程式可以在 IntuneMAMEnrollmentDelegate 的子類別中實作 EnrollmentRequestWithStatus 方法，並將 IntuneMAMEnrollmentManager 的 Delegate 屬性設定為該類別的執行個體，藉以判定註冊嘗試的結果。 請參閱我們的 [ Xamarin.iOS 應用程式範例](https://github.com/msintuneappsdk/sample-intune-xamarin-ios)以取得範例。

      註冊成功時，應用程式可以透過查詢下列屬性來判定已註冊帳戶的 UPN (如果之前不明的話)： 
      ```csharp
       string enrolledAccount = IntuneMAMEnrollmentManager.Instance.EnrolledAccount;
      ```      
> [!NOTE] 
> 沒有 iOS 的 Remapper。 整合到 Xamarin.Forms 應用程式應該與一般 Xamarin.iOS 專案相同。 

## <a name="enabling-intune-app-protection-policies-in-your-android-mobile-app"></a>在 Android 行動應用程式中啟用 Intune 應用程式保護原則

若為未使用 UI 架構且以 Xamarin 為基礎的 Android 應用程式，您必須閱讀並遵循 [Intune App SDK for Android 開發人員指南](app-sdk-android.md)。 針對您的 Xamarin 型 Android 應用程式，您必須根據指南中包含的[類別與方法取代表](app-sdk-android.md#class-and-method-replacements)，將類別、方法與活動取代為其 MAM 對等項目。 如果您的應用程式未定義 `android.app.Application` 類別，則需要建立一個，並確定繼承自 `MAMApplication`。 ADAL 設定值會透過 AndroidManifest 中繼資料傳送給 SDK。 請參閱[設定應用程式的 ADAL](app-sdk-android.md#configure-azure-active-directory-authentication-library-adal) 相關文件。

### <a name="xamarinandroid-integration"></a>Xamarin.Android 整合

1. 將最新版的 [Microsoft.Intune.MAM.Xamarin.Android NuGet 套件](https://www.nuget.org/packages/Microsoft.Intune.MAM.Xamarin.Android)新增至 Xamarin.Android 專案。 這會提供您 Intune 的必要參考來啟用應用程式。

2. 徹底閱讀並遵循 [Intune App SDK for Android 開發人員指南](app-sdk-android.md)，並特別注意：

    1. [完整類別和方法取代](app-sdk-android.md#class-and-method-replacements)一節。 
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

您已完成將元件建置成應用程式的基本步驟。 現在您可以依照 Xamarin Android 範例應用程式中的步驟。 我們提供了兩個範例，一個用於 Xamarin.Forms，另一個適用於 Android。

## <a name="requiring-intune-app-protection-policies-in-order-to-use-your-xamarin-based-android-lob-app-optional"></a>需要 Intune 應用程式保護原則才能使用以 Xamarin 為基礎的 Android LOB 應用程式 (選擇性) 

下列是確保以 Xamarin 為基礎的 Android LOB 應用程式僅供受 Intune 保護之使用者在其裝置上使用的指南。 

### <a name="general-requirements"></a>一般需求
* 確定將您的 Xamarin 應用程式權限授與應用程式保護原則 (APP) 服務的步驟是允許的。 使用[開始使用 Intune SDK 指南](app-sdk-get-started.md#next-steps-after-integration)中＜將您的應用程式存取權授與 Intune 應用程式保護服務 (選擇性)＞中的指示。 
    
### <a name="working-with-the-intune-sdk"></a>使用 Intune SDK
這些指示專門針對所有想要在使用者裝置上使用 Intune 應用程式保護原則的 Android 和 Xamarin 應用程式。

1. 使用 [Intune SDK for Android 指南](app-sdk-android.md#configure-azure-active-directory-authentication-library-adal)中定義的步驟設定 ADAL。
> [!NOTE] 
> 「用戶端識別碼」一詞，和繫結於您應用程式之 Azure 入口網站中的「應用程式識別碼」一詞相同。 
* 若要啟用 SSO，需要「一般 ADAL 設定」#2。

2. 將下列值放在資訊清單中以啟用預設註冊：```xml <meta-data android:name="com.microsoft.intune.mam.DefaultMAMServiceEnrollment" android:value="true" />```
> [!NOTE] 
> 這必須是應用程式中唯一的 MAM-WE 整合。 如有呼叫 MAMEnrollmentManager API 的任何其他嘗試，可能會發生衝突。

3. 將下列值放在資訊清單中以啟用所需的 MAM：```xml <meta-data android:name="com.microsoft.intune.mam.MAMPolicyRequired" android:value="true" />```
> [!NOTE] 
> 這會強制應用程式將公司入口網站下載到裝置上，在使用前完成預設註冊流程。

### <a name="working-with-adal"></a>使用 ADAL
這些指示是 .NET/Xamarin 應用程式的需求，這些應用程式希望在終端使用者裝置上使用 Intune 應用程式保護原則。

1. 請遵循[Brokered Authentication for Android](https://github.com/AzureAD/azure-activedirectory-library-for-dotnet/tree/dev/adal#brokered-authentication-for-android) (適用於 Android 的代理驗證) 下 ADAL 文件中定義的所有步驟。
> [!NOTE] 
> .NET ADAL 將釋出的下一個版本 (3.17.4) 預期會包含使其運作所需的修正。

## <a name="support"></a>支援
如果組織是現有的 Intune 客戶，請與您的 Microsoft 支援代表合作，[在 Github 問題頁面](https://github.com/msintuneappsdk/intune-app-sdk-xamarin/issues)上開啟支援票證並建立問題，我們將會儘快提供協助。 

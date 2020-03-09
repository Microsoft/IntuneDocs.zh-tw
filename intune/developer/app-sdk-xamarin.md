---
title: Microsoft Intune App SDK Xamarin 繫結
description: 「Intune App SDK Xamarin 繫結」可讓您在以 Xamarin 建置的 iOS 和 Android 應用程式中啟用 Intune 應用程式保護原則。
keywords: sdk, Xamarin, intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/28/2020
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: developer
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 275d574b-3560-4992-877c-c6aa480717f4
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune
ms.collection: M365-identity-device-management
ms.openlocfilehash: 183cc5ed233de4a3285cf5cfd3290aead9c1de72
ms.sourcegitcommit: 9ee2401a2f01373a962749b0728c22385dbcba6d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/29/2020
ms.locfileid: "78181903"
---
# <a name="microsoft-intune-app-sdk-xamarin-bindings"></a>Microsoft Intune App SDK Xamarin 繫結

> [!NOTE]
> 您可能想要先閱讀 [Intune App SDK 快速入門](app-sdk-get-started.md)文章，其中說明如何在每個支援的平台上進行整合準備。

## <a name="overview"></a>概觀
[Intune App SDK Xamarin 繫結](https://github.com/msintuneappsdk/intune-app-sdk-xamarin)可讓您在以 Xamarin 建置的 iOS 和 Android 應用程式中啟用 [Intune 應用程式保護原則](../apps/app-protection-policy.md)。 繫結可讓開發人員輕鬆將 Intune 應用程式內的保護功能建置到以 Xamarin 為基礎的應用程式中。

「Microsoft Intune App SDK Xamarin 繫結」可讓您將 Intune 應用程式保護原則 (也稱為 APP 或 MAM 原則) 合併至以 Xamarin 開發的應用程式中。 啟用 MAM 的應用程式是與 Intune App SDK 整合的應用程式。 IT 系統管理員可在 Intune 主動管理應用程式時，將應用程式保護原則部署至行動應用程式。

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

## <a name="prerequisites"></a>先決條件

檢閱[授權條款](https://github.com/msintuneappsdk/intune-app-sdk-xamarin/blob/master/Microsoft%20License%20Terms%20Intune%20App%20SDK%20Xamarin%20Component.pdf)。 列印並保留一份授權條款供您備查。 下載並使用「Intune App SDK Xamarin 繫結」即表示您同意這些授權條款。 如果您不接受這些條款，請不要使用此軟體。

Intune SDK 依賴 [Active Directory 驗證程式庫 (ADAL)](https://azure.microsoft.com/documentation/articles/active-directory-authentication-libraries/) \(部分機器翻譯\) 進行其[驗證](https://azure.microsoft.com/documentation/articles/active-directory-authentication-scenarios/) \(部分機器翻譯\) 與條件式啟動情節，在這些情況下，必須為應用程式設定 [Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-whatis/)。 

如果您的應用程式已設定為使用 ADAL 或 MSAL，且具有自己的自訂用戶端識別碼來用以向 Azure Active Directory 進行驗證，則請務必遵循步驟為 Intune 行動應用程式管理 (MAM) 服務提供您的 Xamarin 應用程式權限。 使用[開始使用 Intune SDK 指南](app-sdk-get-started.md)的＜[將您的應用程式存取權授與 Intune 應用程式保護服務](app-sdk-get-started.md#give-your-app-access-to-the-intune-app-protection-service-optional)＞一節中的指示。

## <a name="security-considerations"></a>安全性考量

若要防止潛在的詐騙、資訊洩漏和權限提升攻擊：

* 確保 Xamarin 應用程式開發是在安全的工作工作站上進行。
* 確保繫結來自有效的 Microsoft 來源：
  * [MS Intune App SDK NuGet 設定檔](https://www.nuget.org/profiles/msintuneappsdk) \(英文\)
  * [Intune App SDK Xamarin GitHub 存放庫](https://github.com/msintuneappsdk/intune-app-sdk-xamarin) \(英文\)
* 將您專案的 NuGet 設定設為信任已簽署、未修改的 NuGet 套件。
如需詳細資訊，請參閱[安裝已簽署的套件](https://docs.microsoft.com/nuget/consume-packages/installing-signed-packages)。
* 保護包含 Xamarin 應用程式的輸出目錄。 考慮針對輸出使用使用者層級目錄。


## <a name="enabling-intune-app-protection-polices-in-your-ios-mobile-app"></a>在 iOS 行動應用程式中啟用 Intune 應用程式保護原則
1. 將 [Microsoft.Intune.MAM.Xamarin.iOS NuGet 套件](https://www.nuget.org/packages/Microsoft.Intune.MAM.Xamarin.iOS)新增至 Xamarin.iOS 專案。
2. 請遵循將 Intune App SDK 整合至 iOS 行動應用程式所需的一般步驟。 您可以從 [Intune App SDK for iOS 開發人員指南](app-sdk-ios.md#build-the-sdk-into-your-mobile-app)之整合指示的步驟 3 開始。 您可以略過執行 IntuneMAMConfigurator 一節中的最後一個步驟，因為此工具隨附於 Microsoft.Intune.MAM.Xamarin.iOS 套件，並會在建置時間自動執行。
    **重要**：在 Visual Studio 中針對應用程式啟用金鑰鏈共用的方式與 Xcode 有些許不同。 開啟應用程式的 Entitlements plist，並確保 [啟用金鑰鏈] 選項已啟用，且已將適當的金鑰鏈共用群組新增至該區段。 接著，確保 Entitlements plist 已針對所有適當的設定/平台組合，指定於專案 [iOS 套件組合簽署] 選項的 [自訂權利] 欄位中。
3. 在新增繫結並正確設定應用程式之後，您的應用程式便可以開始使用 Intune SDK 的 API。 若要這麼做，您必須包含下列命名空間：

      ```csharp
      using Microsoft.Intune.MAM;
      ```

4. 若要開始接收應用程式保護原則，您的應用程式必須註冊至 Intune MAM 服務。 如果您的應用程式不會使用 [Azure Active Directory 驗證程式庫](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory) (ADAL) 或 [Microsoft 驗證程式庫](https://www.nuget.org/packages/Microsoft.Identity.Client) (MSAL) 來驗證使用者，而且您想要使用 Intune SDK 來處理驗證，則應用程式應該提供使用者 UPN 給 IntuneMAMEnrollmentManager 的 LoginAndEnrollAccount 方法：

      ```csharp
       IntuneMAMEnrollmentManager.Instance.LoginAndEnrollAccount([NullAllowed] string identity);
      ```

      如果在呼叫時使用者的 UPN 不明，則應用程式可能會傳入 Null。 在此情況下，系統會提示使用者輸入其電子郵件地址和密碼。
      
      如果您的應用程式已使用 ADAL 或 MSAL 來驗證使用者，則可以設定應用程式與 Intune SDK 之間的單一登入 (SSO) 體驗。 首先，您必須使用應用程式的預設 AAD 設定覆寫 Intune SDK 所使用的這些設定。 若要這麼做，您可以依 [Intune App SDK for iOS 開發人員指南](app-sdk-ios.md#configure-settings-for-the-intune-app-sdk)中所述的方式透過應用程式 Info.plist 中的 IntuneMAMSettings 目錄，或是使用 IntuneMAMSettings 的 AAD 覆寫屬性來完成。 Info.plist 方法是針對 ADAL 設定為靜態之應用程式的建議選項，而覆寫屬性則是針對會於執行階段決定那些值之應用程式的建議選項。 一旦完成設定所有的 SSO 設定，您的應用程式就應該在成功驗證之後，將使用者的 UPN 提供給 IntuneMAMEnrollmentManager 的 RegisterAndEnrollAccount 方法：

      ```csharp
      IntuneMAMEnrollmentManager.Instance.RegisterAndEnrollAccount(string identity);
      ```

      應用程式可以在 IntuneMAMEnrollmentDelegate 的子類別中實作 EnrollmentRequestWithStatus 方法，並將 IntuneMAMEnrollmentManager 的 Delegate 屬性設定為該類別的執行個體，藉以判定註冊嘗試的結果。 

      註冊成功時，應用程式可以透過查詢下列屬性來判定已註冊帳戶的 UPN (如果之前不明的話)： 

      ```csharp
       string enrolledAccount = IntuneMAMEnrollmentManager.Instance.EnrolledAccount;
      ```      
### <a name="sample-applications"></a>範例應用程式
強調 Xamarin.iOS 應用程式中 MAM 功能的應用程式範例可在 [GitHub](https://github.com/msintuneappsdk/sample-intune-xamarin-ios) \(英文\) 找到。

> [!NOTE] 
> 沒有 iOS/iPadOS 的重新對應程式。 整合到 Xamarin.Forms 應用程式應該與一般 Xamarin.iOS 專案相同。 

## <a name="enabling-intune-app-protection-policies-in-your-android-mobile-app"></a>在 Android 行動應用程式中啟用 Intune 應用程式保護原則
1. 將 [Microsoft.Intune.MAM.Xamarin.Android NuGet 套件](https://www.nuget.org/packages/Microsoft.Intune.MAM.Xamarin.Android)新增至 Xamarin.Android 專案。
    1. 針對 Xamarin.Forms 應用程式，也新增 [Microsoft.Intune.MAM.Remapper.Tasks NuGet 套件](https://www.nuget.org/packages/Microsoft.Intune.MAM.Remapper.Tasks)至您的 Xamarin.Android 專案。 
2. 請遵循[整合 Intune App SDK](app-sdk-android.md) 到 Android 行動應用程式所需的一般步驟，同時參考本文件的其他詳細資料。

### <a name="xamarinandroid-integration"></a>Xamarin.Android 整合

整合 Intune App SDK 的完整概觀位於 [Microsoft Intune App SDK for Android 開發人員指南](app-sdk-android.md)。 當您閱讀本指南並整合 Intune App SDK 與 Xamarin 應用程式時，下列各節旨在強調以 Java 開發的原生 Android 應用程式與以 C# 開發的 Xamarin 應用程式兩者之間差異。 這些區段應該視為補充，無法取代閱讀完整的指南。

#### <a name="remapper"></a>Remapper
從 1.4428.1 版開始，您可以將 `Microsoft.Intune.MAM.Remapper` 套件新增至 Xamarin.Android 應用程式，作為[建置工具](app-sdk-android.md#build-tooling)來執行 MAM 類別、方法和系統服務取代。 如果包含 Remapper，就會在建立應用程式時自動執行已重新命名方法和 MAM 應用程式區段的 MAM 對等取代部分。

若要使用 Remapper 排除來自 MAM-ification 的類別，您可以將下列屬性新增到專案 `.csproj` 檔案。

```xml
  <PropertyGroup>
    <ExcludeClasses>Semicolon separated list of relative class paths to exclude from MAM-ification</ExcludeClasses>
  </PropertyGroup>
```

> [!NOTE]
> Remapper 目前會防止在 Xamarin. Android 應用程式中進行偵錯。 建議進行手動整合，以對您的應用程式進行偵錯。

#### <a name="renamed-methods"></a>[重新命名的方法](app-sdk-android.md#renamed-methods)
在許多情況下，Android 類別中可用的方法已在 MAM 取代類別中被標示為完稿。 在此情況下，MAM 取代類別會提供您應該覆寫且具有類似名稱的方法 (名稱具有 `MAM` 尾碼)。 例如，當衍生自 `MAMActivity`，而不是覆寫 `OnCreate()` 然後呼叫 `base.OnCreate()` 時，`Activity` 必須覆寫 `OnMAMCreate()` 並呼叫 `base.OnMAMCreate()`。

#### <a name="mam-application"></a>[MAM 應用程式](app-sdk-android.md#mamapplication)
您的應用程式必須定義 `Android.App.Application` 類別。 如果手動整合 MAM，其必須繼承自 `MAMApplication`。 確定您的子類別已正確地使用 `[Application]` 屬性加以裝飾，並覆寫 `(IntPtr, JniHandleOwnership)` 建構函式。

```csharp
    [Application]
    class TaskrApp : MAMApplication
    {
    public TaskrApp(IntPtr handle, JniHandleOwnership transfer)
        : base(handle, transfer) { }
```

> [!NOTE]
> MAM Xamarin 繫結的問題可能導致在偵錯模式部署應用程式時，應用程式損毀。 因應措施就是，`Debuggable=false` 屬性必須新增至 `Application` 類別，而 `android:debuggable="true"` 旗標必須從資訊清單移除 (如果以手動方式設定)。

#### <a name="enable-features-that-require-app-participation"></a>[啟用需要應用程式參與的功能](app-sdk-android.md#enable-features-that-require-app-participation)
範例：判斷應用程式是否需要 PIN

```csharp
MAMPolicyManager.GetPolicy(currentActivity).IsPinRequired;
```

範例：判斷主要 Intune 使用者

```csharp
IMAMUserInfo info = MAMComponents.Get<IMAMUserInfo>();
return info?.PrimaryUser;
```

範例：判斷是否允許儲存至裝置或雲端儲存體

```csharp
MAMPolicyManager.GetPolicy(currentActivity).GetIsSaveToLocationAllowed(SaveLocation service, String username);
```

#### <a name="register-for-notifications-from-the-sdk"></a>[從 SDK 註冊通知](app-sdk-android.md#register-for-notifications-from-the-sdk)
您的應用程式必須建立 `MAMNotificationReceiver`，並向 `MAMNotificationReceiverRegistry` 進行註冊，才能從 SDK 註冊通知。 這是藉由提供接收者以及想要在 `App.OnMAMCreate` 中接收的通知類型來完成，如下列範例所示：

```csharp
public override void OnMAMCreate()
{
    // Register the notification receivers
    IMAMNotificationReceiverRegistry registry = MAMComponents.Get<IMAMNotificationReceiverRegistry>();
    foreach (MAMNotificationType notification in MAMNotificationType.Values())
    {
        registry.RegisterReceiver(new ToastNotificationReceiver(this), notification);
    }
    ...
```

#### <a name="mam-enrollment-manager"></a>[MAM 註冊管理員](app-sdk-android.md#mamenrollmentmanager)

```csharp
IMAMEnrollmentManager mgr = MAMComponents.Get<IMAMEnrollmentManager>();
```

### <a name="xamarinforms-integration"></a>Xamarin.Forms 整合

針對 `Xamarin.Forms` 應用程式，`Microsoft.Intune.MAM.Remapper` 套件會透過將 `MAM` 類別插入到常用 `Xamarin.Forms` 類別的類別階層，自動執行 MAM 類別取代。 

> [!NOTE]
> 除了完成以上詳述的 Xamarin.Android 整合，也必須進行 Xamarin.Forms 整合。 針對 Xamarin 應用程式，Remapper 的行為有所不同，因此必須完成手動 MAM 取代。

一旦 Remapper 新增至您的專案，您必須執行 MAM 對等取代。 例如，`FormsAppCompatActivity` 和 `FormsApplicationActivity` 可以繼續用於您提供的應用程式，假設 `OnCreate` 和 `OnResume` 的覆寫分別取代為 MAM 對等項目 `OnMAMCreate` 和 `OnMAMResume`。

```csharp
    public class MainActivity : global::Xamarin.Forms.Platform.Android.FormsAppCompatActivity
    {
        protected override void OnMAMCreate(Bundle savedInstanceState)
        {
            base.OnMAMCreate(savedInstanceState);
            global::Xamarin.Forms.Forms.Init(this, savedInstanceState);
            LoadApplication(new App());
        }
```

如果不進行取代，則您可能在進行取代之前會遇到下列編譯錯誤：
* [編譯器錯誤 CS0239](https://docs.microsoft.com/dotnet/csharp/misc/cs0239)。 此錯誤通常是這種形式 ``'MainActivity.OnCreate(Bundle)': cannot override inherited member 'MAMAppCompatActivityBase.OnCreate(Bundle)' because it is sealed``。
預期出現這種狀況是因為當重新對應程式修改 Xamarin 類別的繼承時，某些函式將被設定為 `sealed` 且會改為新增 MAM 變數以覆寫。
* [編譯器錯誤 CS0507](https://docs.microsoft.com/dotnet/csharp/language-reference/compiler-messages/cs0507)：此錯誤通常是這種形式 ``'MyActivity.OnRequestPermissionsResult()' cannot change access modifiers when overriding 'public' inherited member ...``。 當重新對應程式變更一些 Xamarin 類別的繼承時，特定成員函式將會變更為 `public`。 若您覆寫這些函式中的任何函式，您也必須將那些覆寫的存取修飾詞也變更為 `public`。

> [!NOTE]
> Remapper 會重寫 Visual Studio 用於 IntelliSense 自動完成的相依性。 因此，新增 Remapper 時您可能需要重新載入並重建專案，IntelliSense 才能正確識別變更。

#### <a name="troubleshooting"></a>疑難排解
* 如果您的應用程式在啟動時遇到空白的白色畫面，您可能需要在主執行緒上強制執行導覽呼叫。
* Intune SDK Xamarin 繫結不支援使用跨平台架構 (例如 MvvmCross) 的應用程式，因為 MvvmCross 與 Intune MAM 類別之間的衝突。 雖然有些客戶在將應用程式移至純 Xamarin.Forms 後已成功整合，但我們不會為使用 MvvmCross 的應用程式開發人員提供明確的指導方針或外掛程式。

### <a name="company-portal-app"></a>公司入口網站應用程式
Intune SDK Xamarin 繫結必須仰賴裝置上的[公司入口網站](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal) Android 應用程式來啟用應用程式保護原則。 公司入口網站會從 Intune 服務擷取應用程式保護原則。 應用程式初始化時，它會載入原則和程式碼，以從公司入口網站強制執行該原則。 使用者不需要登入。

> [!NOTE]
> 當 **Android** 裝置上沒有公司入口網站應用程式時，由 Intune 管理的應用程式會具有和不支援 Intune 應用程式保護原則的一般應用程式相同的行為。

對於沒有裝置註冊的應用程式保護，使用者「不」 __ 需要使用公司入口網站應用程式註冊裝置。

### <a name="sample-applications"></a>範例應用程式
強調 Xamarin.Android 和 Xamarin.Forms 應用程式中 MAM 功能的應用程式範例可在 [GitHub](https://github.com/msintuneappsdk/Taskr-Sample-Intune-Xamarin-Android-Apps) \(英文\) 找到。

## <a name="support"></a>支援
如果您的組織是現有 Intune 客戶，請與您的 Microsoft 支援代表合作以建立支援票證，並[在 GitHub 問題頁面](https://github.com/msintuneappsdk/intune-app-sdk-xamarin/issues)上建立問題。 我們會儘快提供協助。 

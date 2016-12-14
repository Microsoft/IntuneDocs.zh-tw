---
title: "針對行動應用程式管理準備應用程式 | Microsoft Intune"
description: "本主題中的資訊可協助您決定使用 App Wrapping Tool 和 App SDK 時機，以讓您的自訂企業營運應用程式得以使用行動應用程式管理原則。"
keywords: 
author: mtillman
ms.author: mtillman
manager: angrobe
ms.date: 09/13/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 29e22121-8268-48b5-a671-f940a6be1d24
ms.reviewer: oldang
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ee7e0491c0635c45cbc0377a5de01d5eba851132
ms.openlocfilehash: 3d7b60862942742d663ff23c7b5f3fd135c72640


---

# <a name="decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune"></a>決定如何準備應用程式以使用 Microsoft Intune 進行行動應用程式管理
您可以使用 Intune App Wrapping Tool 或 Intune App SDK，讓應用程式使用行動應用程式管理 (MAM) 原則。 使用這項資訊可了解這兩種方法和其使用時機。

## <a name="intune-app-wrapping-tool"></a>Intune App Wrapping Tool
App Wrapping Tool 主要用於內部企業營運 (LOB) 應用程式。 此工具是可建立應用程式包裝函式的命令列應用程式，因而可讓 Intune MAM 原則管理應用程式。

您不需要原始程式碼即可使用工具，但需要簽署認證。  如需簽署認證的詳細資訊，請參閱 [Intune 部落格](https://blogs.technet.microsoft.com/enterprisemobility/2015/02/25/how-to-obtain-the-prerequisites-for-the-intune-app-wrapping-tool-for-ios/)。 如需 App Wrapping Tool 文件，請參閱 [Android App Wrapping Tool](prepare-android-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool.md) 和 [iOS App Wrapping Tool](prepare-ios-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool.md)。

應用程式包裝工具**不**支援 Apple App Store 或 Google Play 商店中的應用程式。 它也不支援某些需要開發人員整合的功能 (請參閱下列的功能比較表)。


如需 Intune 中未註冊裝置上之 App Wrapping Tool for MAM 的詳細資訊，請參閱[保護未在 Microsoft Intune 註冊之裝置上的企業營運應用程式和資料](protect-line-of-business-apps-and-data-on-devices-not-enrolled-in-microsoft-intune.md)。

### <a name="reasons-to-use-the-app-wrapping-tool"></a>使用 App Wrapping Tool 的原因：
* 您的 App 沒有內建資料保護功能。
* 您的 App 很簡單。
* 您的 App 部署於內部。
* 您沒有 App 原始程式碼的存取權限
* 您並未開發該 App。
* 您的 App 具有最低的使用者驗證體驗。


### <a name="supported-app-development-platforms"></a>支援的應用程式開發平台

|**App Wrapping Tool** | **Xamarin** |**Cordova** |
|------|----|----|
|**iOS** |是|是|
|**Android**| 否 |是|

## <a name="intune-app-sdk"></a>Intune App SDK
App SDK 的設計主要是針對 Apple App Store 或 Google Play Store 中具有應用程式並想要可以使用 Intune 管理應用程式的客戶。 不過，任何應用程式都可以利用 SDK 的整合，即使它是企業營運應用程式也是一樣。

若要深入了解 SDK，請參閱[概觀](/intune/develop/intune-app-sdk)。 若要開始使用 SDK，請參閱[開始使用 Microsoft Intune App SDK](/intune/develop/intune-app-sdk-get-started)。

### <a name="reasons-to-use-the-sdk"></a>使用 SDK 的理由
* 您的 App 沒有內建資料保護功能。
* 您的 App 很複雜，且包含許多體驗。
* 您的 App 會部署在公開的應用程式商店，例如 Google Play 或 Apple 的 App Store。
* 您是 App 開發人員，並且有使用 SDK 的技術背景。
* 您的 App 有其他的 SDK 整合。
* 您的 App 經常更新。

### <a name="supported-app-development-platforms"></a>支援的應用程式開發平台

|**Intune App SDK** |**Xamarin** |**Cordova**
|------|----|----|
|**iOS**|是，使用 [Intune App SDK Xamarin 元件](/../develop/intune-app-sdk-xamarin)。|是，使用 [Intune App SDK Cordova 外掛程式](/../develop/intune-app-sdk-cordova)。|
|**Android**| 是，使用 [Intune App SDK Xamarin 元件](/../develop/intune-app-sdk-xamarin)。|是，使用 [Intune App SDK Cordova 外掛程式](/../develop/intune-app-sdk-cordova)。|

## <a name="feature-comparison"></a>功能比較
此表格列出您可以用於 App SDK 和 App Wrapping Tool 的設定。

> [!NOTE]
> 只有在使用 Intune 獨立版或 Intune (含 Configuration Manager) 時，才能使用 App Wrapping Tool。

|功能|App SDK|App Wrapping Tool|
|-----------|---------------------|-----------|
|限制要在公司管理的瀏覽器中顯示網頁內容|X|X|
|禁止 Android、iTunes 或 iCloud 備份|X|X|
|允許應用程式將資料傳送到其他應用程式|X|X|
|允許應用程式接收來自其他應用程式的資料|X|X|
|限制與其他應用程式的剪下、複製和貼上|X|X|
|需要簡單的 PIN 碼才能存取|X|X|
|將內建應用程式 PIN 取代為 Intune PIN|X||
|指定 PIN 重設之前的嘗試次數|X|X|
|允許指紋而非 PIN |X|X|
|需要公司認證才能存取|X|X|
|封鎖受管理的應用程式在已進行 JB 或 Root 破解的裝置上執行|X|X|
|加密應用程式資料|X|X|
|在指定的分鐘數之後重新檢查存取需求|X|X|
|指定離線寬限期|X|X|
|封鎖螢幕擷取 (僅限 Android)|X|X|
|完整抹除|X|X|
|選擇性抹除 <br></br>**注意：**對於 iOS，移除管理設定檔時，也會移除應用程式。|X||
|避免「另存新檔」 |X||
|支援多重身分識別|X||
|不註冊裝置的 MAM 支援|X|X|
|可自訂樣式 |X|||
### <a name="see-also"></a>請參閱

[Android App Wrapping Tool](prepare-android-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool.md)</br>
[iOS App Wrapping Tool](prepare-ios-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool.md)</br>
[使用 SDK 讓應用程式進行行動應用程式管理](use-the-sdk-to-enable-apps-for-mobile-application-management.md)



<!--HONumber=Dec16_HO2-->



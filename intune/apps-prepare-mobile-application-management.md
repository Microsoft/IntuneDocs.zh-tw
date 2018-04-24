---
title: 準備應用程式防護原則的企業營運應用程式
titlesuffix: Microsoft Intune
description: 您可以使用 App Wrapping Tool 與 App SDK 來啟用自訂的企業營運應用程式，以在 Microsoft Intune 中使用應用程式防護原則。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/24/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 29e22121-8268-48b5-a671-f940a6be1d24
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: d61ba21ba465037fbf2ef4e1c7423f6649fc810f
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="prepare-line-of-business-apps-for-app-protection-policies"></a>準備應用程式防護原則的企業營運應用程式

[!INCLUDE [both-portals](./includes/note-for-both-portals.md)]

您可以使用 Intune App Wrapping Tool 或 Intune App SDK，讓應用程式使用應用程式保護原則。 使用這項資訊可了解這兩種方法和其使用時機。

## <a name="intune-app-wrapping-tool"></a>Intune App Wrapping Tool
App Wrapping Tool 主要用於內部企業營運 (LOB) 應用程式。 此工具是可建立應用程式包裝函式的命令列應用程式，因而可讓 Intune 應用程式保護原則管理應用程式。

您不需要原始程式碼即可使用工具，但需要簽署認證。 如需簽署認證的詳細資訊，請參閱 [Intune 部落格](https://blogs.technet.microsoft.com/enterprisemobility/2015/02/25/how-to-obtain-the-prerequisites-for-the-intune-app-wrapping-tool-for-ios/)。 如需 App Wrapping Tool 文件，請參閱 [Android App Wrapping Tool](app-wrapper-prepare-android.md) 和 [iOS App Wrapping Tool](app-wrapper-prepare-ios.md)。

應用程式包裝工具**不**支援 Apple App Store 或 Google Play 商店中的應用程式。 它也不支援某些需要開發人員整合的功能 (請參閱下列的功能比較表)。


如需 Intune 中未註冊裝置上應用程式保護原則之 App Wrapping Tool 的詳細資訊，請參閱[保護未在 Microsoft Intune 註冊之裝置上的企業營運應用程式和資料](/intune-classic/deploy-use/protect-line-of-business-apps-and-data-on-devices-not-enrolled-in-microsoft-intune)。

### <a name="reasons-to-use-the-app-wrapping-tool"></a>使用 App Wrapping Tool 的原因
* 您的應用程式沒有內建資料保護功能
* 您的應用程式很簡單
* 您的應用程式部署於內部
* 您沒有 App 原始程式碼的存取權限
* 您未開發應用程式
* 您的應用程式具有最低的使用者驗證體驗


### <a name="supported-app-development-platforms"></a>支援的應用程式開發平台

|**App Wrapping Tool** | **Xamarin** |**Cordova** |
|------|----|----|
|**iOS** |是|是|
|**Android**| 預覽中 |是|

## <a name="intune-app-sdk"></a>Intune App SDK
App SDK 的設計主要是針對 Apple App Store 或 Google Play Store 中具有應用程式並想要可以使用 Intune 管理應用程式的客戶。 不過，任何應用程式都可以利用 SDK 的整合，即使它是企業營運應用程式也是一樣。

若要深入了解 SDK，請參閱[概觀](app-sdk.md)。 若要開始使用 SDK，請參閱[開始使用 Microsoft Intune App SDK](app-sdk-get-started.md)。

### <a name="reasons-to-use-the-sdk"></a>使用 SDK 的理由
* 您的應用程式沒有內建資料保護功能
* 您的應用程式很複雜且包含許多體驗
* 您的應用程式部署在公開應用程式商店 (例如 Google Play 或 Apple 的 App Store)
* 您是應用程式開發人員並且擁有使用 SDK 的技術背景
* 您的應用程式有其他的 SDK 整合
* 您的應用程式經常更新

### <a name="supported-app-development-platforms"></a>支援的應用程式開發平台

|**Intune App SDK** |**Xamarin** |**Cordova**
|------|----|----|
|**iOS**|是 - 使用 [Intune App SDK Xamarin 繫結](app-sdk-xamarin.md)。|是 - 使用 [Intune App SDK Cordova 外掛程式](app-sdk-cordova.md)。|
|**Android**| 是 - 使用 [Intune App SDK Xamarin 繫結](app-sdk-xamarin.md)。|是 - 使用 [Intune App SDK Cordova 外掛程式](app-sdk-cordova.md)。|

## <a name="feature-comparison"></a>功能比較
此表格列出您可以用於 App SDK 和 App Wrapping Tool 的設定。

> [!NOTE]
> 只有在使用 Intune 獨立版或 Intune (含 Configuration Manager) 時，才能使用 App Wrapping Tool。

|                                                         功能                                                          | App SDK | App Wrapping Tool |
|--------------------------------------------------------------------------------------------------------------------------|---------|-------------------|
|                              限制要在公司管理的瀏覽器中顯示網頁內容                              |    X    |         X         |
|                                        禁止 Android、iTunes 或 iCloud 備份                                        |    X    |         X         |
|                                         允許應用程式將資料傳送到其他應用程式                                         |    X    |         X         |
|                                        允許應用程式接收來自其他應用程式的資料                                         |    X    |         X         |
|                                      限制利用其他應用程式剪下、複製及貼上                                       |    X    |         X         |
|                                              需要簡單的 PIN 碼才能存取                                               |    X    |         X         |
|                                         將內建應用程式 PIN 取代為 Intune PIN                                         |    X    |                   |
|                                     指定 PIN 重設之前的嘗試次數                                      |    X    |         X         |
|                                             允許指紋而非 PIN                                             |    X    |         X         |
|                                         需要公司認證才能存取                                         |    X    |         X         |
|                             封鎖受管理的應用程式在已進行 JB 或 Root 破解的裝置上執行                              |    X    |         X         |
|                                                     加密應用程式資料                                                     |    X    |         X         |
|                           在指定的分鐘數之後重新檢查存取需求                            |    X    |         X         |
|                                             指定離線寬限期                                             |    X    |         X         |
|                                           封鎖螢幕擷取 (僅限 Android)                                            |    X    |         X         |
|                                        不註冊裝置的 MAM 支援                                         |    X    |         X         |
|                                                        完整抹除                                                         |    X    |         X         |
| 選擇性抹除 <br></br><strong>注意：</strong>對於 iOS，移除管理設定檔時，也會移除應用程式。 |    X    |                   |
|                                                    避免「另存新檔」                                                     |    X    |                   |
|                                            目標應用程式組態                                            |    X    |                   |
|                                                支援多重身分識別                                                |    X    |                   |
|                                                    可自訂樣式                                                    |    X    |                   |

## <a name="next-steps"></a>接下來的步驟

若要深入了解應用程式保護原則和 Intune，請參閱下列主題：

  -  [Android App Wrapping Tool](app-wrapper-prepare-android.md)</br>
  - [iOS App Wrapping Tool](app-wrapper-prepare-ios.md)</br>
  - [使用 SDK 讓應用程式進行行動應用程式管理](/intune-classic/deploy-use/use-the-sdk-to-enable-apps-for-mobile-application-management)

---
title: 為 iOS 裝置建立應用程式通知 - Microsoft Intune - Azure | Microsoft Docs
description: 在 Microsoft Intune 中為 iOS 裝置新增或建立應用程式通知。 選擇要傳送通知的目標應用程式、設定鎖定畫面上的通知設定、啟用音效、選擇警示類型及新增徽章。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/07/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: bda26d1d-2a3b-4669-adf8-a5aa7f994916
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 43068163c15c0588a8a6ef745d5b191f4547a94d
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="configure-app-notifications-settings-on-ios-devices-in-intune"></a>在 Intune 中為 iOS 裝置設定應用程式通知

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

設定安裝在 iOS 裝置上的應用程式如何傳送通知。 這些設定支援執行 iOS 9.3 及更新版本的受監督裝置。

## <a name="add-the-app-notification"></a>新增應用程式通知

1. 登入 [Azure 入口網站](https://portal.azure.com)。
2. 在您的 iOS 或 macOS 設定檔中，選取 [裝置功能]。 [iOS 或 macOS 裝置功能](device-features-configure.md) 會列出建立設定檔的步驟。
3. 選取 [應用程式通知 (限受監督)]，然後選取 [新增]：![在 Intune 中的 iOS 或 macOS 新增應用程式通知](./media/ios-macos-app-notifications.png)
4. 輸入下列內容：

   - **應用程式套件組合識別碼**：輸入您要設定之應用程式的**應用程式套件組合識別碼**。 **內建的 iOS 應用程式套件組合識別碼參考** (本文中) 會提供一些說明。
   - **應用程式名稱**：輸入您要設定之應用程式的名稱。 此名稱不會顯示在裝置上，而是用來協助您識別清單中的應用程式。
   - **發行者**：輸入您要設定之應用程式的發行者。 此發行者名稱不會顯示在裝置上，而是僅用來協助您識別清單中的應用程式。
   - **通知**：啟用或停用應用程式傳送通知到裝置的功能。 如果您停用這項設定，則也會停用下列設定。
     - **在通知中心顯示**：啟用此設定讓應用程式在裝置的「通知中心」內顯示通知。
     - **在鎖定畫面顯示**：啟用此設定以便在裝置鎖定畫面上查看應用程式的通知。
     - **警示設定**：選取當裝置解除鎖定時您想要的通知類型：
       - **無**：不會顯示通知。
       - **橫幅**：橫幅會簡短地顯示通知。
       - **強制回應**：通知顯示之後，使用者必須手動關閉才能繼續使用裝置。
     - **應用程式圖示上的徽章**：啟用此設定會在應用程式圖示上新增徽章，以指示應用程式已傳送通知。
     - **音效**：啟用此設定會在傳遞通知後播放音效。

5. 繼續新增您所需的應用程式。 新增應用程式完成時，請選取 [確定]。
6. 選取 [建立] 儲存您的設定檔。

## <a name="bundle-id-reference-for-built-in-ios-apps"></a>內建 iOS 應用程式的套件組合識別碼參考

下列清單顯示一些常見內建 iOS 應用程式的套件組合識別碼。 若要尋找其他應用程式的套件組合識別碼，請連絡軟體廠商。

|||
|-|-|
|應用程式名稱|套件組合識別碼|
|App Store|com.apple.AppStore|
|計算機|com.apple.calculator|
|行事曆|com.apple.mobilecal|
|相機|com.apple.camera|
|時鐘|com.apple.mobiletimer|
|指南針|com.apple.compass|
|連絡人|com.apple.MobileAddressBook|
|FaceTime|com.apple.facetime|
|尋找朋友|com.apple.mobileme.fmf1|
|尋找 iPhone|com.apple.mobileme.fmip1|
|Game Center|com.apple.gamecenter|
|GarageBand|com.apple.mobilegarageband|
|健全狀況|com.apple.Health|
|iBooks|com.apple.iBooks|
|iTunes Store|com.apple.MobileStore|
|iTunes U|com.apple.itunesu|
|Keynote|com.apple.Keynote|
|Mail|com.apple.mobilemail|
|地圖|com.apple.Maps|
|訊息|com.apple.MobileSMS|
|音樂|com.apple.Music|
|新聞|com.apple.news|
|附註|com.apple.mobilenotes|
|數字|com.apple.Numbers|
|頁面|com.apple.Pages|
|Photo Booth|com.apple.Photo-Booth|
|相片|com.apple.mobileslideshow|
|Podcast|com.apple.podcasts|
|提醒事項|com.apple.reminders|
|Safari|com.apple.mobilesafari|
|設定|com.apple.Preferences|
|股市|com.apple.stocks|
|秘訣|com.apple.tips|
|影片|com.apple.videos|
|語音備忘錄|com.apple.VoiceMemos|
|Wallet|com.apple.Passbook|
|觀看|com.apple.Bridge|
|天氣|com.apple.weather|

## <a name="next-steps"></a>接下來的步驟

將裝置設定檔指派給您選擇的群組。 [如何指派裝置設定檔](device-profile-assign.md)會列出步驟。
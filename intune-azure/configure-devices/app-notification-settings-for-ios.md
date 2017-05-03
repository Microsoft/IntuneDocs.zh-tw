---
title: "適用於 iOS 裝置的 Intune 應用程式通知設定"
titleSuffix: Intune Azure preview
description: "Intune Azure 預覽版：了解 iOS 裝置上您可以用來控制應用程式通知的設定。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 04/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: bda26d1d-2a3b-4669-adf8-a5aa7f994916
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: e5dd7cb5b320df7f443b52a1b502027fa3c4acaf
ms.openlocfilehash: ea4a7a57b853b27008e42fbc635da2d9a14026fd
ms.lasthandoff: 04/19/2017


---

# <a name="intune-app-notifications-settings-for-ios-devices"></a>適用於 iOS 裝置的 Intune 應用程式通知設定

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

讓您設定安裝在裝置上的應用程式如何傳送通知。 這項設定支援執行 iOS 9.3 及更新版本的受監督裝置。

## <a name="configure-settings"></a>進行設定

1. 在 [裝置功能] 刀鋒視窗上選擇 [應用程式通知 (僅限受監督)]。
2. 在 [應用程式通知] 刀鋒視窗上，選擇 [新增]，然後設定下列值：
    - **應用程式套件組合識別碼**：輸入您要設定之應用程式的 [應用程式套件組合識別碼]。 如需說明，請參閱本主題稍後的＜內建 iOS 應用程式的套件組合識別碼參考＞。
    - **應用程式名稱**：輸入您要設定之應用程式的名稱。 這不會顯示在裝置上，而是用來協助您識別清單中的應用程式。
    - **發行者**：輸入您要設定之應用程式的發行者。 這不會顯示在裝置上，而是用來協助您識別清單中的應用程式。
    - **通知**：啟用或停用應用程式傳送通知到裝置。 如果您停用這項設定，則也會停用下列設定。
        - **在通知中心顯示**：啟用以允許應用程式在裝置的「通知中心」內顯示通知。
        - **在鎖定畫面顯示**：啟用以便在裝置鎖定畫面上能查看應用程式的通知。
        - **警示設定**：選取當裝置解除鎖定時您想要的通知類型：
            - **無**：不會顯示通知。
            - **橫幅**：橫幅會簡短地顯示通知。
            - **強制回應**：通知顯示之後，使用者必須手動關閉才能繼續使用裝置。
        - **應用程式圖示上的徽章**：啟用此選項會在應用程式圖示上新增徽章，以指示應用程式已傳送通知。
        - **音效**：啟用此選項會在傳遞通知後播放音效。
3. 繼續新增您所需的應用程式。 完成之後，請選擇 [確定]。
4. 選擇 [確定] 直到您返回 [建立設定檔] 刀鋒視窗，然後選擇 [建立]。 


## <a name="bundle-id-reference-for-built-in-ios-apps"></a>內建 iOS 應用程式的套件組合識別碼參考

此清單顯示一些常見內建 iOS 應用程式的套件組合識別碼。 若要尋找其他應用程式的套件組合識別碼，請連絡軟體廠商。 

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

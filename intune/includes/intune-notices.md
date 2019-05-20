---
title: 包含檔案
description: 包含檔案
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: include
ms.date: 03/28/2019
ms.author: erikje
ms.custom: include file
ms.openlocfilehash: ffcef5b4d78856709f8563ee1f667ec7e5d993b3
ms.sourcegitcommit: d2e04a38e024b0f5afb0ca202823227de9da3ad1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/09/2019
ms.locfileid: "65732625"
---
這些注意事項提供可協助您針對未來的 Intune 變更與功能進行準備的重要資訊。 

### <a name="change-in-enrollment-workflow-with-intune-company-portal-on-corporate-ios-devices-authenticating-with-setup-assistant----1927359---"></a>在使用設定輔助程式進行驗證之公司 iOS 裝置上 Intune 公司入口網站註冊工作流程的變更 <!-- 1927359 -->
使用設定輔助程式進行驗證時，透過其中一個 Apple 公司裝置註冊方法 (Apple Configurator、Apple Business Manager、Apple School Manager 或 the Apple 裝置註冊計劃 (DEP)) 進行 iOS 裝置註冊的工作流程即將變更。 此變更只會套用到使用使用者親和性註冊的裝置。

#### <a name="how-does-this-affect-me"></a>此變更對我造成什麼影響？
當此變更推出時，位於 Azure 入口網站上 Intune 中的註冊設定檔將會更新，如此您就能指定裝置的驗證方式，以及它們是否會收到公司入口網站應用程式。 將會有一個改良的工作流程可透過上述方法註冊 iOS 裝置。 

- 當註冊新裝置並使用設定輔助程式進行驗證時，您將能夠選擇是否要自動部署「公司入口網站」應用程式。 終端使用者在註冊流程中將再也無法看到 [識別您的裝置] 與 [確認您的裝置] 畫面。  
- 在已透過設定輔助程式使用其中一個 Apple 公司裝置註冊方法註冊的裝置上，若要啟用條件式存取，您必須採取動作。 您必須使用特定 xml [設定應用程式設定原則](https://aka.ms/enrollment_setup_assistant)，以將「公司入口網站」向下推送到這些裝置。  若選擇以此方式推送「公司入口網站」，終端使用者在註冊流程中將再也無法看到 [識別您的裝置] 與 [確認您的裝置] 畫面。 
- 在此變更推出之後，若您尚未以上面所述的應用程式設定檔方式部署「公司入口網站」，且若終端使用者從應用程式商店下載「公司入口網站」應用程式，他們可已登入，但他們將會看到錯誤訊息。 他們無法為條件式存取使用該應用程式。 

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>我需要為此變更做什麼準備？
若計畫使用已修改的工作流程，您必須更新您的終端使用者指導方針以指出：

- 終端使用者在註冊流程中將再也無法看到上面提到的兩個畫面。 
- 當「公司入口網站」是自動部署而不是終端使用者從應用程式商店下載時，他們將必須登入「公司入口網站」。 

您可以視需要選擇建立應用程式設定原則，以針對此變更做好準備。 當這個新工作流程推出時，您將會在主控台中看到更新的註冊設定檔。 我們也會透過 [訊息中心] 通知您此推出。 接著，您將必須採取動作，這樣您的終端使用者才能透過 DEP 以使用設定輔助程式進行驗證的方式註冊，您才能針對條件式存取使用「公司入口網站」。

#### <a name="additional-information"></a>其他資訊 
[https://aka.ms/enrollment_setup_assistant](https://aka.ms/enrollment_setup_assistant)


### <a name="update-your-android-company-portal-app-to-the-latest-version---4536963--"></a>將您的 Android 公司入口網站應用程式更新到最新的版本 <!--4536963-->
Intune 會定期發行 Android 公司入口網站應用程式更新。 在 2018 年 11 月，我們發行了公司入口網站更新，其中包括因應 Google 從其現有通知平台轉換到 GoogleFirebase 雲端傳訊 (FCM) 而做準備的後端切換參數。 當 Google 淘汰其現有通知平台並移轉到 FCM 時，終端使用者至少必須將其公司入口網站應用程式更新到 2018 年 11 月版本以繼續與 Google Play 商店通訊。

#### <a name="how-does-this-affect-me"></a>此變更對我造成什麼影響？
我們的遙測指出您擁有「公司入口網站」版本比 5.0.4269.0 舊的裝置。 若未安裝此版本或更新版本的「公司入口網站」應用程式，IT 專業人員起始的裝置動作 (例如抹除、重設密碼、可用與必要應用程式安裝、憑證註冊) 可能無法如預期般運作。 若您的裝置在 Intune 中以 MDM 方式註冊，您可以移至 [用戶端應用程式] – [探索到的應用程式] 以查看公司入口網站版本與使用者。 選取舊版「公司入口網站」將可讓您查看哪些終端使用者有尚未更新公司入口網站的裝置。

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>我需要為此變更做什麼準備？
要求尚未更新的 Android 裝置終端使用者透過 Google Play 商店更新公司入口網站。 若使用者未持續自動更新公司入口網站應用程式，請通知您的技術支援中心。 查看＜額外資訊＞中的連結以取的有關 Google FCM 平台與變更的詳細資訊。

#### <a name="additional-information"></a>其他資訊
https://firebase.google.com/docs/cloud-messaging/
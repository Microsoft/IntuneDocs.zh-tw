---
title: "適用於 iOS 裝置的 Intune 主畫面配置設定"
titlesuffix: Azure portal
description: "了解您可以用來在 iOS 裝置上自訂主畫面和 Dock 的設定。"
keywords: 
author: vhorne
ms.author: victorh
manager: angrobe
ms.date: 07/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6aba4491-afb9-43cd-9ccc-14e6a2a5a3b1
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 0dcc8f5509afa5308f8ae91a3d60ee081d5daa0b
ms.sourcegitcommit: 3b397b1dcb780e2f82a3d8fba693773f1a9fcde1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/12/2017
---
# <a name="intune-home-screen-layout-settings-for-ios-devices"></a>適用於 iOS 裝置的 Intune 主畫面配置設定

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

使用這些設定來設定在 iOS 主畫面及 Dock 上應用程式和資料夾的配置。

指派該設定檔的 iOS 裝置必須處於受監督模式，且執行 iOS 9.3 或更新版本。

1. 在 [裝置功能] 刀鋒視窗上選擇 [主畫面配置 (僅限受監督)]。
2. 在 [主畫面配置 (僅限受監督)] 刀鋒視窗上，選擇是否要設定 [Dock] 或 [頁面] 配置。

## <a name="add-items-to-the-dock"></a>將項目新增到 Dock

在 [Dock] 刀鋒視窗上，您可以新增最多 6 個項目或資料夾到 iOS 畫面的 Dock。 不過，許多裝置支援的項目少於此數目。例如，iPhone 裝置支援最多 4 個項目。 在此情況下，裝置上只會顯示您設定的前四個項目。

1. 選擇 [新增] 來將項目新增到 Dock。
2. 在 [新增列] 刀鋒視窗上，選擇您要新增 [應用程式] 或 [資料夾]。
3. 使用本主題的資訊，設定您想要在 Dock 顯示的應用程式與資料夾。
4. 繼續新增項目。 完成之後，在每個刀鋒視窗上按一下 [確定] 直到您返回 [建立設定檔] 刀鋒視窗為止。 選擇 **[建立]**。

>[!TIP]
> 您可以在任何主畫面或頁面清單中拖放項目以調整順序。 

### <a name="example"></a>範例

在此範例中，您已設定 Dock 畫面只顯示 [Safari]、[郵件] 和 [股市] 應用程式。 在下列影像中，已選取 [郵件] 應用程式以顯示其內容：

![iOS Dock 設定範例](http://i.imgur.com/FfFiUcP.png)

當您將該原則指派給 iPhone 時，會產生如以下螢幕擷取畫面的 Dock：

![iPhone 上的 iOS Dock 配置範例](http://i.imgur.com/bAgCe8F.png)

## <a name="add-home-screen-pages"></a>新增主畫面頁面

新增您想要在主畫面顯示的頁面，以及要在每個頁面顯示的應用程式。 新增到頁面的應用程式會按照您在清單中指定的順序由左往右排列。 如果您新增的應用程式超過一個頁面所能容納的數目，應用程式就會移到下一個頁面。


1. 在 [頁面] 刀鋒視窗上，選擇 [新增]。
2. 在 [新增列] 刀鋒視窗上，輸入 [頁面名稱]。 此名稱僅供您在 Azure 入口網站中參考，「不會顯示」在 iOS 裝置上。
3. 選擇 [新增]，然後選擇您要新增 [應用程式] 或 [資料夾] 到頁面。
4. 使用本主題的資訊，設定您想要在頁面顯示的應用程式與資料夾。

### <a name="example"></a>範例

在此範例中，您會設定一個名為 **Contoso** 的新頁面。 該頁面只顯示 [尋找朋友] 和 [設定] 應用程式。 在下列影像中，已選取 [設定] 應用程式以顯示其內容：

![iOS 主畫面設定範例](http://i.imgur.com/Jc2OxyX.png)

當您將該原則指派給 iPhone 時，會產生如以下螢幕擷取畫面的頁面：

![已修改主畫面的 iOS 裝置](http://i.imgur.com/Bd37PHa.png)

## <a name="how-to-add-an-app-to-the-list"></a>如何將應用程式新增到清單

1. 輸入 [應用程式名稱]。 此名稱僅供您在 Azure 入口網站中參考，「不會顯示」在 iOS 裝置上。
2. 輸入您要顯示之應用程式的 [應用程式套件組合識別碼]。 如需說明，請參閱本主題稍後的＜內建 iOS 應用程式的套件組合識別碼參考＞。
3. 按一下 [確定]，然後繼續新增項目，裝置 Dock 最多可達 **6** 個，而裝置頁面最多可達 **60** 個。
4. 完成後，請按一下 [確定] 。

## <a name="how-to-add-a-folder-to-the-list"></a>如何將資料夾新增到清單

新增到資料夾中頁面的應用程式會按照您在清單中指定的順序由左往右排列。 如果您新增的應用程式超過一個頁面所能容納的數目，應用程式就會移到下一個頁面。

1. 輸入[資料夾名稱]。 使用者會在裝置上看到此名稱。
2. 選擇 [新增] 來在資料夾內建立頁面。 您最多可以新增 20 個頁面。
3. 在 [新增列] 刀鋒視窗上，輸入頁面的名稱。 此名稱僅供您在 Azure 入口網站中參考，「不會顯示」在 iOS 裝置上。
3. 輸入 [應用程式名稱]。 此名稱僅供您在 Azure 入口網站中參考，「不會顯示」在 iOS 裝置上。
2. 輸入您要顯示之應用程式的 [應用程式套件組合識別碼]。 如需說明，請參閱＜如何將應用程式新增到清單＞。
3. 選擇 [新增]。 您最多可以新增 60 個項目。
4. 完成後，請按一下 [確定] 。


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


## <a name="next-steps"></a>後續步驟

您現在可以將裝置設定檔指派給您選擇的群組。 如需詳細資料，請參閱[如何指派裝置設定檔](device-profile-assign.md)。

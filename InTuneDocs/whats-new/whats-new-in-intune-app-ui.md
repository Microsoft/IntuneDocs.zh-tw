---
title: "Intune 終端使用者應用程式的 UI 更新 | Microsoft Docs"
description: "了解在與 Intune 搭配使用之終端使用者裝置上運作的應用程式 UI 變更。"
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 04/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: b782e382-8deb-48a7-a437-d7c5a17163f1
ms.reviewer: priyar
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 0a39abc7f19f4c2c8074de66a9cd5df9cef78ed5
ms.openlocfilehash: 81761af5ab5aebe6abb44ff43a7df5a337d38fc7
ms.lasthandoff: 04/13/2017


---
# <a name="ui-updates-for-intune-end-user-apps"></a>Intune 終端使用者應用程式的 UI 更新
了解我們針對您的使用者在這版 Microsoft Intune 中看到的應用程式 UI 做了哪些更新。 這可協助您進行使用者通訊以及您已建立來支援您部署的任何更新中自訂文件。 它也可協助您了解如何進一步對下列問題進行疑難排解：他們尋求有關公司入口網站使用支援的技術服務時所面臨的問題。

> [!Note]
> 請注意，下列影像為預覽，宣告的產品可能與展示版本不同。

## <a name="whats-coming-in-intune-app-ui"></a>Intune 應用程式 UI 的未來動態

### <a name="april-2017"></a>2017 年 4 月

#### <a name="new-icons-for-the-managed-browser-and-the-company-portal---918433-918431--"></a>Managed Browser 和公司入口網站的新圖示 <!--918433, 918431-->

Managed Browser 會同時收到 Android 和 iOS 版應用程式的更新圖示。 此新圖示會包含更新的 Intune 徽章，以使它與 Enterprise Mobility + Security (EM+S) 中的其他應用程式更一致。

<html>
<body>
   <table id="wrapper">
      <tr>
         <td>
            <img src="https://docs.microsoft.com/InTune/whats-new/media/cp_manbro_before_042017.png" alt="The previous version of the Managed Browser app icon." width=200 height=366 align=center>
          </td>
          <td>
             <img src="https://docs.microsoft.com/InTune/whats-new/media/cp_manbro_after_042017.png" alt="The updated version of the Managed Browser app icon." width=200 height=366 align=center>
           </td>
      </tr>
   </table>
</body>
</html>

公司入口網站也會收到 Android、iOS 和 Windows 版應用程式的更新圖示，以改進與 EM+S 中其他應用程式的一致性。 從四月起到五月底，這些圖示會逐漸在各平台發行。

#### <a name="sign-in-progress-indicator-in-android-company-portal---953374--"></a>Android 公司入口網站中的登入進度列指示器 <!--953374-->

Android 公司入口網站應用程式的更新，會在使用者啟動或繼續應用程式時顯示登入進度列指示器。 在允許使用者存取應用程式之前，該指示器會逐一顯示各種新狀態，從「正在連線...」開始，然後顯示「正在登入...」，最後顯示「正在檢查安全性需求...」。

<html>
<body>
   <table id="wrapper">
      <tr>
         <td>
            <img src="https://docs.microsoft.com/InTune/whats-new/media/cp_android_signing_in_042017.png" alt="The Company Portal app for Android sign in screen that shows a partially filled loading bar with the phrase 'Connecting' underneath it." width=200 height=366 align=center>
          </td>
          <td>
             <img src="https://docs.microsoft.com/InTune/whats-new/media/cp_android_checking_security_reqs_042017.png" alt="The Company Portal app for Android sign in screen that shows a partially filled loading bar with the phrase 'Signing in' underneath it." width=200 height=366 align=center>
           </td>
           <td>
              <img src="https://docs.microsoft.com/InTune/whats-new/media/cp_android_connecting_042017.png" alt="The Company Portal app for Android sign in screen that shows a partially filled loading bar with the phrase 'Checking for security requirements' underneath it." width=200 height=366 align=center>
           </td>
      </tr>
   </table>
</body>
</html>

## <a name="whats-been-announced-for-ui-updates-for-end-user-apps"></a>已宣布的終端使用者應用程式 UI 更新內容

### <a name="february-2017"></a>2017 年 2 月

### <a name="new-user-experience-for-the-company-portal-app-for-android---621622-announced-1702--"></a>Android 版公司入口網站應用程式的新使用者體驗 <!--621622, announced 1702-->
從 3 月起，Android 版公司入口網站應用程式會遵循[素材設計方針](https://material.io/guidelines/material-design/introduction.html)建立更現代化的外觀與風格。 此改善的使用者體驗包括︰

* __色彩__︰索引標籤標頭可根據您的自訂調色盤上色。

![左側是更新前的 Android 版公司入口網站應用程式影像。 右側是更新後的 Android 版公司入口網站應用程式影像。 兩張影像顯示從 [應用程式]、[裝置] 以及 [連絡 IT] 三個可用索引標籤選取的 [裝置] 索引標籤。](./media/CP_Android_DevicesTab_BeforeAfter.png)

* __介面__︰[應用程式] 索引標籤中已更新 [精選 App] 和 [所有應用程式] 按鈕。 [搜尋] 按鈕現在是浮動的動作按鈕。

![左側是更新前的 Android 版公司入口網站應用程式影像。 右側是更新後的 Android 版公司入口網站應用程式影像。 兩張影像顯示從 [應用程式]、[裝置] 以及 [連絡 IT] 三個可用索引標籤選取的 [應用程式] 索引標籤。](./media/CP_Android_AppsTab_BeforeAfter.png)

* __瀏覽__︰所有應用程式都會以索引標籤式的檢視顯示 [精選]、[所有] 與 [類別] 以方便瀏覽。 [連絡 IT] 已簡化以改善可讀性。

<html>
<body>
   <table id="wrapper">
      <tr>
         <td>
            <img src="https://docs.microsoft.com/InTune/whats-new/media/cp_android_contactit_after.png" alt="The Company Portal app for Android displaying an updated version of the Contact IT tab. The tab shows available contact information for IT, including phone number, email address, IT website, and IT contact information." width=200 height=366 align=center>
          </td>
      </tr>
   </table>
</body>
</html>

## <a name="january-2017"></a>2017 年 1 月

### <a name="modernizing-the-company-portal-website---753980-announced-1701--"></a>現代化公司入口網站 <!--753980, announced 1701-->
從 2 月開始，公司入口網站將支援以沒有受管理裝置的使用者為目標的應用程式。 網站會使用新的對比色彩配置、動態圖例及「漢堡功能表」，與其他 Microsoft 產品和服務達成一致， ![公司入口網站左上角新增的漢堡功能表小型影像](./media/CP_hamburger_menu.png) 其包含技術服務連絡人詳細資料以及現有受管理裝置的相關資訊。 登陸頁面將會予以重新排列，以透過 [精選和最近更新] 應用程式的浮動切換來強調使用者可用的應用程式。

![在左側，影像會顯示具有其舊版 [應用程式]、[我的裝置] 以及 [精選] 和 [類別] 檢視的最新版公司入口網站。 在右側，影像會顯示具有重新整理之應用程式浮動切換、最近發佈的應用程式清單和更新過的 [類別] 檢視的公司入口網站更新版。](./media/CP_Website_BeforeAfter_Feb2016.png)


### <a name="see-also"></a>請參閱
* [Microsoft Intune 部落格](http://go.microsoft.com/fwlink/?LinkID=273882)
* [雲端平台藍圖](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)
* [Azure 預覽的新功能](https://docs.microsoft.com/intune-azure/introduction/whats-new)
* [新功能封存](whats-new-archive.md)


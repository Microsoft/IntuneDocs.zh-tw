---
title: "Intune 終端使用者應用程式的 UI 更新 | Microsoft Docs"
description: "了解在與 Intune 搭配使用之終端使用者裝置上運作的應用程式 UI 變更。"
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 05/04/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: b782e382-8deb-48a7-a437-d7c5a17163f1
ms.reviewer: priyar
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 629a091c1016186700a95bf76b9feed9ef0adb79
ms.contentlocale: zh-tw
ms.lasthandoff: 05/23/2017


---
# <a name="ui-updates-for-intune-end-user-apps"></a>Intune 終端使用者應用程式的 UI 更新
了解我們針對您的使用者在這版 Microsoft Intune 中看到的應用程式 UI 做了哪些更新。 這可協助您進行使用者通訊以及您已建立來支援您部署的任何更新中自訂文件。 它也可協助您了解如何進一步對下列問題進行疑難排解：他們尋求有關公司入口網站使用支援的技術服務時所面臨的問題。

## <a name="coming-soon-in-the-ui"></a>即將在 UI 登場
我們計劃將更新使用者介面，以改進使用者的體驗。

> [!Note]
> 請注意，下列影像為預覽，宣告的產品可能與展示版本不同。

### <a name="improved-sign-in-experience-across-company-portal-apps-for-all-platforms---user-story-1132123--"></a>改善適用於所有平台的公司入口網站應用程式登入體驗 <!--User Story 1132123-->

我們宣布將在幾個月內推出變更，以改進 Android、iOS 和 Windows 版 Intune 公司入口網站應用程式的登入體驗。 當 Azure AD 進行此變更時，新的使用者體驗會自動顯示在所有平台的公司入口網站應用程式上。 此外，使用者現在可以使用產生的一次性驗證碼，從另一部裝置登入公司入口網站。 在使用者需要不使用認證登入的情況下，這特別有用。  

以下您可以看到舊版的登入體驗、使用認證的新登入體驗，以及從另一部裝置登入的新登入體驗。

__舊版登入體驗__

![公司入口網站登入頁面，具有一個人員位於代表網站的圖形前方的圖示。 下方是 [登入] 按鈕。 底部的連結會指向 Microsoft 隱私權與 Cookie 資訊。](./media/cp_ios_aad_signin_before_1704_001.png)

![點選 [登入] 之後，使用者會在此頁面上輸入其認證，此頁面會要求輸入使用者的電子郵件和密碼，以及提供解決密碼失敗的方法。](./media/cp_ios_aad_signin_before_1704_002.png)

![使用者提供密碼之後，公司入口網站應用程式會登入，並以載入列指出進度。](./media/cp_ios_aad_signin_before_1704_003.png)

__新的登入體驗__

![公司入口網站登入頁面，具有一個人員位於代表網站的圖形前方的圖示。 下方是 [登入] 按鈕。 底部的連結會指向 Microsoft 隱私權與 Cookie 資訊。](./media/cp_ios_aad_signin_after_1704_001.png)

![系統會在畫面上單獨提示使用者輸入電子郵件地址，而不是同時提示輸入電子郵件與密碼。](./media/cp_ios_aad_signin_after_1704_002.png)

![接受使用者的電子郵件地址後，系統會提示使用者輸入密碼。](./media/cp_ios_aad_signin_after_1704_003.png)

![經過驗證程序之後，公司入口網站應用程式會登入，並以載入列指出進度。](./media/cp_ios_aad_signin_from_another_device_after_1704_007.png)

__從另一部裝置登入時的新登入體驗__

![公司入口網站登入頁面，具有一個人員位於代表網站的圖形前方的圖示。 下方是 [登入] 按鈕。 底部的連結會指向 Microsoft 隱私權與 Cookie 資訊。](./media/cp_ios_aad_signin_from_another_device_after_1704_001.png)

點選 [從另一部裝置登入] 連結。

![系統會顯示使用唯一密碼從工作電腦移至 aka.ms/devicelogin 頁面，並使用驗證碼進行登入的指示。](./media/cp_ios_aad_signin_from_another_device_after_1704_003.png)

啟動瀏覽器並移至 [https://aka.ms/devicelogin](https://aka.ms/devicelogin)。

![使用者工作電腦上的瀏覽器 (而非公司入口網站應用程式) 的影像。 顯示的 [裝置登入] 頁面提示使用者輸入在公司入口網站應用程式中收到的驗證碼。](./media/cp_ios_aad_signin_from_another_device_after_1704_004.png)

輸入您在公司入口網站應用程式中看到的驗證碼。 當您選取 [繼續] 時，您可以使用貴公司所支援的任何方法 (例如智慧卡) 進行驗證。

![使用者已將唯一驗證碼輸入至欄位，且 [裝置登入] 網站已要求確認 Intune 公司入口網站是接收驗證以登入的正確應用程式。](./media/cp_ios_aad_signin_from_another_device_after_1704_005.png)

![確認頁面指出使用者現已在其裝置上登入公司入口網站應用程式，並且可以關閉此頁面。](./media/cp_ios_aad_signin_from_another_device_after_1704_006.png)

公司入口網站應用程式將會開始登入。

![經過驗證程序之後，公司入口網站應用程式會登入，並以載入列指出進度。](./media/cp_ios_aad_signin_from_another_device_after_1704_007.png)

## <a name="april-2017"></a>2017 年 4 月

### <a name="new-icons-for-the-managed-browser-and-the-company-portal---918433-918431--"></a>Managed Browser 和公司入口網站的新圖示 <!--918433, 918431-->

Managed Browser 會同時收到 Android 和 iOS 版應用程式的更新圖示。 此新圖示會包含更新的 Intune 徽章，以使它與 Enterprise Mobility + Security (EM+S) 中的其他應用程式更一致。

<html>
<body>
   <table id="wrapper">
      <tr>
         <td>
            <img src="/intune-classic/whats-new/media/cp_manbro_before_042017.png" alt="The previous version of the Managed Browser app icon." width=200 height=366 align=center>
          </td>
          <td>
             <img src="/intune-classic/whats-new/media/cp_manbro_after_042017.png" alt="The updated version of the Managed Browser app icon." width=200 height=366 align=center>
           </td>
      </tr>
   </table>
</body>
</html>

公司入口網站也會收到 Android、iOS 和 Windows 版應用程式的更新圖示，以改進與 EM+S 中其他應用程式的一致性。 從四月起到五月底，這些圖示會逐漸在各平台發行。

### <a name="sign-in-progress-indicator-in-android-company-portal---953374--"></a>Android 公司入口網站中的登入進度列指示器 <!--953374-->

Android 公司入口網站應用程式的更新會在使用者啟動或繼續執行應用程式時，顯示登入進度指示器。 該指示器會顯示新的狀態進度，一開始為「正在連線...」，接著依序為「正在登入...」和「正在檢查安全性需求...」，之後才允許使用者存取應用程式。

<html>
<body>
   <table id="wrapper">
      <tr>
         <td>
            <img src="/intune-classic/whats-new/media/cp_android_connecting_042017.png" alt="The Company Portal app for Android sign in screen that shows a partially filled loading bar with the phrase 'Connecting' underneath it." width=200 height=366 align=center>
          </td>
          <td>
             <img src="/intune-classic/whats-new/media/cp_android_signing_in_042017.png" alt="The Company Portal app for Android sign in screen that shows a partially filled loading bar with the phrase 'Signing in' underneath it." width=200 height=366 align=center>
           </td>
           <td>
              <img src="/intune-classic/whats-new/media/cp_android_checking_security_reqs_042017.png" alt="The Company Portal app for Android sign in screen that shows a partially filled loading bar with the phrase 'Checking for security requirements' underneath it." width=200 height=366 align=center>
           </td>
      </tr>
   </table>
</body>
</html>

### <a name="improved-app-install-status-for-the-windows-10-company-portal-app---676495--"></a>改進 Windows 10 公司入口網站應用程式的應用程式安裝狀態 <!--676495-->
Windows 10 公司入口網站應用程式現在於應用程式詳細資料頁面提供安裝進度列。 在執行 Windows 10 年度更新版與更新版本裝置上的新式應用程式可支援此功能。

__改進前__
  ![舊版載入畫面的影像，其中狀態僅簡單地表示「安裝中」。](./media/cp_win10_install_status_before_1704.png)

__改進後__
  ![更新版本的載入畫面影像，現在會顯示安裝進度列。](./media/cp_win10_install_status_after_1704.png)

## <a name="february-2017"></a>2017 年 2 月

### <a name="new-user-experience-for-the-company-portal-app-for-android---621622-announced-1702--"></a>Android 版公司入口網站應用程式的新使用者體驗 <!--621622, announced 1702-->
從 3 月起，Android 版公司入口網站應用程式會遵循[素材設計方針](https://material.io/guidelines/material-design/introduction.html)建立更現代化的外觀與風格。 此改善的使用者體驗包括︰

* __色彩__︰索引標籤標頭可根據您的自訂調色盤上色。

![左側是更新前的 Android 版公司入口網站應用程式影像。 右側是更新後的 Android 版公司入口網站應用程式影像。 兩張影像顯示從 [應用程式]、[裝置] 以及 [連絡 IT] 三個可用索引標籤選取的 [裝置] 索引標籤。](./media/CP_Android_DevicesTab_BeforeAfter.png)

* __介面__︰[應用程式] 索引標籤中已更新 [精選 App] 和 [所有 App] 按鈕。 [搜尋] 按鈕現在是浮動的動作按鈕。

![左側是更新前的 Android 版公司入口網站應用程式影像。 右側是更新後的 Android 版公司入口網站應用程式影像。 兩張影像顯示從 [應用程式]、[裝置] 以及 [連絡 IT] 三個可用索引標籤選取的 [應用程式] 索引標籤。](./media/CP_Android_AppsTab_BeforeAfter.png)

* __瀏覽__︰所有應用程式都會以索引標籤式的檢視顯示 [精選]、[所有] 與 [類別] 以方便瀏覽。 [連絡 IT] 已簡化以改善可讀性。

<html>
<body>
   <table id="wrapper">
      <tr>
         <td>
            <img src="/intune-classic/whats-new/media/cp_android_contactit_after.png" alt="The Company Portal app for Android displaying an updated version of the Contact IT tab. The tab shows available contact information for IT, including phone number, email address, IT website, and IT contact information." width=200 height=366 align=center>
          </td>
      </tr>
   </table>
</body>
</html>

## <a name="january-2017"></a>2017 年 1 月

### <a name="modernizing-the-company-portal-website---753980-announced-1701--"></a>現代化公司入口網站 <!--753980, announced 1701-->
從 2 月開始，公司入口網站將支援以沒有受管理裝置的使用者為目標的應用程式。 網站會使用新的對比色彩配置、動態圖例及「漢堡功能表」，與其他 Microsoft 產品和服務達成一致， ![公司入口網站左上角新增的漢堡功能表小型影像](./media/CP_hamburger_menu.png) 其包含技術服務連絡人詳細資料以及現有受管理裝置的相關資訊。 登陸頁面將會予以重新排列，以透過 [精選和最近更新] 應用程式的浮動切換來強調使用者可用的應用程式。

![在左側，影像會顯示具有其舊版 [應用程式]、[我的裝置] 以及 [精選] 和 [類別] 檢視的最新版公司入口網站。 在右側，影像會顯示具有重新整理之應用程式浮動切換、最近發佈的應用程式清單和更新過的 [類別] 檢視的公司入口網站更新版。](./media/CP_Website_BeforeAfter_Feb2016.png)


### <a name="see-also"></a>另請參閱
* [Microsoft Intune 部落格](http://go.microsoft.com/fwlink/?LinkID=273882)
* [雲端平台藍圖](https://www.microsoft.com/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)
* [Azure 預覽中的新增功能](https://docs.microsoft.com/intune/whats-new)
* [新增功能封存](whats-new-archive.md)


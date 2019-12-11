---
title: Intune 終端使用者應用程式的 UI 更新
titleSuffix: Microsoft Intune
description: 了解在與 Microsoft Intune 搭配使用之終端使用者裝置上運作的應用程式 UI 變更。
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 11/14/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: b782e382-8deb-48a7-a437-d7c5a17163f1
ms.reviewer: priyar
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: a3b391bb4ab064c080083e2c31dc28483f6d419a
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "74098214"
---
# <a name="ui-updates-for-intune-end-user-apps"></a>Intune 終端使用者應用程式的 UI 更新

了解 Microsoft Intune 應用程式的最新更新。 我們會定期新增至 Intune 公司入口網站應用程式和網站並會加以改善。 如果您是 Intune 管理員或支援人員，本文會提供您執行下列操作所需的資訊：

* 對學生和員工發出關於應用程式和註冊變更的警示。
* 更新您組織的文件或技術服務人員程序。  

如果您是員工或學生，請務必查看公司入口網站說明文件的螢幕擷取畫面和連結。 如需如何使用公司入口網站應用程式的詳細資訊，請參閱[公司入口網站使用者說明文件](https://docs.microsoft.com/intune-user-help/)。  

<!---End-user messaging for accounts 1573558, 1712; changes to be made for other platforms for 1801 Users of the Company Portal website, will be blocked from taking actions that require write access to your tenant. They will see appropriate error messaging explaining that their account is under maintenance. Similar changes are coming to the Company Portal apps for Android, iOS, macOS, and Windows soon. ![Error message that occurs during account move](./media/whats-new-app-ui/account-move-rom-iwp-user-1712.png)--->

## <a name="week-of-november-11-2019"></a>2019 年 11 月 11 日當週  

#### <a name="web-apps-launched-from-the-windows-company-portal-app---5030972---"></a>從 Windows 公司入口網站應用程式啟動的 Web 應用程式<!-- 5030972 -->
終端使用者現在可以直接從 Windows 公司入口網站應用程式啟動 Web 應用程式。 終端使用者可以選取 Web 應用程式，然後選擇 [以瀏覽器開啟]  選項。 已發佈的 Web URL 會直接在網頁瀏覽器中開啟。 此功能將於下周推出。 如需 Web 應用程式的詳細資訊，請參閱[將 Web 應用程式新增至 Microsoft Intune](~/apps/web-app.md)。

![從 Windows 公司入口網站應用程式啟動的 Web 應用程式範例映像](./media/whats-new-app-ui/webapp-open-in-browser.png)  

### <a name="improved-macos-enrollment-experience-in-company-portal----5074349-wnready---"></a>已改善公司入口網站的 macOS 註冊體驗 <!-- 5074349 WNready -->  
提供 macOS 註冊體驗的公司入口網站有更簡易註冊程序，其更貼近 iOS 版公司入口網站的註冊體驗。 裝置使用者現在會看到：  

* 更時尚的使用者介面。  
* 改善的註冊檢查清單。  
* 更清楚的裝置註冊指示。  
* 改善的疑難排解選項。  

## <a name="week-of-october-28-2019"></a>2019 年 10 月 28 日當週  

### <a name="improved-checklist-design-in-company-portal-app-for-android----5550857---"></a>改善了 Android 版公司入口網站應用程式中的檢查清單設計 <!-- 5550857 -->  
Android 版公司入口網站應用程式中的設定檢查清單已更新為採用輕量設計與新圖示。 這些變更與針對 iOS 版公司入口網站應用程式所做的最新更新一致。 針對已更新的註冊步驟，請參閱[使用 Android 工作設定檔註冊](/intune-user-help/enroll-device-android-work-profile)與[註冊您的 Android 裝置](/intune-user-help/enroll-device-android-company-portal)。  

下列畫面顯示已更新的 Android 工作設定檔註冊檢查清單：

|已更新|上一步|  
|---|---|  
|![公司入口網站中工作設定檔設定的範例影像，其中顯示簡化的檢查清單與新圖示。](./media/whats-new-app-ui/work-profile-checklist-1911.png)|![公司入口網站中先前工作設定檔設定的範例影像，其中顯示較繁複的檢查清單。](./media/whats-new-app-ui/work-profile-checklist-1904.png)|   

下列畫面顯示已更新的 Android 裝置系統管理員註冊檢查清單：  

|已更新|上一步|  
|---|---|  
|![公司入口網站中 Android 裝置系統管理員設定的範例影像，其中顯示簡化的檢查清單與新圖示。](./media/whats-new-app-ui/android-checklist-1911.png)|![公司入口網站中 Android 裝置系統管理員設定的範例影像，其中顯示較繁複的檢查清單。](./media/whats-new-app-ui/android-checklist-1904.png)|  

## <a name="week-of-september-9-2019"></a>2019 年 9 月 9 日當週

### <a name="updates-to-microsoft-intune-app----4997846---"></a>Microsoft Intune 應用程式的更新 <!-- 4997846 -->
適用於 Android 的 Microsoft Intune 應用程式已更新，並具有下列改善：
- 已更新並改善版面配置以納入最重要動作的下方導覽。
- 已新增顯示使用者設定檔的額外頁面。
- 已在應用程式中為使用者新增可採取動作的通知顯示，例如需要更新其裝置設定。
- 已新增自訂推播通知的顯示，並將應用程式與適用於 iOS 和 Android 之公司入口網站應用程式中最近新增的支援一致。 如需詳細資訊，請參閱[在 Intune 中傳送自訂通知](../remote-actions/custom-notifications.md)。

    使用者設定檔範例：<br>
    <img src="./media/whats-new-app-ui/intune-app-android-device-profile.png" alt="Screenshot of Microsoft Intune app for Android - User Profile" width="300">   

    通知和底部導覽範例：<br>
    <img src="./media/whats-new-app-ui/intune-app-android-device-notify.png" alt="Screenshot of Microsoft Intune app for Android - Notification" width="300">   


## <a name="week-of-june-24-2019"></a>2019 年 6 月 24 日當週  

### <a name="view-all-installed-apps-from-new-company-portal-web-page----4224326---"></a>從新的「公司入口網站」網頁檢視已安裝的應用程式 <!-- 4224326 -->
「公司入口網站」的新 [已安裝的應用程式]  頁面會出安裝在使用者裝置上 (必要及可用的) 所有受控應用程式。 除了指派類型之外，使用者也可以看到應用程式的發行者、發行日期，以及目前的安裝狀態。 若您沒有針對使用者將任何應用程式設為必要或可用，他們將會看見一個訊息，說明沒有安裝任何公司應用程式。 若要在 Web 上查看新頁面，請前往[公司入口網站](https://portal.manage.microsoft.com)，然後按一下 [已安裝的應用程式]  。   

![公司入口網站上 [已安裝的應用程式] 頁面之螢幕擷取畫面。](./media/whats-new-app-ui/intune-installed-apps-1907.png)     

### <a name="new-view-lets-app-users-see-all-managed-apps-installed-on-device----2352913---"></a>新的檢視可讓應用程式使用者查看裝置上安裝的所有受控應用程式 <!-- 2352913 -->
適用於 Windows 的「公司入口網站」應用程式現在會列出使用者裝置上已安裝的所有受控應用程式 (必要及可用的)。 使用者也可以看到已嘗試與擱置中的應用程式安裝，以及其目前狀態。 若您沒有針對使用者將應用程式設為必要或可用，他們將會看見一個訊息，說明沒有安裝任何公司應用程式。 若要查看新檢視，請前往「公司入口網站」瀏覽窗格，然後選取 [應用程式]   > [已安裝的應用程式]  。   

![適用於 Windows 10 的「公司入口網站」上 [已安裝的應用程式] 之範例螢幕擷取畫面。 ](./media/whats-new-app-ui/installed-apps-cp-1906.png)  


## <a name="week-of-june-17-2019"></a>2019 年 6 月 17 日當週  

### <a name="new-features-in-microsoft-intune-app"></a>Microsoft Intune 應用程式中的新功能
我們已在適用於 Android 的 Microsoft Intune 應用程式 (預覽) 中新增功能。 完全受控 Android 裝置上的使用者現在可以：  

* 透過 Intune 公司入口網站或 Microsoft Intune 應用程式，檢視及管理已註冊的裝置。    
* 與其組織連絡以尋求支援。    
* 將其意見反應傳送給 Microsoft。    
* 若其組織已設定條款及條件，即可加以檢視。 

## <a name="week-of-april-15-2019"></a>2019 年 4 月 15 日當週  

### <a name="new-end-user-app-microsoft-intune-app---3903244---"></a>新增終端使用者應用程式 (Microsoft Intune 應用程式) <!--3903244 -->  
新增適用於完全受控 Android 裝置的終端使用者應用程式，稱為 **Microsoft Intune**。 這是輕量型且現代化的全新應用程式，提供與公司入口網站應用程式類似的功能，但適用於完全受控的公司裝置。 如需詳細資訊，請參閱 [Google Play 上的 Microsoft Intune 應用程式](https://play.google.com/store/apps/details?id=com.microsoft.intune)。  

裝置詳細資料畫面的範例螢幕擷取畫面： 

![Microsoft Intune 應用程式的螢幕擷取畫面，其中顯示 Jane 的 Android 裝置詳細資料。](./media/whats-new-app-ui/1904-intune-app-device-details.png)   

[設定存取]  畫面的範例螢幕擷取畫面：  

![Microsoft Intune 應用程式的螢幕擷取畫面，其中顯示設定存取註冊畫面。](./media/whats-new-app-ui/1904-intune-app-setup-access.png)   

應用程式功能表的範例螢幕擷取畫面：  

![Microsoft Intune 應用程式的螢幕擷取畫面，其中顯示側邊功能表。](./media/whats-new-app-ui/1904-intune-app-navigation-menu.png)   

[說明]  畫面的範例螢幕擷取畫面：  

![Microsoft Intune 應用程式中 [說明] 畫面的螢幕擷取畫面。](./media/whats-new-app-ui/1904-intune-app-help.png)   


## <a name="week-of-april-1-2019"></a>2019 年 4 月 1 日當週  

### <a name="changes-to-company-portal-enrollment-for-ios-12-device-users---3448635---"></a>適用於 iOS 12 裝置使用者的公司入口網站註冊變更 <!--3448635 -->  
iOS 版公司入口網站註冊畫面和步驟，為了配合 Apple iOS 12.2 中發行的 MDM 註冊變更已有所更新。 更新的工作流程會提示使用者：  

* 允許 Safari 先開啟公司入口網站並下載管理設定檔，再返回公司入口網站應用程式。  
* 開啟設定應用程式以在其裝置上安裝管理設定檔。  
* 返回公司入口網站應用程式以完成註冊。  

如需更新的註冊步驟和畫面，請參閱 [Enroll iOS device in Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios) (在 Intune 中註冊 iOS 裝置)。  

### <a name="user-experience-update-for-the-company-portal-app-for-ios----2536024---"></a>iOS 版公司入口網站應用程式的使用者體驗更新 <!-- 2536024 -->
適用於 iOS 裝置的公司入口網站應用程式首頁已經過重新設計。 透過這項變更，首頁將會改善採用 iOS UI 模式的能力，也會改善探索應用程式和電子書的能力。  

## <a name="week-of-february-19-2019"></a>2019 年 2 月 19 日當週  
### <a name="new-app-categories-screen-in-the-company-portal-app-for-windows-10---3834780-wnready4review---"></a>在 Windows 10 版公司入口網站應用程式中新增 [應用程式類別] 畫面<!-- 3834780 WNready4Review -->  
新增了稱為 [應用程式類別]  的畫面，以改善 Windows 10 版公司入口網站中的應用程式瀏覽和選取體驗。 使用者現在會看到其應用程式依類別排序，例如 [精選]  、[教育]  和 [生產力]  。 這項變更會出現在公司入口網站 10.3.3451.0 版和更新版本。 如需在公司入口網站中安裝應用程式的詳細資訊，請參閱[在裝置上安裝和共用應用程式](/intune-user-help/install-apps-cpapp-windows)。  

![Windows 10 版公司入口網站中 [應用程式類別] 畫面的螢幕擷取畫面。](./media/whats-new-app-ui/1902_CP_app_categories.png)   


## <a name="week-of-november-12-2018"></a>2018 年 11 月 12 日當週

### <a name="windows-company-portal-keyboard-shortcuts----2771518---"></a>Windows 公司入口網站鍵盤快速鍵 <!-- 2771518 -->
終端使用者現在可在 Windows 公司入口網站中[使用鍵盤快速鍵 (快速鍵)](../apps/company-portal-app.md#windows-company-portal-keyboard-shortcuts) 來觸發應用程式和裝置動作。

## <a name="week-of-october-22-2018"></a>2018 年 10 月 22 日當週

### <a name="add-custom-brand-image-for-company-portal-app----1916266---"></a>新增公司入口網站應用程式的自訂品牌形象 <!-- 1916266 -->
作為 Microsoft Intune 系統管理員，您可以上傳自訂品牌影像，該影像會在 iOS 公司入口網站應用程式的使用者設定檔頁面上，作為背景影像顯示。 如需設定公司入口網站應用程式的詳細資訊，請參閱[如何設定 Microsoft Intune 公司入口網站應用程式](../apps/company-portal-app.md)。  

## <a name="week-of-august-27-2018"></a>2018 年 8 月 27 日當週  

### <a name="new-user-experience-update-for-the-company-portal-website---2000968---"></a>對於公司入口網站的新使用者體驗更新 <!--2000968 -->  
我們已依據客戶的意見反應，新增功能至公司入口網站。 您將能於裝置上體驗現有功能和可用性等方面的重大改善。 網站的特定區域 (例如裝置詳細資料、意見反應和支援以及裝置概觀) 現在有全新現代化回應式設計。 已更新 [Intune 公司入口網站文件](https://docs.microsoft.com/intune-user-help/using-the-intune-company-portal-website)，以反映這些變更。   

您會看到的更新包括：  

- 簡化所有裝置平台中的工作流程
- 改善裝置識別和註冊流程
- 更有用的錯誤訊息
- 讓語言更容易使用，讓技術專業術語更少
- 能夠共用應用程式的直接連結
- 已改進大型應用程式目錄的效能
- 增加所有使用者的協助工具  

|已更新|上一步|
|---|---|
|![更新過的裝置頁面會在裝置資訊正上方顯示裝置，不再跳出在完整清單上方。](./media/whats-new-app-ui/iwp-device-after-1803.png)|![舊版的裝置頁面。](./media/whats-new-app-ui/iwp-device-before-1803.png)|
|![更新過的應用程式安裝頁面會顯示描述正上方的應用程式和各種安裝資訊，包含應用程式的發佈日期、版本和類型。](./media/whats-new-app-ui/iwp-app-install-after-1803.png)|![舊版的應用程式安裝頁面。](./media/whats-new-app-ui/iwp-app-install-before-1803.png)|  

## <a name="week-of-july-16-2018"></a>2018 年 7 月 16 日當週  

### <a name="more-opportunities-to-sync-in-the-company-portal-app-for-windows"></a>Windows 版公司入口網站應用程式中的更多同步機會   
Windows 版公司入口網站應用程式現在可讓您直接從 Windows 工作列和 [開始] 功能表起始同步。 如果同步裝置並取得公司資源存取權是您唯一的工作，這項功能特別有用。 若要存取這項新功能，請以滑鼠右鍵按一下已釘選到工作列或 [開始]  功能表的公司入口網站圖示。 在功能表選項 (也稱為捷徑清單) 中，選取 **[同步此裝置]** 。 公司入口網站會開啟至 **[設定]** 頁面並起始您的同步。  

![裝置桌面上 Windows 工作列的螢幕擷取畫面。 按一下公司入口網站應用程式的程式圖示之後，顯示含有 [釘選到工作列]、[關閉視窗] 和 [同步此裝置] 動作等選項的功能表。](./media/whats-new-app-ui/sync-device-from-start-menu-1807.png)  

### <a name="new-browsing-experiences-in-the-company-portal-app-for-windows"></a>Windows 版公司入口網站應用程式的新瀏覽體驗  

現在，在 Windows 版公司入口網站應用程式中瀏覽或搜尋應用程式時，您可以切換現有的 [磚]  檢視和新的 [詳細資料]  檢視。 此新的檢視會列出應用程式詳細資料，例如名稱、發行者、發行日期及安裝狀態。  

[應用程式]  頁面的 [已安裝]  檢視可讓您查看有關已完成和進行中之應用程式安裝的詳細資料。  

顯示 [磚] 檢視的範例螢幕擷取畫面：  
 
![在 [磚] 檢視中顯示已安裝應用程式的 Windows 版 Intune 公司入口網站應用程式的螢幕擷取畫面。](./media/whats-new-app-ui/tiles-installed-view-cpapp-1807.png)  

顯示 [詳細資料] 檢視的範例螢幕擷取畫面：  

![在 [詳細資料] 檢視中顯示已安裝應用程式的 Windows 版 Intune 公司入口網站應用程式的螢幕擷取畫面。](./media/whats-new-app-ui/details-installed-view-cpapp-1807.png)

## <a name="week-of-april-23-2018"></a>2018 年 4 月 23 日當週
### <a name="updated-navigation-view-in-the-company-portal-app-for-windows-10----1195010---"></a>更新 Windows 10 版公司入口網站應用程式的導覽檢視 <!-- 1195010 -->
Windows 10 版的 Intune 公司入口網站應用程式已更新為使用 [Fluent Design System's navigation view](https://docs.microsoft.com/windows/uwp/design/basics/navigation-basics) \(Fluent Design System 的瀏覽檢視\)。 您會發現應用程式側邊多了一個垂直靜態清單，列有最上層的所有頁面。 按一下任何連結都能快速檢視及來回切換頁面。 這是您將看到數個更新其中的第一個，我們正繼續努力建立更彈性、更易用且更熟悉的 Intune 體驗。 

![顯示 Fluent Design 瀏覽檢視之公司入口網站應用程式儀表板的螢幕擷取畫面](./media/whats-new-app-ui/1804_WindowsCP_Fluent_01.png)


## <a name="week-of-april-2-2018"></a>2018 年 4 月 2 日當週

### <a name="user-experience-update-for-the-company-portal-app-for-ios----1412866---"></a>iOS 版公司入口網站應用程式的使用者體驗更新 <!-- 1412866 -->
我們已經發行 iOS 版公司入口網站應用程式的主要使用者經驗更新。 此更新採用全新現代化外觀的視覺設計。 應用程式的功能不變，但強化了可用性與協助工具功能。  

此外還包括：
- iPhone X 的支援。
- 應用程式啟動速度與載入回應的速度變快，可以節省使用者寶貴的時間。
- 增加更多的進度列，方便使用者掌握最新旳狀態資訊。
- 改善使用者上傳記錄的方式，方便在發生問題時回報。  

|之前|在|
|---|---|
|![01](./media/whats-new-app-ui/cp_iosRedesign_before_1803_01.png)|![01](./media/whats-new-app-ui/cp_iosRedesign_after_1803_01.png)|
|*與上一個步驟合併*|![02](./media/whats-new-app-ui/cp_iosRedesign_after_1803_02.png)|
|![03](./media/whats-new-app-ui/cp_iosRedesign_before_1803_02.png)|![03](./media/whats-new-app-ui/cp_iosRedesign_after_1803_03.png)|

### <a name="improvements-to-the-language-in-the-company-portal-app-for-windows----1683758---"></a>Windows 版公司入口網站應用程式中的語言改善 <!-- 1683758 -->
我們已改進 Windows 10 版公司入口網站中的語言，不僅對使用者來說更簡單明瞭，也更專屬於您的公司。

|之前|在|
|---|---|
|![01](./media/whats-new-app-ui/windows_enroll_before_1803.png)|![01](./media/whats-new-app-ui/windows_enroll_after_1803.png)|
|![02](./media/whats-new-app-ui/windows_view_policy_issues_before_1803.png)|![02](./media/whats-new-app-ui/windows_view_policy_issues_after_1803.png)

## <a name="week-of-march-12-2018"></a>2018 年 3 月 12 日當週

### <a name="company-portal-for-android-visual-updates----976944---"></a>Android 視覺效果更新的公司入口網站 <!-- 976944 -->

我們已更新 Android 版公司入口網站應用程式，以遵循 Android 的 [Material Design](https://material.io/) 指導方針。

|之前|在|
|---|---|
|![01](./media/whats-new-app-ui/android_about_before_1803.png)|![01](./media/whats-new-app-ui/androidCP_about_after_1803.png)|
|![02](./media/whats-new-app-ui/android_contact_it_before_1803.png)|![02](./media/whats-new-app-ui/android_contact_it_after_1803.png)|
|![03](./media/whats-new-app-ui/android_devices_before_1803.png)|![03](./media/whats-new-app-ui/androidCP_devicelist_after_1803.png)|
|![04](./media/whats-new-app-ui/android_device_details_before_1803.png)|![05](./media/whats-new-app-ui/androidCP_devicedetails_1_after1803.png)|
|![05](./media/whats-new-app-ui/android_device_details_update_settings_before_1803.png)|![05](./media/whats-new-app-ui/androidCP_devicedetails_red_box_2_after1803.png)|
|![06](./media/whats-new-app-ui/android_profile_before_1803.png)|![06](./media/whats-new-app-ui/android_profile_after_1803.png)|
|![07](./media/whats-new-app-ui/androidCP_Setup01_before_1803.png)|![07](./media/whats-new-app-ui/androidCP_Setup01_after_1803.png)|


## <a name="week-of-november-27-2017"></a>2017 年 11 月 27 日當週

### <a name="new-device-categories-step-in-guided-setup-for-the-company-portal-app-for-windows-10----1335292---"></a>在 Windows 10 版公司入口網站應用程式的引導式設定中新增「裝置類別」步驟 <!-- 1335292 -->

如已啟用 [裝置群組對應](../enrollment/device-group-mapping.md)，則 Windows 10 的公司入口網站應用程式現在會在使用者註冊其裝置後，逐步引導使用者完成選取裝置類別。

![裝置群組對應類別](./media/whats-new-app-ui/w10_cp_category_device_setup_after_1711.png)

## <a name="week-of-november-13-2017"></a>2017 年 11 月 13 日當週

### <a name="improvements-to-device-setup-workflow-in-the-company-portal-for-ios-in-version-290----1417174---"></a>iOS 版公司入口網站 2.9.0 版中裝置設定工作流程的改善 <!-- 1417174 -->

我們已改善 iOS 版公司入口網站應用程式中的裝置設定工作流程。 語言對使用者來說更簡單明瞭，而且我們已盡量將可以合併的畫面合併。 我們也透過在整個設定文字中使用您的公司名稱，讓語言更特定於您的公司。

> [!NOTE]
> 我們會將您在 Azure 入口網站中設定的公司名稱用於 [Microsoft Intune]   > [用戶端應用程式]   > [公司入口網站品牌]   > [公司名稱]  。 如果您沒有設定此值，我們將使用在 [Azure Active Directory]   > [屬性]   > [名稱]  中設定的租用戶名稱。 如果您尚未在 [公司入口網站品牌] 中設定公司名稱，且不希望顯示您的租用戶名稱，建議您在 [公司入口網站品牌] 索引標籤中設定公司名稱。如果您不希望在公司入口網站的標頭中顯示此字串，則可以取消選取 [在標誌旁顯示公司名稱] 核取方塊。

|之前|在|
|---|---|
|![01](./media/whats-new-app-ui/ios_cp_enroll_01_before_1711.png)|![01](./media/whats-new-app-ui/ios_cp_enroll_01_after_1711.png)|
|![02](./media/whats-new-app-ui/ios_cp_enroll_02_before_1711.png)|*與上一個步驟合併*|
|![03](./media/whats-new-app-ui/ios_cp_enroll_03_before_1711.png)|![03](./media/whats-new-app-ui/ios_cp_enroll_03_after_1711.png)|
|![04](./media/whats-new-app-ui/ios_cp_enroll_04_before_1711.png)|![04](./media/whats-new-app-ui/ios_cp_enroll_04_after_1711.png)|
|![05](./media/whats-new-app-ui/ios_cp_enroll_05_before_1711.png)|![05](./media/whats-new-app-ui/ios_cp_enroll_05_after_1711.png)|
|![06](./media/whats-new-app-ui/ios_cp_enroll_06_before_1711.png)|![06](./media/whats-new-app-ui/ios_cp_enroll_06_after_1711.png)|
|![07](./media/whats-new-app-ui/ios_cp_enroll_07_before_1711.png)|![07](./media/whats-new-app-ui/ios_cp_enroll_07_after_1711.png)|


## <a name="week-of-november-6-2017"></a>2017 年 11 月 6 日當週

### <a name="updates-to-the-company-portal-app-for-windows-10---1299474--"></a>Windows 10 版公司入口網站應用程式的更新 <!--1299474-->
Windows 10 版「公司入口網站」應用程式中的 [設定] 頁面已更新，以使設定和預期的使用者動作在所有設定中更加一致。 它也已更新為符合其他 Windows 應用程式的配置。

|之前|在|
|---|---|
|![01](./media/whats-new-app-ui/w10-share-logs.png)|![02](./media/whats-new-app-ui/w10-share-logs-after-1711.png)|


### <a name="search-improvements-to-the-company-portal-apps-and-website----1418189---"></a>公司入口網站應用程式與網站的搜尋改善 <!-- 1418189 -->
公司入口網站應用程式現在會在應用程式類別、名稱及描述之間進行搜尋。 結果會依相關性的遞減順序進行排序。 [公司入口網站](https://portal.manage.microsoft.com)也會得到這些更新。

我們仍然會微調相關性的追蹤方式；因此，請使用公司入口網站底端的 [意見反應] 連結，讓我們知道其運作方式。

## <a name="week-of-october-16-2017"></a>2017 年 10 月 16 日當週

### <a name="search-improvements-to-the-company-portal-website----1331697---"></a>公司入口網站的搜尋改善 <!-- 1331697 -->
我們正在改善應用程式搜尋功能，並從[公司入口網站](https://portal.manage.microsoft.com)開始。 除了 [名稱] 和 [描述] 欄位之外，現在也會對應用程式類別執行搜尋。 預設會依相關性的遞減順序來排序結果。 

iOS 使用者也會收到這項變更，因為也會使用公司入口網站作為適用於 iOS 的公司入口網站應用程式一部分。 適用於 Android 和 Windows 的公司入口網站應用程式將會在接下來的幾個月收到類似的更新。

我們仍然會微調相關性的追蹤方式；因此，請使用公司入口網站底端的 [意見反應] 連結，讓我們知道其運作方式。


### <a name="ios-company-portal-displays-large-icons----1454593---"></a>iOS 公司入口網站顯示大型圖示 <!-- 1454593 -->
此版本修正 iOS 公司入口網站於應用程式磚中顯示圖示方式的已知問題。 如果您上傳 120x120 像素或更大的應用程式圖示，現在會以完整的應用程式磚大小顯示在[公司入口網站](https://portal.manage.microsoft.com)和 iOS 公司入口網站的應用程式頁面中。


## <a name="week-of-october-2-2017"></a>2017 年 10 月 2 日當週

### <a name="improvements-to-device-setup-workflow-in-company-portal----1490692---"></a>對公司入口網站中裝置安裝工作流程的改善 <!-- 1490692 -->
我們已改善 Android 版公司入口網站應用程式中的裝置安裝工作流程。 我們採用您公司專屬的語言、對使用者來說更簡單明瞭，並盡量將可以合併的畫面合併。 

|之前|在|
|---|---|
|![01](./media/whats-new-app-ui/android_cp_enroll_01_post_1709.png)|![01](./media/whats-new-app-ui/android_cp_enroll_01_1709_new.png)|
|![01a](./media/whats-new-app-ui/android_cp_enroll_01_before_1710.png)| *與上一個步驟合併* |
|![02](./media/whats-new-app-ui/android_cp_enroll_02_before_1710.png)|![02](./media/whats-new-app-ui/android_cp_enroll_02_after_1710.png)|
|![03](./media/whats-new-app-ui/android_cp_enroll_03_before_1710.png)|![03](./media/whats-new-app-ui/android_cp_enroll_03_after_1710.png)|

已改善 Android 工作設定檔裝置上的額外步驟。

|之前|在|
|---|---|
|![04](./media/whats-new-app-ui/android_work_cp_enroll_01_before_1710.png)|![04](./media/whats-new-app-ui/android_work_cp_enroll_01_after_1710.png)|
|![05](./media/whats-new-app-ui/android_work_cp_enroll_02_before_1710.png)| *與上一個步驟合併* |
|![06](./media/whats-new-app-ui/android_work_cp_enroll_03_before_1710.png)|![06](./media/whats-new-app-ui/android_work_cp_enroll_03_after_1710.png)|
|![07](./media/whats-new-app-ui/android_work_cp_enroll_04_before_1710.png)|![07](./media/whats-new-app-ui/android_work_cp_enroll_04_after_1710.png)|
|![08](./media/whats-new-app-ui/android_work_cp_enroll_05_before_1710.png)| *與上一個步驟合併* |


我們也已更新條件式存取電子郵件啟用畫面。

|之前|在|
|---|---|
|![06](./media/whats-new-app-ui/android_conditional_access_email_before_1710.png)|![06](./media/whats-new-app-ui/android_conditional_access_email_after_1710.png)

## <a name="week-of-september-11-2017"></a>2017 年 9 月 11 日當週

### <a name="easier-to-understand-phrasing-for-the-company-portal-app-for-android----1396349---"></a>Android 版公司入口網站應用程式中更易了解的措辭 <!-- 1396349 -->  

Android 公司入口網站應用程式的註冊程序已經使用新的文字來簡化，讓終端使用者可更輕鬆地進行註冊。 如果您有自訂註冊文件，建議您予以更新，以反映新的畫面。 您可以在下方查看範例影像：

|之前|在|
|---|---|
|![01](./media/whats-new-app-ui/android_cp_enroll_01_before_1709.png)|![01](./media/whats-new-app-ui/android_cp_enroll_01_post_1709.png)|
|![02](./media/whats-new-app-ui/android_cp_enroll_02_before_1709.png)|![02](./media/whats-new-app-ui/android_cp_enroll_02_post_1709.png)|
|![03](./media/whats-new-app-ui/android_cp_enroll_03_before_1709.png)|![03](./media/whats-new-app-ui/android_cp_enroll_03_post_1709.png)|
|![04](./media/whats-new-app-ui/android_cp_enroll_04_before_1709.png)|![04](./media/whats-new-app-ui/android_cp_enroll_04_post_1709.png)|
|![05](./media/whats-new-app-ui/android_cp_enroll_05_before_1709.png)|![05](./media/whats-new-app-ui/android_cp_enroll_05_post_1709.png)|


## <a name="august-2017"></a>2017 年 8 月

### <a name="ios-11-mail-app-will-support-oauth----1196951---"></a>iOS 11 郵件應用程式將會支援 OAuth <!-- 1196951 -->

搭配 Intune 的條件式存取支援在 iOS 裝置上使用 OAuth 進行更安全的驗證。 為了支援進行更安全的驗證，iOS 公司入口網站應用程式的流程已有所改變。 當終端使用者在「郵件」應用程式中嘗試登入新的 Exchange 帳戶時，會出現網頁檢視提示。 在 Intune 中註冊時，使用者會看見要求允許原生「郵件」應用程式存取憑證的提示。 大多數的使用者都不再會看到任何隔離的電子郵件。 現有郵件帳戶會繼續使用基本驗證通訊協定，因此，這些使用者仍會收到隔離的電子郵件。 終端使用者的此登入體驗很類似於 Office Mobile 應用程式的模式。

![在原生郵件應用程式中選取帳戶類型。](./media/whats-new-app-ui/ios-11-ca-email-after-1708-01.png)

![選取 [Exchange] 之後，iOS 裝置會提示您輸入電子郵件地址與帳戶名稱。](./media/whats-new-app-ui/ios-11-ca-email-after-1708-02.png)

![請提供電子郵件地址與帳戶名稱。](./media/whats-new-app-ui/ios-11-ca-email-after-1708-03.png)

![傳送至外部 Microsoft 登入頁面。](./media/whats-new-app-ui/ios-11-ca-email-after-1708-04.png)

![在 Microsoft 頁面上提供密碼。](./media/whats-new-app-ui/ios-11-ca-email-after-1708-05.png)

![Microsoft 會提示使用者註冊裝置以納入管理。](./media/whats-new-app-ui/ios-11-ca-email-after-1708-06.png)

![系統會提示使用者從公司入口網站註冊。](./media/whats-new-app-ui/ios-11-ca-email-after-1708-07.png)



### <a name="intune-mobile-application-management-mam-dialog-boxes-will-have-a-modern-interface----1199015---"></a>Intune 行動應用程式管理 (MAM) 對話方塊會有新式介面 <!-- 1199015 -->

Intune 行動應用程式管理 (MAM) 對話方塊將更新為新式外觀和操作。 這些對話方塊的運作方式會與舊版樣式相同。

**先前經驗**

![舊介面](./media/whats-new-app-ui/NewUI_Old_AttachFileHandler.jpg)

**新式經驗**

![新式介面](./media/whats-new-app-ui/NewUI_Modern_AttachFileHandler.jpg)


### <a name="updates-to-the-device-details-page-on-the-company-portal-app-for-windows-10----1287448---"></a>Windows 10 之公司入口網站應用程式上的 [裝置詳細資料] 頁面更新 <!-- 1287448 -->

Windows 10 的公司入口網站應用程式會將 [類別]  標記從標題下方移至 [裝置詳細資料]  頁面上的屬性。

![Windows 之公司入口網站應用程式的 [裝置詳細資料] 畫面，現在會將 [類別] 欄位顯示為屬性，而不是直接顯示在該畫面的標題下方。](./media/whats-new-app-ui/cp_win10_category_tag_move_after_1708.png)

## <a name="july-2017"></a>2017 年 7 月

### <a name="apps-details-pages-will-display-new-information-for-android-devices---1287476--"></a>應用程式詳細資料頁面將顯示 Android 裝置的新資訊 <!--1287476-->

適用於 Android 之公司入口網站應用程式的應用程式詳細資料頁面，現在會顯示 IT 系統管理員已為該應用程式定義的應用程式類別。

![新的應用程式詳細資料頁面](./media/whats-new-app-ui/cp_android_appdetails_after_1708.png)

### <a name="improved-sign-in-experience-across-company-portal-apps-for-all-platforms---user-story-1132123--"></a>已改善適用於所有平台公司入口網站應用程式的登入體驗 <!--User Story 1132123-->

我們宣布將在幾個月內推出變更，以改進 Android、iOS 和 Windows 版 Intune 公司入口網站應用程式的登入體驗。 當 Azure AD 進行此變更時，新的使用者體驗會自動顯示在所有平台的公司入口網站應用程式上。 此外，使用者現在可以使用產生的一次性驗證碼，從另一部裝置登入公司入口網站。 在使用者需要不使用認證登入的情況下，這特別有用。  

以下您可以看到舊版的登入體驗、使用認證的新登入體驗，以及從另一部裝置登入的新登入體驗。

__舊版登入體驗__

![公司入口網站登入頁面，具有一個人員位於代表網站的圖形前方的圖示。 [登入] 按鈕在下方。 底部的連結會指向 Microsoft 隱私權與 Cookie 資訊。](./media/whats-new-app-ui/cp_ios_aad_signin_before_1704_001.png)

![點選 [登入] 之後，使用者會在此頁面上輸入其認證，此頁面會要求輸入使用者的電子郵件和密碼，以及提供解決密碼失敗的方法。](./media/whats-new-app-ui/cp_ios_aad_signin_before_1704_002.png)

![使用者提供密碼之後，公司入口網站應用程式會登入，並以載入列指出進度。](./media/whats-new-app-ui/cp_ios_aad_signin_before_1704_003.png)

__新的登入體驗__

![公司入口網站登入頁面，具有一個人員位於代表網站的圖形前方的圖示。 下方是 [登入] 按鈕。 底部的連結會指向 Microsoft 隱私權與 Cookie 資訊。](./media/whats-new-app-ui/cp_ios_aad_signin_after_1704_001.png)

![系統會在畫面上單獨提示使用者輸入電子郵件地址，而不是同時提示輸入電子郵件與密碼。](./media/whats-new-app-ui/cp_ios_aad_signin_after_1704_002.png)

![接受使用者的電子郵件地址後，系統會提示使用者輸入密碼。](./media/whats-new-app-ui/cp_ios_aad_signin_after_1704_003.png)

![經過驗證程序之後，公司入口網站應用程式會登入，並以載入列指出進度。](./media/whats-new-app-ui/cp_ios_aad_signin_from_another_device_after_1704_007.png)

__從另一部裝置登入時的新登入體驗__

![公司入口網站登入頁面，具有一個人員位於代表網站的圖形前方的圖示。 下方是 [登入] 按鈕。 底部的連結會指向 Microsoft 隱私權與 Cookie 資訊。](./media/whats-new-app-ui/cp_ios_aad_signin_from_another_device_after_1704_001.png)

點選 [從另一部裝置登入]  連結。

![系統會顯示使用唯一密碼從工作電腦移至 aka.ms/devicelogin 頁面，並使用驗證碼進行登入的指示。](./media/whats-new-app-ui/cp_ios_aad_signin_from_another_device_after_1704_003.png)

啟動瀏覽器，並移至 [https://aka.ms/devicelogin](https://aka.ms/devicelogin)。

![使用者工作電腦上的瀏覽器 (而非公司入口網站應用程式) 的影像。 顯示的 [裝置登入] 頁面提示使用者輸入在公司入口網站應用程式中收到的驗證碼。](./media/whats-new-app-ui/cp_ios_aad_signin_from_another_device_after_1704_004.png)

輸入您在公司入口網站應用程式中看到的驗證碼。 當您選取 [繼續]  時，您可以使用貴公司所支援的任何方法 (例如智慧卡) 進行驗證。

![使用者已將唯一驗證碼輸入至欄位，且 [裝置登入] 網站已要求確認 Intune 公司入口網站是接收驗證以登入的正確應用程式。](./media/whats-new-app-ui/cp_ios_aad_signin_from_another_device_after_1704_005.png)

![確認頁面指出使用者現已在其裝置上登入公司入口網站應用程式，並且可以關閉此頁面。](./media/whats-new-app-ui/cp_ios_aad_signin_from_another_device_after_1704_006.png)

公司入口網站應用程式將會開始登入。

![經過驗證程序之後，公司入口網站應用程式會登入，並以載入列指出進度。](./media/whats-new-app-ui/cp_ios_aad_signin_from_another_device_after_1704_007.png)

## <a name="june-2017"></a>2017 年 6 月

### <a name="company-portal-app-for-android-now-has-a-new-end-user-experience-for-app-protection-policies"></a>Android 公司入口網站應用程式的應用程式防護原則現在有新的使用者體驗
根據客戶的意見反應，我們已修改 Android 公司入口網站應用程式，以顯示 [存取公司內容]  按鈕。 目的是為了防止使用者在他們只需要存取支援應用程式保護原則 (Intune 行動應用程式管理的一項功能) 的應用程式時，不必要地進行註冊程序。

使用者將點選 [存取公司內容]  按鈕，而非開始註冊裝置。

![Android 公司入口網站應用程式的影像，這會在中間顯示「存取公司內容」大型文字，而不是如同標準案例提供立即註冊選項](./media/whats-new-app-ui/and_access_company_content_after_1706.png)

接著，使用者會進入公司入口網站來授權應用程式在其裝置上使用，公司入口網站會在其中確認他們的認證。

![公司入口網站的影像，正在確認登入。](./media/whats-new-app-ui/and_iwp_sign_in_auth_page_after_1706.png)

透過點選 [動作]  功能表，裝置仍可註冊以接受完整管理。

![Android 公司入口網站應用程式的影像，其中顯示畫面右上角的功能表含有仍可註冊裝置的選項。](./media/whats-new-app-ui/and_sign_in_menu_after_app_protection_policy_enrolled_after_1706.png)

### <a name="improvements-to-app-syncing-with-windows-10-creators-update---676505--"></a>透過 Windows 10 Creators Update 改善應用程式同步處理 <!--676505-->

Windows 10 版公司入口網站應用程式現在會針對具有 Windows 10 Creators Update (版本 1703) 之裝置的應用程式安裝要求，自動初始化同步處理。 這會減少應用程式安裝在「待同步」狀態期間出現拖延的問題。 此外，使用者將能夠從應用程式內手動起始同步。

![Windows 10 公司入口網站應用程式的影像，在其中從公司入口網站應用程式市集下載 Microsoft Word 的作業處於擱置狀態。](./media/whats-new-app-ui/w10_download_pending_after_1706.png)

![Windows 10 公司入口網站應用程式的影像，其中顯示新的自動同步處理狀態與一則狀態訊息，該訊息指出裝置正在同步處理，並嘗試下載應用程式。](./media/whats-new-app-ui/w10_download_pending_syncing_after_1706.png)

### <a name="new-guided-experience-for-windows-10-company-portal----1058938---"></a>Windows 10 公司入口網站新型引導式體驗 <!---1058938--->
Windows 10 的公司入口網站應用程式將包含之前尚未確定或註冊之裝置的引導式 Intune 逐步解說體驗。 此全新體驗提供逐步指示，引導使用者向 Azure Active Directory 註冊 (條件式存取功能所需)，以及 MDM 註冊 (裝置管理功能所需)。 此引導式體驗將可從公司入口網站首頁上存取。 未完成註冊的使用者可以繼續使用應用程式，但可使用的功能將會受到限制。

此更新只會顯示在執行 Windows 10 年度更新版 (組建 1607) 或更高版本的裝置上。

![Windows 10 公司入口網站應用程式登陸頁面的影像，其中 [裝置] 清單中間的狀態訊息會告知使用者，他們所在的裝置尚未設定為公司用，以及使用者應選取該訊息來開始設定。](./media/whats-new-app-ui/win10_guided_enroll_select_setup_after_1706.png)

![Windows 10 公司入口網站應用程式設定頁面的影像，警告使用者他們需要將公司帳戶新增到此裝置，然後可以註冊它以接受管理。](./media/whats-new-app-ui/win10_guided_enroll_we_help_setup_after_1706.png)

![Windows 10 公司入口網站應用程式已將公司帳戶新增到此裝置頁面的影像，告知使用者他們需要移至設定應用程式，然後選取 [連線] 以完成註冊。 這麼做之後，畫面會告知使用者他們必須返回公司入口網站應用程式，以完成註冊。](./media/whats-new-app-ui/win10_guided_enroll_leaving_for_iwp_after_1706.png)

![Windows 10 公司入口網站應用程式註冊以接受管理畫面的影像，其中顯示完成的狀態訊息，指出使用者的裝置現在已註冊，以及他們應點選 [下一步] 按鈕以繼續。](./media/whats-new-app-ui/win10_guided_enroll_youre_now_enrolled_after_1706.png)

![Windows 10 公司入口網站應用程式完成畫面的影像，可讓使用者知道它們已完整設定，以及裝置已在正確加入公司帳戶的情況下註冊。](./media/whats-new-app-ui/win10_guided_enroll_youre_all_set_after_1706.png)

### <a name="new-menu-action-to-easily-remove-company-portal---1164569--"></a>新的功能表動作可輕鬆移除公司入口網站 <!--1164569-->
根據使用者意見反應，Android 版公司入口網站應用程式已新增功能表動作，可從裝置起始公司入口網站的移除。 這個動作會從 Intune 管理移除裝置，讓使用者可以從裝置移除應用程式。

![Android 版公司入口網站應用程式的影像，右上角是開啟的動作功能表。 新的 [移除公司入口網站] 選項是第三個選項，位於 [我的設定檔] 和 [設定] 底下，在 [條款及條件]、[說明與意見反應] 和 [關於] 之上。](./media/whats-new-app-ui/android_remove_cp_menu_action_after_1705.png)

![確認對話方塊的影像，從動作功能表選取新的 [移除公司入口網站] 選項後就會顯示。 此對話方塊會告知使用者「若移除公司入口網站，您的裝置將不再受 IT 管理員管理，並可能移除對公司資料、公司應用程式及公司電子郵件的存取權。」 然後，它會要求使用者選取 [是] 以確認要移除公司入口網站應用程式。](./media/whats-new-app-ui/android_remove_cp_menu_confirmation_after_1705.png)

### <a name="improvements-to-the-app-tiles-in-the-company-portal-app-for-ios---1230777--"></a>iOS 版公司入口網站應用程式中應用程式磚的增強功能 <!--1230777-->
我們已更新首頁上應用程式磚的設計，以反映您為公司入口網站設定的商標色彩。

**更新前**

![更新前的 iOS 版公司入口網站應用程式影像，顯示預先設定之 [所有 App]、[精選 App] 和 [類別] 的篩選影像。](./media/whats-new-app-ui/cp_ios_homepage_before_1705.png)

**更新後**

![更新後的 iOS 版公司入口網站應用程式影像，現在反映出可自由選取與組織相關的任何色彩。](./media/whats-new-app-ui/cp_ios_homepage_after_1705.png)

### <a name="account-picker-now-available-for-the-company-portal-app-for-ios"></a>iOS 版公司入口網站應用程式現在有帳戶選擇器可供使用
若使用者已使用工作或學校帳戶登入他們的 iOS 裝置上的其他 Microsoft 應用程式，第一次登入公司入口網站時，他們會看到新的帳戶選擇器。

![帳戶選擇器的影像，顯示一個名為 Robin Swanson 的測試使用者在兩個電子郵件地址之間選擇。 這兩個地址下方有一個按鈕，可讓使用者以其他的帳戶登入。](./media/whats-new-app-ui/cp_ios_multi-account-selector-after-1705.png)

## <a name="april-2017"></a>2017 年 4 月

### <a name="new-icons-for-the-managed-browser-and-the-company-portal---918433-918431--"></a>Managed Browser 和公司入口網站的新圖示 <!--918433, 918431-->

Managed Browser 會同時收到 Android 和 iOS 版應用程式的更新圖示。 此新圖示會包含更新的 Intune 徽章，以使它與 Enterprise Mobility + Security (EM+S) 中的其他應用程式更一致。

<html>
<body>
   <table id="wrapper">
      <tr>
         <td>
            <img src="/intune/media/cp_manbro_before_042017.png" alt="The previous version of the Managed Browser app icon." width="200" height="366" align="center">
          </td>
          <td>
             <img src="/intune/media/cp_manbro_after_042017.png" alt="The updated version of the Managed Browser app icon." width="200" height="366" align="center">
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
            <img src="/intune/media/cp_android_connecting_042017.png" alt="The Company Portal app for Android sign-in screen that shows a partially filled loading bar with the phrase 'Connecting' underneath it." width="200" height="366" align="center">
          </td>
          <td>
             <img src="/intune/media/cp_android_signing_in_042017.png" alt="The Company Portal app for Android sign-in screen that shows a partially filled loading bar with the phrase 'Signing in' underneath it." width="200" height="366" align="center">
           </td>
           <td>
              <img src="/intune/media/cp_android_checking_security_reqs_042017.png" alt="The Company Portal app for Android sign-in screen that shows a partially filled loading bar with the phrase 'Checking for security requirements' underneath it." width="200" height="366" align="center">
           </td>
      </tr>
   </table>
</body>
</html>

### <a name="improved-app-install-status-for-the-windows-10-company-portal-app---676495--"></a>已改善 Windows 10 公司入口網站應用程式的應用程式安裝狀態 <!--676495-->
Windows 10 公司入口網站應用程式現在於應用程式詳細資料頁面提供安裝進度列。 在執行 Windows 10 年度更新版與更新版本裝置上的新式應用程式可支援此功能。

__改進前__ ![舊版載入畫面的影像，其中狀態僅簡單地表示「安裝中」。](./media/whats-new-app-ui/cp_win10_install_status_before_1704.png)

__改進後__ ![更新版本的載入畫面影像，現在會顯示安裝進度列。](./media/whats-new-app-ui/cp_win10_install_status_after_1704.png)

## <a name="february-2017"></a>2017 年 2 月

### <a name="new-user-experience-for-the-company-portal-app-for-android---621622-announced-1702--"></a>Android 版公司入口網站應用程式的新使用者體驗 <!--621622, announced 1702-->
從 3 月起，Android 版公司入口網站應用程式會遵循[素材設計方針](https://material.io/guidelines/material-design/introduction.html)建立更現代化的外觀與風格。 此改善的使用者體驗包括︰

* __色彩__︰索引標籤標頭可根據您的自訂調色盤上色。

![左側是更新前的 Android 版公司入口網站應用程式影像。 右側是更新後的 Android 版公司入口網站應用程式影像。 兩張影像顯示從 [應用程式]、[裝置] 以及 [連絡 IT] 三個可用索引標籤選取的 [裝置] 索引標籤。](./media/whats-new-app-ui/CP_Android_DevicesTab_BeforeAfter.png)

* __介面__：已更新 [應用程式]  索引標籤中的 [精選應用程式]  和 [所有應用程式]  按鈕。[搜尋]  按鈕現在是浮動的動作按鈕。

![左側是更新前的 Android 版公司入口網站應用程式影像。 右側是更新後的 Android 版公司入口網站應用程式影像。 兩張影像顯示從 [應用程式]、[裝置] 以及 [連絡 IT] 三個可用索引標籤選取的 [應用程式] 索引標籤。](./media/whats-new-app-ui/CP_Android_AppsTab_BeforeAfter.png)

* __瀏覽__：[所有應用程式] 會以索引標籤式的檢視顯示 [精選]  、[所有]  與 [類別]  以更方便瀏覽。 [連絡 IT]  已簡化以改善可讀性。

<html>
<body>
   <table id="wrapper">
      <tr>
         <td>
            <img src="/intune/media/cp_android_contactit_after.png" alt="The Company Portal app for Android displaying an updated version of the Contact IT tab. The tab shows available contact information for IT, including phone number, email address, IT website, and IT contact information." width="200" height="366" align="center">
          </td>
      </tr>
   </table>
</body>
</html>

## <a name="january-2017"></a>2017 年 1 月

### <a name="modernizing-the-company-portal-website---753980-announced-1701--"></a>將公司入口網站現代化 <!--753980, announced 1701-->
從 2 月開始，公司入口網站將支援以沒有受管理裝置的使用者為目標的應用程式。 網站會使用新的對比色彩配置、動態圖例及「漢堡功能表」，與其他 Microsoft 產品和服務達成一致， ![公司入口網站左上角新增的漢堡功能表小型影像](./media/whats-new-app-ui/CP_hamburger_menu.png) 其包含技術服務連絡人詳細資料以及現有受管理裝置的相關資訊。 登陸頁面將會予以重新排列，以透過 [精選和最近更新] 應用程式的浮動切換來強調使用者可用的應用程式。

![在左側，影像會顯示具有其舊版 [應用程式]、[我的裝置] 以及 [精選] 和 [類別] 檢視的最新版公司入口網站。 在右側，影像會顯示具有重新整理之應用程式浮動切換、最近發佈的應用程式清單和更新過的 [類別] 檢視的公司入口網站更新版。](./media/whats-new-app-ui/CP_Website_BeforeAfter_Feb2016.png)

## <a name="coming-soon-in-the-ui"></a>即將在 UI 登場
我們計劃將更新使用者介面，以改進使用者的體驗。

> [!Note]
> 下列影像為預覽，宣告的產品可能與展示版本不同。  


## <a name="see-also"></a>請參閱
* [Microsoft Intune 部落格](https://go.microsoft.com/fwlink/?LinkID=273882)
* [雲端平台藍圖](https://www.microsoft.com/cloud-platform/roadmap)
* [Intune 的新功能](whats-new.md)

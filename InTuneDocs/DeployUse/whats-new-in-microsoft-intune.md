---
title: "新功能 | Microsoft Intune"
description: "了解本月 Microsoft Intune 版本的新功能，以及過去的版本"
keywords: 
author: Lindavr
manager: jeffgilb
ms.date: 07/18/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: fab51ee0-638d-4dd4-8d8f-1f263bc11e5c
ms.reviewer: mamoriss
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b8bff8951c8ced7656f007787d614fd277401fd0
ms.openlocfilehash: 35612b07cf18d8038af51cdfac5146b9e8a876fc


---

# Microsoft Intune 的新功能
了解此 Microsoft Intune 版本中的新功能。 您也可以了解即將推出且您應該加以規劃的變更，以及過去版本的相關資訊。

下列變更正在 Intune 的開發過程中。 混合式客戶部署於未來將會支援這些功能 (具備 Intune 的 Configuration Manager)。 如需新混合式功能的詳細資訊，請查看我們的 [Hybrid What’s New](https://technet.microsoft.com/en-US/library/mt718155(TechNet.10).aspx) (混合式新功能) 頁面。


## 2016 年 7 月
## 應用程式管理
### 改善應用程式佈建設定檔更新體驗
Apple iOS 企業營運行動應用程式已內建佈建設定檔，以及透過憑證簽署的程式碼。 當該應用程式於 iOS 裝置上執行時，iOS 會確認該 iOS 應用程式的完整性，並強制執行由佈建設定檔定義的原則。

您用來簽署應用程式的企業簽署憑證通常會持續 3 年。 不過佈建設定檔將會在 1 年後到期。 透過此更新，Intune 會提的工具，可讓您在裝置上有即將到期的應用程式，但憑證仍然有效的情況下，主動將新的佈建設定檔原則部署到裝置。 如需詳細資訊，請參閱[使用 iOS 行動佈建設定檔原則來保持最新的企業營運應用程式](/intune/deploy-use/ios-mobile-app-provisioning-profiles)。
<!--- TFS 1280247--->
### Intune 應用程式的 Xamarin SDK 可供使用
Intune 應用程式 SDK Xamarin 元件可允許您在使用 Xamarin 建置的行動裝置 iOS 和 Android 應用程式中啟用 Intune 行動裝置應用程式管理功能。 您可以在 [Xamarin 市集](https://components.xamarin.com/view/Microsoft.Intune.MAM)中或 [Microsoft Intune Github 頁面](https://github.com/msintuneappsdk)上找到元件。
<!--- TFS 1061478 --->

## 裝置管理
### 提升裝置註冊限制
Intune 已將每位使用者可設定裝置註冊最大值的限制，從 5 部裝置提升到 15 部裝置。
<!---TFS 1289896 --->



## 公司入口網站更新
### 公司入口網站
- **改善註冊 Windows 裝置時的使用者經驗**<br/>
當您使用條件式存取時，在公司入口網站中已釐清 Windows 8.1、Windows 10 Desktop 和 Windows 10 行動裝置版的註冊步驟。 使用者現在會看到個別的「裝置註冊」和「工作場所聯結」步驟，讓使用者能夠更容易看到他們的裝置狀態，並在遇到工作場所聯結 (WPJ) 失敗時完成程序。 個別的步驟應該也能為 IT 系統管理員簡化疑難排解程序。 以前，當終端使用者嘗試註冊且除了 WPJ 以外的註冊步驟都成功時，已註冊的裝置不會顯示在可讓使用者識別的裝置清單中，而造成使用者混淆。

### Android
- **Android 公司入口網站應用程式**<br/>
如果 Android 終端使用者看到錯誤訊息，指出他們的裝置遺漏必要的憑證，他們可以點選 [如何解決此問題] 按鈕，以取得安裝遺失憑證的[步驟](/intune/enduser/your-device-is-missing-a-required-certificate-android#your-device-is-missing-a-certificate-required-by-your-it-administrator)。 如果使用者完成這些步驟，但看見其他其他「遺漏憑證」錯誤訊息，則會要求他們連絡其 IT 系統管理員並提供此[連結](/intune/troubleshoot/troubleshoot-device-enrollment-in-intune#android-certificate-issues)，其中包含 IT 系統管理員可用來解決憑證問題的步驟。

- **將側載應用程式安裝限制於已註冊的裝置**<br/>
Android 裝置已無法透過公司入口網站安裝應用程式，除非該裝置已使用 Android 版 Intune 公司入口網站應用程式在 Intune 註冊。
<!---TFS 1299082--->

### iOS
- **iOS 公司入口網站應用程式中的裝置註冊管理員帳戶變更**<br/>
為了提升效能及規模，Intune 已不再於 iOS 公司入口網站應用程式的 [我的裝置] 窗格中，顯示所有的裝置註冊管理員 (DEM) 裝置。 只有執行應用程式的本機裝置會顯示，只有在透過公司入口網站應用程式註冊時才會顯示。

    DEM 使用者可在本機裝置上執行動作，但是其他已註冊裝置的遠端管理只能從 Intune 管理主控台執行。 此外，Intune 將會使用 DEM 帳戶取代 Apple 裝置註冊方案或 Apple Configurator 工具。 這兩種註冊方法已經支援共用之 iOS 裝置的較少使用者註冊。

    只有在共用裝置的較少使用者註冊無法使用時，才能使用 DEM 帳戶。 如需詳細資訊，請參閱[使用 Microsoft Intune 中的裝置註冊管理員註冊公司所擁有的裝置](https://docs.microsoft.com/en-us/intune/deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune)。
<!---TFS 1233681--->

## Windows 功能名稱的變更
- [Microsoft Passport for Windows](/intune/deploy-use/control-microsoft-passport-settings-on-devices-with-microsoft-intune) 現在稱為 **Windows Hello 企業版**。
- [企業資料保護](https://technet.microsoft.com/itpro/windows/keep-secure/create-edp-policy-using-intune)現在稱為 **Windows 資訊保護**。

## 未來動態
### 從 2016 年 8 月開始，Intune 群組將開始轉換到 Azure Active Directory 群組
Intune 建立了一個使用 Azure Active Directory (AAD) 安全性群組的新的群組管理經驗。 這些以 Azure AD 為基礎的安全性群組可以同時包含使用者和裝置，並將在我們引進新的 Azure 型 Intune 系統管理入口網站時，用於所有的群組管理、原則部署和設定檔部署。

此新體驗將會：
- 讓您不需要在服務之間複製群組。
- 可讓您存取某些新的 Azure Active Directory Premium (AADP) 群組功能。
- 使用 PowerShell 和圖形提供擴充性。
- 統一不同企業行動管理上的群組管理體驗。

為了移動到安全性群組，目前管理主控台中的體驗將會進行一些修改。 這些變更，以及 Azure AD 安全性群組的使用，將會被記錄在 Intune 文件中。

Intune 的新客戶將會比目前的租用戶更快看見某些安全性群組變更。

除了群組管理中的變更之外，下列功能將會被取代：
- 於建立新群組時排除成員或群組
- 「已取消群組的使用者」和「已取消群組的裝置」群組
- 服務系統管理員角色中的「管理群組」
- 通知規則的自訂群組型警示
- 於報告中針對群組進行樞紐分析

如何減輕取代造成之影響的詳細資訊，將會於 8 月發行。

### 針對 Android 公司入口網站在新增「通知」
我們將在 8 月針對 Android 推出公司入口網站的更新，該更新將會在首頁上推出新的「通知」圖示。 點選此圖示將會存取「通知」頁面，並為您的終端使用者顯示公司入口網站應用程式中所有需要注意的項目，例如裝置不相容、註冊更新，以及註冊啟用。 如果您也使用 iOS 公司入口網站應用程式，您應該已能見到該通知體驗。 透過推出「通知」頁面，只要該裝置已經註冊，您便不會在每次啟動或繼續 Android 版的公司入口網站時看見「公司存取設定」頁面。 我們了解有許多使用者已建立終端使用者指南，並樂於在該指南/螢幕擷取畫面可能需要更新時提前收到通知。 請更新您的文件以反映即將推出的體驗變更。 尋找更新的螢幕擷取畫面，請移至：https://aka.ms/androidcpupdate。  



### 雲端藍圖
請參閱 [Cloud Platform roadmap (雲端平台藍圖)](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)，隨時關注 Intune 的最新發展。

### 服務取代
- **變更 iOS 公司入口網站應用程式的支援**<br/>
自七月起，iOS 版 Microsoft Intune 公司入口網站應用程式的所有使用者都必須使用最新版本。 新使用者只可以下載最新版本，目前使用者則需要它的更新。 最新版本需要 iOS 8.0 或更新版本，因此除非他們將其裝置更新為 iOS 8.0 或更新版本，然後將公司入口網站應用程式更新為最新版本，否則執行較舊 iOS 版本的裝置會無法使用公司入口網站或註冊。 執行 iOS 8.0 以下版本的已註冊裝置會繼續受到管理，並且列在 Intune 管理主控台中。  

- **iOS Managed Browser 最低版本已更新為 8.0**<br/>
Intune 將於八月發行的 iOS 版 Microsoft Intune Managed Browser 應用程式更新，將僅支援執行 iOS 8.0 或更新版本的裝置。 雖然 iOS 7.1 裝置仍然可以使用現有的 Managed Browser 應用程式，請建議您的使用者更新至 iOS 8.0 或更新版本，以存取並且充分利用新的 Managed Browser 功能。  
<!---TFS 1313253--->

- **2016 年 9 月起將取代 Windows 8 版和 Windows Phone 8 版公司入口網站應用程式** <br/>
從 2016 年 9 月開始，Microsoft Intune 將結束 Windows Phone 8 和 Windows 8 平台的 Microsoft Intune 公司入口網站應用程式支援。 將裝置更新為 Windows 8.1 和 Windows Phone 8.1，並使用對應的 Windows 8.1 和 Windows Phone 8.1 公司入口網站應用程式繼續將應用程式發佈至這些裝置。
<!---TFS 1255391--->

- **Intune Viewer 應用程式** <br/>
發佈新的 RMS 共用應用程式版本後，我們會移除下列 Intune Viewer 應用程式，從 2016 年 8 月開始︰
    - Intune AV Viewer
    - Intune PDF Viewer
    - 來自 Google Play 的 Intune Image Viewer for Android

  我們建議使用新的 [Android 版授權管理應用程式 (RMS 共用)](https://docs.microsoft.com/en-us/intune/deploy-use/end-user-experience-for-mam-enabled-apps-with-microsoft-intune#viewing-media-files-with-the-rights-management-sharing-app)，而不是使用 Intune Viewer 應用程式，它可讓您部署一個應用程式，而不必部署三個不同的應用程式，即可安全地在 Android 裝置上檢視公司檔案。 當 Intune Viewer 應用程式不再受到支援時，它將會從 Google 商店移除，且未來無法提供使用。

<!--- - **Custom Group Targeting of Notification Rules Removal.**<br/>
Intune notification rules define who an email alert will be sent to from Intune. Currently, you can configure notification rules to send emails to all users of devices in an Intune device group that you created. From around June 1st 2016 moving forward, targeting user-created groups will no longer be supported.

    Today, to target a notification rule to a group you created from the Microsoft Intune administration console, you would take the following steps:

    In the **Admin** workspace, click **Notification Rules** > **Create New Rule**

    In step two of the Create Notification Rule Wizard, select the device groups which the rule will target. This step, “select device groups”, is being removed from the Intune Console.

    The preliminary timeline for this change is as follows:
    - In August, 2016, new tenants will not see step two of the Create Notification Rule Wizard. Exiting tenants are unaffected.
    - Around September, 2016, some existing tenants will not see the “select device groups” in the wizard.
    - Around November, 2016, we expect that all tenants will not see the “select device groups” in the wizard.

--->



## 舊版 Intune
如果您想要查看過去六個月期間在 Intune 中的發行內容，它們會列在[舊版 Intune](previous-intune-releases.md) 一文中。

### 請參閱
* [Microsoft Intune 部落格](http://go.microsoft.com/fwlink/?LinkID=273882)
* [雲端平台藍圖](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)



<!--HONumber=Jul16_HO3-->



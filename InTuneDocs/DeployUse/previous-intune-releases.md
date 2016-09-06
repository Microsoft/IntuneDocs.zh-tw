---
title: "舊版 | Microsoft Intune"
description: 
keywords: 
author: Lindavr
manager: angrobe
ms.date: 07/18/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 45dad14a-d412-488d-bb1e-ad990ea503df
ROBOTS: noindex,nofollow
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 57570fcf2f738b68a01bb1c5fc8962c7ef117920
ms.openlocfilehash: 43546721245f92309d86c496dbcde7900a598ed0


---

# 舊版 Intune
## 2016 年 7 月
### 應用程式管理
#### 改善應用程式佈建設定檔更新體驗
Apple iOS 企業營運行動應用程式已內建佈建設定檔，以及透過憑證簽署的程式碼。 當該應用程式於 iOS 裝置上執行時，iOS 會確認該 iOS 應用程式的完整性，並強制執行由佈建設定檔定義的原則。

您用來簽署應用程式的企業簽署憑證通常會持續 3 年。 不過佈建設定檔將會在 1 年後到期。 透過此更新，Intune 會提的工具，可讓您在裝置上有即將到期的應用程式，但憑證仍然有效的情況下，主動將新的佈建設定檔原則部署到裝置。 如需詳細資訊，請參閱[使用 iOS 行動佈建設定檔原則來保持最新的企業營運應用程式](/intune/deploy-use/ios-mobile-app-provisioning-profiles)。
<!--- TFS 1280247--->
#### Intune 應用程式的 Xamarin SDK 可供使用
Intune 應用程式 SDK Xamarin 元件可允許您在使用 Xamarin 建置的行動裝置 iOS 和 Android 應用程式中啟用 Intune 行動裝置應用程式管理功能。 您可以在 [Xamarin 市集](https://components.xamarin.com/view/Microsoft.Intune.MAM)中或 [Microsoft Intune Github 頁面](https://github.com/msintuneappsdk)上找到元件。
<!--- TFS 1061478 --->

### 裝置管理
#### 提升裝置註冊限制
Intune 已將每位使用者可設定裝置註冊最大值的限制，從 5 部裝置提升到 15 部裝置。
<!---TFS 1289896 --->

#### 在執行 Intune 用戶端軟體之 Windows 電腦的 TeamViewer 整合
對於執行 Intune 用戶端的 Windows 電腦，[TeamViewer](https://www.teamviewer.com) 整合可讓您建立與 Windows 電腦的遠端協助工作階段，以協助支援終端使用者支援人員部門。 這包括 Windows 7、8、8.1 和 Windows 10。 如需詳細資訊，請參閱[使用 Microsoft Intune 電腦用戶端的一般 Windows 電腦管理工作](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md)。
<!---TFS 1284856--->

### 公司入口網站更新
#### 公司入口網站
- **改善註冊 Windows 裝置時的使用者經驗**<br/>
當您使用條件式存取時，在公司入口網站中已釐清 Windows 8.1、Windows 10 Desktop 和 Windows 10 行動裝置版的註冊步驟。 使用者現在會看到個別的「裝置註冊」和「工作場所聯結」步驟，讓使用者能夠更容易看到他們的裝置狀態，並在遇到工作場所聯結 (WPJ) 失敗時完成程序。 個別的步驟應該也能為 IT 系統管理員簡化疑難排解程序。 以前，當終端使用者嘗試註冊且除了 WPJ 以外的註冊步驟都成功時，已註冊的裝置不會顯示在可讓使用者識別的裝置清單中，而造成使用者混淆。

#### Android
- **Android 公司入口網站應用程式**<br/>
如果 Android 終端使用者看到錯誤訊息，指出他們的裝置遺漏必要的憑證，他們可以點選 [如何解決此問題] 按鈕，以取得安裝遺失憑證的[步驟](/intune/enduser/your-device-is-missing-a-required-certificate-android#your-device-is-missing-a-certificate-required-by-your-it-administrator)。 如果使用者完成這些步驟，但看見其他其他「遺漏憑證」錯誤訊息，則會要求他們連絡其 IT 系統管理員並提供此[連結](/intune/troubleshoot/troubleshoot-device-enrollment-in-intune#android-certificate-issues)，其中包含 IT 系統管理員可用來解決憑證問題的步驟。

- **將側載應用程式安裝限制於已註冊的裝置**<br/>
Android 裝置已無法透過公司入口網站安裝應用程式，除非該裝置已使用 Android 版 Intune 公司入口網站應用程式在 Intune 註冊。
<!---TFS 1299082--->

#### iOS
- **iOS 公司入口網站應用程式中的裝置註冊管理員帳戶變更**<br/>
為了提升效能及規模，Intune 已不再於 iOS 公司入口網站應用程式的 [我的裝置] 窗格中，顯示所有的裝置註冊管理員 (DEM) 裝置。 只有執行應用程式的本機裝置會顯示，只有在透過公司入口網站應用程式註冊時才會顯示。

DEM 使用者可在本機裝置上執行動作，但是其他已註冊裝置的遠端管理只能從 Intune 管理主控台執行。 此外，Intune 將會使用 DEM 帳戶取代 Apple 裝置註冊方案或 Apple Configurator 工具。 這兩種註冊方法已經支援共用之 iOS 裝置的較少使用者註冊。

只有在共用裝置的較少使用者註冊無法使用時，才能使用 DEM 帳戶。 如需詳細資訊，請參閱[使用 Microsoft Intune 中的裝置註冊管理員註冊公司所擁有的裝置](https://docs.microsoft.com/en-us/intune/deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune)。
<!---TFS 1233681--->

### Windows 功能名稱的變更
- [Microsoft Passport for Windows](control-microsoft-passport-settings-on-devices-with-microsoft-intune.md) 現在稱為 **Windows Hello 企業版**。
- [企業資料保護](https://technet.microsoft.com/itpro/windows/keep-secure/create-edp-policy-using-intune)現在稱為 **Windows 資訊保護**。

## 2016 年 6 月
### Intune 服務健全狀況
Intune 的服務健全狀況資訊已與其他 Microsoft 服務一起移至中央位置。 現在，您會在 Office 365 管理入口網站的 [服務健全狀況] 下發現這項資訊。 如需詳細資訊，請參閱[這篇部落格文章](https://blogs.technet.microsoft.com/enterprisemobility/2016/04/28/intune-service-health-is-now-available-in-the-office-365-portal/)。

### 應用程式管理
- **改善 Windows 10 企業資料的原則設定經驗。** 我們強化了建立應用程式規則、指定網路邊界定義及其他企業資料保護設定等功能，從而提升 Windows 10 企業資料保護原則設定經驗。 若要深入了解，請參閱 [Create an enterprise data protection (EDP) policy using Microsoft Intune](https://technet.microsoft.com/itpro/windows/keep-secure/create-edp-policy-using-intune) (使用 Microsoft Intune 建立企業資料保護 (EDP) 原則)。


### 裝置管理
- **Windows Defender 原則設定可防止潛在的垃圾應用程式。** Windows 10 Desktop 與行動裝置版的一般設定原則中，加入了一項新的 Windows Defender 設定，稱為**偵測潛在的垃圾應用程式**。 您可以使用此設定保護已經註冊的 Windows 桌上型電腦，避免執行被 Windows defender 歸類為潛在垃圾應用程式的軟體。 您可以不執行這些應用程式，也可以使用稽核模式，在安裝潛在垃圾應用程式時回報。 如需詳細資訊，請參閱 [Microsoft Intune 的 Windows 10 原則設定](https://docs.microsoft.com/en-us/intune/deploy-use/windows-10-policy-settings-in-microsoft-intune)
<!---TFS 1244478--->

### 條件式存取
- **Intune 的 Cisco ISE 網路存取控制原則。**  同時使用 Cisco Identity Service Engine (ISE) 2.1 與 Microsoft Intune 的客戶，可以在 ISE 中設定網路存取控制原則。

    若要使用此原則，裝置必須透過 WiFi 或 VPN 連線到網路，而且必須符合下列條件，才具備存取資格︰

    * 必須是 Intune 管理的裝置。
    * 必須符合所部署的任何 Intune 相容性原則。

 不相容裝置的使用者會收到提示，要求其註冊及修復任何相容性問題，才能獲得存取權。
- **瀏覽器的條件存取** 您可以設定 [Exchange Online](restrict-access-to-exchange-online-with-microsoft-intune.md) 和 [SharePoint Online](restrict-access-to-sharepoint-online-with-microsoft-intune.md) 的條件式存取原則，以便只能從受管理和相容的 iOS 和 Android 裝置上的支援瀏覽器存取它們。 嘗試使用 iOS 和 Android 裝置登入 Outlook Web Access (OWA) 和 SharePoint 網站的使用者將會收到提示，以其裝置向 Intune 註冊，以及在完成登入之前修正任何不相容問題。
<!---TFS 1175844--->

- **Dynamics CRM Online 支援條件式存取。** 您可以設定 [Dynamics CRM Online](restrict-access-to-dynamics-crm-online-with-microsoft-intune.md) 的條件式存取原則，以便只有受管理和相容的 iOS 和 Android 裝置可以存取它。 嘗試在 iOS 和 Android 上登入 Dynamics CRM 行動應用程式的使用者將會收到提示，在登入完成之前向 Intune 註冊並補救任何不相容問題。
<!---TFS1295358--->

##E 公司入口網站更新

#### Android 公司入口網站應用程式

- 當 IT 系統管理員套用新的「裝置必須防止從不明來源安裝應用程式 (Android 4.0+)」原則時，使用 Android 4.0 或更新版本之裝置的使用者會看到訊息：「必須停用來自未知來源的安裝」。 使用者必須移至 [設定]  >  [安全性]，並關閉 [未知來源]。 相容性訊息中的連結可讓使用者取得訊息的[相關資訊](/Intune/EndUser/you-are-asked-to-turn-off-unknown-sources-android)，以及為什麼他們需要關閉設定。

- 當 IT 系統管理員套用新的「裝置必須已啟用掃描應用程式的安全性威脅 (Android 4.0+)」原則時，使用 Android 4.0 或更新版本之裝置的使用者將會看到訊息：「掃描裝置中的安全性威脅」。 使用者必須移至 [設定]  >  [Google]  >  [安全性]，然後開啟 [掃描裝置中的安全性威脅]。 相容性訊息中的連結可讓使用者取得訊息的[相關資訊](/Intune/EndUser/you-are-asked-to-turn-on-scan-device-for-security-threats-android)，以及為什麼他們需要開啟設定。

- 當 IT 系統管理員套用新的「USB 偵錯需為停用 (Android 4.2+)」原則時，使用 Android 4.2 或更新版本之裝置的使用者將會看到訊息：「必須停用 USB 偵錯」。 使用者必須移至 [設定]  >  [開發人員選項]，並關閉 [USB 偵錯]。 相容性訊息中的連結可讓使用者取得訊息的[相關資訊](/Intune/EndUser/you-are-asked-to-turn-off-usb-debugging-android)，以及為什麼他們需要關閉設定。

- 當 IT 系統管理員套用新的「Android 安全性修補程式等級下限 (Android 6.0+)」原則時，使用 Android 6.0 或更新版本之裝置的使用者將會看到訊息：「此裝置不符合最低的 Android 安全性修補程式等級」。 使用者必須安裝所需的安全性修補程式。 相容性訊息中的連結可讓使用者取得如何安裝必要安全性修補程式以及查看目前已安裝之安全性修補程式的[相關資訊](/Intune/EndUser/you-are-asked-to-turn-on-scan-device-for-security-threats-android)。

#### iOS 公司入口網站應用程式

- 當使用者安裝企業營運應用程式時，就會看到改善的應用程式安裝體驗。 如果應用程式安裝花很長的時間，使用者可以手動同步處理他們的裝置，以強制同步處理程序繼續執行。 若要檢閱使用者指示，請參閱[手動同步處理您的 iOS 裝置](/Intune/EndUser/sync-your-device-manually-ios)。

- 適用於 iOS 的 Microsoft Intune 公司入口網站應用程式已更新為支援 iOS 8.0 和更新版本。 此更新表示唯有裝置執行的是 iOS 8.0 版或更新版本時，使用者才能安裝公司入口網站應用程式以及在 Intune 中註冊新的裝置。 若使用者已經註冊在不支援的 iOS 版本中執行的裝置，則可繼續使用其裝置上的公司入口網站應用程式。


## 2016 年 5 月

混合式部署也支援所有這些功能 (Configuration Manager 與 Intune)。 如需新混合式功能的詳細資訊，請查看 [Hybrid What’s New](https://technet.microsoft.com/en-us/library/mt718155.aspx) (混合式新功能) 頁面。

### 文件
歡迎使用 [docs.microsoft.com](https://docs.microsoft.com/en-us/intune) 的預覽版本！
這是全新的現代內容平台，其設計是為了讓您，也就是我們的客戶，更輕鬆地了解和使用 Intune。
若要閱讀所有新功能，請參閱 [Introducing docs.microsoft.com](https://docs.microsoft.com/teamblog/introducing-docs-microsoft-com/) (docs.microsoft.com 簡介)

### Intune 服務健全狀況
Intune 的服務健全狀況資訊已與其他 Microsoft 服務一起移至中央位置。 現在，您會在 [Office 365 管理入口網站](https://portal.office.com/Admin/Default.aspx) 的 [服務健全狀況] 下發現這項資訊。
如需詳細資訊，請參閱[這篇部落格文章](https://blogs.technet.microsoft.com/microsoftintune/2016/04/28/intune-service-health-is-now-available-in-the-office-365-portal/)。


### 應用程式管理
- **MAM SDK︰支援 PIN 長度組態。** 您可以將 MAM 應用程式的 PIN 長度指定為類似裝置 PIN 的長度。 這將需要使用者符合您設定的新限制。 他們會看到稍微修改的 PIN 畫面以說明較長的輸入。 如需詳細資訊，請參閱 [MAM policy settings for Android](android-mam-policy-settings.md) (適用於 Android 的 MAM 原則設定) 和 [MAM policy settings for iOS](ios-mam-policy-settings.md) (適用於 iOS 的 MAM 原則設定)。

- **iOS 和 Android 的商務用 Skype。** 您現在可以將目標放在具備[無註冊原則之 MAM](get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune.md) 的商務用 Skype。 一旦使用者登入，將會套用 MAM 原則。

- **新的應用程式可用來使用 MAM 原則進行管理。** 適用於 Android 的 Microsoft Word、Excel 和 PowerPoint 應用程式現在可以在未向 Intune 註冊的裝置上與 MAM 原則相關聯。 如需受支援應用程式的完整清單，請移至 Microsoft Intune 應用程式夥伴頁面上的 [Microsoft Intune 行動應用程式庫](https://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/partners.aspx)。


### 公司入口網站更新

#### Android 公司入口網站應用程式
- **使用者快顯通知**：使用者註冊其裝置或從公司入口網站移除他們的裝置時，將會看到來自 Android 公司入口網站應用程式的快顯通知。

- **Android 公司入口網站應用程式中的裝置註冊管理員帳戶的變更。** 為了改善效能和擴充，Intune 將不再於 Android 公司入口網站的 [我的裝置] 窗格中，顯示所有的裝置註冊管理員 (DEM) 裝置。 只有執行應用程式的本機裝置會顯示，只有在透過公司入口網站應用程式註冊時才會顯示。 DEM 使用者可在本機裝置上執行動作，但是其他已註冊裝置的遠端管理只能從 Intune 管理主控台執行。

#### 公司入口網站
- **公司入口網站：裝置識別橫幅將提供詳細資訊給使用者。** 使用者可以更輕鬆地識別他們在使用公司入口網站時所選取的裝置。 如果選取了錯誤的裝置，他們可以藉由點選首頁橫幅中的 [點選這裡] 連結來選取正確的裝置。

## 未來動態
- **訊息中心 UI 入門訓練**。 在 Intune 移轉至 [Office 365 管理入口網站](https://portal.office.com/)的過程中，我們將開始利用他們的訊息中心進行新功能和其他通知等通訊。 此外，藉由安裝隨附的 Office 365 管理行動應用程式，您的行動電話可以接收通知，並輕鬆地將任何訊息轉送至使用者或通訊群組別名。
我們將開始使用訊息中心以及 5 月的版本，以在更新完成時通知您，並將包含新的改善 Intune 功能的資訊。 立即登入 [Office 365 管理入口網站](https://portal.office.com/)，然後選擇左側瀏覽窗格中的 [訊息中心] 選項來查看訊息中心。

- **裝置註冊管理員帳戶的變更**。 為了改善效能和擴充，Intune 將不再於 iOS 公司入口網站的 [我的裝置] 窗格中，顯示**所有**的裝置註冊管理員 (DEM) 裝置。 只有執行應用程式的本機裝置會顯示，只有在透過公司入口網站應用程式註冊時才會顯示。 DEM 使用者可在本機裝置上執行動作，但是其他已註冊裝置的遠端管理只能從 Intune 管理主控台執行。 此外，Intune 將會使用 DEM 帳戶取代 Apple 裝置註冊方案或 Apple Configurator 工具。 這兩種註冊方法已經支援共用之 iOS 裝置的較少使用者註冊。 只有在共用裝置的較少使用者註冊無法使用時，才能使用 DEM 帳戶。

### 雲端藍圖
請參閱 [Cloud Platform roadmap (雲端平台藍圖)](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)，隨時關注 Intune 的最新發展。

### 服務取代
- **Intune Viewer 應用程式。** 發佈新的 RMS 共用應用程式版本後，我們會移除下列 Intune Viewer 應用程式，從 2016 年 8 月開始︰
    - Intune AV Viewer
    - Intune PDF Viewer
    - 來自 Google Play 的 Intune Image Viewer for Android

  我們建議使用 Android 的新授權管理應用程式 (RMS 共用)，而不是使用 Intune Viewer 應用程式，它可讓您部署一個應用程式，而不必部署三個不同的應用程式，即可安全地在 Android 裝置上檢視公司檔案。 進一步了解 RMS 共用應用程式 (使用文件連結)。

- **通知規則移除的自訂群組目標。**
Intune 通知規則會定義要從 Intune 傳送電子郵件警示給誰。 目前，您可以設定通知規則，傳送電子郵件給您建立之 Intune 裝置群組中裝置的所有使用者。 從 2016 年 6 月 1 日起，將不再支援將目標設定為使用者建立的群組。

    現在，若要將通知規則目標設定為您從 Microsoft Intune 管理主控台建立的群組，您可以採取下列步驟︰

    在 [管理] 工作區中，按一下 [通知規則] > [建立新規則]

    在 [建立通知規則精靈] 的步驟二中，選取規則以其作為目標的裝置群組。 此「選取裝置群組」步驟已從 Intune 主控台移除。

    這項變更的初步時間軸如下︰
    - 在 2016 年 6 月，新租用戶將不會看到 [建立通知規則精靈] 的步驟 2。 現有租用戶不受影響。
    - 在 2016 年 8 月左右，某些現有的租用戶將不會在精靈中看到 [選取裝置群組]。
    - 在 2016 年 10 月左右，我們預期所有租用戶都將不會在精靈中看到 [選取裝置群組]。


- **支援的 iOS 公司入口網站應用程式變更**。 在未來的幾個月，iOS 的 Microsoft Intune 公司入口網站應用程式將會有更新，只支援執行 8.0 或更新版本的 iOS 裝置。 使用者將無法註冊執行 iOS 8.0 以下版本的新裝置。 執行 iOS 8.0 以下版本的已註冊裝置會繼續受到管理，並且將在有限的時間內，可以繼續使用公司入口網站應用程式。 不過，裝置必須為 iOS 8.0 或更新版本，才能存取公司入口網站應用程式的最新版本。 我們鼓勵您通知使用者更新到 iOS 8.0 或更新版本，以便完全利用 Intune 的新功能。  


## 2016 年 4 月
混合式客戶也支援這些功能 (Configuration Manager 與 Intune 整合)。
### 應用程式管理
- **MAM 使用者相容性。**
您現在可以檢視 Azure Active Directory (AAD) 租用戶中任一使用者的應用程式管理原則[狀態](monitor-mobile-app-management-policies-with-Microsoft-Intune.md)。 這包括：
   - 裝置
   - 裝置上的應用程式

   狀態值：

   **已存回**︰表示原則已部署至使用者，且已使用工作內容中的應用程式，並成功接收原則。

    **未存回**︰表示原則已部署至使用者，但是應用程式從那時起並未在工作內容中使用。


- **避免 Outlook 連絡人同步處理 (Android) 的 MAM 控制項。**
新的設定可供[行動應用程式管理](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md)使用，而不需要裝置註冊。 此設定可讓您防止應用程式在 Android 裝置上將連絡人同步處理至原生通訊錄。 啟用此設定時，目標應用程式將不再能夠儲存連絡人到原生通訊錄。 停用此設定時，目標應用程式將能夠儲存連絡人到原生通訊錄。 當您[從遠端抹除裝置或應用程式](wipe-managed-company-app-data-with-Microsoft-Intune.md)時，將會移除所有已儲存至原生通訊錄的連絡人。 在 Android 裝置上的 Outlook 應用程式一開始支援這個新的設定。

### 裝置管理
- **公司擁有裝置的電話號碼識別。** 分類為「公司」的電話現在會在 (舉例而言) 您執行行動裝置清查報表時利用其完整電話號碼加以識別。 BYOD 電話號碼會持續以 **** 遮罩，僅顯示最後 4 位數。


### 公司入口網站更新
**Android 公司入口網站應用程式**：尚未在 Intune 中註冊其裝置，且沒有安裝正確憑證的使用者將無法登入 Android 公司入口網站應用程式，而且會看到以下訊息 -「您無法登入，因為您的裝置缺少必要的憑證」。 此訊息包含使用者可以點選以參閱安裝憑證的指示之「如何解決此問題」連結。 若要查看使用者需遵循才能解決此問題的步驟，請參閱[您的裝置遺漏必要的憑證](https://technet.microsoft.com/library/mt502762.aspx#BKMK_andr_cert_missing)。

**iOS 公司入口網站應用程式**：支援已新增至下拉以更新動作來重新整理主畫面上的內容，其中包括列出的應用程式、列出的裝置，以及 IT 連絡人資訊。 下拉更新動作並未檢查相容性或原則資訊，而這可以透過選取目前裝置的磚並點選 [同步處理] 按鈕來完成。

**Windows 10 Mobile 和 Windows Phone 8.1 公司入口網站應用程式**：當使用者安裝企業營運應用程式時，就會看到改善的應用程式安裝體驗。 如果應用程式安裝花很長的時間，使用者可以手動同步處理他們的裝置，以強制同步處理程序繼續執行。 若要檢閱使用者指示，請參閱[以手動方式同步處理您的裝置，以加速應用程式安裝](https://technet.microsoft.com/library/mt427782.aspx#BKMK_win10m_wp81_sync_manually)。

**公司入口網站**：當 Windows 10 Mobile 和 Windows Phone 8.1 使用者安裝企業營運應用程式時，他們會看到下列新狀態，可提供其安裝狀態的詳細資訊︰

* **正在等待裝置同步處理** – 使用者已點選 [安裝]，而裝置會嘗試與 Intune 基礎結構同步處理。 安裝完成之前需要同步處理。 「正在等待裝置同步處理」的訊息也是一個連結，使用者可以點選以在同步處理程序花了較長的時間或已停止時，查看如何手動將他們的裝置與 Intune 同步處理的[指示](https://technet.microsoft.com/library/mt590895.aspx#BKMK_iwp_sync_manually)。
* **正在下載** – 正在處理使用者的下載要求，且裝置正在下載與安裝應用程式。

新增這些狀態之前，如果應用程式安裝花了較長的時間，會讓使用者混淆，因為他們只看到「正在安裝」狀態，可能會在螢幕上維持時小數。 新增狀態表示，使用者現在就可以點選 [正在等待裝置同步處理] 連結，並遵循指示以強制同步處理程序繼續執行，而不是呼叫支援。


## 2016 年 3 月
### 2016 年 3 月 29 日的新功能
Windows 10 一般組態原則的更新除外，所有在 2016 年 3 月 29 日發行的功能也支援供混合式客戶使用 (Configuration Manager 與 Intune 整合)。 即將推出 Windows 10 一般組態原則更新的混合式支援。 請注意，部分功能可能需要最新版本的 Configuration Manager。

### 應用程式管理
- **避免 Outlook 連絡人同步處理 (iOS) 的 MAM 控制項。** 新的設定可供行動應用程式管理使用，而不需要裝置註冊。 此設定可讓您防止應用程式在 iOS 裝置上將連絡人同步處理至原生通訊錄。 啟用此設定時，應用程式將不再能夠儲存連絡人到原生通訊錄。 啟用此設定時，應用程式將能夠儲存連絡人到原生通訊錄。 當您選擇性地抹除裝置時，將會移除所有已儲存至原生通訊錄的所有連絡人。 iOS 裝置上的 Outlook 應用程式支援這個新的設定。 如需這個主題以及其他設定的詳細資訊，請參閱[建立和部署 MAM 原則](https://technet.microsoft.com/en-us/library/dn292747.aspx)。

### 存取控制
- **商務用 Skype Online 支援條件式存取。** 您可以設定商務用 Skype Online 的條件式存取原則，這樣一來，只有受管理和相容的 iOS 和 Android 裝置可以存取它。 嘗試在 iOS 和 Android 上登入商務用 Skype 行動應用程式的使用者將會收到提示，在登入完成之前向 Intune 註冊並修正任何不相容問題。 如需詳細資訊，請參閱[管理商務用 Skype Online 的存取權](https://technet.microsoft.com/en-us/library/mt695297.aspx)。

### 裝置管理
- **iOS 9.3 的 Intune 支援。** 3 月 21 日星期一，Apple 宣佈推出 iOS 9.3。 我們努力確保 Microsoft Intune 與最新版 Apple 行動作業系統相容，[我們很高興宣佈 Intune 支援管理 iOS 9.3 裝置](https://blogs.technet.microsoft.com/microsoftintune/2016/03/23/microsoft-intune-provides-support-for-ios-9-3/)。

  當使用者將裝置升級到 iOS 9.3 時，所有目前可用來管理 iOS 裝置的 Intune 功能將繼續順利運作。 此外，iOS 9.3 目前也支援供混合式客戶使用 (Configuration Manager 與 Intune 整合)。

- **Windows 10 一般組態原則現在有設定可在已註冊的 Windows 10 電腦上的管理 Windows Defender。** 如需詳細資訊，請參閱 [Microsoft Intune 的 Windows 10 組態原則設定](https://technet.microsoft.com/en-us/library/mt404697.aspx)。


### 公司入口網站

- **直接從公司入口網站可取得的 Windows 應用程式套件。** Windows 8、Windows 8.1 和 Windows RT 電腦的使用者現在可以直接從公司入口網站安裝 Windows 應用程式套件 (副檔名為 .appx)。 先前，您必須部署，或使用者必須在裝置上安裝公司入口網站應用程式，才能安裝應用程式。

- **使用者可以從公司入口網站遠端鎖定裝置。** 公司入口網站新增新的 [遠端鎖定] 選項，可讓使用者在裝置遺失或遭竊時，從入口網站遠端鎖定其裝置。 請參閱[使用者指示](https://technet.microsoft.com/library/mt590895.aspx/?wt.mc_id=ui#BKMK_iwp_remote_lock) 下表列出 Intune Standalone 和 Intune 搭配 Configuration Manager 的遠端鎖定的平台支援。

|平台 | 支援詳細資料|
|---------|----------------|
|Android |支援|
|iOS |支援|
|Windows 10 Mobile |只有在電話已設定密碼時才支援|
|Windows 10 Desktop |不支援|
|Windows Phone 8.1 |只有在電話已設定密碼時才支援|
|Windows Phone 8.0 |不支援|
|電腦 (Windows 8.0 及更早版本) |不支援|
|電腦 (Windows 8.1) |不支援|

### 2016 年 3 月 10 日的新功能

### 應用程式管理

- **利用 iOS「開啟位置」管理在協力廠商 MDM 解決方案中註冊的裝置**：您可以使用協力廠商行動裝置管理 (MDM) 廠商來利用 iOS「開啟位置」管理。 您可以在組態設定檔的設定中設定限制，並使用[管理 iOS 應用程式之間的資料傳輸](manage-data-transfer-between-ios-apps-with-microsoft-intune.md)來部署應用程式。

     這個方法有兩大優點︰

     1. 使用者需要以工作帳戶登入，才能從雲端服務或其他應用程式存取任何公司資料。 這可確保行動應用程式管理 (MAM) 原則在存取資料時生效。

     2. 透過協力廠商 MDM 解決方案部署之受管理的電子郵件設定檔和其他受管理的應用程式，可以與具有 Intune MAM 原則的應用程式共用檔案和資料。

- **使用非 Intune 註冊裝置的 MAM 原則來管理 Microsoft Outlook 應用程式**：您現在可以使用 Intune 行動應用程式管理原則，在非 Intune 註冊的裝置上管理 Microsoft Outlook 應用程式。 [iOS](https://itunes.apple.com/us/app/microsoft-outlook-email-calendar/id951937596?mt=8) 和 [Android](https://play.google.com/store/apps/details?id=com.microsoft.office.outlook) 裝置都有使用 MAM 功能更新的 Microsoft Outlook 應用程式。 使用[建立及部署行動應用程式管理原則](https://technet.microsoft.com/library/mt627829.aspx)主題中的指示建立 MAM 原則。  


- **行動應用程式設定原則讓您能靈活地指定 iOS 應用程式的使用者詳細資料**：您可以在 iOS 應用程式開啟時，提供它可能需要的使用者設定。 例如，您可以提供網路連接埠或使用者名稱。 如需詳細資訊，請參閱[在 Microsoft Intune 中使用行動應用程式設定原則設定 iOS 應用程式](configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune.md)。


- **將 Adobe Reader for Microsoft Intune 部署到企業中受 Intune 管理的 iOS 裝置**：使用 Intune 行動應用程式管理原則註冊的裝置現在可以管理 IOS 適用的 Adobe Reader 應用程式。

- **請務必在受管理的瀏覽器中開啟部署的網路美工圖案**：您可以部署只能使用 iOS 和 Android 裝置上受管理瀏覽器開啟的目標網路美工圖案。 例如，您透過公司入口網站部署公司資源連結，當使用者瀏覽這些連結時，他們會直接開啟受 MAM 原則保護的受管理瀏覽器。 如需詳細資訊，請參閱[部署應用程式](deploy-apps.md)。


- **從 Intune 系統管理員主控台尋找、管理及發佈 Windows 10 裝置適用的商務用 Windows 市集應用程式**：Intune 支援商務用 Windows 市集，幫助您尋找、管理及發佈應用程式到您管理的 Windows 10 裝置。 商務用 Windows 市集可讓您從 Intune 系統管理員主控台管理部署和監視這些應用程式的程序，這是您管理其他應用程式的同一個主控台。 具體來說，商務用 Windows 市集用來管理「線上授權應用程式」的內容和授權。 如需詳細資訊，請參閱[管理購自商務用 Windows 市集的應用程式](manage-apps-you-purchased-from-the-windows-store-for-business-with-microsoft-intune.md)。


### 裝置管理
- **iOS 裝置發佈 PFX 憑證**：Intune 系統管理員可以在 iOS 裝置上建立及部署 Wi-Fi、電子郵件和 VPN 驗證的 iOS PFX 憑證。 Android 和 Windows 10 裝置已提供這項功能。 如需詳細資訊，請參閱[利用憑證設定檔存取公司資源](secure-resource-access-with-certificate-profiles.md)。


- **根據使用者類別選項，將應用程式和原則套用至不同的裝置群組**：Intune 系統管理員現在可以定義自訂裝置的類別，供使用者在註冊期間選取。 例如，系統管理員可能希望使用者指定註冊的裝置是用於「收銀機」或「送貨卡車」或「庫房」。 選取的類別會讓裝置成為 Intune 裝置群組的成員，用於將不同的應用程式和原則部署至已註冊的裝置。 如需詳細資訊，請參閱[使用裝置群組對應分類裝置](categorize-devices-with-device-group-mapping-in-microsoft-intune.md)。

### Microsoft 公司入口網站的變更及更新
本版本中公司入口網站的變更如下：

**Android 公司入口網站應用程式**

* 當使用者啟動受行動應用程式管理 (MAM) 管理的應用程式時，就會看到應用程式受公司管理的通知訊息。 使用者現在可以點選 [深入了解] 連結取得何謂「受管理應用程式」的[詳細資訊](https://technet.microsoft.com/library/mt502762.aspx#BKMK_andr_use_mgd_apps)。 他們也可以點選 [不要再顯示這個訊息]，在啟動應用程式時不再顯示這個訊息。
* 已加入新畫面來引導使用者進行註冊程序，並提供使用者應該註冊的原因，以及 IT 系統管理員在其註冊裝置上可見與不可得見內容的詳細資訊。 如需詳細資訊，請參閱[註冊指示](https://technet.microsoft.com/library/mt502762.aspx#BKMK_andr_enroll_devc)。
* 註冊錯誤訊息現在會顯示在公司入口網站應用程式中。 過去，這些訊息是出現在公司入口網站中。 這項變更的意義是所有錯誤訊息現在都只出現在一個位置，而不是兩個不同的地方。


**iOS 公司入口網站應用程式**
* 當使用者啟動受行動應用程式管理 (MAM) 管理的應用程式時，就會看到應用程式受公司管理的通知訊息。 使用者現在可以點選 [深入了解] 連結取得何謂「受管理應用程式」的[詳細資訊](https://technet.microsoft.com/library/mt598622.aspx#BKMK_ios_use_mgd_apps)。 他們也可以點選 [不要再顯示這個訊息]，在啟動應用程式時不再顯示這個訊息。
* 已加入新畫面來引導使用者進行註冊程序，並提供使用者應該註冊的原因，以及 IT 系統管理員在其註冊裝置上可見與不可得見內容的詳細資訊。 如需詳細資訊，請參閱[註冊指示](https://technet.microsoft.com/library/mt598622.aspx#BKMK_enroll_ios_device)。
* 註冊錯誤訊息現在會顯示在公司入口網站應用程式中。 過去，這些訊息是出現在公司入口網站中。 這項變更的意義是所有錯誤訊息現在都只出現在一個位置，而不是兩個不同的地方。




## 2016 年 2 月
### Microsoft 公司入口網站的變更及更新

本版本中公司入口網站的變更如下：

#### Android 公司入口網站應用程式
- 已加入新畫面來引導使用者進行註冊程序，並提供使用者應該註冊的原因，以及 IT 系統管理員在其註冊裝置上可見與不可得見內容的詳細資訊。 如需詳細資訊，請參閱[註冊指示](https://technet.microsoft.com/library/mt502762.aspx#BKMK_andr_enroll_devc)。
- 註冊錯誤訊息現在會顯示在公司入口網站應用程式中。 過去，這些訊息是出現在公司入口網站中。 這項變更的意義是所有錯誤訊息現在都只出現在一個位置，而不是兩個不同的地方。

#### iOS 公司入口網站應用程式
 - 已加入新畫面來引導使用者進行註冊程序，並提供使用者應該註冊的原因，以及 IT 系統管理員在其註冊裝置上可見與不可得見內容的詳細資訊。 如需詳細資訊，請參閱[註冊指示](https://technet.microsoft.com/library/mt598622.aspx#BKMK_enroll_ios_device)。

 - 註冊錯誤訊息現在會顯示在公司入口網站應用程式中。 過去，這些訊息是出現在公司入口網站中。 這項變更的意義是所有錯誤訊息現在都只出現在一個位置，而不是兩個不同的地方。


## 2016 年 1 月

### 利用 Windows 10 功能
* **使用健康情況證明服務的條件式存取**：Intune 系統管理員現在可以在 Intune 管理主控台中檢視 Windows 10 裝置的健康情況證明。 系統管理員可透過裝置健全狀況證明，確認該用戶端電腦具有可信任的 BIOS、TPM 以及開機軟體設定。 若要支援裝置的健全狀況證明，用戶端裝置必須執行啟用了 TPM 2 的 Windows 10。 裝置健全狀況證明會顯示為下列各項啟用的裝置數目：
    * 早期啟動反惡意程式碼
    * BitLocker
    * 安全開機
    * 程式碼完整性

    如需裝置健全狀況設定、收集資料點及狀況證明報告的詳細資訊，請參閱 [Microsoft Intune 的裝置相容性原則簡介](introduction-to-device-compliance-policies-in-microsoft-intune.md)。 [HAS 服務詳細資料](https://msdn.microsoft.com/en-us/library/dn934876.aspx)詳細說明此項服務。

* **Windows 10 Passport for Work Policy 及憑證管理**：使用 Intune 可[與 Microsoft Passport for Work 整合](control-microsoft-passport-settings-on-devices-with-microsoft-intune.md)，這是使用 Active Directory 或 Azure Active Directory 帳戶取代密碼、智慧卡或虛擬智慧卡來登入 Windows 10 的替代方法。 Passport 可讓您以使用者筆勢登入，而不使用密碼登入。 使用者筆勢可能是簡單的 PIN、生物識別驗證 (例如 Windows Hello) 或外部裝置 (例如指紋辨識器)。

* **適用於特定應用程式的 VPN**：您可以選取透過 VPN 自動連接公司網路的應用程式。 設定 VPN 設定檔時，請依＜協助使用者搭配使用 VPN 設定檔與 Microsoft Intune 來連線到工作＞中所述，建立應用程式清單。

* **Windows 10 完整抹除支援**：您現在可以透過 Intune 管理主控台，遠端發出在 Intune 中註冊之 Windows 10 Desktop 裝置的完整抹除。 Windows 10 完整抹除會將裝置重設成出廠預設值。


### Apple 大量採購方案 (VPP) 更新
Intune 現在可以幫助您[管理透過 Apple 商務大量採購方案 (VPP) 購買的應用程式](manage-ios-apps-you-purchased-through-a-volume-purchase-program-with-microsoft-intune.md)。 這包括同步處理 Apple 與 Intune 之間的授權資訊，以及追蹤每個應用程式部署的複本數量。

### 使用 IMEI 編號識別公司擁有的裝置
您現在可以為具有 IMEI 編號的行動裝置平台[匯入國際行動設備識別碼 (IMEI) 編碼](specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers.md)，協助找出公司擁有的行動裝置。 只要在 Intune 註冊，已匯入 IMEI 編號的裝置就會標記為「公司」，以供套用不同於私有裝置套用原則的原則。

### 現在有更多的應用程式與 Intune MAM 原則相容
其他非 Microsoft 合作夥伴的應用程式現在已與 Intune 行動應用程式管理 (MAM) 原則相容 (受 Intune 管理的裝置)︰
* Box for EMM (Box Inc 出品) – 限 iOS
* Adobe Reader (Adobe 出品) – 限 Android
* Foxit PDF 閱讀程式 (Foxit Corporation 出品) – iOS 和 Android


### 一月終止 IE9 支援
從 2016 年 2 月開始，Internet Explorer 9 不再是用於存取 Microsoft Intune 公司入口網站、Intune 帳戶入口網站和 Intune 管理主控台的官方瀏覽器。 您必須移轉至 Internet Explorer 10 或更新版本。


>[!div class="step-by-step"]

>[&larr; **Intune 的新功能**](whats-new-in-microsoft-intune.md)    



<!--HONumber=Aug16_HO3-->



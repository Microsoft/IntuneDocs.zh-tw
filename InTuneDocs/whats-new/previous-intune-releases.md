---
title: "舊版 | Microsoft Intune"
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 10/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 45dad14a-d412-488d-bb1e-ad990ea503df
ROBOTS: noindex,nofollow
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 1360a23647d6e66ba682548ad2b158bb9047265d
ms.openlocfilehash: ec1b118b2c7681f351d83f469b8c32e95f8fa71f


---

# 舊版 Intune

## 2016 年 9 月
### 新功能、宣告和資訊
* [Windows 條件式存取](#windows-conditional-access)
* [iOS 10 支援](#ios-10-support)
* [App Wrapping Tool 支援 MAM，不需要 Android 和 iOS 裝置註冊](#app-wrapping-tool-supports-mam-without-device-enrollment-for-android-and-ios)
* [Intune 群組在 9 月會開始轉換到 Azure Active Directory](#intune-groups-begin-transitioning-to-azure-active-directory-in-september)
* [Lookout 整合以保護 Android 裝置](#lookout-integration-to-protect-android-devices)
* [適用於 Android、iOS 和 Windows 的公司入口網站更新](#company-portal-updates)
* [Intune 字彙](#intune-glossary)
* [未來動態](#whats-coming)

### Windows 條件式存取
您現在可以透過 Intune 管理主控台建立條件式存取原則，來封鎖 Windows 電腦存取 Exchange Online 和 SharePoint Online。 您也可以建立條件式存取原則來封鎖存取 Office 桌面及通用應用程式。

### iOS 10 支援
現有的 Intune MDM 與 MAM 案例與 iOS 10 相容。 如需秘訣，請參閱 [Intune 支援小組部落格](https://blogs.technet.microsoft.com/intunesupport/2016/09/13/support-tip-intune-support-for-ios-10/)。

### App Wrapping Tool 支援 MAM，不需要 Android 和 iOS 裝置註冊
Intune App Wrapping Tool 是命令列工具，用於在 iOS 和 Android 的企業營運 (LOB) 應用程式上啟用 Intune MAM。 它是將 Intune MAM SDK 併入到您 App 最簡單的方式，讓您的 App 可以強制執行透過 Intune 部署的 MAM 原則。 使用 MAM 原則，您可以：

1. 加密 App 的資料。
2. 要求資訊工作者啟動 App 時輸入 PIN。
3. 讓 App 只能傳送資料給其他受管理的 App。
4. 防止 App 將資料備份到 Android、iTunes 及 iCloud。
5. 僅允許對/從其他受管理的 App 執行剪下、複製和貼上。

更新的 Intune App Wrapping Tool 公開預覽版現在支援 MAM，而不需要在 iOS 和 Android 上的內部 LOB 應用程式裝置註冊。 這表示您的使用者不需要向 Intune 註冊其裝置，就能使用啟用 MAM 的 LOB 應用程式。

任何人都可以測試公開預覽版軟體，並閱讀相關實用文件。文件位於 msintuneappsdk 的 GitHub：

http://www.github.com/msintuneappsdk/intune-app-wrapper-ios-preview

http://www.github.com/msintuneappsdk/intune-app-wrapper-android-preview

在您安裝並使用適用於 Android 與 iOS 的 Microsoft Intune App Wrapping Tool 發行前版本之前，您必須：

* 檢閱適用於 Android 與 iOS 的 Microsoft Intune App Wrapping Tool 發行前版本的 Microsoft 授權條款
* 列印並保留一份授權條款供您備查。 下載及使用適用於 Android 的 Microsoft Intune App Wrapping Tool 發行前版本，即代表您同意這些授權條款。 若貴用戶不同意這些授權條款，請不要使用「軟體」。
<!---TFS 1235607--->

### Intune 群組在 9 月會開始轉換到 Azure Active Directory
部分新的 Intune 帳戶將會使用 Azure Active Directory 安全性群組，而不是 Intune 使用者群組。 因為 Intune 入口網站群組頁面將會有連結，將您導向至 Azure 管理入口網站，您會知道您正在使用安全性群組。

### Lookout 整合以保護 Android 裝置
Microsoft 正在整合 Lookout 的行動威脅保護解決方案，藉由偵測裝置上的惡意程式碼、高風險 App 等等，以保護 Android 行動裝置。 Lookout 的解決方案有助於您判斷威脅層級 (可設定)。 您可以根據 Lookout 的風險評估，在 Intune 中建立相容性原則規則，來決定裝置相容性。 您可以利用條件式存取原則，根據裝置相容性狀態，允許或封鎖公司資源的存取。

系統將會提示不相容裝置的使用者進行註冊，並且要求使用者在 Android 裝置上安裝 Lookout for Work 應用程式、啟動應用程式，並修復 Lookout for Work 應用程式中所報告的威脅，才能取得存取權。 若要深入了解，請參閱[根據裝置、網路和應用程式風險限制存取](restrict-access-based-on-device-network-app-risk.md)。


### 公司入口網站更新

### Android
**在適用於 Android 的公司入口網站新增「通知」**<br/>
適用於 Android 的公司入口網站的首頁新增了通知圖示。 點選此圖示可存取 [通知] 頁面，為您的終端使用者顯示公司入口網站應用程式中所有需要注意的項目，例如裝置不相容、註冊更新，以及註冊啟用。 iOS 公司入口網站應用程式已經有這項通知體驗。 有了新的 [通知] 頁面，只要該裝置已經註冊，使用者便不會在每次啟動或繼續使用公司入口網站時看見 [公司存取設定] 頁面。 如果您建立自己的終端使用者指南，建議您更新文件以反映這項變更。 [這裡](https://aka.ms/androidcpupdate)提供更新的螢幕擷取畫面。  
<!---TFS 1095560--->

**在適用於 Android 的公司入口網站提供意見反應**</br>
適用於 Android 的公司入口網站的功能表新增了新項目。 點選 [說明與意見反應] 會顯示三個動作︰
* 使用 [取得說明] 回報公司入口網站的問題給您的 IT 部門。 IT 會使用您的電子郵件用戶端建立電子郵件，並附加公司入口網站記錄。 [取得說明] 會取代 [設定] 頁面上的 [傳送資料] 功能。
* 使用 [提供意見反應] 來提供意見反應給公司入口網站小組。
* 使用 [為我們的應用程式評分]，在 Google Play 上為公司入口網站應用程式評分或評論。

### iOS
**變更 iOS 公司入口網站應用程式的支援**<br/>
iOS 版 Microsoft Intune 公司入口網站 App 的所有使用者，現在都必須使用最新版本。 新使用者可以只下載最新版本，而目前的使用者必須更新至最新版本。 最新版本需要 iOS 8.0 或更新版本，因此除非使用者將其裝置更新為 iOS 8.0 或更新版本，然後將公司入口網站 App 更新為最新版本，否則執行較舊 iOS 版本的裝置將無法使用公司入口網站或註冊。 執行 iOS 8.0 以下版本的已註冊裝置會繼續受到管理，並且列在 Intune 管理主控台中。
<!---TFS 1283165--->

**iOS 使用者取得應用程式方式的改進**<br/>
iOS 版公司入口網站 App 已經對應用程式磚進行下列變更，將使用者指向單一位置 (公司入口網站) 中不同檢視，以取得他們所有的 App。 Apple 限制禁止公司入口網站 App 列出企業營運及受管理市集應用程式，因此使用者必須瀏覽不同的檢視才能找到所有的 App。

- [公司應用程式] 磚先前會指向公司入口網站 [所有] 索引標籤中所有 App 的清單，而它會繼續以相同方式運作。 磚的名稱已變更為 [所有應用程式]。
- [其他應用程式] 磚先前會指向公司入口網站 App 中的檢視，其中會列出 Apple 允許在公司入口網站 App 中顯示的所有 App。 磚的名稱已變更為 [精選應用程式]，點選磚會將使用者移至公司入口網站的 [精選] 索引標籤。
-  [類別] 磚先前會指向公司入口網站 App 中列出 App 類別的檢視。 磚的名稱並未變更，但它現在指向公司入口網站的 [類別] 索引標籤。
您可以在[這裡](https://gallery.technet.microsoft.com/Improvements-in-how-iOS-d1104186)找到更新的螢幕擷取畫面。
<!---TFS 1317133--->

**提示安裝 iOS Managed Browser 應用程式 (若 IT 專業人員針對應用程式設定該需求)**<br/>
如果您已經設定僅能在受管理的瀏覽器中開啟 Web Clip，而裝置上並未安裝受管理的瀏覽器，裝置上的公司入口網站 App 將會提示使用者安裝受管理的瀏覽器，然後才能安裝網 Web Clip。
<!---TFS 1228570--->

### Windows
**Windows Phone 8.1 的公司入口網站應用程式新增了 [意見反應] 按鈕**<br/>
Windows Phone 8.1 公司入口網站應用程式讓終端使用者能夠使用新的 [傳送意見反應] 按鈕，傳送對應用程式的意見反應。 若要尋找按鈕，使用者要點選公司入口網站應用程式畫面右下角的「三個點」功能表，然後點選 **[傳送意見反應]**。 收集到的匿名意見反應可協助 Microsoft 改進使用者的公司入口網站應用程式體驗。
<!---TFS 1317806--->

### Intune 字彙</br>
我們已將新的[字彙主題](https://docs.microsoft.com/intune/understand-explore/intune-glossary)新增至文件庫，協助您了解 Intune 產品中所使用的一些術語。


## 2016 年 8 月
### 應用程式管理
<!---@Barry, I created the buckets of App management, Device management, etc but am not tied to them. Just wanted to break up and organize the feature list. If you're going to take over the Company Portal section, please talk to Stacie about how she's been organizing it. --->

__iOS 9.3 隱藏與顯示的應用程式__：針對執行 iOS 9.3 或更新版本的受監督裝置，您可以在 iOS 一般設定原則中使用隱藏與顯示的應用程式清單，以執行下列動作：
- 指定對使用者隱藏的應用程式清單。 使用者無法檢視或啟動這些應用程式。
- 指定使用者可檢視及啟動的應用程式清單。 無法檢視或啟動其他應用程式。

已部署的應用程式及內建 iOS 應用程式 (如「訊息」和「備忘錄」) 都是您可以指定的應用程式。 如需詳細資訊，請參閱 [Microsoft Intune 的 iOS 原則設定]( /intune/deploy-use/ios-policy-settings-in-microsoft-intune)
<!---TFS 1279009 checked--->
__Samsung KNOX 裝置允許與封鎖的應用程式原則__：您現在可以為 Samsung KNOX 裝置設定自訂原則，讓您可建立下列其中一個項目：
- 無法在裝置上執行的應用程式清單。 即使應用程式已安裝，在封鎖清單中定義後即無法在裝置啟動。
- 裝置使用者可從 Google Play 市集安裝的應用程式清單。 無法從市集安裝其他應用程式。

只有執行 Samsung KNOX 的裝置可使用這些設定。
如需詳細資訊，請參閱 [Use custom policies to allow and block apps for Samsung KNOX devices](/intune/deploy-use/custom-policy-to-allow-and-block-samsung-knox-apps) (使用自訂原則來允許及封鎖 Samsung KNOX 裝置的應用程式)。
<!---TFS 1311629 checked --->
__與行動應用程式管理 (MAM) 原則相容的新應用程式__：無論裝置是否已註冊，適用於 [iOS](https://itunes.apple.com/app/yammer/id289559439?mt=8) 與 [Android](https://play.google.com/store/apps/details?id=com.yammer.v1) 的 Yammer 應用程式現在會與 [Intune 行動應用程式管理 (MAM) 原則](/intune/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune)相容。

如需與 MAM 相容的應用程式完整清單，請參閱 [Microsoft Intune 應用程式合作夥伴](https://www.microsoft.com/en-us/cloud-platform/microsoft-intune-partners)網站。
<!--- TFS 1252335 & 1252336 checked--->

<!--- I started putting TFS numbers in the What's Coming topic and found it helpful when updating the What's New. Up to you if you want to continue. --->

__Intune Viewer 應用程式__：從 2016 年 8 月開始，在發佈新的 RMS 共用應用程式版本後，我們會移除下列 Intune Viewer 應用程式︰
- Intune AV Viewer
- Intune PDF Viewer
- 來自 Google Play 的 Intune Image Viewer for Android

我們建議使用新的 [Android 版授權管理應用程式 (RMS 共用)](/intune/deploy-use/end-user-experience-for-mam-enabled-apps-with-microsoft-intune#viewing-media-files-with-the-rights-management-sharing-app)，而不是使用 Intune Viewer 應用程式，它可讓您部署一個應用程式，而不必部署三個不同的應用程式，即可安全地在 Android 裝置上檢視公司檔案。 當 Intune Viewer 應用程式不再受到支援時，它將會從 Google 商店移除，且未來無法提供使用。

### 裝置管理
__Android 7.0 支援__：Intune 將為即將推出之行動裝置適用的 Android 7.0 作業系統提供「第 0 天」支援。
<!---TFS 1262053--->

__Google 移除 Android 7.0 裝置上的遠端密碼重設功能__：Google 將會移除 Android 7.0 裝置讓 IT 系統管理員與終端使用者在遠端重設密碼的功能。 先前，IT 管理員可以從遠端重設使用者的密碼，而終端使用者可從公司入口網站重新其密碼。

### 公司入口網站更新
__公司入口網站__
- **從公司入口網站傳送到 Microsoft 的意見反應連結** <br/>
公司入口網站可讓使用者在頁面底部點選新的 [意見反應] 連結，以將其網站體驗的相關意見反應傳送到 Microsoft。 收集到的匿名意見反應可協助 Microsoft 改進使用者的公司入口網站體驗。
<!--- TFS 1313657 checked--->

__iOS__
- **iOS Managed Browser 最低版本已更新為 8.0**<br/>
適用於 IOS 的 Microsoft Intune Managed Browser 應用程式已更新為支援執行 iOS 8.0 或更新版本的裝置。 雖然 iOS 7.1 裝置仍然可以使用現有的 Managed Browser 應用程式，請鼓勵您的使用者更新至 iOS 8.0 或更新版本，以存取並且充分利用新的 Managed Browser 功能。  
<!---TFS 1313253 checked--->

### 未來動態

__iOS 10 支援__：Intune 將完整支援 iOS 10。 詳細資訊將隨 iOS 10 公開發行而釋出。

__從 2016 年 9 月開始，Intune 群組將開始轉換到 Azure Active Directory 群組__：Intune 正在建立新的群組管理體驗，將在 Intune 中使用 Azure Active Directory (AAD) 安全性群組作為使用者和裝置群組。 這些群組將會**在我們推出以 Azure 為基礎的新 Intune 管理入口網站時**，用於所有群組管理、原則部署及設定檔部署上。

這個新體驗將會防止您在不同的服務上擁有重複的群組、**允許您存取一些新的 Azure Active Directory Premium (AADP) 群組功能**，以及透過 PowerShell 和 Graph 提供擴充性。 這也會統一不同企業行動管理上的群組管理體驗。

為了移動到安全性群組，**目前管理主控台**中的體驗將會進行一些修改。 **這些變更，以及 AAD 安全性群組的使用，將會被記錄在 Intune 文件中**。

Intune 的新客戶將會**比目前的租用戶更快看見某些安全性群組變更**。

除了群組管理中的變更之外，**下列功能將會被取代**：
- 於建立新群組時排除成員或群組
- 「已取消群組的使用者」和「已取消群組的裝置」群組
- 服務系統管理員角色中的「管理群組」
- 通知規則的自訂群組型警示
- 於報告中針對群組進行樞紐分析
<!--- TFS 1295329--->

**針對 Android 公司入口網站新增「通知」**：我們將在 9 月針對 Android 推出公司入口網站的更新，該更新將會在首頁上推出新的 [通知] 圖示。 點選此圖示將會存取「通知」頁面，並為您的終端使用者顯示公司入口網站應用程式中所有需要注意的項目，例如裝置不相容、註冊更新，以及註冊啟用。 如果您也使用 iOS 公司入口網站應用程式，您應該已能見到該通知體驗。 透過推出「通知」頁面，只要該裝置已經註冊，您便不會在每次啟動或繼續 Android 版的公司入口網站時看見「公司存取設定」頁面。 我們了解有許多使用者已建立終端使用者指南，並樂於在該指南/螢幕擷取畫面可能需要更新時提前收到通知。 請更新您的文件以反映即將推出的體驗變更。 尋找更新的螢幕擷取畫面，請移至：https://aka.ms/androidcpupdate。  

__iOS 使用者取得應用程式方式的改進__：下列對於 iOS 版「公司入口網站」應用程式中應用程式磚的變更將於 9 月進行，這會將使用者指向單一位置 (公司入口網站) 中的不同檢視，以取得他們所有的應用程式。 目前，Apple 限制禁止「公司入口網站」應用程式中列出企業營運應用程式及受管理的應用程式市集應用程式，並且要求使用者瀏覽不同的檢視才能找到所有的應用程式。

- [公司應用程式] 磚目前會指向公司入口網站 [所有] 索引標籤中所有應用程式的清單，而它會繼續以相同方式運作。 磚的名稱將會變更為 [所有應用程式]。
- [其他應用程式] 磚目前會指向「公司入口網站」應用程式中的檢視，其中會列出 Apple 允許在公司入口網站應用程式中顯示的所有應用程式。 磚的名稱將會變更為 [精選應用程式]，點選磚會將使用者移至公司入口網站的 [精選] 索引標籤。
-  [類別] 磚目前會指向公司入口網站應用程式中列出應用程式類別的檢視。 磚的名稱不會變更，但它現在會指向公司入口網站的 [類別] 索引標籤。 您可以在[這裡](https://gallery.technet.microsoft.com/Improvements-in-how-iOS-d1104186)找到更新的螢幕擷取畫面。
<!---TFS 1317133--->

### 雲端藍圖
請參閱 [Cloud Platform roadmap (雲端平台藍圖)](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)，隨時關注 Intune 的最新發展。

### 服務取代
<!---@Barry, we started listing service deprecations earlier this summer. --->
- **變更 iOS 公司入口網站應用程式的支援**<br/>
自 9 月起，iOS 版 Microsoft Intune 公司入口網站應用程式的所有使用者都必須使用最新版本。 新使用者只可以下載最新版本，目前使用者則需要它的更新。 最新版本需要 iOS 8.0 或更新版本，因此除非他們將其裝置更新為 iOS 8.0 或更新版本，然後將公司入口網站應用程式更新為最新版本，否則執行較舊 iOS 版本的裝置會無法使用公司入口網站或註冊。 執行 iOS 8.0 以下版本的已註冊裝置會繼續受到管理，並且列在 Intune 管理主控台中。  

- **iOS Managed Browser 最低版本已更新為 8.0**<br/>
Intune 將於八月發行的 iOS 版 Microsoft Intune Managed Browser 應用程式更新，將僅支援執行 iOS 8.0 或更新版本的裝置。 雖然 iOS 7.1 裝置仍然可以使用現有的 Managed Browser 應用程式，請建議您的使用者更新至 iOS 8.0 或更新版本，以存取並且充分利用新的 Managed Browser 功能。  
<!---TFS 1313253--->

- **將取代 Windows 8 版和 Windows Phone 8 版公司入口網站應用程式** <br/>
自 2016 年 10 月起，Microsoft Intune 將會取代 Windows 8 和 Windows Phone 8 公司入口網站應用程式的支援。 Microsoft Intune 也會取代 Windows Phone 8 平台的支援。 因此，您將無法註冊或更新任何 Windows Phone 8 裝置。 您可以繼續管理已註冊的 Windows Phone 8 和 Windows 8 裝置。 將 Windows Phone 8 和 Windows 8 裝置更新為 Windows 8.1 和 Windows Phone 8.1，並使用對應的 Windows 8.1 和 Windows Phone 8.1 公司入口網站應用程式繼續將應用程式發佈至這些裝置，而不受中斷。
<!---TFS 1255391--->

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

## 2016 年 7 月
### 應用程式管理

__改善應用程式佈建設定檔更新體驗__：Apple iOS 企業營運行動應用程式已內建佈建設定檔，以及透過憑證簽署的程式碼。 當該應用程式於 iOS 裝置上執行時，iOS 會確認該 iOS 應用程式的完整性，並強制執行由佈建設定檔定義的原則。

您用來簽署應用程式的企業簽署憑證通常會持續 3 年。 不過佈建設定檔將會在 1 年後到期。 透過此更新，Intune 會提的工具，可讓您在裝置上有即將到期的應用程式，但憑證仍然有效的情況下，主動將新的佈建設定檔原則部署到裝置。 如需詳細資訊，請參閱[使用 iOS 行動佈建設定檔原則來保持最新的企業營運應用程式](/intune/deploy-use/ios-mobile-app-provisioning-profiles)。
<!--- TFS 1280247--->

__Intune 應用程式的 Xamarin SDK 可供使用__：Intune 應用程式 SDK Xamarin 元件可允許您在使用 Xamarin 建置的行動裝置 iOS 和 Android 應用程式中啟用 Intune 行動裝置應用程式管理功能。 您可以在 [Xamarin 市集](https://components.xamarin.com/view/Microsoft.Intune.MAM)中或 [Microsoft Intune Github 頁面](https://github.com/msintuneappsdk)上找到元件。
<!--- TFS 1061478 --->

### 裝置管理
__提升裝置註冊限制__：Intune 已將每位使用者可設定裝置註冊最大值的限制，從 5 部裝置提升到 15 部裝置。
<!---TFS 1289896 --->

__在執行 Intune 用戶端軟體之 Windows 電腦的 TeamViewer 整合__
：對於執行 Intune 用戶端的 Windows 電腦，[TeamViewer](https://www.teamviewer.com) 整合可讓您建立與 Windows 電腦的遠端協助工作階段，以協助支援終端使用者支援人員部門。 這包括 Windows 7、8、8.1 和 Windows 10。 如需詳細資訊，請參閱[使用 Microsoft Intune 電腦用戶端的一般 Windows 電腦管理工作](/intune/deploy-use/common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client)。
<!---TFS 1284856--->

### 公司入口網站更新

__公司入口網站__
- **改善註冊 Windows 裝置時的使用者經驗**<br/>
當您使用條件式存取時，在公司入口網站中已釐清 Windows 8.1、Windows 10 Desktop 和 Windows 10 行動裝置版的註冊步驟。 使用者現在會看到個別的「裝置註冊」和「工作場所聯結」步驟，讓使用者能夠更容易看到他們的裝置狀態，並在遇到工作場所聯結 (WPJ) 失敗時完成程序。 個別的步驟應該也能為 IT 系統管理員簡化疑難排解程序。 以前，當終端使用者嘗試註冊且除了 WPJ 以外的註冊步驟都成功時，已註冊的裝置不會顯示在可讓使用者識別的裝置清單中，而造成使用者混淆。

__Android__
- **Android 公司入口網站應用程式**<br/>
如果 Android 終端使用者看到錯誤訊息，指出他們的裝置遺漏必要的憑證，他們可以點選 [如何解決此問題] 按鈕，以取得安裝遺失憑證的[步驟](/intune/enduser/your-device-is-missing-a-required-certificate-android#your-device-is-missing-a-certificate-required-by-your-it-administrator)。 如果使用者完成這些步驟，但看見其他其他「遺漏憑證」錯誤訊息，則會要求他們連絡其 IT 系統管理員並提供此[連結](/intune/troubleshoot/troubleshoot-device-enrollment-in-intune#android-certificate-issues)，其中包含 IT 系統管理員可用來解決憑證問題的步驟。

- **將側載應用程式安裝限制於已註冊的裝置**<br/>
Android 裝置已無法透過公司入口網站安裝應用程式，除非該裝置已使用 Android 版 Intune 公司入口網站應用程式在 Intune 註冊。
<!---TFS 1299082--->

__iOS__
- **iOS 公司入口網站應用程式中的裝置註冊管理員帳戶變更**<br/>
為了提升效能及規模，Intune 已不再於 iOS 公司入口網站應用程式的 [我的裝置] 窗格中，顯示所有的裝置註冊管理員 (DEM) 裝置。 只有執行應用程式的本機裝置會顯示，只有在透過公司入口網站應用程式註冊時才會顯示。

DEM 使用者可在本機裝置上執行動作，但是其他已註冊裝置的遠端管理只能從 Intune 管理主控台執行。 此外，Intune 將會使用 DEM 帳戶取代 Apple 裝置註冊方案或 Apple Configurator 工具。 這兩種註冊方法已經支援共用之 iOS 裝置的較少使用者註冊。

只有在共用裝置的較少使用者註冊無法使用時，才能使用 DEM 帳戶。 如需詳細資訊，請參閱[使用 Microsoft Intune 中的裝置註冊管理員註冊公司所擁有的裝置](https://docs.microsoft.com/en-us/intune/deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune)。
<!---TFS 1233681--->

### Windows 功能名稱的變更
- [Microsoft Passport for Windows](/intune/deploy-use/control-microsoft-passport-settings-on-devices-with-microsoft-intune) 現在稱為 **Windows Hello 企業版**。
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
- **瀏覽器的條件存取** 您可以設定 [Exchange Online](/intune/deploy-use/restrict-access-to-exchange-online-with-microsoft-intune) 和 [SharePoint Online](/intune/deploy-use/restrict-access-to-sharepoint-online-with-microsoft-intune) 的條件式存取原則，以便只能從受管理和相容的 iOS 和 Android 裝置上的支援瀏覽器存取它們。 嘗試使用 iOS 和 Android 裝置登入 Outlook Web Access (OWA) 和 SharePoint 網站的使用者將會收到提示，以其裝置向 Intune 註冊，以及在完成登入之前修正任何不相容問題。
<!---TFS 1175844--->

- **Dynamics CRM Online 支援條件式存取。** 您可以設定 [Dynamics CRM Online](/intune/deploy-use/restrict-access-to-dynamics-crm-online-with-microsoft-intune) 的條件式存取原則，以便只有受管理和相容的 iOS 和 Android 裝置可以存取它。 嘗試在 iOS 和 Android 上登入 Dynamics CRM 行動應用程式的使用者將會收到提示，在登入完成之前向 Intune 註冊並補救任何不相容問題。
<!---TFS1295358--->

### Intune 公司入口網站更新

__Android 公司入口網站應用程式__

- 當 IT 系統管理員套用新的「裝置必須防止從不明來源安裝應用程式 (Android 4.0+)」原則時，使用 Android 4.0 或更新版本之裝置的使用者會看到訊息：「必須停用來自未知來源的安裝」。 使用者必須移至 [設定]  >  [安全性]，並關閉 [未知來源]。 相容性訊息中的連結可讓使用者取得訊息的[相關資訊](/Intune/EndUser/you-are-asked-to-turn-off-unknown-sources-android)，以及為什麼他們需要關閉設定。

- 當 IT 系統管理員套用新的「裝置必須已啟用掃描應用程式的安全性威脅 (Android 4.0+)」原則時，使用 Android 4.0 或更新版本之裝置的使用者將會看到訊息：「掃描裝置中的安全性威脅」。 使用者必須移至 [設定]  >  [Google]  >  [安全性]，然後開啟 [掃描裝置中的安全性威脅]。 相容性訊息中的連結可讓使用者取得訊息的[相關資訊](/Intune/EndUser/you-are-asked-to-turn-on-scan-device-for-security-threats-android)，以及為什麼他們需要開啟設定。

- 當 IT 系統管理員套用新的「USB 偵錯需為停用 (Android 4.2+)」原則時，使用 Android 4.2 或更新版本之裝置的使用者將會看到訊息：「必須停用 USB 偵錯」。 使用者必須移至 [設定]  >  [開發人員選項]，並關閉 [USB 偵錯]。 相容性訊息中的連結可讓使用者取得訊息的[相關資訊](/Intune/EndUser/you-are-asked-to-turn-off-usb-debugging-android)，以及為什麼他們需要關閉設定。

- 當 IT 系統管理員套用新的「Android 安全性修補程式等級下限 (Android 6.0+)」原則時，使用 Android 6.0 或更新版本之裝置的使用者將會看到訊息：「此裝置不符合最低的 Android 安全性修補程式等級」。 使用者必須安裝所需的安全性修補程式。 相容性訊息中的連結可讓使用者取得如何安裝必要安全性修補程式以及查看目前已安裝之安全性修補程式的[相關資訊](/Intune/EndUser/you-are-asked-to-turn-on-scan-device-for-security-threats-android)。

__iOS 公司入口網站應用程式__

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
- **MAM SDK︰支援 PIN 長度組態。** 您可以將 MAM 應用程式的 PIN 長度指定為類似裝置 PIN 的長度。 這將需要使用者符合您設定的新限制。 他們會看到稍微修改的 PIN 畫面以說明較長的輸入。 如需詳細資訊，請參閱 [MAM policy settings for Android](/intune/deploy-use/android-mam-policy-settings) (適用於 Android 的 MAM 原則設定) 和 [MAM policy settings for iOS](/intune/deploy-use/ios-mam-policy-settings) (適用於 iOS 的 MAM 原則設定)。

- **iOS 和 Android 的商務用 Skype。** 您現在可以將目標放在具備[無註冊原則之 MAM](/intune/deploy-use/get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune) 的商務用 Skype。 一旦使用者登入，將會套用 MAM 原則。

- **新的應用程式可用來使用 MAM 原則進行管理。** 適用於 Android 的 Microsoft Word、Excel 和 PowerPoint 應用程式現在可以在未向 Intune 註冊的裝置上與 MAM 原則相關聯。 如需受支援應用程式的完整清單，請移至 Microsoft Intune 應用程式夥伴頁面上的 [Microsoft Intune 行動應用程式庫](https://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/partners.aspx)。


### 公司入口網站更新

#### Android 公司入口網站應用程式
- **使用者快顯通知**：使用者註冊其裝置或從公司入口網站移除他們的裝置時，將會看到來自 Android 公司入口網站應用程式的快顯通知。

- **Android 公司入口網站應用程式中的裝置註冊管理員帳戶的變更。** 為了改善效能和擴充，Intune 將不再於 Android 公司入口網站的 [我的裝置] 窗格中，顯示所有的裝置註冊管理員 (DEM) 裝置。 只有執行應用程式的本機裝置會顯示，只有在透過公司入口網站應用程式註冊時才會顯示。 DEM 使用者可在本機裝置上執行動作，但是其他已註冊裝置的遠端管理只能從 Intune 管理主控台執行。

#### 公司入口網站
- **公司入口網站：裝置識別橫幅將提供詳細資訊給使用者。** 使用者可以更輕鬆地識別他們在使用公司入口網站時所選取的裝置。 如果選取了錯誤的裝置，他們可以藉由點選首頁橫幅中的 [點選這裡] 連結來選取正確的裝置。

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
您現在可以檢視 Azure Active Directory (AAD) 租用戶中任一使用者的應用程式管理原則[狀態](/intune/deploy-use/monitor-mobile-app-management-policies-with-Microsoft-Intune)。 這包括：
   - 裝置
   - 裝置上的應用程式

   狀態值：

   **已存回**︰表示原則已部署至使用者，且已使用工作內容中的應用程式，並成功接收原則。

    **未存回**︰表示原則已部署至使用者，但是應用程式從那時起並未在工作內容中使用。


- **避免 Outlook 連絡人同步處理 (Android) 的 MAM 控制項。**
新的設定可供[行動應用程式管理](/intune/deploy-use/create-and-deploy-mobile-app-management-policies-with-microsoft-intune)使用，而不需要裝置註冊。 此設定可讓您防止應用程式在 Android 裝置上將連絡人同步處理至原生通訊錄。 啟用此設定時，目標應用程式將不再能夠儲存連絡人到原生通訊錄。 停用此設定時，目標應用程式將能夠儲存連絡人到原生通訊錄。 當您[從遠端抹除裝置或應用程式](/intune/deploy-use/wipe-managed-company-app-data-with-Microsoft-Intune)時，將會移除所有已儲存至原生通訊錄的連絡人。 在 Android 裝置上的 Outlook 應用程式一開始支援這個新的設定。

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

>[!div class="step-by-step"]

>[&larr; **Intune 的新功能**](whats-new-in-microsoft-intune.md)    



<!--HONumber=Oct16_HO3-->



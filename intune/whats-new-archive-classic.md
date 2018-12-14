---
title: Microsoft Intune 傳統入口網站封存的新功能
description: 封存 Microsoft Intune 新功能公告
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 06/08/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ed2db991-4729-49a7-a1e6-be2ffa0d03d1
ROBOTS: noindex,nofollow
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.openlocfilehash: 56d5d9c773a11b3884b4e72b55fab27e7044f1e9
ms.sourcegitcommit: 5058dbfb0e224207dd4e7ca49712c6ad3434c83c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/08/2018
ms.locfileid: "53112896"
---
# <a name="whats-new-in-the-intune-classic-portal---previous-months"></a>Intune 傳統入口網站的新功能 - 前幾個月

[!INCLUDE [classic-portal](./includes/classic-portal.md)]

此頁面列出先前公告於 Intune 傳統入口網站[新功能頁面](whats-new.md)上的新功能和注意事項。

## <a name="april-2017"></a>2017 年 4 月

### <a name="new-capabilities"></a>新功能

#### <a name="myapps-available-for-managed-browser---822308-822303--"></a>MyApps 可供 Managed Browser 使用 <!--822308, 822303-->

Microsoft MyApps 現在於 Managed Browser 中提供更佳支援。 非管理目標的 Managed Browser 使用者將會直接進入 MyApps 服務，以在其中存取其系統管理員佈建的 SaaS 應用程式。 Intune 管理目標的使用者將能夠繼續從內建 Managed Browser 書籤存取 MyApps。

#### <a name="new-icons-for-the-managed-browser-and-the-company-portal---918433-918431-971473--"></a>Managed Browser 和公司入口網站的新圖示 <!--918433, 918431, 971473-->

Managed Browser 會同時收到 Android 和 iOS 版應用程式的更新圖示。 此新圖示會包含更新的 Intune 徽章，因此與 Enterprise Mobility + Security (EM+S) 中的其他應用程式更一致。 您可以在 [Intune App UI 中的新增功能頁面](whats-new-app-ui.md)中看到 Managed Browser 的新圖示。

公司入口網站也會收到 Android、iOS 和 Windows 版應用程式的更新圖示，以增強與 EM+S 中其他應用程式的一致性。 從四月起到五月底，這些圖示會逐漸在各平台發行。

#### <a name="sign-in-progress-indicator-in-android-company-portal---953374--"></a>Android 公司入口網站中的登入進度列指示器 <!--953374-->

Android 公司入口網站應用程式的更新會在使用者啟動或繼續執行應用程式時，顯示登入進度指示器。 該指示器會顯示新的狀態進度，一開始為「正在連線...」，接著依序為「正在登入...」和「正在檢查安全性需求...」，之後才允許使用者存取應用程式。 您可以在 [Intune 應用程式 UI 中的新增功能頁面](whats-new-app-ui.md)中看到 Android 版公司入口網站應用程式的新畫面。

#### <a name="block-apps-from-accessing-sharepoint-online----679339---"></a>禁止應用程式存取 SharePoint Online <!-- 679339 -->

您現在可以建立以應用程式為基礎的條件式存取原則，來禁止沒有套用應用程式保護原則的應用程式存取 [SharePoint Online](app-based-conditional-access-intune-create.md)。 在以應用程式為基礎的條件式存取案例中，您可以使用 Azure 入口網站指定能存取 SharePoint Online 的應用程式。

#### <a name="single-sign-on-support-from-the-company-portal-for-ios-to-outlook-for-ios---834012--"></a>從 iOS 版入口網站到 iOS 版 Outlook 的單一登入 <!--834012-->
如果使用者在同一部裝置上使用相同的帳戶登入 iOS 公司入口網站應用程式，則不必再登入 Outlook 應用程式。 當使用者啟動 Outlook 應用程式時，將能夠選取其帳戶並自動登入。 我們也將努力為其他 Microsoft 應用程式新增這項功能。

#### <a name="improved-status-messaging-in-the-company-portal-app-for-ios---744866--"></a>改進 iOS 公司入口網站應用程式中的狀態訊息 <!--744866-->
iOS 公司入口網站應用程式中現在會顯示更具體的新錯誤訊息，以提供有關裝置狀況之更容易存取的資訊。 這些錯誤狀況之前包含在標題為「公司入口網站暫時無法使用」的一般錯誤訊息中。 此外，如果使用者在沒有網際網路連線時啟動 iOS 上的公司入口網站，則會在首頁上看到持續性狀態列，指出「沒有網際網路連線」。

#### <a name="improved-app-install-status-for-the-windows-10-company-portal-app---676495--"></a>改進 Windows 10 公司入口網站應用程式的應用程式安裝狀態 <!--676495-->

在 Windows 10 公司入口網站應用程式中啟動的應用程式安裝，有下列新的改進項目：
-   更快速地報告 MSI 套件的安裝進度
-   針對在執行 Windows 10 年度更新版及更新版本裝置上的新式應用程式，可以更快速地報告安裝進度
-   針對在執行 Windows 10 年度更新版及更新版本裝置上的新式應用程式安裝，有新的進度列

您可以在 [Intune 應用程式 UI 的新增功能頁面](whats-new-app-ui.md)中看到新的進度列。

#### <a name="bulk-enroll-windows-10-devices----747607---"></a>大量註冊 Windows 10 裝置 <!-- 747607 -->

您現在可以使用 Windows 設定設計工具 (WCD) 將執行 Windows 10 Creators Update 的大量裝置加入到 Azure Active Directory 和 Intune。 若要為您的 Azure AD 租用戶啟用[大量 MDM 註冊](windows-bulk-enroll.md)，請使用 Windows 設定設計工具建立會將裝置加入到 Azure AD 租用戶的佈建套件，然後將套件套用至您要大量註冊及管理的公司擁有裝置。 將套件套用至裝置之後，裝置會加入 Azure AD、在 Intune 中註冊，並準備好供 Azure AD 使用者登入。  Azure AD 使用者是這些裝置上的標準使用者，並且會接收指派的原則和必要應用程式。 目前不支援自助式和公司入口網站案例。

### <a name="whats-new-in-the-public-preview-of-intune-in-the-azure-portal--736542--"></a>Azure 入口網站中 Intune 公開預覽的新功能<!--736542-->

在 2017 年初，我們會將完整系統管理體驗移轉到 Azure，以便在可透過圖形 API 擴充的新式服務平台上，對核心 EMS 工作流程進行強大的整合式管理。

新的試用租用戶將於本月開始看到 Azure 入口網站中新系統管理體驗的公開預覽。 在預覽狀態期間，將提供與現有 Intune 主控台相同與相當的功能。

Azure 入口網站中的系統管理體驗將使用已宣佈的新分組和目標設定功能；當您現有的租用戶移轉至新的分組體驗時，也會同時將您移轉，以預覽您租用戶的新系統管理體驗。 同時，如果您想要在移轉租用戶之前測試或查看任何新功能，請註冊新的 Intune 試用帳戶或查看[新文件](whats-new.md)。

您可以在[這裡](whats-new.md)找到 Azure 的 Intune 預覽新功能。

### <a name="notices"></a>通知

#### <a name="direct-access-to-apple-enrollment-scenarios---951869--"></a>直接存取 Apple 註冊案例 <!--951869-->

對於在 2017 年 1 月之後建立的 Intune 帳戶，Intune 已經啟用使用 Azure Preview 入口網站中的「註冊裝置」工作負載直接存取 Apple 註冊案例。 Apple 註冊預覽原本只能從 Azure 入口網站中的連結存取。 在 2017 年 1 月之前建立的 Intune 帳戶，將需要進行一次性移轉，才能在 Azure 中使用這些功能。 移轉的排程尚未宣布，但將會盡快提供詳細資料。 如果您現有的帳戶無法存取預覽，我們強烈建議您建立試用帳戶來測試新的體驗。

#### <a name="whats-coming-for-appx-in-intune-in-the-azure-portal----1000270---"></a>Azure 入口網站中 Intune 的 Appx 未來動態 <!-- 1000270 -->

在移轉到 Azure 入口網站中 Intune 的過程中，我們將進行三個 appx 變更：

1. 在 Intune 主控台中，新增只能部署到 MDM 註冊裝置的新 appx 應用程式類型。
2. 重新規劃現有的 appx 應用程式類型，將目標僅限於透過 Intune PC 代理程式管理的電腦。
3. 透過移轉，將所有現有的 appxs 轉換成 MDM appxs。

##### <a name="how-does-this-affect-me"></a>此變更對我造成什麼影響？

這不會影響透過 Intune PC 代理程式管理之裝置上的任何現有部署。 不過移轉之後，您無法將這些移轉的 appxs 部署到透過 Intune PC 代理程式管理但先前未設為目標的任何新裝置。

##### <a name="what-action-do-i-need-to-take"></a>我需要採取什麼動作

移轉之後，如果您想要執行新的 PC 部署，您將必須再次重新上傳 appx 作為 PC 的 appx。 若要深入了解，請參閱 Intune 支援小組部落格上的 [Azure 入口網站中 Intune 的 Appx 變更](https://aka.ms/appxchange) \(英文\)。  

#### <a name="administration-roles-being-replaced-in-azure-portal"></a>Azure 入口網站中將被取代的系統管理角色

在 Intune Azure 入口網站中，將用一組全新且完整的角色型系統管理控制 (RBAC)，取代 Intune 傳統入口網站 (Silverlight) 中使用的現有行動應用程式管理 (MAM) 系統管理角色 (參與者、擁有者和唯讀)。 當您移轉至 Azure 入口網站之後，您必須將系統管理員重新指派至這些新的系統管理角色。 如需 RBAC 和新角色的詳細資訊，請參閱 [Microsoft Intune 的角色型存取控制](role-based-access-control.md)。

### <a name="whats-coming"></a>未來動態

#### <a name="improved-sign-in-experience-across-company-portal-apps-for-all-platforms---user-story-1132123--"></a>改善適用於所有平台的公司入口網站應用程式登入體驗 <!--User Story 1132123-->

我們宣布將在幾個月內推出變更，以改進 Android、iOS 和 Windows 版 Intune 公司入口網站應用程式的登入體驗。 當 Azure AD 進行此變更時，新的使用者體驗會自動顯示在所有平台的公司入口網站應用程式上。 此外，使用者現在可以使用產生的一次性驗證碼，從另一部裝置登入公司入口網站。 在使用者需要不使用認證登入的情況下，這特別有用。

您可在[應用程式 UI 的新功能](whats-new-app-ui.md)頁面上找到舊版登入體驗、使用認證的新登入體驗，以及從另一部裝置登入的新登入體驗的螢幕擷取畫面。

#### <a name="plan-for-change-intune-is-changing-the-intune-partner-portal-experience----1050016---"></a>規劃變更：Intune 正在變更 Intune 合作夥伴入口網站體驗 <!-- 1050016 -->

我們會在 2017 年 5 月中旬的服務更新將 Intune 合作夥伴頁面從 manage.microsoft.com 移除。  

如果您是合作夥伴系統管理員，將無法再從 Intune 合作夥伴頁面代表客戶檢視或採取動作，但會需要登入在 Microsoft 的另外兩個合作夥伴入口網站的其中一個。

[Microsoft 合作夥伴中心](https://partnercenter.microsoft.com/)和 [Microsoft Office 365 合作夥伴系統管理中心](https://portal.office.com/)都能讓您登入所管理客戶的帳戶。 合作夥伴在此後請使用這兩個網站來管理客戶。


#### <a name="apple-to-require-updates-for-application-transport-security---748318--"></a>Apple 要求必須更新 Application Transport Security <!--748318-->

Apple 宣布將會強制執行 Application Transport Security (ATS) 的特定需求。 ATS 可用來對透過 HTTPS 進行的所有應用程式通訊，強制執行更嚴格的安全性。 此變更會影響使用 iOS 公司入口網站應用程式的 Intune 客戶。

我們已透過 Apple TestFlight 方案，提供符合新 ATS 需求的 iOS 版公司入口網站應用程式。 如果您想試用該版本以便測試 ATS 合規性，請傳送電子郵件到 <a href="mailto:CompanyPortalBeta@microsoft.com?subject=Register to TestFlight ATS Company Portal app">CompanyPortalBeta@microsoft.com</a>，並附上您的姓氏、名字、電子郵件地址和公司名稱。 如需詳細資訊，請檢閱我們的 [Intune 支援部落格](https://aka.ms/compportalats)。

## <a name="march-2017"></a>2017 年 3 月

### <a name="new-capabilities"></a>新功能

#### <a name="support-for-skycure"></a>支援 Skycure

您現在可以根據由 Skycure (一個與 Microsoft Intune 整合的行動威脅防禦解決方案) 所進行的風險評估，使用條件式存取來控制行動裝置對公司資源的存取。 風險評估是根據收集自執行 Skycure 裝置的遙測，包括︰

- 實體防禦
- 網路防禦
- 應用程式防禦
- 弱點防禦

您可以設定透過 Intune 裝置合規性政策所啟用之以 Symantec Endpoint Protection Mobile (Skycure) 風險評估的 EMS 條件式存取原則。 您可以根據偵測到的威脅，使用這些原則來允許或封鎖不相容的裝置存取公司資源。 如需詳細資訊，請參閱 [Symantec Endpoint Protection Mobile 連接器](skycure-mobile-threat-defense-connector.md)。

#### <a name="new-user-experience-for-the-company-portal-app-for-android---621622--"></a>Android 版公司入口網站應用程式的新使用者體驗 <!--621622-->

Android 版公司入口網站應用程式將會更新其使用者介面，以提供更現代化的外觀和操作，以及更佳的使用者體驗。 值得注意的更新如下︰

- 色彩：公司入口網站索引標籤標頭會以 IT 定義的品牌上色。
- 應用程式：在 [應用程式] 索引標籤中，已更新 [精選應用程式] 和 [所有應用程式] 按鈕。
- Search：在 [應用程式] 索引標籤中，[搜尋] 按鈕是浮動的動作按鈕。
- 瀏覽應用程式：[所有應用程式] 檢視會以索引標籤式的檢視顯示 [精選]、[所有] 與 [類別]，以更方便瀏覽。
- 支援：已更新 [我的裝置] 和 [連絡 IT] 索引標籤以提高可讀性。

如需有關這些變更的詳細資訊，請參閱 [Intune 使用者應用程式的 UI 更新](whats-new-app-ui.md)。

#### <a name="non-managed-devices-can-access-assigned-apps---664691--"></a>未受管理的裝置可以存取已指派的應用程式 <!--664691-->

iOS 和 Android 使用者能夠在他們未受管理的裝置上，安裝指派給他們的「無須註冊即可使用」應用程式，這屬於公司入口網站的設計變更。 使用 Intune 認證，使用者能夠登入公司入口網站，並查看指派給他們的應用程式清單。 「無須註冊即可使用」應用程式的應用程式套件，可透過公司入口網站下載取得。 這項變更不會影響需要註冊才能安裝的應用程式，因為如果使用者想要安裝這些應用程式，系統會提示他們註冊裝置。

#### <a name="signing-script-for-windows-10-company-portal---941642--"></a>Windows 10 公司入口網站的簽署指令碼 <!--941642-->

如果您需要下載和側載「Windows 10 公司入口網站」應用程式，您現在可以使用指令碼為您的組織簡化及加速應用程式簽署程序。   若需要下載指令碼及其使用指示，請參閱 TechNet 資源庫上 [Windows 10 公司入口網站專用的 Microsoft Intune 簽署指令碼](https://aka.ms/win10cpscript)。 如需本公告的詳細資訊，請參閱 Intune 支援小組部落格上的[更新您的 Windows 10 公司入口網站應用程式](https://blogs.technet.microsoft.com/intunesupport/2017/03/13/updating-your-windows-10-company-portal-app/)。


### <a name="notices"></a>通知

#### <a name="support-for-ios-103"></a>支援 iOS 10.3

iOS 10.3 版在 2017 年 3 月 27 日開始向 iOS 使用者推出。 所有現有的 Intune MDM 與 MAM 案例都與最新版本的 Apple OS 相容。 當使用者將裝置和應用程式升級到 iOS 10.3 時，我們預期所有目前可用來管理 iOS 裝置的 Intune 功能將可繼續運作。

目前沒有任何已知問題可分享。 如果您在使用 iOS 10.3 時發生任何問題，歡迎連絡 [Intune 支援小組](get-support.md)。

#### <a name="improved-support-for-android-users-based-in-china---720444--"></a>改善對於中國 Android 使用者的支援 <!--720444-->

由於中國沒有 Google Play 商店，因此 Android 裝置必須從中文市集取得應用程式。 公司入口網站將支援此工作流程，方法是將中國的 Android 使用者重新導向，以便從當地的應用程式市集下載公司入口網站及 Outlook 應用程式。 這將會在啟用條件式存取原則時，改善對於行動裝置管理及行動應用程式管理的使用者體驗。 Android 版公司入口網站和 Outlook 應用程式可在下列中文應用程式市集取得：

- [百度](https://go.microsoft.com/fwlink/?linkid=836946)
- [小米應用商店](https://go.microsoft.com/fwlink/?linkid=836947)
- [騰訊](https://go.microsoft.com/fwlink/?linkid=836949)
- [華為](https://go.microsoft.com/fwlink/?linkid=836948)
- [豌豆莢](https://go.microsoft.com/fwlink/?linkid=836950)

#### <a name="best-practice-make-sure-your-company-portal-apps-are-up-to-date---879465--"></a>最佳作法︰請確定您的公司入口網站應用程式是最新版本 <!--879465-->

我們於 2016 年 12 月發行的更新，會針對成群使用者註冊 iOS、Android、Windows 8.1+ 或 Windows Phone 8.1+ 裝置時，強制使用 Multi-Factor Authentication (MFA)。 若公司入口網站應用程式低於特定基準版本 (Android 為 v5.0.3419.0+，iOS 為 v2.1.17+)，這個功能便無法運作。

Microsoft 不斷致力改善 Intune，在主控台及所有支援平台的公司入口網站應用程式中加入新功能。 有鑑於此，Microsoft 僅會針對在最新公司入口網站應用程式之中所發現問題來發行修正。 因此，我們建議您使用最新版的公司入口網站應用程式，才能為您帶來最佳的使用者體驗。

>[!Tip]
> 請您的使用者將其裝置設定為自動從適當的應用程式商店更新應用程式。 如果您已在網路共用上提供 Android 公司入口網站應用程式，您可以從 [Microsoft 下載中心](https://www.microsoft.com/download/details.aspx?id=49140)下載最新版本。

#### <a name="microsoft-teams-is-now-enabled-for-mam-on-ios-and-android"></a>iOS 和 Android 版本的 MAM 現在已可使用 Microsoft Teams

Microsoft 已經宣布 Microsoft Teams 正式運作。 更新後的 iOS 和 Android 版 Microsoft Teams 應用程式，現在可在 Intune 行動裝置應用程式管理 (MAM) 功能中使用，因此您可以讓您的團隊自由地跨裝置工作，同時確保每回的交談和公司資料都受到保護。 如需詳細資訊，請參閱 Enterprise Mobility and Security 部落格上的 [Microsoft Teams 公告](https://blogs.technet.microsoft.com/enterprisemobility/2017/03/14/microsoft-teams-is-now-generally-available-and-mam-enabled-on-ios-and-android/)。


## <a name="february-2017"></a>2017 年 2 月

### <a name="new-capabilities"></a>新功能

### <a name="modernizing-the-company-portal-website---753980--"></a>現代化公司入口網站 <!--753980-->
公司入口網站會支援以沒有受管理裝置的使用者為目標的應用程式。 網站會使用新的對比色彩配置、動態圖例及「漢堡功能表」，與其他 Microsoft 產品和服務達成一致， ![公司入口網站左上角新增的漢堡功能表小型影像](./media/CP_hamburger_menu.png)。

### <a name="notices"></a>通知

#### <a name="group-migration-will-not-require-any-updates-to-groups-or-policies-for-ios-devices---898837--"></a>群組移轉不需要 iOS 裝置群組或原則的任何更新 <!--898837-->
每個公司裝置註冊設定檔預先指派的 Intune 裝置群組，在移轉到 Azure Active Directory 裝置群組期間，都會根據公司裝置註冊設定檔的名稱，在 AAD 中建立對應的動態裝置群組。 這可確保在裝置註冊時，它們會自動分組，並與原始 Intune 群組收到相同的原則和應用程式。

一旦租用戶進入分組和鎖定目標的移轉程序，Intune 就會自動建立動態的 AAD 群組，以對應公司裝置註冊設定檔鎖定的 Intune 群組。 如果 Intune 管理員刪除了鎖定的 Intune 群組，就不會刪除對應的動態 AAD 群組。 群組成員和動態查詢會予以清除，但群組本身會一直保留到 IT 管理員透過 AAD 入口網站移除它。

同樣地，如果 IT 管理員變更公司裝置註冊設定檔鎖定的 Intune 群組，Intune 就會建立新的動態群組，反映新的設定檔指派，但不會移除舊指派建立的動態群組。

### <a name="defaulting-to-managing-windows-desktop-devices-through-windows-settings---663050--"></a>預設為透過 Windows 設定管理 Windows Desktop 裝置 <!--663050-->
註冊 Windows 10 Desktop 的預設行為會變更。 新的註冊將會遵循一般 MDM 代理程式註冊流程，而不是透過電腦代理程式。 公司入口網站會提供 Windows 10 Desktop 使用者，有關引導他們新增 Windows 10 Desktop 電腦作為行動裝置之程序的註冊指示。 這不會影響目前已註冊的電腦，而且您的組織還是可以使用電腦代理程式來管理 Windows 10 Desktop，如[設定 Windows 裝置管理](manage-windows-pcs-with-microsoft-intune.md)中所述。

#### <a name="improving-mobile-app-management-support-for-selective-wipe---581242--"></a>改善選擇性抹除的行動應用程式管理支援 <!--581242-->
如果因 [離線間隔幾天後抹除 App 資料] 原則而自動移除工作或學校資料，則會將如何重新存取工作或學校資料的其他指引授與終端使用者。<!--, or the removal of the Intune Company Portal on Android.-->

#### <a name="company-portal-for-ios-links-open-inside-the-app---665954--"></a>適用於 iOS 的公司入口網站連結會在應用程式內開啟 <!--665954-->
適用於 iOS 的公司入口網站應用程式連結 (包括文件和應用程式的連結) 會使用 Safari 的應用程式內檢視直接在公司入口網站應用程式中開啟。 這項更新將在 1 月與服務更新分開提供。

#### <a name="new-mdm-server-address-for-windows-devices---893007--"></a>Windows 裝置的新 MDM 伺服器位址 <!--893007-->
如果 Windows 和 Windows Phone 使用者輸入 __manage.microsoft.com__ 作為 MDM 伺服器位址 (系統提示時)，其嘗試註冊裝置會失敗。 MDM 伺服器位址已從 __manage.microsoft.com__ 變更為 __enrollment.manage.microsoft.com__。 請通知您的使用者，如果在註冊 Windows 或 Windows Phone 裝置時收到提示，請使用 __enrollment.manage.microsoft.com__ 作為 MDM 伺服器位址。 不需要變更您的 CNAME 設定。 如需此變更的其他資訊，請前往 [aka.ms/intuneenrollsvrchange](https://aka.ms/intuneenrollsvrchange)。

#### <a name="new-user-experience-for-the-company-portal-app-for-android---621622--"></a>Android 版公司入口網站應用程式的新使用者體驗 <!--621622-->
從 3 月起，Android 版公司入口網站應用程式會遵循[素材設計方針](https://material.io/guidelines/material-design/introduction.html)建立更現代化的外觀與風格。 此改善的使用者體驗包括︰

* __色彩__︰索引標籤標頭可根據您的自訂調色盤上色。
* __介面__：已更新 [應用程式] 索引標籤中的 [精選 App] 和 [所有應用程式] 按鈕。[搜尋] 按鈕現在是浮動的動作按鈕。
* __瀏覽__：[所有應用程式] 會以索引標籤式的檢視顯示 [精選]、[所有] 與 [類別] 以更方便瀏覽。
* __服務__：[我的裝置] 和 [連絡 IT] 索引標籤皆已改善可讀性。

您可以在 [UI updates for Intune end user apps](whats-new-app-ui.md) (Intune 終端使用者應用程式的 UI 更新) 頁面上找到更新前後的影像。

### <a name="associate-multiple-management-tools-with-the-microsoft-store-for-business---926135--"></a>商務用 Microsoft 網上商店的相關多重管理工具 <!--926135-->
如果您使用多種管理工具來部署商務用 Microsoft 網上商店應用程式，以前只能建立與其中一種與商務用 Microsoft 網上商店的關聯。 現在可以建立多種管理工具與市集的關聯性，例如，Intune 和 Configuration Manager。 如需詳細資料，請參閱[以 Microsoft Intune 管理購自商務用 Microsoft 網上商店的應用程式](windows-store-for-business.md)。

## <a name="whats-new-in-the-public-preview-of-intune-in-the-azure-portal---736542--"></a>Azure 入口網站中 Intune 公開預覽的新功能 <!--736542-->

在 2017 年初，我們會將完整系統管理體驗移轉到 Azure，以便在可透過圖形 API 擴充的新式服務平台上，對核心 EMS 工作流程進行強大的整合式管理。

新的試用租用戶將於本月開始看到 Azure 入口網站中新系統管理體驗的公開預覽。 在預覽狀態期間，將提供與現有 Intune 主控台相同與相當的功能。

Azure 入口網站中的系統管理體驗將使用已宣佈的新分組和目標設定功能；當您現有的租用戶移轉至新的分組體驗時，也會同時將您移轉，以預覽您租用戶的新系統管理體驗。 同時，如果您想要在移轉租用戶之前測試或查看任何新功能，請註冊新的 Intune 試用帳戶或查看[新文件](whats-new.md)。

您可以在[這裡](whats-new.md)找到 Azure 的 Intune 預覽新功能。

## <a name="january-2017"></a>2017 年 1 月

### <a name="new-capabilities"></a>新功能

#### <a name="in-console-reports-for-mam-without-enrollment---677961--"></a>無裝置註冊之 MAM 的主控台內報表 <!--677961-->
已註冊的裝置和未註冊的裝置已新增新的應用程式保護報表。 深入了解如何[使用 Intune 監視行動應用程式管理原則](app-protection-policies-monitor.md)。

#### <a name="android-711-support---694397--"></a>Android 7.1.1 支援 <!--694397-->
Intune 現在完全支援和管理 Android 7.1.1。

#### <a name="resolve-issue-where-ios-devices-are-inactive-or-the-admin-console-cannot-communicate-with-them---unknown--"></a>解決 iOS 裝置處於非使用狀態或管理員主控台無法與它們通訊的問題 <!--unknown-->
當使用者的裝置與 Intune 失去連絡時，您可以提供新的疑難排解步驟，協助他們重新取得公司資源的存取權。 請參閱[裝置處於非使用狀態或管理員主控台無法與它們通訊](troubleshoot-device-enrollment-in-intune.md#devices-are-inactive-or-the-admin-console-cant-communicate-with-them)。

### <a name="notices"></a>通知

#### <a name="defaulting-to-managing-windows-desktop-devices-through-windows-settings---663050--"></a>預設為透過 Windows 設定管理 Windows Desktop 裝置 <!--663050-->
註冊 Windows 10 Desktop 的預設行為會變更。 新的註冊將會遵循一般 MDM 代理程式註冊流程，而不是透過電腦代理程式。

公司入口網站會提供 Windows 10 Desktop 使用者，有關引導他們新增 Windows 10 Desktop 電腦作為行動裝置之程序的註冊指示。 這不會影響目前已註冊的電腦，而且您的組織還是可以使用電腦代理程式來管理 Windows 10 Desktop，如[設定 Windows 裝置管理](manage-windows-pcs-with-microsoft-intune.md)中所述。

#### <a name="improving-mobile-app-management-support-for-selective-wipe---581242--"></a>改善選擇性抹除的行動應用程式管理支援 <!--581242-->
如果因 [離線間隔幾天後抹除 App 資料] 原則而自動移除工作或學校資料，則會將如何重新存取工作或學校資料的其他指引授與終端使用者。<!--, or the removal of the Intune Company Portal on Android.-->

#### <a name="company-portal-for-ios-links-open-inside-the-app---665954--"></a>適用於 iOS 的公司入口網站連結會在應用程式內開啟 <!--665954-->
適用於 iOS 的公司入口網站應用程式連結 (包括文件和應用程式的連結) 會使用 Safari 的應用程式內檢視直接在公司入口網站應用程式中開啟。 這項更新將在 1 月與服務更新分開提供。

#### <a name="modernizing-the-company-portal-website---753980--"></a>現代化公司入口網站 <!--753980-->
從 2 月開始，公司入口網站將支援以沒有受管理裝置的使用者為目標的應用程式。 網站會使用新的對比色彩配置、動態圖例及「漢堡功能表」，與其他 Microsoft 產品和服務達成一致， ![公司入口網站漢堡功能表](./media/CP_hamburger_menu.png)。

#### <a name="new-documentation-for-app-protection-policies---583398--"></a>應用程式保護原則的新文件 <!--583398-->
針對想要使用 Intune App Wrapping Tool 或 Intune App SDK 在 iOS 和 Android 應用程式中啟用應用程式保護原則 (稱為 MAM 原則) 的系統管理員和應用程式開發人員，我們已更新他們適用的文件。

已更新下列文章：

* [決定如何準備應用程式以使用 Microsoft Intune 進行行動應用程式管理](apps-prepare-mobile-application-management.md)
* [準備將 iOS 應用程式交由 Intune App Wrapping Tool 進行行動應用程式管理](app-wrapper-prepare-ios.md)
* [開始使用 Microsoft Intune App SDK](app-sdk-get-started.md)
* [Intune App SDK for iOS 開發人員指南](app-sdk-ios.md)

下列文章是文件庫的新增項目︰

* [Intune App SDK Cordova 外掛程式](app-sdk-cordova.md)
* [Intune App SDK Xamarin 元件](app-sdk-xamarin.md)

#### <a name="progress-bar-when-launching-the-company-portal-on-ios---665978--"></a>在 iOS 上啟動公司入口網站時的進度列 <!--665978-->
適用於 iOS 的公司入口網站會在啟動畫面上引進進度列，以將所發生之載入程序的相關資訊提供給使用者。 將會有進度列的階段性推出，來取代微調按鈕。 這表示部分使用者將會看到新的進度列，而其他人則會持續看見微調按鈕。

## <a name="december-2016"></a>2016 年 12 月

### <a name="public-preview-of-intune-in-the-azure-portal--736542--"></a>Azure 入口網站中的 Intune 公開預覽<!--736542-->
在 2017 年初，我們會將完整管理體驗移轉到 Azure，以便在可透過圖形 API 擴充的新式服務平台上，對核心 EMS 工作流程進行強大的整合式管理。 在將此入口網站的正式運作版本提供給所有 Intune 租用戶之前，我們很高興地宣布在本月稍晚將會推出這個新管理體驗的預覽給特定租用戶。

Azure 入口網站中的管理體驗將使用已宣佈的新群組和目標設定功能；當您現有的租用戶移轉至新的群組體驗時，也會同時將您移轉，以預覽您租用戶的新管理體驗。 在此同時，請在我們的[新文件](/intune/what-is-intune)中深入了解我們在 Azure 入口網站中針對 Microsoft Intune 做了哪些準備。

__Azure 入口網站的電信費用管理整合公開預覽__ <!--747605--> 我們現在將開始在 Azure 入口網站中預覽與第三方電信費用管理 (TEM) 服務的整合。 您可以使用 Intune 強制執行限制國內和漫遊資料使用量。 我們將開始與 [Saaswedo](http://www.saaswedo.com/) 進行這些整合。 若要在您的試用版租用戶中啟用此功能，請[連絡 Microsoft 支援服務](get-support.md)。

### <a name="new-capabilities"></a>新功能

__跨所有平台的 Multi-Factor Authentication__ <!--747590--> 您現在可以在一組選取的使用者從 Azure 管理入口網站註冊 iOS、Android、Windows 8.1+ 或 Windows Phone 8.1+ 裝置時，對這些使用者強制執行 Multi-Factor Authentication (MFA)，方法是在 Azure Active Directory 中設定 Microsoft Intune 註冊應用程式的相關 MFA。

__限制行動裝置註冊的能力__ <!--747596--> Intune 正在新增新的註冊限制，以控制哪些行動裝置平台可以註冊。 Intune 將行動裝置平台分為 iOS、macOS、Android、Windows 和 Windows Mobile。
* 限制行動裝置註冊不會限制電腦用戶端註冊。
* 有一個僅適用於之iOS 的額外選項可封鎖個人擁有的裝置註冊。

Intune 會將所有的新裝置標示為個人，除非 IT 系統管理員採取動作將它們標示為公司擁有，如[本文章](device-enrollment.md)所說明。

### <a name="notices"></a>通知

__移動到 Azure 入口網站之註冊上的 Multi-Factor Authentication__ <!--VSO 750545--> 先前，系統管理員會移至 Intune 主控台或 Configuration Manager (2016 年 10 月以前的版本) 主控台，以設定用於 Intune 註冊的 MFA。 透過這項更新的功能，您現在將會使用 Intune 認證登入 [Microsoft Azure 入口網站](https://manage.windowsazure.com)，並透過 Azure AD 進行 MFA 設定。 如需詳細資訊，請參閱[這裡](https://aka.ms/mfa_ad)。

__適用於 Android 的 [公司入口網站] 應用程式現在可在中國使用__ <!--VSO 658093--> 我們將在中國發佈適用於 Android 的公司入口網站應用程式以供下載。 由於中國沒有 Google Play 商店，因此 Android 裝置必須從中文應用程式市集取得應用程式。 適用於 Android 的公司入口網站應用程式可在下列市集下載：
* [百度](https://go.microsoft.com/fwlink/?linkid=836946)
* [華為](https://go.microsoft.com/fwlink/?linkid=836948)
* [騰訊](https://go.microsoft.com/fwlink/?linkid=836949)
* [豌豆莢](https://go.microsoft.com/fwlink/?linkid=836950)
* [小米應用商店](https://go.microsoft.com/fwlink/?linkid=836947)

適用於 Android 的公司入口網站應用程式會使用 Google Play 服務來與 Microsoft Intune 服務通訊。 由於中國尚無法使用 Google Play 服務，因此執行下列任何工作可能需要多達 8 小時才能完成。 

|Intune 管理主控台| 適用於 Android 的 Intune 公司入口網站應用程式 |Intune 公司入口網站|   
|---|---|---|
|完整抹除| 移除遠端裝置| 移除裝置 (本機和遠端)|
|選擇性抹除| 重設裝置| 重設裝置|
|新的或更新的應用程式部署| 安裝可用的企業營運應用程式| 裝置密碼重設|
|遠端鎖定|||
|密碼重設|||

### <a name="deprecations"></a>棄用功能

__Firefox 不再支援 Silverlight__ <!--VSO TBA--> Mozilla 將於 [Firefox 瀏覽器](https://www.mozilla.org/firefox)版本 52 中移除對 Silverlight 的支援，2017 年 3 月起生效。 如此一來，您將無法再使用 Firefox 51 版之後的版本登入現有的 Intune 主控台。 建議使用 Internet Explorer 10 或 11，或是 [Firefox 52 版之前的版本](https://ftp.mozilla.org/pub/firefox/releases/)來存取管理主控台。 Intune 轉換到 Azure 入口網站將可在不需要 Silverlight 相依性的情況下，支援數種[現代化瀏覽器](/azure/azure-preview-portal-supported-browsers-devices)。

__移除 Exchange Online 行動信箱原則__ <!--770687--> 從 12 月開始，系統管理員將無法再於 Intune 主控台內檢視或設定 Exchange Online (EAS) 行動信箱原則。 這項變更會從 12 月到 1 月推出給所有 Intune 租用戶。 所有現有的原則將會保持設定狀態；若要設定新的原則，請使用 Exchange 管理命令介面。 如需詳細資訊，請參閱[這裡](https://technet.microsoft.com/library/bb123783%28v=exchg.150%29.aspx)。

__Android 上不再支援 Intune AV Player、Image Viewer 和 PDF Viewer 應用程式__ <!--747553--> 從 2016 年 12 月中開始，使用者將無法再使用 Intune AV Player、Image Viewer 和 PDF Viewer 應用程式。 這些應用程式已取代成 Azure 資訊保護應用程式。 如需 Azure 資訊保護應用程式的詳細資訊，請參閱[這裡](/information-protection/rms-client/mobile-app-faq)。

## <a name="november-2016"></a>2016 年 11 月

### <a name="new-capabilities"></a>新功能

__可供 Windows 10 裝置使用的新 Microsoft Intune 公司入口網站__  Microsoft 已經發行 [Windows 10 裝置適用的新 Microsoft Intune 公司入口網站應用程式](https://www.microsoft.com/store/apps/9wzdncrfj3pz)。 利用新的 Windows 10 通用格式的此應用程式，會為使用者提供應用程式內更新的使用者體驗，以及所有 Windows 10 裝置、電腦和類似行動裝置的相同體驗，同時啟用他們目前仍在使用的相同功能。

新的應用程式也可讓使用者運用其他平台功能，例如單一登入 (SSO) 和 Windows 10 裝置上的憑證型驗證。 應用程式會以現有的 Windows 8.1 公司入口網站升級，以及從 Microsoft 網上商店安裝的 Windows Phone 8.1 公司入口網站的方式提供。 如需詳細資訊，請前往 [aka.ms/intunecp_universalapp](http://aka.ms/intunecp_universalapp)。

> [!IMPORTANT]
> __在 Intune 和 Android for Work 上的更新__ 雖然您可以用__必要__動作部署 Android for Work 應用程式，但如果您已將 Intune 群組移轉至新的 Azure AD 群組，就只能將應用程式部署為__可用__。

__Intune App SDK for Cordova 外掛程式現在支援 MAM 而不需註冊__ 應用程式開發人員可以現在使用 Intune App SDK for Cordova 外掛程式啟用 MAM 功能，而不必在其 Android 和 iOS 的 Cordova 應用程式進行裝置註冊。 您可以在[這裡](https://github.com/msintuneappsdk/cordova-plugin-ms-intune-mam)找到 Intune App SDK for Cordova 外掛程式。

__Intune App SDK Xamarin 元件現在支援 MAM 而不需註冊__ 應用程式開發人員可以現在使用 Intune App SDK Xamarin 元件啟用 MAM 功能，而不必在其 Android 和 iOS 的 Xamarin 應用程式進行裝置註冊。 您可以在[這裡](https://github.com/msintuneappsdk/intune-app-sdk-xamarin)找到 Intune App SDK Xamarin 元件。

### <a name="notices"></a>通知

__Symantec 簽署憑證不再需要已簽署的 Windows Phone 8 公司入口網站以進行上傳__ 上傳 Symantec 簽署憑證不再需要已簽署的 Windows Phone 8 公司入口網站應用程式。 可以獨立上傳憑證。

### <a name="deprecations"></a>棄用功能

__Windows Phone 8 公司入口網站的支援__ 對 Windows Phone 8 公司入口網站的支援現在將被取代。 對於 Windows Phone 8 和 WinRT 平台的支援已在 2016 年 10 月被取代。 對於 Windows 8 公司入口網站的支援也已在 2016 年 10 月被取代。


### <a name="see-also"></a>另請參閱
如需近期發展的詳細資料，請參閱 [Microsoft Intune 的新功能](whats-new.md)。

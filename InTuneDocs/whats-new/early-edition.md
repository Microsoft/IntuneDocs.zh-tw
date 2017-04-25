---
title: "舊版 | Microsoft Docs"
description: 
keywords: 
author: mtillman
ms.author: mtillman
manager: angrobe
ms.date: 04/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 0a39abc7f19f4c2c8074de66a9cd5df9cef78ed5
ms.openlocfilehash: 2b6e29e7323d42b1ce3d75a46648203a7a43165c
ms.lasthandoff: 04/13/2017


---


# <a name="the-early-edition-for-microsoft-intune---april-2017"></a>Microsoft Intune 的舊版 - 2017 年 4 月

**舊版**提供 Microsoft Intune 即將發行版本要推出的功能清單。 此資訊以非常有限的基礎在 NDA 下提供，並可能有所變更。 這裡列出的一些功能可能有截止日期，而且可能會延遲到未來的版本。 其他功能正在實驗 (測試) 中進行測試，以確保它們可供客戶使用。 如果你們有任何問題或疑慮，請洽詢 Intune/PM 人員。

此頁面會定期更新。 請回來查看其他更新。

> [!Note]
> 下列變更正在 Intune 的開發過程中。 混合式客戶部署於未來將會支援這些功能 (具備 Intune 的 Configuration Manager)。 如需新混合式功能的詳細資訊，請查看我們的 [Hybrid What’s New](https://docs.microsoft.com/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management) (混合式新功能) 頁面。

## <a name="new-capabilities"></a>新功能

### <a name="improved-app-install-status-for-the-windows-10-company-portal-app---676495--"></a>改進 Windows 10 公司入口網站應用程式的應用程式安裝狀態 <!--676495-->

Windows 10 公司入口網站應用程式現在會針對從公司入口網站開始進行的所有現代應用程式安裝，提供應用程式安裝進度列。

### <a name="improved-status-messaging-in-the-company-portal-app-for-ios---744866--"></a>改進 iOS 公司入口網站應用程式中的狀態訊息 <!--744866-->

iOS 公司入口網站應用程式中現在會顯示更具體的新錯誤訊息，以提供有關裝置狀況之更容易存取的資訊。 這些錯誤狀況之前包含在標題為「公司入口網站暫時無法使用」的一般錯誤訊息中。 此外，如果使用者在沒有網際網路連線時啟動 iOS 上的公司入口網站，則會在首頁上看到持續性狀態列，指出「沒有網際網路連線」。

### <a name="myapps-available-for-managed-browser---822308-822303--"></a>MyApps 可供 Managed Browser 使用 <!--822308, 822303-->

Microsoft MyApps 現在於 Managed Browser 中提供更佳支援。 非管理目標的 Managed Browser 使用者將會直接進入 MyApps 服務，以在其中存取其系統管理員佈建的 SaaS 應用程式。 Intune 管理目標的使用者將能夠繼續從內建 Managed Browser 書籤存取 MyApps。

### <a name="new-icons-for-the-managed-browser-and-the-company-portal---918433-918431--"></a>Managed Browser 和公司入口網站的新圖示 <!--918433, 918431-->

Managed Browser 會同時收到 Android 和 iOS 版應用程式的更新圖示。 此新圖示會包含更新的 Intune 徽章，因此與 Enterprise Mobility + Security (EM+S) 中的其他應用程式更一致。 您可以在 [Intune App UI 頁面的新功能](whats-new-in-intune-app-ui.md)中看到 Managed Browser 的新圖示。

公司入口網站也會收到 Android、iOS 和 Windows 版應用程式的更新圖示，以改進與 EM+S 中其他應用程式的一致性。 從四月到五月底，這些圖示會逐漸在各平台發行。

### <a name="single-sign-on-support-from-the-company-portal-for-ios-to-outlook-for-ios---834012--"></a>從 iOS 版入口網站到 iOS 版 Outlook 的單一登入 <!--834012-->

如果使用者在同一部裝置上使用相同的帳戶登入 iOS 公司入口網站應用程式，則不必再登入 Outlook 應用程式。 當使用者啟動 Outlook 應用程式時，將能夠選取其帳戶並自動登入。 我們也將努力為其他 Microsoft 應用程式新增這項功能。

### <a name="sign-in-progress-indicator-in-android-company-portal---953374--"></a>Android 公司入口網站中的登入進度列指示器 <!--953374-->

Android 公司入口網站應用程式的更新會在使用者啟動或繼續執行應用程式時，顯示登入進度指示器。 該指示器會顯示新的狀態進度，一開始為「正在連線...」，接著依序為「正在登入...」和「正在檢查安全性需求...」，之後才允許使用者存取應用程式。 您可以在 [Intune App UI 頁面的新功能](whats-new-in-intune-app-ui.md)中看到 Android 公司入口網站應用程式的新畫面。 


## <a name="notices"></a>通知

### <a name="apple-to-require-updates-for-application-transport-security---748318--"></a>Apple 需要更新 Application Transport Security <!--748318-->

Apple 宣告，從 2017 年春季開始，將會強制執行 Application Transport Security (ATS) 的特定需求。 ATS 可用來對透過 HTTPS 進行的所有應用程式通訊，強制執行更嚴格的安全性。 這項變更會影響使用 iOS 公司入口網站應用程式的 Intune 客戶。 如需詳細資訊，請檢閱我們的 [Intune 支援部落格](https://aka.ms/compportalats)。

### <a name="direct-access-to-apple-enrollment-scenarios---951869--"></a>直接存取 Apple 註冊案例 <!--951869-->

對於在 2017 年 1 月之後建立的 Intune 帳戶，Intune 已經啟用使用 Azure Preview 入口網站中的「註冊裝置」工作負載直接存取 Apple 註冊案例。 Apple 註冊預覽原本只能從傳統 Intune 入口網站中的連結存取。 在 2017 年 1 月之前建立的 Intune 帳戶，將需要進行一次性移轉，才能在 Azure 中使用這些功能。 移轉的排程尚未宣布，但將會盡快提供詳細資料。 如果您現有的帳戶無法存取預覽，我們強烈建議您建立試用帳戶來測試新的體驗。

### <a name="whats-coming-for-appx-in-intune-on-azure----1000270---"></a>Appx 在 Azure 上的 Intune 中的未來動態 <!-- 1000270 -->

在移轉到 Azure 上的 Intune 的過程中，我們將進行三項 appx 變更：

1. 在傳統 Intune 主控台中，新增只能部署到 MDM 註冊裝置的 appx 應用程式類型。
2. 重新規劃現有的 appx 應用程式類型，將目標僅限於透過 Intune 電腦代理程式管理的電腦。
3. 透過移轉，將所有現有的 appxs 轉換成 MDM appxs。

#### <a name="how-does-this-affect-me"></a>這項變更對我造成什麼影響？

這不會影響透過 Intune 電腦代理程式管理之裝置上的任何現有部署。 不過移轉之後，您無法將這些移轉的 appxs 部署到透過 Intune 電腦代理程式管理但先前未設為目標的任何新裝置。

#### <a name="what-action-do-i-need-to-take"></a>我需要採取什麼動作

移轉之後，如果您想要執行新的電腦部署，您將必須再次重新上傳 appx 作為電腦的 appx。 若要深入了解，請參閱 Intune 支援小組部落格上的 [Appx changes in Intune on Azure](https://aka.ms/appxchange) (Azure 上的 Intune 中的 Appx 變更)。  


## <a name="public-preview-of-the-new-intune-admin-experience-on-azure---736542--"></a>Azure 上新 Intune 管理體驗的公開預覽 <!--736542-->

在 2017 年初，我們會將完整管理體驗移轉到 Azure，以便在可透過圖形 API 擴充的新式服務平台上，對核心 EMS 工作流程進行強大的整合式管理。

新的試用租用戶將於本月開始看到 Azure 入口網站中新管理體驗的公開預覽。 在預覽狀態期間，將透過現有的 Intune 主控台反覆提供功能和同位檢查。

Azure 入口網站中的管理體驗將使用已宣佈的新群組和目標設定功能；當您現有的租用戶移轉至新的群組體驗時，也會同時將您移轉，以預覽您租用戶的新管理體驗。 在此同時，如果您想要在移轉租用戶之前測試或查看任何新功能，請註冊新的 Intune 試用帳戶或查看[新文件](https://docs.microsoft.com/intune-azure/introduction/what-is-microsoft-intune)。

### <a name="support-for-managed-configuration-options-for-android-apps----621621---"></a>支援 Android 應用程式的受管理設定選項 <!-- 621621 -->

Intune 可以設定 Play Store 中支援受管理設定選項的 Android 應用程式。  這項功能可讓 IT 人員檢視應用程式所支援的設定值清單，並提供頂級的引導式 UI，讓 IT 人員可以設定這些值。

### <a name="remote-assistance-for-android-devices----675418---"></a>Android 裝置的遠端協助 <!-- 675418 -->

Intune 將會使用另行購買的 [TeamViewer](https://www.teamviewer.com) 軟體，讓您為執行 Android 裝置的使用者提供遠端協助。

### <a name="new-android-policy-for-complex-pins----722069---"></a>新增複雜 PIN 碼的 Android 原則 <!-- 722069 -->

您可以在 Android 裝置設定檔中，針對執行 Android 5.0 和更新版本的裝置，將必要的密碼類型設定為複雜數字。  使用此設定可防止裝置使用者建立包含重複或連續數字的 PIN 碼，例如 1111 或 1234。

### <a name="additional-support-for-android-for-work-devices"></a>Android for Work 裝置的其他支援

- **管理密碼和工作設定檔設定** <!-- 612808 -->

  我們新增了 Android for Work 裝置限制原則，可讓您在所管理的 Android for Work 裝置上管理密碼和工作設定檔設定。

- **允許工作和個人設定檔間的資料共用** <!-- 1045102 -->

  我們已更新 Android for Work 裝置限制設定檔中的 [工作設定檔與個人設定檔之間的資料共用] 設定，新增選項來協助您設定工作和個人設定檔間的資料共用。

- **限制工作和個人設定檔間的複製和貼上** <!-- 1046094 -->

  當您使用 Intune 管理 Android for Work 裝置時，允許工作和個人應用程式間的複製和貼上動作。 我們現在新增了 Android for Work 裝置的自訂裝置設定檔，讓您限制是否允許工作和個人應用程式間的複製和貼上動作。

### <a name="assign-lob-apps-to-ios-and-android-devices----1057568---"></a>將 LOB 應用程式指派給 iOS 和 Android 裝置 <!-- 1057568 -->

您可以將 iOS 版企業營運應用程式 (.ipa 檔案) 和 Android 版企業營運應用程式 (.apk 檔案) 指派給使用者或裝置。

###  <a name="new-policies-for-ios-devices----723774-723815-723826-723830-723832---"></a>iOS 裝置的新原則 <!-- 723774, 723815, 723826, 723830, 723832 -->

- **主畫面上的應用程式** - 您可以使用裝置原則，控制使用者會在其 iOS 裝置的主畫面上看到哪些應用程式。 這項原則會變更主畫面的配置，但不會部署您所指定但未安裝的任何應用程式。

- **AirPrint 裝置的連線** - 您可以使用 Intune 裝置原則，控制 iOS 裝置的終端使用者可以連線到哪些 AirPrint 裝置 (網路印表機)。

- **AirPlay 裝置的連線** - 您可以使用 Intune 裝置原則，控制 iOS 裝置的終端使用者可以連線到哪些 AirPlay 裝置 (例如 Apple TV)。

- **自訂鎖定畫面訊息** - 您可以設定使用者將會在其 iOS 裝置的鎖定畫面上看到的自訂訊息，這會取代預設鎖定畫面訊息。

- **網路內容篩選器** - 您可以控制 iOS 裝置的哪些網站使用者可以使用下列兩種方法之一進行瀏覽：

  - 使用 Apple 內建網路內容篩選器新增允許和封鎖的 URL。
  - 僅允許 Safari 瀏覽器存取指定的網站。 針對您指定的每個網站，會在 Safari 中建立書籤。


### <a name="restrict-push-notifications-for-ios-apps----723767---"></a>限制 iOS 應用程式的推播通知 <!-- 723767 -->

在 Intune 裝置限制設定檔中，您可以設定 iOS 裝置的下列通知設定：

- 完全開啟或關閉指定應用程式的通知。
- 在通知中心內開啟或關閉指定應用程式的通知。
- 指定警示類型，可以是 [無]、[橫幅] 或 [Modal Alert] (強制回應警示)。
- 指定此應用程式是否允許徽章。
- 指定是否允許通知音效。

### <a name="configure-ios-apps-to-run-in-single-app-mode-autonomously----737837---"></a>設定 iOS 應用程式在單一應用程式模式中自發執行 <!-- 737837 -->

您可以使用 Intune 裝置設定檔，設定 iOS 裝置在自發性單一應用程式模式中執行指定的應用程式。 設定此模式並執行應用程式時，裝置會被鎖定，因此只能執行該應用程式。 一個例子是當您設定應用程式讓使用者在裝置上進行測試時。 當應用程式的動作完成時，或當您移除此原則時，裝置就會回到其正常狀態。

### <a name="configure-trusted-domains-for-email-and-web-browsing-on-ios-devices----723765---"></a>為 iOS 裝置上的電子郵件和網頁瀏覽設定受信任的網域 <!-- 723765 -->

您可以從 iOS 裝置限制設定檔進行下列網域設定：

- **未標示的電子郵件網域** - 使用者傳送或接收的電子郵件，若不符合您於此處所指定的網域，會標示為不受信任。

- **受管理的 Web 網域** - 從您於此處指定的 URL 下載之文件，會視為受管理的文件 (僅限 Safari)。  

- **Safari 密碼自動填入網域** - 使用者在 Safari 中可以儲存的密碼，只有來自與此處指定的模式相符之 URL 的密碼。 若要使用此設定，裝置必須在受監督的模式下，且未設定供多重使用者之用。 (iOS 9.3+)


### <a name="vpp-apps-available-in-ios-company-portal----748782---"></a>IOS 公司入口網站中可以使用 VPP 應用程式 <!-- 748782 -->

您可以將 iOS 大量採購 (VPP) 應用程式當做**可用**的安裝指派給終端使用者。 終端使用者必須有 Apple Store 帳戶，才能安裝應用程式。

### <a name="synchronize-ebooks-from-apple-vpp-store----800878---"></a>從 Apple VPP Store 同步處理電子書 <!-- 800878 -->

您可以將從 Apple 大量採購程式市集購買的書籍與 Intune 同步處理，然後將這些書籍指派給使用者。

### <a name="multi-user-management-for-samsung-knox-standard-devices----971988---"></a>Samsung KNOX Standard 裝置的多使用者管理 <!-- 971988 -->

Intune 的多使用者管理現在支援執行 Samsung KNOX Standard 的裝置。 這表示終端使用者可以使用其 Azure Active Directory 認證登入和登出裝置，而且該裝置不論是否正在使用，都會集中管理。  當終端使用者登入時，他們可以存取應用程式，此外也可以將任何原則套用到這些應用程式。 當使用者登出時，會清除所有應用程式資料。

### <a name="additional-windows-device-restriction-settings----818566---"></a>其他 Windows 裝置限制設定 <!-- 818566 -->

我們新增了其他 Windows 裝置限制設定的支援，例如其他 Edge 瀏覽器支援、裝置鎖定畫面自訂、開始功能表自訂、Windows 焦點搜尋集底色圖案和 Proxy 設定。

### <a name="multi-user-support-for-windows-10-creators-update----822547---"></a>Windows 10 Creators Update 的多使用者支援 <!-- 822547 -->

我們針對執行 Windows 10 Creators Update 並加入 Azure Active Directory 網域的裝置，新增了多使用者管理的支援。 這表示當不同的使用者使用其 AAD 認證登入裝置時，將會收到指派給其使用者名稱的任何應用程式和原則。

### <a name="fresh-start-for-windows-10-pcs---1004830---"></a>Windows 10 電腦的 Fresh Start<!-- 1004830 -->

在此版本中，我們為 Windows 10 電腦新增了 Fresh Start 裝置動作。  當您發出此動作時，將會移除任何安裝在電腦上的應用程式，而且電腦會自動更新為最新版的 Windows。 這可用來協助移除通常會隨新電腦提供之預先安裝的 OEM 應用程式。 您可以設定是否在發出此裝置動作時保留使用者資料。

### <a name="additional-windows-10-upgrade-paths----903672---"></a>其他 Windows 10 升級路徑 <!-- 903672 -->

您現在可以建立版本升級原則，來將裝置升級為下列其他的 Windows 10 版本：

- Windows 10 Professional
- Windows 10 Professional N
- Windows 10 專業教育版
- Windows 10 專業教育版 N

### <a name="bulk-enroll-windows-10-devices----747607---"></a>大量註冊 Windows 10 裝置 <!-- 747607 -->

您可以使用 IT 自動化工具，將大量 Windows 10 裝置加入 Azure Active Directory 和 Intune。 若要啟用您的 Azure AD 租用戶的自動 MDM 註冊，請建立佈建套件，透過 Windows 設定設計工具將裝置加入 Azure AD 租用戶。 將該套件套用到您要大量註冊及管理之公司擁有的裝置。  套用套件之後，裝置會連線到 Azure AD、在 Intune 中註冊，並準備好供 Azure AD 使用者登入。

### <a name="new-mam-settings-for-pin-and-managed-storage-locations----58112-736644---"></a>PIN 碼和受管理儲存位置的新 MAM 設定 <!-- 58112, 736644 -->

有兩個新的應用程式設定可協助您進行行動應用程式管理 (MAM) 案例：

- **在管理裝置 PIN 碼時停用應用程式 PIN 碼** - 偵測已註冊的裝置上是否有裝置 PIN 碼；如果有，則略過應用程式保護原則觸發的應用程式 PIN 碼。 這項設定可減少對在已註冊裝置上開啟啟用 MAM 的應用程式之使用者顯示的 PIN 提示次數。 這項功能適用於 Android 和 iOS。

- **選取要用於儲存公司資料的儲存體服務** - 可讓您指定要用於儲存公司資料的儲存位置。 使用者可以儲存至所選取的儲存位置服務，這表示將會封鎖未列出的其他所有儲存位置服務。

  支援的儲存位置服務清單：

  - OneDrive
  - 商務用 SharePoint Online
  - 本機儲存體


### <a name="see-also"></a>請參閱
如需近期發展的詳細資料，請參閱 [Microsoft Intune 的新功能](whats-new-in-microsoft-intune.md)。


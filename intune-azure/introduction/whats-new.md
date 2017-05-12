---
title: "Microsoft Intune 預覽版的新功能"
titleSuffix: Intune Azure preview
description: "了解 Intune Azure 預覽版中的新功能"
keywords: 
author: mtillman
ms.author: mtillman
manager: angrobe
ms.date: 04/29/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 791ed23f-bd13-4ef0-a3dd-cd2d7332c5cc
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 3758df744311392528be01c826527c2a9d879975
ms.openlocfilehash: f209429bbafe50530e90bbaf133f780f448a8c57
ms.contentlocale: zh-tw
ms.lasthandoff: 05/10/2017

---

# <a name="whats-new-in-the-microsoft-intune-preview"></a>Microsoft Intune 預覽版的新功能

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

隨著公開預覽版的推出，更多新功能陸續加入，我們利用這裡的版面提供相關資訊。

> [!Note]
> 我們將首度發行此頁面所列出的 Azure 入口網站預覽版變更。 不過，基於 Intune 服務更新的方式不同，變更可能無法立即生效。  數個服務元件必須依序更新，才能使用新的入口網站功能。 這些變更於近日首度發行時請務必試試看。

## <a name="april-2017"></a>2017 年 4 月

### <a name="support-for-managing-the-apple-classroom-app"></a>支援管理 Apple「課堂」應用程式

您現在可在 iPad 裝置上管理 iOS「課堂」應用程式。 使用正確的課堂和學生資料，在老師的 iPad 上設定「課堂」應用程式，然後設定學生的 iPad 向課堂註冊，這樣您就能使用應用程式控制它們。
如需詳細資訊，[設定 iOS 的教育設定](../configure-devices/how-to-configure-ios-edu-settings.md)。

### <a name="support-for-managed-configuration-options-for-android-apps----621621---"></a>支援 Android 應用程式的受管理設定選項 <!-- 621621 -->

Intune 現在可以設定 Play 商店中支援受管理設定選項的 Android 應用程式。  這項功能可讓 IT 人員檢視應用程式所支援的設定值清單，並提供頂級的引導式 UI，讓 IT 人員可以設定這些值。

### <a name="new-android-policy-for-complex-pins----722069---"></a>新增複雜 PIN 碼的 Android 原則 <!-- 722069 -->

您現在可以在 Android 裝置設定檔中，針對執行 Android 5.0 和更新版本的裝置，將必要的[密碼](../configure-devices/device-restrictions-for-android.md#password)類型設定為複雜數字。  使用此設定可防止裝置使用者建立包含重複或連續數字的 PIN 碼，例如 1111 或 1234。

### <a name="additional-support-for-android-for-work-devices"></a>Android for Work 裝置的其他支援

- **管理密碼和工作設定檔設定** <!-- 612808 -->

  這項新的 Android for Work 裝置限制原則現在可讓您在所管理的 Android for Work 裝置上管理密碼和工作設定檔設定。

- **允許工作和個人設定檔間的資料共用** <!-- 1045102 -->

Android for Work 裝置限制設定檔現在有新的選項，可協助您設定工作和個人設定檔之間的資料共用。

- **限制工作和個人設定檔間的複製和貼上** <!-- 1046094 -->

  Android for Work 裝置的新自訂裝置設定檔現在可讓您限制是否允許工作和個人應用程式間的複製和貼上動作。

如需詳細資訊，請參閱 [Android for Work 的裝置限制](../configure-devices/device-restrictions-for-afw.md)。

### <a name="assign-lob-apps-to-ios-and-android-devices----1057568---"></a>將 LOB 應用程式指派給 iOS 和 Android 裝置 <!-- 1057568 -->

您現在可以將 [iOS](../manage-apps/ios-lob-app.md) 版企業營運 (LOB) 應用程式 (.ipa 檔案) 和 [Android](../manage-apps/android-lob-app.md) 版企業營運應用程式 (.apk 檔案) 指派給使用者或裝置。

###  <a name="new-device-policies-for-ios----723774-723815-723826-723830---"></a>iOS 的新裝置原則 <!-- 723774, 723815, 723826, 723830 -->

- **主畫面上的應用程式**：控制使用者會在[其 iOS 裝置的主畫面](../configure-devices/home-screen-settings-for-ios.md)上看到哪些應用程式。 這項原則會變更主畫面的配置，但不會部署您所指定但未安裝的任何應用程式。

- **AirPrint 裝置的連線**：控制 iOS 裝置的使用者可以連線到哪些 [AirPrint 裝置](../configure-devices/air-print-settings-for-ios-and-macos.md) (網路印表機)。

- **AirPlay 裝置的連線**：控制 iOS 裝置的使用者可以連線到哪些 [AirPlay 裝置](../configure-devices/airplay-settings-for-ios-devices.md) (例如 Apple TV)。

- **自訂鎖定畫面訊息**：設定使用者將會在其 iOS 裝置的鎖定畫面上看到的自訂訊息，這會取代預設鎖定畫面訊息。 如需詳細資訊，請參閱[可執行的裝置動作](../manage-devices/what-is.md#available-device-actions)


### <a name="restrict-push-notifications-for-ios-apps----723767---"></a>限制 iOS 應用程式的推播通知 <!-- 723767 -->

在 Intune 裝置限制設定檔中，您現在可以設定 iOS 裝置的下列[通知設定](../configure-devices/app-notification-settings-for-ios.md)：

- 完全開啟或關閉指定應用程式的通知。
- 在通知中心內開啟或關閉指定應用程式的通知。
- 指定警示類型，可以是 [無]、[橫幅] 或 [Modal Alert] (強制回應警示)。
- 指定此應用程式是否允許徽章。
- 指定是否允許通知音效。

### <a name="configure-ios-apps-to-run-in-single-app-mode-autonomously----737837---"></a>設定 iOS 應用程式在單一應用程式模式中自發執行 <!-- 737837 -->

您現在可以使用 Intune 裝置設定檔，設定 iOS 裝置在[自發性單一應用程式模式](../configure-devices/device-restrictions-for-ios.md#autonomous-single-app-mode-supervised-only)中執行指定的應用程式。 設定此模式並執行應用程式時，裝置會被鎖定，因此只能執行該應用程式。 一個例子是當您設定應用程式讓使用者在裝置上進行測試時。 當應用程式的動作完成時，或當您移除此原則時，裝置就會回到其正常狀態。

### <a name="configure-trusted-domains-for-email-and-web-browsing-on-ios-devices----723765---"></a>為 iOS 裝置上的電子郵件和網頁瀏覽設定受信任的網域 <!-- 723765 -->

您現在可以從 iOS 裝置限制設定檔設定下列[網域設定](../configure-devices/device-restrictions-for-ios.md#domains)：

- **未標示的電子郵件網域** - 使用者傳送或接收的電子郵件，若不符合您於此處所指定的網域，會標示為不受信任。

- **受管理的 Web 網域** - 從您於此處指定的 URL 下載之文件，會視為受管理的文件 (僅限 Safari)。  

- **Safari 密碼自動填入網域** - 使用者在 Safari 中可以儲存的密碼，只有來自與此處指定的模式相符之 URL 的密碼。 若要使用此設定，裝置必須在受監督的模式下，且未設定供多重使用者之用。 (iOS 9.3+)


### <a name="vpp-apps-available-in-ios-company-portal----748782---"></a>IOS 公司入口網站中可以使用 VPP 應用程式 <!-- 748782 -->

您現在可以將 iOS 大量採購 (VPP) 應用程式當做「可用」的安裝指派給使用者。 終端使用者必須有 Apple Store 帳戶，才能安裝應用程式。

### <a name="synchronize-ebooks-from-apple-vpp-store----800878---"></a>從 Apple VPP Store 同步處理電子書 <!-- 800878 -->

您現在可以將從 Apple 大量採購程式市集購買的[書籍與 Intune 同步處理](../manage-apps/ios-vpp-apps.md)，然後將這些書籍指派給使用者。

### <a name="multi-user-management-for-samsung-knox-standard-devices----971988---"></a>Samsung KNOX Standard 裝置的多使用者管理 <!-- 971988 -->

Intune 的[多使用者管理](../enroll-devices/enroll-android-and-knox-standard-devices.md)現在支援執行 Samsung KNOX Standard 的裝置。 這表示終端使用者可以使用其 Azure Active Directory 認證登入和登出裝置，而且該裝置不論是否正在使用，都會集中管理。  當終端使用者登入時，他們可以存取應用程式，此外也可以將任何原則套用到這些應用程式。 當使用者登出時，會清除所有應用程式資料。

### <a name="additional-windows-device-restriction-settings----818566---"></a>其他 Windows 裝置限制設定 <!-- 818566 -->

我們新增了其他 [Windows 裝置限制設定](../configure-devices/device-restrictions-for-windows-10.md)的支援，例如額外的 Edge 瀏覽器支援、裝置鎖定畫面自訂、[開始] 功能表自訂、Windows 焦點搜尋集桌布，以及 Proxy 設定。

### <a name="multi-user-support-for-windows-10-creators-update----822547---"></a>Windows 10 Creators Update 的多使用者支援 <!-- 822547 -->

我們針對執行 Windows 10 Creators Update 並已加入 Azure Active Directory 網域的裝置，新增了[多使用者管理](../enroll-devices/enroll-windows-devices.md)的支援。 這表示當不同的標準使用者使用其 Azure AD 認證登入裝置時，將會收到指派給其使用者名稱的任何應用程式和原則。 針對安裝應用程式等自助式案例，使用者目前無法使用公司入口網站來進行。

### <a name="fresh-start-for-windows-10-pcs---1004830---"></a>Windows 10 電腦的 Fresh Start<!-- 1004830 -->

適用於 Windows 10 電腦的新[「全新開始」裝置動作](../manage-devices/what-is.md#available-device-actions)現在已經可以使用。  當您發出此動作時，將會移除任何安裝在電腦上的應用程式，而且電腦會自動更新為最新版的 Windows。 這可用來協助移除通常會隨新電腦提供之預先安裝的 OEM 應用程式。 您可以設定是否在發出此裝置動作時保留使用者資料。

### <a name="additional-windows-10-upgrade-paths----903672---"></a>其他 Windows 10 升級路徑 <!-- 903672 -->

您現在可以建立[版本升級原則，來將裝置升級為](../configure-devices/how-to-configure-windows-10-edition-upgrade.md)下列其他的 Windows 10 版本：

- Windows 10 Professional
- Windows 10 Professional N
- Windows 10 專業教育版
- Windows 10 專業教育版 N

### <a name="bulk-enroll-windows-10-devices----747607---"></a>大量註冊 Windows 10 裝置 <!-- 747607 -->

您現在可以使用 Windows 設定設計工具 (WCD) 將執行 Windows 10 Creators Update 的大量裝置加入到 Azure Active Directory 和 Intune。 若要為您的 Azure AD 租用戶啟用[大量 MDM 註冊](../enroll-devices/bulk-enroll-windows.md)，請使用 Windows 設定設計工具建立會將裝置加入到 Azure AD 租用戶的佈建套件，然後將套件套用至您要大量註冊及管理的公司擁有裝置。 將套件套用至裝置之後，裝置會加入 Azure AD、在 Intune 中註冊，並準備好供 Azure AD 使用者登入。  Azure AD 使用者是這些裝置上的標準使用者，並且會接收指派的原則和必要應用程式。 目前不支援自助式和公司入口網站案例。

### <a name="new-mam-settings-for-pin-and-managed-storage-locations----581122-736644---"></a>PIN 碼和受管理儲存位置的新 MAM 設定 <!-- 581122, 736644 -->

現在有兩個新的應用程式設定可協助您進行行動應用程式管理 (MAM) 案例：

- **在管理裝置 PIN 碼時停用應用程式 PIN 碼** - 偵測已註冊的裝置上是否有裝置 PIN 碼；如果有，則略過應用程式保護原則觸發的應用程式 PIN 碼。 這項設定可減少對在已註冊裝置上開啟啟用 MAM 的應用程式之使用者顯示的 PIN 提示次數。 這項功能適用於 Android 和 iOS。

- **選取要用於儲存公司資料的儲存體服務** - 可讓您指定要用於儲存公司資料的儲存位置。 使用者可以儲存至所選取的儲存位置服務，這表示將會封鎖未列出的其他所有儲存位置服務。

  支援的儲存位置服務清單：

  - OneDrive
  - 商務用 SharePoint Online
  - 本機儲存體

### <a name="help-desk-troubleshooting-portal----907448---"></a>服務台疑難排解入口網站 <!-- 907448 -->

新的[疑難排解入口網站](../manage-users/help-desk.md)可協助服務台操作員和 Intune 系統管理員檢視使用者及其裝置，並執行工作以解決 Intune 技術問題。

## <a name="march-2017"></a>2017 年 3 月

### <a name="support-for-ios-lost-mode---431695--"></a>支援 iOS 遺失模式 <!--431695-->

針對 iOS 9.3 和更新的裝置，Intune 新增**遺失模式**的支援。 您現在可以鎖定裝置以防止任何使用，並在裝置的鎖定畫面上顯示訊息和連絡電話號碼。

使用者將無法解除鎖定裝置，除非系統管理員停用「遺失模式」。 啟用「遺失模式」時，您可以使用 [尋找裝置] 動作在 Intune 主控台中的地圖上顯示裝置的地理位置。

裝置必須是透過 DEP 註冊之公司擁有的 iOS 裝置，且處於受監督模式。

如需詳細資訊，請參閱[什麼是 Microsoft Intune 裝置管理？](../manage-devices/what-is.md)

### <a name="improvements-to-device-actions-report---677150--"></a>裝置動作報告改善 <!--677150-->

我們改善了裝置動作報告以提升效能。 此外，您現在可以依狀態篩選報告。 例如，您可以篩選報告以僅顯示已完成的裝置動作。

### <a name="actions-for-non-compliance---730266--"></a>不符合規定時所採取的動作 <!--730266-->

**不符合規定時所採取的動作**是相容性原則的新功能，可讓您對不相容的裝置採取動作。 您可以指定單一或多個動作，並指定必須進行這些動作的時間週期。 例如，您可以在裝置變成不相容之後透過電子郵件立即通知使用者有不相容的裝置，也可以在 3 天寬限期之後透過條件式存取封鎖不相容的裝置存取公司資源。

### <a name="custom-app-categories---748805--"></a>自訂應用程式類別 <!--748805-->

您現在可以建立、編輯和指派您新增至 Intune 之應用程式的類別。 目前只能以英文指定類別。
請參閱[如何將應用程式新增至 Intune](../manage-apps/add-apps.md)。

### <a name="assign-lob-apps-to-users-with-unenrolled-devices---748823--"></a>指派 LOB 應用程式給使用未註冊裝置的使用者 <!--748823-->

您現在可以將市集中的企業營運應用程式指派給使用者，不論其裝置是否已向 Intune 註冊。 如果未向 Intune 註冊使用者裝置，則必須前往「公司入口網站」網站安裝它，而不是公司入口網站應用程式。

### <a name="new-compliance-reports---846671--"></a>新的合規性報告 <!--846671-->

您現在有可提供公司內裝置合規性狀態的合規性報告，並可以快速地針對使用者遇到的合規性相關問題進行疑難排解。 您可以檢視的資訊如下

- 整體的裝置合規性狀態
- 個別設定的合規性狀態
- 個別原則的合規性狀態

您也可以使用這些報告來向下鑽研個別裝置，以檢視影響該裝置的特定設定和原則。

<!--- You can now create an edition upgrade policy to upgrade devices to the following additional Windows 10 editions:

- Windows 10 Professional
- Windows 10 Professional N
- Windows 10 Professional Education
- Windows 10 Professional Education N --->

### <a name="direct-access-to-apple-enrollment-scenarios---951869--"></a>直接存取 Apple 註冊案例 <!--951869-->

對於在 2017 年 1 月之後建立的 Intune 帳戶，Intune 已經啟用使用 Azure Preview 入口網站中的「註冊裝置」工作負載直接存取 Apple 註冊案例。 Apple 註冊預覽原本只能從傳統 Intune 入口網站中的連結存取。 在 2017 年 1 月之前建立的 Intune 帳戶，將需要進行一次性移轉，才能在 Azure 中使用這些功能。 移轉的排程尚未宣布，但將會盡快提供詳細資料。 如果您現有的帳戶無法存取預覽，我們強烈建議您建立試用帳戶來測試新的體驗。


## <a name="february-2017"></a>2017 年 2 月

### <a name="ability-to-restrict-mobile-device-enrollment---747600-795782--"></a>限制行動裝置註冊的能力 <!--747600, 795782-->
Intune 正在新增新的註冊限制，以控制哪些行動裝置平台可以註冊。 Intune 將行動裝置平台分為 iOS、macOS、Android、Windows 和 Windows Mobile。

* 限制行動裝置註冊不會限制電腦用戶端註冊。  
* 僅限 iOS 與 Android，有一個額外選項可阻擋註冊個人擁有的裝置。

Intune 會將所有的新裝置標示為個人，除非 IT 系統管理員採取動作將它們標示為公司擁有，如[本文章](https://docs.microsoft.com/intune/deploy-use/manage-corporate-owned-devices)所說明。

### <a name="view-all-actions-on-managed-devices---677150--"></a>檢視受管理裝置上的所有動作 <!--677150-->
新的__裝置動作__報表會顯示曾執行遠端動作的人員，像是裝置恢復出廠預設值，並會另外顯示該動作的狀態。 請參閱[什麼是裝置管理？](https://docs.microsoft.com../manage-devices/what-is.md)。

### <a name="non-managed-devices-can-access-assigned-apps---664691--"></a>未受管理的裝置可以存取已指派的應用程式 <!--664691-->
iOS 和 Android 使用者能夠在他們未受管理的裝置上，安裝指派給他們的「無須註冊即可使用」應用程式，這屬於公司入口網站的設計變更。 使用 Intune 認證，使用者能夠登入公司入口網站，並查看指派給他們的應用程式清單。 「無須註冊即可使用」應用程式的應用程式套件，可透過公司入口網站下載取得。 這項變更不會影響需要註冊才能安裝的應用程式，因為如果使用者想要安裝這些應用程式，系統會提示他們註冊裝置。

### <a name="custom-app-categories---748805--"></a>自訂應用程式類別 <!--748805-->
您現在可以建立、編輯和指派您新增至 Intune 之應用程式的類別。 目前只能以英文指定類別。
請參閱[如何將應用程式新增至 Intune](../manage-apps/add-apps.md)。

### <a name="display-device-categories---814654--"></a>顯示裝置類別 <!--814654-->
裝置清單現在會以資料行顯示裝置類別。 您也可以在裝置內容刀鋒視窗的內容區段中編輯類別。 請參閱[如何將應用程式新增至 Intune](../manage-apps/add-apps.md)。

### <a name="configure-windows-update-for-business-settings---776716--"></a>設定商務用 Windows Update 的設定 <!--776716-->

「Windows 即服務」是一種為 Windows 10 提供更新的新做法。 從 Windows 10 開始，任何新的「功能更新」和「品質更新」都會包含所有先前的更新內容。 這表示只要您安裝了最新的更新，就能確定您的 Windows 10 裝置已完全更新至最新版。 不同於舊版 Windows，您現在必須安裝整個更新而不是部分更新。

使用商務用 Windows Update，可以簡化更新管理體驗，因此您不需要核准裝置群組的個別更新。 只要設定更新首度發行策略，您還是可以管理環境中的風險，Windows Update 會確保在適當的時間安裝更新。 Microsoft Intune 可讓您在裝置上設定更新設定，並可讓您延後更新的安裝。 Intune 不會儲存更新，只會儲存更新原則指派。 裝置直接存取 Windows Update 進行更新。使用 Intune 設定及管理 **Windows 10 更新響鈴**。 更新響鈴是一組包含何時及如何安裝 Windows 10 更新的設定。 如需詳細資訊，請參閱[設定商務用 Windows Update 的設定](../configure-devices/how-to-configure-windows-update-for-business.md)。

## <a name="january-2017"></a>2017 年 1 月

### <a name="assign-line-of-business-apps-whether-or-not-devices-are-enrolled---748823--"></a>不論是否註冊裝置都指派企業營運應用程式 <!--748823-->
您現在可以將市集中的企業營運和應用程式指派給不論是否向 Intune 註冊其裝置的使用者。 如果未向 Intune 註冊使用者裝置，則他們必須前往公司入口網站安裝它，而不是公司入口網站應用程式。 請參閱[什麼是應用程式管理](../manage-apps/what-is-app-management.md)。

### <a name="resolve-issue-where-ios-devices-are-inactive-or-the-admin-console-cannot-communicate-with-them"></a>解決 iOS 裝置處於非使用狀態或管理員主控台無法與它們通訊的問題
當使用者的裝置與 Intune 失去連絡時，您可以提供新的疑難排解步驟，協助他們重新取得公司資源的存取權。 請參閱[裝置處於非使用狀態或管理員主控台無法與它們通訊](../enroll-devices/troubleshoot-device-enrollment.md#devices-are-inactive-or-the-admin-console-cannot-communicate-with-them)。

## <a name="december-2016-initial-release"></a>2016 年 12 月 (初版)

### <a name="telecom-expense-management-integration-in-public-preview-of-azure-portal--747605--"></a>Azure 入口網站公開預覽中的電信費用管理整合<!--747605-->
我們現在將開始在 Azure 入口網站中預覽與協力廠商電信費用管理 (Telecom Expense Management，TEM) 服務的整合。 您可以使用 Intune 強制執行限制國內和漫遊資料使用量。 我們將開始與 [Saaswedo](http://www.saaswedo.com) 進行這些整合。 若要在您的試用租用戶中啟用此功能，請[連絡 Microsoft 支援服務](https://docs.microsoft.com/intune/troubleshoot/how-to-get-support-for-microsoft-intune)。

- 將市集應用程式部署到 iOS、 Android 及 Windows 裝置並加以管理
- 將企業營運 (LOB) 應用程式部署到 iOS、 Android 及 Windows 裝置並加以管理
- 將大量採購的應用程式部署到 iOS、 Android 及 Windows 裝置並加以管理
- 將 Web 應用程式部署到 iOS、 Android 及 Windows 裝置並加以管理
- 受管理之 iOS 應用程式組態設定檔
- 設定應用程式保護原則，並將企業營運應用程式部署到未向 Intune 註冊的裝置
- VPN 設定檔、個別應用程式 VPN、Wi-Fi、電子郵件及憑證設定檔
- 合規性政策
- Azure AD 的條件式存取
- 對內部部署 Exchange 的條件式存取
- 裝置註冊
- 以角色為基礎的存取控制

## <a name="deprecated-features-in-the-azure-portal"></a>Azure 入口網站中標示即將淘汰的功能

### <a name="support-for-row-by-row-review-of-hardware-identifiers"></a>逐列檢閱硬體識別碼的支援
對於 IMEI 號碼及 Apple 序號，Azure 入口網站逐列檢閱硬體識別碼。 在傳統 Intune 主控台中，您可以匯入逗點分隔值 (.csv) 檔案中的詳細資料來覆寫現有個別硬體識別碼的詳細資料。 Azure 入口網站提供一個精簡選項，會自動覆寫所有的硬體識別碼的詳細資料，或忽略現有識別碼的新詳細資料。

#### <a name="how-this-affects-you"></a>此功能對您的影響
在 Azure 入口網站中，您無法逐列決定要更新的國際行動設備識別碼 (IMEI) 裝置。 傳統 Intune 主控台會繼續支援此功能。

#### <a name="how-to-get-ready-for-this-change"></a>此變更需要哪些準備
事先提出此變更資訊的目的在讓您的水援系統管理員知道這項變更。 這項變更會在移轉到 Azure 入口網站時一併實施，預定時間在 2017 年上半年。


### <a name="support-for-default-corporate-device-enrollment-profiles-in-apple-dep"></a>Apple DEP 中的預設公司裝置註冊設定檔支援
Azure 入口網站不支援 Apple 裝置註冊程式 (DEP) 裝置序號的「預設」公司裝置註冊設定檔。 傳統 Intune 主控台支援此功能，但即將中止，以避免不慎指派這類設定檔。 在 Azure 入口網站中，從 Apple DEP 帳戶同步而步而來的序號一開始並沒有任何公司裝置註冊設定檔指派。

#### <a name="how-this-affects-you"></a>此功能對您的影響
在 Azure 入口網站中，您將無法再設定適用於所有 Apple 裝置的預設設定檔原則。 傳統 Intune 主控台會繼續支援此功能。

#### <a name="how-to-get-ready-for-this-change"></a>此變更需要哪些準備
事先提出此變更資訊的目的在讓您的水援系統管理員知道這項變更。 這項變更會在移轉到 Azure 入口網站時一併實施，預定時間在 2017 年上半年。


## <a name="march-2017"></a>2017 年 3 月

### <a name="new-capabilities"></a>新功能

#### <a name="support-for-skycure"></a>支援 Skycure

您現在可以根據由 Skycure (一個與 Microsoft Intune 整合的行動威脅防禦解決方案) 所進行的風險評估，使用條件式存取來控制行動裝置對公司資源的存取。 風險評估是根據收集自執行 Skycure 裝置的遙測，包括︰

- 實體防禦
- 網路防禦
- 應用程式防禦
- 弱點防禦

您可以根據透過 Intune 裝置合規性政策所啟用的 Skycure 風險評估，來設定 EMS 條件式存取原則。 您可以根據偵測到的威脅，使用這些原則來允許或封鎖不符合規範的裝置存取公司資源。 如需詳細資訊，請參閱 [Skycure Mobile Threat Defense 連接器](/intune/deploy-use/skycure-mobile-threat-defense-connector)。

#### <a name="new-user-experience-for-the-company-portal-app-for-android---621622--"></a>Android 版公司入口網站應用程式的新使用者體驗 <!--621622-->

Android 版公司入口網站應用程式將會更新其使用者介面，以提供更現代化的外觀和操作，以及更佳的使用者體驗。 值得注意的更新如下︰

- 色彩：公司入口網站索引標籤標頭會以 IT 定義的品牌上色。
- 應用程式：在 [應用程式] 索引標籤中，已更新 [熱門應用程式] 和 [所有應用程式] 按鈕。
- 搜尋：在 [應用程式] 索引標籤中，[搜尋] 按鈕是浮動的動作按鈕。
- 瀏覽應用程式：[所有應用程式] 檢視會以索引標籤式的檢視顯示 [熱門]、[所有] 與 [類別]，以更方便瀏覽。
- 支援：已更新 [我的裝置] 和 [連絡 IT] 索引標籤以提高可讀性。

如需有關這些變更的詳細資訊，請參閱 [Intune 使用者應用程式的 UI 更新](/intune/whats-new/whats-new-in-intune-app-ui)。

#### <a name="non-managed-devices-can-access-assigned-apps---664691--"></a>未受管理的裝置可以存取已指派的應用程式 <!--664691-->

iOS 和 Android 使用者能夠在他們未受管理的裝置上，安裝指派給他們的「無須註冊即可使用」應用程式，這屬於公司入口網站的設計變更。 使用 Intune 認證，使用者能夠登入公司入口網站，並查看指派給他們的應用程式清單。 「無須註冊即可使用」應用程式的應用程式套件，可透過公司入口網站下載取得。 這項變更不會影響需要註冊才能安裝的應用程式，因為如果使用者想要安裝這些應用程式，系統會提示他們註冊裝置。

#### <a name="signing-script-for-windows-10-company-portal---941642--"></a>Windows 10 公司入口網站的簽署指令碼 <!--941642-->

如果您需要下載和側載「Windows 10 公司入口網站」應用程式，您現在可以使用指令碼為您的組織簡化及加速應用程式簽署程序。   若需要下載指令碼及其使用指示，請參閱 TechNet 資源庫上 [Windows 10 公司入口網站專用的 Microsoft Intune 簽署指令碼](https://aka.ms/win10cpscript)。 如需本公告的詳細資訊，請參閱 Intune 支援小組部落格上的[更新您的 Windows 10 公司入口網站應用程式](https://blogs.technet.microsoft.com/intunesupport/2017/03/13/updating-your-windows-10-company-portal-app/)。


### <a name="notices"></a>通知

#### <a name="support-for-ios-103"></a>支援 iOS 10.3

iOS 10.3 版在 2017 年 3 月 27 日開始向 iOS 使用者推出。 所有現有的 Intune MDM 與 MAM 案例都與最新版本的 Apple OS 相容。 當使用者將裝置和應用程式升級到 iOS 10.3 時，我們預期所有目前可用來管理 iOS 裝置的 Intune 功能將可繼續運作。

目前沒有任何已知問題可分享。 如果您在使用 iOS 10.3 時發生任何問題，歡迎連絡 [Intune 支援小組](/intune/troubleshoot/contact-assisted-phone-support-for-microsoft-intune)。

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
公司入口網站會支援以沒有受管理裝置的使用者為目標的應用程式。 網站會與其他 Microsoft 產品和服務一致，方法是使用新的對比色彩配置、動態圖例和「漢堡功能表」：![公司入口網站左上角新增的漢堡功能表小型影像](/intune/whats-new/media/CP_hamburger_menu.png)，其包含技術服務連絡人詳細資料以及現有受管理裝置的相關資訊。 登陸頁面將會予以重新排列，以透過 [精選和最近更新] 應用程式的浮動切換來強調使用者可用的應用程式。 您可以在 [UI updates for Intune end user apps](/intune/whats-new/whats-new-in-intune-app-ui) (Intune 使用者應用程式的 UI 更新) 頁面上找到更新前後的影像。

### <a name="notices"></a>通知

#### <a name="group-migration-will-not-require-any-updates-to-groups-or-policies-for-ios-devices---898837--"></a>群組移轉不需要 iOS 裝置群組或原則的任何更新 <!--898837-->
每個公司裝置註冊設定檔預先指派的 Intune 裝置群組，在移轉到 Azure Active Directory 裝置群組期間，都會根據公司裝置註冊設定檔的名稱，在 AAD 中建立對應的動態裝置群組。 這可確保在裝置註冊時，它們會自動分組，並與原始 Intune 群組收到相同的原則和應用程式。

一旦租用戶進入分組和鎖定目標的移轉程序，Intune 就會自動建立動態的 AAD 群組，以對應公司裝置註冊設定檔鎖定的 Intune 群組。 如果 Intune 管理員刪除了鎖定的 Intune 群組，就不會刪除對應的動態 AAD 群組。 群組成員和動態查詢會予以清除，但群組本身會一直保留到 IT 管理員透過 AAD 入口網站移除它。

同樣地，如果 IT 管理員變更公司裝置註冊設定檔鎖定的 Intune 群組，Intune 就會建立新的動態群組，反映新的設定檔指派，但不會移除舊指派建立的動態群組。

### <a name="defaulting-to-managing-windows-desktop-devices-through-windows-settings---663050--"></a>預設為透過 Windows 設定管理 Windows Desktop 裝置 <!--663050-->
註冊 Windows 10 Desktop 的預設行為會變更。 新的註冊將會遵循一般 MDM 代理程式註冊流程，而不是透過電腦代理程式。 公司入口網站會提供 Windows 10 Desktop 使用者，有關引導他們新增 Windows 10 Desktop 電腦作為行動裝置之程序的註冊指示。 這不會影響目前已註冊的電腦，而且您的組織還是可以使用電腦代理程式來管理 Windows 10 Desktop，如[設定 Windows 裝置管理](/intune/deploy-use/set-up-windows-device-management-with-microsoft-intune)中所述。

#### <a name="improving-mobile-app-management-support-for-selective-wipe---581242--"></a>改善選擇性抹除的行動應用程式管理支援 <!--581242-->
如果因 [離線間隔幾天後抹除 App 資料] 原則而自動移除工作或學校資料，則會將如何重新存取工作或學校資料的其他指引授與終端使用者。<!--, or the removal of the Intune Company Portal on Android.-->

#### <a name="company-portal-for-ios-links-open-inside-the-app---665954--"></a>適用於 iOS 的公司入口網站連結會在應用程式內開啟 <!--665954-->
適用於 iOS 的公司入口網站應用程式連結 (包括文件和應用程式的連結) 會使用 Safari 的應用程式內檢視直接在公司入口網站應用程式中開啟。 這項更新將在 1 月與服務更新分開提供。

#### <a name="new-mdm-server-address-for-windows-devices---893007--"></a>Windows 裝置的新 MDM 伺服器位址 <!--893007-->
如果 Windows 和 Windows Phone 使用者輸入 __manage.microsoft.com__ 作為 MDM 伺服器位址 (系統提示時)，其嘗試註冊裝置會失敗。 MDM 伺服器位址已從 __manage.microsoft.com__ 變更為 __enrollment.manage.microsoft.com__。 請通知您的使用者，如果在註冊 Windows 或 Windows Phone 裝置時收到提示，請使用 __enrollment.manage.microsoft.com__ 作為 MDM 伺服器位址。 不需要變更您的 CNAME 設定。 如需此變更的其他資訊，請前往 [aka.ms/intuneenrollsvrchange](https://aka.ms/intuneenrollsvrchange)。

#### <a name="new-user-experience-for-the-company-portal-app-for-android---621622--"></a>Android 版公司入口網站應用程式的新使用者體驗 <!--621622-->
從 3 月起，Android 版公司入口網站應用程式會遵循[素材設計方針](https://material.io/guidelines/material-design/introduction.html)建立更現代化的外觀與風格。 此改善的使用者體驗包括︰

* __色彩__︰索引標籤標頭可根據您的自訂調色盤上色。
* __介面__︰[應用程式] 索引標籤已更新 [精選 App] 和 [所有應用程式] 按鈕。 [搜尋] 按鈕現在是浮動的動作按鈕。
* __瀏覽__︰所有應用程式都會以索引標籤式的檢視顯示 [精選]、[所有] 與 [類別] 以方便瀏覽。
* __服務__︰[我的裝置] 和 [連絡 IT] 索引標籤皆已改善可讀性。

您可以在 [UI updates for Intune end user apps](/intune/whats-new/whats-new-in-intune-app-ui) (Intune 終端使用者應用程式的 UI 更新) 頁面上找到更新前後的影像。

### <a name="associate-multiple-management-tools-with-the-windows-store-for-business---926135--"></a>商務用 Windows 市集的相關多重管理工具 <!--926135-->
如果您使用多種管理工具來部署商務用 Windows 市集應用程式，以前只能建立其中一種與商務用 Windows 市集的關聯性。 現在可以建立多種管理工具與市集的關聯性，例如，Intune 和 Configuration Manager。 如需詳細資料，請參閱[以 Microsoft Intune 管理購自商務用 Windows 市集的應用程式](/intune/deploy-use/manage-apps-you-purchased-from-the-windows-store-for-business-with-microsoft-intune#associate-your-windows-store-for-business-account-with-intune)。

## <a name="whats-new-in-the-public-preview-of-the-intune-admin-experience-on-azure---736542--"></a>Azure 的 Intune 管理體驗公開預覽新功能<!--736542-->

在 2017 年初，我們會將完整管理體驗移轉到 Azure，以便在可透過圖形 API 擴充的新式服務平台上，對核心 EMS 工作流程進行強大的整合式管理。

新的試用租用戶將於本月開始看到 Azure 入口網站中新管理體驗的公開預覽。 在預覽狀態期間，將透過現有的 Intune 主控台反覆提供功能和同位檢查。

Azure 入口網站中的管理體驗將使用已宣佈的新群組和目標設定功能；當您現有的租用戶移轉至新的群組體驗時，也會同時將您移轉，以預覽您租用戶的新管理體驗。 在此同時，如果您想要在移轉租用戶之前測試或查看任何新功能，請註冊新的 Intune 試用帳戶或查看[新文件](/intune-azure/introduction/whats-new)。

您可以在[這裡](/intune-azure/introduction/whats-new)找到 Azure 的 Intune 預覽新功能。

## <a name="january-2017"></a>2017 年 1 月

### <a name="new-capabilities"></a>新功能

#### <a name="in-console-reports-for-mam-without-enrollment---677961--"></a>無裝置註冊之 MAM 的主控台內報表 <!--677961-->
已註冊的裝置和未註冊的裝置已新增新的應用程式保護報表。 在這裡深入了解如何[使用 Microsoft Intune 監視行動應用程式管理原則](/intune/deploy-use/monitor-mobile-app-management-policies-with-microsoft-intune)。

#### <a name="android-711-support---694397--"></a>Android 7.1.1 支援 <!--694397-->
Intune 現在完全支援和管理 Android 7.1.1。

#### <a name="resolve-issue-where-ios-devices-are-inactive-or-the-admin-console-cannot-communicate-with-them---unknown--"></a>解決 iOS 裝置處於非使用狀態或管理員主控台無法與它們通訊的問題 <!--unknown-->
當使用者的裝置與 Intune 失去連絡時，您可以提供新的疑難排解步驟，協助他們重新取得公司資源的存取權。 請參閱[裝置處於非使用狀態或管理員主控台無法與它們通訊](/intune/troubleshoot/troubleshoot-device-enrollment-in-intune#devices-are-inactive-or-the-admin-console-cannot-communicate-with-them)。

### <a name="notices"></a>通知

#### <a name="defaulting-to-managing-windows-desktop-devices-through-windows-settings---663050--"></a>預設為透過 Windows 設定管理 Windows Desktop 裝置 <!--663050-->
註冊 Windows 10 Desktop 的預設行為會變更。 新的註冊將會遵循一般 MDM 代理程式註冊流程，而不是透過電腦代理程式。

公司入口網站會提供 Windows 10 Desktop 使用者，有關引導他們新增 Windows 10 Desktop 電腦作為行動裝置之程序的註冊指示。 這不會影響目前已註冊的電腦，而且您的組織還是可以使用電腦代理程式來管理 Windows 10 Desktop，如[設定 Windows 裝置管理](/intune/deploy-use/set-up-windows-device-management-with-microsoft-intune)中所述。

#### <a name="improving-mobile-app-management-support-for-selective-wipe---581242--"></a>改善選擇性抹除的行動應用程式管理支援 <!--581242-->
如果因 [離線間隔幾天後抹除 App 資料] 原則而自動移除工作或學校資料，則會將如何重新存取工作或學校資料的其他指引授與終端使用者。<!--, or the removal of the Intune Company Portal on Android.-->

#### <a name="company-portal-for-ios-links-open-inside-the-app---665954--"></a>適用於 iOS 的公司入口網站連結會在應用程式內開啟 <!--665954-->
適用於 iOS 的公司入口網站應用程式連結 (包括文件和應用程式的連結) 會使用 Safari 的應用程式內檢視直接在公司入口網站應用程式中開啟。 這項更新將在 1 月與服務更新分開提供。

#### <a name="modernizing-the-company-portal-website---753980--"></a>現代化公司入口網站 <!--753980-->
從 2 月開始，公司入口網站將支援以沒有受管理裝置的使用者為目標的應用程式。 網站會與其他 Microsoft 產品和服務一致，方法是使用新的對比色彩配置、動態圖例和「漢堡功能表」：![公司入口網站漢堡功能表](/intune/whats-new/media/CP_hamburger_menu.png)，其包含技術服務連絡人詳細資料以及現有受管理裝置的相關資訊。 登陸頁面將會予以重新排列，以透過 [精選和最近更新] 應用程式的浮動切換來強調使用者可用的應用程式。 您可以在 [What's new in the Company Portal UI page](/intune/whats-new/whats-new-in-intune-app-ui) (公司入口網站 UI 頁面的新功能) 上找到新版與舊版的映像。

#### <a name="new-documentation-for-app-protection-policies---583398--"></a>應用程式保護原則的新文件 <!--583398-->
針對想要使用 Intune App Wrapping Tool 或 Intune App SDK 在 iOS 和 Android 應用程式中啟用應用程式保護原則 (稱為 MAM 原則) 的系統管理員和應用程式開發人員，我們已更新他們適用的文件。

已更新下列文章：

* [決定如何準備應用程式，以使用 Microsoft Intune 管理行動裝置應用程式](/intune/deploy-use/decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune)
* [準備將 iOS 應用程式交由 Intune App Wrapping Tool 進行行動應用程式管理](/intune/deploy-use/prepare-ios-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool)
* [開始使用 Microsoft Intune App SDK](/intune/develop/intune-app-sdk-get-started)
* [Intune App SDK for iOS 開發人員指南](/intune/develop/intune-app-sdk-ios)

下列文章是文件庫的新增項目︰

* [Intune App SDK Cordova 外掛程式](/intune/develop/intune-app-sdk-cordova)
* [Intune App SDK Xamarin 元件](/intune/develop/intune-app-sdk-xamarin)

#### <a name="progress-bar-when-launching-the-company-portal-on-ios---665978--"></a>在 iOS 上啟動公司入口網站時的進度列 <!--665978-->
適用於 iOS 的公司入口網站會在啟動畫面上引進進度列，以將所發生之載入程序的相關資訊提供給使用者。 將會有進度列的階段性推出，來取代微調按鈕。 這表示部分使用者將會看到新的進度列，而其他人則會持續看見微調按鈕。

## <a name="december-2016"></a>2016 年 12 月

### <a name="public-preview-of-the-new-intune-admin-experience-on-azure---736542--"></a>Azure 上新 Intune 管理體驗的公開預覽 <!--736542-->
在 2017 年初，我們會將完整管理體驗移轉到 Azure，以便在可透過圖形 API 擴充的新式服務平台上，對核心 EMS 工作流程進行強大的整合式管理。 在將此入口網站的正式運作版本提供給所有 Intune 租用戶之前，我們很高興地宣布在本月稍晚將會推出這個新管理體驗的預覽給特定租用戶。

Azure 入口網站中的管理體驗將使用已宣佈的新群組和目標設定功能；當您現有的租用戶移轉至新的群組體驗時，也會同時將您移轉，以預覽您租用戶的新管理體驗。 在此同時，請在我們的[新文件](/intune-azure/introduction/what-is-microsoft-intune)中深入了解我們在 Azure 入口網站中針對 Microsoft Intune 做了哪些準備。

__Azure 入口網站的電信費用管理整合公開預覽__ <!--747605--> 我們現在將開始在 Azure 入口網站中預覽與第三方電信費用管理 (TEM) 服務的整合。 您可以使用 Intune 強制執行限制國內和漫遊資料使用量。 我們將開始與 [Saaswedo](http://www.saaswedo.com) 進行這些整合。 若要在您的試用版租用戶中啟用此功能，請[連絡 Microsoft 支援服務](/intune/troubleshoot/how-to-get-support-for-microsoft-intune)。

### <a name="new-capabilities"></a>新功能

__跨所有平台的 Multi-Factor Authentication__ <!--747590--> 您現在可以在一組選取的使用者從 Azure 管理入口網站註冊 iOS、Android、Windows 8.1+ 或 Windows Phone 8.1+ 裝置時，對這些使用者強制執行 Multi-Factor Authentication (MFA)，方法是在 Azure Active Directory 中設定 Microsoft Intune 註冊應用程式的相關 MFA。

__限制行動裝置註冊的能力__ <!--747596--> Intune 正在新增新的註冊限制，以控制哪些行動裝置平台可以註冊。 Intune 將行動裝置平台分為 iOS、macOS、Android、Windows 和 Windows Mobile。
* 限制行動裝置註冊不會限制電腦用戶端註冊。
* 有一個僅適用於之iOS 的額外選項可封鎖個人擁有的裝置註冊。

Intune 會將所有的新裝置標示為個人，除非 IT 系統管理員採取動作將它們標示為公司擁有，如[本文章](/intune/deploy-use/manage-corporate-owned-devices)所說明。

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

__可供 Windows 10 裝置使用的新 Microsoft Intune 公司入口網站__ Microsoft 已經發行 [Windows 10 裝置適用的新 Microsoft Intune 公司入口網站應用程式](https://www.microsoft.com/store/apps/9wzdncrfj3pz)。 利用新的 Windows 10 通用格式的此應用程式，會為使用者提供應用程式內更新的使用者體驗，以及所有 Windows 10 裝置、電腦和類似行動裝置的相同體驗，同時啟用他們目前仍在使用的相同功能。

新的應用程式也可讓使用者運用其他平台功能，例如單一登入 (SSO) 和 Windows 10 裝置上的憑證型驗證。 應用程式會以現有的 Windows 8.1 公司入口網站升級，以及從 Windows 市集安裝的 Windows Phone 8.1 公司入口網站的方式提供。 如需詳細資訊，請前往 [aka.ms/intunecp_universalapp](http://aka.ms/intunecp_universalapp)。

> [!IMPORTANT]
> __在 Intune 和 Android for Work 上的更新__ 雖然您可以用__必要__動作部署 Android for Work 應用程式，但如果您已將 Intune 群組移轉至新的 Azure AD 群組，就只能將應用程式部署為__可用__。

__Intune App SDK for Cordova 外掛程式現在支援 MAM 而不需註冊__ 應用程式開發人員可以現在使用 Intune App SDK for Cordova 外掛程式啟用 MAM 功能，而不必在其 Android 和 iOS 的 Cordova 應用程式進行裝置註冊。 您可以在[這裡](https://github.com/msintuneappsdk/cordova-plugin-ms-intune-mam)找到 Intune App SDK for Cordova 外掛程式。

__Intune App SDK Xamarin 元件現在支援 MAM 而不需註冊__ 應用程式開發人員可以現在使用 Intune App SDK Xamarin 元件啟用 MAM 功能，而不必在其 Android 和 iOS 的 Xamarin 應用程式進行裝置註冊。 您可以在[這裡](https://github.com/msintuneappsdk/intune-app-sdk-xamarin)找到 Intune App SDK Xamarin 元件。

### <a name="notices"></a>通知

__Symantec 簽署憑證不再需要已簽署的 Windows Phone 8 公司入口網站以進行上傳__ 上傳 Symantec 簽署憑證不再需要已簽署的 Windows Phone 8 公司入口網站應用程式。 可以獨立上傳憑證。

###<a name="deprecations"></a>棄用功能

__Windows Phone 8 公司入口網站的支援__ 對 Windows Phone 8 公司入口網站的支援現在將被取代。 對於 Windows Phone 8 和 WinRT 平台的支援已在 2016 年 10 月被取代。 對於 Windows 8 公司入口網站的支援也已在 2016 年 10 月被取代。

## <a name="october-2016"></a>2016 年 10 月

### <a name="conditional-access-for-mobile-application-management"></a>行動應用程式管理的條件式存取
您將可以限制 Exchange Online 的存取，讓存取只能來自支援 Intune 行動應用程式管理原則的應用程式，例如 Outlook。 [這項新功能](/intune/deploy-use/allow-policy-managed-apps-access-to-o365)可完美對應 Intune 行動應用程式管理 (MAM) 原則，讓您可以封鎖存取內建電子郵件用戶端或並未使用 Intune MAM 原則設定的其他應用程式。 這可確保您的使用者是利用使用 Intune MAM 保護的 App 來存取組織的資料。 您可以透過 Azure 入口網站，從 Intune 行動應用程式管理開始。 尋找 [設定] 刀鋒視窗中新的 [條件式存取] 區段。

### <a name="conditional-access-for-windows-pcs"></a>Windows 電腦的條件式存取
您現在可以透過 Intune 管理主控台建立條件式存取原則，來封鎖 Windows 電腦存取 [Exchange Online](/intune/deploy-use/restrict-access-to-exchange-online-with-microsoft-intune) 和 [SharePoint Online](/intune/deploy-use/restrict-access-to-sharepoint-online-with-microsoft-intune)。 您也可以建立條件式存取原則來封鎖存取 Office 桌面及通用應用程式。

### <a name="android-for-work-support"></a>Android for Work 支援

> [!IMPORTANT]

> 雖然您可以用__必要__動作部署 Android for Work 應用程式，但如果您已將 Intune 群組移轉至新的 Azure AD 群組，就只能將應用程式部署為__可用__。

Intune 現在已是 Android for Work (AfW) 方案中的一部分。 我們將從這個月開始到未來幾個月中，陸續推出 AfW 功能的支援。 請注意，所提供的 AfW 應用程式部署採用新的分組與目標設定功能。 當新佈建的 Intune 服務帳戶可以使用 AfW 時，也隨之能夠使用此功能。

[請參閱 Microsoft 有關 Android for Work 之 Intune 支援的公告](https://blogs.technet.microsoft.com/enterprisemobility/2016/09/12/microsoft-intune-support-for-android-for-work/)。

下列 Intune 主題是全新主題，或更新的 Android for Work 資訊：

IT 專業人員：
- [設定 Android for Work](/intune/deploy-use/set-up-android-for-work)
- [使用 Intune 限制電子郵件存取 Exchange Online 及新版的 Exchange Online Dedicated](/intune/deploy-use/restrict-access-to-exchange-online-with-microsoft-intune)
- [使用 Intune 限制電子郵件存取 Exchange 內部部署及舊版的 Exchange Online Dedicated](/intune/deploy-use/restrict-access-to-exchange-onpremises-with-microsoft-intune)
- [Android for Work 的相容性原則設定](/intune/deploy-use/afw-compliance-policy-settings-in-microsoft-intune)
- [如何部署 Android for Work 應用程式](/intune/deploy-use/android-for-work-apps)
- [設定Android for Work 應用程式套用行動裝置應用程式設定原則 ](/intune/deploy-use/afw-app-configuration-policy)
- [Android for Work 原則設定](/intune/deploy-use/android-for-work-policy-settings-in-microsoft-intune)

使用者：
- [當您建立工作設定檔時會如何](/intune/enduser/what-happens-when-you-create-a-work-profile-android)
- [建立工作設定檔並向 Intune 註冊您的裝置](/intune/enduser/create-a-work-profile-and-enroll-your-device-in-intune-android)

### <a name="lookout-integration-to-protect-ios-devices"></a>Lookout 整合以保護 iOS 裝置
在十月，Microsoft 要整合 Lookout 的行動威脅保護解決方案，藉由偵測裝置上的惡意程式碼、高風險 App 等等，以保護 iOS 行動裝置。 Lookout 的解決方案有助於您判斷威脅層級 (可設定)。 您可以根據 Lookout 的風險評估，在 Intune 中建立相容性原則規則，來決定裝置相容性。 您可以利用條件式存取原則，根據裝置相容性狀態，允許或封鎖公司資源的存取。

系統將會提示不相容 iOS 裝置的使用者進行註冊，並且要求使用者在其裝置上安裝 Lookout for Work 應用程式、啟動應用程式，並修復 Lookout for Work 應用程式中所報告的威脅，才能存取公司資料。 了解如何[設定及部署 Lookout for Work 應用程式](/intune/deploy-use/configure-and-deploy-lookout-for-work-apps)。
<!--TFS 1319493-->

### <a name="intune-app-wrapping-tool-for-android"></a>Intune App Wrapping Tool for Android
您可以使用 Intune App Wrapping Tool，讓應用程式使用 Intune 行動應用程式管理 (MAM) 原則。 現在不需要註冊裝置，即可支援 Intune MAM 原則。

### <a name="manage-printing-from-apps-managed-using-mam-policies"></a>從使用 MAM 原則管理的應用程式管理列印
您現在可以防止有 MAM 原則的應用程式列印公司資料。 此設定可於 [Azure 入口網站](/Intune/deploy-use/create-and-deploy-mobile-app-management-policies-with-microsoft-intune)取得，而且 [iOS](/Intune/deploy-use/ios-mam-policy-settings) 和 [Android](/Intune/deploy-use/android-mam-policy-settings) 裝置都支援。
<!--TFS 1014328-->

### <a name="support-for-fingerprints-on-android-devices"></a>Android 裝置的指紋支援
Android 行動裝置應用程式管理 (MAM) 原則現在已可讓使用者使用其指紋存取應用程式，而無須輸入PIN 碼。 請參閱本文及其他 [Android 行動裝置應用程式管理原則設定](/Intune/deploy-use/android-mam-policy-settings)。

### <a name="notices"></a>通知

__Android Samsung KNOX 與 Intune 的相容性__：某些 Samsung Galaxy Ace 手機型號，Intune 無法作為 Samsung KNOX 裝置管理。 當您向 Intune 註冊這些裝置時，它們會作為標準的 Android 裝置管理。

受影響的型號︰

* SM-G313HU
* SM-G313HY
* SM-G313M
* SM-G313MY
* SM-G313U

您和您的使用者不需要採取任何進一步的動作。 如需詳細資訊，請瀏覽 [Samsung KNOX](https://www.samsungknox.com) 網站。

__Windows 8 的公司入口網站應用程式已被取代，Windows Phone 8 和 Windows RT 平台的支援也即將被取代__：自 2016 年 10 月開始，Windows 8 公司入口網站的支援會換成 Microsoft Intune。 Microsoft Intune 也會取代 Windows Phone 8 和 Windows RT 平台的支援。 因此，您將無法註冊或更新任何 Windows Phone 8 或 Windows RT 裝置。

您可以繼續管理已註冊的 Windows Phone 8、Windows RT 和 Windows 8 裝置。 將 Windows Phone 8 和 Windows 8 裝置更新為 Windows 8.1 和 Windows Phone 8.1，並使用對應的 Windows 8.1 和 Windows Phone 8.1 公司入口網站應用程式繼續將應用程式發佈至這些裝置，而不受中斷。

我們從 2016 年 11 月開始淘汰對 Windows Phone 8 公司入口網站的支援。
<!--TFS 1255391-->

### <a name="whats-coming"></a>未來動態

__Windows 10 裝置可以使用新的 Microsoft Intune 公司入口網站__：Microsoft 即將發行新的 Windows 10 裝置 Microsoft Intune 公司入口網站。 利用新的 Windows 10 通用格式的此應用程式，會為使用者提供應用程式內更新的使用者體驗，以及所有 Windows 10 裝置、電腦和類似行動裝置的相同體驗，同時啟用他們目前仍在使用的相同功能。

新的應用程式也可讓使用者運用其他平台功能，例如單一登入 (SSO) 和 Windows 10 裝置上的憑證型驗證。 應用程式會以現有的 Windows 8.1 公司入口網站升級，以及從 Windows 市集安裝的 Windows Phone 8.1 公司入口網站的方式提供。 如需詳細資訊，請前往 [aka.ms/intunecp_universalapp](http://aka.ms/intunecp_universalapp)。
<!--TFS 1016502-->

## <a name="september-2016"></a>2016 年 9 月
### <a name="new-features-announcements-and-information"></a>新功能、宣告和資訊
* [Windows 條件式存取](#windows-conditional-access)
* [iOS 10 支援](#ios-10-support)
* [App Wrapping Tool 支援 MAM，不需要 Android 和 iOS 裝置註冊](#app-wrapping-tool-supports-mam-without-device-enrollment-for-android-and-ios)
* [Intune 群組在 9 月會開始轉換到 Azure Active Directory](#intune-groups-begin-transitioning-to-azure-active-directory-in-september)
* [Lookout 整合以保護 Android 裝置](#lookout-integration-to-protect-android-devices)
* [適用於 Android、iOS 和 Windows 的公司入口網站更新](#company-portal-updates)
* [Intune 字彙](#intune-glossary)
* [未來動態](#whats-coming)

### <a name="windows-conditional-access"></a>Windows 條件式存取
您現在可以透過 Intune 管理主控台建立條件式存取原則，來封鎖 Windows 電腦存取 Exchange Online 和 SharePoint Online。 您也可以建立條件式存取原則來封鎖存取 Office 桌面及通用應用程式。

### <a name="ios-10-support"></a>iOS 10 支援
現有的 Intune MDM 與 MAM 案例與 iOS 10 相容。 如需秘訣，請參閱 [Intune 支援小組部落格](https://blogs.technet.microsoft.com/intunesupport/2016/09/13/support-tip-intune-support-for-ios-10/)。

### <a name="app-wrapping-tool-supports-mam-without-device-enrollment-for-android-and-ios"></a>App Wrapping Tool 支援 MAM，不需要 Android 和 iOS 裝置註冊
Intune App Wrapping Tool 是命令列工具，用於在 iOS 和 Android 的企業營運 (LOB) 應用程式上啟用 Intune MAM。 它是將 Intune MAM SDK 併入到您 App 最簡單的方式，讓您的 App 可以強制執行透過 Intune 部署的 MAM 原則。 使用 MAM 原則，您可以：

1. 加密 App 的資料。
2. 要求資訊工作者啟動 App 時輸入 PIN。
3. 讓 App 只能傳送資料給其他受管理的 App。
4. 防止 App 將資料備份到 Android、iTunes 及 iCloud。
5. 僅允許對/從其他受管理的 App 執行剪下、複製和貼上。

更新的 Intune App Wrapping Tool 公開預覽版現在支援 MAM，而不需要在 iOS 和 Android 上的內部 LOB 應用程式裝置註冊。 這表示您的使用者不需要向 Intune 註冊其裝置，就能使用啟用 MAM 的 LOB 應用程式。

任何人都可以測試公開預覽版軟體，並閱讀相關實用文件。文件位於 msintuneappsdk 的 GitHub：

<p style="margin-left: 40px">http://www.github.com/msintuneappsdk/intune-app-wrapper-ios-preview

<p style="margin-left: 40px">http://www.github.com/msintuneappsdk/intune-app-wrapper-android-preview

在您安裝並使用適用於 Android 與 iOS 的 Microsoft Intune App Wrapping Tool 發行前版本之前，您必須：

* 檢閱適用於 Android 與 iOS 的 Microsoft Intune App Wrapping Tool 發行前版本的 Microsoft 授權條款
* 列印並保留一份授權條款供您備查。 下載及使用適用於 Android 的 Microsoft Intune App Wrapping Tool 發行前版本，即代表您同意這些授權條款。 若貴用戶不同意這些授權條款，請不要使用「軟體」。
<!---TFS 1235607--->

### <a name="intune-groups-begin-transitioning-to-azure-active-directory-in-september"></a>Intune 群組在 9 月會開始轉換到 Azure Active Directory
部分新的 Intune 帳戶將會使用 Azure Active Directory 安全性群組，而不是 Intune 使用者群組。 因為 Intune 入口網站群組頁面將會有連結，將您導向至 Azure 管理入口網站，您會知道您正在使用安全性群組。

### <a name="lookout-integration-to-protect-android-devices"></a>Lookout 整合以保護 Android 裝置
Microsoft 正在整合 Lookout 的行動威脅保護解決方案，藉由偵測裝置上的惡意程式碼、高風險 App 等等，以保護 Android 行動裝置。 Lookout 的解決方案有助於您判斷威脅層級 (可設定)。 您可以根據 Lookout 的風險評估，在 Intune 中建立相容性原則規則，來決定裝置相容性。 您可以利用條件式存取原則，根據裝置相容性狀態，允許或封鎖公司資源的存取。

系統將會提示不相容裝置的使用者進行註冊，並且要求使用者在 Android 裝置上安裝 Lookout for Work 應用程式、啟動應用程式，並修復 Lookout for Work 應用程式中所報告的威脅，才能取得存取權。 若要深入了解，請參閱[根據裝置、網路和應用程式風險限制存取](/intune/deploy-use/device-threat-protection)。


### <a name="company-portal-updates"></a>公司入口網站更新

__Android__

<p style="margin-left: 40px">**在適用於 Android 的公司入口網站新增「通知」**<br/>
<p style="margin-left: 40px">適用於 Android 的公司入口網站的首頁新增了通知圖示。 點選此圖示可存取 [通知] 頁面，為您的終端使用者顯示公司入口網站應用程式中所有需要注意的項目，例如裝置不相容、註冊更新，以及註冊啟用。 iOS 公司入口網站應用程式已經有這項通知體驗。 有了新的 [通知] 頁面，只要該裝置已經註冊，使用者便不會在每次啟動或繼續使用公司入口網站時看見 [公司存取設定] 頁面。 如果您建立自己的終端使用者指南，建議您更新文件以反映這項變更。 [這裡](https://aka.ms/androidcpupdate)提供更新的螢幕擷取畫面。  

__iOS__
<p style="margin-left: 40px">**支援的 iOS 公司入口網站應用程式變更**<br/>
<p style="margin-left: 40px">iOS 版 Microsoft Intune 公司入口網站 App 的所有使用者，現在都必須使用最新版本。 新使用者可以只下載最新版本，而目前的使用者必須更新至最新版本。 最新版本需要 iOS 8.0 或更新版本，因此除非使用者將其裝置更新為 iOS 8.0 或更新版本，然後將公司入口網站 App 更新為最新版本，否則執行較舊 iOS 版本的裝置將無法使用公司入口網站或註冊。 執行 iOS 8.0 以下版本的已註冊裝置會繼續受到管理，並且列在 Intune 管理主控台中。
<!---TFS 1283165--->

<p style="margin-left: 40px">**iOS 終端使用者取得應用程式方式的改進**<br/>
<p style="margin-left: 40px">iOS 版公司入口網站 App 已經對應用程式磚進行下列變更，將使用者指向單一位置 (公司入口網站) 中不同檢視，以取得他們所有的 App。 Apple 限制禁止公司入口網站 App 列出企業營運及受管理市集應用程式，因此使用者必須瀏覽不同的檢視才能找到所有的 App。

<p style="margin-left: 40px">[公司應用程式] 磚先前會指向公司入口網站 [所有] 索引標籤中所有 App 的清單，而它會繼續以相同方式運作。 磚的名稱已變更為 [所有應用程式]。

<p style="margin-left: 40px">[其他應用程式] 磚先前會指向公司入口網站 App 中的檢視，其中會列出 Apple 允許在公司入口網站 App 中顯示的所有 App。 磚的名稱已變更為 [精選應用程式]，點選磚會將使用者移至公司入口網站的 [精選] 索引標籤。

<p style="margin-left: 40px">[類別] 磚先前會指向公司入口網站 App 中列出 App 類別的檢視。 磚的名稱並未變更，但它現在指向公司入口網站的 [類別] 索引標籤。 您可以在[這裡](https://gallery.technet.microsoft.com/Improvements-in-how-iOS-d1104186)找到更新的螢幕擷取畫面。
  <!---TFS 1317133--->

<p style="margin-left: 40px">**提示安裝 iOS Managed Browser 應用程式 (若 IT 專業人員針對應用程式設定該需求)**<br/>
<p style="margin-left: 40px">如果您已經設定僅能在受管理的瀏覽器中開啟 Web Clip，而裝置上並未安裝受管理的瀏覽器，裝置上的公司入口網站 App 將會提示使用者安裝受管理的瀏覽器，然後才能安裝網 Web Clip。
  <!---TFS 1228570--->

__Windows__
<p style="margin-left: 40px">**Windows Phone 8.1 的公司入口網站應用程式新增了 [意見反應] 按鈕**<br/>
<p style="margin-left: 40px">Windows Phone 8.1 公司入口網站應用程式讓終端使用者能夠使用新的 [傳送意見反應] 按鈕，傳送對應用程式的意見反應。 若要尋找按鈕，使用者要點選公司入口網站應用程式畫面右下角的「三個點」功能表，然後點選 **[傳送意見反應]**。 收集到的匿名意見反應可協助 Microsoft 改進使用者的公司入口網站應用程式體驗。
<!---TFS 1317806--->

### <a name="intune-glossarybr"></a>Intune 字彙</br>
我們已將新的[字彙主題](/intune/understand-explore/intune-glossary)新增至文件庫，協助您了解 Intune 產品中所使用的一些術語。

## <a name="august-2016"></a>2016 年 8 月
### <a name="app-management"></a>應用程式管理

__iOS 9.3 隱藏與顯示的應用程式__：針對執行 iOS 9.3 或更新版本的裝置，您可以在 iOS 一般設定原則中使用隱藏與顯示的應用程式清單，以執行下列動作：
- 指定對使用者隱藏的應用程式清單。 使用者無法檢視或啟動這些應用程式。
- 指定使用者可檢視及啟動的應用程式清單。 無法檢視或啟動其他應用程式。

已部署的應用程式及內建 iOS 應用程式 (如「訊息」和「備忘錄」) 都是您可以指定的應用程式。 如需詳細資訊，請參閱 [Microsoft Intune 的 iOS 原則設定](/intune/deploy-use/ios-policy-settings-in-microsoft-intune)
<!---TFS 1279009 checked--->
__Samsung KNOX 裝置允許與封鎖的應用程式原則__：您現在可以為 Samsung KNOX 裝置設定自訂原則，讓您可建立下列其中一個項目：
- 無法在裝置上執行的應用程式清單。 即使應用程式已安裝，在封鎖清單中定義後即無法在裝置啟動。
- 裝置使用者可從 Google Play 市集安裝的應用程式清單。 無法從市集安裝其他應用程式。

只有執行 Samsung KNOX 的裝置可使用這些設定。
如需詳細資訊，請參閱 [Use custom policies to allow and block apps for Samsung KNOX devices](/intune/deploy-use/custom-policy-to-allow-and-block-samsung-knox-apps) (使用自訂原則來允許及封鎖 Samsung KNOX 裝置的應用程式)。
<!---TFS 1311629 checked --->

__與行動應用程式管理 (MAM) 原則相容的新應用程式__：無論裝置是否已註冊，適用於 [iOS](https://itunes.apple.com/app/yammer/id289559439?mt=8) 與 [Android](https://play.google.com/store/apps/details?id=com.yammer.v1) 的 Yammer 應用程式現在會與 [Intune 行動應用程式管理 (MAM) 原則](/intune/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune)相容。

如需與 MAM 相容的應用程式完整清單，請參閱 [Microsoft Intune 應用程式合作夥伴](https://www.microsoft.com/cloud-platform/microsoft-intune-partners)網站。
<!--- TFS 1252335 & 1252336 checked--->

__Intune Viewer 應用程式__：從 2016 年 8 月開始，在發佈新的 RMS 共用應用程式版本後，我們會移除下列 Intune Viewer 應用程式︰
- Intune AV Viewer
- Intune PDF Viewer
- 來自 Google Play 的 Intune Image Viewer for Android

我們建議使用新的 [Android 版授權管理應用程式 (RMS 共用)](/intune/deploy-use/end-user-experience-for-mam-enabled-apps-with-microsoft-intune#viewing-media-files-with-the-rights-management-sharing-app)，而不是使用 Intune Viewer 應用程式，它可讓您部署一個應用程式，而不必部署三個不同的應用程式，即可安全地在 Android 裝置上檢視公司檔案。 當 Intune Viewer 應用程式不再受到支援時，它將會從 Google 商店移除，且未來無法提供使用。

### <a name="device-management"></a>裝置管理
__Android 7.0 支援__：Intune 將為即將推出之行動裝置適用的 Android 7.0 作業系統提供「第 0 天」支援。
<!---TFS 1262053--->
### <a name="google-removal-of-remote-passcode-reset-capability-on-android-70-devices"></a>Google 移除 Android 7.0 裝置上的遠端密碼重設功能
Google 將會移除 Android 7.0 裝置讓 IT 管理員與終端使用者在遠端重設密碼的功能。 先前，IT 管理員可以從遠端重設使用者的密碼，而終端使用者可從公司入口網站重新其密碼。



### <a name="company-portal-updates"></a>公司入口網站更新
__公司入口網站__
- **從公司入口網站的意見反應連結到 Microsoft** <br/>
公司入口網站可讓使用者在頁面底部點選新的 [意見反應] 連結，以將其網站體驗的相關意見反應傳送到 Microsoft。 收集到的匿名意見反應可協助 Microsoft 改進使用者的公司入口網站體驗。
<!--- TFS 1313657 checked--->

__iOS__
- **iOS Managed Browser 版本至少要更新至 8.0**<br/>
適用於 IOS 的 Microsoft Intune Managed Browser 應用程式已更新為支援執行 iOS 8.0 或更新版本的裝置。 雖然 iOS 7.1 裝置仍然可以使用現有的 Managed Browser 應用程式，請鼓勵您的使用者更新至 iOS 8.0 或更新版本，以存取並且充分利用新的 Managed Browser 功能。  
<!---TFS 1313253 checked--->

### <a name="whats-coming"></a>未來動態
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

### <a name="service-deprecation"></a>服務取代

- **支援的 iOS 公司入口網站應用程式變更**<br/>
自 9 月起，iOS 版 Microsoft Intune 公司入口網站應用程式的所有使用者都必須使用最新版本。 新使用者只可以下載最新版本，目前使用者則需要它的更新。 最新版本需要 iOS 8.0 或更新版本，因此除非他們將其裝置更新為 iOS 8.0 或更新版本，然後將公司入口網站應用程式更新為最新版本，否則執行較舊 iOS 版本的裝置會無法使用公司入口網站或註冊。 執行 iOS 8.0 以下版本的已註冊裝置會繼續受到管理，並且列在 Intune 管理主控台中。  

- **iOS Managed Browser 版本至少要更新至 8.0**<br/>
Intune 將於八月發行的 iOS 版 Microsoft Intune Managed Browser 應用程式更新，將僅支援執行 iOS 8.0 或更新版本的裝置。 雖然 iOS 7.1 裝置仍然可以使用現有的 Managed Browser 應用程式，請建議您的使用者更新至 iOS 8.0 或更新版本，以存取並且充分利用新的 Managed Browser 功能。  
<!---TFS 1313253--->

- **2016 年 9 月起，將取代 Windows 8 和 Windows Phone 8 的公司入口網站應用程式** <br/>
從 2016 年 9 月開始，Microsoft Intune 將結束 Windows Phone 8 和 Windows 8 平台的 Microsoft Intune 公司入口網站應用程式支援。 將裝置更新為 Windows 8.1 和 Windows Phone 8.1，並使用對應的 Windows 8.1 和 Windows Phone 8.1 公司入口網站應用程式繼續將應用程式發佈至這些裝置。
<!---TFS 1255391--->

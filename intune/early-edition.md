---
title: "舊版"
description: 
keywords: 
author: brenduns
ms.author: brenduns
manager: angrobe
ms.date: 09/29/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: f2e11a7fbe226932206f6946ef0603307e76c69c
ms.sourcegitcommit: 4184db38d1a9a223e680bcb4c9b732f7069bf510
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2017
---
# <a name="the-early-edition-for-microsoft-intune---september-2017"></a>Microsoft Intune 的初期版 - 2017 年 9 月

**舊版**提供 Microsoft Intune 即將發行版本要推出的功能清單。 此資訊以有限的基礎提供，並可能有所變更。 請不要在貴公司以外的地方分享此資訊。 這裡列出的一些功能可能有截止日期，而且可能會延遲到未來的版本。 其他功能正在實驗 (測試) 中進行測試，以確保它們可供客戶使用。 如果您有任何問題或疑慮，請洽詢您的 Microsoft 產品群組連絡人。

此頁面會定期更新。 請回來查看其他更新。

> [!Note]
>下列變更正在 Intune 的開發過程中。 如需新混合式功能的詳細資訊，請查看我們的[混合式新增功能](/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management)頁面。

<!--

## What's coming to Intune in the Azure portal  
## What's coming to Intune apps
## Notices
   
-->

  

## <a name="intune-in-the-azure-portal"></a>Azure 入口網站中的 Intune


### <a name="google-play-protect-support-on-android----908720----"></a>Android 中的 Google Play Protect 支援 <!-- 908720  -->  
在 Android Oreo 版本中，Google 引進名為 Google Play Protect 的安全性功能套件，可讓使用者和組織執行安全的應用程式和保護 Android 映像。 Intune 將支援 Google Play Protect 功能，包括 SafetyNet 遠端證明。  系統管理員可設定合規性原則需求，藉此要求設定 Google Play Protect 且其狀況良好。 [SafetyNet 裝置證明] 設定可要求裝置連線至 Google 服務，以驗證裝置狀況良好且未遭入侵。 系統管理員也可以設定 Android for Work 的組態設定檔設定，以要求已安裝的應用程式必須經過 Google Play 服務驗證。  如果裝置不符合 Google Play Protect 的需求規範，條件式存取可能會禁止使用者存取公司資源。 

### <a name="prevent-users-of-android-devices-from-changing-their-device-date-and-time-----1333292---"></a>防止 Android 裝置的使用者變更其裝置的日期和時間 <!-- 1333292 -->
您可以使用 [Android 自訂裝置原則](custom-settings-android.md)來防止 Android 裝置使用者變更裝置的日期和時間。
若要這樣做，請設定 Android 自訂原則，將 URI ./Vendor/MSFT/PolicyManager/My/System/AllowDateTimeChange 設定為 **TRUE**，然後指派給所需的群組。

### <a name="view-app-protection-policy-assignments-for-troubleshooting-----1475003---"></a>檢視應用程式保護原則指派以進行疑難排解 <!--  1475003 -->
在此即將發行的版本中，將會新增 [應用程式保護原則] 選項到疑難排解刀鋒視窗中提供的 [指派] 下拉式清單。 您現在可以選取應用程式保護原則，以查看指派給所選取使用者的應用程式保護原則。

### <a name="create-ios-apps-limited-to-specific-regional-apple-app-stores----1281692---"></a>建立僅限於特定地區 Apple App Store 的 iOS 應用程式 <!-- 1281692 -->
您可以在 Apple App Store 受管理的應用程式建立期間，指定國家/地區的地區設定。

> [!NOTE]  
> 目前，您僅能建立出現在美國市集的 Apple App Store 受管理應用程式。

### <a name="select-apple-country-store-to-sync-vpp-apps-----1332311---"></a>選取 Apple 國家/地區市集以同步處理 VPP 應用程式 <!-- 1332311 -->  
上傳您的大量採購方案 (VPP) 權杖時，可以設定 VPP 的國家/地區市集。 Intune 會從指定的 VPP 國家/地區市集同步處理所有地區設定的 VPP 應用程式。

> [!NOTE]  
> 目前 Intune 只會從符合 Intune 地區設定 (建立 Intune 租用戶所在位置) 的 VPP 國家/地區市集同步處理 VPP 應用程式。

###  <a name="update-ios-vpp-user-and-device-licensed-apps-----1305564---"></a>更新 iOS VPP 使用者和裝置授權的應用程式 <!-- 1305564 -->  
您可以透過 Intune 服務，設定 iOS VPP 權杖以更新為該權杖所購買的全部應用程式。 Intune 會偵測應用程式市集內的 VPP 應用程式更新，並在裝置簽入時將更新自動推送至裝置。

### <a name="ios-11-support----1428975---"></a>iOS 11 支援 <!-- 1428975 -->
當 Apple 發行時，Intune 將會支援 iOS 11。

### <a name="new-settings-for-windows-10-team-device-restriction-profile------1308838----"></a>適用於 Windows 10 團隊版裝置限制設定檔的新設定 <!--- 1308838  -->
在此版本中，我們新增了許多設定到 Windows 10 團隊版裝置限制設定檔，以協助您控制 Surface Hub 裝置。
如需此設定檔的詳細資訊，請參閱 [Windows 10 團隊版裝置限制設定](device-restrictions-windows-10-teams.md)。

### <a name="support-for-windows-10-edition-upgrade-policy------903672-1119689---"></a>支援 Windows 10 版本升級原則 <!-- 903672, 1119689 -->  
您可以建立 Windows 10 版本升級原則，以將 Windows 10 裝置升級為 Windows 10 教育版、Windows 10 教育版 N、Windows 10 專業版、Windows 10 專業版 N、Windows 10 專業教育版和 Windows 10 專業教育版 N。如需 Windows 10 版本升級的詳細資訊，請參閱[如何設定 Windows 10 版本升級](edition-upgrade-configure-windows-10.md)。

### <a name="review-policy-compliance-for-windows-10-update-rings----1352223---"></a>檢閱 Windows 10 更新通道的原則合規性 <!-- 1352223 -->  
您可以從 [軟體更新] > [依更新通道別部署狀態] 來檢閱 Windows 10 更新通道的原則報告。 原則報告包括已設定更新通道的部署狀態。 

### <a name="windows-10-company-portal-app-added-to-windows-information-protection-allow-policy----677129---"></a>Windows 10 公司入口網站應用程式已新增到 Windows 資訊保護允許原則 <!-- 677129 -->  
Windows 10 公司入口網站應用程式將會更新以支援 Windows 資訊保護 (WIP)。 此應用程式可新增至 WIP 允許原則。 透過這項變更，此應用程式將不再需要新增至 [豁免] 清單。 

### <a name="remote-support-for-windows-and-windows-mobile-devices-----1070473---"></a>適用於 Windows 和 Windows Mobile 裝置的遠端支援 <!-- 1070473 -->    
Intune 將可使用 [TeamViewer](https://www.teamviewer.com) 軟體 (需另行購買)，讓您為執行 Windows 和 Windows Mobile 裝置的使用者提供遠端協助。

### <a name="scan-devices-with-windows-defender----1280988--1280990-----"></a>使用 Windows Defender 掃描裝置 <!-- 1280988  1280990   -->
您可以在受管理的 Windows 10 裝置上，使用 Windows Defender 防毒軟體來執行「快速掃描」、「完整掃描」，和「更新簽章」。 從裝置的概觀刀鋒視窗，選擇要在裝置上執行的動作。 系統會提示您確認動作，然後命令才會傳送到裝置。 

**快速掃描**：快速掃描會掃描惡意程式碼註冊要啟動的位置，例如登錄機碼和已知的 Windows 啟動資料夾。 快速掃描平均會花費五分鐘。 快速掃描與 [隨時開啟即時保護] 設定 (可在檔案開啟、關閉，以及使用者每次瀏覽資料夾時掃描檔案) 結合時，可提供保護以防禦潛藏於系統或核心的惡意程式碼。 掃描完成時，使用者可在其裝置上查看掃描結果。 

**完整掃描**：完整掃描對於已遭遇惡意程式碼威脅的裝置非常實用，可找出是否有任何需要進一步完整清理的尚未作用元件，且適合執行隨選掃描。 完整掃描可能需要一個小時來進行。 掃描完成時，使用者可在其裝置上查看掃描結果。 

**更新簽章**：更新簽章命令會更新 Windows Defender 防毒軟體的惡意程式碼定義和簽章。 這有助於確保 Windows Defender 防毒軟體能有效偵測惡意程式碼。 這項功能僅適用於 Windows 10 裝置，且需要裝置的網際網路連線。 

### <a name="bitlocker-device-configuration----1397398---"></a>BitLocker 裝置設定 <!-- 1397398 -->  
[Windows 加密] > [基本設定] 將會納入新的 [其他磁碟加密的警告] 設定，讓您停用使用者裝置上可能正在使用的其他磁碟加密[警告提示](https://docs.microsoft.com/en-us/windows/client-management/mdm/bitlocker-csp#allowarningforotherdiskencryption) \(英文\)。  警告提示會要求使用者同意，然後才會在裝置上設定 BitLocker，在使用者確認之前則會封鎖 BitLocker 設定。  新的設定會停用使用者警告。

### <a name="company-portal-for-windows-81-and-windows-phone-81-moving-to-sustaining-mode---1428681--"></a>Windows 8.1 和 Windows Phone 8.1 版公司入口網站移至維持模式 <!--1428681-->
自 2017 年 10 月起，Windows 8.1 和 Windows Phone 8.1 公司入口網站應用程式將會移至維持模式。 這表示這些平台將會繼續支援應用程式和現有的案例 (例如註冊和合規性)。 這些應用程式仍可透過現有的發行通道 (例如 Microsoft 市集) 下載取得。 

一旦進入維持模式，這些應用程式僅會接收重大安全性更新。 但是，將不會針對這些應用程式發行額外的更新或功能。 如需新功能，建議您將裝置更新為 Windows 10 或 Windows 10 行動裝置版。 

###  <a name="block-copy-and-paste-between-work-and-personal-profiles-in-android-for-work----1098994---"></a>封鎖 Android for Work 中工作和個人設定檔間的複製和貼上 <!-- 1098994 -->   
在此版本中，您可以將 Android for Work 的工作設定檔設定為封鎖工作和個人應用程式間的複製和貼上。 您可以在 [工作設定檔設定] 中，於 [Android for Work] 平台的 [裝置限制] 設定檔內找到這項新設定。

### <a name="new-behaviors-for-the-company-portal-app-for-android-with-work-profiles----1485783---"></a>Android 公司入口網站應用程式使用工作設定檔的新行為 <!---1485783--->
當您使用工作設定檔註冊 Android for Work 裝置時，是由工作設定檔中的公司入口網站應用程式來執行裝置上的管理工作。 除非您使用個人設定檔中啟用 MAM 的應用程式，否則 Android 公司入口網站應用程式不再有任何用途。 為了改善工作設定檔的體驗，Intune 會在成功註冊工作設定檔後，自動隱藏個人的公司入口網站應用程式。

您可以隨時啟用個人設定檔中的 Android 公司入口網站應用程式，方法是瀏覽 [Play Store 中的公司入口網站](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal)，然後點選 [啟用]。

### <a name="intune-mam--outlook-for-android-add-ins-----1450688---"></a>Intune MAM 和 Android 版 Outlook 的增益集 <!-- 1450688 -->
在未來幾週，Office 小組將會宣布適用於 Android 版 Outlook 的增益集。 此增益集功能集現已存在於 Windows、iOS，Web 和 Mac 版 Outlook 中。 因為增益集是透過 Exchange 管理，除非 Exchange 系統管理員關閉增益集的存取功能，否則使用者將能夠在 Outlook 和未受管理的增益集應用程式之間複製並共用資料和郵件。 

若要管理使用者的增益集存取權限，請與您的 Exchange 系統管理員合作，確保 MAM 資料保護原則套用至增益集。

#### <a name="how-does-this-affect-me"></a>此變更對我造成什麼影響？
如果您的 Exchange 原則已設定為防止側載增益集或安裝增益集，則無需繼續閱讀。 您的 MAM 原則將會如預期套用。 不過，如果您已在 MAM 中設定原則以限制 Android 版 Outlook 中的剪下、複製和貼上操作，而並未在 Exchange 中設定增益集原則，您應該了解使用者預設將能夠安裝增益集至 Outlook。 這些增益集可以存取郵件內文、主旨和其他的郵件屬性。 您可以關閉讓使用者安裝增益集的功能，方法是請 Exchange 系統管理員移除「我的市集應用程式」和「我的自訂應用程式」角色。 如需詳細資訊，請參閱下方共用的額外資訊連結。

請注意，Exchange 中的設定變更將會套用至 Windows、iOS、Web、Mac 和行動裝置版 Outlook。 

#### <a name="what-do-i-need-to-do"></a>我需要做什麼？
檢閱您目前的 Exchange 原則。 通知您的 IT 和技術服務人員。 如有任何問題或疑慮，請連絡我們的支援小組。 

### <a name="user-device-association-entity-collection-added-to-intune-data-warehouse-data-model----1187917---"></a>使用者裝置關聯實體集合已新增至 Intune 資料倉儲資料模型 <!-- 1187917 -->
您可以使用使用者裝置關聯資訊 (關聯使用者和裝置實體集合) 來建立報表和資料視覺效果。 資料模型的存取可透過擷取自資料倉儲 Intune 頁面的 Power BI 檔案 (PBIX)、透過 OData 端點，或開發自訂用戶端來存取。


<!-- the following are present prior to 1709 -->

### <a name="actions-for-non-compliance----730266--"></a>非合規性動作 <!--730266-->     
[不符合規定時所採取的動作] 是合規性原則的新功能，可讓您對不相容的裝置採取動作。 您可以指定單一或多個動作，並指定必須進行這些動作的時間週期。 例如，您可以在裝置變成不相容之後透過電子郵件立即通知使用者有不相容的裝置，也可以在 3 天寬限期之後透過條件式存取封鎖不相容的裝置存取公司資源。

### <a name="new-report-that-lists-ios-devices-with-older-ios-versions------1352223---"></a>列出舊版 iOS 之 iOS 裝置的新報表   <!-- 1352223 -->
[軟體更新] 工作區將提供**過期的 iOS 裝置**報表。 在此報表中，您可以檢視受監督的 iOS 裝置清單，這些是 iOS 更新原則之前鎖定並有可用更新的裝置。 針對每部裝置，您可以檢視狀態，以了解為何尚未自動更新裝置。 

### <a name="new-settings-for-windows-10-device-restriction-profile"></a>適用於 Windows 10 裝置限制設定檔的新設定
<!--- 978575, 1308849, -->
我們將為 Windows Defender SmartScreen 類別中的 Windows 10 裝置限制設定檔新增設定。

如需 Windows 10 裝置限制設定檔的詳細資料，請參閱 [Windows 10 及更新版本的裝置限制設定]( device-restrictions-windows-10.md)。

### <a name="android-for-work-support-for-lookout----1087312---"></a>適用於 Lookout 的 Android for Work 支援 <!-- 1087312 -->   
具有 Lookout 的 Intune 連接器將在使用 Lookout for Work 應用程式時支援 Android for Work 裝置。 您能在容器內部或外部部署 Lookout 應用程式。

### <a name="intune-app-protection-and-citrix-mdx-development-tools----709185---"></a>Intune 應用程式防護和 Citrix MDX 開發工具 <!-- 709185 -->
您可以搭配使用 Citrix XenMobile MDX 和 Microsoft Intune 來管理裝置和應用程式。 如此一來，您就可以使用 Citrix 的 mVPN 技術，透過 Intune 應用程式防護原則來管理應用程式。

您可以尋找程式碼存放庫，其中包含適用於 iOS 和 Android 的 Intune App Wrapping Tool 和 Intune App SDK，並與 Citrix MDX mVPN 技術整合。

### <a name="zimperium---new-mobile-threat-defense-partner------954681---"></a>Zimperium - 新的 Mobile Threat Defense 夥伴<!-- 954681 -->
您可以根據由 Zimperium (一個與 Microsoft Intune 整合的 Mobile Threat Defense 解決方案) 所進行的風險評估，使用條件式存取來控制行動裝置對公司資源的存取。

#### <a name="how-integration-with-intune-works"></a>整合 Intune 如何運作？
風險評估的依據是收集自執行 Zimperium 裝置的遙測。 您可以根據透過 Intune 裝置合規性政策啟用的 Zimperium 風險評估，設定 EMS 條件式存取原則。透過該原則，您可以根據偵測到的威脅來允許或封鎖不符合規範的裝置存取公司資源。

### <a name="new-azure-ad-conditional-access-policy-ui-link-from-intune-----1016201---"></a>Intune 中的新 Azure AD 條件式存取原則 UI 連結  <!-- 1016201 -->
IT 系統管理員可以透過 Azure AD 工作負載中的新條件式存取原則 UI，來設定以應用程式為基礎的條件式原則。 Azure 之 [Intune 應用程式防護] 區段中的以應用程式為基礎的條件式存取原則會暫時保留不動，而且會並存強制執行。 Azure AD 的 Intune 工作負載也提供方便的連結，可連至新的條件式存取原則 UI。

### <a name="on-premises-exchange-connector-high-availability-support-----676614---"></a>內部部署 Exchange Connector 高可用性支援<!-- 676614 -->   
內部部署 Exchange Connector 可以有多個用戶端存取伺服器 (CAS) 角色。 例如，如果主要的 CAS 失敗，則 Exchange Connector 就會收到切換回其他 CAS 的查詢。 這項功能可確保服務不中斷。

### <a name="system-center-operations-manager-management-pack-for-exchange-connector----885457---"></a>適用於 Exchange connector 的 System Center Operations Manager 管理組件<!-- 885457 -->   
適用於 Exchange Connector 的 System Center Operations Manager 管理組件將可協助您剖析 Exchange Connector 記錄。 此管理組件可在您需要針對問題進行疑難排解時，為您提供不同方式來監視 Intune。

### <a name="end-of-support-for-ios-80----1164477---"></a>結束對 iOS 8.0 的支援<!---1164477--->
受管理的應用程式和 iOS 公司入口網站應用程式需要 iOS 9.0 及更新版本才能存取公司資源。 今年 9 月前未更新的裝置將不再能存取公司入口網站或這些應用程式。  

### <a name="end-of-support-for-android-43-and-lower----1171127-1326920----"></a>結束對 Android 4.3 和較舊版本的支援<!---1171127, 1326920 --->
受管理的應用程式和 Android 公司入口網站應用程式需要 Android 4.4 及更新版本才能存取公司資源。 10 月初前未更新的裝置將不再能存取公司入口網站或這些應用程式。 今年 12 月會強制淘汰所有已註冊的裝置，以致無法存取公司資源。 如果您使用不含 MDM 的應用程式保護原則，應用程式就不會接收更新，其體驗品質會隨著時間而降低。

### <a name="platform-support-reminder-windows-phone-81-mainstream-support-will-end-july-11-2017----1327781---"></a>平台支援提醒：Windows Phone 8.1 主要支援將於 2017 年 7 月 11 日結束<!-- 1327781 -->  
Windows Phone 8.1 平台將於 2017 年 7 月 11 日結束主要支援。 Windows 8.1 電腦的支援不受影響。

受 Intune 服務管理的所有 Windows Phone 8.1 裝置沒有直接影響。 已註冊的裝置會繼續運作，而所有的原則、設定和應用程式也會一如預期般運作。 請注意，沒有以 Intune 服務內的 Windows Phone 8.1 平台為目標的改進，也沒有以 Windows Phone 8.1 公司入口網站應用程式為目標的改進。

我們建議您盡早將符合資格的 Windows Phone 8.1 裝置升級至 Windows 10 行動裝置版。 





## <a name="intune-apps"></a>Intune 應用程式

### <a name="search-improvements-to-the-company-portal-website---1331697--"></a>公司入口網站的搜尋改善<!--1331697-->
我們正在改善應用程式搜尋功能，並從[公司入口網站](https://portal.manage.microsoft.com)開始。 除了 [名稱] 和 [描述] 欄位之外，現在也會對應用程式類別執行搜尋。 預設會依相關性的遞減順序來排序結果。 

iOS 使用者也會收到這項變更，因為也會使用公司入口網站作為適用於 iOS 的公司入口網站應用程式一部分。 適用於 Android 和 Windows 的公司入口網站應用程式將會在接下來的幾個月收到類似的更新。 

我們仍然會微調相關性的追蹤方式；因此，請使用公司入口網站底端的 [意見反應] 連結，讓我們知道其運作方式。

### <a name="refresh-action-added-to-the-company-portal-app-for-windows-10---1132468--"></a>重新整理動作已新增至 Windows 10 的公司入口網站應用程式 <!--1132468-->
Windows 10 的公司入口網站應用程式可讓使用者重新整理應用程式中的資料，無論是拖動以重新整理，或 (在桌上型電腦) 按一下 F5 皆可。


### <a name="apps-that-are-available-with-or-without-enrollment-can-now-be-installed-without-being-prompted-for-enrollment----1334712---"></a>需要或無須註冊而提供的應用程式現在可以直接安裝，而不會提示註冊。 <!-- 1334712 -->
在 Android 公司入口網站應用程式中需要或無須註冊而提供的應用程式，現在可以安裝而不會提示註冊。

### <a name="ios-company-portal-display-large-icons----1454593---"></a>iOS 公司入口網站顯示大型圖示 <!-- 1454593 -->
我們正在修正 iOS 公司入口網站於應用程式磚中顯示圖示方式的已知問題。 如果您上傳 120x120 像素或更大的應用程式圖示，現在會以完整的應用程式磚大小顯示在 [公司入口網站] (https://portal.manage.microsoft.com) 和 iOS 公司入口網站的應用程式頁面中。

### <a name="easier-to-understand-phrasing-for-the-company-portal-app-for-android------1396349---"></a>Android 公司入口網站應用程式中更易了解的措辭 <!---1396349--->    
Android 公司入口網站應用程式的註冊程序已經使用新的文字來簡化，讓使用者可更輕鬆地進行註冊。 


<!-- the following are present prior to 1709 -->


### <a name="intune-managed-browser-support-for-ios-and-android----1374196---"></a>iOS 和 Android 的 Intune Managed Browser 支援 <!---1374196--->
自 2017 年 10 月起，Android 應用程式上的 Intune Managed Browser 應用程式只會支援執行 Android 4.4 和更新版本的裝置。 iOS 上的 Intune Managed Browser 應用程式只支援執行 iOS 9.0 及更新版本的裝置。 較舊版本的 Android 和 iOS 能夠繼續使用 Managed Browser，但是無法安裝新版的應用程式，而且可能無法存取所有的應用程式功能。 建議您將這些裝置更新為受支援的作業系統版本。

### <a name="allow-end-users-to-access-the-company-portal-app-for-android-without-enrollment----1169910---"></a>允許使用者存取適用於 Android 的公司入口網站應用程式，不需要註冊。<!---1169910--->  
使用者很快地不必註冊裝置也能存取 Android 的公司入口網站。 使用應用程式保護原則的組織使用者，在開啟公司入口網站應用程式時，將不會再收到註冊裝置的提示。 使用者也可以從公司入口網站安裝應用程式，不用註冊裝置。 

### <a name="improved-error-message-for-when-a-user-reaches-the-maximum-number-of-devices-allowed-to-enroll----1270370---"></a>改進使用者達到允許註冊的裝置數目上限時的錯誤訊息 <!-- 1270370 -->
終端使用者不會看到一般錯誤訊息，而是會看到實用且可採取動作的錯誤訊息：「您已註冊 IT 系統管理員所允許的裝置數目上限。請移除已註冊的裝置，或向您的 IT 系統管理員取得協助。」

### <a name="inform-end-users-what-device-information-can-be-seen-for-ios---739894--"></a>通知終端使用者可看到哪些 iOS 裝置資訊 <!--739894-->
我們將為適用於 iOS 的公司入口網站應用程式中的 [裝置詳細資料] 畫面新增 [Ownership Type] (擁有權類型)。 如此一來，使用者就能夠直接從 Intune 終端使用者文件的此頁面，了解有關隱私權的更多資訊。他們也能夠在 [關於] 畫面上找到這項資訊。

### <a name="apps-details-pages-display-new-information-for-android-devices---1287476--"></a>應用程式詳細資料頁面會顯示 Android 裝置的新資訊 <!--1287476-->
適用於 Android 之公司入口網站應用程式的應用程式詳細資料頁面，會顯示 IT 系統管理員已為該應用程式定義的應用程式類別。

### <a name="intune-mobile-application-management-mam-dialog-boxes-now-have-a-modern-interface----1199015---"></a>Intune 行動應用程式管理 (MAM) 對話方塊現在會有新式介面 <!-- 1199015 -->
Intune 行動應用程式管理 (MAM) 對話方塊已更新為新式外觀及操作。 這些對話方塊的運作方式會與舊版樣式相同。

在新式 Android 裝置上，Intune 所顯示的錯誤或通知對話方塊現在會顯示更新的外觀及操作。



## <a name="notices"></a>通知
### <a name="apple-to-require-updates-for-application-transport-security---748318--"></a>Apple 需要更新 Application Transport Security <!--748318-->   
Apple 宣布，從 2017 年春季開始，將會強制執行 Application Transport Security (ATS) 的特定需求。 ATS 可用來對透過 HTTPS 進行的所有應用程式通訊，強制執行更嚴格的安全性。 此變更會影響使用 iOS 公司入口網站應用程式的 Intune 客戶。 如需詳細資訊，請檢閱我們的 [Intune 支援部落格](https://aka.ms/compportalats)。

### <a name="plan-for-change-intune-is-changing-the-intune-partner-portal-experience----1050016---"></a>變更計畫：Intune 正在變更 Intune 合作夥伴入口網站體驗 <!-- 1050016 -->
我們會在 2017 年 5 月中旬的服務更新將 Intune 合作夥伴頁面從 manage.microsoft.com 移除。  

如果您是合作夥伴系統管理員，將無法再從 Intune 合作夥伴頁面代表客戶檢視或採取動作，但會需要登入在 Microsoft 的另外兩個合作夥伴入口網站的其中一個。

[Microsoft 合作夥伴中心](https://partnercenter.microsoft.com/)和 [Microsoft Office 365 合作夥伴系統管理中心](https://portal.office.com/)都能讓您登入所管理客戶的帳戶。 合作夥伴在此後請使用這兩個網站來管理客戶。



### <a name="see-also"></a>請參閱
如需近期發展的詳細資料，請參閱 [Microsoft Intune 的新功能](whats-new.md)。

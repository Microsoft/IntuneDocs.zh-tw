---
title: "舊版"
description: 
keywords: 
author: brenduns
ms.author: brenduns
manager: angrobe
ms.date: 8/3/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 5861c999752bfef05b8a33161d0bf75a6d4daf59
ms.sourcegitcommit: 18cdbdc226f64368de892a8c5cff157c37986c57
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/03/2017
---
# <a name="the-early-edition-for-microsoft-intune---august-2017"></a>Microsoft Intune 的舊版 - 2017 年 8 月

**舊版**提供 Microsoft Intune 即將發行版本要推出的功能清單。 此資訊以有限的基礎提供，並可能有所變更。 請不要在貴公司以外的地方分享此資訊。 這裡列出的一些功能可能有截止日期，而且可能會延遲到未來的版本。 其他功能正在實驗 (測試) 中進行測試，以確保它們可供客戶使用。 如果您有任何問題或疑慮，請洽詢您的 Microsoft 產品群組連絡人。

此頁面會定期更新。 請回來查看其他更新。

> [!Note]
>下列變更正在 Intune 的開發過程中。 如需新混合式功能的詳細資訊，請查看我們的[混合式新增功能](/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management)頁面。

<!--

## What's coming to Intune on the Azure portal  
## What's coming to Intune apps
## Notices

-->



## <a name="intune-on-the-azure-portal"></a>Azure 入口網站上的 Intune




### <a name="new-device-action-to-force-devices-to-sync-with-intune----711369---"></a>新的裝置動作會強制裝置與 Intune 同步處理<!-- 711369 -->    
我們要新增裝置動作，強制所選裝置立即使用 Intune 簽入。 當裝置簽入時，會立即收到所有擱置動作或已指派給它的原則。  這個動作可協助您立即驗證和針對您已指派的原則進行疑難排解，不用等到下次排程的簽入。

### <a name="actions-for-non-compliance----730266--"></a>非合規性動作 <!--730266-->     
[不符合規定時所採取的動作] 是合規性原則的新功能，可讓您對不相容的裝置採取動作。 您可以指定單一或多個動作，並指定必須進行這些動作的時間週期。 例如，您可以在裝置變成不相容之後透過電子郵件立即通知使用者有不相容的裝置，也可以在 3 天寬限期之後透過條件式存取封鎖不相容的裝置存取公司資源。


### <a name="restrict-android-and-ios-device-enrollment-restriction-by-os-version------1333256--1245463----"></a>依作業系統版本限制 Android 和 iOS 裝置註冊限制 <!--- 1333256,  1245463 --->  
Intune 現在支援依作業系統版本號碼限制 iOS 和 Android 註冊。 在 [Intune]  >  [註冊限制]  >  [裝置類型限制]  >  [預設]  >  [平台限制] 下，IT 管理員現在可以設定平台設定，將註冊限制在作業系統值上下限之間。 Android 作業系統版本必須指定為 Major.Minor.Build.Rev，其中 Build 及 Rev 均為選擇性。 iOS 版本必須指定為 Major.Minor.Build，其中 Build 為選擇性。

>[!NOTE]
>此設定不會限制透過 Apple 註冊程式的註冊，這些程式包括 Apple 裝置註冊方案和 Apple School Manager 或 Apple Configurator。

### <a name="restrict-android-ios-and-macos-device-personally-owned-device-enrollment------1333272--1333275-1245709----"></a>限制 Android、iOS 和 macOS 裝置以個人擁有的裝置註冊<!--- 1333272,  1333275, 1245709 --->
Intune 現在支援限制使用裝置序號註冊個人擁有的 iOS、Android 和 macOS 裝置。 某些裝置不會回報序號。 如需詳細資訊，請洽裝置製造商。 將序號上傳至 Intune，您就可以預先宣告此為公司擁有的裝置。 使用註冊限制，您可以封鎖個人擁有 (BYOD) 的裝置，僅註冊公司擁有的裝置。

若要在 Intune 入口網站匯入序號，請移至 [裝置註冊] > [公司裝置識別碼] 並按一下 [新增]，然後上傳 .CSV 檔案。 此檔案應該不含標頭，並具有兩欄，一欄用於序號，另一欄用於 IMEI 編號等詳細資料。  若要限制個人擁有的裝置，請移至 [裝置註冊]  >  [註冊限制]。 在 [裝置類型限制] 下選取 [預設]，然後選取 [平台設定]。 您可以 [允許] 或 [封鎖] 個人擁有的 iOS、Android 和 macOS 裝置。 

### <a name="force-supervised-ios-devices-to-automatically-install-the-latest-available-software-update----777100---"></a>強制受監督的 iOS 裝置自動安裝最新可用的軟體更新<!-- 777100 -->   
新的原則將可從 [軟體更新] 工作區取得，您可在此強制受監督的 iOS 裝置自動安裝最新可用的軟體更新。 您也可以檢視新的報表，它會列出舊版的 iOS 裝置，並摘要說明其過期的原因。

### <a name="new-report-that-lists-ios-devices-with-older-ios-versions------1352223---"></a>列出舊版 iOS 之 iOS 裝置的新報表   <!-- 1352223 -->
[軟體更新] 工作區將提供**過期的 iOS 裝置**報表。 在此報表中，您可以檢視受監督的 iOS 裝置清單，這些是 iOS 更新原則之前鎖定並有可用更新的裝置。 針對每部裝置，您可以檢視狀態，以了解為何尚未自動更新裝置。 

### <a name="new-settings-to-allow-and-block-apps-on-samsung-knox-standard-devices-----822899--1305423--"></a>使用新設定允許或封鎖應用程式在 Samsung KNOX Standard 裝置上執行  <!-- 822899,  1305423-->   
我們會新增新的[裝置限制設定](device-restrictions-android.md)，讓您指定下列應用程式清單：
  - 允許使用者安裝的應用程式
  - 封鎖使用者執行的應用程式
  - 對使用者隱藏的裝置應用程式  

您可依 URL、套件名稱，或從管理的應用程式清單中指定應用程式。

### <a name="new-settings-for-windows-10-device-restriction-profile"></a>適用於 Windows 10 裝置限制設定檔的新設定
<!--- 978575, 1308849, 1308850 -->
我們將為 Windows Defender SmartScreen 類別中的 Windows 10 裝置限制設定檔新增設定。

如需 Windows 10 裝置限制設定檔的詳細資料，請參閱 [Windows 10 及更新版本的裝置限制設定]( device-restrictions-windows-10.md)。

### <a name="new-device-restriction-settings-for-windows-10------1063965---"></a>Windows 10 的新裝置限制設定   <!-- 1063965 -->
我們將為下列類別中的 [Windows 10 裝置限制設定檔](/intune/device-restrictions-windows-10)新增設定：
- Windows Defender SmartScreen
- App Store


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

### <a name="conditional-access-support-for-mac-devices-----720172---"></a>條件式存取支援 Mac 裝置<!-- 720172 -->   
您很快就能夠設定條件式存取原則，要求 Mac 裝置向 Intune 註冊，並符合其裝置的合規性政策。 例如，使用者可以下載適用於 macOS 的 Intune 公司入口網站應用程式，並在 Intune 中註冊其 Mac 裝置。 Intune 會評估 Mac 裝置是否符合 PIN、加密、作業系統版本和系統完整性等需求。

### <a name="end-of-support-for-ios-80----1164477---"></a>結束對 iOS 8.0 的支援<!---1164477--->
受管理的應用程式和 iOS 公司入口網站應用程式需要 iOS 9.0 及更新版本才能存取公司資源。 今年 9 月前未更新的裝置將不再能存取公司入口網站或這些應用程式。 今年 12 月會禁止存取所有公司資源，包括電子郵件。 

### <a name="end-of-support-for-android-43-and-lower----1171127-1326920----"></a>結束對 Android 4.3 和較舊版本的支援<!---1171127, 1326920 --->
受管理的應用程式和 Android 公司入口網站應用程式需要 Android 4.4 及更新版本才能存取公司資源。 10 月初前未更新的裝置將不再能存取公司入口網站或這些應用程式。 今年 12 月會強制淘汰所有已註冊的裝置，以致無法存取公司資源。 如果您使用不含 MDM 的應用程式保護原則，應用程式就不會接收更新，其體驗品質會隨著時間而降低。


### <a name="platform-support-reminder-windows-phone-81-mainstream-support-will-end-july-11-2017----1327781---"></a>平台支援提醒：Windows Phone 8.1 主要支援將於 2017 年 7 月 11 日結束<!-- 1327781 -->  
Windows Phone 8.1 平台將於 2017 年 7 月 11 日結束主要支援。 Windows 8.1 電腦的支援不受影響。

受 Intune 服務管理的所有 Windows Phone 8.1 裝置沒有直接影響。 已註冊的裝置會繼續運作，而所有的原則、設定和應用程式也會一如預期般運作。 請注意，沒有以 Intune 服務內的 Windows Phone 8.1 平台為目標的改進，也沒有以 Windows Phone 8.1 公司入口網站應用程式為目標的改進。

我們建議您盡早將符合資格的 Windows Phone 8.1 裝置升級至 Windows 10 行動裝置版。 




## <a name="intune-apps"></a>Intune 應用程式

### <a name="light-and-dark-modes-available-for-the-company-portal-app-for-windows-10----676547---"></a>Windows 10 的公司入口網站應用程式提供日間和夜間模式<!---676547--->
使用者可以自訂 Windows 10 公司入口網站應用程式的色彩模式。 使用者可在公司入口網站應用程式的 [設定] 區段中進行變更。 使用者重新啟動應用程式後，即會看到變更。 至於 Windows 10 版本 1607 及更新版本，應用程式模式預設為系統設定。 至於執行 Windows 10 版本 1511 及較舊版本的電腦，應用程式模式會預設為日間模式。

### <a name="allow-end-users-to-access-the-company-portal-app-for-android-without-enrollment----1169910---"></a>允許使用者存取適用於 Android 的公司入口網站應用程式，不需要註冊。<!---1169910--->  
使用者很快地不必註冊裝置也能存取 Android 的公司入口網站。 使用應用程式保護原則的組織使用者，在開啟公司入口網站應用程式時，將不會再收到註冊裝置的提示。 使用者也可以從公司入口網站安裝應用程式，不用註冊裝置。 

### <a name="improved-error-message-for-when-a-user-reaches-the-maximum-number-of-devices-allowed-to-enroll----1270370---"></a>改進使用者達到允許註冊的裝置數目上限時的錯誤訊息 <!-- 1270370 -->
終端使用者不會看到一般錯誤訊息，而是會看到實用且可採取動作的錯誤訊息：「您已註冊 IT 系統管理員所允許的裝置數目上限。 請移除已註冊的裝置，或向您的 IT 系統管理員取得協助。」

### <a name="new-signed-in-experience-for-android-company-portal-users-and-app-protection-policy-users----621669---"></a>Android 公司入口網站使用者和應用程式防護原則使用者的新登入體驗 <!-- 621669 -->
終端使用者將能夠使用 Android 公司入口網站應用程式來瀏覽應用程式、管理裝置及檢視 IT 連絡人資訊，而不需要註冊其 Android 裝置。 此外，如果終端使用者已使用由 Intune 應用程式防護原則保護的應用程式，並啟動 Android 公司入口網站，則終端使用者將無法再收到註冊裝置的提示。 

### <a name="inform-end-users-what-device-information-can-be-seen-for-ios---739894--"></a>通知終端使用者可看到哪些 iOS 裝置資訊 <!--739894-->
我們將為適用於 iOS 的公司入口網站應用程式中的 [裝置詳細資料] 畫面新增 [Ownership Type] (擁有權類型)。 如此一來，使用者就能夠直接從 Intune 終端使用者文件的此頁面，了解有關隱私權的更多資訊。 他們也能夠在 [關於] 畫面上找到這項資訊。

### <a name="apps-details-pages-display-new-information-for-android-devices---1287476--"></a>應用程式詳細資料頁面會顯示 Android 裝置的新資訊 <!--1287476-->
適用於 Android 之公司入口網站應用程式的應用程式詳細資料頁面，會顯示 IT 系統管理員已為該應用程式定義的應用程式類別。

### <a name="intune-mobile-application-management-mam-dialog-boxes-now-have-a-modern-interface----1199015---"></a>Intune 行動應用程式管理 (MAM) 對話方塊現在會有新式介面 <!-- 1199015 -->
Intune 行動應用程式管理 (MAM) 對話方塊已更新為新式外觀及操作。 這些對話方塊的運作方式會與舊版樣式相同。

在新式 Android 裝置上，Intune 所顯示的錯誤或通知對話方塊現在會顯示更新的外觀及操作。

### <a name="new-setting-in-the-android-company-portal-app-to-toggle-battery-optimization---1405990--"></a>Android 公司入口網站應用程式中用來切換電池最佳化的新設定 <!--1405990-->
適用於 Android 的公司入口網站應用程式中的 [設定] 頁面將會有新設定，可讓使用者輕鬆地關閉公司入口網站和 Microsoft Authenticator 應用程式的電池最佳化功能。 設定中所顯示的應用程式名稱會因管理工作帳戶的應用程式而有所不同。 建議使用者關閉電池最佳化功能，以提升同步電子郵件和資料的工作應用程式效能。 




## <a name="notices"></a>通知

### <a name="apple-to-require-updates-for-application-transport-security---748318--"></a>Apple 需要更新 Application Transport Security <!--748318-->   
Apple 宣布，從 2017 年春季開始，將會強制執行 Application Transport Security (ATS) 的特定需求。 ATS 可用來對透過 HTTPS 進行的所有應用程式通訊，強制執行更嚴格的安全性。 此變更會影響使用 iOS 公司入口網站應用程式的 Intune 客戶。 如需詳細資訊，請檢閱我們的 [Intune 支援部落格](https://aka.ms/compportalats)。

### <a name="direct-access-to-apple-enrollment-scenarios---951869--"></a>直接存取 Apple 註冊案例 <!--951869-->   
對於在 2017 年 1 月之後建立的 Intune 帳戶，Intune 已經啟用使用 Azure Preview 入口網站中的「註冊裝置」工作負載直接存取 Apple 註冊案例。 Apple 註冊預覽原本只能從傳統 Intune 入口網站中的連結存取。 在 2017 年 1 月之前建立的 Intune 帳戶，將需要進行一次性移轉，才能在 Azure 中使用這些功能。 移轉的排程尚未宣布，但將會盡快提供詳細資料。 如果您現有的帳戶無法存取預覽，我們強烈建議您建立試用帳戶來測試新的體驗。

### <a name="plan-for-change-intune-is-changing-the-intune-partner-portal-experience----1050016---"></a>變更計畫：Intune 正在變更 Intune 合作夥伴入口網站體驗 <!-- 1050016 -->
我們會在 2017 年 5 月中旬的服務更新將 Intune 合作夥伴頁面從 manage.microsoft.com 移除。  

如果您是合作夥伴系統管理員，將無法再從 Intune 合作夥伴頁面代表客戶檢視或採取動作，但會需要登入在 Microsoft 的另外兩個合作夥伴入口網站的其中一個。

[Microsoft 合作夥伴中心](https://partnercenter.microsoft.com/)和 [Microsoft Office 365 合作夥伴系統管理中心](https://portal.office.com/)都能讓您登入所管理客戶的帳戶。 合作夥伴在此後請使用這兩個網站來管理客戶。



### <a name="see-also"></a>請參閱
如需近期發展的詳細資料，請參閱 [Microsoft Intune 的新功能](whats-new.md)。

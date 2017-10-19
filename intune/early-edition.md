---
title: "舊版"
description: 
keywords: 
author: brenduns
ms.author: brenduns
manager: angrobe
ms.date: 10/09/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: abb5612545174e3fd134c38fb763e02d379b50d0
ms.sourcegitcommit: b330045a4f9a807e6e2772c4ed4e1e1148e1f1f9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2017
---
# <a name="the-early-edition-for-microsoft-intune---october-2017"></a>Microsoft Intune 的舊版 - 2017 年 10 月

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

### <a name="azure-active-directory-web-sites-can-require-the-intune-managed-browser-app-and-support-single-sign-on-for-the-managed-browser-public-preview----710595---"></a>Azure Active Directory 網站可以要求使用 Intune Managed Browser 應用程式，並支援 Managed Browser (公開預覽) 的單一登入 <!-- 710595 -->   
使用 Azure Active Directory (Azure AD) 時，您能夠限制行動裝置使用 Intune Managed Browser 應用程式存取網站。 在 Managed Browser 中，網站資料的安全受到保護，並會與使用者的個人資料區隔開來。 此外，針對受 Azure AD 保護的網站，Managed Browser 也支援單一登入功能。 當使用者登入 Managed Browser，或在裝置上搭配使用 Managed Browser 與受 Intune 管理的其他應用程式時，即可在不需輸入認證的情況下，讓 Managed Browser 存取受 Azure AD 保護的公司網站。 這項功能適用於 Outlook Web Access (OWA) 和 SharePoint Online 等網站，以及透過 Azure App Proxy 存取的內部網路資源等其他公司網站。

### <a name="troubleshoot-enrollment-issues------746324----"></a>對註冊問題進行疑難排解  <!--- 746324 --->  
[疑難排解] 工作區會顯示使用者註冊問題。 其中包含問題的詳細資料與建議的補救步驟，可協助系統管理員和技術服務人員針對相關問題進行疑難排解。 未擷取特定註冊問題，某些錯誤可能也沒有補救建議。

### <a name="admins-can-now-configure-the-firewall-settings-on-a-device-using-a-device-configuration-profile----951708---"></a>系統管理員現在可以使用裝置組態設定檔來設定裝置的防火牆設定 <!-- 951708 -->   
系統管理員可以開啟裝置的防火牆，並針對網域、私用網路和公用網路設定各種通訊協定。  您可以在 "Endpoint Protection" 設定檔中找到這些防火牆設定。

### <a name="windows-defender-application-guard-helps-protect-devices-from-untrusted-websites-as-defined-by-your-organization----958257---"></a>Windows Defender 應用程式防護可依據組織的定義，協助保護裝置避免不受信任網站的威脅 <!-- 958257 -->   
系統管理員可以使用 Windows 資訊保護工作流程，或裝置設定下方的全新「網路界限」設定檔，將網站定義為「受信任」網站或「公司」網站。 如果網站未列在 64 位元 Windows 10 裝置受信任的網路界限中，而您使用 Microsoft Edge 來檢視，則系統會改為在 Hyper-V 虛擬電腦的瀏覽器中開啟。

您可以在 "Endpoint Protection" 設定檔的裝置組態設定檔中，找到應用程式防護。 系統管理員可以從該處設定虛擬瀏覽器和主機電腦之間的互動、不受信任的網站和信任網站之間的互動，並儲存虛擬瀏覽器中產生的資料。 若要在裝置上使用應用程式防護，您必須先設定網路界限。 每部裝置都只能定義一個網路界限。  

### <a name="windows-defender-application-guard-on-windows-10-enterprise-provides-mode-to-trust-only-authorized-apps----1031096---"></a>Windows 10 企業版的 Windows Defender 應用程式防護具有僅信任已獲授權應用程式的模式 <!-- 1031096 -->    
每天有高達數千種的惡意檔案流竄出來，單純使用防毒特徵偵測來對抗惡意程式碼時，可能再也無法有效抵禦新的攻擊。 使用 Windows 10 企業版的 Windows Defender 應用程式防護時，您可以將裝置設定的模式，從信任防毒軟體或其他安全性解決方案未封鎖的應用程式，變更為讓作業系統僅信任獲得企業授權的應用程式。 您可以將 Windows Defender 應用程式防護中的應用程式指派為信任。

使用 Intune 時，您可以在「僅限稽核」模式或「強制執行」模式中設定應用程式控制原則。 在「僅限稽核」模式中執行時，不會封鎖應用程式。 「僅限稽核」模式會在本機用戶端記錄檔中記錄所有事件。 您也可以設定是否只允許執行 Windows 元件和 Windows 市集應用程式，或允許依據智慧型安全性圖表的定義，執行評價良好的其他應用程式。

### <a name="new-enrollment-status-page-for-windows-10-enrollments---1063201--"></a>Windows 10 註冊的全新註冊狀態頁面 <!--1063201-->    
現在，您可以設定要在使用者註冊 Windows 10 裝置時顯示的問候語。 請使用**註冊狀態畫面**，設定要在使用者註冊 Windows 10 裝置時顯示的自訂訊息和超連結。  **註冊狀態畫面**亦可讓使用者檢視要套用到其裝置的原則設定進度。  

### <a name="window-defender-exploit-guard-is-a-new-set-of-intrusion-prevention-capabilities-for-windows-10----1063615---"></a>Window Defender 惡意探索防護是 Windows 10 的全新入侵偵測功能 <!-- 1063615 -->   
Window Defender 惡意探索防護包含自訂規則，可降低擅用應用程式的可能性、避免巨集和指令碼的威脅、自動封鎖評價不良的 IP 位址網路連線，並協助資料抵禦勒索軟體和未知的威脅。 Window Defender 惡意探索防護是由下列元件所組成：

- **降低攻擊介面 (ASR)** 提供的規則可讓您避免巨集、指令碼和電子郵件的威脅。
- **控制存取資料夾**會自動封鎖對受保護資料夾內容的存取。
- **網路篩選**會封鎖任何應用程式與評價不良 IP/網域的輸出連線。
- **惡意探索保護**可提供記憶體限制、控制流程限制和原則限制，以用來保護應用程式不受惡意探索的威脅。

### <a name="app-conditional-launch-support----1193313---"></a>支援條件式啟動應用程式 <!-- 1193313 -->
現在，IT 系統管理員可以透過 Azure 管理入口網站，設定在應用程式啟動時強制執行密碼，而不是透過行動裝置應用程式管理 (MAM) 的數字 PIN。 如上進行設定後，使用者就必須在出現提示時設定並使用密碼，才能存取啟用 MAM 的應用程式。 密碼的定義為數字 PIN 和至少一個特殊字元或大寫/小寫字母。 此版 Intune 將**僅在 iOS 上**啟用這項功能。 Intune 支援密碼的方式與數字 PIN 類似，它會設定長度下限，並允許重複的字元和順序。 這項功能需要應用程式的參與 (亦即， WXP、Outlook、Managed Browser、Yammer) 來就地整合 Intune APP SDK 與這項功能的程式碼，以在目標應用程式中強制執行密碼設定。

### <a name="app-version-number-for-line-of-business-in-device-install-status-report----1233999---"></a>裝置安裝狀態報告中的企業營運應用程式版本號碼 <!-- 1233999 -->  
裝置安裝狀態報告會顯示適用於 iOS 和 Android 的企業營運應用程式版本號碼。 您可以使用這些資訊來針對應用程式進行疑難排解，或找出執行過時應用程式版本的裝置。

### <a name="co-management-for-windows-10-devices-----124445---"></a>Windows 10 裝置的共同管理  <!-- 124445 -->
共同管理是一種可讓您從傳統管理過渡到現代化管理的解決方案，並提供您使用分段式方法的轉換過程。 本質上來說，共同管理解決方案可讓 Windows 10 裝置同時受 Configuration Manager 和 Microsoft Intune 管理，並聯結到 Active Directory (AD) 和 Azure Active Directory (Azure AD)。  如果您無法一次到位，此設定提供隨時間逐步實行現代化的轉換過程，讓您依據組織進展的步調來進行。  

### <a name="set-access-for-apps-by-minimum-android-security-patch-on-the-device---1278463---"></a>依據裝置的 Android 安全性修補程式下限，來設定應用程式的存取權<!-- 1278463 -->   
系統管理員可以定義裝置必須安裝的 Android 安全性修補程式下限，才能以受管理帳戶來存取受管理的應用程式。

> [!Note]  
> 這項功能只能限制 Android 6.0+ 裝置上由 Google 發行的安全性修補程式。

### <a name="new-device-restriction-settings-for-windows-10---------1308850---"></a>Windows 10 的新裝置限制設定      <!-- 1308850 -->
-    傳訊 (僅限行動裝置) - 停用測試或 MMS 訊息
-    密碼 - 可啟用 FIPS 和使用 Windows Hello 次要裝置以進行驗證的設定 
-    顯示 - 可開啟或關閉舊版應用程式 GDI 縮放比例的設定


### <a name="windows-10-kiosk-mode-device-restrictions----1308872---"></a>Windows 10 Kiosk 模式的裝置限制 <!-- 1308872 -->   
您可以將 Windows 10 裝置使用者限制在 Kiosk 模式中，讓他們只能使用一組預先定義的應用程式。  若要這樣做，請建立 Windows 10 裝置限制設定檔，然後進行 Kiosk 設定。

Kiosk 模式支援兩種模式：**單一應用程式** (只允許使用者執行一個應用程式) 或**多重應用程式** (允許存取一組應用程式)。  您可定義使用者帳戶和裝置名稱，以決定支援的應用程式。  當使用者登入時，就只能使用定義的應用程式。  若要進一步了解，請參閱 [AssignedAccess CSP](https://docs.microsoft.com/windows/client-management/mdm/assignedaccess-csp)。 

Kiosk 模式具有下列要求：

- Intune 必須為 MDM 授權單位。
- 目標裝置上必須已安裝應用程式。
- 裝置必須[已正確佈建](https://docs.microsoft.com/windows/configuration/set-up-a-kiosk-for-windows-10-for-desktop-editions)。

### <a name="new-device-configuration-profile-for-creating-network-boundaries----1311967---"></a>可建立網路界限的新裝置組態設定檔 <!-- 1311967 -->   
我們已在其他裝置組態設定檔的相同位置，建立名為**網路界限**的裝置組態設定檔。 您可以使用這個設定檔，將線上資源定義為公司資源和受信任的資源。 您必須先定義裝置的網路界限之後，裝置才可以使用 Windows Defender 應用程式防護和 Windows 資訊保護等功能。 每部裝置都只能定義一個網路界限。

您可以定義要信任的企業雲端資源、IP 位址範圍和內部 Proxy 伺服器。 定義好之後，Windows Defender 應用程式防護和 Windows 資訊保護等其他功能才可以使用網路界限。

###  <a name="two-additional-settings-for-windows-defender-antivirus----1338409---"></a>Windows Defender 防毒軟體的兩個其他設定 <!-- 1338409 -->  
**檔案封鎖層級**

| | |
|---|---|
| 尚未設定 | [尚未設定] 會使用預設的 Windows Defender 防毒軟體封鎖層級，並提供強式偵測，而不會增加偵測合法檔案的風險。 |
| 高 | [高] 適用於強力偵測層級。
| 高 +  | [高 +] 可提供 [高] 層級與額外的保護措施，但可能會影響用戶端效能。
| 零容錯  | [零容錯] 會封鎖所有未知的可執行檔。 |

雖然可能性很低，但設定為 [高] 有可能會導致部分合法檔案受到偵測。
建議您將檔案封鎖層級設為預設值 [尚未設定]。

**延長掃描檔案的逾時 (依雲端)**  

| | |
|--|--|
| 秒數 (0-50) | 指定 Windows Defender 防毒軟體在封鎖檔案前應等候雲端結果的時間上限。 預設時間量為 10 秒：此處所指定的任何額外時間 (最多 50 秒) 均會加上預設的 10 秒。 在大部分情況下，掃描需要的時間遠比最大值少很多。 延長的時間可讓雲端徹底調查可疑的檔案。 建議您啟用此設定，並至少多指定 20 秒。 |


### <a name="support-for-symantec-cloud-certification-authority-ca-----1333638---"></a>支援 Symantec 雲端憑證授權單位 (CA)  <!-- 1333638 -->    
Intune 現在支援 Symantec 雲端 CA，因此 Intune 憑證連接器可將來自 Symantec 雲端 CA 的 PKCS 憑證簽發給受 Intune 管理的裝置。 如果您已經使用 Intune 憑證連接器與 Microsoft 憑證授權單位 (CA)，可利用現有的 Intune 憑證連接器安裝程式來新增 Symantec CA 支援。


### <a name="improvements-to-device-setup-workflow-in-company-portal---1490692--"></a>對公司入口網站之裝置安裝工作流程的改善 <!--1490692-->  
我們正著手改善 Android 版公司入口網站應用程式中的裝置安裝工作流程。 我們會採用您公司專屬的語言、對使用者來說更簡單明瞭，並盡量將可以合併的畫面合併。 

### <a name="block-unsupported-samsung-knox-device-activation------1490695----"></a>封鎖不支援的 Samsung Knox 裝置啟用 <!--- 1490695 --->  
公司入口網站應用程式僅會在 MDM 註冊期間嘗試啟用 Samsung KNOX (如果[支援的 KNOX 裝置清單](https://www.samsungknox.com/knox-supported-devices/knox-workspace)中包含該裝置的話)。 這項限制有助於避免 KNOX 啟用錯誤而導致 MDM 註冊失敗。 如果裝置不支援 Samsung KNOX 啟用，則會註冊為標準 Android 裝置。 有些 Samsung 裝置型號可能支援 KNOX，而有些不支援。 在您購買及部署 Samsung 裝置之前，請先跟裝置轉銷商確認 Knox 相容性。

下列清單中的 Samsung 裝置型號不支援 KNOX，因此 Android 版公司入口網站應用程式會將其註冊為原生 Android 裝置：

| **裝置名稱** | **裝置型號** |
| --- | --- |
| Galaxy A3 | SM-A300G<br>SM-A310Y<br>SM-A320FL |
| Galaxy A5 | SM-A500G |
| Galaxy Alpha | SM-G850M |
| Galaxy Avant | SM-G386T |
| Galaxy C9/C9 Pro | SM-C900F |
| Galaxy Core 2/Core 2 Duos | SM-G355H<br>SM-G355M |
| Galaxy Core Lite | SM-G3588V |
| Galaxy Core Prime | SM-G360H |
| Galaxy Core LTE | SM-G386F<br>SM-G386W |
| Galaxy Grand | GT-I9082L<br>GT-I9082<br>GT-I9080L |
| Galaxy Grand 3 | SM-G7200 |
| Galaxy Grand Neo | GT-I9060I |
| Galaxy Grand Prime | SM-G530M |
| Galaxy Grand Prime Value Edition | SM-G531H |
| Galaxy J Max | SM-T285YD |
| Galaxy J1 | SM-J100H<br>SM-J100M<br>SM-J100ML |
| Galaxy J1 Ace | SM-J110F<br>SM-J110H |
| Galaxy J1 Mini | SM-J105M |
| Galaxy J2/J2 Pro | SM-J200H<br>SM-J210F |
| Galaxy J3 | SM-J320F<br>SM-J320FN<br>SM-J320H<br>SM-J320M<br>SM-J320W8 |
| Galaxy J5 | SM-J500G |
| Galaxy J7 | SM-J710F |
| Galaxy J7 Prime | SM-J727T1 |
| Galaxy K Zoom | SM-C115 |
| Galaxy Light | SGH-T399N |
| Galaxy Note 3 | SM-N9002<br>SM-N9009 |
| Galaxy Note 5 | SM-N920G<br>SM-N920I<br>SM-N920W8 |
| Galaxy Note 7/Note 7 Duos | SM-N930S<br>SM-N9300<br>SM-N930F<br>SM-N930T<br>SM-N9300<br>SM-N930F<br>SM-N930S<br>SM-N930T |
| Galaxy Note 10.1 3G | SM-P602 |
| Galaxy NotePRO 12.2&quot; | SM-P902 |
| Galaxy On5 | SM-G570MSM-G570Y |
| Galaxy On7 | SM-G600FY<br>SM-G610M<br>SM-G610Y |
| Galaxy S2 Plus | GT-I9105P |
| Galaxy S3 Mini | SM-G730A<br>SM-G730V |
| Galaxy S3 Neo | GT-I9300<br>GT-I9300I |
| Galaxy S4 | SM-S975L |
| Galaxy S4 Active | GT-I9295 |
| Galaxy S4 Neo | SM-G318ML |
| Galaxy S5 | SM-G9006W<br>SM-G900M |
| Galaxy S5 Neo | SM-G903M |
| Galaxy S6 Edge | 404SCSM-G925I<br>SM-G928G |
| Galaxy Tab A 7.0&quot; | SM-T280SM-T285 |
| Galaxy Tab A 9.7&quot; | SM-P555M |
| Galaxy Tab 3 7&quot;/Tab 3 Lite 7&quot; | SM-T116SM-T210SM-T211 |
| Galaxy Tab 3 8.0&quot; | SM-T311 |
| Galaxy Tab 3 10.1&quot; | GT-P5200<br>GT-P5210<br>GT-P5220 |
| Galaxy Trend 2 Lite | SM-G318H |
| Galaxy V Plus | SM-G318HZ |
| Galaxy Young 2 Duos | SM-G130BU |


### <a name="citrix-vpn-added-for-windows-10-devices----1512457---"></a>為 Windows 10 裝置新增 Citrix VPN <!-- 1512457 -->  
客戶能夠設定其 Windows 10 裝置的 Citrix VPN。 設定 Windows 10 和更新版本的 VPN 時，您可以在 [基本 VPN] 刀鋒視窗的 [選取連線類型] 清單中，選擇 Citrix VPN。

> [!Note]
> iOS 和 Android 中已有 Citrix 設定。





<!-- the following are present prior to 1710 -->

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
您可以在上傳大量採購方案 (VPP) 權杖時，設定 VPP 的國家/地區市集。 Intune 會從指定的 VPP 國家/地區市集同步處理所有地區設定的 VPP 應用程式。

> [!NOTE]  
> 目前 Intune 只會從符合 Intune 地區設定 (建立 Intune 租用戶所在位置) 的 VPP 國家/地區市集同步處理 VPP 應用程式。

###  <a name="update-ios-vpp-user-and-device-licensed-apps-----1305564---"></a>更新 iOS VPP 使用者和裝置授權的應用程式 <!-- 1305564 -->  
您可以透過 Intune 服務，設定 iOS VPP 權杖以更新為該權杖所購買的全部應用程式。 Intune 會偵測應用程式市集內的 VPP 應用程式更新，並在裝置簽入時將更新自動推送至裝置。

### <a name="new-settings-for-windows-10-team-device-restriction-profile------1308838----"></a>適用於 Windows 10 團隊版裝置限制設定檔的新設定 <!--- 1308838  -->
我們會新增許多設定到 Windows 10 團隊版裝置限制設定檔，以協助您控制 Surface Hub 裝置。
如需此設定檔的詳細資訊，請參閱 [Windows 10 團隊版裝置限制設定](device-restrictions-windows-10-teams.md)。

### <a name="support-for-windows-10-edition-upgrade-policy------903672archived-1119689---"></a>支援 Windows 10 版本升級原則 <!-- 903672(archived), 1119689 -->  
您可以建立 Windows 10 版本升級原則，以將 Windows 10 裝置升級為 Windows 10 教育版、Windows 10 教育版 N、Windows 10 專業版、Windows 10 專業版 N、Windows 10 專業教育版和 Windows 10 專業教育版 N。如需 Windows 10 版本升級的詳細資料，請參閱[如何設定 Windows 10 版本升級](edition-upgrade-configure-windows-10.md)。

### <a name="remote-support-for-windows-and-windows-mobile-devices-----1070473---"></a>適用於 Windows 和 Windows Mobile 裝置的遠端支援 <!-- 1070473 -->    
Intune 將可使用 [TeamViewer](https://www.teamviewer.com) 軟體 (需另行購買)，讓您為執行 Windows 和 Windows Mobile 裝置的使用者提供遠端協助。

### <a name="scan-devices-with-windows-defender----1280988--1280990-----"></a>使用 Windows Defender 掃描裝置 <!-- 1280988  1280990   -->
您可以在受管理的 Windows 10 裝置上，使用 Windows Defender 防毒軟體來執行「快速掃描」、「完整掃描」，和「更新簽章」。 從裝置的概觀刀鋒視窗，選擇要在裝置上執行的動作。 系統會提示您確認動作，然後命令才會傳送到裝置。 

**快速掃描**：快速掃描會查看惡意程式碼註冊啟動的位置，例如登錄機碼和已知的 Windows 啟動資料夾。 快速掃描平均會花費五分鐘。 快速掃描與 [隨時開啟即時保護] 設定 (可在檔案開啟、關閉，以及使用者每次瀏覽資料夾時掃描檔案) 結合時，可提供保護以防禦潛藏於系統或核心的惡意程式碼。 掃描完成時，使用者可在其裝置上查看掃描結果。 

**完整掃描**：完整掃描對於已遭遇惡意程式碼威脅的裝置非常實用，可找出是否有任何需要進一步完整清理的尚未作用元件，且適合執行隨選掃描。 完整掃描可能需要一個小時來進行。 掃描完成時，使用者可在其裝置上查看掃描結果。 

**更新簽章**：更新簽章命令會更新 Windows Defender 防毒軟體的惡意程式碼定義和簽章。 這有助於確保 Windows Defender 防毒軟體能有效偵測惡意程式碼。 這項功能僅適用於 Windows 10 裝置，且需要裝置的網際網路連線。 

### <a name="bitlocker-device-configuration----1397398---"></a>BitLocker 裝置設定 <!-- 1397398 -->  
[Windows 加密] > [基本設定] 將會納入新的 [其他磁碟加密的警告] 設定，讓您停用使用者裝置上可能正在使用的其他磁碟加密[警告提示](https://docs.microsoft.com/en-us/windows/client-management/mdm/bitlocker-csp#allowarningforotherdiskencryption) \(英文\)。  使用者必須先同意警告提示，系統才會在裝置上設定 BitLocker；使用者尚未確認之前，均會封鎖 BitLocker 設定。  新的設定會停用使用者警告。

### <a name="company-portal-for-windows-81-and-windows-phone-81-moving-to-sustaining-mode---1428681--"></a>Windows 8.1 和 Windows Phone 8.1 版公司入口網站移至維持模式 <!--1428681-->
自 2017 年 10 月起，Windows 8.1 和 Windows Phone 8.1 公司入口網站應用程式將會移至維持模式。 這表示這些平台將會繼續支援應用程式和現有的案例 (例如註冊和合規性)。 這些應用程式仍可透過現有的發行通道 (例如 Microsoft 市集) 下載取得。 

一旦進入維持模式，這些應用程式就僅會接收重大安全性更新。 但是，將不會針對這些應用程式發行額外的更新或功能。 如需新功能，建議您將裝置更新為 Windows 10 或 Windows 10 行動裝置版。 

###  <a name="block-copy-and-paste-between-work-and-personal-profiles-in-android-for-work----1098994---"></a>封鎖 Android for Work 中工作和個人設定檔間的複製和貼上 <!-- 1098994 -->   
您可以將 Android for Work 的工作設定檔設定為封鎖工作和個人應用程式間的複製和貼上。 您可以在 [工作設定檔設定] 中，於 [Android for Work] 平台的 [裝置限制] 設定檔內找到這項新設定。

### <a name="new-behaviors-for-the-company-portal-app-for-android-with-work-profiles----1485783---"></a>Android 公司入口網站應用程式使用工作設定檔的新行為 <!---1485783--->
當您使用工作設定檔註冊 Android for Work 裝置時，是由工作設定檔中的公司入口網站應用程式來執行裝置上的管理工作。 除非您使用個人設定檔中啟用 MAM 的應用程式，否則 Android 公司入口網站應用程式不再有任何用途。 為了改善工作設定檔的體驗，Intune 會在成功註冊工作設定檔後，自動隱藏個人的公司入口網站應用程式。

您可以隨時啟用個人設定檔中的 Android 公司入口網站應用程式，方法是瀏覽 [Play Store 中的公司入口網站](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal)，然後點選 [啟用]。

### <a name="intune-mam--outlook-for-android-add-ins-----1450688---"></a>Intune MAM 和 Android 版 Outlook 的增益集 <!-- 1450688 -->
在未來幾週，Office 小組將會宣布適用於 Android 版 Outlook 的增益集。 此增益集功能集現已存在於 Windows、iOS，Web 和 Mac 版 Outlook 中。 因為增益集是透過 Exchange 管理，除非 Exchange 系統管理員關閉增益集的存取功能，否則使用者將能夠在 Outlook 和未受管理的增益集應用程式之間複製並共用資料和郵件。 

若要管理使用者的增益集存取權限，請與您的 Exchange 系統管理員合作，確保 MAM 資料保護原則套用至增益集。

#### <a name="how-does-this-affect-me"></a>此變更對我造成什麼影響？
如果您的 Exchange 原則已設定為防止側載增益集或安裝增益集，則無需繼續閱讀。 您的 MAM 原則將會如預期套用。 不過，如果您已在 MAM 中設定原則以限制 Android 版 Outlook 中的剪下、複製和貼上操作，而並未在 Exchange 中設定增益集原則，您應該了解使用者預設將能夠安裝增益集至 Outlook。 這些增益集可以存取郵件內文、主旨和其他的郵件屬性。 您可以請 Exchange 系統管理員移除「我的市集應用程式」和「我的自訂應用程式」角色，即可關閉讓使用者安裝增益集的功能。

Exchange 中的設定變更將會套用至 Windows、iOS、Web、Mac 和行動裝置版 Outlook。 

#### <a name="what-do-i-need-to-do"></a>我需要做什麼？
檢閱您目前的 Exchange 原則。 通知您的 IT 和技術服務人員。 如有任何問題或疑慮，請連絡我們的支援小組。 

### <a name="user-device-association-entity-collection-added-to-intune-data-warehouse-data-model----1187917---"></a>使用者裝置關聯實體集合已新增至 Intune 資料倉儲資料模型 <!-- 1187917 -->
您可以使用使用者裝置關聯資訊 (關聯使用者和裝置實體集合) 來建立報表和資料視覺效果。 資料模型的存取可透過擷取自資料倉儲 Intune 頁面的 Power BI 檔案 (PBIX)、透過 OData 端點，或開發自訂用戶端來存取。




<!-- the following are present prior to 1709 -->

### <a name="actions-for-non-compliance----730266--846515---"></a>非合規性動作 <!--730266  846515 -->     
「非合規性動作」是合規性政策的新功能，可讓您對不符合規範的裝置採取動作。 您可以指定單一或多個動作，並指定必須進行這些動作的時間週期。 例如，您可以在裝置變成不相容之後透過電子郵件立即通知使用者有不相容的裝置，也可以在 3 天寬限期之後透過條件式存取封鎖不相容的裝置存取公司資源。

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

### <a name="on-premises-exchange-connector-high-availability-support-----676614---"></a>內部部署 Exchange Connector 高可用性支援<!-- 676614 -->   
內部部署 Exchange Connector 可以有多個用戶端存取伺服器 (CAS) 角色。 例如，如果主要的 CAS 失敗，則 Exchange Connector 就會收到切換回其他 CAS 的查詢。 這項功能可確保服務不中斷。

### <a name="system-center-operations-manager-management-pack-for-exchange-connector----885457---"></a>適用於 Exchange connector 的 System Center Operations Manager 管理組件<!-- 885457 -->   
適用於 Exchange Connector 的 System Center Operations Manager 管理組件將可協助您剖析 Exchange Connector 記錄。 此管理組件可在您需要針對問題進行疑難排解時，為您提供不同方式來監視 Intune。


### <a name="end-of-support-for-android-43-and-lower----1171127-1326920----"></a>結束對 Android 4.3 和較舊版本的支援<!---1171127, 1326920 --->
受管理的應用程式和 Android 公司入口網站應用程式需要 Android 4.4 及更新版本才能存取公司資源。 10 月初前未更新的裝置將不再能存取公司入口網站或這些應用程式。 今年 12 月會強制淘汰所有已註冊的裝置，以致無法存取公司資源。 如果您使用不含 MDM 的應用程式保護原則，應用程式就不會接收更新，其體驗品質會隨著時間而降低。


## <a name="intune-apps"></a>Intune 應用程式

### <a name="improved-guidance-around-the-request-for-access-to-contacts-on-android-devices---1484985--"></a>改善在 Android 裝置上要求存取連絡人的相關指引 <!--1484985-->   
Android 版公司入口網站應用程式通常會要求使用者接受「連絡人」權限。 如果使用者拒絕此存取權，系統會顯示應用程式內通知，提醒他們授與此權限以進行條件式存取。

### <a name="secure-startup-remediation-for-android---1490712--"></a>Android 的安全啟動修復 <!--1490712-->     
如果使用者是使用 Android 裝置，可以點選公司入口網站應用程式中的不相容原因。 如此一來，系統會盡可能將使用者直接移至設定應用程式的正確位置，以修正問題。


### <a name="redirecting-macos-users-to-our-new-company-portal-app---1380728--"></a>將 macOS 使用者重新導向至新的公司入口網站應用程式 <!--1380728-->   
當使用者登入公司入口網站，並註冊 macOS 裝置時，系統會指示他們下載 macOS 版的新公司入口網站應用程式以 完成程序。 使用 OS X El Capitan 10.11 或更新版本的 macOS 裝置會發生這種情況。 

### <a name="certificate-based-authentication-support-on-the-company-portal-for-ios---1029830--"></a>支援 iOS 版公司入口網站的憑證式驗證 <!--1029830-->
我們已新增支援 iOS 版公司入口網站應用程式的憑證式驗證 (CBA)。 使用 CBA 的使用者可輸入其使用者名稱，然後點選 [Sign in with a certificate] (使用憑證登入) 連結。 Android 和 Windows 版公司入口網站應用程式已支援 CBA。 若要深入了解，請參閱[登入公司入口網站應用程式](https://docs.microsoft.com/intune-user-help/sign-in-to-the-company-portal)頁面。

<!-- the following are present prior to 1710 -->

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

<!-- the following are present prior to 1709 -->

### <a name="intune-managed-browser-support-for-ios-and-android----1374196---"></a>iOS 和 Android 的 Intune Managed Browser 支援 <!-- 1374196 -->
自 2017 年 10 月起，Android 應用程式上的 Intune Managed Browser 應用程式只會支援執行 Android 4.4 和更新版本的裝置。 iOS 上的 Intune Managed Browser 應用程式只支援執行 iOS 9.0 及更新版本的裝置。 較舊版本的 Android 和 iOS 能夠繼續使用 Managed Browser，但是無法安裝新版的應用程式，而且可能無法存取所有的應用程式功能。 建議您將這些裝置更新為受支援的作業系統版本。


### <a name="improved-error-message-for-when-a-user-reaches-the-maximum-number-of-devices-allowed-to-enroll----1270370---"></a>改進使用者達到允許註冊的裝置數目上限時的錯誤訊息 <!-- 1270370 -->
終端使用者不會看到一般錯誤訊息，而是會看到實用且可採取動作的錯誤訊息：「您已註冊 IT 系統管理員所允許的裝置數目上限。請移除已註冊的裝置，或向您的 IT 系統管理員取得協助。」




## <a name="notices"></a>通知

### <a name="device-and-app-management-integration----677972---"></a>裝置與應用程式管理整合 <!-- 677972 -->   
Intune 早已開始整合應用程式和裝置管理的 IT 系統管理員體驗；現在，Intune 的行動裝置管理 (MDM) 與行動應用程式管理 (MAM) 都可從 Azure 入口網站存取。 這些變更都是為了簡化您的裝置和應用程式管理體驗。

如需深入了解已宣布的 MDM 和 MAM 變更，請參閱 [Intune 支援小組部落格](https://blogs.technet.microsoft.com/intunesupport/2017/09/19/support-tip-setting-up-communication-between-mam-managed-and-mdm-managed-apps/)。

### <a name="apple-to-require-updates-for-application-transport-security---748318--"></a>Apple 要求必須更新 Application Transport Security <!--748318-->   
Apple 宣布，從 2017 年春季開始，將會強制執行 Application Transport Security (ATS) 的特定需求。 ATS 可用來對透過 HTTPS 進行的所有應用程式通訊，強制執行更嚴格的安全性。 此變更會影響使用 iOS 公司入口網站應用程式的 Intune 客戶。 如需詳細資訊，請檢閱我們的 [Intune 支援部落格](https://aka.ms/compportalats)。


### <a name="new-path-for-managed-devices-in-graph-api----1586728---"></a>Graph API 中受管理裝置的新路徑 <!-- 1586728 -->  
在 10 月的 Intune 服務版本中，我們針對 Graph API 搶鮮版 (Beta) 中用來存取受管理裝置的路徑進行了變更。

| | |
|--|--|
| 目前的路徑 |  https://graph.microsoft.com/beta/managedDevices |
| 新的路徑 | https://graph.microsoft.com/beta/deviceManagement/managedDevices |

在 10 月期間，這兩個路徑都能運作。 但在 10 月的服務版本之後，就只能使用新的路徑。  如果您使用 Graph API 來存取受管理的裝置，請使用新路徑來更新並驗證您的指令碼和應用程式。 如需了解其他變更，請查看每月的 [Graph API 變更記錄](https://developer.microsoft.com/en-us/graph/docs/concepts/changelog)。

### <a name="see-also"></a>請參閱
如需近期發展的詳細資料，請參閱 [Microsoft Intune 的新功能](whats-new.md)。

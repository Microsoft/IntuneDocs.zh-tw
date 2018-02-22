---
title: "幾個月前的 Microsoft Intune 新功能"
titlesuffix: Azure portal
description: "檢閱 Intune 新功能頁面中較舊的公告"
keywords: 
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/19/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9ba01d60-4a03-4e3e-9aba-8be905c0054c
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: f9022f1e9f30d4a64608d2d8588c794a07c41f24
ms.sourcegitcommit: a6fd6b3df8e96673bc2ea48a2b9bda0cf0a875ae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2018
---
# <a name="whats-new-in-the-microsoft-intune---previous-months"></a>Microsoft Intune 的新功能 - 前幾個月

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

## <a name="october-2017"></a>2017 年 10 月

### <a name="ios-and-android-line-of-business-app-version-number-is-visible----1380712---"></a>顯示 iOS 和 Android 的企業營運應用程式版本號碼<!-- 1380712 -->

Intune 的應用程式現在會顯示 iOS 和 Android 的企業營運應用程式版本號碼。 此號碼會顯示在 Azure 入口網站的應用程式清單及 [應用程式概觀] 刀鋒視窗中。 使用者可以在公司入口網站應用程式及入口網站中看到應用程式號碼。

__完整版本號碼__ 完整的版本號碼可識別特定的應用程式版本。 此號碼會顯示為_版本_(_組建_)。 例如，2.2(2.2.17560800)

完整的版本號碼有兩個部分：

 - **版本**  
   版本號碼是人類可讀的應用程式版本號碼。 可供使用者識別不同的應用程式版本。

 - **組建編號**  
    組建編號是內部編號，用於偵測應用程式與以程式設計方式管理應用程式。 組建編號是指參考程式碼變更的應用程式反覆項目。

深入了解版本號碼及開發企業營運應用程式，請參閱[開始使用 Microsoft Intune App SDK](app-sdk-get-started.md#line-of-business-app-version-numbers)。

### <a name="device-and-app-management-integration----677972---"></a>裝置與應用程式管理整合 <!-- 677972 -->   
Intune 早已開始整合應用程式和裝置管理的 IT 系統管理員體驗；現在，Intune 的行動裝置管理 (MDM) 與行動應用程式管理 (MAM) 都可從 Azure 入口網站存取。 這些變更都是為了簡化您的裝置和應用程式管理體驗。

如需深入了解已宣布的 MDM 和 MAM 變更，請參閱 [Intune 支援小組部落格](https://blogs.technet.microsoft.com/intunesupport/2017/09/19/support-tip-setting-up-communication-between-mam-managed-and-mdm-managed-apps/)。

### <a name="new-enrollment-alerts-for-apple-devices----1471790---"></a>Apple 裝置的新註冊警示 <!-- 1471790 -->
註冊的 [概觀] 頁面會顯示對 IT 管理員極有幫助，有關 Apple 裝置管理的警示。 在下列情況中 [概觀] 頁面會顯示警示：Apple MDM Push Certificate 即將到期或已過期時、裝置註冊計劃權杖即將到期或已過期時、裝置註冊計劃中有未指派的裝置時。

### <a name="support-token-replacement-for-app-configuration-without-device-enrollment----1080364---"></a>支援在不註冊裝置的情況下替換應用程式設定 <!-- 1080364 -->

您可以在未註冊裝置的應用程式中，使用應用程式設定的動態值權杖。 如需詳細資訊，請參閱[在不註冊裝置的情況下新增受管理應用程式的應用程式設定原則](app-configuration-policies-managed-app.md)。

### <a name="updates-to-the-company-portal-app-for-windows-10---1299474--"></a>Windows 10 版公司入口網站應用程式的更新 <!--1299474-->
Windows 10 版「公司入口網站」應用程式中的 [設定] 頁面已更新，以使設定和預期的使用者動作在所有設定中更加一致。 它也已更新為符合其他 Windows 應用程式的配置。 您可以在 [應用程式 UI 中的新增功能](whats-new-app-ui.md) 頁面中找到之前/之後影像。

### <a name="inform-end-users-what-device-information-can-be-seen-for-windows-10-devices---1337920--"></a>通知終端使用者可看到哪些 Windows 10 裝置資訊 <!--1337920-->
我們在 Windows 10 版公司入口網站應用程式的 [裝置詳細資料] 畫面新增了 [擁有權類型]。 如此一來，使用者就能夠直接從 Intune 終端使用者文件的此頁面，了解有關隱私權的更多資訊。他們也能夠在 [關於] 畫面上找到此資訊。

### <a name="feedback-prompts-for-the-company-portal-app-for-android---1165249--"></a>Android 版公司入口網站應用程式的意見反應提示 <!--1165249-->
Android 版公司入口網站應用程式現在會要求使用者意見反應。 此意見反應將直接傳送給 Microsoft，並讓使用者有機會在公開的 Google Play 商店中檢閱應用程式。 意見反應並不是必要的，可以輕鬆地關閉，讓使用者可以繼續使用應用程式。

<!-- #### Update to what device details an organization can see 1616825
The Company Portal app for Android can now use geofencing to protect access to company resources. It uses network details such as IP address, default gateway address, and Domain Name System (DNS) to determine whether to allow access to protected company resources.-->

### <a name="helping-your-users-help-themselves-with-the-company-portal-app-for-android----1573324-1573150-1558616-1564878---"></a>協助您的使用者自助使用適用於 Android 的公司入口網站應用程式 <!-- 1573324, 1573150, 1558616, 1564878 -->

Android 版公司入口網站應用程式新增了終端使用者指示，能幫助他們了解，並盡可能自行解決新的使用案例。
- 如果終端使用者已經達到可新增裝置數目的上限，將會被引導至 [Azure Active Directory 入口網站](https://account.activedirectory.windowsazure.com/r/#/profile)以移除裝置。
- 有提供步驟協助終端使用者[修正 Samsung Knox 裝置的啟動錯誤](https://go.microsoft.com/fwlink/?linkid=859718)或[關閉省電模式](/intune-user-help/power-saving-mode-android)。 如果這些解決方案都無法解決他們的問題，我們會提供如何[向 Microsoft 提交記錄](/intune-user-help/send-logs-to-microsoft-android)的說明。

### <a name="new-resolve-action-available-for-android-devices----1583480---"></a>Android 裝置的新「解決」動作 <!-- 1583480 -->

Android 公司入口網站應用程式在 [更新裝置設定] 頁面中推出「解決」動作。 選取此選項會直接將使用者引導至造成裝置不相容的設定。 Android 版公司入口網站應用程式目前在[裝置密碼](/intune-user-help/set-your-pin-or-password-android)、[USB 偵錯](/intune-user-help/you-need-to-turn-off-usb-debugging-android)和[未知來源](/intune-user-help/you-need-to-turn-off-unknown-sources-android)設定支援此動作。

### <a name="device-setup-progress-indicator-in-android-company-portal----1565657---"></a>Android 版公司入口網站中的裝置設定進度列指示器 <!-- 1565657 -->
Android 版公司入口網站應用程式會顯示使用者註冊其裝置時的裝置設定進度列指示器。 指示器會顯示新的狀態，從「正在設定您的裝置...」開始，然後依序是「正在註冊您的裝置...」、「正在完成註冊您的裝置...」、「正在完成設定您的裝置...」。

### <a name="certificate-based-authentication-support-on-the-company-portal-for-ios---1029830--"></a>支援 iOS 版公司入口網站的憑證式驗證 <!--1029830-->
我們已新增支援 iOS 版公司入口網站應用程式的憑證式驗證 (CBA)。 使用 CBA 的使用者可輸入其使用者名稱，然後點選 [Sign in with a certificate] (使用憑證登入) 連結。 Android 和 Windows 版公司入口網站應用程式已支援 CBA。 若要深入了解，請參閱[登入公司入口網站應用程式](https://docs.microsoft.com/intune-user-help/sign-in-to-the-company-portal)頁面。

### <a name="apps-that-are-available-with-or-without-enrollment-can-now-be-installed-without-being-prompted-for-enrollment----1334712---"></a>需要或無須註冊而提供的應用程式現在可以直接安裝，而不會提示註冊。 <!-- 1334712 -->

在 Android 公司入口網站應用程式上需要或無需註冊才可使用的公司應用程式，現在皆已可安裝而不會提示需要註冊。

### <a name="windows-autopilot-deployment-program-support-in-microsoft-intune-----747617----"></a>Microsoft Intune 中的 Windows AutoPilot Deployment 方案支援<!-- 747617  -->
您可以現在使用 Microsoft Intune Windows AutoPilot 部署計劃，讓您的使用者能夠佈建其公司裝置而不需要 IT 介入。 您可以自訂全新體驗 (OOBE)，並引導使用者將他們的裝置加入 Azure AD 且在 Intune 中註冊。 搭配使用時，Microsoft Intune 和 Windows AutoPilot 不須部署、維護及管理作業系統映像。 如需詳細資料，請參閱 [Enroll Windows devices using Windows AutoPilot Deployment Program](https://docs.microsoft.com/intune/enrollment-autopilot) (使用 Windows AutoPilot Deployment 方案註冊 Windows 裝置)。

### <a name="quick-start-for-device-enrollment-----1425655---"></a>裝置註冊的快速入門  <!-- 1425655 --> 
快速入門現在提供於 [裝置註冊]，並提供管理平台和設定註冊程序的參考表格。 每個項目的簡短描述，以及文件連結和逐步指示，提供實用的文件來簡化開始使用。

### <a name="device-categorization----1427491---"></a>裝置分類 <!-- 1427491 -->
[裝置] > [概觀] 刀鋒視窗的註冊裝置平台圖，會依平台組織裝置，包括 Android、iOS、macOS、Windows 和 Windows Mobile。  執行其他作業系統的裝置會分組為「其他」。  這包括由 Blackberry、NOKIA 和其他廠商製造的裝置。  

若要了解您租用戶中的哪些裝置受到影響，請選擇 [管理] > [所有裝置]，然後使用 [篩選] 限制 [OS] 欄位。

### <a name="zimperium---new-mobile-threat-defense-partner------954681---"></a>Zimperium - 新的 Mobile Threat Defense 夥伴<!-- 954681 -->  
您可以根據由 Zimperium (與 Microsoft Intune 整合的 Mobile Threat Defense 解決方案) 所進行的風險評定，使用條件式存取來控制行動裝置對公司資源的存取。

#### <a name="how-integration-with-intune-works"></a>整合 Intune 如何運作
風險評估的依據是收集自執行 Zimperium 裝置的遙測。 您可以根據透過 Intune 裝置合規性政策啟用的 Zimperium 風險評估，設定 EMS 條件式存取原則。透過該原則，您可以根據偵測到的威脅來允許或封鎖不符合規範的裝置存取公司資源。

### <a name="new-settings-for-windows-10-device-restriction-profile------978575-1308849---"></a>適用於 Windows 10 裝置限制設定檔的新設定 <!--- 978575, 1308849, -->  
我們將為 Windows Defender SmartScreen 類別中的 Windows 10 裝置限制設定檔新增設定。

如需 Windows 10 裝置限制設定檔的詳細資料，請參閱 [Windows 10 及更新版本的裝置限制設定]( device-restrictions-windows-10.md)。

### <a name="remote-support-for-windows-and-windows-mobile-devices------1070473---"></a>適用於 Windows 和 Windows Mobile 裝置的遠端支援 <!-- 1070473 -->  
Intune 現在可使用 [TeamViewer](https://www.teamviewer.com) 軟體 (需另行購買)，讓您為執行 Windows 和 Windows Mobile 裝置的使用者提供遠端協助。

### <a name="scan-devices-with-windows-defender----1280988--1280990-----"></a>使用 Windows Defender 掃描裝置 <!-- 1280988  1280990   -->
您現在可以在受管理的 Windows 10 裝置上，使用 Windows Defender 防毒軟體來執行**快速掃描**、**完整掃描**，和**更新簽章**。 從裝置的概觀刀鋒視窗，選擇要在裝置上執行的動作。 系統會提示您確認動作，然後命令才會傳送到裝置。 

**快速掃描**：快速掃描會掃描惡意程式碼註冊要啟動的位置，例如登錄機碼和已知的 Windows 啟動資料夾。 快速掃描平均會花費五分鐘。 快速掃描與 [隨時開啟即時保護] 設定 (可在檔案開啟、關閉，以及使用者每次瀏覽資料夾時掃描檔案) 結合時，可提供保護以防禦潛藏於系統或核心的惡意程式碼。 掃描完成時，使用者可在其裝置上查看掃描結果。 

**完整掃描**：完整掃描對於已遭遇惡意程式碼威脅的裝置非常實用，可找出是否有任何需要進一步完整清理的尚未作用元件，且適合執行隨選掃描。 完整掃描可能需要一個小時來進行。 掃描完成時，使用者可在其裝置上查看掃描結果。 

**更新簽章**：更新簽章命令會更新 Windows Defender 防毒軟體的惡意程式碼定義和簽章。 這有助於確保 Windows Defender 防毒軟體能有效偵測惡意程式碼。 這項功能僅適用於 Windows 10 裝置，且需要裝置的網際網路連線。 

### <a name="the-enabledisable-button-is-removed-from-the-intune-certificate-authority-page-of-the-intune-azure-portal-----1400455---"></a>[啟用/停用] 按鈕從 Intune Azure 入口網站的 [Intune 憑證授權單位] 頁面移除  <!-- 1400455 -->
 我們正在消除設定 Intune 上憑證連接器的多餘步驟。 目前，您會下載憑證連接器，然後在 Intune 主控台中啟用它。 不過，如果您在 Intune 主控台中停用連接器，連接器會繼續發出憑證。

#### <a name="how-does-this-affect-me"></a>此變更對我造成什麼影響？
從 10 月開始，[啟用/停用] 按鈕不會再出現在 Azure 入口網站的 [憑證授權單位] 頁面上。 連接器功能將保持不變。 憑證仍會部署到在 Intune 中註冊的裝置。 您可以繼續下載並安裝憑證連接器。 若要停止發出憑證，您現在要解除安裝憑證連接器而非將它停用。

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>我需要為這項變更做什麼準備？
如果您目前已停用憑證連接器，您應該將它解除安裝。

### <a name="new-settings-for-windows-10-team-device-restriction-profile-------1308838---"></a>適用於 Windows 10 團隊版裝置限制設定檔的新設定 <!--- 1308838 -->
在此版本中，我們新增了許多設定到 Windows 10 團隊版裝置限制設定檔，以協助您控制 Surface Hub 裝置。

如需此設定檔的詳細資訊，請參閱 [Windows 10 團隊版裝置限制設定](device-restrictions-windows-10-teams.md)。

### <a name="prevent-users-of-android-devices-from-changing-their-device-date-and-time-----1333292---"></a>防止 Android 裝置的使用者變更其裝置的日期和時間 <!-- 1333292 -->
您可以使用 [Android 自訂裝置原則](custom-settings-android.md)來防止 Android 裝置使用者變更裝置的日期和時間。

若要這樣做，請設定 Android 自訂原則，將 URI ./Vendor/MSFT/PolicyManager/My/System/AllowDateTimeChange 設定為 **TRUE**，然後指派給所需的群組。

### <a name="bitlocker-device-configuration----1397398---"></a>BitLocker 裝置設定 <!-- 1397398 -->
[Windows 加密] > [基本設定] 包含新的 [其他磁碟加密的警告] 設定，讓您停用使用者裝置上可能正在使用的其他磁碟加密[警告提示](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp#allowarningforotherdiskencryption)。  警告提示會要求使用者同意，然後才會在裝置上設定 BitLocker，在使用者確認之前則會封鎖 BitLocker 設定。  新的設定會停用使用者警告。


### <a name="volume-purchase-program-for-business-apps-will-now-sync-to-your-intune-tenant----800882---"></a>企業大量採購方案應用程式現在將會同步到 Intune 租用戶 <!-- 800882 -->  
協力廠商開發人員可以私下將應用程式散發給 iTunes Connect 中所指定的授權企業大量採購方案 (VPP) 成員。 這些企業 VPP 成員可以登入大量採購方案 App Store，並購買其應用程式。

在此版本中，終端使用者所購買的企業 VPP 應用程式將開始與其 Intune 租用戶同步。

### <a name="select-apple-country-store-to-sync-vpp-apps-----1332311---"></a>選取 Apple 國家/地區市集以同步處理 VPP 應用程式 <!-- 1332311 -->  
上傳您的大量採購方案 (VPP) 權杖時，可以設定 VPP 的國家/地區市集。 Intune 會從指定的 VPP 國家/地區市集同步處理所有地區設定的 VPP 應用程式。

> [!NOTE]  
> 目前 Intune 只會從符合 Intune 地區設定 (建立 Intune 租用戶所在位置) 的 VPP 國家/地區市集同步處理 VPP 應用程式。


### <a name="block-copy-and-paste-between-work-and-personal-profiles-in-android-for-work----1098994---"></a>封鎖 Android for Work 中工作和個人設定檔間的複製和貼上 <!-- 1098994 -->
在此版本中，您可以將 Android for Work 的工作設定檔設定為封鎖工作和個人應用程式間的複製和貼上。 您可以在 [工作設定檔設定] 中，於 [Android for Work] 平台的 [裝置限制] 設定檔內找到這項新設定。

### <a name="create-ios-apps-limited-to-specific-regional-apple-app-stores----1281692---"></a>建立僅限於特定地區 Apple App Store 的 iOS 應用程式 <!-- 1281692 -->
您可以在 Apple App Store 受管理的應用程式建立期間，指定國家/地區的地區設定。

> [!Note]  
> 目前，您僅能建立出現在美國市集的 Apple App Store 受管理應用程式。

###  <a name="update-ios-vpp-user-and-device-licensed-apps-----1305564---"></a>更新 iOS VPP 使用者和裝置授權的應用程式 <!-- 1305564 -->  
您可以透過 Intune 服務，設定 iOS VPP 權杖以更新為該權杖所購買的全部應用程式。 Intune 會偵測應用程式市集內的 VPP 應用程式更新，並在裝置簽入時將更新自動推送至裝置。

如需設定 VPP 權杖並啟用自動更新的步驟，請參閱 [如何使用 Microsoft Intune 管理透過大量採購方案購買的 iOS 應用程式] (/intune/vpp-apps-ios)。


### <a name="user-device-association-entity-collection-added-to-intune-data-warehouse-data-model----1187917---"></a>使用者裝置關聯實體集合已新增至 Intune 資料倉儲資料模型 <!-- 1187917 -->
您現在可以使用使用者裝置關聯資訊 (關聯使用者和裝置實體集合) 來建立報表和資料視覺效果。 資料模型的存取可透過擷取自資料倉儲 Intune 頁面的 Power BI 檔案 (PBIX)、透過 OData 端點，或開發自訂用戶端來存取。

### <a name="review-policy-compliance-for-windows-10-update-rings----1067886---"></a>檢閱 Windows 10 更新通道的原則合規性 <!-- 1067886 -->
您可以從 [軟體更新] > [依更新通道別部署狀態] 來檢閱 Windows 10 更新通道的原則報告。 原則報告包括已設定更新通道的部署狀態。 

### <a name="new-report-that-lists-ios-devices-with-older-ios-versions------1352223---"></a>列出舊版 iOS 之 iOS 裝置的新報表   <!-- 1352223 -->
[軟體更新] 工作區提供 [過期的 iOS 裝置] 報表。 在此報表中，您可以檢視受監督的 iOS 裝置清單，這些是 iOS 更新原則之前鎖定並有可用更新的裝置。 針對每部裝置，您可以檢視狀態，以了解為何尚未自動更新裝置。 

### <a name="view-app-protection-policy-assignments-for-troubleshooting-----1475003---"></a>檢視應用程式保護原則指派以進行疑難排解 <!--  1475003 -->
在此即將發行的版本中，將會新增 [應用程式保護原則] 選項到疑難排解刀鋒視窗中提供的 [指派] 下拉式清單。 您現在可以選取應用程式保護原則，以查看指派給所選取使用者的應用程式保護原則。



### <a name="improvements-to-device-setup-workflow-in-company-portal---1490692--"></a>對公司入口網站之裝置安裝工作流程的改善 <!--1490692-->
我們已改善 Android 版公司入口網站應用程式中的裝置安裝工作流程。 我們採用您公司專屬的語言、對使用者來說更簡單明瞭，並盡量將可以合併的畫面合併。 您可以在[應用程式 UI 的新功能](whats-new-app-ui.md#week-of-october-2-2017)頁面中，查看這些變更。

### <a name="improved-guidance-around-the-request-for-access-to-contacts-on-android-devices---1484985--"></a>改善在 Android 裝置上要求存取連絡人的相關指引 <!--1484985-->

Android 版公司入口網站應用程式通常會要求使用者接受「連絡人」權限。 如果使用者拒絕此存取權，系統現會顯示應用程式內通知，提醒他們授與此權限以進行條件式存取。 

### <a name="secure-startup-remediation-for-android---1490712--"></a>Android 的安全啟動修復 <!--1490712-->

如果使用者是使用 Android 裝置，可以點選公司入口網站應用程式中的不相容原因。 如此一來，系統會盡可能將使用者直接移至設定應用程式的正確位置，以修正問題。 

### <a name="additional-push-notifications-for-end-users-on-the-company-portal-app-for-android-oreo---1475932--"></a>在 Android Oreo 的公司入口網站應用程式上新增終端使用者的推播通知 <!--1475932-->

終端使用者將會看到其他通知，這些通知會指出 Android Oreo 版公司入口網站應用程式正在執行背景工作，例如從 Intune 服務擷取原則。 這樣可讓終端使用者清楚了解公司入口網站在其裝置上執行的系統管理工作。 這是適用於 Android Oreo 版公司入口網站應用程式之整體[公司入口網站 UI 最佳化](https://blogs.technet.microsoft.com/intunesupport/2017/08/21/android-8-0-o-behaviour-changes-and-microsoft-intune)的一部分。 

在 Android Oreo 中啟用的新 UI 項目已進一步最佳化。  終端使用者會看到額外的通知，顯示出公司入口網站執行背景工作 (例如從 Intune 服務擷取原則) 的時間。  這可讓使用者清楚知道公司入口網站在裝置上執行管理工作的時間。

### <a name="new-behaviors-for-the-company-portal-app-for-android-with-work-profiles----1485783---"></a>Android 公司入口網站應用程式使用工作設定檔的新行為 <!-- 1485783 -->

當您使用工作設定檔註冊 Android for Work 裝置時，是由工作設定檔中的公司入口網站應用程式來執行裝置上的管理工作。 

除非您使用個人設定檔中啟用 MAM 的應用程式，否則 Android 公司入口網站應用程式不再有任何用途。 為了改善工作設定檔的體驗，Intune 會在成功註冊工作設定檔後，自動隱藏個人的公司入口網站應用程式。

您可以隨時啟用個人設定檔中的 Android 公司入口網站應用程式，方法是瀏覽 [Play Store 中的公司入口網站](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal)，然後點選 [啟用]。

### <a name="company-portal-for-windows-81-and-windows-phone-81-moving-to-sustaining-mode---1428681--"></a>Windows 8.1 和 Windows Phone 8.1 版公司入口網站移至維持模式 <!--1428681-->

自 2017 年 10 月起，Windows 8.1 和 Windows Phone 8.1 公司入口網站應用程式將會移至維持模式。 這表示這些平台將會繼續支援應用程式和現有的案例 (例如註冊和合規性)。 這些應用程式仍可透過現有的發行通道 (例如 Microsoft 市集) 下載取得。 

一旦進入維持模式，這些應用程式就僅會接收重大安全性更新。 但是，將不會針對這些應用程式發行額外的更新或功能。 如需新功能，建議您將裝置更新為 Windows 10 或 Windows 10 行動裝置版。 


### <a name="block-unsupported-samsung-knox-device-enrollment-----1490695---"></a>封鎖不支援的 Samsung Knox 裝置註冊 <!-- 1490695 -->

公司入口網站應用程式只會嘗試註冊支援的 Samsung Knox 裝置。 為了避免 Knox 啟用錯誤而導致 MDM 註冊失敗，如果裝置出現在 [Samsung 發佈的裝置清單](https://www.samsungknox.com/knox-supported-devices/knox-workspace)中，則系統只會嘗試進行裝置註冊。 有些 Samsung 裝置型號可能支援 Knox，而有些不支援。 在您購買及部署之前，請先跟裝置轉銷商確認 KNOX 相容性。 您可以在 [Android 和 Samsung Knox Standard 原則設定](/intune/supported-devices-browsers.md#intune-supported-devices)中找到已驗證裝置的完整清單。

### <a name="end-of-support-for-android-43-and-lower----1171126-1326920---"></a>結束對 Android 4.3 和較舊版本的支援<!-- 1171126, 1326920 -->
受管理的應用程式和 Android 公司入口網站應用程式需要 Android 4.4 及更新版本才能存取公司資源。 今年 12 月會強制淘汰所有已註冊的裝置，以致無法存取公司資源。 如果您使用不含 MDM 的應用程式保護原則，應用程式就不會接收更新，其體驗品質會隨著時間而降低。

### <a name="inform-end-users-what-device-information-can-be-seen-on-enrolled-devices---1165314--"></a>通知使用者可在已註冊裝置上看到哪些裝置資訊 <!--1165314-->
針對所有公司入口網站應用程式的 [裝置詳細資料] 畫面，我們會新增 [擁有權類型]。 如此一來，使用者就能夠直接從[公司可以看到哪些資訊？](/intune-user-help/what-info-can-your-company-see-when-you-enroll-your-device-in-intune)一文中，了解隱私權的詳細資訊。 在不久的將來，這項功能就會跨所有公司入口網站應用程式推出。 iOS 的這項功能已於 [9 月](https://docs.microsoft.com/intune/whats-new#week-of-september-11-2017)推出。

## <a name="september-2017"></a>2017 年 9 月

### <a name="intune-supports-ios-11---1428975--"></a>Intune 支援 iOS 11 <!--1428975-->
Intune 支援 iOS 11。 這項資訊之前已在 [Intune 支援部落格](https://blogs.technet.microsoft.com/intunesupport/2017/09/12/support-tip-intune-support-for-ios-11/)宣布過。

### <a name="end-of-support-for-ios-80----1164477---"></a>結束對 iOS 8.0 的支援<!-- 1164477 -->
受管理的應用程式和 iOS 公司入口網站應用程式需要 iOS 9.0 及更新版本才能存取公司資源。 今年 9 月前未更新的裝置將不再能存取公司入口網站或這些應用程式。 

### <a name="refresh-action-added-to-the-company-portal-app-for-windows-10---1132468--"></a>重新整理動作已新增至 Windows 10 的公司入口網站應用程式 <!--1132468-->
Windows 10 公司入口網站應用程式可讓使用者提取以重新整理，或按桌上型電腦的 F5，重新整理應用程式中的資料。

### <a name="inform-end-users-what-device-information-can-be-seen-for-ios---739894--"></a>通知終端使用者可看到哪些 iOS 裝置資訊 <!--739894-->

我們在 iOS 的公司入口網站應用程式 [裝置詳細資料] 畫面新增了 [擁有權類型]。 這樣可讓使用者直接從此頁面從 Intune 終端使用者文件尋找有關隱私權的詳細資訊。他們也能夠在 [關於] 畫面上找到這項資訊。

### <a name="allow-end-users-to-access-the-company-portal-app-for-android-without-enrollment----1169910---"></a>允許使用者存取適用於 Android 的公司入口網站應用程式，不需要註冊。<!---1169910--->

使用者很快地不必註冊裝置也能存取 Android 的公司入口網站。 使用應用程式保護原則的組織使用者，在開啟公司入口網站應用程式時，將不會再收到註冊裝置的提示。 使用者也可以從公司入口網站安裝應用程式，不用註冊裝置。 


### <a name="easier-to-understand-phrasing-for-the-company-portal-app-for-android----1396349---"></a>Android 公司入口網站應用程式中更易了解的措辭 <!---1396349--->  

Android 公司入口網站應用程式的註冊程序已經使用新的文字來簡化，讓使用者可更輕鬆地進行註冊。 如果您有自訂註冊文件，建議您予以更新，以反映新的畫面。 您可以在 [Intune 終端使用者應用程式](whats-new-app-ui.md#week-of-september-11-2017)頁面上找到範例影像。

### <a name="windows-10-company-portal-app-added-to-windows-information-protection-allow-policy----677129---"></a>Windows 10 公司入口網站應用程式已新增到 Windows 資訊保護允許原則 <!-- 677129 -->

Windows 10 公司入口網站應用程式已經更新，以支援 Windows 資訊保護 (WIP)。 此應用程式可以加入到 WIP 允許原則。 透過這項變更，此應用程式將不再需要新增至 [豁免] 清單。


## <a name="august-2017"></a>2017 年 8 月

### <a name="improvements-to-device-overview----1404453---"></a>裝置概觀改善 <!-- 1404453 -->  
裝置概觀改善現在會顯示已註冊的裝置，但不包含 Exchange ActiveSync 所管理的裝置。 Exchange ActiveSync 裝置與已註冊裝置的管理選項不同。 若要在 Azure 入口網站中檢視 Intune 中的已註冊裝置數目以及依平台的已註冊裝置數目，請移至 [裝置] > [概觀]。

### <a name="improvements-to-device-inventory-collected-by-intune"></a>Intune 所收集裝置清查的改善
<!-- 961134, 1104426, 1281327, 1333543 -->
在此版本中，我們已對您管理的裝置所收集的清查資訊進行下列改善：
 
-   對於 Android 裝置，您現在可以將資料行新增至裝置清查，以顯示每個裝置的最新修補程式等級。 將 [Security patch level] (安全性修補程式等級) 資料行新增至裝置清單，以查看這項資訊。
-   當您篩選裝置檢視時，現在可以依其註冊日期篩選裝置。 例如，您可以只顯示在所指定日期之後註冊的裝置。
-   我們已改善 [Last Check-in Date] (最後一次簽入日期) 項目所使用的篩選。
-   在裝置清單中，您現在可以顯示公司所擁有裝置的電話號碼。
此外，您還可以使用篩選窗格，依電話號碼來搜尋裝置。
 
如需裝置清查的詳細資料，請參閱[如何檢視 Intune 裝置清查](device-inventory.md)。

### <a name="conditional-access-support-for-macos-devices"></a>macOS 裝置的條件式存取支援 
<!-- 720172 -->
您現在可以設定條件式存取原則，要求 Mac 裝置向 Intune 註冊，並符合其裝置的合規性原則。 例如，使用者可以下載適用於 macOS 的 Intune 公司入口網站應用程式，並在 Intune 中註冊其 Mac 裝置。 Intune 會評估 Mac 裝置是否符合 PIN、加密、作業系統版本和系統完整性等需求。

- 深入了解 [macOS 裝置的條件式存取支援](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)。

### <a name="company-portal-app-for-macos-is-in-public-preview----1484796---"></a>對 macOS 來說，公司入口網站應用程式目前為公開預覽 <!---1484796--->
公開預覽中目前提供 macOS 的公司入口網站應用程式，以於 Enterprise Mobility + Security 中進行條件式存取。 此版本支援 macOS 10.11 及更新版本。 若要下載，請前往 [https://aka.ms/macOScompanyportal](https://aka.ms/macOScompanyportal)。 


### <a name="new-device-restriction-settings-for-windows-10"></a>Windows 10 的新裝置限制設定    
<!--1063965, 1308850  -->
在此版本中，我們已在下列類別中新增 [Windows 10 裝置限制設定檔](/intune/device-restrictions-windows-10)的新設定：

-   Windows Defender SmartScreen
-   App Store

### <a name="updates-to-the-windows-10-endpoint-protection-device-profile-for-bitlocker-settings"></a>BitLocker 設定的 Windows 10 端點保護裝置設定檔更新
<!--1459533 -->    
在此版本中，我們已對 BitLocker 設定在 Windows 10 端點保護裝置設定檔中的運作方式進行下列改善：
 
在 [BitLocker OS 磁碟機設定] 下，針對 [具有不相容 TPM 晶片的 BitLocker] 設定，當您選取 [封鎖] 時，以前這會導致實際允許 BitLocker。 我們現在已修正這個問題，以在選取 BitLocker 時進行封鎖。
在 [BitLocker OS 磁碟機設定] 下，針對 [以憑證為基礎的資料修復代理程式] 設定，您現在可以明確地封鎖以憑證為基礎的資料修復代理程式。 不過，預設會允許代理程式。
在 [BitLocker 固定式資料磁碟機設定] 下，針對 [資料修復代理程式] 設定，您現在可以明確地封鎖資料修復代理程式。
如需詳細資訊，請參閱 [Windows 10 和更新版本的 Endpoint Protection 設定](endpoint-protection-windows-10.md)。


### <a name="new-signed-in-experience-for-android-company-portal-users-and-app-protection-policy-users----621669---"></a>Android 公司入口網站使用者和應用程式防護原則使用者的新登入體驗 <!-- 621669 -->
使用者現在可以使用 Android 公司入口網站應用程式來瀏覽應用程式、管理裝置及檢視 IT 連絡人資訊，而無需註冊其 Android 裝置。 此外，如果終端使用者已使用由 Intune 應用程式防護原則保護的應用程式，並啟動 Android 公司入口網站，則終端使用者無法再收到註冊裝置的提示。

### <a name="new-setting-in-the-android-company-portal-app-to-toggle-battery-optimization---1405990--"></a>Android 公司入口網站應用程式中用來切換電池最佳化的新設定 <!--1405990-->
適用於 Android 的公司入口網站應用程式中的 [設定] 頁面，具有新的設定，可讓使用者輕鬆關閉公司入口網站及 Microsoft Authenticator 應用程式的電池最佳化功能。 設定中所顯示的應用程式名稱，會依管理公司帳戶的應用程式而有所不同。 建議使用者關閉電池最佳化功能，以提升同步電子郵件與資料的公司應用程式效能。 

### <a name="multi-identity-support-for-onenote-for-ios---------1234281---"></a>OneNote for iOS 的多重身分識別支援 <!-- 1234281 -->
終端使用者現在可以搭配使用不同的帳戶 (公司和個人) 與 Microsoft OneNote for iOS。 應用程式保護原則可以套用至工作筆記本中的公司資料，而不會影響其個人筆記本。 例如，原則可讓使用者在工作筆記本中尋找資訊，但會防止使用者將公司資料從工作筆記本複製並貼入個人筆記本。
 
- 深入了解支援 Intune 的[應用程式保護和多重身分識別](https://www.microsoft.com/cloud-platform/microsoft-intune-apps)的應用程式。

### <a name="new-settings-to-allow-and-block-apps-on-samsung-knox-standard-devices"></a>在 Samsung Knox Standard 裝置上允許或封鎖應用程式的新設定
<!-- 1305423 822899-->  
在此版本中，我們新增新的[裝置限制設定](device-restrictions-android.md)，可讓您指定下列應用程式清單：
 
- 允許使用者安裝的應用程式
- 封鎖使用者執行的應用程式
- 對使用者隱藏的裝置應用程式
 
您可依 URL、套件名稱，或從管理的應用程式清單中指定應用程式。

### <a name="new-azure-ad-app-based-conditional-access-policy-ui-link-from-intune"></a>來自 Intune 的新 Azure AD 應用程式條件式存取原則 UI 連結
<!-- 1016201 -->
IT 管理員現在可以透過 Azure AD 工作負載中的新條件式存取原則 UI，來設定應用程式條件式存取原則。 Azure 入口網站的 [Intune 應用程式防護] 區段中，應用程式條件式存取會暫時保留不動，且會強制並存。 Intune 工作負載中另有提供方便的連結，可連至新的條件式存取原則 UI。

- 深入了解 [Azure AD 上的應用程式條件式存取](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-technical-reference)。



## <a name="july-2017"></a>2017 年 7 月

### <a name="restrict-android-and-ios-device-enrollment-restriction-by-os-version------1333256--1245463----"></a>依作業系統版本限制 Android 和 iOS 裝置註冊限制 <!--- 1333256,  1245463 --->
Intune 現在支援依作業系統版本號碼限制 iOS 和 Android 註冊。 在 [裝置類型限制] 下，IT 系統管理員現在可以進行平台設定，以便將註冊限制於作業系統值上下限之間。 Android 作業系統版本必須指定為 Major.Minor.Build.Rev，其中 Minor、Build 和 Rev 為選擇性。 iOS 版本必須指定為 Major.Minor.Build，其中 Minor 和 Build 為選擇性。 深入了解[裝置註冊限制](enrollment-restrictions-set.md)。

>[!NOTE]
>請勿將註冊限制為透過 Apple 註冊計劃或 Apple Configurator 進行。

### <a name="restrict-android-ios-and-macos-device-personally-owned-device-enrollment------1333272--1333275-1245709----"></a>限制 Android、iOS 和 macOS 裝置以個人擁有的裝置註冊<!--- 1333272,  1333275, 1245709 --->
Intune 可以透過將公司裝置 IMEI 編號列入白名單，來限制個人裝置註冊。 Intune 現在已使用裝置序號，將這項功能擴充到 iOS、Android 和 macOS。 將序號上傳至 Intune，您就可以預先宣告此為公司擁有的裝置。 使用註冊限制，您可以封鎖個人擁有 (BYOD) 的裝置，僅註冊公司擁有的裝置。 深入了解[裝置註冊限制](enrollment-restrictions-set.md)。

若要匯入序號，請移至 [裝置註冊] > [公司裝置識別碼] 並按一下 [新增]，然後上傳 .CSV 檔案 (不含標頭的兩個序號和 IMEI 編號等詳細資料欄位)。  若要限制個人擁有的裝置，請移至 [裝置註冊]  >  [註冊限制]。 在 [裝置類型限制] 下選取 [預設]，然後選取 [平台設定]。 您可以 [允許] 或 [封鎖] 個人擁有的 iOS、Android 和 macOS 裝置。 


### <a name="new-device-action-to-force-devices-to-sync-with-intune----711369---"></a>新的裝置動作會強制裝置與 Intune 同步處理<!-- 711369 -->
在此版本中，我們已新增裝置動作，強制所選裝置立即使用 Intune 簽入。 當裝置簽入時，會立即收到所有擱置動作或已指派給它的原則。  這個動作可協助您立即驗證和針對您已指派的原則進行疑難排解，不用等到下次排程的簽入。
如需詳細資料，請參閱[同步處理裝置](device-sync.md)

### <a name="force-supervised-ios-devices-to-automatically-install-the-latest-available-software-update----777100---"></a>強制受監督的 iOS 裝置自動安裝最新可用的軟體更新<!-- 777100 -->
新的原則可從 [軟體更新] 工作區取得，您可在此強制受監督的 iOS 裝置自動安裝最新可用的軟體更新。 如需詳細資料，請參閱[設定 iOS 更新原則](/intune/software-updates-ios)

### <a name="check-point-sandblast-mobile---new-mobile-threat-defense-partner-----954651-1172027---"></a>Check Point SandBlast Mobile - 新的 Mobile Threat Defense 夥伴<!-- 954651, 1172027 -->
您可以根據由 Checkpoint SandBlast Mobile (一個與 Microsoft Intune 整合的 Mobile Threat Defense 解決方案) 所進行的風險評估，使用條件式存取來控制行動裝置對公司資源的存取。

#### <a name="how-integration-with-intune-works"></a>整合 Intune 如何運作？
風險乃依據收集自執行 Checkpoint SandBlast Mobile 裝置的遙測來進行評估。 您可以根據透過 Intune 裝置合規性政策所啟用的 Checkpoint SandBlast Mobile 風險評估，來設定 EMS 條件式存取原則。 您可以根據偵測到的威脅，允許或封鎖不相容的裝置存取公司資源。


### <a name="deploy-an-app-as-available-in-the-microsoft-store-for-business----748101---"></a>將應用程式部署為商務用 Microsoft 網上商店中的可用項目 <!-- 748101 -->
系統管理員現在可以使用此版本將商務用 Microsoft 網上商店指派為可用。 設定為可用時，終端使用者就可以從公司入口網站應用程式或網站安裝應用程式，而不會被重新導向至 Microsoft 網上商店。

### <a name="ui-updates-to-the-company-portal-website---1313244-part-1--"></a>公司入口網站的 UI 更新 <!--1313244 part 1-->
我們對[公司入口網站](https://portal.manage.microsoft.com)的 UI 進行了數項更新，以增強終端使用者體驗。

- __應用程式磚的增強功能__：應用程式圖示現在會根據圖示的主要色彩 (如果可偵測)來顯示自動產生的背景。 適用時，此背景會取代先前在應用程式磚上顯示的灰色框線。

    公司入口網站會在未來版本中盡可能顯示大圖示。 建議 IT 系統管理員使用大小下限為 120 x120 像素的高解析度圖示來發佈應用程式。 

- __導覽變更__：導覽列項目移至左上方的漢堡功能表。 移除 [類別] 頁面。 使用者現在可以在瀏覽時依類別篩選內容。

- __精選 App 的更新__：我們已將專用頁面新增至網站 (使用者可在其中瀏覽您選為精選的應用程式)，並對首頁上的 [精選] 區段進行一些 UI 調校。

### <a name="ibooks-support-for-the-company-portal-website---1231841--"></a>公司入口網站的 iBooks 支援 <!--1231841-->
我們已將專用頁面新增至公司入口網站，讓使用者可以瀏覽並下載 iBooks。 


### <a name="additional-help-desk-troubleshooting-details------applies-to-1263399-1326964-1341642----"></a>其他技術服務人員疑難排解詳細資料 <!---  Applies to 1263399, 1326964, 1341642 --->
Intune 已更新疑難排解顯示，並新增至針對系統管理員和技術服務人員所提供的資訊。 您現在可以看到 [指派] 表格，其中根據群組成員資格來摘要說明所有使用者指派。 此清單包括：
- 行動裝置應用程式
- 合規性政策
- 組態設定檔
 
此外，[裝置] 資料表現在會包含 [Azure AD 聯結類型] 和 [符合 Azure AD 規範] 資料行。 如需詳細資訊，請參閱[協助使用者針對問題進行疑難排解](help-desk-operators.md)。



### <a name="intune-data-warehouse-public-preview"></a>Intune 資料倉儲 (公開預覽)
Intune 資料倉儲會每日對資料進行抽樣，以提供您租用戶的歷程檢視。 您可以藉由使用 Power BI 檔案 (PBIX)、與許多分析工具相容的 OData 連結，或與 REST API 互動，來存取資料。 如需詳細資訊，請參閱[使用 Intune 資料倉儲](reports-nav-create-intune-reports.md)。


### <a name="light-and-dark-modes-available-for-the-company-portal-app-for-windows-10----676547---"></a>Windows 10 的公司入口網站應用程式提供日間和夜間模式<!---676547--->
使用者可以自訂 Windows 10 公司入口網站應用程式的色彩模式。 使用者可在公司入口網站應用程式的 [設定] 區段中進行變更。 使用者重新啟動應用程式後，即會看到變更。 至於 Windows 10 版本 1607 及更新版本，應用程式模式會預設為系統設定。 至於 Windows 10 版本 1511 及更新版本，應用程式模式會預設為日間模式。

### <a name="enable-end-users-to-tag-their-device-group-in-the-company-portal-app-for-windows-10----807046--"></a>讓使用者在 Windows 10 的公司入口網站應用程式中標記其裝置群組<!---807046-->
終端使用者現在可以直接在 Windows 10 公司入口網站應用程式中標記群組，選取其裝置所屬群組。



## <a name="june-2017"></a>2017 年 6 月

### <a name="new-role-based-administration-access-for-intune-admins------1099990---"></a>適用於 Intune 管理員的全新且以角色為基礎的系統管理存取權 <!-- 1099990 -->  
新增條件式存取管理員角色，來檢視、建立、修改及刪除 Azure AD 條件式存取原則。 先前只有全域管理員和安全性管理員具有此權限。 您可以為 Intune 管理員授與此角色權限，讓他們具有條件式存取原則的存取權。


### <a name="tag-corporate-owned-devices-with-serial-number----1215070---"></a>使用序號標記屬公司擁有的裝置 <!-- 1215070 -->  
Intune 現在支援上傳 iOS、macOS 和 Android 序號以作為公司裝置識別碼。 您無法使用序號來封鎖個人裝置進行註冊，因為在註冊期間不會驗證序號。 依序號封鎖個人裝置，將在不久的未來推出。


### <a name="new-remote-actions-for-ios-devices----854689---"></a>適用於 iOS 裝置的新遠端動作<!-- 854689 -->
在此版本中，我們為用於管理 Apple Classroom 的共用 iPad 裝置新增了兩個遠端裝置動作：

-   [登出目前的使用者](device-logout-user.md) - 會登出您所選擇之 iOS 裝置的目前使用者。
-   [移除使用者](device-remove-user.md) - 會從 iOS 裝置的本機快取中刪除您選擇的使用者。


### <a name="support-for-shared-ipads-with-the-ios-classroom-app----1044681---"></a>使用 iOS Classroom 應用程式支援共用的 iPad <!-- 1044681 -->
在此版本中，我們擴充了對管理 iOS Classroom 應用程式的支援，以包含使用受管理 Apple ID 登入共用 iPad 的學生。


### <a name="changes-to-intune-built-in-apps----1332306---"></a>Intune 內建應用程式的變更 <!-- 1332306 -->
原本，Intune 包含許多您可以快速指派的內建應用程式。 應客戶的意見反應，我們已移除此清單，而您不會再看到內建應用程式。
不過，您已指派的任何內建應用程式仍會顯示在應用程式清單中。 若有需要，您可以繼續指派這些應用程式。
在之後的版本中，我們計劃新增一個方法，讓從 Azure 入口網站選取及指派內建應用程式的流程變得更輕鬆。

### <a name="easier-installation-of-office-365-apps-----1121362----"></a>安裝 Office 365 應用程式更輕鬆<!--- 1121362 --->
新的 **Office 365 ProPlus** 應用程式類型可讓您輕鬆地將 Office 365 ProPlus 2016 應用程式指派給您管理的執行最新版 Windows 10 的裝置。 此外，如果您有 Microsoft Project 或 Microsoft Visio 的授權，也可以安裝它們。 您想要的應用程式會配套在一起，並以單一應用程式的形式出現在 Intune 主控台的應用程式清單中。
如需詳細資訊，請參閱[如何新增適用於 Windows 10 的 Office 365 應用程式](apps-add-office365.md)。


### <a name="support-for-offline-apps-from-the-microsoft-store-for-business-----777044----"></a>支援來自商務用 Microsoft 網上商店的離線應用程式 <!--- 777044 --->
您購買自商務用 Microsoft 網上商店的離線應用程式現在將能同步處理至 Azure 入口網站。 您接著可將這些應用程式部署至裝置群組或使用者群組。 離線應用程式會透過 Intune 安裝，而不透過市集。

### <a name="microsoft-teams-is-now-part-of-the-app-based-ca-list-of-approved-apps------1257019---"></a>Microsoft 小組現在是以應用程式為基礎的已核准應用程式 CA 清單的一部分<!-- 1257019 -->
適用於 iOS 和 Android 的 Microsoft Teams 應用程式，現在是針對適用於 Exchange 和 SharePoint Online 之以應用程式為基礎的條件式存取原則核准的應用程式一部分。 可以透過 Azure 入口網站中的 [Intune 應用程式防護] 刀鋒視窗，使用以應用程式為基礎的條件式存取，將應用程式設定為所有租用戶。

### <a name="managed-browser-and-app-proxy-integration----1287310---"></a>受管理的瀏覽器和應用程式 Proxy 整合<!-- 1287310 -->
Intune Managed Browser 現在可以整合 Azure AD Application Proxy 服務，讓使用者即使在遠端工作時也能存取內部網路網站。 瀏覽器的使用者只需和平常一樣輸入網站 URL，Managed Browser 便會透過應用程式 Proxy Web 閘道來路由傳送要求。 如需詳細資訊，請參閱[使用 Managed Browser 原則管理網際網路存取](app-configuration-managed-browser.md)。

### <a name="new-app-configuration-settings-for-the-intune-managed-browser----682951---"></a>適用於 Intune Managed Browser 的新應用程式組態設定 <!-- 682951 -->
在此版本中，我們已新增 iOS 和 Android 的 Intune Managed Browser 應用程式的進一步設定。 您現在能使用應用程式設定原則，針對瀏覽器設定預設的首頁和書籤。
如需詳細資訊，請參閱[使用 Managed Browser 原則管理網際網路存取](app-configuration-managed-browser.md)

### <a name="bitlocker-settings-for-windows-10-----951707---"></a>Windows 10 的 BitLocker 設定 <!-- 951707 -->
您現在可以使用新的 Intune 裝置設定檔，設定 Windows 10 裝置的 BitLocker 設定。 例如，您可以要求裝置加密，也可以設定在開啟 BitLocker 時套用的進一步設定。
如需詳細資訊，請參閱 [Windows 10 和更新版本的 Endpoint Protection 設定](endpoint-protection-windows-10.md)。

### <a name="new-settings-for-windows-10-device-restriction-profile-----978527--978550-978569-1050031-1058611-----"></a>適用於 Windows 10 裝置限制設定檔的新設定 <!--- 978527,  978550, 978569, 1050031, 1058611,  --->
在此版本中，我們已新增 Windows 10 裝置限制設定檔的新設定，在下列類別中：

-  Windows Defender
-  行動數據與連線
-  鎖定畫面體驗
-  隱私權
-  搜尋
-  Windows 焦點
-  Edge 瀏覽器

如需 Windows 10 設定的詳細資訊，請參閱 [Windows 10 和更新版本的裝置限制設定](device-restrictions-windows-10.md)。


### <a name="company-portal-app-for-android-now-has-a-new-end-user-experience-for-app-protection-policies---1305217--"></a>Android 公司入口網站應用程式的應用程式保護原則現在有了新的使用者體驗<!--1305217-->
根據客戶的意見反應，我們已修改 Android 公司入口網站應用程式，以顯示 [存取公司內容] 按鈕。 目的是為了防止終端使用者在他們只需要存取支援應用程式保護原則 (Intune 行動應用程式管理的一項功能) 的應用程式時，不必要地進行註冊程序。 您可以在[應用程式 UI 的新功能](whats-new-app-ui.md)頁面看到這些變更。

### <a name="new-menu-action-to-easily-remove-company-portal---1164569--"></a>新的功能表動作，可輕鬆地移除公司入口網站<!--1164569-->
根據使用者意見反應，Android 版公司入口網站應用程式已新增功能表動作，可從裝置起始公司入口網站的移除。 此動作會將裝置從 Intune 管理移除，來讓使用者可以將應用程式從裝置移除。 您可以在[應用程式 UI 的新功能](whats-new-app-ui.md)頁面和 [Android 使用者文件](/intune-user-help/unenroll-your-device-from-intune-android)中看到這些變更。

### <a name="improvements-to-app-syncing-with-windows-10-creators-update---676505--"></a>透過 Windows 10 Creators Update 改進應用程式同步<!--676505-->
Windows 10 版公司入口網站應用程式現在會針對具有 Windows 10 Creators Update (版本 1703) 之裝置的應用程式安裝要求，自動初始化同步處理。 這會減少應用程式安裝在「待同步」狀態期間出現拖延的問題。 此外，使用者將能從應用程式內手動起始同步處理。 您可以在[應用程式 UI 的新功能](whats-new-app-ui.md)頁面看到這些變更。

### <a name="new-guided-experience-for-windows-10-company-portal----1058938---"></a>Windows 10 公司入口網站新型引導式體驗 <!---1058938--->
Windows 10 的公司入口網站應用程式將包含之前尚未確定或註冊之裝置的引導式 Intune 逐步解說體驗。 此全新體驗提供逐步指示，引導使用者向 Azure Active Directory 註冊 (條件式存取功能所需)，以及 MDM 註冊 (裝置管理功能所需)。 此引導式體驗將可從公司入口網站首頁上存取。 未完成註冊的使用者可以繼續使用應用程式，但可使用的功能將會受到限制。

此更新只會顯示在執行 Windows 10 年度更新版 (組建 1607) 或更高版本的裝置上。 您可以在[應用程式 UI 的新功能](whats-new-app-ui.md)頁面看到這些變更。


### <a name="microsoft-intune-and-conditional-access-admin-consoles-are-generally-available"></a>Microsoft Intune 和條件式存取管理主控台正式推出
我們宣佈推出 Azure 入口網站管理主控台中的新 Intune 和條件式存取管理主控台。 您現在可以透過 Azure 入口網站中的 Intune，將所有 Intune MAM 與 MDM 功能合併管理，並妥善利用 Azure AD 群組和目標設定功能。 Azure 中的條件式存取跨 Azure AD 和 Intune，將豐富的功能整合在一個統一主控台。 從系統管理經驗的觀點，移至 Azure 平台可讓您使用新式瀏覽器。

您現在可以在 Azure 入口網站 (portal.azure.com) 中看到沒有「預覽」標籤的 Intune。

除非您在訊息中心收到的一系列訊息中，有要求您採取動作來移轉群組的訊息，否則現有的客戶目前不需採取任何動作。 您可能也會收到訊息中心通知，說明因為我們這一端有錯誤而使移轉需要較長的時間。 我們會努力繼續移轉任何受影響的客戶。

### <a name="improvements-to-the-app-tiles-in-the-company-portal-app-for-ios"></a>iOS 版公司入口網站應用程式中應用程式磚的增強功能
我們已更新首頁上應用程式磚的設計，以反映您為公司入口網站設定的商標色彩。 如需詳細資訊，請參閱[應用程式 UI 的新功能](whats-new-app-ui.md)。

### <a name="account-picker-now-available-for-the-company-portal-app-for-ios"></a>iOS 版公司入口網站應用程式現在有帳戶選擇器可供使用
如果 iOS 裝置的使用者使用其工作或學校帳戶登入其他 Microsoft 應用程式，當他們登入公司入口網站時，可能會看到新的帳戶選擇器。 如需詳細資訊，請參閱[應用程式 UI 的新功能](whats-new-app-ui.md)。

## <a name="may-2017"></a>2017 年 5 月

### <a name="change-your-mdm-authority-without-unenrolling-managed-devices---1103950--"></a>在不取消註冊受管理裝置的情況下變更 MDM 授權單位 <!--1103950-->
您現在可以在不需要連絡 Microsoft 支援服務的情況下變更 MDM 授權單位，且不需要取消註冊並重新註冊您現有的受管理裝置。 在 Configuration Manager 主控台中，您可以將 [MDM 授權單位](/sccm/mdm/deploy-use/change-mdm-authority)從 [設定為 Configuration Manager] \(混合式\) 變更為 [Microsoft Intune] \(獨立\)，反之亦然。


### <a name="improved-notification-for-samsung-knox-startup-pins---1087143--"></a>已改進 Samsung Knox 啟動 PIN 的通知 <!--1087143-->
當使用者需要在 Samsung Knox 裝置上設定啟動 PIN 以符合加密規範時，點選對使用者顯示的通知會將他們引導至 [設定] 應用程式中的確切位置。  先前的通知會將使用者引導至密碼變更畫面。

### <a name="device-enrollment"></a>裝置註冊

#### <a name="apple-school-manager-asm-support-with-shared-ipad----748864-770395--"></a>對於共用 iPad 的 Apple School Manager (ASM) 支援<!-- 748864, 770395-->

Intune 現在支援以 Apple School Manager (ASM) 取代 Apple 裝置註冊計劃，來為 iOS 裝置提供全新註冊功能。 下列兩種情況皆需要 ASM 上線：在「共用的 iPad」上使用 Classroom 應用程式，以及透過 Microsoft 學校資料同步處理 (SDS) 將資料從 ASM 同步到 Azure Active Directory。 如需詳細資訊，請參閱[使用 Apple School Manager 啟用 iOS 裝置註冊](apple-school-manager-set-up-ios.md)。

> [!NOTE]
> 若要設定共用的 iPad 搭配 Classroom 應用程式使用，需要在 Azure 中設定 iOS Education，而此功能目前尚未提供。  此功能將於不久後加入。

### <a name="device-management"></a>裝置管理

#### <a name="provide-remote-assistance-to-android-devices-using-teamviewer----675418---"></a>使用 TeamViewer 對 Android 裝置提供遠端協助<!-- 675418 -->

Intune 現在可使用 [TeamViewer](https://www.teamviewer.com) 軟體 (另行購買)，讓您為執行 Android 裝置的使用者提供遠端協助。 如需詳細資訊，請參閱[對 Intune 管理的 Android 裝置提供遠端協助](device-profile-android-teamviewer.md)。

### <a name="app-management"></a>應用程式管理

#### <a name="new-app-protection-policies-conditions-for-mam----679864---"></a>適用於 MAM 的新應用程式保護原則條件 <!-- 679864 -->

您現在可以在無需註冊使用者的情況下，設定能強制執行下列原則的 MAM 需求：

- 對低應用程式版本
- 最低作業系統版本
- 目標應用程式的最低 Intune APP SDK 版本 (僅限 iOS)

這項功能適用於 Android 和 iOS。 Intune 支援作業系統平台版本、應用程式版本，以及 Intune APP SDK 的最低版本強制。 在 iOS 上，已整合 SDK 的應用程式也可以設定 SDK 層級的最低版本強制。 如果沒有符合應用程式保護原則於上述三個不同層級的最低需求，使用者將無法存取目標應用程式。 此時，使用者可以選擇移除其帳戶 (適用於多重身分識別應用程式)、關閉該應用程式，或更新作業系統或應用程式版本。

您也可設定其他設定，以提供能建議使用者進行作業系統或應用程式升級的非封鎖式通知。 使用者可以關閉此通知，並繼續正常地使用應用程式。

如需詳細資訊，請參閱 [iOS 應用程式保護原則設定](app-protection-policy-settings-ios.md)和 [Android 應用程式保護原則設定](app-protection-policy-settings-android.md)。

#### <a name="configure-app-configurations-for-android-for-work----621621---"></a>設定 Android for Work 的應用程式設定<!-- 621621 -->
市集中有一些 Android 應用程式支援受管理設定選項，可以讓 IT 系統管理員控制應用程式在工作設定檔中執行的方式。 您現在可以使用 Intune 來檢視應用程式支援的設定，並使用設定設計工具或 JSON 編輯器從 Azure 入口網站進行設定。 如需詳細資訊，請參閱[使用 Android for Work 的應用程式設定](app-configuration-policies-use-android.md)。

#### <a name="new-app-configuration-capability-for-mam-without-enrollment----677969---"></a>不需註冊的新 MAM 應用程式設定功能<!-- 677969 -->
您現在可以在沒有註冊通道的情況下，透過 MAM 建立應用程式設定原則。 此功能相當於行動裝置管理 (MDM) 應用程式設定中的應用程式設定原則。 如需使用 MAM 而不註冊的應用程式設定範例，請參閱[搭配 Microsoft Intune 使用 Managed Browser 原則管理網際網路存取](app-configuration-managed-browser.md)。

#### <a name="configure-allowed-and-blocked-url-lists-for-the-managed-browser----682960---"></a>為 Managed Browser 設定允許和封鎖的 URL 清單<!-- 682960 -->
您現在可以在 Azure 入口網站中使用應用程式組態設定，為 Intune Managed Browser 設定允許和封鎖的網域及 URL 清單。 不論 Intune Managed Browser 是用於受管理或未受管理的裝置上，都適用這些設定。 如需詳細資訊，請參閱[搭配 Microsoft Intune 使用 Managed Browser 原則管理網際網路存取](app-configuration-managed-browser.md)。

#### <a name="app-protection-policy-helpdesk-view----1069473---"></a>應用程式保護原則技術支援檢視<!-- 1069473 -->
IT 技術支援使用者現在可以在 [疑難排解] 刀鋒視窗中查看使用者授權狀態，和指派給使用者的應用程式保護原則應用程式的狀態。 如需詳細資訊，請參閱[疑難排解](./help-desk-operators.md)。

### <a name="device-configuration"></a>裝置設定

#### <a name="control-website-visits-on-ios-devices----723832---"></a>控制 iOS 裝置上的網站瀏覽<!-- 723832 -->
您現在可以使用下列兩種方法，來控制 iOS 裝置使用者可以瀏覽的網站：

- 使用 Apple 內建網路內容篩選器新增允許和封鎖的 URL。

- 僅允許 Safari 瀏覽器存取指定的網站。 針對您指定的每個網站，會在 Safari 中建立書籤。

如需詳細資訊，請參閱[適用於 iOS 裝置的網路內容篩選器設定](web-content-filter-settings-ios.md)。

#### <a name="preconfigure-device-permissions-for-android-for-work-apps----621614---"></a>預先設定 Android for Work 應用程式的裝置權限 <!-- 621614 -->
對於部署到 Android for Work 裝置工作設定檔的應用程式，您現在可以設定個別應用程式的權限狀態。  根據預設，需要裝置權限 (例如存取位置或裝置相機) 的 Android 應用程式會提示使用者接受或拒絕授與權限。  例如，若應用程式會使用裝置的麥克風，則系統會提示使用者授與應用程式使用麥克風的權限。 此功能可讓您代表使用者定義權限。  您可以設定權限以 a) 自動拒絕而不通知使用者，b) 自動核准而不通知使用者，或 c) 提示使用者接受或拒絕。 如需詳細資訊，請參閱 [Microsoft Intune 中的 Android for Work 裝置限制設定](device-restrictions-android-for-work.md)。

#### <a name="define-app-specific-pin-for-android-for-work-devices----728976-1102534---"></a>針對 Android for Work 裝置定義應用程式特定的 PIN <!-- 728976, 1102534 -->
工作設定檔做為 Android for Work 裝置管理的 Android 7.0 和更新版本裝置，可讓管理員定義僅適用於工作設定檔中的應用程式的密碼原則。  這些選項包括：

- 僅定義全裝置密碼原則：這是使用者必須用來解鎖整個裝置的密碼。
- 僅定義工作設定檔密碼原則：每當開啟工作設定檔中的應用程式時，系統就會提示使用者輸入密碼。
- 定義裝置和工作設定檔原則：IT 管理員可定義具有不同強度的裝置密碼原則和工作設定檔密碼原則 (例如，使用 4 位數 PIN 來解鎖裝置，但必須使用 6 位數 PIN 來開啟任何工作應用程式)。

如需詳細資訊，請參閱 [Microsoft Intune 中的 Android for Work 裝置限制設定](device-restrictions-android-for-work.md)。

> [!NOTE]
> 此功能僅適用於 Android 7.0 及更新版本。  根據預設，使用者可使用這兩個個別定義的 PIN，或選擇結合這兩個定義的 PIN，以組成包含這兩者的最強式密碼。

#### <a name="new-settings-for-windows-10-devices----978585---"></a>Windows 10 裝置的新設定<!-- 978585 -->
我們已新增可控制數種功能 (例如無線顯示器、裝置探索、工作切換和 SIM 卡錯誤訊息) 的 [Windows 裝置限制設定](device-restrictions-windows-10.md)。

#### <a name="updates-to-certificate-configuration----918991-and-823198---"></a>憑證設定的更新<!-- 918991 and 823198 -->
建立 SCEP 憑證設定檔時，針對 [主體名稱格式]，iOS、Android 和 Windows 裝置可使用 [自訂] 選項。 在此更新之前，[自訂] 欄位僅適用於 iOS 裝置。 如需詳細資訊，請參閱[如何建立 SCEP 憑證設定檔] (certificates-scep-configure.md#how-to-create-a-scep-certificate-profile)。

建立 PKCS 憑證設定檔時，針對 [主體別名]，可使用 [自訂 Azure AD 屬性]。 當您選取 [自訂 Azure AD 屬性] 時，可使用 [部門] 選項。 如需詳細資訊，請參閱[如何建立 PKCS 憑證設定檔](certficates-pfx-configure.md#create-a-device-configuration-profile)。

#### <a name="configure-multiple-apps-that-can-run-when-an-android-device-is-in-kiosk-mode----662059---"></a>設定 Android 裝置處於 kiosk 模式時可執行的多個應用程式<!-- 662059 -->
Android 裝置處於 kiosk 模式時，之前只能設定一個允許執行的應用程式。 您現在可以使用應用程式識別碼、存放區 URL或藉由選取您已管理的 Android 應用程式來設定多個應用程式。 如需詳細資訊，請參閱 [Kiosk 模式設定](device-restrictions-android.md#kiosk)。



## <a name="april-2017"></a>2017 年 4 月

### <a name="support-for-managing-the-apple-classroom-app"></a>支援管理 Apple「課堂」應用程式
您現在可在 iPad 裝置上管理 iOS「課堂」應用程式。 使用正確的課堂和學生資料，在老師的 iPad 上設定「課堂」應用程式，然後設定學生的 iPad 向課堂註冊，這樣您就能使用應用程式控制它們。
如需詳細資訊，[設定 iOS 的教育設定](education-settings-configure-ios.md)。

### <a name="support-for-managed-configuration-options-for-android-apps----621621---"></a>支援 Android 應用程式的受管理設定選項 <!-- 621621 -->
Intune 現在可以設定 Play 商店中支援受控設定選項的 Android 應用程式。  這項功能可讓 IT 人員檢視應用程式所支援的設定值清單，並提供頂級的引導式 UI，讓 IT 人員可以設定這些值。

### <a name="new-android-policy-for-complex-pins----722069---"></a>新增複雜 PIN 碼的 Android 原則 <!-- 722069 -->
您現在可以在 Android 裝置設定檔中，針對執行 Android 5.0 和更新版本的裝置，將必要的[密碼](device-restrictions-android.md#password)類型設定為複雜數字。  使用此設定可防止裝置使用者建立包含重複或連續數字的 PIN 碼，例如 1111 或 1234。

### <a name="additional-support-for-android-for-work-devices"></a>Android for Work 裝置的其他支援
- **管理密碼和工作設定檔設定** <!-- 612808 -->

  這項新的 Android for Work 裝置限制原則現在可讓您在所管理的 Android for Work 裝置上管理密碼和工作設定檔設定。

- **允許工作和個人設定檔間的資料共用** <!-- 1045102 -->

Android for Work 裝置限制設定檔現在有新的選項，可協助您設定工作和個人設定檔之間的資料共用。

- **限制工作和個人設定檔間的複製和貼上** <!-- 1046094 -->

  Android for Work 裝置的新自訂裝置設定檔現在可讓您限制是否允許工作和個人應用程式間的複製和貼上動作。

如需詳細資訊，請參閱 [Android for Work 的裝置限制](device-restrictions-android-for-work.md)。

### <a name="assign-lob-apps-to-ios-and-android-devices----1057568---"></a>將 LOB 應用程式指派給 iOS 和 Android 裝置 <!-- 1057568 -->
您現在可以將 [iOS](lob-apps-ios.md) 版企業營運 (LOB) 應用程式 (.ipa 檔案) 和 [Android](lob-apps-android.md) 版企業營運應用程式 (.apk 檔案) 指派給使用者或裝置。


###  <a name="new-device-policies-for-ios----723774-723815-723826-723830---"></a>iOS 的新裝置原則 <!-- 723774, 723815, 723826, 723830 -->
- **主畫面上的應用程式**：控制使用者會在[其 iOS 裝置的主畫面](home-screen-settings-ios.md)上看到哪些應用程式。 這項原則會變更主畫面的配置，但不會部署任何應用程式。

- **AirPrint 裝置的連線**：控制 iOS 裝置的使用者可以連線到哪些 [AirPrint 裝置](air-print-settings-ios-macos.md) (網路印表機)。

- **AirPlay 裝置的連線**：控制 iOS 裝置的使用者可以連線到哪些 [AirPlay 裝置](airplay-settings-ios.md) (例如 Apple TV)。

- **自訂鎖定畫面訊息**：設定使用者將會在其 iOS 裝置的鎖定畫面上看到的自訂訊息，這會取代預設鎖定畫面訊息。 如需詳細資訊，請參閱[啟動 iOS 裝置上的遺失模式](device-lost-mode.md)

### <a name="restrict-push-notifications-for-ios-apps----723767---"></a>限制 iOS 應用程式的推播通知 <!-- 723767 -->
在 Intune 裝置限制設定檔中，您現在可以設定 iOS 裝置的下列[通知設定](app-notification-settings-ios.md)：

- 完全開啟或關閉指定應用程式的通知。
- 在通知中心內開啟或關閉指定應用程式的通知。
- 指定警示類型，可以是 [無]、[橫幅] 或 [Modal Alert] (強制回應警示)。
- 指定此應用程式是否允許徽章。
- 指定是否允許通知音效。

### <a name="configure-ios-apps-to-run-in-single-app-mode-autonomously----737837---"></a>設定 iOS 應用程式在單一應用程式模式中自發執行 <!-- 737837 -->
您現在可以使用 Intune 裝置設定檔，設定 iOS 裝置在[自發性單一應用程式模式](device-restrictions-ios.md#autonomous-single-app-mode-supervised-only)中執行指定的應用程式。 設定此模式並執行應用程式時，裝置會被鎖定，因此只能執行該應用程式。 一個例子是當您設定應用程式讓使用者在裝置上進行測試時。 當應用程式的動作完成時，或當您移除此原則時，裝置就會回到其正常狀態。

### <a name="configure-trusted-domains-for-email-and-web-browsing-on-ios-devices----723765---"></a>為 iOS 裝置上的電子郵件和網頁瀏覽設定受信任的網域 <!-- 723765 -->
您現在可以從 iOS 裝置限制設定檔設定下列[網域設定](device-restrictions-ios.md#domains)：

- **未標示的電子郵件網域** - 使用者傳送或接收的電子郵件，若不符合您於此處所指定的網域，會標示為不受信任。

- **受管理的 Web 網域** - 從您於此處指定的 URL 下載之文件，會視為受管理的文件 (僅限 Safari)。  

- **Safari 密碼自動填入網域** - 使用者在 Safari 中可以儲存的密碼，只有來自與此處指定的模式相符之 URL 的密碼。 若要使用此設定，裝置必須在受監督的模式下，且未設定供多重使用者之用。 (iOS 9.3+)


### <a name="vpp-apps-available-in-ios-company-portal----748782---"></a>IOS 公司入口網站中可以使用 VPP 應用程式 <!-- 748782 -->
您現在可以將 iOS 大量採購 (VPP) 應用程式當做「可用」的安裝指派給使用者。 終端使用者必須有 Apple Store 帳戶，才能安裝應用程式。

### <a name="synchronize-ebooks-from-apple-vpp-store----800878---"></a>從 Apple VPP Store 同步處理電子書 <!-- 800878 -->
您現在可以將從 Apple 大量採購程式市集購買的[書籍與 Intune 同步處理](vpp-apps-ios.md)，然後將這些書籍指派給使用者。

### <a name="multi-user-management-for-samsung-knox-standard-devices----971988---"></a>Samsung Knox Standard 裝置的多使用者管理 <!-- 971988 -->
Intune 的[多使用者管理](android-enroll.md)現在支援執行 Samsung Knox Standard 的裝置。 這表示終端使用者可以使用其 Azure Active Directory 認證登入和登出裝置，而且該裝置不論是否正在使用，都會集中管理。  當使用者登入時，他們可以存取應用程式，並將任何原則套用到這些應用程式。 當使用者登出時，會清除所有應用程式資料。

### <a name="additional-windows-device-restriction-settings----818566---"></a>其他 Windows 裝置限制設定 <!-- 818566 -->
我們新增了其他 [Windows 裝置限制設定](device-restrictions-windows-10.md)的支援，例如額外的 Edge 瀏覽器支援、裝置鎖定畫面自訂、[開始] 功能表自訂、Windows 焦點搜尋集桌布，以及 Proxy 設定。

### <a name="multi-user-support-for-windows-10-creators-update----822547---"></a>Windows 10 Creators Update 的多使用者支援 <!-- 822547 -->
我們針對執行 Windows 10 Creators Update 並已加入 Azure Active Directory 網域的裝置，新增了[多使用者管理](windows-enroll.md)的支援。 這表示當不同的標準使用者使用其 Azure AD 認證登入裝置時，將會收到指派給其使用者名稱的任何應用程式和原則。 針對安裝應用程式等自助式案例，使用者目前無法使用公司入口網站來進行。

### <a name="fresh-start-for-windows-10-pcs---1004830---"></a>Windows 10 電腦的 Fresh Start<!-- 1004830 -->
適用於 Windows 10 電腦的新[「全新開始」裝置動作](device-fresh-start.md)現在已經可以使用。  當您發出此動作時，將會移除任何安裝在電腦上的應用程式，而且電腦會自動更新為最新版的 Windows。 這可用來協助移除通常會隨新電腦提供之預先安裝的 OEM 應用程式。 您可以設定是否在發出此裝置動作時保留使用者資料。

### <a name="additional-windows-10-upgrade-paths----903672---"></a>其他 Windows 10 升級路徑 <!-- 903672 -->
您現在可以建立[版本升級原則，來將裝置升級為](edition-upgrade-configure-windows-10.md)下列其他的 Windows 10 版本：

- Windows 10 Professional
- Windows 10 Professional N
- Windows 10 專業教育版
- Windows 10 專業教育版 N

### <a name="bulk-enroll-windows-10-devices----747607---"></a>大量註冊 Windows 10 裝置 <!-- 747607 -->
您現在可以使用 Windows 設定設計工具 (WCD) 將執行 Windows 10 Creators Update 的大量裝置加入到 Azure Active Directory 和 Intune。 若要為您的 Azure AD 租用戶啟用[大量 MDM 註冊](windows-bulk-enroll.md)，請使用 Windows 設定設計工具建立會將裝置加入到 Azure AD 租用戶的佈建套件，然後將套件套用至您要大量註冊及管理的公司擁有裝置。 將套件套用至裝置之後，裝置會加入 Azure AD、在 Intune 中註冊，並準備好供 Azure AD 使用者登入。  Azure AD 使用者是這些裝置上的標準使用者，並且會接收指派的原則和必要應用程式。 目前不支援自助式和公司入口網站案例。

### <a name="new-mam-settings-for-pin-and-managed-storage-locations----581122-736644---"></a>PIN 碼和受管理儲存位置的新 MAM 設定 <!-- 581122, 736644 -->
現在有兩個新的應用程式設定可協助您進行行動應用程式管理 (MAM) 案例：

- **在管理裝置 PIN 碼時停用應用程式 PIN 碼** - 偵測已註冊的裝置上是否有裝置 PIN 碼；如果有，則略過應用程式保護原則觸發的應用程式 PIN 碼。 這項設定可減少對在已註冊裝置上開啟啟用 MAM 的應用程式之使用者顯示的 PIN 提示次數。 這項功能適用於 Android 和 iOS。

- **選取要用於儲存公司資料的儲存體服務** - 可讓您指定要用於儲存公司資料的儲存位置。 使用者可以儲存至所選取的儲存位置服務，這表示將會封鎖未列出的其他所有儲存位置服務。

  支援的儲存位置服務清單：

  - OneDrive
  - 商務用 SharePoint Online
  - 本機儲存體

### <a name="help-desk-troubleshooting-portal----907448---"></a>服務台疑難排解入口網站 <!-- 907448 -->
新的[疑難排解入口網站](help-desk-operators.md)可協助服務台操作員和 Intune 系統管理員檢視使用者及其裝置，並執行工作以解決 Intune 技術問題。

## <a name="march-2017"></a>2017 年 3 月

### <a name="support-for-ios-lost-mode---431695--"></a>支援 iOS 遺失模式 <!--431695-->
針對 iOS 9.3 和更新的裝置，Intune 新增**遺失模式**的支援。 您現在可以鎖定裝置以防止任何使用，並在裝置的鎖定畫面上顯示訊息和連絡電話號碼。

使用者將無法解除鎖定裝置，除非系統管理員停用「遺失模式」。 啟用「遺失模式」時，您可以使用 [尋找裝置] 動作在 Intune 主控台中的地圖上顯示裝置的地理位置。

裝置必須是透過 DEP 註冊之公司擁有的 iOS 裝置，且處於受監督模式。

如需詳細資訊，請參閱[什麼是 Microsoft Intune 裝置管理？](device-management.md)

### <a name="improvements-to-device-actions-report---677150--"></a>裝置動作報告改善 <!--677150-->
我們改善了裝置動作報告以提升效能。 此外，您現在可以依狀態篩選報告。 例如，您可以篩選報告以僅顯示已完成的裝置動作。

### <a name="custom-app-categories---748805--"></a>自訂應用程式類別 <!--748805-->
您現在可以建立、編輯和指派您新增至 Intune 之應用程式的類別。 目前只能以英文指定類別。
請參閱[如何將應用程式新增至 Intune](apps-add.md)。

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
對於在 2017 年 1 月之後建立的 Intune 帳戶，Intune 已經啟用使用 Azure 入口網站中的「註冊裝置」工作負載直接存取 Apple 註冊案例。 Apple 註冊預覽原本只能從 Azure 入口網站中的連結存取。 在 2017 年 1 月之前建立的 Intune 帳戶，將需要進行一次性移轉，才能在 Azure 中使用這些功能。 移轉的排程尚未宣布，但將會盡快提供詳細資料。 如果您現有的帳戶無法存取預覽，我們強烈建議您建立試用帳戶來測試新的體驗。


## <a name="february-2017"></a>2017 年 2 月

### <a name="ability-to-restrict-mobile-device-enrollment---747600-795782--"></a>限制行動裝置註冊的能力 <!--747600, 795782-->
Intune 正在新增新的註冊限制，以控制哪些行動裝置平台可以註冊。 Intune 將行動裝置平台分為 iOS、macOS、Android、Windows 和 Windows Mobile。

* 限制行動裝置註冊不會限制電腦用戶端註冊。  
* 僅限 iOS 與 Android，有一個額外選項可阻擋註冊個人擁有的裝置。

Intune 會將所有的新裝置標示為個人，除非 IT 系統管理員採取動作將它們標示為公司擁有，如[本文章](https://docs.microsoft.com/intune-classic/deploy-use/manage-corporate-owned-devices)所說明。

### <a name="view-all-actions-on-managed-devices---677150--"></a>檢視受管理裝置上的所有動作 <!--677150-->
新的__裝置動作__報表會顯示曾執行遠端動作的人員，像是裝置恢復出廠預設值，並會另外顯示該動作的狀態。 請參閱[什麼是裝置管理？](device-management.md)。

### <a name="non-managed-devices-can-access-assigned-apps---664691--"></a>未受管理的裝置可以存取已指派的應用程式 <!--664691-->
iOS 和 Android 使用者能夠在他們未受管理的裝置上，安裝指派給他們的「無須註冊即可使用」應用程式，這屬於公司入口網站的設計變更。 使用 Intune 認證，使用者能夠登入公司入口網站，並查看指派給他們的應用程式清單。 「無須註冊即可使用」應用程式的應用程式套件，可透過公司入口網站下載取得。 這項變更不會影響需要註冊才能安裝的應用程式，因為如果使用者想要安裝這些應用程式，系統會提示他們註冊裝置。

### <a name="custom-app-categories---748805--"></a>自訂應用程式類別 <!--748805-->
您現在可以建立、編輯和指派您新增至 Intune 之應用程式的類別。 目前只能以英文指定類別。
請參閱[如何將應用程式新增至 Intune](apps-add.md)。

### <a name="display-device-categories---814654--"></a>顯示裝置類別 <!--814654-->
裝置清單現在會以資料行顯示裝置類別。 您也可以在裝置內容刀鋒視窗的內容區段中編輯類別。 請參閱[如何將應用程式新增至 Intune](apps-add.md)。

### <a name="configure-windows-update-for-business-settings---776716--"></a>設定商務用 Windows Update 的設定 <!--776716-->

「Windows 即服務」是一種為 Windows 10 提供更新的新做法。 從 Windows 10 開始，任何新的「功能更新」和「品質更新」都會包含所有先前的更新內容。 這表示只要您安裝了最新的更新，就能確定您的 Windows 10 裝置已完全更新至最新版。 不同於舊版 Windows，您現在必須安裝整個更新而不是部分更新。

使用商務用 Windows Update，可以簡化更新管理體驗，因此您不需要核准裝置群組的個別更新。 只要設定更新首度發行策略，您還是可以管理環境中的風險，Windows Update 會確保在適當的時間安裝更新。 Microsoft Intune 可讓您在裝置上設定更新設定，並可讓您延後更新的安裝。 Intune 不會儲存更新，只會儲存更新原則指派。 裝置直接存取 Windows Update 進行更新。使用 Intune 設定及管理 **Windows 10 更新響鈴**。 更新響鈴是一組包含何時及如何安裝 Windows 10 更新的設定。 如需詳細資訊，請參閱[設定商務用 Windows Update 的設定](windows-update-for-business-configure.md)。

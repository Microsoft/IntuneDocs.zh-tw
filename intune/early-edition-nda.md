---
title: 舊版 - Microsoft Intune
titlesuffix: ''
description: Microsoft Intune 舊版
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 12/3/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.openlocfilehash: 35298713738c666ca19d57e647412729a85bbc4a
ms.sourcegitcommit: 5058dbfb0e224207dd4e7ca49712c6ad3434c83c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/08/2018
ms.locfileid: "53112828"
---
# <a name="the-early-edition-for-microsoft-intune---december-2018"></a>Microsoft Intune 的舊版 - 2018 年 12 月

> [!Note]
> NDA 通知：下列變更正在 Intune 的開發過程中。 這項資訊會在極有限的基礎下根據 NDA 共用。 請不要在社交媒體或公用網站上張貼任何這項資訊，例如 Twitter、UserVoice、Reddit 等等。 

**舊版**提供 Microsoft Intune 即將發行版本要推出的功能清單 (透過 NDA 共用)。 此資訊以有限的基礎提供，並可能有所變更。 請不要在 UserVoice 上推文、張貼，或在您公司的外部分享這項資訊。 這裡列出的一些功能可能有截止日期，而且可能會延遲到未來的版本。 其他功能正在實驗 (測試) 中進行測試，以確保它們可供客戶使用。 如果您有任何問題或疑慮，請洽詢您的 Microsoft 產品群組連絡人。

此頁面會定期更新。 請回來查看其他更新。

<!--
## What's coming to Intune in the Azure portal  
## What's coming to Intune apps
## Notices
-->
 
## <a name="intune-in-the-azure-portal"></a>Azure 入口網站中的 Intune

<!-- 1812 start -->

### <a name="android-enterprise-app-we-app-deployment----1171203---"></a>Android 企業 APP-WE 應用程式部署 <!-- 1171203 -->
針對未註冊的無註冊應用程式保護原則 (APP-WE) 部署案例中的 Android 裝置，您就能使用受控的 Google Play，將市集應用程式和 LOB 應用程式部署給使用者。 具體來說，IT 可以為終端使用者提供應用程式目錄和安裝體驗，藉由允許從不明來源進行安裝，就不再需要終端使用者放寬其裝置的安全性狀態。 此外，此部署案例將提供已改善的使用者體驗。

### <a name="new-options-to-automatically-connect-and-persist-rules-when-using-dns-settings-on-windows-10-and-later-devices----1333665-2999078---"></a>在 Windows 10 及更新版裝置上使用 DNS 設定時自動連線且持續規則的新選項 <!-- 1333665, 2999078 -->
在 Windows 10 及更新版裝置上，您將能建立 VPN 組態設定檔，其中包含可用以解析網域 (例如 contoso.com) 的 DNS 伺服器清單。 這將包含可用於名稱解析的新設定 ([裝置設定] > [設定檔] > [建立設定檔] > 針對平台選擇 [Windows 10 及更新版本] > 針對設定檔類型選擇 [VPN] > [DNS 設定] >[新增])： 

- **自動連線**：若**已啟用**，裝置就會在連絡您輸入的網域 (例如 contoso.com) 時，自動連線至 VPN。
- **永續性**：根據預設，只要裝置會使用此 VPN 設定檔進行連線，所有的名稱解析原則表格 (NRPT) 規則都會處於作用中狀態。 已在 NRPT 規則上**啟用**此設定時，此規則就會在裝置上維持作用中狀態，即使在 VPN 中斷連線或移除 VPN 設定檔時也一樣。 此規則在手動移除之前會保持作用中狀態，而您可以使用 PowerShell 加以移除。

[Windows 10 VPN 設定](vpn-settings-windows-10.md)會說明目前的設定清單。 

### <a name="use-smime-to-encrypt-and-sign-a-users-multiple-devices-----1333642-eeready---"></a>使用 S/MIME 加密和簽署使用者的多個裝置 <!-- 1333642 eeready -->
將支援使用新匯入之憑證設定檔的 S/MIME 電子郵件加密 ([裝置設定] > [設定檔] > [建立設定檔] > 選取平台 > [PKCS 匯入的憑證] 設定檔類型)。 在 Intune 中，您可以匯入 PFX 格式的憑證。 Intune 接著可以將這些相同的憑證提供給單一使用者所註冊的多個裝置。 這也包括：

- 原生 iOS 電子郵件設定檔支援啟用 PFX 格式之已匯入憑證的 S/MIME 加密。
- Windows Phone 10 裝置上的原生郵件應用程式會自動使用 S/MIME 憑證。
- 私人憑證可以跨多個平台提供。 但並非所有電子郵件應用程式都支援 S/MIME。
- 在其他平台上，您可能需要手動設定郵件應用程式來啟用 S/MIME。  
- 支援 S/MIME 加密的電子郵件應用程式可能會以 MDM 無法支援的方式來處理 S/MIME 電子郵件加密的憑證擷取 (例如從其發行者的憑證存放區中讀取)。

支援於：Windows、Windows Phone 10、macOS、iOS、Android

### <a name="help-and-support-page-in-the-windows-company-portal-app----1488939---"></a>Windows 公司入口網站應用程式中的 [說明及支援] 頁面 <!-- 1488939 -->
系統將在 Windows 公司入口網站應用程式中新增頁面。 [說明及支援] 頁面將提供技術服務人員的連絡資訊。 此外，終端使用者將能在遇到問題時傳送公司入口網站記錄。 此網頁也會提供 [常見問題集] 區段來協助終端使用者。

### <a name="use-trusted-network-detection-for-vpn-profiles-on-windows-10-devices----1500165---"></a>針對 Windows 10 裝置上的 VPN 設定檔使用受信任的網路偵測 <!-- 1500165 -->
使用受信任的網路偵測時，若使用者已經位於受信任的網路上，您將能防止 VPN 設定檔自動建立 VPN 連線。 您將能新增 DNS 尾碼，在執行 Windows 10 及更新版本的裝置上啟用受信任的網路偵測 ([裝置設定] > [設定檔] > [建立設定檔] > 針對平台選擇 [Windows 10 及更新版本] > 針對設定檔類型選擇 [VPN])。
[Windows 10 VPN 設定](vpn-settings-windows-10.md)會列出目前的 VPN 設定。

### <a name="the-intune-app-sdk-will-support-256-bit-encryption-keys----1832174---"></a>Intune App SDK 將支援 256 位元的加密金鑰 <!-- 1832174 -->
適用於 iOS 的 Intune App SDK 將會在應用程式保護原則啟用加密時，使用 256 位元的加密金鑰。 SDK 將繼續提供 128 位元金鑰的支援，以取得與使用較舊 SDK 版本之內容和應用程式的相容性。

### <a name="enabled-shared-pc-settings-in-intune-profile----1907917---"></a>已在 Intune 設定檔中啟用共用的 PC 設定 <!-- 1907917 -->
您目前可以使用自訂的 OMA-URI 設定，在 Windows 10 電腦裝置上設定共用的 PC 設定。 新的設定檔將會新增來設定共用的 PC 設定 ([裝置設定] > [設定檔] > [建立設定檔] > [Windows 10 及更新版本] > [共用的多使用者裝置])。
適用於：Windows 10 及更新版本、Windows Holographic for Business

### <a name="intune-policies-update-authentication-method-and-company-portal-app-installation-----1927359---"></a>Intune 原則會更新驗證方法與公司入口網站應用程式安裝  <!-- 1927359 -->
Intune 將不再支援特定裝置上從 App Store 安裝的公司入口網站應用程式。 只有當您在註冊期間使用 Apple 設定助理進行驗證時，此變更才有意義。 此變更也只會影響透過下列各項註冊的 iOS 裝置：  
* Apple Configurator
* Apple Business Manager
* Apple School Manager
* Apple 裝置註冊方案 (DEP)

如果使用者從 App Store 安裝公司入口網站應用程式，接著嘗試透過它註冊這些裝置，則它們將會收到錯誤。 這些裝置只有在註冊期間透過 Intune 自動推送時，才會使用公司入口網站。 位於 Azure 入口網站上 Intune 中的註冊設定檔將會更新，如此您就能指定裝置的驗證方式，以及它們是否會收到公司入口網站應用程式。 如果您想讓 DEP 裝置使用者擁有公司入口網站，將必須在註冊設定檔中指定喜好設定。 此外，公司入口網站應用程式中的 [識別您的裝置] 畫面很快就會變成過時。  
若要在已經註冊的 DEP 裝置上安裝公司入口網站，您將必須移至 [Intune] > [用戶端應用程式]，然後使用應用程式設定原則來將它推送為受控應用程式。 有關如何執行這些步驟的詳細資料，將在未來的文件中加以概述。

### <a name="non-administrators-can-enable-bitlocker-on-windows-10-devices-joined-to-azure-ad---2147379---"></a>非系統管理員可以在已加入 Azure AD 的 Windows 10 裝置上啟用 BitLocker<!-- 2147379 -->
當您在 Windows 10 裝置上啟用 BitLocker 設定 ([裝置設定] > [設定檔] > [建立設定檔] > 針對平台選擇 [Windows 10 及更新版本] > 針對設定檔類型選擇 [Endpoint Protection] > [Windows 加密]) 時，您會新增 BitLocker 設定。 此更新包含新的 BitLocker 設定，可允許標準使用者 (非系統管理員) 啟用加密。 若要查看目前的設定，請參閱[適用於 Windows 10 的 Endpoint Protection 設定](endpoint-protection-windows-10.md#windows-encryption)。

### <a name="intune-app-pin----2298397---"></a>Intune 應用程式 PIN <!-- 2298397 -->
身為 IT 系統管理員，您將能設定終端使用者可在其 Intune 應用程式 PIN 必須變更之前等候的天數。 您可以藉由選取 [Intune] > [用戶端應用程式] > [應用程式保護原則] > [建立原則] > [設定] > [存取需求]，在 Azure 入口網站中提供新設定。 此功能將會在 iOS 和 Android 裝置上提供。 此設定支援正整數值。

### <a name="new-windows-10-update-settings----2626030-2512994---"></a>新的 Windows 10 更新設定 <!-- 2626030 2512994 -->
針對 Windows 10 更新通道，您將能夠：
- 在位於執行「2018 年 10 月更新」之機器的 Windows 10 機器上還原原始的自動更新設定。
- 設定新的軟體更新設定，可讓您封鎖或允許使用者從其機器的 [設定] 暫停更新安裝。 



### <a name="ios-email-profiles-can-use-smime-signing-and-encryption----2662949---"></a>iOS 電子郵件設定檔可以使用 S/MIME 簽署和加密 <!-- 2662949 -->
您將能建立包含不同設定的電子郵件設定檔。 這包括可在 iOS 裝置上用來簽署與加密電子郵件通訊的 S/MIME 設定 ([裝置設定] > [設定檔] > [建立設定檔]> 針對平台選擇 [iOS] > 針對設定檔類型選擇 [電子郵件])。

[iOS 電子郵件組態設定](email-settings-ios.md)會列出目前的設定。

### <a name="skip-more-setup-assistant-screens-on-an-ios-dep-device----2687509---"></a>在 iOS DEP 裝置上略過更多設定助理畫面 <!-- 2687509 -->
除了您目前可以略過的畫面之外，當使用者註冊裝置時，您還可以將 iOS DEP 裝置設定為略過 [設定助理] 中的下列畫面：顯示色調、隱私權、Android 移轉、首頁按鈕、iMessage 和 FaceTime、上架、Watch 移轉、外觀、螢幕使用時間、軟體更新、SIM 卡設定。
若要選擇要略過的畫面，請前往 [裝置註冊] > [Apple 註冊] > [註冊方案權杖]> 選擇權杖 > [設定檔] > 選擇設定檔 > [屬性] > [設定助理自訂] > 針對任何您想要略過的畫面選擇 [隱藏] > [確定]。

### <a name="some-bitlocker-settings-support-windows-10-pro-edition---2727036---"></a>部分 BitLocker 設定支援 Windows 10 專業版<!-- 2727036 -->
您將能建立組態設定檔，在 Windows 10 裝置上設定 Endpoint Protection 設定，包括 BitLocker。 這會針對部分 BitLocker 設定新增對 Windows 10 專業版的支援。 若要查看目前的 Windows 10 版本設定，請參閱[適用於 Windows 10 的 Endpoint Protection 設定](endpoint-protection-windows-10.md#windows-encryption)。
Intune 將提供其他裝置報告欄位，包括 Android 製造商、型號和安全性修補程式版本，以及 iOS 型號。 在 Intune 中，您將可藉由選取 [用戶端應用程式] > [應用程式保護狀態]，然後選擇 [應用程式保護報表：iOS、Android]，來提供這些欄位。 此外，這些參數將協助您設定適用於裝置製造商 (Android) 的 [允許] 清單、適用於裝置型號 (Android 和 iOS) 的 [允許] 清單，以及最低的 Android 安全性修補程式版本設定。 

### <a name="intune-device-reporting-fields----2748738---"></a>Intune 裝置報告欄位 <!-- 2748738 -->
Intune 將提供其他裝置報告欄位，包括 Android 製造商、型號和安全性修補程式版本，以及 iOS 型號。 在 Intune 中，您將可藉由選取 [用戶端應用程式] > [應用程式保護狀態]，然後選擇 [應用程式保護報表：iOS、Android]，來提供這些欄位。 此外，這些參數將協助您設定適用於裝置製造商 (Android) 的 [允許] 清單、適用於裝置型號 (Android 和 iOS) 的 [允許] 清單，以及最低的 Android 安全性修補程式版本設定。 

### <a name="shared-device-configuration-is-renamed-to-lock-screen-message-for-ios-devices-in-the-azure-portal----2809362---"></a>共用裝置設定已在 Azure 入口網站中針對 iOS 裝置重新命名為鎖定畫面訊息 <!-- 2809362 -->
當您建立適用於 iOS 裝置的組態設定檔時，您將能新增 [共用裝置設定] 設定，以便在鎖定畫面上顯示特定的文字。 這包含下列變更： 

- Azure 入口網站中的 [共用裝置設定] 已重新命名為「鎖定畫面訊息 (僅限受監督)」([裝置設定] > [設定檔] > [建立設定檔] > 針對平台選擇 [iOS] > 針對設定檔類型選擇 [裝置功能] > [鎖定畫面訊息])。
- 新增鎖定畫面訊息時，您可以在 [資產標籤資訊] 中插入序號、裝置名稱或另一個裝置特定的值以作為變數。 例如，您可以使用大括號來輸入 `Device name: {{device name}}` 或 `Serial number is {{serial number}}`。 [iOS 權杖](app-configuration-policies-use-ios.md#tokens-used-in-the-property-list)會列出可使用的可用權杖。

[在鎖定畫面上顯示訊息的設定](shared-device-settings-ios.md)會列出目前的設定。

### <a name="more-detailed-enrollment-restriction-failure-messaging----3111564--"></a>更詳細的註冊限制失敗訊息 <!-- 3111564-->
不符合註冊限制時，將提供更詳細的錯誤訊息。 若要查看這些訊息，請前往 [Intune] > [疑難排解] > 然後檢查 [註冊失敗] 表格。

### <a name="new-notification-hints-and-keyguard-settings-to-android-enterprise-device-owner-devices----3201839-3201843---"></a>將通知、提示和 Keyguard 設定新增至 Android 企業裝置擁有者裝置 <!-- 3201839 3201843 -->
以裝置擁有者身分執行時，此更新會包括 Android 企業裝置上的多個新功能。 若要使用這些功能，請前往 [裝置設定] > [設定檔] > [建立設定檔] > 在 [平台] 中選擇 [Android 企業] > 在 [設定檔類型] 中選擇 [僅限裝置擁有者] > [裝置限制]。
新功能包括： 
- 停用系統通知顯示，包括來電、系統警示、系統錯誤及更多功能
- 建議針對第一次開啟的應用程式略過開始教學課程和提示
- 停用進階的 Keyguard 設定，例如相機、通知、指紋解除鎖定及更多功能

若要查看目前的設定，請前往 [Android 企業裝置限制設定](device-restrictions-android-for-work.md)。

### <a name="android-enterprise-device-owner-devices-can-use-always-on-vpn-connections----3202194---"></a>Android 企業裝置擁有者裝置可以使用 Always On VPN 連線 <!-- 3202194 -->
在此更新中，您可以在 Android 企業裝置擁有者裝置上使用 Always-On VPN 連線。 在使用者將裝置解除鎖定、裝置重新啟動，或是變更無線網路時，Always-On VPN 連線將會保持連線或立即重新連線。 您也可以將連線設定成「鎖定」模式，這會封鎖所有流量，直到 VPN 連線開始作用為止。
您可以在 [裝置設定] > [設定檔] > [建立設定檔] > 針對平台選擇 [Android 企業] > 針對 [僅限裝置擁有者] 選擇 [裝置限制] > [連線能力] 設定中啟用 Always-On VPN。 若要查看目前的設定，請前往 [Android 企業裝置限制設定](device-restrictions-android-for-work.md)。

### <a name="new-setting-to-end-processes-in-task-manager-on-windows-10-devices----3285177---"></a>Windows 10 裝置上的工作管理員中用來結束處理序的新設定 <!-- 3285177 --> 
此更新包含使用 Windows 10 裝置上的工作管理員來結束處理序的新設定。 您可以使用裝置組態設定檔 ([裝置設定] > [設定檔] > [建立設定檔] > 在 [平台] 中選擇 [Windows 10] > 在 [設定檔類型] 中選擇 [裝置限制] > [一般] 設定)，來選擇允許或阻止此設定。
若要查看目前的設定，請前往 [Windows 10 裝置限制設定](device-restrictions-windows-10.md)。
適用於：Windows 10 及更新版本

### <a name="administrative-templates-are-in-public-preview-and-moved-to-their-own-configuration-profile----3322847---"></a>系統管理範本目前處於公開預覽狀態且已移至它們自己的組態設定檔 <!-- 3322847 -->
Intune 中的系統管理範本 ([裝置設定] > [系統管理範本]) 目前為個人預覽版。 使用此更新：系統管理範本包含約 300 個可在 Intune 中管理的設定。 這些設定先前只存在於群組原則編輯器中。
系統管理範本會在公開預覽版中提供。系統管理範本正從 [裝置設定] > [系統管理範本] 移至 [裝置設定] > [設定檔] >[建立設定檔] > 在 [平台] 中選擇 [Windows 10 及更新版本]、在 [設定檔類型] 中選擇 [系統管理範本]。
已啟用報告。適用對象：Windows 10 及更新版本


<!-- 1810 start -->

### <a name="use-microsoft-recommended-settings-with-security-baselines----2055484---"></a>使用針對安全性基準 <!-- 2055484 --> 的 Microsoft 建議設定
Intune 會和其他著重安全性的服務整合，包含 Windows Defender ATP 和 Office 365 ATP。 客戶持續不斷要求一種常見策略，以及橫跨 Microsoft 365 服務，極具凝聚力的一組端點對端點安全性工作流程。 我們的目標是調整策略，建置能擔任安全性作業和常見系統管理工作間橋樑的解決方案。 在 Intune 中，我們試圖透過發佈一組 Microsoft 建議的「安全性基準」(**Intune** > **安全性基準**)，來達到此目標。  系統管理員將能夠直接從這些基準建立安全性政策，並將它們部署到其使用者。 他們也可以自訂最佳做法建議項目，以符合其組織的需求。 Intune 會確保裝置符合這些基準的規範，並會通知系統管理員不合規的使用者或裝置。

### <a name="scope-tags-for-apps---1081941---"></a>應用程式的範圍標籤 <!--1081941 -->
您可以建立範圍標籤來限制對 Intune 資源的存取。 將範圍標籤新增至角色指派，然後將範圍標籤新增至設定檔。 此角色只能存取設定檔具有相符範圍標籤 (或無範圍標籤) 的資源。
若要建立範圍標籤，請選擇 [Intune roles] \(Intune 角色\) > [Scope (Tags)] \(範圍 (標籤)\) > [建立]。
若要將範圍標籤新增至角色指派，請選擇 [Intune roles] \(Intune 角色\) > [All roles] \(所有角色\) > [Policy and Profile Manager] \(原則和設定檔管理員\) > [作業] > [Scope (Tags)] \(範圍 (標籤)\)。
若要將範圍標籤新增至設定檔，請選擇 [裝置設定] > [設定檔] > 選擇設定檔 > [屬性] > [Scope (Tags)] \(範圍 (標籤)\)。

### <a name="tenant-health-dashboard----1124854---"></a>租用戶健康狀態儀表板 <!-- 1124854 -->
Intune 中的 [租用戶健康狀態] 頁面可在單一位置提供您租用戶的狀態資訊。 頁面分為 4 個區段：  
- **租用戶詳細資料**：包含資訊，例如您的 MDM 授權單位、您租用戶中的總註冊裝置數，以及您的授權計數。 此區段也會提供您租用戶目前的服務版本。
- **連接器狀態**：包含設定連接器的資訊，例如 Apple VPP、商務用 Microsoft Store，以及憑證連接器。 根據其目前狀態，連接器會標記為 [良好]、[警告]，或 [不良]。
- **Intune 服務健康狀態**：包含您租用戶正在發生的事件或中斷。 此區段中的資訊是直接從 Office 訊息中心 ([https://portal.office.com](https://portal.office.com)) 擷取的。
- **Intune 新聞**：包含您租用戶使用中的訊息，其中可能會包含像是您的租用戶已接收到最新的 Intune 功能等通知。 此區段中的資訊是直接從 Office 訊息中心 ([https://portal.office.com](https://portal.office.com)) 擷取的。


### <a name="deployed-wip-policies-without-user-enrollment----1434452---"></a>無使用者註冊的部署 WIP 原則 <!-- 1434452 -->
Windows 資訊保護 (WIP) 原則將能在無須 MDM 使用者註冊其 Windows 10 裝置的情況下部署。 此設定允許公司根據 WIP 設定保護其公司文件，同時允許使用者維持其自身 Windows 裝置的管理。 一旦使用 WIP 原則保護文件，Intune 系統管理員便可以選擇性抹除受保護的資料。 透過選取使用者和裝置，並傳送抹除要求，所有透過 WIP 原則保護的資料都會無法使用。 從 Azure 入口網站中的 Intune，選取 [行動應用程式] > [應用程式選擇性抹除]。


<!-- 1809 start -->  

### <a name="app-protection-policy-app-settings-for-web-data----2662995---"></a>適用於 Web 資料的應用程式防護原則 (APP) 設定 <!-- 2662995 -->
Android 及 iOS 裝置上適用於 Web 內容的應用程式原則設定會進行更新，提升處理 HTTP 和 HTTPS Web 連結的能力，以及透過 iOS 通用連結和 Android 應用程式連結進行資料轉送的能力。  

<!-- 1808 start -->

### <a name="apple-vpp-token-used-by-another-mdm----1488946---"></a>另一個 MDM 所使用的 Apple VPP 權杖 <!-- 1488946 -->
如果 Intune 和另一個 MDM 都正在使用 Apple 大量採購方案 (VPP) 權杖，則 Intune 會偵測並顯示詳細資料。

### <a name="retired-devices-in-the-device-compliance-dashboard----1981119---"></a>[裝置合規性] 儀表板中的已淘汰裝置 <!-- 1981119 -->
在未來的更新中，將會從 [裝置合規性] 儀表板中移除已淘汰裝置。 這會變更您的合規性數字。


### <a name="change-in-the-update-process-for-on-premises-connectors----2277554---"></a>內部部署連接器之更新程序中的變更 <!-- 2277554 -->
根據客戶的意見反應，將會變更內部部署連接器更新方式。 在您初次安裝內部部署連接器之後，將會自動更新。 這項變更會從新的適用於 Microsoft Intune 的 PFX 憑證連接器開始，之後將推出至其他類型的內部部署連接器。 

<!-- 1807 start -->

### <a name="check-for-configuration-manager-compliance----2192052---"></a>檢查 Configuration Manager 合規性 <!-- 2192052 -->
未來更新將會包括新的 System Center Configuration Manager 合規性設定 ([裝置相容性] > [原則] > [建立原則] > [Windows 10])。 Configuration Manager 會將訊號傳送至 Intune 合規性。 您可以使用 Intune 設定來要求所有傳回的 Configuration Manager 訊號都需是「符合規範」。

例如，您需要在裝置上安裝所有軟體更新。 在 Configuration Manager 中，此要求將會對應「已安裝」狀態。 如果裝置上的任何程式處於未知狀態，則裝置在 Intune 中將會不相容。

適用於 Windows 10 和更新版本



## <a name="notices"></a>通知

目前沒有任何作用中的通知。

### <a name="see-also"></a>請參閱
如需近期發展的詳細資料，請參閱 [Microsoft Intune 的新功能](whats-new.md)。




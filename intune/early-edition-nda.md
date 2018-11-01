---
title: 舊版
description: ''
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/03/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 606005c3d8abafe989b35841cebf8c11e1f6b04e
ms.sourcegitcommit: f69f2663ebdd9c1def68423e8eadf30f86575f7e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/10/2018
ms.locfileid: "49075875"
---
# <a name="the-early-edition-for-microsoft-intune---october-2018"></a>Microsoft Intune 的舊版 - 2018 年 10 月

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

<!-- 1810 start -->

### <a name="use-microsoft-recommended-settings-with-security-baselines----2055484---"></a>使用針對安全性基準 <!-- 2055484 --> 的 Microsoft 建議設定
Intune 會和其他著重安全性的服務整合，包含 Windows Defender ATP 和 Office 365 ATP。 客戶持續不斷要求一種常見策略，以及橫跨 Microsoft 365 服務，極具凝聚力的一組端點對端點安全性工作流程。 我們的目標是調整策略，建置能擔任安全性作業和常見系統管理工作間橋樑的解決方案。 在 Intune 中，我們試圖透過發佈一組 Microsoft 建議的「安全性基準」(**Intune** > **安全性基準**)，來達到此目標。  系統管理員將能夠直接從這些基準建立安全性政策，並將它們部署到其使用者。 他們也可以自訂最佳做法建議項目，以符合其組織的需求。 Intune 會確保裝置符合這些基準的規範，並會通知系統管理員不合規的使用者或裝置。

### <a name="remove-ability-for-admins-to-wipe-personal-devices-and-reset-passcodes----2934699---"></a>移除系統管理員抹除個人裝置及重設密碼的能力 <!-- 2934699 -->
為了減輕使用者針對公司系統管理員具備抹除其個人裝置能力的恐懼，[抹除](devices-wipe.md#wipe)和[重設密碼](device-passcode-reset.md)遠端動作已不再適用於個人裝置。 使用者可透過使用公司入口網站，從任何裝置重設其密碼及抹除其裝置。

### <a name="autopilot-support-for-hybrid-azure-active-directory-joined-devices----1048100---"></a>混合式 Azure Active Directory 聯結裝置的 Autopilot 支援 <!-- 1048100 -->
您將可以透過使用 Autopilot，來設定混合式 Azure Active Directory 聯結裝置。 裝置必須聯結到您組織的網路，才能使用混合式 Autopilot 功能。

### <a name="scope-tags-for-apps---1081941---"></a>應用程式的範圍標籤 <!--1081941 -->
您可以建立範圍標籤來限制對 Intune 資源的存取。 將範圍標籤新增至角色指派，然後將範圍標籤新增至設定檔。 此角色只能存取設定檔具有相符範圍標籤 (或無範圍標籤) 的資源。
若要建立範圍標籤，請選擇 [Intune roles] \(Intune 角色\) > [Scope (Tags)] \(範圍 (標籤)\) > [建立]。
若要將範圍標籤新增至角色指派，請選擇 [Intune roles] \(Intune 角色\) > [All roles] \(所有角色\) > [Policy and Profile Manager] \(原則和設定檔管理員\) > [作業] > [Scope (Tags)] \(範圍 (標籤)\)。
若要將範圍標籤新增至設定檔，請選擇 [裝置設定] > [設定檔] > 選擇設定檔 > [屬性] > [Scope (Tags)] \(範圍 (標籤)\)。

## <a name="tenant-health-dashboard----1124854---"></a>租用戶健康狀態儀表板 <!-- 1124854 -->
Intune 中的 [租用戶健康狀態] 頁面可在單一位置提供您租用戶的狀態資訊。 頁面分為 4 個區段：  
- **租用戶詳細資料**：包含資訊，例如您的 MDM 授權單位、您租用戶中的總註冊裝置數，以及您的授權計數。 此區段也會提供您租用戶目前的服務版本。
- **連接器狀態**：包含設定連接器的資訊，例如 Apple VPP、商務用 Microsoft Store，以及憑證連接器。 根據其目前狀態，連接器會標記為 [良好]、[警告]，或 [不良]。
- **Intune 服務健康狀態**：包含您租用戶正在發生的事件或中斷。 此區段中的資訊是直接從 Office 訊息中心 ([https://portal.office.com](https://portal.office.com)) 擷取的。
- **Intune 新聞**：包含您租用戶使用中的訊息，其中可能會包含像是您的租用戶已接收到最新的 Intune 功能等通知。 此區段中的資訊是直接從 Office 訊息中心 ([https://portal.office.com](https://portal.office.com)) 擷取的。

### <a name="enrollment-abandonment-report----1382924---"></a>註冊放棄報表 <!-- 1382924 -->
您可以在 [裝置註冊] > [監視] 下取得新報表，提供已放棄註冊的詳細資料。

### <a name="deployed-wip-policies-without-user-enrollment----1434452---"></a>無使用者註冊的部署 WIP 原則 <!-- 1434452 -->
Windows 資訊保護 (WIP) 原則將能在無須 MDM 使用者註冊其 Windows 10 裝置的情況下部署。 此設定允許公司根據 WIP 設定保護其公司文件，同時允許使用者維持其自身 Windows 裝置的管理。 一旦使用 WIP 原則保護文件，Intune 系統管理員便可以選擇性抹除受保護的資料。 透過選取使用者和裝置，並傳送抹除要求，所有透過 WIP 原則保護的資料都會無法使用。 從 Azure 入口網站中的 Intune，選取 [行動應用程式] > [應用程式選擇性抹除]。


### <a name="add-custom-brand-image-for-company-portal-app----1916266---"></a>新增公司入口網站應用程式的自訂品牌形象 <!-- 1916266 -->
作為 Microsoft Intune 系統管理員，您將能夠上傳自訂品牌形象，該影像會在公司入口網站應用程式中的使用者設定檔頁面上，作為背景影像顯示。 如需設定公司入口網站應用程式的詳細資訊，請參閱[如何設定 Microsoft Intune 公司入口網站應用程式](company-portal-app.md)。

### <a name="group-windows-autopilot-enrolled-devices-by-correlator-id----2075110---"></a>透過交互識別碼群組 Windows Autopilot 註冊裝置 <!-- 2075110 -->
Intune 將支援在透過 Configuration Manager 使用[適用於現有裝置的 Autopilot](https://techcommunity.microsoft.com/t5/Windows-IT-Pro-Blog/New-Windows-Autopilot-capabilities-and-expanded-partner-support/ba-p/260430)註冊時，使用交互識別碼來群組 Windows 裝置。 交互識別碼是 Autopilot 設定檔的參數。 Intune 會自動將 [Azure AD 裝置屬性 enrollmentProfileName](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership#using-attributes-to-create-rules-for-device-objects) 設為相等的 "OfflineAutopilotprofile-\<correlator ID\>"。 這會允許透過離線 Autopilot 註冊的 enrollmentprofileName 屬性，根據交互識別碼建立任意 Azure AD 動態群組。 


### <a name="support-for-ios-12-oauth-in-ios-email-profiles---2155106---"></a>在 iOS 電子郵件設定檔中支援 iOS 12 OAuth <!--2155106 -->
Intune 的 iOS 電子郵件設定檔將支援 iOS 12 OAuth。 若要查看這項功能，請選擇 [Intune] > [裝置設定] > [設定檔] > [建立設定檔] > [OAuth]。 若開啟此設定，則會發生兩件事：
1. 會向已瞄準的裝置發出新的設定檔。
2. 終端使用者將接收到提示，要求他們再次提供認證。

### <a name="new-required-password-type-default-setting-for-android-android-enterprise---2649963---"></a>適用於 Android、Android Enterprise 的新「必要密碼類型」預設設定 <!-- 2649963 -->
當您建立新的合規性原則 (針對 [平台] > [系統安全性]，選擇 [Intune] > [裝置合規性] > [原則] > [建立原則] > [Android] 或 [Android Enterprise]) 時，[必要密碼類型] 的預設值將會變更：目前預設值：裝置預設值；新的預設值：至少必須是數值。適用於：Android、Android Enterprise

### <a name="assign-autopilot-profiles-to-the-all-devices-virtual-group---2715522---"></a>將 Autopilot 設定檔指派給所有裝置虛擬群組 <!--2715522 -->
您將可以將 Autopilot 設定檔指派給所有裝置虛擬群組。 若要進行此動作，請選擇 [裝置註冊] > [Windows 註冊] > [部署設定檔]> 選擇設定檔 > [指派] > 在 [指派對象] 下方，選擇 [所有裝置]。

### <a name="new-azure-active-directory-terms-of-use-feature----2870393---"></a>新的 Azure Active Directory 使用條款功能 <!-- 2870393 -->
Azure Active Directory 將具備您可以改使用的條款功能，而無須使用現有 Intune 條款及條件。 Azure AD 使用條款功能可提供更多彈性，讓您決定要顯示哪些條款以及顯示的時機、具備更佳的當地語系化支援、對轉譯條款的方式擁有更大控制能力，以及改善回報。 Azure AD 使用條款需要 Azure Active Directory Premium P1，該項目也是 Enterprise Mobility + Security E3 套件的一部分。


### <a name="intune-will-maintain-the-office-localized-language-when-updating-office-on-end-users-machines----2971030---"></a>Intune 會在更新終端使用者電腦上的 Office 時保留 Office 當地語系化語言 <!-- 2971030 -->
當 Intune 在您終端使用者的電腦上安裝 Office 時，終端使用者會自動取得與其先前 .MSI Office 安裝相同的語言套件。 

<!-- 1809 start -->  

### <a name="intune-app-data-transfer-settings-on-ios-mdm-enrolled-devices----2244713---"></a>已註冊 MDM 之 iOS 裝置上的 Intune 應用程式資料轉送設定 <!-- 2244713 -->
您將能夠把已註冊 MDM 之 iOS 裝置上的 Intune 應用程式資料轉送設定的控制，與指定已註冊使用者的身分識別區分開來。 不使用 IntuneMAMUPN 的系統管理員將不會發現行為變更。 當此功能可用時，使用 IntuneMAMUPN 來控制已註冊裝置上資料轉送行為的系統管理員，應檢閱新的設定並視需要更新其應用程式設定。

### <a name="use-a-pre-shared-key-in-a-windows-10-wi-fi-profile----2662938---"></a>在 Windows 10 Wi-Fi 設定檔中使用預先共用金鑰 <!-- 2662938 -->
您將能夠搭配 WPA/WPA2-Personal 安全性通訊協定使用預先共用金鑰 (PSK)，來驗證適用於 Windows 10 的 Wi-Fi 組態設定檔。
目前您必須匯入 Wi-Fi 設定檔或是建立自訂的設定檔，才能使用預先共用金鑰。 [適用於 Windows 10 的 Wi-Fi 設定](wi-fi-settings-windows.md)列出目前的設定。 

### <a name="app-protection-policy-app-settings-for-web-data----2662995---"></a>適用於 Web 資料的應用程式防護原則 (APP) 設定 <!-- 2662995 -->
Android 及 iOS 裝置上適用於 Web 內容的應用程式原則設定會進行更新，提升處理 HTTP 和 HTTPS Web 連結的能力，以及透過 iOS 通用連結和 Android 應用程式連結進行資料轉送的能力。  

### <a name="autopilot-device-sync-frequency-increasing-to-every-12-hours----2753673---"></a>將 Autopilot 裝置同步頻率提升至每 12 小時同步一次 <!-- 2753673 -->
Autopilot 裝置將會每 12 小時同步一次，而不是每 24 小時。

### <a name="intune-landing-page-updates-and-node-rename---2867309---"></a>Intune 登陸頁面更新和節點重新命名 <!--2867309 -->
針對 Intune 登陸頁面的更新將包含全新變更的監視磚，以及能讓資料視覺效果更好的圖表。 [行動應用程式] 節點將會變更為 [用戶端應用程式]。

### <a name="increased-end-user-access-using-the-company-portal-app----772203---"></a>增加使用公司入口網站應用程式的終端使用者存取 <!-- 772203 -->
使用者將能夠從公司入口網站應用程式存取重要的帳戶動作，例如密碼重設和其 AAD 設定檔。  

<!-- 1808 start -->

### <a name="apple-vpp-token-used-by-another-mdm----1488946---"></a>另一個 MDM 所使用的 Apple VPP 權杖 <!-- 1488946 -->
如果 Intune 和另一個 MDM 都正在使用 Apple 大量採購方案 (VPP) 權杖，則 Intune 會偵測並顯示詳細資料。

### <a name="ios-version-number-and-build-number-are-shown----1892471---"></a>會顯示 iOS 版本號碼和組建編號 <!-- 1892471 -->
在 [裝置合規性] > [裝置合規性] 中，會顯示 iOS 作業系統版本。 在未來的更新中，也會顯示組建編號。
發行安全性更新時，Apple 通常會保留版本號碼，但更新組建編號。 顯示組建編號，即可輕鬆地檢查是否已安裝弱點更新。

### <a name="retired-devices-in-the-device-compliance-dashboard----1981119---"></a>[裝置合規性] 儀表板中的已淘汰裝置 <!-- 1981119 -->
在未來的更新中，將會從 [裝置合規性] 儀表板中移除已淘汰裝置。 這會變更您的合規性數字。


### <a name="change-in-the-update-process-for-on-premises-connectors----2277554---"></a>內部部署連接器之更新程序中的變更 <!-- 2277554 -->
根據客戶的意見反應，將會變更內部部署連接器更新方式。 在您初次安裝內部部署連接器之後，將會自動更新。 這項變更會從新的適用於 Microsoft Intune 的 PFX 憑證連接器開始，之後將推出至其他類型的內部部署連接器。 

<!-- 1807 start -->

### <a name="improved-company-portal-app-experience-for-device-enrollment-manager-users----675800---"></a>已改善裝置註冊管理員使用者的公司入口網站應用程式體驗 <!-- 675800 -->
當裝置註冊管理員 (DEM) 登入適用於 Windows 的公司入口網站應用程式時，應用程式只會列出 DEM 目前執行中的裝置。 這項改善會減少之前應用程式在嘗試載入所有 DEM 註冊裝置時所發生的逾時。  

### <a name="check-for-configuration-manager-compliance----2192052---"></a>檢查 Configuration Manager 合規性 <!-- 2192052 -->
未來更新將會包括新的 System Center Configuration Manager 合規性設定 ([裝置相容性] > [原則] > [建立原則] > [Windows 10])。 Configuration Manager 會將訊號傳送至 Intune 合規性。 您可以使用 Intune 設定來要求所有傳回的 Configuration Manager 訊號都需是「符合規範」。

例如，您需要在裝置上安裝所有軟體更新。 在 Configuration Manager 中，此要求將會對應「已安裝」狀態。 如果裝置上的任何程式處於未知狀態，則裝置在 Intune 中將會不相容。

適用於 Windows 10 和更新版本

### <a name="alerts-for-expiring-vpp-token-or-company-portal-license-running-low----2237572---"></a>VPP 權杖將過期或公司入口網站授權將不足的警示<!-- 2237572 -->
如果您在 DEP 註冊期間使用大量採購方案 (VPP) 預先佈建公司入口網站，則 Intune 會在 VPP 權杖即將過期以及公司入口網站授權即將不足時提醒您。

<!-- 1806 start -->

### <a name="3rd-party-keyboards-can-be-blocked-by-app-settings-on-ios----1248481---"></a>iOS 上的應用程式設定可封鎖第三方鍵盤 <!-- 1248481 -->
在 iOS 裝置上，Intune 系統管理員可以在存取原則保護應用程式中的組織資料時，封鎖第三方鍵盤的使用。 當應用程式保護原則 (APP) 設定為封鎖第三方鍵盤時，裝置使用者會在第一次使用第三方鍵盤與公司資料互動時收到一則訊息。 本機鍵盤以外的所有選項都會被封鎖，裝置使用者不會看到它們。 裝置使用者只會看到對話方塊訊息一次。 

<!-- 1805 start -->

### <a name="require-non-biometric-after-specified-timeout----1506985---"></a>在指定的逾時之後要求非生物特徵辨識 <!-- 1506985 --> 

透過在系統管理員指定的逾時之後要求非生物特徵辨識 PIN，Intune 可藉由限制使用生物特徵辨識身分識別來存取公司資料，為啟用行動應用程式管理 (MAM) 的應用程式增強安全性。 這些設定會影響依賴 Touch ID (iOS)、Face ID (iOS)、 Android 生物特徵辨識或其他未來的生物特徵辨識驗證方法來存取其啟用 APP/MAM 之應用程式的使用者。 這些設定可讓 Intune 系統管理員能夠更細微地控制使用者存取，並排除具有多個指紋或其他生物特徵辨識存取方法的裝置可能會向不正確的使用者顯示公司資料的情況。 在 Azure 入口網站中，開啟 [Microsoft Intune]。 選取 [行動裝置應用程式] > [應用程式保護原則] > [新增原則] > [設定]。 找出特定設定的 [存取] 區段。

<!-- 1803 start -->

### <a name="updating-the-help-and-feedback-experience-on-company-portal-app-for-android---1631531---"></a>更新 Android 的公司入口網站應用程式之說明與意見反應體驗 <!--1631531 -->

Android 公司入口網站應用程式的說明和意見反應體驗將更新，以與 Android 應用程式的最佳做法保持一致。 Android 公司入口網站應用程式將於接下來幾個月內更新，以將 [說明與意見反應] 功能表項目劃分為分開的 [說明] 與 [傳送意見反應] 功能表項目。 **說明**頁面將有**常見問題集**章節和**電子郵件支援** 按鈕，引導使用者上傳記錄給 Microsoft，並將電子郵件傳送給描述問題的公司支援。 **傳送意見反應**會透過標準 Microsoft 意見反應提交來引導使用者，並會提示使用者選擇「我喜歡某些項目」、「我不喜歡某些項目 」，或是「我有個想法」。



<!-- the following are present prior to 1711 -->

## <a name="notices"></a>通知

目前沒有任何作用中的通知。

### <a name="see-also"></a>另請參閱
如需近期發展的詳細資料，請參閱 [Microsoft Intune 的新功能](whats-new.md)。




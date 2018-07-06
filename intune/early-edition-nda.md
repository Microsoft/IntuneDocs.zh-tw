---
title: 舊版
description: ''
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 06/28/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 0500194f5afaba11f37b84bbdf606e6167632a71
ms.sourcegitcommit: afa2e84d5cadf5542ecabc26e61dc71919992a22
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2018
ms.locfileid: "37340171"
---
# <a name="the-early-edition-for-microsoft-intune---july-2018"></a>Microsoft Intune 的舊版 - 2018 年 7 月

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

<!-- 1807 start -->

### <a name="reset-device-passcodes-from-company-portal-app-for-windows-10----2101282---"></a>從 Windows 10 的公司入口網站應用程式重設裝置密碼 <!-- 2101282 --> 
您的員工很快可以直接從 Windows 10 的公司入口網站應用程式重設其裝置的 PIN 或密碼。 此功能將用於支援密碼重設的遠端及本機 Intune 受控裝置。 根據裝置類型，針對遠端裝置所提出的要求將會移除裝置的目前密碼，或建立暫時密碼。 要求重設本機裝置的使用者，將會重新導向至裝置的 [設定] 應用程式。

### <a name="use-smime-to-encrypt-and-sign-a-users-multiple-devices-----1333642---"></a>使用 S/MIME 加密和簽署使用者的多個裝置 <!-- 1333642 -->
未來更新將包括使用新匯入之憑證設定檔的 S/MIME 電子郵件加密 ([裝置設定] > [設定檔] > [建立設定檔] > 選取平台 > [PKCS imported certificate] \(PKCS 匯入的憑證\) 設定檔類型)。 在 Intune 中，您可以匯入 PFX 格式的憑證。 Intune 接著可以將這些相同的憑證提供給單一使用者所註冊的多個裝置。 這也包括：

- 原生 iOS 電子郵件設定檔支援啟用 PFX 格式之已匯入憑證的 S/MIME 加密。
- Windows Phone 10 裝置上的原生郵件應用程式會自動使用 S/MIME 憑證。
- 私人憑證可以跨多個平台提供。 但並非所有電子郵件應用程式都支援 S/MIME。
- 在其他平台上，您可能需要手動設定郵件應用程式來啟用 S/MIME。  
- 支援 S/MIME 加密的電子郵件應用程式可能會以 MDM 無法支援的方式來處理 S/MIME 電子郵件加密的憑證擷取 (例如從其發行者的憑證存放區中讀取)。

其支援：Windows、Windows Phone 10、macOS、iOS、Android

### <a name="use-vpp-device-licenses-to-pre-provision-the-company-portal-during-dep-enrollment----1608345---"></a>在 DEP 註冊期間，使用 VPP 裝置授權預先佈建公司入口網站 <!-- 1608345 -->
您將可以在裝置註冊計劃 (DEP) 註冊期間，使用大量採購方案 (VPP) 裝置授權預先佈建公司入口網站。 若要這麼做，當您建立或編輯註冊設定檔時，請指定您要用來安裝公司入口網站的 VPP 權杖。 請確定您的權杖未過期，而且您有足夠的公司入口網站應用程式權限。 如果權杖過期或授權不足，則 Intune會改為推送 App Store 公司入口網站 (這會提示您輸入 Apple 識別碼)。

### <a name="bulk-delete-devices-on-devices-blade----1793693---"></a>裝置刀鋒視窗上的大量刪除裝置 <!-- 1793693 -->
您可以在 [裝置] 刀鋒視窗上同時刪除多個裝置。 選擇 [裝置] > [所有裝置] > 選取您要刪除的裝置 > [刪除]。 針對無法刪除的裝置，將會顯示警示。

### <a name="new-wi-fi-device-configuration-profile-for-windows-10-and-later----1879077---"></a>Windows 10 和更新版本的新 Wi-Fi 裝置組態設定檔 <!-- 1879077 -->
您目前可以使用 XML 檔案來匯入和匯出 Wi-Fi 設定檔。 您將可以直接在 Intune 中建立 Wi-Fi 裝置組態設定檔，如同一些其他平台。

若要建立設定檔，請開啟 [裝置設定] > [設定檔] > [建立設定檔] > [Windows 10 和更新版本] > [Wi-Fi]。 

適用於 Windows 10 及更新版本。

###  <a name="windows-line-of-business-lob-apps-file-extension-rename----1884873---"></a>Windows 企業營運 (LOB) 應用程式副檔名重新命名 <!-- 1884873 -->
Windows LOB 應用程式副檔名將會從 *.appx* 和 *.appxbundle* 重新命名為 *.msix* 和 *.msixbundle*。 您可以依序選取 [Mobile Apps] > [應用程式] > [新增] 在 Microsoft Intune 中新增應用程式。 隨即顯示 [新增應用程式] 窗格，讓您可以選取 [應用程式類型]。 針對 Windows LOB 應用程式，選取 [企業營運] 應用程式作為應用程式類型，並選取 [應用程式套件檔案]，然後輸入具有適當副檔名的安裝檔。

### <a name="windows-defender-atp-configuration-package-automatically-added-to-configuration-profile----2144658---"></a>Windows Defender ATP 設定套件會自動新增至組態設定檔 <!-- 2144658 -->
在 Intune 中使用[進階威脅保護和上線](advanced-threat-protection.md#onboard-devices-using-a-configuration-profile)裝置時，您目前會下載設定套件，並將它新增至組態設定檔。 在未來更新中，Intune 會從 Windows Defender 資訊安全中心自動取得套件，並將它新增至設定檔。

適用於 Windows 10 及更新版本。

### <a name="kiosk---obsolete-is-grayed-out-and-cant-be-changed----2149998---"></a>Kiosk - 已淘汰變成灰色，而且無法變更 <!-- 2149998 -->
[Kiosk 功能](device-restrictions-windows-10.md#kiosk-preview---obsolete) ([裝置設定] > [設定檔] > [建立設定檔] > [Windows 10 和更新版本] > [裝置限制]) 將會淘汰，並取代為 [Windows 10 和更新版本的 Kiosk 設定](kiosk-settings.md). **Kiosk - 已淘汰**功能將會變成灰色，而且無法變更或更新使用者介面。 

若要啟用 Kiosk 模式，請參閱[適用於 Windows 10 和更新版本的 Kiosk 設定](kiosk-settings.md)。

適用於 Windows 10 和更新版本、Windows Holographic for Business

### <a name="apis-to-use-3rd-party-certification-authorities----2184013---"></a>使用協力廠商憑證授權單位的 API <!-- 2184013 -->
將會有 Java API 可讓協力廠商憑證授權單位與 Intune 和 SCEP 整合。 然後，使用者可將 SCEP 憑證新增至設定檔，並將它套用至使用 MDM 的裝置。

Intune 目前支援[使用 Active Directory 憑證服務的 SCEP 要求](certificates-scep-configure.md)。

### <a name="check-for-sccm-compliance----2192052---"></a>檢查 SCCM 相容性 <!-- 2192052 -->
未來更新將會包括新的 System Center Configuration Manager (SCCM) 相容性設定 ([裝置相容性] > [原則] > [建立原則] > [Windows 10])。 SCCM 將訊號傳送給 Intune 相容性。 使用 Intune 設定，您可能需要所有 SCCM 訊號傳回「相容」。

例如，您需要在裝置上安裝所有軟體更新。 在 SCCM 中，此需求會有「已安裝」狀態。 如果裝置上的任何程式處於未知狀態，則裝置在 Intune 中將會不相容。

適用於 Windows 10 和更新版本

### <a name="alerts-for-expiring-vpp-token-or-company-portal-license-running-low----2237572---"></a>VPP 權杖將過期或公司入口網站授權將不足的警示<!-- 2237572 -->
如果您在 DEP 註冊期間使用大量採購方案 (VPP) 預先佈建公司入口網站，則 Intune 會在 VPP 權杖即將過期以及公司入口網站授權即將不足時提醒您。

### <a name="confirmation-required-to-delete-vpp-token-that-is-being-used-for-company-portal-pre-provisioning----2237634---"></a>需要確認刪除將用於預先佈建公司入口網站的 VPP 權杖 <!-- 2237634 -->
如果在 DEP 註冊期間將使用大量採購方案 (VPP) 權杖來預先佈建公司入口網站，則需要確認刪除該權杖。

### <a name="automatically-mark-android-devices-enrolled-by-using-samsung-knox-mobile-enrollment-as-corporate----2404851---"></a>將使用 Samsung Knox Mobile Enrollment 所註冊的 Android 裝置自動標示為「公司」<!-- 2404851 -->
在 [Device Ownership] \(裝置擁有權\) 下，預設會將使用 Samsung Knox Mobile Enrollment 所註冊的 Android 裝置標示為 [公司]。 在使用 Knox Mobile Enrollment 註冊之前，您不需要手動找出使用 IMEI 或序號的公司裝置。

### <a name="toggle-to-show-or-not-show-the-end-session-button-on-a-kiosk-browser----2455253---"></a>切換在 Kiosk 瀏覽器上顯示或不顯示 [結束工作階段] 按鈕 <!-- 2455253 -->
您可以設定 Kiosk 瀏覽器是否顯示 [結束工作階段] 按鈕。 您可以在 [裝置設定] > [Kiosk (預覽)] > [Kiosk Web Browser] \(Kiosk 網頁瀏覽器\) 看到控制項。 如果開啟，則使用者按一下此按鈕時，應用程式會提示您確認結束工作階段。 確認時，瀏覽器會清除所有瀏覽資料，並巡覽回預設 URL。

### <a name="create-an-esim-cellular-configuration-profile----2564077---"></a>建立 eSIM 行動數據組態設定檔 <!-- 2564077 -->
在 [裝置設定] 中，您將可以建立 eSIM 行動數據設定檔。 您可以匯入檔案，其中包含您的行動電信業者所提供的行動數據啟用碼。 您接著可以將這些設定檔部署至啟用 eSIM LTE 的 Windows 10 裝置，例如 Surface Pro LTE 和其他具有 eSIM 功能的裝置。

確認您的[裝置支援 eSIM 設定檔](https://support.microsoft.com/help/4020763/windows-10-use-esim-for-cellular-data)與否。

適用於 Windows 10 及更新版本。 




<!-- 1806 start -->

### <a name="see-device-configuration-profiles-in-conflict----1556983---"></a>查看衝突的裝置組態設定檔 <!-- 1556983 -->
在 [裝置設定] 中，會顯示現有設定檔的清單。 使用此更新即會新增資料行，以提供衝突之設定檔的詳細資料。 您可以選取衝突的資料列，以查看設定以及發生衝突的設定檔。 

移至[裝置組態設定檔](device-profiles.md)。

### <a name="corporate-owned-single-use-cosu-support-for-android-devices----1630973---"></a>公司所擁有且適用於 Android 裝置的單次使用 (COSU) 支援 <!-- 1630973 -->

Intune 將支援高度受控、鎖定、Kiosk 樣式的 Android 裝置。 這可讓系統管理員將裝置的用途進一步鎖定為單一應用程式或一小組的應用程式，並可防止使用者在裝置上啟用其他應用程式或執行其他動作。

### <a name="macos-support-for-apple-device-enrollment-program----747651---"></a>macOS 支援 Apple 裝置註冊計劃 <!-- 747651 -->

Intune 支援將 macOS 裝置註冊到 Apple 裝置註冊計劃 (DEP) 中。 操作方法：

1. 在 deploy.apple.com 上，將 macOS 序號指派給 MDM 伺服器。
2. 將該序號匯入到 Intune 中。
3. 建立 macOS 裝置專用的註冊方案設定檔。

### <a name="google-name-changes-for-android-for-work-and-play-for-work---842873---"></a>Android for Work 和 Play for Work 的 Google 名稱變更 <!--842873 -->
Intune 將更新 "Android for Work" 術語以反映 Google 的商標變更。  不再使用 "Android for Work" 和 "Play for Work" 這些詞彙。 視內容而定，將會使用不同的術語：

- 「Android 企業」指的是整體的現代 Android 管理堆疊。
- 「工作設定檔」或「設定檔擁有者」指的是使用工作設定檔管理的 BYOD 裝置。
- 「受控 Google Play」則是指 Google 應用程式存放區。

### <a name="monitor-ios--app-configuration-status-per-device----880037-eeready-eestaged---"></a>監視每個裝置的 iOS 應用程式設定狀態 <!-- 880037 eeready eestaged -->

身為 Microsoft Intune 系統管理員，您可以監視每個受控裝置的 iOS 應用程式設定狀態。 從 Azure 入口網站的 [Microsoft Intune] 中，選取 [裝置] > [所有裝置]。 從受控裝置清單中，選取特定的裝置以顯示裝置的刀鋒視窗。 在裝置的刀鋒視窗中，選取 [應用程式設定]。  

### <a name="3rd-party-keyboards-can-be-blocked-by-app-settings-on-ios----1248481---"></a>iOS 上的應用程式設定可封鎖第三方鍵盤 <!-- 1248481 -->
在 iOS 裝置上，Intune 系統管理員可以在存取原則保護應用程式中的組織資料時，封鎖第三方鍵盤的使用。 當應用程式保護原則 (APP) 設定為封鎖第三方鍵盤時，裝置使用者會在第一次使用第三方鍵盤與公司資料互動時收到一則訊息。 本機鍵盤以外的所有選項都會被封鎖，裝置使用者不會看到它們。 裝置使用者只會看到對話方塊訊息一次。 

### <a name="create-device-compliance-policy-using-firewall-settings-on-macos-devices----1497640---"></a>在 macOS 裝置上使用防火牆設定建立裝置合規性原則 <!-- 1497640 -->
當您建立新的 macOS 合規性原則 ([裝置合規性] > [原則] > [建立原則] >  [平台：macOS] > [系統安全性]) 時，會有一些可用的新 [防火牆] 設定： 
- **防火牆**：設定您環境中處理連入連線的方式。
- **連入連線**：除了基本網際網路服務所需的連線 (例如 DHCP、Bonjour 及 IPSec) 之外，[封鎖] 所有連入連線。 這項設定也會封鎖所有的共用服務。
- **隱形模式**：[啟用] 隱形模式以防止電腦回應探查要求。 電腦會繼續回應已授權應用程式的連入要求。

適用對象：macOS 10.12 和更新版本

### <a name="use-samaccountname-as-the-account-username-for-email-profiles----1500307---"></a>使用 sAMAccountName 作為電子郵件設定檔的帳戶使用者名稱 <!-- 1500307 -->

您可以使用內部部署 **sAMAccountName**，作為 Android、iOS 和 Windows 10 電子郵件設定檔的帳戶使用者名稱。 也可以從Azure Active Directory (Azure AD) 中的 `domain` 或 `ntdomain` 屬性取得網域。 或者，輸入自訂靜態網域。

若要使用這項功能，您必須將來自內部部署 Active Directory 環境的 `sAMAccountName` 屬性同步至 Azure AD。

適用對象：Android、iOS、Windows 10 和更新版本

### <a name="require-non-biometric-passcode-on-app-launch-and-timeout----1506985---"></a>在應用程式啟動和逾時時需要非生物特徵辨識密碼 <!-- 1506985 -->

透過在應用程式啟動時和系統管理員指定的逾時之後要求非生物特徵辨識密碼，Intune 可藉由限制使用生物識別存取公司資料，為啟用行動應用程式管理 (MAM) 的應用程式增強安全性。 這些設定會影響依賴 Touch ID (iOS)、Face ID (iOS)、 Android 生物特徵辨識或其他未來的生物特徵辨識驗證方法來存取其啟用 APP/MAM 之應用程式的使用者。 這些設定可讓 Intune 系統管理員能夠更細微地控制使用者存取，並排除具有多個指紋或其他生物特徵辨識存取方法的裝置可能會向不正確的使用者顯示公司資料的情況。 在 Azure 入口網站中，開啟 [Microsoft Intune]。 選取 [行動裝置應用程式] > [應用程式保護原則] > [新增原則] > [設定]。 找出特定設定的 [存取] 區段。

### <a name="selective-wipe-of-organizations-app-data----1507030---"></a>選擇性抹除組織的應用程式資料 <!-- 1507030 -->
不符合應用程式保護原則 (APP) 存取設定的條件時，系統管理員可以設定選擇性抹除組識資料作為新的動作。  這項功能可協助系統管理員依據預先設定的準則，自動保護並移除應用程式中的機密組織資料。

### <a name="revoking-an-ios-app-purchased-through-vpp----1777384---"></a>撤銷透過 VPP 購買的 iOS 應用程式 <!-- 1777384 -->
身為 Microsoft Intune 系統管理員，您可以撤銷透過大量採購方案 (VPP) 購買的所選 iOS 應用程式授權。 當應用程式不再指派給使用者時，您可以通知他們。 撤銷應用程式授權將不會從該裝置解除安裝相關聯的 VPP 應用程式。 若要解除安裝 VPP 應用程式，您必須將指派動作變更為 [解除安裝]。 回收的授權計數將會反映在 Intune 之 [應用程式] 工作負載中的 [授權的應用程式] 節點。 如需與 iOS VPP 應用程式相關的詳細資訊，請參閱[如何使用 Microsoft Intune 管理透過大量採購方案購買的 iOS 應用程式](vpp-apps-ios.md)。

### <a name="office-365-pro-plus-language-packs----1833450---"></a>Office 365 Pro Plus 語言套件 <!-- 1833450 -->
身為 Intune 系統管理員，您可以為透過 Intune 管理的 Office 365 Pro Plus 應用程式部署其他語言。 可用的語言清單包括語言套件的**類型** (核心、部分和校訂)。 在 Azure 入口網站中，選取 [Microsoft Intune] > [行動裝置應用程式] > [應用程式] > [新增]。 在 [新增應用程式] 刀鋒視窗的 [應用程式類型] 清單中，選取 [Office 365 套件] 下的 [Windows 10]。 選取 [應用程式套件設定] 刀鋒視窗中的 [語言]。

### <a name="revoke-ios-vpp-app-license----1863797---"></a>撤銷 iOS VPP 應用程式授權 <!-- 1863797 -->
身為系統管理員，您可以回收指派給使用者或裝置的 iOS VPP 應用程式授權。 解除安裝 iOS VPP 應用程式也可讓您回收應用程式授權。 然後，您可以選擇將應用程式授權指派給其他使用者或裝置。 如需 iOS VPP 應用程式授權的詳細資訊，請參閱[在 Microsoft Intune 中管理 iOS 大量採購的應用程式](vpp-apps-ios.md)。

### <a name="preview-a-new-user-experience-update-for-the-company-portal-website---2000968---"></a>預覽公司入口網站的新使用者體驗更新 <!--2000968 -->
我們正在依據客戶的意見反應，將新功能新增至公司入口網站/iOS 應用程式目錄。 您可在 Android、iOS 和 Windows 裝置上體驗現有功能和可用性方面的重大改善。 網站的各個區域 (例如裝置詳細資料、意見反應和支援，以及裝置概觀) 將獲得全新的現代化回應式設計。 此外還包括：

- 簡化所有裝置平台中的工作流程
- 改善裝置識別和註冊流程
- 更有用的錯誤訊息
- 更容易使用的語言，較少的技術專業術語
- 可以共用應用程式的直接連結
- 改善大型應用程式目錄的效能
- 增加所有使用者的協助工具

更新目前為預覽狀態。 您可以在 http://aka.ms/webcpflighting 註冊加入預覽

### <a name="updates-to-out-of-compliance-messages-in-company-portal-app----1832222---"></a>公司入口網站應用程式中不相容訊息的更新 <!-- 1832222 -->
我們將修訂裝置使用者在裝置不相容時看到的訊息。 訊息將保留其原始意義，但會使用易用語言和較少技術行話來更新。 我們也將重新整理文件和補救步驟的連結，來保持它們的最新資訊。  

下列前後文字是您將看到之傳訊中的一個改善範例：  

前：此裝置未在 IT 管理員所要求的指定時段中連線 Intune 服務。若要解決此問題，請在您的裝置上開啟公司入口網站應用程式，然後按一下 [檢查相容性] 按鈕。  

後：您的裝置未簽入組織一段時間。若要重新建立連線，請在您的裝置上開啟公司入口網站應用程式，然後點選您裝置的 [檢查設定]。  

### <a name="edit-your-office-365-pro-plus-app-deployments----2150145---"></a>編輯 Office 365 Pro Plus 應用程式部署 <!-- 2150145 -->
身為 Microsoft Intune 系統管理員，您可以更有效率地編輯 Office 365 Pro Plus 應用程式部署。 在 Azure 入口網站中，選取 [Microsoft Intune] > [行動裝置應用程式] > [應用程式]。 從應用程式的清單中，選取您的 Office 365 Pro Plus 套件。  

### <a name="per-row-review-of-duplicate-corporate-device-identifiers-uploaded----2203794---"></a>已上傳之重複公司裝置識別碼的每一資料列檢閱 <!-- 2203794 -->
上傳公司識別碼時，Intune 將提供任何重複項目的清單，並可讓您選擇取代或保留現有資訊。 選擇 [裝置註冊] > [公司裝置識別碼] > [新增識別碼] 之後，如果有重複項目，則會出現報表。 

### <a name="manually-add-corporate-device-identifiers----2203803---"></a>手動新增公司裝置識別碼 <!-- 2203803 -->
您可以手動新增公司裝置識別碼。 請選擇 [裝置註冊] > [公司裝置識別碼] > [新增]。

### <a name="new-status-for-devices-in-device-compliance----2308882---"></a>裝置相容性中裝置的新狀態 <!-- 2308882 -->
在 [裝置相容性] > [原則] > 選取原則 > [概觀] 中，將會新增下列新狀態：
- 成功
- 錯誤
- 衝突
- 擱置
- 不適用

同時顯示可顯示不同平台裝置計數的影像。 例如，如果您要查看 iOS 設定檔，新的磚會顯示同時指派給此設定檔的非 iOS 裝置計數。 

### <a name="device-compliance-supports-3rd-party-anti-virus-solutions----2325484---"></a>裝置合規性支援協力廠商防毒解決方案 <!-- 2325484 -->
當您建立裝置合規性原則 ([裝置合規性] > [原則] > [建立原則] >  [平台：Windows 10 和更新版本] > [設定] > [系統安全性]) 時，會有一些新的 [裝置安全性] 選項： 
- **防毒**：當設定為 [必要] 時，您可以使用向 Windows 資訊安全中心註冊的防毒解決方案 (例如 Symantec) 來檢查合規性。 
- **反間諜功能**：當設定為 [必要] 時，您可以使用向 Windows 資訊安全中心註冊的反間諜功能解決方案 (例如 Symantec) 來檢查合規性。 

適用對象：Windows 10 和更新版本 

<!-- 1805 start -->

### <a name="improved-troubleshooting-for-app-installation----928990---"></a>改善的應用程式安裝疑難排解 <!-- 928990 -->
在受 Microsoft Intune MDM 管理的裝置上，應用程式安裝有時可能會失敗。 當這些應用程式安裝失敗時，使用者可能無法輕易地了解失敗的原因，或是對問題進行疑難排解。 我們正在推出應用程式疑難排解功能的公開預覽。 您將會在每個個別裝置的底下看到名為 [受控應用程式] 的新節點。 這會列出透過 Intune MDM 傳遞的應用程式。 在該節點中，您將會看到應用程式安裝狀態的清單。 如果您選取個別的應用程式，將會看到針對該特定應用程式的疑難排解檢視。 在疑難排解檢視中，您將會看到應用程式的端對端生命週期，例如針對該應用程式進行建立、修改、設為目標，以及傳遞至裝置的時間。 此外，如果應用程式安裝沒有成功，系統將會針對導致該錯誤的原因為您顯示錯誤碼及協助訊息。

### <a name="require-non-biometric-passcode-on-cold-app-launch-and-timeout----1506985---"></a>在應用程式冷啟動和逾時時需要非生物特徵辨識密碼 <!-- 1506985 --> 

透過在應用程式冷啟動時和系統管理員指定的逾時之後要求非生物特徵辨識密碼，Intune 可藉由限制使用生物識別存取公司資料，為啟用行動應用程式管理 (MAM) 的應用程式增強安全性。 這些設定會影響依賴 Touch ID (iOS)、Face ID (iOS)、 Android 生物特徵辨識或其他未來的生物特徵辨識驗證方法來存取其啟用 APP/MAM 之應用程式的使用者。 這些設定可讓 Intune 系統管理員能夠更細微地控制使用者存取，並排除具有多個指紋或其他生物特徵辨識存取方法的裝置可能會向不正確的使用者顯示公司資料的情況。 在 Azure 入口網站中，開啟 [Microsoft Intune]。 選取 [行動裝置應用程式] > [應用程式保護原則] > [新增原則] > [設定]。 找出特定設定的 [存取] 區段。

### <a name="block-app-access-based-on-unapproved-device-vendors-and-models-----1425689----"></a>依據未經核准的裝置廠商和型號來封鎖應用程式存取 <!-- 1425689 ! -->
Intune IT 系統管理員將能透過 Intune 應用程式防護原則，強制執行 Android 製造商和/或 iOS 型號的指定清單。 IT 系統管理員可以提供以分號分隔的製造商清單 (適用於 Android 原則) 及裝置型號清單 (適用於 iOS 原則)。 Intune 應用程式防護原則僅適用於 Android 和 iOS。 針對此指定清單，將可以執行兩個個別的動作：
- 針對未指定的裝置，封鎖其存取應用程式的能力。
- 或是針對未指定的裝置，選擇性地抹除該裝置上的公司資料。 

若沒有符合原則需求，使用者將無法存取目標應用程式。 根據設定的不同，系統可能會封鎖該使用者，或選擇性地抹除其位於應用程式內的公司資料。 在 iOS 裝置上，此功能需要應用程式的參與 (亦即， WXP、Outlook、Managed Browser、Yammer) 來整合 Intune APP SDK，以針對目標應用程式強制執行最小版本設定。 此整合會以輪流的方式發生，並取決於特定的應用程式小組。 在 Android 上，此功能需要有最新版的公司入口網站。 

在使用者裝置上，Intune 用戶端將會根據應用程式防護原則 Intune 刀鋒視窗中所指定字串來進行簡單比對，藉以採取動作。 這會完全取決於裝置報告的值。 因此，我們會建議 IT 系統管理員確定預期的行為是正確無誤的。 這可透過針對小型的使用者群組，在各種不同的裝置製造商和型號上測試此設定來達成。 在 Microsoft Intune 中，選取 [行動應用程式] > [應用程式防護原則] 來檢視及新增應用程式防護原則。 如需應用程式防護原則的詳細資訊，請參閱[什麼是應用程式防護原則](app-protection-policy.md)。

### <a name="access-actions-for-app-protection-policies----1483510-eeready---"></a>存取適用於應用程式防護原則的動作 <!-- 1483510 EEready -->
您很快便能設定應用程式防護原則，以明確地針對不符合規範的裝置進行抹除、封鎖或警告。 最新的動作「抹除」能從裝置移除您公司的資料。 如果發生抹除，系統會向裝置使用者告知抹除的原因及補救的步驟。 針對某些設定 (例如最小 OS 版本)，您將能套用多個動作 (例如封鎖和抹除)。 當應用程式啟動時，便會觸發這些動作。

<!-- 1804 start -->

### <a name="rules-for-removing-devices----1609459---"></a>用於移除裝置的規則 <!-- 1609459 -->
將會提供新規則，可讓您自動移除在所設定天數內未簽入的裝置。 若要查看新規則，請移至 [Intune] 窗格，選取 [裝置]，然後選取 [裝置移除規則]。

<!-- 1803 start -->

### <a name="ability-to-deploy-required-line-of-business-lob-apps-to-all-users-on-windows-10-desktop-devices----1627835-rs4---"></a>在 Windows 10 Desktop 裝置上，將所需之企業營運 (LOB) 應用程式部署給所有使用者的能力 <!-- 1627835 RS4 -->
客戶將能夠部署必要的企業營運 Windows 10 應用程式，以安裝在裝置內容中。 這會向裝置上的所有使用者開放使用這些應用程式。 這僅適用於 Windows 10 Desktop 裝置。

### <a name="updating-the-help-and-feedback-experience-on-company-portal-app-for-android---1631531---"></a>更新 Android 的公司入口網站應用程式之說明與意見反應體驗 <!--1631531 -->

Android 公司入口網站應用程式的說明和意見反應體驗將更新，以與 Android 應用程式的最佳做法保持一致。 Android 公司入口網站應用程式將於接下來幾個月內更新，以將 [說明與意見反應] 功能表項目劃分為分開的 [說明] 與 [傳送意見反應] 功能表項目。 **說明**頁面將有**常見問題集**章節和**電子郵件支援** 按鈕，引導使用者上傳記錄給 Microsoft，並將電子郵件傳送給描述問題的公司支援。 **傳送意見反應**會透過標準 Microsoft 意見反應提交來引導使用者，並會提示使用者選擇「我喜歡某些項目」、「我不喜歡某些項目 」，或是「我有個想法」。

<!-- the following are present prior to 1801 -->

### <a name="app-protection-policies-----679615---"></a>應用程式防護原則 <!-- 679615 -->
Intune 應用程式防護原則能提供建立全域預設原則的能力，以針對整個租用戶中的所有使用者快速啟用保護。

<!-- the following are present prior to 1711 -->

## <a name="notices"></a>通知

目前沒有任何作用中的通知。

### <a name="see-also"></a>另請參閱
如需近期發展的詳細資料，請參閱 [Microsoft Intune 的新功能](whats-new.md)。
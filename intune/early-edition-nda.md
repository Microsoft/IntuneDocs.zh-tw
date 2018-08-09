---
title: 舊版
description: ''
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/06/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: ab6c808fc860491ddece5751983071d40864c8dd
ms.sourcegitcommit: 8f68cd3112a71d1cd386da6ecdae3cb014d570f2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/06/2018
ms.locfileid: "39575078"
---
# <a name="the-early-edition-for-microsoft-intune---august-2018"></a>Microsoft Intune 的舊版 - 2018 年 8 月

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

<!-- 1808 start -->

### <a name="windows-hello-will-target-users-and-devices----1106609---"></a>Windows Hello 是以使用者和裝置為目標 <!-- 1106609 -->
當您建立 [Windows Hello 企業版](windows-hello.md)原則時，該原則會套用至組織 (整個租用戶) 內的所有使用者。 使用此更新，也可以使用裝置設定原則將該原則套用至特定使用者或特定裝置 ([裝置設定] > [設定檔] > [建立設定檔] > [Identity Protection] > [Windows Hello 企業版])。

在 Azure 入口網站的 Intune 中，Windows Hello 設定將會存在於 [裝置註冊] 和 [裝置設定] 中。 [裝置註冊] 以整個組織 (整個租用戶) 為目標，並支援 Windows AutoPilot (OOBE)。 [裝置設定] 以使用在簽入期間所套用原則的裝置和使用者為目標。

適用於：  
- Windows 10 及更新版本
- Windows Holographic for Business

### <a name="control-s-mode-on-windows-10-and-later-devices---public-preview----1958649---"></a>Windows 10 及更新版本之裝置上的控制 S 模式 - 公開預覽 <!-- 1958649 -->
您可以建立裝置設定檔以將 Windows 10 裝置切換出 S 模式，或防止使用者將裝置切換出 S 模式。 此功能將位於 Intune > [裝置設定] > [設定檔] >  [Windows 10 and later] \(Windows 10 及更新版本\) > [Edition upgrade and mode switch] \(版本升級和模式切換\) 中。
[引進 Windows 10 S 模式](https://www.microsoft.com/windows/s-mode)提供 S 模式的詳細資訊。
適用於：Windows 10 及更新版本 (1809 及更新版本)

### <a name="modern-vpn-support-updates-for-ios----2459928-1819876-and-2650856---"></a>iOS 的新式 VPN 支援更新 <!-- 2459928, 1819876, and 2650856 -->
未來的更新將會支援下列 iOS VPN 用戶端： 
- F5 Access (3.0.1 版和更高版本)
- Citrix SSO
- Palo Alto Networks GlobalProtect (5.0 版和更高版本) 也在未來的更新中：
- 現有的 **F5 Access** 連線類型將會重新命名為 **F5 Access Legacy** (根據 F5 商標更新)
- 現有的 **Palo Alto Networks GlobalProtect** 連線類型將會重新命名為 **Legacy Palo Alto Networks GlobalProtect** (根據 Palo Alto 商標更新)。 

具有這些連線類型的現有設定檔會持續使用舊版 VPN 用戶端。 如果您搭配使用 Cisco Legacy AnyConnect、F5 Access Legacy、Citrix VPN 或 Legacy Palo Alto Networks GlobalProtect 與 iOS，則應該移至新的應用程式。 請盡快這麼做，確保 iOS 裝置在更新為 iOS 12 時可以提供 VPN 存取。

### <a name="lock-the-company-portal-in-single-app-mode-until-user-sign-in---1067692---"></a>除非使用者登入，否則會以單一應用程式模式鎖定公司入口網站 <!--1067692 --> 
如果您在 DEP 註冊期間透過公司入口網站驗證使用者，而非設定助理，則可以選擇以單一應用程式模式執行公司入口網站。 此選項會在設定助理完成之後立即鎖定裝置，讓使用者必須登入才能存取裝置。 此程序可確保裝置完成上架，而且在處於沒有任何使用者繫結的狀態下未遭到遺棄。

### <a name="scope-tags-for-policies---1081974-eeready--"></a>原則的範圍標籤 <!--1081974 eeready-->

您可以建立範圍標籤來限制對 Intune 資源的存取。 將範圍標籤新增至角色指派，然後將範圍標籤新增至設定檔。 此角色只能存取設定檔具有相符範圍標籤 (或無範圍標籤) 的資源。
若要建立範圍標籤，請選擇 [Intune roles] \(Intune 角色\) > [Scope (Tags)] \(範圍 (標籤)\) > [建立]。
若要將範圍標籤新增至角色指派，請選擇 [Intune roles] \(Intune 角色\) > [All roles] \(所有角色\) > [Policy and Profile Manager] \(原則和設定檔管理員\) > [作業] > [Scope (Tags)] \(範圍 (標籤)\)。
若要將範圍標籤新增至設定檔，請選擇 [裝置設定] > [設定檔] > 選擇設定檔 > [屬性] > [Scope (Tags)] \(範圍 (標籤)\)。

### <a name="assign-a-user-and-friendly-name-to-an-autopilot-device---1346521---"></a>將使用者和易記名稱指派給 AutoPilot 裝置 <!--1346521 -->
未來的公開預覽可讓系統管理員將使用者指派給單一 Autopilot 裝置。  系統管理員也可以提供易記名稱，以在使用 Autopilot 設定其裝置時歡迎使用者。

適用於：Windows Insider 1809 或更新版本的組建 (同時為預覽版本)。

### <a name="apple-vpp-token-used-by-another-mdm----1488946---"></a>另一個 MDM 所使用的 Apple VPP 權杖 <!-- 1488946 -->
如果 Intune 和另一個 MDM 都正在使用 Apple 大量採購方案 (VPP) 權杖，則 Intune 會偵測並顯示詳細資料。

### <a name="packet-tunnel-support-for-ios-per-app-vpn-profiles-for-custom-and-pulse-secure-connection-types----1520957---"></a>自訂和 Pulse Secure 連線類型之 iOS 個別應用程式 VPN 設定檔的封包通道支援 <!-- 1520957 -->
使用 iOS 個別應用程式 VPN 設定檔時，您可以使用應用程式層通道 (app-proxy) 或封包層通道 (packet-tunnel)。 下列連線類型可以使用這些選項：
- 自訂 VPN
- Pulse Secure：如果您不確定要使用的值，請參閱您 VPN 提供者的文件。
適用於：iOS

### <a name="zscaler-is-an-available-connection-for-vpn-profiles-on-ios----1769858-eeready---"></a>Zscaler 是 iOS 上 VPN 設定檔的可用連線 <!-- 1769858 eeready -->
當您建立 iOS VPN 裝置設定檔 ([裝置設定] > [設定檔] > [建立設定檔] > [iOS] 平台 > [VPN] 設定檔類型) 時，有數種連線類型 (包括 Cisco、Citrix 等等)。 未來的更新會將 Zscaler 新增為連線類型。 
[執行 iOS 之裝置的 VPN 設定](vpn-settings-ios.md)列出可用的連線類型。

### <a name="block-windows-personal-device-enrollments----1849498---"></a>封鎖 Windows 個人裝置註冊 <!-- 1849498 -->
您可以在 Intune 中封鎖 Windows 個人裝置註冊[行動裝置管理](windows-enroll.md)。 使用此功能無法封鎖使用 [Intune PC 代理程式](manage-windows-pcs-with-microsoft-intune.md)所註冊的裝置。
若要查看此功能，請選擇 [裝置註冊] > [裝置限制]。
開啟這項限制不會影響已註冊的裝置。
開啟限制之後，Intune 會檢查以確定每個新的 Windows 註冊要求都已獲授權為公司註冊。 下列方法限定成授權為公司註冊：
- 註冊使用者會使用[裝置註冊管理員帳戶]( device-enrollment-manager-enroll.md)。

- 裝置透過 [Windows AutoPilot](enrollment-autopilot.md) 註冊。
- 裝置的 IMEI 編號列在 [裝置註冊] > [[公司裝置識別碼]( corporate-identifiers-add.md)])。
- 裝置透過[大量佈建套件](windows-bulk-enroll.md)註冊。
- 裝置透過[從 SCCM 自動註冊以共同管理](https://docs.microsoft.com/sccm/core/clients/manage/co-management-overview#how-to-configure-co-management)註冊。
將會封鎖未經授權的註冊。
Intune 將下列註冊標示為公司，但因為它們未將每個裝置控制提供給 Intune 系統管理員，因此將會予以封鎖：
- [自動 MDM 註冊](windows-enroll.md#enable-windows-10-automatic-enrollment)，透過[在 Windows 安裝期間的 Azure Active Directory 加入](https://docs.microsoft.com/azure/active-directory/device-management-azuread-joined-devices-frx.md)。
- [自動 MDM 註冊](windows-enroll.md#enable-windows-10-automatic-enrollment)，透過[從 Windows 安裝期間的 Azure Active Directory 加入](https://docs.microsoft.com/azure/active-directory/device-management-azuread-joined-devices-frx.md)。
也會封鎖下列個人註冊方法：
- [自動 MDM 註冊](windows-enroll.md#enable-windows-10-automatic-enrollment)，透過[從 Windows 設定新增公司帳戶](https://docs.microsoft.com/azure/active-directory/user-help/device-management-azuread-registered-devices-windows10-setup)。

- [僅限 MDM 註冊]( https://docs.microsoft.com/windows/client-management/mdm/mdm-enrollment-of-windows-devices#connecting-personally-owned-devices-bring-your-own-device)選項，來自 Windows 設定。

### <a name="specify-machine-name-patterns-in-an-autopilot-profile---1849855--"></a>在 AutoPIlot 設定檔中指定電腦名稱模式 <!--1849855-->
您可以指定電腦名稱範本，以在 AutoPilot 註冊期間產生和設定[電腦名稱](https://docs.microsoft.com/windows/client-management/mdm/accounts-csp)。 您需要在 AutoPilot 設定檔中指定此項目，而此檔案位於 [裝置註冊] > [Windows 註冊] > [Windows Autopilot Deployment service] \(Windows Autopilot Deployment 服務\) > [設定檔]。 只能使用英數和連字號字元。
適用於：Windows Insider 1809 或更新版本的組建 (同時為預覽版本)。

### <a name="ios-version-number-and-build-number-are-shown----1892471---"></a>會顯示 iOS 版本號碼和組建編號 <!-- 1892471 -->
在 [裝置合規性] > [裝置合規性] 中，會顯示 iOS 作業系統版本。 在未來的更新中，也會顯示組建編號。
發行安全性更新時，Apple 通常會保留版本號碼，但更新組建編號。 顯示組建編號，即可輕鬆地檢查是否已安裝弱點更新。

### <a name="for-windows-autopilot-profiles-hide-the-change-account-options-on-the-company-sign-in-page-and-domain-error-page---1901669---"></a>針對 Windows AutoPilot 設定檔，隱藏公司登入頁面和網域錯誤頁面上的變更帳戶選項 <!--1901669 -->
公開預覽會包含新的 Windows AutoPilot 設定檔選項，讓系統管理員隱藏公司登入和網域錯誤頁面上的變更帳戶選項。 隱藏這些選項需要在 Azure Active Directory 中設定公司商標。 適用於：Windows Insider 1809 或更新版本的組建 (同時為預覽版本)。

### <a name="delay-when-ios-software-updates-are-shown-on-the-device----1949583---"></a>在裝置上顯示 iOS 軟體更新時延遲 <!-- 1949583 -->
在 [Intune] > [軟體更新] > [Update policies for iOS] \(更新 iOS 的原則\) 中，您可以設定不想要裝置安裝任何更新的日期和時間。 在未來的更新中，您可以在裝置上以可見的方式顯示軟體更新時延遲 (從 1-90 天)。 
[在 Microsoft Intune 中設定 iOS 更新原則](software-updates-ios.md)會列出目前設定。

### <a name="retired-devices-in-the-device-compliance-dashboard----1981119---"></a>[裝置合規性] 儀表板中的已淘汰裝置 <!-- 1981119 -->
在未來的更新中，將會從 [裝置合規性] 儀表板中移除已淘汰裝置。 這會變更您的合規性數字。

### <a name="new-user-experience-update-for-the-company-portal-website---2000968---"></a>公司入口網站的新使用者體驗更新 <!--2000968 -->
將會根據客戶的意見反應，將新功能新增至公司入口網站。 您可在 Android、iOS 和 Windows 裝置上體驗現有功能和可用性方面的重大改善。 網站的各個區域 (例如裝置詳細資料、意見反應和支援，以及裝置概觀) 將獲得全新的現代化回應式設計。 此外還包括：
- 簡化所有裝置平台中的工作流程
- 改善裝置識別和註冊流程
- 更有用的錯誤訊息
- 更容易使用的語言，較少的技術專業術語
- 可以共用應用程式的直接連結
- 改善大型應用程式目錄的效能
- 增加所有使用者的協助工具

### <a name="office-365-proplus-version----2213968-eeready---"></a>Office 365 ProPlus 版本 <!-- 2213968 eeready -->
使用 Intune 將 Office 365 ProPlus 應用程式指派給 Windows 10 裝置時，您將可以選取 Office 版本。 在 Azure 入口網站中，選取 [Microsoft Intune] > [應用程式] > [新增應用程式]。 然後，從 [類型] 下拉式清單中選取 [Office 365 ProPlus Suite (Windows 10)]。 選取 [App Suite 設定] 以顯示相關聯的刀鋒視窗。 將 [更新通道] 設定為值 (例如 [每月])。 選擇性地選取 [是]，以從終端使用者裝置移除其他 Office (msi) 版本。 選取 [特定]，以在終端使用者裝置上安裝所選取通道的特定 Office 版本。 目前，您可以選取要使用之 Office 的 [特定版本]。 可用的版本將會隨著時間變更。 因此，建立新的部署時，可用的版本可能較新，因此沒有特定較舊版本可用。 目前部署將會繼續部署較舊的版本，但每個通道都會持續更新版本清單。 如需詳細資訊，請參閱 [Office 365 ProPlus 更新通道的概觀](https://docs.microsoft.com/DeployOffice/overview-of-update-channels-for-office-365-proplus)。

### <a name="configure-profile-to-skip-some-screens-during-setup-assistant----2276470---"></a>設定設定檔，以在設定助理期間略過一些畫面 <!-- 2276470 -->
當您建立 macOS 註冊設定檔時，可以將它設定成在使用者完成設定助理時略過下列任何畫面：
- Android 移轉
- 顯示色調
- 隱私權
- iCloudStorage

### <a name="change-in-the-update-process-for-on-premises-connectors----2277554---"></a>內部部署連接器之更新程序中的變更 <!-- 2277554 -->
根據客戶的意見反應，將會變更內部部署連接器更新方式。 在您初次安裝內部部署連接器之後，將會自動更新。 這項變更會從新的適用於 Microsoft Intune 的 PFX 憑證連接器開始，之後將推出至其他類型的內部部署連接器。 

### <a name="support-for-register-dns-setting-for-windows-10-vpn----2282852---"></a>Windows 10 VPN 的註冊 DNS 設定支援 <!-- 2282852 -->
您可以設定 Windows 10 VPN 設定檔，動態註冊指派給具有內部 DNS 之 VPN 介面的 IP 位址，而不需要使用自訂設定檔。
[Windows 10 VPN 設定](vpn-settings-windows-10.md)列出目前可用的 VPN 設定檔設定。 

### <a name="restricts-apps-and-block-access-to-company-resources-on-ios-and-android-for-work-devices----2451462---"></a>限制應用程式，並封鎖存取 iOS 和 Android for Work 裝置上的公司資源 <!-- 2451462 -->
在 [裝置合規性] > [原則] > [建立原則] > [Android for Work] > [系統安全性] 中，將會有新的 [Restricted applications] \(受限制的應用程式\) 設定。 如果在裝置上安裝特定應用程式，則這個新的設定會使用合規性原則來封鎖對公司資源的存取。 除非從裝置中移除受限制應用程式，否則會將裝置視為不符合規範。
適用於： 
- iOS

### <a name="export-azure-classic-portal-compliance-policies-to-csv-file----2469637---"></a>將 Azure 傳統入口網站合規性原則匯出為 .csv 檔案 <!-- 2469637 -->
將會取代在 Azure 傳統入口網站中建立的合規性原則。  發生這種情況時，您可以檢閱和刪除任何現有原則，但無法更新它們。 您可以將原則匯出為逗號分隔檔案 (.csv 檔案)。 然後，使用檔案中的詳細資料，在 Intune Azure 入口網站中中重新建立這些原則。
> [!IMPORTANT]
> 淘汰 Azure 傳統入口網站時，您就無法存取您的原則，包括看不到它們。 因此，請務必匯出它們，並先在 Azure 入口網站中重新建立它們，再淘汰 Azure 傳統入口網站。

<!-- 1807 start -->

### <a name="more-sync-opportunities-in-the-company-portal-app-for-windows----2683177---"></a>適用於 Windows 之公司入口網站應用程式中的更多同步處理機會 <!-- 2683177 -->
適用於 Windows 之公司入口網站應用程式正在向 Windows 工作列和開始功能表捷徑清單新增裝置同步處理動作。 按一下任一位置以快速同步處理您的裝置，並取得公司資源的存取權。  

### <a name="reset-device-passcodes-from-company-portal-app-for-windows-10----2101282---"></a>從 Windows 10 的公司入口網站應用程式重設裝置密碼 <!-- 2101282 --> 
您的員工很快可以直接從 Windows 10 的公司入口網站應用程式重設其裝置的 PIN 或密碼。 此功能將用於支援密碼重設的遠端及本機 Intune 受控裝置。 根據裝置類型，針對遠端裝置所提出的要求將會移除裝置的目前密碼，或建立暫時密碼。 要求重設本機裝置的使用者，將會重新導向至裝置的 [設定] 應用程式。  

### <a name="new-browsing-experiences-in-the-company-portal-app-for-windows----2317227---"></a>適用於 Windows 之公司入口網站應用程式的新瀏覽體驗 <!-- 2317227 -->  
在適用於 Windows 的公司入口網站應用程式中瀏覽或搜尋應用程式時，您能夠切換現有的**磚**檢視和新增的**詳細資料**檢視。 新的檢視會列出應用程式詳細資料，例如名稱、發佈者、發佈日期，以及安裝狀態。  

[應用程式] 頁面會引入**已安裝**檢視，其可讓您查看有關已完成和進行中之應用程式安裝的詳細資料。 想要分享有關新變更的意見反應或想法嗎？ 請在公司入口網站應用程式中將您的意見反應傳送給我們。

### <a name="improved-company-portal-app-experience-for-device-enrollment-manager-users----675800---"></a>已改善裝置註冊管理員使用者的公司入口網站應用程式體驗 <!-- 675800 -->
當裝置註冊管理員 (DEM) 登入適用於 Windows 的公司入口網站應用程式時，應用程式只會列出 DEM 目前執行中的裝置。 這項改善會減少之前應用程式在嘗試載入所有 DEM 註冊裝置時所發生的逾時。  

### <a name="use-vpp-device-licenses-to-pre-provision-the-company-portal-during-dep-enrollment----1608345---"></a>在 DEP 註冊期間，使用 VPP 裝置授權預先佈建公司入口網站 <!-- 1608345 -->
您將可以在裝置註冊計劃 (DEP) 註冊期間，使用大量採購方案 (VPP) 裝置授權預先佈建公司入口網站。 若要這麼做，當您建立或編輯註冊設定檔時，請指定您要用來安裝公司入口網站的 VPP 權杖。 請確定您的權杖未過期，而且您有足夠的公司入口網站應用程式權限。 如果權杖過期或授權不足，則 Intune會改為推送 App Store 公司入口網站 (這會提示您輸入 Apple 識別碼)。

###  <a name="windows-line-of-business-lob-apps-file-extensions----1884873---"></a>Windows 企業營運 (LOB) 應用程式副檔名 <!-- 1884873 -->
Windows LOB 應用程式的附檔名現在包含 *.msi*、*.appx*、*.appxbundle*、*.msix* 和 *.msixbundle*。 您可以依序選取 [Mobile Apps] > [應用程式] > [新增] 在 Microsoft Intune 中新增應用程式。 隨即顯示 [新增應用程式] 窗格，讓您可以選取 [應用程式類型]。 針對 Windows LOB 應用程式，選取 [企業營運] 應用程式作為應用程式類型，並選取 [應用程式套件檔案]，然後輸入具有適當副檔名的安裝檔。

### <a name="windows-defender-atp-configuration-package-automatically-added-to-configuration-profile----2144658---"></a>Windows Defender ATP 設定套件會自動新增至組態設定檔 <!-- 2144658 -->
在 Intune 中使用[進階威脅保護和上線](advanced-threat-protection.md#onboard-devices-using-a-configuration-profile)裝置時，您目前會下載設定套件，並將它新增至組態設定檔。 在未來更新中，Intune 會從 Windows Defender 資訊安全中心自動取得套件，並將它新增至設定檔。

適用於 Windows 10 及更新版本。

### <a name="check-for-sccm-compliance----2192052---"></a>檢查 SCCM 相容性 <!-- 2192052 -->
未來更新將會包括新的 System Center Configuration Manager (SCCM) 相容性設定 ([裝置相容性] > [原則] > [建立原則] > [Windows 10])。 SCCM 將訊號傳送給 Intune 相容性。 使用 Intune 設定，您可能需要所有 SCCM 訊號傳回「相容」。

例如，您需要在裝置上安裝所有軟體更新。 在 SCCM 中，此需求會有「已安裝」狀態。 如果裝置上的任何程式處於未知狀態，則裝置在 Intune 中將會不相容。

適用於 Windows 10 和更新版本

### <a name="alerts-for-expiring-vpp-token-or-company-portal-license-running-low----2237572---"></a>VPP 權杖將過期或公司入口網站授權將不足的警示<!-- 2237572 -->
如果您在 DEP 註冊期間使用大量採購方案 (VPP) 預先佈建公司入口網站，則 Intune 會在 VPP 權杖即將過期以及公司入口網站授權即將不足時提醒您。

### <a name="confirmation-required-to-delete-vpp-token-that-is-being-used-for-company-portal-pre-provisioning----2237634---"></a>需要確認刪除將用於預先佈建公司入口網站的 VPP 權杖 <!-- 2237634 -->
如果在 DEP 註冊期間將使用大量採購方案 (VPP) 權杖來預先佈建公司入口網站，則需要確認刪除該權杖。

#### <a name="additional-security-settings-for-windows-installer----2282430---"></a>Windows Installer 的其他安全性設定 <!-- 2282430 -->
您可以允許使用者控制應用程式安裝。 如啟用，則可讓以安全性違規方式停止的安裝繼續執行。 您可以指示 Windows Installer 在系統上安裝任何程式時使用提升的權限。 此外，您可以將 Windows 資訊保護 (WIP) 項目編入索引，並將跟其有關的中繼資料儲存在未加密的位置。 停用此原則時，不會編製 WIP 保護項目的索引，且不會出現在 Cortana 或檔案總管的結果中。 預設會停用這些選項的功能。 

<!-- 1806 start -->

### <a name="3rd-party-keyboards-can-be-blocked-by-app-settings-on-ios----1248481---"></a>iOS 上的應用程式設定可封鎖第三方鍵盤 <!-- 1248481 -->
在 iOS 裝置上，Intune 系統管理員可以在存取原則保護應用程式中的組織資料時，封鎖第三方鍵盤的使用。 當應用程式保護原則 (APP) 設定為封鎖第三方鍵盤時，裝置使用者會在第一次使用第三方鍵盤與公司資料互動時收到一則訊息。 本機鍵盤以外的所有選項都會被封鎖，裝置使用者不會看到它們。 裝置使用者只會看到對話方塊訊息一次。 

### <a name="require-non-biometric-passcode-on-app-launch-and-timeout----1506985---"></a>在應用程式啟動和逾時時需要非生物特徵辨識密碼 <!-- 1506985 -->

透過在應用程式啟動時和系統管理員指定的逾時之後要求非生物特徵辨識密碼，Intune 可藉由限制使用生物識別存取公司資料，為啟用行動應用程式管理 (MAM) 的應用程式增強安全性。 這些設定會影響依賴 Touch ID (iOS)、Face ID (iOS)、 Android 生物特徵辨識或其他未來的生物特徵辨識驗證方法來存取其啟用 APP/MAM 之應用程式的使用者。 這些設定可讓 Intune 系統管理員能夠更細微地控制使用者存取，並排除具有多個指紋或其他生物特徵辨識存取方法的裝置可能會向不正確的使用者顯示公司資料的情況。 在 Azure 入口網站中，開啟 [Microsoft Intune]。 選取 [行動裝置應用程式] > [應用程式保護原則] > [新增原則] > [設定]。 找出特定設定的 [存取] 區段。

### <a name="office-365-pro-plus-language-packs----1833450---"></a>Office 365 Pro Plus 語言套件 <!-- 1833450 -->
身為 Intune 系統管理員，您可以為透過 Intune 管理的 Office 365 Pro Plus 應用程式部署其他語言。 可用的語言清單包括語言套件的**類型** (核心、部分和校訂)。 在 Azure 入口網站中，選取 [Microsoft Intune] > [行動裝置應用程式] > [應用程式] > [新增]。 在 [新增應用程式] 刀鋒視窗的 [應用程式類型] 清單中，選取 [Office 365 套件] 下的 [Windows 10]。 選取 [應用程式套件設定] 刀鋒視窗中的 [語言]。

### <a name="preview-a-new-user-experience-update-for-the-company-portal-website---2000968---"></a>預覽公司入口網站的新使用者體驗更新 <!--2000968 -->
我們正在依據客戶的意見反應，將新功能新增至公司入口網站/iOS 應用程式目錄。 您可在 Android、iOS 和 Windows 裝置上體驗現有功能和可用性方面的重大改善。 網站的各個區域 (例如裝置詳細資料、意見反應和支援，以及裝置概觀) 將獲得全新的現代化回應式設計。 此外還包括：

- 簡化所有裝置平台中的工作流程
- 改善裝置識別和註冊流程
- 更有用的錯誤訊息
- 更容易使用的語言，較少的技術專業術語
- 可以共用應用程式的直接連結
- 改善大型應用程式目錄的效能
- 增加所有使用者的協助工具

更新目前為預覽狀態。 您可在 http://aka.ms/webcpflighting 註冊加入預覽

<!-- 1805 start -->

### <a name="require-non-biometric-passcode-on-cold-app-launch-and-timeout----1506985---"></a>在應用程式冷啟動和逾時時需要非生物特徵辨識密碼 <!-- 1506985 --> 

透過在應用程式冷啟動時和系統管理員指定的逾時之後要求非生物特徵辨識密碼，Intune 可藉由限制使用生物識別存取公司資料，為啟用行動應用程式管理 (MAM) 的應用程式增強安全性。 這些設定會影響依賴 Touch ID (iOS)、Face ID (iOS)、 Android 生物特徵辨識或其他未來的生物特徵辨識驗證方法來存取其啟用 APP/MAM 之應用程式的使用者。 這些設定可讓 Intune 系統管理員能夠更細微地控制使用者存取，並排除具有多個指紋或其他生物特徵辨識存取方法的裝置可能會向不正確的使用者顯示公司資料的情況。 在 Azure 入口網站中，開啟 [Microsoft Intune]。 選取 [行動裝置應用程式] > [應用程式保護原則] > [新增原則] > [設定]。 找出特定設定的 [存取] 區段。

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




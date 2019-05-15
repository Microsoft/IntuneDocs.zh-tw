---
title: 開發中 - Microsoft Intune
titleSuffix: ''
description: 正在開發的 Microsoft Intune 功能
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/15/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: aa38a684a32756d4f2c3be3b750f8e79b66e98f6
ms.sourcegitcommit: 8c795b041cd39e3896595f64f53ace48be0ec84c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2019
ms.locfileid: "59587377"
---
# <a name="in-development-for-microsoft-intune---april-2019"></a>Microsoft Intune 正在開發的項目 - 2019 年 4 月

為了協助您整備及規劃，此頁面會列出正在開發，但尚未發行的 Intune UI 更新及功能。 此外：

- 若我們預期您將需要在變更前先行採取動作，我們會發佈輔助性的 Office 訊息中心貼文。
- 當功能在生產環境中啟動時，無論是作為預覽功能還是正式推出，功能描述都會從此頁面移除，並移到 [[新增功能]](whats-new.md) 頁面。
- 此頁面和 [[新增功能]](whats-new.md) 頁面會定期更新。 請回來查看其他更新。
- 請參閱 [M365 藍圖](https://www.microsoft.com/microsoft-365/roadmap?rtc=2&filters=EMS)以取得策略性的交付時間表。

> [!Note]
> 這些項目會反映 Microsoft 目前針對未來版本中 Intune 功能的預期。 日期和個別的功能可能會產生變更。 並非所有正在開發的項目在此頁面上都具有功能描述。

**RSS 摘要**：將下列 URL 複製並貼上至您的摘要讀取器中，以在本頁更新時收到通知：`https://docs.microsoft.com/api/search/rss?search=%22in+development+-+microsoft+intune%22&locale=en-us`

<!--
## What's coming to Intune in the Azure portal 
## What's coming to Intune apps
## Notices
-->
 
## <a name="intune-in-the-azure-portal"></a>Azure 入口網站中的 Intune

<!-- 1904 start-->

### <a name="set-login-settings-and-control-restart-options-on-macos-devices----1210083---"></a>在 macOS 裝置上設定登入設定及控制重新啟動選項 <!-- 1210083 -->
在 iOS 裝置上，您可以建立裝置組態設定檔 ([裝置設定] > [設定檔] > [建立設定檔] > 選擇 [macOS] 平台 > [裝置功能] 設定檔類型)。 新的登入視窗設定會包含例如顯示自訂橫幅、選擇使用者登入方式、顯示或隱藏電源設定等項目。

若要查看目前的設定，請前往 [macOS 功能設定](macos-device-features-settings.md)。

適用於：macOS

### <a name="advanced-settings-for-windows-defender-firewall----1311949---"></a>Windows Defender 防火牆的進階設定 <!-- 1311949 -->
您很快地將可以使用 Intune 來為 Windows Defender 管理用戶端上的自訂防火牆規則。 規則可指定應用程式、網路位址和連接埠的輸入及輸出行為。 

### <a name="require-app-protection-conditional-access----1634317---"></a>需要應用程式防護條件式存取  <!--1634317 -->
您將能夠使用 [要求應用程式防護原則]，確認已將原則套用至使用者的應用程式後，登入才能順利完成，藉此防止使用者存取您使用條件式存取保護的資料。 雖然原則保證可能會使初次使用體驗的速度降低，它能協助避免發生網路問題、管理設定錯誤，或是阻撓應用程式防護原則的意圖。 

### <a name="retire-noncompliant-devices----1827291---"></a>淘汰不符合規範的裝置 <!-- 1827291 -->
我們將會新增新的相容性動作，淘汰不相容的裝置。 淘汰不相容的裝置會從移除所有公司資料，同時將裝置從由 Intune 管理的裝置中移除。 此動作會在設定的值 (天數) 到達時執行。 最小值為 30 天。 

### <a name="configure-settings-for-kernel-extensions-on-macos-devices----2043024---"></a>在 macOS 裝置上設定核心延伸模組的設定 <!-- 2043024 -->
在 macOS 裝置上，您可以建立裝置組態設定檔 ([裝置設定] > [設定檔] > [建立設定檔] > 針對平台選擇 [macOS])。 新的設定群組可讓您在裝置上設定及使用核心延伸模組。

適用於：macOS 10.13.2 和更新版本

### <a name="configure-profile-to-skip-some-screens-during-setup-assistant----2276470---"></a>設定設定檔，以在設定助理期間略過一些畫面 <!-- 2276470 -->
當您建立 macOS 註冊設定檔時，可以將它設定成在使用者完成設定助理時略過下列任何畫面：
- Android 移轉
- 顯示色調
- 隱私權
- iCloudStorage，如果您建立新的設定檔或編輯設定檔，則所選略過畫面需要與 Apple MDM 伺服器同步處理。 使用者可以發出裝置的手動同步處理，這樣在取得設定檔變更時才不會有延遲。
如需詳細資訊，請參閱[使用裝置註冊計劃或 Apple School Manager 自動註冊 macOS 裝置](device-enrollment-program-enroll-macos.md)。

### <a name="device-users-can-view-all-managed-apps-theyve-installed-or-tried-to-install----2352913---"></a>裝置使用者可檢視其安裝或嘗試安裝的所有受控應用程式 <!-- 2352913 -->
Windows 的公司入口網站會列出在使用者裝置上所安裝所有受控應用程式，包括必要及可用的應用程式。 使用者將能夠檢視嘗試及正在擱置的應用程式安裝，以及其目前的狀態。 若您的組織沒有將應用程式設為必要或可用，使用者會看見一個訊息，說明沒有安裝任何公司應用程式。 使用者也將能夠根據安裝狀態排序或篩選其應用程式。

### <a name="scope-tags-for-apple-vpp-tokens---2371886---"></a>Apple VPP 權杖的範圍標籤 <!--2371886 -->
您將能把範圍標籤新增到 Apple VPP 權杖。 只有獲派相同範圍標籤的使用者，才能存取具有該標籤的 Apple VPP 權杖。 使用該權杖購買的 VPP 應用程式和電子書會繼承其範圍標籤。 如需範圍標籤的詳細資訊，請參閱[使用 RBAC 和範圍標籤](scope-tags.md)。

### <a name="use-applicability-rules-when-creating-windows-10-device-configuration-profiles----2549910---"></a>在建立 Windows 10 裝置組態設定檔時使用「適用性規則」 <!-- 2549910 -->
您可以建立 Windows 10 裝置組態設定檔 ([裝置設定] > [設定檔] > [建立設定檔] > 針對平台選取 [Windows 10])。 您將能夠建立**適用性規則**，讓設定檔只套用到特定版本。 例如，您可以建立設定檔來啟用某些 BitLocker 設定。 一旦您新增設定檔後，您便可以使用適用性規則，將設定檔設為只套用到執行 Windows 10 企業版的裝置。

適用於： 
- Windows 10 及更新版本

### <a name="enable-win32-app-dependencies----2617348---"></a>啟用 Win32 應用程式相依性 <!-- 2617348 -->
公開預覽 - 身為管理員，您將能夠要求先將其他應用程式作為相依性安裝，才能安裝您的 Win32 應用程式。 具體來說，裝置必須安裝相依的應用程式，才能安裝 Win32 應用程式。 此功能只會在 Intune 管理代理程式升級至 1904 版本 (大於 1.18.120.0) 後開放使用，這可能會在我們將服務升級到 1904 後，另外花費 1 到 2 週的時間。 在 Intune 中，選取 [用戶端應用程式] > [應用程式] > [新增] 以顯示 [新增應用程式] 刀鋒視窗。 選取 [Windows 應用程式 (Win32)] 作為 [應用程式類型]。 如需詳細資訊，請參閱 [Intune 獨立版 - Win32 應用程式管理](apps-win32-app-management.md)。

### <a name="new-device-restriction-setting-for-android-enterprise-device-owner-let-users-connect-to-wi-fi-networks-on-android-enterprise-dedicated-devices-running-multi-app-kiosk-mode---3041940---"></a>Android Enterprise、裝置擁有者的新裝置限制設定：讓使用者連線到執行多應用程式 Kiosk 模式 Android Enterprise 專用裝置上的 Wi-Fi 網路 <!--3041940 -->
管理員將能夠切換新設定，讓使用者在其執行多應用程式 Kiosk 模式的 Android Enterprise 專用裝置上設定藍牙。 若要在 Intune 主控台中查看這項設定，請選擇 [Intune] > [裝置設定] > [設定檔] > [建立設定檔]，針對平台選擇 [Android Enterprise] > 針對設定檔類型選擇 [僅限裝置擁有者、裝置限制] > [設定] > [專用裝置] > 從 [Kiosk 模式] 設定的下拉式清單中選取 [多應用程式]。 稱為 [Wi-Fi 設定] 的選項將會可供啟用。 

適用於：執行多應用程式 Kiosk 模式的 Android Enterprise 專用裝置。 

### <a name="new-device-restriction-setting-for-android-enterprise-device-owner-let-users-configure-bluetooth-and-pairing-on-android-enterprise-dedicated-devices---3041941---"></a>Android Enterprise、裝置擁有者的新裝置限制設定：讓使用者設定藍牙，並在 Android Enterprise 專用裝置上進行配對 <!--3041941 -->
管理員將能夠切換新設定，讓使用者在其執行多應用程式 Kiosk 模式的 Android Enterprise 專用裝置上設定藍牙。 若要在 Intune 主控台中查看這項設定，請選擇 [Intune] > [裝置設定] > [設定檔] > [建立設定檔]，針對平台選擇 [Android Enterprise] > 針對設定檔類型選擇 [僅限裝置擁有者、裝置限制] > [設定] > [專用裝置] > 從 [Kiosk 模式] 設定的下拉式清單中選取 [多應用程式]。 稱為 [藍牙設定] 的選項將會開放啟用。 

適用於：執行多應用程式 Kiosk 模式的 Android Enterprise 專用裝置。 

### <a name="monitor-security-baseline-status-public-preview----3082047---"></a>監視安全性基準狀態 (公開預覽) <!-- 3082047 --> 
當您為安全基準監視 [裝置狀態] 時，檢視將會透過基準類別組織狀態，例如 [上方鎖定]、[BitLocker] 及 [瀏覽器] 等。 所有可用的基準類別將會隨即呈現。 針對每個類別，您將會看到有多少裝置不符合特定的基準類別、設定錯誤，或不適用。

###  <a name="intune-security-tasks-for-defender-atp-in-public-preview----3208597---"></a>Defender ATP 的 Intune 安全性工作 (公開預覽) <!-- 3208597 -->
作為即將進入公開預覽的功能，Intune 將會針對新宣告的 Microsoft Defender 威脅及弱點管理新增安全性工作。  透過這項整合，Windows Defender ATP (WDATP) 中的安全性操作管理員能更有效地針對 Intune 管理員面對的新威脅，傳遞建議的補救措施。 新增安全性工作，可新增一種風險式的方法，探索、優先處理及補救端點弱點和錯誤設定。

或要深入了解 Intune 中的安全性工作，請參閱 [using Intune security tasks to extend Microsoft Defender ATP’s Threat and Vulnerability Management](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/Microsoft-Intune-security-tasks-extend-Microsoft-Defender-ATP-s/ba-p/369857) (使用 Intune 安全性工作延伸 Microsoft Defender ATP 的威脅及弱點管理) 部落格文章。 

### <a name="create-and-use-oemconfig-device-configuration-profiles-in-intune----3305883---"></a>在 Intune 中建立和使用 OEMConfig 裝置組態設定檔 <!-- 3305883 -->
Intune 將會支援使用 OEMConfig 設定 Android Enterprise 裝置。 具體來說，您可以建立裝置組態設定檔，並使用 OEMConfig 將設定套用到 Android Enterprise 裝置 ([裝置設定] > [設定檔] > [建立設定檔] > [Android Enterprise] 平台)。

對 OEM 的支援目前是依個別 OEM 來提供。 如果您想要的 OEMConfig 應用程式不在 OEMConfig 應用程式清單中，請連絡 `IntuneOEMConfig@microsoft.com`。

適用於： 
- Android Enterprise

### <a name="new-device-restriction-settings-for-android-enterprise-device-owner----3574254---"></a>新增 Android Enterprise 裝置擁有者的裝置限制設定 <!-- 3574254 -->
在 Android Enterprise 裝置上，您可以建立裝置限制設定檔來允許或限制功能、設定密碼規則等 ([裝置設定] > [設定檔] > [建立設定檔] > 選擇 [Android Enterprise] 平台 > [僅限裝置擁有者] > [裝置限制] 設定檔類型)。 

新設定 (包括密碼設定) 會允許完全受控的裝置完整存取 Google Play Store 中的應用程式，且會提高可用性。 

若要查看目前的設定清單，請前往[允許或限制功能的 Android Enterprise 裝置設定](device-restrictions-android-for-work.md)。 

適用於：Android Enterprise 完全受控裝置

### <a name="check-for-a-tpm-chipset-in-a-windows-10-device-compliance-policy----3617671---"></a>在 Windows 10 裝置合規性政策中檢查是否有 TPM 晶片組 <!-- 3617671 -->
許多 Windows 10 及更新版本的裝置都具有信賴平台模組 (TPM) 晶片組。 新的相容性設定會檢查裝置上是否有 TPM。

[Windows 10 及更新版本的相容性原則設定](compliance-policy-create-windows.md)會列出目前的設定。

適用於： 
- Windows 10 及更新版本

### <a name="configure-your-win32-apps-to-be-installed-on-intune-enrolled-azure-ad-joined-devices----3695227---"></a>設定在已註冊 Intune 並加入 Azure AD 之裝置上安裝您的 Win32 應用程式 <!-- 3695227 -->
您將能夠指派您 Win32 應用程式在向 Intune 註冊且已加入 Azure AD 的裝置上安裝。 如需 Intune 中 Win32 應用程式的詳細資訊，請參閱 [Win32 應用程式管理](apps-win32-app-management.md)。

### <a name="windows-defender-advanced-threat-protection-baseline----3754134---"></a>Windows Defender 進階威脅防護基準 <!-- 3754134 -->
我們將會新增新的基準，協助您設定 Windows Defender 進階威脅防護設定。

### <a name="device-overview-shows-primary-user---794259---"></a>裝置概觀會顯示主要使用者 <!--794259 -->
裝置概觀頁面會顯示主要使用者，也稱為使用者裝置親和性使用者 (UDA)。 若要查看裝置的主要使用者，請選擇 [Intune] > [裝置] > [所有裝置] > 選擇裝置。 主要使用者會出現在 [概觀] 頁面頂端附近。

### <a name="expanded-support-for-android-enterprise-fully-managed-devices----3903241-3903244-3903246---"></a>擴展 Android Enterprise 完全受控裝置的支援 <!-- 3903241, 3903244, 3903246 -->
我們將會擴展對 Android Enterprise 完全受控裝置 ([在 2019 年 1 月首次宣告](whats-new.md#week-of-january-14-2019)) 的支援，使其包含下列項目：
- 合規性
- 條件式存取
- 新的終端使用者應用程式

若要設定完全受控的 Android 裝置，請前往 [裝置註冊] > [Android 註冊] > [公司擁有、完全受控的使用者裝置]。 完全受控的 Android 裝置支援仍在預覽階段，某些 Intune 功能可能無法完全正常運作。 

### <a name="additional-managed-google-play-app-reporting-for-android-enterprise-work-profile-devices----4105925---"></a>Android Enterprise 工作設定檔裝置的其他受控 Google Play 應用程式報告 <!-- 4105925 -->
針對部署到 Android Enterprise 工作設定檔裝置的受控 Google Play 應用程式，您將能夠檢視裝置上所安裝應用程式的特定版本號碼。 這只適用於必要的應用程式。 未來版本中將會針對可用的應用程式啟用相同功能。

### <a name="ios-third-party-keyboards----4111843---"></a>iOS 協力廠商鍵盤 <!-- 4111843 -->
針對**協力廠商鍵盤**的 Intune 應用程式防護原則 (APP) 支援將因 iOS 平台的變更結束。 您將無法在 Intune 管理主控台中設定此設定，且無法在 Intune 應用程式 SDK 中於用戶端上實行此設定。

<!-- 1903 start-->

### <a name="block-users-from-scanning-for-windows-updates----3316758---"></a>封鎖使用者掃描 Windows 更新 <!-- 3316758 -->
我們將會新增新的 Windows 更新環狀設定，讓您可以用來封鎖使用者掃描 Windows 更新。 此設定將無法在入口網站中取得，但可使用 Intune 圖形 API 來設定。

### <a name="windows-update-notifications----3316782---"></a>Windows 更新通知 <!-- 3316782 -->
我們將會新增 Windows Update 環狀設定的支援，讓您可以設定您使用者看見的 Windows Update 通知。 此設定將無法在入口網站中取得，但可使用 Intune 圖形 API 來設定。

### <a name="easier-access-to-diagnostic-settings----3804627---"></a>更容易存取的診斷設定 <!-- 3804627 -->
我們會將新選項新增到 Intune 主控台中每個稽核紀錄工作負載中的 [稽核紀錄] 刀鋒視窗，讓您可以用來直接開啟 [診斷設定] 頁面。

## <a name="notices"></a>通知

[!INCLUDE [Intune notices](./includes/intune-notices.md)]

### <a name="see-also"></a>請參閱
如需近期發展的詳細資料，請參閱 [Microsoft Intune 的新功能](whats-new.md)。



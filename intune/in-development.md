---
title: 在開發-Microsoft Intune
titlesuffix: ''
description: 在開發過程中的 Microsoft Intune 功能
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/29/2019
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
ms.openlocfilehash: 3e068e2c9834290b705e8e7bc2f895636415f9ba
ms.sourcegitcommit: 69aaf89140f82f344404e75a69dc59d8a1585b10
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/30/2019
ms.locfileid: "58675437"
---
# <a name="in-development-for-microsoft-intune---april-2019"></a>在開發 Microsoft Intune-2019 年 4 月

若要可協助您的整備程度和計劃、 此頁面清單 Intune UI 更新及功能正在開發，但尚未發行。 此外：

- 如果我們預期，您必須採取動作，在變更之前，我們將發佈免費的 Office 訊息中心 post。
- 當為預覽功能啟動實際執行環境，或已正式推出，功能描述會移動關閉此頁面，並拖曳至[什麼是新的頁面](whats-new.md)。
- 此頁面並[什麼是新的頁面](whats-new.md)會定期更新。 請回來查看其他更新。
- 請參閱[M365 藍圖](https://www.microsoft.com/microsoft-365/roadmap?rtc=2&filters=EMS)策略性的交付項目與時間軸。

> [!Note]
> 這些項目會反映 Microsoft 的未來版本中推出的 Intune 功能的目前預期動作。 日期和個別的功能可能會變更。 並非所有的項目，在開發過程中會對此頁面中的功能描述。

**RSS 摘要**：將下列 URL 複製並貼上至您的摘要讀取器中，以在本頁更新時收到通知：`https://docs.microsoft.com/api/search/rss?search=%22in+development+-+microsoft+intune%22&locale=en-us`

<!--
## What's coming to Intune in the Azure portal 
## What's coming to Intune apps
## Notices
-->
 
## <a name="intune-in-the-azure-portal"></a>Azure 入口網站中的 Intune

<!-- 1904 start-->

### <a name="set-login-settings-and-control-restart-options-on-macos-devices----1210083---"></a>設定登入設定，並控制在 macOS 裝置上的重新啟動選項 <!-- 1210083 -->
在 macOS 裝置上，您可以建立裝置組態設定檔 (**裝置組態** > **設定檔** > **建立設定檔**>選擇**macOS**平台 >**裝置功能**設定檔類型)。 新的登入] 視窗設定會包含項目，例如顯示自訂的橫幅，請選擇使用者如何登入、 顯示或隱藏 [電源設定等。

若要查看目前的設定，請前往[macOS 裝置功能設定](macos-device-features-settings.md)。

適用於： macOS

### <a name="advanced-settings-for-windows-defender-firewall----1311949---"></a>Windows Defender 防火牆的進階的設定 <!-- 1311949 -->
您很快就可以使用 Intune 來管理適用於 Windows Defender 用戶端上的自訂的防火牆規則。 規則可指定應用程式、 網路位址和連接埠的輸入和輸出行為。 

### <a name="require-app-protection-conditional-access----1634317---"></a>需要應用程式保護條件式存取  <!--1634317 -->
您將能夠使用*需要應用程式保護原則*，以確認原則會防止使用者存取您所保護的資料，使用條件式存取的登入完成之前套用至使用者的應用程式。 雖然原則保證可能會變慢的第一個的使用體驗，有助於防止網路問題、 系統管理的設定錯誤或刻意設計的工作，以阻止應用程式保護原則。 

### <a name="deployment-of-online-licensed-microsoft-store-for-business-apps----16726660---"></a>線上授權商務用 Microsoft Store 應用程式的部署 <!-- 16726660 -->
您將能夠在裝置內容中指派必要的線上授權商務用 Microsoft Store 應用程式。 以此方式部署商務用 Microsoft Store 應用程式，即可在裝置上為所有使用者安裝應用程式。 這僅適用於 Windows 10 RS4+ 電腦裝置。 您可以從 MSFB 線上授權應用程式的用戶端應用程式指派頁面，存取在裝置內容中安裝的選項。

### <a name="include-and-exclude-mixture-of-user-groups-and-device-groups-when-assigning-policies-and-profiles----1807547---"></a>包含與排除混合的使用者群組和裝置群組指派原則和設定檔時 <!-- 1807547 -->
指派合規性政策或組態設定檔時，您可以指派這些安全性群組與使用者或裝置。 目前，您可以在其中包含與排除只有使用者群組*或*include 和 exclude 只有裝置群組。 您不能包含和排除混合的群組，例如包含 使用者群組*和*排除裝置群組。

您將能夠包含和排除使用者群組和裝置群組的混合。 您可以包含一群使用者，並排除裝置群組。 例如，您可以指派，或將裝置組態設定檔部署到一群使用者，但排除個人裝置。

[指派裝置組態設定檔](device-profile-assign.md)包含更多有關將設定檔指派給使用者群組和裝置群組。

適用於： 所有平台

### <a name="retire-noncompliant-devices----1827291---"></a>淘汰不符合規範的裝置 <!-- 1827291 -->
我們要新增新的合規性動作，以淘汰不符合規範的裝置。 淘汰不符合規範的裝置移除所有的公司資料，也會移除該裝置由 Intune 所管理。 當達到設定的值，以天為單位，就會執行此動作。 最小值為 30 天。 

### <a name="configure-settings-for-kernel-extensions-on-macos-devices----2043024---"></a>在 macOS 裝置上設定核心延伸模組 <!-- 2043024 -->
在 macOS 裝置上，您可以建立裝置組態設定檔 (**裝置組態** > **設定檔** > **建立設定檔**>選擇**macOS**平台)。 新的設定群組可讓您設定及使用核心延伸模組，您的裝置。

適用於：macOS 10.13.2 和更新版本

### <a name="configure-profile-to-skip-some-screens-during-setup-assistant----2276470---"></a>設定設定檔，以在設定助理期間略過一些畫面 <!-- 2276470 -->
當您建立 macOS 註冊設定檔時，可以將它設定成在使用者完成設定助理時略過下列任何畫面：
- Android 移轉
- 顯示色調
- 隱私權
- iCloudStorage，如果您建立新的設定檔或編輯設定檔，則所選略過畫面需要與 Apple MDM 伺服器同步處理。 使用者可以發出裝置的手動同步處理，這樣在取得設定檔變更時才不會有延遲。
如需詳細資訊，請參閱[使用裝置註冊計劃或 Apple School Manager 自動註冊 macOS 裝置](device-enrollment-program-enroll-macos.md)。

### <a name="device-users-can-view-all-managed-apps-theyve-installed-or-tried-to-install----2352913---"></a>裝置使用者可以檢視所有受管理的應用程式，它們已安裝，或嘗試安裝 <!-- 2352913 -->
針對 Windows 公司入口網站將會列出所有受管理的應用程式&ndash;必要且可用&ndash;使用者的裝置上所安裝。 使用者將能夠檢視嘗試並暫止應用程式安裝，以及其目前的狀態。 如果您的組織不讓應用程式，必要或可用，則使用者會看到訊息，說明已安裝任何公司應用程式。 使用者也會無法排序或篩選應用程式安裝狀態。

### <a name="scope-tags-for-apple-vpp-tokens---2371886---"></a>Apple VPP 權杖的範圍標籤 <!--2371886 -->
您可以將範圍標記新增至 Apple VPP 權杖。 只有使用相同的範圍標籤指派的使用者必須具有該標記的 Apple VPP 權杖的存取。 VPP 應用程式和使用該權杖購買的電子書會繼承其範圍標籤。 如需有關範圍標籤的詳細資訊，請參閱[使用 RBAC 和範圍標記](scope-tags.md)。

### <a name="use-applicability-rules-when-creating-windows-10-device-configuration-profiles----2549910---"></a>當使用 「 適用性規則 」 建立的 Windows 10 裝置組態設定檔 <!-- 2549910 -->
建立 Windows 10 裝置組態設定檔 (**裝置組態** > **設定檔** > **建立設定檔** > **Windows 10**平台)。 您將能夠建立**適用性規則**因此設定檔僅適用於特定版本或特定版本。 比方說，您會建立設定檔，可讓某些 BitLocker 設定。 當您新增設定檔之後時，使用適用性規則，因此設定檔僅適用於執行 Windows 10 企業版的裝置。

適用於： 
- Windows 10 及更新版本

### <a name="enable-win32-app-dependencies----2617348---"></a>啟用 Win32 應用程式相依性 <!-- 2617348 -->
公開預覽狀態-以系統管理員，您可以為需要其他應用程式會安裝為相依性，然後再安裝 Win32 應用程式。 具體來說，該裝置在安裝 Win32 應用程式之前，必須安裝相依的應用程式。 在 Intune 管理代理程式已升級為 1904年版本 （大於 1.18.120.0） 可能需要 1 或 2 個額外週，我們為 1904年升級服務之後，才會提供這項功能。 在 Intune 中，選取**用戶端應用程式** > **應用程式** > **新增**顯示**新增應用程式**刀鋒視窗。 選取  **Windows 應用程式 (Win32)** 作為**應用程式類型**。 如需詳細資訊，請參閱 < [Intune 獨立部署-Win32 應用程式管理](apps-win32-app-management.md)。

### <a name="new-device-restriction-setting-for-android-enterprise-device-owner-let-users-connect-to-wi-fi-networks-on-android-enterprise-dedicated-devices-running-multi-app-kiosk-mode---3041940---"></a>Android Enterprise 裝置擁有者的新裝置限制設定： 讓使用者連線到 Wi-fi 網路上執行多個應用程式的 kiosk 模式的 Android 企業專用裝置 <!--3041940 -->
系統管理員將能夠切換新的設定，可讓使用者執行多重應用程式的 kiosk 模式在專用的 Android 企業裝置上設定藍芽。 若要查看這項設定在 Intune 主控台中，選擇**Intune** > **裝置組態** > **設定檔** >  **建立設定檔**> 選擇**Android Enterprise**平台 >**只有裝置擁有者、 裝置限制**設定檔類型 >**設定**  > **專用裝置**> 選取**多應用程式**從**Kiosk 模式**設定下拉式清單。 選項呼叫**Wi-fi 組態**可啟用。 

適用於： Android 的企業專用執行多個應用程式的 kiosk 模式的裝置。 

### <a name="new-device-restriction-setting-for-android-enterprise-device-owner-let-users-configure-bluetooth-and-pairing-on-android-enterprise-dedicated-devices---3041941---"></a>Android Enterprise 裝置擁有者的新裝置限制設定： 讓使用者設定藍芽及配對在專用的 Android 企業裝置上 <!--3041941 -->
系統管理員將能夠切換新的設定，可讓使用者執行多重應用程式的 kiosk 模式在專用的 Android 企業裝置上設定藍芽。 若要查看這項設定在 Intune 主控台中，選擇**Intune** > **裝置組態** > **設定檔** >  **建立設定檔**> 選擇**Android Enterprise**平台 >**只有裝置擁有者、 裝置限制**設定檔類型 >**設定**  > **專用裝置**> 選取**多應用程式**從**Kiosk 模式**設定下拉式清單。 選項呼叫**藍芽設定**可啟用。 

適用於： Android 的企業專用執行多個應用程式的 kiosk 模式的裝置。 

### <a name="monitor-security-baseline-status-public-preview----3082047---"></a>監視安全性基準狀態 （公開預覽） <!-- 3082047 --> 
當您監視*裝置狀態*您的安全性基準，檢視將狀態依照基準類別組織，例如*鎖定上*， *BitLocker*，和*瀏覽器*。 將表示所有可用的基準線類別目錄。 每個類別中，您會看到有多少裝置不符合特定基準類別、 設定錯誤，或不適用。

###  <a name="intune-security-tasks-for-defender-atp-in-public-preview----3208597---"></a>Defender atp （公開預覽） 中的 Intune 安全性工作 <!-- 3208597 -->
即將為公開預覽，Intune 很快就會加安全性工作的新發表的 Microsoft Defender 威脅和弱點管理。  透過這項整合，安全性作業管理員在 Windows Defender ATP (WDATP) 可以更有效地傳達給 Intune 系統管理員的新興威脅的建議的補救措施。 新增安全性工作會將風險為基礎的方法來探索、 設定優先順序，以及補救端點弱點和錯誤設定。

若要深入了解在 Intune 中的安全性工作，請參閱部落格文章有關[來擴充 Microsoft Defender ATP 的威脅和弱點管理使用 Intune 的安全性工作](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/Microsoft-Intune-security-tasks-extend-Microsoft-Defender-ATP-s/ba-p/369857)。 

### <a name="create-and-use-oemconfig-device-configuration-profiles-in-intune----3305883---"></a>建立並在 Intune 中使用 OEMConfig 裝置組態設定檔 <!-- 3305883 -->
Intune 將支援 OEMConfig 設定 Android 企業裝置。 具體來說，您可以建立裝置組態設定檔，並將設定套用至使用 OEMConfig 的 Android 企業裝置 (**裝置組態** > **設定檔** > **建立設定檔** > **Android enterprise**平台)。

Oem 的支援目前為每個 OEM 為基礎。 如果您想要的 OEMConfig 應用程式沒有 OEMConfig 應用程式清單中，請連絡`IntuneOEMConfig@microsoft.com`。

適用於： 
- Android Enterprise

### <a name="new-device-restriction-settings-for-android-enterprise-device-owner----3574254---"></a>新的 Android Enterprise 裝置擁有者的裝置限制設定 <!-- 3574254 -->
Android 企業裝置，您可以建立允許或限制功能、 設定密碼規則，和更多功能裝置限制設定檔 (**裝置組態** > **設定檔** > **建立設定檔**> 選擇**Android Enterprise**平台 >**只有裝置擁有者 > 裝置限制**設定檔類型)。 

新的設定，包括密碼設定，讓完整的存取權受到完整管理的裝置，在 Google Play 商店中的應用程式，因此多個可用。 

若要查看目前的設定清單，請前往[允許或限制功能的 Android Enterprise 裝置設定](device-restrictions-android-for-work.md)。 

適用於： Android 企業完全受管理的裝置

### <a name="check-for-a-tpm-chipset-in-a-windows-10-device-compliance-policy----3617671---"></a>Windows 10 裝置的合規性政策中的 TPM 晶片組的核取 <!-- 3617671 -->
許多 Windows 10 和更新版本的裝置有受信任的平台模組 (TPM) 晶片。 新的合規性設定會檢查裝置上是否有 TPM。

[Windows 10 和更新版本的合規性政策設定](compliance-policy-create-windows.md#windows-10-and-later-policy-settings)列出目前的設定。

適用於： 
- Windows 10 及更新版本

### <a name="configure-your-win32-apps-to-be-installed-on-intune-enrolled-azure-ad-joined-devices----3695227---"></a>設定您的 Win32 應用程式安裝在 Intune 中註冊 Azure AD 已加入裝置 <!-- 3695227 -->
您將能夠的指派您的 Win32 應用程式安裝在 Intune 註冊的 Azure AD 已加入裝置。 如需有關在 Intune 中的 Win32 應用程式的詳細資訊，請參閱 < [Win32 應用程式管理](apps-win32-app-management.md)。

### <a name="windows-defender-advanced-threat-protection-baseline----3754134---"></a>Windows Defender 進階威脅防護基準 <!-- 3754134 -->
我們要新增新的基準，可協助您設定 Windows Defender 進階威脅防護設定。

### <a name="device-overview-shows-primary-user---794259---"></a>裝置概觀會顯示主要使用者 <!--794259 -->
裝置的 [概觀] 頁面會顯示主要使用者，也稱為 「 使用者裝置親和性使用者 (UDA)。 若要查看裝置之主要使用者，請選擇**Intune** > **裝置** > **所有裝置**> 選擇裝置。 主要的使用者會靠近頂端**概觀**頁面。

### <a name="expanded-support-for-android-enterprise-fully-managed-devices----3903241-3903244-3903246---"></a>已擴大受到完整管理的 Android 企業裝置的支援 <!-- 3903241, 3903244, 3903246 -->
我們將擴充的完全受控的 Android 企業裝置的支援 ([首次推出於 2019 年 1 月](whats-new.md#week-of-january-14-2019)包含下列：
- 合規性
- 條件式存取
- 新的終端使用者應用程式

若要設定完全受控的 Android 裝置，請前往 [裝置註冊] > [Android 註冊] > [公司擁有、完全受控的使用者裝置]。 支援完全受管理的 Android 裝置會維持預覽狀態，以及一些 Intune 功能可能無法完全正常運作。 

### <a name="additional-managed-google-play-app-reporting-for-android-enterprise-work-profile-devices----4105925---"></a>其他受控 Google Play 應用程式適用於 Android 的企業工作設定檔裝置的報告 <!-- 4105925 -->
受控的 Google Play 應用程式部署到 Android 的企業工作設定檔的裝置，將可以檢視安裝在裝置上的應用程式的特定版本號碼。 這適用於必要應用程式。 在未來版本中，將會啟用可用的應用程式的相同功能。

### <a name="ios-third-party-keyboards----4111843---"></a>iOS 協力廠商鍵盤 <!-- 4111843 -->
支援 Intune 應用程式保護原則 （應用程式）**協力廠商鍵盤**設定將會因為 iOS 平台變更而結束。 您無法在 Intune 管理主控台中設定此設定，則不會強制 Intune App SDK 中的用戶端上。

<!-- 1903 start-->

### <a name="block-users-from-scanning-for-windows-updates----3316758---"></a>禁止使用者掃描 Windows 更新 <!-- 3316758 -->
我們將新增新 Windows 更新通道的設定，您可以使用封鎖掃描 Windows 更新的使用者。 此設定無法從入口網站中使用，但可以使用 Intune 圖形 API 來設定。

### <a name="windows-update-notifications----3316782---"></a>Windows 更新通知 <!-- 3316782 -->
我們將新增支援 Windows Update ring 設定，因此您可以設定您的使用者看到的 Windows 更新通知。 此設定無法從入口網站中使用，但可以使用 Intune 圖形 API 來設定。

### <a name="changes-to-company-portal-enrollment-for-ios-12-device-users---3448635---"></a>變更為適用於 iOS 的公司入口網站註冊 12 的裝置使用者 <!--3448635 --> 
適用於 iOS 的公司入口網站將會更新，應用程式註冊畫面和步驟來配合在 Apple iOS 12.2 中發行的 MDM 註冊變更。 更新的工作流程現在會提示使用者：

- 允許 Safari 以開啟公司入口網站 （透過 Safari)，並下載管理設定檔，然後再回到 公司入口網站應用程式。
- 開啟 設定 應用程式在其裝置上安裝管理設定檔。
- 返回公司入口網站應用程式，以完成註冊。

如需有關如何準備這些變更的詳細資訊，請參閱 < [Microsoft 技術社群文章](https://aka.ms/CP_changes_iOS12)。 在此同時，若要支援新的 iOS 註冊在公司入口網站中，我們已更新中的步驟[在 Intune 中的註冊 iOS 裝置](https://docs.microsoft.com/en-us/intune/ios-enroll)。 Apple 發行 iOS 版 12.2 之後，這些文件變更會即時。 

### <a name="easier-access-to-diagnostic-settings----3804627---"></a>更容易存取的診斷設定 <!-- 3804627 -->
我們將新增的新選項**稽核記錄檔**刀鋒視窗中每個稽核記錄檔工作負載，在 Intune 主控台中，您可以使用來直接開啟*診斷設定*頁面。

## <a name="notices"></a>通知

[!INCLUDE [Intune notices](./includes/intune-notices.md)]

### <a name="see-also"></a>請參閱
如需近期發展的詳細資料，請參閱 [Microsoft Intune 的新功能](whats-new.md)。



---
title: 開發中 - Microsoft Intune
titleSuffix: ''
description: 正在開發的 Microsoft Intune 功能
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/30/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4bd5392abba3ea22127cb9bcbbb53ec4929f2d5e
ms.sourcegitcommit: 1494ff4b33c13a87f20e0f3315da79a3567db96e
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2019
ms.locfileid: "71166346"
---
# <a name="in-development-for-microsoft-intune---september-2019"></a>Microsoft Intune 正在開發的項目 - 2019 年 9 月

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

<!-- Common categories:  
#### App management
#### Device configuration
#### Device enrollment
#### Device management
#### Intune apps
#### Monitor and troubleshoot
#### Role-based access control
#### Security

-->
 
<!-- ***********************************************-->
## <a name="app-management"></a>應用程式管理

### <a name="managed-google-play-private-lob-apps----1464182----"></a>受控 Google Play 私用 LOB 應用程式 <!-- 1464182  -->
Intune 可讓 IT 系統管理員透過內嵌在 Intune 主控台中的 iframe，將私人 Android LOB 應用程式發佈至受控 Google Play。  目前，IT 系統管理員需要將 LOB 應用程式直接發佈到 Google 的「Play 發行」主控台，這需要許多步驟，而且非常耗時。  這項新功能可讓您使用最少的一組步驟輕鬆發佈 LOB 應用程式，而不需要離開 Intune 主控台。  任何使用受控 Google Play 的 Android 企業管理案例都可以利用這項功能（工作設定檔、專用、完全受控和未註冊的裝置）。  從 Intune，選取 [用戶端應用程式]   > [應用程式]   > [新增]  。 然後，從 [**應用程式類型**] 清單中選取 [**受控 Google Play** ]。 如需受控 Google Play 應用程式的詳細資訊，請參閱[使用 Intune 將受控 Google Play 應用程式新增至 Android Enterprise 裝置](apps-add-android-for-work.md)。

### <a name="company-portal-app-installation-status-messages----2514416----"></a>公司入口網站應用程式安裝狀態訊息 <!-- 2514416  -->
公司入口網站應用程式會向終端使用者顯示額外的應用程式安裝狀態訊息。 下列條件將適用于新的 Win32 相依性功能：
- 應用程式無法啟動。 不符合系統管理員所定義的相依性。
- 已成功安裝應用程式，但需要重新開機。
- 應用程式正在安裝，但需要重新開機才能繼續。

### <a name="managed-google-play-iframe-support----2871756----"></a>受控 Google Play iframe 支援 <!-- 2871756  -->
Intune 可讓您透過受控 Google Play iframe，直接在 Intune 主控台中新增和管理網頁連結。  這可讓 IT 系統管理員提交 URL 和圖示圖形，然後將這些連結部署到裝置，就像一般的 Android 應用程式一樣。 任何使用受控 Google Play 的 Android 企業管理案例都可以利用這項功能（工作設定檔、專用、完全受控和未註冊的裝置）。  從 Intune，選取 [用戶端應用程式]   > [應用程式]   > [新增]  。 然後，從 [**應用程式類型**] 清單中選取 [**受控 Google Play** ]。 如需受控 Google Play 應用程式的詳細資訊，請參閱[使用 Intune 將受控 Google Play 應用程式新增至 Android Enterprise 裝置](apps-add-android-for-work.md)。

### <a name="macos-support-for-vpp-apps----3173501----"></a>VPP 應用程式的 macOS 支援 <!-- 3173501  -->
使用 Apple Business Manager 購買的 macOS 應用程式，會在 Intune 中的 Apple VPP 權杖同步處理時顯示在主控台中。 您可以使用 Intune 主控台為群組指派、撤銷和重新指派裝置和使用者型授權。 Microsoft Intune 可協助您管理已購買供公司使用的 VPP 應用程式，方法是：
- 從應用程式市集報告授權資訊。
- 追蹤您已經使用多少個授權。
- 協助您不要安裝超過擁有數目的應用程式複本。
如需有關 Intune 與 VPP 的詳細資訊，請參閱[使用 Microsoft Intune 管理大量採購的應用程式與書籍](vpp-apps.md)。

### <a name="macos-support-for-web-apps----3174427----"></a>Web 應用程式的 macOS 支援 <!-- 3174427  -->
Web 應用程式 (可讓您新增 Web URL 的捷徑) 可以使用 macOS 公司入口網站安裝到 Dock。 使用者可以在 macOS 公司入口網站中，從 Web 應用程式的 [應用程式詳細資料] 頁面存取 [安裝]  動作。 如需**Web 連結**應用程式類型的詳細資訊，請參閱[將應用程式新增至 Microsoft Intune](apps-add.md)。

#### <a name="assign-microsoft-edge-beta-for-macos----4678761----"></a>為 macOS 指派 Microsoft Edge Beta <!-- 4678761  -->
您將能夠為 macOS 裝置新增並指派最新版本的 Microsoft Edge Beta 至 Intune。 從 Intune，選取 **[用戶端應用** > **程式** > ] [**新增應用程式** > ] [**Microsoft Edge-macOS**]。 然後，將 Microsoft Edge Beta 指派給想要的群組。 Microsoft 自動更新（MAU）可讓 Microsoft Edge 保持在最新狀態。 如需 Microsoft Edge 的詳細資訊，請參閱[使用 Microsoft edge 搭配 Microsoft Intune 來管理 web 存取](manage-microsoft-edge.md)。

### <a name="read-and-write-graph-api-operations-for-intune-apps----5031704----"></a>Intune 應用程式的讀取和寫入圖形 API 作業 <!-- 5031704  -->
應用程式可以使用沒有使用者認證的應用程式身分識別，透過讀取和寫入作業呼叫 Intune 圖形 API。 如需有關存取「適用於 Intune 的 Microsoft Graph API」的詳細資訊，請參閱[在 Microsoft Graph 中使用 Intune](https://docs.microsoft.com/graph/api/resources/intune-graph-overview?view=graph-rest-1.0) \(英文\)。

### <a name="configure-app-notification-content-for-organization-accounts----2576686---"></a>設定組織帳戶的代理程式更新內容 <!-- 2576686 -->
Android 和 iOS 裝置上的 Intune 應用程式保護原則 (應用程式) 可讓您控制組織帳戶的代理程式更新內容。 這項功能將需要應用程式的支援, 而且可能無法供所有啟用應用程式的應用程式使用。 如需 APP 的詳細資訊，請參閱[什麼是應用程式防護原則？](app-protection-policy.md)

### <a name="available-google-play-app-reporting-for-android-work-profiles----3041956----"></a>報告 Android 工作設定檔的可用 Google Play 應用程式 <!-- 3041956  -->
針對安裝在 Android 工作設定檔裝置上的可用應用程式，您可以檢視應用程式安裝狀態，以及受控 Google Play 應用程式的安裝版本。 如需詳細資訊，請參閱[如何監視應用程式保護原則](app-protection-policies-monitor.md)、[使用 Intune 管理 Android 工作設定檔裝置](android-enterprise-overview.md)及[受控的 Google Play 應用程式類型](apps-add-android-for-work.md#managed-google-play-app-types)。

<!-- ***********************************************-->
## <a name="device-configuration"></a>裝置設定

### <a name="device-features-device-restrictions-and-extension-profiles-for-ios-and-macos-settings-are-shown-by-enrollment-type----4886161----"></a>適用于 iOS 和 macOS 設定的裝置功能、裝置限制和延伸模組設定檔會以註冊類型顯示 <!-- 4886161  -->

在 Intune 中，您會建立 iOS 和 macOS 裝置的設定檔（**裝置** > 設定**設定檔** > 會為平臺 > 裝置功能**建立設定檔** >  **iOS**或**macOS**  、**裝置限制**或配置檔案類型的**擴充**功能）。 目前會列出這些設定檔中的可用設定。 

在未來的更新中，Intune 入口網站中的可用設定會依其適用的註冊類型分類：

- iOS
  - 所有註冊類型
  - 裝置註冊和自動裝置註冊
  - 自動裝置註冊

- macOS
  - 所有註冊類型
  - 裝置註冊
  - 使用者已核准並自動註冊裝置
  - 自動裝置註冊

適用於：

- iOS
  - [裝置功能](ios-device-features-settings.md)
  - [裝置限制](device-restrictions-ios.md)

- macOS
  - [裝置功能](macos-device-features-settings.md)
  - [裝置限制](device-restrictions-macos.md)
  - [擴充功能](kernel-extensions-settings-macos.md)

### <a name="new-voice-control-settings-for-supervised-ios-devices-running-in-kiosk-mode----4892835----"></a>以 kiosk 模式執行之受監督 iOS 裝置的新語音控制設定 <!-- 4892835  -->

在 Intune 中，您可以建立原則來執行受監督的 iOS 裝置做為 kiosk 或專用裝置（**裝置** > 設定**設定檔** > 建立適用于平臺的**設定檔** >  **iOS** >  配置檔案類型 > Kiosk 的裝置限制 **（僅限受監督）** ）。 

在未來的更新中，將會有您可以控制的新設定：

- **語音控制**：在 kiosk 模式中啟用裝置上的語音控制。
- **語音控制項的修改**：允許使用者在 kiosk 模式下變更裝置上的語音控制設定。

若要查看目前的設定，請移至 [ [IOS Kiosk （僅限受監督）] 設定](device-restrictions-ios.md#kiosk)。

適用於：

- iOS 13.0 與更新版本

### <a name="use-single-sign-on-for-apps-and-websites-on-your-ios-and-macos-devices----4893175----"></a>在您的 iOS 和 macOS 裝置上使用應用程式和網站的單一登入 <!-- 4893175  -->
在未來的更新中，iOS 和 macOS 裝置會有一些新的「單一登入」設定（**裝置配置** > **檔** > 會為**ios**或**macOS** **建立設定檔** > 配置檔案類型的平臺 >**裝置功能**）。

使用這些設定來設定單一登入體驗，特別是針對使用 Kerberos 驗證的應用程式和網站。 您可以選擇一般認證單一登入應用程式延伸模組，以及 Apple 的內建 Kerberos 延伸模組。

若要查看您可以設定的目前裝置功能，請移至[iOS 裝置功能](ios-device-features-settings.md)和[macOS 裝置功能](macos-device-features-settings.md)。

適用於：

- iOS 13.0 與更新版本
- macOS 10.15 與更新版本

### <a name="associate-domains-to-apps-on-macos-1015-devices----4898079----"></a>將網域關聯至 macOS 10.15 + 裝置上的應用程式 <!-- 4898079  -->
在 macOS 裝置上，您可以設定不同的功能，並使用原則將這些功能推送至您的裝置（**裝置** > 設定**配置** > 檔**建立設定檔** >  **macOS**配置檔案類型的平臺 >**裝置功能**）。 在未來的更新中，您將能夠將網域與您的應用程式建立關聯。 這項功能可協助與您的應用程式相關的網站共用認證，並可搭配 Apple 的單一登入擴充功能、通用連結和密碼自動填入使用。 

若要查看您可以設定的目前功能，請移至[Intune 中的 macOS 裝置功能設定](macos-device-features-settings.md)。

適用於：

- macOS 10.15 與更新版本

### <a name="use-itunes-and-apps-in-the-itunes-app-store-url-when-showing-or-hiding-apps-on-ios-supervised-devices----4928474----"></a>當顯示或隱藏 iOS 受監督裝置上的應用程式時，請使用 iTunes App store URL 中的 "itunes" 和 "apps" <!-- 4928474  --> 
在 Intune 中，您可以建立原則，以顯示或隱藏受監督的 iOS 裝置上的應用程式（**裝置** > 設定**設定檔** > 為平臺 > 裝置**建立設定檔** >  **iOS**  配置檔案類型的限制 >**顯示或隱藏應用程式（僅限受監督）** ）。 

您可以輸入 iTunes App store URL，例如`https://itunes.apple.com/us/app/work-folders/id950878067?mt=8`。 在未來的更新中，您將能夠在 URL 中`apps`使用`itunes`和，例如：

- `https://itunes.apple.com/us/app/work-folders/id950878067?mt=8`
- `https://apps.apple.com/us/app/work-folders/id950878067?mt=8`

如需這些設定的詳細資訊，請參閱[顯示或隱藏應用程式](device-restrictions-ios.md#show-or-hide-apps)。

適用於：

- iOS

### <a name="support-for-ikev2-vpn-profiles-for-ios----1943438---"></a>支援 iOS 版的 IKEv2 VPN 設定檔 <!-- 1943438 -->
您可以使用 IKEv2 通訊協定建立 iOS 原生 VPN 用戶端的 VPN 設定檔。 IKEv2 是 [裝置設定]   > [設定檔]   > [建立設定檔]   > [iOS]  (平台) > [VPN]  (設定檔類型) > [設定]  中的新連線類型。

這些 VPN 設定檔會設定原生的 VPN 用戶端。 因此，不會有 VPN 用戶端應用程式安裝或推送到受控裝置。 這項功能需要向 Intune 註冊裝置 (MDM 註冊)。

若要查看您目前可以設定的 VPN 設定，請前往[在 Microsoft Intune 中的 iOS 裝置上設定 VPN 設定](vpn-settings-ios.md)。

適用於：iOS


<!-- ***********************************************-->
## <a name="device-enrollment"></a>裝置註冊

### <a name="new-tenants-will-default-away-from-android-device-administrator-management----4869790----"></a>新的租使用者預設會離開 Android 裝置系統管理員管理 <!-- 4869790  -->
Android 企業的裝置系統管理員功能已被取代。 因此，建議您改為使用 Android Enterprise 來進行新的註冊。 在未來的更新中，新的租使用者將需要完成 Android 註冊中的下列必要條件步驟，才能使用裝置系統管理員管理：移至**Intune**  > **裝置註冊** >  **Android 註冊**具有裝置系統 > **管理許可權的個人和公司擁有的裝置**，會**使用裝置管理員來管理裝置。**  > 

現有的租使用者在其環境中將不會有任何變更。 

如需 Intune 中 Android 裝置系統管理員的詳細資訊，請參閱[android 裝置系統管理員註冊](android-enroll-device-administrator.md)。

### <a name="for-ios-devices-customize-the-enrollment-process-privacy-screen-of-the-company-portal----4394993----"></a>針對 iOS 裝置，請自訂公司入口網站的 [註冊程序隱私權] 畫面 <!-- 4394993  -->
使用 Markdown，您可以自訂使用者在 iOS 註冊期間看到的公司入口網站隱私權畫面。 具體來說，您可以自訂組織無法在裝置上查看或執行的操作清單。

<!-- ***********************************************-->
## <a name="device-management"></a>裝置管理

### <a name="deploy-software-updates-to-macos-devices----3194876---"></a>將軟體更新部署到 macOS 裝置 <!-- 3194876 -->
您將能夠將軟體更新部署到 macOS 裝置群組。 這項功能包括重要、固件、設定檔及其他更新。 您將能夠在下一次裝置簽入時傳送更新，或選取每週排程，將更新部署到您設定的時間或時段內。 當您想要更新標準工作時間以外的裝置時，或當您的技術服務人員已滿時，這會很有説明。 您也會取得已部署更新之所有 macOS 裝置的詳細報告。 您可以根據每個裝置深入探索報表，以查看特定更新的狀態。

### <a name="send-custom-notifications-to-a-device----4928910----"></a>將自訂通知傳送至裝置 <!-- 4928910  -->
您將能夠將自訂通知傳送到已安裝公司入口網站或 Intune 應用程式的特定裝置。 若要這麼做，請移至 [ **Intune**  > **裝置** > ] [**所有裝置**] > 選擇裝置 >**更多** > **傳送自訂通知**。 

### <a name="updates-to-android-enterprise-fully-managed-features----3464667-5227935-4062195-4631425-4631440---"></a>Android Enterprise 完全受控功能的更新 <!-- 3464667, 5227935, 4062195, 4631425, 4631440 -->

我們將為 Android 完全受控裝置新增下列支援：

- 適用于完全受控 Android 的 SCEP 憑證可用於以裝置擁有者身分管理之裝置上的 cert 驗證。 公司設定檔裝置上已支援 SCEP 憑證。  使用適用于裝置擁有者的 SCEP 憑證時，您將能夠： <!-- 5227935 -->
    - 在 Android Enterprise 的 DO 區段下建立 SCEP 設定檔
    - 連結 SCEP 憑證以進行驗證的 Wi-fi 設定檔
    - 連結 SCEP 憑證以進行驗證的 VPN 設定檔
    - 連結 SCEP 憑證以執行電子郵件設定檔以進行驗證（透過應用程式設定）
- Android Enterprise 裝置上將支援系統應用程式。 在 Intune 中，您將選取 [**用戶端應用** > **程式** > ] [**新增**] 來新增 Android Enterprise 系統應用程式。 在 [**應用程式類型**] 清單中，選取 [ **Android Enterprise 系統應用程式**]。 如需將應用程式新增至 Intune 的詳細資訊，請參閱[將應用程式新增至 Microsoft Intune](apps-add.md)。 <!-- 4062195 -->
- 在 [**裝置合規性** > ] [**Android Enterprise**  > **裝置擁有**者] 中，您將能夠建立設定 Google SafetyNet 證明層級的合規性政策。   <!-- 4631425 -->
- 在 Android Enterprise 完全受控裝置上，將支援行動威脅防禦提供者。 在 [**裝置合規性** > ] [**Android Enterprise**  > **裝置擁有**者] 中，您可以選擇可接受的威脅等級。 <!-- 4631440 --> [使用 Intune，透過 Android Enterprise 設定將裝置標示為符合規範或不符合規範](compliance-policy-create-android-for-work.md#device-owner)列出目前的設定。


適用於： 
- 完全受控的 Android Enterprise 裝置

<!-- ***********************************************-->
## <a name="monitor-and-troubleshoot"></a>監視及疑難排解

### <a name="updated-support-experience-------5012398------"></a>更新的支援體驗   <!--  5012398    -->
在持續改進的過程中，我們將會更新 Intune 的主控台內支援體驗。  我們將改善主控台內搜尋和常見問題的意見反應，並簡化工作流程以聯絡支援人員。     

<!-- ***********************************************-->
## <a name="security"></a>安全性

### <a name="tamper-protection-for-windows-defender-antivirus-----4705448---------"></a>Windows Defender 防毒軟體的防篡改保護  <!-- 4705448       -->
我們會將*防篡改保護*新增至 Intune 可針對 Windows Defender 防毒軟體管理的設定。 您將能夠使用適用于 Windows 10 endpoint protection 的裝置設定檔，來開啟或關閉防篡改保護功能。  如需有關防篡改保護的詳細資訊，請參閱 Windows 檔中的[使用防篡改保護來防止安全性設定變更](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-antivirus/prevent-changes-to-security-settings-with-tamper-protection)。 


<!-- ***********************************************-->
## <a name="notices"></a>通知

[!INCLUDE [Intune notices](./includes/intune-notices.md)]

## <a name="see-also"></a>請參閱
如需近期發展的詳細資料，請參閱 [Microsoft Intune 的新功能](whats-new.md)。





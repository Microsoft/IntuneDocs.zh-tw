---
title: 開發中 - Microsoft Intune
titleSuffix: ''
description: 正在開發的 Microsoft Intune 功能
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/07/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0e7c4e5ed45455dda941fb0c61c989c12c57135d
ms.sourcegitcommit: 29b1113dc04534c4c87c33c773c5a0e24266e042
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "71999319"
---
# <a name="in-development-for-microsoft-intune---october-2019"></a>Microsoft Intune 正在開發的項目 - 2019 年 10 月

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
## App management
## Device configuration
## Device enrollment
## Device management
## Intune apps
## Monitor and troubleshoot
## Role-based access control
## Security

-->
 
<!-- ***********************************************-->
## <a name="app-management"></a>應用程式管理

### <a name="additional-app-configuration-variable-available----4969237----"></a>有其他可用的應用程式設定變數 <!-- 4969237  -->
建立應用程式設定原則時，您將能夠在您的設定中包含 `AAD Device ID` 設定變數。 在 Intune 中，選取 [用戶端應用程式]   > [應用程式設定原則]   > [新增]  。 輸入您的設定原則詳細資料，然後選取 [**設定**] 以查看 [**設定設定**] 分頁。

### <a name="dark-mode-for-ios-company-portal----4911422----"></a>IOS 公司入口網站的深色模式 <!-- 4911422  -->
已規劃 iOS 公司入口網站的深色模式。 下載公司應用程式、管理您的裝置，並在您選擇的色彩配置中取得 IT 支援。 如需 iOS 公司入口網站的詳細資訊，請參閱[如何設定 Microsoft Intune 公司入口網站應用程式](../apps/company-portal-app.md)。

### <a name="prevent-installation-of-apps-from-unknown-sources-on-android-enterprise-devices----4760025----"></a>防止在 Android Enterprise 裝置上安裝來自不明來源的應用程式 <!-- 4760025  -->
若為 Android Enterprise 工作設定檔裝置，終端使用者將無法從不明來源將應用程式安裝到工作設定檔。 您也可以選擇性地將此限制延伸至個人設定檔。 如果您啟用這項限制，Android Enterprise 工作設定檔裝置上的使用者也將無法從不明來源將應用程式側載到裝置的個人端。 

### <a name="update-to-app-protection-ui-and-ios-app-provisioning-ui----4102027-4102029----"></a>應用程式保護 UI 和 iOS 應用程式布建 UI 的更新 <!-- 4102027, 4102029  -->
在 Intune 中建立和編輯應用程式保護原則和 iOS 應用程式布建設定檔的 UI 將會更新。 UI 變更包括：
- 使用在一個分頁中壓縮的 wizard 樣式格式的簡化體驗。 
- 要包含指派的建立流程更新。
- 在建立新的原則之前或編輯屬性時，在流覽屬性時所設定之所有專案的摘要頁面。 此外，編輯屬性時，摘要只會顯示來自所編輯屬性類別目錄中的專案清單。

### <a name="create-groups-of-management-objects-called-policy-sets----3762880----"></a>建立稱為原則集的管理物件群組 <!-- 3762880  -->
原則集可讓您建立已經存在的管理實體的參考組合，這些實體必須識別、設定目標，並以單一概念單位進行監視。 原則集不會取代現有的概念或物件。 系統管理員可以依現狀繼續指派個別物件。 原則集會參考個別的物件。 因此，對這些個別物件所做的任何變更都會反映在原則集內。  在 Intune 中，您將選取 **原則集**  > **建立** 來建立新的原則集。 

### <a name="win32-apps-on-windows-10-s-mode-devices----3747604----"></a>Windows 10 S 模式裝置上的 Win32 應用程式 <!-- 3747604  --> 
您將能夠在 Windows 10 S 模式管理的裝置上安裝和執行 Win32 應用程式。 您將能夠使用 Windows Defender 應用程式控制（WDAC） PowerShell 工具，為 S 模式建立一或多個補充原則。 使用 Device Guard 簽署入口網站簽署補充原則，然後透過 Intune 上傳和散發原則。 在 Intune 中，您可以藉由選取**用戶端應用程式** > **Windows 10 S 補充原則**來找到這項功能。 

### <a name="set-app-availability-based-on-a-date-and-time----3510685----"></a>根據日期和時間設定應用程式可用性 <!-- 3510685  -->
身為系統管理員，您將能夠設定所需應用程式的開始時間和期限時間。 在開始時，Intune 管理延伸模組會啟動應用程式內容下載，並加以快取。 應用程式將會在期限時間安裝。 針對可用的應用程式，[開始時間] 會決定應用程式何時會顯示在公司入口網站中。 在 Intune 中，選取 [用戶端應用程式]   > [應用程式]  。 然後，從清單中選取特定的應用程式，或選取 [**新增**] 以新增應用程式。 從 [應用程式] 分頁，選取 [**指派**]  >  [**新增群組**]。 將 [**指派類型**] 設定為 [**必要**]，然後選取 [**包含的群組**]。 將 [**讓所有使用者都需要此應用程式**] 設定為 **[是]** ，然後選取 [**編輯**] 以修改 [**使用者體驗**] 選項。 在 [**使用者體驗**] 分頁中，視需要設定 [**軟體可用時間**]。 如需新增應用程式的詳細資訊，請參閱[將應用程式新增至 Microsoft Intune](../apps/apps-add.md)。

### <a name="require-win32-apps-to-restart----3136567----"></a>需要 Win32 應用程式重新開機 <!-- 3136567  -->
您將能夠要求 Win32 應用程式必須在成功安裝後重新開機。 此外，您還可以選擇必須重新開機之前的時間量（寬限期）。

### <a name="company-portal-app-on-windows----1808082----"></a>Windows 上的公司入口網站應用程式 <!-- 1808082  -->
即使應用程式關閉，Windows 裝置上的公司入口網站應用程式也會更新，以向使用者顯示快顯通知。 當安裝狀態為 [已完成] 或 [失敗] 時，更新只會顯示可用應用程式的通知。 公司入口網站應用程式不會顯示必要應用程式的通知。

### <a name="company-portal-app-installation-status-messages----2514416----"></a>公司入口網站應用程式安裝狀態訊息 <!-- 2514416  -->
公司入口網站應用程式會向終端使用者顯示額外的應用程式安裝狀態訊息。 下列條件將適用于新的 Win32 相依性功能：
- 應用程式無法啟動。 不符合系統管理員所定義的相依性。
- 已成功安裝應用程式，但需要重新開機。
- 應用程式正在安裝，但需要重新開機才能繼續。

#### <a name="assign-microsoft-edge-beta-for-macos----4678761----"></a>為 macOS 指派 Microsoft Edge Beta <!-- 4678761  -->
您將能夠為 macOS 裝置新增並指派最新版本的 Microsoft Edge Beta 至 Intune。 從 Intune，選取 [**用戶端應用程式** >  個**應用程式** > **新增應用程式** > **Microsoft Edge-macOS**]。 然後，將 Microsoft Edge Beta 指派給想要的群組。 Microsoft 自動更新（MAU）可讓 Microsoft Edge 保持在最新狀態。 如需 Microsoft Edge 的詳細資訊，請參閱[使用 Microsoft edge 搭配 Microsoft Intune 來管理 web 存取](../apps/manage-microsoft-edge.md)。

### <a name="configure-app-notification-content-for-organization-accounts----2576686---"></a>設定組織帳戶的代理程式更新內容 <!-- 2576686 -->
Android 和 iOS 裝置上的 Intune 應用程式保護原則（應用程式）可讓您控制組織帳戶的代理程式更新內容。 這項功能將需要應用程式的支援，而且可能無法供所有啟用應用程式的應用程式使用。 如需 APP 的詳細資訊，請參閱[什麼是應用程式防護原則？](../apps/app-protection-policy.md)

### <a name="available-google-play-app-reporting-for-android-work-profiles----3041956----"></a>報告 Android 工作設定檔的可用 Google Play 應用程式 <!-- 3041956  -->
針對安裝在 Android 工作設定檔裝置上的可用應用程式，您可以檢視應用程式安裝狀態，以及受控 Google Play 應用程式的安裝版本。 如需詳細資訊，請參閱[如何監視應用程式保護原則](../apps/app-protection-policies-monitor.md)、[使用 Intune 管理 Android 工作設定檔裝置](../enrollment/android-enterprise-overview.md)及[受控的 Google Play 應用程式類型](../apps/apps-add-android-for-work.md#managed-google-play-app-types)。

<!-- ***********************************************-->
## <a name="device-configuration"></a>裝置設定


### <a name="new-device-configuration-settings-for-supervised-ios-and-ipados-devices----5199328----"></a>受監督 iOS 和 iPadOS 裝置的新裝置設定設定 <!-- 5199328  -->
在 iOS 和 iPadOS 裝置上，您可以建立設定檔來限制裝置上的功能和設定（**裝置**設定  > **配置**檔  > **建立設定檔** >  適用于平臺 > 裝置的**iOS/iPadOS**  配置檔案類型的限制）。 將會有您可以控制的新設定： 
- 存取檔案應用程式中的網路磁碟機機  
- 存取檔案應用程式中的 USB 磁片磁碟機 
- Wi-fi 一律開啟 

若要查看目前的設定，請前往[使用 Intune 允許或限制功能的 iOS 裝置設定](../configuration/device-restrictions-ios.md)。

適用於：
- iOS 13.0 與更新版本
- iPadOS 13.0 和更新版本

### <a name="connect-automatically-setting-is-removed-in-wi-fi-profiles-on-android-and-android-enterprise----5021055----"></a>Android 和 Android Enterprise 的 Wi-fi 設定檔中已移除 [自動連線] 設定 <!-- 5021055  -->
在 Android 和 Android Enterprise 裝置上，您可以建立 Wi-fi 設定檔來設定不同的設定（**裝置**設定  > **設定檔** > **建立設定檔** > **android**或**Android Enterprise**適用于配置檔案類型的平臺 > **wi-fi** ）。 將會移除 [**自動連線]** 設定，因為它[不受 Android 支援](https://developer.android.com/reference/android/net/wifi/WifiManager.html#enableNetwork%28int%2c%20boolean%29)。 

如果您在 Wi-fi 設定檔中使用此設定，您可能會注意**到自動**連線不會有作用。 您不需要採取任何動作，但請注意，Intune 使用者介面中已移除這項設定。

若要查看目前的設定，請移至 [ [Android wi-fi 設定](../configuration/wi-fi-settings-android.md)] 或 [ [android Enterprise wi-fi 設定](../configuration/wi-fi-settings-android-enterprise.md)]。

適用於：
- Android
- Android 企業

### <a name="create-a-global-http-proxy-on-android-enterprise-device-owner-devices----4816339----"></a>在 Android Enterprise 裝置擁有者裝置上建立全域 HTTP proxy <!-- 4816339  -->
在 Android Enterprise 裝置上，您可以設定全域 HTTP Proxy 以符合組織的 web 流覽標準（**裝置**設定  > **設定檔** > **建立設定檔** > **Android Enterprise** for平臺 >**裝置擁有者 >** 配置檔案類型 > 連線**能力**）的裝置限制。 一旦設定之後，所有 HTTP 流量都會使用此 proxy。

適用於：
- Android Enterprise 裝置擁有者

### <a name="new-device-firmware-configuration-interface-profile-for-windows-10-and-later-devices----2266073----"></a>適用于 Windows 10 和更新版本裝置的新裝置固件設定介面設定檔 <!-- 2266073  -->
在 Windows 10 和更新版本上，您可以建立裝置設定檔來控制設定和功能（**裝置**設定  > **設定檔** > **建立設定檔** > **Windows 10 和更新版本**的平臺）。 將會有新的裝置固件設定介面配置檔案類型，可讓 Intune 管理 UEFI （BIOS）設定。

若要查看您可以設定之所有目前設定的總覽，請參閱[在 Microsoft Intune 中使用裝置設定檔套用裝置上的功能和設定](../configuration/device-profiles.md)。

適用於：
- 選取裝置上的 Windows 10 RS5 （1809）和更新版本

### <a name="pkcs-certificates-for-macos-----1333650------------------"></a>MacOS 的 PKCS 憑證  <!-- 1333650                -->
我們將在執行 macOS 的裝置上新增 PKCS 憑證的完整支援。 使用者將能夠使用 [自訂主旨] 和 [主體替代名稱] 欄位來部署使用者和裝置憑證。 我們也會有新的 [允許所有應用程式存取] 設定，其啟用方式為所有相關聯的應用程式授與私密金鑰的存取權。 如需此設定的詳細資訊，請造訪下列 Apple 檔： https://developer.apple.com/business/documentation/Configuration-Profile-Reference.pdf 。

###   <a name="derived-credentials-to-provision-mobile-devices-with-certificates----------1736036-1736037-1772050--------"></a>用來布建具有憑證之行動裝置的衍生認證      <!--  1736036, 1736037, 1772050      --> 
我們將新增對衍生認證的支援，以支援將憑證部署至裝置的*美國國家標準與技術局（NIST） 800-157*標準。  衍生的認證依賴個人身分識別驗證（PIV）或一般存取卡（CAC）卡（例如智慧卡）。 使用者在電腦上使用其智慧卡進行驗證，然後在衍生的認證提供者所需的程式之後，針對其受管理的裝置提交憑證要求。   

使用衍生認證來取得憑證的程式與使用 SCEP 或 PKCS 憑證設定檔不同，但最終結果是相同–具有驗證憑證的行動裝置，可用於應用程式驗證、VPN、Wi-fi 或電子郵件資料.   

如需詳細資訊，請參閱 www.nccoe.nist.gov 的[衍生 PIV 認證](https://www.nccoe.nist.gov/projects/building-blocks/piv-credentials)。

衍生認證的初始版本將支援 iOS 上的 Entrust Datacard、調解和 DISA Purebred。 較新的版本將支援其他平臺和衍生認證提供者。   

<!-- ***********************************************-->
## <a name="device-enrollment"></a>裝置註冊

### <a name="specify-which-android-device-operating-system-versions-enroll-with-work-profile-or-device-administrator-enrollment----4350697---"></a>指定向工作設定檔或裝置系統管理員註冊註冊的 Android 裝置作業系統版本 <!-- 4350697 -->
使用 Intune 裝置類型限制時，您將能夠使用裝置的 OS 版本來指定哪些使用者裝置將使用 Android Enterprise 工作設定檔註冊或 Android 裝置系統管理員註冊。 若要這麼做，請移至**Intune** > **裝置註冊** > **註冊限制** > **建立限制** > **裝置類型限制** > **平臺設定**。

### <a name="edit-device-name-value-for-autopilot-devices----4816775---"></a>編輯 Autopilot 裝置的裝置名稱值 <!-- 4816775 -->
您將能夠編輯 Azure AD 已加入 Autopilot 裝置的裝置名稱值。 若要這麼做，請移至**Intune** > **裝置註冊** > **Windows 註冊** > **windows Autopilot** > **裝置**> 選擇裝置 > 變更右窗格中的 裝置名稱 值 >**儲存**.

### <a name="for-ios-devices-customize-the-enrollment-process-privacy-screen-of-the-company-portal----4394993----"></a>針對 iOS 裝置，請自訂公司入口網站的 [註冊程序隱私權] 畫面 <!-- 4394993  -->
使用 Markdown，您將能夠自訂使用者在 iOS 註冊期間看到的公司入口網站隱私權畫面。 具體來說，您可以自訂組織無法在裝置上查看或執行的操作清單。

<!-- ***********************************************-->
## <a name="device-management"></a>裝置管理


### <a name="edit-group-tag-value-for-autopilot-devices---4816775---"></a>編輯 Autopilot 裝置的群組標記值<!-- 4816775 -->
您將能夠編輯 Autopilot 裝置的群組標記值。 若要這麼做，請移至**Intune** > **裝置註冊** > **Windows 註冊** > **windows Autopilot** > **裝置**> 選擇裝置 > 變更右窗格中的群組標記值 >**儲存**.

### <a name="ui-update-for-creating-and-editing-windows-10-update-rings-----4099089------------"></a>建立和編輯 Windows 10 更新通道的 UI 更新  <!-- 4099089          -->   
我們將推出適用于 Intune 的 Windows 10 更新通道的已更新建立和編輯 UI 體驗。  UI 的變更將包含：  
- 使用在一個分頁中壓縮的 wizard 樣式格式，來簡化現有的體驗。 此 UI 更新將會脫離分頁激增，需要 IT 專業人員向下切入深度的 blade 旅程。   
- 修訂 [建立流程] 以包含指派。  
- 在建立新的更新通道之前，以及在編輯屬性時，加入屬性時所設定之所有專案的摘要頁面。 編輯時，摘要只會顯示在目前編輯的一個屬性類別內設定的項目清單。

### <a name="ui-update-for-creating-and-editing-ios-software-updates-----4099090----------"></a>用於建立和編輯 iOS 軟體更新的 UI 更新  <!-- 4099090        -->   
我們將會推出適用于 Intune 的 iOS 軟體更新的已更新建立和編輯 UI 體驗。 UI 的變更將包含：
- 使用在一個分頁中壓縮的 wizard 樣式格式，來簡化現有的體驗。 此 UI 更新將會脫離分頁激增，需要 IT 專業人員向下切入深度的 blade 旅程。  
- IOS 軟體更新原則建立流程將更新為包含指派 
- 在建立新的原則和編輯屬性時，iOS 軟體更新原則會包含在流覽屬性時所設定之所有專案的摘要頁面。 編輯時，摘要只會顯示在目前編輯的一個屬性類別內設定的項目清單。

### <a name="target-macos-user-groups-to-require-jamf-management----4061739---"></a>目標 macOS 使用者群組需要 Jamf 管理 <!-- 4061739 -->
您將能夠以特定使用者群組為目標，要求其 macOS 裝置必須由 Jamf 管理。 此目標可讓您將 Jamf 合規性整合套用至 macOS 裝置的子集，而其他裝置則會繼續由 Intune 管理。 它也可讓您將使用者的裝置從一個 MDM 逐漸遷移到另一個。

### <a name="new-restrictions-for-renaming-windows-devices----3478938---"></a>重新命名 Windows 裝置的新限制 <!-- 3478938 -->
裝置名稱將必須遵循下列規則：
- 15個字元或更少（必須小於或等於63個位元組，不包括尾端的 Null）
- 不是 Null 或空字串
- 允許的 ASCII：字母（a-z、a-z）、數位（0-9）和連字號
- 允許的 Unicode：字元 > = 0x80，必須是有效的 UTF8，必須是 IDN-可映射（RtlIdnToNameprepUnicode 成功; 請參閱 RFC 3492）
- 名稱不得只包含數位，或以數位開頭
- 名稱中沒有空格
- 不允許的字元： {|} ~ [\] ^ '：;< = >？ &AMP; @！ " # $ % ` ( ) + / , . _ *)

### <a name="deploy-software-updates-to-macos-devices----3194876---"></a>將軟體更新部署到 macOS 裝置 <!-- 3194876 -->
您將能夠將軟體更新部署到 macOS 裝置群組。 這項功能包括重要、固件、設定檔及其他更新。 您將能夠在下一次裝置簽入時傳送更新，或選取每週排程，將更新部署到您設定的時間或時段內。 當您想要更新標準工作時間以外的裝置，或當您的技術服務人員已滿時，這項功能會有説明。 您也會取得已部署更新之所有 macOS 裝置的詳細報告。 您可以根據每個裝置深入探索報表，以查看特定更新的狀態。

<!-- ***********************************************-->
## <a name="monitor-and-troubleshoot"></a>監視及疑難排解

### <a name="new-android-report-on-devices-overview-page----2984353----"></a>裝置上的新 Android 報表總覽頁面 <!-- 2984353  -->
我們會將新的報告新增至 [裝置總覽] 頁面，其中會顯示已在每個裝置管理解決方案中註冊多少 Android 裝置。 此圖表會顯示工作設定檔、完全受控、專用和裝置系統管理員註冊的裝置計數。 若要查看報告，請選擇 [ **Intune**] [ >  部**裝置** **] [ > ]** 。

### <a name="windows-autopilot-deployment-reports----3856172----"></a>Windows Autopilot 部署報告 <!-- 3856172  -->
新的報表會詳細說明透過 Windows Autopilot 部署的每個裝置。 此資料會在部署後的30天內上市。 若要查看報告，請移至**Intune** > **裝置註冊** > **監視器** > **Autopilot 部署**。

### <a name="updated-support-experience-------5012398------"></a>更新的支援體驗   <!--  5012398    -->
在持續改進的過程中，我們將會更新 Intune 的主控台內支援體驗。  我們將改善主控台內搜尋和常見問題的意見反應，並簡化工作流程以聯絡支援人員。     

<!-- ***********************************************-->
<!--## Security-->


<!-- ***********************************************-->
## <a name="notices"></a>通知

[!INCLUDE [Intune notices](../includes/intune-notices.md)]

## <a name="see-also"></a>請參閱
如需近期發展的詳細資料，請參閱 [Microsoft Intune 的新功能](whats-new.md)。





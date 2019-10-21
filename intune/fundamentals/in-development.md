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
ms.subservice: fundamentals
ms.assetid: 25b3c26e-cf4e-4152-8306-bf4be4af2ad1
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: ea5fae72f6e2057ef0b03a7bd295085ed1ac3bbd
ms.sourcegitcommit: 5807f4db4a45a093ce2fd6cb0c480bec384ec1ff
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72601529"
---
# <a name="in-development-for-microsoft-intune---october-2019"></a>Microsoft Intune 正在開發的項目 - 2019 年 10 月

為了協助您整備及規劃，此頁面會列出正在開發，但尚未發行的 Intune UI 更新及功能。 除了此頁面上的資訊：

- 若我們預期您將需要在變更前先行採取動作，我們會在 Office 訊息中心發佈輔助性貼文。
- 當功能進入生產環境時，不論是預覽或正式推出，功能描述都會從這個頁面移至[新](whats-new.md)功能。
- 此頁面和[新增功能](whats-new.md)頁面會定期更新。 請回來查看其他更新。
- 請參閱 [Microsoft 365 藍圖](https://www.microsoft.com/microsoft-365/roadmap?rtc=2&filters=EMS)以取得策略性交付與時間表。

> [!NOTE]
> 此頁面會反映我們在未來版本中目前對 Intune 功能的期望。 日期和個別功能可能會變更。 此頁面不會描述開發中的所有功能。

**RSS 摘要**：將下列 URL 複製並貼上至您的摘要讀取器中，以了解此頁面何時更新：`https://docs.microsoft.com/api/search/rss?search=%22in+development+-+microsoft+intune%22&locale=en-us`

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

### <a name="apply-dark-mode-in-ios-company-portal----4911422----"></a>在 iOS 公司入口網站中套用深色模式 <!-- 4911422  -->
已規劃 iOS 公司入口網站的深色模式。 您將能夠下載公司應用程式、管理您的裝置，並在您選擇的色彩配置中取得 IT 支援。 如需有關 iOS 公司入口網站的詳細資訊，請參閱[如何設定 Microsoft Intune 公司入口網站應用程式](../apps/company-portal-app.md)。

### <a name="run-win32-apps-on-windows-10-s-mode-devices----3747604----"></a>在 Windows 10 S 模式的裝置上執行 Win32 應用程式 <!-- 3747604  --> 
您將能夠在以 Windows 10 S 模式管理的裝置上安裝和執行 Win32 應用程式。 使用 Windows Defender 應用程式控制（WDAC） PowerShell 工具，為 S 模式建立一或多個補充原則。 使用 Device Guard 簽署入口網站來簽署補充原則。 然後透過 Intune 上傳和散發原則。 

在 Intune 中，您可以藉由選取 [**用戶端應用程式**]  > **Windows 10 S 補充原則**來找到這項功能。 

### <a name="set-app-availability-based-on-a-date-and-time----3510685----"></a>根據日期和時間設定應用程式可用性 <!-- 3510685  -->
身為系統管理員，您將能夠設定必要應用程式的開始時間和期限。 在開始時，Intune 管理延伸模組會下載應用程式內容並加以快取。 應用程式將會在期限時間安裝。 針對可用的應用程式，開始時間將會指示應用程式何時會顯示在公司入口網站中。 

若要根據日期和時間設定應用程式可用性：

1. 在 Intune 中，選取 [用戶端應用程式]   > [應用程式]  。 
1. 選取清單中的應用程式，或選取 [新增] 來加入**一個。** 
1. 從 [應用程式] 分頁，選取 [**指派**]  >  [**新增群組**]。 
1. 將 [**指派類型**] 設定為 [**必要**]，然後選取 [**包含的群組**]。 
1. 將 [**讓所有使用者都需要此應用程式**] 設定為 **[是]** 。 
1. 選取 [**編輯**] 以修改 [**使用者體驗**] 選項。 
1. 在 [**終端使用者體驗**] 分頁上，視需要設定 [**軟體可用時間**]。 

如需詳細資訊，請參閱[將應用程式新增至 Microsoft Intune](../apps/apps-add.md)。

### <a name="require-win32-apps-to-restart----3136567----"></a>需要 Win32 應用程式重新開機 <!-- 3136567  -->
安裝成功之後，您將能夠要求 Win32 應用程式重新開機。 您可以選擇重新開機前的時間量（寬限期）。

### <a name="display-notifications-for-the-company-portal-app-on-windows----1808082----"></a>在 Windows 上顯示公司入口網站應用程式的通知 <!-- 1808082  -->
我們會更新 Windows 裝置上的公司入口網站應用程式，以向使用者顯示快顯通知，即使應用程式關閉也是一樣。 只有在安裝狀態為 [已完成] 或 [失敗] 時，更新才會顯示可用應用程式的通知。 公司入口網站應用程式不會顯示必要應用程式的通知。

### <a name="display-installation-status-messages-for-the-company-portal-app----2514416----"></a>顯示公司入口網站應用程式的安裝狀態訊息 <!-- 2514416  -->
公司入口網站應用程式會向終端使用者顯示額外的應用程式安裝狀態訊息。 下列條件將適用于新的 Win32 相依性功能：
- 應用程式無法啟動。 不符合系統管理員所定義的相依性。
- 已成功安裝應用程式，但需要重新開機。
- 應用程式正在進行安裝，但需要重新開機才能繼續。

### <a name="assign-the-microsoft-edge-beta-for-macos----4678761----"></a>指派適用于 macOS 的 Microsoft Edge Beta <!-- 4678761  -->
您將能夠為 macOS 裝置新增並指派最新版本的 Microsoft Edge Beta 至 Intune。 

指派適用于 macOS 裝置的 Microsoft Edge Beta：
1. 在 Intune 中，選取 **用戶端應用程式**  > **應用**程式  > **新增應用程式** > **Microsoft Edge-macOS**。 
1. 將 Microsoft Edge Beta 指派給預定的群組。 Microsoft 自動更新（MAU）可讓 Microsoft Edge 保持在最新狀態。 
 
如需 Microsoft Edge 的詳細資訊，請參閱[使用 Microsoft edge 搭配 Microsoft Intune 來管理 web 存取](../apps/manage-microsoft-edge.md)。

### <a name="configure-app-notification-content-for-organization-accounts----2576686---"></a>設定組織帳戶的代理程式更新內容 <!-- 2576686 -->
Android 和 iOS 裝置上的 Intune 應用程式可讓您控制組織帳戶的代理程式更新內容。 這項功能將需要應用程式的支援，而且可能無法供所有啟用應用程式的應用程式使用。 如需有關應用程式的詳細資訊，請參閱[什麼是應用程式保護原則？](../apps/app-protection-policy.md)


<!-- ***********************************************-->
## <a name="device-configuration"></a>裝置設定

### <a name="new-device-firmware-configuration-interface-profile-for-devices-that-run-windows-10-and-later----2266073----"></a>執行 Windows 10 和更新版本之裝置的新裝置固件設定介面設定檔 <!-- 2266073  -->
在 Windows 10 和更新版本上，您可以建立裝置設定檔來控制設定和功能： 

1. 選取 [裝置設定]   > [設定檔]   > [建立設定檔]  。
1. 針對 [平台]，請選取 [Windows 10 及更新版本]  。 
 
新的裝置固件設定介面配置檔案類型將允許 Intune 管理 UEFI （BIOS）設定。

如需您可以設定之目前設定的相關資訊，請參閱[在 Microsoft Intune 中使用裝置設定檔，在裝置上套用功能和設定](../configuration/device-profiles.md)。

這項功能適用于選取的裝置上的 Windows 10 RS5 （1809）和更新版本。
 

<!-- ***********************************************-->
## <a name="device-enrollment"></a>裝置註冊

### <a name="for-ios-devices-customize-the-enrollment-privacy-window-of-company-portal----4394993----"></a>若是 iOS 裝置，請自訂公司入口網站的 [註冊隱私權] 視窗 <!-- 4394993  -->
使用 Markdown，您將能夠自訂終端使用者在 iOS 註冊期間看到的公司入口網站隱私權視窗。 具體來說，您可以自訂組織無法在裝置上查看或執行的操作清單。

<!-- ***********************************************-->
## <a name="device-management"></a>裝置管理


### <a name="edit-the-group-tag-value-for-autopilot-devices---4816775---"></a>編輯 Autopilot 裝置的群組標記值<!-- 4816775 -->
您將能夠編輯 Autopilot 裝置的**群組標記**值：

1. 選取  **Intune**  > **裝置註冊**  > **windows 註冊** > **windows Autopilot**  > **裝置**。
1. 選擇裝置。
1. 在右側窗格中，變更 [群組]**標記**值。
1. 選取 [儲存]  。

### <a name="target-macos-user-groups-to-require-jamf-management----4061739---"></a>目標 macOS 使用者群組需要 Jamf 管理 <!-- 4061739 -->
您將能夠以特定使用者群組為目標，要求其 macOS 裝置受 Jamf 管理。 此目標可讓您將 Jamf 合規性整合套用至 macOS 裝置的子集，而其他裝置則會繼續由 Intune 管理。 目標也可讓您將使用者的裝置從一個行動裝置管理（MDM）系統逐漸遷移到另一個。

### <a name="deploy-software-updates-to-macos-devices----3194876---"></a>將軟體更新部署到 macOS 裝置 <!-- 3194876 -->
您將能夠將軟體更新部署到 macOS 裝置群組。 這項功能包括重要、固件、設定檔及其他更新。 您可以在下一次裝置簽入時傳送更新。 或者，您可以選取每週排程，將更新部署在您設定的期間或外。 

當您想要在技術支援人員全公司時，于標準工作時間或以外的時間更新裝置時，這項功能會有説明。 您也會取得已部署更新之所有 macOS 裝置的詳細報告。 您可以依裝置向內切入報表，以查看特定更新的狀態。

<!-- ***********************************************-->
## <a name="monitoring-and-troubleshooting"></a>監視和疑難排解

### <a name="android-report-on-the-devices-overview-page----2984353----"></a>裝置 [總覽] 頁面上的 Android 報表 <!-- 2984353  -->
我們會將新的報告新增至 [**裝置] [總覽**] 頁面。 此報告會顯示每個裝置管理解決方案中已註冊的 Android 裝置數。 此圖表會顯示工作設定檔、完全受控、專用及裝置系統管理員註冊的裝置計數。 

若要查看報告，請選擇 [ **Intune**] [ >  部**裝置** **] [ > ]** 。

### <a name="updated-support-experience-------5012398------"></a>更新的支援體驗   <!--  5012398    -->
在持續改進的過程中，我們將更新 Intune 的主控台內支援體驗。  我們將改善主控台內搜尋和常見問題的意見反應，我們將簡化工作流程以聯絡支援人員。     

<!-- ***********************************************-->
<!--## Security-->


<!-- ***********************************************-->
## <a name="notices"></a>通知

[!INCLUDE [Intune notices](../includes/intune-notices.md)]

## <a name="see-also"></a>請參閱
如需近期發展的詳細資料，請參閱 [Microsoft Intune 的新功能](whats-new.md)。

---
title: 開發中 - Microsoft Intune
titleSuffix: ''
description: 正在開發的 Microsoft Intune 功能
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/28/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.assetid: 25b3c26e-cf4e-4152-8306-bf4be4af2ad1
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3720b0b9a67f0c3462993feef4162ef35f7f3f92
ms.sourcegitcommit: d1b36501186e867355843ddd67c795ade800b76a
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2019
ms.locfileid: "73182933"
---
# <a name="in-development-for-microsoft-intune---november-2019"></a>Microsoft Intune 正在開發的項目 - 2019 年 11 月

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

### <a name="smime-support-for-microsoft-outlook-mobile----2669398----"></a>Microsoft Outlook Mobile 的 S/MIME 支援 <!-- 2669398  -->
Intune 將支援提供可與 iOS 和 Android 上的 Outlook Mobile 搭配使用的 S/MIME 簽署和加密憑證。 如需相關資訊，請參閱[iOS 裝置的電子郵件設定](~/configuration/email-settings-ios.md)和[Android 裝置的電子郵件設定](~/configuration/email-settings-android.md)。

### <a name="custom-settings-support-for-macos-applications----4736278----"></a>MacOS 應用程式的自訂設定支援 <!-- 4736278  -->
Intune 將支援自訂設定，可讓您將特定的索引鍵和值新增至現有的喜好設定屬性清單（. plist）檔案，以設定 macOS 應用程式和裝置。 並非所有應用程式都支援受控喜好設定，而在某些情況下，只能管理特定的設定。 這些設定只會透過裝置通道進行部署。 您應該只上傳以裝置通道設定為目標的屬性清單檔案或 .xml 檔案。

### <a name="assignment-type-value-in-windows-company-portal----5459950----"></a>Windows 公司入口網站中的指派類型值 <!-- 5459950  -->
Windows 公司入口網站應用程式的 [**已安裝的應用程式**] 頁面將會更新。 [**已安裝的應用程式**] 頁面的 [**指派類型**] 欄已更新為 [您的組織所需]。 可能的值為 **[是] 或 [** **否**]，以指定必要和可用的應用程式。 這項變更是為了回應某些使用者的混淆而進行。 如需 Windows 公司入口網站的詳細資訊，請參閱[如何設定 Microsoft Intune 公司入口網站應用程式](~/apps/company-portal-app.md)。

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

### <a name="configure-app-notification-content-for-organization-accounts----2576686---"></a>設定組織帳戶的代理程式更新內容 <!-- 2576686 -->
Android 和 iOS 裝置上的 Intune 應用程式可讓您控制組織帳戶的代理程式更新內容。 這項功能將需要應用程式的支援，而且可能無法供所有啟用應用程式的應用程式使用。 如需有關應用程式的詳細資訊，請參閱[什麼是應用程式保護原則？](../apps/app-protection-policy.md)


<!-- ***********************************************-->
## <a name="device-configuration"></a>裝置設定

### <a name="use-pkcs-certificates-with-wi-fi-profiles-on-windows-10-and-later-devices----3246388----"></a>在 Windows 10 和更新版本的裝置上搭配使用 PKCS 憑證與 Wi-fi 設定檔 <!-- 3246388  -->
目前，您可以使用 SCEP 憑證來驗證 Windows Wi-fi 設定檔（**裝置**設定 > **設定檔** > **建立設定檔** > **Windows 10 和更新版本**（適用于平臺 > 的**wi-fi）** 配置檔案類型 > **Enterprise** > **EAP 類型**）。 您將可以搭配 Windows Wi-fi 設定檔使用 PKCS 憑證。 這項功能可讓使用者使用您租使用者中新的或現有的 PKCS 憑證設定檔來驗證 Wi-fi 設定檔。 

如需有關 Wi-fi 設定檔的詳細資訊，請參閱[在 Intune 中新增適用于 Windows 10 和更新版本裝置的 wi-fi 設定](../configuration/wi-fi-settings-windows.md)。

適用於：
- Windows 10 及更新版本

### <a name="new-exchangeactivesync-settings-when-creating-an-email-device-configuration-profile-on-ios-devices----4892824----"></a>在 iOS 裝置上建立電子郵件裝置設定檔時的新 ExchangeActiveSync 設定 <!-- 4892824  --> 
在 iOS/iPadOS 裝置上，您可以在裝置設定檔中設定電子郵件連線能力（**裝置**設定 > **配置**檔 > 為平臺 >**電子郵件** **建立設定檔** > **iOS/iPadOS**適用于配置檔案類型）。 

將會提供新的 ExchangeActiveSync 設定，包括：
- 選擇要同步（或封鎖同步處理）的服務，例如電子郵件、行事曆和連絡人。
- 允許（或封鎖）使用者在其裝置上變更這些服務的同步設定。 

若要查看目前的設定，請移至[Intune 中 iOS 裝置的電子郵件設定檔設定](../configuration/email-settings-ios.md)。

適用於：
- iOS 13.0 與更新版本
- iPadOS 13.0 和更新版本

### <a name="prevent-users-from-adding-personal-google-accounts-to-android-enterprise-device-owner-and-dedicated-devices----5353228----"></a>防止使用者將個人 Google 帳戶新增至 Android Enterprise 裝置擁有者和專用裝置 <!-- 5353228  -->
您將能夠防止使用者在 Android 企業裝置擁有者和專用裝置上建立個人 Google 帳戶（**裝置**設定 > **設定檔** > **建立設定檔** > **Android Enterprise** **僅限平臺 > 裝置擁有者 >** 配置檔案類型 >**使用者和帳戶設定**）的裝置限制。

若要查看您目前可以設定的設定，請參閱[使用 Intune 來允許或限制功能的 Android Enterprise 裝置設定](../configuration/device-restrictions-android-for-work.md)。

適用於：
- Android Enterprise 裝置擁有者
- Android Enterprise 專用裝置

### <a name="server-side-logging-for-siri-commands-setting-is-removed-in-ios-device-restrictions-profile----5468501----"></a>IOS 裝置限制設定檔中已移除 Siri 命令的伺服器端記錄設定 <!-- 5468501  -->
在 iOS 裝置上，您可以建立裝置限制設定檔，以設定 Siri 命令的伺服器端記錄（**裝置**設定 > **配置**檔 > 為平臺**建立設定檔** > **iOS/iPadOS**> 配置檔案類型 >**內建應用程式**）的**裝置限制**。 將會移除**Siri 命令的伺服器端記錄**設定。

此設定將會從 Intune 管理主控台移除。 即使已設定此設定的現有原則會繼續顯示設定，此設定對裝置沒有任何作用。 如果您想要從現有的原則中移除設定，請移至原則、進行次要編輯、儲存，然後將更新原則。

若要查看您可以設定的設定，請參閱[使用 Intune 透過 iOS 與 iPadOS 裝置設定來允許或限制功能](../configuration/device-restrictions-ios.md)。

適用於：
- iOS


<!-- ***********************************************-->
<!--## Device enrollment-->

<!-- ***********************************************-->
## <a name="device-management"></a>裝置管理

### <a name="edit-device-name-value-for-autopilot-devices---2640074----"></a>編輯 Autopilot 裝置的裝置名稱值<!-- 2640074  -->
您將能夠編輯 Azure AD 已加入 Autopilot 裝置的裝置名稱值。 若要這麼做，請移至**Intune** > **裝置註冊** > **windows 註冊** > **windows Autopilot** > **裝置**> 選擇裝置 > 變更右窗格中的 **裝置名稱** 值>**儲存**。


### <a name="edit-the-group-tag-value-for-autopilot-devices---4816775---"></a>編輯 Autopilot 裝置的群組標記值<!-- 4816775 -->
您將能夠編輯 Autopilot 裝置的**群組標記**值：

1. 選取  **Intune**  > **裝置註冊**  > **windows 註冊** > **windows Autopilot**  > **裝置**。
1. 選擇裝置。
1. 在右側窗格中，變更 [群組]**標記**值。
1. 選取 [儲存]  。

### <a name="target-macos-user-groups-to-require-jamf-management----4061739---"></a>目標 macOS 使用者群組需要 Jamf 管理 <!-- 4061739 -->
您將能夠以特定使用者群組為目標，要求其 macOS 裝置受 Jamf 管理。 此目標可讓您將 Jamf 合規性整合套用至 macOS 裝置的子集，而其他裝置則會繼續由 Intune 管理。 目標也可讓您將使用者的裝置從一個行動裝置管理（MDM）系統逐漸遷移到另一個。

<!-- ***********************************************-->
## <a name="intune-apps"></a>Intune 應用程式

### <a name="improved-macos-enrollment-experience-in-company-portal----5074349----"></a>改善公司入口網站中的 macOS 註冊體驗 <!-- 5074349  -->
MacOS 註冊體驗的公司入口網站將會有更簡單的註冊程式，以更密切地配合 iOS 註冊體驗的公司入口網站。 裝置使用者會看到：  

* 輕巧的使用者介面。  
* 改良的註冊檢查清單。  
* 更清楚的指示，說明如何註冊其裝置。  
* 改良的疑難排解選項。  

### <a name="improved-checklist-design-in-company-portal-app-for-android---5550857----"></a>已改善 Android 公司入口網站應用程式中的檢查清單設計<!-- 5550857  -->
適用于 Android 的公司入口網站應用程式中的安裝檢查清單，將會以輕量設計和新圖示進行更新。 這些變更會與適用于 iOS 之公司入口網站應用程式的最新更新一致。

<!-- ***********************************************-->
## <a name="monitoring-and-troubleshooting"></a>監視和疑難排解

### <a name="updated-support-experience-------5012398------"></a>更新的支援體驗   <!--  5012398    -->
在持續改進的過程中，我們將更新 Intune 的主控台內支援體驗。  我們將改善主控台內搜尋和常見問題的意見反應，我們將簡化工作流程以聯絡支援人員。     

<!-- ***********************************************-->
## <a name="role-based-access-control"></a>以角色為基礎的存取控制

### <a name="duplicate-custom-or-built-in-roles----1081938---"></a>重複的自訂或內建角色 <!-- 1081938 -->
您將能夠複製內建和自訂角色。 若要這麼做，請移至**Intune** > **角色** > **所有角色**> 挑選清單中的角色 >**重複**。 請務必輸入唯一的新名稱。

<!-- ***********************************************-->

## <a name="security"></a>安全性

### <a name="bitlocker-key-rotation--------2564951--------"></a>BitLocker 金鑰輪替     <!-- 2564951      -->
您將能夠使用 Intune 來輪替執行 Windows 1909 版或更新版本之受管理裝置的 BitLocker 修復金鑰。 

<!-- ***********************************************-->
## <a name="notices"></a>通知

[!INCLUDE [Intune notices](../includes/intune-notices.md)]

## <a name="see-also"></a>請參閱
如需近期發展的詳細資料，請參閱 [Microsoft Intune 的新功能](whats-new.md)。

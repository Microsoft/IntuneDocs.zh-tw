---
title: 開發中 - Microsoft Intune
titleSuffix: ''
description: 正在開發的 Microsoft Intune 功能
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/03/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.assetid: 25b3c26e-cf4e-4152-8306-bf4be4af2ad1
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: e099537bce6327e9a8991bc42f406e4abd3dfd2e
ms.sourcegitcommit: 6608dc70d01376e0cd90aa620a2fe01337f6a2f1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2020
ms.locfileid: "78260226"
---
# <a name="in-development-for-microsoft-intune---march-2020"></a>Microsoft Intune 正在開發的項目 - 2020 年 3 月

為了協助您整備及規劃，此頁面會列出正在開發，但尚未發行的 Intune UI 更新及功能。 除了此頁面上的資訊之外： 

- 若我們預期您將需要在變更前先行採取動作，我們會在 Office 訊息中心發佈輔助性貼文。
- 當功能進入生產環境時，無論是作為預覽功能還是正式推出，功能描述都會從此頁面移除，並移到[新功能](whats-new.md)頁面。
- 此頁面和[新增功能](whats-new.md)頁面會定期更新。 請回來查看其他更新。
- 請參閱 [Microsoft 365 藍圖](https://www.microsoft.com/microsoft-365/roadmap?rtc=2&filters=EMS)以取得策略性交付與時間表。

> [!NOTE]
> 此頁面反映我們目前對未來版本中 Intune 功能的預期。 日期和個別功能可能會變更。 此頁面不會描述開發中的所有功能。

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

### <a name="retarget-web-clips-to-microsoft-edge-on-iosipados-devices---5455276---"></a>在 iOS/iPadOS 裝置上將 Web 剪輯的目標重新設定為 Microsoft Edge<!-- 5455276 -->
Web 剪輯 (在 iOS/iPadOS 裝置上會作為釘選的 Web 應用程式) 必須更新。 如果需要在受保護的瀏覽器中開啟，新部署的 Web 剪輯會在 Microsoft Edge 中開啟，而不是在 Intune Managed Browser 中開啟。 您必須為預先存在的 Web 剪輯重定目標，以確保其在 Microsoft Edge 中開啟，而不是在 Managed Browser 中開啟。

### <a name="macos-and-ios-company-portal-updates---5779439-5780234----"></a>macOS 與 iOS 公司入口網站更新<!-- 5779439, 5780234  -->
即將更新 macOS 與 iOS 公司入口網站的 [設定檔] 窗格，往後將會包含 [登出] 按鈕。 此外，本次更新也包含 macOS 公司入口網站中 [設定檔] 窗格的 UI 功能改善。 如需公司入口網站的詳細資訊，請參閱[如何設定 Microsoft Intune 公司入口網站應用程式](~/apps/company-portal-app.md)。

### <a name="updates-to-branding-and-customization-pane---5236032---"></a>更新 [商標和自訂] 窗格<!-- 5236032 -->
我們將更新目前名為 [商標和自訂] 的 Intune 窗格，其改善的功能包括：

- 將該窗格重新命名為 [自訂]  。
- 改善設定的配置與設計。
- 改善設定的文字與工具提示。

若要在 Intune 中尋找這些設定，請巡覽至 [Microsoft 端點管理員系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)，然後選取 [租用戶系統管理]   > [自訂]  。 如需現有自訂的資訊，請參閱[如何設定 Microsoft Intune 公司入口網站應用程式](~/apps/company-portal-app.md)。

### <a name="configure-the-ios-microsoft-azure-ad-sso-app-extension---567534----"></a>設定 iOS Microsoft Azure AD SSO 應用程式延伸模組<!-- 567534  -->
Microsoft Azure AD 小組正在開發重新導向的單一登入 (SSO) 應用程式延伸模組，以讓 iOS 與 iPadOS 13.0 + 的使用者能夠使用單一登入來順暢地存取 Microsoft 應用程式和網站。 在 AAD SSO 應用程式延伸模組發行後，您只需要按幾下，就能在系統管理主控台的 [裝置功能]   > [單一登入應用程式延伸模組]  中，設定 SSO 延伸模組。 

如需 iOS SSO 應用程式延伸模組或如何設定裝置功能的詳細資訊，請參閱[單一登入應用程式延伸模組](~/configuration/device-features-configure.md#single-sign-on-app-extension)。

### <a name="company-portal-for-ios-to-support-landscape-mode--6048329----"></a>iOS 公司入口網站支援橫向模式<!--6048329  -->
使用者將可以自由選擇螢幕方向來註冊其裝置、尋找應用程式，以及取得 IT 支援。 除非使用者將螢幕鎖定在直向模式，否則應用程式會自動偵測並將螢幕調整為直向或橫向模式。 

### <a name="configure-if-enrollment-is-available-in-company-portal-for-android-and-ios---4260128-idready-idstaged---"></a>設定是否可在 Android 與 iOS 公司入口網站中註冊<!-- 4260128 idready idstaged -->
即將提供新的設定，可讓您設定在具有提示 (或沒有提示) 的情況下，讓使用者能夠在 Android 與 iOS 裝置的公司入口網站中註冊裝置，或不提供使用者註冊裝置。 若要在 Intune 中尋找這些設定，請巡覽至 [Microsoft 端點管理員系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)，然後選取 [租用戶系統管理]   > [自訂]   > [編輯]   > [裝置註冊]  。 如需現有公司入口網站自訂的詳細資訊，請參閱[如何設定 Microsoft Intune 公司入口網站應用程式](~/apps/company-portal-app.md)。

### <a name="improved-sign-in-experience-in-company-portal-for-android---6103997----"></a>改善了 Android 公司入口網站登入體驗<!-- 6103997  -->
我們將更新 Android 公司入口網站應用程式中數個登入畫面的版面配置，讓使用者獲得更加現代化且簡潔的體驗。

<!-- ***********************************************-->
## <a name="device-configuration"></a>裝置設定

### <a name="wired-network-device-configuration-profiles-for-macos-devices---3508686----"></a>適用於 macOS 裝置的有線網路裝置組態設定檔<!-- 3508686  -->
將會可以使用設定有線網路的 macOS 裝置設定檔 ([裝置設定]   > [設定檔]   > [建立設定檔]   > [macOS]  平台 > [有線網路]  設定檔類型)。 使用此功能來建立 802.1x 設定檔以管理有線網路，並將這些有線網路部署至您的 macOS 裝置。

適用於：
- macOS

### <a name="vpn-profiles-with-ikev2-vpn-connections-can-use-always-on-with-iosipados-devices----1947932----"></a>使用 IKEv2 VPN 連線的 VPN 設定檔可以搭配 iOS/iPadOS 裝置使用 Always On <!-- 1947932  -->
在 iOS/iPadOS 裝置上，您可以建立使用 IKEv2 連線的 VPN 設定檔 ([裝置設定]   > [設定檔]   > [建立設定檔]   > [iOS/iPadOS]  作為平台 > [VPN]  作為設定檔類型)。 在未來的更新中，您可以搭配 IKEv2 設定 Always-On。 設定之後，IKEv2 VPN 設定檔會自動連線，並保持連線 (或快速重新連線) 至 VPN。 即使在網路之間移動或將裝置重新開機，仍會保持連線。

在 iOS/iPadOS 上，Always-On VPN 僅限用於 IKEv2 設定檔。

若要查看您目前可以設定的 IKEv2 設定，請前往[在 Microsoft Intune 中於 iOS/iPadOS 裝置上新增 VPN 設定](../configuration/vpn-settings-ios.md#ikev2-settings)。

適用於：
- iOS

### <a name="improved-user-interface-experience-when-creating-configuration-profiles-on-iosipados-and-macos-devices---5569008-5569039-5569057-5569110-5569116-5569131-5569139-5569153-5859984----"></a>已改善在 iOS/iPadOS 和 macOS 裝置上建立設定檔時的使用者介面體驗<!-- 5569008-5569039-5569057-5569110-5569116-5569131-5569139-5569153-5859984  -->
當您建立 iOS/iPadOS 或 macOS 裝置的設定檔時，將會更新端點管理員系統管理中心中的體驗。 此變更會影響下列裝置設定檔 ([裝置]   > [設定檔]   > [建立設定檔]   > [iOS]  或 [macOS]  平台)：

- 自訂：iOS/iPadOS、macOS
- 裝置功能：iOS/iPadOS、macOS
- 裝置限制：iOS/iPadOS、macOS
- 端點保護：macOS
- 擴充功能：macOS
- 喜好設定檔案：macOS

### <a name="improved-user-interface-experience-when-creating-oemconfig-configuration-profiles-on-android-enterprise-devices---5568645-----"></a>已改善在 Android Enterprise 裝置上建立 OEMConfig 設定檔時的使用者介面體驗<!-- 5568645   -->
當您建立或編輯 Android Enterprise 裝置的 OEMConfig 設定檔時，端點管理系統管理中心的體驗已更新。 更新的體驗將會針對您已設定的項目提供簡短摘要。 此變更會影響 OEMConfig 裝置設定檔 ([裝置]   > [設定檔]   > [建立設定檔]   > [Android Enterprise]  平台 > [OEMConfig]  設定檔類型)。

本功能適用於：
- Android 企業 

### <a name="enterprise-app-trust-settings-modification-setting-will-be-removed-from-iosipados-device-restriction-profiles---6225131----"></a>[修改企業應用程式信任設定] 設定將從 iOS/iPadOS 裝置限制設定檔中移除<!-- 6225131  -->
在 iOS/iPadOS 裝置上，您可以建立裝置限制設定檔 ([裝置]   > [組態設定檔]   > [建立設定檔]   > 選取 [iOS/iPadOS]  作為平台 > 選取 [裝置限制]  作為設定檔類型)。 [修改企業應用程式信任設定]  設定將會由 Apple 移除，並因此從 Intune 移除。 如果您目前在設定檔中使用此設定，則不會有任何影響，且會保留在設定檔中，直到建立新的設定檔為止。 此設定也會從 Intune 的所有報告中移除。

適用於：
- iOS/iPadOS

若要查看您可以限制的設定，請前往[允許或限制功能的 iOS 和 iPadOS 裝置設定](../configuration/device-restrictions-ios.md)。

### <a name="device-configuration-profile-settings-and-values-will-be-updated-for-windows-platforms---4091122---"></a>即將更新 Windows 平台的裝置組態設定檔設定和值<!-- 4091122 -->
當您建立 Windows 平台的裝置組態設定檔時 ([裝置]   > [組態設定檔]   > [建立設定檔]  > 任意 [Windows]  平台選項)，部分設定和其值與 CSP 不相同，而可能造成混淆。 即將更新設定名稱和其值，以便更加清楚地表示。

適用於：

- Windows 10 和更新版本裝置組態設定檔
- Windows Holographic for Business 裝置組態設定檔
- Windows 8.1 裝置組態設定檔
- Windows Phone 8.1 裝置組態設定檔

### <a name="improved-user-interface-experience-when-creating-device-restrictions-profiles-on-android-and-android-enterprise-devices---5841361---"></a>改善了在 Android 與 Android 企業裝置上建立裝置限制設定檔時的使用者介面體驗<!-- 5841361 -->
當您建立 Android 或 Android 企業裝置的設定檔時，將能夠體驗更新的端點管理系統管理中心。 此變更會影響下列裝置組態設定檔 ([裝置]   > [組態設定檔]   > [建立設定檔]   > 選取 [Android 裝置管理員]  或 [Android 企業]  作為平台)：

- 裝置限制：Android 裝置管理員
- 裝置限制：Android Enterprise 裝置擁有者
- 裝置限制：Android Enterprise 工作設定檔

如需您可以設定之裝置限制的詳細資訊，請參閱 [Android 裝置系統管理員](../configuration/device-restrictions-android.md) 和 [Android 企業](../configuration/device-restrictions-android-for-work.md)。

### <a name="delete-bundles-and-bundle-arrays-in-oemconfig-device-configuration-profiles-on-android-enterprise-devices---5550355----"></a>在 Android 企業裝置的 OEMConfig 裝置組態設定檔中刪除套件組合與組合陣列<!-- 5550355  -->
在 Android 企業裝置上，您可以建立及更新 OEMConfig 設定檔。 使用者將能夠使用 Intune 中的 [設定設計工具]  來刪除套件組合與組合陣列。

如需 OEMConfig 設定檔的詳細資訊，請參閱[在 Microsoft Intune 中透過 OEMConfig 來使用和管理 Android Enterprise 裝置](../configuration/android-oem-configuration-overview.md)。

本功能適用於：
- Android 企業

### <a name="support-for-wpa-and-wpa2-in-ios-enterprise-wi-fi-profiles--6215273-----"></a>iOS 企業 Wi-Fi 設定檔中的 WPA 與 WPA2 支援<!--6215273   -->
我們將新增「安全性類型」  欄位至 [iOS 的企業 Wi-Fi 設定檔](../configuration/wi-fi-settings-ios.md) ([裝置]   > [組態設定檔]   > [建立設定檔]  ，然後選取 [iOS/iPadOS]  作為「平台」  ，並選取 [Wi-Fi]  作為「設定檔」  )。 此動作類似適用於 iOS 基本 Wi-Fi 設定檔的選項。 透過這項變更，您將可以建立新的設定檔，以指定 [WPA-Enterprise]  或 [WPA/WPA2-Enterprise]  的安全性類型，並為「EAP 類型」  指定選取項目。

### <a name="new-user-experience-for-certificate-email-vpn-and-wi-fi-profiles---5615208-----"></a>新的憑證、電子郵件、VPN 以及 Wi-Fi 設定檔使用者體驗<!-- 5615208   -->
我們將更新端點管理系統管理中心的[使用者體驗](../configuration/device-profile-create.md) ([裝置]   > [組態設定檔]   > [建立設定檔]  )，以便建立及修改下列設定檔類型。 新體驗將會與先前的設定相同，但具有類似使用精靈的體驗，且不太需要水平捲動。 您不需要修改現有設定也能使用新的體驗。
- 衍生認證
- 電子郵件
- PKCS 憑證
- PKCS 匯入憑證
- SCEP 憑證
- 信任的憑證
- VPN
- Wi-Fi

([裝置]   > [組態設定檔]   > [建立設定檔]  ，然後選取上述任何一個設定檔作為「設定檔類型」  )

### <a name="configure-the-microsoft-defender-atp-app-for-macos-----5520115----"></a>設定 macOS 的 Microsoft Defender ATP 應用程式  <!-- 5520115  -->
您即將可以針對以 macOS 作為 Endpoint Protection 裝置組態設定檔一部分執行的裝置，進行 Microsoft Defender ATP 應用程式的[設定](../protect/endpoint-protection-macos.md) ([裝置]   > [組態設定檔]   > [建立設定檔]  ，選取 [macOS]  作為「平台」  ，然後選取 [Endpoint Protection]  作為「設定檔類型」  )。 macOS 裝置設定將會具有八項設定。 

macOS 10.13 (High Sierra) 與更新版本支援 Defender ATP，而 [Microsoft Defender ATP](../apps/apps-advanced-threat-protection-macos.md) 應用程式必須在套用這些設定「之後」  部署到裝置。 在部署應用程式之前，您需要將這些設定傳送至裝置。 不支援 macOS 的 Beta 版。

### <a name="new-filevault-setting-for-macos-endpoint-protection-device-configuration-policy---5459801-----"></a>macOS Endpoint Protection 裝置設定原則的新 FileVault 設定<!-- 5459801   -->
我們將在 [macOS Endpoint Protection](../protect/endpoint-protection-macos.md) 範本內新增設定至 [FileVault] 類別：隱藏修復金鑰。 ([裝置]   > [組態設定檔]   > [建立設定檔]  ，選取 [macOS]  作為「平台」  ，然後選取 [Endpoint Protection]  作為「設定檔類型」  )。 此設定會在 FileVault 2 加密期間隱藏來自終端使用者的個人金鑰。 裝置使用者可以隨時從 iOS 公司入口網站應用程式，或從已加密 macOS 裝置的公司入口網站，查看其個人的修復金鑰。 若要查看個人修復金鑰，使用者可以前往 [裝置詳細資料]，然後按一下「取得修復金鑰」  。

此設定不適用於先前建立的原則。 您必須重新建立 FileVault 原則，才能進行並使用此設定。 

###  <a name="ui-update-when-configuring-compliance-policy----3961639----"></a>設定合規性政策時的 UI 更新 <!-- 3961639  -->
我們將更新 Microsoft 端點管理員中設定合規性政策的 UI ([裝置]   > [合規性政策]   > [原則]   > [建立原則]  )。 您將會看到新的使用者體驗，但仍提供您與先前相同的設定和詳細資料。 新體驗會遵循類似使用精靈的流程來建立合規性政策，並將包含新的頁面，以便您在其中為原則新增「指派」  ，以及「摘要」  頁面，您可以在建立原則前，於該頁面中檢閱設定。 

### <a name="configure-delivery-optimization-agent-when-downloading-win32-app-content---5410945----"></a>於下載 Win32 應用程式內容時設定傳遞最佳化代理程式<!-- 5410945  -->
您將能夠設定傳遞最佳化代理程式，以根據指派，在背景或前景模式下載 Win32 應用程式內容。 針對現有的 Win32 應用程式，內容會繼續以背景模式下載。 在 [Microsoft Endpoint Manager 系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)內，選取 [裝置]   > [組態設定檔]   > [建立設定檔]  。 選取 [Windows 10 及更新版本]  作為 [平台]  。 在 [設定檔類型]  中，選取 [傳遞最佳化]  。 如需傳遞最佳化的詳細資訊，請參閱 [Win32 應用程式管理 - 傳遞最佳化](~/apps/apps-win32-app-management.md#delivery-optimization)。


<!-- ***********************************************-->
<!--## Device enrollment-->

<!-- ***********************************************-->
## <a name="device-management"></a>裝置管理

### <a name="change-primary-user-for-windows-devices----3794742---"></a>變更 Windows 裝置的主要使用者 <!-- 3794742 -->
您將能夠變更 Windows 混合式和 Azure AD 加入裝置的主要使用者。 若要執行此操作，請前往 [Intune]   > [裝置]   > [所有裝置]  > 選擇裝置 > [屬性]   > [主要使用者]  。 

### <a name="new-android-report-on-android-devices-overview-page---5435435---"></a>[Android 裝置概觀] 頁面上的新 Android 報告<!-- 5435435 -->
我們將在 [Android 裝置概觀] 頁面中，新增報告至 Microsoft 端點管理員系統管理主控台，以顯示每個裝置管理解決方案中已註冊的 Android 裝置數量。 此圖表 (如同 Azure 主控台中已有的相同圖表) 會顯示工作設定檔、完全受控、專用，以及已註冊裝置系統管理員的裝置數量。 若要查看報告，請選擇 [裝置]   > [Android]   > [概觀]  。

### <a name="powershell-scripts-support-for-byod-devices---1862833----"></a>適用於 BYOD 裝置的 PowerShell 指令碼支援<!-- 1862833  -->
PowerShell 指令碼將支援在 Intune 中已註冊 Azure AD 的裝置。 如需 PowerShell 的詳細資訊，請參閱[在 Intune 的 Windows 10 裝置上使用 PowerShell 指令碼](~/apps/intune-management-extension.md)。 此功能不支援執行 Windows 10 家用版的裝置。

### <a name="additional-data-warehouse-device-inventory-properties---6125732----"></a>其他資料倉儲裝置庫存屬性<!-- 6125732  -->
其他裝置庫存屬性將可使用 Intune 資料倉儲取得。 下列屬性將會透過[裝置](~/developer/intune-data-warehouse-collections.md#devices)集合公開：
- 儲存體容量 
- 記憶體容量
- Office 365 版本
- 裝置型號

如需資料倉儲的詳細資訊，請參閱 [Microsoft Intune 資料倉儲 API](~/developer/reports-nav-intune-data-warehouse.md)。

### <a name="guide-users-from-android-device-administrator-management-to-work-profile-management--5857738--"></a>引導使用者從 Android 裝置系統管理員管理至工作設定檔管理<!--5857738-->
我們將發行 Android 裝置系統管理員平台的新合規性設定。 此設定可讓您在裝置由裝置系統管理員管理時，將其設為不符合規範。

在這些不符合規範的裝置上，於 [更新裝置設定]  頁面中，使用者會看到 [移至新的裝置管理安裝程式]  訊息。 如果使用者按下 [解決]  按鈕，系統將會引導完成下列動作：

1. 從裝置系統管理員管理取消註冊
2. 在工作設定檔管理中註冊
3. 解決合規性問題 
 
為了透過 Android 企業轉移到更加現代化、豐富且安全的裝置管理，Google 正在減少新 Android 版本中裝置系統管理員的支援。  Intune 只能為執行 Android 10 和更新版本的裝置系統管理員所管理 Android 裝置提供完整支援，且支援僅提供至 2020 年度第 2 季。 在此期間過後，執行 Android 10 或更新版本的裝置系統管理員所管理裝置 (Samsung 除外) 將無法再完全受控。 尤其受影響的裝置不會再收到新的密碼要求。 如需詳細資訊，請參閱此[注意事項](#decreasing-support-for-android-device-administrator)。

### <a name="retire-noncompliant-devices---1827291---"></a>淘汰不符合規範的裝置<!-- 1827291 -->
我們將新增選擇性的合規性動作，以淘汰不符合規範的裝置 ([裝置]   > [合規性政策]   > [原則]   > [建立原則]  ，然後在「針對不符合規範要採取的動作」  頁面上查看可用的「動作」  。  淘汰不相容的裝置會從移除所有公司資料，同時將裝置從由 Intune 管理的裝置中移除。 此動作會在設定的值 (天數) 到達時執行。 最小值為 30 天。  明確的 IT 系統管理員核准必須使用「淘汰不符合規範的裝置」  區段來淘汰裝置，系統管理員可以在該區段中淘汰所有符合條件的裝置。

### <a name="new-information-in-device-details---5604099---"></a>裝置詳細資料中的新資訊<!-- 5604099 -->
下列資訊將顯示於裝置的 [概觀]  頁面上：
- 儲存體容量 (裝置上的實體儲存體總數)
- 記憶體容量 (裝置上的實體記憶體總數)

### <a name="script-support-for-macos-devices---4280361----"></a>macOS 裝置的指令碼支援<!-- 4280361  -->
您將能夠新增指令碼並將其部署至 macOS 裝置。 這項支援可讓您使用 macOS 裝置上的原生 MDM 功能，大幅延伸您能對 macOS 裝置所做的設定。 

<!-- ***********************************************-->
<!--## Intune apps-->
 

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
## <a name="monitor-and-troubleshoot"></a>監視及疑難排解

### <a name="help-and-support-workflow-update-to-support-additional-services---5654170---"></a>更新說明及支援工作流程以支援其他服務<!-- 5654170 -->
我們將更新 Microsoft 端點管理員系統管理中心的 [說明及支援] 頁面，讓您能夠選擇想要使用的管理類型，並以更佳的方式提供特定支援 ([疑難排解 + 支援]   >  [說明及支援]  )。 透過這項變更，您將可以從下列管理類型中選取：
- Configuration Manager (包含電腦分析)
- Intune
- 共同管理

<!-- ***********************************************-->
<!--
## Role-based access control
-->

<!-- ***********************************************-->
## <a name="security"></a>安全性

### <a name="derived-credentials-support-on-android-cobo-devices--4839592--"></a>Android COBO 裝置上的衍生認證支援<!--4839592-->
您將能夠在 Android Enterprise 完全受控裝置上使用衍生認證。 將會包含針對擷取 Entrust Datacard、Intercede 和 DISA Purebred 衍生認證的支援。 若應用程式支援，您可以將衍生認證用於應用程式驗證、Wi-Fi、VPN 或 S/MIME 簽署和/或加密。

### <a name="use-antivirus-policy-to-manage-settings-for-microsoft-defender-antivirus-and-the-windows-security-experience--6131401---"></a>使用防毒原則來管理 Microsoft Defender 防毒軟體和 Windows 安全性體驗的設定<!--6131401 -->
您將能夠從 [端點安全性]  節點中設定**防毒軟體**的設定。 在您設定防毒軟體的原則時，您會透過兩個設定檔類型來定義 Windows 10 裝置的設定：

- Microsoft Defender 防毒軟體：管理雲端保護、防毒軟體的排除項目、補救、掃描選項等設定。
- Windows 安全性體驗：管理使用者在其裝置上體驗 Windows 安全性設定的方式。 您將可以設定終端使用者能在 Microsoft Defender 安全性中心內所看到內容以及所收到通知。

### <a name="users-personal-encrypted-recovery-key---6273943---"></a>使用者的個人加密修復金鑰<!-- 6273943 -->
即將提供新的 Intune 功能，可讓使用者透過 Android 公司入口網站應用程式，或透過 Android Intune 應用程式，擷取其 Mac 裝置的個人加密 **FileVault** 修復金鑰。 公司入口網站應用程式與 Intune 應用程式中都將會提供一個連結，該連結會開啟 Chrome 瀏覽器，並連線至 Web 公司入口網站，使用者可以在該網站中看到存取其 Mac 裝置所需的 **FileVault** 復原金鑰。 如需加密的詳細資訊，請參閱[搭配 Intune 使用裝置加密](~/protect/encrypt-devices.md)。

### <a name="privacy-preferences-settings-for-macos-devices---2934232---"></a>macOS 裝置的隱私權喜好設定<!-- 2934232 --> 
隨著 macOS Catalina 10.15 的發行，Apple 新增了安全性與隱私權的增強功能。 根據預設，應用程式與處理序無法在沒有使用者同意的情況下存取特定資料。 如果未經過使用者同意，則應用程式與處理序可能無法運作。 Intune 將新增設定的支援，可讓 IT 系統管理員在執行 macOS 10.14 和更新版本的裝置上，代表終端使用者允許 (或不允許) 資料存取。 這些設定可確保應用程式與處理序繼續正常運作，並減少終端使用者接收到提示的次數。 

### <a name="updated-ui-text-and-labels-for-windows-10-endpoint-protection-profile-settings---5983747---"></a>更新了 Windows 10 Endpoint Protection 設定檔設定的 UI 文字與標籤<!-- 5983747 -->
我們將更新 Windows 10 裝置組態設定檔中各種設定的文字，讓您更容易理解這些設定的用途與結果。 

我們即將更新的設定會包括 Windows 10 裝置組態設定檔的下列項目： 
- [裝置限制](../configuration/device-restrictions-windows-10.md#microsoft-defender-antivirus) > Microsoft Defender 防毒軟體  
- [Endpoint Protection](../protect/endpoint-protection-windows-10.md) > Microsoft Defender 防毒軟體

Intune 所支援的設定不會變更。 此僅為 Microsoft 端點管理系統管理中心內的 UI 文字更新。 


<!-- ***********************************************-->
## <a name="notices"></a>通知

[!INCLUDE [Intune notices](../includes/intune-notices.md)]

## <a name="see-also"></a>請參閱
如需近期發展的詳細資料，請參閱 [Microsoft Intune 的新功能](whats-new.md)。




---
title: 開發中 - Microsoft Intune
titleSuffix: ''
description: 正在開發的 Microsoft Intune 功能
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/03/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.assetid: 25b3c26e-cf4e-4152-8306-bf4be4af2ad1
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: cafe9d3036a727d79de88eda050399138da55675
ms.sourcegitcommit: 24487f078349795922dc497c952e8358cf767a1a
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 02/04/2020
ms.locfileid: "76977745"
---
# <a name="in-development-for-microsoft-intune---february-2020"></a>Microsoft Intune 正在開發的項目 - 2020 年 2 月

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

### <a name="display-notifications-for-the-company-portal-app-on-windows---1808082----"></a>在 Windows 上顯示公司入口網站應用程式的通知<!-- 1808082  -->
我們會更新 Windows 裝置上的公司入口網站應用程式，以向使用者顯示快顯通知，即使應用程式關閉也是一樣。 只有在安裝狀態為已完成或失敗時，更新才會顯示可用應用程式的通知。 公司入口網站應用程式不會顯示必要應用程式的通知。 

### <a name="display-installation-status-messages-for-the-company-portal-app---2514416----"></a>顯示公司入口網站應用程式的安裝狀態訊息<!-- 2514416  -->
公司入口網站應用程式會向終端使用者顯示額外的應用程式安裝狀態訊息。 下列條件將會適用於新的 Win32 相依性功能：
- 應用程式無法啟動。 不符合系統管理員定義的相依性。

### <a name="retarget-web-clips-to-microsoft-edge-on-ios-devices---5455276---"></a>在 iOS 裝置上將 Web 剪輯的目標重新設定為 Microsoft Edge<!-- 5455276 -->
必須更新 Web 剪輯 (iOS 裝置上釘選為 Web 應用程式)。 如果需要在受保護的瀏覽器中開啟，新部署的 Web 剪輯會在 Microsoft Edge 中開啟，而不是在 Intune Managed Browser 中開啟。 您必須為預先存在的 Web 剪輯重定目標，以確保其在 Microsoft Edge 中開啟，而不是在 Managed Browser 中開啟。

### <a name="macos-company-portal-user-experience-improvements---5568987---"></a>macOS 公司入口網站使用者體驗改善<!-- 5568987 -->
我們正在改善 macOS 裝置註冊體驗和 Mac 的公司入口網站應用程式。 您可以預期下列項目：
- 在註冊期間獲得更佳的 Microsoft **自動更新**體驗，可確保使用者擁有最新版公司入口網站。
- 註冊期間增強的合規性檢查步驟。
- 支援複製的事件識別碼，可讓使用者更快速從裝置將錯誤傳送給您的公司支援小組。

如需註冊和 Mac 的公司入口網站應用程式詳細資訊，請參閱使用公司入口網站應用程式註冊您的 macOS 裝置 (https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-macos-cp) 。 


### <a name="screen-removed-from-company-portal-android-work-profile-enrollment--6103987---"></a>將從公司入口網站 Android 工作設定檔註冊移除畫面<!--6103987 -->
我們將從公司入口網站中的 Android 工作設定檔註冊流程移除 [下一步是什麼？]  畫面，以簡化使用者體驗。 請前往[使用 Android 工作設定檔註冊]( https://docs.microsoft.com/intune-user-help/enroll-device-android-work-profile)，以查看目前的 Android 工作設定檔註冊流程。

### <a name="microsoft-defender-advanced-threat-protection-atp-app-for-macos---5424518-idready---"></a>macOS 版 Microsoft Defender 進階威脅防護 (ATP) 應用程式<!-- 5424518 idready -->
Intune 將會提供一種將 macOS 版 Microsoft Defender 進階威脅防護 (ATP) 應用程式部署至受控 Mac 裝置的簡單方法。 如需詳細資訊，請參閱 [Mac 版 Microsoft Defender 進階威脅防護](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-atp-mac)。 

<!-- ***********************************************-->
## <a name="device-configuration"></a>裝置設定

### <a name="wired-network-device-configuration-profiles-for-macos-devices---3508686----"></a>適用於 macOS 裝置的有線網路裝置組態設定檔<!-- 3508686  -->
將會可以使用設定有線網路的 macOS 裝置設定檔 ([裝置設定]   > [設定檔]   > [建立設定檔]   > [macOS]  平台 > [有線網路]  設定檔類型)。 使用此功能來建立 802.1x 設定檔以管理有線網路，並將這些有線網路部署至您的 macOS 裝置。

適用於：
- macOS

### <a name="vpn-profiles-with-ikev2-vpn-connections-can-use-always-on-with-ios-devices----1947932-idready---"></a>使用 IKEv2 VPN 連線的 VPN 設定檔可以搭配 iOS 裝置使用 Always On <!-- 1947932 idready -->
在 iOS 裝置上，您可以建立使用 IKEv2 連線的 VPN 設定檔 ([裝置設定]   > [設定檔]   > [建立設定檔]   > [iOS/iPadOS]  平台 > [VPN]  設定檔類型)。 在未來的更新中，您可以搭配 IKEv2 設定 Always-On。 設定之後，IKEv2 VPN 設定檔會自動連線，並保持連線 (或快速重新連線) 至 VPN。 即使在網路之間移動或將裝置重新開機，仍會保持連線。

在 iOS 上，Always-On VPN 僅限於 IKEv2 設定檔。

若要查看您目前可以設定的 IKEv2 設定，請前往[在 Microsoft Intune 中於 iOS 裝置上新增 VPN 設定](../configuration/vpn-settings-ios.md#ikev2-settings)。

適用於：
- iOS

### <a name="improved-user-interface-experience-when-creating-configuration-profiles-on-ios-and-macos-devices---5569008-5569039-5569057-5569110-5569116-5569131-5569139-5569153-5859984-idready---"></a>已改善在 iOS 和 macOS 裝置上建立設定檔時的使用者介面體驗<!-- 5569008-5569039-5569057-5569110-5569116-5569131-5569139-5569153-5859984 idready -->
當您建立 iOS 或 macOS 裝置的設定檔時，將會更新端點管理系統管理中心的體驗。 此變更會影響下列裝置設定檔 ([裝置]   > [設定檔]   > [建立設定檔]   > [iOS]  或 [macOS]  平台)：

- 自訂：iOS、macOS
- 裝置功能：iOS、macOS
- 裝置限制：iOS、macOS
- 端點保護：macOS
- 擴充功能：macOS
- 喜好設定檔案：macOS

### <a name="improved-user-interface-experience-when-creating-oemconfig-configuration-profiles-on-android-enterprise-devices---5568645-idready----"></a>已改善在 Android Enterprise 裝置上建立 OEMConfig 設定檔時的使用者介面體驗<!-- 5568645 idready  -->
當您建立或編輯 Android Enterprise 裝置的 OEMConfig 設定檔時，端點管理系統管理中心的體驗已更新。 更新的體驗將會針對您已設定的項目提供簡短摘要。 此變更會影響 OEMConfig 裝置設定檔 ([裝置]   > [設定檔]   > [建立設定檔]   > [Android Enterprise]  平台 > [OEMConfig]  設定檔類型)。

本功能適用於：
- Android 企業 


<!-- ***********************************************-->
<!--## Device enrollment-->


<!-- ***********************************************-->
## <a name="device-management"></a>裝置管理

### <a name="change-primary-user-for-windows-devices----3794742---"></a>變更 Windows 裝置的主要使用者 <!-- 3794742 -->
您將能夠變更 Windows 混合式和 Azure AD 加入裝置的主要使用者。 若要執行此操作，請前往 [Intune]   > [裝置]   > [所有裝置]  > 選擇裝置 > [屬性]   > [主要使用者]  。 

### <a name="serial-number-on-the-apple-mdm-push-certificate-page--5947765---"></a>[Apple MDM Push Certificate] 頁面上的序號<!--5947765 -->
[Apple MDM Push Certificate] 頁面將會顯示序號。 如果您無法存取建立憑證的 Apple ID，則需要序號來重新取得 Apple MDM Push Certificate 的存取權。 若要查看序號，請前往 [裝置]   > [iOS]   > [iOS 註冊]   > [Apple MDM Push Certificate]  。

### <a name="choose-which-iosipados-updates-to-push-to-enrolled-devices--5879689---"></a>選擇要推送至已註冊裝置的 iOS/iPadOS 更新<!--5879689 -->
您將能夠選擇特定的 iOS/iPadOS 更新，以推送至使用 Apple Business Manager 或 Apple School Manager 註冊的裝置。 這些裝置必須將裝置設定原則設為將軟體更新可見度延遲數天。 若要查看這項功能，請前往 MEM > [裝置]   > [iOS]   > [iOS/iPadOS 的更新原則]   > [建立設定檔]  。

### <a name="new-update-schedule-options-for-pushing-os-updates-to-enrolled-iosipados-devices--5879689--"></a>將 OS 更新推送至已註冊 iOS/iPadOS 裝置的新更新排程選項<!--5879689-->
在排程 iOS/iPadOS 裝置的作業系統更新時，您將可以選擇下列選項。 這項功能適用於使用 Apple Business Manager 或 Apple School Manager 註冊類型的裝置。
- 在下次簽入時更新
- 在排程時間的期間內更新
- 在排程時間的期間外更新

針對後面兩個選項，您可以建立多個時間範圍。

若要查看新選項，請前往 MEM > [裝置]   > [iOS]   > [iOS/iPadOS 的更新原則]   > [建立設定檔]  。


<!-- ***********************************************-->
<!--## Intune apps-->
 

<!-- ***********************************************-->
## <a name="monitoring-and-troubleshooting"></a>監視和疑難排解

### <a name="improved-intune-reporting-experience---3791418-idready---"></a>已改善的 Intune 報告體驗<!-- 3791418 idready -->
Intune 現在提供已改善的報告體驗，包括新報表類型、更好的報表組織、更聚焦的檢視、已改善的報表功能，以及更一致且即時的資料。 報告體驗將從公開預覽改為 GA (正式版本)。 此外，GA 版本將會提供當地語系化支援、Bug 修正、設計改善、且在 [Microsoft 端點管理員系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)的圖格上彙總裝置合規性資料。

新報表類型著重於下列項目：
- **營運** - 提供最新記錄，包含負面健康情況焦點。 
- **組織** - 提供整體狀態的更廣泛摘要。
- **歷程記錄** - 提供一段時間的模式和趨勢。
- **專家** - 可讓您使用未經處理資料來建立您自己的自訂報表。

第一組新報表專注於裝置合規性。 如需詳細資訊，請參閱[部落格 - Microsoft Intune 報告架構](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/New-Reporting-Framework-Coming-to-Intune/ba-p/1009553) \(英文\) 和 [Intune 報表](~/fundamentals/reports.md)。



<!-- ***********************************************-->
## <a name="role-based-access-control"></a>角色型存取控制

### <a name="intune-roles-user-interface-changes-coming--5801612-idready--"></a>Intune 角色使用者介面變更即將推出<!--5801612 idready-->
[Microsoft 端點管理員系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)的使用者介面 > [租用戶系統管理]   >  [角色]  將會變更為更容易使用且直覺的設計。 此體驗提供您現在所使用的相同設定和詳細資料，但新體驗是採用精靈型程序。


<!-- ***********************************************-->
## <a name="security"></a>安全性

### <a name="derived-credentials-support-on-android-cobo-devices--4839592--"></a>Android COBO 裝置上的衍生認證支援<!--4839592-->
您將能夠在 Android Enterprise 完全受控裝置上使用衍生認證。 將會包含針對擷取 Entrust Datacard、Intercede 和 DISA Purebred 衍生認證的支援。 若應用程式支援，您可以將衍生認證用於應用程式驗證、Wi-Fi、VPN 或 S/MIME 簽署和/或加密。

### <a name="use-antivirus-policy-to-manage-settings-for-microsoft-defender-antivirus-and-the-windows-security-experience--6131401---"></a>使用防毒原則來管理 Microsoft Defender 防毒軟體和 Windows 安全性體驗的設定<!--6131401 -->
您將能夠從 [端點安全性]  節點中設定**防毒軟體**的設定。 在您設定防毒軟體的原則時，您會透過兩個設定檔類型來定義 Windows 10 裝置的設定：

- Microsoft Defender 防毒軟體：管理雲端保護、防毒軟體的排除項目、補救、掃描選項等設定。
- Windows 安全性體驗：管理使用者在其裝置上體驗 Windows 安全性設定的方式。 您將可以設定終端使用者能在 Microsoft Defender 安全性中心內所看到內容以及所收到通知。 

<!-- ***********************************************-->
## <a name="notices"></a>通知

[!INCLUDE [Intune notices](../includes/intune-notices.md)]

## <a name="see-also"></a>請參閱
如需近期發展的詳細資料，請參閱 [Microsoft Intune 的新功能](whats-new.md)。



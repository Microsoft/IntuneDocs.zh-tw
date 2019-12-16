---
title: Microsoft Intune 的新功能 - Azure | Microsoft Docs
titleSuffix: ''
description: 了解 Intune Azure 入口網站中的新功能
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 12/09/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 791ed23f-bd13-4ef0-a3dd-cd2d7332c5cc
ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 77cf4745262346ec2f8bfb5d4d7e67e1ee5c5e07
ms.sourcegitcommit: edd06a494a241d198ca9b0d3030c92195976e0d3
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/11/2019
ms.locfileid: "75000375"
---
# <a name="whats-new-in-microsoft-intune"></a>Microsoft Intune 的新功能

了解每週的 Microsoft Intune 新功能 您也可以尋找[重要通知](#notices)、[過去的版本](whats-new-archive.md)，以及[如何發佈 Intune 服務更新](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Microsoft-Intune-Service-Updates/ba-p/358728) \(英文\) 的相關資訊。

> [!Note]
> 每個[每月更新](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Microsoft-Intune-Service-Updates/ba-p/358728) \(英文\) 最多可能需要三天的推出時間，而且將依照下列順序推出：
>
> - 第 1 天：亞太地區 (APAC)
> - 第 2 天：歐洲、中東、非洲 (EMEA)
> - 第 3 天：北美
>
> 某些功能在首度發行時可能會花費數週的時間，而可能無法在第一週就提供給所有客戶。
>
> 請檢查[開發中頁面](in-development.md)，以了解某個版本中即將推出的功能清單。

**RSS 摘要**：將下列 URL 複製並貼上至您的摘要讀取器中，以在本頁更新時收到通知：`https://docs.microsoft.com/api/search/rss?search=%22What%27s+new+in+microsoft+intune%3F+-+Azure%22&locale=en-us`

<!-- Common categories:  
### App management
### Device configuration
### Device enrollment
### Device management
### Device security
### Intune apps
### Monitor and troubleshoot
### Role-based access control
-->  

<!-- ########################## -->
## <a name="week-of-december-9-2019"></a>2019 年 12 月 9 日當週

#### <a name="migrating-to-microsoft-edge-for-managed-browsing-scenarios---5173762---"></a>移轉到 Microsoft Edge 以進行受控瀏覽案例<!-- 5173762 -->

隨著 Intune Managed Browser 即將淘汰，我們對應用程式防護原則進行了變更，以簡化將使用者移至 Edge 所需的步驟。 我們已將應用程式防護原則設定 [限制使用其他應用程式的 Web 內容傳輸]  中的選項更新為下列其中一項：

- 任何應用程式
- Intune Managed Browser
- Microsoft Edge
- 非受控瀏覽器 

當您選取 [Microsoft Edge]  時，終端使用者會看到條件式存取訊息，通知他們需要 Microsoft Edge才能進行受控瀏覽案例。 如果尚未使用其 AAD 帳戶下載和登入 Microsoft Edge，也會收到執行此作業的提示。  這相當於以啟用 MAM 的應用程式為目標，並將應用程式組態設定 `com.microsoft.intune.useEdge` 設定為 [True]  。 使用 [受原則管理的瀏覽器]  設定的現有應用程式防護原則現在會選取 **Intune Managed Browser**，且您不會看到任何行為變更。 這表示如果您已將應用程式組態設定 [useEdge]  設定為 [True]  ，則使用者會看到使用 Microsoft Edge 的訊息。 建議利用受控瀏覽案例的所有客戶，都將其應用程式防護原則更新為 [限制使用其他應用程式的 Web 內容傳輸]  ，以確保使用者無論在哪一個應用程式啟動連結，都能看到轉換至 Microsoft Edge 的適當指引。 

<!-- ########################## -->
## <a name="week-of-december-2-2019"></a>2019 年 12 月 2 日當週

#### <a name="new-microsoft-endpoint-configuration-manager-co-management-licensing--5027281--"></a>新的 Microsoft Endpoint Configuration Manager 共同管理授權<!--5027281-->
現在提供新的授權，可讓具有軟體保證的 Configuration Manager 客戶取得適用於 Windows 10 電腦的 Intune 共同管理功能，不需要購買額外的 Intune 授權，即可進行共同管理。 客戶不再需要將個別的 Intune/EMS 授權指派給其終端使用者，即可共同管理 Windows 10。
- Configuration Manager 所管理並已註冊共同管理的裝置，與 Intune 獨立版 MDM 受控電腦幾乎有相同的權限。 不過，重設之後，則無法使用 Autopilot 來重新佈建些裝置。
- 使用其他方式在 Intune 中註冊的 Windows 10 裝置需要完整的 Intune 授權。
- 其他平台上的裝至仍然需要完整的 Intune 授權。

如需詳細資訊，請參閱[授權條款](https://www.microsoft.com/en-us/Licensing/product-licensing/products)。


<!-- ########################## -->
## <a name="week-of-november-18-2019-1911-service-release"></a>2019 年 11 月 18 日當週 (1911 服務版本)

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>應用程式管理

#### <a name="smime-support-with-microsoft-outlook-for-ios---2669398-idready---"></a>搭配 iOS 版 Microsoft Outlook 的 S/MIME 支援<!-- 2669398 idready -->

   > [!NOTE]
   > 此功能已延後，但即將發行。

Intune 支援在 iOS 裝置上傳遞可搭配 iOS 版 Microsoft Outlook 使用的 S/MIME 簽署和加密憑證。 如需相關資訊，請參閱[設定 iOS 版 Microsoft Outlook 的 S/MIME](~/apps/app-configuration-policies-outlook-smime.md)。

#### <a name="ui-update-when-selectively-wiping-app-data---4102028---"></a>選擇性地抹除應用程式資料時的 UI 更新<!-- 4102028 -->
在 Intune 中選擇性地抹除應用程式資料的 UI 已更新。 UI 變更包括：
- 使用壓縮成單一窗格的精靈樣式格式簡化體驗。
- 針對建立流程的更新，以包含指派。
- 檢視屬性 (建立新的原則之前) 或編輯屬性時所設定之所有內容的摘要頁面。 此外，當編輯屬性時，摘要只會顯示正在編輯的屬性類別中的項目清單。

如需詳細資訊，請參閱[如何僅抹除 Intune 受控應用程式中的公司資料](~/apps/apps-selective-wipe.md)。

#### <a name="ios-and-ipados-third-party-keyboard-support---4922950---"></a>iOS 和 iPadOS 協力廠商鍵盤支援<!-- 4922950 -->
在 2019 年 3 月，我們宣布移除「協力廠商鍵盤」iOS 應用程式保護原則。 該功能將回到 Intune，且包含 iOS 和 iPadOS 支援。 若要啟用此設定，請瀏覽新的或現有 iOS/iPadOS 應用程式保護原則的 [資料保護]  索引標籤，並在 [資料傳輸]  底下尋找 [協力廠商鍵盤]  設定。

此原則設定的行為與先前的實作稍有不同。 在使用 SDK 12.0.16 版和更新版本的多重身分識別應用程式中，若該應用程式為應用程式保護原則的目標，且此設定為 [封鎖]  時，終端使用者將無法在其組織和個人帳戶中選擇協力廠商鍵盤。 使用 SDK 12.0.12 版和更早版本的應用程式會繼續表現我們部落格文章標題中記載的行為，[已知問題：在 iOS 中未針對個人帳戶封鎖協力廠商鍵盤](https://aka.ms/3rdparty_iOS_Intune) \(英文\)。

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-configuration"></a>裝置設定

#### <a name="target-macos-user-groups-to-require-jamf-management---4061739----"></a>將目標 macOS 使用者群組設定為需要 Jamf 管理<!-- 4061739  --> 
您可以將特定使用者群組作為目標，其 [macOS 裝置會由 Jamf 管理](../protect/conditional-access-integrate-jamf.md)。 這可讓您將 Jamf 合規性整合套用至 macOS 裝置的子集，而其他裝置則由 Intune 管理。 如果您已經使用 Jamf 整合，則預設會將所有使用者作為整合目標。

#### <a name="new-exchange-activesync-settings-when-creating-an-email-device-configuration-profile-on-ios-devices---4892824-----"></a>在 iOS 裝置上建立電子郵件裝置組態設定檔時的新 Exchange ActiveSync 設定<!-- 4892824   --> 
在 iOS/iPadOS 裝置上，您可以在裝置組態設定檔中設定電子郵件連線能力 ([裝置設定]   > [設定檔]   > [建立設定檔]   > [iOS/iPadOS]  作為平台 > [電子郵件]  作為設定檔類型)。 

有新的 Exchange ActiveSync 設定可供使用，包括：
- **要同步的 Exchange 資料**：選擇要同步處理 (或封鎖同步處理) 行事曆、連絡人、提醒事項、便箋和電子郵件的 Exchange 服務。
- **允許使用者變更同步設定**：允許 (或封鎖) 使用者在其裝置上變更這些服務的同步處理設定。  

如需這些設定的詳細資訊，請移至 [Intune 中 iOS 裝置的電子郵件設定檔設定](../configuration/email-settings-ios.md)。 

適用於：
- iOS 13.0 與更新版本
- iPadOS 13.0 和更新版本

#### <a name="prevent-users-from-adding-personal-google-accounts-to-android-enterprise-fully-managed-and-dedicated-devices---5353228-----"></a>防止使用者將個人 Google 帳戶新增至 Android Enterprise 完全受控和專用裝置<!-- 5353228   -->
在 Android Enterprise 完全受控和專用的裝置上，有新設定可防止使用者建立個人 Google 帳戶 ([裝置設定]   > [設定檔]   > [建立設定檔]   >  [Android Enterprise]  作為平台 > [僅限裝置擁有者] > [裝置限制]  作為設定檔類型 > [使用者及帳戶] 設定   > [個人 Google 帳戶]  )。

若要查看您可以設定的設定，請參閱[使用 Intune 來允許或限制功能的 Android Enterprise 裝置設定](../configuration/device-restrictions-android-for-work.md)。

適用於：
- 完全受控的 Android Enterprise 裝置
- Android Enterprise 專用裝置

#### <a name="server-side-logging-for-siri-commands-setting-is-removed-in-iosipados-device-restrictions-profile----5468501-----"></a>Siri 命令的伺服器端記錄設定已從 iOS/iPadOS 裝置限制設定檔中移除 <!-- 5468501   -->
在 iOS 和 iPadOS 裝置上，[Siri 命令的伺服器端記錄]  設定已從 Microsoft 端點管理員系統管理員主控台中移除 ([裝置設定]   > [設定檔]   > [建立設定檔]   > [iOS/iPadOS]  作為平台 > [裝置限制]  作為設定檔類型 > [內建應用程式]  )。 

此設定不會影響裝置。 若要從現有設定檔中移除設定，請開啟設定檔、進行任何變更，然後儲存設定檔。 設定檔隨即更新，並從裝置刪除設定。

若要查看您可以設定的所有設定，請參閱[使用 Intune 來允許或限制功能的 iOS 和 iPadOS 裝置設定](../configuration/device-restrictions-ios.md)。

適用於：
- iOS/iPadOS

#### <a name="windows-10-feature-updates-public-preview---2384877---"></a>Windows 10 功能更新 (公開預覽)<!-- 2384877 -->
您現在可以將 [Windows 10 功能更新](../protect/windows-update-for-business-configure.md#windows-10-feature-updates)部署至 Windows 10 裝置。 Windows 10 功能更新是新的軟體更新原則，可設定您想要裝置安裝並保持的 Windows 10 版本。 您可以使用此新原則類型以及現有的 Windows 10 更新通道。

收到 Windows 10 功能更新原則的裝置會安裝所指定 Windows 版本，並在編輯或移除原則之前保持為該版本。 執行較新 Windows 版本的裝置仍會保持為其目前版本。 保持為特定 Windows 版本之裝置仍然可以從 Windows 10 更新通道安裝該版本的品質和安全性更新。

自本週開始，會向租用戶推出此新的原則類型。 這項原則將於近日推出供租用戶使用。

#### <a name="add-and-change-key-information-in-plist-files-for-macos-applications---4736278---"></a>在 macOS 應用程式的 plist 檔案中新增和變更重要資訊<!-- 4736278 -->
在 macOS 裝置上，您現在可以建立裝置組態設定檔，以上傳與應用程式或裝置相關聯的屬性清單檔案 (.plist) ([裝置設定]   > [設定檔]   > [建立設定檔]   > [macOS]  作為平台 > [喜好設定檔案]  作為設定檔類型)。

只有部分應用程式支援受控喜好設定，而這些應用程式可能不允許您管理所有設定。 請務必上傳設定裝置通道設定的屬性清單檔案，而不是使用者通道設定。

如需此功能的詳細資訊，請參閱[使用 Microsoft Intune 將屬性清單檔案新增至 macOS 裝置](../configuration/preference-file-settings-macos.md)。

適用於：
- 執行 10.7 和更新版本的 macOS 裝置

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>裝置管理

#### <a name="edit-device-name-value-for-autopilot-devices---2640074---"></a>編輯 Autopilot 裝置的裝置名稱值<!-- 2640074 -->
您可以針對已加入 Azure AD 的 Autopilot 裝置，編輯其裝置名稱值。  如需詳細資訊，請參閱[編輯 Autopilot 裝置屬性](../enrollment/enrollment-autopilot.md#edit-autopilot-device-attributes)。

#### <a name="edit-group-tag-value-for-autopilot-devices---4816775-----"></a>編輯 Autopilot 裝置的群組標籤值<!-- 4816775   -->
您可以編輯 Autopilot 裝置的群組標籤值。 如需詳細資訊，請參閱[編輯 Autopilot 裝置屬性](../enrollment/enrollment-autopilot.md#edit-autopilot-device-attributes)。

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="monitor-and-troubleshoot"></a>監視及疑難排解

#### <a name="updated-support-experience---5012398---"></a>已更新支援體驗<!-- 5012398 -->

自即日起，會向租用戶推出針對[取得 Intune 說明及支援](get-support.md)之更新及簡化的主控台內體驗。 這項新體驗將於近日推出供您使用。

我們已改善主控台內常見問題的搜尋和意見反應，以及您用於連絡支援人員的工作流程。 當您建立支援問題時，您會看到回撥或電子郵件回覆的即時預估，且進階與統一支援客戶可以輕鬆地指定其問題的嚴重性，以協助更快取得支援。

#### <a name="improved-intune-reporting-experience-public-preview----3791418---"></a>已改善的 Intune 報告體驗 (公開預覽) <!-- 3791418 -->
Intune 現在提供已改善的報告體驗，包括新報表類型、更好的報表組織、更聚焦的檢視、已改善的報表功能，以及更一致且即時的資料。 新報表類型著重於下列項目：
- **營運** - 提供最新記錄，包含負面健康情況焦點。 
- **組織** - 提供整體狀態的更廣泛摘要。
- **歷程記錄** - 提供一段時間的模式和趨勢。
- **專家** - 可讓您使用未經處理資料來建立您自己的自訂報表。

第一組新報表專注於裝置合規性。 如需詳細資訊，請參閱[部落格 - Microsoft Intune 報告架構](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/New-Reporting-Framework-Coming-to-Intune/ba-p/1009553) \(英文\) 和 [Intune 報表](~/fundamentals/reports.md)。

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="role-based-access-control"></a>以角色為基礎的存取控制

#### <a name="duplicate-custom-or-built-in-roles----1081938-----"></a>重複的自訂或內建角色 <!-- 1081938   -->
您現在可以複製內建和自訂角色。 如需詳細資訊，請參閱[複製角色](../fundamentals/create-custom-role.md#copy-a-role)。

#### <a name="new-permissions-for-school-administrator-role----5621805----"></a>學校系統管理員角色的新權限 <!-- 5621805  -->  
已經新增兩個新權限 ([指派設定檔]  和 [同步裝置]  ) 至學校系統管理員角色 > [權限]   > [註冊計劃]  。 同步設定檔權限可讓群組管理員同步處理 Windows Autopilot 裝置。 指派設定檔權限可讓他們刪除使用者起始的 Apple 註冊設定檔。 它也讓他們有權管理 Autopilot 裝置指派和 Autopilot 部署設定檔指派。 如需學校系統管理員/群組管理員所有權限的清單，請參閱[指派群組管理員](https://docs.microsoft.com/intune-education/group-admin-delegate) \(部分機器翻譯\)。 

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="security"></a>安全性

#### <a name="bitlocker-key-rotation---2564951----"></a>BitLocker 金鑰輪替<!-- 2564951  -->
您可以使用 Intune 裝置動作，針對執行 Windows 1909 版或更新版本的受控裝置，從遠端[輪替 BitLocker 修復金鑰](../protect/encrypt-devices.md#rotate-bitlocker-recovery-keys)。 若要有資格輪替修復金鑰，裝置必須設定為支援修復金鑰輪替。  

#### <a name="updates-to-dedicated-device-enrollment-to-support-scep-device-certificate-deployment----5198878----"></a>更新專用裝置註冊以支援 SCEP 裝置憑證部署 <!-- 5198878  -->
Intune 現在支援對 Android Enterprise 專用裝置進行憑證型 Wi-Fi 存取設定檔的 SCEP 裝置憑證部署。 Microsoft Intune 應用程式必須存在於裝置上才能部署。 因此，我們已經更新 Android Enterprise 專用裝置的註冊體驗。 新註冊仍然以相同方式開始 (使用 QR、NFC、零觸控或裝置識別碼)，但現在有要求使用者安裝 Intune 應用程式的步驟。 現有裝置將會輪流自動安裝該應用程式。

#### <a name="intune-audit-logs-for-business-to-business-collaboration--5670211---"></a>企業對企業的 Intune 稽核記錄<!--5670211 -->
企業對企業 (B2B) 共同作業可讓您安全地與來自任何其他組織的來賓使用者共用公司的應用程式和服務，同時保有您公司資料的控制權。 Intune 現在支援 B2B 來賓使用者的稽核記錄。 例如，當來賓使用者進行變更時，Intune 將能夠透過稽核記錄來捕捉此資料。 如需詳細資訊，請參閱[什麼是 Azure Active Directory B2B 中的來賓使用者存取權？](https://docs.microsoft.com/azure/active-directory/b2b/what-is-b2b)


<!-- ########################## -->
## <a name="week-of-november-11-2019"></a>2019 年 11 月 11 日當週  

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>應用程式管理  

#### <a name="improved-macos-enrollment-experience-in-company-portal----5074349-wnready---"></a>已改善公司入口網站的 macOS 註冊體驗 <!-- 5074349 WNready -->  
提供 macOS 註冊體驗的公司入口網站有更簡易註冊程序，其更貼近 iOS 版公司入口網站的註冊體驗。 裝置使用者現在會看到：  

* 更時尚的使用者介面。  
* 改善的註冊檢查清單。  
* 更清楚的裝置註冊指示。  
* 改善的疑難排解選項。  

#### <a name="web-apps-launched-from-the-windows-company-portal-app---5030972---"></a>從 Windows 公司入口網站應用程式啟動的 Web 應用程式<!-- 5030972 -->
終端使用者現在可以直接從 Windows 公司入口網站應用程式啟動 Web 應用程式。 終端使用者可以選取 Web 應用程式，然後選擇 [以瀏覽器開啟]  選項。 已發佈的 Web URL 會直接在網頁瀏覽器中開啟。 此功能將於下周推出。 如需 Web 應用程式的詳細資訊，請參閱[將 Web 應用程式新增至 Microsoft Intune](~/apps/web-app.md)。  


#### <a name="new-assignment-type-column-in-company-portal-for-windows-10----5459950-wnready---"></a>Windows 10 公司入口網站中新的指派類型資料行 <!-- 5459950 WNready -->
公司入口網站 > [已安裝的應用程式]   > [指派類型]  資料行已重新命名為 [由您的組織要求]  。  使用者在該資料行下會看到 [是]  或 [否]  值，其表示應用程式為必要或是由其組織設為選擇性。 因為裝置使用者對可用應用程式的概念深感困惑，所以才有這些變更。 如需從公司入口網站安裝應用程式的詳細資訊，請參閱[在裝置上安裝和共用應用程式](/intune-user-help/install-apps-cpapp-windows)。 使用者如需設定公司入口網站應用程式的詳細資訊，請參閱[如何設定 Microsoft Intune 公司入口網站應用程式](~/apps/company-portal-app.md)。  

<!-- ########################## -->
## <a name="week-of-november-4-2019"></a>2019 年 11 月 4 日當週

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-security"></a>裝置安全性

#### <a name="security-baselines-are-supported-on-microsoft-azure-government---4062552---"></a>Microsoft Azure Government 上支援安全性基準<!-- 4062552 -->

*Microsoft Azure Government* 上裝載的 Intune 的執行個體現在可以使用[安全性基準](../protect/security-baselines.md)來協助您保護您的使用者與裝置。

<!-- ########################## -->
## <a name="week-of-october-28-2019"></a>2019 年 10 月 28 日當週

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>應用程式管理

#### <a name="improved-checklist-design-in-company-portal-app-for-android---5550857---"></a>改善了 Android 版公司入口網站應用程式中的檢查清單設計<!-- 5550857 -->  
Android 版公司入口網站應用程式中的設定檢查清單已更新為採用輕量設計與新圖示。 這些變更與針對 iOS 版公司入口網站應用程式所做的最新更新一致。 如需變更項目的並列比較，請參閱[應用程式 UI 中的新功能](whats-new-app-ui.md)。 針對已更新的註冊步驟，請參閱[使用 Android 工作設定檔註冊](/intune-user-help/enroll-device-android-work-profile)與[註冊您的 Android 裝置](/intune-user-help/enroll-device-android-company-portal)。  

#### <a name="win32-apps-on-windows-10-s-mode-devices---3747604---"></a>Windows 10 S 模式裝置上的 Win32 應用程式<!-- 3747604 --> 
您可以在 Windows 10 S 模式受控裝置上安裝並執行 Win32 應用程式。 若要這樣做，您可以使用 Windows Defender 應用程式控制 (WDAC) PowerShell 工具，為 S 模式建立一或多個補充原則。 使用「Device Guard 簽署入口網站」簽署補充原則，然後透過 Intune 上傳及散發原則。 在 Intune 中，只要選取 [用戶端應用程式]   > [Windows 10 S 補充原則]  就可以找到此功能。 如需詳細資訊，請參閱[在 S 模式裝置上啟用 Win32 應用程式](~/apps/apps-win32-s-mode.md)。

#### <a name="set-win32-app-availability-based-on-a-date-and-time---3510685---"></a>以日期和時間為基礎來設定 Win32 應用程式可用性<!-- 3510685 -->
身為系統管理員，您可以設定必要 Win32 應用程式的開始時間和期限時間。 Intune 管理延伸模組將會在開始時間開始下載並快取應用程式內容。 系統會在期限時間安裝應用程式。 針對可用的應用程式，開始時間會決定應用程式何時會顯示在公司入口網站。 如需詳細資訊，請參閱 [Intune Win32 應用程式管理](~/apps/apps-win32-app-management.md#set-win32-app-availability-and-notifications)。

#### <a name="require-device-restart-based-on-grace-period-after-win32-app-install---3136567---"></a>依據安裝 Win32 應用程式之後的寬限期要求重新啟動裝置<!-- 3136567 -->
您可以要求裝置必須在 Win32 應用程式成功安裝後重新啟動。 如需詳細資訊，請參閱 [Win32 應用程式管理 - 設定應用程式安裝詳細資料](~/apps/apps-win32-app-management.md#step-4-configure-app-installation-details)。

#### <a name="dark-mode-for-ios-company-portal---4911422---"></a>iOS 公司入口網站的深色模式<!-- 4911422 -->
iOS 公司入口網站可以使用深色模式。 使用者可以下載公司應用程式、管理其裝置，以及取得根據所選裝置設定色彩配置的 IT 支援。 iOS 公司入口網站會自動符合使用者的裝置設定，以深色或淺色模式顯示。 如需詳細資訊，請參閱[推出 iOS 版 Microsoft Intune 公司入口網站應用程式的深色模式](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/Introducing-dark-mode-on-Microsoft-Intune-Company-Portal-for-iOS/ba-p/918453) \(英文\)。 如需 iOS 公司入口網站的詳細資訊，請參閱[如何設定 Microsoft Intune 公司入口網站應用程式](~/apps/company-portal-app.md)。

#### <a name="android-company-portal-enforced-minimum-app-version---2378776---"></a>Android 公司入口網站強制要求最低應用程式版本<!-- 2378776 -->
透過使用應用程式防護原則 [最低公司入口網站版本]  ，您可以指定在使用者裝置上強制要求公司入口網站的特定最低定義版本。 此條件式啟動設定可讓您將 [封鎖存取]  、[抹除資料]  或 [警告]  作為未符合值時的可能動作。 此值的可能格式遵循模式 [主要].[次要]  、[主要].[次要].[組建]  或 [主要].[次要].[組建].[修訂]  。

若已設定 [最低公司入口網站版本]  設定，將會影響公司入口網站 5.0.4560.0 版及未來任何版本的任何使用者。 此設定不會影響使用的公司入口網站版本是早於推出此功能版本的使用者。 在裝置上使用應用程式自動更新的使用者，可能會因為使用最新的公司入口網站版本，而不會看到此功能的任何對話。 此設定僅適用於 Android 已註冊與尚未註冊之裝置的應用程式防護。 如需詳細資訊，請參閱 [Android 應用程式防護原則設定 - 條件式啟動](~/apps/app-protection-policy-settings-android.md#conditional-launch)。

<!-- vvvvvvvvvvvvvvvvvvvvvv -->

### <a name="microsoft-365-device-management"></a>Microsoft 365 裝置管理

#### <a name="introducing-endpoint-security-node-in-microsoft-365-device-management---5630102---"></a>推出 Microsoft 365 裝置管理中的端點安全性節點<!-- 5630102 -->

**端點安全性**節點現已在 Microsoft 365 裝置管理專家工作區 (https://devicemanagement.microsoft.com ) 中公開推出，它將各功能分組在一起，以保護端點，例如：

- 安全性基準：預先設定的設定群組，可協助您套用 Microsoft 所建議的已知設定群組與預設值。

- 安全性工作：利用 Microsoft Defender ATP 威脅與弱點管理 (TVM)，並使用 Intune 來修復端點弱點。

- Microsoft Defender ATP：整合 Microsoft Defender 進階威脅防護 (ATP) 來協助防止安全性缺口。

從其他適用的節點 (例如裝置) 仍然可以存取這些設定，不論您從哪裡存取與是否啟用這些功能，目前設定的狀態都會相同。

如需這些改進的詳細資訊，請參閱 Microsoft 技術社群網站上的 [Intune 客戶成功部落格文章](https://aka.ms/Endpoint_security_node) \(英文\)。

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>裝置管理

#### <a name="intune-supports-ios-11-and-later---4665324----"></a>Intune 支援 iOS 11 與更新版本<!-- 4665324  -->

Intune 註冊與公司入口網站現在支援 iOS 11 版與更新版本。 不支援舊版。

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-security"></a>裝置安全性

#### <a name="microsoft-edge-baseline-preview----3787164----"></a>Microsoft Edge 基準 (預覽)<!--  3787164  -->

我們已新增 [Microsoft Edge 設定](../protect/security-baseline-settings-edge.md)的安全性基準預覽。 

<!-- ########################## -->
## <a name="week-of-october-21-2019-1910-service-release"></a>2019 年 10 月 21 日當週 (1910 服務版本)

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="microsoft-365-device-management"></a>Microsoft 365 裝置管理

#### <a name="improved-administration-experience-in-microsoft-365-device-management---5551239---"></a>已改善 Microsoft 365 裝置管理中的管理體驗<!-- 5551239 -->

現已在 Microsoft 365 裝置管理專家工作區 ([https://devicemanagement.microsoft.com](https://devicemanagement.microsoft.com)) 中推出重新整理且簡化的管理體驗，包括：

- **已更新的導覽**：您會發現第一層導覽已簡化，並以邏輯方式將功能分組。
- **新的平台篩選器**：您可以在 [裝置及應用程式] 頁面上選取單一平台，只顯示所選平台的原則與應用程式。
- **新的首頁**：在新的首頁上快速查看服務健康情況、租用戶狀態、新聞等等。

如需這些改進的詳細資訊，請參閱 Microsoft 技術社群網站上的 [Enterprise Mobility + Security 部落格文章](https://go.microsoft.com/fwlink/?linkid=2109094) \(英文\)。

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>應用程式管理

#### <a name="add-mobile-threat-defense-apps-to-unenrolled-devices---3005337---"></a>將 Mobile Threat Defense 應用程式新增至尚未註冊的裝置<!-- 3005337 -->
您可以建立會根據裝置健康情況，而封鎖或選擇性地抹除使用者公司資料的 Intune 應用程式防護原則。 裝置的健康情況是使用您選擇的 Mobile Threat Defense (MTD) 解決方案來判斷的。 此功能目前使用 Intune 已註冊的裝置作為裝置合規性設定。 透過此新功能，我們將來自 Mobile Threat Defense 廠商的威脅偵測，延伸到在尚未註冊的裝置上運作。 在 Android 上，此功能需要裝置上有最新版公司入口網站。 在 iOS 上，當應用程式整合最新的 Intune SDK (v 12.0.15+) 時，就可以使用此功能。 當第一個應用程式採用最新的 Intune SDK 時，我們會更新「新功能」主題。 其餘應用程式將會輪流推出。 如需詳細資訊，請參閱[使用 Intune 建立 Mobile Threat Defense 應用程式防護原則](~/protect/mtd-app-protection-policy.md)。

### <a name="device-configuration"></a>裝置設定

#### <a name="new-device-firmware-configuration-interface-profile-for-windows-10-and-later-devices-public-preview---2266073----"></a>適用於 Windows 10 和更新版本裝置的新裝置韌體設定介面設定檔 (公開預覽)<!-- 2266073  -->

在 Windows 10 和更新版本上，您可以建立裝置組態設定檔來控制設定和功能 (**裝置組態** > **設定檔** > **建立設定檔** > **Windows10 和更新版本** (針對平台))。 在此更新中，有新的裝置韌體設定介面設定檔類型，可讓 Intune 管理 UEFI (BIOS) 設定。

如需這項功能的詳細資訊，請參閱[在 Microsoft Intune 中的 Windows 裝置上使用 DFCI 設定檔](../configuration/device-firmware-configuration-interface-windows.md)。

適用於：
- 支援韌體上的 Windows 10 RS5 (1809) 和更新版本

### <a name="device-enrollment"></a>裝置註冊

#### <a name="toggle-to-only-show-enrollment-status-page-on-devices-provisioned-by-out-of-box-experience-oobe--3959566--"></a>切換以在使用全新體驗 (OOBE) 佈建的裝置上僅顯示 [註冊狀態頁面]<!--3959566-->
您現在可以選擇在 Autopilot OOBE 所佈建的裝置上只顯示 [註冊狀態頁面]。

若要查看新的切換開關，請選擇 [Intune]   > [裝置註冊]   > [Windows 註冊]   > [註冊狀態頁面]   > [建立設定檔]   > [設定]   > [僅顯示由全新體驗 (OOBE) 佈建的裝置頁面]  。


<!-- ########################## -->
## <a name="week-of-october-14-2019"></a>2019 年 10 月 14 日當週

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>應用程式管理 

#### <a name="available-google-play-app-reporting-for-android-work-profiles---3041956-----"></a>報告 Android 工作設定檔的可用 Google Play 應用程式<!-- 3041956   -->
針對安裝在 Android Enterprise 工作設定檔、專用且完全受控的裝置上的可用應用程式，您可以檢視應用程式安裝狀態，以及受控 Google Play 應用程式的安裝版本。 如需詳細資訊，請參閱[如何監視應用程式保護原則](~/apps/app-protection-policies-monitor.md)、[使用 Intune 管理 Android 工作設定檔裝置](~/enrollment/android-enterprise-overview.md)及[受控的 Google Play 應用程式類型](~/apps/apps-add-android-for-work.md#managed-google-play-app-types)。

#### <a name="microsoft-edge-version-77-and-later-for-windows-10-and-macos-public-preview---3872025-4678761----"></a>適用於 Windows 10 和 macOS (公開預覽) 的 Microsoft Edge 77 版和更新版本<!-- 3872025, 4678761  -->
Microsoft Edge 77 版與更新版本將可部署至執行 Windows 10 與 macOS 的電腦。 

公開預覽針對 Windows 10 提供 **Dev** 和 **Beta** 通道，以及針對 macOS 提供 **Beta** 通道。 部署僅限英文 (EN)，不過，終端使用者可以在瀏覽器中的 [設定]   > [語言]  下變更顯示語言。 Microsoft Edge 是一個 Win32 應用程式，安裝在系統內容和類似的架構 (x86 OS 上的 x86 應用程式，以及 x64 OS 上的 x64 應用程式) 上。 此外，瀏覽器的自動更新預設會 [開啟]  ，而且無法解除安裝 Microsoft Edge。 如需詳細資訊，請參閱[將適用於 Windows 10 的 Microsoft Edge 新增至 Microsoft Intune](~/apps/apps-windows-edge.md) 和 [Microsoft Edge 文件](https://go.microsoft.com/fwlink/?linkid=2103823) \(英文\)。

#### <a name="update-to-app-protection-ui-and-ios-app-provisioning-ui---4102027-4102029-----"></a>應用程式保護 UI 和 iOS 應用程式佈建 UI 的更新<!-- 4102027, 4102029   -->
在 Intune 中用來建立和編輯應用程式保護原則和 iOS 應用程式佈建設定檔的 UI 已更新。 UI 變更包括：
- 使用壓縮成單一刀鋒視窗的精靈樣式格式簡化體驗。 
- 針對建立流程的更新，以包含指派。
- 檢視屬性 (建立新的原則之前) 或編輯屬性時所設定之所有內容的摘要頁面。 此外，當編輯屬性時，摘要只會顯示正在編輯的屬性類別中的項目清單。

如需詳細資訊，請參閱[如何建立及指派應用程式保護原則](~/apps/app-protection-policies.md)與[使用 iOS 應用程式佈建設定檔](~/apps/app-provisioning-profile-ios.md)。

#### <a name="intune-guided-scenarios---4850318-4831296-3610611----"></a>Intune 引導式案例<!-- 4850318, 4831296, 3610611  -->
Intune 現在提供引導式案例，協助您在 Intune 中完成一項特定工作或一組工作。 引導式案例是以一個端對端使用案例為中心的一系列自訂步驟 (工作流程)。 常見案例是根據組織中系統管理員、使用者或裝置所扮演的角色來定義。 這些工作流程通常需要一組仔細協調的設定檔、設定、應用程式和安全性控制項，以提供最佳的使用者體驗和安全性。 新的引導式案例包括：
- [部署適用於行動裝置的 Microsoft Edge](~/fundamentals/guided-scenarios-edge.md)
- [保護 Microsoft Office 行動應用程式](~/fundamentals/guided-scenarios-office-mobile.md) 
- [雲端管理的新式桌面](~/fundamentals/guided-scenarios-cloud-managed-pc.md)

如需詳細資訊，請參閱 [Intune 引導式案例概觀](guided-scenarios-overview.md)。

#### <a name="additional-app-configuration-variable-available---4969237-----"></a>其他可用的應用程式設定變數<!-- 4969237   -->
建立應用程式設定原則時，您可以將 `AAD Device ID` 設定變數包含在您的組態設定中。 在 Intune 中，選取 [用戶端應用程式]   > [應用程式設定原則]   > [新增]  。 輸入設定原則詳細資料，然後選取 [組態設定]  以檢視 [組態設定]  刀鋒視窗。 如需詳細資訊，請參閱[適用於受控 Android Enterprise 裝置的應用程式設定原則 - 使用設定設計工具](~/apps/app-configuration-policies-use-android.md#use-the-configuration-designer)。


#### <a name="create-groups-of-management-objects-called-policy-sets---3762880----"></a>建立稱為原則集合的管理物件群組<!-- 3762880  -->
原則集合可讓您建立現有管理實體的參考組合；這些實體必須以單一概念單元進行識別、設為目標及監視。 原則集合不會取代現有的概念或物件。 您可以繼續在 Intune 中指派個別物件，而且可以參考個別物件作為原則集合的一部分。 因此，對那些個別物件所做的任何變更都會反映在原則集合中。  在 Intune 中，您將選取 [原則集合]   > [建立]  建立新的原則集合。 

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-configuration"></a>裝置設定

#### <a name="ui-update-for-creating-and-editing-windows-10-update-rings---4099089-----------"></a>建立和編輯 Windows 10 更新通道的 UI 更新<!-- 4099089         -->
我們已針對 Intune 更新[建立和編輯 Windows 10 更新通道的 UI 體驗](../protect/windows-update-for-business-configure.md#create-and-assign-update-rings)。 UI 的變更包括：  
- 壓縮成單一刀鋒視窗的精靈樣式格式，與先前在設定更新通道時看到的刀鋒視窗蔓延不一樣。   
- 在完成通道的初始設定之前，修改後的工作流程包含 [指派]。
- [摘要] 頁面可用來檢查您所做的所有設定，然後再儲存和部署新的更新通道。 編輯更新通道時，摘要僅顯示在您所編輯的屬性類別內設定的項目清單。

#### <a name="ui-update-for-creating-and-editing-ios-software-update-policy---4099090---------"></a>用於建立和編輯 iOS 軟體更新原則的 UI 更新<!-- 4099090       --> 
我們已針對 Intune 更新[建立](../protect/software-updates-ios.md#configure-the-policy)和[編輯](../protect/software-updates-ios.md#edit-a-policy) iOS 軟體更新原則的 UI 體驗。  UI 的變更包括：  
- 壓縮成單一刀鋒視窗的精靈樣式格式，與先前在設定更新原則時看到的刀鋒視窗蔓延不一樣。   
- 在完成原則的初始設定之前，修改後的工作流程包含 [指派]。
- 在儲存和部署新原則之前，您可以用來檢閱所有設定的 [摘要] 頁面。 編輯原則時，摘要僅顯示在您所編輯的屬性類別內設定的項目清單。

#### <a name="engaged-restart-settings-are-removed-from-windows-update-rings----4464404---wnready-----"></a>Windows Update 通道的 [預約重新啟動] 設定已移除<!--  4464404   WNReady   -->
如先前所宣佈的那樣，Intune 的 Windows 10 更新通道現在[支援期限設定](../protect/windows-update-settings.md)，並且不再支援 [預約重新啟動]  。 當您在 Intune 中設定或管理更新通道時，將無法再使用 [預約重新啟動]  設定。  

這種變更會與最近的 [Windows 服務變更](https://docs.microsoft.com//windows/whats-new/whats-new-windows-10-version-1903#servicing)一致，並且在執行 Windows 10 1903 或更高版本的裝置上，[期限]  取代了 [預約重新啟動]  設定。

#### <a name="prevent-installation-of-apps-from-unknown-sources-on-android-enterprise-work-profile-devices---4760025-----"></a>防止在 Android Enterprise 工作設定檔裝置上安裝來自不明來源的應用程式<!-- 4760025   -->
在 Android Enterprise 工作設定檔裝置上，使用者無法從不明來源安裝應用程式。 在此更新中，有一個新的設定 - **禁止在個人設定檔中從不明來源安裝應用程式**。 根據預設，此設定可防止使用者從不明來源側載應用程式到裝置上的個人設定檔。

若要查看您可以設定的設定，請前往[使用 Intune 來允許或限制功能的 Android Enterprise 裝置設定](../configuration/device-restrictions-android-for-work.md)。

適用於：
- Android Enterprise 工作設定檔

#### <a name="create-a-global-http-proxy-on-android-enterprise-device-owner-devices---4816339-----"></a>在 Android Enterprise 裝置擁有者裝置上建立全域 HTTP Proxy<!-- 4816339   -->
在 Android Enterprise 裝置上，您可以設定全域 HTTP Proxy 以符合組織的網頁瀏覽標準 ([裝置組態]   > [設定檔]   > [建立設定檔]   > [Android Enterprise]  (針對平台) > [裝置擁有者] > [裝置限制]  (針對設定檔類型) > [連線]  )。 一旦設定之後，所有 HTTP 流量都會使用此 Proxy。

若要設定此功能，並查看您設定的所有設定，請前往[使用 Intune 來允許或限制功能的 Android Enterprise 裝置設定](../configuration/device-restrictions-android-for-work.md)。

適用於：
- Android Enterprise 裝置擁有者

#### <a name="connect-automatically-setting-is-removed-in-wi-fi-profiles-on-android-device-administrator-and-android-enterprise---5021055-----"></a>Android 裝置系統管理員和 Android Enterprise 的 Wi-Fi 設定檔中已移除 [自動連線] 設定<!-- 5021055   -->
在 Android 裝置系統管理員和 Android Enterprise 裝置上，您可以建立 Wi-Fi 設定檔來設定不同的設定 ([裝置組態]   > [設定檔]   > [建立設定檔]   > [Android 裝置系統管理員]  或 [Android Enterprise]  (針對平台) > [Wi-Fi]  (針對設定檔類型))。 在此更新中，會移除 [自動連線]  設定，因為它[不受 Android 支援](https://developer.android.com/reference/android/net/wifi/WifiManager.html#enableNetwork%28int%2c%20boolean%29) \(英文\)。 

如果您在 Wi-Fi 設定檔中使用此設定，您可能已注意到 [自動連線]  無法使用。 您不需要採取任何動作，但請注意，Intune 使用者介面中已移除這項設定。

若要查看目前的設定，請前往 [Android Wi-Fi 設定](../configuration/wi-fi-settings-android.md)或 [Android Enterprise Wi-Fi 設定](../configuration/wi-fi-settings-android-enterprise.md)。

適用於：
- Android 裝置管理員 
- Android 企業


#### <a name="new-device-configuration-settings-for-supervised-ios-and-ipados-devices---5199328-----"></a>受監督 iOS 和 iPadOS 裝置的新裝置組態設定<!-- 5199328   -->
在 iOS 和 iPadOS 裝置上，您可以建立設定檔以限制裝置上的功能和設定 ([裝置組態]   > [設定檔]   > [建立設定檔]   > [iOS/iPadOS]  (針對平台) > [裝置限制]  (針對設定檔類型))。 在此更新中，有您可以控制的新設定： 
- 存取檔案應用程式中的網路磁碟機  
- 存取檔案應用程式中的 USB 磁碟機 
- Wi-Fi 一律開啟 

若要查看這些設定，請前往[使用 Intune 來允許或限制功能的 iOS 裝置設定](../configuration/device-restrictions-ios.md)。

適用於：
- iOS 13.0 與更新版本
- iPadOS 13.0 和更新版本

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-enrollment"></a>裝置註冊

#### <a name="specify-which-android-device-operating-system-versions-enroll-with-work-profile-or-device-administrator-enrollment---4350697-----"></a>指定使用工作設定檔註冊或裝置系統管理員註冊進行註冊的 Android 裝置作業系統版本<!-- 4350697   -->
使用 Intune 裝置類型限制時，您可以使用裝置的 OS 版本來指定哪些使用者裝置將使用 Android Enterprise 工作設定檔註冊或 Android 裝置系統管理員註冊。  如需詳細資訊，請參閱[設定註冊限制](../enrollment/enrollment-restrictions-set.md)。

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>裝置管理

#### <a name="new-restrictions-for-renaming-windows-devices---3478938----"></a>重新命名 Windows 裝置的新限制<!-- 3478938  -->
重新命名 Windows 裝置時，您必須遵循新規則：
- 15 個字元或更少 (必須小於或等於 63 個位元組，不包括尾端的 Null 字元)
- 非 Null 或空字串
- 允許的 ASCII：字母 (a-z, A-Z)、數字 (0-9) 和連字號
- 允許的 Unicode：字元 >= 0x80，必須是有效的 UTF8，必須是 IDN 可映射 (也就是繼 RtlIdnToNameprepUnicode 之後；請參閱 RFC 3492)
- 名稱不能僅包含數字
- 名稱中不能有空格
- 不允許的字元：{ | } ~ [ \ ] ^ ' : ; < = > ? & @ ! " # $ % ` ( ) + / , . _ *)

 如需詳細資訊，請參閱[在 Intune 中重新命名裝置](../remote-actions/device-rename.md)。

### <a name="new-android-report-on-devices-overview-page---4924364---"></a>[裝置概觀] 頁面上的新 Android 報告<!-- 4924364 -->
[裝置概觀] 頁面的新報告會顯示每個裝置管理解決方案中已註冊的 Android 裝置數目。 此圖表顯示工作設定檔、完全受控、專用和裝置系統管理員註冊的裝置計數。 若要查看報告，請選擇 [Intune]   > [裝置]   > [概觀]  。

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-security"></a>裝置安全性

#### <a name="pkcs-certificates-for-macos---1333650---------"></a>適用於 macOS 的 PKCS 憑證<!-- 1333650       -->
您現在可以[搭配 macOS 使用 PKCS 憑證](../protect/certficates-pfx-configure.md#create-a-pkcs-certificate-profile)。 您可以選取 [PKCS 憑證] 作為 macOS 的設定檔類型，並部署具有[自訂主體和主體別名欄位](../protect/certficates-pfx-configure.md#subject-name-format-for-macos)的使用者和裝置憑證。  

macOS 的 PKCS 憑證也支援新的設定 [允許所有應用程式存取]  。 使用這項設定，您可以啟用所有相關聯的應用程式存取憑證的私密金鑰。  如需此設定的詳細資訊，請參閱位於 https://developer.apple.com/business/documentation/Configuration-Profile-Reference.pdf 的 Apple 文件。

####   <a name="derived-credentials-to-provision-ios-mobile-devices-with-certificates----1736036-1736037-1772050-2777333-----------"></a>使用憑證佈建 iOS 行動裝置的衍生認證<!--  1736036, 1736037, 1772050, 2777333         -->  
Intune 支援使用[衍生認證](../protect/derived-credentials.md)作為驗證方法，以及適用於 iOS 裝置的 S/MIME 簽署和加密。 衍生認證是*國家標準暨技術研究院 (NIST) 800-157* 標準的實作，用於將憑證部署至裝置。  

衍生認證仰賴個人識別驗證 (PIV) 或一般存取卡 (CAC)，如智慧卡。 若要取得其行動裝置的衍生認證，使用者必須從公司入口網站應用程式中啟動，並遵循您所使用之提供者獨有的註冊工作流程。  對於所有提供者來說，共同的要求是在電腦上使用智慧卡向衍生認證提供者進行驗證。 該提供者接著會將憑證發行至衍生自使用者智慧卡的裝置。  

Intune 支援下列衍生認證提供者：
- DISA Purebred
- Entrust Datacard
- Intercede

您可以使用衍生認證作為 VPN、Wi-Fi 和電子郵件的裝置組態設定檔的驗證方法。 您也可以使用它們進行應用程式驗證和 S/MIME 簽署和加密。  

如需有關標準的詳細資訊，請參閱位於 www.nccoe.nist.gov 的 [PIV 衍生認證](https://www.nccoe.nist.gov/projects/building-blocks/piv-credentials) \(英文\)。

#### <a name="use-graph-api-to-specify-a-on-premises-user-principal-name-as-a-variable-for-scep-certificates----5437939----------"></a>使用圖形 API 指定內部部署使用者主體名稱作為 SCEP 憑證的變數<!--  5437939        -->  
當您使用 [Intune 圖形 API](https://docs.microsoft.com/graph/api/resources/intune-graph-overview?view=graph-rest-1.0) 時，您可以將 onPremisesUserPrincipalName 指定為 SCEP 憑證的主體別名 (SAN) 的變數。



<!-- ########################## -->

## <a name="week-of-september-23-2019"></a>2019 年 9 月 23 日當週

#### <a name="ios-user-enrollment-in-preview---4817900---"></a>預覽中的 iOS 使用者註冊<!-- 4817900 -->
Apple 的 iOS 13.1 版本包括使用者註冊，這是適用於 iOS 裝置的新形式輕量型管理。 它可用來代替個人擁有之裝置的裝置註冊或自動裝置註冊 (先前為「裝置註冊計劃」)。 Intune 的預覽藉由讓您能夠執行下列動作來支援此功能集：

- 將使用者註冊的目標設定為使用者群組。
- 讓終端使用者在註冊其裝置時，能夠在較輕量的使用者註冊或更強大的裝置註冊之間選取。

從 2019 年 9 月 24 日開始，隨著 iOS 13.1 的發行，我們正在將這些更新推出給所有客戶，預計會在下週末完成。
適用於：

iOS 13.1 與更新版本

#### <a name="intune-support-for-ipados-and-ios-131-devices--5439574--"></a>適用於 iPadOS 與 iOS 13.1 裝置的 Intune 支援<!--5439574-->
Intune 現在支援同時管理 iPadOS 與 iOS 13.1 裝置。 如需詳細資訊，請參閱[這篇部落格文章](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Microsoft-Intune-Support-for-iOS-13-1-and-iPadOS/ba-p/873094)。

<!-- ########################## -->

## <a name="week-of-september-16-2019-1909-service-release"></a>2019 年 9 月 16 日當週 (1909 服務版本)

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>應用程式管理 

#### <a name="managed-google-play-private-lob-apps---1464182----"></a>受控的 Google Play 私人 LOB 應用程式<!-- 1464182  -->
Intune 現在讓 IT 管理員能夠透過內嵌於 Intune 主控台中的 iframe，將私人 Android LOB 應用程式發佈至受控的 Google Play。  以前，IT 管理員需要將 LOB 應用程式直接發佈至 Google 的 Play 發佈主控台，而這需要數個步驟且相當耗時。 這項新功能可讓您使用一組最少的步驟來輕鬆發佈 LOB 應用程式，而不需離開 Intune 主控台。  管理員將不再需要以 Google 的開發人員身分手動註冊，也不再需要向 Google 支付 25 美元的註冊費用。  任何使用受控 Google Play 的 Android Enterprise 管理案例都可利用這項功能 (工作設定檔、專用、完全受控及未註冊的裝置)。 從 Intune，選取 [用戶端應用程式]   > [應用程式]   > [新增]  。 接著，從 [應用程式類型]  清單中，選取 [受控的 Google Play]  。 如需受控 Google Play 應用程式的詳細資訊，請參閱[使用 Intune 將受控 Google Play 應用程式新增至 Android Enterprise 裝置](../apps/apps-add-android-for-work.md)。

#### <a name="windows-company-portal-experience---1473353-3598357---"></a>Windows 公司入口網站體驗<!-- 1473353, 3598357 -->
Windows 公司入口網站正在更新。 您將能夠在 Windows 公司入口網站中的 [應用程式] 頁面上使用多個篩選。 [裝置詳細資料] 頁面也會使用已改進的使用者體驗進行更新。 我們正在將這些更新推出給所有客戶，預計會在下周末完成。

#### <a name="macos-support-for-web-apps---3174427---"></a>Web 應用程式的 macOS 支援<!-- 3174427 -->
Web 應用程式 (可讓您新增 Web URL 的捷徑) 可以使用 macOS 公司入口網站安裝到 Dock。 終端使用者可以在 macOS 公司入口網站中，從 Web 應用程式的 [應用程式詳細資料] 頁面存取 [安裝]  動作。 如需 **Web 連結**應用程式類型的詳細資訊，請參閱[將應用程式新增至 Microsoft Intune](../apps/apps-add.md)，以及[將 Web 應用程式新增至 Microsoft Intune](../apps/web-app.md)。

#### <a name="macos-support-for-vpp-apps---3173501----"></a>VPP 應用程式的 macOS 支援<!-- 3173501  -->
使用 Apple Business Manager 購買的 macOS 應用程式，會在 Intune 中的 Apple VPP 權杖同步處理時顯示在主控台中。 您可以使用 Intune 主控台為群組指派、撤銷和重新指派裝置和使用者型授權。 Microsoft Intune 可協助您管理已購買供公司使用的 VPP 應用程式，方法是：

- 從應用程式市集報告授權資訊。
- 追蹤您已經使用多少個授權。
- 協助您避免安裝超過所擁有數目的應用程式複本。

如需有關 Intune 與 VPP 的詳細資訊，請參閱[使用 Microsoft Intune 管理大量採購的應用程式與書籍](../apps/vpp-apps.md)。

#### <a name="managed-google-play-iframe-support---2871756----"></a>受控的 Google Play iframe 支援<!-- 2871756  -->
Intune 現在支援透過受控的 Google Play iframe，直接在 Intune 主控台中新增和管理網頁連結。  這讓 IT 管理員能夠提交 URL 和圖示圖形，然後將那些連結部署到裝置，就像一般的 Android 應用程式一樣。 任何使用受控 Google Play 的 Android Enterprise 管理案例都可利用這項功能 (工作設定檔、專用、完全受控及未註冊的裝置)。 從 Intune，選取 [用戶端應用程式]   > [應用程式]   > [新增]  。 接著，從 [應用程式類型]  清單中，選取 [受控的 Google Play]  。 如需受控 Google Play 應用程式的詳細資訊，請參閱[使用 Intune 將受控 Google Play 應用程式新增至 Android Enterprise 裝置](../apps/apps-add-android-for-work.md)。

#### <a name="silently-install-android-lob-apps-on-zebra-devices---4252734----"></a>在 Zebra 裝置上以無訊息方式安裝 Android LOB 應用程式<!-- 4252734  -->
在 [Zebra 裝置](../configuration/android-zebra-mx-overview.md)上安裝 Android 企業營運 (LOB) 應用程式時，不會提示您下載並安裝 LOB 應用程式，您將能夠以無訊息方式安裝該應用程式。 在 Intune 中，選取 [用戶端應用程式]   > [應用程式]   > [新增]  。 在 [新增應用程式]  窗格中，選取 [企業營運應用程式]  。 如需詳細資訊，請參閱[將 Android 企業營運應用程式新增至 Microsoft Intune](../apps/lob-apps-android.md)。

目前，在下載 LOB 應用程式之後，使用者的裝置上將出現**下載成功**通知。 只有點選通知陰影中的 [全部清除]  ，才能關閉通知。 即將發行的版本中將會修正此通知問題，而且安裝將以完全無訊息方式執行，且不會顯示任何視覺指標。

#### <a name="read-and-write-graph-api-operations-for-intune-apps---5031704----"></a>Intune 應用程式的讀取和寫入圖形 API 作業<!-- 5031704  -->
應用程式可以使用應用程式身分識別，搭配讀取和寫入作業來呼叫 Intune 圖形 API，而無需使用者認證。 如需有關存取「適用於 Intune 的 Microsoft Graph API」的詳細資訊，請參閱[在 Microsoft Graph 中使用 Intune](https://docs.microsoft.com/graph/api/resources/intune-graph-overview?view=graph-rest-1.0) \(英文\)。

#### <a name="protected-data-sharing-and-encryption-for-intune-app-sdk-for-ios---3586942----"></a>針對適用於 iOS 的 Intune App SDK 共用和加密受保護資料<!-- 3586942  -->
適用於 iOS 的 Intune App SDK 將會在應用程式保護原則啟用加密時，使用 256 位元的加密金鑰。 所有應用程式都將需要有 SDK 8.1.1 版，才能共用受保護資料。

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-configuration"></a>裝置設定

#### <a name="support-for-ikev2-vpn-profiles-for-ios---1943438-----"></a>支援 iOS 版的 IKEv2 VPN 設定檔<!-- 1943438   -->
在此更新中，您可以使用 IKEv2 通訊協定，來建立 iOS 原生 VPN 用戶端的 VPN 設定檔。 IKEv2 是 [裝置設定]   > [設定檔]   > [建立設定檔]   > [iOS]  作為平台 > [VPN]  作為設定檔類型 > [連線類型]  中的新連線類型。

這些 VPN 設定檔會設定原生 VPN 用戶端，因此，不會安裝任何 VPN 用戶端應用程式，或將其推送至受控裝置。 這項功能需要向 Intune 註冊裝置 (MDM 註冊)。

若要查看您目前可以設定的 VPN 設定，請移至[在 iOS 裝置上設定 VPN 設定](../configuration/vpn-settings-ios.md)。

適用於：
- iOS

#### <a name="device-features-device-restrictions-and-extension-profiles-for-ios-and-macos-settings-are-shown-by-enrollment-type---4886161-----"></a>適用於 iOS 和 macOS 設定的裝置功能、裝置限制及擴充功能設定檔會依註冊類型顯示<!-- 4886161   -->

在 Intune 中，您會為 iOS 和 macOS 裝置建立設定檔 ([裝置設定]   > [設定檔]   > [建立設定檔]   > [iOS]  或 [macOS]  作為平台 > [裝置功能]  、[裝置限制]  或 [擴充功能]  作為設定檔類型)。 

在此更新中，Intune 入口網站中的可用設定會依其適用的註冊類型分類：

- iOS
  - 使用者註冊
  - 裝置註冊
  - 自動裝置註冊 (受監督)
  - 所有註冊類型

- macOS
  - 使用者已核准
  - 裝置註冊
  - 自動裝置註冊
  - 所有註冊類型

適用於：
- iOS

#### <a name="new-voice-control-settings-for-supervised-ios-devices-running-in-kiosk-mode---4892835-----"></a>以 kiosk 模式執行之受監督 iOS 裝置的新語音控制設定<!-- 4892835   -->
在 Intune 中，您可以建立原則來執行受監督的 iOS 裝置作為 kiosk 或專用裝置 ([裝置設定]   > [設定檔]   > [建立設定檔]   > [iOS]  作為平台 > [裝置限制]  作為設定檔類型 > [Kiosk]  )。

在此更新中，有您可以控制的新設定：
- **語音控制**：在 kiosk 模式中，啟用裝置上的語音控制。
- **修改語音控制**：允許使用者在 kiosk 模式中變更裝置上的語音控制設定。

若要查看目前的設定，請移至 [iOS Kiosk 設定](../configuration/device-restrictions-ios.md#kiosk)。

適用於：
- iOS 13.0 與更新版本

#### <a name="use-single-sign-on-for-apps-and-websites-on-your-ios-and-macos-devices---4893175-----"></a>在 iOS 和 macOS 裝置上針對應用程式和網站使用單一登入<!-- 4893175   -->
在此更新中，有一些適用於 iOS 和 macOS 裝置的新單一登入設定 ([裝置設定]   > [設定檔]   > [建立設定檔]   > [iOS]  或 [macOS]  作為平台 > [裝置功能]  作為設定檔類型)。

使用這些設定來設定單一登入體驗，特別是針對使用 Kerberos 驗證的應用程式和網站。 您可以在一般認證單一登入應用程式擴充功能，以及 Apple 的內建 Kerberos 擴充功能之間進行選擇。

若要查看您目前可以設定的裝置功能，請參閱 [iOS 裝置功能](../configuration/ios-device-features-settings.md)和 [macOS 裝置功能](../configuration/macos-device-features-settings.md)。

適用於：
- iOS 13.0 與更新版本
- macOS 10.15 與更新版本

#### <a name="associate-domains-to-apps-on-macos-1015-devices---4898079-----"></a>將網域關聯至 macOS 10.15 及以上版本裝置上的應用程式<!-- 4898079   -->
在 macOS 裝置上，您可以設定不同功能，並使用原則來將這些功能推送至裝置 ([裝置設定]   > [設定檔]   > [建立設定檔]   > [macOS]  作為平台 > [裝置功能]  作為設定檔類型)。 在此更新中，您可以將網域關聯至應用程式。 這項功能可協助與您應用程式相關的網站共用認證，並可搭配 Apple 的單一登入擴充功能、通用連結及密碼自動填入使用。 

若要查看目前您可以設定的功能，請參閱 [Intune 中的 macOS 裝置功能設定](../configuration/macos-device-features-settings.md)。

適用於：
- macOS 10.15 與更新版本

#### <a name="use-itunes-and-apps-in-the-itunes-app-store-url-when-showing-or-hiding-apps-on-ios-supervised-devices---4928474-----"></a>顯示或隱藏 iOS 受監督裝置上的應用程式時，在 iTunes App Store URL 中使用 "iTunes" 與 "apps"<!-- 4928474   --> 
在 Intune 中，您可以建立原則來顯示或隱藏受監督 iOS 裝置上的應用程式 ([裝置設定]   > [設定檔]   > [建立設定檔]   > [iOS]  作為平台 > [裝置限制]  作為設定檔類型 > [顯示或隱藏應用程式]  )。 

您可以輸入 iTunes App Store URL，例如 `https://itunes.apple.com/us/app/work-folders/id950878067?mt=8`。 在此更新中，`apps` 和 `itunes` 都可在 URL 中使用，例如：
- `https://itunes.apple.com/us/app/work-folders/id950878067?mt=8`
- `https://apps.apple.com/us/app/work-folders/id950878067?mt=8`

如需這些設定的詳細資訊，請參閱[顯示或隱藏應用程式](../configuration/device-restrictions-ios.md#show-or-hide-apps)。

適用於：
- iOS

#### <a name="windows-10-compliance-policy-password-type-values-are-clearer-and-match-csp---5138985---"></a>Windows 10 合規性政策密碼類型值更清楚且符合 CSP<!-- 5138985 -->
在 Windows 10 裝置上，您可以建立需要特定密碼功能的合規性政策 ([裝置合規性]   > [原則]   > [建立原則]   > [Windows 10 及更新版本]  作為平台 > [系統安全性]  )。 在此更新中：
- [密碼類型]  值更清楚，且已更新以符合 [DeviceLock/AlphanumericDevicePasswordRequired CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock#devicelock-alphanumericdevicepasswordrequired) \(部分機器翻譯\)。
- [密碼到期 (天數)]  設定已更新以允許 1-730 天的值。 

如需 Windows 10 合規性設定的詳細資訊，請參閱[透過 Windows 10 及更新版本的設定將裝置標示為符合規範或不符合規範](../protect/compliance-policy-create-windows.md)。 

適用於：
- Windows 10 及更新版本

 #### <a name="updated-ui-for-configuring-microsoft-exchange-on-premises-access---4092920---"></a>已更新用來設定 Microsoft Exchange 內部部署存取的 UI<!-- 4092920 -->  
我們已更新主控台，讓您可在其中[設定存取 Microsoft Exchange 內部部署存取](../protect/conditional-access-exchange-create.md)。 適用於 Exchange 內部部署存取的所有設定現在可在您「啟用 Exchange 內部部署存取控制」  的相同主控台窗格中取得。  

#### <a name="allow-or-restrict-adding-app-widgets-to-the-home-screen-on-android-enterprise-work-profile-devices---1109650----"></a>允許或限制將應用程式 Widget 新增至 Android Enterprise 工作設定檔裝置上的主畫面<!-- 1109650  --> 
在 Android Enterprise 裝置上，您可以在工作設定檔中設定功能 ([裝置設定]   > [設定檔]   > [建立設定檔]   > [Android Enterprise]  作為平台 > [僅限工作設定檔] > [裝置限制]  作為設定檔類型)。 在此更新中，您可以讓使用者將工作設定檔應用程式所公開的 Widget 新增至裝置主畫面。

若要查看您可以設定的設定，請參閱[使用 Intune 來允許或限制功能的 Android Enterprise 裝置設定](../configuration/device-restrictions-android-for-work.md)。

適用於：
- Android Enterprise 工作設定檔

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-enrollment"></a>裝置註冊

#### <a name="new-tenants-will-default-away-from-android-device-administrator-management---4869790-----"></a>新的租用戶預設將離開 Android 裝置管理員管理<!-- 4869790   -->
Android 的裝置系統管理員功能已被 Android Enterprise 取代。 因此，建議您改用 Android Enterprise 來進行新的註冊。 在未來的更新中，新的租用戶將需要在 Android 註冊中完成下列必要條件步驟，才能使用裝置系統管理員管理：移至 [Intune]   > [裝置註冊]   > [Android 註冊]   > [具有裝置系統管理權限之個人及屬公司擁有的裝置]   > [使用裝置系統管理員來管理裝置]  。

現有的租用戶將在其環境中保持不變。

如需 Intune 中 Android 裝置系統管理員的詳細資訊，請參閱 [Android 裝置系統管理員註冊](https://docs.microsoft.com/intune/android-enroll-device-administrator)。

#### <a name="list-of-dep-devices-associated-with-a-profile---5012045-idmiss---"></a>與設定檔相關聯的 DEP 裝置清單<!-- 5012045 idmiss -->
您現在可以看到與設定檔相關聯的 Apple 自動裝置註冊計劃 (DEP) 裝置的分頁清單。 您可以從清單中的任何頁面搜尋此清單。 若要查看清單，請移至 [Intune]   > [裝置註冊]   > [Apple 註冊]   > [註冊計劃權杖]  > 選擇權杖 > [設定檔]  > 選擇設定檔 > [指派的裝置]  (位於 [監視]  下方)。

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>裝置管理

#### <a name="more-android-fully-managed-support---3464667-4631425-4631440-5227935-4062195-----"></a>更多 Android 完全受控支援<!-- 3464667, 4631425, 4631440, 5227935, 4062195   -->
我們新增了下列適用於 Android 完全受控裝置的支援：

- 適用於完全受控 Android 的 SCEP 憑證，可用來在以裝置擁有者身分管理的裝置上進行憑證驗證。 公司設定檔裝置上已經支援 SCEP 憑證。  使用適用於裝置擁有者的 SCEP 憑證，您將能夠： <!-- 5227935 -->
    - 在 Android Enterprise 的 DO 區段下方建立 SCEP 設定檔
    - 將 SCEP 憑證連結至 DO Wi-Fi 設定檔以進行驗證
    - 將 SCEP 憑證連結至 DO VPN 設定檔以進行驗證
    - 將 SCEP 憑證連結至 DO Email 設定檔以進行驗證 (透過 AppConfig)
- Android Enterprise 裝置上支援系統應用程式。 在 Intune 中，藉由選取 [用戶端應用程式]   > [應用程式]   > [新增]  ，來新增 Android Enterprise 系統應用程式。 在 [應用程式類型]  清單中，選取 [Android Enterprise 系統應用程式]  。 如需詳細資訊，請參閱[將 Android Enterprise 系統應用程式新增至 Microsoft Intune](../apps/apps-ae-system.md)。 <!-- 4062195 -->
- 在 [裝置合規性]   > [Android Enterprise]   > [裝置擁有者]  中，您可以建立合規性政策來設定 Google SafetyNet 證明層級。   <!-- 4631425 -->
- 在 Android Enterprise 完全受控裝置上，支援 Mobile Threat Defense 提供者。 在 [裝置合規性]   > [Android Enterprise]   > [裝置擁有者]  中，您可以選擇可接受的威脅等級。 <!-- 4631440 --> [使用 Intune，透過 Android Enterprise 設定將裝置標示為符合規範或不符合規範](../protect/compliance-policy-create-android-for-work.md#device-owner)列出目前的設定。
- 在 Android Enterprise 完全受控裝置上，現在可以透過應用程式設定原則來設定 Microsoft Launcher 應用程式，以便在完全受控的裝置上允許標準化的終端使用者體驗。 您可以使用 Microsoft Launcher 應用程式來將 Android 裝置個人化。 將應用程式搭配 Microsoft 帳戶或公司/學校帳戶一起使用，即可存取您個人化摘要中的行事曆、文件及最近活動。 <!-- 5334044 -->

透過此更新，我們很高興宣佈現已正式推出適用於 Android Enterprise 完全受控的 Intune 支援。

適用於：

- 完全受控的 Android Enterprise 裝置

#### <a name="send-custom-notifications-to-a-single-device---4928910---"></a>將自訂通知傳送至單一裝置<!-- 4928910 -->
您現在可以選取單一裝置，然後使用遠端裝置動作，[只傳送自訂通知給該裝置](../remote-actions/custom-notifications.md#send-a-custom-notification-to-a-single-device)。

#### <a name="wipe-and-passcode-reset-actions-arent-available-for-ios-devices-that-are-enrolled-by-using-user-enrollment---4950491---"></a>利用使用者註冊來註冊的 iOS 裝置無法使用「抹除」和「密碼重設」動作<!-- 4950491 -->
使用者註冊是新類型的 Apple 裝置註冊。 當您利用使用者註冊來註冊裝置時，這類裝置將無法使用「抹除」和「密碼重設」遠端動作。

#### <a name="intune-support-for-ios-13-and-macos-catalina-devices---4665317---"></a>適用於 iOS 13 和 macOS Catalina 裝置的 Intune 支援<!-- 4665317 -->
Intune 現在支援同時管理 iOS 13 和 macOS Catalina 裝置。
如需詳細資訊，請參閱[適用於 iOS 13 和 iPadOS 的 Microsoft Intune 支援部落格文章](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Microsoft-Intune-Support-for-iOS-13-and-iPadOS/ba-p/861998) \(英文\)。

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-security"></a>裝置安全性

#### <a name="bitlocker-support-for-client-driven-recovery-password-rotation----3444125---"></a>適用於用戶端驅動的復原密碼輪替的 BitLocker 支援<!--  3444125 -->
使用 Intune Endpoint Protection 設定，在執行 Windows 1909 版或更新版本的裝置上設定適用於 BitLocker 的[用戶端驅動的復原密碼輪替](../protect/endpoint-protection-windows-10.md#windows-encryption)。

此設定會在 OS 磁碟機復原 (藉由使用 bootmgr 或 WinRE) 之後起始用戶端驅動的復原密碼重新整理，並在固定資料磁碟機上解除鎖定復原密碼。 此設定會重新整理所使用的特定復原密碼，而磁碟區上其他未使用的密碼則會保持不變。 如需詳細資訊，請參閱適用於 [ConfigureRecoveryPasswordRotation](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp) \(部分機器翻譯\) 的 BitLocker CSP 文件。

#### <a name="tamper-protection-for-windows-defender-antivirus---4705448----------"></a>適用於 Windows Defender 防毒軟體的防篡改保護<!-- 4705448        -->
使用 Intune 來管理適用於 Windows Defender 防毒軟體的「防篡改保護」  。 當您使用 Windows 10 Endpoint Protection 的裝置組態設定檔時，將可在 Microsoft Defender 資訊安全中心群組內找到[適用於防篡改保護的設定](../protect/endpoint-protection-windows-10.md#microsoft-defender-security-center)。 您可以將 [防篡改保護] 設定為 [已啟用]  以開啟 [防篡改保護] 限制、設定 [已停用]  以關閉它們，或設定 [未設定]  以讓裝置保留目前設定。  

如需防篡改保護的詳細資訊，請參閱 Windows 文件中的[使用防篡改保護來防止安全性設定變更](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-antivirus/prevent-changes-to-security-settings-with-tamper-protection) \(部分機器翻譯\)。

#### <a name="advanced-settings-for-windows-defender-firewall-are-now-generally-available----5317392---------"></a>現已正式推出適用於 Windows Defender 防火牆的進階設定<!--  5317392       -->  
[適用於 Endpoint Protection 的 Windows Defender 自訂防火牆規則](../protect/endpoint-protection-configure.md#add-custom-firewall-rules-for-windows-10-devices) (您設定為裝置組態設定檔的一部分) 已超出公開預覽狀態且已正式推出 (GA)。  您可以使用這些規則，來指定應用程式、網路位址和連接埠的輸入及輸出行為。 這些規則已於七月發行為公開預覽。 

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="role-based-access-control"></a>以角色為基礎的存取控制

#### <a name="scope-tags-now-support-terms-of-use-policies---2358863-idmiss---"></a>範圍標籤現在支援使用規定原則<!-- 2358863 idmiss -->
您現在可以將[範圍標籤](scope-tags.md)指派給使用規定原則。 若要這麼做，請移至 [Intune]   > [裝置註冊]   > [條款及條件]  > 選擇清單中的項目 > [屬性]   > [範圍標籤]  > 選擇範圍標籤。

## <a name="week-of-september-9-2019"></a>2019 年 9 月 9 日當週

### <a name="app-management"></a>應用程式管理

#### <a name="updates-to-microsoft-intune-app---4997846---"></a>Microsoft Intune 應用程式的更新<!-- 4997846 -->
適用於 Android 的 Microsoft Intune 應用程式已更新，並具有下列改善：
- 已更新並改善版面配置以納入最重要動作的下方導覽。
- 已新增顯示使用者設定檔的額外頁面。
- 已在應用程式中為使用者新增可採取動作的通知顯示，例如需要更新其裝置設定。
- 已新增自訂推播通知的顯示，並將應用程式與適用於 iOS 和 Android 之公司入口網站應用程式中最近新增的支援一致。 如需詳細資訊，請參閱[在 Intune 中傳送自訂通知](../remote-actions/custom-notifications.md)。

#### <a name="for-ios-devices-customize-the-enrollment-process-privacy-screen-of-the-company-portal---4394993---"></a>針對 iOS 裝置，請自訂公司入口網站的 [註冊程序隱私權] 畫面<!-- 4394993 -->
使用 Markdown，您可以自訂使用者在 iOS 註冊期間看到的公司入口網站隱私權畫面。 具體來說，您可以自訂組織無法在裝置上查看或執行的操作清單。 如需詳細資訊，請參閱[如何設定 Intune 公司入口網站應用程式](../apps/company-portal-app.md#privacy-statement-customization)。


## <a name="week-of-september-2-2019"></a>2019 年 9 月 2 日當週

### <a name="monitor-and-troubleshoot"></a>監視及疑難排解

#### <a name="intune-user-interface-update--tenant-status-dashboard---5273210----"></a>Intune 使用者介面更新 - [租用戶狀態] 儀表板<!-- 5273210  -->
已更新 [租用戶狀態] 儀表板的使用者介面以與 Azure 使用者介面樣式一致。 如需詳細資訊，請參閱[租用戶狀態](../tenant-status.md)。

## <a name="week-of-august-26-2019"></a>2019 年 8 月 26 日當週

### <a name="configure-microsoft-edge-settings-using-administrative-templates-for-windows-10-and-newer---5228061---"></a>使用 Windows 10 和更新版本的系統管理範本，進行 Microsoft Edge 設定<!-- 5228061 -->

在 Windows 10 和更新版本的裝置中 ，您可以建立系統管理範本以進行 Intune 中的群組原則設定。 在此更新中，您可以進行設定，並套用至 Microsoft Edge 77 版和更新版本。

若要深入了解系統管理範本，請參閱[在 Intune 中使用 Windows 10 範本設定群組原則設定](../configuration/administrative-templates-windows.md)。

適用於：

- Windows 10 與更新版本 (Windows RS4+)

## <a name="week-of-august-12-2019-1908-service-release"></a>2019 年 8 月 12 日當週 (1908 服務版本)

### <a name="app-management"></a>應用程式管理

#### <a name="control-ios-app-uninstall-behavior-at-device-unenrollment---3504144-----"></a>控制當裝置取消註冊時的 iOS 應用程式解除安裝行為<!-- 3504144   -->
系統管理員可以管理當裝置在使用者或裝置群組層級取消註冊時，應用程式要從裝置上移除或保留。 

#### <a name="categorize-microsoft-store-for-business-apps---3926922---"></a>分類商務用 Microsoft 網上商店應用程式<!-- 3926922 -->
您可以將商務用 Microsoft Store 應用程式分類。 若要這樣做，請選擇 [Intune]   > [用戶端應用程式]   > [應用程式]  > 選取商務用 Microsoft Store 應用程式 > [應用程式資訊]   > [類別]  。 在下拉式功能表中，指派類別。

#### <a name="customized-notifications-for-microsoft-intune-app-users---4843354----"></a>Microsoft Intune 應用程式使用者的自訂通知<!-- 4843354  -->
適用於 Android 的 Microsoft Intune 應用程式現在支援顯示自訂推播通知，使它與最近在適用於 iOS 與 Android 的公司入口網站應用程式中新增的支援有相同功能。 如需詳細資訊，請參閱[在 Intune 中傳送自訂通知](../remote-actions/custom-notifications.md)。

### <a name="device-configuration"></a>裝置設定

#### <a name="new-features-for-android-enterprise-dedicated-devices-in-multi-app-mode---3755304-3041943-3041946-----"></a>多個應用程式模式 Android Enterprise 專用裝置的新功能<!-- 3755304 3041943 3041946   -->

在 Intune 中，您可以控制 Android Enterprise 專用裝置上 Kiosk 式體驗的功能與設定 ([裝置設定]   > [設定檔]   > [建立設定檔]   > [Android Enterprise]  平台 > [僅限裝置擁有者]、[裝置限制]  設定檔類型)。

在此更新中，已新增下列功能：

- [專用裝置]   > [多個應用程式]  ：[虛擬首頁按鈕]  可以透過在裝置上向上撥動來顯示，或是浮動顯示在畫面上，以便使用者可以移動它。
- [專用裝置]   > [多個應用程式]  ：[手電筒存取權]  可讓使用者使用手電筒。 
- [專用裝置]   > [多個應用程式]  ：[媒體音量控制]  可讓使用者使用滑桿來控制裝置的媒體音量。 
- [專用裝置]   > [多個應用程式]  ：**啟用螢幕保護裝置**、上傳自訂影像，並控制何時顯示螢幕保護裝置程式。

若要查看目前的設定，請前往[使用 Intune 允許或限制功能的 Android Enterprise 裝置設定](../configuration/device-restrictions-android-for-work.md#dedicated-device-settings)。

適用於：

- Android Enterprise 專用裝置

#### <a name="new-app-and-configuration-profiles-for-android-enterprise-fully-managed-devices---3574215-3574238-3574235-3574232-----"></a>適用於 Android Enterprise 完全受控裝置的新應用程式設定檔<!-- 3574215 3574238 3574235 3574232   -->
您可以使用設定檔來設定將 VPN、電子郵件與 Wi-Fi 設定套用到 Android Enterprise 裝置擁有者 (完全受控) 裝置的設定。 在此更新中，您可以：

- 使用[應用程式設定原則](../apps/app-configuration-policies-use-android.md)來部署 Outlook、Gmail 與 Nine Work 電子郵件設定。
- 使用裝置組態設定檔來部署[受信任的根憑證設定](../protect/certificates-configure.md)。
- 使用裝置組態設定檔來部署 [VPN](../configuration/vpn-settings-android-enterprise.md) 與 [Wi-Fi](../configuration/wi-fi-settings-android-enterprise.md) 設定。

> [!IMPORTANT]
> 使用者可以使用此功能來驗證其 VPN、Wi-Fi 與電子郵件設定檔的使用者名稱與密碼。 目前無法使用憑證式驗證。

適用於：  
- Android Enterprise 裝置擁有者 (完全受控)

#### <a name="control-the-apps-files-documents-and-folders-that-open-when-users-sign-in-to-macos-devices--3914202-----"></a>控制當使用者登入 macOS 裝置時會開啟的應用程式、檔案、文件與資料夾<!--3914202   -->
您可以啟用及設定 macOS 裝置上的功能 ([裝置設定]   > [設定檔]   > [建立設定檔]   > [macOS]  平台 > [裝置功能]  設定檔類型)。 

在此更新中，有一個新的 [登入項目] 設定，可控制當使用者登入已註冊的裝置時，會開啟哪些應用程式、檔案、文件與資料夾。 

若要查看目前的設定，請前往 [Intune 中的 macOS 裝置功能設定](../configuration/macos-device-features-settings.md)。

適用於：  
- macOS

#### <a name="deadlines-replace-engaged-restart-settings-for-windows-update-rings---4464404----------"></a>Windows Update 通道的「預約重新啟動」已由「期限」取代<!-- 4464404        -->
為了具有與 [Windows 維護變更](https://docs.microsoft.com/windows/whats-new/whats-new-windows-10-version-1903#servicing)相同的功能，Intune 的 Windows 10 Update 通道現在[支援期限設定](../protect/windows-update-settings.md)。 「期限」  決定裝置何時安裝功能與安全性更新。  在執行 Windows 10 1903 或更新版本的裝置上，「期限」  會取代「預約重新啟動」  的設定。  未來「期限」  也會取代舊版 Windows 10 上的「預約重新啟動」  。  

當您未設定 [期限]  時，裝置會繼續使用其 [預約重新啟動]  設定，不過在未來的更新中，Intune 將會淘汰對預約重新啟動設定的支援。  

規劃在您的所有 Windows 10 裝置上使用「期限」  。 當「期限」  的設定就緒之後，您可以將您 Intune 的「預約重新啟動」  設定變更為 [尚未設定]。 當設定為 [尚未設定] 時，Intune 會停止管理裝置上的這些設定，但不會從裝置中移除設定的最後一個組態。 因此，為「預約重新啟動」  設定的最後一個設定會在裝置上維持作用中設定，直到透過 Intune 以外的方法修改這些設定為止。 之後，當裝置的 Windows 版本變更時，或當 Intune 對「期限」  的支援擴充到裝置 Windows 版本時，裝置就會開始使用已準備好的新設定。

#### <a name="support-for-multiple-microsoft-intune-certificate-connectors-----4704642--------"></a>支援多個 Microsoft Intune 憑證連接器<!--   4704642      -->
Intune 現在支援安裝並使用多個[適用於 PKCS 作業的 Microsoft Intune 憑證連接器](../protect/certficates-pfx-configure.md)。 此變更支援連接器的負載平衡與高可用性。 每個連接器執行個體都能處理來自 Intune 的憑證要求。  如果某個連接器無法使用，其他連接器會繼續處理要求。

若要使用多個連接器，您不需要升級到連接器軟體的最新版本。  

#### <a name="new-settings-and-changes-to-existing-settings-to-restrict-features-on-ios-and-macos-devices---4867699-4867709-----"></a>新設定，以及可限制 iOS 與 macOS 裝置上功能的現有設定變更<!-- 4867699 4867709   -->
您可以建立設定檔來限制執行 iOS 與 macOS 之裝置上的功能 ([裝置設定]   > [設定檔]   > [建立設定檔]   > [iOS]  或 [macOS]  平台類型 > [裝置限制]  )。 此更新包含下列功能：

- 在 [macOS]   > [裝置限制]   > [雲端與儲存體]  中，使用新的 [Handoff]  設定可防止使用者在一部 macOS 裝置上工作，然後在另一部 macOS 或 iOS 裝置上繼續工作。

  若要查看目前的設定，請前往 [macOS 裝置設定以使用 Intune 允許或限制功能](../configuration/device-restrictions-macos.md)。

- 在 [iOS]   > [裝置限制]  上，有幾個變更：

  - [內建應用程式]   > [尋找我的 iPhone (僅限受監督)]  ：封鎖 Find My 應用程式功能中此功能的新設定。 
  - [內建應用程式]   > [尋找我的朋友 (僅限受監督)]  ：封鎖 Find My 應用程式功能中此功能的新設定。 
  - [無線]   > [修改 Wi-Fi 狀態 (僅限受監督)]  ：防止使用者開啟或關閉裝置上 Wi-Fi 功能的新設定。
  - [鍵盤與字典]   > [QuickPath (僅限受監督)]  ：封鎖 QuickPath 功能的新設定。
  - **雲端與儲存體**：[活動接續]  已重新命名為 [Handoff]  。

  若要查看目前的設定，請前往[使用 Intune 允許或限制功能的 iOS 裝置設定](../configuration/device-restrictions-ios.md)。

適用於：  
- macOS 10.15 與更新版本
- iOS 13 與更新版本

#### <a name="some-unsupervised-ios-device-restrictions-will-become-supervised-only-with-the-ios-130-release---4867809-----"></a>某些不受監督的 iOS 裝置限制將會只在 iOS 13.0 版本中受到監督<!-- 4867809   -->
在此更新中，某些設定適用於執行 iOS 13.0 版的僅限受監督裝置。 如果在執行早於 iOS 13.0 版之版本的未受監督裝置上設定並指派這些設定，這些設定仍然會套用到那些未受監督裝置。 裝置升級到 iOS 13.0 之後仍然會套用它們。 在已備份和已還原的未受監督裝置上，系統會移除這些限制。

這些設定包括：

- App Store、文件檢視、遊戲
  - App Store
  - 清晰的 iTunes 音樂、播客或新聞內容
  - 新增 Game Center 朋友
  - 多人遊戲
- 內建應用程式
  - 相機
    - FaceTime
  - Safari
    - 自動填寫
- 雲端與儲存體
  - 備份至 iCloud
  - 禁止 iCloud Document 同步
  - 防止同步 iCloud 鑰匙圈

若要查看目前的設定，請前往[使用 Intune 允許或限制功能的 iOS 裝置設定](../configuration/device-restrictions-ios.md)。

適用於：  
- iOS 13.0 與更新版本

#### <a name="improved-device-status-for-macos-filevault-encryption---4944983-----------"></a>已改善 macOS FileVault 加密的裝置狀態<!-- 4944983         -->
我們已針對 macOS 裝置的 FileVault 加密更新數個[裝置狀態訊息](../protect/encryption-monitor.md#device-encryption-status)。

#### <a name="some-windows-defender-antivirus-scan-settings-in-the-reporting-show-a-failed-status---5119229---"></a>報告中的某些 Windows Defender 防毒軟體掃描設定顯示 [失敗] 狀態<!-- 5119229 -->
在 Intune 中，您可以建立原則來使用 Windows Defender Antivirus 掃描您的 Windows 10 裝置 ([裝置設定]   > [設定檔]   > [建立設定檔]   > [Windows 10 及更新版本]  平台 > [裝置限制]  設定檔類型 > [Windows Defender 防毒軟體]  )。 [執行每日快速掃描的時間]  與 [要執行的系統掃描類型]  報告顯示 [失敗] 狀態，但它實際上是成功狀態。 

在此更新中，已修正此行為。 因此，[執行每日快速掃描的時間]  和 [要執行的系統掃描類型]  設定會在掃描成功完成時顯示成功狀態，並在無法套用設定時顯示失敗狀態。

如需 Windows Defender 防毒軟體設定的詳細資訊，請參閱[使用 Intune 來允許或限制功能的 Windows 10 (和更新版本) 裝置設定](../configuration/device-restrictions-windows-10.md#microsoft-defender-antivirus)。

### <a name="device-enrollment"></a>裝置註冊

#### <a name="default-scope-tags---3702875----"></a>預設範圍標籤<!-- 3702875  -->
現已可使用新內建功能「預設範圍標籤」。 所有支援範圍標籤的未標記 Intune 物件都會自動指派至預設範圍標籤。 [預設]  範圍標籤會新增至所有現有的角色指派，以維持與目前系統管理員相同的體驗。 如果您不想讓系統管理員看到 Intune 物件有預設範圍標籤，請從角色指派中移除預設範圍標籤。 此功能與 System Center Configuration Manager 中的安全性範圍功能類似。 如需詳細資訊，請參閱[針對分散式 IT 使用 RBAC 和範圍標籤](scope-tags.md)。

#### <a name="android-enrollment-device-administrator-support---4869749-----"></a>Android 註冊裝置系統管理員支援<!-- 4869749   -->
Android 裝置系統管理員註冊選項已新增至 Android 註冊頁面 ([Intune]   > [裝置註冊]   > [Android 註冊]  )。 針對所有租用戶，預設仍會啟用 Android 裝置系統管理員。  如需詳細資訊，請參閱 [Android 裝置系統管理員註冊](../enrollment/android-enroll-device-administrator.md)。

#### <a name="skip-more-screens-in-setup-assistant---4877451----"></a>在設定輔助程式中略過更多畫面 <!--4877451  -->
您可以設定 [裝置註冊計劃] 設定檔，以略過下列 [設定輔助程式] 畫面：
- 適用於 iOS
    - 外觀
    - 快速語言
    - 慣用語言
    - 裝置到裝置的移轉
- 適用於 macOS
    - 螢幕使用時間
    - Touch ID 設定

如需 [設定輔助程式] 的詳細資訊，請參閱[建立適用於 iOS 的 Apple 註冊設定檔](../enrollment/device-enrollment-program-enroll-ios.md#create-an-apple-enrollment-profile)與[建立適用於 macOS 的 Apple 註冊設定檔](../enrollment/device-enrollment-program-enroll-macos.md#create-an-apple-enrollment-profile)。

#### <a name="add-a-user-column-to-the-autopilot-device-csv-upload-process---3823054---"></a>將使用者欄新增至 Autopilot 裝置 CSV 上傳程序<!-- 3823054 -->
您現在可以將使用者欄新增至 Autopilot 裝置的 CSV 上傳。 這可讓您在匯入 CSV 時大量指派使用者。 如需詳細資訊，請參閱[使用 Windows Autopilot 在 Intune 中註冊 Windows 裝置](../enrollment/enrollment-autopilot.md)。


### <a name="device-management"></a>裝置管理

#### <a name="configure-automatic-device-clean-up-time-limit-down-to-30-days--4231059----"></a>將自動裝置清除時間限制設定為最低 30 天<!--4231059  -->
您可以將自動裝置清除時間限制設定為最短在最後一次登入之後的 30 天 (而不是先前的限制 90 天)。 若要這樣做，請移至 [Intune]   > [裝置]   > [設定]   > [裝置清除規則]  。

#### <a name="build-number-included-on-android-device-hardware-page---4461910-----"></a>Android 裝置 [硬體] 頁面上包括的組建編號<!-- 4461910   -->
每個 Android 裝置的 [硬體] 頁面上都有一個新項目，它包括裝置的作業系統組建編號。 如需詳細資訊，請參閱[在 Intune 中檢視裝置詳細資料](../remote-actions/device-inventory.md)。


<!-- ########################## -->

## <a name="week-of-august-5-2019"></a>2019 年 8 月 5 日當週

### <a name="zebra-technologies-is-a-supported-oem-for-oemconfig-on-android-enterprise-devices---4843713---"></a>Zebra Technologies 是 Android Enterprise 裝置上支援的 OEMConfig OEM<!-- 4843713 -->

在 Intune 中，您可以建立裝置組態設定檔，並使用 OEMConfig 將設定套用至 Android Enterprise 裝置 ([裝置設定]   > [設定檔]   > [建立設定檔]   > [Android Enterprise]  平台 > [OEMConfig]  設定檔類型)。

在此更新中，Zebra Technologies 是受支援的 OEMConfig 原始設備製造商 (OEM)。 如需 OEMConfig 的詳細資訊，請參閱[運用 OEMConfig 來使用及管理 Android Enterprise 裝置](../configuration/android-oem-configuration-overview.md)。

適用於：  
- Android Enterprise

<!-- ########################## -->

## <a name="week-of-july-22-2019-1907-service-release"></a>2019 年 7 月 22 日當週 (1907 服務版本)

### <a name="app-management"></a>應用程式管理

#### <a name="customized-notifications-for-users-and-groups---16766574------------"></a>使用者和群組的自訂通知<!-- 16766574          -->
將來自「公司入口網站」應用程式的自訂推播通知傳送給您以 Intune 管理的 iOS 和 Android 裝置上的使用者。 您可以使用任意文字來大幅自訂這些行動推播通知，並可用於任何用途。 您可以將它們的目標設定成您組織中各種不同的使用者群組。 如需詳細資訊，請參閱[自訂通知](../remote-actions/custom-notifications.md)。

#### <a name="googles-device-policy-controller-app---3041950----"></a>Google 的 Device Policy Controller 應用程式<!-- 3041950  -->
Managed Home Screen 應用程式現在可讓您存取 Google 的 Android Device Policy 應用程式。 Managed Home Screen 應用程式是用於裝置的自訂啟動器，這些裝置已在 Intune 中註冊為使用多應用程式 kiosk 模式的 Android Enterprise (AE) 專用裝置。 您可以存取 Android Device Policy 應用程式，或引導使用者存取 Android Device Policy 應用程式，以用以支援和偵錯。 當裝置在 Managed Home Screen 中註冊和鎖定時，即可使用這項啟動功能。 不需要其他安裝即可使用這項功能。

#### <a name="outlook-protection-settings-for-ios-and-android-devices---3212619---"></a>iOS 和 Android 裝置的 Outlook 保護設定<!-- 3212619 -->
您現在可以在不註冊裝置的情況下，使用簡單的 Intune 系統管理控制項，為 iOS 與 Android 版 Outlook 設定一般應用程式和資料保護組態設定。 一般應用程式組態設定所提供的設定，相當於系統管理員在管理已註冊裝置上 iOS 與 Android 版 Outlook 時所能啟用的設定。 如需有關 Outlook 設定的詳細資訊，請參閱[部署 iOS 與 Android 版 Outlook 應用程式組態設定](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/outlook-for-ios-and-android/outlook-for-ios-and-android-configuration-with-microsoft-intune) \(部分機器翻譯\)。

### <a name="device-configuration"></a>裝置設定

#### <a name="use-applicability-rules-when-creating-windows-10-device-configuration-profiles----2549910-eeready---idstaged---"></a>在建立 Windows 10 裝置組態設定檔時使用「適用性規則」 <!-- 2549910 eeready   idstaged -->

您可以建立 Windows 10 裝置組態設定檔 ([裝置設定]   > [設定檔]   > [建立設定檔]   > [Windows 10]  平台 > [適用性規則]  )。 在這項更新中，您可以建立**適用性規則**，讓設定檔只套用到特定版本。 例如，您可以建立設定檔來啟用某些 BitLocker 設定。 一旦您新增設定檔後，您便可以使用適用性規則，將設定檔設為只套用到執行 Windows 10 企業版的裝置。

若要新增適用性規則，請參閱[適用性規則](../configuration/device-profile-create.md#applicability-rules)。

適用於：Windows 10 及更新版本

#### <a name="use-tokens-to-add-device-specific-information-in-custom-profiles-for-ios-and-macos-devices---3330008----"></a>使用權杖在 iOS 與 macOS 裝置的自訂設定檔中新增裝置特定資訊<!-- 3330008  -->
您可以使用 iOS 與 macOS 裝置的自訂設定檔來設定 Intune 未內建的設定和功能 ([裝置設定]   > [設定檔]   > [建立設定檔]   > [iOS]  或 [macOS]  平台 > [自訂]  設定檔類型)。 在這項更新中，您可以將權杖新增至您的 `.mobileconfig` 檔案來新增裝置特定資訊。 例如，您可以將 `Serial Number: {{serialnumber}}` 新增至您的組態檔以顯示裝置的序號。

若要建立自訂設定檔，請參閱 [iOS 自訂設定](../configuration/custom-settings-ios.md) 或 [macOS 自訂設定](../configuration/custom-settings-macos.md)。

適用於：
- iOS
- macOS

#### <a name="new-configuration-designer-when-creating-an-oemconfig-profile-for-android-enterprise---3712769-----"></a>為 Android Enterprise 建立 OEMConfig 設定檔時的新設定設計工具<!-- 3712769   -->
在 Intune 中，您可以建立使用 OEMConfig 應用程式的裝置組態設定檔 ([裝置設定] > [設定檔] > [建立設定檔] > [Android 企業] 平台 > [OEMConfig] 設定檔類型)。 當您這麼做時，JSON 編輯器會開啟，其中含有可供您變更的範本和值。 

這項更新包含具有更佳使用者體驗的「設定設計工具」，可顯示內嵌在應用程式中的詳細資料，包括標題、描述等。 JSON 工具仍然可供使用，並且會顯示您在「設定設計工具中」所做的任何變更。

若要查看目前的設定，請前往[運用 OEMConfig 來使用及管理 Android Enterprise 裝置](../configuration/android-oem-configuration-overview.md)。

適用於：Android 企業

#### <a name="updated-ui-for-configuring-windows-hello---4089576--------------"></a>已更新用於設定 Windows Hello 的 UI<!-- 4089576            -->
我們已更新您[設定 Intune 以使用 Windows Hello 企業版](../protect/windows-hello.md)的主控台。 在您啟用 Windows Hello 支援的相同主控台窗格上現已提供所有組態設定。

#### <a name="intune-powershell-sdk---4924113---"></a>Intune PowerShell SDK<!-- 4924113 --> 
透過 Microsoft Graph 提供 Intune API 支援的 Intune PowerShell SDK 已更新成 6.1907.1.0 版。 SDK 現在支援下列各項：
- 與「Azure 自動化」搭配運作。
- 支援僅限應用程式的驗證讀取作業。 
- 支援使用易記的縮寫名稱作為別名。
- 符合 PowerShell 命名慣例。 具體而言，`PSCredential` 參數 (在 `Connect-MSGraph` Cmdlet 上) 已重新命名為 `Credential`。
- 使用 `Invoke-MSGraphRequest` Cmdlet 時，支援手動指定 `Content-Type` 標頭。

如需詳細資訊，請參閱[適用於 Microsoft Intune Graph API 的 PowerShell SDK](https://www.powershellgallery.com/packages/Microsoft.Graph.Intune)。


### <a name="device-enrollment"></a>裝置註冊

#### <a name="updates-for-enrollment-restrictions---2871968---"></a>更新註冊限制<!-- 2871968 -->
新租用戶的「註冊限制」已更新成預設允許 Android Enterprise 公司設定檔。 現有租用戶將保持不變。 若要使用 Android Enterprise 公司設定檔，您仍然必須[將 Intune 帳戶連線至受控的 Google Play 帳戶](../enrollment/connect-intune-android-enterprise.md)。

#### <a name="ui-updates-for-apple-enrollment-and-enrollment-restrictions--4089575-4089579----"></a>Apple 註冊和註冊限制的 UI 更新<!--4089575, 4089579  -->
下列兩個程序皆使用精靈樣式的使用者介面：
- Apple 裝置註冊。 如需詳細資訊，請參閱[使用 Apple 的裝置註冊計劃來自動註冊 iOS 裝置](../enrollment/device-enrollment-program-enroll-ios.md)。
- 註冊限制建立。 如需詳細資訊，請參閱[設定註冊限制](../enrollment/enrollment-restrictions-set.md)。

#### <a name="handling-pre-configuration-of-corporate-device-identifiers-for-android-q-devices---4711509--idmiss---"></a>處理 Android Q 裝置的公司裝置識別碼預先設定<!-- 4711509  idmiss -->
在 Android Q (v10) 中，Google 會讓舊版受控 (裝置系統管理員) Android 裝置上的 MDM 代理程式無法收集裝置識別碼資訊。  Intune 有一項功能，可讓 IT 系統管理員[預先設定一份裝置序號或 IMEI 的清單](../enrollment/corporate-identifiers-add.md#identify-corporate-owned-devices-with-imei-or-serial-number)，以便自動將這些裝置標記為公司擁有的裝置。 此功能不適用於受裝置管理員管理的 Android Q 裝置。  不論是否上傳裝置的序號或 IMEI，在進行 Intune 註冊時，都會將其視為個人裝置。  您可以在註冊後手動將擁有權切換至公司。  這只會影響新的註冊項目，不會影響現有的已註冊裝置。  以公司設定檔管理的 Android 裝置不受這項變更影響，將會繼續依照目前的方式運作。  此外，以裝置管理員身分註冊的 Android Q 裝置將不再能夠於 Intune 主控台中將序號或 IMEI 回報成裝置屬性。

#### <a name="icons-have-changed-for-android-enterprise-enrollments-work-profile-dedicated-devices-and-fully-managed-devices---4977730---"></a>Android Enterprise 註冊 (公司設定檔、專用裝置及完全受控裝置) 的圖示已變更<!-- 4977730 -->
Android Enterprise 註冊設定檔的圖示已變更。 若要查看新圖示，請前往 [Intune]   > [註冊]   > [Android 註冊]  > 在 [註冊設定檔]  底下尋找。


#### <a name="windows-diagnostic-data-collection-change---4113859---"></a>Windows 診斷資料收集變更<!-- 4113859 -->
執行 Windows 10 1903 版和更新版本之裝置的診斷資料收集預設值已變更。 從 Windows 10 1903 開始，預設會開啟診斷資料收集。 Windows 診斷資料是來自 Windows 裝置的重要技術資料，是與裝置及 Windows 和相關軟體執行情況有關的資料。 如需詳細資訊，請參閱[在組織中設定 Windows 診斷資料](https://docs.microsoft.com/windows/privacy/configure-windows-diagnostic-data-in-your-organization)。 除非在 Autopilot 設定檔中另以 [System/AllowTelemetry](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-system#system-allowtelemetry) 進行設定，否則 Autopilot 裝置也會選擇加入「完整」遙測。

### <a name="device-management"></a>裝置管理

#### <a name="improve-device-location---3855417----"></a>改善裝置位置<!-- 3855417  -->
您可以使用 [尋找裝置]  動作來移向裝置的確切座標。 如需有關尋找遺失之 iOS 裝置的詳細資訊，請參閱[尋找遺失的 iOS 裝置](../remote-actions/device-locate.md)。

### <a name="device-security"></a>裝置安全性

#### <a name="advanced-settings-for-windows-defender-firewall--public-preview----1311949-------"></a>適用於 Windows Defender 防火牆的進階設定 (公開預覽版)<!--  1311949     -->  
使用 Intune [將自訂防火牆規則納入裝置組態設定檔中](../protect/endpoint-protection-configure.md#add-custom-firewall-rules-for-windows-10-devices)來管理，以執行 Windows 10 上的端點保護。 規則可指定應用程式、網路位址和連接埠的輸入及輸出行為。 

#### <a name="updated-ui-for-managing-security-baselines---4091125-------"></a>已更新用於管理安全性基準的 UI<!-- 4091125     -->
我們已更新 Intune 主控台中安全性基準的[建立和編輯體驗](../protect/security-baselines.md#create-the-profile)。 這些變更包括：

已壓縮成更簡單精靈樣式的單一刀鋒視窗格式。 在一個刀鋒視窗內操作即可。 這個新設計廢除了需要 IT 專業人員向下切入至數個個別窗格的刀鋒視窗擴展。  
您現在可以在建立和編輯體驗中一併建立「指派」，而不需稍後返回來指派基準。 我們已新增設定摘要，可供您在建立新基準之前及在編輯現有基準時檢視。 編輯時，摘要只會顯示在目前編輯的一個屬性類別內設定的項目清單。

<!-- ########################## -->

## <a name="week-of-july-15-2019"></a>2019 年 7 月 15 日當週 

### <a name="app-management"></a>應用程式管理

#### <a name="managed-home-screen-and-managed-settings-icons---4918107---"></a>Managed Home Screen 和受管理設定圖示<!-- 4918107 -->
Managed Home Screen 應用程式圖示和 [受管理設定]  圖示已更新。 Managed Home Screen 應用程式僅供在 Intune 中註冊為 Android Enterprise (AE) 專用裝置並以多應用程式 kiosk 模式執行的裝置使用。 如需有關 Managed Home Screen 應用程式的詳細資訊，請參閱[設定適用於 Android Enterprise 的 Microsoft Managed Home Screen 應用程式](../apps/app-configuration-managed-home-screen-app.md)。

#### <a name="android-device-policy-on-android-enterprise-dedicated-devices---4918136---"></a>Android Enterprise 專用裝置上的 Android Device Policy<!-- 4918136 -->
您可以從 Managed Home Screen 應用程式的偵錯畫面存取 Android Device Policy 應用程式。 Managed Home Screen 應用程式僅供在 Intune 中註冊為 Android Enterprise (AE) 專用裝置並以多應用程式 kiosk 模式執行的裝置使用。 如需詳細資訊，請參閱[設定適用於 Android Enterprise 的 Microsoft Managed Home Screen 應用程式](../apps/app-configuration-managed-home-screen-app.md)。

#### <a name="ios-company-portal-updates---3902931---"></a>iOS 公司入口網站更新<!-- 3902931 -->
iOS 應用程式管理提示上的貴公司名稱將取代目前的 "i.manage.microsoft.com" 文字。 例如，當使用者嘗試從「公司入口網站」安裝 iOS 應用程式，或當使用者允許管理應用程式時，使用者會看到其公司名稱而不是 "i.manage.microsoft.com"。 在接下來幾天將會向所有客戶推出這項功能。

### <a name="device-configuration"></a>裝置設定

#### <a name="manage-filevault-for-macos----3858502--4557986--1210104----"></a>管理 macOS 的 FileVault<!--  3858502 + 4557986 + 1210104  -->
您可以使用 Intune 來[管理 macOS 裝置的 FileVault 金鑰加密](../protect/encrypt-devices.md)。 若要加密裝置，您需使用端點保護裝置組態設定檔。

我們對 FileVault 的支援包括將未加密的裝置加密、委付裝置個人修復金鑰、自動或手動輪替個人加密金鑰，以及擷取您公司裝置的金鑰。 終端使用者也可以使用「公司入口網站」網站來取得其已加密裝置的個人修復金鑰。

我們也已將加密報告擴充成除了 BitLocker 資訊之外，還包含 [FileVault 相關資訊](../protect/encryption-monitor.md)，讓您可以在一個位置檢視所有裝置加密詳細資料。

### <a name="device-enrollment"></a>裝置註冊

#### <a name="windows-autopilot-reset-removes-the-devices-primary-user---4156123---"></a>Windows Autopilot 重設會移除裝置的主要使用者<!-- 4156123 -->
在裝置上使用 Autopilot 重設時，將會移除裝置的主要使用者。 在重設後登入的下一個使用者將被設定為主要使用者。 在接下來幾天將會向所有客戶推出這項功能。

## <a name="week-of-july-8-2019"></a>2019 年 7 月 8 日當週

### <a name="new-office-windows-and-onedrive-settings-in-windows-10-administrative-templates----3510695---"></a>Windows 10 系統管理範本中的新 Office、Windows 及 OneDrive 設定 <!-- 3510695 -->

您可以在 Intune 中建立模擬內部部署群組原則管理的系統管理範本 ([裝置管理]   > [設定檔]   > [建立設定檔]   > [Windows 10 及更新版本]  平台 > [系統管理範本]  設定檔類型)。

這項更新包含更多可供您新增至範本的 Office、Windows 及 OneDrive 設定。 透過這些新的設定，您現在便可設定超過 2500 個 100% 雲端型的設定。

若要深入了解這項功能，請參閱[在 Intune 中使用 Windows 10 範本設定群組原則設定](../configuration/administrative-templates-windows.md)。

適用於：Windows 10 及更新版本

## <a name="week-of-july-1-2019"></a>2019 年 7 月 1 日當週 

### <a name="app-management"></a>應用程式管理

#### <a name="aad-and-app-on-android-enterprise-devices---3574267---"></a>Android Enterprise 裝置上的 AAD 和 APP<!-- 3574267 -->
讓完全受控的 Android Enterprise 裝置上線時，使用者現在會在初次設定其新的或恢復出廠預設值的裝置期間，向 Azure Active Directory (AAD) 註冊。 先前，針對完全受控的裝置，在完成設定之後，使用者必須手動啟動 Microsoft Intune 應用程式，才能啟動 AAD 註冊。 現在，當使用者在初次設定後抵達裝置首頁時，裝置便已註冊和登錄。

除了 AAD 更新之外，在完全受控的 Android Enterprise 裝置上現在也支援 Intune 應用程式防護原則 (APP)。 此功能將在我們推出它後變成可用功能。如需詳細資訊，請參閱[使用 Intune 將受控 Google Play 應用程式新增至 Android Enterprise 裝置](../apps/apps-add-android-for-work.md)。

## <a name="week-of-june-24-2019-1906-service-release"></a>2019 年 6 月 24 日當週 (1906 服務版本)

### <a name="app-management"></a>應用程式管理

#### <a name="configure-which-browser-is-allowed-to-link-to-organization-data---3145939---"></a>設定允許連結至組織資料的瀏覽器<!-- 3145939 -->
Android 和 iOS 裝置上的 Intune 應用程式防護原則 (APP) 現在可讓您將組織網頁連結傳輸至 Intune Managed Browser 或 Microsoft Edge 以外的特定瀏覽器。  如需 APP 的詳細資訊，請參閱[什麼是應用程式防護原則？](../apps/app-protection-policy.md)

#### <a name="all-apps-page-identifies-onlineoffline-microsoft-store-for-business-apps--4089647---"></a>所有應用程式頁面皆可識別線上/離線商務用 Microsoft Store 應用程式<!--4089647 -->
[所有應用程式]  頁面現在包含可識別「商務用 Microsoft Store」(MSFB) 應用程式為線上或離線應用程式的標籤。 每個 MSFB 應用程式現在都包含「線上」  或「離線」  的尾碼。 應用程式詳細資料頁面也包含「授權類型」  和「支援裝置內容安裝」  (僅限離線授權應用程式) 資訊。

#### <a name="company-portal-app-on-windows-shared-devices--4393553---"></a>Windows 共用裝置上的公司入口網站應用程式<!--4393553 -->
使用者現在可以存取 Windows 共用裝置上的「公司入口網站」應用程式。 終端使用者會在裝置圖標上看到「共用」  標籤。 這適用於「Windows 公司入口網站」應用程式 10.3.45609.0 版和更新版本。

#### <a name="view-all-installed-apps-from-new-company-portal-web-page---4224326---"></a>從新的「公司入口網站」網頁檢視已安裝的應用程式<!-- 4224326 -->
「公司入口網站」的新 [已安裝的應用程式]  頁面會出安裝在使用者裝置上 (必要及可用的) 所有受控應用程式。 除了指派類型之外，使用者也可以看到應用程式的發行者、發行日期，以及目前的安裝狀態。 若您沒有針對使用者將任何應用程式設為必要或可用，他們將會看見一個訊息，說明沒有安裝任何公司應用程式。 若要在 Web 上查看新頁面，請前往[公司入口網站](https://portal.manage.microsoft.com)，然後按一下 [已安裝的應用程式]  。  

#### <a name="new-view-lets-app-users-see-all-managed-apps-installed-on-device---2352913---"></a>新的檢視可讓應用程式使用者查看裝置上安裝的所有受控應用程式<!-- 2352913 -->  
適用於 Windows 的「公司入口網站」應用程式現在會列出使用者裝置上已安裝的所有受控應用程式 (必要及可用的)。 使用者也可以看到已嘗試與擱置中的應用程式安裝，以及其目前狀態。 若您沒有針對使用者將應用程式設為必要或可用，他們將會看見一個訊息，說明沒有安裝任何公司應用程式。 若要查看新檢視，請前往「公司入口網站」瀏覽窗格，然後選取 [應用程式]   > [已安裝的應用程式]  。

### <a name="device-configuration"></a>裝置設定

#### <a name="configure-settings-for-kernel-extensions-on-macos-devices---2043024---"></a>在 macOS 裝置上設定核心延伸模組的設定<!-- 2043024 -->
在 macOS 裝置上，您可以建立裝置組態設定檔 ([裝置設定]   > [設定檔]   > [建立設定檔]  > 針對平台選擇 [macOS]  )。 這項更新包含一組新的設定，可讓您在裝置上設定及使用核心延伸模組。 您可以新增特定的延伸模組，或是允許來自特定合作夥伴或開發者的所有延伸模組。

若要深入了解此功能，請參閱[核心延伸模組概觀](../configuration/kernel-extensions-overview-macos.md)和[核心延伸模組設定](../configuration/kernel-extensions-settings-macos.md)。

適用於：macOS 10.13.2 和更新版本

#### <a name="apps-from-the-store-only-setting-for-windows-10-devices-includes-more-configuration-options---2697002---"></a>Windows 10 裝置的 [Apps from the store only] \(僅限來自 Store 的應用程式\) 設定包含更多設定選項<!-- 2697002 -->
當您建立 Windows 裝置的裝置限制設定檔時，您可以使用 [Apps from the store only] \(僅限來自 Store 的應用程式\)  設定，讓使用者只安裝來自 Windows App Store 的應用程式 ([裝置設定]   > [設定檔]   > [建立設定檔]   > [Windows 10 及更新版本]  (平台) > [裝置限制]  (設定檔類型))。 在這項更新中，此設定會擴展成支援更多選項。

若要查看新的設定，請前往[用以允許或限制功能的 Windows 10 (及更新版本) 裝置設定](../configuration/device-restrictions-windows-10.md#app-store)。

適用於：Windows 10 及更新版本

#### <a name="deploy-multiple-zebra-mobility-extensions-device-profiles-to-a-device-same-user-group-or-same-devices-group---4089955---"></a>將多個 Zebra 行動延伸模組的裝置設定檔部署至裝置、相同的使用者群組或裝置群組<!-- 4089955 -->
在 Intune 中，您可以在裝置組態設定檔中使用 Zebra 行動延伸模組 (MX)，來自訂 Intune 未內建的 Zebra 裝置設定。 目前，一部裝置只能部署一個設定檔。 在這項更新中，您可以將多個設定檔部署至：
- 相同的使用者群組
- 相同的裝置群組
- 單一裝置

[在 Microsoft Intune 中透過 Zebra 行動延伸模組使用及管理 Zebra 裝置示範](../configuration/android-zebra-mx-overview.md)，了解如何在 Intune 中使用 MX。

適用於：Android

#### <a name="some-kiosk-settings-on-ios-devices-are-set-using-block-replacing-allow---4404075----"></a>iOS 裝置上的某些 kiosk 設定是設定為使用 [封鎖] 來取代 [允許]<!-- 4404075  -->
當您在 iOS 裝置上建立裝置限制設定檔時 ([裝置設定]   >  [設定檔]   >  [建立設定檔]   >  [iOS] (平台)  [裝置限制]  (設定檔類型) > [Kiosk]  )，您可以設定 [自動鎖定]  、[響鈴開關]  、[旋轉螢幕]  、[螢幕睡眠按鈕]  以及 [音量按鈕]  。

在這項更新中，這些值會是 [封鎖]  (封鎖功能) 和 [未設定]  (允許功能)。 若要查看設定，請前往[用以允許或限制功能的 iOS 裝置設定](../configuration/device-restrictions-ios.md#kiosk)。

適用於：iOS

#### <a name="use-face-id-for-password-authentication-on-ios-devices---4490704---"></a>在 iOS 裝置上使用 Face ID 進行密碼驗證<!-- 4490704 -->
當您建立 iOS 裝置的裝置限制設定檔時，您可以使用指紋作為密碼。 在這項更新中，指紋密碼設定也會允許臉部辨識 ([裝置設定]   > [設定檔]   > [建立設定檔]   > [iOS]  平台 > [裝置限制]  設定檔類型 > [密碼]  )。 因此，下列設定已變更：

- [指紋解除鎖定]  現為 [Touch ID 和 Face ID 解鎖]  。
- [指紋修改 (僅限監督對象)]  現為 [Touch ID 和 Face ID 修改 (僅限受監督)]  。

iOS 11.0 和更新版本可使用 Face ID。 若要查看這些設定，請前往[使用 Intune 來允許或限制功能的 iOS 裝置設定](../configuration/device-restrictions-ios.md#password)。

適用於：iOS

#### <a name="restricting-gaming-and-app-store-features-on-ios-devices-is-now-dependent-on-ratings-region---4593948---"></a>iOS 裝置上的限制遊戲和 App Store 功能現在與分級區域相依<!-- 4593948 -->
您可以在 iOS 裝置上允許或限制與遊戲、App Store 及檢視文件相關的功能 ([裝置設定]   > [設定檔]   > [建立設定檔]   > [iOS]  (平台) > [裝置限制]  (設定檔類型) > [App Store、文件檢視、遊戲]  )。 您也可以選擇分級區域，例如美國。

在這項更新中，「應用程式」  功能會移動成為「分級區域」  的子系，並相依於「分級區域」  。 若要查看這些設定，請前往[使用 Intune 來允許或限制功能的 iOS 裝置設定](../configuration/device-restrictions-ios.md#app-store-doc-viewing-gaming)。

適用於：iOS

### <a name="device-enrollment"></a>裝置註冊

#### <a name="windows-autopilot-support-for-hybrid-azure-ad-join---4809146--"></a>混合式 Azure AD Join 的 Windows Autopilot 支援<!-- 4809146-->
現有裝置的 Windows Autopilot 除了現有的 Azure AD Join 支援之外，現在也支援「混合式 Azure AD Join」。 適用於 Windows 10 1809 版和更新版本的裝置。 如需詳細資訊，請參閱[現有裝置的 Windows Autopilot](https://docs.microsoft.com/windows/deployment/windows-autopilot/existing-devices) \(部分機器翻譯)\。

### <a name="device-management"></a>裝置管理

#### <a name="see-the-security-patch-level-for-android-devices---4461911---"></a>請參閱 Android 裝置的安全性修補程式等級<!-- 4461911 -->
您現在可以查看 Android 裝置的安全性修補程式等級。 若要這樣做，請選擇 [Intune]   > [裝置]   > [所有裝置]  > 選擇裝置 > [硬體]  。
修補程式等級會列在 [作業系統]  區段中。

#### <a name="assign-scope-tags-to-all-managed-devices-in-a-security-group---3173810---"></a>將範圍標籤指派給安全性群組中的所有受控裝置<!-- 3173810 -->
您現在可以將範圍標籤指派給安全性群組，而安全性群組中的所有裝置也都會與這些範圍標籤建立關聯。 這些群組中的所有裝置也都會獲指派範圍標籤。 使用此功能設定之範圍標籤會覆寫以目前裝置範圍標記流程設定的範圍標籤。 如需詳細資訊，請參閱[針對分散式 IT 使用 RBAC 和範圍標籤](scope-tags.md) \(部分機器翻譯\)。

### <a name="device-security"></a>裝置安全性

#### <a name="use-keyword-search-with-security-baselines------"></a>搭配安全性基準使用關鍵字搜尋<!--  -->
建立或編輯[安全性基準設定檔](../protect/security-baselines.md#create-the-profile)時，您可以在新的「搜尋」  列中指定關鍵字，以將可用的設定群組篩選成包含您搜尋條件的設定。

#### <a name="the-security-baselines-feature-is-now-generally-available---3785395---"></a>安全性基準現已正式運作<!-- 3785395 -->
「安全性基準」  功能已結束預覽狀態，現已正式運作 (GA)。  這意謂著此功能已準備好在生產環境中使用。 不過，個別基準範本可以維持預覽狀態，並依據自己的排程進行評估及發行成 GA。

#### <a name="the-mdm-security-baseline-template-is-now-generally-available---3794072-4217151--3534649---"></a>MDM 安全性基準範本現已正式運作<!-- 3794072, 4217151,  3534649 -->
MDM 安全性基準範本現已結束預覽狀態，現已正式運作 (GA)。 GA 範本會識別為「2019 年 5 月的 MDM 安全性基準」  。  這是一個新範本，不是預覽版的升級。  作為新範本，您將必須檢閱[它包含的設定](../protect/security-baseline-settings-mdm.md)，然後建立新設定檔以將範本部署至您的裝置。 其他安全性基準範本可以繼續保持預覽狀態。 如需可用基準的清單，請參閱[可用的安全性基準](../protect/security-baselines.md#available-security-baselines)。  

除了成為新範本之外，「2019 年 5 月的 MDM 安全性基準」  範本還包含我們最近在「開發中」文章中宣佈的兩個設定：  
- 鎖定畫面上：在鎖定畫面上啟動語音啟動應用程式  
- DeviceGuard：在下次裝置重新開機時使用虛擬化型安全性 (VBS)。  

「2019 年 5 月的 MDM 安全性基準」  也包括新增數個新設定、移除其他設定，以及修訂一個設定的預設值。 如需從預覽版到 GA 的變更詳細清單，請參閱＜新範本的變更內容＞  。

#### <a name="security-baseline-versioning---3194322---"></a>安全性基準版本設定<!-- 3194322 -->
Intune 的安全性基準支援版本設定。 有了這項支援，在每個安全性基準的新版本發行時，您便可以更新現有的安全性基準設定檔以使用較新的基準版本，而不需從頭開始重新建立及部署新的基準。 此外，在 Intune 主控台中，您還可以檢視每個基準的相關資訊，例如您所擁有之使用基準的個別設定檔數目、您的設定檔使用多少個不同的基準版本，以及特定安全性基準的最新版本是何時發行的。  如需詳細資訊，請參閱**安全性基準**。

#### <a name="the-use-security-keys-for-sign-in-setting-has-moved---4501151---"></a>[使用安全性金鑰登入] 設定已移動<!-- 4501151 -->
在 [設定 Windows Hello 企業版]  的子設定中，已經找不到名為 [使用安全性金鑰登入]  的身分識別保護裝置組態設定。 它現在已是即使您未啟用「Windows Hello 企業版」，也一律可用的最上層設定。 如需詳細資訊，請參閱[身分識別保護](../protect/identity-protection-windows-settings.md)。

### <a name="role-based-access-control"></a>以角色為基礎的存取控制

#### <a name="new-permissions-for-assigned-group-admins---4504437-----"></a>所指派群組管理員的新權限<!-- 4504437   -->
Intune 內建的「學校管理員」角色現在具有「受管理的應用程式」的建立、讀取、更新及刪除 (CRUD) 權限。 這項更新意謂著如果您在「Intune 教育版」中被指派為群組管理員，您現在便可以建立、檢視、更新及刪除 iOS MDM Push Certificate、iOS MDM 伺服器權杖和 iOS VPP 權杖，以及[您具備的所有現有權限](https://docs.microsoft.com/intune-education/group-admin-delegate#group-admin-permissions)。 若要進行這其中任何一個動作，請前往 [租用戶設定]   > [iOS 裝置管理]  。  

#### <a name="applications-can-use-the-graph-api-to-call-read-operations-without-user-credentials---4655885---"></a>應用程式可以使用圖形 API 來呼叫讀取作業而無需使用者認證<!-- 4655885 -->
應用程式可以使用應用程式身分識別來呼叫「Intune 圖形 API」讀取作業，而無需使用者認證。 如需有關存取「適用於 Intune 的 Microsoft Graph API」的詳細資訊，請參閱[在 Microsoft Graph 中使用 Intune](https://docs.microsoft.com/graph/api/resources/intune-graph-overview?view=graph-rest-1.0) \(英文\)。

#### <a name="apply-scope-tags-to-microsoft-store-for-business-apps---4392555---"></a>將範圍標籤套用至商務用 Microsoft Store 應用程式<!-- 4392555 -->
您現在可以將範圍標籤套用至商務用 Microsoft Store 應用程式。 如需有關範圍標籤的詳細資訊，請參閱[針對分散式 IT 使用角色型存取控制 (RBAC) 和範圍標籤](scope-tags.md)。

## <a name="week-of-june-17-2019"></a>2019 年 6 月 17 日當週

### <a name="app-management"></a>應用程式管理

#### <a name="new-features-in-microsoft-intune-app"></a>Microsoft Intune 應用程式中的新功能
我們已在適用於 Android 的 Microsoft Intune 應用程式 (預覽) 中新增功能。 完全受控 Android 裝置上的使用者現在可以：  

* 透過 Intune 公司入口網站或 Microsoft Intune 應用程式，檢視及管理已註冊的裝置。
* 與其組織連絡以尋求支援。
* 將其意見反應傳送給 Microsoft。
* 若其組織已設定條款及條件，即可加以檢視。

## <a name="week-of-june-10-2019"></a>2019 年 6 月 10 日當週

### <a name="app-management"></a>應用程式管理

#### <a name="new-sample-apps-showing-intune-sdk-integration-available-on-github---2653471---"></a>可在 GitHub 上取得新的範例應用程式 (其會顯示 Intune SDK 整合)<!-- 2653471 -->
Msintuneappsdk GitHub 帳戶已新增適用於 iOS (Swift)、Android、Xamarin.iOS、Xamarin Forms 和 Xamarin.Android 的新範例應用程式。 這些應用程式旨在補充我們現有的文件，並提供如何將 Intune APP SDK 整合到您自己的行動裝置應用程式的示範。 如果您是需要其他 Intune SDK 指引的應用程式開發人員，請參閱以下連結的範例：
- [Chatr](https://github.com/msintuneappsdk/Chatr-Sample-Intune-iOS-App) \(英文\) - 原生的 iOS (Swift) 即時通訊應用程式，其會使用 Azure Active Directory 驗證程式庫 (ADAL) 來進行代理驗證。
- [Taskr](https://github.com/msintuneappsdk/Taskr-Sample-Intune-Android-App) \(英文\) -原生的 Android 待辦事項清單應用程式，其會使用 ADAL 來進行代理驗證。
- [Taskr](https://github.com/msintuneappsdk/Taskr-Sample-Intune-Xamarin-Android-Apps) \(英文\) - Xamarin.Android 待辦事項清單應用程式，其會使用 ADAL 來進行代理驗證，此存放庫也有 Xamarin.Forms 應用程式。
- [Xamarin.iOS 範例應用程式](https://github.com/msintuneappsdk/sample-intune-xamarin-ios) - 重點式的 Xamarin.iOS 範例應用程式。

## <a name="week-of-may-27-2019"></a>2019 年 5 月 27 日當週

### <a name="app-management"></a>應用程式管理

#### <a name="reporting-for-potentially-harmful-apps-on-android-devices---4223162---"></a>針對 Android 裝置上具潛在危害之應用程式的報告<!-- 4223162 -->
Intune 現在能針對 Android 裝置上具潛在危害的應用程式提供額外的報告資訊。 

## <a name="week-of-may-20-2019"></a>2019 年 5 月 20 日當週

### <a name="app-management"></a>應用程式管理

#### <a name="windows-company-portal-app---3316993---"></a>Windows 公司入口網站應用程式<!-- 3316993 -->
Windows 公司入口網站應用程式將新增標籤為 [裝置]  的頁面。 [裝置]  頁面會向終端使用者顯示其所有已註冊裝置。 使用者會在使用 10.3.4291.0 版或更新版本時，於公司入口網站看到這項變更。 如需設定公司入口網站的相關資訊，請參閱[如何設定 Microsoft Intune 公司入口網站應用程式](../apps/company-portal-app.md)。

### <a name="device-enrollment"></a>裝置註冊

#### <a name="autopilot-device-orderid-attribute-name-changed-to-group-tag----4659453---"></a>Autopilot 裝置 OrderID 屬性名稱變更為群組標籤 <!-- 4659453 -->

為了更容易查看，Autopilot 裝置上的 **OrderID** 屬性名稱已變更為**群組標籤**。 當您使用 CSV 上傳 Autopilot 裝置資訊時，必須使用群組標籤作為資料行標題，而非 OrderID。  

## <a name="week-of-may-13-2019-1905-service-release"></a>2019 年 5 月 13 日當週 (1905 服務版本)

### <a name="app-management"></a>應用程式管理

#### <a name="intune-policies-update-authentication-method-and-company-portal-app-installation---1927359----"></a>Intune 原則會更新驗證方法與公司入口網站應用程式安裝<!-- 1927359  -->
在已透過 [設定助理] 註冊的裝置上 (透過 Apple 的公司裝置註冊方法之一)，Intune 將不再支援公司入口網站 (當使用者從 App Store 手動安裝時)。 只有當您在註冊期間使用 Apple 設定助理進行驗證時，此變更才有意義。 此變更也只會影響透過下列各項註冊的 iOS 裝置：  
* Apple Configurator

* Apple Business Manager

* Apple School Manager

* Apple 裝置註冊方案 (DEP)

如果使用者從 App Store 安裝公司入口網站應用程式，接著嘗試透過它註冊這些裝置，則它們將會收到錯誤。 這些裝置應該只有已在註冊期間透過 Intune 自動推送時，才會使用公司入口網站。 位於 Azure 入口網站上 Intune 中的註冊設定檔將會更新，如此您就能指定裝置的驗證方式，以及它們是否會收到公司入口網站應用程式。 如果您想讓 DEP 裝置使用者擁有公司入口網站，將必須在註冊設定檔中指定喜好設定。 

此外，會在 iOS 公司入口網站應用程式中移除 [識別您的裝置]  畫面。 因此，想要啟用條件式存取或部署公司應用程式的管理員必須更新 DEP 註冊設定檔。 此需求只有在 DEP 註冊是透過安裝小幫手驗證時才適用。 在該情況下，您必須將公司入口網站推送到裝置。 若要這樣做，請選擇 [Intune]   > [裝置註冊]   > [Apple 註冊]   > [註冊計劃權杖]  > 選擇權杖 > [設定檔]  > 選擇設定檔 > [屬性]  > 將 [安裝公司入口網站]  設定為 [是]  。

若要在已經註冊的 DEP 裝置上安裝公司入口網站，您將必須移至 [Intune] > [用戶端應用程式]，然後使用應用程式設定原則來將它推送為受控應用程式。 

#### <a name="configure-how-end-users-update-a-line-of-business-lob-app-using-an-app-protection-policy---3568384---"></a>設定終端使用者如何使用應用程式保護原則來更新企業營運 (LOB) 應用程式<!-- 3568384 -->
您現在可以設定終端使用者可從何處取得企業營運 (LOB) 應用程式的更新版本。 終端使用者將可在 [應用程式最小版本]  條件式啟動對話方塊中看見此功能，其將提示終端使用者更新為 LOB 應用程式的最小版本。 您必須提供這些更新詳細資料作為 LOB 應用程式保護原則 (APP) 一部分。 此功能適用於 iOS 和 Android。 在 iOS 上，此功能需要整合 (或使用包裝工具包裝) 應用程式與 Intune SDK for iOS 10.0.7 版或更新版本。 在 Android 上，此功能需要最新版的公司入口網站。 若要設定終端使用者更新 LOB 應用程式的方式，應用程式需要透過金鑰 `com.microsoft.intune.myappstore` 傳送給它的受控應用程式設定原則。 傳送的值將定義終端使用者要從哪個存放區下載應用程式。 如果透過公司入口網站部署應用程式，則值必須為 `CompanyPortal`。 針對任何其他存放區，您必須輸入完整的 URL。

#### <a name="intune-management-extension-powershell-scripts---3734186----"></a>Intune 管理延伸模組 PowerShell 指令碼<!-- 3734186  -->
您可以設定 PowerShell 指令碼，以在裝置上使用使用者的管理員權限來執行。 如需詳細資訊，請參閱[在 Windows 10 裝置上的 Intune 中使用 PowerShell 指令碼](../apps/intune-management-extension.md)和 [Win32 應用程式管理](../apps/app-management.md)。

#### <a name="android-enterprise-app-management---4459905---"></a>Android 企業應用程式管理<!-- 4459905 -->
為讓 IT 系統管理員輕鬆地設定及使用 Android 企業管理，Intune 會自動新增四個通用 Android 企業相關應用程式到 Intune 系統管理主控台。 這四個 Android Enterprise 應用程式為下列應用程式：

- **[Microsoft Intune](https://play.google.com/store/apps/details?id=com.microsoft.intune)** - 用於 Android 企業完全受控案例。
- **[Microsoft Authenticator](https://play.google.com/store/apps/details?id=com.azure.authenticator)** - 協助您登入您的帳戶 (若您使用雙重要素驗證)。
- **[Intune 公司入口網站](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal)** - 用於應用程式保護原則 (APP) 與 Android 企業公司設定檔案例。
- [受控主螢幕](https://play.google.com/store/apps/details?id=com.microsoft.launcher.enterprise) - 用於 Android 企業專用/資訊站案例。

之前，IT 系統管理員需要在安裝期間於[受控 Google Play 商店](https://play.google.com/store/apps)中手動尋找及核准這些應用程式。 此變更移除了先前那些手動步驟，讓客戶可以更輕鬆、更快速地使用 Android 企業管理。

系統管理員在第一次連線到其 Intune 租用戶的受控 Google Play 商店時，將會看到這四個應用程式自動新增到其 Intune 應用程式清單。 如需詳細資訊，請參閱[將您的 Intune 帳戶連結到受控 Google Play 帳戶](../enrollment/connect-intune-android-enterprise.md)。 針對已連結其租用戶或已使用 Android 企業的租用戶，系統管理員不需要採取任何動作。 這四個應用程式會在 2019 年 5 月服務推出完成後的 7 天內自動顯示。

### <a name="device-configuration"></a>裝置設定

#### <a name="updated-pfx-certificate-connector-for-microsoft-intune---1533038---"></a>已更新適用於 Microsoft Intune 的 PFX 憑證連接器<!-- 1533038 -->
我們已經發行 [Microsoft Intune 的 PFX 憑證連接器](../protect/certficates-pfx-configure.md#whats-new-for-connectors)的更新，解決現有 PFX 憑證繼續重新處理的問題，此問題造成連接器停止處理新要求。

#### <a name="intune-security-tasks-for-defender-atp-in-public-preview---3208597---"></a>Defender ATP 的 Intune 安全性工作 (公開預覽)<!-- 3208597 -->
在公開預覽中，您可以使用 Intune 來管理 [Microsoft Defender 進階威脅防護 (ATP) 的安全性工作](../protect/atp-manage-vulnerabilities.md)。 這會與 ATP 整合，並新增一個以風險為基礎的方法來探索、設定優先順序及補救端點弱點和錯誤設定，同時減少從探索到風險降低之間的時間。

#### <a name="check-for-a-tpm-chipset-in-a-windows-10-device-compliance-policy---3617671---idstaged--"></a>在 Windows 10 裝置合規性政策中檢查是否有 TPM 晶片組<!-- 3617671   idstaged-->
許多 Windows 10 及更新版本的裝置都具有信賴平台模組 (TPM) 晶片組。 這個更新引進新的合規性設定，此設定會檢查裝置上的 TPM 晶片版本。

[Windows 10 與更新版本的合規性原則設定](../protect/compliance-policy-create-windows.md#device-security)說明此設定。

適用於：Windows 10 及更新版本

#### <a name="prevent-end-users-from-modifying-their-personal-hotspot-and-disable-siri-server-logging-on-ios-devices---4097904-----"></a>在 iOS 裝置上，防止終端使用者修改其個人熱點，並停用 Siri 伺服器記錄<!-- 4097904   -->  
您會在 iOS 裝置上建立裝置限制設定檔 ([裝置設定]   > [設定檔]   > [建立設定檔]   > 選取 [iOS] 作為平台  > 選取 [裝置限制]  作為設定檔類型)。 此更新包括您可以設定的新設定：

- **內建應用程式**：在伺服器端記錄 Siri 命令
- **無線**：使用者修改個人熱點 (僅限受監督)

若要查看這些設定，請移至[適用於 iOS 的內建應用程式設定](../configuration/device-restrictions-ios.md#built-in-apps)和[適用於 iOS 的無線設定](../configuration/device-restrictions-ios.md#wireless)。

適用於：iOS 12.2 與更新版本

#### <a name="new-classroom-app-device-restriction-settings-for-macos-devices---4097905-----"></a>適用於 macOS 裝置的新教室應用程式裝置限制設定<!-- 4097905   --> 
您可以為 macOS 裝置建立裝置設定設定檔 ([裝置設定]   > [設定檔]   > [建立設定檔]   > 選取 [macOS]  作為平台 > 選取 [裝置限制]  作為設定檔類型)。 這項更新包括新的教室應用程式設定、封鎖螢幕擷取畫面的選項，以及停用「iCloud 照片圖庫」的選項。

若要查看目前的設定，請前往 [macOS 裝置設定以使用 Intune 允許或限制功能](../configuration/device-restrictions-macos.md)。

適用於：macOS

#### <a name="the-ios-password-to-access-app-store-setting-is-renamed---4557891----"></a>將用來存取 App Store 設定的 iOS 密碼重新命名<!-- 4557891  -->
將 [存取 App Store 的密碼]  設定重新命名為 [所有購買都需要 iTunes 密碼]  ([裝置設定]   > [設定檔]   > [建立設定檔]   > [iOS]  (針對平台) > [裝置限制]  (針對設定檔類型) > [App Store、文件檢視、遊戲]  )。

若要查看可用的設定，請移至 [App Store、文件檢視、遊戲的 iOS 設定](../configuration/device-restrictions-ios.md#app-store-doc-viewing-gaming)。

適用於：iOS

#### <a name="microsoft-defender-advanced-threat-protection--baseline--preview----3754134---"></a>Microsoft Defender 進階威脅防護基準 (預覽)<!--  3754134 -->
我們已新增 [Microsoft Defender 進階威脅防護](../protect/security-baseline-settings-defender-atp.md)設定的安全性基準預覽。 當您的環境符合使用 [Microsoft Defender 進階威脅防護](../protect/advanced-threat-protection.md#prerequisites)的必要條件時，即可使用此基準。

### <a name="device-enrollment"></a>裝置註冊

#### <a name="windows-enrollment-status-page-esp-is-now-generally-available---3605348---"></a>Windows 註冊狀態頁面 (ESP) 現已全面上市<!-- 3605348 -->
註冊狀態頁面現已結束預覽。 如需詳細資訊，請參閱[設定註冊狀態頁面](../enrollment/windows-enrollment-status.md)。


#### <a name="intune-user-interface-update---autopilot-enrollment-profile-creation---4593669---"></a>Intune 使用者介面更新 - 建立 Autopilot 註冊設定檔<!-- 4593669 -->
建立 Autopilot 註冊設定檔的使用者介面已更新，以符合 Azure 使用者介面樣式。 如需詳細資訊，請參閱[建立 Autopilot 註冊設定檔](../enrollment/enrollment-autopilot.md#create-an-autopilot-deployment-profile)。 接下來，將其他 Intune 案例更新為這個新的 UI 樣式。

#### <a name="enable-autopilot-reset-for-all-windows-devices---4225665---"></a>針對所有 Windows 裝置啟用 Autopilot 重設<!-- 4225665 -->
Autopilot 重設目前適用於所有 Windows 裝置，即使未設定為使用註冊狀態頁面的裝置也適用。 如果未在初始裝置註冊期間針對裝置設定註冊狀態頁面，則裝置將在登入之後直接前往桌面。 在 Intune 中最多可能需要 8 小時來進行同步處理並顯示符合規範。 如需詳細資訊，請參閱[使用遠端 Windows Autopilot 重設來重設裝置](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-autopilot-reset-remote) \(部分機器翻譯\)。

#### <a name="exact-imei-format-not-required-when-searching-all-devices--30407680---"></a>搜尋所有裝置時不需要精確的 IMEI 格式<!--30407680 -->
您不需要在搜尋**所有裝置**時，於 IMEI 編號中包含空格。

#### <a name="deleting-a-device-in-the-apple-portal-will-be-reflected-in-the-intune-portal--2489996---"></a>在 Apple 入口網站刪除裝置將反映在 Intune 入口網站中<!--2489996 -->
若從 Apple 的裝置註冊計劃或 Apple 商務管理員入口網站刪除裝置，在下次同步時，會自動將該裝置從 Intune 刪除。

### <a name="the-enrollment-status-page-now-tracks-win32-apps---2714451---"></a>註冊狀態頁面現在會追蹤 Win32 應用程式<!-- 2714451 -->
這只適用於執行 Windows 10 1903 版及更新版本的裝置。 如需詳細資訊，請參閱[設定註冊狀態頁面](../enrollment/windows-enrollment-status.md)。

### <a name="device-management"></a>裝置管理

#### <a name="reset-and-wipe-devices-in-bulk-by-using-the-graph-api---3295288---"></a>使用圖形 API 大量重設及抹除裝置<!-- 3295288 -->
您現在可以使用圖形 API 大量重設及抹除最多 100 部裝置。

### <a name="monitor-and-troubleshoot"></a>監視及疑難排解

#### <a name="the-encryption-report-is-out-of-public-preview---4587546--------"></a>加密報表已結束公開預覽<!-- 4587546      -->
現已正式推出[適用於 BitLocker 和裝置加密的報表](../protect/encryption-monitor.md)，其不再是公開預覽的一部分。

<!-- ########################## -->

#### <a name="outlook-signature-and-biometric-settings-for--ios-and-android-devices---4050557---"></a>適用於 iOS 和 Android 裝置的 Outlook 簽章和生物特徵辨識設定<!-- 4050557 -->
您現在可以指定是否要在 iOS 和 Android 裝置上的 Outlook 中啟用預設簽章。 此外，您可以選擇允許使用者在 iOS 上的 Outlook 中變更生物特徵辨識設定。

## <a name="week-of-may-6-2019"></a>2019 年 5 月 6 日當週

### <a name="device-configuration"></a>裝置設定

#### <a name="network-access-control-nac-support-for-f5-access-for-ios-devices---4500808---"></a>iOS 裝置 F5 Access 的網路存取控制 (NAC) 支援<!-- 4500808 -->

F5 發行了 BIG-IP 13 的更新，可在 Intune 中於 iOS 上的 F5 Access 提供 NAC 功能。 若要使用此功能：

- 將 BIG-IP 更新為 13.1.1.5 版。 不支援 BIG-IP 14。
- 針對 NAC 整合 BIG-IP 與 Intune。 步驟位於 [Overview:Configuring APM for device posture checks with endpoint management systems](https://techdocs.f5.com/kb/en-us/products/big-ip_apm/manuals/product/apm-client-configuration-7-1-6/6.html) (概觀：設定 APM 以向端點管理系統確認裝置狀態)。
- 在 Intune 中，確認 VPN 設定檔中的 [啟用網路存取控制 (NAC)]  設定。

若要查看可用的設定，請前往[在 iOS 裝置上進行 VPN 設定](../configuration/vpn-settings-ios.md)。

適用於：iOS

#### <a name="updated-pfx-certificate-connector-for-microsoft-intune---doc-vso-1521237----"></a>已更新適用於 Microsoft Intune 的 PFX 憑證連接器<!-- doc-vso 1521237  -->  
我們發行了[適用於 Microsoft Intune 的 PFX 認證連接器](../protect/certficates-pfx-configure.md#whats-new-for-connectors)更新，可將輪詢間隔從 5 分鐘縮短為 30 秒。




## <a name="notices"></a>通知

[!INCLUDE [Intune notices](../includes/intune-notices.md)]

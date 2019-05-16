---
title: 開發中 - Microsoft Intune
titleSuffix: ''
description: 正在開發的 Microsoft Intune 功能
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/29/2019
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
ms.openlocfilehash: 7bba992c79f69a126f0199d9cdac52779910ff38
ms.sourcegitcommit: 068c4e4bc6e6d778ece4a83d000128c4d2b732db
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 04/29/2019
ms.locfileid: "64910319"
---
# <a name="in-development-for-microsoft-intune---may-2019"></a>Microsoft Intune 正在開發的項目 - 2019 年 5 月

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


<!-- 1905 start-->


### <a name="deleting-a-device-in-the-apple-portal-will-be-reflected-in-the-intune-portal---2489996---"></a>在 Apple 入口網站刪除裝置將反映在 Intune 入口網站中 <!--2489996 -->
若從 Apple 的裝置註冊計劃或 Apple 商務管理員入口網站刪除裝置，在下次同步時，會自動將該裝置從 Intune 刪除。

### <a name="baseline-support-for-keyword-search-----3082036-----------"></a>關鍵字搜尋的基準支援  <!-- 3082036         -->
建立或編輯安全性基準設定檔時，您很快就可以使用搜尋功能來篩選主控台中顯示的設定。   

### <a name="reset-and-wipe-devices-in-bulk-by-using-the-graph-api----3295288---"></a>使用圖形 API 大量重設及抹除裝置 <!-- 3295288 -->
您可以使用圖形 API 大量重設及抹除最多 100 部裝置。

### <a name="check-for-a-tpm-chipset-in-a-windows-10-device-compliance-policy----3617671---"></a>在 Windows 10 裝置合規性政策中檢查是否有 TPM 晶片組 <!-- 3617671 -->
許多 Windows 10 及更新版本的裝置都具有信賴平台模組 (TPM) 晶片組。 這個更新引進新的合規性設定，此設定會檢查裝置上的 TPM 晶片版本。 

[Windows 10 與更新版本的合規性原則設定](compliance-policy-create-windows.md#device-security)說明此設定。

適用對象：Windows 10 和更新版本

### <a name="intune-management-extension-powershell-scripts-----3734186------"></a>Intune 管理延伸模組 PowerShell 指令碼  <!-- 3734186    -->
您將能設定 PowerShell 指令碼以在裝置上使用使用者的系統管理員權限執行。 如需詳細資訊，請參閱[在 Windows 10 裝置上的 Intune 中使用 PowerShell 指令碼](intune-management-extension.md)。

### <a name="prevent-end-users-from-modifying-their-personal-hotspot-and-disable-siri-server-logging-on-ios-supervised-devices----4097904----"></a>防止終端使用者在 iOS 售監督的裝置上修改其個人熱點並停用 Siri 伺服器記錄 <!-- 4097904  --> 
您會在 iOS 裝置上建立裝置限制設定檔 ([裝置設定] > [設定檔] > [建立設定檔] > 選取 [iOS] 作為平台 > 選取 [裝置限制] 作為設定檔類型)。 此更新包括您可以設定的新設定：

- 個人熱點
- Siri 伺服器記錄

若要查看目前的設定，請前往 [iOS 裝置設定以允許或限制功能](device-restrictions-ios.md)。 

適用於：iOS 12.2 與更新版本

### <a name="new-classroom-app-device-restriction-settings-for-dep-enrolled-macos-devices----4097905----"></a>適用於 DEP 註冊 macOS 裝置的新教室應用程式裝置限制設定 <!-- 4097905  --> 
您可以為 macOS 裝置建立裝置設定設定檔 ([裝置設定] > [設定檔] > [建立設定檔] > 選取 [macOS] 作為平台 > 選取 [裝置限制] 作為設定檔類型)。 此更新包括適用於 DEP 註冊裝置的新教室應用程式設定，以及可用於停用 iCloud 照片圖庫的選項。

若要查看目前的設定，請前往 [macOS 裝置設定以使用 Intune 允許或限制功能](device-restrictions-macos.md)。

適用於：macOS 10.14.4 與更新版本

### <a name="android-enterprise-app-management----4459905-idready---"></a>Android 企業應用程式管理 <!-- 4459905 idready -->
為讓 IT 系統管理員輕鬆地設定及使用 Android 企業管理，Intune 會自動新增四個通用 Android 企業相關應用程式到 Intune 系統管理主控台。 四個 Android 企業應用程式如下：

- **[Microsoft Intune](https://play.google.com/store/apps/details?id=com.microsoft.intune)** - 用於 Android 企業完全受控案例。
- **[Microsoft Authenticator](https://play.google.com/store/apps/details?id=com.azure.authenticator)** -  協助您登入您的帳戶 (若您使用雙因素驗證)。
- **[Intune 公司入口網站](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal)** - 用於 應用程式保護原則 (APP) 與 Android 企業公司設定檔案例。
- [受控家用案例](https://play.google.com/store/apps/details?id=com.microsoft.launcher.enterprise) - 用於 Android 企業專用/資訊站案例。

之前，IT 系統管理員需要在安裝期間於[受控 Google Play 商店](https://play.google.com/store/apps)中手動尋找及核准這些應用程式。 此變更移除了先前那些手動步驟，讓客戶可以更輕鬆、更快速地使用 Android 企業管理。

系統管理員在第一次連線到其 Intune 租用戶的受控 Google Play 商店時，將會看到這四個應用程式自動新增到其 Intune 應用程式清單。 如需詳細資訊，請參閱[將您的 Intune 帳戶連結到受控 Google Play 帳戶](connect-intune-android-enterprise.md)。 針對已連結其租用戶或已使用 Android 企業的租用戶，系統管理員不需要採取任何動作。 在 2019 年 5 月服務推出之後 7 天內，那四個應用程式將會自動顯示。

<!-- 1904 start-->

### <a name="advanced-settings-for-windows-defender-firewall----1311949---"></a>Windows Defender 防火牆的進階設定 <!-- 1311949 -->
您很快地將可以使用 Intune 來為 Windows Defender 管理用戶端上的自訂防火牆規則。 規則可指定應用程式、網路位址和連接埠的輸入及輸出行為。 


### <a name="device-users-can-view-all-managed-apps-theyve-installed-or-tried-to-install----2352913---"></a>裝置使用者可檢視其安裝或嘗試安裝的所有受控應用程式 <!-- 2352913 -->
Windows 的公司入口網站會列出在使用者裝置上所安裝所有受控應用程式，包括必要及可用的應用程式。 使用者將能夠檢視嘗試及正在擱置的應用程式安裝，以及其目前的狀態。 若您的組織沒有將應用程式設為必要或可用，使用者會看見一個訊息，說明沒有安裝任何公司應用程式。 使用者也將能夠根據安裝狀態排序或篩選其應用程式。

### <a name="use-applicability-rules-when-creating-windows-10-device-configuration-profiles----2549910---"></a>在建立 Windows 10 裝置組態設定檔時使用「適用性規則」 <!-- 2549910 -->
您可以建立 Windows 10 裝置組態設定檔 ([裝置設定] > [設定檔] > [建立設定檔] > 針對平台選取 [Windows 10])。 您將能夠建立**適用性規則**，讓設定檔只套用到特定版本。 例如，您可以建立設定檔來啟用某些 BitLocker 設定。 一旦您新增設定檔後，您便可以使用適用性規則，將設定檔設為只套用到執行 Windows 10 企業版的裝置。

適用於： 
- Windows 10 及更新版本

###  <a name="intune-security-tasks-for-defender-atp-in-public-preview----3208597---"></a>Defender ATP 的 Intune 安全性工作 (公開預覽) <!-- 3208597 -->
作為即將進入公開預覽的功能，Intune 將會針對新宣告的 Microsoft Defender 威脅及弱點管理新增安全性工作。  透過這項整合，Windows Defender ATP (WDATP) 中的安全性操作管理員能更有效地針對 Intune 管理員面對的新威脅，傳遞建議的補救措施。 新增安全性工作，可新增一種風險式的方法，探索、優先處理及補救端點弱點和錯誤設定。

或要深入了解 Intune 中的安全性工作，請參閱 [using Intune security tasks to extend Microsoft Defender ATP’s Threat and Vulnerability Management](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/Microsoft-Intune-security-tasks-extend-Microsoft-Defender-ATP-s/ba-p/369857) (使用 Intune 安全性工作延伸 Microsoft Defender ATP 的威脅及弱點管理) 部落格文章。 

### <a name="windows-defender-advanced-threat-protection-baseline----3754134---"></a>Windows Defender 進階威脅防護基準 <!-- 3754134 -->
我們將會新增新的基準，協助您設定 Windows Defender 進階威脅防護設定。



## <a name="notices"></a>通知

[!INCLUDE [Intune notices](./includes/intune-notices.md)]

### <a name="see-also"></a>請參閱
如需近期發展的詳細資料，請參閱 [Microsoft Intune 的新功能](whats-new.md)。



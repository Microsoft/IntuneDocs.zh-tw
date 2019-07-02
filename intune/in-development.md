---
title: 開發中 - Microsoft Intune
titleSuffix: ''
description: 正在開發的 Microsoft Intune 功能
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 06/28/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 633bf52084ad261f768cb4e59aaf4ce0ab5cd5bc
ms.sourcegitcommit: 46f4d3d160e18aeab9de7477eedc8351fbb78c85
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/29/2019
ms.locfileid: "67468719"
---
# <a name="in-development-for-microsoft-intune---july-2019"></a>Microsoft Intune 正在開發的項目 - 2019 年 7 月

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

### <a name="device-users-can-view-all-managed-apps-theyve-installed-or-tried-to-install----2352913---"></a>裝置使用者可檢視其安裝或嘗試安裝的所有受控應用程式 <!-- 2352913 -->
Windows 的公司入口網站會列出所有安裝在使用者裝置上 (必要及可用的) 受控應用程式。 使用者將能夠檢視嘗試及正在擱置的應用程式安裝，以及其目前的狀態。 若您的組織沒有將應用程式設為必要或可用，使用者會看見一個訊息，說明沒有安裝任何公司應用程式。 使用者也將能夠根據安裝狀態排序或篩選其應用程式。

### <a name="customized-notifications-for-users-and-groups-------16766574-----"></a>使用者和群組的自訂的通知    <!-- 16766574   -->
您很快就可以從 iOS 和您使用 Intune 管理的 Android 裝置上的使用者將公司入口網站應用程式傳送自訂的特定推播通知。 這些自訂的通知不會繫結至特定的 Intune 功能和可用於任何用途，需要，包括一般通知，您想要傳送部分或所有員工。  

### <a name="configure-app-notification-content-for-organization-accounts----2576686---"></a>設定應用程式通知內容的組織帳戶 <!-- 2576686 -->
Intune 應用程式保護原則在 Android 和 iOS 裝置上的 （應用程式） 可讓您控制應用程式通知內容的組織帳戶。 這項功能會需要從應用程式的支援，而且不可能適用於所有的應用程式啟用應用程式。 如需 APP 的詳細資訊，請參閱[什麼是應用程式防護原則？](app-protection-policy.md)

### <a name="available-google-play-app-reporting-for-android-work-profiles----3041956----"></a>報告 Android 工作設定檔的可用 Google Play 應用程式 <!-- 3041956  -->
針對安裝在 Android 工作設定檔裝置上的可用應用程式，您可以檢視應用程式安裝狀態，以及受控 Google Play 應用程式的安裝版本。 如需詳細資訊，請參閱[如何監視應用程式保護原則](app-protection-policies-monitor.md)、[使用 Intune 管理 Android 工作設定檔裝置](android-enterprise-overview.md)及[受控的 Google Play 應用程式類型](apps-add-android-for-work.md#managed-google-play-app-type)。

<!-- ***********************************************-->
## <a name="device-configuration"></a>裝置設定


### <a name="support-for-ikev2-vpn-profiles-for-ios----1943438---"></a>支援 iOS 版的 IKEv2 VPN 設定檔 <!-- 1943438 -->
您可以使用 IKEv2 通訊協定建立 iOS 原生 VPN 用戶端的 VPN 設定檔。 IKEv2 是 [裝置設定]   > [設定檔]   > [建立設定檔]   > [iOS]  (平台) > [VPN]  (設定檔類型) > [設定]  中的新連線類型。

這些 VPN 設定檔會設定原生的 VPN 用戶端。 因此，不會有 VPN 用戶端應用程式安裝或推送到受控裝置。 這項功能需要向 Intune 註冊裝置 (MDM 註冊)。

若要查看您目前可以設定的 VPN 設定，請前往[在 Microsoft Intune 中的 iOS 裝置上設定 VPN 設定](vpn-settings-ios.md)。

適用於：iOS

### <a name="use-applicability-rules-when-creating-windows-10-device-configuration-profiles----2549910---"></a>在建立 Windows 10 裝置組態設定檔時使用「適用性規則」 <!-- 2549910 -->
您可以建立 Windows 10 裝置組態設定檔 ([裝置設定]   > [設定檔]   > [建立設定檔]   > 針對平台選取 [Windows 10]  )。 您將能夠建立**適用性規則**，讓設定檔只套用到特定版本。 例如，您可以建立設定檔來啟用某些 BitLocker 設定。 一旦您新增設定檔後，您便可以使用適用性規則，將設定檔設為只套用到執行 Windows 10 企業版的裝置。

適用於： 
- Windows 10 及更新版本

### <a name="administrative-templates-for-group-policy---------3510695---"></a>群組原則的系統管理範本     <!--  3510695 -->
為協助改善雲端裝置的安全性，我們將發行系統管理範本，讓您使用 Intune 設定選取適用於 Windows 電腦的群組原則設定。  這些範本會使用原則設定服務提供者 (CSP)，提供多達 2500 項的 Office、Windows 和 OneDrive 其他設定。

### <a name="manage-filevault-for-macos-------3858502--1210104-----"></a>管理適用於 macOS 的 FileVault   <!--  3858502 + 1210104   -->
您可以使用 Intune endpoint protection 裝置組態設定檔來管理的 macOS 裝置的 FileVault 金鑰加密。 這包括委付的檢視，以及輪替加密金鑰，您公司的裝置。 終端使用者將能夠擷取這些金鑰，透過公司入口網站。

### <a name="advanced-settings-for-windows-defender-firewall-------1311949-------"></a>Windows Defender 防火牆的進階設定   <!--  1311949     -->
作為公開預覽版，您很快地將可以使用 Intune 來為 Windows Defender 管理用戶端上的自訂防火牆規則。  

### <a name="new-configuration-designer-when-creating-an-oemconfig-profile-for-android-enterprise----3712769----"></a>新的組態設計工具時建立 OEMConfig 設定檔的 Android 企業 <!-- 3712769  -->
在 Intune 中，您可以建立使用 OEMConfig 應用程式的裝置組態設定檔 (裝置組態 > 設定檔 > 建立設定檔 > Android 的企業平台 > OEMConfig 設定檔類型)。 當您這樣做時，JSON 編輯器隨即開啟範本與您變更的值。 此更新包括改善的使用者經驗顯示內嵌在應用程式，包括標題、 描述及更多詳細資料與設定設計工具。 JSON 編輯器仍然可用，並顯示您在組態設計工具中進行的任何變更。

若要查看目前的設定，請前往[使用使用和管理 Android Enterprise 裝置 OEMConfig](android-oem-configuration-overview.md)。

適用於：Android Enterprise


<!-- ***********************************************-->
## <a name="device-management"></a>裝置管理

### <a name="improve-device-location---3855417---"></a>提升裝置位置<!-- 3855417 -->
您可以放大裝置使用的確切的座標**尋找裝置**動作。 如需有關如何尋找遺失的 iOS 裝置的詳細資訊，請參閱 <<c0> [ 尋找遺失的 iOS 裝置](device-locate.md)。

### <a name="configure-automatic-device-clean-up-time-limit-down-to-30-days---4231059----"></a>設定自動裝置清除到 30 天的時間限制 <!--4231059  -->
您可以設定自動裝置清除時間限制越短越好 （而不是目前的限制為 90 天） 最後一個登入之後的 30 天。 若要這樣做，請前往**Intune** > **裝置** > **安裝** > **裝置清除設定規則**。


<!-- ***********************************************-->
## <a name="security"></a>安全性

### <a name="import-and-export-security-baselines------3408610------------"></a>匯入和匯出的安全性基準    <!--3408610          -->  
我們將新增匯出和匯入安全性基準，因此就可以 Intune 環境之間共用它們，讓您與您的自訂功能。



<!-- ***********************************************-->
## <a name="notices"></a>通知

[!INCLUDE [Intune notices](./includes/intune-notices.md)]

## <a name="see-also"></a>請參閱
如需近期發展的詳細資料，請參閱 [Microsoft Intune 的新功能](whats-new.md)。



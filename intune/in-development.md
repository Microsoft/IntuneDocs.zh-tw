---
title: 開發中 - Microsoft Intune
titleSuffix: ''
description: 正在開發的 Microsoft Intune 功能
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 06/03/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: bc5ea7076e77e5071724168fab58fa78f59601c4
ms.sourcegitcommit: 7ceae61e036ccf8b33704751b0b39fee81944072
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2019
ms.locfileid: "66744321"
---
# <a name="in-development-for-microsoft-intune---june-2019"></a>Microsoft Intune 正在開發的項目 - 2019 年 6 月

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

<!-- ***********************************************-->
### <a name="app-management"></a>應用程式管理

#### <a name="device-users-can-view-all-managed-apps-theyve-installed-or-tried-to-install----2352913---"></a>裝置使用者可檢視其安裝或嘗試安裝的所有受控應用程式 <!-- 2352913 -->
Windows 的公司入口網站會列出所有安裝在使用者裝置上 (必要及可用的) 受控應用程式。 使用者將能夠檢視嘗試及正在擱置的應用程式安裝，以及其目前的狀態。 若您的組織沒有將應用程式設為必要或可用，使用者會看見一個訊息，說明沒有安裝任何公司應用程式。 使用者也將能夠根據安裝狀態排序或篩選其應用程式。

#### <a name="available-google-play-app-reporting-for-android-work-profiles----3041956---"></a>報告 Android 工作設定檔的可用 Google Play 應用程式 <!-- 3041956 -->
針對安裝在 Android 工作設定檔裝置上的可用應用程式，您可以檢視應用程式安裝狀態，以及受控 Google Play 應用程式的安裝版本。 如需詳細資訊，請參閱[如何監視應用程式保護原則](app-protection-policies-monitor.md)、[使用 Intune 管理 Android 工作設定檔裝置](android-enterprise-overview.md)及[受控的 Google Play 應用程式類型](apps-add-android-for-work.md#managed-google-play-app-type)。

#### <a name="configure-which-browser-is-allowed-to-link-to-organization-data----3145939---"></a>設定允許連結至組織資料的瀏覽器 <!-- 3145939 -->
Android 和 iOS 裝置上的 Intune 應用程式防護原則 (APP) 可讓您將組織網頁連結傳送給 Intune Managed Browser 或 Microsoft Edge 之外的特定瀏覽器。  如需 APP 的詳細資訊，請參閱[什麼是應用程式防護原則？](app-protection-policy.md)

#### <a name="installed-apps-page-on-the-company-portal-website-----4224326---"></a>公司入口網站上的已安裝應用程式頁面  <!-- 4224326 -->
[公司入口網站](https://portal.manage.microsoft.com/)會包含新的頁面，向使用者顯示所有已安裝在其裝置上的應用程式。 這份清單包括可用的應用程式和其組織所需應用程式。 在這個頁面中，使用者可以看到其裝置上的應用程式安裝與需求狀態。 如需公司入口網站的詳細資訊，請參閱[使用 Intune 公司入口網站](/intune-user-help/using-the-intune-company-portal-website.md)和[如何設定 Microsoft Intune 公司入口網站應用程式](company-portal-app.md)。

#### <a name="call-graph-api-read-operations-from-an-application-without-user-credentials----4655885---"></a>從沒有使用者認證的應用程式中呼叫圖形 API 讀取作業 <!-- 4655885 -->
應用程式可以使用無使用者認證的應用程式身分識別呼叫 Intune 圖形 API 讀取作業。 若要進一步了解，請參閱 [Get access without a user](https://docs.microsoft.com/graph/auth-v2-service) (無使用者的存取)。

<!-- ***********************************************-->
### <a name="device-configuration"></a>裝置設定


#### <a name="support-for-ikev2-vpn-profiles-for-ios----1943438---"></a>支援 iOS 版的 IKEv2 VPN 設定檔 <!-- 1943438 -->
您可以使用 IKEv2 通訊協定建立 iOS 原生 VPN 用戶端的 VPN 設定檔。 IKEv2 是 [裝置設定]   > [設定檔]   > [建立設定檔]   > [iOS]  (平台) > [VPN]  (設定檔類型) > [設定]  中的新連線類型。

這些 VPN 設定檔會設定原生的 VPN 用戶端。 因此，不會有 VPN 用戶端應用程式安裝或推送到受控裝置。 這項功能需要向 Intune 註冊裝置 (MDM 註冊)。

若要查看您目前可以設定的 VPN 設定，請前往[在 Microsoft Intune 中的 iOS 裝置上設定 VPN 設定](vpn-settings-ios.md)。

適用於：iOS

#### <a name="configure-settings-for-kernel-extensions-on-macos-devices----20430240---"></a>在 macOS 裝置上設定核心延伸模組的設定 <!-- 20430240 -->
在 macOS 裝置上，您可以建立裝置組態設定檔 ([裝置設定]   > [設定檔]   > [建立設定檔]  > 針對平台選擇 [macOS]  )。 未來的更新會包含新設定群組，讓您在裝置上設定及使用核心延伸模組。

適用於：macOS 10.13.2 和更新版本

#### <a name="baseline-support-for-keyword-search-----3082036-----------"></a>關鍵字搜尋的基準支援  <!-- 3082036         -->
建立或編輯安全性基準設定檔時，您很快就可以使用搜尋功能  來篩選主控台中顯示的設定。   

#### <a name="use-applicability-rules-when-creating-windows-10-device-configuration-profiles----2549910---"></a>在建立 Windows 10 裝置組態設定檔時使用「適用性規則」 <!-- 2549910 -->
您可以建立 Windows 10 裝置組態設定檔 ([裝置設定]   > [設定檔]   > [建立設定檔]   > 針對平台選取 [Windows 10]  )。 您將能夠建立**適用性規則**，讓設定檔只套用到特定版本。 例如，您可以建立設定檔來啟用某些 BitLocker 設定。 一旦您新增設定檔後，您便可以使用適用性規則，將設定檔設為只套用到執行 Windows 10 企業版的裝置。

適用於： 
- Windows 10 及更新版本

#### <a name="apps-from-the-store-only-setting-for-windows-10-devices-includes-more-configuration-options----2697002----"></a>Windows 10 裝置的 [Apps from the store only] \(僅限來自 Store 的應用程式\) 設定包含更多設定選項 <!-- 2697002  -->

當您建立 Windows 裝置的裝置限制設定檔時，您可以使用 [Apps from the store only] \(僅限來自 Store 的應用程式\)  設定，讓使用者只安裝來自 Windows App Store 的應用程式 ([裝置設定]   > [設定檔]   > [建立設定檔]   > [Windows 10 及更新版本]  (平台) > [裝置限制]  (設定檔類型))。 在未來的更新中，這項設定會擴展以支援更多選項。 

若要查看目前的設定，請前往[使用 Intune 允許或限制功能的 Windows 10 (及更新版本) 裝置設定](device-restrictions-windows-10.md#app-store)。

適用對象：Windows 10 和更新版本

#### <a name="deploy-multiple-zebra-mobility-extensions-device-profiles-to-a-device-same-user-group-or-same-devices-group----4089955---"></a>將多個 Zebra 行動延伸模組的裝置設定檔部署至裝置、相同的使用者群組或裝置群組 <!-- 4089955 -->
在 Intune 中，您可以在裝置組態設定檔中使用 Zebra 行動延伸模組 (MX)，來自訂設定或將非內建的設定新增至 Intune。 目前，一部裝置只能部署一個設定檔。 在未來的更新中，您將能夠部署多個設定檔至：

- 相同的使用者群組
- 相同的裝置群組
- 單一裝置

[在 Microsoft Intune 中透過 Zebra 行動延伸模組使用及管理 Zebra 裝置](android-zebra-mx-overview.md)示範如何在 Intune 中使用 MX。

適用於：Android

#### <a name="some-kiosk-settings-on-ios-devices-are-set-using-block-replacing-allow----4404075----"></a>iOS 裝置上的某些 kiosk 設定是設定為使用 [封鎖] 來取代 [允許] <!-- 4404075  -->
當您在 iOS 裝置上建立裝置限制設定檔時 ([裝置設定]   > [設定檔]   > [建立設定檔]   > [iOS]  (平台) > [裝置限制]  (設定檔類型) > [Kiosk]  )，您會設定 [自動鎖定]  、[響鈴開關]  、[旋轉螢幕]  、[螢幕睡眠按鈕]  以及 [音量按鈕]  。 

目前，這些設定都是使用 [允許]  (封鎖功能) 或 [未設定]  (允許功能) 設定。 在未來的更新中，這些值會是 [封鎖]  (封鎖功能) 或 [未設定]  (允許功能)。

若要查看目前的設定，請前往 [iOS 裝置設定以允許或限制功能](device-restrictions-ios.md)。 

適用於：iOS

#### <a name="use-face-id-for-password-authentication-on-ios-devices----4490704----"></a>在 iOS 裝置上使用 Face ID 進行密碼驗證 <!-- 4490704  -->
當您建立 iOS 裝置的裝置限制設定檔時，您可以使用指紋作為密碼。 在未來的更新中，指紋密碼設定也會允許臉部辨識 ([裝置設定]   > [設定檔]   > [建立設定檔]   > [iOS]  (平台) > [裝置限制]  (設定檔類型) > [密碼]  )。 因此，會變更下列設定：

- [指紋解除鎖定]  現為 [Touch ID 和 Face ID 解鎖]  。
- [指紋修改 (僅限監督對象)]  現為 [Touch ID 和 Face ID 修改 (僅限受監督)]  。

iOS 11.0 和更新版本可使用 Face ID。 若要查看目前的設定，請前往[使用 Intune 允許或限制功能的 iOS 裝置設定](device-restrictions-ios.md#password)。

適用於：iOS

#### <a name="apps-feature-is-dependent-on-ratings-region-when-restricting-gaming-and-app-store-features-on-ios-devices----4593948----"></a>在 iOS 裝置上限制遊戲和 App Store 功能時，應用程式功能會相依於分級區域 <!-- 4593948  -->
您可以在 iOS 裝置上允許或限制與遊戲、App Store 及檢視文件相關的功能 ([裝置設定]   > [設定檔]   > [建立設定檔]   > [iOS]  (平台) > [裝置限制]  (設定檔類型) > [App Store、文件檢視、遊戲]  )。 您也可以選擇分級區域，例如美國。 在未來的更新中，**應用程式**功能會移到**分級區域**的子系，相依於**分級區域**。

若要查看目前的設定，請前往[使用 Intune 允許或限制功能的 iOS 裝置設定](device-restrictions-ios.md#app-store-doc-viewing-gaming)。

適用於：iOS

#### <a name="administrative-templates-for-group-policy---------3510695---"></a>群組原則的系統管理範本     <!--  3510695 -->
為協助改善雲端裝置的安全性，我們將發行系統管理範本，讓您使用 Intune 設定選取適用於 Windows 電腦的群組原則設定。  這些範本會使用原則設定服務提供者 (CSP)，提供多達 2500 項的 Office、Windows 和 OneDrive 其他設定。

####  <a name="new-settings-for-the-windows-security-baseline-----3534649-4217151------------"></a>新的 Windows 安全性基準設定  <!-- 3534649, 4217151          -->
我們會新增 Windows 安全性基準新設定。 第一項設定為虛擬化型安全性，需要安全開機。 第二項設定可讓您在畫面鎖定時管理 Windows 應用程式的語音啟用。

#### <a name="security-baselines-will-be-generally-available------3785395---------"></a>安全性基準即將上市  <!--  3785395       -->
安全性基準功能即將結束預覽正式推出。 

#### <a name="the-windows-security-baseline-template-will-be-generally-available-------3794072---------"></a>Windows 安全性基準範本即將上市   <!--  3794072       -->
Windows 安全性基準範本即將結束預覽正式推出。 範本的預覽版本將會淘汰，並推出新範本。

<!-- ***********************************************-->
### <a name="device-management"></a>裝置管理

#### <a name="assign-scope-tags-to-all-managed-devices-in-a-security-group----3173810---"></a>將範圍標籤指派給安全性群組中的所有受控裝置 <!-- 3173810 -->
目前，您可前往每部個別裝置的 [屬性]  頁面，選取範圍標籤，將範圍標籤指派給裝置。 在未來的更新中，您可以將範圍標籤指派給安全性群組，而安全性群組中的所有裝置也都會與這些範圍標籤建立關聯。 若要這樣做，請選擇 [Intune]   > [角色]   > [範圍 (標籤)]   > [建立]   > [範圍 (標籤)]  > 選擇您想要指派範圍標籤的群組。 這些群組中的所有裝置也都會獲指派範圍標籤。 使用此功能設定之範圍標籤會覆寫以目前裝置範圍標記流程設定的範圍標籤。 (在未來的更新中，目前將範圍標籤指派給裝置的流程會變成唯讀。)

#### <a name="see-the-security-patch-level-for-android-devices----4461911----"></a>請參閱 Android 裝置的安全性修補程式等級 <!-- 4461911  -->
您可參閱 Android 裝置的安全性修補程式等級。 若要這樣做，請選擇 [Intune]   > [裝置]   > [所有裝置]  > 選擇裝置 > [監視]   > [硬體]  。


<!-- ***********************************************-->
## <a name="notices"></a>通知

[!INCLUDE [Intune notices](./includes/intune-notices.md)]

### <a name="see-also"></a>請參閱
如需近期發展的詳細資料，請參閱 [Microsoft Intune 的新功能](whats-new.md)。



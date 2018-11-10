---
title: 舊版
description: ''
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/31/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: bacaf8ff4119d4cd40483b65ea45e283d98a51f1
ms.sourcegitcommit: 814d1d473de2de2e735efab826b1091de2b093f5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2018
ms.locfileid: "51025197"
---
# <a name="the-early-edition-for-microsoft-intune---november-2018"></a>Microsoft Intune 的舊版 - 2018 年 11 月

> [!Note]
> NDA 通知：下列變更正在 Intune 的開發過程中。 這項資訊會在極有限的基礎下根據 NDA 共用。 請不要在社交媒體或公用網站上張貼任何這項資訊，例如 Twitter、UserVoice、Reddit 等等。 

**舊版**提供 Microsoft Intune 即將發行版本要推出的功能清單 (透過 NDA 共用)。 此資訊以有限的基礎提供，並可能有所變更。 請不要在 UserVoice 上推文、張貼，或在您公司的外部分享這項資訊。 這裡列出的一些功能可能有截止日期，而且可能會延遲到未來的版本。 其他功能正在實驗 (測試) 中進行測試，以確保它們可供客戶使用。 如果您有任何問題或疑慮，請洽詢您的 Microsoft 產品群組連絡人。

此頁面會定期更新。 請回來查看其他更新。

<!--
## What's coming to Intune in the Azure portal  
## What's coming to Intune apps
## Notices
-->
 
## <a name="intune-in-the-azure-portal"></a>Azure 入口網站中的 Intune

<!-- 1811 start -->

### <a name="uninstalling-apps-on-corporate-owned-supervised-ios-devices----1281677---"></a>在公司擁有的受監督 iOS 裝置上解除安裝應用程式 <!-- 1281677 -->
您可以移除公司所擁有受監督 iOS 裝置上的任何應用程式。 您可以透過針對具有**解除安裝**指派類型的使用者或裝置群組，來移除任何應用程式。 針對個人或不受監督的 iOS 裝置，您仍可以僅移除使用 Intune 安裝的應用程式。

### <a name="support-for-ios-12-oauth-in-ios-email-profiles---2155106---"></a>在 iOS 電子郵件設定檔中支援 iOS 12 OAuth <!--2155106 -->
Intune 的 iOS 電子郵件設定檔將支援 iOS 12 OAuth。 若要查看這項功能，請選擇 [Intune] > [裝置設定] > [設定檔] > [建立設定檔]。 在建立設定檔刀鋒視窗中，您可以啟用或停用 [OAuth]。 若開啟此設定，則會發生兩件事：
1. 會向已瞄準的裝置發出新的設定檔。
2. 終端使用者將接收到提示，要求他們再次提供認證。

### <a name="track-installation-of-office-proplus---2620217--"></a>追蹤 Office 專業增強版的安裝 <!--2620217-->
您可以使用[註冊狀態頁面](windows-enrollment-status.md)，來追蹤 [Office 專業增強版](apps-add-office365.md)安裝進度。

### <a name="macos-device-enrollment-program-support-for-apple-school-manager-accounts---3006133--"></a>Apple School Manager 帳戶的 macOS 裝置註冊計劃 <!--3006133-->
Intune 將支持在 Apple School Manager 帳戶的 macOS 裝置上使用裝置註冊計劃。

### <a name="temporarily-pause-kiosk-mode-on-android-devices-to-make-changes----3041935---"></a>暫時暫停 Android 裝置上的 kiosk 模式以進行變更 <!-- 3041935 -->
在多應用程式 kiosk 模式下使用 Android 裝置時，IT 系統管理員可能需要對裝置進行變更。 一種新的多應用程式 kiosk 設定，允許 IT 系統管理員使用 PIN 暫時暫停 kiosk 模式，並可存取整個裝置。
若要查看目前的 kiosk 設定，請參閱 [Android kiosk 設定](android-kiosk-settings.md)。

### <a name="set-custom-background-in-managed-home-screen-app-----3041945---"></a>在受控主畫面應用程式中設定自訂背景 <!-- 3041945 -->
我們將新增一項設定，可讓您在 Android Enterprise、多應用程式、kiosk 模式裝置上自訂受控主畫面應用程式的背景外觀。  若要設定**自訂 URL 背景**，請前往 Azure 入口網站 > [裝置設定] 中的 Intune。 選取目前或建立一個新的裝置組態設定檔，來編輯其 kiosk 設定。

### <a name="enable-virtual-home-button-on-android-enterprise-kiosk-devices-----3042021---"></a>啟用 Android Enterprise kiosk 裝置上的虛擬首頁按鈕 <!-- 3042021 -->
新設定可讓使用者點選其裝置上的螢幕按鍵按鈕，以在其多應用程式 kiok 裝置上的受控主畫面應用程式和其他已指派應用程式之間切換。 在使用者的 kiosk 應用程式未對「返回」按鈕做出適當回應情況下，此設定特別有用。 您將能夠為公司擁有的一次性 Android 裝置設定此設定。 若要啟用或停用**虛擬首頁按鈕**，請前往 Azure 入口網站 > 裝置設定中的 Intune。 選取目前或建立一個新的裝置組態設定檔，來編輯其 kiosk 設定。

### <a name="app-protection-policy-assignment-save-and-apply----3104570---"></a>會儲存並套用應用程式保護原則指派 <!-- 3104570 -->
您將可以更有效控制應用程式保護原則指派。 透過儲存並套用應用程式保護原則指派，只有特定使用者會受到應用程式保護原則指派的直接影響。

### <a name="new-microsoft-edge-browser-settings-for-windows-10-and-later----3174639---"></a>適用於 Windows 10 及更新版本的新 Microsoft Edge 瀏覽器設定 <!-- 3174639 -->
我們將新增一個新設定，以協助您控制和管理裝置上的 Microsoft Edge 瀏覽器。 如需目前設定的清單，請參閱[適用於 Windows 10 (及更新版本) 的裝置限制](device-restrictions-windows-10.md#edge-browser)。

### <a name="select-apps-tracked-on-the-enrollment-status-page---2531007---"></a>選取註冊狀態頁面上追蹤的應用程式<!-- 2531007 -->
您可以在註冊狀態頁面上選擇追蹤哪些應用程式。

### <a name="intune-app-protection-policies-ui-update----3251427---"></a>Intune 應用程式保護原則 UI 更新 <!-- 3251427 -->

Intune 應用程式保護原則可讓您為 Intune 保護的應用程式 (如 Microsoft Outlook 和 Word) 設定各種資料保護設定。 我們正在變更設定和按鈕標籤，以便更容易理解。 控制項將從 [是]/[否] 控制項主要變更為 [封鎖]/[允許] 和 [停用]/[啟用]，同時控制項標籤也會更新，以便清晰顯示。 設定也將重新格式化，以便設定和其標籤在控制項中並排顯示，提供更好的瀏覽。 預設設定和多項設定數量會保持相同，但這項變更可讓使用者更輕鬆了解、巡覽和利用設定以套用所選的應用程式保護原則。



<!-- 1810 start -->

### <a name="use-microsoft-recommended-settings-with-security-baselines----2055484---"></a>使用針對安全性基準 <!-- 2055484 --> 的 Microsoft 建議設定
Intune 會和其他著重安全性的服務整合，包含 Windows Defender ATP 和 Office 365 ATP。 客戶持續不斷要求一種常見策略，以及橫跨 Microsoft 365 服務，極具凝聚力的一組端點對端點安全性工作流程。 我們的目標是調整策略，建置能擔任安全性作業和常見系統管理工作間橋樑的解決方案。 在 Intune 中，我們試圖透過發佈一組 Microsoft 建議的「安全性基準」(**Intune** > **安全性基準**)，來達到此目標。  系統管理員將能夠直接從這些基準建立安全性政策，並將它們部署到其使用者。 他們也可以自訂最佳做法建議項目，以符合其組織的需求。 Intune 會確保裝置符合這些基準的規範，並會通知系統管理員不合規的使用者或裝置。

### <a name="scope-tags-for-apps---1081941---"></a>應用程式的範圍標籤 <!--1081941 -->
您可以建立範圍標籤來限制對 Intune 資源的存取。 將範圍標籤新增至角色指派，然後將範圍標籤新增至設定檔。 此角色只能存取設定檔具有相符範圍標籤 (或無範圍標籤) 的資源。
若要建立範圍標籤，請選擇 [Intune roles] \(Intune 角色\) > [Scope (Tags)] \(範圍 (標籤)\) > [建立]。
若要將範圍標籤新增至角色指派，請選擇 [Intune roles] \(Intune 角色\) > [All roles] \(所有角色\) > [Policy and Profile Manager] \(原則和設定檔管理員\) > [作業] > [Scope (Tags)] \(範圍 (標籤)\)。
若要將範圍標籤新增至設定檔，請選擇 [裝置設定] > [設定檔] > 選擇設定檔 > [屬性] > [Scope (Tags)] \(範圍 (標籤)\)。

### <a name="tenant-health-dashboard----1124854---"></a>租用戶健康狀態儀表板 <!-- 1124854 -->
Intune 中的 [租用戶健康狀態] 頁面可在單一位置提供您租用戶的狀態資訊。 頁面分為 4 個區段：  
- **租用戶詳細資料**：包含資訊，例如您的 MDM 授權單位、您租用戶中的總註冊裝置數，以及您的授權計數。 此區段也會提供您租用戶目前的服務版本。
- **連接器狀態**：包含設定連接器的資訊，例如 Apple VPP、商務用 Microsoft Store，以及憑證連接器。 根據其目前狀態，連接器會標記為 [良好]、[警告]，或 [不良]。
- **Intune 服務健康狀態**：包含您租用戶正在發生的事件或中斷。 此區段中的資訊是直接從 Office 訊息中心 ([https://portal.office.com](https://portal.office.com)) 擷取的。
- **Intune 新聞**：包含您租用戶使用中的訊息，其中可能會包含像是您的租用戶已接收到最新的 Intune 功能等通知。 此區段中的資訊是直接從 Office 訊息中心 ([https://portal.office.com](https://portal.office.com)) 擷取的。


### <a name="deployed-wip-policies-without-user-enrollment----1434452---"></a>無使用者註冊的部署 WIP 原則 <!-- 1434452 -->
Windows 資訊保護 (WIP) 原則將能在無須 MDM 使用者註冊其 Windows 10 裝置的情況下部署。 此設定允許公司根據 WIP 設定保護其公司文件，同時允許使用者維持其自身 Windows 裝置的管理。 一旦使用 WIP 原則保護文件，Intune 系統管理員便可以選擇性抹除受保護的資料。 透過選取使用者和裝置，並傳送抹除要求，所有透過 WIP 原則保護的資料都會無法使用。 從 Azure 入口網站中的 Intune，選取 [行動應用程式] > [應用程式選擇性抹除]。


<!-- 1809 start -->  

### <a name="app-protection-policy-app-settings-for-web-data----2662995---"></a>適用於 Web 資料的應用程式防護原則 (APP) 設定 <!-- 2662995 -->
Android 及 iOS 裝置上適用於 Web 內容的應用程式原則設定會進行更新，提升處理 HTTP 和 HTTPS Web 連結的能力，以及透過 iOS 通用連結和 Android 應用程式連結進行資料轉送的能力。  

<!-- 1808 start -->

### <a name="apple-vpp-token-used-by-another-mdm----1488946---"></a>另一個 MDM 所使用的 Apple VPP 權杖 <!-- 1488946 -->
如果 Intune 和另一個 MDM 都正在使用 Apple 大量採購方案 (VPP) 權杖，則 Intune 會偵測並顯示詳細資料。

### <a name="ios-and-macos-version-numbers-and-build-numbers-are-shown----1892471---"></a>顯示 iOS 和 macOS 版本號碼和組建編號 <!-- 1892471 -->
在 [裝置合規性] > [裝置合規性] 中，會顯示 iOS 和 macOS 作業系統版本。 在未來的更新中，也會顯示這兩個平台的組建編號。

發行安全性更新時，Apple 通常會保留版本號碼，但更新組建編號。 顯示組建編號，即可輕鬆地檢查是否已安裝弱點更新。

### <a name="retired-devices-in-the-device-compliance-dashboard----1981119---"></a>[裝置合規性] 儀表板中的已淘汰裝置 <!-- 1981119 -->
在未來的更新中，將會從 [裝置合規性] 儀表板中移除已淘汰裝置。 這會變更您的合規性數字。


### <a name="change-in-the-update-process-for-on-premises-connectors----2277554---"></a>內部部署連接器之更新程序中的變更 <!-- 2277554 -->
根據客戶的意見反應，將會變更內部部署連接器更新方式。 在您初次安裝內部部署連接器之後，將會自動更新。 這項變更會從新的適用於 Microsoft Intune 的 PFX 憑證連接器開始，之後將推出至其他類型的內部部署連接器。 

<!-- 1807 start -->

### <a name="check-for-configuration-manager-compliance----2192052---"></a>檢查 Configuration Manager 合規性 <!-- 2192052 -->
未來更新將會包括新的 System Center Configuration Manager 合規性設定 ([裝置相容性] > [原則] > [建立原則] > [Windows 10])。 Configuration Manager 會將訊號傳送至 Intune 合規性。 您可以使用 Intune 設定來要求所有傳回的 Configuration Manager 訊號都需是「符合規範」。

例如，您需要在裝置上安裝所有軟體更新。 在 Configuration Manager 中，此要求將會對應「已安裝」狀態。 如果裝置上的任何程式處於未知狀態，則裝置在 Intune 中將會不相容。

適用於 Windows 10 和更新版本

### <a name="alerts-for-expiring-vpp-token-or-company-portal-license-running-low----2237572---"></a>VPP 權杖將過期或公司入口網站授權將不足的警示<!-- 2237572 -->
如果您在 DEP 註冊期間使用大量採購方案 (VPP) 預先佈建公司入口網站，則 Intune 會在 VPP 權杖即將過期以及公司入口網站授權即將不足時提醒您。



<!-- the following are present prior to 1711 -->

## <a name="notices"></a>通知

目前沒有任何作用中的通知。

### <a name="see-also"></a>另請參閱
如需近期發展的詳細資料，請參閱 [Microsoft Intune 的新功能](whats-new.md)。




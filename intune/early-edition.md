---
title: 舊版
description: ''
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/03/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: b6ca8108924c6c062da0d0ef56ab5b68635dd9ca
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="the-early-edition-for-microsoft-intune---april-2018"></a>Microsoft Intune 的舊版 - 2018 年 4 月

**舊版**提供 Microsoft Intune 即將發行版本要推出的功能清單。 此資訊以有限的基礎提供，並可能有所變更。 請不要在貴公司以外的地方分享此資訊。 這裡列出的一些功能可能有截止日期，而且可能會延遲到未來的版本。 其他功能正在實驗 (測試) 中進行測試，以確保它們可供客戶使用。 如果您有任何問題或疑慮，請洽詢您的 Microsoft 產品群組連絡人。

此頁面會定期更新。 請回來查看其他更新。

> [!Note]
>下列變更正在 Intune 的開發過程中。 如需新混合式功能的詳細資訊，請參閱[混合式新功能頁面](/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management)。

<!--
## What's coming to Intune in the Azure portal  
## What's coming to Intune apps
## Notices
-->
 
## <a name="intune-in-the-azure-portal"></a>Azure 入口網站中的 Intune

<!-- 1804 start -->

### <a name="new-windows-defender-credential-guard-settings-added-to-endpoint-protection-settings---1102252-----from-1802--"></a>在 Endpoint Protection 設定中新增新的 Windows Defender Credential Guard 設定 <!--1102252 --><!--from 1802-->

新的 [Windows Defender Credential Guard](https://docs.microsoft.com/windows/access-protection/credential-guard/credential-guard) 設定將會新增至 [裝置設定] > [設定檔] > [Endpoint Protection]。 會新增下列設定：

- 平台安全性層級：指定下次重新開機時是否啟用平台安全性層級。 虛擬化型安全性需要安全開機。 使用直接記憶體存取 (DMA) 保護，可以選擇性啟用虛擬化型安全性。 DMA 保護需要硬體支援，而且只能在正確設定的裝置上啟用。
- 虛擬化型安全性：指定下次重新開機時是否啟用虛擬化型安全性。
- Windows Defender Credential Guard：以虛擬化型安全性開啟 Credential Guard，以在下次重新開機時，於安全開機平台安全性層級和虛擬化型安全性同時啟用的狀況下，協助保護認證。 可用的選項包括 [停用]、[在包含 UEFI 鎖定的情況下啟用]、[在不含鎖定情況下啟用] 和 [未設定]。
  - 如果先前是以 [在不含鎖定情況下啟用] 選項開啟 Credential Guard，[停用] 選項就會從遠端關閉它。

  - [在包含 UEFI 鎖定的情況下啟用] 選項可確保無法以登錄機碼或使用群組原則停用 Credential Guard。 若要在使用這項設定之後停用 Credential Guard，您必須將群組原則設成 [停用]，並且移除每部電腦的安全性功能與實際存在的使用者，才能清除保存在 UEFI 中的設定。 只要 UEFI 設定持續存在，就會一直啟用 Credential Guard。

  - [在不含鎖定情況下啟用] 選項可使用群組原則從遠端停用 Credential Guard。 使用此設定的裝置至少必須執行 Windows 10 (1511 版)。

  - [未設定] 選項會保持原則設定的未定義狀態。 群組原則不會將原則設定寫入登錄，所以不會影響到電腦或使用者。 如果目前在登錄中有設定，它不會被修改。

### <a name="passcode-support-for-mam-pin-on-android---1438086---"></a>在 Android 上針對 MAM PIN 提供密碼支援<!-- 1438086 -->

Intune 系統管理員將能夠設定應用程式啟動需求來強制使用密碼，而不使用數字 MAM PIN。 如上進行設定後，使用者就必須在出現提示時設定並使用密碼，才能存取啟用 MAM 的應用程式。 密碼的定義為數字 PIN 和至少一個特殊字元或大寫/小寫字母。 Intune 支援密碼的方式與數字 PIN 類似，能夠透過管理主控台設定長度下限、允許重複的字元及順序。 若要使用此功能，Android 上必須要有最新版的公司入口網站。 此功能已經可供 iOS 使用。

###  <a name="block-camera-and-screen-captures-on-android-for-work----1098977-eeready--"></a>在 Android for Work 上封鎖相機和螢幕擷取 <!-- 1098977 eeready-->
當您為 Android 裝置設定裝置限制時，將會有兩個可用來進行封鎖的新屬性： 
- 相機：封鎖對裝置上所有相機的存取
- 螢幕擷取：封鎖螢幕擷取，同時也防止在沒有安全視訊輸出的顯示裝置上顯示內容

適用於 Android for Work。

### <a name="line-of-business-lob-app-support-for-macos----1473977---"></a>macOS 的企業營運 (LOB) 應用程式支援 <!-- 1473977 -->
Microsoft Intune 將可讓您從 Azure 入口網站安裝 macOS LOB 應用程式。 您將能夠在以 GitHub 中提供的工具對 macOS LOB 應用程式進行前處理之後，將其新增至 Intune。 在 Azure 入口網站中，從 [Intune] 刀鋒視窗上選擇 [行動應用程式]。 在 [行動應用程式] 刀鋒視窗上，選擇 [應用程式] > [新增]。 在 [新增應用程式] 刀鋒視窗上，選取 [企業營運應用程式]。 

### <a name="support-for-user-less-devices----1637553---"></a>支援無使用者裝置 <!-- 1637553 -->
Intune 將支援評估無使用者裝置 (例如 Microsoft Surface Hub) 上合規性的功能。 合規性原則可以針對特定裝置。 因此，可以針對沒有相關使用者的裝置判斷是否符合規範 (和不符合規範)。

### <a name="additions-to-local-device-security-options-settings----1403702---"></a>新增本機裝置安全性選項設定 <!-- 1403702 -->
您將能夠為 Windows 10 裝置設定額外的 [本機裝置安全性選項] 設定。 可供使用額外設定的領域包括 Microsoft Network Client、Microsoft Network Server、[網路存取和安全性] 及 [互動式登入]。 當您建立 Windows 10 裝置設定原則時，在 [Endpoint Protection] 類別中找到這些設定。

### <a name="require-installation-of-policies-apps-certificate-and-network-profiles----1553555---"></a>要求安裝原則、應用程式、憑證及網路設定檔 <!-- 1553555 -->
在佈建 AutoPilot 裝置期間，系統管理員將能夠禁止使用者存取 Windows 10 RS4 桌面，直到 Intune 安裝原則、應用程式及憑證和網路設定檔為止。

### <a name="rules-for-removing-devices----1609459---"></a>用於移除裝置的規則 <!-- 1609459 -->
將會提供新規則，可讓您自動移除在所設定天數內未簽入的裝置。 若要查看新規則，請移至 [Intune] 窗格，選取 [裝置]，然後選取 [裝置移除規則]。

### <a name="prevent-consumer-apps-and-experiences-on-windows-10-enterprise-rs4-autopilot-devices---1621980---"></a>防止 Windows 10 企業版 RS4 AutoPilot 裝置上的消費者應用程式和體驗<!-- 1621980 -->
您將能夠防止在「Windows 10 企業版 RS4 AutoPilot」裝置上安裝消費者應用程式和體驗。 若要查看此功能，請移至 [Intune] > [裝置註冊] > [Windows 註冊] > [Windows AutoPilot 設定檔] > [新建] > [註冊設定]。 

### <a name="advanced-threat-protection-integrated-with-intune----1629303---"></a>進階威脅防護與 Intune 整合 <!-- 1629303 -->
[進階威脅防護 (ATP)](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/dashboard-windows-defender-advanced-threat-protection) 會顯示 Windows 10 裝置的風險層級。 當 Intune 評估 Windows 10 裝置是否符合規範時，此評估中會包括 ATP 風險分數。 您可以使用 ATP 搭配條件式存取來協助保護您的網路。

### <a name="new-enrollment-steps-for-users-on-devices-with-macos-high-sierra-10132---1734567---"></a>適用於具有 macOS High Sierra 10.13.2+ 之裝置上使用者的新註冊步驟 <!--1734567 -->
macOS High Sierra 10.13.2 引進了「使用者核准的」MDM 註冊概念。 在未來，已核准的註冊將可讓 Intune 管理一些安全性敏感設定。 如需詳細資訊，請參閱以下的 Apple 支援文件：https://support.apple.com/HT208019。

使用 macOS 公司入口網站來註冊的裝置將被視為「未經使用者核准」，除非使用者開啟 [系統偏好設定] 並手動提供核准。 為此，macOS 公司入口網站現在會在註冊程序結尾，將 macOS 10.13.2 和更新版本的使用者導向以供他們手動核准其註冊。 Intune 管理主控台將會針對已註冊裝置是否獲得使用者核准進行回報。

### <a name="delete-autopilot-devices----1713650---"></a>刪除 AutoPilot 裝置 <!-- 1713650 -->
Intune 系統管理員將能夠刪除 AutoPilot 裝置。

### <a name="built-in-all-users-and-all-devices-group-for-android-for-work-afw-app-assignment----1813073---"></a>適用於 Android for Work (AFW) 應用程式指派的內建所有使用者和所有裝置群組 <!-- 1813073 -->
您將能夠利用內建的 [所有使用者] 和 [所有裝置] 群組來進行 AFW 應用程式指派。 如需詳細資訊，請參閱 [Microsoft Intune 的包含與排除應用程式指派](apps-inc-exl-assignments.md)。

### <a name="improved-device-deletion-experience---1832333---"></a>改進的裝置刪除體驗 <!--1832333 -->
在從 Intune 刪除裝置之前，您將不再需要移除公司資料或重設成出廠預設值。

若要查看新體驗，請登入 Intune，然後選取 [裝置] > [所有裝置] > 裝置的名稱 > [刪除]。

 如果您仍然想要確認抹除/淘汰，可以使用標準裝置生命週期途徑，方法是先發出 [移除公司資料] 和 [重設成出廠預設值]，再進行 [刪除]。 

### <a name="autopilot-profiles-moving-to-group-targeting----1877935---"></a>將 AutoPilot 設定檔移至群組目標設定 <!-- 1877935 -->
目前，可將 AutoPilot 部署設定檔指派給選取的裝置。 以下是到四月底時，您將指派這些設定檔的方式：
- 建立包含 AutoPilot 裝置的 (Azure AD) 群組
- 將所需的設定檔指派給 Azure AD 群組。 現在將會把 AutoPilot 設定檔指派給該群組中的 AutoPilot 裝置。

### <a name="play-sounds-on-ios-when-in-lost-mode----1629303---"></a>在處於遺失模式時於 iOS 上播放音效 <!-- 1629303 -->
當受監督的 iOS 裝置處於「行動裝置管理」(MDM) [遺失模式](device-lost-mode.md)時，您可以播放音效 ([裝置] > [所有裝置] > 選取 iOS 裝置 > [概觀] > [更多])。 此音效會持續播放，直該裝置已自遺失模式中移除，或使用者將該裝置上的音效停用為止。 適用於 iOS 裝置 9.3 和更新版本。

### <a name="use-a-custom-subject-name-on-scep-certificate----2064190---"></a>在 SCEP 憑證上使用自訂主體名稱 <!-- 2064190 -->
您將能夠在 SCEP 憑證設定檔上的自訂主體中，使用 **OnPremisesSamAccountName** 一般名稱。 例如，您可以使用 `CN={OnPremisesSamAccountName})`。

### <a name="send-diagnostic-reports-in-company-portal-app-for-macos----2216677---"></a>在 macOS 版公司入口網站應用程式中傳送診斷報告 <!-- 2216677 -->
將會更新 macOS 版公司入口網站應用程式裝置，以改進使用者回報 Intune 相關錯誤的方式。 從公司入口網站應用程式中，您的員工將能夠：
- 將診斷報告直接上傳至 Microsoft 開發人員小組。
- 透過電子郵件將事件識別碼傳送給 IT 支援小組。

### <a name="always-on-vpn-for-windows-10---1333666---"></a>適用於 Windows 10 的一律開啟 VPN<!--1333666 -->

目前，可藉由使用以 OMA-URI 建立的自訂虛擬私人網路 (VPN) 設定檔，在 Windows 10 裝置上使用[一律開啟](https://docs.microsoft.com/windows/security/identity-protection/vpn/vpn-auto-trigger-profile#always-on)。

在此更新中，系統管理員將能夠直接在 Azure 入口網站的 Intune 中，為 Windows 10 VPN 設定檔啟用「一律開啟」。 「一律開啟」VPN 設定檔會在下列情況下自動連線：

- 使用者登入其裝置
- 裝置上的網路發生變更
- 裝置上的螢幕在關閉後恢復開啟

### <a name="improved-error-messaging-for-apple-mdm-push-certificate-upload-failure----2172331---"></a>改進 Apple MDM Push Certificate 上傳失敗的錯誤訊息傳遞 <!-- 2172331 -->

錯誤訊息將會說明更新現有的 MDM 憑證時，必須使用相同的 Apple ID。

###  <a name="device-profile-chart-and-status-list-show-all-devices-in-a-group----1449153-eeready---"></a>裝置設定檔圖表和狀態清單顯示群組中的所有裝置 <!-- 1449153 eeready -->
當您設定裝置設定檔 ([裝置設定] > [設定檔]) 時，可以選擇裝置設定檔，例如 iOS。 您會將這個設定檔指派給包含 iOS 裝置和非 iOS 裝置的群組。 圖形化圖表計數會顯示設定檔已套用至 iOS「和」非 iOS 裝置 ([裝置設定] > [設定檔] > 選取現有的設定檔 > [概觀])。 當您在 [概觀] 索引標籤中選取圖形化圖表時，[裝置狀態] 會列出群組中的所有裝置，而不是只列出 iOS 裝置。 

在此更新中，圖形化圖表 ([裝置設定] > [設定檔] > 選取現有的設定檔 > [概觀]) 將只會顯示特定裝置設定檔的計數。 例如，如果設定裝置設定檔適用於 iOS 裝置，圖表只會列出 iOS 裝置的計數。 選取圖形化圖表和開啟 [裝置狀態] 只會列出 iOS 裝置。

進行此更新時，會暫時移除圖形化使用者圖表。 


<!-- 1803 start -->

#### <a name="multiple-exchange-connector-support----2070451---"></a>多重 Exchange 連接器支援 <!-- 2070451 -->

您不會再受到每個租用戶只能有一個 Microsoft Intune Exchange 連接器的限制了。 Intune 將會支援多個 Exchange 連接器，使您可以用多個內部部署 Exchange 組織來設定 Intune 條件式存取。

透過 Intune 內部部署 Exchange 連接器，您可以根據裝置是否已在 Intune 註冊且符合 Intune 裝置合規性政策，來管理裝置對於您內部部署 Exchange 信箱的存取。 若要設定連接器，請從 Azure 入口網站下載 Intune 內部部署 Exchange 連接器，並安裝在您 Exchange 組織中的伺服器。 在 Microsoft Intune 儀表板中，選擇 [內部部署存取]，然後在 [安裝] 下選擇 [Exchange ActiveSync 連接器]。 下載 Exchange 內部部署連接器，並將其安裝在您 Exchange 組織中的伺服器。 您現在已經沒有一個租用戶只能有一個 Exchange 連接器的限制，因此您如果有其他 Exchange 組織，亦可遵循此相同流程為每個 Exchange 組織下載並安裝連接器。

### <a name="support-coming-for-new-cisco-anyconnect-client-for-ios----1333708---"></a>適用於 iOS 之新 Cisco AnyConnect 用戶端的支援即將推出 <!-- 1333708 -->

為 iOS 的 Cisco AnyConnect 所建立的新 VPN 設定檔，將可與 Cisco AnyConnect 4.0.7x 或更新版本搭配運作。 現有的 iOS Cisco AnyConnect VPN 設定檔將會標記為 **Cisco Legacy AnyConnect**，但能夠繼續以目前的方式搭配 Cisco AnyConnect 4.0.5x 運作。

> [!NOTE]
> 這項變更僅適用於 iOS，而 Android、Android for Work 及 macOS 仍然只有一個 Cisco AnyConnect 選項。

#### <a name="more-information"></a>詳細資訊

您需要建立新的 iOS Cisco AnyConnect VPN 設定檔以支援新的應用程式，因為新的 Cisco AnyConnect 應用程式和 Cisco Legacy AnyConnect 應用程式是獨立的應用程式。 如果在您的環境中管理 AnyConnect 用戶端，您也需要部署新的 Cisco AnyConnect 應用程式。 若要完成升級，您也需要刪除您的 Cisco Legacy AnyConnect VPN 設定檔，並移除 Cisco Legacy AnyConnect 應用程式。

網路存取控制 (NAC) 整合在初始版本中將無法於新的 AnyConnect 用戶端運作。 我們正與 Cisco 合作，以在 Intune 未來版本中提供 NAC 整合。

### <a name="ability-to-deploy-required-line-of-business-lob-apps-to-all-users-on-windows-10-desktop-devices----1627835-rs4---"></a>在 Windows 10 Desktop 裝置上，將所需之企業營運 (LOB) 應用程式部署給所有使用者的能力 <!-- 1627835 RS4 -->
客戶將能夠部署必要的企業營運 Windows 10 應用程式，以安裝在裝置內容中。 這會向裝置上的所有使用者開放使用這些應用程式。 這僅適用於 Windows 10 Desktop 裝置。

### <a name="company-portal-enrollment-improved----1874230--"></a>改善的公司入口網站註冊 <!-- 1874230-->
在 Windows 10 1703 組建或更新版本上使用公司入口網站來註冊裝置的使用者，將能夠完成註冊的第一個步驟，且不需離開應用程式。

### <a name="updating-the-help-and-feedback-experience-on-company-portal-app-for-android---1631531---"></a>更新 Android 的公司入口網站應用程式之說明與意見反應體驗 <!--1631531 -->

我們將更新 Android 公司入口應用程式的說明和意見反應體驗，以與 Android 應用程式的最佳做法保持一致。 我們將於接下來幾個月內更新 Android 公司入口網站應用程式，以將 **說明與意見反應** 功能表項目劃分為分開的**說明**與**傳送意見反應**功能表項目。 **說明**頁面將有**常見問題集**章節和**電子郵件支援** 按鈕，引導使用者上傳記錄給 Microsoft，並將電子郵件傳送給描述問題的公司支援。 **傳送意見反應**會透過標準 Microsoft 意見反應提交來引導使用者，並會提示使用者選擇「我喜歡某些項目」、「我不喜歡某些項目 」，或是「我有個想法」。

<!-- 1802 start -->

### <a name="new-printer-settings-for-education-profiles----1308900---"></a>教育版設定檔的新印表機設定 <!-- 1308900 -->

若為教育版設定檔，新的設定會位在 [印表機] 類別下：[印表機]、[預設印表機]、[Add new printers] (新增印表機)。

<!-- the following are present prior to 1801 -->

### <a name="app-protection-policies-----679615---"></a>應用程式防護原則 <!-- 679615 -->
Intune 應用程式防護原則能提供建立全域預設原則的能力，以針對整個租用戶中的所有使用者快速啟用保護。

<!-- the following are present prior to 1711 -->

### <a name="azure-active-directory-web-sites-can-require-the-intune-managed-browser-app-and-support-single-sign-on-for-the-managed-browser-public-preview----710595---"></a>Azure Active Directory 網站可以要求使用 Intune Managed Browser 應用程式，並支援 Managed Browser (公開預覽) 的單一登入 <!-- 710595 -->   
使用 Azure Active Directory (Azure AD) 時，您能夠限制行動裝置使用 Intune Managed Browser 應用程式存取網站。 在 Managed Browser 中，網站資料的安全受到保護，並會與使用者的個人資料區隔開來。 此外，針對受 Azure AD 保護的網站，Managed Browser 也支援單一登入功能。 當使用者登入 Managed Browser，或在裝置上搭配使用 Managed Browser 與受 Intune 管理的其他應用程式時，即可在不需輸入認證的情況下，讓 Managed Browser 存取受 Azure AD 保護的公司網站。 這項功能適用於 Outlook Web Access (OWA) 和 SharePoint Online 等網站，以及透過 Azure App Proxy 存取的內部網路資源等其他公司網站。




## <a name="notices"></a>通知

目前沒有任何作用中的通知。


### <a name="see-also"></a>另請參閱
如需近期發展的詳細資料，請參閱 [Microsoft Intune 的新功能](whats-new.md)。



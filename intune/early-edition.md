---
title: 舊版
description: ''
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/15/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 62028232e4d6c9ab20a05480811978234ed0a3c1
ms.sourcegitcommit: 91802e78cd5014d20a828ca25a54a381d452f0f8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/16/2018
---
# <a name="the-early-edition-for-microsoft-intune---may-2018"></a>Microsoft Intune 的初期版本 - 2018 年 5 月

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

<!-- 1805 start -->

### <a name="support-for-palo-alto-networks-globalprotect-vpn-profiles----1333680-eeready----"></a>Palo Alto Networks GLOBalProtect VPN 設定檔的支援 <!-- 1333680 eeready ! -->

透過這項更新，您可以選擇 Palo Alto Networks GLOBalProtect 作為在 Intune 中 VPN 設定檔的 VPN 連線類型 ([裝置設定] > [設定檔] > [建立設定檔] > [設定檔類型] > [VPN])。 在此版本中，支援下列平台： 

- iOS
- Windows 10

### <a name="set-compliance-by-device-location----851881----"></a>依裝置位置設定合規性 <!-- 851881 ! -->
在某些情況下，您可能會想要依網路連線將公司資源的存取限制於特定的位置。 您於未來將能依據裝置的 IP 位址建立合規性原則 ([裝置合規性] > [位置])。 如果裝置移出該 IP 範圍，則該裝置將會無法存取公司資源。

適用對象：公司入口網站應用程式已更新的 6.0 和更新版本的 Android 裝置

### <a name="improved-troubleshooting-for-app-installation----928990---"></a>改善的應用程式安裝疑難排解 <!-- 928990 -->
在受 Microsoft Intune MDM 管理的裝置上，應用程式安裝有時可能會失敗。 當這些應用程式安裝失敗時，使用者可能無法輕易地了解失敗的原因，或是對問題進行疑難排解。 我們正在推出應用程式疑難排解功能的公開預覽。 您將會在每個個別裝置的底下看到名為 [受控應用程式] 的新節點。 這會列出透過 Intune MDM 傳遞的應用程式。 在該節點中，您將會看到應用程式安裝狀態的清單。 如果您選取個別的應用程式，將會看到針對該特定應用程式的疑難排解檢視。 在疑難排解檢視中，您將會看到應用程式的端對端生命週期，例如針對該應用程式進行建立、修改、設為目標，以及傳遞至裝置的時間。 此外，如果應用程式安裝沒有成功，系統將會針對導致該錯誤的原因為您顯示錯誤碼及協助訊息。 

### <a name="block-app-access-based-on-unapproved-device-vendors-and-models-----1425689----"></a>依據未經核准的裝置廠商和型號來封鎖應用程式存取 <!-- 1425689 ! -->
Intune IT 系統管理員將能透過 Intune 應用程式防護原則，強制執行 Android 製造商和/或 iOS 型號的指定清單。 IT 系統管理員可以提供以分號分隔的製造商清單 (適用於 Android 原則) 及裝置型號清單 (適用於 iOS 原則)。 Intune 應用程式防護原則僅適用於 Android 和 iOS。 針對此指定清單，將可以執行兩個個別的動作：
- 針對未指定的裝置，封鎖其存取應用程式的能力。
- 或是針對未指定的裝置，選擇性地抹除該裝置上的公司資料。 

若沒有符合原則需求，使用者將無法存取目標應用程式。 根據設定的不同，系統可能會封鎖該使用者，或選擇性地抹除其位於應用程式內的公司資料。 在 iOS 裝置上，此功能需要應用程式的參與 (亦即， WXP、Outlook、Managed Browser、Yammer) 來整合 Intune APP SDK，以針對目標應用程式強制執行最小版本設定。 此整合會以輪流的方式發生，並取決於特定的應用程式小組。 在 Android 上，此功能需要有最新版的公司入口網站。

在使用者裝置上，Intune 用戶端將會根據應用程式防護原則 Intune 刀鋒視窗中所指定字串來進行簡單比對，藉以採取動作。 這會完全取決於裝置報告的值。 因此，我們會建議 IT 系統管理員確定預期的行為是正確無誤的。 這可透過針對小型的使用者群組，在各種不同的裝置製造商和型號上測試此設定來達成。 在 Microsoft Intune 中，選取 [行動應用程式] > [應用程式防護原則] 來檢視及新增應用程式防護原則。 如需應用程式防護原則的詳細資訊，請參閱[什麼是應用程式防護原則](app-protection-policy.md)。

### <a name="enable-kiosk-mode-on-windows-10-devices----1560072----"></a>在 Windows 10 裝置上啟用 Kiosk 模式 <!-- 1560072 ! -->
在 Windows 10 裝置上，您可以建立組態設定檔並啟用 Kiosk 模式 ([裝置設定] > [設定檔] > [建立設定檔] > [Windows 10] > [裝置限制] > [Kiosk])。 在此更新中，[Kiosk (預覽)] 設定已重新命名為 [Kiosk (已淘汰)]。 我們不建議繼續使用 [Kiosk (已淘汰)]，但該功能在 7 月更新之前將會持續運作。 [Kiosk (已淘汰)] 已由新的 [Kiosk] 設定檔類型 ([建立設定檔] > [Windows 10] > [Kiosk (預覽)]) 取代，此設定檔類型將會包含在 Windows 10 RS4 及更新版本上設定 Kiosk 的設定。

適用於 Windows 10 及更新版本。

### <a name="retrieve-the-associated-app-user-model-id-aumid-for-microsoft-store-for-business-apps-in-kiosk-mode----1560077----"></a>在 Kiosk 模式中擷取商務用 Microsoft Store 應用程式的相關聯應用程式使用者模型識別碼 (AUMID) <!-- 1560077 ! -->
Intune 將能夠擷取商務用 Microsoft Store (WSfB) 應用程式的應用程式使用者模型識別碼 (AUMID)，以提供改善的 Kiosk 設定檔設定。

如需商務用 Microsoft Store 應用程式的詳細資訊，請參閱[管理來自商務用 Microsoft Store 的應用程式](windows-store-for-business.md)。

### <a name="access-actions-for-app-protection-policies----1483510-eeready---"></a>存取適用於應用程式防護原則的動作 <!-- 1483510 EEready -->
您很快便能設定應用程式防護原則，以明確地針對不符合規範的裝置進行抹除、封鎖或警告。 最新的動作「抹除」能從裝置移除您公司的資料。 如果發生抹除，系統會向裝置使用者告知抹除的原因及補救的步驟。 針對某些設定 (例如最小 OS 版本)，您將能套用多個動作 (例如封鎖和抹除)。

### <a name="new-inventory-information-for-windows-devices----1333569-eeready---"></a>適用於 Windows 裝置的新清查資訊 <!-- 1333569 eeready -->

針對 Windows 裝置，下列清查資訊將會針對個別裝置於 [硬體] 索引標籤中提供 ([群組] > [所有行動裝置] > [裝置] > 選擇使用者的裝置 > [檢視內容] > [硬體])：
- TPM
- 防毒
- 反間諜功能
- 防火牆
- UAC
- 電池
- 網域名稱

如需 CSP 如何擷取此資料的詳細資訊，請參閱 [DeviceStatus CSP](https://docs.microsoft.com/en-us/windows/client-management/mdm/devicestatus-csp) \(英文\) 一文中的 DeviceGuard 相關內容。

### <a name="intune-and-the-microsoft-edge-browser----1818969---"></a>Intune 和 Microsoft Edge 瀏覽器 <!-- 1818969 -->
適用於行動裝置 (iOS 和 Android) 的 Microsoft Edge 瀏覽器現已支援 Intune 應用程式防護原則。 使用其公司 Azure AD 帳戶登入 Edge 瀏覽器應用程式的使用者，將會受到 Intune 的保護。 

### <a name="new-languageregion-setting-when-configuring-oobe-for-autopilot----1821766---"></a>針對 Autopilot 設定 OOBE 時的新語言/地區設定 <!-- 1821766 -->
在全新體驗期間，將會有新設定可供設定 Autopilot 設定檔的語言和地區。

### <a name="new-setting-for-configuring-device-keyboard----1821768---"></a>適用於設定裝置鍵盤的新設定 <!-- 1821768 -->
在全新體驗期間，將會有新設定可供設定 Autopilot 設定檔的鍵盤。

### <a name="use-teamviewer-to-screen-share-ios-and-macos-devices----1985547---"></a>使用 TeamViewer 來共用 iOS 和 MacOS 裝置的螢幕畫面 <!-- 1985547 -->
目前，您可以使用 TeamViewer 來遠端管理[受 Intune 管理的 Android 和 Windows 裝置](device-profile-android-teamviewer.md)。

系統管理員於未來將可以連線至 TeamViewer，並與 iOS 和 macOS 裝置建立螢幕畫面共用工作階段。 iPhone、iPad 及 macOS 使用者都可以與任何其他電腦或行動裝置即時共用其螢幕畫面。 

### <a name="device-profile-graphical-user-chart-is-back----2160133---"></a>已重新推出裝置設定檔圖形化使用者圖表 <!-- 2160133 -->
在改善裝置設定檔圖形化圖表 ([裝置設定] > [設定檔] > 選取現有的設定檔 > [概觀]) 上所顯示的數值計數之際，暫時移除了圖形化使用者圖表。

此更新已重新推出圖形化使用者圖表，如 Azure 入口網站中所示。

### <a name="assign-all-users-and-all-devices-as-scope-groups----2196803---"></a>將所有使用者和所有裝置指派為範圍群組 <!-- 2196803 -->
您將能以範圍群組的形式指派所有使用者、所有裝置，以及所有使用者和所有裝置。

### <a name="autopilot-profiles-moving-to-group-targeting----1877935---"></a>將 AutoPilot 設定檔移至群組目標設定 <!-- 1877935 -->
目前，可將 AutoPilot 部署設定檔指派給選取的裝置。 在推出此功能之後，指派這些設定檔的方法如下：
- 建立包含 AutoPilot 裝置的 (Azure AD) 群組
- 將所需的設定檔指派給 Azure AD 群組。 現在將會把 AutoPilot 設定檔指派給該群組中的 AutoPilot 裝置。

### <a name="management-name-field-will-be-editable----1875989---"></a>管理名稱欄位將可以編輯 <!-- 1875989 -->
您將能在裝置的 [屬性] 刀鋒視窗上編輯管理名稱欄位。 如果要編輯此欄位，請選擇 [裝置] > [所有裝置] > 選擇裝置 > [屬性]。 您可以使用管理名稱欄位來唯一識別裝置。

<!-- 1804 start -->


### <a name="additions-to-local-device-security-options-settings----1403702---"></a>新增本機裝置安全性選項設定 <!-- 1403702 -->
您將能夠為 Windows 10 裝置設定額外的 [本機裝置安全性選項] 設定。 可供使用額外設定的領域包括 Microsoft Network Client、Microsoft Network Server、[網路存取和安全性] 及 [互動式登入]。 當您建立 Windows 10 裝置設定原則時，在 [Endpoint Protection] 類別中找到這些設定。

### <a name="require-installation-of-policies-apps-certificate-and-network-profiles----1553555---"></a>要求安裝原則、應用程式、憑證及網路設定檔 <!-- 1553555 -->
在佈建 AutoPilot 裝置期間，系統管理員將能夠禁止使用者存取 Windows 10 RS4 桌面，直到 Intune 安裝原則、應用程式及憑證和網路設定檔為止。

### <a name="rules-for-removing-devices----1609459---"></a>用於移除裝置的規則 <!-- 1609459 -->
將會提供新規則，可讓您自動移除在所設定天數內未簽入的裝置。 若要查看新規則，請移至 [Intune] 窗格，選取 [裝置]，然後選取 [裝置移除規則]。

### <a name="prevent-consumer-apps-and-experiences-on-windows-10-enterprise-rs4-autopilot-devices---1621980---"></a>防止 Windows 10 企業版 RS4 AutoPilot 裝置上的消費者應用程式和體驗<!-- 1621980 -->
您將能夠防止在「Windows 10 企業版 RS4 AutoPilot」裝置上安裝消費者應用程式和體驗。 若要查看此功能，請移至 [Intune] > [裝置註冊] > [Windows 註冊] > [Windows AutoPilot 設定檔] > [新建] > [註冊設定]。 

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

<!-- the following are present prior to 1801 -->

### <a name="app-protection-policies-----679615---"></a>應用程式防護原則 <!-- 679615 -->
Intune 應用程式防護原則能提供建立全域預設原則的能力，以針對整個租用戶中的所有使用者快速啟用保護。

<!-- the following are present prior to 1711 -->

## <a name="notices"></a>通知

目前沒有任何作用中的通知。

### <a name="see-also"></a>另請參閱
如需近期發展的詳細資料，請參閱 [Microsoft Intune 的新功能](whats-new.md)。

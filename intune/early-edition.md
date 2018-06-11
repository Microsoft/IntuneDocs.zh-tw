---
title: 舊版
description: ''
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/30/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 95ad588b084319cd8a0f5f5c5d92da0e892eed50
ms.sourcegitcommit: 97b9f966f23895495b4c8a685f1397b78cc01d57
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2018
ms.locfileid: "34745038"
---
# <a name="the-early-edition-for-microsoft-intune---june-2018"></a>Microsoft Intune 的舊版 - 2018 年 6 月

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

<!-- 1806 start -->

### <a name="corporate-owned-single-use-cosu-support-for-android-devices----1630973---"></a>公司所擁有且適用於 Android 裝置的單次使用 (COSU) 支援 <!-- 1630973 -->

Intune 將支援高度受控、鎖定、Kiosk 樣式的 Android 裝置。 這可讓系統管理員將裝置的用途進一步鎖定為單一應用程式或一小組的應用程式，並可防止使用者在裝置上啟用其他應用程式或執行其他動作。

### <a name="macos-support-for-apple-device-enrollment-program----747651---"></a>macOS 支援 Apple 裝置註冊計劃 <!-- 747651 -->

Intune 支援將 macOS 裝置註冊到 Apple 裝置註冊計劃 (DEP) 中。 操作方法：

1. 在 deploy.apple.com 上，將 macOS 序號指派給 MDM 伺服器。
2. 將該序號匯入到 Intune 中。
3. 建立 macOS 裝置專用的註冊方案設定檔。

### <a name="google-name-changes-for-android-for-work-and-play-for-work---842873---"></a>Android for Work 和 Play for Work 的 Google 名稱變更 <!--842873 -->
Intune 將更新 "Android for Work" 術語以反映 Google 的商標變更。  不再使用 "Android for Work" 和 "Play for Work" 這些詞彙。 視內容而定，將會使用不同的術語：

- 「Android 企業」指的是整體的現代 Android 管理堆疊。
- 「工作設定檔」或「設定檔擁有者」指的是使用工作設定檔管理的 BYOD 裝置。
- 「受控 Google Play」則是指 Google 應用程式存放區。

### <a name="monitor-ios--app-configuration-status-per-device----880037-eeready-eestaged---"></a>監視每個裝置的 iOS 應用程式設定狀態 <!-- 880037 eeready eestaged -->

身為 Microsoft Intune 系統管理員，您可以監視每個受控裝置的 iOS 應用程式設定狀態。 從 Azure 入口網站的 [Microsoft Intune] 中，選取 [裝置] > [所有裝置]。 從受控裝置清單中，選取特定的裝置以顯示裝置的刀鋒視窗。 在裝置的刀鋒視窗中，選取 [應用程式設定]。  

### <a name="3rd-party-keyboards-can-be-blocked-by-app-settings-on-ios----1248481---"></a>iOS 上的應用程式設定可封鎖第三方鍵盤 <!-- 1248481 -->
在 iOS 裝置上，Intune 系統管理員可以在存取原則保護應用程式中的組織資料時，封鎖第三方鍵盤的使用。 當應用程式保護原則 (APP) 設定為封鎖第三方鍵盤時，裝置使用者會在第一次使用第三方鍵盤與公司資料互動時收到一則訊息。 本機鍵盤以外的所有選項都會被封鎖，裝置使用者不會看到它們。 裝置使用者只會看到對話方塊訊息一次。 

### <a name="create-device-compliance-policy-using-firewall-settings-on-macos-devices----1497640---"></a>在 macOS 裝置上使用防火牆設定建立裝置合規性原則 <!-- 1497640 -->
當您建立新的 macOS 合規性原則 ([裝置合規性] > [原則] > [建立原則] >  [平台：macOS] > [系統安全性]) 時，會有一些可用的新 [防火牆] 設定： 
- **防火牆**：設定您環境中處理連入連線的方式。
- **連入連線**：除了基本網際網路服務所需的連線 (例如 DHCP、Bonjour 及 IPSec) 之外，[封鎖] 所有連入連線。 這項設定也會封鎖所有的共用服務。
- **隱形模式**：[啟用] 隱形模式以防止電腦回應探查要求。 電腦會繼續回應已授權應用程式的連入要求。

適用對象：macOS 10.12 和更新版本

### <a name="use-samaccountname-as-the-account-username-for-email-profiles----1500307---"></a>使用 sAMAccountName 作為電子郵件設定檔的帳戶使用者名稱 <!-- 1500307 -->

您可以使用內部部署 **sAMAccountName**，作為 Android、iOS 和 Windows 10 電子郵件設定檔的帳戶使用者名稱。 也可以從Azure Active Directory (Azure AD) 中的 `domain` 或 `ntdomain` 屬性取得網域。 或者，輸入自訂靜態網域。

若要使用這項功能，您必須將來自內部部署 Active Directory 環境的 `sAMAccountName` 屬性同步至 Azure AD。

適用對象：Android、iOS、Windows 10 和更新版本

### <a name="require-non-biometric-passcode-on-app-launch-and-timeout----1506985---"></a>在應用程式啟動和逾時時需要非生物特徵辨識密碼 <!-- 1506985 -->

透過在應用程式啟動時和系統管理員指定的逾時之後要求非生物特徵辨識密碼，Intune 可藉由限制使用生物識別存取公司資料，為啟用行動應用程式管理 (MAM) 的應用程式增強安全性。 這些設定會影響依賴 Touch ID (iOS)、Face ID (iOS)、 Android 生物特徵辨識或其他未來的生物特徵辨識驗證方法來存取其啟用 APP/MAM 之應用程式的使用者。 這些設定可讓 Intune 系統管理員能夠更細微地控制使用者存取，並排除具有多個指紋或其他生物特徵辨識存取方法的裝置可能會向不正確的使用者顯示公司資料的情況。 在 Azure 入口網站中，開啟 [Microsoft Intune]。 選取 [行動裝置應用程式] > [應用程式保護原則] > [新增原則] > [設定]。 找出特定設定的 [存取] 區段。

### <a name="selective-wipe-of-organizations-app-data----1507030---"></a>選擇性抹除組織的應用程式資料 <!-- 1507030 -->
不符合應用程式保護原則 (APP) 存取設定的條件時，系統管理員可以設定選擇性抹除組識資料作為新的動作。  這項功能可協助系統管理員依據預先設定的準則，自動保護並移除應用程式中的機密組織資料。

### <a name="revoking-an-ios-app-purchased-through-vpp----1777384---"></a>撤銷透過 VPP 購買的 iOS 應用程式 <!-- 1777384 -->
身為 Microsoft Intune 系統管理員，您可以撤銷透過大量採購方案 (VPP) 購買的所選 iOS 應用程式授權。 當應用程式不再指派給使用者時，您可以通知他們。 撤銷應用程式授權將不會從該裝置解除安裝相關聯的 VPP 應用程式。 若要解除安裝 VPP 應用程式，您必須將指派動作變更為 [解除安裝]。 回收的授權計數將會反映在 Intune 之 [應用程式] 工作負載中的 [授權的應用程式] 節點。 如需與 iOS VPP 應用程式相關的詳細資訊，請參閱[如何使用 Microsoft Intune 管理透過大量採購方案購買的 iOS 應用程式](vpp-apps-ios.md)。

### <a name="office-365-pro-plus-language-packs----1833450---"></a>Office 365 Pro Plus 語言套件 <!-- 1833450 -->
身為 Intune 系統管理員，您可以為透過 Intune 管理的 Office 365 Pro Plus 應用程式部署其他語言。 可用的語言清單包括語言套件的**類型** (核心、部分和校訂)。 在 Azure 入口網站中，選取 [Microsoft Intune] > [行動裝置應用程式] > [應用程式] > [新增]。 在 [新增應用程式] 刀鋒視窗的 [應用程式類型] 清單中，選取 [Office 365 套件] 下的 [Windows 10]。 選取 [應用程式套件設定] 刀鋒視窗中的 [語言]。

### <a name="revoke-ios-vpp-app-license----1863797---"></a>撤銷 iOS VPP 應用程式授權 <!-- 1863797 -->
身為系統管理員，您可以回收指派給使用者或裝置的 iOS VPP 應用程式授權。 解除安裝 iOS VPP 應用程式也可讓您回收應用程式授權。 然後，您可以選擇將應用程式授權指派給其他使用者或裝置。 如需 iOS VPP 應用程式授權的詳細資訊，請參閱[在 Microsoft Intune 中管理 iOS 大量採購的應用程式](vpp-apps-ios.md)。

### <a name="new-user-experience-update-for-the-company-portal-website---2000968---"></a>公司入口網站的新使用者體驗更新 <!--2000968 -->
我們正在依據客戶的意見反應，將新功能新增至公司入口網站。 您可在 Android、iOS 和 Windows 裝置上體驗現有功能和可用性方面的重大改善。 網站的各個區域 (例如裝置詳細資料、意見反應和支援，以及裝置概觀) 將獲得全新的現代化回應式設計。 此外還包括：

- 簡化所有裝置平台中的工作流程
- 改善裝置識別和註冊流程
- 更有用的錯誤訊息
- 更容易使用的語言，較少的技術專業術語
- 可以共用應用程式的直接連結
- 改善大型應用程式目錄的效能
- 增加所有使用者的協助工具

### <a name="edit-your-office-365-pro-plus-app-deployments----2150145---"></a>編輯 Office 365 Pro Plus 應用程式部署 <!-- 2150145 -->
身為 Microsoft Intune 系統管理員，您可以更有效率地編輯 Office 365 Pro Plus 應用程式部署。 在 Azure 入口網站中，選取 [Microsoft Intune] > [行動裝置應用程式] > [應用程式]。 從應用程式的清單中，選取您的 Office 365 Pro Plus 套件。  

### <a name="per-row-review-of-duplicate-corporate-device-identifiers-uploaded----2203794---"></a>已上傳之重複公司裝置識別碼的每一資料列檢閱 <!-- 2203794 -->
上傳公司識別碼時，Intune 將提供任何重複項目的清單，並可讓您選擇取代或保留現有資訊。 選擇 [裝置註冊] > [公司裝置識別碼] > [新增識別碼] 之後，如果有重複項目，則會出現報表。 

### <a name="manually-add-corporate-device-identifiers----2203803---"></a>手動新增公司裝置識別碼 <!-- 2203803 -->
您可以手動新增公司裝置識別碼。 請選擇 [裝置註冊] > [公司裝置識別碼] > [新增]。

### <a name="new-status-for-devices-in-device-configuration----2308882---"></a>裝置設定中裝置的新狀態 <!-- 2308882 -->
在 [裝置設定] > [概觀] 中，將會新增下列新狀態：
- 成功
- 錯誤
- 衝突
- 擱置
- 不適用。同時顯示了顯示不同平台裝置計數的影像。 例如，如果您要查看 iOS 設定檔，新的磚會顯示同時指派給此設定檔的非 iOS 裝置計數。 

### <a name="device-compliance-supports-3rd-party-anti-virus-solutions----2325484---"></a>裝置合規性支援協力廠商防毒解決方案 <!-- 2325484 -->
當您建立裝置合規性原則 ([裝置合規性] > [原則] > [建立原則] >  [平台：Windows 10 和更新版本] > [設定] > [系統安全性]) 時，會有一些新的 [裝置安全性] 選項： 
- **防毒**：當設定為 [必要] 時，您可以使用向 Windows 資訊安全中心註冊的防毒解決方案 (例如 Symantec) 來檢查合規性。 
- **反間諜功能**：當設定為 [必要] 時，您可以使用向 Windows 資訊安全中心註冊的反間諜功能解決方案 (例如 Symantec) 來檢查合規性。 

適用對象：Windows 10 和更新版本 

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

### <a name="require-non-biometric-passcode-on-cold-app-launch-and-timeout----1506985---"></a>在應用程式冷啟動和逾時時需要非生物特徵辨識密碼 <!-- 1506985 --> 

透過在應用程式冷啟動時和系統管理員指定的逾時之後要求非生物特徵辨識密碼，Intune 可藉由限制使用生物識別存取公司資料，為啟用行動應用程式管理 (MAM) 的應用程式增強安全性。 這些設定會影響依賴 Touch ID (iOS)、Face ID (iOS)、 Android 生物特徵辨識或其他未來的生物特徵辨識驗證方法來存取其啟用 APP/MAM 之應用程式的使用者。 這些設定可讓 Intune 系統管理員能夠更細微地控制使用者存取，並排除具有多個指紋或其他生物特徵辨識存取方法的裝置可能會向不正確的使用者顯示公司資料的情況。 在 Azure 入口網站中，開啟 [Microsoft Intune]。 選取 [行動裝置應用程式] > [應用程式保護原則] > [新增原則] > [設定]。 找出特定設定的 [存取] 區段。

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
您很快便能設定應用程式防護原則，以明確地針對不符合規範的裝置進行抹除、封鎖或警告。 最新的動作「抹除」能從裝置移除您公司的資料。 如果發生抹除，系統會向裝置使用者告知抹除的原因及補救的步驟。 針對某些設定 (例如最小 OS 版本)，您將能套用多個動作 (例如封鎖和抹除)。 當應用程式啟動時，便會觸發這些動作。

### <a name="new-inventory-information-for-windows-devices----1333569-eeready---"></a>適用於 Windows 裝置的新清查資訊 <!-- 1333569 eeready -->

針對 Windows 裝置，下列清查資訊將會針對個別裝置於 [硬體] 索引標籤中提供 ([群組] > [所有行動裝置] > [裝置] > 選擇使用者的裝置 > [檢視內容] > [硬體])：
- TPM
- 防毒
- 反間諜功能
- 防火牆
- UAC
- 電池
- 網域名稱

如需 CSP 如何擷取此資料的詳細資訊，請參閱 [DeviceStatus CSP](https://docs.microsoft.com/en-us/windows/client-management/mdm/devicestatus-csp) 一文中的 DeviceStatus 項目。

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
您將能以範圍群組的形式指派所有使用者、所有裝置，以及所有使用者和所有裝置。 若要這樣做，請選擇 [Intune 角色] > [所有角色] > [原則和設定檔管理員] > [指派] > 選擇指派 > [範圍 (群組)]。

### <a name="autopilot-profiles-moving-to-group-targeting----1877935---"></a>將 AutoPilot 設定檔移至群組目標設定 <!-- 1877935 -->
目前，可將 AutoPilot 部署設定檔指派給選取的裝置。 在推出此功能之後，指派這些設定檔的方法如下：
- 建立包含 AutoPilot 裝置的 (Azure AD) 群組
- 將所需的設定檔指派給 Azure AD 群組。 現在將會把 AutoPilot 設定檔指派給該群組中的 AutoPilot 裝置。

### <a name="management-name-field-will-be-editable----1875989---"></a>管理名稱欄位將可以編輯 <!-- 1875989 -->
您將能在裝置的 [屬性] 刀鋒視窗上編輯管理名稱欄位。 如果要編輯此欄位，請選擇 [裝置] > [所有裝置] > 選擇裝置 > [屬性]。 您可以使用管理名稱欄位來唯一識別裝置。

<!-- 1804 start -->

### <a name="additions-to-local-device-security-options-settings----1403702---"></a>新增本機裝置安全性選項設定 <!-- 1403702 -->
您將能夠為 Windows 10 裝置設定額外的 [本機裝置安全性選項] 設定。 可供使用額外設定的領域包括 Microsoft Network Client、Microsoft Network Server、[網路存取和安全性] 及 [互動式登入]。 當您建立 Windows 10 裝置設定原則時，在 [Endpoint Protection] 類別中找到這些設定。

### <a name="rules-for-removing-devices----1609459---"></a>用於移除裝置的規則 <!-- 1609459 -->
將會提供新規則，可讓您自動移除在所設定天數內未簽入的裝置。 若要查看新規則，請移至 [Intune] 窗格，選取 [裝置]，然後選取 [裝置移除規則]。

### <a name="prevent-consumer-apps-and-experiences-on-windows-10-enterprise-rs4-autopilot-devices---1621980---"></a>防止 Windows 10 企業版 RS4 AutoPilot 裝置上的消費者應用程式和體驗<!-- 1621980 -->
您將能夠防止在「Windows 10 企業版 RS4 AutoPilot」裝置上安裝消費者應用程式和體驗。 若要查看此功能，請移至 [Intune] > [裝置註冊] > [Windows 註冊] > [Windows AutoPilot 設定檔] > [新建] > [註冊設定]。 

<!-- 1803 start -->

#### <a name="multiple-exchange-connector-support----2070451---"></a>多重 Exchange 連接器支援 <!-- 2070451 -->

您不會再受到每個租用戶只能有一個 Microsoft Intune Exchange 連接器的限制了。 Intune 將會支援多個 Exchange 連接器，使您可以用多個內部部署 Exchange 組織來設定 Intune 條件式存取。

透過 Intune 內部部署 Exchange 連接器，您可以根據裝置是否已在 Intune 註冊且符合 Intune 裝置合規性政策，來管理裝置對於您內部部署 Exchange 信箱的存取。 若要設定連接器，請從 Azure 入口網站下載 Intune 內部部署 Exchange 連接器，並安裝在您 Exchange 組織中的伺服器。 在 Microsoft Intune 儀表板中，選擇 [內部部署存取]，然後在 [安裝] 下選擇 [Exchange ActiveSync 連接器]。 下載 Exchange 內部部署連接器，並將其安裝在您 Exchange 組織中的伺服器。 您現在已經沒有一個租用戶只能有一個 Exchange 連接器的限制，因此您如果有其他 Exchange 組織，亦可遵循此相同流程為每個 Exchange 組織下載並安裝連接器。

### <a name="ability-to-deploy-required-line-of-business-lob-apps-to-all-users-on-windows-10-desktop-devices----1627835-rs4---"></a>在 Windows 10 Desktop 裝置上，將所需之企業營運 (LOB) 應用程式部署給所有使用者的能力 <!-- 1627835 RS4 -->
客戶將能夠部署必要的企業營運 Windows 10 應用程式，以安裝在裝置內容中。 這會向裝置上的所有使用者開放使用這些應用程式。 這僅適用於 Windows 10 Desktop 裝置。

### <a name="company-portal-enrollment-improved----1874230--"></a>改善的公司入口網站註冊 <!-- 1874230-->
在 Windows 10 1703 組建或更新版本上使用公司入口網站來註冊裝置的使用者，將能夠完成註冊的第一個步驟，且不需離開應用程式。

### <a name="updating-the-help-and-feedback-experience-on-company-portal-app-for-android---1631531---"></a>更新 Android 的公司入口網站應用程式之說明與意見反應體驗 <!--1631531 -->

Android 公司入口網站應用程式的說明和意見反應體驗將更新，以與 Android 應用程式的最佳做法保持一致。 Android 公司入口網站應用程式將於接下來幾個月內更新，以將 [說明與意見反應] 功能表項目劃分為分開的 [說明] 與 [傳送意見反應] 功能表項目。 **說明**頁面將有**常見問題集**章節和**電子郵件支援** 按鈕，引導使用者上傳記錄給 Microsoft，並將電子郵件傳送給描述問題的公司支援。 **傳送意見反應**會透過標準 Microsoft 意見反應提交來引導使用者，並會提示使用者選擇「我喜歡某些項目」、「我不喜歡某些項目 」，或是「我有個想法」。

<!-- the following are present prior to 1801 -->

### <a name="app-protection-policies-----679615---"></a>應用程式防護原則 <!-- 679615 -->
Intune 應用程式防護原則能提供建立全域預設原則的能力，以針對整個租用戶中的所有使用者快速啟用保護。

<!-- the following are present prior to 1711 -->

## <a name="notices"></a>通知

目前沒有任何作用中的通知。

### <a name="see-also"></a>請參閱
如需近期發展的詳細資料，請參閱 [Microsoft Intune 的新功能](whats-new.md)。




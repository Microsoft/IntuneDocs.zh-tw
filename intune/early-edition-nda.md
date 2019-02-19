---
title: 舊版 - Microsoft Intune
titlesuffix: ''
description: Microsoft Intune 舊版
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/04/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 19994745a232a362d6bba0f09ed3934e492a17ed
ms.sourcegitcommit: 2f431f122ce3ee6b5d0cdb04a0b748d00f83e295
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2019
ms.locfileid: "56265667"
---
# <a name="the-early-edition-for-microsoft-intune---february-2019"></a>舊版的 Microsoft Intune - 2019 年 2 月

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
<!-- 1902 start-->

### <a name="powershell-scripts-can-run-in-a-64-bit-host-on-64-bit-devices----1862675----"></a>PowerShell 指令碼可以在 64 位元裝置上以 64 位元主機執行 <!-- 1862675  -->
當您將 PowerShell 指令碼新增至裝置組態設定檔時，指令碼一律會以 32 位元執行，即使在 64 位元作業系統上也一樣。 在此更新中，系統管理員可以在 64 位元裝置上以 64 位元 PowerShell 主機執行指令碼 ([裝置設定] > [PowerShell 指令碼] > [新增] > [設定] > [Run script in 64 bit PowerShell Host] \(以 64 位元 PowerShell 主機執行指令碼\))。
如需使用 PowerShell 的詳細資料，請參閱 [Intune 中的 PowerShell 指令碼](intune-management-extension.md)。
適用於：Windows 10 及更新版本

### <a name="rename-an-enrolled-windows-device----1911112----"></a>重新命名已註冊的 Windows 裝置 <!-- 1911112  -->
您將能夠重新命名已註冊的 Windows 10 裝置 (RS4 或更新版本)。 若要這樣做，請選擇 [Intune] > [裝置] > [所有裝置] > 選擇裝置 > [重新命名裝置]。

### <a name="assign-scep-certificates-to-a-userless-macos-device-------2340521-----"></a>將 SCEP 憑證指派給無使用者的 macOS 裝置    <!-- 2340521   -->
您能夠將簡單憑證註冊通訊協定 (SCEP) 憑證指派給無使用者的 macOS 裝置，並建立憑證與 Wi-Fi 或 VPN 設定檔的關聯。 這會擴充我們已有的現成支援，以便[將憑證指派給執行 Windows、iOS 和 Android 的無使用者裝置](certificates-scep-configure.md#create-a-scep-certificate-profile)。

### <a name="intune-conditional-access-ui-update------2432313----"></a>Intune 條件式存取 UI 更新   <!-- 2432313  -->
我們將改善 Intune 主控台中的條件式存取 UI。 這些地方包括：
- 以 Azure Active Directory 中的刀鋒視窗取代 Intune 的 [條件式存取] 刀鋒視窗。 由於條件式存取仍是 Azure AD 技術，因此確保您可以存取其完整的設定和組態。
- 將「Exchange 服務連接器」安裝程式重新放置到目前的 [內部部署存取] 刀鋒視窗。 我們也會將該刀鋒視窗重新命名為 [Exchange 存取]。 這項變更會整合您設定和監視 Exchange Online 和內部部署相關詳細資料的位置。

### <a name="intune-will-leverage-google-play-protect-apis-on-android-devices----2577355----"></a>Intune 會在 Android 裝置上利用 Google Play Protect API <!-- 2577355  -->
某些 IT 系統管理員面臨到在 BYOD 的情況下，終端使用者的行動電話最後可能會遭到 Root 或 JB 破解。 這項行為雖然有時並非惡意，但還是會導致為了保護終端使用者裝置上組織資料所設定的許多 Intune 原則遭到略過。 因此，Intune 會針對已註冊和取消註冊的裝置提供 Root 和 JB 破解偵測。 在此版本中，Intune 現在會利用 Google Play Protect API，在我們現有的 Root 破解偵測檢查中新增對已取消註冊裝置的檢查。 雖然 Google 不會共用所發生 Root 破解偵測檢查的全部內容，但我們預期這些 API 會偵測到其裝置基於任何原因而遭到 Root 破解的使用者，這些原因從裝置自訂到能夠在舊版裝置上取得新版 OS 更新。 接著可防止這些使用者存取公司資料，或從其啟用原則的應用程式抹除其公司帳戶。 為了提高價值，IT 系統管理員現在於 [Intune 應用程式防護] 刀鋒視窗中有數項報告更新：「標有旗標的使用者」報告將會顯示透過 Google Play Protect 的 SafetyNet API 掃描偵測到哪些使用者，而「潛在有害的應用程式」報告將會顯示透過 Google 的 Verify Apps API 掃描偵測到哪些應用程式。 這項功能適用於 Android。 

### <a name="win32-app-information-available-in-troubleshooting-blade----2617342------"></a>[疑難排解] 刀鋒視窗提供 Win32 應用程式資訊 <!-- 2617342    -->
您將能夠從 Intune 應用程式的 [疑難排解] 刀鋒視窗，收集 Win32 應用程式安裝的失敗記錄檔。 如需應用程式安裝疑難排解的詳細資訊，請參閱[針對應用程式安裝問題進行疑難排解](troubleshoot-app-install.md)。

### <a name="kiosk-browser-and-microsoft-edge-browser-apps-can-run-on-windows-10-devices-in-kiosk-mode----2935135----"></a>Kiosk 瀏覽器和 Microsoft Edge 瀏覽器應用程式可以在 Windows 10 裝置上以 kiosk 模式執行 <!-- 2935135  -->
您可以使用 kiosk 模式的 Windows 10 裝置來執行一或多個應用程式。 此更新包含在 kiosk 模式中使用瀏覽器應用程式的數項變更，包括：

- 新增 Microsoft Edge 瀏覽器或 Kiosk 瀏覽器以作為 kiosk 裝置上的應用程式執行 ([裝置設定] > [設定檔] > [新增設定檔] > [Windows 10 及更新版本] 平台 > [Kiosk] 設定檔類型)。
- 限制 Microsoft Edge，讓它可以 (或無法) 在 kiosk 模式中執行 ([裝置設定] > [設定檔] > [新增設定檔] > [Windows 10 及更新版本] 平台 > [裝置限制] 設定檔類型 > [Microsoft Edge 瀏覽器])。 未在 kiosk 模式中執行時，終端使用者可以變更 Microsoft Edge 設定。

如需目前的設定清單，請參閱：

- [讓 Windows 10 和更新版本的裝置設定以 kiosk 形式執行](kiosk-settings-windows.md)
- [Microsoft Edge 瀏覽器裝置限制](device-restrictions-windows-10.md#microsoft-edge-browser)

適用於：Windows 10 及更新版本

### <a name="auto-assign-scope-tags-to-resources-created-by-an-admin-with-that-scope----3173823----"></a>自動將範圍標籤指派給系統管理員所建立並具有該範圍的資源 <!-- 3173823  -->
當系統管理員建立資源時，任何指派給系統管理員的範圍標籤都會自動指派給這些新資源。

### <a name="new-device-restriction-settings-for-ios-and-macos-devices----3448774---"></a>iOS 和 macOS 裝置的新裝置限制設定 <!-- 3448774 -->
您可以在執行 iOS 和 macOS 的裝置上限制一些設定和功能 ([裝置設定] > [設定檔] > [新增設定檔] > [iOS] 或 [macOS] 平台 > [裝置限制] 設定檔類型)。 此更新會新增您可以控制的更多功能和設定，包括設定螢幕使用時間，變更 eSIM 設定和行動數據方案、對使用者延遲顯示軟體更新、封鎖內容快取等。
若要查看您目前可以限制的功能和設定，請參閱：
- [iOS 裝置限制設定](device-restrictions-ios.md)
- [macOS 裝置限制設定](device-restrictions-macos.md)

適用於：
- iOS
- macOS

### <a name="failed-enrollment-report-moves-to-the-device-enrollment-blade----3560202---"></a>失敗的註冊報告會移至 [裝置註冊] 刀鋒視窗 <!-- 3560202 -->
**註冊失敗**報告將會移至 [裝置註冊] 刀鋒視窗的 [監視] 區段。 此外，也會新增兩欄 ([註冊方法] 和 [OS 版本])。

### <a name="change-kiosk-to-dedicated-devices----3598402----"></a>將 "Kiosk" 變更為「專用裝置」<!-- 3598402  -->
為了配合 Android 術語，[Kiosk] 將會變更為裝置組態設定檔中 [Android Enterprise] > [裝置擁有者] > [裝置限制] 下的 [專用裝置]。

### <a name="safari-and-delaying-user-software-update-visibility-ios-settings-are-moving-in-the-intune-ui----3640850--3803313----"></a>Safari 及對使用者延遲顯示軟體更新等 iOS 設定將會移至 Intune UI <!-- 3640850, , 3803313  -->
針對 iOS 裝置，您可以進行 Safari 設定及設定軟體更新。 在此更新中，這些設定將會移至 Intune UI 的不同部分：

- Safari 設定將會從 [Safari] ([裝置設定] > [設定檔] > [新增設定檔] > [iOS] 平台 > [裝置限制] 設定檔類型) 移至 [內建應用程式]。 
- [Delaying user software update visibility for supervised iOS devices] \(對使用者延遲顯示受監督 iOS 裝置的軟體更新\) 設定 ([軟體更新] > [更新 iOS 的原則]) 將會移至 [裝置限制] > [一般]。

如需目前設定的清單，請參閱 [iOS 裝置限制](device-restrictions-ios.md)和 [iOS 軟體更新](software-updates-ios.md)。

適用於： 
- iOS

### <a name="enabling-restrictions-in-the-device-settings-is-renamed-to-screen-time-on-ios-devices----3699164----"></a>在 iOS 裝置上，[啟用裝置設定的限制] 已重新命名為 [螢幕使用時間] <!-- 3699164  -->
您可以在受監督的 iOS 裝置上設定 [啟用裝置設定的限制] ([裝置設定] > [設定檔] > [新增設定檔] > [iOS] 平台 > [裝置限制] 設定檔類型 > [一般])。 在此更新中，此設定已重新命名為 [螢幕使用時間 (僅限受監督)]。 其行為完全一樣。 明確說來： 

- iOS 11.4.1 和更早版本：[封鎖] 可防止終端使用者在裝置設定中設定自己的限制。 
- iOS 12.0 和更新版本：[封鎖] 可防止終端使用者在裝置設定中設定自己的 [螢幕使用時間]，包括內容與隱私權限制。 升級為 iOS 12.0 的裝置不會再於裝置設定中看到 [限制] 索引標籤。 這些設定位於 [螢幕使用時間] 中。 

如需目前設定的清單，請參閱 [iOS 裝置限制](device-restrictions-ios.md)。

適用於： 
- iOS

### <a name="app-status-details-for-ios-apps----3761235----"></a>iOS 應用程式的應用程式狀態詳細資料 <!-- 3761235  -->
新增下列應用程式安裝錯誤訊息：
- 在共用的 iPad 上安裝 VPP 應用程式時失敗
- 停用 App Store 時失敗
- 找不到應用程式的 VPP 授權
- 無法使用 MDM 提供者來安裝系統應用程式
- 裝置處於遺失模式或 kiosk 模式時，無法安裝應用程式
- 使用者未登入 App Store 時，無法安裝應用程式

在 Intune 中，選取 [用戶端應用程式] > [應用程式] >「應用程式名稱」> [裝置安裝狀態]。 [狀態詳細資料] 欄將會提供新的錯誤訊息。

<!-- 1901 start -->

### <a name="deployment-of-online-licensed-microsoft-store-for-business-apps----1672660----"></a>線上授權商務用 Microsoft Store 應用程式的部署 <!-- 1672660  -->
您將能夠在裝置內容中指派必要的線上授權商務用 Microsoft Store 應用程式。 以此方式部署商務用 Microsoft Store 應用程式，即可在裝置上為所有使用者安裝應用程式。 這僅適用於 Windows 10 RS4+ 電腦裝置。 您可以從 MSFB 線上授權應用程式的用戶端應用程式指派頁面，存取在裝置內容中安裝的選項。

<!-- 1812 start -->

### <a name="android-enterprise-app-we-app-deployment----1171203---"></a>Android 企業 APP-WE 應用程式部署 <!-- 1171203 -->
針對未註冊的無註冊應用程式保護原則 (APP-WE) 部署案例中的 Android 裝置，您就能使用受控的 Google Play，將市集應用程式和 LOB 應用程式部署給使用者。 具體來說，IT 可以為終端使用者提供應用程式目錄和安裝體驗，藉由允許從不明來源進行安裝，就不再需要終端使用者放寬其裝置的安全性狀態。 此外，此部署案例將提供已改善的使用者體驗。

### <a name="intune-policies-update-authentication-method-and-company-portal-app-installation-----1927359---"></a>Intune 原則會更新驗證方法與公司入口網站應用程式安裝  <!-- 1927359 -->
在已透過 [設定助理] 註冊的裝置上 (透過 Apple 的公司裝置註冊方法之一)，Intune 將不再支援公司入口網站 (當使用者從 App Store 手動安裝時)。 只有當您在註冊期間使用 Apple 設定助理進行驗證時，此變更才有意義。 此變更也只會影響透過下列各項註冊的 iOS 裝置：  
* Apple Configurator
* Apple Business Manager
* Apple School Manager
* Apple 裝置註冊方案 (DEP)

如果使用者從 App Store 安裝公司入口網站應用程式，接著嘗試透過它註冊這些裝置，則它們將會收到錯誤。 這些裝置只有在註冊期間透過 Intune 自動推送時，才會使用公司入口網站。 位於 Azure 入口網站上 Intune 中的註冊設定檔將會更新，如此您就能指定裝置的驗證方式，以及它們是否會收到公司入口網站應用程式。 如果您想讓 DEP 裝置使用者擁有公司入口網站，將必須在註冊設定檔中指定喜好設定。 此外，公司入口網站應用程式中的 [識別您的裝置] 畫面很快就會變成過時。  
若要在已經註冊的 DEP 裝置上安裝公司入口網站，您將必須移至 [Intune] > [用戶端應用程式]，然後使用應用程式設定原則來將它推送為受控應用程式。 有關如何執行這些步驟的詳細資料，將在未來的文件中加以概述。

### <a name="administrative-templates-are-in-public-preview-and-moved-to-their-own-configuration-profile----3322847---"></a>系統管理範本目前處於公開預覽狀態且已移至它們自己的組態設定檔 <!-- 3322847 -->
Intune 中的系統管理範本 ([裝置設定] > [系統管理範本]) 目前為個人預覽版。 使用此更新：系統管理範本包含約 300 個可在 Intune 中管理的設定。 這些設定先前只存在於群組原則編輯器中。
系統管理範本會在公開預覽版中提供。系統管理範本正從 [裝置設定] > [系統管理範本] 移至 [裝置設定] > [設定檔] >[建立設定檔] > 在 [平台] 中選擇 [Windows 10 及更新版本]、在 [設定檔類型] 中選擇 [系統管理範本]。
已啟用報告。適用對象：Windows 10 及更新版本

### <a name="intune-macos-company-portal-dark-mode----3300524---"></a>Intune macOS 公司入口網站深色模式 <!-- 3300524 -->
Intune macOS 公司入口網站現在支援 macOS 的深色模式。 當您在 macOS 10.14+ 裝置上啟用 [深色模式] 時，公司入口網站會將其外觀調整為反映該模式的色彩。

<!-- 1809 start -->  

### <a name="app-protection-policy-app-settings-for-web-data----2662995---"></a>適用於 Web 資料的應用程式防護原則 (APP) 設定 <!-- 2662995 -->
Android 及 iOS 裝置上適用於 Web 內容的應用程式原則設定會進行更新，提升處理 HTTP 和 HTTPS Web 連結的能力，以及透過 iOS 通用連結和 Android 應用程式連結進行資料轉送的能力。  

<!-- 1808 start -->

### <a name="apple-vpp-token-used-by-another-mdm----1488946---"></a>另一個 MDM 所使用的 Apple VPP 權杖 <!-- 1488946 -->
如果 Intune 和另一個 MDM 都正在使用 Apple 大量採購方案 (VPP) 權杖，則 Intune 會偵測並顯示詳細資料。

### <a name="retired-devices-in-the-device-compliance-dashboard----1981119---"></a>[裝置合規性] 儀表板中的已淘汰裝置 <!-- 1981119 -->
在未來的更新中，將會從 [裝置合規性] 儀表板中移除已淘汰裝置。 這會變更您的合規性數字。

## <a name="notices"></a>通知

目前沒有任何作用中的通知。

### <a name="see-also"></a>請參閱
如需近期發展的詳細資料，請參閱 [Microsoft Intune 的新功能](whats-new.md)。

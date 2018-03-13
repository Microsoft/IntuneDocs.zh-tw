---
title: "舊版"
description: 
keywords: 
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 01/24/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: d7c2ec47a163c16de91d3004a6204c1c00feb801
ms.sourcegitcommit: eac89306d1391a6d3ae1179612b0820b19c2baa6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="the-early-edition-for-microsoft-intune---february-2018"></a>舊版 Microsoft Intune - 2018 年 2 月

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


<!-- 1802 start -->

### <a name="new-enrollment-failure-trend-chart-and-failure-reasons-table----1471783---"></a>新註冊失敗趨勢圖和失敗原因表 <!-- 1471783 -->

在 [註冊概觀] 頁面上，您將能夠檢視註冊失敗趨勢和失敗的前五個原因。 按一下圖表或資料表，即可向下鑽研至詳細資料來尋找疑難排解建議和補救建議。

### <a name="prevent-end-users-from-adding-or-removing-accounts-in-the-work-profile----1728700---"></a>防止終端使用者在工作設定檔中新增或移除帳戶 <!-- 1728700 -->    
當您將 Gmail 應用程式部署到 Android for Work 設定檔時，您將可使用 Android for Work 裝置限制設定檔中的 [Add and remove accounts] (新增與移除帳戶) 設定，防止終端使用者在工作設定檔中新增或移除帳戶。

### <a name="app-protection-policies-----679615---"></a>應用程式防護原則 <!-- 679615 -->
Intune 應用程式防護原則能提供建立全域預設原則的能力，以針對整個租用戶中的所有使用者快速啟用保護。

### <a name="intune-support-for-multiple-apple-dep--apple-school-manager-accounts----747685---"></a>Intune 支援多個 Apple DEP / Apple School Manager 帳戶 <!-- 747685 -->

Intune 可支援註冊最多達 100 個來自不同 Apple 裝置註冊計劃 (DEP) 或 Apple School Manager 帳戶的裝置。 每個上傳的權杖可以針對註冊設定檔和裝置來個別管理。 不同的註冊設定檔可以根據上傳的 DEP/School Manager 權杖來自動指派。 如果上傳了多個 School Manager 權杖，則一次只能與 Microsoft School Data Sync 共用一個權杖。

移轉之後，透過 Graph 來管理 Apple DEP 或 ASM 的搶鮮版 (Beta) Graph API 與發佈的指令碼將無法再運作。 新的搶鮮版 (Beta) Graph API 正在開發，將會在移轉後發行。

### <a name="windows-defender-health-status-and-threat-status-reports---854704---"></a>Windows Defender 健全狀況狀態和威脅狀態報告 <!--854704 -->

瞭解 Windows Defender 的健全狀況狀態是管理 Windows 電腦的關鍵。  Intune 會在 Windows Defender 代理程式的健全狀況狀態中新增報告和動作。 在裝置相容性工作負載中使用狀態積存報告，即可看到需要下列任一項的裝置：

- 簽章更新
- 重新啟動
- 手動介入
- 完整掃描
- 需要介入的其他代理程式狀態

在某些情況下可以採取遠端補救動作，例如觸發簽章更新。  報告也會指出回報為**清除**的電腦數目。

每個狀態類別的鑽研報表都會列出需要注意的個別電腦，或那些回報為**清除**的電腦。

### <a name="protocol-exceptions-for-applications---1035509-eeready--"></a>應用程式的通訊協定例外狀況 <!--1035509 eeready-->

您可以建立 Intune 行動應用程式管理 (MAM) 資料傳輸原則的例外狀況，開啟特定的非受控應用程式。 這類應用程式必須為 IT 所信任。 當資料傳輸原則設為 [managed apps only] (僅限受控的應用程式) 時，除您建立的例外狀況，資料傳輸仍僅限於受 Intune 管理的應用程式。 您可以使用通訊協定 (iOS) 或套件 (Android) 來建立限制。

例如，您可以將 Webex 套件新增為 MAM 資料傳輸原則的例外狀況。 這樣可以直接在 Webex 應用程式中開啟受控 outlook 電子郵件訊息中的 Webex 連結。 其他非受控應用程式中的資料傳輸仍會受到限制。

### <a name="customize-your-company-portal-themes-with-hex-codes---1049561-eeready--"></a>以十六進位碼自訂您的公司入口網站佈景主題 <!--1049561 eeready-->

您可以使用十六進位碼自訂公司入口網站應用程式的佈景主題色彩。 當您輸入您的十六進位碼時，Intune 會決定文字色彩，依 [WCAG 2.0 標準](http://www.w3.org/TR/WCAG20)提供文字色彩和背景色彩之間的最高階對比。 您可以在 [Mobile Apps] > **[公司入口網站]** 中預覽文字色彩和公司標誌的色彩。 

### <a name="new-windows-defender-credential-guard-settings-added-to-endpoint-protection-settings---1102252---"></a>新增至 Endpoint Protection 設定的新 Windows Defender Credential Guard 設定 <!--1102252 --> 

新的 [Windows Defender Credential Guard](https://docs.microsoft.com/windows/access-protection/credential-guard/credential-guard] 設定會新增至 [裝置設定] > **[設定檔]** > **[Endpoint Protection]**。 會新增下列設定： 

- 平台安全性層級：指定下次重新開機時是否啟用平台安全性層級。 虛擬化型安全性需要安全開機。 使用直接記憶體存取 (DMA) 保護，可以選擇性啟用虛擬化型安全性。 DMA 保護需要硬體支援，而且只能在正確設定的裝置上啟用。
- 虛擬化型安全性：指定下次重新開機時是否啟用虛擬化型安全性。 
- Windows Defender Credential Guard：以虛擬化型安全性開啟 Credential Guard，以在下次重新開機時，於安全開機平台安全性層級和虛擬化型安全性同時啟用的狀況下，協助保護認證。 可用的選項包括 [停用]、[在包含 UEFI 鎖定的情況下啟用]、[在不含鎖定情況下啟用] 和 [未設定]。 
  - 如果先前是以 [在不含鎖定情況下啟用] 選項開啟 Credential Guard，[停用] 選項就會從遠端關閉它。

  - [在包含 UEFI 鎖定的情況下啟用] 選項可確保無法以登錄機碼或使用群組原則停用 Credential Guard。 若要在使用這項設定之後停用 Credential Guard，您必須將群組原則設成 [停用]，並且移除每部電腦的安全性功能與實際存在的使用者，才能清除保存在 UEFI 中的設定。 只要 UEFI 設定持續存在，就會一直啟用 Credential Guard。

  - [在不含鎖定情況下啟用] 選項可使用群組原則從遠端停用 Credential Guard。 使用此設定的裝置至少必須執行 Windows 10 (1511 版)。

  - [未設定] 選項會保持原則設定的未定義狀態。 群組原則不會將原則設定寫入登錄，所以不會影響到電腦或使用者。 如果目前在登錄中有設定，它不會被修改。

### <a name="synchronize-and-deploy-sparsely-bundled-windows-store-for-business-apps---1222672---"></a>同步處理並鬆散部署配套的商務用 Microsoft Store 應用程式 <!--1222672 -->
購買自商務用 Microsoft Store 的離線應用程式將可同步處理至 Intune 入口網站。 您接著可將這些應用程式部署至裝置群組或使用者群組。 離線應用程式會透過 Intune 安裝，而非市集。

### <a name="reset-passwords-for-android-o-devices----1238299---"></a>重設 Android O 裝置的密碼 <!-- 1238299 -->
您可以為已註冊的 Android O 裝置重設密碼。 當您將「重設密碼」要求傳送至 Android O 裝置時，它會將新的裝置解除鎖定密碼或受控設定檔查問設成目前的使用者。 傳送密碼或查問是以裝置有設定檔擁有者或裝置擁有者作為根據，並立即生效。

### <a name="local-device-security-option-settings----1251887---"></a>本機裝置安全性選項設定 <!-- 1251887 -->
您可以使用新的本機裝置安全性選項設定在 Windows 10 裝置上啟用安全性設定。 當您建立 Windows 10 裝置設定原則時，在 [Endpoint Protection] 類別中找到這些設定。

### <a name="new-printer-settings-for-education-profiles----1308900---"></a>教育版設定檔的新印表機設定 <!-- 1308900 -->

若為教育版設定檔，新的設定會位在 [印表機] 類別下：[印表機]、[預設印表機]、[Add new printers] (新增印表機)。 

### <a name="new-privacy-settings-for-device-restrictions---1308926---"></a>裝置限制的新隱私權設定 <!--1308926 -->

裝置會有兩項新的隱私權設定：

- **發佈使用者活動**：設定此項以**封鎖**防止共用體驗以及在工作切換器中探索最近使用的資源。

- **僅限本機活動**：設定此項以**封鎖**防止共用體驗，以及僅根據本機活動，在工作切換器中探索最近使用的資源。

### <a name="macos-company-portal-support-for-enrollments-that-use-the-device-enrollment-manager----1352411---"></a>macOS 公司入口網站支援使用裝置註冊管理員註冊 <!-- 1352411 -->

使用者可以在使用 macOS 公司入口網站註冊時，使用裝置註冊管理員。

#### <a name="new-settings-for-the-edge-browser---1469166---"></a>Edge 瀏覽器的新設定 <!--1469166 -->

使用 Edge 瀏覽器的裝置會有兩項新設定可用：[Path to favorites file] (我的最愛檔案路徑) 和 [Changes to Favorites] (我的最愛的變更)。 

### <a name="windows-information-protection-wip-encrypted-data-in-windows-search-results----1469193---"></a>Windows 搜尋結果中的 Windows 資訊保護 (WIP) 加密資料 <!-- 1469193 -->

Windows 資訊保護 (WIP) 原則中的新設定可讓您控制 Windows 搜尋結果是否包含 WIP 加密資料。

### <a name="line-of-business-lob-app-support-for-macos----1473977---"></a>macOS 的企業營運 (LOB) 應用程式支援 <!-- 1473977 -->
Intune 會提供安裝 macOS LOB 應用程式的功能。 LOB 應用程式是您提供安裝檔案並使用 Intune 在裝置上安裝應用程式的應用程式。 Microsoft Intune App Wrapping Tool for macOS 是 macOS LOB 應用程式支援的一部分，所以您必須使用它預先處理 macOS 企業營運 (LOB) 應用程式。

### <a name="configure-resource-account-settings-for-surface-hubs----1475674---"></a>設定 Surface Hub 的資源帳戶設定 <!-- 1475674 -->

您可以從遠端設定 Surface Hub 的資源帳戶設定。

Surface Hub 會使用資源帳戶驗證 Skype/Exchange 以加入會議。 您會想要建立唯一的資源帳戶，使 Surface Hub 在會議中顯示為會議室。 例如，像**會議室 B41/6233** 的資源帳戶。

> [!NOTE]
> - 如果欄位留白，您會覆寫先前在裝置上設定的屬性。
>
> - Surface Hub 的資源帳戶內容可以動態變更。 例如，開啟密碼輪換。 因此，Azure 主控台中的這些值很可能需要一些時間才能反映裝置的實際狀況。 
>
>   若要了解 Surface Hub 目前的設定內容，資源帳戶資訊可以包含在硬體清查 (已有 7 天間隔) 中，或當成唯讀屬性。 為在採取遠端動作後強化精確度，您可以立即在執行動作後取得參數狀態，更新 Surface Hub 上的帳戶/參數。

### <a name="ios-app-provisioning-configuration----1581650---"></a>iOS 應用程式佈建設定 <!-- 1581650 -->
您可以指派 iOS 應用程式佈建設定檔，包含或排除安全性群組以免應用程式過期。

### <a name="new-windows-defender-exploit-guard-settings----631893---"></a>新的 Windows Defender 惡意探索防護設定 <!-- 631893 -->

有六項新的 [Attack Surface Reduction] (攻擊表面縮減) 設定和擴充的 [Controlled folder access: Folder protection] (受控資料夾存取權: 資料夾防護) 功能可用。 這些設定位在：Device configuration\Profiles\
建立 profile\Endpoint protection\Windows Defender 惡意探索防護。

#### <a name="attack-surface-reduction"></a>攻擊表面縮減

|設定名稱  |設定選項  |說明  |
|---------|---------|---------|
|進階勒索軟體防護|啟用、稽核、未設定|使用積極的勒索軟體防護。|
|從 Windows 本機安全性授權子系統設立認證竊取旗標|啟用、稽核、未設定|從 Windows 本機安全性授權子系統設立認證竊取旗標 (lsass.exe)。|
|從 PSExec 和 WMI 命令建立處理程序|封鎖、稽核、未設定|封鎖源自 PSExec 和 WMI 命令的處理程序建立。|
|從 USB 執行的不受信任和不帶正負號的處理程序|封鎖、稽核、未設定|封鎖從 USB 執行的不受信任和不帶正負號的處理程序。|
|不符合普遍性、存留期或受信任清單條件的可執行檔|封鎖、稽核、未設定|封鎖執行可執行檔，除非它們符合普遍性、存留期或受信任清單的條件。|

#### <a name="controlled-folder-access"></a>受控資料夾存取權

|設定名稱  |設定選項  |說明  |
|---------|---------|---------|
|資料夾防護 (已實作)|未設定、啟用、僅稽核 (已實作)<br><br> **新增**<br>封鎖磁碟修改、稽核磁碟修改|
保護檔案和資料夾免於惡意應用程式未經授權的變更。<br><br>**啟用**：免於不受信任的應用程式修改或刪除受保護資料夾中的檔案，也不讓這些應用程式在磁碟磁區寫入資料。<br><br>
**僅封鎖磁碟修改**：<br>封鎖不受信任的應用程式在磁碟磁區寫入資料。 不受信任的應用程式仍然可以修改或刪除受保護資料夾中的檔案。|

### <a name="new-windows-defender-application-guard-settings----1631890---"></a>新的 Windows Defender 應用程式防護設定 <!-- 1631890 -->

- **啟用圖形加速**

系統管理員能夠啟用 Windows Defender 應用程式防護的虛擬圖形處理器。 此設定可讓 CPU 將圖形轉譯卸載至 vGPU。 使用圖形運算密集的網站或觀賞容器內的影片時，這可以改善效能。

- **SaveFilestoHost**

系統管理員能夠讓檔案通過在容器中執行的 Microsoft Edge，到主機檔案系統。 開啟這個功能可讓使用者從容器中的 Microsoft Edge 將檔案下載到主機檔案系統。

### <a name="see-enrollment-restrictions-per-user----1634444---"></a>查看每位使用者的註冊限制 <!-- 1634444 -->
在 [疑難排解] 刀鋒視窗中，您可以查看每位使用者作用中的註冊限制。

### <a name="configuring-a-self-updating-mobile-msi-app----1740840---"></a>設定自行更新的行動 MSI 應用程式 <!-- 1740840 -->
您可以設定已知的自行更新行動 MSI 應用程式略過版本檢查程序。 這項功能對於不陷入競爭狀況很有用。 例如，當應用程式開發人員正在執行自動更新的應用程式，也正被 Intune 更新時，就可能發生這種情況。 雙方都可能嘗試在 Windows 用戶端上強制執行某個版本的應用程式，這可能造成衝突。

### <a name="additions-to-system-security-settings-for-windows-10-and-later-compliance-policies---1704133---"></a>Windows 10 和更新版本系統安全性設定新增項目的相容性原則 <!--1704133 -->

Windows 10 相容性設定的新增項目將可供使用，但需要防火牆及 Windows Defender 防毒軟體才能包含此內容。

### <a name="including-and-excluding-app-assignment-based-on-groups-for-android-enterprise----1813081---"></a>Android Enterprise 依據群組來包含和排除應用程式指派 <!-- 1813081 -->
在應用程式指派期間以及選取指派類型之後，Android Enterprise (原稱為 Android for Work) 會支援排除功能。


### <a name="related-sets-of-app-licenses-supported-in-intune----1864117---"></a>Intune 支援的相關應用程式授權集 <!-- 1864117 -->
Azure 入口網站中的 Intune 會支援相關的應用程式授權集，作為 UI 中單一應用程式項目。 此外，從商務用 Microsoft Store 同步處理的任何離線授權應用程式都會合併到單一應用程式項目，而個別套件的所有部署詳細資料都會移轉至單一項目。 若要在 Azure 入口網站中檢視相關的應用程式授權集，請選取 [Mobile Apps] 刀鋒視窗中的 [應用程式授權]。

<!-- the following are present prior to 1802 -->

### <a name="new-option-for-user-authentication-for-apple-bulk-enrollment----747625---"></a>適用於 Apple 大量註冊的使用者驗證新選項 <!-- 747625 -->
Intune 可讓您使用公司入口網站應用程式於下列註冊方法，以便對裝置進行驗證：

- Apple 裝置註冊方案
- Apple School Manager
- Apple Configurator 註冊

使用 [公司入口網站] 選項時，可以強制執行 Azure Active Directory 多重要素驗證，而不會封鎖這些註冊方法。

使用 [公司入口網站] 選項時，針對使用者親和性註冊，Intune 會跳過 iOS 設定輔助程式中的使用者驗證。 這表示該裝置一開始會註冊為無使用者的裝置，因此不會收到使用者群組的設定或原則。 它只會接收裝置群組的設定和原則。 不過，Intune 會自動在裝置上安裝公司入口網站應用程式。 第一位啟動並登入公司入口網站應用程式的使用者，將會在 Intune 中與該裝置產生關聯。 此時，使用者將會收到其使用者群組的設定和原則。 使用者關聯需要重新註冊才可以變更。

### <a name="intune-support-for-multiple-apple-dep--apple-school-manager-accounts----747685---"></a>Intune 支援多個 Apple DEP / Apple School Manager 帳戶 <!-- 747685 -->
Intune 可支援註冊最多達 100 個來自不同 Apple 裝置註冊計劃 (DEP) 或 Apple School Manager 帳戶的裝置。 每個上傳的權杖可以針對註冊設定檔和裝置來個別管理。 不同的註冊設定檔可以根據上傳的 DEP/School Manager 權杖來自動指派。 如果上傳了多個 School Manager 權杖，則一次只能與 Microsoft School Data Sync 共用一個權杖。

移轉之後，透過 Graph 來管理 Apple DEP 或 ASM 的搶鮮版 (Beta) Graph API 與發佈的指令碼將無法再運作。 新的搶鮮版 (Beta) Graph API 正在開發，將會在移轉後發行。

### <a name="targeting-compliance-policies-to-devices-in-device-groups---1307012---"></a>讓合規性原則以裝置群組中的裝置為目標 <!--1307012 -->

您可以讓合規性原則以使用者群組中的使用者為目標。 您可以讓合規性原則以裝置群組中的裝置為目標。

### <a name="windows-information-protection-wip-encrypted-data-in-windows-search-results----1469193---"></a>Windows 搜尋結果中的 Windows 資訊保護 (WIP) 加密資料 <!-- 1469193 -->

Windows 資訊保護 (WIP) 原則中的新設定可讓您控制 Windows 搜尋結果是否包含 WIP 加密資料。

### <a name="remote-printing-over-a-secure-network----1709994----"></a>透過安全網路進行遠端列印 <!-- 1709994  -->
PrinterOn 的無線行動列印方案，可讓使用者隨時隨地透過安全的網路來進行遠端列印。 PrinterOn 將與適用於 iOS 和 Android 的 Intune APP SDK 整合。 您將能透過管理主控台中的 [應用程式保護原則] 刀鋒視窗，讓應用程式保護原則以此應用程式為目標。 終端使用者將能夠透過 Play 商店或 iTunes 下載 'PrinterOn for Microsoft' 應用程式，以在其 Intune 生態系統內使用。



### <a name="microsoft-graph-api-for-intune---general-availability-----1833289---"></a>適用於 Intune 的 Microsoft Graph API - 正式運作  <!-- 1833289 -->
Microsoft Graph 中的 Intune API 可提供以程式設計的方式來存取資料與方法，以自動化 Intune 服務的系統管理動作。  這些 API **正式運作**之後，客戶、合作夥伴和開發人員將能利用這些 API，針對 Intune 或透過 Microsoft Graph 提供的其他 Microsoft 服務，整合相關或需要其支援的內部或商業解決方案。

<!-- the following are present prior to 1801 -->

### <a name="app-protection-policies-----679615---"></a>應用程式防護原則 <!-- 679615 -->
Intune 應用程式防護原則能提供建立全域預設原則的能力，以針對整個租用戶中的所有使用者快速啟用保護。

### <a name="new-ios-device-action------1244701---"></a>新的 iOS 裝置動作 <!-- 1244701 -->
您可以關閉 iOS 10.3 受監督的裝置。 這個動作會立即關閉裝置，而不會警告使用者。 您可以在 [裝置] 工作負載中選取裝置時，於裝置屬性中找到 [關機 (僅限受監督)] 動作。

### <a name="intune-provides-the-account-move-operation-----1573558-1579830---"></a>Intune 提供帳戶移動作業 <!-- 1573558, 1579830 -->
**帳戶移動**可將租用戶從某個 Azure 縮放單位 (ASU) 移轉至另一個。 **帳戶移動**可用於客戶起始的案例 (當您呼叫 Intune 支援小組並要求它時)，也可用於由 Microsoft 驅動的案例 (當 Microsoft 需要對後端對服務進行調整時)。 在**帳戶移動**期間，租用戶會進入唯讀模式 (ROM)。 諸如註冊、重新命名裝置、更新合規性狀態等服務作業，在 ROM 期間都將會失敗。

當一個應用程式指派給多個具有不同應用程式用途的群組時，此變更會處理此混亂。

如果您希望在 11 月服務版本前向資訊工作者入口網站和公司入口網站提供您的應用程式，您有兩個選項：

1. 移除群組的**不適用**指派。
2. 建立不包含指派**必要且可用**用途之成員的新群組，並將該群組指派為**不適用**。

如需詳細資訊，請參閱[如何使用 Microsoft Intune 將應用程式指派給群組](apps-deploy.md)。

> [!Note]
> 在此版本後，您將無法再於 Intune 傳統主控台中檢視或修改行動裝置管理 (MDM) 應用程式指派。 不過，您可以使用 Azure 主控台或 Intune 圖形 API 指派應用程式。

### <a name="configure-an-ios-app-pin----1586774---"></a>設定 iOS 應用程式 PIN <!-- 1586774 -->
您很快就可以要求目標 iOS 應用程式的 PIN。 您可以透過 Azure 入口網站設定 PIN 需求及以天計的到期日期。 必要時，使用者必須設定並使用新的 PIN，才能存取 iOS 應用程式。 只有使用 Intune App SDK 啟用應用程式保護的 iOS 應用程式才支援這項功能。

### <a name="user-experience-update-for-the-company-portal-app-for-ios---1412866--"></a>iOS 版公司入口網站應用程式的使用者體驗更新 <!--1412866-->

我們將發行 iOS 版公司入口網站應用程式的重大使用者體驗更新。 此項更新的重點是全面視覺效果的重新設計，包括提高使用性和存取範圍的現代化外觀及操作。 保留目前所有的 iOS 公司入口網站功能。

我們會透過 Apple TestFlight 計劃，提供更新公司入口網站應用程式的發行前版本讓您使用，並歡迎您提供意見反應。 請在 https://aka.ms/intune_ios_cp_testflight 註冊存取 TestFlight。 

![新 ios 公司入口網站應用程式的預告片影像](./media/ios-cp-app-redesign-1801-teaser.png)

<!-- the following are present prior to 1711 -->

### <a name="azure-active-directory-web-sites-can-require-the-intune-managed-browser-app-and-support-single-sign-on-for-the-managed-browser-public-preview----710595---"></a>Azure Active Directory 網站可以要求使用 Intune Managed Browser 應用程式，並支援 Managed Browser (公開預覽) 的單一登入 <!-- 710595 -->   
使用 Azure Active Directory (Azure AD) 時，您能夠限制行動裝置使用 Intune Managed Browser 應用程式存取網站。 在 Managed Browser 中，網站資料的安全受到保護，並會與使用者的個人資料區隔開來。 此外，針對受 Azure AD 保護的網站，Managed Browser 也支援單一登入功能。 當使用者登入 Managed Browser，或在裝置上搭配使用 Managed Browser 與受 Intune 管理的其他應用程式時，即可在不需輸入認證的情況下，讓 Managed Browser 存取受 Azure AD 保護的公司網站。 這項功能適用於 Outlook Web Access (OWA) 和 SharePoint Online 等網站，以及透過 Azure App Proxy 存取的內部網路資源等其他公司網站。

<!-- the following are present prior to 1709 -->
### <a name="intune-app-protection-and-citrix-mdx-development-tools----709185---"></a>Intune 應用程式防護和 Citrix MDX 開發工具 <!-- 709185 -->
您可以搭配使用 Citrix XenMobile MDX 和 Microsoft Intune 來管理裝置和應用程式。 如此一來，您就可以使用 Citrix 的 mVPN 技術，透過 Intune 應用程式防護原則來管理應用程式。

您可以尋找程式碼存放庫，其中包含適用於 iOS 和 Android 的 Intune App Wrapping Tool 和 Intune App SDK，並與 Citrix MDX mVPN 技術整合。

<!-- the following are present prior to 1711 -->

### <a name="redirecting-macos-users-to-the-new-company-portal-app---1380728--"></a>將 macOS 使用者重新導向至新的公司入口網站應用程式 <!--1380728-->   
當使用者登入公司入口網站，並註冊 macOS 裝置時，系統會指示他們下載 macOS 版的新公司入口網站應用程式以 完成程序。 使用 OS X El Capitan 10.11 或更新版本的 macOS 裝置會發生這種情況。 

<!-- the following are present prior to 1709 -->

### <a name="intune-managed-browser-support-for-ios-and-android----1374196---"></a>iOS 和 Android 的 Intune Managed Browser 支援 <!-- 1374196 -->
自 2017 年 10 月起，Android 應用程式上的 Intune Managed Browser 應用程式只會支援執行 Android 4.4 和更新版本的裝置。 iOS 上的 Intune Managed Browser 應用程式只支援執行 iOS 9.0 及更新版本的裝置。 較舊版本的 Android 和 iOS 能夠繼續使用 Managed Browser，但是無法安裝新版的應用程式，而且可能無法存取所有的應用程式功能。 建議您將這些裝置更新為受支援的作業系統版本。

### <a name="improved-error-message-for-when-a-user-reaches-the-maximum-number-of-devices-allowed-to-enroll----1270370---"></a>改進使用者達到允許註冊的裝置數目上限時的錯誤訊息 <!-- 1270370 -->
使用 Android 裝置的終端使用者不會看到一般錯誤訊息，而是會看到易讀且可採取動作的錯誤訊息：「您已註冊 IT 系統管理員所允許的裝置數目上限。請移除已註冊的裝置，或向您的 IT 系統管理員取得協助。」



## <a name="notices"></a>通知

目前沒有任何作用中的通知。



### <a name="see-also"></a>另請參閱
如需近期發展的詳細資料，請參閱 [Microsoft Intune 的新功能](whats-new.md)。



---
title: "舊版"
description: 
keywords: 
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/06/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 9a2c104200518af31fd05e6b8abe853377767aa9
ms.sourcegitcommit: 9cf05d3cb8099e4a238dae9b561920801ad5cdc6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2018
---
# <a name="the-early-edition-for-microsoft-intune---march-2018"></a>舊版 Microsoft Intune - 2018 年 3 月

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

### <a name="enhanced-jailbreak-detection----846515---"></a>增強的越獄偵測 <!-- 846515 -->

增強的越獄偵測是新的合規性設定，可改進 Intune 評估已越獄裝置的方式。 此設定將導致裝置更頻繁地簽入 Intune ，這會使用裝置的位置服務並影響電池使用量。

### <a name="ability-to-deploy-required-line-of-business-lob-apps-to-all-users-on-windows-10-desktop-devices----1627835-rs4---"></a>在 Windows 10 Desktop 裝置上，將所需之企業營運 (LOB) 應用程式部署給所有使用者的能力 <!-- 1627835 RS4 -->
客戶將能夠部署必要的企業營運 Windows 10 應用程式，以安裝在裝置內容中。 這會向裝置上的所有使用者開放使用這些應用程式。 這僅適用於 Windows 10 Desktop 裝置。 

### <a name="expiring-line-of-business-lob-apps-for-microsoft-intune----748789---"></a>Microsoft Intune 即將到期的企業營運 (LOB) 應用程式 <!-- 748789 -->
在 Azure 入口網站，Intune 將會提醒您即將到期的企業營運應用程式。 在上傳新版本的企業營運應用程式後，Intune 將會從應用程式清單中移除到期通知。

### <a name="company-portal-enrollment-improved----1874230--"></a>改善的公司入口網站註冊 <!-- 1874230-->
在 Windows 10 1703 組建或更新版本上使用公司入口網站來註冊裝置的使用者，將能夠完成註冊的第一個步驟，且不需離開應用程式。

### <a name="new-management-name-column----1333586---"></a>新的管理名稱資料行 <!-- 1333586 -->
名為**管理名稱**的新資料行，會新增至 [裝置] 刀鋒視窗。 此名稱會依照下列公式自動產生且不可編輯，並會指派給每一個裝置： 
- 所有裝置的預設名稱：<username>_<devicetype>_<enrollmenttimestamp>
- 針對大量新增裝置：<PackageId/ProfileId>_<DeviceType>_<EnrollmentTime> 
 
這是在 [裝置] 刀鋒視窗中的可選資料行。 此資料行預設為無法使用，而您只能透過資料行選取器加以存取。 裝置名稱不會受到這個新資料行影響。

### <a name="new-settings-for-windows-defender-security-center-notifications-device-configuration-profile----1631906---"></a>Windows Defender 資訊安全中心裝置組態設定檔的新設定 <!-- 1631906 -->

Windows Defender 資訊安全中心 (WDSC) 通知裝置組態設定檔將新增三個新設定。

系統管理員將能夠：

- 隱藏身分識別柱
- 隱藏硬體柱及其子設定
- 隱藏勒索軟體柱 (商務用 OneDrive 檔案還原)

當您從 WDSC 應用程式隱藏這些柱時，使用者將不能進行這些設定，與隱藏元件相關聯的所有通知也都不會產生。

### <a name="mam-policies-targeted-based-on-management-state----1665993---"></a>根據管理狀態，設為目標的 MAM 原則 <!-- 1665993 -->

您可以根據裝置管理狀態，將 MAM 原則設為目標：

- **iOS 裝置** - 您可以將非受控裝置 (僅限 MAM) 或受 Intune 管理的裝置設為目標。
- **Android 裝置** - 您可以將非受控裝置、受 Intune 管理的裝置、受 Intune 管理的 Android Enterprise 設定檔 (先前稱為 Android for Work) 設為目標。

### <a name="configure-gatekeeper-to-control-macos-app-download-source----1690459--"></a>設定閘道管理員以控制 macOS 應用程式下載來源 <!-- 1690459-->

您可以藉由控制可下載的應用程式來設定閘道管理員，以從應用程式保護您的裝置。 您可以設定下列下載來源：**Mac App Store**、**Mac App Store 和已識別的開發人員**，或 **Anywhere**。 您也可以藉由按住 Control 同時按一下來覆寫這些閘道管理員控制項，以設定使用者是否可以安裝應用程式。

您可以在**裝置設定** -> **建立設定檔** -> **macOS** -> **Endpoint Protection** 中找到這些設定。

### <a name="configure-the-mac-application-firewall----1690461---"></a>設定 Mac 應用程式防火牆 <!-- 1690461 -->

您將能設定 Mac 應用程式防火牆。 您可以利用此項目以每一應用程式為單位控制連線，而非以每一連接埠為單位。 這讓您能更輕鬆地取得防火牆保護的優點，也可協助防止不想要的應用程式控制為合法應用程式開啟之網路連接埠。
 
您可以在**裝置設定** -> **建立設定檔** -> **macOS** -> **Endpoint Protection** 中找到此功能。

啟用防火牆設定後，您可以使用兩種策略來設定防火牆：

- 封鎖所有連入連線

   您可以為目標裝置封鎖所有連入連線。 如果您選擇這樣做，將會針對所有應用程式封鎖連入連線。 

- 允許或封鎖特定應用程式

   您可以允許或封鎖特定的應用程式，使其無法接收連入連線。 您也可以啟用隱形模式，以避免回應探查要求。
 
#### <a name="more-information"></a>詳細資訊

- 封鎖所有連入連線

   這會封鎖所有共用服務 (例如檔案共用和螢幕共用)，使其無法接收連入連線。 仍允許接收連入連線的系統服務是：
   - configd - 實作 DHCP 與其他網路設定服務
   - mDNSResponder - 實作 Bonjour
   - racoon - 實作 IPSec

   若要使用共用服務，請確認**連入連線**設定為**未設定** (而不是**封鎖**)。

- 隱形模式

   啟用此模式來防止電腦回應探查要求。 電腦仍然會回應已授權應用程式的連入要求。 ICMP (ping) 等未預期的要求都會予以忽略。
 

### <a name="updating-the-help-and-feedback-experience-on-company-portal-app-for-android---1631531---"></a>更新 Android 的公司入口網站應用程式之說明與意見反應體驗 <!--1631531 -->

我們將更新 Android 公司入口應用程式的說明和意見反應體驗，以與 Android 應用程式的最佳做法保持一致。 我們將於接下來幾個月內更新 Android 公司入口網站應用程式，以將 **說明與意見反應** 功能表項目劃分為分開的**說明**與**傳送意見反應**功能表項目。 **說明**頁面將有**常見問題集**章節和**電子郵件支援** 按鈕，引導使用者上傳記錄給 Microsoft，並將電子郵件傳送給描述問題的公司支援。 **傳送意見反應**會透過標準 Microsoft 意見反應提交來引導使用者，並會提示使用者選擇「我喜歡某些項目」、「我不喜歡某些項目 」，或是「我有個想法」。

### <a name="custom-book-categories-for-volume-purchase-program-vpp-ebooks----1488911---"></a>為大量採購方案 (VPP) 電子書自訂書籍類別 <!-- 1488911 -->
您可以建立自訂電子書類別，然後將 VPP 電子書指派給這些自訂電子書類別。 終端使用者便可以看見新建立的電子書類別，以及指派給這些類別的書籍。

#### <a name="company-portal-for-android-visual-updates---976944---"></a>Android 視覺效果更新的公司入口網站 <!--976944 -->

我們將為 Android 更新公司入口網站應用程式，以遵循 Android 的 [Material Design](https://material.io/) 指導方針。 當應用程式發行時，我們將發佈新圖示的影像至[應用程式 UI 的新功能](whats-new-app-ui.md)文章。 


<!-- 1802 start -->

### <a name="new-enrollment-failure-trend-chart-and-failure-reasons-table----1471783---"></a>新註冊失敗趨勢圖和失敗原因表 <!-- 1471783 -->

在 [註冊概觀] 頁面上，您將能夠檢視註冊失敗趨勢和失敗的前五個原因。 按一下圖表或資料表，即可向下鑽研至詳細資料來尋找疑難排解建議和補救建議。

### <a name="customize-your-company-portal-themes-with-hex-codes---1049561---"></a>以十六進位碼自訂您的公司入口網站佈景主題 <!--1049561 -->

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

### <a name="reset-passwords-for-android-o-devices----1238299---"></a>重設 Android O 裝置的密碼 <!-- 1238299 -->
您可以為已註冊的 Android O 裝置重設密碼。 當您將「重設密碼」要求傳送至 Android O 裝置時，它會將新的裝置解除鎖定密碼或受控設定檔查問設成目前的使用者。 傳送密碼或查問是以裝置有設定檔擁有者或裝置擁有者作為根據，並立即生效。

### <a name="local-device-security-option-settings----1251887---"></a>本機裝置安全性選項設定 <!-- 1251887 -->
您可以使用新的本機裝置安全性選項設定在 Windows 10 裝置上啟用安全性設定。 當您建立 Windows 10 裝置設定原則時，在 [Endpoint Protection] 類別中找到這些設定。

### <a name="new-printer-settings-for-education-profiles----1308900---"></a>教育版設定檔的新印表機設定 <!-- 1308900 -->

若為教育版設定檔，新的設定會位在 [印表機] 類別下：[印表機]、[預設印表機]、[Add new printers] (新增印表機)。 

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

### <a name="including-and-excluding-app-assignment-based-on-groups-for-android-enterprise----1813081---"></a>Android Enterprise 依據群組來包含和排除應用程式指派 <!-- 1813081 -->
在應用程式指派期間以及選取指派類型之後，Android Enterprise (原稱為 Android for Work) 會支援排除功能。

<!-- the following are present prior to 1802 -->

### <a name="targeting-compliance-policies-to-devices-in-device-groups---1307012---"></a>讓合規性原則以裝置群組中的裝置為目標 <!--1307012 -->

您可以讓合規性原則以使用者群組中的使用者為目標。 您可以讓合規性原則以裝置群組中的裝置為目標。

<!-- the following are present prior to 1801 -->

### <a name="app-protection-policies-----679615---"></a>應用程式防護原則 <!-- 679615 -->
Intune 應用程式防護原則能提供建立全域預設原則的能力，以針對整個租用戶中的所有使用者快速啟用保護。

### <a name="configure-an-ios-app-pin----1586774---"></a>設定 iOS 應用程式 PIN <!-- 1586774 -->
您很快就可以要求目標 iOS 應用程式的 PIN。 您可以透過 Azure 入口網站設定 PIN 需求及以天計的到期日期。 必要時，使用者必須設定並使用新的 PIN，才能存取 iOS 應用程式。 只有使用 Intune App SDK 啟用應用程式保護的 iOS 應用程式才支援這項功能。

<!-- the following are present prior to 1711 -->

### <a name="azure-active-directory-web-sites-can-require-the-intune-managed-browser-app-and-support-single-sign-on-for-the-managed-browser-public-preview----710595---"></a>Azure Active Directory 網站可以要求使用 Intune Managed Browser 應用程式，並支援 Managed Browser (公開預覽) 的單一登入 <!-- 710595 -->   
使用 Azure Active Directory (Azure AD) 時，您能夠限制行動裝置使用 Intune Managed Browser 應用程式存取網站。 在 Managed Browser 中，網站資料的安全受到保護，並會與使用者的個人資料區隔開來。 此外，針對受 Azure AD 保護的網站，Managed Browser 也支援單一登入功能。 當使用者登入 Managed Browser，或在裝置上搭配使用 Managed Browser 與受 Intune 管理的其他應用程式時，即可在不需輸入認證的情況下，讓 Managed Browser 存取受 Azure AD 保護的公司網站。 這項功能適用於 Outlook Web Access (OWA) 和 SharePoint Online 等網站，以及透過 Azure App Proxy 存取的內部網路資源等其他公司網站。

<!-- the following are present prior to 1711 -->

### <a name="redirecting-macos-users-to-the-new-company-portal-app---1380728--"></a>將 macOS 使用者重新導向至新的公司入口網站應用程式 <!--1380728-->   
當使用者登入公司入口網站，並註冊 macOS 裝置時，系統會指示他們下載 macOS 版的新公司入口網站應用程式以 完成程序。 使用 OS X El Capitan 10.11 或更新版本的 macOS 裝置會發生這種情況。 

<!-- the following are present prior to 1709 -->

### <a name="improved-error-message-for-when-a-user-reaches-the-maximum-number-of-devices-allowed-to-enroll----1270370---"></a>改進使用者達到允許註冊的裝置數目上限時的錯誤訊息 <!-- 1270370 -->
使用 Android 裝置的終端使用者不會看到一般錯誤訊息，而是會看到易讀且可採取動作的錯誤訊息：「您已註冊 IT 系統管理員所允許的裝置數目上限。請移除已註冊的裝置，或向您的 IT 系統管理員取得協助。」



## <a name="notices"></a>通知

目前沒有任何作用中的通知。



### <a name="see-also"></a>另請參閱
如需近期發展的詳細資料，請參閱 [Microsoft Intune 的新功能](whats-new.md)。



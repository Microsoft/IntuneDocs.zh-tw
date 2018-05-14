---
title: 在 Microsoft Intune 中於 Windows 10 上新增 Endpoint Protection - Azure | Microsoft Docs
description: 在 Microsoft Intune 中，於 Windows 10 裝置上，使用或設定 Endpoint Protection 設定以啟用 Windows Defender 功能，包括「應用程式防護」、「防火牆」、SmartScreen、加密和 Bitlocker、「惡意探索防護」、「應用程式控制」、「資訊安全中心」，以及本機裝置上的安全性。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/23/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 3af7c91b-8292-4c7e-8d25-8834fcf3517a
ms.reviewer: ilwu
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 22eceb7792aee714fb728d64d8bec2ae8db4167c
ms.sourcegitcommit: 401cedcd7acc6cb3a6f18d4679bdadb0e0cdf443
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
---
# <a name="endpoint-protection-settings-for-windows-10-and-later-in-intune"></a>Intune 中適用於 Windows 10 (和更新版本) 的 Endpoint Protection 設定

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Endpoint Protection 設定檔可讓您控制 Windows 10 裝置上的 BitLocker 和 Windows Defender 等安全性功能。

請使用本文中的資訊，以了解如何建立 Endpoint Protection 設定檔。

> [!NOTE]
> Home 和 Professional 版本的 Windows 10 不支援這些設定。

## <a name="windows-defender-application-guard"></a>Windows Defender 應用程式防護

使用 Microsoft Edge 時，Windows Defender 應用程式防護可保護您的環境免受組織尚未定義為信任網站的影響。 當使用者造訪未列在隔離的網路界限中的網站時，這些網站將在 Hyper-V 中的虛擬瀏覽工作階段中開啟。 信任的網站是由網路界限定義，可以在 [裝置設定] 中進行設定。 

應用程式防護只適用於 Windows 10 (64 位元) 裝置。 使用此設定檔會安裝 Win32 元件，以啟動應用程式防護。

- **應用程式防護**：在 Hyper-V 虛擬化的瀏覽容器中開啟未核准的網站。
- **剪貼簿行為**：選擇本機電腦和應用程式防護虛擬瀏覽器之間允許的複製/貼上動作。
- **企業網站上的外部內容**：封鎖自未經核准的網站載入內容。
- **從虛擬瀏覽器列印**：允許 PDF、XPS、本機及/或網路印表機，以列印虛擬瀏覽器的內容。
- **收集記錄檔**：收集應用程式防護瀏覽工作階段內發生的事件記錄檔。
- **保留使用者產生的瀏覽器資料**：儲存在「應用程式防護」虛擬瀏覽工作階段期間建立的使用者資料 (例如密碼、我的最愛及 Cookie)。
- **圖形加速**：在「應用程式防護」虛擬瀏覽工作階段內運作時，可讓需要載入大量圖形的網站以更快的速度載入。 藉由啟用存取虛擬圖形處理單元的功能，網站可以更快速載入。
- **將檔案下載到主機檔案系統**：可讓使用者將檔案從虛擬化瀏覽器下載到主機作業系統。

## <a name="windows-defender-firewall"></a>Windows Defender 防火牆

### <a name="global-settings"></a>全域設定

這些設定適用於所有網路類型。

- **檔案傳輸通訊協定**：封鎖可以設定狀態的 FTP。
- **刪除前的安全性關聯閒置時間**：*n* 秒偵測不到任何網路流量之後，即刪除安全性關聯。
- **預先共用金鑰編碼**：使用 UTF-8 編碼預先共用的金鑰。
- **IPsec 豁免**：設定自 IPsec 豁免特定的流量，包括**鄰居探索 IPv6 的 ICMP 類型代碼**、**ICMP**、**路由器探索 IPv6 的 ICMP 類型代碼**，和 **IPv4 和 IPv6 的 DHCP 網路流量**。
- **憑證撤銷清單驗證**：設定憑證撤銷清單驗證強制執行方式的值，包括 [停用 CRL 驗證]、[僅撤銷憑證上的 CRL 驗證會失敗]，以及 [發生任何錯誤 CRL 驗證都會失敗]。
- **每個金鑰處理模組都伺機比對驗證組**：如果金鑰處理模組不支援驗證集中所有的驗證套件，設定金鑰處理模組以忽略整個驗證集。
- **封包佇列**：指定如何啟用接收端軟體的縮放比例，處理 IPsec 通道閘道案例中轉接接收和清除的加密文字。 此設定可確保保留封包順序。

### <a name="network-settings"></a>網路設定

這些設定適用於特定的網路類型，包括**網域 (工作場所) 網路**、**私人 (可探索) 網路**和**公用 (非可探索) 網路**。

#### <a name="general-settings"></a>一般設定

- **Windows Defender 防火牆**：啟用此設定可封鎖網路流量。
- **隱形模式**：封鎖防火牆在隱形模式下運作。 封鎖隱形模式可讓您也封鎖 **IPsec 安全封包豁免**。
- **受防護**：啟用此設定和防火牆設定會封鎖所有連入流量。
- **多點傳送廣播的單點傳播回應**：封鎖多點傳送廣播的單點傳播回應。 一般而言，您不希望接收對多點傳送或廣播訊息的單點傳播回應。 這些回應可能表示拒絕服務 (DOS) 攻擊，或者攻擊者嘗試探查已知的即時電腦。
- **輸入通知**：從連接埠的接聽封鎖應用程式時，封鎖通知不向使用者顯示。
- **輸入連線的預設動作**：封鎖防火牆對輸入連線執行的預設動作。

#### <a name="rule-merging"></a>規則合併

- **來自本機存放區的已授權應用程式 Windows Defender 防火牆規則**：套用本機存放區中要辨識並強制執行的已授權防火牆規則。
- **來自本機存放區的全域連接埠 Windows Defender 防火牆規則**：套用本機存放區中要辨識並強制執行的全域連接埠防火牆規則。
- **來自本機存放區的 Windows Defender 防火牆規則**：套用本機存放區中要辨識並強制執行的全域防火牆規則。
- **來自本機存放區的 IPsec 規則**：套用本機存放區的連線安全性規則，不論結構描述或連線安全性規則版本。

## <a name="windows-defender-smartscreen-settings"></a>Windows Defender SmartScreen 設定

- **應用程式及檔案適用的 SmartScreen**：讓 Windows SmartScreen 執行檔案，以及執行應用程式。
- **未經驗證檔案的執行**：讓終端使用者無法執行 Windows SmartScreen 尚未驗證的檔案。

## <a name="windows-encryption"></a>Windows 加密

### <a name="windows-settings"></a>Windows 設定

下列兩個設定適用於所有版本的 Windows 10：

- **加密裝置**：啟用時，系統會提示使用者啟用裝置加密。 此外，還會要求他們確認尚未啟用來自其他提供者的加密。 如果已在另一種加密方法為使用中時開啟 Windows 加密，裝置可能會變得不穩定。
- **加密儲存卡**：啟用此設定可加密裝置使用的任何抽取式儲存卡。


### <a name="bitlocker-base-settings"></a>BitLocker 基本設定

基底設定是適用於所有資料磁碟機類型的通用 BitLocker 設定。 BitLocker 群組原則設定會管理使用者在所有資料磁碟機類型上可以修改的磁碟機加密工作或設定選項。

- **其他磁碟加密警告**：停用使用者電腦上的其他磁碟加密警告提示。
- **設定加密方法**：啟用此設定可設定作業系統、資料和抽取式磁碟機的加密演算法。
  - **作業系統磁碟機的加密**：選擇作業系統磁碟機的加密方法。 建議您使用 XTS-AES 演算法。
  - **固定式資料磁碟機的加密**：選擇固定式 (內建) 資料磁碟機的加密方法。 建議您使用 XTS-AES 演算法。
  - **抽取式資料磁碟機的加密**：選擇抽取式資料磁碟機的加密方法。 如果抽取式磁碟機與不是執行 Windows 10 的裝置搭配使用，建議您使用 AES-CBC 演算法。

### <a name="bitlocker-os-drive-settings"></a>BitLocker 作業系統磁碟機設定

這些設定只套用在作業系統資料磁碟機。

- **啟動時的其他驗證**：設定電腦啟動時的驗證需求，包括使用信賴平台模組 (TPM)。
  - **具有不相容 TPM 晶片的 BitLocker**
  - **相容的 TPM 啟動**：選擇允許、不允許，或需要 TPM 晶片。
  - **相容的 TPM 啟動 PIN**：選擇允許、不允許，或需要搭配 TPM 晶片使用啟動 PIN。
  - **相容的 TPM 啟動金鑰**：選擇允許、不允許，或需要搭配 TPM 晶片使用啟動金鑰。
  - **相容的 TPM 啟動金鑰及 PIN**：選擇允許、不允許，或需要搭配 TPM 晶片使用啟動金鑰及 PIN。
- **最小 PIN 長度**：啟用此設定可設定 TPM 啟動 PIN 的最小長度。
  - **字元數下限**：輸入啟動 PIN 所需的字元數 (**4**-**20**)。
- **OS 磁碟機修復**：啟用此設定可控制在未提供必要的啟動資訊時，如何復原受 BitLocker 保護的作業系統磁碟機。
  - **以憑證為基礎的資料修復代理程式**：如果您希望資料修復代理程式能夠與受 BitLocker 保護的作業系統磁碟機搭配使用，請啟用此設定。
  - **使用者的修復密碼建立**：選擇是否允許、需要還是不允許使用者產生 48 位數的修復密碼。
  - **使用者的修復金鑰建立**：選擇是否允許、需要還是不允許使用者產生 256 位元的修復金鑰。
  - **BitLocker 安裝精靈中的修復選項**：啟用此設定可防止使用者在開啟 BitLocker 時看到或變更修復選項。
  - **將 BitLocker 修復資訊儲存到 AD DS**：啟用在 Active Directory 中儲存 BitLocker 修復資訊的功能。
  - **儲存在 AD DS 的 BitLocker 修復資訊**：設定 BitLocker 修復資訊的哪些部分會儲存在 Active Directory 中。 從下列選項進行選擇：
    - **備份修復密碼和金鑰封裝**
    - **只備份修復密碼**
  - **先將修復資訊儲存在 AD DS 再啟用 BitLocker**：啟用此設定可阻止使用者開啟 BitLocker，除非裝置已加入網域，且 BitLocker 修復資訊成功儲存在 Active Directory 中。
- **開機前修復訊息及 URL**：啟用此設定可設定開機前金鑰修復畫面顯示的訊息及 URL。
  - **開機前修復訊息**：設定開機前修復訊息會向使用者顯示。 從下列選項進行選擇：
    - **使用預設修復訊息及 URL**
    - **使用空白修復訊息及 URL**
    - **使用自訂修復訊息**
    - **使用自訂修復 URL**

### <a name="bitlocker-fixed-data-drive-settings"></a>BitLocker 固定式資料磁碟機設定

- **不受 BitLocker 保護的固定式資料磁碟機的寫入權限**：啟用時，必須在所有固定式或內建的資料磁碟機中啟用 BitLocker 保護，才能進行寫入。
- **固定式磁碟機修復**：啟用此設定可控制在未提供必要的啟動資訊時，如何復原受 BitLocker 保護的固定式磁碟機。
  - **資料修復代理程式**：如果您希望資料修復代理程式能夠與受 BitLocker 保護的固定式磁碟機搭配使用，請啟用此設定。
  - **使用者的修復密碼建立**：設定使用者是允許、需要還是不允許產生 48 位數的修復密碼。  
  - **使用者的修復金鑰建立**：設定使用者是允許、需要還是不允許產生 256 位元的修復金鑰。
  - **BitLocker 安裝精靈中的修復選項**：啟用此設定可防止使用者在開啟 BitLocker 時看到或變更修復選項。
  - **將 BitLocker 修復資訊儲存到 AD DS**：啟用在 Active Directory 中儲存 BitLocker 修復資訊的功能。
  - **AD DS 的 BitLocker 修復資訊**：設定 BitLocker 修復資訊的哪些部分會儲存在 Active Directory 中。 從下列選項進行選擇：
    - **備份修復密碼和金鑰封裝**
    - **只備份修復密碼**
  - **先將修復資訊儲存在 AD DS 再啟用 BitLocker**：啟用此設定可阻止使用者開啟 BitLocker，除非裝置已加入網域，且 BitLocker 修復資訊已成功儲存在 Active Directory 中。

### <a name="bitlocker-removable-data-drive-settings"></a>BitLocker 抽取式資料磁碟機設定

- **不受 BitLocker 保護的抽取式資料磁碟機的寫入權限**：指定是否需要抽取式存放磁碟機的 BitLocker 加密。
  - **在其他組織中設定的裝置的寫入權限**：指定屬於其他組織的抽取式資料磁碟機是否可以寫入。

## <a name="windows-defender-exploit-guard"></a>Windows Defender 惡意探索防護

使用 [Windows Defender 惡意探索防護](https://docs.microsoft.com/windows/threat-protection/windows-defender-exploit-guard/windows-defender-exploit-guard)來管理員工所用應用程式並減少受攻擊面。

### <a name="attack-surface-reduction"></a>攻擊表面縮減

- **標記對 Windows 本機安全性授權子系統進行的認證竊取**

[協助預防搜尋惡意探索程式碼一般感染電腦所使用的動作和應用程式](https://docs.microsoft.com/windows/threat-protection/windows-defender-exploit-guard/attack-surface-reduction-exploit-guard)。

#### <a name="rules-to-prevent-office-macro-threats"></a>預防 Office 巨集威脅的規則

禁止 Office 應用程式採取下列動作：

- **Office 應用程式插入其他處理序 (沒有例外狀況)**
- **Office 應用程式/巨集建立可執行檔內容**
- **Office 應用程式啟動子處理序**
- **Win32 從 Office 巨集程式碼匯入**

#### <a name="rules-to-prevent-script-threats"></a>預防指令碼威脅的規則

請封鎖下列項目以協助防止指令碼威脅：

- **混淆的 js/vbs/ps/巨集程式碼**
- **js/vbs 從網際網路執行裝載下載 (無例外狀況)**
- **從 PSExec 與 WMI 命令建立的程序**
- **從 USB 執行的未受信任及未簽署程序**
- **未符合普遍性、年齡或受信任清單準則的可執行檔**

#### <a name="rules-to-prevent-email-threats"></a>預防電子郵件威脅的規則

請封鎖下列項目以協助防止電子郵件威脅：

- **執行自電子郵件 (webmail/郵件用戶端) 卸除的可執行檔內容 (exe、dll、ps、js、vbs 等) (沒有例外狀況)**

#### <a name="rules-to-protect-against-ransomware"></a>可預防勒索軟體的規則
- **進階勒索軟體保護**

> [!TIP]
> [使用 Windows Defender 惡意探索防護來減少受攻擊面](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-exploit-guard/attack-surface-reduction-exploit-guard) \(英文\) 提供有關這些規則的更多詳細資料。

#### <a name="attack-surface-reduction-exceptions"></a>攻擊表面縮減例外狀況

- **從攻擊介面降低規則中排除的檔案和資料夾**：匯入/新增要從設定規則中排除的位置清單。

### <a name="controlled-folder-access"></a>受控資料夾存取權

協助保護寶貴的資料不受惡意應用程式和威脅侵害，例如勒索軟體。

- **資料夾防護**：保護檔案和資料夾不受惡意應用程式進行不想要的變更。 您可以匯入**可存取受保護資料夾的應用程式清單**或手動新增它們。 您也可以上傳來新增**其他需要保護的資料夾清單**或手動新增它們。

### <a name="network-filtering"></a>網路篩選

封鎖任何應用程式對低評價 IP/網域的輸出連線。

### <a name="exploit-protection"></a>惡意探索保護

上載 XML 檔案，讓您設定記憶體、控制流程以及原則限制，以封鎖**使用者編輯的惡意探索保護介面**。 XML 檔案中的設定可用來封鎖惡意探索應用程式。

若要啟用惡意探索保護，請建立代表所選系統和應用程式風險降低設定的 XML 檔案。 您可以使用下列兩種方法之一執行此作業：

 1. PowerShell：使用一或多個 Get-ProcessMitigation、Set-ProcessMitigation 和 ConvertTo-ProcessMitigationPolicy PowerShell Cmdlet。 Cmdlet 會設定安全防護功能設定，並匯出它們的 XML 表示法。

 2. Windows Defender 資訊安全中心 UI：Windows Defender 資訊安全中心，按一下 [App 與瀏覽器控制]，然後捲動至結果畫面的底部，找到 [惡意探索保護]。 首先，使用 [系統設定] 與 [程式設定] 索引標籤來進行低風險的設定。 然後，在畫面底部找到 [匯出設定] 連結，匯出它們的 XML 表示。

## <a name="windows-defender-application-control"></a>Windows Defender 應用程式控制

使用**應用程式控制程式碼完整性原則**選擇其他必須由 Windows Defender 應用程式控制稽核或信任執行的應用程式。 Windows 元件和所有 Windows 市集的應用程式都自動受信任執行。

在**僅稽核**模式中執行時，不會封鎖應用程式。 **僅稽核**模式會在本機用戶端記錄檔中記錄所有事件。

應用程式控制一經啟用，就只能透過從**強制**變更為**僅稽核**模式來停用。 從**強制**變更為**未設定**模式的結果會是在指派的裝置上繼續強制使用應用程式控制。

## <a name="windows-defender-credential-guard"></a>Windows Defender Credential Guard
Windows Defender Credential Guard 可防止認證遭竊的攻擊。 它會隔離機密資料，因此只有特殊權限的系統軟體可以存取它們。

**Credential Guard** 設定包括：

- [停用]：如果先前是以 [在不含 UEFI 鎖定情況下啟用] 選項開啟 Credential Guard，此選項就會從遠端關閉它。
- [在包含 UEFI 鎖定的情況下啟用]：此選項可確保無法使用登錄機碼或群組原則從遠端停用 Credential Guard。

    > [!NOTE]
    > 如果您使用此設定，而稍後想要停用 Credential Guard，則必須將群組原則設定為 [停用]。 此外，從每一部電腦實際清除 UEFI 設定資訊。 只要 UEFI 設定持續存在，就會一直啟用 Credential Guard。

- [在不含 UEFI 鎖定情況下啟用]：此選項可使用群組原則從遠端停用 Credential Guard。 使用此設定的裝置必須執行 Windows 10 1511 版及更新版本。

當您啟用 Credential Guard 時，也會啟用下列必要的功能：

- **虛擬化型安全性** (VBS)：在下次重新開機期間開啟。 虛擬化型安全性會使用 Windows Hypervisor 來提供安全性服務的支援。
- **安全開機與直接記憶體存取**：使用安全開機和直接記憶體存取 (DMA) 保護開啟 VBS。 DMA 保護需要硬體支援，而且只能在正確設定的裝置上啟用。

## <a name="windows-defender-security-center"></a>Windows Defender 資訊安全中心

Windows Defender 資訊安全中心應用程式是以個別的應用程式或各個功能的處理序運行。 它會透過重要訊息中心顯示通知。 它充當收集器，或查看狀態及執行每項功能一些設定的單一位置。 詳細資訊請參閱 [Windows Defender](https://docs.microsoft.com/windows/threat-protection/windows-defender-security-center/windows-defender-security-center) 文件。

#### <a name="windows-defender-security-center-app-and-notifications"></a>Windows Defender 資訊安全中心應用程式和通知

封鎖使用者對「Windows Defender 資訊安全中心」應用程式之各種區域的存取。 隱藏區段也會封鎖相關通知。

- **病毒與威脅防護**
- **裝置效能與健全狀況**
- **防火牆與網路保護**
- **應用程式與瀏覽器控制**
- **家長監護選項**
- **應用程式顯示區中的通知**：選擇要向使用者顯示的通知。 非重大通知包括 Windows Defender 防毒軟體活動摘要，包括掃描完成時的通知。 所有其他通知都被視為重大通知。

#### <a name="it-contact-information"></a>IT 連絡人資訊

提供要顯示在「Windows Defender 資訊安全中心」應用程式和應用程式通知中的 IT 連絡人資訊。 您可以選擇 [Display in app and in notifications] \(在應用程式和通知中顯示)、[Display only in app] \(只在應用程式中顯示)、[Display only in notifications] \(只在通知中顯示) 或 [Don't display] \(不顯示)。 您必須輸入 **IT 組織名稱**，以及至少下列其中一個連絡選項：

- **IT 部門電話號碼或 Skype 識別碼**
- **IT 部門電子郵件地址**
- **IT 支援網站 URL**

## <a name="local-device-security-options"></a>本機裝置安全性選項

您可以使用這些選項來設定 Windows 10 裝置上的本機安全性設定。

### <a name="accounts"></a>帳戶

- **加入新的 Microsoft 帳戶**：防止使用者在這部電腦上加入新的 Microsoft 帳戶。
- **不使用密碼進行遠端登入**：啟用不受密碼保護的本機帳戶，以從實體裝置以外的位置登入。

#### <a name="admin"></a>系統管理員

- **本機系統管理員帳戶**：決定是否啟用或停用本機系統管理員帳戶。
- **重新命名系統管理員帳戶**：定義與系統管理員帳戶的安全性識別碼 (SID) 相關聯的其他帳戶名稱。

#### <a name="guest"></a>Guest

- **來賓帳戶**：決定是否啟用或停用來賓帳戶。
- **重新命名來賓帳戶**：定義與來賓帳戶的安全性識別碼 (SID) 相關聯的其他帳戶名稱。

### <a name="devices"></a>裝置

- **卸除未登錄的裝置**：防止可攜式電腦不需要登入而脫離連接。
- **安裝共用印表機的印表機驅動程式**：將安裝印表機驅動程式作為連接到共用印表機的一部分，限制為僅限系統管理員。
- **限制本機作用中使用者的 CD-ROM 存取**：啟用此設定允許僅以互動方式登入的使用者存取 CD-ROM 媒體
- **格式化及退出卸除式媒體**：定義可以格式化並退出卸除式 NTFS 媒體的人員：
  - **未設定**
  - **系統管理員與進階使用者**
  - **系統管理員和互動式使用者**

### <a name="interactive-logon"></a>互動式登入

- **鎖定畫面閒置，直到螢幕保護裝置啟動的分鐘數**：定義互動式桌面登入畫面閒置，直到螢幕保護裝置啟動的最長分鐘數。
- **需要 CTRL+ALT+DEL 才能登入**：在使用者登入之前需要按下 CTRL+ALT+DEL。
- **智慧卡移除行為**：判斷從智慧卡讀卡機中移除登入使用者的智慧卡時會發生的情況。
[LocalPoliciesSecurity 選項](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-localpoliciessecurityoptions#localpoliciessecurityoptions-interactivelogon-smartcardremovalbehavior)提供更多詳細資料。

#### <a name="display"></a>顯示

- **鎖定螢幕上的使用者資訊**：設定在工作階段鎖定時顯示的使用者資訊。 如果未設定，則會顯示使用者顯示名稱、網域及使用者名稱。
  - **僅使用者顯示名稱**
  - **不顯示使用者資訊**
  - **未設定**：使用者顯示名稱、網域及使用者名稱
- **隱藏上次登入的使用者**：不顯示在此裝置上登入的最後一個人員名稱。
- **在登入時隱藏使用者名稱**：在輸入認證之後且顯示裝置的桌面之前，不要顯示登入此裝置之人員的使用者名稱。
- **登入訊息標題**：設定給嘗試登入之使用者的訊息標題。
- **登入訊息文字**：設定給嘗試登入之使用者的訊息文字。

### <a name="network-access-and-security"></a>網路存取與安全性

- **具名管道和共用的匿名存取**：限制共用和具名管道設定的匿名存取。 適用於可以匿名存取的設定。
- **SAM 帳戶的匿名列舉**：允許匿名使用者列舉 SAM 帳戶。 Windows 允許匿名使用者列舉網域帳戶和網路共用的名稱。
- **SAM 帳戶和共用的匿名列舉**：可以封鎖匿名 SAM 帳戶和共用的匿名列舉。 Windows 允許匿名使用者列舉網域帳戶和網路共用的名稱。
- **密碼變更時儲存的 LAN Manager 雜湊值**：在下次密碼變更時，選擇是否要儲存新密碼的 LAN Manager (LM) 雜湊值。 預設不會儲存。
- **PKU2U 驗證要求**：封鎖此裝置的 PKU2U 驗證要求以使用線上身分識別。
- **限制 SAM 的遠端 RPC 連線**：編輯預設安全性描述元定義語言字串，以允許或拒絕使用者和群組進行 SAM 的遠端呼叫。
- **安全性描述元**

### <a name="recovery-console-and-shutdown"></a>修復主控台和關閉

- **關閉時清除虛擬記憶體分頁檔**：在裝置關機時清除虛擬記憶體分頁檔。
- **未登入關閉**：封鎖從 Windows 登入畫面關閉電腦的選項。 在此情況下，使用者必須能夠順利登入電腦，然後才能執行系統關機。

### <a name="user-account-control"></a>使用者帳戶控制

- **不安全位置的 UIA 完整性**：啟用來自檔案系統中不安全位置的應用程式以 UIAccess 完整性層級執行。
- **將檔案及登錄寫入失敗虛擬化並儲存至每一使用者位置**：判斷應用程式寫入失敗是否會重新導向至定義的登錄和檔案系統位置。 或者，造成應用程式失敗。
- **僅針對已簽署與驗證過的可執行檔，提升其權限**：允許指定的可執行檔執行之前，強制執行它的 PKI 憑證路徑有效性。

#### <a name="uia-elevation-prompt-behavior-settings"></a>UIA 提高權限提示的行為設定

- **針對系統管理員的提高權限提示**：在管理員核准模式中定義系統管理員提高權限提示的行為：
  - **提高權限而不提示**
  - **在安全桌面提示輸入認證**
  - **在安全桌面提示要求同意**
  - **提示輸入認證**
  - **提示決定是否同意**
  - **未設定**：提示要求同意非 Windows 二進位檔案
- **針對標準使用者的提高權限提示**：定義標準使用者提高權限提示的行為：
  - **自動拒絕提高權限要求**
  - **在安全桌面提示輸入認證**
  - **未設定**：認證的提示
- **將提高權限提示路由傳送至使用者的互動式桌面**：啟用所有的提高權限要求，以前往互動式使用者的桌面而不是安全桌面。 系統會使用系統管理員和標準使用者的提示行為原則設定。
- **針對應用程式安裝的提高權限提示**：需要提高權限的應用程式安裝會提示輸入系統管理員認證。
- **UIA 提高權限提示不使用安全桌面**：允許 UIAccess 應用程式不使用安全桌面來提示提高權限。

#### <a name="admin-approval-mode-settings"></a>管理員核准模式設定

- **內建系統管理員的管理員核准模式**：定義內建的系統管理員帳戶是使用「管理員核准模式」還是以完整系統管理員權限執行所有應用程式。
- **以管理員核准模式執行所有系統管理員**：定義是否啟用管理員核准模式和所有 UAC 原則設定。

### <a name="microsoft-network-client"></a>Microsoft 網路用戶端

- **數位簽章通訊 (如果伺服器同意)**：判斷 SMB 用戶端是否會嘗試交涉 SMB 封包簽署。 啟用 (預設值) 時，Microsoft 網路用戶端會要求伺服器在工作階段設定期間執行 SMB 封包簽署。 如果伺服器上已啟用封包簽署，則會交涉封包簽署。 如果停用此原則，則 SMB 用戶端永遠不會交涉 SMB 封包簽署。
- **將未加密的密碼傳送到協力廠商 SMB 伺服器**：啟用時，允許伺服器訊息區塊 (SMB) 重新導向程式將純文字密碼傳送給驗證期間不支援密碼加密的非 Microsoft SMB 伺服器。

### <a name="microsoft-network-server"></a>Microsoft 網路伺服器

- **數位簽章通訊 (如果用戶端同意)**：判斷 SMB 伺服器是否會與要求 SMB 封包簽署的用戶端協商 SMB 封包簽署。 啟用時，Microsoft 網路伺服器會根據用戶端要求的交涉 SMB 封包簽署。 就是說，如果用戶端已啟用封包簽署，則會交涉封包簽署。 停用 (預設值) 時，SMB 用戶端永遠不會交涉 SMB 封包簽署。
- **數位簽章通訊 (自動)**：判斷 SMB 伺服器元件是否需要封包簽署。 啟用後，Microsoft 網路伺服器不會與 Microsoft 網路用戶端通訊，除非該用戶端同意執行 SMB 封包簽署。 停用 (預設值) 時，用戶端和伺服器之間會交涉 SMB 封包簽署。

## <a name="next-steps"></a>接下來的步驟

若要將此設定檔指派給群組，請參閱[如何指派裝置設定檔](device-profile-assign.md)。

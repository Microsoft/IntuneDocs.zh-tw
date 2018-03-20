---
title: "適用於 Windows 10 的 Microsoft Intune Endpoint Protection 設定"
titlesuffix: 
description: "了解 Windows 10 裝置上可用以控制 BitLocker 等 Endpoint Protection 設定的 Intune 設定。"
keywords: 
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 02/23/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3af7c91b-8292-4c7e-8d25-8834fcf3517a
ms.reviewer: ilwu
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 02a32f678b40b2b40535984e17b41e0a864d8fdf
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/08/2018
---
# <a name="create-endpoint-protection-settings-for-windows-10-and-later-in-microsoft-intune"></a>在 Microsoft Intune 中建立適用於 Windows 10 和更新版本的 Endpoint Protection 設定

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Endpoint Protection 設定檔可讓您控制 Windows 10 裝置上的 BitLocker 和 Windows Defender 等安全性功能。

請使用本文中的資訊，以了解如何建立 Endpoint Protection 設定檔。

> [!Note]
> Home 和 Professional 版本的 Windows 10 不支援這些設定。

## <a name="create-an-endpoint-protection-profile"></a>建立 Endpoint Protection 設定檔

1. 登入 [Azure 入口網站](https://portal.azure.com)。
2. 選擇 [所有服務] > [Intune]。 [Intune] 位於 [監視 + 管理] 區段。
3. 在 [Intune] 刀鋒視窗中，選擇 [裝置設定]。
2. 在 [裝置設定] 刀鋒視窗的 [管理] 區段下，選擇 [設定檔]。
3. 在設定檔刀鋒視窗中，選擇 [建立設定檔]。
4. 在 [建立設定檔] 刀鋒視窗上，為裝置功能設定檔輸入 [名稱] 及 [描述]。
5. 從 [平台] 下拉式清單中，選取 [Windows 10 及更新版本]。
6. 從 [設定檔類型] 下拉式清單中，選擇 [Endpoint Protection]。
7. 設定您想要的設定。 使用本文中的詳細資料有助您了解每個設定的用途。 完成之後，請選擇 [確定]。
8. 返回 [建立設定檔] 刀鋒視窗，然後選擇 [建立]。

設定檔隨即建立，並出現在 [設定檔清單] 刀鋒視窗上。

## <a name="windows-defender-application-guard"></a>Windows Defender 應用程式防護

應用程式防護只適用於 Windows 10 (64 位元) 裝置。 使用此設定檔會安裝 Win32 元件，啟動應用程式防護。

- **應用程式防護** - 在 Hyper-V 虛擬化的瀏覽容器中開啟未核准的站台。
- **剪貼簿行為** - 選擇本機電腦和應用程式防護虛擬瀏覽器之間允許的複製/貼上動作。
- **企業網站上的外部內容** - 封鎖自未經核准的網站載入內容。
- **從虛擬瀏覽器列印** - 允許 PDF、XPS、本機及/或網路印表機，列印虛擬瀏覽器的內容。
- **收集記錄檔** - 收集應用程式防護瀏覽工作階段內發生的事件記錄檔。
- **保留使用者產生的瀏覽器資料** - 允許儲存於應用程式防護虛擬瀏覽工作階段期間內建立的使用者資料 (例如密碼、我的最愛和 Cookie)。
- **圖形加速** - 透過啟用對虛擬圖形處理單位的存取，在應用程式防護虛擬瀏覽工作階段中作業時，加快載入高圖形效能需求網站的速度。


## <a name="windows-defender-firewall"></a>Windows Defender 防火牆

### <a name="global-settings"></a>全域設定

這些設定適用於所有網路類型。

- **檔案傳輸通訊協定** - 封鎖可以設定狀態的 FTP。
- **刪除前的安全性關聯閒置時間** - *n* 秒偵測不到任何網路流量之後，即刪除安全性關聯。
- **預先共用金鑰編碼** - 使用 UTF-8 編碼預先共用的金鑰。
- **IPsec 豁免** - 設定自 IPsec 豁免特定的流量，包括**鄰居探索 IPv6 的 ICMP 類型代碼**、**ICMP**、**路由器探索 IPv6 的 ICMP 類型代碼**，和 **IPv4 和 IPv6 的 DHCP 網路流量**。
- **憑證撤銷清單驗證** - 設定憑證撤銷清單驗證強制執行方式的值，包括 [Disable CRL verification] (停用 CRL 驗證)、[Fail CRL verification on revoked certificate only] (僅撤銷憑證上的 CRL 驗證會失敗)，以及 [Fail CRL verification on any error encountered] (發生任何錯誤 CRL 驗證都會失敗)。
- **每個金鑰處理模組都伺機比對驗證組** - 如果金鑰處理模組不支援驗證集中所有的驗證套件，設定金鑰處理模組以忽略整個驗證集。
- **封包佇列** - 指定如何啟用接收端軟體的縮放比例，處理 IPsec 通道閘道案例中轉接接收和清除的加密文字。 這可確定保留封包順序。

### <a name="network-settings"></a>網路設定

這些設定適用於特定的網路類型，包括**網域 (工作場所) 網路**、**私人 (可探索) 網路**和**公用 (非可探索) 網路**。

#### <a name="general-settings"></a>一般設定

- **Windows Defender 防火牆** - 啟用此設定可封鎖網路流量。
- **隱形模式** - 封鎖防火牆在隱形模式下運作。 封鎖此項目也可讓您封鎖 **IPsec 安全封包豁免**。
- **受防護** - 啟用此功能則防火牆設定會封鎖所有的連入流量。
- **多點傳送廣播的單點傳播回應** - 封鎖多點傳送廣播的單點傳播回應。 一般不希望收到多點傳送或廣播訊息的單點傳播回應，因為這類回應表示阻斷服務攻擊或攻擊者嘗試探查已知的即時電腦。
- **輸入通知** - 從連接埠的接聽封鎖應用程式時，封鎖通知不向使用者顯示。
- **輸入連線的預設動作** - 封鎖防火牆對輸入連線執行的預設動作。

#### <a name="rule-merging"></a>規則合併

- **來自本機存放區的已授權應用程式 Windows Defender 防火牆規則** - 套用本機存放區中要辨識並強制執行的已授權防火牆規則。
- **來自本機存放區的全域連接埠 Windows Defender 防火牆規則** - 套用本機存放區中要辨識並強制執行的全域連接埠防火牆規則。
- **來自本機存放區的 Windows Defender 防火牆規則** - 套用本機存放區中要辨識並強制執行的全域防火牆規則。
- **來自本機存放區的 IPsec 規則** - 套用本機存放區的連線安全性規則，不論結構描述或連線安全性規則版本。

## <a name="windows-defender-smartscreen-settings"></a>Windows Defender SmartScreen 設定

- **應用程式及檔案適用的 SmartScreen** - 讓 Windows SmartScreen 執行檔案，以及執行應用程式。
- **未經驗證檔案的執行** - 讓終端使用者無法執行 Windows SmartScreen 尚未驗證的檔案。

## <a name="windows-encryption"></a>Windows 加密

### <a name="windows-settings"></a>Windows 設定

這些設定適用於所有版本的 Windows 10。

- **加密裝置** - 啟用時，系統會提示使用者啟用裝置加密。 此外，還會要求他們確認尚未啟用來自其他提供者的加密。 如果已在另一種加密方法為使用中時開啟 Windows 加密，裝置可能會變得不穩定。
- **加密儲存卡** - 啟用此設定可加密裝置使用的任何抽取式儲存卡。


### <a name="bitlocker-base-settings"></a>BitLocker 基本設定

基底設定是適用於所有資料磁碟機類型的通用 BitLocker 設定。 BitLocker 群組原則設定會管理使用者在所有資料磁碟機類型上可以修改的磁碟機加密工作或設定選項。

- **其他磁碟加密警告** - 停用使用者電腦上的其他磁碟加密警告提示。
- **設定加密方法** - 啟用此設定可設定作業系統、資料和抽取式磁碟機的加密演算法。
    - **作業系統磁碟機的加密** - 選擇作業系統磁碟機的加密方法。 建議您使用 XTS-AES 演算法。
    - **固定式資料磁碟機的加密** - 選擇固定式 (內建) 資料磁碟機的加密方法。 建議您使用 XTS-AES 演算法。
    - **抽取式資料磁碟機的加密** - 選擇抽取式資料磁碟機的加密方法。 如果抽取式磁碟機與不是執行 Windows 10 的裝置搭配使用，建議您使用 AES-CBC 演算法。

### <a name="bitlocker-os-drive-settings"></a>BitLocker 作業系統磁碟機設定

這些設定只套用在作業系統資料磁碟機。

- **啟動時的其他驗證** - 設定電腦啟動時的驗證需求，包括使用信賴平台模組 (TPM)。
    - **具有不相容 TPM 晶片的 BitLocker**
    - **相容的 TPM 啟動** - 設定 TPM 晶片是已允許、不允許還是必要。
    - **相容的 TPM 啟動 PIN** - 設定搭配 TPM 晶片使用啟動 PIN 是已允許、不允許還是必要。
    - **相容的 TPM 啟動金鑰** - 設定搭配 TPM 晶片使用啟動金鑰是已允許、不允許還是必要。
    - **相容的 TPM 啟動金鑰及 PIN** - 設定搭配 TPM 晶片使用啟動金鑰及 PIN 是已允許、不允許還是必要。
- **最小 PIN 長度** - 啟用此設定可設定 TPM 啟動 PIN 的最小長度。
    - **字元數下限** - 輸入啟動 PIN 所需的字元數 (**4**-**20**)。
- **OS 磁碟機修復** - 啟用此設定可控制在未提供必要的啟動資訊時，如何復原受 BitLocker 保護的作業系統磁碟機。
    - **以憑證為基礎的資料修復代理程式** - 如果您希望資料修復代理程式能夠與受 BitLocker 保護的作業系統磁碟機搭配使用，請啟用此設定。
    - **使用者的修復密碼建立** - 設定使用者是允許、需要還是不允許產生 48 位數的修復密碼。
    - **使用者的修復金鑰建立** - 設定使用者是允許、需要還是不允許產生 256 位元的修復金鑰。
    - **BitLocker 安裝精靈中的修復選項** - 啟用此設定可防止使用者在開啟 BitLocker 時看到或變更修復選項。
    - **將 BitLocker 修復資訊儲存到 AD DS** - 啟用在 Active Directory 中儲存 BitLocker 修復資訊的功能。
    - **儲存在 AD DS 的 BitLocker 修復資訊** - 設定 BitLocker 修復資訊的哪些部分會儲存在 Active Directory 中。 從下列選項進行選擇：
        - **備份修復密碼和金鑰封裝**
        - **只備份修復密碼**
    - **先將修復資訊儲存在 AD DS 再啟用 BitLocker** - 啟用此設定可阻止使用者開啟 BitLocker，除非裝置已加入網域，且 BitLocker 修復資訊成功儲存在 Active Directory 中。
- **開機前修復訊息及 URL** - 啟用此設定可設定開機前金鑰修復畫面顯示的訊息及 URL。
    - **開機前修復訊息** - 設定開機前修復訊息會向使用者顯示。 從下列選項進行選擇：
        - **使用預設修復訊息及 URL**
        - **使用空白修復訊息及 URL**
        - **使用自訂修復訊息**
        - **使用自訂修復 URL**


### <a name="bitlocker-fixed-data-drive-settings"></a>BitLocker 固定式資料磁碟機設定

- **不受 BitLocker 保護的固定式資料磁碟機的寫入權限** - 啟用時，必須在所有固定式或內建的資料磁碟機中啟用 BitLocker 保護，才能進行寫入。
- **固定式磁碟機修復** - 啟用此設定可控制在未提供必要的啟動資訊時，如何復原受 BitLocker 保護的固定式磁碟機。
    - **資料修復代理程式** - 如果您希望資料修復代理程式能夠與受 BitLocker 保護的固定式磁碟機搭配使用，請啟用此設定。
    - **使用者的修復密碼建立** - 設定使用者是允許、需要還是不允許產生 48 位數的修復密碼。  
    - **使用者的修復金鑰建立** - 設定使用者是允許、需要還是不允許產生 256 位元的修復金鑰。
    - **BitLocker 安裝精靈中的修復選項** - 啟用此設定可防止使用者在開啟 BitLocker 時看到或變更修復選項。
    - **將 BitLocker 修復資訊儲存到 AD DS** - 啟用在 Active Directory 中儲存 BitLocker 修復資訊的功能。
    - **AD DS 的 BitLocker 修復資訊** - 設定 BitLocker 修復資訊的哪些部分會儲存在 Active Directory 中。 從下列選項進行選擇：
        - **備份修復密碼和金鑰封裝**
        - **只備份修復密碼**
    - **先將修復資訊儲存在 AD DS 再啟用 BitLocker** - 啟用此設定可阻止使用者開啟 BitLocker，除非裝置已加入網域，且 BitLocker 修復資訊已成功儲存在 Active Directory 中。

### <a name="bitlocker-removable-data-drive-settings"></a>BitLocker 抽取式資料磁碟機設定

- **不受 BitLocker 保護的抽取式資料磁碟機的寫入權限** - 指定是否需要抽取式存放磁碟機的 BitLocker 加密。
  - **在其他組織中設定的裝置的寫入權限** - 指定屬於其他組織的抽取式資料磁碟機是否可以寫入。

## <a name="windows-defender-exploit-guard"></a>Windows Defender 惡意探索防護

使用 [Windows Defender 惡意探索防護](https://docs.microsoft.com/windows/threat-protection/windows-defender-exploit-guard/windows-defender-exploit-guard)來管理員工所用應用程式並減少受攻擊面。

### <a name="attack-surface-reduction"></a>攻擊表面縮減

[協助預防搜尋惡意探索程式碼一般感染電腦所使用的動作和應用程式](https://docs.microsoft.com/windows/threat-protection/windows-defender-exploit-guard/attack-surface-reduction-exploit-guard)。

#### <a name="rules-to-prevent-office-macro-threats"></a>預防 Office 巨集威脅的規則

禁止 Office 應用程式採取下列動作：

- **Office 應用程式插入其他處理序 (沒有例外狀況)**
- **Office 應用程式/巨集建立可執行檔內容**
- **Office 應用程式啟動子處理序**
- **Win32 從 Office 巨集程式碼匯入**

#### <a name="rules-to-prevent-script-threats"></a>預防指令碼威脅的規則

封鎖這些以利預防指令碼威脅：

- **混淆的 js/vbs/ps/巨集程式碼**
- **js/vbs 從網際網路執行裝載下載 (無例外狀況)**

#### <a name="rules-to-prevent-email-threats"></a>預防電子郵件威脅的規則

封鎖此項目以利預防電子郵件威脅：

- **執行自電子郵件 (webmail/郵件用戶端) 卸除的可執行檔內容 (exe、dll、ps、js、vbs 等) (沒有例外狀況)**

#### <a name="attack-surface-reduction-exceptions"></a>攻擊表面縮減例外狀況

- **從攻擊介面降低規則中排除的檔案和資料夾** - 匯入/新增要從設定規則中排除的位置清單。

### <a name="controlled-folder-access"></a>受控資料夾存取權

協助保護寶貴的資料不受惡意應用程式和威脅侵害，例如勒索軟體。

- **資料夾防護** - 保護檔案和資料夾不受惡意應用程式進行不想要的變更。 您可以匯入**可存取受保護資料夾的應用程式清單**或手動新增它們。 您也可以上傳來新增**其他需要保護的資料夾清單**或手動新增它們。

### <a name="network-filtering"></a>網路篩選

封鎖任何應用程式對低評價 IP/網域的輸出連線。

### <a name="exploit-protection"></a>惡意探索保護

上載 XML 檔案，讓您設定記憶體、控制流程，以及可用來封鎖惡意探索應用程式的原則限制，以封鎖**使用者編輯的惡意探索保護介面**。

若要啟用惡意探索保護，請建立代表所選系統和應用程式風險降低設定的 XML 檔案。 您可以使用下列兩種方法之一執行此作業：

 1. PowerShell：使用一或多個 Get-ProcessMitigation、Set-ProcessMitigation 和 ConvertTo-ProcessMitigationPolicy PowerShell Cmdlet 設定降低風險的設定，再匯出它們的 XML 表示。

 2. Windows Defender 資訊安全中心 UI：Windows Defender 資訊安全中心，按一下 [App 與瀏覽器控制]，然後捲動至結果畫面的底部，找到 [惡意探索保護]。 首先，使用 [系統設定] 與 [程式設定] 索引標籤來進行低風險的設定。 然後，在畫面底部找到 [匯出設定] 連結，匯出它們的 XML 表示。

## <a name="windows-defender-application-control"></a>Windows Defender 應用程式控制

使用**應用程式控制程式碼完整性原則**選擇其他需要 Windows Defender 應用程式控制稽核或信任執行的應用程式。 Windows 元件和所有 Windows 市集的應用程式都自動受信任執行。

在**僅稽核**模式中執行時，不會封鎖應用程式。 **僅稽核**模式會在本機用戶端記錄檔中記錄所有事件。

應用程式控制一經啟用，就只能透過從**強制**變更為**僅稽核**模式來停用。 從**強制**變更為**未設定**模式的結果會是在指派的裝置上繼續強制使用應用程式控制。

## <a name="windows-defender-security-center"></a>Windows Defender 資訊安全中心

Windows Defender 資訊安全中心應用程式是以個別的應用程式或各個功能的處理序運行，且透過控制中心顯示通知。 它充當收集器，或查看狀態及執行每項功能一些設定的單一位置。 詳細資訊請參閱 [Windows Defender](https://docs.microsoft.com/windows/threat-protection/windows-defender-security-center/windows-defender-security-center) 文件。

#### <a name="windows-defender-security-center-app-and-notifications"></a>Windows Defender 資訊安全中心應用程式和通知

封鎖使用者存取 Windows Defender 資訊安全中心應用程式的不同區域。 隱藏區段也會封鎖相關通知。

- **病毒與威脅防護**
- **裝置效能與健全狀況**
- **防火牆與網路保護**
- **應用程式與瀏覽器控制**
- **家長監護選項**
- **應用程式顯示區中的通知** - 選擇要向使用者顯示的通知。 非重大通知包括 Windows Defender 防毒軟體活動摘要，包括掃描完成時的通知。 所有其他通知都被視為重大通知。

#### <a name="it-contact-information"></a>IT 連絡人資訊

提供 IT 連絡人資訊，顯示在 Windows Defender 資訊安全中心應用程式和應用程式通知中。 您可以選擇 [Display in app and in notifications] (在應用程式和通知中顯示)、[Display only in app] (只在應用程式中顯示)、[Display only in notifications] (只在通知中顯示) 或 [Don't display] (不顯示)。 您必須定義 **IT 組織名稱**以及至少一個下列連絡選項：

- **IT 部門電話號碼或 Skype 識別碼**
- **IT 部門電子郵件地址**
- **IT 支援網站 URL**

## <a name="next-steps"></a>接下來的步驟

若想繼續，並將此設定檔指派給群組，請參閱[如何指派裝置設定檔](device-profile-assign.md)。

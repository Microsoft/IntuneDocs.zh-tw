---
title: Microsoft Defender 進階威脅防護的 Intune 安全性基準設定
titleSuffix: Microsoft Intune
description: 由 Intune 支援、用於管理 Microsoft Defender 進階威脅防護的安全性基準設定Advanced Threat Protection
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 07/25/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: karthib
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: a2cb5d7375ae5b76a24861872d4abf786f199dfd
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72508999"
---
# <a name="microsoft-defender-advanced-threat-protection-baseline-settings-for-intune"></a>Intune 的 Microsoft Defender 進階威脅防護基準設定

檢視 Microsoft Intune 支援的 Microsoft Defender 進階威脅防護 (先前稱為 Windows Defender 進階威脅防護) 基準設定。 進階威脅防護 (ATP) 基準預設值代表 ATP 建議的設定，可能不符合其他安全性基準的基準預設值。  

當您的環境符合使用 [Microsoft Defender 進階威脅防護](advanced-threat-protection.md#prerequisites)的必要條件時，即可使用 Microsoft Defender 進階威脅防護基準。 

此基準已針對實體裝置進行優化，目前不建議用於虛擬機器（Vm）或 VDI 端點。 特定基準設定可能會影響虛擬化環境上的遠端互動式工作階段。 如需詳細資訊，請參閱 Windows 文件中的[提高 Microsoft Defender ATP 安全性基準的合規性](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/configure-machines-security-baseline) \(英文\)。


> [!NOTE]  
> ATP 基準設定現為**預覽**。 在預覽狀態中，可用設定清單以及此內容呈現那些設定的順序可能不符合入口網站中提供的項目。  
>
> 當基準設定結束預覽時，將會更新此內容以反映 Intune 支援的最新安全性基準設定清單。

## <a name="application-guard"></a>應用程式防護  
如需詳細資訊，請參閱 Windows 文件中的 [WindowsDefenderApplicationGuard CSP](https://docs.microsoft.com/windows/client-management/mdm/windowsdefenderapplicationguard-csp) \(英文\)。  

使用 Microsoft Edge 時，Microsoft Defender 應用程式防護可保護您的環境免受組織不信任之網站的影響。 當使用者瀏覽未列在隔離之網路界限中的網站時，這些網站將在 Hyper-V 虛擬瀏覽工作階段中開啟。 信任的網站是由網路界限定義的。  

- **應用程式防護** - *Settings/AllowWindowsDefenderApplicationGuard*  
  選取 [是]  表示開啟此功能，這會在 Hyper-V 虛擬化瀏覽容器中開啟未受信任的網站。 當設定為 [尚未設定]  時，所有網站 (受信任與未受信任) 都會在裝置上開啟，而非在虛擬化容器中開啟。  

  **預設值**：是
 
  - **企業網站上的外部內容** - *Settings/BlockNonEnterpriseContent*  
    選取 [是]  以封鎖從未經核准的網站載入內容。 當設定為 [尚未設定]  時，非企業網站可在裝置上開啟。 
 
    **預設值**：是

  - **剪貼簿行為** - *Settings/ClipboardSettings*  
    選擇要在本機電腦和應用程式防護虛擬瀏覽器之間允許的複製與貼上動作。  這些選項包括：
    - *尚未設定*  
    - *封鎖兩者* - 資料無法在電腦與虛擬瀏覽器之間傳輸。  
    - *封鎖主機到容器* - 資料無法從電腦傳輸到虛擬瀏覽器。
    - *封鎖容器到主機* - 資料無法從虛擬瀏覽器傳輸到主機電腦。
    - *皆不封鎖* - 不封鎖內容。  

    **預設**：封鎖兩者  

- **Windows 網路隔離原則 – 企業網路網域名稱**  
  如需詳細資訊，請參閱 Windows 文件中的[原則 CSP - NetworkIsolation](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-networkisolation) \(英文\)。
  
  以網域、IP 位址範圍與網路界限的方式指定企業資源清單，這些資源裝載在「應用程式防護」將其視為企業站台的雲端。  

  **預設值**：securitycenter.windows.com

## <a name="application-reputation"></a>應用程式信譽  

如需詳細資訊，請參閱 Windows 文件中的 [Policy CSP - SmartScreen](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-smartscreen) (原則 CSP - SmartScreen)。

- **封鎖未經驗證檔案的執行**  
    防止使用者執行未經驗證的檔案。 當設定為 [尚未設定]  時，員工可以忽略 SmartScreen 警告並執行惡意檔案。 設定為 [是]  ，以便員工不可忽略 SmartScreen 警告並執行惡意檔案。  
  
    **預設值**：是

- **應用程式和檔案需要 SmartScreen**  
  設定為 [是]  以啟用適用於 Windows 的 SmartScreen。  

  **預設值**：是

## <a name="attack-surface-reduction"></a>攻擊表面縮減  

- **Office 應用程式啟動子處理序**  
  [受攻擊面縮小規則](/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#attack-surface-reduction-rules) – 當設定為 [封鎖]  時，Office 應用程式將無法建立子處理序。 Office 應用程式包括 Word、Excel、PowerPoint、OneNote 與 Access。 建立子處理序是典型的惡意程式碼行為，特別是針對試圖使用 Office 應用程式啟動或下載惡意可執行檔的巨集型攻擊。  

  **預設值**：封鎖

- **指令碼下載的承載執行類型**  
  [Defender/PUAProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-puaprotection) – 指定下載或嘗試安裝之潛在垃圾應用程式的偵測層級。  

  **預設值**：封鎖 

- **防止認證竊取類型**  
  設定為 [啟用]  以[使用 Credential Guard 保護衍生的網域認證](https://docs.microsoft.com/windows/security/identity-protection/credential-guard/credential-guard) \(部分機器翻譯\)。 Windows Defender Credential Guard 使用以虛擬化為基礎的安全性來隔離祕密，只有具特殊權限的系統軟體才能進行存取。 未經授權存取這些機密資料可能會導致認證竊取攻擊，例如傳遞雜湊或傳遞票證。 Windows Defender Credential Guard 會保護 NTLM 密碼雜湊、Kerberos 票證授權票證及應用程式儲存為網域認證的認證，以防止這些攻擊。  

  **預設值**：啟用

- **電子郵件內容執行類型**  
  [受攻擊免縮小規則](/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#attack-surface-reduction-rules) – 當設定為 [封鎖]  時，此規則可防止從 Microsoft Outlook 或網路郵件 (例如 Gmail.com 或 Outlook.com) 中出現的電子郵件，執行或啟動下列檔案類型：  

  - 可執行檔 (例如 .exe、.dll 或 .scr)  
  - 指令碼檔案 (例如 PowerShell .ps、VisualBasic .vbs 或 JavaScript .js 檔案)  
  - 指令碼封存檔案  

  **預設值**：封鎖

- **Adobe Reader 在子處理序中啟動**  
  [受攻擊面縮小規則](/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#attack-surface-reduction-rules) – *啟用*此規則以封鎖 Adobe Reader，使其無法建立子處理序。 惡意程式碼可以透過社交工程或惡意探索來下載並啟動額外的承載並以 Adobe Reader 為跳板發動攻擊。  

  **預設值**：啟用

- **撰寫混淆的巨集程式碼類型**  
  [受攻擊面縮小規則](/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#attack-surface-reduction-rules) – 惡意程式碼與其他威脅可能會在某些指令檔中，嘗試混淆或隱藏其惡意程式碼。 此規則可防止看似混淆的指令碼執行。  
    
  **預設值**：封鎖

- **不受信任的 USB 處理序類型**  
  [受攻擊面縮小規則](/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#attack-surface-reduction-rules) – 當設定為 [封鎖]  時，來自 USB 抽取式磁碟機與 SD 卡且未經簽署或未受信任的可執行檔將無法執行。

  可執行檔包括：
  - 可執行檔 (例如 .exe、.dll 或 .scr)
  - 指令碼檔案 (例如 PowerShell .ps、VisualBasic .vbs 或 JavaScript .js 檔案)  

  **預設值**：封鎖

- **Office 應用程式的其他處理序插入類型**  
  [受攻擊面縮小規則](/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#attack-surface-reduction-rules) - 當設定為 [封鎖]  時，Office 應用程式 (包括 Word、Excel、PowerPoint 與 OneNote) 無法將程式碼插入到其他處理序中。 程式碼插入通常會利用這點來執行惡意程式碼，試圖隱藏活動不讓防毒掃描引擎發現。  

  **預設值**：封鎖

- **Office 巨集程式碼允許 Win32 匯入類型**  
  [受攻擊面縮小規則](/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#attack-surface-reduction-rules) - 當設定為 [封鎖]  時，此規則會嘗試封鎖包含可匯入 Win32 DLL 之巨集程式碼的 Office 檔案。 Office 應用程式包括 Word、Excel、PowerPoint 與 OneNote。 惡意軟體可能會利用 Office 檔案中的巨集程式碼來匯入和載入 Win32 DLL，這些 DLL 接著可用來進行 API 呼叫，以便允許進一步感染整個系統。  

  **預設值**：封鎖

- **Office 通訊應用程式在子處理序中啟動**  
  [受攻擊面縮小規則](/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#attack-surface-reduction-rules) – 當設定為 [啟用]  時，此規則會防止 Outlook 建立子處理序。 透過封鎖建立子程序的動作，此規則可保護您免於社交功能攻擊並防止惡意探索程式碼濫用 Outlook 中的弱點。  

  **預設值**：啟用

- **Office 應用程式可執行的內容建立或啟動類型**  
  [受攻擊面縮小規則](/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#attack-surface-reduction-rules) – 當設定為 [封鎖]  時，Office 應用程式將無法建立可執行的內容。 Office 應用程式包括 Word、Excel、PowerPoint、OneNote 與 Access。  

  此規則會將目標鎖定在可疑且惡意附加元件和指令碼 (延伸模組) 為建立或啟動可執行檔所使用的典型行為。 這是典型的惡意軟體手段。 延伸模組會被封鎖而無法供 Office 應用程式使用。 一般而言，這些延伸模組會使用 Windows Scripting Host (.wsh 檔案) 執行指令碼，來將特定工作自動化或提供使用者建立的附加元件功能。

  **預設值**：封鎖

## <a name="bitlocker"></a>BitLocker  

如需詳細資訊，請參閱 Windows 文件中的 [BitLocke 群組原則設定](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-group-policy-settings) \(部分機器翻譯\)。  

- **加密裝置**  
  選取 [是]  以啟用 BitLocker 裝置加密。 視裝置硬體與 Windows 版本而定，系統可能會要求裝置使用者確認裝置上沒有第三方加密。 在第三方加密作用中的情況下開啟 Windows 加密會造成裝置不穩定。  

   **預設值**：是

- **BitLocker 抽取式磁碟機原則**  
  此原則的值決定 BitLocker 用於抽取式磁碟機加密的加密強度。 企業可控制加密層級以提高安全性 (AES-256 強於 AES-128)。 如果您選取 [是]  以啟用此設定，則能夠為固定資料磁碟機、作業系統磁碟機和抽取式資料磁碟機個別設定加密演算法和金鑰加密強度。 如果是固定磁碟機和作業系統磁碟機，建議您使用 XTS-AES 演算法。 如果是抽取式磁碟機，若在其他未執行 Windows 10 1511 版或更新版本的裝置上使用該磁碟機，您應該使用 AES-CBC 128 位元或 AES-CBC 256 位元。 如果磁碟機已加密或加密正在進行中，變更加密方法就沒有任何作用。 在這些情況下，會忽略這個原則設定。 

  針對 BitLocker 抽取式磁碟機原則，請設定下列設定：

  - **寫入存取需要加密**  
    **預設值**：是

  - **加密方法**  
    **預設值**：AES 128 位元 CBC

- **BitLocker 固定磁碟機原則**  
  此原則的值決定 BitLocker 用於固定式磁碟機加密的加密強度。 企業可控制加密層級以提高安全性 (AES-256 強於 AES-128)。 如果您啟用此設定，則能夠為固定資料磁碟機、作業系統磁碟機和抽取式資料磁碟機個別設定加密演算法和金鑰加密強度。 如果是固定磁碟機和作業系統磁碟機，建議您使用 XTS-AES 演算法。 如果是抽取式磁碟機，若在其他未執行 Windows 10 1511 版或更新版本的裝置上使用該磁碟機，您應該使用 AES-CBC 128 位元或 AES-CBC 256 位元。 如果磁碟機已加密或加密正在進行中，變更加密方法就沒有任何作用。 在這些情況下，會忽略這個原則設定。

  針對 BitLocker 抽取式磁碟機原則，請設定下列設定：

  - **寫入存取需要加密**  
    **預設值**：是

  - **加密方法**  
    **預設值**：AES 128 位元 XTS

- **BitLocker 系統磁碟機原則**  
  此原則的值決定 BitLocker 用於檔案系統磁碟機加密的加密強度。 企業可能想要控制加密層級以提高安全性 (AES-256 強於 AES-128)。 如果您啟用此設定，則能夠為固定資料磁碟機、作業系統磁碟機和抽取式資料磁碟機個別設定加密演算法和金鑰加密強度。 如果是固定磁碟機和作業系統磁碟機，建議您使用 XTS-AES 演算法。 如果是抽取式磁碟機，若在其他未執行 Windows 10 1511 版或更新版本的裝置上使用該磁碟機，您應該使用 AES-CBC 128 位元或 AES-CBC 256 位元。 如果磁碟機已加密或加密正在進行中，變更加密方法就沒有任何作用。 在這些情況下，會忽略這個原則設定。  

  針對 BitLocker 系統磁碟機原則，請設定下列設定：  

  - **加密方法**  
    **預設值**：AES 128 位元 XTS

## <a name="device-control"></a>裝置控制  

- **在完整掃描期間掃描抽取式磁碟機**  
  [Defender/AllowFullScanRemovableDriveScanning](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowfullscanremovabledrivescanning) - 當設定為 [是]  時，Defender 會在執行完整掃描期間在抽取式磁碟機 (例如快閃磁碟機) 中掃描惡意軟體與垃圾軟體。 Defender 防毒軟體會掃描 USB 裝置上的所有檔案，再執行 USB 裝置。

  此清單中的相關設定：*Defender/AllowFullScanOnMappedNetworkDrives*  

  **預設值**：是

- **列舉與 Kernel DMA Protection 不相容的外部裝置**  
   請參閱[原則 CSP - DmaGuard](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-dmaguard#dmaguard-deviceenumerationpolicy) 中的 *DmaGuard/DeviceEnumerationPolicy* \(英文\)

  此原則提供外部 DMA 裝置的額外安全性。 它可讓您更有效地控制與 DMA 裝置記憶體隔離和沙箱處理不相容之外部 DMA 裝置的列舉。

  只有當支援 Kernel DMA Protection 並由系統韌體啟用它時，此原則才會生效。 Kernel DMA Protection 是無法由原則或由裝置使用者控制的平台功能。 系統製造時即必須支援此功能。 

  若要檢查系統是否支援 Kernel DMA Protection，請再系統上執行 MSINFO32.exe，然後檢閱 [摘要] 頁面上的 [Kernel DMA Protection]  欄位。  

  這些選項包括： 
  -  - 登入或螢幕解除鎖定之後，允許隨時列舉具有 DMA 重新對應相容驅動程式的裝置。 具有 DMA 重新對應不相容驅動程式的裝置只有在使用者將畫面解除鎖定之後才會列舉
  -  - 將隨時列舉所有外部具 DMA 功能的 PCIe 裝置
  - *全部封鎖* - 登入或螢幕解除鎖定之後，允許隨時列舉具有 DMA 重新對應相容驅動程式的裝置。 具有 DMA 重新對應不相容驅動程式的裝置將無法隨時啟動並執行 DMA。

  **預設值**：裝置預設值

- **依裝置識別碼的硬體裝置安裝**  
  [DeviceInstallation/PreventInstallationOfMatchingDeviceIDs](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deviceinstallation#deviceinstallation-preventinstallationofmatchingdeviceids) - 使用此原則時，您可以針對 Windows 防止安裝的裝置，指定隨插即用硬體識別碼與相容識別碼的清單。 此原則設定優先於任何其他允許 Windows 安裝裝置的原則設定。 如果您啟用此原則設定 (設定為 [封鎖硬體裝置安裝]  )，Windows 會防止安裝其硬體識別碼或相容識別碼出現在您所建立清單中的裝置。 如果您在遠端桌面伺服器上啟用此原則設定，此原則會影響指定裝置從遠端桌面用戶端到遠端桌面伺服器的重新導向。 如果您停用或未設定此原則設定 (設定為 [允許硬體裝置安裝]  )，裝置可以按照其他原則設定的允許或防止來進行安裝及更新。  

  **預設**：封鎖硬體裝置安裝  

  選取 [封鎖硬體裝置安裝]  時，有下列設定可用。
  - **移除相符的硬體裝置**  
    只有在 [依裝置識別碼的硬體裝置安裝]  設定為 [封鎖硬體裝置安裝]  時，才能使用此設定。  

    **預設**：沒有任何預設設定 

  - **已封鎖的硬體裝置識別碼**  
    只有在 [依裝置識別碼的硬體裝置安裝]  設定為 [封鎖硬體裝置安裝]  時，才能使用此設定。 若要設定此設定，請展開該選項並選取 [+ 新增]  ，然後指定您要封鎖的硬體裝置識別碼。  

    **預設值**：*不會封鎖任何裝置*  

- **封鎖直接記憶體存取**  
  [DataProtection/AllowDirectMemoryAccess](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-dataprotection#dataprotection-allowdirectmemoryaccess) - 使用此原則設定來針對裝置上所有可熱插拔的 PCI 下游連接埠封鎖直接記憶體存取 (DMA)，直到使用者登入 Windows。 使用者登入後，Windows 就會列舉連接至隨插即用 PCI 連接埠的 PCI 裝置。 只要使用者鎖定電腦，在使用者再次登入之前，將會在沒有子裝置的隨插即用 PCI 連接埠上封鎖 DMA。 電腦解除鎖定時已列舉的裝置將繼續運作，直到遭拔除為止。 

  只有在啟用 BitLocker 或裝置加密時，才會強制執行此原則設定。  

  **預設值**：是


- **依安裝類別的硬體裝置安裝**  
  [DeviceInstallation/AllowInstallationOfMatchingDeviceSetupClasses](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deviceinstallation#deviceinstallation-allowinstallationofmatchingdevicesetupclasses) - 使用此原則時，您可以針對 Windows 防止安裝的裝置驅動程式，指定裝置安裝類別全域唯一識別碼 (GUID) 的清單。 此原則設定優先於任何其他允許 Windows 安裝裝置的原則設定。 如果您啟用此原則設定 (設定為 [封鎖要體裝置安裝]  )，Windows 會防止安裝或更新其裝置安裝類別 GUID 出現在您所建立清單中的裝置驅動程式。 如果您在遠端桌面伺服器上啟用此原則設定，此原則設定會影響指定裝置從遠端桌面用戶端到遠端桌面伺服器的重新導向。 如果您停用或未設定此原則設定 (設定為 [允許硬體裝置安裝]  )，Windows 可以按照其他原則設定的允許或防止來進行安裝及更新裝置。  

  **預設**：封鎖硬體裝置安裝

  選取 [封鎖硬體裝置安裝]  時，有下列設定可用。  

  - **移除相符的硬體裝置**  
    只有在 [Hardware device installation by setup classes]  \(依安裝類別安裝硬體裝置\) 設定為 [Block hardware device installation]  \(封鎖硬體裝置安裝\) 時，才能使用此設定。  
 
    **預設**：沒有任何預設設定   

  - **已封鎖的硬體裝置識別碼**  
    只有在 [Hardware device installation by setup classes] \(依安裝類別的硬體裝置安裝\) 設定為 [Block hardware device installation] \(封鎖硬體裝置安裝\) 時，才能使用此設定。 若要設定此設定，請展開該選項並選取 [+ 新增]  ，然後指定您要封鎖的硬體裝置識別碼。  
 
    **預設值**：*不會封鎖任何裝置*

## <a name="endpoint-detection-and-response"></a>端點偵測與回應  
如需詳細資訊，請參閱 Windows 文件中的 [WindowsAdvancedThreatProtection CSP](https://docs.microsoft.com/windows/client-management/mdm/windowsadvancedthreatprotection-csp) \(英文\)。  

- **加快遙測回報頻率** - *Configuration/TelemetryReportingFrequency*  

  加快 Microsoft Defender 進階威脅防護遙測回報頻率。  

  **預設值**：是

- **所有檔案的範例共用** - *Configuration/SampleSharing*  

  傳回或設定 Microsoft Defender 進階威脅防護範例共用設定參數。  

  **預設值**：是

## <a name="exploit-protection"></a>惡意探索保護  

- **惡意探索保護 XML**  
  如需詳細資訊，請參閱 Windows 文件中的[匯入、匯出及部署惡意探索保護設定](/windows/security/threat-protection/microsoft-defender-atp/import-export-exploit-protection-emet-xml) \(部分機器翻譯\)。  

  讓 IT 系統管理員得以將代表想要的系統及應用程式風險降低選項設定，推送至組織中的所有裝置。 此設定是以 XML 表示。 

  套用惡意探索保護可協助保護裝置，以防惡意程式碼利用惡意探索散播和感染。 您可以使用 Windows 安全性應用程式或 PowerShell 建立風險降低集合 (稱為設定)。 然後，您可以將此設定匯出為 XML 檔案，並在您網路上的多部電腦之間共用，以便所有檔案都有相同的風險降低設定集合。
 
  您也可以將現有的 EMET 設定 XML 檔案轉換並匯入到惡意探索保護設定 XML。

- **封鎖惡意探索保護覆寫**  
  [WindowsDefenderSecurityCenter/DisallowExploitProtectionOverride](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowsdefendersecuritycenter#windowsdefendersecuritycenter-disallowexploitprotectionoverride) – 設定為 [是]  以防止使用者變更 Windows Defender 資訊安全中心中的惡意探索保護設定區域。 若您停用或未設定此設定，本機使用者可以變更惡意探索保護設定區域。  
  **預設值**：是  

- **受控制的資料夾存取**  
  請參閱 [Defender/ControlledFolderAccessAllowedApplications](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-controlledfolderaccessallowedapplications) \(英文\) 與 [Defender/ControlledFolderAccessProtectedFolders](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-controlledfolderaccessprotectedfolders) \(英文\) 
  
   保護檔案和資料夾免於惡意應用程式未經授權的變更。

  **預設值**：稽核模式

## <a name="web--network-protection"></a>Web 與網路保護  

- **網路保護類型**  
  [Defender/EnableNetworkProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-enablenetworkprotection)  - 此原則可讓您開啟 Windows Defender 惡意探索防護中的網路保護。 網路保護是 Windows Defender 惡意探索防護的一項功能，可防止使用任何應用程式的員工存取網路釣魚詐騙、裝載入侵程式網站及網際網路上的惡意內容。 這包括防止第三方瀏覽器連線到危險的網站。  

  當設定為 [啟用]  或 [稽核模式]  時，使用者無法關閉網路保護，而且您可以使用 Windows Defender 資訊安全中心來檢視連線嘗試的相關資訊。  
 
  - [啟用]  將會封鎖使用者與應用程式，使其無法連線到危險網域。  
  - [稽核模式]  不會封鎖使用者與應用程式，使其無法連線到危險網域。  

  當設定為 [使用者定義]  時，系統不會封鎖使用者與應用程式，使其無法連線到危險網域，而且 Windows Defender 資訊安全中心不會有連線相關資訊。  

  **預設值**：稽核模式

- **Microsoft Edge 需要 SmartScreen**  
  [Browser/AllowSmartScreen](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-allowsmartscreen) - Microsoft Edge 預設會使用 Windows Defender SmartScreen (已開啟)，以保護使用者免於遭受潛在的網路釣魚詐騙和惡意軟體攻擊。 根據預設，會啟用此原則 (設定為 [是]  )，而且當啟用時，可以防止使用者關閉 Windows Defender SmartScreen。  當裝置的有效原則等於 [尚未設定] 時，使用者可以關閉 Windows Defender SmartScreen，這會讓裝置處於未受保護狀態。  

  **預設值**：是
  
- **封鎖惡意網站存取**  
  [Browser/PreventSmartScreenPromptOverride](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-preventsmartscreenpromptoverride) - 根據預設，Microsoft Edge 可讓使用者略過 (忽略) 有關潛在惡意網站的 Windows Defender SmartScreen 警告，讓使用者可以繼續前往該網站。 在啟用此原則的情況下 (設定為 [是]  )，Microsoft Edge 會防止使用者跳過該警告，而且會封鎖他們，使他們無法繼續瀏覽該網站。  

  **預設值**：是

- **封鎖未經驗證的檔案下載**  
  [Browser/PreventSmartScreenPromptOverrideForFiles](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-preventsmartscreenpromptoverrideforfiles) - 根據預設，Microsoft Edge 可讓使用者略過 (忽略) 有關潛在惡意檔案的 Windows Defender SmartScreen 警告，讓他們可以繼續下載未經驗證的檔案。 在啟用此原則的情況下 (設定為 [是]  )，使用者無法略過警告，而且無法下載未經驗證的檔案。  

  **預設值**：是

## <a name="windows-defender-anti-virus----settings-review-pending-for-this-section"></a>Windows Defender 防毒軟體    [此節的設定檢閱擱置中]

如需詳細資訊，請參閱 Windows 文件中的 [Policy CSP - Defender](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender) (原則 CSP - Defender)。

- **掃描 Microsoft 網頁瀏覽器中所載入的指令碼**  
  [Defender/AllowScriptScanning](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowscriptscanning) – 設定為 [是]  以允許 Windows Defender 指令碼掃描功能運作。  

  **預設值**：是

- **掃描內送郵件訊息**  
  [Defender/AllowEmailScanning](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowemailscanning) – 設定為 [是]  以允許 Windows Defender 掃描電子郵件。  

  **預設值**：是

- **Defender 範例提交同意類型**  
  [Defender/SubmitSamplesConsent](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-submitsamplesconsent) - 檢查 Windows Defender 中針對傳送資料的使用者同意層級。 如果已獲得必要的同意，Windows Defender 將會提交同意。 如果沒有 (而且指定了一律不再詢問使用者)，您可以啟動 UI，要求使用者同意 (當 [雲端提供的保護]  設定為 [是]*Yes* 時) 再傳送資料。  

  **預設**：自動傳送安全的範例

- **網路檢查系統 (NIS)**  
  [Defender/EnableNetworkProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-enablenetworkprotection) - 透過網路檢測系統 (NIS) 中的特徵碼封鎖偵測到的惡意流量。  
 
  **預設值**：是

- **特徵碼更新間隔 (小時)**  
  [Defender/SignatureUpdateInterval](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-signatureupdateinterval) – 以小時為單位指定裝置檢查新 Defender 特徵碼更新的頻率。  
 
  **預設**：4

- **設定已排定之掃描的低 CPU 優先順序**  
  [Defender/EnableLowCPUPriority](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-enablelowcpupriority) – 當設定為 [是]  時，掃描的 CPU 優先順序會設定為低。 當 [尚未設定]  時，不會對已排定之掃描的 CPU 優先順序進行變更。  

    **預設值**：是

- **Defender 封鎖即時監視保護**  
  [Defender/AllowOnAccessProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowonaccessprotection) – 當設定為 [是]  時，會啟用 Windows Defender 即時監視保護。  

  **預設值**：是

- **要執行的系統掃描類型**  
  [Defender/ScanParameter](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-scanparameter) - Defender 掃描類型。  

  **預設值**：快速掃描

- **掃描所有下載**  
  [Defender/AllowIOAVProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowioavprotection) - 當設定為 [是]  時，Defender 會掃描所有已下載的檔案與附件。  

  **預設值**：是

- **多少天之後刪除隔離的惡意程式碼**  
  [Defender/DaysToRetainCleanedMalware](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-daystoretaincleanedmalware) - 指定系統自動刪除隔離項目之前要保留隔離項目的天數。 當設定為零時，一律不會自動刪除隔離區中的項目。  

  **預設**：0

- **排定的掃描開始時間**  
  [Defender/ScheduleScanTime](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-schedulescantime) – 排定要讓 Defender 掃描裝置的當日時間。 
  
  此清單中的相關選項：*Defender/ScheduleScanDay*   

  **預設值**：上午 2 點

- **雲端提供的保護**  
  [Defender/AllowCloudProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowcloudprotection) – 當設定為 [是]  時，Windows Defender 會將有關它發現之任何問題的資訊傳送給 Microsoft。 Microsoft 將分析該資訊、深入了解影響您與其他客戶的問題，並提供改善的解決方案。

  當此原則設定為 [是]  時，您可以使用 [Defender sample submission consent type]  \(Defender 樣本提交同意類型\) 讓使用者可以控制是否從其裝置傳送資訊。  

  **預設值**：是

- **Defender 潛在的垃圾應用程式動作**  
  [Defender/PUAProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-puaprotection) – Windows Defender 防毒軟體可以識別並封鎖「潛在垃圾應用程式(PUA)」  ，並防止將它下載並安裝到您網路中的端點。 
 
  - 當設定為 [封鎖]  時，Windows Defender 會封鎖 PUA，而且會隨著其他威脅將其列在歷程記錄中。
  - 當設定為 [稽核]  時，Windows defender 會偵測 PUA，但不會封鎖它們。 搜尋 [事件檢視器] 中由 Windows Defender 建立的事件，即可找到有關 Windows Defender 會對其採取動作之應用程式的相關資訊。  
  - 當設定為 [裝置預設值]  時，會關閉 PUA 保護。  
 
  **預設值**：封鎖

- **Defender 雲端延長逾時**  
  [Defender/CloudExtendedTimeout](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-cloudextendedtimeout) - 指定 Windows Defender 防毒軟體在封鎖檔案前應等候雲端結果的額外時間上限。 Windows Defender 會等候的基底時間量是 10 秒。 您在這裡指定的任何額外時間 (最長 50 秒) 會加到那 10 秒。 在大部分情況下，掃描時間會少於時間上限。 延長的時間可讓雲端徹底調查可疑的檔案。  

  根據預設，延長時間值是 0 (停用)。 Intune 建議您啟用此設定，並至少多指定 20 秒。  
 
  **預設**：0

- **掃描封存檔**  
  [Defender/AllowArchiveScanning](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowarchivescanning) – 設定為 [是]   以讓 Windows Defender 掃描封存檔案。  

  **預設值**：是

- **Defender 系統掃描排程**  
  [Defender/ScheduleScanDay](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-schedulescanday) - 排定 Defender 將在哪天掃描裝置。 
 
  此清單中的相關選項：*Defender/ScheduleScanTime*

  **預設值**：使用者定義

- **行為監視**  
  [Defender/AllowBehaviorMonitoring](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowbehaviormonitoring) – 設定為 [是]  以開啟 Windows Defender 行為監視功能。 Windows Defender 行為監視感應器建於 Windows 10 中，這些感應器可以收集並處理作業系統的行為訊號，並將此感應器資料傳送至您私人獨立的 Microsoft Defender ATP 雲端執行個體。  

  **預設值**：是

- **掃描從網路資料夾中開啟的檔案**  
  [Defender/AllowScanningNetworkFiles](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowscanningnetworkfiles) – 設定為 [是]  以讓 Windows Defender 掃描網路上的檔案。 使用者將無法從唯讀檔案移除偵測到的惡意程式碼。  

  **預設值**：是

- **Defender 雲端封鎖層級**  
  [Defender/CloudBlockLevel](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-cloudblocklevel) – 使用此原則來決定 Windows Defender 防毒軟體封鎖及掃描可疑檔案的積極程度。 這些選項包括：

  - 高 - 積極地封鎖未知的檔案，同時最佳化最佳化用戶端效能 (極可能發生誤判)
  - 極高 - 積極地封鎖未知的檔案，並套用額外的保護措施 (可能會影響用戶端效能)
  - 零容錯 - 會封鎖所有未知的可執行檔

  **預設值**：尚未設定

- **即時監視**  
  [Defender/AllowRealtimeMonitoring](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowrealtimemonitoring) – 設定為 [是]  以允許 Windows Defender 即時監視。  

  **預設值**：是

- **掃描期間的 CPU 使用率限制**  
  [Defender/AvgCPULoadFactor](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-avgcpuloadfactor) – 指定 Windows Defender 在掃描期間可以使用的最大平均 CPU 使用率百分比。  

  **預設值**：50

- **在完整掃描期間掃描對應的網路磁碟機**  
  [Defender/AllowFullScanOnMappedNetworkDrives](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowfullscanonmappednetworkdrives) - 設定為 [是]  以讓 Windows Defender 掃描網路上的檔案。 使用者無法從唯讀檔案移除偵測到的惡意程式碼，

  此清單中的相關設定：*Defender/AllowScanningNetworkFiles*

  **預設值**：是

- **禁止終端使用者存取 Defender**  
  [Defender/AllowUserUIAccess](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowuseruiaccess) – 設定為 [是]  以禁止終端使用者在此裝置上存取 Windows Defender UI。  

  **預設值**：是

- **快速掃描開始時間**  
  [Defender/ScheduleQuickScanTime](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-schedulequickscantime) - 排定要讓 Defender 執行快速掃描的當日時間。  

  **預設值**：上午 2 點

## <a name="windows-defender-firewall"></a>Windows Defender 防火牆
如需詳細資訊，請參閱 Windows 文件中的[防火牆 CSP](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp) \(英文\)。

- **刪除前的安全性關聯閒置時間** - *MdmStore/Global/SaIdleTime*   
  在指定秒數過後偵測不到任何網路流量時，即刪除安全性關聯。  
  **預設值**：300

- **檔案傳輸通訊協定** - *MdmStore/Global/DisableStatefulFtp*   
  封鎖具狀態檔案傳輸通訊協定 (FTP)。  
  **預設值**：是

-   - *MdmStore/Global/EnablePacketQueue*    
  指定如何啟用接收端軟體的規模調整，處理 IPsec 通道閘道案例中加密的接收和純文字轉送。 這可確定保留封包順序。  
  **預設值**：裝置預設值

-   - *FirewallRules/FirewallRuleName/Profiles*  
  指定規則所屬設定檔：網域、私人、公用。 此值代表連結到網域之網路的設定檔。  

  可用的設定：  
  - **需要多點傳送廣播的單點傳播回應**  
    **預設值**：是

  - **來自群組原則的授權應用程式規則已合併**  
    **預設值**：是

  - **已封鎖輸入通知**  
    **預設值**：是

  - <bpt id="p1">**</bpt>Global port rules from group policy merged<ept id="p1">**</ept>  
    **預設值**：是

  - **已封鎖隱形模式**  
    **預設值**：是

  - **已啟用防火牆**  
    **預設值**：允許

  - **來自群組原則的連線安全性規則已合併**  
    **預設值**：是

  - **來自群組原則的原則規則已合併**  
    **預設值**：是

- **防火牆設定檔公用** - *FirewallRules/FirewallRuleName/Profiles*  
  指定規則所屬設定檔：網域、私人、公用。 此值代表公用網路的設定檔。 這些網路是由系統管理員在伺服器主機中分類為公用。 主機第一次連線到網路時即會進行分類。 這些網路通常位於機場、咖啡廳與其他公共場所，其中網路中的同儕節點或網路系統管理員不受信任。  

  可用的設定：

  - **已封鎖輸入連線**  
    **預設值**：是 

  - **需要多點傳送廣播的單點傳播回應**  
    **預設值**：是  

  - **需要隱形模式**  
    **預設值**：是 
 
  - **需要輸出連線**  
    **預設值**：是  

  - **來自群組原則的授權應用程式規則已合併**  
    **預設值**：是  

  - **已封鎖輸入通知**  
    **預設值**：是  

  - <bpt id="p1">**</bpt>Global port rules from group policy merged<ept id="p1">**</ept>  
    **預設值**：是

  - **已封鎖隱形模式**  
    **預設值**：是

  - **已啟用防火牆**  
    **預設值**：允許  

  - **來自群組原則的連線安全性規則已合併**  
    **預設值**：是  

  - **需要連入流量**  
    **預設值**：是

  - **來自群組原則的原則規則已合併**  
    **預設值**：是  

- **防火牆設定檔私人** - *FirewallRules/FirewallRuleName/Profiles*  
  指定規則所屬設定檔：網域、私人、公用。 此值代表私人網路的設定檔。  

  可用的設定： 

  - **已封鎖輸入連線**  
    **預設值**：是

  - **需要多點傳送廣播的單點傳播回應**  
    **預設值**：是

  - **需要隱形模式**  
    **預設值**：是

  - **需要輸出連線**  
    **預設值**：是

  - **已封鎖輸入通知**  
    **預設值**：是

  - <bpt id="p1">**</bpt>Global port rules from group policy merged<ept id="p1">**</ept>  
    **預設值**：是

  - **已封鎖隱形模式**  
    **預設值**：是  

  - **已啟用防火牆**  
    **預設值**：允許

  - **來自群組原則的授權應用程式規則未合併**  
    **預設值**：是

  - **來自群組原則的連線安全性規則已合併**  
    **預設值**：是

  - **需要連入流量**  
    **預設值**：是

  - **來自群組原則的原則規則已合併**  
    **預設值**：是  

- **防火牆預先共用金鑰編碼方法**  
  **預設值**：UTF8

- **憑證撤銷清單驗證**  
  **預設值**：裝置預設值

## <a name="windows-hello-for-business"></a>Windows Hello 企業版  

如需詳細資訊，請參閱 Windows 文件中的 [PassportForWork CSP](https://docs.microsoft.com/windows/client-management/mdm/passportforwork-csp) \(英文\)。

- **設定 Windows Hello 企業版** - *TenantId/Policies/UsePassportForWork*    
  Windows Hello 企業版是一種能取代密碼、智慧卡及虛擬智慧卡來登入 Windows 的方法。  

  - 當設定為 *[是]* 時，您會啟用此原則，且裝置會布建 Windows Hello 企業版。  
  - 當設定為 [*未*設定] 時，基準不會影響裝置的原則設定。 這表示如果裝置上的 Windows Hello 企業版已停用，它就會保持停用狀態。 如果已啟用，則會保持啟用狀態。 

  您無法透過此基準停用 Windows Hello 企業版。 您可以在設定[windows 註冊](windows-hello.md)時停用 Windows Hello 企業版，或做為身分[識別保護](identity-protection-configure.md)裝置設定檔的一部分。  

Windows Hello 企業版是一種能取代密碼、智慧卡及虛擬智慧卡來登入 Windows 的方法。  

  若您啟用或未設定此原則設定，裝置會佈建 Windows Hello 企業版。 若停用此原則設定，裝置不會為任何使用者佈建 Windows Hello 企業版。

  Intune 不支援停用 Windows Hello。 您可以改為設定原則以啟用 Windows Hello 企業版 ([是])，或不直接設定 Windows Hello directly ([尚未設定])。 若選項為尚未設定，裝置可以透過其他原則接收設定，進而啟用或停用此功能。  

  **預設值**：是  

- **PIN 中需要有小寫字母** - *TenantId/Policies/PINComplexity/LowercaseLetters*  
  **預設值**：允許  

- **PIN 中需要有特殊字元** - *TenantId/Policies/PINComplexity/SpecialCharacters*  
  **預設值**：允許  

- **PIN 中需要有大寫字母** - *TenantId/Policies/PINComplexity/UppercaseLetters*   
  **預設值**：允許  


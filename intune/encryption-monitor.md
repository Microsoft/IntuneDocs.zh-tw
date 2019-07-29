---
title: Microsoft Intune 中加密裝置的加密報表
titleSuffix: Microsoft Intune
description: 從 Microsoft Intune 入口網站檢視有關 iOS 或 Windows 裝置加密狀態的報表，以及存取 FileVault 和 BitLocker 修復金鑰。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 07/19/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: shpate
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: a04a8b9f1973479fd0695ad0e782488fdef43d10
ms.sourcegitcommit: c3a4fefbac8ff7badc42b1711b7ed2da81d1ad67
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/22/2019
ms.locfileid: "68375159"
---
# <a name="monitor-device-encryption"></a>監視裝置加密  

Microsoft Intune 加密報表是您檢視受控裝置加密狀態相關詳細資料的一個集中式位置。 您可以檢視裝置加密狀態的相關詳細資料，並找到管理裝置修復金鑰的選項。 修復金鑰可用選項取決於您所檢視的裝置類型。  

若要尋找報表，請登入 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) 並移至 [裝置設定]  ，然後在 [監視]  下方選取 [加密報表]  。  

## <a name="view-encryption-details"></a>檢視加密詳細資料  

加密報表顯示您所管理各種支援裝置的常見詳細資料。 下列各節提供有關 Intune 在報表中所顯示資訊的詳細資料。  
 
### <a name="prerequisites"></a>必要條件：  

加密報表支援在執行下列作業系統版本的裝置上進行報告：  
- macOS 10.13 或更新版本  
- Windows 1607 版或更新版本  

### <a name="report-details"></a>報表詳細資料  

[加密報表] 窗格會顯示您管理的裝置清單，以及這些裝置的整體詳細資料。 您可以從清單中選取裝置，在該裝置的 [[裝置加密狀態]](#device-encryption-status) 窗格中鑽研和檢視其他詳細資料。  

- **裝置名稱** - 裝置的名稱。  
- **OS** - 裝置平台，例如 Windows 或 macOS。  
- **OS 版本** - 裝置上的 Windows 或 macOS 版本。  
- **TPM 版本** (僅適用於 Windows 10)  - Windows 10 裝置上的信賴平台模組 (TPM) 晶片版本。  
- **加密整備** - 評估裝置整備以支援適用的加密技術，例如 BitLocker 或 FileVault 加密。 裝置可以識別為：  
  - **就緒**：裝置可以使用 MDM 原則進行加密，該原則需要裝置符合下列需求：  
    
    **針對 macOS 裝置**：  
    - MacOS 10.13 版或更新版本  
    
    **Windows 10 裝置**：  
    - 「商務版」  、「企業版」  、「教育版」  1703 版或更新版本，或是「專業版」  1809 版或更新版本  
    - 裝置必須具有 TPM 晶片  
    
    如需詳細資訊，請參閱 Windows 文件中的 [BitLocker configuration service provider (CSP)](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp) (BitLocker 設定服務提供者 (CSP))。  

  - **未就緒**：裝置沒有完整的加密功能，但仍支援加密。 例如，Windows 裝置可能是由使用者以手動方式進行加密，或透過將群組原則設定為允許在沒有 TMP 的情況下加密來進行加密。
  - **不適用**：資訊不足，無法分類此裝置。  

- **加密狀態** - OS 磁碟機是否已加密。  

- **使用者主體名稱** - 裝置的主要使用者。  

### <a name="device-encryption-status"></a>裝置加密狀態  

當您從 [加密報表] 中選取裝置時，Intune 會顯示 [裝置加密狀態]  窗格。 此窗格提供下列詳細資料：  

- **裝置名稱** - 您要檢視的裝置名稱。  

- **加密整備** - 評估裝置整備以支援透過 MDM 原則進行加密。  
  
  例如：當 Windows 10 裝置的整備狀態為 [未就緒]  時，可能仍然支援加密。 若要指定 [就緒]  狀態，Windows 10 裝置必須具有 TPM 晶片。 不需要 TPM 晶片，也能支援加密。 (如需詳細資料，請參閱上一節的＜加密整備＞)。  

- **加密狀態** - OS 磁碟機是否已加密。 Intune 可能需要最多 24 小時的時間，才能報告裝置的加密狀態或該狀態的變更。  

- **設定檔** - 套用到此裝置並設定下列值的「裝置組態」  設定檔清單：  

  - macOS：
    - 設定檔類型 = *Endpoint Protection*  
    - [設定] > [FileVault] > [FileVault] = [啟用] 

  - Windows 10：
    - 設定檔類型 = *Endpoint Protection*  
    - [設定] > [Windows 加密] > [加密裝置] = [需要]   

  如果「設定檔狀態摘要」  指出問題，您可以使用設定檔清單來找出要檢閱的個別原則。  

- **設定檔狀態摘要** - 套用到此裝置的設定檔摘要。 此摘要表示適用設定檔中最不利的條件。 例如，如果多個適用設定檔中只有一個產生錯誤，則「設定檔狀態摘要」  會顯示「錯誤」  。  

- **狀態詳細資料** - 裝置加密狀態的相關進階詳細資料。  
  > [!NOTE]
  > FileVault 的支援在幾天後 7 月版完成推出之前會受到限制。 推出完成之前，macOS 的裝置狀態詳細資料和裝置加密詳細資料可能無法在加密報表中正確顯示。

  > [!IMPORTANT]  
  > 若是 Windows 10 裝置，Intune 只會針對執行「Windows 10 2019 年 4 月更新」  或更新版本的裝置，顯示其「狀態詳細資料」  。  
  
  此欄位會顯示可能偵測到的每個適用錯誤資訊。 您可以使用這項資訊來了解裝置為何尚未準備好加密。  

  下列是 Intune 可能報告的狀態詳細資料範例：  
  
  **macOS**：
  - 目前無法安裝設定檔，因為我們正在等候某個必要條件。  
 
    *考量：這項結果不一定代表錯誤狀況，而是暫時性狀態，這可能是由於必須先設定修復金鑰委付，才能將加密要求傳送到裝置的裝置時機所造成。這也可能表示裝置仍處於鎖定狀態，或最近尚未使用 Intune 簽入。最後，由於 FileVault 加密在裝置插入 (充電) 之前不會啟動，所以使用者可能會收到尚未加密裝置的修復金鑰*。  

  - 已安裝 FileVault 設定檔，但未在裝置上啟用 FileVault。  
 
    *考量：可能是使用者在收到加密要求之後尚未登出，必須登出，FileVault 才能加密裝置；也可能是使用者已手動解密裝置。Intune 無法防止使用者解密其裝置。*  

  - 使用者已啟用 FileVault，因此 Intune 無法管理其修復。  
 
    *考量：Intune 無法在已加密的裝置上設定 FileVault。相反地，使用者必須先手動解密其裝置，才能透過裝置設定原則和 Intune 管理裝置*。 
 
  - FileVault 需要使用者在 MacOS Catalina 和更新版本中核准其管理設定檔。  
 
    *考量：從 MacOS 10.15 版 (Catalina) 開始，使用者核准的註冊設定可能會導致使用者必須手動核准 FileVault 加密。如需詳細資訊，請參閱 Intune 文件中的[使用者核准的註冊](macos-enroll.md)* 。  

  - iOS 裝置傳回 NotNow (已鎖定)。  

    *考量：裝置目前已鎖定，因此 Intune 無法啟動委付或加密程序。將裝置解除鎖定之後，即可繼續進行程序*。  

  **Windows 10**：  
  - BitLocker 原則需要使用者同意，才能啟動 [BitLocker 磁碟機加密精靈] 開始加密 OS 磁碟區，但使用者未同意。  
  
  - OS 磁碟區的加密方法不符合 BitLocker 原則。  
  
  - BitLocker 原則需要 TPM 保護裝置才能保護 OS 磁碟區，但未使用 TPM。  
  
  - BitLocker 原則需要 OS 磁碟區有僅限 TPM 的保護裝置，但未使用 TPM 保護。  
  
  - BitLocker 原則需要 OS 磁碟區有 TPM+PIN 保護，但未使用 TPM+PIN 保護裝置。  
  
  - BitLocker 原則需要 OS 磁碟區有 TPM+啟動金鑰保護，但未使用 TPM+啟動金鑰保護裝置。  
  
  - BitLocker 原則需要 OS 磁碟區有 TPM+PIN+啟動金鑰保護，但未使用 TPM+PIN+啟動金鑰保護裝置。  
  
  - OS 磁碟區未受保護。  
  
  - 修復金鑰備份失敗。  
  
  - 固定磁碟機未受保護。  
  
  - 固定磁碟機的加密方法不符合 BitLocker 原則。  
  
  - 若要加密磁碟機，BitLocker 原則需要使用者以系統管理員身分登入；如果裝置已加入 Azure AD，則 AllowStandardUserEncryption 原則必須設定為 1。  
  
  - 未設定 Windows 修復環境 (WinRE)。  
  
  - BitLocker 無法使用 TPM，因為它不存在、已設定為無法在登錄中使用，或 OS 位在抽取式磁碟機上。  
  
  - TPM 尚未備妥供 BitLocker 使用。  
  
  - 網路無法使用，但修復金鑰備份需要網路。  

## <a name="export-report-details"></a>匯出報表詳細資料 
檢視 [加密報表] 窗格時，您可以選取 [匯出]  來建立報表詳細資料的 *.csv* 檔案下載。  此報表包含 [加密報表]  窗格中的整體詳細資料，以及您所管理每部裝置的 [裝置加密狀態]  詳細資料。   
 
  
![匯出詳細資料](./media/encryption-monitor/export.png) 
 
此報表可用於找出裝置群組的問題。 例如，您可以使用報表來找出報告「使用者已啟用 FileVault」  的所有 macOS 裝置清單，這表示必須先手動解密裝置，Intune 才能開始管理其 FileVault 設定。  
 
## <a name="filevault-recovery-keys"></a>FileVault 修復金鑰   
當 Intune 第一次使用 FileVault 加密 macOS 裝置時，會建立個人修復金鑰。 加密後，裝置只會向終端使用者顯示一次個人金鑰。  
 
針對受控裝置，Intune 可以委付個人修復金鑰的複本。 金鑰委付可讓 Intune 管理員輪替金鑰以協助保護裝置，並讓使用者復原遺失或輪替的個人修復金鑰。  
 
Intune 支援輪替和復原個人修復金鑰的多個選項。 輪替金鑰的一個原因是如果目前的個人金鑰遺失則視為風險。  
 
> [!IMPORTANT]  
>  由使用者 (而非 Intune) 加密的裝置無法由 Intune 管理。 這表示 Intune 無法委付這些裝置的個人修復，也無法管理修復金鑰的輪替。  使用者必須先解密其裝置，再讓 Intune 加密裝置，Intune 才能管理 FileVault 和裝置的修復金鑰。  

### <a name="rotate-recovery-keys"></a>輪替修復金鑰  

- **自動輪替**：身為管理員，您可以將 FileVault 設定中的個人修復金鑰輪替，設定為自動定期產生新的修復金鑰。  為裝置產生新的金鑰之後，不會向使用者顯示該金鑰。 相反地，使用者必須向管理員或使用公司入口網站應用程式取得金鑰。  

- **手動輪替**：身為管理員，您可以檢視由 Intune 管理並使用 FileVault 加密的裝置資訊。 然後，您可以選擇手動輪替公司裝置的修復金鑰。 您無法輪替個人裝置的修復金鑰。  

  若要輪替修復金鑰： 
  1. 登入 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)，移至 [裝置] ****  ，然後在 [管理] 下選取 [所有裝置] **** 。  
  2. 從裝置清單中選取您想要輪替其金鑰的加密裝置。 然後在 [監視] 下選取 [修復金鑰] **** 。  
  3. 在 [修復金鑰] 窗格中，選取 [輪替 FileVault 修復金鑰]  。  
  
     下一次裝置使用 Intune 簽入時，即會輪替個人金鑰。 如有需要，終端使用者可以透過公司入口網站取得新的金鑰。 


### <a name="recover-recovery-keys"></a>復原修復金鑰  
- **管理員**：管理員無法檢視 FileVault 加密裝置的個人修復金鑰。  

- **終端使用者**：終端使用者可以從任何裝置使用公司入口網站來檢視其任何受控裝置的目前個人修復金鑰。 您無法從公司入口網站應用程式檢視修復金鑰。  

 
  若要檢視修復金鑰：  
  1. 從任何裝置登入「Intune 公司入口網站」  網站。  
  2. 在入口網站中，移至 [裝置]  ，然後選取使用 FileVault 加密的 macOS 裝置。  
  3. 選取 [取得修復金鑰]  。 目前的修復金鑰會隨即顯示。  
  
     在 iPhone 上，您必須選取「三個」  點，[取得修復金鑰]  選項才會顯示。  

## <a name="bitlocker-recovery-keys"></a>BitLocker 修復金鑰  

Intune 可讓您從 Intune 入口網站內存取 Azure AD 刀鋒視窗中的 BitLocker，以便檢視 Windows 10 裝置的 BitLocker 金鑰識別碼和修復金鑰。  為了能夠存取，裝置必須將其金鑰委付給 Azure AD。 
1. 登入 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)，移至 [裝置]  ，然後在 [管理]  下選取 [所有裝置]  。  

2. 從清單中選取裝置，然後在 [監視]  下方選取 [修復金鑰]  。  
  
當 Azure AD 中有可用的金鑰時，會提供下列資訊：
- BitLocker 金鑰識別碼  
- BitLocker 修復金鑰  
- 磁碟機類型  

當金鑰不在 Azure AD 時，Intune 會顯示 [找不到此裝置的 BitLocker 金鑰]  。  

您可以使用 [BitLocker 設定服務提供者](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp) (CSP) 來取得 BitLocker 的資訊。 Windows 10 1703 版和更新版本，以及 Windows 10 專業版 1809 版和更新版本支援 BitLocker CSP。  

## <a name="next-steps"></a>後續步驟  

建立[裝置合規性](compliance-policy-create-windows.md)政策。
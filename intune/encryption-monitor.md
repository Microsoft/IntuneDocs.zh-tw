---
title: Microsoft Intune 中的加密報表和 BitLocker 金鑰
titleSuffix: Microsoft Intune
description: 從 Microsoft Intune 入口網站檢視有關裝置加密狀態的報表，以及存取 BitLocker 修復金鑰。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: shpate
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: b4c7e4b2d35eb2662ca74660e2133dcd2c89f0a1
ms.sourcegitcommit: 7c251948811b8b817e9fe590b77f23aed95b2d4e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "67883358"
---
# <a name="monitor-bitlocker-and-device-encryption"></a>監視 BitLocker 和裝置加密  
Intune 提供集中式位置來識別 Windows 10 裝置的加密狀態，並協助您從裝置存取 BitLocker 的重要資訊 (位於 Azure Active Directory (Azure AD) 中)。  

- [加密報表](#encryption-report)提供關於裝置加密狀態和整備程度的詳細資料。 這些報表詳細資料可協助您找出導致您所要保護裝置無法成功加密的問題。  
- 從 Intune 入口網站內[檢視 BitLocker 詳細資料](#bitlocker-recovery-keys)，例如裝置的金鑰識別碼和修復金鑰。  

## <a name="encryption-report"></a>加密報表
您可以使用加密報表，來檢視關於 Windows 10 裝置加密狀態的詳細資料。  

若要尋找報表，請登入 [Intune](https://aka.ms/intuneportal) 並移至 [裝置設定]  ，然後在 [監視]  下方選取 [加密報表]  。  

### <a name="prerequisites"></a>必要條件：
裝置必須執行 Windows 1607 版或更新版本，才能出現在加密報表中。  

### <a name="report-details"></a>報表詳細資料
報表會顯示 Windows 10 裝置的**裝置名稱**，以及每部裝置的整體詳細資料，包括：  
- **OS 版本** - Windows 的版本。  
- **TPM 版本** - 裝置上信賴平台模組 (TPM) 晶片的版本。  
- **加密整備** - 評估裝置整備以支援 BitLocker 加密。 裝置可以識別為：
  - **就緒**：裝置可以使用 MDM 原則進行加密，該原則需要裝置具有 TPM 並符合下列 Windows 10 版本和 SKU 需求：
    - 商務版、企業版、教育版 1703 版或更新版本
    - 專業版 1809 版或更新版本  
  
    如需詳細資訊，請參閱 Windows 文件中的 [BitLocker configuration service provider (CSP)](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp) (BitLocker 設定服務提供者 (CSP))。  

  - **未就緒**：裝置沒有完整的加密功能，但仍支援加密。 例如，裝置可能是由使用者以手動方式進行加密，或透過將群組原則設定為允許在沒有 TMP 的情況下加密來進行加密。
  - **不適用**：資訊不足，無法分類此裝置。  

- **加密狀態** - OS 磁碟機是否已加密。 


### <a name="device-encryption-status"></a>裝置加密狀態
當您選取裝置時，Intune 會顯示 [裝置加密狀態]  窗格。

此窗格提供下列詳細資料：  
- **裝置名稱** - 您要檢視的裝置名稱。  
- **加密整備** - 評估裝置整備以支援 BitLocker 加密。 裝置可能會有 [已加密]  的加密狀態，但由於缺少 TPM 而導致其加密整備為 [未就緒]  (如需詳細資料，請參閱上一節的＜加密整備＞)。
- **加密狀態** - OS 磁碟機是否已加密。 針對 Intune，可能需要 24 小時，才會開始報告裝置加密狀態或該狀態的變更。  
- **設定檔** - 套用到此裝置並包含下列設定檔類型和設定的「裝置設定」  設定檔清單：  
  - 設定檔類型 = *Endpoint Protection*  
  - [設定] > [Windows 加密] > [加密裝置] = [需要]   

  如果設定檔狀態摘要指出問題，則可以使用此清單來尋找要檢閱的個別原則。  

- **設定檔狀態摘要** - 套用到此裝置的設定檔摘要。 此摘要表示所有適用設定檔中最不利的條件。 例如，如果某個設定檔產生錯誤，則 [設定檔狀態摘要] 會顯示「錯誤」  。  
- **狀態詳細資料** - 裝置加密狀態的相關進階詳細資料。 
  > [!NOTE]  
  > Intune 只會針對執行「Windows 10 2019 年 4 月更新」  或更新版本的裝置，顯示其「狀態詳細資料」  。
  
  此欄位會顯示可能偵測到的每個適用錯誤資訊。 您可以使用這項資訊來了解裝置為何尚未準備好加密。  

  下列是 Intune 可能報告的狀態詳細資料範例：  

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
  - BitLocker 無法使用 TPM，因為它不存在、已設定為無法在登錄中使用，或 OS 位於抽取式磁碟機。  
  - TPM 尚未備妥供 BitLocker 使用。  
  - 網路無法使用，但修復金鑰備份需要網路。  

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
為 Windows 10 裝置建立[裝置合規性](compliance-policy-create-windows.md)政策，以設定 BitLocker 和加密。

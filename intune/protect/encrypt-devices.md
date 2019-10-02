---
title: 使用受平台支援的加密方法，在 Microsoft Intune 中加密裝置
titleSuffix: Microsoft Intune
description: 使用內建的加密方法 (例如 BitLocker 或 FileVault) 來加密裝置，並從 Intune 入口網站管理這些加密裝置的修復金鑰。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 08/02/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: annovich
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: ad995a4b8b67a2ff7e3604f899fdbeebc2bad8cc
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2019
ms.locfileid: "71721392"
---
# <a name="use-device-encryption-with-intune"></a>搭配 Intune 使用裝置加密  

使用 Intune 來管理裝置的內建磁碟或磁碟機加密，以保護您裝置上的資料。  

將磁碟加密設定為裝置設定檔的一部分以取得 Endpoint Protection。 Intune 支援下列平台與加密技術：  
- macOS：FileVault   
- Windows 10 及更新版本：BitLocker  

Intune 也提供內建的[加密報告](encryption-monitor.md)，該報告會提供裝置加密狀態的詳細資料，涵蓋您的所有受控裝置。  

## <a name="filevault-encryption-for-macos"></a>MacOS 的 FileVault 加密  

使用 Intune 在執行 macOS 的裝置上設定 FileVault 磁碟加密。 然後，使用 Intune 加密報告來檢視這些裝置的加密詳細資料，並管理 FileVault 加密裝置的修復金鑰。  

FileVault 是隨附於 macOS 的完整磁碟加密程式。 您可以使用 Intune，在執行 **macOS 10.13 或更新版本**的裝置上設定 FileVault。  

若要設定 FileVault，請針對 macOS 平台建立 Endpoint Protection 的[裝置組態設定檔](../configuration/device-profile-create.md)。 FileVault 設定是 macOS Endpoint Protection 其中一項可用的設定類別。  

當您使用 FileVault 建立加密裝置的原則後，原則會以兩階段套用至裝置。 首先，裝置已準備好讓 Intune 擷取和備份修復金鑰。 這稱為委付。 委付金鑰之後，磁碟加密就可以啟動。

![FileVault 設定](./media/encrypt-devices/filevault-settings.png)

如需可讓您使用 Intune 來管理的 FileVault 設定詳細資料，請參閱適用於 macOS Endpoint Protection 設定的 Intune 文章中 [FileVault](endpoint-protection-macos.md#filevault)。  

### <a name="how-to-configure-macos-filevault"></a>如何設定 macOS FileVault 

1. 登入 [[Intune]](https://go.microsoft.com/fwlink/?linkid=2090973) 並前往 [裝置設定]   > [設定檔]   > [建立設定檔]  。  

2. 設定下列選項：  

   - 平台：macOS  
   - 設定檔類型：Endpoint Protection  

3. 選取 [設定]   > [FileVault]  。  

4. 針對 [FileVault]  ，選取 [啟用]  。  

5. 針對 [修復金鑰類型]  ，只支援 [個人金鑰]  。  

   請考慮新增一則訊息來協助引導終端使用者擷取其裝置的修復金鑰。 當您使用個人修復金鑰輪替的設定時，這項資訊對您的終端使用者會很有幫助，其可以自動為裝置定期產生新的修復金鑰。  

   例如：若要擷取遺失或最近輪替的修復金鑰，請從任何裝置登入 Intune 公司入口網站。 在入口網站中，前往 [裝置]  並選取已啟用 FileVault 的裝置，然後選取 [取得修復金鑰]  。 目前的修復金鑰會隨即顯示。  

6. 完成其餘 [FileVault 設定](endpoint-protection-macos.md#filevault)以符合您的商務需求，然後選取 [確定]  。  

   > [!IMPORTANT]  
   > 將 [停用登出時的提示]  設定設為 [啟用]  時，有一個已知問題。 當設為 [啟用]  時，[允許略過的次數]  設定必須設為一個值，而不得設為 [未設定]  。 如果設為 [未設定]  ，設定檔就會在裝置上失敗。 在此情況下，裝置會將其 [設定檔狀態摘要]  回報成 [錯誤]  ，且沒有進一步詳細資料。
   > 
   > 當 [停用登出時的提示]  設為 [未設定]  時，[允許略過的次數]  可以是 [未設定]  或有某個值。  
   > 
   > 在未來的更新中將會解決此問題。 

7. 完成其他組態設定，然後儲存設定檔。  

### <a name="manage-filevault"></a>管理 FileVault  

在 Intune 使用 FileVault 來加密 macOS 裝置之後，您可以在檢視 Intune [加密報告](encryption-monitor.md)時檢視並管理 FileVault 復原金鑰。  

在 Intune 使用 FileVault 來加密 macOS 裝置之後，您可以從任何裝置上的 Web 公司入口網站查看該裝置的個人修復金鑰。 在 Web 公司入口網站中，選擇已加密的 macOS 裝置，然後選擇 [取得修復金鑰] 作為遠端裝置動作。 

## <a name="bitlocker-encryption-for-windows-10"></a>適用於 Windows 10 的 BitLocker 加密  

使用 Intune 在執行 Windows 10 的裝置上設定 BitLocker 磁碟機加密。 接著，使用 Intune 加密報告來檢視這些裝置的加密詳細資料。 您也可以從裝置存取 BitLocker 的重要資訊，如同在 Azure Active Directory (Azure AD) 中找到的。  

BitLocker 適用於執行 **Windows 10 或更新版本**的裝置。  

當您針對 Windows 10 或更新版本平台建立 Endpoint Protection 的[裝置組態設定檔](../configuration/device-profile-create.md)時，請設定 BitLocker。 BitLocker 設定位於 Windows 10 Endpoint Protection 的 Windows 加密設定類別中。    

![Bitlocker 設定](./media/encrypt-devices/bitlocker-settings.png) 

### <a name="how-to-configure-windows-10-bitlocker"></a>如何設定 Windows 10 BitLocker  

1. 登入 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) 並前往 [裝置設定] > [設定檔] > [建立設定檔]。  

2. 設定下列選項：  
   - 平台：Windows 10 及更新版本  
   - 設定檔類型：Endpoint Protection  

3. 選取 [設定]   > [Windows 加密]  。

4. 完成 BitLocker 設定以符合您的商務需求，然後選取 [確定]  。  

5. 完成其他組態設定，然後儲存設定檔。  

### <a name="manage-bitlocker"></a>管理 BitLocker  

在 Intune 使用 BitLocker 來加密 Windows 10 裝置之後，您可以在檢視 Intune [加密報告](encryption-monitor.md)時檢視並擷取 BitLocker 修復金鑰。  

## <a name="next-steps"></a>後續步驟  

建立[裝置合規性](compliance-policy-create-windows.md)政策  

使用加密報告來管理：  
- [BitLocker 修復金鑰](encryption-monitor.md#bitlocker-recovery-keys)
- [FileVault 修復金鑰](encryption-monitor.md#filevault-recovery-keys)

針對下列項目，檢閱您可以使用 Intune 來設定的加密設定：  
- [BitLocker](endpoint-protection-windows-10.md#windows-encryption)  
- [FileVault](endpoint-protection-macos.md#filevault)  
 
 

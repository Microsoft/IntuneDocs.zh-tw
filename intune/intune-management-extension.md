---
title: 在 Microsoft Intune 中新增適用於 Windows 10 裝置的 PowerShell 指令碼 - Azure | Microsoft Docs
description: 新增 PowerShell 指令碼、將指令碼原則指派給 Azure Active Directory 群組、使用報告來監視指令碼，以及查看刪除您在 Microsoft Intune 的 Windows 10 裝置上所新增之指令碼的步驟。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 05/30/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 768b6f08-3eff-4551-b139-095b3cfd1f89
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: af80dd180e8fdbaeb633bdffaad90ccdf02d5380
ms.sourcegitcommit: 604b29c480b24270b5debc3e5f3141c8149ee6ed
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2018
ms.locfileid: "49959565"
---
# <a name="manage-powershell-scripts-in-intune-for-windows-10-devices"></a>在 Intune 中管理適用於 Windows 10 裝置的 PowerShell 指令碼
Intune 管理延伸模組可讓您在 Intune 中上傳 PowerShell 指令碼，以便在 Windows 10 裝置上執行。 管理延伸模組可補充 Windows 10 的行動裝置管理 (MDM) 功能，讓您更輕鬆地轉移至新式管理。

## <a name="moving-to-modern-management"></a>轉移至新式管理
終端使用者運算正在歷經數位轉型。 典型的傳統 IT 著重於單一裝置平台、公司擁有的裝置、在辦公室工作的使用者，以及各種手動且反動的 IT 程序。 然而，新式工作場所可讓使用者和企業擁有多種裝置平台，允許使用者在任何地方工作，並提供自動且主動的 IT 程序。 

MDM 服務 (例如 Microsoft Intune) 可以使用 MDM 通訊協定管理 Windows 10 裝置。 內建的 Windows 10 管理用戶端能夠與 Intune 進行通訊，進而執行企業管理工作。 它可協助您在 Windows 10 裝置上實現新式管理。 不過，Windows 10 MDM 目前並未提供某些您可能需要的功能，例如進階裝置設定、疑難排解和傳統 Win32 應用程式管理。 如需這些功能，您可以在 Windows 10 裝置上執行 Intune 軟體用戶端。 如此一來，就無法使用 Windows 10 MDM 提供的新功能。 [比較 Intune 軟體用戶端和 Windows 10 MDM 之間的差異](https://docs.microsoft.com/intune-classic/deploy-use/pc-management-comparison)。

Intune 管理延伸模組可補充內建的 Windows 10 MDM 功能。 您可以建立要在 Windows 10 裝置上執行的 PowerShell 指令碼，以提供您所需要的功能。 例如，您可以建立在 Windows 10 裝置上安裝傳統 Win32 應用程式的 PowerShell 指令碼、將指令碼上傳至 Intune、將指令碼指派給 Azure Active Directory (AD) 群組，以及在 Windows 10 裝置上執行指令碼。 然後，您可以監視指令碼在 Windows 10 裝置上從開始到完成的執行狀態。

## <a name="prerequisites"></a>必要條件
Intune 管理延伸模組具有下列必要條件：
- 裝置必須加入 Azure AD。 Intune 管理延伸模組支援加入 Azure Active Directory、加入混合網域及註冊共同管理的 Windows 裝置。
- 裝置必須執行 Windows 10 版本 1607 或更新版本。
- 必須[在 Azure AD 中啟用](https://docs.microsoft.com/intune/windows-enroll#enable-windows-10-automatic-enrollment)自動 MDM 註冊，而且裝置必須向 Intune 自動註冊。

## <a name="create-a-powershell-script-policy"></a>建立 PowerShell 指令碼原則 
1. 登入 [Azure 入口網站](https://portal.azure.com)。
2. 選取 [All services] (所有服務)，篩選 [Intune]，然後選取 [Microsoft Intune]。
3. 選取 [裝置設定] > [PowerShell 指令碼] > [新增]。
4. 為 PowerShell 指令碼輸入 [名稱] 和 [描述]。 對於 [指令碼位置]，瀏覽至 PowerShell 指令碼。 指令碼的大小必須小於 200KB (ASCII) 或 100KB (Unicode)。
5. 選擇 **[設定]**。 然後選擇要在裝置上 ([是]) 或系統內容 ([否]) 上執行包含使用者認證的指令碼。 根據預設，會在系統內容中執行指令碼。 除非需要在系統內容中執行指令碼，否則請選取 [是]。 
  ![新增 PowerShell 指令碼窗格](./media/mgmt-extension-add-script.png)
6. 選擇指令碼是否必須由信任的發行者簽署 ([是])。 根據預設，指令碼不需要簽署。 
7. 選取 [確定]，然後選取 [建立] 以儲存您的指令碼。

## <a name="assign-a-powershell-script-policy"></a>指派 PowerShell 指令碼原則
1. 在 [PowerShell 指令碼] 中，選取要指派的指令碼，然後選擇 [管理] > [指派]。
  ![新增 PowerShell 指令碼窗格](./media/mgmt-extension-assignments.png)
 
2. 選擇 [選取群組] 列出可用的 Azure AD 群組。 
3. 選取包含其裝置接收指令碼之使用者的一或多個群組。 [選取] 以將原則指派給選取的群組。

> [!NOTE]
> - 無法將 PowerShell 指令碼套用至電腦群組。
> - 只有當 Azure Active Directory (AD) 使用者登入裝置時，才會在裝置上執行 PowerShell 指令碼。

Intune 管理延伸模組每小時會與 Intune 進行同步處理一次。 將原則指派給 Azure AD 群組之後，即會執行 PowerShell 指令碼，並報告執行結果。 
 
## <a name="monitor-run-status-for-powershell-scripts"></a>監視 PowerShell 指令碼的執行狀態
您可以在 Azure 入口網站中，監視使用者和裝置之 PowerShell 指令碼的執行狀態。

在 [PowerShell 指令碼] 中，選取要監視的指令碼，然後選擇 [監視]，再選擇下列其中一種報表：
   - **裝置狀態**
   - **使用者狀態**

## <a name="delete-a-powershell-script"></a>刪除 PowerShell 指令碼
在 [PowerShell 指令碼] 中，以滑鼠右鍵按一下指令碼，然後選取 [刪除]。

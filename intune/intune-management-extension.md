---
title: 在 Microsoft Intune 中新增適用於 Windows 10 裝置的 PowerShell 指令碼 - Azure | Microsoft Docs
description: 新增 PowerShell 指令碼、將指令碼原則指派給 Azure Active Directory 群組、使用報告來監視指令碼，以及查看刪除您在 Microsoft Intune 的 Windows 10 裝置上所新增之指令碼的步驟。 另請參閱一些常見問題和解決方式。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/03/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 768b6f08-3eff-4551-b139-095b3cfd1f89
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0d0594c9f14b9d18c597de9ca37826a669dde5f3
ms.sourcegitcommit: e262b0ad8df610e25eb9421b9ebc2673bcf1020e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2019
ms.locfileid: "55986870"
---
# <a name="manage-powershell-scripts-in-intune-for-windows-10-devices"></a>在 Intune 中管理適用於 Windows 10 裝置的 PowerShell 指令碼

使用 Intune 管理延伸模組在 Intune 中上傳 PowerShell 指令碼，以便在 Windows 10 裝置上執行。 管理延伸模組可增強 Windows 10 的行動裝置管理 (MDM)，可更輕鬆地轉移至新式管理。

## <a name="moving-to-modern-management"></a>轉移至新式管理

終端使用者運算正在歷經數位轉型。 典型的傳統 IT 著重於單一裝置平台、公司擁有的裝置、在辦公室工作的使用者，以及各種手動且反動的 IT 程序。 新式工作場所可使用使用者和企業擁有的多種平台，允許使用者在任何地方工作，並提供自動且主動的 IT 程序。

MDM 服務 (例如 Microsoft Intune) 可以管理執行 Windows 10 的行動裝置及桌面裝置。 內建的 Windows 10 管理用戶端可與 Intune 進行通訊，進而執行企業管理工作。 Windows 10 MDM 目前並未提供某些您可能需要的工作，例如進階裝置設定、疑難排解和傳統 Win32 應用程式管理。 如需這些功能，您可以在 Windows 10 裝置上執行 Intune 軟體用戶端。 [比較作為電腦或行動裝置來管理 Windows 電腦](pc-management-comparison.md)是絕佳的資源。

Intune 管理延伸模組可補充內建的 Windows 10 MDM 功能。 您可以建立要在 Windows 10 裝置上執行的 PowerShell 指令碼。 例如，您可以建立安裝傳統 Win32 應用程式的 PowerShell 指令碼、將指令碼上傳至 Intune、將指令碼指派給 Azure Active Directory (AD) 群組，並執行指令碼。 然後，您可以監視指令碼從開始到完成的執行狀態。

## <a name="prerequisites"></a>必要條件

Intune 管理延伸模組具有下列必要條件：

- 裝置必須加入或註冊到 Azure AD，並設定 Azure AD [向 Intune 自動註冊](windows-enroll.md#enable-windows-10-automatic-enrollment)。 Intune 管理延伸模組支援加入 Azure AD、加入混合網域及註冊共同管理的 Windows 裝置。
- 裝置必須執行 Windows 10 版本 1607 或更新版本。
- 將 PowerShell 指令碼或 Win32 應用程式部署至使用者或裝置安全性群組時，將安裝 Intune 管理延伸模組代理程式。

## <a name="create-a-powershell-script-policy"></a>建立 PowerShell 指令碼原則 

1. 在 [Azure 入口網站](https://portal.azure.com)中，選取 [所有服務] > 篩選 [Intune] > 選取 [Microsoft Intune]。
2. 選取 [裝置設定] > [PowerShell 指令碼] > [新增]。
3. 為 PowerShell 指令碼輸入 [名稱] 和 [描述]。 對於 [指令碼位置]，瀏覽至 PowerShell 指令碼。 指令碼的大小不得大於 200 KB。
4. 選擇 **[設定]**。 然後選擇要在裝置上 ([是]) 或系統內容 ([否]) 上執行包含使用者認證的指令碼。 根據預設，會在系統內容中執行指令碼。 除非需要在系統內容中執行指令碼，否則請選取 [是]。 
  ![新增 PowerShell 指令碼窗格](./media/mgmt-extension-add-script.png)
5. 選擇指令碼是否必須由信任的發行者簽署 ([是])。 根據預設，指令碼不需要簽署。 
6. 選取 [確定]，然後選取 [建立] 以儲存您的指令碼。

## <a name="assign-a-powershell-script-policy"></a>指派 PowerShell 指令碼原則

1. 在 [PowerShell 指令碼] 中，選取要指派的指令碼，然後選擇 [管理] > [指派]。

    ![新增 PowerShell 指令碼窗格](./media/mgmt-extension-assignments.png)

2. 選擇 [選取群組] 列出可用的 Azure AD 群組。 
3. 選取包含其裝置接收指令碼之使用者的一或多個群組。 [選取] 以將原則指派給選取的群組。

> [!NOTE]
> - 終端使用者不需要登入裝置來執行 PowerShell 指令碼。
> - Intune 中的 PowerShell 指令碼可以鎖定至 Azure AD 裝置安全性群組。
> - Intune 中的 PowerShell 指令碼可以鎖定至 Azure AD 使用者安全性群組。

Intune 管理延伸模組用戶端每小時會檢查 Intune 一次。 將原則指派給 Azure AD 群組之後，即會執行 PowerShell 指令碼，並報告執行結果。

## <a name="monitor-run-status-for-powershell-scripts"></a>監視 PowerShell 指令碼的執行狀態

您可以在 Azure 入口網站中，監視使用者和裝置之 PowerShell 指令碼的執行狀態。

在 [PowerShell 指令碼] 中，選取要監視的指令碼，然後選擇 [監視]，再選擇下列其中一種報表：

- **裝置狀態**
- **使用者狀態**

## <a name="troubleshoot-powershell-scripts"></a>對 PowerShell 指令碼進行疑難排解

用戶端電腦上的代理程式記錄通常位於 `\ProgramData\Microsoft\IntuneManagementExtension\Logs`。 您可以使用 [CMTrace.exe](https://docs.microsoft.com/sccm/core/support/tools) 來檢視這些記錄檔。 

![代理程式記錄的螢幕擷取畫面](./media/apps-win32-app-10.png)  

## <a name="delete-a-powershell-script"></a>刪除 PowerShell 指令碼

在 [PowerShell 指令碼] 中，以滑鼠右鍵按一下指令碼，然後選取 [刪除]。

## <a name="common-issues-and-resolutions"></a>常見問題和解決方式

PowerShell 指令碼不會在每次登入時執行。 它們僅在重新開機之後，或者 **Microsoft Intune 管理延伸模組**服務重新啟動之後執行。 對於 Intune 中指令碼或原則的任何變更，Intune 管理延伸模組用戶端會每小時檢查一次。

#### <a name="issue-intune-management-extension-doesnt-download"></a>問題：Intune 管理延伸模組不會下載

**可能的解決方式**：

- 請確定裝置在 Azure AD 中自動註冊。 若要確認，請在裝置上： 

  1. 移至 [設定] > [帳戶] > [存取公司或學校資源]。
  2. 選取已加入的帳戶 > [資訊]。
  3. 在 [進階診斷報告] 下，選取 [建立報表]。
  4. 在網頁瀏覽器中開啟 `MDMDiagReport`，然後前往 [註冊組態來源] 區段。
  5. 尋找 **MDMDeviceWithAAD** 屬性。 如果此屬性不存在，則您的裝置並非自動註冊。

    [啟用 Windows 10 自動註冊](windows-enroll.md#enable-windows-10-automatic-enrollment)包含的步驟。

#### <a name="issue-the-powershell-scripts-do-not-run"></a>問題：無法執行 PowerShell 指令碼

**可能的解決方式**：

- 確認 Intune 管理延伸模組已下載至 `%ProgramFiles(x86)%\Microsoft Intune Management Extension`。
- 在 Surface Hub 上不會執行指令碼。
- 檢查 `\ProgramData\Microsoft\IntuneManagementExtension\Logs` 中的記錄檔是否有任何錯誤。
- 針對可能的權限問題，請確保 PowerShell 指令碼的屬性設定為 `Run this script using the logged on credentials`。 也請檢查已登入的使用者是否具有執行指令碼的適當權限。
- 若要找出指令碼的問題，請執行範例指令碼。 例如，建立 `C:\Scripts` 目錄，並為每個人提供完全控制。 執行下列指令碼：

  ```powershell
  write-output "Script worked" | out-file c:\Scripts\output.txt
  ```

  如果成功，則應該建立 output.txt，並應包含 "Script worked" 文字。

- 若要在沒有 Intune 的情況下測試指令碼執行，請於本機使用 [psexec 工具](https://docs.microsoft.com/sysinternals/downloads/psexec)在系統內容中執行指令碼：

  `psexec -i -s`

## <a name="next-steps"></a>後續步驟

針對您的設定檔進行[監視](device-profile-monitor.md)及[疑難排解](device-profile-troubleshoot.md)。

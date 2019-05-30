---
title: 在 Microsoft Intune 中將 PowerShell 指令碼新增至 Windows 10 裝置 - Azure | Microsoft Docs
description: 在 Microsoft Intune 中建立和執行 PowerShell 指令碼、將指令碼原則指派給 Azure Active Directory 群組、使用報告來監視指令碼，以及查看用於刪除您在 Windows 10 裝置上所新增指令碼的步驟。 另請參閱一些常見問題和解決方式。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 05/28/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 768b6f08-3eff-4551-b139-095b3cfd1f89
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2c590f81b846fe3671d5ccddede28a4a4bd799ba
ms.sourcegitcommit: 876719180e0d73b69fc053cf67bb8cc40b364056
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/28/2019
ms.locfileid: "66264147"
---
# <a name="use-powershell-scripts-on-windows-10-devices-in-intune"></a>在 Intune 的 Windows 10 裝置上使用 PowerShell 指令碼

使用 Microsoft Intune 管理延伸模組在 Intune 中上傳 PowerShell 指令碼，以便在 Windows 10 裝置上執行。 管理延伸模組可增強 Windows 10 的行動裝置管理 (MDM)，可更輕鬆地轉移至新式管理。

本功能適用於：

- Windows 10 及更新版本

## <a name="move-to-modern-management"></a>移至新式管理

終端使用者運算正在歷經數位轉型。 典型的傳統 IT 著重於單一裝置平台、公司擁有的裝置、在辦公室工作的使用者，以及各種不同手動且反動的 IT 程序。 新式工作場所可使用使用者和企業擁有的多種平台，允許使用者在任何地方工作，並提供自動且主動的 IT 程序。

MDM 服務 (例如 Microsoft Intune) 可以管理執行 Windows 10 的行動裝置及桌面裝置。 內建的 Windows 10 管理用戶端可與 Intune 進行通訊，進而執行企業管理工作。 有一些您可能需要的工作，例如進階裝置設定和疑難排解。 針對 Win32 應用程式管理，您可以使用 Windows 10 裝置上的 [Win32 應用程式管理](apps-win32-app-management.md)功能。

Intune 管理延伸模組可補充內建的 Windows 10 MDM 功能。 您可以建立要在 Windows 10 裝置上執行的 PowerShell 指令碼。 例如，您可以建立會執行進階裝置設定的 PowerShell 指令碼，將該指令碼上傳至 Intune，將該指令碼指派至 Azure Active Directory (AD) 群組，然後執行該指令碼。 然後，您可以監視指令碼從開始到完成的執行狀態。

## <a name="prerequisites"></a>必要條件

Intune 管理延伸模組具有下列必要條件。 滿足這些必要條件時，會在 PowerShell 指令碼或 Win32 應用程式指派至使用者或裝置時自動安裝 Intune 管理延伸模組。

- 執行 Windows 10 1607 版或更新版本的裝置。 如果裝置是使用[大量自動註冊](windows-bulk-enroll.md)進行註冊的，則裝置必須執行 Windows 10 1703 版或更新版本。 因為 S 模式不允許執行非 Microsoft Store 應用程式，所以 Windows 10 的 S 模式不支援 Intune 管理延伸模組。 
  
- 已加入 Azure Active Directory (AD) 的裝置，包括：
  
  - 已加入混合式 Azure AD：已加入 Azure Active Directory (AD) 和內部部署 Active Directory (AD) 的裝置。 請參閱 [Plan your hybrid Azure Active Directory join implementation](https://docs.microsoft.com/azure/active-directory/devices/hybrid-azuread-join-plan) (規劃混合式 Azure Active Directory 加入實作) 以獲得指導。

- 在 Intune 中註冊的裝置，包括：

  - 在群組原則 (GPO) 中註冊的裝置。 請參閱 [Enroll a Windows 10 device automatically using Group Policy](https://docs.microsoft.com/windows/client-management/mdm/enroll-a-windows-10-device-automatically-using-group-policy) (使用群組原則自動註冊 Windows 10 裝置) 以獲得指導。
  
  - 在 Intune 中手動註冊的裝置，即為於：
  
    - 使用者以本機使用者帳戶登入裝置，然後手動將裝置加入 Azure AD (且 Azure AD 中的自動註冊 Intune 已啟用)。
    
    或是
    
    - 使用者使用自身 Azure AD 帳戶登入裝置，然後在 Intune 中註冊。

  - 使用 Configuration Manager 和 Intune 共同管理的裝置。 請參閱[什麼是共同管理？](https://docs.microsoft.com/sccm/comanage/overview)以獲得指導。

## <a name="create-a-script-policy"></a>建立指令碼原則 

1. 在 [Azure 入口網站](https://portal.azure.com)中，選取 [所有服務]  > 篩選 [Intune]  > 選取 [Intune]  。
2. 選取 [裝置設定]   > [PowerShell 指令碼]   > [新增]  。
3. 輸入下列內容：
    - **名稱**：輸入 PowerShell 指令碼的名稱。 
    - **描述**：輸入 PowerShell 指令碼的描述。 這是選擇性設定，但建議執行。 
    - **指令碼位置**：瀏覽至 PowerShell 指令碼。 指令碼必須小於 200 KB (ASCII)。
4. 選擇 [設定]  ，然後輸入下列屬性：
    - **使用登入認證執行此指令碼**：選取 [是]  以使用裝置上的使用者認證來執行指令碼。 選擇 [否]  (預設) 以在系統內容中執行指令碼。 許多系統管理員會選擇 [是]  。 如果需要在系統內容中執行指令碼，請選擇 [否]  。
    - **強制執行指令碼簽章檢查**：如果指令碼必須由信任的發行者簽章，請選取 [是]  。 如果指令碼不需要簽章，請選取 [否]  (預設)。 
    - **在 64 位元的 PowerShell 主機中執行指令碼**：選取 [是]  以在 64 位元用戶端架構的 64 位元 PowerShell (PS) 主機中執行指令碼。 選取 [否]  (預設) 以在 32 位元的 PowerShell 主機中執行指令碼。

      設定為 [是]  或 [否]  時，可使用下表來了解新的和現有原則行為：

      | 在 64 位元的 PS 主機中執行指令碼 | 用戶端架構 | 新的 PS 指令碼 | 現有的 PS 指令碼原則 |
      | --- | --- | --- | --- | 
      | 否 | 32 位元  | 支援 32 位元的 PS 主機 | 僅在 32 位元的 PS 主機中執行，該主機可在 32 位元和 64 位元架構上運作。 |
      | 是 | 64 位元 | 僅在 64 位元架構的 64 位元 PS 主機中執行。 在 32 位元上執行時，指令碼會在 32 位元的 PS 主機中執行。 | 在 32 位元的 PS 主機中執行指令碼。 如果此設定變更為 64 位元，指令碼會在 64 位元的 PS 主機中開啟 (但不會執行) 並報告結果。 在 32 位元上執行時，指令碼會在 32 位元的 PS 主機中執行。 |

    ![在 Microsoft Intune 中新增和使用 PowerShell 指令碼](./media/mgmt-extension-add-script.png)
5. 選取 [確定]   > [建立]  以儲存指令碼。

> [!NOTE]
> 將指令碼設定為使用者內容，且裝置上的終端使用者具有管理員權限時，(根據預設) PowerShell 指令碼將以管理員權限來執行。

## <a name="assign-the-policy"></a>指派原則

1. 在 [PowerShell 指令碼]  中，選取要指派的指令碼，然後選擇 [管理]   > [指派]  。

    ![在 Microsoft Intune 中將 PowerShell 指令碼指派或部署到裝置群組](./media/mgmt-extension-assignments.png)

2. 選擇 [選取群組]  列出可用的 Azure AD 群組。 
3. 選取包含其裝置接收指令碼之使用者的一或多個群組。 [選取]  以將原則指派給選取的群組。

> [!NOTE]
> - 終端使用者不需要登入裝置來執行 PowerShell 指令碼。
> - Intune 中的 PowerShell 指令碼可以鎖定至 Azure AD 裝置安全性群組或 Azure AD 使用者安全性群組。

Intune 管理延伸模組用戶端會每小時及在每次重新啟動後檢查 Intune 一次，看看其中是否有任何新的指令碼或變更。 將原則指派給 Azure AD 群組之後，即會執行 PowerShell 指令碼，並報告執行結果。 指令碼執行之後，除非指令碼或原則中發生變更，否則不會再次執行。

## <a name="monitor-run-status"></a>監視執行狀態

您可以在 Azure 入口網站中，監視使用者和裝置之 PowerShell 指令碼的執行狀態。

在 [PowerShell 指令碼]  中，選取要監視的指令碼，然後選擇 [監視]  ，再選擇下列其中一種報表：

- **裝置狀態**
- **使用者狀態**

## <a name="troubleshoot-scripts"></a>針對指令碼進行疑難排解

用戶端電腦上的代理程式記錄通常位於 `\ProgramData\Microsoft\IntuneManagementExtension\Logs`。 您可以使用 [CMTrace.exe](https://docs.microsoft.com/sccm/core/support/tools) 來檢視這些記錄檔。 

![Microsoft Intune 中的 CMTrace 代理程式記錄螢幕擷取畫面或範例](./media/apps-win32-app-10.png)  

## <a name="delete-a-script"></a>刪除指令碼

在 [PowerShell 指令碼]  中，以滑鼠右鍵按一下指令碼，然後選取 [刪除]  。

## <a name="common-issues-and-resolutions"></a>常見問題和解決方式

#### <a name="issue-intune-management-extension-doesnt-download"></a>問題：Intune 管理延伸模組不會下載

**可能的解決方式**：

- 裝置未加入 Azure AD。 請確保裝置滿足本文中的[必要條件](#prerequisites)。 
- 沒有任何指派至使用者或裝置所屬群組的 PowerShell 指令碼或 Win32 應用程式。
- 因為沒有網際網路存取、沒有 Windows 推播通知服務 (WNS) 等原因，所以裝置無法簽入 Intune 服務。
- 裝置處於 S 模式。 於 S 模式中執行的裝置不支援 Intune 管理延伸模組。 

若要查看裝置是否已自動註冊，您可以：

  1. 移至 [設定]   > [帳戶]   > [存取公司或學校資源]  。
  2. 選取已加入的帳戶 > [資訊]  。
  3. 在 [進階診斷報告]  下，選取 [建立報表]  。
  4. 在 Web 瀏覽器中開啟 `MDMDiagReport`。
  5. 搜尋 **MDMDeviceWithAAD** 屬性。 如果屬性存在，就代表裝置已自動註冊。 如果屬性不存在，則代表裝置未自動註冊。

[啟用 Windows 10 自動註冊](windows-enroll.md#enable-windows-10-automatic-enrollment)包含於 Intune 中設定自訂註冊的步驟。

#### <a name="issue-powershell-scripts-do-not-run"></a>問題：無法執行 PowerShell 指令碼

**可能的解決方式**：

- PowerShell 指令碼不會在每次登入時執行。 指令碼執行時機：

  - 當指令碼指派至裝置時
  - 當您變更指令碼並加以上傳，然後將其指派至使用者或裝置時
  
    > [!TIP]
    > **Microsoft Intune 管理延伸模組**是在裝置上執行的服務，性質如同服務應用程式 (services.msc) 中列出的所有其他服務。 裝置重新開機之後，此服務也可能重新啟動，並向 Intune 服務確認所有指派的 PowerShell 指令碼。 如果 **Microsoft Intune 管理延伸模組**服務設定為手動，則服務就可能不會在裝置重新開機後重新啟動。

- 對於 Intune 中指令碼或原則的任何變更，Intune 管理延伸模組用戶端會每小時檢查一次。
- 確認 Intune 管理延伸模組已下載至 `%ProgramFiles(x86)%\Microsoft Intune Management Extension`。
- 指令碼在 Surface Hub 和 Windows 10 S 模式中不會執行。
- 請檢閱記錄中是否存在任何錯誤。 請參閱本文的[針對指令碼進行疑難排解](#troubleshoot-scripts)。
- 針對可能的權限問題，請確保 PowerShell 指令碼的屬性設定為 `Run this script using the logged on credentials`。 也請檢查已登入的使用者是否具有執行指令碼的適當權限。

- 若要解決指令碼問題，請進行以下操作：

  - 檢閱您裝置上的 PowerShell 執行設定。 請參閱 [PowerShell execution policy](https://docs.microsoft.com/powershell/module/microsoft.powershell.security/set-executionpolicy?view=powershell-6) (PowerShell 執行原則) 以獲得指導。
  - 使用 Intune 管理延伸模組執行範例指令碼。 例如，建立 `C:\Scripts` 目錄，並為每個人提供完全控制。 執行下列指令碼：

    ```powershell
    write-output "Script worked" | out-file c:\Scripts\output.txt
    ```

    如果成功，則應該建立 output.txt，並應包含 "Script worked" 文字。

  - 若要在沒有 Intune 的情況下測試指令碼執行，請於本機使用 [psexec 工具](https://docs.microsoft.com/sysinternals/downloads/psexec)在系統帳戶中執行指令碼：

    `psexec -i -s`

## <a name="next-steps"></a>後續步驟

針對您的設定檔進行[監視](device-profile-monitor.md)及[疑難排解](device-profile-troubleshoot.md)。

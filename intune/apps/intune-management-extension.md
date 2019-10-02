---
title: 在 Microsoft Intune 中將 PowerShell 指令碼新增至 Windows 10 裝置 - Azure | Microsoft Docs
description: 在 Microsoft Intune 中建立和執行 PowerShell 指令碼、將指令碼原則指派給 Azure Active Directory 群組、使用報告來監視指令碼，以及查看用於刪除您在 Windows 10 裝置上所新增指令碼的步驟。 另請參閱一些常見問題和解決方式。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/16/2019
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
ms.openlocfilehash: 8214c36c627958c7978b823b99bd62a5b166d26b
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2019
ms.locfileid: "71724876"
---
# <a name="use-powershell-scripts-on-windows-10-devices-in-intune"></a>在 Intune 的 Windows 10 裝置上使用 PowerShell 指令碼

使用 Microsoft Intune 管理延伸模組在 Intune 中上傳 PowerShell 指令碼，以便在 Windows 10 裝置上執行。 管理延伸模組可增強 Windows 10 的行動裝置管理 (MDM)，可更輕鬆地轉移至新式管理。

本功能適用於：

- Windows 10 及更新版本

## <a name="move-to-modern-management"></a>移至新式管理

終端使用者運算正在歷經數位轉型。 典型的傳統 IT 著重於單一裝置平台、公司擁有的裝置、在辦公室工作的使用者，以及各種不同手動且反動的 IT 程序。 新式工作場所可使用使用者和企業擁有的多種平台，允許使用者在任何地方工作，並提供自動且主動的 IT 程序。

MDM 服務 (例如 Microsoft Intune) 可以管理執行 Windows 10 的行動裝置及桌面裝置。 內建的 Windows 10 管理用戶端可與 Intune 進行通訊，進而執行企業管理工作。 有一些您可能需要的工作，例如進階裝置設定和疑難排解。 針對 Win32 應用程式管理，您可以使用 Windows 10 裝置上的 [Win32 應用程式管理](app-management.md)功能。

Intune 管理延伸模組可補充內建的 Windows 10 MDM 功能。 您可以建立要在 Windows 10 裝置上執行的 PowerShell 指令碼。 例如，建立執行進階裝置設定的 PowerShell 指令碼。 然後，將指令碼上傳至 Intune、將指令碼指派給 Azure Active Directory (AD) 群組，以及執行指令碼。 然後，您可以監視指令碼從開始到完成的執行狀態。

## <a name="prerequisites"></a>必要條件

Intune 管理延伸模組具有下列必要條件。 一旦符合這些必要條件，就會在 PowerShell 指令碼或 Win32 應用程式指派至使用者或裝置時，自動安裝 Intune 管理延伸模組。

- 執行 Windows 10 1607 版或更新版本的裝置。 如果裝置是使用[大量自動註冊](../enrollment/windows-bulk-enroll.md)進行註冊的，則裝置必須執行 Windows 10 1703 版或更新版本。 因為 S 模式不允許執行非 Microsoft Store 應用程式，所以 Windows 10 的 S 模式不支援 Intune 管理延伸模組。 
  
- 已加入 Azure Active Directory (AD) 的裝置，包括：  
  
  - 已加入混合式 Azure AD：已加入 Azure Active Directory (AD) 和內部部署 Active Directory (AD) 的裝置。 請參閱 [Plan your hybrid Azure Active Directory join implementation](https://docs.microsoft.com/azure/active-directory/devices/hybrid-azuread-join-plan) (規劃混合式 Azure Active Directory 加入實作) 以獲得指導。

- 在 Intune 中註冊的裝置，包括：

  - 在群組原則 (GPO) 中註冊的裝置。 請參閱 [Enroll a Windows 10 device automatically using Group Policy](https://docs.microsoft.com/windows/client-management/mdm/enroll-a-windows-10-device-automatically-using-group-policy) (使用群組原則自動註冊 Windows 10 裝置) 以獲得指導。
  
  - 在 Intune 中手動註冊的裝置，即為於：
  
    - 在 Azure AD 中啟用[向 Intune 自動註冊](../enrollment/quickstart-setup-auto-enrollment.md)。 終端使用者會使用本機使用者帳戶登入裝置、手動將裝置加入至 Azure AD，然後使用其 Azure AD 帳戶登入裝置。
    
    或  
    
    - 使用者使用自身 Azure AD 帳戶登入裝置，然後在 Intune 中註冊。

  - 使用 Configuration Manager 和 Intune 共同管理的裝置。 請務必將 [用戶端應用程式]  工作負載設定為 [試驗 Intune]  或 [Intune]  。 如需指引，請參閱下列文章： 
  
    - [什麼是共同管理](https://docs.microsoft.com/sccm/comanage/overview) 
    - [用戶端應用程式工作負載](https://docs.microsoft.com/sccm/comanage/workloads#client-apps)
    - [將 Configuration Manager 工作負載切換至 Intune](https://docs.microsoft.com/sccm/comanage/how-to-switch-workloads)
  
> [!TIP]
> 請確定裝置均會[加入](https://docs.microsoft.com/azure/active-directory/user-help/user-help-join-device-on-network) \(部分機器翻譯\) 至 Azure AD。 只在 Azure AD 中[註冊](https://docs.microsoft.com/azure/active-directory/user-help/user-help-register-device-on-network) \(部分機器翻譯\) 的裝置將不會收到您的指令碼。

## <a name="create-a-script-policy-and-assign-it"></a>建立並指派指令碼原則

1. 登入 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
2. 選取 [裝置設定]   > [PowerShell 指令碼]   > [新增]  。

    ![在 Microsoft Intune 中新增和使用 PowerShell 指令碼](./media/intune-management-extension/mgmt-extension-add-script.png)

3. 在 [基本資訊]  中，輸入下列內容，然後選取 [下一步]  ：
    - **名稱**：輸入 PowerShell 指令碼的名稱。 
    - **描述**：輸入 PowerShell 指令碼的描述。 這是選擇性設定，但建議執行。
4. 在 [指令碼設定]  中，輸入下列內容，然後選取 [下一步]  ：
    - **指令碼位置**：瀏覽至 PowerShell 指令碼。 指令碼必須小於 200 KB (ASCII)。
    - **使用登入認證執行此指令碼**：選取 [是]  以使用裝置上的使用者認證來執行指令碼。 選擇 [否]  (預設) 以在系統內容中執行指令碼。 許多系統管理員會選擇 [是]  。 如果需要在系統內容中執行指令碼，請選擇 [否]  。
    - **強制執行指令碼簽章檢查**：如果指令碼必須由信任的發行者簽章，請選取 [是]  。 如果指令碼不需要簽章，請選取 [否]  (預設)。 
    - **在 64 位元的 PowerShell 主機中執行指令碼**：選取 [是]  以在 64 位元用戶端架構的 64 位元 PowerShell (PS) 主機中執行指令碼。 選取 [否]  (預設) 以在 32 位元的 PowerShell 主機中執行指令碼。

      設定為 [是]  或 [否]  時，可使用下表來了解新的和現有原則行為：

      | 在 64 位元的 PS 主機中執行指令碼 | 用戶端架構 | 新的 PS 指令碼 | 現有的 PS 指令碼原則 |
      | --- | --- | --- | --- | 
      | 否 | 32 位元  | 支援 32 位元的 PS 主機 | 僅在 32 位元的 PS 主機中執行，該主機可在 32 位元和 64 位元架構上運作。 |
      | 是 | 64 位元 | 僅在 64 位元架構的 64 位元 PS 主機中執行。 在 32 位元上執行時，指令碼會在 32 位元的 PS 主機中執行。 | 在 32 位元的 PS 主機中執行指令碼。 如果此設定變更為 64 位元，指令碼會在 64 位元的 PS 主機中開啟 (但不會執行) 並報告結果。 在 32 位元上執行時，指令碼會在 32 位元的 PS 主機中執行。 |

5. 選取 [範圍標籤]  。 範圍標籤為選擇性。 [針對分散式 IT 使用角色型存取控制 (RBAC) 和範圍標籤](../fundamentals/scope-tags.md)提供詳細資訊。

    若要新增範圍標籤：

    1. 選擇 [選取範圍標籤]  > 從清單中選取現有的範圍標籤 > [選取]  。

    2. 完成時，請選取 [下一步]  。

6. 選取 [指派]   > [選取要包含的群組]  。 Azure AD 群組的現有清單會隨即顯示。

    1. 選取包含其裝置接收指令碼之使用者的一或多個群組。 選擇 [選取]  。 您選擇的群組會顯示在清單中，並會接收您的原則。

        > [!NOTE]
        > Intune 中的 PowerShell 指令碼可以鎖定至 Azure AD 裝置安全性群組或 Azure AD 使用者安全性群組。

    2. 選取 [下一步]  。

        ![在 Microsoft Intune 中將 PowerShell 指令碼指派或部署到裝置群組](./media/intune-management-extension/mgmt-extension-assignments.png)

7. 在 [檢閱 + 新增]  中，會顯示您設定的設定摘要。 選取 [新增]  以儲存此指令碼。 當您選取 [新增]  時，會將原則部署到您選擇的群組。

## <a name="important-considerations"></a>重要考量

- 將指令碼設定為使用者內容且終端使用者具有系統管理員權限時，根據預設，PowerShell 指令碼會以系統管理員權限來執行。

- 終端使用者不需要登入裝置來執行 PowerShell 指令碼。

- Intune 管理延伸模組用戶端會每小時及在每次重新啟動後檢查 Intune 一次，查看其中是否有任何新的指令碼或變更。 將原則指派給 Azure AD 群組之後，即會執行 PowerShell 指令碼，並報告執行結果。 指令碼執行之後，除非指令碼或原則中發生變更，否則不會再次執行。

## <a name="monitor-run-status"></a>監視執行狀態

您可以在 Azure 入口網站中，監視使用者和裝置之 PowerShell 指令碼的執行狀態。

在 [PowerShell 指令碼]  中，選取要監視的指令碼，然後選擇 [監視]  ，再選擇下列其中一種報表：

- **裝置狀態**
- **使用者狀態**

## <a name="intune-management-extension-logs"></a>Intune 管理延伸模組記錄

用戶端電腦上的代理程式記錄通常位於 `\ProgramData\Microsoft\IntuneManagementExtension\Logs`。 您可以使用 [CMTrace.exe](https://docs.microsoft.com/sccm/core/support/tools) 來檢視這些記錄檔。 

![Microsoft Intune 中的 CMTrace 代理程式記錄螢幕擷取畫面或範例](./media/apps-win32-app-management/apps-win32-app-10.png)  

## <a name="delete-a-script"></a>刪除指令碼

在 [PowerShell 指令碼]  中，以滑鼠右鍵按一下指令碼，然後選取 [刪除]  。

## <a name="common-issues-and-resolutions"></a>常見問題和解決方式

### <a name="issue-intune-management-extension-doesnt-download"></a>問題：Intune 管理延伸模組不會下載

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

[啟用 Windows 10 自動註冊](../enrollment/windows-enroll.md#enable-windows-10-automatic-enrollment)包含於 Intune 中設定自訂註冊的步驟。

### <a name="issue-powershell-scripts-do-not-run"></a>問題：無法執行 PowerShell 指令碼

**可能的解決方式**：

- PowerShell 指令碼不會在每次登入時執行。 指令碼執行時機：

  - 當指令碼指派至裝置時
  - 當您變更指令碼並加以上傳，然後將其指派至使用者或裝置時
  
    > [!TIP]
    > **Microsoft Intune 管理延伸模組**是在裝置上執行的服務，性質如同服務應用程式 (services.msc) 中列出的所有其他服務。 裝置重新開機之後，此服務也可能重新啟動，並向 Intune 服務確認所有指派的 PowerShell 指令碼。 如果 **Microsoft Intune 管理延伸模組**服務設定為手動，則服務就可能不會在裝置重新開機後重新啟動。

- 請確定裝置均會[加入至 Azure AD](https://docs.microsoft.com/azure/active-directory/user-help/user-help-join-device-on-network) \(部分機器翻譯\)。 只加入至您的工作場所或組織的裝置 (已在 Azure AD 中[註冊](https://docs.microsoft.com/azure/active-directory/user-help/user-help-register-device-on-network) \(部分機器翻譯\)) 將不會收到指令碼。
- 對於 Intune 中指令碼或原則的任何變更，Intune 管理延伸模組用戶端會每小時檢查一次。
- 確認 Intune 管理延伸模組已下載至 `%ProgramFiles(x86)%\Microsoft Intune Management Extension`。
- 指令碼在 Surface Hub 和 Windows 10 S 模式中不會執行。
- 請檢閱記錄中是否存在任何錯誤。 請參閱 [Intune 管理延伸模組記錄](#intune-management-extension-logs) (在本文中)。
- 針對可能的權限問題，請確保 PowerShell 指令碼的屬性設定為 `Run this script using the logged on credentials`。 也請檢查已登入的使用者是否具有執行指令碼的適當權限。

- 若要找出指令碼的問題，您可以：

  - 檢閱您裝置上的 PowerShell 執行設定。 請參閱 [PowerShell execution policy](https://docs.microsoft.com/powershell/module/microsoft.powershell.security/set-executionpolicy?view=powershell-6) (PowerShell 執行原則) 以獲得指導。
  - 使用 Intune 管理延伸模組執行範例指令碼。 例如，建立 `C:\Scripts` 目錄，並為每個人提供完全控制。 執行下列指令碼：

    ```powershell
    write-output "Script worked" | out-file c:\Scripts\output.txt
    ```

    如果成功，則應該建立 output.txt，並應包含 "Script worked" 文字。

  - 若要在沒有 Intune 的情況下測試指令碼執行，請於本機使用 [psexec 工具](https://docs.microsoft.com/sysinternals/downloads/psexec)在系統帳戶中執行指令碼：

    `psexec -i -s`  
    
  - 如果指令碼報告它已成功，但實際上並未成功，則可能是您的防毒軟體服務可能將 AgentExecutor 設為在沙箱中執行。 下列指令碼一律會報告 Intune 中的失敗。 作為測試，您可以使用此指令碼：
  
    ```powershell
    Write-Error -Message "Forced Fail" -Category OperationStopped
    mkdir "c:\temp" 
    echo "Forced Fail" | out-file c:\temp\Fail.txt
    ```

    如果指令碼報告成功，請查看 `AgentExecutor.log` 以確認錯誤輸出。 如果指令碼執行，則長度應 >2。

  - 若要擷取 .error 和 .output 檔，下列程式碼片段會透過 AgentExecutor 執行指令碼到 PSx86 (`C:\Windows\SysWOW64\WindowsPowerShell\v1.0`)。 它會保留記錄以供您檢閱。 請記住，在指令碼執行之後，Intune 管理延伸模組會清除記錄：
  
    ```powershell
    $scriptPath = read-host "Enter the path to the script file to execute"
    $logFolder = read-host "Enter the path to a folder to output the logs to"
    $outputPath = $logFolder+"\output.output"
    $errorPath =  $logFolder+"\error.error"
    $timeoutPath =  $logFolder+"\timeout.timeout"
    $timeoutVal = 60000 
    $PSFolder = "C:\Windows\SysWOW64\WindowsPowerShell\v1.0"
    $AgentExec = "C:\Program Files (x86)\Microsoft Intune Management Extension\agentexecutor.exe"
    &$AgentExec -powershell  $scriptPath $outputPath $errorPath $timeoutPath $timeoutVal $PSFolder 0 0
    ```

## <a name="next-steps"></a>後續步驟

針對您的設定檔進行[監視](../device-profile-monitor.md)及[疑難排解](../device-profile-troubleshoot.md)。

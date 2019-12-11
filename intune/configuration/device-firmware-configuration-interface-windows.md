---
title: 在 Microsoft Intune 中使用 MDM 原則更新 Windows BIOS 功能 - Azure | Microsoft Docs
description: 在 Microsoft Intune 中，新增裝置韌體設定介面 (DFCI) 設定檔來管理 Windows 10 裝置上的 UEFI 設定，例如 CPU、內建硬體和開機選項。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/06/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 38f02d694f1935e4732805f3ae7c66fd9718057a
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "74059598"
---
# <a name="use-device-firmware-configuration-interface-profiles-on-windows-devices-in-microsoft-intune-public-preview"></a>在 Microsoft Intune 中，於 Windows 裝置上使用裝置韌體設定介面設定檔 (公開預覽)

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

當您使用 Intune 來管理 Autopilot 裝置時，您可以使用裝置韌體設定介面 (DFCI)，在註冊之後管理 UEFI (BIOS) 設定。 如需優點、案例和必要條件的概觀，請參閱 [DFCI 概觀](https://microsoft.github.io/mu/dyn/mu_plus/DfciPkg/Docs/Dfci_Feature/) \(英文\)。

DFCI [可讓 Windows](https://docs.microsoft.com/windows/client-management/mdm/uefi-csp) \(部分機器翻譯\) 從 Intune 傳遞管理命令至 UEFI (整合可延伸韌體介面)。

在 Intune 中，使用此功能來控制 BIOS 設定。 韌體對惡意攻擊通常更具有復原性。 它會限制使用者對 BIOS 的控制權，這在遭到入侵的情況下是很好的做法。

例如，您在安全的環境中使用 Windows 10 裝置，而且想要停用相機。 您可以在韌體層停用相機，這樣不論使用者做什麼都不會開啟相機。 重新安裝 OS 或抹除電腦不會重新開啟相機。 在另一個範例中，鎖定開機選項，以防止使用者開機為另一個 OS，或不具有相同安全性功能的舊版 Windows。

當您重新安裝舊版 Windows、安裝個別 OS 或格式化硬碟時，無法覆寫 DFCI 管理。 此功能可防止惡意程式碼與 OS 處理序 (包括提高權限的 OS 處理序) 通訊。 DFCI 的信任鏈結使用公開金鑰加密，而不會依賴本機 UEFI (BIOS) 密碼安全性。 這一層安全性會阻止本機使用者從裝置的 UEFI (BIOS) 功能表存取受管理的設定。

本功能適用於：

- 在受支援 UEFI 上的 Windows 10 RS5 (1809) 和更新版本

## <a name="before-you-begin"></a>開始之前

- 裝置製造商必須在製造程序中將 DFCI 新增至其 UEFI 韌體，或作為您安裝的韌體更新。 請與您的裝置廠商合作，以判斷[支援 DFCI 的廠商](https://microsoft.github.io/mu/dyn/mu_plus/DfciPkg/Docs/Scenarios/DfciScenarios/#oems-that-support-dfci)，或使用 DFCI 所需的韌體版本。

- 裝置必須由 [Microsoft 雲端解決方案提供者 (CSP) 合作夥伴](https://partner.microsoft.com/cloud-solution-provider)註冊 Windows Autopilot，或由 OEM 直接註冊。 

  手動註冊 Autopilot 的裝置 (例如[從 CSV 檔案匯入](../enrollment/enrollment-autopilot.md#add-devices)) 不允許使用 DFCI。 根據設計，DFCI 管理需要透過 OEM 或 Microsoft CSP 合作夥伴向 Windows Autopilot 進行註冊的裝置商業收購外部證明。

  註冊裝置之後，其序號會顯示在 Windows Autopilot 裝置清單中。

  如需 Autopilot 的詳細資訊 (包含任何需求)，請參閱[使用 Windows Autopilot 在 Intune 中註冊 Windows 裝置](../enrollment/enrollment-autopilot.md)。

## <a name="create-your-azure-ad-security-groups"></a>建立您的 Azure AD 安全性群組

Autopilot 部署設定檔會指派給 Azure AD 安全性群組。 請務必建立包含 DFCI 裝置的群組。 針對 DFCI 裝置，大部分組織可能會建立裝置群組，而不是使用者群組。 請考慮以下案例：

- 人力資源 (HR) 有不同的 Windows 裝置。 基於安全性理由，您不希望此群組中的任何人使用裝置上的相機。 在此案例中，您可以建立 HR 安全性使用者群組，這樣無論裝置類型為何，原則都會套用至 HR 群組中的使用者。
- 在製造場所，您有 10 部裝置。 在所有裝置上，您想要防止從 USB 裝置啟動裝置。 在此案例中，您可以建立安全性裝置群組，並將這 10 部裝置新增至該群組。

如需在 Intune 中建立群組的詳細資訊，請參閱[新增群組來組織使用者和裝置](../fundamentals/groups-add.md)。

## <a name="create-the-profiles"></a>建立設定檔

若要使用 DFCI，請建立下列設定檔，並將它們指派給您的群組。

### <a name="create-an-autopilot-deployment-profile"></a>建立 Autopilot 部署設定檔

此設定檔會安裝並預先設定新的裝置。 [Autopilot 部署設定檔](../enrollment/enrollment-autopilot.md#create-an-autopilot-deployment-profile)列出建立設定檔的步驟。

### <a name="create-an-enrollment-state-page-profile"></a>建立註冊狀態頁面設定檔

此設定檔可確保在 Windows 安裝期間，裝置會驗證並啟用 DFCI。 強烈建議使用此設定檔來封鎖裝置使用，直到已安裝所有應用程式和設定檔為止。 [註冊狀態頁面設定檔](../enrollment/windows-enrollment-status.md)列出建立設定檔的步驟。

### <a name="create-the-dfci-profile"></a>建立 DFCI 設定檔

此設定檔包含您設定的 DFCI 設定。

1. 登入 [Microsoft 端點管理員系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。
2. 選取 [裝置]   > [組態設定檔]   > [建立設定檔]  。
3. 輸入下列內容：

    - **名稱**：為設定檔輸入描述性名稱。 為您的設定檔命名，以方便之後能夠輕鬆識別。 例如，一個良好的設定檔名稱是 **Windows：在 Windows 裝置上設定 DFCI 設定**。
    - **描述**：輸入設定檔的描述。 這是選擇性設定，但建議執行。
    - **平台**：選擇 [Windows 10 及更新版本]  。
    - **設定檔類型**：選取 [裝置韌體設定介面]  。

4. 設定這些設定：

    - **允許本機使用者變更 UEFI (BIOS) 設定**：選項包括：
      - **僅未設定的設定**：「除非」  是使用 Intune 明確設定為 [啟用]  或 [停用]  的設定，否則本機使用者可以變更任何設定。
      - **無**：本機使用者不能變更任何 UEFI (BIOS) 設定，包括未顯示在 DFCI 設定檔中的設定。

    - **CPU 與 IO 虛擬化**：選項包括：
        - **未設定**：Intune 不會變更此功能，任何設定都會保持原狀。
        - **啟用**：BIOS 讓平台的 CPU 與 IO 虛擬化功能可供 OS 使用。 它會開啟以 Windows 虛擬化為基礎的安全性和 Device Guard 技術。
        - **停用**：BIOS 會停用平台 CPU 與 IO 虛擬化功能，並防止它們被使用。
    - **相機**：選項包括：
        - **未設定**：Intune 不會變更此功能，任何設定都會保持原狀。
        - **啟用**：啟用由 UEFI (BIOS) 管理的所有內建相機。 週邊設備 (如 USB 相機) 不受影響。
        - **已停用**：停用由 UEFI (BIOS) 管理的所有內建相機。 週邊設備 (如 USB 相機) 不受影響。
    - **麥克風和喇叭**：選項包括：
        - **未設定**：Intune 不會變更此功能，任何設定都會保持原狀。
        - **啟用**：啟用由 UEFI (BIOS) 管理的所有內建式麥克風和喇叭。 週邊設備 (如 USB 裝置) 不受影響。
        - **已停用**：停用由 UEFI (BIOS) 管理的所有內建式麥克風和喇叭。 週邊設備 (如 USB 裝置) 不受影響。
    - **無線電波 (藍牙、Wi-Fi、NFC 等等。)** ：選項包括：
        - **未設定**：Intune 不會變更此功能，任何設定都會保持原狀。
        - **啟用**：啟用由 UEFI (BIOS) 管理的所有內建無線電波。 週邊設備 (如 USB 裝置) 不受影響。
        - **已停用**：停用由 UEFI (BIOS) 管理的所有內建無線電波。 週邊設備 (如 USB 裝置) 不受影響。

        > [!WARNING]
        > 如果您停用**無線電波**設定，裝置需要有線網路連線。 否則，裝置可能無法受管理。

    - **從外部媒體 (USB、SD) 開機**：選項包括：
        - **未設定**：Intune 不會變更此功能，任何設定都會保持原狀。
        - **啟用**：UEFI (BIOS) 允許從非硬碟儲存體開機。
        - **已停用**：UEFI (BIOS) 不允許從非硬碟儲存體開機。
    - **從網路介面卡開機**：選項包括：
        - **未設定**：Intune 不會變更此功能，任何設定都會保持原狀。
        - **啟用**：UEFI (BIOS) 允許從內建網路介面開機。
        - **已停用**：UEFI (BIOS) 不允許從內建網路介面開機。

5. 當您完成時，請選取 [確定]   > [建立]  儲存變更。 就會建立設定檔，並顯示在清單中。

## <a name="assign-the-profiles-and-reboot"></a>指派設定檔，然後重新開機

建立設定檔之後，就[可以指派它](../configuration/device-profile-assign.md)。 請務必將設定檔指派給包含 DFCI 裝置的 Azure AD 安全性群組。

當裝置執行 Windows Autopilot 時，DFCI 可能會在 [註冊狀態] 頁面中強制重新開機。 在這次重新開機期間，會向 Intune 註冊 UEFI。 

如果您想要確認裝置已註冊，您可以再次將裝置重新開機，但不需要。 使用裝置製造商的指示來開啟 UEFI 功能表，然後確認 UEFI 現在已受管理。

下次裝置與 Intune 同步時，Windows 會收到 DFCI 設定。 將裝置重新開機。 需要這個第三次重新開機，UEFI 才能從 Windows 接收 DFCI 設定。

## <a name="update-existing-dfci-settings"></a>更新現有 DFCI 設定

如果您想要在使用中的裝置上變更現有 DFCI 設定，您可以。 在您的現有 DFCI 設定檔中，變更設定並儲存變更。 由於已指派設定檔，因此新的 DFCI 設定會在下列情況下生效：

1. 裝置簽入 Intune 服務，以審查設定檔更新。 簽入會在不同時間發生。 如需詳細資訊，請參閱[當裝置取得原則、設定檔或應用程式更新時](../configuration/device-profile-troubleshoot.md#how-long-does-it-take-for-devices-to-get-a-policy-profile-or-app-after-they-are-assigned)。

2. 若要強制新設定生效，請從[遠端](../remote-actions/device-restart.md)或本機將裝置重新開機。

您也可以[發出信號要求裝置簽入](../remote-actions/device-sync.md)。 成功同步之後，[發出信號要求重新開機](../remote-actions/device-restart.md)。

>[!NOTE]
> 刪除 DFCI 設定檔，或將裝置從指派給設定檔的群組中移除，並不會移除 DFCI 設定或重新啟用 UEFI (BIOS) 功能表。 如果您想要停止使用 DFCI，請更新現有 DFCI 設定檔。 如需這些步驟的詳細資訊，請參閱此文章中的[淘汰裝置](#retire)。

## <a name="reuse-retire-or-recover-the-device"></a>重複使用、淘汰或復原裝置

### <a name="reuse"></a>重複使用

如果您打算重設 Windows 以重新規劃裝置，請[抹除裝置](../remote-actions/devices-wipe.md)。 請**勿**移除 Autopilot 裝置記錄。

抹除裝置之後，請將裝置移至指派新 DFCI 和 Autopilot 設定檔的群組。 請務必將裝置重新開機，以重新執行 Windows 安裝程式。

### <a name="retire"></a>淘汰

當您準備好要淘汰裝置，並將它從管理系統釋放時，請將 DFCI 設定檔更新為您想要裝置在離開時具有的 UEFI (BIOS) 設定狀態。 您通常會想要啟用所有設定。 例如：

1. 開啟您的 DFCI 設定檔 ([裝置]   > [組態設定檔]  )。
2. 將 [允許本機使用者變更 UEFI (BIOS) 設定]  設定變更為 [僅未設定的設定]  。
3. 將所有其他設定設定為 [未設定]  。
4. 儲存設定。

這些步驟會將裝置的 UEFI (BIOS) 功能表解除鎖定。 這些值保持與設定檔 ([啟用]  或 [停用]  ) 的相同，不會設定為任何預設 OS 值。

您現在可以抹除裝置。 抹除裝置之後，請刪除 Autopilot 記錄。 刪除記錄可防止裝置在重新開機時自動重新註冊。

### <a name="recover"></a>復原

如果您抹除裝置，並在將 UEFI (BIOS) 功能表解除鎖定之前刪除 Autopilot 記錄，則功能表會保持鎖定。 Intune 無法傳送設定檔更新來將它解除鎖定。

若要將裝置解除鎖定，請開啟 UEFI (BIOS) 功能表，然後從網路重新整理管理。 復原會將功能表解除鎖定，但所有 UEFI (BIOS) 設定都會保留為先前 Intune DFCI 設定檔中的值。

## <a name="end-user-impact"></a>使用者影響

套用 DFCI 原則時，即使 UEFI (BIOS) 功能表受密碼保護，本機使用者也無法變更 DFCI 所設定的設定。 視您設定的組態而定，終端使用者可能會收到找不到硬體元件或無法診斷的錯誤。 請務必提供文件給使用者，說明您已停用的選項。  

## <a name="next-steps"></a>後續步驟

指派設定檔之後，[監視其狀態](../device-profile-monitor.md)。

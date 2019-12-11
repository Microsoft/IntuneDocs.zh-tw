---
title: Microsoft Intune 中 BitLocker 原則的疑難排解秘訣
titleSuffix: Microsoft Intune
description: 說明如何使用 Intune 原則在裝置上啟用 BitLocker 加密，以及如何驗證您的原則是否已成功部署到裝置。
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/02/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 744277b0e49a4e3ca8b0fa3bac43c666110bb8a3
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "74410360"
---
# <a name="troubleshoot-bitlocker-policies-in-microsoft-intune"></a>針對 Microsoft Intune 中的 BitLocker 原則進行疑難排解

本文可協助 Intune 系統管理員瞭解 Windows 10 裝置如何根據 Intune 原則來設定 BitLocker。 本文也提供如何針對使用 Intune 管理的裝置上的 BitLocker 設定問題進行疑難排解的指引。  

## <a name="understanding-bitlocker"></a>瞭解 BitLocker

BitLocker 磁片磁碟機加密是 Microsoft Windows 作業系統所提供的一項服務，可讓使用者加密其硬碟上的資料。 BitLocker 支援作業系統磁片磁碟機、卸載式媒體磁片磁碟機和固定資料磁片磁碟機的加密。 BitLocker 也支援使用256位加密，以提供更佳的機密資料保護。  

有了 Microsoft Intune，您可以使用下列方法來管理 Windows 10 裝置上的 BitLocker：

- **裝置設定原則**-當您建立裝置設定檔以管理 endpoint protection 時，Intune 中會提供某些內建原則選項。 若要尋找這些選項，請[建立 endpoint protection 的裝置設定檔](endpoint-protection-configure.md#create-a-device-profile-containing-endpoint-protection-settings)，為*平臺*選取**windows 10 和更新版本**，然後選取 [ **windows 加密**] 類別以進行*設定*。 

   您可以在這裡閱讀有關可用選項和功能的資訊： [Windows 加密](https://docs.microsoft.com/intune/endpoint-protection-windows-10#windows-encryption)。

- **安全性基準** - [安全性基準](security-baselines.md)是已知的設定群組，以及相關安全性小組建議的預設值，以協助保護 Windows 裝置的安全。 不同的基準來源（例如*MDM 安全性基準*或*Microsoft Defender ATP 基準*）可以管理與彼此不同的設定。 他們也可以管理您使用裝置設定原則管理的相同設定。 

除了 Intune 以外，BitLocker 設定也可能透過其他方式（例如群組原則）來管理，或由裝置使用者手動設定。

無論如何將設定套用至裝置，BitLocker 原則都會使用[BITLOCKER CSP](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp)來設定裝置上的加密。 BitLocker CSP 內建于 Windows 中，當 Intune 將 BitLocker 原則部署到指派的裝置時，它是裝置上的 BitLocker CSP，可將適當的值寫入 Windows 登錄，讓原則的設定生效。

如果您想要深入瞭解 BitLocker，請參閱下列資源：

- [BitLocker](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview)
- [BitLocker 總覽和需求常見問題](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview-and-requirements-faq)

既然您已大致瞭解這些原則的作用及其使用方式，請查看如何確認 BitLocker 設定是否成功套用至 Windows 用戶端。

## <a name="verify-the-source-of-bitlocker-settings"></a>確認 BitLocker 設定的來源

當您調查 Windows 10 裝置上的 BitLocker 問題時，請務必先判斷問題是否與 Intune 相關或與 Windows 相關。 已知失敗的來源之後，您可以將疑難排解工作放在正確的位置，並在必要時從正確的小組取得支援。  

第一個步驟是判斷 Intune 原則是否已成功部署到目標裝置。 在下列範例中，您具有部署 Windows 加密（BitLocker）設定的裝置設定原則，如下所示：

![具有設定的 Windows 加密裝置設定原則](./media/troubleshooting-bitlocker-policies/settings.png)

如何確認設定已套用至目標裝置？ 以下是幾個執行此動作的方法。

### <a name="device-configuration-policy-device-status"></a>裝置設定原則裝置狀態  

當您使用裝置設定原則來設定 BitLocker 時，您可以在 Intune 入口網站中檢查原則的狀態。

1. 登入 [Microsoft 端點管理員系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。

2. 選取 [**裝置**] > [**設定檔**]，然後選取包含 BitLocker 設定的設定檔。

3. 選取您想要查看的設定檔之後，請選取 [**裝置狀態**]。 系統會列出指派給設定檔的裝置，而 [*裝置狀態*] 欄會指出裝置是否已成功部署設定檔。

請記住，接收 BitLocker 原則的裝置與要完全加密的磁片磁碟機之間可能會有延遲。  

### <a name="use-control-panel-on-the-client"></a>在用戶端上使用控制台  

在啟用 BitLocker 和加密磁片磁碟機的裝置上，您可以從 [裝置] 控制台查看 BitLocker 狀態。 在裝置上，開啟 **控制台** > **系統及安全性** > **BitLocker 磁碟機加密**。 如下圖所示的確認隨即出現。  

![開啟控制台中的 BitLocker](./media/troubleshooting-bitlocker-policies/control-panel.png)

### <a name="use-a-command-prompt"></a>使用命令提示字元  

在已啟用 BitLocker 並已加密磁片磁碟機的裝置上，以系統管理員認證啟動命令提示字元，然後執行 `manage-bde -status`。 結果應類似下列範例：  
![A status 命令](./media/troubleshooting-bitlocker-policies/command.png) 的結果

在下列範例中：

- **BitLocker 保護**已**開啟**
- 已**加密的百分比**為**100%**
- **加密方法**為**XTS-AES 256**

您也可以執行下列命令來檢查**金鑰保護**裝置：

```cmd
Manage-bde -protectors -get c:
```

或者使用 PowerShell：

```powershell
Confirm-SecureBootUEFI
```

### <a name="review-the-devices-registry-key-configuration"></a>檢查裝置登錄機碼設定

在 BitLocker 原則成功部署至裝置之後，請在裝置上查看下列登錄機碼，您可以在其中查看 BitLocker 設定的設定： *HKEY_LOCAL_MACHINE \software\microsoft\policymanager\current\device\bitlocker*。 範例如下：

![BitLocker 登錄機碼](./media/troubleshooting-bitlocker-policies/registry.png)

這些值是由 BitLocker CSP 所設定。 確認索引鍵的值符合 Intune Windows 加密原則來源中指定的設定。 如需每個設定的詳細資訊，請參閱[BITLOCKER CSP](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp)。

> [!NOTE]
> Windows 事件檢視器也會包含與 Bitlocker 相關的各種資訊。 這裡的清單太多，但搜尋**BITLOCKER API**將提供許多有用的資訊。

### <a name="check-the-mdm-diagnostics-report"></a>檢查 MDM 診斷報告

在已啟用 BitLocker 的裝置上，您可以從目標裝置產生並查看 MDM 診斷報告，以確認 BitLocker 原則是否存在。 如果您可以看到報告中的原則設定，這是另一個指出原則已成功部署的指示。 下列連結中的*Microsoft 協助*影片說明如何從 Windows 裝置捕獲 MDM 診斷報告。

> [!VIDEO https://www.youtube.com/embed/WKxlcjV4TNE]

當您分析 MDM 診斷報告時，內容一開始可能有點令人困惑。 以下範例顯示如何將報表中的內容與原則中的設定相互關聯：

![MDM 診斷報告範例](./media/troubleshooting-bitlocker-policies/report.png)

輸出結果會顯示與您 BitLocker 原則中的值對應的值：

![輸出結果顯示值 ](./media/troubleshooting-bitlocker-policies/output.png)

MDM 診斷輸出結果：

```asciidoc
EncryptionMethodWithXtsOsDropDown: 7 (The value 7 refers to the 256 bit encryption)
EncryptionMethodWithXtsFdvDropDown: 6 (The value 6 refers to the 128 bit encryption)
EncryptionMethodWithXtsRdvDropDown: 6 (The value 6 refers to the 128 bit encryption)
```

您可以參考[BITLOCKER CSP 檔](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp)，以瞭解每個值的意義。 在此範例中，會在下圖中共用程式碼片段。

![值的用途](./media/troubleshooting-bitlocker-policies/shared-example.png)

同樣地，您可以查看所有的值，並從 BitLocker CSP 連結進行驗證。

> [!TIP]
> MDM 診斷報告的主要目的是在針對問題進行疑難排解時，協助 Microsoft 支援服務。 如果您開啟 Intune 的支援案例，而問題牽涉到 Windows 用戶端，則收集這份報表並將其納入您的支援要求中，是個不錯的主意。

## <a name="troubleshooting-bitlocker-policy"></a>疑難排解 BitLocker 原則

您現在應該已瞭解如何確認 Intune 已成功部署 BitLocker 原則，這會將 BitLocker 的設定交給 WIndows 中的 BitLocker CSP。

**原則無法連線到裝置**-當您的 Intune 原則不存在於任何容量中時：

- **裝置是否已正確註冊到 Microsoft Intune？** 如果不是，您必須先解決此問題，再疑難排解原則特定的任何專案。 您可以在[這裡](../enrollment/troubleshoot-windows-enrollment-errors.md)找到疑難排解 Windows 註冊問題的協助。

- **裝置上是否有作用中的網路連線？** 如果裝置處於飛機模式或已關閉，或使用者在沒有服務的位置中有裝置，則在還原網路連線之前，不會傳送或套用原則。

- **BitLocker 原則是否部署到正確的使用者或裝置群組？** 檢查正確的使用者或裝置是否為您的目標群組的成員。

**原則存在，但並非所有設定都已成功**-當您的 Intune 原則到達裝置時，但未設定所有設定：

- **整個原則的部署是否失敗，或是否只有不適用的特定設定？** 如果您發現自己遇到只有部分原則設定不適用的案例，請檢查下列考慮：

  1. **並非所有 Windows 版本都支援所有 BitLocker 設定**。
     原則會以單一單位的形式提供給裝置，因此，如果有些設定適用，而其他則不是，則您可以確信已收到原則本身。 在此案例中，裝置上的 Windows 版本可能不支援有問題的設定。 如需每個設定的版本需求詳細資料，請參閱 Windows 檔中的[BITLOCKER CSP](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp) 。

  2. **並非所有硬體都支援 BitLocker**。
     即使您有正確版本的 Windows，基礎裝置硬體仍可能不符合 BitLocker 加密的需求。 您可以在 Windows 檔中找到[BitLocker 的系統需求](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview#system-requirements)，但要檢查的主要事項是裝置具有相容的 TPM 晶片（1.2 或更新版本）和受信任運算群組（TCG）相容的 BIOS 或 UEFI 固件。

**範例調查**

- 您會將 BitLocker 原則部署到 Windows 10 裝置，而 [**加密裝置**] 設定會在入口網站中顯示 [**錯誤**] 狀態。

- 如其名所示，這項設定可讓系統管理員使用*BitLocker > 裝置加密*來開啟加密。 使用稍早所述的疑難排解秘訣，您會先檢查 MDM 診斷報告。 此報告會確認裝置上已部署正確的原則：

  ![報表確認裝置上已部署正確的原則](./media/troubleshooting-bitlocker-policies/mdm-report.png)

- 您也會在登錄中確認成功：

  ![RequiredDeviceEncryption 登錄值顯示1](./media/troubleshooting-bitlocker-policies/registry-confirm.png)

- 接下來，您會使用 PowerShell 檢查 TPM 的狀態，並找出該 TPM 在裝置上無法使用：

  ![使用 PowerShell 檢查 TPM 狀態](./media/troubleshooting-bitlocker-policies/tpm-command.png)

- 因為 BitLocker 會依賴 TPM，所以您可以結束 BitLocker 不會因為 Intune 或原則的問題而失敗，而是因為裝置本身沒有 TPM 晶片，或是在 BIOS 中停用 TPM。

  另一個秘訣是，您可以在 Windows 事件檢視器的 [**應用程式和服務**] [Log > **WINDOWS** > **BitLocker API**] 下確認相同的提示。 在**BITLOCKER API**事件記錄檔中，您會發現事件識別碼853，表示 TPM 無法使用：

  ![事件識別碼 853](./media/troubleshooting-bitlocker-policies/event-error.png)

  > [!NOTE]
  > 您也可以在裝置上執行**tpm** ，以檢查 tpm 狀態。

## <a name="summary"></a>[摘要]

當您針對 Intune 的 BitLocker 原則問題進行疑難排解，並可確認原則是否達到預定的裝置時，可以安全地假設問題與 Intune 不直接相關。 問題很可能是 Windows OS 或硬體的問題。 在此情況下，請開始查看其他區域，例如 TPM 設定或 UEFI 和安全開機）。

## <a name="next-steps"></a>後續步驟  

以下是使用 BitLocker 時可能有説明的更多資源：

- [BitLocker 產品檔](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview)
- [BitLocker 系統需求](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview#system-requirements)
- [BitLocker 常見問題集](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-frequently-asked-questions)
- [BitLocker CSP 檔](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp)
- [Intune Windows 加密原則設定](https://docs.microsoft.com/intune/endpoint-protection-windows-10#windows-encryption)
- [使用 AAD/MDM 的硬體獨立自動 BitLocker 加密](https://blogs.technet.microsoft.com/home_is_where_i_lay_my_head/2017/06/07/hardware-independent-automatic-bitlocker-encryption-using-aadmdm/)
- [自動試驗裝置上 BitLocker 加密的 CSP 原則](https://techcommunity.microsoft.com/t5/Windows-10-security/CSP-policy-for-bitLocker-encryption-on-autopilot-devices/m-p/284537)
- [逐步解說使用 Intune 建立和部署 BitLocker 原則](https://blogs.technet.microsoft.com/cbernier/2017/07/11/windows-10-intune-windows-bitlocker-management-yes/)
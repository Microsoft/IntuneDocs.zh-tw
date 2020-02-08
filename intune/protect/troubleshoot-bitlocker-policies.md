---
title: 適用於 Microsoft Intune 中 BitLocker 原則的疑難排解祕訣
titleSuffix: Microsoft Intune
description: 說明如何使用 Intune 原則在裝置上啟用 BitLocker 加密，以及如何確認您的原則是否已成功部署到裝置。
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/29/2020
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
ms.openlocfilehash: 61b703837598ddbe2c0c44874928b4444466c811
ms.sourcegitcommit: 5ad0ce27a30ee3ef3beefc46d2ee49db6ec0cbe3
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2020
ms.locfileid: "76886775"
---
# <a name="troubleshoot-bitlocker-policies-in-microsoft-intune"></a>針對 Microsoft Intune 中的 BitLocker 原則進行疑難排解

此文章可協助 Intune 系統管理員了解 Windows 10 裝置如何根據 Intune 原則來設定 BitLocker。 此文章也提供如何針對使用 Intune 管理之裝置上的 BitLocker 設定問題進行疑難排解的指導方針。  

## <a name="understanding-bitlocker"></a>了解 BitLocker

BitLocker 磁碟機加密是 Microsoft Windows 作業系統所提供的服務，可讓使用者加密其硬碟上的資料。 BitLocker 支援作業系統磁碟機、抽取式媒體磁碟機與固定式資料磁碟機的加密。 BitLocker 也支援使用 256 位元加密，以提供更棒的機密資料保護。  

使用 Microsoft Intune，您可以透過下列方法來管理 Windows 10 裝置上的 BitLocker：

- **裝置設定原則** - 當您建立裝置組態設定檔以管理端點保護時，Intune 中會提供一些內建原則選項。 若要尋找這些選項，請[建立端點保護的裝置設定檔](endpoint-protection-configure.md#create-a-device-profile-containing-endpoint-protection-settings)、針對 [平台]  選取 [Windows 10 和更高版本]  ，然後針對 [設定]  選取 [Windows 加密]  類別。 

   您可以在這裡閱讀可用選項與功能的相關資訊：[Windows 加密](https://docs.microsoft.com/intune/endpoint-protection-windows-10#windows-encryption)。

- **安全性基準** - [安全性基準](security-baselines.md)是設定和預設值的已知群組，由相關安全性小組建議，以協助保護 Windows 裝置的安全。 不同的基準來源 (例如 *MDM 安全性基準*或 *Microsoft Defender ATP 基準*) 可以管理相同的設定以及彼此不同的設定。 它們也可以管理您使用裝置設定原則管理的相同設定。 

除了 Intune 以外，BitLocker 設定也可能透過其他方式 (例如群組原則) 來管理，或由裝置使用者手動設定。

無論將設定套用至裝置的方式為何，BitLocker 原則都會使用 [BitLocker CSP](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp) 來設定裝置上的加密。 BitLocker CSP 內建於 Windows 中，而當 Intune 將 BitLocker 原則部署到指派的裝置時，是裝置上的 BitLocker CSP 將適當的值寫入 Windows 登錄，原則中的設定才能生效。

如果您想要深入了解 BitLocker，請參閱下列資源：

- [BitLocker](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview)
- [BitLocker 概觀與需求常見問題集](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview-and-requirements-faq) \(部分機器翻譯\)

既然您已大致了解這些原則的作用與其使用方式，請查看如何確認 BitLocker 設定是否成功套用至 Windows 用戶端。

## <a name="verify-the-source-of-bitlocker-settings"></a>確認 BitLocker 設定的來源

當您調查 Windows 10 裝置上的 BitLocker 問題時，請務必先判斷問題是與 Intune 相關或與 Windows 相關。 在知道可能的失敗來源之後，您可以將疑難排解工作集中在正確的位置，並在必要時從正確的小組取得支援。  

第一個步驟是判斷 Intune 原則是否已成功部署到目標裝置。 在下列範例中，您有會部署 Windows 加密 (BitLocker) 設定的裝置設定原則，如下所示：

![具有設定的 Windows 加密裝置設定原則](./media/troubleshooting-bitlocker-policies/settings.png)

如何確認設定已套用至目標裝置？ 以下是幾個執行該動作的方法。

### <a name="device-configuration-policy-device-status"></a>裝置設定原則裝置狀態  

當您使用裝置設定原則來設定 BitLocker 時，您可以在 Intune 入口網站中檢查原則的狀態。

1. 登入 [Microsoft 端點管理員系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。

2. 選取 [裝置]   > [組態設定檔]  ，然後選取包含 BitLocker 設定的設定檔。

3. 選取您想要檢視的設定檔之後，請選取 [裝置狀態]  。 系統會列出指派給設定檔的裝置，而 [裝置狀態]  欄會指出裝置是否已成功部署設定檔。

請記住，接收 BitLocker 原則的裝置與完全加密的磁碟機之間可能會有延遲。  

### <a name="use-control-panel-on-the-client"></a>在用戶端上使用控制台  

在已啟用 BitLocker 且已加密磁碟機的裝置上，您可以從裝置 [控制台] 檢視 BitLocker 狀態。 在裝置上，開啟 [控制台]   > [系統及安全性]   > [BitLocker 磁碟機加密]  。 確認隨即出現，如下圖所示。  

![控制台中的 BitLocker 已開啟](./media/troubleshooting-bitlocker-policies/control-panel.png)

### <a name="use-a-command-prompt"></a>使用命令提示字元  

在已啟用 BitLocker 且已加密磁碟機的裝置上，使用系統管理員認證啟動 [命令提示字元]，然後執行 `manage-bde -status`。 結果應類似下列範例：  
![A status 命令](./media/troubleshooting-bitlocker-policies/command.png) 的結果

在下列範例中：

- [BitLocker 保護]  為 [開啟] 
- [加密的百分比]  為 [100%] 
- [加密方法]  為 [XTS-AES 256] 

您也可以執行下列命令來檢查**金鑰保護裝置**：

```cmd
Manage-bde -protectors -get c:
```

或者使用 PowerShell：

```powershell
Confirm-SecureBootUEFI
```

### <a name="review-the-devices-registry-key-configuration"></a>檢閱裝置登錄機碼設定

在 BitLocker 原則成功部署至裝置之後，請在裝置上檢視下列登錄機碼，其中您可以檢閱 BitLocker 設定的組態：*HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\PolicyManager\current\device\BitLocker*。 範例如下：

![BitLocker 登錄機碼](./media/troubleshooting-bitlocker-policies/registry.png)

這些值是由 BitLocker CSP 設定的。 確認機碼值符合 Intune Windows 加密原則來源中指定的設定。 如需每個設定的詳細資訊，請參閱 [BitLocker CSP](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp) \(部分機器翻譯\)。

> [!NOTE]
> Windows 事件檢視器也會包含與 Bitlocker 相關的各種資訊。 有太多內容無法在這裡一一列出，但是搜尋 **Bitlocker API** 將提供您許多有用的資訊。

### <a name="check-the-mdm-diagnostics-report"></a>檢查 MDM 診斷報告

在已啟用 BitLocker 的裝置上，您可以從目標裝置產生 MDM 診斷報告並檢視，以確認 BitLocker 原則存在。 如果您可以看到報告中的原則設定，則表示該原則已成功部署。 下列連結中的 Microsoft 協助  影片說明如何從 Windows 裝置擷取 MDM 診斷報告。

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

您可以參考 [BitLocker CSP 文件](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp) \(部分機器翻譯\)，以了解每個值的意義。 在此範例中，會在下圖中共用程式碼片段。

![值的用途](./media/troubleshooting-bitlocker-policies/shared-example.png)

同樣地，您可以查看所有的值，並從 BitLocker CSP 連結加以確認。

> [!TIP]
> MDM 診斷報告的主要目的是在針對問題進行疑難排解時，協助 Microsoft 支援服務。 如果您建立 Intune 的支援案例，而問題牽涉到 Windows 用戶端，則收集此報表並將其納入您的支援要求中，是個不錯的主意。

## <a name="troubleshooting-bitlocker-policy"></a>針對 BitLocker 原則進行疑難排解

您現在應該已了解如何確認 Intune 已成功部署 BitLocker 原則，Intune 會將 BitLocker 的設定交給 WIndows 中的 BitLocker CSP。

**原則無法連線到裝置** - 當您的 Intune 原則不存在於任何容量中時：

- **裝置是否已正確註冊到 Microsoft Intune？** 如果不是，您必須先解決此問題，再針對原則特定的任何項目進行疑難排解。 您可以在[這裡](../enrollment/troubleshoot-windows-enrollment-errors.md)找到針對 Windows 註冊問題進行疑難排解的協助。

- **裝置上是否有作用中的網路連線？** 如果裝置處於飛航模式或已關閉，或使用者讓裝置處在沒有服務的位置中，則在網路連線還原之前，不會傳遞或套用原則。

- **BitLocker 原則是否部署到正確的使用者或裝置群組？** 檢查正確的使用者或裝置是否為您的目標群組的成員。

**原則存在，但並非所有設定都已成功** - 當您的 Intune 原則連線到裝置，但未設定所有組態時：

- **整個原則的部署失敗，或只有特定的設定不適用？** 如果您發現自己遇到只有部分原則設定不適用的案例，請確認下列考量：

  1. **並非所有 Windows 版本都支援所有 BitLocker 設定**。
     原則會以單一單位的形式提供給裝置，因此，如果有些設定適用，而有些則不適用，您可以確信已收到原則本身。 在此案例中，裝置上的 Windows 版本可能不支援有問題的設定。 如需每個設定的版本需求詳細資料，請參閱 Windows 文件中的 [BitLocker CSP](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp) \(部分機器翻譯\)。

  2. **並非所有硬體都支援 BitLocker**。
     即使您有正確版本的 Windows，基礎裝置硬體仍可能不符合 BitLocker 加密的需求。 您可以在 Windows 文件中找到 [BitLocker 的系統需求](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview#system-requirements) \(部分機器翻譯\)，但要檢查的主要事項是裝置具有相容的 TPM 晶片 (1.2 或更新版本) 和信賴運算群組 (TCG) 相容的 BIOS 或 UEFI 韌體。

**範例調查**

- 您會將 BitLocker 原則部署到 Windows 10 裝置，而 [加密裝置]  設定會在入口網站中顯示 [錯誤]  狀態。

- 如其名所示，此設定可讓系統管理員使用 [BitLocker] > [裝置加密]  來要求開啟加密。 使用稍早所述的疑難排解祕訣，您首先要檢查 MDM 診斷報告。 此報告會確認裝置上已部署正確的原則：

  ![報表確認裝置上已部署正確的原則](./media/troubleshooting-bitlocker-policies/mdm-report.png)

- 您也可在登錄中確認是否成功：

  ![RequiredDeviceEncryption 登錄值顯示 1](./media/troubleshooting-bitlocker-policies/registry-confirm.png)

- 接下來，您會使用 PowerShell 檢查 TPM 的狀態，並發現該 TPM 在裝置上無法使用：

  ![使用 PowerShell 檢查 TPM 狀態](./media/troubleshooting-bitlocker-policies/tpm-command.png)

- 由於 BitLocker 仰賴 TPM，因此您可以得出的結論是，BitLocker 不會因為 Intune 或原則問題而失敗，而是因為裝置本身沒有 TPM 晶片或在 BIOS 中停用了 TPM。

  另一個祕訣是，您可以在 [應用程式和服務記錄檔]   > [Microsoft]   > [Windows]   > [BitLocker API]  下的 [Windows 事件檢視器] 中確認同樣的事。 在 **BitLocker API** 事件記錄檔中，您會發現事件識別碼 853，表示 TPM 無法使用：

  ![事件識別碼 853](./media/troubleshooting-bitlocker-policies/event-error.png)

  > [!NOTE]
  > 您也可以在裝置上執行 **tpm.msc**，以檢查 TPM 狀態。

## <a name="summary"></a>[摘要]

當您針對 Intune 的 BitLocker 原則問題進行疑難排解，並可確認原則連線到預定的裝置時，便可以安全地假設問題與 Intune 沒有直接關係。 問題很可能是 Windows OS 或硬體的問題。 在此情況下，請開始查看其他區域，例如 TPM 設定或 UEFI 和安全開機。

## <a name="next-steps"></a>後續步驟  

以下是在使用 BitLocker 時可能會有所幫助的更多資源：

- [BitLocker 產品文件](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview) \(部分機器翻譯\)
- [BitLocker 系統需求](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview#system-requirements) \(部分機器翻譯\)
- [BitLocker 常見問題集](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-frequently-asked-questions)
- [BitLocker CSP 文件](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp) \(部分機器翻譯\)
- [Intune Windows 加密原則設定](https://docs.microsoft.com/intune/endpoint-protection-windows-10#windows-encryption) \(部分機器翻譯\)
- [使用 AAD/MDM 的硬體獨立自動 BitLocker 加密](https://blogs.technet.microsoft.com/home_is_where_i_lay_my_head/2017/06/07/hardware-independent-automatic-bitlocker-encryption-using-aadmdm/) \(英文\)
- [適用於 Auto-Pilot 裝置上 BitLocker 加密的 CSP 原則](https://techcommunity.microsoft.com/t5/Windows-10-security/CSP-policy-for-bitLocker-encryption-on-autopilot-devices/m-p/284537) \(英文\)
- [逐步解說使用 Intune 建立及部署 BitLocker 原則](https://blogs.technet.microsoft.com/cbernier/2017/07/11/windows-10-intune-windows-bitlocker-management-yes/) \(英文\)
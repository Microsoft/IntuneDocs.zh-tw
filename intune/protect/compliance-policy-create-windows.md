---
title: Microsoft Intune 中的 Windows 10 相容性設定 - Azure | Microsoft Docs
description: 查看您在 Microsoft Intune 中為 Windows 10、Windows 全像攝影版、Surface Hub 裝置設定相容性時，能夠使用的所有設定清單。 檢查最小和最大作業系統上的相容性、設定密碼限制和長度、檢查合作夥伴防毒程式 (AV) 解決方案、啟用資料儲存區加密等。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/12/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 484035603e4fb447b004aad6c6f85726034f3c23
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2019
ms.locfileid: "71732824"
---
# <a name="windows-10-and-later-settings-to-mark-devices-as-compliant-or-not-compliant-using-intune"></a>使用 Intune，透過 Windows 10 及更新版本的設定將裝置標示為相容或不相容

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

本文列出及描述您可在 Intune 中 Windows 10 及更新版本裝置上設定的不同相容性設定。 作為您行動裝置管理 (MDM) 解決方案的一部分，請使用這些設定來要求 BitLocker、設定最低及最高的作業系統、使用 Microsoft Defender 進階威脅防護 (ATP) 設定風險層級等。

本功能適用於：

- Windows 10 及更新版本
- Windows Holographic for Business
- Surface Hub

身為 Intune 管理員，請使用這些相容性設定來協助保護您的組織資源。 若要深入了解相容性原則及其執行的操作，請參閱[開始使用裝置相容性](device-compliance-get-started.md)。

## <a name="before-you-begin"></a>開始之前

[建立合規性政策](create-compliance-policy.md#create-the-policy)。 針對 [平台]  ，選取 [Windows 10 及更新版本]  。

## <a name="device-health"></a>Device health

- [要求 BitLocker]  ：當設為 [要求]  時，裝置便能保護儲存在磁碟機上的資料，使其在系統關閉或是休眠時不受未經授權的存取。 Windows BitLocker 磁碟機加密會加密儲存在 Windows 作業系統磁碟區上的所有資料。 BitLocker 使用 TPM 協助保護 Windows 作業系統和使用者資料。 即使該電腦處於無人看管、遺失或遭竊的情況，它也能協助確保電腦不受竄改。 如果電腦配備相容的 TPM，BitLocker 會使用 TPM 來鎖定可保護資料的加密金鑰。 因此，必須等到 TPM 驗證電腦的狀態之後，才能存取金鑰。

  當設為 [未設定]  (預設) 時，便不會針對相容性或非相容性評估此設定。

- [要求在裝置上啟用安全開機]  ：當設為 [要求]  時，便會強制系統開機進入原廠信任狀態。 當啟用時，用來啟動電腦之核心元件便必須擁有製造裝置組織所信任的正確密碼編譯簽章。 UEFI 韌體會在讓電腦啟動之前先驗證簽章。 如果有任何檔案遭到竄改 (這會中斷它們的簽章)，系統就不會開機。

  當設為 [未設定]  (預設) 時，便不會針對相容性或非相容性評估此設定。

  > [!NOTE]
  > 某些 TPM 1.2 和 2.0 裝置支援 [要求在裝置上啟用安全開機]  設定。 針對不支援 TPM 2.0 或更新版本的裝置，Intune 中的原則狀態會顯示為 [不符合規範]  。 如需支援版本的詳細資訊，請參閱[裝置健全狀況證明](https://docs.microsoft.com/windows/security/information-protection/tpm/trusted-platform-module-overview#device-health-attestation)。

- **要求程式碼完整性**：程式碼完整性是一種功能，可在每次將驅動程式或系統檔案載入記憶體時驗證其完整性。 當設為 [需要]  時，程式碼完整性便會偵測是否正在將未簽署的驅動程式或系統檔案載入核心。 它也會偵測是否有透過具系統管理員權限使用者帳戶執行的惡意軟體變更了系統檔案。

  當設為 [未設定]  (預設) 時，便不會針對相容性或非相容性評估此設定。

其他資源：

- 如需 HAS 服務如何運作的詳細資料，請參閱 [Health Attestation CSP](https://docs.microsoft.com/windows/client-management/mdm/healthattestation-csp) (健全狀況證明 CSP)。
- [支援提示：使用裝置健康情況證明設定，作為您 Intune 合規性政策的一部分](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Using-Device-Health-Attestation-Settings-as-Part-of/ba-p/282643) \(英文\)

## <a name="device-properties"></a>裝置內容

- **最低 OS 版本**：輸入允許的最低版本 (格式為 **major.minor.build.CU 編號**)。 若要取得正確值，請開啟命令提示字元，然後鍵入 `ver`。 `ver` 命令會傳回格式如下的版本：

  `Microsoft Windows [Version 10.0.17134.1]`

  當裝置版本比您輸入的 OS 版本更早時，就會回報為不符合規範。 您會看到如何升級的資訊連結。 終端使用者可以選擇升級其裝置。 當他們升級之後，就能存取公司資源。

- **最高 OS 版本**：輸入允許的最高版本 (格式為 **major.minor.build.revision 編號**)。 若要取得正確值，請開啟命令提示字元，然後鍵入 `ver`。 `ver` 命令會傳回格式如下的版本：

  `Microsoft Windows [Version 10.0.17134.1]`

  當裝置正在使用的 OS 版本比所輸入的版本更新時，便會封鎖其對組織資源的存取。 系統會要求終端使用者連絡其 IT 管理員。 直到規則變更為允許該 OS 版本前，裝置都無法存取組織資源。

- **針對行動裝置所需的最低 OS**：輸入允許的最低版本 (格式為 major.minor.build 編號格式)。

  當裝置版本比您輸入的 OS 版本更早時，就會回報為不符合規範。 您會看到如何升級的資訊連結。 終端使用者可以選擇升級其裝置。 當他們升級之後，就能存取公司資源。

- **針對行動裝置所需的最高 OS**：輸入允許的最高版本 (編號格式為 major.minor.build)。

  當裝置正在使用的 OS 版本比所輸入版本更新時，便會封鎖其對組織資源的存取。 系統會要求終端使用者連絡其 IT 管理員。 直到規則變更為允許該 OS 版本前，裝置都無法存取組織資源。

- **有效的作業系統組建**：輸入可接受的作業系統版本範圍，包括最低和最高。 您也可以將這些可接受的 OS 組建編號清單**匯出**逗號分隔值 (CSV) 檔案。

## <a name="configuration-manager-compliance"></a>Configuration Manager 合規性

僅適用於執行 Windows 10 和更新版本的共同受控裝置。 僅 Intune 的裝置會傳回無法使用的狀態。

- [向來自 System Center Configuration Manager 的設定要求裝置相容性]  ：選擇 [要求]  以強制 System Center Configuration Manager 中的所有設定 (設定項目) 具備相容性。 

  例如，您需要在裝置上安裝所有軟體更新。 在 Configuration Manager 中，此要求將會對應「已安裝」狀態。 如果裝置上的任何程式處於未知狀態，則裝置在 Intune 中就不會符合規範。
  
  如果**未設定**，Intune 就不會針對合規性檢查任何 Configuration Manager 設定。

## <a name="system-security"></a>系統安全性

### <a name="password"></a>密碼

- **需要密碼才可解除鎖定行動裝置**：**要求**使用者必須輸入密碼以存取其裝置。 **未設定**時，Intune 不會評估裝置是否符合合規性的密碼設定。
- **簡單密碼**：設定為 [封鎖]  時，使用者將無法建立 **1234** 或 **1111** 之類的簡單密碼。 設定為 [未設定]  時，使用者可以建立 **1234** 或 **1111** 之類的密碼。
- **密碼類型**：選擇需要的密碼或 PIN 類型。 選項包括：

  - **裝置預設**：需要密碼、數位 pin 或英數位元 pin
  - **數值**：需要密碼或數位 PIN
  - 英**數位**元：需要密碼或英數位元 PIN。 也請選擇**密碼複雜度**： 
    
    - **需要數位和小寫字母**
    - **需要數位、小寫字母和大寫字母**
    - **需要數字、小寫字母、大寫字母及特殊字元**

    > [!TIP]
    > 英數位元密碼原則可能很複雜。 我們鼓勵系統管理員閱讀 Csp 以取得詳細資訊：
    >
    > - [DeviceLock/AlphanumericDevicePasswordRequired CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock#devicelock-alphanumericdevicepasswordrequired)
    > - [DeviceLock/MinDevicePasswordComplexCharacters CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock#devicelock-mindevicepasswordcomplexcharacters)

- **最小密碼長度**：輸入密碼至少須包含的位數或字元數。
- **停止活動幾分鐘後需要輸入密碼**：輸入在閒置多久後，使用者必須重新輸入密碼。
- **密碼到期 (天數)** ：輸入密碼到期且必須建立新密碼前的天數 (從 1 到 730)。
- **避免重複使用前幾個密碼**：輸入不可使用先前所使用的多少個密碼。
- **於裝置從閒置狀態回復時要求密碼 (行動裝置版和 Holographic)** ：強制使用者於每次裝置從閒置狀態回復時輸入密碼。

  > [!IMPORTANT]
  > 在 Windows 桌面上變更密碼需求時，使用者會在下次登入時受到影響，因為此時裝置會從閒置變成作用中。 系統仍會提示密碼符合需求的使用者變更其密碼。

### <a name="encryption"></a>加密

- **對裝置上的資料存放區加密**：選擇 [需要]  來將裝置上的資料存放區加密。

  > [!NOTE]
  > [裝置上的資料儲存區加密]  設定通常會檢查裝置上是否有加密。 如需更強固的加密設定，請考慮使用 [要求 Bitlocker]  ，這會利用 Windows 運作狀況證明在 TPM 層級驗證 Bitlocker 狀態。

### <a name="device-security"></a>裝置安全性

- **防火牆**：設定為 [**需要**] 以開啟 Microsoft Defender 防火牆，並防止使用者將它關閉。 [**未設定**] （預設）不會控制 Microsoft Defender 防火牆，也不會變更現有的設定。

  [防火牆 CSP](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp)

- **信賴平臺模組（TPM）** ：當設定為 [**需要**] 時，Intune 會檢查版本是否符合規範。 如果 TPM 晶片版本大於0（零），則裝置相容。 如果裝置上沒有 TPM 版本，則裝置不相容。 **未設定**時，Intune 不會檢查裝置是否有 TPM 晶片版本。

  [DeviceStatus CSP-DeviceStatus/TPM/SpecificationVersion 節點](https://docs.microsoft.com/windows/client-management/mdm/devicestatus-csp)
  
- **防毒**：當設定為 [必要]  時，您可以使用向 [Windows 資訊安全中心](https://blogs.windows.com/windowsexperience/2017/01/23/introducing-windows-defender-security-center/) \(英文\) 註冊的防毒解決方案 (例如 Symantec 和 Microsoft Defender) 來檢查合規性。 **未設定**時，Intune 不會檢查裝置上是否有任何安裝的 AV 解決方案。
- **反間諜功能**：當設定為 [必要]  時，您可以使用向 [Windows 資訊安全中心](https://blogs.windows.com/windowsexperience/2017/01/23/introducing-windows-defender-security-center/) \(英文\) 註冊的反間諜功能解決方案 (例如 Symantec 和 Microsoft Defender) 來檢查合規性。 **未設定**時，Intune 不會檢查裝置上是否有任何安裝的反間諜軟體解決方案。

### <a name="defender"></a>Defender

- **Microsoft Defender 反惡意**代碼：設定為 [**需要**] 以開啟 Microsoft Defender 反惡意程式碼服務，並防止使用者將其關閉。 [**未設定**] （預設）不會控制服務，也不會變更現有的設定。
- **Microsoft Defender 反惡意程式碼最小版本**：輸入最小允許版本的 microsoft defender 反惡意程式碼服務。 例如，輸入 `4.11.0.0`。 保留空白時，可以使用任何版本的 Microsoft Defender 反惡意程式碼服務。
- **Microsoft Defender 反惡意程式碼安全性情報最**新：控制裝置上的 Windows 安全性病毒和威脅防護更新。 [**需要**] 會強制 Microsoft Defender 安全情報保持在最新狀態。 [**未設定**] （預設）不會強制執行任何需求。

  [Microsoft Defender 防毒軟體和其他 microsoft 反惡意程式碼的安全性情報更新](https://www.microsoft.com/en-us/wdsi/defenderupdates)，有更多有關安全性情報的資訊。

- **即時保護**： [**需要**] 會開啟即時保護，這會掃描惡意程式碼、間諜軟體和其他垃圾軟體。 [**未設定**] （預設）不會控制這項功能，也不會變更現有的設定。

  [Defender/AllowRealtimeMonitoring CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowrealtimemonitoring)

## <a name="microsoft-defender-atp"></a>Microsoft Defender ATP

- **要求裝置不高於電腦風險分數**：使用此設定進行來自您防禦威脅服務的風險評估，以作為合規性的條件。 選擇允許的最高威脅層級：

  - **清除**：此選項最安全，因為裝置不能有任何威脅。 若裝置上偵測到任何等級的威脅，便會評估為不相容。
  - **低**︰如果只有低等級的威脅，則會將裝置評估為相容。 任何更高等級的威脅都會使裝置處於不相容狀態。
  - **中**︰如果裝置上的現有威脅是低等級或中等級，則會將裝置評估為符合規範。 若在裝置上偵測到高等級的威脅，便會判斷為不相容。
  - **高**：此選項最不安全，且允許所有威脅層級。 如果此解決方案只用於報告用途，則此設定可能很實用。
  
  若要將 Microsoft Defender ATP (進階威脅防護) 設定為防禦威脅服務，請參閱[使用條件式存取啟用 Microsoft Defender ATP](advanced-threat-protection.md)。

選取 [確定]   > [建立]  儲存您的變更。

## <a name="windows-holographic-for-business"></a>Windows Holographic for Business

Windows Holographic for Business 使用 **Windows 10 及更新版本**平台。 Windows Holographic for Business 支援下列設定：

- [系統安全性]   > [加密]   > [對裝置上的資料存放區加密]  。

若要在 Microsoft HoloLens 上驗證裝置加密，請參閱[驗證裝置加密](https://docs.microsoft.com/hololens/hololens-encryption#verify-device-encryption)。

## <a name="surface-hub"></a>Surface Hub

Surface Hub 使用 **Windows 10 及更新版本**平台。 Surface Hub 支援合規性和條件式存取。 若要在 Surface Hub 上啟用這些功能，我們建議您在 Intune 中[啟用 Windows 10 自動註冊](../enrollment/windows-enroll.md) (需要 Azure Active Directory (Azure AD))，並瞄準 Surface Hub 裝置作為裝置群組。 Surface Hub 需要加入 Azure AD，合規性和條件式存取才能運作。

請參閱[設定 Windows 裝置的註冊](../enrollment/windows-enroll.md)以取得指引。

## <a name="next-steps"></a>後續步驟

- [為不相容的裝置新增動作](actions-for-noncompliance.md)及[使用範圍標籤篩選原則](../fundamentals/scope-tags.md)。
- [監視您的相容性原則](compliance-policy-monitor.md)。
- 請參閱 [Windows 8.1 裝置的相容性原則設定](compliance-policy-create-windows-8-1.md)。

---
title: Microsoft Intune 中的 Windows 10 相容性設定 - Azure | Microsoft Docs
description: 查看您在 Microsoft Intune 中為 Windows 10、Windows 全像攝影版、Surface Hub 裝置設定相容性時，能夠使用的所有設定清單。 檢查最小和最大作業系統上的相容性、設定密碼限制和長度、檢查合作夥伴防毒程式 (AV) 解決方案、啟用資料儲存區加密等。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 12/09/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: samyada
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 60a87340c1a275b8fb878ef2f3891cca23fc9c85
ms.sourcegitcommit: f5108039f0ade52e95ea3ac1da1aa16d02224af3
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 12/09/2019
ms.locfileid: "74946648"
---
# <a name="windows-10-and-later-settings-to-mark-devices-as-compliant-or-not-compliant-using-intune"></a>使用 Intune，透過 Windows 10 及更新版本的設定將裝置標示為相容或不相容

本文列出及描述您可在 Intune 中 Windows 10 及更新版本裝置上設定的不同相容性設定。 作為您行動裝置管理 (MDM) 解決方案的一部分，請使用這些設定來要求 BitLocker、設定最低及最高的作業系統、使用 Microsoft Defender 進階威脅防護 (ATP) 設定風險層級等。

本功能適用於：

- Windows 10 及更新版本
- Windows Holographic for Business
- Surface Hub

身為 Intune 管理員，請使用這些相容性設定來協助保護您的組織資源。 若要深入了解相容性原則及其執行的操作，請參閱[開始使用裝置相容性](device-compliance-get-started.md)。

## <a name="before-you-begin"></a>開始之前

[建立合規性政策](create-compliance-policy.md#create-the-policy)。 針對 [平台]  ，選取 [Windows 10 及更新版本]  。

## <a name="device-health"></a>裝置健全狀況

### <a name="windows-health-attestation-service-evaluation-rules"></a>Windows 健康情況證明服務評估規則

- **要求 BitLocker**：  
   Windows BitLocker 磁碟機加密會加密儲存在 Windows 作業系統磁碟區上的所有資料。 BitLocker 使用可信賴平臺模組（TPM）來協助保護 Windows 作業系統和使用者資料。 即使該電腦處於無人看管、遺失或遭竊的情況，它也能協助確保電腦不受竄改。 如果電腦配備相容的 TPM，BitLocker 會使用 TPM 來鎖定可保護資料的加密金鑰。 因此，必須等到 TPM 驗證電腦的狀態之後，才能存取金鑰。  

   - [未設定]  (預設  ) - 不會評估此設定是否符合規範。
   - [需要]  - 裝置可以保護儲存在磁碟機上的資料，使其在系統關閉或是休眠時免於未經授權的存取。  


- **要求在裝置上啟用安全開機**：  
    - [未設定]  (預設  ) - 不會評估此設定是否符合規範。
    - **需要**-系統強制開機到原廠信任的狀態。 用來啟動電腦的核心元件必須擁有製造裝置組織所信任的正確密碼編譯簽章。 UEFI 韌體會在讓電腦啟動之前先驗證簽章。 如果有任何檔案遭到竄改 (這會中斷它們的簽章)，系統就不會開機。

  > [!NOTE]
  > 某些 TPM 1.2 和 2.0 裝置支援 [要求在裝置上啟用安全開機]  設定。 針對不支援 TPM 2.0 或更新版本的裝置，Intune 中的原則狀態會顯示為 [不符合規範]  。 如需支援版本的詳細資訊，請參閱[裝置健全狀況證明](https://docs.microsoft.com/windows/security/information-protection/tpm/trusted-platform-module-overview#device-health-attestation)。

- **要求程式碼完整性**：  
  程式碼完整性是一種功能，可在每次將驅動程式或系統檔案載入至記憶體時驗證其完整性。
  - [未設定]  (預設  ) - 不會評估此設定是否符合規範。
  -  [需要]  - 需要程式碼完整性，它會偵測是否正在將未簽署的驅動程式或系統檔案載入核心。 它也會偵測是否透過惡意軟體變更了系統檔案，或以具系統管理員權限的使用者帳戶執行了系統檔案。

其他資源：

- 如需健康情況證明服務運作方式的詳細資訊，請參閱[健康情況證明 CSP](https://docs.microsoft.com/windows/client-management/mdm/healthattestation-csp)。
- [Support Tip: Using Device Health Attestation Settings as Part of Your Intune Compliance Policy](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Using-Device-Health-Attestation-Settings-as-Part-of/ba-p/282643) (支援提示：使用裝置健康情況證明設定，作為您 Intune 合規性政策的一部分)。

## <a name="device-properties"></a>裝置內容

### <a name="operating-system-version"></a>作業系統版本

- **最小 OS 版本**：  
  輸入允許的最低版本 (格式為 **major.minor.build.CU number**)。 若要取得正確值，請開啟命令提示字元，然後鍵入 `ver`。 `ver` 命令會傳回格式如下的版本：

  `Microsoft Windows [Version 10.0.17134.1]`

  當裝置版本比您輸入的 OS 版本更早時，就會回報為不符合規範。 您會看到如何升級的資訊連結。 終端使用者可以選擇升級其裝置。 當他們升級之後，就能存取公司資源。

- **最大 OS 版本**：  
  輸入允許的最高版本 (格式為 **major.minor.build.revision number**)。 若要取得正確值，請開啟命令提示字元，然後鍵入 `ver`。 `ver` 命令會傳回格式如下的版本：

  `Microsoft Windows [Version 10.0.17134.1]`

  當裝置正在使用的 OS 版本比所輸入的版本更新時，便會封鎖其對組織資源的存取。 系統會要求終端使用者連絡其 IT 管理員。 直到規則變更為允許該 OS 版本前，裝置都無法存取組織資源。

- **行動裝置所需的最低 OS 版本**：  
  輸入允許的最低版本 (格式為 major.minor.build number)。

  當裝置版本比您輸入的 OS 版本更早時，就會回報為不符合規範。 您會看到如何升級的資訊連結。 終端使用者可以選擇升級其裝置。 當他們升級之後，就能存取公司資源。

- **行動裝置所需的最高 OS 版本**：  
  輸入允許的最高版本 (格式為 major.minor.build number)。

  當裝置正在使用的 OS 版本比所輸入版本更新時，便會封鎖其對組織資源的存取。 系統會要求終端使用者連絡其 IT 管理員。 直到規則變更為允許該 OS 版本前，裝置都無法存取組織資源。

- **有效的作業系統組建**：  
  輸入可接受的作業系統版本範圍，包括最低和最高版本。 您也可以將這些可接受的 OS 組建編號清單**匯出**逗號分隔值 (CSV) 檔案。

## <a name="configuration-manager-compliance"></a>Configuration Manager 合規性

僅適用於執行 Windows 10 和更新版本的共同受控裝置。 僅 Intune 的裝置會傳回無法使用的狀態。

- **需要 System Center Configuration Manager 的裝置合規性**：  
  - [未設定]  (預設  ) - Intune 不會針對合規性檢查任何 Configuration Manager 設定。
  - [需要]  - 需要 System Center Configuration Manager 中的所有設定 (設定項目) 符合規範。  

    例如，您需要在裝置上安裝所有軟體更新。 在 Configuration Manager 中，此要求將會對應「已安裝」狀態。 如果裝置上的任何程式處於未知狀態，則裝置在 Intune 中就不會符合規範。

## <a name="system-security"></a>系統安全性

### <a name="password"></a>密碼

- **需要密碼來解除鎖定行動裝置**：  
  - [未設定]  (預設  ) - 不會評估此設定是否符合規範。
  - [需要]  - 使用者必須輸入密碼，才能存取其裝置。 

- **簡單密碼**：  
  - [**未設定**] （*預設*）-使用者可以建立簡單密碼，例如**1234**或**1111**。
  - [封鎖]  - 使用者無法建立 **1234** 或 **1111** 之類的簡單密碼。

- **密碼類型**：  
  選擇需要的密碼或 PIN 類型。 選項包括：
  - **裝置預設值**（*預設值*）-需要密碼、數位 pin 或英數位元 pin
  - **數值**-需要密碼或數位 PIN
  - 英**數位**元-需要密碼或英數位元 PIN。  
  
  設定為英*數位*元時，可以使用下列設定：  
  - [密碼複雜性]  ：  
    選項包括： 
    - **需要數位和小寫字母**（*預設值*）
    - **需要數位、小寫字母和大寫字母**
    - **需要數字、小寫字母、大寫字母及特殊字元**

    > [!TIP]
    > 英數位元密碼原則可能很複雜。 我們鼓勵系統管理員閱讀 Csp 以取得詳細資訊：
    >
    > - [DeviceLock/AlphanumericDevicePasswordRequired CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock#devicelock-alphanumericdevicepasswordrequired)
    > - [DeviceLock/MinDevicePasswordComplexCharacters CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock#devicelock-mindevicepasswordcomplexcharacters)

- **密碼長度下限**：  
  輸入使用者密碼中至少必須具有的數字位數或字元數。

- **在停止活動最少幾分鐘後必須輸入密碼**：  
  輸入使用者必須重新輸入密碼之前的閒置時間。

- **密碼到期 (天數)** ：  
  輸入密碼到期，而他們必須建立新密碼之前的天數 (從 1 到 730)。

- **避免重複使用以前用過的密碼次數**：  
  輸入不得重複使用的舊密碼數。

- **裝置從閒置狀態回復時需要密碼 (Mobile 與 Holographic)** ：  
  - [未設定]  (預設  )
  - [需要]  - 需要裝置使用者在每次裝置從閒置狀態回復時輸入密碼。

  > [!IMPORTANT]
  > 在 Windows 桌面上變更密碼需求時，使用者會在下次登入時受到影響，因為此時裝置會從閒置變成作用中。 系統仍會提示密碼符合需求的使用者變更其密碼。

### <a name="encryption"></a>加密

- **裝置上的資料儲存區加密**：  
  此設定適用于裝置上的所有磁片磁碟機。
  - [未設定]  (預設  )
  - [需要]  - 使用 [需要]  可將裝置上的資料儲存區加密。

  > [!NOTE]
  > [裝置上的資料儲存區加密]  設定通常會檢查裝置上是否有加密。 如需更強固的加密設定，請考慮使用 [要求 Bitlocker]  ，這會利用 Windows 運作狀況證明在 TPM 層級驗證 Bitlocker 狀態。

### <a name="device-security"></a>裝置安全性  

- **防火牆**：  
  - [**未設定**] （*預設*）-Intune 不會控制 Microsoft Defender 防火牆，也不會變更現有的設定。
  - [**需要**]-開啟 [Microsoft Defender 防火牆]，並防止使用者將其關閉。  

  [防火牆 CSP](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp)

  > [!NOTE]
  > 如果裝置在重新開機後立即同步處理，或立即同步處理從睡眠狀態喚醒，則此設定可能會報告為**錯誤**。 此案例可能不會影響整體裝置合規性狀態。 若要重新評估合規性狀態，請手動[同步處理裝置](https://docs.microsoft.com/intune-user-help/sync-your-device-manually-windows)。

- [信賴平台模組 (TPM)]  ：  
  - **未設定**（*預設*）-Intune 不會檢查裝置是否有 TPM 晶片版本。
  - **需要**-Intune 會檢查 TPM 晶片版本的相容性。 如果 TPM 晶片版本大於**0** （零），則裝置相容。 如果裝置上沒有 TPM 版本，則裝置不相容。  

  [DeviceStatus CSP-DeviceStatus/TPM/SpecificationVersion 節點](https://docs.microsoft.com/windows/client-management/mdm/devicestatus-csp)
  
- **防毒**：  
  - [未設定]  (預設  ) - Intune 不會檢查裝置上是否有任何安裝的反間諜功能解決方案。 
  - [需要]  - 使用向 [Windows 資訊安全中心](https://blogs.windows.com/windowsexperience/2017/01/23/introducing-windows-defender-security-center/)註冊的防毒解決方案 (例如 Symantec 和 Microsoft Defender) 來檢查合規性。

- [反間諜功能]  ：  
  - [未設定]  (預設  ) - Intune 不會檢查裝置上是否有任何安裝的反間諜功能解決方案。
  - [需要]  - 使用向 [Windows 資訊安全中心](https://blogs.windows.com/windowsexperience/2017/01/23/introducing-windows-defender-security-center/)註冊的反間諜功能解決方案 (例如 Symantec 和 Microsoft Defender) 來檢查合規性。  

### <a name="defender"></a>Defender

*Windows 10 Desktop 支援下列合規性設定。*

- **Microsoft Defender 反惡意程式碼**：  
  - [**未設定**] （*預設*）-Intune 不會控制服務，也不會變更現有的設定。
  - [**需要**]-開啟 Microsoft Defender 反惡意程式碼服務，並防止使用者將其關閉。

- **Microsoft Defender 反惡意程式碼最小版本**：  
  輸入 Microsoft Defender 反惡意程式碼服務允許的最低版本。 例如，輸入 `4.11.0.0`。 保留空白時，可以使用任何版本的 Microsoft Defender 反惡意程式碼服務。  

  *根據預設，不會設定任何版本*。

- **Microsoft Defender 反惡意程式碼安全性情報最**新：  
  控制裝置上的 Windows 安全性病毒和威脅防護更新。
  - [**未設定**] （*預設*）-Intune 不會強制執行任何需求。
  - **要求**-強制 Microsoft Defender 安全性情報為最新狀態。

  [Defender/Health/SignatureOutOfDate CSP](https://docs.microsoft.com/windows/client-management/mdm/defender-csp)
  
  如需詳細資訊，請參閱[Microsoft Defender 防毒軟體的安全性情報更新和其他 microsoft 反惡意](https://www.microsoft.com/en-us/wdsi/defenderupdates)代碼。

- [即時保護]  ：  
  - **未設定**（*預設*）-Intune 不會控制這項功能，也不會變更現有的設定。
  - [**需要**]-開啟 [即時保護]，這會掃描惡意程式碼、間諜軟體和其他垃圾軟體。  

  [Defender/AllowRealtimeMonitoring CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowrealtimemonitoring)

## <a name="microsoft-defender-atp"></a>Microsoft Defender ATP

### <a name="microsoft-defender-advanced-threat-protection-rules"></a>Microsoft Defender 進階威脅防護規則

- **裝置必須等於或低於電腦風險分數**：  
  使用此設定，以採用來自防禦威脅服務的風險評估作為合規性的條件。 選擇允許的最高威脅層級：
  - [未設定]  (預設  )  
  - [清除]  - 此選項最安全，因為裝置不能有任何威脅。 若裝置上偵測到任何等級的威脅，便會評估為不相容。
  - [低]  - 若只有低等級的威脅，會將裝置評估為符合規範。 任何更高等級的威脅都會使裝置處於不相容狀態。
  - [中]  - 如果裝置上的現有威脅是低等級或中等級，會將裝置評估為符合規範。 若在裝置上偵測到高等級的威脅，便會判斷為不相容。
  - [高]  - 此選項最不安全，且允許所有威脅等級。 如果此解決方案只用於報告用途，則此設定可能很實用。
  
  若要將 Microsoft Defender ATP (進階威脅防護) 設定為防禦威脅服務，請參閱[使用條件式存取啟用 Microsoft Defender ATP](advanced-threat-protection.md)。


## <a name="windows-holographic-for-business"></a>Windows Holographic for Business

Windows Holographic for Business 使用 **Windows 10 及更新版本**平台。 Windows Holographic for Business 支援下列設定：

- [系統安全性]   > [加密]   > [對裝置上的資料存放區加密]  。

若要在 Microsoft HoloLens 上驗證裝置加密，請參閱[驗證裝置加密](https://docs.microsoft.com/hololens/hololens-encryption#verify-device-encryption)。

## <a name="surface-hub"></a>Surface Hub

Surface Hub 使用 **Windows 10 及更新版本**平台。 Surface Hub 支援合規性和條件式存取。 若要在 Surface Hub 上啟用這些功能，我們建議您在 Intune 中[啟用 Windows 10 自動註冊](../enrollment/windows-enroll.md) (需要 Azure Active Directory (Azure AD))，並瞄準 Surface Hub 裝置作為裝置群組。 Surface Hub 需要加入 Azure AD，合規性和條件式存取才能運作。

如需指引，請參閱[設定 Windows 裝置的註冊](../enrollment/windows-enroll.md)。

## <a name="next-steps"></a>後續步驟

- [為不相容的裝置新增動作](actions-for-noncompliance.md)及[使用範圍標籤篩選原則](../fundamentals/scope-tags.md)。
- [監視您的相容性原則](compliance-policy-monitor.md)。
- 請參閱 [Windows 8.1 裝置的相容性原則設定](compliance-policy-create-windows-8-1.md)。

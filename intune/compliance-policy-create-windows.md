---
title: 在 Microsoft Intune 中建立 Windows 裝置相容性原則 - Azure | Microsoft Docs
description: 建立或設定適用於 Windows Phone 8.1、Windows 8.1 和更新版本，以及 Windows 10 和更新版本裝置的 Microsoft Intune 裝置合規性原則。 檢查最低和最高作業系統上的合規性、設定密碼限制和長度、要求 BitLocker、檢查是否有協力廠商 AV 解決方案、設定可接受的威脅層級，以及啟用資料存放區上的加密，包括 Surface Hub 和 Windows Holographic for Business。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/13/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: e0772f4e577f6660926f6827a7fda8e51bcdd280
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2018
ms.locfileid: "52182953"
---
# <a name="add-a-device-compliance-policy-for-windows-devices-in-intune"></a>在 Intune 中為 Windows 裝置新增裝置合規性原則

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

適用於 Windows 的 Intune 裝置合規性政策，會指定 Windows 裝置為被視為符合規範必須滿足的規則與設定。 您可以使用這些原則搭配條件式存取，以允許或封鎖存取公司資源。 您也可以取得裝置報表，並針對不相容採取動作。 在 Intune Azure 入口網站中，為每個平台建立裝置相容性原則。 若要深入了解合規性原則，以及任何必要條件，請參閱[開始使用裝置合規性](device-compliance-get-started.md)。

下表描述搭配使用合規性政策與條件式存取原則時，不相容設定的管理方式。

---------------------------

| **原則設定** | **Windows 8.1 及更新版本** | **Windows Phone 8.1 及更新版本** |
|----| ----| --- |
| **PIN 或密碼設定** | 已修復 | 已修復 |   
| **裝置加密** | 不適用 | 已修復 |   
| **已越獄或 Root 的裝置** | 不適用 | 不適用 |  
| **電子郵件設定檔** | 不適用 | 不適用 |   
| **最低 OS 版本** | 已隔離 | 已隔離 |   
| **最高 OS 版本** | 已隔離 | 已隔離 |   
| **Windows 健康情況證明** | 已隔離：Windows 10 和 Windows 10 行動裝置版|不適用：Windows 8.1 |

-------------------------------

**已補救** = 裝置作業系統強制符合規範。 (例如，強制使用者設定 PIN。)

**已隔離** = 裝置作業系統不強制符合規範。 (例如，Android 裝置不強制使用者為裝置加密。)裝置不相容時，會採取下列動作︰

- 如果對使用者套用了條件式存取原則，裝置會遭到封鎖。
- 公司入口網站會通知使用者任何合規性問題的相關事項。

## <a name="create-a-device-compliance-policy"></a>建立裝置合規性政策

[!INCLUDE [new-device-compliance-policy](./includes/new-device-compliance-policy.md)]
5. 針對 [平台]，選取 [Windows Phone 8.1]、[Windows 8.1 及更新版本] 或 [Windows 10 及更新版本]。
6. 選擇 [組態設定]，並輸入 [裝置健全狀況]、[裝置屬性]，以及 [系統安全性] 設定。 完成後，請選取 [確定] 和 [建立]。

<!--- 4. Choose **Actions for noncompliance** to say what actions should happen when a device is determined as noncompliant with this policy.
5. In the **Actions for noncompliance** pane, choose **Add** to create a new action.  The action parameters pane allows you to specify the action, email recipients that should receive the notification in addition to the user of the device, and the content of the notification that you want to send.
6. The message template option allows you to create several custom emails depending on when the action is set to take. For example, you can create a message for notifications that are sent for the first time and a different message for final warning before access is blocked. The custom messages that you create can be used for all your device compliance policy.
7. Specify the **Grace period** which determines when that action to take place.  For example, you may want to send a notification as soon as the device is evaluated as noncompliant, but allow some time before enforcing the conditional access policy to block access to company resources like SharePoint online.
8. Choose **Add** to finish creating the action.
9. You can create multiple actions and the sequence in which they should occur. Choose **Ok** when you are finished creating all the actions.--->

## <a name="windows-81-devices-policy-settings"></a>Windows 8.1 裝置原則設定

這些原則設定會套用到執行下列平台的裝置：

- Windows Phone 8.1
- Windows 8.1 及更新版本

### <a name="device-properties"></a>裝置內容

- **所需的最低 OS**︰當裝置不符合最低 OS 版本需求時，它會回報為不符合規範。 會顯示如何升級的資訊連結。 終端使用者可以選擇升級其裝置，然後便可存取公司資源。
- **允許的最高 OS 版本**：當裝置使用的 OS 版本高於規則所指定的版本時，系統會封鎖對公司資源的存取。 系統會要求使用者連絡其 IT 管理員。在規則變更為允許該作業系統版本之前，此裝置將無法存取公司資源。

Windows 8.1 電腦會傳回版本 **3**。 如果 Windows 的 OS 版本規則設為 Windows 8.1，則即使裝置具有 Windows 8.1，還是會回報為不相容。

### <a name="system-security"></a>系統安全性

#### <a name="password"></a>密碼

- **需要密碼才可解除鎖定行動裝置**：**要求**使用者必須輸入密碼以存取其裝置。
- **簡單密碼**：設定為 [封鎖] 時，使用者將無法建立 **1234** 或 **1111** 之類的簡單密碼。 設定為 [未設定] 時，使用者可以建立 **1234** 或 **1111** 之類的密碼。
- **最小密碼長度**：輸入密碼至少須包含的位數或字元數。

  對於執行 Windows 並使用 Microsoft 帳戶存取的裝置，合規性原則在下列情況下將無法正確評估：
  - 如果最小密碼長度超過八個字元
  - 或者，如果字元集數目下限超過兩個

- **密碼類型**：選擇密碼是否應該只包含**數值**字元，或是應該混合數字和其他字元 (**英數字元**)。
  
  - **密碼中的非英數字元數目**：若將 [需要的密碼類型] 設定為 [英數字元]，則此設定可指定密碼至少須包含的最少字元集數目。 四個字元集為：
    - 小寫字母
    - 大寫字母
    - 符號
    - 數字

    若設定較高的數目，使用者就必須建立較複雜的密碼。 對於執行 Windows 並使用 Microsoft 帳戶存取的裝置，若密碼長度下限超過八個字元，或字元集數目下限大於二，合規性政策將無法正確進行評估。

- **停止活動幾分鐘後需要輸入密碼**：輸入在閒置多久後，使用者必須重新輸入密碼。
- **密碼到期 (天數)**：選取密碼到期且必須建立新密碼前的天數。
- **避免重複使用前幾個密碼**：輸入不可使用先前所使用的多少個密碼。

#### <a name="encryption"></a>加密

- **在行動裝置上要求加密**：**要求**裝置必須加密以連線至資料存放區資源。

## <a name="windows-10-and-later-policy-settings"></a>Windows 10 及更新版本的原則設定

### <a name="device-health"></a>Device health

- **需要 BitLocker**：開啟 BitLocker 時，裝置能夠在系統已關閉或進入休眠狀態的情況下，保護存放在磁碟機中的資料不受未經授權的存取。 Windows BitLocker 磁碟機加密會加密儲存在 Windows 作業系統磁碟區上的所有資料。 BitLocker 使用 TPM 協助保護 Windows 作業系統和使用者資料。 它也能協助確保電腦不受竄改，即使該電腦是處於無人看管、遺失或遭竊的情況。 如果電腦配備相容的 TPM，BitLocker 會使用 TPM 來鎖定可保護資料的加密金鑰。 因此，除非 TPM 驗證電腦的狀態，否則無法存取金鑰。
- **要求在裝置上啟用安全開機**：啟用安全開機時，會強迫系統開機到原廠信任狀態。 此外，啟用安全開機時，用來啟動電腦的核心元件必須具有製造裝置之組織所信任的正確密碼編譯簽章。 UEFI 韌體會在讓電腦啟動之前先驗證簽章。 如果有任何檔案已遭竄改 (即中斷其簽章)，則無法啟動系統。

  > [!NOTE]
  > TPM 1.2 和 2.0 裝置支援 [要求在裝置上啟用安全開機] 設定。 針對不支援 TPM 2.0 或更新版本的裝置，Intune 中的原則狀態會顯示為 [不符合規範]。 這是 Windows 10 中的[裝置健康情況證明](https://docs.microsoft.com/windows/security/information-protection/tpm/trusted-platform-module-overview#device-health-attestation)服務限制。

- **要求程式碼完整性**：程式碼完整性是一種功能，可在每次將驅動程式或系統檔案載入記憶體時驗證其完整性。 程式碼完整性會偵測核心是否正在載入未簽署的驅動程式或系統檔案。 或者是否有具系統管理員權限的使用者帳戶執行惡意軟體以修改系統檔案。

如需 HAS 服務如何運作的詳細資料，請參閱[健全狀況證明 CSP](https://docs.microsoft.com/windows/client-management/mdm/healthattestation-csp)。

### <a name="device-properties"></a>裝置內容

- **最低 OS 版本**：輸入允許的最低版本 (格式為 **major.minor.build.CU 編號**)。 若要取得正確值，請開啟命令提示字元，然後鍵入 `ver`。 `ver` 命令會傳回格式如下的版本：

  `Microsoft Windows [Version 10.0.17134.1]`

  若裝置上的 OS 版本較指定版本舊，會將其回報為不相容。 會顯示如何升級的資訊連結。 終端使用者可以選擇升級其裝置，之後便可以存取公司資源。

- **最高 OS 版本**：輸入允許的最高版本 (格式為 **major.minor.build.revision 編號**)。 若要取得正確值，請開啟命令提示字元，然後鍵入 `ver`。 `ver` 命令會傳回格式如下的版本：

  `Microsoft Windows [Version 10.0.17134.1]`

  當裝置使用的 OS 版本晚於規則中所指定的版本時，系統便會封鎖對公司資源的存取權，並要求使用者連絡其 IT 管理員。在將規則變更為允許該 OS 版本之前，此裝置無法用來存取公司資源。

- **針對行動裝置所需的最低 OS**：輸入允許的最低版本 (格式為 major.minor.build 編號格式)。

  若裝置上的 OS 版本較指定版本舊，會將其回報為不相容。 會顯示如何升級的資訊連結。 終端使用者可以選擇升級其裝置，之後便可以存取公司資源。

- **針對行動裝置所需的最高 OS**：輸入允許的最高版本 (編號格式為 major.minor.build)。

  當裝置使用的 OS 版本晚於規則中所指定的版本時，系統便會封鎖對公司資源的存取權，並要求使用者連絡其 IT 管理員。在將規則變更為允許該 OS 版本之前，此裝置無法用來存取公司資源。

- **有效的作業系統組建**：輸入可接受的作業系統版本範圍，包括最低和最高。 您也可以將這些可接受的 OS 組建編號清單**匯出**逗號分隔值 (CSV) 檔案。

### <a name="system-security-settings"></a>系統安全性設定

#### <a name="password"></a>密碼

- **需要密碼才可解除鎖定行動裝置**：**要求**使用者必須輸入密碼以存取其裝置。
- **簡單密碼**：設定為 [封鎖] 時，使用者將無法建立 **1234** 或 **1111** 之類的簡單密碼。 設定為 [未設定] 時，使用者可以建立 **1234** 或 **1111** 之類的密碼。
- **密碼類型**：選擇密碼是否應該只包含**數值**字元，或是應該混合數字和其他字元 (**英數字元**)。

  - **密碼中的非英數字元數目**：若將 [需要的密碼類型] 設定為 [英數字元]，則此設定可指定密碼至少須包含的最少字元集數目。 四個字元集為：
    - 小寫字母
    - 大寫字母
    - 符號
    - 數字

    若設定較高的數目，使用者就必須建立較複雜的密碼。

- **最小密碼長度**：輸入密碼至少須包含的位數或字元數。
- **停止活動幾分鐘後需要輸入密碼**：輸入在閒置多久後，使用者必須重新輸入密碼。
- **密碼到期 (天數)**：選取密碼到期且必須建立新密碼前的天數。
- **避免重複使用前幾個密碼**：輸入不可使用先前所使用的多少個密碼。
- **於裝置從閒置狀態回復時要求密碼 (行動裝置版和 Holographic)**：強制使用者於每次裝置從閒置狀態回復時輸入密碼。

#### <a name="encryption"></a>加密

- **對裝置上的資料存放區加密**：選擇 [需要] 來將裝置上的資料存放區加密。

  > [!NOTE]
  > [裝置上的資料儲存區加密] 設定通常會檢查裝置上是否有加密。 如需更強固的加密設定，請考慮使用 [要求 Bitlocker]，這會利用 Windows 運作狀況證明在 TPM 層級驗證 Bitlocker 狀態。

#### <a name="device-security"></a>裝置安全性

- **防毒**：當設定為 [必要] 時，您可以使用向 Windows 資訊安全中心註冊的防毒解決方案 (例如 Symantec 和 Windows Defender) 來檢查合規性。 **未設定**時，Intune 不會檢查裝置上是否有任何安裝的 AV 解決方案。
- **反間諜功能**：當設定為 [必要] 時，您可以使用向 Windows 資訊安全中心註冊的防毒解決方案 (例如 Symantec 和 Windows Defender) 來檢查合規性。 **未設定**時，Intune 不會檢查裝置上是否有任何安裝的反間諜軟體解決方案。

### <a name="windows-defender-atp"></a>Windows Defender ATP

- **要求裝置不高於電腦風險分數**：使用此設定進行來自您防禦威脅服務的風險評估，以作為合規性的條件。 選擇允許的最高威脅層級：
  - **清除**：此選項最安全，因為裝置不能有任何威脅。 如果在裝置上偵測到任何等級的威脅，即評估為不符合規範。
  - **低**︰如果只有低等級的威脅，則會將裝置評估為相容。 任何更高等級的威脅都會使裝置處於不相容狀態。
  - **中**︰如果裝置上的現有威脅是低等級或中等級，則會將裝置評估為符合規範。 如果在裝置上偵測到高等級的威脅，則會判斷為不相容。
  - **高**：此選項最不安全，且允許所有威脅層級。 如果此解決方案只用於報告用途，則此設定可能很實用。
  
  若要將 Windows Defender ATP (進階威脅防護) 設定為防禦威脅服務，請參閱[使用條件式存取啟用 Windows Defender ATP](advanced-threat-protection.md)。

## <a name="windows-holographic-for-business"></a>Windows Holographic for Business

Windows Holographic for Business 使用 **Windows 10 及更新版本**平台。 Windows Holographic for Business 支援下列設定：

- [系統安全性] > [加密] > [對裝置上的資料存放區加密]。

若要在 Microsoft HoloLens 上驗證裝置加密，請參閱[驗證裝置加密](https://docs.microsoft.com/hololens/hololens-encryption#verify-device-encryption)。

## <a name="surface-hub"></a>Surface Hub
Surface Hub 使用 **Windows 10 及更新版本**平台。 Surface Hub 支援合規性和條件式存取。 若要在 Surface Hub 上啟用這些功能，建議您在 Intune 中[啟用 Windows 10 自動註冊](windows-enroll.md) (也需要 Azure Active Directory (AAD))，並將 Surface Hub 裝置以裝置群組的形式設定為目標。 Surface Hub 需要加入 Azure Active Directory，合規性和條件式存取才能運作。

請參閱[設定 Windows 裝置的註冊](windows-enroll.md)以取得指引。

## <a name="assign-user-or-device-groups"></a>指派使用者或裝置群組

1. 選擇您已設定的原則。 現有的原則位於 [裝置合規性] > [原則]。
2. 選擇原則，然後選擇 [指派]。 您可以包含或排除 Azure AD 安全性群組。
3. 選擇 [選取的群組] 以查看您的 Azure AD 安全性群組。 選取要套用這項原則的使用者或裝置群組，然後選擇 [儲存] 以部署原則。

您已套用此原則。 要套用原則之使用者的裝置將會接受相容性評估。

## <a name="next-steps"></a>接下來的步驟
[將電子郵件自動化，並為不符合規範的裝置新增動作](actions-for-noncompliance.md)  
[監視 Intune 裝置合規性原則](compliance-policy-monitor.md)

---
title: 在 Microsoft Intune 中檢查 Windows 裝置上的合規性 - Azure | Microsoft Docs
description: 建立或設定適用於 Windows Phone 8.1、Windows 8.1 和更新版本，以及 Windows 10 和更新版本裝置的 Microsoft Intune 裝置合規性原則。 檢查最低和最高作業系統上的合規性、設定密碼限制和長度、要求 BitLocker、檢查是否有協力廠商 AV 解決方案、設定可接受的威脅層級，以及啟用資料存放區上的加密，包括 Surface Hub 和 Windows Holographic for Business。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/22/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 518bb2ab0f59b5692ff2c2391fe971abba0639c6
ms.sourcegitcommit: 06f62ae989da6c60bac4a52ccd41b429f7367d8c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/26/2019
ms.locfileid: "55072519"
---
# <a name="add-a-device-compliance-policy-for-windows-devices-in-intune"></a>在 Intune 中為 Windows 裝置新增裝置合規性原則

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune 裝置合規性政策包括裝置必須符合才能視為符合規範的規則和設定。 將這些原則與條件式存取搭配使用，以允許或封鎖對您組織資源的存取。 您也可以取得裝置報表，並針對不相容採取動作。

若要深入了解合規性原則，以及任何必要條件，請參閱[開始使用裝置合規性](device-compliance-get-started.md)。

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
| **Windows 健康情況證明** | 已隔離：Windows 10 和 Windows 10 Mobile|不適用：Windows 8.1 |

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

- **最低 OS 需求**：當裝置不符合最小 OS 版本需求時，會回報為不符合規範。 會顯示如何升級的資訊連結。 終端使用者可以選擇升級其裝置，然後便可存取公司資源。
- **允許的最高作業系統版本**：當裝置使用的 OS 版本比規則中所輸入的版本還新時，系統就會封鎖對公司資源的存取。 系統會要求使用者連絡其 IT 管理員。在您變更規則以允許該 OS 版本之前，裝置無法存取組織資源。

Windows 8.1 電腦會傳回版本 **3**。 如果 Windows 的 OS 版本規則設為 Windows 8.1，則即使裝置具有 Windows 8.1，還是會回報為不相容。

### <a name="system-security"></a>系統安全性

#### <a name="password"></a>密碼

- **需要密碼來解除鎖定行動裝置**：**要求**使用者輸入密碼，然後才能存取裝置。
- **簡單密碼**：設定為 [封鎖] 時，使用者將無法建立 **1234** 或 **1111** 之類的簡單密碼。 設定為 [未設定] 時，使用者可以建立 **1234** 或 **1111** 之類的密碼。
- **密碼長度下限**：輸入使用者密碼中至少必須具有的數字位數或字元數。

  對於執行 Windows 並使用 Microsoft 帳戶存取的裝置，合規性原則在下列情況下將無法正確評估：
  - 如果最小密碼長度超過八個字元
  - 或者，如果字元集數目下限超過兩個

- **密碼類型**：選擇密碼是否應該只包含**數值**字元，或是應該混合數字和其他字元 (**英數字元**)。
  
  - **密碼中的非英數字元數目**：若將 [必要的密碼類型] 設為 [英數字元]，此設定即會指定密碼至少須包含的字元集數下限。 四個字元集為：
    - 小寫字母
    - 大寫字母
    - 符號
    - 數字

    若設定較高的數目，使用者就必須建立較複雜的密碼。 對於使用 Microsoft 帳戶存取的裝置，合規性政策將無法在下列情況中進行正確評估：

    - 如果最小密碼長度超過八個字元
    - 或者，如果字元集數目下限超過兩個

- **在停止活動最少幾分鐘後必須輸入密碼**：輸入使用者必須重新輸入密碼之前的閒置時間。
- **密碼到期 (天數)**：選取密碼到期，必須建立新密碼的天數。
- **避免重複使用以前用過的密碼次數**：輸入不得重複使用的舊密碼數。

#### <a name="encryption"></a>加密

- **必須啟用行動裝置的加密**：**要求**裝置必須加密，才能連線至資料儲存體資源。

## <a name="windows-10-and-later-policy-settings"></a>Windows 10 及更新版本的原則設定

### <a name="device-health"></a>Device health

- **要求 BitLocker**：開啟 BitLocker 時，裝置能夠在系統已關閉或進入休眠狀態的情況下，保護儲存於磁碟機的資料，以防止未經授權的存取。 Windows BitLocker 磁碟機加密會加密儲存在 Windows 作業系統磁碟區上的所有資料。 BitLocker 使用 TPM 協助保護 Windows 作業系統和使用者資料。 即使該電腦處於無人看管、遺失或遭竊的情況，它也能協助確保電腦不受竄改。 如果電腦配備相容的 TPM，BitLocker 會使用 TPM 來鎖定可保護資料的加密金鑰。 因此，必須等到 TPM 驗證電腦的狀態之後，才能存取金鑰。
- **要求在裝置上啟用安全開機**：啟用安全開機時，強迫系統開機到原廠信任狀態。 此外，啟用安全開機時，用來啟動電腦的核心元件必須具有製造裝置之組織所信任的正確密碼編譯簽章。 UEFI 韌體會在讓電腦啟動之前先驗證簽章。 如果有任何檔案遭到竄改 (這會中斷它們的簽章)，系統就不會開機。

  > [!NOTE]
  > TPM 1.2 和 2.0 裝置支援 [要求在裝置上啟用安全開機] 設定。 針對不支援 TPM 2.0 或更新版本的裝置，Intune 中的原則狀態會顯示為 [不符合規範]。 這是 Windows 10 中的[裝置健康情況證明](https://docs.microsoft.com/windows/security/information-protection/tpm/trusted-platform-module-overview#device-health-attestation)服務限制。

- **要求程式碼完整性**：程式碼完整性是一種功能，可在每次將驅動程式或系統檔案載入至記憶體時驗證其完整性。 程式碼完整性會偵測系統是否正在將未簽署的驅動程式或系統檔案載入至核心。 它也會偵測是否有透過具系統管理員權限之使用者帳戶執行的惡意軟體修改了系統檔案。

如需 HAS 服務如何運作的詳細資料，請參閱[健全狀況證明 CSP](https://docs.microsoft.com/windows/client-management/mdm/healthattestation-csp)。

### <a name="device-properties"></a>裝置內容

- **最小 OS 版本**：輸入允許的最低版本 (格式為 **major.minor.build.CU number**)。 若要取得正確值，請開啟命令提示字元，然後鍵入 `ver`。 `ver` 命令會傳回格式如下的版本：

  `Microsoft Windows [Version 10.0.17134.1]`

  當裝置版本比您輸入的 OS 版本更早時，就會回報為不符合規範。 您會看到如何升級的資訊連結。 終端使用者可以選擇升級其裝置。 當他們升級之後，就能存取公司資源。

- **最大 OS 版本**：輸入允許的最高版本 (格式為 **major.minor.build.revision number**)。 若要取得正確值，請開啟命令提示字元，然後鍵入 `ver`。 `ver` 命令會傳回格式如下的版本：

  `Microsoft Windows [Version 10.0.17134.1]`

  當裝置使用的 OS 版本晚於規則中所輸入的版本時，系統便會封鎖對公司資源的存取，並要求使用者連絡其 IT 管理員。將規則變更為允許該 OS 版本之前，裝置將無法存取公司資源。

- **行動裝置所需的最低 OS 版本**：輸入允許的最低版本 (格式為 major.minor.build number)。

  當裝置版本比您輸入的 OS 版本更早時，就會回報為不符合規範。 您會看到如何升級的資訊連結。 終端使用者可以選擇升級其裝置。 當他們升級之後，就能存取公司資源。

- **行動裝置所需的最高 OS 版本**：輸入允許的最高版本 (格式為 major.minor.build number)。

  當裝置使用的 OS 版本晚於您所輸入的版本時，系統便會封鎖對公司資源的存取，並要求使用者連絡其 IT 管理員。將規則變更為允許該 OS 版本之前，裝置將無法存取公司資源。

- **有效的作業系統組建**：輸入可接受的作業系統版本範圍，包括最低和最高版本。 您也可以將這些可接受的 OS 組建編號清單**匯出**逗號分隔值 (CSV) 檔案。

### <a name="configuration-manager-compliance"></a>Configuration Manager 合規性

僅適用於執行 Windows 10 和更新版本的共同受控裝置。 僅 Intune 的裝置會傳回無法使用的狀態。

- **需要 System Center Configuration Manager 的裝置合規性**：選擇 [需要] 以強制 System Center Configuration Manager 中的所有設定 (設定項目) 符合規範。 

  例如，您需要在裝置上安裝所有軟體更新。 在 Configuration Manager 中，此要求將會對應「已安裝」狀態。 如果裝置上的任何程式處於未知狀態，則裝置在 Intune 中就不會符合規範。
  
  如果**未設定**，Intune 就不會針對合規性檢查任何 Configuration Manager 設定。

### <a name="system-security-settings"></a>系統安全性設定

#### <a name="password"></a>密碼

- **需要密碼來解除鎖定行動裝置**：**要求**使用者輸入密碼，然後才能存取裝置。
- **簡單密碼**：設定為 [封鎖] 時，使用者將無法建立 **1234** 或 **1111** 之類的簡單密碼。 設定為 [未設定] 時，使用者可以建立 **1234** 或 **1111** 之類的密碼。
- **密碼類型**：選擇密碼是否應該只包含**數值**字元，或是應該混合數字和其他字元 (**英數字元**)。

  - **密碼中的非英數字元數目**：若將 [必要的密碼類型] 設為 [英數字元]，此設定即會指定密碼至少須包含的字元集數下限。 四個字元集為：
    - 小寫字母
    - 大寫字母
    - 符號
    - 數字

    若設定較高的數目，使用者就必須建立較複雜的密碼。

- **密碼長度下限**：輸入使用者密碼中至少必須具有的數字位數或字元數。
- **在停止活動最少幾分鐘後必須輸入密碼**：輸入使用者必須重新輸入密碼之前的閒置時間。
- **密碼到期 (天數)**：選取密碼到期，必須建立新密碼的天數。
- **避免重複使用以前用過的密碼次數**：輸入不得重複使用的舊密碼數。
- **裝置從閒置狀態回復時需要密碼 (Mobile 與 Holographic)**：強制使用者在每次裝置從閒置狀態回復時輸入密碼。

#### <a name="encryption"></a>加密

- **裝置上的資料儲存區加密**：選擇 [需要] 以將裝置上的資料儲存區加密。

  > [!NOTE]
  > [裝置上的資料儲存區加密] 設定通常會檢查裝置上是否有加密。 如需更強固的加密設定，請考慮使用 [要求 Bitlocker]，這會利用 Windows 運作狀況證明在 TPM 層級驗證 Bitlocker 狀態。

#### <a name="device-security"></a>裝置安全性

- **防毒**：當設定為 [必要] 時，您可以使用向 Windows 資訊安全中心註冊的防毒解決方案 (例如 Symantec 和 Windows Defender) 來檢查合規性。 **未設定**時，Intune 不會檢查裝置上是否有任何安裝的 AV 解決方案。
- **反間諜功能**：當設定為 [必要] 時，您可以使用向 Windows 資訊安全中心註冊的防毒解決方案 (例如 Symantec 和 Windows Defender) 來檢查合規性。 **未設定**時，Intune 不會檢查裝置上是否有任何安裝的反間諜軟體解決方案。

### <a name="windows-defender-atp"></a>Windows Defender ATP

- **裝置必須等於或低於電腦風險分數**：使用此設定，以採用來自防禦威脅服務的風險評估作為合規性的條件。 選擇允許的最高威脅層級：
  - **清除**：此選項最安全，因為裝置不能有任何威脅。 如果裝置上偵測到任何等級的威脅，即會評估為不符合規範。
  - **低**︰如果只有低等級的威脅，會將裝置評估為符合規範。 任何更高等級的威脅都會使裝置處於不相容狀態。
  - **中**︰如果裝置上的現有威脅是低等級或中等級，則會將裝置評估為符合規範。 如果在裝置上偵測到高等級的威脅，即判斷為不符合規範。
  - **高**：此選項最不安全，且允許所有威脅層級。 如果此解決方案只用於報告用途，則此設定可能很實用。
  
  若要將 Windows Defender ATP (進階威脅防護) 設定為防禦威脅服務，請參閱[使用條件式存取啟用 Windows Defender ATP](advanced-threat-protection.md)。

## <a name="windows-holographic-for-business"></a>Windows Holographic for Business

Windows Holographic for Business 使用 **Windows 10 及更新版本**平台。 Windows Holographic for Business 支援下列設定：

- [系統安全性] > [加密] > [對裝置上的資料存放區加密]。

若要在 Microsoft HoloLens 上驗證裝置加密，請參閱[驗證裝置加密](https://docs.microsoft.com/hololens/hololens-encryption#verify-device-encryption)。

## <a name="surface-hub"></a>Surface Hub
Surface Hub 使用 **Windows 10 及更新版本**平台。 Surface Hub 支援合規性和條件式存取。 若要在 Surface Hub 上啟用這些功能，建議您在 Intune 中[啟用 Windows 10 自動註冊](windows-enroll.md) (也需要 Azure Active Directory (Azure AD))，並以裝置群組的形式將 Surface Hub 裝置設定為目標。 Surface Hub 需要加入 Azure AD，合規性和條件式存取才能運作。

請參閱[設定 Windows 裝置的註冊](windows-enroll.md)以取得指引。

## <a name="assign-user-or-device-groups"></a>指派使用者或裝置群組

1. 選擇您已設定的原則。 現有的原則位於 [裝置合規性] > [原則]。
2. 選擇原則，然後選擇 [指派]。 您可以包含或排除 Azure AD 安全性群組。
3. 選擇 [選取的群組] 以查看您的 Azure AD 安全性群組。 選取要套用這項原則的使用者或裝置群組，然後選擇 [儲存] 以部署原則。

您已套用此原則。 系統將會評估原則目標使用者所使用的裝置是否符合規範。

## <a name="next-steps"></a>後續步驟
[將電子郵件自動化，並為不符合規範的裝置新增動作](actions-for-noncompliance.md)  
[監視 Intune 裝置合規性原則](compliance-policy-monitor.md)

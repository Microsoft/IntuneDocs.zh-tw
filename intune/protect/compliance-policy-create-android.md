---
title: Microsoft Intune 中的 Android 裝置相容性設定 - Azure | Microsoft Docs
description: 查看您在 Microsoft Intune 中為 Android 裝置設定相容性時可使用的所有設定清單。 設定密碼規則、選擇最低或最高作業系統版本、限制特定應用程式，防止重複使用密碼等。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/21/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: e1258fe4-0b5c-4485-8bd1-152090df6345
ms.reviewer: samyada
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: efff117ca79e4fa9a00fd8d9a4be792e246f1a86
ms.sourcegitcommit: 3ace4cba6e2f6fefa9120be3807387a49b200c9b
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2019
ms.locfileid: "72810171"
---
# <a name="android-settings-to-mark-devices-as-compliant-or-not-compliant-using-intune"></a>使用 Intune，透過 Android 設定將裝置標示為相容或不相容

本文列出及描述您可在 Intune 中 Android 裝置上設定的不同相容性設定。 作為您行動裝置管理 (MDM) 解決方案的一部分，請使用這些設定來將經破解 (越獄) 的裝置標示為不相容、設定允許的威脅等級、啟用 Google Play Protect 等。

本功能適用於：

- Android 裝置管理員

身為 Intune 管理員，請使用這些相容性設定來協助保護您的組織資源。 若要深入了解相容性原則及其執行的操作，請參閱[開始使用裝置相容性](device-compliance-get-started.md)。

## <a name="before-you-begin"></a>開始之前

[建立合規性政策](create-compliance-policy.md#create-the-policy)。 針對 [**平臺**]，選取 [ **Android 裝置系統管理員**]。

## <a name="device-health"></a>裝置健全狀況

- **破解的裝置**： 
  - [未設定]  (預設  ) - 不會評估此設定是否符合規範。
  - [封鎖]  - 將已破解 (已進行越獄) 的裝置標示為不符合規範。 

- **裝置須等於或低於裝置威脅等級**：  
  使用此設定可從連線的行動裝置威脅防護服務進行風險評估，以作為合規性的條件。 
  - [未設定]  (預設  ) - 不會評估此設定是否符合規範。 
  - [安全]  - 此選項最安全，因為裝置不能有任何威脅。 如果在裝置上偵測到任何等級的威脅，即評估為不符合規範。
  - [低]  - 若只有低等級的威脅，會將裝置評估為符合規範。 任何更高等級的威脅都會使裝置處於不相容狀態。
  - [中]  - 如果裝置上的現有威脅是低等級或中等級，會將裝置評估為符合規範。 如果在裝置上偵測到高等級的威脅，即判斷為不符合規範。
  - [高]  - 此選項最不安全，且允許所有威脅等級。 如果此解決方案只用於報告用途，則此設定可能很實用。

### <a name="google-play-protect"></a>Google Play 安全防護

- **已設定 Google Play Services**：  
  Google Play 服務可允許安全性更新，而且是 Google 認證裝置上許多安全性功能的基層相依服務。
  - [未設定]  (預設  ) - 不會評估此設定是否符合規範。  
  - [需要]  - 需要安裝並啟用 Google Play 服務應用程式。  

- **最新的安全性提供者**： 
  - [未設定]  (預設  ) - 不會評估此設定是否符合規範。  
  - [需要]  - 需要最新的安全性提供者能夠保護裝置免受已知弱點的威脅。 

- **對應用程式進行威脅掃描**：  
  - [未設定]  (預設  ) - 不會評估此設定是否符合規範。  
  - [需要]  - 需要啟用 Android [驗證應用程式]  功能。  
  > [!NOTE]
  > 在舊版的 Android 平台上，此功能為合規性設定。 Intune 只能在裝置層級檢查是否已啟用此設定。

- **SafetyNet 裝置證明**：  
  輸入必須符合的 [SafetyNet 證明](https://developer.android.com/training/safetynet/attestation.html)層級。 選項包括：
  - [未設定]  (預設  ) - 不會評估此設定是否符合規範。
  - **檢查基本完整性**
  - **檢查基本完整性與經過認證的裝置**

> [!NOTE]
> 若要使用應用程式防護原則設定 Google Play Protect 設定，請參閱 Android 的 [Intune 應用程式防護原則設定](../apps/app-protection-policy-settings-android.md#conditional-launch)。

## <a name="device-properties"></a>裝置內容

### <a name="operating-system-version"></a>作業系統版本 

- **最小 OS 版本**：  
  當裝置不符合最小 OS 版本需求時，會回報為不符合規範。 會顯示如何升級的資訊連結。 終端使用者可以選擇升級其裝置，然後便可存取公司資源。

   *根據預設，不會設定任何版本*。

- **最大 OS 版本**：  
  當裝置使用的 OS 版本比規則中所指定的版本還新時，系統就會封鎖對公司資源的存取。 系統會要求使用者連絡其 IT 管理員。在規則變更為允許該作業系統版本之前，此裝置將無法存取公司資源。

  *根據預設，不會設定任何版本*。

## <a name="system-security"></a>系統安全性

### <a name="password"></a>密碼
<!-- - **Minimum password length**: Enter the minimum number of digits or characters that the user's password must have.   


- **Maximum minutes of inactivity before password is required**: Enter the idle time before the user must reenter their password. When you choose **Not configured** (default), this setting isn't evaluated for compliance or non-compliance.

- **Password expiration (days)**: Select the number of days before the password expires and the user must create a new password.

- **Number of previous passwords to prevent reuse**: Enter the number of recent passwords that can't be reused. Use this setting to restrict the user from creating previously used passwords.

-->

- **需要密碼來解除鎖定行動裝置**： 
  - [未設定]  (預設  ) - 不會評估此設定是否符合規範。
  - [需要]  - 使用者必須輸入密碼，才能存取其裝置。  

- **必要的密碼類型**：  
  選擇密碼應該只包含數字字元，還是混合數字及其他字元。 選項包括：
  - **裝置預設**-若要評估密碼合規性，請務必選取 [**裝置預設**] 以外的 [密碼強度]。
  - **低安全性生物識別**
  - **至少包含數字** 
  - [複雜數字]  - 不允許重複或連續的數字 (例如 `1111` 或 `1234`)。
  - **至少包含字母** 
  - **至少包含英數字元**
  - **至少包含英數字元和符號**


### <a name="encryption"></a>加密

- **裝置上的資料儲存區加密**：  
  *支援 Android 4.0 和更新版本，或 KNOX 4.0 和更新版本。*  
  <br>
  - [未設定]  (預設  ) - 不會評估此設定是否符合規範。 
  - **需要**加密裝置上的資料儲存體。 當您選擇 [需要密碼來將行動裝置解除鎖定]  設定時，裝置便會加密。  

### <a name="device-security"></a>裝置安全性

- **封鎖來自不明來源的應用程式**：  
  - [未設定]  (預設  ) - 不會評估此設定是否符合規範。
  - **封鎖**-封鎖具有**安全性 > 不明來源**已啟用來源的裝置（在 android 4.0 透過 android 7.x 支援 *。Android 8.0 和更新版本不支援*)。  

  若要側載應用程式，則必須允許未知的來源。 如果您不會側載 Android 應用程式，則將此功能設定為 [封鎖]  可啟用這項合規性政策。 

  > [!IMPORTANT]
  > 側載應用程式必須啟用 [封鎖來自不明來源的應用程式]  設定。 只有當您不會在裝置上側載 Android 應用程式時，才應該施行這項合規性政策。

- **公司入口網站應用程式執行階段完整性**：  
  - [未設定]  (預設  ) - 不會評估此設定是否符合規範。  
  - [需要]  - 選擇 [需要]  以確認公司入口網站應用程式符合下列所有需求：
    - 已安裝預設執行階段環境
    - 已正確簽署
    - 不在偵錯模式
    - 從已知來源安裝

- **封鎖裝置上的 USB 調試** *（Android 4.2 或更新版本）* ：  
  - [未設定]  (預設  ) - 不會評估此設定是否符合規範。
  - [封鎖]  - 防止裝置使用 USB 偵錯功能。  

- **最低安全性修補程式等級** *（Android 6.0 或更新版本）* ：  
  選取裝置可擁有的最舊安全性修補程式等級。 未至少達此修補程式等級的裝置將視為不符合規範。 日期必須以 `YYYY-MM-DD` 格式輸入。

  *根據預設，不會設定任何日期*。

- [受限應用程式]  ：  
  針對應限制的應用程式，輸入其 [應用程式名稱]  和 [應用程式套件組合識別碼]  ，然後選取 [新增]  。 已安裝至少一個受限應用程式的裝置會標示為不符合規範。

## <a name="next-steps"></a>後續步驟

- [為不相容的裝置新增動作](actions-for-noncompliance.md)及[使用範圍標籤篩選原則](../fundamentals/scope-tags.md)。
- [監視您的相容性原則](compliance-policy-monitor.md)。
- 請參閱 [Android Enterprise 裝置的相容性原則設定](compliance-policy-create-android-for-work.md)。

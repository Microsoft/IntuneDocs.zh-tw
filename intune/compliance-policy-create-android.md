---
title: 在 Microsoft Intune 中建立 Android 裝置合規性原則 - Azure | Microsoft Docs
description: 請參閱 Microsoft Intune 中設定您的 Android 裝置的合規性時，您可以使用的所有設定的清單。 設定密碼規則，選擇最小值或最大作業系統版本、 限制特定的應用程式，避免重複使用密碼，以及更多。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/08/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: e1258fe4-0b5c-4485-8bd1-152090df6345
ms.reviewer: muhosabe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7670af46657fed048bfe10b8659eae6d45db7620
ms.sourcegitcommit: 02803863eba37ecf3d8823a7f1cd7c4f8e3bb42c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59423572"
---
# <a name="android-settings-to-mark-devices-as-compliant-or-not-compliant-using-intune"></a>將裝置標記為符合規範或不符合規範使用 Intune 的 android 設定

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

這篇文章列出並描述您可以在 Intune 中 Android 裝置設定的不同的合規性設定。 您的行動裝置管理 (MDM) 解決方案的一部分，使用這些設定來 root 破解 （已進行 jb 破解） 將裝置標記為不符合規範、 設定允許的威脅層級，啟用 Google Play Protect，，和更多功能。

本功能適用於：

- Android

身為 Intune 管理員，使用這些合規性設定來協助保護您組織的資源。 若要深入了解合規性原則，以及任何必要條件，請參閱[開始使用裝置合規性](device-compliance-get-started.md)。

## <a name="before-you-begin"></a>開始之前

[建立合規性政策](create-compliance-policy.md#create-the-policy)。 針對 [平台]，選取 [Android]。

## <a name="device-health"></a>Device health

- **已 Root 破解的裝置**：選擇 [封鎖] 將已 Root (JB) 破解的裝置標示為不符合規範。 當您選擇 [未設定]  (預設值) 時，則不會評估此設定是否符合規範。
- **裝置層級需要不高於裝置威脅層級**：使用此設定進行來自 Lookout MTP 解決方案的風險評估，以作為合規性的條件。 當您選擇 [未設定]  (預設值) 時，則不會評估此設定是否符合規範。 若要使用此設定，請選擇允許的威脅等級：
  - **安全**：此選項最安全，因為裝置不能有任何威脅。 如果在裝置上偵測到任何等級的威脅，即評估為不符合規範。
  - **低**︰如果只有低等級的威脅，則會將裝置評估為相容。 任何更高等級的威脅都會使裝置處於不相容狀態。
  - **中**︰如果裝置上的現有威脅是低等級或中等級，則會將裝置評估為符合規範。 如果在裝置上偵測到高等級的威脅，即判斷為不符合規範。
  - **高**：此選項最不安全，且允許所有威脅層級。 如果此解決方案只用於報告用途，則此設定可能很實用。

### <a name="google-play-protect"></a>Google Play 保護

- **已設定 Google Play 服務**：**需要**安裝並啟用 Google Play 服務應用程式。 Google Play 服務可允許安全性更新，而且是 Google 認證裝置上許多安全性功能的基層相依服務。 當您選擇 [未設定]  (預設值) 時，則不會評估此設定是否符合規範。
- **最新安全性提供者**：**需要**最新安全性提供者可保護裝置免於已知的弱點。 當您選擇 [未設定]  (預設值) 時，則不會評估此設定是否符合規範。
- **對應用程式進行威脅掃描**：**需要**啟用 Android 的 [驗證應用程式] 功能。 當您選擇 [未設定]  (預設值) 時，則不會評估此設定是否符合規範。

  > [!NOTE]
  > 在舊版的 Android 平台上，此功能為合規性設定。 Intune 只能在裝置層級檢查是否已啟用此設定。

- **SafetyNet 裝置證明**：輸入必須符合的 [SafetyNet 證明](https://developer.android.com/training/safetynet/attestation.html)層級。 選項包括：
  - **未設定** (預設值)：不會評估設定是否符合規範。
  - **檢查基本完整性**
  - **檢查基本完整性與經過認證的裝置**

> [!NOTE]
> 若要設定 Google Play 安全防護 設定使用應用程式保護原則，請參閱[Intune 應用程式保護原則設定](app-protection-policy-settings-android.md#conditional-launch)在 Android 上。

## <a name="device-property-settings"></a>裝置屬性設定

- **最低作業系統版本**︰當裝置不符合最低作業系統版本需求時，它會回報為不符合規範。 會顯示如何升級的資訊連結。 終端使用者可以選擇升級其裝置，然後便可存取公司資源。
- **最高作業系統版本**：當裝置使用的作業系統版本高於規則指定的版本時，會封鎖對公司資源的存取。 系統會要求使用者連絡其 IT 管理員。在規則變更為允許該作業系統版本之前，此裝置將無法存取公司資源。

## <a name="system-security-settings"></a>系統安全性設定

### <a name="password"></a>密碼

- **需要密碼才可解除鎖定行動裝置**：**要求**使用者必須輸入密碼以存取其裝置。 當您選擇 [未設定]  (預設值) 時，則不會評估此設定是否符合規範。
- **最小密碼長度**：輸入使用者密碼至少須包含的位數或字元數。
- **所需的密碼類型**：選擇密碼是否應該只有數值字元，或者混合數字和其他字元。 選項包括：
  - **裝置預設**
  - **低安全性生物識別**
  - **至少包含數字** (預設值)
  - **複雜數字**：不允許重複或連續的數字 (例如 `1111` 或 `1234`)。
  - **至少包含字母** 
  - **至少包含英數字元**
  - **至少包含英數字元和符號**

- **停止活動幾分鐘後需要輸入密碼**：輸入在閒置多久後，使用者必須重新輸入密碼。 當您選擇 [未設定]  (預設值) 時，則不會評估此設定是否符合規範。
- **密碼到期日 (天數)**：選取使用者的密碼到期，而必須建立新密碼前的天數。
- **避免重複使用前幾個密碼**：輸入不可使用最近的多少個密碼。 使用此設定以限制使用者建立先前使用過的密碼。

### <a name="encryption"></a>加密

- **裝置上的資料存放區加密** (Android 4.0 及更新版本，或 KNOX 4.0 及更新版本)：選擇 [需要] 以加密裝置上的資料存放區。 當您選擇 [需要密碼來將行動裝置解除鎖定] 設定時，裝置便會加密。 當您選擇 [未設定]  (預設值) 時，則不會評估此設定是否符合規範。

### <a name="device-security"></a>裝置安全性

- **封鎖來自不明來源的應用程式**：選擇**封鎖**啟用了 [安全性 > 不明來源] 來源的裝置 (支援 Android 4.0 - Android 7.x ，不支援 Android 8.0 和更新版本)。 當您選擇 [未設定]  (預設值) 時，則不會評估此設定是否符合規範。

  若要側載應用程式，則必須允許未知的來源。 如果您不會側載 Android 應用程式，則將此功能設定為 [封鎖] 可啟用這項合規性政策。 

  > [!IMPORTANT]
  > 側載應用程式必須啟用 [封鎖來自不明來源的應用程式] 設定。 只有當您不會在裝置上側載 Android 應用程式時，才應該施行這項合規性政策。

- **公司入口網站應用程式執行階段完整性**：選擇 [需要] 以確認公司入口網站應用程式符合下列所有需求：

  - 已安裝預設執行階段環境
  - 已正確簽署
  - 不在偵錯模式
  - 從已知來源安裝

  當您選擇 [未設定]  (預設值) 時，則不會評估此設定是否符合規範。

- **封鎖裝置上的 USB 偵錯** (Android 4.2 或更新版本)：選擇 [封鎖] 以防止裝置使用 USB 偵錯功能。 當您選擇 [未設定]  (預設值) 時，則不會評估此設定是否符合規範。
- **安全性修補程式等級下限** (Android 6.0 或更新版本)：選取裝置可擁有的安全性修補程式等級下限。 未至少達此修補程式等級的裝置將視為不符合規範。 日期必須以 `YYYY-MM-DD` 格式輸入。
- **受限應用程式**：針對應限制的應用程式，輸入其 [應用程式名稱] 和 [應用程式套件組合識別碼]。 選擇 [新增]。 已安裝至少一個受限應用程式的裝置會標示為不符合規範。

選取 [確定] > [建立] 儲存您的變更。

## <a name="locations"></a>位置

在原則中，您可以強制合規性由裝置的位置。 選擇此選項，從現有的位置。 還沒有位置？ [使用 Intune 中的位置 (網路範圍)](use-network-locations.md)可提供一些指引。

1. 選擇**位置** > **選取位置**。
2. 從清單中，請檢查您的位置 >**選取**。
3. [儲存] 原則。

## <a name="next-steps"></a>後續步驟

- [新增適用於不符合規範的裝置動作](actions-for-noncompliance.md)並[使用篩選器原則的範圍標籤](scope-tags.md)。
- [監視合規性政策](compliance-policy-monitor.md)。
- [Android Enterprise 的合規性政策設定](compliance-policy-create-android-for-work.md)

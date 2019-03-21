---
title: 在 Microsoft Intune 中建立 Android Enterprise 合規性政策 - Azure | Microsoft Docs
description: 建立或設定適用於 Android Enterprise 或工作設定檔裝置的 Microsoft Intune 裝置合規性政策。 選擇允許越獄的裝置、設定可接受的威脅層級、檢查 Google Play、輸入最低和最高作業系統版本、選擇您的密碼需求，以及允許側載應用程式。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/19/2018
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 9da89713-6306-4468-b211-57cfb4b51cc6
ms.reviewer: muhosabe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: a6f1f07c1cb7b5dbe81120fd678f429a996f230e
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57566228"
---
# <a name="add-a-device-compliance-policy-for-android-enterprise-devices-in-intune"></a>在 Intune 中為 Android Enterprise 裝置新增裝置合規性政策

裝置合規性政策是使用 Intune 保護您組織資源時的一項重要功能。 在 Intune 中，您可以建立裝置必須符合才能視為符合規範的規則和設定，例如密碼長度。 如果裝置不符合規範，您可以接著使用[條件式存取](conditional-access.md)來封鎖對資料和資源的存取。 

您也可以取得裝置報表，並針對不符合規範的裝置採取動作，例如傳送通知電子郵件給使用者。 若要深入了解合規性原則，以及任何必要條件，請參閱[開始使用裝置合規性](device-compliance-get-started.md)。

本文列出您可以在執行 Android Enterprise 的裝置合規性政策中使用的設定。

## <a name="non-compliance-and-conditional-access"></a>不符合規範和條件式存取

下表描述搭配使用合規性政策與條件式存取原則時，不相容設定的管理方式。

--------------------------

|**原則設定**| **Android Enterprise 設定檔** |
| --- | --- |
| **PIN 或密碼設定** |  已隔離 |
| **裝置加密** |  已隔離 |
| **已越獄或 Root 的裝置** | 隔離 (非設定) |
| **電子郵件設定檔** | 不適用 |
| **最低 OS 版本** | 已隔離 |
| **最高 OS 版本** | 已隔離 |
| **Windows 健康情況證明** |不適用 |

**已補救** = 裝置作業系統強制符合規範。 例如，強制使用者設定 PIN。

**已隔離** = 裝置作業系統不強制符合規範。 例如，Android 裝置不強制使用者為裝置加密。 裝置不符合規範時，會採取下列動作：

  - 如果對使用者套用了條件式存取原則，就會封鎖裝置。
  - 公司入口網站會通知使用者任何合規性問題的相關事項。

## <a name="create-a-device-compliance-policy"></a>建立裝置合規性政策

[!INCLUDE [new-device-compliance-policy](./includes/new-device-compliance-policy.md)]
4. 針對 [平台]，選取 [Android 企業]。 
5. 選擇 [組態設定]。 輸入 [裝置健全狀況]、[裝置屬性] 和 [系統安全性] 設定，如本文中所述。

## <a name="device-health"></a>Device health

- **已 Root 破解的裝置**：選擇 [封鎖] 將已 Root (JB) 破解的裝置標示為不符合規範。 當您選擇 [未設定]  (預設值) 時，則不會評估此設定是否符合規範。
- **裝置層級需要不高於裝置威脅層級**：使用此設定進行來自 Lookout MTP 解決方案的風險評估，以作為合規性的條件。 當您選擇 [未設定]  (預設值) 時，則不會評估此設定是否符合規範。 若要使用此設定，請選擇允許的威脅等級：
  - **安全**：此選項最安全，意味著裝置不能有任何威脅。 如果在裝置上偵測到任何等級的威脅，即評估為不符合規範。
  - **低**︰如果只有低等級的威脅，則會將裝置評估為相容。 任何更高等級的威脅都會使裝置處於不相容狀態。
  - **中**︰如果裝置有低等級或中等級的威脅，則會將裝置評估為相容。 如果在裝置上偵測到高等級的威脅，即判斷為不符合規範。
  - **高**：此選項最不安全，因為它允許所有威脅層級。 如果此解決方案只用於報告用途，則此設定可能很實用。
- **已設定 Google Play 服務**：**需要**安裝並啟用 Google Play 服務應用程式。 Google Play 服務可允許安全性更新，而且是 Google 認證裝置上許多安全性功能的基層相依服務。 當您選擇 [未設定]  (預設值) 時，則不會評估此設定是否符合規範。
- **最新安全性提供者**：**需要**最新安全性提供者可保護裝置免於已知的弱點。 當您選擇 [未設定]  (預設值) 時，則不會評估此設定是否符合規範。
- **SafetyNet 裝置證明**：輸入必須符合的 [SafetyNet 證明](https://developer.android.com/training/safetynet/attestation.html)層級。 選項包括：
  - **未設定** (預設值)：不會評估設定是否符合規範。
  - **檢查基本完整性**
  - **檢查基本完整性與經過認證的裝置**

#### <a name="threat-scan-on-apps"></a>對應用程式進行威脅掃描

在 Android Enterprise 裝置上，[對應用程式進行威脅掃描] 設定為設定原則。 請參閱 [Android Enterprise 裝置限制設定](device-restrictions-android-for-work.md)。

## <a name="device-properties-settings"></a>裝置內容設定

- **最低作業系統版本**︰當裝置不符合最低作業系統版本需求時，它會回報為不符合規範。 會顯示如何升級的資訊連結。 終端使用者可以選擇升級其裝置，之後便可以存取公司資源。
- **最高作業系統版本**：當裝置使用的作業系統版本高於規則中的版本時，會封鎖對公司資源的存取。 而且，系統會要求使用者連絡其 IT 管理員。在規則變更為允許該作業系統版本之前，此裝置將無法存取公司資源。

## <a name="system-security-settings"></a>系統安全性設定

### <a name="password"></a>密碼

- **需要密碼才可解除鎖定行動裝置**：**要求**使用者必須輸入密碼以存取其裝置。 當您選擇 [未設定]  (預設值) 時，則不會評估此設定是否符合規範。 此設定會套用在裝置層級。 如果您只需要在工作設定檔層級要求密碼，則請使用設定原則。 請參閱 [Android 企業裝置組態設定](device-restrictions-android-for-work.md)。
- **最小密碼長度**：輸入使用者密碼至少須包含的位數或字元數。
- **所需的密碼類型**：選擇密碼是否應該只有數值字元，或者混合數字和其他字元。 選項包括：
  - **裝置預設**
  - **低安全性生物識別**
  - **至少包含數字** (預設值)
  - **複雜數字**
  - **至少包含字母**
  - **至少包含英數字元**
  - **至少包含英數字元和符號**

- **停止活動幾分鐘後需要輸入密碼**：輸入在閒置多久後，使用者必須重新輸入密碼。 當您選擇 [未設定]  (預設值) 時，則不會評估此設定是否符合規範。
- **密碼到期 (天數)**：選取密碼到期且必須建立新密碼前的天數。
- **避免重複使用前幾個密碼**：輸入不可使用最近的多少個密碼。 使用此設定以限制使用者建立先前使用過的密碼。

### <a name="encryption"></a>加密

- **對裝置上的資料存放區加密**：選擇 [需要] 來將裝置上的資料存放區加密。 當您選擇 [未設定] (預設值) 時，則不會評估此設定是否符合規範。 

  您不需要進行此設定，因為 Android 工作設定檔裝置會強制執行加密。

### <a name="device-security"></a>裝置安全性

- **封鎖來自不明來源的應用程式**：選擇**封鎖**啟用了 [安全性 > 不明來源] 來源的裝置 (支援 Android 4.0 - Android 7.x ，不支援 Android 8.0 和更新版本)。 當您選擇 [未設定]  (預設值) 時，則不會評估此設定是否符合規範。

  若要側載應用程式，則必須允許未知的來源。 如果您不會側載 Android 應用程式，則將此功能設定為 [封鎖] 可啟用這項合規性政策。 

  > [!IMPORTANT]
  > 側載應用程式必須啟用 [封鎖來自不明來源的應用程式] 設定。 只有當您不會在裝置上側載 Android 應用程式時，才應該施行這項合規性政策。

  您不需要進行此設定，因為 Android 工作設定檔裝置一律會限制來自不明來源的安裝。

- **公司入口網站應用程式執行階段完整性**：選擇 [需要] 以確認公司入口網站應用程式符合下列所有需求：

  - 已安裝預設執行階段環境
  - 已正確簽署
  - 不在偵錯模式
  - 從已知來源安裝

  當您選擇 [未設定]  (預設值) 時，則不會評估此設定是否符合規範。

- **封鎖裝置上的 USB 偵錯**：選擇 [封鎖] 以防止裝置使用 USB 偵錯功能。 當您選擇 [未設定]  (預設值) 時，則不會評估此設定是否符合規範。

  您不需要進行此設定，因為 Android 工作設定檔裝置上已停用 USB 偵錯。

- **安全性修補程式等級下限**：選取裝置可擁有的安全性修補程式等級下限。 未至少達此修補程式等級的裝置將視為不符合規範。 日期必須以 *YYYY-MM-DD* 格式輸入。

完成時，請選取 [確定] > [確定] 以儲存變更。

## <a name="actions-for-noncompliance"></a>不符合標準時所採取的動作

選取 [不符合規範時所採取的動作]。 預設動作會立即將裝置標示為不符合規範。

您可以變更裝置標示為不符合規範的排程 (例如一天之後)。 您也可以設定第二個動作，在裝置不符合規範時傳送電子郵件給使用者。

[為不符合規範的裝置新增動作](actions-for-noncompliance.md)提供詳細資訊，包括建立通知電子郵件給您的使用者。

## <a name="scope-tags"></a>範圍標籤

範圍標籤是將原則指派給特定群組 (例如銷售、工程、人力資源等) 的絕佳方式。 您可以將範圍標籤新增至合規性政策。 請參閱[使用範圍標籤篩選原則](scope-tags.md)。 

## <a name="assign-user-groups"></a>指派使用者群組

一旦原則建立完成，在您指派原則之前，它不會執行任何動作。 若要指派原則： 

1. 選擇您已設定的原則。 現有的原則位於 [裝置合規性] > [原則]。
2. 選擇原則，然後選擇 [指派]。 您可以包含或排除 Azure Active Directory (AD) 安全性群組。
3. 選擇 [選取的群組] 以查看您的 Azure AD 安全性群組。 選取要套用這項原則的使用者群組，然後選擇 [儲存] 將原則部署給使用者。

您已將原則套用至使用者。 系統將會評估原則目標使用者所使用的裝置是否符合規範。

## <a name="next-steps"></a>後續步驟
[將電子郵件自動化，並為不符合規範的裝置新增動作](actions-for-noncompliance.md)  
[監視 Intune 裝置合規性原則](compliance-policy-monitor.md)  
[適用於 Android 的合規性政策設定](compliance-policy-create-android.md)

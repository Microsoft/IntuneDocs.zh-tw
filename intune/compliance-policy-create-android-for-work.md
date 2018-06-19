---
title: 在 Microsoft Intune 中建立 Android for Work 合規性原則 - Azure | Microsoft Docs
description: 建立或設定適用於 Android for Work 裝置的 Microsoft Intune 裝置合規性原則。 選擇允許越獄的裝置、設定可接受的威脅層級、檢查 Google Play、輸入最低和最高作業系統版本、選擇您的密碼需求，以及允許側載應用程式。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/16/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 9da89713-6306-4468-b211-57cfb4b51cc6
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: c1d438aa7416b1629af7ab2b899afa06720e2b49
ms.sourcegitcommit: 6a9830de768dd97a0e95b366fd5d2f93980cee05
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/10/2018
ms.locfileid: "34047980"
---
# <a name="add-a-device-compliance-policy-for-android-for-work-devices-in-intune"></a>在 Intune 中為 Android for Work 裝置新增裝置合規性政策

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

適用於 Android for Work 的 Intune 裝置合規性政策，會指定這些裝置為被視為符合規範必須滿足的規則與設定。 您可以使用這些原則搭配條件式存取，以允許或封鎖存取公司資源。 您也可以取得裝置報表，並針對不合規範的裝置採取動作。 在 Intune Azure 入口網站中，為不同平台建立裝置合規性原則。 若要深入了解合規性原則，以及任何必要條件，請參閱[開始使用裝置合規性](device-compliance-get-started.md)。

下表描述搭配使用合規性政策與條件式存取原則時，不相容設定的管理方式。

--------------------------

|**原則設定**| **Android for Work** |
| --- | --- |
| **PIN 或密碼設定** |  已隔離 |
| **裝置加密** |  已隔離 |
| **已越獄或 Root 的裝置** | 隔離 (非設定) |
| **電子郵件設定檔** | 不適用 |
| **最低 OS 版本** | 已隔離 |
| **最高 OS 版本** | 已隔離 |
| **Windows 健康情況證明** |不適用 |

**已補救** = 裝置作業系統強制符合規範。 (例如強制使用者設定 PIN 碼)。

**已隔離** = 裝置作業系統不強制符合規範。 (例如，Android 裝置不強制使用者為裝置加密。)裝置不相容時，會採取下列動作︰

- 如果對使用者套用了條件式存取原則，就會封鎖裝置。
- 公司入口網站會通知使用者任何合規性問題的相關事項。

## <a name="create-a-device-compliance-policy"></a>建立裝置合規性政策

[!INCLUDE [new-device-compliance-policy](./includes/new-device-compliance-policy.md)]
5. 針對 [平台]，選取 [Android for Work]。 選擇 [組態設定]，並輸入 [裝置健全狀況]、[裝置屬性]，以及 [系統安全性] 設定。 完成後，請選取 [確定] 和 [建立]。

<!--- 4. Choose **Actions for noncompliance** to say what actions should happen when a device is determined as noncompliant with this policy.
5. In the **Actions for noncompliance** pane, choose **Add** to create a new action.  The action parameters pane allows you to specify the action, email recipients that should receive the notification in addition to the user of the device, and the content of the notification that you want to send.
6. The message template option allows you to create several custom emails depending on when the action is set to take. For example, you can create a message for notifications that are sent for the first time and a different message for final warning before access is blocked. The custom messages that you create can be used for all your device compliance policy.
7. Specify the **Grace period** which determines when that action to take place.  For example, you may want to send a notification as soon as the device is evaluated as noncompliant, but allow some time before enforcing the conditional access policy to block access to company resources like SharePoint online.
8. Choose **Add** to finish creating the action.
9. You can create multiple actions and the sequence in which they should occur. Choose **Ok** when you are finished creating all the actions.--->

## <a name="device-health"></a>Device health

- **已刷機的裝置**：如果您啟用此設定，已越獄的裝置會評估為不合規範。
- **裝置層級需要不高於裝置威脅層級**：使用此設定進行來自 Lookout MTP 解決方案的風險評估，以作為合規性的條件。 選擇允許的最高威脅層級：
  - **安全**：此選項最安全，意味著裝置不能有任何威脅。 如果在裝置上偵測到任何等級的威脅，即評估為不符合規範。
  - **低**︰如果只有低等級的威脅，則會將裝置評估為相容。 任何更高等級的威脅都會使裝置處於不相容狀態。
  - **中**︰如果裝置有低等級或中等級的威脅，則會將裝置評估為相容。 如果在裝置上偵測到高等級的威脅，則會判斷為不相容。
  - **高**：此選項最不安全，因為它允許所有威脅層級。 如果此解決方案只用於報告用途，則此設定可能很實用。
- **已設定 Google Play 服務**：需要安裝並啟用「Google Play 服務」應用程式。 Google Play 服務可允許安全性更新，而且是 Google 認證裝置上許多安全性功能的基層相依服務。
- **最新安全性提供者**：需要最新安全性提供者，以保護裝置已知的漏洞。
- **SafetyNet 裝置證明**：輸入必須符合的 [SafetyNet 證明](https://developer.android.com/training/safetynet/attestation.html)層級。 選項包括：
  - **未設定**
  - **檢查基本完整性**
  - **檢查基本完整性與經過認證的裝置**

#### <a name="threat-scan-on-apps"></a>對應用程式進行威脅掃描

在具有工作設定檔的裝置上 (Android for Work)，[對應用程式進行威脅掃描] 設定可在組態原則設定中找到。 系統管理員可以啟用裝置的設定。

如果您的企業使用 Android 工作設定檔，則您可以在已註冊的裝置上啟用 [對應用程式進行威脅掃描]。 建立裝置設定檔，並要求系統安全性設定。 如需詳細資訊，請參閱 [Intune 中的 Android for Work 裝置限制設定](device-restrictions-android-for-work.md)。

## <a name="device-property-settings"></a>裝置屬性設定

- **最低作業系統版本**︰當裝置不符合最低作業系統版本需求時，它會回報為不符合規範。 會顯示如何升級的資訊連結。 終端使用者可以選擇升級其裝置，之後便可以存取公司資源。
- **最高作業系統版本**：當裝置使用的作業系統版本高於規則中的版本時，會封鎖對公司資源的存取。 而且，系統會要求使用者連絡其 IT 管理員。在規則變更為允許該作業系統版本之前，裝置無法存取公司資源。

## <a name="system-security-settings"></a>系統安全性設定

### <a name="password"></a>密碼

- **需要密碼才可解除鎖定行動裝置**：**要求**使用者必須輸入密碼以存取其裝置。
- **最小密碼長度**：輸入使用者密碼至少須包含的位數或字元數。
- **所需的密碼類型**：選擇密碼是否應該只有數值字元，或者混合數字和其他字元。 從下列選項進行選擇：
  - **裝置預設**
  - **低安全性生物識別**
  - **至少包含數字**
  - **複雜數字**
  - **至少包含字母**
  - **至少包含英數字元**
  - **至少包含英數字元和符號**
- **停止活動幾分鐘後需要輸入密碼**：輸入在閒置多久後，使用者必須重新輸入密碼。
- **密碼到期 (天數)**：選取密碼到期且必須建立新密碼前的天數。
- **避免重複使用前幾個密碼**：輸入不可使用最近的多少個密碼。 使用此設定以限制使用者建立先前使用過的密碼。

### <a name="encryption"></a>加密

- **行動裝置需要加密**︰您不需要進行此設定，因為 Android for Work 裝置會強制執行加密。

### <a name="device-security"></a>裝置安全性

- **封鎖來自不明來源的應用程式**：您不需要進行此設定，因為 Android for Work 裝置一律會限制來自不明來源的安裝。
- **公司入口網站應用程式執行階段完整性**：檢查公司入口網站應用程式是否已安裝預設執行階段環境、是否已適當地簽署、是否不處於偵錯模式，以及是否是從已知來源安裝。
- **封鎖裝置上的 USB 偵錯**：您不需要進行此設定，因為 Android for Work 裝置上已停用 USB 偵錯。
- **安全性修補程式等級下限**：選取裝置可擁有的安全性修補程式等級下限。 未至少達此修補程式等級的裝置將視為不合規範。 日期必須以 `YYYY-MM-DD` 格式輸入。

## <a name="assign-user-groups"></a>指派使用者群組

1. 選擇您已設定的原則。 現有的原則位於 [裝置合規性] > [原則]。
2. 選擇原則，然後選擇 [指派]。 您可以包含或排除 Azure Active Directory (AD) 安全性群組。
3. 選擇 [選取的群組] 以查看您的 Azure AD 安全性群組。 選取要套用這項原則的使用者群組，然後選擇 [儲存] 將原則部署給使用者。

您已對使用者套用此原則。 要套用原則之使用者的裝置將會接受相容性評估。

## <a name="next-steps"></a>接下來的步驟
[將電子郵件自動化，並為不符合規範的裝置新增動作](actions-for-noncompliance.md)  
[監視 Intune 裝置合規性原則](compliance-policy-monitor.md)

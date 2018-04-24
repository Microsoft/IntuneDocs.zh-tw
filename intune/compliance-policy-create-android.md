---
title: 在 Microsoft Intune 中建立 Android 裝置相容性原則
titleSuffix: ''
description: 建立適用於 Android 裝置的 Microsoft Intune 的裝置相容性原則，以便您可以指定裝置必須符合的相容性需求。
keywords: ''
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 02/22/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: e1258fe4-0b5c-4485-8bd1-152090df6345
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 586672bf84be6e7bcd8d3b8618aab09088620eb1
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-create-a-device-compliance-policy-for-android-devices-in-intune"></a>如何在 Intune 中為 Android 裝置建立裝置合規性政策


[!INCLUDE [azure_portal](./includes/azure_portal.md)]

適用於 Android 的 Intune 裝置相容性原則指定 Android 設備必須符合的規則和設置，才能視為相。 您可以使用這些原則與條件式存取來允許或封鎖存取公司資源，並取得裝置報告、針對不符合規範來採取動作。 在 Intune Azure 入口網站中，為每個平台建立裝置相容性原則。 若要更了解建立相容性原則之前必須滿足的先決條件，請參閱[開始使用 Microsoft Intune 裝置相容性原則](device-compliance-get-started.md)。

## <a name="to-create-a-device-compliance-policy"></a>建立裝置合規性政策

1. 登入 [Azure 入口網站](https://portal.azure.com)。
2. 選擇 [All services] (所有服務) > [Intune]。 Intune 位於 [Monitoring + Management] (監視 + 管理) 區段。
1. 從 [Intune] 頁面中，選擇 [裝置相容性]。 在 [管理] 下選擇 [原則]，然後選擇 [建立原則]。
3. 在此處選擇 [組態設定] 來指定 [系統安全性]、[裝置健康情況] 及 [裝置屬性] 設定。 完成後，請選擇 [確定]。

<!--- 4. Choose **Actions for noncompliance** to say what actions should happen when a device is determined as noncompliant based on the configured settings in this policy.
5. In the **Actions for noncompliance** pane, choose **Add** to create a new action.  The action parameters pane allows you to specify the action, email recipients that should receive the notification in addition to the user of the device, and the content of the notification that you want to send.
6. The message template option allows you to create several custom emails depending on when the action is set to take. For example, you can create a message for notifications that are sent for the first time and a different message for final warning before access is blocked. The custom messages that you create can be used for all your device compliance policy.
7. Specify the **Grace period** which determines when that action to take place.  For example, you may want to send a notification as soon as the device is evaluated as noncompliant, but allow some time before enforcing the conditional access policy to block access to company resources like SharePoint online.
8. Choose **Add** to finish creating the action.
9. You can create multiple actions and the sequence in which they should occur. Choose **OK** when you are finished creating all the actions.--->

## <a name="to-assign-user-groups"></a>指派使用者群組

若要將合規性政策指派給使用者，請選擇您先前設定的原則。 現有的原則可以在 [裝置相容性 – 原則] 窗格中找到。

1. 選擇原則，然後選擇 [指派]。 這會開啟窗格讓您選取 **Azure Active Directory 安全性群組**，並將其指派給原則。
2. 選擇 [選取群組] 以開啟顯示 Azure AD 安全性群組的窗格。 您可以從中尋找您 Azure Active Directory 中的安全性群組。  您可以選取要套用這項原則的使用者群組，然後選擇 [儲存] 將原則部署給使用者。

您已對使用者套用此原則。  要套用原則之使用者的裝置將會接受合規性評估。

<!---##  Compliance policy settings--->

## <a name="device-health-and-security-settings"></a>裝置健全狀況和安全性設定

- **不得破解裝置或刷機**：如果您啟用這個設定，會將遭破解的裝置評估為不相容。
- **裝置必須防止從不明來源安裝應用程式 (Android 4.0 或更新版本)**：若要封鎖已啟用 [安全性] > [不明來源] 的裝置，請啟用此設定，並將其設為 [是]。

### <a name="important"></a>重要

側載應用程式時必須啟用 [不明來源] 設定。 只有當您不會在裝置上側載 Android 應用程式時，才應該強制執行這項法務遵循政策。

- **USB 偵錯需為停用 (Android 4.2 或更新版本)**︰此設定指定是否要偵測已啟用 USB 偵錯選項的裝置。
- **裝置必須已啟用 [掃描裝置的安全性威脅 (Android 4.2-4.4)]**︰此設定指定要在裝置上啟用 [驗證應用程式] 功能。
- **Android 安全性修補程式等級下限 (Android 6.0 或更新版本)**︰使用此設定可指定 Android 的最低修補程式等級。 未至少達此修補程式等級的裝置將視為不相容。 日期的格式必須指定為 YYYY-MM-DD。
- **必須啟用裝置威脅防護**：使用此設定進行來自 Lookout MTP 解決方案的風險評估，以做為相容的條件。 選擇下列其中一項允許的最高威脅等級：
  - **無 (受保護)**︰這是最安全的選項。 這表示裝置不能受到任何威脅。 如果在裝置上偵測到任何等級的威脅，則會評估為不相容。
  - **低**︰如果只有低等級的威脅，則會將裝置評估為相容。 任何更高等級的威脅都會使裝置處於不相容狀態。
  - **中**︰如果裝置有低等級或中等級的威脅，則會將裝置評估為相容。 如果在裝置上偵測到高等級的威脅，則會判斷為不相容。
  - **高**：這是最不安全的選項。 基本上，這會允許所有威脅等級， 若只將此解決方案用於報告，可能就還不錯。

## <a name="system-security-settings"></a>系統安全性設定

### <a name="password"></a>密碼

- **需要密碼來解除鎖定行動裝置**︰將此項目設為 [是] 時，可要求使用者必須輸入密碼才能存取其裝置。
- **最小密碼長度**：指定使用者密碼中至少須包含的數字或字元數。
- **密碼品質**︰此設定會偵測裝置是否已設定您所指定的密碼需求。 啟用此設定可要求使用者符合 Android 裝置的特定密碼需求。 從下列選項進行選擇：
  - **低安全性摸生物特徵辨識**
  - **必要**
  - **至少包含數字**
  - **至少包含字母**
  - **至少包含英數字元**
  - **英數字元 (含符號)**
- **在非使用狀態幾分鐘後需要輸入密碼**：指定使用者在經過多久閒置時間之後必須重新輸入密碼。
- **密碼到期 (天數)**：選取密碼到期前，必須建立新密碼的天數。
- **記住密碼歷程記錄**：此設定請搭配 [不得重複使用以前用過的密碼] 一起使用，以限制使用者不得建立之前用過的密碼。
- **不得重複使用以前用過的密碼**：如果已選取 [記住密碼歷程記錄]，請指定不得重複使用的舊密碼數目。
- **當裝置從閒置狀態返回時，需要密碼**：請搭配使用這項設定與 [在非使用狀態幾分鐘後需要輸入密碼] 設定。 如果裝置達到 [在非使用狀態幾分鐘後需要輸入密碼] 設定所指定的閒置時間，系統會提示使用者輸入密碼，才能存取該裝置。

### <a name="encryption"></a>加密

- **行動裝置需要加密**︰將此項目設為 [是] 時，可要求裝置必須加密才能連線到資源。 當您選擇 [需要密碼來將行動裝置解除鎖定] 的設定時，裝置會加密。

## <a name="device-property-settings"></a>裝置屬性設定

- **最低作業系統版本需求**︰當裝置不符合最低作業系統版本需求時，它會回報為不相容， 您會看到如何升級的資訊連結。 使用者可以選擇升級其裝置，之後便可以存取公司資源。
- **允許的最高作業系統版本**：當裝置使用的作業系統版本高於規則指定的版本時，會封鎖對公司資源的存取，並要求使用者連絡其 IT 系統管理員。除非將規則變更為允許該作業系統版本，否則此裝置無法用來存取公司資源。

## <a name="how-noncompliant-settings-work-with-conditional-access-policies"></a>如何將不相容設定用於條件式存取原則？

下表說明如何搭配使用合規性政策與條件式存取原則時，不合規設定的管理方式。

--------------------

|**原則設定**| **Android 4.0 及更新版本、Samsung Knox Standard 4.0 及更新版本** |
| --- | ----|
| **PIN 或密碼設定** |  已隔離 |
| **裝置加密** | 已隔離 |
| **已越獄或 Root 的裝置** | 隔離 (非設定) |
| **電子郵件設定檔** | 不適用 |
| **最低 OS 版本** | 已隔離 |
| **最高 OS 版本** |   已隔離 |
| **Windows 健康情況證明** | 不適用 |

--------------------------

**已補救** = 裝置作業系統強制符合規範。 (例如，強制使用者設定 PIN。)

**已隔離** = 裝置作業系統不強制符合規範。 (例如，Android 裝置不強制使用者為裝置加密。)裝置不相容時，會採取下列動作︰

- 如果對使用者套用了條件式存取原則，裝置會遭到封鎖。
- 公司入口網站會通知使用者任何合規性問題的相關事項。

<!--- ## Next steps

[How to monitor device compliance](device-compliance-monitor.md)--->

---
title: "建立 Android for Work 的合規性政策"
titleSuffix: Intune Azure preview
description: "Intune Azure 預覽版︰了解如何為 Android for Work 裝置建立合規性政策。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9da89713-6306-4468-b211-57cfb4b51cc6
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 153cce3809e24303b8f88a833e2fc7bdd9428a4a
ms.openlocfilehash: 48eaa3cbe1ff4e3fb18bfa762a341dbe74a7adce
ms.lasthandoff: 02/18/2017


---

# <a name="how-to-create-a-device-compliance-policy-for-android-for-work-devices-in-intune-azure-preview"></a>如何在 Intune Azure 預覽版中為 Android for Work 裝置建立合規性政策


[!INCLUDE[azure_preview](../includes/azure_preview.md)]

每個平台都會建立合規性政策。  您可以在 Azure 入口網站中建立合規性政策。 如需深入了解什麼是合規性政策，請參閱[什麼是裝置合規性](what-is-device-compliance.md)主題。 如需了解建立合規性政策之前必須滿足的先決條件，請參閱[裝置合規性入門](get-started-with-device-compliance.md)主題。

下表說明如何搭配使用合規性政策與條件式存取原則時，不合規設定的管理方式。

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

- 如果對使用者套用了條件式存取原則，裝置會遭到封鎖。
- 公司入口網站會通知使用者任何合規性問題的相關事項。

## <a name="create-a-compliance-policy-in-the-azure-portal"></a>在 Azure 入口網站中建立合規性政策

1. 從 **Intune** 刀鋒視窗中，選擇 [設定裝置合規性]。 在 [管理] 中選擇 [All device compliance policies] (所有裝置合規性政策) 及 [建立]。
2. 輸入名稱及描述，然後選擇要套用此原則的平台。
3. 選擇 [合規性需求]，在此指定 [安全性]、[裝置健全狀況] 及 [裝置屬性]。完成設定後，請選擇 [確定]。

<!--- 4. Choose **Actions for noncompliance** to say what actions should happen when a device is determined as noncompliant with this policy.
5. In the **Actions for noncompliance** blade, choose **Add** to create a new action.  The action parameters blade allows you to specify the action, email recipients that should receive the notification in addition to the user of the device, and the content of the notification that you want to send.
6. The message template option allows you to create several custom emails depending on when the action is set to take. For example, you can create a message for notifications that are sent for the first time and a different message for final warning before access is blocked. The custom messages that you create can be used for all your device compliance policy.
7. Specify the **Grace period** which determines when that action to take place.  For example, you may want to send a notification as soon as the device is evaluated as noncompliant, but allow some time before enforcing the conditional access policy to block access to company resources like SharePoint online.
8. Choose **Add** to finish creating the action.
9. You can create multiple actions and the sequence in which they should occur. Choose **Ok** when you are finished creating all the actions.--->

## <a name="assign-user-groups"></a>指派使用者群組

若要將合規性政策指派給使用者，請選擇您先前設定的原則。 現有的原則可以在 [合規性 - 政策] 刀鋒視窗中找到。

1. 選擇您想要指派給使用者的原則，然後選擇 [指派]。 這會開啟刀鋒視窗讓您從中選取 [Azure Active Directory 安全性群組]，並將其指派給原則。
2. 選擇 [選取群組] 會開啟刀鋒視窗顯示 Azure AD 安全性群組。  選擇 [選取] 會將原則部署給使用者。

您已對使用者套用此原則。  要套用原則之使用者的裝置將會接受合規性評估。

<!--- ##  Compliance policy settings--->

## <a name="system-security-settings"></a>系統安全性設定

### <a name="password"></a>密碼

- **需要密碼來解除鎖定行動裝置︰**將此設定為 [是]，以要求使用者在存取他們的裝置前輸入密碼。
- **最小密碼長度**：指定密碼至少須包含的數字位數或字元數。
- **密碼品質**︰此設定會偵測是否已在裝置上設定您指定的密碼需求。 啟用此設定可要求使用者設定 Android 裝置的特定密碼需求。 從下列選項進行選擇：
  - **低安全性摸生物特徵辨識**
  - **必要**
  - **至少包含數字**
  - **至少包含字母**
  - **至少包含英數字元**
  - **英數字元 (含符號)**
- **停止活動幾分鐘後需要輸入密碼**：指定閒置多久後使用者必須重新輸入密碼。
- **密碼到期 (天數)**：選取使用者密碼到期，必須建立新密碼前的天數。
- **記住密碼歷程記錄：**此設定請與 [不得重複使用以前用過的密碼] 一起使用，以限制使用者建立以前用過的密碼。
- **不得重複使用以前用過的密碼：**如果已選取 [記住密碼歷程記錄]，請指定不得重複使用的舊密碼數目。
- **裝置從閒置狀態恢復時必須輸入密碼：**這項設定應該與 [在非使用狀態多少分鐘後需要輸入密碼] 設定一起使用。 系統會提示終端使用者輸入密碼，以存取達到 [在非使用狀態幾分鐘後需要輸入密碼] 設定所指定的非使用中時間的裝置。


### <a name="encryption"></a>加密

- **行動裝置需要加密**︰您不需要進行此設定，因為 Android for Work 裝置會強制執行加密。


## <a name="device-health-and-security-settings"></a>裝置健全狀況和安全性設定

- **不得破解裝置或刷機：**如果您啟用這個設定，破解的裝置會評估為不相容。
- **裝置必須防止從不明來源安裝應用程式**︰您不需要進行此設定，因為 Android for Work 裝置一律會限制來自不明來源的安裝。 。
- **需要停用 USB 偵錯**︰因為 Android for Work 裝置已停用 USB 偵錯，所以您無須進行此設定。
- **Android 安全性修補程式等級下限**︰使用此設定可指定 Android 修補程式等級下限。 未至少達此修補程式等級的裝置將視為不相容。 日期的格式必須指定為︰ YYYY-MM-DD。
- **必須啟用裝置威脅防護**：使用此設定作為合規性條件來評估 Lookout MTP 解決方案的風險。 選取允許的最高威脅等級，這會是下列其中一項：
  - **無 (受保護)**：這是最安全的選項。 這表示裝置不能受到任何威脅。 如果在裝置上偵測到任何等級的威脅，則會評估為不相容。
  - **低**︰如果只有低等級的威脅，則會將裝置評估為相容。 任何更高等級的威脅都會使裝置處於不相容狀態。
  - **中**︰如果裝置有低等級或中等級的威脅，則會將裝置評估為相容。 如果在裝置上偵測到高等級的威脅，則會判斷為不相容。
  - **高**：這是最不安全的選項。 基本上，這會允許所有威脅等級，或許僅在此解決方案的用途只有報告時才適用。

如需詳細資訊，請參閱[啟用合規性政策中的裝置威脅保護規則](https://docs.microsoft.com/en-us/intune/deploy-use/enable-device-threat-protection-rule-in-compliance-policy)。

## <a name="device-property-settings"></a>裝置屬性設定

- **最低作業系統版本需求︰**當裝置不符合最低作業系統版本需求時，它會回報為不相容。 會顯示如何升級的資訊連結。 終端使用者可以選擇升級其裝置，之後便可以存取公司資源。
- **允許的最高作業系統版本：**當裝置使用的作業系統版本高於規則指定的版本時，會封鎖對公司資源的存取，並要求使用者連絡其 IT 管理員。 在將規則變更為允許該 OS 版本之前，此裝置無法用來存取公司資源。

<!--- ## Next steps

[How to monitor device compliance](monitor-device-compliance.md)--->


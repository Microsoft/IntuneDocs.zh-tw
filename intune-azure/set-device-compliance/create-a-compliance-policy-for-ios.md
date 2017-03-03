---
title: "如何建立 iOS 的合規性政策"
titleSuffix: Intune Azure preview
description: "Intune Azure 預覽版︰了解如何為 iOS 裝置建立合規性政策。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3cfb8222-d05b-49e3-ae6f-36ce1a16c61d
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 153cce3809e24303b8f88a833e2fc7bdd9428a4a
ms.openlocfilehash: c2ace3061e175a6eefd864bdda176651cc09a5b1
ms.lasthandoff: 02/18/2017


---

# <a name="how-to-create-a-device-compliance-policy-for-ios-devices-in-intune-azure-preview"></a>如何在 Intune Azure 預覽版中為 iOS 裝置建立合規性政策


[!INCLUDE[azure_preview](../includes/azure_preview.md)]

每個平台都會建立合規性政策。  您可以在 Azure 入口網站中建立合規性政策。 如需深入了解什麼是合規性政策，請參閱[什麼是裝置合規性](what-is-device-compliance.md)主題。 如需了解建立合規性政策之前必須滿足的先決條件，請參閱[裝置合規性入門](get-started-with-device-compliance.md)主題。

下表說明如何搭配使用合規性政策與條件式存取原則時，不合規設定的管理方式。

-------------------------------


| **原則設定** | **iOS 8.0 及更新版本** |
| --- | --- |
| **PIN 或密碼設定** | 已修復 |   
| **裝置加密** | 已修復 (藉由設定 PIN 碼) |
| **已越獄或 Root 的裝置** | 隔離 (非設定)
| **電子郵件設定檔** | 已隔離 |
|**最低 OS 版本** | 已隔離 |
| **最高 OS 版本** | 已隔離 |  
| **Windows 健康情況證明** | 不適用 |  
----------------------------


**已補救** = 裝置作業系統強制符合規範。 (例如，強制使用者設定 PIN。)

**已隔離** = 裝置作業系統不強制符合規範。 (例如，Android 裝置不強制使用者為裝置加密。)裝置不相容時，會採取下列動作︰

- 如果對使用者套用了條件式存取原則，裝置會遭到封鎖。
- 公司入口網站會通知使用者任何合規性問題的相關事項。

## <a name="create-a-compliance-policy-in-the-azure-portal"></a>在 Azure 入口網站中建立合規性政策

1. 從 **Intune** 刀鋒視窗中，選擇 [設定裝置合規性]。 在 [管理] 中選擇 [All device compliance policies] (所有裝置合規性政策) 及 [建立]。
2. 輸入名稱及描述，然後選擇要套用此原則的平台。
3. 選擇 [合規性需求]，在此指定 [安全性]、[裝置健全狀況] 及 [裝置屬性]。完成設定後，請選擇 [確定]。

<!--- 4. Choose **Actions for noncompliance** to say what actions should happen when a device is determined as noncompliant with this policy.
5. In the **Actions for noncompliance** blade, choose **Add** to create a new action.  The action parameters blade allows you to specify the action, email recipients that should receive the notification in addition to the user of the device, and the content of the notification that you want to send.
7. The message template option allows you to create several custom emails depending on when the action is set to take. For example, you can create a message for notifications that are sent for the first time and a different message for final warning before access is blocked. The custom messages that you create can be used for all your device compliance policy.
7. Specify the **Grace period** which determines when that action to take place.  For example, you may want to send a notification as soon as the device is evaluated as noncompliant, but allow some time before enforcing the conditional access policy to block access to company resources like SharePoint online.
8. Choose **Add** to finish creating the action.
9. You can create multiple actions and the sequence in which they should occur. Choose **Ok** when you are finished creating all the actions.--->

## <a name="assign-user-groups"></a>指派使用者群組

若要將合規性政策指派給使用者，請選擇您先前設定的原則。 現有的原則可以在 [合規性 - 政策] 刀鋒視窗中找到。

1. 選擇您想要指派給使用者的原則，然後選擇 [指派]。 這會開啟刀鋒視窗讓您從中選取 [Azure Active Directory 安全性群組]，並將其指派給原則。
2. 選擇 [選取群組] 會開啟刀鋒視窗顯示 Azure AD 安全性群組。  選擇 [選取] 會將原則部署給使用者。

您已對使用者套用此原則。  要套用原則之使用者的裝置將會接受合規性評估。

<!---## Compliance policy settings--->

## <a name="system-security-settings"></a>系統安全性設定

### <a name="password"></a>密碼

- **需要密碼才可解除鎖定行動裝置**：將此設定為 [是] 會要求使用者必須輸入密碼才能存取其裝置。 使用密碼的 iOS 裝置會予以加密。
- **允許簡單密碼**︰將此項目設為 [是] 可允許使用者建立簡單密碼，例如 **1234** 或 **1111**。
- **最小密碼長度**：指定密碼至少須包含的數字位數或字元數。
- **需要的密碼類型**：指定使用者必須建立**英數字元**密碼或**數字**密碼。
- **字元集數目下限**︰若將 [需要的密碼類型] 設定為 [英數字元]，請使用此設定指定密碼至少須包含的最少字元集數。 四個字元集為：
  - 小寫字母
  - 大寫字母
  - 符號
  - 數字

若要將此設定設為較高的數目，使用者必須建立更複雜的密碼。

若是 iOS 裝置，此設定是指密碼中必須包含的特殊字元數 (例如 **!** 、**#**、**&amp;** )。

- **停止活動幾分鐘後需要輸入密碼**：指定閒置多久後使用者必須重新輸入密碼。
- **密碼到期 (天數)**：選取密碼到期前，必須建立新密碼的天數。
- **記住密碼歷程記錄**：此設定必須搭配 [不得重複使用以前用過的密碼] 一起使用，才能禁止使用者建立之前用過的密碼。
- **不得重複使用以前用過的密碼**：如有選取 [記住密碼歷程記錄]，請指定不得重複使用的舊密碼數。
- **裝置從閒置狀態恢復時必須輸入密碼**：此設定必須搭配 [停止活動幾分鐘後需要輸入密碼] 設定一起使用。 如果裝置達到 [在非使用狀態幾分鐘後需要輸入密碼] 設定所指定的閒置時間，系統會提示使用者輸入密碼，才能存取該裝置。

### <a name="email-profile"></a>電子郵件設定檔

- **電子郵件帳戶必須由 Intune 管理**：當此選項設定為 [是] 時，裝置必須使用部署到裝置的電子郵件設定檔。 在下列情況下，裝置視為不相容︰
  - 電子郵件設定檔部署到合規性政策的目標使用者群組以外的使用者群組。
  - 使用者已經在裝置上設定符合部署到該裝置之 Intune 電子郵件設定檔的電子郵件帳戶。 Intune 無法覆寫使用者所佈建的設定檔，因此也無法加以管理。 若要確保相容，使用者必須移除現有電子郵件設定。 然後 Intune 可以安裝受管理的電子郵件設定檔。
- **選取必須由 Intune 管理的電子郵件設定檔**︰如有選取 [必須由 Intune 管理電子郵件帳戶] 設定，請選擇 [選取]，以指定 Intune 電子郵件設定檔。 電子郵件設定檔必須在裝置上。

如需電子郵件設定檔的詳細資訊，請參閱[使用 Microsoft Intune 的電子郵件設定檔設定對公司電子郵件存取](https://docs.microsoft.com/en-us/intune/deploy-use/configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune)。

## <a name="device-health-settings"></a>裝置健全狀況設定

- **裝置不得經過越獄或 Root**︰如有啟用此設定，經過越獄的裝置將視為不符合規範。

## <a name="device-properties"></a>裝置內容

- **Minimum OS required** (需要的最低作業系統版本)：當裝置不符合最低作業系統版本需求時，會回報為不符合規範。 並顯示如何升級的資訊連結。 使用者可以選擇升級其裝置， 之後即可存取公司資源。
- **Maximum OS version allowed** (允許的最高 OS 版本)：當裝置使用的作業系統版本高於規則指定的版本時，會禁止存取公司資源，並要求使用者連絡其 IT 系統管理員。 在將規則變更為允許該 OS 版本之前，此裝置無法用來存取公司資源。

<!--- ## Next steps

[How to monitor device compliance](monitor-device-compliance.md)--->


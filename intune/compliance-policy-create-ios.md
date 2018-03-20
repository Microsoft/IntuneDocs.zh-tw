---
title: "在 Microsoft Intune 中建立 iOS 裝置相容性原則"
titleSuffix: 
description: "建立適用於 iOS 裝置的 Microsoft Intune 裝置相容性原則，以便您可以指定裝置必須符合的需求。"
keywords: 
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 02/22/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3cfb8222-d05b-49e3-ae6f-36ce1a16c61d
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: b024c846f9fc79fe214e3e90b094384455f2b086
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/08/2018
---
# <a name="how-to-create-a-device-compliance-policy-for-ios-devices-in-intune"></a>如何在 Intune 中為 iOS 裝置建立裝置合規性政策


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

適用於 iOS 的 Intune 裝置相容性原則指定 iOS 設備必須符合的規則和設置，才能視為相容。 當您使用裝置相容性原則搭配條件式存取時，可以允許或封鎖公司資源的存取。 您也可以取得裝置報表，並針對不相容採取動作。 在 Intune Azure 入口網站中，可以為每個平台建立裝置相容性原則。 若要更了解建立相容性原則之前必須滿足的先決條件，請參閱[裝置相容性入門](device-compliance-get-started.md)主題。

下表描述搭配使用合規性政策與條件式存取原則時，不相容設定的管理方式。

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

1. 登入 [Azure 入口網站](https://portal.azure.com)。
2. 選擇 [All services] (所有服務) > [Intune]。 Intune 位於 [Monitoring + Management] (監視 + 管理) 區段。
1. 從 [Intune] 頁面中，選擇 [裝置相容性]。 在 [管理] 中選擇 [原則]，然後選擇 [建立原則]。
2. 輸入名稱及描述，然後選擇要套用此原則的平台。
3. 選擇 [相容性需求]，在此指定 [系統安全性]、[裝置健全狀況] 及 [裝置屬性]。完成設定後，請選擇 [確定]。

<!--- 4. Choose **Actions for noncompliance** to say what actions should happen when a device is determined as noncompliant with this policy.
5. In the **Actions for noncompliance** pane, choose **Add** to create a new action.  The action parameters pane allows you to specify the action, email recipients that should receive the notification in addition to the user of the device, and the content of the notification that you want to send.
7. The message template option allows you to create several custom emails depending on when the action is set to take. For example, you can create a message for notifications that are sent for the first time and a different message for final warning before access is blocked. The custom messages that you create can be used for all your device compliance policy.
7. Specify the **Grace period** which determines when that action to take place.  For example, you may want to send a notification as soon as the device is evaluated as noncompliant, but allow some time before enforcing the conditional access policy to block access to company resources like SharePoint online.
8. Choose **Add** to finish creating the action.
9. You can create multiple actions and the sequence in which they should occur. Choose **Ok** when you are finished creating all the actions.--->

## <a name="assign-user-groups"></a>指派使用者群組

若要將合規性政策指派給使用者，請選擇您先前設定的原則。 現有的原則可以在 [裝置相容性 – 原則] 窗格中找到。

1. 選擇您想要指派給使用者的原則，然後選擇 [指派]。 隨即會開啟窗格讓您選取 **Azure Active Directory 安全性群組**，並將其指派給原則。
2. 選擇 [選取群組] 會開啟窗格顯示 Azure AD 安全性群組。  選擇 [儲存] 會將原則部署給使用者。

您已對使用者套用此原則。  要套用原則之使用者的裝置將會接受相容性評估。

<!---## Compliance policy settings--->

## <a name="system-security-settings"></a>系統安全性設定

### <a name="password"></a>密碼

- **需要密碼才可解除鎖定行動裝置**：設定為 [是] 會要求使用者必須輸入密碼才能存取其裝置。 使用密碼的 iOS 裝置會予以加密。
- **允許簡單密碼**︰設定為 [是] 會允許使用者建立如 **1234** 或 **1111** 的密碼。
- **最小密碼長度**：指定密碼至少須包含的位數或字元數。
- **必要的密碼類型**：指定使用者是否必須建立**英數**密碼或**數值**密碼。
- **字元集數目下限**︰如果您將 [必要的密碼類型] 設定為 [英數]，請使用此設定以指定密碼必須包含的字元集數目下限。 四個字元集為：
  - 小寫字母
  - 大寫字母
  - 符號
  - 數字

若設定較高的數目，使用者就必須建立較複雜的密碼。

若是 iOS 裝置，此設定是指密碼中必須包含的特殊字元數 (例如 **!** 、**#**、**&amp;** )。

- **在非使用狀態幾分鐘後需要輸入密碼**：指定使用者在經過多久閒置時間之後必須重新輸入密碼。
- **密碼到期 (天數)**：選取密碼到期前，必須建立新密碼的天數。
- **記住密碼歷程記錄**：此設定請與 [不得重複使用以前用過的密碼] 一起使用，以限制使用者建立以前用過的密碼。
- **不得重複使用以前用過的密碼**：如果已選取 [記住密碼歷程記錄]，請指定不得重複使用的舊密碼數目。
- **當裝置從閒置狀態返回時，需要密碼**：請搭配使用這項設定與 [在非使用狀態幾分鐘後需要輸入密碼] 設定。 如果裝置達到 [在非使用狀態幾分鐘後需要輸入密碼] 設定所指定的閒置時間，系統會提示使用者輸入密碼，才能存取該裝置。

### <a name="email-profile"></a>電子郵件設定檔

- **必須由 Intune 管理電子郵件帳戶**：將此選項設定為 [是] 時，裝置必須使用部署到裝置的電子郵件設定檔。 在下列情況下，裝置視為不相容︰
  - 電子郵件設定檔部署到合規性政策的目標使用者群組以外的使用者群組。
  - 使用者已經在裝置上設定符合部署到該裝置之 Intune 電子郵件設定檔的電子郵件帳戶。 Intune 無法覆寫使用者所佈建的設定檔，因此也無法加以管理。 若要確保相容，使用者必須移除現有電子郵件設定。 然後 Intune 可以安裝受管理的電子郵件設定檔。
- **選取必須由 Intune 管理的電子郵件設定檔**︰如果已選取 [必須由 Intune 管理電子郵件帳戶] 設定，請選擇 [選取] 以指定 Intune 電子郵件設定檔。 電子郵件設定檔必須在裝置上。

如需電子郵件設定檔的詳細資訊，請參閱[使用 Microsoft Intune 的電子郵件設定檔設定對公司電子郵件存取](https://docs.microsoft.com/intune-classic/deploy-use/configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune)。

## <a name="device-health-settings"></a>裝置健全狀況設定

- **不得破解裝置或刷機**︰如果您啟用此設定，破解的裝置將不相容。

## <a name="device-properties"></a>裝置內容

- **最低作業系統版本需求**︰當裝置不符合最低作業系統版本需求時，它會回報為不相容， 並顯示如何升級的資訊連結。 使用者可以選擇升級其裝置， 之後即可存取公司資源。
- **允許的最高作業系統版本**：當裝置使用的作業系統版本高於規則指定的版本時，會封鎖對公司資源的存取，並要求使用者連絡其 IT 系統管理員。在將規則變更為允許該 OS 版本之前，此裝置無法用來存取公司資源。

<!--- ## Next steps

[How to monitor device compliance](device-compliance-monitor.md)--->

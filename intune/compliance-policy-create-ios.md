---
title: 在 Microsoft Intune 中建立 iOS 裝置相容性原則 - Azure | Microsoft Docs
description: 建立適用於 iOS 裝置的 Microsoft Intune 裝置相容性原則，即可輸入電子郵件帳戶、檢查已進行 JB 破解的裝置、檢查最低與最高作業系統，以及設定密碼限制，包括密碼長度和裝置停止活動。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/20/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 3cfb8222-d05b-49e3-ae6f-36ce1a16c61d
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: b05eb725adb61ae47a24ca884d0e73ffe0dd269f
ms.sourcegitcommit: a22309174e617e59ab0cdd0a55abde38711a5f35
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/23/2018
---
# <a name="add-a-device-compliance-policy-for-ios-devices-in-intune"></a>如何在 Intune 中為 iOS 裝置新增裝置相容性原則

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Intune iOS 裝置相容性原則決定 iOS 設備必須符合的規則和設定，才能視為相容。 當您使用裝置相容性原則搭配條件式存取時，可以允許或封鎖公司資源的存取。 您也可以取得裝置報表，並針對不相容採取動作。 在 Intune Azure 入口網站中，可以為每個平台建立裝置相容性原則。 若要深入了解建立相容性原則之前必須滿足的先決條件，請參閱[開始使用 Microsoft Intune 裝置相容性原則](device-compliance-get-started.md)。

下表描述搭配使用合規性政策與條件式存取原則時，不相容設定的管理方式。

| **原則設定** | **iOS 8.0 及更新版本** |
| --- | --- |
| **PIN 或密碼設定** | 已修復 |
| **裝置加密** | 已修復 (藉由設定 PIN 碼) |
| **已越獄或 Root 的裝置** | 隔離 (非設定)
| **電子郵件設定檔** | 已隔離 |
|**最低 OS 版本** | 已隔離 |
| **最高 OS 版本** | 已隔離 |
| **Windows 健康情況證明** | 不適用 |

**已補救** = 裝置作業系統強制符合規範。 (例如，強制使用者設定 PIN。)

**已隔離** = 裝置作業系統不強制符合規範。 (例如，Android 裝置不強制使用者為裝置加密。)裝置不相容時，會採取下列動作︰

- 如果對使用者套用了條件式存取原則，裝置會遭到封鎖。
- 公司入口網站會通知使用者任何合規性問題的相關事項。

## <a name="create-a-compliance-policy-in-the-azure-portal"></a>在 Azure 入口網站中建立合規性政策

1. 登入 [Azure 入口網站](https://portal.azure.com)。
2. 選取 [All services] (所有服務)，篩選 [Intune]，然後選取 [Microsoft Intune]。
3. 選取 [裝置相容性] > [原則] > [建立原則]。
4. 輸入名稱及描述，然後選擇要套用此原則的平台。
5. 選擇 [設定] 輸入 [電子郵件]、[裝置健全狀況]、[裝置屬性] 和 [系統安全性] 設定。 完成後，選擇 [確定]。

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

## <a name="email"></a>電子郵件

- **必須由 Intune 管理電子郵件帳戶**：將此選項設定為 [是] 時，裝置必須使用部署到裝置的電子郵件設定檔。 在下列情況下，裝置視為不相容︰
  - 電子郵件設定檔部署到合規性政策的目標使用者群組以外的使用者群組。
  - 使用者已經在裝置上設定符合部署到該裝置之 Intune 電子郵件設定檔的電子郵件帳戶。 Intune 無法覆寫使用者所佈建的設定檔，因此也無法加以管理。 若要確保相容，使用者必須移除現有電子郵件設定。 然後 Intune 可以安裝受管理的電子郵件設定檔。
- **選取必須由 Intune 管理的電子郵件設定檔**︰如果已選取 [必須由 Intune 管理電子郵件帳戶] 設定，請選擇 [選取] 以指定 Intune 電子郵件設定檔。 電子郵件設定檔必須在裝置上。

如需電子郵件設定檔的詳細資訊，請參閱[使用 Microsoft Intune 的電子郵件設定檔設定對公司電子郵件存取](https://docs.microsoft.com/intune-classic/deploy-use/configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune)。

## <a name="device-health"></a>Device health

- **已進行 JB 破解的裝置**：如果您啟用此設定，已進行 JB 破解的裝置即不相容。
- **Require the device to be at or under the Device Threat Level** (裝置層級需要不高於裝置威脅層級)：選擇將裝置標記為不相容的最高威脅層級。 例如，如果您將威脅層級設定為 [中]，則中、低或安全的裝置都相容。 高威脅層級的裝置則不相容。

## <a name="device-properties"></a>裝置內容

- **最低作業系統版本需求**︰當裝置不符合最低作業系統版本需求時，它會回報為不相容， 您會看到如何升級的資訊連結。 使用者可以選擇升級其裝置， 之後即可存取公司資源。
- **允許的最高作業系統版本**：當裝置使用的作業系統版本高於規則指定的版本時，會封鎖對公司資源的存取。 然後要求使用者連絡其 IT 管理員。在將規則變更為允許該 OS 版本之前，此裝置無法存取公司資源。

## <a name="system-security"></a>系統安全性

### <a name="password"></a>密碼

> [!NOTE]
> 將相容性或設定原則套用至 iOS 裝置之後，系統每 15 分鐘會提示使用者設定密碼。 在設定密碼之前，使用者會一直收到系統提示。

- **需要密碼才可解除鎖定行動裝置**：設定為 [是] 會要求使用者必須輸入密碼才能存取其裝置。 使用密碼的 iOS 裝置會予以加密。
- **簡單密碼**︰設定為 [是] 會允許使用者建立如 **1234** 或 **1111** 這類的密碼。
- **最小密碼長度**：輸入密碼至少須包含的位數或字元數。
- **需要的密碼類型**：輸入使用者必須建立**英數字元**密碼或**數字**密碼。
- **密碼中的非英數字元數目**：輸入密碼中必須包含的最少特殊字元 (&、#、%、! 等等) 數目。

    若設定較高的數目，使用者就必須建立較複雜的密碼。

- **停止活動幾分鐘後需要輸入密碼**：輸入在閒置多久後，使用者必須重新輸入密碼。
- **密碼到期 (天數)**：選取密碼到期前，必須建立新密碼的天數。
- **避免重複使用前幾個密碼**：輸入不可使用先前使用的多少個密碼。

<!--- ## Next steps

[How to monitor device compliance](device-compliance-monitor.md)--->

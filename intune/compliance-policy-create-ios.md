---
title: 在 Microsoft Intune 中建立 iOS 裝置相容性原則 - Azure | Microsoft Docs
description: 建立或設定適用於 iOS 裝置的 Microsoft Intune 裝置合規性原則，即可輸入電子郵件帳戶、檢查已進行越獄的裝置、檢查最低與最高作業系統，以及設定密碼限制，包括密碼長度和裝置停止活動。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/14/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 3cfb8222-d05b-49e3-ae6f-36ce1a16c61d
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 41ae1ffc17eee93b45f00e4eef5590f6a5d0b7b4
ms.sourcegitcommit: 5058dbfb0e224207dd4e7ca49712c6ad3434c83c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/08/2018
ms.locfileid: "53112505"
---
# <a name="add-a-device-compliance-policy-for-ios-devices-in-intune"></a>如何在 Intune 中為 iOS 裝置新增裝置相容性原則

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune iOS 裝置相容性原則決定 iOS 設備必須符合的規則和設定，才能視為相容。 當您使用裝置相容性原則搭配條件式存取時，可以允許或封鎖公司資源的存取。 您也可以取得裝置報表，並針對不相容採取動作。 在 Intune Azure 入口網站中，可以為每個平台建立裝置相容性原則。 若要深入了解合規性原則，以及任何必要條件，請參閱[開始使用裝置合規性](device-compliance-get-started.md)。

下表描述搭配使用合規性政策與條件式存取原則時，不相容設定的管理方式。

---------------------------

| **原則設定** | **iOS 8.0 及更新版本** |
| --- | --- |
| **PIN 碼或密碼設定** | 已修復 |
| **裝置加密** | 已修復 (藉由設定 PIN 碼) |
| **已進行 JB 或 Root 破解的裝置** | 隔離 (非設定)
| **電子郵件設定檔** | 已隔離 |
|**最低 OS 版本** | 已隔離 |
| **最高 OS 版本** | 已隔離 |
| **Windows 健康情況證明** | 不適用 |

---------------------------

**已補救** = 裝置作業系統強制符合規範。 (例如，強制使用者設定 PIN。)

**已隔離** = 裝置作業系統不強制符合規範。 (例如，Android 裝置不強制使用者為裝置加密。)裝置不相容時，會採取下列動作︰

- 如果對使用者套用了條件式存取原則，裝置會遭到封鎖。
- 公司入口網站會通知使用者任何合規性問題的相關事項。

## <a name="create-a-device-compliance-policy"></a>建立裝置合規性政策

[!INCLUDE [new-device-compliance-policy](./includes/new-device-compliance-policy.md)]
4. 針對 [平台]，選取 [iOS]。 
5. 選擇 [設定組態]，並輸入本主題中所述的 [電子郵件]、[裝置健康情況]、[裝置內容]，以及 [系統安全性] 設定。 完成後，請選取 [確定] 和 [建立]。

<!--- 4. Choose **Actions for noncompliance** to say what actions should happen when a device is determined as noncompliant with this policy.
5. In the **Actions for noncompliance** pane, choose **Add** to create a new action.  The action parameters pane allows you to specify the action, email recipients that should receive the notification in addition to the user of the device, and the content of the notification that you want to send.
7. The message template option allows you to create several custom emails depending on when the action is set to take. For example, you can create a message for notifications that are sent for the first time and a different message for final warning before access is blocked. The custom messages that you create can be used for all your device compliance policy.
7. Specify the **Grace period** which determines when that action to take place.  For example, you may want to send a notification as soon as the device is evaluated as noncompliant, but allow some time before enforcing the conditional access policy to block access to company resources like SharePoint online.
8. Choose **Add** to finish creating the action.
9. You can create multiple actions and the sequence in which they should occur. Choose **Ok** when you are finished creating all the actions.--->

## <a name="email"></a>電子郵件

- **需要行動裝置具有受管理的電子郵件設定檔**：如果您將此項設定為 [要求]，則裝置若沒有 Intune 管理的電子郵件設定檔，就會視為不合規範。 當裝置未正確設為目標時，或者如果使用者手動設定裝置上的電子郵件帳戶，則裝置可能沒有受控電子郵件設定檔。

  在下列情況，裝置會被視為不相容︰
  - 電子郵件設定檔部署到合規性政策的目標使用者群組以外的使用者群組。
  - 使用者已經在裝置上設定符合部署到該裝置之 Intune 電子郵件設定檔的電子郵件帳戶。 Intune 無法覆寫使用者所佈建的設定檔，因此也無法加以管理。 若要確保相容，使用者必須移除現有電子郵件設定。 然後 Intune 可以安裝受管理的電子郵件設定檔。

- **選取必須由 Intune 管理的電子郵件設定檔**：如果選取 [電子郵件帳戶必須由 Intune 管理]，請選擇 [選取]，以指定必須用來管理裝置的 Intune 電子郵件設定檔。 電子郵件設定檔必須在裝置上。

如需電子郵件設定檔的詳細資訊，請參閱[使用 Microsoft Intune 的電子郵件設定檔設定對公司電子郵件存取](email-settings-configure.md)。

## <a name="device-health"></a>裝置健全狀況

- **破解的裝置**：如果您啟用此設定，已進行 JB 破解的裝置即不相容。
- **裝置須等於或低於裝置威脅等級** (iOS 8.0 及更新版本)：選擇最高威脅層級以將裝置標記為不符合規範。 超過此威脅層級的裝置會標示為不合規範：
  - **安全**：此選項最安全，因為裝置不能有任何威脅。 如果在裝置上偵測到任何等級的威脅，即評估為不符合規範。
  - **低**︰如果只有低等級的威脅，會將裝置評估為符合規範。 任何更高等級的威脅都會使裝置處於不相容狀態。
  - **中**︰如果裝置上的現有威脅是低等級或中等級，則會將裝置評估為符合規範。 如果在裝置上偵測到高等級的威脅，則會判斷為不相容。
  - **高**：此選項最不安全，且允許所有威脅層級。 如果此解決方案只用於報告用途，則此設定可能很實用。

## <a name="device-properties"></a>裝置內容

- **最低 OS 需求**：當裝置不符合最低 OS 版本需求時，會回報為不合規。 您會看到如何升級的資訊連結。 使用者可以選擇升級其裝置， 之後即可存取公司資源。
- **允許的最高作業系統版本**：當裝置使用的作業系統版本高於規則指定的版本時，會封鎖對公司資源的存取。 然後要求使用者連絡其 IT 管理員。在將規則變更為允許該 OS 版本之前，此裝置無法存取公司資源。
- **最低 OS 組建版本**：當 Apple 發佈安全性更新時，通常是更新組建編號，而不是 OS 版本。 使用此功能來輸入在裝置上允許的最低組建編號。 此合規性檢查支援執行 iOS 8.0 和更新版本的裝置。 
- **最高 OS 組建版本**：當 Apple 發佈安全性更新時，通常是更新組建編號，而不是 OS 版本。 使用此功能來輸入在裝置上允許的最高組建編號。 此合規性檢查支援執行 iOS 8.0 和更新版本的裝置。

## <a name="system-security"></a>系統安全性

### <a name="password"></a>密碼

> [!NOTE]
> 將相容性或設定原則套用至 iOS 裝置之後，系統每 15 分鐘會提示使用者設定密碼。 在設定密碼之前，使用者會一直收到系統提示。

- **需要密碼來解除鎖定行動裝置**：**要求**使用者輸入密碼，然後才能存取裝置。 使用密碼的 iOS 裝置會予以加密。
- **簡單密碼**：設定為 [封鎖] 時，使用者將無法建立 **1234** 或 **1111** 之類的簡單密碼。 設定為 [未設定] 時，使用者可以建立 **1234** 或 **1111** 之類的密碼。
- **密碼長度下限**：輸入使用者密碼中至少必須具有的數字位數或字元數。
- **必要的密碼類型**：選擇密碼是否應該只包含**數值**字元，或是應該混合數字和其他字元 (**英數字元**)。
- **密碼中的非英數字元數目**：輸入密碼中必須包含的最少特殊字元 (&、#、%、! 等等) 數目。

    若設定較高的數目，使用者就必須建立較複雜的密碼。

- **在停止活動最少幾分鐘後必須輸入密碼**：輸入使用者必須重新輸入密碼之前的閒置時間。
- **密碼到期 (天數)**：選取密碼到期，必須建立新密碼的天數。
- **避免重複使用以前用過的密碼次數**：輸入不得重複使用的舊密碼數。

### <a name="restricted-applications"></a>受限制的應用程式 
您可以透過將應用程式的套件組合識別碼新增至原則，來限制應用程式。 然後，如果裝置安裝該應用程式，就會標示為不相容。 
- **應用程式名稱**：輸入使用者易記的名稱來協助您識別套件組合識別碼。 
- **應用程式套件組合識別碼**：輸入應用程式提供者指派的唯一套件組合識別碼。 若要尋找套件組合識別碼，請參閱 [How to find the bundle ID for an iOS app](https://support.microsoft.com/help/4294074/how-to-find-the-bundle-id-for-an-ios-app) (如何尋找 iOS 應用程式的套件組合識別碼)。  

## <a name="assign-user-groups"></a>指派使用者群組

1. 選擇您已設定的原則。 現有的原則位於 [裝置合規性] > [原則]。
2. 選擇原則，然後選擇 [指派]。 您可以包含或排除 Azure Active Directory (AD) 安全性群組。
3. 選擇 [選取的群組] 以查看您的 Azure AD 安全性群組。 選取要套用這項原則的使用者群組，然後選擇 [儲存] 將原則部署給使用者。

您已對使用者套用此原則。 要套用原則之使用者的裝置將會接受相容性評估。

## <a name="next-steps"></a>後續步驟
[將電子郵件自動化，並為不符合規範的裝置新增動作](actions-for-noncompliance.md)  
[監視 Intune 裝置合規性原則](compliance-policy-monitor.md)

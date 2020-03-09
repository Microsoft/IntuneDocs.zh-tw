---
title: Microsoft Intune 中的裝置合規性原則 - Azure | Microsoft Docs
description: 使用裝置合規性政策入門、狀態和嚴重性等級的概觀、使用 InGracePeriod 狀態、使用條件式存取，以及處理未獲指派原則的裝置。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/13/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: samyada
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 45bcabf8c7dc932c9415fbd309bf09f53499fbcc
ms.sourcegitcommit: 045ca42cad6f86024af9a38a380535f42a6b4bef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2020
ms.locfileid: "77781940"
---
# <a name="set-rules-on-devices-to-allow-access-to-resources-in-your-organization-using-intune"></a>在裝置上設定規則可在您的組織中使用 Intune 存取資源

許多行動裝置管理 (MDM) 解決方案都藉由要求使用者和裝置符合一些需求來協助保護組織資料。 在 Intune 中，此功能稱為「合規性政策」。 合規性政策會定義使用者和裝置必須符合才能符合規範的規則和設定。 與條件式存取結合時，管理員可以封鎖不符合規則的使用者和裝置。

例如，Intune 系統管理員可以要求：

- 終端使用者使用密碼來存取行動裝置上的組織資料
- 裝置並未越獄或 Root 破解
- 裝置上最低或最高的作業系統版本
- 裝置等級必須等於或低於威脅等級

您也可以在組織中使用此功能來監視裝置上的合規性狀態。

> [!IMPORTANT]
> Intune 會遵循裝置簽入排程，以符合裝置上的所有合規性評估。 [原則和設定檔重新整理循環](../configuration/device-profile-troubleshoot.md#how-long-does-it-take-for-devices-to-get-a-policy-profile-or-app-after-they-are-assigned)列出預估的重新整理時間。

<!---### Actions for noncompliance

You can specify what needs to happen when a device is determined as noncompliant. This can be a sequence of actions during a specific time.
When you specify these actions, Intune will automatically initiate them in the sequence you specify. See the following example of a sequence of
actions for a device that continues to be in the noncompliant status for
a week:

- When the device is first determined to be noncompliant, an email with noncompliant notification is sent to the user.

- 3 days after initial noncompliance state, a follow up reminder is sent to the user.

- 5 days after initial noncompliance state, a final reminder with a notification that access to company resources will be blocked on the device in 2 days if the compliance issues are not remediated is sent to the user.

- 7 days after initial noncompliance state, access to company resources is blocked. This requires that you have Conditional Access policy that specifies that access from noncompliant devices should    be blocked for services such as Exchange and SharePoint.

### Grace Period

This is the time between when a device is first determined as
noncompliant to when access to company resources on that device is blocked. This time allows for time that the user has to resolve
compliance issues on the device. You can also use this time to create your action sequences to send notifications to the user before their access is blocked.

Remember that you need to implement Conditional Access policies in addition to compliance policies in order for access to company resources to be blocked.--->

## <a name="device-compliance-policies-work-with-azure-ad"></a>裝置合規性政策會與 Azure AD 一起運作

Intune 會使用 Azure Active Directory (AD) [條件式存取](https://docs.microsoft.com/azure/active-directory/conditional-access/overview) (開啟另一個 Docs 網站)，來協助強制執行合規性。 當裝置在 Intune 中註冊之後，Azure AD 註冊程序便會開始，而且裝置資訊會在 Azure AD 中更新。 其中一項關鍵的資訊就是裝置合規性狀態。 條件式存取原則會使用此合規性狀態，來封鎖或允許對電子郵件及其他組織資源的存取。

- [什麼是 Azure Active Directory 中的裝置管理](https://docs.microsoft.com/azure/active-directory/device-management-introduction)是不錯的資源，可了解在 Azure AD 中註冊裝置的原因和方式。

- [條件式存取](conditional-access.md)和[使用條件式存取的常見方式](conditional-access-intune-common-ways-use.md)描述這項功能，因為它與 Intune 相關。

## <a name="ways-to-use-device-compliance-policies"></a>使用裝置合規性政策的方式

### <a name="with-conditional-access"></a>使用條件式存取

針對符合政策規則的裝置，您可以將電子郵件及其他組織資源的存取權提供給它們。 如果裝置不符合政策規則，它們便無法存取組織資源。 這就是條件式存取。

### <a name="without-conditional-access"></a>不使用條件式存取

您也可以使用裝置合規性政策而不搭配任何條件式存取。 單獨使用合規性政策時，將會評估目標裝置，並回報其合規狀態。 例如，您可以取得有關下列內容的報告：未加密的裝置數，或者已越獄或 Root 破解的裝置。 當您使用合規性政策而不搭配條件式存取時，對組織資源不會有任何存取限制。

## <a name="ways-to-deploy-device-compliance-policies"></a>部署裝置合規性原則的方式

您可以將合規性政策部署至使用者群組中的使用者，或是裝置群組中的裝置。 將合規性政策部署到使用者時，即會檢查使用者所有裝置的相容性。 在 Windows 10 1803 版和更新版本的裝置上，「如果」  主要使用者未註冊裝置，則建議部署到裝置群組。 在此案例中使用裝置群組可協助進行合規性報告。

Intune 也包含一組內建的合規性政策設定。 下列內建政策會在 Intune 中註冊的所有裝置上進行評估：

- **將未指派合規性原則的裝置標記為**：此屬性有兩個值：

  - **符合規範** (預設值  )：關閉安全性功能
  - **不符合規範**：開啟安全性功能

  如果裝置未獲指派合規性政策，則預設會將此裝置視為不符合規範。 如果您搭配合規性政策使用條件式存取，建議您將預設設定變更為 [不符合規範]  。 如果使用者因為未指派政策而不符合規範，[公司入口網站應用程式](../apps/company-portal-app.md)就會顯示 `No compliance policies have been assigned`。

- **加強的越獄偵測**：啟用時，此設定會造成 iOS/iPadOS 裝置上更頻繁發生越獄裝置狀態。 此設定只會影響以封鎖越獄裝置之合規性政策為目標的裝置。 啟用此屬性會使用裝置的位置服務，並可能影響電池使用量。 Intune 不會儲存使用者的位置資料，此資料只會用來在背景中更頻繁地觸發越獄偵測。 

  啟用此設定會要求裝置：
  - 啟用 OS 層級的位置服務。
  - 一律允許公司入口網站使用位置服務。

  您可以透過開啟公司入口網站應用程式，或將裝置實際移動約 500 公尺以上的顯著距離來觸發評估。 在 iOS 13 和更新版上，只要裝置提示使用者繼續允許公司入口網站在背景中使用其位置，此功能會要求使用者選取 [一律允許]。 如果使用者不一律允許位置存取，且有設定此設定的原則，則其裝置會標示為不相容。 請注意，Intune 無法保證每次顯著的位置變更都會執行越獄偵測檢查，因為這取決於裝置當時的網路連線。

- **合規性狀態有效期限 (天)** ：輸入一段期間，裝置要在期間內回報所有收到的合規性政策狀態。 未在此期間內傳回狀態的裝置將被視為不相容。 預設值是 30 天。 最小值是 1 天。

  當預設合規性政策 ([裝置]   > [監視器]   > [設定合規性]  ) 為 [使用中]  時，就會顯示此設定。 此原則的背景工作每天執行一次。

您可以使用這些內建政策來監視這些設定。 Intune 也會在不同的時間間隔[重新整理或檢查更新](create-compliance-policy.md#refresh-cycle-times)，端視裝置平台而定。 [對於 Microsoft Intune 中的裝置政策和設定檔的常見疑問、問題和解決方式](../configuration/device-profile-troubleshoot.md)是不錯的資源。

合規性報告是檢查裝置狀態的絕佳方式。 [監視合規性政策](compliance-policy-monitor.md)包括一些指引。

## <a name="non-compliance-and-conditional-access-on-the-different-platforms"></a>不同平台上的不符合規範和條件式存取

下表描述搭配條件式存取原則使用合規性政策與時，系統如何管理不符合規範的設定。

---------------------------

|**原則設定**| **平台** |
| --- | ----|
| **PIN 或密碼設定** | - **Android 4.0 及更新版本**：已隔離<br>- **Samsung Knox Standard 4.0 及更新版本**：已隔離<br>- **Android Enterprise**：已隔離  <br>  <br>- **iOS 8.0 及更新版本**：已修復<br>- **macOS 10.11 及更新版本**：已修復  <br>  <br>- **Windows 8.1 及更新版本**：已修復<br>- **Windows Phone 8.1 及更新版本**：已修復|
| **裝置加密** | - **Android 4.0 及更新版本**：已隔離<br>- **Samsung Knox Standard 4.0 及更新版本**：已隔離<br>- **Android Enterprise**：已隔離<br><br>- **iOS 8.0 及更新版本**：已修復 (藉由設定 PIN 碼)<br>- **macOS 10.11 及更新版本**：已修復 (藉由設定 PIN 碼)<br><br>- **Windows 8.1 及更新版本**：不適用<br>- **Windows Phone 8.1 及更新版本**：已修復 |
| **已越獄或 Root 的裝置** | - **Android 4.0 及更新版本**：隔離 (非設定)<br>- **Samsung Knox Standard 4.0 及更新版本**：隔離 (非設定)<br>- **Android Enterprise**：隔離 (非設定)<br><br>- **iOS 8.0 及更新版本**：隔離 (非設定)<br>- **macOS 10.11 及更新版本**：不適用<br><br>- **Windows 8.1 及更新版本**：不適用<br>- **Windows Phone 8.1 及更新版本**：不適用 |
| **電子郵件設定檔** | - **Android 4.0 及更新版本**：不適用<br>- **Samsung Knox Standard 4.0 及更新版本**：不適用<br>- **Android Enterprise**：不適用<br><br>- **iOS 8.0 及更新版本**：已隔離<br>- **macOS 10.11 及更新版本**：已隔離<br><br>- **Windows 8.1 及更新版本**：不適用<br>- **Windows Phone 8.1 及更新版本**：不適用 |
| **最低 OS 版本** | - **Android 4.0 及更新版本**：已隔離<br>- **Samsung Knox Standard 4.0 及更新版本**：已隔離<br>- **Android Enterprise**：已隔離<br><br>- **iOS 8.0 及更新版本**：已隔離<br>- **macOS 10.11 及更新版本**：已隔離<br><br>- **Windows 8.1 及更新版本**：已隔離<br>- **Windows Phone 8.1 及更新版本**：已隔離 |
| **最高 OS 版本** | - **Android 4.0 及更新版本**：已隔離<br>- **Samsung Knox Standard 4.0 及更新版本**：已隔離<br>- **Android Enterprise**：已隔離<br><br>- **iOS 8.0 及更新版本**：已隔離<br>- **macOS 10.11 及更新版本**：已隔離<br><br>- **Windows 8.1 及更新版本**：已隔離<br>- **Windows Phone 8.1 及更新版本**：已隔離 |
| **Windows 健康情況證明** | - **Android 4.0 及更新版本**：不適用<br>- **Samsung Knox Standard 4.0 及更新版本**：不適用<br>- **Android Enterprise**：不適用<br><br>- **iOS 8.0 及更新版本**：不適用<br>- **macOS 10.11 及更新版本**：不適用<br><br>- **Windows 10 和 Windows 10 Mobile**：已隔離<br>- **Windows 8.1 及更新版本**：已隔離<br>- **Windows Phone 8.1 及更新版本**：不適用 |

---------------------------

**已補救**：裝置作業系統強制符合規範。 例如，強制使用者設定 PIN。

**已隔離**：裝置作業系統不強制符合規範。 例如，Android 和 Android Enterprise 裝置不強制使用者為裝置加密。 裝置不符合規範時，會採取下列動作：

- 如果條件式存取原則適用於使用者，就會封鎖裝置。
- 公司入口網站應用程式會通知使用者任何合規性問題的相關事項。

## <a name="next-steps"></a>後續步驟

- [建立政策](create-compliance-policy.md)並檢視必要條件。
- 請參閱適用於不同裝置平台的合規性設定：

  - [Android](compliance-policy-create-android.md)
  - [Android Enterprise](compliance-policy-create-android-for-work.md)
  - [iOS](compliance-policy-create-ios.md)
  - [macOS](compliance-policy-create-mac-os.md)
  - [Windows Holographic for Business](compliance-policy-create-windows.md#windows-holographic-for-business)
  - [Windows Phone 8.1](compliance-policy-create-windows-8-1.md)
  - [Windows 8.1 及更新版本](compliance-policy-create-windows-8-1.md)
  - [Windows 10 及以上版本](compliance-policy-create-windows.md)

- 如需有關 Intune 資料倉儲政策實體的詳細資訊，請參閱[政策實體的參考](../reports-ref-policy.md)。

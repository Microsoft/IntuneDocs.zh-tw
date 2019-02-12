---
title: Microsoft Intune 中的裝置合規性原則 - Azure | Microsoft Docs
description: 使用裝置合規性原則的需求、狀態和嚴重性等級的概觀、使用 InGracePeriod 狀態、使用條件式存取、處理沒有已指派原則的裝置，以及 Azure 入口網站與傳統入口網站中的 Microsoft Intune 合規性差異
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/28/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: a2a3a9838043d4e9b69c6369da87a6f54087f76c
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/07/2019
ms.locfileid: "55849997"
---
# <a name="get-started-with-device-compliance-policies-in-intune"></a>Intune 中的裝置合規性原則入門

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

許多行動裝置管理 (MDM) 解決方案都藉由要求使用者和裝置符合一些需求來協助保護組織資料。 在 Intune 中，此功能稱為「合規性政策」。 合規性政策會定義使用者和裝置必須符合才能符合規範的規則和設定。 與條件式存取結合時，系統管理員就可以封鎖不符合規則的使用者和裝置。 例如，Intune 系統管理員可以要求：

- 終端使用者使用密碼來存取行動裝置上的組織資料

- 裝置並未越獄或 Root 破解

- 裝置上最低或最高的作業系統版本

- 裝置等級必須等於或低於威脅等級

您也可以使用裝置合規性政策來監視裝置上的合規性狀態。

> [!IMPORTANT]
> Intune 會遵循裝置簽入排程，以符合裝置上的所有合規性評估。 [深入了解裝置簽入排程](https://docs.microsoft.com/intune/device-profile-troubleshoot#how-long-does-it-take-for-mobile-devices-to-get-a-policy-or-apps-after-they-have-been-assigned)。

<!---### Actions for noncompliance

You can specify what needs to happen when a device is determined as noncompliant. This can be a sequence of actions during a specific time.
When you specify these actions, Intune will automatically initiate them in the sequence you specify. See the following example of a sequence of
actions for a device that continues to be in the noncompliant status for
a week:

-   When the device is first determined to be noncompliant, an email with noncompliant notification is sent to the user.

-   3 days after initial noncompliance state, a follow up reminder is sent to the user.

-   5 days after initial noncompliance state, a final reminder with a notification that access to company resources will be blocked on the device in 2 days if the compliance issues are not remediated is sent to the user.

-   7 days after initial noncompliance state, access to company resources is blocked. This requires that you have conditional access policy that specifies that access from noncompliant devices should    be blocked for services such as Exchange and SharePoint.

### Grace Period

This is the time between when a device is first determined as
noncompliant to when access to company resources on that device is blocked. This time allows for time that the user has to resolve
compliance issues on the device. You can also use this time to create your action sequences to send notifications to the user before their access is blocked.

Remember that you need to implement conditional access policies in addition to compliance policies in order for access to company resources to be blocked.--->

## <a name="prerequisites"></a>必要條件

若要使用裝置合規性政策，請確定您：

- 使用下列訂用帳戶：

  - Intune
  - Azure Active Directory (AD) Premium

- 使用支援的平台：

  - Android
  - iOS
  - macOS (預覽)
  - Windows 8.1
  - Windows Phone 8.1
  - Windows 10

- 在 Intune 中註冊裝置以查看合規性狀態

- 向一位使用者註冊裝置，或者在沒有主要使用者的情況下進行註冊。 不支援向多位使用者註冊裝置。

## <a name="how-device-compliance-policies-work-with-azure-ad"></a>裝置合規性政策如何與 Azure AD 一起運作

當裝置在 Intune 中註冊之後，Azure AD 註冊程序便會開始，並將裝置屬性更新至 Azure AD。 其中一項關鍵的資訊就是裝置合規性狀態。 條件式存取原則會使用此合規性狀態，來封鎖或允許對電子郵件及其他公司資源的存取。

[Azure AD 註冊程序](https://docs.microsoft.com/azure/active-directory/device-management-introduction)提供了更多資訊。

## <a name="refresh-cycle-times"></a>重新整理週期時間

檢查合規性時，Intune 會使用與組態設定檔相同的重新整理週期。 通常會使用下列時間：

- iOS：每 6 小時
- macOS：每 6 小時
- Android：每 8 小時
- 註冊為裝置的 Windows 10 PC：每 8 小時
- Windows Phone：每 8 小時
- Windows 8.1：每 8 小時

裝置註冊之後，合規性檢查即會更頻繁地發生。

### <a name="assign-an-ingraceperiod-status"></a>指派 InGracePeriod 狀態

合規性原則的 InGracePeriod 狀態是一個值。 此值會由裝置寬限期與裝置該合規性原則實際狀態的組合來決定。

具體來說，若裝置的已指派合規性政策為 NonCompliant 狀態，且：

- 裝置沒有已指派的寬限期，則為合規性原則指派的值會是 NonCompliant
- 裝置的寬限期已過，則為合規性原則指派的值會是 NonCompliant
- 裝置的寬限期未到，則為合規性規則指派的值會是 InGracePeriod

下表摘要說明這些選項：

|實際合規性狀態|指派的寬限期值|有效合規性狀態|
|---------|---------|---------|
|NonCompliant |未指派任何寬限期 |NonCompliant |
|NonCompliant |昨天的日期|NonCompliant|
|NonCompliant |明天的日期|InGracePeriod|

如需有關監視裝置合規性政策的詳細資訊，請參閱[監視 Intune 裝置合規性政策](compliance-policy-monitor.md)。

### <a name="assign-a-resulting-compliance-policy-status"></a>指派最終合規性規則狀態

如果裝置有多個合規性原則，且裝置的兩個或更多個已指派的合規性原則具有不同的合規性狀態，系統就會指派單一的最終合規性狀態。 此指派會以指派至各合規性狀態的概念嚴重性等級為準。 每個合規性狀態均具下列嚴重性等級：

|狀態  |嚴重性  |
|---------|---------|
|Unknown     |1|
|NotApplicable     |2|
|符合標準|3|
|InGracePeriod|4|
|NonCompliant|5|
|錯誤|6|

當裝置具有多個合規性原則時，系統就會將所有原則的最高嚴重性等級指派給該裝置。

例如，假設裝置有三個合規性原則指派，分別為：Unknown 狀態 (嚴重性 = 1)、Compliant 狀態 (嚴重性 = 3)、InGracePeriod 狀態 (嚴重性 = 4)。 由於 InGracePeriod 狀態的嚴重性等級最高，因此全部三個原則的合規性狀態都會是 InGracePeriod。

## <a name="ways-to-use-device-compliance-policies"></a>使用裝置合規性政策的方式

#### <a name="with-conditional-access"></a>使用條件式存取
針對符合原則規則的裝置，您可以將電子郵件及其他公司資源的存取權提供給它們。 如果裝置不符合原則規則，它們便無法存取公司資源。 這就是條件式存取。

#### <a name="without-conditional-access"></a>不使用條件式存取
您也可以使用裝置合規性原則而不搭配任何條件式存取。 單獨使用合規性政策時，將會評估目標裝置，並回報其合規狀態。 例如，您可以取得有關下列內容的報告：未加密的裝置數，或者已越獄或 Root 破解的裝置。 當您使用合規性政策而不搭配條件式存取時，對組織資源不會有任何存取限制。

## <a name="ways-to-deploy-device-compliance-policies"></a>部署裝置合規性原則的方式
您可以將合規性政策部署至使用者群組中的使用者，或是裝置群組中的裝置。 將合規性政策部署到使用者時，即會檢查使用者所有裝置的相容性。 在 Windows 10 1803 版和更新版本的裝置上，「如果」主要使用者未註冊裝置，則建議部署到裝置群組。 在此案例中使用裝置群組可協助進行合規性報告。

系統會在所有 Intune 註冊的裝置上評估一組內建的合規性政策設定 ([Intune] > [裝置合規性])。 這些地方包括：

- **將未指派合規性原則的裝置標記為**：此屬性有兩個值：

  - **符合規範**：關閉安全性功能
  - **不符合規範** (預設值)：開啟安全性功能

  如果裝置沒有已指派的合規性原則，系統就會將此裝置視為不符合規範。 預設會將這些裝置標示為 [不符合規範]。 如果您使用條件式存取，建議您將設定變更為 [不符合規範]。 如果使用者因為未指派政策而不符合規範，公司入口網站就會顯示 `No compliance policies have been assigned`。

- **加強的越獄偵測**：啟用時，此設定會使 iOS 裝置更頻繁地使用 Intune 來簽入。 啟用此屬性會使用裝置的位置服務，並影響電池使用量。 Intune 不會儲存使用者位置資料。

  啟用此設定會要求裝置：
  - 啟用 OS 層級的位置服務
  - 允許公司入口網站使用位置服務
  - 至少每隔 72 小時對其越獄狀態進行一次評估並回報給 Intune。 否則，會將裝置標示為不符合規範。 您可以透過開啟公司入口網站應用程式，或實際將裝置移動 500 公尺以上來觸發評估。 如果裝置未在 72 小時內移動 500 公尺，使用者就必須開啟 [公司入口網站] 應用程式來進行加強的越獄評估。

- **合規性狀態有效期限 (天)**：輸入一段期間，裝置要在期間內回報所有收到的合規性政策狀態。 未在此期間內傳回狀態的裝置將被視為不相容。 預設值是 30 天。

所有裝置都有**內建裝置合規性政策** (Azure 入口網站 > [裝置合規性] > [原則合規性])。 您可以使用此內建原則來監視這些設定。

若要了解在部署原則之後，行動裝置需要多久才能取得原則，請參閱[針對裝置設定檔問題進行疑難排解](device-profile-troubleshoot.md#how-long-does-it-take-for-mobile-devices-to-get-a-policy-or-apps-after-they-have-been-assigned)。

合規性報告是檢查裝置狀態的絕佳方式。 如需相關指引，請參閱[監視合規性原則](compliance-policy-monitor.md)。

### <a name="actions-for-noncompliance"></a>不符合標準時所採取的動作
您可以設定一系列依時間排序的動作，以套用至未符合合規性原則準則的裝置。 這些在不符合規範時執行的動作可以自動化，如[將不符合規範時執行的動作自動化](actions-for-noncompliance.md)所述。

## <a name="azure-classic-portal-vs-azure-portal"></a>Azure 傳統入口網站與Azure 入口網站

在 Azure 入口網站中使用裝置合規性原則時的主要差異：

- 在 Azure 入口網站中，會針對每個支援的平台個別建立合規性原則
- 在 Azure 傳統入口網站中，所有支援的平台會使用一個通用的合規性原則

<!--- -   In the Azure portal, you have the ability to specify actions and notifications that are intiated when a device is determined to be noncompliant. This ability does not exist in the Intune admin console.

-   In the Azure portal, you can set a grace period to allow time for the end-user to get their device back to compliance status before they completely lose the ability to get company data on their device. This is not available in the Intune admin console.--->

## <a name="device-compliance-policies-in-the-classic-portal-and-azure-portal"></a>傳統入口網站與 Azure 入口網站中的裝置合規性原則

在[傳統入口網站](https://manage.microsoft.com)中建立的裝置合規性原則不會出現在 [Azure 入口網站](https://portal.azure.com)中。 不過，它們仍會以使用者作為目標，並可透過傳統入口網站管理。

若要在 Azure 入口網站中使用裝置合規性相關功能，您必須在 Azure 入口網站中建立新的裝置合規性原則。 若您在 Azure 入口網站中將某個裝置合規性原則指派給已從傳統入口網站獲指派裝置合規性原則的使用者，則來自 Azure 入口網站之裝置合規性原則的優先順序會高於在傳統入口網站中建立的原則。

## <a name="next-steps"></a>後續步驟

- 為下列平台建立裝置合規性政策：

  - [Android](compliance-policy-create-android.md)
  - [Android 工作設定檔](compliance-policy-create-android-for-work.md)
  - [iOS](compliance-policy-create-ios.md)
  - [macOS](compliance-policy-create-mac-os.md)
  - [Windows](compliance-policy-create-windows.md)

- 如需有關 Intune 資料倉儲原則實體的詳細資訊，請參閱[原則實體的參考](reports-ref-policy.md)。

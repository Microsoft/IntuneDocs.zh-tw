---
title: "Intune 裝置合規性政策"
titleSuffix: Azure portal
description: "使用本主題來了解 Microsoft Intune 中的裝置合規性"
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 2/6/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 98a9a93efb93697b454cb9bc06d1ac268ebaf9d8
ms.sourcegitcommit: cccbb6730a8c84dc3a62093b8910305081ac9d24
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/15/2018
---
# <a name="get-started-with-intune-device-compliance-policies"></a>開始使用 Intune 裝置合規性政策

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

## <a name="what-is-device-compliance-in-intune"></a>Intune 中的裝置合規性是什麼？

Intune 裝置合規性政策會定義裝置必須符合才能被 Intune 視為符合規範的規則與設定。

這些規則包括：

- 使用密碼才能存取裝置

- 加密

- 裝置為越獄或取得根權限破解

- 所需的最低 OS 版本

- 允許的最高 OS 版本

- 需要裝置層級不高於 Mobile Threat Defense

您也可以使用裝置合規性政策，來監視裝置的合規性狀態。

### <a name="device-compliance-requirements"></a>裝置合規性需求

合規性需求是一組基本規則，舉例來說，是否需要提供裝置 PIN 碼或加密就可以在合規性政策中指定。

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

##  <a name="pre-requisites"></a>必要條件

您需要有下列訂閱才能使用 Intune 的裝置合規性政策：

- Intune EMS

- Azure AD Premium

###  <a name="supported-platforms"></a>支援的平台：

-   Android

-   iOS

-   macOS (預覽)

-   Windows 8.1

-   Windows Phone 8.1

-   Windows 10

> [!IMPORTANT]
> 裝置必須在 Intune 註冊才能回報其合規性狀態。

## <a name="how-intune-device-compliance-policies-work-with-azure-ad"></a>Intune 裝置合規性政策如何與 Azure AD 一起運作

當裝置註冊到 Intune 時，Azure AD 註冊程序隨即開始，這會將裝置屬性及詳細資訊更新至 Azure AD。 裝置合規性狀態是重要的裝置資訊之一，條件式存取原則會用以禁止或允許存取電子郵件和其他公司資源。

- 深入了解 [Azure AD 註冊程序](https://docs.microsoft.com/en-us/azure/active-directory/device-management-introduction)。

### <a name="assigning-a-resulting-device-configuration-profile-status"></a>指派最終裝置組態設定檔狀態

若裝置有多個組態設定檔指派，且二或多個指派的組態設定檔具有不同的合規性狀態，就必須指派單一最終合規性狀態。 此指派會以指派至各合規性狀態的概念嚴重性等級為準。 每個合規性狀態均具下列嚴重性等級：


|狀態  |嚴重性  |
|---------|---------|
|Pending     |1|
|已成功     |2|
|Failed     |3|
|錯誤     |4|

為指派至裝置的所有設定檔選取最高嚴重性等級，即會指派二或多個組態設定檔的最終狀態。

舉例來說，假設裝置有三個設定檔指派，分別為：Pending 狀態 (嚴重性 = 1)、Succeeded 狀態 (嚴重性 = 2)、Error 狀態 (嚴重性 = 4)。 因為 Error 狀態的嚴重性等級最高，所以會指派為全部三個設定檔的最終合規性狀態。

### <a name="assigning-an-ingraceperiod-status-for-an-assigned-compliance-policy"></a>為指派的合規性政策指派 InGracePeriod 狀態

合規性政策 InGracePeriod 狀態值的判定，會綜合考量裝置的寬限期與裝置的實際狀態來得出指派的合規性政策。 

具體來說，若裝置的已指派合規性政策為 NonCompliant 狀態，且：

- 裝置沒有指派的寬限期，則為合規性政策指派的值為 NonCompliant。
- 裝置的寬限期已過，則為合規性政策指派的值為 NonCompliant。
- 裝置的寬限期未到，則為合規性政策指派的值為 InGracePeriod。

下表摘要了上述幾點：


|實際合規性狀態|指派的寬限期值|有效合規性狀態|
|---------|---------|---------|
|NonCompliant |未指派任何寬限期 |NonCompliant |
|NonCompliant |昨天的日期|NonCompliant|
|NonCompliant |明天的日期|InGracePeriod|

如需有關監視裝置合規性政策的詳細資訊，請參閱[監視 Intune 裝置合規性政策](compliance-policy-monitor.md)。

### <a name="assigning-a-resulting-compliance-policy-status"></a>指派最終合規性政策狀態

若裝置有多個合規性政策指派，且二或多個指派的合規性政策具有不同的合規性狀態，就必須指派單一最終合規性狀態。 此指派會以指派至各合規性狀態的概念嚴重性等級為準。 每個合規性狀態均具下列嚴重性等級： 

|狀態  |嚴重性  |
|---------|---------|
|Unknown     |1|
|NotApplicable     |2|
|符合標準|3|
|InGracePeriod|4|
|NonCompliant|5|
|錯誤|6|

為指派至裝置的所有原則選取最高嚴重性等級，即會指派二或多個合規性政策的最終狀態。
 
舉例來說，假設裝置有三個合規性政策指派，分別為：Unknown 狀態 (嚴重性 = 1)、Compliant 狀態 (嚴重性 = 3)、InGracePeriod 狀態 (嚴重性 = 4)。 因為 InGracePeriod 狀態的嚴重性等級最高，所以會指派為全部三個設定檔的最終合規性狀態。  

##  <a name="ways-to-use-device-compliance-policies"></a>使用裝置合規性政策的方式

### <a name="with-conditional-access"></a>使用條件式存取
合規性政策可與條件式存取原則搭配使用，只讓符合一或多條合規性政策規則的裝置存取電子郵件和其他公司資源。

### <a name="without-conditional-access"></a>不使用條件式存取
您也可以使用與條件式存取無關的裝置合規性政策。 單獨使用合規性政策時，將會評估目標裝置，並回報其合規狀態。 例如，您可以取得報告，列出未加密的裝置數，或是列出已遭越獄或取得根權限破解的裝置。 不過，單獨使用合規性原則時，對公司資源沒有存取限制。

您可以對使用者部署合規性政策。 將合規性政策部署到使用者時，即會檢查使用者裝置的相容性。 若要深入了解行動裝置在部署原則之後需要多長的時間才能取得原則，請參閱[針對 Microsoft Intune 中的裝置設定檔問題進行疑難排解](device-profile-troubleshoot.md#how-long-does-it-take-for-mobile-devices-to-get-a-policy-or-apps-after-they-have-been-assigned)。

#### <a name="actions-for-non-compliance"></a>處理不符合規範狀況的動作

不合規範狀況的動作可讓您設定一套依時間排序的動作，以套用至未達到合規性政策準則的裝置。 如需詳細資訊，請參閱[將不符合規範的動作自動化](actions-for-noncompliance.md)。

##  <a name="using-device-compliance-policies-in-the-intune-classic-portal-vs-azure-portal"></a>使用 Intune 傳統入口網站中的裝置合規性政策與Azure 入口網站

請注意 Azure 入口網站中協助您轉換至新裝置合規性政策工作流程的主要差異。

- 在 Azure 入口網站中，必須個別為各個支援平台建立合規性政策。
- 在 Intune 傳統入口網站中，所有支援平台可以共用同一個合規性政策。

<!--- -   In the Azure portal, you have the ability to specify actions and notifications that are intiated when a device is determined to be noncompliant. This ability does not exist in the Intune admin console.

-   In the Azure portal, you can set a grace period to allow time for the end-user to get their device back to compliance status before they completely lose the ability to get company data on their device. This is not available in the Intune admin console.--->

##  <a name="migrate-device-compliance-policies-from-the-intune-classic-portal-to-the-azure-portal"></a>將裝置合規性政策從 Intune 傳統入口網站移轉到 Azure 入口網站

在 [Intune 傳統入口網站](https://manage.microsoft.com)中建立的裝置合規性政策不會出現在新的 [Intune Azure 入口網站](https://portal.azure.com)中。 不過，它們仍會以使用者作為目標，並可透過 Intune 傳統入口網站管理。

如果您想要充分利用 Azure 入口網站中新的裝置合規性相關功能，您必須在 Azure 入口網站本身建立新的裝置合規性政策。 如果您在 Azure 入口網站中將新的裝置合規性政策指派給已從 Intune 傳統入口網站被指派裝置合規性政策的使用者，則 Intune Azure 入口網站的裝置合規性政策會優先於在 Intune 傳統入口網站中建立的裝置合規性政策。

##  <a name="next-steps"></a>接下來的步驟

- 為下列平台建立裝置合規性政策：

   - [Android](compliance-policy-create-android.md)
   - [Android for work](compliance-policy-create-android-for-work.md)
   - [iOS](compliance-policy-create-ios.md)
   - [macOS](compliance-policy-create-mac-os.md)
   - [Windows](compliance-policy-create-windows.md)

- 如需有關 Intune 資料倉儲原則實體的詳細資訊，請參閱[原則實體的參考](reports-ref-policy.md)。

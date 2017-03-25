---
title: "裝置合規性"
titleSuffix: Intune Azure preview
description: "Intune Azure 預覽版︰使用本主題深入了解 Microsoft Intune 的裝置合規性"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a916fa0d-890d-4efb-941c-7c3c05f8fe7c
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: cddeb6bf854b9ffbbc1744d5d164c8ceea34ff49
ms.openlocfilehash: 7d5a1859ef1a373ce424dd4f351fc137c6052fb7
ms.lasthandoff: 03/10/2017


---

# <a name="what-is-device-compliance-in-intune-azure-preview"></a>Intune Azure 預覽版的裝置合規性是什麼？

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Intune 中的裝置合規性政策定義裝置必須符合才能被 Intune 和 EMS 條件式存取原則視為符合規範的規則與設定。 您也可以使用裝置合規性政策，來監視和修復裝置的合規性問題。 

這些規則包括：

- 使用密碼才能存取裝置
- 加密
- 裝置為越獄或取得根權限破解
- 所需的最低 OS 版本
- 允許的最高 OS 版本
- 需要裝置層級不高於 Mobile Threat Defense

<!---##  Concepts
Following are some terms and concepts that are useful to understanding how to use compliance policies.

### Device compliance requirements
Compliance requirements are essentially rules like requiring a device PIN or encryption that you can specify as required or not required for a compliance policy.

### Actions for noncompliance

You can specify what needs to happen when a device is determined as noncompliant. This can be a sequence of actions during a specific time.
When you specify these actions, Intune will automatically initiate them in the sequence you specify. See the following example of a sequence of
actions for a device that continues to be in the noncompliant status for
a week:

-   When the device is first determined to be non-compliant, an email with noncompliant notification is sent to the user.

-   3 days after initial noncompliance state, a follow up reminder is sent to the user.

-   5 days after initial noncompliance state, a final reminder with a notification that access to company resources will be blocked on the device in 2 days if the compliance issues are not remediated is sent to the user.

-   7 days after initial noncompliance state, access to company resources is blocked. This requires that you have conditional access policy that specifies that access from noncompliant devices should    be blocked for services such as Exchange and SharePoint.

### Grace Period

This is the time between when a device is first determined as
noncompliant to when access to company resources on that device is blocked. This time allows for time that the user has to resolve
compliance issues on the device. You can also use this time to create your action sequences to send notifications to the user before their access is blocked.

Remember that you need to implement conditional access policies in addition to compliance policies in order for access to company resources to be blocked.--->

##  <a name="how-should-i-use-a-device-compliance-policy"></a>如何使用合規性政策？

### <a name="using-ems-conditional-access"></a>使用 EMS 條件式存取
合規性政策可與 EMS 條件式存取原則搭配使用，只讓符合一或多條合規性政策規則的裝置存取電子郵件和其他公司資源。

### <a name="not-using-ems-conditional-access"></a>不使用 EMS 條件式存取
您也可以使用與 EMS 條件式存取無關的裝置合規性政策。
單獨使用合規性政策時，將會評估目標裝置，並回報其合規狀態。 例如，您可以取得報告，列出未加密的裝置數，或是列出已遭越獄或取得根權限破解的裝置。 不過，單獨使用合規性政策時，對公司資源沒有存取限制。

您可以對使用者部署合規性政策。 將合規性政策部署到使用者時，即會檢查使用者裝置的相容性。 如需深入了解行動裝置在部署原則之後原則生效所需的時間，請參閱您裝置上的管理設定和功能。

##  <a name="intune-classic-admin-console-vs-intune-azure-preview-portal"></a>Intune 傳統管理主控台與Intune Azure 預覽版入口網站

若您一直以來都是使用 Intune 傳統管理主控台，在轉換到 Azure 入口網站的新裝置合規性政策工作流程之前，請留意下列差異︰

-   在 Azure 入口網站中，必須個別為各個支援平台建立合規性政策。 在 Intune 系統管理主控台中，所有支援平台可以共用同一個合規性政策。

<!--- -   In the Azure portal, you have the ability to specify actions and notifications that are intiated when a device is determined to be noncompliant. This ability does not exist in the Intune admin console.

-   In the Azure portal, you can set a grace period to allow time for the end-user to get their device back to compliance status before they completely lose the ability to get company data on their device. This is not available in the Intune admin console.--->

##  <a name="next-steps"></a>後續步驟

[開始使用裝置合規性政策](get-started-with-device-compliance.md)


<!---### See also

Conditional access--->


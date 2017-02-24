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
ms.sourcegitcommit: 153cce3809e24303b8f88a833e2fc7bdd9428a4a
ms.openlocfilehash: b245dac28f88e7eab70dfa9d759b15e155f8a7df


---

# <a name="what-is-device-compliance-in-intune-azure-preview"></a>Intune Azure 預覽版的裝置合規性是什麼？


[!INCLUDE[azure_preview](../includes/azure_preview.md)]

為協助保護公司資料，您必須確認用來存取公司應用程式及資料的裝置符合特定規則。 這些規則可能包括使用 PIN 來存取裝置，以及為裝置中儲存的資料加密。 這組規則稱為**合規性政策**。

##  <a name="how-should-i-use-a-device-compliance-policy"></a>如何使用合規性政策？
合規性政策可與條件式存取原則規配使用，只讓符合合規性政策規則的裝置存取電子郵件和其他服務。

您也可以使用單獨使用合規性政策而不使用條件式存取。
單獨使用合規性政策時，將會評估目標裝置，並回報其合規狀態。 例如，您可以取得報表列出未加密的裝置數，或是列出越獄或 root 破解的裝置數。 不過，單獨使用合規性政策時，對公司資源沒有存取限制。

您可以對使用者部署合規性政策。 將合規性政策部署到使用者時，即會檢查使用者裝置的相容性。 如需深入了解行動裝置在部署原則之後原則生效所需的時間，請參閱您裝置上的管理設定和功能。

##  <a name="concepts"></a>概念
下列詞彙及概念對於了解如何使用合規性政策十分實用。

### <a name="compliance-requirements"></a>合規性需求
合規性需求是一組基本規則，舉例來說，是否需要提供裝置 PIN 碼或加密就可以在合規性政策中指定。

<!---### Actions for noncompliance

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

##  <a name="differences-between-the-classic-intune-admin-console-and-intune-in-the-azure-portal"></a>傳統 Intune 系統管理主控台與 Azure 入口網站之 Intune 的差異


若您一直以來都是使用傳統 Intune 系統管理主控台，在移轉到 Azure 入口網站的新裝置合規性工作流程之前，請留意下列差異︰


-   在 Azure 入口網站中，必須個別為各個支援平台建立合規性政策。 在 Intune 系統管理主控台中，所有支援平台可以共用同一個合規性政策。


<!--- -   In the Azure portal, you have the ability to specify actions and notifications that are intiated when a device is determined to be noncompliant. This ability does not exist in the Intune admin console.

-   In the Azure portal, you can set a grace period to allow time for the end-user to get their device back to compliance status before they completely lose the ability to get company data on their device. This is not available in the Intune admin console.--->

##  <a name="next-steps"></a>後續步驟

[開始使用合規性政策](get-started-with-device-compliance.md)


<!---### See also

Conditional access--->



<!--HONumber=Feb17_HO3-->



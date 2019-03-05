---
title: Azure 入口網站中的 Intune 傳統群組
titleSuffix: Microsoft Intune
description: 了解 Microsoft Intune Azure 入口網站中群組的新功能。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 01/02/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 323f384d-8a76-4adc-999b-e508d641bfa1
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b96fc17bbe8a235d7bb2ae0c4710b3458a17b469
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/02/2019
ms.locfileid: "57231259"
---
# <a name="microsoft-intune-classic-groups-in-the-azure-portal"></a>Azure 入口網站中的 Microsoft Intune 傳統群組

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

我們已收到您的意見反應，將會對如何在 Microsoft Intune 中使用群組進行一些變更。
如果您從 Azure 入口網站使用 Intune，則您的 Intune 群組即已遷移至 Azure Active Directory 安全性群組。

對您而言，優點是您現在在所有 Enterprise Mobility + Security 和 Azure AD 應用程式都能使用相同的群組體驗。 此外，您還可以使用 PowerShell 和 Graph API 來擴充和自訂這項新功能。

Azure AD 安全性群組支援使用者和裝置的所有 Intune 部署類型。 此外，您還可以使用 Azure AD 動態群組，根據您提供的屬性自動進行更新。 例如，您可以建立可執行 iOS 9 的裝置群組。 只要註冊執行 iOS 9 的裝置，裝置就會自動出現在動態群組中。

## <a name="what-is-not-available"></a>不適用的範圍為？

Azure AD 中不提供您先前可能使用過的某些 Intune 群組功能︰

- 將不再提供 [已取消群組的使用者] 與 [已取消群組的裝置] Intune 群組。
- 從 Azure 入口網站中不存在的群組，[排除特定成員] 的選項。 不過，您可以搭配使用 Azure AD 安全性群組與進階規則來複寫這項行為。 例如，若要建立進階規則來包含安全性群組中 Sales 部門的所有人員，但排除職稱中有 "Assistant" 這個字的群組，您可以使用這個進階規則︰

  `(user.department -eq "Sales") -and -not (user.jobTitle -contains "Assistant")`。
- Intune 傳統主控台中的 [所有受 Exchange ActiveSync 管理的裝置] 群組將不會移轉至 Azure AD。 不過，您仍然可以從 Azure 入口網站存取 EAS 受管理裝置的相關資訊。

## <a name="how-to-get-started"></a>如何開始使用？

- 閱讀下列主題，以了解 Azure AD 安全性群組和其運作方式︰
    -  [使用 Azure Active Directory 群組來管理資源的存取權](https://azure.microsoft.com/documentation/articles/active-directory-manage-groups/)。
    -  [在 Azure Active Directory 中管理群組](https://azure.microsoft.com/documentation/articles/active-directory-accessmanagement-manage-groups/)。
    -  [使用屬性來建立進階規則](https://azure.microsoft.com/documentation/articles/active-directory-accessmanagement-groups-with-advanced-rules/)。
-  請確定將需要建立群組的系統管理員新增至 [Intune 服務管理員] Azure AD 角色。 Azure AD 服務系統管理員角色沒有 [管理群組] 權限。
-  如果您的 Intune 群組已使用 [排除特定成員] 選項，則請決定是否可以重新設計這些群組，而沒有排除項目，或者是否需要進階規則來符合商業需求。


## <a name="what-happened-to-intune-groups"></a>Intune 群組發生什麼事？
在 Azure 入口網站中，將群組從 Azure 入口網站移轉至 Intune 時，會套用下列規則︰

| Intune 中的群組|Azure AD 的群組|
|-----------------------------------------------------------------------|-------------------------------------------------------------|
|靜態使用者群組|靜態 Azure AD 安全性群組|
|動態使用者群組|含有 Azure AD 安全性群組階層的靜態 Azure AD 安全性群組|
|靜態裝置群組|靜態 Azure AD 安全性群組|
|動態裝置群組|動態 Azure AD 安全性群組|
|包含 include 條件的群組|靜態 Azure AD 安全性群組，包含 Intune 中 include 條件的任何靜態或動態成員|
|包含 exclude 條件的群組|未移轉|
|內建群組：<br>- **所有使用者**<br>- **已取消群組的使用者**<br>- **所有裝置**<br>- **已取消群組的裝置**<br>- **所有電腦**<br>- **所有行動裝置**<br>- **所有 MDM 管理裝置**<br>- **所有 EAS 管理裝置**|Azure AD 安全性群組|

## <a name="group-hierarchy"></a>群組階層

在 Intune 主控台中，所有群組都會有父群組。 群組只能包含其父群組的成員。 在 Azure AD 中，子群組可以包含其父群組中沒有的成員。

## <a name="group-attributes"></a>群組屬性
屬性是可用於定義群組的裝置內容。 本表說明這些準則如何移轉至 Azure AD 安全性群組。

| Intune 中的屬性|Azure AD 中的屬性|
|-----------------------------------------------------------------------|-------------------------------------------------------------|
|裝置群組的組織單位 (OU) 屬性|動態群組的 OU 屬性。|
|裝置群組的網域名稱屬性|動態群組的網域名稱屬性。|
|作為使用者群組屬性的安全性群組|群組不能是 Azure AD 動態查詢中的屬性。 動態群組只能包含使用者或裝置特定屬性。|
|使用者群組的 manager 屬性|動態群組中 *manager* 屬性的進階規則|
|父使用者群組中的所有使用者|該群組為成員的靜態群組|
|父裝置群組中的所有行動裝置|該群組為成員的靜態群組|
|Intune 所管理的所有行動裝置|'MDM' 為動態群組值的管理類型屬性|
|靜態群組內的巢狀群組 |靜態群組內的巢狀群組|
|動態群組內的巢狀群組|有一層巢狀的動態群組|

## <a name="what-happens-to-policies-and-apps-you-previously-deployed"></a>您先前部署的原則與應用程式會發生什麼事？

就像以前一樣，原則和應用程式會繼續部署到群組。 不過，您現在是從 Azure 入口網站管理這些群組，不是從 Intune 主控台。

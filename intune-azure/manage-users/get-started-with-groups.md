---
title: "開始使用 Intune Azure 入口網站預覽版中的群組 | Microsoft Docs"
description: "了解 Intune Azure 入口網站預覽版中群組的新功能"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angerobe
ms.date: 01/18/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 323f384d-8a76-4adc-999b-e508d641bfa1
translationtype: Human Translation
ms.sourcegitcommit: 990062ecf03a117dad74eb71e3f40abb79f22be6
ms.openlocfilehash: 27a9c9d8269b302fa9735972056d38e7919f42b5


---

# <a name="get-started-with-groups"></a>開始使用群組

[!INCLUDE[azure preview](../includes/azure_preview.md)]

我們已收到您的意見反應，將會對如何在 Microsoft Intune 中使用群組進行一些變更。
如果您從 Azure 入口網站使用 Intune，則您的 Intune 群組即已遷移至 Azure Active Directory 安全性群組。

對您而言，優點是您現在會對所有 Enterprise Mobility + Security 和 Azure AD 應用程式使用相同的群組體驗。 此外，您還可以使用 PowerShell 和 Graph API 來擴充和自訂這項新功能。

Azure AD 安全性群組支援使用者和裝置的所有 Intune 部署類型。 此外，您還可以使用 Azure AD 動態群組，根據您提供的屬性自動進行更新。 例如，您可以建立可執行 iOS 9 的裝置群組。 只要註冊執行 iOS 9 的新裝置，就會將它自動新增至動態群組。

## <a name="what-is-not-available"></a>不適用的範圍為？

Azure AD 中不提供您先前可能使用過的某些 Intune 群組功能︰

- 將不再提供 [已取消群組的使用者] 與 [已取消群組的裝置] Intune 群組。
- 從 Azure 入口網站中不存在的群組，[排除特定成員] 的選項。 不過，您可以搭配使用 Azure AD 安全性群組與進階規則來複寫這項行為。 例如，您可以建立進階規則來包含安全性群組中 Sales 部門的所有人員，而非職稱中有 "Assistant" 這個字的人員，方法是使用這個進階規則︰`(user.department -eq "Sales") -and -not (user.jobTitle -contains "Assistant")`。
- Intune 主控台內建的 [所有受 Exchange ActiveSync 管理的裝置] 群組，將不會遷移至 Azure AD。 不過，您仍然可以從 Azure 入口網站存取 EAS 受管理裝置的相關資訊。


## <a name="how-to-get-started"></a>如何開始使用？

- 閱讀下列 Azure AD 主題，以了解 Azure AD 安全性群組和其運作方式︰
    -  [使用 Azure Active Directory 群組來管理資源的存取權](https://azure.microsoft.com/en-us/documentation/articles/active-directory-manage-groups/)。
    -  [在 Azure Active Directory 中管理群組](https://azure.microsoft.com/en-us/documentation/articles/active-directory-accessmanagement-manage-groups/)。
    -  [使用屬性來建立進階規則](https://azure.microsoft.com/en-us/documentation/articles/active-directory-accessmanagement-groups-with-advanced-rules/)。
-  請確定將任何需要建立群組的系統管理員新增至 [Intune 服務管理員] Azure AD 角色。 請注意，Azure AD 服務系統管理員角色沒有 [管理群組] 權限。
-  如果使用群組時搭配選項 [排除特定成員]，請考慮是否可以將這些群組重新設計成不需要排除，或者是否可以在 Azure AD 查詢中使用進階規則，來達成相同的結果。


## <a name="what-happened-to-intune-groups"></a>Intune 群組發生什麼事？

| Intune 中的群組|Azure AD 中的群組|
|-----------------------------------------------------------------------|-------------------------------------------------------------|
|靜態使用者群組|靜態 Azure AD 安全性群組|
|動態使用者群組|含有 Azure AD 安全性群組階層的靜態 Azure AD 安全性群組|
|靜態裝置群組|靜態 Azure AD 安全性群組|
|動態裝置群組|動態 Azure AD 安全性群組|
|包含 include 條件的群組|靜態 Azure AD 安全性群組，包含 Intune 中 include 條件的任何靜態或動態成員|
|包含 exclude 條件的群組|未移轉|
|[所有使用者]、[已取消群組的使用者]、[所有裝置]、[已取消群組的裝置]、[所有電腦]、[所有行動裝置]、[所有 MDM 管理的裝置] 和 [所有 EAS 管理的裝置] 內建群組|Azure AD 安全性群組|

在 Intune 中，所有群組都必須有父群組。 群組只能包含其父群組中的成員。 在 Azure AD 中，子群組可以包含父群組沒有的成員。

屬性是可用於定義群組的裝置內容。 這個表格描述這些準則如何移轉至 Azure AD 安全性群組。

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

就像以前一樣，原則和應用程式會繼續部署到群組。 不過，您現在會從 Azure 入口網站管理這些群組，而不是從傳統 Intune 主控台。



<!--HONumber=Feb17_HO1-->



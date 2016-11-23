---
title: "移轉至 Azure Active Directory 群組| Microsoft Intune"
description: "如何將群組從 Intune 移轉至 Azure AD"
keywords: 
author: Mtillman
ms.author: mtillman
manager: angerobe
ms.date: 10/10/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 03b69afa-3548-4033-9039-191528f3fd99
translationtype: Human Translation
ms.sourcegitcommit: 17b957cc2baedddfc53bfdf7b875e4ecb28b8517
ms.openlocfilehash: e14bbadc4293b7b963197b35704a7170e4fc29e8


---

## <a name="the-new-admin-experience-for-groups"></a>群組的新管理體驗
    
根據您想要在整個企業行動和安全性中僅使用一個群組和目標體驗的意見反應，我們將 Intune 群組轉換到基於 Azure Active Directory 的安全性群組。 這會整合 Intune 和 Azure Active Directory (Azure AD) 之間的群組管理。 全新體驗將會讓您無須在服務之間複製群組，並且使用 PowerShell 和圖形提供擴充性。 

### <a name="how-and-when-will-i-migrate-to-the-new-groups-experience"></a>移轉至新群組體驗的的方式和時間點為何？
我們將會在一段時間之後移轉現有的客戶，最早會從 2016 年 12 月起開始。 您會在群組移轉之前收到通知。 如果您有任何移轉上的問題，請在 [intunegrps@microsoft.com](mailto:intunegrps@microsoft.com) 連絡我們的移轉小組。

### <a name="what-new-features-will-be-available-to-me"></a>會有哪些新功能可供我使用呢？
以下是所引進的新功能︰ 
 
-    將會針對所有的部署類型，在 Intune 中支援 Azure AD 安全性群組。 
-    Azure AD 安全性群組將支援裝置群組以及使用者。
-    Azure AD 安全性群組將使用 Intune 裝置屬性支援動態群組。 例如，您將能夠根據平台來動態地將裝置分組，如 iOS。 這樣一來，在您的組織中註冊新 iOS 裝置時，它將會自動加入 iOS 動態裝置群組中。
-    在 Azure AD 與 Intune 之間共用群組管理的系統管理員體驗。
- 「Intune 服務系統管理員角色」將會加入 Azure AD 中，以允許 Intune 中之服務系統管理員執行 Azure AD 中的群組管理工作。

 
### <a name="what-intune-functionality-wont-be-available"></a>哪些 Intune 功能將無法使用？
雖然群組體驗將會有所改善，但在移轉之後將會停止提供部分 Intune 功能。

#### <a name="group-management-functionality"></a>群組管理功能

-   當您建立新的群組時，您將無法排除成員或群組。 不過，Azure AD 動態群組可讓您使用屬性來建立進階規則，根據準則來排除成員。 例如，您可以建立進階規則來包含安全性群組中 Sales 部門的所有人員，而非職稱中有 "Assistant" 這個字的人員，而這個進階規則為︰`(user.department -eq "Sales") -and -not (user.jobTitle -contains "Assistant")`。 如需詳細資訊，請參閱[使用屬性建立進階規則](https://azure.microsoft.com/en-us/documentation/articles/active-directory-accessmanagement-groups-with-advanced-rules/)。
-   將不會支援 [已取消群組的使用者] 和 [已取消群組的裝置]  群組。 將不會移轉這些群組。

#### <a name="group-dependent-functionality"></a>群組的相依功能

-   服務系統管理員角色並不會擁有**管理群組**權限。
-   您無法將 Exchange ActiveSync 裝置分組。  您的 [所有 EAS 管理的裝置] 群組會從群組轉換成報表檢視。
-  報表中的群組樞紐分析將無法使用。
-  通知規則的自訂群組目標將無法使用。

### <a name="what-should-i-do-to-prepare-for-this-change"></a>我該如何為這項變更進行準備？
 我們有一些建議，讓這項轉換能夠更輕鬆地進行︰
 
- 先清除任何不想要或不需要的 Intune 群組，再進行移轉。
- 評估您在群組中如何使用排除，並考慮如何重新設計您的群組，使您不需要使用排除，或者，可以使用進階規則來達到相同目的。
-  如果您是不具有在 Azure AD 中建立群組權限的系統管理員，請您的 Azure AD 系統管理員將其加入 **Intune 服務管理員** Azure AD 角色中。

您也可以深入了解 Azure AD 安全性群組︰
-  如需概觀，請閱讀[使用 Azure Active Directory 群組管理資源存取](https://azure.microsoft.com/en-us/documentation/articles/active-directory-manage-groups/)。
-  如需如何建立和管理 Azure AD 群組的相關資訊，請參閱[在 Azure Active Directory 中管理群組](https://azure.microsoft.com/en-us/documentation/articles/active-directory-accessmanagement-manage-groups/)。
-  如需安全性群組進階規則的詳細資訊，請參閱[使用屬性建立進階規則](https://azure.microsoft.com/en-us/documentation/articles/active-directory-accessmanagement-groups-with-advanced-rules/)。

> [!NOTE]
您可能會注意到 Azure AD 安全性群組文件未討論如何建立裝置的群組。 開始移轉 Intune 群組之前，將會在 Azure AD 中啟用該功能。

## <a name="migration-details"></a>移轉詳細資料
以下是如何將 Intune 群組移轉至 Azure AD 安全性群組的詳細資料。

### <a name="migration-of-existing-groups"></a>現有群組移轉

| Intune 群組會變成...|...Azure AD 安全性群組|
|-----------------------------------------------------------------------|-------------------------------------------------------------|
|Intune 原則設為目標的靜態使用者群組|包含相同使用者的靜態 Azure AD 安全性群組|
|Intune 原則設為目標的動態使用者群組|含有 Azure AD 安全性群組階層的靜態 Azure AD 安全性群組|
|Intune 原則設為目標的靜態裝置群組|含有裝置的靜態 Azure AD 安全性群組|
|Intune 原則設為目標且含有裝置屬性的動態裝置群組|含有裝置屬性的動態 Azure AD 安全性群組|
|包含 include 條件的群組|個別靜態 Azure AD 安全性群組，將包含一個群組 + include 條件已在 Intune 中允許的任何靜態/動態成員|
|包含 exclude 條件的群組|...將不會進行移轉。 在 Azure AD 中建立靜態群組期間不支援 Exclude 條件。 在 Azure AD 中建立動態群組時，可以使用 Exclude 條件。|
|在 Intune 原則中使用的 [所有使用者]、[已取消群組的使用者]、[所有裝置]、[已取消群組的裝置]、[所有電腦]、[所有行動裝置]、[所有 MDM 管理的裝置] 和 [所有 EAS 管理的裝置] 預設群組  |Azure AD 安全性群組。 使用動態群組時，客戶必須在必要時建立未使用的預設群組。|

### <a name="changes-in-hierarchical-views"></a>階層檢視中的變更
Intune 內 Intune 父子式關聯性中群組的階層檢視是超集子集式關聯性，而在 Azure AD 中則不是這種情況。 子系可以有父系沒有的成員。 在 Azure AD 中，群組本質上也可以是循環的 - 父群組可以是子群組的子系。

### <a name="attribute-conversion-during-migration"></a>移轉期間的屬性轉換
屬性是可用於定義群組的裝置內容。 這個表格描述這些準則如何移轉至 Azure AD 安全性群組。

| Intune 屬性|Azure AD 屬性|
|-----------------------------------------------------------------------|-------------------------------------------------------------|
|裝置群組的組織單位 (OU) 屬性|動態群組的 OU 屬性。 可讓與每個租用戶有關的系統管理員使用的屬性值，方法是將它新增為其中一個租用戶元件來進行檢視。|
|裝置群組的網域名稱屬性|動態群組的網域名稱屬性。 可讓與每個租用戶有關的系統管理員使用的屬性值，方法是將它新增為其中一個租用戶元件來進行檢視|
|作為使用者群組屬性的安全性群組|群組不能是 Azure AD 動態查詢中的屬性。 動態群組只能包含使用者或裝置特定屬性。|
|使用者群組的 manager 屬性|動態群組中 *manager* 屬性的進階規則|
|父使用者群組中的所有使用者|該群組為成員的靜態群組|
|父裝置群組中的所有行動裝置|該群組為成員的靜態群組|
|Microsoft Intune 直接管理所管理的所有行動裝置|'MDM' 為動態群組值的管理類型屬性|
|EAS 所管理的所有行動裝置|EAS 裝置無法在 Azure AD 中進行群組。 您的 [所有 EAS 管理的裝置] 群組會從群組轉換成報表檢視。|
|靜態群組內的巢狀群組 |靜態群組內的巢狀群組|
|動態群組內的巢狀群組|有一層巢狀的動態群組|


## <a name="migration-of-policies"></a>原則移轉
正在進行群組移轉時，您將繼續在 Intune 主控台中管理原則。 Intune 主控台中會有 Azure 管理主控台連結，而您可以在 Azure 管理主控台連結中管理群組。 您的原則將會繼續部署至與舊 Intune 群組平行的已移轉 Azure AD 安全性群組。

所有 Intune 的功能移轉至 Azure 管理入口網站 (大約是 2017 年第一季) 時，您將在該處管理原則和群組。

     
### <a name="see-also"></a>請參閱
[使用 Azure Active Directory 群組管理資源存取](https://azure.microsoft.com/en-us/documentation/articles/active-directory-manage-groups/)

[在 Azure Active Directory 中管理群組](https://azure.microsoft.com/en-us/documentation/articles/active-directory-accessmanagement-manage-groups/)

[使用屬性建立進階規則](https://azure.microsoft.com/en-us/documentation/articles/active-directory-accessmanagement-groups-with-advanced-rules/)



<!--HONumber=Nov16_HO1-->



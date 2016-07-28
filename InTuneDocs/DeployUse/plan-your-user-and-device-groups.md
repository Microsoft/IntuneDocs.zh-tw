---
title: "規劃您的使用者和裝置群組 | Microsoft Intune"
description: "規劃群組以符合組織需求。"
keywords: 
author: nbigman
manager: Arob98
ms.date: 07/21/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f11bb256-1094-4f7e-b826-1314c57f3356
ms.reviewer: lpatha
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 72288296d966b9b9fae4fd721b4460528213f626
ms.openlocfilehash: 73909ebf2226b4fa50ad39b095a7cc1d73460c65


---

# 規劃您的使用者和裝置群組
Intune 中的「群組」可讓您在管理裝置和使用者上擁有絕佳彈性。 您可以根據下列各項來設定群組以符合組織需求：

- 地理位置
- department
- 硬體特性
- 作業系統
- 裝置是使用者擁有或公司擁有


## Intune 群組如何運作


在 Intune 管理主控台中，[群組] 節點的預設檢視為︰

![Intune 主控台中群組節點的螢幕擷取畫面](/intune/media/Intune_Planning_Groups_Default_small.png)

原則會部署到群組，因此群組階層是您的重要設計考量之一。 同時也一定要知道，一旦建立群組之後，便不能變更群組的父群組，因此您的群組設計，從您開始使用 Intune 服務的那一刻起便非常重要。 一些根據組織需求設計群組階層的建議做法如下所示。

## 群組成員資格規則

1. 群組可包含使用者或裝置，但不能同時包含兩者。

    * **裝置群組** ：此群組包括電腦和行動裝置。 新增電腦到群組之前，您必須先註冊電腦。 新增行動裝置到群組之前，您的環境必須先設定成可支援行動裝置，且必須註冊裝置，或是從 Exchange ActiveSync 探索裝置。

    * **使用者群組：** 群組可以包含安全性群組中的使用者；安全性群組是從您的 Active Directory 同步處理的群組。 如果您並未使用 Active Directory 同步處理，可以手動建立這些群組。

2. 單一裝置或使用者可隸屬於多個群組。

3. 群組可以根據下列成員資格規則來包含及排除成員：

    * **準則成員資格：** 這些規則屬於動態規則，Intune 會執行這些規則來包含或排除成員。 這些準則使用從您的本機 Active Directory (AD) 同步處理的**安全性群組**和其他資訊。 安全性群組或資料變更時，群組成員資格會在您與 AD 同步處理時變更。

    * **直接成員資格：** 這些規則是會明確新增或排除成員的靜態規則。 成員資格清單是靜態清單。

4. 建立包含使用者或電腦的使用者群組或裝置群組時並不需要 Active Directory 網域服務 (AD DS)，但是如果您要在裝置群組中包含行動裝置，則必須將環境設定成可支援行動裝置。

    此外，您還必須探索裝置並將它們新增到 Intune。

## 群組關聯性規則

1. 您建立的每個群組都必須有父群組，而且一旦建立群組之後，您便無法變更該群組的父群組。

2. 新增使用者或裝置到子群組時：

    * 子群組一定是父群組的子集。

    * 您新增到子群組的新成員會自動新增到該群組的父群組。

    * 您不能將從父群組排除的成員新增到子群組。

3. 父群組的成員資格限定了子群組的可用成員資格。

4. 當您刪除父群組時，將會刪除所有的子群組。

5. 您可以將內容和原則部署到父群組，但排除部署到子群組。

6. 您可以將特定使用者或裝置新增到不是父群組成員的子群組。 如果您這樣做，新的群組成員將會新增到父群組。

    不過，您不能將從父群組排除的成員新增到子群組。

7. 群組成員資格具遞迴性質。 例如：

    * **Pat** 只隸屬於一個群組：[膝上型電腦使用者]  安全性群組。

    * [膝上型電腦使用者]  群組是 [已核准的使用者]  安全性群組的成員。

    * 您在 Intune 中建立一個群組，而這個群組使用包含 [已核准的成員] 群組成員的動態成員資格查詢。 結果是您的 Intune 使用者群組包含 **Pat**。

> [!TIP]
> 當您建立群組時，請考慮將如何套用原則。 例如，您可能會有裝置作業系統特定的原則，以及組織中不同角色特定的原則，或是您已經定義於 Active Directory 中組織單位特定的原則。 有些人認為具有 iOS、Android 及 Windows 特定的裝置群組，以及適用於每個組織角色的使用者群組是非常實用的。

<!--- should we just link to a policies topic at this point and remove this? Ask Rob
 You'll probably want to create a default policy that applies to all groups and devices, to establish the basic compliance requirements of your company. Then create more specific policies for the broadest categories of users and devices, for example, email policies for each of the device operating systems.

 Be careful naming your policies so that you can easily identify them later. For example, a good, descriptive policy name is **WP Email Policy for Entire Company**.

 Each time you create a restrictive policy you'll want to communicate it to your users, so after you create the more general groups and policies pay attention to how you create smaller groups so that you can reduce unnecessary communication.--->

## 內建群組
Intune 提供九個內建群組，您無法加以編輯或刪除： <!--maybe a screen shot would be best?-->

-   **所有使用者**
    -   已取消群組的使用者
-   **所有裝置**
    -   所有電腦
    -   所有行動裝置
        -   所有受直接管理的裝置
        -   所有受 Exchange ActiveSync 管理的裝置
    -   公司擁有的所有裝置
    -   已取消群組的裝置

> [!NOTE]
> 讓您的座右銘成為︰*保持簡單*。 如果您的組織沒有像是以下所述的特定需求，那麼保持簡單並採用預設群組結構和原則會讓服務長期來看更容易管理。 如果您能相同地對待您的使用者，但在各群組之間略有區別，則維護會比較簡單，因為需要維護的原則較少。


### 組織中的所有使用者及裝置
請為組織中的所有使用者和裝置定義父群組，因為您可能會有適用於全體的原則。 針對此目的，您可以在 Intune 中使用預設的**所有使用者**和**所有裝置**群組。 依特性組織裝置的子群組，例如一個群組給攜帶您自己的裝置 (BYOD)，而另一個群組用於公司擁有的裝置 (CO)，可以是**所有使用者**和**所有裝置**父群組的子系。

## 自訂您的組織的群組

### BYOD 與屬公司擁有的裝置
如果您的組織允許員工在公司使用自己的裝置 (BYOD)、提供公司擁有的裝置 (CO)，或兩者的組合，建議您根據這兩個類別的裝置套用原則。

如果是 BYOD 或混合，請仔細規劃不會侵犯當地隱私權法規的原則。 為攜帶自己裝置的所有使用者建立父群組。 此群組便可用來套用適用於此類別中所有使用者的原則。

![建立 BYOD 父群組的螢幕擷取畫面](/intune/media/Intune_Planning_Groups_BYOD_small.png)

同樣地，您可以為組織中的 CO 使用者建立群組︰

![BYOD 和 CO 的同層級使用者群組的螢幕擷取畫面](/intune/media/Intune_Planning_Groups_BYOD_Hierachy_View_small.png)

<!---START HERE--->

### 地理區域的群組
如果您的組織需要特定地區的原則，您可以根據地理區域建立群組。 您可以根據您可能已經在 Active Directory (AD) 中建立的區域群組，並予以同步處理至 Azure AD。 您也可以直接在 Azure AD 中建立它們。

這些螢幕擷取畫面顯示如何根據從內部部署 AD 同步處理的群組建立 Intune 群組。 此範例假設您有稱為**美國使用者群組**的 AD 安全性群組。

1. 首先，提供一般資訊。

![編輯群組區域的螢幕擷取畫面](/intune/media/Intune_Planning_Groups_AD_General_small.png)

在 [成員資格] 準則下選取 [美國使用者群組]、從 AD 同步處理，作為要在成員資格規則之下使用的安全性群組。

![編輯群組對話方塊](/intune/media/Intune_Planning_Groups_AD_Criteria_small.png)

檢閱內容，然後按一下 [完成] 以完成建立群組。

![編輯群組對話方塊](/intune/media/Intune_Planning_Groups_AD_Summary_small.png)

在範例中，我們也建立了中東和亞洲群組 MEA。

> [!NOTE]
> 如果未以安全群組成員資格來填入群組成員資格，請檢查您是否已指派 Intune 授權給這些成員。

### 特定硬體的群組
如果您的組織需要適用於特定硬體類型的原則，您可以根據這項需求建立群組。 您可以根據已經在內部部署 AD 中建立的特定群組，並予以同步處理至 Azure AD。 您也可以直接在 Azure AD 中建立它們。 在此範例中，我們使用 [美國使用者群組] 作為 [膝上型電腦使用者] 群組的父群組。

![選取安全性群組對話方塊](/intune/media/Intune_Planning_Groups_Laptop_small.png)

此時，群組階層應該如下所示。 如您所見，現在在 Intune 群組 [膝上型電腦使用者]  內有成員。 套用到此群組的任何原則，現在將套用到來自美國地區的 BYOD 膝上型電腦使用者。

![膝上型電腦使用者群組的顯示](/intune/media/Intune_Planning_Groups_Laptop_Hierarchy_small.png)

### 特定作業系統的群組
如果您的組織要求適用於特定作業系統，例如 Android、iOS 或 Windows 等的原則，您可以根據此需求建立群組。 在上述範例中，您可以根據已經在內部部署 AD 中建立的作業系統特定群組，並予以同步處理至 Azure AD。 您也可以在 Azure AD 中直接建立它們。

依照前列範例的方法，我們可以使用特定作業系統平台的使用者 <!--devices?--> 為依據來建立群組。

> [!NOTE]
> 如果您的使用者會使用多種行動平台/作業系統，且沒有自動化的方式來將使用者分類為 Android 使用者、iOS 使用者或 Windows 使用者，請考慮在裝置層級套用原則，這樣會提供您較大的彈性來套用 OS 特定原則。
>
> 您無法根據裝置的作業系統動態佈建群組。 請使用 AD 或 AAD 安全性群組執行這項操作。

![膝上型電腦使用者群組的顯示](/intune/media/Intune_Planning_Groups_OS_Hierachy_small.png)

一旦您的所有使用者群組都已根據這些組織需求填入，群組階層看起來應該像這樣︰

![群組階層檢視](/intune/media/Intune_Planning_Groups_Midpoint_Hierachy_small.png)

這個階層可以用來適當地套用組織的原則。

### 裝置群組
您也可以如下所示，為裝置建立類似的群組，例如 BYOD 案例，從包含所有屬員工擁有之裝置的廣泛群組開始︰

![建立群組對話方塊](/intune/media/Intune_Planning_Groups_Device_General_small.png)

確定您選取 [所有裝置 (電腦和行動裝置)]，讓群組包含所有 BYO 裝置︰

![定義成員資格準則頁面](/intune/media/Intune_Planning_Groups_Device_Criteria_small.png)

檢閱內容，然後選擇 [完成] 以建立 BYOD 群組。

![建立群組對話方塊](/intune/media/Intune_Planning_Groups_Device_Summary_small.png)

繼續建立裝置群組，直到您的裝置群組階層類似於使用者群組階層。 然後，Intune 主控台中的群組節點看起來應該像這樣︰

![Intune 群組階層檢視](/intune/media/Intune_Groups_Hierarchy_Final_Small.png)

## 群組階層和命名慣例
為了讓原則的管理更輕鬆，我們建議您依據用途、平台和其套用範圍來命名每個原則。 這個命名標準應該遵循您在準備套用原則時建立的群組結構。

例如要套用到在美國地區層級之所有公司裝置、Android 裝置及行動裝置的 Android 原則，可以命名為 **CO_US_Mob_Android_General**。

![建立 Android 的原則](/intune/media/Intune_planning_policy_android_small.png)

藉由這種原則命名方式，您可以從主控台的原則節點快速識別原則及其用途和範圍，如下所示︰

![Intune 原則清單](/intune/media/Intune_planning_policy_view_small.png)

## 後續步驟
[建立群組](use-groups-to-manage-users-and-devices-with-microsoft-intune.md)



<!--HONumber=Jul16_HO3-->



---
title: "使用群組管理使用者和裝置 | Microsoft Docs"
description: "使用 [群組] 工作區建立及管理群組。"
keywords: 
author: Mtillman
ms.author: mtillman
manager: angrobe
ms.date: 12/15/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: eb9b01ce-9b9b-4c2a-bf99-3879c0bdaba5
ms.reviewer: lpatha
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 095b8db0cb5097edca98d138edccafbe8e55b9ba
ms.contentlocale: zh-tw
ms.lasthandoff: 05/23/2017


---
# <a name="use-groups-to-manage-users-and-devices-in-microsoft-intune"></a>在 Microsoft Intune 中使用群組管理使用者和裝置

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

本主題說明如何在 Intune 中建立群組。 此外，也提供關於群組的管理在未來幾個月內將如何變更的資訊。 

>[!IMPORTANT]
>
>如果您在 Intune 入口網站中開啟 [群組] 工作區，並看到 Azure Active Directory (Azure AD) 入口網站的連結，即表示您在 Intune 中使用的是「新的」Azure AD 安全性群組方法來管理群組，如[將群組移轉至 Azure Active Directory](migrating-groups-to-azure-active-directory.md) 中所述。 按一下 Azure AD 入口網站的連結，即可建立及管理您的群組。
>
>![Azure 群組管理連結螢幕擷取畫面](../media/groups-link-azure.png) 
>
>如果您看不到 Azure AD 入口網站的連結，則表示您仍使用「目前的」方法進行群組管理，如本主題的[使用 Microsoft Intune 建立群組以管理使用者和裝置](#Create-groups-to-manage-users-and-devices-with-Microsoft-Intune)中所述。

本主題描述如何在 Intune 管理主控台中建立 Intune 群組。

您可以在 Microsoft Intune 管理主控台的 [群組] 工作區中建立及管理群組。 [群組概觀] 頁面顯示狀態摘要，可協助您識別並優先處理需要注意的問題。 狀態摘要涵蓋下列區域：

-   警示
-   軟體更新
-   Endpoint Protection
-   原則
-   軟體管理

您的群組階層也會顯示狀態摘要，以協助您識別及解決所選群組之成員的問題。

## <a name="create-groups"></a>建立群組

> [!TIP]
> 當您建立群組時，請考慮如何套用原則。 例如，您可能會有裝置作業系統特定的原則、您組織中不同角色特定的原則，或您已於 Active Directory 中定義之組織單位特定的原則。 具有適用於 iOS、Android 和 Windows 的個別裝置群組，以及適用於每個組織角色的使用者群組可能會很有用。
>
> 您可能也想要建立套用至所有群組和裝置的預設原則，以建立組織的基本相容性需求。 然後，您可以針對最廣泛的使用者和裝置類別建立更具體的原則。 例如，您可以針對每個裝置作業系統建立電子郵件原則。
>
> 請謹慎為原則命名，以便日後能夠輕鬆地找到它們。 例如，**適用於整家公司的 WP 電子郵件原則**就是一個很好的描述性原則名稱。
>
> 當您每次建立嚴格的原則時，會想要將它傳達給您的使用者。 在您建立更通用的群組和原則之後，就能留意如何建立較小的群組，使您能夠減少不必要的通訊。

## <a name="to-create-a-device-group"></a>若要建立裝置群組

1.  在 Intune 管理主控台中，選擇 [群組] &gt; [概觀] &gt; [建立群組]。

2.  輸入群組的名稱和描述 (選擇性)，然後選取一個裝置群組作為父群組。 選擇 **[下一步]**。

3.  在 [定義成員資格準則] 頁面上，選取要包含在群組中的裝置類型。 根據您選擇要包含的裝置類型，您會有其他群組組態選項：

    -   **電腦**： 選取是否要包含父群組的所有成員、要包含或排除的組織單位，以及要包含或排除的網域。 您可以透過清查取得電腦的組織單位和網域資訊。

    -   **行動裝置**： 選取要包含受 Intune 管理的行動裝置、受 Exchange ActiveSync 管理的行動裝置，還是兩者都包含。

    -   **所有裝置**： 這個選項會包含所有裝置，不會依據任何準則排除任何項目。

4.  在 [定義直接成員資格] 頁面上，選擇 [瀏覽] 以選取要包含或排除的個別裝置。 如果您選取的裝置不在指定的父群組中，Intune 會自動將這些裝置新增至父群組。

5.  在 [摘要] 頁面上檢閱您的選取，然後選擇 [完成]。

新建立的群組會顯示在 [群組] 工作區之父群組下的 [群組] 清單中。 這也是您可以編輯或刪除群組的位置。

## <a name="to-create-a-user-group"></a>若要建立使用者群組

1.  在 Intune 管理主控台中，選擇 [群組] &gt; [概觀] &gt; [建立群組]。

2.  輸入群組的名稱和描述 (選擇性)，然後選取一個使用者群組作為父群組。 選擇 **[下一步]**。

3.  在 [定義成員資格準則] 頁面上，選擇要包含父群組的所有成員，還是要從一個空群組開始。 您可以接著依據在 [Office 365 系統管理中心](http://go.microsoft.com/fwlink/?LinkId=698854)手動設定或從 Active Directory 同步處理的使用者安全性群組，包含或排除成員。 如果安全性群組的成員資格變更，以該安全性群組為依據的使用者群組成員資格可能也會變更。

    > [!IMPORTANT]
    > 目前，如果您的群組包含特定安全性群組或經理群組的成員，而且您排除某些群組的成員，則會移除您一開始所包含的成員。 若要建立同時具有包含成員和排除成員的群組，建議您先建立具有包含成員的父群組。 再建立該父群組的子群組。 在新的子群組中，列出排除的成員。 接著，使用該子群組來管理 Intune 原則、設定檔和應用程式發佈。

    > [!NOTE]
    > 在 Azure 入口網站中，您可以建立以使用者回報之經理為基礎的群組。 此類型的群組是動態的，並隨著 Azure Active Directory 中該經理的團隊新增或移除員工而改變。 [使用屬性來建立進階規則](https://azure.microsoft.com/documentation/articles/active-directory-accessmanagement-groups-with-advanced-rules/)的**設定群組為「經理」群組**一節將說明如何建立以經理名稱為基礎的 Azure 群組。

4.  在 [定義直接成員資格] 頁面上，選擇 [瀏覽] 以選取要包含或排除的個別使用者。 如果您選取的使用者不在指定的父群組中，這些裝置會自動新增至父群組。 手動新增使用者的選項位於 [選取成員] 對話方塊的底部。 如果您想要新增還沒有已註冊裝置的使用者，這會很有幫助。

5.  在 [摘要] 頁面上檢閱您的選取，然後選擇 [完成]。

新建立的群組會顯示在 [群組] 工作區之父群組下的 [群組] 清單中。 這也是您可以編輯或刪除群組的位置。

> [!TIP]
> 安全性群組是擴展使用者群組時可使用的良好資源。 由於安全性群組會定義誰可存取哪些資源，因此安全性群組可適當轉譯為 Intune 使用者群組。 從 Active Directory 同步處理至 Azure Active Directory 的安全性群組，或者透過 Office 365 系統管理中心或 Azure 入口網站直接在 Azure Active Directory 中建立的安全性群組，都可供您用來在 Intune 中建立使用者群組。

## <a name="filter-admin-views-by-role"></a>依角色篩選管理檢視
在已篩選的群組檢視中，您可以自訂 IT 系統管理員根據系統管理員角色所能看到的內容。 您也可以限制每位 IT 系統管理員可以管理哪些群組。 在下列情況時，這可能十分有用：

-   您想要讓 IT 系統管理員只能將項目部署到特定使用者和裝置
-   您想要讓 IT 系統管理員只能看到與該系統管理員相關的群組

您可以在 Intune 管理主控台中設定服務管理員的已篩選群組檢視。 如需詳細資訊，請參閱[設定啟動 Microsoft Intune 前的須知事項](/intune-classic/get-started/what-to-know-before-you-start-microsoft-intune)。

在您為服務管理員設定已篩選的群組檢視之後，當系統管理員部署軟體或原則，或是執行報表時，系統管理員可以只檢視和選取您指定的群組。 系統管理員也不會在管理主控台的這些頁面上看到狀態資訊：

-   **系統概觀**
-   **群組概觀**
-   **Endpoint Protection 概觀**
-   **警示概觀**
-   **軟體概觀**
-   **原則概觀**

### <a name="to-create-a-filtered-group-view"></a>建立已篩選的群組檢視

1.  在 Intune 管理主控台中，選擇 [管理] &gt; [系統管理員管理] &gt; [服務管理員]。

2.  選取您想要為其建立已篩選群組檢視的服務管理員，然後選擇 [管理群組]。

3.  在 [選取要對此服務管理員顯示的群組] 對話方塊中，新增服務管理員能夠存取的群組，然後選擇 [確定]。

設定已篩選的群組檢視之後，IT 系統管理員只能檢視和選取您指定的群組。

## <a name="manage-your-groups"></a>管理群組
在您建立群組之後，您可以繼續根據組織需求來管理它們。

您可以編輯群組，來變更其名稱或描述，或是隸屬於該群組的成員。

您可以刪除不再符合組織需求的群組。 刪除群組不會刪除隸屬於該群組的使用者。

## <a name="next-steps"></a>後續步驟
在您設定群組和原則之後，請檢閱 [預定的值] 和 [狀態] 來檢查設計的實際影響。

### <a name="to-check-your-design"></a>檢查您的設計

1. 從裝置群組中選取任何裝置，然後完整瀏覽頁面頂端的資訊類別。
2. 選擇 [原則]。 您會看到與下列螢幕擷取畫面類似的 Android 裝置原則設定。

![Android 設定原則範例](../media/Intune-Device-Policy-v.2.jpg)

每個原則都具有 [預定的值]  和 [狀態] 。 預定的值是您在指派原則時想要達到的值。 狀態則是您在一併考慮要套用到裝置的所有原則，以及硬體和作業系統的限制與需求時，所達成的情況。 在此螢幕擷取畫面中，您可以看到兩個明確的範例：

-   [允許簡單密碼] 已設為 [是 (如 [預定的值] 欄中所示)]，但其 [狀態] 為 [不適用]。 這是因為 Android 裝置不支援簡單的密碼。
-   同樣地，擴充的原則項目 [iOS 裝置的電子郵件設定] 不會套用到此裝置，因為它是 Android 裝置。

> [!NOTE]
> 請記住，當有兩項不同限制等級的原則套用至同一部裝置或使用者時，實際上會套用限制更嚴格的原則。


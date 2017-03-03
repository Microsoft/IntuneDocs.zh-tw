---
title: "條款和條件原則設定 | Microsoft Docs"
description: "您可以將 Intune 條款和條件部署到使用者群組，以說明註冊、對工作資源的存取，以及使用公司入口網站應用程式，如何影響裝置和使用者。"
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 07/11/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6edf0ac1-4f46-4543-a9e5-f484ac37e9a5
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: b6d5ea579b675d85d4404f289db83055642ffddd
ms.openlocfilehash: a6d5f19b1d5f5bac3cd5e6d8bc445d765d703de0
ms.lasthandoff: 12/10/2016


---

# <a name="terms-and-condition-policy-settings-in-microsoft-intune"></a>Microsoft Intune 的條款和條件原則設定

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

您可以將 Intune 條款和條件部署到使用者群組，以說明註冊、對工作資源的存取以及公司入口網站應用程式如何影響裝置和使用者。 使用者必須先接受這些條款和條件，才可使用公司入口網站來註冊及存取其工作。

您可以建立及部署多個包含不同條款和條件的原則。 您也可以產生相同條款和條件的不同語言版本，再將這些版本部署到適當的群組。

## <a name="create-a-terms-and-conditions-policy"></a>建立條款和條件原則

1.  在 [Microsoft Intune 管理主控台](http://manage.microsoft.com)中，按一下 [原則] &gt; [條款和條件]。

    ![條款和條件原則螢幕擷取畫面](./media/pol-sa-terms-conditions.png)

2.  按一下 [新增] 建立新的條款和條件原則。

    您也可以 [編輯] 或 [刪除] 現有的原則。

3.  在 [建立條款和條件] 頁面上，指定下列資訊：

    -   **名稱**&mdash;Intune 主控台中顯示的唯一原則名稱。

    -   **描述**&mdash;協助您在 Intune 主控台中識別原則的詳細資料。

    -   **標題**&mdash;使用者在公司入口網站中看到的標題。

    -   **說明使用者接受之涵義的文字**&mdash;使用者所看到有關接受的標籤。 例如，「我同意這些條款和條件。」

4.  完成後，請按一下 [儲存]。 新原則會隨即顯示在 [原則] 工作區的 [條款和條件] 節點中。

## <a name="deploy-a-terms-and-conditions-policy"></a>部署條款和條件原則

1.  在 [Microsoft Intune 管理主控台](http://manage.microsoft.com)中，按一下 [原則] &gt; [條款和條件]。

2.  在 [條款和條件原則] 清單中，選取您要部署的原則，然後按一下 [管理部署]。

3.  在 [管理部署] 對話方塊中，選取您要部署原則的使用者群組，然後按一下 [確定]。

    當目標使用者存取公司入口網站時，Intune 會顯示您所部署的條款和條件。 使用者必須接受這些條款，才能存取公司資源。

## <a name="monitor-a-terms-and-conditions-policy"></a>監視條款和條件原則

1.  在 [Microsoft Intune 管理主控台](http://manage.microsoft.com)中，按一下 [原則] &gt; [條款和條件]。

2.  在 [建立新報表] 視窗中，按一下 [檢視報表]。 報表會隨即開啟，並詳細列出哪些使用者已接受您所部署的條款和條件。

### <a name="updates-and-version-control-for-terms-and-conditions"></a>更新條款和條件並進行版本控制
當您編輯現有的條款和條件原則時，您可以選擇部署原則時的行為。 請使用下列程序來協助您更新現有的條款和條件原則。

## <a name="work-with-multiple-versions-of-terms-and-conditions"></a>使用多個版本的條款和條件

1.  在 [Microsoft Intune 管理主控台](http://manage.microsoft.com)中，按一下 [原則] &gt; [條款和條件]。

2.  選取您要編輯的條款和條件原則，然後按一下 [編輯]。

3.  在 [編輯條款和條件] 頁面上，進行任何必要的編輯，然後指定這個新版本是否要求所有使用者都接受條款和條件，還是只有新使用者會看到新版本。

    建議您在大幅變更條款和條件原則時，增加版本號碼並要求接受。 如果您想要修正錯字或變更格式，請保留目前的版本號碼。

### <a name="see-also"></a>請參閱
[使用 Microsoft Intune 原則管理裝置的設定及功能](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)


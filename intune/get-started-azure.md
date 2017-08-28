---
title: "開始使用 Azure 入口網站"
titleSuffix: Intune on Azure
description: "了解如何在 Azure 的 Intune 中建立和共用儀表板。"
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 08/16/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 917c0eed-96d0-49d8-8db8-a6ba13ad0e1f
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: f27ae85160573f6757b20c885e95a280eb7f1155
ms.sourcegitcommit: 45204e0fb8cb4cce449e65f2f1d7bb6f6ac4ccf5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/16/2017
---
# <a name="getting-started-with-intune-in-the-azure-portal"></a>開始在 Azure 入口網站中使用 Intune

Azure 入口網站是您可以在其中尋找 Intune 服務的位置。 Azure 中有許多服務，而其中大部分可能不會定期使用。 自訂儀表板和資訊看板可協助您在每次登入以使用 Intune 來管理裝置時快速找到正確的資訊。

## <a name="changing-the-sidebar"></a>變更資訊看板

Azure 入口網站左側的「資訊看板」會顯示所有可用 Azure 服務清單。 您可以從其預設檢視修改此完整清單，以保留您最重要服務的持續性檢視。 我們將使用 Intune 作為要新增至清單頂端的服務範例。

![在 [More services] (更多服務) 清單中搜尋 Intune 的使用者。](./media/azure-add-intune1.png)

1. 從頁面左側的資訊看板底部，選取 [More services] (更多服務)。
2. 在篩選方塊中，搜尋 **Intune**。
3. 選取**星狀**，以將 Intune 新增至我的最愛服務清單底部。
4. 將滑鼠游標放在 Intune 服務上方。 使用服務名稱右側的三個垂直點，以選取並拖曳 Intune。

## <a name="changing-the-dashboard"></a>變更儀表板

您的預設登陸頁面是「儀表板」。 您將在這個位置自訂您的磚，以顯示與您最相關的資訊。

![泛型新儀表板的影像。 它會在左側顯示具有所有服務的資訊看板，然後在中央顯示主要儀表板。 儀表板修改按鈕會沿著上方，並且具有多個磚可以存取所有資源、快速入門教學課程、服務健全狀況和 Azure Marketplace。](./media/azure-default-dashboard.png)

若要修改目前儀表板，請選取 [編輯儀表板] 按鈕。 如果您不想要變更預設儀表板，也可以建立「新儀表板」。 建立新的儀表板，即可透過「磚庫」提供空白的私用儀表板。 這可讓您新增或重新排列磚。 您可以透過 [搜尋] 以及 [資源群組] 或 [標記]，依 [一般] 類別 [類型] 找到磚。

您也可以透過任何**省略**按鈕以及選取 [釘選到儀表板]，直接將磚新增至儀表板。

![[使用者和群組] > Intune 中的 [所有群組] 位置的特寫，其可在群組最右側顯示 [釘選到儀表板] 選項。](./media/azure-pin-to-dashboard.png)

將更多內容 (例如群組和使用者) 新增至 Intune 之後，這會更具相關性。

## <a name="using-services"></a>使用服務

只要在 Azure 中開啟 Intune 或任何其他服務，它就會出現在「刀鋒視窗」中。 您在 Intune 中使用的第一個工作負載有一些 (例如 [使用者]、[群組] 和 [行動應用程式]) 會出現在全螢幕刀鋒視窗中。 當您選取工作負載時，它會以完整頁面開啟該刀鋒視窗。 其他刀鋒視窗會在開啟時從刀鋒視窗右側滑出，並摺疊在其來源主要刀鋒視窗下方。 

## <a name="next-steps"></a>後續步驟

* [開始管理使用者](get-started-users.md) - 將使用者新增至 Intune，以允許他們存取行動裝置上的公司資源。

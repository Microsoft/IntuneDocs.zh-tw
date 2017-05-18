---
title: "監視應用程式部署 | Microsoft Docs"
description: "了解如何監視使用 Intune 部署的應用程式。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 11/10/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5daad56d-71c8-455b-8a55-f8b33e279a8a
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: b6d5ea579b675d85d4404f289db83055642ffddd
ms.openlocfilehash: ee0d10f9b86b1122d0f16568b71b087c341e88df
ms.lasthandoff: 12/10/2016


---


# <a name="monitor-app-deployments-in-microsoft-intune"></a>在 Microsoft Intune 中監視應用程式部署

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

## <a name="monitor-an-app-deployment"></a>監視應用程式部署
您可以在 Intune 管理主控台中看到所管理的應用程式，以及任何部署的狀態。 <!---App status is displayed in real-time. You don't have to wait for the device to check-in before you can see this.--->

### <a name="to-view-apps-that-you-manage-and-their-status"></a>檢視您管理的應用程式及其狀態
在 **[應用程式]** 工作區中，選擇 **[應用程式]** 節點，然後選擇 **[應用程式]**。

您所管理之應用程式的清單隨即出現。 您可以選擇任何應用程式，以在主控台視窗的下方窗格中查看安裝狀態。 選擇這個狀態可查看進一步的詳細資料。 例如，如果狀態顯示 **[1 個使用者備有此軟體]**，您可以選擇該訊息以查看使用者的名稱。

> [!TIP]
> 您可以使用 **[篩選器]** 下拉式清單，只顯示符合您指定之準則的應用程式，例如無法安裝的應用程式，或已成功部署的應用程式。
>
> ![應用程式篩選器範例](./media/app-filters.png)

此外，[儀表板] 工作區會顯示應用程式的狀態概觀。 如果按一下概觀中的任何位置，則會前往應用程式清單。

## <a name="to-view-more-detailed-information-about-an-app"></a>檢視應用程式的更詳細資訊
在應用程式清單中，選取任何應用程式，然後選擇 **[檢視內容]**。

在應用程式的 **[軟體內容]** 頁面上，選擇以下其中一個索引標籤︰**[一般]** - 顯示關於應用程式的一般資訊和其安裝狀態；**[裝置]** - 顯示已成功安裝應用程式的目標部署的裝置；以及 **[使用者]** - 顯示其裝置已成功安裝應用程式之目標部署的使用者。

如前所述，您可以使用 [篩選器] 下拉式清單，來設定每個索引標籤所顯示的值。


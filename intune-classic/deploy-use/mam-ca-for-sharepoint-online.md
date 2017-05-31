---
title: "針對 SharePoint Online 建立以應用程式為基礎的條件式存取原則"
description: 
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 05/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 531b09bb-ddfd-498f-8ee3-6675d2466208
ms.reviewer: chrisgre
ms.suite: ems
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 2d9065281436d4c44e6af7d7a4401786a2a01965
ms.contentlocale: zh-tw
ms.lasthandoff: 05/31/2017


---

# <a name="set-up-app-based-conditional-access-ca-policies-for-sharepoint-online"></a>針對 SharePoint Online 設定以應用程式為基礎的條件式存取 (CA) 原則

[!INCLUDE[note for both-portals](../includes/note-for-both-portals.md)]

本主題提供如何針對 SharePoint Online 設定以應用程式為基礎之條件式存取原則的指導方針。 以應用程式為基礎的 CA 可協助系統管理員僅允許已套用 Intune 應用程式保護原則的行動應用程式。

## <a name="to-create-the-app-based-ca-policy-for-sharepoint-online"></a>針對 SharePoint Online 建立以應用程式為基礎的 CA 原則

1. 移至 [Azure 入口網站](https://portal.azure.com)，並使用您的認證登入。

    > [!NOTE]
    > 如果您不熟悉 Azure 入口網站體驗，請閱讀[用於應用程式保護原則的 Azure 入口網站](azure-portal-for-microsoft-intune-mam-policies.md)主題。

2. 選擇左功能表中的 [更多服務]，然後在文字方塊篩選中輸入 **Intune**。

3. 選擇 [Intune 應用程式保護] > [Intune 行動應用程式管理] > [所有設定]。

4. 在 [Intune 行動應用程式管理] 刀鋒視窗上，選擇 [SharePoint Online] 磚。

5. 在 [允許的應用程式] 刀鋒視窗上，選擇 [允許支援 Intune 應用程式原則的應用程式] 選項，來僅允許 Intune 應用程式保護原則所支援的應用程式。

    > [!NOTE] 
    > 當您選取「僅允許 Intune 應用程式保護原則所支援的應用程式」的選項時，便會顯示「僅」包含支援之應用程式的清單。

    ![允許的應用程式刀鋒視窗顯示應用程式清單的螢幕擷取畫面](../media/mam-ca-spo-allowed-apps.png)

## <a name="to-assign-app-based-ca-policies-to-your-users"></a>將以應用程式為基礎的 CA 原則指派給使用者

1. 開啟 [受限的使用者群組] 刀鋒視窗，然後選擇 [新增使用者群組]。

2. 選取應取得此原則的一或多個使用者群組。

    ![反白顯示 [新增使用者群組] 選項之 [受限的使用者群組] 刀鋒視窗的螢幕擷取畫面](../media/mam-ca-spo-restricted-groups.png)

    > [!IMPORTANT] 
    > 您可能想要讓您在上一個步驟中所選取之使用者群組中的一些使用者不受此原則的影響。 在此情況下，請將使用者群組新增至免套用使用者群組清單。 

3. 在 [SharePoint Online] 刀鋒視窗上，選擇 [免套用使用者群組]，然後選擇 [新增使用者群組] 以開啟使用者群組清單。

4. 選取您要免除此原則的群組。  

## <a name="to-modify-or-delete-user-groups-from-an-existing-app-based-ca-policy"></a>從現有以應用程式為基礎的 CA 原則中修改或刪除使用者群組

1. 開啟 [受限的使用者群組] 刀鋒視窗，然後反白您想要刪除的使用者群組。
2. 按一下省略符號以查看刪除選項。
3. 選擇 [刪除] 從清單中移除使用者群組。

> [!NOTE] 
> 您可以遵循步驟程序，來從 [免套用使用者群組] 清單中移除使用者群組。

## <a name="next-steps"></a>後續步驟

[封鎖未使用新式驗證的應用程式](block-apps-with-no-modern-authentication.md)

## <a name="see-also"></a>請參閱

[使用應用程式保護原則保護應用程式資料](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md)

[針對 Exchange Online 設定以應用程式為基礎的 CA](mam-ca-for-exchange-online.md)


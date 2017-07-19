---
title: "搭配 Intune 使用以應用程式為基礎的條件式存取原則"
description: "本主題說明如何搭配 Intune 設定以應用程式為基礎的條件式存取原則。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 06/28/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d1693515-de18-4553-91ef-801976cd3ec7
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: a7f054868d0bae061f348239614f3a40b96a15b1
ms.sourcegitcommit: fd2e8f6f8761fdd65b49f6e4223c2d4a013dd6d9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2017
---
# <a name="set-up-app-based-conditional-access-policies"></a>設定以應用程式為基礎的條件式存取原則

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

本主題說明如何為屬於已核准應用程式清單一部分的應用程式，設定以應用程式為基礎的條件式存取原則。 已核准應用程式清單包含 Microsoft 已測試的應用程式。

> [!IMPORTANT]
> 本主題會逐步解說步驟，以使用 Exchange Online 新增以應用程式為基礎的條件式存取原則，但是在從已核准應用程式清單中新增其他應用程式，例如 SharePoint Online、Microsoft Teams 等時，您可以使用相同的步驟。

## <a name="to-create-an-app-based-conditional-access-policy"></a>建立以應用程式為基礎的條件式存取原則
1.  移至 [Azure 入口網站](https://portal.azure.com)，並使用您的認證登入。

2.  選擇 [更多服務] 並輸入 "Intune"。

3.  選擇 [Intune 應用程式保護]。

4.  在 [Intune 行動應用程式管理] 刀鋒視窗中，選擇 [所有設定]。

5.  在 [條件式存取] 區段中，選擇 [Exchange Online]。

    ![顯示 [條件式存取] 區段並反白顯示 [Exchange Online] 選項之 [設定] 刀鋒視窗的螢幕擷取畫面](./media/MAM-conditional-access-1.png)

6. 在 [允許的應用程式] 刀鋒視窗上，選擇 [Allow apps that support Intune app policies] \(允許支援 Intune 應用程式原則的應用程式) 選項，只允許 Intune 應用程式保護原則支援的應用程式能夠存取 Exchange Online。 當您選取此選項時，會顯示支援的應用程式清單。

    > [!NOTE]
    > 所有 Exchange Active Sync 郵件用戶端 (包括 iOS 和 Android 上連線到 Exchange Online 的內建郵件用戶端) 將無法傳送或接收電子郵件。 相反地，使用者會收到一封電子郵件，通知他們需要使用 Outlook 郵件應用程式。

7. 若要將此原則套用至使用者，請開啟 [受限的使用者群組] 刀鋒視窗，然後選擇 [新增使用者群組]。 選取應取得此原則的一或多個使用者群組。

    ![反白顯示 [新增使用者群組] 選項之 [受限的使用者群組] 刀鋒視窗的螢幕擷取畫面](./media/mam-ca-add-user-group.png)

8. 您可能想要讓您在上一個步驟中所選取之使用者群組中的一些使用者不受此原則的影響。 在此情況下，請將使用者群組新增至免套用使用者群組清單。 從 [Exchange Online] 刀鋒視窗選擇 [免套用使用者群組]。 選擇 [新增使用者群組] 開啟使用者群組清單。 選取您要免除此原則的群組。

## <a name="to-modify-or-delete-user-groups-from-an-existing-app-based-ca-policy"></a>從現有以應用程式為基礎的 CA 原則中修改或刪除使用者群組

1. 開啟 [受限的使用者群組] 刀鋒視窗，然後反白您想要刪除的使用者群組。
2. 按一下省略符號以查看刪除選項。
3. 選擇 [刪除] 從清單中移除使用者群組。

## <a name="next-steps"></a>後續步驟
[封鎖沒有新式驗證的應用程式](app-modern-authentication-block.md)

### <a name="see-also"></a>請參閱

[使用應用程式保護原則保護應用程式資料](app-protection-policies.md)

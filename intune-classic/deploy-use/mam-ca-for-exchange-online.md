---
title: "Exchange Online 的應用程式存取 | Microsoft Docs"
description: "本主題說明如何設定 MAM 應用程式的條件式存取原則。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 10/15/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f2cd1a1f-fd29-4081-8dfa-c40993a107d5
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: df84bdf2358b596905299c7099ce22e128e9d17d
ms.contentlocale: zh-tw
ms.lasthandoff: 05/23/2017


---

# <a name="create-an-exchange-online-conditional-access-to-only-allow-apps-supported-by-mam"></a>建立 Exchange Online 條件式存取，只允許 MAM 支援的應用程式

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

本主題逐步說明如何設定 Exchange Online 的條件式存取，只允許支援 Intune 應用程式保護原則的 mobile apps。


## <a name="create-an-exchange-online-policy"></a>建立 Exchange Online 原則
1.  登入包含應用程式存取功能的 [Azure 入口網站](https://portal.azure.com)。 如果您不熟悉 Azure 入口網站體驗，請閱讀[應用程式保護原則的 Azure 入口網站](azure-portal-for-microsoft-intune-mam-policies.md)主題。

2.  選擇 [更多服務] 並輸入 "Intune"。

3.  選擇 [Intune 應用程式保護]。

4.  在 [Intune 行動應用程式管理] 刀鋒視窗中，選擇 [所有設定]。

5.  在 [條件式存取] 區段中，選擇 [Exchange Online]。

    ![顯示 [條件式存取] 區段並反白顯示 [Exchange Online] 選項之 [設定] 刀鋒視窗的螢幕擷取畫面](../media/MAM-conditional-access-1.png)

6. 在 [允許的應用程式] 刀鋒視窗上，選擇 [Allow apps that support Intune app policies] \(允許支援 Intune 應用程式原則的應用程式) 選項，只允許 Intune 應用程式保護原則支援的應用程式能夠存取 Exchange Online。 當您選取此選項時，會顯示支援的應用程式清單。

    >[!NOTE]
    >所有 Exchange Active Sync 郵件用戶端 (包括 iOS 和 Android 上連線到 Exchange Online 的內建郵件用戶端) 將無法傳送或接收電子郵件。 相反地，使用者會收到一封電子郵件，通知他們需要使用 Outlook 郵件應用程式。

7. 若要將此原則套用至使用者，請開啟 [受限的使用者群組] 刀鋒視窗，然後選擇 [新增使用者群組]。 選取應取得此原則的一或多個使用者群組。

    ![反白顯示 [新增使用者群組] 選項之 [受限的使用者群組] 刀鋒視窗的螢幕擷取畫面](../media/mam-ca-add-user-group.png)

8. 您可能想要讓您在上一個步驟中所選取之使用者群組中的一些使用者不受此原則的影響。 在此情況下，請將使用者群組新增至免套用使用者群組清單。 從 [Exchange Online] 刀鋒視窗選擇 [免套用使用者群組]。 選擇 [新增使用者群組] 開啟使用者群組清單。 選取您要免除此原則的群組。  

## <a name="modify-an-existing-policy"></a>修改現有的原則
### <a name="add-or-delete-user-groups"></a>新增或刪除使用者群組

若要從 [受限的使用者群組] 清單中**刪除使用者群組**，請開啟 [受限的使用者群組] 刀鋒視窗，反白顯示您要刪除的使用者群組，然後按一下**省略符號 (...)** 檢視 [刪除] 選項。 選擇 [刪除] 從清單中移除使用者群組。 您可以遵循相同的程序，從 [免套用使用者群組] 清單中移除使用者群組。


## <a name="next-steps"></a>後續步驟
[封鎖沒有新式驗證的應用程式](block-apps-with-no-modern-authentication.md)
### <a name="see-also"></a>請參閱
[使用應用程式保護原則保護應用程式資料](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md)


---
title: "設定 SharePoint Online 的應用程式存取"
description: 
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 10/15/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 531b09bb-ddfd-498f-8ee3-6675d2466208
ms.reviewer: chrisgre
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: e5dd7cb5b320df7f443b52a1b502027fa3c4acaf
ms.openlocfilehash: 992273f88e4bbe234f11f936d6416dbaf0d394e9
ms.lasthandoff: 04/19/2017


---

# <a name="create-a-sharepoint-online-conditional-access-policy-to-only-allow-apps-supported-by-mam"></a>建立 SharePoint Online 條件式存取原則，以便只允許 MAM 支援的應用程式
本主題逐步說明如何設定 Exchange Online 的條件式存取，只允許支援 Intune 行動應用程式管理 (MAM) 原則的行動裝置應用程式。

## <a name="configure-a-sharepoint-online-policy"></a>設定 SharePoint Online 原則
**步驟 1：**登入包含應用程式存取功能的 [Azure 入口網站](https://portal.azure.com)。 如果您不熟悉 Azure 入口網站體驗，請閱讀 [MAM 原則的 Azure 入口網站](azure-portal-for-microsoft-intune-mam-policies.md)主題。

**步驟 2：**移至 [瀏覽] > [Intune] > [Intune 行動應用程式管理] 刀鋒視窗 > [設定]，然後在 [條件式存取] 區段中，選擇 [SharePoint Online]。

![顯示條件式存取區段的設定刀鋒視窗，以及開啟的 SharePoint Online 刀鋒視窗的螢幕擷取畫面](../media/mam-ca-settings-spo.png)

**步驟 3：**在 [允許的應用程式] 刀鋒視窗上，選擇 [允許支援 Intune 應用程式原則的應用程式] 選項，以便只允許 Intune MAM 原則支援的應用程式能夠存取 SharePoint Online。 當您選取選項只允許 Intune MAM 原則支援的應用程式時，便會顯示支援的應用程式清單。

![允許的應用程式刀鋒視窗顯示應用程式清單的螢幕擷取畫面](../media/mam-ca-spo-allowed-apps.png)

**步驟 4：**若要將此原則套用至使用者，請開啟 [限制的使用者群組] 刀鋒視窗，然後選擇 [新增使用者群組]。 選取應取得此原則的一或多個使用者群組。

![反白顯示 [新增使用者群組] 選項之 [受限的使用者群組] 刀鋒視窗的螢幕擷取畫面](../media/mam-ca-spo-restricted-groups.png)


**步驟 5：**針對您在上一個步驟中所選取的使用者群組，您可能想要讓其中的一些使用者不受此原則影響。 在此情況下，請將使用者群組新增至免套用使用者群組清單。 從 [SharePoint Online] 刀鋒視窗選擇 [免套用的使用者群組]。 選擇 [新增使用者群組] 開啟使用者群組清單。 選取您要免除此原則的群組。  

## <a name="modifying-an-existing-policy"></a>修改現有的原則
### <a name="adding-or-deleting-user-groups"></a>新增或刪除使用者群組
若要從 [限制的使用者群組] 清單中**刪除使用者群組**，請開啟 [限制的使用者群組] 刀鋒視窗，反白顯示您要刪除的使用者群組，然後按一下 [...] 以檢視刪除選項。 選擇 [刪除] 從清單中移除使用者群組。 您可以遵循相同的程序，從 [免套用使用者群組] 清單中移除使用者群組。


## <a name="next-steps"></a>後續步驟
[設定 Exchange Online 的應用程式存取](mam-ca-for-exchange-online.md)

[封鎖沒有新式驗證的應用程式](block-apps-with-no-modern-authentication.md)

### <a name="see-also"></a>請參閱

[使用 MAM 原則保護應用程式資料](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md)


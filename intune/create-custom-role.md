---
title: 在 Intune 中建立自訂角色
description: 了解如何在 Microsoft Intune 中建立自訂角色。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: pjain
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 10366a41be05dbedee5cd84a1222a727a02a1b93
ms.sourcegitcommit: 74911a263944f2dbd9b754415ccda6c68dae0759
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71071468"
---
# <a name="create-a-custom-role-in-intune"></a>在 Intune 中建立自訂角色

您可以建立自訂 Intune 角色，其中包含特定工作功能所需的任何權限。 例如，如果 IT 部門群組管理應用程式、原則和組態設定檔，您可以將這裡的所有權限一起新增至一個自訂角色。 建立自訂角色之後，您可以將其[指派](assign-role.md)給任何需要這些權限的使用者。

若要建立、編輯或指派角色，您的帳戶必須具備下列其中一項 Azure AD 權限︰
- **全域管理員**
- **Intune 服務管理員**

## <a name="to-create-a-custom-role"></a>建立自訂角色

1. 使用您的 Intune 認證登入 [Azure 入口網站](https://portal.azure.com)。

2. 選擇左功能表中的 [All services] (所有服務)  ，然後在文字方塊篩選中鍵入 **Intune**。

3. 選擇 [Intune]   > [角色]   > [所有角色]   > [新增]  。

4. 在 [新增自訂角色]  刀鋒視窗中輸入新角色的名稱及描述，然後按一下 [權限]  。

5. 在 [權限]  刀鋒視窗中，選擇此角色所要使用的權限。 使用 [Intune RBAC 表格](https://gallery.technet.microsoft.com/Intune-RBAC-table-2e3c9a1a) \(英文\) 可協助您決定套用哪些權限。

6. 在 [範圍 (標籤)]  刀鋒視窗中，選擇此角色的標籤。 這個角色可以存取也擁有這些標籤的資源。

7. 完成後，選擇 [確定]  。

8. 在 [新增自訂角色]  刀鋒視窗中按一下 [建立]  。 新角色會顯示在 [Intune 角色 - 所有角色]  刀鋒視窗上的清單中。

## <a name="next-steps"></a>後續步驟
- [將角色指派給使用者](assign-role.md)
- [深入了解 Intune 中的角色型存取控制](role-based-access-control.md)

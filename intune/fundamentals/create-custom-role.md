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
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: pjain
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3ca83287c58f8d2fb7c8eec5f8cc793e2c67b77a
ms.sourcegitcommit: 2fddb293d37453736ffa54692d03eca642f3ab58
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74390710"
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

5. 在 [權限]  刀鋒視窗中，選擇此角色所要使用的權限。

6. 在 [範圍 (標籤)]  刀鋒視窗中，選擇此角色的標籤。 這個角色可以存取也擁有這些標籤的資源。

7. 完成後，選擇 [確定]  。

8. 在 [新增自訂角色]  刀鋒視窗中按一下 [建立]  。 新角色會顯示在 [Intune 角色 - 所有角色]  刀鋒視窗上的清單中。


## <a name="copy-a-role"></a>複製角色

您也可以複製現有的角色。

1. 使用您的 Intune 認證登入 [Azure 入口網站](https://portal.azure.com)，然後選取 [Intune]  。

2. 選取 [角色]   > [所有角色]  > 選取清單中的角色 > [重複]  。

3. 在 [角色重複]  底下，輸入名稱。 請務必使用唯一的名稱。

4. 系統將會預先選取來自原始角色的所有權限和範圍標籤。 您可以接著變更重複角色的 [名稱]  、[描述]  、[權限]  ，以及 [範圍 (標籤)]  。

5. 選取 [建立]  。 

## <a name="next-steps"></a>後續步驟
- [將角色指派給使用者](assign-role.md)
- [深入了解 Intune 中的角色型存取控制](role-based-access-control.md)

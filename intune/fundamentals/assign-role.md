---
title: 將角色指派給 Intune 使用者
description: 了解如何將內建或自訂角色指派給 Microsoft Intune 中的使用者。
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
ms.openlocfilehash: 780a248f16a8a5028875c9c2401921ea23d0af24
ms.sourcegitcommit: 70b40aa4743c8396f8d6a0163893c4a337d67c48
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2020
ms.locfileid: "76540923"
---
# <a name="assign-a-role-to-an-intune-user"></a>將角色指派給 Intune 使用者

您可以將[內建](role-based-access-control.md#built-in-roles)或[自訂](create-custom-role.md)角色指派給 Intune 使用者。

若要建立、編輯或指派角色，您的帳戶必須具備下列其中一項 Azure AD 權限︰
- **全域管理員**
- **Intune 服務管理員**

1. 在 [Microsoft 端點管理員系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)中，選擇 [租用戶系統管理]   > [角色]   > [所有角色]  。

2. 在 [Intune 角色 - 所有角色]  刀鋒視窗上，選擇您想要指派的內建角色。

3. 在 [<*角色名稱*> - 概觀]  刀鋒視窗上，選擇 [管理]   > [指派]  。

4. 在自訂角色刀鋒視窗中，選擇 [指派]  。

5. 在 [角色指派]  刀鋒視窗上，針對該指派輸入 [指派名稱]  及選擇性的 [指派描述]  。

6. 針對 [成員 (群組)]  ，選擇包含您要授與權限之使用者的群組。

7. 針對 [範圍 (群組)]  ，選擇包含允許上述成員進行管理的使用者/裝置群組。

8. 針對 [範圍 (標籤)]  ，選擇將套用此角色指派的標籤。

9. 完成後，選擇 [確定]  。 新指派會隨即顯示在指派清單中。


## <a name="next-steps"></a>後續步驟
- [深入了解 Intune 中的角色型存取控制](role-based-access-control.md)
- [建立自訂角色](create-custom-role.md)

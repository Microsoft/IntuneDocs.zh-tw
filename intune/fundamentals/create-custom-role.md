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
ms.openlocfilehash: bfa2758546595d1e6237d88e128958c50759eb04
ms.sourcegitcommit: 5881979c45fc973cba382413eaa193d369b8dcf6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/24/2020
ms.locfileid: "77569178"
---
# <a name="create-a-custom-role-in-intune"></a>在 Intune 中建立自訂角色

您可以建立自訂 Intune 角色，其中包含特定工作功能所需的任何權限。 例如，如果 IT 部門群組管理應用程式、原則和組態設定檔，您可以將這裡的所有權限一起新增至一個自訂角色。 建立自訂角色之後，您可以將其[指派](assign-role.md)給任何需要這些權限的使用者。

若要建立、編輯或指派角色，您的帳戶必須具備下列其中一項 Azure AD 權限︰
- **全域管理員**
- **Intune 服務管理員**

## <a name="to-create-a-custom-role"></a>建立自訂角色

1. 在 [Microsoft 端點管理員系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)內，選擇 [租用戶管理]   > [角色]   > [所有角色]   > [建立]  。

2. 在 [基本]  頁面上，輸入新角色的名稱與描述，然後選擇 [下一步]  。

3. 在 [權限]  頁面上，選擇您希望搭配此角色使用的權限。

4. 在 [範圍 (標籤)]  頁面上，選擇此角色的標籤。 這個角色可以存取也擁有這些標籤的資源。 選擇 [下一步]  。

5. 在 [檢閱 + 建立]  頁面上，當您完成操作時，請選擇 [建立]  。 新角色會顯示在 [Intune 角色 - 所有角色]  刀鋒視窗上的清單中。

## <a name="copy-a-role"></a>複製角色

您也可以複製現有的角色。

1. 在 [Microsoft Endpoint Manager 系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)內，選擇 [租用戶管理]   > [角色]   > 所有角色  > 選取清單中角色的核取方塊 > [複製]  。

2. 在 [基本]  頁面上，輸入名稱。 請務必使用唯一的名稱。

3. 系統將會預先選取來自原始角色的所有權限和範圍標籤。 您可以接著變更重複角色的 [名稱]  、[描述]  、[權限]  ，以及 [範圍 (標籤)]  。

4. 在您進行所有希望的變更後，請選擇 [下一步]  來前往 [檢閱 + 建立]  頁面。 選取 [建立]  。 

## <a name="next-steps"></a>後續步驟
- [將角色指派給使用者](assign-role.md)
- [深入了解 Intune 中的角色型存取控制](role-based-access-control.md)



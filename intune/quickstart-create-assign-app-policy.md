---
title: 快速入門 - 建立並指派應用程式防護原則
titleSuffix: Microsoft Intune
description: 在此快速入門中，您將使用 Microsoft Intune 建立並指派應用程式防護原則。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/24/2019
ms.topic: quickstart
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 2586fce0-5dca-4686-b9c4-791778838401
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 626c5d49c4f6bc7fef5f4f29c2397fafead50fda
ms.sourcegitcommit: d2ac912b834c4840de9cc92ba1815b6ecfbfb52b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/25/2019
ms.locfileid: "68482991"
---
# <a name="quickstart-create-and-assign-an-app-protection-policy"></a>快速入門：建立並指派應用程式保護原則

在此快速入門中，您將使用 Intune 建立應用程式防護原則，並將其指派給終端使用者裝置上的用戶端應用程式。 Intune 使用應用程式防護原則，以確認應用程式符合您組織的資料保護需求。

如果您沒有 Intune 訂用帳戶，請[註冊免費試用帳戶](free-trial-sign-up.md)。

## <a name="prerequisites"></a>必要條件

- 若要完成此快速入門，您必須[建立使用者](quickstart-create-user.md)、[建立群組](quickstart-create-group.md)、[註冊裝置](quickstart-setup-auto-enrollment.md)，然後[新增並指派應用程式](quickstart-add-assign-app.md)。

## <a name="sign-in-to-intune"></a>登入 Intune

請以[全域管理員或 Intune 服務管理員](users-add.md#types-of-administrators)身分登入 [Intune](https://aka.ms/intuneportal)。 如果您已建立 Intune 試用版訂閱，則用來建立訂閱的帳戶是全域管理員。

## <a name="create-an-app-protection-policy"></a>建立應用程式保護原則

使用下列步驟來建立應用程式防護原則：

1. 在 [Intune](https://aka.ms/intuneportal) 中，選取 [用戶端應用程式]   > [應用程式防護原則]   > [建立原則]  。 
2. 輸入下列詳細資料： 

    - **名稱**：Windows 10 內容保護 
    - **描述**：與此原則建立關聯的使用者將無法在已指派應用程式與裝置上其他非受控應用程式之間剪下、複製或貼上任何內容。 
    - **平台**：*Windows 10*
    - [註冊狀態]  ：已註冊 

3. 選取 [受保護的應用程式]  以選擇必須遵守此原則的應用程式。
4. 按一下 [新增應用程式]  。
5. 在 [建議的應用程式]  下，選取 [Word Mobile]  。
5. 按一下 [確定]   > [確定]  。 
6. 選取 [Required settings] \(所需的設定\)  以設定應用程式。
7. 按一下 [Allow Overrides] \(允許覆寫\)  以設定 Windows 資訊保護模式。 選取此選項會防止企業資料離開受保護的應用程式。
8. 按一下 [確定]   > [建立]  。

您現在會在 Intune 中看到應用程式防護原則。

### <a name="assign-the-app-protection-policy"></a>指派應用程式防護原則

在 Intune 中建立應用程式防護原則之後，您可以指派給群組。 

使用下列步驟來指派應用程式防護原則：

1. 在 [Intune](https://aka.ms/intuneportal) 中，選取 [Intune]   > [用戶端應用程式]   > [應用程式防護原則]  。 
2. 選取您稍早建立的應用程式防護原則。 在此快速入門中，原則為 **Windows 10 內容保護**。
3. 選取 [指派]  。
4. 在 [包含]  索引標籤中，按一下 [選取要包含的群組]  。
5. 選取 **Contoso Testers** 作為要包含的群組。
6. 按一下 [選取]   > [儲存]  。 

您現在已指派應用程式防護原則。

> [!NOTE]
> 應用程式防護原則只能套用至包含使用者的群組，不能套用至包含裝置的群組。

## <a name="next-steps"></a>後續步驟

在此快速入門中，您已建立並指派應用程式防護原則。 已指派此原則的應用程式使用者將無法在已指派應用程式與裝置上其他非受控應用程式之間剪下、複製或貼上任何內容。 此保護類型將協助保護您組織的資料。 如需 Intune 應用程式防護原則的詳細資訊，請參閱[什麼是應用程式防護原則？](app-protection-policy.md)

若要遵循此 Intune 快速入門系列，請繼續前往下一個快速入門。

> [!div class="nextstepaction"]
> [快速入門：建立並指派自訂角色](quickstart-create-custom-role.md)

---
title: 快速入門 - 建立群組來管理使用者
titleSuffix: Microsoft Intune
description: 在此快速入門中，您將使用 Microsoft Intune 根據現有的使用者建立群組。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/17/2020
ms.topic: quickstart
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 723f4b4e-3090-4811-84ff-6af652abea5a
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: d9b06043dd10f92b6176d4b2e9f90f1b7c87aac9
ms.sourcegitcommit: 70b40aa4743c8396f8d6a0163893c4a337d67c48
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2020
ms.locfileid: "76540942"
---
# <a name="quickstart-create-a-group-to-manage-users"></a>快速入門：建立群組來管理使用者

在此快速入門中，您將使用 Intune 根據現有的使用者建立群組。 群組是用來管理您的使用者，以及控制您的員工對公司資源的存取。 這些資源可以是您公司內部網路的一部分，也可以是外部資源，例如 SharePoint 網站、SaaS 應用程式或 Web 應用程式。

如果您沒有 Intune 訂用帳戶，請[註冊免費試用帳戶](free-trial-sign-up.md)。

>[!NOTE]
>Intune 會在主控台中提供預先建立的 [所有使用者]  和 [所有裝置]  群組，附有內建的最佳化方便您使用。

## <a name="prerequisites"></a>先決條件

- Microsoft Intune 訂用帳戶 - [註冊免費試用帳戶](../fundamentals/free-trial-sign-up.md)。
- 若要完成此快速入門，您必須[建立使用者](quickstart-create-user.md)。

## <a name="sign-in-to-intune-in-the-microsoft-endpoint-manager"></a>在 Microsoft 端點管理員中登入 Intune

以[全域管理員或 Intune 服務管理員身分](users-add.md#types-of-administrators)登入 [Microsoft 端點管理員系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。 如果您已建立 Intune 試用版訂閱，則用來建立訂閱的帳戶是全域管理員。

## <a name="create-a-group"></a>建立群組

您將會建立稍後要用於此快速入門系列的群組。 建立群組：

1. 當您開啟 [Microsoft 端點管理員]  後，請選取 [群組]   > [新增群組]  。
2. 在 [群組類型]  下拉式方塊中，選取 [安全性]  。
3. 在 [群組名稱]  欄位中，輸入新群組的名稱 (例如 **Contoso 測試人員**)。
4. 新增該群組的 [群組描述]  。
5. 將 [成員資格類型]  設定為 [已指派]  。 
6. 在 [成員]  下，從清單中選取連結並針對群組新增一或多個成員。

    ![在 Microsoft Intune 中建立群組的螢幕擷取畫面](./media/quickstart-create-group/quickstart-use-groups-01.png)

7. 按一下 [選取]   > [建立]  。

一旦您已成功建立群組，它會出現在 [所有群組]  清單中。 

## <a name="next-steps"></a>後續步驟

在此快速入門中，您已使用 Intune 根據現有的使用者建立群組。 如需將群組新增至 Intune 的詳細資訊，請參閱[新增群組來組織使用者和裝置](../groups-add.md)。

若要繼續參閱此 Intune 快速入門系列，請前往下一個快速入門。

> [!div class="nextstepaction"]
> [快速入門：設定 Windows 10 裝置的自動註冊](../enrollment/quickstart-setup-auto-enrollment.md)

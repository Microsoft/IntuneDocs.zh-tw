---
title: 快速入門 - 建立群組來管理使用者
titlesuffix: Microsoft Intune
description: 在此快速入門中，您將使用 Microsoft Intune 根據現有的使用者建立群組。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 09/21/2018
ms.topic: quickstart
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 723f4b4e-3090-4811-84ff-6af652abea5a
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 2b52265bb9b3df800c0e13450a2154e46098a933
ms.sourcegitcommit: 9d08545727543b434dd270371fa50233470f2bce
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50410815"
---
# <a name="quickstart-create-a-group-to-manage-users"></a>快速入門：建立群組來管理使用者

在此快速入門中，您將使用 Intune 根據現有的使用者建立群組。 群組是用來管理您的使用者，以及控制您的員工對公司資源的存取。 這些資源可以是您公司內部網路的一部分，也可以是外部資源，例如 SharePoint 網站、SaaS 應用程式或 Web 應用程式。

如果您沒有 Intune 訂用帳戶，請[註冊免費試用帳戶](free-trial-sign-up.md)。

>[!NOTE]
>Intune 會在主控台中提供預先建立的 [所有使用者] 和 [所有裝置] 群組，附有內建的最佳化方便您使用。

## <a name="prerequisites"></a>必要條件

- 若要完成此快速入門，您必須[建立使用者](quickstart-create-user.md)。

## <a name="sign-in-to-intune"></a>登入 Intune

請以[全域管理員或 Intune 服務管理員](users-add.md#types-of-administrators)身分登入 [Intune](https://aka.ms/intuneportal)。 如果您已建立 Intune 試用版訂閱，則用來建立訂閱的帳戶是全域管理員。

## <a name="create-a-group"></a>建立群組

您將會建立稍後要用於此快速入門系列的群組。

1. 開啟 [Microsoft Intune] 窗格之後，選取 [群組] > [新增群組]。
2. 在 [群組類型] 下拉式方塊中，選取 [安全性]。
3. 將 [名稱] 設定為 "Contoso Testers"，並新增群組的**描述**。
4. 將 [成員資格類型] 設定為 [已指派]。 
5. 按一下 [成員]，然後從現有清單中選取群組的一或多個成員。

    ![在 Microsoft Intune 中建立群組的螢幕擷取畫面](./media/quickstart-use-groups-01.png)

6. 按一下 [選取] > [建立]。

一旦您已成功建立群組，它會出現在 [所有群組] 清單中。 

## <a name="next-steps"></a>接下來的步驟

在此快速入門中，您已使用 Intune 根據現有的使用者建立群組。

> [!div class="nextstepaction"]
> [建立裝置相容性原則](quickstart-create-policy.md)

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
ms.openlocfilehash: 3a4468f2e6919349095d934790740afc8c347282
ms.sourcegitcommit: 27eed5aba5c8bfafb079171081b68f75a6cbffaf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2018
ms.locfileid: "46581540"
---
# <a name="quickstart-create-a-group-to-manage-users"></a>快速入門：建立群組來管理使用者

在此快速入門中，您將使用 Intune 根據現有的使用者建立群組。 群組是用來管理您的使用者，以及控制您的員工對公司資源的存取。 這些資源可以是您公司內部網路的一部分，也可以是外部資源，例如 SharePoint 網站、SaaS 應用程式或 Web 應用程式。

如果您沒有 Intune 訂用帳戶，請[註冊免費試用帳戶](free-trial-sign-up.md)。

>[!NOTE]
>Intune 會在主控台中提供預先建立的 [所有使用者] 和 [所有裝置] 群組，附有內建的最佳化方便您使用。

## <a name="prerequisites"></a>必要條件

- 若要完成此快速入門，您必須[建立使用者](quickstart-create-user.md)。

## <a name="sign-in-to-intune"></a>登入 Intune

請以全域管理員或 Intune 服務管理員身分登入 [Intune](https://aka.ms/intuneportal)。 您可以透過選擇 [所有服務] > [Intune]，在 Azure 入口網站中找到 Intune。 Intune 位於 [Monitoring + Management] (監視 + 管理) 區段。

## <a name="create-a-group"></a>建立群組
1. 開啟 [Microsoft Intune] 窗格之後，選取 [群組] > [新增群組]。
2. 在 [群組] 窗格上，選取 [群組類型] > [安全性]。
3. 將 [名稱] 設定為 "Contoso Testers"，並新增群組的**描述**。
4. 將 [成員資格類型] 設定為 [指派]。 
5. 按一下 [成員]，然後從現有清單中選取群組的**成員**。

    ![在 Microsoft Intune 中建立群組的螢幕擷取畫面](./media/quickstart-use-groups-01.png)

6. 按一下 [選取]。
7. 按一下 [建立]。

如果您已成功建立群組，它會出現在 [所有群組] 清單中。 

## <a name="next-steps"></a>接下來的步驟

在此快速入門中，您已使用 Intune 根據現有的使用者建立群組。

> [!div class="nextstepaction"]
> [建立裝置相容性原則](quickstart-create-policy.md)

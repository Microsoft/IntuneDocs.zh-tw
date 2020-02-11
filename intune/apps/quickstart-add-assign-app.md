---
title: 快速入門 - 新增並指派用戶端應用程式
titleSuffix: Microsoft Intune
description: 在此快速入門中，您將使用 Microsoft Intune 新增並指派用戶端應用程式。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/26/2019
ms.topic: quickstart
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: dab6f5c8-1ebb-42c4-a7a7-7af001f94e15
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 40337b3c45885dacf486173814044a27b7f3f6cc
ms.sourcegitcommit: 139853f8d6ea61786da7056cfb9024a6459abd70
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/26/2020
ms.locfileid: "76755063"
---
# <a name="quickstart-add-and-assign-a-client-app"></a>快速入門：新增並指派用戶端應用程式

在此快速入門中，您將使用 Intune 新增用戶端應用程式，並將其指派給您公司的員工。 系統管理員最優先的事項之一，是確保終端使用者能夠存取工作所需的應用程式。 

如果您沒有 Intune 訂用帳戶，請[註冊免費試用帳戶](../fundamentals/free-trial-sign-up.md)。

## <a name="prerequisites"></a>先決條件

- 若要完成此快速入門，您必須[建立使用者](../fundamentals/quickstart-create-user.md)、[建立群組](../fundamentals/quickstart-create-group.md)並[註冊裝置](../quickstart-setup-auto-enrollment.md)。

## <a name="sign-in-to-intune"></a>登入 Intune

請以[全域管理員或 Intune 服務管理員](../fundamentals/users-add.md#types-of-administrators)身分登入 [Intune](https://aka.ms/intuneportal)。 如果您已建立 Intune 試用版訂閱，則用來建立訂閱的帳戶是全域管理員。

## <a name="add-the-client-app-to-intune"></a>將用戶端應用程式新增至 Intune

您可以加入應用程式，讓 Intune 能夠管理應用程式的所有層面。 

使用下列步驟將應用程式新增至 Intune：
1. 在 [Intune](https://aka.ms/intuneportal) 中，選取 [應用程式]   > [所有應用程式]   > [新增]  。 
2. 選取 [選取應用程式類型]  窗格 [Office 365 套件]  區段中的 [Windows 10]  。
3. 按一下 [選取]  。 [新增應用程式]  步驟隨即顯示。
4. 確認 [應用程式套件資訊]  頁面中的預設詳細資料。
5. 按一下 [下一步]  以顯示 [設定應用程式套件]  頁面。
6. 在 [更新通道]  旁邊，從下拉式方塊選取 [每月]  。
7. 確認 [設定應用程式套件]  頁面中剩餘的預設詳細資料。
8. 按一下 [下一步]  以顯示 [範圍標籤]  頁面。
9. 按一下 [選取範圍標籤]  來選擇性地為應用程式新增範圍標籤。 如需詳細資訊，請參閱[針對分散式 IT 使用角色型存取控制 (RBAC) 和範圍標籤](~/fundamentals/scope-tags.md)。
10. 按一下 [下一步]  以顯示 [指派]  頁面。
11. 為應用程式選取群組指派。 如需詳細資訊，請參閱[新增群組來組織使用者與裝置](~/fundamentals/groups-add.md)。 
12. 按一下 [下一步]  以顯示 [檢閱 + 建立]  頁面。 檢閱您針對應用程式所輸入的值和設定。
13. 當您完成時，請按一下 [建立]  以將應用程式新增到 Intune。

## <a name="assign-the-app-to-a-group"></a>將應用程式指派給群組

將應用程式新增至 Microsoft Intune 之後，您可以將該應用程式指派給使用者或裝置群組。

> [!NOTE]
> 此快速入門是以此系列中的前幾個快速入門為基礎所建置的。 如需詳細資料，請參閱此快速入門中的[必要條件](quickstart-add-assign-app.md#prerequisites)。

使用下列步驟將應用程式指派給群組：
1. 在 [Intune](https://aka.ms/intuneportal) 中，選取 [應用程式]   > [所有應用程式]  。 
2. 選取您要指派給群組的應用程式。
3. 按一下 [指派]   > [新增群組]  以顯示 [新增群組]  窗格。
4. 在 [指派類型]  下拉式方塊中，選取 [適用於已註冊的裝置]  。 
5. 按一下 [包含的群組]   > [選取要包含的群組]   > [Contoso Testers]  。
6. 按一下 [選取]   > [確定]   > [確定]   > [儲存]  以指派群組。

您現在已將應用程式指派給 **Contoso Testers** 群組。

## <a name="install-the-app-on-the-enrolled-device"></a>在已註冊的裝置上安裝應用程式

您必須安裝並使用公司入口網站應用程式，來安裝 **Contoso 的待辦事項**應用程式以供 Intune 使用。 使用下列步驟來確認應用程式可供已註冊裝置的使用者使用。

1. 登入您已註冊的 Windows 10 Desktop 裝置。

    > [!IMPORTANT]
    > 該裝置必須已[向 Intune 註冊](../quickstart-enroll-windows-device.md)。 此外，您必須使用指派給應用程式之群組中內含的帳戶來登入裝置。

2. 從 [開始]  功能表開啟 [Microsoft Store]  。 然後，尋找並安裝 [公司入口網站]  應用程式。
3. 啟動 [公司入口網站]  應用程式。
4. 按一下您使用 Intune 新增的應用程式。 在此快速入門中，您已新增 **Microsoft Office 365 應用程式套件**應用程式。

    > [!NOTE]
    > 如果您未成功指派任何應用程式給 Intune 使用者，您將會看到下列訊息：「您的 IT 系統管理員並未提供任何應用程式給您。」 

5. 按一下 [安裝]  。

如果企業需要由您指派公司入口網站應用程式給員工，您也可以直接透過 Intune 手動指派 Windows 10 公司入口網站應用程式。 如需詳細資訊，請參閱[使用 Microsoft Intune 手動新增 Windows 10 公司入口網站應用程式](../company-portal-app.md)。

## <a name="next-steps"></a>後續步驟

在此快速入門中，您已將應用程式新增至 Intune、將應用程式指派給群組，並在已註冊的 Windows 10 Desktop 裝置上安裝應用程式。 如需在 Intune 中管理應用程式的詳細資訊，請參閱[什麼是 Microsoft Intune 應用程式管理？](app-management.md)

若要繼續參閱此 Intune 快速入門系列，請前往下一個快速入門。

> [!div class="nextstepaction"]
> [快速入門：建立並指派應用程式保護原則](quickstart-create-assign-app-policy.md)

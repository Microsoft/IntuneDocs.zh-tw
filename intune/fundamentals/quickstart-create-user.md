---
title: 快速入門 - 在 Intune 中建立使用者
description: 快速入門 - 在 Intune 中建立使用者。
services: microsoft-intune
author: ErikjeMS
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.topic: quickstart
ms.date: 01/17/2020
ms.author: erikje
ms.manager: dougeby
ms.assetid: 820fcb18-0927-4ebd-be79-dce92b51c261
ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
ms.custom: intune
ms.collection: M365-identity-device-management
ms.openlocfilehash: f6aa57b71e052e3fc8566fcdff8bdd9ef5d1c39e
ms.sourcegitcommit: 139853f8d6ea61786da7056cfb9024a6459abd70
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/26/2020
ms.locfileid: "76754485"
---
# <a name="quickstart-create-a-user-in-intune-and-assign-the-user-a-license"></a>快速入門：在 Intune 中建立使用者並為該使用者指派授權

在此快速入門中，您將建立使用者，然後將 Intune 授權指派給該使用者。 當您使用 Intune 時，您要授與公司資料存取權的每個人都必須具備自己的使用者帳戶。 Intune 系統管理員稍後可以設定使用者以管理存取控制。

## <a name="prerequisites"></a>先決條件

- Microsoft Intune 訂用帳戶。 [註冊免費試用帳戶](../fundamentals/free-trial-sign-up.md)。

## <a name="sign-in-to-intune-in-microsoft-endpoint-manager"></a>在 Microsoft 端點管理員中登入 Intune

以[全域管理員或 Intune 服務管理員身分](users-add.md#types-of-administrators)登入 [Microsoft 端點管理員系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。 如果您已建立 Intune 試用版訂用帳戶，則用來建立訂閱的帳戶是全域管理員。

## <a name="create-a-user"></a>建立使用者

使用者必須擁有使用者帳戶才能在 Intune 裝置管理中進行註冊。 建立新的使用者：

1. 在 Microsoft 端點管理員中，選取 [使用者]  > [所有使用者]  > [新使用者]  ：![在 Microsoft 端點管理員中，選取 [新增使用者]](./media/quickstart-create-user/create-user.png)
2. 在 [名稱]  方塊中輸入名稱，例如 *Dewey Kellum*：![新增使用者詳細資料](./media/quickstart-create-user/create-user-02.png)
3. 在 [使用者名稱]  方塊中輸入使用者識別碼，例如 Dewey@contoso.onmicrosoft.com。

    > [!NOTE]
    > 如果您尚未設定客戶網域名稱，請使用用來建立 Intune 訂閱 (或[免費試用版](free-trial-sign-up.md#sign-up-for-a-microsoft-intune-free-trial)) 的已驗證網域名稱。 

4. 選取 [顯示密碼]  並務必記住自動產生的密碼，以便您可以登入測試裝置。
5. 選取 [建立]  。

## <a name="assign-a-license-to-the-user"></a>指派授權給使用者

建立使用者之後，必須使用 [Microsoft 365 系統管理中心](https://go.microsoft.com/fwlink/p/?LinkId=698854)將 Intune 授權指派給該使用者。 如果您未指派授權給使用者，他們將無法在 Intune 中註冊裝置。

將 Intune 授權指派給使用者：

1. 使用與您用來登入 Intune 相同的認證登入 [Microsoft 365 系統管理中心](https://go.microsoft.com/fwlink/p/?LinkId=698854)。
2. 選取 [使用者]   > [作用中使用者]  ，然後選取您剛剛建立的使用者。
3. 選取 [授權與 App]  索引標籤。
4. 在 [選取位置]  下，選取使用者的位置 (如果尚未設定)。
2. 選取 [授權]  區段中的 [Intune]  核取方塊。 如果其他授權包含 Intune，您可以選取該授權。 顯示的[產品名稱](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference) \(部分機器翻譯\) 會作為 Azure 管理中的服務方案使用。

    ![選取 [位置] 與 [Intune 授權]](./media/quickstart-create-user/create-user-03.png)

   > [!NOTE]
   > 此設定會將您的其中一個授權用於該使用者。 如果您使用的是試用環境，稍後會將此授權重新指派給即時環境中真正的使用者。

6. 選取 [儲存變更]  。

新的使用中的 Intune 使用者現在會顯示他們正在使用 **Intune** 授權。

## <a name="clean-up-resources"></a>清除資源

如果您不再需要此使用者，您可以前往 [Microsoft 365 系統管理中心](https://go.microsoft.com/fwlink/p/?LinkId=698854)，然後選取 [使用者]   > 該使用者   > 刪除使用者圖示   > [刪除使用者]   > [關閉]  。

   ![選取刪除圖示](./media/quickstart-create-user/create-user-04.png)

## <a name="next-steps"></a>後續步驟

在此快速入門中，您已建立使用者並指派 Intune 授權給該使用者。 如需如何將使用者新增至 Intune 的詳細資訊，請參閱[新增使用者並授與 Intune 系統管理權限](users-add.md)。

若要繼續此 Intune 快速入門系列，請移至下一個快速入門：

> [!div class="nextstepaction"]
> [快速入門：建立群組來管理使用者](../quickstart-create-group.md)

---
title: 快速入門 - 在 Intune 中建立使用者
description: 快速入門 - 在 Intune 中建立使用者。
services: microsoft-intune
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: quickstart
ms.date: 10/30/2018
ms.author: erikje
ms.openlocfilehash: fb88f703048eaa122bb406d8adb1fc9face764c4
ms.sourcegitcommit: 9d08545727543b434dd270371fa50233470f2bce
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50410747"
---
# <a name="quickstart-create-a-user-and-assign-a-license-to-it"></a>快速入門：建立使用者並為其指派授權

在此快速入門中，您將建立使用者，然後為該使用者指派授權。 使用 Intune 時，您要授與公司資料存取權的每個人都必須具有使用者帳戶。 Intune 系統管理員稍後可以設定這類使用者管理存取控制。

如果您沒有 Intune 訂用帳戶，請[註冊免費試用帳戶](free-trial-sign-up.md)。

## <a name="sign-in-to-intune"></a>登入 Intune

請以[全域管理員或 Intune 服務管理員](users-add.md#types-of-administrators)身分登入 [Intune](https://aka.ms/intuneportal)。 如果您已建立 Intune 試用版訂閱，則用來建立訂閱的帳戶是全域管理員。

## <a name="create-a-user"></a>建立使用者

人員必須擁有使用者帳戶才能在 Intune 裝置管理中進行註冊。

1. 在 Intune 中，選擇 [使用者] > [所有使用者] > [新增使用者]。
![瀏覽器](media/quickstart-create-user/create-user.png)
2. 在 [名稱] 方塊中輸入名稱，例如 *Dewey Kellum*。
3. 在 [使用者名稱] 方塊中輸入使用者識別碼，例如 Dewey@contoso.onmicrosoft.com。

    > [!NOTE]
    > 如果您尚未設定客戶網域名稱，請使用您用來建立 Intune 訂閱 (或[免費試用版](free-trial-sign-up.md#sign-up-for-a-microsoft-intune-free-trial)) 的已驗證網域名稱。 

4. 選擇 [顯示密碼] 並記下自動產生的密碼，以便您可以登入測試裝置。
5. 選擇 **[建立]**。

## <a name="assign-a-license-to-the-user"></a>指派授權給使用者

建立使用者之後，您必須使用 [Office 365 入口網站](http://go.microsoft.com/fwlink/p/?LinkId=698854)將 Intune 授權指派給該使用者。 若未指派授權，他們就無法將其裝置註冊到 Intune 中。 

1. 使用與您用來登入 Intune 相同的認證登入 [Office 365 入口網站](http://go.microsoft.com/fwlink/p/?LinkId=698854)。
2. 選擇 [使用者] > [作用中使用者] > 選擇您剛才建立的使用者。
3. 在 [產品授權] 旁，選取 [編輯]。
4. 在 [位置] 下，選擇使用者的位置。
5. 按一下 Intune 授權 (或您所擁有內含 Intune 的其他授權) 旁的 [開啟]。 顯示的[產品名稱](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference)** 會用作 Azure 管理中的服務方案 

   > [!NOTE]
   > 此設定會將您的其中一個授權用於這位使用者。 如果您使用試用環境，稍後會將此授權重新指派給即時環境中真正的使用者。
6. 選擇 [儲存] > [關閉]。

新的作用中 Intune 使用者現在會顯示他們正在使用 **Intune** 授權。

## <a name="clean-up-resources"></a>清除資源

如果您不再需要此使用者，您可以巡覽至 [Office 365 入口網站](http://go.microsoft.com/fwlink/p/?LinkId=698854)，然後選擇 [使用者] > [作用中使用者] > 選擇清單中的使用者 > [刪除使用者] > [刪除使用者] > [確認變更] > [關閉] 來刪除使用者。

## <a name="next-steps"></a>接下來的步驟

在此快速入門中，您已建立使用者並為該使用者指派授權。 您現在可以將該使用者指派給群組。

> [!div class="nextstepaction"]
> [建立群組](quickstart-create-group.md)

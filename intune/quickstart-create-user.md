---
title: 快速入門 - 在 Intune 中建立使用者
description: 快速入門 - 在 Intune 中建立使用者。
services: microsoft-intune
author: ErikjeMS
ms.service: microsoft-intune
ms.localizationpriority: high
ms.topic: quickstart
ms.date: 03/25/2019
ms.author: erikje
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune
ms.collection: M365-identity-device-management
ms.openlocfilehash: 398b8c748fddfa032194cfa60547d76322e28c9a
ms.sourcegitcommit: 2a7d621587471822b1428440b24f08c8722612dd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70234818"
---
# <a name="quickstart-create-a-user-in-intune-and-assign-them-a-license"></a>快速入門：在 Intune 中建立使用者並為他們指派授權

在本快速入門中，您將建立使用者，然後將 Intune 授權指派給他們。 使用 Intune 時，您要授與公司資料存取權的每個人都必須具備自己的使用者帳戶。 Intune 系統管理員稍後可以設定使用者以管理存取控制。

如果您沒有 Intune 訂用帳戶，請[註冊免費試用帳戶](free-trial-sign-up.md)。

## <a name="sign-in-to-intune"></a>登入 Intune

請以[全域管理員或 Intune 服務管理員](users-add.md#types-of-administrators)身分登入 [Intune](https://aka.ms/intuneportal)。 如果您已建立 Intune 試用版訂閱，則用來建立訂閱的帳戶是全域管理員。

## <a name="create-a-user"></a>建立使用者

使用者必須擁有使用者帳戶才能在 Intune 裝置管理中進行註冊。 建立新的使用者：

1. 在 Intune 中，選擇 [使用者] > [所有使用者] > [新增使用者]。
![瀏覽器](media/quickstart-create-user/create-user.png)
2. 在 [名稱] 方塊中輸入名稱，例如 *Dewey Kellum*。
3. 在 [使用者名稱] 方塊中輸入使用者識別碼，例如 Dewey@contoso.onmicrosoft.com。

    > [!NOTE]
    > 如果您尚未設定客戶網域名稱，請使用用來建立 Intune 訂閱 (或[免費試用版](free-trial-sign-up.md#sign-up-for-a-microsoft-intune-free-trial)) 的已驗證網域名稱。 

4. 選擇 [顯示密碼] 並記下自動產生的密碼，以便您可以登入測試裝置。
5. 選擇 **[建立]**。

## <a name="assign-a-license-to-the-user"></a>指派授權給使用者

建立使用者之後，必須使用 [Microsoft 365 系統管理中心](http://go.microsoft.com/fwlink/p/?LinkId=698854)將 Intune 授權指派給他們。 如果您未指派授權給使用者，他們將無法在 Intune 中註冊裝置。 

將 Intune 授權指派給使用者：

1. 使用與您用來登入 Intune 相同的認證登入 [Microsoft 365 系統管理中心](http://go.microsoft.com/fwlink/p/?LinkId=698854)。
2. 選擇 [使用者] > [作用中使用者] > 選擇您剛才建立的使用者。
3. 在 [產品授權] 旁，選取 [編輯]。
4. 在 [位置] 下，選擇使用者的位置。
5. 按一下 Intune 授權 (或您所擁有包含 Intune 的其他授權) 旁的 [開啟]。 顯示的[產品名稱](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference)** 會用作 Azure 管理中的服務方案 

   > [!NOTE]
   > 此設定會將您的其中一個授權用於這位使用者。 如果您使用試用環境，稍後會將此授權重新指派給即時環境中真正的使用者。
6. 選擇 [儲存] > [關閉]。

新的作用中 Intune 使用者現在會顯示他們正在使用 **Intune** 授權。

## <a name="clean-up-resources"></a>清除資源

如果您不再需要此使用者，您可以巡覽至 [Microsoft 365 系統管理中心](http://go.microsoft.com/fwlink/p/?LinkId=698854)，然後選擇 [使用者] > [作用中使用者] > 「選擇清單中的使用者」 > [刪除使用者] > [刪除使用者] > [確認變更] > [關閉] 來刪除使用者。

## <a name="next-steps"></a>後續步驟

您已在此快速入門中建立使用者並指 Intune 授權給他們。 如需如何將使用者新增至 Intune 的詳細資訊，請參閱[新增使用者並授與 Intune 系統管理權限](users-add.md)。

若要遵循此 Intune 快速入門系列，請繼續前往下一個快速入門。

> [!div class="nextstepaction"]
> [快速入門：建立群組來管理使用者](quickstart-create-group.md)

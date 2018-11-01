---
title: 快速入門 - 在 Intune 中建立使用者
description: 快速入門 - 在 Intune 中建立使用者。
services: microsoft-intune
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: quickstart
ms.date: 09/21/2018
ms.author: erikje
ms.openlocfilehash: 6a1d591e635dccd99551d9b8d40e099724a85d77
ms.sourcegitcommit: 27eed5aba5c8bfafb079171081b68f75a6cbffaf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2018
ms.locfileid: "46581544"
---
# <a name="quickstart-create-a-user-and-assign-a-license-to-it"></a>快速入門：建立使用者並為其指派授權

在此快速入門中，您將建立使用者，然後為其指派授權。 使用 Intune 時，您要授與公司資料存取權的每個人都必須具有使用者帳戶。 Intune 系統管理員接著可以設定這類使用者管理存取控制。

如果您沒有 Intune 訂用帳戶，請[註冊免費試用帳戶](free-trial-sign-up.md)。

## <a name="sign-in-to-intune"></a>登入 Intune

請以全域管理員或 Intune 服務管理員身分登入 [Intune](https://aka.ms/intuneportal)。

## <a name="create-a-user"></a>建立使用者

人員必須擁有使用者帳戶才能在 Intune 裝置管理中進行註冊。

1. 在 Intune 中，選擇 [使用者] > [所有使用者] > [新增使用者]。
![瀏覽器](media/quickstart-create-user/create-user.png)
2. 在 [名稱] 方塊中，輸入 *Dewey Kellum*。
3. 在 [使用者名稱] 方塊中，輸入 *Dewey@contoso.onmicrosoft.com*。
4. 選擇 [群組] > Everyone > **[選取]**。
5. 選擇 [顯示密碼] 並記下自動產生的密碼，以便您可以登入測試裝置。
6. 選擇 **[建立]**。

## <a name="assign-a-license-to-the-user"></a>指派授權給使用者

建立使用者之後，您必須使用 [Office 365 入口網站](http://go.microsoft.com/fwlink/p/?LinkId=698854)將 Intune 授權指派給該使用者。 若未指派授權，他們就無法將其裝置註冊到 Intune 中。 

1. 使用與您用來登入 Intune 相同的認證登入 [Office 365 入口網站](http://go.microsoft.com/fwlink/p/?LinkId=698854)。
2. 選擇 [使用者] > [作用中使用者] > 選擇您剛才建立的使用者。
3. 在 [位置] 下，選擇使用者的位置。
3. 選擇 [產品授權]，然後將 [Enterprise Mobility + Security E3] (或您所擁有內含 Intune 的其他授權) 設定為 [開啟]。
   > [!NOTE]
   > 這樣會將您的其中一個授權用於這名使用者。 如果您使用實際環境，可以稍後關閉使用此授權，將它重新指派給真正的使用者。
5. 選擇 [儲存]。

## <a name="clean-up-resources"></a>清除資源

如果您不再需要此使用者，您可以選擇 [使用者] > [所有使用者] > 選擇清單中的使用者 > [刪除使用者] > [是] 進行刪除。

## <a name="next-steps"></a>接下來的步驟

在此快速入門中，您已建立使用者並為其指派授權。 您現在可以將該使用者指派給群組。

> [!div class="nextstepaction"]
> [建立群組](quickstart-create-group.md)

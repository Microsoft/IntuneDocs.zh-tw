---
title: 快速入門 - 在 Intune 中建立並指派自訂角色
description: 快速入門 - 為遠端裝置管理員建立並指派自訂角色。
services: microsoft-intune
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: quickstart
ms.date: 09/21/2018
ms.author: erikje
ms.openlocfilehash: 5c83af252b1c728b9e3d4015cdc8bb4fd3668ad1
ms.sourcegitcommit: 2e6851a5c1f934dcdb3f854d8462a4d23cc0453b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2018
ms.locfileid: "51561919"
---
# <a name="quickstart-create-and-assign-a-custom-role"></a>快速入門：建立並指派自訂角色

在此 Intune 快速入門中，您將建立具備安全性作業部門特定權限的自訂角色。 然後，您會將角色指派給這類操作員群組。 有幾個預設角色可讓您直接使用。 藉由建立類似的自訂角色，您就可以對行動裝置管理系統的所有組件進行精確的存取控制。

如果您沒有 Intune 訂用帳戶，請[註冊免費試用帳戶](free-trial-sign-up.md)。

## <a name="prerequisites"></a>必要條件

- 若要完成此快速入門，您必須[建立群組](quickstart-create-group.md)。

## <a name="sign-in-to-intune"></a>登入 Intune

請以全域管理員或 Intune 服務管理員身分登入 [Intune](https://aka.ms/intuneportal)。

## <a name="create-a-custom-role"></a>建立自訂角色

當您建立自訂角色時，可以為各種不同的動作設定權限。 針對安全性作業角色，我們將設定一些「讀取」權限，讓操作員可以檢閱裝置的設定和原則。

1. 在 Intune 中，選擇 [角色] > [所有角色] > [新增]。
![瀏覽器](media/quickstart-create-custom-role/add-custom-role.png)
2. 在 [新增自訂角色] 下的 [名稱] 方塊中，輸入「安全性作業」。
3. 在 [描述] 方塊中，輸入「此角色可讓安全性操作員監視裝置設定與合規性資訊」。
4. 選擇 [設定] > [公司裝置識別碼] > [讀取] 旁的 [是] > [確定]。
![瀏覽器](media/quickstart-create-custom-role/corp-device-id-read.png)
5. 選擇 [裝置合規性原則] > [讀取] 旁的 [是] > [確定]。
6. 選擇 [裝置設定] > [讀取] 旁的 [是] > [確定]。
7. 選擇 [組織] > [讀取] 旁的 [是] > [確定]。
8. 選擇 [確定] > [建立]。

## <a name="assign-the-role-to-a-group"></a>將角色指派給群組

您必須將角色指派給包含安全性使用者的群組，安全性操作員才能使用新的權限。

1. 在 Intune 中，選擇 [角色] > [所有角色] > [Security operations] \(安全性作業\)。
2. 在 [Intune 角色] 下，選擇 [作業] > [指派]。
3. 在 [作業名稱] 方塊中，輸入「安全性作業」。
4. 選擇 [成員 (群組)] > [新增]。
5. 選擇 **Contoso Testers** 群組。
6. 選擇 [選取] > [確定]。
7. 選擇 [範圍 (群組)] > [選取要納入的群組] > [Contoso Testers]。
8. 選擇 [選取] > [確定] > [確定]。

現在，群組中的所有人都是「安全性作業」角色的成員，而且可以檢閱下列有關裝置的資訊：公司裝置識別碼、裝置合規性原則、裝置設定和組織資訊。

## <a name="clean-up-resources"></a>清除資源

如果您不想再使用新的自訂角色，您可以將它刪除。 選擇 [角色] > [所有角色] > 選擇角色旁的省略符號 > [刪除]。

## <a name="next-steps"></a>接下來的步驟

在此快速入門中，您已建立自訂安全性作業角色，並將它指派給群組。 如需 Intune 中角色的詳細資訊，請參閱[以角色為基礎的系統管理 (RBAC) 搭配 Microsoft Intune](role-based-access-control.md)

若要遵循此 Intune 快速入門系列，請繼續前往下一個快速入門。

> [!div class="nextstepaction"]
> [快速入門：建立 iOS 的電子郵件裝置設定檔](quickstart-email-profile.md)

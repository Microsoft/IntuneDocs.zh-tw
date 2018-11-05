---
title: 快速入門：為 Windows 10 裝置新增裝置合規性原則
description: 您可以使用此快速入門來建立原則，以協助保護公司資料及管理終端使用者用來存取公司資源的裝置。 然後，將原則指派給群組。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/17/2018
ms.topic: quickstart
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 1ac74ba5-7441-44ac-98b5-9d8bb8899747
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 9d9169ab353da30e0f7b292cea4f5b9c93e316aa
ms.sourcegitcommit: 2e88ec7a412a2db35034d30a70d20a5014ddddee
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2018
ms.locfileid: "49391547"
---
# <a name="quickstart-add-a-device-compliance-policy-for-a-windows-10-device"></a>快速入門：為 Windows 10 裝置新增裝置合規性原則
適用於 Windows 的 Intune 裝置合規性政策，會指定 Windows 裝置為被視為符合規範必須滿足的規則與設定。 您可以將這些原則與[條件式存取](https://docs.microsoft.com/intune/conditional-access)搭配使用，來允許或封鎖存取公司資源。 您也可以取得裝置報表，並針對不相容採取動作。

在此快速入門中，您會為 Windows 10 裝置建立裝置合規性原則，然後將裝置群組指派給原則。

如果您沒有 Intune 訂用帳戶，請[註冊免費試用帳戶](free-trial-sign-up.md)。

## <a name="prerequisites"></a>必要條件
- 若要完成此快速入門，您必須先[建立使用者](quickstart-create-user.md)並[建立群組](quickstart-create-group.md)。


## <a name="sign-in-to-intune"></a>登入 Intune
請以全域管理員或 Intune 服務管理員身分登入 [Intune](https://aka.ms/intuneportal)。

## <a name="create-a-device-compliance-policy"></a>建立裝置合規性政策
1. 選取 [裝置相容性] > [原則] > [建立原則]。
2. 在 [名稱] 中輸入 **Windows 10 合規性**，並在 [描述] 中輸入 **Windows 10 的範例合規性原則**。
3. 針對 [平台]，選取 [Windows 10 及更新版本]。
4. 在 [設定] 中，選取 [系統安全性]，然後將 [需要密碼才可解除鎖定行動裝置] 設定為 [需要]。 設定完成您的原則之後，選取 [確定]。
   ![合規性原則](/intune/media/quickstart-create-policy/compliance-policy.png)
5. 關閉 [Windows 10 合規性原則] 窗格。 
6. 在 [建立原則] 窗格上，選取 [建立]。 此步驟會建立原則，並在 [裝置合規性] > [原則] 中列出您的原則。
7. 選取您的新原則，然後選擇 [指派]。 您可以包含或排除 Azure Active Directory (AD) 安全性群組。
8. 選擇 [選取的群組] 以查看您現有的 Azure AD 安全性群組。 選取 [Contoso Testers]，然後選擇 [儲存] 將原則部署給群組中的使用者。 如果您未在[建立群組](quickstart-create-group.md)中建立此群組，您可以使用自選的群組。 

## <a name="clean-up-resources"></a>清除資源
不再需要時，請刪除原則。 若要這樣做，請選取 [Windows 10 合規性] 原則，然後按一下 [刪除]。 

## <a name="next-steps"></a>接下來的步驟
在此快速入門中，您已建立並指派簡單的裝置合規性原則。 若要註冊將會接收原則的 Windows 10 裝置，請繼續進行快速入門來設定自動註冊。 
 
> [!div class="nextstepaction"]
> [設定裝置密碼長度](quickstart-set-password-length-android.md)
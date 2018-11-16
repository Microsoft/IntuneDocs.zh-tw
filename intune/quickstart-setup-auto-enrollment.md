---
title: 快速入門 - 在 Intune 中設定自動註冊
description: 快速入門 - 在 Intune 中設定 Windows 10 裝置的自動註冊。
services: microsoft-intune
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: quickstart
ms.date: 11/05/2018
ms.author: erikje
ms.openlocfilehash: c219629968fbd66ee14abf61786a791bf7f5e2e0
ms.sourcegitcommit: 4c4e87cb0d8906085fcb7cdd170bd6b0cfeb23ff
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2018
ms.locfileid: "51510783"
---
# <a name="quickstart-set-up-automatic-enrollment-for-windows-10-devices"></a>快速入門：設定 Windows 10 裝置的自動註冊

在此快速入門中，您將設定 Microsoft Intune 在特定使用者登入 Windows 10 裝置時自動註冊裝置。

如果您沒有 Intune 訂用帳戶，請[註冊免費試用帳戶](free-trial-sign-up.md)。

## <a name="prerequisites"></a>必要條件

- Microsoft Intune 訂用帳戶 - [註冊免費試用帳戶](free-trial-sign-up.md)。
- 若要完成此快速入門，您必須先[建立使用者](quickstart-create-user.md)並[建立群組](quickstart-create-group.md)。

## <a name="sign-in-to-intune"></a>登入 Intune

請以全域管理員或 Intune 服務管理員身分登入 [Intune](https://aka.ms/intuneportal)。

## <a name="set-up-windows-10-automatic-enrollment"></a>設定 Windows 10 自動註冊

在此範例中，您將使用 MDM 註冊，讓公司裝置與自備裝置都能自動註冊。 您將註冊免費的 Azure Active Directory Premium 訂用帳戶。

1. 在 Azure 中，選擇 [Azure Active Directory] > [行動性 (MDM 與 MAM)]。
2. 選取 [取得免費 Premium 試用版即可使用此功能]。 選取此選項可讓您使用免費的 Azure Active Directory Premium 試用版來自動註冊。 

    ![選取免費的 Azure Active Directory Premium 試用版](media/quickstart-setup-auto-enrollment/quickstart-setup-auto-enrollment-01.png)

    選擇 [Enterprise Mobility + Security E5] 免費試用選項。 此外，您必須選擇 [啟動] 免費試用版。

    ![選擇 [Enterprise Mobility + Security E5] 免費試用版](media/quickstart-setup-auto-enrollment/quickstart-setup-auto-enrollment-02.png)

3. 選取 [Microsoft Intune]。 

    ![從清單中選擇 Microsoft Intune](media/quickstart-setup-auto-enrollment/quickstart-setup-auto-enrollment-03.png)

4. 從 [MDM 使用者範圍] 選取 [部分]，使用 MAM 自動註冊來管理您員工 Windows 裝置上的企業資料。 將會針對已加入 AAD 的裝置和自備裝置案例設定 MDM 自動註冊。

    ![從 [設定] 清單選取 [部分]](media/quickstart-setup-auto-enrollment/quickstart-setup-auto-enrollment-04.png)

5. 選擇 [選取群組] > [Contoso Testers] > [選取] 作為指派的群組。

    ![選取要註冊的群組](media/quickstart-setup-auto-enrollment/quickstart-setup-auto-enrollment-05.png)

6. 從 [MAM 使用者範圍] 選取 [部分] 來管理您員工裝置上的資料。
7. 選擇 [選取群組] > [Contoso Testers] > [選取] 作為指派的群組。 
8. 其餘的設定值請使用預設值。
9. 選擇 [儲存]。

## <a name="clean-up-resources"></a>清除資源

若要重新設定 Intune 自動註冊，請參閱[設定 Windows 裝置的註冊](windows-enroll.md)。

## <a name="next-steps"></a>接下來的步驟

在此快速入門中，您已了解如何設定 Windows 10 裝置的自動註冊。 如需裝置註冊的詳細資訊，請參閱[什麼是裝置註冊？](device-enrollment.md)

若要遵循此 Intune 快速入門系列，請繼續前往下一個快速入門。

> [!div class="nextstepaction"]
> [快速入門：註冊您的 Windows 10 裝置](quickstart-enroll-windows-device.md)
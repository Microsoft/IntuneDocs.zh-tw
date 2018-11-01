---
title: 快速入門 - 在 Intune 中設定自動註冊
description: 快速入門 - 在 Intune 中設定 Windows 10 裝置的自動註冊。
services: microsoft-intune
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: quickstart
ms.date: 09/21/2018
ms.author: erikje
ms.openlocfilehash: 3b713f090fb6ada884a269e286f55f6e1b1087c4
ms.sourcegitcommit: 27eed5aba5c8bfafb079171081b68f75a6cbffaf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2018
ms.locfileid: "46581537"
---
# <a name="quickstart-set-up-automatic-enrollment-for-windows-10-devices"></a>快速入門：設定 Windows 10 裝置的自動註冊

在此快速入門中，您將設定 Microsoft Intune 在特定使用者登入 Windows 10 裝置時自動註冊裝置。

如果您沒有 Intune 訂用帳戶，請[註冊免費試用帳戶](free-trial-sign-up.md)。

## <a name="prerequisites"></a>必要條件

- 若要完成此快速入門，您必須先[建立使用者](quickstart-create-user.md)並[建立群組](quickstart-create-group.md)。

## <a name="sign-in-to-intune"></a>登入 Intune

請以全域管理員或 Intune 服務管理員身分登入 [Intune](https://aka.ms/intuneportal)。

## <a name="set-up-windows-10-automatic-enrollment"></a>設定 Windows 10 自動註冊

在此範例中，您將使用 MDM 註冊，讓公司裝置與您自己攜帶的裝置都能自動註冊。

1. 在 Azure 中，選擇 [Azure Active Directory] > [行動性 (MDM 與 MAM)] > [Microsoft Intune] > [部分]。
![瀏覽器](media/quickstart-setup-auto-enrollment/setup-automatic-enrollment-win10.png)
2. 選擇 [選取群組] > [Contoso Testers] > [選取]。
3. 使用下列 URL 的預設值：
    - MDM 使用條款 URL
    - MDM 探索 URL
    - MDM 合規性 URL
4. 選擇 [儲存]。
5. 以群組中的使用者身分登入 Windows 10 裝置，並依照提示進行。

## <a name="clean-up-resources"></a>清除資源

若要重新設定 Intune 自動註冊，請參閱[設定 Windows 裝置的註冊](windows-enroll.md)。

## <a name="next-steps"></a>接下來的步驟

在此快速入門中，您已了解如何設定 Windows 10 裝置的自動註冊。 您可以了解跨所有平台註冊裝置的其他方式。

> [!div class="nextstepaction"]
> [什麼是裝置註冊？](device-enrollment.md)一文
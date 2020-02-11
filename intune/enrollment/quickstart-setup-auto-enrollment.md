---
title: 快速入門 - 在 Intune 中設定自動註冊
description: 快速入門 - 在 Intune 中設定 Windows 10 裝置的自動註冊。
services: microsoft-intune
author: ErikjeMS
manager: dougeby
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.topic: quickstart
ms.date: 01/17/2020
ms.author: erikje
ms.reviewer: spshumwa
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: e5cc7cf3661caa2b2640d9370d26402b7702d36b
ms.sourcegitcommit: 70b40aa4743c8396f8d6a0163893c4a337d67c48
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2020
ms.locfileid: "76541003"
---
# <a name="quickstart-set-up-automatic-enrollment-for-windows-10-devices"></a>快速入門：設定 Windows 10 裝置的自動註冊

在此快速入門中，您將設定 Microsoft Intune 在特定使用者登入 Windows 10 裝置時自動註冊裝置。

如果您沒有 Intune 訂用帳戶，請[註冊免費試用帳戶](../fundamentals/free-trial-sign-up.md)。

## <a name="prerequisites"></a>先決條件

- Microsoft Intune 訂用帳戶 - [註冊免費試用帳戶](../fundamentals/free-trial-sign-up.md)。
- 若要完成此快速入門，您必須先[建立使用者](../fundamentals/quickstart-create-user.md)並[建立群組](../fundamentals/quickstart-create-group.md)。

## <a name="sign-in-to-intune-in-the-microsoft-endpoint-manager"></a>在 Microsoft 端點管理員中登入 Intune

請以全域管理員或 Intune 服務管理員身分登入 [Microsoft Endpoint Manager 系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。 如果您已建立 Intune 試用版訂閱，則用來建立訂閱的帳戶是全域管理員。

## <a name="set-up-windows-10-automatic-enrollment"></a>設定 Windows 10 自動註冊

在此範例中，您將使用 MDM 註冊，讓公司裝置與自備裝置都能自動註冊。 您將註冊免費的 Azure Active Directory Premium 訂用帳戶。

1. 在 [Microsoft 端點管理員系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)中，選擇 [所有服務]   > [M365 Azure Active Directory]   > [Azure Active Directory]   > [行動性 (MDM 和 MAM)]  。
2. 選取 [取得免費 Premium 試用版即可使用此功能]  。 選取此選項可讓您使用免費的 Azure Active Directory Premium 試用版來自動註冊。 

    ![選取免費的 Azure Active Directory Premium 試用版](./media/quickstart-setup-auto-enrollment/quickstart-setup-auto-enrollment-01.png)

3. 選擇 [Enterprise Mobility + Security E5]  免費試用選項。 
4. 按一下 [免費試用]   > [啟用]  免費試用版。

    ![選擇 [Enterprise Mobility + Security E5] 免費試用版](./media/quickstart-setup-auto-enrollment/quickstart-setup-auto-enrollment-02.png)

    > [!NOTE]
    > 啟用可能需要幾分鐘的時間。 

3. 選取 [Microsoft Intune]  以設定 Intune。 

    ![從清單中選擇 Microsoft Intune](./media/quickstart-setup-auto-enrollment/quickstart-setup-auto-enrollment-03.png)

4. 從 [MDM 使用者範圍]  選取 [部分]  ，使用 MAM 自動註冊來管理您員工 Windows 裝置上的企業資料。 將會針對已加入 AAD 的裝置和自備裝置案例設定 MDM 自動註冊。

    ![從 [設定] 清單選取 [部分]](./media/quickstart-setup-auto-enrollment/quickstart-setup-auto-enrollment-04.png)

5. 按一下 [選取群組]   > [Contoso Testers]   > [選取]  作為指派的群組。

    ![選取要註冊的群組](./media/quickstart-setup-auto-enrollment/quickstart-setup-auto-enrollment-05.png)

6. 從 [MAM 使用者範圍]  選取 [部分]  來管理您員工裝置上的資料。

    ![選取要註冊的群組](./media/quickstart-setup-auto-enrollment/quickstart-setup-auto-enrollment-06.png)

7. 選擇 [選取群組]   > [Contoso Testers]   > [選取]  作為指派的群組。 
8. 其餘的設定值請使用預設值。
9. 選擇 [儲存]  。

## <a name="clean-up-resources"></a>清除資源

若要重新設定 Intune 自動註冊，請參閱[設定 Windows 裝置的註冊](windows-enroll.md)。

## <a name="next-steps"></a>後續步驟

在此快速入門中，您已了解如何設定 Windows 10 裝置的自動註冊。 如需裝置註冊的詳細資訊，請參閱[什麼是裝置註冊？](device-enrollment.md)

若要繼續參閱此 Intune 快速入門系列，請前往下一個快速入門。

> [!div class="nextstepaction"]
> [快速入門：註冊您的 Windows 10 裝置](../quickstart-enroll-windows-device.md)

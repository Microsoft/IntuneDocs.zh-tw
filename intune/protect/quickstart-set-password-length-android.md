---
title: 快速入門 - Android 裝置的密碼合規性政策
titleSuffix: Microsoft Intune
description: 您將在本快速入門中，使用 Microsoft Intune 設定 Android 裝置所需的密碼長度。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/21/2019
ms.topic: quickstart
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 81b4fa08-5333-4c54-9f49-8db5f6984ed2
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 61fdf91d57ce5d187a0c43153f317b0b42c6b46c
ms.sourcegitcommit: a7b479c84b3af5b85528db676594bdb3a1ff6ec6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74409759"
---
# <a name="quickstart-create-a-password-compliance-policy-for-android-devices"></a>快速入門：建立 Android 裝置的密碼合規性政策

您將在本快速入門中，使用 Microsoft Intune 要求您使用 Android 裝置的員工必須先輸入特定長度的密碼，才會在其 Android 裝置上授與資訊存取權。

Intune 裝置合規性政策指定裝置必須符合的規則和設定，才能視為相容。 您可以將合規性政策與條件式存取搭配使用，以允許或封鎖對公司資源的存取。 您也可以取得裝置報表，並針對不相容採取動作。

> [!IMPORTANT]
> 除了密碼設定之外，也應該考量運用其他系統安全性設定保護您的員工。 如需詳細資訊，請參閱[系統安全性設定](compliance-policy-create-android-for-work.md)。

如果您沒有 Intune 訂用帳戶，請[註冊免費試用帳戶](../fundamentals/free-trial-sign-up.md)。

## <a name="sign-in-to-intune"></a>登入 Intune

以[全域管理員](../fundamentals/users-add.md#types-of-administrators)或 Intune [服務管理員](../fundamentals/users-add.md#types-of-administrators)身分登入 [Microsoft 端點管理員系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。

## <a name="create-a-device-compliance-policy"></a>建立裝置合規性政策

建立裝置合規性原則來要求您員工中的 Android 使用者輸入特定長度的密碼，才能在其 Android 裝置上授與資訊存取權。

1. 在 Intune 中，選取 [裝置]   > [合規性原則]   > [建立原則]  。

2. 新增 [Android 合規性]  作為 [名稱]  。 也請新增 [描述]  。

3. 針對 [平台]  ，選取 [Android Enterprise]  。

4. 針對 [設定檔類型]  ，選取 [工作設定檔]  。

5. 選取 [設定]   > [系統安全性]  以顯示 Android [系統安全性]  刀鋒視窗。

6. 針對 [需要密碼才可解除鎖定行動裝置]  選取 [必要]  。

7. 針對 [必要的密碼類型]  ，選取 [至少要有數字]  。

8. 針對 [密碼長度下限]  ，請輸入 **6**。

    ![在 Microsoft Intune 中建立群組的螢幕擷取畫面](./media/quickstart-set-password-length-android/quickstart-set-password-length-android-01.png)

9. 完成後，請選取 [確定]   > [確定]   > [建立]  來建立原則。

成功建立原則之後，它便會顯示在您的裝置合規性原則清單中。

## <a name="clean-up-resources"></a>清除資源

不再需要時，請刪除原則。 若要這樣做，請選取合規性政策，然後按一下 [刪除]  。

## <a name="next-steps"></a>後續步驟

您可以在本快速入門中，使用 Intune 為員工的 Android 裝置建立合規性政策，以要求長度至少為六個字元的密碼。 如需建立合規性政策的詳細資訊，請參閱[開始使用 Intune 中的裝置合規性政策](device-compliance-get-started.md)。

若要繼續參閱此 Intune 快速入門系列，請前往下一個快速入門。

> [!div class="nextstepaction"]
> [快速入門：傳送通知到不符合規範的裝置](../quickstart-send-notification.md)

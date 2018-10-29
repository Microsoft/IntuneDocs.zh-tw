---
title: 快速入門 - 為 Android 裝置設定必要的密碼長度
titlesuffix: Microsoft Intune
description: 您將在本快速入門中，使用 Microsoft Intune 設定 Android 裝置所需的密碼長度。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/17/2018
ms.topic: quickstart
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 81b4fa08-5333-4c54-9f49-8db5f6984ed2
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: f925df731c3ddd45b13d976b0686d76d941c71e6
ms.sourcegitcommit: 2e88ec7a412a2db35034d30a70d20a5014ddddee
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2018
ms.locfileid: "49395274"
---
# <a name="quickstart-set-a-required-password-length-for-android-devices"></a>快速入門：為 Android 裝置設定必要的密碼長度

您將在本快速入門中，使用 Microsoft Intune 要求您使用 Android 裝置的員工必須先輸入特定長度的密碼，才會在其 Android 裝置上授與資訊存取權。 

> [!IMPORTANT]
> 除了密碼設定之外，也應該考量運用其他系統安全性設定保護您的員工。 如需詳細資訊，請參閱[系統安全性設定](compliance-policy-create-android-for-work.md#system-security-settings)。

如果您沒有 Intune 訂用帳戶，請[註冊免費試用帳戶](free-trial-sign-up.md)。

## <a name="sign-in-to-intune"></a>登入 Intune

請以全域管理員或 Intune 服務管理員身分登入 [Intune](https://aka.ms/intuneportal)。 您可以透過選擇 [所有服務] > [Intune]，在 Azure 入口網站中找到 Intune。 Intune 位於 [Monitoring + Management] (監視 + 管理) 區段。

## <a name="create-a-device-compliance-policy"></a>建立裝置合規性政策
1. 一旦您開啟 [Microsoft Intune] 刀鋒視窗，請選取 [裝置合規性] > [原則][建立原則] > 。
2. 新增 [Android 合規性] 作為 [名稱]。 也請新增 [描述]。
3. 針對 [平台]，選取 [Android]。 
4. 選取 [設定] > [系統安全性] 以顯示 Android [系統安全性] 刀鋒視窗。
5. 在 [密碼] 區段中，按一下 [需要密碼才可解除鎖定行動裝置] 旁邊的 [必要]。
6. 在 [最小密碼長度] 旁邊，輸入 **6**。  

    ![在 Microsoft Intune 中建立群組的螢幕擷取畫面](./media/quickstart-set-password-length-android-01.png)

7. 完成時，按一下 [確定] 關閉 [系統安全性] 刀鋒視窗。 
8. 按一下 [確定] 關閉 [Android 合規性政策] 刀鋒視窗。 
9. 按一下 [建立] 建立原則。

成功建立原則時，它會顯示在 [裝置 complice - 原則] 清單中。 

## <a name="next-steps"></a>接下來的步驟

您可以在本快速入門中，使用 Intune 為員工的 Android 裝置建立合規性政策，以要求長度至少為六個字元的密碼。

> [!div class="nextstepaction"]
> [設定自動註冊](quickstart-setup-auto-enrollment.md)

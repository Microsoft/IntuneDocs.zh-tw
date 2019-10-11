---
title: 在 Microsoft Intune 中使用原則以限制裝置功能 - Azure | Microsoft Docs
description: 在 Microsoft Intune 中新增裝置設定檔以限制 Android、macOS、iOS、iPadOS、Windows Phone 及 Windows 10 裝置上的功能
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/04/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 61a8815bdbb0121d727c80dda0421922e0531cf7
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2019
ms.locfileid: "71724044"
---
# <a name="configure-device-restriction-settings-in-microsoft-intune"></a>在 Microsoft Intune 中設定裝置限制設定

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Intune 包含裝置限制原則，可協助系統管理員控制 Android、iOS、macOS 及 Windows 裝置。 這些限制可讓您控制廣泛的設定及功能，以保護您組織的資源。 例如，系統管理員可以：

- 允許或封鎖裝置相機
- 控制針對 Google Play、應用程式市集、檢視文件，以及遊戲的存取
- 封鎖內建應用程式，或是建立允許或禁止使用之應用程式的清單
- 允許或防止將檔案備份至雲端或儲存體帳戶
- 設定密碼長度下限，以及封鎖簡單密碼

這些功能可於 Intune 中取得，並可由系統管理員設定。 Intune 會使用「組態設定檔」來依據貴組織的需求建立和自訂這些設定。 在設定檔中新增這些功能之後，您接著便可以將設定檔推送或部署到您組織中的裝置。

本文會示範如何建立裝置限制設定檔。 您也可以查看適用於不同平台的所有可用設定。

## <a name="create-the-profile"></a>建立設定檔

1. 登入 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
2. 選取 [裝置設定]   > [設定檔]   > [建立設定檔]  。
3. 輸入下列內容：

    - **名稱**：輸入政策的描述性名稱。 為您的設定檔命名，以方便之後能夠輕鬆識別。 例如，一個良好的原則名稱是 **iOS:Block camera on devices**。
    - **描述**：輸入政策的描述。 這是選擇性設定，但建議執行。
    - **平台**：選擇您的裝置平台。 選項包括：  

        - **Android**
        - **Android 企業**
        - **iOS/iPadOS**
        - **macOS**
        - **Windows Phone 8.1**
        - **Windows 8.1 及更新版本**
        - **Windows 10 及更新版本**

    - **設定檔類型**：選取 [裝置限制]  。

        若想要建立像是 Surface Hub 等 Windows 10 團隊版裝置的裝置限制設定檔，選擇 [裝置限制 (Windows 10 團隊版)]  。

4. 您可設定的設定會視您選擇的平台而不同。 選擇您平台來進行詳細設定：

    - [Android 設定](../device-restrictions-android.md)
    - [Android 企業設定](../device-restrictions-android-for-work.md)
    - [iOS/iPadOS 設定](device-restrictions-ios.md)
    - [macOS 設定](device-restrictions-macos.md)
    - [Windows Phone 8.1 設定](device-restrictions-windows-phone-8-1.md)
    - [Windows 8.1](device-restrictions-windows-8-1.md)
    - [Windows 10 設定](device-restrictions-windows-10.md)
    - [Windows 10 團隊版設定](device-restrictions-windows-10-teams.md)
    - [Windows Holographic for Business 設定](device-restrictions-windows-holographic.md)

5. 當您完成時，請選取 [確定]   > [建立]  儲存變更。

設定檔隨即建立，並顯示在設定檔清單上。

## <a name="next-steps"></a>後續步驟

建立設定檔之後，就可以指派它。 接下來，[指派設定檔](../device-profile-assign.md)並[監視其狀態](../device-profile-monitor.md)。

<!--  Removing image as part of design review; retaining source until we known the disposition.

## Example of device restriction settings

In this high-level example, you'll create a device restriction policy that blocks the use of the built-in camera app on Android devices.

![How to disable the camera on Android devices](./media/device-restrictions-configure/disable-android-camera.png)

-->

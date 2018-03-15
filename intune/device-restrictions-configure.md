---
title: "設定 Microsoft Intune 裝置限制設定"
titleSuffix: 
description: "了解如何使用 Microsoft Intune 設定您管理之裝置上的設定與功能。"
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 3/1/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 62c12cde5ca128a26b10e0e4516e0bbf7e0f0bbb
ms.sourcegitcommit: aafed032492c1b5861d7097a335f9bbb29ce3221
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/02/2018
---
# <a name="how-to-configure-device-restriction-settings-in-microsoft-intune"></a>如何在 Microsoft Intune 中設定裝置限制設定

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

裝置限制可讓您控制各種類別中，您所管理的各種設定及功能，例如：
- 安全性
- 瀏覽器
- 硬體
- 資料共用設定

例如，您可以建立裝置限制設定檔，禁止 iOS 裝置的使用者存取裝置相機 。

了解裝置限制設定檔基本概念，並進一步閱讀每個平台的文章以了解裝置特性。

## <a name="create-a-device-profile-containing-device-restriction-settings"></a>建立內含裝置限制設定的裝置設定檔

1. 登入 [Azure 入口網站](https://portal.azure.com)。
2. 選擇 [All services] (所有服務) > [Intune]。 Intune 位於 [監視 + 管理] 區段。
3. 在 [Intune] 頁面上，選擇 [裝置設定]。
2. 在 [裝置設定] 頁面的 [管理] 區段下，選擇 [設定檔]。
3. 在 [設定檔] 頁面上，選擇 [建立設定檔]。
4. 在 [建立設定檔] 頁面上，為裝置限制設定檔輸入 [名稱] 及 [描述]。
5. 從 [平台] 下拉式清單中，選取要套用自訂設定的裝置平台。 您目前可選擇下列平台之一，進行裝置限制設定︰
    - **Android**
    - **iOS**
    - **macOS**
    - **Windows Phone 8.1**
    - **Windows 8.1 及更新版本**
    - **Windows 10 及更新版本**
6. 從 [設定檔類型] 下拉式清單中，選擇 [裝置限制]。 若想要建立像是 Surface Hub 等 Windows 10 團隊版裝置之裝置限制設定檔，選擇 [裝置限制 (Windows 10 團隊版)]。
7. 您可設定的設定會視您選擇的平台而不同。 前往下列主題之一，即可取得每個平台的詳細設定︰
    - [Android 設定](device-restrictions-android.md)
    - [iOS 設定](device-restrictions-ios.md)
    - [macOS 設定](device-restrictions-macos.md)
    - [Windows Phone 8.1 設定](device-restrictions-windows-phone-8-1.md)
    - [Windows 8.1](device-restrictions-windows-8-1.md)
    - [Windows 10 設定](device-restrictions-windows-10.md)
    - [Windows 10 團隊版設定](device-restrictions-windows-10-teams.md)
    - [Windows Holographic for Business 設定](device-restrictions-windows-holographic.md)
    - [Android for Work 設定](device-restrictions-android-for-work.md)
8. 當您完成時，請返回 [建立設定檔] 頁面，然後按一下 [建立]。

設定檔隨即建立，並出現在 [設定檔清單] 頁面上。
若想繼續，並將此設定檔指派給群組，請參閱[如何指派裝置設定檔](device-profile-assign.md)。

<!--  Removing image as part of design review; retaining source until we known the disposition.

## Example of device restriction settings

In this high-level example, you'll create a device restriction policy that blocks the use of the built-in camera app on Android devices.

![How to disable the camera on Android devices](./media/disable-android-camera.png)

-->
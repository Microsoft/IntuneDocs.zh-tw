---
title: 在 Microsoft Intune 中設定裝置限制設定 - Azure | Microsoft Docs
description: 在 Microsoft Intune 中新增裝置設定檔以限制 Android、macOS、iOS、Windows Phone 及 Windows 10 裝置上的功能
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/27/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 13f93f9fcf813c2e86809d2cc20991d2fd635187
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31024612"
---
# <a name="configure-device-restriction-settings-in-microsoft-intune"></a>在 Microsoft Intune 中設定裝置限制設定

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

裝置限制可讓您控制各種類別中，您所管理的各種設定及功能，例如：
- 安全性
- 瀏覽器
- 硬體
- 資料共用設定

例如，您可以建立裝置限制設定檔，禁止 iOS 裝置的使用者存取裝置相機 。

了解裝置限制設定檔基本概念，並進一步閱讀每個平台的文章以了解裝置特性。

## <a name="create-a-device-profile-containing-device-restriction-settings"></a>建立內含裝置限制設定的裝置設定檔

1. 登入 [Azure 入口網站](https://portal.azure.com)。
2. 選取 [All services] (所有服務)，篩選 [Intune]，然後選取 [Microsoft Intune]。
3. 選取 [裝置設定] > [設定檔] > [建立設定檔]。
4. 輸入裝置限制設定檔的 [名稱] 和 [描述]。
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

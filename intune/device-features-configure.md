---
title: "設定 Microsoft Intune 裝置功能設定"
titleSuffix: 
description: "了解如何在所管理的裝置上使用 Microsoft Intune 設定功能。"
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 3/2/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 6cd646976deb1599c4cbc9154b6f2a487029dd79
ms.sourcegitcommit: 7e5c4d43cbd757342cb731bf691ef3891b0792b5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2018
---
#<a name="configure-device-feature-settings-in-microsoft-intune"></a>在 Microsoft Intune 中設定裝置功能設定

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

裝置功能可讓您控制 iOS 和 macOS 裝置上的功能，例如 AirPrint、通知，以及共用的裝置設定。

使用本文中的資訊，以了解設定裝置功能設定檔的相關基本概念，然後閱讀每個平台的文章，以了解裝置特定內容。

## <a name="create-a-device-profile-containing-device-feature-settings"></a>建立包含裝置功能設定的裝置設定檔

1. 登入 [Azure 入口網站](https://portal.azure.com)。
2. 選擇 [All services] (所有服務) > [Intune]。 Intune 位於 [監視 + 管理] 區段。
3. 在 [Intune] 頁面上，選擇 [裝置設定]。
2. 在 [裝置設定] 頁面的 [管理] 區段下，選擇 [設定檔]。
3. 在 [設定檔] 頁面上，選擇 [建立設定檔]。
4. 在 [建立設定檔] 頁面上，為裝置功能設定檔輸入 [名稱] 及 [描述]。
5. 從 [平台] 下拉式清單中，選取要套用設定的裝置平台。 您目前可為裝置功能選擇下列平台之一︰
    - **iOS**
    - **macOS**
6. 從 [設定檔類型] 下拉式清單中，選擇 [裝置功能]。 
7. 您可設定的設定值隨您選擇的平台而有所不同。 前往下列其中一篇文章，即可取得每個平台的詳細設定︰
    - [適用於 iOS 和 macOS 裝置的 AirPrint 設定](air-print-settings-ios-macos.md)
    - [適用於 iOS 裝置的 AirPlay 設定](airplay-settings-ios.md)
    - [適用於 iOS 的主畫面配置設定](home-screen-settings-ios.md)
    - [適用於 iOS 的應用程式通知設定](app-notification-settings-ios.md)
    - [適用於 iOS 的共用裝置組態設定](shared-device-settings-ios.md)
    - [設定 Intune 以進行 iOS 裝置單一登入](sso-ios.md)
    - [適用於 iOS 的網路內容篩選器](web-content-filter-settings-ios.md)

8. 當您完成時，請選取 [確定] 返回 [建立設定檔] 頁面，然後選擇 [建立]。

設定檔隨即建立，並出現在 [設定檔清單] 頁面上。
## <a name="next-steps"></a>後續步驟

如果您想要將此設定檔指派給群組，請參閱[如何指派裝置設定檔](device-profile-assign.md)。




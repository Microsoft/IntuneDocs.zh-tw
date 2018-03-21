---
title: "如何設定 Intune Wi-Fi 設定"
titleSuffix: Microsoft Intune
description: "了解如何使用 Microsoft Intune 在您管理的裝置上設定 Wi-Fi 連線。"
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 03/02/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 90d2df028d5a61bb134b6a2b76efa570eed80f20
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/08/2018
---
# <a name="how-to-configure-wi-fi-settings-in-microsoft-intune"></a>如何在 Microsoft Intune 中設定 Wi-Fi 設定

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

使用 Microsoft Intune Wi-Fi 設定檔，將無線網路設定指派給您組織中的使用者與裝置。 當您指派 Wi-Fi 設定檔時，使用者不需要自行設定，即可存取您公司的 Wi-Fi 網路。

例如，您安裝了名為 Contoso Wi-Fi 的新 Wi-Fi 網路，且想要將所有 iOS 裝置都設定為連線至此網路。 程序如下︰

1. 建立 Wi-Fi 設定檔，內含連線到 Contoso Wi-Fi 無線網路所需的設定。
2. 將設定檔指派給此群組，包含所有 iOS 裝置的使用者。
3. 使用者即可在其裝置上的無線網路清單中找到此新的 Contoso Wi-Fi 網路，且可輕鬆地連線到該網路。

## <a name="supported-device-platforms"></a>支援的裝置平台

Wi-Fi 設定檔支援下列裝置平台：

- Android 4 及更新版本
- Android for Work
- iOS 8.0 和更新版本
- macOS (Mac OS X 10.9 及更新版本)

對於執行 Windows 8.1、Windows 10、Windows 10 行動裝置版和 Windows Holographic for Business 的裝置，可以匯入先前從其他裝置所匯出的 Wi-Fi 設定。

使用本主題中的資訊，可深入了解設定 Wi-Fi 設定檔的相關基本概念，然後可深入閱讀每個平台的主題，以了解裝置專屬內容。

## <a name="create-a-device-profile-containing-wi-fi-settings"></a>建立內含 Wi-Fi 設定的裝置設定檔

1. 登入 [Azure 入口網站](https://portal.azure.com)。
2. 選擇 [All services] (所有服務) > [Intune]。 Intune 位於 [監視 + 管理] 區段。
3. 在 [Intune] 窗格中，選擇 [裝置設定]。
2. 在 [裝置設定] 窗格的 [管理] 區段下，選擇 [設定檔]。
3. 在 [設定檔] 窗格中，選擇 [建立設定檔]。
4. 在 [建立設定檔] 窗格中，為 Wi-Fi 設定檔輸入 [名稱] 及 [描述]。
5. 從 [平台] 下拉式清單中，選取要套用 Wi-Fi 設定的裝置平台。 您目前可為 Wi-Fi 裝置設定，選擇下列平台之一︰
    - **Android**
    - **Android for Work**
    - **iOS**
    - **macOS**
    - **Windows Phone 8.1**
    - **Windows 8.1 及更新版本**
    - **Windows 10 及更新版本**

   > [!IMPORTANT]
   > 如果您要為執行 Windows 10 (包括 Windows Holographic for Business) 的裝置建立設定檔，您必須選擇 **Windows 8.1 和更新版本**平台。 **Windows 10 和更新版本**平台不包含 Wi-Fi 設定檔類型。 

6. Apple 或 Android 裝置請在 [WiFi type] (WiFi 類型) 下拉式清單中選擇 [基本] 或 [企業]。 您可以使用 [基本] 提供基本功能，像是網路名稱以及 SSID。 您可利用 **Enterprise** 提供更進階的資訊，例如「可延伸的驗證通訊協定」(EAP) (如果您的 Wi-Fi 網路使用此通訊協定)。 

   **Wi-Fi 匯入**設定檔 (適用於 Windows 8.1 與更新版本) 可讓您將 Wi-Fi 設定匯入為先前從不同裝置所匯出的 XML 檔案。
1. 您可設定的設定值隨您選擇的平台而有所不同。 前往下列主題之一，即可取得每個平台的詳細設定︰
    - [Android 和 Android for Work 設定](wi-fi-settings-android.md)
    - [iOS 設定](wi-fi-settings-ios.md)
    - [macOS 設定](wi-fi-settings-macos.md)
    - [Windows 8.1 和更新版本設定](wi-fi-settings-import-windows-8-1.md) (包括 Windows Holographic for Business)
1. 當您完成時，請返回 [建立設定檔] 窗格，然後點擊 [建立]。

設定檔隨即建立，並出現在 [設定檔清單] 窗格上。

## <a name="next-steps"></a>接下來的步驟

若想繼續，並將此設定檔指派給群組，請參閱[如何指派裝置設定檔](device-profile-assign.md)。

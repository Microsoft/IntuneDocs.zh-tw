---
title: "如何設定 Intune Wi-Fi 設定"
titleSuffix: Azure portal
description: "了解如何使用 Intune 在您管理的裝置上設定 Wi-Fi 連線。"
keywords: 
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.date: 06/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1fadb488-9c6c-43c1-ba23-8c69db633b96
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: e3333a5addfd0c4ab757121e22e19ac66c0b3e1d
ms.sourcegitcommit: ec8561b8c63515e0b5f21a858984108dc5dbd5d3
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
---
# <a name="how-to-configure-wi-fi-settings-in-microsoft-intune"></a>如何在 Microsoft Intune 中設定 Wi-Fi 設定

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

使用 Microsoft Intune Wi-Fi 設定檔，將無線網路設定指派給您組織中的使用者與裝置。 當您指派 Wi-Fi 設定檔時，使用者不需要自行設定，即可存取您公司的 Wi-Fi 網路。

例如，您安裝了名為 Contoso Wi-Fi 的新 Wi-Fi 網路，且想要將所有 iOS 裝置都設定為連線至此網路。 程序如下︰

1. 建立 Wi-Fi 設定檔，內含連線到 Contoso Wi-Fi 無線網路所需的設定。
2. 將設定檔指派給此群組，包含所有 iOS 裝置的使用者。
3. 使用者即可在其裝置上的無線網路清單中找到此新的 Contoso Wi-Fi 網路，且可輕鬆地連線到該網路。

Wi-Fi 設定檔支援下列裝置平台：

- Android 4 及更新版本
- Android for Work
- iOS 8.0 和更新版本
- macOS (Mac OS X 10.9 及更新版本)

對於執行 Windows 8.1、Windows 10 以及 Windows 10 行動裝置版的裝置，可以匯入先前從其他裝置所匯出的 Wi-fi 設定。

使用本主題中的資訊，可深入了解設定 Wi-Fi 設定檔的相關基本概念，然後可深入閱讀每個平台的主題，以了解裝置專屬內容。

## <a name="create-a-device-profile-containing-wi-fi-settings"></a>建立內含 Wi-Fi 設定的裝置設定檔

1. 登入 Azure 入口網站。
2. 選擇 [更多服務]  >  [監視 + 管理]  >  [Intune]。
3. 在 [Intune] 刀鋒視窗中，選擇 [裝置設定]。
2. 在 [裝置設定] 刀鋒視窗中，選擇 [管理]  >  [設定檔]。
3. 在設定檔刀鋒視窗中，選擇 [建立設定檔]。
4. 在 [建立設定檔] 刀鋒視窗中，為 Wi-Fi 設定檔輸入 [名稱] 及 [描述]。
5. 從 [平台] 下拉式清單中，選取要套用 Wi-Fi 設定的裝置平台。 您目前可為 Wi-Fi 裝置設定，選擇下列平台之一︰
    - **Android**
    - **Android for Work**
    - **iOS**
    - **macOS**
    - **Windows 8.1 及更新版本 (匯入設定檔)**
6. 從 [設定檔類型] 下拉式清單中，選擇 [Wi-Fi Basic] 或 [Wi-Fi Enterprise]。
    >[!TIP]
    >使用 [Wi-Fi Basic] 可提供基本功能，像是網路名稱以及 SSID。 您可利用 **Wi-Fi Enterprise** 提供更進階的資訊，像是「可延伸的驗證通訊協定 (EAP)」(如果您的 Wi-Fi 網路使用此)。 您可利用 **Wi-Fi 匯入** (適用於 Windows 8.1 與 Windows 10)，將 Wi-Fi 設定匯入為先前從不同裝置所匯出的 XML 檔案。
7. 您可設定的設定值取決於您選擇的平台而有所不同。 前往下列主題之一，即可取得每個平台的詳細設定︰
    - [Android 和 Android for Work 設定](wi-fi-settings-android.md)
    - [iOS 設定](wi-fi-settings-ios.md)
    - [macOS 設定](wi-fi-settings-macos.md)
    - [Windows Phone 8.1 設定](wi-fi-settings-import-windows-8-1.md)
8. 當您完成時，請返回 [建立設定檔] 刀鋒視窗，然後點擊 [建立]。

隨即會建立設定檔，並會出現在 [設定檔清單] 刀鋒視窗上。
若想繼續，並將此設定檔指派給群組，請參閱[如何指派裝置設定檔](device-profile-assign.md)。

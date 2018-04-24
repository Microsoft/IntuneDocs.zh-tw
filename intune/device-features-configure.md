---
title: 使用 Microsoft Intune 建立 iOS 或 macOS 裝置設定檔 - Azure | Micrososft Docs
description: 新增或建立 iOS 或 macOS 裝置設定檔，然後在 Microsoft Intune 中設定 AirPrint、AirPlay、主畫面配置、應用程式通知、共用裝置、單一登入以及網路內容篩選器的設定。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/07/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: d823a7f8d3478c0ff6c0049a6bbaa76bb4247479
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="add-ios-or-macos-device-feature-settings-in-intune"></a>在 Intune 中新增 iOS 或 macOS 裝置功能設定

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

裝置功能可讓您在 iOS 及 macOS 裝置上控制一定範圍的設定與功能，例如：

- AirPrint 和 AirPlay 設定
- 主畫面配置
- 應用程式的通知
- 共用裝置設定
- 設定單一登入
- 篩選 web 內容

本文章會示範設定 iOS 裝置功能設定檔的基本概念。 然後，您可以瀏覽其他文章，為您的裝置設定平台專屬的設定。

## <a name="create-a-device-profile"></a>建立裝置設定檔

1. 登入 [Azure 入口網站](https://portal.azure.com)。
2. 選取 [所有服務]，篩選 [Intune]，然後選取 [Microsoft Intune]。
3. 選取 [裝置設定] > [設定檔] > [建立設定檔]。
4. 輸入下列內容：

   - **名稱**：為新的設定檔輸入描述性名稱。
   - **描述**：輸入設定檔的描述。 (這是選用項目，但建議使用。)
   - **平台**：選取您的平台類型：
     - **iOS**
     - **macOS**
   - **設定檔類型**：選取 [裝置功能]。
   - **設定**：設定取決於您選擇的平台。 下列文章會描述每個設定檔類型的設定︰

     - [適用於 iOS 和 macOS 裝置的 AirPrint 設定](air-print-settings-ios-macos.md)
     - [適用於 iOS 裝置的 AirPlay 設定](airplay-settings-ios.md)
     - [適用於 iOS 的主畫面配置設定](home-screen-settings-ios.md)
     - [適用於 iOS 的應用程式通知設定](app-notification-settings-ios.md)
     - [適用於 iOS 的共用裝置組態設定](shared-device-settings-ios.md)
     - [設定 Intune 以進行 iOS 裝置單一登入](sso-ios.md)
     - [適用於 iOS 的網路內容篩選器](web-content-filter-settings-ios.md)

5. 當您完成時，請選取 [確定]，然後選擇 [建立] 儲存變更。

會建立設定檔，而且會出現在清單中。

## <a name="next-step"></a>後續步驟

若要將此設定檔指派給群組，請參閱[如何指派裝置設定檔](device-profile-assign.md)。
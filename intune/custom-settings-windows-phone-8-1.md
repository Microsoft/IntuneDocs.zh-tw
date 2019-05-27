---
title: 在 Microsoft Intune 中將自訂設定新增至 Windows Phone 8.1 裝置 - Azure | Microsoft Docs
titleSuffix: ''
description: 在 Microsoft Intune 中新增或建立自訂設定檔，將 OMA-URI 設定用於執行 Windows Phone 8.1 的裝置。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/24/2018
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: cb54f5e4cede6141c87073a7dfb6570cf85e920b
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 05/23/2019
ms.locfileid: "66042887"
---
# <a name="use-custom-settings-for-windows-phone-81-devices-in-intune"></a>在 Intune 中使用 Windows Phone 8.1 裝置的自訂設定

透過 Microsoft Intune，您可以使用「自訂設定檔」新增或建立 Windows Phone 8.1 裝置的自訂設定。 自訂設定檔是 Intune 中的功能。 其設計目的是為了新增 Intune 中未內建的裝置設定和功能。

Windows Phone 8.1 自訂設定檔會使用開放行動聯盟的統一資源識別項 (OMA-URI) 設定來進行各種功能設定。 行動裝置製造商通常會使用這些設定來控制裝置上的功能。

本文示範如何建立 Windows Phone 8.1 裝置的自訂設定檔。 

## <a name="create-the-profile"></a>建立設定檔

1. 在 [Azure 入口網站](https://portal.azure.com)中，選取 [所有服務]，篩選 [Intune]，然後選取 [Microsoft Intune]。
2. 選取 [裝置設定] > [設定檔] > [建立設定檔]。
3. 輸入下列設定：

    - **名稱**：輸入設定檔的名稱，例如 `windows phone custom profile`。
    - **描述**：輸入設定檔的描述。
    - **平台**：選擇 [Windows Phone 8.1]。
    - **設定檔類型**：選擇 [自訂]。

4. 在 [自訂 OMA-URI 設定] 中，選取 [新增]。 輸入下列設定：

    - **名稱**：輸入 OMA-URI 設定的唯一名稱，協助您在設定清單中識別該設定。
    - **描述**：輸入描述來概述設定及其他可協助您找到設定檔的相關資訊。
    - **OMA-URI** (區分大小寫)：輸入您要用作設定的 OMA-URI。
    - **資料類型**：選擇您要用於這個 OMA-URI 設定的資料類型。 選項包括：

        - 字串
        - 字串 (XML 檔案)
        - 日期和時間
        - 整數
        - 浮點數
        - 布林值
        - Base64 (檔案)

    - **值**：輸入要與您輸入之 OMA-URI 相關聯的資料值。 該值取決於您選取的資料類型。 例如，如果您選擇 [日期和時間]，請從日期選擇器選取值。

    新增一些設定之後，您可以選取 [匯出]。 [匯出] 會以逗號分隔值 (.csv) 檔案格式，為您新增的所有值建立一份清單。

5. 按一下 [確定] 以儲存您的變更。 視需要繼續新增更多設定。
6. 完成時，選擇 [確定] > [建立] 以建立 Intune 設定檔。 完成時，您的設定檔會顯示在 [裝置設定 - 設定檔] 清單中。

## <a name="next-steps"></a>後續步驟

設定檔已建立，但還不會執行任何動作。 接下來，請[指派此設定檔](device-profile-assign.md)。

了解如何在 [Windows 10 裝置](custom-settings-windows-10.md)上建立自訂設定檔。

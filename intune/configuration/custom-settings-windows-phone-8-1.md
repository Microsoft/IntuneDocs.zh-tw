---
title: 在 Microsoft Intune 中將自訂設定新增至 Windows Phone 8.1 裝置 - Azure | Microsoft Docs
titleSuffix: ''
description: 在 Microsoft Intune 中新增或建立自訂設定檔，將 OMA-URI 設定用於執行 Windows Phone 8.1 的裝置。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/18/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6ed1f43e7c7e6f0580cb22513a489fb32c30e5f6
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 12/19/2019
ms.locfileid: "75206749"
---
# <a name="use-custom-settings-for-windows-phone-81-devices-in-intune"></a>在 Intune 中使用 Windows Phone 8.1 裝置的自訂設定

透過 Microsoft Intune，您可以使用「自訂設定檔」新增或建立 Windows Phone 8.1 裝置的自訂設定。 自訂設定檔是 Intune 中的功能。 其設計目的是為了新增 Intune 中未內建的裝置設定和功能。

Windows Phone 8.1 自訂設定檔會使用開放行動聯盟的統一資源識別項 (OMA-URI) 設定來進行各種功能設定。 行動裝置製造商通常會使用這些設定來控制裝置上的功能。 [Windows Phone 8.1 MDM 通訊協定檔](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-phone/dn499787(v=technet.10))會列出這些設定。

本文示範如何建立 Windows Phone 8.1 裝置的自訂設定檔。 

## <a name="create-the-profile"></a>建立設定檔

1. 登入 [Microsoft Endpoint Manager 系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。
2. 選取 [裝置]   > [組態設定檔]   > [建立設定檔]  。
3. 輸入下列設定：

    - **名稱**：為設定檔輸入描述性名稱。 命名您的設定檔，以方便之後能輕鬆識別。 例如，良好的設定檔名稱是**Windows phone 自訂設定檔**。
    - **描述**：輸入描述來概述設定和其他重要的詳細資料。
    - **平臺**：選取 [ **Windows Phone 8.1**]。
    - **配置檔案類型**：選取 [**自訂**]。

4. 在 [自訂 OMA-URI 設定]  中，選取 [新增]  。 輸入下列設定：

    - **名稱**：輸入 OMA-URI 設定的唯一名稱，協助您在設定清單中識別該設定。
    - **描述**：輸入描述來概述設定及其他可協助您找到設定檔的相關資訊。
    - **OMA-URI** (區分大小寫)：輸入您要用作設定的 OMA-URI。
    - **資料類型**：選取您要用於這個 OMA-URI 設定的資料類型。 選項包括：

        - 字串
        - 字串 (XML 檔案)
        - 日期和時間
        - 整數
        - 浮點數
        - 布林值
        - Base64 (檔案)

    - **值**：輸入要與您輸入之 OMA-URI 相關聯的資料值。 該值取決於您選取的資料類型。 例如，如果您選取 [日期和時間]  ，請從日期選擇器選取值。

    新增一些設定之後，您可以選取 [匯出]  。 [匯出]  會以逗號分隔值 (.csv) 檔案格式，為您新增的所有值建立一份清單。

5. 按一下 [確定]  以儲存您的變更。 視需要繼續新增更多設定。
6. 完成時，選取 [確定]   > [建立]  以建立 Intune 設定檔。 完成時，您的設定檔會顯示在 [裝置 - 設定檔]  清單中。

## <a name="example"></a>範例

在下列範例中，當您在承運商涵蓋範圍外行動電話通訊網路時，會防止 Windows 8.1 的電話裝置變更行動資料。

- **名稱**：允許行動電話資料漫遊
- **描述**：允許或禁止行動電話資料漫遊
- **Oma-uri** （區分大小寫）：./Vendor/MSFT/PolicyManager/My/Connectivity/AllowCellularDataRoaming
- **資料類型**：整數
- **值**：0

## <a name="next-steps"></a>後續步驟

設定檔已建立，但還不會執行任何動作。 接下來，[指派設定檔](../device-profile-assign.md)並[監視其狀態](device-profile-monitor.md)。

[在 Windows 10 裝置上建立自訂設定檔](../custom-settings-windows-10.md)。

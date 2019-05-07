---
title: 在 Microsoft Intune 中將自訂設定新增至 Android 裝置 - Azure | Microsoft Docs
description: 在 Microsoft Intune 中為 Android 裝置新增或建立自訂設定檔，以使用預先共用金鑰、建立 WiFi 設定檔、建立個別應用程式 VPN 設定檔，或允許、禁止 Samsung Knox Standard 裝置應用程式
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/24/2018
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 494b3892-916e-4b40-9b67-61adec889bdf
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: ba6d2f60d91388aa1c8ceea6580f1d583d4c987c
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57564817"
---
# <a name="use-custom-settings-for-android-devices-in-microsoft-intune"></a>在 Microsoft Intune 中使用 Android 裝置的自訂設定

透過 Microsoft Intune，您可以使用「自訂設定檔」新增或建立 Android 裝置的自訂設定。 自訂設定檔是 Intune 中的功能。 其設計目的是為了新增未內建在 Intune 的裝置設定和功能。

Android 自訂設定檔會使用開放行動聯盟的統一資源識別項 (OMA URI) 設定來進行 Android 裝置上的各種功能設定。 行動裝置製造商通常會使用這些設定來控制這些功能。

使用自訂設定檔，您便可以設定及指派下列 Android 設定。 Intune 並未內建下列設定：

- [使用預先共用的金鑰建立 Wi-Fi 設定檔](/intune/wi-fi-profile-shared-key)
- [建立個別應用程式 VPN 設定檔](/intune/android-pulse-secure-per-app-vpn)
- [允許或禁止應用程式在 Samsung Know Standard 裝置上執行](/intune/samsung-knox-apps-allow-block)

>[!IMPORTANT]
> 自訂設定檔只能進行列出的設定。 Android 裝置不會公開您可設定的完整 OMA-URI 設定清單。 如果您希望能夠使用更多設定，請在 [Intune Uservoice 網站](https://microsoftintune.uservoice.com/forums/291681-ideas) (Intune Uservoice 網站) 票選更多設定。

本文示範如何建立 Android 裝置的自訂設定檔。

## <a name="create-the-profile"></a>建立設定檔

1. 在 [Azure 入口網站](https://portal.azure.com)中，選取 [所有服務]，篩選 [Intune]，然後選取 [Microsoft Intune]。
2. 選取 [裝置設定] > [設定檔] > [建立設定檔]。
3. 輸入下列設定：

    - **名稱**：輸入設定檔的名稱，例如 `android custom profile`。
    - **描述**：輸入設定檔的描述。
    - **平台**：選擇 [Android]。
    - **設定檔類型**：選擇 [自訂]。

4. 在 [自訂 OMA-URI 設定] 中，選取 [新增]。 輸入下列設定：

    - **名稱**：為 OMA-URI 設定輸入唯一名稱，使其易於找到。
    - **描述**：輸入描述來概述設定和其他重要的詳細資料。
    - **OMA-URI**：輸入您要用作設定的 OMA-URI。
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

了解如何[在 Android Enterprise 裝置上建立設定檔](custom-settings-android-for-work.md)。

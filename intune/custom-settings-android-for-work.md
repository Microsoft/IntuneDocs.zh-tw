---
title: 在 Microsoft Intune 中將自訂設定新增至 Android Enterprise 裝置 - Azure | Microsoft Docs
description: 在 Microsoft Intune 中新增或建立可讓 Android Enterprise 裝置建立的自訂設定檔
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/24/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4724d6e5-05e5-496c-9af3-b74f083141f8
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 73075ed06e98ca987e87a7cfda70c546127bf881
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2018
ms.locfileid: "52179587"
---
# <a name="use-custom-settings-for-android-enterprise-devices-in-microsoft-intune"></a>在 Microsoft Intune 中使用 Android Enterprise 裝置的自訂設定

透過 Microsoft Intune，您可以使用「自訂設定檔」新增或建立 Android Enterprise 裝置的自訂設定。 自訂設定檔是 Intune 中的功能。 其設計目的是為了新增未內建在 Intune 的裝置設定和功能。

Android Enterprise 自訂設定檔會使用開放行動聯盟的統一資源識別項 (OMA-URI) 設定來控制 Android Enterprise 裝置上的各種功能。 行動裝置製造商通常會使用這些設定來控制這些功能。

Intune 支援有限數目的 Android 自訂設定檔。

本文示範如何建立 Android Enterprise 裝置的自訂設定檔。 其中也會提供封鎖複製和貼上的自訂設定檔範例。

## <a name="create-the-profile"></a>建立設定檔

1. 在 [Azure 入口網站](https://portal.azure.com)中，選取 [所有服務]，篩選 [Intune]，然後選取 [Microsoft Intune]。
2. 選取 [裝置設定] > [設定檔] > [建立設定檔]。
3. 輸入下列設定：

    - **名稱**：輸入設定檔的名稱，例如 `android enterprise custom profile`
    - **描述**：輸入設定檔的描述
    - **平台**：選擇 [Android Enterprise]
    - **設定檔類型**：選擇 [自訂]

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

## <a name="example"></a>範例

在此範例中，您會建立自訂設定檔，在 Android Enterprise 裝置上限制工作和個人應用程式之間的複製和貼上動作。

1. 在 [Azure 入口網站](https://portal.azure.com)中，選取 [所有服務]，篩選 [Intune]，然後選取 [Microsoft Intune]。
2. 選取 [裝置設定] > [設定檔] > [建立設定檔]。
3. 輸入下列設定：

    - **名稱**：輸入設定檔的名稱，例如 `android ent block copy paste custom profile`。
    - **描述**：輸入設定檔的描述。
    - **平台**：選擇 [Android Enterprise]。
    - **設定檔類型**：選擇 [自訂]。

4. 在 [自訂 OMA-URI 設定] 中，選取 [新增]。 輸入下列設定：

    - **名稱**：輸入類似 `Block copy and paste` 的內容。
    - **描述**：輸入類似 `Blocks copy/paste between work and personal apps` 的內容。
    - **OMA-URI**：輸入 `./Vendor/MSFT/WorkProfile/DisallowCrossProfileCopyPaste`。
    - **資料類型**：選擇 [布林值]，讓此 OMA-URI 的值為 **True** 或 **False**。
    - **值**：選擇 [True]。

5. 輸入設定之後，您的環境應該如下圖所示：

    ![針對 Android 工作設定檔封鎖複製和貼上。](./media/custom-policy-afw-copy-paste.png)

當您將此設定檔指派至您所管理的 Android Enterprise 裝置時，工作設定檔和個人設定檔中的應用程式，將無法在彼此之間進行複製和貼上。

## <a name="next-steps"></a>接下來的步驟

設定檔已建立，但還不會執行任何動作。 接下來，請[指派此設定檔](device-profile-assign.md)。

了解如何[在 Android 裝置上建立設定檔](custom-settings-android.md)。
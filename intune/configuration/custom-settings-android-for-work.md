---
title: 在 Microsoft Intune 中將自訂設定新增至 Android Enterprise 裝置 - Azure | Microsoft Docs
description: 在 Microsoft Intune 中新增或建立可讓 Android Enterprise 裝置建立的自訂設定檔
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
ms.assetid: 4724d6e5-05e5-496c-9af3-b74f083141f8
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1bd6e2d5ceebd23e87f464d15376594d1764c5b8
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 12/19/2019
ms.locfileid: "75206800"
---
# <a name="use-custom-settings-for-android-enterprise-devices-in-microsoft-intune"></a>在 Microsoft Intune 中使用 Android Enterprise 裝置的自訂設定

透過 Microsoft Intune，您可以使用「自訂設定檔」新增或建立 Android Enterprise 工作設定檔裝置的自訂設定。 自訂設定檔是 Intune 中的功能。 其設計目的是為了新增未內建在 Intune 的裝置設定和功能。

Android Enterprise 自訂設定檔會使用開放行動聯盟的統一資源識別項 (OMA-URI) 設定來控制 Android Enterprise 裝置上的各種功能。 行動裝置製造商通常會使用這些設定來控制這些功能。

Intune 支援下列有限數目的 Android Enterprise 自訂設定檔：

- ./Vendor/MSFT/WiFi/Profile/SSID/Settings：[使用預先共用金鑰建立 wi-fi 設定檔](wi-fi-profile-shared-key.md)中有一些範例。
- ./Vendor/MSFT/VPN/Profile/Name/PackageList：[建立個別應用程式 VPN 設定檔](android-pulse-secure-per-app-vpn.md)有一些範例。
- ./Vendor/msft/workprofile/disallowcrossprofilecopypaste：請參閱這篇文章中的[範例](#example)。 此設定也可以在使用者介面中使用。 如需詳細資訊，請參閱[允許或限制功能的 Android Enterprise 裝置設定](device-restrictions-android-for-work.md)。

如果您需要其他設定，請參閱[OEMConfig For Android Enterprise](android-oem-configuration-overview.md)。

本文示範如何建立 Android Enterprise 裝置的自訂設定檔。 其中也會提供封鎖複製和貼上的自訂設定檔範例。

## <a name="create-the-profile"></a>建立設定檔

1. 登入 [Microsoft Endpoint Manager 系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。
2. 選取 [裝置]   > [組態設定檔]   > [建立設定檔]  。
3. 輸入下列設定：

    - **名稱**：為設定檔輸入描述性名稱。 命名您的設定檔，以方便之後能輕鬆識別。 例如，良好的設定檔名稱是**Android Enterprise 自訂設定檔**。
    - **描述**：輸入設定檔的描述。 這是選擇性設定，但建議執行。
    - **平台**：選取 [Android 企業]  。
    - **配置檔案類型**：選取 [**自訂**]。

4. 在 [自訂 OMA-URI 設定]  中，選取 [新增]  。 輸入下列設定：

    - **名稱**：為 OMA-URI 設定輸入唯一名稱，使您可以輕鬆找到它。
    - **描述**：輸入描述來概述設定和其他重要的詳細資料。
    - **OMA-URI**：輸入您要用作設定的 OMA-URI。
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

在此範例中，您會建立自訂設定檔，在 Android Enterprise 裝置上限制工作和個人應用程式之間的複製和貼上動作。

1. 登入 [Microsoft Endpoint Manager 系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。
2. 選取 [裝置]   > [組態設定檔]   > [建立設定檔]  。
3. 輸入下列設定：

    - **名稱**：為設定檔輸入描述性名稱。 命名您的設定檔，以方便之後能輕鬆識別。 例如，輸入**android ent 區塊複製貼上自訂設定檔**。
    - **描述**：輸入設定檔的描述。 這是選擇性設定，但建議執行。
    - **平台**：選取 [Android 企業]  。
    - **配置檔案類型**：選取 [**自訂**]。

4. 在 [自訂 OMA-URI 設定]  中，選取 [新增]  。 輸入下列設定：

    - **名稱**：輸入類似 `Block copy and paste` 的內容。
    - **描述**：輸入類似 `Blocks copy/paste between work and personal apps` 的內容。
    - **OMA-URI**：輸入 `./Vendor/MSFT/WorkProfile/DisallowCrossProfileCopyPaste`。
    - **資料類型**：選取 [布林值]  ，讓此 OMA-URI 的值為 **True** 或 **False**。
    - **值**：選取 [True]  。

5. 輸入設定之後，您的環境應該如下圖所示：

    ![針對 Android 工作設定檔封鎖複製和貼上。](./media/custom-settings-android-for-work/custom-policy-afw-copy-paste.png)

當您將此設定檔指派至您所管理的 Android Enterprise 裝置時，工作設定檔和個人設定檔中的應用程式，將無法在彼此之間進行複製和貼上。

## <a name="next-steps"></a>後續步驟

設定檔已建立，但還不會執行任何動作。 接下來，[指派設定檔](../device-profile-assign.md)並[監視其狀態](device-profile-monitor.md)。

[在 Android 裝置上建立自訂設定檔](../custom-settings-android.md)。

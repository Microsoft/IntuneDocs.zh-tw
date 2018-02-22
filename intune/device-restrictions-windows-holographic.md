---
title: "適用於 Windows Holographic for Business 的 Intune 裝置限制設定"
titlesuffix: Azure portal
description: "了解 Windows Holographic for Business 裝置上可用以控制裝置設定與功能的 Intune 設定。」"
keywords: 
author: vhorne
ms.author: victorh
manager: angrobe
ms.date: 1/19/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 300ddb15f2d7b8f2fc6ab4a0e9e32852e0604e0a
ms.sourcegitcommit: 93622d740cbd12043eedc25a9699cc4256e23e7e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/01/2018
---
# <a name="windows-holographic-for-business-device-restriction-settings-in-microsoft-intune"></a>Microsoft Intune 中的 Windows Holographic for Business 裝置限制設定

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

執行 Windows Holographic for Business 的裝置，例如 Microsoft Hololens，支援下列裝置限制設定。

## <a name="general"></a>一般

- **手動取消註冊** - 讓使用者可從裝置手動刪除工作場所帳戶。
- **Cortana** - 啟用或停用 Cortana 語音助理。
- **地理位置** - 指定裝置是否可以使用定位服務資訊。



## <a name="password"></a>密碼
-   **密碼** - 需要使用者輸入密碼才可存取該裝置。
    -   **裝置從閒置狀態回復時需要密碼** - 指定使用者必須輸入密碼才能解除鎖定裝置。



## <a name="app-store"></a>App Store

-   **應用程式市集** - 啟用或封鎖裝置使用應用程式市集。
-   **自動更新來自市集的應用程式** - 允許自動更新從 Microsoft 網上商店安裝的應用程式。
-   **安裝信任的應用程式** - 允許側載使用受信任憑證簽署的應用程式。
-   **開發人員解除鎖定** - 允許 Windows 開發人員設定，例如允許使用者修改側載應用程式。

## <a name="edge-browser"></a>Microsoft Edge 瀏覽器

-   **Microsoft Edge 瀏覽器** - 允許在裝置上使用 Edge 網頁瀏覽器。
-   **Cookie** - 讓瀏覽器儲存網際網路 Cookie 到裝置上。
-   **快顯視窗** - 封鎖瀏覽器中的快顯視窗 (僅適用於 Windows 10 Desktop)。
-   **搜尋建議** - 讓您的搜尋引擎在您輸入搜尋片語時建議網站。
-   **密碼管理員** - 啟用或停用 Microsoft Edge 密碼管理員功能。
- **傳送不追蹤標頭** - 設定 Microsoft Edge 瀏覽器以傳送「不追蹤」標頭給使用者瀏覽的網站。

## <a name="windows-defender-smart-screen"></a>Windows Defender SmartScreen 篩選工具

- **適用於 Microsoft Edge 的 SmartScreen 篩選工具** - 啟用 Edge SmartScreen 以存取網站和檔案下載。

## <a name="search"></a>搜尋
- **搜尋位置** - 指定搜尋是否可使用位置資訊。 資訊


## <a name="cloud-and-storage"></a>雲端與儲存體
-   **Microsoft 帳戶** - 讓使用者建立 Microsoft 帳戶與裝置之間的關聯。

## <a name="cellular-and-connectivity"></a>行動數據與連線

-   **藍牙**- 控制使用者是否可在裝置上啟用及設定藍牙。
-   **藍牙探索** - 讓其他藍牙啟用的裝置探索此裝置。
-   **藍牙廣告** - 讓藍牙可透過藍牙裝置接收廣告。

## <a name="control-panel-and-settings"></a>控制台和設定

- **修改系統時間** - 防止使用者變更裝置日期和時間。

## <a name="reporting-and-telemetry"></a>報告和遙測

- **共用使用方式資料** - 選取診斷資料傳送層級。
---
title: "Windows 8.1 的 Intune 裝置限制設定"
titleSuffix: Azure portal
description: "了解 Windows 8.1 裝置上可用以控制裝置設定與功能的 Intune 設定。"
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 08/01/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: fe5785e9-8d35-4ad7-95e8-d50f8d87154a
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 3c96340255e9b71694278b5a396d907a6212541d
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2018
---
# <a name="windows-81-and-later-device-restriction-settings-in-microsoft-intune"></a>Microsoft Intune 中 Windows 8.1 及更新版本的裝置限制設定

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

## <a name="general"></a>一般

-   **診斷資料提交** - 讓裝置可將診斷資訊提交到 Microsoft。
-   **防火牆** - 需要開啟 Windows 防火牆。
-   **使用者帳戶控制** - 需要在裝置上使用使用者帳戶控制 (UAC)。

## <a name="password"></a>密碼
-   **必要的密碼類型** - 需要使用者輸入密碼才可存取該裝置。
-   **密碼長度下限** - 設定密碼的必要長度下限 (字元)。
-   **登入失敗幾次後即抹除裝置** - 若登入嘗試失敗了此次數之後，即抹除該裝置。
-   **沒有活動最久幾分鐘後鎖定螢**指定在需要密碼將裝置解鎖之前，裝置必須處於閒置狀態的分鐘數。
-   **密碼到期 (天數)** - 指定多少天後必須變更裝置密碼。
-   **避免重複使用以前用過的密碼** - 指定使用者是否可以設定先前已使用的密碼。
-   **圖片密碼和 PIN** - 可以在裝置上使用圖片密碼和 PIN。 圖片密碼可讓使用者利用圖片上的手勢登入。 PIN 可讓使用者快速利用 4 位數代碼登入。
-   **加密** - 需要加密裝置上的檔案。<br>若要在執行 Windows 8.1 的裝置上強制加密，您必須在每個裝置上安裝 [2014 年 12 月適用於 Windows 的 MDM 用戶端更新](https://support.microsoft.com/kb/3013816) 。
如果您針對 Windows 8.1 裝置啟用此設定，則裝置的所有使用者必須都具有 Microsoft 帳戶。
為了讓加密能運作，裝置必須符合 [Microsoft InstantGo](https://blogs.windows.com/windowsexperience/2014/06/19/instantgo-a-better-way-to-sleep/#IBHULcTfI4PokO8X.97) 硬體認證需求。
當您在裝置上強制加密時，就只能從使用者 Microsoft 帳戶存取修復金鑰，該帳戶是從其 OneDrive 帳戶進行存取的。 您無法代表使用者修復此金鑰。     



## <a name="browser"></a>瀏覽器
-   **自動填滿** - 讓使用者可變更瀏覽器中的自動完成設定。
-   **詐騙警告** - 啟用或停用潛在詐騙網站的警告。
-   **SmartScreen** - 啟用或停用潛在詐騙網站的警告。
-   **JavaScript** - 讓瀏覽器可執行指令碼，例如 Java 指令碼。
-   **快顯** - 啟用或停用瀏覽器的快顯封鎖程式。
-   **傳送不追蹤標頭** - 在 Internet Explorer 中傳送「不追蹤」標頭給造訪的網站。
-   **外掛程式** - 讓使用者可將外掛程式加入 Internet Explorer 中。
-   **內部網路網站中的單一文字** - 可以使用單一文字來將 Internet Explorer 導向某個網站，例如 Bing。
-   **自動偵測內部網路網站**協助在 Internet Explorer 中設定內部網站的安全性。
-   **網際網路安全性層級** - 設定網際網路網站的 Internet Explorer 安全性等級。
-   **內部網路安全性層級** - 設定網際網路網站的 Internet Explorer 安全性等級。
-   **信任網站安全性層級** - 設定信任的網站區域的安全性等級。
-   **信任網站安全性層級** - 設定信任的網站區域的安全性等級。
-   **企業模式功能表存取** - 讓使用者可從 Internet Explorer 存取企業模式功能表選項。
如果您選取此設定，您也可以指定 [記錄報告位置]，其中包含報告的 URL，顯示使用者已開啟企業模式存取的網站。
-   **企業模式網站清單位置** - 指定啟用企業模式時，將使用企業模式的網站清單位置。

## <a name="cellular"></a>行動電話通訊
-   **數據漫遊** - 讓裝置可在行動電話通訊網路上時進行數據漫遊。

## <a name="cloud-and-storage"></a>雲端與儲存體
-   **工作資料夾 URL** - 此設定會設定工作資料夾的 URL，允許跨裝置同步處理文件。
-   **在沒有 Microsoft 帳戶的情況下存取 Windows Mail 應用程式** - 讓您可在沒有 Microsoft 帳戶的情況下，存取 Windows Mail 應用程式。    

---
title: Microsoft Intune 中的 macOS 裝置功能設定 - Azure | Microsoft Docs
description: 請在 Microsoft Intune 中查看針對 AirPrint 設定 macOS 裝置的設定，並自訂 [登入] 視窗以顯示或隱藏電源按鈕。 請參閱取得適用於您網路中 AirPrint 伺服器的 IP 位址、路徑及連接埠設定步驟。 在裝置組態設定檔中使用這些設定，可設定 macOS 裝置功能。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 08/05/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: ''
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 63f2832dd321425efe8092f1bb12dd0d479ef71b
ms.sourcegitcommit: b78793ccbef2a644a759ca3110ea73e7ed6ceb8f
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 08/16/2019
ms.locfileid: "69549928"
---
# <a name="macos-device-feature-settings-in-intune"></a>Intune 中的 macOS 裝置功能設定

Intune 包含一些內建設定，用來自訂您 macOS 裝置上的功能。 本文會列出這些設定，並說明每個設定的用途。 同時也會列出使用終端機應用程式 (模擬器) 來取得 AirPrint 印表機之 IP 位址、路徑和連接埠的步驟。

本功能適用於：

- macOS

作為行動裝置管理 (MDM) 解決方案的一部分，請使用這些設定來建立橫幅、選擇使用者的登入方式、新增 AirPrint 伺服器等。

這些設定會新增至 Intune 裝置組態設定檔，然後指派或部署到您的 macOS 裝置。

## <a name="before-you-begin"></a>開始之前

[建立 macOS 裝置組態設定檔](device-features-configure.md)。

## <a name="airprint"></a>AirPrint

- **IP 位址**：輸入印表機的 IPv4 或 IPv6 位址。 如果您使用主機名稱來識別印表機，可以透過在終端機應用程式中偵測該印表機來取得 IP 位址。 本文中的[取得 IP 位址和路徑](#get-the-ip-address-and-path)會提供更多詳細資料。
- **路徑**：輸入印表機的路徑。 您網路上印表機的路徑通常是 `ipp/print`。 本文中的[取得 IP 位址和路徑](#get-the-ip-address-and-path)會提供更多詳細資料。
- **連接埠** (iOS 11.0 和更新版本)：輸入 AirPrint 目的地的接聽連接埠。 如果將此屬性留白，AirPrint 就會使用預設連接埠。
- **TLS** (iOS 11.0 和更新版本)：選取 [啟用]  以保護 AirPrint 與傳輸層安全性 (TLS) 的連線。

**新增** AirPrint 伺服器。 您可以新增許多 AirPrint 伺服器。

- **匯入** (選擇性)：您也可以 [匯入]  包括 AirPrint 印表機清單的逗號分隔檔 (.csv)。 此外，當您於 Intune 中新增 AirPrint 印表機之後，也可以**匯出**此清單。

選取 [確定]  儲存設定。

### <a name="get-the-ip-address-and-path"></a>取得 IP 位址和路徑

若要新增 AirPrinter 伺服器，您需要有印表機的 IP 位址、資源路徑及連接埠。 下列步驟說明如何取得此資訊。

1. 在連線到與 AirPrint 印表機相同之區域網路 (子網路) 的 Mac 上，開啟 [終端機]  (從 **/Applications/Utilities**)。
2. 在 [終端機] 應用程式中，輸入 `ippfind`，然後選取 Enter 鍵。

    記下印表機資訊。 例如，可能會傳回類似 `ipp://myprinter.local.:631/ipp/port1` 的內容。 第一個部分是印表機的名稱。 最後一個部分 (`ipp/port1`) 是資源路徑。

3. 在 [終端機] 中，輸入 `ping myprinter.local`，然後選取 Enter 鍵。

   記下 IP 位址。 例如，可能會傳回類似 `PING myprinter.local (10.50.25.21)` 的內容。

4. 使用 IP 位址和資源路徑值。 在此範例中，IP 位址是 `10.50.25.21`，而資源路徑則是 `/ipp/port1`。

## <a name="login-items"></a>登入專案

- 檔案 **、資料夾和自訂應用程式**:**新增**您想要在使用者登入裝置時開啟的檔案、資料夾、自訂應用程式或系統應用程式的路徑。 系統應用程式, 或為您的組織建立或自訂的應用`Applications`程式通常在資料夾中, 其`/Applications/AppName.app`路徑類似于。 

  您可以新增許多檔案、資料夾和應用程式。 例如，輸入：  
  
  - `/Applications/Calculator.app`
  - `/Applications`
  - `/Applications/Microsoft Office/root/Office16/winword.exe`
  - `/Users/UserName/music/itunes.app`
  
  新增任何應用程式、資料夾或檔案時, 請務必輸入正確的路徑。 並非所有專案都在`Applications`資料夾中。 如果使用者將專案從某個位置移到另一個位置, 則路徑會變更。 當使用者登入時, 將不會開啟此移動的專案。

## <a name="login-window"></a>登入視窗

### <a name="window-layout"></a>視窗版面配置

- **在功能表列中顯示其他資訊**：選取功能表列上的時間區域時，[允許]  顯示主機名稱和 macOS 版本。 [未設定]  (預設) 不會在功能表列上顯示這項資訊。
- **橫幅**：輸入在裝置登入畫面中顯示的訊息。 例如，輸入您的組織資訊、歡迎訊息、失物招領資訊等。
- **選擇登入格式**：選擇使用者登入裝置的方式。 選項包括：
  - **提示輸入使用者名稱及密碼** (預設)：要求使用者輸入使用者名稱和密碼。
  - **列出全部使用者，提示輸入密碼**：要求使用者從使用者清單中選取其使用者名稱，然後輸入其密碼。 同時設定：

    - **本機使用者**：[隱藏]  不會在使用者清單中顯示本機使用者帳戶，其中可能包含標準和系統管理員帳戶。 只會顯示網路和系統使用者帳戶。 [未設定]  (預設) 會在使用者清單中顯示本機使用者帳戶。
    - **行動帳戶**：[隱藏]  不會在使用者清單中顯示行動帳戶。 [未設定]  (預設) 會在使用者清單中顯示行動帳戶。 有些行動帳戶可能會顯示為網路使用者。
    - **網路使用者**：選取 [顯示]  在使用者清單中列出網路使用者。 [未設定]  (預設) 不會在使用者清單中顯示網路使用者帳戶。
    - **管理使用者**：[隱藏]  不會在使用者清單中顯示系統管理員使用者帳戶。 [未設定]  (預設) 會在使用者清單中顯示系統管理員使用者帳戶。
    - **其他使用者**：選取 [顯示]  在使用者清單中列出 [其他...]  使用者。 [未設定]  (預設) 不會在使用者清單中顯示其他使用者帳戶。

### <a name="login-screen-power-settings"></a>登入畫面電源設定

- **[關機] 按鈕**：[隱藏]  不會在登入畫面上顯示 [關機] 按鈕。 [未設定]  (預設) 會顯示 [關機] 按鈕。
- **[重新開機] 按鈕**：[隱藏]  不會在登入畫面上顯示 [重新開機] 按鈕。 [未設定]  (預設) 會顯示 [重新開機] 按鈕。
- **[睡眠] 按鈕**：[隱藏]  不會在登入畫面上顯示 [睡眠] 按鈕。 [未設定]  (預設) 會顯示 [睡眠] 按鈕。

### <a name="other"></a>其他

- **讓使用者無法從 [主控台] 登入**：[停用]  會隱藏用來登入的 macOS 命令列。 如果是一般使用者，請 [停用]  這項設定。 [未設定]  (預設) 可讓進階使用者使用 macOS 命令列登入。 為了進入主控台模式，使用者要在 [使用者名稱] 欄位中輸入 `>console`，然後必須在主控台視窗中進行驗證。

### <a name="apple-menu"></a>Apple 功能表

使用者登入裝置之後，下列設定會影響它們可執行的功能。

- **停用 [關機]** ：[停用]  可防止使用者在登入之後選取 [關機]  選項。 [未設定]  (預設) 可讓使用者在裝置上選取 [關機]  功能表項目。
- **停用 [重新開機]** ：[停用]  可防止使用者在登入之後選取 [重新開機]  選項。 [未設定]  (預設) 可讓使用者在裝置上選取 [重新開機]  功能表項目。
- **停用 [關閉電源]** ：[停用]  可防止使用者在登入之後選取 [關閉電源]  選項。 [未設定]  (預設) 可讓使用者在裝置上選取 [關閉電源]  功能表項目。
- **停用 [登出]** (macOS 10.13 和更新版本)：[停用]  可防止使用者在登入之後選取 [登出]  選項。 [未設定]  (預設) 可讓使用者在裝置上選取 [登出]  功能表項目。
- **停用 [鎖定畫面]** (macOS 10.13 和更新版本)：[停用]  可防止使用者在登入之後選取 [鎖定畫面]  選項。 [未設定]  (預設) 可讓使用者在裝置上選取 [鎖定畫面]  功能表項目。

選取 [確定]  儲存設定。

## <a name="next-steps"></a>後續步驟

- 檢視 [iOS](ios-device-features-settings.md) 裝置的所有設定。
- [指派此設定檔](device-profile-assign.md)給您的群組，並[監視其狀態](device-profile-monitor.md)。

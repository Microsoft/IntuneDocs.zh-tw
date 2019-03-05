---
title: Microsoft Intune 中的 macOS 裝置功能設定 - Azure | Microsoft Docs
description: 請參閱在 Microsoft Intune 中設定適用於 AirPrint 之 macOS 裝置的所有設定。 另請參閱取得適用於您網路中 AirPrint 伺服器之 IP 位址、路徑和連接埠設定的步驟。 在裝置組態設定檔中使用這些設定，將 macOS 裝置設定為使用您網路中的 AirPrint 伺服器。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/05/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: ''
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e0707226412d314ac1d44ba339b4c9151b394919
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/02/2019
ms.locfileid: "57233894"
---
# <a name="macos-device-feature-settings-in-intune"></a>Intune 中的 macOS 裝置功能設定

Intune 包含一些內建設定，讓 macOS 使用者能夠列印到您網路中的 AirPrint 印表機。 本文會列出這些設定，並說明每個設定的用途。 同時也會列出使用終端機應用程式 (模擬器) 來取得 AirPrint 印表機之 IP 位址、路徑和連接埠的步驟。

## <a name="before-you-begin"></a>開始之前

[建立 macOS 裝置組態設定檔](device-features-configure.md)。

## <a name="airprint-settings"></a>AirPrint 設定

1. 在 [設定] 中，選取 [AirPrint]。 輸入下列 AirPrint 伺服器屬性：

    - **IP 位址**：輸入印表機的 IPv4 或 IPv6 位址。 如果您使用主機名稱來識別印表機，您可以透過在終端機應用程式中偵測該印表機來取得 IP 位址。 [取得 IP 位址和路徑](#get-the-ip-address-and-path) (在本文中) 會提供更多詳細資料。
    - **路徑**：輸入印表機的路徑。 您網路上印表機的路徑通常是 `ipp/print`。 [取得 IP 位址和路徑](#get-the-ip-address-and-path) (在本文中) 會提供更多詳細資料。
    - **連接埠**：輸入 AirPrint 目的地的接聽連接埠。 如果將此屬性留白，AirPrint 就會使用預設連接埠。 適用於 iOS 11.0 和更新版本。
    - **TLS**：選擇 [啟用] 以保護 AirPrint 與傳輸層安全性 (TLS) 的連線。 適用於 iOS 11.0 和更新版本。

2. 選取 [新增]。 隨即會將 AirPrint 伺服器新增至清單。 您可以新增許多 AirPrint 伺服器。

    您也可以**匯入**包括 AirPrint 印表機清單的逗號分隔檔 (.csv)。 此外，當您於 Intune 中新增 AirPrint 印表機之後，也可以**匯出**此清單。

3. 完成時，請選取 [確定] 以儲存您的清單。

## <a name="get-the-ip-address-and-path"></a>取得 IP 位址和路徑

若要新增 AirPrinter 伺服器，您需要有印表機的 IP 位址、資源路徑及連接埠。 下列步驟說明如何取得此資訊。

1. 在連線到與 AirPrint 印表機相同之區域網路 (子網路) 的 Mac 上，開啟 [終端機] (從 **/Applications/Utilities**)。
2. 在 [終端機] 應用程式中，輸入 `ippfind`，然後選取 Enter 鍵。

    記下印表機資訊。 例如，可能會傳回類似 `ipp://myprinter.local.:631/ipp/port1` 的內容。 第一個部分是印表機的名稱。 最後一個部分 (`ipp/port1`) 是資源路徑。

3. 在 [終端機] 中，輸入 `ping myprinter.local`，然後選取 Enter 鍵。

   記下 IP 位址。 例如，可能會傳回類似 `PING myprinter.local (10.50.25.21)` 的內容。

4. 使用 IP 位址和資源路徑值。 在此範例中，IP 位址是 `10.50.25.21`，而資源路徑則是 `/ipp/port1`。

## <a name="next-steps"></a>後續步驟

- 檢視 [iOS](ios-device-features-settings.md) 裝置的所有設定。
- 將此設定檔指派給群組；請參閱[指派裝置設定檔](device-profile-assign.md)。

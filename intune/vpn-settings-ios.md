---
title: Microsoft Intune 中 iOS 裝置的 VPN 設定- Azure | Microsoft Docs
description: 檢視 Microsoft Intune 中執行 iOS 之裝置上的可用虛擬私人網路 (VPN) 組態設定，包括基底設定中的連線詳細資料、驗證方法和分割通道；含有識別碼和機碼值組的自訂 VPN 設定；包含 Safari URL 的個別應用程式 VPN 設定和含 SSID 或 DNS 搜尋網域的隨選 VPN；以及要包含設定指令碼、IP 或 FQDN 位址和 TCP 連接埠的 Proxy 設定。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 4/17/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 374c3937d04fd546c17d6f147609f448875dddba
ms.sourcegitcommit: 2773f388f50654366197a95a6838306f70fc18b8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
---
# <a name="configure-vpn-settings-in-microsoft-intune-for-devices-running-ios"></a>設定 Microsoft Intune 中執行 iOS 之裝置的 VPN 設定

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

本文說明可用於設定執行 iOS 之裝置上 VPN 連線的 Intune 設定。

下列清單中的值並非全部都能設定，須取決於您選擇的設定。

## <a name="base-vpn-settings"></a>基本 VPN 設定

- **連線名稱**：輸入此連線的名稱。 使用者會在瀏覽其裝置是否有可用的 VPN 連線清單時，看到此名稱。
- **IP 位址或 FQDN**輸入裝置所連線 VPN 伺服器的 IP 位址或完整網域名稱 (FQDN)。 例如，輸入 **192.168.1.1** 或 **vpn.contoso.com**。
- **驗證方法**從下列方式中選擇裝置向 VPN 伺服器進行驗證的方式︰
  - **憑證**：在 [驗證憑證] 底下，選擇現有的 SCEP 或 PKCS 憑證設定檔來驗證連線。 [設定憑證](certificates-configure.md)提供了一些有關憑證設定檔的指引。
  - **使用者名稱及密碼**：使用者必須輸入使用者名稱及密碼，才能登入 VPN 伺服器。
- **連線類型**：從下列廠商清單中選取 VPN 連線類型︰
  - **Check Point Capsule VPN**
  - **Cisco AnyConnect**
  - **Cisco Legacy AnyConnect**
  - **SonicWall Mobile Connect**
  - **F5 Edge Client**
  - **Pulse Secure**
  - **Cisco (IPSec)**
  - **Citrix**
  - **自訂 VPN**

    > [!NOTE]
    > - **Cisco Legacy AnyConnect VPN** 設定檔適用於 [Cisco Legacy AnyConnect](https://itunes.apple.com/app/cisco-legacy-anyconnect/id392790924) 應用程式版本 4.0.5x 及更舊版本
    > - **Cisco AnyConnect VPN** 設定檔適用於 [Cisco AnyConnect](https://itunes.apple.com/app/cisco-anyconnect/id1135064690) 應用程式版本 4.0.7x 及更新版本

- **分割通道**：**啟用**或**停用**以讓裝置依據流量決定所要使用的連線。 例如，旅館中的使用者使用 VPN 連線存取工作檔案，但使用旅館的標準網路進行一般的網頁瀏覽。

## <a name="custom-vpn-settings"></a>自訂 VPN 設定

如果您已選取 [自訂 VPN] 作為連線類型，請一併設定下列設定︰

- **VPN 識別碼**：您要使用之 VPN 應用程式的識別碼，由您的 VPN 提供者所提供。
- **輸入自訂 VPN 屬性的機碼值組**：新增或匯入 [機碼] 和 [值] 來自訂您的 VPN 連線。 同樣地，這些值通常由 VPN 提供者提供。

## <a name="apps-per-app-vpn-settings"></a>應用程式 (個別應用程式 VPN) 設定

- **個別應用程式的 VPN**：若要使用可在從 Safari 瀏覽器瀏覽 URL 時啟用 VPN 連線功能的 URL，請啟用此選項。 若要設定個別應用程式 VPN，您必須在選取 [憑證] 作為基底 VPN 設定中的驗證方法。
  - **觸發此 VPN 的 Safari URL**選取即可新增一或多個網站 URL。 前往這些 URL 時，會啟用 VPN 連線。

- **隨選 VPN**：設定可控制 VPN 連線起始時機的條件式規則。 例如，建立一個只在裝置未連線到公司 Wi-Fi 網路時才使用 VPN 連線的條件。 或者，建立一個如果裝置無法存取所指定 DNS 搜尋網域便不起始 VPN 連線的條件。

  - **SSID 或 DNS 搜尋網域**選取此條件是要使用無線網路 **SSID** 還是 **DNS 搜尋網域**。 選擇 [新增] 即可設定一或多個 SSID 或搜尋網域。
  - **URL 字串探查**：選用。 請輸入規則用來作為測試的 URL。 如果安裝此設定檔的裝置無須重新導向就能存取此 URL，便會起始 VPN 連線，而裝置便可連線到目標 URL。 使用者不會看到 URL 字串探查網站。 URL 字串探查的其中一例就是稽核網頁伺服器的位址，此伺服器會在連線 VPN 之前先檢查裝置合規性。 另一種可能，是 URL 會先測試 VPN 連線到網站的能力，再將裝置透過 VPN 連線到目標 URL。
  - **網域動作**：請選擇下列其中一個項目︰
    - 連線 (若需要)
    - 一律不連線
  - **動作**：請選擇下列其中一個項目︰
    - 連線
    - 評估連線
    - 忽略
    - 中斷連線

## <a name="proxy-settings"></a>Proxy 設定

- **自動設定指令碼**：使用檔案設定 Proxy 伺服器。 輸入包含設定檔的 [Proxy 伺服器 URL] (例如 **http://proxy.contoso.com**)。
- **位址**：輸入 Proxy 伺服器的完整主機名稱 IP 位址。
- **連接埠號碼**：輸入與 Proxy 伺服器相關聯的連接埠號碼。

## <a name="next-step"></a>後續步驟
[在 Intune 中建立 VPN 設定檔](vpn-settings-configure.md)
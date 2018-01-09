---
title: "iOS 裝置的 Intune VPN 設定"
titlesuffix: Azure portal
description: "了解可用於設定 iOS 裝置上 VPN 連線的 Intune 設定。"
keywords: 
author: vhorne
ms.author: victorh
manager: angrobe
ms.date: 12/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1447c123-ea33-4ea0-aab4-69577cdb8d00
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: fe6878601f84ccf6c7296a039060b4049a17e22d
ms.sourcegitcommit: a3a744ea55f38a360ca9f788c77a5b3018d1add5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/30/2017
---
# <a name="vpn-settings-for-ios-devices-in-microsoft-intune"></a>Microsoft Intune 中 iOS 裝置的 VPN 設定

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

下列清單中的值並非全部都能設定，須取決於您選擇的設定。

## <a name="base-vpn-settings"></a>基本 VPN 設定


**連線名稱** - 輸入此連線的名稱。 終端使用者瀏覽其裝置尋找可用 VPN 連線的清單時，使用者會看到此名稱。
- **IP 位或 FQDN** - 提供裝置所連線之 VPN 伺服器的 IP 位址或完整網域名稱。 範例：**192.168.1.1**、**vpn.contoso.com**。
- **驗證方法** - 從下列方式中選擇裝置對 VPN 伺服器的驗證方式︰
    - **憑證** - 從 [驗證憑證] 下選擇先前建立用於驗證連線的 SCEP 或 PKCS 憑證設定檔。 如需憑證設定檔的詳細資訊，請參閱[如何設定憑證](certificates-configure.md)。
    - **使用者名稱與密碼** - 使用者必須提供使用者名稱及密碼才能登入 VPN 伺服器。
- **連線類型** - 從下列廠商清單中選取 VPN 連線類型︰
    - **Check Point Capsule VPN**
    - **Cisco AnyConnect**
    - **Dell SonicWALL Mobile Connect**
    - **F5 Edge Client**
    - **Pulse Secure**
    - **Cisco (IPSec)**
    - **Citrix**
    - **自訂 VPN**
- **分割通道**  -  **啟用**或**停用**此選項可讓裝置依據流量決定所要使用的連線。 例如，旅館中的使用者使用 VPN 連線存取工作檔案，但使用旅館的標準網路進行一般的網頁瀏覽。


## <a name="custom-vpn-settings"></a>自訂 VPN 設定

若選取 [自訂 VPN] 作為連線類型，請進一步設定如下︰

- **VPN 識別碼**：這是您 VPN 提供者提供您使用之 VPN 應用程式的識別碼。
- **為自訂 VPN 屬性輸入索引鍵/值組**：您可以新增或匯入**索引鍵**和**值**來自訂您的 VPN 連線。 同樣地，這些值通常由 VPN 提供者提供。

## <a name="apps-per-app-vpn-settings"></a>應用程式 (個別應用程式 VPN) 設定

- **個別應用程式 VPN** - 如果希望從 Safari 瀏覽器連入 URL 時能夠使用 VPN 連線，可啟用此選項。 若要如此設定，必須選取**憑證**作為基本 VPN 設定中的驗證方法。
- **使用 Safari 瀏覽器時啟用的 VPN 連線 URL** - 按一下 [新增]，以新增一或多個網站 URL。 前往這些 URL 時，會啟用 VPN 連線。

- **依需求指定的規則** - 這可讓您設定條件式規則，控制初始化 VPN 連線的時機。 例如，您可以建立條件，在裝置未連線到您公司任何一個 Wi-Fi 網路時才使用 VPN 連線。 您也可以建立條件，在裝置無法存取您指定的 DNS 搜尋網域時不啟動 VPN 連線。

    - **SSID 或 DNS 搜尋網域** - 選取此條件要使用無線網路 **SSID** 還是 **DNS 搜尋網域**。 選擇 [新增] 設定一或多個 SSID 或搜尋網域。
    - **URL 字串探查** - (非必要) 提供規則用於測試的 URL。 如果此設定檔的安裝裝置無須重新導向就能存取此 URL，便會起始 VPN 連線讓裝置連線到目標 URL。 使用者將不會看到 URL 字串探查網站。 URL 字串探查的範例，是會在連線 VPN 之前先檢查裝置相容性的稽核網頁伺服器位址。 另一種可能，是 URL 會先測試 VPN 連線到網站的能力，再將裝置透過 VPN 連線到目標 URL。
    - **網域動作** - 請選擇下列其中一個項目︰
        - 連線 (若需要) - 
        - 一律不連線 - 
    - **動作** - 請選擇下列其中一個項目︰
        - 連線 - 
        - 評估連線 - 
        - 忽略 - 
        - 中斷連線 - 


## <a name="proxy-settings"></a>Proxy 設定

- **自動設定指令碼** - 使用檔案設定 Proxy 伺服器。 輸入包含設定檔的 **Proxy 伺服器 URL** (例如**http://proxy.contoso.com**)。
- **位址** - 輸入 proxy 伺服器位址 (例如 IP 位址)。
- **連接埠號碼** - 輸入與 Proxy 伺服器相關聯的連接埠號碼。
---
title: macOS 裝置的 Microsoft Intune VPN 設定
titlesuffix: ''
description: 了解可用於設定 macOS 裝置上 VPN 連線的 Intune 設定。
keywords: ''
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 3/6/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: a59d17c9497d5f7d0fbc3bcdf5f1e232115f643a
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="configure-vpn-settings-in-microsoft-intune-for-devices-running-macos"></a>設定 Microsoft Intune 中執行 macOS 之裝置的 VPN 設定

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

本文說明可用於設定執行 macOS 之裝置上 VPN 連線的 Intune 設定。

下列清單中的值並非全部都能設定，須取決於您選擇的設定。

## <a name="base-vpn-settings"></a>基本 VPN 設定

**連線名稱** - 輸入此連線的名稱。 終端使用者瀏覽其裝置的可用 VPN 連線清單時，使用者會看到此名稱。
- **IP 位址或 FQDN** - 提供裝置所連線之 VPN 伺服器的 IP 位址或完整網域名稱。 範例：**192.168.1.1**、**vpn.contoso.com**。
- **驗證方法** - 從下列方式中選擇裝置對 VPN 伺服器的驗證方式︰
    - **憑證** - 從 [驗證憑證] 下選擇先前建立用於驗證連線的 SCEP 或 PKCS 憑證設定檔。 如需憑證設定檔的詳細資訊，請參閱[如何設定憑證](certificates-configure.md)。
    - **使用者名稱與密碼** - 使用者必須提供使用者名稱及密碼才能登入 VPN 伺服器。
- **連線類型** - 從下列廠商清單中選取 VPN 連線類型︰
    - **Check Point Capsule VPN**
    - **Cisco AnyConnect**
    - **SonicWall Mobile Connect**
    - **F5 Edge Client**
    - **Pulse Secure**
    - **自訂 VPN**
- **分割通道** - **啟用**或**停用**此選項可讓裝置依據流量決定所要使用的連線。 例如，旅館中的使用者使用 VPN 連線存取工作檔案，但使用旅館的標準網路進行一般的網頁瀏覽。

<!--- **Per-app VPN** - Select this option if you want to associate this VPN connection with an iOS or macOS app so that the connection will be opened when the app is run. You can associate the VPN profile with an app when you assign the software. For more information, see [How to assign and monitor apps](apps-deploy.md). --->

## <a name="custom-vpn-settings"></a>自訂 VPN 設定

若選取 [自訂 VPN]，請進一步設定如下：

- **VPN 識別碼**：這是您 VPN 提供者提供您使用之 VPN 應用程式的識別碼。
- **為自訂 VPN 屬性輸入索引鍵/值組**：您可以新增或匯入**索引鍵**和**值**來自訂您的 VPN 連線。 同樣地，這些值通常由 VPN 提供者提供。


## <a name="proxy-settings"></a>Proxy 設定

- **自動設定指令碼** - 使用檔案設定 Proxy 伺服器。 輸入包含設定檔的 [Proxy 伺服器 URL] (例如 **http://proxy.contoso.com**)。
- **位址** - 輸入 proxy 伺服器位址 (例如 IP 位址)。
- **連接埠號碼** - 輸入與 Proxy 伺服器相關聯的連接埠號碼。

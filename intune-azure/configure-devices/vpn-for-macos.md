---
title: "macOS 裝置的 Intune VPN 設定"
titleSuffix: Intune Azure preview
description: "Intune Azure 預覽版︰了解您可用於設定 macOS 裝置之 VPN 連線的 Intune 設定。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/08/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d203a70d-37df-4195-85f7-ad5ef14ac2a1
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 153cce3809e24303b8f88a833e2fc7bdd9428a4a
ms.openlocfilehash: 068dcd5209ff1cc2b2799919fe38bdfbf809423a
ms.lasthandoff: 02/18/2017


---

# <a name="vpn-settings-for-macos-devices-in-microsoft-intune"></a>Microsoft Intune 中 macOS 裝置的 VPN 設定

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

下列清單中所列的值並非全部都能設定，須取決於您選擇的設定。

## <a name="base-vpn-settings"></a>**基本 VPN 設定**

**連線名稱** - 輸入此連線的名稱。 當使用者瀏覽其裝置尋找可用 VPN 連線的清單時，使用者會看到此名稱。
- **IP 位或 FQDN** - 提供裝置要連線之 VPN 伺服器的 IP 位址或完整網域名稱。 範例：**192.168.1.1**、**vpn.contoso.com**。
- **驗證方法** - 從下列各方式中選擇裝置對 VPN 伺服器的驗證方式︰
    - **憑證** - 從 [驗證憑證] 下選擇先前建立用於驗證連線的 SCEP 或 PKCS 憑證設定檔。 如需憑證設定檔的詳細資訊，請參閱[如何設定憑證](how-to-configure-certificates.md)。
    - **使用者名稱與密碼** - 使用者必須提供使用者名稱及密碼才能登入 VPN 伺服器。
- **連線類型** - 從下列廠商清單中選取 VPN 連線類型︰
    - **Check Point Capsule VPN**
    - **Cisco AnyConnect**
    - **Dell SonicWALL Mobile Connect**
    - **F5 Edge Client**
    - **Pulse Secure**
    - **自訂 VPN**
- **分割通道**  -  **啟用**或**停用**此選項可讓裝置依據流量決定所要使用的連線。 例如，旅館中的使用者使用 VPN 連線存取工作檔案，但使用旅館的標準網路進行一般的網頁瀏覽。

<!--- **Per-app VPN** - Select this option if you want to associate this VPN connection with an iOS or Mac OS X app so that the connection will be opened when the app is run. You can associate the VPN profile with an app when you deploy the software. For more information, see [How to deploy and monitor apps](/intune-azure/manage-apps/deploy-apps). --->

## <a name="custom-vpn-settings"></a>自訂 VPN 設定

若選取 [自訂 VPN]，請進一步設定如下：

- **VPN 識別碼**：這是您 VPN 提供者提供您使用之 VPN 應用程式的識別碼。
- **為自訂 VPN 屬性輸入索引鍵/值組**：您可以新增或匯入**索引鍵**和**值**來自訂您的 VPN 連線。 同樣地，這些值通常由 VPN 提供者提供。


## <a name="proxy-settings"></a>Proxy 設定

- **自動設定指令碼** - 使用檔案設定 Proxy 伺服器。 輸入包含設定檔的 **Proxy 伺服器 URL** (例如**http://proxy.contoso.com**)。
- **位址** - 輸入 proxy 伺服器位址 (例如 IP 位址)。
- **連接埠號碼** - 輸入與 Proxy 伺服器相關聯的連接埠號碼。


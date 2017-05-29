---
title: "Windows 10 裝置的 Intune VPN 設定"
titleSuffix: Intune Azure preview
description: "Intune Azure Preview︰了解您可用於設定 Windows 10 裝置之 VPN 連線的 Intune 設定。"
keywords: 
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 495e4ed6-b2ef-47cc-a110-13fa9b5f85a6
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 6dd98b176c76e19d6ff261a4dafbabfb9698f787
ms.contentlocale: zh-tw
ms.lasthandoff: 05/23/2017


---

# <a name="vpn-settings-for-windows-10-devices-in-microsoft-intune"></a>Microsoft Intune 中 Windows 10 裝置的 VPN 設定

[!INCLUDE[azure_preview](./includes/azure_preview.md)]

根據您選擇的設定，下列清單中所列的值並非全部都能設定。


## <a name="base-vpn-settings"></a>基本 VPN 設定


- **連線名稱** - 輸入此連線的名稱。 當使用者瀏覽其裝置尋找可用 VPN 連線的清單時，使用者會看到此名稱。
- **伺服器** - 新增裝置要連線的一或多部 VPN 伺服器。
    - **新增**- 開啟 [加入資料列] 刀鋒視窗指定下列資訊︰
        - **描述** - 為伺服器指定描述性名稱，例如 **Contoso VPN 伺服器**。
        - **IP 位或 FQDN** - 提供裝置要連線之 VPN 伺服器的 IP 位址或完整網域名稱。 範例：**192.168.1.1**、**vpn.contoso.com**。
        - **預設伺服器** - 啟用此伺服器作為裝置所要連線的預設伺服器。 您只可設定一部預設伺服器。
    - **匯入** - 瀏覽至內含以逗點分隔之伺服器清單 (格式為：描述、IP 位址或 FQDN、預設伺服器) 的檔案。 選擇 [確定]，以匯入這些項目成為**伺服器**清單。
    - **匯出** - 將伺服器清單匯出成逗點分隔值 (csv) 檔案。

**連線類型** - 從下列廠商清單中選取 VPN 連線類型︰
- **Pulse Secure**
- **F5 Edge Client**
- **Dell SonicWALL Mobile Connect**
- **Check Point Capsule VPN**
- **自動**
- **IKEv2**
- **L2TP**
- **PPTP**

**登入群組或網域** (僅限 Dell SonicWALL Mobile Connect) - 指定登入群組或您要連線之網域的名稱。

**自訂 XML**/**EAP XML** - 指定任何可用於設定 VPN 連線的自訂 XML 命令。

**Pulse Secure 的範例：**

```
    <pulse-schema><isSingleSignOnCredential>true</isSingleSignOnCredential></pulse-schema>
```

**CheckPoint Mobile VPN 的範例：**

```
    <CheckPointVPN port="443" name="CheckPointSelfhost" sso="true" debug="3" />
```

**ell SonicWALL Mobile Connect 的範例：**

```
    <MobileConnect><Compression>false</Compression><debugLogging>True</debugLogging><packetCapture>False</packetCapture></MobileConnect>
```

**F5 Edge 用戶端的範例︰**

```
    <f5-vpn-conf><single-sign-on-credential /></f5-vpn-conf>
```

如需如何撰寫自訂 XML 命令的詳細資訊，請參閱相關製造商的 VPN 文件。

**分割通道**  -  **啟用**或**停用**此選項可讓裝置依據流量決定所要使用的連線。 例如，旅館中的使用者使用 VPN 連線存取工作檔案，但使用旅館的標準網路進行一般的網頁瀏覽。
- **此 VPN 連線的分割通道路徑** - 新增第三方 VPN 提供者的選擇性路由。 為每個路由指定目的地首碼及首碼大小。

## <a name="apps-and-traffic-rules"></a>應用程式與流量規則

**限制這些應用程式使用 VPN 連線** - 若只希望您指定的應用程式使用 VPN 連線，可啟用此選項。
**相關聯的應用程式** - 提供會自動使用 VPN 連線的應用程式清單。 應用程式類型會決定應用程式識別碼。 若為通用應用程式，會提供套件系列名稱。 若為傳統型應用程式，會提供應用程式的檔案路徑。

>[!IMPORTANT]
>我們建議您保護所有您為了用於個別應用程式 VPN 設定而編譯的應用程式清單。 如果未經授權的使用者修改您的清單，而您將它匯入到個別應用程式的 VPN 應用程式清單中，則您可能會將 VPN 存取權授權給不應該存取的應用程式。 保護應用程式清單的一種方法是使用存取控制清單 (ACL)。

**此 VPN 連線的網路流量規則** - 選取要為 VPN 連線啟用的通訊協定、本機和遠端連接埠，以及位址範圍。 如果您未建立網路流量規則，則會啟用所有通訊協定、連接埠和位址範圍。 在您建立規則之後，VPN 連線只會使用您在該項規則中所指定的通訊協定、連接埠和位址範圍。


## <a name="conditional-access"></a>條件式存取

**此 VPN 連線的條件式存取** -
**使用其他憑證的單一登入 (SSO)** -
**擴充金鑰使用方法** -
**簽發者雜湊** -

## <a name="dns-settings"></a>DNS 設定

**此 VPN 連線的 DNS 名稱和伺服器** - 選取連線之後 VPN 連線所要使用的 DNS 伺服器。
針對每部伺服器。 指定：
- **DNS 名稱**
- **DNS 伺服器**
- **Proxy**

## <a name="proxy-settings"></a>Proxy 設定

- **自動偵測 Proxy 設定** - 若您的 VPN 伺服器需要 Proxy 伺服器才能連線，請指定您的裝置是否需要自動偵測連線設定。 如需詳細資訊，請參閱 Windows Server 文件。
- **自動設定指令碼** - 使用檔案設定 Proxy 伺服器。 輸入包含設定檔的 **Proxy 伺服器 URL** (例如**http://proxy.contoso.com**)。
- **使用 proxy 伺服器** - 若要手動輸入 Proxy 伺服器設定，可啟用此選項。
    - **位址** - 輸入 proxy 伺服器位址 (例如 IP 位址)。
    - **連接埠號碼** - 輸入與 Proxy 伺服器相關聯的連接埠號碼。
- **本機位址不要使用 Proxy** - 若您的 VPN 伺服器需要 Proxy 伺服器才能連線，但您希望您指定的本機位置不要使用 Proxy 伺服器，可選取此選項。 如需詳細資訊，請參閱 Windows Server 文件。


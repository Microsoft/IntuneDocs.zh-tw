---
title: Windows 8.1 裝置的 Microsoft Intune VPN 設定
titleSuffix: ''
description: 了解可用於設定執行 Windows 8.1 之裝置上 VPN 連線的 Intune 設定。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/6/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 69f347b3e59ca9dfe3f05c9a60dd44c257d485fb
ms.sourcegitcommit: 0dbce0415e53fe963dc7f927ac4b0c06411f199c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2018
ms.locfileid: "52281117"
---
# <a name="configure-vpn-settings-in-microsoft-intune-for-devices-running-windows-81"></a>設定 Microsoft Intune 中執行 Windows 8.1 之裝置的 VPN 設定

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

本文說明可用於設定執行 Windows 8.1 之裝置上 VPN 連線的 Intune 設定。

下列清單中的值並非全部都能設定，須取決於您選擇的設定。

## <a name="base-vpn-settings"></a>基本 VPN 設定


- **將所有設定只套用至 Windows 8.1**：此設定可以在 Intune 傳統入口網站中設定。 在 Azure 入口網站中，此設定無法變更。 若此值設定為 [已設定]，則所有設定將只會套用到 Windows 8.1 裝置。 若設定為 [未設定]，則這些設定也會套用到 Windows 10 裝置。
- **連線名稱** - 輸入此連線的名稱。 使用者瀏覽其裝置的可用 VPN 連線清單時，會看到此名稱。
- **伺服器** - 新增裝置要連線的一或多部 VPN 伺服器。
    - **新增** - 開啟 [新增資料列] 頁面指定下列資訊︰
        - **描述** - 為伺服器指定描述性名稱，例如 **Contoso VPN 伺服器**。
        - **IP 位址或 FQDN** - 提供裝置所連線之 VPN 伺服器的 IP 位址或完整網域名稱。 範例：**192.168.1.1**、**vpn.contoso.com**。
        - **預設伺服器** - 啟用此伺服器作為裝置所要連線的預設伺服器。 您只可設定一部預設伺服器。
    - **匯入** - 瀏覽至內含以逗點分隔之伺服器清單 (格式為：描述、IP 位址或 FQDN、預設伺服器) 的檔案。 選擇 [確定]，以匯入這些項目成為**伺服器**清單。
    - **匯出** - 將伺服器清單匯出成逗點分隔值 (csv) 檔案。

- **連線類型** - 從下列廠商清單中選取 VPN 連線類型︰
- **Check Point Capsule VPN**
- **SonicWall Mobile Connect**
- **F5 Edge Client**
- **Pulse Secure**

<!--- **Fingerprint** (Check Point Capsule VPN only) - Specify a string (for example, "Contoso Fingerprint Code") that will be used to verify that the VPN server can be trusted. A fingerprint can be sent to the client so it knows to trust any server that presents the same fingerprint when connecting. If the device doesn’t already have the fingerprint, it will prompt the user to trust the VPN server that they are connecting to while showing the fingerprint. (The user manually verifies the fingerprint and chooses **trust** to connect.) --->

- **登入群組或網域** (僅限 SonicWall Mobile Connect) - 指定登入群組或您要連線之網域的名稱。

- **角色** 僅限 Pulse Secure - 指定有權存取此連線之使用者角色的名稱。 使用者角色定義個人設定和選項，以及啟用或停用某些存取功能。

- **領域** (僅限 Pulse Secure) - 指定您要使用的驗證領域名稱。 驗證領域就是 Pulse Secure 連線類型使用的驗證資源群組。


- **自訂 XML** - 指定任何可用於設定 VPN 連線的自訂 XML 命令。

**Pulse Secure 的範例：**

```
    <pulse-schema><isSingleSignOnCredential>true</isSingleSignOnCredential></pulse-schema>
```

**CheckPoint Mobile VPN 的範例：**
```
    <CheckPointVPN port="443" name="CheckPointSelfhost" sso="true" debug="3" />
```

**SonicWall Mobile Connect 的範例：**
```
    <MobileConnect><Compression>false</Compression><debugLogging>True</debugLogging><packetCapture>False</packetCapture></MobileConnect>
```

**F5 Edge 用戶端的範例︰**

```
    <f5-vpn-conf><single-sign-on-credential /></f5-vpn-conf>
```

如需詳細資訊，請參閱相關製造商關於如何撰寫自訂 XML 命令的 VPN 文件。


## <a name="proxy-settings"></a>Proxy 設定

- **自動偵測 Proxy 設定** - 若您的 VPN 伺服器需要 Proxy 伺服器才能連線，請指定您的裝置是否需要自動偵測連線設定。 如需詳細資訊，請參閱 Windows Server 文件。
- **自動設定指令碼** - 使用檔案設定 Proxy 伺服器。 輸入包含設定檔的 [Proxy 伺服器 URL]。 例如，輸入 `http://proxy.contoso.com`。
- **使用 proxy 伺服器** - 若要手動輸入 Proxy 伺服器設定，可啟用此選項。
    - **位址** - 輸入 proxy 伺服器位址 (例如 IP 位址)。
    - **連接埠號碼** - 輸入與 Proxy 伺服器相關聯的連接埠號碼。
- **本機位址不要使用 Proxy** - 若您的 VPN 伺服器需要 Proxy 伺服器才能連線，但您希望您指定的本機位置不要使用 Proxy 伺服器，可選取此選項。 如需詳細資訊，請參閱 Windows Server 文件。

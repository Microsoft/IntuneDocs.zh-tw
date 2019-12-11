---
title: Windows Phone 8.1 裝置的 Microsoft Intune VPN 設定
titleSuffix: ''
description: 了解可用於設定執行 Windows Phone 8.1 之裝置上 VPN 連線的 Intune 設定。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/6/2018
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 69de660e65ed2a0f3b6c9c7e4ce774a6fcde2676
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72506511"
---
# <a name="configure-vpn-settings-in-microsoft-intune-for-devices-running-windows-phone-81"></a>設定 Microsoft Intune 中執行 Windows Phone 8.1 之裝置的 VPN 設定

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

本文說明可用於設定執行 Windows Phone 8.1 之裝置上 VPN 連線的 Intune 設定。


下列清單中的值並非全部都能設定，須取決於您選擇的設定。

## <a name="base-vpn-settings"></a>基本 VPN 設定

- **將所有設定只套用至 Windows Phone 8.1**：此設定可以在 Intune 傳統入口網站中設定。 在 Azure 入口網站中，此設定無法變更。 若此值設定為 [已設定]  ，則所有設定只會套用到 Windows Phone 8.1 裝置。 若設定為 [未設定]  ，則這些設定也會套用於 Windows 10 行動裝置。
- **連線名稱** - 輸入此連線的名稱。 使用者瀏覽其裝置的可用 VPN 連線清單時，會看到此名稱。
- **驗證方法** - 從下列方式中選擇裝置對 VPN 伺服器的驗證方式︰
  - **憑證** - 從 [驗證憑證]  下選擇先前建立用於驗證連線的 SCEP 或 PKCS 憑證設定檔。 如需憑證設定檔的詳細資訊，請參閱[如何設定憑證](../protect/certificates-configure.md)。
  - **使用者名稱與密碼** - 使用者必須提供使用者名稱及密碼才能登入 VPN 伺服器。
- **伺服器** - 新增裝置要連線的一或多部 VPN 伺服器。
  - **新增**- 開啟 [加入資料列]  刀鋒視窗指定下列資訊︰
    - **描述** - 為伺服器指定描述性名稱，例如 **Contoso VPN 伺服器**。
    - **IP 位址或 FQDN** - 提供裝置所連線之 VPN 伺服器的 IP 位址或完整網域名稱。 範例：**192.168.1.1**、**vpn.contoso.com**。
    - **預設伺服器** - 啟用此伺服器作為裝置所要連線的預設伺服器。 您只可設定一部預設伺服器。
  - **匯入** - 瀏覽至內含以逗點分隔之伺服器清單 (格式為：描述、IP 位址或 FQDN、預設伺服器) 的檔案。 選擇 [確定]  ，以匯入這些項目成為**伺服器**清單。
  - **匯出** - 將伺服器清單匯出成逗點分隔值 (csv) 檔案。

- **使用公司 Wi-Fi 網路時不要使用 VPN** - 啟用此選項可指定當裝置連線到公司 Wi-Fi 網路時不要使用 VPN 連線。
- **使用家用 Wi-Fi 網路時不要使用 VPN** - 啟用此選項可指定當裝置連線到家用 Wi-Fi 網路時不要使用 VPN 連線。

- **連線類型** - 從下列廠商清單中選取 VPN 連線類型︰
  - **Check Point Capsule VPN**
  - **SonicWall Mobile Connect**
  - **F5 Edge Client**
  - **Pulse Secure**

- **登入群組或網域** (僅限 SonicWall Mobile Connect) - 指定登入群組或您要連線之網域的名稱。
- **角色** 僅限 Pulse Secure - 指定有權存取此連線之使用者角色的名稱。 使用者角色定義個人設定和選項，以及啟用或停用某些存取功能。
- **領域** (僅限 Pulse Secure) - 指定您要使用的驗證領域名稱。 驗證領域就是 Pulse Secure 連線類型使用的驗證資源群組。

- **DNS 尾碼搜尋清單**  -  **新增**一或多個 DNS 尾碼。 使用簡短名稱連線到網站時，會搜尋您指定的每個 DNS 尾碼。 例如，指定 DNS 尾碼 **domain1.contoso.com** 和 **domain2.contoso.com**，然後瀏覽 URL `http://mywebsite`，就會搜尋 URL `http://mywebsite.domain1.contoso.com` 和 `http://mywebsite.domain2.contoso.com`。

- **自訂 XML** - 指定任何可用於設定 VPN 連線的自訂 XML 命令。

    **Pulse Secure 的範例：**

```xml
    <pulse-schema><isSingleSignOnCredential>true</isSingleSignOnCredential></pulse-schema>
```

**CheckPoint Mobile VPN 的範例：**

```xml
    <CheckPointVPN port="443" name="CheckPointSelfhost" sso="true" debug="3" />
```

**SonicWall Mobile Connect 的範例：**

```xml
<MobileConnect><Compression>false</Compression><debugLogging>True</debugLogging><packetCapture>False</packetCapture></MobileConnect>
```

**F5 Edge 用戶端的範例︰**

```xml
    <f5-vpn-conf><single-sign-on-credential /></f5-vpn-conf>
```

如需如何撰寫自訂 XML 命令的詳細資訊，請參閱相關製造商的 VPN 文件。

- **分割通道** - **啟用**或**停用**此選項可讓裝置依據流量決定所要使用的連線。 例如，旅館中的使用者使用 VPN 連線存取工作檔案，但使用旅館的標準網路進行一般的網頁瀏覽。




## <a name="proxy-settings"></a>Proxy 設定

- **自動偵測 Proxy 設定** - 若您的 VPN 伺服器需要 Proxy 伺服器才能連線，請指定您的裝置是否需要自動偵測連線設定。 如需詳細資訊，請參閱 Windows Server 文件。
- **自動設定指令碼** - 使用檔案設定 Proxy 伺服器。 輸入包含組態設定檔的 [Proxy 伺服器 URL]  (例如 `http://proxy.contoso.com`)。
- **使用 proxy 伺服器** - 若要手動輸入 Proxy 伺服器設定，可啟用此選項。
  - **位址** - 輸入 proxy 伺服器位址 (例如 IP 位址)。
  - **連接埠號碼** - 輸入與 Proxy 伺服器相關聯的連接埠號碼。
- **本機位址不要使用 Proxy** - 若您的 VPN 伺服器需要 Proxy 伺服器才能連線，但您希望您指定的本機位置不要使用 Proxy 伺服器，可選取此選項。 如需詳細資訊，請參閱 Windows Server 文件。

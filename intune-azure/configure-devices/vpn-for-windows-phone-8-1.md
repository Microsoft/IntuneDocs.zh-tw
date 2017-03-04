---
title: "Windows Phone 8.1 裝置的 Intune VPN 設定"
titleSuffix: Intune Azure preview
description: "Intune Azure 預覽版︰了解您可用於設定 Windows Phone 8.1 裝置之 VPN 連線的 Intune 設定。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c1a9053f-02a7-4735-bc0d-fe4573b31ed4
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 153cce3809e24303b8f88a833e2fc7bdd9428a4a
ms.openlocfilehash: 2fe54f4d97c28825f06d40ec47a8a9dc40da2554
ms.lasthandoff: 02/18/2017


---

# <a name="vpn-settings-for-windows-phone-81-devices-in-microsoft-intune"></a>Microsoft Intune 中 Windows Phone 8.1 裝置的 VPN 設定

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

下列清單中所列的值並非全部都能設定，須取決於您選擇的設定。

## <a name="base-vpn-settings"></a>基本 VPN 設定

- **將所有設定套用至 Windows 8.1** - 您可以在傳統 Intune 入口網站中設定此設定。 在 Azure 入口網站中，此設定無法變更。 若此值設定為 [已設定]，則所有設定將只會套用到 Windows Phone 8.1 裝置。 若設定為 [未設定]，則這些設定也會套用到 Windows 10 行動裝置版裝置。
- **連線名稱** - 輸入此連線的名稱。 當使用者瀏覽其裝置尋找可用 VPN 連線的清單時，使用者會看到此名稱。
- **驗證方法** - 從下列各方式中選擇裝置對 VPN 伺服器的驗證方式︰
    - **憑證** - 從 [驗證憑證] 下選擇先前建立用於驗證連線的 SCEP 或 PKCS 憑證設定檔。 如需憑證設定檔的詳細資訊，請參閱[如何設定憑證](how-to-configure-certificates.md)。
    - **使用者名稱與密碼** - 使用者必須提供使用者名稱及密碼才能登入 VPN 伺服器。
- **伺服器** - 新增裝置要連線的一或多部 VPN 伺服器。
    - **新增**- 開啟 [加入資料列] 刀鋒視窗指定下列資訊︰
        - **描述** - 為伺服器指定描述性名稱，例如 **Contoso VPN 伺服器**。
        - **IP 位或 FQDN** - 提供裝置要連線之 VPN 伺服器的 IP 位址或完整網域名稱。 範例：**192.168.1.1**、**vpn.contoso.com**。
        - **預設伺服器** - 啟用此伺服器作為裝置所要連線的預設伺服器。 您只可設定一部預設伺服器。
    - **匯入** - 瀏覽至內含以逗點分隔之伺服器清單 (格式為：描述、IP 位址或 FQDN、預設伺服器) 的檔案。 選擇 [確定]，以匯入這些項目成為**伺服器**清單。
    - **匯出** - 將伺服器清單匯出成逗點分隔值 (csv) 檔案。

- **使用公司 Wi-Fi 網路時不要使用 VPN** - 啟用此選項可指定當裝置連線到公司 Wi-Fi 網路時不要使用 VPN 連線。
- **使用家用 Wi-Fi 網路時不要使用 VPN** - 啟用此選項可指定當裝置連線到家用 Wi-Fi 網路時不要使用 VPN 連線。

- **連線類型** - 從下列廠商清單中選取 VPN 連線類型︰
    - **Check Point Capsule VPN**
    - **Dell SonicWALL Mobile Connect**
    - **F5 Edge Client**
    - **Pulse Secure**

- **登入群組或網域** (僅限 Dell SonicWALL Mobile Connect) - 指定登入群組或您要登入之網域的名稱。
- **角色** 僅限 Pulse Secure - 指定有權存取此連線之使用者角色的名稱。 使用者角色定義個人設定和選項，以及啟用或停用某些存取功能。
- **領域** (僅限 Pulse Secure) - 指定您要使用的驗證領域名稱。 驗證領域就是 Pulse Secure 連線類型使用的驗證資源群組。

- **DNS 尾碼搜尋清單**  -  **新增**一或多個 DNS 尾碼。 使用簡短名稱連線到網站時，將會搜尋您指定的每個 DNS 尾碼。 例如若是指定 DNS 尾碼 **domain1.contoso.com** 及 **domain2.contoso.com**，將會前往 URL **http://mywebsite** 搜尋下列 URL：**http://mywebsite.domain1.contoso.com** 及 **http://mywebsite.domain2.contoso.com**。

- **自訂 XML** - 指定任何可用於設定 VPN 連線的自訂 XML 命令。

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

- **分割通道**  -  **啟用**或**停用**此選項可讓裝置依據流量決定所要使用的連線。 例如，旅館中的使用者使用 VPN 連線存取工作檔案，但使用旅館的標準網路進行一般的網頁瀏覽。




## <a name="proxy-settings"></a>Proxy 設定

- **自動偵測 Proxy 設定** - 若您的 VPN 伺服器需要 Proxy 伺服器才能連線，請指定您的裝置是否需要自動偵測連線設定。 如需詳細資訊，請參閱 Windows Server 文件。
- **自動設定指令碼** - 使用檔案設定 Proxy 伺服器。 輸入包含設定檔的 **Proxy 伺服器 URL** (例如**http://proxy.contoso.com**)。
- **使用 proxy 伺服器** - 若要手動輸入 Proxy 伺服器設定，可啟用此選項。
    - **位址** - 輸入 proxy 伺服器位址 (例如 IP 位址)。
    - **連接埠號碼** - 輸入與 Proxy 伺服器相關聯的連接埠號碼。
- **本機位址不要使用 Proxy** - 若您的 VPN 伺服器需要 Proxy 伺服器才能連線，但您希望您指定的本機位置不要使用 Proxy 伺服器，可選取此選項。 如需詳細資訊，請參閱 Windows Server 文件。


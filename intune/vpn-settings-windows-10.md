---
title: "在 Microsoft Intune - Azure 中檢視 VPN 設定 | Microsoft Docs"
description: "深入了解和閱讀在 Microsoft Intune 中可用的 VPN 設定、用途以及可執行的動作，包括流量規則、條件式存取，以及適用於 Windows 10 裝置與 Windows Holographic for Business 裝置的 DNS 和 Proxy 設定。"
keywords: 
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/8/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.suite: ems
ms.reviewer: tycast
ms.custom: intune-azure
ms.openlocfilehash: 1c1ed2946782f92313aacec05a65a80b2704ddaa
ms.sourcegitcommit: 8a235b7af6ec3932c29a76d0b1aa481d983054bc
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2018
---
# <a name="read-about-the-vpn-settings-in-intune"></a>閱讀在 Intune 中的 VPN 設定

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

您可以使用 Intune 設定 VPN 連線。 本文說明這些設定、流量規則、條件式存取，以及 DNS 和 Proxy 設定。

這些設定適用於：

- 執行 Windows 10 的裝置
- 執行 Windows Holographic for Business 的裝置

並非全部的值都能設定，須取決於您選擇的設定。

## <a name="base-vpn-settings"></a>基本 VPN 設定

- **連線名稱**：輸入此連線的名稱。 終端使用者瀏覽其裝置尋找可用 VPN 連線的清單時，使用者會看到此名稱。
- **伺服器**：新增裝置要連線的一或多部 VPN 伺服器。
  - **新增**：開啟 [新增資料列] 供您輸入下列資訊：
    - **描述**：為伺服器輸入描述性名稱，例如 **Contoso VPN 伺服器**
    - **IP 位址或 FQDN**：輸入裝置所連線之 VPN 伺服器的 IP 位址或完整網域名稱，例如 **192.168.1.1** 或 **vpn.contoso.com**
    - **預設伺服器**：啟用此伺服器作為裝置所要連線的預設伺服器。 只設定一部伺服器為預設。
  - **匯入**：瀏覽至內含伺服器清單、以逗點分隔 (格式為：描述、IP 位址或 FQDN、預設伺服器) 的檔案。 選擇 [確定]，以將這些伺服器匯入**伺服器**清單。
  - **匯出**：將伺服器清單匯出成逗點分隔值 (csv) 檔案

**連線類型**：從下列廠商清單中選取 VPN 連線類型︰

- **自動**
- **Check Point Capsule VPN**
- **Citrix VPN**
- **SonicWALL Mobile Connect**
- **F5 Edge Client**
- **IKEv2**
- **L2TP**
- **PPTP**
- **Pulse Secure**

**登入群組或網域** (僅限 SonicWALL Mobile Connect)：無法在 VPN 設定檔中設定此屬性。 相反地，當以 `username@domain` 或 `DOMAIN\username` 格式輸入使用者名稱和網域時，Mobile Connect 會剖析此值。

**自訂 XML**/**EAP XML**：輸入任何可用於設定 VPN 連線的自訂 XML 命令。

**Pulse Secure 的範例：**

```
<pulse-schema><isSingleSignOnCredential>true</isSingleSignOnCredential></pulse-schema>
```

**CheckPoint Mobile VPN 的範例：**

```
<CheckPointVPN port="443" name="CheckPointSelfhost" sso="true" debug="3" />
```

**SonicWALL Mobile Connect 的範例：**

```
<MobileConnect><Compression>false</Compression><debugLogging>True</debugLogging><packetCapture>False</packetCapture></MobileConnect>
```

**F5 Edge 用戶端的範例︰**

```
<f5-vpn-conf><single-sign-on-credential /></f5-vpn-conf>
```

如需撰寫自訂 XML 命令的詳細資訊，請參閱各製造商的 VPN 文件。

如需建立自訂 EAP XML 的詳細資訊，請參閱 [EAP configuration](https://docs.microsoft.com/windows/client-management/mdm/eap-configuration) (EAP 設定)。

**分割通道**：**啟用**或**停用**以讓裝置依據流量決定所要使用的連線。 例如，旅館中的使用者使用 VPN 連線存取工作檔案，但使用旅館的標準網路進行一般的網頁瀏覽。
- **此 VPN 連線的分割通道路徑**：新增協力廠商 VPN 提供者的選擇性路由。 為每個路由輸入目的地首碼及首碼大小。

## <a name="apps-and-traffic-rules"></a>應用程式與流量規則

**限制這些應用程式的 VPN 連線**：若您只希望某些應用程式使用 VPN 連線，可啟用此設定。
**相關聯的應用程式**：輸入會自動使用 VPN 連線的應用程式清單。 應用程式類型會決定應用程式識別碼。 若為通用 app，請輸入套件系列名稱。 若為傳統型應用程式，請輸入應用程式的檔案路徑。

>[!IMPORTANT]
>我們建議您為所建立的每個應用程式 VPN 保護所有的應用程式清單。 如果未經授權的使用者變更這個清單，而您將其匯入到個別應用程式的 VPN 應用程式清單中，則您可能會將 VPN 存取權授權給不應該存取的應用程式。 保護應用程式清單的方法之一是使用存取控制清單 (ACL)。

**此 VPN 連線的網路流量規則**：選取要為 VPN 連線啟用的通訊協定、本機和遠端連接埠，以及位址範圍。 如果您未建立網路流量規則，則會啟用所有通訊協定、連接埠和位址範圍。 在您建立規則之後，VPN 連線只會使用您在該項規則中所輸入的通訊協定、連接埠和位址範圍。

## <a name="conditional-access"></a>條件式存取

**此 VPN 連線的條件式存取**：從用戶端啟用裝置合規性流程。 啟用時，VPN 用戶端會嘗試與 Azure Active Directory 通訊，以取得要用於驗證的憑證。 VPN 應該設定成使用憑證驗證，而且 VPN 伺服器必須信任 Azure Active Directory 所傳回的伺服器。

**使用其他憑證的單一登入 (SSO)**：針對裝置合規性，使用與 VPN 驗證憑證不同的憑證來進行 Kerberos 驗證。 輸入具有下列設定的憑證：

- **擴充金鑰使用方法**：擴充金鑰使用方法 (EKU) 的名稱
- **物件識別碼**：EKU 的物件識別碼
- **簽發者雜湊**：SSO 憑證的指紋

## <a name="dns-settings"></a>DNS 設定

**此 VPN 連線的 DNS 名稱和伺服器**：選取連線之後 VPN 連線所要使用的 DNS 伺服器。
為每部伺服器輸入：
- **DNS 名稱**
- **DNS 伺服器**
- **Proxy**

## <a name="proxy-settings"></a>Proxy 設定

- **自動偵測 Proxy 設定**：若您的 VPN 伺服器需要 Proxy 伺服器才能連線，請選擇是否需要您的裝置自動偵測連線設定。
- **自動設定指令碼**：使用檔案設定 Proxy 伺服器。 輸入 **Proxy 伺服器 URL**，例如 `http://proxy.contoso.com`，其中包含設定檔。
- **使用 Proxy 伺服器**：啟用此選項以手動輸入 Proxy 伺服器設定。
  - **位址**：輸入 Proxy 伺服器位址 (例如 IP 位址)
  - **連接埠號碼**：輸入與 Proxy 伺服器相關聯的連接埠號碼
- **本機位址不要使用 Proxy**：若您的 VPN 伺服器需要 Proxy 伺服器才能連線，但您希望您輸入的本機位置不要使用 Proxy 伺服器，可選取此設定。

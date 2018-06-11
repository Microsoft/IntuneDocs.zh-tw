---
title: 在 Microsoft Intune 中設定 Windows 10 VPN - Azure | Microsoft Docs
description: 深入了解和閱讀在 Microsoft Intune 中可用的 VPN 設定、用途以及可執行的動作，包括流量規則、條件式存取，以及適用於 Windows 10 裝置與 Windows Holographic for Business 裝置的 DNS 和 Proxy 設定。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 5/16/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.reviewer: tycast
ms.custom: intune-azure
ms.openlocfilehash: 61310f5baa64c43d2e818df6c61a36d232922c1c
ms.sourcegitcommit: 97b9f966f23895495b4c8a685f1397b78cc01d57
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2018
ms.locfileid: "34744732"
---
# <a name="windows-10-vpn-settings-in-intune"></a>Intune 中的 Windows 10 VPN 設定

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

您可以使用 Intune 設定 VPN 連線。 本文說明這些設定、流量規則、條件式存取，以及 DNS 和 Proxy 設定。

這些設定適用於：

- 執行 Windows 10 的裝置
- 執行 Windows Holographic for Business 的裝置

並非全部的值都能設定，須取決於您選擇的設定。

## <a name="base-vpn-settings"></a>基本 VPN 設定

- **連線名稱**：輸入此連線的名稱。 終端使用者瀏覽其裝置的可用 VPN 連線清單時，使用者會看到此名稱。
- **伺服器**：新增裝置要連線的一或多部 VPN 伺服器。 當您新增伺服器時，要輸入下列資訊：
  - **描述**：為伺服器輸入描述性名稱，例如 **Contoso VPN 伺服器**
  - **IP 位址或 FQDN**：輸入裝置所連線之 VPN 伺服器的 IP 位址或完整網域名稱，例如 **192.168.1.1** 或 **vpn.contoso.com**
  - **預設伺服器**：啟用此伺服器作為裝置所要連線的預設伺服器。 只設定一部伺服器為預設。
  - **匯入**：瀏覽至內含伺服器清單、以逗點分隔 (格式為：描述、IP 位址或 FQDN、預設伺服器) 的檔案。 選擇 [確定]，以將這些伺服器匯入**伺服器**清單。
  - **匯出**：將伺服器清單匯出成逗點分隔值 (csv) 檔案

- **連線類型**：從下列廠商清單中選取 VPN 連線類型︰

  - **Pulse Secure**
  - **F5 Edge Client**
  - **SonicWALL Mobile Connect**
  - **Check Point Capsule VPN**
  - **Citrix**
  - **Palo Alto Networks GlobalProtect**
  - **自動**
  - **IKEv2**
  - **L2TP**
  - **PPTP**

  當您選擇 VPN 連線類型時，可能也會要求您進行下列設定：  
    - **Always On**：啟用以在下列狀況發生時自動連線到 VPN 連線： 
      - 使用者登入其裝置
      - 裝置上的網路發生變更
      - 裝置上的螢幕在關閉後恢復開啟 

    - **驗證方法**：選取您要讓 VPN 伺服器驗證使用者的方法。 使用 [憑證] 可提供增強的功能，例如零觸控體驗、隨選 VPN，和個別應用程式的 VPN。
    - **在每次登入時記住認證**：選擇此選項以快取驗證認證。
    - **自訂 XML**：輸入可設定 VPN 連線的任何自訂 XML 命令。
    - **EAP Xml**：輸入可設定 VPN 連線的任何 EAP XML 命令

#### <a name="pulse-secure-example"></a>Pulse Secure 範例

```
<pulse-schema><isSingleSignOnCredential>true</isSingleSignOnCredential></pulse-schema>
```

#### <a name="f5-edge-client-example"></a>F5 Edge Client 範例

```
<f5-vpn-conf><single-sign-on-credential /></f5-vpn-conf>
```

#### <a name="sonicwall-mobile-connect-example"></a>SonicWALL Mobile Connect 範例
**登入群組或網域**：無法在 VPN 設定檔中設定此屬性。 相反地，當以 `username@domain` 或 `DOMAIN\username` 格式輸入使用者名稱和網域時，Mobile Connect 會剖析此值。

範例：

```
<MobileConnect><Compression>false</Compression><debugLogging>True</debugLogging><packetCapture>False</packetCapture></MobileConnect>
```

#### <a name="checkpoint-mobile-vpn-example"></a>CheckPoint Mobile VPN 範例

```
<CheckPointVPN port="443" name="CheckPointSelfhost" sso="true" debug="3" />
```

#### <a name="writing-custom-xml"></a>撰寫自訂 XML
如需撰寫自訂 XML 命令的詳細資訊，請參閱各製造商的 VPN 文件。

如需建立自訂 EAP XML 的詳細資訊，請參閱 [EAP configuration](https://docs.microsoft.com/windows/client-management/mdm/eap-configuration) (EAP 設定)。

## <a name="apps-and-traffic-rules"></a>應用程式與流量規則

- **將 WIP 或應用程式與此 VPN 建立關聯**：若您只希望某些應用程式使用 VPN 連線，可啟用此設定。 選項包括：

  - **將 WIP 與此連線建立關聯**：輸入**此連線的 WIP 網域**
  - **將應用程式與此連線建立關聯**：您可以**限制這些應用程式的 VPN 連線**，然後新增**相關聯的應用程式**。 您輸入的應用程式會自動使用 VPN 連線。 應用程式類型會決定應用程式識別碼。 若為通用 app，請輸入套件系列名稱。 若為傳統型應用程式，請輸入應用程式的檔案路徑。
  >[!IMPORTANT]
  >我們建議您為所建立的每個應用程式 VPN 保護所有的應用程式清單。 如果未經授權的使用者變更這個清單，而您將其匯入到個別應用程式的 VPN 應用程式清單中，則您可能會將 VPN 存取權授權給不應該存取的應用程式。 保護應用程式清單的方法之一是使用存取控制清單 (ACL)。

- **此 VPN 連線的網路流量規則**：選取要為 VPN 連線啟用的通訊協定、本機和遠端連接埠，以及位址範圍。 如果您未建立網路流量規則，則會啟用所有通訊協定、連接埠和位址範圍。 在您建立規則之後，VPN 連線只會使用您在該項規則中所輸入的通訊協定、連接埠和位址範圍。

## <a name="conditional-access"></a>條件式存取

- **此 VPN 連線的條件式存取**：從用戶端啟用裝置合規性流程。 啟用時，VPN 用戶端會嘗試與 Azure Active Directory (AD) 通訊，以取得要用於驗證的憑證。 VPN 應該設定成使用憑證驗證，而且 VPN 伺服器必須信任 Azure AD 所傳回的伺服器。

- **使用其他憑證的單一登入 (SSO)**：針對裝置合規性，使用與 VPN 驗證憑證不同的憑證來進行 Kerberos 驗證。 輸入具有下列設定的憑證：

  - **名稱**：擴充金鑰使用方法 (EKU) 的名稱
  - **物件識別碼**：EKU 的物件識別碼
  - **簽發者雜湊**：SSO 憑證的指紋

## <a name="dns-settings"></a>DNS 設定

**此 VPN 連線的網域和伺服器**：新增要使用之 VPN 的網域和 DNS 伺服器。 您可以選擇連線建立之後，VPN 連線要使用的 DNS 伺服器。 為每部伺服器輸入：
- **網域**
- **DNS 伺服器**
- **Proxy**

## <a name="proxy-settings"></a>Proxy 設定

- **自動設定指令碼**：使用檔案設定 Proxy 伺服器。 輸入 **Proxy 伺服器 URL**，例如 `http://proxy.contoso.com`，其中包含設定檔。
- **位址**：輸入 Proxy 伺服器位址 (例如 IP 位址或 `vpn.contoso.com`)
- **連接埠號碼**：輸入 Proxy 伺服器使用的 TCP 連接埠號碼
- **本機位址不使用 Proxy 伺服器**：如果您不想針對本機位址使用 Proxy 伺服器，則選擇 [啟用]。 這項設定適用於您的 VPN 伺服器需要 Proxy 伺服器進行連線時。

## <a name="split-tunneling"></a>分割通道

- **分割通道**：**啟用**或**停用**以讓裝置依據流量決定所要使用的連線。 例如，旅館中的使用者使用 VPN 連線存取工作檔案，但使用旅館的標準網路進行一般的網頁瀏覽。
- **此 VPN 連線的分割通道路徑**：新增協力廠商 VPN 提供者的選擇性路由。 為每個連線輸入目的地首碼及首碼大小。

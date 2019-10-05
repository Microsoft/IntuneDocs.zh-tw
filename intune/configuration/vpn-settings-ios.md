---
title: 在 Microsoft Intune 中設定 iOS 裝置的 VPN 設定 - Azure | Microsoft Docs
description: 在 Microsoft Intune 中，使用虛擬私人網路 (VPN) 組態設定在執行 iOS 的裝置上新增或建立 VPN 組態設定檔，包括基底設定中的連線詳細資料、驗證方法和分割通道；具有識別碼的自訂 VPN 設定，以及金鑰和值組；包含 Safari URL 的個別應用程式 VPN 設定，與 具有 SSID 或 DNS 搜尋網域的隨選 VPN；以及要包含設定指令碼、IP 或 FQDN 位址和 TCP 連接埠的 Proxy 設定。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/05/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 274b5a8d45f9fb525010e4d225172a6a1ce22275
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2019
ms.locfileid: "71734150"
---
# <a name="add-vpn-settings-on-ios-devices-in-microsoft-intune"></a>在 Microsoft Intune 中設定 iOS 裝置上的 VPN 設定

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Microsoft Intune 包含許多 VPN 設定，可部署到您的 iOS 裝置。 這些設定可用來建立及設定您組織網路的 VPN 連線。 本文說明了這些設定。 其中一些設定僅適用於特定 VPN 用戶端，例如 Citrix、Zscaler 等。

## <a name="before-you-begin"></a>開始之前

[建立裝置組態設定檔](vpn-settings-configure.md)。

> [!NOTE]
> 這些設定適用于所有的註冊類型。 如需註冊類型的詳細資訊，請參閱[iOS 註冊](../enrollment/ios-enroll.md)。

## <a name="connection-type"></a>連線類型

從下列廠商清單中選取 VPN 連線類型︰

- **Check Point Capsule VPN**
- **Cisco Legacy AnyConnect**：適用於 [Cisco Legacy AnyConnect](https://itunes.apple.com/app/cisco-legacy-anyconnect/id392790924) 應用程式 4.0.5x 版及更舊版本。
- **Cisco AnyConnect**：適用於 [Cisco AnyConnect](https://itunes.apple.com/app/cisco-anyconnect/id1135064690) 應用程式 4.0.7x 版及更新版本。
- **SonicWall Mobile Connect**
- **F5 Access Legacy**：適用於 F5 Access 應用程式 2.1 版及更舊版本。
- **F5 Access**：適用於 F5 Access 應用程式 3.0 版及更新版本。
- **Palo Alto Networks GlobalProtect (Legacy)** ：適用於 Palo Alto Networks GlobalProtect 應用程式 4.1 版及更舊版本。
- **Palo Alto Networks GlobalProtect**：適用於 Palo Alto Networks GlobalProtect 應用程式 5.0 版及更新版本。
- **Pulse Secure**
- **Cisco (IPSec)**
- **Citrix VPN**
- **Citrix SSO**
- **Zscaler**：若要使用條件式存取，或允許使用者略過 Zscaler 登入畫面，您必須整合 Zscaler Private Access (ZPA) 與 Azure AD 帳戶。 如需詳細步驟，請參閱 [Zscaler 文件](https://help.zscaler.com/zpa/configuration-example-microsoft-azure-ad)。 
- **Ikev2**： [ikev2 設定](#ikev2-settings)（在本文中）描述屬性。
- **自訂 VPN**

> [!NOTE]
> Cisco、Citrix、F5 和 Palo Alto 已宣告其舊版用戶端在 iOS 12 上無法運作。 您應該盡快移轉到新的應用程式。 如需詳細資訊，請參閱 [Microsoft Intune 支援小組部落格](https://go.microsoft.com/fwlink/?linkid=2013806&clcid=0x409)。

## <a name="base-vpn-settings"></a>基本 VPN 設定

下列清單中所顯示設定取決於您選擇的 VPN 連線類型。  

- **連線名稱**：終端使用者會在瀏覽其裝置是否有可用的 VPN 連線清單時，看到此名稱。
- **自訂網域名稱** (僅限 Zscaler)：在 Zscaler 應用程式的登入欄位中預先填入您的使用者所屬網域。 例如，如果使用者名稱為 `Joe@contoso.net`，則 `contoso.net` 網域會在應用程式開啟時以靜態方式出現在欄位中。 如果您未輸入網域名稱，則會使用 Azure Active Directory (AD) 中 UPN 的網域部分。
- **IP 位址或 FQDN**：裝置連線之 VPN 伺服器的 IP 位址或完整網域名稱 (FQDN)。 例如，輸入 `192.168.1.1` 或 `vpn.contoso.com`。
- **組織的雲端名稱** (僅限 Zscaler)：輸入您組織佈建所在的雲端名稱。 您用來登入 Zscaler 的 URL 具有名稱。  
- **驗證方法**：選擇裝置向 VPN 伺服器進行驗證的方式。 
  - **憑證**：在 [驗證憑證]  底下，選取現有的 SCEP 或 PKCS 憑證設定檔來驗證連線。 [設定憑證](../protect/certificates-configure.md)提供了一些有關憑證設定檔的指引。
  - **使用者名稱及密碼**：使用者必須輸入使用者名稱及密碼，才能登入 VPN 伺服器。  

    > [!NOTE]
    > 如果使用者名稱和密碼用來作為 Cisco IPsec VPN 的驗證方法，它們必須透過自訂的 Apple Configurator 設定檔傳遞 SharedSecret。

- **排除的 URL** (僅限 Zscaler)：連線到 Zscaler VPN 時，所列出的 URL 可從 Zscaler 雲端外部存取。 

- **分割通道**：[啟用]  或 [停用]  ，讓裝置依據流量決定所要使用的連線。 例如，旅館中的使用者使用 VPN 連線存取工作檔案，但使用旅館的標準網路進行一般的網頁瀏覽。

- **VPN 識別碼** (自訂 VPN、Zscaler 與 Citrix)：您要使用之 VPN 應用程式的識別碼，由您的 VPN 提供者提供。
  - **輸入您組織之自訂 VPN 屬性的機碼值組**：新增或匯入 [機碼]  和 [值]  來自訂您的 VPN 連線。 請記住，這些值通常由 VPN 提供者提供。

- **啟用網路存取控制 (NAC)** (Citrix SSO、F5 Access)：當您選擇 [我同意]  時，裝置識別碼會包含在 VPN 設定檔中。 此識別碼可用來向 VPN 驗證以允許或防止網路存取。

  **使用 F5 Access 時**，請務必：

  - 確認您使用的是 F5 BIG-IP 13.1.1.5。 不支援 BIG-IP 14。
  - 針對 NAC 將 BIG-IP 與 Intune 整合。 請參閱 [Overview: Configuring APM for device posture checks with endpoint management systems](https://support.f5.com/kb/en-us/products/big-ip_apm/manuals/product/apm-client-configuration-7-1-6/6.html#guid-0bd12e12-8107-40ec-979d-c44779a8cc89) (概觀：使用端點管理系統設定 APM 以進行裝置狀態檢查) F5 指南。
  - 在 VPN 設定檔中啟用 NAC。

  **搭配 Gateway 使用 Citrix SSO 時**，請務必：

  - 確認您是使用 Citrix Gateway 12.0.59 或更高版本。
  - 確認您的使用者也在其裝置上安裝 Citrix SSO 1.1.6 或更新版本。
  - 針對 NAC 將 Citrix Gateway 與 Intune 整合。 請參閱 [Integrating Microsoft Intune/Enterprise Mobility Suite with NetScaler (LDAP+OTP Scenario)](https://www.citrix.com/content/dam/citrix/en_us/documents/guide/integrating-microsoft-intune-enterprise-mobility-suite-with-netscaler.pdf) (將 Microsoft Intune/Enterprise Mobility Suite 與 NetScaler 整合 (LDAP+OTP 案例)) Citrix 部署指南。
  - 在 VPN 設定檔中啟用 NAC。

  **重要詳細資料**：  

  - 啟用 NAC 時，VPN 連線每隔 24 小時會中斷一次。 VPN 可以立即重新連線。
  - 裝置識別碼是設定檔的一部分，但它不會顯示在 Intune 中。 Microsoft 不會將此識別碼儲存在任何位置，也不會將它共用。

  當 VPN 夥伴支援裝置識別碼時，VPN 用戶端 (例如 Citrix SSO) 可以取得該識別碼。 接著，它可以查詢 Intune 來確認裝置已註冊，以及 VPN 設定檔是否相容。

  - 若要移除此設定，請重新建立設定檔，但不要選取 [我同意]  。 然後，重新指派設定檔。

## <a name="ikev2-settings"></a>IKEv2 設定

當您選擇 [連線**類型**]  > **IKEv2**時，就會套用這些設定。

- **遠端識別碼**：輸入 IKEv2 伺服器的網路 IP 位址、FQDN、USERFQDN 或 ASN1DN。 例如，輸入 `10.0.0.3` 或 `vpn.contoso.com`。 一般來說，您輸入的值與[**連接名稱**](#base-vpn-settings)相同（在本文中）。 但是，它會根據您的 IKEv2 伺服器設定而定。

- **用戶端驗證類型**：選擇 vpn 用戶端向 vpn 驗證的方式。 選項包括：
  - **使用者驗證**（預設值）：向 VPN 驗證使用者認證。
  - **電腦驗證**：向 VPN 驗證裝置認證。

- **驗證方法**：選擇要傳送至伺服器的用戶端認證類型。 選項包括：
  - **憑證**：使用現有的憑證設定檔向 VPN 進行驗證。 請確認此憑證設定檔已指派給使用者或裝置。 否則，VPN 連線將會失敗。
    - **憑證類型**：選取憑證所使用的加密類型。 請確定 VPN 伺服器已設定為接受這種類型的憑證。 選項包括：
      - **RSA** （預設值）
      - **ECDSA256**
      - **ECDSA384**
      - **ECDSA521**

  - 使用者**名稱和密碼**（僅限使用者驗證）：當使用者連接到 VPN 時，系統會提示他們輸入其使用者名稱和密碼。
  - **共用密碼**（僅限電腦驗證）：可讓您輸入要傳送至 VPN 伺服器的共用密碼。
    - **共用密碼**：輸入共用密碼，也稱為預先共用金鑰（PSK）。 請確定值符合 VPN 伺服器上設定的共用密碼。

- **伺服器憑證簽發者一般名稱**：允許 vpn 伺服器向 vpn 用戶端進行驗證。 輸入在裝置上傳送給 VPN 用戶端的 VPN 伺服器證書的憑證簽發者一般名稱（CN）。 請確定 CN 值符合 VPN 伺服器上的設定。 否則，VPN 連線將會失敗。
- **伺服器憑證一般名稱**：輸入憑證本身的 CN。 如果保留空白，則會使用遠端識別碼值。

- 不正確**對等偵測速率**：選擇 vpn 用戶端檢查 vpn 通道是否作用中的頻率。 選項包括：
  - [**未設定**]：使用 iOS 系統預設值，這可能與選擇 [**中**] 相同。
  - **無**：停用不正確對等偵測。
  - **低**：每隔30分鐘傳送一則 keepalive 訊息。
  - **中**（預設值）：每10分鐘傳送一則 keepalive 訊息。
  - **高**：每60秒傳送一則 keepalive 訊息。

- **最小 tls 版本範圍**：輸入要使用的最低 tls 版本。 輸入 `1.0`、`1.1` 或 `1.2`。 如果保留空白，則會使用 `1.0` 的預設值。
- **Tls 版本範圍上限**：輸入要使用的最大 tls 版本。 輸入 `1.0`、`1.1` 或 `1.2`。 如果保留空白，則會使用 `1.2` 的預設值。
- 完整**轉寄**密碼：選取 [**啟用**] 以開啟完整轉寄密碼（PFS）。 PFS 是一種 IP 安全性功能，可降低工作階段金鑰遭到入侵時的影響。 **Disable** （預設值）不會使用 PFS。
- **憑證撤銷檢查**：選取 [**啟用**] 以確保憑證不會被撤銷，然後才允許 VPN 連線成功。 這種檢查是最佳做法。 如果 VPN 伺服器在判斷憑證是否已撤銷之前超時，則會授與存取權。 [**停**用] （預設）不會檢查是否有已撤銷的憑證。

- **設定安全性關聯參數**： [**未設定**] （預設）會使用 iOS 系統預設值。 選取 [**啟用**] 以輸入與 VPN 伺服器建立安全性關聯時所使用的參數：
  - **加密演算法**：選取您想要的演算法：
    - DES
    - 3DES
    - AES-128
    - AES-256 （預設值）
    - AES-128-GCM
    - AES-256-GCM
  - **完整性演算法**：選取您想要的演算法：
    - SHA1-96
    - SHA1-160
    - SHA2-256 （預設值）
    - SHA2-384
    - SHA2-512
  - **Diffie-hellman 群組**：選取您想要的群組。 預設值為 group `2`。
  - **存留期**（分鐘）：選擇在旋轉金鑰之前，安全性關聯保持作用中的時間長度。 輸入介於 `10` 和 `1440` 之間的整數（1440分鐘是24小時）。 預設值為 `1440`。

- **為子系安全性關聯設定一組不同的參數**： iOS 可讓您針對 IKE 連線和任何子連接，設定不同的參數。 

  [**未設定**] （預設）會使用您在先前的 [**設定安全性關聯參數**] 設定中輸入的值。 選取 [**啟用**] 以輸入與 VPN 伺服器建立*子*安全性關聯時所使用的參數：
  - **加密演算法**：選取您想要的演算法：
    - DES
    - 3DES
    - AES-128
    - AES-256 （預設值）
    - AES-128-GCM
    - AES-256-GCM
  - **完整性演算法**：選取您想要的演算法：
    - SHA1-96
    - SHA1-160
    - SHA2-256 （預設值）
    - SHA2-384
    - SHA2-512
  - **Diffie-hellman 群組**：選取您想要的群組。 預設值為 group `2`。
  - **存留期**（分鐘）：選擇在旋轉金鑰之前，安全性關聯保持作用中的時間長度。 輸入介於 `10` 和 `1440` 之間的整數（1440分鐘是24小時）。 預設值為 `1440`。

## <a name="automatic-vpn-settings"></a>自動 VPN 設定

- **個別應用程式 VPN**：啟用個別應用程式 VPN。 允許 VPN 連線在特定應用程式開啟時自動觸發。 另請建立應用程式與此 VPN 設定檔的關聯。 如需詳細資訊，請參閱[為 iOS 設定個別應用程式 VPN 的指示](vpn-setting-configure-per-app.md)。
  - **提供者類型**：僅適用於 Pulse Secure 和自訂 VPN。
  - 搭配 Pulse Secure 或自訂 VPN 使用 iOS **個別應用程式 VPN** 設定檔時，選擇應用程式層通道 (app-proxy) 或封包層通道 (packet-tunnel)。 若是應用程式層通道，請將 [ProviderType]  值設定為 [應用程式 Proxy]  ，若是封包層通道，則設定為 [封包通道]  。 如果您不確定要使用的值，請參閱您 VPN 提供者的文件。
  - **觸發此 VPN 的 Safari URL**：新增一或多個網站 URL。 在裝置上使用 Safari 瀏覽器瀏覽這些 URL 時，就會自動建立 VPN 連線。

- **隨選 VPN**：設定可控制 VPN 連線啟動時的條件式規則。 例如，建立一個只在裝置未連線到公司 Wi-Fi 網路時才使用 VPN 連線的條件。 或者，建立一個條件。 例如，若裝置無法存取所輸入 DNS 搜尋網域，則不會啟動 VPN 連線。

  - **SSID 或 DNS 搜尋網域**選取此條件是要使用無線網路 **SSID** 還是 **DNS 搜尋網域**。 選擇 [新增]  即可設定一或多個 SSID 或搜尋網域。
  - **URL 字串探查**：選用。 請輸入規則用來作為測試的 URL。 如果具有此設定檔的裝置無須重新導向就能存取此 URL，則會啟動 VPN 連線。 而裝置會連線到目標 URL。 使用者不會看到 URL 字串探查網站。 URL 字串探查的其中一例就是稽核網頁伺服器的位址，此伺服器會在連線 VPN 之前先檢查裝置合規性。 另一種可能，是 URL 會先測試 VPN 連線到網站的能力，再將裝置透過 VPN 連線到目標 URL。
  - **網域動作**：請選擇下列其中一個項目︰
    - 連線 (若需要)
    - 一律不連線
  - **動作**：請選擇下列其中一個項目︰
    - 連線
    - 評估連線
    - 忽略
    - 中斷連線

## <a name="proxy-settings"></a>Proxy 設定

如果使用 Proxy，請設定下列設定。 Proxy 設定不適用於 Zscaler VPN 連線。  

- **自動設定指令碼**：使用檔案設定 Proxy 伺服器。 輸入包含設定檔的 [Proxy 伺服器 URL]  (例如 `http://proxy.contoso.com`)。
- **位址**：輸入 Proxy 伺服器的完整主機名稱 IP 位址。
- **連接埠號碼**：輸入與 Proxy 伺服器相關聯的連接埠號碼。

## <a name="next-steps"></a>後續步驟

設定檔已建立，但還不會執行任何動作。 接下來，[指派設定檔](device-profile-assign.md)並[監視其狀態](device-profile-monitor.md)。

在[android](vpn-settings-android.md)、 [android Enterprise](vpn-settings-android-enterprise.md)、 [macOS](vpn-settings-macos.md)和[Windows 10](vpn-settings-windows-10.md)裝置上設定 VPN 設定。

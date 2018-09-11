---
title: Microsoft Intune 中 iOS 裝置的 VPN 設定- Azure | Microsoft Docs
description: 在執行 iOS 裝置上的 Microsoft Intune 中，檢視可用虛擬私人網路 (VPN) 組態設定，包括基底設定中的連線詳細資料、驗證方法和分割通道；含有識別碼的自訂 VPN 設定，以及和機碼和值組；包含 Safari URL 的依應用程式 VPN 設定，與含 SSID 或 DNS 搜尋網域的隨選 VPN；以及要包含設定指令碼、IP 或 FQDN 位址和 TCP 連接埠的 Proxy 設定。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 8/28/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: deb6a230573ff20237e6eee386052baba472832a
ms.sourcegitcommit: 4d314df59747800169090b3a870ffbacfab1f5ed
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/30/2018
ms.locfileid: "43313865"
---
# <a name="configure-vpn-settings-in-microsoft-intune-for-devices-running-ios"></a>設定 Microsoft Intune 中執行 iOS 之裝置的 VPN 設定

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

本文說明可用於設定執行 iOS 之裝置上 VPN 連線的 Intune 設定。

下列清單中的值並非全部都能設定，須取決於您選擇的設定。

## <a name="base-vpn-settings"></a>基本 VPN 設定
您在下列清單中看到的實際設定取決於您選取的 VPN 連線類型。  
- **連線名稱**：終端使用者會在瀏覽其裝置是否有可用的 VPN 連線清單時，看到此名稱。
- **自訂網域名稱** (僅限 Zscaler)：在 Zscaler 應用程式的登入欄位中預先填入您的使用者所屬網域。 例如，如果使用者名稱為 **Joe@contoso.net**，網域 **contoso.net** 會在應用程式開啟時以靜態方式出現在欄位中。 如果您未鍵入網域名稱，將會使用 Azure Active Directory 中 UPN 的網域部分。
- **IP 位址或 FQDN**：裝置連線之 VPN 伺服器的 IP 位址或完整網域名稱 (FQDN)。 例如，輸入 **192.168.1.1** 或 **vpn.contoso.com**。 
- **組織的雲端名稱** (僅限 Zscaler)：鍵入您組織佈建所在的雲端名稱。 查詢您用來登入 Zscaler 的 URL 以尋找名稱。  
- **驗證方法**：選擇裝置向 VPN 伺服器進行驗證的方式。 
  - **憑證**：在 [驗證憑證] 底下，選取現有的 SCEP 或 PKCS 憑證設定檔來驗證連線。 [設定憑證](certificates-configure.md)提供了一些有關憑證設定檔的指引。
  - **使用者名稱及密碼**：使用者必須輸入使用者名稱及密碼，才能登入 VPN 伺服器。  

    > [!NOTE]
    > 如果使用者名稱和密碼用來作為 Cisco IPsec VPN 的驗證方法，它們必須透過自訂的 Apple Configurator 設定檔傳遞 SharedSecret。
  
- **連線類型**：從下列廠商清單中選取 VPN 連線類型︰
  - **Check Point Capsule VPN**
  - **Cisco Legacy AnyConnect**：適用於 [Cisco Legacy AnyConnect](https://itunes.apple.com/app/cisco-legacy-anyconnect/id392790924) 應用程式 4.0.5x 版及更舊版本。
  - **Cisco AnyConnect**：適用於 [Cisco AnyConnect](https://itunes.apple.com/app/cisco-anyconnect/id1135064690) 應用程式 4.0.7x 版及更新版本。
  - **SonicWall Mobile Connect**
  - **F5 Access Legacy**：適用於 F5 Access 應用程式 2.1 版及更舊版本。
  - **F5 Access**：適用於 F5 Access 應用程式 3.0 版及更新版本。
  - **Palo Alto Networks GlobalProtect (Legacy)**：適用於 Palo Alto Networks GlobalProtect 應用程式 4.1 版及更舊版本。
  - **Palo Alto Networks GlobalProtect**：適用於 Palo Alto Networks GlobalProtect 應用程式 5.0 版及更新版本。
  - **Pulse Secure**
  - **Cisco (IPSec)**
  - **Citrix VPN**
  - **Citrix SSO**
  - **Zscaler**：需要您整合 Zscaler Private Access (ZPA) 與您的 Azure Active Directory 目錄。 如需詳細步驟，請參閱 [Zscaler 文件](https://help.zscaler.com/zpa/configuration-example-microsoft-azure-ad#Azure_UserSSO)。 
  - **自訂 VPN**    

    > [!NOTE]
    > Cisco、Citrix、F5 和 Palo Alto 已宣佈其舊版用戶端在即將發行的 iOS 12 上無法運作。 您應該盡快移轉到新的應用程式。 如需詳細資訊，請參閱 [Microsoft Intune 支援小組部落格](https://go.microsoft.com/fwlink/?linkid=2013806&clcid=0x409)。

* **排除的 URL** (僅限 Zscaler)：連線到 Zscaler VPN 時，所列出的 URL 可從 Zscaler 雲端外部存取。 

- **分割通道**：[啟用] 或 [停用]，讓裝置依據流量決定所要使用的連線。 例如，旅館中的使用者使用 VPN 連線存取工作檔案，但使用旅館的標準網路進行一般的網頁瀏覽。   

## <a name="custom-vpn-settings"></a>自訂 VPN 設定

如果您已選取 [自訂 VPN] 作為連線類型，請設定下列設定。 Zscaler 和 Citrix 連線也會顯示這些設定。

- **VPN 識別碼**：您要使用之 VPN 應用程式的識別碼，由您的 VPN 提供者所提供。
- **輸入您組織之自訂 VPN 屬性的機碼值組**：新增或匯入 [機碼] 和 [值] 來自訂您的 VPN 連線。 同樣地，這些值通常由 VPN 提供者提供。

## <a name="automatic-vpn-settings"></a>自動 VPN 設定

- **個別應用程式的 VPN**：選擇此選項會啟用個別應用程式的 VPN，這使 VPN 連線能在特定應用程式開啟時自動觸發。 除了選擇此選項外，您還需要建立應用程式與此 VPN 設定檔的關聯。 如需更多詳細資料，請參閱[為 iOS 設定個別應用程式 VPN 的指示](vpn-setting-configure-per-app.md)。 
  - [提供者類型] 設定僅適用於 Pulse Secure 和自訂 VPN。
  - 搭配 Pulse Secure 或自訂 VPN 使用 iOS **個別應用程式 VPN** 設定檔時，您可以選擇使用應用程式層通道 (app-proxy) 或封包層通道 (packet-tunnel)。 將 [提供者類型] 值設定為 [app-proxy] (表示應用程式層通道) 或 [packet-tunnel] (表示封包層通道)。如果您不確定要使用的值，請參閱您 VPN 提供者的文件。 
  - **觸發此 VPN 的 Safari URL**選取即可新增一或多個網站 URL。 在裝置上使用 Safari 瀏覽器瀏覽這些 URL 時，就會自動建立 VPN 連線。

- **隨選 VPN**：設定可控制 VPN 連線起始時機的條件式規則。 例如，建立一個只在裝置未連線到公司 Wi-Fi 網路時才使用 VPN 連線的條件。 或者，建立一個如果裝置無法存取所指定 DNS 搜尋網域便不起始 VPN 連線的條件。

  - **SSID 或 DNS 搜尋網域**選取此條件是要使用無線網路 **SSID** 還是 **DNS 搜尋網域**。 選擇 [新增] 即可設定一或多個 SSID 或搜尋網域。
  - **URL 字串探查**：選用。 請輸入規則用來作為測試的 URL。 如果安裝此設定檔的裝置無須重新導向就能存取此 URL，便會起始 VPN 連線，而裝置便可連線到目標 URL。 使用者不會看到 URL 字串探查網站。 URL 字串探查的其中一例就是稽核網頁伺服器的位址，此伺服器會在連線 VPN 之前先檢查裝置合規性。 另一種可能，是 URL 會先測試 VPN 連線到網站的能力，再將裝置透過 VPN 連線到目標 URL。
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

- **自動設定指令碼**：使用檔案設定 Proxy 伺服器。 輸入包含設定檔的 [Proxy 伺服器 URL] (例如 **http://proxy.contoso.com**)。
- **位址**：輸入 Proxy 伺服器的完整主機名稱 IP 位址。
- **連接埠號碼**：輸入與 Proxy 伺服器相關聯的連接埠號碼。

## <a name="next-step"></a>後續步驟
[在 Intune 中建立 VPN 設定檔](vpn-settings-configure.md)  

---
title: "VPN 連線"
description: "使用 VPN 設定檔，將 VPN 設定部署至組織中的使用者和裝置。"
keywords: 
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.date: 05/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: abc57093-7351-408f-9f41-a30877f96f73
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: e1498cb88fe99129a5ee7f24b618f78fefcf42a6
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2017
---
# <a name="vpn-connections-in-microsoft-intune"></a>Microsoft Intune 中的 VPN 連線

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

虛擬私人網路 (VPN) 為您的使用者提供安全的公司網路遠端存取。 裝置使用「VPN 連線設定檔」來啟動與 VPN 伺服器的連線。 在 Microsoft Intune 中使用「VPN 設定檔」，將 VPN 設定部署給組織中的使用者和裝置，讓他們可以輕鬆且安全地連線到網路。

例如，假設您想要使用連線到公司網路上檔案共用所需的設定來佈建所有 iOS 裝置。 您在建立的 VPN 設定檔中包含連線到公司網路所需的設定，然後將此設定檔部署給所有 iOS 裝置的使用者。 使用者會在可用的網路清單中看到此 VPN 連線，而且很輕鬆就能完成連線。

您可以使用 VPN 設定檔設定下列裝置類型：

* 執行 Android 4 和更新版本的裝置
* Android for Work 裝置
* 執行 iOS 8.0 和更新版本的裝置
* 執行 Mac OS X 10.9 及更新版本的裝置
* 執行 Windows 8.1 和更新版本的已註冊裝置
* 執行 Windows Phone 8.1 和更新版本的裝置
* 執行 Windows 10 Desktop 和行動裝置版的裝置

VPN 設定檔組態選項會視您選取的裝置類型而有所不同。

## <a name="vpn-connection-types"></a>VPN 連線類型

Intune 支援使用下列連線類型建立 VPN 設定檔：


連線類型 |iOS 和 Mac OS X  |Android 和 Android for Work|Windows 8.1|Windows RT 8.1|Windows Phone 8.1|Windows 10 Desktop 和行動裝置版 |
----------------|------------------|-------|-----------|----------|--------------|-----------------|----------------------|
Cisco AnyConnect|是 |是   |否    |否  |否    | 是 (OMA-URI，僅限行動裝置)|     
Cisco (IPsec)|是 |是   |否  |否  |否 | 否|
Citrix|是 |是 (僅 Android)   |否  |否  |否 | 否|
Pulse Secure|是  |是 |是   |是  |是| 是|        
F5 Edge Client|是 |是 |是 |是  |   是 |  是|   
Dell SonicWALL Mobile Connect|是 |是 |是 |是 |是 |是|         
CheckPoint Mobile VPN|是 |是 |是 |是|是|是|
Microsoft SSL (SSTP)|否 |否 |否 |否|否|VPNv1 OMA-URI*|
Microsoft Automatic|否 |否 |否 |否|是 (OMA-URI)|是|
IKEv2|iOS 自訂設定檔|否 |否 |否|是 (OMA-URI)|是|
PPTP|iOS 自訂設定檔|否 |否 |否|否|是|
L2TP|iOS 自訂設定檔|否 |否 |否|是 (OMA-URI)|是|

\* 沒有其他設定可供Windows 10 在其他狀況使用。

> [!IMPORTANT]
> 您必須先針對設定檔安裝適用的 VPN 應用程式，才能使用部署至裝置的 VPN 設定檔。 您可以使用[在 Microsoft Intune 中部署應用程式](deploy-apps-in-microsoft-intune.md)主題中的資訊，協助您使用 Intune 部署適用的應用程式。  

 了解如何使用 [VPN 設定檔自訂組態](create-custom-vpn-profiles.md)中的 URI 設定，建立自訂 VPN 設定檔。     

## <a name="methods-of-securing-vpn-profiles"></a>保護 VPN 設定檔的方法

VPN 設定檔可以使用來自不同製造商的多種連線類型及通訊協定。 這些連線通常透過以下兩種方法之一進行保護。

### <a name="certificates"></a>憑證

當您建立 VPN 設定檔時，請選擇先前在 Intune 中建立的 SCEP 或 PFX 憑證設定檔。 這稱為識別憑證。 其用來針對您建立且允許使用者裝置連線的受信任憑證設定檔 (或「根憑證」) 進行驗證。 受信任的憑證會部署到可驗證 VPN 連線的電腦 (一般是 VPN 伺服器)。

如需如何建立和使用 Intune 中憑證設定檔的詳細資訊，請參閱[使用憑證設定檔保護資源存取](secure-resource-access-with-certificate-profiles.md)。

### <a name="user-name-and-password"></a>使用者名稱和密碼

使用者藉由提供使用者名稱和密碼向 VPN 伺服器進行驗證。

## <a name="create-a-vpn-profile"></a>建立 VPN 設定檔

1. 在 [Microsoft Intune 管理主控台](https://manage.microsoft.com)中，選擇 [原則] > [新增原則]。
2. 展開相關的裝置類型，然後選擇該裝置的 VPN 設定檔，以選取新原則的範本：
    * **VPN 設定檔 (Android 4 及更新版本)**
    * **VPN 設定檔 (Android for Work)**
    * **VPN 設定檔 (iOS 8.0 及更新版本)**
    * **VPN 設定檔 (Mac OS X 10.9 及更新版本)**
    * **VPN 設定檔 (Windows 8.1 及更新版本)**
    * **VPN 設定檔 (Windows Phone 8.1 及更新版本)**
    * **VPN 設定檔 (Windows 10 Desktop/行動裝置版及更新版本)**

 您只能建立和部署自訂 VPN 設定檔原則。 沒有建議的設定。

> [!Note]
> 適用於 Android for Work 裝置的 VPN 設定檔只會針對安裝在該裝置之工作設定檔的應用程式，啟用 VPN 連線。
>
> 部分 VPN 連線類型支援 Android for Work 裝置的個別應用程式 VPN，以及在透過 Intune 散發的應用程式上啟用個別應用程式 VPN。  

3. 使用下表協助您設定 VPN 設定檔設定：

設定名稱  |詳細資訊  
---------|---------
**Name**     |輸入 VPN 設定檔的唯一名稱，協助您在 Intune 主控台中識別該 VPN 設定檔。         
**說明**     |提供概述 VPN 設定檔的描述以及協助您找到它的其他相關資訊。         
**VPN 連線名稱 (對使用者顯示)**     |指定 VPN 設定檔的名稱。 這是使用者在其裝置的可用 VPN 連線清單中看到的名稱。         
**連線類型**     |  請在下列項目中選取 VPN 設定檔要使用的連線類型：[Cisco AnyConnect (Windows 8.1 或 Windows Phone 8.1 不提供)]、[Pulse Secure]、[Citrix]、[F5 Edge Client]、[Dell SonicWALL Mobile Connect]、[CheckPoint Mobile VPN]。
**VPN 伺服器描述**     | 指定裝置將連線之 VPN 伺服器的描述。 範例：**Contoso VPN 伺服器**。 當連線類型為 [F5 Edge Client] 時，使用 [伺服器清單] 欄位指定伺服器描述及 IP 位址的清單。
**伺服器 IP 位址或 FQDN**    |提供裝置要連線之 VPN 伺服器的 IP 位址或完整網域名稱。 範例：**192.168.1.1**、**vpn.contoso.com**。  當連線類型為 [F5 Edge Client] 時，使用 [伺服器清單] 欄位指定伺服器描述及 IP 位址的清單。         |         
**伺服器清單**     |選擇 [新增] 來新增要用於 VPN 連線的新 VPN 伺服器。 您也可以指定哪部伺服器是連線時的預設伺服器。 只有在連線類型為 [F5 Edge Client] 時，才會顯示此選項。         
**透過 VPN 連線傳送所有網路流量**     |如果您選取此選項，則會透過 VPN 連線傳送所有網路流量。 若未選取此選項，用戶端將會在連線到協力廠商 VPN 伺服器時，動態交涉分割通道時的路由。 只有公司網路的連線會透過 VPN 通道傳送。 當您連線至網際網路上的資源時不會使用 VPN 通道。
**驗證方法**| 選取 VPN 連線使用的驗證方法：[憑證] 或 [使用者名稱及密碼]。 (當連線類型為 Cisco AnyConnect 時，無法使用 [使用者名稱及密碼])。Windows 8.1 沒有 [驗證方法] 選項。
**在每次登入時記住使用者認證**|選取此選項，確保記住使用者認證，讓使用者不必每次建立連線時都輸入認證。
**選取用戶端驗證的用戶端憑證 (身分識別憑證)**|選取先前建立的用戶端 SCEP 憑證，並用來驗證 VPN 連線。 如需如何使用 Intune 中憑證設定檔的詳細資訊，請參閱[使用憑證設定檔保護資源存取](secure-resource-access-with-certificate-profiles.md)。 只有在驗證方法是 [憑證] 時，才會顯示此選項。
**角色**| 指定有權存取此連線之使用者角色的名稱。 使用者角色定義個人設定和選項，以及啟用或停用某些存取功能。 只有在連線類型為 [Pulse Secure] 或 [Citrix] 時，才會顯示這個選項。
**領域**|指定您想要使用之驗證領域的名稱。 驗證領域就是 Pulse Secure 或 Citrix 連線類型使用的驗證資源群組。 只有在連線類型為 [Pulse Secure] 或 [Citrix] 時，才會顯示這個選項。
**登入群組或網域**|指定您想要連線之登入群組或網域的名稱。 只有在連線類型為 [Dell SonicWALL Mobile Connect] 時，才會顯示此選項。
**指紋**|指定將用來確認是否可信任 VPN 伺服器的字串 (例如 "Contoso Fingerprint Code")。 指紋可以傳送至用戶端，如此用戶端才知道連線時可以信任有相同指紋的任何伺服器。 如果裝置還沒有指紋，則會提示使用者信任所連線的 VPN 伺服器，同時顯示指紋。 (使用者可手動驗證指紋，然後選擇 [信任] 即可連線)。只有在連線類型為 [CheckPoint Mobile VPN] 時，才會顯示此選項。
**個別應用程式的 VPN**|如果您想要這個 VPN 連線與 iOS 或 Mac OS X 應用程式產生關聯，以在執行應用程式時開啟連線，請選取這個選項。 部署軟體時，您可以將 VPN 設定檔與應用程式產生關聯。 如需詳細資訊，請參閱[在 Microsoft Intune 中部署應用程式](deploy-apps-in-microsoft-intune.md)
**隨選 VPN**|您可以針對 iOS 8.0 和更新裝置設定隨選 VPN。 設定這項功能的指示已在[適用於 iOS 裝置的隨選 VPN](#on-demand-vpn-for-ios-devices) 中提供。
**自動偵測 Proxy 設定** (僅限 iOS、Mac OS X、Windows 8.1 和 Windows Phone 8.1)|如果您的 VPN 伺服器進行連線時需要 Proxy 伺服器，請指定是否要裝置自動偵測連線設定。 如需詳細資訊，請參閱 Windows Server 文件。
**使用自動設定指令碼** (僅限 iOS、Mac OS X、Windows 8.1 和 Windows Phone 8.1)|如果您的 VPN 伺服器進行連線時需要 Proxy 伺服器，請指定是否要使用自動設定指令碼來定義設定，然後指定含有設定的檔案 URL。 如需詳細資訊，請參閱 Windows Server 文件。
**使用 Proxy 伺服器** (僅限 iOS、Mac OS X、Windows 8.1 和 Windows Phone 8.1)|如果您的 VPN 伺服器進行連線時需要 Proxy 伺服器，請選取此選項，然後指定 Proxy 伺服器的位址和連接埠號碼。 如需詳細資訊，請參閱 Windows Server 文件。
**本機位址不要使用 Proxy 設定** (僅限 iOS、Mac OS X、Windows 8.1 和 Windows Phone 8.1)|如果您的 VPN 伺服器進行連線時需要 Proxy 伺服器，則不想要使用所指定本機位址的 Proxy 伺服器時，請選取此選項。 如需詳細資訊，請參閱 Windows Server 文件。
**自訂 XML** (Windows 8.1 和更新版本，以及 Windows Phone 8.1 和更新版本)|指定設定 VPN 連線的自訂 XML 命令。 **Pulse Secure** 的範例：&lt;pulse-schema&gt;&lt;isSingleSignOnCredential&gt;true&lt;/isSingleSignOnCredential&gt;&lt;/pulse-schema&gt;。 **CheckPoint Mobile VPN** 的範例：&lt;CheckPointVPN port="443" name="CheckPointSelfhost" sso="true"  debug="3" /&gt;。 **Dell SonicWALL Mobile Connect** 的範例：&lt;MobileConnect&gt;&lt;Compression&gt;false&lt;/Compression&gt;&lt;debugLogging&gt;True&lt;/debugLogging&gt;&lt;packetCapture&gt;False&lt;/packetCapture&gt;&lt;/MobileConnect&gt;。 **F5 Edge Client**&lt;f5-vpn-conf&gt;&lt;single-sign-on-credential /&gt;&lt;/f5-vpn-conf&gt;。 如需如何撰寫自訂 XML 命令的詳細資訊，請參閱相關製造商的 VPN 文件。
**DNS 尾碼搜尋清單** (僅限 Windows Phone 8.1)|在一行指定一個 DNS 尾碼。 使用簡短名稱連線到網站時，將會搜尋您指定的每個 DNS 尾碼。 例如，指定 DNS 尾碼 **domain1.contoso.com** 和 **domain2.contoso.com**、造訪 URL **http://mywebsite**，以及搜尋 URL **http://mywebsite.domain1.contoso.com** 和 **http://mywebsite.domain2.contoso.com**。
**連線到公司 Wi-Fi 網路時略過 VPN** (僅限 Windows Phone 8.1)|選取此選項，指定當裝置連線到公司 Wi-Fi 網路時，不會使用 VPN 連線。
**連線到家用 Wi-Fi 網路時略過 VPN** (僅限 Windows Phone 8.1)|選取此選項，指定當裝置連線到家用 Wi-Fi 網路時，不會使用 VPN 連線。

Windows 10 Desktop 和行動裝置版也提供下列設定。

設定名稱  |詳細資訊  
---------|---------
**網路流量規則**|選取將針對 VPN 連線啟用的通訊協定、本機和遠端連接埠，以及位址範圍。 如果您未建立網路流量規則，則會啟用所有通訊協定、連接埠和位址範圍。 在您建立規則之後，VPN 連線只會使用您在該項規則中所指定的通訊協定、連接埠和位址範圍。
**路由**|選取哪些路由會使用 VPN 連線。
**DNS 伺服器**| 選取在連線建立之後 VPN 連線會使用的 DNS 伺服器。         
**相關聯的應用程式**|提供會自動使用 VPN 連線的應用程式清單。 應用程式類型會決定應用程式識別碼。 若為通用應用程式，會提供套件系列名稱。 若為傳統型應用程式，會提供應用程式的檔案路徑。          


> [!IMPORTANT]
> 我們建議您保護所有您為了用於個別應用程式 VPN 設定而編譯的應用程式清單。 如果未經授權的使用者修改您的清單，而您將它匯入到個別應用程式的 VPN 應用程式清單中，則您可能會將 VPN 存取權授權給不應該存取的應用程式。 保護應用程式清單的一種方法是使用存取控制清單 (ACL)。

以下舉例說明何時可能會使用公司界限設定。 如果您只想針對遠端桌面啟用 VPN，請建立網路流量規則，允許外部連接埠 3996 上有通訊協定 27 的流量。 其他任何流量都不會使用 VPN。

當您的 VPN 連線類型無法讓您定義流量在分割通道中的處理方式時，定義公司界限中的路由可能會有幫助。 在本例中，使用 [路由] 可列出將要使用 VPN 的所有路由。

您可以建立自訂 OMA-URI 設定，僅限 Windows 10 裝置的特定應用程式才能使用 VPN。

新的原則會顯示在 [原則] 工作區的 [設定原則] 節點中。

### <a name="on-demand-vpn-for-ios-devices"></a>適用於 iOS 裝置的隨選 VPN
您可以針對 iOS 8.0 和更新裝置設定隨選 VPN。

> [!NOTE]
>  
> 您無法在相同原則中使用個別應用程式 VPN 和隨選 VPN。

1. 在原則設定頁面上，尋找 [此 VPN 連線之依需求指定的規則]。 標示為 [符合] 的欄位為規則所要檢查的條件，[動作] 的欄位則為條件符合時原則所要觸發的動作。
2. 選擇 [新增] 來建立規則。 您可以在規則中設定的符合類型有兩種。 您在每個規則中只能設定其中一種類型。
  - **SSID** - 該類型會參照到無線網路。
  - **DNS 搜尋網域** - 您可以使用如 *team. corp.contoso.com* 的完整網域名稱，或使用如 *contoso.com* 的網域名稱，這相當於使用 * *.contoso.com*。
3. 選擇性：提供 URL 字串探查，這是規則會用來做為測試的 URL。 如果安裝此設定檔的裝置可以在不需重新導向之下存取這個 URL，VPN 便會建立，且裝置將會連線到目標 URL。 使用者將不會看到 URL 字串探查網站。 URL 字串探查的範例，是會在連線 VPN 之前先檢查裝置相容性的稽核網頁伺服器位址。 另一種可能，是 URL 會先測試 VPN 連線到網站的能力，然後再將裝置透過 VPN 連線到目標 URL。
4. 選擇下列其中一項動作：
  - **連線**
  - **評估連線**：它有三個設定 a. **網域動作** - 選擇 [連線 (若需要)] 或 [Never connect] (一律不連線) b. **以逗號分隔的網域清單** - 只有在您選擇 [網域動作] 的 [連線 (若需要)] 時才能進行這項設定 c. **必要的 URL 字串探查** - HTTP 或 HTTPS (建議選項) URL，例如 *https://vpntestprobe.contoso.com*。 規則會檢查是否有來自此地址的回應。 如果沒有，且 [網域動作] 為 [連線 (若需要)]，便會觸發 VPN。
      
     > [!TIP]
     >
     >您可能使用此動作的範例，是您公司網路上的某些網站需要直接或是 VPN 公司網路連線，但其他網站則不用。 如果您將 *corp.contoso.com* 列入 [以逗號分隔的 DNS 搜尋網域清單]，您可以選擇 [連線 (若需要)]，然後在可能需要 VPN 的網路中列出特定網站，例如 *sharepoint.corp.contoso.com*。 此規則接著會檢查是否可連線到 *vpntestprobe.contoso.com*。 如果不行，則會針對 sharepoint 網站觸發 VPN。
  - **忽略**：此設定會使 VPN 連線能力不受變更。 如果已連線 VPN，則會維持連線，如果未連線 VPN，則不會連線。 例如，您可能會有針對所有內部公司網站連線 VPN 的規則，但想要讓其中一個內部網站僅在裝置實際連線到公司網路時才能存取。 在此情況下，您要針對該網站建立忽略規則。
  - **中斷連線**：當符合條件時，將裝置從 VPN 中斷連線。 例如，您可以將您的公司無線網路列入 [SSID] 欄位並建立規則，使裝置連線到那些網路時，將它們從 VPN 中斷連線。

會先評估網域特定規則，然後才評估所有網域規則。


## <a name="deploy-the-policy"></a>部署原則

1.  在 [原則] 工作區中，選取您要部署的原則，然後選擇 [管理部署]。

2.  在 [管理部署]  對話方塊中：

    -   若要部署原則，選取您要部署原則的一或多個群組，然後選擇 [新增] &gt; [確定]。

    -   若要關閉對話方塊但不加以部署，請選擇 [取消]。


成功部署之後，使用者會看到您在其裝置的 VPN 連線清單中指定的 VPN 連線名稱。

在 [原則]  工作區的 [概觀]  頁面上，狀態摘要和警示可識別需要注意的原則問題。 此外，狀態摘要還會顯示在 [儀表板] 工作區中。

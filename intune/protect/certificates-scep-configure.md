---
title: 使用 Microsoft Intune 設定基礎結構以支援 SCEP 憑證設定檔 - Azure | Microsoft Docs
description: 若要在 Microsoft Intune 中使用 SCEP，請設定您的內部部署 AD 網域、建立憑證授權單位、設定 NDES 伺服器，並安裝 Intune 憑證連接器。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 08/28/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 82177e475c6f5a637aba9f053e64986dcd9bdadf
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72502546"
---
# <a name="configure-infrastructure-to-support-scep-with-intune"></a>設定基礎結構以支援 SCEP 與 Intune  
  
Intune 支援使用簡單憑證註冊通訊協定 (SCEP) 來[驗證與您應用程式和公司資源的連線](certificates-configure.md)。 SCEP 使用憑證授權單位 (CA) 憑證來保護憑證簽署要求 (CSR) 的訊息交換。 如果您的基礎結構支援 SCEP，您可以使用 Intune *SCEP 憑證*設定檔 (Intune 中的一種裝置設定檔) 將憑證部署至您的裝置。 使用 Active Directory 憑證服務授權單位時，需要 Microsoft Intune 憑證連接器以搭配 Intune 使用 SCEP 憑證設定檔。 使用[協力廠商憑證授權單位](certificate-authority-add-scep-overview.md#set-up-third-party-ca-integration)時，則不需要連接器。  

本文中的資訊可協助您設定基礎結構，以在使用 Active Directory 憑證服務時支援 SCEP。 在您設定基礎結構後，您即可使用 Intune 來[建立及部署 SCEP 憑證設定檔](certificates-profile-scep.md)。  

> [!TIP]  
> Intune 也支援使用[公開金鑰加密標準 #12 憑證](certficates-pfx-configure.md)。  


## <a name="prerequisites-for-using-scep-for-certificates"></a>將 SCEP 用於憑證的必要條件  
在您繼續之前，請確認您已為將使用 SCEP 憑證設定檔的裝置[建立並部署「受信任憑證」  設定檔](certificates-configure.md#export-the-trusted-root-ca-certificate)。 SCEP 憑證設定檔會直接參考您用於透過受信任根 CA 憑證來佈建裝置的受信任憑證設定檔。  

### <a name="servers-and-server-roles"></a>伺服器與伺服器角色  
下列內部部署基礎結構必須在已加入網域的伺服器上執行 (Web 應用程式 Proxy 伺服器除外)。  
- **憑證授權單位** – 使用在企業版 Windows Server 2008 R2 Service Pack 1 或更新版本上執行的 Microsoft Active Directory 憑證服務企業憑證授權單位 (CA)。 您使用的 Windows Server 版本必須持續受到 Microsoft 支援。 不支援獨立 CA。 如需詳細資訊，請參閱[安裝憑證授權單位](https://technet.microsoft.com/library/jj125375.aspx)。 如果您的 CA 執行 Windows Server 2008 R2 SP1，您必須[從 KB2483564 安裝 Hotfix](https://support.microsoft.com/kb/2483564/)。  

- **NDES 伺服器角色** - 您必須在 Windows Server 2012 R2 或更新版本上，設定網路裝置註冊服務 (NDES) 伺服器角色。 我們將在本文後面的章節引導您[安裝 NDES](#set-up-ndes)。  

  - 裝載 NDES 的伺服器必須已加入網域，且與企業 CA 位於同一個樹系中。  
  - 您無法使用安裝於裝載企業 CA 之伺服器上的 NDES。  
  - 您可在與裝載 NDES 相同的伺服器上安裝 Microsoft Intune 憑證連接器。  

  若要深入了解 NDES，請參閱 Windows Server 文件中的 [Network Device Enrollment Service Guidance](https://technet.microsoft.com/library/hh831498.aspx) (網路裝置註冊服務指導)，以及 [Using a Policy Module with the Network Device Enrollment Service](https://technet.microsoft.com/library/dn473016.aspx) (使用原則模組搭配網路裝置註冊服務)。  

- **Microsoft Intune 憑證連接器** - 需要 Microsoft Intune 憑證連接器以搭配 Intune 使用 SCEP 憑證設定檔。 本文將引導您[安裝此連接器](#install-the-intune-certificate-connector)。  

  連接器支援聯邦資訊處理標準 (FIPS) 模式。 FIPS 並非必要，但當其啟用時可發行及撤銷憑證。  
  - 連接器必須與 NDES 伺服器角色 (執行 Windows Server 2012 R2 或更新版本的伺服器) 在相同伺服器上執行。  
  - Windows Server 2012 R2 及更新版本會自動隨附連接器所需的 .NET 4.5 Framework。  
  - 在裝載 Microsoft Intune 憑證連接器和 [NDES 的伺服器上必須停用](https://technet.microsoft.com/library/cc775800(v=WS.10).aspx) Internet Explorer 增強式安全性設定。  

下列內部部署基礎結構為選擇性：  
  若要允許網際網路上的裝置獲得憑證，您需要在公司網路外部發佈 NDES URL。 您可以使用 Azure AD 應用程式 Proxy、Web 應用程式 Proxy 伺服器或其他反向 Proxy。
  
- **Azure AD 應用程式 Proxy** (選擇性) - 您可以使用 Azure AD 應用程式 Proxy 將您的 NDES URL 發佈至網際網路，而不是使用專用的 Web 應用程式 Proxy (WAP) 伺服器來發佈。 這會允許內部網路和網際網路對應裝置獲得憑證。 如需詳細資訊，請參閱[如何為內部部署應用程式提供安全的遠端存取](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy)。 

- **Web 應用程式 Proxy 伺服器** (選擇性) - 使用執行 Windows Server 2012 R2 或更新版本的伺服器作為 Web 應用程式 Proxy (WAP) 伺服器，將您的 NDES URL 發佈至網際網路。  這會允許內部網路和網際網路對應裝置獲得憑證。

  裝載 WAP 伺服器 [必須安裝更新](https://blogs.technet.com/b/ems/archive/2014/12/11/hotfix-large-uri-request-in-web-application-proxy-on-windows-server-2012-r2.aspx) ，以啟用網路裝置註冊服務所使用之長 URL 的支援。 此更新隨附於 [2014 年 12 月更新彙總套件](https://support.microsoft.com/kb/3013769)，或個別提供於 [KB3011135](https://support.microsoft.com/kb/3011135)。  

  WAP 伺服器必須有 SSL 憑證，該憑證符合發佈給外部用戶端的名稱，且信任在裝載 NDES 服務的電腦上所使用 SSL 憑證。 這些憑證讓 WAP 伺服器能從用戶端終止 SSL 連線，以及建立與 NDES 服務的新 SSL 連線。  

  如需詳細資訊，請參閱[規劃 WAP 的憑證](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn383650(v=ws.11)#plan-certificates) \(英文\) 和 [WAP 伺服器的一般相關資訊](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn584113(v=ws.11)) \(英文\)。

### <a name="accounts"></a>帳戶   
- **NDES服務帳戶** - 在您設定 NDES 前，請先識別要用作 NDES 服務帳戶的網域使用者帳戶。 您需要在發行 CA 上設定範本時指定此帳戶，才能設定 NDES。  

  此帳戶必須在裝載 NDES 的伺服器上具有下列權限：  
  - **本機登入**  
  - **登入為服務**  
  - **以批次工作登入**  

  如需詳細資訊，請參閱[建立網域使用者帳戶來作為 NDES 服務帳戶](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831498(v=ws.11)#to-create-a-domain-user-account-to-act-as-the-ndes-service-account)。 
- **存取裝載 NDES 服務的電腦** - 您需要擁有在您安裝 NDES 之伺服器上安裝和設定 Windows 伺服器角色權限的網域使用者帳戶。  

- **存取憑證授權單位** - 您需要擁有有權管理憑證授權單位的網域使用者帳戶。  

### <a name="network-requirements"></a>網路需求

建議您透過反向 Proxy 發佈 NDES 服務，例如 [Azure AD 應用程式 Proxy、Web 存取 Proxy](https://azure.microsoft.com/documentation/articles/active-directory-application-proxy-publish/)，或是協力廠商 Proxy。 如果您未使用反向 Proxy，則允許連接埠 443 上從網際網路所有主機和 IP 位址到 NDES 服務的 TCP 流量。  

允許 NDES 服務與您環境中任何支援基礎結構之間進行通訊所需的所有連接埠和通訊協定。 例如，裝載 NDES 服務的電腦必須與 CA、DNS 伺服器、網域控制站以及環境內可能存在的其他服務或伺服器進行通訊，例如 Configuration Manager。

### <a name="certificates-and-templates"></a>憑證和範本

當您使用 SCEP 時，會使用下列憑證證和範本。

|物件    |詳細資料    |
|----------|-----------|
|**SCEP 憑證範本**         |您將在發行 CA 上設定用於完成裝置 SCEP 要求的範本。 |
|**用戶端驗證憑證** |從您的發行 CA 或公用 CA 要求。<br /> 您在裝載 NDES 服務的電腦上安裝此憑證，並由 Intune 憑證連接器使用。<br /> 如果憑證在您用於發行此憑證的 CA 範本上具有「用戶端」  和「伺服器驗證」  金鑰使用方式集合 (**增強金鑰使用方法**)。 您即可使用相同的憑證來進行伺服器和用戶端驗證。 |
|**伺服器驗證憑證** |從發行 CA 或公用 CA 要求的網頁伺服器認證。<br /> 您在裝載 NDES 之電腦上的 IIS 中安裝並繫結此 SSL 憑證。<br />如果憑證在您用於發行此憑證的 CA 範本上具有「用戶端」  和「伺服器驗證」  金鑰使用方式集合 (**增強金鑰使用方法**)。 您即可使用相同的憑證來進行伺服器和用戶端驗證。 |
|**可信任的根 CA 憑證**       |若要使用 SCEP 憑證設定檔，裝置必須信任您的受信任根憑證授權單位 (CA)。 使用 Intune 中的「受信任憑證設定檔」  ，將受信任的根 CA 憑證佈建給使用者和裝置。 <br/><br/> **-** 針對每個作業系統平台使用單一受信任根 CA 憑證，並將該憑證與您建立的每個受信任根憑證設定檔建立關聯。 <br /><br /> **-** 您可以在需要時使用其他受信任根 CA 憑證。 例如，當您需要向 CA 提供信任，使其為您簽署 Wi-Fi 存取點的伺服器驗證憑證時，您可能會使用其他的憑證。 針對發行 CA 建立其他受信任的根 CA 憑證。  在 Intune 中建立的 SCEP 憑證設定檔中，請確認您為發行 CA 指定受信任的根 CA 設定檔。<br/><br/> 如需受信任憑證設定檔的資訊，請參閱＜在 Intune 中使用憑證以進行驗證＞  中的[＜匯出受信任的根 CA 憑證＞](certificates-configure.md#export-the-trusted-root-ca-certificate)和[＜建立受信任的憑證設定檔＞](certificates-configure.md#create-trusted-certificate-profiles)。 |

## <a name="configure-the-certification-authority"></a>設定憑證授權單位

在下列各節中，您將：
- 設定並發佈 NDES 所需的範本。 
- 設定撤銷憑證的必要權限。 

下列章節需要對 Windows Server 2012 R2 或更新版本以及 Active Directory 憑證服務 (AD CS) 有一定程度的了解。  

### <a name="access-your-issuing-ca"></a>存取您的發行 CA

1. 使用具有充分權限管理 CA 的網域帳戶來登入您的發行 CA。  
2. 開啟憑證授權單位 Microsoft Management Console (MMC)。 您可以**執行** 'certsrv.msc'，或在 [伺服器管理員]  中按一下 [工具]  ，然後按一下 [憑證授權單位]  。
3. 選取 [憑證範本]  節點，按一下 [動作]   > [管理]  。

### <a name="create-the-scep-certificate-template"></a>建立 SCEP 憑證範本

1. 建立 v2 憑證範本 (具有 Windows 2003 相容性) 以用作 SCEP 憑證範本。 您可以：  
   - 使用 [憑證範本]  嵌入式管理單元來建立新的自訂範本。  
   - 複製現有範本 (例如使用者範本) 並更新複本以用作 NDES 範本。
 
2. 在範本的指定索引標籤上進行下列設定：
   - **一般**：
     - 取消選取 [在 Active Directory 中發佈憑證]  。
     - 指定易記的 [範本顯示名稱]  ，以便您稍後識別此範本。  

   - **主體名稱**：  
     - 選取 [在要求中提供]  。 安全性由 NDES 的 Intune 原則模組實施。  

     ![範本, 主體名稱索引標籤](./media/certificates-scep-configure/scep-ndes-subject-name.jpg)
   - **延伸模組**：  
     - 確認 [應用程式原則描述]  包含 [用戶端驗證]  。  
       > [!IMPORTANT]  
       > 僅新增您需要的應用程式原則。 向您的安全性系統管理員確認您的選擇。
 
     - 針對 iOS 和 macOS 憑證範本，另請編輯 [金鑰使用方法]  ，並確保未選取 [簽章是原件證明]  。

     ![範本, 延伸索引標籤](./media/certificates-scep-configure/scep-ndes-extensions.jpg)  

   - **安全性**：  
     - 新增 **NDES 服務帳戶**。 此帳戶需要此範本的**閱讀**及**註冊**權限。

     - 針對將建立 SCEP 設定檔的 Intune 管理員新增其他帳戶。 這些帳戶需要範本的**讀取**權限，以便這些管理員能在建立 SCEP 設定檔時瀏覽至此範本。  

     ![範本, 安全性索引標籤](./media/certificates-scep-configure/scep-ndes-security.jpg)  

   - **處理要求**：  
      下圖為範例。 您的設定可能會有所不同。  

     ![範本, 處理要求索引標籤](./media/certificates-scep-configure/scep-ndes-request-handling.png) 

   - **發行需求**：  
     下圖為範例。 您的設定可能會有所不同。  

     ![範本, 發行需求索引標籤](./media/certificates-scep-configure/scep-ndes-issuance-reqs.jpg)  

3. 儲存憑證範本。  

### <a name="create-the-client-certificate-template"></a>建立用戶端憑證範本

Intune 憑證連接器需要具有「用戶端驗證」  增強金鑰使用方法的憑證，以及等同於安裝連接器之電腦 FQDN 的主體名稱。 具有下列屬性的範本是必要的：

- **延伸模組** > **應用程式原則**必須包含**用戶端驗證**
- **主體名稱** > **在要求中提供**。

如果您已擁有包含這些屬性的範本，您可以重複使用該範本，或複製現有範本或建立自訂範本來建立新範本。

### <a name="create-the-server-certificate-template"></a>建立伺服器憑證範本

受控裝置與 NDES 伺服器的 IIS 之間使用 HTTPS 進行通訊，而 HTTPS 需要使用憑證。 您可以使用**網頁伺服器**憑證範本來發行此憑證。 或者，如果您希望擁有專用範本，則需要下列屬性：

- **延伸模組** > **應用程式原則**必須包含**伺服器驗證**
- **主體名稱** > **在要求中提供**。

> [!NOTE]  
> 如果您擁有可滿足用戶端和伺服器憑證範本要求的憑證，則您可以為 IIS 和 Intune 憑證連接器使用單一憑證。

### <a name="grant-permissions-for-certificate-revocation"></a>授與撤銷憑證的權限

若要讓 Intune 能夠撤銷不再需要的憑證，您必須在憑證授權單位中授與權限。 

在 Intune 憑證連接器上，您可以使用 NDES 伺服器**系統帳戶**或特定帳戶 (例如 **NDES 服務帳戶**)。

1. 在憑證授權單位主控台上，以右鍵按一下 CA 名稱並選取 [屬性]  。
2. 在 [安全性]  索引標籤中按一下 [新增]  。
3. 授與**發行與管理憑證**權限：
   - 如果您選擇使用 NDES 伺服器**系統帳戶**，請將權限提供給 NDES 伺服器。
   - 如果您選擇使用 **NDES 服務帳戶**，請改將權限提供給該帳戶。

### <a name="modify-the-validity-period-of-the-certificate-template"></a>修改憑證範本的有效期間

修改憑證範本的有效期間為選擇性。  

在您[建立 SCEP 憑證範本](#create-the-scep-certificate-template)後，您即可編輯範本以檢閱 [一般]  索引標籤上的**有效期間**。  

根據預設，Intune 使用範本中所設定的值。 不過，您可以設定 CA 以允許要求者輸入不同的值，然後就可以從 Intune 主控台內設定該值。  

> [!IMPORTANT]  
> 針對 iOS 和 macOS，一律使用範本中的值集合。  

#### <a name="to-configure-a-value-that-can-be-set-from-within-the-intune-console"></a>設定可在 Intune 主控台內設定的值  
1. 在 CA 上執行下列命令：  
   -**certutil -setreg Policy\EditFlags +EDITF_ATTRIBUTEENDDATE**  
   -**net stop certsvc**  
   -**net start certsvc**  

2. 在發行的 CA 上使用 [憑證授權單位] 嵌入式管理單元來發行憑證範本。 選取 [憑證範本]  節點，選取 [動作]   > [新增]   > [要發行的憑證範本]  ，然後選取您上一節中建立的憑證範本。  

3. 檢視**憑證範本**資料夾中的發行範本來加以驗證。  

## <a name="set-up-ndes"></a>設定 NDES  
下列程序可協助您設定網路裝置註冊服務 (NDES) 以搭配 Intune 使用。 如需 NDES 的詳細資訊，請參閱 [Network Device Enrollment Service Guidance](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831498(v%3dws.11)) (網路裝置註冊服務指導)。  

### <a name="install-the-ndes-service"></a>安裝 NDES 服務  
1. 在將裝載 NDES 服務的伺服器上，以**企業系統管理員**的身分登入，然後使用[新增角色及功能精靈](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831809(v=ws.11))來安裝 NDES：

   1. 在精靈中，選取 [Active Directory 憑證服務]  以存取 AD CS 角色服務。 選取 [網路裝置註冊服務]  ，取消選取 [憑證授權單位]  ，然後完成精靈。  

      > [!TIP]  
      > 在 [安裝進度]  中，不要選取 [關閉]  。 相反地，請選取 [設定目的地伺服器上的 Active Directory 憑證服務]  連結。 [AD CS 設定精靈]  隨即開啟，可讓您用來進行本文中的下一個程序：「設定 NDES 服務」  。 [AD CS 設定] 開啟之後，您可以關閉 [新增角色及功能精靈]。  

   2. 當 NDES 加入至伺服器時，精靈也會安裝 IIS。 請確認 IIS 具有下列設定：  

      - [Web 伺服器]   > [安全性]   > [要求篩選]   
      - [網頁伺服器]   > [應用程式開發]   > [ASP.NET 3.5]   

        安裝 ASP.NET 3.5 時會安裝 .NET Framework 3.5。 安裝 .NET Framework 3.5 時，請安裝核心 [.NET Framework 3.5]  功能和 [HTTP 啟動]  。  
      - [網頁伺服器]   > [應用程式開發]   > [ASP.NET 4.5]   

        安裝 ASP.NET 4.5 時會安裝 .NET Framework 4.5。 安裝 .NET Framework 4.5 時，請安裝核心 [.NET Framework 4.5]  功能、[ASP.NET 4.5]  與 [WCF 服務]   > [HTTP 啟動]  功能。  

      - [管理工具]   > [IIS 6 管理相容性]   > [IIS 6 Metabase 相容性]   
      - [管理工具]   > [IIS 6 管理相容性]   > [IIS 6 WMI 相容性]   
      - 在伺服器上，新增 NDES 服務帳戶作為本機 **IIS_IUSR** 群組的成員。  

2. 在裝載 NDES 服務的電腦上，於提升權限的命令提示字元中執行下列命令。 下列命令會設定 NDES 服務帳戶的 SPN：  

   `setspn -s http/<DNS name of the computer that hosts the NDES service> <Domain name>\<NDES Service account name>`
   
   例如，如果裝載 NDES 服務的電腦名稱為 **Server01**，您的網域是 **Contoso.com**，且服務帳戶是 **NDESService**，請使用：  

   `setspn –s http/Server01.contoso.com contoso\NDESService`  

### <a name="configure-the-ndes-service"></a>設定 NDES 服務  

1. 在裝載 NDES 服務的電腦上，開啟 [AD CS 設定精靈]  ，然後進行下列更新：  

   > [!TIP]  
   > 如果您是從上一個程序繼續進行，並按一下**在目的地伺服器上設定 Active Directory 憑證服務**連結，則此精靈應該已經開啟。 否則，開啟 [伺服器管理員] 來存取 Active Directory 憑證服務的部署後組態。  

   - 在 [角色服務]  中選取 [網路裝置註冊服務]  。
   - 在 [NDES 的服務帳戶]  中指定 NDES 服務帳戶。
   - 在 [NDES 的 CA]  中，按一下 [選取]  ，然後選取您設定憑證範本的發行 CA。
   - 在 [NDES 的密碼編譯]  中，設定符合您公司需求的金鑰長度。
   - 在 [確認]  中，選取 [設定]  來完成精靈。

2. 精靈完成之後，在裝載 NDES 服務的電腦上更新下列登錄機碼：  
   `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Cryptography\MSCEP\`  

   若要更新此機碼，請指出憑證範本的 [用途]  (可以在其 [要求處理]  索引標籤上找到)。 接著，使用您在[建立憑證範本](#create-the-scep-certificate-template)時所指定的憑證範本名稱 (而非範本的顯示名稱) 來取代現有資料，以更新對應的登錄項目。  

   下表會將憑證範本目的對應到登錄中的值：
   
   |憑證範本目的 (在 [處理要求] 索引標籤上)|要編輯的登錄值|SCEP 設定檔的 Intune 管理主控台中看到的值|
   |------------------------|-------------------------|---|
   |簽章               |SignatureTemplate        |數位簽章 |
   |加密              |EncryptionTemplate       |金鑰加密  |
   |簽章和加密|GeneralPurposeTemplate   |金鑰加密<br/>數位簽章 |  

   例如，如果您的憑證範本目的是 [加密]  ，則請將 **EncryptionTemplate** 值編輯為憑證範本的名稱。  

3. 設定 IIS 要求篩選，以在 IIS 中為 NDES 服務所接收的長 URL (查詢) 新增支援。
   1. 在 IIS 管理員中，選取 [預設的網站]   > [要求篩選]   > [編輯功能設定]  以開啟 [編輯要求篩選設定]  頁面。  

   2. 進行以下設定：  
      - **URL 長度上限 (位元組)** = 65534  
      - **查詢字串上限 (位元組)** = 65534  
   3. 選取 [確定]  以儲存這項設定並關閉 IIS 管理員。  
   4. 檢視下列登錄機碼以確認其具有已指出的值來驗證此設定：  

      `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\HTTP\Parameters`    

      下列值設定為 DWORD 項目：  
      - 名稱：**MaxFieldLength**，具有十進位值 **65534**  
      - 名稱：**MaxRequestBytes**，具有十進位值 **65534**  
4. 重新啟動裝載 NDES 服務的伺服器。 請勿使用 **iisreset**，iireset 不會完成所需的變更。  

5. 瀏覽至 *http://* Server_FQDN */certsrv/mscep/mscep.dll*。 您應該會看到與下圖類似的 NDES 頁面︰  

   ![測試 NDES](./media/certificates-scep-configure/scep-ndes-url.png)
  
   如果網址傳回 **503 服務無法使用**，請檢查電腦事件檢視器。 當應用程式集區因 [NDES 服務帳戶權限](#accounts)遺失而停止時，通常會發生此錯誤。  
  
### <a name="install-and-bind-certificates-on-the-server-that-hosts-ndes"></a>在裝載 NDES 的伺服器上安裝並繫結憑證  
> [!TIP]  
> 在下列程序中，您可以將單一憑證用於「伺服器驗證」  和「用戶端驗證」  (當該憑證設定為符合這兩種用途的準則時)。 下列程序的步驟 1 和 3，將描述每種用途的準則。  

1. 從您的內部 CA 或公用 CA 要求**伺服器驗證**憑證，然後將憑證安裝在伺服器上。  

   如果伺服器針對單一網路位址使用外部與內部名稱，則伺服器驗證憑證必須有：  

   - 外部公開伺服器名稱的**主體名稱**。
   - 包含內部伺服器名稱的**主體別名**。  

2. 在 IIS 中繫結伺服器驗證憑證：  
  
   1. 安裝伺服器驗證憑證之後，請開啟 [IIS 管理員]  並選取 [預設的網站]  。 在 [動作]  窗格中，選取 [繫結]  。  
   1. 選取下 [新增]  ，將 [類型]  設定為 [https]  ，然後確認連接埠是 [443]  。  
   1. 針對 [SSL 憑證]  ，指定伺服器驗證憑證。  
 
3. 在 NDES 伺服器上，從內部 CA 或公開憑證授權單位，要求並安裝 **用戶端驗證** 憑證。  

   用戶端驗證憑證必須具有下列屬性：  
   - **增強金鑰使用方法**：此值必須包含**用戶端驗證**。  
   - **主體名稱**：此值必須等於您要安裝憑證之伺服器 (NDES 伺服器) 的 DNS 名稱。  

4. 裝載 NDES 服務的伺服器現在已準備好支援 Intune 憑證連接器。  

## <a name="install-the-intune-certificate-connector"></a>安裝 Intune 憑證連接器  
Microsoft Intune 憑證連接器會安裝在執行 NDES 服務的伺服器上。 不支援在與您的憑證授權單位 (CA) 相同伺服器上使用 NDES 或 Intune 憑證連接器。  

安裝憑證連接器：  
1. 使用具有 Intune 權限的帳戶來登入 [Intune 入口網站](https://aka.ms/intuneportal)。  

2. 選取 [裝置設定]   > [憑證授權單位]   > [新增]  。  

3. 下載並儲存 SCEP 檔案的連接器。 請將它儲存到可從將安裝連接器的伺服器存取的位置。

   ![ConnectorDownload](./media/certificates-scep-configure/download-certificates-connector.png)

4. 下載完成之後，前往裝載網路裝置註冊服務 (NDES) 角色的伺服器。 然後：  

   1. 確認已安裝 .NET 4.5 Framework，這對 Intune 憑證連接器是必要的。 Windows Server 2012 R2 及更新版本會自動隨附 .NET 4.5 Framework。  
   2. 執行安裝程式 (**NDESConnectorSetup.exe**)。 安裝程式也會安裝 NDES 和 IIS 憑證登錄點 (CRP) Web 服務的原則模組。 CRP Web 服務 *CertificateRegistrationSvc* 會在 IIS 中以應用程式的形式執行。  

      - 當您為獨立版 Intune 安裝 NDES 時，CRP 服務會自動與 Certificate Connector 一起安裝。 
      - 當您使用 Intune 搭配 Configuration Manager 時，將憑證註冊點安裝為 Configuration Manager 站台系統角色。  
5. 當系統提示您提供憑證連接器的用戶端憑證時，請選擇 [選取]  ，並選取您在本文先前[在裝載 NDES 的伺服器上安裝並繫結憑證](#install-and-bind-certificates-on-the-server-that-hosts-ndes)程序中步驟 #3 期間在 NDES 伺服器上所安裝**用戶端驗證**憑證。  

   選取用戶端驗證憑證之後，您會回到 [Microsoft Intune Certificate Connector 的用戶端憑證]  介面。 雖然不會顯示您選取的憑證，但請選取 [下一步]  以檢視該憑證的屬性。 選取 [下一步]  [安裝]  。

6. 在精靈完成後，但在關閉精靈之前，按一下 [啟動 Certificate Connector UI]  。  

   如果您在啟動 Certificate Connector UI 之前關閉精靈，您可以藉由執行下列命令重新加以開啟：<安裝路徑>\NDESConnectorUI\NDESConnectorUI.exe 

7. 在 **Certificate Connector** UI 中：  
   1. 選取 [登入]  並輸入您的 Intune 服務系統管理員認證，或擁有全域系統管理權限的租用戶管理員認證。  
   2. 您所使用帳戶必須獲指派有效的 Intune 授權。  
   3. 在您登入之後，Intune 憑證連接器會從 Intune 下載憑證。 此憑證用於連接器與 Intune 之間的驗證。 如果您使用的帳戶沒有 Intune 授權，連接器 (NDESConnectorUI) 就無法從 Intune 取得憑證。  

      如果您的組織使用 Proxy 伺服器，而且 NDES 伺服器需要該 Proxy 以存取網際網路，請選取 [使用 Proxy 伺服器]  。 然後輸入 Proxy 伺服器名稱、連接埠，以及用以連線的帳戶認證。  

    4. 選取 [進階]  索引標籤，然後輸入對您的發行憑證授權單位具有 [發行及管理憑證]  權限的帳戶認證。 **套用**您的變更。  

    5. 您現在可以關閉 Certificate Connector UI。  

8. 開啟命令提示字元，輸入 **services.msc** **Enter**。 以滑鼠右鍵按一下 [Intune 連接器服務]   > [重新啟動]  。


若要驗證服務正在執行，請開啟瀏覽器並輸入下列 URL。 這應該會傳回 **403** 錯誤：`https://<FQDN_of_your_NDES_server>/certsrv/mscep/mscep.dll`  

> [!NOTE]  
> Intune 憑證連接器支援 TLS 1.2。 如果裝載連接器的伺服器支援 TLS 1.2，則會使用 TLS 1.2。 如果伺服器不支援 TLS 1.2，則會使用 TLS 1.1。 目前，使用 TLS 1.1 在裝置與伺服器之間進行驗證。

## <a name="next-steps"></a>後續步驟

[建立 SCEP 憑證設定檔](certificates-profile-scep.md)  
[針對 Intune 憑證連接器的問題進行疑難排解](troubleshoot-certificate-connector-events.md)

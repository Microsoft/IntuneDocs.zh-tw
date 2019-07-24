---
title: 搭配 Microsoft Intune 使用 SCEP 憑證 - Azure | Microsoft Docs
description: 若要在 Microsoft Intune 中使用 SCEP 憑證，請設定您的內部部署 AD 網域、建立憑證授權單位、設定 NDES 伺服器，並安裝 Intune 憑證連接器。 接著，建立 SCEP 憑證設定檔，然後將此設定檔指派給群組。 此外，請參閱不同的事件識別碼與其描述，以及 Intune 連接器服務的診斷碼。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/28/2019
ms.topic: article
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b073047455cd21dc3ffe5efcb52f51584db5ff30
ms.sourcegitcommit: bd09decb754a832574d7f7375bad0186a22a15ab
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/19/2019
ms.locfileid: "68353770"
---
# <a name="configure-and-use-scep-certificates-with-intune"></a>搭配 Intune 設定及使用 SCEP 憑證

此文章說明如何搭配 Intune 設定基礎結構，並建立及指派簡單憑證註冊通訊協定 (SCEP) 憑證設定檔。

## <a name="configure-on-premises-infrastructure"></a>設定內部部署基礎結構

- **Active Directory 網域**：本節所列的所有伺服器 (除了 Web 應用程式 Proxy 伺服器) 均須加入 Active Directory 網域。

- **憑證授權單位** (CA)：必須是在企業版 Windows Server 2008 R2 或更新版本上執行的 Microsoft 企業憑證授權單位 (CA)。 不支援獨立 CA。 如需詳細資料，請參閱[安裝憑證授權單位 (機器翻譯)](https://technet.microsoft.com/library/jj125375.aspx)。
    如果您的 CA 執行 Windows Server 2008 R2，您必須 [從 KB2483564 安裝 Hotfix](http://support.microsoft.com/kb/2483564/)。

- **NDES 伺服器**：在 Windows Server 2012 R2 或更新版本上，設定「網路裝置註冊服務」(NDES) 伺服器角色。 Intune 不支援在同時執行企業 CA 的伺服器上使用 NDES。 請參閱[網路裝置註冊服務指導方針](https://technet.microsoft.com/library/hh831498.aspx)，以取得有關如何設定 Windows Server 2012 R2 來裝載 NDES 的指示。
NDES 伺服器必須加入與企業 CA 相同樹系內的網域。 在[使用原則模組和網路裝置註冊服務](https://technet.microsoft.com/library/dn473016.aspx)中可以找到將 NDES 伺服器部署至不同樹系、隔離網路或內部網域的詳細資訊。 您無法使用已經由另一個 MDM 使用的 NDES 伺服器。

- **Microsoft Intune 憑證連接器**：在 Intune 入口網站中，移至 [裝置設定]   > [憑證連接器]   > [新增]  ，並遵循「安裝 SCEP 連接器的步驟」  。 使用入口網站中的下載連結，開始下載憑證連接器安裝程式 **NDESConnectorSetup.exe**。  您將以 NDES 角色在伺服器上執行此安裝程式。  

這個 NDES 憑證連接器也支援聯邦資訊處理標準 (FIPS) 模式。 FIPS 並非必要，但啟用時可發出及撤銷憑證。

- **Web 應用程式 Proxy 伺服器** (選擇性)：使用執行 Windows Server 2012 R2 或更新版本的伺服器作為「Web 應用程式 Proxy」(WAP) 伺服器。 此組態：
  - 允許裝置使用網際網路連線接收憑證。
  - 是裝置連線透過網際網路來接收和更新憑證時的安全性建議。
  
- **Azure AD 應用程式 Proxy** (選擇性)：可使用「Azure AD 應用程式 Proxy」將 NDES 伺服器發佈至網際網路，而不使用專用的「Web 應用程式 Proxy (WAP) 伺服器」來發佈。 如需詳細資訊，請參閱[如何為內部部署應用程式提供安全的遠端存取](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy)。

### <a name="additional"></a>Additional

- 裝載 WAP 伺服器 [必須安裝更新](http://blogs.technet.com/b/ems/archive/2014/12/11/hotfix-large-uri-request-in-web-application-proxy-on-windows-server-2012-r2.aspx) ，以啟用網路裝置註冊服務所使用之長 URL 的支援。 此更新隨附於 [2014 年 12 月更新彙總套件](http://support.microsoft.com/kb/3013769)，或個別提供於 [KB3011135](http://support.microsoft.com/kb/3011135)。
- WAP 的伺服器必須有 SSL 憑證，該憑證符合發佈給外部用戶端的名稱，並且信任 NDES 伺服器上使用的 SSL 憑證。 這些憑證讓 WAP 伺服器能從用戶端終止 SSL 連線，以及建立與 NDES 伺服器的新 SSL 連線。

如需詳細資訊，請參閱[規劃 WAP 的憑證](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn383650(v=ws.11)#plan-certificates) \(英文\) 和 [WAP 伺服器的一般相關資訊](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn584113(v=ws.11)) \(英文\)。

### <a name="network-requirements"></a>網路需求

如果您未使用反向 Proxy (例如 WAP 或 Azure AD App Proxy)，則允許連接埠 443 上從網際網路之所有主機 /IP 位址到 NDES 伺服器的 TCP 流量。

允許 NDES 伺服器與任何支援基礎結構之間所需的所有連接埠和通訊協定。 例如，NDES 伺服器必須與 CA、DNS 伺服器、Configuration Manager 伺服器、網域控制站，以及環境內可能存在的其他服務進行通訊。

強烈建議您透過反向 Proxy 發佈 NDES 伺服器，例如 [Azure AD 應用程式 Proxy](https://azure.microsoft.com/documentation/articles/active-directory-application-proxy-publish/)、[Web 存取 Proxy](https://technet.microsoft.com/library/dn584107.aspx)，或是協力廠商 Proxy。

### <a name="certificates-and-templates"></a>憑證和範本  

|物件|詳細資料|
|----------|-----------|
|**憑證範本**|在發行 CA 上設定此範本。|
|**用戶端驗證憑證**|自發行 CA 或公用 CA 所要求的憑證，您會將它安裝於 NDES 伺服器上。|
|**伺服器驗證憑證**|自發行 CA 或公用 CA 所要求的憑證，您會在 NDES 伺服器的 IIS 中安裝並繫結此 SSL 憑證。 如果憑證具有用戶端和伺服器的驗證金鑰使用方式集合 (**增強金鑰使用方法**)，則您可以使用相同的憑證。|
|**可信任的根 CA 憑證**|您可以從根 CA 或信任根 CA 的任何裝置，將此憑證匯出為 **.cer** 檔案。 然後，使用信任的 CA 憑證設定檔將其指派至使用者、裝置或兩者。<br /> **請注意：<br />指派 SCEP 憑證設定檔時，請務必將您的 SCEP 憑證設定檔中參考的「受信任根憑證設定檔」  指派給相同的使用者或裝置群組。若要建立此設定檔，請參閱[建立受信任的憑證設定檔](certficates-pfx-configure.md#create-a-trusted-certificate-profile)，其記載於與 PKCS 憑證設定檔有關的文章中。** <br/><br />您會針對每個作業系統平台使用單一受信任根 CA 憑證，並將它關聯至您建立的每個受信任根憑證設定檔。 <br /><br />您可以在需要時使用其他受信任根 CA 憑證。 比方說，當您需要向 CA 提供信任，好讓它為您簽署 Wi-Fi 存取點的伺服器驗證憑證時，您可能就會這麼做。|

### <a name="accounts"></a>帳戶

|名稱|詳細資料|
|--------|-----------|
|**NDES 服務帳戶**|輸入網域使用者帳戶以做為 NDES 服務帳戶。 |

## <a name="configure-your-infrastructure"></a>設定基礎結構
在您設定憑證設定檔前，必須先完成下列步驟。 執行這些步驟需要對 Windows Server 2012 R2 或更新版本以及 Active Directory 憑證服務 (ADCS) 有一定程度的了解：

### <a name="step-1---create-an-ndes-service-account"></a>步驟 1：建立 NDES 服務帳戶

建立網域使用者帳戶以做為 NDES 服務帳戶。 在您安裝及設定 NDES 之前，會在發行 CA 上設定範本時輸入此帳戶。 請確定使用者具有預設權限：[本機登入]  、[以服務方式登入]  和 [以批次工作登入]  權限。 某些組織擁有停用這些權限的強化原則。

### <a name="step-2---configure-certificate-templates-on-the-certification-authority"></a>步驟 2：設定憑證授權單位上的憑證範本
在此步驟中，您將：

- 設定 NDES 的憑證範本
- 發行 NDES 的憑證範本

#### <a name="configure-the-certification-authority"></a>設定憑證授權單位

1. 以企業系統管理員身分登入。

2. 在發行 CA 上，使用 [憑證範本] 嵌入式管理單元來建立新的自訂範本。 或者，複製現有範本，然後更新現有範本 (例如使用者範本) 以搭配 NDES 使用。

   >[!NOTE]
   > NDES 憑證範本必須根據 v2 憑證範本 (具有 Windows 2003 相容性)。

   範本必須要有下列組態：

   - 在 [一般]  中：
   
       - 確認**未**核取 [將憑證發佈到 Active Directory]  屬性。
       - 輸入範本的易記「範本顯示名稱」  。

   - 在 [主體名稱]  中，選取 [在要求中提供]  (安全性由 NDES 的 Intune 原則模組加強)。

   - 在 [延伸]  索引標籤上，確認 [應用程式原則描述]  包含 [用戶端驗證]  。

     > [!IMPORTANT]
     > 針對 iOS 與 macOS 憑證範本，請在 [延伸]  索引標籤上編輯 [金鑰使用方法]  ，並確認未選取 [簽章是原件證明]  。

   - 在 [安全性]  中，新增 NDES 服務帳戶，並提供其 [註冊]  範本的權限。 建立 SCEP 設定檔的 Intune 系統管理員需要**讀取** 權限，讓他們可以在建立 SCEP 設定檔時瀏覽至範本。

     > [!NOTE]
     > 若要撤銷憑證，NDES 服務帳戶需要有憑證授權單位的「發行與管理憑證」  權限。 若要委派此權限，請開啟 [憑證授權單位] 管理主控台，並以滑鼠右鍵按一下憑證授權單位名稱。 然後，在 [安全性] 索引標籤中，新增或選取帳戶，然後選取 [發行與管理憑證]  核取方塊。


3. 檢閱範本 [一般]  索引標籤上的 [有效期間]  。 根據預設，Intune 使用範本中所設定的值。 不過，您可以設定 CA 以允許要求者輸入不同的值，然後就可以從 Intune 系統管理員主控台內設定該值。 如果您想要一律使用範本中的值，請略過此步驟中的其餘部分。

   > [!IMPORTANT]
   > iOS 和 macOS 一律會使用範本中的值，而不管您所做的其他組態設定。

範例範本設定：

![範本, 處理要求索引標籤](./media/scep_ndes_request_handling.png)

![範本, 主體名稱索引標籤](./media/scep_ndes_subject_name.jpg)

![範本, 安全性索引標籤](./media/scep_ndes_security.jpg)

![範本, 延伸索引標籤](./media/scep_ndes_extensions.jpg)

![範本, 發行需求索引標籤](./media/scep_ndes_issuance_reqs.jpg)

> [!IMPORTANT]
> 針對應用程式原則，僅新增所需的應用程式原則。 向您的安全性系統管理員確認您的選擇。

設定 CA 以允許要求者輸入有效期間：

1. 在 CA 上執行下列命令：
   - **certutil -setreg Policy\EditFlags +EDITF_ATTRIBUTEENDDATE**
   - **net stop certsvc**
   - **net start certsvc**

2. 在發行的 CA 上使用 [憑證授權單位] 嵌入式管理單元來發行憑證範本。
   選取 [憑證範本]  節點，按一下 [動作]   > [新增]   > [要發出的憑證範本]  ，然後選取您在步驟 2 中建立的範本。

3. 檢視 [憑證範本]  資料夾下的發行範本來加以驗證。

### <a name="step-3---configure-prerequisites-on-the-ndes-server"></a>步驟 3：設定 NDES 伺服器上的必要條件
在此步驟中，您將：

- 將 NDES 加入至 Windows Server 並設定 IIS 以支援 NDES
- 將 NDES 服務帳戶加入至 IIS_IUSR 群組
- 設定 NDES 服務帳戶的服務主體名稱 (SPN)

1. 在裝載 NDES 的伺服器上，以**企業系統管理員**的身分登入，然後使用[新增角色及功能精靈](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831809(v=ws.11))來安裝 NDES：

   1. 在精靈中，選取 [Active Directory 憑證服務]  以存取 AD CS 角色服務。 選取 [網路裝置註冊服務]  ，取消核取 [憑證授權單位]  ，然後完成精靈。

      > [!TIP]
      > 在 [安裝進度]  中，不要核取 [關閉]  。 相反地，請選取 [設定目的地伺服器上的 Active Directory 憑證服務]  連結。 [AD CS 設定精靈]  隨即開啟，讓您用於下一個步驟。 [AD CS 設定] 開啟之後，您可以關閉 [新增角色及功能精靈]。

   2. 當 NDES 加入至伺服器時，精靈也會安裝 IIS。 請確認 IIS 具有下列設定：

       - [Web 伺服器]   > [安全性]   > [要求篩選] 

       - [網頁伺服器]   > [應用程式開發]   > [ASP.NET 3.5]  

            安裝 ASP.NET 3.5 時會安裝 .NET Framework 3.5。 安裝 .NET Framework 3.5 時，請安裝核心 [.NET Framework 3.5]  功能和 [HTTP 啟動]  。

       - [網頁伺服器]   > [應用程式開發]   > [ASP.NET 4.5]  

            安裝 ASP.NET 4.5 時會安裝 .NET Framework 4.5。 安裝 .NET Framework 4.5 時，請安裝核心 [.NET Framework 4.5]  功能、[ASP.NET 4.5]  與 [WCF 服務]   > [HTTP 啟動]  功能。

       - [管理工具]   > [IIS 6 管理相容性]   > [IIS 6 Metabase 相容性] 

       - [管理工具]   > [IIS 6 管理相容性]   > [IIS 6 WMI 相容性] 

       - 在伺服器上，新增 NDES 服務帳戶作為本機 **IIS_IUSR** 群組的成員。

2. 在提升權限的命令提示字元中，執行下列命令來設定 NDES 服務帳戶的 SPN：

    `setspn -s http/<DNS name of NDES Server> <Domain name>\<NDES Service account name>`

    例如，如果 NDES 伺服器的名稱為 **Server01**，您的網域是 **Contoso.com**，而且服務帳戶是 **NDESService**，請使用：

    `setspn –s http/Server01.contoso.com contoso\NDESService`

### <a name="step-4---configure-ndes-for-use-with-intune"></a>步驟 4：設定 NDES 以搭配 Intune 使用
在此步驟中，您將：

- 設定 NDES 以便用於發行 CA
- 在 IIS 中繫結伺服器驗證 (SSL) 憑證
- 設定 IIS 中的要求篩選

1. 在 NDES 伺服器上，開啟 [AD CS 設定] 精靈，然後進行下列設定：

    > [!TIP]
    > 如果您按一下上一個步驟中的連結，此精靈已經開啟。 否則，開啟 [伺服器管理員] 來存取 Active Directory 憑證服務的部署後組態。

   - 在 [角色服務]  中，選取 [網路裝置註冊服務] 
   - 在 [NDES 的服務帳戶]  中，輸入 NDES 服務帳戶
   - 在 [NDES 的 CA]  中，按一下 [選取]  ，然後選取您設定憑證範本的發行 CA
   - 在 [NDES 的密碼編譯]  中，設定符合您公司需求的金鑰長度。
   - 在 [確認]  中，選取 [設定]  來完成精靈。

2. 在精靈完成之後，在 NDES 伺服器上更新下列登錄機碼：

    `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Cryptography\MSCEP\`

    若要更新此機碼，請指出憑證範本的 [目的]  (可以在其 [要求處理]  索引標籤上找到)。 接著，透過使用您在步驟 2 中指定的憑證範本名稱 (而非範本的顯示名稱) 來取代現有資料，以更新對應的登錄項目。 下表會將憑證範本目的對應到登錄中的值：

    |憑證範本目的 (在 [處理要求] 索引標籤上)|要編輯的登錄值|SCEP 設定檔的 Intune 管理主控台中看到的值|
    |---|---|---|
    |簽章|SignatureTemplate|數位簽章|
    |加密|EncryptionTemplate|金鑰加密|
    |簽章和加密|GeneralPurposeTemplate|金鑰加密<br/>數位簽章|

    例如，如果您的憑證範本目的是 [加密]  ，則請將 **EncryptionTemplate** 值編輯為憑證範本的名稱。

3. NDES 伺服器會收到長的 URL (查詢)，而這需要您新增兩個登錄項目︰


   |                        位置                        |      值      | 類型  |      資料       |
   |--------------------------------------------------------|-----------------|-------|-----------------|
   | HKLM\SYSTEM\CurrentControlSet\Services\HTTP\Parameters | MaxFieldLength  | DWORD | 65534 (十進位) |
   | HKLM\SYSTEM\CurrentControlSet\Services\HTTP\Parameters | MaxRequestBytes | DWORD | 65534 (十進位) |

4. 在 IIS 管理員中，選取 [預設的網站]   > [要求篩選]   > [編輯功能設定]  。 將 [URL 長度上限]  與 [查詢字串上限]  變更為 *65534*，如下所示：

    ![IIS URL 和查詢長度上限](./media/SCEP_IIS_max_URL.png)

5. 重新啟動伺服器。 請勿使用 **iisreset**；它無法完成這些變更。
6. 瀏覽至 `http://*FQDN*/certsrv/mscep/mscep.dll` 。 您應該會看到與下面類似的 NDES 頁面︰

    ![測試 NDES](./media/SCEP_NDES_URL.png)

    如果您收到「503 服務無法使用」  ，請檢查事件檢視器。 因為遺失 NDES 使用者的權限，所以可能已停止應用程式集區。 步驟 1 會說明這些權限。

#### <a name="install-and-bind-certificates-on-the-ndes-server"></a>在 NDES 伺服器上安裝並繫結憑證

1. 在 NDES 伺服器上，要求並安裝來自內部 CA 或公用 CA 的 **伺服器驗證** 憑證。 然後將此 SSL 憑證繫結在 IIS 中。

    > [!TIP]
    > 在 IIS 中繫結 SSL 憑證之後，安裝用戶端驗證憑證。 此憑證可以由 NDES 伺服器所信任的任何 CA 發出。 如果憑證具有用戶端和伺服器的驗證金鑰使用方式集合 (**增強金鑰使用方法**)，就可以使用相同的憑證。 請檢閱以下的步驟，以取得這些驗證憑證的相關資訊。

   1. 取得伺服器驗證憑證之後，請開啟 [IIS 管理員]  並選取 [預設的網站]  。 在 [動作]  窗格中，選取 [繫結]  。

   2. 選取下 [新增]  ，將 [類型]  設定為 [https]  ，然後確認連接埠是 [443]  。 獨立版 Intune 只支援連接埠 443。

   3. 針對 [SSL 憑證]  ，輸入伺服器驗證憑證。

      > [!NOTE]
      > 若 NDES 伺服器針對單一網路位址使用外部與內部名稱，則伺服器驗證憑證必須有：
      > - 具有外部公開伺服器名稱的**主體名稱**
      > - 包含內部伺服器名稱的**主體別名**

2. 在 NDES 伺服器上，從內部 CA 或公開憑證授權單位，要求並安裝 **用戶端驗證** 憑證。 如果伺服器驗證憑證具備兩種功能，則此憑證可以是與該憑證相同的憑證。

    用戶端驗證憑證必須具有下列屬性：

    - **增強金鑰使用方法**：此值必須包含**用戶端驗證**

    - **主體名稱**：此值必須等於您要安裝憑證之伺服器 (NDES 伺服器) 的 DNS 名稱

#### <a name="configure-iis-request-filtering"></a>設定 IIS 要求篩選

1. 在 NDES 伺服器上，開啟 [IIS 管理員]  ，在 [連線]  窗格中選取 [預設的網站]  ，然後開啟 [要求篩選]  。

2. 選取 [編輯功能設定]  ，然後設定下列值：

    - **查詢字串 (位元組)**  = **65534**
    - **URL 長度上限 (位元組)**  = **65534**

3. 檢閱下列登錄機碼：

    `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\HTTP\Parameters`

    確認下列值設定為 DWORD 項目：

    - 名稱：**MaxFieldLength**，具有十進位值 **65534**
    - 名稱：**MaxRequestBytes**，具有十進位值 **65534**

4. 重新啟動 NDES 伺服器。 伺服器現在已準備好支援 Certificate Connector。

### <a name="step-5---enable-install-and-configure-the-intune-certificate-connector"></a>步驟 5：啟用、安裝及設定 Intune 憑證連接器
在此步驟中，您將：

- 啟用 Intune 中的 NDES 支援。
- 在您環境中裝載網路裝置註冊服務 (NDES) 角色的伺服器上，下載、安裝及設定憑證連接器。 若要增加您組織的 NDES 實作規模，您可以在每部 NDES 伺服器上，搭配 Microsoft Intune 憑證連接器安裝多部 NDES 伺服器。

#### <a name="download-install-and-configure-the-certificate-connector"></a>下載、安裝及設定憑證連接器

> [!IMPORTANT] 
> Microsoft Intune Certificate Connector **必須**安裝在個別的 Windows 伺服器中。 它不能安裝在發行的授權憑證單位 (CA) 上。 它也**必須**安裝在與網路裝置註冊服務 (NDES) 角色相同的伺服器上。

1. 登入 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
2. 選取 [裝置設定]   > [憑證連接器]   > [新增]  。
3. 下載並儲存 SCEP 檔案的連接器。 請將它儲存要安裝連接器之 NDES 伺服器所能存取的位置。

   ![ConnectorDownload](./media/certificates-scep-configure/download-certificates-connector.png)


4. 下載完成之後，前往裝載網路裝置註冊服務 (NDES) 的 NDES 伺服器。 然後：

    1. 確定已安裝 .NET 4.5 Framework，這對 NDES 憑證連接器是必要的。 Windows Server 2012 R2 及更新版本會自動隨附 .NET 4.5 Framework。
    2. 使用具有伺服器系統管理權限的帳戶來執行安裝程式 (**NDESConnectorSetup.exe**)。 安裝程式也會安裝 NDES 和 CRP Web 服務的原則模組。 CRP Web 服務 CertificateRegistrationSvc 會以 IIS 中的應用程式方式執行。

    > [!NOTE]
    > 當您為獨立版 Intune 安裝 NDES 時，CRP 服務會自動與 Certificate Connector 一起安裝。 當您使用 Intune 搭配 Configuration Manager 時，將憑證註冊點安裝為個別的網站系統角色。

5. 當系統提示您提供憑證連接器的用戶端憑證時，請選擇 [選取]  ，然後選取您在步驟 4 中，於 NDES 伺服器上安裝的**用戶端驗證**憑證。

    選取用戶端驗證憑證之後，您會回到 [Microsoft Intune Certificate Connector 的用戶端憑證]  介面。 雖然未顯示您選取的憑證，請選取 [下一步]  以檢視該憑證的屬性。 選取 [下一步]  [安裝]  。

    > [!IMPORTANT]
    > 在裝載 Intune 憑證連接器的 [NDES 伺服器上必須停用](https://technet.microsoft.com/library/cc775800(v=WS.10).aspx) Internet Explorer 增強式安全性設定。

6. 在精靈完成後，但在關閉精靈之前，按一下 [啟動 Certificate Connector UI]  。

    > [!TIP]
    > 如果您在啟動 Certificate Connector UI 之前關閉精靈，您可以藉由執行下列命令重新加以開啟：
    >
    > <安裝路徑>\NDESConnectorUI\NDESConnectorUI.exe

7. 在 **Certificate Connector** UI 中：

    選取 [登入]  並輸入您的 Intune 服務系統管理員認證，或擁有全域系統管理權限的租用戶管理員認證。 在您登入之後，Intune 憑證連接器會從 Intune 下載憑證。 此憑證用於連接器與 Intune 之間的驗證。

    > [!IMPORTANT]
    > 使用者帳戶必須指派有效的 Intune 授權。 如果使用者帳戶沒有有效的 Intune 授權，則 NDESConnectorUI.exe 就會失敗。

    如果您的組織使用 Proxy 伺服器，而且 NDES 伺服器需要該 Proxy 以存取網際網路，請選取 [使用 Proxy 伺服器]  。 然後輸入 Proxy 伺服器名稱、連接埠，以及用以連線的帳戶認證。

    選取 [進階]  索引標籤，然後輸入對您的發行憑證授權單位具有 [發行及管理憑證]  權限的帳戶認證。 **套用**您的變更。 如果您在[設定您的憑證授權單位](#configure-the-certification-authority)時，將此權限委派給您的 NDES 服務帳戶，請在此指定該帳戶。 

    您現在可以關閉 Certificate Connector UI。

8. 開啟命令提示字元，輸入 **services.msc** **Enter**。 以滑鼠右鍵按一下 [Intune 連接器服務]   > [重新啟動]  。

若要驗證服務正在執行，請開啟瀏覽器並輸入下列 URL。 這應該會傳回 **403** 錯誤：

`http://<FQDN_of_your_NDES_server>/certsrv/mscep/mscep.dll`

> [!NOTE]
> NDES 憑證連接器隨附 TLS 1.2 支援。 因此，如果安裝 NDES 憑證連接器的伺服器支援 TLS 1.2，則會使用 TLS 1.2。 如果伺服器不支援 TLS 1.2，則會使用 TLS 1.1。 目前，使用 TLS 1.1 在裝置與伺服器之間進行驗證。

## <a name="create-a-scep-certificate-profile"></a>建立 SCEP 憑證設定檔

1. 登入 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
2. 選取 [裝置設定]   > [設定檔]   > [建立設定檔]  。
3. 輸入 SCEP 憑證設定檔的 [名稱]  與 [描述]  。
4. 從 [平台]  下拉式清單中，選取此 SCEP 憑證的裝置平台。 您目前可選取下列平台之一，進行裝置限制設定︰
   - **Android**
   - **Android Enterprise**
   - **iOS**
   - **macOS**
   - **Windows Phone 8.1**
   - **Windows 8.1 及更新版本**
   - **Windows 10 及更新版本**
5. 從 [設定檔類型]  下拉式清單中，選取 [SCEP 憑證]  。
6. 輸入下列設定：

   - **憑證類型**：針對使用者憑證，請選擇 [使用者]  。 [使用者]  憑證類型可在憑證的主旨與 SAN 中包含使用者屬性和裝置屬性。  針對無使用者裝置之類的案例 (例如 kiosk)，或針對 Windows 裝置，選擇 [裝置]  ，並將憑證放在本機電腦的憑證存放區。 [裝置]  憑證只能在憑證的主旨與 SAN 中包含裝置屬性。  提供下列平台可用的 [裝置]  憑證：  
     - Android 企業 - 工作設定檔
     - iOS
     - macOS
     - Windows 8.1 及更新版本
     - Windows 10 及更新版本


   - **主體名稱格式**：選取 Intune 在憑證要求中自動建立主體名稱的方式。 如果您選擇 [使用者]  憑證類型或 [裝置]  憑證類型，則選項會變更。 

        **使用者憑證類型**  

        您可以在主體名稱中包含使用者的電子郵件地址。 從下列選項進行選擇：

        - **未設定**
        - **一般名稱**
        - **包括電子郵件的一般名稱**
        - **一般名稱及電子郵件地址**
        - **IMEI (國際行動設備識別)**
        - **序號**
        - **自訂**：選取此選項時，會一併顯示 [自訂]  文字方塊。 您可以使用此欄位來輸入自訂主體名稱格式，包括變數。 自訂格式支援兩個變數：**一般名稱 (CN)** 和**電子郵件 (E)** 。 **一般名稱 (CN)** 可以設定為下列任何變數：

            - **CN={{UserName}}** ：使用者的使用者主體名稱，例如 janedoe@contoso.com
            - **CN={{AAD_Device_ID}}** ：您在 Azure Active Directory (AD) 中註冊裝置時所指派的識別碼。 此識別碼通常用於向 Azure AD 驗證。
            - **CN={{SERIALNUMBER}}** ：製造商通常用來識別裝置的唯一序號 (SN)
            - **CN={{IMEINumber}}** ：用來識別行動電話的「國際行動設備識別碼」(IMEI)
            - **CN={{OnPrem_Distinguished_Name}}** ：以逗號分隔的相對辨別名稱序列，例如 `CN=Jane Doe,OU=UserAccounts,DC=corp,DC=contoso,DC=com`

                若要使用 `{{OnPrem_Distinguished_Name}}` 變數，請務必將使用 [Azure AD Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect) 的 `onpremisesdistingishedname` 使用者屬性與 Azure AD 同步。

            - **CN={{onPremisesSamAccountName}}** ：系統管理員可以使用 Azure AD 連線到名為 `onPremisesSamAccountName` 的屬性，將 Active Directory 的 samAccountName 屬性與 Azure AD 同步。 Intune 可將該變數替換為 SCEP 憑證主體中憑證發行要求的一部分。  samAccountName 屬性是使用者登入名稱，用於支援舊版 Windows 客戶端和伺服器 (Windows 2000 以前的版本)。 使用者登入名稱的格式為：`DomainName\testUser`，或僅 `testUser`。

                若要使用 `{{onPremisesSamAccountName}}` 變數，請務必將使用 [Azure AD Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect) 的 `onPremisesSamAccountName` 使用者屬性與 Azure AD 同步。

            您可以結合使用一或多個這些變數和靜態字串，建立自訂的主體名稱格式，如下：  

            **CN={{UserName}},E={{EmailAddress}},OU=Mobile,O=Finance Group,L=Redmond,ST=Washington,C=US**

            在此範例中，您建立的主體名稱格式除了有 CN 與 E 變數之外，還會使用組織單位、組織、位置、狀態及國家/地區值的字串。 [CertStrToName 函式](https://msdn.microsoft.com/library/windows/desktop/aa377160.aspx) 說明此函式和它支援的字串。

        **裝置憑證類型**  

        當您使用 [裝置]  憑證類型時，也可以使用下列裝置憑證變數作為值：  

        ```
        "{{AAD_Device_ID}}",
        "{{Device_Serial}}",
        "{{Device_IMEI}}",
        "{{SerialNumber}}",
        "{{IMEINumber}}",
        "{{AzureADDeviceId}}",
        "{{WiFiMacAddress}}",
        "{{IMEI}}",
        "{{DeviceName}}",
        "{{FullyQualifiedDomainName}}",
        "{{MEID}}",
        ```

        您可以在自訂值文字方塊中以靜態文字新增這些變數。 例如，一般名稱可以新增為 `CN = {{DeviceName}}text`。

        > [!IMPORTANT]
        >  - 在主體的靜態文字中，未含括變數的大括弧 **{ }** 會解析為錯誤。 
        >  - 當您使用裝置憑證變數時，請用大括弧 **{ }** 將變數括住。
        >  - `{{FullyQualifiedDomainName}}` 只適用於 Windows 和已加入網域的裝置。 
        >  - 在裝置憑證的主體或 SAN 中使用 IMEI、序號和完整網域名稱等裝置屬性時，請留意這些屬性可能會被能夠存取該裝置的人員竄改。
        >  - 如果不支援指定的裝置變數，則設定檔不會安裝在裝置上。 例如，如果 SCEP 設定檔的主體名稱中使用 {{IMEI}}，但該設定檔指派給沒有 IMEI 編號的裝置，則設定檔安裝將會失敗。 


   - **主體別名**：輸入 Intune 在憑證要求中自動建立主體別名 (SAN) 值的方式。 如果您選擇 [使用者]  憑證類型或 [裝置]  憑證類型，則選項會變更。 

        **使用者憑證類型**  

        可以使用下列屬性：

        - 電子郵件地址
        - 使用者主體名稱 (UPN)

            例如，如果您選取使用者憑證類型，就可以在主體別名中包含使用者主體名稱 (UPN)。 如果用戶端憑證是用來驗證網路原則伺服器，您必須將主體別名設定為 UPN。 

        **裝置憑證類型**  

        您可以自訂的資料表格式文字方塊。 可以使用下列屬性：

        - DNS

        透過 [裝置]  憑證類型，您可以使用下列裝置憑證變數作為值：  

        ```
        "{{AAD_Device_ID}}",
        "{{Device_Serial}}",
        "{{Device_IMEI}}",
        "{{SerialNumber}}",
        "{{IMEINumber}}",
        "{{AzureADDeviceId}}",
        "{{WiFiMacAddress}}",
        "{{IMEI}}",
        "{{DeviceName}}",
        "{{FullyQualifiedDomainName}}",
        "{{MEID}}",
        ```

        您可以在自訂值文字方塊中以靜態文字新增這些變數。 例如，DNS 屬性可以新增為 `DNS name = {{AzureADDeviceId}}.domain.com`。

        > [!IMPORTANT]
        >  - 在 SAN 的靜態文字中，大括弧 **{ }** 、直立線符號 **|** 和分號 **;** 沒有作用。 
        >  - 當您使用裝置憑證變數時，請用大括弧 **{ }** 將變數括住。
        >  - `{{FullyQualifiedDomainName}}` 只適用於 Windows 和已加入網域的裝置。 
        >  - 在裝置憑證的主體或 SAN 中使用 IMEI、序號和完整網域名稱等裝置屬性時，請留意這些屬性可能會被能夠存取該裝置的人員竄改。
        >  - 如果不支援指定的裝置變數，則設定檔不會安裝在裝置上。 例如，如果 SCEP 設定檔的主體別名中使用 {{IMEI}}，但該設定檔指派給沒有 IMEI 編號的裝置，則設定檔安裝將會失敗。  

   - **憑證有效期間**：如果您已在發行 CA 上執行 `certutil - setreg Policy\EditFlags +EDITF_ATTRIBUTEENDDATE` 命令以允許使用自訂的有效期間，便可以輸入憑證到期之前的剩餘時間長度。<br>您可以輸入一個比憑證範本中指定的有效期間更低，而不是更高的值。 例如，如果憑證範本中的憑證有效期間為兩年，您可以輸入一年而不是五年的值。 該值也必須低於發行 CA 憑證的剩餘有效期。 
   - **金鑰儲存提供者 (KSP)** (Windows Phone 8.1、Windows 8.1、Windows 10)：輸入儲存憑證金鑰的位置。 選擇下列其中一個值：
     - **註冊至受信任平台模組 (TPM) KSP (如果存在)，否則註冊至軟體 KSP**
     - **註冊至信賴平台模組 (TPM) KSP，否則失敗**
     - **註冊至 Passport，否則失敗 (Windows 10 及更新版本)**
     - **註冊至軟體 KSP**

   - **金鑰使用方法**：輸入憑證的金鑰使用方法選項。 選項包括：
     - **金鑰編密**：只有在已將金鑰加密時，才允許交換金鑰
     - **數位簽章**：只有在有數位簽章協助保護金鑰時，才允許交換金鑰
   - **金鑰大小 (位元)** ：選取金鑰中包含的位元數
   - **雜湊演算法** (Android、Windows Phone 8.1、Windows 8.1、Windows 10)：選取其中一種可用的雜湊演算法類型，以搭配此憑證使用。 選取連線中裝置所支援的最強安全性層級。
   - **根憑證**：選擇您先前建立並指派給使用者和/或裝置的[受信任根憑證設定檔](certficates-pfx-configure.md#create-a-trusted-certificate-profile)。 此 CA 憑證必須是發行憑證 (您在此憑證設定檔中設定) 之 CA 的根憑證。 請務必將此受信任的根憑證設定檔指派至在 SCEP 憑證設定檔中指派的相同群組。
   - **擴充金鑰使用方法**：針對憑證的使用目的**新增**值。 在大部分情況下，憑證需要 [用戶端驗證]  ，使用者或裝置才能向伺服器進行驗證。 不過，您可以視需要新增任何其他金鑰使用方式。
   - **註冊設定**
     - **更新閾值 (%)** ：輸入裝置要求更新憑證之前，剩餘的憑證存留時間百分比。
     - **SCEP 伺服器 URL**：輸入一或多個透過 SCEP 發行憑證的 NDES 伺服器 URL。 例如，輸入類似 `https://ndes.contoso.com/certsrv/mscep/mscep.dll` 的內容。
     - 選取 [確定]  然後選取 [建立]  以建立您的設定檔。

設定檔隨即建立，並出現在 [設定檔清單] 窗格上。

## <a name="assign-the-certificate-profile"></a>指派憑證設定檔

將憑證設定檔指派給群組之前，請考慮下列事宜︰

- 當您指派憑證設定檔給群組時，來自受信任 CA 憑證設定檔的憑證檔案，即會安裝在裝置上。 裝置會使用 SCEP 憑證設定檔來建立裝置所要求的憑證。
- 憑證設定檔只會安裝在執行於您建立設定檔時所用的平台裝置上。
- 您可以將憑證設定檔指派到使用者集合或裝置集合。
- 若要在裝置註冊之後快速將憑證發行至裝置，請將憑證設定檔指派到使用者群組，而不是裝置群組。 如果您將它指派至裝置群組，便必須先執行完整的裝置註冊，裝置才能接收原則。
- 雖然您會分別指派每個設定檔，但仍需指派受信任的根 CA 以及 SCEP 或 PKCS 設定檔。 否則，SCEP 或 PKCS 憑證原則會失敗。

    > [!NOTE]
    > 在 iOS 裝置上，當 SCEP 憑證設定檔與額外設定檔 (例如 Wi-Fi 或 VPN 設定檔) 關聯時，裝置會接受那些每個額外設定檔的憑證。 這會導致 iOS 裝置具有多個由 SCEP 憑證要求提供的憑證。  

- 如果您針對 Intune 和 Configuration Manager 使用共同管理，請在 Configuration Manager 中，針對「資源存取原則」  [設定工作負載滑動軸](https://docs.microsoft.com/sccm/comanage/how-to-switch-workloads)為 [Intune]  或 [試驗 Intune]  。 此設定可讓 Windows 10 用戶端啟動要求憑證的流程。  

如需如何指派設定檔的資訊，請參閱[指派裝置設定檔](device-profile-assign.md)。

## <a name="intune-connector-setup-verification-and-troubleshooting"></a>Intune 連接器設定驗證和疑難排解

若要針對問題進行疑難排解及驗證 Intune 連接器設定，請參閱 [Certificate Authority script samples](https://aka.ms/intuneconnectorverificationscript) (憑證授權單位指令碼範例)

## <a name="intune-connector-events-and-diagnostic-codes"></a>Intune 連接器事件和診斷碼

從 6.1806.x.x 版開始，Intune 連接器服務會在 [事件檢視器]  ([應用程式及服務記錄檔]   > [Microsoft Intune 連接器]  ) 中記錄事件。 您可以使用這些事件來協助對 Intune 連接器設定中的潛在問題進行疑難排解。 這些事件會記錄作業的成功與失敗，還會包含診斷碼及訊息，以協助 IT 系統管理員進行疑難排解。

### <a name="event-ids-and-descriptions"></a>事件識別碼和描述

> [!NOTE]
> 如需每個事件相關診斷碼的詳細資料，請使用**診斷碼**資料表 (在本文中)。

| 事件識別碼      | 事件名稱    | 事件描述 | 相關的診斷碼 |
| ------------- | ------------- | -------------     | -------------            |
| 10010 | StartedConnectorService  | 已啟動連接器服務 | 0x00000000、0x0FFFFFFF |
| 10020 | StoppedConnectorService  | 已停止連接器服務 | 0x00000000、0x0FFFFFFF |
| 10100 | CertificateRenewal_Success  | 已成功更新連接器註冊憑證 | 0x00000000、0x0FFFFFFF |
| 10102 | CertificateRenewal_Failure  | 連接器註冊憑證無法更新。 請重新安裝連接器。 | 0x00000000、0x00000405、0x0FFFFFFF |
| 10302 | RetrieveCertificate_Error  | 無法從登錄中擷取連接器註冊憑證。 請檢閱與此事件相關之憑證指紋的事件詳細資料。 | 0x00000000、0x00000404、0x0FFFFFFF |
| 10301 | RetrieveCertificate_Warning  | 檢查事件詳細資料中的診斷資訊。 | 0x00000000、0x00000403、0x0FFFFFFF |
| 20100 | PkcsCertIssue_Success  | 已成功發行 PKCS 憑證。 請檢閱與此事件相關之裝置識別碼、使用者識別碼、CA 名稱、憑證範本名稱和憑證指紋的事件詳細資料。 | 0x00000000、0x0FFFFFFF |
| 20102 | PkcsCertIssue_Failure  | 無法發行 PKCS 憑證。 請檢閱與此事件相關之裝置識別碼、使用者識別碼、CA 名稱、憑證範本名稱和憑證指紋的事件詳細資料。 | 0x00000000、0x00000400、0x00000401、0x0FFFFFFF |
| 20200 | RevokeCert_Success  | 已成功撤銷憑證。 請檢閱與此事件相關之裝置識別碼、使用者識別碼、CA 名稱、憑證序號的事件詳細資料。 | 0x00000000、0x0FFFFFFF |
| 20202 | RevokeCert_Failure | 無法撤銷憑證。 請檢閱與此事件相關之裝置識別碼、使用者識別碼、CA 名稱、憑證序號的事件詳細資料。 如需額外資訊，請參閱 NDES SVC 記錄檔。   | 0x00000000、0x00000402、0x0FFFFFFF |
| 20300 | Upload_Success | 已成功上傳憑證的要求或撤銷資料。 請檢閱上傳詳細資料的事件詳細資料。 | 0x00000000、0x0FFFFFFF |
| 20302 | Upload_Failure | 無法上傳憑證的要求或撤銷資料。 請檢閱事件詳細資料 > 上傳狀態，以判斷失敗點。| 0x00000000、0x0FFFFFFF |
| 20400 | Download_Success | 已成功下載簽署憑證、下載用戶端憑證或撤銷憑證的要求。 請檢閱下載詳細資料的事件詳細資料。  | 0x00000000、0x0FFFFFFF |
| 20402 | Download_Failure | 無法下載簽署憑證、下載用戶端憑證或撤銷憑證的要求。 請檢閱下載詳細資料的事件詳細資料。 | 0x00000000、0x0FFFFFFF |
| 20500 | CRPVerifyMetric_Success  | 憑證登錄點已成功驗證用戶端挑戰 | 0x00000000、0x0FFFFFFF |
| 20501 | CRPVerifyMetric_Warning  | 憑證登錄點已完成，但拒絕要求。 請參閱診斷碼和訊息，以取得詳細資料。 | 0x00000000、0x00000411、0x0FFFFFFF |
| 20502 | CRPVerifyMetric_Failure  | 憑證登錄點無法驗證用戶端挑戰。 請參閱診斷碼和訊息，以取得詳細資料。 請參閱對應至挑戰之裝置識別碼的事件訊息詳細資料。 | 0x00000000、0x00000408、0x00000409、0x00000410、0x0FFFFFFF |
| 20600 | CRPNotifyMetric_Success  | 憑證登錄點已成功完成通知程序，並已將憑證傳送到用戶端裝置。 | 0x00000000、0x0FFFFFFF |
| 20602 | CRPNotifyMetric_Failure  | 憑證登錄點無法完成通知程序。 請參閱事件訊息詳細資料，以取得要求的相關資訊。 請驗證 NDES 伺服器與 CA 之間的連線。 | 0x00000000、0x0FFFFFFF |

### <a name="diagnostic-codes"></a>診斷碼

| 診斷碼 | 診斷名稱 | 診斷訊息 |
| -------------   | -------------   | -------------      |
| 0x00000000 | 成功  | 成功 |
| 0x00000400 | PKCS_Issue_CA_Unavailable  | 憑證授權單位無效或無法連線。 請確認憑證授權單位可用，且您的伺服器可以與其通訊。 |
| 0x00000401 | Symantec_ClientAuthCertNotFound  | 本機憑證存放區中找不到 Symantec 用戶端驗證憑證。 如需詳細資訊，請參閱[針對 DigiCert PKI 平台設定 Intune 憑證連接器](https://docs.microsoft.com/intune/certificates-digicert-configure#troubleshooting) \(英文\) 一文。  |
| 0x00000402 | RevokeCert_AccessDenied  | 指定的帳戶無權撤銷來自 CA 的憑證。 請參閱事件訊息詳細資料中的 CA 名稱欄位，以判斷發行的 CA。  |
| 0x00000403 | CertThumbprint_NotFound  | 找不到符合您輸入的憑證。 請註冊憑證連接器，然後再試一次。 |
| 0x00000404 | Certificate_NotFound  | 找不到符合所提供輸入的憑證。 請重新註冊憑證連接器，然後再試一次。 |
| 0x00000405 | Certificate_Expired  | 憑證已過期。 請重新註冊憑證連接器以更新憑證，然後再試一次。 |
| 0x00000408 | CRPSCEPCert_NotFound  | 找不到 CRP 加密憑證。 請確認 NDES 和 Intune 連接器已正確設定。 |
| 0x00000409 | CRPSCEPSigningCert_NotFound  | 無法擷取簽署憑證。 請確認 Intune 連接器服務已設定正確，且 Intune 連接器服務正在執行。 另請確認憑證下載事件已成功。 |
| 0x00000410 | CRPSCEPDeserialize_Failed  | 無法還原序列化 SCEP 挑戰要求。 請確認 NDES 和 Intune 連接器已正確設定。 |
| 0x00000411 | CRPSCEPChallenge_Expired  | 由於憑證挑戰過期，已拒絕要求。 用戶端裝置可以在從管理伺服器取得新挑戰之後重試。 |
| 0x0FFFFFFFF | Unknown_Error  | 我們無法完成您的要求，因為發生伺服器端錯誤。 請再試一次。 |

## <a name="next-steps"></a>後續步驟

- [使用 PKCS 憑證](certficates-pfx-configure.md)，或[從 Symantec PKI Manager Web 服務核發 PKCS 憑證](certificates-symantec-configure.md)
- [新增協力廠商 CA 以搭配使用 SCEP 與 Intune](certificate-authority-add-scep-overview.md)
- 如需其他協助，請使用下列指南：
  - [針對 Microsoft Intune 中的 SCEP 憑證設定檔部署進行疑難排解](https://support.microsoft.com/help/4457481) \(機器翻譯\)
  - [針對要與 Microsoft Intune 憑證設定檔搭配使用的 NDES 設定進行疑難排解](https://support.microsoft.com/help/4459540) \(機器翻譯\)

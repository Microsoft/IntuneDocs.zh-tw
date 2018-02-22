---
title: "透過 Intune 設定並管理 SCEP 憑證"
titlesuffix: Azure portal
description: "了解如何設定基礎結構，並建立及指派 Intune SCEP 憑證設定檔。"
keywords: 
author: arob98
ms.author: angrobe
manager: dougeby
ms.date: 1/18/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.reviewer: kmyrup
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 61193cc96f0ea22e9a80d24fe8ee0499e80d4202
ms.sourcegitcommit: 2c7794848777e73d6a9502b4e1000f0b07ac96bc
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/01/2018
---
# <a name="configure-and-manage-scep-certificates-with-intune"></a>透過 Intune 設定並管理 SCEP 憑證
[!INCLUDE[azure_portal](./includes/azure_portal.md)]

本主題說明如何透過 Intune 設定基礎結構，並建立及指派簡單憑證註冊通訊協定 (SCEP) 憑證設定檔。

## <a name="configure-on-premises-infrastructure"></a>設定內部部署基礎結構

-    **Active Directory 網域**：本節所列的所有伺服器 (除了 Web 應用程式 Proxy 伺服器) 均須加入 Active Directory 網域。

-  **憑證授權單位** (CA)：在企業版 Windows Server 2008 R2 或更新版本上執行的企業憑證授權單位 (CA)。 不支援獨立 CA。 如需詳細資料，請參閱[安裝憑證授權單位 (機器翻譯)](http://technet.microsoft.com/library/jj125375.aspx)。
    如果您的 CA 執行 Windows Server 2008 R2，您必須 [從 KB2483564 安裝 Hotfix](http://support.microsoft.com/kb/2483564/)。

-  **NDES 伺服器**：在執行 Windows Server 2012 R2 或更新版本的伺服器上，您必須設定網路裝置註冊服務 (NDES)。 在同時執行企業 CA 的伺服器上執行 NDES 時，Intune 便無法支援 NDES。 請參閱[網路裝置註冊服務指導方針](http://technet.microsoft.com/library/hh831498.aspx)以取得有關如何設定 Windows Server 2012 R2 來裝載網路裝置註冊服務的指示。
NDES 伺服器必須加入裝載 CA 的網域，但不在與 CA 相同的伺服器上。 在[使用原則模組和網路裝置註冊服務](https://technet.microsoft.com/library/dn473016.aspx)中可以找到將 NDES 伺服器部署至不同樹系、隔離網路或內部網域的詳細資訊。

-  **Microsoft Intune 憑證連接器**：使用 Azure 入口網站來下載「憑證連接器」安裝程式 (**ndesconnectorssetup.exe**)。 然後您可以在裝載網路裝置註冊服務 (NDES) 角色，在要安裝憑證連接器的伺服器上執行 **ndesconnectorssetup.exe**。 
-  **Web 應用程式 Proxy 伺服器** (選用)︰使用執行 Windows Server 2012 R2 或更新版本的伺服器做為 Web 應用程式 Proxy (WAP) 伺服器。 此組態：
    -  允許裝置使用網際網路連線接收憑證。
    -  是裝置連線透過網際網路來接收和更新憑證時的安全性建議。

 > [!NOTE]           
> -    裝載 WAP 伺服器 [必須安裝更新](http://blogs.technet.com/b/ems/archive/2014/12/11/hotfix-large-uri-request-in-web-application-proxy-on-windows-server-2012-r2.aspx) ，以啟用網路裝置註冊服務所使用之長 URL 的支援。 此更新隨附於 [2014 年 12 月更新彙總套件](http://support.microsoft.com/kb/3013769)，或個別提供於 [KB3011135](http://support.microsoft.com/kb/3011135)。
>-  此外，裝載 WAP 的伺服器必須有 SSL 憑證，該憑證符合發佈給外部用戶端的名稱，並且信任 NDES 伺服器上使用的 SSL 憑證。 這些憑證讓 WAP 伺服器能從用戶端終止 SSL 連線，以及建立與 NDES 伺服器的新 SSL 連線。
    如需 WAP 憑證的相關資訊，請參閱[計劃使用 Web 應用程式 Proxy 發行應用程式](https://technet.microsoft.com/library/dn383650.aspx)的**規劃憑證**小節。 如需 WAP 伺服器的一般資訊，請參閱[使用 Web 應用程式 Proxy](http://technet.microsoft.com/library/dn584113.aspx)。|

### <a name="network-requirements"></a>網路需求

從網際網路到周邊網路，允許網際網路上所有主機/IP 位址的連接埠 443 都能連線到 NDES 伺服器。

從周邊網路到受信任網路，允許在加入網域的 NDES 伺服器上進行網域存取所需的所有連接埠和通訊協定。 NDES 伺服器需要存取憑證伺服器、DNS 伺服器、Configuration Manager 伺服器和網域控制站。

建議您透過 Proxy 發佈 NDES 伺服器，例如 [Azure AD 應用程式 Proxy](https://azure.microsoft.com/documentation/articles/active-directory-application-proxy-publish/)、[Web Access Proxy](https://technet.microsoft.com/library/dn584107.aspx)，或是協力廠商 Proxy。


### <a name="certificates-and-templates"></a>憑證和範本

|物件|詳細資料|
|----------|-----------|
|**憑證範本**|在發行 CA 上設定此範本。|
|**用戶端驗證憑證**|自發行 CA 或公用 CA 所要求的憑證，您會將它安裝於 NDES 伺服器上。|
|**伺服器驗證憑證**|自發行 CA 或公用 CA 所要求的憑證，您會在 NDES 伺服器的 IIS 中安裝並繫結此 SSL 憑證。|
|**可信任的根 CA 憑證**|您會從根 CA (或任何信任根 CA 的裝置) 將此憑證匯出為 **.cer** 檔案，並使用受信任的 CA 憑證設定檔將它指派給裝置。<br /><br />您針對每個作業系統平台使用單一受信任根 CA 憑證，並將它與您建立的每個受信任根憑證設定檔產生關聯。<br /><br />您可以在需要時使用其他受信任根 CA 憑證。 比方說，當您需要向 CA 提供信任，好讓它為您簽署 Wi-Fi 存取點的伺服器驗證憑證時，您可能就會這麼做。|

### <a name="accounts"></a>帳戶

|名稱|詳細資料|
|--------|-----------|
|**NDES 服務帳戶**|指定網域使用者帳戶以做為 NDES 服務帳戶使用。|

## <a name="configure-your-infrastructure"></a>設定基礎結構
您可以設定憑證設定檔之前，必須先完成下列工作，這些需要 Windows Server 2012 R2 和 Active Directory 憑證服務 (ADCS) 的知識：

**步驟 1**：建立 NDES 服務帳戶

**步驟 2**：設定憑證授權單位上的憑證範本

**步驟 3**：設定 NDES 伺服器上的必要條件

**步驟 4**：設定 NDES 以搭配 Intune 使用

**步驟 5**：啟用、安裝及設定 Intune 憑證連接器

#### <a name="step-1---create-an-ndes-service-account"></a>步驟 1：建立 NDES 服務帳戶

建立網域使用者帳戶以做為 NDES 服務帳戶。 在您安裝及設定 NDES 之前，會在發行 CA 上設定範本時指定此帳戶。 請確定使用者具有預設權限：[本機登入]、[以服務方式登入] 和 [以批次工作登入] 權限。 某些組織擁有停用這些權限的強化原則。

#### <a name="step-2---configure-certificate-templates-on-the-certification-authority"></a>步驟 2：設定憑證授權單位上的憑證範本
在這項工作中，您將會：

-   設定 NDES 的憑證範本

-   發行 NDES 的憑證範本

##### <a name="to-configure-the-certification-authority"></a>設定憑證授權單位

1.  以企業系統管理員身分登入。

2.  在發行 CA 上，使用 [憑證範本] 嵌入式管理單元來建立新的自訂範本，或複製現有的範本，然後編輯現有的範本 (例如使用者範本) 以搭配 NDES 使用。

    >[!NOTE]
    > NDES 憑證範本必須根據 v2 憑證範本 (具有 Windows 2003 相容性)。

    範本必須要有下列組態：

    -   指定範本的易記「範本顯示名稱」  。

    -   在 [主體名稱]  索引標籤上，選取 [在要求中提供] 。 (安全性由 NDES 的 Intune 原則模組加強)。

    -   在 [延伸]  索引標籤上，確定 [應用程式原則描述]  包含 [用戶端驗證] 。

        > [!IMPORTANT]
        > 若為 iOS 和 macOS 憑證範本，請在 [延伸] 索引標籤上編輯 [金鑰使用方法]，並確保未選取 [簽章是原件證明]。

    -   在 [安全性] 索引標籤上，新增 NDES 服務帳戶，並提供其 [註冊] 範本的權限。 建立 SCEP 設定檔的 Intune 系統管理員需要**讀取** 權限，讓他們可以在建立 SCEP 設定檔時瀏覽至範本。

    > [!NOTE]
    > 若要撤銷憑證，NDES 服務帳戶需要憑證設定檔所使用之每個憑證範本的*發行及管理憑證*權限。

3.  檢閱範本 [一般]  索引標籤上的 [有效期間]  。 根據預設，Intune 使用範本中所設定的值。 不過，您可以選擇設定 CA 以允許要求者指定不同的值，然後您可以從 Intune 管理主控台內設定該值。 如果您想要一律使用範本中的值，請略過此步驟中的其餘部分。

    > [!IMPORTANT]
    > iOS 和 macOS 一律會使用範本中的值，而不論您所做的其他組態設定。

以下是範例範本設定的螢幕擷取畫面。

![範本, 處理要求索引標籤](.\media\scep_ndes_request_handling.png)

![範本, 主體名稱索引標籤](.\media\scep_ndes_subject_name.jpg)

![範本, 安全性索引標籤](.\media\scep_ndes_security.jpg)

![範本, 延伸索引標籤](.\media\scep_ndes_extensions.jpg)

![範本, 發行需求索引標籤](.\media\scep_ndes_issuance_reqs.jpg)

>   [!IMPORTANT]
    > 針對應用程式原則，僅新增所需的應用程式原則。 向您的安全性系統管理員確認您的選擇。



若要設定 CA 以允許要求者指定有效期間：

1. 在 CA 上執行下列命令：
    - **certutil -setreg Policy\EditFlags +EDITF_ATTRIBUTEENDDATE**
    - **net stop certsvc**
    - **net start certsvc**
2. 在發行的 CA 上使用 [憑證授權單位] 嵌入式管理單元來發行憑證範本。
    選取 [憑證範本] 節點，並按一下 [動作]-&gt; [新增]&gt; [要發出的憑證範本]，然後選取您在步驟 2 中建立的範本。
3. 檢視 [憑證範本]  資料夾下的發行範本來加以驗證。


#### <a name="step-3---configure-prerequisites-on-the-ndes-server"></a>步驟 3：設定 NDES 伺服器上的必要條件
在這項工作中，您要：

-   將 NDES 加入至 Windows Server 並設定 IIS 以支援 NDES

-   將 NDES 服務帳戶加入至 IIS_IUSR 群組

-   設定 NDES 服務帳戶的 SPN




   1.  在裝載 NDES 的伺服器上，以**企業系統管理員**的身分登入，然後使用[新增角色及功能精靈](https://technet.microsoft.com/library/hh831809.aspx)來安裝 NDES：

    1.  在精靈中，選取 [Active Directory 憑證服務]  以存取 AD CS 角色服務。 選取 [網路裝置註冊服務] ，取消核取 [憑證授權單位] ，然後完成精靈。

        > [!TIP]
        > 在精靈的 [安裝進度]  頁面，請不要按一下 [關閉] 。 相反地，請按一下 [設定目的地伺服器上的 Active Directory 憑證服務] 的連結。 這會開啟 [AD CS 設定精靈]  ，讓您用於下一個工作。 [AD CS 設定] 開啟之後，您可以關閉 [新增角色及功能精靈]。

    2.  當 NDES 加入至伺服器時，精靈也會安裝 IIS。 請確定 IIS 具有下列組態：

        -   [Web 伺服器] &gt; [安全性] &gt; [要求篩選]

        -   [Web 伺服器] &gt; [應用程式部署] &gt; [ASP.NET 3.5]。 安裝 ASP.NET 3.5 時會安裝 .NET Framework 3.5。 安裝 .NET Framework 3.5 時，請安裝核心 [.NET Framework 3.5]  功能和 [HTTP 啟動] 。

        -   [Web 伺服器] &gt; [應用程式部署] &gt; [ASP.NET 4.5]。 安裝 ASP.NET 4.5 時會安裝 .NET Framework 4.5。 安裝 .NET Framework 4.5 時，請安裝核心 [.NET Framework 4.5] 功能、[ASP.NET 4.5] 以及 [WCF 服務] &gt; [HTTP 啟動] 功能。

        -   [管理工具] &gt; [IIS 6 管理相容性] &gt; [IIS 6 Metabase 相容性]

        -   [管理工具] &gt; [IIS 6 管理相容性] &gt; [IIS 6 WMI 相容性]

  2.  在伺服器上，新增 NDES 服務帳戶成為 **IIS_IUSR** 群組的成員身分。

   3.  在提升權限的命令提示字元中，執行下列命令來設定 NDES 服務帳戶的 SPN：

`**setspn -s http/&lt;DNS name of NDES Server&gt; &lt;Domain name&gt;\&lt;NDES Service account name&gt;**`

   例如，如果 NDES 伺服器的名稱為 **Server01**，您的網域是 **Contoso.com**，而且服務帳戶是 **NDESService**，請使用：

`**setspn –s http/Server01.contoso.com contoso\NDESService**`

#### <a name="step-4---configure-ndes-for-use-with-intune"></a>步驟 4：設定 NDES 以搭配 Intune 使用
在這項工作中，您將會：

-   設定 NDES 以便用於發行 CA

-   在 IIS 中繫結伺服器驗證 (SSL) 憑證

-   設定 IIS 中的要求篩選


1.  在 NDES 伺服器上，開啟 [AD CS 設定精靈]，然後進行下列設定：

    > [!TIP]
    > 如果您按一下前個工作中的連結，此精靈已經開啟。 否則，開啟 [伺服器管理員] 來存取 Active Directory 憑證服務的部署後組態。

    -   在 [角色服務]  頁面上，選取 [網路裝置註冊服務] 。

    -   在 [NDES 的服務帳戶]  頁面上，指定 NDES 服務帳戶。

    -   在 [NDES 的 CA]  頁面上，按一下 [選取] ，然後選取您設定憑證範本的發行 CA。

    -   在 [NDES 的密碼編譯]  頁面上，設定符合您公司需求的金鑰長度。

    在 [確認]  頁面上，按一下 [設定]  來完成精靈。

2.  在精靈完成之後，在 NDES 伺服器上編輯下列登錄機碼：

    -   **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Cryptography\MSCEP\**

    若要編輯這個機碼，請識別憑證範本的 [目的 (可在其 [要求處理] 索引標籤上找到)]，然後使用您在工作 1 中指定的憑證範本名稱 (而不是範本顯示名稱) 來取代現有的資料，以編輯登錄中的對應項目。 下表會將憑證範本目的對應到登錄中的值：

    |憑證範本目的 (在 [處理要求] 索引標籤上)|要編輯的登錄值|SCEP 設定檔的 Intune 管理主控台中看到的值|
    |--------------------------------------------------------------|--------------------------|------------------------------------------------------------------------------------------------------------|
    |簽章|SignatureTemplate|數位簽章|
    |加密|EncryptionTemplate|金鑰加密|
    |簽章和加密|GeneralPurposeTemplate|金鑰加密<br /><br />數位簽章|
    例如，如果您的憑證範本目的是 [加密] ，則請將 **EncryptionTemplate** 值編輯為憑證範本的名稱。

3. NDES 伺服器會收到長的 URL (查詢)，而這需要您新增兩個登錄項目︰

    |位置|值|類型|資料|
    |-------|-----|----|----|
    |HKLM\SYSTEM\CurrentControlSet\Services\HTTP\Parameters|MaxFieldLength|DWORD|65534 (十進位)|
    |HKLM\SYSTEM\CurrentControlSet\Services\HTTP\Parameters|MaxRequestBytes|DWORD|65534 (十進位)|


4. 在 IIS 管理員中，選取 [預設的網站] -> [要求篩選] -> [編輯功能設定]，然後將 [URL 長度上限] 和 [查詢字串上限] 變更為 *65534* (如所顯示)。

    ![IIS URL 和查詢長度上限](.\media\SCEP_IIS_max_URL.png)

5.  重新啟動伺服器。 在伺服器上執行 **iisreset** 不足以完成這些變更。
6. 瀏覽至 http://*FQDN*/certsrv/mscep/mscep.dll。 您應該會看到與下面類似的 NDES 頁面︰

    ![測試 NDES](.\media\SCEP_NDES_URL.png)

    如果您收到「503 服務無法使用」，請檢查事件檢視器。 因為遺失 NDES 使用者的權限，所以可能已停止應用程式集區。 工作 1 會說明這些權限。

##### <a name="to-install-and-bind-certificates-on-the-ndes-server"></a>在 NDES 伺服器上安裝並繫結憑證

1.  在 NDES 伺服器上，要求並安裝來自內部 CA 或公用 CA 的 **伺服器驗證** 憑證。 然後將此 SSL 憑證繫結在 IIS 中。

    > [!TIP]
    > 在 IIS 中繫結 SSL 憑證之後，安裝用戶端驗證憑證。 此憑證可以由 NDES 伺服器所信任的任何 CA 發出。 雖然不是最佳做法，但您可以使用相同的憑證，進行伺服器和用戶端驗證，只要憑證中同時有雙方的增強金鑰使用方法 (EKU) 即可。 請檢閱以下的步驟，以取得這些驗證憑證的相關資訊。

    1.  取得伺服器驗證憑證後，開啟 [IIS 管理員] ，在 [連線]  窗格中選取 [預設的網站]  ，然後按一下 [動作]  窗格中的 [繫結]  。

    2.  按一下 [新增] ，將 [類型]  設為 [https] ，然後確定連接埠是 [443] 。 (獨立版 Intune 只支援連接埠 443)。

    3.  針對 [SSL 憑證] ，指定伺服器驗證憑證。

        > [!NOTE]
        > 如果 NDES 伺服器針對單一網路位址同時使用外部和內部名稱，則伺服器驗證憑證必須具有外部公用伺服器名稱的 [主體名稱]  ，以及包括內部伺服器名稱的 [主體替代名稱]  。

2.  在 NDES 伺服器上，從內部 CA 或公開憑證授權單位，要求並安裝 **用戶端驗證** 憑證。 這可以是與伺服器驗證憑證相同的憑證，如果該憑證具備兩種功能。

    用戶端驗證憑證必須具有下列屬性：

    **增強金鑰使用方法** - 這必須包括 [用戶端驗證]。

    **主體名稱** - 這必須等於您要在其中安裝憑證之伺服器 (NDES 伺服器) 的 DNS 名稱。

##### <a name="to-configure-iis-request-filtering"></a>設定 IIS 要求篩選

1.  在 NDES 伺服器上，開啟 [IIS 管理員] ，在 [連線]  窗格中選取 [預設的網站]  ，然後開啟 [要求篩選] 。

2.  按一下 [編輯功能設定]，然後設定下列值：

    **查詢字串 (位元組)** = **65534**

    **URL 長度上限 (位元組)** = **65534**

3.  檢閱下列登錄機碼：

    **HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\HTTP\Parameters**

    確定下列值設定為 DWORD 項目：

    名稱： **MaxFieldLength**，具有十進位值 **65534**

    名稱： **MaxRequestBytes**，具有十進位值 **65534**

4. 重新啟動 NDES 伺服器。 伺服器現在已準備好支援 Certificate Connector。

#### <a name="step-5---enable-install-and-configure-the-intune-certificate-connector"></a>步驟 5：啟用、安裝及設定 Intune 憑證連接器
在這項工作中，您將會：

- 啟用 Intune 中的 NDES 支援。
- 在您環境中裝載網路裝置註冊服務 (NDES) 角色的伺服器上，下載、安裝及設定憑證連接器。 若要增加您組織的 NDES 實作擴充性，您可以在每部 NDES 伺服器上，安裝多部 NDES 伺服器與 Microsoft Intune 憑證連接器。

##### <a name="to-download-install-and-configure-the-certificate-connector"></a>下載、安裝及設定憑證連接器
![ConnectorDownload](./media/certificates-download-connector.png)   
 
1. 登入 Azure 入口網站。 
2. 選取 [More Services] (更多服務) > [監視 + 管理] > [Intune]。
3. 在 [Intune] 刀鋒視窗中，選取 [裝置設定]。
4. 在 [裝置設定] 刀鋒視窗中選取 [憑證授權單位]。
5. 按一下 [新增] 並選取 [Download Connector file] (下載連接器檔案)。 將下載項目儲存到可從安裝它之伺服器存取的位置。 
6.  下載完成之後，在裝載網路裝置註冊服務 (NDES) 角色的伺服器上執行下載的安裝程式 (**ndesconnectorssetup.exe**)。 安裝程式也會安裝 NDES 和 CRP Web 服務的原則模組。 (CRP Web 服務 CertificateRegistrationSvc 會以 IIS 中的應用程式方式執行。)

    > [!NOTE]
    > 當您為獨立版 Intune 安裝 NDES 時，CRP 服務會自動與 Certificate Connector 一起安裝。 當您使用 Intune 搭配 Configuration Manager 時，將憑證註冊點安裝為個別的網站系統角色。

3.  當提示您提供憑證連接器的用戶端憑證時，請選擇 [選取]，然後選取您在工作 3 中，於 NDES 伺服器上安裝的**用戶端驗證**憑證。

    選取用戶端驗證憑證之後，您會回到 [Microsoft Intune Certificate Connector 的用戶端憑證]  介面。 雖然未顯示您所選取的憑證，請按 [下一步]  檢視該憑證的屬性。 然後按 [下一步] ，再按一下 [安裝] 。

4.  在精靈完成後，但在關閉精靈之前，按一下 [啟動 Certificate Connector UI] 。

    > [!TIP]
    > 如果您在啟動 Certificate Connector UI 之前關閉精靈，您可以藉由執行下列命令重新加以開啟：
    >
    > **&lt;安裝路徑&gt;\NDESConnectorUI\NDESConnectorUI.exe**

5.  在 **Certificate Connector** UI 中：

    按一下 [登入] 並輸入您的 Intune 服務系統管理員認證，或擁有全域管理權限的租用戶管理員認證。

    > [!IMPORTANT]
    > 使用者帳戶必須指派有效的 Intune 授權。 如果使用者帳戶沒有有效的 Intune 授權，則 NDESConnectorUI.exe 就會失敗。

    如果您的組織使用 Proxy 伺服器，而且 NDES 伺服器需要該 Proxy 以存取網際網路，請按一下 [使用 Proxy 伺服器]，然後提供 Proxy 伺服器名稱、連接埠，以及用以連接的帳戶認證。

    選取 [進階]  索引標籤，然後再提供對您的發行憑證授權單位具有 [發行及管理憑證]  權限的帳戶認證，再按一下 [套用] 。

    您現在可以關閉 Certificate Connector UI。

6.  開啟命令提示字元並輸入 **services.msc**，然後按下 **Enter**，再以滑鼠右鍵按一下 [Intune Connector 服務]，然後按一下 [重新啟動]。

若要驗證服務正在執行，請開啟瀏覽器並輸入下列 URL，這應傳回 **403** 錯誤：

**http:// &lt;NDES 伺服器的 FQDN&gt;/certsrv/mscep/mscep.dll**

## <a name="how-to-create-a-scep-certificate-profile"></a>如何建立 SCEP 憑證設定檔

1. 在 Azure 入口網站中，選取 [設定裝置] 工作負載。
2. 在 [裝置設定] 刀鋒視窗中，選取 [管理]  >  [設定檔]。
3. 在 [設定檔] 刀鋒視窗中，選取 [建立設定檔]。
4. 在 [建立設定檔] 刀鋒視窗中，為 SCEP 憑證設定檔輸入 [名稱] 及 [描述]。
5. 從 [平台] 下拉式清單中，選取此 SCEP 憑證的裝置平台。 您目前可選取下列平台之一，進行裝置限制設定︰
    - **Android**
    - **iOS**
    - **macOS**
    - **Windows Phone 8.1**
    - **Windows 8.1 及更新版本**
    - **Windows 10 及更新版本**
6. 從 [設定檔類型] 下拉式清單中，選取 [SCEP 憑證]。
7. 在 [SCEP 憑證] 刀鋒視窗上，進行以下設定：
    - **憑證有效期間** - 如果您已在發行 CA 上執行 **certutil - setreg Policy\EditFlags +EDITF_ATTRIBUTEENDDATE** 命令，允許自訂有效期間，則可以指定憑證到期之前的剩餘時間長度。<br>您可以指定一個比憑證範本中指定之有效期間更低，而不是更高的值。 舉例來說，如果憑證範本中的憑證有效期間為兩年，您可以指定一年而不是五年的值。 該值也必須低於發行 CA 憑證的剩餘有效期。 
    - **金鑰儲存提供者 (KSP)** (Windows Phone 8.1、Windows 8.1、Windows 10) - 指定儲存憑證金鑰的位置。 選擇下列其中一個值：
        - **註冊至受信任平台模組 (TPM) KSP (如果存在)，否則註冊至軟體 KSP**
        - **註冊至信賴平台模組 (TPM) KSP，否則失敗**
        - **註冊至 Passport，否則失敗 (Windows 10 及更新版本)**
        - **註冊至軟體 KSP**
    - **主體名稱格式**從清單中選取 Intune 如何自動在憑證要求中建立主體名稱。 如果憑證是針對使用者，您也可以在主體名稱中包含使用者的電子郵件地址。 從下列選項進行選擇：
        - **未設定**
        - **一般名稱**
        - **包括電子郵件的一般名稱**
        - **一般名稱及電子郵件地址**
        - **IMEI (國際行動設備識別)**
        - **序號**
        - **自訂** - 當您選取此選項時，會顯示另一個下拉式欄位。 您可以使用此欄位輸入自訂主體名稱格式。 自訂格式支援的兩個變數為「一般名稱 (CN)」和「電子郵件 (E)」。 您可使用由這些變數與靜態字串的其中之一或多個組成的組合，建立自訂主體名稱格式，例如︰**CN={{UserName}},E={{EmailAddress}},OU=Mobile,O=Finance Group,L=Redmond,ST=Washington,C=US**。在此範例中，您建立了主體名稱格式，除了 CN 與 E 變數之外，為組織單位、組織、位置、州與國家/地區值使用字串。 [本主題](https://msdn.microsoft.com/library/windows/desktop/aa377160.aspx) 說明 **CertStrToName** 函式和它支援的字串。
        
    - **主體別名**指定 Intune 如何在憑證要求中，自動建立主體別名 (SAN) 的值。 舉例來說，如果您選擇使用者憑證類型，您可以在主體別名中包含使用者主體名稱 (UPN)。 如果用戶端憑證將用來驗證網路原則伺服器，您必須將主體別名設定成 UPN。 
    - **金鑰使用方式** - 指定憑證的金鑰使用方式選項。 您可以選擇下列選項： 
        - **金鑰編密：**只允許在金鑰加密後交換金鑰。 
        - **數位簽章：**只允許在以數位簽章協助保護金鑰後交換金鑰。 
    - **金鑰大小 (位元)** - 選取金鑰中要包含的位元數。 
    - **雜湊演算法：** (Android、Windows Phone 8.1、Windows 8.1、Windows 10) - 選取其中一種可用的雜湊演算法類型，搭配此憑證使用。 選取連線中裝置所支援的最強安全性層級。 
    - **根憑證** - 選擇先前所設定並指派到使用者或裝置的根 CA 憑證設定檔。 此 CA 憑證必須是發行憑證 (您在此憑證設定檔中設定) 之 CA 的根憑證。 
    - **擴充金鑰使用方法** - 選取 [新增] 以新增憑證使用目的值。 在大部分情況下，憑證需要 [用戶端驗證]，使用者或裝置才能向伺服器進行驗證。 不過，您可以視需要新增任何其他金鑰使用方式。 
    - **註冊設定**
        - **更新閾值 (%)** - 指定裝置要求憑證更新之前，剩餘的憑證存留時間百分比。
        - **SCEP 伺服器 URL** - 指定一或多個將透過 SCEP 發行憑證的 NDES 伺服器 URL。 
8. 當您完成時，請返回 [建立設定檔] 刀鋒視窗，然後點擊 [建立]。

設定檔隨即建立，並出現在 [設定檔清單] 刀鋒視窗上。

## <a name="how-to-assign-the-certificate-profile"></a>如何指派憑證設定檔

將憑證設定檔指派給群組之前，請考慮下列事宜︰

- 當您指派憑證設定檔給群組時，來自受信任 CA 憑證設定檔的憑證檔案，即會安裝在裝置上。 裝置會使用 SCEP 憑證設定檔來建立裝置所要求的憑證。
- 憑證設定檔只會安裝在執行於您建立設定檔時所用的平台裝置上。
- 您可以將憑證設定檔指派到使用者集合或裝置集合。
- 若要在裝置註冊之後快速將憑證發行至裝置，請將憑證設定檔指派到使用者群組，而不是裝置群組。 如果您將它指派至裝置群組，便必須先執行完整的裝置註冊，裝置才能接收原則。
- 雖然您會分別指派每個設定檔，但仍需指派受信任的根 CA 以及 SCEP 或 PKCS 設定檔。 否則，SCEP 或 PKCS 憑證原則會失敗。

如需如何指派設定檔的相關資訊，請參閱[如何指派裝置設定檔](device-profile-assign.md)。


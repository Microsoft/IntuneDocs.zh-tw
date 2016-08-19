---
title: "設定 SCEP 的憑證基礎結構 |Microsoft Intune"
description: "建立及部署 SCEP 憑證設定檔的基礎結構。"
keywords: 
author: nbigman
manager: angrobe
ms.date: 07/25/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4ae137ae-34e5-4a45-950c-983de831270f
ms.reviewer: kmyrup
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 5b9d201200d2b18553778ba2234831854658c6c2
ms.openlocfilehash: 1f8e692e1938822342fda399df3832d2749de7c3

---
# 設定 SCEP 的憑證基礎結構
本主題說明建立及部署 SCEP 憑證設定檔所需的基礎結構。

### 內部部署基礎結構

-    **Active Directory 網域**：本節所列的所有伺服器 (除了 Web 應用程式 Proxy 伺服器) 均須加入 Active Directory 網域。

-  **憑證授權單位** (CA)：在企業版 Windows Server 2008 R2 或更新版本上執行的企業憑證授權單位 (CA)。 不支援獨立 CA。 如需如何設定憑證授權單位的指示，請參閱 [安裝憑證授權單位](http://technet.microsoft.com/library/jj125375.aspx)。
    如果您的 CA 執行 Windows Server 2008 R2，您必須 [從 KB2483564 安裝 Hotfix](http://support.microsoft.com/kb/2483564/)。
I
-  **NDES 伺服器**：在執行 Windows Server 2012 R2 或更新版本的伺服器上，您必須設定網路裝置註冊服務 (NDES)。 在同時執行企業 CA 的伺服器上執行 NDES 時，Intune 便無法支援 NDES。 請參閱[網路裝置註冊服務指導方針](http://technet.microsoft.com/library/hh831498.aspx)以取得有關如何設定 Windows Server 2012 R2 來裝載網路裝置註冊服務的指示。 NDES 伺服器必須加入裝載 CA 的網域，但不在與 CA 相同的伺服器上。 在[使用原則模組和網路裝置註冊服務](https://technet.microsoft.com/en-us/library/dn473016.aspx)中可以找到將 NDES 伺服器部署至不同樹系、隔離網路或內部網域的詳細資訊。

-  **Microsoft Intune Certificate Connector**：您可使用 Intune 管理主控台來下載 **Certificate Connector** 安裝程式 (**ndesconnectorssetup.exe**)。 然後您可以在要安裝 Certificate Connector 的電腦上執行 **ndesconnectorssetup.exe** 。
-  **Web 應用程式 Proxy 伺服器** (選用)︰您可以將執行 Windows Server 2012 R2 或更新版本的伺服器用作 Web 應用程式 Proxy (WAP) 伺服器。 此組態：
    -  允許裝置使用網際網路連線接收憑證。
    -  是裝置連線透過網際網路來接收和更新憑證時的安全性建議。

 > [!NOTE]           
> -    裝載 WAP 伺服器 [必須安裝更新](http://blogs.technet.com/b/ems/archive/2014/12/11/hotfix-large-uri-request-in-web-application-proxy-on-windows-server-2012-r2.aspx) ，以啟用網路裝置註冊服務所使用之長 URL 的支援。 此更新隨附於 [2014 年 12 月更新彙總套件](http://support.microsoft.com/kb/3013769)，或個別提供於 [KB3011135](http://support.microsoft.com/kb/3011135)。
>-  此外，主控 WAP 的伺服器必須有 SSL 憑證，該憑證必須符合發佈給外部用戶端，以及信任 NDES 伺服器上使用的 SSL 憑證的名稱。 這些憑證讓 WAP 伺服器能從用戶端終止 SSL 連線，以及建立與 NDES 伺服器的新 SSL 連線。
    如需 WAP 憑證的相關資訊，請參閱[計劃使用 Web 應用程式 Proxy 發行應用程式](https://technet.microsoft.com/library/dn383650.aspx)的**規劃憑證**小節。 如需 WAP 伺服器的一般資訊，請參閱[使用 Web 應用程式 Proxy](http://technet.microsoft.com/library/dn584113.aspx)。|

### 網路需求

從網際網路到周邊網路，允許經由連接埠 443 從網際網路上所有主機/IP 位址連接到 NDES 伺服器。

從周邊網路到受信任網路，允許在加入網域的 NDES 伺服器上進行網域存取所需的所有連接埠和通訊協定。 NDES 伺服器需要存取憑證伺服器、DNS 伺服器、Configuration Manager 伺服器和網域控制站。

建議您透過 Proxy 發佈 NDES 伺服器，例如 [Azure AD 應用程式 Proxy](https://azure.microsoft.com/en-us/documentation/articles/active-directory-application-proxy-publish/)、[Web Access Proxy](https://technet.microsoft.com/en-us/library/dn584107.aspx)，或是協力廠商 Proxy。


### <a name="BKMK_CertsAndTemplates"></a>憑證和範本

|物件|詳細資料|
|----------|-----------|
|**憑證範本**|在發行的 CA 上所設定的範本。|
|**用戶端驗證憑證**|由發行的 CA 或公用 CA 所要求，安裝於 NDES 伺服器上的憑證。|
|**伺服器驗證憑證**|由發行的 CA 或公用 CA 所要求，於 NDES 伺服器的 IIS 中安裝並繫結的 SSL 憑證。|
|**受信任的根 CA 憑證**|從根 CA (或任何信任根 CA 的裝置) 匯出為 **.cer** 檔案，並使用受信任的 CA 憑證加以部署至裝置之中的憑證。<br /><br />您針對每個作業系統平台使用單一受信任根 CA 憑證，並將它與您建立的每個受信任根憑證設定檔產生關聯。<br /><br />您可以在需要時使用其他受信任根 CA 憑證。 比方說，當您需要向 CA 提供信任，好讓它為您簽署 Wi-Fi 存取點的伺服器驗證憑證時，您可能就會這麼做。|

### <a name="BKMK_Accounts"></a>帳戶

|Name|詳細資料|
|--------|-----------|
|**NDES 服務帳戶**|您指定網域使用者帳戶以做為 NDES 服務帳戶。|

## <a name="BKMK_ConfigureInfrastructure"></a>設定基礎結構
您可以設定憑證設定檔之前，必須先完成下列工作，這些需要 Windows Server 2012 R2 和 Active Directory 憑證服務 (ADCS) 的知識：

**工作 1**：建立 NDES 服務帳戶

**工作 2**：設定憑證授權單位上的憑證範本

**工作 3**：設定 NDES 伺服器上的必要條件

**工作 4**：設定 NDES 以便搭配 Intune

**工作 5**：啟用、安裝及設定 Intune 憑證連接器

### 工作 1 - 建立 NDES 服務帳戶

建立網域使用者帳戶以做為 NDES 服務帳戶。 在您安裝及設定 NDES 之前，會在發行 CA 上設定範本時指定此帳戶。 請確定使用者具有預設權限：[本機登入]、[以服務方式登入] 和 [以批次工作登入] 權限。 某些組織擁有停用這些權限的強化原則。




### 工作 2 - 設定憑證授權單位上的憑證範本
在這項工作中，您將會：

-   設定 NDES 的憑證範本

-   發行 NDES 的憑證範本

##### 設定憑證授權單位

1.  以企業系統管理員身分登入。 

2.  在發行 CA 上，使用 [憑證範本] 嵌入式管理單元來建立新的自訂範本，或複製現有的範本，然後編輯現有的範本 (例如使用者範本) 以搭配 NDES 使用。

    範本必須要有下列組態：

    -   指定範本的易記「範本顯示名稱」  。

    -   在 [主體名稱]  索引標籤上，選取 [在要求中提供] 。 (安全性由 NDES 的 Intune 原則模組加強)。

    -   在 [延伸]  索引標籤上，確定 [應用程式原則描述]  包含 [用戶端驗證] 。

        > [!IMPORTANT]
        > 若為 iOS 和 Mac OS X 憑證範本，請在 [延伸] 索引標籤上，編輯 [金鑰使用方法] ，並確保未選取 [簽章是原件證明]。

    -   在 [安全性] 索引標籤上，新增 NDES 服務帳戶，並提供其 [註冊] 範本的權限。 將建立 SCEP 設定檔的 Intune 系統管理員需要 [讀取] 權限，讓他們可以在建立 SCEP 設定檔時瀏覽至範本。
    
    > [!NOTE]
    > 若要撤銷憑證，NDES 服務帳戶需要憑證設定檔所使用之每個憑證範本的*發行及管理憑證*權限。

3.  檢閱範本 [一般]  索引標籤上的 [有效期間]  。 根據預設，Intune 使用範本中所設定的值。 不過，您可以選擇設定 CA 以允許要求者指定不同的值，然後您可以從 Intune 管理主控台內設定該值。 如果您想要一律使用範本中的值，請略過此步驟中的其餘部分。

    > [!IMPORTANT]
    > iOS 和 Mac OS X 平台一律會使用範本中的設定值，而不論您所做的其他組態設定。

以下是範例範本設定的螢幕擷取畫面。

![範本, 處理要求索引標籤](..\media\scep_ndes_request_handling.png) 

![範本, 主體名稱索引標籤](..\media\scep_ndes_subject_name.jpg) 

![範本, 安全性索引標籤](..\media\scep_ndes_security.jpg) 

![範本, 延伸索引標籤](..\media\scep_ndes_extensions.jpg) 

![範本, 發行需求索引標籤](..\media\scep_ndes_issuance_reqs.jpg) 

>   [!IMPORTANT]
    > 對於應用程式原則 (在第 4 個螢幕擷取畫面)，只能新增所需的應用程式原則。 向您的安全性系統管理員確認您的選擇。
   


若要設定 CA 以允許要求者指定有效期間，請在 CA 上執行下列命令：

   1.  **certutil-setreg Policy\EditFlags + EDITF_ATTRIBUTEENDDATE**
   2.  **net stop certsvc**

   3.  **net start certsvc**

4.  在發行的 CA 上使用 [憑證授權單位] 嵌入式管理單元來發行憑證範本。

    1.  選取 [憑證範本] 節點，並按一下 [動作] -&gt; [新增] &gt; [要發出的憑證範本]，然後選取您在步驟 2 中建立的範本。

    2.  檢視 [憑證範本]  資料夾下的發行範本來加以驗證。


### 工作 3 - 設定 NDES 伺服器上的必要條件
在這項工作中，您將會：

-   將 NDES 加入至 Windows Server 並設定 IIS 以支援 NDES

-   將 NDES 服務帳戶加入至 IIS_IUSR 群組

-   設定 NDES 服務帳戶的 SPN




   1.  在將裝載 NDES 的伺服器上，您必須以 **企業系統管理員**的身分登入，然後使用 [新增角色及功能精靈](https://technet.microsoft.com/library/hh831809.aspx) 安裝 NDES：

    1.  在精靈中，選取 [Active Directory 憑證服務]  以存取 AD CS 角色服務。 選取 [網路裝置註冊服務] ，取消核取 [憑證授權單位] ，然後完成精靈。

        > [!TIP]
        > 在精靈的 [安裝進度]  頁面，請不要按一下 [關閉] 。 相反地，請按一下 [設定目的地伺服器上的 Active Directory 憑證服務] 的連結。 這會開啟 [AD CS 設定精靈]  ，讓您用於下一個工作。 [AD CS 設定] 開啟之後，您可以關閉 [新增角色及功能精靈]。

    2.  當 NDES 加入至伺服器時，精靈也會安裝 IIS。 請確定 IIS 具有下列組態：

        -   [Web 伺服器] &gt; [安全性] &gt; [要求篩選]

        -   [Web 伺服器] &gt; [應用程式部署] &gt; [ASP.NET 3.5]。 安裝 ASP.NET 3.5 時，將會安裝 .NET Framework 3.5。 安裝 .NET Framework 3.5 時，請安裝核心 [.NET Framework 3.5]  功能和 [HTTP 啟動] 。

        -   [Web 伺服器] &gt; [應用程式部署] &gt; [ASP.NET 4.5]。 安裝 ASP.NET 4.5 時，將會安裝 .NET Framework 4.5。 安裝 .NET Framework 4.5 時，請安裝核心 [.NET Framework 4.5] 功能、[ASP.NET 4.5] 以及 [WCF 服務] &gt; [HTTP 啟動] 功能。

        -   [管理工具] &gt; [IIS 6 管理相容性] &gt; [IIS 6 Metabase 相容性]

        -   [管理工具] &gt; [IIS 6 管理相容性] &gt; [IIS 6 WMI 相容性]

  2.  在伺服器上，新增 NDES 服務帳戶成為 **IIS_IUSR** 群組的成員身分。

   3.  在提升權限的命令提示字元中，執行下列命令來設定 NDES 服務帳戶的 SPN：

`**setspn -s http/&lt;DNS name of NDES Server&gt; &lt;Domain name&gt;\&lt;NDES Service account name&gt;**`

   例如，如果 NDES 伺服器的名稱為 **Server01**，您的網域是 **Contoso.com**，而且服務帳戶是 **NDESService**，請使用：

`**setspn –s http/Server01.contoso.com contoso\NDESService**`

### 工作 4 - 設定 NDES 以便搭配 Intune
在這項工作中，您將會：

-   設定 NDES 以便用於發行 CA

-   在 IIS 中繫結伺服器驗證 (SSL) 憑證

-   設定 IIS 中的要求篩選

##### 設定 NDES 以便搭配 Intune

1.  在 NDES 伺服器上，開啟 [AD CS 設定精靈]，然後進行下列組態設定。

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

3. NDES 伺服器將會收到很長的 URL (查詢)，而這需要您新增兩個登錄項目︰

    |位置|值|類型|資料|
    |-------|-----|----|----|
    |HKLM\SYSTEM\CurrentControlSet\Services\HTTP\Parameters|MaxFieldLength|DWORD|65534 (十進位)|
    |HKLM\SYSTEM\CurrentControlSet\Services\HTTP\Parameters|MaxRequestBytes|DWORD|65534 (十進位)|


4. 在 IIS 管理員中，選擇 [預設的網站] -> [要求篩選] -> [編輯功能設定]，然後將 [URL 長度上限] 和 [查詢字串上限] 變更為 *65534* (如所顯示)。

    ![IIS URL 和查詢長度上限](..\media\SCEP_IIS_max_URL.png) 

5.  重新啟動伺服器。 在伺服器上執行 **iisreset** 並無法完成這些變更。
6. 瀏覽至 http://*FQDN*/certsrv/mscep/mscep.dll。 您應該會看到與下面類似的 NDES 頁面︰

    ![測試 NDES](..\media\SCEP_NDES_URL.png) 

    如果您收到「503 服務無法使用」，請檢查 eventviewer。 因為遺失 NDES 使用者的權限，所以可能已停止應用程式集區。 工作 1 會說明這些權限。

##### 在 NDES 伺服器上安裝並繫結憑證

1.  在 NDES 伺服器上，要求並安裝來自內部 CA 或公用 CA 的 **伺服器驗證** 憑證。 然後將此 SSL 憑證繫結在 IIS 中。

    > [!TIP]
    > 在 IIS 中繫結 SSL 憑證之後，您也會安裝用戶端驗證憑證。 此憑證可以由 NDES 伺服器所信任的任何 CA 發出。 雖然不是最佳的作法，但您可以使用相同的憑證，進行伺服器和用戶端驗證，只要憑證中同時有雙方的增強金鑰使用方法 (EKU) 即可。 請檢閱以下的步驟，以取得這些驗證憑證的相關資訊。

    1.  取得伺服器驗證憑證後，開啟 [IIS 管理員] ，在 [連線]  窗格中選取 [預設的網站]  ，然後按一下 [動作]  窗格中的 [繫結]  。

    2.  按一下 [新增] ，將 [類型]  設為 [https] ，然後確定連接埠是 [443] 。 (獨立版 Intune 只支援連接埠 443)。

    3.  針對 [SSL 憑證] ，指定伺服器驗證憑證。

        > [!NOTE]
        > 如果 NDES 伺服器針對單一網路位址同時使用外部和內部名稱，則伺服器驗證憑證必須具有外部公用伺服器名稱的 [主體名稱]  ，以及包括內部伺服器名稱的 [主體替代名稱]  。

2.  在 NDES 伺服器上，從內部 CA 或公開憑證授權單位，要求並安裝 **用戶端驗證** 憑證。 這可以是與伺服器驗證憑證相同的憑證，如果該憑證具備兩種功能。

    用戶端驗證憑證必須具有下列屬性：

    **增強金鑰使用方法** - 這必須包括 [用戶端驗證]。

    **主體名稱** - 這必須等於您要在其中安裝憑證之伺服器 (NDES 伺服器) 的 DNS 名稱。

##### 設定 IIS 要求篩選

1.  在 NDES 伺服器上，開啟 [IIS 管理員] ，在 [連線]  窗格中選取 [預設的網站]  ，然後開啟 [要求篩選] 。

2.  按一下 [編輯功能設定] ，然後設定下列項目：

    **查詢字串 (位元組)** = **65534**

    **URL 長度上限 (位元組)** = **65534**

3.  檢閱下列登錄機碼：

    **HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\HTTP\Parameters**

    確定下列值設定為 DWORD 項目：

    名稱： **MaxFieldLength**，具有十進位值 **65534**

    名稱： **MaxRequestBytes**，具有十進位值 **65534**

4.  重新啟動 NDES 伺服器。 伺服器現在已準備好支援 Certificate Connector。

### 工作 5 - 啟用、安裝及設定 Intune 憑證連接器
在這項工作中，您將會：

啟用 Intune 中的 NDES 支援。

下載、安裝及設定 NDES 伺服器上的憑證連接器。

##### 啟用 Certificate Connector 的支援

1.  開啟 [Intune 管理主控台](https://manage.microsoft.com)，然後按一下 [系統管理] &gt; [憑證連接器]。

2.  按一下 [設定內部部署憑證連接器]。

3.  選取 [啟用 Certificate Connector] ，然後按一下 [確定] 。

##### 下載、安裝及設定 Certificate Connector

1.  開啟 [Intune 管理主控台](https://manage.microsoft.com)，然後按一下 [系統管理] &gt; [行動裝置管理] &gt; [憑證連接器] &gt; [下載憑證連接器]。

2.  下載完成之後，請在 Windows Server 2012 R2 伺服器上執行下載的安裝程式 (**ndesconnectorssetup.exe**)。 安裝程式也會安裝 NDES 和 CRP Web 服務的原則模組。 (CRP Web 服務 CertificateRegistrationSvc 會以 IIS 中的應用程式方式執行。)

    > [!NOTE]
    > 當您為獨立版 Intune 安裝 NDES 時，CRP 服務會自動與 Certificate Connector 一起安裝。 當您使用 Intune 搭配 Configuration Manager 時，將憑證註冊點安裝為個別的網站系統角色。

3.  提示輸入 Certificate Connector 的用戶端憑證，請按一下 [選取] ，然後選取您在工作 3 時在 NDES 伺服器上安裝的 **用戶端驗證** 憑證。

    選取用戶端驗證憑證之後，您會回到 [Microsoft Intune Certificate Connector 的用戶端憑證]  介面。 雖然未顯示您所選取的憑證，請按 [下一步]  檢視該憑證的屬性。 然後按 [下一步] ，再按一下 [安裝] 。

4.  在精靈完成後，但在關閉精靈之前，按一下 [啟動 Certificate Connector UI] 。

    > [!TIP]
    > 如果您在啟動 Certificate Connector UI 之前關閉精靈，您可以藉由執行下列命令重新加以開啟：
    >
    > **&lt;install_Path&gt;\NDESConnectorUI\NDESConnectorUI.exe**

5.  在 **Certificate Connector** UI 中：

    按一下 [登入] 並輸入您的 Intune 服務系統管理員認證，或擁有全域管理權限的租用戶管理員認證。

    如果您的組織使用 Proxy 伺服器，而且 NDES 伺服器需要該 Proxy 以存取網際網路，請按一下 [使用 Proxy 伺服器]，然後提供 Proxy 伺服器名稱、連接埠，以及用以連接的帳戶認證。

    選取 [進階]  索引標籤，然後再提供對您的發行憑證授權單位具有 [發行及管理憑證]  權限的帳戶認證，再按一下 [套用] 。

    您現在可以關閉 Certificate Connector UI。

6.  開啟命令提示字元並輸入 **services.msc**，然後按下 **Enter**，再以滑鼠右鍵按一下 [Intune Connector 服務]，然後按一下 [重新啟動]。

若要驗證服務正在執行，請開啟瀏覽器並輸入下列 URL，這應傳回 **403** 錯誤：

**http:// &lt;FQDN_of_your_NDES_server&gt;/certsrv/mscep/mscep.dll**

## 後續步驟
您現在已可設定憑證設定檔，如[設定憑證設定檔](Configure-Intune-certificate-profiles.md)中所述。



<!--HONumber=Jul16_HO4-->



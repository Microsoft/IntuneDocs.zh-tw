---
title: 搭配 Microsoft Intune 使用 SCEP 憑證 - Azure | Microsoft Docs
description: 若要在 Microsoft Intune 中使用 SCEP 憑證，請設定您的內部部署 AD 網域、建立憑證授權單位、設定 NDES 伺服器，並安裝 Intune 憑證連接器。 接著，建立 SCEP 憑證設定檔，然後將此設定檔指派給群組。 此外，請參閱不同的事件識別碼與其描述，以及 Intune 連接器服務的診斷碼。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 06/04/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: kmyrup
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: f5441bb15d6906257432afbfe51fffc6c11a6324
ms.sourcegitcommit: 97b9f966f23895495b4c8a685f1397b78cc01d57
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2018
ms.locfileid: "34745021"
---
# <a name="configure-and-use-scep-certificates-with-intune"></a>搭配 Intune 設定及使用 SCEP 憑證

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

此文章說明如何搭配 Intune 設定基礎結構，並建立及指派簡單憑證註冊通訊協定 (SCEP) 憑證設定檔。

## <a name="configure-on-premises-infrastructure"></a>設定內部部署基礎結構

- **Active Directory 網域**：本節所列的所有伺服器 (除了 Web 應用程式 Proxy 伺服器) 均須加入 Active Directory 網域。

- **憑證授權單位** (CA)：在企業版 Windows Server 2008 R2 或更新版本上執行的企業憑證授權單位 (CA)。 不支援獨立 CA。 如需詳細資料，請參閱[安裝憑證授權單位 (機器翻譯)](http://technet.microsoft.com/library/jj125375.aspx)。
    如果您的 CA 執行 Windows Server 2008 R2，您必須 [從 KB2483564 安裝 Hotfix](http://support.microsoft.com/kb/2483564/)。

- **NDES 伺服器**：在執行 Windows Server 2012 R2 或更新版本的伺服器上，您必須設定網路裝置註冊服務 (NDES)。 在同時執行企業 CA 的伺服器上執行 NDES 時，Intune 便無法支援 NDES。 請參閱[網路裝置註冊服務指導方針](http://technet.microsoft.com/library/hh831498.aspx)以取得有關如何設定 Windows Server 2012 R2 來裝載網路裝置註冊服務的指示。
NDES 伺服器必須加入裝載 CA 的網域，但不在與 CA 相同的伺服器上。 在[使用原則模組和網路裝置註冊服務](https://technet.microsoft.com/library/dn473016.aspx)中可以找到將 NDES 伺服器部署至不同樹系、隔離網路或內部網域的詳細資訊。

- **Microsoft Intune 憑證連接器**：使用 Azure 入口網站來下載「憑證連接器」安裝程式 (**ndesconnectorssetup.exe**)。 然後您可以在裝載網路裝置註冊服務 (NDES) 角色，在要安裝憑證連接器的伺服器上執行 **ndesconnectorssetup.exe**。 
- **Web 應用程式 Proxy 伺服器** (選用)︰使用執行 Windows Server 2012 R2 或更新版本的伺服器做為 Web 應用程式 Proxy (WAP) 伺服器。 此組態：
  -  允許裝置使用網際網路連線接收憑證。
  -  是裝置連線透過網際網路來接收和更新憑證時的安全性建議。

#### <a name="additional"></a>Additional
- 裝載 WAP 伺服器 [必須安裝更新](http://blogs.technet.com/b/ems/archive/2014/12/11/hotfix-large-uri-request-in-web-application-proxy-on-windows-server-2012-r2.aspx) ，以啟用網路裝置註冊服務所使用之長 URL 的支援。 此更新隨附於 [2014 年 12 月更新彙總套件](http://support.microsoft.com/kb/3013769)，或個別提供於 [KB3011135](http://support.microsoft.com/kb/3011135)。
- WAP 的伺服器必須有 SSL 憑證，該憑證符合發佈給外部用戶端的名稱，並且信任 NDES 伺服器上使用的 SSL 憑證。 這些憑證讓 WAP 伺服器能從用戶端終止 SSL 連線，以及建立與 NDES 伺服器的新 SSL 連線。

如需詳細資訊，請參閱[規劃 WAP 的憑證](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn383650(v=ws.11)#plan-certificates) \(英文\) 和 [WAP 伺服器的一般相關資訊](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn584113(v=ws.11)) \(英文\)。

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
|**NDES 服務帳戶**|輸入網域使用者帳戶以做為 NDES 服務帳戶。|

## <a name="configure-your-infrastructure"></a>設定基礎結構
在您設定憑證設定檔前，必須先完成下列工作。 執行這些工作需要對 Windows Server 2012 R2 及 Active Directory 憑證服務 (ADCS) 有一定程度的了解：

**步驟 1**：建立 NDES 服務帳戶

**步驟 2**：設定憑證授權單位上的憑證範本

**步驟 3**：設定 NDES 伺服器上的必要條件

**步驟 4**：設定 NDES 以搭配 Intune 使用

**步驟 5**：啟用、安裝及設定 Intune 憑證連接器

#### <a name="step-1---create-an-ndes-service-account"></a>步驟 1：建立 NDES 服務帳戶

建立網域使用者帳戶以做為 NDES 服務帳戶。 在您安裝及設定 NDES 之前，會在發行 CA 上設定範本時輸入此帳戶。 請確定使用者具有預設權限：[本機登入]、[以服務方式登入] 和 [以批次工作登入] 權限。 某些組織擁有停用這些權限的強化原則。

#### <a name="step-2---configure-certificate-templates-on-the-certification-authority"></a>步驟 2：設定憑證授權單位上的憑證範本
在此工作中，您要：

- 設定 NDES 的憑證範本
- 發行 NDES 的憑證範本

##### <a name="configure-the-certification-authority"></a>設定憑證授權單位

1. 以企業系統管理員身分登入。

2. 在發行 CA 上，使用 [憑證範本] 嵌入式管理單元來建立新的自訂範本。 或者，複製現有範本，然後更新現有範本 (例如使用者範本) 以搭配 NDES 使用。

   >[!NOTE]
   > NDES 憑證範本必須根據 v2 憑證範本 (具有 Windows 2003 相容性)。

   範本必須要有下列組態：

   - 輸入範本的易記「範本顯示名稱」  。

   - 在 [主體名稱] 中，選取 [在要求中提供] (安全性由 NDES 的 Intune 原則模組加強)。

   - 在 [延伸] 索引標籤上，確認 [應用程式原則描述] 包含 [用戶端驗證]。

     > [!IMPORTANT]
     > 針對 iOS 與 macOS 憑證範本，請在 [延伸] 索引標籤上編輯 [金鑰使用方法]，並確認未選取 [簽章是原件證明]。

   - 在 [安全性] 中，新增 NDES 服務帳戶，並提供其 [註冊] 範本的權限。 建立 SCEP 設定檔的 Intune 系統管理員需要**讀取** 權限，讓他們可以在建立 SCEP 設定檔時瀏覽至範本。

     > [!NOTE]
     > 若要撤銷憑證，NDES 服務帳戶需要憑證設定檔所使用每個憑證範本的*發行及管理憑證*權限。

3. 檢閱範本 [一般]  索引標籤上的 [有效期間]  。 根據預設，Intune 使用範本中所設定的值。 不過，您可以選擇設定 CA 以允許要求者輸入不同的值，然後就可以從 Intune 系統管理員主控台內設定該值。 如果您想要一律使用範本中的值，請略過此步驟中的其餘部分。

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
   選取 [憑證範本] 節點，按一下 [動作] > [新增] > [要發出的憑證範本]，然後選取您在步驟 2 中建立的範本。

3. 檢視 [憑證範本]  資料夾下的發行範本來加以驗證。

#### <a name="step-3---configure-prerequisites-on-the-ndes-server"></a>步驟 3：設定 NDES 伺服器上的必要條件
在此工作中，您要：

- 將 NDES 加入至 Windows Server 並設定 IIS 以支援 NDES
- 將 NDES 服務帳戶加入至 IIS_IUSR 群組
- 設定 NDES 服務帳戶的 SPN

1. 在裝載 NDES 的伺服器上，以**企業系統管理員**的身分登入，然後使用[新增角色及功能精靈](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831809(v=ws.11))來安裝 NDES：

   1. 在精靈中，選取 [Active Directory 憑證服務]  以存取 AD CS 角色服務。 選取 [網路裝置註冊服務] ，取消核取 [憑證授權單位] ，然後完成精靈。

      > [!TIP]
      > 在 [安裝進度] 中，不要選取 [關閉]。 相反地，請選取 [設定目的地伺服器上的 Active Directory 憑證服務] 連結。 [AD CS 設定] 精靈隨即開啟，讓您用於下一個工作。 [AD CS 設定] 開啟之後，您可以關閉 [新增角色及功能精靈]。

   2. 當 NDES 加入至伺服器時，精靈也會安裝 IIS。 請確定 IIS 具有下列組態：

   3. [Web 伺服器] > [安全性] > [要求篩選]

   4. [Web 伺服器] > [應用程式開發] > [ASP.NET 3.5]。 安裝 ASP.NET 3.5 時會安裝 .NET Framework 3.5。 安裝 .NET Framework 3.5 時，請安裝核心 [.NET Framework 3.5]  功能和 [HTTP 啟動] 。

   5. [Web 伺服器] > [應用程式開發] > [ASP.NET 4.5]。 安裝 ASP.NET 4.5 時會安裝 .NET Framework 4.5。 安裝 .NET Framework 4.5 時，請安裝核心 [.NET Framework 4.5] 功能、[ASP.NET 4.5] 與 [WCF 服務] > [HTTP 啟動] 功能。

   6. [管理工具] > [IIS 6 管理相容性] > [IIS 6 Metabase 相容性]

   7. [管理工具] > [IIS 6 管理相容性] > [IIS 6 WMI 相容性]

   8. 在伺服器上，新增 NDES 服務帳戶成為 **IIS_IUSR** 群組的成員身分。

2. 在提升權限的命令提示字元中，執行下列命令來設定 NDES 服務帳戶的 SPN：

    `setspn -s http/<DNS name of NDES Server> <Domain name>\<NDES Service account name>`

    例如，如果 NDES 伺服器的名稱為 **Server01**，您的網域是 **Contoso.com**，而且服務帳戶是 **NDESService**，請使用：

    `setspn –s http/Server01.contoso.com contoso\NDESService`

#### <a name="step-4---configure-ndes-for-use-with-intune"></a>步驟 4：設定 NDES 以搭配 Intune 使用
在此工作中，您要：

- 設定 NDES 以便用於發行 CA
- 在 IIS 中繫結伺服器驗證 (SSL) 憑證
- 設定 IIS 中的要求篩選

1. 在 NDES 伺服器上，開啟 [AD CS 設定] 精靈，然後進行下列設定：

    > [!TIP]
    > 如果您按一下前個工作中的連結，此精靈已經開啟。 否則，開啟 [伺服器管理員] 來存取 Active Directory 憑證服務的部署後組態。

   - 在 [角色服務]  中，選取 [網路裝置註冊服務] 
   - 在 [NDES 的服務帳戶] 中，輸入 NDES 服務帳戶
   - 在 [NDES 的 CA] 中，按一下 [選取]，然後選取您設定憑證範本的發行 CA
   - 在 [NDES 的密碼編譯] 中，設定符合您公司需求的金鑰長度。
   - 在 [確認] 中，選取 [設定]  來完成精靈。

2. 在精靈完成之後，在 NDES 伺服器上更新下列登錄機碼：

    `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Cryptography\MSCEP\`

    若要更新此機碼，請指出憑證範本的 [目的] (可以在其 [要求處理] 索引標籤上找到)。 接著，透過使用您在工作 1 中指定的憑證範本名稱 (而非範本的顯示名稱) 來取代現有資料，以更新對應的登錄項目。 下表會將憑證範本目的對應到登錄中的值：

    |憑證範本目的 (在 [處理要求] 索引標籤上)|要編輯的登錄值|SCEP 設定檔的 Intune 管理主控台中看到的值|
    |---|---|---|
    |簽章|SignatureTemplate|數位簽章|
    |加密|EncryptionTemplate|金鑰加密|
    |簽章和加密|GeneralPurposeTemplate|金鑰加密<br/>數位簽章|

    例如，如果您的憑證範本目的是 [加密] ，則請將 **EncryptionTemplate** 值編輯為憑證範本的名稱。

3. NDES 伺服器會收到長的 URL (查詢)，而這需要您新增兩個登錄項目︰


   |                        位置                        |      值      | 類型  |      資料       |
   |--------------------------------------------------------|-----------------|-------|-----------------|
   | HKLM\SYSTEM\CurrentControlSet\Services\HTTP\Parameters | MaxFieldLength  | DWORD | 65534 (十進位) |
   | HKLM\SYSTEM\CurrentControlSet\Services\HTTP\Parameters | MaxRequestBytes | DWORD | 65534 (十進位) |


4. 在 IIS 管理員中，選取 [預設的網站] > [要求篩選] > [編輯功能設定]。 將 [URL 長度上限] 與 [查詢字串上限] 變更為 *65534*，如下所示：

    ![IIS URL 和查詢長度上限](./media/SCEP_IIS_max_URL.png)

5. 重新啟動伺服器。 在伺服器上執行 **iisreset** 不足以完成這些變更。
6. 瀏覽至 `http://*FQDN*/certsrv/mscep/mscep.dll`。 您應該會看到與下面類似的 NDES 頁面︰

    ![測試 NDES](./media/SCEP_NDES_URL.png)

    如果您收到「503 服務無法使用」，請檢查事件檢視器。 因為遺失 NDES 使用者的權限，所以可能已停止應用程式集區。 工作 1 會說明這些權限。

##### <a name="install-and-bind-certificates-on-the-ndes-server"></a>在 NDES 伺服器上安裝並繫結憑證

1. 在 NDES 伺服器上，要求並安裝來自內部 CA 或公用 CA 的 **伺服器驗證** 憑證。 然後將此 SSL 憑證繫結在 IIS 中。

    > [!TIP]
    > 在 IIS 中繫結 SSL 憑證之後，安裝用戶端驗證憑證。 此憑證可以由 NDES 伺服器所信任的任何 CA 發出。 雖然不是最佳做法，但您可以使用相同的憑證，進行伺服器和用戶端驗證，只要憑證中同時有雙方的增強金鑰使用方法 (EKU) 即可。 請檢閱以下的步驟，以取得這些驗證憑證的相關資訊。

   1. 取得伺服器驗證憑證之後，請開啟 [IIS 管理員] 並選取 [預設的網站]。 在 [動作] 窗格中，選取 [繫結]。

   2. 選取下 [新增]，將 [類型] 設定為 [https]，然後確認連接埠是 [443]。 獨立版 Intune 只支援連接埠 443。

   3. 針對 [SSL 憑證]，輸入伺服器驗證憑證。

      > [!NOTE]
      > 若 NDES 伺服器針對單一網路位址使用外部與內部名稱，則伺服器驗證憑證必須有：
      > - 具有外部公開伺服器名稱的**主體名稱**
      > - 包含內部伺服器名稱的**主體別名**

2. 在 NDES 伺服器上，從內部 CA 或公開憑證授權單位，要求並安裝 **用戶端驗證** 憑證。 這可以是與伺服器驗證憑證相同的憑證，如果該憑證具備兩種功能。

    用戶端驗證憑證必須具有下列屬性：

    - **增強金鑰使用方法**：這必須包括 [用戶端驗證]

    - **主體名稱**：這必須等於您要在其上安裝憑證之伺服器 (NDES 伺服器) 的 DNS 名稱

##### <a name="configure-iis-request-filtering"></a>設定 IIS 要求篩選

1. 在 NDES 伺服器上，開啟 [IIS 管理員]，在 [連線] 窗格中選取 [預設的網站] ，然後開啟 [要求篩選]。

2. 選取 [編輯功能設定]，然後設定下列值：

    - **查詢字串 (位元組)** = **65534**
    - **URL 長度上限 (位元組)** = **65534**

3. 檢閱下列登錄機碼：

    `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\HTTP\Parameters`

    確認下列值設定為 DWORD 項目：

    - 名稱： **MaxFieldLength**，具有十進位值 **65534**
    - 名稱： **MaxRequestBytes**，具有十進位值 **65534**

4. 重新啟動 NDES 伺服器。 伺服器現在已準備好支援 Certificate Connector。

#### <a name="step-5---enable-install-and-configure-the-intune-certificate-connector"></a>步驟 5：啟用、安裝及設定 Intune 憑證連接器
在此工作中，您要：

- 啟用 Intune 中的 NDES 支援。
- 在您環境中裝載網路裝置註冊服務 (NDES) 角色的伺服器上，下載、安裝及設定憑證連接器。 若要增加您組織的 NDES 實作規模，您可以在每部 NDES 伺服器上，搭配 Microsoft Intune 憑證連接器安裝多部 NDES 伺服器。

##### <a name="download-install-and-configure-the-certificate-connector"></a>下載、安裝及設定憑證連接器
![ConnectorDownload](./media/certificates-download-connector.png)

1. 登入 [Azure 入口網站](https://portal.azure.com)。
2. 選取 [All services] (所有服務)，篩選 [Intune]，然後選取 [Microsoft Intune]。
3. 選取 [裝置設定] [憑證授權單位]。
4. 選取 [新增] 並選取 [下載連接器檔案]。 將下載項目儲存到要安裝下載項目的伺服器所能存取的位置。
5. 下載完成之後，在裝載網路裝置註冊服務 (NDES) 角色的伺服器上執行下載的安裝程式 (**ndesconnectorssetup.exe**)。 安裝程式也會安裝 NDES 和 CRP Web 服務的原則模組。 (CRP Web 服務 CertificateRegistrationSvc 會以 IIS 中的應用程式方式執行。)

    > [!NOTE]
    > 當您為獨立版 Intune 安裝 NDES 時，CRP 服務會自動與 Certificate Connector 一起安裝。 當您使用 Intune 搭配 Configuration Manager 時，將憑證註冊點安裝為個別的網站系統角色。

6. 當提示您提供憑證連接器的用戶端憑證時，請選擇 [選取]，然後選取您在工作 3 中，於 NDES 伺服器上安裝的**用戶端驗證**憑證。

    選取用戶端驗證憑證之後，您會回到 [Microsoft Intune Certificate Connector 的用戶端憑證]  介面。 雖然未顯示您選取的憑證，請選取 [下一步] 以檢視該憑證的屬性。 選取 [下一步] [安裝]。
    
    > [!IMPORTANT]
    > 啟用 Internet Explorer 增強式安全性設定的裝置上無法註冊 Intune 憑證連接器。 若要使用 Intune 憑證連接器，請[停用 IE 增強式安全性設定](https://technet.microsoft.com/library/cc775800(v=WS.10).aspx)。

7. 在精靈完成後，但在關閉精靈之前，按一下 [啟動 Certificate Connector UI]。

    > [!TIP]
    > 如果您在啟動 Certificate Connector UI 之前關閉精靈，您可以藉由執行下列命令重新加以開啟：
    >
    > <install_Path>\NDESConnectorUI\NDESConnectorUI.exe

8. 在 **Certificate Connector** UI 中：

    選取 [登入] 並輸入您的 Intune 服務系統管理員認證，或擁有全域系統管理權限的租用戶管理員認證。

    > [!IMPORTANT]
    > 使用者帳戶必須指派有效的 Intune 授權。 如果使用者帳戶沒有有效的 Intune 授權，則 NDESConnectorUI.exe 就會失敗。

    如果您的組織使用 Proxy 伺服器，而且 NDES 伺服器需要該 Proxy 以存取網際網路，請選取 [使用 Proxy 伺服器]，然後輸入 Proxy 伺服器名稱、連接埠，以及用以連線的帳戶認證。

    選取 [進階] 索引標籤，然後輸入對您的發行憑證授權單位具有 [發行及管理憑證] 權限的帳戶認證。 **套用**您的變更。

    您現在可以關閉 Certificate Connector UI。

9. 開啟命令提示字元，輸入 **services.msc** **Enter**。 以滑鼠右鍵按一下 [Intune 連接器服務] [重新啟動]。

若要驗證服務正在執行，請開啟瀏覽器並輸入下列 URL。 這應該會傳回 **403** 錯誤：

`http://<FQDN_of_your_NDES_server>/certsrv/mscep/mscep.dll`

## <a name="create-a-scep-certificate-profile"></a>建立 SCEP 憑證設定檔

1. 在 Azure 入口網站中，開啟 Microsoft Intune。
2. 依序選取 [裝置設定] 及 [設定檔]，然後選取 [建立設定檔]。
3. 輸入 SCEP 憑證設定檔的 [名稱] 與 [描述]。
4. 從 [平台] 下拉式清單中，選取此 SCEP 憑證的裝置平台。 您目前可選取下列平台之一，進行裝置限制設定︰
   - **Android**
   - **iOS**
   - **macOS**
   - **Windows Phone 8.1**
   - **Windows 8.1 及更新版本**
   - **Windows 10 及更新版本**
5. 從 [設定檔類型] 下拉式清單中，選取 [SCEP 憑證]。
6. 在 [SCEP 憑證] 窗格中，進行以下設定：

   - **憑證有效期間**：如果您已在發行 CA 上執行 `certutil - setreg Policy\EditFlags +EDITF_ATTRIBUTEENDDATE` 命令以允許自訂有效期間，就可以輸入憑證到期之前的剩餘時間長度。<br>您可以輸入一個比憑證範本中指定的有效期間更低，而不是更高的值。 例如，如果憑證範本中的憑證有效期間為兩年，您可以輸入一年而不是五年的值。 該值也必須低於發行 CA 憑證的剩餘有效期。 
   - **金鑰儲存提供者 (KSP)** (Windows Phone 8.1、Windows 8.1、Windows 10)：輸入儲存憑證金鑰的位置。 選擇下列其中一個值：
     - **註冊至受信任平台模組 (TPM) KSP (如果存在)，否則註冊至軟體 KSP**
     - **註冊至信賴平台模組 (TPM) KSP，否則失敗**
     - **註冊至 Passport，否則失敗 (Windows 10 及更新版本)**
     - **註冊至軟體 KSP**

   - **主體名稱格式**：從清單中選取 Intune 如何自動在憑證要求中建立主體名稱。 如果憑證是針對使用者，您也可以在主體名稱中包含使用者的電子郵件地址。 從下列選項進行選擇：
     - **未設定**
     - **一般名稱**
     - **包括電子郵件的一般名稱**
     - **一般名稱及電子郵件地址**
     - **IMEI (國際行動設備識別)**
     - **序號**
     - **自訂**：當您選取此選項時，會顯示另一個下拉式欄位。 您可以使用此欄位輸入自訂主體名稱格式。 自訂格式支援兩個變數： **(CN)** 與**電子郵件 (E)**。 **一般名稱 (CN)** 可以設定為下列任何變數：
       - **CN={{UserName}}** 使用者的使用者主體名稱，例如 janedoe@contoso.com
       - **CN={{AAD_Device_ID}}** 當您在 Azure Active Directory (AD) 中註冊裝置時指派的識別碼。 此識別碼通常用於向 Azure AD 驗證。
       - **CN={{SERIALNUMBER}}**：通常由製造商用於識別裝置的唯一序號 (SN)
       - **CN={{IMEINumber}}**：用於識別行動電話的國際行動設備識別碼 (IMEI)
       - **CN={{OnPrem_Distinguished_Name}}** 由逗號分隔的相對辨別名稱序列，例如 `CN=Jane Doe,OU=UserAccounts,DC=corp,DC=contoso,DC=com`

          若要使用 `{{OnPrem_Distinguished_Name}}` 變數，請務必將使用 [Azure AD Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect) 的 `onpremisesdistingishedname` 使用者屬性與 Azure AD 同步。

       - **CN={{onPremisesSamAccountName}}**：系統管理員可使用 Azure AD 連線到稱為 `onPremisesSamAccountName` 的屬性，將 Active Directory 的 samAccountName 屬性與 Azure AD 同步。 Intune 可將該變數替換為 SCEP 憑證主體中憑證發行要求的一部分。  samAccountName 屬性是使用者登入名稱，用於支援舊版 Windows 客戶端和伺服器 (Windows 2000 以前的版本)。 使用者登入名稱的格式為：`DomainName\testUser`，或僅 `testUser`。

          若要使用 `{{onPremisesSamAccountName}}` 變數，請務必將使用 [Azure AD Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect) 的 `onPremisesSamAccountName` 使用者屬性與 Azure AD 同步。

       透過使用一或多個這些變數與靜態字串的組合，您可以建立自訂主體名稱格式，例如：**CN={{UserName}},E={{EmailAddress}},OU=Mobile,O=Finance Group,L=Redmond,ST=Washington,C=US**。 <br/> 在此範例中，您建立的主體名稱格式除了有 CN 與 E 變數之外，還會使用組織單位、組織、位置、狀態及國家/地區值的字串。 [CertStrToName 函式](https://msdn.microsoft.com/library/windows/desktop/aa377160.aspx) 說明此函式和它支援的字串。

- **主體別名**：輸入 Intune 如何在憑證要求中，自動建立主體別名 (SAN) 的值。 例如，如果您選取使用者憑證類型，就可以在主體別名中包含使用者主體名稱 (UPN)。 如果用戶端憑證將用來驗證網路原則伺服器，您必須將主體別名設定成 UPN。
- **金鑰使用方法**：輸入憑證的金鑰使用方法選項。 選項包括：
  - **金鑰編密**：只允許在金鑰加密後交換金鑰
  - **數位簽章**：只允許在以數位簽章協助保護金鑰後交換金鑰
- **金鑰大小 (位元)**：選取金鑰中要包含的位元數
- **雜湊演算法** (Android、Windows Phone 8.1、Windows 8.1、Windows 10)：選取其中一種可用的雜湊演算法類型，搭配此憑證使用。 選取連線中裝置所支援的最強安全性層級。
- **根憑證**：選擇您先前所設定並指派到使用者或裝置的根 CA 憑證設定檔。 此 CA 憑證必須是發行憑證 (您在此憑證設定檔中設定) 之 CA 的根憑證。
- **擴充金鑰使用方法**：選擇 [新增] 以新增憑證使用目的值。 在大部分情況下，憑證需要 [用戶端驗證]，使用者或裝置才能向伺服器進行驗證。 不過，您可以視需要新增任何其他金鑰使用方式。
- **註冊設定**
  - **更新閾值 (%)**：輸入裝置要求憑證更新之前，剩餘的憑證存留時間百分比。
  - **SCEP 伺服器 URL**：輸入 一或多個將透過 SCEP 發行憑證的 NDES 伺服器 URL。
  - 選取 [確定]然後選取 [建立] 以建立您的設定檔。

設定檔隨即建立，並出現在 [設定檔清單] 窗格上。

## <a name="assign-the-certificate-profile"></a>指派憑證設定檔

將憑證設定檔指派給群組之前，請考慮下列事宜︰

- 當您指派憑證設定檔給群組時，來自受信任 CA 憑證設定檔的憑證檔案，即會安裝在裝置上。 裝置會使用 SCEP 憑證設定檔來建立裝置所要求的憑證。
- 憑證設定檔只會安裝在執行於您建立設定檔時所用的平台裝置上。
- 您可以將憑證設定檔指派到使用者集合或裝置集合。
- 若要在裝置註冊之後快速將憑證發行至裝置，請將憑證設定檔指派到使用者群組，而不是裝置群組。 如果您將它指派至裝置群組，便必須先執行完整的裝置註冊，裝置才能接收原則。
- 雖然您會分別指派每個設定檔，但仍需指派受信任的根 CA 以及 SCEP 或 PKCS 設定檔。 否則，SCEP 或 PKCS 憑證原則會失敗。

    > [!NOTE]
    > 針對 iOS，如果您部署多個使用相同憑證設定檔的資源設定檔，就應該會在管理設定檔中看到多個憑證複本。
    
如需如何指派設定檔的相關資訊，請參閱[如何指派裝置設定檔](device-profile-assign.md)。

## <a name="intune-connector-events-and-diagnostic-codes"></a>Intune 連接器事件和診斷碼

從 6.1803.x.x 版開始，Intune 連接器服務會在 [事件檢視器] ([應用程式及服務記錄檔] > [Microsoft Intune 連接器]) 中記錄事件。 您可以使用這些事件來協助對 Intune 連接器設定中的潛在問題進行疑難排解。 這些事件會記錄作業的成功與失敗，還會包含診斷碼及訊息，以協助 IT 系統管理員進行疑難排解。

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
| 20300 | Download_Success | 已成功下載簽署憑證、下載用戶端憑證或撤銷憑證的要求。 請檢閱下載詳細資料的事件詳細資料。  | 0x00000000、0x0FFFFFFF |
| 20302 | Download_Failure | 無法下載簽署憑證、下載用戶端憑證或撤銷憑證的要求。 請檢閱下載詳細資料的事件詳細資料。 | 0x00000000、0x0FFFFFFF |
| 20400 | Upload_Success | 已成功上傳憑證的要求或撤銷資料。 請檢閱上傳詳細資料的事件詳細資料。 | 0x00000000、0x0FFFFFFF |
| 20402 | Upload_Failure | 無法上傳憑證的要求或撤銷資料。 請檢閱事件詳細資料 > 上傳狀態，以判斷失敗點。| 0x00000000、0x0FFFFFFF |
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
| 0x00000401 | Symantec_ClientAuthCertNotFound  | 本機憑證存放區中找不到 Symantec 用戶端驗證憑證。 請參閱[安裝 Symantec 註冊驗證憑證](https://docs.microsoft.com/en-us/intune/certificates-symantec-configure#install-the-symantec-registration-authorization-certificate)一文，以取得詳細資料。  |
| 0x00000402 | RevokeCert_AccessDenied  | 指定的帳戶無權撤銷來自 CA 的憑證。 請參閱事件訊息詳細資料中的 CA 名稱欄位，以判斷發行的 CA。  |
| 0x00000403 | CertThumbprint_NotFound  | 找不到符合您輸入的憑證。 請註冊憑證連接器，然後再試一次。 |
| 0x00000404 | Certificate_NotFound  | 找不到符合所提供輸入的憑證。 請重新註冊憑證連接器，然後再試一次。 |
| 0x00000405 | Certificate_Expired  | 憑證已過期。 請重新註冊憑證連接器以更新憑證，然後再試一次。 |
| 0x00000408 | CRPSCEPCert_NotFound  | 找不到 CRP 加密憑證。 請確認 NDES 和 Intune 連接器已正確設定。 |
| 0x00000409 | CRPSCEPSigningCert_NotFound  | 無法擷取簽署憑證。 請確認 Intune 連接器服務已設定正確，且 Intune 連接器服務正在執行。 另請確認憑證下載事件已成功。 |
| 0x00000410 | CRPSCEPDeserialize_Failed  | 無法還原序列化 SCEP 挑戰要求。 請確認 NDES 和 Intune 連接器已正確設定。 |
| 0x00000411 | CRPSCEPChallenge_Expired  | 由於憑證挑戰過期，已拒絕要求。 用戶端裝置可以在從管理伺服器取得新挑戰之後重試。 |
| 0x0FFFFFFFF | Unknown_Error  | 我們無法完成您的要求，因為發生伺服器端錯誤。 請再試一次。 |

## <a name="next-steps"></a>接下來的步驟
[使用 PKCS 憑證](certficates-pfx-configure.md)，或[從 Symantec PKI Manager Web 服務發行 PKCS 憑證](certificates-symantec-configure.md)。

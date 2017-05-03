---
title: "透過 Intune 設定並管理 PKCS 憑證"
titleSuffix: Intune Azure preview
description: "Intune Azure 預覽版︰了解如何透過 Intune 設定基礎結構，並建立及指派 PKCS 憑證。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 04/22/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e189ebd1-6ca1-4365-9d5d-fab313b7e979
ms.reviewer: vinaybha
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 8b2bd3ecba0b597bc742ea08872ffe8fc58155cf
ms.openlocfilehash: 11bb2cbcf14abe5966e0b203ba3466adc12bd4dd
ms.lasthandoff: 04/24/2017



---
# <a name="configure-and-manage-pkcs-certificates-with-intune"></a>透過 Intune 設定並管理 PKCS 憑證
[!INCLUDE[azure_preview](../includes/azure_preview.md)]

本主題說明如何透過 Intune 設定基礎結構，並建立及指派 PKCS 憑證設定檔。

若要在組織中執行任何憑證式驗證，需要企業憑證授權單位。

若要使用 PKCS 憑證設定檔，除了企業憑證授權單位之外，您還需要︰

-   可以與憑證授權單位通訊的電腦，或者您可以使用憑證授權單位電腦本身。

-  Intune Certificate Connector，其在可與憑證授權單位通訊的電腦上執行。

## <a name="important-terms"></a>重要詞彙


-    **Active Directory 網域**：本節所列的所有伺服器 (除了 Web 應用程式 Proxy 伺服器) 均須加入 Active Directory 網域。

-  **憑證授權單位**：在企業版 Windows Server 2008 R2 或更新版本上執行的企業憑證授權單位 (CA)。 不支援獨立 CA。 如需如何設定憑證授權單位的指示，請參閱 [安裝憑證授權單位](http://technet.microsoft.com/library/jj125375.aspx)。
    如果您的 CA 執行 Windows Server 2008 R2，您必須 [從 KB2483564 安裝 Hotfix](http://support.microsoft.com/kb/2483564/)。

-  **可以與憑證授權單位通訊的電腦**：也可以使用憑證授權單位電腦本身。
-  **Microsoft Intune 憑證連接器**︰從 Azure 入口網站下載**憑證連接器**安裝程式 (**ndesconnectorssetup.exe**)。 然後您可以在要安裝 Certificate Connector 的電腦上執行 **ndesconnectorssetup.exe** 。 為 PKCS 憑證設定檔在與憑證授權單位通訊的電腦上安裝憑證連接器。
-  **Web 應用程式 Proxy 伺服器** (選用)︰您可以將執行 Windows Server 2012 R2 或更新版本的伺服器用作 Web 應用程式 Proxy (WAP) 伺服器。 此組態：
    -  允許裝置使用網際網路連線接收憑證。
    -  是裝置連線透過網際網路來接收和更新憑證時的安全性建議。

 > [!NOTE]           
> -    裝載 WAP 的伺服器[必須安裝更新](http://blogs.technet.com/b/ems/archive/2014/12/11/hotfix-large-uri-request-in-web-application-proxy-on-windows-server-2012-r2.aspx)，以允許支援網路裝置註冊服務 (NDES) 所使用的長 URL。 此更新隨附於 [2014 年 12 月更新彙總套件](http://support.microsoft.com/kb/3013769)，或個別提供於 [KB3011135](http://support.microsoft.com/kb/3011135)。
>-  此外，裝載 WAP 的伺服器必須有 SSL 憑證，該憑證符合發佈給外部用戶端的名稱，並且信任 NDES 伺服器上使用的 SSL 憑證。 這些憑證讓 WAP 伺服器能從用戶端終止 SSL 連線，以及建立與 NDES 伺服器的新 SSL 連線。
    如需 WAP 憑證的相關資訊，請參閱[計劃使用 Web 應用程式 Proxy 發行應用程式](https://technet.microsoft.com/library/dn383650.aspx)的**規劃憑證**小節。 如需 WAP 伺服器的一般資訊，請參閱[使用 Web 應用程式 Proxy](http://technet.microsoft.com/library/dn584113.aspx)。|


## <a name="certificates-and-templates"></a>憑證和範本

|物件|詳細資料|
|----------|-----------|
|**憑證範本**|在發行的 CA 上所設定的範本。|
|**可信任的根 CA 憑證**|您會從發行 CA (或任何信任發行 CA 的裝置) 將此匯出為 **.cer** 檔案，並使用受信任的 CA 憑證設定檔將它指派給裝置。<br /><br />您針對每個作業系統平台使用單一受信任根 CA 憑證，並將它與您建立的每個受信任根憑證設定檔產生關聯。<br /><br />您可以在需要時使用其他受信任根 CA 憑證。 比方說，當您需要向 CA 提供信任，好讓它為您簽署 Wi-Fi 存取點的伺服器驗證憑證時，您可能就會這麼做。|


## <a name="configure-your-infrastructure"></a>設定基礎結構
在您可以設定憑證設定檔之前，必須先完成下列步驟。 執行這些步驟需要對 Windows Server 2012 R2 及 Active Directory 憑證服務 (ADCS) 有一定程度的了解：

- **步驟 1**：設定憑證授權單位上的憑證範本。
- **步驟 2**：啟用、安裝及設定 Intune 憑證連接器。

## <a name="step-1---configure-certificate-templates-on-the-certification-authority"></a>步驟 1：設定憑證授權單位上的憑證範本

### <a name="to-configure-the-certification-authority"></a>設定憑證授權單位

1.  在發行 CA 上，使用 [憑證範本] 嵌入式管理單元建立新的自訂範本，或複製及編輯現有的範本 (例如使用者範本) 來使用 PKCS。

    範本必須包含下列項目：

    -   指定範本的易記「範本顯示名稱」  。

    -   在 [主體名稱]  索引標籤上，選取 [在要求中提供] 。 (安全性由 NDES 的 Intune 原則模組加強)。

    -   在 [延伸]  索引標籤上，確定 [應用程式原則描述]  包含 [用戶端驗證] 。

        > [!IMPORTANT]
        > 若為 iOS 和 macOS 憑證範本，請在 [延伸模組] 索引標籤上，編輯 [金鑰使用方法]，並確認未選取 [簽章是原件證明]。

2.  檢閱範本 [一般]  索引標籤上的 [有效期間]  。 根據預設，Intune 使用範本中所設定的值。 不過，您可以選擇設定 CA 以允許要求者指定不同的值，然後您可以從 Intune 管理主控台內設定該值。 如果您想要一律使用範本中的值，請略過此步驟中的其餘部分。

    > [!IMPORTANT]
    > iOS 和 macOS 一律會使用範本中的值，而不管您所做的其他組態設定。

    若要設定 CA 以允許要求者指定有效期間，請在 CA 上執行下列命令：

    a.  **certutil -setreg Policy\EditFlags +EDITF_ATTRIBUTEENDDATE**

    b。  **net stop certsvc**

    c.  **net start certsvc**

3.  在發行的 CA 上使用 [憑證授權單位] 嵌入式管理單元來發行憑證範本。

    a.  選取 [憑證範本] 節點，並按一下 [動作]-&gt; [新增]&gt; [要發出的憑證範本]，然後選取您在步驟 2 中建立的範本。

    b。  檢視 [憑證範本]  資料夾下的發行範本來加以驗證。

4.  在 CA 電腦上，確認裝載 Intune 憑證連接器的電腦具備註冊權限，能夠存取建立 PKCS 憑證設定檔時所使用的範本。 在 CA 電腦內容的 [安全性]  索引標籤上設定該權限。

## <a name="step-2---enable-install-and-configure-the-intune-certificate-connector"></a>步驟 2：啟用、安裝及設定 Intune 憑證連接器
在這個步驟中，您將：

- 啟用針對憑證連接器的支援
- 下載、安裝及設定憑證連接器。

### <a name="to-enable-support-for-the-certificate-connector"></a>啟用針對憑證連接器的支援

1.  登入 Azure 入口網站。
2.  選擇 [更多服務]  >  [其他]  >  [Intune]。
3.  在 [Intune] 刀鋒視窗中選擇 [設定裝置]。
2.  在 [裝置設定] 刀鋒視窗中選擇 [設定]  >  [憑證授權單位]。
2.  在 [步驟 1] 中選擇 [啟用]。

### <a name="to-download-install-and-configure-the-certificate-connector"></a>下載、安裝及設定憑證連接器

1.  在 [設定裝置] 刀鋒視窗中選擇 [設定]  >  [憑證授權單位]。
2.  選擇 [下載憑證連接器]。
2.  下載完成後，執行下載的安裝程式 (**ndesconnectorssetup.exe**)。
  在可連接至憑證授權單位的電腦上執行安裝程式。 選擇 PKCS (PFX) 發佈選項，然後選擇 [安裝]。 安裝完成後，請依照[如何設定憑證設定檔](how-to-configure-certificates.md)所述建立憑證設定檔。

3.  當提示您提供憑證連接器的用戶端憑證時，請選擇 [選取]，然後選取您安裝的**用戶端驗證**憑證。

    選取用戶端驗證憑證之後，您會回到 [Microsoft Intune Certificate Connector 的用戶端憑證]  介面。 雖然您選取的憑證未顯示，請選擇 [下一步] 檢視該憑證的屬性。 然後依序選擇 [下一步] 與 [安裝]。

4.  在精靈完成後，但在關閉精靈之前，按一下 [啟動 Certificate Connector UI] 。

    > [!TIP]
    > 如果您在啟動 Certificate Connector UI 之前關閉精靈，您可以藉由執行下列命令重新加以開啟：
    >
    > **&lt;安裝路徑&gt;\NDESConnectorUI\NDESConnectorUI.exe**

5.  在 **Certificate Connector** UI 中：

    a. 選擇 [登入] 並輸入您的 Intune 服務管理員認證，或擁有全域管理權限的租用戶管理員認證。

  <!--  If your organization uses a proxy server and the proxy is needed for the NDES server to access the Internet, click **Use proxy server** and then provide the proxy server name, port, and account credentials to connect.-->

    b。 選取 [進階] 索引標籤，然後提供對您的發行憑證授權單位具有 [發行及管理憑證] 權限的帳戶認證。

    c. 選擇 [套用]。

    您現在可以關閉 Certificate Connector UI。

6.  開啟命令提示字元，然後鍵入 **services.msc**。 然後按 **Enter**，以滑鼠右鍵按一下 [Intune 連接器服務]，再選擇 [重新啟動]。

若要驗證服務正在執行，請開啟瀏覽器並輸入下列 URL，這應傳回 **403** 錯誤：

**http:// &lt;NDES 伺服器的 FQDN&gt;/certsrv/mscep/mscep.dll**


### <a name="how-to-create-a-pkcs-certificate-profile"></a>如何建立 PKCS 憑證設定檔

在 Azure 入口網站中，選取 [設定裝置] 工作負載。
2. 在 [裝置設定] 刀鋒視窗中，選擇 [管理]  >  [設定檔]。
3. 在 [設定檔] 刀鋒視窗中，按一下 [建立設定檔]。
4. 在 [建立設定檔] 刀鋒視窗中，為 PKCS 憑證設定檔輸入 [名稱] 及 [描述]。
5. 從 [平台] 下拉式清單中，選取此 PKCS 憑證的來源裝置平台：
    - **Android**
    - **Android for Work**
    - **iOS**
    - **Windows 10 及更新版本**
6. 從 [設定檔類型] 下拉式清單中，選擇 [PKCS 憑證]。
7. 在 [PKCS 憑證] 刀鋒視窗上，進行以下設定：
    - **更新閾值 (%)** - 指定裝置要求憑證更新之前，剩餘的憑證存留時間百分比。
    - **憑證有效期間** - 如果您已在發行 CA 上執行 **certutil - setreg Policy\EditFlags +EDITF_ATTRIBUTEENDDATE** 命令，允許自訂有效期間，則可以指定憑證到期之前的剩餘時間長度。<br>您可以指定一個比憑證範本中指定之有效期間更低，而不是更高的值。 舉例來說，如果憑證範本中的憑證有效期間為兩年，您可以指定一年而不是五年的值。 該值也必須低於發行 CA 憑證的剩餘有效期。
    - **金鑰儲存提供者 (KSP)** (Windows 10)：指定儲存憑證金鑰的位置。 選擇下列其中一個值：
        - **註冊至受信任平台模組 (TPM) KSP (如果存在)，否則註冊至軟體 KSP**
        - **註冊至信賴平台模組 (TPM) KSP，否則失敗**
        - **註冊至 Passport，否則失敗 (Windows 10 及更新版本)**
        - **註冊至軟體 KSP**
    - **憑證授權單位**：在企業版 Windows Server 2008 R2 或更新版本上執行的企業憑證授權單位 (CA)。 不支援獨立 CA。 如需如何設定憑證授權單位的指示，請參閱 [安裝憑證授權單位](http://technet.microsoft.com/library/jj125375.aspx)。 如果您的 CA 執行 Windows Server 2008 R2，您必須 [從 KB2483564 安裝 Hotfix](http://support.microsoft.com/kb/2483564/)。
    - **憑證授權單位名稱**：輸入您的憑證授權單位名稱。
    - **憑證範本名稱**：輸入網路裝置註冊服務設定要使用且已新增至發行 CA 的憑證範本名稱。
    請確定該名稱完全符合執行網路裝置註冊服務的伺服器，於登錄中列出的其中一個憑證範本。 請確定您指定的是憑證範本的名稱，而非憑證範本的顯示名稱。 
    若要尋找憑證範本的名稱，請瀏覽至下列機碼：HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Cryptography\MSCEP。 您將會看見憑證範本已列為 [EncryptionTemplate] 、[GeneralPurposeTemplate] 和 [SignatureTemplate] 的值。 根據預示，這三個憑證範本的值是 [IPSECIntermediateOffline]，對應至 [IPSec (離線要求)] 的範本顯示名稱。 
    - **主體名稱格式**從清單中選取 Intune 如何自動在憑證要求中建立主體名稱。 如果憑證是針對使用者，您也可以在主體名稱中包含使用者的電子郵件地址。 從下列選項進行選擇：
        - **未設定**
        - **一般名稱**
        - **包括電子郵件的一般名稱**
        - **一般名稱及電子郵件地址**
    - **主體別名**指定 Intune 如何在憑證要求中，自動建立主體別名 (SAN) 的值。 舉例來說，如果您選擇使用者憑證類型，您可以在主體別名中包含使用者主體名稱 (UPN)。 如果用戶端憑證將用來驗證網路原則伺服器，您必須將主體別名設定成 UPN。
    - **擴充金鑰使用方法** (Android) - 選擇 [新增] 以新增憑證使用目的值。 在大部分情況下，憑證需要 [用戶端驗證]  ，使用者或裝置才能向伺服器進行驗證。 不過，您可以視需要新增任何其他金鑰使用方式。 
    - **根憑證**- 選擇先前所設定並指派到使用者或裝置的根 CA 憑證設定檔。 此 CA 憑證必須是將發行憑證 (您在此憑證設定檔中設定) 之 CA 的根憑證。 這是您先前所建立的受信任憑證設定檔。
8. 當您完成時，請返回 [建立設定檔] 刀鋒視窗，然後點擊 [建立]。

隨即會建立設定檔，並會出現在 [設定檔清單] 刀鋒視窗上。

## <a name="how-to-assign-the-certificate-profile"></a>如何指派憑證設定檔

將憑證設定檔指派給群組之前，請考慮下列事宜︰

- 當您指派憑證設定檔給群組時，來自受信任 CA 憑證設定檔的憑證檔案，即會安裝在裝置上。 裝置會使用 PKCS 憑證設定檔來建立裝置所要求的憑證。
- 憑證設定檔只會安裝在執行於您建立設定檔時所用的平台裝置上。
- 您可以將憑證設定檔指派到使用者集合或裝置集合。
- 若要在裝置註冊之後快速將憑證發行至裝置，請將憑證設定檔指派到使用者群組，而不是裝置群組。 如果您將它指派至裝置群組，便必須先執行完整的裝置註冊，裝置才能接收原則。
- 雖然您會分別指派每個設定檔，但仍需指派受信任的根 CA 以及 PKCS 設定檔。 否則，PKCS 憑證原則會失敗。

如需如何指派設定檔的相關資訊，請參閱[如何指派裝置設定檔](how-to-assign-device-profiles.md)。


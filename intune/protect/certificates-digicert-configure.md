---
title: 透過 Microsoft Intune 發出 DigiCert PKCS 憑證
titleSuffix: Microsoft Intune
description: 安裝並設定 Intune 憑證連接器，以從 DigiCert PKI 平台向受 Intune 管理的裝置發出 PKCS 憑證。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/07/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: ca76ffe0c8fa42f1c2cf24fcdefd287140231220
ms.sourcegitcommit: b5e719fb507b1bc4774674e76c856c435e69f68c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/08/2019
ms.locfileid: "73801630"
---
# <a name="set-up-intune-certificate-connector-for-digicert-pki-platform"></a>針對 DigiCert PKI 平台設定 Intune 憑證連接器

使用 Intune 憑證連接器，以從 DigiCert PKI 平台向受 Intune 管理的裝置發出 PKCS 憑證。 您可以只搭配 DigiCert 憑證授權單位 (CA)，或同時搭配 DigiCert CA 和 Microsoft CA 來使用連接器。

> [!TIP]
> DigiCert 已收購 Symantec 的 Website Security 及相關 PKI 解決方案業務。 如需此變更的詳細資訊，請參閱 [Symantec 技術支援文章](https://support.symantec.com/en_US/article.INFO4722.html) \(英文\)。

如果您已經使用 Intune 憑證連接器來透過 PKCS 或 System Center Endpoint Protection 發出來自 Microsoft CA 的憑證，您可以使用相同的連接器來設定和發出來自 DigiCert CA 的 PKCS 憑證。 當您完成支援 DigiCert CA 的設定之後，Intune 憑證連接器就可以發出下列憑證：

* 來自 Microsoft CA 的 PKCS 憑證
* 來自 DigiCert CA 的 PKCS 憑證
* 來自 Microsoft CA 的 Endpoint Protection 憑證

如果您尚未安裝連接器，但計畫同時針對 Microsoft CA 和 DigiCert CA 使用它，請先完成 Microsoft CA 的連接器設定。 然後，返回本文，以將它設定為也支援 DigiCert。 如需憑證設定檔和連接器的詳細資訊，請參閱[在 Microsoft Intune 中設定裝置的憑證設定檔](certificates-configure.md)。  

如果您只會搭配 DigiCert CA 使用連接器，則可使用本文中的指示來安裝連接器，然後加以設定。

## <a name="prerequisites"></a>必要條件

- **DigiCert CA 的有效訂用帳戶**：需要有訂用帳戶，才能從 DigiCert CA 取得登錄授權單位 (RA) 憑證。

## <a name="install-the-digicert-ra-certificate"></a>安裝 DigiCert RA 憑證

1. 將下列程式碼片段儲存在名為 **certreq.ini** 的檔案中，並視需要更新它 (例如：*CN 格式的主體名稱*)。

        [Version] 
        Signature="$Windows NT$" 
        
        [NewRequest] 
        ;Change to your,country code, company name and common name 
        Subject = "Subject Name in CN format"
        
        KeySpec = 1 
        KeyLength = 2048 
        Exportable = TRUE 
        MachineKeySet = TRUE 
        SMIME = False 
        PrivateKeyArchive = FALSE 
        UserProtected = FALSE 
        UseExistingKeySet = FALSE 
        ProviderName = "Microsoft RSA SChannel Cryptographic Provider" 
        ProviderType = 12 
        RequestType = PKCS10 
        KeyUsage = 0xa0 
        
        [EnhancedKeyUsageExtension] 
        OID=1.3.6.1.5.5.7.3.2 ; Client Authentication  // Uncomment if you need a mutual TLS authentication
        
        ;----------------------------------------------- 

2. 開啟提升權限的命令提示字元，並使用下列命令來產生憑證簽署要求 (CSR)：

   `Certreq.exe -new certreq.ini request.csr`

3. 在 [記事本] 中開啟 request.csr 檔案，然後複製下列格式的 CSR 內容：

        -----BEGIN NEW CERTIFICATE REQUEST-----
        MIID8TCCAtkCAQAwbTEMMAoGA1UEBhMDVVNBMQswCQYDVQQIDAJXQTEQMA4GA1UE
        …
        …
        fzpeAWo=
        -----END NEW CERTIFICATE REQUEST-----


4. 登入 DigiCert CA，然後瀏覽至工作中的 [取得 RA 憑證]  。

   a. 在文字方塊中，提供來自步驟 3 的 CSR 內容。

   b. 為憑證提供易記名稱。

   c. 選取 [繼續]  。

   d. 使用提供的連結來將 RA 憑證下載至您的本機電腦。

5. 將 RA 憑證匯入至 Windows 憑證存放區：

   a. 開啟 MMC 主控台。

   b. 選取 [檔案]   > [新增或移除嵌入式管理單元]   > [憑證]   > [新增]  。

   c. 選取 [電腦帳戶]   > [下一步]  。

   d. 選取 [本機電腦]   > [完成]  。

   e. 在 [新增或移除嵌入式管理單元]  視窗中，選取 [確定]  。 展開 [憑證 (本機電腦)]   > [個人]   > [憑證]  。

   f. 以滑鼠右鍵按一下 [憑證]  節點，然後選取 [所有工作]   > [匯入]  。

   g. 選取您從 DigiCert CA 所下載之 RA 憑證的位置，然後選取 [下一步]  。

   h. 選取 [個人憑證存放區]   > [下一步]  。

   i. 選取 [完成]  ，以將 RA 憑證連同其私密金鑰一起匯入至 [本機電腦-個人]  存放區。

6. 匯出及匯入私密金鑰憑證：

   a. 展開 [憑證 (本機電腦)]   > [個人]   > [憑證]  。

   b. 選取於上個步驟中匯入的憑證。

   c. 以滑鼠右鍵按一下憑證，然後選取 [所有工作]   > [匯出]  。

   d. 選取 [下一步]  ，然後輸入密碼。

   e. 選取匯出的目標位置，然後選取 [完成]  。

   f. 使用步驟 5 的程序，以將私密金鑰憑證匯入至 [本機電腦-個人]  存放區。

   g. 記錄 RA 憑證指紋的複本，且不包含任何空格。 以下為指紋範例：

        RA Cert Thumbprint: “EA7A4E0CD1A4F81CF0740527C31A57F6020C17C5”

    > [!NOTE]
    > 如需從 DigiCert CA 取得 RA 憑證的協助，請連絡 [DigiCert 客戶支援](mailto:enterprise-pkisupport@digicert.com)。

## <a name="prepare-to-install-intune-certificate-connector"></a>準備安裝 Intune 憑證連接器

> [!TIP]
> 本節適用於您只會搭配 DigiCert CA 使用 Intune 憑證連接器的情況。 如果您是搭配 Microsoft CA 使用 Intune 憑證連接器，並且想要新增 DigiCert CA 支援，請直接跳到[設定連接器以支援 DigiCert](#configure-the-connector-to-support-digicert)。

1. 從下列清單選擇其中一個 Windows 作業系統版本，並將它安裝於電腦上：
   * Windows Server 2012 R2 Datacenter
   * Windows Server 2012 R2 Standard
   * Windows Server 2016 Datacenter
   * Windows Server 2016 Standard

2. 建立具有系統管理權限的使用者，並使用它來完成下列步驟。

3. 檢查是否有最新的 Windows 更新，並在可用的情況下安裝它們。 安裝 Windows 更新之後，請重新啟動電腦。

4. 安裝 .NET Framework 3.5：

   a. 開啟 [控制台]   > [程式和功能]   > [開啟或關閉 Windows 功能]  。

   b. 選取 [.NET Framework 3.5]  ，然後安裝它。

## <a name="install-intune-certificate-connector-for-use-with-digicert"></a>安裝 Intune 憑證連接器以便與 DigiCert 搭配使用

> [!TIP]
> 如果您是搭配 Microsoft CA 使用 Intune 憑證連接器，並且想要新增 DigiCert CA 支援，請直接跳到[設定連接器以支援 DigiCert](#configure-the-connector-to-support-digicert)。

從 Intune 管理入口網站下載最新的 Intune 憑證連接器版本，並遵循下列指示。

1. 登入 [Microsoft Endpoint Manager 系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。

2. 選取 [租用戶系統管理]   > [連接器與權杖]   > [憑證連接器]   > [+ 新增]  。

3. 針對 PKCS #12 的連接器按一下 [下載憑證連接器軟體]  ，並將該檔案儲存到要安裝連接器的伺服器所能存取位置。

   ![下載連接器軟體](./media/certificates-digicert-configure/connector-download.png)

4. 在您要安裝連接器的伺服器上，以提升的權限執行 **NDESConnectorSetup.exe**。

5. 在 [安裝選項]  頁面上，選取 [PFX 發佈]  。

   ![選取 [PFX 發佈]](./media/certificates-digicert-configure/digicert-ca-connector-install.png)

   > [!IMPORTANT]
   > 如果您將使用 Intune 憑證連接器以發出來自 Microsoft CA 和 Symantec CA 的憑證，請選取 [SCEP 與 PFX 設定檔發佈]  。

6. 使用預設選取項目來完成連接器的設定。

## <a name="configure-the-connector-to-support-digicert"></a>設定連接器以支援 DigiCert

根據預設，Intune 憑證連接器會安裝於 **%ProgramFiles%\Microsoft Intune\NDESConnectorSvc**。

1. 在 **NDESConnectorSvc** 資料夾中，在 [記事本] 中開啟 **NDESConnector.exe.config** 檔案。

   a. 以您在上一節複製的憑證指紋值來更新 `RACertThumbprint` 金鑰值。 例如：

        <add key="RACertThumbprint"
        value="EA7A4E0CD1A4F81CF0740527C31A57F6020C17C5"/>

   b. 儲存並關閉檔案。

2. 開啟 **services.msc**：

   a. 選取 [Intune 連接器服務]  。

   b. 停止服務，然後啟動服務。

   c. 關閉服務的視窗。

## <a name="set-up-the-intune-administrator-account"></a>設定 Intune 管理員帳戶  

> [!TIP]
> 如果您是搭配 Microsoft CA 使用 Intune 憑證連接器，並且想要新增 DigiCert CA 支援，請直接跳到[建立受信任的憑證設定檔](#create-a-trusted-certificate-profile)。
 
1. 從 **%ProgramFiles%\Microsoft Intune\NDESConnectorUI\NDESConnectorUI.exe** 開啟 NDES 連接器使用者介面。

2. 在 [註冊]  索引標籤上，選取 [登入]  。

3. 提供您的 Intune 租用戶管理員認證。

4. 選取 [登入]  ，然後選取 [確定]  以確認註冊成功。 您接著可以關閉 NDES 連接器使用者介面。

   ![顯示 [已成功註冊] 訊息的 NDES 連接器介面](./media/certificates-digicert-configure/certificates-digicert-configure-connector-configure.png)

## <a name="create-a-trusted-certificate-profile"></a>建立受信任的憑證設定檔

您將針對受 Intune 管理的裝置所部署的 PKCS 憑證，必須與受信任的根憑證建立鏈結。 若要建立此鏈結，請搭配來自 DigiCert CA 的根憑證來建立 Intune 受信任的憑證設定檔。

1. 從 DigiCert CA 取得受信任的根憑證：

   a. 登入 DigiCert CA 管理入口網站。

   b. 從 [Tasks]  \(工作\) 中選取 [Manage CAs]  \(管理 CA\)。

   c. 從清單中選取適當的 CA。

   d. 選取 [Download root certificate]  \(下載根憑證\) 以下載受信任的根憑證。

2. 在 Intune 入口網站中，建立受信任的憑證設定檔：

   a. 登入 [Microsoft Endpoint Manager 系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。

   b. 選取 [裝置]   > [組態設定檔]   > [建立設定檔]  。

   c. 輸入下列內容：

      - 設定檔的 [名稱] 
      - 選擇性設定 [描述] 
      - 要部署設定檔的目標 [平台] 
      - 將 [設定檔類型]  設為 [信任的憑證] 

   d. 選取 [設定]  ，然後瀏覽至先前匯出要與此憑證設定檔搭配使用的受信任根 CA 憑證 .cer 檔案，然後選取 [確定]  。

   e. 僅適用於 Windows 8.1 與 Windows 10 裝置，請為來自以下位置的受信任憑證，選取 [目的地存放區]  ︰
      - **電腦憑證存放區 - 根**
      - **電腦憑證存放區 - 中繼**
      - **使用者憑證存放區 - 中繼**

   f. 當您完成時，請選取 [確定]  返回 [建立設定檔]  窗格，然後選取 [建立]  。  

  設定檔隨即會顯示於 [裝置設定 - 設定檔]  窗格的設定檔清單中，且設定檔類型為 [受信任的憑證]  。  請務必將此設定檔指派給將接收憑證的裝置。 若要將設定檔指派給群組，請參閱[指派裝置設定檔](../configuration/device-profile-assign.md)。


## <a name="get-the-certificate-profile-oid"></a>取得憑證設定檔 OID  

憑證設定檔 OID 會與 DigiCert CA 中的憑證設定檔範本建立關聯。 若要在 Intune 中建立 PKCS 憑證設定檔，憑證範本名稱必須是與 DigiCert CA 中憑證範本相關聯之憑證設定檔 OID 的格式。

1. 登入 DigiCert CA 管理入口網站。
2. 選取 [Manage Certificate Profiles]  \(管理憑證設定檔\)。
3. 選取您要使用的憑證設定檔。
4. 複製憑證設定檔 OID。 它看起來會與下列範例類似：

       Certificate Profile OID = 2.16.840.1.113733.1.16.1.2.3.1.1.47196109 

> [!NOTE]
> 如果您需要協助以取得憑證設定檔 OID，請連絡 [DigiCert 客戶支援](mailto:enterprise-pkisupport@digicert.com)。

## <a name="create-a-pkcs-certificate-profile"></a>建立 PKCS 憑證設定檔

1. 登入 [Microsoft Endpoint Manager 系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。

2. 選取 [裝置]   > [組態設定檔]   > [建立設定檔]  。

3. 輸入下列內容：

   - 設定檔的 [名稱] 
   - 選擇性設定 [描述] 
   - 要部署設定檔的目標 [平台] 
   - 將 [設定檔類型]  設為 [PKCS 憑證] 

4. 在 [PKCS 憑證]  窗格中，使用下表中的值來設定參數。 需要這些值，才能透過 Intune 憑證連接器從 DigiCert CA 發出 PKCS 憑證。

   |PKCS 憑證參數 | 值 | 說明 |
   | --- | --- | --- |
   | 憑證授權單位 | pki-ws.symauth.com | 此值必須為不含結尾斜線的 DigiCert CA 基礎服務 FQDN。 如果您不確定這是否為適用於您 DigiCert CA 訂用帳戶的正確基礎服務 FQDN，請連絡 DigiCert 客戶支援。 <br><br>「在從 Symantec 變更為 DigiCert 的情況下，此 URL 會維持不變」  。 <br><br> 如果此 FQDN 不正確，Intune 憑證連接器將不會從 DigiCert CA 發出 PKCS 憑證。| 
   | 憑證授權單位名稱 | Symantec | 此值必須為 **Symantec**字串。 <br><br> 如果對此值進行任何變更，Intune 憑證連接器將不會從 DigiCert CA 發出 PKCS 憑證。|
   | 憑證範本名稱 | 來自 DigiCert CA 的憑證設定檔 OID。 例如：**2.16.840.1.113733.1.16.1.2.3.1.1.61904612**| 此值必須是從 DigiCert CA 憑證設定檔範本[在上一節中取得](#get-the-certificate-profile-oid)的憑證設定檔 OID。 <br><br> 如果 Intune 憑證連接器在 DigiCert CA 中找不到與此憑證設定檔 OID 相關聯的憑證範本，它將不會從 DigiCert CA 發出 PKCS 憑證。|

   ![CA 和憑證範本的選取項目](./media/certificates-digicert-configure/certificates-digicert-pkcs-example.png)

   > [!NOTE]
   > 適用於 Windows 平台的 PKCS 憑證設定檔不需要與受信任的憑證設定檔相關聯。 但這對於非 Windows 平台的設定檔 (例如 Android) 則是必要的。

5. 完成設定檔的設定以符合商務需求，然後選取 [建立]  以儲存設定檔。

6. 在新設定檔的 [概觀]  頁面上，選取 [指派]  ，然後設定將接收此設定檔的適當群組。 指派的群組中至少要有一個使用者或裝置。
 
當您完成先前的步驟之後，Intune 憑證連接器會將來自 DigiCert CA 的 PKCS 憑證發給已指派群組中受 Intune 管理的裝置。 這些憑證將會在受 Intune 管理的裝置上，於 [目前使用者]  憑證存放區的 [個人]  存放區中提供使用。

### <a name="supported-attributes-for-the-pkcs-certificate-profile"></a>PKCS 憑證設定檔支援的屬性

|屬性 | Intune 支援的格式 | DigiCert 雲端 CA 支援的格式 | result |
| --- | --- | --- | --- |
| 主體名稱 |Intune 僅支援下列三種格式的主體名稱： <br><br> 1.一般名稱 <br> 2.包括電子郵件的一般名稱 <br> 3.作為電子郵件的一般名稱 <br><br> 例如： <br><br> `CN = IWUser0 <br><br> E = IWUser0@samplendes.onmicrosoft.com` | DigiCert CA 支援更多屬性。  如果您想要選取更多屬性，就必須在 DigiCert 憑證設定檔範本中以固定值定義它們。| 我們使用來自 PKCS 憑證要求的一般名稱或電子郵件。 <br><br> 在 Intune 憑證設定檔和 DigiCert 憑證設定檔範本之間，若屬性選取項目中有任何差異，將導致不會從 DigiCert CA 發出任何憑證。|
| SAN | Intune 僅支援下列 SAN 欄位值： <br><br> **AltNameTypeEmail** <br> **AltNameTypeUpn** <br> **AltNameTypeOtherName** (編碼值) | DigiCert 雲端 CA 也支援這些參數。 如果您想要選取更多屬性，就必須在 DigiCert 憑證設定檔範本中以固定值定義它們。 <br><br> **AltNameTypeEmail**：如果在 SAN 中找不到此類型，Intune 憑證連接器就會使用來自 **AltNameTypeUpn** 的值。  如果在 SAN 中也找不到 **AltNameTypeUpn**，則 Intune 憑證連接器會使用來自主體名稱的值 (若它為電子郵件格式)。  如果還是找不到此類型，Intune 憑證連接器就無法發出憑證。 <br><br> 範例： `RFC822 Name=IWUser0@ndesvenkatb.onmicrosoft.com`  <br><br> **AltNameTypeUpn**：如果在 SAN 中找不到此類型，Intune 憑證連接器就會使用來自 **AltNameTypeEmail** 的值。 如果在 SAN 中也找不到 **AltNameTypeEmail**，則 Intune 憑證連接器會使用來自主體名稱的值 (若它為電子郵件格式)。 如果還是找不到此類型，Intune 憑證連接器就無法發出憑證。  <br><br> 範例： `Other Name: Principal Name=IWUser0@ndesvenkatb.onmicrosoft.com` <br><br> **AltNameTypeOtherName**：如果在 SAN 中找不到此類型，Intune 憑證連接器就無法發出憑證。 <br><br> 範例： `Other Name: DS Object Guid=04 12 b8 ba 65 41 f2 d4 07 41 a9 f7 47 08 f3 e4 28 5c ef 2c` <br><br>  DigiCert CA 僅支援欄位值為十六進位值的編碼格式。 Intune 憑證連接器會先將此欄位中的所有值都轉換成 Base64 編碼，然後再提交憑證要求。 *Intune 憑證連接器並不會先驗證此值是否已進行編碼。* | 無 |

## <a name="troubleshooting"></a>疑難排解

您可以在 NDES 連接器電腦上的 **%ProgramFiles%\Microsoft Intune\NDESConnectorSvc\Logs\Logs** 中找到 Intune 憑證連接器服務記錄。 在 [SvcTraceViewer](https://docs.microsoft.com/dotnet/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe) \(部分機器翻譯\) 中開啟記錄，然後搜尋例外狀況或錯誤訊息。

| 問題/錯誤訊息 | 解決步驟 |
| --- | --- |
| 無法在 NDES 連接器 UI 上使用 Intune 租用戶管理帳戶登入。 | 若未在 Microsoft Endpoint Manager 系統管理中心內啟用內部部署憑證連接器，就可能發生此情況。 解決此問題： <br><br> 1.登入 [Microsoft Endpoint Manager 系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。 <br> 2.選取 [租用戶系統管理]   > [連接器與權杖]   > [憑證連接器]  。 <br> 3.找出憑證連接器，並確定其已啟用。 <br><br> 完成上述步驟之後，請嘗試在 NDES 連接器 UI 中使用相同的 Intune 租用戶管理帳戶登入。 |
| 找不到 NDES 連接器憑證。 <br><br> System.ArgumentNullException:值不能是 Null。 | 如果 Intune 租用戶系統管理員帳戶從未登入 NDES 連接器 UI，Intune 憑證連接器便會顯示此錯誤。 <br><br> 如果此錯誤持續發生，請重新啟動 Intune 服務連接器。 <br><br> 1.開啟 **services.msc**。 <br> 2.選取 [Intune 連接器服務]  。 <br> 3.以滑鼠右鍵按一下並選取 [重新啟動]  。|
| NDES 連接器 - IssuePfx - 一般例外狀況： <br> System.NullReferenceException：物件參考未設定成物件的執行個體。 | 這是暫時性的錯誤。 請重新啟動 Intune 服務連接器。 <br><br> 1.開啟 **services.msc**。 <br> 2.選取 [Intune 連接器服務]  。 <br> 3.以滑鼠右鍵按一下並選取 [重新啟動]  。 |
| DigiCert 提供者 - 無法取得 DigiCert 原則。 <br><br>「作業已逾時。」 | Intune 憑證連接器在與 DigiCert CA 通訊期間，接收到作業逾時錯誤。 如果此錯誤持續發生，請提高連線逾時值，然後再試一次。 <br><br> 提高連線逾時： <br> 1.移至 NDES 連接器電腦。 <br>2.在 [記事本] 中開啟 **%ProgramFiles%\Microsoft Intune\NDESConnectorSvc\NDESConnector.exe.config** 檔案。 <br> 3.提高下列參數的逾時值： <br><br> `CloudCAConnTimeoutInMilliseconds` <br><br> 4.重新啟動 Intune 憑證連接器服務。 <br><br> 如果此問題持續發生，請連絡 DigiCert 客戶支援。 |
| DigiCert 提供者 - 無法取得用戶端憑證。 | Intune 憑證連接器無法從 [本機電腦-個人] 憑證存放區擷取資源授權憑證。 若要解決此問題，請將資源授權憑證連同其私密金鑰一起安裝於 [本機電腦-個人] 憑證存放區中。 <br><br> 資源授權憑證必須從 DigiCert CA 取得。 如需更多詳細資料，請連絡 DigiCert 客戶支援。 | 
| DigiCert 提供者 - 無法取得 DigiCert 原則。 <br><br>「要求已經中止:無法建立 SSL/TLS 的安全通道」。 | 此錯誤會在下列案例發生： <br><br> 1.Intune 憑證連接器服務無權從 [本機電腦-個人] 憑證存放區讀取資源授權憑證及其私密金鑰。 若要解決此問題，請在 services.msc 中檢查連接器服務的執行中內容帳戶。 連接器服務必須在 NT AUTHORITY\SYSTEM 內容下執行。 <br><br> 2.Intune 管理入口網站中的 PKCS 憑證設定檔可能會使用對 DigiCert CA 無效的基礎服務 FQDN 來設定。 FQDN 類似於 **pki-ws.symauth.com**。 若要解決此問題，請連絡 DigiCert 客戶支援，以確認該 URL 是否適用於您的訂用帳戶。 <br><br> 3.Intune 憑證連接器無法透過資源授權憑證向 DigiCert CA 進行驗證，因為該憑證無法擷取私密金鑰。 若要解決此問題，請將資源授權憑證連同其私密金鑰一起安裝於 [本機電腦-個人] 憑證存放區中。 <br><br> 如果此問題持續發生，請連絡 DigiCert 客戶支援。 |
| DigiCert 提供者 - 無法取得 DigiCert 原則。 <br><br>「無法了解要求元素。」 | Intune 憑證連接器無法取得 DigiCert 憑證設定檔範本，因為用戶端設定檔 OID 與 Intune 憑證設定檔不符。 在另一種情況下，Intune 憑證連接器在 DigiCert CA 中找不到與用戶端設定檔 OID 相關聯的憑證設定檔範本。 <br><br> 若要解決此問題，請從 DigiCert CA 中的 DigiCert 憑證範本中取得正確的用戶端設定檔 OID。 然後在 Intune 管理入口網站中更新 PKCS 憑證設定檔。 <br><br> 從 DigiCert CA 取得用戶端設定檔 OID： <br> 1.登入 DigiCert CA 管理入口網站。 <br> 2.選取 [Manage Certificate Profiles]  \(管理憑證設定檔\)。 <br> 3.選取您要使用的憑證設定檔。 <br> 4.取得憑證設定檔 OID。 它看起來會與下列範例類似： <br> `Certificate Profile OID = 2.16.840.1.113733.1.16.1.2.3.1.1.47196109` <br><br> 使用正確的憑證設定檔 OID來更新 PKCS 憑證設定檔： <br>1.登入 Intune 管理入口網站。 <br> 2.移至 PKCS 憑證設定檔，然後選取 [編輯]  。 <br> 3.在憑證範本名稱的欄位中，更新憑證設定檔 OID。 <br> 4.儲存 PKCS 憑證設定檔。 |
| DigiCert 提供者 - 原則驗證失敗。 <br><br> 此屬性不在 DigiCert 支援的憑證範本屬性清單內。 | 當 DigiCert 憑證設定檔範本和 Intune 憑證設定檔之間出現差異時，DigiCert CA 便會顯示此訊息。 此問題很可能是因為 **SubjectName** 或 **SubjectAltName** 中的屬性不符而造成。 <br><br> 若要解決此問題，請在 DigiCert 憑證設定檔範本中針對 **SubjectName** 和 **SubjectAltName** 選取 Intune 支援的屬性。 如需詳細資訊，請參閱＜憑證參數＞  一節中 Intune 所支援的屬性。 |
| 某些使用者裝置未接收到來自 DigiCert CA 的 PKCS 憑證。 | 此問題會在使用者 UPN 包含像是底線的特殊字元時發生 (範例：`global_admin@intune.onmicrosoft.com`)。 <br><br> DigiCert CA 在 **mail_firstname** 和 **mail_lastname** 中不支援特殊字元。 <br><br> 下列步驟可協助解決此問題： <br><br> 1.登入 DigiCert CA 管理入口網站。 <br> 2.移至 [Manage Certificate Profiles]  \(管理憑證設定檔\)。 <br> 3.選取用於 Intune 的憑證設定檔。 <br> 4.選取 [Customize options]  \(自訂選項\) 連結。 <br> 5.選取 [Advanced options]  \(進階選項\) 按鈕。 <br> 6.在 [Certificate fields – Subject DN]  \(憑證欄位 - 主體 DN\) 底下，新增 [Common Name (CN)]  \(一般名稱 (CN)\) 欄位，並刪除現有的 [Common Name (CN)]  \(一般名稱 (CN)\) 欄位。 新增和刪除作業必須同時執行。 <br> 7.選取 [儲存]  。 <br><br> 透過先前的變更，DigiCert 憑證設定檔將會要求 **“CN=<upn>”** ，而非 **mail_firstname** 和 **mail_lastname**。 |
| 使用者手動從裝置刪除已部署的憑證。 | Intune 會在下一次簽入或強制執行原則時，重新部署相同的憑證。 在此情況下，NDES 連接器不會接收到 PKCS 憑證要求。 |

## <a name="next-steps"></a>後續步驟

使用本文中的資訊以及[什麼是 Microsoft Intune 裝置設定檔？](../configuration/device-profiles.md)中的資訊，來管理您組織的裝置及裝置上的憑證。

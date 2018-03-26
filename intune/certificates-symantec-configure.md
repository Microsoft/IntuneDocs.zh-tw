---
title: 透過 Microsoft Intune 核發 Symantec PKCS 憑證
titlesuffix: ''
description: 安裝並設定 Intune 憑證連接器，以從 Symantec PKI Manager Web 服務向受 Intune 管理的裝置核發 PKCS 憑證。
keywords: ''
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 02/22/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 1fbb0ccd21ff15cf86656d7badf08002f1e42bb3
ms.sourcegitcommit: e30fb2375fb79f67e5c1e4ed7b2c21fb9ca80c59
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2018
---
# <a name="set-up-intune-certificate-connector-for-symantec-pki-manager-web-service"></a>針對 Symantec PKI Manager Web 服務設定 Intune 憑證連接器

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

本文會示範如何安裝並設定 Intune 憑證連接器，以從 Symantec PKI Manager Web 服務向受 Intune 管理的裝置核發 PKCS 憑證。

本文會將 Symantec PKI Manager Web 服務稱為 Symantec CA。 如果您已設定 Intune 憑證連接器以從 Microsoft 憑證授權單位 (CA) 核發 PKCS 憑證和 SCEP 憑證，您可以設定相同的連接器以從 Symantec CA 核發 PKCS 憑證。 在此情況下，Intune 憑證連接器可以核發下列憑證：

* 來自 Microsoft CA 的 PKCS 憑證
* 來自 Microsoft CA 的 SCEP 憑證
* 來自 Symantec CA 的 PKCS 憑證

如果您想要針對 Microsoft CA 和 Symantec CA 使用 Intune 憑證連接器，您必須先針對 Microsoft CA 完成 Intune 憑證連接器的設定，然後再依照下列指示完成針對 Symantec CA 的設定。  如需針對 Microsoft CA 設定 Intune 憑證連接器的詳細資料，請參閱[如何在 Microsoft Intune 中設定憑證](certificates-configure.md)。

## <a name="prepare-to-install-intune-certificate-connector"></a>準備安裝 Intune 憑證連接器

如果您已經針對現有的 Microsoft CA 使用 Intune 憑證連接器，並想要新增 Symantec CA 支援，請略過此步驟，並在從 Intune 系統管理入口網站安裝最新的 Intune 憑證連接器之後，繼續完成剩餘的步驟。 只有您想要針對獨立的 Symantec CA 使用 Intune 憑證連接器時，才需要執行此步驟。

1. 從下列清單中選擇其中一個 Windows 作業系統版本，並將它安裝於電腦上：
   * Windows Server 2012 R2 Datacenter
   * Windows Server 2012 R2 Standard
   * Windows Server 2016 Datacenter
   * Windows Server 2016 Standard

2. 建立具有系統管理權限的使用者，並使用它來完成下列步驟。

3. 檢查是否有最新的 Windows 更新，並在可用的情況下安裝它們。

   > [!IMPORTANT]
   > 安裝 Windows 更新之後，請重新啟動電腦。

4. 安裝 .NET Framework 3.5：

    a. 開啟 [控制台] > [程式和功能] > [開啟或關閉 Windows 功能]

    b. 選取 [.NET Framework 3.5]，然後安裝它。

## <a name="install-the-symantec-registration-authorization-certificate"></a>安裝 Symantec 註冊驗證憑證

使用下列步驟以從 Symantec CA 取得註冊驗證 (RA) 憑證。 您必須於 Symantec CA 具有作用中的訂閱，才能取得 RA 憑證。

1. 將下列程式碼片段儲存為名為 **certreq.ini** 的檔案，並視需要做出更新 (例如：*Subject name in CN format*)。

   ```
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
   ```

2. 開啟提升權限的命令提示字元，並使用下列命令產生 CSR 內容：

   `Certreq.exe -new certreq.ini request.csr`

3. 在記事本中開啟 request.csr 檔案，並複製格式如下的 CSR 內容。

    ```
    -----BEGIN NEW CERTIFICATE REQUEST-----
    MIID8TCCAtkCAQAwbTEMMAoGA1UEBhMDVVNBMQswCQYDVQQIDAJXQTEQMA4GA1UE
    …
    …
    fzpeAWo=
    -----END NEW CERTIFICATE REQUEST-----
    ```

4. 登入 Symantec CA 並從 [Tasks] \(工作\) 瀏覽至 [Get an RA Cert] \(取得 RA 憑證\)。

   a. 在指定的文字方塊中提供來自步驟 3 的 CSR 內容。

   b. 在指定的文字方塊中提供憑證易記名稱。

   c. 按一下 [繼續] 。

      這會向您顯示 RA 憑證的可下載連結。

   d. 將 RA 憑證下載至本機電腦。

5. 將 RA 憑證匯入 Windows 憑證存放區：

    a. 開啟 MMC 主控台。

    b. 按一下 [檔案] > [新增或移除嵌入式管理單元] > [憑證] > 然後按一下 [新增]。

    c. 選取 [電腦帳戶] > 然後按一下 [下一步]。

    d. 選取 [本機電腦] > 然後按一下 [完成]。

    e. 按一下 [新增或移除嵌入式管理單元] 視窗上的 [確定]。展開 [憑證 (本機電腦)] > [個人] > [憑證]。

    f. 以滑鼠右鍵按一下 [憑證] 節點，然後選取 [所有工作] > [匯入]。

    g. 選取您從 Symantec CA 所下載之 RA 憑證的位置，然後按一下 [下一步]。

    h. 選取 [個人憑證存放區]，然後按一下 [下一步]。

    i. 按一下 [完成] 。 這會將 RA 憑證連同其私密金鑰一起匯入至 [本機電腦\個人] 存放區。  

6. 匯出及匯入私密金鑰憑證：

    a. 展開 [憑證 (本機電腦)] > [個人] > [憑證]。

    b. 選取於上個步驟中匯入的憑證。

    c. 以滑鼠右鍵按一下憑證，然後選擇 [所有工作] > [匯出]。

    d. 按一下 [下一步]，並輸入密碼。

    e. 選取要進行匯出的位置，然後按一下 [完成]。

    f. 遵循和步驟 5 相同的程序，將私密金鑰憑證匯入至 [本機電腦\個人] 存放區。

7. 在不包含任何空格之下，複製 RA 憑證指紋。  以下為範例指紋：

   ```
   RA Cert Thumbprint: “EA7A4E0CD1A4F81CF0740527C31A57F6020C17C5”
   ```


   > [!NOTE]
   > 如果在從 Symantec CA 取得 RA 憑證時發生任何問題，請連絡 Symantec 客戶支援。

## <a name="install-intune-certificate-connector"></a>安裝 Intune 憑證連接器

如果您已針對現有的 Microsoft CA 使用最新的 Intune 憑證連接器，並想要新增 Symantec CA 支援，請略過此步驟。 否則，請從 Intune 系統管理入口網站下載最新的 Intune 憑證連接器，並遵循下列指示。

1. 登入 [Azure 入口網站](https://portal.azure.com)。
2. 選擇 [All services] (所有服務) > [Intune]。 Intune 位於 [Monitoring + Management] (監視 + 管理) 區段。
3. 在 [Intune] 窗格中，選取 [裝置設定]。
4. 在 [裝置設定] 窗格中，選取 [憑證授權單位]。
5. 按一下 [新增] 並選取 [下載連接器檔案]。 將下載項目儲存到可從安裝它之伺服器存取的位置。 
3. 以較高的權限執行 NDESConnectorSetup.exe。

    a. 在 [安裝選項] 畫面上，選取 [PFX 發佈]，如下列螢幕擷取畫面所示。  以預設選項完成剩餘的設定。

   > [!IMPORTANT]
   > 如果您想要設定 Intune 憑證連接器以核發來自 Microsoft CA 和 Symantec CA 的憑證，請選取 [SCEP 與 PFX 設定檔發佈]。 以預設選項完成剩餘的設定。

   ![安裝連接器][InstallConnector]
 
## <a name="configure-intune-certificate-connector"></a>設定 Intune 憑證連接器

Intune 憑證連接器預設是安裝在 `%ProgramFiles%\Microsoft Intune`。

1. 在記事本中開啟 %ProgramFiles%\Microsoft Intune\NDESConnectorSvc\NDESConnector.exe.config 檔案。

    a. 以您在上一節中所複製的憑證指紋值，更新 RACertThumbprint 金鑰值。  以下是一個範例：

   ```
   <add key="RACertThumbprint"
   value="EA7A4E0CD1A4F81CF0740527C31A57F6020C17C5"/>
   ```

    b. 儲存並關閉檔案。

2. 開啟 services.msc。

    a. 選取 [Intune 連接器服務]。

    b. 停止服務，然後啟動服務。

    c. 關閉 [服務] 視窗。

## <a name="setup-the-intune-administrator-account"></a>設定 Intune 系統管理員帳戶

如果您已針對現有的 Microsoft CA 使用 Intune 憑證連接器，並想要新增 Symantec CA 支援，請略過此步驟並繼續完成剩餘的步驟。 

1. 從 ` %ProgramFiles%\Microsoft Intune\NDESConnectorUI\NDESConnectorUI.exe ` 啟動 NDES 連接器使用者介面

    a. 按一下 [註冊] 索引標籤，然後按一下 [登入]。

    b. 在指定的文字方塊中提供您的 Intune 租用戶系統管理員認證。

    c. 按一下 [登入]。  這將會顯示具有 [已成功註冊] 訊息的確認對話方塊，如下列螢幕擷取畫面所示。
2. 關閉 NDES 連接器使用者介面。

![設定連接器][ConfigureConnector]
 
## <a name="create-a-trusted-certificate-profile"></a>建立受信任的憑證設定檔

針對受 Intune 管理的裝置所部署的 PKCS 憑證，必須與受信任的根憑證進行鏈結。 這需要您搭配從 Symantec CA 取得的根憑證，建立 Intune 受信任憑證設定檔。

1. 從 Symantec CA 取得受信任的根憑證：

    a. 登入 Symantec CA 系統管理入口網站。

    b. 從 [Tasks] \(工作\) 按一下 [Manage CAs] \(管理 CA\)：

    c. 從 CA 清單選取適當的 CA。

    d. 按一下 [Download root certificate] \(下載根憑證\) 以下載受信任的根憑證。

2. 在 Intune 系統管理入口網站中建立受信任的憑證設定檔：

    a. 使用 Intune 租用戶系統管理員認證登入 [Azure 入口網站](https://portal.azure.com)，並搜尋 Intune 資源。

    b. 從 [Microsoft Intune] > [裝置設定] > [設定檔] > [建立設定檔] 建立受信任的憑證設定檔。

    c. 在 [名稱] 和 [描述] 欄位中提供必要的資訊，然後選取目標平台。 

    d. 從 [設定檔類型] 下拉式清單中，選取 [受信任的憑證設定檔]。

    e. 上傳您於上個步驟中從 Symantec CA 取得的「受信任的根憑證」。

    f. 完成剩餘的設定檔建立步驟。 

    g. 按一下 [指派] 並選取適當的群組。  指派的群組中至少要有一個使用者或裝置。

## <a name="get-the-certificate-profile-oid"></a>取得憑證設定檔 OID

憑證設定檔 OID 會與 Symantec CA 中的憑證設定檔範本相關聯。  若要在 Intune 系統管理入口網站中建立 PKCS 憑證設定檔，必須以和 Symantec CA 中的憑證範本相關聯之憑證設定檔 OID 的形式，提供憑證範本的名稱。

1. 登入 Symantec CA 系統管理入口網站。
2. 按一下 [Manage Certificate Profiles] \(管理憑證設定檔\)。
3. 選取您要使用的憑證設定檔。
4. 複製憑證設定檔 OID。 它看起來會與下列範例類似：

   ```
   Certificate Profile OID = 2.16.840.1.113733.1.16.1.2.3.1.1.47196109 
   ```

   > [!NOTE]
   > 如果在取得憑證設定檔 OID 時發生任何問題，請連絡 Symantec 客戶支援。

## <a name="create-a-pkcs-certificate-profile"></a>建立 PKCS 憑證設定檔

1. 使用您的 Intune 租用戶系統管理員認證登入 [Azure 入口網站](https://portal.azure.com)，並搜尋 Intune 資源。
2. 從 [Microsoft Intune] > [裝置設定] > [設定檔] > [建立設定檔] 建立 PKCS 憑證設定檔。

    a. 在 [名稱] 和 [描述] 欄位中提供必要的資訊，然後選取目標平台。

    b. 從 [設定檔類型] 下拉式清單中，選取 [PKCS 憑證設定檔]。  

    c. 完成剩餘的步驟以建立設定檔。

   ![設定設定檔][ConfigureProfile]

   > [!IMPORTANT]
   > 下列的 PKCS 憑證設定檔參數必須搭配下表中的指定值進行設定 (如上方螢幕擷取畫面所示)，以透過 Intune 憑證連接器從 Symantec CA 核發 PKCS 憑證。 

    |PKCS 憑證參數 | 值 | 說明 |
    | --- | --- | --- |
    | 憑證授權單位 | pki-ws.symauth.com | 此值必須為不具結尾斜線的 Symantec CA 基礎服務 FQDN。  如果您不確定這是否為適用於您 Symantec CA 訂閱的正確基礎服務 FQDN，請連絡 Symantec 客戶服務。 <br><br> 如果 FQDN 不正確，Intune 憑證連接器將不會從 Symantec CA 核發 PKCS 憑證。| 
    | 憑證授權單位名稱 | Symantec | 此值必須為 **Symantec**字串。 <br><br> 如果對此值做出任何變更，Intune 憑證連接器將不會從 Symantec CA 核發 PKCS 憑證。|
    | 憑證範本名稱 | 來自 Symantec CA 的憑證設定檔 OID。 <br><br> 範例：`2.16.840.1.113733.1.16.1.2.3.1.1.61904612`| 此值必須為在上一節中從 Symantec CA 憑證設定檔範本取得的憑證設定檔 OID。 <br><br> 如果 Intune 憑證連接器無法在 Symantec CA 中找到與此憑證設定檔 OID 相關聯的憑證範本，它將不會從 Symantec CA 核發 PKCS 憑證。|

   > [!NOTE]
   > 適用於 Windows 平台的 PKCS 憑證設定檔並不需要與受信任的憑證設定檔相關聯。 但這對於非 Windows 平台的設定檔 (例如 Android) 則是必要的。

3. 按一下 [指派] 並選取適當的群組。  指派的群組中至少要有一個使用者或裝置。
 
在完成先前的步驟之後，Intune 憑證連接器將會從 Symantec CA 將 PKCS 憑證核發給指派群組中之受 Intune 管理的裝置。 這些憑證將會在受 Intune 管理的裝置上，於目前使用者之憑證存放區的個人存放區中提供使用。

### <a name="pkcs-certificate-profile-supported-attributes"></a>PKCS 憑證設定檔支援的屬性

|屬性 | Intune 支援的格式 | Symantec 雲端 CA 支援的格式 | 結果 |
| --- | --- | --- | --- |
| 主體名稱 |Intune 僅支援下列三種格式的主體名稱： <br><br> 1.一般名稱 <br> 2.包括電子郵件的一般名稱 <br> 3.作為電子郵件的一般名稱 <br><br> 以下是一個範例： <br><br> `CN = IWUser0 <br><br> E = IWUser0@samplendes.onmicrosoft.com` | Symantec CA 有支援其他屬性。  如果您想要選取其他屬性，便必須在 Symantec 憑證設定檔範本中以固定值定義它們。| 我們使用來自 PKCS 憑證要求的一般名稱或電子郵件。 <br><br> Intune 憑證設定檔和 Symantec 憑證設定檔範本之間若有任何屬性選取項目上的差異，將會導致 Symantec CA 不會核發任何憑證。|
| SAN | Intune 僅支援下列 SAN 欄位值： <br><br> AltNameTypeEmail <br><br> AltNameTypeUpn <br><br> AltNameTypeOtherName (編碼值) | Symantec 雲端 CA 也支援這些參數。 如果您想要選取其他屬性，便必須在 Symantec 憑證設定檔範本中以固定值定義它們。 <br><br> AltNameTypeEmail：如果無法在 SAN 中找到此類型，便會使用來自 AltNameTypeUpn 的值。  如果也無法在 SAN 中找到 AltNameTypeUpn，便會 (在主體名稱為電子郵件格式的情況下) 使用來自主體名稱的值。  如果仍然無法找到它，Intune 憑證連接器便無法核發憑證。 <br><br> 範例：`RFC822 Name=IWUser0@ndesvenkatb.onmicrosoft.com`  <br><br> AltNameTypeUpn：如果無法在 SAN 中找到此類型，便會使用來自 AltNameTypeEmail 的值。 如果也無法在 SAN 中找到 AltNameTypeEmail，便會 (在主體名稱為電子郵件格式的情況下) 使用來自主體名稱的值。  如果仍然無法找到它，Intune 憑證連接器便無法核發憑證。  <br><br> 範例：`Other Name: Principal Name=IWUser0@ndesvenkatb.onmicrosoft.com` <br><br> AltNameTypeOtherName：如果無法在 SAN 中找到此類型，Intune 憑證連接器便無法核發憑證。 <br><br> 範例：`Other Name: DS Object Guid=04 12 b8 ba 65 41 f2 d4 07 41 a9 f7 47 08 f3 e4 28 5c ef 2c` <br><br>  **重要事項：**此欄位的值必須為編碼格式 (十六進位值) 才能受 Symantec CA 支援。 因此，Intune 憑證連接器會先將此欄位中所有的值都轉換成 Base 64 編碼，然後再提交憑證要求。 **Intune 憑證連接器並不會先驗證此值是否已進行編碼。** | 無 |

## <a name="troubleshooting"></a>疑難排解

Intune 憑證連接器服務記錄可於 NDES 連接器電腦上的 `%ProgramFiles%\Microsoft Intune\NDESConnectorSvc\Logs\Logs` 取得。 在 [SvcTraceViewer](https://docs.microsoft.com/dotnet/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe) \(英文\) 中開啟記錄，並搜尋例外狀況或錯誤訊息。

| 問題/錯誤訊息 | 解決步驟 |
| --- | --- |
| 無法在 NDES 連接器 UI 上使用 Intune 租用戶系統管理員帳戶登入 | 當內部部署憑證連接器沒有在 Intune 系統管理入口網站中啟用時，便可能發生此情況。 若要解決此問題，請使用下列步驟： <br><br> 從 Silver Light UI： <br> 1.登入 [Intune 系統管理入口網站](https://admin.manage.microsoft.com) <br> 2.按一下 [管理員] <br> 3.選取 [行動裝置管理] > [憑證連接器] <br> 4.按一下 [設定內部部署憑證連接器] <br> 5.選取 [啟用憑證連接器] 核取方塊 <br> 6.按一下 [確定]。 <br><br>或是 <br><br> 從 Azure 入口網站 UI： <br> 1.登入 [Azure 入口網站](https://portal.azure.com) <br> 2.移至 [Microsoft Intune] <br> 3.選取 [裝置設定] > [憑證授權單位] <br> 4.按一下 [啟用]。 <br><br> 從 Silver Light UI 或 Azure 入口網站完成上述步驟之後，請嘗試在 NDES 連接器 UI 中使用相同的 Intune 租用戶系統管理員帳戶登入。 |
| 找不到 NDES 連接器憑證。 <br><br> System.ArgumentNullException: 值不可以是 Null。 | 如果 Intune 租用戶系統管理員帳戶從未登入 NDES 連接器 UI，Intune 憑證連接器便會顯示此錯誤。 <br><br> 如果此錯誤持續發生，請重新啟動 Intune 服務連接器。 <br><br> 1.開啟 services.msc <br> 2.選取 [Intune 連接器服務]。 <br> 3.以滑鼠右鍵按一下並選取 [重新啟動]。|
| NDES 連接器 - IssuePfx - 一般例外狀況： <br> System.NullReferenceException: 物件參考未設定至物件的執行個體。 | 這是暫時性的錯誤。 請重新啟動 Intune 服務連接器。 <br><br> 1.開啟 services.msc <br> 2.選取 [Intune 連接器服務] <br> 3.以滑鼠右鍵按一下並選取 [重新啟動]。 |
| Symantec 提供者 - 無法取得 Symantec 原則「作業逾時」 | Intune 憑證連接器在與 Symantec CA 通訊期間接收到作業逾時錯誤。 如果此錯誤持續發生，請提升連線逾時值並再試一次。 <br><br> 嘗試提升連線逾時： <br> 1.移至 NDES 連接器電腦。 <br>2.在 [記事本] 中開啟 `%ProgramFiles%\Microsoft Intune\NDESConnectorSvc\NDESConnector.exe.config` 檔案。 <br> 3.提升下列參數的逾時值： <br><br> `CloudCAConnTimeoutInMilliseconds` <br><br> 4.重新啟動 Intune 連接器服務。 <br><br> 如果此問題持續發生，請連絡 Symantec 客戶服務。 |
| Symantec 提供者 - 無法取得用戶端憑證 | Intune 憑證連接器無法從 [本機電腦\個人] 憑證存放區擷取資源驗證憑證。 若要解決此問題，請務必將資源驗證憑證連同其私密金鑰一起安裝於 [本機電腦\個人] 憑證存放區中。 <br><br> **注意：**資源驗證憑證必須從 Symantec CA 取得。 如需詳細資料，請連絡 Symantec 客戶服務。 | 
| Symantec 提供者 - 無法取得 Symantec 原則「要求已經中止: 無法建立 SSL/TLS 的安全通道」。 | 此錯誤會在下列案例發生： <br><br> 1.Intune 憑證連接器服務沒有從 [本機電腦\個人] 憑證存放區讀取資源驗證憑證及其私密金鑰的足夠權限。 若要解決此問題，請檢查 services.msc 中執行內容帳戶的「連接器」服務。 「連接器」服務必須於 NT AUTHORITY\SYSTEM 內容下執行。 <br><br> 2.Intune 系統管理入口網站中的 PKCS 憑證設定檔可能具有無效的 Symantec CA 基礎服務 FQDN 設定。 FQDN 應該會類似於 `pki-ws.symauth.com`。 若要解決此問題，請連絡 Symantec 客戶服務以確認該 URL 是否適用於您的訂閱。 <br><br> 3.Intune 憑證連接器無法使用資源驗證憑證與 Symantec CA 進行驗證，因為該憑證無法擷取其私密金鑰。 若要解決此問題，請務必將資源驗證憑證連同其私密金鑰一起安裝於 [本機電腦\個人] 憑證存放區中。 <br><br> 如果此問題持續發生，請連絡 Symantec 客戶服務。 |
| Symantec 提供者 - 無法取得 Symantec 原則「無法解讀要求項目」。 | Intune 憑證連接器無法取得 Symantec 憑證設定檔範本，因為用戶端設定檔 OID 與 Intune 憑證設定檔不符。 在另一個情況下，Intune 憑證連接器無法在 Symantec CA 中找到與指定用戶端設定檔 OID 相關聯的憑證設定檔範本。 <br><br> 若要解決此問題，請務必從 Symantec CA 中的 Symantec 憑證範本取得正確的用戶端設定檔 OID。 然後在 Intune 管理入口網站中更新 PKCS 憑證設定檔。 <br><br> 從 Symantec CA 取得用戶端設定檔 OID： <br> 1.登入 Symantec CA 系統管理入口網站。 <br> 2.按一下 [Manage Certificate Profiles] \(管理憑證設定檔\) <br> 3.選取您要使用的憑證設定檔。 <br> 4.取得憑證設定檔 OID。 它看起來會與下列範例類似： <br> `Certificate Profile OID = 2.16.840.1.113733.1.16.1.2.3.1.1.47196109` <br><br> 為 PKCS 憑證設定檔更新正確的憑證設定檔 OID： <br>1.登入 Intune 系統管理入口網站 <br> 2.移至 [PKCS 憑證設定檔]，並按一下 [編輯]。 <br> 3.在 [憑證範本名稱] 欄位中，更新憑證設定檔 OID。 <br> 4.儲存 PKCS 憑證設定檔。 |
| Symantec 提供者 - 原則驗證失敗。 <br><br> 屬性沒有位於 Symantec 支援的憑證範本屬性清單上 | 當 Symantec 憑證設定檔範本和 Intune 憑證設定檔之間出現差異時，Symantec CA 便會顯示此訊息。 此問題很可能是因為 SubjectName 或 SubjectAltName 屬性不符而造成。 <br><br> 若要解決此問題，請務必在 Symantec 憑證設定檔範本中，針對 SubjectName 和 SubjectAltName 選取 Intune 支援的屬性。 如需詳細資訊，請參閱＜憑證參數＞一節中的 Intune 支援的屬性。 |
| 某些使用者裝置沒有接收到來自 Symantec CA 的 PKCS 憑證。 | 此問題會在使用者 UPN 包含如底線等特殊字元時發生 (範例：`global_admin@intune.onmicrosoft.com`)。 <br><br> Symantec CA 在 mail_firstname 和 mail_lastname 中並不支援特殊字元。 <br><br> 下列步驟可協助解決此問題： <br><br> 1. 登入 Symantec CA 系統管理入口網站。 <br> 2.移至 [Manage Certificate Profiles] \(管理憑證設定檔\)。 <br> 3. 按一下用於 Intune 的憑證設定檔。 <br> 4.按一下 [Customize] \(自訂\) 選項連結。 <br> 5. 按一下 [Advanced] \(進階\) 按鈕。 <br> 6.在 [Certificate fields – Subject DN] \(憑證欄位 - 主體 DN\) 底下，新增 [Common Name (CN)] \(一般名稱 (CN)\) 欄位，並刪除現有的 [Common Name (CN)] \(一般名稱 (CN)\) 欄位。 新增和刪除動作必須同時執行。 <br> 7.  按一下 [儲存]。 <br><br> 透過先前的變更，Symantec 憑證設定檔將會要求 “CN=<upn>”，而非 mail_firstname 和 mail_lastname。 |
| 使用者手動從裝置刪除已部署的憑證。 | Intune 會在下一次簽入或強制執行原則時，重新部署相同的憑證。 在此情況下，NDES 連接器並不會接收到 PKCS 憑證要求。 |

## <a name="next-steps"></a>接下來的步驟

- 使用在本文及[什麼是 Microsoft Intune 裝置設定檔？](device-profiles.md)中所提供的資訊，來管理您組織的裝置及裝置上的憑證。

[InstallConnector]:  ./media/certificates-symantec-connector-install.png "安裝 Intune 憑證連接器並選取 [PFX 發佈]"
[ConfigureConnector]: ./media/certificates-symantec-configure-connector-configure.png "設定 Intune 憑證連接器"
[ConfigureProfile]: ./media/certificates-symantec-pkcs-example.png "在 Azure 入口網站中建立 PKCS 憑證設定檔"

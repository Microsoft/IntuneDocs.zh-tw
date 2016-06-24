---
# required metadata

title: 準備 Android 應用程式以使用 App Wrapping Tool 進行管理 | Microsoft Intune
description:
keywords:
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: e9c349c8-51ae-4d73-b74a-6173728a520b

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# 準備 Android 應用程式以使用 Intune 應用程式包裝工具進行行動應用程式管理
使用 [適用於 Android 的 Microsoft Intune 應用程式包裝工具] 來修改內部 Android 應用程式的行為，讓您能夠設定應用程式的功能，而不需修改應用程式本身的程式碼。

此工具是一個 Windows 命令列應用程式，可在 PowerShell 中執行並在您的應用程式周圍建立「包裝程式」。 一旦處理應用程式之後，您便可以使用您設定的[行動應用程式管理原則](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md)來變更應用程式功能。

如果您的應用程式正在使用 Azure Active Directory Authentication Library，您必須在包裝應用程式之前，先完成[使用 Azure Active Directory Library (ADAL) 包裝應用程式](#how-to-wrap-apps-that-use-the-azure-active-directory-library) 中的步驟。 如果您不確定您的應用程式是否使用此程式庫，請連絡應用程式的開發人員。

執行此工具之前，請檢閱[執行應用程式包裝工具的安全性考量](#security-considerations-for-running-the-app-wrapping-tool)。 若要下載此工具，請參閱 [Microsoft Intune App Wrapping Tool for Android](https://www.microsoft.com/download/details.aspx?id=47267)

## 步驟 1：滿足使用 App Wrapping Tool 的必要條件

-   您必須在執行 Windows 7 或更新版本的 Windows 電腦上執行應用程式包裝工具。

-   您的輸入應用程式必須是副檔名為 .apk 檔案的有效 Android 應用程式套件，而且：

    -   無法加密

    -   必須尚未使用應用程式包裝工具進行包裝

    -   必須是針對 Android 4.0 或更新版本編寫的

-   該應用程式必須是由貴公司所開發，或針對貴公司所開發。 您無法使用此工具，來處理從 Google Play 商店下載的應用程式。

-   若要執行應用程式包裝工具，您必須安裝最新版的 [Java Runtime Environment](http://java.com/download/)，然後確定已在您的 Windows 環境變數中將 Java 路徑變數設為 C:\ProgramData\Oracle\Java\javapath。 如需詳細說明，請參閱您的 [Java 文件](http://java.com/download/help/)

    > [!NOTE]
    > 在某些情況下，Java 32 位元版本可能會導致記憶體問題。 我們建議您改為安裝 64 位元版本。

## 步驟 2：安裝 App Wrapping Tool

1.  從 Microsoft 下載中心，將應用程式包裝工具下載到 Windows 電腦，並開啟其安裝檔案。

2.  接受授權合約，然後完成安裝。

記下您安裝此工具的資料夾。 預設位置為：C:\Program Files (x86)\Microsoft Intune Mobile Application Management\Android\App Wrapping Tool

## 步驟 3：執行 App Wrapping Tool

1.  在您安裝應用程式包裝工具的 Windows 電腦上，開啟 PowerShell 視窗。

2.  從安裝此工具的資料夾，匯入應用程式包裝工具 PowerShell 模組：

    ```
    Import-Module .\IntuneAppWrappingTool.psm1
    ```

3.  使用 invoke-AppWrappingTool 命令搭配下列參數來執行工具。 標示為「選用」的參數適用於使用 Azure Active Directory Library (ADAL) 的應用程式。 如需詳細資訊，請參閱[使用 Azure Active Directory Library 包裝應用程式](#how-to-wrap-apps-that-use-the-azure-active-directory-library)。

|參數|詳細資訊|範例|
|-------------|--------------------|---------|
|-InputPath&lt;String&gt;|來源 Android 應用程式 (.apk) 的路徑。| |
|-OutputPath&lt;String&gt;|輸出的 Android 應用程式路徑。 如果此路徑與 InputPath 的目錄路徑相同，封裝會失敗。| |
|-KeyStorePath&lt;String&gt;|包含要簽署之公開/私密金鑰組的 keystore 檔案路徑。| |
|-KeyStorePassword&lt;SecureString&gt;|用來解密 keystore 的密碼。| |
|-KeyAlias&lt;String&gt;|要用於簽署的金鑰名稱。| |
|-KeyPassword&lt;SecureString&gt;|用來解密簽署用途之私密金鑰的密碼。| |
|-SigAlg&lt;SecureString&gt;|要用於簽署的簽章演算法名稱。 此演算法必須與私密金鑰相容。|範例：SHA256withRSA、SHA1withRSA、MD5withRSA|
|-ClientID&lt;GUID&gt;|輸入應用程式的 Azure Active Directory 用戶端識別碼 (選用)。| |
|-AuthorityURI&lt;Uri&gt;|輸入應用程式的 Azure Active 授權 URI (選用)。| |
|-SkipBroker&lt;Boolean&gt;|指出輸入應用程式是否支援全裝置代理單一登入 (選用)。 |True - 輸入應用程式不支援全裝置代理單一登入。 使用 NonBrokerRedirectURI 參數。 False - 輸入應用程式支援全裝置代理單一登入。|
|-NonBrokerRedirectURI&lt;URI&gt;|如果 SkipBroker 為 true，則使用 Azure Active Directory 重新導向 URI (選用)。|  |


CommonParameters

- (選擇性 - 支援常用的 PowerShell 參數，例如 verbose、debug 等參數)

- 如需常用參數清單，請參閱 [Microsoft 指令碼中心](https://technet.microsoft.com/library/hh847884.aspx)

    ```
    Help Invoke-AppWrappingTool
    ```
- 若要查看工具的說明，請輸入下列命令：

**若要了解 Azure Active Directory (AAD) 整合的詳細資訊，請參閱[如何包裝使用 Azure Active Directory 程式庫的應用程式](#how-to-wrap-apps-that-use-the-azure-active-directory-library)**


    Import-Module "C:\Program Files (x86)\Microsoft Intune Mobile Application Management\Android\App Wrapping Tool\IntuneAppWrappingTool.psm1"
    Invoke-AppWrappingTool –InputPath <input-app.apk> -OutputPath <output-app.apk> -KeyStorePath <path-to-signing.keystore> -KeyAlias <signing-key-name> -ClientID <xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx> -AuthorityURI <http://AzureActiveDirectory.Authority.URL> -SkipBroker<$True|$False> -NonBrokerRedirectURI <urn:xxx:xx:xxxx:xx:xxx>

範例：

系統接著會提示您提供 KeyStorePassword 和 KeyPassword

## 隨即會產生已包裝的應用程式，並和記錄檔案一起儲存於您指定的輸出路徑中。
執行應用程式包裝工具的安全性考量

-   若要防止潛在的詐騙、資訊洩漏和權限提升攻擊：

-   請確定輸入的商務營運應用程式、輸出應用程式及 Java KeyStore 都位於執行應用程式包裝工具的同一部電腦上。

-   在匯入執行工具的同一部電腦上，將輸出應用程式匯入 Intune 主控台。

-   如果輸出應用程式和工具位於通用命名慣例 (UNC) 路徑上，而您未在同一部電腦上執行工具和輸入檔案，請使用 [網際網路通訊協定安全性 (IPsec)](http://en.wikipedia.org/wiki/IPsec) 或 [伺服器訊息區塊 (SMB) 簽署](https://support.microsoft.com/en-us/kb/887429)，將環境設定為安全的

-   確保應用程式來自受信任的來源，特別是當您使用 Azure Active Directory (AAD) 時，這可能會讓應用程式在執行階段存取 AAD Token。 保護包含已包裝應用程式的輸出目錄。

## 考慮針對輸出使用使用者層級目錄。
使用 Azure Active Directory Library 包裝應用程式

### 如果您的應用程式正在使用 Azure Active Directory Authentication Library (ADAL)，您必須在包裝應用程式之前，先完成這些步驟。
步驟 1：確定您符合 ADAL 的需求

-   針對使用 ADAL 的應用程式，下列條件必須為真：

-   應用程式必須納入大於或等於 1.0.2 的 ADAL 版本。

### 開發人員必須將其應用程式存取權授與 Intune 行動應用程式管理資源，如[步驟 3：設定 AAD 中的行動應用程式管理存取權](#step-3-configure-access-to-mobile-app-management-in-aad)中所述
步驟 2：檢閱您在註冊應用程式時必須取得的識別碼 在下一個步驟中，您將使用 Azure 管理入口網站來註冊您的應用程式 (搭配使用 ADAL 與 Azure Active Directory (AAD))，以取得下表中所列的唯一識別碼。

|當您將 ADAL 與應用程式整合時，再將識別碼提供給開發人員。|識別碼|詳細資訊|
|--------------|--------------------|-----------------|
|**預設值**|用戶端識別碼<br /><br />使用 AAD 註冊應用程式之後，針對該應用程式所產生的唯一 GUID 識別碼。 如果您知道應用程式的用戶端識別碼，請指定該值。|否則，請使用預設值。|
|**6c7e8096-f593-4d72-807f-a5f86dcc9c77**|授權 URI<br /><br />AAD 物件的授權統一資源識別元 (URI) 值 (例如使用者和群組)。 AuthorityURI 參數是選用的應用程式包裝工具。||
|**如果您不使用此參數，則會使用預設 URI。**|SkipBroker<br /><br />指出公司入口網站是否將用來做為 Broker 的值。<br /><br />True - 公司入口網站不會用於 ADAL 驗證。 False - 公司入口網站將用於 ADAL 驗證。||
|**公司入口網站正因「單一登入」的緣故而使用已註冊的使用者。**|非 Broker 重新導向 URI|ADAL 不使用 Broker 應用程式 (Intune 公司入口網站) 時，則使用登入 URI。|
|**urn:ietf:wg:oauth:2.0:oob**|資源識別碼||

### 應用程式 AAD 資源的指標。
步驟 3：設定 AAD 中的行動應用程式管理存取權

1.  在您可以於應用程式包裝工具中使用應用程式的 AAD 註冊值之前，應用程式開發人員必須先遵循以下步驟，授與該應用程式對於 Intune 行動應用程式管理資源的存取權：

2.  在 Azure 管理入口網站中登入現有的 AAD 帳戶。

3.  選擇 [現有的 LOB 應用程式註冊]

4.  在 [設定] 區段中，選擇 [設定其他應用程式中 Web API 的存取]

從 [其他應用程式的權限] 區段的第一個下拉式清單中，選擇 [Intune 行動應用程式管理] 您現在可以使用應用程式包裝工具中的應用程式用戶端識別碼。

### 您可以在 Azure Active Directory 管理入口網站中找到用戶端識別碼，如[步驟 2：檢閱您在註冊應用程式時必須取得的識別碼](#step-2-review-the-identifiers-you-need-to-get-when-you-register-the-app)中的表格內容所述
步驟 4：使用 App Wrapping Tool 中的 AAD 識別碼值 使用您在註冊程序中取得的識別碼值，在應用程式包裝工具中輸入該值做為命令列的內容。 您必須指定表格中所有的值，使用者才能成功驗證應用程式。

|如果不指定值，則會使用預設值。|識別碼|
|--------------|-------------|
|參數|用戶端識別碼|
|ClientID|授權 URI|
|授權-URI|SkipBroker|
|SkipBroker|非 Broker 重新導向 URI|
|NonBrokerRedirectURI|資源識別碼|
ResourceID

-   包裝應用程式時請謹記下列重點： 應用程式包裝工具不會搜尋應用程式內的 ADAL 二進位檔 (如果有的話)。

-   如果應用程式連結到過期的二進位檔版本，則如果啟用驗證原則，可能會在登入期間發生執行階段錯誤。 為了確認驗證已成功， [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 提取與 MAM 資源識別碼相關聯的 AAD 權杖。 然而，該權杖並非用於任何會依次確認權杖有效性的呼叫中。

-   只能讀取已登入使用者的使用者主體名稱 (UPN)，來決定應用程式存取權限。 AAD 權杖不用於任何進一步的服務呼叫。

-   驗證權杖會在來自相同發行者的應用程式之間共用，因為它們存放在共用的金鑰鏈。 若要找出特定的應用程式，則必須針對該應用程式使用不同的簽章憑證、佈建設定檔 keystore 和索引鍵別名。 如果您提供用戶端應用程式的用戶端識別碼和授權 URI，將會避免雙重的登入提示。


### 您必須註冊此用戶端識別碼才能存取 AAD 儀表板中已發佈的 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] MAM 資源識別碼。
- [如果您沒有註冊用戶端識別碼，使用者會在應用程式執行時發生登入失敗的狀況。](decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune.md)

- [請參閱](use-the-sdk-to-enable-apps-for-mobile-application-management.md)


<!--HONumber=May16_HO2-->



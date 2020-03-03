---
title: 在 Microsoft Intune 中使用私密和公開金鑰憑證 - Azure | Microsoft Docs
description: 使用公開金鑰加密標準 (PKCS) 憑證搭配 Microsoft Intune、使用根憑證和憑證範本、安裝 Intune 憑證連接器 (NDES) 和針對 PKCS 憑證使用裝置組態設定檔。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/25/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 99983b2d2776e72232c65fcfb12d8075061d804b
ms.sourcegitcommit: 29f3ba071c9348686d3ad6f3b8864d8557e05b97
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/26/2020
ms.locfileid: "77609336"
---
# <a name="configure-and-use-pkcs-certificates-with-intune"></a>透過 Intune 設定並使用 PKCS 憑證

Intune 支援使用私密和公開金鑰組 (PKCS) 憑證。 本文可協助您設定必要的基礎結構 (例如，內部部署憑證連接器)，匯出 PKCS 憑證，然後將憑證新增至 Intune 裝置組態設定檔。

Microsoft Intune 中包含的內建設定，可使用 PKCS 憑證對您的組織資源進行存取和驗證。 憑證會驗證並保護您的公司資源存取，例如 VPN 或 WiFi 網路。 您可以使用 Intune 中的裝置組態設定檔，將這些設定部署到裝置。

如需使用匯入的 PKCS 憑證的相關資訊，請參閱[匯入的 PFX 憑證](certificates-imported-pfx-configure.md)。


## <a name="requirements"></a>需求

若要透過 Intune 使用 PKCS 憑證，您需要下列基礎結構：

- **Active Directory 網域**：  
  本節所列的所有伺服器均須加入 Active Directory 網域。

  如需安裝及設定 Active Directory Domain Services (AD DS) 的詳細資訊，請參閱 [AD DS 設計與規劃](https://docs.microsoft.com/windows-server/identity/ad-ds/plan/ad-ds-design-and-planning)。

- **憑證授權單位**：  
   企業憑證授權單位 (CA)。

  如需安裝及設定 Active Directory 憑證服務 (AD CS) 的資訊，請參閱 [Active Directory Certificate Services Step-by-Step Guide](https://technet.microsoft.com/library/cc772393) (Active Directory 憑證服務逐步指南)。

  > [!WARNING]  
  > Intune 需要您搭配企業憑證授權單位 (CA) 執行 AD CS，而非獨立 CA。

- **用戶端**：  
  連線到企業 CA。

- **根憑證**：  
  從您的企業 CA 匯出的根憑證複本。

- **Intune 憑證連接器** (亦稱為「NDES 憑證連接器」  )：  
  在 Intune 入口網站中，移至 [裝置設定]   > [憑證連接器]   > [新增]  ，並遵循「安裝 PKCS #12 連接器的步驟」  。 使用入口網站中的下載連結，開始下載憑證連接器安裝程式 **NDESConnectorSetup.exe**。  

  Intune 支援每個租用戶最多 100 此連接器的個執行個體。 連接器的每個執行個體都必須位於個別的 Windows 伺服器上。 您可以在與 Microsoft Intune 的 PFX 憑證連接器執行個體相同的伺服器上，安裝此連接器的執行個體。 當您使用多個連接器時，連接器基礎結構支援高可用性與負載平衡，因為任何可用的連接器執行個體都可以處理您的 PKCS 憑證要求。 

  此連接器會處理用於驗證或 S/MIME 電子郵件簽署的 PKCS 憑證要求。

  Microsoft Intune 憑證連接器也支援聯邦資訊處理標準 (FIPS) 模式。 FIPS 並非必要，但啟用時可發出及撤銷憑證。

- **適用於 Microsoft Intune 的 PFX 憑證連接器**：  
  如果您打算使用 S/MIME 電子郵件加密，請使用 Intune 入口網站來下載支援匯入 PFX 憑證的 *PFX 憑證連接器*。  移至 [裝置設定]   > [憑證連接器]   > [新增]  ，並遵循「安裝匯入 PFX 憑證連接器的步驟」  。 使用入口網站中的下載連結，開始下載安裝程式 **PfxCertificateConnectorBootstrapper.exe**。

  每個 Intune 租用戶都支援此連接器的單一執行個體。 您可在相同的伺服器上安裝此連接器，作為 Microsoft Intune 憑證連接器的執行個體。

  此連接器會處理對 Intune 中所匯入之 PFX 檔案的要求，為特定使用者進行 S/MIME 電子郵件加密。  

  當新版本可供使用時，此連接器會自動自行更新。 若要使用更新功能，您必須：
  - 在伺服器上安裝適用於 Microsoft Intune 的 PFX 憑證連接器。  
  - 若要自動接收重要更新，請確定防火牆已開啟，可讓連接器在連接埠 **443** 上連絡 **autoupdate.msappproxy.net**。   

  如需詳細資訊，請參閱 [Microsoft intune 的網路端點](../fundamentals/intune-endpoints.md)和 [Intune 網路設定需求與頻寬](../fundamentals/network-bandwidth-use.md)。

- **Windows 伺服器**：  
  使用 Windows Server 來裝載：

  - Microsoft Intune 憑證連接器，用於驗證和 S/MIME 電子郵件簽署情況
  - 適用於 Microsoft Intune 的 PFX 憑證連接器，用於 S/MIME 電子郵件加密情況。

  連接器需要存取相同的連接埠，請參閱[裝置端點內容](https://docs.microsoft.com/intune/fundamentals/intune-endpoints#access-for-managed-devices)中，對於受控裝置的詳細描述。

  Intune 支援在與 *Microsoft Intune 憑證連接器*相同的伺服器上安裝 *PFX 憑證連接器*。
  
## <a name="export-the-root-certificate-from-the-enterprise-ca"></a>從企業 CA 匯出根憑證

若要向 VPN、WiFi 或其他資源驗證裝置，裝置需要有根憑證或中繼 CA 憑證。 下列步驟說明如何從您的企業 CA 取得所需的憑證。

**使用命令列**：  
1. 使用系統管理員帳戶登入根憑證授權單位伺服器。
 
2. 移至 [開始]   > [執行]  ，然後輸入 **Cmd** 來開啟命令提示字元。 
    
3. 指定 **certutil -ca.cert ca_name.cer**，將根憑證匯出為名為 *ca_name.cer* 的檔案。



## <a name="configure-certificate-templates-on-the-ca"></a>設定 CA 上的憑證範本

1. 使用具有系統管理權限的帳戶登入您的企業 CA。
2. 開啟 [憑證授權單位]  主控台、以滑鼠右鍵按一下 [憑證範本]  ，然後選取 [管理]  。
3. 找出 [使用者]  憑證範本、以滑鼠右鍵按一下它，然後選擇 [複製範本]  ，以開啟 [新範本的內容]  。

    > [!NOTE]
    > 在 S/MIME 電子郵件簽署和加密情況下，許多系統管理員使用個別的憑證進行簽署和加密。 如果您要使用 Microsoft Active Directory 憑證服務，則可以將 [僅限 Exchange 簽章]  範本用於 S/MIME 電子郵件簽署憑證，並將 [Exchange 使用者]  範本用於 S/MIME 加密憑證。  如果您要使用協力廠商憑證授權單位，建議您檢閱其設定簽署和加密範本的指引。

4. 在 [相容性]  索引標籤上：

    - 將 [憑證授權單位]  設為 [Windows Server 2008 R2] 
    - 將 [憑證接收者]  設為 [Windows 7 / Server 2008 R2] 

5. 在 [一般]  索引標籤上，將 [範本顯示名稱]  設為對您有意義的名稱。

    > [!WARNING]
    > [範本名稱]  預設會與 [範本顯示名稱]  相同，但*沒有空格*。 請記下範本名稱，您之後會需要它。

6. 在 [要求處理]  索引標籤中，選取 [允許匯出私密金鑰]  。
7. 在 [密碼編譯]  中，確認 [最小金鑰大小]  已設為 2048。
8. 在 [主體名稱]  中，選擇 [在要求中提供]  。
9. 在 [延伸模組]  中，確認您在 [應用程式原則]  下看到「加密檔案系統」、「安全電子郵件」和「用戶端驗證」。

    > [!IMPORTANT]
    > 若為 iOS/iPadOS 憑證範本，請前往 [延伸模組]  索引標籤、更新 [金鑰使用方式]  ，並確認未選取 [簽章為原件證明]  。

10. 在 [安全性]  中，新增您安裝 Microsoft Intune 憑證連接器之伺服器的電腦帳戶。 允許此帳戶的 [讀取]  和 [註冊]  權限。
11. 選取 [套用]   > [確定]  ，儲存憑證範本。 關閉 [憑證範本主控台]  。
12. 在 [憑證授權單位]  主控台中，以滑鼠右鍵按一下 [憑證範本]   > [新增]   > [要發出的憑證範本]  。 選擇您在前述步驟中建立的範本。 選取 [確定]  。
13. 若要讓伺服器為已註冊的裝置及使用者管理憑證，請使用下列步驟：

    1. 以滑鼠右鍵按一下憑證授權單位，選擇 [內容]  。
    2. 在 [安全性] 索引標籤上，新增您執行連接器 (**Microsoft Intune 憑證連接器**或**適用於 Microsoft Intune 的 PFX 憑證連接器**) 之伺服器的電腦帳戶。 
    3. 將 [發行及管理憑證]  和 [要求憑證]  的「允許」權限授與該電腦帳戶。

14. 登出企業 CA。

## <a name="download-install-and-configure-the-microsoft-intune-certificate-connector"></a>下載、安裝和設定 Microsoft Intune 憑證連接器

> [!IMPORTANT]  
> Microsoft Intune 憑證連接器無法安裝在發行憑證授權單位 (CA) 上，而必須安裝在不同的 Windows 伺服器上。  

1. 登入 [Microsoft 端點管理員系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。

2. 選取 [租用戶系統管理]   > [連接器與權杖]   > [憑證連接器]   > [+ 新增]  。

3. 針對 PKCS #12 的連接器按一下 [下載憑證連接器軟體]  ，並將該檔案儲存到要安裝連接器的伺服器所能存取位置。

   ![Microsoft Intune 憑證連接器下載](./media/certficates-pfx-configure/download-ndes-connector.png)
 
4. 下載完成後，請登入伺服器。 然後：

    1. 確定已安裝 .NET 4.5 Framework 或更高版本，這是 NDES 憑證連接器的必要項目。 Windows Server 2012 R2 及更新版本會自動隨附 .NET 4.5 Framework。
    2. 執行安裝程式 (NDESConnectorSetup.exe)，並接受預設位置。 它會將連接器安裝到 `\Program Files\Microsoft Intune\NDESConnectorUI`。 在 [安裝程式選項] 中，選取 [PFX 發佈]  。 繼續並完成安裝。
    3. 連接器服務預設會以本機系統帳戶執行。 如果需要有 Proxy 才能存取網際網路，請確認本機服務帳戶可以存取伺服器上的 Proxy 設定。

5. Microsoft Intune 憑證連接器會開啟 [註冊]  索引標籤。若要連線到 Intune，請**登入**並輸入具有全域系統管理權限的帳戶。
6. 在 [進階]  索引標籤上，建議保持選取 [使用此電腦的 SYSTEM 帳戶 (預設)]  。
7. [套用]   > [關閉] 
8. 返回 Intune 入口網站 ([Intune]   > [裝置設定]   > [憑證連接器]  )。 在幾分鐘後會顯示綠色的核取記號，且 [連線狀態]  為 [使用中]  。 連接器伺服器現在可以與 Intune 通訊。
9. 如果在您的網路環境中有 Web Proxy，您可能需要其他設定才能讓連接器運作。 如需詳細資訊，請參閱 Azure Active Directory 文件中的[使用現有的內部部署 Proxy 伺服器](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy-configure-connectors-with-proxy-servers)。
<ul><li>Android Enterprise (工作設定檔  )</li><li>iOS</li><li>macOS</li><li>Windows 10 及更新版本 > Microsoft Intune 憑證連接器支援 TLS 1.2。 如果裝載連接器的伺服器上安裝了 TLS 1.2，連接器就會使用 TLS 1.2。 否則，會使用 TLS 1.1。 目前，使用 TLS 1.1 在裝置與伺服器之間進行驗證。

## <a name="create-a-trusted-certificate-profile"></a>建立受信任的憑證設定檔

1. 登入 [Microsoft 端點管理員系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。

2. 選取 [裝置]   > [組態設定檔]   > [建立設定檔]  。

   ![巡覽至 Intune 並建立受信任憑證的新設定檔](./media/certficates-pfx-configure/certificates-pfx-configure-profile-new.png)

3. 輸入下列內容：

    - 設定檔的 [名稱] 
    - 可選擇性地設定說明
    - 要部署設定檔的目標 [平台] 
    - 將 [設定檔類型]  設為 [信任的憑證] 

4. 選取 [設定]  ，並指定先前匯出的根 CA 憑證 .cer 檔案。

   > [!NOTE]
   > 視您在**步驟 2** 中選擇的平台而定，您可能會有選擇憑證 [目的地存放區]  的選項。

   ![建立設定檔並上傳受信任的憑證](./media/certficates-pfx-configure/certificates-pfx-configure-profile-fill.png)

5. 選取 [確定]   > [建立]  儲存您的設定檔。

6. 若要將新的設定檔指派給一或多部裝置，請參閱[指派 Microsoft Intune 裝置設定檔](../configuration/device-profile-assign.md)。

## <a name="create-a-pkcs-certificate-profile"></a>建立 PKCS 憑證設定檔

1. 登入 [Microsoft 端點管理員系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。

2. 選取並移至 [裝置]   > [組態設定檔]   > [建立設定檔]  。

3. 輸入下列內容：

    - 設定檔的 [名稱] 
    - 可選擇性地設定說明
    - 要部署設定檔的目標 [平台] 
    - 將 [設定檔類型]  設為 [PKCS 憑證] 

4. 選取 [設定]  ，並設定適用於所選平台的屬性：
   
   |設定     | 平台     | 詳細資料   |
   |------------|------------|------------|
   |**更新閾值 (%)**        |<ul><li>全部         |建議為 20%  | 
   |**憑證有效期間**  |<ul><li>全部         |如果您沒有變更憑證範本，此選項可設定為一年。 |
   |**金鑰儲存提供者 (KSP)**   |<ul><li>Windows 10  |針對 Windows，選取要在裝置上儲存金鑰的位置。 |
   |**憑證授權單位**      |<ul><li>全部         |顯示您企業 CA 的內部完整網域名稱 (FQDN)。  |
   |**憑證授權單位名稱** |<ul><li>全部         |列出您企業 CA 的名稱，例如 "Contoso Certification Authority"。 |
   |**憑證範本名稱**    |<ul><li>全部         |列出您的憑證範本名稱。 |
   |**憑證類型**             |<ul><li>Android Enterprise (工作設定檔  )</li><li>iOS</li><li>macOS</li><li>Windows 10 及更新版本|選取類型： <ul><li> [使用者]  憑證可在憑證的主旨與 SAN 中包含使用者屬性和裝置屬性。 </il><li>[裝置]  憑證只能在憑證的主旨與 SAN 中包含裝置屬性。 針對無使用者裝置 (如 Kiosk 或其他共用裝置) 等情況使用 [裝置]。  <br><br> 此選項會影響 [主體名稱格式]。 |
   |**主體名稱格式**          |<ul><li>全部         |如需如何設定主體名稱格式的詳細資料，請參閱本文稍後的[主體名稱格式](#subject-name-format)。  <br><br> 針對大部分平台，除非另有需要，否則請使用 [一般名稱]  選項。 <br><br>對於下列平台，[主體名稱格式] 取決於憑證類型： <ul><li>Android Enterprise (工作設定檔  )</li><li>iOS</li><li>macOS</li><li>Windows 10 及更新版本</li></ul>  <p>  |
   |**主體別名**     |<ul><li>全部         |針對「屬性」  ，除非另有需要，否則請選取 [使用者主體名稱 (UPN)]  並設定對應的「值」  ，然後按一下 [新增]  。 <br><br>如需詳細資訊，請參閱本文稍後的[主體名稱格式](#subject-name-format)。|
   |**擴充金鑰使用方法**           |<ul><li> Android 裝置管理員 </li><li>Android Enterprise (裝置擁有者  、工作設定檔  ) </li><li>Windows 10 |憑證需要 [用戶端驗證]  ，使用者或裝置才能向伺服器進行驗證。 |
   |**允許所有應用程式存取私密金鑰** |<ul><li>macOS  |設定為 [啟用]  ，將 PKCS 憑證私密金鑰的存取權，授與為相關聯 Mac 裝置設定的應用程式。 <br><br> 如需此設定的詳細資訊，請參閱 Apple 開發人員文件中[組態設定檔參考](https://developer.apple.com/business/documentation/Configuration-Profile-Reference.pdf) \(英文\) 的 *AllowAllAppsAccess* 憑證承載一節。 |
   |**根憑證**             |<ul><li>Android 裝置管理員 </li><li>Android Enterprise (裝置擁有者  、工作設定檔  ) |選取先前指派的根 CA 憑證設定檔。 |

5. 選取 [確定]   > [建立]  儲存您的設定檔。

6. 若要將新的設定檔指派給一或多部裝置，請參閱[指派 Microsoft Intune 裝置設定檔](../configuration/device-profile-assign.md)。

   > [!NOTE]
   > 在具有 Android 企業設定檔的裝置上，使用 PKCS 憑證設定檔安裝的憑證不會顯示在裝置上。 若要確認憑證部署成功，請在 Intune 主控台中檢查設定檔的狀態。

### <a name="subject-name-format"></a>主體名稱格式

當您針對下列平台建立 PKCS 憑證設定檔時，主體名稱格式的選項，取決於您選取的憑證類型 ([使用者]  或 [裝置]  )。  

平台：

- Android Enterprise (工作設定檔  )
- iOS
- macOS
- Windows 10 及更新版本

> [!NOTE]
> 當產生的憑證簽署要求 (CSR) 中的主體名稱包含下列其中一個字元作為逸出字元 (以反斜線 \\ 開頭) 時，使用 PKCS 取得憑證有一個[已知問題](certificates-profile-scep.md#avoid-certificate-signing-requests-with-escaped-special-characters)，如同在 SCEP 所見的問題：
> - \+
> - ;
> - ,
> - =

- **使用者憑證類型**  
  「主體名稱格式」  的格式選項包括兩個變數：**一般名稱 (CN)** 和**電子郵件 (E)** 。 **一般名稱 (CN)** 可以設定為下列任何變數：

  - **CN={{UserName}}** ：使用者的使用者主體名稱，例如 janedoe@contoso.com。
  - **CN={{AAD_Device_ID}}** ：您在 Azure Active Directory (AD) 中註冊裝置時所指派的識別碼。 此識別碼通常用於向 Azure AD 驗證。
  - **CN={{SERIALNUMBER}}** ：製造商通常用來識別裝置的唯一序號 (SN)。
  - **CN={{IMEINumber}}** ：用來識別行動電話的國際行動設備識別碼 (IMEI)。
  - **CN={{OnPrem_Distinguished_Name}}** ：以逗號分隔的相對辨別名稱序列，例如 *CN=Jane Doe,OU=UserAccounts,DC=corp,DC=contoso,DC=com*。

    若要使用 *{{OnPrem_Distinguished_Name}}* 變數，請務必使用 [Azure AD Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect) 將 *onpremisesdistinguishedname* 使用者屬性同步至您的 Azure AD。

  - **CN={{onPremisesSamAccountName}}** ：系統管理員可使用 Azure AD 連線到稱為 *onPremisesSamAccountName* 的屬性，將 Active Directory 的 samAccountName 屬性與 Azure AD 同步。 Intune 可將該變數替換為憑證主體中憑證發行要求的一部分。 samAccountName 屬性是使用者登入名稱，用於支援舊版 Windows 客戶端和伺服器 (Windows 2000 以前的版本)。 使用者登入名稱格式為：*DomainName\testUser*，或僅 *testUser*。

    若要使用 *{{onPremisesSamAccountName}}* 變數，請務必使用 [Azure AD Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect) 將 *onPremisesSamAccountName* 使用者屬性同步至您的 Azure AD。

  您可以結合使用一或多個這些變數和靜態字串，建立自訂的主體名稱格式，如下：  
  - **CN={{UserName}},E={{EmailAddress}},OU=Mobile,O=Finance Group,L=Redmond,ST=Washington,C=US**
  
  該範例包含使用 CN 和 E 變數的主體名稱格式，以及組織單位、組織、位置、縣/市及國家/地區值的字串。 [CertStrToName 函式](https://msdn.microsoft.com/library/windows/desktop/aa377160.aspx) 說明此函式和它支援的字串。

- **裝置憑證類型**  
  主體名稱格式的格式選項包括下列變數： 
  - **{{AAD_Device_ID}}**
  - **{{Device_Serial}}**
  - **{{Device_IMEI}}**
  - **{{SerialNumber}}**
  - **{{IMEINumber}}**
  - **{{AzureADDeviceId}}**
  - **{{WiFiMacAddress}}**
  - **{{IMEI}}**
  - **{{DeviceName}}**
  - **{{FullyQualifiedDomainName}}** *(僅適用於 Windows 和已加入網域的裝置)*
  - **{{MEID}}**

  您可以在文字方塊中指定這些變數，後接變數的文字。 例如，名為 *Device1* 的裝置一般名稱可以新增為 **CN={{DeviceName}}Device1**。

  > [!IMPORTANT]  
  > - 當您指定變數時，請將變數名稱括在大括弧 { } 中 (如範例所示)，以避免發生錯誤。  
  > - 裝置憑證的「主體」  或 *SAN* 中所使用裝置屬性 (例如 **IMEI**、**SerialNumber** 和 **FullyQualifiedDomainName**)，這些屬性可由具有裝置存取權的人員來偽造。
  > - 裝置必須支援憑證設定檔中指定的所有變數，才能在該裝置上安裝該設定檔。  例如，如果 SCEP 設定檔的主體名稱中使用 **{{IMEI}}** ，但該設定檔指派給沒有 IMEI 編號的裝置，則設定檔安裝將會失敗。  
 
## <a name="whats-new-for-connectors"></a>連接器的新功能

這兩個憑證連接器的更新會定期發行。 當我們更新連接器時，您可在此閱讀有關變更的資訊。

「適用於 Microsoft Intune 的 PFX 憑證連接器」  [支援自動更新](#requirements)，而「Intune 憑證連接器」  則以手動方式更新。

### <a name="may-17-2019"></a>2019 年 5 月 17 日

- **適用於 Microsoft Intune 的 PFX 憑證連接器 - 6.1905.0.404 版**  
  此版本的變更：  
  - 已修正現有 PFX 憑證繼續重新處理而導致連接器停止處理新要求的問題。 

### <a name="may-6-2019"></a>2019 年 5 月 6 日

- **適用於 Microsoft Intune 的 PFX 憑證連接器 - 6.1905.0.402 版**  
  此版本的變更：  
  - 連接器的輪詢間隔已從 5 分鐘縮短為 30 秒。

### <a name="april-2-2019"></a>2019 年 4 月 2 日

- **Intune 憑證連接器 - 6.1904.1.0 版**  
  此版本的變更：  
  - 修正了使用全域系統管理員帳戶登入連接器之後，連接器無法向 Intune 註冊的問題。  
  - 包含憑證撤銷的可靠性修正。  
  - 包含效能修正，用來提高處理 PKCS 憑證要求的速度。  

- **適用於 Microsoft Intune 的 PFX 憑證連接器 - 6.1904.0.401 版**
  > [!NOTE]  
  > 在 2019 年 4 月 11 日之前，不提供適用於這個 PFX 連接器版本的自動更新。  

  此版本的變更：  
  - 修正了使用全域系統管理員帳戶登入連接器之後，連接器無法向 Intune 註冊的問題。  


## <a name="next-steps"></a>後續步驟

設定檔已建立，但還不會執行任何動作。 接下來，[指派設定檔](../configuration/device-profile-assign.md)並[監視其狀態](../configuration/device-profile-monitor.md)。

[使用 SCEP 憑證](certificates-scep-configure.md)，或[從 Symantec PKI Manager Web 服務發行 PKCS 憑證](certificates-digicert-configure.md)。

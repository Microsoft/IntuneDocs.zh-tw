---
title: 在 Microsoft Intune 中使用匯入的 PFX 憑證 - Azure | Microsoft Docs
description: 搭配 Microsoft Intune 使用匯入的公開金鑰加密標準 (PKCS) 憑證，包括匯入憑證、設定憑證範本、安裝 Intune 匯入的 PFX 憑證連接器，以及建立匯入的 PKCS憑證設定檔。
keywords: ''
author: ralms
ms.author: brenduns
manager: dougeby
ms.date: 09/16/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 18d01692f8c42b67605c223f59e13b1e5197a8db
ms.sourcegitcommit: 3db8af810b95c3a6ed3f8cc00f6ce79076ebb9db
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/16/2019
ms.locfileid: "71017133"
---
# <a name="configure-and-use-imported-pkcs-certificates-with-intune"></a>透過 Intune 設定並使用匯入的 PKCS 憑證

Microsoft Intune 支援使用匯入的公開金鑰組 (PKCS) 憑證，通常用於具有電子郵件設定檔的 S/MIME 加密。 Intune 中的某些電子郵件設定檔支援啟用 S/MIME 的選項，您可以在其中定義 S/MIME 簽署憑證和 S/MIME 加密憑證。

S/MIME 加密很具挑戰性，因為電子郵件是以特定憑證加密。 在您閱讀電子郵件的裝置上，您必須擁有加密電子郵件的憑證私密金鑰，以便對電子郵件進行解密。 加密憑證會定期更新，這表示您可能需要所有裝置上的加密歷程記錄，以確保您可以讀取較舊的電子郵件。  由於必須跨裝置使用相同的憑證，因此無法將 [SCEP](certificates-scep-configure.md) 或 [PKCS](certficates-pfx-configure.md) 憑證設定檔用於此目的，因為那些憑證傳遞機制提供了每一裝置唯一的憑證。 

如需搭配 Intune 使用 S/MIME 的詳細資訊，請參閱[使用 S/MIME 來加密電子郵件](certificates-s-mime-encryption-sign.md)。

## <a name="requirements"></a>需求

若要透過 Intune 使用匯入的 PKCS 憑證，您需要下列基礎結構：

- **適用於 Microsoft Intune 的 PFX 憑證連接器**：  
  每個 Intune 租用戶都支援此連接器的單一執行個體。 您可在相同的伺服器上安裝此連接器，作為 Microsoft Intune 憑證連接器的執行個體。

  此連接器會處理對 Intune 中所匯入之 PFX 檔案的要求，為特定使用者進行 S/MIME 電子郵件加密。  

  當新版本可供使用時，此連接器會自動自行更新。 若要使用更新功能，您必須確定防火牆已開啟，可讓連接器在連接埠 **443** 上連絡 **autoupdate.msappproxy.net**。  

  如需連接器所存取之所有網路端點的詳細資訊，請參閱 [Intune 網路設定需求和頻寬](https://docs.microsoft.com/intune/network-bandwidth-use)。


- **Windows Server**：  
  您會使用 Windows Server 來裝載適用於 Microsoft Intune 的 PFX 憑證連接器。  連接器是用來處理匯入至 Intune 之憑證的要求。

  Intune 支援在與*適用於 Microsoft Intune 的 PFX 憑證連接器*相同的伺服器上安裝 *Microsoft Intune 憑證連接器*。

  若要支援連接器，伺服器必須執行 .NET 4.6 Framework 或更高版本。 當您開始安裝連接器時，如果未安裝 .NET 4.6 Framework，連接器安裝將會自動安裝。

- **Visual Studio 2015 或更新版本** (選擇性)：您可以使用 Visual Studio 來建置協助程式 PowerShell 模組，並使用 Cmdlet 將 PFX 憑證匯入至 Microsoft Intune。 若要取得協助程式 PowerShell Cmdlet，請參閱 [GitHub 中的 PFXImport PowerShell 專案](https://github.com/microsoft/Intune-Resource-Access/tree/develop/src/PFXImportPowershell) \(英文\)。

## <a name="how-it-works"></a>運作方式

當您使用 Intune 將**匯入的 PFX 憑證**部署至使用者時，除了裝置之外，還會有兩個執行元件： 

- **Intune 服務**：會以加密狀態儲存 PFX 憑證，並處理憑證到使用者裝置的部署。  保護憑證私密金鑰的密碼會在使用硬體安全性模組 (HSM) 或 Windows 加密來上傳之前進行加密，以確保 Intune 無法隨時存取私密金鑰。
- **適用於 Microsoft Intune 的 PFX 憑證連接器**：當裝置要求已匯入至 Intune 的 PFX 憑證時，加密的密碼、憑證和裝置的公開金鑰會傳送至連接器。  連接器會使用內部部署私密金鑰來解密密碼，然後在將憑證傳送回 Intune 之前，使用裝置金鑰重新加密密碼 (和任何 plist 設定檔，如果使用 iOS 的話)。  Intune 接著會將憑證傳遞至裝置，而裝置可以使用裝置的私密金鑰將它解密，並安裝憑證。

## <a name="download-install-and-configure-the-pfx-certificate-connector-for-microsoft-intune"></a>為 Microsoft Intune 下載、安裝並設定 PFX 憑證連接器

1. 在 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) 入口網站中，選取 [裝置設定]   > [憑證連接器]   > [新增] 

   ![下載適用於 Microsoft Intune 的 PFX 憑證連接器](media/certificates-imported-pfx-configure/download-imported-pfxconnector.png)

2. 遵循指導方針，將*適用於 Microsoft Intune 的 PFX 憑證連接器*下載到可從您要安裝連接器之伺服器存取的位置。
3. 下載完成之後，請登入伺服器，然後執行安裝程式 (PfxCertificateConnectorBootstrapper.exe)。  
   - 當您接受預設安裝位置時，連接器會安裝到 `Program Files\Microsoft Intune\PFXCertificateConnector`。
   - 連接器服務會以本機系統帳戶執行。 如果網際網路存取需要 Proxy，請確認本機服務帳戶可以存取伺服器上的 Proxy 設定。

4. 適用於 Microsoft Intune 的 PFX 憑證連接器隨即會在安裝之後開啟 [註冊]  索引標籤。 若要啟用 Intune 的連線，請 [登入]  ，並輸入具有 Azure 全域管理員或 Intune 系統管理員權限的帳戶。

   > [!WARNING]
   > 根據預設，在 Windows Server 中，[IE 增強式安全性設定]  已設定為 [開啟]  ，這可能會造成登入 Office 365 發生問題。

5. 關閉視窗。
6. 在 Intune 入口網站中，返回 [裝置設定]   > [憑證連接器]  。 在幾分鐘後，會出現綠色的核取記號，且 [連線狀態]  為 [使用中]  。 連接器伺服器現在可以與 Intune 通訊。

## <a name="import-pfx-certificates-to-intune"></a>將 PFX 憑證匯入至 Intune

您可以使用 [Microsoft Graph](https://docs.microsoft.com/graph)，將您的使用者 PFX 憑證匯入 Intune。 GitHub 上的 [PFXImport PowerShell 專案協助程式](https://github.com/microsoft/Intune-Resource-Access/tree/develop/src/PFXImportPowershell) \(英文\) 提供 Cmdlet，讓您輕鬆地執行作業。

如果您偏好使用 Graph 使用自己的自訂解決方案，請使用 [userPFXCertificate 資源類型](https://docs.microsoft.com/graph/api/resources/intune-raimportcerts-userpfxcertificate?view=graph-rest-beta)。

### <a name="build-pfximport-powershell-project-cmdlets"></a>建置 'PFXImport PowerShell 專案' Cmdlet

若要使用 PowerShell Cmdlet，您可以使用 Visual Studio 自行建置專案。 程序很簡單，雖然它可以在伺服器上執行，但我們建議您在工作站上執行。  

1. 前往 GitHub 上的 [Intune-Resource-Access](https://github.com/microsoft/Intune-Resource-Access) 存放庫的根目錄，然後使用 Git 將存放庫下載或複製到您的電腦。

   ![GitHub [下載] 按鈕](media/certificates-imported-pfx-configure/github-download.png)

2. 移至 `.\Intune-Resource-Access-develop\src\PFXImportPowershell\`，並透過 Visual Studio 使用 **PFXImportPS.sln** 檔案來開啟專案。
3. 在頂端，從 [偵錯]  變更為 [發行]  。
4. 移至 [建置]  ，然後選取 [建置 PFXImportPS]  。 幾分鐘後，您會看到 [建置成功]  確認通知出現在 Visual Studio 的左下方。

   ![Visual Studio [建置] 選項](media/certificates-imported-pfx-configure/vs-build-release.png)

5. 建置程序會使用位於 `.\Intune-Resource-Access-develop\src\PFXImportPowershell\PFXImportPS\bin\Release` 的 PowerShell 模組來建立新的資料夾。

   您將使用此 [發行]  資料夾進行後續步驟。

### <a name="create-the-encryption-public-key"></a>建立加密公開金鑰

您會將 PFX 憑證和其私密金鑰匯入至 Intune。 保護私密金鑰的密碼會使用儲存在內部部署的公開金鑰進行加密。 您可以使用 Windows 密碼編譯、硬體安全性模組或其他類型的密碼編譯來產生及儲存公開/私密金鑰組。  視使用的密碼編譯類型而定，公開/私密金鑰組可以供備份之用的檔案格式匯出。

PowerShell 模組提供了使用 Windows 密碼編譯建立金鑰的方法。 您也可以使用其他工具來建立金鑰。  

#### <a name="to-create-the-encryption-key-using-windows-cryptography"></a>使用 Windows 密碼編譯建立加密金鑰

1. 將 Visual Studio 建立的 [發行]  資料夾複製到您安裝**適用於 Microsoft Intune 的 PFX 憑證連接器**的伺服器。 此資料夾包含 PowerShell 模組。  
2. 在伺服器上，以系統管理員身分開啟 *PowerShell*，然後瀏覽至包含 PowerShell 模組的 [發行]  資料夾。
3. 若要匯入模組，請執行 `Import-Module .\IntunePfxImport.psd1` 來匯入模組。
4. 接下來，執行 `Add-IntuneKspKey "Microsoft Software Key Storage Provider" "PFXEncryptionKey"`

   > [!TIP]  
   > 當您匯入 PFX 憑證時，必須再次選取您所使用的提供者。 雖然支援使用不同的提供者，但您可以使用 **Microsoft 軟體金鑰儲存體提供者**。 金鑰名稱也作為範例提供，且您可以使用您選擇的不同金鑰名稱。  

   如果您想要從您的工作站匯入憑證，可以使用下列命令將此金鑰匯出至檔案：  `Export-IntunePublicKey -ProviderName "<ProviderName>" -KeyName "<KeyName>" -FilePath "<File path to write to>"`

   您必須為 Microsoft Intune 在裝載 PFX 憑證連接器的伺服器上匯入私密金鑰，才能順利處理匯入的 PFX 憑證。  

#### <a name="to-use-a-hardware-security-module-hsm"></a>使用硬體安全性模組 (HSM)  

您可以使用硬體安全性模組 (HSM) 來產生及儲存公開/私密金鑰組。 如需詳細資訊，請參閱 HSM 提供者的文件。

### <a name="import-pfx-certificates"></a>匯入 PFX 憑證 

下列程序會使用 PowerShell Cmdlet 作為如何匯入 PFX 憑證的範例。 視您的需求而定，您可以挑選不同的選項。

這些選項包括：  
- 預期的用途 (根據標籤將憑證分組)：  
  - 未指派
  - smimeEncryption
  - smimeSigning


- 填補配置：  
  - pkcs1
  - oaepSha1
  - oaepSha256
  - oaepSha384
  - oaepSha512

選取符合您用來建立金鑰之提供者的金鑰儲存體提供者。

#### <a name="to-import-the-pfx-certificate"></a>匯入 PFX 憑證  

1. 遵循提供者的文件，從任何憑證授權單位 (CA) 匯出憑證。  針對 Microsoft Active Directory 憑證服務，您可以使用[此範例指令碼](https://gallery.technet.microsoft.com/Export-CMPfxCertificatesFro-d55f687b)。   
2. 在伺服器上，以系統管理員身分開啟 *PowerShell*，然後瀏覽至包含 PowerShell 模組的 [發行]  資料夾。
3. 若要匯入模組，請執行 `Import-Module .\IntunePfxImport.psd1`  
4. 若要向 Intune Graph 進行驗證，請執行 `$authResult = Get-IntuneAuthenticationToken -AdminUserName "<Admin-UPN>"`

   > [!NOTE]
   > 當針對 Graph 執行驗證時，您必須向 AppID 提供權限。 如果這是您第一次使用此公用程式，則需要*全域系統管理員*。 Powershell Cmdlet 會使用與 [PowerShell Intune 範例](https://github.com/microsoftgraph/powershell-intune-samples) \(英文\) 搭配使用的同一個 AppID。   
5. 透過執行 `$SecureFilePassword = ConvertTo-SecureString -String "<PFXPassword>" -AsPlainText -Force` 將要匯入的每個 PFX 檔案的密碼都轉換成安全字串。  
6. 若要建立 **UserPFXCertificate** 物件，請執行 `$userPFXObject = New-IntuneUserPfxCertificate -PathToPfxFile "<FullPathPFXToCert>" $SecureFilePassword "<UserUPN>" "<ProviderName>" "<KeyName>" "<IntendedPurpose>" "<PaddingScheme>"`

   例如：`$userPFXObject = New-IntuneUserPfxCertificate -PathToPfxFile "C:\temp\userA.pfx" $SecureFilePassword "userA@contoso.com" "Microsoft Software Key Storage Provider" "PFXEncryptionKey" "smimeEncryption" "pkcs1"`

   > [!NOTE]  
   > 當您從安裝連接器的伺服器以外的系統匯入憑證時，必須使用包含金鑰檔案路徑的下列命令：`$userPFXObject = New-IntuneUserPfxCertificate -PathToPfxFile "<FullPathPFXToCert>" $SecureFilePassword "<UserUPN>" "<ProviderName>" "<KeyName>" "<IntendedPurpose>" "<PaddingScheme>" "<File path to public key file>"`

7. 透過執行 `Import-IntuneUserPfxCertificate -AuthenticationResult $authResult -CertificateList $userPFXObject` 將 **UserPFXCertificate** 物件匯入至 Intune

8. 若要驗證憑證是否已匯入，請執行 `Get-IntuneUserPfxCertificate -AuthenticationResult $authResult -UsertList "<UserUPN>"`

如需其他可用命令的詳細資訊，請參閱 [GitHub 上的 PFXImport PowerShell 專案](https://github.com/microsoft/Intune-Resource-Access/tree/develop/src/PFXImportPowershell) \(英文\) 中的讀我檔案。

## <a name="create-a-pkcs-imported-certificate-profile"></a>建立 PKCS 匯入憑證設定檔

將憑證匯入至 Intune 之後，請建立 **PKCS 匯入憑證**設定檔，並將它指派給 Azure Active Directory 群組。

1. 在 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) 入口網站中，移至 [裝置設定]   > [設定檔]   > [建立設定檔]  。
2. 輸入下列內容：

   - 設定檔的 [名稱] 
   - 可選擇性地設定說明
   - 要部署設定檔的目標 [平台] 
   - 將 [設定檔類型]  設定為 [PKCS 匯入憑證] 

3. 移至 [設定]  索引標籤，然後輸入下列內容：

   - **使用目的**：指定此設定檔匯入之憑證的使用目的。 系統管理員可以匯入使用目的不同 (例如驗證、S/MIME 簽署或 S/MIME 加密) 的憑證。 憑證設定檔中選取的使用目的符合含有正確匯入憑證的憑證設定檔。 使用目的是將匯入的憑證分組的標記，並不保證使用該標記匯入的憑證會符合使用目的。  
   - **憑證有效期間**：除非已在憑證範本中變更有效期間，否則此選項預設為一年。  
   - **金鑰儲存提供者 (KSP)** ：針對 Windows，選取要在裝置上儲存金鑰的位置。  

4. 選取 [確定]   > [建立]  儲存您的設定檔。
5. 若要將新的設定檔指派給一或多部裝置，請參閱[指派 Microsoft Intune 裝置設定檔](device-profile-assign.md)。




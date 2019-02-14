---
title: 在 Microsoft Intune 中使用私密和公開金鑰憑證 - Azure | Micrososft Docs
description: 使用 Microsoft Intune 新增或建立公開金鑰加密標準 (PKCS) 憑證，包括匯出根憑證、設定憑證範本、下載並安裝 Microsoft Intune 憑證連接器 (NDES)、建立裝置組態設定檔、在 Azure 與您的憑證授權單位中建立 PKCS 憑證設定檔等步驟。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 12/10/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5c2c649df23a84d8836a68fd0456da6ce8dda2c0
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/07/2019
ms.locfileid: "55837272"
---
# <a name="configure-and-use-pkcs-certificates-with-intune"></a>透過 Intune 設定並使用 PKCS 憑證

憑證會驗證並保護您的公司資源存取，例如 VPN 或 Wi-Fi 網路。 使用私密和公開金鑰組的憑證也稱為 PKCS 憑證，這是許多組織所採用的憑證。 Microsoft Intune 中包含的內建設定，可使用 PKCS 憑證對您的組織資源進行存取和驗證。 這些設定使用 Intune 的裝置組態設定檔來推送 (或部署) 到裝置。

本文列出使用 PKCS 憑證的需求、示範如何匯出 PKCS 憑證，並將憑證新增至 Intune 裝置組態設定檔。

## <a name="requirements"></a>需求

若要透過 Intune 使用 PKCS 憑證，您必須具備下列基礎結構：

- **Active Directory 網域**：本節所列的所有伺服器均須加入 Active Directory 網域。

  如需安裝和設定 AD DS 的詳細資訊，請參閱 [AD DS 設計與規劃](https://docs.microsoft.com/windows-server/identity/ad-ds/plan/ad-ds-design-and-planning)。

- **憑證授權單位** (CA)：企業憑證授權單位 (CA)

  如需安裝和設定 Active Directory 憑證服務 (AD CS) 的詳細資訊，請參閱 [Active Directory 憑證服務逐步指南](https://technet.microsoft.com/library/cc772393)。

  > [!WARNING]
  > Intune 需要您搭配企業憑證授權單位 (CA) 執行 AD CS，而非獨立 CA。

- **用戶端**：連線到企業 CA

- **根憑證**：從您企業 CA 匯出的根憑證複本

- **Microsoft Intune 憑證連接器**：使用 Azure 入口網站來下載**憑證連接器**安裝程式 (**NDESConnectorSetup.exe**)。 

  連接器會處理用於驗證或 S/MIME 電子郵件簽署的 PKCS 憑證要求。

  NDES 憑證連接器也支援聯邦資訊處理標準 (FIPS) 模式。 FIPS 並非必要，但啟用時可發出及撤銷憑證。

- **適用於 Microsoft Intune 的 PFX 憑證連接器**：如果您計劃使用 S/MIME 電子郵件加密，請使用 Azure 入口網站來下載**適用於 Microsoft Intune 的 PFX 憑證連接器**安裝程式 (**PfxCertificateConnectorBootstrapper.exe**)。 連接器會處理對 Intune 中所匯入之 PFX 檔案的要求，為特定使用者進行 S/MIME 電子郵件加密。

- **Windows Server**：裝載：

  - Microsoft Intune 憑證連接器 (NDESConnectorSetup.exe)，用於驗證和 S/MIME 電子郵件簽署情況
  - 適用於 Microsoft Intune 的 PFX 憑證連接器 (PfxCertificateConnectorBootstrapper.exe)，用於 S/MIME 電子郵件加密情況。

  您可以在相同的伺服器上執行這兩種連接器 (**Microsoft Intune 憑證連接器**和**適用於 Microsoft Intune 的 PFX 憑證連接器**)。

## <a name="export-the-root-certificate-from-the-enterprise-ca"></a>從企業 CA 匯出根憑證

若要向 VPN、Wi-Fi 和其他資源進行驗證，在每部裝置上都需要根憑證或中繼 CA 憑證。 下列步驟說明如何從您的企業 CA 取得所需的憑證。

1. 使用具有系統管理權限的帳戶登入您的企業 CA。
2. 以系統管理員身分開啟命令提示字元。
3. 將根 CA 憑證 (.cer) 匯出到您稍後可以加以存取的位置。
4. 在精靈完成後，但在關閉精靈之前，按一下 [啟動 Certificate Connector UI] 。

   `certutil -ca.cert certnew.cer`

   如需詳細資訊，請參閱[管理憑證的 Certutil 工作](https://technet.microsoft.com/library/cc772898.aspx#BKMK_ret_sign)。

## <a name="configure-certificate-templates-on-the-ca"></a>設定 CA 上的憑證範本

1. 使用具有系統管理權限的帳戶登入您的企業 CA。
2. 開啟 [憑證授權單位] 主控台、以滑鼠右鍵按一下 [憑證範本]，然後選取 [管理]。
3. 找出 [使用者] 憑證範本、以滑鼠右鍵按一下它，然後選擇 [複製範本]。 [新範本的內容] 隨即開啟。

    > [!NOTE]
    > 在 S/MIME 電子郵件簽署和加密情況下，許多系統管理員使用個別的憑證進行簽署和加密。 如果您要使用 Microsoft Active Directory 憑證服務，則可以將 [僅限 Exchange 簽章] 範本用於 S/MIME 電子郵件簽署憑證，並將 [Exchange 使用者] 範本用於 S/MIME 加密憑證。  如果您要使用協力廠商憑證授權單位，建議您檢閱其設定簽署和加密範本的指引。

4. 在 [相容性] 索引標籤上：

    - 將 [憑證授權單位] 設為 [Windows Server 2008 R2]
    - 將 [憑證接收者] 設為 [Windows 7 / Server 2008 R2]

5. 在 [一般] 索引標籤上，將 [範本顯示名稱] 設為對您有意義的名稱。

    > [!WARNING]
    > [範本名稱] 預設會與 [範本顯示名稱] 相同，但*沒有空格*。 請記下範本名稱，您之後會需要它。

6. 在 [要求處理] 索引標籤中，選取 [允許匯出私密金鑰]。
7. 在 [密碼編譯] 中，確認 [最小金鑰大小] 已設為 2048。
8. 在 [主體名稱] 中，選擇 [在要求中提供]。
9. 在 [延伸模組] 中，確認您在 [應用程式原則] 下看到「加密檔案系統」、「安全電子郵件」和「用戶端驗證」。

    > [!IMPORTANT]
    > 若為 iOS 憑證範本，請移至 [延伸模組] 索引標籤、更新 [金鑰使用方法]，並確認未選取 [簽章是原件證明]。

10. 在 [安全性] 中，新增您安裝 Microsoft Intune 憑證連接器之伺服器的電腦帳戶。 允許此帳戶的 [讀取] 和 [註冊] 權限。
11. 選取 [套用] > [確定]，儲存憑證範本。 關閉 [憑證範本主控台] 。
12. 在 [憑證授權單位] 主控台中，以滑鼠右鍵按一下 [憑證範本] > [新增] > [要發出的憑證範本]。 選擇您在前述步驟中建立的範本。 選取 [確定]。
13. 若要讓伺服器為已註冊的裝置及使用者管理憑證，請使用下列步驟：

    1. 以滑鼠右鍵按一下憑證授權單位，選擇 [內容]。
    2. 在 [安全性] 索引標籤上，新增您執行連接器 (**Microsoft Intune 憑證連接器**或**適用於 Microsoft Intune 的 PFX 憑證連接器**) 之伺服器的電腦帳戶。 
    3. 將 [發行及管理憑證] 和 [要求憑證] 的「允許」權限授與該電腦帳戶。

14. 登出企業 CA。

## <a name="download-install-and-configure-the-certificate-connectors"></a>下載、安裝和設定憑證連接器

### <a name="microsoft-intune-certificate-connector"></a>Microsoft Intune Certificate Connec設為 [https]r

> [!IMPORTANT] 
> Microsoft Intune Certificate Connector **必須**安裝在個別的 Windows 伺服器中。 它不能安裝在發行的授權憑證單位 (CA) 上。

1. 在 [Azure 入口網站](https://portal.azure.com)中，選取 [所有服務] > 篩選 [Intune] > 選取 [Intune]。
2. 選取 [裝置設定] > [憑證授權單位] > [新增]。
3. 下載並儲存連接器檔案。 請將它儲存到可從將安裝連接器的伺服器存取的位置。

    ![ConnectorDownload][ConnectorDownload]

4. 下載完成後，請登入伺服器。 然後：

    1. 確定已安裝 .NET 4.5 Framework 或更高版本，這是 NDES 憑證連接器的必要項目。 Windows Server 2012 R2 及更新版本會自動隨附 .NET 4.5 Framework。
    2. 執行安裝程式 (NDESConnectorSetup.exe)，並接受預設位置。 它會將連接器安裝到 `\Program Files\Microsoft Intune\NDESConnectorUI`。 在 [安裝程式選項] 中，選取 [PFX 發佈]。 繼續並完成安裝。
    3. 連接器服務預設會以本機系統帳戶執行。 如果需要有 Proxy 才能存取網際網路，請確認本機服務帳戶可以存取伺服器上的 Proxy 設定。

5. [NDES 連接器] 會開啟 [註冊] 索引標籤。若要連線到 Intune，請**登入**並輸入具有全域系統管理權限的帳戶。
6. 在 [進階] 索引標籤上，建議保持選取 [使用此電腦的 SYSTEM 帳戶 (預設)]。
7. [套用] > [關閉]
8. 返回 Azure 入口網站 ([Intune] > [裝置設定] > [憑證授權單位])。 在幾分鐘後會顯示綠色的核取記號，且 [連線狀態] 為 [使用中]。 連接器伺服器現在可以與 Intune 通訊。
9. 如果在您的網路環境中有 Web Proxy，您可能需要其他設定才能讓連接器運作。 如需詳細資訊，請參閱 Azure Active Directory 文件中的[使用現有的內部部署 Proxy 伺服器](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy-configure-connectors-with-proxy-servers)。

> [!NOTE]
> Microsoft Intune 憑證連接器隨附 TLS 1.2 支援。 因此，如果安裝 Microsoft Intune 憑證連接器的伺服器支援 TLS 1.2，則會使用 TLS 1.2。 如果伺服器不支援 TLS 1.2，則會使用 TLS 1.1。 目前，使用 TLS 1.1 在裝置與伺服器之間進行驗證。

### <a name="pfx-certificate-connector-for-microsoft-intune"></a>適用於 Microsoft Intune 的 PFX 憑證連接器

1. 在 [Azure 入口網站](https://portal.azure.com)中，選取 [所有服務]，篩選 [Intune]，然後選取 [Microsoft Intune]。
2. 選取 [裝置設定] > [憑證授權單位] > [新增]
3. 下載並儲存適用於 Microsoft Intune 的 PFX 憑證連接器。 請將它儲存到可從將安裝連接器的伺服器存取的位置。
4. 下載完成後，請登入伺服器。 然後：

    1. 確定已安裝 .NET 4.6 Framework 或更高版本，這是適用於 Microsoft Intune 之 PFX 憑證連接器的必要項目。 如果未安裝 .NET 4.6 Framework，安裝程式就會自動安裝它。
    2. 執行安裝程式 (PfxCertificateConnectorBootstrapper.exe)，並接受預設位置。 它會將連接器安裝到 `Program Files\Microsoft Intune\PFXCertificateConnector`。
    3. 連接器服務會以本機系統帳戶執行。 如果網際網路存取需要 Proxy，則請確認本機服務帳戶可以存取伺服器上的 Proxy 設定。

5. 適用於 Microsoft Intune 的 PFX 憑證連接器隨即會在安裝之後開啟 [註冊] 索引標籤。 若要啟用 Intune 的連線，請 [登入]，並輸入具有 Azure 全域管理員或 Intune 系統管理員權限的帳戶。
6. 關閉視窗。
7. 返回 Azure 入口網站 ([Intune] > [裝置設定] > [憑證授權單位])。 在幾分鐘後會顯示綠色的核取記號，且 [連線狀態] 為 [使用中]。 連接器伺服器現在可以與 Intune 通訊。

## <a name="create-a-trusted-certificate-profile"></a>建立受信任的憑證設定檔

1. 在 [Azure 入口網站](https://portal.azure.com)，移至 [Intune] > [裝置設定] > [設定檔] > [建立設定檔]。

   ![NavigateIntune][NavigateIntune]

2. 輸入下列內容：

    - 設定檔的 [名稱]
    - 可選擇性地設定說明
    - 要部署設定檔的目標 [平台]
    - 將 [設定檔類型] 設為 [信任的憑證]

3. 移至 [設定]，並輸入先前匯出的根 CA 憑證 .cer 檔案。

   > [!NOTE]
   > 視您在**步驟 3** 中選擇的平台而定，您可能會有選擇憑證 [目的地存放區] 的選項。

   ![ProfileSettings][ProfileSettings]

4. 選取 [確定] > [建立] 儲存您的設定檔。
5. 若要將新的設定檔指派給一或多部裝置，請參閱[指派 Microsoft Intune 裝置設定檔](device-profile-assign.md)。

## <a name="create-a-pkcs-certificate-profile"></a>建立 PKCS 憑證設定檔

1. 在 [Azure 入口網站](https://portal.azure.com)，移至 [Intune] > [裝置設定] > [設定檔] > [建立設定檔]。
2. 輸入下列內容：

    - 設定檔的 [名稱]
    - 可選擇性地設定說明
    - 要部署設定檔的目標 [平台]
    - 將 [設定檔類型] 設為 [PKCS 憑證]

3. 移至 [設定] 索引標籤，然後輸入下列內容：

    - **更新閾值 (%)**：建議為 20%。
    - **憑證有效期間**：如果您沒有變更憑證範本，此選項可設定為一年。
    - **金鑰儲存提供者 (KSP)**：針對 Windows，選取要在裝置上儲存金鑰的位置。
    - **憑證授權單位**：顯示您企業 CA 的內部完整網域名稱 (FQDN)。
    - **憑證授權單位名稱**：列出您企業 CA 的名稱，例如 "Contoso Certification Authority"。
    - **憑證範本名稱**：稍早建立之範本的名稱。 請記住，[範本名稱] 預設會與 [範本顯示名稱] 相同，但*沒有空格*。
    - **主體名稱格式**：除非另有需要，否則請將此選項設定為 [一般名稱]。
    - **主體別名**：除非另有需要，否則請將此選項設定為 [使用者主體名稱 (UPN)]。

4. 選取 [確定] > [建立] 儲存您的設定檔。
5. 若要將新的設定檔指派給一或多部裝置，請參閱[指派 Microsoft Intune 裝置設定檔](device-profile-assign.md)。

## <a name="create-a-pkcs-imported-certificate-profile"></a>建立 PKCS 匯入憑證設定檔

您可以將先前從任何 CA 核發給特定使用者的憑證匯入至 Intune。 匯入的憑證會安裝在使用者註冊的每部裝置上。 S/MIME 電子郵件加密是將現有 PFX 憑證匯入至 Intune 的最常見情況。 使用者可能有許多憑證來加密電子郵件。 這些憑證的私密金鑰必須存在於所有使用者的裝置上，因此它們可以解密先前加密的電子郵件。

若要將憑證匯入至 Intune，您可以使用 [GitHub 上提供的 PowerShell Cmdlet](https://github.com/Microsoft/Intune-Resource-Access)。

將憑證匯入至 Intune 之後，請建立 **PKCS 匯入憑證**設定檔，並將它指派給 Azure Active Directory 群組。

1. 在 [Azure 入口網站](https://portal.azure.com)，移至 [Intune] > [裝置設定] > [設定檔] > [建立設定檔]。
2. 輸入下列內容：

    - 設定檔的 [名稱]
    - 可選擇性地設定說明
    - 要部署設定檔的目標 [平台]
    - 將 [設定檔類型] 設定為 [PKCS 匯入憑證]

3. 移至 [設定] 索引標籤，然後輸入下列內容：

    - **使用目的**：針對此設定檔匯入之憑證的使用目的。 系統管理員可能已匯入使用目的不同 (例如驗證、S/MIME 簽署或 S/MIME 加密) 的憑證。 憑證設定檔中選取的使用目的符合含有正確匯入憑證的憑證設定檔。
    - **憑證有效期間**：如果您沒有變更憑證範本，此選項可設定為一年。
    - **金鑰儲存提供者 (KSP)**：針對 Windows，選取要在裝置上儲存金鑰的位置。

4. 選取 [確定] > [建立] 儲存您的設定檔。
5. 若要將新的設定檔指派給一或多部裝置，請參閱[指派 Microsoft Intune 裝置設定檔](device-profile-assign.md)。

## <a name="next-steps"></a>後續步驟

設定檔已建立，但還不會執行任何動作。 接下來，[指派設定檔](device-profile-assign.md)並[監視其狀態](device-profile-monitor.md)。

[使用 SCEP 憑證](certificates-scep-configure.md)，或[從 Symantec PKI Manager Web 服務發行 PKCS 憑證](certificates-symantec-configure.md)。

[NavigateIntune]: ./media/certificates-pfx-configure-profile-new.png "在 Azure 入口網站中瀏覽至 Intune 並建立受信任憑證的新設定檔"
[ProfileSettings]: ./media/certificates-pfx-configure-profile-fill.png "建立設定檔並上傳受信任的憑證"
[ConnectorDownload]: ./media/certificates-download-connector.png "從 Azure 入口網站下載憑證連接器"  

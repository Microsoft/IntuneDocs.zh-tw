---
title: 在 Microsoft Intune 中使用私密和公開金鑰憑證 - Azure | Microsoft Docs
description: 使用 Microsoft Intune 新增或建立公開金鑰加密標準 (PKCS) 憑證，包括匯出根憑證、設定憑證範本、下載並安裝 Intune 憑證連接器 (NDES)、建立裝置組態設定檔、以及在 Azure 與您的憑證授權單位中建立 PKCS 憑證設定檔等步驟。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 08/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 25beef7e6593865b92e349163768ded5ce3b9e2d
ms.sourcegitcommit: 5bb46d3c0bf8c5595132c4200849b1c4bcfe7cdb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2019
ms.locfileid: "70376943"
---
# <a name="configure-and-use-pkcs-certificates-with-intune"></a>透過 Intune 設定並使用 PKCS 憑證

Intune 支援使用私密和公開金鑰組 (PKCS) 憑證。 本文可協助您設定必要的基礎結構 (例如，內部部署憑證連接器)，匯出 PKCS 憑證，然後將憑證新增至 Intune 裝置組態設定檔。

Microsoft Intune 中包含的內建設定，可使用 PKCS 憑證對您的組織資源進行存取和驗證。 憑證會驗證並保護您的公司資源存取，例如 VPN 或 WiFi 網路。 您可以使用 Intune 中的裝置組態設定檔，將這些設定部署到裝置。


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

  針對每個租用戶，Intune 支援此連接器最多 100 個執行個體，每個執行個體都位於個別的 Windows 伺服器上。 您可以在與 Microsoft Intune 的 PFX 憑證連接器執行個體相同的伺服器上，安裝此連接器的執行個體。 當您使用多個連接器時，連接器基礎結構支援高可用性與負載平衡，因為任何可用的連接器執行個體都可以處理您的 PKCS 憑證要求。 

  此連接器會處理用於驗證或 S/MIME 電子郵件簽署的 PKCS 憑證要求。

  Microsoft Intune 憑證連接器也支援聯邦資訊處理標準 (FIPS) 模式。 FIPS 並非必要，但啟用時可發出及撤銷憑證。

- **適用於 Microsoft Intune 的 PFX 憑證連接器**：  
  如果您打算使用 S/MIME 電子郵件加密，請使用 Intune 入口網站來下載用於「匯入 PFX 憑證」  的連接器。  移至 [裝置設定]   > [憑證連接器]   > [新增]  ，並遵循「安裝匯入 PFX 憑證連接器的步驟」  。 使用入口網站中的下載連結，開始下載安裝程式 **PfxCertificateConnectorBootstrapper.exe**。 

  每個 Intune 租用戶都支援此連接器的單一執行個體。 您可在相同的伺服器上安裝此連接器，作為 Microsoft Intune 憑證連接器的執行個體。

  此連接器會處理對 Intune 中所匯入之 PFX 檔案的要求，為特定使用者進行 S/MIME 電子郵件加密。  

  當新版本可供使用時，此連接器會自動自行更新。 若要使用更新功能，您必須：
  - 在伺服器上安裝適用於 Microsoft Intune 的匯入 PFX 憑證連接器。  
  - 若要自動接收重要更新，請確定防火牆已開啟，可讓連接器在連接埠 **443** 上連絡 **autoupdate.msappproxy.net**。   

  如需連接器必須能夠存取之所有網路端點的詳細資訊，請參閱 [Microsoft Intune 憑證連接器](intune-endpoints.md)。

- **Windows Server**：  
  您可以使用 Windows Server 來裝載：

  - Microsoft Intune 憑證連接器，用於驗證和 S/MIME 電子郵件簽署情況
  - 適用於 Microsoft Intune 的 PFX 憑證連接器，用於 S/MIME 電子郵件加密情況。

  您可在相同的伺服器上安裝這兩種連接器 (「Microsoft Intune 憑證連接器」  和「PFX 憑證連接器」  )。

## <a name="export-the-root-certificate-from-the-enterprise-ca"></a>從企業 CA 匯出根憑證

若要向 VPN、WiFi 或其他資源驗證裝置，裝置需要有根憑證或中繼 CA 憑證。 下列步驟說明如何從您的企業 CA 取得所需的憑證。

**使用命令列**：  
1. 使用系統管理員帳戶登入根憑證授權單位伺服器。
 
2. 移至 [開始]   > [執行]  ，然後輸入 **Cmd** 來開啟命令提示字元。 
    
3. 指定 **certutil -ca.cert ca_name.cer**，將根憑證匯出為名為 *ca_name.cer* 的檔案。



## <a name="configure-certificate-templates-on-the-ca"></a>設定 CA 上的憑證範本

1. 使用具有系統管理權限的帳戶登入您的企業 CA。
2. 開啟 [憑證授權單位]  主控台、以滑鼠右鍵按一下 [憑證範本]  ，然後選取 [管理]  。
3. 找出 [使用者]  憑證範本、以滑鼠右鍵按一下它，然後選擇 [複製範本]  。 [新範本的內容]  隨即開啟。

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
    > 若為 iOS 憑證範本，請移至 [延伸模組]  索引標籤、更新 [金鑰使用方法]  ，並確認未選取 [簽章是原件證明]  。

10. 在 [安全性]  中，新增您安裝 Microsoft Intune 憑證連接器之伺服器的電腦帳戶。 允許此帳戶的 [讀取]  和 [註冊]  權限。
11. 選取 [套用]   > [確定]  ，儲存憑證範本。 關閉 [憑證範本主控台]  。
12. 在 [憑證授權單位]  主控台中，以滑鼠右鍵按一下 [憑證範本]   > [新增]   > [要發出的憑證範本]  。 選擇您在前述步驟中建立的範本。 選取 [確定]  。
13. 若要讓伺服器為已註冊的裝置及使用者管理憑證，請使用下列步驟：

    1. 以滑鼠右鍵按一下憑證授權單位，選擇 [內容]  。
    2. 在 [安全性] 索引標籤上，新增您執行連接器 (**Microsoft Intune 憑證連接器**或**適用於 Microsoft Intune 的 PFX 憑證連接器**) 之伺服器的電腦帳戶。 
    3. 將 [發行及管理憑證]  和 [要求憑證]  的「允許」權限授與該電腦帳戶。

14. 登出企業 CA。

## <a name="download-install-and-configure-the-certificate-connectors"></a>下載、安裝和設定憑證連接器

### <a name="microsoft-intune-certificate-connector"></a>Microsoft Intune Certificate Connec設為 [https]r

> [!IMPORTANT]  
> Microsoft Intune 憑證連接器無法安裝在發行憑證授權單位 (CA) 上，而必須安裝在不同的 Windows 伺服器上。  

1. 登入 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
2. 選取 [裝置設定]   > [憑證連接器]   > [新增]  。
3. 下載連接器檔案，並將其儲存到要安裝連接器之伺服器所能存取的位置。

    ![Microsoft Intune 憑證連接器下載](media/certificates-pfx-configure/download-ndes-connector.png)
 

4. 下載完成後，請登入伺服器。 然後：

    1. 確定已安裝 .NET 4.5 Framework 或更高版本，這是 NDES 憑證連接器的必要項目。 Windows Server 2012 R2 及更新版本會自動隨附 .NET 4.5 Framework。
    2. 執行安裝程式 (NDESConnectorSetup.exe)，並接受預設位置。 它會將連接器安裝到 `\Program Files\Microsoft Intune\NDESConnectorUI`。 在 [安裝程式選項] 中，選取 [PFX 發佈]  。 繼續並完成安裝。
    3. 連接器服務預設會以本機系統帳戶執行。 如果需要有 Proxy 才能存取網際網路，請確認本機服務帳戶可以存取伺服器上的 Proxy 設定。

5. Microsoft Intune 憑證連接器會開啟 [註冊]  索引標籤。若要連線到 Intune，請**登入**並輸入具有全域系統管理權限的帳戶。
6. 在 [進階]  索引標籤上，建議保持選取 [使用此電腦的 SYSTEM 帳戶 (預設)]  。
7. [套用]   > [關閉] 
8. 返回 Intune 入口網站 ([Intune]   > [裝置設定]   > [憑證連接器]  )。 在幾分鐘後會顯示綠色的核取記號，且 [連線狀態]  為 [使用中]  。 連接器伺服器現在可以與 Intune 通訊。
9. 如果在您的網路環境中有 Web Proxy，您可能需要其他設定才能讓連接器運作。 如需詳細資訊，請參閱 Azure Active Directory 文件中的[使用現有的內部部署 Proxy 伺服器](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy-configure-connectors-with-proxy-servers)。

> [!NOTE]  
> Microsoft Intune 憑證連接器支援 TLS 1.2。 如果裝載連接器的伺服器上安裝了 TLS 1.2，連接器就會使用 TLS 1.2。 否則，會使用 TLS 1.1。 目前，使用 TLS 1.1 在裝置與伺服器之間進行驗證。

### <a name="pfx-certificate-connector-for-microsoft-intune"></a>適用於 Microsoft Intune 的 PFX 憑證連接器

1. 登入 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
2. 選取 [裝置設定]   > [憑證連接器]   > [新增] 
3. 下載並儲存適用於 Microsoft Intune 的 PFX 憑證連接器。 請將它儲存到可從將安裝連接器的伺服器存取的位置。
4. 下載完成後，請登入伺服器。 然後：

    1. 確定已安裝 .NET 4.6 Framework 或更高版本，這是適用於 Microsoft Intune 之 PFX 憑證連接器的必要項目。 如果未安裝 .NET 4.6 Framework，安裝程式就會自動安裝它。
    2. 執行安裝程式 (PfxCertificateConnectorBootstrapper.exe)，並接受預設位置，這會將連接器安裝到 `Program Files\Microsoft Intune\PFXCertificateConnector`。
    3. 連接器服務會以本機系統帳戶執行。 如果網際網路存取需要 Proxy，則請確認本機服務帳戶可以存取伺服器上的 Proxy 設定。

5. 適用於 Microsoft Intune 的 PFX 憑證連接器隨即會在安裝之後開啟 [註冊]  索引標籤。 若要啟用 Intune 的連線，請 [登入]  ，並輸入具有 Azure 全域管理員或 Intune 系統管理員權限的帳戶。
6. 關閉視窗。
7. 返回 Azure 入口網站 ([Intune]   > [裝置設定]   > [憑證連接器]  )。 在幾分鐘後會顯示綠色的核取記號，且 [連線狀態]  為 [使用中]  。 連接器伺服器現在可以與 Intune 通訊。

## <a name="create-a-trusted-certificate-profile"></a>建立受信任的憑證設定檔

1. 在 [Azure 入口網站](https://portal.azure.com)，移至 [Intune]   > [裝置設定]   > [設定檔]   > [建立設定檔]  。
    ![巡覽至 Intune 並建立受信任憑證的新設定檔](media/certificates-pfx-configure/certificates-pfx-configure-profile-new.png)

2. 輸入下列內容：

    - 設定檔的 [名稱] 
    - 可選擇性地設定說明
    - 要部署設定檔的目標 [平台] 
    - 將 [設定檔類型]  設為 [信任的憑證] 

3. 移至 [設定]  ，並輸入先前匯出的根 CA 憑證 .cer 檔案。

   > [!NOTE]
   > 視您在**步驟 2** 中選擇的平台而定，您可能會有選擇憑證 [目的地存放區]  的選項。

   ![建立設定檔並上傳受信任的憑證](media/certificates-pfx-configure/certificates-pfx-configure-profile-fill.png) 

4. 選取 [確定]   > [建立]  儲存您的設定檔。
5. 若要將新的設定檔指派給一或多部裝置，請參閱[指派 Microsoft Intune 裝置設定檔](device-profile-assign.md)。

## <a name="create-a-pkcs-certificate-profile"></a>建立 PKCS 憑證設定檔

1. 在 [Azure 入口網站](https://portal.azure.com)，移至 [Intune]   > [裝置設定]   > [設定檔]   > [建立設定檔]  。
2. 輸入下列內容：

    - 設定檔的 [名稱] 
    - 可選擇性地設定說明
    - 要部署設定檔的目標 [平台] 
    - 將 [設定檔類型]  設為 [PKCS 憑證] 

3. 移至 [設定]  索引標籤，然後輸入下列內容：

    - **更新閾值 (%)** ：建議為 20%。
    - **憑證有效期間**：如果您沒有變更憑證範本，此選項可設定為一年。
    - **金鑰儲存提供者 (KSP)** ：針對 Windows，選取要在裝置上儲存金鑰的位置。
    - **憑證授權單位**：顯示您企業 CA 的內部完整網域名稱 (FQDN)。
    - **憑證授權單位名稱**：列出您企業 CA 的名稱，例如 "Contoso Certification Authority"。
    - **憑證範本名稱**：稍早建立之範本的名稱。 請記住，[範本名稱]  預設會與 [範本顯示名稱]  相同，但*沒有空格*。
    - **主體名稱格式**：除非另有需要，否則請將此選項設定為 [一般名稱]  。
    - **主體別名**：除非另有需要，否則請將此選項設定為 [使用者主體名稱 (UPN)]  。

4. 選取 [確定]   > [建立]  儲存您的設定檔。
5. 若要將新的設定檔指派給一或多部裝置，請參閱[指派 Microsoft Intune 裝置設定檔](device-profile-assign.md)。

   > [!NOTE]
   > 在具有 Android 企業設定檔的裝置上，使用 PKCS 憑證設定檔安裝的憑證不會顯示在裝置上。 若要確認憑證部署成功，請在 Intune 主控台中檢查設定檔的狀態。

## <a name="create-a-pkcs-imported-certificate-profile"></a>建立 PKCS 匯入憑證設定檔

您可以將先前從任何 CA 核發給特定使用者的憑證匯入至 Intune。 匯入的憑證會安裝在使用者註冊的每部裝置上。 S/MIME 電子郵件加密是將現有 PFX 憑證匯入至 Intune 的最常見情況。 使用者可能有許多憑證來加密電子郵件。 這些憑證的私密金鑰必須存在於所有使用者的裝置上，因此它們可以解密先前加密的電子郵件。

若要將憑證匯入至 Intune，您可以使用 [GitHub 上提供的 PowerShell Cmdlet](https://github.com/Microsoft/Intune-Resource-Access)。

將憑證匯入至 Intune 之後，請建立 **PKCS 匯入憑證**設定檔，並將它指派給 Azure Active Directory 群組。

1. 在 [Azure 入口網站](https://portal.azure.com)，移至 [Intune]   > [裝置設定]   > [設定檔]   > [建立設定檔]  。
2. 輸入下列內容：

    - 設定檔的 [名稱] 
    - 可選擇性地設定說明
    - 要部署設定檔的目標 [平台] 
    - 將 [設定檔類型]  設定為 [PKCS 匯入憑證] 

3. 移至 [設定]  索引標籤，然後輸入下列內容：

    - **使用目的**：針對此設定檔匯入之憑證的使用目的。 系統管理員可能已匯入使用目的不同 (例如驗證、S/MIME 簽署或 S/MIME 加密) 的憑證。 憑證設定檔中選取的使用目的符合含有正確匯入憑證的憑證設定檔。
    - **憑證有效期間**：如果您沒有變更憑證範本，此選項可設定為一年。
    - **金鑰儲存提供者 (KSP)** ：針對 Windows，選取要在裝置上儲存金鑰的位置。

4. 選取 [確定]   > [建立]  儲存您的設定檔。
5. 若要將新的設定檔指派給一或多部裝置，請參閱[指派 Microsoft Intune 裝置設定檔](device-profile-assign.md)。

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

設定檔已建立，但還不會執行任何動作。 接下來，[指派設定檔](device-profile-assign.md)並[監視其狀態](device-profile-monitor.md)。

[使用 SCEP 憑證](certificates-scep-configure.md)，或[從 Symantec PKI Manager Web 服務發行 PKCS 憑證](certificates-symantec-configure.md)。


---
title: 透過 Microsoft Intune - Azure 使用 PKCS 憑證 | Microsoft Docs
description: 使用 Microsoft Intune 新增或建立公用金鑰密碼編譯標準憑證，包括匯出根憑證、設定憑證範本、下載並安裝 Microsoft Intune 憑證連接器 (NDES)、建立裝置組態設定檔、在 Azure 與您的憑證授權單位建立 PKCS 憑證設定檔等步驟。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 06/20/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 3b3bfe76173eff76a3175952bef5c6e23ad5e429
ms.sourcegitcommit: afda8a0fc0f615e976b18ddddf81d56d7ae3566e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/20/2018
ms.locfileid: "36271536"
---
# <a name="configure-and-use-pkcs-certificates-with-intune"></a>透過 Intune 設定並使用 PKCS 憑證

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

憑證用來驗證並保護您的公司資源存取，例如 VPN 或 WiFi 網路。 本文將說明如何匯出 PKCS 憑證，然後將憑證新增至 Intune 設定檔。 

## <a name="requirements"></a>需求

若要透過 Intune 使用 PKCS 憑證，您必須具備下列基礎結構：

- **Active Directory 網域**：本節所列的所有伺服器均須加入 Active Directory 網域。

  如需安裝和設定 AD DS 的詳細資訊，請參閱 [AD DS 設計與規劃](https://docs.microsoft.com/windows-server/identity/ad-ds/plan/ad-ds-design-and-planning)。

- **憑證授權單位** (CA)：企業憑證授權單位 (CA)

  如需安裝和設定 Active Directory 憑證服務 (AD CS) 的詳細資訊，請參閱 [Active Directory 憑證服務逐步指南](https://technet.microsoft.com/library/cc772393)。

  > [!WARNING]
  > Intune 需要您搭配企業憑證授權單位 (CA) 執行 AD CS，而非獨立 CA。

- **用戶端**：連線到企業 CA

- **根憑證**：從您的企業 CA 匯出的根憑證複本

- **Microsoft Intune 憑證連接器**：使用 Azure 入口網站來下載**憑證連接器**安裝程式 (**NDESConnectorSetup.exe**)。 

  NDES 憑證連接器也支援聯邦資訊處理標準 (FIPS) 模式。 FIPS 並非必要，但啟用時可發出及撤銷憑證。

- **Windows Server**：裝載 Microsoft Intune 憑證連接器 (NDESConnectorSetup.exe)

## <a name="export-the-root-certificate-from-the-enterprise-ca"></a>從企業 CA 匯出根憑證

若要向 VPN、WiFi 和其他資源進行驗證，在每部裝置上都需要根憑證或中繼 CA 憑證。 下列步驟說明如何從您的企業 CA 取得所需的憑證。

1. 使用具有系統管理權限的帳戶登入您的企業 CA。
2. 以系統管理員身分開啟命令提示字元。
3. 將根 CA 憑證 (.cer) 匯出到您稍後可以加以存取的位置。

   例如：

4. 在精靈完成後，但在關閉精靈之前，按一下 [啟動 Certificate Connector UI] 。

   `certutil -ca.cert certnew.cer`

   如需詳細資訊，請參閱[管理憑證的 Certutil 工作](https://technet.microsoft.com/library/cc772898.aspx#BKMK_ret_sign)。

## <a name="configure-certificate-templates-on-the-certification-authority"></a>設定憑證授權單位上的憑證範本

1. 使用具有系統管理權限的帳戶登入您的企業 CA。
2. 開啟 [憑證授權單位] 主控台、以滑鼠右鍵按一下 [憑證範本]，然後選取 [管理]。
3. 找出 [使用者] 憑證範本、以滑鼠右鍵按一下它，然後選擇 [複製範本]。 [新範本的內容] 隨即開啟。
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
11. 依序選取 [套用]和 [確定]，儲存憑證範本。
12. 關閉 [憑證範本主控台] 。
13. 從 [憑證授權單位] 主控台，以滑鼠右鍵按一下 [憑證範本]，[新增]，[要發出的憑證範本]。 選擇您在前述步驟中建立的範本，然後選取 [確定]。
14. 若要讓伺服器代表已在 Intune 註冊的裝置及使用者來管理憑證，請遵循這些步驟：

    1. 以滑鼠右鍵按一下憑證授權單位，選擇 [內容]。
    2. 在 [安全性] 索引標籤上，新增您執行 Microsoft Intune 憑證連接器之伺服器的電腦帳戶。 將 [發行及管理憑證] 和 [要求憑證] 的「允許」權限授與該電腦帳戶。

15. 登出企業 CA。

## <a name="download-install-and-configure-the-certificate-connector"></a>下載、安裝及設定憑證連接器

![ConnectorDownload][ConnectorDownload]

1. 登入 [Azure 入口網站](https://portal.azure.com)。
2. 選取 [All services] (所有服務)，篩選 [Intune]，然後選取 [Microsoft Intune]。
3. 選取 [裝置設定] [憑證授權單位]。
4. 選取 [新增] 和 [下載連接器檔案]。 將下載項目儲存到要安裝下載項目的伺服器所能存取的位置。
5. 下載完成後，請登入伺服器。 然後：

    1. 確定已安裝 .NET 4.5 Framework，這對 NDES 憑證連接器是必要的。 Windows Server 2012 R2 及更新版本會自動隨附 .NET 4.5 Framework。
    2. 執行安裝程式 (NDESConnectorSetup.exe)，並接受預設位置。 它會將連接器安裝到 `\Program Files\Microsoft Intune\NDESConnectorUI\NDESConnectorUI.exe`。 在 [安裝程式選項] 中，選取 [PFX 發佈]。 繼續並完成安裝。

6. [NDES 連接器] 會開啟 [註冊] 索引標籤。若要連線到 Intune，請**登入**並輸入具有全域系統管理權限的帳戶。
7. 在 [進階] 索引標籤上，保持選取 [使用此電腦的 SYSTEM 帳戶 (預設)]。
8. 按一下 [套用]，然後按一下 [關閉]。
9. 返回 Azure 入口網站 ([Intune] > [裝置設定] > [憑證授權單位])。 在幾分鐘後會顯示綠色的核取記號，且 [連線狀態] 為 [使用中]。 連接器伺服器現在可以與 Intune 通訊。

> [!NOTE]
> NDES 憑證連接器隨附 TLS 1.2 支援。 因此，如果安裝 NDES 憑證連接器的伺服器支援 TLS 1.2，則會使用 TLS 1.2。 如果伺服器不支援 TLS 1.2，則會使用 TLS 1.1。 目前，使用 TLS 1.1 在裝置與伺服器之間進行驗證。

## <a name="create-a-device-configuration-profile"></a>建立裝置組態設定檔

1. 登入 [Azure 入口網站](https://portal.azure.com)。
2. 移至 [Intune] > [裝置設定] > [設定檔] > [建立設定檔]。

   ![NavigateIntune][NavigateIntune]

3. 輸入下列內容：

  - 設定檔的 [名稱]
  - 可選擇性地設定說明
  - 要部署設定檔的目標 [平台]
  - 將 [設定檔類型] 設為 [信任的憑證]

4. 移至 [設定]，並輸入先前匯出的根 CA 憑證 .cer 檔案。

   > [!NOTE]
   > 視您在**步驟 3** 中選擇的平台而定，您可能會有選擇憑證 [目的地存放區] 的選項。

   ![ProfileSettings][ProfileSettings]

5. 選取 [確定]，然後選取 [建立] 以儲存您的設定檔。
6. 若要將新的設定檔指派給一或多部裝置，請參閱[指派 Microsoft Intune 裝置設定檔](device-profile-assign.md)。

## <a name="create-a-pkcs-certificate-profile"></a>建立 PKCS 憑證設定檔

1. 登入 [Azure 入口網站](https://portal.azure.com)。
2. 移至 [Intune] > [裝置設定] > [設定檔] > [建立設定檔]。
3. 輸入下列內容：

  - 設定檔的 [名稱]
  - 可選擇性地設定說明
  - 要部署設定檔的目標 [平台]
  - 將 [設定檔類型] 設為 [PKCS 憑證]

4. 移至 [設定] 索引標籤，然後輸入下列內容：

  - **更新閾值 (%)**：建議為 20%。
  - **憑證有效期間** - 如果您沒有變更憑證範本，此選項可設定為一年。
  - **憑證授權單位** - 顯示您企業 CA 的內部完整網域名稱 (FQDN)。
  - **憑證授權單位名稱** - 列出您企業 CA 的名稱，且可能與前一項目不同。
  - **憑證範本名稱** - 稍早建立之範本的名稱。 請記住，[範本名稱] 預設會與 [範本顯示名稱] 相同，但*沒有空格*。
  - **主體名稱格式**：除非另有需要，否則請將此選項設為 [一般名稱]。
  - **主體替代名稱**：除非另有需要，否則請將此選項設為 [使用者主體名稱 (UPN)]。
  - **擴充金鑰使用方法** - 只要您在[憑證授權單位上的憑證範本](#configure-certificate-templates-on-the-certification-authority)一節 (在本文中) 的步驟 10 中使用預設的設定，請從選項新增下列 [預先定義的值]：
    - **任何目的**
    - **用戶端驗證**
    - **安全電子郵件**
  - **根憑證**(針對 Android 設定檔) 列出在[從企業 CA 匯出根憑證](#export-the-root-certificate-from-the-enterprise-ca)一節 (在本文中) 的步驟 3 中所匯出的 .cer 檔案。

5. 選取 [確定]，然後選取 [建立] 以儲存您的設定檔。
6. 若要將新的設定檔指派給一或多部裝置，請參閱[指派 Microsoft Intune 裝置設定檔](device-profile-assign.md)。

## <a name="next-steps"></a>接下來的步驟
[使用 SCEP 憑證](certificates-scep-configure.md)，或[從 Symantec PKI Manager Web 服務發行 PKCS 憑證](certificates-symantec-configure.md)。

[NavigateIntune]: ./media/certificates-pfx-configure-profile-new.png "在 Azure 入口網站中瀏覽至 Intune 並建立受信任憑證的新設定檔"
[ProfileSettings]: ./media/certificates-pfx-configure-profile-fill.png "建立設定檔並上傳受信任的憑證"
[ConnectorDownload]: ./media/certificates-download-connector.png "從 Azure 入口網站下載憑證連接器"  

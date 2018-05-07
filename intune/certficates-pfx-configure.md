---
title: 透過 Microsoft Intune - Azure 使用 PKCS 憑證 | Microsoft Docs
description: 使用 Microsoft Intune 新增或建立公用金鑰密碼編譯標準憑證，包括匯出根憑證、設定憑證範本、下載並安裝 Microsoft Intune Certificate Connector、建立裝置組態設定檔、在 Azure 與您的憑證授權單位建立 PKCS 憑證設定檔等步驟
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/05/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 61a190be2b4685030438988dab0d0134a8fa9f9b
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="configure-and-use-pkcs-certificates-with-intune"></a>透過 Intune 設定並使用 PKCS 憑證

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

憑證用來驗證並保護您的公司資源存取，例如 VPN 或 WiFi 網路。 本文將說明如何匯出 PKCS 憑證，然後將憑證新增至 Intune 設定檔。 

## <a name="requirements"></a>需求

若要透過 Intune 使用 PKCS 憑證，您必須具備下列基礎結構：

* 已設定的現有 Active Directory Domain Services (AD DS) 網域。
 
  如需安裝和設定 AD DS 的詳細資訊，請參閱 [AD DS 設計與規劃](https://docs.microsoft.com/windows-server/identity/ad-ds/plan/ad-ds-design-and-planning)。

* 已設定的現有企業憑證授權單位 (CA)。

  如需安裝和設定 Active Directory 憑證服務 (AD CS) 的詳細資訊，請參閱 [Active Directory 憑證服務逐步指南](https://technet.microsoft.com/library/cc772393)。

  > [!WARNING]
  > Intune 需要您搭配企業憑證授權單位 (CA) 執行 AD CS，而非獨立 CA。

* 具有連線至企業 CA 之能力的用戶端。
* 從您的企業 CA 匯出的根憑證複本。
* 從您的 Intune 入口網站下載的 Microsoft Intune 憑證連接器 (NDESConnectorSetup.exe)。
* 裝載 Microsoft Intune 憑證連接器 (NDESConnectorSetup.exe) 的 Windows 伺服器。

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
   * 將 [憑證授權單位] 設為 [Windows Server 2008 R2]
   * 將 [憑證接收者] 設為 [Windows 7 / Server 2008 R2]
5. 在 [一般] 索引標籤上：
   * 將 [範本顯示名稱] 設為對您有意義的名稱。

   > [!WARNING]
   > [範本名稱] 預設會與 [範本顯示名稱] 相同，但*沒有空格*。 請記下範本名稱，您之後會需要它。

6. 在 [要求處理] 索引標籤中，選取 [允許匯出私密金鑰]。
7. 在 [密碼編譯] 中，確認 [最小金鑰大小] 已設為 2048。
8. 在 [主體名稱] 中，選擇 [在要求中提供]。
9. 在 [延伸模組] 中，確認您在 [應用程式原則] 下看到「加密檔案系統」、「安全電子郵件」和「用戶端驗證」。
    
      > [!IMPORTANT]
      > 若為 iOS 憑證範本，請移至 [延伸模組] 索引標籤、更新 [金鑰使用方法]，並確認未選取 [簽章是原件證明]。

10. 在 [安全性] 中，新增您安裝 Microsoft Intune 憑證連接器之伺服器的電腦帳戶。
    * 允許此帳戶的 [讀取] 和 [註冊] 權限。
11. 依序選取 [套用]和 [確定]，儲存憑證範本。
12. 關閉 [憑證範本主控台] 。
13. 從 [憑證授權單位] 主控台，以滑鼠右鍵按一下 [憑證範本]，[新增]，[要發出的憑證範本]。
    * 選擇您在前述步驟中建立的範本，然後選取 [確定]。
14. 若要讓伺服器代表已在 Intune 註冊的裝置及使用者來管理憑證，請遵循這些步驟：

    a. 以滑鼠右鍵按一下憑證授權單位，選擇 [內容]。

    b. 在 [安全性] 索引標籤上，新增您執行 Microsoft Intune 憑證連接器之伺服器的電腦帳戶。
      * 將 [發行及管理憑證] 和 [要求憑證] 的「允許」權限授與該電腦帳戶。
15. 登出企業 CA。

## <a name="download-install-and-configure-the-microsoft-intune-certificate-connector"></a>下載、安裝和設定 Microsoft Intune 憑證連接器

![ConnectorDownload][ConnectorDownload]

1. 在 [Azure 入口網站](https://portal.azure.com)中，選取 [All services] (所有服務)，並篩選 **Intune**。 依序選取 [Microsoft Intune] 和 [裝置設定]。 
2. 依序選取 [憑證授權單位] 和 [新增]，然後選取 [下載連接器檔案]。 將下載項目儲存到可從將安裝它之伺服器存取的位置。 
3. 登入這部伺服器，並執行安裝程式： 

    1. 接受預設位置。 它會將連接器安裝到 `\Program Files\Microsoft Intune\NDESConnectorUI\NDESConnectorUI.exe`。
    2. 在 [安裝程式選項] 中，選取 [PFX 散發]，然後選取 [下一步]。
    3. 按一下 [安裝]，然後等候安裝完成。
    4. 完成之後，核取 [啟動 Intune 連接器]，然後按一下 [完成]。

4. [NDES 連接器] 視窗應該會開啟至 [註冊] 索引標籤。若要連線到 Intune，請選取 [登入] 並輸入具有全域系統管理權限的帳戶。
5. 在 [進階] 索引標籤上，保持選取 [使用此電腦的 SYSTEM 帳戶 (預設)]。
6. 按一下 [套用]，然後按一下 [關閉]。
7. 返回 Azure 入口網站 ([Intune] > [裝置設定] > [憑證授權單位])。 在幾分鐘後會顯示綠色的核取記號，而 [連線狀態] 為 [使用中]。 連接器伺服器現在可以與 Intune 通訊。

## <a name="create-a-device-configuration-profile"></a>建立裝置組態設定檔

1. 登入 [Azure 入口網站](https://portal.azure.com)。
2. 移至 [Intune]、[裝置設定]、[設定檔]，然後選取 [建立設定檔]。

   ![NavigateIntune][NavigateIntune]

3. 輸入下列內容：
   * 設定檔的 [名稱]
   * 可選擇性地設定說明
   * 要部署設定檔的目標 [平台]
   * 將 [設定檔類型] 設為 [信任的憑證]

4. 移至 [設定]，並輸入先前匯出的根 CA 憑證 .cer 檔案。

   > [!NOTE]
   > 視您在**步驟 3** 中選擇的平台而定，您可能會有選擇憑證 [目的地存放區] 的選項。

   ![ProfileSettings][ProfileSettings]

5. 選取 [確定]，然後選取 [建立] 以儲存您的設定檔。
6. 若要將新的設定檔指派給一或多部裝置，請參閱[如何指派 Microsoft Intune 裝置設定檔](device-profile-assign.md)。

## <a name="create-a-pkcs-certificate-profile"></a>建立 PKCS 憑證設定檔

1. 登入 [Azure 入口網站](https://portal.azure.com)。
2. 移至 [Intune]、[裝置設定]、[設定檔]，然後選取 [建立設定檔]。
3. 輸入下列內容：
   * 設定檔的 [名稱]
   * 可選擇性地設定說明
   * 要部署設定檔的目標 [平台]
   * 將 [設定檔類型] 設為 [PKCS 憑證]
4. 移至 [設定] 索引標籤，然後輸入下列內容：
   * **更新閾值 (%)**：建議為 20%。
   * **憑證有效期間** - 如果您沒有變更憑證範本，此選項可設定為一年。
   * **憑證授權單位** - 顯示您企業 CA 的內部完整網域名稱 (FQDN)。
   * **憑證授權單位名稱** - 列出您企業 CA 的名稱，且可能與前一項目不同。
   * **憑證範本名稱** - 稍早建立之範本的名稱。 請記住，[範本名稱] 預設會與 [範本顯示名稱] 相同，但*沒有空格*。
   * **主體名稱格式**：除非另有需要，否則請將此選項設為 [一般名稱]。
   * **主體替代名稱**：除非另有需要，否則請將此選項設為 [使用者主體名稱 (UPN)]。
   * **擴充金鑰使用方法** - 只要您在[憑證授權單位上的憑證範本](#configure-certificate-templates-on-the-certification-authority)一節 (在本文中) 的步驟 10 中使用預設的設定，請從選項新增下列 [預先定義的值]：
      * **任何目的**
      * **用戶端驗證**
      * **安全電子郵件**
   * **根憑證**(針對 Android 設定檔) 列出在[從企業 CA 匯出根憑證](#export-the-root-certificate-from-the-enterprise-ca)一節 (在本文中) 的步驟 3 中所匯出的 .cer 檔案。

5. 選取 [確定]，然後選取 [建立] 以儲存您的設定檔。
6. 若要將新的設定檔指派給一或多個裝置，請參閱[如何指派 Microsoft Intune 裝置設定檔](device-profile-assign.md)一文。


[NavigateIntune]: ./media/certificates-pfx-configure-profile-new.png "在 Azure 入口網站中瀏覽至 Intune 並建立受信任憑證的新設定檔"
[ProfileSettings]: ./media/certificates-pfx-configure-profile-fill.png "建立設定檔並上傳受信任的憑證"
[ConnectorDownload]: ./media/certificates-download-connector.png "從 Azure 入口網站下載憑證連接器"  

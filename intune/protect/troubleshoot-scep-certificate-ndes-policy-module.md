---
title: 針對 Microsoft Intune 憑證連接器原則模組進行疑難排解 | Microsoft Docs
description: 當您使用 SCEP 憑證設定檔搭配 Intune 部署憑證時，當模組處理憑證要求時，針對 NDES 原則模組的操作進行疑難排解。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/30/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: be53f6102226b004cab2bd953357e8c360a00f67
ms.sourcegitcommit: c46b0c2d4507be6a2786a4ea06009b2d5aafef85
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/01/2020
ms.locfileid: "76915833"
---
# <a name="troubleshoot-the-ndes-policy-module-in-microsoft-intune"></a>在 Microsoft Intune 中針對 NDES 原則模組進行疑難排解

此文章中的資訊可協助您驗證隨 Microsoft Intune 憑證連接器安裝之網路裝置註冊服務 (NDES) 原則模組的操作。 當 NDES 收到憑證要求時，它會將要求轉送至原則模組，而原則模組會驗證對裝置而言有效的要求。 驗證之後，NDES 會連絡憑證授權單位 (CA)，以代表裝置要求憑證。

此文章同時適用於 [SCEP 通訊工作流程](troubleshoot-scep-certificate-profiles.md)的步驟 3 與步驟 4。

## <a name="ndes-communication-to-the-policy-module"></a>與原則模組的 NDES 通訊

從裝置接收憑證要求之後，NDES 會透過隨 Microsoft Intune 憑證連接器安裝的原則模組，向 Intune 驗證該要求。 這些項目會參考憑證登錄點  。

**指出成功的記錄項目**：

若要確認驗證要求已提交至模組，請在 NDES 伺服器上的記錄中尋找類似下列範例的項目：

- **IIS 記錄**：

  ```
  fe80::f53d:89b8:c3e8:5fec%13 POST /CertificateRegistrationSvc/Certificate/VerifyRequest - 443 - 
  fe80::f53d:89b8:c3e8:5fec%13 NDES_Plugin - 201 0 0 341 875
  ```

- **Ndesplugin 記錄**：

  ```
  Calling VerifyRequest ...  
  Sending request to certificate registration point.
  ```

  下列範例表示成功驗證裝置查問要求，且 NDES 現在可以與 CA 聯繫：

  ```
  Verify challenge returns true
  Exiting VerifyRequest with 0x0
  ```

- **CertificateRegistrationPoint.svclog**：

  `Validation Phase 1 finished with status True.`  
  `Validation Phase 3 finished with status True.`  
  `VerifyRequest Finished with status True`


**當成功指示器不存在時**：

如果您找不到這些項目，請從檢閱適用於[裝置到 NDES 伺服器的通訊](troubleshoot-scep-certificate-device-to-ndes.md#troubleshoot-common-errors)的疑難排解指導方針開始。

如果該文章中的資訊無法協助您解決問題，以下是可指出問題的其他項目。

### <a name="ndespluginlog-contains-an-error-12175"></a>NDESPlugin.log 包含錯誤 12175

當記錄包含與下列類項目似的錯誤 12175 時，SSL 憑證可能會發生問題：

```
WINHTTP_CALLBACK_STATUS_FLAG_CERT_CN_INVALID
Failed to send http request /CertificateRegistrationSvc/Certificate/VerifyRequest. Error 12175
```

新式瀏覽器和行動裝置上的瀏覽器會忽略 SSL 憑證上的「一般名稱」  (如果有「主體替代名稱」  存在的話)。

**解決方案**：針對「一般名稱」  與「主體替代名稱」  發行具有下列屬性的 Web 伺服器 SSL 憑證，然後將其繫結至 IIS 中的連接埠 443：

  - **主體名稱**  
    CN = 外部伺服器名稱
  - **主體別名**  
     名稱 = 外部伺服器名稱  
     DNS 名稱 = 內部伺服器名稱

### <a name="ndespluginlog-contains-an-error-403--forbidden-access-is-denied"></a>NDESPlugin.log 包含錯誤 403 – 禁止:拒絕存取」

當下列記錄包含與下列項目類似的錯誤 403 時，用戶端憑證可能不受信任或無效：

**NDESPlugin.log**：

```
Sending request to certificate registration point.
Verify challenge returns <!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd"> <html xmlns="http://www.w3.org/1999/xhtml"> <head><meta http-equiv="Content-Type" content="text/html; charset=iso-8859-1"/>
<title>403 - Forbidden: Access is denied.</title>
```

**IIS 記錄**：

```
POST /CertificateRegistrationSvc/Certificate/VerifyRequest - 443 -<IP_address>
NDES_Plugin - 403 16 2148204809 453  
```

如果 NDES 伺服器的「受信任的根憑證授權單位」憑證存放區中有中繼 CA 憑證，就會發生此問題。

如果憑證擁有相同的「發行給」  與「發行者」  值，則它是根憑證。 否則，它是中繼憑證。

**解決方案**：若要修正此問題，請從「信任的根憑證授權單位」憑證存放區識別並移除中繼 CA 憑證。

### <a name="ndespluginlog-indicates-the-challenge-returns-false"></a>Ndesplugin.log 指出查問傳回 False

當查問的結果傳回 **false** 時，請檢查 *CertificateRegistrationPoint.svclog* 中是否有錯誤。 例如，您可能會看到類似下列項目的「無法取出簽署憑證」錯誤：

```
Signing certificate could not be retrieved. System.Security.Cryptography.CryptographicException: m_safeCertContext is an invalid handle. at System.Security.Cryptography.X509Certificates.X509Certificate.ThrowIfContextInvalid() at System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHashString() at Microsoft.ConfigurationManager.CertRegPoint.CRPCertificate.RetrieveSigningCert(String certThumbprint
```

**解決方案**：在安裝連接器的伺服器上，開啟 [登錄編輯程式]，找出 `HKLM\SOFTWARE\Microsoft\MicrosoftIntune\NDESConnector` 登錄機碼，然後檢查 SigningCertificate 值是否存在。

如果此值不存在，請重新啟動 services.msc 中的 Intune 連接器服務，然後檢查該值是否出現在登錄中。 如果仍然缺少該值，通常是因為 NDES 與 Intune 服務的伺服器之間發生網路連線問題。

## <a name="ndes-passes-the-request-to-issue-the-certificate"></a>NDES 通過發出憑證的要求

憑證登錄點 (原則模組) 成功驗證之後，NDES 會代表裝置將憑證要求傳遞給 CA。

**指出成功的記錄項目**：

- **Ndesplugin 記錄**：

  ```
  Verify challenge returns true
  Exiting VerifyRequest with 0x0
  ```

- **IIS 記錄**：

  ```
  fe80::f53d:89b8:c3e8:5fec%13 GET /certsrv/mscep/mscep.dll/pkiclient.exe ... 80 - 
  fe80::f53d:89b8:c3e8:5fec%13 Mozilla/4.0+(compatible;+Win32;+NDES+client) - 200 0 0 2713 1296
  ```

- **CertificateRegistrationPoint.svclog**：

  `Validation Phase 1 finished with status True.`  
  `Validation Phase 3 finished with status True.`  
  `VerifyRequest Finished with status True`

**當成功指示器不存在時**：

如果您沒有看到指出成功的項目，請遵循下列步驟：

1. 當憑證登錄點驗證查問時，尋找 *CertificateRegistrationPoint.svclog* 中記錄的問題。 在下列幾行之間尋找項目：

   - VerifyRequest 已啟動。
   - VerifyRequest 已完成，狀態為 False

2. 在 CA 上開啟憑證授權單位 MMC，然後選取 [失敗的要求]  以尋找有助於找出問題的錯誤。 下圖為範例：

   ![失敗要求的範例](../protect/media/troubleshoot-scep-certificate-ndes-policy-module/failed-requests.png)

3. 檢閱 CA 上的應用程式事件記錄檔中是否有錯誤。 通常，您會看到與上一個步驟 [失敗的要求]  中看到的錯誤相符的錯誤。 下圖為範例：

   ![檢閱應用程式記錄檔](../protect/media/troubleshoot-scep-certificate-ndes-policy-module/application-log-errors.png)

## <a name="next-steps"></a>後續步驟

如果 NDES 原則模組驗證要求，並將要求轉送到憑證授權單位，下一步就是檢閱[憑證傳遞至裝置](troubleshoot-scep-certificate-delivery.md)。

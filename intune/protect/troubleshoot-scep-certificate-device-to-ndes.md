---
title: 在 Microsoft Intune 中針對受控裝置對 NDES 通訊進行疑難排解 | Microsoft Docs
description: 搭配 Intune 針對使用 SCEP 憑證設定檔來部署憑證時的受控裝置對 NDES 伺服器通訊進行疑難排解。
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
ms.openlocfilehash: 8c81fa9b521b0d950fb69c29f7625981e709863d
ms.sourcegitcommit: c46b0c2d4507be6a2786a4ea06009b2d5aafef85
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/01/2020
ms.locfileid: "76916106"
---
# <a name="troubleshoot-device-to-ndes-server-communication-for-scep-certificate-profiles-in-microsoft-intune"></a>在 Microsoft Intune 中針對 SCEP 憑證設定檔的裝置對 NDES 伺服器通訊進行疑難排解

使用下列資訊來判斷接收並處理 Intune 簡單憑證註冊通訊協定 (SCEP) 憑證設定檔的裝置是否可以順利連絡網路裝置註冊服務 (NDES) 以提出挑戰。 在裝置上，系統會產生私密金鑰，並將憑證簽署要求 (CSR) 和挑戰從裝置傳送到 NDES 伺服器。 為了連絡 NDES 伺服器，裝置會使用來自 SCEP 憑證設定檔的 URI。

此文章會參考 [SCEP 通訊流程概觀](troubleshoot-scep-certificate-profiles.md)的步驟 2。

## <a name="review-iis-logs-for-a-connection-from-the-device"></a>檢閱 IIS 記錄中來自裝置的連線

IIS 記錄針對所有平台皆包含相同類型的項目。


1. 在 NDES 伺服器上開啟最新的 IIS 記錄檔，其可在下列資料夾中找到： *%SystemDrive%\inetpub\logs\logfiles\w3svc1*

2. 搜尋記錄檔以尋找類似下列範例的項目。 這兩個範例皆包含狀態 **200**，其出現在結尾附近：

   `fe80::f53d:89b8:c3e8:5fec%13 GET /certsrv/mscep/mscep.dll/pkiclient.exe operation=GetCACaps&message=default 80 - fe80::f53d:89b8:c3e8:5fec%13 Mozilla/4.0+(compatible;+Win32;+NDES+client) - 200 0 0 186 0.`

   And

   `fe80::f53d:89b8:c3e8:5fec%13 GET /certsrv/mscep/mscep.dll/pkiclient.exe operation=GetCACert&message=default 80 - fe80::f53d:89b8:c3e8:5fec%13 Mozilla/4.0+(compatible;+Win32;+NDES+client) - 200 0 0 3567 0`

3. 當裝置連絡 IIS 時，系統會記錄針對 mscep.dll 的 HTTP GET 要求。

   檢閱此要求結尾附近的狀態碼：
   - **狀態碼為 200**：此狀態表示與 NDES 伺服器的連線成功。
   - **狀態碼為 500**：IIS_IURS 群組可能缺少正確權限。 請參閱此文章稍後的[狀態碼 500](#status-code-500)。
   - 如果狀態碼不是 200 或 500：

     - 請參閱此文章稍後的[測試 SCEP 伺服器 URL](#test-the-scep-server-url) 以協助驗證設定。

     - 請參閱 [IIS 7 和更新版本中的 HTTP 狀態碼](https://support.microsoft.com/help/943891)以取得較不常見錯誤碼的詳細資訊。

   如果系統完全沒有記錄連線，裝置和 NDES 伺服器之間的網路可能已封鎖來自該裝置的連絡。

## <a name="review-device-logs-for-connections-to-ndes"></a>檢閱裝置記錄中針對 NDES 的連線

### <a name="android-devices"></a>Android 裝置

請檢閱[裝置 OMADM 記錄](troubleshoot-scep-certificate-profiles.md#logs-for-android-devices)。 尋找與下列類似的項目，這些項目會在裝置連線至 NDES 時記錄：

```
2018-02-27T05:16:08.2500000  VERB  Event  com.microsoft.omadm.platforms.android.certmgr.CertificateEnrollmentManager  18327    10  There are 1 requests
2018-02-27T05:16:08.2500000  VERB  Event  com.microsoft.omadm.platforms.android.certmgr.CertificateEnrollmentManager  18327    10  Trying to enroll certificate request: ModelName=AC_51bad41f-3854-4eb5-a2f2-0f7a94034ee8%2FLogicalName_39907e78_e61b_4730_b9fa_d44a53e4111c;Hash=1677525787
2018-02-27T05:16:09.5530000  VERB  Event  org.jscep.transport.UrlConnectionGetTransport  18327    10  Sending GetCACaps(ca) to https://<server>.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACaps&message=ca
2018-02-27T05:16:14.6440000  VERB  Event  org.jscep.transport.UrlConnectionGetTransport  18327    10  Received '200 OK' when sending GetCACaps(ca) to https://<server>.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACaps&message=ca
2018-02-27T05:16:21.8220000  VERB  Event  org.jscep.message.PkiMessageEncoder  18327     10 Encoding message: org.jscep.message.PkcsReq@2b06f45f[messageData=org.<server>.pkcs.PKCS10CertificationRequest@699b3cd,messageType=PKCS_REQ,senderNonce=Nonce [D447AE9955E624A56A09D64E2B3AE76E],transId=251E592A777C82996C7CF96F3AAADCF996FC31FF]
2018-02-27T05:16:21.8790000  VERB  Event  org.jscep.message.PkiMessageEncoder  18327     10  Signing pkiMessage using key belonging to [dn=CN=<uesrname>; serial=1]
2018-02-27T05:16:21.9580000  VERB  Event  org.jscep.transaction.EnrollmentTransaction  18327     10  Sending org.<server>.cms.CMSSignedData@ad57775
```

重要項目會包含下列範例文字字串：

- 有 1 個要求
- 傳送 GetCACaps(ca) 至 https://\<server>.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACaps&message=ca 時，接收到 '200 OK'
- 使用屬於 [dn=CN=\<username>; serial=1] 的金鑰來簽署 pkiMessage


該連線也會由 IIS 記錄在 NDES 伺服器的 %SystemDrive%\inetpub\logs\LogFiles\W3SVC1\ 資料夾。 下列為範例：

```
fe80::f53d:89b8:c3e8:5fec%13 GET /certsrv/mscep/mscep.dll operation=GetCACert&message=ca 443 - 
fe80::f53d:89b8:c3e8:5fec%13 Dalvik/2.1.0+(Linux;+U;+Android+5.0;+P01M+Build/LRX21V) - 200 0 0 3909 0
fe80::f53d:89b8:c3e8:5fec%13 GET /certsrv/mscep/mscep.dll operation=GetCACaps&message=ca 443 - 
fe80::f53d:89b8:c3e8:5fec%13 Dalvik/2.1.0+(Linux;+U;+Android+5.0;+P01M+Build/LRX21V) - 200 0 0 421 
```

### <a name="ios-and-ipados-devices"></a>iOS 和 iPadOS 裝置

請檢閱[裝置偵錯記錄](troubleshoot-scep-certificate-profiles.md#logs-for-ios-and-ipados-devices)。 尋找與下列類似的項目，這些項目會在裝置連線至 NDES 時記錄：

```
debug    18:30:53.691033 -0500    profiled    Performing synchronous URL request: https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACert&message=SCEP%20Authority\ 
debug    18:30:54.640644 -0500    profiled    Performing synchronous URL request: https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACaps&message=SCEP%20Authority\ 
default    18:30:55.483977 -0500    profiled    Attempting to retrieve issued certificate...\ 
debug    18:30:55.487798 -0500    profiled    Sending CSR via GET.\  
debug    18:30:55.487908 -0500    profiled    Performing synchronous URL request: https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll?operation=PKIOperation&message=MIAGCSqGSIb3DQEHAqCAMIACAQExDzANBglghkgBZQMEAgMFADCABgkqhkiG9w0BBwGggCSABIIZfzCABgkqhkiG9w0BBwOggDCAAgEAMYIBgjCCAX4CAQAwZjBPMRUwEwYKCZImiZPyLGQBGRYFbG9jYWwxHDAaBgoJkiaJk/IsZAEZFgxmb3VydGhjb2ZmZWUxGDAWBgNVBAMTD0ZvdXJ0aENvZmZlZSBDQQITaAAAAAmaneVjEPlcTwAAAAAACTANBgkqhkiG9w0BAQEFAASCAQCqfsOYpuBToerQLkw/tl4tH9E+97TBTjGQN9NCjSgb78fF6edY0pNDU+PH4RB356wv3rfZi5IiNrVu5Od4k6uK4w0582ZM2n8NJFRY7KWSNHsmTIWlo/Vcr4laAtq5rw+CygaYcefptcaamkjdLj07e/Uk4KsetGo7ztPVjSEFwfRIfKv474dLDmPqp0ZwEWRQGZwmPoqFMbX3g85CJT8khPaqFW05yGDTPSX9YpuEE0Bmtht9EwOpOZe6O7sd77IhfFZVmHmwy5mIYN7K6mpx/4Cb5zcNmY3wmTBlKEkDQpZDRf5PpVQ3bmQ3we9XxeK1S4UsAXHVdYGD+bg/bCafMIAGCSqGSIb3DQEHATAUBggqhkiG9w0DBwQI5D5J2lwZS5OggASCF6jSG9iZA/EJ93fEvZYLV0v7GVo3JAsR11O7DlmkIqvkAg5iC6DQvXO1j88T/MS3wV+rqUbEhktr8Xyf4sAAPI4M6HMfVENCJTStJw1PzaGwUJHEasq39793nw4k268UV5XHXvzZoF3Os2OxUHSfHECOj
```

重要項目會包含下列範例文字字串：

- operation=GetCACert
- 嘗試擷取已發行的憑證
- 透過 GET 傳送 CSR
- operation=PKIOperation

### <a name="windows-devices"></a>Windows 裝置

在連線到 NDES 的 Windows 裝置上，您可以檢視裝置的 Windows 事件檢視器，並尋找成功連線的跡象。 系統會在裝置的 [DeviceManagement-Enterprise-Diagnostics-Provide]   > [管理員]  記錄中，將連線記錄為事件識別碼 **36**。

若要開啟記錄：

1. 在裝置上，執行 **eventvwr.msc** 以開啟 Windows 事件檢視器。

2. 展開 [應用程式及服務記錄檔]   > [Microsoft]   > [Windows]   > [DeviceManagement-Enterprise-Diagnostic-Provider]   > [管理員]  。

3. 尋找事件 **36**，其類似於下列範例，並具有 **SCEP:Certificate request generated successfully** (SCEP: 成功產生憑證要求) 的關鍵行：

   ```
   Event ID:      36
   Task Category: None
   Level:         Information
   Keywords:
   User:          <UserSid>
   Computer:      <Computer Name>
   Description:
   SCEP: Certificate request generated successfully. Enhanced Key Usage: (1.3.6.1.5.5.7.3.2), NDES URL: (https://<server>/certsrv/mscep/mscep.dll/pkiclient.exe), Container Name: (), KSP Setting: (0x2), Store Location: (0x1).
   ```

## <a name="troubleshoot-common-errors"></a>對常見錯誤進行疑難排解

下列各節可協助處理所有裝置平台對 NDES 的常見連線問題。

### <a name="status-code-500"></a>狀態碼 500

類似下列範例並具有狀態碼 500 的連線，表示 [在驗證後模擬用戶端]  使用者權限並未指派給 NDES 伺服器上的 IIS_IURS 群組。 狀態值 **500** 會出現在結尾：

```
2017-08-08 20:22:16 IP_address GET /certsrv/mscep/mscep.dll operation=GetCACert&message=SCEP%20Authority 443 - 10.5.14.22 profiled/1.0+CFNetwork/811.5.4+Darwin/16.6.0 - 500 0 1346 31
```

**修正此問題**：

1. 在 NDES 伺服器上，執行 **secpol.msc** 以開啟本機安全性原則。

2. 展開 [本機原則]  ，然後按一下 [使用者權限指派]  。

3. 按兩下右窗格中的 [在驗證後模擬用戶端]  。

4. 按一下 [新增使用者或群組]  ，在 [輸入物件名稱來選取]  方塊中輸入 **IIS_IURS**，然後按一下 [確定]  。

5. 按一下 [確定]  。

6. 重新啟動電腦，然後再次嘗試從裝置進行連線。

### <a name="test-the-scep-server-url"></a>測試 SCEP 伺服器 URL

使用下列步驟來測試於 SCEP 憑證設定檔中指定的 URL。

1. 在 Intune 中，編輯您的 SCEP 憑證設定檔並複製伺服器 URL。 URL 應該類似 *https://contoso.com/certsrv/mscep/msecp.dll* 。

2. 開啟網頁瀏覽器，然後瀏覽到該 SCEP 伺服器 URL。 結果應該如下：「HTTP 錯誤 403.0 – 禁止」  。 此結果指出 URL 正常運作。

   如果您沒有接收到該錯誤，請選取類似您所看到錯誤的連結，以檢視問題特定的指引：
   - [我接收到一般網路裝置註冊服務訊息](#general-ndes-message)
   - [我接收到「HTTP 錯誤 503。服務無法使用」](#http-error-503)
   - [我接收到 "GatewayTimeout" 錯誤](#gatewaytimeout)
   - [我接收到「HTTP 414 要求 - URI 太長」](#http-414-request-uri-too-long)
   - [我接收到「無法顯示此頁面」](#this-page-cant-be-displayed)
   - [我接收到「500 - 內部伺服器錯誤」](#internal-server-error)

#### <a name="general-ndes-message"></a>一般 NDES 訊息

當您瀏覽到 SCEP 伺服器 URL 時，您接收到下列網路裝置註冊服務訊息：

![SCEP 伺服器 URL](../protect/media/troubleshoot-scep-certificate-device-to-ndes/ndes-server-url-message.png)

- **原因**：此問題通常源自於 Microsoft Intune 連接器安裝的問題。

  Mscep.dll 是 ISAPI 擴充，其會在沒有正確安裝的情況下攔截連入要求並顯示 HTTP 403 錯誤。
  
  **解決方案**：檢查 *SetupMsi.log* 檔案以判斷 Microsoft Intune 連接器是否已成功安裝。 在下列範例中，*Installation completed successfully* (已成功完成安裝) 和 *Installation success or error status:0* (安裝成功或錯誤狀態: 0) 表示成功安裝：

  ```
  MSI (c) (28:54) [16:13:11:905]: Product: Microsoft Intune Connector -- Installation completed successfully.
  MSI (c) (28:54) [16:13:11:999]: Windows Installer installed the product. Product Name: Microsoft Intune Connector. Product Version: 6.1711.4.0. Product Language: 1033. Manufacturer: Microsoft Corporation. Installation success or error status: 0.
  ```

  如果安裝失敗，請移除 Microsoft Intune 連接器然後加以重新安裝。

#### <a name="http-error-503"></a>HTTP 錯誤 503

當您瀏覽至 SCEP 伺服器 URL 時，您接收到下列錯誤：

![HTTP 錯誤 503。 服務無法使用](../protect/media/troubleshoot-scep-certificate-device-to-ndes/service-unavailable.png)

此問題通常是因為 IIS 中的 **SCEP** 應用程式集區並未啟動。 在 NDES 伺服器上，開啟 [IIS 管理員]  並移至 [應用程式集區]  。 找出 **SCEP** 應用程式集區並確認其已啟動。

如果 SCEP 應用程式集區未啟動，請檢查伺服器上的應用程式事件記錄：

1. 在裝置上，執行 **eventvwr.msc** 以開啟 [事件檢視器]  ，然後移至 [Windows 記錄]   > [應用程式]  。

2. 尋找類似下列範例的事件，這代表應用程式集區在接收到要求時損毀：

   ```
   Log Name:      Application
   Source:        Application Error
   Event ID:      1000
   Task Category: Application Crashing Events
   Level:         Error
   Keywords:      Classic
   Description: Faulting application name: w3wp.exe, version: 8.5.9600.16384, time stamp: 0x5215df96
   Faulting module name: ntdll.dll, version: 6.3.9600.18821, time stamp: 0x59ba86db
   Exception code: 0xc0000005
   ```

**應用程式集區損毀的常見原因**：

- **原因 1**：NDES 伺服器的「信任的根憑證授權單位」憑證存放區中有 (未自我簽署的) 中繼 CA 憑證。

  **解決方案**：從「信任的根憑證授權單位」憑證存放區移除中繼憑證，然後重新啟動 NDES 伺服器。
  
  若要識別「信任的根憑證授權單位」憑證存放區中的所有中繼憑證，請執行下列 PowerShell Cmdlet：`Get-Childitem -Path cert:\LocalMachine\root -Recurse | Where-Object {$_.Issuer -ne $_.Subject}`

  擁有相同 [發行給]  和 [發行者]  值的憑證是根憑證。 否則，其便是中繼憑證。

  在移除憑證並重新啟動伺服器之後，請再次執行 PowerShell Cmdlet 以確認沒有中繼憑證。 如果有，請檢查是否有群組原則會將中繼憑證推送至 NDES 伺服器。 如果是，請從群組原則排除 NDES 伺服器，然後再次移除中繼憑證。

- **原因 2**：憑證撤銷清單 (CRL) 中的 URL 已被封鎖，或是無法由 Intune 憑證連接器所使用的憑證所存取。

  **解決方案**：啟用其他記錄以收集更多資訊：
  1. 開啟 [事件檢視器]，按一下 [檢視]  ，確定已選取 [顯示分析與偵錯記錄檔]  選項。
  2. 移至 [應用程式及服務記錄檔]   > [Microsoft]   > [Windows]   > [CAPI2]   > [操作]  ，以滑鼠右鍵按一下 [操作]  ，然後按一下 [啟用記錄]  。
  3. 在啟用 CAPI2 記錄之後，請重新產生該問題，並檢視事件記錄以對問題進行疑難排解。

- **原因 3**：[CertificateRegistrationSvc]  上的 IIS 權限已啟用 [Windows 驗證]  。

  **解決方案**：啟用 [匿名驗證]  並停用 [Windows 驗證]  ，然後重新啟動 NDES 伺服器。

  ![IIS 權限](../protect/media/troubleshoot-scep-certificate-device-to-ndes/iis-permissions.png)

#### <a name="gatewaytimeout"></a>GatewayTimeout

當您瀏覽至 SCEP 伺服器 URL 時，您接收到下列錯誤：

![Gatewaytimeout 錯誤](../protect/media/troubleshoot-scep-certificate-device-to-ndes/gateway-timeout.png)

- **原因**：未啟動 [Microsoft AAD 應用程式 Proxy 連接器]  服務。

  **解決方案**：執行 **services.msc**，然後確定 [Microsoft AAD 應用程式 Proxy 連接器]  服務正在執行，且 [啟動類型]  已設定為 [自動]  。

#### <a name="http-414-request-uri-too-long"></a>HTTP 414 要求 - URI 太長

當您瀏覽至 SCEP 伺服器 URL 時，您接收到下列錯誤：`HTTP 414 Request-URI Too Long`

- **原因**：IIS 要求篩選沒有設定以支援 NDES 服務所接收的長 URL (查詢)。 此支援會在您[設定 NDES 服務](certificates-scep-configure.md#configure-the-ndes-service)以搭配您的 SCEP 基礎結構使用時設定。

- **解決方案**：設定長 URL 的支援。

  1. 在 NDES 伺服器上開啟 [IIS 管理員]，選取 [預設的網站]   > [要求篩選]   > [編輯功能設定]  以開啟 [編輯要求篩選設定]  頁面。

  2. 進行以下設定：
     - **URL 長度上限 (位元組)** = 65534
     - **查詢字串上限 (位元組)** = 65534

  3. 選取 [確定]  以儲存這項設定並關閉 IIS 管理員。

  4. 找出下列登錄機碼以確認其具有指出的值來驗證此設定：

     HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\HTTP\Parameters

     下列值設定為 DWORD 項目：
     - 名稱：**MaxFieldLength**，具有十進位值 **65534**
     - 名稱：**MaxRequestBytes**，具有十進位值 **65534**

  5. 重新啟動 NDES 伺服器。

#### <a name="this-page-cant-be-displayed"></a>無法顯示此頁面

您已設定 Azure AD 應用程式 Proxy。 當您瀏覽至 SCEP 伺服器 URL 時，您接收到下列錯誤：

`This page can't be displayed`

- **原因**：此問題會在應用程式 Proxy 設定中的 SCEP 外部 URL 不正確時發生。 此 URL 的範例為 https://contoso.com/certsrv/mscep/mscep.dll 。

  **解決方案**：在應用程式 Proxy 設定中，針對 SCEP 外部 URL 使用預設網域 *yourtenant.msappproxy.net*。

#### <a name="internal-server-error"></a>500 - 內部伺服器錯誤

當您瀏覽至 SCEP 伺服器 URL 時，您接收到下列錯誤：

![500 - 內部伺服器錯誤](../protect/media/troubleshoot-scep-certificate-device-to-ndes/500-internal-server-error.png)

- **原因 1**：NDES 服務帳戶已鎖定，或是其密碼已過期。

  **解決方案**：將帳戶解除鎖定，或是重設密碼。

- **原因 2**：MSCEP-RA 憑證已過期。

  **解決方案**：如果 MSCEP-RA 憑證已過期，請重新安裝 NDES 角色或是要求新的 CEP 加密和 Exchange 註冊代理程式 (離線要求) 憑證。

  若要要求新的憑證，請遵循這些步驟：

  1. 在憑證授權單位 (CA) 或發行 CA 上，開啟 [憑證範本] MMC。 確定已登入的使用者和 NDES 伺服器具有 CEP 加密和 Exchange 註冊代理程式 (離線要求) 憑證範本的 [讀取]  和 [註冊]  權限。

  2. 檢查 NDES 伺服器上的過期憑證，從憑證中複製 [主體]  資訊。

  3. 開啟 [電腦帳戶]  的 [憑證] MMC。

  4. 展開 [個人]  ，以滑鼠右鍵按一下 [憑證]  ，然後選取 [所有工作]   > [要求新憑證]  。

  5. 在 [要求憑證]  頁面上，選取 [CEP 加密]  ，然後按一下 [需要更多資訊才能註冊此憑證。**請按一下此處以設定設定值。]** 。

     ![選取 CEP 加密](../protect/media/troubleshoot-scep-certificate-device-to-ndes/select-scep-encryption.png)

  6. 在 [憑證內容]  中，按一下 [主體]  索引標籤，以您在步驟 2 期間所收集的資訊填入 [主體名稱]  ，按一下 [新增]  ，然後按一下 [確定]  。

  7. 完成憑證註冊。

  8. 開啟 [我的使用者帳戶]  的 [憑證] MMC。

     當您註冊 Exchange 註冊代理程式 (離線要求) 憑證時，必須在使用者內容中加以完成。 因為此憑證範本的 [主體類型]  已設定為 [使用者]  。

  9. 展開 [個人]  ，以滑鼠右鍵按一下 [憑證]  ，然後選取 [所有工作]   > [要求新憑證]  。

  10. 在 [要求憑證]  頁面上，選取 [Exchange 註冊代理程式 (離線要求)]  ，然後按一下 [需要更多資訊才能註冊此憑證。**請按一下此處以設定設定值。]** 。

      ![選取 Exchange 註冊代理程式](../protect/media/troubleshoot-scep-certificate-device-to-ndes/select-exchange-enrollment-agent.png)

  11. 在 [憑證內容]  中，按一下 [主體]  索引標籤，以您在步驟 2 期間所收集的資訊填入 [主體名稱]  ，按一下 [新增]  。

      ![憑證內容](../protect/media/troubleshoot-scep-certificate-device-to-ndes/certificate-properties.png)

      選取 [私密金鑰]  索引標籤，選取 [可匯出私密金鑰]  ，然後按一下 [確定]  。

      ![私密金鑰](../protect/media/troubleshoot-scep-certificate-device-to-ndes/private-key.png)

  12. 完成憑證註冊。

  13. 從目前使用者的憑證存放區中匯出 Exchange 註冊代理程式 (離線要求) 憑證。 在 [憑證匯出精靈] 中，選取 [是，匯出私密金鑰]  。

  14. 將憑證匯入至本機電腦的憑證存放區。

  15. 在 [憑證] MMC 中，針對每個新憑證執行下列動作：

      以滑鼠右鍵按一下憑證，按一下 [所有工作]   > [管理私密金鑰]  ，將 [讀取]  權限新增至 NDES 服務帳戶。

  16. 執行 **iisreset** 命令來重新啟動 IIS。

## <a name="next-steps"></a>後續步驟

如果裝置成功連線到 NDES 伺服器以提出憑證要求，下一步便是檢閱[Intune 憑證連接器原則模組](troubleshoot-scep-certificate-ndes-policy-module.md)。

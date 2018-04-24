---
title: 使用 Cisco ISE 保護網路存取權
description: 使用 Cisco ISE 與 Intune，讓裝置向 Intune 註冊並符合原則，然後才存取 Cisco ISE 控制的 Wi-Fi 和 VPN。
keywords: ''
author: dougeby
ms.author: angrobe
manager: angrobe
ms.date: 01/03/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 5631bac3-921d-438e-a320-d9061d88726c
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 1893410f4993d6feaa218d251dd7e2561286f5a3
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="using-cisco-ise-with-microsoft-intune"></a>使用 Cisco ISE 與 Microsoft Intune

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Intune 與 Cisco Identity Services Engine (ISE) 整合可讓您在 ISE 環境中使用 Intune 裝置註冊與相容性狀態來撰寫網路原則。 您可以使用這些原則來確保您公司網路的存取權僅限於受 Intune 管理且符合 Intune 原則的裝置。

## <a name="configuration-steps"></a>設定步驟

若要啟用這項整合，您不需要在 Intune 租用戶中進行任何設定。 您必須提供給 Cisco ISE 伺服器存取您 Intune 租用戶的權限。 完成之後，安裝程式的其餘部分會在 Cisco ISE 伺服器內執行。 本文給予您為 ISE 伺服器提供存取 Intune 租用戶權限的指示。

### <a name="step-1-manage-the-certificates"></a>步驟 1︰管理憑證
從 Azure Active Directory (Azure AD) 主控台匯出憑證，再匯入 ISE 主控台的受信任憑證存放區：

#### <a name="internet-explorer-11"></a>Internet Explorer 11


   a. 以系統管理員身分執行 Internet Explorer，並登入 Azure AD 主控台。

   b. 在網址列中選擇鎖定圖示，然後選擇 [檢視憑證]。

   c. 在憑證內容的 [詳細資料] 索引標籤，選擇 [複製到檔案]。

   d. 在 [憑證匯出精靈] 的 [歡迎使用] 頁面上，選擇 [下一步]。

   e. 在 [匯出檔案格式] 頁面上，保留預設值 [DER 編碼二進位 x.509 (.CER)]，然後選擇 [下一步]。  

   f. 在 [要匯出的檔案] 頁面上，選擇 [瀏覽] 選取儲存檔案的位置，並提供檔案名稱。 雖然看似您選取要匯出的檔案，但您實際上是為要儲存匯出憑證的檔案命名。 選擇 [下一步] &gt; [完成]。

   g. 從 ISE 主控台內，將 Intune 憑證 (您已匯出的檔案) 匯入到 [受信任的憑證] 存放區。

#### <a name="safari"></a>Safari

 a. 登入 Azure AD 主控台。

b. 選擇鎖定圖示 &gt; [更多資訊]。

   c. 選擇 [檢視憑證] &gt; [詳細資料]。

   d. 選擇憑證，然後選擇 [匯出]。 

   e. 從 ISE 主控台內，將 Intune 憑證 (您已匯出的檔案) 匯入到 [受信任的憑證] 存放區。

> [!IMPORTANT]
>
> 檢查憑證的到期日，因為您必須在此憑證到期時匯出並匯入新的憑證。


### <a name="obtain-a-self-signed-cert-from-ise"></a>從 ISE 取得自我簽署憑證 

1. 在 ISE 主控台中，請移至 [管理] > [憑證] > [系統憑證] > [產生自我簽署憑證]。  
2. 匯出自我簽署憑證。
3. 在文字編輯器中，編輯匯出的憑證︰

   - 刪除 **-----BEGIN CERTIFICATE-----**
   - 刪除 **-----END CERTIFICATE-----**

請確定所有的文字在同一行


### <a name="step-2-create-an-app-for-ise-in-your-azure-ad-tenant"></a>步驟 2︰在 Azure AD 租用戶中為 ISE 建立應用程式
1. 在 Azure AD 主控台中，選擇 [應用程式]  > [新增應用程式] > [加入我的組織正在開發的應用程式]。
2. 提供應用程式的名稱和 URL。 URL 可能是您的公司網站。
3. 下載應用程式資訊清單 (JSON 檔案)。
4. 編輯資訊清單 JSON 檔案。 在稱為 **keyCredentials** 的設定中，提供步驟 1 中的已編輯憑證文字作為設定值。
5. 儲存檔案，而不變更其名稱。
6. 提供應用程式對於 Microsoft Graph 和 Microsoft Intune API 的權限。

   a. 針對 Microsoft Graph，選擇下列各項：
    - **應用程式權限**︰讀取目錄資料
    - **已委派的權限**：
        - 隨時存取使用者的資料
        - 登入使用者

   b. 針對 Microsoft Intune API，在 **[應用程式權限]** 中選擇 **[Get device state and compliance from Intune]** (從 Intune 取得裝置狀態和相容性)。

7. 選擇 [檢視端點]，並複製下列值以便用於進行 ISE 設定︰

|Azure AD 入口網站的價值|ISE 入口網站中的對應欄位|
|-------------------|---------------------------------|
|Microsoft Azure AD Graph API 端點|自動搜索 URL|
|OAuth 2.0 權杖端點|權杖簽發 URL|
|使用用戶端識別碼更新您的程式碼|用戶端識別碼|

### <a name="step-4-upload-the-self-signed-certificate-from-ise-into-the-ise-app-you-created-in-azure-ad"></a>步驟 4︰將自我簽署憑證從 ISE 上傳至您在 Azure AD 中建立的 ISE 應用程式
1. 從 .cer X509 公開憑證檔取得 Base64 編碼的憑證值和指紋。 這個範例使用 PowerShell：


~~~
  $cer = New-Object System.Security.Cryptography.X509Certificates.X509Certificate2
  $cer.Import(“mycer.cer”)
  $bin = $cer.GetRawCertData()
  $base64Value = [System.Convert]::ToBase64String($bin)
  $bin = $cer.GetCertHash()
  $base64Thumbprint = [System.Convert]::ToBase64String($bin)
  $keyid = [System.Guid]::NewGuid().ToString()

Store the values for $base64Thumbprint, $base64Value and $keyid, to be used in the next step.
~~~
2. 透過資訊清單檔上傳憑證。 登入 [Azure 管理入口網站](https://manage.windowsazure.com)
3. 在 Azure AD 嵌入式管理單元中，尋找您要使用 X.509 憑證設定的應用程式。
4. 下載應用程式資訊清單檔。 
5. 以下列 JSON 取代空的 “KeyCredentials”: [], 屬性。  KeyCredentials 複雜類型記載於 [Entity and complex type reference](https://msdn.microsoft.com/library/azure/ad/graph/api/entity-and-complex-type-reference#KeyCredentialType) (實體和複雜類型參考) 中。


~~~
“keyCredentials“: [
{
 “customKeyIdentifier“: “$base64Thumbprint_from_above”,
 “keyId“: “$keyid_from_above“,
 “type”: “AsymmetricX509Cert”,
 “usage”: “Verify”,
 “value”:  “$base64Value_from_above”
 }2. 
 ], 
~~~

例如：

    “keyCredentials“: [
    {
    “customKeyIdentifier“: “ieF43L8nkyw/PEHjWvj+PkWebXk=”,
    “keyId“: “2d6d849e-3e9e-46cd-b5ed-0f9e30d078cc”,
    “type”: “AsymmetricX509Cert”,
    “usage”: “Verify”,
    “value”: “MIICWjCCAgSgAwIBA***omitted for brevity***qoD4dmgJqZmXDfFyQ”
    }
    ],

6. 將變更儲存至應用程式資訊清單檔。
7. 透過 Azure 管理入口網站上傳已編輯的應用程式資訊清單檔。
8. 選擇性︰再次下載資訊清單，以檢查應用程式中是否有您的 X.509 憑證。

>[!NOTE]
>
> KeyCredentials 是一項集合，因此您可以上傳多個 X.509 憑證進行變換，或在遭到洩漏的情況下刪除多個憑證。


### <a name="step-4-configure-ise-settings"></a>步驟 4：進行 ISE 設定
在 ISE 管理員主控台中，提供這些設定值︰
  - **伺服器類型**：Mobile Device Manager
  - **驗證類型**：OAuth – 用戶端認證
  - **自動搜索**：是
  - **自動探索 URL**︰輸入步驟 1 的值。
  - **用戶端識別碼**︰輸入步驟 1 的值。
  - **權杖簽發 URL**︰輸入步驟 1 的值。



## <a name="information-shared-between-your-intune-tenant-and-your-cisco-ise-server"></a>Intune 租用戶和 Cisco ISE 伺服器之間共用的資訊
下表列出您的 Intune 租用戶和 Cisco ISE 伺服器之間，針對受 Intune 管理之裝置所共用的資訊。

|屬性|  說明|
|---------------|------------------------------------------------------------|
|complianceState|指出裝置相容或不相容的 true 或 false 字串。|
|isManaged|指出用戶端是否受 Intune 管理的 true 或 false 字串。|
|macAddress|裝置的 MAC 位址。|
|serialNumber|裝置的序號。 它僅適用於 iOS 裝置。|
|imei|IMEI (15 位數︰14 個數字再加上一個檢查碼) 或 IMEISV (16 位數) 數字包含裝置的來源、型號和序號等資訊。 此數字的結構指定於 3GPP TS 23.003 中。 僅適用於具有 SIM 卡的裝置。|
|udid|唯一裝置識別碼為 40 個字母和數字的序列。 它是專用於 iOS 裝置。|
|meid|行動設備識別碼，是用來識別實體 CDMA 行動站設備的全球唯一編號。 數字格式由 3GPP2 report S. R0048 所定義。 不過，實際上它可被視為 IMEI，但使用十六進位數字。 MEID 有 56 個位元長 (14 個十六進位的數字)。 它包含三個欄位，包括 8 位元地區碼 (RR)、24 位元製造商碼，和製造商指派的 24 位元序號。|
|osVersion|裝置的作業系統版本。
|模型|裝置型號。
|manufacturer|裝置製造商。
|azureDeviceId|裝置加入 Azure AD 工作場所之後的識別碼。 若裝置未加入則為空的 GUID。|
|lastContactTimeUtc|裝置上一次簽入 Intune 管理服務時的日期和時間。


## <a name="user-experience"></a>使用者經驗

當使用者嘗試使用任何未經註冊的裝置存取資源時，他們會看見註冊的提示，如以下所示︰

![註冊提示的範例](../media/cisco-ise-user-iphone.png)

當使用者選擇註冊，就會重新導向至 Intune 註冊程序。 這些主題中說明 Intune 的使用者註冊體驗︰

- [將您的 Android 裝置註冊到 Intune](/intune-user-help/enroll-your-device-in-Intune-android)</br>
- [在 Intune 註冊 iOS 裝置](/intune-user-help/enroll-your-device-in-intune-ios)</br>
- [在 Intune 註冊 Mac OS X 裝置](/intune-user-help/enroll-your-device-in-intune-mac-os-x)</br>
- [在 Intune 註冊 Windows 裝置](/intune-user-help/enroll-your-device-in-intune-windows)</br>

另外還有[可下載的註冊指示集合](https://gallery.technet.microsoft.com/End-user-Intune-enrollment-55dfd64a)，可用來建立自訂的使用者體驗指導方針。


### <a name="see-also"></a>另請參閱

[Cisco Identity Services Engine Administrator Guide, Release 2.1](http://www.cisco.com/c/en/us/td/docs/security/ise/2-1/admin_guide/b_ise_admin_guide_21/b_ise_admin_guide_20_chapter_01000.html#task_820C9C2A1A6647E995CA5AAB01E1CDEF) (思科身分服務引擎管理指南 2.1 版)

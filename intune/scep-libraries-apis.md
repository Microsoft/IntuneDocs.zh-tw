---
title: 用於上架第 3 方憑證授權單位的 API
titleSuffix: Microsoft Intune
description: 新增或整合協力廠商憑證授權單位 (CA) 的 SCEP GitHub 解決方案，以在 Microsoft Intune 中向裝置核發 SCEP 憑證。 此解決方案包含 Java 和 C# API，它們會驗證、將成功和失敗的通知傳送至 Intune，並在與 Intune 進行通訊時使用 SSL 通訊端 Factory。 也請檢視測試您 SCEP CA 設定的步驟概觀。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/06/2018
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: a7baa95d6719dfa3161ae6644bbc9351d3f3d9f0
ms.sourcegitcommit: 7c251948811b8b817e9fe590b77f23aed95b2d4e
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "67882373"
---
# <a name="use-apis-to-add-third-party-cas-for-scep-to-intune"></a>使用 API 以針對 SCEP 將協力廠商 CA 新增至 Intune

在 Microsoft Intune 中，您可以新增協力廠商憑證授權單位 (CA)，並讓這些 CA 使用簡單憑證註冊通訊協定 (SCEP) 核發和驗證憑證。 [新增協力廠商憑證授權單位](certificate-authority-add-scep-overview.md)提供這項功能的概觀，並描述 Intune 中的系統管理員工作。

也有一些開發人員工作使用 Microsoft 發佈了在 GitHub.com 中的開放原始碼程式庫。 程式庫包含的 API 會：

- 驗證 Intune 動態產生的 SCEP 密碼
- 通知 Intune 在裝置上建立的憑證正在提交 SCEP 要求

使用此 API，您的協力廠商 SCEP 伺服器會與 MDM 裝置的 Intune SCEP 管理解決方案整合。 程式庫對使用者而言抽象化了許多層面，例如驗證、服務位置和 ODATA Intune 服務 API。

## <a name="scep-management-solution"></a>SCEP 管理解決方案

![協力廠商憑證授權單位 SCEP 如何與 Microsoft Intune 整合](./media/scep-certificate-vendor-integration.png)

使用 Intune 時，系統管理員會建立 SCEP 設定檔，然後將這些設定檔指派給 MDM 裝置。 SCEP 設定檔包含參數，例如：

- SCEP 伺服器 URL
- 憑證授權單位的受信任根憑證
- 憑證屬性和更多功能

簽入 Intune 的裝置會被指派 SCEP 設定檔，並且會使用這些參數設定。 動態產生的 SCEP 挑戰密碼是由 Intune 所建立，然後指派給裝置。

這項挑戰包含：

- 動態產生的挑戰密碼
- 裝置核發給 SCEP 伺服器之憑證簽署要求 (CSR) 中預期參數的詳細資料
- 挑戰到期時間

Intune 會將這項資訊加密，並簽署加密 Blob，然後將這些詳細資料封裝至 SCEP 挑戰密碼。

連絡 SCEP 伺服器以要求憑證後提供此 SCEP 挑戰密碼的裝置。 SCEP 伺服器會將 CSR 和加密 SCEP 挑戰密碼傳送給 Intune，以供驗證。  此挑戰密碼和 CSR 必須通過 SCEP 伺服器的驗證，才能將憑證核發給裝置。 驗證 SCEP 挑戰時，會發生下列檢查：


- 驗證加密 blob 的簽章
- 驗證挑戰尚未過期
- 驗證設定檔仍以裝置為目標
- 驗證 CSR 中的裝置所要求的憑證屬性符合預期的值

SCEP 管理解決方案也包含報告。 系統管理員可以取得有關 SCEP 設定檔的部署狀態資訊，以及核發給裝置的憑證相關資訊。

## <a name="integrate-with-intune"></a>與 Intune 整合

與 Intune SCEP 整合的程式庫程式碼可供下載，其位於 [Microsoft/Intune-Resource-Acess GitHub 存放庫](https://github.com/Microsoft/Intune-Resource-Access/tree/develop/src/CsrValidation)。

將程式庫整合至產品包含下列步驟。 這些步驟需要使用 GitHub 存放庫，以及在 Visual Studio 中建立解決方案和專案的知識。

1. 註冊以接收存放庫的通知
2. 複製或下載存放庫
3. 移至您需要的程式庫實作，在 `\src\CsrValidation` 資料夾下 (https://github.com/Microsoft/Intune-Resource-Access/tree/develop/src/CsrValidation)
4. 使用讀我檔案中的指示建置程式庫
5. 將程式庫包含在建置您 SCEP 伺服器的專案中
6. 在 SCEP 伺服器上完成下列工作：

    - 允許系統管理員設定程式庫用於驗證的 [Azure 應用程式識別碼、Azure 應用程式金鑰和租用戶識別碼](#onboard-scep-server-in-azure) (在本文中)。 系統管理員應該可以更新 Azure 應用程式金鑰。
    - 識別包含 Intune 所產生之 SCEP 密碼的 SCEP 要求
    - 使用**驗證要求 API** 程式庫驗證 Intune 產生的 SCEP 密碼
    - 使用程式庫通知 API 通知 Intune 有關針對具有 Intune 產生之 SCEP 密碼的 SCEP 要求核發的憑證。 也通知 Intune 有關處理這些 SCEP 要求時可能發生的錯誤。
    - 確認伺服器記錄足夠的資訊來協助系統管理員針對問題進行疑難排解

7. 完成[整合測試](#integration-testing) (在本文中)，並解決任何問題
8. 提供客戶書面的指引，其說明：

    - SCEP 伺服器需在 Azure 入口網站上架的方式
    - 如何取得設定程式庫所需的 Azure 應用程式識別碼及 Azure 應用程式金鑰

### <a name="onboard-scep-server-in-azure"></a>將 SCEP 伺服器在 Azure 上架

若要向 Intune 驗證，SCEP 伺服器需要 Azure 應用程式識別碼、Azure 應用程式金鑰和租用戶識別碼。 SCEP 伺服器也需要權限可存取 Intune API。

為了取得這項資料，SCEP 伺服器系統管理員會登入 Azure 入口網站、註冊應用程式、提供應用程式 **Microsoft Intune API\SCEP 挑戰驗證**權限、建立應用程式金鑰，然後下載應用程式識別碼、其金鑰及租用戶識別碼。

如需註冊應用程式並取得識別碼和金鑰的指引，請參閱[使用入口網站來建立 AAD 應用程式和服務主體以存取資源](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-create-service-principal-portal)。

### <a name="java-library-api"></a>Java 程式庫 API

Java 程式庫會實作為 Maven 專案，它會在建立時提取其相依性。 API 由 `IntuneScepServiceClient` 類別實作在 `com.microsoft.intune.scepvalidation` 命名空間下。

#### <a name="intunescepserviceclient-class"></a>IntuneScepServiceClient 類別

`IntuneScepServiceClient` 類別包含 SCEP 服務用來驗證 SCEP 密碼、通知 Intune 所建立的憑證，以及列出任何錯誤的方法。

##### <a name="intunescepserviceclient-constructor"></a>IntuneScepServiceClient 建構函式

簽章：

```java
IntuneScepServiceClient(
    Properties configProperties)
```

描述:

具現化並設定 `IntuneScepServiceClient` 物件。

參數：

    - configProperties    包含用戶端設定資訊的屬性物件

設定必須包含下列屬性：

    - AAD_APP_ID="在上架程序中取得的 Azure 應用程式識別碼"
    - AAD_APP_KEY="在上架程序中取得的 Azure 應用程式金鑰"
    - TENANT="在上架程序中取得的租用戶識別碼"
    - PROVIDER_NAME_AND_VERSION="用來識別您的產品和其版本的資訊"
    
如果您的解決方案需要 Proxy (可搭配或不搭配驗證使用)，則您可以新增下列屬性：

    - PROXY_HOST="裝載 Proxy 的主機。"
    - PROXY_PORT="Proxy 正在接聽的連接埠。"
    - PROXY_USER="Proxy 使用基本驗證時要使用的使用者名稱。"
    - PROXY_PASS="Proxy 使用基本驗證時要使用的密碼。"

擲回：

    - IllegalArgumentException    若建構函式執行時沒有適當的屬性物件便擲回。

> [!IMPORTANT]
> 最好是具現化這個類別的執行個體，並使用它來處理多個 SCEP 要求。 這樣做可以降低額外負荷，因為它會快取驗證權杖和服務位置資訊。

**安全性注意事項**  
SCEP 伺服器實作者必須保護輸入在設定屬性並保存到儲存體中的資料，免於遭受竄改和洩漏。 建議使用適當的 ACL 和加密來保護資訊。

##### <a name="validaterequest-method"></a>ValidateRequest 方法

簽章：

```java
void ValidateRequest(
    String transactionId,
    String certificateRequest)
```

描述:

驗證 SCEP 憑證要求。

參數：

    - transactionId         SCEP 交易識別碼
    - certificateRequest    DER 編碼 PKCS #10 憑證要求以 Base64 編碼為字串

擲回：

    - IllegalArgumentException      若使用無效的參數呼叫便擲回
    - IntuneScepServiceException    若發現憑證要求無效便擲回
    - Exception                     若發生未預期的錯誤便擲回

> [!IMPORTANT]
> 這個方法所擲回的例外狀況應該由伺服器記錄。 請注意，`IntuneScepServiceException` 屬性具有憑證要求驗證失敗原因的詳細資訊。

**安全性注意事項**  

- 如果這個方法擲回例外狀況，SCEP 伺服器**不得**核發憑證給用戶端。
- SCEP 憑證要求驗證失敗可能表示 Intune 基礎結構中的問題。 或者，它們可能表示攻擊者正在嘗試取得憑證。

##### <a name="sendsuccessnotification-method"></a>SendSuccessNotification 方法

簽章：

```java
void SendSuccessNotification(
    String transactionId,
    String certificateRequest,
    String certThumbprint,
    String certSerialNumber,
    String certExpirationDate,
    String certIssuingAuthority)
```

描述:

通知 Intune 在處理 SCEP 要求的過程中建立了憑證。

參數：

    - transactionId         SCEP 交易識別碼
    - certificateRequest    DER 編碼 PKCS #10 憑證要求以 Base64 編碼為字串
    - certThumprint           已佈建憑證的指紋
    - certSerialNumber        已佈建憑證的序號
    - certExpirationDate      已佈建憑證的到期日。 日期時間字串的格式應為 Web UTC 時間 (YYYY-MM-DDThh:mm:ss.sssTZD) ISO 8601。
    - certIssuingAuthority    核發憑證的授權單位名稱

擲回：

    - IllegalArgumentException      若使用無效的參數呼叫便擲回
    - IntuneScepServiceException    若發現憑證要求無效便擲回
    - Exception                     若發生未預期的錯誤便擲回

> [!IMPORTANT]
> 這個方法所擲回的例外狀況應該由伺服器記錄。 請注意，`IntuneScepServiceException` 屬性具有憑證要求驗證失敗原因的詳細資訊。

**安全性注意事項**

- 如果這個方法擲回例外狀況，SCEP 伺服器**不得**核發憑證給用戶端。
- SCEP 憑證要求驗證失敗可能表示 Intune 基礎結構中的問題。 或者，它們可能表示攻擊者正在嘗試取得憑證。

##### <a name="sendfailurenotification-method"></a>SendFailureNotification 方法

簽章：

```java
void SendFailureNotification(
    String transactionId,
    String certificateRequest,
    long  hResult,
    String errorDescription)
```

描述:

通知 Intune 在處理 SCEP 要求時發生錯誤。 不應該針對此類別的方法所擲回的例外狀況叫用這個方法。

參數：

    - transactionId         SCEP 交易識別碼
    - certificateRequest    DER 編碼 PKCS #10 憑證要求以 Base64 編碼為字串
    - hResult               最能描述所發生錯誤的 Win32 錯誤碼。 請參閱 [Win32 錯誤碼](https://msdn.microsoft.com/library/cc231199.aspx)
    - errorDescription      所發生錯誤的描述

擲回：

    - IllegalArgumentException      若使用無效的參數呼叫便擲回
    - IntuneScepServiceException    若發現憑證要求無效便擲回
    - Exception                     若發生未預期的錯誤便擲回

> [!IMPORTANT]
> 這個方法所擲回的例外狀況應該由伺服器記錄。 請注意，`IntuneScepServiceException` 屬性具有憑證要求驗證失敗原因的詳細資訊。

**安全性注意事項**

- 如果這個方法擲回例外狀況，SCEP 伺服器**不得**核發憑證給用戶端。
- SCEP 憑證要求驗證失敗可能表示 Intune 基礎結構中的問題。 或者，它們可能表示攻擊者正在嘗試取得憑證。

##### <a name="setsslsocketfactory-method"></a>SetSslSocketFactory 方法

簽章：

```java
void SetSslSocketFactory(
    SSLSocketFactory factory)
```

描述:

使用這個方法來通知用戶端，它必須在與 Intune 通訊時，使用指定的 SSL 通訊端 Factory (而不是預設值)。

參數：

    - Factory    用戶端應該用於 HTTPS 要求的 SSL 通訊端 Factory

擲回：

    - IllegalArgumentException      若使用無效的參數呼叫便擲回

> [!NOTE]
> 如果需要，必須在執行此類別的其他方法之前，設定 SSL 通訊端 Factory。

## <a name="integration-testing"></a>整合測試

驗證及測試您的解決方案與 Intune 正確地整合是必要的。 以下列出步驟概觀：

1. 設定 [Intune 試用帳戶](account-sign-up.md)。
2. [在 Azure 入口網站中將 SCEP 伺服器上架](#onboard-scep-server-in-azure) (在本文中)。
3. 使用上架 SCEP 伺服器時建立的識別碼和金鑰，[設定 SCEP 伺服器](certificates-scep-configure.md)。
4. [註冊裝置](device-enrollment.md)以測試[案例測試矩陣](https://github.com/Microsoft/Intune-Resource-Access/blob/develop/src/CsrValidation/doc/TestMatrix.csv)中的案例。
5. 為您的測試憑證授權單位[建立受信任的根憑證設定檔](certificates-scep-configure.md)。
6. 建立 SCEP 設定檔以測試[案例測試矩陣](https://github.com/Microsoft/Intune-Resource-Access/blob/develop/src/CsrValidation/doc/TestMatrix.csv)中所列的案例。
7. [指派設定檔](device-profile-assign.md)給註冊裝置的使用者。
8. 等待裝置與 Intune 同步處理。 或以手動方式[同步處理裝置](device-sync.md)。
9. 確認受信任的根憑證和 SCEP [設定檔已部署到裝置](device-profile-monitor.md)。
10. 確認所有裝置上都已安裝受信任的根憑證。
11. 確認所有裝置上都已安裝指派設定檔的 SCEP 憑證。
12. 確認已安裝之憑證的屬性符合 SCEP 設定檔中設定的屬性。
13. 確認已核發的憑證正確地列在 Intune 主控台中

## <a name="see-also"></a>請參閱

- [新增協力廠商 CA 概觀](certificate-authority-add-scep-overview.md)
- [安裝 Intune](setup-steps.md)
- [裝置註冊](device-enrollment.md)
- [設定 SCEP 憑證設定檔](certificates-scep-configure.md#create-a-scep-certificate-profile) (Microsoft NDES Server\Connector 安裝程式不能用在此案例中)

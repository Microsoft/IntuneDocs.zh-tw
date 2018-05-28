---
title: 設定 Microsoft Intune 以進行 iOS 裝置單一登入
titlesuffix: ''
description: 了解如何設定 Microsoft Intune 以進行 iOS 裝置單一登入。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/2/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 010ed8511b042d6f764ba947f616d76521588f42
ms.sourcegitcommit: 91802e78cd5014d20a828ca25a54a381d452f0f8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/16/2018
---
# <a name="configure-microsoft-intune-for-ios-device-single-sign-on"></a>設定 Microsoft Intune 以進行 iOS 裝置單一登入

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

大部分的企業營運 (LOB) 應用程式需要某種程度的使用者驗證才會支援安全性。 在許多情況下這需要使用者多次鍵入相同的認證，這很令使用者沮喪。 為改善使用者體驗，開發人員可以建立使用單一登入的應用程式，減少使用者必須提供認證的次數。

若要利用 iOS 裝置單一登入，您必須具備下列條件：

- 自動編碼在 iOS 裝置的單一登入承載中尋找使用者認證存放區的應用程式。
- 設定進行 iOS 裝置單一登入的 Intune。

## <a name="to-configure-intune-for-ios-device-single-sign-on"></a>設定 Intune 進行 iOS 裝置單一登入


1. 登入 [Azure 入口網站](https://portal.azure.com)。
2. 選擇 [All services] (所有服務) > [Intune]。 Intune 位於 [Monitoring + Management] (監視 + 管理) 區段。
3. 在 [Intune] 窗格中，選擇 [裝置設定]。
4. 在 [裝置設定] 窗格的 [管理] 區段下，選擇 [設定檔]。
5. 在 [設定檔] 窗格中，選擇 [建立設定檔]。
6. 提供名稱和描述，並設定下列設定：
   - [平台]：選擇 [iOS]。
   - [設定檔類型]：選擇 [裝置功能]。
7. 在 [裝置功能] 窗格上，選擇 [單一登入]。

   ![單一登入窗格](./media/sso-blade.png)

8. 使用下列摘要表，協助您填寫 [單一登入] 窗格上的欄位。 如需詳細資料，請參閱表格之後的章節。

   |欄位  |附註|
   |---------|---------|
   |**AAD 中的使用者名稱屬性**|Intune 會在 AAD 中查看每個使用者的屬性，並填入個別欄位 (例如 UPN)，然後產生安裝在裝置上的 XML 承載。|
   |**領域**|URL 的網域部分。|
   |**使用單一登入的 URL 首碼**|您組織中需要使用者單一登入驗證的任何 URL|
   |**使用單一登入的應用程式**|使用者裝置上使用單一登入承載的應用程式。|
   |**認證更新憑證**|如果使用憑證進行驗證，請選取部署至使用者當作驗證憑證的 SCEP 或 PFX 憑證。|

以下各節提供單一登入各欄位的詳細資料。

### <a name="username-attribute-from-aad-and-realm"></a>AAD 和領域中的使用者名稱屬性

- 如果此欄位選取 [使用者主體名稱]，則會以下列方式剖析：

   ![使用者名稱屬性](media/User-name-attribute.png)

   您也可以選擇以 [領域] 文字方塊中鍵入的文字覆寫領域。

   例如，Contoso 可能有歐洲、亞洲和北美洲等數個子地區。 他們可能希望亞洲的使用者使用 SSO 承載，而應用程式要求的 UPN 格式為 *username@asia.contoso.com*。在此情況下，如果您選取 [使用者主體名稱]，預設會從 AAD 取得每位使用者的領域，可能是 *contoso.com*。因此，您可專門針對亞洲使用者，建立此承載並以值 *asia.contoso.com* 覆寫領域。現在使用者的 UPN 會變成 *username@asia.contoso.com*，而非 *username@contoso.com*。

- 如果您選取 [裝置識別碼]，Intune 會自動選取 Intune 裝置識別碼。

   根據預設，應用程式只需要使用裝置識別碼。 但如果您的應用程式在裝置識別碼之外還使用領域，您可以在 [領域] 文字方塊中鍵入領域。

   > [!NOTE]
   > 如果使用裝置識別碼，領域預設留白。

### <a name="url-prefixes-that-will-use-single-sign-on"></a>使用單一登入的 URL 首碼

在此鍵入存在於您組織中需要使用者驗證的任何 URL。

例如，當使用者連線到這些網站的任一個時，iOS 裝置會使用單一登入認證，使用者不需要輸入任何其他認證。 不過，如已啟用 Multi-Factor Authentication，使用者必須輸入第二道驗證。

> [!NOTE]
> 這些 URL 必須是格式正確的 FQDN。 Apple 要求它們的格式為 `http://<yourURL.domain>`

URL 的比對模式開頭必須是 `http://` 或 `https://`。 已執行簡單的字串比對，所以 URL 首碼 `http://www.contoso.com/` 與 `http://www.contoso.com:80/` 不符。 但使用 iOS 9.0 或更新版本，可使用單一萬用字元 \* 指定所有相符的值。 例如，`http://*.contoso.com/` 符合 `http://store.contoso.com/` 和 `http://www.contoso.com`。
模式 `http://.com` 和 `https://.com` 分別符合所有的 HTTP 和 HTTPS URL。

### <a name="apps-that-will-use-single-sign-on"></a>使用單一登入的應用程式

指出使用者裝置上哪個應用程式可以使用單一登入承載。

`AppIdentifierMatches` 陣列必須包含符合應用程式套件組合識別碼的字串。 這些字串可能是完全相符項目 (例如：`com.contoso.myapp`)，或者使用 \* 萬用字元指定套件組合識別碼首碼相符。 萬用字元必須出現在句號字元 (.) 之後，在字串結尾處，而且只能出現一次 (例如：`com.contoso.*`)。 包含萬用字元時，套件組合識別碼開頭為首碼的任何應用程式都會被授與帳戶存取權。

[應用程式名稱] 欄位用以新增使用者易記的名稱，以利識別套件組合識別碼。

### <a name="credential-renewal-certificate"></a>認證更新憑證

如果使用憑證 (不是密碼) 驗證您的使用者，則請使用此欄位選取部署至使用者當作驗證憑證的 SCEP 或 PFX 憑證。 一般而言，這和部署至使用者供 VPN、Wi-Fi 或電子郵件等使用的其他設定檔是相同的憑證。

## <a name="next-steps"></a>接下來的步驟

如需其他的裝置功能設定資訊，請參閱[如何在 Microsoft Intune 中設定裝置功能設定](device-features-configure.md)。

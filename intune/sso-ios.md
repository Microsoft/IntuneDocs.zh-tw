---
title: 在 Microsoft Intune 中新增 iOS 裝置的單一登入 - Azure | Microsoft Docs
description: 在 Microsoft Intune 中，建立、設定、允許或啟用 iOS 裝置，以使用單一登入 (SSO) 而非密碼，向您組織的資源和資料進行驗證。 若要使用 SSO，請建立裝置組態設定檔，並輸入 UPN、裝置識別碼、您的應用程式和憑證來驗證使用者和裝置。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/24/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: d1add113222c2aa7eaea10679c329e877b1a136f
ms.sourcegitcommit: 437eaf364c3b8a38d294397310c770ea4d8a8015
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2018
ms.locfileid: "49992004"
---
# <a name="use-single-sign-on-ios-device-in-microsoft-intune"></a>在 Microsoft Intune 中使用單一登入來登入 iOS 裝置

大部分的企業營運 (LOB) 應用程式需要某種程度的使用者驗證才會支援安全性。 在許多情況下，此驗證需要使用者多次輸入相同的認證，這很令人沮喪。 為改善使用者體驗，開發人員可以建立使用單一登入 (SSO) 的應用程式，減少使用者必須輸入認證的次數。

本文示範如何使用 Microsoft Intune 中的裝置組態設定檔為 iOS 裝置開啟單一登入。

## <a name="before-you-begin"></a>開始之前

請確定您已編碼應用程式，以在 iOS 裝置的單一登入承載中尋找使用者認證存放區。

## <a name="create-the-sso-profile"></a>建立 SSO 設定檔

1. 在 [Azure 入口網站](https://portal.azure.com)中，選取 [所有服務]，篩選 [Intune]，然後選取 [Microsoft Intune]。
2. 選擇 [裝置設定] > [設定檔] > [建立設定檔]。
3. 輸入下列設定：

    - **名稱**：輸入設定檔的名稱，例如 `ios sso profile`。
    - **描述**：輸入包含關鍵字詞的描述，以協助您在清單中尋找設定檔。
    - [平台]：選擇 [iOS]。
    - [設定檔類型]：選擇 [裝置功能]。

4. 選擇 [單一登入]。

    ![單一登入窗格](./media/sso-blade.png)

5. 輸入下列設定： 

    - **來自 AAD 的使用者名稱屬性**：Intune 會尋找 Azure AD 中每位使用者的這個屬性。 Intune 會接著填入個別欄位 (例如 UPN)，然後產生安裝在裝置上的 XML 承載。 選項包括：
    
        - **使用者主體名稱**：UPN 會以下列方式剖析：

            ![使用者名稱屬性](media/User-name-attribute.png)

            您也可以使用在 [領域] 文字方塊中輸入的文字覆寫領域。

            例如，Contoso 可能有歐洲、亞洲和北美洲等數個子地區。 他們可能希望亞洲的使用者使用 SSO 承載，而應用程式要求的 UPN 格式為 `username@asia.contoso.com`。 在此情況下，如果您選取 [使用者主體名稱]，預設會從 Azure AD 取得每位使用者的領域，可能是 *contoso.com*。 因此，您可專門針對亞洲使用者，建立此承載並以值 *asia.contoso.com* 覆寫領域。 現在終端使用者的 UPN 會變成 username@asia.contoso.com，而非 username@contoso.com。

        - **Intune 裝置識別碼**：Intune 會自動選取 Intune 裝置識別碼。 

            根據預設，應用程式只需要使用裝置識別碼。 但如果您的應用程式使用領域「和」裝置識別碼，您可以在 [領域] 文字方塊中鍵入領域。

            > [!NOTE]
            > 如果使用裝置識別碼，則領域預設為留白。

    - **領域**：URL 的網域部分。
    
    - **將會使用單一登入的 URL 首碼**：[新增] 您組織中需要使用者單一登入驗證的任何 URL。 

        例如，當使用者連線到這些網站的任一個時，iOS 裝置會使用單一登入認證。 使用者不需要輸入任何其他認證。 不過，如已啟用 Multi-Factor Authentication，使用者必須輸入第二道驗證。

        > [!NOTE]
        > 這些 URL 必須是格式正確的 FQDN。 Apple 要求 URL 的格式為 `http://<yourURL.domain>`。

        URL 的比對模式開頭必須是 `http://` 或 `https://`。 已執行簡單的字串比對，所以 URL 首碼 `http://www.contoso.com/` 與 `http://www.contoso.com:80/` 不符。 但使用 iOS 10.0 或更新版本，可使用單一萬用字元 \* 輸入所有相符的值。 例如，`http://*.contoso.com/` 符合 `http://store.contoso.com/` 和 `http://www.contoso.com`。

        模式 `http://.com` 和 `https://.com` 分別符合所有的 HTTP 和 HTTPS URL。
    
    - **將會使用單一登入的應用程式**：在終端使用者的裝置上，[新增] 可使用單一登入的應用程式。 

        `AppIdentifierMatches` 陣列必須包含符合應用程式套件組合識別碼的字串。 這些字串可能是完全相符項目 (例如 `com.contoso.myapp`)，您也可以使用 \* 萬用字元輸入與套件組合識別碼相符的首碼。 萬用字元必須出現在句號字元 (.) 之後，在字串結尾處，而且只能出現一次 (例如：`com.contoso.*`)。 包含萬用字元時，套件組合識別碼開頭為首碼的任何應用程式都會被授與帳戶存取權。

        使用 [應用程式名稱] 輸入使用者易記的名稱來協助您識別套件組合識別碼。
    
    - **認證更新憑證**：如果使用憑證進行驗證 (而非密碼)，請選取部署至使用者的 SCEP 或 PFX 憑證來當作驗證憑證。 一般而言，這和部署至使用者供 VPN、Wi-Fi 或電子郵件等使用的其他設定檔是相同憑證。

6. 選取 [確定] > [確定] > [建立] 以儲存您的變更，然後建立設定檔。 建立之後，它會顯示在 [裝置設定 - 設定檔] 清單中。 

## <a name="next-steps"></a>接下來的步驟

如需其他的裝置功能設定資訊，請參閱[如何在 Microsoft Intune 中設定裝置功能設定](device-features-configure.md)。

[指派此設定檔](device-profile-assign.md)給您的 iOS 裝置。

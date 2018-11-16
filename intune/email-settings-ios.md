---
title: Microsoft Intune 中 iOS 裝置的電子郵件設定- Azure | Microsoft Docs
description: 建立使用 Exchange Server 的裝置設定電子郵件設定檔，並從 Azure Active Directory 中擷取屬性。 您也可以在 iOS 裝置上使用 Microsoft Intune 來啟用 SSL、使用憑證或使用者名稱/密碼驗證使用者，以及同步處理電子郵件。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/05/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: a6fd10ab6a1e9dd7249e2ae1d4bf558d190276ed
ms.sourcegitcommit: b0ee8626191961dc07f9f7f9d8e6a5fb09c63350
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2018
ms.locfileid: "51505873"
---
# <a name="email-profile-settings-for-ios-devices---intune"></a>iOS 裝置的電子郵件設定檔設定 - Intune

請使用電子郵件設定檔設定來設定執行 iOS 的裝置。

> [!IMPORTANT]
> 我們已改進此文章中所述的一些 S/MIME 功能。 因此，S/MIME 功能已暫時從 Intune 移除。 當此功能推出時，我們將會移除此備註。

## <a name="email-settings"></a>電子郵件設定

- **電子郵件伺服器**：輸入 Exchange Server 的主機名稱。
- **帳戶名稱**：輸入電子郵件帳戶的顯示名稱。 此名稱會在其裝置上向使用者顯示。
- **AAD 中的使用者名稱屬性**：此名稱是 Intune 從 Azure Active Directory (AAD) 中取得的屬性。 Intune 會動態產生此設定檔所使用的使用者名稱。 選項包括：
  - **使用者主體名稱**：取得名稱，例如 `user1` 或 `user1@contoso.com`
  - **主要 SMTP 位址**：取得電子郵件地址格式的名稱，例如 `user1@contoso.com`
  - **SAM 帳戶名稱**：需要網域，例如 `domain\user1`。

    另請輸入：  
    - **使用者網域名稱來源**：選擇 [AAD] (Azure Active Directory) 或 [自訂]。

      選擇要從 [AAD] 取得屬性時，請輸入：
      - **AAD 中的使用者網域名稱屬性**：選擇取得使用者的 [完整網域名稱] 或 [NetBIOS 名稱] 屬性

      選擇使用 [自訂] 屬性時，請輸入：
      - **要使用的自訂網域名稱**：輸入 Intune 用於網域名稱的值，例如 `contoso.com` 或 `contoso`

- **AAD 中的電子郵件地址屬性**：選擇使用者電子郵件地址的產生方式。 選取 [使用者主體名稱] (`user1@contoso.com` 或 `user1`)，以使用完整主體名稱作為電子郵件地址。 選取 [主要 SMTP 位址] (`user1@contoso.com`)，以使用主要 SMTP 位址登入 Exchange。
- **驗證方法**：選取 [使用者名稱和密碼] 或 [憑證] 作為電子郵件設定檔所使用的驗證方法。 不支援 Azure Multi-Factor Authentication。
  - 若選取了 [憑證]，請選取先前所建立用於驗證 Exchange 連線的用戶端 SCEP 或 PKCS 憑證。
- **SSL**：[啟用] 會在傳送電子郵件、接收電子郵件以及與 Exchange Server 進行通訊時，使用安全通訊端層 (SSL) 通訊。
- **OAuth**：[啟用] 會在傳送電子郵件、接收電子郵件以及與 Exchange 進行通訊時，使用 Open Authorization (OAuth) 通訊。 如果您的 OAuth 伺服器使用憑證驗證，請選擇 [憑證] 作為 [驗證方法]，並在設定檔中包含憑證。 否則，請選擇 [使用者名稱和密碼] 作為 [驗證方法]。 使用 OAuth 時，請確定：

  - 確認您的電子郵件解決方案支援 OAuth，再將此設定檔目標設為您的使用者。 Office 365 Exchange Online 支援 OAuth。 內部部署 Exchange 和其他合作夥伴或協力廠商解決方案可能不支援 OAuth。 您可以設定內部部署 Exchange 進行新式驗證 (請參閱 [Announcing Hybrid Modern Authentication for Exchange On-Premises](https://blogs.technet.microsoft.com/exchange/2017/12/06/announcing-hybrid-modern-authentication-for-exchange-on-premises/) (宣告適用於 Exchange 內部部署的混合新式驗證) 部落格文章)。

    如果電子郵件設定檔使用 OAuth，但電子郵件服務並不支援，則 [重新輸入密碼] 選項會看似損毀。 例如，當使用者在 Apple 的裝置設定中選取 [重新輸入密碼] 時，不會發生任何事。

  - 啟用 OAuth 時，終端使用者會有支援 Multi-Factor Authentication (MFA) 的不同「新式驗證」電子郵件登入體驗。 

  - 某些組織會停用終端使用者執行[自助式應用程式存取](https://docs.microsoft.com/azure/active-directory/manage-apps/manage-self-service-access)的能力。 在此案例中，在系統管理員建立「iOS 帳戶」企業應用程式，並授與使用者存取 Azure AD 中的應用程式之前，新式驗證登入可能會失敗。

    預設動作是使用[應用程式存取面板](https://docs.microsoft.com/azure/active-directory/user-help/active-directory-saas-access-panel-introduction)的 [新增應用程式] 功能，而**不需要企業核准**。 如需詳細資訊，請參閱[將使用者指派至應用程式](https://docs.microsoft.com/azure/active-directory/manage-apps/ways-users-get-assigned-to-applications)。

  > [!NOTE]
  > 當您啟用 OAuth 時，會發生下列情況：  
  > 1. 會向已瞄準的裝置發出新設定檔。
  > 2. 終端使用者會收到提示，要求他們再次輸入認證。

- **S/MIME**：[啟用 S/MIME] 以使用 S/MIME 字串傳送外寄電子郵件。 啟用時，您也可以將能夠接收加密電子郵件之收件者的電子郵件加密，並解密從寄件者收到電子郵件。
  - 如果您選取 [憑證]，請選擇現有的 PKCS 憑證設定檔來驗證 Exchange 連線及/或加密電子郵件交換。
- **要同步處理的電子郵件數量**：選擇想要同步處理的電子郵件天數。 或者，選取 [無限制] 來同步處理所有可用的電子郵件。
- **允許將訊息移至其他電子郵件帳戶**：[啟用] 可讓使用者在使用者於其裝置上設定的不同帳戶之間移動電子郵件訊息。
- **允許從協力廠商應用程式傳送電子郵件**：[啟用] 可讓使用者選取此設定檔作為傳送電子郵件的預設帳戶。 它允許協力廠商應用程式在原生電子郵件應用程式中開啟電子郵件，例如將檔案附加至電子郵件。
- **同步最近使用的電子郵件地址**：[啟用] 可讓使用者將裝置上最近使用的電子郵件地址清單與伺服器同步。

## <a name="next-steps"></a>接下來的步驟
[設定 Intune 中的電子郵件設定](email-settings-configure.md)

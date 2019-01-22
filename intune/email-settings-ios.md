---
title: Microsoft Intune 中 iOS 裝置的電子郵件設定- Azure | Microsoft Docs
description: 了解您可以在 Microsoft Intune 中設定並新增至 iOS 裝置的所有電子郵件設定清單，包括使用 Exchange 伺服器，以及從 Azure Active Directory 取得屬性。 您也可以使用 Microsoft Intune 的裝置組態設定檔，在 iOS 裝置上啟用 SSL、使用憑證或使用者名稱/密碼來驗證使用者，以及同步電子郵件。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/11/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.openlocfilehash: c54ccf5bba53d5d638f011d3bd0d308adf6cb013
ms.sourcegitcommit: 4a7421470569ce4efe848633bd36d5946f44fc8d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2019
ms.locfileid: "54203360"
---
# <a name="email-profile-settings-for-ios-devices-in-intune"></a>Intune 中 iOS 裝置的電子郵件設定檔設定

在 Microsoft Intune 中，您可以建立並設定電子郵件連線到電子郵件伺服器、選擇使用者驗證的方式、使用 S/MIME 進行加密，以及執行更多作業。

本文列出並描述適用於執行 iOS 裝置的所有電子郵件設定。 您可以建立裝置組態設定檔，來將這些電子郵件設定推送或部署到您的 iOS 裝置。

## <a name="before-you-begin"></a>開始之前

[建立裝置組態設定檔](email-settings-configure.md#create-a-device-profile)。

## <a name="email-settings"></a>電子郵件設定

- **電子郵件伺服器**：輸入 Exchange Server 的主機名稱。
- **帳戶名稱**：輸入電子郵件帳戶的顯示名稱。 此名稱會在其裝置上向使用者顯示。
- **AAD 中的使用者名稱屬性**：此名稱是 Intune 從 Azure Active Directory (AAD) 中取得的屬性。 Intune 會動態產生此設定檔所使用的使用者名稱。 選項包括：
  - **使用者主體名稱**：取得名稱，例如 `user1` 或 `user1@contoso.com`
  - **主要 SMTP 位址**：取得電子郵件地址格式的名稱，例如 `user1@contoso.com`
  - **sAM 帳戶名稱**：需要網域，例如 `domain\user1`。

    另請輸入：  
    - **使用者網域名稱來源**：選擇 [AAD] (Azure Active Directory) 或 [自訂]。

      選擇要從 [AAD] 取得屬性時，請輸入：
      - **AAD 中的使用者網域名稱屬性**：選擇取得使用者的 [完整網域名稱] 或 [NetBIOS 名稱] 屬性

      選擇使用 [自訂] 屬性時，請輸入：
      - **要使用的自訂網域名稱**：輸入 Intune 用於網域名稱的值，例如 `contoso.com` 或 `contoso`

- **AAD 中的電子郵件地址屬性**：選擇使用者電子郵件地址的產生方式。 選取 [使用者主體名稱] (`user1@contoso.com` 或 `user1`)，以使用完整主體名稱作為電子郵件地址。 選取 [主要 SMTP 位址] (`user1@contoso.com`)，以使用主要 SMTP 位址登入 Exchange。
- **驗證方法**：選取 [使用者名稱和密碼] 或 [憑證] 作為電子郵件設定檔所使用的驗證方法。 不支援 Azure Multi-Factor Authentication。
  - 若選取了 [憑證]，請選取先前所建立用於驗證 Exchange 連線的用戶端 SCEP 或 PKCS 憑證。
- **SSL**：[啟用] 會在傳送電子郵件、接收電子郵件以及與 Exchange 伺服器進行通訊時，使用安全通訊端層 (SSL) 通訊。
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

- **S/MIME**：[啟用 S/MIME] 以允許使用者在 iOS 原生郵件應用程式中簽署及/或加密電子郵件。 

  當您對電子郵件訊息使用 S/MIME 時，您會確認寄件者的真確性，以及訊息的完整性和機密性。

  - **啟用 S/MIME 簽署**：選擇 [啟用] 以允許使用者為您所輸入帳戶的外寄電子郵件加上數位簽章。 簽署可協助接收訊息的使用者確定訊息是來自特定寄件者，而不是來自假冒該寄件者的其他人。 [停用] 則不允許使用者為訊息加上數位簽章。
    - **允許使用者變更設定**：選擇 [啟用] 以允許使用者變更 S/MIME 簽署行為。 [停用] 會防止使用者變更您所設定的 S/MIME 簽署設定。 適用於 iOS 12 和更新版本。

  - **S/MIME 簽署憑證**：選取用於簽署電子郵件訊息的現有 PKCS 或 SCEP 憑證設定檔。
    - **允許使用者變更設定**：選擇 [啟用] 以允許使用者變更簽署憑證。 [停用] 會防止使用者變更簽署憑證，並強制使用者使用您所設定的憑證。 適用於 iOS 12 和更新版本。

  - **預設為加密**：[啟用] 時，預設行為是加密所有訊息。 [停用] 時，預設行為是不加密所有訊息。
    - **允許使用者變更設定**：選擇 [啟用] 以允許使用者變更預設加密行為。 [停用] 會防止使用者變更加密預設行為，並強制使用者使用您所設定的設定。 適用於 iOS 12 和更新版本。

  - **強制執行個別訊息加密**：個別訊息加密可讓使用者在傳送電子郵件之前，選擇要加密哪些電子郵件。 選擇 [啟用] 可在建立新的電子郵件時，顯示個別訊息加密選項。 然後，使用者可以選擇加入或退出個別訊息加密。 [停用] 會防止顯示個別訊息加密選項。

    如果啟用 [預設為加密] 設定，則啟用個別訊息加密可讓使用者退出個別訊息加密。 如果停用 [預設為加密] 設定，則啟用個別訊息加密可讓使用者加入個別訊息加密。

  - **S/MIME 加密憑證**：選取用於加密電子郵件訊息的現有 PKCS 或 SCEP 憑證設定檔。
    - **允許使用者變更設定**：選擇 [啟用] 以允許使用者變更加密憑證。 [停用] 會防止使用者變更加密憑證，並強制使用者使用您所設定的憑證。 適用於 iOS 12 和更新版本。
- **要同步處理的電子郵件數量**：選擇您要同步電子郵件的天數。 或者，選取 [無限制] 來同步處理所有可用的電子郵件。
- **允許將訊息移至其他電子郵件帳戶**：[啟用] 可讓使用者在使用者於其裝置上設定的不同帳戶之間移動電子郵件訊息。
- **允許從協力廠商應用程式傳送電子郵件**：[啟用] 可讓使用者選取此設定檔作為傳送電子郵件的預設帳戶。 它允許協力廠商應用程式在原生電子郵件應用程式中開啟電子郵件，例如將檔案附加至電子郵件。
- **同步最近使用的電子郵件地址**：[啟用] 可讓使用者將裝置上最近使用的電子郵件地址清單與伺服器同步。

## <a name="next-steps"></a>後續步驟

設定檔已建立，但還不會執行任何動作。 接下來，[指派設定檔](device-profile-assign.md)並[監視其狀態](device-profile-monitor.md)。

在 [Android](email-settings-android.md)、[Windows 10](email-settings-windows-10.md) 和 [Windows Phone 8.1](email-settings-windows-phone-8-1.md) 裝置上設定電子郵件設定。

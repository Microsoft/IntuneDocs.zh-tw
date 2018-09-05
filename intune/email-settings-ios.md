---
title: Microsoft Intune 中 iOS 裝置的電子郵件設定- Azure | Microsoft Docs
description: 建立使用 Exchange Server 的裝置設定電子郵件設定檔，並從 Azure Active Directory 中擷取屬性。 您也可以在 iOS 裝置上使用 Microsoft Intune 來啟用 SSL、使用憑證或使用者名稱/密碼驗證使用者，以及同步處理電子郵件。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 8/21/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 2d27e90655e54051d73989202d2bc849a66208f5
ms.sourcegitcommit: 488be75cbee88455b33c68a3ec2acb864d461bf8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "41910797"
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

- **AAD 中的電子郵件地址屬性**：選擇使用者電子郵件地址的產生方式。 選取 [使用者主體名稱] (`user1@contoso.com` 或 `user1`)，使用完整主體名稱作為電子郵件地址，或選取 [主要 SMTP 位址] (`user1@contoso.com`)，使用主要 SMTP 位址以登入 Exchange。
- **驗證方法**：選取 [使用者名稱和密碼] 或 [憑證] 作為電子郵件設定檔所使用的驗證方法。 不支援 Azure Multi-Factor Authentication。
  - 若選取了 [憑證]，請選取先前所建立用於驗證 Exchange 連線的用戶端 SCEP 或 PKCS 憑證。
- **SSL**：[啟用] 以在傳送電子郵件、接收電子郵件以及與 Exchange Server 進行通訊時，使用安全通訊端層 (SSL) 通訊。
- **S/MIME**：[啟用 S/MIME] 以使用 S/MIME 字串傳送外寄電子郵件。 啟用時，您也可以將能夠接收加密電子郵件之收件者的電子郵件加密，並解密從寄件者收到電子郵件。
  - 若選取 [憑證]，請選取先前建立用來驗證 Exchange 連線的 PKCS 憑證設定檔，和/或加密電子郵件交換。
- **要同步處理的電子郵件數量**：選擇想要同步處理的電子郵件天數。 或者，選取 [無限制] 來同步處理所有可用的電子郵件。
- **允許將訊息移至其他電子郵件帳戶**：[啟用] 可讓使用者在其裝置上設定的不同帳戶之間移動電子郵件訊息。
- **允許從協力廠商應用程式傳送電子郵件**：[啟用] 以允許使用者選取此設定檔作為傳送電子郵件的預設帳戶，以及允許協力廠商的應用程式在原生電子郵件應用程式中開啟電子郵件；例如，將檔案附加至電子郵件。
- **同步最近使用的電子郵件地址**：[啟用] 可讓使用者將裝置上最近使用的電子郵件地址清單與伺服器同步。

## <a name="next-steps"></a>接下來的步驟
[設定 Intune 中的電子郵件設定](email-settings-configure.md)

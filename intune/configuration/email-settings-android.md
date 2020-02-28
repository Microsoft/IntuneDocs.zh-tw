---
title: Microsoft Intune 中的 Android 電子郵件設定 - Azure | Microsoft Docs
description: 建立使用 Exchange Server 的裝置設定電子郵件設定檔，並從 Azure Active Directory 中擷取屬性。 使用 Microsoft Intune，在 Android Samsung Knox 裝置上啟用 SSL 或 SMIME、使用憑證或使用者名稱/密碼來驗證使用者，以及同步處理電子郵件和排程。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/18/2020
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0a1bc53e0f05818b28bbd975e0de5cf5c9368afb
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/20/2020
ms.locfileid: "77512852"
---
# <a name="android-device-settings-to-configure-email-authentication-and-synchronization-in-intune"></a>在 Intune 中設定電子郵件、驗證及同步處理的 Android 裝置設定

本文列出並描述您可以在 Intune 中的 Android Samsung Knox 裝置上控制的不同電子郵件設定。 作為行動裝置管理 (MDM) 解決方案的一部分，請使用這些設定來設定電子郵件伺服器，使用 SSL 來加密電子郵件。

身為 Intune 系統管理員，您可以建立電子郵件設定並將其指派給 Android Samsung Knox Standard 裝置。

若要深入了解 Intune 中的電子郵件設定檔，請參閱[設定電子郵件設定](email-settings-configure.md)。

## <a name="before-you-begin"></a>開始之前

[建立裝置組態設定檔](email-settings-configure.md#create-a-device-profile)。

## <a name="android-samsung-knox"></a>Android (Samsung Knox)

- **電子郵件伺服器**：輸入 Exchange Server 的主機名稱。 例如，輸入 `outlook.office365.com`。
- **帳戶名稱**：輸入電子郵件帳戶的顯示名稱。 此名稱會在其裝置上向使用者顯示。
- **AAD 中的使用者名稱屬性**：此名稱是 Intune 從 Azure Active Directory (Azure AD) 中取得的屬性。 Intune 會動態產生此設定檔所使用的使用者名稱。 選項包括：
  - **使用者主體名稱**：取得名稱，例如 `user1` 或 `user1@contoso.com`
  - **使用者名稱**：只取得名稱，例如 `user1`
  - **sAM 帳戶名稱**：需要網域，例如 `domain\user1`。 SAM 帳戶名稱只能與 Android 裝置搭配使用。

    另請輸入：  
    - **使用者網域名稱來源**：選擇 [AAD]  (Azure Active Directory) 或 [自訂]  。

      選擇要從 [AAD]  取得屬性時，請輸入：
      - **AAD 中的使用者網域名稱屬性**：選擇取得使用者的 [完整網域名稱]  或 [NetBIOS 名稱]  屬性

      選擇使用 [自訂]  屬性時，請輸入：
      - **要使用的自訂網域名稱**：輸入 Intune 用於網域名稱的值，例如 `contoso.com` 或 `contoso`

- **AAD 中的電子郵件地址屬性**：此名稱是 Intune 從 Azure AD 取得的電子郵件屬性。 Intune 會動態產生此設定檔所使用的電子郵件地址。 選項包括：
  - **使用者主體名稱**：使用完整主體名稱 (例如 `user1@contoso.com` 或 `user1`) 作為電子郵件地址。
  - **主要 SMTP 位址**：使用主要 SMTP 位址 (例如 `user1@contoso.com`) 來登入 Exchange。

- **驗證方法**：選取 [使用者名稱和密碼]  或 [憑證]  作為電子郵件設定檔所使用的驗證方法。
  - 若要選取 [憑證]  ，請選取先前建立來驗證 Exchange 連線的用戶端 SCEP 或 PKCS 憑證設定檔。

### <a name="security-settings"></a>安全性設定

- **SSL**：傳送電子郵件、接收電子郵件以及與 Exchange Server 進行通訊時，請使用 Secure Sockets Layer (SSL) 通訊。
- **S/MIME**：使用 S/MIME 加密傳送外寄電子郵件。
  - 若要選取 [憑證]  ，請選取先前建立來驗證 Exchange 連線的用戶端 SCEP 或 PKCS 憑證設定檔。

### <a name="synchronization-settings"></a>同步處理設定

- **要同步處理的電子郵件數量**：選擇想要同步處理的電子郵件天數，或選取 [無限制]  來同步處理所有可用的電子郵件。
- **同步排程**：選取裝置用來同步處理 Exchange Server 資料的排程。 您也可以選取 [郵件送達時]  以在資料到達時同步處理資料，或 [手動]  \(使用此方式，裝置使用者必須啟動同步處理)。

### <a name="content-sync-settings"></a>內容同步設定

- **要同步處理的內容類型**：選取您想要在裝置上同步處理的內容類型。 [未設定]  會停用此設定。 設為 [未設定]  時，如果終端使用者在裝置上啟用同步處理，則會在裝置與 Intune 同步時再次停用同步處理，因為此原則已經過強化。 

  您可以同步處理下列內容：  
  - **連絡人**：選擇 [啟用]  以允許使用者將連絡人同步至其裝置。
  - **行事曆**：選擇 [啟用]  以允許使用者將行事曆同步至其裝置。
  - **工作**：選擇 [啟用]  以允許使用者將工作同步至其裝置。

## <a name="next-steps"></a>後續步驟

[指派設定檔](device-profile-assign.md)並[監視其狀態](device-profile-monitor.md)。

您也可以為 [Android Enterprise - 公司設定檔](email-settings-android-enterprise.md)、[iOS/iPadOS](email-settings-ios.md)、[Windows 10 與更新版本](email-settings-windows-10.md)與 [Windows Phone 8.1](email-settings-windows-phone-8-1.md) 建立電子郵件設定檔。

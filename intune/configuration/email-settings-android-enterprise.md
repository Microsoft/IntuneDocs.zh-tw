---
title: Microsoft Intune 中的 Android 企業電子郵件設定 - Azure | Microsoft Docs
description: 建立會使用 Exchange 伺服器，並從 Azure Active Directory 擷取屬性的裝置設定電子郵件設定檔。 使用 Microsoft Intune 在 Android 公司設定檔裝置上啟用 SSL 或 SMIME、使用憑證或使用者名稱/密碼來驗證使用者，以及同步處理電子郵件和排程。
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
ms.reviewer: maholdaa
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 978ddf279dc221a56fddaf99da4dbb2377a93c24
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/20/2020
ms.locfileid: "77511148"
---
# <a name="android-enterprise-device-settings-to-configure-email-authentication-and-synchronization-in-intune"></a>用以在 Intune 中設定電子郵件、驗證及同步處理的 Android 企業裝置設定



本文會列出並說明您可以在 Android 企業裝置上控制的不同電子郵件設定。 作為行動裝置管理 (MDM) 解決方案的一部分，請使用這些設定來設定電子郵件伺服器，使用 SSL 來加密電子郵件。

身為 Intune 系統管理員，您可以建立電子郵件設定並將其指派給公司設定檔中的 Android 企業裝置。

若要深入了解 Intune 中的電子郵件設定檔，請參閱[設定電子郵件設定](email-settings-configure.md)。

## <a name="before-you-begin"></a>開始之前

建立[裝置組態設定檔](email-settings-configure.md#create-a-device-profile) (選擇工作設定檔)，或建立[應用程式設定原則](../apps/app-configuration-policies-use-android.md)。

## <a name="android-enterprise"></a>Android 企業

- **電子郵件應用程式**：選取 **Gmail** 或 **Nine Work**
- **電子郵件伺服器**：Exchange Server 的主機名稱。 例如，輸入 `outlook.office365.com`。
- **AAD 中的使用者名稱屬性**：此名稱是 Intune 從 Azure Active Directory (Azure AD) 中取得的屬性。 Intune 會動態產生此設定檔所使用的使用者名稱。 選項包括：

  - **使用者主體名稱**：取得名稱，例如 `user1` 或 `user1@contoso.com`
  - **使用者名稱**：只取得名稱，例如 `user1`

- **AAD 中的電子郵件地址屬性**：此名稱是 Intune 從 Azure AD 取得的電子郵件屬性。 Intune 會動態產生此設定檔所使用的電子郵件地址。 選項包括：
  - **使用者主體名稱**：使用完整主體名稱 (例如 `user1@contoso.com` 或 `user1`) 作為電子郵件地址。
  - **主要 SMTP 位址**：使用主要 SMTP 位址 (例如 `user1@contoso.com`) 來登入 Exchange。

- **驗證方法**：選取 [使用者名稱及密碼]  或 [憑證]  作為電子郵件設定檔所使用的驗證方法。
  - 若要選取 [憑證]  ，請選取先前建立來驗證 Exchange 連線的用戶端 SCEP 或 PKCS 憑證設定檔。
- **SSL**：選擇 [啟用]  以在傳送電子郵件、接收電子郵件，以及與 Exchange 伺服器進行通訊時使用安全通訊端層 (SSL) 通訊。
- **要同步處理的電子郵件數量**：選擇您想要同步處理的電子郵件時間長度。 或者，選取 [無限制]  來同步處理所有可用的電子郵件。
- **要同步處理的內容類型** (僅限 Nine Work)：選擇您想要在裝置上同步哪些資料。 選項包括：
  - **連絡人**：選擇 [啟用]  以允許使用者將連絡人同步至其裝置。
  - **行事曆**：選擇 [啟用]  以允許使用者將行事曆同步至其裝置。
  - **工作**：選擇 [啟用]  以允許使用者將工作同步至其裝置。

## <a name="next-steps"></a>後續步驟

[指派設定檔](device-profile-assign.md)並[監視其狀態](device-profile-monitor.md)。

您也可以為 [Android Samsung Knox](email-settings-android.md)、[iOS/iPadOS](email-settings-ios.md)、[Windows 10 與更新版本](email-settings-windows-10.md)與 [Windows Phone 8.1](email-settings-windows-phone-8-1.md) 裝置建立電子郵件設定檔。

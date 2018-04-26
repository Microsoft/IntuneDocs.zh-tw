---
title: 執行 Android 和 Android for Work 之裝置的 Microsoft Intune 電子郵件設定
titleSuffix: ''
description: 了解有關可用於執行 Android 和 Android for Work 之裝置上設定電子郵件的 Microsoft Intune 設定。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/6/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: d492e107fffe730d36c662b9187fc9c6faced907
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="email-profile-settings-in-microsoft-intune-for-devices-running-android-and-android-for-work"></a>執行 Android 和 Android for Work 之裝置的 Microsoft Intune 電子郵件設定檔設定

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

本文展示您可為執行 Android 之裝置設定的電子郵件設定檔設定。

身為 Intune 系統管理員，您可以建立電子郵件設定並將其指派給下列 Android 裝置：
- [Android Samsung Knox Standard](#android-samsung-knox-standard-email-settings)
- [Android for Work](#android-for-work-email-settings)

## <a name="android-samsung-knox-standard-email-settings"></a>Android Samsung Knox Standard 電子郵件設定
- **電子郵件伺服器** - Exchange 伺服器的主機名稱。
- **帳戶名稱** - 在使用者裝置上顯示的電子郵件帳戶顯示名稱。
- **來自 AAD 的使用者名稱屬性** - 此名稱為 Active Directory (AD) 或 Azure AD 中的屬性，會用來產生此電子郵件設定檔的使用者名稱。 選取 [主要 SMTP 位址]，例如 user1@contoso.com 或 [使用者主體名稱]，像是 user1 或 user1@contoso.com。
- **AAD 的電子郵件地址屬性** - 每部裝置上產生使用者電子郵件地址的方式。 選取 [主要 SMTP 位址]，使用主要 SMTP 位址以登入 Exchange；或使用 [使用者主體名稱]，將完整主體名稱作為電子郵件地址。
- **驗證方法** - 選取 [使用者名稱和密碼] 或 [憑證]作為電子郵件設定檔所使用的驗證方法。
    - 若選取了 [憑證]，請選取先前建立來驗證 Exchange 連線的用戶端 SCEP 或 PKCS 憑證設定檔。

### <a name="security-settings"></a>安全性設定

- **SSL** - 傳送電子郵件、接收電子郵件以及與 Exchange Server 進行通訊時，請使用安全通訊端層 (SSL)。
- **S/MIME** - 使用 S/MIME 加密傳送外寄電子郵件。
    - 若選取了 [憑證]，請選取先前建立來驗證 Exchange 連線的用戶端 SCEP 或 PKCS 憑證設定檔。

### <a name="synchronization-settings"></a>同步處理設定

- **要同步處理的電子郵件數量** - 選擇想要同步處理的電子郵件天數，或選取 [無限制] 來同步處理所有可用的電子郵件。
- **同步排程** - 選取裝置用來同步處理 Exchange Server 資料的排程。 您也可以選取 [郵件送達時] 以在資料到達時同步處理資料，或 [手動] (使用此方式，裝置使用者必須啟動同步處理)。

### <a name="content-sync-settings"></a>內容同步設定

- **要同步處理的內容類型** - 選取想要同步至裝置的內容類型來源：
    - **連絡人**
    - **行事曆**
    - **工作**

## <a name="android-for-work-email-settings"></a>Android for Work 電子郵件設定

- **電子郵件應用程式** - 選取 [Gmail] 或 [Nine Work]
- **電子郵件伺服器** - Exchange 伺服器的主機名稱。
- **AAD 的使用者名稱屬性** - 此名稱是 Active Directory (AD) 或 Azure AD 中的屬性，會用來產生此電子郵件設定檔的使用者名稱。 選取 [主要 SMTP 位址]，例如 user1@contoso.com 或 [使用者主體名稱]，像是 user1 或 user1@contoso.com。
- **來自 AAD 的電子郵件地址屬性** - 選取每個裝置上產生使用者電子郵件地址的方式。 選取 [使用者主體名稱]，使用完整主體名稱作為電子郵件地址或**使用者名稱**。
- **驗證方法** - 選取 [使用者名稱和密碼] 或 [憑證] 作為電子郵件設定檔所使用的驗證方法。
    - 若選取了 [憑證]，請選取先前建立來驗證 Exchange 連線的用戶端 SCEP 或 PKCS 憑證設定檔。
- **SSL** - 傳送電子郵件、接收電子郵件以及與 Exchange Server 進行通訊時，請使用安全通訊端層 (SSL)。
- **要同步處理的電子郵件數量** - 選擇想要同步處理的電子郵件天數，或選取 [無限制] 來同步處理所有可用的電子郵件。
- **要同步處理的內容類型** (僅限 Nine Work) - 選取想要同步至裝置的內容類型來源：
    - **連絡人**
    - **行事曆**
    - **工作**

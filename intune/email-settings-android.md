---
title: "Android 和 Android for Work 裝置的 Intune 電子郵件設定"
titleSuffix: Azure portal
description: "了解可用於設定 Android 裝置上電子郵件連線的 Intune 設定。"
keywords: 
author: vhorne
ms.author: victorh
manager: angrobe
ms.date: 06/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4d3458cc-fcaa-4648-b13f-bf1f0616c1c5
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 0c793721cad40ea0f1662ae72ed334b98226c96d
ms.sourcegitcommit: 3b397b1dcb780e2f82a3d8fba693773f1a9fcde1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/12/2017
---
# <a name="email-profile-settings-for-android--devices-in-microsoft-intune"></a>Microsoft Intune 中 Android 裝置的電子郵件設定檔設定

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

身為 Intune 系統管理員，您可以建立電子郵件設定並將其指派給下列 Android 裝置：
- [Android Samsung KNOX Standard](#android-samsung-knox-standard-email-settings)
- [Android for Work](#android-for-work-email-settings)

## <a name="android-samsung-knox-standard-email-settings"></a>Android Samsung KNOX Standard 電子郵件設定
- **電子郵件伺服器** - Exchange 伺服器的主機名稱。
- **帳戶名稱** - 在使用者裝置上顯示的電子郵件帳戶顯示名稱。
- **來自 AAD 的使用者名稱屬性** - 此名稱為 Active Directory (AD) 或 Azure AD 中的屬性，會用來產生此電子郵件設定檔的使用者名稱。 選取 [主要 SMTP 位址]，例如 user1@contoso.com 或 [使用者主體名稱]，例如 user1 或 user1@contoso.com。
- **來自 AAD 的電子郵件地址屬性** - 選取每個裝置上產生使用者電子郵件地址的方式。 選取 [主要 SMTP 位址]，使用主要 SMTP 位址以登入 Exchange；或使用 [使用者主體名稱]，將完整主體名稱作為電子郵件地址。
- **驗證方法** - 選取 [使用者名稱和密碼] 或 [憑證]作為電子郵件設定檔所使用的驗證方法。
    - 若選取了 [憑證]，請選取先前建立來驗證 Exchange 連線的用戶端 SCEP 或 PKCS 憑證設定檔。

### <a name="security-settings"></a>安全性設定

- **SSL** - 傳送電子郵件、接收電子郵件以及與 Exchange Server 進行通訊時，請使用安全通訊端層 (SSL) 通訊。
- **S/MIME** - 使用 S/MIME 加密傳送外寄電子郵件。
    - 若選取了 [憑證]，請選取先前建立來驗證 Exchange 連線的用戶端 SCEP 或 PKCS 憑證設定檔。

### <a name="synchronization-settings"></a>同步處理設定

- **從要同步處理的電子郵件數量** - 選擇想要同步處理的電子郵件天數，或選取 [無限制] 來同步處理所有可用的電子郵件。
- **同步排程** - 選取裝置用來同步處理 Exchange Server 資料的排程。 您也可以選取 [郵件送達時] 以在資料到達時同步處理資料，或 [手動] (使用此方式，裝置使用者必須啟動同步處理)。

### <a name="content-sync-settings"></a>內容同步設定

- **要同步處理的內容類型** - 選取想要同步至裝置的內容類型來源：
    - **連絡人**
    - **行事曆**
    - **工作**

## <a name="android-for-work-email-settings"></a>Android for Work 電子郵件設定

- **電子郵件應用程式** - 選取 [Gmail] 或 [Nine Work]
- **電子郵件伺服器** - Exchange 伺服器的主機名稱。
- **來自 AAD 的使用者名稱屬性** - 此名稱是 Active Directory (AD) 或 Azure AD 中的屬性，將會用來產生此電子郵件設定檔的使用者名稱。 選取 [主要 SMTP 位址]，例如 user1@contoso.com 或 [使用者主體名稱]，例如 user1 或 user1@contoso.com。
- **來自 AAD 的電子郵件地址屬性** - 選取每個裝置上產生使用者電子郵件地址的方式。 選取 [使用者主體名稱]，使用完整主體名稱作為電子郵件地址或**使用者名稱**。
- **驗證方法** - 選取 [使用者名稱和密碼] 或 [憑證]作為電子郵件設定檔所使用的驗證方法。
    - 若選取了 [憑證]，請選取先前建立來驗證 Exchange 連線的用戶端 SCEP 或 PKCS 憑證設定檔。
- **SSL** - 傳送電子郵件、接收電子郵件以及與 Exchange Server 進行通訊時，請使用安全通訊端層 (SSL) 通訊。
- **從要同步處理的電子郵件數量** - 選擇想要同步處理的電子郵件天數，或選取 [無限制] 來同步處理所有可用的電子郵件。
- **要同步處理的內容類型** (僅限 Nine Work) - 選取想要同步至裝置的內容類型來源：
    - **連絡人**
    - **行事曆**
    - **工作**

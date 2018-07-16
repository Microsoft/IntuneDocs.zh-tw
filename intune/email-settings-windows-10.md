---
title: Microsoft Intune 中適用於 Windows 10 裝置的電子郵件設定 - Azure | Microsoft Docs
description: 建立使用 Exchange Server 的裝置設定電子郵件設定檔，並從 Azure Active Directory 中擷取屬性。 您也可以啟用 SSL，並在 Windows 10 裝置上使用 Microsoft Intune 同步處理電子郵件和排程。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 6/20/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 04834f21e5fd2f6ed0f7454988936397d3249987
ms.sourcegitcommit: 98b444468df3fb2a6e8977ce5eb9d238610d4398
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2018
ms.locfileid: "37904963"
---
# <a name="email-profile-settings-for-devices-running-windows-10---intune"></a>執行 Windows 10 之裝置的電子郵件設定檔設定 - Intune

請使用電子郵件設定檔設定，來設定執行 Windows 10 的裝置。

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

## <a name="security-settings"></a>安全性設定

- **SSL**：傳送電子郵件、接收電子郵件以及與 Exchange Server 進行通訊時，請使用安全通訊端層 (SSL) 通訊。

## <a name="synchronization-settings"></a>同步處理設定

- **要同步處理的電子郵件數量**：選擇想要同步處理的電子郵件天數。 或者，選取 [無限制] 來同步處理所有可用的電子郵件。
- **同步排程**：選取裝置用來同步處理 Exchange Server 資料的排程。您也可以選取 [郵件送達時] 以在資料到達時立即同步處理資料，或選取 [手動] (使用此方式，裝置使用者必須啟動同步處理)。

## <a name="content-sync-settings"></a>內容同步設定

- **要同步處理的內容類型**：選取想要同步至裝置的內容類型來源：
  - **連絡人**
  - **行事曆**
  - **工作**

## <a name="next-steps"></a>接下來的步驟
[設定 Intune 中的電子郵件設定](email-settings-configure.md)
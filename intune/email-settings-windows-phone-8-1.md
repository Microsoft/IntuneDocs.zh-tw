---
title: Windows Phone 8.1 的 Microsoft Intune 電子郵件設定
titleSuffix: ''
description: 了解可用於設定執行 Windows Phone 8.1 之裝置上電子郵件連線的 Intune 設定。
keywords: ''
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 3/6/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: a8d0ce028fbfa214240ce7973a2a0699a8c88a6a
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="email-profile-settings-in-microsoft-intune-for-devices-running-windows-phone-81"></a>在執行 Windows Phone 8.1 之裝置上的 Microsoft Intune 電子郵件設定檔設定

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

本文展示您可為執行 Windows Phone 8.1 之裝置設定的電子郵件設定檔設定。


- **將所有設定只套用至 Windows Phone 8.1**：此設定可以在 Intune 傳統入口網站中設定。 在 Azure 入口網站中，此設定無法變更。 若此值設定為 [已設定]，則所有設定只會套用到 Windows Phone 8.1 裝置。 若設定為 [未設定]，則這些設定也會套用於 Windows 10 行動裝置。
- **電子郵件伺服器** - Exchange 伺服器的主機名稱。
- **帳戶名稱** - 在使用者裝置上顯示的電子郵件帳戶顯示名稱。
- **AAD 的使用者名稱屬性** - 此為 Active Directory (AD) 或 Azure AD 中的屬性，可用以產生此電子郵件設定檔的使用者名稱。 選取 [主要 SMTP 位址]，例如 **user1@contoso.com** 或 [使用者主體名稱]，例如 **user1** 或 **user1@contoso.com**。
- **AAD 的電子郵件地址屬性** - 每部裝置上產生使用者電子郵件地址的方式。 選取 [主要 SMTP 位址]，使用主要 SMTP 位址來登入 Exchange；或使用 [使用者主體名稱]，將完整主體名稱作為電子郵件地址。


## <a name="security-settings"></a>安全性設定

- **SSL** - 傳送電子郵件、接收電子郵件以及與 Exchange Server 進行通訊時，請使用安全通訊端層 (SSL)。



## <a name="synchronization-settings"></a>同步處理設定

- **要同步處理的電子郵件數量** - 選擇想要同步處理的電子郵件天數，或選取 [無限制] 來同步處理所有可用的電子郵件。
- **同步排程** - 選取裝置用來同步處理 Exchange Server 資料的排程。 您也可以選取 [郵件送達時] 以在資料到達時立即同步處理資料，或 [手動 (使用此方式，裝置使用者必須啟動同步處理)]。

## <a name="content-sync-settings"></a>內容同步設定

- **要同步處理的內容類型** - 選取想要同步至裝置的內容類型來源：
    - **連絡人**
    - **行事曆**
    - **工作**

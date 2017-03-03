---
title: "Android 裝置的 Intune 電子郵件設定 | Intune Azure 預覽版 | Microsoft Docs"
description: "Intune Azure 預覽版︰了解您可用於設定 Android 裝置上電子郵件連線的 Intune 設定。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4d3458cc-fcaa-4648-b13f-bf1f0616c1c5
ms.reviewer: heenamac
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b4d095506215b775d56d172e9aabae1737757310
ms.openlocfilehash: 29a4346a04470192553ad2d4f0962a2a21d637ec
ms.lasthandoff: 02/16/2017


---

# <a name="email-profile-settings-for-android-devices-in-microsoft-intune"></a>Microsoft Intune 中 Android 裝置的電子郵件設定檔設定

[!INCLUDE[azure_preview](../includes/azure_preview.md)]



- **電子郵件伺服器** - Exchange 伺服器的主機名稱。
- **帳戶名稱** - 在使用者裝置上顯示的電子郵件帳戶顯示名稱。
- **來自 AAD 的使用者名稱屬** -Active Directory (AD) 或 Azure AD 中的這個屬性，將會用來產生此電子郵件設定檔的使用者名稱。 選取 [主要 SMTP 位址]，例如 user1@contoso.com 或 [使用者主體名稱]，例如 user1 或 user1@contoso.com。
- **來自 AAD 的電子郵件地址屬性** - 選取每個裝置上產生使用者電子郵件地址的方式。 選取 [主要 SMTP 位址]，使用主要 SMTP 位址來登入 Exchange；或使用 [使用者主體名稱]，將完整主體名稱作為電子郵件地址。
- **驗證方法** - 選取 [使用者名稱和密碼] 或 [憑證]作為電子郵件設定檔所使用的驗證方法。
    - 若選取了 [憑證]，請選取先前所建立的用戶端 SCEP 或 PKCS 憑證 (將用於驗證 Exchange 連線)。

## <a name="security-settings"></a>安全性設定

- **SSL** - 傳送電子郵件、接收電子郵件以及與 Exchange Server 進行通訊時，請使用安全通訊端層 (SSL) 通訊。
- **S/MIME** - 使用 S/MIME 加密傳送外寄電子郵件。
    - 若選取了 [憑證]，請選取先前所建立的用戶端 SCEP 或 PKCS 憑證 (將用於驗證 Exchange 連線)。

## <a name="synchronization-settings"></a>同步處理設定

- **從要同步處理的電子郵件數量** - 選擇想要同步處理的電子郵件天數，或選取 [無限制] 來同步處理所有可用的電子郵件。
- **同步排程** - 選取裝置用來同步處理 Exchange Server 資料的排程。 您也可以選取 [郵件送達時] 以在資料到達時立即同步處理資料，或 [手動 (使用此方式，裝置使用者必須啟動同步處理)]。

## <a name="content-sync-settings"></a>內容同步設定

- **要同步處理的內容類型** - 選取想要同步至裝置的內容類型來源：
    - **連絡人**
    - **行事曆**
    - **工作**


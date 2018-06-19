---
title: iOS 裝置的 Microsoft Intune 電子郵件設定
titleSuffix: ''
description: 了解可用於設定執行 iOS 之裝置上電子郵件設定的 Microsoft Intune 設定。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 5/10/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: fe791dce88878fdbde7c62e59452a53ac08ef06b
ms.sourcegitcommit: af0cc27b05bf0743f7d0970f5f3822f0aab346af
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/16/2018
ms.locfileid: "34190480"
---
# <a name="email-profile-settings-in-microsoft-intune-for-devices-running-ios"></a>在執行 iOS 之裝置上的 Microsoft Intune 電子郵件設定檔設定 

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

本文展示您可為執行 iOS 之裝置設定的電子郵件設定檔設定。

## <a name="email-settings"></a>電子郵件設定

- **電子郵件伺服器** - Exchange 伺服器的主機名稱。
- **帳戶名稱** - 在使用者裝置上顯示的電子郵件帳戶顯示名稱。
- **AAD 的使用者名稱屬性** - 此為 Active Directory (AD) 或 Azure AD 中的屬性，可用以產生此電子郵件設定檔的使用者名稱。 選取 [主要 SMTP 位址]，例如 **user1@contoso.com** 或 [使用者主體名稱]，例如 **user1** 或 **user1@contoso.com**。
- **AAD 的電子郵件地址屬性** - 每部裝置上產生使用者電子郵件地址的方式。 選取 [主要 SMTP 位址]，使用主要 SMTP 位址來登入 Exchange；或使用 [使用者主體名稱]，將完整主體名稱作為電子郵件地址。
- **驗證方法** - 選取 [使用者名稱和密碼] 或 [憑證] 作為電子郵件設定檔所使用的驗證方法 (**注意**：不支援 Azure 多重要素驗證)。
    - 若選取了 [憑證]，請選取先前所建立用於驗證 Exchange 連線的用戶端 SCEP 或 PKCS 憑證。
- **SSL** - 傳送電子郵件、接收電子郵件以及與 Exchange Server 進行通訊時，請使用安全通訊端層 (SSL)。
- **S/MIME** - 使用 S/MIME 簽署傳送外寄電子郵件。
    - 若選取 [憑證]，請選取先前建立用來驗證 Exchange 連線的 PKCS 憑證設定檔。
- **要同步處理的電子郵件數量** - 選擇想要同步處理的電子郵件天數，或選取 [無限制] 來同步處理所有可用的電子郵件。
- **允許將訊息移至其他電子郵件帳戶** - 其可讓使用者在其裝置上設定的不同帳戶之間，移動電子郵件訊息。
- **允許從協力廠商應用程式傳送電子郵件** - 允許使用者選取此設定檔作為傳送電子郵件的預設帳戶，以及允許協力廠商的應用程式在原生電子郵件應用程式中開啟開啟電子郵件，例如，將檔案附加至電子郵件。
- **同步最近使用過的電子郵件地址** - 使用者可利用此功能，將裝置上最近使用過的電子郵件地址清單，與伺服器同步。

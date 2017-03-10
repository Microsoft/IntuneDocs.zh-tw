---
title: "iOS 裝置的 Intune 電子郵件設定"
titleSuffix: Intune Azure preview
description: "Intune Azure 預覽版︰了解您可用於設定 iOS 裝置之電子郵件連線的 Intune 設定。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/24/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9f0fa6af-3669-439a-bd0d-75d8b1a0b135
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 78f99bba07180c06f979fec997a7bfb749d879c8
ms.openlocfilehash: f18fd3ceee5c73a96444092691c590c7d9a7419c
ms.lasthandoff: 02/24/2017


---

# <a name="email-profile-settings-for-ios-devices-in-microsoft-intune"></a>Microsoft Intune 中 iOS 裝置的電子郵件設定檔設定

[!INCLUDE[azure_preview](../includes/azure_preview.md)]



- **電子郵件伺服器** - Exchange 伺服器的主機名稱。
- **帳戶名稱** - 在使用者裝置上顯示的電子郵件帳戶顯示名稱。
- **來自 AAD 的使用者名稱屬** -Active Directory (AD) 或 Azure AD 中的這個屬性，將會用來產生此電子郵件設定檔的使用者名稱。 選取 [主要 SMTP 位址]，例如 **user1@contoso.com** 或 [使用者主體名稱]，例如 **user1** 或 **user1@contoso.com**。
- **來自 AAD 的電子郵件地址屬性** - 選取每個裝置上產生使用者電子郵件地址的方式。 選取 [主要 SMTP 位址]，使用主要 SMTP 位址來登入 Exchange；或使用 [使用者主體名稱]，將完整主體名稱作為電子郵件地址。
- **驗證方法** - 選取 [使用者名稱和密碼] 或 [憑證]作為電子郵件設定檔所使用的驗證方法。
    - 若選取了 [憑證]，請選取先前所建立的用戶端 SCEP 或 PKCS 憑證 (將用於驗證 Exchange 連線)。
- **SSL** - 傳送電子郵件、接收電子郵件以及與 Exchange Server 進行通訊時，請使用安全通訊端層 (SSL) 通訊。
- **S/MIME** - 使用 S/MIME 簽署傳送外寄電子郵件。
    - 若選取了 [憑證]，請選取先前所建立的用戶端 SCEP 或 PKCS 憑證 (將用於驗證 Exchange 連線)。
- **從要同步處理的電子郵件數量** - 選擇想要同步處理的電子郵件天數，或選取 [無限制] 來同步處理所有可用的電子郵件。
- **允許將訊息移至其他電子郵件帳戶** - 其可讓使用者在其裝置上設定的不同帳戶之間，移動電子郵件訊息。
- **允許從協力廠商應用程式傳送電子郵件** - 允許使用者選取此設定檔作為預設的帳戶來傳送電子郵件，以及允許在原生電子郵件應用程式中開啟協力廠商應用程式以開啟電子郵件，例如，將檔案附加至電子郵件。
- **同步最近使用過的電子郵件地址** - 使用者可利用此功能，將裝置上最近使用過的電子郵件地址清單，與伺服器同步。


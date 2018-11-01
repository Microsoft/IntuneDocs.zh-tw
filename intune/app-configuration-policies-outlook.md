---
title: Microsoft Intune 中 iOS 和 Android 裝置的 Outlook 設定
description: 建立設定原則，設定在 iOS 和 Android 裝置上執行的 Microsoft Outlook 設定。
keywords: ''
author: Erikre
ms.author: erikre
ms.reviewer: smithre4
manager: dougeby
ms.date: 10/04/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 24ed1a895dd3e4cad6111b40913b43fa9c6a3cec
ms.sourcegitcommit: 11bd3dbbc9dd762df7c6d20143f2171799712547
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/10/2018
ms.locfileid: "48903517"
---
# <a name="microsoft-outlook-configuration-settings"></a>Microsoft Outlook 組態設定 

使用設定原則，設定在 iOS 和 Android 裝置上執行的 Microsoft Outlook 設定。 

若要為受控 iOS 裝置建立應用程式設定原則，請參閱[為受控 iOS 裝置新增應用程式設定原則](app-configuration-policies-use-ios.md)。 若要為受控 Android 裝置建立應用程式設定原則，請參閱[為受控 Android 裝置新增應用程式設定原則](app-configuration-policies-use-android.md)。 

## <a name="configuration-settings"></a>組態設定

在 Intune 中新增設定原則時，您可以設定特定設定，來設定 Microsoft Outlook。 在 [組態設定] 窗格中，您可以設定電子郵件帳戶組態。

### <a name="basic-authentication-email-account-settings"></a>基本驗證電子郵件帳戶設定
適用於 iOS 和 Android 的 Outlook 可讓 Exchange 系統管理員將帳戶設定「推送」到其搭配 Exchange ActiveSync 通訊協定來使用基本驗證的內部部署使用者。 如需詳細資訊，請參閱[在適用於 iOS 和 Android 之 Outlook 中使用基本驗證的帳戶設定](https://docs.microsoft.com/Exchange/clients/outlook-for-ios-and-android/account-setup)。 若要啟用帳戶設定組態，您可以設定下列設定：

- **電子郵件伺服器**：輸入您內部部署 Exchange 伺服器的主機名稱 (例如：mail.contoso.com)。
- **電子郵件帳戶名稱**：輸入電子郵件帳戶的顯示名稱。 此名稱會在其裝置上向使用者顯示。
- **AAD 中的使用者名稱屬性**：此名稱是 Intune 從 Azure Active Directory (AAD) 取得的屬性。 Intune 會動態產生此設定檔所使用的使用者名稱。 選項包含：
  - **使用者主體名稱**：取得名稱，例如 `user1` 或 `user1@contoso.com`
  - **主要 SMTP 位址**：取得電子郵件地址格式的名稱，例如 `user1@contoso.com`
- **AAD 中的電子郵件地址屬性**：選擇使用者電子郵件地址的產生方式。 選取 [使用者主體名稱] (`user1@contoso.com` 或 `user1`)，使用完整主體名稱作為電子郵件地址，或選取 [主要 SMTP 位址] (`user1@contoso.com`)，使用主要 SMTP 位址以登入 Exchange。 建議項目是選取 [主要 SMTP 地址]。
- **帳戶網域**：(選擇性) 帳戶的網域。

## <a name="next-steps"></a>接下來的步驟
[設定 Intune 中的電子郵件設定](email-settings-configure.md)


---
title: "搭配 MAM CA 使用應用程式"
description: "了解 MAM CA 如何協助控制哪些應用程式可存取 O365 服務的概念。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 10/24/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 71dcf9bc-bfd1-4e06-b7ad-14b33a2288d0
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: e5dd7cb5b320df7f443b52a1b502027fa3c4acaf
ms.openlocfilehash: ee407827c1c4eb7b113d29c301da0b9fa08fa86d
ms.lasthandoff: 04/19/2017


---
# <a name="what-to-expect-when-using-an-app-with-app-based-ca"></a>搭配使用應用程式與應用程式 CA 時的預期狀況

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

應用程式 CA 會透過裝置上必須有的 Broker 應用程式，來驗證核准的應用程式身分識別：
*  在 **iOS** 上，**Azure Authenticator 應用程式**是 Broker 應用程式。
* 在 **Android** 上，**Intune 公司入口網站應用程式**是 Broker 應用程式。 

系統會提示第一次登入應用程式 CA 支援之應用程式 (例如 OneDrive 或 Outlook) 的使用者安裝 Broker 應用程式，並向 Azure AD 註冊裝置。 Azure AD 的裝置註冊 (之前稱為工作場所聯結) 會根據發行的權杖建立裝置記錄和憑證。  這與 **MDM 註冊****不同**。 不會套用任何管理設定檔，也不會清查裝置上的應用程式。  只有第一次使用受管理的應用程式時，才會安裝 Broker 應用程式並註冊裝置。

以下是直接衍生自裝置的內容清單：

* alternativeSecurityIds (Azure Active Directory 憑證指紋和公開金鑰雜湊)
* deviceOSType
* deviceOSVersion
* displayName

> [!NOTE]
> 在 Android 裝置上：
  * 裝置上必須安裝公司入口網站應用程式，但使用者不需登入應用程式。
  * 裝置註冊必須透過 OneDrive 或 Outlook 應用程式完成。

## <a name="to-remove-a-device-from-azure-ad-registration"></a>移除 Azure AD 註冊的裝置。
您可以透過 Azure AD 管理主控台移除裝置註冊，IT 系統管理員通常這麼做。  也可以讓使用者在裝置上進行。

* **Azure AD 管理主控台**︰在 Azure AD 管理主控台**，刪除您想要移除的裝置。
* **iOS 裝置**︰開啟 Azure Authenticator 應用程式，在帳戶向左撥動，然後選擇 [取消註冊]。  
* **Android 裝置**︰解除安裝公司入口網站應用程式，或從 [系統設定] 移除帳戶。

## <a name="app-based-ca-with-device-based-ca"></a>以應用程式為基礎的 CA 與以裝置為基礎的 CA  

您可以在 [Intune 系統管理員主控台](https://manage.microsoft.com)或 [Azure AD Premium 管理主控台] (https://manage.windowsazure.com) 上設定[以裝置相容性為基礎的條件式存取](restrict-access-to-email-and-o365-services-with-microsoft-intune.md) (**裝置 CA**)。 裝置 CA 要求使用者只透過符合 Intune 裝置相容性原則之受 Intune 管理的裝置或加入網域的電腦，來連線到 Exchange Online。  如果使用者屬於同時以應用程式 CA 和裝置 CA 原則為目標的一或多個安全性群組，使用者必須符合下列兩個需求之一：
* 用來存取服務的應用程式是下者所支援的行動裝置應用程式 
* ，且應用程式執行所在的裝置已安裝 **iOS Authenticator (適用於 iOS 裝置)** 或**公司入口網站應用程式 (適用於 Android 裝置)**。
* 用來存取服務的裝置**受 Intune 管理且符合** Intune 裝置相容性原則，或是**加入網域的電腦**。  以下是協助說明的一些範例：
  * 如果使用者嘗試從**原生 iOS 電子郵件應用程式**進行連線，因為應用程式 CA 不支援原生郵件應用程式，所以該使用者必須在**受管理和符合規範的裝置**上。
  * 如果使用者嘗試從 **Windows 家用電腦**進行連線，則會套用**裝置 CA 原則**，要求使用者必須使用加入網域的電腦。

## <a name="next-steps"></a>後續步驟
[建立 MAM 應用程式的 Exchange Online 原則](mam-ca-for-exchange-online.md)

[封鎖沒有新式驗證的應用程式](block-apps-with-no-modern-authentication.md)

### <a name="see-also"></a>請參閱

[使用應用程式保護原則保護應用程式資料](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md)


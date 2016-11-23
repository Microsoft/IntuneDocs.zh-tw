---
title: "搭配 MAM CA 使用應用程式 | Microsoft Intune"
description: "了解 MAM CA 如何協助控制哪些應用程式可存取 O365 服務的概念。"
keywords: 
author: karthikaraman
manager: angrobe
ms.date: 10/24/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 71dcf9bc-bfd1-4e06-b7ad-14b33a2288d0
ms.reviewer: chrisgre
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 5083cb49e7a98f19ff21c1972149b00aee4ec93e
ms.openlocfilehash: f93dc1d57e87b17bb949de8ad5476dd8abc364d0


---
# 搭配 MAM CA 使用應用程式時的預期狀況
MAM CA 會透過裝置上必須有的 Broker 應用程式，來驗證核准的應用程式識別：
*  在 **iOS** 上，**Azure Authenticator 應用程式**是 Broker 應用程式。
* 在 **Android** 上，**Intune 公司入口網站應用程式**是 Broker 應用程式。 

系統會提示第一次登入 MAM CA 支援之應用程式 (例如 OneDrive 或 Outlook) 的使用者安裝 Broker 應用程式，並向 Azure AD 註冊裝置。 Azure AD 的裝置註冊 (之前稱為工作場所聯結) 會根據發行的權杖建立裝置記錄和憑證。  這與 **MDM 註冊****不同**。 不會套用任何管理設定檔，也不會清查裝置上的應用程式。  只有第一次使用受管理的應用程式時，才會安裝 Broker 應用程式並註冊裝置。

以下是直接衍生自裝置的內容清單：

* alternativeSecurityIds (Azure Active Directory 憑證指紋和公開金鑰雜湊)
* deviceOSType
* deviceOSVersion
* displayName


## MAM CA 與以裝置相容性為基礎的條件式存取  

您可以在 [Intune 系統管理員主控台](https://manage.microsoft.com)或 [Azure AD Premium 管理主控台] (https://manage.windowsazure.com) 上設定[以裝置相容性為基礎的條件式存取](restrict-access-to-email-and-o365-services-with-microsoft-intune.md) (**裝置 CA**)。 裝置 CA 要求使用者只透過符合 Intune 裝置相容性原則之受 Intune 管理的裝置或加入網域的電腦，來連線到 Exchange Online。  如果使用者屬於同時以 MAM CA 和裝置 CA 原則為目標的一或多個安全性群組，使用者必須符合下列兩個需求之一：
* 用來存取服務的應用程式是 MAM CA 支援的行動裝置應用程式，且應用程式執行所在的裝置已安裝 **iOS Authenticator (適用於 iOS 裝置)** 或**公司入口網站應用程式 (適用於 Android 裝置)**。
* 用來存取服務的裝置**受 Intune 管理且符合** Intune 裝置相容性原則，或是**加入網域的電腦**。  以下是協助說明的一些範例：
  * 如果使用者嘗試從**原生 iOS 電子郵件應用程式**進行連線，由於 MAM CA 不支援原生郵件應用程式，因此該使用者必須在**受管理和相容的裝置**上。
  * 如果使用者嘗試從 **Windows 家用電腦**進行連線，則會套用**裝置 CA 原則**，要求使用者必須使用加入網域的電腦。




## 後續步驟
[建立 MAM 應用程式的 Exchange Online 原則](mam-ca-for-exchange-online.md)

[封鎖沒有新式驗證的應用程式](block-apps-with-no-modern-authentication.md)

### 請參閱

[使用 MAM 原則保護應用程式資料](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md)



<!--HONumber=Oct16_HO4-->



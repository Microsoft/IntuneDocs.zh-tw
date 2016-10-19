---
title: "對 O365 進行之以應用程式為基礎的條件式存取 | Microsoft Intune"
description: "了解 MAM CA 如何協助控制哪些應用程式可存取 O365 服務的概念。"
keywords: 
author: karthikaraman
manager: angrobe
ms.date: 10/15/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: bd6bee60-5e39-42c8-a2e9-f5865ac3573f
ms.reviewer: chrisgre
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 64eaba6918c4a5c7ccc39fb8ccfeae729a34ff4c
ms.openlocfilehash: a03faa57f9bf1ec6784f0b1ec2d41d3f4cd88a12


---

# 建立原則，只允許支援 Intune MAM 原則的行動裝置應用程式存取 Office 365 服務
[Intune 行動應用程式管理 (MAM) 原則](protect-apps-and-data-with-microsoft-intune.md)可協助您在向 Intune 註冊管理的裝置上保護公司資料。 您也可以在**未向 Intune 註冊管理之屬員工擁有的裝置**上，使用 MAM 原則。  在此情況下，即使未管理裝置，仍然需要確定公司資料和資源受到保護。 透過 MAM (MAM CA) 的條件式存取，您可以建立原則，只允許支援 Intune MAM 原則的行動裝置應用程式存取 Exchange Online 等 O365 服務。

例如，您可以藉由只允許 **Microsoft Outlook 應用程式**存取 Exchange Online，來**封鎖 iOS 和 Android 上的內建郵件應用程式**，這些應用程式從**Exchange Online** 取得電子郵件時，不會受到 Intune MAM 原則所提供的資料保護。

## 必要條件
設定 MAM CA 原則**之前**，您必須擁有 **Enterprise Mobility + Security 或 Azure Active Directory Premium 訂閱**，且使用者必須獲 EMS 或 Azure AD 授權。 如需詳細資訊，請參閱 [Enterprise Mobility 定價頁面](https://www.microsoft.com/en-us/cloud-platform/enterprise-mobility-pricing)或 [Azure Active Directory 定價頁面](https://azure.microsoft.com/en-us/pricing/details/active-directory/)。


## 支援的應用程式
**Exchange Online**
* Android 和 iOS 版 Microsoft Outlook

## 與其他條件式存取和驗證方法重疊
### MAM CA 與 Azure Active Directory 憑證式驗證

MAM CA 不能搭配 Azure Active Directory (Azure AD) 憑證式驗證使用。 您一次只能設定其中一個項目。
### MAM CA 與以裝置相容性為基礎的條件式存取  

您可以在 [Intune 系統管理員主控台](https://manage.microsoft.com)或 [Azure AD Premium 管理主控台] (https://manage.windowsazure.com) 上設定[以裝置相容性為基礎的條件式存取](restrict-access-to-email-and-o365-services-with-microsoft-intune.md) (**裝置 CA**)。 裝置 CA 要求使用者只透過符合 Intune 裝置相容性原則之受 Intune 管理的裝置或加入網域的電腦，來連線到 Exchange Online。  如果使用者屬於同時以 MAM CA 和裝置 CA 原則為目標的一或多個安全性群組，使用者必須符合下列兩個需求之一：
* 用來存取服務的應用程式是 MAM CA 支援的行動裝置應用程式，且應用程式執行所在的裝置已安裝 **iOS Authenticator (適用於 iOS 裝置)** 或**公司入口網站應用程式 (適用於 Android 裝置)**。
* 用來存取服務的裝置**受 Intune 管理且符合** Intune 裝置相容性原則，或是**加入網域的電腦**。  以下是協助說明的一些範例：
  * 如果使用者嘗試從**原生 iOS 電子郵件應用程式**進行連線，由於 MAM CA 不支援原生郵件應用程式，因此該使用者必須在**受管理和相容的裝置**上。
  * 如果使用者嘗試從 **Windows 家用電腦**進行連線，則會套用**裝置 CA 原則**，要求使用者必須使用加入網域的電腦。


## 搭配 MAM CA 使用應用程式時的預期狀況
MAM CA 會透過裝置上必須有的 Broker 應用程式，來驗證核准的應用程式識別：
*  在 **iOS** 上，**Azure Authenticator 應用程式**是 Broker 應用程式。
* 在 **Android** 上，**Intune 公司入口網站應用程式**是 Broker 應用程式。 

系統會提示第一次登入 MAM CA 支援之應用程式 (例如 OneDrive 或 Outlook) 的使用者安裝 Broker 應用程式，並向 Azure AD 註冊裝置。 Azure AD 的裝置註冊 (之前稱為工作場所聯結) 會根據發行的權杖建立裝置記錄和憑證。  這與 **MDM 註冊****不同**。 不會套用任何管理設定檔，也不會清查裝置上的應用程式。  只有第一次使用受管理的應用程式時，才會安裝 Broker 應用程式並註冊裝置。


## 後續步驟
[建立 MAM 應用程式的 Exchange Online 原則](mam-ca-for-exchange-online.md)

[封鎖沒有新式驗證的應用程式](block-apps-with-no-modern-authentication.md)

### 請參閱

[使用 MAM 原則保護應用程式資料](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md)



<!--HONumber=Oct16_HO2-->



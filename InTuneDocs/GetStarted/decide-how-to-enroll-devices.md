---
title: "選擇如何註冊行動裝置 | Microsoft Intune"
description: "回答一些簡單的問題，以決定如何在 Intune 中註冊行動裝置"
keywords: 
author: NathBarn
manager: angrobe
ms.date: 07/25/2016
ms.topic: article
ms.prod: 
ms.service: 
ms.technology: 
ms.assetid: cac62b64-3f8b-47ae-aa66-970c7ba15466
ms.reviewer: dagerrit
translationtype: Human Translation
ms.sourcegitcommit: c671610b9c56d8b92d126d9902cce9c8c689ed63
ms.openlocfilehash: 9f1612ffd9ab85e38058edb09870297a44b37c16


---

# 選擇如何註冊行動裝置

行動裝置註冊是由 Microsoft Intune 來管理智慧型手機、平板電腦和電腦的程序。 身為系統管理員，您需要決定如何根據下列項目來註冊裝置︰

 -  擁有權 (個人與 公司擁有的)
 -  使用方式 (共用與 個人)
 -  平台 (iOS、Android、Windows Phone、Windows 電腦、Mac 電腦)

下列問題的回答可協助您判斷所管理裝置的最佳註冊方法。

## **員工攜帶自己的裝置，還是由您的組織提供裝置？**

  - **使用者擁有的裝置** - "BYOD” (攜帶您自己的裝置) 註冊 - 使用者可以在裝置上安裝 Intune 公司入口網站應用程式然後進行註冊，以存取公司資源 (例如電子郵件、公司入口網站、公司資料和支援)。  

  - **公司擁有的裝置** - 根據組織需求和所管理裝置的類型，Intune 可以透過各種方式來註冊公司擁有的裝置 (COD)。

> [!div class="button"]
[BYOD 註冊 >](#what-byod-devices-can-your-users-enroll)   [COD 註冊 >](#are-your-company-owned-devices-shared-or-do-they-have-dedicated-users)

## **您的使用者可以註冊哪些 BYOD 裝置？**

> [!div class="button"]
[Android](/intune/deploy-use/set-up-android-management-with-microsoft-intune) [iOS 和 Mac](/intune/deploy-use/set-up-ios-and-mac-management-with-microsoft-intune) [Windows 10 行動裝置版和 Windows Phone](/intune/deploy-use/set-up-windows-phone-management-with-microsoft-intune) [Windows 電腦](/intune/deploy-use/set-up-windows-device-management-with-microsoft-intune)

## **您的公司所擁有的裝置是共用裝置，或是否有專用使用者？**

- **共用公司擁有的裝置** - 這些裝置沒有單一使用者，而且通常不會設定成存取電子郵件。 範例包括使用者視需要從集區取出然後傳回的 Kiosk 裝置或工作導向裝置。 建議的註冊方法取決於裝置平台。

- **使用者** - 發行給個別使用者的公司擁有裝置需要追蹤為公司資產，同時允許使用者將電子郵件和資料存取為個人裝置。 建議的註冊方法取決於裝置平台。

> [!div class="button"]
[共用 >](#what-operating-system-are-your-shared-devices-running)   [專用 >](#how-will-you-manage-dedicated-ios-devices)


## **您共用的裝置正在執行哪個作業系統？**

  > [!div class="button"]
  [Windows >](/intune/deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune) [Android >](/intune/deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune) [iOS >](#how-will-you-manage-shared-ios-devices)

## **您會如何管理共用的 iOS 裝置？**

- **Apple 的裝置註冊方案 (DEP)** - 使用註冊設定檔，可以將目標設為使用 DEP 所購買或管理的 iOS 裝置。 使用者第一次開啟裝置的電源時，裝置會下載 DEP 設定檔，並使用設定檔 DEP 進行註冊

- **Mac 上的 Apple Configurator** - Apple Configurator 是在 Mac 電腦上執行的 Apple 應用程式。 您可以使用 USB 纜線將 iOS 裝置連接至 Mac，以在裝置上安裝註冊設定檔。 如果您可以將裝置重設為原廠預設值來進行註冊，請使用 [設定助理] 註冊。 如果您不想將裝置重設為原廠預設值，請使用 [直接註冊]。

- **裝置註冊管理員** - Intune 的裝置註冊管理員 (DEM) 可讓管理員或系統管理員以單一使用者帳戶註冊許多行動裝置。 這些裝置不能有使用者親和性 (也就是專用使用者)，而且必須透過安裝並登入公司入口網站應用程式進行註冊。

  > [!div class="button"]
  [iOS DEP 註冊 >](/intune/deploy-use/ios-device-enrollment-program-in-microsoft-intune) [iOS 直接註冊 >](/intune/deploy-use/ios-direct-enrollment-in-microsoft-intune)  [DEM 註冊 >](/intune/deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune)。

## **您會如何管理專用的 iOS 裝置？**

您可以透過下列方式，向專用的使用者註冊公司所擁有的裝置︰

- **Apple 的裝置註冊方案 (DEP)** - 使用註冊設定檔，可以將目標設為使用 DEP 所購買或管理的 iOS 裝置。 使用者第一次開啟裝置的電源時，裝置會下載 DEP 設定檔，並向 Intune 註冊。

- **Mac 上的 Apple Configurator** - Apple Configurator 是在 Mac 電腦上執行的 Apple 應用程式。 您可以使用 USB 纜線將 iOS 裝置連接至 Mac，以在裝置上安裝註冊設定檔。 如果您可以將裝置重設為原廠預設值來進行註冊，請使用 [設定助理] 註冊。

- **以 IMEI 編號標記** - 匯入公司擁有之裝置的國際行動設備識別 (IMEI) 編號，以在 Intune 中將它們標記為公司擁有的裝置。 使用者接著可以安裝公司入口網站，以將他們的裝置註冊為個人裝置來存取公司資源 (例如電子郵件、應用程式和資料)。

  > [!div class="button"]
  [使用 IMEI 標記 >](/intune/deploy-use/specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers) [iOS DEP](/intune/deploy-use/ios-device-enrollment-program-in-microsoft-intune) [iOS 設定助理](/intune/deploy-use/ios-setup-assistant-enrollment-in-microsoft-intune) [使用 IMEI 標記](/intune/deploy-use/specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers)



<!--HONumber=Aug16_HO1-->



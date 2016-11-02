---
title: "選擇如何註冊行動裝置 | Microsoft Intune"
description: "回答一些簡單的問題，以決定如何在 Intune 中註冊行動裝置"
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 07/25/2016
ms.topic: article
ms.prod: 
ms.service: 
ms.technology: 
ms.assetid: cac62b64-3f8b-47ae-aa66-970c7ba15466
ms.reviewer: dagerrit
translationtype: Human Translation
ms.sourcegitcommit: 2c14071f5fb1a3604b897d6b2f81797d40bedc6d
ms.openlocfilehash: 1fd8495811e2cbcf4761707f2d1b705e49a240c6


---

# 選擇如何註冊行動裝置

下列問題的回答有助於判斷用來註冊所管理裝置的最佳方法。

## **員工攜帶自己的裝置，還是由您的組織提供裝置？**

  - **使用者所擁有的裝置** -「攜帶您自己的裝置」(BYOD) 註冊
  - **公司所擁有的裝置** - COD 註冊

> [!div class="button"]
[BYOD 註冊 >](#what-byod-devices-can-your-users-enroll)   
> [!div class="button"]
[COD 註冊 >](#are-your-company-owned-devices-shared-or-do-they-have-dedicated-users)

## **您的使用者可以註冊哪些 BYOD 裝置？**

> [!div class="button"]
[Android](/intune/deploy-use/set-up-android-management-with-microsoft-intune) [iOS 和 Mac](/intune/deploy-use/set-up-ios-and-mac-management-with-microsoft-intune) [Windows 10 行動裝置版和 Windows Phone](/intune/deploy-use/set-up-windows-phone-management-with-microsoft-intune) [Windows 電腦](/intune/deploy-use/set-up-windows-device-management-with-microsoft-intune)

## **公司所擁有的裝置是大家共用，還是屬於專用使用者？**

> [!div class="button"]
[共用 >](#what-operating-system-are-your-shared-devices-running)   [專用 >](#how-will-you-manage-dedicated-ios-devices)


## **您共用的裝置正在執行哪個作業系統？**

  > [!div class="button"]
  [Windows >](/intune/deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune) [Android >](/intune/deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune) [iOS >](#how-will-you-manage-shared-ios-devices)

## **您會如何管理共用的 iOS 裝置？**

  > [!div class="button"]
  [iOS DEP 註冊 >](/intune/deploy-use/ios-device-enrollment-program-in-microsoft-intune) [iOS 直接註冊 >](/intune/deploy-use/ios-direct-enrollment-in-microsoft-intune)  [DEM 註冊 >](/intune/deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune)

  - **Apple 的裝置註冊方案 (DEP)** - 透過 DEP 所購買或管理的 iOS 裝置可以和註冊設定檔建立關聯。 使用者第一次開啟裝置時，裝置會下載 DEP 設定檔，並使用設定檔 DEP 進行註冊。

  - **Mac 上的 Apple Configurator** - Apple Configurator 是在 Mac 電腦上執行的 Apple 應用程式。 您可以使用 USB 纜線將 iOS 裝置連接至 Mac，以在裝置上安裝註冊設定檔。 如果您可以將裝置重設為原廠預設值來進行註冊，請使用 [設定輔助程式註冊] 選項。 如果您不想將裝置重設為原廠預設值，請使用 [直接註冊] 選項。

  - **裝置註冊管理員 (Intune)** - Intune 的裝置註冊管理員 (DEM) 可讓管理員或系統管理員以單一使用者帳戶註冊許多行動裝置。 這些裝置不能有專用使用者 (使用者親和性)，而且必須安裝公司入口網站應用程式並登入以進行註冊。

## **您會如何管理專用的 iOS 裝置？**

  > [!div class="button"]
   [iOS DEP](/intune/deploy-use/ios-device-enrollment-program-in-microsoft-intune) [iOS 設定輔助程式](/intune/deploy-use/ios-setup-assistant-enrollment-in-microsoft-intune) [使用 IMEI 標記](/intune/deploy-use/specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers)

  您可以透過下列方式，向專用的使用者註冊公司所擁有的裝置︰

  - **Apple 的裝置註冊方案 (DEP)** - 透過 DEP 所購買或管理的 iOS 裝置可以和註冊設定檔建立關聯。 使用者第一次開啟裝置時，裝置會下載 DEP 設定檔，並向 Intune 註冊。

  - **Mac 上的 Apple Configurator** - Apple Configurator 是在 Mac 電腦上執行的 Apple 應用程式。 您可以使用 USB 纜線將 iOS 裝置連接至 Mac，以在裝置上安裝註冊設定檔。 如果您可以將裝置重設為原廠預設值來進行註冊，請使用 [設定輔助程式註冊] 選項。

  - **以 IMEI 編號標記** - 匯入公司擁有之裝置的國際行動設備識別 (IMEI) 編號，即可在 Intune 中將其標記為屬公司擁有的裝置。 接下來，使用者可以安裝公司入口網站，再將他們的裝置註冊為個人裝置，以存取公司資源 (例如電子郵件、應用程式和資料)。



<!--HONumber=Oct16_HO3-->



---
title: "選擇如何註冊行動裝置 | Microsoft Intune"
description: "回答一些簡單的問題，以決定如何在 Intune 中註冊行動裝置"
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 11/14/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ed9250aa-e894-4eac-92b8-5f1a3748e255
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: dagerrit
translationtype: Human Translation
ms.sourcegitcommit: 6adfb7375f9747f64e7037164f48918789bd7ee0
ms.openlocfilehash: 53c22143b5b367ed5732ed14fb06937d66489afa


---
# <a name="choose-how-to-enroll-mobile-devices"></a>選擇如何註冊行動裝置

下列一系列問題的回答可協助您判斷所管理裝置的最佳註冊方法。


## <a name="how-will-you-manage-shared-ios-devices"></a>**您會如何管理共用的 iOS 裝置？**

> [!div class="button"]
[iOS DEP 註冊 >](/intune/deploy-use/ios-device-enrollment-program-in-microsoft-intune)
> [!div class="button"]
[iOS 直接註冊 >](/intune/deploy-use/ios-direct-enrollment-in-microsoft-intune)
> [!div class="button"]
[DEM 註冊 >](/intune/deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune)

  - **Apple 的裝置註冊方案 (DEP)** - 使用註冊設定檔，可以將目標設為使用 DEP 所購買或管理的 iOS 裝置。 使用者第一次開啟裝置的電源時，裝置會下載 DEP 設定檔，並使用設定檔 DEP 進行註冊。

  - **Mac 上的 Apple Configurator** - Apple Configurator 是在 Mac 電腦上執行的 Apple 應用程式。 您可以使用 USB 纜線將 iOS 裝置連接至 Mac，以在裝置上安裝註冊設定檔。 如果您可以將裝置重設為原廠預設值來進行註冊，請使用 [設定助理] 註冊。 如果您不想將裝置重設為原廠預設值，請使用 [直接註冊]。

  - **裝置註冊管理員** - Intune 的裝置註冊管理員 (DEM) 可讓管理員或系統管理員以單一使用者帳戶註冊許多行動裝置。 這些裝置不能有使用者親和性 (也就是專用使用者)，而且必須透過安裝並登入公司入口網站應用程式進行註冊。

  > [!div class="button"]
  [< 返回](choose-how-to-enroll-devices3.md)



<!--HONumber=Dec16_HO2-->



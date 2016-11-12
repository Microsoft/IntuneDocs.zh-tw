---
title: "收集裝置記錄檔 | Microsoft Intune"
description: "了解如何收集受管理裝置的記錄檔。"
keywords: 
author: staciebarker
ms.author: staciebarker
manager: angrobe
ms.date: 10/18/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d97fb610-9d88-40e5-bb06-447eec533630
ms.reviewer: esmich
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 3a081109cd499d3bdda75cb6c8a4dab9d9d28fab
ms.openlocfilehash: ec7d522e8dcff66d1b84fed3c4c0cc708e555e67


---

# <a name="device-logs"></a>裝置記錄檔

進行疑難排解時，您可能想要從使用者裝置收集記錄檔。 這裡說明收集這些記錄檔的指示。 通常，您可能需要存取裝置，或向使用者要求它們收集記錄檔，並將它們傳送給您。

### <a name="android-log-location"></a>Android 記錄檔位置
Android 記錄檔位於 *<Android Device>\Phone\Android\data\com.microsoft.windowsintune.companyportal\files* 中。 使用者也可以透過電子郵件傳送您的記錄檔 (如[使用電子郵件將 Android 診斷資料記錄檔傳送給 IT 系統管理員](/intune/enduser/send-diagnostic-data-logs-to-your-it-administrator-using-email-android)中所述)。

### <a name="ios-logs"></a>iOS 記錄檔

使用者可以將註冊錯誤傳送給您 (如[將 iOS 註冊錯誤傳送給 IT 系統管理員](/intune/enduser/send-errors-to-your-it-admin-ios)中所述)。

### <a name="mac-os-x-devices"></a>Mac OS X 裝置

1. 開啟 **[主控台]** 應用程式。
2. 在 **[檔案]** 下，選擇 **[system.log]**。
3. 在頂端的功能表列中，選擇 **[檔案]** > **[Save a Copy As]** (將複本另存為)， 然後儲存檔案。

### <a name="windows-phone"></a>Windows Phone

在 **Windows Phone 公司入口網站**中，使用者必須選擇 **[…]** 存取功能表，然後選擇 **[傳送記錄檔]**。 登入入口網站之前和之後，都能使用這個選項。

### <a name="windows"></a>Windows

針對 Windows 公司入口網站，記錄檔位於 *%localappdata%\Packages\Microsoft.CompanyPortal_8wekyb3d8bbwe\LocalState* 中。



<!--HONumber=Oct16_HO3-->



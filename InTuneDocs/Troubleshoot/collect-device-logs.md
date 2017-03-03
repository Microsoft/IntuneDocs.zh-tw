---
title: "收集裝置記錄檔| Microsoft Docs"
description: "了解如何收集受管理裝置的記錄檔。"
keywords: 
author: staciebarker
ms.author: staciebarker
manager: angrobe
ms.date: 02/07/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d97fb610-9d88-40e5-bb06-447eec533630
ms.reviewer: esmich
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 211b996263aae7a42f8370eb343c7e759ef87790
ms.openlocfilehash: 5aae8edd2b851eb94156e82bc9b6e604644cb900


---

# <a name="device-logs"></a>裝置記錄檔

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

進行疑難排解時，您可能想要從使用者裝置收集記錄檔。 這裡說明收集這些記錄檔的指示。 通常您需要存取裝置來取得這些記錄檔，或要求使用者收集記錄檔，並將記錄檔傳送給您。

### <a name="android-logs"></a>Android 記錄
Android 記錄檔位於 *<Android Device>\Phone\Android\data\com.microsoft.windowsintune.companyportal\files* 中。

檔案有時不會顯示，尤其是在較新的 Android 裝置上。 若是發生這種情況，請讓您的使用者開啟 Android 的公司入口網站應用程式。 然後他們應該選擇 [設定]>[複製記錄]，然後重新啟動裝置。

如需使用者如何傳送資料記錄的詳細資訊，請參閱下列文章：

- [使用詳細資訊記錄來協助 IT 系統管理員修正裝置問題](/intune/enduser/use-verbose-logging-to-help-your-it-administrator-fix-device-issues-android)：描述使用者如何開啟詳細資訊記錄，以自動傳送所有資料記錄給您。 根據預設，詳細資訊記錄為開啟狀態。

- [使用電子郵件將 Android 診斷資料記錄傳送給 IT 系統管理員](/intune/enduser/send-logs-to-your-it-admin-by-email-android)

- [使用 USB 纜線將診斷資料記錄傳送給 IT 系統管理員](/intune/enduser/send-diagnostic-data-logs-to-your-it-administrator-using-a-usb-cable-android)

### <a name="ios-logs"></a>iOS 記錄檔

使用者可以將註冊錯誤傳送給您，如[將 iOS 註冊錯誤傳送給 IT 系統管理員](/intune/enduser/send-errors-to-your-it-admin-ios)中所述。

### <a name="mac-os-x-logs"></a>Mac OS X 記錄

1. 開啟 **[主控台]** 應用程式。
2. 在 [檔案] 下，選擇 [system.log]。
3. 在頂端的功能表列中，選擇 [檔案] >  [Save a Copy As] (將複本另存為)。 然後儲存檔案。

### <a name="windows-phone"></a>Windows Phone

在 Windows Phone 公司入口網站應用程式中，使用者可以選擇三個點 (**…**) 來存取功能表，然後選擇 [傳送記錄]。 在登入公司入口網站應用程式前後，都能使用這個選項。

### <a name="windows"></a>Windows

若是 Windows 公司入口網站，記錄位於 *%localappdata%\Packages\Microsoft.CompanyPortal_8wekyb3d8bbwe\LocalState*。



<!--HONumber=Feb17_HO2-->



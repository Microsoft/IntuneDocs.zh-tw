---
title: "如果您安裝公司入口網站應用程式並在 Intune 註冊您的裝置，會發生什麼情況？ | Microsoft Intune"
description: 
keywords: 
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d65e3452-5bbf-4d26-a06e-401ddcc47f39
ms.reviewer: priyar
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: e52ebdd62ca68f1d9226def654961075400184a8
ms.openlocfilehash: e2da1f39d0cfe05bb0ea1c149c91e5ff82312c01


---


# 如果您安裝公司入口網站應用程式並在 Intune 註冊您的裝置，會發生什麼情況？

若要了解當您安裝公司入口網站應用程式並註冊您的裝置時會發生什麼情況，請使用符合您使用之裝置的連結，如上述＜在本文中＞一節所示。 如需 Windows 10 裝置的資訊，請參閱[本頁](what-happens-if-you-install-the-company-portal-app-and-enroll-your-device-in-intune-windows10.md)。

## Windows 8.1 和 Windows RT
當您安裝公司入口網站應用程式，然後使用該應用程式在 Intune 註冊您的 Windows 8.1 企業版或專業版或 Windows RT 裝置時，公司入口網站應用程式會執行下列動作：

-   存取公司網路、電子郵件和工作檔案

-   從公司入口網站取得公司應用程式

-   自動設定公司電子郵件帳戶

-   如果電話遺失或遭竊即重設為原廠設定

如需註冊的步驟，請參閱[在 Intune 中註冊您的 Windows 裝置](enroll-your-device-in-intune-windows.md)。 若要了解 IT 系統管理員可以在您的裝置上看到什麼內容，請參閱[當我在 Intune 註冊裝置時，我的 IT 系統管理員會看到什麼內容？](what-can-your-it-administrator-see-when-you-enroll-your-device-in-intune-windows.md)

新增電腦時：

-   軟體會安裝在您的電腦上，讓 IT 系統管理員可以管理電腦，同時讓您可以取得公司資源，例如應用程式和支援資訊。 您的 IT 系統管理員可能會自動更新此軟體。

-   Intune Endpoint Protection 可能會安裝在您的電腦上。 這是用來檢查病毒和惡意程式碼的軟體。

-   IT 系統管理員可以清查安裝在電腦上的所有軟體，包括您個人安裝的軟體。

-   系統可能會要求您接受條款和條件。

-   IT 系統管理員可以收集或刪除電腦硬碟上的資料。 IT 系統管理員也可以刪除整個硬碟。

-   IT 系統管理員可以在電腦上安裝應用程式和更新。

-   IT 系統管理員可以在電腦上強制執行原則。 例如，您可能必須在電腦上設定密碼或 PIN；如果不正確的密碼嘗試次數過多，系統可能會鎖定您的電腦存取權，或是刪除電腦硬碟上的所有資料。

## Windows Phone 8.1 和 Windows Phone 8
當您安裝公司入口網站應用程式，然後使用該應用程式在 Intune 註冊您的 Windows Phone 8.1 或 Windows Phone 8 裝置時，公司入口網站應用程式會執行下列動作：

-   存取公司網路、電子郵件和工作檔案

-   從公司入口網站取得公司應用程式

-   自動設定公司電子郵件帳戶

-   如果電話遺失或遭竊即重設為原廠設定

如需註冊的步驟，請參閱[在 Intune 中註冊您的 Windows 裝置](enroll-your-device-in-intune-windows.md)。 若要了解 IT 系統管理員可以在您的裝置上看到什麼內容，請參閱[當我在 Intune 註冊裝置時，我的 IT 系統管理員會看到什麼內容？](what-can-your-it-administrator-see-when-you-enroll-your-device-in-intune-windows.md)

當您新增 Windows Phone 裝置時，您會賦予 IT 系統管理員存取裝置的權限。 IT 系統管理員可以執行下列作業：

-   將裝置重設為製造商的預設設定。 這項功能對裝置遺失或失竊的情況很有幫助。

-   移除所有公司相關資料和已安裝的商務應用程式。 不會移除您的個人資料和設定。

-   強制要求您在裝置上設定密碼或 PIN；如果不正確的密碼嘗試次數過多，系統可能會鎖定您的裝置存取權，或是將裝置重設為製造商的預設設定 (可能包括刪除資料)。

-   強制加密裝置上的所有資料。 如果裝置遺失或失竊，這將可幫助您保護資料。

-   要求您接受條款和條件。

-   停用 SD 卡。

-   在裝置上安裝應用程式的更新。 這只適用於更新。 IT 系統管理員不能在裝置上強制安裝新應用程式，但是您可以選擇安裝公司入口網站上顯示的應用程式。

-   在裝置新增到公司入口網站之後，大約每隔 8 個小時裝置會：

    -   下載 IT 系統管理員提供的任何原則或應用程式更新。

    -   傳送任何硬體清查更新。

    -   傳送任何公司應用程式清查更新。

## Windows 7 和 Vista
當您安裝公司入口網站應用程式，然後使用該應用程式在 Intune 註冊您的 Windows 7 或 Vista 裝置時，公司入口網站應用程式會執行下列動作：

-   存取公司網路、電子郵件和工作檔案

-   從公司入口網站取得公司應用程式

-   自動設定公司電子郵件帳戶

-   如果電話遺失或遭竊即重設為原廠設定

若要了解 IT 系統管理員可以在您的裝置上看到什麼內容，請參閱[當我在 Intune 註冊裝置時，我的 IT 系統管理員會看到什麼內容？](what-can-your-it-administrator-see-when-you-enroll-your-device-in-intune-windows.md)

新增電腦時：

-   軟體會安裝在您的電腦上，讓 IT 系統管理員可以管理電腦，同時讓您可以取得公司資源，例如應用程式和支援資訊。 您的 IT 系統管理員可能會自動更新此軟體。

-   Intune Endpoint Protection 可能會安裝在您的電腦上。 這是用來檢查病毒和惡意程式碼的軟體。

-   IT 系統管理員可以清查安裝在電腦上的所有軟體，包括您個人安裝的軟體。

-   系統可能會要求您接受條款和條件。

-   IT 系統管理員可以收集或刪除電腦硬碟上的資料。 IT 系統管理員也可以刪除整個硬碟。

-   IT 系統管理員可以在電腦上安裝應用程式和更新。

-   IT 系統管理員可以在電腦上強制執行原則。 例如，您可能必須在電腦上設定密碼或 PIN；如果不正確的密碼嘗試次數過多，系統可能會鎖定您的電腦存取權，或是刪除電腦硬碟上的所有資料。

如有任何問題，請連絡您的 IT 系統管理員。 如需其連絡資訊，請查看[公司入口網站](http://portal.manage.microsoft.com)。

### 請參閱
[使用具有 Intune 的 Windows 裝置](using-your-windows-device-with-intune.md)



<!--HONumber=Jun16_HO4-->



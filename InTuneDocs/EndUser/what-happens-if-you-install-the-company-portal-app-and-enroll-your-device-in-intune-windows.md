---
title: "如果您安裝公司入口網站應用程式並在 Intune 註冊您的 Windows 裝置，會發生什麼情況？ | Microsoft Intune"
description: 
keywords: 
author: Staciebarker
manager: angrobe
ms.date: 7/8/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d65e3452-5bbf-4d26-a06e-401ddcc47f39
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: priyar
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: d3a2daebdb781ce99aa103e7717ffa1b0297cb3a
ms.openlocfilehash: 840d985fd2c4771831f722cdff214026a383f606


---


# 如果您安裝公司入口網站應用程式並在 Intune 註冊您的 Windows 裝置，會發生什麼情況？

當您安裝公司入口網站應用程式，並使用它來註冊 Windows 或 Windows Phone 裝置時，您將允許您的 IT 系統管理員管理您的裝置以保護公司或學校資料的安全性，如下方針對早於 Windows 10 之裝置的描述。 如需 Windows 10 裝置的資訊，請參閱[本頁](what-happens-if-you-install-the-company-portal-app-and-enroll-your-device-in-intune-windows10.md)。

## 所有 Windows 裝置在註冊後會發生的事
當您在 Intune 註冊您的 Windows 或 Windows Phone 裝置，您可以：

-   存取公司網路、電子郵件和工作檔案

-   從公司入口網站取得公司應用程式 (針對 Windows 7 和 Vista，您只能從公司入口網站取得公司應用程式)

-   自動設定公司或學校電子郵件帳戶

-   如果電話遺失或遭竊即重設為原廠設定

當您註冊裝置時，您會賦予 IT 系統管理員執行下列動作的權限：

-   將裝置重設為製造商的預設設定。 這項功能對裝置遺失或失竊的情況很有幫助。

-   移除所有公司相關資料和已安裝的商務應用程式。 不會移除您的個人資料和設定。

-   IT 系統管理員可以清查安裝在電腦上的所有軟體，包括您個人安裝的軟體。

-   強制要求您在裝置上設定密碼或 PIN；如果不正確的密碼嘗試次數過多，系統可能會鎖定您的裝置存取權，或是將裝置重設為製造商的預設設定 (可能包括刪除資料)。

-   強制將裝置上所有資料進行加密，這將能在裝置遺失或遭竊的情況下協助保護資料。

-   要求您接受條款和條件。

-   IT 系統管理員可以在電腦上強制執行原則。 例如，您可能必須在電腦上設定密碼或 PIN；如果不正確的密碼嘗試次數過多，系統可能會鎖定您的電腦存取權，或是刪除電腦硬碟上的所有資料。

-   停用 SD 卡。

## 所有 Windows 電腦在註冊後會發生的事

-  軟體會安裝在您的電腦上，讓 IT 系統管理員可以管理電腦，同時讓您可以取得公司資源，例如應用程式和支援資訊。 您的 IT 系統管理員可能會自動更新此軟體。

-  Intune Endpoint Protection 可能會安裝在您的電腦上。 這是用來檢查病毒和惡意程式碼的軟體。

-  IT 系統管理員可以清查安裝在電腦上的所有軟體，包括您個人安裝的軟體。

-  系統可能會要求您接受條款和條件。

-  IT 系統管理員可以收集或刪除電腦硬碟上的資料。 IT 系統管理員也可以刪除整個硬碟。

-  IT 系統管理員可以在電腦上安裝應用程式和更新。

-  IT 系統管理員可以在電腦上強制執行原則。 例如，您可能必須在電腦上設定密碼或 PIN；如果不正確的密碼嘗試次數過多，系統可能會鎖定您的電腦存取權，或是刪除電腦硬碟上的所有資料。


## 在註冊裝置後每隔八小時會發生的事
已註冊的裝置每隔大約八小時將會：

-   下載 IT 系統管理員提供的任何原則或應用程式更新。

-   傳送任何硬體清查更新。

-   傳送任何公司應用程式清查更新。

如需註冊的步驟，請參閱[在 Intune 中註冊您的 Windows 裝置](enroll-your-device-in-intune-windows.md)。 若要了解 IT 系統管理員可以在您的裝置上看到什麼內容，請參閱[當我在 Intune 註冊裝置時，我的 IT 系統管理員會看到什麼內容？](what-can-your-it-administrator-see-when-you-enroll-your-device-in-intune-windows.md)

如有任何問題，請連絡您的 IT 系統管理員。 如需其連絡資訊，請查看[公司入口網站](http://portal.manage.microsoft.com)。

### 請參閱
[使用具有 Intune 的 Windows 裝置](using-your-windows-device-with-intune.md)



<!--HONumber=Aug16_HO4-->



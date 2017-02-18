---
title: "安裝 Windows 的公司入口網站應用程式 | Microsoft Docs"
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 01/23/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d65e3452-5bbf-4d26-a06e-401ddcc47f39
searchScope:
- Company Portal
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: priyar
ms.suite: ems
ms.custom: intune-enduser
translationtype: Human Translation
ms.sourcegitcommit: a87fe0cf9591040f1455d71b1f40cd0705ba8abf
ms.openlocfilehash: 7a4b5acea4a4bdce32c42ca33f81778965ee1abb


---


# <a name="what-happens-if-you-install-the-company-portal-app-and-enroll-your-windows-device-in-intune"></a>如果您安裝公司入口網站應用程式並在 Intune 註冊您的 Windows 裝置，會發生什麼情況？

當您安裝公司入口網站應用程式，然後使用其註冊 Windows 或 Windows Phone 裝置時，即授權您的 IT 系統管理員可以管理您的裝置來協助保護公司或學校資料的安全。 本主題說明 Windows 10 之前的裝置行為。 若為 Windows 10 裝置，請參閱[相關主題](what-happens-if-you-install-the-company-portal-app-and-enroll-your-device-in-intune-windows10.md)。

## <a name="what-happens-to-all-windows-devices-after-enrollment"></a>所有 Windows 裝置在註冊後會發生的事
在 Intune 註冊 Windows 或 Windows Phone 裝置可讓您：

-   存取公司的網路、電子郵件與工作檔案。

-   從公司入口網站取得公司應用程式。 (若為 Windows 7 及 Windows Vista，可以從公司入口網站取得公司應用程式)。

-   自動設定公司或學校的電子郵件帳戶。

-   當手機遺失或遭竊時，將其重設為原廠設定。

當您註冊裝置時，即授權您的 IT 系統管理員可以執行下列動作：

-   將您的裝置重設為製造商的預設設定。 這項功能對裝置遺失或失竊的情況很有幫助。

-   只移除公司相關的檔案及商務應用程式。 *您的個人資料及設定不會移除。*

-   您的 IT 系統管理員可以查看裝置上所安裝的軟體，包括您個人安裝的軟體。

-   設定裝置的需求，例如要求您為裝置設定密碼或 PIN 碼，以保護公司的資料。 您的 IT 系統管理員也可能會限制您能輸入錯誤密碼的次數，並在嘗試次數過多時鎖定裝置，禁止您繼續使用。

-   要求您將裝置上的資料加密以協助在您的裝置遺失或遭竊時保護公司資料。

-   要求您接受條款和條件。

-   防止您拍攝公司相關資料的相片。

## <a name="what-happens-to-all-windows-pcs-after-enrollment"></a>所有 Windows 電腦在註冊後會發生的事

-  軟體會安裝在您的電腦上，以便於您的 IT 系統管理員管理電腦，並讓您能夠存取公司資源 (例如應用程式及支援資訊)。 您的 IT 系統管理員可能會自動更新此軟體。

-  Intune Endpoint Protection 可能會安裝在您的電腦上。 此軟體會檢查病毒及惡意程式碼。

-  您的 IT 系統管理員可能會從您的電腦硬碟收集或刪除資料。

-  您的 IT 系統管理員可以在您的電腦上安裝應用程式並加以更新。

## <a name="what-happens-every-eight-hours-after-device-enrollment"></a>在註冊裝置後每隔八小時會發生的事
已註冊的裝置每隔大約八小時將會：

-   下載您 IT 系統管理員提供的原則或應用程式更新。

-   傳送任何硬體清查更新。

-   傳送任何公司應用程式清查更新。

如有任何問題，請連絡您的 IT 系統管理員。 如需連絡資訊，請查看[公司入口網站](http://portal.manage.microsoft.com)。



<!--HONumber=Jan17_HO4-->



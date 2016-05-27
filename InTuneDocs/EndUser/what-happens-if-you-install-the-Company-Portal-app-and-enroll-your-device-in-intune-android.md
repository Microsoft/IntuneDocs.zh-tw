---
# required metadata

title: 如果您安裝公司入口網站應用程式並在 Intune 註冊您的裝置，會發生什麼情況？ | Microsoft Intune
description:
keywords:
author: staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: d22f5aea-7be4-419b-b51b-a522ca037b69

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---


# 如果您安裝公司入口網站應用程式並在 Intune 註冊您的裝置，會發生什麼情況？

當您安裝公司入口網站應用程式，並在 Intune 中註冊您的 Android 裝置時，您可以使用公司入口網站應用程式執行下列動作：

-   存取公司網路、電子郵件和工作檔案

-   從公司入口網站取得公司應用程式

-   自動設定公司電子郵件帳戶

-   如果電話遺失或遭竊即重設為原廠設定

當您新增 Android 裝置時，您會賦予 IT 系統管理員存取裝置的權限。 IT 系統管理員可以執行下列作業：

-   將裝置重設為製造商的預設值。 這項功能對裝置遺失或失竊的情況很有幫助。

-   移除所有公司相關資料。 不會移除您的個人資料和設定。

-   強制要求您在裝置上設定密碼或 PIN；如果不正確的密碼嘗試次數過多，系統可能會鎖定您的裝置存取權，或是將裝置重設為製造商的預設設定 (可能包括刪除資料)。

-   要求您接受條款和條件。

-   啟用或停用裝置上的相機。

-   強制加密裝置上的所有資料，包括公司和個人資料。 如果裝置遺失或失竊，這將可幫助您保護資料。

-   在裝置新增到公司入口網站之後，大約每隔 8 個小時裝置會：

    -   下載 IT 系統管理員提供的任何原則或應用程式更新。

    -   傳送任何硬體清查更新 (這些更新不含個人資訊)。

    -   傳送任何公司應用程式清查更新 (這些更新不含個人資訊)。

### 請參閱
[透過 Intune 使用 Android 裝置](using-your-android-device-with-intune.md)

<!--HONumber=May16_HO2-->



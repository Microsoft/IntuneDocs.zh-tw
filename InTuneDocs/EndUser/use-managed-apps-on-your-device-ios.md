---
# required metadata

title: 在裝置上使用受管理的應用程式 | Microsoft Intune
description:
keywords:
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 3232c5c1-cb9f-45ca-806f-7e74eeb3533e

# optional metadata

ROBOTS: noindex
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---


# 在裝置上使用受管理的應用程式

受管理應用程式是 IT 系統管理員可以設定來協助保護公司資料的應用程式，您可以在該應用程式中存取這些資料。 當您在 iOS 裝置上存取受管理應用程式中的公司資料時，您可能會注意到，應用程式的運作方式與您的預期有點不同。 例如，您可能無法複製並貼上受保護的公司資料，或可能無法將該資料儲存至特定位置。

不同的受管理應用程式也可能在您的裝置上一同運作，讓您可以執行日常工作，同時持續保護公司資料。 例如，如果您在一個受管理的應用程式中開啟公司檔案，而另一個受管理的應用程式被要求檢視該檔案，可讓您檢視檔案的受管理應用程式會自動開啟。 如果可用的特定動作的不必要的應用程式，像是開啟文件或存取網頁連結從受管理的文件，可能無法使用。

當您在受管理應用程式中存取公司資料時，您會看到如下的訊息，它可讓您知道您開啟的應用程式受到管理。

![managed-apps-message-ios](./media/managed-apps-message.png)

### 如何取得受管理的應用程式？
您可利用數個不同方是取得受管理的應用程式︰

-   當您在 Microsoft Intune 中註冊您的裝置，您可從公司入口網站應用程式或公司入口網站安裝應用程式，或者您的 IT 系統管理員可能會將它安裝在您的裝置上。 若要了解註冊，請參閱[在 Intune 中註冊您的 iOS 裝置](enroll-your-device-in-intune-ios.md)或[在 Intune 中註冊您的 Mac OS X 裝置](enroll-your-device-in-intune-mac-os-x.md).

-   您從 App Store 安裝應用程式，然後使用由 Intune 管理的公司使用者帳戶登入。

### 我的 IT 系統管理員可以在應用程式中管理什麼內容？
以下是您的 IT 系統管理員可以在應用程式中管理，以及可能影響您在裝置上與公司資料互動的一些選項範例︰

-   特定網站的存取

-   應用程式之間傳送資料

-   儲存檔案

-   複製和貼上作業

-   PIN 存取需求

-   您的登入，使用公司認證

-   備份至雲端的功能

-   擷取螢幕擷取畫面的功能

-   資料加密需求

可能用來管理您的 IT 部門的一些常見應用程式如下：

-   受管理的 web 瀏覽器

-   受管理的映像檢視器

-   受管理的 PDF 檢視器

-   受管理的 AV 播放程式

-   Microsoft Word、Excel、PowerPoint

針對您的裝置上的受管理的應用程式的詳細資訊，請連絡您的 IT 系統管理員。

### 請參閱
[Using your iOS or Mac OS X device with Intune](using-your-ios-or-mac-os-x-device-with-intune.md)

<!--HONumber=May16_HO1-->



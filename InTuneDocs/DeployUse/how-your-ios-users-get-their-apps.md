---
title: "iOS 使用者如何取得其應用程式 | Microsoft Intune"
description: "讓終端使用者可以使用 iOS 應用程式的方法"
keywords: 
author: Staciebarker
manager: angrobe
ms.date: 08/24/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7e3135c1-df26-48c9-aa4c-cdab6168897a
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 9f1946c02c6267a22844106e8f72555ec5e9cabb
ms.openlocfilehash: 212dcd31697180dae61569dda13b56704a079bf4


---


# iOS 使用者如何取得其應用程式

使用這項資訊，了解您的使用者取得您透過 Microsoft Intune 散發之應用程式的方式和位置。

**必要的應用程式** - 依據不同的平台，系統管理員所需且安裝在最少使用者介入之裝置上的應用程式。

**可用的應用程式** - 公司入口網站應用程式清單中所提供且使用者可選擇性決定是否要安裝的應用程式。

**受管理的應用程式** - 可透過原則進行管理的應用程式，以及已由 Intune「包裝 (wrapped)」或已透過 Intune 行動應用程式管理 (MAM) 軟體開發套件 (SDK) 建置的應用程式。 這些應用程式可由 Intune 管理，並套用應用程式原則。

**不受管理的應用程式** - 可透過原則進行管理的應用程式，以及未受 Intune 包裝或不包含 Intune MAM SDK 的應用程式。 應用程式原則不適用於這些應用程式。

Apple 限制禁止「公司入口網站」應用程式中列出企業營運應用程式及受管理的應用程式市集應用程式，這代表使用者必須瀏覽不同的檢視才能找到所有的應用程式。 對於在公司入口網站應用程式 [應用程式] 頁面中每個所顯示磚的應用程式，可以透過下列方式取得：

- [公司應用程式] 磚會指向[公司入口網站](http://portal.manage.microsoft.com)中 [所有] 索引標籤中所有應用程式的清單。

- [其他應用程式] 磚目前會指向「公司入口網站」應用程式中的檢視，其中會列出 Apple 允許在公司入口網站應用程式中顯示的所有應用程式。 這包括所有的應用程式，但不包含企業營運應用程式和受管理的應用程式市集應用程式。

- [類別] 磚目前會指向公司入口網站應用程式中列出應用程式類別的檢視。

    ![ios-how-to-sync-device-with-intune](./media/ios-sync-comp-portal-apps.png)


###請參閱
[Android 使用者如何取得其應用程式](how-your-android-users-get-their-apps.md)</br>
[Windows 使用者如何取得其應用程式](how-your-windows-users-get-their-apps.md)



<!--HONumber=Aug16_HO4-->



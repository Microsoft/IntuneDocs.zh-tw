---
title: "Android 使用者如何取得其應用程式 | Microsoft Intune"
description: 
keywords: 
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f33d1684-b1b5-44f7-9aac-c6d5186a5d7c
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: d3bcf89636f9da8fd8bfa5cc52391742a9ce9f92
ms.openlocfilehash: 25571ce1b214c927f3dc2ea3968d00970621e474


---


# Android 使用者如何取得其應用程式
使用這項資訊，了解您的使用者取得您透過 Microsoft Intune 散發之應用程式的方式和位置。 

**必要的應用程式** - 依據不同的平台，系統管理員所需且安裝在最少使用者介入之裝置上的應用程式。
 
- **Samsung Knox 裝置**︰如果您將必要的應用程式部署至 Samsung Knox 裝置，它會自動且無訊息地安裝在其裝置上。
- **原生 (非 Samsung Knox 裝置)**︰如果您將必要的應用程式部署至非 Samsung Knox 裝置，它不會自動安裝在使用者的裝置上。 相反地，系統會提示使用者安裝應用程式。 使用者接受提示之後，會下載應用程式，然後使用者會收到通知，指出需要安裝它。 

**可用的應用程式** - 公司入口網站應用程式清單中所提供且使用者可選擇性決定是否要安裝的應用程式。

**受管理的應用程式** - 可透過原則進行管理的應用程式，以及已由 Intune「包裝 (wrapped)」或已透過 Intune 行動應用程式管理 (MAM) 軟體開發套件 (SDK) 建置的應用程式。 這些應用程式可由 Intune 管理，並套用應用程式原則。

**不受管理的應用程式** - 可透過原則進行管理的應用程式，以及未受 Intune 包裝或不包含 Intune MAM SDK 的應用程式。 應用程式原則不適用於這些應用程式。

###請參閱
[使用 Microsoft Intune 新增應用程式](/intune/deploy-use/add-apps)
[iOS 使用者如何取得其應用程式](how-your-ios-users-get-their-apps.md)
[Windows 使用者如何取得其應用程式](how-your-windows-users-get-their-apps.md)


<!--HONumber=Jul16_HO1-->



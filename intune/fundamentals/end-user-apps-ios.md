---
title: iOS 使用者如何取得其應用程式
description: 讓終端使用者可以使用 iOS 應用程式的方法
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 05/07/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 7e3135c1-df26-48c9-aa4c-cdab6168897a
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 06cc977ce8b0b892e1020436f89ada4a40bac3f2
ms.sourcegitcommit: 60f0ff6d2efbae0f2ce14b9a9f3f9267309e209b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73413985"
---
# <a name="how-your-ios-users-get-their-apps"></a>iOS 使用者如何取得其應用程式

使用這項資訊，了解您的使用者取得您透過 Microsoft Intune 散發之應用程式的方式和位置。

**必要的應用程式** - 依據不同的平台，系統管理員所需且安裝在最少使用者介入之裝置上的應用程式。

**可用的應用程式** - 公司入口網站應用程式清單中所提供且使用者可選擇性地選擇要安裝的應用程式。

**受管理的應用程式** - 可透過原則進行管理的應用程式，以及已由 Intune「包裝」或已透過 Intune 應用程式軟體開發套件 (SDK) 建置的應用程式。 這些應用程式可由 Intune 管理，並套用應用程式保護原則。

**非受控的應用程式** - 使用者可從未與 Intune 應用程式 SDK 整合的 iOS App Store 下載的應用程式。 Intune 無法控制這些應用程式的散發、管理或選擇性抹除。  

Apple 限制禁止公司入口網站應用程式中列出企業營運應用程式及受管理的 App Store 應用程式。 為了解決此問題，iOS 版公司入口網站應用程式中的磚會將使用者指向單一位置 (公司入口網站) 中的不同檢視，以取得他們所有的應用程式。

已註冊的使用者可在公司入口網站應用程式的 [應用程式] 畫面上點選下列磚，以取得他們的應用程式：

- [所有應用程式]  會指向[公司入口網站](https://portal.manage.microsoft.com) [所有] 索引標籤中所有應用程式的清單。

- [精選應用程式]  則將使用者帶往公司入口網站的 [精選] 索引標籤。

- [類別]  會指向公司入口網站的 [類別] 索引標籤。

![iOS 公司入口網站應用程式畫面](./media/end-user-apps-ios/ios-cp-app-main-apps-screen.png)

如需如何新增應用程式的資訊，請參閱[如何將應用程式新增至 Microsoft Intune](../apps/apps-add.md)。

## <a name="see-also"></a>請參閱

[Android 使用者如何取得其應用程式](end-user-apps-android.md)

[Windows 使用者如何取得其應用程式](end-user-apps-windows.md)

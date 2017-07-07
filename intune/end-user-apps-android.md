---
title: "Android 使用者如何取得其應用程式"
description: "讓終端使用者可以使用 Android 應用程式的方法"
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 11/14/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f33d1684-b1b5-44f7-9aac-c6d5186a5d7c
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 4f0364750edf2e97e2b621c27fb25bea8e0f537c
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2017
---
# <a name="how-your-android-users-get-their-apps"></a>Android 使用者如何取得其應用程式

[!INCLUDE[both-portals](./includes/note-for-both-portals.md)]

使用這項資訊，了解您的 Android 使用者取得您透過 Microsoft Intune 散發之應用程式的方式和位置。 該資訊可能會因裝置類型 (原生 Android 裝置或 Samsung Knox Standard 裝置) 而有所不同。

## <a name="native-non-samsung-knox-standard-android-devices"></a>原生 (非 Samsung Knox Standard) Android 裝置

| 應用程式類型 | 企業營運 (LOB) 應用程式 | Play Store 應用程式  |
| ------------- |-------------| -----|
| 可用的應用程式      | 使用者在公司入口網站中點選 [安裝]。 隨即會出現通知，而使用者將點選該通知以開始安裝。 安裝成功之後，通知將會消失。 | 使用者點選公司網站中的應用程式，並被移至 Play Store 中的應用程式頁面，使用者可以在該處開始安裝。|
| Required apps      | 使用者會看見一個無法關閉的通知，指出他們必須安裝應用程式。 使用者點選通知以開始安裝。 安裝成功之後，通知將會消失。    | 使用者會看見一個無法關閉的通知，指出他們必須安裝應用程式。 使用者點選通知，並被移至 Play Store 中的應用程式頁面，使用者可以在該處開始安裝。 安裝成功之後，通知將會消失。 |

## <a name="samsung-knox-standard-android-devices"></a>Samsung Knox Standard Android 裝置

| 應用程式類型 | 企業營運 (LOB) 應用程式 | Play Store 應用程式  |
| ------------- |-------------| -----|
| 可用的應用程式      | 使用者在公司入口網站中點選 [安裝]。 應用程式將在使用者無須介入下完成安裝。 | 使用者點選公司網站中的應用程式，並被移至 Play Store 中的應用程式頁面，使用者可以在該處開始安裝。|
| Required apps      | 應用程式將在使用者無須介入下完成安裝。    | 使用者會看見一個無法關閉的通知，指出他們必須安裝應用程式。 使用者點選通知，並被移至 Play Store 中的應用程式頁面，使用者可以在該處開始安裝。 安裝成功之後，通知將會消失。 |

應用程式可為受管理或不受管理，如下所述。 讓應用程式受管理的程序，針對所有類型的 Android 裝置都是相同的。

**受管理的應用程式** - 可透過原則進行管理的應用程式。 這些應用程式已由 Intune「包裝」或已透過 Intune 行動應用程式管理 (MAM) 軟體開發套件 (SDK) 建置。 這些應用程式可由 Intune 管理，並套用應用程式原則。

**未受管理的應用程式** - 無法透過原則進行管理的應用程式。 這些應用程式未受 Intune 包裝或不包含 Intune MAM SDK。 應用程式原則不適用於這些應用程式。

### <a name="see-also"></a>請參閱
[使用 Microsoft Intune 新增應用程式](apps-add.md)

[iOS 使用者如何取得其應用程式](end-user-apps-ios.md)

[Windows 使用者如何取得其應用程式](end-user-apps-windows.md)

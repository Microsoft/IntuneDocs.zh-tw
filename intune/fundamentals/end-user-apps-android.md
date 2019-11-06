---
title: Android 使用者如何取得其應用程式
description: 讓終端使用者可以使用 Android 應用程式的方法
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 09/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f33d1684-b1b5-44f7-9aac-c6d5186a5d7c
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 40e8dd8409f70a70934684c56ed9e9729f4ebf0f
ms.sourcegitcommit: 60f0ff6d2efbae0f2ce14b9a9f3f9267309e209b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73414591"
---
# <a name="how-your-android-users-get-their-apps"></a>Android 使用者如何取得其應用程式

此文章可協助您了解 Android 終端使用者取得您透過 Microsoft Intune 散發之應用程式的方式和位置。 該資訊可能會因裝置類型 (原生 Android 裝置或 Samsung Knox Standard 裝置) 而有所不同。

## <a name="native-non-samsung-knox-standard-android-devices"></a>原生 (非 Samsung Knox Standard) Android 裝置

| 應用程式類型 | 企業營運 (LOB) 應用程式 | Play Store 應用程式  |
| ------------- |-------------| -----|
| 可用的應用程式      | 使用者在公司入口網站中點選 [安裝]  。 隨即會出現通知，而使用者將點選該通知以開始安裝。 安裝成功之後，通知將會消失。 | 使用者點選公司網站中的應用程式，即會前往 Play Store 中的應用程式頁面。 使用者可以在這裡開始安裝。|
| Required apps      | 使用者會看見他們無法關閉的通知，指出他們必須安裝應用程式。 使用者點選通知以開始安裝。 安裝成功之後，通知將會消失。    | 使用者會看見他們無法關閉的通知，指出他們必須安裝應用程式。 使用者點選通知，即會前往 Play Store 中的應用程式頁面。 使用者可以在這裡開始安裝。 安裝成功之後，通知將會消失。 |

您的終端使用者必須允許來自未知來源的安裝，才能安裝 [LOB 應用程式](../apps/lob-apps-android.md)。 這些設定通常可在兩個不同的位置中找到：

* **Android 7.1.2 和更舊版本**：[設定]   > [安全性]   > [未知來源] 
* **Android 8.0 和更新版本**：[設定]   > [應用程式與通知]   > [特殊應用程式存取]   > [安裝未知的應用程式]   > [公司入口網站]   > [允許從這個來源] 

如果發生這種情況，公司入口網站應用程式將會通知，並直接引導終端使用者進行適當的設定。 

## <a name="samsung-knox-standard-android-devices"></a>Samsung Knox Standard Android 裝置

| 應用程式類型 | 企業營運 (LOB) 應用程式 | Play Store 應用程式  |
| ------------- |-------------| -----|
| 可用的應用程式      | 使用者在公司入口網站中點選 [安裝]  。 應用程式將在使用者無須介入下完成安裝。 | 使用者點選公司網站中的應用程式，即會前往 Play Store 中的應用程式頁面。 使用者可以在這裡開始安裝。|
| Required apps      | 應用程式將在使用者無須介入下完成安裝。    | 使用者會看見他們無法關閉的通知，指出他們必須安裝應用程式。 使用者點選通知，即會前往 Play Store 中的應用程式頁面。 使用者可以在這裡開始安裝。 安裝成功之後，通知將會消失。 |

應用程式可為受管理或不受管理，如下所述。 讓應用程式受管理的程序，針對所有類型的 Android 裝置都是相同的。

**受控應用程式**：這些應用程式可透過原則進行管理。 它們已由 Intune「包裝」或已透過 Intune App SDK 建置。 這些應用程式可由 Intune 管理，並套用應用程式原則。

**非受控應用程式**：這些應用程式無法透過原則進行管理。 它們未受 Intune 包裝或未併入 Intune App SDK。 應用程式原則無法套用到這些應用程式。

## <a name="zebra-devices-with-zebra-mobility-extensions"></a>含有 Zebra Mobility Extensions 的 Zebra 裝置

Intune 會使用 Zebra Mobility Extensions (MX) 工具組，在裝置系統管理員所管理的 Zebra 裝置上以無訊息方式安裝應用程式。 此功能可讓您在 Zebra 裝置上部署及更新應用程式，而不需使用者介入。 如果裝置上的 MX 版本是 4.2 或更舊版本，則不會以無訊息方式安裝應用程式。 如需詳細資訊，請參閱 Zebra 網站上的[完整 MX 功能對照表](http://techdocs.zebra.com/mx/compatibility/) \(英文\)。

部署到 Zebra 裝置的 LOB 應用程式必須從裝置上的公用位置進行安裝。 其他應用程式和服務 (也可存取裝置上的公用存放裝置) 可以存取 .apk 應用程式套件。 一般來說，此存取是應用程式下載完成和安裝開始之間的一個小視窗。 此視窗可能允許計時攻擊。 例如，.apk 套件可能在此視窗期間遭到變更。 Intune 會將 .apk 花費在公用存放裝置中的時間量降到最低，且不允許安裝未簽署的應用程式。 若要協助將安全性風險降到最低，請確定您上傳的 .apk 檔案不包含敏感性資訊。

## <a name="see-also"></a>請參閱

[使用 Microsoft Intune 新增應用程式](../apps/apps-add.md)

[iOS 使用者如何取得其應用程式](end-user-apps-ios.md)

[Windows 使用者如何取得其應用程式](end-user-apps-windows.md)

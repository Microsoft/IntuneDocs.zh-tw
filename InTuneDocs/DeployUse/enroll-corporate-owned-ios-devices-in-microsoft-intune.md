---
# required metadata

title: 在 Microsoft Intune 中註冊屬公司擁有的 iOS 裝置 | Microsoft Intune
description:
keywords:
author: NathBarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 2d3ca4ab-f20c-4d56-9413-f8ef19cf0722

# optional metadata

ROBOTS: noindex,nofollow
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# 在 Microsoft Intune 中註冊屬公司擁有的 iOS 裝置
Microsoft Intune 支援使用 Mac 電腦上所執行的 [Apple Configurator](http://go.microsoft.com/fwlink/?LinkId=518017) 工具，來註冊公司所擁有的 iOS 裝置。

您可以利用下列三種方式來註冊公司所註冊的 iOS 裝置：

-   設定助理註冊 - 將裝置重設為原廠值，並準備好裝置以供裝置的新使用者進行設定。 此方法需要系統管理員使用 USB，將 iOS 裝置連接到執行 Apple Configurator 以預先註冊的 Mac 電腦。 裝置接著會傳遞至其執行設定助理程序的使用者，使用其工作或學校認證來設定裝置並完成註冊程序。 [使用 Apple Configurator 和設定助理來註冊 iOS 裝置](ios-setup-assistant-enrollment-in-microsoft-intune.md)

-   直接註冊 – 在裝置準備期間，建立 Apple Configurator 相容的檔案以供使用。 註冊的裝置未重設為原廠值，但不具有任何使用者關係。 此方法需要系統管理員使用 USB，將 iOS 裝置連接到執行 Apple Configurator 以註冊裝置的 Mac 電腦。 [使用 Apple Configurator 直接註冊來註冊 iOS 裝置](ios-direct-enrollment-in-microsoft-intune.md)

-   裝置註冊方案 (DEP) – 將註冊設定檔「無線」部署到透過 Apple 的裝置註冊方案所購買的裝置。 當使用者在裝置上執行設定助理時，會在 Intune 中註冊裝置。  透過 DEP 註冊的裝置不能由使用者取消註冊。 [註冊裝置註冊方案 iOS 裝置](ios-device-enrollment-program-in-microsoft-intune.md)




### 請參閱
[準備在 Microsoft Intune 中註冊裝置](get-ready-to-enroll-devices-in-microsoft-intune.md)


<!--HONumber=May16_HO2-->



---
title: "您在嘗試註冊 iOS 裝置時看到錯誤 | Microsoft Docs"
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
ms.assetid: 92a8d06d-0ecb-4912-898b-993e8eaf4e58
searchScope:
- Company Portal
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: esmich
ms.suite: ems
ms.custom: intune-enduser
translationtype: Human Translation
ms.sourcegitcommit: a87fe0cf9591040f1455d71b1f40cd0705ba8abf
ms.openlocfilehash: 06866b9db458851dbb23d5ccf741cad3e1d4c5d0


---

# <a name="you-see-errors-while-trying-to-enroll-your-ios-device-in-intune"></a>您在 Intune 嘗試註冊 iOS 裝置時看到錯誤

下表列出您在 Intune 中註冊 iOS 裝置時可能發現的錯誤。 與您的 IT 系統管理員分享此連結。 如需連絡資訊，請查看[公司入口網站](http://portal.manage.microsoft.com)。

|錯誤訊息|問題|要告訴 IT 系統管理員的內容|
|-----------------|---------|----------------------------------------------------------------------------------------------------------------------------------------------------------------|
|NoEnrollmentPolicy|無註冊原則|請檢查所有註冊必要條件 (例如 APNs 憑證)，並確認已設定並啟用 [iOS as a platform] (iOS 即平台)。 如需指示，請參閱[設定 iOS 和 Mac 裝置管理](/intune/deploy-use/set-up-ios-and-mac-management-with-microsoft-intune)。|
|DeviceCapReached|您已經註冊過多行動裝置。|註冊其他行動裝置之前，使用者必須先從公司入口網站移除目前已註冊的其中一部行動裝置。 請參閱您所使用的裝置類型的指示︰[Android](unenroll-your-device-from-intune-android.md)、[iOS](unenroll-your-device-from-intune-ios.md)、[Windows](unenroll-your-device-from-intune-windows.md)。|
|APNSCertificateNotValid|行動裝置用來與公司網路通訊的憑證發生問題。<br /><br />請連絡並告知 IT 系統管理員，您在嘗試註冊行動裝置時收到 **APNSCertificateNotValid** 訊息，並請他們參閱本表的解決方法。|Apple Push Notification Service (APNs) 是可用來連接已註冊 iOS 裝置的管道。 若未執行取得 APNs 憑證的步驟，或者 APNs 憑證已過期，則嘗試註冊將會失敗，且會出現此訊息。<br /><br />如需如何設定使用者的資訊，請檢閱[同步處理 Active Directory 並將使用者新增至 Intune](/Intune/Get-Started/start-with-a-paid-subscription-to-microsoft-intune-step-3) 和[組織使用者和裝置](/Intune/Get-Started/start-with-a-paid-subscription-to-microsoft-intune-step-5)。|
|AccountNotOnboarded|行動裝置用來與公司網路通訊的憑證發生問題。<br /><br />請連絡並告知 IT 系統管理員，您在嘗試註冊行動裝置時收到 **APNSNotOnboarded** 訊息，並請他們參閱本表的解決方法。|Apple Push Notification Service (APNs) 是可用來連接已註冊 iOS 裝置的管道。 若未執行取得 APNs 憑證的步驟，或者 APNs 憑證已過期，則嘗試註冊將會失敗，且會出現此訊息。<br /><br />如需詳細資訊，請檢閱[使用 Microsoft Intune 設定 iOS 和 Mac 管理](/Intune/Deploy-use/set-up-ios-and-mac-management-with-microsoft-intune)。|
|DeviceTypeNotSupported|您可能嘗試使用非 iOS 進行註冊。 您嘗試註冊的行動裝置類型不受支援。<br /><br />確定您的裝置正在執行 iOS 8.0 版或更新版本。<br /><br />請連絡並告知 IT 系統管理員，您在嘗試註冊行動裝置時收到 **DeviceTypeNotSupported** 訊息，並請他們參閱本表的解決方法。|確定您的使用者裝置正在執行 iOS 8.0 版或更新版本。|
|UserLicenseTypeInvalid|您不能註冊行動裝置，因為您的使用者帳戶還不是必要的使用者群組的成員。<br /><br />請連絡並告知 IT 系統管理員，您在嘗試註冊行動裝置時收到 **UserLicenseTypeInvalid** 訊息，並請他們參閱本表的解決方法。|使用者必須是正確使用者群組的成員，才可以註冊裝置。 這則訊息表示他們擁有的授權類型錯誤，不能用於指定的行動裝置管理授權單位。 例如，如果已指定 Intune 做為行動裝置管理授權單位，而他們使用的是 System Center 2012 R2 Configuration Manager 授權，他們就會發現這個錯誤。<br /><br />如需詳細資訊，請檢閱下列內容：<br /><br />檢閱[使用 Microsoft Intune 設定 iOS 和 Mac 管理](/Intune/Deploy-use/set-up-ios-and-mac-management-with-microsoft-intune)，以及[同步處理 Active Directory 並將使用者新增至 Intune](/Intune/Get-Started/start-with-a-paid-subscription-to-microsoft-intune-step-3) 和[組織使用者和裝置](/Intune/Get-Started/start-with-a-paid-subscription-to-microsoft-intune-step-5)，以取得如何設定使用者的資訊。|
|MdmAuthorityNotDefined|您的 IT 系統管理員需要設定公司管理行動裝置的方式。<br /><br />請連絡並告知 IT 系統管理員，您在嘗試註冊行動裝置時收到 **MdmAuthorityNotDefined** 訊息，並請他們參閱本表的解決方法。|尚未在 Intune 中指定行動裝置管理授權單位。<br /><br />檢閱[開始使用 Microsoft Intune 30 天試用版](/Intune/Understand-explore/get-started-with-a-30-day-trial-of-microsoft-intune)中＜步驟 6：註冊行動裝置並安裝應用程式＞一節中的項目 #1。|



<!--HONumber=Jan17_HO4-->



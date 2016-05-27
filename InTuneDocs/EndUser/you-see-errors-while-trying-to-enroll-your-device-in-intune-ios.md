---
# required metadata

title: 您在 Intune 嘗試註冊 iOS 裝置時看到錯誤 | Microsoft Intune
description:
keywords:
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 92a8d06d-0ecb-4912-898b-993e8eaf4e58

# optional metadata

ROBOTS: noindex
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---


# 您在 Intune 嘗試註冊 iOS 裝置時看到錯誤

下表列出您在 Intune 中註冊 iOS 裝置時可能發現的錯誤。 與您的 IT 系統管理員分享此連結。 

|錯誤訊息|問題|要告訴 IT 系統管理員的內容|
|-----------------|---------|----------------------------------------------------------------------------------------------------------------------------------------------------------------|
|DeviceCapReached|您已經註冊過多行動裝置。|註冊其他行動裝置之前，使用者必須先從公司入口網站移除目前已註冊的其中一部行動裝置。|
|APNSCertificateNotValid|可讓行動裝置與公司網路通訊的憑證發生問題。<br /><br />請連絡您的 IT 系統管理員，告知您在嘗試註冊行動裝置時收到的訊息 APNSCertificateNotValid，並告訴他們參閱本表中的解析。|Apple Push Notification Service (APNS) 提供一個連接已註冊 iOS 裝置的管道。 若未執行取得 APNS 憑證的步驟，或 APNS 憑證已過期，則註冊嘗試將會失敗，且會出現此訊息。<br /><br />檢閱[同步處理 Active Directory 並將使用者新增至 Intune](/Intune/Get-Started/start-with-a-paid-subscription-to-microsoft-intune-step-3) 和 [組織使用者和裝置](/Intune/Get-Started/start-with-a-paid-subscription-to-microsoft-intune-step-5)中設定使用者的資訊|
|AccountNotOnboarded|可讓行動裝置與公司網路通訊的憑證發生問題。<br /><br />請連絡您的 IT 系統管理員，告知您在嘗試註冊行動裝置時收到的訊息 APNSNotOnboarded，並告訴他們參閱本表中的解析。|Apple Push Notification Service (APNS) 提供一個連接已註冊 iOS 裝置的管道。 若未執行取得 APNS 憑證的步驟，或 APNS 憑證已過期，則註冊嘗試將會失敗，且會出現此訊息。<br /><br />如需詳細資訊，請檢閱[使用 Microsoft Intune 設定 iOS 和 Mac 管理](/Intune/Deployuse/set-up-ios-and-mac-management-with-microsoft-intune)。|
|DeviceTypeNotSupported|您可能會嘗試使用非 iOS 裝置進行註冊。 您嘗試註冊的行動裝置類型不受支援。<br /><br />確定您的裝置正在執行 iOS 7.1 版或更新版本。<br /><br />請連絡您的 IT 系統管理員，告知其您收到訊息 DeviceTypeNotSupported 時嘗試註冊行動裝置，並請參閱本表中的解析的指示。|確定您的使用者裝置正在執行 iOS 7.1 版或更新版本。|
|UserLicenseTypeInvalid|您不能註冊行動裝置，因為您的使用者帳戶還不是必要的使用者群組的成員。<br /><br />請連絡您的 IT 系統管理員，告知其您收到訊息 UserLicenseTypeInvalid 時嘗試註冊行動裝置，並請參閱本表中的解析的指示。|在使用者可以註冊其裝置之前，他們必須是正確使用者群組的成員。 這則訊息表示他們擁有的授權類型錯誤，不能用於指定的行動裝置管理授權單位。 例如，如果已指定 Intune 做為行動裝置管理授權單位，而他們使用的是 System Center 2012 R2 Configuration Manager 授權，他們就會發現這個錯誤。<br /><br />如需詳細資訊，請檢閱下列內容：<br /><br />檢閱[使用 Microsoft Intune 設定 iOS 和 Mac 管理](/Intune/Deploy-use/set-up-ios-and-mac-management-with-microsoft-intune)和 [同步處理 Active Directory 並將使用者新增至 Intune ] (/Intune/Get-Started/start-with-a-paid-subscription-to-microsoft-intune-step-3 以及[組織使用者和裝置](/Intune/Get-Started/start-with-a-paid-subscription-to-microsoft-intune-step-5)中設定使用者的相關資訊|
|MdmAuthorityNotDefined|您的 IT 系統管理員需要設定貴公司的行動裝置管理方式。<br /><br />請連絡您的 IT 系統管理員，告知其您收到訊息 MdmAuthorityNotDefined 時嘗試註冊行動裝置，並請參閱本表中的解析的指示。|尚未在 Intune 中指定行動裝置管理授權單位。<br /><br />檢閱[開始使用 Microsoft Intune 30 天試用版](/Intune/Understand-explore/get-started-with-a-30-day-trial-of-microsoft-intune)中「步驟 6：註冊行動裝置並安裝應用程式」一節中的項目 #1|

### 請參閱
[Using your iOS or Mac OS X device with Intune](using-your-ios-or-mac-os-x-device-with-intune.md)

<!--HONumber=May16_HO2-->



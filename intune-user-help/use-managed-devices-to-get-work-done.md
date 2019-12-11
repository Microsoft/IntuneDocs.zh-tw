---
title: 什麼是裝置註冊 | Microsoft Docs
description: 瞭解向公司入口網站和 Microsoft Intune 應用程式註冊您的裝置所代表的意義。
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 09/13/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: 523caa6b-d792-4bb6-bddb-24b2479932d8
searchScope:
- User help
ROBOTS: ''
ms.reviewer: esmich
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: ca1776915d50858c28b43a49faa7c737c825c67d
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72501849"
---
# <a name="what-is-device-enrollment"></a>什麼是裝置註冊？
若要從您的裝置存取公司或學校資源，您必須使用 Intune 公司入口網站應用程式或 Microsoft Intune 應用程式來註冊您的裝置。 

在裝置註冊期間：

* 您的裝置已向您的組織註冊。 此步驟可確保您有權存取貴組織的電子郵件、應用程式和 Wi-fi。 
* 貴組織的裝置管理原則會套用至您的裝置。 原則可能包括裝置密碼和加密等專案的需求。 這些需求的目的是要讓您的裝置和組織的資料安全地免于未經授權的存取。

當您更新裝置設定以符合組織的需求時，註冊便已完成。 您幾乎可以從任何地方安全地登入您的工作或學校帳戶。  

本文說明註冊的其他層面，例如如何取得應用程式、支援的裝置，以及移除或重設您的裝置。  

## <a name="company-portal-and-microsoft-intune-app"></a>公司入口網站和 Microsoft Intune 應用程式

公司入口網站和 Microsoft Intune 應用程式會向您發出原則或設定變更的警示，讓您可以採取動作，而不會失去對公司或學校的存取權。 

公司入口網站應用程式會將您的個人和工作資訊分開，讓您可以維持生產力且專注于。 此外，它也可供您使用工作和學校應用程式，因此您可以尋找並安裝與您的工作相關的使用者。  

### <a name="get-company-portal"></a>取得公司入口網站

在某些情況下，您的組織會為您在裝置上安裝公司入口網站應用程式。 應用程式也可以從應用程式存放區（例如 Microsoft Store、App Store 和 Google Play 存放區）進行安裝。 若要從網頁瀏覽器存取應用程式，請使用您的工作或學校帳戶登入[公司入口網站網站](https://go.microsoft.com/fwlink/?linkid=2010980)。  

### <a name="get-microsoft-intune-app"></a>取得 Microsoft Intune 應用程式

如果您需要使用 Microsoft Intune 應用程式，您的組織會將它安裝在您的裝置上。  

## <a name="whats-the-difference-between-the-apps-and-the-website"></a>應用程式與網站之間的差異為何？
公司入口網站應用程式適用于 Windows 10、iOS、macOS 和 Android 裝置。 它可與您裝置的個別平臺完美整合。 網站版本可從任何裝置存取，不論您使用哪種裝置，都能提供您相同且通用的體驗。 

Microsoft Intune 應用程式適用于公司擁有的 Android 裝置，且沒有網站。  

## <a name="what-kind-of-devices-can-you-enroll-with-company-portal"></a>您可以使用公司入口網站註冊哪些類型的裝置？
您可以使用公司入口網站註冊下列裝置：  

- Windows 裝置
  - Windows 10 Mobile
  - Windows 10 Desktop
  - Windows Phone 8.1
  - Windows 8.1
- Apple 裝置
    - iOS
    - macOS
- Android 裝置


## <a name="what-kind-of-devices-can-you-enroll-with-the-microsoft-intune-app"></a>您可以使用 Microsoft Intune 應用程式註冊何種裝置？  
您可以註冊公司所擁有的 Android 裝置，您的組織已設定為與應用程式搭配使用。 應用程式支援 Android 6.0 和更新版本。 

## <a name="can-you-remove-a-device-from-the-company-portal"></a>您是否可以從公司入口網站移除裝置？
您可以從公司入口網站移除或重設裝置。 [移除]  與 [重設]  不同。

移除裝置時，公司入口網站取消註冊並取消註冊裝置。 該裝置會失去公司入口網站的存取權。 可能也會移除工作或學校資料。 

在裝置重設期間，公司入口網站會嘗試將電腦或裝置重設為製造商的預設設定。 所有的工作或學校資料，以及所有個人資料都會從裝置中移除。 例如，如果您遺失您的裝置，重設會很有用。 您可以從公司入口網站網站遠端重設它。  

## <a name="can-you-remove-a-device-from-the-microsoft-intune-app"></a>您可以從 Microsoft Intune 應用程式移除裝置嗎？
否，您無法從 Microsoft Intune 應用程式中移除公司擁有的裝置。  

## <a name="what-if-i-cant-see-my-device-in-the-company-portal-or-microsoft-intune-app"></a>如果我在公司入口網站或 Microsoft Intune 應用程式中看不到我的裝置，該怎麼辦？
若要查看公司入口網站中的裝置，必須先進行註冊。 註冊之後，如果您仍然看不到所有的裝置，請嘗試透過公司入口網站同步或檢查存取。 您將不會看到您公司所擁有及管理的裝置。

在 Microsoft Intune 應用程式中，您只會看到目前正在使用的裝置。 應用程式中不會顯示其他已註冊的裝置。  

## <a name="where-else-can-i-go-for-help"></a>我還能去哪裡尋求協助？  
若要針對常見問題進行疑難排解，請參閱下列平臺特定檔：  

- [修正 Android 裝置常見的問題](check-compliance-on-your-device-android.md)  
- [修正 iOS 裝置常見的問題](troubleshoot-your-device-ios.md)
- [修正 macOS 裝置常見的問題](troubleshoot-your-device-macos.md)
- [修正 Windows 裝置常見的問題](troubleshoot-your-device-windows.md)

您也可以聯繫到您的 IT 支援人員。 公司入口網站和 Microsoft Intune 應用程式提供列出連絡人資訊的說明及支援頁面，以及回報問題的方式。 您組織的[公司入口網站網站](https://go.microsoft.com/fwlink/?linkid=2010980)也提供連絡人資訊。  

## <a name="next-steps"></a>後續步驟  

如果您已準備好存取公司或學校帳戶，請遵循您組織的指示來註冊您的裝置。 您也可以在下列文章中找到逐步註冊指引。

* [註冊 Windows 10 裝置](enroll-windows-10-device.md)
* [註冊您的 Android 裝置](enroll-device-android-company-portal.md)
* [使用 Android 工作設定檔註冊](enroll-device-android-work-profile.md)
* [使用 Microsoft Intune 應用程式註冊](enroll-device-android-microsoft-intune-app.md)
* [註冊 iOS 裝置](enroll-your-device-in-intune-ios.md)
* [註冊您組織提供的 iOS 裝置](enroll-your-device-dep-ios.md)
* [註冊 macOS 裝置](enroll-your-device-in-intune-macos-cp.md)
* [註冊您組織提供的 macOS 裝置](enroll-company-device-macos.md)



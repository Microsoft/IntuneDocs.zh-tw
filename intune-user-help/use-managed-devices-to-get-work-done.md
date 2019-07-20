---
title: 使用受管理的裝置完成工作 | Microsoft Docs
description: 了解使用 Intune 註冊管理您的裝置代表的意義。
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 04/19/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 523caa6b-d792-4bb6-bddb-24b2479932d8
searchScope:
- User help
ROBOTS: ''
ms.reviewer: esmich
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2f698f03ed3c7523ef1d768d2a1361d6d1a55008
ms.sourcegitcommit: 7c251948811b8b817e9fe590b77f23aed95b2d4e
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "67883861"
---
# <a name="enroll-device-for-access-to-work-or-school-resources"></a>註冊裝置以存取公司或學校資源
若要註冊您的裝置並取得電子郵件和應用程式的存取權, 您必須安裝 Intune 公司入口網站應用程式或 Microsoft Intune 應用程式。 當您註冊時, 您的組織所設定的基本管理原則 (例如密碼、PIN 和加密) 會套用至您的裝置。 一旦您的裝置設定符合您組織的所有需求, 您幾乎可以從任何地方安全地存取您的工作資訊。  

公司入口網站和 Microsoft Intune 應用程式會確保您的裝置設定符合您組織的原則, 讓您的已註冊裝置保持安全。 

公司入口網站應用程式也會：  
* 個別保存個人和工作資訊。  
* 可讓您輕鬆地尋找及安裝相關的工作和學校應用程式。   

## <a name="get-the-apps"></a>取得應用程式
取得公司入口網站：

- 從平臺特定的應用程式存放區安裝公司入口網站應用程式。 在某些情況下, 您的組織將會為您安裝公司入口網站應用程式。  
- 前往[公司入口網站網站](https://go.microsoft.com/fwlink/?linkid=2010980), 從瀏覽器存取應用程式。  

如果您需要使用 Microsoft Intune 應用程式, 您的組織將會為您安裝。  


## <a name="what-information-can-my-company-see-when-i-enroll"></a>當我註冊時，我的公司可以看到哪些資訊？
註冊裝置之後, 您組織的支援人員只會看到與工作相關的資訊。 他們無法看到您的個人資訊。 如果您要註冊個人裝置以供工作使用, 請確實[瞭解哪些內容可以看見](what-info-can-your-company-see-when-you-enroll-your-device-in-intune.md)。  


## <a name="whats-the-difference-between-the-apps-and-the-website"></a>應用程式與網站之間的差異為何？
公司入口網站應用程式適用于 Windows 10、iOS、macOS 和 Android 裝置。 它可與您裝置的個別平臺完美整合。 網站版本可從任何裝置存取，不論您使用哪種裝置，都能提供您相同且通用的體驗。 

Microsoft Intune 應用程式適用于公司擁有的 Android 裝置。  

## <a name="what-kind-of-devices-can-you-enroll-with-company-portal"></a>您可以使用公司入口網站註冊哪些類型的裝置？
- 使用 iOS (例如 iPhone 和 iPad) 及 macOS (例如 MacBook 和 iMac) 的 Apple 裝置
- Android 裝置
- Windows 裝置
  - Windows 10 Mobile
  - Windows 10 Desktop
  - Windows Phone 8.1
  - Windows 8.1

## <a name="what-kind-of-devices-can-you-enroll-with-the-microsoft-intune-app"></a>您可以使用 Microsoft Intune 應用程式註冊何種裝置？  
您可以註冊公司所擁有的 Android 裝置, 您的組織已設定為與應用程式搭配使用。 應用程式支援 Android 6.0 和更新版本。 

## <a name="can-you-remove-a-computer-or-device-from-the-company-portal"></a>您可以從公司入口網站移除電腦或裝置嗎？
您可以從公司入口網站移除或重設電腦或裝置。 [移除]  與 [重設]  不同。

當從公司入口網站移除電腦或裝置時，即會從 Intune 取消註冊裝置。 取消註冊之後，將無法再從該裝置存取公司入口網站，而且有些公司資料也會從您的裝置上移除。 若要瞭解如何從公司入口網站中移除您的裝置, 請參閱下列連結:  

- [取消註冊您的 Android 裝置](unenroll-your-device-from-intune-android.md)
- [取消註冊 iOS 裝置](unenroll-your-device-from-intune-ios.md)
- [取消註冊 macOS 裝置](unenroll-your-device-from-intune-macos.md)
- [取消註冊您的 Windows 裝置](unenroll-your-device-from-intune-windows.md)

當您重設電腦或裝置時，公司入口網站會嘗試將電腦或裝置重設為製造商的預設設定。 重設裝置會移除裝置中的所有公司與個人資料。 如果您遺失您的裝置，則也可以從公司入口網站進行遠端重設。  

若要瞭解如何重設您的裝置, 請參閱[從公司入口網站網站重設您的裝置](reset-erase-your-device-cpwebsite.md)。  

## <a name="can-you-remove-a-computer-or-device-from-the-microsoft-intune-app"></a>您可以從 Microsoft Intune 應用程式移除電腦或裝置嗎？
否, 您無法從 Microsoft Intune 應用程式中移除公司擁有的裝置。  

## <a name="what-if-i-cant-see-my-device-in-the-company-portal-or-microsoft-intune-app"></a>如果我在公司入口網站或 Microsoft Intune 應用程式中看不到我的裝置, 該怎麼辦？
您必須先將裝置新增到公司入口網站，才能看到該裝置。 前往您系統管理員建議的公司入口網站，並遵循您裝置適用的步驟。 此外也無法再看到您公司所擁有及管理的裝置。

如果您使用的是 Microsoft Intune 應用程式, 您只會看到目前正在使用的裝置。 應用程式中不會顯示其他已註冊的裝置。  

## <a name="where-else-can-i-go-for-help"></a>我還能去哪裡尋求協助？  
若要針對常見問題和問題進行疑難排解, 請參閱下列平臺特定檔:  

- [修正 Android 裝置常見的問題](check-compliance-on-your-device-android.md)  
- [修正 iOS 裝置常見的問題](troubleshoot-your-device-ios.md)
- [修正 macOS 裝置常見的問題](troubleshoot-your-device-macos.md)
- [修正 Windows 裝置常見的問題](troubleshoot-your-device-windows.md)

您也可以與支援人員聯繫。 公司入口網站和 Microsoft Intune 應用程式提供列出連絡人資訊的說明及支援頁面, 以及回報問題的方式。 您組織的[公司入口網站網站](https://go.microsoft.com/fwlink/?linkid=2010980)也提供連絡人資訊。  

## <a name="next-steps"></a>後續步驟  

從註冊開始, 這是您裝置平臺的專屬協助:  

- [使用您的 Android 裝置](using-your-android-device-with-intune.md)
- [使用您的 iOS 裝置](using-your-ios-device-with-intune.md)
- [使用您的 macOS 裝置](using-your-macos-device-with-intune.md)
- [使用您的 Windows 裝置](using-your-windows-device-with-intune.md)
- [使用公司入口網站](using-the-intune-company-portal-website.md)



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
ms.openlocfilehash: 2c0d3484311d044842daf6718b306d45fc93edf2
ms.sourcegitcommit: bccfbf1e3bdc31382189fc4489d337d1a554e6a1
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2019
ms.locfileid: "67545937"
---
# <a name="enroll-device-for-access-to-work-or-school-resources"></a>註冊裝置存取公司或學校資源
若要註冊您的裝置，並取得電子郵件和應用程式的存取權，您必須安裝 Intune 公司入口網站應用程式或 Microsoft Intune 應用程式。 當您註冊時，您的組織已設定，例如密碼、 PIN 和加密，基本的管理原則會套用到您的裝置。 一旦您的裝置設定符合所有組織的需求，您就可以從幾乎任何地方，安全地存取公司資訊。  

公司入口網站和 Microsoft Intune 的應用程式保護已註冊的裝置藉由確保您的裝置設定符合您的組織原則。 

公司入口網站應用程式也會：  
* 分開保留您的個人和工作資訊。  
* 可讓您輕鬆地尋找並安裝相關的工作和學校應用程式。   

## <a name="get-the-apps"></a>取得應用程式
取得公司入口網站：

- 從平台專屬的應用程式市集安裝公司入口網站應用程式。 在某些情況下，您的組織會為您安裝公司入口網站應用程式。  
- 移至[公司入口網站](https://go.microsoft.com/fwlink/?linkid=2010980)從瀏覽器存取應用程式。  

如果您必須使用 Microsoft Intune 應用程式，您的組織會替您安裝。  


## <a name="what-information-can-my-company-see-when-i-enroll"></a>當我註冊時，我的公司可以看到哪些資訊？
您的裝置註冊之後，您的組織支援人員只能看到與工作相關的資訊。 他們無法看到您的個人資訊。 如果您要註冊個人裝置的實際運作，供[了解有什麼可以和無法看到](what-info-can-your-company-see-when-you-enroll-your-device-in-intune.md)。  


## <a name="whats-the-difference-between-the-apps-and-the-website"></a>應用程式與網站之間的差異為何？
使用 Windows 10、 iOS、 macOS 和 Android 裝置的公司入口網站應用程式。 它與無縫整合您的裝置各平台。 網站版本可從任何裝置存取，不論您使用哪種裝置，都能提供您相同且通用的體驗。 

Microsoft Intune 應用程式是公司擁有的 Android 裝置。  

## <a name="what-kind-of-devices-can-you-enroll-with-company-portal"></a>您可以使用公司入口網站註冊的裝置種類？
- 使用 iOS (例如 iPhone 和 iPad) 及 macOS (例如 MacBook 和 iMac) 的 Apple 裝置
- Android 裝置
- Windows 裝置
    - Windows 10 Mobile
    - Windows 10 Desktop
    - Windows Phone 8.1
    - Windows 8.1

## <a name="what-kind-of-devices-can-you-enroll-with-the-microsoft-intune-app"></a>您可以使用 Microsoft Intune 應用程式註冊的裝置種類？  
您可以註冊公司擁有的 Android 裝置，您的組織已設定以搭配應用程式。 應用程式支援 Android 6.0 和更新版本。 

## <a name="can-you-remove-a-computer-or-device-from-the-company-portal"></a>您可以從公司入口網站移除電腦或裝置嗎？
您可以從公司入口網站移除或重設電腦或裝置。 [移除]  與 [重設]  不同。

當從公司入口網站移除電腦或裝置時，即會從 Intune 取消註冊裝置。 取消註冊之後，將無法再從該裝置存取公司入口網站，而且有些公司資料也會從您的裝置上移除。 若要了解如何從公司入口網站移除裝置，請參閱下列連結：  

- [取消註冊您的 Android 裝置](unenroll-your-device-from-intune-android.md)
- [取消註冊 iOS 裝置](unenroll-your-device-from-intune-ios.md)
- [取消註冊 macOS 裝置](unenroll-your-device-from-intune-macos.md)
- [取消註冊您的 Windows 裝置](unenroll-your-device-from-intune-windows.md)

當您重設電腦或裝置時，公司入口網站會嘗試將電腦或裝置重設為製造商的預設設定。 重設裝置會移除裝置中的所有公司與個人資料。 如果您遺失您的裝置，則也可以從公司入口網站進行遠端重設。  

若要了解如何重設您的裝置，請參閱[從公司入口網站將裝置重設](reset-erase-your-device-cpwebsite.md)。  

## <a name="can-you-remove-a-computer-or-device-from-the-microsoft-intune-app"></a>可以從 Microsoft Intune 應用程式移除電腦或裝置嗎？
否，沒有任何方式，讓您能夠從 Microsoft Intune 應用程式中移除屬公司擁有的裝置。  

## <a name="what-if-i-cant-see-my-device-in-the-company-portal-or-microsoft-intune-app"></a>如果我看不到我的公司入口網站或 Microsoft Intune 的應用程式中的裝置？
您必須先將裝置新增到公司入口網站，才能看到該裝置。 前往您系統管理員建議的公司入口網站，並遵循您裝置適用的步驟。 此外也無法再看到您公司所擁有及管理的裝置。

如果您使用 Microsoft Intune 應用程式，您只會看到您目前正在使用的裝置。 其他已註冊的裝置不會顯示在應用程式。  

## <a name="where-else-can-i-go-for-help"></a>我還能去哪裡尋求協助？  
若要疑難排解常見問題和疑問，請參閱這些平台特定文件：  

- [修正 Android 裝置常見的問題](check-compliance-on-your-device-android.md)  
- [修正 iOS 裝置常見的問題](troubleshoot-your-device-ios.md)
- [修正 macOS 裝置常見的問題](troubleshoot-your-device-macos.md)
- [修正 Windows 裝置常見的問題](troubleshoot-your-device-windows.md)

您可以也連絡支援人員。 公司入口網站和 Microsoft Intune 應用程式提供說明和支援列出的連絡資訊和如何回報問題的頁面。 連絡資訊也會提供在您的組織[公司入口網站](https://go.microsoft.com/fwlink/?linkid=2010980)。  

## <a name="next-steps"></a>後續步驟  

取得開始註冊您的裝置平台專屬的協助：  

- [使用您的 Android 裝置](using-your-android-device-with-intune.md)
- [使用您的 iOS 裝置](using-your-ios-device-with-intune.md)
- [使用您的 macOS 裝置](using-your-macos-device-with-intune.md)
- [使用您的 Windows 裝置](using-your-windows-device-with-intune.md)
- [使用公司入口網站](using-the-intune-company-portal-website.md)



---
title: "如何教育終端使用者關於 Microsoft Intune 的事項 | Microsoft Intune"
description: "與您的使用者共用資訊，以成功完成 Intune 部署。"
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 04/10/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 48914533-f138-4dc0-8b93-4cea3ac61f7b
ms.reviewer: robstack
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 8b2bd3ecba0b597bc742ea08872ffe8fc58155cf
ms.openlocfilehash: abba595672fa88efc022128ec8751cb27d14b089
ms.lasthandoff: 04/24/2017


---

# <a name="how-to-educate-your-end-users-about-microsoft-intune"></a>如何指導使用者使用 Microsoft Intune

Microsoft Intune 可協助您提供行動裝置給您的工作人員，同時保護公司資料。 有許多步驟可確保成功部署，包括透過[免費試用版](/Intune/Understand/mobile-device-management-trial-guide-microsoft-intune)評估 Intune、[保護您的電子郵件](https://docs.microsoft.com/intune/understand-explore/common-ways-to-use-intune#protecting-your-on-premises-email-and-data-so-it-can-be-safely-accessed-by-mobile-devices)和[將 Intune SDK 嵌入您的應用程式](/intune/develop/intune-app-sdk)。

這些技術全都無法確保您的使用者了解您管理他們裝置的原因有多重要。 事實上，許多使用者可能會感覺您正在侵害他們的隱私權 - 特別是若您要將 Intune 部署為 [BYOD 解決方案](/enterprise-mobility-security/solutions/byod-design-considerations-guide)。

> [!Important]
> 了解並主動解決使用者對於為何需要管理裝置的顧慮，對於成功部署而言很重要。

採用不只是讓技術運作，並分散給所有工作人員，而是讓您的使用者擁抱 Intune 提供的安全存取。 使用者可能受到企業行動力的脅迫，因為一般來說，我們並未向他們說明他們對於企業行動力需要知道的事，以及它能 (和不能) 做到的事。

## <a name="things-to-consider-about-your-end-users"></a>關於您的終端使用者應該考慮的事項

__您的終端使用者具有什麼經驗層級？__ 您的終端使用者可能有各種不同技術的各種使用經驗。 這些經驗可能是正面和負面，從他們為子女拍下的令人印象深刻的相片，到他們的裝置掉入水槽並遺失任何未備份資料的時刻。 這些經驗影響了他們接近技術的方式，以及他們對於個人和公司使用裝置有什麼看法。

__行動力管理對我有什麼意義？__ 使用者可能沒有完全了解您對他們的裝置和資訊具有 (和不具有) 何種存取權。 使用者可能會對於 IT 與領導階層追蹤他們的每次移動有所顧慮。 這對於經驗較少的使用者而言可能特別令人擔心，他們可能會認為裝置上的所有活動都是私人活動。 較有經驗的使用者可能會因為「老大哥」監視他們的裝置而有特定的恐懼，並且可能向同事宣揚其顧慮。

__這可能會對我的終端使用者造成什麼不便？__ 安裝應用程式、註冊裝置，以及維持相容性需要時間。 確保您的公司資料安全性是任何 Intune 部署的第一要務，但在個人裝置上要求不合理的密碼會導致您的使用者憎惡您管理他們的裝置。 在攸關業務的電話會議中傳送必要的應用程式更新，可能會造成使用者變得較不具生產力，破壞了提供他們行動裝置的目的。

## <a name="things-you-should-do"></a>您應該做的事

安撫這些使用者顧慮，可讓您的部署更順暢。 我們有一份方法清單，可以讓您的終端使用者更容易接受裝置管理。

* __提供資源。__ Intune 文件有各種不同的內容，以協助您的終端使用者了解如何執行特定工作，例如註冊和為他們的裝置進行疑難排解。 這當中最重要的是使用者從公司入口網站傳送到的文章，分為幾個章節：公司入口網站應用程式安裝和 Intune 註冊、使用者可在裝置上執行的一般工作，以及疑難排解。 這份文件提供於我們的說明中，指出如何[使用受管理的裝置來完成工作](/Intune/EndUser/use-managed-devices-to-get-work-done)。

* __可以存取。__ 使用者需要知道他們可以從何處得到裝置的協助。 [自訂公司入口網站](/Intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-7)時，請確定您包含 IT 系統管理員連絡資訊，讓您的使用者可以在需要時取得協助。

* __個人化。__ 提供非您的部署專屬的指示可能會讓使用者覺得您沒有思考過他們的經驗。 您可以使用這個[可供 IT 系統管理員自訂的使用者 Intune 註冊範本](https://gallery.technet.microsoft.com/office/Intune-End-User-Enrollment-3a0c9b0c)，為終端使用者建立您自己的註冊指示。

* __找出溝通的不同方式。__ 如同[不同學習模式](https://www.umassd.edu/dss/resources/facultystaff/howtoteachandaccommodate/howtoaccommodatedifferentlearningstyles/)，使用者使用資訊的慣用方法。 對於偏好影片而非文件的使用者，我們提供[如何註冊各種裝置類型的影片版本](https://channel9.msdn.com/Series/IntuneEnrollment)，以及 Channel 9 上的更多內容。 這些影片可直接嵌入您自己的 [SharePoint 網站](https://support.office.com/article/Embed-a-video-from-Office-365-Video-59e19984-c34e-4be8-889b-f6fa93910581)，或下載本機複本 - 影片的複本或是只有音訊播放軌的複本。

* __有意識。__ 您的終端使用者經驗將會影響您的生產力，而了解他們的經驗將能幫助您在他們前來時針對問題進行疑難排解。 了解終端使用者如何取得他們的應用程式，可以讓您更輕鬆地診斷他們遇到什麼問題，並且可以協助您更快地修正問題。

* **Android**
  * [在 Intune 上使用 Android 裝置](https://docs.microsoft.com/Intune/EndUser/using-your-android-device-with-intune)
  * [Android 使用者如何取得其應用程式](how-your-android-users-get-their-apps.md)

* **iOS**
  * [在 Intune 上使用 iOS 裝置](https://docs.microsoft.com/intune-user-help/using-your-ios-or-macos-device-with-intune)
  * [iOS 使用者如何取得其應用程式](how-your-ios-users-get-their-apps.md)

* **Windows**
  * [在 Intune 上使用 Windows 裝置](https://docs.microsoft.com/Intune/EndUser/using-your-windows-device-with-intune)
  * [Windows 使用者如何取得其應用程式](how-your-windows-users-get-their-apps.md)

* __事先告知。__ 清楚地告訴您的使用者您要管理他們裝置上的什麼內容。 告訴他們您要收集的資料類型，以及收集的原因。 告知他們您打算如何使用所有資產資料。 [Microsoft 相信您有權盡可能知道我們如何處理雲端中的客戶資料](https://www.microsoft.com/trustcenter/about/transparency)，並且我們相信這個觀點可以大幅提升終端使用者對 Intune 的滿意度。

>[!Note]
> 透明度，在任何可能之處，都是部署成功的基礎。

您想要結合信任與經過精心設計的相容性原則，以確定終端使用者知道，即使您「可以」查看特定類型的個人資料，您也「不想」，以及您侵犯他們的隱私權時可能要負的責任。 與您的法務和人事部門一起精心製作一份聲明，對特別難相處的員工可能有效。


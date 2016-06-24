---
# required metadata

title: 什麼是新資料庫 | Microsoft Intune
description:
keywords:
author: Lindavr
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: ed2db991-4729-49a7-a1e6-be2ffa0d03d1

# optional metadata

ROBOTS: noindex,nofollow
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---


## 2015 年 9 月
### 行動裝置與應用程式管理更新
所有的 Intune iOS 管理功能現在都支援 iOS 9

如需 iOS 9 管理功能的詳細資訊，請參閱[這篇部落格文章](http://blogs.technet.com/b/microsoftintune/archive/2015/09/09/day-zero-support-for-ios-9-with-intune.aspx) iOS 新的行動應用程式組態原則 您可以使用新的行動應用程式組態原則，自動提供 iOS 應用程式執行時可能需要的設定。

例如，您可以提供網路連接埠或使用者名稱。 如需詳細資訊，請參閱[在 Microsoft Intune 中使用行動應用程式組態原則設定應用程式](https://technet.microsoft.com/library/mt481447.aspx)

 讓 iOS 9 使用者更容易管理應用程式

 在本版本中，您可以將 Intune 所管理的已部署應用程式帶給 iOS 9 使用者。

 若是舊版 iOS，當您要部署應用程式且裝置上已安裝該應用程式未受管理的版本時，仍然必須要求使用者先手動解除安裝應用程式，Intune 才可安裝受管理的應用程式。 但從本版本的 Intune 開始，您現在可以提示 iOS 9 裝置的使用者允許 Intune 接管應用程式的管理，並套用任何相關的行動應用程式管理原則。

### Windows 10 管理 您可以使用新的 [Windows 10 一般組態原則](https://technet.microsoft.com/library/mt404697.aspx)，為執行 Windows 10 和 Windows 10 行動裝置版的已註冊裝置，設定密碼、裝置、瀏覽器和其他設定。
建立應用程式並部署到已註冊的 Windows 10 裝置 透過 MDM 的 Windows Installer (&#42;.msi) 是新的軟體安裝程式類型，可讓您建立 Windows Installer 應用程式並部署到執行 Windows 10 的已註冊裝置。

**如需詳細資訊，請參閱[開始使用 Microsoft Intune 部署應用程式](https://technet.microsoft.com/library/dn646955.aspx)**
* 變更並新新 Microsoft 公司入口網站應用程式 本版公司入口網站應用程式的變更如下：
* iOS
* Microsoft 會自動收集有關公司入口網站效能和使用的匿名資料，以改善 Microsoft 產品和服務。

### 使用者可以使用裝置上的使用狀況資料設定來關閉資料收集，但系統管理員無法控制資料收集，也無法變更使用者在這項設定中的選取項目。
**iPhone 6 及更新版本的全螢幕解析度支援**

|修正 Bug 以提升安全性|Intune 文件的新內容 -- 2015 年 9 月|
|----|--------|
|[新增主題](https://technet.microsoft.com/library/mt404697.aspx)|Name
| [詳細資料](https://technet.microsoft.com/library/mt481447.aspx)|Microsoft Intune 的 Windows 10 組態原則設定 |

**這是新的組態原則，可讓您管理執行 Windows 10 和 Windows 10 行動裝置版之裝置上的設定和功能。**

|在 Microsoft Intune 中使用行動裝置應用程式組態原則設定應用程式|這是新的原則類型，可讓您自動提供使用者執行 iOS 應用程式時可能需要的設定。|
|----|-------|
|[更新的主題](https://technet.microsoft.com/library/dn743712.aspx)|Name|

## 詳細資料
### 利用 Microsoft Intune，使用原則管理電腦和行動裝置
* 已更新並包含最新資訊，以協助您了解及建立原則。 2015 年 8 月 行動裝置與應用程式管理更新 Intune 註冊與公司存取的 條款和條件 [現在透過原則來管理](https://technet.microsoft.com/library/mt405893.aspx)。
* 您可以設定不同的條款和條件組合，以符合特定使用者群組需求。 例如，您可以部署不同語言的條款和條件，以依照地理位置來定義使用者群組。
* 您也可以 [編輯您的條款和條件](https://technet.microsoft.com/library/mt405893.aspx#BKMK_TCVers) ，以及指定是否要遞增版本號碼，並要求使用者同意新的條款和條件才能使用公司入口網站。 已重新命名一些 Intune 原則 ，使其在產品內更一致，並讓您更容易找到。 如需所有可用 Intune 原則的清單，請參閱[利用 Microsoft Intune，使用原則管理電腦和行動裝置](https://technet.microsoft.com/library/dn743712.aspx)
* PKCS #12 (.PFX) 憑證設定檔 適用於 Android 4.0 或更新版本以及 Windows 10 (Desktop 和行動裝置版) 及更新版本。
* 使用 .PFX 不需要 NDES 伺服器。 若要了解如何使用 .PFX 憑證設定檔，請參閱[透過 Microsoft Intune 利用憑證設定檔存取公司資源](http://technet.microsoft.com/library/dn818904.aspx)。
* 適用於 Windows 10 Desktop 和行動公司界限設定 能夠進行細緻的 VPN 設定，如[協助使用者搭配使用 VPN 設定檔與 Microsoft Intune 來連線到工作](https://technet.microsoft.com/library/dn818905.aspx)中所述。 Android 的 OneDrive App 現在支援多重身分識別。 [您可以管理的 Microsoft 應用程式清單](https://technet.microsoft.com/library/dn708489.aspx)中描述這項更新和行動裝置應用程式管理原則的其他更新 iOS 啟用鎖定略過。

### 如果屬公司所擁有的 iOS 裝置受到啟用鎖定的保護，您必須輸入使用者的 Apple ID 和密碼，才能清除或重新啟動裝置。
當使用者離職並歸還屬公司所擁有的裝置時，如果未關閉啟用鎖定，可能會是項挑戰。 為了協助解決這個問題，您可以使用 [Intune 啟用鎖定略過](https://technet.microsoft.com/library/mt414176.aspx)。
電腦的條件存取
* 您現在可以設定電腦的條件式存取原則。
* 這可讓 Office 桌面應用程式存取 Exchange Online 和 SharePoint Online 服務。
* 若要啟用電腦的條件存取原則，此電腦必須加入網域或相容。

### 如需啟用電腦條件式存取需求的完整清單，請參閱[使用 Microsoft Intune 管理電子郵件和 SharePoint 的存取](http://technet.microsoft.com/library/dn818907).aspx) 的 開始使用 一節。
如需啟用電子郵件存取之條件式存取可以設定的選項，請參閱[使用 Microsoft Intune 管理電子郵件存取](https://technet.microsoft.com/library/dn705841.aspx)。

**如需啟用 SharePoint Online 之條件式存取可以設定的選項，請參閱[以 Microsoft Intune 管理 SharePoint Online 存取](https://technet.microsoft.com/library/dn705844.aspx)。**

變更並新新 Microsoft 公司入口網站應用程式

### 本版公司入口網站應用程式的變更如下：
**Android**

|如果使用者尚未註冊要管理的裝置，則在登入後會立即看到裝置註冊指示。|Intune 文件的新內容 -- 2015 年 8 月|
|-----|-------|
|[新增主題](https://technet.microsoft.com/library/mt414176.aspx)|標題|

**詳細資料**

|使用 Microsoft Intune 的啟用鎖定略過協助保護 iOS 裝置|了解當使用者離職並歸還鎖定的裝置時，如何使用 Intune 略過 iOS 啟用鎖定。|
|-----|-------|
|[更新的主題](https://technet.microsoft.com/library/dn708489.aspx)|標題
|[詳細資料](http://technet.microsoft.com/library/dn743712.aspx)|可與 Microsoft Intune 行動應用程式管理原則搭配使用的 Microsoft 應用程式|
<!---
## July 2015
July updates for Intune are limited to behind-the-scenes enhancements that allow us to continue providing you with a high-quality service experience. New features are not included in this service update.

### Intune Onboarding benefit
Microsoft offers the Intune Onboarding benefit for eligible plans. The Onboarding benefit lets you work remotely with Microsoft specialists to get your Intune environment ready for use. For more information, see [Microsoft Intune Onboarding benefit description](https://technet.microsoft.com/library/mt228266.aspx)
### Changes and updates to Microsoft Company Portal apps
The following changes have been made to the company portal apps in this release.

**Android**

Microsoft automatically collects anonymous data about the performance and use of the company portal to improve Microsoft products and services. End users can turn off data collection by using the Usage Data setting on their device, but administrators have no control over the data collection and cannot change the end user’s selection for this setting.--->


<!--HONumber=May16_HO2-->



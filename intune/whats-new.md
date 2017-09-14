---
title: "Microsoft Intune 的新功能"
titlesuffix: Azure portal
description: "了解 Intune Azure 入口網站中的新功能"
keywords: 
author: brenduns
ms.author: brenduns
manager: angrobe
ms.date: 09/01/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 791ed23f-bd13-4ef0-a3dd-cd2d7332c5cc
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: c4787c716f94e95ab98badf924273af5d02751f8
ms.sourcegitcommit: fa6aaf12611c3e03e38e467806fc30b1d0255e88
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2017
---
# <a name="whats-new-in-microsoft-intune"></a>Microsoft Intune 的新功能

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

了解每週的 Microsoft Intune 新功能 您也可以了解[即將推出的變更](#whats-coming)、關於服務的[重要通知](#notices)，以及[過去版本](whats-new-archive.md)的相關資訊。

> [!Note]
> 具備 Configuration Manager 的混合式部署於未來將會支援多數的這些功能。 如需新混合式功能的詳細資訊，請查看我們的[混合式新增功能](/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management)頁面。


<!-- Common categories:  
  ### Device enrollment
  ### Device management
  ### App management
  ### Device configuration
  ### Role-based access control
  ### Intune apps
  ### Monitor and troubleshoot

-->   


## <a name="week-of-august-21-2017"></a>2017 年 8 月 21 日這週

### <a name="device-enrollment"></a>裝置註冊
#### <a name="improvements-to-device-overview----1404453---"></a>裝置概觀改善 <!-- 1404453 -->  
裝置概觀改善現在會顯示已註冊的裝置，但不包含 Exchange ActiveSync 所管理的裝置。 Exchange ActiveSync 裝置與已註冊裝置的管理選項不同。 若要在 Azure 入口網站中檢視 Intune 中的已註冊裝置數目以及依平台的已註冊裝置數目，請移至 [裝置] > [概觀]。

### <a name="device-management"></a>裝置管理
#### <a name="improvements-to-device-inventory-collected-by-intune"></a>Intune 所收集裝置清查的改善
<!-- 961134, 1104426, 1281327, 1333543 -->
在此版本中，我們已對您管理的裝置所收集的清查資訊進行下列改善：
 
-   對於 Android 裝置，您現在可以將資料行新增至裝置清查，以顯示每個裝置的最新修補程式等級。 將 [Security patch level] (安全性修補程式等級) 資料行新增至裝置清單，以查看這項資訊。
-   當您篩選裝置檢視時，現在可以依其註冊日期篩選裝置。 例如，您可以只顯示在所指定日期之後註冊的裝置。
-   我們已改善 [Last Check-in Date] (最後一次簽入日期) 項目所使用的篩選。
-   在裝置清單中，您現在可以顯示公司所擁有裝置的電話號碼。
此外，您還可以使用篩選窗格，依電話號碼來搜尋裝置。
 
如需裝置清查的詳細資料，請參閱[如何檢視 Intune 裝置清查](device-inventory.md)。

#### <a name="conditional-access-support-for-macos-devices"></a>macOS 裝置的條件式存取支援 
<!-- 720172 -->
您現在可以設定條件式存取原則，要求 Mac 裝置向 Intune 註冊，並符合其裝置的合規性原則。 例如，使用者可以下載適用於 macOS 的 Intune 公司入口網站應用程式，並在 Intune 中註冊其 Mac 裝置。 Intune 會評估 Mac 裝置是否符合 PIN、加密、作業系統版本和系統完整性等需求。

- 深入了解 [macOS 裝置的條件式存取支援](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)。

#### <a name="company-portal-app-for-macos-is-in-public-preview----1484796---"></a>對 macOS 來說，公司入口網站應用程式目前為公開預覽 <!---1484796--->
公開預覽中目前提供 macOS 的公司入口網站應用程式，以於 Enterprise Mobility + Security 中進行條件式存取。 此版本支援 macOS 10.11 及更新版本。 若要下載，請前往 [https://aka.ms/macOScompanyportal](https://aka.ms/macOScompanyportal)。 


#### <a name="new-device-restriction-settings-for-windows-10"></a>Windows 10 的新裝置限制設定    
<!--1063965, 1308850  -->
在此版本中，我們已在下列類別中新增 [Windows 10 裝置限制設定檔](/intune/device-restrictions-windows-10)的新設定：

-   Windows Defender SmartScreen
-   App Store

#### <a name="updates-to-the-windows-10-endpoint-protection-device-profile-for-bitlocker-settings"></a>BitLocker 設定的 Windows 10 端點保護裝置設定檔更新
<!--1459533 -->    
在此版本中，我們已對 BitLocker 設定在 Windows 10 端點保護裝置設定檔中的運作方式進行下列改善：
 
在 [BitLocker OS 磁碟機設定] 下，針對 [具有不相容 TPM 晶片的 BitLocker] 設定，當您選取 [封鎖] 時，以前這會導致實際允許 BitLocker。 我們現在已修正這個問題，以在選取 BitLocker 時進行封鎖。
在 [BitLocker OS 磁碟機設定] 下，針對 [以憑證為基礎的資料修復代理程式] 設定，您現在可以明確地封鎖以憑證為基礎的資料修復代理程式。 不過，預設會允許代理程式。
在 [BitLocker 固定式資料磁碟機設定] 下，針對 [資料修復代理程式] 設定，您現在可以明確地封鎖資料修復代理程式。
如需詳細資訊，請參閱 [Windows 10 和更新版本的 Endpoint Protection 設定](endpoint-protection-windows-10.md)。


### <a name="app-management"></a>應用程式管理
#### <a name="new-signed-in-experience-for-android-company-portal-users-and-app-protection-policy-users----621669---"></a>Android 公司入口網站使用者和應用程式防護原則使用者的新登入體驗 <!-- 621669 -->
終端使用者現在可以使用 Android 公司入口網站應用程式來瀏覽應用程式、管理裝置以及檢視 IT 連絡人資訊，而不需要註冊其 Android 裝置。 此外，如果終端使用者已使用由 Intune 應用程式防護原則保護的應用程式，並啟動 Android 公司入口網站，則終端使用者無法再收到註冊裝置的提示。

### <a name="new-setting-in-the-android-company-portal-app-to-toggle-battery-optimization---1405990--"></a>Android 公司入口網站應用程式中用來切換電池最佳化的新設定 <!--1405990-->
適用於 Android 的公司入口網站應用程式中的 [設定] 頁面，具有新的設定，可讓使用者輕鬆關閉公司入口網站及 Microsoft Authenticator 應用程式的電池最佳化功能。 設定中所顯示的應用程式名稱，會依管理公司帳戶的應用程式而有所不同。 建議使用者關閉電池最佳化功能，以提升同步電子郵件與資料的公司應用程式效能。 

#### <a name="multi-identity-support-for-onenote-for-ios---------1234281---"></a>OneNote for iOS 的多重身分識別支援 <!-- 1234281 -->
終端使用者現在可以搭配使用不同的帳戶 (公司和個人) 與 Microsoft OneNote for iOS。 應用程式保護原則可以套用至工作筆記本中的公司資料，而不會影響其個人筆記本。 例如，原則可讓使用者在工作筆記本中尋找資訊，但會防止使用者將公司資料從工作筆記本複製並貼入個人筆記本。
 
- 深入了解支援 Intune 的[應用程式保護和多重身分識別](https://www.microsoft.com/cloud-platform/microsoft-intune-apps)的應用程式。

#### <a name="new-settings-to-allow-and-block-apps-on-samsung-knox-standard-devices"></a>在 Samsung KNOX Standard 裝置上允許或封鎖應用程式的新設定
<!-- 1305423 822899-->  
在此版本中，我們新增新的[裝置限制設定](device-restrictions-android.md)，可讓您指定下列應用程式清單：
 
- 允許使用者安裝的應用程式
- 封鎖使用者執行的應用程式
- 對使用者隱藏的裝置應用程式
 
您可依 URL、套件名稱，或從管理的應用程式清單中指定應用程式。

#### <a name="new-azure-ad-app-based-conditional-access-policy-ui-link-from-intune"></a>來自 Intune 的新 Azure AD 應用程式條件式存取原則 UI 連結
<!-- 1016201 -->
IT 管理員現在可以透過 Azure AD 工作負載中的新條件式存取原則 UI，來設定應用程式條件式存取原則。 Azure 入口網站的 [Intune 應用程式防護] 區段中，應用程式條件式存取會暫時保留不動，且會強制並存。 Intune 工作負載中另有提供方便的連結，可連至新的條件式存取原則 UI。

- 深入了解 [Azure AD 上的應用程式條件式存取](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-technical-reference)。


## <a name="notices"></a>通知

### <a name="ip-addresses-for-intune-updated----1175274---"></a>Intune 的 IP 位址已更新<!-- 1175274 -->
防火牆 Proxy 設定有[更新的 DNS 名稱和 IP 位址清單](/intune/network-bandwidth-use)。

### <a name="use-azure-active-directory-for-conditional-access----967947---"></a>使用 Azure Active Directory 進行條件式存取<!-- 967947 -->
Azure 入口網站的 Azure Active Directory 區段提供條件式存取，在設定 Office 365 Exchange Online 和 SharePoint Online 等雲端應用程式的原則時，可提供更強大而彈性的架構。  使用 [Azure Active Directory] 刀鋒視窗中的 [條件式存取] 來設定原則，以取代 Intune 主控台。 Intune 主控台中的現有原則，必須在 Azure 入口網站中重新建立。 如需詳細資訊，請參閱[建立 Azure AD 條件式存取原則](/intune/conditional-access-exchange-create.md#create-azure-ad-conditional-access-policies-in-intune-azure-preview)。

### <a name="direct-access-to-apple-enrollment-scenarios---951869--"></a>直接存取 Apple 註冊案例 <!--951869-->
對於在 2017 年 1 月之後建立的 Intune 帳戶，Intune 已經啟用使用 Azure 入口網站中的「註冊裝置」工作負載直接存取 Apple 註冊案例。 Apple 註冊預覽原本只能從 Intune 傳統入口網站中的連結存取。 在 2017 年 1 月之前建立的 Intune 帳戶需要進行一次性移轉，才能在 Azure 中使用這些功能。 移轉的排程尚未宣布，但將會盡快提供詳細資料。 如果您現有的帳戶無法存取 Azure 入口網站，我們強烈建議您建立試用帳戶來測試新的體驗。

### <a name="administration-roles-being-replaced-in-azure-portal"></a>Azure 入口網站中將被取代的系統管理角色
在 Intune 傳統入口網站 (Silverlight) 中使用的現有行動應用程式管理 (MAM) 系統管理角色 (參與者、擁有者或唯讀) 在 Intune Azure 入口網站中會被取代為一組新的、完整的角色型系統管理控制 (RBAC)。 當您移轉至 Azure 入口網站之後，必須將系統管理員重新指派至這些新的系統管理角色。 如需 RBAC 和新角色的詳細資訊，請參閱 [Microsoft Intune 的角色型存取控制](/intune/role-based-access-control)。



## <a name="whats-coming"></a>未來動態

#### <a name="ios-11-mail-app-will-support-oauth----1196951---"></a>iOS 11「郵件」應用程式將會支援 OAuth <!---1196951--->
Intune 條件式存取支援在 iOS 裝置上進行更安全的 OAuth 驗證。 為了支援進行更安全的驗證，iOS 公司入口網站應用程式的流程已有所改變。 當終端使用者在「郵件」應用程式中嘗試登入新的 Exchange 帳戶時，會出現網頁檢視提示。 在 Intune 中註冊時，使用者會看見要求允許原生「郵件」應用程式存取憑證的提示。 大多數的使用者都不再會看到任何隔離的電子郵件。 現有郵件帳戶會繼續使用基本驗證通訊協定，因此，這些使用者仍會收到隔離的電子郵件。 終端使用者的此登入體驗很類似於 Office Mobile 應用程式的模式。

### <a name="end-of-support-for-ios-80----1164477---"></a>結束對 iOS 8.0 的支援<!---1164477--->
受管理的應用程式和 iOS 公司入口網站應用程式需要 iOS 9.0 及更新版本才能存取公司資源。 今年 9 月前未更新的裝置將不再能存取公司入口網站或這些應用程式。 

### <a name="ui-updates-to-the-company-portal-website---1313244-part-2--"></a>公司入口網站的 UI 更新 <!--1313244 part 2-->
__精選 App 的更新__  
我們已將專用頁面新增至網站 (使用者可在其中瀏覽您選為精選的應用程式)，並對首頁上的 [精選] 區段進行一些 UI 調校。 您可以在[應用程式 UI 的新功能](whats-new-app-ui.md)頁面看到這些變更的樣子。


### <a name="end-of-support-for-android-43-and-lower----1171127-1326920----"></a>結束對 Android 4.3 和較舊版本的支援<!---1171127, 1326920 --->
受管理的應用程式和 Android 公司入口網站應用程式需要 Android 4.4 及更新版本才能存取公司資源。 10 月初前未更新的裝置將不再能存取公司入口網站或這些應用程式。 今年 12 月會強制淘汰所有已註冊的裝置，以致無法存取公司資源。 如果您使用不含 MDM 的應用程式保護原則，應用程式就不會接收更新，其體驗品質會隨著時間而降低。


### <a name="platform-support-reminder-windows-phone-81-mainstream-support-ended-july-11-2017"></a>平台支援提醒：Windows Phone 8.1 的主要支援已於 2017 年 7 月 11 日結束
<!-- 1327781 -->
Windows Phone 8.1 平台已於 2017 年 7 月 11 日結束主要支援。 Windows 8.1 電腦的支援不受影響。

受 Intune 服務管理的所有 Windows Phone 8.1 裝置沒有直接影響。 已註冊的裝置會繼續運作，而所有的原則、設定和應用程式也會一如預期般運作。 請注意，沒有以 Intune 服務內的 Windows Phone 8.1 平台為目標的改進，也沒有以 Windows Phone 8.1 公司入口網站應用程式為目標的改進。

我們建議您儘早將符合資格的 Windows Phone 8.1 裝置升級至 Windows 10 行動裝置版。 

### <a name="changes-in-support-for-the-intune-ios-company-portal-app-----1164474----"></a>Intune iOS 公司入口網站應用程式的支援變更 <!-- 1164474  -->
iOS 的 Microsoft Intune 公司入口網站應用程式很快將會有更新，屆時將只支援執行 iOS 9.0 或更新版本的裝置。 支援 iOS 8 的公司入口網站版本仍然可以使用非常短的一段時間。 不過，請注意，如果您也使用啟用 MAM 的 iOS 應用程式，我們支援 iOS 9.0 及更新版本，因此您會想要確保您的終端使用者更新到最新的作業系統。 

#### <a name="how-does-this-affect-me"></a>此變更對我造成什麼影響？
我們讓您事先知道這項資訊，雖然我們沒有特定的日期，您仍有時間進行規劃。 請確認您的使用者更新為 iOS 9+，且當公司入口網站應用程式發行時，要求您的終端使用者更新其公司入口網站應用程式。

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>我需要為這項變更做什麼準備？
鼓勵您的使用者更新到 iOS 9.0 或更新版本，以便完全利用 Intune 的新功能。  鼓勵使用者安裝新版的公司入口網站，並利用它將提供的新功能。

在 Azure 入口網站中移至 Intune，檢視 [裝置] > [所有裝置]，並依 iOS 版本篩選，以查看作業系統早於 iOS 9 的任何目前裝置。


### <a name="apple-to-require-updates-for-application-transport-security---748318--"></a>Apple 要求必須更新 Application Transport Security <!--748318-->
Apple 宣布將會強制執行 Application Transport Security (ATS) 的特定需求。 ATS 可用來對透過 HTTPS 進行的所有應用程式通訊，強制執行更嚴格的安全性。 此變更會影響使用 iOS 公司入口網站應用程式的 Intune 客戶。

我們已透過 Apple TestFlight 方案，提供符合新 ATS 需求的 iOS 版公司入口網站應用程式。 如果您想試用該版本以便測試 ATS 合規性，請傳送電子郵件到 <a href="mailto:CompanyPortalBeta@microsoft.com?subject=Register to TestFlight ATS Company Portal app">CompanyPortalBeta@microsoft.com</a>，並附上您的姓氏、名字、電子郵件地址和公司名稱。 如需詳細資訊，請檢閱我們的 [Intune 支援部落格](https://aka.ms/compportalats)。

### <a name="see-also"></a>另請參閱
* [Microsoft Intune 部落格](http://go.microsoft.com/fwlink/?LinkID=273882)
* [雲端平台藍圖](https://www.microsoft.com/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)
* [公司入口網站 UI 中的新增功能](whats-new-app-ui.md)
* [前幾個月的新功能](whats-new-archive.md)

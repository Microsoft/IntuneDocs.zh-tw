---
title: Microsoft Intune 的新功能 - Azure | Microsoft Docs
titlesuffix: ''
description: 了解 Intune Azure 入口網站中的新功能
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 07/30/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 791ed23f-bd13-4ef0-a3dd-cd2d7332c5cc
ms.reviewer: dougeby
ms.suite: ems
/ms.custom: intune-azure
ms.openlocfilehash: ff2774b76bceeeeaecec7a4dc74876b11706d574
ms.sourcegitcommit: 56a8a3c8974f54f0f9ecc1e5b43581502ecc348e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/07/2018
ms.locfileid: "39614508"
---
# <a name="whats-new-in-microsoft-intune"></a>Microsoft Intune 的新功能
[!INCLUDE [azure_portal](./includes/azure_portal.md)]

了解每週的 Microsoft Intune 新功能 您也可以了解[即將推出的變更](#whats-coming)、關於服務的[重要通知](#notices)，以及[過去版本](whats-new-archive.md)的相關資訊。 某些功能在首度發行時可能會花費數週的時間，而可能無法在第一週就提供給所有客戶。

> [!Note]
> 如需混合式行動裝置管理 (MDM) 的新功能資訊，請參閱[混合式新功能頁面](/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management)。


<!-- Common categories:  
### App management
### Device configuration
### Device enrollment
### Device management
### Intune apps
### Monitor and troubleshoot
### Role-based access control

-->   

## <a name="week-of-july-23-2018"></a>2018 年 7 月 23 日當週

### <a name="app-management"></a>應用程式管理

####  <a name="windows-apps-file-extensions----1884873---"></a>Windows 應用程式副檔名 <!-- 1884873 -->
Windows 應用程式的副檔名現在包含 *.msi*、*.appx*、*.appxbundle*、*.msix* 和 *.msixbundle*。 您可以依序選取 [Mobile Apps] > [應用程式] > [新增] 在 Microsoft Intune 中新增應用程式。 隨即顯示 [新增應用程式] 窗格，讓您可以選取 [應用程式類型]。 選取可讓您上傳應用程式套件檔案的應用程式類型，選取 [應用程式套件檔案]，然後輸入具有適當副檔名的安裝檔。

#### <a name="line-of-business-lob-app-support-for-macos----1895847---"></a>macOS 的企業營運 (LOB) 應用程式支援 <!-- 1895847 -->
Microsoft Intune 可讓 macOS LOB 應用程式部署為**必要**或**註冊可用**。 終端使用者可以使用適用於 macOS 的公司入口網站或[公司入口網站](https://portal.manage.microsoft.com)，來取得部署為**可用**的應用程式。

#### <a name="ios-built-in-app-support-for-kiosk-mode----2051098---"></a>kiosk 模組的 iOS 內建應用程式支援 <!-- 2051098 -->
除了市集應用程式和受控應用程式，您現在可以選取在 iOS 裝置上以 kiosk 模式執行的內建應用程式 (例如 Safari)。

#### <a name="edit-your-office-365-pro-plus-app-deployments----2150145---"></a>編輯 Office 365 Pro Plus 應用程式部署 <!-- 2150145 -->
身為 Microsoft Intune 系統管理員，您可以更有效率地編輯 Office 365 Pro Plus 應用程式部署。 此外，您不再需要刪除部署，就能變更套件的任何內容。 在 Azure 入口網站中，選取 [Microsoft Intune] > [行動裝置應用程式] > [應用程式]。 從應用程式的清單中，選取您的 Office 365 Pro Plus 套件。  


#### <a name="updated-intune-app-sdk-for-android-is-now-available----2744271--"></a>現在已提供更新的適用於 Android 的 Intune App SDK <!-- 2744271-->

已提供適用於 Android 的 Intune App SDK 的更新版本，以支援 Android P 版本。 如果您是應用程式開發人員，並使用適用於 Android 的 Intune SDK，則必須安裝 Intune App SDK 的更新版本，以確保 Android 應用程式中的 Intune 功能在 Android P 裝置上可以繼續如預期般運作。 這個版本的 Intune App SDK 提供了一個執行 SDK 更新的內建外掛程式。 您不需要重寫任何已整合的現有程式碼。 如需詳細資訊，請參閱[適用於 Android 的 Intune SDK](https://github.com/msintuneappsdk/ms-intune-app-sdk-android) \(英文\)。 如果您使用 Intune 舊的徽章樣式，建議您使用 [公事包] 圖示。 如需商標詳細資料，請參閱[此 GitHub 存放庫](https://github.com/msintuneappsdk/intune-app-partner-badge) \(英文\)。


### <a name="device-configuration"></a>裝置設定

#### <a name="use-smime-to-encrypt-and-sign-a-users-multiple-devices-----1333642---"></a>使用 S/MIME 加密和簽署使用者的多個裝置 <!-- 1333642 -->
此更新包括使用新匯入之憑證設定檔的 S/MIME 電子郵件加密 ([裝置設定] > [設定檔] > [建立設定檔] > 選取平台 > [PKCS imported certificate] \(PKCS 匯入的憑證\) 設定檔類型)。 在 Intune 中，您可以匯入 PFX 格式的憑證。 Intune 接著可以將這些相同的憑證提供給單一使用者所註冊的多個裝置。 這也包括：

- 原生 iOS 電子郵件設定檔支援啟用 PFX 格式之已匯入憑證的 S/MIME 加密。
- Windows Phone 10 裝置上的原生郵件應用程式會自動使用 S/MIME 憑證。
- 私人憑證可以跨多個平台提供。 但並非所有電子郵件應用程式都支援 S/MIME。
- 在其他平台上，您可能需要手動設定郵件應用程式來啟用 S/MIME。  
- 支援 S/MIME 加密的電子郵件應用程式可能會以 MDM 無法支援的方式來處理 S/MIME 電子郵件加密的憑證擷取 (例如從其發行者的憑證存放區中讀取)。

其支援：Windows、Windows Phone 10、macOS、iOS、Android

#### <a name="create-device-compliance-policy-using-firewall-settings-on-macos-devices----1497640---"></a>在 macOS 裝置上使用防火牆設定建立裝置合規性原則 <!-- 1497640 -->
當您建立新的 macOS 合規性原則 ([裝置合規性] > [原則] > [建立原則] >  [平台：macOS] > [系統安全性]) 時，會有一些可用的新 [防火牆] 設定： 

- **防火牆**：設定您環境中處理連入連線的方式。
- **連入連線**：除了基本網際網路服務所需的連線 (例如 DHCP、Bonjour 及 IPSec) 之外，[封鎖] 所有連入連線。 這項設定也會封鎖所有的共用服務。
- **隱形模式**：[啟用] 隱形模式以防止電腦回應探查要求。 電腦會繼續回應已授權應用程式的連入要求。

適用對象：macOS 10.12 和更新版本

#### <a name="new-wi-fi-device-configuration-profile-for-windows-10-and-later----1879077---"></a>Windows 10 和更新版本的新 Wi-Fi 裝置組態設定檔 <!-- 1879077 -->
您目前可以使用 XML 檔案來匯入和匯出 Wi-Fi 設定檔。 透過此更新，您可以直接在 Intune 中建立 Wi-Fi 裝置組態設定檔，如同一些其他平台。

若要建立設定檔，請開啟 [裝置設定] > [設定檔] > [建立設定檔] > [Windows 10 和更新版本] > [Wi-Fi]。 

適用於 Windows 10 及更新版本。

#### <a name="kiosk---obsolete-is-grayed-out-and-cant-be-changed----2149998-eeready---"></a>Kiosk - 已淘汰變成灰色，而且無法變更 <!-- 2149998 eeready -->
[Kiosk 功能](device-restrictions-windows-10.md#kiosk-preview---obsolete) ([裝置設定] > [設定檔] > [建立設定檔] > [Windows 10 和更新版本] > [裝置限制]) 會淘汰，並取代為 [Windows 10 和更新版本的 Kiosk 設定](kiosk-settings.md). 透過此更新，[Kiosk - 已淘汰] 功能會變成灰色，而且無法變更或更新使用者介面。 

若要啟用 Kiosk 模式，請參閱[適用於 Windows 10 和更新版本的 Kiosk 設定](kiosk-settings.md)。

適用於 Windows 10 和更新版本、Windows Holographic for Business

#### <a name="apis-to-use-3rd-party-certification-authorities----2184013---"></a>使用協力廠商憑證授權單位的 API <!-- 2184013 -->
在此更新中，有 Java API 可讓協力廠商憑證授權單位與 Intune 和 SCEP 整合。 然後，使用者可將 SCEP 憑證新增至設定檔，並將它套用至使用 MDM 的裝置。

Intune 目前支援[使用 Active Directory 憑證服務的 SCEP 要求](certificates-scep-configure.md)。

#### <a name="toggle-to-show-or-not-show-the-end-session-button-on-a-kiosk-browser----2455253---"></a>切換在 Kiosk 瀏覽器上顯示或不顯示 [結束工作階段] 按鈕 <!-- 2455253 -->
您現在可以設定 Kiosk 瀏覽器是否顯示 [結束工作階段] 按鈕。 您可以在 [裝置設定] > [Kiosk (預覽)] > [Kiosk Web Browser] \(Kiosk 網頁瀏覽器\) 看到控制項。 如果開啟，則使用者按一下此按鈕時，應用程式會提示您確認結束工作階段。 確認時，瀏覽器會清除所有瀏覽資料，並巡覽回預設 URL。

#### <a name="create-an-esim-cellular-configuration-profile----2564077---"></a>建立 eSIM 行動數據組態設定檔 <!-- 2564077 -->
在 [裝置設定] 中，您可以建立 eSIM 行動數據設定檔。 您可以匯入檔案，其中包含您的行動電信業者所提供的行動數據啟用碼。 您接著可以將這些設定檔部署至啟用 eSIM LTE 的 Windows 10 裝置，例如 Surface Pro LTE 和其他具有 eSIM 功能的裝置。

確認您的[裝置支援 eSIM 設定檔](https://support.microsoft.com/help/4020763/windows-10-use-esim-for-cellular-data)與否。

適用於 Windows 10 及更新版本。 




### <a name="device-enrollment"></a>裝置註冊

#### <a name="automatically-mark-android-devices-enrolled-by-using-samsung-knox-mobile-enrollment-as-corporate----2404851---"></a>將使用 Samsung Knox Mobile Enrollment 所註冊的 Android 裝置自動標示為「公司」。 <!-- 2404851 -->
根據預設，使用 Samsung Knox Mobile Enrollment 所註冊的 Android 裝置現在會在 [Device Ownership] \(裝置擁有權\) 下標示為 [公司]。 在使用 Knox Mobile Enrollment 註冊之前，您不需要手動找出使用 IMEI 或序號的公司裝置。

### <a name="device-management"></a>裝置管理

#### <a name="bulk-delete-devices-on-devices-blade----1793693---"></a>裝置刀鋒視窗上的大量刪除裝置 <!-- 1793693 -->

您現在可以在 [裝置] 刀鋒視窗上同時刪除多部裝置。 選擇 [裝置] > [所有裝置] > 選取您要刪除的裝置 > [刪除]。 針對無法刪除的裝置，將會顯示警示。

## <a name="week-of-july-16-2018"></a>2018 年 7 月 16 日當週  

### <a name="more-opportunities-to-sync-in-the-company-portal-app-for-windows"></a>Windows 版公司入口網站應用程式中的更多同步機會  
Windows 版公司入口網站應用程式現在可讓您直接從 Windows 工作列和 [開始] 功能表起始同步。 如果同步裝置並取得公司資源存取權是您唯一的工作，這項功能特別有用。 若要存取這項新功能，請以滑鼠右鍵按一下已釘選到工作列或 [開始] 功能表的公司入口網站圖示。 在功能表選項 (也稱為捷徑清單) 中，選取 [同步此裝置]。 公司入口網站會開啟至 **[設定]** 頁面並起始您的同步。若要查看新功能，請參閱 [UI 的新功能](whats-new-app-ui.md)。   

### <a name="new-browsing-experiences-in-the-company-portal-app-for-windows"></a>Windows 版公司入口網站應用程式的新瀏覽體驗  

現在，在 Windows 版公司入口網站應用程式中瀏覽或搜尋應用程式時，您可以切換現有的 [磚] 檢視和新增的 [詳細資料] 檢視。 新的檢視會列出應用程式詳細資料，例如名稱、發佈者、發佈日期，以及安裝狀態。  

[應用程式] 頁面的 [已安裝] 檢視可讓您查看有關已完成和進行中之應用程式安裝的詳細資料。 若要查看新檢視的外觀，請參閱 [UI 的新功能](whats-new-app-ui.md)。  
### <a name="improved-company-portal-app-experience-for-device-enrollment-managers"></a>已改善裝置註冊管理員的公司入口網站應用程式體驗  
當裝置註冊管理員 (DEM) 登入 Windows 版公司入口網站應用程式時，應用程式現在只會列出 DEM 目前執行中的裝置。 這項改善會減少之前應用程式在嘗試顯示所有 DEM 註冊裝置時所發生的逾時。  


## <a name="week-of-july-9-2018"></a>2018 年 7 月 9 日當週

### <a name="app-management"></a>應用程式管理

### <a name="block-app-access-based-on-unapproved-device-vendors-and-models-----1425689----"></a>依據未經核准的裝置廠商和型號來封鎖應用程式存取 <!-- 1425689 ! -->
Intune IT 系統管理員可以透過 Intune 應用程式防護原則，強制執行 Android 製造商和/或 iOS 型號的指定清單。 IT 系統管理員可以提供以分號分隔的製造商清單 (適用於 Android 原則) 及裝置型號清單 (適用於 iOS 原則)。 Intune 應用程式防護原則僅適用於 Android 和 iOS。 針對此指定清單，將可以執行兩個個別的動作：
- 針對未指定的裝置，封鎖其存取應用程式的能力。
- 或是針對未指定的裝置，選擇性地抹除該裝置上的公司資料。 

若沒有符合原則需求，使用者將無法存取目標應用程式。 根據設定的不同，系統可能會封鎖該使用者，或選擇性地抹除其位於應用程式內的公司資料。 在 iOS 裝置上，此功能需要應用程式 (亦即，WXP、Outlook、Managed Browser、Yammer) 的參與來就地整合 Intune App SDK，以在目標應用程式中強制執行此功能。 此整合會以輪流的方式發生，並取決於特定的應用程式小組。 在 Android 上，此功能需要有最新版的公司入口網站。 

在使用者裝置上，Intune 用戶端將會根據應用程式防護原則 Intune 刀鋒視窗中所指定字串來進行簡單比對，藉以採取動作。 這會完全取決於裝置報告的值。 因此，我們會建議 IT 系統管理員確定預期的行為是正確無誤的。 這可透過針對小型的使用者群組，在各種不同的裝置製造商和型號上測試此設定來達成。 在 Microsoft Intune 中，選取 [行動應用程式] > [應用程式防護原則] 來檢視及新增應用程式防護原則。 如需有關應用程式保護原則的詳細資訊，請參閱[什麼是應用程式保護原則](app-protection-policy.md)與[在 Intune 中使用應用程式防護原則的存取動作選擇性地抹除資料](app-protection-policies-access-actions.md)。

### <a name="access-to-macos-company-portal-pre-release-build----1734766---"></a>存取 macOS 公司入口網站發行前版本組建 <!-- 1734766 -->
使用 Microsoft AutoUpdate 註冊，您可以透過加入測試人員計畫提早收到組建。 註冊可讓您在使用者可使用已更新的公司入口網站之前先行使用。 如需詳細資訊，請參閱 [Microsoft Intune 部落格](https://blogs.technet.microsoft.com/intunesupport/2018/07/13/use-microsoft-autoupdate-for-early-access-to-the-macos-company-portal-app/)。

## <a name="week-of-july-2-2018"></a>2018 年 7 月 2 日當週

### <a name="app-management"></a>應用程式管理

#### <a name="monitor-ios--app-configuration-status-per-device----880037---"></a>監視每個裝置的 iOS 應用程式設定狀態 <!-- 880037 -->
身為 Microsoft Intune 系統管理員，您可以監視每個受控裝置的 iOS 應用程式設定狀態。 從 Azure 入口網站的 [Microsoft Intune] 中，選取 [裝置] > [所有裝置]。 從受控裝置清單中，選取特定的裝置以顯示裝置的刀鋒視窗。 在裝置的刀鋒視窗中，選取 [應用程式設定]。

#### <a name="access-actions-for-app-protection-policies----1483510---"></a>存取適用於應用程式防護原則的動作 <!-- 1483510 -->
您可以設定應用程式防護原則，以明確地針對不符合規範的裝置進行抹除、封鎖或警告。 「抹除」動作能從裝置移除您公司的資料。 如果發生抹除，系統會向裝置使用者告知抹除的原因及補救的步驟。 針對某些設定 (例如最小 OS 版本)，您將能套用多個動作 (例如封鎖和抹除)。 請注意，當應用程式啟動時，便會觸發這些動作。

#### <a name="selective-wipe-of-organizations-app-data----1507030---"></a>選擇性抹除組織的應用程式資料 <!-- 1507030 -->
不符合應用程式保護原則 (APP) 存取設定的條件時，系統管理員現在可以設定選擇性抹除組識資料作為新的動作。  這項功能可協助系統管理員依據預先設定的準則，自動保護並移除應用程式中的機密組織資料。

#### <a name="revoking-an-ios-app-purchased-through-vpp----1777384---"></a>撤銷透過 VPP 購買的 iOS 應用程式 <!-- 1777384 -->
身為 Microsoft Intune 系統管理員，您可以撤銷所有透過大量採購方案 (VPP) 購買的所選 iOS 應用程式授權。 當使用者授權的應用程式不再指派給使用者時，您可以通知他們。 撤銷應用程式授權將不會從該裝置解除安裝相關聯的 VPP 應用程式。 若要解除安裝 VPP 應用程式，您必須將指派動作變更為 [解除安裝]。 回收的授權計數將會反映在 Intune 之 [應用程式] 工作負載中的 [授權的應用程式] 節點。 如需與 iOS VPP 應用程式相關的詳細資訊，請參閱[如何使用 Microsoft Intune 管理透過大量採購方案購買的 iOS 應用程式](vpp-apps-ios.md)。

#### <a name="updates-to-out-of-compliance-messages-in-company-portal-app----1832222---"></a>公司入口網站應用程式中不相容訊息的更新 <!-- 1832222 -->
我們已修訂裝置使用者在裝置不相容時看到的訊息。 訊息保留其原始意義，但已透過更友善的語言和技術性較低的術語更新。 我們也已重新整理文件和補救步驟的連結，將其保持為最新。
下列前後文字是您將看到之傳訊中的一個改善範例：
- **之前**：此裝置未在 IT 管理員所要求的指定時段中連線 Intune 服務。若要解決此問題，請在您的裝置上開啟公司入口網站應用程式，然後按一下 [檢查相容性] 按鈕。
- **之後**：您的裝置已一段時間未簽入組織。若要重新建立連線，請在裝置上開啟公司入口網站應用程式，然後針對您的裝置點選 [檢查設定]。

#### <a name="revoke-ios-vpp-app-license----1863797---"></a>撤銷 iOS VPP 應用程式授權 <!-- 1863797 -->
身為系統管理員，您可以回收指派給使用者或裝置的 iOS VPP 應用程式授權。 解除安裝 iOS VPP 應用程式也可讓您回收應用程式授權。 在解除安裝應用程式之前，需要先從目標應用程式群組中刪除使用者或裝置。 從群組移除使用者或裝置，可避免重新安裝應用程式。 完成這些步驟後，您可以選擇將應用程式授權指派給其他使用者或裝置。 如需 iOS VPP 應用程式授權的詳細資訊，請參閱[在 Microsoft Intune 中管理 iOS 大量採購的應用程式](vpp-apps-ios.md)。

### <a name="device-configuration"></a>裝置設定

#### <a name="select-device-categories-by-using-the-access-work-or-school-settings----1058963-eenotready---"></a>使用 [存取公司或學校資源] 設定來選取裝置類別 <!-- 1058963 eenotready --> 
如果您已啟用[裝置群組對應](https://docs.microsoft.com/en-us/intune/device-group-mapping)，現在將在 Windows 10 上的使用者透過 [設定] > [帳戶] > [存取公司或學校資源] 中的 [連線] 按鈕註冊之後，提示他們選取裝置類別。 

#### <a name="use-samaccountname-as-the-account-username-for-email-profiles----1500307---"></a>使用 sAMAccountName 作為電子郵件設定檔的帳戶使用者名稱 <!-- 1500307 -->
您可以使用內部部署 **sAMAccountName**，作為 Android、iOS 和 Windows 10 電子郵件設定檔的帳戶使用者名稱。 也可以從Azure Active Directory (Azure AD) 中的 `domain` 或 `ntdomain` 屬性取得網域。 或者，輸入自訂靜態網域。

若要使用這項功能，您必須將來自內部部署 Active Directory 環境的 `sAMAccountName` 屬性同步至 Azure AD。

適用於 [Android](email-settings-android.md)、[iOS](email-settings-ios.md)、[Windows 10 和更新版本](email-settings-windows-10.md)

#### <a name="see-device-configuration-profiles-in-conflict----1556983---"></a>查看衝突的裝置組態設定檔 <!-- 1556983 -->
在 [裝置設定] 中，會顯示現有設定檔的清單。 使用此更新即會新增資料行，以提供衝突之設定檔的詳細資料。 您可以選取衝突的資料列，以查看設定以及發生衝突的設定檔。 

移至[管理組態設定檔](device-profile-monitor.md#view-conflicts)以取得更多資訊。

#### <a name="new-status-for-devices-in-device-compliance----2308882---"></a>裝置相容性中裝置的新狀態 <!-- 2308882 -->
在 [裝置相容性] > [原則] > 選取原則 > [概觀] 中，已新增下列新狀態：
- 成功
- 錯誤
- 衝突
- 擱置
- 不適用。同時顯示了顯示不同平台裝置計數的影像。 例如，如果您要查看 iOS 設定檔，新的磚會顯示同時指派給此設定檔的非 iOS 裝置計數。 請參閱[裝置合規性原則](compliance-policy-monitor.md#view-status-of-device-policies)。

#### <a name="device-compliance-supports-3rd-party-anti-virus-solutions----2325484---"></a>裝置合規性支援協力廠商防毒解決方案 <!-- 2325484 -->
當您建立裝置合規性原則 ([裝置合規性] > [原則] > [建立原則] >  [平台：Windows 10 和更新版本] > [設定] > [系統安全性]) 時，有一些新的 [裝置安全性](compliance-policy-create-windows.md#windows-10-and-later-policy-settings)選項： 
- **防毒**：當設定為 [必要] 時，您可以使用向 Windows 資訊安全中心註冊的防毒解決方案 (例如 Symantec 和 Windows Defender) 來檢查合規性。 
- **反間諜功能**：當設定為 [必要] 時，您可以使用向 Windows 資訊安全中心註冊的防毒解決方案 (例如 Symantec 和 Windows Defender) 來檢查合規性。 

適用對象：Windows 10 和更新版本 

### <a name="device-enrollment"></a>裝置註冊

####  <a name="devices-without-profiles-column-in-the-list-of-enrollment-program-tokens----1853904---"></a>註冊計劃權杖清單中沒有設定檔資料行的裝置 <!-- 1853904 -->
在註冊程式權杖清單中，有一個新資料行會顯示未指派設定檔的裝置數目。 這有助於系統管理員在將設定檔交給使用者之前將其指派給這些裝置。 若要查看新資料行，請前往 [裝置註冊] > [Apple 註冊] > [註冊計劃權杖]。

### <a name="device-management"></a>裝置管理

#### <a name="google-name-changes-for-android-for-work-and-play-for-work---842873---"></a>Android for Work 和 Play for Work 的 Google 名稱變更 <!--842873 -->
Intune 已更新 "Android for Work" 術語以反映 Google 的商標變更。 "Android for Work" 和 "Play for Work" 這些詞彙已不再使用。 視內容而定，會使用不同的術語：
- 「Android 企業」指的是整體的現代 Android 管理堆疊。
- 「工作設定檔」或「設定檔擁有者」指的是使用工作設定檔管理的 BYOD 裝置。
- 「受控 Google Play」則是指 Google 應用程式存放區。

#### <a name="rules-for-removing-devices----1609459---"></a>用於移除裝置的規則 <!-- 1609459 -->
新規則已可用，可讓您自動移除在所設定天數內未簽入的裝置。 若要查看新規則，請移至 [Intune] 窗格，然後依序選取 [裝置] 和 [裝置清除規則]。

#### <a name="corporate-owned-single-use-support-for-android-devices----1630973---"></a>公司所擁有且適用於 Android 裝置的單次使用支援 <!-- 1630973 -->

Intune 現在支援高度受控、鎖定、Kiosk 樣式的 Android 裝置。 這可讓系統管理員將裝置的用途進一步鎖定為單一應用程式或一小組的應用程式，並可防止使用者在裝置上啟用其他應用程式或執行其他動作。 若要設定 Android Kiosk，請移至 [Intune] > [裝置註冊] > [Android 註冊] > [Kiosk 及工作裝置註冊]。 如需詳細資訊，請參閱[設定 Android 企業 Kiosk 裝置註冊](android-kiosk-enroll.md)。

#### <a name="per-row-review-of-duplicate-corporate-device-identifiers-uploaded----2203794--"></a>已上傳之重複公司裝置識別碼的每一資料列檢閱 <!-- 2203794-->
上傳公司識別碼時，Intune 現在會提供任何重複項目的清單，並可讓您選擇取代或保留現有資訊。 選擇 [裝置註冊] > [公司裝置識別碼] > [新增識別碼] 之後，如果有重複項目，則會出現報表。 

#### <a name="manually-add-corporate-device-identifiers----2203803---"></a>手動新增公司裝置識別碼 <!-- 2203803 -->
您現在可以手動新增公司裝置識別碼。 請選擇 [裝置註冊] > [公司裝置識別碼] > [新增]。 

## <a name="week-of-june-25-2018"></a>2018年 6 月 25 日當週

### <a name="pradeo---new-mobile-threat-defense-partner----1169249---"></a>Pradeo - 新的 Mobile Threat Defense 夥伴 <!-- 1169249 -->

您可以根據由 Pradeo (一個與 Microsoft Intune 整合的 Mobile Threat Defense 解決方案) 所進行的風險評定，使用條件式存取來控制行動裝置對公司資源的存取。

## <a name="week-of-june-18-2018"></a>2018年 6 月 18 日當週

### <a name="edge-mobile-support-for-intune-app-protection-policies----1817882---"></a>Intune 應用程式防護原則的 Edge 行動支援 <!-- 1817882 -->

行動裝置的 Microsoft Edge 瀏覽器現在支援 Intune 中所定義的應用程式防護原則。

## <a name="week-of-june-11-2018"></a>2018年 6 月 11 日當週

### <a name="use-fips-mode-with-the-ndes-certificate-connector----1333688---"></a>使用 FIPS 模式和 NDES 憑證連接器 <!-- 1333688 -->
當您在啟用聯邦資訊處理標準 (FIPS) 模式的電腦上安裝 NDES 憑證連接器時，發行和撤銷憑證無法如預期運作。 在此更新中，NDES 憑證連接器隨附 FIPS 支援。 

此更新還包括：

- NDES 憑證連接器需要 .NET 4.5 Framework，這會自動隨附於 Windows Server 2016 和 Windows Server 2012 R2。 之前，.NET 3.5 Framework 是最低必要版本。
- NDES 憑證連接器隨附 TLS 1.2 支援。 因此，如果安裝 NDES 憑證連接器的伺服器支援 TLS 1.2，則會使用 TLS 1.2。 如果伺服器不支援 TLS 1.2，則會使用 TLS 1.1。 目前，使用 TLS 1.1 在裝置與伺服器之間進行驗證。

如需詳細資訊，請參閱[設定並使用 SCEP 憑證](certificates-scep-configure.md)和[設定並使用 PKCS 憑證](certficates-pfx-configure.md)。

## <a name="week-of-june-4-2018"></a>2018年 6 月 4日當週

### <a name="app-management"></a>應用程式管理

#### <a name="retrieve-the-associated-app-user-model-id-aumid-for-microsoft-store-for-business-apps-in-kiosk-mode----1560077----"></a>在 Kiosk 模式中擷取商務用 Microsoft Store 應用程式的相關聯應用程式使用者模型識別碼 (AUMID) <!-- 1560077 ! -->
Intune 目前可以擷取商務用 Microsoft Store (WSfB) 應用程式的應用程式使用者模型識別碼 (AUMID)，以提供改善的 Kiosk 設定檔設定。

如需商務用 Microsoft Store 應用程式的詳細資訊，請參閱[管理來自商務用 Microsoft Store 的應用程式](windows-store-for-business.md)。

#### <a name="new-company-portal-branding-page----1916370---"></a>新的公司入口網站商標頁面 <!-- 1916370 -->
公司入口網站商標頁面有新的版面配置、訊息和工具提示。


### <a name="device-configuration"></a>裝置設定

#### <a name="support-for-palo-alto-networks-globalprotect-vpn-profiles----1333680-eeready----"></a>Palo Alto Networks GLOBalProtect VPN 設定檔的支援 <!-- 1333680 eeready ! -->
透過這項更新，您可以選擇 Palo Alto Networks GLOBalProtect 作為在 Intune 中 VPN 設定檔的 VPN 連線類型 ([裝置設定] > [設定檔] > [建立設定檔] > [設定檔類型] > [VPN])。 在此版本中，支援下列平台： 

- iOS
- Windows 10

#### <a name="additions-to-local-device-security-options-settings----1403702---"></a>新增本機裝置安全性選項設定 <!-- 1403702 -->
您現在能夠為 Windows 10 裝置設定額外的 [本機裝置安全性選項] 設定。 可使用額外設定的區域包括 Microsoft Network Client、Microsoft Network Server、[網路存取和安全性] 及 [互動式登入]。 當您建立 Windows 10 裝置設定原則時，在 [Endpoint Protection] 類別中找到這些設定。

#### <a name="enable-kiosk-mode-on-windows-10-devices----1560072----"></a>在 Windows 10 裝置上啟用 Kiosk 模式 <!-- 1560072 ! -->
在 Windows 10 裝置上，您可以建立組態設定檔並啟用 Kiosk 模式 ([裝置設定] > [設定檔] > [建立設定檔] > [Windows 10] > [裝置限制] > [Kiosk])。 在此更新中，[Kiosk (預覽)] 設定已重新命名為 [Kiosk (已淘汰)]。 我們不建議繼續使用 [Kiosk (已淘汰)]，但該功能在 7 月更新之前將會持續運作。 [Kiosk (已淘汰)] 已由新的 [Kiosk] 設定檔類型 ([建立設定檔] > [Windows 10] > [Kiosk (預覽)]) 取代，此設定檔類型將會包含在 Windows 10 RS4 及更新版本上設定 Kiosk 的設定。

適用於 Windows 10 及更新版本。

#### <a name="device-profile-graphical-user-chart-is-back----2160133---"></a>已重新推出裝置設定檔圖形化使用者圖表 <!-- 2160133 -->
在改善裝置設定檔圖形化圖表 ([裝置設定] > [設定檔] > 選取現有的設定檔 > [概觀]) 上所顯示的數值計數之際，暫時移除了圖形化使用者圖表。

此更新已重新推出圖形化使用者圖表，如 Azure 入口網站中所示。

### <a name="device-enrollment"></a>裝置註冊

#### <a name="support-for-windows-autopilot-enrollment-without-user-authentication----1165118-wnready---"></a>支援 Windows Autopilot 註冊而不需要使用者驗證 <!-- 1165118 wnready -->
Intune 現在支援 Windows Autopilot 註冊，而不需要使用者驗證。 這是 Windows Autopilot 部署設定檔中 [Autopilot 部署模式] 設為 [自我部署] 的新選項。  裝置必須執行 Windows 10 Insider Preview 組建 17672 或更新版本，並擁有 TPM 2.0 晶片才能成功完成此類型的註冊。 由於不需要任何使用者驗證，您只應將此選項指派給您擁有實體控制權的裝置。

#### <a name="new-languageregion-setting-when-configuring-oobe-for-autopilot----1821766-eeready---"></a>針對 Autopilot 設定 OOBE 時的新語言/地區設定 <!-- 1821766 eeready -->
在全新體驗期間，將會有新的組態設定可供設定 Autopilot 設定檔的語言和地區。 若要查看新設定，請選擇 [裝置註冊] > [Windows 註冊] > [部署設定檔] > [建立設定檔] > [部署模式] = [自我部署] > [設定的預設值]。

#### <a name="new-setting-for-configuring-device-keyboard----1821768---"></a>適用於設定裝置鍵盤的新設定 <!-- 1821768 -->
在全新體驗期間，將會有新設定可供設定 Autopilot 設定檔的鍵盤。 若要查看新設定，請選擇 [裝置註冊] > [Windows 註冊] > [部署設定檔] > [建立設定檔] > [部署模式] = [自我部署] > [設定的預設值]。

#### <a name="autopilot-profiles-moving-to-group-targeting----1877935---"></a>將 AutoPilot 設定檔移至群組目標設定 <!-- 1877935 -->
AutoPilot 部署設定檔可以指派給包含 AutoPilot 裝置的 Azure AD 群組。

### <a name="device-management"></a>裝置管理

#### <a name="set-compliance-by-device-location----851881----"></a>依裝置位置設定合規性 <!-- 851881 ! -->
在某些情況下，您可能會想要依網路連線將公司資源的存取限制於特定的位置。 您現在可以依據裝置的 IP 位址建立合規性原則 ([裝置合規性] > [位置])。 如果裝置移出該 IP 範圍，則該裝置將會無法存取公司資源。

適用對象：公司入口網站應用程式已更新的 6.0 和更新版本的 Android 裝置

#### <a name="prevent-consumer-apps-and-experiences-on-windows-10-enterprise-rs4-autopilot-devices---1621980---"></a>防止 Windows 10 企業版 RS4 AutoPilot 裝置上的消費者應用程式和體驗<!-- 1621980 -->
您將能夠防止在「Windows 10 企業版 RS4 AutoPilot」裝置上安裝消費者應用程式和體驗。 若要查看此功能，請移至 [Intune] > [裝置設定] > [設定檔] > [建立設定檔] > [平台] = [Windows 10 或更新版本] > [設定檔類型] = [裝置限制] > [設定] > [Windows 焦點] > [消費者功能]。 

#### <a name="uninstall-the-latest-from-windows-10-software-updates----1732948-eeready---"></a>解除安裝 Windows 10 軟體更新的最新版本 <!-- 1732948 eeready -->
如果您發現 Windows 10 電腦上發生重大問題，可以選擇解除安裝 (復原) 最新的功能更新或最新的品質更新。 解除安裝功能或品質更新只適用於裝置所在的維護通道。 解除安裝將會觸發原則，以在 Windows 10 電腦上還原先前的更新。 特別是對於功能更新，您可以將能夠套用解除安裝最新版本的時間限制為 2-60 天。 若要設定軟體更新解除安裝選項，請從 Azure 入口網站內的 [Microsoft Intune] 刀鋒視窗中選取 [軟體更新]。 然後，從 [軟體更新] 刀鋒視窗中，選取 [Windows 10 更新通道]。 接著可以選擇 [概觀] 區段中的 [解除安裝] 選項。

#### <a name="search-all-devices-for-imei-and-serial-number----1793685---"></a>搜尋所有裝置的 IMEI 和序號 <!-- 1793685 -->
您目前能在所有裝置的刀鋒視窗上搜尋 IMEI 和序號 (電子郵件、UPN、裝置名稱和管理名稱仍然可用)。 在 Intune 中，選擇 [裝置] > [所有裝置] > 在搜尋方塊中輸入您的搜尋。

#### <a name="management-name-field-will-be-editable----1875989---"></a>管理名稱欄位將可以編輯 <!-- 1875989 -->
您目前可在裝置的 [屬性] 刀鋒視窗上編輯管理名稱欄位。 如果要編輯此欄位，請選擇 [裝置] > [所有裝置] > 選擇裝置 > [屬性]。 您可以使用管理名稱欄位來唯一識別裝置。

#### <a name="new-all-devices-filter-device-category----1878520---"></a>新的所有裝置篩選器：裝置類別 <!-- 1878520 -->
您現在可以依裝置類別篩選 [所有裝置] 清單。 若要這樣做，請選擇 [裝置] > [所有裝置] > [篩選] > [裝置類別]。

#### <a name="use-teamviewer-to-screen-share-ios-and-macos-devices----1985547---"></a>使用 TeamViewer 來共用 iOS 和 MacOS 裝置的螢幕畫面 <!-- 1985547 -->
系統管理員現在可以連線至 [TeamViewer](device-profile-android-teamviewer.md)，並與 iOS 和 macOS 裝置建立螢幕畫面共用工作階段。 iPhone、iPad 及 macOS 使用者都可以與任何其他電腦或行動裝置即時共用其螢幕畫面。 

#### <a name="multiple-exchange-connector-support----2070451---"></a>多重 Exchange 連接器支援 <!-- 2070451 -->
您不會再受到每個租用戶只能有一個 Microsoft Intune Exchange Connector 的限制了。 Intune 現在支援多個 Exchange 連接器，使您可以用多個內部部署 Exchange 組織來設定 Intune 條件式存取。

透過 Intune 內部部署 Exchange 連接器，您可以根據裝置是否已在 Intune 註冊且符合 Intune 裝置合規性政策，來管理裝置對於您內部部署 Exchange 信箱的存取。 若要設定連接器，請從 Azure 入口網站下載 Intune 內部部署 Exchange 連接器，並安裝在您 Exchange 組織中的伺服器。 在 Microsoft Intune 儀表板中，選擇 [內部部署存取]，然後在 [安裝] 下選擇 [Exchange ActiveSync 連接器]。 下載 Exchange 內部部署連接器，並將其安裝在您 Exchange 組織中的伺服器。 您現在已經沒有一個租用戶只能有一個 Exchange 連接器的限制，因此您如果有其他 Exchange 組織，亦可遵循此相同流程為每個 Exchange 組織下載並安裝連接器。

#### <a name="new-device-hardware-detail-ccid----2156657---"></a>新的裝置硬體詳細資料： CCID <!-- 2156657 -->
每個裝置現在都包含晶片卡介面裝置 (CCID) 資訊。 若要查看它，請選擇 [裝置] > [所有裝置] > 選擇裝置 > [硬體] > 檢查 [網路詳細資料] 下的內容 >

#### <a name="assign-all-users-and-all-devices-as-scope-groups----2196803---"></a>將所有使用者和所有裝置指派為範圍群組 <!-- 2196803 -->
您現在能以範圍群組的形式指派所有使用者、所有裝置，以及所有使用者和所有裝置。 若要這樣做，請選擇 [Intune 角色] > [所有角色] > [原則和設定檔管理員] > [指派] > 選擇指派 > [範圍 (群組)]。

#### <a name="udid-information-now-included-for-ios-and-macos-devices----2219806-wnready--"></a>iOS 和 macOS 裝置現在包含 UDID 資訊 <!-- 2219806 wnready-->
若要查看 iOS 和 macOS 裝置的唯一裝置識別碼 (UDID)，請移至 [裝置] > [所有裝置] > 選擇裝置 > [硬體]。 UDID 只適用於公司裝置 (如 [裝置] > [所有裝置] > 選擇裝置 > [屬性] > [裝置擁有權] 下的設定)。

### <a name="intune-apps"></a>Intune 應用程式

#### <a name="improved-troubleshooting-for-app-installation----928990---"></a>改善的應用程式安裝疑難排解 <!-- 928990 -->
在受 Microsoft Intune MDM 管理的裝置上，應用程式安裝有時可能會失敗。 當這些應用程式安裝失敗時，使用者可能無法輕易地了解失敗的原因，或是對問題進行疑難排解。 我們正在推出應用程式疑難排解功能的公開預覽。 您將會在每個個別裝置的底下看到名為 [受控應用程式] 的新節點。 這會列出透過 Intune MDM 傳遞的應用程式。 在該節點中，您將會看到應用程式安裝狀態的清單。 如果您選取個別的應用程式，將會看到針對該特定應用程式的疑難排解檢視。 在疑難排解檢視中，您將會看到應用程式的端對端生命週期，例如針對該應用程式進行建立、修改、設為目標，以及傳遞至裝置的時間。 此外，如果應用程式安裝沒有成功，系統將會針對導致該錯誤的原因為您顯示錯誤碼及協助訊息。 

#### <a name="intune-app-protection-policies-and-microsoft-edge----1818968---"></a>Inunte 應用程式保護原則和 Microsoft Edge <!-- 1818968 -->
適用於行動裝置 (iOS 和 Android) 的 Microsoft Edge 瀏覽器現在支援 Microsoft Intune 應用程式保護原則。 使用其公司 Azure AD 帳戶登入 Edge 應用程式的 iOS 和 Android 裝置使用者，將會受到 Intune 的保護。 在 iOS 裝置上，[要求受控瀏覽器的 Web 內容] 原則可讓使用者開啟受控 Edge 中的連結。

## <a name="week-of-may-14-2018"></a>2018 年 5 月 14 日當週

### <a name="app-management"></a>應用程式管理

#### <a name="require-installation-of-policies-apps-certificate-and-network-profiles----1553555---"></a>要求安裝原則、應用程式、憑證及網路設定檔 <!-- 1553555 -->

在佈建 AutoPilot 裝置期間，系統管理員能夠禁止使用者存取 Windows 10 RS4 桌面，直到 Intune 安裝原則、應用程式及憑證和網路設定檔為止。 如需詳細資訊，請參閱[設定註冊狀態頁面](windows-enrollment-status.md)。

#### <a name="configuring-your-app-protection-policies----2144597-part-2---"></a>設定應用程式保護原則 <!-- 2144597 Part 2 -->

在 Azure 入口網站，不用移至 Intune 應用程式保護服務刀鋒視窗，您現在只需移至 Intune。 目前在 Intune 中只有一個應用程式保護原則的位置。 請注意，所有應用程式保護原則都在 Intune [應用程式保護原則] 底下的 [行動應用程式] 刀鋒視窗上。 這項整合有助於簡化雲端管理系統管理。 請記住，所有應用程式保護原則都已經在 Intune 中，而您可以修改任何先前已設定的原則。 Intune 應用程式原則保護 (APP) 和條件式存取 (CA) 原則現在會在 [條件式存取] 下，這可以在 [Microsoft Intune] 刀鋒視窗的 [管理] 區段找到，或在 [Azure Active Directory] 刀鋒視窗的 [安全性] 區段找到。 如需有關修改條件式存取原則詳細資訊，請參閱 [Azure Active Directory 中的條件式存取](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)。 如需其他資訊，請參閱[什麼是應用程式保護原則？](app-protection-policy.md)

## <a name="week-of-may-7-2018"></a>2018 年 5 月 7 日當週

### <a name="app-management"></a>應用程式管理

#### <a name="samsung-knox-mobile-enrollment-support---1112863--"></a>Samsung Knox Mobile Enrollment 支援 <!--1112863-->

當 Intune 與 Samsung Knox Mobile Enrollment (KME) 搭配使用時，您可以註冊大量公司擁有的 Android 裝置。 使用 WiFi 或行動電話通訊網路的使用者第一次開啟其裝置時，只需輕點幾下即可註冊。 使用 Knox 部署應用程式時，可以使用藍牙或 NFC 註冊裝置。 如需詳細資訊，請參閱[使用 Samsung Knox Mobile Enrollment 自動註冊 Android 裝置](android-samsung-knox-mobile-enroll.md)。

#### <a name="requesting-help-in-the-company-portal-for-windows-10----1874137---"></a>要求 Windows 10 版公司入口網站中的說明 <!-- 1874137 -->

當使用者啟動工作流程以取得有關問題的說明時，Windows 10 版公司入口網站現在會將應用程式記錄檔直接傳送給 Microsoft。 這樣可以更輕鬆地進行疑難排解並解決向 Microsoft 提出的問題。

## <a name="week-of-april-23-2018"></a>2018 年 4 月 23 日當週

### <a name="app-management"></a>應用程式管理

#### <a name="passcode-support-for-mam-pin-on-android---1438086---"></a>在 Android 上針對 MAM PIN 提供密碼支援<!-- 1438086 -->

Intune 系統管理員可以將應用程式的啟動要求設定為使用密碼，而不是使用數字型的 MAM PIN 碼。 如上進行設定後，使用者就必須在出現提示時設定並使用密碼，才能存取啟用 MAM 的應用程式。 密碼的定義為數字 PIN 和至少一個特殊字元或大寫/小寫字母。 Intune 支援密碼的方式與數字 PIN 類似，能夠透過管理主控台設定長度下限、允許重複的字元及順序。 若要使用此功能，Android 上必須要有最新版的公司入口網站。 此功能已經可供 iOS 使用。

#### <a name="line-of-business-lob-app-support-for-macos----1473977---"></a>macOS 的企業營運 (LOB) 應用程式支援 <!-- 1473977 -->
Microsoft Intune 將可讓您從 Azure 入口網站安裝 macOS LOB 應用程式。 您將能夠在以 GitHub 中提供的工具對 macOS LOB 應用程式進行前處理之後，將其新增至 Intune。 在 Azure 入口網站中，從 [Intune] 刀鋒視窗上選擇 [行動應用程式]。 在 [行動應用程式] 刀鋒視窗上，選擇 [應用程式] > [新增]。 在 [新增應用程式] 刀鋒視窗上，選取 [企業營運應用程式]。 

#### <a name="built-in-all-users-and-all-devices-group-for-android-for-work-afw-app-assignment----1813073---"></a>適用於 Android for Work (AFW) 應用程式指派的內建所有使用者和所有裝置群組 <!-- 1813073 -->
您可以使用內建的 [所有使用者] 與 [所有裝置] 群組指派 AFW 應用程式。 如需詳細資訊，請參閱 [Microsoft Intune 的包含與排除應用程式指派](apps-inc-exl-assignments.md)。

#### <a name="intune-will-reinstall-required-apps-that-are-uninstalled-by-users----1947010---"></a>Intune 會重新安裝被使用者解除安裝的必要應用程式 <!-- 1947010 -->
如果終端使用者解除安裝必要的應用程式，Intune 會在 24 小時內自動重新安裝應用程式，而不會等待 7 天的重新評估週期。

### <a name="device-configuration"></a>裝置設定

####  <a name="device-profile-chart-and-status-list-show-all-devices-in-a-group----1449153-eeready---"></a>裝置設定檔圖表和狀態清單顯示群組中的所有裝置 <!-- 1449153 eeready -->
當您設定裝置設定檔 ([裝置設定] > [設定檔]) 時，可以選擇裝置設定檔，例如 iOS。 您會將這個設定檔指派給包含 iOS 裝置和非 iOS 裝置的群組。 圖形化圖表計數會顯示設定檔已套用至 iOS「和」非 iOS 裝置 ([裝置設定] > [設定檔] > 選取現有的設定檔 > [概觀])。 當您在 [概觀] 索引標籤中選取圖形化圖表時，[裝置狀態] 會列出群組中的所有裝置，而不是只列出 iOS 裝置。 

在此更新中，圖形化圖表 ([裝置設定]  >  [設定檔] > 選取現有的設定檔 > [概觀]) 只會顯示特定裝置設定檔的計數。 例如，如果設定裝置設定檔適用於 iOS 裝置，圖表只會列出 iOS 裝置的計數。 選取圖形化圖表和開啟 [裝置狀態] 只會列出 iOS 裝置。

進行此更新時，會暫時移除圖形化使用者圖表。 

#### <a name="always-on-vpn-for-windows-10---1333666---"></a>適用於 Windows 10 的一律開啟 VPN<!--1333666 -->

目前，可藉由使用以 OMA-URI 建立的自訂虛擬私人網路 (VPN) 設定檔，在 Windows 10 裝置上使用[一律開啟](https://docs.microsoft.com/windows/security/identity-protection/vpn/vpn-auto-trigger-profile#always-on)。

在此更新中，系統管理員將能夠直接在 Azure 入口網站的 Intune 中，為 Windows 10 VPN 設定檔啟用 Always On。 「一律開啟」VPN 設定檔會在下列情況下自動連線：

- 使用者登入其裝置
- 裝置上的網路發生變更
- 裝置上的螢幕在關閉後恢復開啟

#### <a name="new-printer-settings-for-education-profiles----1308900---"></a>教育版設定檔的新印表機設定 <!-- 1308900 -->

教育版設定檔的新設定位於 [印表機] 類別下：[印表機]、[預設印表機]、[Add new printers] (新增印表機)。

#### <a name="show-caller-id-in-personal-profile---android-for-work---1098984---"></a>在個人的設定檔中顯示呼叫者識別碼 - Android for Work <!--1098984 -->
在裝置上使用個人設定檔時，終端使用者可能無法從工作連絡人看到呼叫者識別碼詳細資料。 

在此更新中，[Android for Work] > [裝置限制] > [工作設定檔設定] 會有一個新的設定：
- 在個人設定檔中顯示工作連絡人呼叫者識別碼

啟用 (未設定) 時，工作連絡呼叫者詳細資料會顯示在個人設定檔中。 封鎖時，工作連絡呼叫者詳細資料不會顯示在個人設定檔中。 

適用於：Android OS 6.0 版和更新版本上的 Android 工作設定檔裝置

#### <a name="new-windows-defender-credential-guard-settings-added-to-endpoint-protection-settings---1102252-----from-1802-and-1804--"></a>在 Endpoint Protection 設定中新增新的 Windows Defender Credential Guard 設定 <!--1102252 --><!--from 1802 and 1804-->

在此更新中，[Windows Defender Credential Guard](https://docs.microsoft.com/windows/access-protection/credential-guard/credential-guard) ([裝置設定]  >  [設定檔]  >  [端點保護]) 包含下列設定： 

- **Windows Defender Credential Guard**：開啟搭載虛擬化安全性的 Credential Guard。 若同時啟用了**安全開機的平台安全性層級**與**虛擬化安全性**，啟用此功能將有助於在下次重新開機時保護認證。 這些選項包括：
  - **已停用**：若先前開啟 Credential Guard 時也啟用了 [在不含鎖定情況下啟用] 選項，將會從遠端關閉 Credential Guard。

  - **Enabled with UEFI lock** (啟用並鎖定 UEFI)：確保無法使用登錄機碼或群組原則停用 Credential Guard。 若要在使用此設定後停用 Credential Guard，必須將群組原則設為 [已停用]。 接著移除每位真實存在之使用者每部電腦的安全性功能。 下列步驟會清除 UEFI 中保存的設定。 只要 UEFI 設定持續存在，就會啟用 Credential Guard。

  - **在不含鎖定情況下啟用**：允許使用群組原則從遠端停用 Credential Guard。 使用此設定的裝置至少必須執行 Windows 10 (1511 版)。

設定 Credential Guard 時會自動啟用下列相關技術： 

  - **啟用虛擬化安全性 (VBS)**：於下次重新開機時開啟虛擬化安全性 (VBS)。 虛擬化安全性使用 Windows Hypervisor 支援安全性服務，需要安全開機功能。
  - **安全開機與直接記憶體存取 (DMA)**：開啟安全開機的 VBS 及直接記憶體存取。 DMA 保護需要硬體支援，而且只可在設定正確的裝置上啟用。 

#### <a name="use-a-custom-subject-name-on-scep-certificate----2064190---"></a>在 SCEP 憑證上使用自訂主體名稱 <!-- 2064190 -->
您可以使用在 SCEP 憑證設定檔中，使用自訂主體常見的名稱 **OnPremisesSamAccountName**。 例如，您可以使用 `CN={OnPremisesSamAccountName})`。

####  <a name="block-camera-and-screen-captures-on-android-for-work----1098977-eeready--"></a>在 Android for Work 上封鎖相機和螢幕擷取 <!-- 1098977 eeready-->
當您為 Android 裝置設定裝置限制時，有兩個新屬性可用於封鎖： 
- 相機：封鎖對裝置上所有相機的存取
- 螢幕擷取：封鎖螢幕擷取，同時也防止在沒有安全視訊輸出的顯示裝置上顯示內容

適用於 Android for Work。


### <a name="device-enrollment"></a>裝置註冊

#### <a name="new-enrollment-steps-for-users-on-devices-with-macos-high-sierra-10132---1734567---"></a>適用於具有 macOS High Sierra 10.13.2+ 之裝置上使用者的新註冊步驟 <!--1734567 -->
macOS High Sierra 10.13.2 引進了「使用者核准的」MDM 註冊概念。 核准的註冊讓 Intune 可以管理一些高度安全性的設定。 如需詳細資訊，請參閱以下的 Apple 支援文件：https://support.apple.com/HT208019。

除非使用者開啟 [系統偏好設定] 手動提供核准，否則使用 macOS 公司入口網站註冊的裝置會被視為「未經使用者核准」。 為此，macOS 公司入口網站現在會在註冊程序結尾，將 macOS 10.13.2 和更新版本的使用者導向以供他們手動核准其註冊。 Intune 管理主控台將會針對已註冊裝置是否獲得使用者核准進行回報。



### <a name="device-management"></a>裝置管理

#### <a name="advanced-threat-protection-atp-and-intune-are-fully-integrated----eeready-1629303---"></a>進階威脅防護 (ATP) 和 Intune 已完全整合<!-- EEready 1629303 -->

[進階威脅防護 (ATP)](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/dashboard-windows-defender-advanced-threat-protection) 會顯示 Windows 10 裝置的風險層級。 在 Windows Defender 資訊安全中心 (ATP 入口網站)，您可以建立與 Microsoft Intune 的連線。 一旦建立之後，Intune 合規性原則會用來判斷可接受的威脅層級。 如果超過威脅層級時，那麼 Azure Active Directory (AD) 條件存取原則可封鎖存取組織內的不同應用程式。

這項功能可讓 ATP 掃描檔案、偵測威脅，以及報告 Windows 10 裝置上的任何風險。

請參閱[在 Intune 中啟用具有條件存取的 ATP](advanced-threat-protection.md)。

#### <a name="support-for-user-less-devices----1637553---"></a>支援無使用者裝置 <!-- 1637553 -->
Intune 可以評估不具使用者之裝置 (例如 Microsoft Surface Hub) 的合規性。 合規性原則可以針對特定裝置。 因此，可以針對沒有相關使用者的裝置判斷是否符合規範 (和不符合規範)。

#### <a name="delete-autopilot-devices----1713650---"></a>刪除 AutoPilot 裝置 <!-- 1713650 -->
Intune 系統管理員可以[刪除 Autopilot 裝置](enrollment-autopilot.md#delete-autopilot-devices)。

#### <a name="improved-device-deletion-experience---1832333---"></a>改進的裝置刪除體驗 <!--1832333 -->
您現在無須移除公司資料，或是將裝置重設為原廠預設值，就能[從 Intune 刪除裝置](devices-wipe.md#delete-devices-from-the-intune-portal)。

若要查看新體驗，請登入 Intune，然後選取 [裝置] > [所有裝置] > 裝置的名稱 > [刪除]。

如果您仍然想要確認抹除/淘汰，可以使用標準裝置生命週期途徑，方法是先發出 [移除公司資料] 和 [重設成出廠預設值]，再進行 [刪除]。 

#### <a name="play-sounds-on-ios-when-in-lost-mode----1947769---"></a>在處於遺失模式時於 iOS 上播放音效 <!-- 1947769 -->
當受監督的 iOS 裝置處於「行動裝置管理」(MDM) 的[遺失模式](device-lost-mode.md)時，您可以[播放音效](device-locate.md#activate-lost-mode-sound-alert-on-an-ios-device) ([裝置]  >  [所有裝置]  **> 選取 iOS 裝置 > [概觀]** >  [更多])。 此音效會持續播放，直到裝置解除遺失模式，或使用者停用了裝置上的音效。 適用於 iOS 裝置 9.3 和更新版本。

#### <a name="block-or-allow-web-results-in-searches-made-on-an-intune-device---1972804--"></a>禁止或允許在 Intune 裝置上執行的搜尋中出現 Web 結果 <!--1972804-->

系統管理員現在可以禁止裝置上的搜尋出現 Web 結果。

#### <a name="improved-error-messaging-for-apple-mdm-push-certificate-upload-failure----2172331---"></a>改進 Apple MDM Push Certificate 上傳失敗的錯誤訊息傳遞 <!-- 2172331 -->

錯誤訊息將會說明更新現有的 MDM 憑證時，必須使用相同的 Apple ID。

#### <a name="test-the-company-portal-for-macos-on-virtual-machines----2216679---"></a>在虛擬機器上的 macOS 測試公司入口網站 <!-- 2216679 -->

我們已發佈指導，協助 IT 系統管理員在 Parallels Desktop 與 VMware Fusion 之虛擬機器上的 macOS 中測試公司入口網站應用程式。 深入了解如何[虛擬 macOS 機器進行測試](macos-enroll.md#enroll-virtual-macos-machines-for-testing)。


### <a name="user-interface"></a>使用者介面

#### <a name="improved-device-tiles-in-the-windows-10-company-portal---2213364---"></a>改進 Windows 10 公司入口網站中的裝置磚 <!--2213364 -->

這些磚在更新之後將更方便視障使用者使用，而且可以為螢幕閱讀工具提供更好的效能。

#### <a name="send-diagnostic-reports-in-company-portal-app-for-macos----2216677---"></a>在 macOS 版公司入口網站應用程式中傳送診斷報告 <!-- 2216677 -->
macOS 裝置版的公司入口網站應用程式在更新之後，改進了使用者回報 Intune 相關錯誤的方式。 您的員工可以透過公司入口網站應用程式，進行下列作業：

- 將診斷報告直接上傳給 Microsoft 開發人員小組。
- 透過電子郵件將事件識別碼傳送給 IT 支援小組。

如需詳細資訊，請參閱[傳送 macOS 的錯誤](/intune-user-help/send-errors-macos)。

#### <a name="intune-adapts-to-fluent-design-system-in-the-company-portal-app-for-windows-10----1195010-wnready---"></a>Intune 在 Windows 10 版的公司入口網站中，採用了 Fluent Design System <!-- 1195010 WNready -->
Windows 10 版的 Intune 公司入口網站應用程式已更新為使用 [Fluent Design System's navigation view](https://docs.microsoft.com/en-us/windows/uwp/design/basics/navigation-basics) \(Fluent Design System 的瀏覽檢視\)。 您會發現應用程式側邊多了一個垂直靜態清單，列有最上層的所有頁面。 按一下任何連結都能快速檢視及來回切換頁面。 我們仍持續努力為 Intune 建立適應性更好、更彈性、更直觀及更加容易上手的體驗，而這只是好幾個更新中的第一個。 若要查看更新後的外觀，請參閱[應用程式 UI 的新功能](whats-new-app-ui.md)。

## <a name="week-of-april-16-2018"></a>2018 年 4 月 16 日當週

#### <a name="use-cisco-anyconnect-client-for-ios----eeready-1333708---"></a>使用適用於 iOS 的 Cisco AnyConnect 用戶端 <!-- EEready 1333708 -->

當您建立適用於 iOS 的新 VPN 設定檔時，現在有兩個選項：[Cisco AnyConnect] 和 [Cisco Legacy AnyConnect]。 Cisco AnyConnect 設定檔支援 4.0.7x 和較新版本。 現有的 iOS Cisco AnyConnect VPN 設定檔會標記為 **Cisco Legacy AnyConnect**，但仍會繼續以目前的方式搭配 Cisco AnyConnect 4.0.5x 和較舊版本運作。

> [!NOTE]
> 這項變更只適用於 iOS。 Android、Android for Work 及 macOS 平台仍然只有一個 Cisco AnyConnect 選項。

#### <a name="jamf-enrolled-macos-devices-can-now-register-with-intune----2370684---"></a>現在可以使用 Intune 註冊 Jamf 註冊的 macOS 裝置 <!-- 2370684 -->

版本 1.3 和 1.4 的 macOS 公司入口網站並未使用 Intune 成功註冊 Jamf 裝置。 版本 1.4.2 的 macOS 入口網站已修正此問題。


## <a name="week-of-april-9-2018"></a>2018 年 4 月 9 日當週  
#### <a name="updated-help-experience-in-company-portal-app-for-android----1631531---"></a>更新 Android 版公司入口網站應用程式的說明體驗 <!-- 1631531 -->

我們已更新 Android 公司入口應用程式的說明體驗，以符合 Android 平台的最佳做法。 現在，當使用者在應用程式中遇到問題時，可以點選 [功能表] > [說明]，然後：
- 向 Microsoft 傳送診斷記錄。
- 傳送描述問題和事件識別碼的電子郵件給公司支援人員。  

若要了解已更新的說明體驗，請參閱[使用電子郵件來傳送記錄](/intune-user-help/send-logs-to-your-it-admin-by-email-android)和[將錯誤傳送給 Microsoft](/intune-user-help/send-logs-to-microsoft-android)。


#### <a name="new-enrollment-failure-trend-chart-and-failure-reasons-table----1471783---"></a>新註冊失敗趨勢圖和失敗原因表 <!-- 1471783 -->

在 [註冊概觀] 頁面上，您可以檢視註冊失敗趨勢和前五大失敗原因。 按一下圖表或資料表，即可向下鑽研至詳細資料來尋找疑難排解建議和補救建議。

#### <a name="update-where-to-configure-your-app-protection-policies----2144597---"></a>更新設定應用程式保護原則的位置 <!-- 2144597 -->

在 Azure 入口網站的 Microsoft Intune 服務內，我們會暫時將您從 [Intune 應用程式防護] 服務刀鋒視窗重新導向至 [行動應用程式] 刀鋒視窗。 請注意，您所有的應用程式防護原則都已經在 Intune 中應用程式組態底下的 [行動應用程式] 刀鋒視窗上。 若前往 Intune 應用程式防護，您就會直接前往 Intune。 在 2018 年 4 月，我們將停止重新導向，並完全移除 [Intune 應用程式防護] 服務刀鋒視窗，如此一來 Intune 中的應用程式防護原則只會有一個位置。 

**此變更會對我造成什麼影響？**
這項變更會影響 Intune 獨立部署客戶和混合部署 (Intune 搭配 Configuration Manager) 客戶。 此整合將有助於簡化您的雲端管理。

**我需要為這項變更做什麼準備？**
請將 [Intune] 標記為我的最愛，而不是 [Intune 應用程式防護] 服務刀鋒視窗，並確定您熟悉 Intune 內 [行動應用程式] 刀鋒視窗中的應用程式保護原則工作流程。 在短時間內，我們會進行重新導向，然後就會移除 [應用程式保護] 刀鋒視窗。 請記住，所有應用程式保護原則都已經在 Intune 中，而您可以修改任何條件式存取原則。 如需有關修改條件式存取原則詳細資訊，請參閱 [Azure Active Directory 中的條件式存取](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)。 如需其他資訊，請參閱[什麼是應用程式保護原則？](app-protection-policy.md) 


## <a name="week-of-april-2-2018"></a>2018 年 4 月 2 日當週

### <a name="intune-apps"></a>Intune 應用程式

#### <a name="user-experience-update-for-the-company-portal-app-for-ios---1412866---"></a>iOS 版公司入口網站應用程式的使用者體驗更新 <!--1412866 -->
我們已經發行 iOS 版 公司入口網站應用程式的主要使用者經驗更新。 此更新採用全新現代化外觀的視覺設計。 應用程式的功能不變，但強化了可用性與協助工具功能。  

此外還包括：
- iPhone X 的支援。
- 應用程式啟動速度與載入回應的速度變快，可以節省使用者寶貴的時間。
- 增加更多的進度列，方便使用者掌握最新旳狀態資訊。
- 改善使用者上傳記錄的方式，方便在發生問題時回報。  

若要查看更新後的外觀，請參閱[應用程式 UI 的新功能](whats-new-app-ui.md)。

#### <a name="protect-on-premises-exchange-data-using-intune-app-and-ca----1056954---"></a>使用 Intune APP 和 CA 來保護內部部署 Exchange 資料 <!-- 1056954 -->
您現在可以搭配 Outlook Mobile 使用 Intune「應用程式原則保護」(APP) 和「條件式存取」(CA) 來保護對內部部署 Exchange 資料的存取。 若要在 Azure 入口網站內新增或修改應用程式保護原則，請選取 [Microsoft Intune] > [行動應用程式] > [應用程式保護原則]。 開始使用此功能之前，請確定您符合 [iOS 版和 Android 版 Outlook 的需求](https://technet.microsoft.com/en-us/library/mt846639(v=exchg.160).aspx)。

## <a name="week-of-march-26-2018"></a>2018 年 3 月 26 日當週

### <a name="app-management"></a>應用程式管理

#### <a name="alerts-for-expiring-ios-line-of-business-lob-apps-for-microsoft-intune----748789---"></a>Microsoft Intune 即將到期的 iOS 企業營運 (LOB) 應用程式警示 <!-- 748789 -->

在 Azure 入口網站中，Intune 會提醒您有即將到期的 iOS 企業營運應用程式。 上傳新版 iOS 企業營運應用程式之後，Intune 就會從應用程式清單中移除到期通知。 此到期通知只對新上傳的 iOS 企業營運應用程式有效。 在 iOS LOB 應用程式佈建設定檔到期前 30 天會出現警告。 到期時，警示就會變更為 [已到期]。

#### <a name="customize-your-company-portal-themes-with-hex-codes---1049561---"></a>以十六進位碼自訂您的公司入口網站佈景主題 <!--1049561 -->

您可以使用十六進位碼自訂公司入口網站應用程式的佈景主題色彩。 當您輸入您的十六進位碼時，Intune 會判斷可在文字色彩與背景色彩之間提供最高程度對比的文字色彩。 您可以在 [Mobile Apps] > **[公司入口網站]** 中預覽文字色彩和公司標誌的色彩。

### <a name="including-and-excluding-app-assignment-based-on-groups-for-android-enterprise----1813081---"></a>Android Enterprise 依據群組來包含和排除應用程式指派 <!-- 1813081 -->

Android Enterprise (先前稱為 Android for Work) 支援包含及排除群組，但不支援預先建立的 [所有使用者] 和 [所有裝置] 內建群組。 如需詳細資訊，請參閱 [Microsoft Intune 的包含與排除應用程式指派](apps-inc-exl-assignments.md)。


### <a name="device-management"></a>裝置管理

#### <a name="new-security-enhancements-in-the-intune-service-----1637539---"></a>Intune 服務中的新安全性增強功能  <!-- 1637539 -->   

我們已在 Azure 上的 Intune 中導入一個切換，可供 Intune 獨立客戶用來將沒有任何已指派原則的裝置視為 [符合規範] (關閉安全性功能)，或將這些裝置視為 [不符合規範] (開啟安全性功能)。 這將可確保只有在評估裝置合規性之後，才能存取資源。

此功能影響您的方式會依您是否已經指派合規性原則而有所不同。

- 如果您是新的或現有的帳戶，而且未將任何合規性原則指派給裝置，則此切換自動設定為 [符合規範]。 在主控台中，預設是將此功能設定為關閉。 這不會影響任何使用者。
- 如果您是現有的帳戶，而且有任何已獲指派合規性原則的裝置，則此切換會自動設定為 [不符合規範]。 隨著三月更新的首度發行，預設就會將此功能設定為開啟。

如果您使用合規性原則搭配「條件式存取」(CA)，並且開啟此功能，CA 現在就會封鎖任何未至少已獲指派一個合規性原則的裝置。 除非您至少將一個合規性原則指派給所有裝置，否則與這些裝置關聯且先前已獲允許存取電子郵件的使用者將會失去其存取權。   

請注意，雖然預設切換狀態隨著 Intune 服務的三月更新而立即顯示在 UI 中，但系統並不會立即實施此切換狀態。 在我們讓您的帳戶擁有可運作的切換以進行正式發行前的小眾測試之前，您對此切換進行的任何變更將不會影響裝置合規性。 當我們完成您帳戶的正式發行前小眾測試之後，會透過「訊息中心」通知您。 在您的 Intune 服務進行三月更新之後，這可能會花費幾天的時間。

**其他資訊**：[https://aka.ms/compliance_policies](https://aka.ms/compliance_policies)

#### <a name="enhanced-jailbreak-detection----846515---"></a>增強的越獄偵測 <!-- 846515 -->

加強的越獄偵測是一項新的合規性設定，可改進 Intune 評估已越獄裝置的方式。 此設定會使裝置更頻繁地簽入 Intune ，這會使用裝置的位置服務並影響電池使用量。

#### <a name="reset-passwords-for-android-o-devices----1238299---"></a>重設 Android O 裝置的密碼 <!-- 1238299 -->
您將能夠使用工作設定檔重設已註冊 Android 8.0 裝置的密碼。 當您向 Android 8.0 裝置傳送「重設密碼」要求時，它會將新的裝置解除鎖定密碼或受控設定檔查問設定成目前的使用者。 這會傳送密碼或查問，並立即生效。

#### <a name="targeting-compliance-policies-to-devices-in-device-groups---1307012---"></a>讓合規性原則以裝置群組中的裝置為目標 <!--1307012 -->

您可以讓合規性原則以使用者群組中的使用者為目標。 在此更新中，您可以讓合規性原則以裝置群組中的裝置為目標。 隨著裝置群組一起作為目標的裝置不會收到任何合規性動作。

#### <a name="new-management-name-column----1333586---"></a>新的管理名稱資料行 <!-- 1333586 -->
 [裝置] 刀鋒視窗中會提供名為 [管理名稱] 的新資料行。 此名稱會依照下列公式自動產生且不可編輯，並會指派給每一個裝置：
- 所有裝置的預設名稱：<username><em><devicetype></em><enrollmenttimestamp>
- 針對大量新增裝置：<PackageId/ProfileId><em><DeviceType></em><EnrollmentTime>

這是在 [裝置] 刀鋒視窗中的可選資料行。 預設並不會提供此資料行，您只能藉由使用資料行選取器來存取它。 裝置名稱不會受到這個新資料行影響。

#### <a name="ios-devices-are-prompted-for-a-pin-every-15-minutes---1550837---"></a>每 15 分鐘都會提示 iOS 裝置輸入PIN <!--1550837 -->
將合規性或設定原則套用至 iOS 裝置之後，系統會每隔 15 分鐘提示使用者設定 PIN。 系統會持續提示使用者，直到設定 PIN 為止。

#### <a name="schedule-your-automatic-updates---1805514---"></a>排程自動更新 <!--1805514 -->
Intune 可讓您使用 [Windows Update Ring 設定](windows-update-for-business-configure.md)來控制自動更新安裝。 在此更新中，您可以排定重複發生的更新，包括週、日及時間。

#### <a name="use-fully-distinguished-name-as-subject-for-scep-certificate---2221763---"></a>使用完整辨別名稱作為 SCEP 憑證的主體 <!--2221763 -->
當您建立 SCEP 憑證設定檔時，會輸入主體名稱。 在此更新中，您可以使用完整辨別名稱作為主體。 針對 [主體名稱]，選取 [自訂]，然後輸入 `CN={{OnPrem_Distinguished_Name}}`。 若要使用 `{{OnPrem_Distinguished_Name}}` 變數，請務必將使用 [Azure Active Directory (AD) Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect) 的 `onpremisesdistingishedname` 使用者屬性與 Azure AD 同步。

### <a name="device-configuration"></a>裝置設定

#### <a name="enable-bluetooth-contact-sharing---android-for-work---1098983---"></a>啟用藍牙連絡人共用 - Android for Work <!--1098983 -->
Android 預設會防止工作設定檔中的連絡人與藍牙裝置同步。 因此，工作設定檔連絡人不會顯示在藍牙裝置的呼叫者識別碼上。

在此更新中，[Android for Work] > [裝置限制] > [工作設定檔設定] 會有一個新的設定：
- 透過藍牙的連絡人共用

Intune 系統管理員可以設定這些設定，以啟用共用。 將裝置與汽車藍牙裝置配對時，這十分有用，而汽車藍牙裝置顯示免持式使用的呼叫者識別碼。 啟用時，會顯示工作設定檔連絡人。 未啟用時，不會顯示工作設定檔連絡人。

#### <a name="configure-gatekeeper-to-control-macos-app-download-source----1690459---"></a>設定閘道管理員以控制 macOS 應用程式下載來源 <!-- 1690459 -->

您可以藉由控制可下載應用程式的位置，以設定 Gatekeeper 來為您的裝置提供應用程式安全防護。 您可以設定下列下載來源：[Mac App Store]、[Mac App Store 和已識別的開發人員]或 [任何位置]。 您可以藉由按住 Control 並同時按一下來覆寫這些 Gatekeeper 控制措施，以設定使用者是否可以安裝應用程式。

您可以在**裝置設定** -> **建立設定檔** -> **macOS** -> **Endpoint Protection** 中找到這些設定。

#### <a name="configure-the-mac-application-firewall----1690461---"></a>設定 Mac 應用程式防火牆 <!-- 1690461 -->

您可以設定 Mac 應用程式防火牆。 您可以利用此項目以每一應用程式為單位控制連線，而非以每一連接埠為單位。 這讓您能更輕鬆地取得防火牆保護的優點，也可協助防止不想要的應用程式控制為合法應用程式開啟之網路連接埠。

您可以在**裝置設定** -> **建立設定檔** -> **macOS** -> **Endpoint Protection** 中找到此功能。

啟用防火牆設定後，您可以使用兩種策略來設定防火牆：

- 封鎖所有連入連線

   您可以為目標裝置封鎖所有連入連線。 如果您選擇這樣做，系統就會針對所有應用程式封鎖連入連線。

- 允許或封鎖特定應用程式

   您可以允許或封鎖特定的應用程式，使其無法接收連入連線。 您也可以啟用隱形模式，以避免回應探查要求。

####  <a name="detailed-error-codes-and-messages----1376342---"></a>詳細的錯誤碼和訊息<!-- 1376342 -->

在您的 [裝置設定] 中，可以檢視更詳細的錯誤碼和錯誤訊息。 這項改良的報告功能會顯示設定、這些設定的狀態，以及有關疑難排解的詳細資料。

##### <a name="more-information"></a>詳細資訊

- 封鎖所有連入連線

   這會封鎖所有共用服務 (例如檔案共用和螢幕共用)，使其無法接收連入連線。 仍允許接收連入連線的系統服務是：
  - configd - 實作 DHCP 與其他網路設定服務
  - mDNSResponder - 實作 Bonjour
  - racoon - 實作 IPSec

    若要使用共用服務，請確認**連入連線**設定為**未設定** (而不是**封鎖**)。

- 隱形模式

   啟用此模式來防止電腦回應探查要求。 電腦仍然會回應已授權應用程式的連入要求。 ICMP (ping) 等未預期的要求都會予以忽略。

#### <a name="disable-checks-on-device-restart---1805490---"></a>停用裝置重新啟動的檢查 <!--1805490 -->
Intune 可提供您控制權來[管理軟體更新](windows-update-for-business-configure.md)。 在此更新中，預設會提供並啟用 <strong>[重新啟動檢查]</strong> 屬性。 若要跳過重新啟動裝置時進行的典型檢查 (如作用中使用者、電池電量等等) 時，請選取 [跳過]。

#### <a name="new-windows-10-insider-preview-channels-available-for-deployment-rings----1746293---"></a>可供部署通道使用的新 Windows 10 Insider Preview 通道 <!-- 1746293 -->
現在，當您建立 Windows 10 部署通道時，可以選擇選取下列 Windows 10 Insider Preview 維護通道：
- Windows 測試人員組建 &#8208; 快
- Windows 測試人員組建 &#8208; 慢
- 發行 Windows 測試人員組建 

如需有關這些通道的詳細資訊，請參閱[管理 Insider Preview 組建](https://insider.windows.com/en-us/for-business-organization-admin/)。   
如需有關在 Intune 中建立部署通道的詳細資訊，請參閱[管理 Intune 中的軟體更新](windows-update-for-business-configure.md)。

### <a name="intune-apps"></a>Intune 應用程式

#### <a name="company-portal-enrollment-improved----1874230-eeready--"></a>改善的公司入口網站註冊 <!-- 1874230 eeready-->
使用者如果是在 Windows 10 1703 組建或更新版本上使用公司入口網站來註冊裝置，現在將能夠在不離開應用程式的情況下，完成第一個註冊步驟。
#### <a name="hololens-and-surface-hub-now-appear-in-device-lists---1725868---"></a>HoloLens 和 Surface Hub 現在會出現在裝置清單 <!--1725868 --> 中
我們已新增支援，可向 Android 版公司入口網站應用程式顯示已在 Intune 註冊的 HoloLens 和 Surface Hub 裝置。

#### <a name="custom-book-categories-for-volume-purchase-program-vpp-ebooks----1488911---"></a>為大量採購方案 (VPP) 電子書自訂書籍類別 <!-- 1488911 -->
您可以建立自訂電子書類別，然後將 VPP 電子書指派給這些自訂電子書類別。 終端使用者便可以看見新建立的電子書類別，以及指派給這些類別的書籍。 如需詳細資訊，請參閱[使用 Microsoft Intune 管理大量採購的應用程式與書籍](vpp-apps.md)。  

#### <a name="support-changes-for-company-portal-app-for-windows-send-feedback-option----2070166---"></a>針對 Windows 版公司入口網站應用程式傳送意見反應選項的支援已變更 <!-- 2070166 -->
從 2018 年 4 月 30 日起，Windows 版公司入口網站應用程式中的 [傳送意見反應] 選項僅可在執行 Windows 10 年度更新 (1607) 及更新版本的裝置上執行。 搭配下列版本使用 Windows 版公司入口網站應用程式時，不再支援傳送意見反應的選項：  
- Windows 10，1507 版本  
- Windows 10，1511 版本  
- Windows Phone 8.1 

如果您的裝置執行的是 Windows 10 RS1 或更新版本，請從市集下載最新的 Windows 版公司入口網站應用程式。 如果您執行的是不支援的版本，請繼續透過下列通道傳送意見反應： 
- Windows 10 上的 [意見反應中樞] 應用程式
- 電子郵件 WinCPfeedback@microsoft.com  

#### <a name="new-windows-defender-application-guard-settings----1631890---"></a>新的 Windows Defender 應用程式防護設定 <!-- 1631890 -->

- **啟用圖形加速**：系統管理員可以啟用「Windows Defender 應用程式防護」的虛擬圖形處理器。 此設定可讓 CPU 將圖形轉譯卸載至 vGPU。 使用圖形運算密集的網站或觀賞容器內的影片時，這可以改善效能。

- **SaveFilestoHost**：系統管理員可以讓檔案經由在容器中執行的 Microsoft Edge 到主機檔案系統。 開啟這個功能可讓使用者從容器中的 Microsoft Edge 將檔案下載到主機檔案系統。

#### <a name="mam-protection-policies-targeted-based-on-management-state----1665993---"></a>根據管理狀態將 MAM 保護原則設為目標 <!-- 1665993 -->
您可以根據裝置管理狀態將 MAM 原則設為目標：
- **Android 裝置** - 您可以將非受控裝置、受 Intune 管理的裝置及受 Intune 管理的 Android Enterprise 設定檔 (先前稱為 Android for Work) 設為目標。
- **iOS 裝置** - 您可以將非受控裝置 (僅限 MAM) 或受 Intune 管理的裝置設為目標。

    > [!NOTE]
    > - 此功能的 iOS 支援會在 2018 年的整個 4 月首度發行。

如需詳細資訊，請參閱[根據裝置管理狀態將應用程式保護原則設為目標](app-protection-policies.md)。

#### <a name="improvements-to-the-language-in-the-company-portal-app-for-windows----1683758---"></a>改進 Windows 版公司入口網站應用程式中的語言 <!-- 1683758 -->
我們已改進 Windows 10 版公司入口網站中的語言，不僅對使用者來說更簡單明瞭，也更專屬於您的公司。 若要查看我們所做改進的範例影像，請參閱[應用程式 UI 的新功能](whats-new-app-ui.md)。

#### <a name="new-additions-to-our-docs-about-user-privacy----1440709---"></a>在我們的文件中新增有關使用者隱私權的部分 <!-- 1440709 -->
我們努力讓使用者對其資料和隱私權有更多的控制，因此我們發佈了文件更新，說明如何檢視及移除公司入口網站應用程式儲存在本機的資料。 您可以在下列位置找到這些更新：

- **Android**：[如何從 Intune 移除 Android 裝置](/intune-user-help/unenroll-your-device-from-intune-android.md)
- **Android (如果使用者已拒絕使用規定)**[移除裝置管理 (如果您已拒絕「使用規定」)](/intune-user-help/unenroll-your-device-from-intune-if-you-declined-terms-of-use-android.md)
- **iOS**：[從 Intune 移除 iOS 裝置](/intune-user-help/unenroll-your-device-from-intune-ios.md)
- **Windows**：[從 Intune 移除 Windows 裝置](/intune-user-help/unenroll-your-device-from-intune-windows.md)

## <a name="week-of-march-19-2018"></a>2018 年 3 月 19 日當週

### <a name="export-all-devices-into-csv-files-in-ie-edge-or-chrome----2258071---"></a>在 IE、Edge 或 Chrome 中將所有裝置匯出成 CSV 檔案 <!-- 2258071 -->
在 [裝置] > [所有裝置] 中，您可以將裝置**匯出**成 CSV 格式的清單。 裝置超過 10,000 部的 Internet Explorer (IE) 使用者可以成功將其裝置匯出成多個檔案。 每個檔案最多可包含 10,000 部裝置。

裝置超過 30,000 部的 Edge 和 Chrome 使用者可以成功將其裝置匯出成多個檔案。 每個檔案最多可包含 30,000 部裝置。

[管理裝置](device-management.md)可以針對您可以對所管理裝置執行的操作，提供更多的詳細資料。

## <a name="week-of-march-12-2018"></a>2018 年 3 月 12 日當週

### <a name="azure-active-directory-web-sites-can-require-the-intune-managed-browser-app-and-support-single-sign-on-for-the-managed-browser-public-preview----710595---"></a>Azure Active Directory 網站可以要求使用 Intune Managed Browser 應用程式，並支援 Managed Browser (公開預覽) 的單一登入 <!-- 710595 -->

使用 Azure Active Directory (Azure AD) 時，您現在可在行動裝置上限制只有 Intune Managed Browser 應用程式可以存取網站。 在 Managed Browser 中，網站資料會受到保護，而且會與使用者個人資料分開管理。 此外，針對受 Azure AD 保護的網站，Managed Browser 也支援單一登入功能。 當使用者登入 Managed Browser，或在裝置上搭配使用 Managed Browser 與受 Intune 管理的其他應用程式時，即可在不需輸入認證的情況下，讓 Managed Browser 存取受 Azure AD 保護的公司網站。 這項功能適用於 Outlook Web Access (OWA) 和 SharePoint Online 等網站，以及透過 Azure App Proxy 存取的內部網路資源等其他公司網站。 如需詳細資訊，請參閱 [Access controls in Azure Active Directory conditional access](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-controls) (Azure Active Directory 條件式存取中的存取控制)。

#### <a name="company-portal-app-for-android-visual-updates---976944---"></a>Android 版公司入口網站的視覺效果更新 <!--976944 -->

我們已更新 Android 版公司入口網站應用程式，以遵循 Android 的 [Material Design](https://material.io/) 指導方針。 您可以在[應用程式 UI 最新內容](whats-new-app-ui.md)一文中看到新圖示的影像。

### <a name="new-windows-defender-exploit-guard-settings----1631893---"></a>新的 Windows Defender 惡意探索防護設定 <!-- 1631893 -->

有六項新的 [攻擊面縮減] 設定和擴充的 [受控資料夾存取權: 資料夾保護] 功能可用。 這些設定位在：Device configuration\Profiles\
建立 profile\Endpoint protection\Windows Defender 惡意探索防護。

#### <a name="attack-surface-reduction"></a>攻擊表面縮減

|設定名稱  |設定選項  |說明  |
|---------|---------|---------|
|進階勒索軟體防護|啟用、稽核、未設定|使用積極的勒索軟體防護。|
|從 Windows 本機安全性授權子系統設立認證竊取旗標|啟用、稽核、未設定|從 Windows 本機安全性授權子系統設立認證竊取旗標 (lsass.exe)。|
|從 PSExec 和 WMI 命令建立處理程序|封鎖、稽核、未設定|封鎖源自 PSExec 和 WMI 命令的處理程序建立。|
|從 USB 執行的不受信任和不帶正負號的處理程序|封鎖、稽核、未設定|封鎖從 USB 執行的不受信任和不帶正負號的處理程序。|
|不符合普遍性、存留期或受信任清單條件的可執行檔|封鎖、稽核、未設定|封鎖執行可執行檔，除非它們符合普遍性、存留期或受信任清單的條件。|

#### <a name="controlled-folder-access"></a>受控資料夾存取權

|              設定名稱               |                                                              設定選項                                                              | 說明 |
|-----------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|-------------|
| 資料夾防護 (已實作) | 未設定、啟用、僅稽核 (已實作)<br><br> <strong>新增</strong><br>封鎖磁碟修改、稽核磁碟修改 |             |

保護檔案和資料夾免於惡意應用程式未經授權的變更。<br><br>**啟用**：免於不受信任的應用程式修改或刪除受保護資料夾中的檔案，也不讓這些應用程式在磁碟磁區寫入資料。<br><br>
**僅封鎖磁碟修改**：<br>封鎖不受信任的應用程式在磁碟磁區寫入資料。 不受信任的應用程式仍然可以修改或刪除受保護資料夾中的檔案。|

## <a name="week-of-february-19-2018"></a>2018 年 2 月 19 日這週

### <a name="device-enrollment"></a>裝置註冊

#### <a name="intune-support-for-multiple-apple-dep--apple-school-manager-accounts----747685---"></a>Intune 支援多個 Apple DEP / Apple School Manager 帳戶 <!-- 747685 -->

Intune 現在支援註冊最多達 100 個來自不同 [Apple 裝置註冊計劃 (DEP)](device-enrollment-program-enroll-ios.md) 或 [Apple School Manager](apple-school-manager-set-up-ios.md) 帳戶的裝置。 每個上傳的權杖可以針對註冊設定檔和裝置來個別管理。 不同的註冊設定檔可以根據上傳的 DEP/School Manager 權杖來自動指派。 如果上傳了多個 School Manager 權杖，則一次只能與 Microsoft School Data Sync 共用一個權杖。

移轉之後，透過 Graph 來管理 Apple DEP 或 ASM 的搶鮮版 (Beta) Graph API 與發佈的指令碼將無法再運作。 新的搶鮮版 (Beta) Graph API 正在開發，將會在移轉後發行。

#### <a name="see-enrollment-restrictions-per-user----1634444-eeready-wnready---"></a>查看每位使用者的註冊限制 <!-- 1634444 eeready wnready -->
在 [疑難排解] 刀鋒視窗中，您現在可以從 [指派] 清單中選取 [註冊限制]，以查看對每位使用者有效的[註冊限制](enrollment-restrictions-set.md)。

### <a name="device-management"></a>裝置管理
#### <a name="windows-defender-health-status-and-threat-status-reports---854704---"></a>Windows Defender 健全狀況狀態和威脅狀態報告 <!--854704 -->

瞭解 Windows Defender 的健全狀況狀態是管理 Windows 電腦的關鍵。  使用此更新，Intune 會在 Windows Defender 代理程式的健全狀況狀態中新增報告和動作。 在[裝置合規性工作負載](compliance-policy-monitor.md)中使用狀態積存報表，即可看到需要下列任一項的裝置：
- 簽章更新
- [重新啟動]，
- 手動介入
- 完整掃描
- 需要介入的其他代理程式狀態

每個狀態類別的鑽研報表都會列出需要注意的個別電腦，或那些回報為**清除**的電腦。

#### <a name="new-privacy-settings-for-device-restrictions---1308926---"></a>裝置限制的新隱私權設定 <!--1308926 -->
裝置現在有[兩項新的隱私權設定](device-restrictions-windows-10.md#privacy)可用：
- **發佈使用者活動**：設定此項以**封鎖**防止共用體驗以及在工作切換器中探索最近使用的資源。
- **僅限本機活動**：設定此項以**封鎖**防止共用體驗，以及僅根據本機活動，在工作切換器中探索最近使用的資源。

#### <a name="new-settings-for-the-edge-browser---1469166---"></a>Edge 瀏覽器的新設定 <!--1469166 -->
現在使用 Edge 瀏覽器的裝置有[兩項新設定](device-restrictions-windows-10.md#edge-browser)可用：[我的最愛檔案路徑] 和 [我的最愛的變更]。

### <a name="app-management"></a>應用程式管理
#### <a name="protocol-exceptions-for-applications---1035509---"></a>應用程式的通訊協定例外狀況 <!--1035509 -->

您現在可以建立 Intune 行動應用程式管理 (MAM) 資料傳輸原則的例外狀況，開啟特定的非受控應用程式。 這類應用程式必須為 IT 所信任。 當資料傳輸原則設為**僅限受管理應用程式** 時，除您建立的例外狀況，資料傳輸仍僅限於受 Intune 管理的應用程式。 您可以使用通訊協定 (iOS) 或套件 (Android) 來建立限制。

例如，您可以將 Webex 套件新增為 MAM 資料傳輸原則的例外狀況。 這樣可以直接在 Webex 應用程式中開啟受控 Outlook 電子郵件訊息中的 Webex 連結。 其他非受控應用程式中的資料傳輸仍會受到限制。 如需詳細資訊，請參閱[應用程式的資料傳輸原則例外狀況](app-protection-policies-exception.md)。

#### <a name="windows-information-protection-wip-encrypted-data-in-windows-search-results----1469193---"></a>Windows 搜尋結果中的 Windows 資訊保護 (WIP) 加密資料 <!-- 1469193 -->
Windows 資訊保護 (WIP) 原則中的設定現在可讓您控制 Windows 搜尋結果是否包含 WIP 加密資料。 在 Windows 資訊保護原則的 [進階設定] 中，選取 [允許 Windows 搜尋索引子搜尋加密項目] 來設定此應用程式保護原則選項。 應用程式保護原則必須設為 *Windows 10* 平台，且應用程式原則 [註冊狀態] 必須設為 [註冊]。 如需詳細資訊，請參閱[允許 Windows 搜尋索引子搜尋加密項目](windows-information-protection-policy-create.md#allow-windows-search-indexer-to-search-encrypted-items)。

#### <a name="configuring-a-self-updating-mobile-msi-app----1740840---"></a>設定自行更新的行動 MSI 應用程式 <!-- 1740840 -->
您可以設定已知的自行更新行動 MSI 應用程式略過版本檢查程序。 這項功能對於不陷入競爭狀況很有用。 例如，當應用程式開發人員正在執行自動更新的應用程式，也正被 Intune 更新時，就可能發生這種競爭狀況。 雙方都可能嘗試在 Windows 用戶端上強制執行某個版本的應用程式，這可能造成衝突。 對於這些自動更新的 MSI 應用程式，您可以在 [應用程式資訊] 刀鋒視窗中設定 [略過應用程式版本] 設定。 當此設定切換為 [是] 時，Microsoft Intune 將會忽略 Windows 用戶端上安裝的應用程式版本。

#### <a name="related-sets-of-app-licenses-supported-in-intune----1864117---"></a>Intune 支援的相關應用程式授權集 <!-- 1864117 -->
Azure 入口網站中的 Intune 現在支援相關的應用程式授權集，作為 UI 中單一應用程式項目。 此外，從商務用 Microsoft Store 同步處理的任何離線授權應用程式都會合併到單一應用程式項目，而個別套件的所有部署詳細資料都會移轉至單一項目。 若要在 Azure 入口網站中檢視相關的應用程式授權集，請選取 [Mobile Apps] 刀鋒視窗中的 [應用程式授權]。

### <a name="device-configuration"></a>裝置設定
#### <a name="windows-information-protection-wip-file-extensions-for-automatic-encryption----1463582---"></a>自動加密的 Windows 資訊保護 (WIP) 檔案副檔名 <!-- 1463582 -->
Windows 資訊保護 (WIP) 原則中的設定現在可讓您指定，哪些檔案副檔名會在從公司界限內的伺服器訊息區塊 (SMB) 共用 (如 WIP 原則中所定義) 複製時自動加密。

#### <a name="configure-resource-account-settings-for-surface-hubs"></a>設定 Surface Hub 的資源帳戶設定

您現在可以從遠端設定 Surface Hub 的資源帳戶設定。

Surface Hub 會使用資源帳戶驗證 Skype/Exchange 以加入會議。
您會想要建立唯一的資源帳戶，使 Surface Hub 在會議中顯示為會議室。
例如，像**會議室 B41/6233** 的資源帳戶。

> [!NOTE]
> - 如果欄位留白，您會覆寫先前在裝置上設定的屬性。
>
> - Surface Hub 的資源帳戶內容可以動態變更。 例如，開啟密碼輪換。 因此，Azure 主控台中的這些值很可能需要一些時間才能反映裝置的實際狀況。
>
>   若要了解 Surface Hub 目前的設定內容，資源帳戶資訊可以包含在硬體清查 (已有 7 天間隔) 中，或當成唯讀屬性。 為在採取遠端動作後強化精確度，您可以立即在執行動作後取得參數狀態，更新 Surface Hub 上的帳戶/參數。


##### <a name="attack-surface-reduction"></a>攻擊表面縮減


|設定名稱  |設定選項  |說明  |
|---------|---------|---------|
|執行電子郵件中受密碼保護的可執行檔內容|封鎖、稽核、未設定|避免執行透過電子郵件下載的受密碼保護可執行檔。|
|進階勒索軟體防護|啟用、稽核、未設定|使用積極的勒索軟體防護。|
|從 Windows 本機安全性授權子系統設立認證竊取旗標|啟用、稽核、未設定|從 Windows 本機安全性授權子系統設立認證竊取旗標 (lsass.exe)。|
|從 PSExec 和 WMI 命令建立處理程序|封鎖、稽核、未設定|封鎖源自 PSExec 和 WMI 命令的處理程序建立。|
|從 USB 執行的不受信任和不帶正負號的處理程序|封鎖、稽核、未設定|封鎖從 USB 執行的不受信任和不帶正負號的處理程序。|
|不符合普遍性、存留期或受信任清單條件的可執行檔|封鎖、稽核、未設定|封鎖執行可執行檔，除非它們符合普遍性、存留期或受信任清單的條件。|

##### <a name="controlled-folder-access"></a>受控資料夾存取權

|              設定名稱               |                                                              設定選項                                                              | 說明 |
|-----------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|-------------|
| 資料夾防護 (已實作) | 未設定、啟用、僅稽核 (已實作)<br><br> <strong>新增</strong><br>封鎖磁碟修改、稽核磁碟修改 |             |

保護檔案和資料夾免於惡意應用程式未經授權的變更。<br><br>**啟用**：免於不受信任的應用程式修改或刪除受保護資料夾中的檔案，也不讓這些應用程式在磁碟磁區寫入資料。<br><br>
**僅封鎖磁碟修改**：<br>封鎖不受信任的應用程式在磁碟磁區寫入資料。 不受信任的應用程式仍然可以修改或刪除受保護資料夾中的檔案。|

#### <a name="additions-to-system-security-settings-for-windows-10-and-later-compliance-policies---1704133--"></a>Windows 10 和更新版本系統安全性設定新增項目的相容性原則 <!--1704133-->

Windows 10 相容性設定的新增項目現在已可供使用，但需要防火牆及 Windows Defender 防毒軟體才能包含此內容。


### <a name="role-based-access-control"></a>以角色為基礎的存取控制
### <a name="intune-apps"></a>Intune 應用程式
#### <a name="support-for-offline-apps-from-the-microsoft-store-for-business---1222672--"></a>支援來自商務用 Microsoft 網上商店的離線應用程式 <!--1222672-->
您從商務用 Microsoft Store 購買的離線應用程式現在會同步處理至 Azure 入口網站。 您可以將這些應用程式部署至裝置群組或使用者群組。 離線應用程式會透過 Intune 安裝，而不透過市集。

#### <a name="prevent-end-users-from-manually-adding-or-removing-accounts-in-the-work-profile----1728700---"></a>防止終端使用者在工作設定檔中手動新增或移除帳戶 <!-- 1728700 -->

當您將 Gmail 應用程式部署到 Android for Work 設定檔時，現在可以使用 Android for Work 裝置限制設定檔中的 [Add and remove accounts] (新增與移除帳戶) 設定，防止終端使用者在工作設定檔中手動新增或移除帳戶。

## <a name="week-of-february-5-2018"></a>2018 年 2 月 5 日這週

### <a name="device-enrollment"></a>裝置註冊

#### <a name="new-option-for-user-authentication-for-apple-bulk-enrollment----747625-eeready---"></a>適用於 Apple 大量註冊的使用者驗證新選項 <!-- 747625 eeready -->

> [!NOTE]
> 新的租用戶會立即看到此項目。 現有租用戶的這項功能會在 4 月推出。 全部推出之後，您可能無法存取這些新功能。

Intune 現在可讓您將公司入口網站應用程式用於下列註冊方法，以對裝置進行驗證：

- Apple 裝置註冊方案
- Apple School Manager
- Apple Configurator 註冊

使用 [公司入口網站] 選項時，可以強制執行 Azure Active Directory 多重要素驗證，而不會封鎖這些註冊方法。

使用 [公司入口網站] 選項時，針對使用者親和性註冊，Intune 會跳過 iOS 設定輔助程式中的使用者驗證。 這表示該裝置一開始會註冊為無使用者的裝置，因此不會收到使用者群組的設定或原則。 它只會接收裝置群組的設定和原則。 不過，Intune 會自動在裝置上安裝公司入口網站應用程式。 第一位啟動並登入公司入口網站應用程式的使用者，將會在 Intune 中與該裝置產生關聯。 此時，使用者將會收到其使用者群組的設定和原則。 使用者關聯需要重新註冊才可以變更。

#### <a name="intune-support-for-multiple-apple-dep--apple-school-manager-accounts----747685-eeready---"></a>Intune 支援多個 Apple DEP / Apple School Manager 帳戶 <!-- 747685 eeready -->

Intune 現在支援註冊最多達 100 個來自不同 Apple 裝置註冊計劃 (DEP) 或 Apple School Manager 帳戶的裝置。 每個上傳的權杖可以針對註冊設定檔和裝置來個別管理。 不同的註冊設定檔可以根據上傳的 DEP/School Manager 權杖來自動指派。 如果上傳了多個 School Manager 權杖，則一次只能與 Microsoft School Data Sync 共用一個權杖。

移轉之後，透過 Graph 來管理 Apple DEP 或 ASM 的搶鮮版 (Beta) Graph API 與發佈的指令碼將無法再運作。 新的搶鮮版 (Beta) Graph API 正在開發，將會在移轉後發行。

### <a name="remote-printing-over-a-secure-network----1709994----"></a>透過安全網路進行遠端列印 <!-- 1709994  -->
PrinterOn 的無線行動列印方案，可讓使用者隨時隨地透過安全的網路來進行遠端列印。 PrinterOn 將與適用於 iOS 和 Android 的 Intune APP SDK 整合。 您將能透過管理主控台中的 [應用程式保護原則] 刀鋒視窗，讓應用程式保護原則以此應用程式為目標。 終端使用者將能夠透過 Play 商店或 iTunes 下載 'PrinterOn for Microsoft' 應用程式，以在其 Intune 生態系統內使用。

### <a name="macos-company-portal-support-for-enrollments-that-use-the-device-enrollment-manager----1352411---"></a>macOS 公司入口網站支援使用裝置註冊管理員註冊 <!-- 1352411 -->

使用者現在於使用 macOS 公司入口網站進行註冊時，已可以使用裝置註冊管理員。

## <a name="week-of-january-29-2018"></a>2018 年 1 月 29 日當週

### <a name="device-enrollment"></a>裝置註冊

#### <a name="alerts-for-expired-tokens-and-tokens-that-will-soon-expire----1639263---"></a>過期的權杖與即將過期之權杖的警示 <!-- 1639263 -->
概觀頁面現在會針對過期的權杖與即將過期的權杖顯示警示。 當您按一下單一權杖的警示時，將會移至權杖的詳細資料頁面。  當您按一下多個權杖的警示時，將會移至所有權杖的清單，其中包含權杖的狀態。 系統管理員應該在到期日之前更新其權杖。

### <a name="device-management"></a>裝置管理

#### <a name="remote-erase-command-support-for-macos-devices----1438084---"></a>macOS 裝置的遠端「清除」命令支援 <!-- 1438084 -->

系統管理員可以針對 macOS 裝置遠端發出「清除」命令。

> [!IMPORTANT]
> 清除命令無法回復，應該謹慎使用。

清除命令會從裝置移除所有資料，包括作業系統。 這樣做也會從 Intune 管理移除裝置。 系統不會向使用者發出任何警告，且將在發出命令之際，立即開始清除。

您必須設定 6 位數的復原 PIN。 此 PIN 可用來將已清除的裝置解除鎖定，並開始重新安裝作業系統。 開始進行清除後，PIN 會出現在 Intune 中裝置 [概觀] 刀鋒視窗的狀態列上。 在清除進行期間，PIN 會持續顯示。 完成清除後，裝置會完全從 Intune 管理中消失。 請務必記錄復原 PIN，以供還原裝置的人員來使用。

#### <a name="revoke-licenses-for-an-ios-volume-purchasing-program-token----820870---"></a>撤銷 iOS 大量採購方案權杖的授權 <!-- 820870 -->
您可針對指定的 VPP 權杖，撤銷所有 iOS Volume Purchasing Program (VPP) 應用程式的授權。

### <a name="app-management"></a>應用程式管理

#### <a name="revoking-ios-volume-purchase-program-apps-----820863---"></a>撤銷 iOS 大量採購方案應用程式 <!-- 820863 -->
對於具有一或多個 iOS Volume Purchasing Program (VPP) 應用程式的指定裝置，您可將裝置撤銷與其建立關聯的裝置應用程式授權。 撤銷應用程式授權將不會從該裝置解除安裝相關聯的 VPP 應用程式。 若要解除安裝 VPP 應用程式，您必須將指派動作變更為 [解除安裝]。 如需詳細資訊，請參閱[如何使用 Microsoft Intune 管理透過大量採購方案購買的 iOS 應用程式](vpp-apps-ios.md)。

#### <a name="assign-office-365-mobile-apps-to-ios-and-android-devices-using-built-in-app-type----1332318---"></a>將 Office 365 行動應用程式指派給使用內建應用程式類型的 iOS 和 Android 裝置 <!-- 1332318 -->
**內建**應用程式類型讓您可更輕鬆地建立 Office 365 應用程式，並將其指派給您管理的 iOS 及 Android 裝置。 這些應用程式包括 0365 應用程式，例如 Word、Excel、PowerPoint 和 OneDrive。 您可以將特定的應用程式指派給應用程式類型，並編輯應用程式資訊設定。

#### <a name="including-and-excluding-app-assignment-based-on-groups----1406920---"></a>依據群組來包含和排除應用程式指派 <!-- 1406920 -->

在應用程式指派期間和選取指派類型後，您可選取要包含的群組及要排除的群組。

### <a name="device-configuration"></a>裝置設定

#### <a name="you-can-assign-an-application-configuration-policy-to-groups-by-including-and-excluding-assignments-----1480316---"></a>您可包含和排除指派，將應用程式設定原則指派給群組  <!-- 1480316 -->

您可使用包含和排除指派的組合，將應用程式設定原則指派給一群使用者和裝置。 您可選擇自選群組或虛擬群組作為指派。 虛擬群組可以包括 [所有使用者]、[所有裝置] 或 [所有使用者及所有裝置]。

#### <a name="support-for-windows-10-edition-upgrade-policy------903672archived-1119689---"></a>支援 Windows 10 版本升級原則 <!-- 903672(archived), 1119689 -->  
您可以建立 Windows 10 版本升級原則，以將 Windows 10 裝置升級至 Windows 10 教育版、Windows 10 教育版 N、Windows 10 專業版、Windows 10 專業版 N、Windows 10 專業教育版和 Windows 10 專業教育版 N。如需 Windows 10 版本升級的詳細資料，請參閱[如何設定 Windows 10 版本升級](edition-upgrade-configure-windows-10.md)。

#### <a name="conditional-access-policies-for-intune-is-only-available-from-the-azure-portal-----1737088-1634311---"></a>Intune 的條件式存取原則只能從 Azure 入口網站使用 <!-- 1737088 1634311 -->

自此版開始，您必須在 [Azure 入口網站](https://portal.azure.com)的 **Azure Active Directory** > **條件式存取**中設定及管理您的條件式存取原則。 為了方便起見，您也可以在 [Intune] > [條件式存取]，從 Azure 入口網站的 Intune 存取此刀鋒視窗。

#### <a name="updates-to-compliance-emails---1637547---"></a>更新合規性電子郵件 <!--1637547 -->

當傳送電子郵件回報不相容的裝置時，電子郵件會包含不相容之裝置的詳細資料。


## <a name="week-of-january-22-2018"></a>2018 年 1 月 22 日當週

### <a name="intune-apps"></a>Intune 應用程式

#### <a name="new-functionality-for-the-resolve-action-for-android-devices---1583480--"></a>Android 裝置之「解決」動作的新功能 <!--1583480-->

Android 版公司入口網站應用程式正在擴充 [更新裝置設定] 的「解決」動作，以解決[裝置加密問題](/intune-user-help/encrypt-your-device-android)。

#### <a name="remote-lock-available-in-company-portal-app-for-windows-10---676506--"></a>Windows 10 的公司入口網站應用程式提供遠端鎖定 <!--676506-->
使用者現在可以從 Windows 10 的公司入口網站應用程式遠端鎖定其裝置。 這不會顯示在他們正使用的本機裝置上。

#### <a name="easier-resolution-of-compliance-issues-for-the-company-portal-app-for-windows-10---676546--"></a>針對 Windows 10 公司入口網站應用程式，可以更容易解決合規性問題 <!--676546-->
使用 Windows 裝置的終端使用者將可在公司入口網站應用程式中點選不相容的原因。 如此一來，系統會盡可能將使用者直接移至設定應用程式的正確位置，以修正問題。

## <a name="week-of-december-11-2017"></a>2017 年 12 月 11 日當週

### <a name="device-configuration"></a>裝置設定

#### <a name="new-automatic-redeployment-setting----1469168---"></a>新的自動重新部署設定 <!-- 1469168 -->
**自動重新部署**設定允許具有系統管理權限的使用者，在裝置鎖定畫面上使用 **CTRL + Win + R** 來刪除所有使用者資料和設定。 裝置會自動重新設定並重新註冊以納入管理。 您可以在 [Windows 10] > [裝置限制] > [一般] > [自動重新部署] 下找到此設定。 如需詳細資料，請參閱 [Windows 10 的 Intune 裝置限制設定](device-restrictions-windows-10.md#general)。

#### <a name="support-for-additional-source-editions-in-the-windows-10-edition-upgrade-policy-----903672--1119689---"></a>支援 Windows 10 版本升級原則中的其他來源版本  <!-- 903672,  1119689 -->
您現在可以使用 Windows 10 版本升級原則，從其他 Windows 10 版本 (Windows 10 專業版、Windows 10 專業教育版、Windows 10 Cloud 等) 進行升級。 在此版本之前，支援的版本升級路徑十分有限。 如需詳細資訊，請參閱[如何設定 Windows 10 版本升級](edition-upgrade-configure-windows-10.md)。

#### <a name="new-windows-defender-security-center-wdsc-device-configuration-profile-settings----1335507---"></a>新的 Windows Defender 資訊安全中心 (WDSC) 裝置組態設定檔設定 <!-- 1335507 -->

Intune 在 [端點保護] 下新增了新的裝置組態設定檔設定區段，名為 [Windows Defender 資訊安全中心]。 IT 系統管理員可以設定終端使用者可存取的 Windows Defender 資訊安全中心應用程式方針。 如果 IT 系統管理員在 Windows Defender 資訊安全中心應用程式中隱藏某個方針，則與該隱藏方針相關聯的所有通知都不會顯示在使用者的裝置上。

以下是系統管理員可從 Windows Defender 資訊安全中心裝置組態設定檔設定中隱藏的方針：
- 病毒與威脅防護
- 裝置效能與健康情況
- 防火牆與網路保護
- 應用程式與瀏覽器控制
- 家長監護選項

IT 系統管理員也可以自訂使用者可接收的通知。 例如，您可以設定是否讓使用者接收由 WDSC 中可見方針所產生的所有通知，或僅接收重要通知。 非重大通知包括 Windows Defender 防毒軟體活動的定期摘要，以及掃描完成時的通知。 所有其他通知都被視為重大通知。 此外，您也可以自訂通知內容本身，例如，您可以在顯示於使用者裝置上的通知中內嵌 IT 連絡資訊。

#### <a name="multiple-connector-support-for-scep-and-pfx-certificate-handling----1361755---"></a>針對 SCEP 和 PFX 憑證處理的多連接器支援 <!-- 1361755 -->

使用內部部署 NDES 連接器將憑證傳遞至裝置的客戶，現在可在單一租用戶上設定多個連接器。

此新功能支援下列案例：

- **高可用性**

每個 NDES 連接器都會從 Intune 提取憑證要求。  如果有某個 NDES 連接器離線，其他連接器將可以繼續處理要求。

#### <a name="customer-subject-name-can-use-aaddeviceid-variable-----1468599---"></a>客戶主體名稱可以使用 AAD_DEVICE_ID 變數  <!-- 1468599 -->

當您在 Intune 中建立 SCEP 憑證設定檔時，現在可在建置自訂的主體名稱時使用 AAD_DEVICE_ID 變數。   當使用此 SCEP 設定檔要求憑證時，該變數會以要求憑證之裝置的 AAD 裝置識別碼來取代。


### <a name="device-management"></a>裝置管理

#### <a name="manage-jamf-enrolled-macos-devices-with-intunes-device-compliance-engine----1592747---"></a>使用 Intune 的裝置合規性引擎管理 Jamf 註冊的 macOS 裝置 <!-- 1592747 -->
您現在可以使用 Jamf 將 macOS 裝置狀態資訊傳送到 Intune，然後 Intune 會評估裝置是否符合 Intune 主控台中定義的合規性原則。 根據裝置合規性狀態以及其他條件 (例如位置、使用者風險等)，條件式存取將會針對存取雲端的 macOS 裝置和與 Azure AD 連線之內部部署應用程式 (包括 Office 365) 強制執行合規性檢查。 深入了解[設定 Jamf 整合](conditional-access-integrate-jamf.md)與[強制執行 Jamf 受控裝置的合規性](conditional-access-assign-jamf.md)。

#### <a name="new-ios-device-action------1424701---"></a>新的 iOS 裝置動作 <!-- 1424701 -->

您現在可以關閉 iOS 10.3 受監督的裝置。 這個動作會立即關閉裝置，而不會警告使用者。 您可以在 [裝置] 工作負載中選取裝置時，於裝置屬性中找到 [關機 (僅限受監督)] 動作。

#### <a name="disallow-datetime-changes-to-samsung-knox-devices----1468103---"></a>不允許 Samsung Knox 裝置的日期/時間變更 <!-- 1468103 -->

我們已加入新的功能，可讓您封鎖 Samsung Knox 裝置上的日期與時間變更。 您可以在 [裝置組態設定檔] > [裝置限制 (Android)] > [一般] 中找到此功能。

#### <a name="surface-hub-resource-account-supported----1566442----"></a>支援 Surface Hub 資源帳戶 <!-- 1566442  -->

已加入新的裝置動作，以便系統管理員對與 Surface Hub 相關聯的資源帳戶進行定義及更新。

Surface Hub 會使用資源帳戶向 Skype/Exchange 進行驗證以加入會議。 您可以建立唯一的資源帳戶，使 Surface Hub 在會議中顯示為會議室。 例如，資源帳戶可能會顯示為*會議室 B41/6233*。 Surface Hub 的資源帳戶 (也稱為裝置帳戶) 通常需要針對會議室位置，以及在其他資源帳戶參數需要被變更時進行設定。

當系統管理員想要更新裝置上的資源帳戶時，他們必須提供目前與裝置相關聯的 Active Directory/Azure Active Directory 認證。 如果裝置有開啟密碼輪換，則系統管理員必須移至 Azure Active Directory 以找出密碼。

> [!NOTE]
> 所有的欄位會以組合方式向下傳送，並覆寫先前設定的所有欄位。 空白欄位也會覆寫現有欄位。

以下是系統管理員可以設定的設定：

- **資源帳戶**
   - **Active Directory 使用者**

      Domainname\username 或使用者主體名稱 (UPN)：user@domainname.com

   - **密碼**

- **選擇性資源帳戶參數** (必須使用指定的資源帳戶進行設定)

   - **密碼輪換期間**

     確保帳戶密碼每週會由 Surface Hub 基於安全性考量進行自動更新。 若要在啟用此設定後設定任何參數，必須先將 Azure Active Directory 中的帳戶進行密碼重設。

   - **SIP (工作階段初始通訊協定) 位址**

     只有在自動探索失敗時才會使用。

   - **電子郵件**

     裝置/資源帳戶的電子郵件地址。

   - **Exchange 伺服器**

     只有自動探索失敗時才需要。

   - **行事曆同步處理**

     指定是否啟用行事曆同步處理和其他 Exchange 伺服器服務。 例如：會議同步處理。

#### <a name="install-office-apps-on-macos-devices----1494311---"></a>在 macOS 裝置上安裝 Office 應用程式 <!-- 1494311 -->
您現在可在 macOS 裝置上安裝 Office 應用程式。 這個新的應用程式類型可讓您安裝 Word、Excel、PowerPoint、Outlook 及 OneNote。 這些應用程式也會隨附於 Microsoft AutoUpdate (MAU)，以協助保護您的應用程式並使它保持在最新狀態。

### <a name="app-management"></a>應用程式管理

#### <a name="delete-an-ios--volume-purchasing-program-token----820879---"></a>刪除 iOS 大量採購方案權杖 <!-- 820879 -->
您可以使用主控台來刪除 iOS 大量採購方案 (VPP) 權杖。 當您擁有重複的 VPP 權杖執行個體時，這可能是必要的。

### <a name="intune-apps"></a>Intune 應用程式


### <a name="role-based-access-control"></a>以角色為基礎的存取控制

#### <a name="a-new-entity-collection-named-current-user-is-limited-to-currently-active-user-data----1667026---"></a>名為 Current User 的新實體集合限於目前作用中的使用者資料 <!-- 1667026 -->

**User** 實體集合包含企業中具有所指派授權的所有 Azure Active Directory (Azure AD) 使用者。 例如，某個使用者可能在上個月內被新增到 Intune 然後又被移除。 雖然在報告的時候這個使用者不會出現，但使用者和狀態會出現在資料中。 您可以建立一個報告，其中顯示使用者的歷程記錄在您資料中出現的期間。

相較之下，新的 **Current User** 實體集合只包含尚未被移除的使用者。 **Current User** 實體集合只包含目前作用中的使用者。 如需 **Current User** 實體的詳細資訊，請參閱 [Current User 實體的參考](reports-ref-current-user.md)。


### <a name="updated-graph-apis----1736360---"></a>更新的 Graph API <!-- 1736360 -->

在此版本中，我們已更新一些 Intune 的搶鮮版 (Beta) Graph API。 如需詳細資訊，請查看每月 [Graph API 變更記錄](https://developer.microsoft.com/graph/docs/concepts/changelog) \(英文\)。

## <a name="week-of-december-4-2017"></a>2017 年 12 月 4 日當週

### <a name="monitor-and-troubleshoot"></a>監視及疑難排解

#### <a name="intune-supports-windows-information-protection-wip-denied-apps----1479103---"></a>Intune 支援 Windows 資訊保護 (WIP) 拒絕應用程式 <!-- 1479103 -->
您可以在 Intune 中指定拒絕的應用程式。 如果應用程式遭到拒絕，它會被封鎖而無法存取公司資訊，效果與允許的應用程式清單相反。 如需詳細資訊，請參閱 [Recommended deny list for Windows Information Protection](https://docs.microsoft.com/windows/client-management/mdm/applocker-csp?f=255&MSPPError=-2147217396#recommended-deny-list-for-windows-information-protection) (Windows 資訊保護的建議拒絕清單)。



## <a name="notices"></a>通知

### <a name="plan-for-change-change-password-at-next-auth-added-to-intune---1873216---"></a>規劃變更：Intune 已新增 [Change Password at Next Auth] \(在下次驗證時變更密碼\) <!-- 1873216 -->
在 9 月服務版本中，Intune 想要針對執行 macOS 10.13 版和更新版本的裝置整合 Apple 的新發行 [Change Password at Next Auth] \(在下次驗證時變更密碼\) 設定。 在此設定之前，MDM 提供者無法驗證裝置密碼是否已變更為符合規範。 Intune 的設定和合規性原則只會驗證下次變更裝置密碼時，會將裝置密碼標示為符合規範。 新增這個新的 Apple 功能時，您的 macOS 使用者將會收到更新密碼的要求，即使他們的密碼符合規範也是一樣。

#### <a name="how-does-this-affect-me"></a>此變更對我造成什麼影響？
這會影響具有使用 Intune 或混合式 MDM 之 macOS 裝置原則的環境。 現在，Apple 已有這個 [Change Password at Next Auth] \(在下次驗證時變更密碼\) 設定，Intune 即可強制使用者在推入密碼原則時更新其密碼。 如果您在將裝置標示為符合規範之前封鎖公司資源，則可能會封鎖您的終端使用者，使其在重設其密碼之前都無法存取公司資源 (例如電子郵件或 SharePoint 網站)。 在未來，對設定和合規性密碼原則的所有更新都會強制目標使用者更新其密碼。

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>我需要為這項變更做什麼準備？
讓您的技術服務人員知道。 如果您不想要強制執行此 macOS 裝置原則，建議您取消指派或刪除現有的 macOS 原則。 客戶研究建議大部分客戶不會受到這項變更的影響。 大部分的終端使用者都會在收到使用者密碼註冊的要求之後更新其密碼，或重設其密碼以符合規範。


### <a name="plan-for-change-intune-moving-to-support-ios-10-and-later-in-september----2454656---"></a>為變更做計劃 ：Intune 將於 9 月開始支援 iOS 10 和更新版本 <!-- 2454656 -->
預期 Apple 將在 9 月發行 iOS 12。 在此版本發行之後不久，我們將使 Intune 註冊、公司入口網站及受控瀏覽器可支援 iOS 10 和更新版本。  

#### <a name="how-does-this-affect-me"></a>此變更對我造成什麼影響？  
iOS 10 和更新版本上支援 Office 365 行動應用程式，因此您可能已經升級您的 OS 或裝置。 如果是，這將不會對您造成任何影響。  

不過，如果您有下面列出的任何裝置，或想要註冊下面列出的任何裝置，請注意，它們只支援 iOS 9 和更早版本。  若要繼續存取 Intune 公司入口網站，您必須在 9 月之前將這些裝置升級為支援 iOS 10 或更新版本的裝置：  

* iPhone 4S  
* iPod Touch  
* iPad 2  
* iPad (第 3 代)  
* iPad Mini (第 1 代)  

從 7 月開始，使用 iOS 9 和公司入口網站註冊 MDM 的裝置將收到升級其 OS 或裝置的提示。 如果您使用應用程式保護原則，也可以設定 [需要 iOS 作業系統的最低版本 (僅警告)] 存取設定。  

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>我需要為這項變更做什麼準備？   
檢查組織中受到影響的裝置或使用者。 在 Intune Azure 入口網站中，移至 [裝置] > [所有裝置]，然後依 [OS] 進行篩選。  按一下 [欄] 以呈現例如 OS 版本的詳細資料。 要求使用者在 9 月之前將他們的裝置升級至支援的 OS 版本。  

### <a name="plan-for-change-intune-moving-to-tls-12"></a>規劃變更：Intune 移至 TLS 1.2
從 2018 年 10 月 31 日開始，Intune 將會支援傳輸層安全性 (TLS) 通訊協定 1.2 版，以提供最佳的加密、確保我們的服務預設更安全，並符合 Microsoft Office 365 等其他 Microsoft 服務。 Office 已在 MC128929 中傳達此變更。

#### <a name="how-does-this-affect-me"></a>此變更對我造成什麼影響？
自 2018 年 10 月 31 日起，Intune 將不再支援 TLS 通訊協定 1.0 或 1.1 版。 所有的用戶端/伺服器和瀏覽器/伺服器組合都應該使用 TLS 1.2 版，以確保與 Intune 的連線沒有問題。 請注意，此變更會影響 Intune 不再支援但仍會透過 Intune 接收原則，以及無法使用 TLS 1.2 版的終端使用者裝置。 這包括執行 Android 4.3 和舊版的裝置。 如需受影響的裝置和瀏覽器清單，請參閱下面的＜其他資訊＞。

2018 年 10 月 31 日之後，如果您發生與使用舊版 TLS 相關的問題，則必須更新為 TLS 1.2 或支援 TLS 1.2 的裝置來解決。

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>我需要為這項變更做什麼準備？
建議您主動移除環境中的 TLS 1.0 和 1.1 相依性，並盡可能在作業系統層級停用 TLS 1.0 和 1.1。 請立即開始規劃移轉至 TLS 1.2。 請查看下面的支援部落格文章，以取得 Intune 目前不支援但可能仍會接收原則，以及無法使用 TLS 1.2 版通訊的裝置清單。 您可能需要通知這些終端使用者，他們即將失去對公司資源的存取權。

**其他資訊**：[Intune moving to TLS 1.2 for encryption](https://blogs.technet.microsoft.com/intunesupport/2018/06/05/intune-moving-to-tls-1-2-for-encryption/) (Intune 移至 TLS 1.2 進行加密)

### <a name="plan-for-change-new-windows-10-setting-for-kiosk-configuration-in-intune----1560072---"></a>為變更做規劃：適用於 Intune 中 Kiosk 設定的新 Windows 10 設定 <!-- 1560072 -->
我們正在變更您在 Intune Azure 入口網站中設定 Windows 10 1709 和更新版本 (RS3 和更新版本) 桌面的方式和位置。

#### <a name="how-does-this-affect-me"></a>此變更對我造成什麼影響？ 
我們的記錄指出您目前使用 [Windows 10] > [裝置限制] > [Kiosk (預覽)] 設定。 這會在五月於 UI 中重新命名為 [Windows 10] > [裝置限制] > [Kiosk (已過時)]，用來指出已不再建議使用。 不過，它仍將持續運作，直到七月的 Intune 更新為止。 接著，就會在後端將其設定為已過時，且將無法再運作。 我們將在五月發行新的裝置組態設定檔來作為替代方案：[Windows 10] > [Kiosk]，其中包含可設定 Windows 10 RS4 和更新版本上 Kiosk 的設定。

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>我需要為這項變更做什麼準備？  
當 Intune 在大約五月底發行五月服務更新時，我們將會提供指示，供您測試及驗證是否能夠將您的 Kiosk 設定從 Windows 10 RS3 移轉至 Windows 10 RS4。 請參考這些指示，使用新的 Kiosk 裝置組態設定檔將您的裝置設定成 Kiosk。

#### <a name="how-does-this-affect-me"></a>此變更對我造成什麼影響？
這項變更會影響 Intune 獨立客戶和混合式 (含 Configuration Manager 的 Intune) 客戶。 這項整合有助於簡化雲端管理系統管理。 現在，Azure 中只會有一個刀鋒視窗 (Intune 刀鋒視窗) 來管理群組、原則、應用程式和任何行動裝置管理。

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>我需要為這項變更做什麼準備？
請將 Intune 標記為我的最愛，而不是 [Intune 應用程式防護] 服務刀鋒視窗，並確定您熟悉 Intune 的 [行動應用程式] 刀鋒視窗中的應用程式保護原則工作流程。 我們會短時間內重新導向，然後移除 [應用程式保護] 刀鋒視窗。 請記住，所有應用程式保護原則都已在 Intune 中，而且您可以遵循這裡的文件來修改任何條件式存取原則：[https://aka.ms/azuread_ca](https://aka.ms/azuread_ca)。

**其他資訊**：[https://aka.ms/intuneapppolicy](https://aka.ms/intuneapppolicy)

### <a name="plan-for-change-change-in-support-for-the-microsoft-intune-app-sdk-for-cordova-plugin"></a>變更計劃：變更適用於 Cordova 外掛程式的 Microsoft Intune App SDK 支援
Intune 即將在 2018 年 5 月 1 日結束 [Microsoft Intune App SDK Cordova 外掛程式](app-sdk-cordova.md)的支援。 建議您改用 Intune App Wrapping Tool，以讓您的 Cordova 應用程式可在 Intune 中管理及運作。 當此變更生效時，適用於 Cordova 外掛程式的 Microsoft Intune APP SDK 將不再保留或接收更新。 應用程式開發人員將無法使用此外掛程式。 Intune 計劃繼續支援以 Cordova 建置的應用程式。 但是，以適用於 Cordova 外掛程式之 Microsoft Intune APP SDK 建置的任何應用程式在 Intune 中的功能會減少。 使用 Intune App Wrapping Tool 包裝後，應用程式就能以其一般狀態部署至終端使用者。 對於發行至 Google Play 商店之 Cordova 的 Android 應用程式：
- 使用者第一次啟動時，系統將提示其認證，以接收 Intune 原則。
- 應用程式應發行至以 Intune 使用者為目標的應用程式市集，如「適用於 Intune 的 Contoso 應用程式」。

如需了解 App Wrapping Tool 的詳細資訊，請參閱[適用於 iOS 的 App Wrapping Tool](app-wrapper-prepare-ios.md) 和[適用於 Android 的 App Wrapping Tool](app-wrapper-prepare-android.md)。 如有任何問題或疑問，請連絡 [msintuneappsdk@microsoft.com](mailto:msintuneappsdk@microsoft.com)。

### <a name="plan-for-change-use-intune-on-azure-now-for-your-mdm-management----1227338---"></a>規劃變更：立即在 Azure 上使用 Intune 進行 MDM 管理 <!-- 1227338 -->
一年多前，我們公佈了 [Azure 上的 Intune 公開預覽版 ](https://cloudblogs.microsoft.com/enterprisemobility/2016/12/07/public-preview-of-intune-on-azure/)，六個月前追加了 Intune 的[新管理員體驗正式運作](https://cloudblogs.microsoft.com/enterprisemobility/2017/06/08/the-new-intune-and-conditional-access-admin-consoles-are-ga/)。 自 2018 年 8 月 31 日起，使用 Intune 獨立版的客戶將無法繼續在傳統 Silverlight 主控台中使用行動裝置管理 (MDM)。 但您可以使用 [Azure 上的 Intune](https://aka.ms/Intune_on_Azure) 處理 MDM 需求。 如果仍在使用 MDM 的傳統主控台，請停止使用並熟悉 Azure 上的 Intune。 我們不希望這項變更影響任何使用者。 Silverlight 仍提供傳統的電腦管理。 您可以在[這裡](https://aka.ms/Intune_on_Azure_mdm)深入了解這項變更，以及它對您的影響。

### <a name="direct-access-to-apple-enrollment-scenarios---951869--"></a>直接存取 Apple 註冊案例 <!--951869-->
對於在 2017 年 1 月之後建立的 Intune 帳戶，Intune 已經啟用使用 Azure 入口網站中的「註冊裝置」工作負載直接存取 Apple 註冊案例。 Apple 註冊預覽原本只能從 Intune 傳統入口網站中的連結存取。 在 2017 年 1 月之前建立的 Intune 帳戶需要進行一次性移轉，才能在 Azure 中使用這些功能。 移轉的排程尚未宣布，但將會盡快提供詳細資料。 如果您現有的帳戶無法存取 Azure 入口網站，則強烈建議建立試用帳戶來測試新的體驗。

## <a name="whats-coming"></a>未來動態

### <a name="local-device-security-option-settings----1251887---"></a>本機裝置安全性選項設定 <!-- 1251887 -->
您將能夠使用新的 [本機裝置安全性選項] 設定，在 Windows 10 裝置上啟用安全性設定。 當您建立 Windows 10 裝置設定原則時，在 [Endpoint Protection] 類別中找到這些設定。

### <a name="new-user-experience-update-for-the-company-portal-website---2000968--"></a>公司入口網站的新使用者體驗更新 <!--2000968-->

我們將在八月開始引進新的公司入口網站體驗，以及 UI 更新、簡化的工作流程和協助工具改善。 這將包含客戶驅動的增強功能，例如應用程式共用和改善的整體效能，讓您擁有更方便使用的體驗。
我們已根據客戶的意見反應來新增一些新功能，這將大幅改善現有功能和可用性：

* 整個網站的 UI 改進
* 可以共用應用程式的直接連結
* 改善大型應用程式目錄的效能

您不需要為此變更進行任何準備動作。 我們會讓您知道更新過的公司入口網站何時可供使用。 不過，您最終可能需要使用更新過的螢幕擷取畫面來更新使用者文件。 請注意，您也可能需要更新 iOS 上公司入口網站應用程式的文件，因為網站具有 iOS 應用程式的 [應用程式] 區段。 您可以在[應用程式 UI 中的新功能](whats-new-app-ui.md)頁面上查看此動作的範例影像。

### <a name="apple-to-require-updates-for-application-transport-security---748318--"></a>Apple 要求必須更新 Application Transport Security <!--748318-->
Apple 宣布將會強制執行 Application Transport Security (ATS) 的特定需求。 ATS 可用來對透過 HTTPS 進行的所有應用程式通訊，強制執行更嚴格的安全性。 此變更會影響使用 iOS 公司入口網站應用程式的 Intune 客戶。 我們會在 [Intune 支援部落格](https://aka.ms/compportalats)上持續提供詳細資料。



## <a name="see-also"></a>另請參閱
* [Microsoft Intune 部落格](http://go.microsoft.com/fwlink/?LinkID=273882)
* [雲端平台藍圖](https://www.microsoft.com/cloud-platform/roadmap)
* [公司入口網站 UI 中的新增功能](whats-new-app-ui.md)
* [前幾個月的新功能](whats-new-archive.md)

---
title: "Microsoft Intune 的新功能"
titleSuffix: Intune on Azure
description: "了解 Intune Azure 入口網站中的新功能"
keywords: 
author: brenduns
ms.author: brenduns
manager: angrobe
ms.date: 08/10/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 791ed23f-bd13-4ef0-a3dd-cd2d7332c5cc
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: f915c805b20e88c661ad52e280a31054bbebce02
ms.sourcegitcommit: 2ed8d1c39d4b3e3282111f1d758afb3a50f19f8f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/10/2017
---
# <a name="whats-new-in-microsoft-intune"></a>Microsoft Intune 的新功能

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

了解每週的 Microsoft Intune 新功能 您也可以了解[即將推出的變更](#whats-coming)、關於服務的[重要通知](#notices)，以及[過去版本](whats-new-archive.md)的相關資訊。

> [!Note]
> 具備 Configuration Manager 的混合式部署於未來將會支援多數的這些功能。 如需新混合式功能的詳細資訊，請查看我們的[混合式新增功能](/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management)頁面。


<!-- Common categories:  
  ### Role-based access control
  ### Device enrollment
  ### Device management
  ### App management
  ### Device configuration
  ### Intune apps
-->   

## <a name="week-of-july-31-2017"></a>2017 年 7 月 31 日一週

### <a name="device-enrollment"></a>裝置註冊  

#### <a name="restrict-android-and-ios-device-enrollment-restriction-by-os-version------1333256--1245463----"></a>依作業系統版本限制 Android 和 iOS 裝置註冊限制 <!--- 1333256,  1245463 --->
Intune 現在支援依作業系統版本號碼限制 iOS 和 Android 註冊。 在 [裝置類型限制] 下，IT 系統管理員現在可以進行平台設定，以便將註冊限制於作業系統值上下限之間。 Android 作業系統版本必須指定為 Major.Minor.Build.Rev，其中 Minor、Build 和 Rev 為選擇性。 iOS 版本必須指定為 Major.Minor.Build，其中 Minor 和 Build 為選擇性。 深入了解[裝置註冊限制](enrollment-restrictions-set.md)。

>[!NOTE]
>請勿將註冊限制為透過 Apple 註冊計劃或 Apple Configurator 進行。

#### <a name="restrict-android-ios-and-macos-device-personally-owned-device-enrollment------1333272--1333275-1245709----"></a>限制 Android、iOS 和 macOS 裝置以個人擁有的裝置註冊<!--- 1333272,  1333275, 1245709 --->
Intune 可以透過將公司裝置 IMEI 編號列入白名單，來限制個人裝置註冊。 Intune 現在已使用裝置序號，將這項功能擴充到 iOS、Android 和 macOS。 將序號上傳至 Intune，您就可以預先宣告此為公司擁有的裝置。 使用註冊限制，您可以封鎖個人擁有 (BYOD) 的裝置，僅註冊公司擁有的裝置。 深入了解[裝置註冊限制](enrollment-restrictions-set.md)。

若要匯入序號，請移至 [裝置註冊] > [公司裝置識別碼] 並按一下 [新增]，然後上傳 .CSV 檔案 (不含標頭的兩個序號和 IMEI 編號等詳細資料欄位)。  若要限制個人擁有的裝置，請移至 [裝置註冊]  >  [註冊限制]。 在 [裝置類型限制] 下選取 [預設]，然後選取 [平台設定]。 您可以 [允許] 或 [封鎖] 個人擁有的 iOS、Android 和 macOS 裝置。 


### <a name="device-management"></a>裝置管理   

#### <a name="new-device-action-to-force-devices-to-sync-with-intune----711369---"></a>新的裝置動作會強制裝置與 Intune 同步處理<!-- 711369 -->
在此版本中，我們已新增裝置動作，強制所選裝置立即使用 Intune 簽入。 當裝置簽入時，會立即收到所有擱置動作或已指派給它的原則。  這個動作可協助您立即驗證和針對您已指派的原則進行疑難排解，不用等到下次排程的簽入。
如需詳細資料，請參閱[同步處理裝置](device-sync.md)

#### <a name="force-supervised-ios-devices-to-automatically-install-the-latest-available-software-update----777100---"></a>強制受監督的 iOS 裝置自動安裝最新可用的軟體更新<!-- 777100 -->
新的原則可從 [軟體更新] 工作區取得，您可在此強制受監督的 iOS 裝置自動安裝最新可用的軟體更新。 如需詳細資料，請參閱[設定 iOS 更新原則](/intune/software-updates-ios)


#### <a name="check-point-sandblast-mobile---new-mobile-threat-defense-partner-----954651-1172027---"></a>Check Point SandBlast Mobile - 新的 Mobile Threat Defense 夥伴<!-- 954651, 1172027 -->
您可以根據由 Checkpoint SandBlast Mobile (一個與 Microsoft Intune 整合的 Mobile Threat Defense 解決方案) 所進行的風險評估，使用條件式存取來控制行動裝置對公司資源的存取。

##### <a name="how-integration-with-intune-works"></a>整合 Intune 如何運作？
風險乃依據收集自執行 Checkpoint SandBlast Mobile 裝置的遙測來進行評估。 您可以根據透過 Intune 裝置合規性政策所啟用的 Checkpoint SandBlast Mobile 風險評估，來設定 EMS 條件式存取原則。 您可以根據偵測到的威脅，允許或封鎖不符合規範的裝置存取公司資源。


### <a name="app-management"></a>應用程式管理

#### <a name="deploy-an-app-as-available-in-the-microsoft-store-for-business----748101---"></a>將應用程式部署為商務用 Microsoft 網上商店中的可用項目 <!-- 748101 -->
系統管理員現在可以使用此版本將商務用 Microsoft 網上商店指派為可用。 設定為可用時，終端使用者就可以從公司入口網站應用程式或網站安裝應用程式，而不會被重新導向至 Microsoft 網上商店。


### <a name="intune-apps"></a>Intune 應用程式  

#### <a name="ui-updates-to-the-company-portal-website---1313244-part-1--"></a>公司入口網站的 UI 更新 <!--1313244 part 1-->
我們對[公司入口網站](https://portal.manage.microsoft.com)的 UI 進行了數項更新，以增強終端使用者體驗。

- __應用程式磚的增強功能__：應用程式圖示現在會根據圖示的主要色彩 (如果可偵測)來顯示自動產生的背景。 適用時，此背景會取代先前在應用程式磚上顯示的灰色框線。

    公司入口網站會在未來版本中盡可能顯示大圖示。 建議 IT 系統管理員使用大小下限為 120 x120 像素的高解析度圖示來發佈應用程式。 

- __導覽變更__：導覽列項目移至左上方的漢堡功能表。 移除 [類別] 頁面。 使用者現在可以在瀏覽時依類別篩選內容。

- __精選 App 的更新__：我們已將專用頁面新增至網站 (使用者可在其中瀏覽您選為精選的應用程式)，並對首頁上的 [精選] 區段進行一些 UI 調校。

#### <a name="ibooks-support-for-the-company-portal-website---1231841--"></a>公司入口網站的 iBooks 支援 <!--1231841-->
我們已將專用頁面新增至公司入口網站，讓使用者可以瀏覽並下載 iBooks。 

### <a name="reporting"></a>報告

#### <a name="intune-data-warehouse-public-preview"></a>Intune 資料倉儲 (公開預覽)

Intune 資料倉儲會每日對資料進行抽樣，以提供您租用戶的歷程檢視。 您可以藉由使用 Power BI 檔案 (PBIX)、與許多分析工具相容的 OData 連結，或與 REST API 互動，來存取資料。 如需詳細資訊，請參閱[使用 Intune 資料倉儲](reports-nav-create-intune-reports.md)。


## <a name="week-of-july-23rd-2017"></a>2017 年 7 月 23 日一週

### <a name="light-and-dark-modes-available-for-the-company-portal-app-for-windows-10----676547---"></a>Windows 10 的公司入口網站應用程式提供日間和夜間模式<!---676547--->
使用者可以自訂 Windows 10 公司入口網站應用程式的色彩模式。 使用者可在公司入口網站應用程式的 [設定] 區段中進行變更。 使用者重新啟動應用程式後，即會看到變更。 至於 Windows 10 版本 1607 及更新版本，應用程式模式會預設為系統設定。 至於 Windows 10 版本 1511 及更新版本，應用程式模式會預設為日間模式。

### <a name="enable-end-users-to-tag-their-device-group-in-the-company-portal-app-for-windows-10----807046--"></a>讓使用者在 Windows 10 的公司入口網站應用程式中標記其裝置群組<!---807046-->
終端使用者現在可以直接在 Windows 10 公司入口網站應用程式中標記群組，選取其裝置所屬群組。




## <a name="notices"></a>通知

### <a name="ip-addresses-for-intune-updated----1175274---"></a>Intune 的 IP 位址已更新<!-- 1175274 -->
防火牆 Proxy 設定有[更新的 DNS 名稱和 IP 位址清單](/intune/network-bandwidth-use)。

### <a name="use-azure-active-directory-for-conditional-access----967947---"></a>使用 Azure Active Directory 進行條件式存取<!-- 967947 -->
Azure 主控台的 Azure Active Directory 區段提供條件式存取，在設定 Office 365 Exchange Online 和 SharePoint Online 等雲端應用程式的原則時，可提供更強大而彈性的架構。  使用 [Azure Active Directory] 刀鋒視窗中的 [條件式存取] 來設定原則，取代傳統的 Intune 主控台。 傳統 Intune 主控台中的現有原則，必須在 Azure 主控台中重新建立。 如需詳細資訊，請參閱[建立 Azure AD 條件式存取原則](/intune/conditional-access-exchange-create.md#create-azure-ad-conditional-access-policies-in-intune-azure-preview)。

### <a name="direct-access-to-apple-enrollment-scenarios---951869--"></a>直接存取 Apple 註冊案例 <!--951869-->
對於在 2017 年 1 月之後建立的 Intune 帳戶，Intune 已經啟用使用 Azure 入口網站中的「註冊裝置」工作負載直接存取 Apple 註冊案例。 Apple 註冊預覽原本只能從傳統 Intune 入口網站中的連結存取。 在 2017 年 1 月之前建立的 Intune 帳戶需要進行一次性移轉，才能在 Azure 中使用這些功能。 移轉的排程尚未宣布，但將會盡快提供詳細資料。 如果您現有的帳戶無法存取 Azure 入口網站，我們強烈建議您建立試用帳戶來測試新的體驗。

### <a name="administration-roles-being-replaced-in-azure-portal"></a>Azure 入口網站中將被取代的系統管理角色
在 Intune 傳統入口網站 (Silverlight) 中使用的現有行動應用程式管理 (MAM) 系統管理角色 (參與者、擁有者或唯讀) 在 Intune Azure 入口網站中會被取代為一組新的、完整的角色型系統管理控制 (RBAC)。 當您移轉至 Azure 入口網站之後，必須將系統管理員重新指派至這些新的系統管理角色。 如需 RBAC 和新角色的詳細資訊，請參閱 [Microsoft Intune 的角色型存取控制](/intune/role-based-access-control)。



## <a name="whats-coming"></a>未來動態

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
我們讓您事先知道這項資訊，雖然我們沒有特定的日期，您仍有時間進行規劃。 請確認您的使用者更新為 iOS 9+，且當公司入口網站應用程式發表時，要求您的終端使用者更新其公司入口網站應用程式。

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>我需要為這項變更做什麼準備？
鼓勵您的使用者更新到 iOS 9.0 或更新版本，以便完全利用 Intune 的新功能。  鼓勵使用者安裝新版的公司入口網站，並利用它將提供的新功能。

在 Azure 入口網站移至 Intune，並檢視 [裝置] > [所有裝置]，並依 iOS 版本篩選，查看作業系統早於 iOS 9 的任何目前的裝置。

### <a name="plan-for-change-intune-is-changing-the-intune-partner-portal-experience----1050016---"></a>變更計畫：Intune 正在變更 Intune 合作夥伴入口網站體驗 <!-- 1050016 -->
我們會在 2017 年 5 月中旬的服務更新將 Intune 合作夥伴頁面從 manage.microsoft.com 移除。  

如果您是合作夥伴系統管理員，將無法再從 Intune 合作夥伴頁面代表客戶檢視或採取動作，但會需要登入在 Microsoft 的另外兩個合作夥伴入口網站的其中一個。

[Microsoft 合作夥伴中心](https://partnercenter.microsoft.com/)和 [Microsoft Office 365 合作夥伴系統管理中心](https://portal.office.com/)都能讓您登入所管理客戶的帳戶。 合作夥伴在此後請使用這兩個網站來管理客戶。


### <a name="apple-to-require-updates-for-application-transport-security---748318--"></a>Apple 要求必須更新 Application Transport Security <!--748318-->
Apple 宣布將會強制執行 Application Transport Security (ATS) 的特定需求。 ATS 可用來對透過 HTTPS 進行的所有應用程式通訊，強制執行更嚴格的安全性。 此變更會影響使用 iOS 公司入口網站應用程式的 Intune 客戶。

我們已透過 Apple TestFlight 方案，提供符合新 ATS 需求的 iOS 版公司入口網站應用程式。 如果您想試用該版本以便測試 ATS 合規性，請傳送電子郵件到 <a href="mailto:CompanyPortalBeta@microsoft.com?subject=Register to TestFlight ATS Company Portal app">CompanyPortalBeta@microsoft.com</a>，並附上您的姓氏、名字、電子郵件地址和公司名稱。 如需詳細資訊，請檢閱我們的 [Intune 支援部落格](https://aka.ms/compportalats)。

### <a name="see-also"></a>另請參閱
* [Microsoft Intune 部落格](http://go.microsoft.com/fwlink/?LinkID=273882)
* [雲端平台藍圖](https://www.microsoft.com/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)
* [公司入口網站 UI 中的新增功能](whats-new-app-ui.md)
* [前幾個月的新功能](whats-new-archive.md)

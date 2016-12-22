---
title: "新功能 | Microsoft Intune"
description: "了解本月 Microsoft Intune 版本的新功能，以及過去的版本"
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 12/08/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: fab51ee0-638d-4dd4-8d8f-1f263bc11e5c
ms.reviewer: priyar
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 9fd309a10d9eb020795c5ce46df124b13dc1a006
ms.openlocfilehash: d117c929fbde4dd0a39503b8da695aa9c9ea91ad


---
# <a name="whats-new-in-microsoft-intune---december-2016"></a>Microsoft Intune 的新功能 - 2016 年 12 月
了解此 Microsoft Intune 版本中的新功能。 您也可以了解即將推出且您應該加以規劃的變更，以及過去版本的相關資訊。

> [!Note]
> 混合式客戶部署於未來將會支援這些功能 (具備 Intune 的 Configuration Manager)。 如需新混合式功能的詳細資訊，請查看我們的 [Hybrid What’s New](https://docs.microsoft.com/en-us/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management) (混合式新功能) 頁面。

## <a name="public-preview-of-the-new-intune-admin-experience-on-azure--736542--"></a>Azure 上新 Intune 管理體驗的公開預覽<!--736542-->
在 2017 年初，我們會將完整管理體驗移轉到 Azure，以便在可透過圖形 API 擴充的新式服務平台上，對核心 EMS 工作流程進行強大的整合式管理。 在將此入口網站的正式運作版本提供給所有 Intune 租用戶之前，我們很高興地宣布在本月稍晚將會推出這個新管理體驗的預覽給特定租用戶。

Azure 入口網站中的管理體驗將使用已宣佈的新群組和目標設定功能；當您現有的租用戶移轉至新的群組體驗時，也會同時將您移轉，以預覽您租用戶的新管理體驗。 在此同時，請在我們的[新文件](https://docs.microsoft.com/intune-azure/introduction/what-is-microsoft-intune)中深入了解我們在 Azure 入口網站中針對 Microsoft Intune 做了哪些準備。

如果您有任何關於租用戶移轉時間表的問題，請連絡我們的移轉團隊：[intunegrps@microsoft.com](mailto:intunegrps@microsoft.com)。

### <a name="telecom-expense-management-integration-in-public-preview-of-azure-portal--747605--"></a>Azure 入口網站公開預覽中的電信費用管理整合<!--747605-->
我們現在將開始在 Azure 入口網站中預覽與協力廠商電信費用管理 (Telecom Expense Management，TEM) 服務的整合。 您可以使用 Intune 強制執行限制國內和漫遊資料使用量。 我們將開始與 [Saaswedo](http://www.saaswedo.com) 進行這些整合。

## <a name="new-capabilities"></a>新功能

### <a name="multi-factor-authentication-across-all-platforms---747590--"></a>跨所有平台的 Multi-Factor Authentication <!--747590-->
您現在可以在一組選取的使用者從 Azure 管理入口網站註冊 iOS、Android、Windows 8.1+ 或 Windows Phone 8.1+ 裝置時，對這些使用者強制執行 Multi-Factor Authentication (MFA)，方法是在 Azure Active Directory 中設定 Microsoft Intune 註冊應用程式的相關 MFA。

<!--VSO 679339, awaiting chrisgre for go-live--><!--### Conditional access for MAM with SharePoint Online
您可以禁止不受 Intune 行動應用程式管理 (MAM) 原則支援的應用程式存取 SharePoint Online。  您可以在 Azure 入口網站中使用 Intune 行動應用程式管理開始進行。 在包含 SharePoint Online 選項的 [設定] 刀鋒視窗中，尋找 [條件存取] 區段。 這項功能將與服務版本的其餘部分分開提供。 如需這項新功能的詳細資訊，請參閱[這裡](https://docs.microsoft.com/intune/deploy-use/mam-ca-for-sharepoint-online)。-->

### <a name="ability-to-restrict-mobile-device-enrollment--747596--"></a>限制行動裝置註冊的能力<!--747596-->
Intune 正在新增新的註冊限制，以控制哪些行動裝置平台可以註冊。 Intune 將行動裝置平台分為 iOS、macOS、Android、Windows 和 Windows Mobile。
* 限制行動裝置註冊不會限制電腦用戶端註冊。
* 有一個僅適用於之iOS 的額外選項可封鎖個人擁有的裝置註冊。

Intune 會將所有的新裝置標示為個人，除非 IT 系統管理員採取動作將它們標示為公司擁有，如[本文章](https://docs.microsoft.com/en-us/intune/deploy-use/manage-corporate-owned-devices)所說明。


## <a name="notices"></a>通知

### <a name="multi-factor-authentication-on-enrollment-moving-to-the-azure-portal---vso-750545--"></a>移至 Azure 入口網站的註冊相關 Multi-Factor Authentication <!--VSO 750545-->
之前，系統管理員會移至 Intune 主控台或 Configuration Manager (2016 年 10 月以前的版本) 主控台，以設定用於 Intune 註冊的 MFA。 透過這項更新的功能，您現在將會使用 Intune 認證登入 [Microsoft Azure 入口網站](https://manage.windowsazure.com)，並透過 Azure AD 進行 MFA 設定。 如需詳細資訊，請參閱[這裡](https://aka.ms/mfa_ad)。

### <a name="company-portal-app-for-android-now-available-in-china---vso-658093--"></a>中國現在提供適用於 Android 的公司入口網站應用程式 <!--VSO 658093-->
我們將在中國發佈適用於 Android 的公司入口網站應用程式以供下載。 由於中國沒有 Google Play 商店，因此 Android 裝置必須從中文應用程式市集取得應用程式。 適用於 Android 的公司入口網站應用程式可在下列市集下載：
* [百度](https://go.microsoft.com/fwlink/?linkid=836946)
* [華為](https://go.microsoft.com/fwlink/?linkid=836948)
* [騰迅](https://go.microsoft.com/fwlink/?linkid=836949)
* [豌豆莢](https://go.microsoft.com/fwlink/?linkid=836950)
* [小米](https://go.microsoft.com/fwlink/?linkid=836947)

適用於 Android 的公司入口網站應用程式會使用 Google Play Services 來與 Microsoft Intune 服務通訊。 由於中國尚無法使用 Google Play 服務，因此執行下列任何工作可能需要多達 8 小時才能完成。 

|Intune 管理主控台| 適用於 Android 的 Intune 公司入口網站應用程式 |Intune 公司入口網站|   
|---|---|---|
|完整抹除| 移除遠端裝置| 移除裝置 (本機和遠端)|
|選擇性抹除| 重設裝置| 重設裝置|
|新的或更新的應用程式部署| 安裝可用的企業營運應用程式| 裝置密碼重設|
|遠端鎖定|||
|密碼重設|||

## <a name="deprecations"></a>棄用功能

### <a name="firefox-to-no-longer-support-silverlight--vso-tba--"></a>Firefox 不再支援 Silverlight<!--VSO TBA-->
Mozilla 正於 [Firefox 瀏覽器](https://www.mozilla.org/firefox)的 52 版中移除對 Silverlight 的支援，將於 2017 年 3 月生效。 如此一來，您將無法再使用 Firefox 51 版之後的版本登入現有的 Intune 主控台。 建議使用 Internet Explorer 10 或 11，或是 [Firefox 52 版之前的版本](https://ftp.mozilla.org/pub/firefox/releases/)來存取管理主控台。 Intune 轉換到 Azure 入口網站將可在不需要 Silverlight 相依性的情況下，支援數種[現代化瀏覽器](https://docs.microsoft.com/en-us/azure/azure-preview-portal-supported-browsers-devices)。

### <a name="removal-of-exchange-online-mobile-inbox-policies---770687--"></a>移除 Exchange Online 行動信箱原則 <!--770687-->
從 12 月開始，系統管理員將無法再於 Intune 主控台內檢視或設定 Exchange Online (EAS) 行動信箱原則。 這項變更會從 12 月到 1 月推出給所有 Intune 租用戶。 所有現有的原則將會保持設定狀態；若要設定新的原則，請使用 Exchange 管理命令介面。 如需詳細資訊，請參閱[這裡](https://technet.microsoft.com/en-us/library/bb123783%28v=exchg.150%29.aspx)。

### <a name="intune-av-player-image-viewer-and-pdf-viewer-apps-are-no-longer-supported-on-android---747553--"></a>Android 不再支援 Intune AV 播放程式、影像檢視器及 PDF 檢視器應用程式 <!--747553-->
從 2016 年 12 月中開始，使用者將無法再使用 Intune AV 播放程式、影像檢視器及 PDF 檢視器應用程式。 這些應用程式已取代成 Azure 資訊保護應用程式。 如需 Azure 資訊保護應用程式的詳細資訊，請參閱[這裡](https://docs.microsoft.com/information-protection/rms-client/mobile-app-faq)。

### <a name="see-also"></a>請參閱
* [Microsoft Intune 部落格](http://go.microsoft.com/fwlink/?LinkID=273882)
* [雲端平台藍圖](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)
* [舊版的 Intune](whats-new-archive.md)



<!--HONumber=Dec16_HO2-->



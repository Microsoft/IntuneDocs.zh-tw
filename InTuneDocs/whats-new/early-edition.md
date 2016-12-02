---
title: "舊版 | Microsoft Intune"
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 11/22/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: f287a0ad082fa20a2e84abbf8f5585117aae6f57
ms.openlocfilehash: e604b8809bd444d9069d449a6c691a8444296623


---

# <a name="the-early-edition-for-microsoft-intune---december"></a>Microsoft Intune 的舊版 - 12 月

**舊版**提供 Microsoft Intune 即將發行版本要推出的功能清單。 此資訊以非常有限的基礎在 NDA 下提供，並可能有所變更。 這裡列出的一些功能可能有截止日期，而且可能會延遲到未來的版本。 其他功能正在實驗 (測試) 中進行測試，以確保它們可供客戶使用。 如果你們有任何問題或疑慮，請洽詢 Intune/PM 人員。

此頁面會定期更新。 請回來查看其他更新。

下列變更正在 Intune 的開發過程中。 混合式客戶部署於未來將會支援這些功能 (具備 Intune 的 Configuration Manager)。 如需新混合式功能的詳細資訊，請查看我們的 [Hybrid What’s New](https://technet.microsoft.com/en-US/library/mt718155(TechNet.10).aspx) (混合式新功能) 頁面。

<!--736542-->
## <a name="public-preview-of-the-new-intune-admin-experience-on-azure"></a>Azure 上新 Intune 管理體驗的公開預覽

在 2017 年初，我們會將完整管理體驗移轉到 Azure，以便在可透過圖形 API 擴充的新式服務平台上，對核心 EMS 工作流程進行強大的整合式管理。

新的試用租用戶將於本月開始看到 Azure 入口網站中新管理體驗的公開預覽。 在預覽狀態期間，將透過現有的 Intune 主控台反覆提供功能和同位檢查。

Azure 入口網站中的管理體驗將使用已宣佈的新群組和目標設定功能；當您現有的租用戶移轉至新的群組體驗時，也會同時將您移轉，以預覽您租用戶的新管理體驗。 在此同時，如果您想要在移轉租用戶之前測試或查看任何新功能，請註冊新的 Intune 試用帳戶或查看新的文件。

如果您有任何關於租用戶移轉時間表的問題，請連絡我們的移轉團隊：[intunegrps@microsoft.com](mailto:intunegrps@microsoft.com)。

### <a name="telecom-expense-management-integration-in-public-preview-of-azure-portal--747605--"></a>Azure 入口網站公開預覽中的電信費用管理整合<!--747605-->
我們現在將開始在 Azure 入口網站中預覽與協力廠商電信費用管理 (Telecom Expense Management，TEM) 服務的整合。 您可以使用 Intune 強制執行限制國內和漫遊資料使用量。 我們將開始與 [Saaswedo](http://www.saaswedo.com) 進行這些整合。

## <a name="new-capabilities"></a>新功能

### <a name="multi-factor-authentication-across-all-platforms---747590--"></a>跨所有平台的 Multi-Factor Authentication <!--747590-->
您現在可以在一組選取的使用者從 Azure 管理入口網站註冊 iOS、Android、Windows 8.1+ 或 Windows Phone 8.1+ 裝置時，對這些使用者強制執行 Multi-Factor Authentication (MFA)，方法是在 Azure Active Directory 中設定 Microsoft Intune 註冊應用程式的相關 MFA。

### <a name="conditional-access-for-mam-with-sharepoint-online---vso-679339--"></a>MAM 和 SharePoint Online 的條件存取 <!--VSO 679339-->
您可以禁止不受 Intune 行動應用程式管理 (MAM) 原則支援的應用程式存取 SharePoint Online。  您可以在 Azure 入口網站中使用 Intune 行動應用程式管理開始進行。 在包含 SharePoint Online 選項的 [設定] 刀鋒視窗中，尋找 [條件存取] 區段。 這項功能將與服務版本的其餘部分分開提供。

## <a name="notices"></a>通知

### <a name="multi-factor-authentication-on-enrollment-moving-to-the-azure-portal---vso-750545--"></a>移至 Azure 入口網站的註冊相關 Multi-Factor Authentication <!--VSO 750545-->
之前，系統管理員會移至 Intune 主控台或 Configuration Manager (1610 版以前) 主控台，以設定用於 Intune 註冊的 MFA。 透過這項更新的功能，您現在將會使用 Intune 認證登入 [Microsoft Azure 入口網站](https://manage.windowsazure.com)，並透過 Azure AD 進行 MFA 設定。 如需詳細資訊，請參閱[這裡](https://aka.ms/mfa_ad)。

### <a name="company-portal-app-for-android-now-available-in-china---vso-658093--"></a>中國現在提供適用於 Android 的公司入口網站應用程式 <!--VSO 658093-->
我們將在中國發佈適用於 Android 的公司入口網站應用程式以供下載。 由於中國沒有 Google Play 商店，因此 Android 裝置必須從中文應用程式市集取得應用程式。 適用於 Android 的公司入口網站應用程式將在 360、騰訊、小米、豌豆荚和華為提供下載。 

適用於 Android 的公司入口網站應用程式會使用 Google Play Services 來與 Microsoft Intune 服務通訊。 由於中國尚無法使用 Google Play 服務，因此執行下列任何工作可能需要多達 8 小時才能完成。 

|Intune 管理主控台| 適用於 Android 的 Intune 公司入口網站應用程式 |Intune 公司入口網站|   
|---|---|---|
|完整抹除| 移除遠端裝置| 移除裝置 (本機和遠端)|
|選擇性抹除| 重設裝置| 重設裝置|
|新的或更新的應用程式部署| 安裝可用的企業營運應用程式| 裝置密碼重設|
|遠端鎖定|||
|密碼重設|||

## <a name="deprecations"></a>棄用功能

### <a name="removal-of-exchange-online-mobile-inbox-policies---770687--"></a>移除 Exchange Online 行動信箱原則 <!--770687-->
從 12 月開始，系統管理員將無法再於 Intune 主控台內檢視或設定 Exchange Online (EAS) 行動信箱原則。 這項變更會從 12 月到 1 月推出給所有 Intune 租用戶。 所有現有的原則將會保持設定狀態；若要設定新的原則，請使用 Exchange 管理命令介面。 如需詳細資訊，請參閱[這裡](https://technet.microsoft.com/en-us/library/bb123783%28v=exchg.150%29.aspx)。

### <a name="intune-av-player-image-viewer-and-pdf-viewer-apps-are-no-longer-supported-on-android---747553--"></a>Android 不再支援 Intune AV 播放程式、影像檢視器及 PDF 檢視器應用程式 <!--747553-->
從 2016 年 12 月中開始，使用者將無法再使用 Intune AV 播放程式、影像檢視器及 PDF 檢視器應用程式。 這些應用程式已取代成 Azure 資訊保護應用程式。 如需 Azure 資訊保護應用程式的詳細資訊，請參閱[這裡](https://docs.microsoft.com/information-protection/rms-client/mobile-app-faq)。

### <a name="see-also"></a>請參閱
如需近期發展的詳細資料，請參閱 [Microsoft Intune 的新功能](whats-new-in-microsoft-intune.md)。



<!--HONumber=Nov16_HO4-->



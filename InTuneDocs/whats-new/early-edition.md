---
title: "舊版 | Microsoft Docs"
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 02/13/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: d0b3a883bb307fb06cb8d16500798086f328314a
ms.openlocfilehash: eeebf8b6b3bc5c7c35386eb20c96097af1f6769c
ms.lasthandoff: 02/14/2017


---


# <a name="the-early-edition-for-microsoft-intune---february-2017"></a>舊版 Microsoft Intune - 2017 年 2 月

**舊版**提供 Microsoft Intune 即將發行版本要推出的功能清單。 此資訊以非常有限的基礎在 NDA 下提供，並可能有所變更。 這裡列出的一些功能可能有截止日期，而且可能會延遲到未來的版本。 其他功能正在實驗 (測試) 中進行測試，以確保它們可供客戶使用。 如果你們有任何問題或疑慮，請洽詢 Intune/PM 人員。

此頁面會定期更新。 請回來查看其他更新。

> [!Note]
> 下列變更正在 Intune 的開發過程中。 混合式客戶部署於未來將會支援這些功能 (具備 Intune 的 Configuration Manager)。 如需新混合式功能的詳細資訊，請查看我們的 [Hybrid What’s New](https://docs.microsoft.com/en-us/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management) (混合式新功能) 頁面。

## <a name="new-capabilities"></a>新功能

### <a name="modernizing-the-company-portal-website---753980--"></a>現代化公司入口網站 <!--753980-->
從&2; 月開始，公司入口網站的設計會與其他 Microsoft 產品和服務一致，方法是使用新的對比色彩配置、動態圖例和「漢堡功能表」：![公司入口網站左上角新增的漢堡功能表小型影像](./media/CP_hamburger_menu.png)，其包含技術服務連絡人詳細資料以及現有受管理裝置的相關資訊。 登陸頁面將會予以重新排列，以透過 [精選和最近更新] 應用程式的浮動切換來強調使用者可用的應用程式。 您可以在 [UI updates for Intune end user apps](https://docs.microsoft.com/intune/whats-new/whats-new-in-intune-app-ui) (Intune 使用者應用程式的 UI 更新) 頁面上找到更新前後的影像。

### <a name="new-guided-experience-for-windows-10-company-portal---713927--"></a>Windows 10 公司入口網站新型引導式體驗 <!--713927-->
從 3 月開始，Windows 10 的公司入口網站將會包含之前尚未確定或註冊的裝置之引導式 Intune 逐步解說體驗。 此全新體驗提供逐步指示，專為使用者的 Windows 10 組建所量身打造，引導使用者執行 AAD 註冊 (條件式存取功能之識別所需)，以及 MDM 註冊 (裝置管理功能所需)。 從公司入口網站首頁上即可使用引導式體驗，且使用者如果沒有完成登錄與註冊，仍可選擇繼續使用該應用程式，但體驗的功能可能有限。

###

## <a name="notices"></a>通知

### <a name="group-migration-will-not-require-any-updates-to-groups-or-policies-for-ios-devices---898837--"></a>群組移轉不需要 iOS 裝置群組或原則的任何更新 <!--898837-->
每個公司裝置註冊設定檔預先指派的 Intune 裝置群組，在移轉到 Azure Active Directory 裝置群組期間，都會根據公司裝置註冊設定檔的名稱，在 AAD 中建立對應的動態裝置群組。 這可確保在裝置註冊時，它們會自動分組，並和原始的 Intune 群組收到相同的原則和應用程式。

一旦租用戶進入分組和鎖定目標的移轉程序，Intune 就會自動建立動態的 AAD 群組，以對應公司裝置註冊設定檔鎖定的 Intune 群組。 如果 Intune 管理員刪除了鎖定的 Intune 群組，就不會刪除對應的動態 AAD 群組。 群組成員和動態查詢會予以清除，但群組本身會一直保留到 IT 管理員透過 AAD 入口網站移除它。

同樣地，如果 IT 管理員變更公司裝置註冊設定檔鎖定的 Intune 群組，Intune 就會建立新的動態群組，反映新的設定檔指派，但不會移除舊指派建立的動態群組。

### <a name="new-mdm-server-address-for-windows-devices---893007--"></a>Windows 裝置的新 MDM 伺服器位址 <!--893007-->
如果 Windows 和 Windows Phone 使用者輸入 __manage.microsoft.com__ 作為 MDM 伺服器位址 (系統提示時)，其嘗試註冊裝置會失敗。 MDM 伺服器位址已從 __manage.microsoft.com__ 變更為 __enrollment.manage.microsoft.com__。 請通知您的使用者，如果在註冊 Windows 或 Windows Phone 裝置時收到提示，請使用 __enrollment.manage.microsoft.com__ 作為 MDM 伺服器位址。 此更新需要 DNS 中有任何 CNAME 可將 __EnterpriseEnrollment.contoso.com__ 重新導向至 __manage.microsoft.com__，以替換成 DNS 中有 CNAME 可將 __EnterpriseEnrollment.contoso.com__ 重新導向至 __EnterpriseEnrollment-s.manage.microsoft.com__。 如需此變更的其他資訊，請前往 [aka.ms/intuneenrollsvrchange](https://aka.ms/intuneenrollsvrchange)。

### <a name="new-user-experience-for-the-company-portal-app-for-android---621622--"></a>Android 版公司入口網站應用程式的新使用者體驗 <!--621622-->
從&3; 月起，Android 版公司入口網站應用程式會遵循[素材設計方針](https://material.io/guidelines/material-design/introduction.html)建立更現代化的外觀與風格。 此改善的使用者體驗包括︰

* __色彩__︰索引標籤標頭可根據您的自訂調色盤上色。
* __介面__︰[應用程式] 索引標籤已更新 [精選 App] 和 [所有應用程式] 按鈕。 [搜尋] 按鈕現在是浮動的動作按鈕。
* __瀏覽__︰所有應用程式都會以索引標籤式的檢視顯示 [精選]、[所有] 與 [類別] 以方便瀏覽。
* __服務__︰[我的裝置] 和 [連絡 IT] 索引標籤皆已改善可讀性。

您可以在 [UI updates for Intune end user apps](https://docs.microsoft.com/intune/whats-new/whats-new-in-intune-app-ui) (Intune 終端使用者應用程式的 UI 更新) 頁面上找到更新前後的影像。

### <a name="associate-multiple-management-tools-with-the-windows-store-for-business---926135--"></a>商務用 Windows 市集的相關多重管理工具 <!--926135-->
如果您使用多種管理工具來部署商務用 Windows 市集應用程式，以前只能建立其中一種與商務用 Windows 市集的關聯性。 現在可以建立多種管理工具與市集的關聯性，例如，Intune 和 Configuration Manager。 如需詳細資料，請參閱[以 Microsoft Intune 管理購自商務用 Windows 市集的應用程式](https://docs.microsoft.com/en-us/intune/deploy-use/manage-apps-you-purchased-from-the-windows-store-for-business-with-microsoft-intune#associate-your-windows-store-for-business-account-with-intune)。

## <a name="public-preview-of-the-new-intune-admin-experience-on-azure---736542--"></a>Azure 上新 Intune 管理體驗的公開預覽 <!--736542-->

在 2017 年初，我們會將完整管理體驗移轉到 Azure，以便在可透過圖形 API 擴充的新式服務平台上，對核心 EMS 工作流程進行強大的整合式管理。

新的試用租用戶將於本月開始看到 Azure 入口網站中新管理體驗的公開預覽。 在預覽狀態期間，將透過現有的 Intune 主控台反覆提供功能和同位檢查。

Azure 入口網站中的管理體驗將使用已宣佈的新群組和目標設定功能；當您現有的租用戶移轉至新的群組體驗時，也會同時將您移轉，以預覽您租用戶的新管理體驗。 在此同時，如果您想要在移轉租用戶之前測試或查看任何新功能，請註冊新的 Intune 試用帳戶或查看[新文件](https://docs.microsoft.com/en-us/intune-azure/introduction/what-is-microsoft-intune)。

如果您有任何關於租用戶移轉時間表的問題，請連絡我們的移轉團隊：[intunegrps@microsoft.com](mailto:intunegrps@microsoft.com)。

### <a name="february-2017"></a>2017 年 2 月

#### <a name="ability-to-restrict-mobile-device-enrollment---747600-795782--"></a>限制行動裝置註冊的能力 <!--747600, 795782-->
Intune 正在新增新的註冊限制，以控制哪些行動裝置平台可以註冊。 Intune 將行動裝置平台分為 iOS、macOS、Android、Windows 和 Windows Mobile。

* 限制行動裝置註冊不會限制電腦用戶端註冊。  
* 僅限 iOS 與 Android，有一個額外選項可阻擋註冊個人擁有的裝置。

Intune 會將所有的新裝置標示為個人，除非 IT 系統管理員採取動作將它們標示為公司擁有，如[本文章](https://docs.microsoft.com/en-us/intune/deploy-use/manage-corporate-owned-devices)所說明。

#### <a name="view-all-actions-on-managed-devices---677150--"></a>檢視受管理裝置上的所有動作 <!--677150-->
新的__裝置動作__報表會顯示曾執行遠端動作的人員，像是裝置恢復出廠預設值，並會另外顯示該動作的狀態。

#### <a name="non-managed-devices-can-access-assigned-apps---664691--"></a>未受管理的裝置可以存取已指派的應用程式 <!--664691-->
iOS 和 Android 使用者能夠在他們未受管理的裝置上，安裝指派給他們的「無須註冊即可使用」應用程式，這屬於公司入口網站的設計變更。 使用 Intune 認證，使用者能夠登入公司入口網站，並查看指派給他們的應用程式清單。 「無須註冊即可使用」應用程式的應用程式套件，可透過公司入口網站下載取得。 這項變更不會影響需要註冊才能安裝的應用程式，因為如果使用者想要安裝這些應用程式，系統會提示他們註冊裝置。

#### <a name="custom-app-categories---748805--"></a>自訂應用程式類別 <!--748805-->
您現在可以建立、編輯和指派您新增至 Intune 之應用程式的類別。 目前只能以英文指定類別。
請參閱[如何將應用程式新增至 Intune](/intune-azure/manage-apps/add-apps)。

#### <a name="display-device-categories---814654--"></a>顯示裝置類別 <!--814654-->
裝置清單現在會以資料行顯示裝置類別。 您也可以在裝置內容刀鋒視窗的內容區段中編輯類別。

### <a name="january-2017"></a>2017 年 1 月

#### <a name="custom-app-categories---748805--"></a>自訂應用程式類別 <!--748805-->
您現在可以建立、編輯和指派您新增至 Intune 之應用程式的類別。 目前只能以英文指定類別。

#### <a name="assign-line-of-business-apps-whether-or-not-devices-are-enrolled---748803--"></a>不論是否註冊裝置都指派企業營運應用程式 <!--748803-->
您現在可以將市集中的企業營運和應用程式指派給不論是否向 Intune 註冊其裝置的使用者。 如果未向 Intune 註冊使用者裝置，則他們必須前往公司入口網站安裝它，而不是公司入口網站應用程式。

### <a name="december-2016"></a>2016 年 12 月

#### <a name="telecom-expense-management-integration-in-public-preview-of-azure-portal--747605--"></a>Azure 入口網站公開預覽中的電信費用管理整合<!--747605-->
我們現在將開始在 Azure 入口網站中預覽與協力廠商電信費用管理 (Telecom Expense Management，TEM) 服務的整合。 您可以使用 Intune 強制執行限制國內和漫遊資料使用量。 我們將開始與 [Saaswedo](http://www.saaswedo.com) 進行這些整合。 若要在您的試用租用戶中啟用此功能，請[連絡 Microsoft 支援服務](https://docs.microsoft.com/intune/troubleshoot/how-to-get-support-for-microsoft-intune)。

### <a name="see-also"></a>請參閱
如需近期發展的詳細資料，請參閱 [Microsoft Intune 的新功能](whats-new-in-microsoft-intune.md)。


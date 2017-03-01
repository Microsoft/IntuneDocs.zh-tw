---
title: "新功能 | Microsoft Docs"
description: "了解本月 Microsoft Intune 版本的新功能，以及過去的版本"
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: fab51ee0-638d-4dd4-8d8f-1f263bc11e5c
ms.reviewer: cacampbell
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 846084a3810e43d9fd6a6c254f1b0167a36f37ff
ms.openlocfilehash: b99731c7becd90f4092ec758234a96e202d95130
ms.lasthandoff: 02/15/2017


---
# <a name="whats-new-in-microsoft-intune---february-2017"></a>Microsoft Intune 的新功能 - 2017 年 2 月
了解此 Microsoft Intune 版本中的新功能。 您也可以了解即將推出且您應該加以規劃的變更，以及過去版本的相關資訊。

> [!Note]
> 混合式客戶部署於未來將會支援這些功能 (具備 Intune 的 Configuration Manager)。 如需新混合式功能的詳細資訊，請查看我們的 [Hybrid What’s New](https://docs.microsoft.com/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management) (混合式新功能) 頁面。

## <a name="new-capabilities"></a>新功能

### <a name="modernizing-the-company-portal-website---753980--"></a>現代化公司入口網站 <!--753980-->
公司入口網站會支援以沒有受管理裝置的使用者為目標的應用程式。 網站會與其他 Microsoft 產品和服務一致，方法是使用新的對比色彩配置、動態圖例和「漢堡功能表」：![公司入口網站左上角新增的漢堡功能表小型影像](./media/CP_hamburger_menu.png)，其包含技術服務連絡人詳細資料以及現有受管理裝置的相關資訊。 登陸頁面將會予以重新排列，以透過 [精選和最近更新] 應用程式的浮動切換來強調使用者可用的應用程式。 您可以在 [UI updates for Intune end user apps](https://docs.microsoft.com/intune/whats-new/whats-new-in-intune-app-ui) (Intune 使用者應用程式的 UI 更新) 頁面上找到更新前後的影像。

### <a name="new-guided-experience-for-windows-10-company-portal---713927--"></a>Windows 10 公司入口網站新型引導式體驗 <!--713927-->
從 3 月開始，Windows 10 的公司入口網站將會包含之前尚未確定或註冊的裝置之引導式 Intune 逐步解說體驗。 此全新體驗提供逐步指示，專為使用者的 Windows 10 組建所量身打造，引導使用者執行 AAD 註冊 (條件式存取功能之識別所需)，以及 MDM 註冊 (裝置管理功能所需)。 從公司入口網站首頁上即可使用引導式體驗，且使用者如果沒有完成登錄與註冊，仍可選擇繼續使用該應用程式，但體驗的功能可能有限。

## <a name="notices"></a>通知

### <a name="group-migration-will-not-require-any-updates-to-groups-or-policies-for-ios-devices---898837--"></a>群組移轉不需要 iOS 裝置群組或原則的任何更新 <!--898837-->
每個公司裝置註冊設定檔預先指派的 Intune 裝置群組，在移轉到 Azure Active Directory 裝置群組期間，都會根據公司裝置註冊設定檔的名稱，在 AAD 中建立對應的動態裝置群組。 這可確保在裝置註冊時，它們會自動分組，並與原始 Intune 群組收到相同的原則和應用程式。 

一旦租用戶進入分組和鎖定目標的移轉程序，Intune 就會自動建立動態的 AAD 群組，以對應公司裝置註冊設定檔鎖定的 Intune 群組。 如果 Intune 管理員刪除了鎖定的 Intune 群組，就不會刪除對應的動態 AAD 群組。 群組成員和動態查詢會予以清除，但群組本身會一直保留到 IT 管理員透過 AAD 入口網站移除它。

同樣地，如果 IT 管理員變更公司裝置註冊設定檔鎖定的 Intune 群組，Intune 就會建立新的動態群組，反映新的設定檔指派，但不會移除舊指派建立的動態群組。

### <a name="defaulting-to-managing-windows-desktop-devices-through-windows-settings---663050--"></a>預設為透過 Windows 設定管理 Windows Desktop 裝置 <!--663050-->
註冊 Windows 10 Desktop 的預設行為會變更。 新的註冊將會遵循一般 MDM 代理程式註冊流程，而不是透過電腦代理程式。 公司入口網站會提供 Windows 10 Desktop 使用者，有關引導他們新增 Windows 10 Desktop 電腦作為行動裝置之程序的註冊指示。 這不會影響目前已註冊的電腦，而且您的組織還是可以使用電腦代理程式來管理 Windows 10 Desktop，如[設定 Windows 裝置管理](https://docs.microsoft.com/intune/deploy-use/set-up-windows-device-management-with-microsoft-intune)中所述。

### <a name="improving-mobile-app-management-support-for-selective-wipe---581242--"></a>改善選擇性抹除的行動應用程式管理支援 <!--581242-->
如果因 [離線間隔幾天後抹除 App 資料] 原則而自動移除工作或學校資料，則會將如何重新存取工作或學校資料的其他指引授與終端使用者。<!--, or the removal of the Intune Company Portal on Android.-->

### <a name="company-portal-for-ios-links-open-inside-the-app---665954--"></a>適用於 iOS 的公司入口網站連結會在應用程式內開啟 <!--665954-->
適用於 iOS 的公司入口網站應用程式連結 (包括文件和應用程式的連結) 會使用 Safari 的應用程式內檢視直接在公司入口網站應用程式中開啟。 這項更新將在&1; 月與服務更新分開提供。

### <a name="new-mdm-server-address-for-windows-devices---893007--"></a>Windows 裝置的新 MDM 伺服器位址 <!--893007-->
如果 Windows 和 Windows Phone 使用者輸入 __manage.microsoft.com__ 作為 MDM 伺服器位址 (系統提示時)，其嘗試註冊裝置會失敗。 MDM 伺服器位址已從 __manage.microsoft.com__ 變更為 __enrollment.manage.microsoft.com__。 請通知您的使用者，如果在註冊 Windows 或 Windows Phone 裝置時收到提示，請使用 __enrollment.manage.microsoft.com__ 作為 MDM 伺服器位址。 如需此變更的其他資訊，請前往 [aka.ms/intuneenrollsvrchange](https://aka.ms/intuneenrollsvrchange)。

### <a name="new-user-experience-for-the-company-portal-app-for-android---621622--"></a>Android 版公司入口網站應用程式的新使用者體驗 <!--621622-->
從&3; 月起，Android 版公司入口網站應用程式會遵循[素材設計方針](https://material.io/guidelines/material-design/introduction.html)建立更現代化的外觀與風格。 此改善的使用者體驗包括︰

* __色彩__︰索引標籤標頭可根據您的自訂調色盤上色。
* __介面__︰[應用程式] 索引標籤已更新 [精選 App] 和 [所有應用程式] 按鈕。 [搜尋] 按鈕現在是浮動的動作按鈕。
* __瀏覽__︰所有應用程式都會以索引標籤式的檢視顯示 [精選]、[所有] 與 [類別] 以方便瀏覽。
* __服務__︰[我的裝置] 和 [連絡 IT] 索引標籤皆已改善可讀性。

您可以在 [UI updates for Intune end user apps](https://docs.microsoft.com/intune/whats-new/whats-new-in-intune-app-ui) (Intune 終端使用者應用程式的 UI 更新) 頁面上找到更新前後的影像。

### <a name="associate-multiple-management-tools-with-the-windows-store-for-business---926135--"></a>商務用 Windows 市集的相關多重管理工具 <!--926135-->
如果您使用多種管理工具來部署商務用 Windows 市集應用程式，以前只能建立其中一種與商務用 Windows 市集的關聯性。 現在可以建立多種管理工具與市集的關聯性，例如，Intune 和 Configuration Manager。 如需詳細資料，請參閱[以 Microsoft Intune 管理購自商務用 Windows 市集的應用程式](https://docs.microsoft.com/en-us/intune/deploy-use/manage-apps-you-purchased-from-the-windows-store-for-business-with-microsoft-intune#associate-your-windows-store-for-business-account-with-intune)。

## <a name="whats-new-in-the-public-preview-of-the-intune-admin-experience-on-azure---736542--"></a>Azure 的 Intune 管理體驗公開預覽新功能<!--736542-->

在 2017 年初，我們會將完整管理體驗移轉到 Azure，以便在可透過圖形 API 擴充的新式服務平台上，對核心 EMS 工作流程進行強大的整合式管理。

新的試用租用戶將於本月開始看到 Azure 入口網站中新管理體驗的公開預覽。 在預覽狀態期間，將透過現有的 Intune 主控台反覆提供功能和同位檢查。

Azure 入口網站中的管理體驗將使用已宣佈的新群組和目標設定功能；當您現有的租用戶移轉至新的群組體驗時，也會同時將您移轉，以預覽您租用戶的新管理體驗。 在此同時，如果您想要在移轉租用戶之前測試或查看任何新功能，請註冊新的 Intune 試用帳戶或查看[新文件](https://docs.microsoft.com/intune-azure/introduction/whats-new)。

如果您有任何關於租用戶移轉時間表的問題，請連絡我們的移轉團隊：[intunegrps@microsoft.com](mailto:intunegrps@microsoft.com)。

您可以在[這裡](https://docs.microsoft.com/intune-azure/introduction/whats-new)找到 Azure 的 Intune 預覽新功能。

### <a name="see-also"></a>請參閱
* [Microsoft Intune 部落格](http://go.microsoft.com/fwlink/?LinkID=273882)
* [雲端平台藍圖](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)
* [Azure 預覽的新功能](https://docs.microsoft.com/intune-azure/introduction/whats-new)
* [公司入口網站 UI 的新功能](https://docs.microsoft.com/intune/whats-new/whats-new-in-company-portal-ui)
* [新功能封存](whats-new-archive.md)


---
title: "新功能 | Microsoft Docs"
description: "了解 Microsoft Intune 本月及過去版本中的新功能"
keywords: 
author: mtillman
ms.author: mtillman
manager: angrobe
ms.date: 03/28/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: fab51ee0-638d-4dd4-8d8f-1f263bc11e5c
ms.reviewer: priyar
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: c473a1f05b0a7b0ce5205598b2b9a9b86bfe6c1d
ms.openlocfilehash: bddd8c0dc74835f74a71af1d900d43d84aab894c
ms.lasthandoff: 03/29/2017


---
# <a name="whats-new-in-microsoft-intune---march-2017"></a>Microsoft Intune 的新功能 - 2017 年 3 月
了解此 Microsoft Intune 版本中的新功能。 您也可以了解即將推出且您應該加以規劃的變更，以及過去版本的相關資訊。

> [!Note]
> 混合式客戶部署於未來將會支援這些功能 (具備 Intune 的 Configuration Manager)。 如需新混合式功能的詳細資訊，請查看我們的 [Hybrid What’s New](https://docs.microsoft.com/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management) (混合式新功能) 頁面。

## <a name="new-capabilities"></a>新功能

### <a name="support-for-skycure"></a>支援 Skycure

您現在可以根據由 Skycure (一個與 Microsoft Intune 整合的行動威脅防禦解決方案) 所進行的風險評估，使用條件式存取來控制行動裝置對公司資源的存取。 風險評估是根據收集自執行 Skycure 裝置的遙測，包括︰

- 實體防禦
- 網路防禦
- 應用程式防禦
- 弱點防禦

您可以根據透過 Intune 裝置合規性政策所啟用的 Skycure 風險評估，來設定 EMS 條件式存取原則。 您可以根據偵測到的威脅，使用這些原則來允許或封鎖不符合規範的裝置存取公司資源。 如需詳細資訊，請參閱 [Skycure Mobile Threat Defense 連接器](/intune/deploy-use/skycure-mobile-threat-defense-connector)。

### <a name="new-user-experience-for-the-company-portal-app-for-android---621622--"></a>Android 版公司入口網站應用程式的新使用者體驗 <!--621622-->

Android 版公司入口網站應用程式將會更新其使用者介面，以提供更現代化的外觀和操作，以及更佳的使用者體驗。 值得注意的更新如下︰

- 色彩：公司入口網站索引標籤標頭會以 IT 定義的品牌上色。
- 應用程式：在 [應用程式] 索引標籤中，已更新 [熱門應用程式] 和 [所有應用程式] 按鈕。
- 搜尋：在 [應用程式] 索引標籤中，[搜尋] 按鈕是浮動的動作按鈕。
- 瀏覽應用程式：[所有應用程式] 檢視會以索引標籤式的檢視顯示 [熱門]、[所有] 與 [類別]，以更方便瀏覽。
- 支援：已更新 [我的裝置] 和 [連絡 IT] 索引標籤以提高可讀性。

如需有關這些變更的詳細資訊，請參閱 [Intune 使用者應用程式的 UI 更新](whats-new-in-intune-app-ui.md)。

### <a name="non-managed-devices-can-access-assigned-apps---664691--"></a>未受管理的裝置可以存取已指派的應用程式 <!--664691-->

iOS 和 Android 使用者能夠在他們未受管理的裝置上，安裝指派給他們的「無須註冊即可使用」應用程式，這屬於公司入口網站的設計變更。 使用 Intune 認證，使用者能夠登入公司入口網站，並查看指派給他們的應用程式清單。 「無須註冊即可使用」應用程式的應用程式套件，可透過公司入口網站下載取得。 這項變更不會影響需要註冊才能安裝的應用程式，因為如果使用者想要安裝這些應用程式，系統會提示他們註冊裝置。

### <a name="signing-script-for-windows-10-company-portal---941642--"></a>Windows 10 公司入口網站的簽署指令碼 <!--941642-->

如果您需要下載和側載「Windows 10 公司入口網站」應用程式，您現在可以使用指令碼為您的組織簡化及加速應用程式簽署程序。   若需要下載指令碼及其使用指示，請參閱 TechNet 資源庫上 [Windows 10 公司入口網站專用的 Microsoft Intune 簽署指令碼](https://aka.ms/win10cpscript)。 如需本公告的詳細資訊，請參閱 Intune 支援小組部落格上的[更新您的 Windows 10 公司入口網站應用程式](https://blogs.technet.microsoft.com/intunesupport/2017/03/13/updating-your-windows-10-company-portal-app/)。


## <a name="notices"></a>通知

### <a name="support-for-ios-103"></a>支援 iOS 10.3

iOS 10.3 版在 2017 年 3 月 27 日開始向 iOS 使用者推出。 所有現有的 Intune MDM 與 MAM 案例都與最新版本的 Apple OS 相容。 當使用者將裝置和應用程式升級到 iOS 10.3 時，我們預期所有目前可用來管理 iOS 裝置的 Intune 功能將可繼續運作。

目前沒有任何已知問題可分享。 如果您在使用 iOS 10.3 時發生任何問題，歡迎連絡 [Intune 支援小組](/intune/troubleshoot/contact-assisted-phone-support-for-microsoft-intune)。

### <a name="improved-support-for-android-users-based-in-china---720444--"></a>改善對於中國 Android 使用者的支援 <!--720444-->

由於中國沒有 Google Play 商店，因此 Android 裝置必須從中文市集取得應用程式。 公司入口網站將支援此工作流程，方法是將中國的 Android 使用者重新導向，以便從當地的應用程式市集下載公司入口網站及 Outlook 應用程式。 這將會在啟用條件式存取原則時，改善對於行動裝置管理及行動應用程式管理的使用者體驗。 Android 版公司入口網站和 Outlook 應用程式可在下列中文應用程式市集取得：

- [百度](https://go.microsoft.com/fwlink/?linkid=836946)
- [小米應用商店](https://go.microsoft.com/fwlink/?linkid=836947)
- [騰訊](https://go.microsoft.com/fwlink/?linkid=836949)
- [華為](https://go.microsoft.com/fwlink/?linkid=836948)
- [豌豆莢](https://go.microsoft.com/fwlink/?linkid=836950)

### <a name="best-practice-make-sure-your-company-portal-apps-are-up-to-date---879465--"></a>最佳作法︰請確定您的公司入口網站應用程式是最新版本 <!--879465-->

我們於 2016 年 12 月發行的更新，會針對成群使用者註冊 iOS、Android、Windows 8.1+ 或 Windows Phone 8.1+ 裝置時，強制使用 Multi-Factor Authentication (MFA)。 若公司入口網站應用程式低於特定基準版本 (Android 為 v5.0.3419.0+，iOS 為 v2.1.17+)，這個功能便無法運作。

Microsoft 不斷致力改善 Intune，在主控台及所有支援平台的公司入口網站應用程式中加入新功能。 有鑑於此，Microsoft 僅會針對在最新公司入口網站應用程式之中所發現問題來發行修正。 因此，我們建議您使用最新版的公司入口網站應用程式，才能為您帶來最佳的使用者體驗。

>[!Tip]
> 請您的使用者將其裝置設定為自動從適當的應用程式商店更新應用程式。 如果您已在網路共用上提供 Android 公司入口網站應用程式，您可以從 [Microsoft 下載中心](https://www.microsoft.com/download/details.aspx?id=49140)下載最新版本。

### <a name="microsoft-teams-is-now-enabled-for-mam-on-ios-and-android"></a>iOS 和 Android 版本的 MAM 現在已可使用 Microsoft Teams

Microsoft 已經宣布 Microsoft Teams 正式運作。 更新後的 iOS 和 Android 版 Microsoft Teams 應用程式，現在可在 Intune 行動裝置應用程式管理 (MAM) 功能中使用，因此您可以讓您的團隊自由地跨裝置工作，同時確保每回的交談和公司資料都受到保護。 如需詳細資訊，請參閱 Enterprise Mobility and Security 部落格上的 [Microsoft Teams 公告](https://blogs.technet.microsoft.com/enterprisemobility/2017/03/14/microsoft-teams-is-now-generally-available-and-mam-enabled-on-ios-and-android/)。


## <a name="whats-new-in-the-public-preview-of-the-intune-admin-experience-on-azure---736542--"></a>Azure 的 Intune 管理體驗公開預覽新功能<!--736542-->

在 2017 年初，我們會將完整管理體驗移轉到 Azure，以便在可透過圖形 API 擴充的新式服務平台上，對核心 EMS 工作流程進行強大的整合式管理。

新的試用租用戶將於本月開始看到 Azure 入口網站中新管理體驗的公開預覽。 在預覽狀態期間，將透過現有的 Intune 主控台反覆提供功能和同位檢查。

Azure 入口網站中的管理體驗將使用已宣佈的新群組和目標設定功能；當您現有的租用戶移轉至新的群組體驗時，也會同時將您移轉，以預覽您租用戶的新管理體驗。 在此同時，如果您想要在移轉租用戶之前測試或查看任何新功能，請註冊新的 Intune 試用帳戶或查看[新文件](/intune-azure/introduction/whats-new)。

> [!Note]
> 針對 Azure 入口網站預覽版，我們將在本月首度發行變更。 不過，基於 Intune 服務發行的方式不同，變更可能無法立即生效。  數個服務元件必須依序更新，才能使用新的入口網站功能。 Azure 入口網站預覽版的變更將於近日首度發行，屆時請務必試試看。 如需變更的完整清單，請參閱 [Microsoft Intune 預覽版的新功能](/intune-azure/introduction/whats-new)。

### <a name="administration-roles-being-replaced-in-azure-portal"></a>Azure 入口網站中要被取代的管理角色

在 Intune 傳統入口網站 (Silverlight) 中使用的現有行動應用程式管理 (MAM) 管理角色 (參與者、擁有者或唯讀) 在 Intune Azure 入口網站中會取代為一組新的、完整的角色型管理控制 (RBAC)。 當您移轉至 Azure 入口網站之後，您必須將系統管理員重新指派至這些新的管理角色。 如需 RBAC 和新角色的詳細資訊，請參閱 [Microsoft Intune 的角色型存取控制](/intune-azure/access-control/role-based-access-control)。


## <a name="whats-coming"></a>未來動態

### <a name="apple-to-require-updates-for-application-transport-security---748318--"></a>Apple 需要更新 Application Transport Security <!--748318-->

Apple 宣告，從 2017 年春季開始，將會強制執行 Application Transport Security (ATS) 的特定需求。 ATS 可用來對透過 HTTPS 進行的所有應用程式通訊，強制執行更嚴格的安全性。 這項變更會影響使用 iOS 公司入口網站應用程式的 Intune 客戶。 如需詳細資訊，請檢閱我們的 [Intune 支援部落格](https://aka.ms/compportalats)。

### <a name="see-also"></a>請參閱
* [Microsoft Intune 部落格](http://go.microsoft.com/fwlink/?LinkID=273882)
* [雲端平台藍圖](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)
* [Azure 預覽的新功能](https://docs.microsoft.com/intune-azure/introduction/whats-new)
* [公司入口網站 UI 的新功能](https://docs.microsoft.com/intune/whats-new/whats-new-in-company-portal-ui)
* [新功能封存](whats-new-archive.md)


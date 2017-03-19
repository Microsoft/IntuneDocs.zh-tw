---
title: "舊版 | Microsoft Docs"
description: 
keywords: 
author: mtillman
ms.author: mtillman
manager: angrobe
ms.date: 03/09/2017
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
ms.sourcegitcommit: 0936051b5c33a2e98f275ef7a3a32be2e8f5a8b0
ms.openlocfilehash: 0ba6695b595849f72eb44d8e6f095e8b1aae39eb
ms.lasthandoff: 03/10/2017


---


# <a name="the-early-edition-for-microsoft-intune---march-2017"></a>Microsoft Intune 的舊版 - 2017 年 3 月

**舊版**提供 Microsoft Intune 即將發行版本要推出的功能清單。 此資訊以非常有限的基礎在 NDA 下提供，並可能有所變更。 這裡列出的一些功能可能有截止日期，而且可能會延遲到未來的版本。 其他功能正在實驗 (測試) 中進行測試，以確保它們可供客戶使用。 如果你們有任何問題或疑慮，請洽詢 Intune/PM 人員。

此頁面會定期更新。 請回來查看其他更新。

> [!Note]
> 下列變更正在 Intune 的開發過程中。 混合式客戶部署於未來將會支援這些功能 (具備 Intune 的 Configuration Manager)。 如需新混合式功能的詳細資訊，請查看我們的 [Hybrid What’s New](https://docs.microsoft.com/en-us/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management) (混合式新功能) 頁面。

## <a name="new-capabilities"></a>新功能

### <a name="new-user-experience-for-the-company-portal-app-for-android---621622--"></a>Android 版公司入口網站應用程式的新使用者體驗 <!--621622-->

Android 版公司入口網站應用程式將會更新其使用者介面，以提供更現代化的外觀和操作，以及更佳的使用者體驗。 值得注意的更新如下︰

- 色彩：公司入口網站索引標籤標頭會以 IT 定義的品牌上色。
- 應用程式：在 [應用程式] 索引標籤中，已更新 [熱門應用程式] 和 [所有應用程式] 按鈕。
- 搜尋：在 [應用程式] 索引標籤中，[搜尋] 按鈕是浮動的動作按鈕。
- 瀏覽應用程式：[所有應用程式] 檢視會以索引標籤式的檢視顯示 [熱門]、[所有] 與 [類別]，以更方便瀏覽。
- 支援：已更新 [我的裝置] 和 [連絡 IT] 索引標籤以提高可讀性。

如需關於這些變更的詳細資料，請參閱[應用程式 UI 更新頁面](whats-new-in-intune-app-ui.md]。

## <a name="notices"></a>通知

### <a name="improved-support-for-android-users-based-in-china---720444--"></a>改善對於中國 Android 使用者的支援 <!--720444-->

由於中國沒有 Google Play 商店，因此 Android 裝置必須從中文市集取得應用程式。 公司入口網站將支援此工作流程，方法是將中國的 Android 使用者重新導向，以便從當地的應用程式市集下載公司入口網站及 Outlook 應用程式。 這將會在啟用條件式存取原則時，改善對於行動裝置管理及行動應用程式管理的使用者體驗。 Android 版公司入口網站和 Outlook 應用程式可在下列中文應用程式市集取得： 

- [百度](https://go.microsoft.com/fwlink/?linkid=836946)
- [小米應用商店](https://go.microsoft.com/fwlink/?linkid=836947)
- [騰訊](https://go.microsoft.com/fwlink/?linkid=836949)
- [華為](https://go.microsoft.com/fwlink/?linkid=836948)
- [豌豆莢](https://go.microsoft.com/fwlink/?linkid=836950)

### <a name="apple-to-require-updates-for-application-transport-security---748318--"></a>Apple 需要更新 Application Transport Security <!--748318-->

Apple 宣告，從 2017 年春季開始，將會強制執行 Application Transport Security (ATS) 的特定需求。 ATS 可用來對透過 HTTPS 進行的所有應用程式通訊，強制執行更嚴格的安全性。 這項變更會影響使用 iOS/macOS 公司入口網站應用程式的 Intune 客戶。 如需詳細資訊，請檢閱我們的 [Intune 支援部落格 (英文)](https://aka.ms/compportalats)。

## <a name="public-preview-of-the-new-intune-admin-experience-on-azure---736542--"></a>Azure 上新 Intune 管理體驗的公開預覽 <!--736542-->

在 2017 年初，我們會將完整管理體驗移轉到 Azure，以便在可透過圖形 API 擴充的新式服務平台上，對核心 EMS 工作流程進行強大的整合式管理。

新的試用租用戶將於本月開始看到 Azure 入口網站中新管理體驗的公開預覽。 在預覽狀態期間，將透過現有的 Intune 主控台反覆提供功能和同位檢查。

Azure 入口網站中的管理體驗將使用已宣佈的新群組和目標設定功能；當您現有的租用戶移轉至新的群組體驗時，也會同時將您移轉，以預覽您租用戶的新管理體驗。 在此同時，如果您想要在移轉租用戶之前測試或查看任何新功能，請註冊新的 Intune 試用帳戶或查看[新文件](https://docs.microsoft.com/en-us/intune-azure/introduction/what-is-microsoft-intune)。

如果您有任何關於租用戶移轉時間表的問題，請連絡我們的移轉團隊：[intunegrps@microsoft.com](mailto:intunegrps@microsoft.com)。

### <a name="non-managed-devices-can-access-assigned-apps---664691--"></a>未受管理的裝置可以存取已指派的應用程式 <!--664691-->

iOS 和 Android 使用者能夠在他們未受管理的裝置上，安裝指派給他們的「無須註冊即可使用」應用程式，這屬於公司入口網站的設計變更。 使用 Intune 認證，使用者能夠登入公司入口網站，並查看指派給他們的應用程式清單。 「無須註冊即可使用」應用程式的應用程式套件，可透過公司入口網站下載取得。 這項變更不會影響需要註冊才能安裝的應用程式，因為如果使用者想要安裝這些應用程式，系統會提示他們註冊裝置。

### <a name="improvements-to-device-actions-report---677150--"></a>裝置動作報告改善 <!--677150-->

我們改善了裝置動作報告以提升效能。 此外，您現在可以依狀態篩選報告。 例如，您可以篩選報告以僅顯示已完成的裝置動作。

### <a name="actions-for-non-compliance---730266--"></a>不符合規定時所採取的動作 <!--730266-->

**不符合規定時所採取的動作**是相容性原則的新功能，可讓您對不相容的裝置採取動作。 您可以指定單一或多個動作，並指定必須進行這些動作的時間週期。 例如，您可以在裝置變成不相容之後透過電子郵件立即通知使用者有不相容的裝置，也可以在 3 天寬限期之後透過條件式存取封鎖不相容的裝置存取公司資源。

### <a name="custom-app-categories---748805--"></a>自訂應用程式類別 <!--748805-->

您現在可以建立、編輯和指派您新增至 Intune 之應用程式的類別。 目前只能以英文指定類別。
請參閱[如何將應用程式新增至 Intune](/intune-azure/manage-apps/add-apps)。

### <a name="assign-lob-apps-to-users-with-unenrolled-devices---748823--"></a>指派 LOB 應用程式給使用未註冊裝置的使用者 <!--748823-->

您現在可以將市集中的企業營運應用程式指派給使用者，不論其裝置是否已向 Intune 註冊。 如果未向 Intune 註冊使用者裝置，則他們必須前往公司入口網站安裝它，而不是公司入口網站應用程式。

### <a name="new-compliance-reports---846671--"></a>新的合規性報告 <!--846671-->

您現在有可提供公司內裝置合規性狀態的合規性報告，並可以快速地針對使用者遇到的合規性相關問題進行疑難排解。 您可以檢視的資訊如下

- 整體的裝置合規性狀態
- 個別設定的合規性狀態
- 個別原則的合規性狀態

您也可以使用這些報告來向下鑽研個別裝置，以檢視影響該裝置的特定設定和原則。

### <a name="additional-windows-10-upgrade-paths---903672--"></a>其他 Windows 10 升級路徑 <!--903672-->

您現在可以建立版本升級原則，來將裝置升級為下列其他的 Windows 10 版本：

- Windows 10 Professional
- Windows 10 Professional N
- Windows 10 專業教育版
- Windows 10 專業教育版 N


### <a name="direct-access-to-apple-enrollment-scenarios---951869--"></a>直接存取 Apple 註冊案例 <!--951869-->

對於在 2017 年 1 月之後建立的 Intune 帳戶，Intune 已經啟用使用 Azure Preview 入口網站中的「註冊裝置」工作負載直接存取 Apple 註冊案例。 Apple 註冊預覽原本只能從傳統 Intune 入口網站中的連結存取。 在 2017 年 1 月之前建立的 Intune 帳戶，將需要進行一次性移轉，才能在 Azure 中使用這些功能。 移轉的排程尚未宣布，但將會盡快提供詳細資料。 如果您現有的帳戶無法存取預覽，我們強烈建議您建立試用帳戶來測試新的體驗。

### <a name="see-also"></a>請參閱
如需近期發展的詳細資料，請參閱 [Microsoft Intune 的新功能](whats-new-in-microsoft-intune.md)。


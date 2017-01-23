---
title: "舊版 | Microsoft Docs"
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 12/21/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 18d47678b0fbdbd98502f2d3b469b202b567b2e7
ms.openlocfilehash: 3c7edc236878232c6f4c0ae993733c967946e765


---

# <a name="the-early-edition-for-microsoft-intune---january"></a>Microsoft Intune 的舊版 - 1 月

**舊版**提供 Microsoft Intune 即將發行版本要推出的功能清單。 此資訊以非常有限的基礎在 NDA 下提供，並可能有所變更。 這裡列出的一些功能可能有截止日期，而且可能會延遲到未來的版本。 其他功能正在實驗 (測試) 中進行測試，以確保它們可供客戶使用。 如果你們有任何問題或疑慮，請洽詢 Intune/PM 人員。

此頁面會定期更新。 請回來查看其他更新。

> [!Note]
> 下列變更正在 Intune 的開發過程中。 混合式客戶部署於未來將會支援這些功能 (具備 Intune 的 Configuration Manager)。 如需新混合式功能的詳細資訊，請查看我們的 [Hybrid What’s New](https://docs.microsoft.com/en-us/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management) (混合式新功能) 頁面。

## <a name="new-capabilities"></a>新功能

### <a name="actions-for-non-compliance---730266--"></a>不符合規定時所採取的動作 <!--730266-->
_不符合規定時所採取的動作_是相容性原則的新功能，可讓您對不相容的裝置採取動作。 您可以指定單一或多個動作，並指定必須進行這些動作的時間週期。 例如，您可以在裝置變成不相容之後透過電子郵件立即通知使用者有不相容的裝置，也可以在 3 天寬限期之後透過條件式存取封鎖不相容的裝置存取公司資源。

### <a name="in-console-reports-for-mam-without-enrollment---677961--"></a>無裝置註冊之 MAM 的主控台內報表 <!--677961-->
已註冊的裝置和未註冊的裝置已新增新的應用程式保護報表。 在這裡深入了解如何[使用 Microsoft Intune 監視行動應用程式管理原則](https://docs.microsoft.com/en-us/intune/deploy-use/monitor-mobile-app-management-policies-with-microsoft-intune)。

### <a name="conditional-access-for-mam-with-sharepoint-online---679339--"></a>MAM 和 SharePoint Online 的條件存取 <!--679339-->
您可以禁止不受 Intune 行動應用程式管理 (MAM) 原則支援的應用程式存取 SharePoint Online。  您可以在 Azure 入口網站中使用 Intune 行動應用程式管理開始進行。 在包含 SharePoint Online 選項的 [設定] 刀鋒視窗中，尋找 [條件存取] 區段。 這項功能將與服務版本的其餘部分分開提供。 <!--Find out more about this new feature [here](https://docs.microsoft.com/intune/deploy-use/mam-ca-for-sharepoint-online).-->

### <a name="android-711-support---694397--"></a>Android 7.1.1 支援 <!--694397-->
Intune 現在完全支援和管理 Android 7.1.1。

## <a name="notices"></a>通知

### <a name="defaulting-to-managing-windows-desktop-devices-through-windows-settings---663050--"></a>預設為透過 Windows 設定管理 Windows Desktop 裝置 <!--663050-->
註冊 Windows 10 Desktop 的預設行為會變更。 新的註冊將會遵循一般 MDM 代理程式註冊流程，而不是透過電腦代理程式。

公司入口網站會提供 Windows 10 Desktop 使用者，有關引導他們新增 Windows 10 Desktop 電腦作為行動裝置之程序的註冊指示。 這不會影響目前已註冊的電腦，而且您的組織還是可以使用電腦代理程式來管理 Windows 10 Desktop，如[設定 Windows 裝置管理](https://docs.microsoft.com/en-us/intune/deploy-use/set-up-windows-device-management-with-microsoft-intune)中所述。

### <a name="company-portal-for-ios-links-open-inside-the-app---665954--"></a>適用於 iOS 的公司入口網站連結會在應用程式內開啟 <!--665954-->
適用於 iOS 的公司入口網站應用程式連結 (包括文件和應用程式的連結) 會使用 Safari 的應用程式內檢視直接在公司入口網站應用程式中開啟。 這項更新將在 1 月與服務更新分開提供。

### <a name="improving-mobile-app-management-support-for-selective-wipe---581242--"></a>改善選擇性抹除的行動應用程式管理支援 <!--581242-->
如果因 [離線間隔幾天後抹除 App 資料] 原則而自動移除工作或學校資料，則會將如何重新存取工作或學校資料的其他指引授與終端使用者。<!--, or the removal of the Intune Company Portal on Android.-->

### <a name="new-documentation-for-app-protection-policies---583398--"></a>應用程式保護原則的新文件 <!--583398-->
針對想要使用 Intune App Wrapping Tool 或 Intune App SDK 在 iOS 和 Android 應用程式中啟用應用程式保護原則 (稱為 MAM 原則) 的系統管理員和應用程式開發人員，我們已更新他們適用的文件。

已更新下列文章：

* [決定如何準備應用程式，以使用 Microsoft Intune 管理行動裝置應用程式](https://docs.microsoft.com/intune/deploy-use/decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune)
* [準備將 iOS 應用程式交由 Intune App Wrapping Tool 進行行動應用程式管理](https://docs.microsoft.com/intune/deploy-use/prepare-ios-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool)
* [開始使用 Microsoft Intune App SDK](https://docs.microsoft.com/intune/develop/intune-app-sdk-get-started)
* [Intune App SDK for iOS 開發人員指南](https://docs.microsoft.com/intune/develop/intune-app-sdk-ios)

下列文章是文件庫的新增項目︰

* [Intune App SDK Cordova 外掛程式](https://docs.microsoft.com/intune/develop/intune-app-sdk-cordova)
* [Intune App SDK Xamarin 元件](https://docs.microsoft.com/intune/develop/intune-app-sdk-xamarin)

### <a name="progress-bar-when-launching-the-company-portal-on-ios---665978--"></a>在 iOS 上啟動公司入口網站時的進度列 <!--665978-->
適用於 iOS 的公司入口網站會在啟動畫面上引進進度列，以將所發生之載入程序的相關資訊提供給使用者。 將會有進度列的階段性推出，來取代微調按鈕。 這表示部分使用者將會看到新的進度列，而其他人則會持續看見微調按鈕。

## <a name="public-preview-of-the-new-intune-admin-experience-on-azure---736542--"></a>Azure 上新 Intune 管理體驗的公開預覽 <!--736542-->

在 2017 年初，我們會將完整管理體驗移轉到 Azure，以便在可透過圖形 API 擴充的新式服務平台上，對核心 EMS 工作流程進行強大的整合式管理。

新的試用租用戶將於本月開始看到 Azure 入口網站中新管理體驗的公開預覽。 在預覽狀態期間，將透過現有的 Intune 主控台反覆提供功能和同位檢查。

Azure 入口網站中的管理體驗將使用已宣佈的新群組和目標設定功能；當您現有的租用戶移轉至新的群組體驗時，也會同時將您移轉，以預覽您租用戶的新管理體驗。 在此同時，如果您想要在移轉租用戶之前測試或查看任何新功能，請註冊新的 Intune 試用帳戶或查看[新文件](https://docs.microsoft.com/en-us/intune-azure/introduction/what-is-microsoft-intune)。

如果您有任何關於租用戶移轉時間表的問題，請連絡我們的移轉團隊：[intunegrps@microsoft.com](mailto:intunegrps@microsoft.com)。

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



<!--HONumber=Dec16_HO4-->



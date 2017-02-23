---
title: "新功能 | Microsoft Docs"
description: "了解本月 Microsoft Intune 版本的新功能，以及過去的版本"
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 02/07/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: fab51ee0-638d-4dd4-8d8f-1f263bc11e5c
ms.reviewer: cacampbell
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 053cf0a1b5d06496397b36cbd1a7ebdce420fed3
ms.openlocfilehash: 5158d58c32066ea720335a878fef87451542c195


---
# <a name="whats-new-in-microsoft-intune---january-2017"></a>Microsoft Intune 的新功能 - 2017 年 1 月
了解此 Microsoft Intune 版本中的新功能。 您也可以了解即將推出且您應該加以規劃的變更，以及過去版本的相關資訊。

> [!Note]
> 混合式客戶部署於未來將會支援這些功能 (具備 Intune 的 Configuration Manager)。 如需新混合式功能的詳細資訊，請查看我們的 [Hybrid What’s New](https://docs.microsoft.com/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management) (混合式新功能) 頁面。

## <a name="new-capabilities"></a>新功能

<!--### Actions for non-compliance <!--730266
_Actions for non-compliance_ is a new feature of compliance policies that lets you take action on devices that are out of compliance. You can specify single or multiple actions and specify the time period at which those actions must occur. For example, you can notify users of non-compliant devices immediately after the devices become non-compliant through email, or you can block non-compliant devices from accessing corporate resources after a 3-day grace period via Conditional Access.-->

### <a name="in-console-reports-for-mam-without-enrollment---677961--"></a>無裝置註冊之 MAM 的主控台內報表 <!--677961-->
已註冊的裝置和未註冊的裝置已新增新的應用程式保護報表。 在這裡深入了解如何[使用 Microsoft Intune 監視行動應用程式管理原則](https://docs.microsoft.com/intune/deploy-use/monitor-mobile-app-management-policies-with-microsoft-intune)。

<!--### Conditional access for MAM with SharePoint Online <!--679339
You can block apps that are not supported by Intune mobile app management (MAM) policies from accessing SharePoint Online.  You can get started using Intune mobile app management in the Azure portal. Look for the __Conditional Access__ section in the __Settings__ blade which will include the option for SharePoint Online. This feature will ship separately from the rest of the service release. <!--Find out more about this new feature [here](https://docs.microsoft.com/intune/deploy-use/mam-ca-for-sharepoint-online).-->

### <a name="android-711-support---694397--"></a>Android 7.1.1 支援 <!--694397-->
Intune 現在完全支援和管理 Android 7.1.1。

### <a name="resolve-issue-where-ios-devices-are-inactive-or-the-admin-console-cannot-communicate-with-them---unknown--"></a>解決 iOS 裝置處於非使用狀態或管理員主控台無法與它們通訊的問題 <!--unknown-->
當使用者的裝置與 Intune 失去連絡時，您可以提供新的疑難排解步驟，協助他們重新取得公司資源的存取權。 請參閱[裝置處於非使用狀態或管理員主控台無法與它們通訊](/intune/troubleshoot/troubleshoot-device-enrollment-in-intune#devices-are-inactive-or-the-admin-console-cannot-communicate-with-them)。

## <a name="notices"></a>通知

### <a name="defaulting-to-managing-windows-desktop-devices-through-windows-settings---663050--"></a>預設為透過 Windows 設定管理 Windows Desktop 裝置 <!--663050-->
註冊 Windows 10 Desktop 的預設行為會變更。 新的註冊將會遵循一般 MDM 代理程式註冊流程，而不是透過電腦代理程式。

公司入口網站會提供 Windows 10 Desktop 使用者，有關引導他們新增 Windows 10 Desktop 電腦作為行動裝置之程序的註冊指示。 這不會影響目前已註冊的電腦，而且您的組織還是可以使用電腦代理程式來管理 Windows 10 Desktop，如[設定 Windows 裝置管理](https://docs.microsoft.com/intune/deploy-use/set-up-windows-device-management-with-microsoft-intune)中所述。

<!--### Company Portal for iOS links open inside the app <!--665954
Links inside of the Company Portal app for iOS, including those to documentation and apps, will open directly in the Company Portal app using an in-app view of Safari. This update will ship separately from the service update in January.-->

### <a name="improving-mobile-app-management-support-for-selective-wipe---581242--"></a>改善選擇性抹除的行動應用程式管理支援 <!--581242-->
如果因 [離線間隔幾天後抹除 App 資料] 原則而自動移除工作或學校資料，則會將如何重新存取工作或學校資料的其他指引授與終端使用者。<!--, or the removal of the Intune Company Portal on Android.-->

### <a name="company-portal-for-ios-links-open-inside-the-app---665954--"></a>適用於 iOS 的公司入口網站連結會在應用程式內開啟 <!--665954-->
適用於 iOS 的公司入口網站應用程式連結 (包括文件和應用程式的連結) 會使用 Safari 的應用程式內檢視直接在公司入口網站應用程式中開啟。 這項更新將在&1; 月與服務更新分開提供。

### <a name="modernizing-the-company-portal-website---753980--"></a>現代化公司入口網站 <!--753980-->
從&2; 月開始，公司入口網站將支援以沒有受管理裝置的使用者為目標的應用程式。 網站會與其他 Microsoft 產品和服務一致，方法是使用新的對比色彩配置、動態圖例和「漢堡功能表」：![公司入口網站漢堡功能表](./media/CP_hamburger_menu.png)，其包含技術服務連絡人詳細資料以及現有受管理裝置的相關資訊。 登陸頁面將會予以重新排列，以透過 [精選和最近更新] 應用程式的浮動切換來強調使用者可用的應用程式。 您可以在 [What's new in the Company Portal UI page](https://docs.microsoft.com/intune/whats-new/whats-new-in-intune-app-ui#January_2017) (公司入口網站 UI 頁面的新功能) 上找到新版與舊版的映像。

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

<!--### Progress bar when launching the Company Portal on iOS <!--665978
The Company Portal for iOS is introducing a progress bar on the launch screen to provide the user with information about the loading processes that occur. There will be a phased rollout of the progress bar to replace the spinner. This means that some of your users will see the new progress bar while others will continue to see the spinner.-->

### <a name="progress-bar-when-launching-the-company-portal-on-ios---665978--"></a>在 iOS 上啟動公司入口網站時的進度列 <!--665978-->
適用於 iOS 的公司入口網站會在啟動畫面上引進進度列，以將所發生之載入程序的相關資訊提供給使用者。 將會有進度列的階段性推出，來取代微調按鈕。 這表示部分使用者將會看到新的進度列，而其他人則會持續看見微調按鈕。

## <a name="whats-new-in-the-public-preview-of-the-intune-admin-experience-on-azure---736542--"></a>Azure 的 Intune 管理體驗公開預覽新功能<!--736542-->

在 2017 年初，我們會將完整管理體驗移轉到 Azure，以便在可透過圖形 API 擴充的新式服務平台上，對核心 EMS 工作流程進行強大的整合式管理。

新的試用租用戶將於本月開始看到 Azure 入口網站中新管理體驗的公開預覽。 在預覽狀態期間，將透過現有的 Intune 主控台反覆提供功能和同位檢查。

Azure 入口網站中的管理體驗將使用已宣佈的新群組和目標設定功能；當您現有的租用戶移轉至新的群組體驗時，也會同時將您移轉，以預覽您租用戶的新管理體驗。 在此同時，如果您想要在移轉租用戶之前測試或查看任何新功能，請註冊新的 Intune 試用帳戶或查看[新文件](https://docs.microsoft.com/intune-azure/introduction/what-is-microsoft-intune)。

如果您有任何關於租用戶移轉時間表的問題，請連絡我們的移轉團隊：[intunegrps@microsoft.com](mailto:intunegrps@microsoft.com)。

您可以在[這裡](https://docs.microsoft.com/intune-azure/introduction/whats-new)找到 Azure 的 Intune 預覽新功能。

### <a name="see-also"></a>請參閱
* [Microsoft Intune 部落格](http://go.microsoft.com/fwlink/?LinkID=273882)
* [雲端平台藍圖](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)
* [Azure 預覽的新功能](https://docs.microsoft.com/intune-azure/introduction/whats-new)
* [公司入口網站 UI 的新功能](https://docs.microsoft.com/intune/whats-new/whats-new-in-company-portal-ui)
* [新功能封存](whats-new-archive.md)



<!--HONumber=Feb17_HO1-->



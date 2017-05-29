---
title: "舊版 | Microsoft Docs"
description: 
keywords: 
author: mtillman
ms.author: mtillman
manager: angrobe
ms.date: 05/04/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 249a902e6e10f799dcff4e1c46da90cd62f2c125
ms.contentlocale: zh-tw
ms.lasthandoff: 05/23/2017


---

# <a name="the-early-edition-for-microsoft-intune---may-2017"></a>Microsoft Intune 的舊版 - 2017 年 5 月

**舊版**提供 Microsoft Intune 即將發行版本要推出的功能清單。 此資訊以非常有限的基礎在 NDA 下提供，並可能有所變更。 這裡列出的一些功能可能有截止日期，而且可能會延遲到未來的版本。 其他功能正在實驗 (測試) 中進行測試，以確保它們可供客戶使用。 如果你們有任何問題或疑慮，請洽詢 Intune/PM 人員。

此頁面會定期更新。 請回來查看其他更新。

> [!Note]
> 下列變更正在 Intune 的開發過程中。 混合式客戶部署於未來將會支援這些功能 (具備 Intune 的 Configuration Manager)。 如需新混合式功能的詳細資訊，請查看我們的[混合式新增功能](https://docs.microsoft.com/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management)頁面。

## <a name="new-capabilities"></a>新功能

### <a name="single-sign-on-support-from-the-company-portal-for-ios-to-outlook-for-ios---834012--"></a>從 iOS 版入口網站到 iOS 版 Outlook 的單一登入 <!--834012-->

如果使用者在同一部裝置上使用相同的帳戶登入 iOS 版公司入口網站應用程式，他們將不必再登入 Outlook 應用程式。 當使用者啟動 Outlook 應用程式時，將能夠選取其帳戶並自動登入。 我們也將努力為其他 Microsoft 應用程式新增這項功能。

### <a name="improved-notification-for-samsung-knox-startup-pins---1087143--"></a>已改進 Samsung KNOX 啟動 PIN 的通知 <!--1087143-->

當使用者需要在 Samsung KNOX 裝置上設定啟動 PIN 以符合加密條件時，點選對使用者顯示的通知會將他們引導至 [設定] 應用程式中的確切位置。  先前的通知會將使用者引導至密碼變更畫面。

### <a name="promoting-the-most-current-version-of-the-company-portal-for-android---1098661--"></a>宣傳 Android 版公司入口網站的最新版本 <!--1098661-->

當有 Android 版公司入口網站應用程式的新建議版本推出時，使用者會在應用程式的 [通知] 畫面看到應用程式內通知。 此通知會告知使用者「有可用的公司入口網站更新」。 點選通知會開啟網頁，顯示使用者可用來下載更新版本的應用程式商店清單。 

### <a name="improvements-to-app-syncing-with-windows-10-creators-update----676505---"></a>透過 Windows 10 Creators Update 改進應用程式同步<!-- 676505 -->

Windows 10 版公司入口網站會針對具有 Windows 10 Creators Update (1704) 之裝置的應用程式安裝要求，自動初始化同步處理。 這會減少應用程式安裝在「待同步」狀態期間出現拖延的問題。 此外，使用者將能夠從應用程式內手動起始同步。 

Windows 10 版公司入口網站也會公開重新整理按鈕，以允許使用者視需要重新整理應用程式中的內容。 

## <a name="notices"></a>通知

### <a name="apple-to-require-updates-for-application-transport-security---748318--"></a>Apple 需要更新 Application Transport Security <!--748318-->

Apple 宣布，從 2017 年春季開始，將會強制執行 Application Transport Security (ATS) 的特定需求。 ATS 可用來對透過 HTTPS 進行的所有應用程式通訊，強制執行更嚴格的安全性。 此變更會影響使用 iOS 公司入口網站應用程式的 Intune 客戶。 如需詳細資訊，請檢閱我們的 [Intune 支援部落格](https://aka.ms/compportalats)。

### <a name="direct-access-to-apple-enrollment-scenarios---951869--"></a>直接存取 Apple 註冊案例 <!--951869-->

對於在 2017 年 1 月之後建立的 Intune 帳戶，Intune 已經啟用使用 Azure Preview 入口網站中的「註冊裝置」工作負載直接存取 Apple 註冊案例。 Apple 註冊預覽原本只能從傳統 Intune 入口網站中的連結存取。 在 2017 年 1 月之前建立的 Intune 帳戶，將需要進行一次性移轉，才能在 Azure 中使用這些功能。 移轉的排程尚未宣布，但將會盡快提供詳細資料。 如果您現有的帳戶無法存取預覽，我們強烈建議您建立試用帳戶來測試新的體驗。

### <a name="whats-coming-for-appx-in-intune-on-azure----1000270---"></a>Appx 在 Azure 上的 Intune 中的未來動態 <!-- 1000270 -->

在移轉到 Azure 上的 Intune 的過程中，我們將進行三個 appx 變更：

1. 在傳統 Intune 主控台中，新增只能部署到 MDM 註冊裝置的 appx 應用程式類型。
2. 重新規劃現有的 appx 應用程式類型，將目標僅限於透過 Intune PC 代理程式管理的電腦。
3. 透過移轉，將所有現有的 appxs 轉換成 MDM appxs。

這不會影響透過 Intune PC 代理程式管理之裝置上的任何現有部署。 不過移轉之後，您無法將這些移轉的 appxs 部署到透過 Intune PC 代理程式管理但先前未設為目標的任何新裝置。

移轉之後，如果您想要執行新的 PC 部署，您將必須再次重新上傳 appx 作為 PC 的 appx。 若要深入了解，請參閱 Intune 支援小組部落格上的 [Appx changes in Intune on Azure](https://aka.ms/appxchange) (Azure 上的 Intune 中的 Appx 變更)。  


## <a name="public-preview-of-the-new-intune-admin-experience-on-azure---736542--"></a>Azure 上新 Intune 管理體驗的公開預覽 <!--736542-->

在 2017 年初，我們會將完整管理體驗移轉到 Azure，以便在可透過圖形 API 擴充的新式服務平台上，對核心 EMS 工作流程進行強大的整合式管理。

新的試用租用戶將於本月開始看到 Azure 入口網站中新系統管理體驗的公開預覽。 在預覽狀態期間，將提供與現有 Intune 主控台相同與相當的功能。

Azure 入口網站中的系統管理體驗將使用已宣佈的新分組和目標設定功能；當您現有的租用戶移轉至新的分組體驗時，也會同時將您移轉，以預覽您租用戶的新系統管理體驗。 在此同時，如果您想要在移轉租用戶之前測試或查看任何新功能，請註冊新的 Intune 試用帳戶或查看[新文件](https://docs.microsoft.com/intune/what-is-intune)。

### <a name="support-for-managed-configuration-options-for-android-apps----621621---"></a>支援 Android 應用程式的受管理設定選項 <!-- 621621 -->

您將能夠設定 Play 商店中支援受管理設定選項的 Android 應用程式。  這項功能可讓您檢視應用程式所支援的設定值清單，並提供頂級的引導式 UI 以設定那些值。

### <a name="remote-assistance-for-android-devices----675418---"></a>Android 裝置的遠端協助 <!-- 675418 -->

Intune 將會使用另行購買的 [TeamViewer](https://www.teamviewer.com) 軟體，讓您為執行 Android 裝置的使用者提供遠端協助。

### <a name="preconfigure-device-permissions-for-android-for-work-apps----621614---"></a>預先設定 Android for Work 應用程式的裝置權限 <!-- 621614 -->

對於部署到 Android for Work 裝置工作設定檔的應用程式，您將能夠設定個別應用程式的權限狀態。 根據預設，需要裝置權限 (例如存取位置或裝置相機) 的 Android 應用程式會提示使用者接受或拒絕授與權限。  例如，若應用程式會使用裝置的麥克風，則系統會提示使用者授與應用程式使用麥克風的權限。 此功能可讓您代表使用者定義權限。  系統管理員可以將權限設為

- 自動拒絕且不通知使用者
- 自動核准且不通知使用者
- 提示使用者接受或拒絕。

### <a name="define-app-specific-pin-for-android-for-work-devices---728976--"></a>針對 Android for Work 裝置定義應用程式特定的 PIN <!--728976-->

您將能夠定義僅適用於做為 Android for Work 裝置進行管理的 Android 7.0 或更新版本裝置工作設定檔中之應用程式的密碼原則。  這些選項包括：

- 僅定義全裝置密碼原則：這是使用者必須用來解鎖整個裝置的密碼
- 僅定義工作設定檔密碼原則：每當開啟工作設定檔中的應用程式時，系統就會提示使用者輸入密碼。
- 定義裝置和工作設定檔原則：IT 人員可定義具有不同強度的裝置密碼原則和工作設定檔密碼原則 (例如，使用 4 位數 PIN 來解鎖裝置，但必須使用 6 位數 PIN 來開啟任何工作應用程式)

>[!NOTE]
> 此功能僅適用於 Android 7.0 及更新版本。  根據預設，使用者能選擇使用這兩個個別定義的 PIN，或選擇結合這兩個定義的 PIN，並使用兩者中最強的一個。

### <a name="manage-password-and-other-android-for-work-settings---1102534--"></a>管理密碼和其他 Android for Work 設定 <!--1102534-->

我們正在加入新的 Android for Work 裝置限制原則，讓您可在 Android for Work 裝置上管理密碼和工作設定檔設定。

###  <a name="new-web-content-filter-policy-for-ios-devices----723832---"></a>適用於 iOS 裝置的新網路內容篩選原則 <!-- 723832 -->

您將能夠使用下列兩種方法，來控制 iOS 裝置使用者可以瀏覽的網站：

  - 使用 Apple 內建網路內容篩選器新增允許和封鎖的 URL。
  - 僅允許 Safari 瀏覽器存取指定的網站。 針對您指定的每個網站，會在 Safari 中建立書籤。

### <a name="apple-school-manager-asm-support---748864--"></a>Apple School Manager (ASM) 支援 <!--748864-->

Intune 將支援以 Apple School Manager (ASM) 取代 Apple 裝置註冊計劃，來為 iOS 裝置提供全新註冊功能。 下列兩種情況皆需要 ASM 上線：在「共用的 iPad」上使用 Classroom 應用程式，以及透過 Microsoft 學校資料同步處理 (SDS) 將資料從 ASM 同步到 Azure Active Directory。  

### <a name="shared-ipad-support---770395-1044681---"></a>共用的 iPad 支援 <!--770395, 1044681 -->

Intune 將支援在「Apple 的裝置註冊計劃」或「Apple School Manager」的註冊設定檔中設定「共用的 iPad」模式。 此設定可讓多個受管理的 Apple ID 登入同一部裝置。

我們也會擴充對管理 iOS Classroom 應用程式的支援，以包含使用受管理 Apple ID 登入共用 iPad 的學生。

### <a name="new-windows-device-restriction-settings---978585--"></a>新的 Windows 裝置限制設定 <!--978585-->

我們準備將可控制數種功能 (例如無線顯示器、裝置探索、工作切換和 SIM 卡錯誤訊息) 的設定新增至 Windows 裝置限制設定檔。

### <a name="office-365-proplus-app-available-for-windows-10-devices---1121362--"></a>適用於 Windows 10 裝置的 Office 365 專業增強版應用程式 <!--1121362-->

我們準備加入新的 Office 365 專業增強版應用程式類型，可讓您輕鬆地將 Office 365 專業增強版應用程式指派給 Windows 10 裝置。 此外，如果您有 Microsoft Project 或 Microsoft Visio 的授權，將也能安裝它們。 您想要的應用程式將會配套在一起，並以單一應用程式的形式出現在 Intune 主控台的應用程式清單中。

### <a name="new-allowblock-list-for-the-managed-browser---682960--"></a>適用於 Managed Browser 的新允許/封鎖清單 <!--682960-->

您將能夠使用 Azure 入口網站中的「Intune 應用程式組態」設定，來設定 Managed Browser 的網域和 URL 允許/封鎖清單。 不論 Managed Browser 是用於受管理或未受管理的裝置上，都適用此設定。

### <a name="new-app-configuration-capabilities----677969---"></a>新的應用程式設定功能 <!-- 677969 -->

此功能相當於行動裝置管理 (MDM) 應用程式設定。 它能在沒有註冊通道的情況下，讓系統管理員在 MAM 中套用比應用程式保護原則所提供的應用程式設定值還要多的應用程式設定值。

### <a name="new-app-protection-policies-conditions-for-mam---679864--"></a>適用於 MAM 的新應用程式保護原則條件 <!--679864-->

您將可以在無需透過管理主控台註冊使用者的情況下，設定能強制執行下列項目的 MAM 需求：

- 對低應用程式版本
- 最低作業系統版本
- 目標應用程式的最低 Intune APP SDK 版本 (僅限 iOS)

這項功能將會在 Android 和 iOS 上提供。 Intune 支援作業系統平台版本、應用程式版本，以及 Intune APP SDK 的最低版本強制。 在 iOS 上，已整合 SDK 的應用程式也可以設定 SDK 層級的最低版本強制。

如果沒有符合應用程式保護原則於上述 3 個不同層級的最低需求，使用者將無法存取目標應用程式。 此時，使用者可以選擇移除其帳戶 (適用於多重身分識別應用程式)、關閉該應用程式，以及/或更新作業系統或應用程式版本以符合需求。

此外，您也能夠透過管理主控台設定其他設定，以提供能建議使用者進行作業系統或應用程式升級的非封鎖式通知。 使用者可以關閉此通知，並繼續正常地使用應用程式。

### <a name="change-your-mdm-authority-without-unenrolling-managed-devices---1103950--"></a>在不取消註冊受管理裝置的情況下變更 MDM 授權單位 <!--1103950-->

您將可以在不需要連絡 Microsoft 支援服務的情況下變更 MDM 授權單位，且不需要取消註冊並重新註冊您現有的受管理裝置。 在 Configuration Manager 主控台中，您可以將 [MDM 授權單位] 從 [設定為 Configuration Manager (混合式)] 變更為 [Microsoft Intune (獨立)]，反之亦然。


### <a name="see-also"></a>請參閱
如需近期發展的詳細資料，請參閱 [Microsoft Intune 的新功能](whats-new-in-microsoft-intune.md)。


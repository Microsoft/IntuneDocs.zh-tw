---
title: "Microsoft Intune 的新功能"
titleSuffix: Intune on Azure
description: "了解 Intune Azure 入口網站中的新功能"
keywords: 
author: brenduns
ms.author: brenduns
manager: angrobe
ms.date: 08/01/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 791ed23f-bd13-4ef0-a3dd-cd2d7332c5cc
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: c27ce82d10b927fdecec3ea2952376dc7b1f792e
ms.sourcegitcommit: 79116d4c7f11bafc7c444fc9f5af80fa0b21224e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/03/2017
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
-->   

## <a name="week-of-july-31-2017"></a>2017 年 7 月 31 日一週

### <a name="ui-updates-to-the-company-portal-website---1313244-part-1--"></a>公司入口網站的 UI 更新 <!--1313244 part 1-->
我們對[公司入口網站](https://portal.manage.microsoft.com)的 UI 進行了數項更新，以增強終端使用者體驗。

__應用程式磚的增強功能__：小於 79x79 像素的應用程式圖示現在會根據圖示的主要色彩來顯示自動產生的背景。 這會取代先前在含有小圖示的應用程式磚上顯示的灰色框線。 較大的圖示會調整大小以盡可能填滿應用程式磚，同時維持影像品質。

建議 IT 系統管理員使用大小下限為 120 x120 像素的圖示來發佈應用程式。

__導覽變更__：導覽列項目已移至左上方的漢堡功能表。 已移除 [類別] 頁面。 使用者現在可以在瀏覽時依類別篩選內容。

### <a name="improved-sign-in-experience-across-company-portal-apps-for-all-platforms---user-story-1132123--"></a>改善適用於所有平台的公司入口網站應用程式登入體驗 <!--User Story 1132123-->

我們宣布將在幾個月內推出變更，以改進 Android、iOS 和 Windows 版 Intune 公司入口網站應用程式的登入體驗。 當 Azure AD 進行此變更時，新的使用者體驗會自動顯示在所有平台的公司入口網站應用程式上。 此外，使用者現在可以使用產生的一次性驗證碼，從另一部裝置登入公司入口網站。 在使用者需要不使用認證登入的情況下，這特別有用。

若要查看先前的登入體驗、使用認證的新登入體驗及從另一部裝置登入的新登入體驗的螢幕擷取畫面，請參閱[應用程式 UI 的新功能](/intune/whats-new-app-ui)。


## <a name="week-of-july-23rd-2017"></a>2017 年 7 月 23 日一週

### <a name="light-and-dark-modes-available-for-the-company-portal-app-for-windows-10----676547---"></a>Windows 10 的公司入口網站應用程式提供日間和夜間模式<!---676547--->
使用者可以自訂 Windows 10 公司入口網站應用程式的色彩模式。 使用者可在公司入口網站應用程式的 [設定] 區段中進行變更。 使用者重新啟動應用程式後，即會看到變更。 至於 Windows 10 版本 1607 及更新版本，應用程式模式會預設為系統設定。 至於 Windows 10 版本 1511 及更新版本，應用程式模式會預設為日間模式。

### <a name="enable-end-users-to-tag-their-device-group-in-the-company-portal-app-for-windows-10----807046--"></a>讓使用者在 Windows 10 的公司入口網站應用程式中標記其裝置群組<!---807046-->
終端使用者現在可以直接在 Windows 10 公司入口網站應用程式中標記群組，選取其裝置所屬群組。

## <a name="week-of-june-26th-2017"></a>2017 年 6 月 26 日一週

### <a name="role-based-access-control"></a>以角色為基礎的存取控制
#### <a name="new-role-based-administration-access-for-intune-admins------1099990---"></a>適用於 Intune 管理員的全新且以角色為基礎的系統管理存取權 <!-- 1099990 -->  
新增條件式存取管理員角色，來檢視、建立、修改及刪除 Azure AD 條件式存取原則。 先前只有全域管理員和安全性管理員具有此權限。 您可以為 Intune 管理員授與此角色權限，讓他們具有條件式存取原則的存取權。


### <a name="device-enrollment"></a>裝置註冊
#### <a name="tag-corporate-owned-devices-with-serial-number----1215070---"></a>使用序號標記屬公司擁有的裝置 <!-- 1215070 -->  
Intune 現在支援上傳 iOS、macOS 和 Android 序號以作為公司裝置識別碼。 您無法使用序號來封鎖個人裝置進行註冊，因為在註冊期間不會驗證序號。 依序號封鎖個人裝置，將在不久的未來推出。


### <a name="device-management"></a>裝置管理
#### <a name="new-remote-actions-for-ios-devices----854689---"></a>適用於 iOS 裝置的新遠端動作<!-- 854689 -->
在此版本中，我們為用於管理 Apple Classroom 的共用 iPad 裝置新增了兩個遠端裝置動作：

-   [登出目前的使用者](device-logout-user.md) - 會登出您所選擇之 iOS 裝置的目前使用者。
-   [移除使用者](device-remove-user.md) - 會從 iOS 裝置的本機快取中刪除您選擇的使用者。


#### <a name="support-for-shared-ipads-with-the-ios-classroom-app----1044681---"></a>使用 iOS Classroom 應用程式支援共用的 iPad <!-- 1044681 -->
在此版本中，我們擴充了對管理 iOS Classroom 應用程式的支援，以包含使用受管理 Apple ID 登入共用 iPad 的學生。


### <a name="app-management"></a>應用程式管理  

#### <a name="changes-to-intune-built-in-apps----1332306---"></a>Intune 內建應用程式的變更 <!-- 1332306 -->

原本，Intune 包含許多您可以快速指派的內建應用程式。 應客戶的意見反應，我們已移除此清單，而您不會再看到內建應用程式。
不過，您已指派的任何內建應用程式仍會顯示在應用程式清單中。 若有需要，您可以繼續指派這些應用程式。
在之後的版本中，我們計畫新增一個方法，讓從 Intune 入口網站選取及指派內建應用程式的流程變得更輕鬆。

#### <a name="easier-installation-of-office-365-apps-----1121362----"></a>安裝 Office 365 應用程式更輕鬆<!--- 1121362 --->
新的 **Office 365 ProPlus** 應用程式類型可讓您輕鬆地將 Office 365 ProPlus 2016 應用程式指派給您管理的執行最新版 Windows 10 的裝置。 此外，如果您有 Microsoft Project 或 Microsoft Visio 的授權，也可以安裝它們。 您想要的應用程式會配套在一起，並以單一應用程式的形式出現在 Intune 主控台的應用程式清單中。
如需詳細資訊，請參閱[如何新增適用於 Windows 10 的 Office 365 應用程式](apps-add-office365.md)。


#### <a name="support-for-offline-apps-from-the-windows-store-for-business-----777044----"></a>支援來自商務用 Windows 市集的離線應用程式 <!--- 777044 --->
您購買自商務用 Windows 市集的離線應用程式現在將能同步處理至 Intune 入口網站。 您接著可將這些應用程式部署至裝置群組或使用者群組。 離線應用程式會透過 Intune 安裝，而不透過市集。

#### <a name="microsoft-teams-is-now-part-of-the-app-based-ca-list-of-approved-apps------1257019---"></a>Microsoft 小組現在是以應用程式為基礎的已核准應用程式 CA 清單的一部分<!-- 1257019 -->

適用於 iOS 和 Android 的 Microsoft Teams 應用程式，現在是針對適用於 Exchange 和 SharePoint Online 之以應用程式為基礎的條件式存取原則核准的應用程式一部分。 可以透過 Azure 入口網站中的 [Intune 應用程式防護] 刀鋒視窗，使用以應用程式為基礎的條件式存取，將應用程式設定為所有租用戶。

#### <a name="managed-browser-and-app-proxy-integration----1287310---"></a>受管理的瀏覽器和應用程式 Proxy 整合<!-- 1287310 -->
 Intune Managed Browser 現在可以整合 Azure AD Application Proxy 服務，讓使用者即使在遠端工作時也能存取內部網路網站。 瀏覽器的使用者只需和平常一樣輸入網站 URL，Managed Browser 便會透過應用程式 Proxy Web 閘道來路由傳送要求。 如需詳細資訊，請參閱[使用 Managed Browser 原則管理網際網路存取](app-configuration-managed-browser.md)。


#### <a name="new-app-configuration-settings-for-the-intune-managed-browser----682951---"></a>適用於 Intune Managed Browser 的新應用程式組態設定 <!-- 682951 -->
在此版本中，我們已新增 iOS 和 Android 的 Intune Managed Browser 應用程式的進一步設定。 您現在能使用應用程式設定原則，針對瀏覽器設定預設的首頁和書籤。
如需詳細資訊，請參閱[使用 Managed Browser 原則管理網際網路存取](app-configuration-managed-browser.md)




### <a name="device-configuration"></a>裝置設定  
#### <a name="bitlocker-settings-for-windows-10-----951707---"></a>Windows 10 的 BitLocker 設定 <!-- 951707 -->
您現在可以使用新的 Intune 裝置設定檔，設定 Windows 10 裝置的 BitLocker 設定。 例如，您可以要求裝置加密，也可以設定在開啟 BitLocker 時套用的進一步設定。
如需詳細資訊，請參閱 [Windows 10 和更新版本的 Endpoint Protection 設定](endpoint-protection-windows-10.md)。

### <a name="new-settings-for-windows-10-device-restriction-profile-----978527--978550-978569-1050031-1058611-----"></a>適用於 Windows 10 裝置限制設定檔的新設定 <!--- 978527,  978550, 978569, 1050031, 1058611,  --->

在此版本中，我們已新增 Windows 10 裝置限制設定檔的新設定，在下列類別中：

-  Windows Defender
-  行動數據與連線
-  鎖定畫面體驗
-  隱私權
-  搜尋
-  Windows 焦點
-  Edge 瀏覽器

如需 Windows 10 設定的詳細資訊，請參閱 [Windows 10 和更新版本的裝置限制設定](device-restrictions-windows-10.md)。

## <a name="week-of-june-12-2017"></a>2017 年 6 月 12 日一週

### <a name="company-portal-app-for-android-now-has-a-new-end-user-experience-for-app-protection-policies---1305217--"></a>Android 公司入口網站應用程式的應用程式保護原則現在有了新的使用者體驗<!--1305217-->
根據客戶的意見反應，我們已修改 Android 公司入口網站應用程式，以顯示 [存取公司內容] 按鈕。 目的是為了防止終端使用者在他們只需要存取支援應用程式保護原則 (Intune 行動應用程式管理的一項功能) 的應用程式時，不必要地進行註冊程序。 您可以在[應用程式 UI 的新功能](whats-new-app-ui.md)頁面看到這些變更。

### <a name="new-menu-action-to-easily-remove-company-portal---1164569--"></a>新的功能表動作，可輕鬆地移除公司入口網站<!--1164569-->
根據使用者意見反應，Android 版公司入口網站應用程式已新增功能表動作，可從裝置起始公司入口網站的移除。 這個動作會從 Intune 管理移除裝置，讓使用者可以從裝置移除應用程式。 您可以在[應用程式 UI 的新功能](whats-new-app-ui.md)頁面和 [Android 使用者文件](/intune-user-help/unenroll-your-device-from-intune-android)中看到這些變更。

### <a name="improvements-to-app-syncing-with-windows-10-creators-update---676505--"></a>透過 Windows 10 Creators Update 改進應用程式同步<!--676505-->

Windows 10 版公司入口網站應用程式現在會針對具有 Windows 10 Creators Update (版本 1703) 之裝置的應用程式安裝要求，自動初始化同步處理。 這會減少應用程式安裝在「待同步」狀態期間出現拖延的問題。 此外，使用者將能夠從應用程式內手動起始同步。 您可以在[應用程式 UI 的新功能](whats-new-app-ui.md)頁面看到這些變更。

### <a name="new-guided-experience-for-windows-10-company-portal----1058938---"></a>Windows 10 公司入口網站新型引導式體驗 <!---1058938--->

Windows 10 的公司入口網站應用程式將包含之前尚未確定或註冊之裝置的引導式 Intune 逐步解說體驗。 此全新體驗提供逐步指示，引導使用者向 Azure Active Directory 註冊 (條件式存取功能所需)，以及 MDM 註冊 (裝置管理功能所需)。 此引導式體驗將可從公司入口網站首頁上存取。 如果使用者無法完成註冊，他們可以繼續使用該應用程式，但將經歷有限的功能。

此更新只會顯示在執行 Windows 10 年度更新版 (組建 1607) 或更高版本的裝置上。 您可以在[應用程式 UI 的新功能](whats-new-app-ui.md)頁面看到這些變更。

## <a name="week-of-june-5-2017"></a>2017 年 6 月 5 日一週

### <a name="microsoft-intune-and-conditional-access-admin-consoles-are-generally-available"></a>Microsoft Intune 和條件式存取管理主控台正式推出

我們宣佈推出 Azure 管理主控台上的新 Intune 和條件式存取管理主控台。 透過 Azure 上的 Intune，您現在可以將所有 Intune MAM 與 MDM 功能合併管理，並妥善利用 Azure AD 群組和目標設定功能。 Azure 中的條件式存取跨 Azure AD 和 Intune，將豐富的功能整合在一個統一主控台。 從系統管理經驗的觀點，移至 Azure 平台可讓您使用新式瀏覽器。

您現在可以在 Azure 主控台 (portal.azure.com) 中看到沒有**預覽**標籤的 Intune。

除非您在訊息中心收到的一系列訊息中，有要求您採取動作來移轉群組的訊息，否則現有的客戶目前不需採取任何動作。 您可能也會收到訊息中心通知，說明因為我們這一端有錯誤而使移轉需要較長的時間。 我們會努力繼續移轉任何受影響的客戶。

### <a name="improvements-to-the-app-tiles-in-the-company-portal-app-for-ios"></a>iOS 版公司入口網站應用程式中應用程式磚的增強功能
我們已更新首頁上應用程式磚的設計，以反映您為公司入口網站設定的商標色彩。 如需詳細資訊，請參閱[應用程式 UI 的新功能](whats-new-app-ui.md)。

### <a name="account-picker-now-available-for-the-company-portal-app-for-ios"></a>iOS 版公司入口網站應用程式現在有帳戶選擇器可供使用
如果 iOS 裝置的使用者使用其工作或學校帳戶登入其他 Microsoft 應用程式，當他們登入公司入口網站時，可能會看到新的帳戶選擇器。 如需詳細資訊，請參閱[應用程式 UI 的新功能](whats-new-app-ui.md)。

## <a name="week-of-may-29-2017"></a>2017 年 5 月 29 日一週

### <a name="change-your-mdm-authority-without-unenrolling-managed-devices---1103950--"></a>在不取消註冊受管理裝置的情況下變更 MDM 授權單位 <!--1103950-->

您現在可以在不需要連絡 Microsoft 支援服務的情況下變更 MDM 授權單位，且不需要取消註冊並重新註冊您現有的受管理裝置。 在 Configuration Manager 主控台中，您可以將 [MDM 授權單位](/sccm/mdm/deploy-use/change-mdm-authority)從 [設定為 Configuration Manager] \(混合式\) 變更為 [Microsoft Intune] \(獨立\)，反之亦然。


### <a name="improved-notification-for-samsung-knox-startup-pins---1087143--"></a>已改進 Samsung KNOX 啟動 PIN 的通知 <!--1087143-->
當使用者需要在 Samsung KNOX 裝置上設定啟動 PIN 以符合加密規範時，點選對使用者顯示的通知會將他們引導至 [設定] 應用程式中的確切位置。  先前的通知會將使用者引導至密碼變更畫面。


### <a name="device-enrollment"></a>裝置註冊

#### <a name="apple-school-manager-asm-support-with-shared-ipad----748864-770395--"></a>對於共用 iPad 的 Apple School Manager (ASM) 支援<!-- 748864, 770395-->

Intune 現在支援以 Apple School Manager (ASM) 取代 Apple 裝置註冊計劃，來為 iOS 裝置提供全新註冊功能。 下列兩種情況皆需要 ASM 上線：在「共用的 iPad」上使用 Classroom 應用程式，以及透過 Microsoft 學校資料同步處理 (SDS) 將資料從 ASM 同步到 Azure Active Directory。 如需詳細資訊，請參閱[使用 Apple School Manager 啟用 iOS 裝置註冊](apple-school-manager-set-up-ios.md)。

> [!NOTE]
> 若要設定共用的 iPad 搭配 Classroom 應用程式使用，需要在 Azure 中設定 iOS Education，而此功能目前尚未提供。  此功能將於不久後加入。

### <a name="device-management"></a>裝置管理

#### <a name="provide-remote-assistance-to-android-devices-using-teamviewer----675418---"></a>使用 TeamViewer 對 Android 裝置提供遠端協助<!-- 675418 -->

Intune 現在可使用 [TeamViewer](https://www.teamviewer.com) 軟體 (另行購買)，讓您為執行 Android 裝置的使用者提供遠端協助。 如需詳細資訊，請參閱[對 Intune 管理的 Android 裝置提供遠端協助](device-profile-android-teamviewer.md)。

### <a name="app-management"></a>應用程式管理

#### <a name="new-app-protection-policies-conditions-for-mam----679864---"></a>適用於 MAM 的新應用程式保護原則條件 <!-- 679864 -->

您現在可以在無需註冊使用者的情況下，設定能強制執行下列原則的 MAM 需求：

- 對低應用程式版本
- 最低作業系統版本
- 目標應用程式的最低 Intune APP SDK 版本 (僅限 iOS)

這項功能適用於 Android 和 iOS。 Intune 支援作業系統平台版本、應用程式版本，以及 Intune APP SDK 的最低版本強制。 在 iOS 上，已整合 SDK 的應用程式也可以設定 SDK 層級的最低版本強制。 如果沒有符合應用程式保護原則於上述三個不同層級的最低需求，使用者將無法存取目標應用程式。 此時，使用者可以選擇移除其帳戶 (適用於多重身分識別應用程式)、關閉該應用程式，或更新作業系統或應用程式版本。

您也可設定其他設定，以提供能建議使用者進行作業系統或應用程式升級的非封鎖式通知。 使用者可以關閉此通知，並繼續正常地使用應用程式。

如需詳細資訊，請參閱 [iOS 應用程式保護原則設定](app-protection-policy-settings-ios.md)和 [Android 應用程式保護原則設定](app-protection-policy-settings-android.md)。

#### <a name="configure-app-configurations-for-android-for-work----621621---"></a>設定 Android for Work 的應用程式設定<!-- 621621 -->
市集中有一些 Android 應用程式支援受管理設定選項，可以讓 IT 系統管理員控制應用程式在工作設定檔中執行的方式。 您現在可以使用 Intune 來檢視應用程式支援的設定，並使用設定設計工具或 JSON 編輯器從 Intune 入口網站進行設定。 如需詳細資訊，請參閱[使用 Android for Work 的應用程式設定](app-configuration-policies-use-android.md)。

#### <a name="new-app-configuration-capability-for-mam-without-enrollment----677969---"></a>不需註冊的新 MAM 應用程式設定功能<!-- 677969 -->

您現在可以在沒有註冊通道的情況下，透過 MAM 建立應用程式設定原則。 此功能相當於行動裝置管理 (MDM) 應用程式設定中的應用程式設定原則。 如需使用 MAM 而不註冊的應用程式設定範例，請參閱[搭配 Microsoft Intune 使用 Managed Browser 原則管理網際網路存取](app-configuration-managed-browser.md)。

#### <a name="configure-allowed-and-blocked-url-lists-for-the-managed-browser----682960---"></a>為 Managed Browser 設定允許和封鎖的 URL 清單<!-- 682960 -->

您現在可以在 Azure 入口網站中使用應用程式組態設定，為 Intune Managed Browser 設定允許和封鎖的網域及 URL 清單。 不論 Intune Managed Browser 是用於受管理或未受管理的裝置上，都適用這些設定。 如需詳細資訊，請參閱[搭配 Microsoft Intune 使用 Managed Browser 原則管理網際網路存取](app-configuration-managed-browser.md)。

#### <a name="app-protection-policy-helpdesk-view----1069473---"></a>應用程式保護原則技術支援檢視<!-- 1069473 -->

IT 技術支援使用者現在可以在 [疑難排解] 刀鋒視窗中查看使用者授權狀態，和指派給使用者的應用程式保護原則應用程式的狀態。 如需詳細資訊，請參閱[疑難排解](./help-desk-operators.md)。

### <a name="device-configuration"></a>裝置設定

#### <a name="control-website-visits-on-ios-devices----723832---"></a>控制 iOS 裝置上的網站瀏覽<!-- 723832 -->

您現在可以使用下列兩種方法，來控制 iOS 裝置使用者可以瀏覽的網站：

- 使用 Apple 內建網路內容篩選器新增允許和封鎖的 URL。

- 僅允許 Safari 瀏覽器存取指定的網站。 針對您指定的每個網站，會在 Safari 中建立書籤。

如需詳細資訊，請參閱[適用於 iOS 裝置的網路內容篩選器設定](web-content-filter-settings-ios.md)。

#### <a name="preconfigure-device-permissions-for-android-for-work-apps----621614---"></a>預先設定 Android for Work 應用程式的裝置權限 <!-- 621614 -->

對於部署到 Android for Work 裝置工作設定檔的應用程式，您現在可以設定個別應用程式的權限狀態。  根據預設，需要裝置權限 (例如存取位置或裝置相機) 的 Android 應用程式會提示使用者接受或拒絕授與權限。  例如，若應用程式會使用裝置的麥克風，則系統會提示使用者授與應用程式使用麥克風的權限。 此功能可讓您代表使用者定義權限。  您可以設定權限以 a) 自動拒絕而不通知使用者，b) 自動核准而不通知使用者，或 c) 提示使用者接受或拒絕。 如需詳細資訊，請參閱 [Microsoft Intune 中的 Android for Work 裝置限制設定](device-restrictions-android-for-work.md)。

#### <a name="define-app-specific-pin-for-android-for-work-devices----728976-1102534---"></a>針對 Android for Work 裝置定義應用程式特定的 PIN <!-- 728976, 1102534 -->

工作設定檔做為 Android for Work 裝置管理的 Android 7.0 和更新版本裝置，可讓管理員定義僅適用於工作設定檔中的應用程式的密碼原則。  這些選項包括：

- 僅定義全裝置密碼原則：這是使用者必須用來解鎖整個裝置的密碼。
- 僅定義工作設定檔密碼原則：每當開啟工作設定檔中的應用程式時，系統就會提示使用者輸入密碼。
- 定義裝置和工作設定檔原則：IT 管理員可定義具有不同強度的裝置密碼原則和工作設定檔密碼原則 (例如，使用 4 位數 PIN 來解鎖裝置，但必須使用 6 位數 PIN 來開啟任何工作應用程式)。

如需詳細資訊，請參閱 [Microsoft Intune 中的 Android for Work 裝置限制設定](device-restrictions-android-for-work.md)。

> [!NOTE]
> 此功能僅適用於 Android 7.0 及更新版本。  根據預設，使用者可使用這兩個個別定義的 PIN，或選擇結合這兩個定義的 PIN，以組成包含這兩者的最強式密碼。

#### <a name="new-settings-for-windows-10-devices----978585---"></a>Windows 10 裝置的新設定<!-- 978585 -->

我們已新增可控制數種功能 (例如無線顯示器、裝置探索、工作切換和 SIM 卡錯誤訊息) 的 [Windows 裝置限制設定](device-restrictions-windows-10.md)。

#### <a name="updates-to-certificate-configuration----918991-and-823198---"></a>憑證設定的更新<!-- 918991 and 823198 -->

建立 SCEP 憑證設定檔時，針對 [主體名稱格式]，iOS、Android 和 Windows 裝置可使用 [自訂] 選項。 在此更新之前，[自訂] 欄位僅適用於 iOS 裝置。 如需詳細資訊，請參閱[如何建立 SCEP 憑證設定檔] (certificates-scep-configure.md#how-to-create-a-scep-certificate-profile)。

建立 PKCS 憑證設定檔時，針對 [主體別名]，可使用 [自訂 Azure AD 屬性]。 當您選取 [自訂 Azure AD 屬性] 時，可使用 [部門] 選項。 如需詳細資訊，請參閱[如何建立 PKCS 憑證設定檔] (certficates-pfx-configure.md#how-to-create-a-pkcs-certificate-profile)。

#### <a name="configure-multiple-apps-that-can-run-when-an-android-device-is-in-kiosk-mode----662059---"></a>設定 Android 裝置處於 kiosk 模式時可執行的多個應用程式<!-- 662059 -->

Android 裝置處於 kiosk 模式時，之前只能設定一個允許執行的應用程式。 您現在可以使用應用程式識別碼、存放區 URL或藉由選取您已管理的 Android 應用程式來設定多個應用程式。 如需詳細資訊，請參閱 [Kiosk 模式設定](device-restrictions-android.md#kiosk)。


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

### <a name="ui-updates-to-the-company-portal-website---1313244-part-2--"></a>公司入口網站的 UI 更新 <!--1313244 part 2-->

__精選 App 的更新__：我們已將專用頁面新增至網站 (使用者可在其中瀏覽您選為精選的應用程式)，並對首頁上的 [精選] 區段進行一些 UI 調校。 您可以在[應用程式 UI 的新功能](whats-new-app-ui.md)頁面看到這些變更的樣子。

### <a name="end-of-support-for-android-43-and-lower----1171127-1326920----"></a>結束對 Android 4.3 和較舊版本的支援<!---1171127, 1326920 --->
受管理的應用程式和 Android 公司入口網站應用程式需要 Android 4.4 及更新版本才能存取公司資源。 10 月初前未更新的裝置將不再能存取公司入口網站或這些應用程式。 今年 12 月會強制淘汰所有已註冊的裝置，以致無法存取公司資源。 如果您使用不含 MDM 的應用程式保護原則，應用程式就不會接收更新，其體驗品質會隨著時間而降低。


### <a name="platform-support-reminder-windows-phone-81-mainstream-support-will-end-july-11-2017"></a>平台支援提醒：Windows Phone 8.1 主要支援將於 2017 年 7 月 11 日結束
<!-- 1327781 -->

Windows Phone 8.1 平台將於 2017 年 7 月 11 日結束主要支援。 Windows 8.1 電腦的支援不受影響。

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

---
title: "Microsoft Intune 預覽版的新功能"
titleSuffix: Intune Azure preview
description: "了解 Intune Azure 預覽版中的新功能"
keywords: 
author: mtillman
ms.author: mtillman
manager: angrobe
ms.date: 03/17/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 791ed23f-bd13-4ef0-a3dd-cd2d7332c5cc
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 671d862c8d9a98e02f33d96cf6ceba712e740dec
ms.openlocfilehash: 586bdab54ee60ba8d620857ab3506aa27622d17a
ms.lasthandoff: 03/17/2017

---

# <a name="whats-new-in-the-microsoft-intune-preview"></a>Microsoft Intune 預覽版的新功能

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

隨著公開預覽版的推出，更多新功能陸續加入，我們利用這裡的版面提供相關資訊。

> [!Note]
> 我們將首度發行此頁面所列出的 Azure 入口網站預覽版變更。 不過，基於 Intune 服務更新的方式不同，變更可能無法立即生效。  數個服務元件必須依序更新，才能使用新的入口網站功能。 這些變更於近日首度發行時請務必試試看。

## <a name="march-2017"></a>2017 年 3 月

### <a name="support-for-ios-lost-mode---431695--"></a>支援 iOS 遺失模式 <!--431695-->

針對 iOS 9.3 和更新的裝置，Intune 新增**遺失模式**的支援。 您現在可以鎖定裝置以防止任何使用，並在裝置的鎖定畫面上顯示訊息和連絡電話號碼。

使用者將無法解除鎖定裝置，除非系統管理員停用「遺失模式」。 啟用「遺失模式」時，您可以使用 [尋找裝置] 動作在 Intune 主控台中的地圖上顯示裝置的地理位置。

裝置必須是透過 DEP 註冊之公司擁有的 iOS 裝置，且處於受監督模式。

如需詳細資訊，請參閱[什麼是 Microsoft Intune 裝置管理？](/intune-azure/manage-devices/what-is)

### <a name="improvements-to-device-actions-report---677150--"></a>裝置動作報告改善 <!--677150-->

我們改善了裝置動作報告以提升效能。 此外，您現在可以依狀態篩選報告。 例如，您可以篩選報告以僅顯示已完成的裝置動作。

### <a name="actions-for-non-compliance---730266--"></a>不符合規定時所採取的動作 <!--730266-->

**不符合規定時所採取的動作**是相容性原則的新功能，可讓您對不相容的裝置採取動作。 您可以指定單一或多個動作，並指定必須進行這些動作的時間週期。 例如，您可以在裝置變成不相容之後透過電子郵件立即通知使用者有不相容的裝置，也可以在 3 天寬限期之後透過條件式存取封鎖不相容的裝置存取公司資源。

### <a name="custom-app-categories---748805--"></a>自訂應用程式類別 <!--748805-->

您現在可以建立、編輯和指派您新增至 Intune 之應用程式的類別。 目前只能以英文指定類別。
請參閱[如何將應用程式新增至 Intune](/intune-azure/manage-apps/add-apps)。

### <a name="assign-lob-apps-to-users-with-unenrolled-devices---748823--"></a>指派 LOB 應用程式給使用未註冊裝置的使用者 <!--748823-->

您現在可以將市集中的企業營運應用程式指派給使用者，不論其裝置是否已向 Intune 註冊。 如果未向 Intune 註冊使用者裝置，則必須前往「公司入口網站」網站安裝它，而不是公司入口網站應用程式。

### <a name="new-compliance-reports---846671--"></a>新的合規性報告 <!--846671-->

您現在有可提供公司內裝置合規性狀態的合規性報告，並可以快速地針對使用者遇到的合規性相關問題進行疑難排解。 您可以檢視的資訊如下

- 整體的裝置合規性狀態
- 個別設定的合規性狀態
- 個別原則的合規性狀態

您也可以使用這些報告來向下鑽研個別裝置，以檢視影響該裝置的特定設定和原則。

<!--- You can now create an edition upgrade policy to upgrade devices to the following additional Windows 10 editions:

- Windows 10 Professional
- Windows 10 Professional N
- Windows 10 Professional Education
- Windows 10 Professional Education N --->

### <a name="direct-access-to-apple-enrollment-scenarios---951869--"></a>直接存取 Apple 註冊案例 <!--951869-->

對於在 2017 年 1 月之後建立的 Intune 帳戶，Intune 已經啟用使用 Azure Preview 入口網站中的「註冊裝置」工作負載直接存取 Apple 註冊案例。 Apple 註冊預覽原本只能從傳統 Intune 入口網站中的連結存取。 在 2017 年 1 月之前建立的 Intune 帳戶，將需要進行一次性移轉，才能在 Azure 中使用這些功能。 移轉的排程尚未宣布，但將會盡快提供詳細資料。 如果您現有的帳戶無法存取預覽，我們強烈建議您建立試用帳戶來測試新的體驗。


## <a name="february-2017"></a>2017 年 2 月

### <a name="ability-to-restrict-mobile-device-enrollment---747600-795782--"></a>限制行動裝置註冊的能力 <!--747600, 795782-->
Intune 正在新增新的註冊限制，以控制哪些行動裝置平台可以註冊。 Intune 將行動裝置平台分為 iOS、macOS、Android、Windows 和 Windows Mobile。

* 限制行動裝置註冊不會限制電腦用戶端註冊。  
* 僅限 iOS 與 Android，有一個額外選項可阻擋註冊個人擁有的裝置。

Intune 會將所有的新裝置標示為個人，除非 IT 系統管理員採取動作將它們標示為公司擁有，如[本文章](https://docs.microsoft.com/en-us/intune/deploy-use/manage-corporate-owned-devices)所說明。

### <a name="view-all-actions-on-managed-devices---677150--"></a>檢視受管理裝置上的所有動作 <!--677150-->
新的__裝置動作__報表會顯示曾執行遠端動作的人員，像是裝置恢復出廠預設值，並會另外顯示該動作的狀態。 請參閱[什麼是裝置管理？](https://docs.microsoft.com/intune-azure/manage-devices/what-is)。

### <a name="non-managed-devices-can-access-assigned-apps---664691--"></a>未受管理的裝置可以存取已指派的應用程式 <!--664691-->
iOS 和 Android 使用者能夠在他們未受管理的裝置上，安裝指派給他們的「無須註冊即可使用」應用程式，這屬於公司入口網站的設計變更。 使用 Intune 認證，使用者能夠登入公司入口網站，並查看指派給他們的應用程式清單。 「無須註冊即可使用」應用程式的應用程式套件，可透過公司入口網站下載取得。 這項變更不會影響需要註冊才能安裝的應用程式，因為如果使用者想要安裝這些應用程式，系統會提示他們註冊裝置。

### <a name="custom-app-categories---748805--"></a>自訂應用程式類別 <!--748805-->
您現在可以建立、編輯和指派您新增至 Intune 之應用程式的類別。 目前只能以英文指定類別。
請參閱[如何將應用程式新增至 Intune](/intune-azure/manage-apps/add-apps)。

### <a name="display-device-categories---814654--"></a>顯示裝置類別 <!--814654-->
裝置清單現在會以資料行顯示裝置類別。 您也可以在裝置內容刀鋒視窗的內容區段中編輯類別。 請參閱[如何將應用程式新增至 Intune](/intune-azure/manage-apps/add-apps)。

### <a name="configure-windows-update-for-business-settings---776716--"></a>設定商務用 Windows Update 的設定 <!--776716-->

「Windows 即服務」是一種為 Windows 10 提供更新的新做法。 從 Windows 10 開始，任何新的「功能更新」和「品質更新」都會包含所有先前的更新內容。 這表示只要您安裝了最新的更新，就能確定您的 Windows 10 裝置已完全更新至最新版。 不同於舊版 Windows，您現在必須安裝整個更新而不是部分更新。

使用商務用 Windows Update，可以簡化更新管理體驗，因此您不需要核准裝置群組的個別更新。 只要設定更新首度發行策略，您還是可以管理環境中的風險，Windows Update 會確保在適當的時間安裝更新。 Microsoft Intune 可讓您在裝置上設定更新設定，並可讓您延後更新的安裝。 Intune 不會儲存更新，只會儲存更新原則指派。 裝置直接存取 Windows Update 進行更新。使用 Intune 設定及管理 **Windows 10 更新響鈴**。 更新響鈴是一組包含何時及如何安裝 Windows 10 更新的設定。 如需詳細資訊，請參閱[設定商務用 Windows Update 的設定](/intune-azure/configure-devices/how-to-configure-windows-update-for-business)。

## <a name="january-2017"></a>2017 年 1 月

### <a name="assign-line-of-business-apps-whether-or-not-devices-are-enrolled---748823--"></a>不論是否註冊裝置都指派企業營運應用程式 <!--748823-->
您現在可以將市集中的企業營運和應用程式指派給不論是否向 Intune 註冊其裝置的使用者。 如果未向 Intune 註冊使用者裝置，則他們必須前往公司入口網站安裝它，而不是公司入口網站應用程式。 請參閱[什麼是應用程式管理](/intune-azure/manage-apps/what-is-app-management)。

### <a name="resolve-issue-where-ios-devices-are-inactive-or-the-admin-console-cannot-communicate-with-them"></a>解決 iOS 裝置處於非使用狀態或管理員主控台無法與它們通訊的問題
當使用者的裝置與 Intune 失去連絡時，您可以提供新的疑難排解步驟，協助他們重新取得公司資源的存取權。 請參閱[裝置處於非使用狀態或管理員主控台無法與它們通訊](/intune-azure/enroll-devices/troubleshoot-device-enrollment#devices-are-inactive-or-the-admin-console-cannot-communicate-with-them)。

## <a name="december-2016-initial-release"></a>2016 年 12 月 (初版)

### <a name="telecom-expense-management-integration-in-public-preview-of-azure-portal--747605--"></a>Azure 入口網站公開預覽中的電信費用管理整合<!--747605-->
我們現在將開始在 Azure 入口網站中預覽與協力廠商電信費用管理 (Telecom Expense Management，TEM) 服務的整合。 您可以使用 Intune 強制執行限制國內和漫遊資料使用量。 我們將開始與 [Saaswedo](http://www.saaswedo.com) 進行這些整合。 若要在您的試用租用戶中啟用此功能，請[連絡 Microsoft 支援服務](https://docs.microsoft.com/intune/troubleshoot/how-to-get-support-for-microsoft-intune)。

- 將市集應用程式部署到 iOS、 Android 及 Windows 裝置並加以管理
- 將企業營運 (LOB) 應用程式部署到 iOS、 Android 及 Windows 裝置並加以管理
- 將大量採購的應用程式部署到 iOS、 Android 及 Windows 裝置並加以管理
- 將 Web 應用程式部署到 iOS、 Android 及 Windows 裝置並加以管理
- 受管理之 iOS 應用程式組態設定檔
- 設定應用程式保護原則，並將企業營運應用程式部署到未向 Intune 註冊的裝置
- VPN 設定檔、個別應用程式 VPN、Wi-Fi、電子郵件及憑證設定檔
- 合規性政策
- Azure AD 的條件式存取
- 對內部部署 Exchange 的條件式存取
- 裝置註冊
- 以角色為基礎的存取控制

## <a name="deprecated-features-in-the-azure-portal"></a>Azure 入口網站中標示即將淘汰的功能

### <a name="support-for-row-by-row-review-of-hardware-identifiers"></a>逐列檢閱硬體識別碼的支援
對於 IMEI 號碼及 Apple 序號，Azure 入口網站逐列檢閱硬體識別碼。 在傳統 Intune 主控台中，您可以匯入逗點分隔值 (.csv) 檔案中的詳細資料來覆寫現有個別硬體識別碼的詳細資料。 Azure 入口網站提供一個精簡選項，會自動覆寫所有的硬體識別碼的詳細資料，或忽略現有識別碼的新詳細資料。

#### <a name="how-this-affects-you"></a>此功能對您的影響
在 Azure 入口網站中，您無法逐列決定要更新的國際行動設備識別碼 (IMEI) 裝置。 傳統 Intune 主控台會繼續支援此功能。

#### <a name="how-to-get-ready-for-this-change"></a>此變更需要哪些準備
事先提出此變更資訊的目的在讓您的水援系統管理員知道這項變更。 這項變更會在移轉到 Azure 入口網站時一併實施，預定時間在 2017 年上半年。


### <a name="support-for-default-corporate-device-enrollment-profiles-in-apple-dep"></a>Apple DEP 中的預設公司裝置註冊設定檔支援
Azure 入口網站不支援 Apple 裝置註冊程式 (DEP) 裝置序號的「預設」公司裝置註冊設定檔。 傳統 Intune 主控台支援此功能，但即將中止，以避免不慎指派這類設定檔。 在 Azure 入口網站中，從 Apple DEP 帳戶同步而步而來的序號一開始並沒有任何公司裝置註冊設定檔指派。

#### <a name="how-this-affects-you"></a>此功能對您的影響
在 Azure 入口網站中，您將無法再設定適用於所有 Apple 裝置的預設設定檔原則。 傳統 Intune 主控台會繼續支援此功能。

#### <a name="how-to-get-ready-for-this-change"></a>此變更需要哪些準備
事先提出此變更資訊的目的在讓您的水援系統管理員知道這項變更。 這項變更會在移轉到 Azure 入口網站時一併實施，預定時間在 2017 年上半年。


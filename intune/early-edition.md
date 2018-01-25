---
title: "舊版"
description: 
keywords: 
author: ErikjeMS
ms.author: erikje
manager: angrobe
ms.date: 01/18/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 12f4a09fe10ec792abe8183369a21f53c23f5d1a
ms.sourcegitcommit: 53d272defd2ec061dfdfdae3668d1b676c8aa7c6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2018
---
# <a name="the-early-edition-for-microsoft-intune---january-2018"></a>Microsoft Intune 的初期版本 - 2018 年 1 月

**舊版**提供 Microsoft Intune 即將發行版本要推出的功能清單。 此資訊以有限的基礎提供，並可能有所變更。 請不要在貴公司以外的地方分享此資訊。 這裡列出的一些功能可能有截止日期，而且可能會延遲到未來的版本。 其他功能正在實驗 (測試) 中進行測試，以確保它們可供客戶使用。 如果您有任何問題或疑慮，請洽詢您的 Microsoft 產品群組連絡人。

此頁面會定期更新。 請回來查看其他更新。

> [!Note]
>下列變更正在 Intune 的開發過程中。 如需新混合式功能的詳細資訊，請查看我們的[混合式新增功能](/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management)頁面。

<!--
## What's coming to Intune in the Azure portal  
## What's coming to Intune apps
## Notices
-->


## <a name="intune-in-the-azure-portal"></a>Azure 入口網站中的 Intune

### <a name="easier-resolution-of-compliance-issues-for-the-company-portal-app-for-windows-10---676546---"></a>針對 Windows 10 公司入口網站應用程式，可以更容易解決合規性問題 <!--676546 -->

如果終端使用者是使用 Windows 裝置，便可以在公司入口網站應用程式中點選不符合規範的原因。 如此一來，系統會盡可能將使用者直接移至設定應用程式的正確位置，以修正問題。

### <a name="new-option-for-user-authentication-for-apple-bulk-enrollment----747625---"></a>適用於 Apple 大量註冊的使用者驗證新選項 <!-- 747625 -->
Intune 可讓您使用公司入口網站應用程式於下列註冊方法，以便對裝置進行驗證：

- Apple 裝置註冊方案
- Apple School Manager
- Apple Configurator 註冊

使用 [公司入口網站] 選項時，可以強制執行 Azure Active Directory 多重要素驗證，而不會封鎖這些註冊方法。

使用 [公司入口網站] 選項時，針對使用者親和性註冊，Intune 會跳過 iOS 設定輔助程式中的使用者驗證。 這表示該裝置一開始會註冊為無使用者的裝置，因此不會收到使用者群組的設定或原則。 它只會接收裝置群組的設定和原則。 不過，Intune 會自動在裝置上安裝公司入口網站應用程式。 第一位啟動並登入公司入口網站應用程式的使用者，將會在 Intune 中與該裝置產生關聯。 此時，使用者將會收到其使用者群組的設定和原則。 使用者關聯需要重新註冊才可以變更。

### <a name="intune-support-for-multiple-apple-dep--apple-school-manager-accounts----747685---"></a>Intune 支援多個 Apple DEP / Apple School Manager 帳戶 <!-- 747685 -->
Intune 可支援註冊最多達 100 個來自不同 Apple 裝置註冊計劃 (DEP) 或 Apple School Manager 帳戶的裝置。 每個上傳的權杖可以針對註冊設定檔和裝置來個別管理。 不同的註冊設定檔可以根據上傳的 DEP/School Manager 權杖來自動指派。 如果上傳了多個 School Manager 權杖，則一次只能與 Microsoft School Data Sync 共用一個權杖。

移轉之後，透過 Graph 來管理 Apple DEP 或 ASM 的搶鮮版 (Beta) Graph API 與發佈的指令碼將無法再運作。 新的搶鮮版 (Beta) Graph API 正在開發，將會在移轉後發行。

### <a name="select-device-categories-by-using-the-access-work-or-school-settings----1058963-eeready---"></a>使用 [存取公司或學校資源] 設定來選取裝置類別 <!-- 1058963 eeready -->
如果您已啟用[裝置群組對應](https://docs.microsoft.com/en-us/intune/device-group-mapping)，當 Windows 10 上的使用者透過 [設定] > [帳戶] > [存取公司或學校資源] 中的 [連線] 按鈕來註冊之後或在全新體驗期間，會出現選取裝置類別的提示。

### <a name="targeting-compliance-policies-to-devices-in-device-groups---1307012---"></a>讓合規性原則以裝置群組中的裝置為目標 <!--1307012 -->

您可以讓合規性原則以使用者群組中的使用者為目標。 您可以讓合規性原則以裝置群組中的裝置為目標。

### <a name="including-and-excluding-app-assignment-based-on-groups----1406920---"></a>依據群組來包含和排除應用程式指派 <!-- 1406920 -->

應用程式指派期間和選取指派類型之後，您將能選取要包含的群組，以及要排除的群組。

### <a name="remote-erase-command-support----1438084---"></a>遠端「清除」命令支援 <!-- 1438084 -->

系統管理員可以從遠端發出清除命令。

> [!IMPORTANT]
> 清除命令無法回復，應該謹慎使用。

清除命令會從裝置移除所有資料，包括作業系統。 這樣做也會從 Intune 管理移除裝置。 系統不會向使用者發出任何警告，且將在發出命令之際，立即開始清除。

您可以設定 6 位數的復原 PIN。 此 PIN 可用來將已清除的裝置解除鎖定，並開始重新安裝作業系統。 開始進行清除後，PIN 會出現在 Intune 中裝置 [概觀] 刀鋒視窗的狀態列上。 在清除進行期間，PIN 會持續顯示。 完成清除後，裝置會完全從 Intune 管理中消失。 請務必記錄復原 PIN，以供還原裝置的人員來使用。

### <a name="windows-information-protection-wip-encrypted-data-in-windows-search-results----1469193---"></a>Windows 搜尋結果中的 Windows 資訊保護 (WIP) 加密資料 <!-- 1469193 -->

Windows 資訊保護 (WIP) 原則中的新設定可讓您控制 Windows 搜尋結果是否包含 WIP 加密資料。

### <a name="website-learning-mode----1631908---"></a>網站學習模式 <!-- 1631908 -->

Intune 將引入 Windows 資訊保護 (WIP) 學習模式的延伸模組。 除了檢視已啟用 WIP 的應用程式相關資訊以外，您也能檢視與網站共用工作資料之裝置的摘要。 您可以藉由這項資訊，決定哪些網站應該加入群組和使用者 WIP 原則。

### <a name="updates-to-compliance-emails---1637547---"></a>更新合規性電子郵件 <!--1637547 -->

當傳送電子郵件以回報不符合規範的裝置時，電子郵件會包含不符合規範的裝置相關詳細資料。 下列文章將會更新以指示這項事實：[針對不符合規範的自動化動作](#actions-for-noncompliance)。

### <a name="conditional-access-policies-for-intune-is-only-available-from-the-azure-portal-----1737088-1634311---"></a>Intune 的條件式存取原則只能從 Azure 入口網站使用 <!-- 1737088 1634311 -->
我們將會簡化您設定與管理條件式存取之處。 您將會從 [Azure Active Directory] > [條件式存取]，在 [Azure 入口網站](https://portal.azure.com)中設定與管理原則。 為了方便起見，您也可以從 [Intune] > [條件式存取]，在 Azure 入口網站中從 Intune 存取此刀鋒視窗。

###  <a name="alerts-for-expired-tokens-and-tokens-that-will-soon-expire----1639263---"></a>過期的權杖與即將過期之權杖的警示 <!-- 1639263 -->
[概觀] 頁面會顯示過期的權杖與即將過期之權杖的警示。 當您按一下單一權杖的警示時，將會移至權杖的詳細資料頁面。  當您按一下多個權杖的警示時，將會移至所有權杖的清單，其中包含權杖的狀態。 系統管理員應該在到期日之前更新其權杖。

### <a name="remote-printing-over-a-secure-network----1709994----"></a>透過安全網路進行遠端列印 <!-- 1709994  -->
PrinterOn 的無線行動列印方案，可讓使用者隨時隨地透過安全的網路來進行遠端列印。 PrinterOn 將與適用於 iOS 和 Android 的 Intune APP SDK 整合。 您將能透過管理主控台中的 [應用程式保護原則] 刀鋒視窗，讓應用程式保護原則以此應用程式為目標。 終端使用者將能夠透過 Play 商店或 iTunes 下載 'PrinterOn for Microsoft' 應用程式，以在其 Intune 生態系統內使用。

### <a name="approve-the-company-portal-app-for-android-for-work---1797090---"></a>核准適用於 Android for Work 的公司入口網站應用程式 <!--1797090 -->
如果您的組織使用 Android for Work，您就必須手動核准適用於 Android 的公司入口網站應用程式，這樣它才能繼續從受控的 Google Play 商店接收自動更新。

### <a name="faceid-on-ios-devices----1807377---"></a>iOS 裝置上的 FaceID <!-- 1807377 -->
Intune 應用程式保護原則現在支援控制 iOS 裝置 FaceID 的設定。 此設定適用於支援 FaceID 功能的裝置 (目前僅 iPhone X 提供此功能)。 這項設定與目前支援的 TouchID 控制項是分開的。 組織可以選擇是否在 TouchID 控制項外，信任 FaceID 作為有效的 PIN 提示。

### <a name="microsoft-graph-api-for-intune---general-availability-----1833289---"></a>適用於 Intune 的 Microsoft Graph API - 正式運作  <!-- 1833289 -->
Microsoft Graph 中的 Intune API 可提供以程式設計的方式來存取資料與方法，以自動化 Intune 服務的系統管理動作。  這些 API **正式運作**之後，客戶、合作夥伴和開發人員將能利用這些 API，針對 Intune 或透過 Microsoft Graph 提供的其他 Microsoft 服務，整合相關或需要其支援的內部或商業解決方案。

<!-- the following are present prior to 1801 -->

### <a name="app-protection-policies-----679615---"></a>應用程式防護原則 <!-- 679615 -->
Intune 應用程式防護原則能提供建立全域預設原則的能力，以針對整個租用戶中的所有使用者快速啟用保護。

### <a name="revoking-ios-volume-purchase-program-apps-----820863---"></a>撤銷 iOS 大量採購方案應用程式 <!-- 820863 -->
對於具有一或多個 iOS 大量採購方案 (VPP) 應用程式的指定裝置，您將可撤銷與該裝置相關連的裝置型應用程式授權。 撤銷應用程式授權將不會從該裝置解除安裝相關聯的 VPP 應用程式。 若要解除安裝 VPP 應用程式，您必須將指派動作變更為 [解除安裝]。 如需詳細資訊，請參閱[如何使用 Microsoft Intune 管理透過大量採購方案購買的 iOS 應用程式](vpp-apps-ios.md)。

### <a name="revoke-licenses-for-an-ios-volume-purchasing-program-token----820870---"></a>撤銷 iOS 大量採購方案權杖的授權 <!-- 820870 -->
您將可針對指定的 VPP 權杖撤銷所有 iOS 大量採購方案 (VPP) 應用程式的授權。

### <a name="new-ios-device-action------1244701---"></a>新的 iOS 裝置動作 <!-- 1244701 -->
您可以關閉 iOS 10.3 受監督的裝置。 這個動作會立即關閉裝置，而不會警告使用者。 您可以在 [裝置] 工作負載中選取裝置時，於裝置屬性中找到 [關機 (僅限受監督)] 動作。


### <a name="intune-now-provides-the-account-move-operation-----1573558-1579830---"></a>Intune 現在提供帳戶移動作業 <!-- 1573558, 1579830 -->
**帳戶移動**可將租用戶從某個 Azure 縮放單位 (ASU) 移轉至另一個。 **帳戶移動**可用於客戶起始的案例 (當您呼叫 Intune 支援小組並要求它時)，也可用於由 Microsoft 驅動的案例 (當 Microsoft 需要對後端對服務進行調整時)。 在**帳戶移動**期間，租用戶會進入唯讀模式 (ROM)。 諸如註冊、重新命名裝置、更新合規性狀態等服務作業，在 ROM 期間都將會失敗。




<!-- the following are present prior to 1712 -->
### <a name="assign-office-365-mobile-apps-to-ios-and-android-devices-using-built-in-app-type----1332318---"></a>將 Office 365 行動應用程式指派給使用內建應用程式類型的 iOS 和 Android 裝置 <!-- 1332318 -->
**內建** - 應用程式類型能讓您更輕鬆地建立 Office 365 應用程式，並將它們指派給您管理的 iOS 及 Android 裝置。 這些應用程式包括 0365 應用程式，例如 Word、Excel、PowerPoint 和 OneDrive。 您可以將特定的應用程式指派給應用程式類型，並編輯應用程式資訊設定。


### <a name="assignment-conflict-resolution-has-changed-for-ios-store-apps----1480316---"></a>iOS 市集應用程式之指派衝突的解析已變更 <!-- 1480316 -->
使用者可能會遇到 iOS 市集應用程式可用性的變更。 目前，已指派給兩個群組，在**必要且可用**與**不適用**之間發生衝突的應用程式，會解析成**必要且可用**。 因為這項變更，發生此衝突的應用程式會解析成**不適用**。

當一個應用程式指派給多個具有不同應用程式用途的群組時，此變更會處理此混亂。

如果您希望在 11 月服務版本前向資訊工作者入口網站和公司入口網站提供您的應用程式，您有兩個選項：

1. 移除群組的**不適用**指派。
2. 建立不包含指派**必要且可用**用途之成員的新群組，並將該群組指派為**不適用**。

如需詳細資訊，請參閱[如何使用 Microsoft Intune 將應用程式指派給群組](apps-deploy.md)。

> [!Note]
> 在此版本後，您將無法再於 Intune 傳統主控台中檢視或修改行動裝置管理 (MDM) 應用程式指派。 不過，您可以使用 Azure 主控台或 Intune 圖形 API 指派應用程式。

### <a name="manage-android-for-work-devices-independently-from-android-devices----1490731---"></a>從 Android 裝置獨立管理 Android for Work 裝置<!-- 1490731 -->
Intune 會支援從 Android 平台獨立管理 Android for Work 裝置的註冊。 這些設定在 [裝置註冊] > [註冊限制] > [裝置類型限制] 下管理。 (原位於 [裝置註冊] > [Android for Work 註冊] > [Android for Work 註冊設定] 下。)

根據預設，Android for Work 裝置設定會與您的 Android 裝置設定相同。 不過，變更 Android for Work 設定後，就不再是那麼回事了。
 
如果您封鎖個人的 Android for Work 註冊，只有公司的 Android 裝置可以註冊為 Android for Work。

使用新設定時，請考慮下列事項：

#### <a name="if-you-have-never-previously-onboarded-android-for-work-enrollment"></a>之前是否從未啟動 Android for Work 註冊
在預設的裝置類型限制中封鎖新的 Android for Work 平台。 啟動功能後，您可以允許裝置註冊 Android for Work。 若要這樣做，請變更預設值，或建立新的裝置類型限制來取代預設的裝置類型限制。

#### <a name="if-you-have-onboarded-android-for-work-enrollment"></a>是否曾啟動 Android for Work 註冊
如果曾經啟動過，您的情況會隨您選擇的設定而異：

| Setting | 預設裝置類型限制中的 Android for Work 狀態 | 注意 |
| --- | --- | --- |
| **將所有裝置當成 Android 管理** | 已封鎖 | 所有 Android 裝置都必須註冊，但不是 Android for Work。 |
| **將支援的裝置當成 Android for Work 管理** | 允許 | 所有支援 Android for Work 的裝置都必須註冊 Android for Work。 |
| **將這些群組中僅限使用者的受支援裝置當成 Android for Work 管理** | 已封鎖 | 已建立不同的裝置類型限制原則，以覆寫預設值。 此原則會定義您先前選取的群組，以允許 Android for Work 註冊。 所選群組內的使用者仍可以繼續註冊他們的 Android for Work 裝置。 所有其他使用者則限制不能註冊 Android for Work。 |

無論什麼情況，都會保留您預期的法規。 您不需要執行任何動作，即能維持您環境中 Android for Work 的全域或各群組額度。

這些變更會在 11 月更新中推出，但可能要一段時間後才會在您的帳戶上執行。 當這些變更對您的帳戶生效時，您會在 Office 365 入口網站中收到確認通知。


### <a name="configure-an-ios-app-pin----1586774---"></a>設定 iOS 應用程式 PIN <!-- 1586774 -->
您很快就可以要求目標 iOS 應用程式的 PIN。 您可以透過 Azure 入口網站設定 PIN 需求及以天計的到期日期。 必要時，使用者必須設定並使用新的 PIN，才能存取 iOS 應用程式。 只有使用 Intune App SDK 啟用應用程式保護的 iOS 應用程式才支援這項功能。

### <a name="user-experience-update-for-the-company-portal-app-for-ios---1412866--"></a>iOS 版公司入口網站應用程式的使用者體驗更新 <!--1412866-->

我們將發行 iOS 版公司入口網站應用程式的重大使用者體驗更新。 此項更新的重點是全面視覺效果的重新設計，包括提高使用性和存取範圍的現代化外觀及操作。 保留目前所有的 iOS 公司入口網站功能。

我們會透過 Apple TestFlight 計劃，提供更新公司入口網站應用程式的發行前版本讓您使用，並歡迎您提供意見反應。 請在 https://aka.ms/intune_ios_cp_testflight 註冊存取 TestFlight。 

![新 ios 公司入口網站應用程式的預告片影像](./media/ios-cp-app-redesign-1801-teaser.png)


<!-- the following are present prior to 1711 -->

### <a name="azure-active-directory-web-sites-can-require-the-intune-managed-browser-app-and-support-single-sign-on-for-the-managed-browser-public-preview----710595---"></a>Azure Active Directory 網站可以要求使用 Intune Managed Browser 應用程式，並支援 Managed Browser (公開預覽) 的單一登入 <!-- 710595 -->   
使用 Azure Active Directory (Azure AD) 時，您能夠限制行動裝置使用 Intune Managed Browser 應用程式存取網站。 在 Managed Browser 中，網站資料的安全受到保護，並會與使用者的個人資料區隔開來。 此外，針對受 Azure AD 保護的網站，Managed Browser 也支援單一登入功能。 當使用者登入 Managed Browser，或在裝置上搭配使用 Managed Browser 與受 Intune 管理的其他應用程式時，即可在不需輸入認證的情況下，讓 Managed Browser 存取受 Azure AD 保護的公司網站。 這項功能適用於 Outlook Web Access (OWA) 和 SharePoint Online 等網站，以及透過 Azure App Proxy 存取的內部網路資源等其他公司網站。


<!-- the following are present prior to 1710 -->



### <a name="support-for-windows-10-edition-upgrade-policy------903672archived-1119689---"></a>支援 Windows 10 版本升級原則 <!-- 903672(archived), 1119689 -->  
您可以建立 Windows 10 版本升級原則，以將 Windows 10 裝置升級為 Windows 10 教育版、Windows 10 教育版 N、Windows 10 專業版、Windows 10 專業版 N、Windows 10 專業教育版和 Windows 10 專業教育版 N。如需 Windows 10 版本升級的詳細資料，請參閱[如何設定 Windows 10 版本升級](edition-upgrade-configure-windows-10.md)。




<!-- the following are present prior to 1709 -->


### <a name="intune-app-protection-and-citrix-mdx-development-tools----709185---"></a>Intune 應用程式防護和 Citrix MDX 開發工具 <!-- 709185 -->
您可以搭配使用 Citrix XenMobile MDX 和 Microsoft Intune 來管理裝置和應用程式。 如此一來，您就可以使用 Citrix 的 mVPN 技術，透過 Intune 應用程式防護原則來管理應用程式。

您可以尋找程式碼存放庫，其中包含適用於 iOS 和 Android 的 Intune App Wrapping Tool 和 Intune App SDK，並與 Citrix MDX mVPN 技術整合。




<!-- the following are present prior to 1711 -->


### <a name="redirecting-macos-users-to-our-new-company-portal-app---1380728--"></a>將 macOS 使用者重新導向至新的公司入口網站應用程式 <!--1380728-->   
當使用者登入公司入口網站，並註冊 macOS 裝置時，系統會指示他們下載 macOS 版的新公司入口網站應用程式以 完成程序。 使用 OS X El Capitan 10.11 或更新版本的 macOS 裝置會發生這種情況。 



<!-- the following are present prior to 1709 -->

### <a name="intune-managed-browser-support-for-ios-and-android----1374196---"></a>iOS 和 Android 的 Intune Managed Browser 支援 <!-- 1374196 -->
自 2017 年 10 月起，Android 應用程式上的 Intune Managed Browser 應用程式只會支援執行 Android 4.4 和更新版本的裝置。 iOS 上的 Intune Managed Browser 應用程式只支援執行 iOS 9.0 及更新版本的裝置。 較舊版本的 Android 和 iOS 能夠繼續使用 Managed Browser，但是無法安裝新版的應用程式，而且可能無法存取所有的應用程式功能。 建議您將這些裝置更新為受支援的作業系統版本。


### <a name="improved-error-message-for-when-a-user-reaches-the-maximum-number-of-devices-allowed-to-enroll----1270370---"></a>改進使用者達到允許註冊的裝置數目上限時的錯誤訊息 <!-- 1270370 -->
使用 Android 裝置的終端使用者不會看到一般錯誤訊息，而是會看到易讀且可採取動作的錯誤訊息：「您已註冊 IT 系統管理員所允許的裝置數目上限。請移除已註冊的裝置，或向您的 IT 系統管理員取得協助。」




## <a name="notices"></a>通知

目前沒有任何作用中的通知。




### <a name="see-also"></a>另請參閱
如需近期發展的詳細資料，請參閱 [Microsoft Intune 的新功能](whats-new.md)。

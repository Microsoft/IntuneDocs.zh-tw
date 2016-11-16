---
title: "「新功能」封存 | Microsoft Intune"
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 11/11/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ed2db991-4729-49a7-a1e6-be2ffa0d03d1
ROBOTS: noindex,nofollow
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 861b5ea3bb0772d2853942e2b3f11f607dad3774
ms.openlocfilehash: 25128cfe93280e38a03779a7e6f38ddeb3c15612


---
# <a name="whats-new-archive"></a>「新功能」封存

此頁面是 [Microsoft Intune 的新功能](whats-new-in-microsoft-intune.md)中近期公告的封存。

## <a name="september-2016"></a>2016 年 9 月
### <a name="new-features-announcements-and-information"></a>新功能、宣告和資訊
* [Windows 條件式存取](#windows-conditional-access)
* [iOS 10 支援](#ios-10-support)
* [App Wrapping Tool 支援 MAM，不需要 Android 和 iOS 裝置註冊](#app-wrapping-tool-supports-mam-without-device-enrollment-for-android-and-ios)
* [Intune 群組在 9 月會開始轉換到 Azure Active Directory](#intune-groups-begin-transitioning-to-azure-active-directory-in-september)
* [Lookout 整合以保護 Android 裝置](#lookout-integration-to-protect-android-devices)
* [適用於 Android、iOS 和 Windows 的公司入口網站更新](#company-portal-updates)
* [Intune 字彙](#intune-glossary)
* [未來動態](#whats-coming)

### <a name="windows-conditional-access"></a>Windows 條件式存取
您現在可以透過 Intune 管理主控台建立條件式存取原則，來封鎖 Windows 電腦存取 Exchange Online 和 SharePoint Online。 您也可以建立條件式存取原則來封鎖存取 Office 桌面及通用應用程式。

### <a name="ios-10-support"></a>iOS 10 支援
現有的 Intune MDM 與 MAM 案例與 iOS 10 相容。 如需秘訣，請參閱 [Intune 支援小組部落格](https://blogs.technet.microsoft.com/intunesupport/2016/09/13/support-tip-intune-support-for-ios-10/)。

### <a name="app-wrapping-tool-supports-mam-without-device-enrollment-for-android-and-ios"></a>App Wrapping Tool 支援 MAM，不需要 Android 和 iOS 裝置註冊
Intune App Wrapping Tool 是命令列工具，用於在 iOS 和 Android 的企業營運 (LOB) 應用程式上啟用 Intune MAM。 它是將 Intune MAM SDK 併入到您 App 最簡單的方式，讓您的 App 可以強制執行透過 Intune 部署的 MAM 原則。 使用 MAM 原則，您可以：

1. 加密 App 的資料。
2. 要求資訊工作者啟動 App 時輸入 PIN。
3. 讓 App 只能傳送資料給其他受管理的 App。
4. 防止 App 將資料備份到 Android、iTunes 及 iCloud。
5. 僅允許對/從其他受管理的 App 執行剪下、複製和貼上。

更新的 Intune App Wrapping Tool 公開預覽版現在支援 MAM，而不需要在 iOS 和 Android 上的內部 LOB 應用程式裝置註冊。 這表示您的使用者不需要向 Intune 註冊其裝置，就能使用啟用 MAM 的 LOB 應用程式。

任何人都可以測試公開預覽版軟體，並閱讀相關實用文件。文件位於 msintuneappsdk 的 GitHub：

<p style="margin-left: 40px">http://www.github.com/msintuneappsdk/intune-app-wrapper-ios-preview

<p style="margin-left: 40px">http://www.github.com/msintuneappsdk/intune-app-wrapper-android-preview

在您安裝並使用適用於 Android 與 iOS 的 Microsoft Intune App Wrapping Tool 發行前版本之前，您必須：

* 檢閱適用於 Android 與 iOS 的 Microsoft Intune App Wrapping Tool 發行前版本的 Microsoft 授權條款
* 列印並保留一份授權條款供您備查。 下載及使用適用於 Android 的 Microsoft Intune App Wrapping Tool 發行前版本，即代表您同意這些授權條款。 若貴用戶不同意這些授權條款，請不要使用「軟體」。
<!---TFS 1235607--->

### <a name="intune-groups-begin-transitioning-to-azure-active-directory-in-september"></a>Intune 群組在 9 月會開始轉換到 Azure Active Directory
部分新的 Intune 帳戶將會使用 Azure Active Directory 安全性群組，而不是 Intune 使用者群組。 因為 Intune 入口網站群組頁面將會有連結，將您導向至 Azure 管理入口網站，您會知道您正在使用安全性群組。

### <a name="lookout-integration-to-protect-android-devices"></a>Lookout 整合以保護 Android 裝置
Microsoft 正在整合 Lookout 的行動威脅保護解決方案，藉由偵測裝置上的惡意程式碼、高風險 App 等等，以保護 Android 行動裝置。 Lookout 的解決方案有助於您判斷威脅層級 (可設定)。 您可以根據 Lookout 的風險評估，在 Intune 中建立相容性原則規則，來決定裝置相容性。 您可以利用條件式存取原則，根據裝置相容性狀態，允許或封鎖公司資源的存取。

系統將會提示不相容裝置的使用者進行註冊，並且要求使用者在 Android 裝置上安裝 Lookout for Work 應用程式、啟動應用程式，並修復 Lookout for Work 應用程式中所報告的威脅，才能取得存取權。 若要深入了解，請參閱[根據裝置、網路和應用程式風險限制存取](restrict-access-based-on-device-network-app-risk.md)。


### <a name="company-portal-updates"></a>公司入口網站更新

__Android__

<p style="margin-left: 40px">**在適用於 Android 的公司入口網站新增「通知」**<br/>
<p style="margin-left: 40px">適用於 Android 的公司入口網站的首頁新增了通知圖示。 點選此圖示可存取 [通知] 頁面，為您的終端使用者顯示公司入口網站應用程式中所有需要注意的項目，例如裝置不相容、註冊更新，以及註冊啟用。 iOS 公司入口網站應用程式已經有這項通知體驗。 有了新的 [通知] 頁面，只要該裝置已經註冊，使用者便不會在每次啟動或繼續使用公司入口網站時看見 [公司存取設定] 頁面。 如果您建立自己的終端使用者指南，建議您更新文件以反映這項變更。 [這裡](https://aka.ms/androidcpupdate)提供更新的螢幕擷取畫面。  

__iOS__
<p style="margin-left: 40px">**支援的 iOS 公司入口網站應用程式變更**<br/>
<p style="margin-left: 40px">iOS 版 Microsoft Intune 公司入口網站 App 的所有使用者，現在都必須使用最新版本。 新使用者可以只下載最新版本，而目前的使用者必須更新至最新版本。 最新版本需要 iOS 8.0 或更新版本，因此除非使用者將其裝置更新為 iOS 8.0 或更新版本，然後將公司入口網站 App 更新為最新版本，否則執行較舊 iOS 版本的裝置將無法使用公司入口網站或註冊。 執行 iOS 8.0 以下版本的已註冊裝置會繼續受到管理，並且列在 Intune 管理主控台中。
<!---TFS 1283165--->

<p style="margin-left: 40px">**iOS 終端使用者取得應用程式方式的改進**<br/>
<p style="margin-left: 40px">iOS 版公司入口網站 App 已經對應用程式磚進行下列變更，將使用者指向單一位置 (公司入口網站) 中不同檢視，以取得他們所有的 App。 Apple 限制禁止公司入口網站 App 列出企業營運及受管理市集應用程式，因此使用者必須瀏覽不同的檢視才能找到所有的 App。

<p style="margin-left: 40px">[公司應用程式] 磚先前會指向公司入口網站 [所有] 索引標籤中所有 App 的清單，而它會繼續以相同方式運作。 磚的名稱已變更為 [所有應用程式]。

<p style="margin-left: 40px">[其他應用程式] 磚先前會指向公司入口網站 App 中的檢視，其中會列出 Apple 允許在公司入口網站 App 中顯示的所有 App。 磚的名稱已變更為 [精選應用程式]，點選磚會將使用者移至公司入口網站的 [精選] 索引標籤。

<p style="margin-left: 40px">[類別] 磚先前會指向公司入口網站 App 中列出 App 類別的檢視。 磚的名稱並未變更，但它現在指向公司入口網站的 [類別] 索引標籤。 您可以在[這裡](https://gallery.technet.microsoft.com/Improvements-in-how-iOS-d1104186)找到更新的螢幕擷取畫面。
  <!---TFS 1317133--->

<p style="margin-left: 40px">**提示安裝 iOS Managed Browser 應用程式 (若 IT 專業人員針對應用程式設定該需求)**<br/>
<p style="margin-left: 40px">如果您已經設定僅能在受管理的瀏覽器中開啟 Web Clip，而裝置上並未安裝受管理的瀏覽器，裝置上的公司入口網站 App 將會提示使用者安裝受管理的瀏覽器，然後才能安裝網 Web Clip。
  <!---TFS 1228570--->

__Windows__
<p style="margin-left: 40px">**Windows Phone 8.1 的公司入口網站應用程式新增了 [意見反應] 按鈕**<br/>
<p style="margin-left: 40px">Windows Phone 8.1 公司入口網站應用程式讓終端使用者能夠使用新的 [傳送意見反應] 按鈕，傳送對應用程式的意見反應。 若要尋找按鈕，使用者要點選公司入口網站應用程式畫面右下角的「三個點」功能表，然後點選 **[傳送意見反應]**。 收集到的匿名意見反應可協助 Microsoft 改進使用者的公司入口網站應用程式體驗。
<!---TFS 1317806--->

### <a name="intune-glossarybr"></a>Intune 字彙</br>
我們已將新的[字彙主題](https://docs.microsoft.com/intune/understand-explore/intune-glossary)新增至文件庫，協助您了解 Intune 產品中所使用的一些術語。

### <a name="see-also"></a>請參閱
如需近期發展的詳細資料，請參閱 [Microsoft Intune 的新功能](whats-new-in-microsoft-intune.md)。



<!--HONumber=Nov16_HO2-->



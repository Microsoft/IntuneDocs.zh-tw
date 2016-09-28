---
title: "新功能 | Microsoft Intune"
description: "了解本月 Microsoft Intune 版本的新功能，以及過去的版本"
keywords: 
author: barlanmsft
manager: angrobe
ms.date: 09/22/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: fab51ee0-638d-4dd4-8d8f-1f263bc11e5c
ms.reviewer: mamoriss
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 5b3256852431efb83fb2cc9fa067dd3f4a68a050
ms.openlocfilehash: cef0a26204a22c95d2b639500246e435fcf7f9f7


---

# Microsoft Intune 的新功能 -- 9 月
了解此 Microsoft Intune 版本中的新功能。 您也可以了解即將推出且您應該加以規劃的變更，以及過去版本的相關資訊。

混合式客戶部署於未來將會支援這些功能 (具備 Intune 的 Configuration Manager)。 如需新混合式功能的詳細資訊，請查看我們的 [Hybrid What’s New](https://technet.microsoft.com/library/mt718155.aspx) (混合式新功能) 頁面。
<!---@Barry, the above blurb stays in each version, but make sure Tyler signs off each time. Also, remember to set the ms.date in the metadata to the sprint release. --->

>[!IMPORTANT]
>部落格文章 - 使用 Microsoft Intune 確保行動裝置維持最新狀態<br>
>我們針對 iOS 裝置上最近的 "Trident" 惡意程式碼攻擊，新發行了一篇部落格文章：[Ensuring mobile devices are up to date using Microsoft Intune](https://blogs.technet.microsoft.com/enterprisemobility/2016/08/26/ensuring-mobile-devices-are-up-to-date-using-microsoft-intune/) (確定使用 Microsoft Intune 的行動裝置為最新狀態)，說明 Intune 所提供的各種方法，如何協助您保護裝置安全及保持裝置為最新狀態。

## iOS 10 支援
現有的 Intune MDM 與 MAM 案例與 iOS 10 相容。 如需秘訣，請參閱 [Intune 支援小組部落格](https://blogs.technet.microsoft.com/intunesupport/2016/09/13/support-tip-intune-support-for-ios-10/)。

## App Wrapping Tool 支援 MAM，不需要 Android 和 iOS 裝置註冊
Intune App Wrapping Tool 是命令列工具，用於在 iOS 和 Android 的企業營運 (LOB) 應用程式上啟用 Intune MAM。 它是將 Intune MAM SDK 併入到您 App 最簡單的方式，讓您的 App 可以強制執行透過 Intune 部署的 MAM 原則。 使用 MAM 原則，您可以：

1. 加密 App 的資料。
2. 要求資訊工作者啟動 App 時輸入 PIN。
3. 讓 App 只能傳送資料給其他受管理的 App。
4. 防止 App 將資料備份到 Android、iTunes 及 iCloud。
5. 僅允許對/從其他受管理的 App 執行剪下、複製和貼上。

更新的 Intune App Wrapping Tool 公開預覽版現在支援 MAM，而不需要在 iOS 和 Android 上的內部 LOB 應用程式裝置註冊。 這表示您的使用者不需要向 Intune 註冊其裝置，就能使用啟用 MAM 的 LOB 應用程式。

任何人都可以測試公開預覽版軟體，並閱讀相關實用文件。文件位於 msintuneappsdk 的 GitHub：

http://www.github.com/msintuneappsdk/intune-app-wrapper-ios-preview

http://www.github.com/msintuneappsdk/intune-app-wrapper-android-preview

在您安裝並使用適用於 Android 與 iOS 的 Microsoft Intune App Wrapping Tool 發行前版本之前，您必須：

* 檢閱適用於 Android 與 iOS 的 Microsoft Intune App Wrapping Tool 發行前版本的 Microsoft 授權條款
* 列印並保留一份授權條款供您備查。 下載及使用適用於 Android 的 Microsoft Intune App Wrapping Tool 發行前版本，即代表您同意這些授權條款。 若貴用戶不同意這些授權條款，請不要使用「軟體」。
<!---TFS 1235607--->

## Intune 群組在 9 月會開始轉換到 Azure Active Directory
部分新的 Intune 帳戶將會使用 Azure Active Directory 安全性群組，而不是 Intune 使用者群組。 因為 Intune 入口網站群組頁面將會有連結，將您導向至 Azure 管理入口網站，您會知道您正在使用安全性群組。

## Lookout 整合以保護 Android 裝置
Microsoft 正在整合 Lookout 的行動威脅保護解決方案，藉由偵測裝置上的惡意程式碼、高風險 App 等等，以保護 Android 行動裝置。 Lookout 的解決方案有助於您判斷威脅層級 (可設定)。 您可以根據 Lookout 的風險評估，在 Intune 中建立相容性原則規則，來決定裝置相容性。 您可以利用條件式存取原則，根據裝置相容性狀態，允許或封鎖公司資源的存取。

系統將會提示不相容裝置的使用者進行註冊，並且要求使用者在 Android 裝置上安裝 Lookout for Work 應用程式、啟動應用程式，並修復 Lookout for Work 應用程式中所報告的威脅，才能取得存取權。 若要深入了解，請參閱[根據裝置、網路和應用程式風險限制存取](restrict-access-based-on-device-network-app-risk.md)。


## 公司入口網站更新

### Android

**在適用於 Android 的公司入口網站新增「通知」**<br/>
適用於 Android 的公司入口網站的首頁新增了通知圖示。 點選此圖示可存取 [通知] 頁面，為您的終端使用者顯示公司入口網站應用程式中所有需要注意的項目，例如裝置不相容、註冊更新，以及註冊啟用。 iOS 公司入口網站應用程式已經有這項通知體驗。 有了新的 [通知] 頁面，只要該裝置已經註冊，使用者便不會在每次啟動或繼續使用公司入口網站時看見 [公司存取設定] 頁面。 如果您建立自己的終端使用者指南，建議您更新文件以反映這項變更。 [這裡](https://aka.ms/androidcpupdate)提供更新的螢幕擷取畫面。  
<!---TFS 1095560--->

**在適用於 Android 的公司入口網站提供意見反應**</br>
適用於 Android 的公司入口網站的功能表新增了新項目。 點選 [說明與意見反應] 會顯示三個動作︰
* 使用 [取得說明] 回報公司入口網站的問題給您的 IT 部門。 IT 會使用您的電子郵件用戶端建立電子郵件，並附加公司入口網站記錄。 [取得說明] 會取代 [設定] 頁面上的 [傳送資料] 功能。
* 使用 [提供意見反應] 來提供意見反應給公司入口網站小組。
* 使用 [為我們的應用程式評分]，在 Google Play 上為公司入口網站應用程式評分或評論。

### iOS
**變更 iOS 公司入口網站應用程式的支援**<br/>
iOS 版 Microsoft Intune 公司入口網站 App 的所有使用者，現在都必須使用最新版本。 新使用者可以只下載最新版本，而目前的使用者必須更新至最新版本。 最新版本需要 iOS 8.0 或更新版本，因此除非使用者將其裝置更新為 iOS 8.0 或更新版本，然後將公司入口網站 App 更新為最新版本，否則執行較舊 iOS 版本的裝置將無法使用公司入口網站或註冊。 執行 iOS 8.0 以下版本的已註冊裝置會繼續受到管理，並且列在 Intune 管理主控台中。
<!---TFS 1283165--->

**iOS 使用者取得應用程式方式的改進**<br/>
iOS 版公司入口網站 App 已經對應用程式磚進行下列變更，將使用者指向單一位置 (公司入口網站) 中不同檢視，以取得他們所有的 App。 Apple 限制禁止公司入口網站 App 列出企業營運及受管理市集應用程式，因此使用者必須瀏覽不同的檢視才能找到所有的 App。

- [公司應用程式] 磚先前會指向公司入口網站 [所有] 索引標籤中所有 App 的清單，而它會繼續以相同方式運作。 磚的名稱已變更為 [所有應用程式]。
- [其他應用程式] 磚先前會指向公司入口網站 App 中的檢視，其中會列出 Apple 允許在公司入口網站 App 中顯示的所有 App。 磚的名稱已變更為 [精選應用程式]，點選磚會將使用者移至公司入口網站的 [精選] 索引標籤。
-  [類別] 磚先前會指向公司入口網站 App 中列出 App 類別的檢視。 磚的名稱並未變更，但它現在指向公司入口網站的 [類別] 索引標籤。
您可以在[這裡](https://gallery.technet.microsoft.com/Improvements-in-how-iOS-d1104186)找到更新的螢幕擷取畫面。
<!---TFS 1317133--->

**提示安裝 iOS Managed Browser 應用程式 (若 IT 專業人員針對應用程式設定該需求)**<br/>
如果您已經設定僅能在受管理的瀏覽器中開啟 Web Clip，而裝置上並未安裝受管理的瀏覽器，裝置上的公司入口網站 App 將會提示使用者安裝受管理的瀏覽器，然後才能安裝網 Web Clip。
<!---TFS 1228570--->

### Windows
**Windows Phone 8.1 的公司入口網站應用程式新增了 [意見反應] 按鈕**<br/>
Windows Phone 8.1 公司入口網站應用程式讓終端使用者能夠使用新的 [傳送意見反應] 按鈕，傳送對應用程式的意見反應。 若要尋找按鈕，使用者要點選公司入口網站應用程式畫面右下角的「三個點」功能表，然後點選 **[傳送意見反應]**。 收集到的匿名意見反應可協助 Microsoft 改進使用者的公司入口網站應用程式體驗。
<!---TFS 1317806--->


## 未來動態

### Intune 群組轉換到 Azure Active Directory 群組
Intune 正在建立新的群組管理體驗，將在 Intune 中使用 Azure Active Directory (AAD) 安全性群組做為使用者和裝置群組。 這些群組將會**在我們推出以 Azure 為基礎的新 Intune 管理入口網站時**，用於所有群組管理、原則部署及設定檔部署上。

這個新體驗將會防止您在不同的服務上擁有重複的群組、**允許您存取一些新的 Azure Active Directory Premium (AADP) 群組功能**，以及透過 PowerShell 和 Graph 提供擴充性。 這也會統一不同企業行動管理上的群組管理體驗。

為了移動到安全性群組，**目前管理主控台**中的體驗將會進行一些修改。 **這些變更，以及 AAD 安全性群組的使用，將會被記錄在 Intune 文件中**。

Intune 的新客戶將會**比目前的租用戶更快看見某些安全性群組變更**。

除了群組管理中的變更之外，**下列功能將會被取代**：
- 於建立新群組時排除成員或群組
- 「已取消群組的使用者」和「已取消群組的裝置」群組
- 服務系統管理員角色中的「管理群組」
- 通知規則的自訂群組型警示
- 於報告中針對群組進行樞紐分析
<!--- TFS 1295329--->

### Exchange Online 和 SharePoint Online 的新條件式存取 App 原則
您將可以限制 Exchange Online 和 SharePoint Online 的存取，讓存取只能來自 Office 行動應用程式，例如 Outlook、Word、Excel 和 OneDrive。 這項新功能可完美對應 Intune 行動應用程式管理 (MAM) 原則，讓您可以封鎖存取內建電子郵件用戶端或並未使用 Intune MAM 原則設定的其他 App。 這可確保您的使用者是利用使用 Intune MAM 保護的 App 來存取組織的資料。 您可以透過 Azure 入口網站，從 Intune 行動應用程式管理開始。 尋找 [設定] 刀鋒視窗中新的 [條件式存取] 區段。



### 服務取代

- **將取代 Windows 8 版和 Windows Phone 8 版公司入口網站應用程式** <br/>
自 2016 年 10 月起，Microsoft Intune 將會取代 Windows 8 和 Windows Phone 8 公司入口網站應用程式的支援。 Microsoft Intune 也會取代 Windows Phone 8 平台的支援。 因此，您將無法註冊或更新任何 Windows Phone 8 裝置。 您可以繼續管理已註冊的 Windows Phone 8 和 Windows 8 裝置。 將 Windows Phone 8 和 Windows 8 裝置更新為 Windows 8.1 和 Windows Phone 8.1，並使用對應的 Windows 8.1 和 Windows Phone 8.1 公司入口網站應用程式繼續將應用程式發佈至這些裝置，而不受中斷。



### 雲端藍圖
請參閱 [Cloud Platform roadmap (雲端平台藍圖)](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)，隨時關注 Intune 的最新發展。


## 舊版 Intune
如果您想要查看過去六個月期間在 Intune 中的發行內容，它們會列在[舊版 Intune](previous-intune-releases.md) 一文中。

### 請參閱
* [Microsoft Intune 部落格](http://go.microsoft.com/fwlink/?LinkID=273882)
* [雲端平台藍圖](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)



<!--HONumber=Sep16_HO4-->



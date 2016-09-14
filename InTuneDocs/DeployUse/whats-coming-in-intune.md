---
title: "未來動態 | Microsoft Intune"
description: 
keywords: 
author: Lindavr
manager: angrobe
ms.date: 08/04/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: mamoriss
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 500cc93b595e04cea987bda699abf94ae010443a
ms.openlocfilehash: f45fc02003c6b40cc15fabeffff35cf0cde1a830


---

# Microsoft Intune 的未來動態 - 8 月
此資訊以非常有限的基礎在 NDA 下提供，並可能有所變更。 這裡列出的一些功能可能有截止日期，而且可能會延遲到未來的版本。 其他功能正在實驗 (測試) 中進行測試，以確保它們可供客戶使用。 如果你們有任何問題或疑慮，請洽詢 Intune/PM 人員。

此頁面會定期更新。 回頭檢查新的未來動態更新。

下列變更正在 Intune 的開發過程中。 混合式客戶部署於未來將會支援這些功能 (具備 Intune 的 Configuration Manager)。 如需新混合式功能的詳細資訊，請查看我們的 [Hybrid What’s New](https://technet.microsoft.com/en-US/library/mt718155(TechNet.10).aspx) (混合式新功能) 頁面。


## 應用程式管理
### iOS 9.3 隱藏與顯示的應用程式
若是執行 iOS 9.3 或更新版本的受監督裝置，您將能夠在 iOS 一般設定原則中使用隱藏與顯示的應用程式清單，以執行下列動作：
- 指定對使用者隱藏的應用程式清單。 使用者無法檢視或啟動這些應用程式。
- 指定使用者可檢視及啟動的應用程式清單。 無法檢視或啟動其他應用程式。

已部署的應用程式及內建 iOS 應用程式 (如「訊息」和「備忘錄」) 都是您可以指定的應用程式。
<!---TFS 1279009--->

### Samsung KNOX 裝置允許與封鎖的應用程式原則

您現在可以為 Samsung KNOX 裝置設定自訂原則，讓您可建立下列其中一個項目：
- 無法在裝置上執行的應用程式清單。 即使應用程式已安裝，在封鎖清單中定義後即無法在裝置啟動。
- 裝置使用者可從 Google Play 市集安裝的應用程式清單。 無法從市集安裝其他應用程式。

只有執行 Samsung KNOX 的裝置可使用這些設定。
<!--- For details, see [Use custom policies to allow and block apps for Samsung KNOX devices]( custom-policy-to-allow-and-block-samsung-knox-apps.md)--->
<!---TFS 1311629 --->

### 與行動應用程式管理原則 (MAM) 相容的新應用程式
無論裝置是否已註冊，適用於 [iOS](https://itunes.apple.com/app/yammer/id289559439?mt=8) 與 [Android](https://play.google.com/store/apps/details?id=com.yammer.v1) 的 Yammer 應用程式都會與 [Intune 行動應用程式管理 (MAM) 原則](/intune/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune)相容。

如需與 MAM 相容的應用程式完整清單，請參閱 [Microsoft Intune 應用程式合作夥伴](https://www.microsoft.com/en-us/cloud-platform/microsoft-intune-partners)網站。
<!--- TFS 1252335 & 1252336--->

## 裝置管理
### Android 7.0 支援
Intune 將於 8 月為即將推出的行動裝置適用 Android 7.0 作業系統提供「第 0 天」支援。
<!---TFS 1262053--->
### Google 移除 Android 7.0 裝置上的遠端密碼重設功能
Google 將會移除 Android 7.0 裝置讓 IT 管理員與終端使用者在遠端重設密碼的功能。 先前，IT 管理員可以從遠端重設使用者的密碼，而終端使用者可從公司入口網站重新其密碼。

## 群組管理
### 從 2016 年 9 月開始，Intune 群組將開始轉換到 Azure Active Directory 群組
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

## 公司入口網站

### 從公司入口網站傳送到 Microsoft 的意見反應連結
公司入口網站將可讓終端使用者在頁面底部點選新的 [意見反應] 連結，以將其網站體驗的相關意見反應傳送到 Microsoft。 收集到的匿名意見反應可協助 Microsoft 改進使用者的公司入口網站體驗。
<!--- TFS 1313657--->

### 針對 Android 公司入口網站在新增「通知」
我們將在 9 月針對 Android 推出公司入口網站的更新，該更新將會在首頁上推出新的**通知**圖示。 點選此圖示將會存取「通知」頁面，並為您的終端使用者顯示公司入口網站應用程式中所有需要注意的項目，例如裝置不相容、註冊更新，以及註冊啟用。 如果您也使用 iOS 公司入口網站應用程式，您應該已能見到該通知體驗。 透過推出「通知」頁面，只要該裝置已經註冊，您便不會在每次啟動或繼續 Android 版的公司入口網站時看見「公司存取設定」頁面。 我們了解有許多使用者已建立終端使用者指南，並樂於在該指南/螢幕擷取畫面可能需要更新時提前收到通知。 請更新您的文件以反映即將推出的體驗變更。 如需更新的螢幕擷取畫面，請前往：https://gallery.technet.microsoft.com/Addition-of-Notifications-02e2e0a3。  

### iOS 使用者取得應用程式方式的改進
下列對於 iOS 版「公司入口網站」應用程式中應用程式磚的變更將於 9 月進行，這會將使用者指向單一位置 (公司入口網站) 中的不同檢視，以取得他們所有的應用程式。 目前，Apple 限制禁止「公司入口網站」應用程式中列出企業營運應用程式及受管理的應用程式市集應用程式，並且要求使用者瀏覽不同的檢視才能找到所有的應用程式。

- [公司應用程式] 磚目前會指向公司入口網站 [所有] 索引標籤中所有應用程式的清單，而它會繼續以相同方式運作。 磚的名稱將會變更為 [所有應用程式]。
- [其他應用程式] 磚目前會指向「公司入口網站」應用程式中的檢視，其中會列出 Apple 允許在公司入口網站應用程式中顯示的所有應用程式。 磚的名稱將會變更為 [精選應用程式]，點選磚會將使用者移至公司入口網站的 [精選] 索引標籤。
-  [類別] 磚目前會指向公司入口網站應用程式中列出應用程式類別的檢視。 磚的名稱不會變更，但它現在會指向公司入口網站的 [類別] 索引標籤。
您可以在[這裡](https://gallery.technet.microsoft.com/Improvements-in-how-iOS-d1104186)找到更新的螢幕擷取畫面。
<!---TFS 1317133--->

### 提示安裝 iOS Managed Browser 應用程式 (若 IT 專業人員針對應用程式設定該需求)
在 iOS 公司入口網站應用程式的 9 月版本中，如果您已經設定僅能在受管理的瀏覽器中開啟網路美工圖案，而裝置上並未安裝受管理的瀏覽器，裝置上的公司入口網站應用程式將會提示使用者安裝受管理的瀏覽器，然後才能安裝網路美工圖案。 
<!---TFS 1228570--->

## 服務取代
### 將自 2016 年 9 月起取代 Windows 8 和 Windows Phone 8 的公司入口網站應用程式
自 2016 年 10 月起，Microsoft Intune 將會取代 Windows 8 和 Windows Phone 8 公司入口網站應用程式的支援。 Microsoft Intune 也會取代 Windows Phone 8 平台的支援。 因此，您將無法註冊或更新任何 Windows Phone 8 裝置。 您可以繼續管理已註冊的 Windows Phone 8 和 Windows 8 裝置。 將 Windows Phone 8 和 Windows 8 裝置更新為 Windows 8.1 和 Windows Phone 8.1，並使用對應的 Windows 8.1 和 Windows Phone 8.1 公司入口網站應用程式繼續將應用程式發佈至這些裝置，而不受中斷。
<!---TFS 1255391--->

### 移除通知規則的自訂群組目標
Intune 通知規則會定義要從 Intune 傳送電子郵件警示給誰。 目前，您可以設定通知規則，傳送電子郵件給您建立之 Intune 裝置群組中裝置的所有使用者。 自 2016 年 6 月起，即不再支援以使用者建立的群組為目標。

這項變更的初步時間軸如下︰
- 自 2016 年 9 月起，新租用戶將不再會看到 [建立通知規則精靈] 的步驟 2。 現有租用戶不受影響。
- 大約從 2016 年 10 月起，現有一些租用戶將不再會在精靈中看到 [選取裝置群組]。
- 近期，所有租用戶將不再會在精靈中看到 [選取裝置群組]。

<!---   TFS 1278864--->
### 變更 iOS 公司入口網站應用程式的支援
自 9 月起，iOS 版 Microsoft Intune 公司入口網站應用程式的所有使用者都必須使用最新版本。 新使用者只可以下載最新版本，目前使用者則需要它的更新。 最新版本需要 iOS 8.0 或更新版本，因此除非他們將其裝置更新為 iOS 8.0 或更新版本，然後將公司入口網站應用程式更新為最新版本，否則執行較舊 iOS 版本的裝置會無法使用公司入口網站或註冊。 執行 iOS 8.0 以下版本的已註冊裝置會繼續受到管理，並且列在 Intune 管理主控台中。

<!---TFS 1283165--->


### Intune Viewer 應用程式
發佈新的 RMS 共用應用程式版本後，我們會在 2016 年 8 月移除下列 Intune Viewer 應用程式︰
- Intune AV Viewer
- Intune PDF Viewer
- 來自 Google Play 的 Intune Image Viewer for Android

我們建議使用 Android 的新授權管理應用程式 (RMS 共用)，而不是使用 Intune Viewer 應用程式，它可讓您部署一個應用程式，而不必部署三個不同的應用程式，即可安全地在 Android 裝置上檢視公司檔案。 深入了解 [RMS 共用應用程式](https://docs.microsoft.com/en-us/intune/deploy-use/end-user-experience-for-mam-enabled-apps-with-microsoft-intune#viewing-media-files-with-the-rights-management-sharing-app)。
<!--- goes in 1608 What's New--->


### 請參閱
如需近期發展的詳細資料，請參閱 [Microsoft Intune 的新功能](whats-new-in-microsoft-intune.md)。



<!--HONumber=Aug16_HO5-->



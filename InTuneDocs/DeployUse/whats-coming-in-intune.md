---
title: "未來動態 | Microsoft Intune"
description: 
keywords: 
author: Lindavr
manager: jeffgilb
ms.date: 07/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: mamoriss
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 35ee5d0c8898c95898c0527a623cf13c454387f2
ms.openlocfilehash: 831cec6cd0e02a94c1a3f67d4adf5a5dcbb01449


---

# Microsoft Intune 的未來動態 - 7 月
此資訊以非常有限的基礎在 NDA 下提供，並可能有所變更。 這裡列出的一些功能可能有截止日期，而且可能會延遲到未來的版本。 其他功能正在實驗 (測試) 中進行測試，以確保它們可供客戶使用。 如果你們有任何問題或疑慮，請洽詢 Intune/PM 人員。

此頁面會定期更新。 回頭檢查新的未來動態更新。

下列變更正在 Intune 的開發過程中。 混合式客戶部署於未來將會支援這些功能 (具備 Intune 的 Configuration Manager)。 如需新混合式功能的詳細資訊，請查看我們的 [Hybrid What’s New](https://technet.microsoft.com/en-US/library/mt718155(TechNet.10).aspx) (混合式新功能) 頁面。


## 應用程式管理
### 改善應用程式佈建設定檔更新體驗
Apple iOS 企業營運行動應用程式已內建佈建設定檔，以及透過憑證簽署的程式碼。 當該應用程式於 iOS 裝置上執行時，iOS 會確認該 iOS 應用程式的完整性，並強制執行由佈建設定檔定義的原則。

您用來簽署應用程式的企業簽署憑證通常會持續 3 年。 不過佈建設定檔將會在 1 年後到期。 透過此更新，Intune 將會提供您工具，可讓您在裝置擁有即將到期的應用程式，但憑證仍然有效的情況下，主動將新的佈建設定檔原則部署到裝置。
<!--- TFS 1280247--->

### Xamarin 支援
Microsoft Intune 應用程式 SDK 現在在下列情況下已可支援 Xamarin 應用程式︰

- 撰寫新的應用程式，或使用 Intune SDK 修改現有企業營運應用程式的程式碼。 您可以在 [Microsoft Intune Github](https://github.com/msintuneappsdk) 頁面中取得此外掛程式。
- 使用 Intune App Wrapping Tool 將 MAM 支援新增至現有的企業營運應用程式。

如需協助選擇要使用的方法，請參閱 [Decide how to prepare apps for mobile application management with Microsoft Intune](https://docs.microsoft.com/en-us/intune/deploy-use/decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune) (決定如何準備應用程式以使用 Microsoft Intune 進行行動應用程式管理)。

<!--- TFS 1061478 & TFS 1152340--->

## 裝置管理
### 提升裝置註冊限制
Intune 將會把每位使用者可設定裝置註冊最大值的限制，從 5 部裝置提升到 15 部裝置。
<!---TFS 1289896 --->

## 群組管理
### 從 2016 年 8 月開始，Intune 群組將開始轉換到 Azure Active Directory 群組
Intune 正在建立新的群組管理體驗，將在 Intune 中使用 Azure Active Directory (AAD) 安全性群組做為使用者和裝置群組。 這些群組將會**在我們推出以 Azure 為基礎的新 Intune 管理入口網站時**，用於所有群組管理、原則部署及設定檔部署上。

這個新體驗將會防止您在不同的服務上擁有重複的群組、**允許您存取一些新的 Azure Active Directory Premium (AADP) 群組功能**，以及透過 PowerShell 和 Graph 提供擴充性。 這也會統一不同企業行動管理上的群組管理體驗。

為了移動到安全性群組，**目前管理主控台**中的體驗將會進行一些修改。 **這些變更，以及 AAD 安全性群組的使用，將會被記錄在 Intune 文件中**。

Intune 的新客戶將會**比目前的租用戶更快看見某些安全性群組變更**。

除了群組管理中的變更之外，**下列功能將會被取代**：
- 於建立新群組時排除成員或群組
- 服務系統管理員角色中的「管理群組」
- 通知規則的自訂群組型警示
- 於報告中針對群組進行樞紐分析


## 公司入口網站

### 針對 Android 公司入口網站在新增「通知」
我們將在 8 月針對 Android 推出公司入口網站的更新，該更新將會在首頁上推出新的「通知」圖示。 點選此圖示將會存取「通知」頁面，並為您的終端使用者顯示公司入口網站應用程式中所有需要注意的項目，例如裝置不相容、註冊更新，以及註冊啟用。 如果您也使用 iOS 公司入口網站應用程式，您應該已能見到該通知體驗。 透過推出「通知」頁面，只要該裝置已經註冊，您便不會在每次啟動或繼續 Android 版的公司入口網站時看見「公司存取設定」頁面。 我們了解有許多使用者已建立終端使用者指南，並樂於在該指南/螢幕擷取畫面可能需要更新時提前收到通知。 請更新您的文件以反映即將推出的體驗變更。 如需更新的螢幕擷取畫面，請移至：https://aka.ms/androidcpupdate  

### 於「加入工作場所」失敗時協助使用者解決註冊問題
當您使用條件式存取時，公司入口網站中針對 Windows 8.1、Windows 10 Desktop 及 Windows 10 行動裝置版的註冊步驟，將會針對遇到「加入工作場所 (WPJ)」失敗的終端使用者進行簡化。 之前當終端使用者嘗試註冊及執行 WPJ，並遇到註冊成功但 WPJ 失敗的情況時，已註冊的裝置不會出現在供使用者識別的裝置清單上，這對使用者造成困惑。 使用者現在將能見到個別的「裝置註冊」和「加入工作場所」步驟，使他們能更輕鬆地查看裝置的狀態，並能在遇到 WPJ 失敗後完成程序。 個別的步驟應該也能為 IT 系統管理員簡化疑難排解程序。

### iOS 公司入口網站應用程式中的裝置註冊管理員帳戶變更
為提升效能及規模，Intune 已不再於公司入口網站的 [我的裝置] 窗格中，顯示所有的裝置註冊管理員 (DEM) 裝置。 只會顯示執行應用程式的本機裝置，並且只有在透過公司入口網站應用程式註冊時才會顯示。 DEM 使用者可以對本機裝置執行動作，但只能從 Intune 系統管理主控台對其他已經註冊的裝置執行遠端管理。  此外，Intune 將會使用 DEM 帳戶取代 Apple 裝置註冊方案或 Apple Configurator 工具。 這兩種註冊方法已經支援共用之 iOS 裝置的較少使用者註冊。 只有在共用裝置的較少使用者註冊無法使用時，才能使用 DEM 帳戶。
<!---TFS 1233681--->
### 將側載應用程式安裝限制於已註冊的 Android 裝置
Android 裝置已無法透過公司入口網站安裝應用程式，除非該裝置已使用 Android 版 Intune 公司入口網站應用程式在 Intune 註冊。 
<!---TFS 1299082--->

## 服務取代
**將在 2016 年 9 月取代 Windows 8 和 Windows Phone 8 的公司入口網站應用程式。** 從 2016 年 9 月開始，Microsoft Intune 將結束 Windows Phone 8 和 Windows 8 平台的 Microsoft Intune 公司入口網站應用程式支援。 將裝置更新為 Windows 8.1 和 Windows Phone 8.1，並使用對應的 Windows 8.1 和 Windows Phone 8.1 公司入口網站應用程式繼續將應用程式發佈至這些裝置。
<!---TFS 1255391--->

**通知規則移除的自訂群組目標。**
Intune 通知規則會定義要從 Intune 傳送電子郵件警示給誰。 目前，您可以設定通知規則，傳送電子郵件給您建立之 Intune 裝置群組中裝置的所有使用者。 從 2016 年 6 月 1 日起，將不再支援將目標設定為使用者建立的群組。

這項變更的初步時間軸如下︰
- 自 2016 年 8 月起，新租用戶將不再會看到 [建立通知規則精靈] 的步驟 2。 現有租用戶不受影響。
- 大約從 2016 年 9 月起，現有一些租用戶將不再會在精靈中看到 [選取裝置群組]。
- 我們預計大約從 2016 年 10 月起，所有租用戶將不再會在精靈中看到 [選取裝置群組]。

<!---   TFS 1278864--->

**支援的 iOS 公司入口網站應用程式變更。**
自七月起，iOS 版 Microsoft Intune 公司入口網站應用程式的所有使用者都必須使用最新版本。 新使用者只可以下載最新版本，目前使用者則需要它的更新。 最新版本需要 iOS 8.0 或更新版本，因此除非他們將其裝置更新為 iOS 8.0 或更新版本，然後將公司入口網站應用程式更新為最新版本，否則執行較舊 iOS 版本的裝置會無法使用公司入口網站或註冊。 執行 iOS 8.0 以下版本的已註冊裝置會繼續受到管理，並且列在 Intune 管理主控台中。  

**Intune Viewer 應用程式。** 發佈新的 RMS 共用應用程式版本後，我們會移除下列 Intune Viewer 應用程式，從 2016 年 8 月開始︰
- Intune AV Viewer
- Intune PDF Viewer
- 來自 Google Play 的 Intune Image Viewer for Android

我們建議使用 Android 的新授權管理應用程式 (RMS 共用)，而不是使用 Intune Viewer 應用程式，它可讓您部署一個應用程式，而不必部署三個不同的應用程式，即可安全地在 Android 裝置上檢視公司檔案。 進一步了解 RMS 共用應用程式 (使用文件連結)。



### 請參閱
如需近期發展的詳細資料，請參閱 [Microsoft Intune 的新功能](whats-new-in-microsoft-intune.md)。



<!--HONumber=Jul16_HO3-->



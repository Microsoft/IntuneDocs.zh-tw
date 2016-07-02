---
title: "未來動態 | Microsoft Intune"
description: 
keywords: 
author: Lindavr
manager: jeffgilb
ms.date: 06/10/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: mamoriss
ms.suite: ems
ms.sourcegitcommit: b203f51171d38f2b0fc2b46e556679322701d29b
ms.openlocfilehash: 77d2e74dcb032ff52808998c56de7d6b8847ebbe


---

# Microsoft Intune 的未來動態
此資訊以非常有限的基礎在 NDA 下提供，並可能有所變更。 這裡列出的一些功能可能有截止日期，而且可能會延遲到未來的版本。 其他功能正在實驗 (測試) 中進行測試，以確保它們可供客戶使用。 如果你們有任何問題或疑慮，請洽詢 Intune/PM 人員。

此頁面會定期更新。 回頭檢查新的未來動態更新。

下列變更正在 Intune 的開發過程中。 混合式客戶部署也支援這些功能 (Configuration Manager 與 Intune)。 如需新混合式功能的詳細資訊，請查看我們的 [Hybrid What’s New](https://technet.microsoft.com/en-US/library/mt718155(TechNet.10).aspx) (混合式新功能) 頁面。


## 應用程式管理
- **改善 Windows 10 企業資料的原則設定經驗。** 我們強化了建立應用程式規則、指定網路邊界定義及其他企業資料保護設定等功能，從而提升 Win 10 企業資料保護原則設定經驗。
<!---TFS 1303011--->

- **瀏覽器的條件存取** 您可以設定 Exchange Online 和 SharePoint Online 的條件式存取原則，以便只有受管理和相容的 iOS 和 Android 裝置可以存取它們。 嘗試使用 iOS 和 Android 裝置登入 Outlook Web Access (OWA) 和 SharePoint 網站的使用者將會收到提示，以其裝置向 Intune 註冊，以及在完成登入之前修正任何不相容問題。
<!---TFS 1175844--->

- **Dynamics CRM Online 支援條件式存取。** 客戶將可以設定 Dynamics CRM Online 的條件式存取原則，這樣一來，只有受管理和相容的 iOS 和 Android 裝置可以存取它。 嘗試在 iOS 和 Android 上登入 Dynamics CRM 行動應用程式的使用者將會收到提示，在登入完成之前向 Intune 註冊並補救任何不相容問題。
<!---TFS1295358--->

### Xamarin 支援
Microsoft Intune 應用程式 SDK 現在在下列情況下已可支援 Xamarin 應用程式︰

- 撰寫新的應用程式，或使用 Intune SDK 修改現有企業營運應用程式的程式碼。 您可以在 [Microsoft Intune Github](https://github.com/msintuneappsdk) 頁面中取得此外掛程式。
- 使用 Intune App Wrapping Tool 將 MAM 支援新增至現有的企業營運應用程式。

如需協助選擇要使用的方法，請參閱 [Decide how to prepare apps for mobile application management with Microsoft Intune](https://docs.microsoft.com/en-us/intune/deploy-use/decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune) (決定如何準備應用程式以使用 Microsoft Intune 進行行動應用程式管理)。
<!--- TFS 1061478 & TFS 1152340--->

## 裝置管理
- **Windows Defender 原則設定可防止潛在的垃圾應用程式。** Windows 10 Desktop 與行動裝置版的一般設定原則中，加入了一項新的 Windows Defender 設定，稱為**偵測潛在的垃圾應用程式**。 您可以使用此設定保護已經註冊的 Windows 桌上型電腦，避免執行被 Windows defender 歸類為潛在垃圾應用程式的軟體。 您可以不執行這些應用程式，也可以使用稽核模式，在安裝潛在垃圾應用程式時回報。
<!---TFS 1244478--->

## 條件式存取
**Intune 的 Cisco ISE 網路存取控制原則。**  同時使用 Cisco Identity Service Engine (ISE) 2.1 與 Microsoft Intune 的客戶，可以在 ISE 中設定網路存取控制原則。

若要使用此原則，裝置必須透過 WiFi 或 VPN 連線到網路，而且必須符合下列條件，才具備存取資格︰

* 必須是 Intune 管理的裝置。
* 必須符合所部署的任何 Intune 相容性原則。

不相容裝置的使用者會收到提示，要求其註冊及修復任何相容性問題，才能獲得存取權。
<!---TFS 1299144--->

## 公司入口網站
**iOS 公司入口網站應用程式中的裝置註冊管理員帳戶的變更。** 為提升效能及規模，Intune 已不再於公司入口網站的 [我的裝置] 窗格中，顯示所有的裝置註冊管理員 (DEM) 裝置。 只會顯示執行應用程式的本機裝置，並且只有在透過公司入口網站應用程式註冊時才會顯示。 DEM 使用者可以對本機裝置執行動作，但只能從 Intune 系統管理主控台對其他已經註冊的裝置執行遠端管理。  此外，Intune 將會使用 DEM 帳戶取代 Apple 裝置註冊方案或 Apple Configurator 工具。 這兩種註冊方法已經支援共用之 iOS 裝置的較少使用者註冊。 只有在共用裝置的較少使用者註冊無法使用時，才能使用 DEM 帳戶。
<!---TFS 1233681--->

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
如需近期發展的詳細資廖，請參閱 [Microsoft Intune 的新功能](whats-new-in-microsoft-intune.md)。



<!--HONumber=Jun16_HO3-->



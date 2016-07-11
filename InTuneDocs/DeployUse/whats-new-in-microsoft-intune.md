---
title: "新功能 | Microsoft Intune"
description: "了解本月 Microsoft Intune 版本的新功能，以及過去的版本"
keywords: 
author: Lindavr
manager: jeffgilb
ms.date: 06/16/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: fab51ee0-638d-4dd4-8d8f-1f263bc11e5c
ms.reviewer: mamoriss
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 79617dd41e51402a73759da792f581028095a2f5
ms.openlocfilehash: 65e53ad6a74fbf0e9249c367f517ab52ea0efa80


---

# Microsoft Intune 的新功能
了解此 Microsoft Intune 版本中的新功能。 您也可以了解即將推出且您應該加以規劃的變更，以及過去版本的相關資訊。

以下是此版本中的新功能。 除了 Windows Defender 原則設定更新，所有這些功能支援混合式客戶的部署 (Configuration Manager 與 Intune)。 如需新混合式功能的詳細資訊，請查看我們的 [Hybrid What’s New](https://technet.microsoft.com/en-US/library/mt718155(TechNet.10).aspx) (混合式新功能) 頁面。

## 2016 年 6 月
### Intune 服務健全狀況
Intune 的服務健全狀況資訊已與其他 Microsoft 服務一起移至中央位置。 現在，您會在 Office 365 管理入口網站的 [服務健全狀況] 下發現這項資訊。 如需詳細資訊，請參閱[這篇部落格文章](https://blogs.technet.microsoft.com/enterprisemobility/2016/04/28/intune-service-health-is-now-available-in-the-office-365-portal/)。

## 應用程式管理
- **改善 Windows 10 企業資料的原則設定經驗。** 我們強化了建立應用程式規則、指定網路邊界定義及其他企業資料保護設定等功能，從而提升 Windows 10 企業資料保護原則設定經驗。 若要深入了解，請參閱 [Create an enterprise data protection (EDP) policy using Microsoft Intune](https://technet.microsoft.com/itpro/windows/keep-secure/create-edp-policy-using-intune) (使用 Microsoft Intune 建立企業資料保護 (EDP) 原則)。


## 裝置管理
- **Windows Defender 原則設定可防止潛在的垃圾應用程式。** Windows 10 Desktop 與行動裝置版的一般設定原則中，加入了一項新的 Windows Defender 設定，稱為**偵測潛在的垃圾應用程式**。 您可以使用此設定保護已經註冊的 Windows 桌上型電腦，避免執行被 Windows defender 歸類為潛在垃圾應用程式的軟體。 您可以不執行這些應用程式，也可以使用稽核模式，在安裝潛在垃圾應用程式時回報。 如需詳細資訊，請參閱 [Microsoft Intune 的 Windows 10 原則設定](https://docs.microsoft.com/en-us/intune/deploy-use/windows-10-policy-settings-in-microsoft-intune)
<!---TFS 1244478--->

## 條件式存取
- **Intune 的 Cisco ISE 網路存取控制原則。**  同時使用 Cisco Identity Service Engine (ISE) 2.1 與 Microsoft Intune 的客戶，可以在 ISE 中設定網路存取控制原則。

    若要使用此原則，裝置必須透過 WiFi 或 VPN 連線到網路，而且必須符合下列條件，才具備存取資格︰

    * 必須是 Intune 管理的裝置。
    * 必須符合所部署的任何 Intune 相容性原則。

 不相容裝置的使用者會收到提示，要求其註冊及修復任何相容性問題，才能獲得存取權。
- **瀏覽器的條件存取** 您可以設定 [Exchange Online](restrict-access-to-exchange-online-with-microsoft-intune.md) 和 [SharePoint Online](restrict-access-to-sharepoint-online-with-microsoft-intune.md) 的條件式存取原則，以便只能從受管理和相容的 iOS 和 Android 裝置上的支援瀏覽器存取它們。 嘗試使用 iOS 和 Android 裝置登入 Outlook Web Access (OWA) 和 SharePoint 網站的使用者將會收到提示，以其裝置向 Intune 註冊，以及在完成登入之前修正任何不相容問題。
<!---TFS 1175844--->

- **Dynamics CRM Online 支援條件式存取。** 您可以設定 [Dynamics CRM Online](restrict-access-to-dynamics-crm-online-with-microsoft-intune.md) 的條件式存取原則，以便只有受管理和相容的 iOS 和 Android 裝置可以存取它。 嘗試在 iOS 和 Android 上登入 Dynamics CRM 行動應用程式的使用者將會收到提示，在登入完成之前向 Intune 註冊並補救任何不相容問題。
<!---TFS1295358--->

## 公司入口網站更新

### Android 公司入口網站應用程式

- 當 IT 系統管理員套用新的「裝置必須防止從不明來源安裝應用程式 (Android 4.0+)」原則時，使用 Android 4.0 或更新版本之裝置的使用者會看到訊息：「必須停用來自未知來源的安裝」。 使用者必須移至 [設定]  >  [安全性]，並關閉 [未知來源]。 相容性訊息中的連結可讓使用者取得訊息的[相關資訊](/Intune/EndUser/you-are-asked-to-turn-off-unknown-sources-android)，以及為什麼他們需要關閉設定。

- 當 IT 系統管理員套用新的「裝置必須已啟用掃描應用程式的安全性威脅 (Android 4.0+)」原則時，使用 Android 4.0 或更新版本之裝置的使用者將會看到訊息：「掃描裝置中的安全性威脅」。 使用者必須移至 [設定]  >  [Google]  >  [安全性]，然後開啟 [掃描裝置中的安全性威脅]。 相容性訊息中的連結可讓使用者取得訊息的[相關資訊](/Intune/EndUser/you-are-asked-to-turn-on-scan-device-for-security-threats-android)，以及為什麼他們需要開啟設定。

- 當 IT 系統管理員套用新的「USB 偵錯需為停用 (Android 4.2+)」原則時，使用 Android 4.2 或更新版本之裝置的使用者將會看到訊息：「必須停用 USB 偵錯」。 使用者必須移至 [設定]  >  [開發人員選項]，並關閉 [USB 偵錯]。 相容性訊息中的連結可讓使用者取得訊息的[相關資訊](/Intune/EndUser/you-are-asked-to-turn-off-usb-debugging-android)，以及為什麼他們需要關閉設定。

- 當 IT 系統管理員套用新的「Android 安全性修補程式等級下限 (Android 6.0+)」原則時，使用 Android 6.0 或更新版本之裝置的使用者將會看到訊息：「此裝置不符合最低的 Android 安全性更新程式層級」。 使用者必須安裝所需的安全性修補程式。 相容性訊息中的連結可讓使用者取得如何安裝必要安全性修補程式以及查看目前已安裝之安全性修補程式的[相關資訊](/Intune/EndUser/you-are-asked-to-turn-on-scan-device-for-security-threats-android)。

### iOS 公司入口網站應用程式

- 當使用者安裝企業營運應用程式時，就會看到改善的應用程式安裝體驗。 如果應用程式安裝花很長的時間，使用者可以手動同步處理他們的裝置，以強制同步處理程序繼續執行。 若要檢閱使用者指示，請參閱[手動同步處理您的 iOS 裝置](/Intune/EndUser/sync-your-device-manually-ios)。

- 適用於 iOS 的 Microsoft Intune 公司入口網站應用程式已更新為支援 iOS 8.0 和更新版本。 此更新表示唯有裝置執行的是 iOS 8.0 版或更新版本時，使用者才能安裝公司入口網站應用程式以及在 Intune 中註冊新的裝置。 若使用者已經註冊在不支援的 iOS 版本中執行的裝置，則可繼續使用其裝置上的公司入口網站應用程式。


## 未來動態

### 雲端藍圖
請參閱 [Cloud Platform roadmap (雲端平台藍圖)](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)，隨時關注 Intune 的最新發展。

### 服務取代
- **Intune Viewer 應用程式。** 發佈新的 RMS 共用應用程式版本後，我們會移除下列 Intune Viewer 應用程式，從 2016 年 8 月開始︰
    - Intune AV Viewer
    - Intune PDF Viewer
    - 來自 Google Play 的 Intune Image Viewer for Android

  我們建議使用 Android 的新授權管理應用程式 (RMS 共用)，而不是使用 Intune Viewer 應用程式，它可讓您部署一個應用程式，而不必部署三個不同的應用程式，即可安全地在 Android 裝置上檢視公司檔案。

- **通知規則移除的自訂群組目標。**
Intune 通知規則會定義要從 Intune 傳送電子郵件警示給誰。 目前，您可以設定通知規則，傳送電子郵件給您建立之 Intune 裝置群組中裝置的所有使用者。 從 2016 年 6 月 1 日起，將不再支援將目標設定為使用者建立的群組。

    現在，若要將通知規則目標設定為您從 Microsoft Intune 管理主控台建立的群組，您可以採取下列步驟︰

    在 [管理] 工作區中，按一下 [通知規則] > [建立新規則]

    在 [建立通知規則精靈] 的步驟二中，選取規則以其作為目標的裝置群組。 此「選取裝置群組」步驟已從 Intune 主控台移除。

    這項變更的初步時間軸如下︰
    - 自 2016 年 8 月起，新租用戶將不再會看到 [建立通知規則精靈] 的步驟 2。 現有租用戶不受影響。
    - 大約從 2016 年 9 月起，現有一些租用戶將不再會在精靈中看到 [選取裝置群組]。
    - 我們預計大約從 2016 年 10 月起，所有租用戶將不再會在精靈中看到 [選取裝置群組]。


- **支援的 iOS 公司入口網站應用程式變更**。 自七月起，iOS 版 Microsoft Intune 公司入口網站應用程式的所有使用者都必須使用最新版本。 新使用者只可以下載最新版本，目前使用者則需要它的更新。 最新版本需要 iOS 8.0 或更新版本，因此除非他們將其裝置更新為 iOS 8.0 或更新版本，然後將公司入口網站應用程式更新為最新版本，否則執行較舊 iOS 版本的裝置會無法使用公司入口網站或註冊。 執行 iOS 8.0 以下版本的已註冊裝置會繼續受到管理，並且列在 Intune 管理主控台中。





## 舊版 Intune
如果您想要查看過去六個月期間在 Intune 中的發行內容，它們會列在[舊版 Intune](previous-intune-releases.md) 一文中。



### 請參閱
* [Microsoft Intune 部落格](http://go.microsoft.com/fwlink/?LinkID=273882)
* [雲端平台藍圖](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)



<!--HONumber=Jul16_HO1-->



---
# required metadata

title: 未來動態 | Microsoft Intune
description:
keywords:
author: Lindavr
manager: jeffgilb
ms.date: 05/03/2016
ms.topic: get-started-article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Microsoft Intune 的未來動態
此資訊以非常有限的基礎在 NDA 下提供，並可能有所變更。 這裡列出的一些功能可能有截止日期，而且可能會延遲到未來的版本。 其他功能正在實驗 (測試) 中進行測試，以確保它們可供客戶使用。 如果你們有任何問題或疑慮，請洽詢 Intune/PM 人員。

此頁面會定期更新。 回頭檢查新的未來動態更新。

下列變更正在 Intune 的開發過程中。 混合式客戶部署也支援這些功能 (Configuration Manager 與 Intune)。 如需有關新混合式功能的詳細資訊，請查看我們的[混合式新功能頁面](https://technet.microsoft.com/en-US/library/mt718155(TechNet.10).aspx).

## 訊息中心入門訓練
在 Intune 移轉至 [Office 365 管理入口網站](https://portal.office.com/)的過程中，我們將開始利用他們的訊息中心進行新功能和其他通知等通訊。  此外，藉由安裝隨附的 Office 365 管理行動應用程式，您的行動電話可以接收通知，並輕鬆地將任何訊息轉送至使用者或通訊群組別名。<br>  
我們將開始使用訊息中心以及 5 月的版本，以在更新完成時通知您，並將包含新的改善 Intune 功能的資訊。  立即登入 [Office 365 管理入口網站](https://portal.office.com/)，然後選擇左側導覽窗格中的 [訊息中心] 選項來查看訊息中心。
<!---TFS 1242782--->


## 應用程式管理
- **瀏覽器的條件存取** 您可以設定 Exchange Online 和 SharePoint Online 的條件式存取原則，以便只有受管理和相容的 iOS 和 Android 裝置可以存取它們。 嘗試使用 iOS 和 Android 裝置登入 Outlook Web Access (OWA) 和 SharePoint 網站的使用者將會收到提示，以其裝置向 Intune 註冊，以及在完成登入之前修正任何不相容問題。
<!---TFS 1175844--->

- **MAM SDK︰支援 PIN 長度組態。** 您可以將 MAM 應用程式的 PIN 長度指定為類似裝置 PIN 的長度。 這將需要使用者符合您設定的新限制。 他們會看到稍微修改的 PIN 畫面以說明較長的輸入。
<!--- TFS 1104753--->

- **避免 Outlook 連絡人同步處理 (iOS) 的 MAM 控制項。** 新的設定可供行動應用程式管理使用，而不需要裝置註冊。 此設定可讓 Intune 系統管理員防止應用程式在 iOS 裝置上將連絡人同步處理至原生通訊錄。 啟用此設定時，應用程式將不再能夠儲存連絡人到原生通訊錄。 啟用此設定時，應用程式將能夠儲存連絡人到原生通訊錄。 當 Intune 系統管理員選擇性地抹除裝置時，將會移除所有已儲存至原生通訊錄的連絡人。 在 iOS 裝置上的 Outlook 應用程式現在支援這個新的設定。
<!---TFS item 1276166--->

- **Android 的商務用 Skype。** Intune 系統管理員現在可以將目標放在具備無註冊原則之 MAM 的商務用 Skype。  一旦其使用者登入，將會套用 MAM 原則。
<!--- TFS item 1248444 --->

- **iOS 的商務用 Skype。** Intune 系統管理員現在可以將目標放在具備無註冊原則之 MAM 的商務用 Skype。  一旦其使用者登入，將會套用 MAM 原則。
<!--- TFS item 1248443 --->

### Xamarin 支援
Microsoft Intune 應用程式 SDK 現在支援這些案例中的 Xamarin 應用程式︰

- 撰寫新的應用程式，或使用 Intune SDK 修改現有企業營運應用程式的程式碼。 您可以在 [Microsoft Intune Github](https://github.com/msintuneappsdk) 頁面取得外掛程式。
- 使用 Intune App Wrapping Tool 將 MAM 支援新增至現有的企業營運應用程式。

如需協助選擇要使用的方法，請參閱[決定如何準備應用程式以使用 Microsoft Intune 進行行動應用程式管理](https://docs.microsoft.com/en-us/intune/deploy-use/decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune).
<!--- TFS 1061478 & TFS 1152340--->


## 裝置管理
- **Windows 個人電腦的遠端協助工作階段。** Windows 桌面代理程式管理電腦的 TeamViewer 整合可讓您利用Windows 桌面代理程式管理的電腦建立遠端協助工作階段，以支援使用者技術支援部門。 這包括 Windows 7、8、8.1 和 Windows 10。
<!--- TFS 1284856--->


<!--- TFS item 1274326 --->

## 存取控制
* **商務用 Skype Online 支援條件式存取。** Intune 系統管理員將可以設定商務用 Skype 的條件式存取原則，這樣一來，只有受管理和相容的 iOS 和 Android 裝置可以存取它。 嘗試在 iOS 和 Android 上登入商務用 Skype 行動應用程式的使用者將會收到提示，在登入完成之前向 Intune 註冊並修正任何不相容問題。
<!---TFS item 1254499--->

## 公司入口網站
* **裝置識別橫幅將提供詳細資訊給使用者。** 使用者可以輕鬆地識別他們在使用公司入口網站時所選取的裝置。 如果選取了錯誤的裝置，他們可以藉由點選首頁橫幅中的 [點選這裡] 連結來選取正確的裝置。
<!--- TFS 1231157--->

* Windows 應用程式套件可以直接從公司入口網站使用︰Windows 8、Windows 8.1 和 Windows RT 電腦的使用者現在可以直接從公司入口網站安裝 Windows 應用程式套件 (副檔名為 .appx)。 先前，Intune 系統管理員必須部署，或使用者必須在裝置上安裝公司入口網站應用程式才能安裝其他應用程式。
<!--- TFS item 1082481 --->

* 使用者可以從公司入口網站遠端鎖定裝置公司入口網站新增了新的遠端鎖定選項，可讓使用者在裝置遺失或遭竊時，從入口網站遠端鎖定其裝置。 下表列出 Intune 和 Intune 搭配 Configuration Manager 的遠端鎖定平台支援。
<!--- TFS item 1195661 --->

|平台  |支援詳細資料|
|---------|---------|
|iOS | 支援|
|Android | 支援|
|Windows Phone 8.1 | 支援|
|Windows 10 Mobile | 只有在電話已設定密碼時才支援|
|電腦 (Windows 8.0 及更早版本) | 不支援|
|電腦 (Windows 8.1) | 不支援|
|Windows Phone 8。0 | 不支援|
|Windows 10 Desktop | 不支援|

## 服務取代
* **通知規則移除的自訂群組目標。** 將於 2016 年 6 月初推出，您將無法再使用 [建立通知規則精靈] 將使用者建立群組與通知規則設定為目標。

    目前，若要將 Microsoft Intune 管理主控台的使用者建立群組設為目標，您要選擇 Admin > 通知規則 > 建立新規則。 在 [建立通知規則精靈] 的步驟二中，您必須選取規則以其做為目標的裝置群組。 此選取裝置群組步驟已從 Intune 主控台被取代。

    1606 年 6 月版的 Intune 之後不再支援選取裝置群組。 不過，在 2016 年 8 月之前，您將會繼續看見此選項。 8 月之後，我們將在兩個月內開始逐步將租用戶引入全新的體驗。 在 2016 年 10 月之前，所有現有的客戶都將轉換成全新的體驗。 移轉至新的體驗之後，您將不再能選擇在特定群組將通知規則設為目標。
<!---   TFS 1278864--->







### 請參閱
如需近期發展的詳細資廖，請參閱 [Microsoft Intune 的新功能](whats-new-in-microsoft-intune.md)。


<!--HONumber=May16_HO1-->



---
# required metadata

experiment_id: lindavr-abtest-20160527
experimental: true
title: 新功能 | Microsoft Intune
description:
keywords:
author: Lindavr
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: fab51ee0-638d-4dd4-8d8f-1f263bc11e5c

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Microsoft Intune 的新功能


## 2016 年 6 月

### 公司入口網站更新

#### iOS 公司入口網站應用程式

- 當使用者安裝企業營運應用程式時，就會看到改善的應用程式安裝體驗。 如果應用程式安裝花很長的時間，使用者可以手動同步處理他們的裝置，以強制同步處理程序繼續執行。 若要檢閱使用者指示，請參閱[手動同步處理您的 iOS 裝置](/Intune/EndUser/sync-your-device-manually-ios.md)。

- 適用於 iOS 的 Microsoft Intune 公司入口網站應用程式已更新為支援 iOS 8.0 和更新版本。 此更新表示唯有裝置執行的是 iOS 版本 8.0 或更新版本時，使用者才能安裝公司入口網站應用程式以及在 Intune 中註冊新的裝置。 若使用者已經註冊在不支援的 iOS 版本中執行的裝置，則可繼續使用其裝置上的公司入口網站應用程式。

## 2016 年 5 月


混合式部署也支援所有這些功能 (Configuration Manager 與 Intune)。 如需新混合式功能的詳細資訊，請查看 [Hybrid What’s New](https://technet.microsoft.com/en-us/library/mt718155.aspx) (混合式新功能) 頁面。

### 文件

歡迎使用 [docs.microsoft.com](https://docs.microsoft.com/en-us/intune) 的預覽版本！
這是全新的現代內容平台，其設計是為了讓您，也就是我們的客戶，更輕鬆地了解和使用 Intune。
若要閱讀所有新功能，請參閱 [Introducing docs.microsoft.com](https://docs.microsoft.com/teamblog/introducing-docs-microsoft-com/) (docs.microsoft.com 簡介)

### Intune 服務健全狀況
Intune 的服務健全狀況資訊已與其他 Microsoft 服務一起移至中央位置。 現在，您會在 [Office 365 管理入口網站](https://portal.office.com/Admin/Default.aspx) 的 [服務健全狀況] 下發現這項資訊。
如需詳細資訊，請參閱[這篇部落格文章](https://blogs.technet.microsoft.com/microsoftintune/2016/04/28/intune-service-health-is-now-available-in-the-office-365-portal/)。


### 應用程式管理

- **MAM SDK︰支援 PIN 長度組態。** 您可以將 MAM 應用程式的 PIN 長度指定為類似裝置 PIN 的長度。 這將需要使用者符合您設定的新限制。 他們會看到稍微修改的 PIN 畫面以說明較長的輸入。 如需詳細資訊，請參閱 [Android 的 MAM 原則設定](/intune/deploy-use/android-mam-policy-settings)和 [iOS 的 MAM 原則設定](/intune/deploy-use/ios-mam-policy-settings)。

- **iOS 和 Android 的商務用 Skype。** 您現在可以將目標放在具備[無註冊原則之 MAM](/intune/deploy-use/get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune) 的商務用 Skype。 一旦使用者登入，將會套用 MAM 原則。

- **新的應用程式可用來使用 MAM 原則進行管理。** 適用於 Android 的 Microsoft Word、Excel 和 PowerPoint 應用程式現在可以在未向 Intune 註冊的裝置上與 MAM 原則相關聯。 如需受支援應用程式的完整清單，請移至 Microsoft Intune 應用程式夥伴頁面上的 [Microsoft Intune 行動應用程式庫](https://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/partners.aspx)。


### 公司入口網站更新

#### Android 公司入口網站應用程式

- **使用者快顯通知**：使用者註冊其裝置或從公司入口網站移除他們的裝置時，將會看到來自 Android 公司入口網站應用程式的快顯通知。

- **Android 公司入口網站應用程式中的裝置註冊管理員帳戶的變更。** 為了改善效能和擴充，Intune 將不再於 Android 公司入口網站的 [我的裝置] 窗格中，顯示所有的裝置註冊管理員 (DEM) 裝置。 只有執行應用程式的本機裝置會顯示，只有在透過公司入口網站應用程式註冊時才會顯示。 DEM 使用者可在本機裝置上執行動作，但是其他已註冊裝置的遠端管理只能從 Intune 管理主控台執行。

#### 公司入口網站

- **公司入口網站：裝置識別橫幅將提供詳細資訊給使用者。** 使用者可以更輕鬆地識別他們在使用公司入口網站時所選取的裝置。 如果選取了錯誤的裝置，他們可以藉由點選首頁橫幅中的 [點選這裡] 連結來選取正確的裝置。


## 未來動態

- **訊息中心 UI 入門訓練**。 在 Intune 移轉至 [Office 365 管理入口網站](https://portal.office.com/)的過程中，我們將開始利用他們的訊息中心進行新功能和其他通知等通訊。 此外，藉由安裝隨附的 Office 365 管理行動應用程式，您的行動電話可以接收通知，並輕鬆地將任何訊息轉送至使用者或通訊群組別名。
我們將開始使用訊息中心以及 5 月的版本，以在更新完成時通知您，並將包含新的改善 Intune 功能的資訊。 立即登入 [Office 365 管理入口網站](https://portal.office.com/)，然後選擇左側瀏覽窗格中的 [訊息中心] 選項來查看訊息中心。

- **裝置註冊管理員帳戶的變更**。 為了改善效能和擴充，Intune 將不再於 iOS 公司入口網站的 [我的裝置] 窗格中，顯示**所有**的裝置註冊管理員 (DEM) 裝置。 只有執行應用程式的本機裝置會顯示，只有在透過公司入口網站應用程式註冊時才會顯示。 DEM 使用者可在本機裝置上執行動作，但是其他已註冊裝置的遠端管理只能從 Intune 管理主控台執行。 此外，Intune 將會使用 DEM 帳戶取代 Apple 裝置註冊方案或 Apple Configurator 工具。 這兩種註冊方法已經支援共用之 iOS 裝置的較少使用者註冊。 只有在共用裝置的較少使用者註冊無法使用時，才能使用 DEM 帳戶。

### 雲端藍圖
請參閱 [Cloud Platform roadmap (雲端平台藍圖)](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)，隨時關注 Intune 的最新發展。

### 服務取代
- **Intune Viewer 應用程式。** 發佈新的 RMS 共用應用程式版本後，我們會移除下列 Intune Viewer 應用程式，從 2016 年 8 月開始︰
    - Intune AV Viewer
    - Intune PDF Viewer
    - 來自 Google Play 的 Intune Image Viewer for Android

  我們建議使用 Android 的新授權管理應用程式 (RMS 共用)，而不是使用 Intune Viewer 應用程式，它可讓您部署一個應用程式，而不必部署三個不同的應用程式，即可安全地在 Android 裝置上檢視公司檔案。 進一步了解 RMS 共用應用程式 (使用文件連結)。

- **通知規則移除的自訂群組目標。**
Intune 通知規則會定義要從 Intune 傳送電子郵件警示給誰。 目前，您可以設定通知規則，傳送電子郵件給您建立之 Intune 裝置群組中裝置的所有使用者。 從 2016 年 6 月 1 日起，將不再支援將目標設定為使用者建立的群組。

    現在，若要將通知規則目標設定為您從 Microsoft Intune 管理主控台建立的群組，您可以採取下列步驟︰

    在 [管理] 工作區中，按一下 [通知規則] > [建立新規則]

    在 [建立通知規則精靈] 的步驟二中，選取規則以其作為目標的裝置群組。 此「選取裝置群組」步驟已從 Intune 主控台移除。

    這項變更的初步時間軸如下︰
    - 在 2016 年 6 月，新租用戶將不會看到 [建立通知規則精靈] 的步驟 2。 現有租用戶不受影響。
    - 在 2016 年 8 月左右，某些現有的租用戶將不會在精靈中看到 [選取裝置群組]。
    - 在 2016 年 10 月左右，我們預期所有租用戶都將不會在精靈中看到 [選取裝置群組]。


- **支援的 iOS 公司入口網站應用程式變更**。 在未來的幾個月，iOS 的 Microsoft Intune 公司入口網站應用程式將會有更新，只支援執行 8.0 或更新版本的 iOS 裝置。 使用者將無法註冊執行 iOS 8.0 以下版本的新裝置。 執行 iOS 8.0 以下版本的已註冊裝置會繼續受到管理，並且將在有限的時間內，可以繼續使用公司入口網站應用程式。 不過，裝置必須為 iOS 8.0 或更新版本，才能存取公司入口網站應用程式的最新版本。 我們鼓勵您通知使用者更新到 iOS 8.0 或更新版本，以便完全利用 Intune 的新功能。  



## 舊版 Intune
如果您想要查看過去六個月期間在 Intune 中的發行內容，它們會列在[舊版 Intune](previous-intune-releases.md) 一文中。



### 請參閱
* [Microsoft Intune 部落格](http://go.microsoft.com/fwlink/?LinkID=273882)
* [雲端平台藍圖](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)


<!--HONumber=Jun16_HO2-->



---
title: "舊版 | Microsoft Intune"
description: 
keywords: 
author: Lindavr
manager: jeffgilb
ms.date: 06/16/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 45dad14a-d412-488d-bb1e-ad990ea503df
ROBOTS: noindex,nofollow
ms.reviewer: mamoriss
ms.suite: ems
ms.sourcegitcommit: 3080d23f464e96315ed9e5fd59774ba9f1b2dd86
ms.openlocfilehash: 65d582958d77150091880cce72e079b87308209f


---

# 舊版 Intune
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


## 2016 年 4 月
混合式客戶也支援這些功能 (Configuration Manager 與 Intune 整合)。
### 應用程式管理
- **MAM 使用者相容性。**
您現在可以檢視 Azure Active Directory (AAD) 租用戶中任一使用者的應用程式管理原則[狀態](monitor-mobile-app-management-policies-with-Microsoft-Intune.md)。 這包括：
   - 裝置
   - 裝置上的應用程式

   狀態值：

   **已存回**︰表示原則已部署至使用者，且已使用工作內容中的應用程式，並成功接收原則。

    **未存回**︰表示原則已部署至使用者，但是應用程式從那時起並未在工作內容中使用。


- **避免 Outlook 連絡人同步處理 (Android) 的 MAM 控制項。**
新的設定可供[行動應用程式管理](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md)使用，而不需要裝置註冊。 此設定可讓您防止應用程式在 Android 裝置上將連絡人同步處理至原生通訊錄。 啟用此設定時，目標應用程式將不再能夠儲存連絡人到原生通訊錄。 停用此設定時，目標應用程式將能夠儲存連絡人到原生通訊錄。 當您[從遠端抹除裝置或應用程式](wipe-managed-company-app-data-with-Microsoft-Intune.md)時，將會移除所有已儲存至原生通訊錄的連絡人。 在 Android 裝置上的 Outlook 應用程式一開始支援這個新的設定。

### 裝置管理
- **公司擁有裝置的電話號碼識別。** 分類為「公司」的電話現在會在 (舉例而言) 您執行行動裝置清查報表時利用其完整電話號碼加以識別。 BYOD 電話號碼會持續以 **** 遮罩，僅顯示最後 4 位數。


### 公司入口網站更新
**Android 公司入口網站應用程式**：尚未在 Intune 中註冊其裝置，且沒有安裝正確憑證的使用者將無法登入 Android 公司入口網站應用程式，而且會看到以下訊息 -「您無法登入，因為您的裝置缺少必要的憑證」。 此訊息包含使用者可以點選以參閱安裝憑證的指示之「如何解決此問題」連結。 若要查看使用者需遵循才能解決此問題的步驟，請參閱[您的裝置遺漏必要的憑證](https://technet.microsoft.com/library/mt502762.aspx#BKMK_andr_cert_missing)。

**iOS 公司入口網站應用程式**：支援已新增至下拉以更新動作來重新整理主畫面上的內容，其中包括列出的應用程式、列出的裝置，以及 IT 連絡人資訊。 下拉更新動作並未檢查相容性或原則資訊，而這可以透過選取目前裝置的磚並點選 [同步處理] 按鈕來完成。

**Windows 10 Mobile 和 Windows Phone 8.1 公司入口網站應用程式**：當使用者安裝企業營運應用程式時，就會看到改善的應用程式安裝體驗。 如果應用程式安裝花很長的時間，使用者可以手動同步處理他們的裝置，以強制同步處理程序繼續執行。 若要檢閱使用者指示，請參閱[以手動方式同步處理您的裝置，以加速應用程式安裝](https://technet.microsoft.com/library/mt427782.aspx#BKMK_win10m_wp81_sync_manually)。

**公司入口網站**：當 Windows 10 Mobile 和 Windows Phone 8.1 使用者安裝企業營運應用程式時，他們會看到下列新狀態，可提供其安裝狀態的詳細資訊︰

* **正在等待裝置同步處理** – 使用者已點選 [安裝]，而裝置會嘗試與 Intune 基礎結構同步處理。 安裝完成之前需要同步處理。 「正在等待裝置同步處理」的訊息也是一個連結，使用者可以點選以在同步處理程序花了較長的時間或已停止時，查看如何手動將他們的裝置與 Intune 同步處理的[指示](https://technet.microsoft.com/library/mt590895.aspx#BKMK_iwp_sync_manually)。
* **正在下載** – 正在處理使用者的下載要求，且裝置正在下載與安裝應用程式。

新增這些狀態之前，如果應用程式安裝花了較長的時間，會讓使用者混淆，因為他們只看到「正在安裝」狀態，可能會在螢幕上維持時小數。 新增狀態表示，使用者現在就可以點選 [正在等待裝置同步處理] 連結，並遵循指示以強制同步處理程序繼續執行，而不是呼叫支援。


## 2016 年 3 月
### 2016 年 3 月 29 日的新功能
Windows 10 一般組態原則的更新除外，所有在 2016 年 3 月 29 日發行的功能也支援供混合式客戶使用 (Configuration Manager 與 Intune 整合)。 即將推出 Windows 10 一般組態原則更新的混合式支援。 請注意，部分功能可能需要最新版本的 Configuration Manager。

### 應用程式管理
- **避免 Outlook 連絡人同步處理 (iOS) 的 MAM 控制項。** 新的設定可供行動應用程式管理使用，而不需要裝置註冊。 此設定可讓您防止應用程式在 iOS 裝置上將連絡人同步處理至原生通訊錄。 啟用此設定時，應用程式將不再能夠儲存連絡人到原生通訊錄。 啟用此設定時，應用程式將能夠儲存連絡人到原生通訊錄。 當您選擇性地抹除裝置時，將會移除所有已儲存至原生通訊錄的所有連絡人。 iOS 裝置上的 Outlook 應用程式支援這個新的設定。 如需這個主題以及其他設定的詳細資訊，請參閱[建立和部署 MAM 原則](https://technet.microsoft.com/en-us/library/dn292747.aspx)。

### 存取控制
- **商務用 Skype Online 支援條件式存取。** 您可以設定商務用 Skype Online 的條件式存取原則，這樣一來，只有受管理和相容的 iOS 和 Android 裝置可以存取它。 嘗試在 iOS 和 Android 上登入商務用 Skype 行動應用程式的使用者將會收到提示，在登入完成之前向 Intune 註冊並修正任何不相容問題。 如需詳細資訊，請參閱[管理商務用 Skype Online 的存取權](https://technet.microsoft.com/en-us/library/mt695297.aspx)。

### 裝置管理
- **iOS 9.3 的 Intune 支援。** 3 月 21 日星期一，Apple 宣佈推出 iOS 9.3。 我們努力確保 Microsoft Intune 與最新版 Apple 行動作業系統相容，[我們很高興宣佈 Intune 支援管理 iOS 9.3 裝置](https://blogs.technet.microsoft.com/microsoftintune/2016/03/23/microsoft-intune-provides-support-for-ios-9-3/)。

  當使用者將裝置升級到 iOS 9.3 時，所有目前可用來管理 iOS 裝置的 Intune 功能將繼續順利運作。 此外，iOS 9.3 目前也支援供混合式客戶使用 (Configuration Manager 與 Intune 整合)。

- **Windows 10 一般組態原則現在有設定可在已註冊的 Windows 10 電腦上的管理 Windows Defender。** 如需詳細資訊，請參閱 [Microsoft Intune 的 Windows 10 組態原則設定](https://technet.microsoft.com/en-us/library/mt404697.aspx)。


### 公司入口網站

- **直接從公司入口網站可取得的 Windows 應用程式套件。** Windows 8、Windows 8.1 和 Windows RT 電腦的使用者現在可以直接從公司入口網站安裝 Windows 應用程式套件 (副檔名為 .appx)。 先前，您必須部署，或使用者必須在裝置上安裝公司入口網站應用程式，才能安裝應用程式。

- **使用者可以從公司入口網站遠端鎖定裝置。** 公司入口網站新增新的 [遠端鎖定] 選項，可讓使用者在裝置遺失或遭竊時，從入口網站遠端鎖定其裝置。 請參閱[使用者指示](https://technet.microsoft.com/library/mt590895.aspx/?wt.mc_id=ui#BKMK_iwp_remote_lock) 下表列出 Intune Standalone 和 Intune 搭配 Configuration Manager 的遠端鎖定的平台支援。

|平台 | 支援詳細資料|
|---------|----------------|
|Android |支援|
|iOS |支援|
|Windows 10 Mobile |只有在電話已設定密碼時才支援|
|Windows 10 Desktop |不支援|
|Windows Phone 8.1 |只有在電話已設定密碼時才支援|
|Windows Phone 8。0 |不支援|
|電腦 (Windows 8.0 及更早版本) |不支援|
|電腦 (Windows 8.1) |不支援|

### 2016 年 3 月 10 日的新功能

### 應用程式管理

- **利用 iOS「開啟位置」管理在協力廠商 MDM 解決方案中註冊的裝置**：您可以使用協力廠商行動裝置管理 (MDM) 廠商來利用 iOS「開啟位置」管理。 您可以在組態設定檔的設定中設定限制，並使用[管理 iOS 應用程式之間的資料傳輸](manage-data-transfer-between-ios-apps-with-microsoft-intune.md)來部署應用程式。

     這個方法有兩大優點︰

     1. 使用者需要以工作帳戶登入，才能從雲端服務或其他應用程式存取任何公司資料。 這可確保行動應用程式管理 (MAM) 原則在存取資料時生效。

     2. 透過協力廠商 MDM 解決方案部署之受管理的電子郵件設定檔和其他受管理的應用程式，可以與具有 Intune MAM 原則的應用程式共用檔案和資料。

- **使用非 Intune 註冊裝置的 MAM 原則來管理 Microsoft Outlook 應用程式**：您現在可以使用 Intune 行動應用程式管理原則，在非 Intune 註冊的裝置上管理 Microsoft Outlook 應用程式。 [iOS](https://itunes.apple.com/us/app/microsoft-outlook-email-calendar/id951937596?mt=8) 和 [Android](https://play.google.com/store/apps/details?id=com.microsoft.office.outlook) 裝置都有使用 MAM 功能更新的 Microsoft Outlook 應用程式。 使用[建立及部署行動應用程式管理原則](https://technet.microsoft.com/library/mt627829.aspx)主題中的指示建立 MAM 原則。  


- **行動應用程式設定原則讓您能靈活地指定 iOS 應用程式的使用者詳細資料**：您可以在 iOS 應用程式開啟時，提供它可能需要的使用者設定。 例如，您可以提供網路連接埠或使用者名稱。 如需詳細資訊，請參閱[在 Microsoft Intune 中使用行動應用程式設定原則設定 iOS 應用程式](configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune.md)。


- **將 Adobe Reader for Microsoft Intune 部署到企業中受 Intune 管理的 iOS 裝置**：使用 Intune 行動應用程式管理原則註冊的裝置現在可以管理 IOS 適用的 Adobe Reader 應用程式。

- **請務必在受管理的瀏覽器中開啟部署的網路美工圖案**：您可以部署只能使用 iOS 和 Android 裝置上受管理瀏覽器開啟的目標網路美工圖案。 例如，您透過公司入口網站部署公司資源連結，當使用者瀏覽這些連結時，他們會直接開啟受 MAM 原則保護的受管理瀏覽器。 如需詳細資訊，請參閱[部署應用程式](deploy-apps.md)。


- **從 Intune 系統管理員主控台尋找、管理及發佈 Windows 10 裝置適用的商務用 Windows 市集應用程式**：Intune 支援商務用 Windows 市集，幫助您尋找、管理及發佈應用程式到您管理的 Windows 10 裝置。 商務用 Windows 市集可讓您從 Intune 系統管理員主控台管理部署和監視這些應用程式的程序，這是您管理其他應用程式的同一個主控台。 具體來說，商務用 Windows 市集用來管理「線上授權應用程式」的內容和授權。 如需詳細資訊，請參閱[管理購自商務用 Windows 市集的應用程式](manage-apps-you-purchased-from-the-windows-store-for-business-with-microsoft-intune.md)。


### 裝置管理
- **iOS 裝置發佈 PFX 憑證**：Intune 系統管理員可以在 iOS 裝置上建立及部署 Wi-Fi、電子郵件和 VPN 驗證的 iOS PFX 憑證。 Android 和 Windows 10 裝置已提供這項功能。 如需詳細資訊，請參閱[利用憑證設定檔存取公司資源](secure-resource-access-with-certificate-profiles.md)。


- **根據使用者類別選項，將應用程式和原則套用至不同的裝置群組**：Intune 系統管理員現在可以定義自訂裝置的類別，供使用者在註冊期間選取。 例如，系統管理員可能希望使用者指定註冊的裝置是用於「收銀機」或「送貨卡車」或「庫房」。 選取的類別會讓裝置成為 Intune 裝置群組的成員，用於將不同的應用程式和原則部署至已註冊的裝置。 如需詳細資訊，請參閱[使用裝置群組對應分類裝置](categorize-devices-with-device-group-mapping-in-microsoft-intune.md)。

### Microsoft 公司入口網站的變更及更新
本版本中公司入口網站的變更如下：

**Android 公司入口網站應用程式**

* 當使用者啟動受行動應用程式管理 (MAM) 管理的應用程式時，就會看到應用程式受公司管理的通知訊息。 使用者現在可以點選 [深入了解] 連結取得何謂「受管理應用程式」的[詳細資訊](https://technet.microsoft.com/library/mt502762.aspx#BKMK_andr_use_mgd_apps)。 他們也可以點選 [不要再顯示這個訊息]，在啟動應用程式時不再顯示這個訊息。
* 已加入新畫面來引導使用者進行註冊程序，並提供使用者應該註冊的原因，以及 IT 系統管理員在其註冊裝置上可見與不可得見內容的詳細資訊。 如需詳細資訊，請參閱[註冊指示](https://technet.microsoft.com/library/mt502762.aspx#BKMK_andr_enroll_devc)。
* 註冊錯誤訊息現在會顯示在公司入口網站應用程式中。 過去，這些訊息是出現在公司入口網站中。 這項變更的意義是所有錯誤訊息現在都只出現在一個位置，而不是兩個不同的地方。


**iOS 公司入口網站應用程式**
* 當使用者啟動受行動應用程式管理 (MAM) 管理的應用程式時，就會看到應用程式受公司管理的通知訊息。 使用者現在可以點選 [深入了解] 連結取得何謂「受管理應用程式」的[詳細資訊](https://technet.microsoft.com/library/mt598622.aspx#BKMK_ios_use_mgd_apps)。 他們也可以點選 [不要再顯示這個訊息]，在啟動應用程式時不再顯示這個訊息。
* 已加入新畫面來引導使用者進行註冊程序，並提供使用者應該註冊的原因，以及 IT 系統管理員在其註冊裝置上可見與不可得見內容的詳細資訊。 如需詳細資訊，請參閱[註冊指示](https://technet.microsoft.com/library/mt598622.aspx#BKMK_enroll_ios_device)。
* 註冊錯誤訊息現在會顯示在公司入口網站應用程式中。 過去，這些訊息是出現在公司入口網站中。 這項變更的意義是所有錯誤訊息現在都只出現在一個位置，而不是兩個不同的地方。




## 2016 年 2 月
### Microsoft 公司入口網站的變更及更新

本版本中公司入口網站的變更如下：

#### Android 公司入口網站應用程式
- 已加入新畫面來引導使用者進行註冊程序，並提供使用者應該註冊的原因，以及 IT 系統管理員在其註冊裝置上可見與不可得見內容的詳細資訊。 如需詳細資訊，請參閱[註冊指示](https://technet.microsoft.com/library/mt502762.aspx#BKMK_andr_enroll_devc)。
- 註冊錯誤訊息現在會顯示在公司入口網站應用程式中。 過去，這些訊息是出現在公司入口網站中。 這項變更的意義是所有錯誤訊息現在都只出現在一個位置，而不是兩個不同的地方。

#### iOS 公司入口網站應用程式
 - 已加入新畫面來引導使用者進行註冊程序，並提供使用者應該註冊的原因，以及 IT 系統管理員在其註冊裝置上可見與不可得見內容的詳細資訊。 如需詳細資訊，請參閱[註冊指示](https://technet.microsoft.com/library/mt598622.aspx#BKMK_enroll_ios_device)。

 - 註冊錯誤訊息現在會顯示在公司入口網站應用程式中。 過去，這些訊息是出現在公司入口網站中。 這項變更的意義是所有錯誤訊息現在都只出現在一個位置，而不是兩個不同的地方。


## 2016 年 1 月

### 利用 Windows 10 功能
* **使用健康情況證明服務的條件式存取**：Intune 系統管理員現在可以在 Intune 管理主控台中檢視 Windows 10 裝置的健康情況證明。 系統管理員可透過裝置健全狀況證明，確認該用戶端電腦具有可信任的 BIOS、TPM 以及開機軟體設定。 若要支援裝置的健全狀況證明，用戶端裝置必須執行啟用了 TPM 2 的 Windows 10。 裝置健全狀況證明會顯示為下列各項啟用的裝置數目：
    * 早期啟動反惡意程式碼
    * BitLocker
    * 安全開機
    * 程式碼完整性

    如需裝置健全狀況設定、收集資料點及狀況證明報告的詳細資訊，請參閱 [Microsoft Intune 的裝置相容性原則簡介](introduction-to-device-compliance-policies-in-microsoft-intune.md)。 [HAS 服務詳細資料](https://msdn.microsoft.com/en-us/library/dn934876.aspx)詳細說明此項服務。

* **Windows 10 Passport for Work Policy 及憑證管理**：使用 Intune 可[與 Microsoft Passport for Work 整合](control-microsoft-passport-settings-on-devices-with-microsoft-intune.md)，這是使用 Active Directory 或 Azure Active Directory 帳戶取代密碼、智慧卡或虛擬智慧卡來登入 Windows 10 的替代方法。 Passport 可讓您以使用者筆勢登入，而不使用密碼登入。 使用者筆勢可能是簡單的 PIN、生物識別驗證 (例如 Windows Hello) 或外部裝置 (例如指紋辨識器)。

* **適用於特定應用程式的 VPN**：您可以選取透過 VPN 自動連接公司網路的應用程式。 設定 VPN 設定檔時，請依＜協助使用者搭配使用 VPN 設定檔與 Microsoft Intune 來連線到工作＞中所述，建立應用程式清單。

* **Windows 10 完整抹除支援**：您現在可以透過 Intune 管理主控台，遠端發出在 Intune 中註冊之 Windows 10 Desktop 裝置的完整抹除。 Windows 10 完整抹除會將裝置重設成出廠預設值。


### Apple 大量採購方案 (VPP) 更新
Intune 現在可以幫助您[管理透過 Apple 商務大量採購方案 (VPP) 購買的應用程式](manage-ios-apps-you-purchased-through-a-volume-purchase-program-with-microsoft-intune.md)。 這包括同步處理 Apple 與 Intune 之間的授權資訊，以及追蹤每個應用程式部署的複本數量。

### 使用 IMEI 編號識別公司擁有的裝置
您現在可以為具有 IMEI 編號的行動裝置平台[匯入國際行動設備識別碼 (IMEI) 編碼](specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers.md)，協助找出公司擁有的行動裝置。 只要在 Intune 註冊，已匯入 IMEI 編號的裝置就會標記為「公司」，以供套用不同於私有裝置套用原則的原則。

### 現在有更多的應用程式與 Intune MAM 原則相容
其他非 Microsoft 合作夥伴的應用程式現在已與 Intune 行動應用程式管理 (MAM) 原則相容 (受 Intune 管理的裝置)︰
* Box for EMM (Box Inc 出品) – 限 iOS
* Adobe Reader (Adobe 出品) – 限 Android
* Foxit PDF 閱讀程式 (Foxit Corporation 出品) – iOS 和 Android


### 一月終止 IE9 支援
從 2016 年 2 月開始，Internet Explorer 9 不再是用於存取 Microsoft Intune 公司入口網站、Intune 帳戶入口網站和 Intune 管理主控台的官方瀏覽器。 您必須移轉至 Internet Explorer 10 或更新版本。

## 2015 年 12 月
### Microsoft 公司入口網站的變更及更新
本版本中公司入口網站的變更如下：

**Android 公司入口網站應用程式**

已進行下列變更以符合 Gooogle 的新需求。 Android 6.0 和更新版本的裝置會向使用者顯示兩則新訊息︰
* 是否允許公司入口網站進行和管理通話？
* 是否允許公司入口網站存取相片、媒體和裝置上的檔案？

請參閱下表以取得這兩則訊息的詳細資料。



訊息文字  |是否允許公司入口網站進行和管理通話？  
---------|---------
訊息意義     |  讓使用者的裝置電話號碼和 IMEI 傳送到 Intune 服務中，並在 [硬體] 頁面上的系統管理主控台中顯示。   </br></br>**注意：一律不要讓公司入口網站應用程式進行或管理通話！** 由 Google 控制此訊息文字，且無法變更。 </br></br>若要查看 [硬體] 頁面，請移至 [群組] > [所有行動裝置] > [裝置]。 選取使用者的裝置，然後移至 **[檢視內容]** > **[硬體]**。    
訊息出現的位置和時機  | 當使用者第一次登入公司入口網站應用程式並開始註冊其裝置時，會出現此訊息。|         
如果使用者允許存取會怎樣  |  裝置的電話號碼和 IMEI 會出現在系統管理員主控台的硬體上。 |         
如果使用者拒絕存取會怎樣     | 他們可以繼續使用公司入口網站應用程式並註冊其裝置，但在系統管理主控台中的 [硬體] 頁面上，使用者的裝置電話號碼和 IMEI為空白。       </br></br> 使用者拒絕存取後並再次登入公司入口網站應用程式時，訊息會顯示 **不要再詢問** 核取方塊，使用者可選取該核取方塊讓訊息不再顯示。</br></br>若使用者在允許之後又拒絕存取，則訊息會在使用者註冊後下一次登入公司入口網站應用程式時出現。</br></br>如果使用者稍後決定允許存取，他們可以移至 [設定] > [應用程式] > [公司入口網站] > [權限] > [電話]，然後開啟權限。
詳細資訊     |  針對您的使用者：[登入公司入口網站](https://technet.microsoft.com/library/mt502762.aspx#BKMK_andr_signin_cp)  </br></br>針對 IT 專業人員：本表中的資訊亦見於[幫助使用者了解公司入口網站應用程式的訊息](https://technet.microsoft.com/library/dn948527.aspx#BKMK_help_users_understd_msgs)   

訊息文字  |是否允許公司入口網站存取相片、媒體和裝置上的檔案？  
---------|---------
訊息意義     |  讓裝置將資料記錄檔寫入裝置的 SD 記憶卡中，以使用 USB 纜線來移動資料的記錄檔。   </br></br>**注意：一律不要讓公司入口網站應用程式存取使用者的相片、媒體和檔案！** 由 Google 控制此訊息文字，且無法變更。     
訊息出現的位置和時機  | 當使用者點選 **傳送資料** 將資料記錄檔傳送至其 IT 系統管理員時，會出現此訊息。|         
如果使用者允許存取會怎樣  |  記錄檔會複製到 SD 卡中。 |         
如果使用者拒絕存取會怎樣     | 他們仍然可以傳送資料記錄檔，但記錄檔將不會複製到裝置的 SD 記憶卡中。       </br></br> 使用者拒絕存取後並再次登入公司入口網站應用程式時，訊息會顯示 **不要再詢問** 核取方塊，使用者可選取該核取方塊讓訊息不再顯示。</br></br>若使用者在允許之後又拒絕存取，則訊息會在使用者下一次嘗試傳送記錄檔時出現。</br></br>如果使用者稍後決定允許存取，他們可以移至 [設定] > [應用程式] > [公司入口網站] > [權限] > [儲存體]，然後開啟權限。
詳細資訊     |  針對您的使用者：[使用電子郵件將診斷資料記錄傳送給 IT 管理員](https://technet.microsoft.com/library/mt502762.aspx#BKMK_andr_send_diag_logs)  </br></br>針對 IT 專業人員：本表中的資訊亦見於[幫助使用者了解公司入口網站應用程式的訊息](https://technet.microsoft.com/library/dn948527.aspx#BKMK_help_users_understd_msgs)   


**iOS 公司入口網站應用程式**
* 使用者現在可以使用 Microsoft Outlook 或其他電子郵件應用程式，將診斷記錄檔傳送給 IT 系統管理員。 先前只能使用原生應用程式。
* 已針對 Apple 的裝置註冊方案 (DEP) 和公司註冊的裝置進行支援改善。 如需詳細資訊，請參閱[系統在您嘗試註冊時，要求您識別您的裝置](https://technet.microsoft.com/library/mt598622.aspx#BKMK_ios_id_your_device)。
* 在使用者的已註冊裝置清單中，使用者目前正在使用的裝置旁現在會顯示綠色的核取符號。 在加入此核取符號之前，使用者無法得知正在使用哪一個已註冊的裝置。

**Windows 公司入口網站應用程式**

Microsoft 會自動收集有關公司入口網站效能和使用的匿名資料，以改善 Microsoft 產品和服務。 使用者可以使用裝置上的使用量資料設定來關閉資料收集，但系統管理員無法控制資料收集，也無法變更此設定中使用者的選取項目。



## 2015 年 11 月
### 應用程式管理
Intune 支援行動應用程式管理 (MAM) 原則，可防止公司資料外洩予消費者應用程式或服務。 在過去，這些原則只會在也註冊了 Intune 行動裝置管理 (MDM) 之裝置上執行的行動應用程式上強制執行。

在本月的更新中，Intune 的 MAM 功能擴及新類別的裝置。 除了向 Intune 註冊的裝置，MAM 原則現在也可以強制施行於︰
* 受任何其他裝置管理 (MDM) 解決方案管理的裝置
* 未向任何裝置管理系統註冊的裝置，通常是自備 (BYO) 裝置

如需這些新 MAM 功能的詳細資訊，請參閱以下的部落格文章︰
* [增強受管理的行動產能](http://blogs.technet.com/b/microsoftintune/archive/2015/11/17/enhancing-managed-mobile-productivity.aspx)
* [宣告新的 Microsoft Enterprise Mobility 功能](http://blogs.technet.com/b/microsoftintune/archive/2015/11/17/enhancing-managed-mobile-productivity.aspx)

此外，以下是 Intune MAM 功能的一些重點和其他資訊︰
* 在啟用 Intune 的應用程式中，公司資料和消費者資料是分開的，它們包括 Office 行動應用程式、採用 Intune SDK 的協力廠商應用程式，或 Intune 包裝的企業營運應用程式。
* 公司資料可以跨公司應用程式共用 (**剪下/複製/貼上**)，同時防止個人應用程式共用公司資料。 如需詳細資訊，請參閱 [MAM 原則如何保護應用程式資料](https://technet.microsoft.com/library/mt627825.aspx)。 [使用 Microsoft Word 應用程式執行公司和個人工作](https://technet.microsoft.com/library/mt627827.aspx)這個範例案例，會示範如何防止個人應用程式共用公司資料。
* 關鍵資料外洩防護原則如同每個應用程式的 PIN、另存新檔控制項，以及應用程式之間共用的受管理資料。 如需所有原則的清單，請參閱[使用 Microsoft Intune 建立及部署行動應用程式管理原則](https://technet.microsoft.com/library/mt627829.aspx)。
* Word、Excel、PowerPoint、Outlook、OneNote 和商務用 OneDrive 都擁有這些新功能，可使用/不使用裝置註冊管理。 Apple 市集或 Google Play 商店的標準 Office 應用程式原就內建有資料外洩防護功能，不需要應用程式包裝或側載。
* 若想要開始使用，請參閱[在 Azure 入口網站中開始使用行動裝置應用程式管理原則](https://technet.microsoft.com/library/mt627830.aspx)。 若要了解如何設定及部署行動應用程式管理原則，請參閱[使用 Microsoft Intune 建立及部署行動應用程式管理原則](https://technet.microsoft.com/library/mt627829.aspx)。
* 當使用者使用公司認證來驗證應用程式時，就會自動設定資料外洩防護功能。 [與 Microsoft Intune 行動應用程式管理原則相關聯之應用程式的使用者體驗](https://technet.microsoft.com/library/mt627827.aspx)主題提供在 iOS 和 Android 裝置上存取 OneDrive 的範例案例。
* 適用於 iOS 和 Android 裝置。

[可與 Microsoft Intune 行動應用程式管理原則搭配使用的 Microsoft 應用程式](https://technet.microsoft.com/library/dn708489.aspx)的清單已更新，會顯示最新的應用程式。

### 裝置管理
 **Mac OS X 裝置管理**：您現在可以使用 Intune 註冊及管理 Mac OS X 裝置。 您可以使用 Mac OS X 裝置執行下列作業︰
* 註冊由 Intune 管理的裝置。 請參閱[使用 Microsoft Intune 設定 iOS 和 Mac 管理](https://technet.microsoft.com/library/dn408185.aspx)。
* 具有一般組態原則的控制裝置設定。 請參閱[Microsoft Intune 的 Mac OS X 設定原則設定](https://technet.microsoft.com/library/mt627823.aspx)。
* 部署使用 Apple Configurator 建立的 Mac OS X 設定。 請參閱[Microsoft Intune 的 Mac OS X 自訂原則設定](https://technet.microsoft.com/library/mt627820.aspx)。
* 收集 Mac OS X 裝置的硬體和軟體清查。 請參閱[透過 Microsoft Intune 的清查了解您的裝置](https://technet.microsoft.com/library/jj733634.aspx)。
* 執行顯示您管理之 Mac OS X 裝置詳細資料的新報表。 請參閱[透過報表來了解 Microsoft Intune 作業](https://technet.microsoft.com/library/dn646977.aspx)。

**適用於 Windows 10 裝置的新 Edge 瀏覽器設定**：新設定已加入 Windows 10 一般設定原則中，可讓您管理 Microsoft Edge 瀏覽器的設定和功能。 請參閱 [Microsoft Intune 的 Windows 10 組態原則設定](https://technet.microsoft.com/library/mt404697.aspx)。

**電子郵件設定檔**：Windows 10 Desktop 和 Windows 10 行動裝置中已加入新的電子郵件設定檔原則。 請參閱[透過 Microsoft Intune 原則管理裝置上的設定和功能](https://technet.microsoft.com/library/dn646984.aspx)。

**新的相容性原則設定**：相容性原則清單中已加入下列的新安全性和系統原則設定︰
* 若要確定存取公司資源的 Windows 8.1 或更新裝置已安裝最新的更新，請使用 **需要自動更新** 設定。 您也可以指定要自動安裝的更新類型：安裝標示為重要的所有更新，或是安裝標示為重要或建議的所有更新。 如需相容性原則設定的完整清單，請參閱[管理 Microsoft Intune 的裝置相容性原則](https://technet.microsoft.com/library/dn705843.aspx)。
* 新的 **裝置從閒置狀態恢復時必須輸入密碼** 設定結合現有的 **在非使用狀態幾分鐘後需要輸入密碼** 設定，可讓您建立需要使用者輸入密碼才能使用閒置一段時間之裝置的相容性設定。

**新的條件式存取原則選項**：您可以將條件式存取原則套用到新的或現有的條件式存取原則的**所有使用者**。 有 Intune 和 Office 365 授權的所有使用者都需要註冊其裝置，如果 Intune 不支援裝置平台，就會封鎖使用 [Active Directory 驗證型登入 (新式驗證)](https://blogs.office.com/2014/11/12/office-2013-updated-authentication-enabling-multi-factor-authentication-saml-identity-providers/) 之用戶端應用程式的存取。

您也可以指定將條件式存取原則套用至 **所有平台**。  任何使用 [Active Directory 驗證型登入 (新式驗證)](https://blogs.office.com/2014/11/12/office-2013-updated-authentication-enabling-multi-factor-authentication-saml-identity-providers/) 的用戶端應用程式都必須遵守條件式存取原則，如果 Intune 不支援該平台，應用程式就會被封鎖。

### Microsoft 公司入口網站的變更及更新
本版公司入口網站應用程式的變更如下：

* **Android**：Android 公司入口網站應用程式中加入了歡迎畫面，幫助使用者了解公司入口網站應用程式的用途。 這個畫面是為了減少公司不是 Intune 訂閱者的使用者下載應用程式的次數。

* **iOS**：Intune 現在支援使用[公司入口網站](https://portal.manage.microsoft.com)來註冊 Mac OS X 裝置。 如需指示，請參閱[在 Intune 中註冊您的 Mac OS X 裝置](https://technet.microsoft.com/library/mt598622.aspx)。

* **公司入口網站**：若使用者已在 Intune 中註冊裝置，則可立即使用公司入口網站上的 **重設密碼** 選項來重設密碼。 先前只有 IT 系統管理員可以重設使用者的密碼。 [重設密碼] 選項不受 Windows 8.1 和 Windows RT 裝置支援，且此選項僅會在裝置註冊於行動裝置管理 (MDM) 中或使用 Exchange ActiveSync 的 MDM 中時出現。 如需使用者指示，請參閱[重設密碼](https://technet.microsoft.com/library/mt590895.aspx)。

### 變更為全域管理員授權
10 月的時候，我們告訴大家，全域系統管理員 (也稱為租用戶系統管理員) 不需要分別擁有 Intune 或 Enterprise Mobility Suite (EMS) 授權，也可以繼續執行日常的管理工作。 但是，如果全域系統管理員想要使用服務，例如註冊自己的裝置、公司裝置或使用 Intune 公司入口網站，他們就需要有 Intune 或 EMS 授權，像任何其他使用者一樣。 以下為其他詳細資料。
* Intune 公司入口網站是使用者執行下列作業的地方：
    * 註冊裝置
    * 檢視裝置的狀態
    * 下載全域管理員部署到組織的軟體
    * 尋找全域系統管理員發佈的連結，供其連絡 IT 部門

    [深入了解公司入口網站](https://technet.microsoft.com/library/dn646966.aspx#BKMK_CompanyPortal)和[自訂公司入口網站的方法](https://technet.microsoft.com/library/dn646983.aspx#BKMK_ConfigureCompanyPortal)。
* 代表組織註冊購買 Intune 或 EMS 的人員會自動成為其租用戶中第一位全域系統管理員。 自今年秋天開始，Intune 自動指派 Intune 或 EMS 授權給這名第一位全域系統管理員，當成移至 [Office 365 入口網站](http://portal.office.com/)和淘汰 [Intune 帳戶入口網站](http://account.manage.microsoft.com/)的一部分。 任何後來加入的全域管理員不需要分別擁有 Intune 或 EMS 授權，也可以繼續執行日常管理工作。 當他們以一般使用者身分，註冊自己 (或公司) 的裝置或從公司入口網站下載軟體時，就會需要授權，和任何其他使用者一樣。
* 變更從 2016 年 1 月開始。
* 對 Microsoft 的合作夥伴而言，這項變更應該不會影響您代表客戶管理服務的能力。 至於使用者工作，使用者必須要有 Intune 或 EMS 授權才能註冊裝置，以及從公司入口網站存取或下載軟體。

如需有關於這項變更的任何問題，歡迎連絡您的 Intune 支援小組︰
* [Microsoft Intune 支援通道](https://technet.microsoft.com/library/jj839713.aspx)
* [社群支援](https://social.technet.microsoft.com/Forums/en-US/home?forum=microsoftintuneprod)

如需一般 Microsoft Intune 的意見反應，包括提出設計變更要求 (DCR) 或 Bug，請造訪 [Intune 使用者意見](https://microsoftintune.uservoice.com/)。


### Intune 文件的新內容 -- 2015 年 11 月
**新內容**
* [Microsoft Intune 的 Mac OS X 設定原則設定](https://technet.microsoft.com/library/mt627823.aspx)︰如何控制 Mac OS X 裝置的裝置設定和功能。
* [Microsoft Intune 的 Mac OS X 自訂原則設定](https://technet.microsoft.com/library/mt627820.aspx)︰如何部署使用 Apple Configurator 工具建立的 Mac OS X 裝置設定。
* [使用 Microsoft Intune 設定資料外洩防護應用程式原則](https://technet.microsoft.com/library/mt627825.aspx)︰包含行動應用程式管理原則支援案例和資料保護原則運作方式的資訊。
* [在 Azure 入口網站中開始使用行動應用程式管理原則](https://technet.microsoft.com/library/mt627830.aspx)︰開始使用 Azure Preview 入口網站執行行動應用程式管理原則所需要的內容。
* [使用 Microsoft Intune 建立及部署行動應用程式管理原則](https://technet.microsoft.com/library/mt627829.aspx)︰包含如何在 Azure Preview 入口網站中建立行動應用程式管理原則的逐步解說。
* [使用 Microsoft Intune 監視行動應用程式管理原則](https://technet.microsoft.com/library/mt627824.aspx)︰如何使用 Azure Preview 入口網站監視行動應用程式管理原則的資訊。
* [Microsoft Intune 行動應用程式管理原則和 iOS 的開啟位置](https://technet.microsoft.com/library/mt627821.aspx)︰行動應用程式管理原則如何搭配 iOS 開啟位置功能的資訊。
* [與 Microsoft Intune 行動應用程式管理原則相關聯之應用程式的使用者體驗](https://technet.microsoft.com/library/mt627827.aspx)：使用與行動應用程式管理原則相關聯之應用程式時的使用者體驗。
* [使用 Microsoft Intune 抹除受管理的公司應用程式資料](https://technet.microsoft.com/library/mt627826.aspx)：如何移除公司應用程式資料。

**更新的內容**
* [Microsoft Intune 的 Windows 10 組態原則設定](https://technet.microsoft.com/library/mt404697.aspx)：加入了新的 Edge 瀏覽器設定。
* [使用 Microsoft Intune 設定 iOS 和 Mac 管理](http://technet.microsoft.com/library/dn408185.aspx)︰加入了如何註冊 Mac OS X 裝置的資訊。
* [透過 Microsoft Intune 的清查了解您的裝置](https://technet.microsoft.com/library/jj733634.aspx)：加入了收集自 Mac OS X 裝置的清查資訊。 此外，也使用所有裝置平台的最新資訊更新了本主題。
* [透過報表來了解 Microsoft Intune 作業](https://technet.microsoft.com/library/dn646977.aspx)︰加入了兩份新報表的資訊，用以顯示受管理的 Mac OS X 裝置的資訊。
* [管理 Microsoft Intune 的裝置相容性原則](https://technet.microsoft.com/library/dn705843.aspx)：加入了新相容性原則的資訊，這些原則可在裝置從閒置狀態恢復時，要求自動更新和密碼需求。
* [使用 Microsoft Intune 管理電子郵件存取](https://technet.microsoft.com/library/dn705841.aspx)：加入了將條件式存取原則套用至所有平台和所有使用者的資訊。
* [以 Microsoft Intune 管理 SharePoint Online 存取](https://technet.microsoft.com/library/dn705844.aspx)：加入了將條件式存取原則套用至所有平台和所有使用者的資訊。

## 2015 年 10 月

### Exchange 內部部署的條件式存取更新
**您現在可以在通用 Exchange 規則設定為封鎖或隔離時，允許在 Intune 中註冊的相容裝置存取 Exchange Active Sync 電子郵件。** 到目前為止，若要允許在已註冊及相容的裝置存取電子郵件，預設的通用 Exchange 規則必須設定為 **允許**。

有了這項服務更新，您不再需要這項設定來進行條件式存取。 如果您的 Exchange 環境要求您將預設通用規則設定為 **封鎖/隔離**，請直接核取 Exchange 內部部署條件式存取原則頁面中的 **預設規則覆寫** 核取方塊。 [使用 Microsoft Intune 管理電子郵件存取](https://technet.microsoft.com/library/dn705841.aspx)主題包含規則及所產生之使用者通知的詳細資訊。

**全新的單鍵隔離體驗**：我們已簡化隔離電子郵件體驗，只要按一下就能註冊。 有了這項服務更新，終端使用者只要按一下隔離電子郵件中的單一連結，就可在公司入口網站應用程式內完成註冊程序。
### 行動裝置與應用程式管理更新
**Android** 所有 Intune 管理功能現在都支援 Android 6.0 (Marshmallow)，如這篇部落格文章所述：[Microsoft Intune Provides Day 0 Support for Android Marshmallow (Microsoft Intune 提供 Android Marshmallow 的 0 天支援)](http://blogs.technet.com/b/microsoftintune/archive/2015/10/09/microsoft-intune-to-provide-day-0-support-for-android-marshmallow.aspx)。

**iOS** 您無法再對執行 iOS 7.1 之前版本的 iOS 裝置，建立新的應用程式部署。 執行 iOS 7.1 之前版本之裝置上的任何現有應用程式部署將會繼續運作，並由 Intune 管理。

**Windows 10** Intune 現在可部署使用 **Windows 應用程式封裝** 軟體安裝程式類型的 Windows 10 通用應用程式。 如需詳細資訊和需求，請參閱[開始使用 Microsoft Intune 部署應用程式](http://technet.microsoft.com/en-US/library/dn646955.aspx)。


### 變更並新新 Microsoft 公司入口網站應用程式
本版之公司入口網站應用程式的變更如下：公司入口網站應用程式已加入 **iOS** 新增按鈕，讓使用者能夠更輕鬆地將診斷記錄檔傳送給 IT 系統管理員：

|按鈕名稱|出現的位置|
|------------|---------------|
|報表|錯誤警示訊息|
|傳送診斷報表|關於公司入口網站應用程式的畫面|


>[!div class="step-by-step"]

>[&larr; **[!div class="step-by-step"]**](whats-new-in-microsoft-intune.md)    



<!--HONumber=Jul16_HO1-->



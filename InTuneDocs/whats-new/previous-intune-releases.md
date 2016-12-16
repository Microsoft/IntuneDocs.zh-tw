---
title: "舊版 | Microsoft Intune"
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 12/05/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 45dad14a-d412-488d-bb1e-ad990ea503df
ROBOTS: noindex,nofollow
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b4dab832da4490c3df045d2c627b231028c92b25
ms.openlocfilehash: 3de5e57589a24600301e54a3b60eecb5321ff838


---

# <a name="previous-intune-releases"></a>舊版 Intune

此頁面是 [Microsoft Intune 的新功能](whats-new-in-microsoft-intune.md)中公告的清單。

[!INCLUDE[wit_nextref](../includes/whats-new-last-six-months.md)]

## <a name="may-2016"></a>2016 年 5 月
混合式部署也支援所有這些功能 (Configuration Manager 與 Intune)。 如需新混合式功能的詳細資訊，請查看 [Hybrid What’s New](https://technet.microsoft.com/en-us/library/mt718155.aspx) (混合式新功能) 頁面。

### <a name="documentation"></a>文件
歡迎使用 [docs.microsoft.com](https://docs.microsoft.com/en-us/intune) 的預覽版本！
這是全新的現代內容平台，其設計是為了讓您，也就是我們的客戶，更輕鬆地了解和使用 Intune。
若要閱讀所有新功能，請參閱 [Introducing docs.microsoft.com](https://docs.microsoft.com/teamblog/introducing-docs-microsoft-com/) (docs.microsoft.com 簡介)

### <a name="intune-service-health"></a>Intune 服務健全狀況
Intune 的服務健全狀況資訊已與其他 Microsoft 服務一起移至中央位置。 現在，您會在 [Office 365 管理入口網站](https://portal.office.com/Admin/Default.aspx) 的 [服務健全狀況] 下發現這項資訊。
如需詳細資訊，請參閱[這篇部落格文章](https://blogs.technet.microsoft.com/microsoftintune/2016/04/28/intune-service-health-is-now-available-in-the-office-365-portal/)。

### <a name="app-management"></a>應用程式管理
- **MAM SDK︰支援 PIN 長度設定。** 您可以將 MAM 應用程式的 PIN 長度指定為類似裝置 PIN 的長度。 這將需要使用者符合您設定的新限制。 他們會看到稍微修改的 PIN 畫面以說明較長的輸入。 如需詳細資訊，請參閱 [MAM policy settings for Android](/intune/deploy-use/android-mam-policy-settings) (適用於 Android 的 MAM 原則設定) 和 [MAM policy settings for iOS](/intune/deploy-use/ios-mam-policy-settings) (適用於 iOS 的 MAM 原則設定)。

- **iOS 和 Android 的商務用 Skype。** 您現在可以將目標放在具備[無註冊原則之 MAM](/intune/deploy-use/get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune) 的商務用 Skype。 一旦使用者登入，將會套用 MAM 原則。

- **新的應用程式可用來使用 MAM 原則進行管理。** 適用於 Android 的 Microsoft Word、Excel 和 PowerPoint 應用程式現在可以在未向 Intune 註冊的裝置上與 MAM 原則相關聯。 如需受支援應用程式的完整清單，請移至 Microsoft Intune 應用程式夥伴頁面上的 [Microsoft Intune 行動應用程式庫](https://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/partners.aspx)。


### <a name="company-portal-updates"></a>公司入口網站更新

#### <a name="android-company-portal-app"></a>Android 公司入口網站應用程式
- **使用者快顯通知**：使用者註冊其裝置或從公司入口網站移除他們的裝置時，將會看到來自 Android 公司入口網站應用程式的快顯通知。

- **Android 公司入口網站應用程式中的裝置註冊管理員帳戶的變更。** 為了改善效能和擴充，Intune 將不再於 Android 公司入口網站的 [我的裝置] 窗格中，顯示所有的裝置註冊管理員 (DEM) 裝置。 只有執行應用程式的本機裝置會顯示，只有在透過公司入口網站應用程式註冊時才會顯示。 DEM 使用者可在本機裝置上執行動作，但是其他已註冊裝置的遠端管理只能從 Intune 管理主控台執行。

#### <a name="company-portal-website"></a>公司入口網站
- **公司入口網站：裝置識別橫幅將提供詳細資訊給使用者。** 使用者可以更輕鬆地識別他們在使用公司入口網站時所選取的裝置。 如果選取了錯誤的裝置，他們可以藉由點選首頁橫幅中的 [點選這裡] 連結來選取正確的裝置。

### <a name="service-deprecation"></a>服務取代
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


## <a name="april-2016"></a>2016 年 4 月
混合式客戶也支援這些功能 (Configuration Manager 與 Intune 整合)。

### <a name="app-management"></a>應用程式管理
- **MAM 使用者相容性。**
您現在可以檢視 Azure Active Directory (AAD) 租用戶中任一使用者的應用程式管理原則[狀態](/intune/deploy-use/monitor-mobile-app-management-policies-with-Microsoft-Intune)。 這包括：
   - 裝置
   - 裝置上的應用程式

   狀態值：

   **已存回**︰表示原則已部署至使用者，且已使用工作內容中的應用程式，並成功接收原則。

    **未存回**︰表示原則已部署至使用者，但是應用程式從那時起並未在工作內容中使用。


- **避免 Outlook 連絡人同步處理的 MAM 控制項 (Android)。**
新的設定可供[行動應用程式管理](/intune/deploy-use/create-and-deploy-mobile-app-management-policies-with-microsoft-intune)使用，而不需要裝置註冊。 此設定可讓您防止應用程式在 Android 裝置上將連絡人同步處理至原生通訊錄。 啟用此設定時，目標應用程式將不再能夠儲存連絡人到原生通訊錄。 停用此設定時，目標應用程式將能夠儲存連絡人到原生通訊錄。 當您[從遠端抹除裝置或應用程式](/intune/deploy-use/wipe-managed-company-app-data-with-Microsoft-Intune)時，將會移除所有已儲存至原生通訊錄的連絡人。 在 Android 裝置上的 Outlook 應用程式一開始支援這個新的設定。

### <a name="device-management"></a>裝置管理
- **公司擁有裝置的電話號碼識別。** 分類為「公司」的電話現在會在 (舉例而言) 您執行行動裝置清查報表時利用其完整電話號碼加以識別。 BYOD 電話號碼會持續以 **** 遮罩，僅顯示最後 4 位數。


### <a name="company-portal-updates"></a>公司入口網站更新
**Android 公司入口網站應用程式**：尚未在 Intune 中註冊其裝置，且沒有安裝正確憑證的使用者將無法登入 Android 公司入口網站應用程式，而且會看到以下訊息 -「您無法登入，因為您的裝置缺少必要的憑證」。 此訊息包含使用者可以點選以參閱安裝憑證的指示之「如何解決此問題」連結。 若要查看使用者需遵循才能解決此問題的步驟，請參閱[您的裝置遺漏必要的憑證](https://technet.microsoft.com/library/mt502762.aspx#BKMK_andr_cert_missing)。

**iOS 公司入口網站應用程式**：支援已新增至下拉以更新動作來重新整理主畫面上的內容，其中包括列出的應用程式、列出的裝置，以及 IT 連絡人資訊。 下拉更新動作並未檢查相容性或原則資訊，而這可以透過選取目前裝置的磚並點選 [同步處理] 按鈕來完成。

**Windows 10 Mobile 和 Windows Phone 8.1 公司入口網站應用程式**：當使用者安裝企業營運應用程式時，就會看到改善的應用程式安裝體驗。 如果應用程式安裝花很長的時間，使用者可以手動同步處理他們的裝置，以強制同步處理程序繼續執行。 若要檢閱使用者指示，請參閱[以手動方式同步處理您的裝置，以加速應用程式安裝](https://technet.microsoft.com/library/mt427782.aspx#BKMK_win10m_wp81_sync_manually)。

**公司入口網站**：當 Windows 10 Mobile 和 Windows Phone 8.1 使用者安裝企業營運應用程式時，他們會看到下列新狀態，可提供其安裝狀態的詳細資訊︰

* **正在等待裝置同步處理** – 使用者已點選 [安裝]，而裝置會嘗試與 Intune 基礎結構同步處理。 安裝完成之前需要同步處理。 「正在等待裝置同步處理」的訊息也是一個連結，使用者可以點選以在同步處理程序花了較長的時間或已停止時，查看如何手動將他們的裝置與 Intune 同步處理的[指示](https://technet.microsoft.com/library/mt590895.aspx#BKMK_iwp_sync_manually)。
* **正在下載** – 正在處理使用者的下載要求，且裝置正在下載與安裝應用程式。

新增這些狀態之前，如果應用程式安裝花了較長的時間，會讓使用者混淆，因為他們只看到「正在安裝」狀態，可能會在螢幕上維持時小數。 新增狀態表示，使用者現在就可以點選 [正在等待裝置同步處理] 連結，並遵循指示以強制同步處理程序繼續執行，而不是呼叫支援。

>[!div class="step-by-step"]

>[&larr;**Intune 的新功能**](whats-new-in-microsoft-intune.md)    



<!--HONumber=Dec16_HO1-->



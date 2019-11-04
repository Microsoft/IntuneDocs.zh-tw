---
title: 包含檔案
description: 包含檔案
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: include
ms.date: 03/28/2019
ms.author: erikje
ms.custom: include file
ms.openlocfilehash: 0aa78ec17aba5deb0c914c3698676219f203b856
ms.sourcegitcommit: 60f0ff6d2efbae0f2ce14b9a9f3f9267309e209b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73415094"
---
這些注意事項提供可協助您針對未來的 Intune 變更與功能進行準備的重要資訊。

### <a name="plan-for-change-the-server-side-logging-for-siri-commands-setting-will-be-removed-from-the-intune-console----5468501--"></a>規劃變更：[Siri 命令的伺服器端記錄] 設定將會從 Intune 主控台移除 <!-- 5468501-->

我們計畫在 Intune 服務的 11 月更新，移除 Intune 主控台中的 [Siri 命令的伺服器端記錄] 設定。 此變更與 Apple 已移除其設定相符。

#### <a name="how-does-this-affect-me"></a>此變更對我造成什麼影響？
當 11 月更新或 1911 在 11 月中推出時，您會看到在 Intune 主控台中，已從 iOS 組態設定檔的 [裝置限制] 功能表 (內建應用程式) 中移除此設定。 它可能會出現在您的原則和目標裝置的管理設定檔中，但此設定不會影響您的裝置。 我們不預期對功能有太大的影響，因為它目前無法在裝置上執行，即使您在管理設定檔中看到此設定也一樣。

您可以選擇下列兩個路徑之一：
- 如果您想要從原則中刪除此設定，您可以移至具有此設定的設定檔，進行微幅編輯並儲存原則。 原則將會在後端重新計算，而且設定將會從您的原則中刪除。
- 如果您選擇不要採取此動作，終端使用者將會在其裝置的管理設定檔中看到此設定，但設定不會有任何作用。

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>我該如何為此變更做準備？
您可以根據上一節採取動作，或讓您的原則保持原狀。 當此變更推出時，我們將會更新 [新功能] 頁面與文件。

### <a name="end-of-support-for-legacy-pc-management"></a>結束對舊版電腦管理的支援

自 2020 年 10 月 15 日起結束對舊版電腦管理的支援。 請將裝置升級至 Windows 10，並重新註冊為 MDM 裝置，讓 Intune 管理它們。

[深入了解](https://go.microsoft.com/fwlink/?linkid=2107122)

### <a name="decreasing-support-for-android-device-administrator"></a>減少 Android 裝置系統管理員的支援 
Android 裝置系統管理員 (有時稱為「舊版」Android 管理，隨 Android 2.2 發行)，是一種管理 Android 裝置的方式。 不過，您現在可以在 [Android Enterprise](../enrollment/connect-intune-android-enterprise.md) \(隨 Android 5.0 發行\) 中找到已改善的管理功能。 為了要移到現代化、更豐富且更安全的裝置管理，Google 在新的 Android 版本中減少了裝置系統管理員的支援。

#### <a name="how-does-this-affect-me"></a>此變更對我造成什麼影響？
由於 Google 的這些變更，Intune 使用者會受到下列方面的影響：  
- Intune 僅支援執行 Android 10 與更新版本 (亦稱為 Android Q) 的裝置系統管理員受控 Android 裝置，且支援僅提供至 2020 年夏天。 這是下一個 Android 主要版本預計發行的日期。   
- 在 2020 年夏天之後，將無法再全面管理執行 Android 10 或更新版本的裝置系統管理員受控裝置。       
- 在 Android 10 以下的 Android 版本上，系統中仍有的裝置系統管理員管理的 Android 裝置將不會受到影響，而且可以繼續使用裝置系統管理員完全管理。    
- 針對所有執行 Android 10 與更新版本的裝置，Google 已限制裝置系統管理員管理代理程式 (例如公司入口網站) 存取裝置識別碼資訊的能力。 這會影響裝置更新至 Android 10 或更新版本之後的下列 Intune 功能：  
    - VPN 的網路存取控制將不再有效。   
    - 透過 IMEI 或序號識別為公司擁有的裝置，將不會自動將裝置標示為公司擁有。  
    - 在 Intune 中，IT 系統管理員再也看不到 IMEI 與序號。 
        > [!NOTE]
        > 這只會影響 Android 10 與更新版本的裝置系統管理員受控裝置，且不會影響受 Android Enterprise 管理的裝置。 

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>我需要為這項變更做什麼準備？
為避免在 2020 年夏天即將來臨的功能減少，建議您執行下列動作：
- 不要在裝置系統管理員管理中上架新裝置。
- 若裝置預期會收到 Android 10 的更新，請將它從裝置系統管理員管理移轉到 Android Enterprise 管理和/或應用程式保護原則。

#### <a name="additional-information"></a>其他資訊
- [Google's guidance for migration from device administrator to Android Enterprise](http://static.googleusercontent.com/media/android.com/en/enterprise/static/2016/pdfs/enterprise/Android-Enterprise-Migration-Bluebook_2019.pdf) (Google 指南：從裝置系統管理員移轉到 Android Enterprise)
- [Google's documentation on the plan to deprecate the device administrator API](https://developers.google.com/android/work/device-admin-deprecation) (Google 文件：裝置系統管理員 API 淘汰因應措施)

### <a name="update-your-android-company-portal-app-to-the-latest-version---4536963--"></a>將您的 Android 公司入口網站應用程式更新到最新的版本 <!--4536963-->
Intune 會定期發行 Android 公司入口網站應用程式更新。 在 2018 年 11 月，我們發行了公司入口網站更新，其中包括因應 Google 從其現有通知平台轉換到 Google Firebase 雲端傳訊 (FCM) 而做的後端切換參數準備。 當 Google 淘汰其現有通知平台並移轉到 FCM 時，終端使用者至少必須將其公司入口網站應用程式更新到 2018 年 11 月版本以繼續與 Google Play 商店通訊。

#### <a name="how-does-this-affect-me"></a>此變更對我造成什麼影響？
我們的遙測指出您擁有「公司入口網站」版本比 5.0.4269.0 舊的裝置。 若未安裝此版本或更新版本的公司入口網站應用程式，則 IT 專業人員起始的裝置動作 (例如抹除、重設密碼、可用與必要應用程式安裝、憑證註冊) 可能無法如預期運作。 若您的裝置在 Intune 中以 MDM 方式註冊，您可以移至 [用戶端應用程式] – [探索到的應用程式] 來查看公司入口網站版本與使用者。 選取舊版的公司入口網站應用程式，可讓您查看哪些終端使用者有尚未更新公司入口網站應用程式的裝置。

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>我需要為這項變更做什麼準備？
要求尚未更新 Android 裝置的終端使用者透過 Google Play 更新公司入口網站應用程式。 若使用者未持續自動更新公司入口網站應用程式，請通知您的技術支援中心。 如需 Google FCM 平台與變更的詳細資訊，請參閱「額外資訊」  中的連結。

#### <a name="additional-information"></a>其他資訊
https://firebase.google.com/docs/cloud-messaging/


### <a name="new-full-screen-experience-coming-to-intune---4593669--"></a>Intune 即將推出新的全螢幕體驗 <!--4593669-->
我們即將在 Azure 入口網站推出更新後的 Intune 建立與編輯 UI 體驗。 這個新體驗將透過可容納在單一刀鋒視窗內的精靈樣式格式來簡化現有工作流程。 此更新將拋棄「刀鋒視窗擴展」或任何要求您向下切入至深層刀鋒視窗旅程圖的建立與編輯流程。 建立工作流程也會更新以包含指派 (應用程式指派除外)。

#### <a name="how-does-this-affect-me"></a>此變更對我造成什麼影響？
Intune 全螢幕體驗將於接下來幾個月在 portal.azure.com 與 devicemanagement.microsoft.com 推出。 這個對 UI 的更新將會影響現有原則的功能與設定檔，但您將會看到稍微修改的工作流程。 例如，當您建立新原則時，您將能在建立此流程時設定一些指派，而不是在建立原則之後才設定指派。 請參閱「其他資訊」  的部落格文章，以取得螢幕擷取畫面，了解新體驗在主控台中看起來像什麼樣子。

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>我該如何為此變更做準備？
您不需要採取任何動作，但可以考慮視需要更新您的 IT 專業人員指導方針。 當 Azure 入口網站的 Intune 在各個刀鋒視窗推出此體驗時，我們將會更新我們的文件。

#### <a name="additional-information"></a>其他資訊 
https://aka.ms/intune_fullscreen

### <a name="plan-for-change-intune-app-sdk-and-app-protection-policies-for-android-moving-to-support-android-50-and-higher-in-an-upcoming-release---4911065---"></a>規劃變更：適用於 Android 的 Intune App SDK 與應用程式保護原則會在即將推出的版本中開始支援 Android 5.0 與更新版本 <!--4911065 -->
Intune 將會在即將推出的版本中開始支援 Android 5.x (Lollipop) 與更新版本。 使用最新的 Intune App SDK 更新任何已包裝的應用程式，並更新您的裝置。

#### <a name="how-does-this-affect-me"></a>此變更對我造成什麼影響？
如果您使用的不是或不打算使用 Android 版 SDK 或應用程式，則此變更不會影響您。 若您使用 Intune App SDK，請務必更新至最新版本，並一併將您的裝置更新為 Android 5.x 與更高版本。 若您不更新，應用程式就不會收到更新，且其體驗品質會隨著時間而降低。

在下面尋找執行 Android 4.x 版且在 Intune 中註冊的通用裝置清單。 若您有這類裝置，請採取適當步驟，以確定此裝置將支援 Android 5.0 版或更高版本，否則它會被支援 Android 5.0 版或更新版本的裝置所取代。 此清單並未包含所有可能需要評估的裝置：

- Samsung SM-T561  
- Samsung SM-T365
- Samsung GT-I9195
- Samsung SM-G800F
- Samsung SM-G357FZ
- Motorola XT1080
- Samsung GT-I9305
- Samsung SM-T231

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>我需要為這項變更做什麼準備？
使用最新的 Intune App SDK 包裝您的應用程式。 您也可以設定 [需要最低 OS 版本 (僅警告)] 條件式啟動設定，以通知個人裝置的終端使用者進行升級。

### <a name="intune-plan-for-change-nearing-end-of-support-for-windows-7---3042987---"></a>Intune 規劃變更：即將結束對 Windows 7 的支援<!-- 3042987 -->
如我們在 2018 年 9 月於 MC148476 所發佈並於 2019 年 3 月於 MC176794 中再次發佈的訊息，Windows 7 將在 2020 年 1 月 14 日結束其延伸支援。 屆時，Intune 將不再支援執行 Windows 7 的裝置，以便我們將精力專注在支援較新技術並提供絕佳的新終端使用者體驗。 在該日期之後，將無法再透過 Intune 取得可協助保護您 Windows 7 PC 的技術協助與自動更新。 Microsoft 強烈建議您在 2020 年 1 月之前升級到 Windows 10，以免發生不再提供所需服務或支援的情況。 在[這裡](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet)閱讀更多有關 Windows 支援生命週期的資訊。

#### <a name="how-does-this-affect-me"></a>此變更對我造成什麼影響？
您收到此訊息的原因，是因為您目前正在使用舊版的 Intune 電腦軟體代理程式來管理 Windows 7 電腦。 由於距離 Windows 7 延伸支援終止已不到一年，因此我們強烈建議您的組織儘快開始升級到 Windows 10。  

電腦管理功能已直接內建到 Windows 10 作業系統中，因此您再也不需要安裝用戶端代理程式，例如適用於 Windows 7 的 Intune 軟體用戶端。 從 Windows 8.1 開始，Microsoft 使用行動裝置管理 (MDM) 架構來佈建、設定、更新及管理 Windows PC。 設定 Intune 之後，您可以透過 MDM 通道[向 Intune 註冊 Windows 10 電腦](..\windows-enroll.md)，以簡化 Windows 註冊。 我們建議您使用這個「無代理程式」MDM 管理解決方案來管理您的 Windows 10 電腦。

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>我需要為這項變更做什麼準備？
我們鼓勵您的組織立即考慮此行動計畫：

- 在 2020 年 1 月 14 日之前規劃並升級 Windows 7 至 Windows 10。
- 探索 [Windows 10 部署支援](https://docs.microsoft.com/windows/deployment/)以深入了解如何將現有的 Windows 7 電腦群升級到 Windows 10。
- 透過 FastTrack 檢閱[電腦 App 保證](https://www.microsoft.com/fasttrack/microsoft-365/desktop-app-assure?rtc=1)方案，以解決 Microsoft 應用程式相容性問題。
- 將現有舊版 Intune 軟體用戶端受控裝置移轉到 Microsoft 建議的解決方案，以使用 MDM 管理來管理 Windows 10。 在 Azure 入口網站中使用適用於 Intune 的 MDM 管理來註冊所有 Windows 10 新電腦。

如需詳細資訊，請參閱此[部落格文章](https://aka.ms/Windows7_Intune)。

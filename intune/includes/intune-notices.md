---
title: 包含檔案
description: 包含檔案
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: include
ms.date: 03/28/2019
ms.author: erikje
ms.custom: include file
ms.openlocfilehash: fa251a0edd943d566849b138af5cbab0be248a53
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2019
ms.locfileid: "71726397"
---
這些注意事項提供可協助您針對未來的 Intune 變更與功能進行準備的重要資訊。 


### <a name="decreasing-support-for-android-device-administrator"></a>減少 Android 裝置系統管理員的支援 
Android 裝置系統管理員 (有時稱為「舊版」的 Android 管理，而且隨 Android 2.2 發行) 是一種管理 Android 裝置的方式。 不過，您現在可以在 [Android Enterprise](../enrollment/connect-intune-android-enterprise.md) \(隨 Android 5.0 發行\) 中找到已改善的管理功能。 為了要移到現代化、更豐富且更安全的裝置管理，Google 在新的 Android 版本中減少了裝置系統管理員的支援。

#### <a name="how-does-this-affect-me"></a>此變更對我造成什麼影響？
由於 Google 的這些變更，Intune 使用者會受到下列方面的影響： 
- Intune 只能為執行 Android 10 (亦稱為 Android Q) 與更新版本的裝置系統管理員管理 Android 裝置提供支援，且支援僅提供至 2020 年夏天。 這是下一個 Android 主要版本的預計發行日期。  
- 在 2020 年夏天之後，執行 Android 10 或更新版本的裝置系統管理員管理裝置將無法再完全受到管理。    
- 在 Android 10 以下的 Android 版本上，系統中仍有的裝置系統管理員管理的 Android 裝置將不會受到影響，而且可以繼續使用裝置系統管理員完全管理。  
- 針對所有 Android 10 與更新版本的裝置，Google 已限制裝置系統管理員管理代理程式 (例如公司入口網站) 存取裝置識別碼資訊的能力。 這會影響裝置更新至 Android 10 或更新版本之後的下列 Intune 功能： 
    - VPN 的網路存取控制將不再有效。  
    - 將裝透過 IMEI 或序號將裝置識別為公司擁有裝置將不會自動將裝置標示為公司擁有。 
    - 在 Intune 中，IT 系統管理員將不會再看到 IMEI 與序號。 
        > [!Note]
        > 這只會影響 Android 10 與更新版本上的裝置系統管理員管理裝置，而不會影響受 Android Enterprise 管理的裝置。 

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>我需要為這項變更做什麼準備？
若要避免在 2020 年夏天推出的功能減少，建議您執行下列動作:
- 不要將新裝置使用裝置系統管理員管理。
- 若裝置預期會收到 Android 10 的更新，請將它從裝置系統管理員管理移轉到 Android Enterprise 管理和/或應用程式保護原則。

#### <a name="additional-information"></a>其他資訊
- [Google 從裝置系統管理員移轉到 Android Enterprise 指南](http://static.googleusercontent.com/media/android.com/en/enterprise/static/2016/pdfs/enterprise/Android-Enterprise-Migration-Bluebook_2019.pdf) \(英文\)
- [Google 裝置系統管理員 API 過時因應措施文件](https://developers.google.com/android/work/device-admin-deprecation) \(英文\)

### <a name="update-your-android-company-portal-app-to-the-latest-version---4536963--"></a>將您的 Android 公司入口網站應用程式更新到最新的版本 <!--4536963-->
Intune 會定期發行 Android 公司入口網站應用程式更新。 在 2018 年 11 月，我們發行了公司入口網站更新，其中包括因應 Google 從其現有通知平台轉換到 GoogleFirebase 雲端傳訊 (FCM) 而做準備的後端切換參數。 當 Google 淘汰其現有通知平台並移轉到 FCM 時，終端使用者至少必須將其公司入口網站應用程式更新到 2018 年 11 月版本以繼續與 Google Play 商店通訊。

#### <a name="how-does-this-affect-me"></a>此變更對我造成什麼影響？
我們的遙測指出您擁有「公司入口網站」版本比 5.0.4269.0 舊的裝置。 若未安裝此版本或更新版本的「公司入口網站」應用程式，IT 專業人員起始的裝置動作 (例如抹除、重設密碼、可用與必要應用程式安裝、憑證註冊) 可能無法如預期般運作。 若您的裝置在 Intune 中以 MDM 方式註冊，您可以移至 [用戶端應用程式] – [探索到的應用程式] 以查看公司入口網站版本與使用者。 選取舊版「公司入口網站」將可讓您查看哪些終端使用者有尚未更新公司入口網站的裝置。

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>我需要為這項變更做什麼準備？
要求尚未更新的 Android 裝置終端使用者透過 Google Play 商店更新公司入口網站。 若使用者未持續自動更新公司入口網站應用程式，請通知您的技術支援中心。 查看＜額外資訊＞中的連結以取的有關 Google FCM 平台與變更的詳細資訊。

#### <a name="additional-information"></a>其他資訊
https://firebase.google.com/docs/cloud-messaging/


### <a name="new-fullscreen-experience-coming-to-intune---4593669--"></a>即將在 Intune 中推出的新全螢幕體驗 <!--4593669-->
我們正在為 Azure 入口網站中的 Intune 推出更新的建立與編輯 UI 體驗。 這個新的體驗將可透過可容納在單一刀鋒視窗內的精靈樣式格式來簡化現有的工作流程。 此更新將拋棄「刀鋒視窗」或任何要求您向下切入至深層刀鋒視窗旅程圖的建立與編輯流程。 建立工作流程也會更新以包含指派 (應用程式指派除外)。

#### <a name="how-does-this-affect-me"></a>此變更對我造成什麼影響？
全螢幕體驗將在接下來幾個月推出到位於 portal.azure.com 與 devicemanagement.microsoft.com 的 Intune。 這個對 UI 的更新將會影響現有原則的功能與設定檔，但您將會看到稍微修改的工作流程。 例如，當您建立新原則時，您將能在建立此流程時設定一些指派，而不是在建立原則之後才設定指派。 請查看部落格文章的＜其他資訊＞，以檢視新體驗在主控台中看起來像什麼樣子的螢幕擷取畫面。

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>我該如何為此變更做準備？
您不需要採取任何動作，但可以考慮視需要更新您的 IT 專業人員指導方針。 當此體驗推出到 Azure 入口網站上 Intune 中的各個刀鋒視窗時，我們將會更新我們的文件。

#### <a name="additional-information"></a>其他資訊 
https://aka.ms/intune_fullscreen

### <a name="plan-for-change-new-windows-updates-settings-in-intune----4464404---"></a>規劃變更：Intune 中的新 Windows 更新設定 <!-- 4464404 -->
從 8 月版的 Intune 服務或 1908 開始，我們新增了新的「期限設定」，您可以設定此功能而不是 [可讓使用者重新啟動 (預約重新啟動)] 設定。 我們計劃在 1909 或 9 月更新中停用使用者介面中的重新開機設定，然後在 10 月底之前將它們從主控台中完全移除。

#### <a name="how-does-this-affect-me"></a>此變更對我造成什麼影響？
如果您在您的環境中管理 Windows 10 裝置：

- 使用 8 月 Intune 更新或 1908，除了舊的預約重新啟動設定之外，您還將在主控台中看到新的期限設定。
- 當您同時設定這些舊的和新的設定時，期限設定值將會覆寫已啟用的預約重新啟動設定值。
- 期限設定將取代 1910 更新中主控台內的 [可讓使用者重新啟動 (預約重新啟動)] 選項。

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>我該如何為此變更做準備？
透過使用您想要的值設定 1908 中的期限設定，來開始使用它們。 備妥之後，可以將已啟用的預約重新啟動設定設為 [尚未設定]，為這些設定將在 10 月從主控台中移除做準備。

如有需要，請更新您的文件和任何自動化指令碼。

我們會及時通知您更新並將提醒張貼到訊息中心，然後我們會移除預約重新啟動設定。

### <a name="plan-for-change-intune-app-sdk-and-app-protection-policies-for-android-moving-to-support-android-50-and-higher-in-october---4911065---"></a>規劃變更：適用於 Android 的 Intune App SDK 與應用程式保護原則會在10月移至支援 Android 5.0 與更新版本 <!--4911065 -->
Intune 將會在10月移至支援 Android 5.x (Lollipop) 與更新版本。 使用最新的 Intune App SDK 更新任何已包裝的應用程式，並更新您的裝置。

#### <a name="how-does-this-affect-me"></a>此變更對我造成什麼影響？
若您不是使用或計畫使用適用於 Android 的 SDK 或應用程式，此變更不會影響您。 若您使用 Intune App SDK，請務必更新至最新版本，並一併將您的裝置更新為 Android 5.x 與更高版本。 若您未更新，應用程式將不會接收更新，而且其體驗品質會隨著時間而降低。

在下面尋找執行 Android 4.x 版且在 Intune 中註冊的通用裝置清單。 若您有其中一部裝置，請採取適當的步驟，以確定此裝置將支援 Android 5.0 版或更高版本，或它將會被取代為支援 Android 5.0 版或更新版本的裝置。 此清單並未包含所有可能需要評估的裝置：

- Samsung SM-T561  
- Samsung SM-T365
- Samsung GT-I9195
- Samsung SM-G800F
- Samsung SM-G357FZ
- Motorola XT1080
- Samsung GT-I9305
- Samsung SM-T231

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>我需要為這項變更做什麼準備？
使用最新的 Intune App SDK 包裝您的應用程式。 您也可以設定 [需要最低 OS 版本 (僅警告)] 條件式啟動設定，以通知個人裝置上的使用者進行升級。

### <a name="intune-plan-for-change-nearing-end-of-support-for-windows-7----3042987---"></a>Intune 針對變更做好規劃：接近 Windows 7 終止支援 <!-- 3042987 -->
如我們在 2018 年 9 月於 MC148476 所發佈並於 2019 年 3 月於 MC176794 中重新發佈的訊息，Windows 7 將在 2020 年 1 月 14 日達到延伸支援結束。 屆時，Intune 將不再支援執行 Windows 7 的裝置，以便我們可以將我們的精力專注在支援較新的技術並提供絕佳新終端使用者體驗。 在該日期之後，將無法再透過 Intune 取得可協助保護您 Windows 7 PC 的技術協助與自動更新。 Microsoft 強烈建議您在 2020 年 1 月之前升級到 Windows 10，以避免您需要已不再提供之服務或支援的情況。 在[這裡](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet)閱讀更多有關 Windows 支援生命週期的資訊。

#### <a name="how-does-this-affect-me"></a>此變更對我造成什麼影響？
您收到此訊息的原因是您目前正在使用傳統 Intune PC 軟體代理程式來管理 Windows 7 PC。 由於距離 Windows 7 延伸支援終止已不到一年，我們強烈建議您的組織儘快開始升級到 Windows 10。 PC 電腦管理功能已直接內建到 Windows 10 作業系統中，因此您再也不需要安裝用戶端代理程式，例如適用於 Windows 7 的 Intune 軟體用戶端。 從 Windows 8.1 開始，Microsoft 使用行動裝置管理 (MDM) 架構來佈建、設定、更新及管理 Windows PC。 設定 Intune 之後，您可以透過使用 MDM 通道[向 Intune 註冊 Windows 10 PC](..\windows-enroll.md)，以簡化 Windows 管理程序。 我們建議您使用這個「無代理程式」MDM 管理解決方案來管理您的 Windows 10 PC。

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>我需要為這項變更做什麼準備？
我們鼓勵您的組織立即考慮此行動計畫：

- 在 2020 年 1 月 14 日之前規劃並升級 Windows 7 至 Windows 10。
- 探索 [Windows 10 部署支援](https://docs.microsoft.com/windows/deployment/)以深入了解如何將您現有的 Windows 7 PC 升級到 Windows 10。
- 透過 Fast Track 檢閱[電腦 App 保證](https://www.microsoft.com/fasttrack/microsoft-365/desktop-app-assure?rtc=1)方案，以解決 Microsoft 應用程式相容性問題。
- 將現有的傳統 Intune 軟體用戶端受管理的裝置移轉到 Microsoft 建議的解決方案以使用 MDM 管理來管理 Windows 10。 在 Azure 入口網站中使用適用於 Intune 的 MDM 管理註冊所有新的 Windows 10 PC。
- 如需詳細資訊，請參閱此[部落格文章](https://aka.ms/Windows7_Intune) \(英文\)。

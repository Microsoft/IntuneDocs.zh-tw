---
title: 包含檔案
description: 包含檔案
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: include
ms.date: 11/19/2019
ms.author: erikje
ms.custom: include file
ms.openlocfilehash: 9aa82268fb02f5124e48eb303f19cf32be02c284
ms.sourcegitcommit: c46b0c2d4507be6a2786a4ea06009b2d5aafef85
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/01/2020
ms.locfileid: "76912622"
---
這些注意事項提供可協助您針對未來的 Intune 變更與功能進行準備的重要資訊。

### <a name="updated-feature-new-rbac-role-coming-to-intune--4253397--"></a>更新的功能：Intune 即將推出新的 RBAC 角色<!--4253397-->
在 1 月份的 Intune 服務更新中，我們計畫在 Intune 中推出新的安全性角色。 您在 Intune 中將會看到此角色被列為「端點安全性管理員」，且該角色是 Azure AD「安全性系統管理員」的延伸。
 
#### <a name="how-does-this-affect-me"></a>此變更會對我造成什麼影響？
目前，Azure AD 中有三個角色可供安全性專業人員使用：
- Azure AD 中的安全性讀取者角色，可提供對 Intune 的唯讀存取權。
- Azure AD 中的安全性操作員角色，可提供對 Intune 的唯讀存取權。
- Azure AD 中的安全性系統管理員。 當 Intune 推出 1 月份更新時，除了對 Intune 的唯讀權限之外，還有端點安全性管理員角色提供的新權限，如下所示：
    - 讀取、建立、更新、刪除及指派裝置合規性原則
    - 讀取、刪除及更新受控裝置
    - 讀取、建立、更新、刪除及指派安全性基準
    - 讀取及更新安全性工作
 
### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>我需要為這項變更做什麼準備？
立即檢閱您的 Intune RBAC 角色。 如果您目前只有全域管理員作為角色，則不需要做任何變更。 如果您會使用角色，且您想要端點安全性管理員所提供的細微性，請在該角色可用時指派它。 請查看 Intune [[新功能]](../fundamentals/whats-new.md) 頁面以取得最新的 Intune 版本資訊。 

### <a name="updated-support-statement-for-adobe-acrobat-reader-for-intune-mobile-app--5746776--"></a>「Adobe Acrobat Reader for Intune」行動應用程式的已更新支援聲明<!--5746776-->
我們在 8 月底於 MC188653 中分享了 Adobe Acrobat Reader for Intune 行動應用程式會在 2019 年 12 月 1 日終止生命週期，且 Adobe 已規劃在其主要 Acrobat Reader 應用程式中支援 Intune 的應用程式保護原則。 從那時起，我們收到客戶意見反應，我們需要提供更多時間來繼續讓 IT 系統管理員以 Adobe Acrobat Reader for Intune 為目標，以及讓終端使用者繼續使用它。 有鑑於 Adobe Acrobat Reader for Intune 在終端使用者裝置上有高使用量，以及其在企業案例中的重要性，我們想要確保任何體驗都符合您組織的應用程式保護需求。 

雖然 Adobe Acrobat Reader for Intune 應用程式會繼續受支援，直到 2020 年 3 月 31 日為止，我們仍然建議您在原則中將一般的 Acrobat Reader 行動應用程式設為目標，因為 Acrobat Reader 行動應用程式支援應用程式保護原則，且已整合 Intune SDK。 

#### <a name="how-does-this-affect-me"></a>此變更會對我造成什麼影響？
因為我們的報告指出您組織中的一或多個原則是以 Adobe Acrobat Reader for Intune 應用程式為目標，且/或您已收到我們先前的 EOL 通訊，所以傳送此訊息通知您。 

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>我需要為這項變更做什麼準備？
讓您的終端使用者和技術服務人員知道此變更。 您可以使用[公司入口網站的支援資訊功能](../apps/company-portal-app.md#support-information)，來建立 Intune 相關問題的通道。

#### <a name="additional-information"></a>其他資訊
https://helpx.adobe.com/acrobat/kb/intune-app-end-of-life.html


### <a name="end-support-for-windows-phone-81--3544909--"></a>Windows Phone 8.1 終止支援<!--3544909-->
Windows Phone 8.1 的 Microsoft 主要支援已於 2017 年 7 月終止，而且延伸支援已於 2019 年 6 月結束。 適用於 Windows Phone 8.1 的公司入口網站應用程式從 2017 年 10 月起就進入維持模式了。 Microsoft Intune 現在將於 2020 年 2 月 20 日終止對 Windows Phone 8.1 的支援。

#### <a name="how-does-this-affect-me"></a>此變更會對我造成什麼影響？
2020 年 2 月 20 日之後，這些裝置將不會收到任何安全性更新，而且您將無法註冊任何新裝置。 現有的 Windows Phone 8.1 裝置會保持在註冊狀態 (原則、應用程式、報告)，但請注意，在此日期之後，將不再支援現有註冊的任何疑難排解，原因是許多元件 (例如協力廠商憑證) 已終止對該平台的支援。 Intune 將會停止與 Intune 和 Windows Phone 8.1 的相容性測試。

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>我需要為這項變更做什麼準備？
您可以檢查您的 Intune 報告，查看哪些裝置或使用者可能會受到影響。 移至 [裝置] > [所有裝置]，然後依 OS 進行篩選。 您可以新增其他資料行，協助識別您組織中誰有執行 Windows Phone 8.1 的裝置。 要求使用者將其裝置升級至支援的 OS 版本。


### <a name="take-action-use-microsoft-edge-for-your-protected-intune-browser-experience--5728447--"></a>採取動作：將 Microsoft Edge 用於受保護的 Intune 瀏覽器體驗<!--5728447-->
隨著過去一年的分享，Microsoft Edge 行動裝置版本支援與 Managed Browser 相同的一組管理功能，同時提供更好的終端使用者體驗。 為了讓 Microsoft Edge 中提供的強大體驗得以實現，我們將會淘汰 Intune Managed Browser。 從 2020 年 1 月 27 日開始，Intune 將不再支援 Intune Managed Browser。  

#### <a name="how-does-this-affect-me"></a>此變更會對我造成什麼影響？ 
從 2020 年 2 月 1 日開始，Google Play 商店或 iOS App Store 中將不再提供 Intune Managed Browser。 此時，您仍然可以將新應用程式保護原則的目標設為 Intune Managed Browser，但新的使用者將無法下載 Intune Managed Browser 應用程式。 此外，在 iOS 上，向下推送至 MDM 註冊裝置的新 Web 剪輯，將會在 Microsoft Edge 中開啟，而不是在 Intune Managed Browser 中開啟。  

從 2020 年 3 月 31 日起，將從 Azure 主控台移除 Intune Managed Browser。 這表示您將無法再為 Intune Managed Browser 建立新原則。 現有的 Intune Managed Browser 原則不會受到影響。 Intune Managed Browser 將會顯示在主控台中，作為沒有圖示的 LOB 應用程式，而現有的原則仍會顯示為以應用程式為目標。 此時，我們也會在應用程式保護原則的 [資料保護] 區段中，移除將 Web 內容重新導向至 Intune Managed Browser 的選項。  

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>我需要為這項變更做什麼準備？ 
若要確保從 Intune Managed Browser 順利轉換到 Microsoft Edge，建議您主動執行下列步驟： 

1. 使用應用程式保護原則 (亦稱為 MAM) 與應用程式組態設定，以適用於 iOS 與 Android 的 Microsoft Edge 為目標。 您也可以將現有原則的目標設定為 Microsoft Edge，以針對 Microsoft Edge 重複使用 Intune Managed Browser 原則。  
2. 確定您環境中所有受 MAM 保護的應用程式的應用程式保護原則設定 [限制使用其他應用程式的 Web 內容傳輸] 設定為 [受原則管理的瀏覽器]。 
3. 在受管理的應用程式組態設定 "com.microsoft.intune.useEdge" 設定為 True 的情況下以所有受 MAM 保護的項目為目標。 從下個月將推出的 1911 版開始，您只需要設定 [限制使用其他應用程式的 Web 內容傳輸] 設定以在您應用程式保護原則的 [資料保護] 區段中選取 [Microsoft Edge]，就可以完成步驟 2 與 3。 

即將推出對 iOS 與 Android 上 Web 剪輯的支援。 當此支援發行後，您必須為預先存在的 Web 剪輯重定目標，以確保其在 Microsoft Edge 中開啟，而不是在 Managed Browser 中開啟。 

#### <a name="additional-information"></a>其他資訊
如需詳細資訊，請參閱我們的[搭配應用程式保護原則使用 Microsoft Edge](../apps/manage-microsoft-edge.md) 相關文件，或我們的[支援部落格文章](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Use-Microsoft-Edge-for-your-Protected-Intune-Browser-Experience/ba-p/1004269)。


### <a name="end-of-support-for-legacy-pc-management"></a>結束對舊版電腦管理的支援

自 2020 年 10 月 15 日起結束對舊版電腦管理的支援。 請將裝置升級至 Windows 10，並重新註冊為行動裝置管理 (MDM) 裝置，以繼續交由 Intune 管理。

[深入了解](https://go.microsoft.com/fwlink/?linkid=2107122)

### <a name="decreasing-support-for-android-device-administrator"></a>減少 Android 裝置系統管理員的支援 
Android 裝置系統管理員 (有時稱為「舊版」Android 管理，隨 Android 2.2 發行)，是一種管理 Android 裝置的方式。 不過，您現在可以在 [Android Enterprise](../enrollment/connect-intune-android-enterprise.md) \(隨 Android 5.0 發行\) 中找到已改善的管理功能。 為了要移到現代化、更豐富且更安全的裝置管理，Google 在新的 Android 版本中減少了裝置系統管理員的支援。

#### <a name="how-does-this-affect-me"></a>此變更會對我造成什麼影響？
由於 Google 的這些變更，Intune 使用者會受到下列方面的影響：  
- Intune 只能為執行 Android 10 和更新版本之裝置系統管理員受控的 Android 裝置提供完整支援，且支援僅提供至 2020 年度第 2 季。 在此期間過後，執行 Android 10 或更新版本之裝置系統管理員受控的裝置將無法再完全受控。 尤其受影響的裝置不會再收到新的密碼要求。
    - 在此期間內，Samsung Knox 裝置不會受到影響，因為其透過 Intune 與 Knox 平台的整合來獲得延伸支援。 讓您有更多時間規劃裝置系統管理員管理的轉換。    
- 在 Android 10 以下的 Android 版本上，仍由裝置系統管理員管理的 Android 裝置不會受到影響，並可繼續由裝置系統管理員全權管理。    
- 針對所有執行 Android 10 與更新版本的裝置，Google 已限制裝置系統管理員管理代理程式 (例如公司入口網站) 存取裝置識別碼資訊的能力。 當裝置更新為 Android 10 或更新版本之後，此限制會影響下列 Intune 功能：  
    - VPN 的網路存取控制將不再有效。   
    - 透過 IMEI 或序號識別為公司擁有的裝置將不會自動將裝置標示為公司擁有。  
    - 在 Intune 中，IT 系統管理員再也看不到 IMEI 與序號。 
        > [!NOTE]
        > 這只會影響 Android 10 與更新版本的裝置系統管理員受控裝置，且不會影響受 Android Enterprise 管理的裝置。 

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>我需要為這項變更做什麼準備？
若要避免功能在 2020 年度第 3 季減少，建議您執行下列動作:
- 不要在裝置系統管理員管理中上架新裝置。
- 若裝置預期會收到 Android 10 的更新，請將它從裝置系統管理員管理移轉到 Android Enterprise 管理和/或應用程式保護原則。

#### <a name="additional-information"></a>其他資訊
- [Google's guidance for migration from device administrator to Android Enterprise](http://static.googleusercontent.com/media/android.com/en/enterprise/static/2016/pdfs/enterprise/Android-Enterprise-Migration-Bluebook_2019.pdf) (Google 指南：從裝置系統管理員移轉到 Android Enterprise)
- [Google's documentation on the plan to deprecate the device administrator API](https://developers.google.com/android/work/device-admin-deprecation) (Google 文件：裝置系統管理員 API 淘汰因應措施)

### <a name="plan-for-change-intune-app-sdk-and-app-protection-policies-for-android-moving-to-support-android-50-and-higher-in-an-upcoming-release---4911065---"></a>規劃變更：適用於 Android 的 Intune App SDK 與應用程式保護原則會在即將推出的版本中開始支援 Android 5.0 與更新版本 <!--4911065 -->
Intune 將會在即將推出的版本中開始支援 Android 5.x (Lollipop) 與更新版本。 使用最新的 Intune App SDK 更新任何已包裝的應用程式，並更新您的裝置。

#### <a name="how-does-this-affect-me"></a>此變更會對我造成什麼影響？
如果您使用的不是或不打算使用 Android 版 SDK 或應用程式，則此變更不會影響您。 若您使用 Intune App SDK，請務必更新至最新版本，並一併將您的裝置更新為 Android 5.x 與更高版本。 若不更新，則應用程式就不會收到更新，且其體驗品質會隨著時間而降低。

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

#### <a name="how-does-this-affect-me"></a>此變更會對我造成什麼影響？
您收到此訊息的原因，是因為您目前正在使用舊版的 Intune 電腦軟體代理程式來管理 Windows 7 電腦。 由於距離 Windows 7 延伸支援終止已不到一年，因此我們強烈建議您的組織儘快開始升級到 Windows 10。  

電腦管理功能已直接內建到 Windows 10 作業系統中，因此您再也不需要安裝用戶端代理程式，例如適用於 Windows 7 的 Intune 軟體用戶端。 從 Windows 8.1 開始，Microsoft 使用行動裝置管理 (MDM) 架構來佈建、設定、更新及管理 Windows PC。 設定 Intune 之後，您可以透過 MDM 通道[向 Intune 註冊 Windows 10 電腦](..\windows-enroll.md)，以簡化 Windows 註冊。 我們建議您使用這個「無代理程式」MDM 管理解決方案來管理您的 Windows 10 電腦。

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>我需要為這項變更做什麼準備？
我們鼓勵您的組織立即考慮此行動計畫：

- 在 2020 年 1 月 14 日之前規劃並升級 Windows 7 至 Windows 10。
- 探索 [Windows 10 部署支援](https://docs.microsoft.com/windows/deployment/)以深入了解如何將現有的 Windows 7 電腦群升級到 Windows 10。
- 透過 FastTrack 檢閱[電腦 App 保證](https://www.microsoft.com/fasttrack/microsoft-365/desktop-app-assure?rtc=1)方案，以解決 Microsoft 應用程式相容性問題。
- 將現有的舊版 Intune 軟體用戶端受控裝置轉換到 Microsoft 建議的解決方案，以使用 MDM 管理來管理 Windows 10。 在 Azure 入口網站中使用適用於 Intune 的 MDM 管理來註冊所有 Windows 10 新電腦。

如需詳細資訊，請參閱[這裡的部落格文章](https://aka.ms/Windows7_Intune)。



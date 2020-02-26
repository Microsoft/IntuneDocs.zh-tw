---
title: 包含檔案
description: 包含檔案
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: include
ms.date: 11/19/2019
ms.author: erikje
ms.custom: include file
ms.openlocfilehash: 373aeea9ab4fcbd075ac2ab18f205f3ddd191a39
ms.sourcegitcommit: 29f3ba071c9348686d3ad6f3b8864d8557e05b97
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/26/2020
ms.locfileid: "77609291"
---
這些注意事項提供可協助您針對未來的 Intune 變更與功能進行準備的重要資訊。

### <a name="microsoft-intune-support-for-windows-10-mobile-ending--3544938--"></a>適用於 Windows 10 行動裝置版的 Microsoft Intune 支援結束<!--3544938-->
Microsoft 針對 Windows 10 行動裝置版的主流支援已於 2019 年 12 月結束。 如此支援聲明中所述，Windows 10 行動裝置版使用者將不再具備接收來自 Microsoft 的新安全性更新、非安全性 Hotfix、免費協助支援選項，或線上技術內容更新的資格。 基於已結束的行動裝置版 OS 支援，Microsoft Intune 從 2020 年 5 月 11 日起將終止支援適用於 Windows 10 行動裝置版的公司入口網站應用程式，以及 Windows 10 行動裝置版作業系統。

#### <a name="how-does-this-affect-me"></a>此變更會對我造成什麼影響？
如果您已在組織中部署 Windows 10 行動裝置版裝置，從現在到 2020 年 5 月 11 日為止，您可以註冊新裝置、新增或移除原則與應用程式，或更新任何管理設定。 在 5 月 11 日之後，我們將會停止新的註冊，而且最終會從 Intune UI 移除 Windows 10 行動裝置版管理。 裝置將無法再簽入 Intune 服務，而且我們將會刪除裝置與原則資料。  

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>我需要為這項變更做什麼準備？
您可以檢查您的 Intune 報告，查看哪些裝置或使用者可能會受到影響。 移至 [裝置]   > [所有裝置]  ，然後依作業系統篩選。 您可以新增其他欄，協助識別您組織中誰擁有執行 Windows 10 行動裝置版的裝置。 請要求您的終端使用者升級其裝置，或停止將該裝置用於公司存取。



### <a name="plan-for-change-change-in-experience-when-enrolling-android-enterprise-dedicated-devices-in-intune--6114580--"></a>規劃變更：變更在 Intune 中註冊 Android Enterprise 專用裝置的體驗<!--6114580-->
我們已在十一月版本中說明我們已將對 SCEP 憑證部署的支援新增至 Android Enterprise 專用裝置，以啟用 Wi-Fi 設定檔的憑證型存取功能。 此變更牽涉到 Android Enterprise 專用裝置的一些微幅註冊流程變更。 在即將推出的三月服務更新或 2003 中，有一些需要您注意的進一步變更。

#### <a name="how-does-this-affect-me"></a>此變更會對我造成什麼影響？
如果您是環境中 Android Enterprise 專用裝置的管理員，您將會在三月開始看到我們推出一些變更。
- 針對在 2019 年 11 月 22 日之前註冊的現有 Android 專用裝置，或 1911 服務更新：這些裝置上已安裝 Microsoft Intune 應用程式。 在三月的 Intune 服務中推出後端變更之後，將會開始套用部署至裝置並與 Wi-Fi 設定檔相關聯的 SCEP 憑證。
- 針對在 2019 年 11 月 22 日之後且此變更在三月推出之前註冊的裝置：這些裝置上已安裝 Microsoft Intune 應用程式。 將會繼續套用部署至裝置並與 Wi-Fi 設定檔相關聯的 SCEP 憑證。
- 針對變更在三月中推出之後的新 Android Enterprise 專用裝置註冊：終端使用者會在註冊期間看到一組不同的裝置設定步驟。 註冊仍會以目前的啟動方式啟動 (使用 QR、NFC、零接觸或裝置識別碼)，但將不會有強制應用程式安裝步驟。 相反地，Microsoft Intune 應用程式將會自動安裝在裝置上。 此外，終端使用者將不需要在流程期間點選 [啟用 Intune 代理程式]。 與 WiFi 設定檔相關聯的 SCEP 憑證可以部署到這些裝置。

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>如何為這項變更進行準備？
您可以更新終端使用者指導方針，並讓技術服務人員知道此變更。 我們將更新 [新功能] 頁面，並在此變更開始推出時，透過「訊息中心」通知您。

#### <a name="additional-information"></a>其他資訊
[Android Enterprise 專用裝置中的 SCEP 憑證支援](https://aka.ms/Dedicated_devices_enrollment)

### <a name="updated-support-statement-for-adobe-acrobat-reader-for-intune-mobile-app--5746776--"></a>「Adobe Acrobat Reader for Intune」行動應用程式的已更新支援聲明<!--5746776-->
我們在 8 月底於 MC188653 中分享了 Adobe Acrobat Reader for Intune 行動應用程式會在 2019 年 12 月 1 日終止生命週期，且 Adobe 已規劃在其主要 Acrobat Reader 應用程式中支援 Intune 的應用程式保護原則。 從那時起，我們收到客戶意見反應，我們需要提供更多時間來繼續讓 IT 系統管理員以 Adobe Acrobat Reader for Intune 為目標，以及讓終端使用者繼續使用它。 有鑑於 Adobe Acrobat Reader for Intune 在終端使用者裝置上有高使用量，以及其在企業案例中的重要性，我們想要確保任何體驗都符合您組織的應用程式保護需求。 

雖然 Adobe Acrobat Reader for Intune 應用程式會繼續受支援，直到 2020 年 3 月 31 日為止，我們仍然建議您在原則中將一般的 Acrobat Reader 行動應用程式設為目標，因為 Acrobat Reader 行動應用程式支援應用程式保護原則，且已整合 Intune SDK。 

#### <a name="how-does-this-affect-me"></a>此變更會對我造成什麼影響？
因為我們的報告指出您組織中的一或多個原則是以 Adobe Acrobat Reader for Intune 應用程式為目標，且/或您已收到我們先前的 EOL 通訊，所以傳送此訊息通知您。 

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>我需要為這項變更做什麼準備？
讓您的終端使用者和技術服務人員知道此變更。 您可以使用[公司入口網站的支援資訊功能](../apps/company-portal-app.md#support-information)，來建立 Intune 相關問題的通道。

#### <a name="additional-information"></a>其他資訊
https://helpx.adobe.com/acrobat/kb/intune-app-end-of-life.html


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

### <a name="decreasing-support-for-android-device-administrator--5857738--"></a>減少 Android 裝置系統管理員的支援<!--5857738-->
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




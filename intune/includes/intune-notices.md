---
title: 包含檔案
description: 包含檔案
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: include
ms.date: 03/28/2019
ms.author: erikje
ms.custom: include file
ms.openlocfilehash: d907c5256469e86410c9916d117d3e322d43cfc3
ms.sourcegitcommit: 2614d1b08b8a78cd792aebd2ca9848f391df8550
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2019
ms.locfileid: "67812464"
---
這些注意事項提供可協助您針對未來的 Intune 變更與功能進行準備的重要資訊。 

### <a name="update-your-android-company-portal-app-to-the-latest-version---4536963--"></a>將您的 Android 公司入口網站應用程式更新到最新的版本 <!--4536963-->
Intune 會定期發行 Android 公司入口網站應用程式更新。 在 2018 年 11 月，我們發行了公司入口網站更新，其中包括因應 Google 從其現有通知平台轉換到 GoogleFirebase 雲端傳訊 (FCM) 而做準備的後端切換參數。 當 Google 淘汰其現有通知平台並移轉到 FCM 時，終端使用者至少必須將其公司入口網站應用程式更新到 2018 年 11 月版本以繼續與 Google Play 商店通訊。

#### <a name="how-does-this-affect-me"></a>此變更對我造成什麼影響？
我們的遙測指出您擁有「公司入口網站」版本比 5.0.4269.0 舊的裝置。 若未安裝此版本或更新版本的「公司入口網站」應用程式，IT 專業人員起始的裝置動作 (例如抹除、重設密碼、可用與必要應用程式安裝、憑證註冊) 可能無法如預期般運作。 若您的裝置在 Intune 中以 MDM 方式註冊，您可以移至 [用戶端應用程式] – [探索到的應用程式] 以查看公司入口網站版本與使用者。 選取舊版「公司入口網站」將可讓您查看哪些終端使用者有尚未更新公司入口網站的裝置。

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>我需要為此變更做什麼準備？
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

### <a name="plan-for-change-intune-moving-to-support-ios-11-and-higher-in-september----4665342--"></a>規劃變更：Intune 將於 9 月開始支援 iOS 11 和更高版本 <!-- 4665342-->
Apple 預期於 9 月發行 iOS 13。 iOS 13 發行後，Intune 註冊、公司入口網站及受控瀏覽器即可支援 iOS 11 和更高版本。

#### <a name="how-does-this-affect-me"></a>此變更對我造成什麼影響？
如果 iOS 11.0 或更高版本支援 O365 行動裝置應用程式，則這可能不會影響您；您可能已經升級作業系統或裝置。 不過，如果您有下列任一裝置，或決定註冊下列任一裝置，請注意，下列裝置不支援 iOS 10 以上的版本。 這些裝置需要升級為支援 iOS 11 或更高版本的裝置：

- iPhone 5
- iPhone 5c
- iPad (第 4 代)

從 7 月開始，使用 iOS 10 和公司入口網站註冊的 MDM 裝置會收到升級作業系統或裝置的提示。 如果您使用應用程式保護原則 (APP)，您也可以設定 [需要最低的 iOS 作業系統 (僅警告)] 存取設定。

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>我需要為此變更做什麼準備？
檢查您的 Intune 報告，查看哪些裝置或使用者可能會受到影響。 移至 [裝置]   > [所有裝置]  ，然後依作業系統篩選。 您可以新增其他資料行，協助識別您組織中誰有執行 iOS 10 的裝置。 要求使用者在 9 月之前將其裝置升級至支援的作業系統版本。

### <a name="plan-for-change-support-for-version-811-and-higher-of-intune-app-sdk-for-ios----3586942--"></a>規劃變更：支援 iOS 版 Intune App SDK 8.1.1 版和更高版本 <!-- 3586942-->
從 2019 年 9 月開始，Intune 開始支援使用 Intune App SDK 8.1.1 及更高版本的 iOS 應用程式。 不再支援使用 SDK 8.1.1 以下版本建置的應用程式。 此變更預期會在 Apple 9 月發行 iOS 13 後生效，已在 MC181399 中宣告。

#### <a name="how-does-this-affect-me"></a>此變更對我造成什麼影響？
與 Intune App SDK 或 App Wrapping 整合，您可透過資料加密，保護公司資料不受未核准的應用程式和使用者存取。 根據預設，iOS 版的 Intune App SDK 會在 Intune 應用程式保護原則 (APP) 啟用加密時，使用 256 位元的加密金鑰。 在此變更後，SDK 8.1.1 版以前的 iOS 應用程式 (使用 128 位元加密金鑰)，將不再能夠與已整合 SDK 8.1.1 或使用 256 位元金鑰的應用程式共用資料。 所有的 iOS 應用程式都需要有 SDK 8.1.1 版或更高版本才能共用受保護資料。

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>我該如何為此變更做準備？
請檢查您的 Microsoft、協力廠商和企業營運 (LOB) 應用程式。 您應該確定所有受 Intune APP 保護的應用程式都使用 SDK 8.1.1 版或更新版本。

- 針對 LOB 應用程式：您可能需要重新發佈與 SDK 8.1.1 版或更新版本相整合的應用程式。 我們建議的最新 SDK 版本。 如需如何為應用程式保護原則準備 LOB 應用程式的相關資訊，請參閱[準備應用程式保護原則的企業營運應用程式](../apps-prepare-mobile-application-management.md)。
- 針對 Microsoft/協力廠商應用程式：請務必為使用者部署這些應用程式的最新版本。

SDK 支援如適合納入此變更，則您應該一併更新您的文件或開發人員指導方針。

#### <a name="additional-information"></a>其他資訊
https://docs.microsoft.com/intune/apps-prepare-mobile-application-management

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

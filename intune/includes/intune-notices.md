---
title: 包含檔案
description: 包含檔案
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: include
ms.date: 03/28/2019
ms.author: erikje
ms.custom: include file
ms.openlocfilehash: 1073a38da8a5b2467b1ff8c97b32b93f92e34e4c
ms.sourcegitcommit: f90cba0b2c2672ea733052269bcc372a80772945
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/31/2019
ms.locfileid: "66454139"
---
這些注意事項提供可協助您針對未來的 Intune 變更與功能進行準備的重要資訊。 

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

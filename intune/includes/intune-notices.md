---
title: 包含檔案
description: 包含檔案
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: include
ms.date: 03/28/2019
ms.author: erikje
ms.custom: include file
ms.openlocfilehash: 073115d33f9a4f22fe3706ef15860c2a8d8a68ee
ms.sourcegitcommit: 69aaf89140f82f344404e75a69dc59d8a1585b10
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 03/30/2019
ms.locfileid: "58675488"
---
這些注意事項提供重要資訊，可協助您做好未來的 Intune 變更與功能。 

### <a name="change-in-enrollment-workflow-with-intune-company-portal-on-corporate-ios-devices-authenticating-with-setup-assistant----1927359---"></a>在註冊工作流程使用設定助理進行驗證的公司的 iOS 裝置上 Intune 公司入口網站中變更 <!-- 1927359 -->
註冊 iOS 裝置，透過 Apple 的公司裝置註冊方法-Apple Configurator、 Apple 商務管理員 」、 Apple School Manager 或 Apple 裝置註冊方案 (DEP)，其中的工作流程中即將變更時則使用安裝程式適用於驗證的小幫手。 這項變更僅適用於具有使用者親和性註冊的裝置。

#### <a name="how-does-this-affect-me"></a>此變更對我造成什麼影響？
當此變更在 ~~3 月~~ 4 月推出時，位於 Azure 入口網站上 Intune 中的註冊設定檔將會更新，如此您就能指定裝置的驗證方式，以及它們是否會收到公司入口網站應用程式。 將會有改進的工作流程來註冊 iOS 裝置，透過上面所列的方法。 

- 當註冊新的裝置，以及使用設定助理進行驗證，您可以選擇要自動部署公司入口網站應用程式。 使用者不會再看到 」 識別您的裝置 」 畫面與 [確認您的裝置] 畫面中註冊流程。  
- 在裝置上已透過設定助理註冊，透過 Apple 的公司裝置註冊方法之一，您必須採取動作，如果您想要啟用條件式存取。 您必須使用特定的 xml，到推播到這些裝置的公司入口網站中設定應用程式設定原則。 若要執行這項操作的指示位於部落格文章的額外資訊連結。 如果您選擇將公司入口網站推送以這種方式，使用者將無法再看到 」 識別您的裝置 」 畫面與 [確認您的裝置] 畫面中註冊流程。 
- 這項變更推出，如果您尚未部署公司入口網站之後，前面所提到的應用程式組態設定檔和使用者下載公司入口網站應用程式，從應用程式存放區，他們可以登入，但它們將會收到錯誤訊息。 他們將無法使用條件式存取應用程式。 

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>我需要為這項變更做什麼準備？
如果您打算使用修改過的工作流程，您會想要更新您的終端使用者指南，以表示：

- 終端使用者將無法再看到註冊流程中所述的兩個畫面。 
- 他們必須登入公司入口網站時就會自動部署並不從 app store 下載。 

您可以選擇立即建立應用程式設定原則，如有需要在這項變更的準備。 當這個新的工作流程推出時，您會看到在主控台中更新的註冊設定檔。 我們也會通知您訊息中心透過本次首度發行。 在此之後，您必須採取的動作，讓您的終端使用者可以透過 DEP 註冊方法使用設定助理進行驗證，您可以使用公司入口網站的條件式存取。

支援部落格文章的其他資訊連結，如需有關這項變更的詳細資訊，請參閱。

#### <a name="additional-information"></a>其他資訊 
[https://aka.ms/enrollment_setup_assistant](https://aka.ms/enrollment_setup_assistant)

### <a name="plan-for-change-user-experience-update-to-intune-company-portal-app-for-ios"></a>規劃變更：iOS 版 Intune 公司入口網站應用程式的使用者體驗更新
很高興宣布 Intune 很快就會發佈主要使用者體驗更新到 iOS 公司入口網站應用程式。 該更新包括重新設計的首頁視覺呈現，以及進階篩選和更快的應用程式與書籍存取速度。

#### <a name="how-does-this-affect-me"></a>此變更對我造成什麼影響？
這個使用者體驗更新 (維持了目前的 iOS 公司入口網站功能) 包含：
- 具有原生 iOS 外觀和感覺的首頁 
- 內容清單以及搜尋篩選功能，包括依內容類型 (應用程式或電子書) 篩選的功能，以及可用性 (需要裝置管理或不需註冊即會提供)
- 搜尋電子書的功能
- 應用程式和電子書的搜尋歷程記錄

若您已加入 Apple TestFlight 計畫，當發行前版本的 Intune 已更新 iOS 公司入口網站應用程式推出時，您將會收到通知。 若您未加入 Apple TestFlight 計畫，現在註冊不會太晚。 註冊可讓您在使用者可使用已更新的公司入口網站應用程式之前先行使用。 您也可以提供直接與 Intune 小組的意見反應。  

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>我該如何為此變更做準備？
您不需要採取任何動作，這些變更將會在即將推出的 iOS CP 應用程式版本中發行。 

#### <a name="additional-information"></a>其他資訊
[https://aka.ms/cp_update_iOS](https://aka.ms/cp_update_iOS)

### <a name="check-your-delay-visibility-of-software-updates-setting-in-intune"></a>請檢查您在 Intune 中的 「 延遲可視性的軟體更新 」 設定 

我們告訴大家在 MC171466，我們已在主控台中四處移動的一些設定。 Intune 年 3 月更新，我們將會完全移除 延遲可見性的軟體更新 設定 iOS 更新原則 刀鋒視窗。 這不會變更您的已排程的軟體更新套用的方式，但它可能會影響終端使用者的可見性的更新延遲的時間長度。 您可能需要採取動作，年 3 月結束之前，如果您使用此設定。 

#### <a name="how-does-this-affect-me"></a>此變更對我造成什麼影響？
2 月 Intune 服務更新之後，您會發現設定會顯示在主控台中，並在 iOS 中的裝置限制設定檔中更新的軟體更新刀鋒視窗中的原則。 當您看到這項變更反映在主控台中時，以下是您可能需要執行。

- 適用於 iOS 的現有更新原則： 如果您有自訂設定此設定為非預設值 30 天內，而且想繼續年 3 月結束後所套用的延遲可見性設定的現有組態，您必須建立新的iOS 裝置限制設定檔。 在這裡，延遲可見性設定需要擁有相同的值與現有的 iOS 更新原則，並設為目標的相同的群組。 年 3 月服務更新之後，您將不再能夠編輯現有的 iOS 更新原則在此設定的值，因為它將不再顯示此刀鋒視窗中。 您會改為在新的設定檔中設定這項設定。
  如果您可以延遲指定天數的值不符合自訂設定的設定值，設定將無法運作，延遲可見性的兩個位置中的可見性和終端使用者會看到更新在其裝置上為可用。 因為 [軟體更新原則] 刀鋒視窗中的其他設定一律已優先順序高於此設定，在主控台中，這可能會有對大多數客戶的影響降到最低。
- 適用於 iOS 的新更新原則： 如果您嘗試在 [軟體更新] 刀鋒視窗中建立新的原則，Intune 年 2 月服務更新之後，您會看到這項設定灰色。您會看到在主控台中將您重新導向至 [裝置設定] 刀鋒視窗如果您想要延遲更新的可見性附註。

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>我該如何為此變更做準備？
您不需要採取動作，如果您不使用此設定，或不想要延遲到使用者的可見性的軟體更新。

如果您想要延遲更新的可見性，開始設定裝置的限制下的 [裝置設定] 刀鋒視窗中的新設定檔中的設定 > 一般。 如果您有此設定自訂設定中現有的 iOS 更新原則、 建立新的對等的裝置限制設定檔具有相同的值為 「 天 」 要延遲更新您的使用者的可見性、 2 月更新之前年 3 月更新後的首度發行。 

您可能想要更新您 IT 專業人員的指引，並通知技術服務人員。

支援部落格文章的其他資訊，如需有關如何設定此設定，請參閱。

#### <a name="additional-information"></a>其他資訊 
[https://aka.ms/Delay_visibility_setting_iOS](https://aka.ms/Delay_visibility_setting_iOS)

### <a name="plan-for-change-upcoming-fix-for-windows-10-email-profiles-in-intune---3904031--"></a>為變更做規劃： Windows 10 在 Intune 中的電子郵件設定檔的近期修正 <!--3904031-->
我們正在更新 Intune 寫入至 Intune 服務，以修正 bug 以及，並確保您的電子郵件設定檔繼續努力在未來版本的 Windows 10 更新的適用於 Windows 10 年 4 月中的設定檔的電子郵件的方式。 沒有您需要在部署此修正程式之後所採取的動作。

#### <a name="how-does-this-affect-me"></a>此變更對我造成什麼影響？
這項變更會影響您如果使用 Windows 10 使用的電子郵件設定檔
- 在 Windows 10 桌上型電腦上的原生郵件用戶端或
- 在 Windows 10 行動裝置上的 Outlook 電子郵件用戶端

這會影響這兩個 Intune 獨立和混合式行動裝置管理 (MDM) 的客戶。

4 月更新推出之後，您必須重新建立這些設定檔，在 Intune 主控台中 （在 Configuration Manager 系統管理員主控台中如果您使用混合式 MDM）。

如果您未採取任何動作，以下是您會看到年 4 月更新之前建立的設定檔：

- 現有的電子郵件設定檔會顯示在 Intune 主控台或 Configuration Manager 系統管理員主控台中的錯誤狀態，但使用者仍然可以存取電子郵件。 不過，後續的 Windows 更新的首度發行之後，這些設定檔將無法運作。 這些設定檔的目標裝置上的終端使用者將無法存取電子郵件。
- 之後年 4 月將不會反映在對這些設定檔編輯目標裝置。
- 選擇性抹除移除這些設定檔，即使在修正程式在 4 月推出後，將無法運作。

如果您採取的動作，然後重新建立電子郵件設定檔，使用者必須進行類似的步驟，第一次部署電子郵件設定檔時。 其電子郵件將會封鎖，直到它們接受更新適用於新的設定檔同步處理。

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>我需要為這項變更做什麼準備？
您需要在 4 月更新推出修正之後，才採取動作。 我們會連到您透過訊息中心時，即可開始來重新建立您在 Intune 中的設定檔，這項變更會上線。

如果您在 Intune 中使用 Windows 10 的電子郵件設定檔，您必須採取下列步驟：

1. 擷取現有的 Win 10 設定檔設定
2. 取消指派及/或刪除現有的設定檔
3. 建立新的設定檔使用擷取的設定，並將新的設定檔指派給相同的群組

您可能需要通知使用者，並讓技術服務人員知道這項變更。 請參閱錯誤詳細資料和重新建立這些設定檔的指示的其他資訊的支援 」 的部落格文章。

#### <a name="additional-information"></a>其他資訊
https://aka.ms/Win10EmailProfiles


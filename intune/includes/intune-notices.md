---
ms.openlocfilehash: dc86f2c22410236368753acd4dd3b66698037241
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57736847"
---

這些注意事項提供重要資訊，可協助您做好未來的 Intune 變更與功能。 

### <a name="change-in-enrollment-workflow-with-intune-company-portal-on-corporate-ios-devices-authenticating-with-setup-assistant----1927359---"></a>在註冊工作流程使用設定助理進行驗證的公司的 iOS 裝置上 Intune 公司入口網站中變更 <!-- 1927359 -->
註冊 iOS 裝置，透過 Apple 的公司裝置註冊方法-Apple Configurator、 Apple 商務管理員 」、 Apple School Manager 或 Apple 裝置註冊方案 (DEP)，其中的工作流程中即將變更時則使用安裝程式適用於驗證的小幫手。 這項變更僅適用於具有使用者親和性註冊的裝置。

#### <a name="how-does-this-affect-me"></a>此變更對我造成什麼影響？
當此變更在 ~~3 月~~ 4 月推出時，位於 Azure 入口網站上 Intune 中的註冊設定檔將會更新，如此您就能指定裝置的驗證方式，以及它們是否會收到公司入口網站應用程式。 將會有改進的工作流程來註冊 iOS 裝置，透過上面所列的方法。 注意：

- 當註冊新的裝置，以及使用設定助理進行驗證，您可以選擇要自動部署公司入口網站應用程式。 使用者不會再看到 」 識別您的裝置 」 畫面與 [確認您的裝置] 畫面中註冊流程。  
- 在裝置上已透過設定助理註冊，透過 Apple 的公司裝置註冊方法之一，您必須採取動作，如果您想要啟用條件式存取。 您必須使用特定的 xml，到推播到這些裝置的公司入口網站中設定應用程式設定原則。 若要執行這項操作的指示位於部落格文章的額外資訊連結。 如果您選擇將公司入口網站推送以這種方式，使用者將無法再看到 」 識別您的裝置 」 畫面與 [確認您的裝置] 畫面中註冊流程。 
- 這項變更推出，如果您尚未部署公司入口網站之後，前面所提到的應用程式組態設定檔和使用者下載公司入口網站應用程式，從應用程式存放區，將登入，但它們將會收到錯誤訊息。 他們將無法使用條件式存取應用程式。 

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>我需要為這項變更做什麼準備？
如果您打算使用修改過的工作流程，您會想要更新您的終端使用者指南，以表示：

- 終端使用者將無法再看到註冊流程中所述的兩個畫面。 
- 他們必須登入公司入口網站時就會自動部署並不從 app store 下載。 

您可以選擇立即建立應用程式設定原則，如有需要在這項變更的準備。 當這個新的工作流程推出時，您會看到在主控台中更新的註冊設定檔。 我們也會通知您訊息中心透過本次首度發行。 在此之後，您必須採取的動作，讓您的終端使用者可以透過 DEP 註冊方法使用設定助理進行驗證，您可以使用公司入口網站的條件式存取。

支援部落格文章的其他資訊連結，如需有關這項變更的詳細資訊，請參閱。

#### <a name="additional-information"></a>其他資訊 
[https://aka.ms/enrollment_setup_assistant](https://aka.ms/enrollment_setup_assistant)


### <a name="company-portal-changes-for-ios-122-enrollment-in-intune"></a>在 Intune 中 iOS 12.2 註冊的公司入口網站變更
根據我們在 MC172534 中的分享，Apple 已宣告與在行動裝置管理 (MDM) 服務中註冊 iOS 裝置相關的一些變更。 變更可能會看到在 2019 年 3 月中的 iOS 版本，以及所有未來的 iOS 版本。 我們將某些更新在公司入口網站中，以反映 Apple 的變更。 
 
#### <a name="how-does-this-affect-me"></a>此變更對我造成什麼影響？
如果您的終端使用者將裝置升級至 iOS 12.2 和更新版本，知道有修改過的工作流程，而且它們必須採取額外步驟要完成註冊到 Intune。 年 3 月更新之後到 Intune，以下是將執行的動作-  

- 開始註冊程序，在公司入口網站應用程式中，若要下載管理設定檔
- 移至 設定 > 一般 > 設定檔並尋找紅色徽章通知
- 選取正確的設定檔，然後逐一點選以安裝
- 回到 公司入口網站，以完成註冊

如需註冊流程的詳細資訊，按一下 其他資訊。

除非他們正在取消註冊，且需要最新的註冊，裝置已註冊並升級至 iOS 12.2 和更新版本應該不會受到影響。 Apple 將不會在此新版本中變更執行 iOS 12.1 或舊版裝置上的註冊體驗。 透過一或 Apple 的公司註冊方法 （裝置註冊計劃、 Apple School Manager 或 Apple 商務經理人） 註冊的裝置不會受到影響。

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>我該如何為此變更做準備？
您應該規劃升級文件和終端使用者指引。 您也可能需要讓技術服務人員知道這些變更。 我們會持續通知您認識我們新的頁面時，這項變更會即時收到通知。 

如果您想要善用我們導入的公司入口網站變更，要求使用者之後 3 月更新至 Intune 服務時，就將其裝置更新為新的 iOS 版公司入口網站應用程式版本 3.9.0。 會被釋放。

針對支援部落格文章中的公司入口網站變更預覽螢幕擷取畫面，按一下 其他資訊。

其他資訊 [https://aka.ms/CP_changes_iOS12](https://aka.ms/CP_changes_iOS12)

### <a name="plan-for-change-workflow-changes-for-ios-12-enrollment-in-intune"></a>為變更做規劃： 在 Intune 中 iOS 12 註冊的工作流程變更
Apple 已宣告與在行動裝置管理 (MDM) 服務中註冊 iOS 裝置相關的一些變更。 該變更可能會出現在 iOS 的 2019 年春季版，以及所有未來的 iOS 版本。

#### <a name="how-does-this-affect-me"></a>此變更對我造成什麼影響？
如果您的終端使用者在春季將其裝置升級為此新版 iOS 12，請注意工作流程會有所修改，因此使用者必須採取其他步驟來完成在 Intune 中註冊。 當 Apple 引進了下列變更時，使用者必須：

- 開始註冊程序，在公司入口網站應用程式中，若要下載管理設定檔
- 移至 設定 > 一般 > 設定檔
- 選取正確的設定檔，然後逐一點選以安裝
- 回到 公司入口網站，以完成註冊 

已註冊並升級為新版 iOS 的裝置除非取消註冊，否則不應該會受到影響，且取消註冊後需要重新註冊。

Apple 將不會在此新版本中變更執行 iOS 12.1 或舊版裝置上的註冊體驗。

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>我該如何為此變更做準備？
您應該規劃升級文件和終端使用者指引。 您也可能需要讓技術服務人員知道這些變更。 我們將透過訊息中心和「新功能」頁面，讓您隨時掌握這項變更何時生效。

#### <a name="additional-information"></a>其他資訊
[支援部落格文章中螢幕擷取畫面和影片的預期的註冊流程](https://aka.ms/iOS_enrollment_changes)。

### <a name="plan-for-change-user-experience-update-to-intune-company-portal-app-for-ios"></a>規劃變更：iOS 版 Intune 公司入口網站應用程式的使用者體驗更新
很高興宣布 Intune 很快就會發佈主要使用者體驗更新到 iOS 公司入口網站應用程式。 該更新包括重新設計的首頁視覺呈現，以及進階篩選和更快的應用程式與書籍存取速度。

#### <a name="how-does-this-affect-me"></a>此變更對我造成什麼影響？
這個使用者體驗更新 (維持了目前的 iOS 公司入口網站功能) 包含：
- 具有原生 iOS 外觀和感覺的首頁 
- 內容清單以及搜尋篩選功能，包括依內容類型 (應用程式或電子書) 篩選的功能，以及可用性 (需要裝置管理或不需註冊即會提供)
- 搜尋電子書的功能
- 應用程式和電子書的搜尋歷程記錄

若您已加入 Apple TestFlight 計畫，當發行前版本的 Intune 已更新 iOS 公司入口網站應用程式推出時，您將會收到通知。 若您未加入 Apple TestFlight 計畫，現在註冊不會太晚。 註冊可讓您在使用者可使用已更新的公司入口網站應用程式之前先行使用。 您將可以也提供直接與 Intune 小組的意見反應。  

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>我該如何為此變更做準備？
您不需要採取任何動作，這些變更將會在即將推出的 iOS CP 應用程式版本中發行。 

#### <a name="additional-information"></a>其他資訊
[https://aka.ms/cp_update_iOS](https://aka.ms/cp_update_iOS)


### <a name="reminder-removal-of-existing-exchange-online-to-intune-connectors----3105122---"></a>提醒： 移除的 現有 Exchange Online Intune 連接器 <!-- 3105122 -->
MC165575，在我們告訴大家，我們會移除 Exchange Online Intune '服務對服務' 連接器功能在未來更新中。 2 月版更新至 Intune 服務中，我們將停用按鈕，以設定新的連接器。 我們打算在 2019 年 3 月中移除所有現有 Exchange Online Intune 連接器。
 
#### <a name="how-does-this-affect-me"></a>此變更對我造成什麼影響？
您之所以接收到此訊息的原因，是因為我們的記錄顯示您可能正在您的環境中使用「服務對服務」連接器功能。 「服務對服務」連接器支援對適用於 Exchange Online 的 Exchange Active Sync Only 裝置進行 Intune 管理，但不支援內部部署基礎結構。 此連接器在主控台上的顯示方式，會讓人認為它是條件式存取 (CA) 的必要項目，但事實上 CA 並不需要它。 您可能已使用此連接器來了解使用 Exchange Online，再套用條件式存取。 Microsoft 365 系統管理中心已提供這項資訊。 您可以在這裡，找到正用於 7 到 180 天的 Exchange Online 包括應用程式類型，提供使用情況報告。 如需詳細資訊，請參閱[在系統管理中心-電子郵件應用程式使用 Office 365 報表](https://docs.microsoft.com/office365/admin/activity-reports/email-apps-usage?view=o365-worldwide)。  
 
如果您在您的環境中使用此連接器，在我們於 2 月停用連接器之後，您將無法在 Intune 中監視或抹除 Exchange Active Sync Only 裝置。 此變更期間預期不會對您的終端使用者造成任何影響。
 
#### <a name="what-can-i-do-to-prepare-for-this-change"></a>我該如何為此變更做準備？
如果您已設定服務對服務連接器，並具有 Exchange Active Sync Only 裝置，請切換成其他方法以管理您的裝置。 下列選項可供您選擇：

- 在行動裝置管理 (MDM) 中註冊裝置 
- 使用 Intune 應用程式防護原則來管理裝置 
- 使用在[這裡](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/clients-and-mobile-in-exchange-online)的文件中所概述的 Exchange 控制項 

#### <a name="additional-information"></a>其他資訊  
https://docs.microsoft.com/intune/exchange-service-connector-configure




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

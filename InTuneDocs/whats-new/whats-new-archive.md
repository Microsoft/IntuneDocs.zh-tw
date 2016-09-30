---
title: "「新功能」封存 | Microsoft Intune"
description: 
keywords: 
author: barlanmsft
manager: angrobe
ms.date: 07/18/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ed2db991-4729-49a7-a1e6-be2ffa0d03d1
ROBOTS: noindex,nofollow
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ecf43b38e9593375981770583220d4ce2dfd709f
ms.openlocfilehash: 8b0f393da727b433a926e780d6de42cf7b4c6034


---
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



## 2015 年 9 月
### 行動裝置與應用程式管理更新
**所有 Intune iOS 管理功能現在支援 iOS 9** 如需 iOS 9 管理功能的詳細資訊，請參閱[這篇部落格文章](http://blogs.technet.com/b/microsoftintune/archive/2015/09/09/day-zero-support-for-ios-9-with-intune.aspx)。

**新的 iOS 行動應用程式設定原則** 您可以使用新的行動應用程式設定原則，自動提供 iOS 應用程式執行時可能需要的設定。 例如，您可以提供網路連接埠或使用者名稱。 如需詳細資訊，請參閱[在 Microsoft Intune 中使用行動裝置應用程式組態原則設定應用程式](https://technet.microsoft.com/library/mt481447.aspx)。

**讓 iOS 9 使用者更輕鬆地管理應用程式**
 在本版中，您可以將 Intune 所管理的已部署應用程式提供給 iOS 9 使用者。 若是舊版 iOS，當您要部署應用程式且裝置上已安裝該應用程式未受管理的版本時，仍然必須要求使用者先手動解除安裝應用程式，Intune 才可安裝受管理的應用程式。

 但從本版本的 Intune 開始，您現在可以提示 iOS 9 裝置的使用者允許 Intune 接管應用程式的管理，並套用任何相關的行動應用程式管理原則。

 **Windows 10 管理** 您可以使用新的 [Windows 10 一般組態原則](https://technet.microsoft.com/library/mt404697.aspx)，為執行 Windows 10 和 Windows 10 行動裝置版的已註冊裝置，設定密碼、裝置、瀏覽器和其他設定。

 **建立應用程式並部署到已註冊的 Windows 10 裝置** 透過 MDM 的 Windows Installer (&#42;.msi) 是新的軟體安裝程式類型，可讓您建立 Windows Installer 應用程式並部署到執行 Windows 10 的已註冊裝置。 如需詳細資訊，請參閱[開始使用 Microsoft Intune 部署應用程式](https://technet.microsoft.com/library/dn646955.aspx)。

### 變更並新新 Microsoft 公司入口網站應用程式
本版公司入口網站應用程式的變更如下：

**iOS**
* Microsoft 會自動收集有關公司入口網站效能和使用的匿名資料，以改善 Microsoft 產品和服務。 使用者可以使用裝置上的使用狀況資料設定來關閉資料收集，但系統管理員無法控制資料收集，也無法變更使用者在這項設定中的選取項目。
* iPhone 6 及更新版本的全螢幕解析度支援
* 修正 Bug 以提升安全性

### Intune 文件的新內容 -- 2015 年 9 月
**新增主題**

|Name|詳細資料|
|----|--------|
|[Microsoft Intune 的 Windows 10 組態原則設定](https://technet.microsoft.com/library/mt404697.aspx)|這是新的組態原則，可讓您管理執行 Windows 10 和 Windows 10 行動裝置版之裝置上的設定和功能。
| [在 Microsoft Intune 中使用行動裝置應用程式組態原則設定應用程式](https://technet.microsoft.com/library/mt481447.aspx)|這是新的原則類型，可讓您自動提供使用者執行 iOS 應用程式時可能需要的設定。 |

**更新的主題**

|Name|詳細資料|
|----|-------|
|[利用 Microsoft Intune，使用原則管理電腦和行動裝置](https://technet.microsoft.com/library/dn743712.aspx)|已更新並包含最新資訊，以協助您了解及建立原則。|

## 2015 年 8 月
### 行動裝置與應用程式管理更新
* Intune 註冊與公司存取的 **條款和條件** [現在透過原則來管理](https://technet.microsoft.com/library/mt405893.aspx)。 您可以設定不同的條款和條件組合，以符合特定使用者群組需求。 例如，您可以部署不同語言的條款和條件，以依照地理位置來定義使用者群組。 您也可以 [編輯您的條款和條件](https://technet.microsoft.com/library/mt405893.aspx#BKMK_TCVers) ，以及指定是否要遞增版本號碼，並要求使用者同意新的條款和條件才能使用公司入口網站。
* **已重新命名一些 Intune 原則** ，使其在產品內更一致，並讓您更容易找到。 如需所有可用 Intune 原則的清單，請參閱[利用 Microsoft Intune，使用原則管理電腦和行動裝置](https://technet.microsoft.com/library/dn743712.aspx)。
* **PKCS #12 (.PFX) 憑證設定檔** 適用於 Android 4.0 或更新版本以及 Windows 10 (Desktop 和行動裝置版) 及更新版本。 使用 .PFX 不需要 NDES 伺服器。 若要了解如何使用 .PFX 憑證設定檔，請參閱[透過 Microsoft Intune 利用憑證設定檔存取公司資源](http://technet.microsoft.com/library/dn818904.aspx)。
* **適用於 Windows 10 Desktop 和行動公司界限設定** 能夠進行細緻的 VPN 設定，如[協助使用者搭配使用 VPN 設定檔與 Microsoft Intune 來連線到工作](https://technet.microsoft.com/library/dn818905.aspx)中所述。
* **Android 的 OneDrive App 現在支援多重身分識別**。  [您可以管理的 Microsoft 應用程式清單](https://technet.microsoft.com/library/dn708489.aspx)中描述這項更新和行動裝置應用程式管理原則的其他更新。
* **iOS 啟用鎖定略過**。 如果屬公司所擁有的 iOS 裝置受到啟用鎖定的保護，您必須輸入使用者的 Apple ID 和密碼，才能清除或重新啟動裝置。 當使用者離職並歸還屬公司所擁有的裝置時，如果未關閉啟用鎖定，可能會是項挑戰。 為了協助解決這個問題，您可以使用 [Intune 啟用鎖定略過](https://technet.microsoft.com/library/mt414176.aspx)。

### 電腦的條件存取
您現在可以設定電腦的條件式存取原則。 這可讓 Office 桌面應用程式存取 Exchange Online 和 SharePoint Online 服務。
若要啟用電腦的條件存取原則，此電腦必須加入網域或相容。
* 如需啟用電腦條件式存取需求的完整清單，請參閱[使用 Microsoft Intune 管理電子郵件和 SharePoint 的存取](http://technet.microsoft.com/library/dn818907).aspx) 的 **開始使用** 一節。
* 如需啟用電子郵件存取之條件式存取可以設定的選項，請參閱[使用 Microsoft Intune 管理電子郵件存取](https://technet.microsoft.com/library/dn705841.aspx)。
* 如需啟用 SharePoint Online 之條件式存取可以設定的選項，請參閱[以 Microsoft Intune 管理 SharePoint Online 存取](https://technet.microsoft.com/library/dn705844.aspx)。

### 變更並新新 Microsoft 公司入口網站應用程式
本版公司入口網站應用程式的變更如下：

**Android**

如果使用者尚未註冊要管理的裝置，則在登入後會立即看到裝置註冊指示。

### Intune 文件的新內容 -- 2015 年 8 月
**新增主題**

|標題|詳細資料|
|-----|-------|
|[使用 Microsoft Intune 的啟用鎖定略過協助保護 iOS 裝置](https://technet.microsoft.com/library/mt414176.aspx)|了解當使用者離職並歸還鎖定的裝置時，如何使用 Intune 略過 iOS 啟用鎖定。|

**更新的主題**

|標題|詳細資料|
|-----|-------|
|[可與 Microsoft Intune 行動應用程式管理原則搭配使用的 Microsoft 應用程式](https://technet.microsoft.com/library/dn708489.aspx)|更新有關可以使用行動應用程式管理原則管理之應用程式的最新資訊。
|[利用 Microsoft Intune，使用原則管理電腦和行動裝置](http://technet.microsoft.com/library/dn743712.aspx)|更新 Intune 新增的最新原則。|
<!---
## July 2015
July updates for Intune are limited to behind-the-scenes enhancements that allow us to continue providing you with a high-quality service experience. New features are not included in this service update.

### Intune Onboarding benefit
Microsoft offers the Intune Onboarding benefit for eligible plans. The Onboarding benefit lets you work remotely with Microsoft specialists to get your Intune environment ready for use. For more information, see [Microsoft Intune Onboarding benefit description](https://technet.microsoft.com/library/mt228266.aspx)
### Changes and updates to Microsoft Company Portal apps
The following changes have been made to the company portal apps in this release.

**Android**

Microsoft automatically collects anonymous data about the performance and use of the company portal to improve Microsoft products and services. End users can turn off data collection by using the Usage Data setting on their device, but administrators have no control over the data collection and cannot change the end user’s selection for this setting.--->



<!--HONumber=Sep16_HO5-->



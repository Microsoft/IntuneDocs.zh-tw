---
title: "iOS 的 Intune 裝置限制設定"
titleSuffix: Intune Azure preview
description: "Intune Azure 預覽版︰了解 iOS 裝置上可用以控制裝置設定與功能的 Intune 設定。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 73590192-54ca-4833-9f1d-83e1b654399f
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 153cce3809e24303b8f88a833e2fc7bdd9428a4a
ms.openlocfilehash: a062b92cba0042153ffe22b949ce8a3b7b740b3f
ms.lasthandoff: 02/18/2017


---

# <a name="ios-device-restriction-settings-in-microsoft-intune"></a>Microsoft Intune 中的 iOS 裝置限制設定

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

## <a name="general"></a>一般
-     **相機** - 指定是否可以使用裝置上的相機。     
-     **診斷資料提交** - 允許或封鎖裝置提交診斷資料給 Apple。
-     **FaceTime** -允許在裝置上使用 FaceTime 應用程式。
-     **螢幕擷取** - 允許使用者可擷取螢幕內容做成影像。
-     **Siri** - 允許在裝置上使用 Siri 語音助理。
    -     **在鎖定裝置時使用 Siri** - 允許裝置在鎖定的情況下使用 Siri 語音助理。
    -     **Siri 不雅內容篩選 (僅限受監督)** - 讓 Siri 不會聽寫出或說出不雅字眼。
    -     **Siri 從網際網路查詢使用者產生的內容 (僅限受監督)** - 允許 Siri 存取網站來回答問題。
-     **不信任的 TLS 憑證** - 在裝置上允許不信任傳輸層安全性憑證。
-     **在鎖定裝置時存取控制中心** - 允許使用者在裝置鎖定時存取控制中心應用程式。
-     **鎖定裝置時通知** - 允許使用者在未解除鎖定裝置的情況下，存取通知檢視。
-     **在鎖定裝置時使用 Passbook** - 允許使用者在鎖定裝置時存取 Passbook 應用程式。
-     **在鎖定裝置時使用今日檢視** - 允許使用者在鎖定裝置時可以看到今日檢視。
-     **企業應用程式信任** - 讓使用者選擇信任不是從應用程式市集下載的應用程式。
-     **AirDrop (僅限受監督)** - 允許使用 AirDrop 功能與鄰近裝置交換內容。
-     **Spotlight 搜尋傳回網際網路上的結果 (僅限受監督)** - 讓 Spotlight 搜尋連線至網際網路，以提供進一步的結果。
-     **字組定義查閱 (僅限受監督)** - 允許可讓您反白字組並查詢其定義的 iOS 功能。
-     **預測鍵盤 (僅限受監督)** - 允許使用預測鍵盤，以建議使用者可能想要使用的字組。
-     **自動校正 (僅限受監督)** - 讓裝置自動校正拼字錯誤的字組。
-     **鍵盤拼字檢查 (僅限受監督)** - 允許在裝置進行拼字檢查程式。
-     **鍵盤快速鍵 (僅限受監督)** - 允許使用鍵盤快速鍵。
-     **已配對之 Apple Watch 的手腕偵測** - 啟用時，Apple Watch 就不會在穿戴期間顯示通知。
- **需要 AirPlay 連出要求配對密碼** - 使用者在使用 AirePlay 將內容串流到其他 Apple 裝置時，需要有成對的密碼。
- **帳戶修改 (僅限受監督)** - 允許使用者變更帳戶設定，例如電子郵件設定。
- **Apple Watch 配對 (僅限受監督)** - 允許裝置與 Apple Watch 配對。
- **修改藍牙 (僅限受監督)** - 封鎖使用者變更藍牙裝置上的設定。
- **Classroom 應用程式的遠端螢幕觀察 (僅限受監督)** - 從觀察遠端裝置上的畫面來允許或封鎖 Classroom 應用程式。
- **啟用裝置設定的限制 (僅限受監督)** - 允許使用者在裝置上設定裝置限制 (家長監護)。
- **在裝置上使用 [清除所有內容及設定] 選項 (僅限受監督)** - 允許使用者可利用清除所有內容與裝置上的設定的選項。
- **修改裝置名稱 (僅限受監督)** - 允許使用者變更裝置的名稱。
- **修改診斷提交設定 (僅限受監督)** - 允許或封鎖裝置提交診斷資料給 Apple。
- **主機配對，以控制 iOS 裝置所能配對的裝置 (僅限受監督)** - 允許主機配對，讓系統管理員可控制能與 iOS 裝置配對的裝置。
- **修改通知設定 (僅限受監督)** - 允許使用者變更裝置通知設定。
- **修改密碼 (僅限受監督)** - 允許新增、變更或移除裝置密碼。
- **修改背景圖片 (僅限受監督)** - 允許使用者變更裝置的背景圖案。
- **修改企業應用程式信任設定 (僅限受監督)** - 讓使用者能選擇信任不是從應用程式市集下載的應用程式。
- **從應用程式市集下載應用程式 (僅限受監督)** - 允許裝置可存取應用程式市集，以及安裝應用程式。
- **「尋找我的朋友」應用程式設定的變更 (僅限受監督)** - 允許使用者可變更「尋找我的朋友」應用程式之設定。
- **iBooks Store (僅限受監督)** - 允許使用者在 iBooks Store 瀏覽及購買書籍。
- **裝置上的「訊息」應用程式 (僅限受監督)** - 允許使用傳送及讀取簡訊的「訊息」應用程式。
- **Podcasts (僅限受監督)** - 允許使用 Podcasts 應用程式。
- **音樂服務 (僅限受監督)** - 允許使用 Apple「音樂」應用程式。
- **iTunes Radio 服務 (僅限受監督)** - 允許使用 iTunes Radio 應用程式。
- **Apple News (僅限受監督)** - 允許使用 Apple News 應用程式。
- **組態設定檔變更** - 允許使用者安裝組態設定檔。

## <a name="password"></a>密碼
-     **需要密碼** - 需要使用者輸入密碼才可存取該裝置。
-     **簡單密碼** - 允許簡單密碼，像是0000 和 1234。
-     **必要的密碼類型** - 指定需要的密碼類型，例如只可包含數字或英數字元。
-     **密碼中的非英數字元數目** - 指定密碼中必須包含的符號字元數 (例如 **#** 或 **@**)。
-     **密碼長度下限** - 指定密碼的字元數下限。
-     **登入失敗幾次後即抹除裝置** - 指定失敗的登入嘗試次數，之後這個設定即抹除裝置。
-     **在螢幕鎖定最少幾分鐘後必須輸入密碼**<sup>1</sup> - 指定裝置可閒置多久之後，使用者必須重新輸入密碼。
-     **沒有活動最久幾分鐘後鎖定螢幕**<sup>1</sup> - 指定裝置顯示畫面關閉之前維持開啟狀態的分鐘數。
-     **密碼到期 (天數)** - 指定多少天後必須變更裝置密碼。
-     **避免重複使用以前用過的密碼** - 指定裝置記憶先前使用過的密碼數目。
-     **指紋解除鎖定** - 允許使用指紋來解除鎖定相容的裝置。

<sup>1</sup>當您設定 [沒有活動最久幾分鐘後鎖定螢幕] 的設定以及 [在螢幕鎖定最少幾分鐘後必須輸入密碼] 時，它們會依序套用。 例如，若您設定將兩項全都設定為 **5** 分鐘，螢幕將會自動在 5 分鐘後關閉，裝置將會在另一個 5 分鐘之後鎖定。 但使用者若是手動關閉螢幕，便會立即套用第二項設定。 在同一範例中，當使用者關閉螢幕之後，裝置將會在 5 分鐘後鎖定。

## <a name="app-store-doc-viewing-gaming"></a>App Store、文件檢視、遊戲


-   **App Store (僅限受監督)** - 封鎖對受監督裝置上 App Store 的存取。
-     **存取 App Store 的密碼** - 要求使用者先輸入密碼，才可瀏覽 App Store。
-     **應用程式內購買** - 允許從執行中的應用程式進行市集購買。
-     **自動應用程式下載 (僅限受監督)** -
-     **明確的 iTunes 音樂、播客或新聞內容 (僅限監督)** - 允許裝置可從市集存取標記為成人內容的內容。
-     **從 iBook Store 下載標記為 [成人作品] 的內容** - 允許使用者下載分類為「成人作品」的書籍。
-     **在未受管理應用程式中檢視公司文件** - 允許在任何應用程式中檢視公司文件。<br>**範例︰**您想要防止使用者將檔案從 OneDrive 應用程式儲存至 Dropbox。 將此設定設定為否。 裝置收到原則後 (例如重新啟動後)，即不再允許儲存。
-     **在公司應用程式中檢視非公司文件** - 允許在公司的受管理應用程式中檢視任何文件。
-     **將 AirDrop 視為未受管理的目的地** - 停止透過從受管理應用程式傳送資料。 從 Airdrop 傳送資料。
-     **正在新增 Game Center 的朋友 (僅限監督)** - 允許使用者在 Game Center 新增朋友。
-     **Game Center (僅限受監督)** - 封鎖或啟用使用 Game Center 應用程式。
-     **多人遊戲 (僅限受監督)** - 允許使用者在裝置上玩多人遊戲。
-     **分級區域** - 為想要設定允許的下載項目選擇分級區域，然後為**電影**和**電視節目**選擇允許的分級。
-     **應用程式** - 選擇使用者可下載之應用程式的年齡分級，也可以選擇 [允許所有應用程式]。

## <a name="restricted-apps"></a>受限應用程式

您可以在受限制應用程式清單中，設定下列清單之一︰

**禁止的應用程式**清單 - 列出不允許使用者安裝與執行的應用程式 (並非由 Intune 管理)。
**核准的應用程式**清單 - 列出允許使用者安裝的應用程式。 若要保持相容，使用者絕不能安裝未列出的應用程式。 自動允許 Intune 所管理的應用程式。

若要設定清單，請按一下 [新增]，然後在應用程式市集中，指定您所選的名稱 (也可指定選用的應用程式發行者) 以及應用程式的 URL。

### <a name="how-to-specify-the-url-to-an-app-in-the-store"></a>如何在市集中指定應用程式的 URL

若要指定應用程式清單中的應用程式 URL，請使用下列格式：

使用搜尋引擎，在 iTunes App Store 中尋找您要使用的應用程式，然後開啟應用程式的頁面。
複製頁面的 URL，並使用此 URL 作為設定允許或禁止的應用程式清單之 URL，或是想要以 kiosk 模式執行的應用程式。
包含受限應用程式設定的裝置設定檔，必須部署到使用者群組。

範例：搜尋 Microsoft Word for iPad。 您要使用的 URL 是 https://itunes.apple.com/us/app/microsoft-word-for-ipad/id586447913?mt=8。

> [!Note]
> 您也可以先使用 iTunes 軟體尋找應用程式，再使用 [複製連結]  命令取得應用程式的 URL。



### <a name="additional-options"></a>其他選項

您也可以按一下 [匯入]填入格式如一下的 csv 檔案清單：<*應用程式 URL*>，<*應用程式名稱*>，<*應用程式發行者*>，或按一下 [匯出]，建立 csv 檔案，其中包含格式相同的受限應用程式清單內容。

## <a name="show-or-hide-apps"></a>顯示或隱藏應用程式

在顯示或隱藏的應用程式清單中，可以設定下列清單之一 (需要執行 iOS 9.3 或更新版本的受監督裝置)。

**隱藏的應用程式**清單 - 指定對使用者隱藏的應用程式清單。 使用者無法檢視或啟動這些應用程式。
**顯示的應用程式**清單 - 指定使用者可檢視及啟動的應用程式清單。 無法檢視或啟動其他應用程式。

若要設定清單，請按一下 [新增]，然後在應用程式市集中，指定您所選的名稱 (也可指定選用的應用程式發行者) 以及應用程式的 URL。

### <a name="how-to-specify-the-url-to-an-app-in-the-store"></a>如何在市集中指定應用程式的 URL

若要指定應用程式清單中的應用程式 URL，請使用下列格式：

使用搜尋引擎，在 iTunes App Store 中尋找您要使用的應用程式，然後開啟應用程式的頁面。
複製頁面的 URL，並使用此 URL 作為設定允許或禁止的應用程式清單之 URL，或是想要以 kiosk 模式執行的應用程式。

範例：搜尋 Microsoft Word for iPad。 您要使用的 URL 是 https://itunes.apple.com/us/app/microsoft-word-for-ipad/id586447913?mt=8。

> [!Note]
> 您也可以先使用 iTunes 軟體尋找應用程式，再使用 [複製連結]  命令取得應用程式的 URL。

### <a name="additional-options"></a>其他選項

您也可按一下 [匯入]，填入格式如下的 csv 檔案清單：<*應用程式 URL*>，<*應用程式名稱*>，<*應用程式發行者*>，或按一下 [匯出]，建立 csv 檔案，其中包含格式相同的隱藏或顯示之應用程式清單的內容。

### <a name="app-information-for-built-in-ios-apps"></a>內建 iOS 應用程式的應用程式資訊
使用此清單中的資訊來識別您可能想要顯示或隱藏之內建 iOS 應用程式的名稱、發行者及組合識別碼。 如果想要顯示或隱藏清單中的所有應用程式，可以將下列資料複製到文字檔，並使用副檔名 **.csv**，然後使用 [匯入] 選項來同時匯入所有的應用程式。


    App Store,Apple,com.apple.AppStore
    Calculator,Apple,com.apple.calculator
    Calendar,Apple,com.apple.mobilecal
    Camera,Apple,com.apple.camera
    Clock,Apple,com.apple.mobiletimer
    Compass,Apple,com.apple.compass
    Contacts,Apple,com.apple.MobileAddressBook
    FaceTime,Apple,com.apple.facetime
    Find Friends,Apple,com.apple.mobileme.fmf1
    Find iPhone,Apple,com.apple.mobileme.fmip1
    Game Center,Apple,com.apple.gamecenter
    GarageBand,Apple,com.apple.mobilegarageband
    Health,Apple,com.apple.Health
    iBooks,Apple,com.apple.iBooks
    iTunes Store,Apple,com.apple.MobileStore
    iTunes U,Apple,com.apple.itunesu
    Keynote,Apple,com.apple.Keynote
    Mail,Apple,com.apple.mobilemail
    Maps,Apple,com.apple.Maps
    Messages,Apple,com.apple.MobileSMS
    Music,Apple,com.apple.Music
    News,Apple,com.apple.news
    Notes,Apple,com.apple.mobilenotes
    Numbers,Apple,com.apple.Numbers
    Pages,Apple,com.apple.Pages
    Photo Booth,Apple,com.apple.Photo-Booth
    Photos,Apple,com.apple.mobileslideshow
    Podcasts,Apple,com.apple.podcasts
    Reminders,Apple,com.apple.reminders
    Safari,Apple,com.apple.mobilesafari
    Settings,Apple,com.apple.Preferences
    Stocks,Apple,com.apple.stocks
    Tips,Apple,com.apple.tips
    Videos,Apple,com.apple.videos
    VoiceMemos,Apple,com.apple.VoiceMemos
    Wallet,Apple,com.apple.Passbook
    Watch,Apple,com.apple.Bridge
    Weather,Apple,com.apple.weather





## <a name="cellular"></a>行動電話通訊
-     **數據漫遊** - 允許裝置在行動電話通訊網路時進行資料漫遊。
-     **漫遊時執行全域背景擷取** - 允許裝置在行動電話通訊網路漫遊時擷取資料 (例如電子郵件)。
-     **語音撥號** - 允許在裝置上使用語音撥號功能。
-     **語音漫遊** - 允許裝置在行動電話通訊網路時進行語音漫遊。
-     **應用程式行動數據使用量設定的變更 (僅限受監督)** - 允許使用者控制哪些應用程式可以使用行動數據資料。

## <a name="cloud-and-storage"></a>雲端與儲存體
-     **備份至 iCloud** - 允許使用者將裝置備份到 iCloud。
-     **文件同步至 iCloud (僅限受監督)** - 允許文件和索引鍵-值同步處理到 iCloud 儲存空間。
-     **相片串流同步至 iCloud** - 讓使用者可在其裝置上啟用 [共享相片串流]，以允許將相片同步處理到 iCloud 並可在所有使用者裝置上使用。
-     **加密備份** - 需要加密任何裝置備份。
-     **iCloud 照片圖庫** - 如果設定為 [否]，請停用 iCloud 相片圖庫，讓使用者在雲端中儲存相片和視訊。    如果這是設定為 [否]，將會從裝置中移除任何未從 iCloud 相片圖庫完整下載到裝置的相片。
-     **受管理應用程式同步至雲端** - 允許您使用 Intune 管理的應用程式將資料同步至使用者的 iCloud 帳戶。
-     **共享相片串流** - 設定為 [否]，會停用裝置上的 [iCloud 相片共享]。
-     **活動接續** - 允許使用者在另一部 iOS 或 Mac OS X 裝置上繼續執行在 iOS 裝置上啟動的工作 (遞交)。

## <a name="kiosk"></a>Kiosk
-     **啟用鎖定** - 在受監督的 iOS 裝置上將啟用鎖定啟用。
-     **kiosk 模式下執行的應用程式** - 選擇 [受管理的應用程式] 可選取已新增至 Intune 的應用程式，而選擇 [市集應用程式] 則可指定市集中應用程式的 URL。 不允許在裝置上執行其他應用程式。 如需詳細說明，請參閱本主題稍後的＜如何將 URL 指定給應用程式市集＞。
-     **輔助觸控** - 啟用或停用 [輔助觸控] 協助工具設定，協助使用者執行可能很難執行的螢幕手勢。
-     **色彩對換** - 啟用或停用 [色彩對換] 協助工具設定，以調整顯示畫面來協助視力受損的使用者。
-     **單聲道音訊** - 啟用或停用協助工具設定 [單聲道音訊]。
-     **配音** - 啟用或停用協助工具設定 [配音]，以大聲讀出裝置螢幕上的文字。
-     **縮放** - 啟用或停用 [縮放] 協助工具的設定，以讓使用者使用觸控來縮放裝置螢幕。
-     **自動鎖定** - 啟用或停用裝置的自動鎖定。
-     **響鈴切換** - 啟用或停用裝置上的響鈴 (靜音) 切換。
-     **旋轉螢幕** - 啟用或停用在使用者旋轉裝置時變更螢幕方向。
-     **螢幕睡眠按鈕** - 啟用或停用裝置上的喚醒螢幕睡眠按鈕。
-     **觸控** - 在裝置上啟用或停用觸控螢幕。
-     **音量按鈕** - 啟用或停用裝置上的音量按鈕。
-     **輔助觸控控制項** - 啟用或停用輔助觸控調整，以讓使用者調整輔助觸控功能。
-     **色彩對換控制** - 啟用或停用色彩對換調整，以讓使用者調整色彩對換功能。
-     **說出選取的文字** - 啟用或停用 [讀出選取範圍] 協助工具設定，以大聲讀出使用者選取的文字。
-     **配音控制** - 啟用或停用配音調整，以讓使用者調整配音功能 (例如，大聲讀出螢幕上文字的速度)。
-     **縮放控制** - 啟用或停用縮放調整，以讓使用者調整縮放功能。

>[!NOTE]
> 您必須先使用 Apple Configurator 工具或 Apple 裝置註冊方案，將裝置設為受監督模式，才可為 iOS 裝置設定 kiosk 模式。 如需 Apple Configurator 工具的詳細資訊，請參閱您的 Apple 文件。
>如果在部署組態原則之後安裝您指定的 iOS 應用程式，則除非重新啟動裝置，否則裝置不會進入 kiosk 模式。

## <a name="safari"></a>Safari
-     **Safari (僅限受監督)** - 指定是否可以在裝置上使用 Safari 瀏覽器。
-     **自動填滿** - 允許使用者變更瀏覽器中的自動完成設定。
-     **Cookie** - 允許瀏覽器使用 Cookie。
-     **JavaScript** - 允許在瀏覽器中執行 Java 指令碼。
-     **詐騙警告** - 允許瀏覽器中的詐騙警告。
-     **快顯** - 啟用或停用瀏覽器的快顯封鎖程式。


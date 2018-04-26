---
title: iOS 的 Microsoft Intune 裝置限制設定
titleSuffix: ''
description: 了解執行 iOS 的裝置上可用以控制裝置設定與功能的 Intune 設定。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/1/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: b810a9dd783f59e778f3ffcb40da8fa52acf70ff
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="microsoft-intune-ios-device-restriction-settings"></a>Microsoft Intune iOS 裝置限制設定

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

本文將告訴您，可以為執行 iOS 之裝置設定的 Microsoft Intune 裝置限制設定。

## <a name="general"></a>一般

-   **共用的使用方式資料** - 允許或封鎖裝置將診斷和使用方式的遙測資料傳送至 Apple。
-   **診斷資料提交** - 允許或封鎖裝置提交診斷資料給 Apple。
-   **螢幕擷取** - 允許使用者可擷取螢幕內容做成影像。
    - **Classroom 應用程式的遠端螢幕觀察 (僅限受監督)** - 允許或封鎖 Apple Classroom 應用程式檢視 iOS 裝置螢幕。
    - **Classroom 應用程式的無提示螢幕觀察 (僅限受監督)** - 如果允許，老師可以在學生不知情的情況下，使用 Classroom 應用程式以無訊息方式觀察學生的 iOS 裝置螢幕。
-   **不信任的 TLS 憑證** - 在裝置上允許不信任傳輸層安全性憑證。
-   **企業應用程式信任** - 讓使用者選擇信任不是從應用程式市集下載的應用程式。
- **帳戶修改 (僅限受監督)** - 封鎖時，這會防止使用者從 iOS 設定應用程式修改裝置特有的設定，例如建立新的裝置帳戶，以及變更使用者名稱或密碼。
這也適用於可從 iOS 設定應用程式 (例如郵件、連絡人、行事曆、Facebook 和 Twitter) 中存取的設定。 若應用程式的帳戶設定無法從 iOS 設定應用程式 (例如 Microsoft Outlook 應用程式) 加以設定，則這不適用這類應用程式。
- **啟用裝置設定的限制 (僅限受監督)** - 允許使用者在裝置上設定裝置限制 (家長監護)。
- **在裝置上使用 [清除所有內容及設定] 選項 (僅限受監督)** - 允許使用者可利用清除所有內容與裝置上的設定的選項。
- **修改裝置名稱 (僅限受監督)** - 允許使用者變更裝置的名稱。
- **修改通知設定 (僅限受監督)** - 允許使用者變更裝置通知設定。
- **修改企業應用程式信任設定 (僅限受監督)** - 讓使用者能選擇信任不是從應用程式市集下載的應用程式。
- **組態設定檔變更 (僅供監督)** - 允許使用者安裝組態設定檔。
- **啟用鎖定 (僅限受監督)** - 在受監督的 iOS 裝置上將啟用鎖定啟用。

## <a name="configurations-requiring-supervision"></a>設定需要監督

iOS 受監督模式只能透過 Apple 的裝置註冊計劃，或使用 Apple Configurator，在初始裝置安裝期間啟用。 一旦啟用受監督模式，Intune 即可設定裝置的下列功能：

- App Lock (單一應用程式模式) 
- 全域 HTTP Proxy 
- 啟用鎖定略過 
- 自發性單一應用程式模式 
- 網路內容篩選 
- 設定背景和鎖定畫面 
- 無訊息應用程式推送 
- AlwaysOn VPN 
- 只允許受管理應用程式安裝 
- iBookstore 
- iMessages 
- Game Center 
- AirDrop 
- AirPlay 
- 主機配對 
- 雲端同步 
- Spotlight 搜尋 
- 遞交 
- 清除裝置 
- 限制 UI 
- 透過 UI 安裝組態設定檔 
- 新聞 
- 鍵盤快速鍵 
- 密碼修改 
- 裝置名稱變更 
- 自動應用程式下載 
- 企業應用程式信任變更 
- Apple Music 
- 郵件放置 
- 與 Apple Watch 配對 

> [!NOTE]
> Apple 確認在 2018 年，特定設定將會移至僅受監督。 建議您在使用這些設定時考慮這點，而不是等待 Apple 將它們移轉至僅受監督：
> - 由使用者安裝應用程式
> - 應用程式移除
> - FaceTime
> - Safari
> - iTunes
> - 偏激內容
> - iCloud 文件和資料
> - 多人遊戲
> - 新增 Game Center 朋友

## <a name="password"></a>密碼
-   **密碼** - 需要使用者輸入密碼才可存取該裝置。
    -   **簡單密碼** - 允許簡單密碼，像是0000 和 1234。
    -   **必要的密碼類型** - 指定需要的密碼類型，例如只可包含數字或英數字元。
    -   **密碼中的非英數字元數目** - 指定密碼中必須包含的符號字元數 (例如 **#** 或 **@**)。
    -   **密碼長度下限** - 指定密碼的字元數下限。
    -   **登入失敗幾次後即抹除裝置** - 指定失敗的登入嘗試次數，之後這個設定即抹除裝置。
    -   **在螢幕鎖定最少幾分鐘後必須輸入密碼**<sup>1</sup> - 指定裝置可閒置多久之後，使用者必須重新輸入密碼。
    -   **沒有活動最久幾分鐘後鎖定螢幕**<sup>1</sup> - 指定裝置顯示畫面關閉之前維持開啟狀態的分鐘數。
    -   **密碼到期 (天數)** - 指定多少天後必須變更裝置密碼。
    -   **避免重複使用以前用過的密碼** - 指定裝置記憶先前使用過的密碼數目。
    -   **指紋解除鎖定** - 允許使用指紋來解除鎖定相容的裝置。
- **修改密碼 (僅限受監督)** - 防止變更、新增或移除密碼。
    - **修改指紋 (僅限受監督)** - 防止使用者變更、新增或移除 TouchID 設定。

<sup>1</sup>當您設定 [沒有活動最久幾分鐘後鎖定螢幕] 的設定以及 [在螢幕鎖定最少幾分鐘後必須輸入密碼] 時，它們會依序套用。 例如，如果您將兩個設定的值都設定為 **5** 分鐘，則會在五分鐘後自動關閉螢幕，並會在另一個五分鐘之後鎖定裝置。 但使用者若是手動關閉螢幕，便會立即套用第二項設定。 在同一範例中，當使用者關閉螢幕之後，裝置將會在五分鐘後鎖定。

## <a name="locked-screen-experience"></a>鎖定畫面體驗

-   **在鎖定裝置時存取控制中心** - 允許使用者在裝置鎖定時存取控制中心應用程式。
-   **鎖定裝置時通知** - 允許使用者在未解除鎖定裝置的情況下，存取通知檢視。
-   **在鎖定裝置時使用 Passbook** - 允許使用者在鎖定裝置時存取 Passbook 應用程式。
-   **在鎖定裝置時使用今日檢視** - 允許使用者在鎖定裝置時可以看到今日檢視。

## <a name="app-store-doc-viewing-gaming"></a>App Store、文件檢視、遊戲


-   **App Store** - 封鎖對受監督裝置上 App Store 的存取。
    - **從 App Store 安裝應用程式 (僅限受監督)** - 從裝置主畫面封鎖 App Store。 終端使用者可以繼續使用 iTunes 或 Apple Configurator 來安裝應用程式。
    - **自動應用程式下載 (僅限受監督)** - 防止將其他 iOS 裝置上購買的應用程式下載到此裝置。
-   **存取 App Store 的密碼** - 要求使用者先輸入密碼，才可瀏覽 App Store。
-   **應用程式內購買** - 允許從執行中的應用程式進行市集購買。
-   **明確的 iTunes 音樂、播客或新聞內容 (僅限監督)** - 允許裝置可從市集存取標記為成人內容的內容。
-   **從 iBook Store 下載標記為 [成人作品] 的內容** - 允許使用者下載分類為「成人作品」的書籍。
-   **在未受管理應用程式中檢視公司文件** - 允許在任何應用程式中檢視公司文件。<br>**範例︰**您想要防止使用者將檔案從 OneDrive 應用程式儲存至 Dropbox。 將此設定設定為否。 裝置收到原則後 (例如重新啟動後)，即不再允許儲存。
-   **在公司應用程式中檢視非公司文件** - 允許在公司的受管理應用程式中檢視任何文件。
-   **將 AirDrop 視為未受管理的目的地** - 停止透過從受管理應用程式傳送資料。 從 Airdrop 傳送資料。
-   **正在新增 Game Center 的朋友 (僅限監督)** - 允許使用者在 Game Center 新增朋友。
-   **Game Center (僅限受監督)** - 封鎖或啟用使用 Game Center 應用程式。
-   **多人遊戲 (僅限受監督)** - 允許使用者在裝置上玩多人遊戲。
-   **分級區域** - 為想要設定允許的下載項目選擇分級區域，然後為**電影**和**電視節目**選擇允許的分級。
-   **應用程式** - 選擇使用者可下載之應用程式的年齡分級，也可以選擇 [允許所有應用程式]。

## <a name="built-in-apps"></a>內建應用程式

-   **相機** - 指定是否可以使用裝置上的相機。
    -   **FaceTime** -允許在裝置上使用 FaceTime 應用程式。
-   **Siri** - 允許在裝置上使用 Siri 語音助理。
    -   **在鎖定裝置時使用 Siri** - 允許裝置在鎖定的情況下使用 Siri 語音助理。
    -   **Siri 不雅內容篩選 (僅限受監督)** - 讓 Siri 不會聽寫出或說出不雅字眼。
    -   **Siri 從網際網路查詢使用者產生的內容 (僅限受監督)** - 允許 Siri 存取網站來回答問題。
- **Apple News (僅限受監督)** - 允許使用 Apple News 應用程式。
- **iBooks Store (僅限受監督)** - 允許使用者在 iBooks Store 瀏覽及購買書籍。
- **裝置上的「訊息」應用程式 (僅限受監督)** - 允許使用傳送及讀取簡訊的「訊息」應用程式。
- **Podcasts (僅限受監督)** - 允許使用 Podcasts 應用程式。
- **音樂服務 (僅限受監督)** - 允許使用 Apple「音樂」應用程式。
- **iTunes Radio 服務 (僅限受監督)** - 允許使用 iTunes Radio 應用程式。
- **「尋找我的朋友」應用程式設定的變更 (僅限受監督)** - 允許使用者可變更「尋找我的朋友」應用程式之設定。
- **Spotlight 搜尋傳回網際網路上的結果 (僅限受監督)** - 讓 Spotlight 搜尋連線至網際網路，以提供進一步的結果。

## <a name="restricted-apps"></a>受限應用程式

您可以在受限制應用程式清單中，設定下列清單之一︰

- **禁止的應用程式**清單 - 列出不允許使用者安裝與執行的應用程式 (並非由 Intune 管理)。 使用者安裝禁止的應用程式並不會受到阻止，但如果已安裝，系統會向您回報。
- **核准的應用程式**清單 - 列出允許使用者安裝的應用程式。 使用者絕不能安裝未列出的應用程式。 自動允許 Intune 所管理的應用程式。 使用者安裝不在核准的清單上的應用程式並不會受到阻止，但如果已安裝，系統會向您回報。

若要設定清單，請按一下 [新增]，然後在應用程式市集中，指定您所選的名稱 (也可指定選用的應用程式發行者) 以及應用程式的 URL。

### <a name="how-to-specify-the-url-to-an-app-in-the-store"></a>如何在市集中指定應用程式的 URL

若要指定應用程式清單中的應用程式 URL，請使用下列格式：

使用搜尋引擎，在 iTunes App Store 中尋找您要使用的應用程式，然後開啟應用程式的頁面。
複製頁面的 URL，並使用此 URL 作為設定允許或禁止的應用程式清單之 URL，或是想要以 kiosk 模式執行的應用程式。
包含受限應用程式設定的裝置設定檔，必須指派給使用者群組。

範例：搜尋 Microsoft Word for iPad。 您使用的 URL 是 https://itunes.apple.com/us/app/microsoft-word-for-ipad/id586447913?mt=8。

> [!Note]
> 您也可以先使用 iTunes 尋找應用程式，再使用**複製連結**命令取得應用程式的 URL。

### <a name="additional-options"></a>其他選項

您也可以按一下 [匯入]填入格式如一下的 csv 檔案清單：<*應用程式 URL*>，<*應用程式名稱*>，<*應用程式發行者*>，或按一下 [匯出]，建立 csv 檔案，其中包含格式相同的受限應用程式清單內容。

## <a name="show-or-hide-apps-supervised-only"></a>顯示或隱藏應用程式 (僅限受監督)

在顯示或隱藏的應用程式清單中，可以設定下列清單之一 (需要執行 iOS 9.3 或更新版本的受監督裝置)。

**隱藏的應用程式**清單 - 指定對使用者隱藏的應用程式清單。 使用者無法檢視或啟動這些應用程式。
**顯示的應用程式**清單 - 指定使用者可檢視及啟動的應用程式清單。 無法檢視或啟動其他應用程式。

若要設定清單，請按一下 [新增]，然後在應用程式市集中，指定您所選的名稱 (也可指定選用的應用程式發行者) 以及應用程式的 URL。

### <a name="how-to-specify-the-url-to-an-app-in-the-store"></a>如何在市集中指定應用程式的 URL

若要指定應用程式清單中的應用程式 URL，請使用下列格式：

使用搜尋引擎，在 iTunes App Store 中尋找您要使用的應用程式，然後開啟應用程式的頁面。
複製頁面的 URL，並使用此 URL 作為設定允許或禁止的應用程式清單之 URL，或是想要以 kiosk 模式執行的應用程式。

範例：搜尋 Microsoft Word for iPad。 您使用的 URL 是 https://itunes.apple.com/us/app/microsoft-word-for-ipad/id586447913?mt=8。

> [!Note]
> 您也可以先使用 iTunes 軟體尋找應用程式，再使用 [複製連結]  命令取得應用程式的 URL。

### <a name="additional-options"></a>其他選項

您也可按一下 [匯入]，填入格式如下的 csv 檔案清單：<*應用程式 URL*>，<*應用程式名稱*>，<*應用程式發行者*>，或按一下 [匯出]，建立 csv 檔案，其中包含格式相同的隱藏或顯示之應用程式清單的內容。


## <a name="wireless"></a>無線
-   **數據漫遊** - 允許裝置在行動電話通訊網路時進行資料漫遊。
-   **漫遊時執行全域背景擷取** - 允許裝置在行動電話通訊網路漫遊時擷取資料 (例如電子郵件)。
-   **語音撥號** - 允許在裝置上使用語音撥號功能。
-   **語音漫遊** - 允許裝置在行動電話通訊網路時進行語音漫遊。
-   **應用程式行動數據使用量設定的變更 (僅限受監督)** - 允許使用者控制哪些應用程式可以使用行動數據資料。
-   **個人熱點** - 不允許裝置作為個人熱點。 這項設定可能與某些電訊廠商不相容。
-   **僅使用組態設定檔加入 Wi-Fi 網路 (僅限受監督)** - 僅允許裝置加入已設定 Intune Wi-Fi 設定檔的 Wi-Fi 網路。

- **行動數據使用規則 (僅限受管理的應用程式)** - 讓您定義受管理的應用程式可在行動電話通訊網路上使用的資料類型。 從下列選項進行選擇：
    - **封鎖使用行動數據** - 您可以封鎖使用 [All managed apps] (所有受控應用程式)**** 的行動數據，或 [Choose specific apps] (選擇特定的應用程式)。
    - **漫遊時封鎖使用行動數據** - 您可以封鎖漫遊時使用 [All managed apps] (所有受控應用程式)**** 的行動數據，或 [Choose specific apps] (選擇特定的應用程式)。

## <a name="connected-devices"></a>已連線的裝置

-   **AirDrop (僅限受監督)** - 允許使用 AirDrop 功能與鄰近裝置交換內容。
-   **Apple Watch 配對 (僅限受監督)** - 允許裝置與 Apple Watch 配對。
-   **已配對之 Apple Watch 的手腕偵測** - 啟用時，Apple Watch 就不會在穿戴期間顯示通知。
-   **修改藍牙 (僅限受監督)** - 封鎖使用者變更藍牙裝置上的設定。
-   **主機配對，以控制 iOS 裝置所能配對的裝置 (僅限受監督)** - 允許主機配對，讓系統管理員可控制能與 iOS 裝置配對的裝置。
-   **需要 AirPlay 連出要求配對密碼** - 使用者在使用 AirePlay 將內容串流到其他 Apple 裝置時，需要有成對的密碼。

## <a name="keyboard-and-dictionary"></a>鍵盤與字典

-   **字組定義查閱 (僅限受監督)** - 允許可讓您反白字組並查閱其定義的 iOS 功能。
-   **預測鍵盤 (僅限受監督)** - 允許使用預測鍵盤，以建議使用者可能想要使用的字組。
-   **自動校正 (僅限受監督)** - 讓裝置自動校正拼字錯誤的字組。
-   **鍵盤拼字檢查 (僅限受監督)** - 允許在裝置進行拼字檢查程式。
-   **鍵盤快速鍵 (僅限受監督)** - 允許使用鍵盤快速鍵。
-   **聽寫 (僅限受監督)** - 防止使用者使用語音輸入來輸入文字。

## <a name="cloud-and-storage"></a>雲端與儲存體
-   **備份至 iCloud** - 允許使用者將裝置備份到 iCloud。
-   **文件同步至 iCloud (僅限受監督)** - 允許文件和索引鍵-值同步處理到 iCloud 儲存空間。
-   **相片串流同步至 iCloud** - 讓使用者可在其裝置上啟用 [My Photo Stream] (共享相片串流)，以允許將相片同步處理到 iCloud 並可在所有使用者裝置上使用。
-   **加密備份** - 需要加密任何裝置備份。
-   **iCloud 照片圖庫** - 如果設定為 [否]，請停用 iCloud 照片圖庫，讓使用者在雲端中儲存相片和視訊。   如果這是設定為 [否]，則會從裝置中移除任何未從 iCloud 照片圖庫完整下載到裝置的相片。
-   **受管理應用程式同步至雲端** - 允許您使用 Intune 管理的應用程式將資料同步至使用者的 iCloud 帳戶。
-   **共享相片串流** - 設定為 [否]，會停用裝置上的 [iCloud 相片共享]。
-   **活動接續** - 允許使用者在另一部 iOS 或 macOS 裝置上繼續執行在 iOS 裝置上啟動的工作 (遞交)。

## <a name="autonomous-single-app-mode-supervised-only"></a>自發性單一應用程式模式 (僅限受監督)

使用這些設定來設定 iOS 裝置在自發性單一應用程式模式中執行指定的應用程式。 設定此模式並執行應用程式時，裝置會被鎖定，因此只能執行該應用程式。 一個例子是當您設定應用程式讓使用者在裝置上進行測試時。 當應用程式的動作完成時，或當您移除此原則時，裝置就會回到其正常狀態。

### <a name="settings"></a>設定

- **應用程式名稱**：輸入應用程式的名稱，這會顯示在此刀鋒視窗上的應用程式清單中。
- **應用程式套件組合識別碼**：輸入應用程式的套件組合識別碼。 如需說明，請參閱本主題中的＜內建的 iOS 應用程式套件組合識別碼參考＞。

在您指定每個應用程式的名稱和套件組合識別碼之後，選擇 [新增] 以將它附加至清單。

- **匯入**：匯入包含應用程式名稱及其相關聯套件組合識別碼清單的逗點分隔值 (.csv) 檔案。
- **匯出**：將您所設定的應用程式名稱及相關聯的套件組合識別碼匯出為逗點分隔值 (.csv) 檔案。

### <a name="bundle-id-reference-for-built-in-ios-apps"></a>內建 iOS 應用程式的套件組合識別碼參考

此清單顯示一些常見內建 iOS 應用程式的套件組合識別碼。 若要尋找其他應用程式的套件組合識別碼，請連絡軟體廠商。

```
,com.apple.AppStore,App Store,Apple
,com.apple.calculator,Calculator,Apple
,com.apple.mobilecal,Calendar,Apple
,com.apple.camera,Camera,Apple
,com.apple.mobiletimer,Clock,Apple
,com.apple.compass,Compass,Apple
,com.apple.MobileAddressBook,Contacts,Apple
,com.apple.facetime,FaceTime,Apple
,com.apple.mobileme.fmf1,Find Friends,Apple
,com.apple.mobileme.fmip1,Find iPhone,Apple
,com.apple.gamecenter,Game Center,Apple
,com.apple.mobilegarageband,GarageBand,Apple
,com.apple.Health,Health,Apple
,com.apple.iBooks,iBooks,Apple
,com.apple.MobileStore,iTunes Store,Apple
,com.apple.itunesu,iTunes U,Apple
,com.apple.Keynote,Keynote,Apple
,com.apple.mobilemail,Mail,Apple
,com.apple.MapsMaps,Apple
,com.apple.MobileSMS,Messages,Apple
,com.apple.Music,Music,Apple
,com.apple.news,News,Apple
,com.apple.mobilenotes,Notes,Apple
,com.apple.Numbers,Numbers,Apple
,com.apple.Pages,Pages,Apple
,com.apple.Photo-Booth,Photo Booth,Apple
,com.apple.mobileslideshow,Photos,Apple
,com.apple.podcasts,Podcasts,Apple
,com.apple.reminders,Reminders,Apple
,com.apple.MobileSafari,Safari,Apple
,com.apple.Preferences,Settings,Apple
,com.apple.stocks,Stocks,Apple
,com.apple.tips,Tips,Apple
,com.apple.videos,Videos,Apple
,com.apple.VoiceMemos,VoiceMemos,Apple
,com.apple.Passbook,Wallet,Apple
,com.apple.Bridge,Watch,Apple
,com.apple.weather,Weather,Apple
```


## <a name="kiosk-supervised-only"></a>Kiosk (僅限受監督)
-   **kiosk 模式下執行的應用程式** - 選擇 [受管理的應用程式] 可選取已新增至 Intune 的應用程式，而選擇 [市集應用程式] 則可指定市集中應用程式的 URL。 不允許在裝置上執行其他應用程式。 如需詳細說明，請參閱本主題稍後的＜如何將 URL 指定給應用程式市集＞。
    -   **輔助觸控** - 啟用或停用 [輔助觸控] 協助工具設定，協助使用者執行可能很難執行的螢幕手勢。
    -   **色彩對換** - 啟用或停用 [色彩對換] 協助工具設定，以調整顯示畫面來協助視力受損的使用者。
    -   **單聲道音訊** - 啟用或停用協助工具設定 [單聲道音訊]。
    -   **配音** - 啟用或停用協助工具設定 [配音]，以大聲讀出裝置螢幕上的文字。
    -   **縮放** - 啟用或停用 [縮放] 協助工具的設定，以讓使用者使用觸控來縮放裝置螢幕。
    -   **自動鎖定** - 啟用或停用裝置的自動鎖定。
    -   **響鈴切換** - 啟用或停用裝置上的響鈴 (靜音) 切換。
    -   **旋轉螢幕** - 啟用或停用在使用者旋轉裝置時變更螢幕方向。
    -   **螢幕睡眠按鈕** - 啟用或停用裝置上的喚醒螢幕睡眠按鈕。
    -   **觸控** - 在裝置上啟用或停用觸控螢幕。
    -   **音量按鈕** - 啟用或停用裝置上的音量按鈕。
    -   **輔助觸控控制項** - 啟用或停用輔助觸控調整，以讓使用者調整輔助觸控功能。
    -   **色彩對換控制** - 啟用或停用色彩對換調整，以讓使用者調整色彩對換功能。
    -   **說出選取的文字** - 啟用或停用 [讀出選取範圍] 協助工具設定，以大聲讀出使用者選取的文字。
    -   **配音控制** - 啟用或停用配音調整，以讓使用者調整配音功能 (例如，大聲讀出螢幕上文字的速度)。
    -   **縮放控制** - 啟用或停用縮放調整，以讓使用者調整縮放功能。

>[!NOTE]
> 您必須先使用 Apple Configurator 工具或 Apple 裝置註冊方案，將裝置設為受監督模式，才可為 iOS 裝置設定 kiosk 模式。 如需 Apple Configurator 工具的詳細資訊，請參閱您的 Apple 文件。
>如果指定的 iOS 應用程式在您指派設定檔之後安裝，則裝置在重新啟動之前，不會進入 Kiosk 模式。

## <a name="safari"></a>Safari
-   **Safari (僅限受監督)** - 指定是否可以在裝置上使用 Safari 瀏覽器。
-   **自動填滿** - 允許使用者變更瀏覽器中的自動完成設定。
-   **Cookie** - 允許瀏覽器使用 Cookie。
-   **JavaScript** - 允許在瀏覽器中執行 Java 指令碼。
-   **詐騙警告** - 允許瀏覽器中的詐騙警告。
-   **快顯** - 啟用或停用瀏覽器的快顯封鎖程式。


## <a name="domains"></a>Domains

### <a name="unmarked-email-domains"></a>未標記的電子郵件網域

在 [電子郵件網域 URL] 欄位中，將一或多個 URL 新增到清單中。 當使用者接收到來自不是您所設定之網域的電子郵件時，該電子郵件會在 iOS 郵件應用程式中標記為不受信任。


### <a name="managed-web-domains"></a>受管理的 Web 網域

在 [Web 網域 URL] 欄位中，將一或多個 URL 新增到清單中。 當文件是從您所指定的網域下載時，它們會被視為受控文件。 此設定僅適用於使用 Safari 瀏覽器下載的文件。


### <a name="safari-password-autofill-domains"></a>Safari 密碼自動填入網域

在 [網域 URL] 欄位中，將一或多個 URL 新增到清單中。 使用者只能儲存此清單中 URL 的密碼。 此設定僅適用於處於受監督模式的 iOS 9.3 及更新版本裝置中的 Safari 瀏覽器。 如果您不指定任何 URL，便可以儲存所有網站的密碼。

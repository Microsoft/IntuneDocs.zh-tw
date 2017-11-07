---
title: "iOS 原則設定"
description: "建立原則，以在您使用 Intune 管理的 iOS 裝置上控制設定及功能。"
keywords: 
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.date: 11/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ab46be6c-ab73-4c99-8492-66d1dd418293
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 58be7ad24da7e4eadc1c67016979396114799bd8
ms.sourcegitcommit: 0f877251e6adf4e45b918cc8dc9193626727f2d9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2017
---
# <a name="ios-policy-settings-in-microsoft-intune"></a>Microsoft Intune 的 iOS 原則設定

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Intune 提供一些內建的一般設定，您可在 iOS 裝置上加以設定。 此外，您可以使用 Apple Configurator 工具建立 Intune 所沒有的自訂設定。

## <a name="general-configuration-policy-settings"></a>一般設定原則設定

使用 Microsoft Intune **iOS 一般設定原則**進行下列設定：

-   **一般裝置與安全性設定**。 您可以從預先定義的設定清單中選擇，以控制裝置上某個功能範圍。

-   **Kiosk 模式**。 鎖定裝置以限定執行某些特定功能。 例如，您可以允許裝置只執行您指定的一個受管理應用程式，也可以停用裝置上的音量按鈕。 這些設定可能用於裝置的展示模型，或是專用來只執行一個功能的裝置，例如銷售點裝置。

-   **相容和不相容的應用程式**。 指定在公司中相容或不相容的應用程式清單。 在 Android 和 iOS 裝置上，**不相容的應用程式報告**可用來針對使用者已安裝 (但無法實際封鎖應用程式安裝) 的應用程式，檢視您在清單中所指定應用程式的相容性。

> [!TIP]
> 您可以設定使用者的條款及條件，確定他們知道將會評估其裝置上的應用程式 (包括個人應用程式)，並會封鎖不相容應用程式，或將其回報為不相容。 使用者必須先接受這些條款及條件，才能註冊他們的裝置，並使用公司入口網站來取得應用程式。 如需使用條款與條件的詳細資訊，請參閱 [Microsoft Intune 的條款和條件原則設定](terms-and-condition-policy-settings-in-microsoft-intune.md)。

若本主題中未包含您所需要的設定，您可以使用 iOS 自訂原則加以建立，以便您使用 [Apple Configurator 工具](https://itunes.apple.com/us/app/apple-configurator/id434433123?mt=12)匯入您所建立的設定。 如需詳細資訊，請參閱本主題稍後的＜自訂原則設定＞。

### <a name="security-settings"></a>安全性設定
所有設定適用於 iOS 8.0 和更新版本。

|設定名稱|詳細資料|
|----------------|-------|
|**需要密碼才可解除鎖定行動裝置**|指定使用者是否需要輸入密碼才能存取其裝置。|
|**所需的密碼類型**|指定必要密碼的類型，例如只可包含數字，或必須是英數字元等等。|
|**密碼所需的複合字元數**|指定密碼中必須包含的符號字元數 (例如 **#** 或 **@**)。|
|**密碼長度下限**|指定密碼的字元數下限。|
|**允許簡單密碼**|允許簡單密碼，例如 **0000** 和 **1234**。|
|**抹除裝置前允許的重複登入失敗次數**|指定失敗的登入嘗試次數，之後這個設定即抹除裝置。|
|**在非使用狀態幾分鐘後需要輸入密碼**<sup>1</sup>|指定使用者必須重新輸入密碼之前，裝置可保持閒置多長的時間。|
|**密碼到期 (天數)**|指定必須變更裝置密碼前的天數。|
|**記住密碼歷程記錄**|指定使用者是否可以使用先前使用過的密碼。|
|**記住密碼歷程記錄** - **不得重複使用以前用過的密碼**|指定裝置記憶的先前使用過密碼數目。|
|**在非使用狀態幾分鐘後會關閉螢幕**<sup>1</sup>|指定關閉裝置顯示器之前的分鐘數。|
|**允許指紋解除鎖定**|允許使用指紋解除鎖定裝置。|
<sup>1</sup> 對於 iOS 裝置，您如有設定 [在非使用狀態幾分鐘後會關閉螢幕] 和 [在非使用狀態幾分鐘後需要輸入密碼]，這兩項設定將會依序套用。 例如，若您設定將兩項全都設定為 **5** 分鐘，螢幕將會自動在 5 分鐘後關閉，裝置將會在另一個 5 分鐘之後鎖定。 但使用者若是手動關閉螢幕，便會立即套用第二項設定。 在同一範例中，當使用者關閉螢幕之後，裝置將會在 5 分鐘後鎖定。

### <a name="system-settings"></a>系統設定
所有設定適用於 iOS 8.0 和更新版本。

|設定名稱|詳細資料|
|----------------|-------|
|**允許擷取螢幕畫面**|允許使用者將螢幕的內容擷取為影像。|
|**允許在鎖定畫面時使用控制中心**|允許使用者在裝置鎖定時存取控制中心應用程式。|
|**允許在鎖定畫面時使用通知檢視**|允許使用者在未解除鎖定裝置的情況下存取通知檢視。|
|**允許在鎖定畫面時使用今日檢視**|允許使用者在裝置鎖定時檢視通知。|
|**允許未受信任的 TLS 憑證**|允許裝置上的未受信任傳輸層安全性憑證。|
|**允許提交診斷資料**|允許或封鎖裝置提交診斷資料給 Apple。|
|**允許在鎖定時使用 Passbook**|允許使用者在鎖定裝置時存取 Passbook 應用程式。|

### <a name="cloud-settings-for-documents-and-data"></a>文件和資料的雲端設定
所有設定適用於 iOS 8.0 和更新版本。

|設定名稱|詳細資料|
|----------------|-------|
|**允許備份至 iCloud**|允許使用者將裝置備份到 iCloud。|
|**允許文件同步至 iCloud**|允許文件和索引鍵-值同步處理到 iCloud 儲存空間。|
|**允許相片串流同步至 iCloud**|可讓使用者在其裝置上啟用 [共享相片串流]，以允許將相片同步處理到 iCloud 並可在所有使用者裝置上使用。|
|**需要加密備份**|需要加密任何裝置備份。|
|**允許受管理的應用程式將資料同步到 iCloud**|允許您使用 Intune 管理的應用程式將資料同步至使用者的 iCloud 帳戶。|
|**允許 Handoff，以繼續執行其他裝置上的活動**|允許使用者在另一部 iOS 或 Mac OS X 裝置上繼續執行在 iOS 裝置上啟動的工作。|
|**允許 iCloud 照片共享**|設定為 [否]，停用裝置 上的 [iCloud 相片共享]。|
|**允許 iCloud 照片圖庫**|如果設定為 [否]，請停用 iCloud 相片圖庫，讓使用者在雲端中儲存相片和視訊。   如果這是設定為 [否]，將會從裝置中移除任何未從 iCloud 相片圖庫完整下載到裝置的相片。|

### <a name="application-settings-for-the-browser"></a>瀏覽器的應用程式設定
所有設定適用於 iOS 8.0 和更新版本。

|設定名稱|詳細資料|
|----------------|-------|
|**允許 Safari**|指定是否可以在裝置上使用 Safari 瀏覽器。|
|**允許自動填滿**|允許使用者變更瀏覽器中的自動完成設定。|
|**允許快顯封鎖程式**|啟用或停用瀏覽器的快顯封鎖程式。|
|**允許 Cookie**|允許瀏覽器使用 Cookie。|
|**允許撰寫 Java 指令碼**|允許在瀏覽器中執行 Java 指令碼。|
|**允許詐騙警告**|允許瀏覽器中的詐騙警告。|

### <a name="application-settings-for-apps"></a>應用程式的應用程式設定
所有設定適用於 iOS 8.0 和更新版本。

|設定名稱|詳細資料|
|----------------|-------|
|**允許安裝應用程式**|允許裝置存取應用程式市集並安裝應用程式。|
|**需要密碼才可存取應用程式市集**|要求使用者先輸入密碼，才可以瀏覽應用程式市集。|
|**允許應用程式內購買**|允許從執行中應用程式進行市集購買。|
|**允許在其他未受管理的應用程式中使用受管理的文件**|允許在任何應用程式中檢視公司文件。<br>**範例︰**您想要防止使用者將檔案從 OneDrive 應用程式儲存至 Dropbox。 將此設定設定為否。 裝置收到原則後 (例如重新啟動後)，即不再允許儲存。|
|**允許在其他受管理應用程式中使用未受管理的文件**|允許在公司受管理應用程式中檢視任何文件。|
|**允許視訊會議**|允許在裝置上執行視訊會議應用程式，例如 Face Time。|
|**允許使用者信任新的企業應用程式作者**|讓使用者選擇信任不是從應用程式市集下載的應用程式。|


### <a name="application-settings-for-games"></a>遊戲的應用程式設定
所有設定適用於 iOS 8.0 和更新版本。

|設定名稱|詳細資料|
|----------------|-------|
|**允許新增 Game Center 的朋友**|允許使用者在 Game Center 中新增朋友。|
|**允許多人連線遊戲**|允許使用者在裝置上玩多人遊戲。|

### <a name="application-settings-for-media-content"></a>媒體內容的應用程式設定
所有設定適用於 iOS 8.0 和更新版本。

|設定名稱|詳細資料|
|----------------|-------|
|**分級區域**|選取區域，然後選取使用者可下載的**電影**、**電視節目**及**應用程式**分級上限。|
|**允許媒體市集中的成人內容**|允許裝置存取市集中評分為成人的內容。|
|**允許使用者從 iBook Store 下載標示為 [成人作品] 的內容**|允許使用者下載「成人作品」類別的書籍。|


### <a name="device-capabilities-settings-for-hardware"></a>硬體的裝置功能設定
所有設定適用於 iOS 8.0 和更新版本。

|設定名稱|詳細資料|
|----------------|-------|
|**允許相機**|指定是否可以使用裝置上的相機。|
|**強制已配對的 Apple Watch 使用手腕偵測**|啟用時，Apple Watch 就不會在穿戴期間顯示通知。|
|**須有配對密碼，才能傳出 AirPlay 要求**|使用者在使用 AirePlay 將內容串流到其他 Apple 裝置時，需要有成對的密碼。|

### <a name="device-capabilities-settings-for-cellular"></a>行動數據的裝置功能設定
所有設定適用於 iOS 8.0 和更新版本。

|設定名稱|詳細資料|
|----------------|-------|
|**允許語音漫遊**|允許裝置在行動電話通訊網路時進行語音漫遊。|
|**允許數據漫遊**|允許裝置在行動電話通訊網路時進行資料漫遊。|
|**允許漫遊時進行全域背景擷取**|允許裝置在行動電話通訊網路漫遊時擷取資料 (例如電子郵件)。|

### <a name="device-capabilities-settings-for-features"></a>功能的裝置功能設定
所有設定適用於 iOS 8.0 和更新版本。

|設定名稱|詳細資料|
|----------------|-------|
|**允許 Siri**|允許在裝置上使用 Siri 助理。|
|**允許在裝置鎖定時使用 Siri**|允許裝置在鎖定時於其上使用 Siri 語音助理。|
|**允許語音撥號**|允許在裝置上使用語音撥號功能。|
|**不允許來自受管理應用程式的 Airdrop**|讓受管理的應用程式不再能夠 從 Airdrop 傳送資料。|


### <a name="settings-for-compliant-and-noncompliant-apps"></a>相容與不相容之應用程式的設定
在 **[相容和不相容的應用程式]** 清單中，使用下列資訊指定相容或不相容的應用程式清單。

> [!NOTE]
> 單一原則只能包含一份相容應用程式的清單或不相容應用程式的清單。 您不能在相同的原則中同時指定兩者。

|設定名稱|詳細資料|
|----------------|--------------------|
|**當使用者安裝列出的應用程式時回報不符合規範**|列出不允許使用者安裝和執行的應用程式 (不由 Intune 管理)。|
|**當使用者安裝未列出的應用程式時回報不符合規範**|列出允許使用者安裝的應用程式。 若要保持相容，使用者絕不能安裝未列出的應用程式。 自動允許 Intune 所管理的應用程式。|
|**[新增]**|將應用程式加入選取的清單中。 指定應用程式存放區中應用程式由您選擇的名稱 (選擇性的應用程式發行者) 和 URL。 如需更多協助，請參閱本主題稍後的＜如何指定 URL 給應用程式市集＞。|
|**匯入應用程式**|匯入逗點分隔值檔案中所指定的應用程式清單。 請在檔案中使用「應用程式名稱, 發行者, 應用程式 URL」格式。|
|**編輯**|編輯所選取應用程式的名稱、發行者和 URL。|
|**刪除**|從清單中刪除選取的應用程式。|

包含相容和不相容應用程式設定的原則必須部署到使用者群組。

### <a name="kiosk-mode-settings"></a>Kiosk 模式設定

|設定名稱|詳細資料|
|----------------|--------------------|
|**選取當裝置為 Kiosk 模式時，允許執行的受管理應用程式**|選擇 **[瀏覽]**，然後指定在裝置處於 kiosk 模式時允許執行的受管理應用程式或市集中的應用程式。 不允許在裝置上執行其他應用程式。 如需詳細說明，請參閱本主題稍後的＜如何將 URL 指定給應用程式市集＞。|
|**允許觸控**|在裝置上啟用或停用觸控螢幕。|
|**允許旋轉螢幕**|啟用或停用在使用者旋轉裝置時變更螢幕方向。|
|**允許音量按鈕**|在裝置上啟用或停用音量按鈕。|
|**允許響鈴開關**|在裝置上啟用或停用響鈴 (靜音) 開關。|
|**允許喚醒螢幕睡眠按鈕**|在裝置上啟用或停用喚醒螢幕睡眠按鈕。|
|**允許自動鎖定**|啟用或停用裝置的自動鎖定。|
|**啟用單聲道音訊**|啟用或停用協助工具設定 **[單聲道音訊]**。|
|**啟用旁白**|啟用或停用協助工具設定 **[VoiceOver]**，以大聲讀出裝置螢幕上的文字。|
|**啟用旁白調整**|啟用或停用配音調整，以讓使用者調整 VoiceOver 功能 (例如，大聲讀出螢幕上文字的速度)。|
|**啟用縮放**|啟用或停用 **[縮放]** 協助工具設定，以讓使用者使用觸控來縮放裝置螢幕。|
|**啟用縮放調整**|啟用或停用縮放調整，以讓使用者調整縮放功能。|
|**啟用色彩對換**|啟用或停用 **[色彩對換]** 協助工具設定，以調整顯示畫面來協助視力受損的使用者。|
|**啟用色彩對換調整**|啟用或停用色彩對換調整，以讓使用者調整色彩對換功能。|
|**啟用輔助觸控**|啟用或停用 **[輔助觸控]** 協助工具設定，協助使用者執行可能很難執行的螢幕手勢。|
|**啟用輔助觸控調整**|啟用或停用輔助觸控調整，以讓使用者調整輔助觸控功能。|
|**啟用語音選取**|啟用或停用 **[讀出選取範圍]** 協助工具設定，以大聲讀出使用者選取的文字。|
> [!NOTE]
> 下列附註適用於 iOS 裝置的資訊站模式設定：
>
> -   您必須先使用 [Apple Configurator 工具](https://itunes.apple.com/us/app/apple-configurator/id434433123?mt=12)或 [Apple 裝置註冊方案](ios-device-enrollment-program-in-microsoft-intune.md)，將裝置設為受監督模式，才能為 iOS 裝置設定 kiosk 模式。 如需 Apple Configurator 工具的詳細資訊，請參閱您的 Apple 文件。
> -   如果在部署組態原則之後安裝您指定的 iOS 應用程式，則除非重新啟動裝置，否則裝置不會進入 kiosk 模式。

### <a name="reference-information-for-compliant-and-noncompliant-apps"></a>相容與不相容之應用程式的參考資訊

使用 [不相容應用程式報表]  檢視允許和封鎖應用程式的相容性。

##### <a name="to-run-the-noncompliant-apps-report"></a>執行不相容應用程式報表

1.  在 [Microsoft Intune 管理主控台](https://manage.microsoft.com)中，選擇 [報表] &gt; [不相容應用程式報表]。

2.  選取您想要檢查的裝置群組、選取是否要檢查相容應用程式和 (或) 不相容應用程式，然後選擇 **[檢視報告]**。

#### <a name="how-to-specify-urls-to-app-stores"></a>如何指定 URL 給應用程式市集
若要在符合規定及不符合規定的應用程式清單中或在 [選取當裝置為 Kiosk 模式時，允許執行的受管理應用程式]  選項 (僅限 iOS) 中，指定應用程式 URL，請使用下列其中一種格式：

1. 使用搜尋引擎，在 iTunes App Store 中尋找您要使用的應用程式，然後開啟應用程式的頁面。

2. 複製頁面的 URL，並以此 URL 設定相容和不相容的應用程式清單，或您要在 kiosk 模式下執行的應用程式。

範例： 搜尋 **Microsoft Word for iPad**。 您要使用的 URL 是 **https://itunes.apple.com/us/app/microsoft-word-for-ipad/id586447913?mt=8**。

> [!NOTE]
> 您也可以先使用 iTunes 軟體尋找應用程式，再使用 [複製連結]  命令取得應用程式的 URL。

### <a name="enrollment-settings"></a>註冊設定
所有設定適用於 iOS 8.0 和更新版本。

|設定名稱|詳細資料|
|----------------|--------------------|
|**允許裝置在受監督模式時使用啟用鎖定**|在受監督的 iOS 裝置上將啟用鎖定啟用。|

### <a name="supervised-mode-settings"></a>受監督模式設定
您可以在處於受監督模式且執行 iOS 8.0 和更新版本的裝置上進行下列設定。

### <a name="supervised-mode-settings-for-device-restrictions"></a>用於限制裝置的受監督模式設定

|設定名稱|詳細資料|
|----------------|--------------------|
|**允許修改帳戶**|允許使用者變更帳戶設定，例如電子郵件設定。|
|**允許變更應用程式的行動數據使用量設定**|允許使用者控制哪些應用程式可以使用行動數據。|
|**允許在裝置上使用清除所有內容及設定的選項**|允許使用者使用清除裝置上所有內容及設定的選項。|
|**允許使用者啟用裝置設定中的限制**|允許使用者在裝置上設定裝置限制 (家長監護)。|
|**允許主機配對，以控制 iOS 裝置所能配對的裝置**|允許主機配對讓管理員可控制 iOS 裝置所能配對的裝置。|
|**允許使用者安裝組態設定檔與憑證**|允許使用者安裝組態設定檔和憑證。|
|**允許修改裝置名稱**|允許使用者變更裝置的名稱。|
|**允許密碼修改**|允許新增、變更或移除裝置密碼。|
|**允許 Apple Watch 配對**|允許裝置與 Apple Watch 配對。|
|**允許通知設定修改**|允許使用者變更裝置通知設定。|
|**允許背景圖片修改**|允許使用者變更裝置背景圖片。|

### <a name="supervised-mode-settings-for-feature-restrictions"></a>用於限制功能的受監督模式設定

|設定名稱|詳細資料|
|----------------|--------------------|
|**允許 AirDrop**|允許使用 AirDrop 功能與鄰近裝置交換內容。|
|**允許 Siri 從網際網路查詢使用者產生的內容**|允許 Siri 存取網站來回答問題。|
|**使用 Siri 不雅內容篩選**|防止 Siri 聽寫或說出不雅字眼。|
|**允許 Spotlight 搜尋傳回網際網路上的結果**|讓 Spotlight 搜尋連線到網際網路，以提供進一步的結果。|
|**允許字詞定義查詢**|允許可讓您反白字組並查詢其定義的 iOS 功能。|
|**允許預測鍵盤**|允許使用預測鍵盤，以建議使用者可能想要使用的字組。|
|**允許自動修正**|讓裝置自動校正拼字錯誤的字組。|
|**允許鍵盤拼字檢查**|允許裝置的拼字檢查工具。|
|**允許鍵盤快速鍵**|允許使用鍵盤快速鍵。|

### <a name="supervised-mode-settings-for-app-restrictions"></a>用於限制應用程式的受監督模式設定

|設定名稱|詳細資料|
|----------------|--------------------|
|**允許企業應用程式信任設定修改**|可讓使用者變更企業應用程式的信任設定。|
|**只允許使用 Apple Configurator 和 iTunes 安裝應用程式**|從裝置主畫面啟用或停用 App Store。 使用者仍可使用 iTunes 或 Apple Configurator 工具來安裝和更新應用程式。|
|**允許自動 App 下載**|允許其他裝置上購買的應用程式自動下載到此裝置。 這項設定不會影響應用程式更新。|
|**允許變更 [尋找我的朋友] 應用程式設定**|允許使用者變更 [尋找我的朋友] 應用程式的設定。|
|**允許存取 iBooks Store**|允許使用者在 iBooks Store 瀏覽和購買書籍。|
|**允許在裝置上使用「訊息」應用程式**|允許使用「訊息」應用程式傳送簡訊。|
|**允許使用 Podcast**|允許使用播客應用程式。|
|**允許使用 Music 服務**|允許使用 Apple Music 應用程式。|
|**允許 iTunes Radio 服務**|允許使用 iTunes Radio 應用程式。|
|**允許 Apple News**|允許使用 Apple News 應用程式。|
|**允許 Game Center**|允許使用 Game Center 應用程式。|


### <a name="show-or-hide-apps"></a>顯示或隱藏應用程式

使用 **[Hidden and shown apps list]** (隱藏與顯示的應用程式清單) 來在受監督的裝置 (執行 iOS 9.3 或更新版本) 上控制下列項目︰

- 指定對使用者隱藏的應用程式清單。 使用者無法檢視或啟動這些應用程式。
- 指定使用者可檢視及啟動的應用程式清單。 無法檢視或啟動其他應用程式。


#### <a name="how-to-create-a-hidden-or-shown-app-list"></a>如何建立隱藏或顯示的應用程式清單

指定下列設定：

|設定名稱|詳細資料|
|-|-|
|**隱藏與顯示的應用程式清單**|如果您想要建立隱藏或顯示的應用程式清單，請啟用此設定。|
|**對使用者隱藏列出的應用程式**|如果您想要建立會對使用者隱藏的應用程式清單，請選取此選項。<br>當您建立此清單類型時，除了 iOS「設定」和「電話」 (適用於 iPhone) 應用程式以外的所有應用程式都可被隱藏。|
|**只對使用者顯示列出的應用程式**|如果您想要建立會對使用者顯示的應用程式清單，請選取此選項。<br>當您建立此清單類型時，除了 iOS **設定**和**電話** (適用於 Iphone) 應用程式以外的所有應用程式都會隱藏 。<br>此外，您必須將公司入口網站和任何您已部署，並使用 Intune 管理的應用程式加入清單中。|
|**[新增]**|將應用程式新增至選取的清單。<br>針對隱藏清單中，您必須指定每個想要隱藏之應用程式的 **[名稱]**，**[發行者]**，和 **[App URL or Bundle ID]** (應用程式 URL 或組合識別碼)。<br>針對所示清單，您可以 **[選取受管理的應用程式]**，這會提供您使用 Intune 所管理的應用程式清單以供您選取，或 [選取市集應用程式]，之後您必須指定每個您想要顯示之應用程式的 **[名稱]**，**[發行者]**，和 **[App URL or Bundle ID]** (應用程式 URL 或組合識別碼)。|
|**匯入應用程式**|匯入逗點分隔值檔案中所指定的應用程式清單。 請在檔案中使用「應用程式名稱, 發行者, 應用程式 URL」格式。|
|**編輯**|讓我們編輯所選取應用程式的名稱、發行者和 URL。|
|**刪除**|從清單中刪除選取的應用程式。|

#### <a name="app-information-for-built-in-ios-apps"></a>內建 iOS 應用程式的應用程式資訊

使用此清單中的資訊來識別您可能想要顯示或隱藏之內建 iOS 應用程式的名稱、發行者及組合識別碼。 如果您想要顯示或隱藏清單中的所有應用程式，您可以將下列資料複製到文字檔，並使用副檔名 **.csv**，然後使用 [匯入應用程式] 選項來同時匯入所有的應用程式。

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




## <a name="custom-policy-settings"></a>自訂原則設定

使用 Microsoft Intune **iOS 自訂原則**，將您使用 [Apple Configurator 工具](https://itunes.apple.com/us/app/apple-configurator/id434433123?mt=12)建立的設定，部署至 iOS 裝置。 此工具讓您能夠建立許多設定來控制這些裝置的操作，並將它們匯出到組態設定檔。 您接著可將這個組態設定檔匯入 Intune iOS 自訂原則，並將設定部署到組織中的使用者和裝置。

這項功能可讓您部署無法使用 Intune 一般組態原則進行的 iOS 設定。

### <a name="prerequisites"></a>必要條件
開始之前，您必須安裝 Apple Configurator，並建立包含您要部署到使用者或裝置之設定的組態檔。 您可以從 [Mac App Store](https://itunes.apple.com/us/app/apple-configurator/id434433123?mt=12) 下載並了解 Apple Configurator。

> [!NOTE]
> Intune 不會報告 iOS 自訂原則中個別設定的相容性。 不過，會報告原則的整體相容性。

### <a name="general-settings"></a>一般設定

|設定名稱|詳細資料|
    |----------------|--------------------|
    |**Name**|輸入 iOS 自訂原則的唯一名稱，有助於您在 Intune 主控台中識別該原則。|
    |**說明**|提供可給予 iOS 自訂原則概觀的說明，以及可協助您找到該說明的其他相關資訊。|

### <a name="custom-settings"></a>自訂設定

|設定名稱|詳細資料|
    |----------------|--------------------|
|**自訂組態設定檔名稱 (對使用者顯示)**|提供原則的名稱，因為它將顯示於裝置上和 Intune 原則報告中。|
|**組態設定檔**|選擇 **[匯入]**，然後瀏覽到您使用 Apple Configurator 建立的組態設定檔。 **注意：** 確定您從 Apple Configurator 工具匯出的設定會與您部署 iOS 自訂原則之裝置上的 iOS 版本相容。 如需如何解決不相容設定的相關資訊，請在 [Apple Developer](https://developer.apple.com/) 網站上搜尋 **組態設定檔參考**和**行動裝置管理通訊協定參考**。|
    |**組態設定檔詳細資料**|顯示您所匯入組態設定檔的 XML 程式碼。|

### <a name="see-also"></a>請參閱
[使用 Microsoft Intune 原則管理裝置的設定及功能](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)

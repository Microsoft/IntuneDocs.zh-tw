---
title: "適用於 Android 的 Intune 裝置限制設定 | Intune Azure 預覽版 | Microsoft Docs"
description: "Intune Azure 預覽版︰了解 Android 裝置上可用以控制裝置設定與功能的 Intune 設定。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6bdf714a-5d93-485c-8b52-513635c60cb6
ms.reviewer: heenamac
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b4d095506215b775d56d172e9aabae1737757310
ms.openlocfilehash: a003b2b16e05c2d071bb7dbaaf564e24d0cf5823
ms.lasthandoff: 02/16/2017


---

# <a name="android-and-samsung-knox-standard-device-restriction-settings-in-microsoft-intune"></a>Microsoft Intune 中的 Android 與 Samsung KNOX Standard 裝置限制設定

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

## <a name="general"></a>一般
-     **相機** - 允許使用裝置的相機。
-     **複製並貼上** - 允許在裝置上進行複製並貼上功能。
-     **在應用程式之間共用剪貼簿** - 允許使用剪貼簿在應用程式之間 (僅限 Samsung KNOX Standard) 複製並貼上。
-     **送出診斷資料** - 讓使用者無法從裝置送出診斷資料。    
-     **恢復出廠預設值** - 允許使用者在裝置上重設為原廠設定。
-     **地理位置** - 允許裝置可利用位置資訊 (僅限 Samsung KNOX Standard)。
-     **關閉電源** - 允許使用者關閉裝置的電源。<br>如果停用此設定，Samsung KNOX Standard 裝置的 [登入失敗幾次後即抹除裝置] 設定將無法運作。
-     **螢幕擷取** - 讓使用者可擷取螢幕內容做成影像。
-     **語音助理** - 允許在裝置上使用語音助理軟體 (僅限 Samsung KNOX Standard)。
-     **YouTube** - 允許在裝置上使用 YouTube 應用程式 (僅限 Samsung KNOX Standard)。

## <a name="password"></a>密碼
-     **需要密碼** - 需要使用者輸入密碼才可存取該裝置。
-     **密碼長度下限** - 輸入使用者必須設定的密碼長度下限 (介於 4 到 16 個字元之間)。
-     **沒有活動最久幾分鐘後鎖定螢幕** - 指定沒有任何活動幾分鐘之後，自動鎖定裝置。
-     **登入失敗幾次後即抹除裝置** - 指定抹除裝置前允許的登入失敗次數。
-     **密碼到期 (天數)** - 指定多少天後必須變更裝置密碼。
-     **必要的密碼類型** - 指定所需的密碼複雜度等級，以及是否可以使用生物識別裝置。
-     **避免重複使用先前的密碼** - 讓使用者無法建立以前用過的密碼。
-     **指紋解除鎖定** - 允許使用指紋來解除鎖定受支援的裝置。
-     **Smart Lock 與其他信任代理程式** - 可讓您控制相容的 Android 裝置 (Samsung KNOX Standard 5.0 及更新版本) 上的 Smart Lock 功能。 此電話功能 (有時也稱為信任代理程式) 可讓您在裝置位於受信任的位置 (例如連線到特定的藍牙裝置或靠近 NFC 標記) 時，停用或略過裝置鎖定畫面密碼。您可以使用此設定來防止使用者設定 Smart Lock。
-     **加密** - 需要加密裝置上的檔案。

## <a name="google-play-store"></a>Google Play 商店

-     **Google Play 商店** - 允許使用者在裝置上存取 Google Play 商店 (僅限 Samsung KNOX Standard)。

## <a name="restricted-apps"></a>受限應用程式

您可以在受限制應用程式清單中，設定下列清單之一︰

**禁止的應用程式**清單 - 列出不允許使用者安裝與執行的應用程式 (並非由 Intune 管理)。
**核准的應用程式**清單 - 列出允許使用者安裝的應用程式。 若要保持相容，使用者絕不能安裝未列出的應用程式。 自動允許 Intune 所管理的應用程式。
包含受限應用程式設定的裝置設定檔，必須部署到使用者群組。

若要設定清單，請按一下 [新增]，然後在應用程式市集中，指定您所選的名稱 (也可指定選用的應用程式發行者) 以及應用程式的 URL。

### <a name="how-to-specify-the-url-to-an-app-in-the-store"></a>如何在市集中指定應用程式的 URL

若要在相容或不相容應用程式清單中指定應用程式 URL，請採取下列步驟︰

在 [Google Play 商店的 [應用程式] 區段](https://play.google.com/store/apps)中，搜尋您要使用的應用程式。

開啟應用程式的安裝頁面，然後將 URL 複製到剪貼簿。 您現在可以使用在相容或不相容的應用程式清單中使用此 URL。

範例：在 Google Play 中搜尋 Microsoft Office Mobile。 您要使用的 URL 是 **https://play.google.com/store/apps/details?id=com.microsoft.office.officehub**。

### <a name="additional-options"></a>其他選項

您也可以按一下 [匯入]填入格式如一下的 csv 檔案清單：<*應用程式 URL*>，<*應用程式名稱*>，<*應用程式發行者*>，或按一下 [匯出]，建立 csv 檔案，其中包含格式相同的受限應用程式清單內容。        

## <a name="browser"></a>瀏覽器
-     **網頁瀏覽器** - 指定是否可使用裝置的預設網頁瀏覽器。
-     **自動填滿** - 允許使用網頁瀏覽器的自動填入功能。
-     **Cookies** - 允許裝置的網頁瀏覽器使用 Cookie。
-     **Javascript** - 允許裝置網頁瀏覽器執行 Java 指令碼。
-     **快顯** - 允許在網頁瀏覽器中使用快顯封鎖程式。

## <a name="cloud-and-storage"></a>雲端與儲存體
-     **Google 備份** - 允許使用 Google 備份。
-     **Google 帳戶自動同步** - 允許自動同步 Google 帳戶設定。
-     **抽取式存放裝置** - 允許裝置使用抽取式存放裝置，例如 SD 記憶卡 (僅限 Samsung KNOX Standard)。
-     **加密儲存卡上的內容** - 指定是否必須加密裝置儲存卡。

## <a name="cellular-and-connectivity"></a>行動數據與連線
-     **數據漫遊** - 允許裝置在行動數據網路進行數據漫遊 (僅限 Samsung KNOX Standard)。
-     **SMS/MMS 傳訊** - 允許在裝置上使用 SMS 與 MMS 傳訊 (僅限 Samsung KNOX Standard)。
-     **語音撥號** - 在裝置上啟用或停用語音撥號功能 (僅限 Samsung KNOX Standard)。
-     **語音漫遊** - 允許裝置在行動數據網路上進行語音漫遊 (僅限 Samsung KNOX Standard)。
-     **藍牙** - 允許在裝置上使用藍牙 (僅限 Samsung KNOX Standard)。
-     **NFC** - 如果裝置支援，則允許使用近距離無線通訊的作業 (僅限 Samsung KNOX Standard)。
-     **Wi-Fi** - 允許在裝置上使用 Wi-Fi 功能 (僅限 Samsung KNOX Standard)。
-     **Wi-Fi 網際網路共用功能** - 允許在裝置上使用 Wi-Fi 網際網路共用功能 (僅限 Samsung KNOX Standard)。

## <a name="kiosk"></a>Kiosk
-     **選取受管理的應用程式** - 瀏覽到應用程式，然後選取當裝置為 Kiosk 模式時可執行的受管理應用程式 (目前不支援指定為市集連結的應用程式)。 不允許在裝置上執行其他應用程式。
-     **螢幕睡眠按鈕** - 啟用或停用裝置上的螢幕睡眠喚醒按鈕。
-     **音量按鈕** - 啟用或停用裝置上的音量按鈕。


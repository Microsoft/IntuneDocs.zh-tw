---
title: "Android 的 Intune 裝置限制設定"
titleSuffix: Intune Azure preview
description: "Intune Azure 預覽版︰了解 Android 裝置上可用以控制裝置設定與功能的 Intune 設定。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 03/29/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6bdf714a-5d93-485c-8b52-513635c60cb6
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: f316b332c3f1b80b9d6af488943298fcfea13741
ms.openlocfilehash: 009c6491b8ce457a371f5db31de3f122fa41fb95
ms.lasthandoff: 03/30/2017


---

# <a name="android-and-samsung-knox-standard-device-restriction-settings-in-microsoft-intune"></a>Microsoft Intune 中的 Android 與 Samsung KNOX Standard 裝置限制設定

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

## <a name="general"></a>一般

|||||
|-|-|-|-|
|設定名稱|詳細資料|Android 4.0+|Samsung KNOX Standard|
|**相機**|允許使用裝置相機。|是|是|
|**複製及貼上**|允許裝置上的複製及貼上功能。|否|是|
|**應用程式之間的剪貼簿共用**|允許使用剪貼簿在應用程式之間複製並貼上。|否|是|
|**診斷資料提交**|讓使用者無法從裝置送出診斷資料。|否|是|
|**重設為原廠設定**|允許使用者在裝置上重設為原廠設定。|否|是|
|**地理位置**|允許裝置可利用位置資訊 (僅限 Samsung KNOX Standard)。|否|是|
|**關閉電源**|可讓使用者關閉裝置電源。<br>如果停用此設定，Samsung KNOX Standard 裝置的 [登入失敗幾次後即抹除裝置] 設定將無法運作。|否|是|
|**螢幕擷取**|讓使用者擷取螢幕內容做為映像。|否|是|
|**語音助理**|允許在裝置上使用語音助理軟體。|否|是|
|**YouTube**|允許在裝置上使用 YouTube 應用程式。|否|是|

## <a name="password"></a>密碼

|||||
|-|-|-|-|
|設定名稱|詳細資料|Android 4.0+|Samsung KNOX Standard|
|**密碼**|需要使用者輸入密碼才可存取該裝置。|是|是|
|**密碼最小長度**|輸入使用者必須設定的密碼長度下限 (介於 4 到 16 個字元之間)。|是|是|
|**在停止活動最少幾分鐘後鎖定螢幕**|指定裝置自動鎖定之前，需停止活動達幾分鐘。|是|是|
|**登入失敗幾次後即抹除裝置**|指定抹除裝置前允許的登入失敗次數。|是|是|
|**密碼到期 (天數)**|指定必須變更裝置密碼的天數。|是|是|
|**必要的密碼類型**|指定所需的密碼複雜性等級，以及是否可以使用生物識別裝置。|是|是|
|**不得重複使用以前用過的密碼**|讓使用者無法建立以前用過的密碼。|是|是|
|**指紋解除鎖定**|允許使用指紋來解除鎖定受支援的裝置。|否|是|
|**Smart Lock 與其他信任代理程式**|可讓您控制相容的 Android 裝置 (Samsung KNOX Standard 5.0 及更新版本) 上的 Smart Lock 功能。 此電話功能 (有時也稱為信任代理程式) 可讓您在裝置位於受信任的位置 (例如連線到特定的藍牙裝置或靠近 NFC 標記) 時，停用或略過裝置鎖定畫面密碼。您可以使用此設定來防止使用者設定 Smart Lock。|是 (5.0 和更新版本)|否|
|**加密**|裝置上的檔案需要加密。|是|是|

## <a name="google-play-store"></a>Google Play 商店

|||||
|-|-|-|-|
|設定名稱|詳細資料|Android 4.0+|Samsung KNOX Standard|
|**Google Play 商店**|允許使用者在裝置上存取 Google Play 商店|否|是|

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
|||||
|-|-|-|-|
|設定名稱|詳細資料|Android 4.0+|Samsung KNOX Standard|
|**網頁瀏覽器**|指定是否可使用裝置的預設網頁瀏覽器。|否|是|
|**自動填寫**|允許使用網頁瀏覽器的自動填入功能。|否|是|
|**Cookie**|允許裝置的網頁瀏覽器使用 Cookie。|否|是|
|**Javascript**|允許裝置網頁瀏覽器執行 Java 指令碼。|否|是|
|**快顯視窗**|允許在網頁瀏覽器中使用快顯封鎖程式。|否|是|

## <a name="cloud-and-storage"></a>雲端與儲存體
|||||
|-|-|-|-|
|設定名稱|詳細資料|Android 4.0+|Samsung KNOX Standard|
|**Google 備份**|允許使用 Google 備份。|否|是|
|**Google 帳戶自動同步處理**|允許自動同步處理 Google 帳戶設定。|否|是|
|**卸除式存放裝置**|允許裝置使用卸除式存放裝置，例如 SD 記憶卡。|否|是|
|**儲存卡加密**|指定裝置儲存卡是否必須加密。|否|是|

## <a name="cellular-and-connectivity"></a>行動數據與連線
|||||
|-|-|-|-|
|設定名稱|詳細資料|Android 4.0+|Samsung KNOX Standard|
|**數據漫遊**|允許裝置在使用行動電話通訊網路時進行數據漫遊。|否|是|
|**SMS/MMS 傳訊**|允許在裝置上使用 SMS 和多媒體簡訊。|否|是|
|**語音撥號**|在裝置上啟用或停用語音撥號功能。|否|是|
|**語音漫遊**|允許裝置在行動電話通訊網路時進行語音漫遊。|否|是|
|**Bluetooth**|允許在裝置上使用藍牙。|否|是|
|**NFC**|允許使用近距離無線通訊的操作 (如果裝置支援)。|否|是|
|**Wi-Fi**|允許使用裝置的 Wi-Fi 功能。|否|是|
|**Wi-Fi 網際網路共用功能**|允許使用裝置的 Wi-Fi 網際網路共用功能。|否|是|

## <a name="kiosk"></a>Kiosk
|||||
|-|-|-|-|
|設定名稱|詳細資料|Android 4.0+|Samsung KNOX Standard|
|**選取受管理的應用程式**|瀏覽到應用程式，然後選取當裝置為 Kiosk 模式時可執行的受管理應用程式 (目前不支援指定為市集連結的應用程式)。 不允許在裝置上執行其他應用程式。|否|是|
|**螢幕睡眠按鈕**|啟用或停用裝置上的喚醒螢幕睡眠按鈕。|否|是|
|**音量按鈕**|啟用或停用裝置上的音量按鈕。|否|是|


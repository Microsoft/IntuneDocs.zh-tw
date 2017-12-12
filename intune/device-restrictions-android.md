---
title: "Android 的 Intune 裝置限制設定"
titlesuffix: Azure portal
description: "了解 Android 裝置上可用以控制裝置設定與功能的 Intune 設定。"
keywords: 
author: vhorne
ms.author: victorh
manager: angrobe
ms.date: 09/07/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6bdf714a-5d93-485c-8b52-513635c60cb6
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: ffddf9e5fcdf8359c729eb048a6f8052a1b3286f
ms.sourcegitcommit: 3b397b1dcb780e2f82a3d8fba693773f1a9fcde1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/12/2017
---
# <a name="android-and-samsung-knox-standard-device-restriction-settings-in-microsoft-intune"></a>Microsoft Intune 中的 Android 與 Samsung KNOX Standard 裝置限制設定

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

搭配 Android 裝置限制原則使用這些設定，來設定您組織中的裝置。

>[!TIP]
>如果沒有您想要的設定，您可以使用[自訂設定檔](custom-settings-android.md)來設定裝置。 

## <a name="general"></a>一般

- **相機** - 允許使用裝置的相機。
- **複製並貼上 (僅限 Samsung KNOX)** - 允許裝置上的複製及貼上功能。
- **應用程式之間的剪貼簿共用 (僅限 Samsung KNOX)** - 允許使用剪貼簿在應用程式之間複製並貼上。
- **診斷資料提交 (僅限 Samsung KNOX)** - 讓使用者無法從裝置提交診斷資料。
- **恢復出廠預設值 (僅限 Samsung KNOX)** - 可讓使用者在裝置上執行原廠重設。
- **地理位置 (僅限 Samsung KNOX)** - 允許裝置使用位置資訊。
- **關閉電源 (僅限 Samsung KNOX)** - 可讓使用者關閉裝置電源。<br>如果停用，就無法設定**登入失敗幾次後即抹除裝置**。
- **螢幕擷取 (僅限 Samsung KNOX)** - 讓使用者將螢幕內容擷取成影像。
- **語音助理 (僅限 Samsung KNOX)** - 允許在裝置上使用語音助理軟體。
- **YouTube (僅限 Samsung KNOX)** - 允許在裝置上使用 YouTube 應用程式。
- **共用的裝置 (僅限 Samsung KNOX)** - 將受管理的 Samsung KNOX Standard 裝置設定為共用。 在此模式中，使用者可以利用他們的 Azure AD 認證登入和登出裝置。 裝置不論是否處於使用狀態，都會維持受管理狀態。<br>搭配 SCEP 憑證設定檔使用時，此功能可讓使用者共用具有所有使用者應用程式集的裝置，但他們要使用自己的 SCEP 使用者憑證。當使用者登出時，會清除所有應用程式資料。  此功能僅限於 LOB 應用程式。

## <a name="password"></a>密碼

- **密碼** - 需要終端使用者輸入密碼才可存取該裝置。|是|是|
- **密碼長度下限** - 輸入使用者必須設定的密碼長度下限 (介於 4 到 16 個字元)。
- **沒有活動最久幾分鐘後鎖定螢幕** - 指定沒有任何活動幾分鐘之後，自動鎖定裝置。
- **登入失敗幾次後即抹除裝置** - 指定抹除裝置前允許的登入失敗次數。
- **密碼到期 (天數)** - 指定多少天後必須變更裝置密碼。
-  **必要的密碼類型** - 指定所需的密碼複雜度等級，以及是否可以使用生物識別裝置。 從下列選項進行選擇：
    - **裝置預設**
    - **低安全性生物識別**
    - **至少包含數字**
    - **複雜數字** - 不允許重複或連續的數字，例如 '1111' 或 '1234'<sup>1</sup>
    - **至少包含字母**
    - **至少包含英數字元**
    - **至少包含英數字元和符號**
- **避免重複使用先前的密碼** - 讓使用者無法建立以前用過的密碼。
- **指紋解除鎖定 (僅限 Samsung KNOX)** - 允許使用指紋來解除鎖定受支援的裝置。
- **Smart Lock 與其他信任代理程式** - 可讓您控制相容的 Android 裝置 (Samsung KNOX Standard 5.0 及更新版本) 上的 Smart Lock 功能。 此電話功能 (有時稱為信任代理程式) 可讓您在裝置位於受信任的位置時，停用或略過裝置鎖定畫面密碼。 例如，當裝置連線到特定的藍牙裝置或靠近 NFC 標記時，就能使用此功能。 您可以使用此設定來防止使用者設定 Smart Lock。
- **加密** - 需要加密裝置上的檔案。

<sup>1</sup> 在您將此設定指派至裝置之前，請確定會將這些裝置上的公司入口網站應用程式更新至最新版本。

如果您設定 [複雜數字] 設定，然後將它指派至執行早於 5.0 之 Android 版本的裝置，則將適用下列行為。
- 如果公司入口網站應用程式的版本早於 1704，就不會將任何 PIN 原則套用至裝置，且 Azure 入口網站中會顯示錯誤。
- 如果公司入口網站應用程式執行 1704 版或更新版本，則只能套用簡單的 PIN。 早於 5.0 的 Android 版本並不支援此設定。 Azure 入口網站中將不會顯示錯誤。


## <a name="google-play-store"></a>Google Play 商店

- **Google Play 商店 (僅限 Samsung KNOX)** - 可讓使用者在裝置上存取 Google Play 商店。

## <a name="restricted-apps"></a>受限應用程式

在受限應用程式清單中，您可以針對 Android 和 Samsung KNOX Standard 裝置設定下列其中一個清單：

**禁止的應用程式**清單：列出使用者安裝與執行時將會回報的應用程式 (並非由 Intune 管理)。
**核准的應用程式**清單 - 列出允許使用者安裝的應用程式。 為了持續符合規範，使用者絕不能安裝其他應用程式。 自動允許 Intune 所管理的應用程式。
包含受限應用程式設定的裝置設定檔，必須指派給使用者群組。

若要設定清單，請按一下 [新增]，然後在應用程式市集中，指定您所選的名稱 (也可指定選用的應用程式發行者) 以及應用程式的 URL。

### <a name="how-to-specify-the-url-to-an-app-in-the-store"></a>如何在市集中指定應用程式的 URL

若要在相容或不相容應用程式清單中指定應用程式 URL，請採取下列步驟︰

在 [Google Play 商店的 [應用程式] 區段](https://play.google.com/store/apps)中，搜尋您要使用的應用程式。

開啟應用程式的安裝頁面，然後將 URL 複製到剪貼簿。 您現在可以在符合規範或不符合規範的應用程式清單中使用此 URL。

範例：在 Google Play 中搜尋 Microsoft Office Mobile。 使用 URL：**https://play.google.com/store/apps/details?id=com.microsoft.office.officehub**。

### <a name="additional-options"></a>其他選項

您也可以按一下 [匯入]，從 csv 檔案取得清單。 請使用 <應用程式 URL>、<應用程式名稱>、<應用程式發行者> 格式，或在包含相同格式之受限應用程式清單內容的 csv 檔案中按一下 [匯出]。      

## <a name="browser"></a>瀏覽器

- **網頁瀏覽器 (僅限 Samsung KNOX)** - 指定是否可使用裝置的預設網頁瀏覽器。
- **自動填入 (僅限 Samsung KNOX)** - 允許使用網頁瀏覽器的自動填入功能。
- **Cookie (僅限 Samsung KNOX)** - 允許裝置的網頁瀏覽器使用 Cookie。
- **JavaScript (僅限 Samsung KNOX)** - 允許裝置的網頁瀏覽器執行 Java 指令碼。
- **快顯 (僅限 Samsung KNOX)** - 允許在網頁瀏覽器中使用快顯封鎖程式。

## <a name="allow-or-block-apps"></a>允許或封鎖應用程式

針對執行 Samsung KNOX Standard 的裝置，這些設定可以用來指定只能在這些裝置上安裝或啟動的應用程式。
此外，您還可以指定將會對裝置使用者隱藏的已安裝應用程式。 使用者將無法執行這些應用程式。

- **允許安裝的應用程式 (僅限 Samsung KNOX Standard)**
- **禁止應用程式啟動 (僅限 Samsung KNOX Standard)**
- **不對使用者顯示應用程式 (僅限 Samsung KNOX Standard)**

針對每個設定，使用下列其中一項來設定應用程式清單：

- **依套件名稱新增應用程式**：主要用於商務營運應用程式。 輸入應用程式名稱，以及應用程式套件的名稱。 
- **依 URL 新增應用程式**：輸入應用程式名稱，及其在 Google Play 商店中的 URL。
- **新增受管理的應用程式**：從您使用 Intune 管理的應用程式清單，選取您需要的應用程式。

## <a name="cloud-and-storage"></a>雲端與儲存體

- **Google 備份 (僅限 Samsung KNOX)** - 允許使用 Google 備份。
- **Google 帳戶自動同步 (僅限 Samsung KNOX)** - 允許自動同步處理 Google 帳戶設定。
- **抽取式存放裝置 (僅限 Samsung KNOX)** - 允許裝置使用抽取式存放裝置，例如 SD 記憶卡。
- **加密儲存卡上的內容 (僅限 Samsung KNOX)** - 指定是否必須加密裝置儲存卡。

## <a name="cellular-and-connectivity"></a>行動數據與連線

- **數據漫遊 (僅限 Samsung KNOX)** - 允許裝置在行動電話通訊網路時進行數據漫遊。
- **簡訊/多媒體簡訊傳訊 (僅限 Samsung KNOX)** - 允許在裝置上使用簡訊和多媒體簡訊傳訊。
- **語音撥號 (僅限 Samsung KNOX)** - 在裝置上啟用或停用語音撥號功能。
- **語音漫遊 (僅限 Samsung KNOX)** - 允許裝置在行動電話通訊網路時進行語音漫遊。
- **藍牙 (僅限 Samsung KNOX)** - 允許在裝置上使用藍牙。
- **NFC (僅限 Samsung KNOX)** - 允許在支援裝置上使用近距離無線通訊的操作。
- **Wi-Fi (僅限 Samsung KNOX)** - 允許在裝置上使用 Wi-Fi 功能。
- **Wi-Fi 網際網路共用功能 (僅限 Samsung KNOX)** - 允許在裝置上使用 Wi-Fi 網際網路共用功能。

## <a name="kiosk"></a>Kiosk

Kiosk 設定僅套用至 Samsung KNOX Standard 裝置，且只套用至您使用 Intune 管理的應用程式。

- **選取受管理的應用程式**：選擇下列其中一個選項，以新增當裝置處於 Kiosk 模式時可執行的一或多個受管理的應用程式。 不允許在裝置上執行其他應用程式。
    - **依套件名稱新增應用程式**
    - **依 URL 新增應用程式**
    - **新增受管理的應用程式**。
- **螢幕睡眠按鈕** - 啟用或停用裝置上的喚醒螢幕睡眠按鈕。
- **音量按鈕** - 啟用或停用裝置上的音量按鈕。


## <a name="next-steps"></a>後續步驟

繼續使用[如何設定裝置限制設定](device-restrictions-configure.md)中的指示建立裝置限制設定檔，然後進行指派。

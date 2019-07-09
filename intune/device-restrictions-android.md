---
title: Microsoft Intune 中 Android 的裝置限制設定 | Microsoft Docs
description: 查看您可以在 Microsoft Intune 中控制及限制之所有 Android 裝置設定的清單。 使用這些設定來控制密碼、存取 Google Play、允許或禁止應用程式、控制瀏覽器設定、封鎖應用程式、備份至 Google 雲端，以及控制訊息、語音、數據漫遊、Wi-Fi 及藍牙連線選項。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/13/2018
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: ayesham, chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9ac25a0f3305cdfac9f3eeaa75b9e2106b3571b0
ms.sourcegitcommit: ede86a3cb094c12e3e218b956abb9935bec76902
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 07/05/2019
ms.locfileid: "67572507"
---
# <a name="android-and-samsung-knox-standard-device-restriction-settings-lists-in-intune"></a>Intune 中的 Android 與 Samsung Knox Standard 裝置限制設定

本文將告訴您所有的 Microsoft Intune 裝置限制設定，讓您可以為執行 Android 的裝置進行設定。

>[!TIP]
>如果沒有您想要的設定，您可以使用[自訂設定檔](custom-settings-android.md)來設定裝置。

## <a name="general"></a>一般

- **相機**：選擇 [封鎖]  來禁止存取相機。 [未設定]  允許存取裝置的相機。
- **複製並貼上 (僅 Samsung Knox)** ：選擇 [封鎖]  以防止複製並貼上。 [未設定]  允許使用裝置上的複製和貼上功能。
- **應用程式之間的剪貼簿共用 (僅限 Samsung Knox)** ：選擇 [封鎖]  以防止使用剪貼簿在應用程式之間複製並貼上。 [未設定]  允許使用剪貼簿在應用程式之間複製並貼上。
- **診斷資料提交 (僅限 Samsung Knox)** ：選擇 [封鎖]  讓使用者無法從裝置提交診斷資料。 [未設定]  允許使用者提交資料。
- **抹除 (僅限 Samsung Knox)** ：可讓使用者在裝置上執行[抹除](devices-wipe.md)動作。
- **地理位置 (僅限 Samsung Knox)** ：選擇 [封鎖]  以停用此裝置使用位置資訊。 [未設定]  允許裝置利用位置資訊。
- **關閉電源 (僅限 Samsung Knox)** ：選擇 [封鎖]  以防止使用者關閉裝置電源。 如果已停用此設定，則無法設定 [登入失敗幾次後即抹除裝置]  設定，也無法運作。 [未設定]  允許使用者關閉裝置的電源。
- **螢幕擷取 (僅限 Samsung Knox)** ：選擇 [封鎖]  以防止螢幕擷取畫面。 [未設定]  讓使用者可擷取螢幕內容做成影像。
- **語音助理 (僅限 Samsung Knox)** ：選擇 [封鎖]  以停用 S 語音服務。 [未設定]  允許在裝置上使用 S 語音服務和應用程式。 此設定不適用於 Bixby 或用於大聲讀取螢幕內容的語音助理。
- **YouTube (僅限 Samsung Knox)** ：選擇 [封鎖]  以防止使用者使用 YouTube 應用程式。 [未設定]  允許在裝置上使用 YouTube 應用程式。
- **共用的裝置 (僅限 Samsung Knox)** ：將受控 Samsung Knox Standard 裝置設定為共用。 設定為**允許**時，使用者可以利用他們的 Azure AD 認證登入和登出裝置。 裝置不論是否處於使用狀態，都會維持受控狀態。</br>搭配 SCEP 憑證設定檔使用時，此功能可讓使用者針對所有使用者共用相同應用程式的裝置。 但是，每個使用者都有自己的 SCEP 使用者憑證。 當使用者登出時，會清除所有應用程式資料。 此功能僅限於 LOB 應用程式。 </br>[未設定]  可避免多個使用者使用其 Azure AD 認證在裝置上登入公司入口網站應用程式。
- **封鎖日期和時間變更 (Samsung Knox)** ：選擇 [封鎖]  以防止使用者在裝置上變更日期和時間設定。 [未設定]  可讓使用者變更日期和時間設定。

## <a name="password"></a>密碼

- **密碼**：**要求**使用者輸入密碼才可存取該裝置。 [未設定]  可讓使用者存取裝置，而不需要輸入密碼。

    > [!NOTE]
    > Samsung Knox 裝置在 MDM 註冊期間會自動要求 4 位數的 PIN。 原生 Android 裝置可能會自動要求 PIN，以符合條件式存取。

- **密碼長度下限**：輸入使用者必須輸入的密碼長度下限 (介於 4 到 16 個字元之間)。
- **在停止活動最少幾分鐘後鎖定螢幕** ：輸入裝置上沒有任何活動最久幾分鐘後鎖定螢幕。 在裝置上，使用者無法在設定檔中設定大於已設定時間的時間值。 使用者可以設定較低的時間值。 例如，如果設定檔設定為 15 分鐘，則使用者可以將值設定為 5 分鐘。 使用者無法將值設定為 30 分鐘。 
- **登入失敗幾次後即抹除裝置**：輸入抹除裝置前允許的登入失敗次數。
- **密碼到期 (天數)** ：輸入多少天後必須變更裝置密碼。
- **必要的密碼類型**：輸入所需的密碼複雜度等級，以及是否可以使用生物識別裝置。 選項包括：
  - **裝置預設**
  - **低安全性生物識別**
  - **至少包含數字**
  - **複雜數字**：不允許重複或連續的數字，例如 "1111" 或 "1234"。<sup>1</sup>
  - **至少包含字母**
  - **至少包含英數字元**
  - **至少包含英數字元和符號**
- **避免重複使用先前的密碼**：讓使用者無法建立以前用過的密碼。
- **指紋解除鎖定 (僅限 Samsung Knox)** ： 選擇**區塊**以防止使用指紋來解除鎖定裝置。 [未設定]  允許使用者使用指紋將裝置解除鎖定。
- **Smart Lock 與其他信任代理程式**：選擇 [封鎖]  以防止 Smart Lock 或其他信任代理程式調整鎖定畫面設定 (Samsung KNOX Standard 5.0 +)。 此電話功能 (也稱為信任代理程式) 可讓您在裝置位於受信任的位置時，停用或略過裝置鎖定畫面密碼。 例如，當裝置連線到特定的藍牙裝置或靠近 NFC 標記時，就能使用此功能。 您可以使用此設定來防止使用者設定 Smart Lock。
- **加密** - 選擇 [需要]  ，以便加密裝置上的檔案。 並非所有裝置都支援加密。 若要使用此功能，也請： 
  1. 將 [密碼]  設定為 [需要]  。
  2. 將 [必要的密碼類型]  設定為 [至少包含數字]  。
  3. 將**最小密碼長度**設定為至少 4，以正確報告這項設定的合規性。

  > [!NOTE]
  > 如果實施加密原則，Samsung Knox 裝置會要求使用者設定一個六個字元的複雜密碼來作為裝置密碼。

<sup>1</sup> 在您將此設定指派至裝置之前，請確定會將這些裝置上的公司入口網站應用程式更新至最新版本。

如果您將**必要的密碼類型**設定為**複雜數字**，然後將它指派至執行早於 5.0 之 Android 版本的裝置，則將適用下列行為：

- 如果公司入口網站應用程式的版本早於 1704，就不會將任何 PIN 原則套用至裝置，且 Azure 入口網站中會顯示錯誤。
- 如果公司入口網站應用程式執行 1704 版或更新版本，則只能套用簡單的 PIN。 早於 5.0 的 Android 版本並不支援此設定。 Azure 入口網站不會顯示錯誤。

## <a name="google-play-store"></a>Google Play 商店

- **Google Play 商店 (僅限 Samsung Knox)** ：選擇 [封鎖]  以防止使用者使用 Google Play 商店。 [未設定]  允許使用者在裝置上存取 Google Play 商店。

## <a name="restricted-apps"></a>受限應用程式

使用這些設定來允許或防止裝置上的特定應用程式。 Android 和 Samsung Knox Standard 裝置上支援此功能：

- **禁止的應用程式**：由 Intune 管理，且您不希望在裝置上安裝的應用程式清單。 如果使用者安裝此清單中的應用程式，則 Intune 會通知您。
- **核准的應用程式**：允許使用者安裝的應用程式清單。 若要持續符合規範，使用者絕不能安裝其他應用程式。 自動允許 Intune 所管理的應用程式。

若要將應用程式新增至這些清單中，您可以：

- **新增**所需應用程式的 Google Play 商店 URL。 例如，如果您想要新增適用於 Android 的 Microsoft 遠端桌面應用程式，請輸入 `https://play.google.com/store/apps/details?id=com.microsoft.rdc.android`。 若要尋找應用程式的 URL，請開啟 [Google Play 商店](https://play.google.com/store/apps)，然後搜尋該應用程式。 例如，搜尋 `Microsoft Remote Desktop Play Store` 或 `Microsoft Planner`。 選取應用程式，並複製 URL。
- 匯入 CSV 檔案的應用程式，包括 URL 的相關詳細資料。 使用 <*app url*>、<*app name*>、<*app publisher*> 格式。 或者，以相同格式**匯出**包含受限應用程式清單的現有清單。

> [!IMPORTANT]
> 使用受限應用程式設定的裝置設定檔，必須指派給使用者群組。

## <a name="browser"></a>瀏覽器

- **網頁瀏覽器 (僅限 Samsung Knox)** ：選擇 [封鎖]  以防止在裝置上使用預設網頁瀏覽器。 [未設定]  允許使用裝置的預設網頁瀏覽器。
- **自動填入 (僅限 Samsung Knox)** ：選擇 [封鎖]  以防止在瀏覽器中自動填寫文字。 [未設定]  允許使用網頁瀏覽器的自動填寫功能。
- **Cookie (僅限 Samsung Knox)** ：選擇您希望如何處理裝置上來自網站的 Cookie。 選項包括：
  - Allow
  - 封鎖所有 Cookie
  - 允許來自瀏覽網站的 Cookie
  - 允許來自目前網站的 Cookie
- **Javascript (僅限 Samsung Knox)** ：選擇 [封鎖]  以防止網頁瀏覽器執行 Java 指令碼。 [未設定]  允許裝置 Web 瀏覽器執行 Java 指令碼。
- **快顯 (僅限 Samsung Knox)** ：選擇 [封鎖]  以防止網頁瀏覽器的快顯視窗。 [未設定]  允許網頁瀏覽器的快顯視窗。

## <a name="allow-or-block-apps"></a>允許或封鎖應用程式

使用這些設定在 Samsung Knox Standard 裝置上允許、封鎖或隱藏特定應用程式。 使用者無法開啟或執行隱藏的應用程式。

選項包括：

- **允許安裝的應用程式 (僅限 Samsung Knox Standard)**
- **禁止應用程式啟動 (僅限 Samsung Knox Standard)**
- **不對使用者顯示應用程式 (僅限 Samsung Knox Standard)**

針對每個設定，新增應用程式清單。 選項包括：

- **依套件名稱新增應用程式**：主要用於企業營運應用程式。 輸入應用程式名稱，以及應用程式套件的名稱。
- **依 URL 新增應用程式**：輸入應用程式名稱，及其在 Google Play 商店中的 URL。
- **新增市集應用程式**：從您在 Intune 中管理的應用程式清單中選取一個應用程式。

## <a name="cloud-and-storage"></a>雲端與儲存體

- **Google 備份 (僅限 Samsung Knox)** ：選擇 [封鎖]  以防止裝置同步至 Google 備份。 [未設定]  允許使用 Google 備份。
- **Google 帳戶自動同步 (僅限 Samsung Knox)** ：選擇**封鎖**以防止裝置上的 Google 帳戶自動同步處理功能。 [未設定]  允許自動同步處理 Google 帳戶設定。
- **卸除式存放裝置 (僅限 Samsung Knox)** ：選擇**封鎖**以防止裝置使用卸除式存放裝置。 [未設定]  允許裝置使用卸除式存放裝置，例如 SD 記憶卡。
- **加密儲存卡上的內容 (僅限 Samsung Knox)** ：[需要]  會強制執行裝置儲存卡必須加密。 [未設定]  允許使用未加密的儲存卡。 並非所有裝置都支援儲存卡加密。 若要確認，請與裝置製造商聯繫。

## <a name="cellular-and-connectivity"></a>行動數據與連線

- **數據漫遊 (僅限 Samsung Knox)** ： 選擇**區塊**禁止在行動電話通訊網路上漫遊的資料。 [未設定]  允許裝置在行動電話通訊網路時進行數據漫遊。
- **簡訊/多媒體簡訊傳訊 (僅限 Samsung Knox)** ：選擇 [封鎖]  以防止在裝置上使用簡訊和多媒體簡訊傳訊。 [未設定]  允許在裝置上使用簡訊和多媒體簡訊傳訊。
- **語音撥號 (僅限 Samsung Knox)** ：選擇 [封鎖]  以防止使用者在裝置上使用語音撥號功能。 [未設定]  允許在裝置上使用語音撥號功能。
- **語音漫遊 (僅限 Samsung Knox)** ：選擇 [封鎖]  以防止透過行動電話通訊網路進行語音漫遊。 [未設定]  允許裝置在行動電話通訊網路時進行語音漫遊。
- **藍牙 (僅限 Samsung Knox)** ：選擇 [封鎖]  以防止在裝置上使用藍牙。 [未設定]  允許在裝置上使用藍牙。
- **NFC (僅限 Samsung Knox)** ：選擇 [封鎖]  以停止近距離無線通訊 (NFC) 技術。 [未設定]  允許在支援裝置上使用近距離無線通訊的操作。
- **Wi-Fi (僅限 Samsung Knox)** ：選擇 [封鎖]  以防止在裝置上使用 Wi-Fi。 [未設定]  允許在裝置上使用 Wi-Fi 功能。
- **Wi-Fi 網際網路共用功能 (僅限 Samsung Knox)** ：選擇 [封鎖]  以防止在裝置上使用 Wi-Fi 網際網路共用功能。 [未設定]  允許使用裝置的 Wi-Fi 網際網路共用功能。

## <a name="kiosk"></a>Kiosk

Kiosk 設定僅套用至 Samsung Knox Standard 裝置，且只套用至您使用 Intune 管理的應用程式。

- 新增您想要在裝置處於 kiosk 模式時執行的應用程式。 在 kiosk 模式中，只會執行您新增的應用程式；未新增的應用程式無法執行。 當裝置處於 kiosk 模式時，預先安裝的瀏覽器不會作為應用程式執行。 如果瀏覽器為必要項目，請考慮使用[受控瀏覽器](app-configuration-managed-browser.md)。

  您的應用程式選項：

  - **依套件名稱新增應用程式**：主要用於企業營運應用程式。 輸入應用程式名稱，以及應用程式套件的名稱。
  - **依 URL 新增應用程式**：輸入應用程式名稱，及其在 Google Play 商店中的 URL。
  - **新增市集應用程式**：從您在 Intune 中管理的應用程式清單中選取一個應用程式。

- **螢幕睡眠按鈕**：選擇 [封鎖]  以防止或隱藏螢幕睡眠按鈕。 [未設定]  允許裝置上的喚醒螢幕睡眠按鈕。
- **音量按鈕**：選擇 [封鎖]  以防止使用者藉由停用音量按鈕來調整音量。 [未設定]  允許在裝置上使用音量按鈕。

## <a name="next-steps"></a>後續步驟

[指派設定檔](device-profile-assign.md)並[監視其狀態](device-profile-monitor.md)。

您也可以為 [Android Enterprise](device-restrictions-android-for-work.md#dedicated-device-settings) 和 [Windows 10](kiosk-settings.md) 裝置建立 kiosk 設定檔。

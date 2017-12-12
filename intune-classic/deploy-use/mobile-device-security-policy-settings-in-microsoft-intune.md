---
title: "行動裝置安全性原則設定"
description: "使用 Intune 來設定各種不同的設定，您可以部署到組織中受管理的裝置。"
keywords: 
author: vhorne
ms.author: victorh
manager: angrobe
ms.date: 11/02/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e5ab3b76-08af-4893-b294-fb6627fdc4c6
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: fa86e50ebf7e65be0ce8ace65e2cb0bc7e38658e
ms.sourcegitcommit: 3b397b1dcb780e2f82a3d8fba693773f1a9fcde1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/12/2017
---
# <a name="mobile-device-security-policy-settings-in-microsoft-intune"></a>Microsoft Intune 的行動裝置安全性原則設定

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

> [!IMPORTANT]
> Microsoft Intune 現在具有區隔每個裝置平台之設定原則的功能。 這些原則包含您可以使用的最新設定。 您可以繼續使用行動裝置安全性原則，現有的部署也還能運作。 然而，因為行動裝置安全性原則未來將予移除，所以您應及早規劃改用新的設定原則。

您可以使用 Intune 行動裝置安全性原則，設定可部署到組織中受管理裝置的多種設定。 這些設定是用來控制裝置的功能和安全性。

您可以建立和部署下列裝置類型的行動裝置安全性原則：

-   Windows RT 8.1 和已註冊的 Windows 8.1 裝置

-   Windows RT

-   Windows Phone 8 和 Windows Phone 8.1

-   iOS

-   Android 和 Samsung KNOX Standard

> [!NOTE]
> 某些設定不適用於某些裝置。 請參閱下表，以取得您可設定的完整設定清單。
> Microsoft Intune 自 2016 年 10 月起會取代 Windows 8 公司入口網站應用程式的支援。 Microsoft Intune 也會取代 Windows Phone 8 和 WinRT 平台的支援。 因此，您將無法註冊或更新任何 Windows Phone 8 或 WinRT 裝置。 您可以繼續管理已註冊的 Windows Phone 8、WinRT 和 Windows 8 裝置。 將 Windows Phone 8 和 Windows 8 裝置更新為 Windows 8.1 和 Windows Phone 8.1，並使用對應的 Windows 8.1 和 Windows Phone 8.1 公司入口網站應用程式繼續將應用程式發佈至這些裝置，而不受中斷。

## <a name="security-settings"></a>安全性設定

|設定名稱|Windows 8.1 和 Windows RT 8.1|Windows RT|Windows Phone 8 和 Windows Phone 8.1|iOS|Android 和 Samsung KNOX Standard|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**需要密碼才可解除鎖定行動裝置**|否|否|是|是|是|
|**所需的密碼類型**<br /><br />此設定指定必要密碼的類型，例如只可包含數字，或必須是英數字元等等。|是|是|是|是|否|
|**需要的密碼類型 – 最小字元集數**<br /><br />總共分為四種字元集：小寫字母、大寫字母、數字與符號。 此設定指定密碼中必須包含幾種不同的字元集。 然而，但對於 iOS 裝置，這會指定密碼中必須包含的符號字元數。|是|是|是|是|否|
|**最小密碼長度**|是|是|是|是|是|
|**允許簡單密碼**<br /><br />簡單密碼包括 '0000' 與 '1234'。|否|否|是|是|否|
|**抹除裝置前允許的重複登入失敗次數**|是|是|是|是|是|
|**在非使用狀態幾分鐘後會關閉螢幕**<sup>1</sup>|是|是|是|是|是|
|**密碼到期 (天數)**|是|是|是|是|是|
|**記住密碼歷程記錄**|是|是|是|是|是|
|**記住密碼歷程記錄** - **不得重複使用以前用過的密碼**|是|是|是|是|是|
|**密碼品質**|否|否|否|否|是|
|**允許圖片密碼和 PIN**|是|是|否|否|否|
|**在非使用狀態幾分鐘後需要輸入密碼**|否|否|否|是|否|
|**允許指紋解除鎖定**|否|否|否|iOS 7 及更新版本|否|
<sup>1</sup>針對 iOS 裝置，在您設定 [在非使用狀態幾分鐘後會關閉螢幕] 和 [在非使用狀態幾分鐘後需要輸入密碼] 設定時，將會依序套用這兩項設定。 例如，若您設定將兩項全都設定為 **5** 分鐘，螢幕將會自動在 5 分鐘後關閉，裝置將會在另一個 5 分鐘之後鎖定。 但使用者若是手動關閉螢幕，便會立即套用第二項設定。 在同一範例中，當使用者關閉螢幕之後，裝置將會在 5 分鐘後鎖定。

當您將密碼長度原則部署到執行 Windows RT 的裝置時，將會強制使用者重設其密碼—即使其目前的密碼符合原則需求也是一樣。

## <a name="encryption-settings"></a>加密設定

|設定名稱|Windows 8.1 和 Windows RT 8.1|Windows RT|Windows Phone 8 和 Windows Phone 8.1|iOS|Android 和 Samsung KNOX Standard|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**行動裝置需要加密**<sup>1</sup><br /><br />對於 Windows Phone 8 裝置，您必須將此項目設定為 [是] 。<br /><br />若要在 iOS 裝置上啟用加密，可啟用 [需要密碼來解除鎖定行動裝置] 設定。|是|否|是|否|是|
|**儲存卡需要加密**<br /><br />此設定同時也適用於 Exchange ActiveSync 管理的裝置。|n/a|n/a|n/a <br />應用程式及相關聯的資料會自動加密。|n/a|是|
<sup>1</sup>以下是執行 Windows 8.1 之裝置的其他資訊：

-   若要在執行 Windows 8.1 的裝置上強制加密，您必須在每個裝置上安裝 [2014 年 12 月適用於 Windows 的 MDM 用戶端更新](http://support.microsoft.com/kb/3013816) 。

-   如果您針對 Windows 8.1 裝置啟用此設定，則裝置的所有使用者必須都具有 Microsoft 帳戶。

-   為了進行加密，裝置必須符合 Microsoft [InstantGo](http://blogs.windows.com/bloggingwindows/2014/06/19/instantgo-a-better-way-to-sleep/) 硬體認證需求。

-   當您在裝置上強制加密時，就只能從使用者 Microsoft 帳戶存取修復金鑰，該帳戶是從其 OneDrive 帳戶進行存取的。 您無法代表使用者修復此金鑰。

## <a name="malware-settings"></a>惡意程式碼設定

|設定名稱|Windows 8.1 和 Windows RT 8.1|Windows RT|Windows Phone 8 和 Windows Phone 8.1|iOS|Android 和 Samsung KNOX Standard|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**需要網路防火牆**|是|否|否|否|否|
|**啟用 SmartScreen**|是|否|否|否|否|

## <a name="system-settings"></a>系統設定

|設定名稱|Windows 8.1 和 Windows RT 8.1|Windows RT|Windows Phone 8 和 Windows Phone 8.1|iOS|Android 和 Samsung KNOX Standard|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**需要自動更新**|是|否|否|否|否|
|**需要自動更新 - 自動安裝之更新的最小分類**<br /><br />選擇將自動安裝的更新分類：<br /><br />- **重要**。 安裝所有分類為重要的更新。<br /><br />- **建議**。 安裝所有分類為重要或建議的更新。|是|否|否|否|否|
|**允許螢幕擷取**|否|否|僅限 Windows Phone 8.1|是|是 (僅限 Samsung KNOX Standard)|
|**允許在鎖定畫面時使用控制中心**|否|否|否|iOS 7 及更新版本|否|
|**允許在鎖定畫面時使用通知檢視**|否|否|否|iOS 7 及更新版本|否|
|**允許在鎖定畫面時使用今日檢視**|否|否|否|iOS 7 及更新版本|否|
|**使用者帳戶控制**|是|否|否|否|否|
|**允許提交診斷資料**|是|否|僅限 Windows Phone 8.1|是|是 (僅限 Samsung KNOX Standard)|
|**允許未受信任的 TLS 憑證**|否|否|否|是|否|
|**鎖定時允許個人錢包軟體**|否|否|否|是|否|
|**允許原廠重設**|否|否|否|否|是 (僅限 Samsung KNOX Standard)|


## <a name="cloud-settings--documents-and-data"></a>雲端設定 – 文件和資料

|設定名稱|Windows 8.1 和 Windows RT 8.1|Windows RT|Windows Phone 8 和 Windows Phone 8.1|iOS|Android 和 Samsung KNOX Standard|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**允許備份至 iCloud**|否|否|否|是|否|
|**允許文件同步至 iCloud**|否|否|否|是|否|
|**允許相片串流同步至 iCloud**|否|否|否|是|否|
|**需要加密備份**|否|否|否|是|否|
|**工作資料夾 URL**<br /><br />此設定會設定工作資料夾的 URL，允許跨裝置同步處理文件。|是|否|否|否|否|
|**允許 Google 備份**|否|否|否|否|是 (僅限 Samsung KNOX Standard)|

## <a name="cloud-settings--accounts-and-synchronization"></a>雲端設定 – 帳戶和同步處理

|設定名稱|Windows 8.1 和 Windows RT 8.1|Windows RT|Windows Phone 8 和 Windows Phone 8.1|iOS|Android 和 Samsung KNOX Standard|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**允許 Microsoft 帳戶**|否|否|僅限 Windows Phone 8.1|否|否|
|**允許 Google 帳戶自動同步**|否|否|否|否|是 (僅限 Samsung KNOX Standard)|

## <a name="email-settings"></a>電子郵件設定

|設定名稱|Windows 8.1 和 Windows RT 8.1|Windows RT|Windows Phone 8 和 Windows Phone 8.1|iOS|Android 和 Samsung KNOX Standard|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**允許使用者下載電子郵件附件**<sup>1</sup>|n/a|n/a|n/a|n/a|n/a|
|**電子郵件同步處理期間** <br /><br />此設定同時也適用於 Exchange ActiveSync 管理的裝置。|n/a|n/a|n/a|n/a|n/a|
|**允許未完全支援這些設定的行動裝置與 Exchange 同步 (Exchange ActiveSync)** <br /><br />此設定同時也適用於 Exchange ActiveSync 管理的裝置。|n/a|n/a|n/a|n/a|n/a|
|**讓 Microsoft 帳戶變成 Windows Mail 應用程式的選用帳戶**|是|否|否|否|否|
|**允許自訂電子郵件帳戶**|否|否|僅限 Windows Phone 8.1|否|否|

## <a name="application-settings---browser"></a>應用程式設定 - 瀏覽器

|設定名稱|Windows 8.1 和 Windows RT 8.1|Windows RT|Windows Phone 8 和 Windows Phone 8.1|iOS|Android 和 Samsung KNOX Standard|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**允許網頁瀏覽器**|否|否|僅限 Windows Phone 8.1|是|是 (僅限 Samsung KNOX Standard)|
|**允許自動填滿**|是|否|否|是|是 (僅限 Samsung KNOX Standard)|
|**允許快顯封鎖程式**|是|否|否|是|是 (僅限 Samsung KNOX Standard)|
|**允許 Cookie**|否|否|否|是|是 (僅限 Samsung KNOX Standard)|
|**允許外掛程式**|是|否|否|否|否|
|**允許動態指令碼處理**|是|否|否|是|是 (僅限 Samsung KNOX Standard)|
|**允許詐騙警告**|是|否|否|是|否|
|**允許內部網路網站可輸入單一文字**<br /><br />(此設定可允許使用單一文字來將 Internet Explorer 導向某個網站 — 例如「Bing」。)|是|否|否|否|否|
|**允許自動偵測內部網路**|是|否|否|否|否|
|**網際網路的安全性等級**|是|否|否|否|否|
|**內部網路的安全性等級**|是|否|否|否|否|
|**信任的網站的安全性等級**|是|否|否|否|否|
|**限制的網站的安全性等級**|是|否|否|否|否|
|**傳送「不要追蹤」標頭**|是|否|否|否|否|
|**允許企業模式功能表存取**|是|否|否|否|否|
|**企業模式網站清單位置**|是|否|否|否|否|

## <a name="application-settings---apps"></a>應用程式設定 - 應用程式

|設定名稱|Windows 8.1 和 Windows RT 8.1|Windows RT|Windows Phone 8 和 Windows Phone 8.1|iOS|Android 和 Samsung KNOX Standard|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**允許應用程式市集**|否|否|僅限 Windows Phone 8.1|是|是 (僅限 Samsung KNOX Standard)|
|**需要密碼才可存取應用程式市集**|否|否|否|是|否|
|**允許應用程式內購買**|否|否|否|是|否|
|**允許在其他未受管理的應用程式中使用受管理的文件**|否|否|否|iOS 7 及更新版本|否|
|**允許在其他受管理應用程式中使用未受管理的文件**|否|否|否|iOS 7 及更新版本|否|
|**允許視訊會議**|否|否|否|是|否|
|**允許媒體市集中的成人內容**|否|否|否|是|否|
|**允許應用程式安裝**|否|否|否|iOS 6 和更新版本|否|

## <a name="application-settings---gaming"></a>應用程式設定 - 遊戲

|設定名稱|Windows 8.1 和 Windows RT 8.1|Windows RT|Windows Phone 8 和 Windows Phone 8.1|iOS|Android 和 Samsung KNOX Standard|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**允許遊戲中心朋友**|否|否|否|是|否|
|**允許多人連線遊戲**|否|否|否|是|否|

## <a name="device-capabilities-settings---hardware"></a>裝置功能設定 - 硬體

|設定名稱|Windows 8.1 和 Windows RT 8.1|Windows RT|Windows Phone 8 和 Windows Phone 8.1|iOS|Android 和 Samsung KNOX Standard|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**允許相機**|否|否|僅限 Windows Phone 8.1|是|是|
|**允許卸除式存放裝置**|否|否|是|否|是 (僅限 Samsung KNOX Standard)|
|**允許 Wi-Fi**|否|否|僅限 Windows Phone 8.1|否|是 (僅限 Samsung KNOX Standard)|
|**允許 Wi-Fi 網際網路共用功能**|否|否|僅限 Windows Phone 8.1|否|是 (僅限 Samsung KNOX Standard)|
|**允許自動連線到免費的 Wi-Fi 熱點**|否|否|僅限 Windows Phone 8.1|否|否|
|**允許 Wi-Fi 熱點回報**<br /><br />此設定傳送 Wi-Fi 連線的相關資訊，協助找出附近的連線。|否|否|僅限 Windows Phone 8.1|否|否|
|**允許地理位置**<br /><br />此設定允許裝置利用位置資訊。|否|否|僅限 Windows Phone 8.1|否|是 (僅限 Samsung KNOX Standard)|
|**允許 NFC**<br /><br />此設定允許使用近距離無線通訊的操作。|否|否|僅限 Windows Phone 8.1|否|是 (僅限 Samsung KNOX Standard)|
|**允許藍芽**|否|否|僅限 Windows Phone 8.1|否|是 (僅限 Samsung KNOX Standard)|
|**允許關閉電源**<br>如果已停用此設定，Samsung KNOX Standard 裝置的 [抹除裝置前允許的重複登入失敗次數] 設定無法運作。|否|否|否|否|是 (僅限 Samsung KNOX Standard)|

## <a name="device-capabilities-settings---cellular"></a>裝置功能設定 - 行動電話通訊

|設定名稱|Windows 8.1 和 Windows RT 8.1|Windows RT|Windows Phone 8 和 Windows Phone 8.1|iOS|Android 和 Samsung KNOX Standard|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**允許語音漫遊**|否|否|否|是|是 (僅限 Samsung KNOX Standard)|
|**允許數據漫遊**|是|否|否|是|是 (僅限 Samsung KNOX Standard)|
|**允許在漫遊時自動同步處理**|否|否|否|是|否|
|**允許 SMS/MMS 傳訊**|否|否|否|否|是 (僅限 Samsung KNOX Standard)|

## <a name="device-capabilities-settings---features"></a>裝置功能設定 - 功能

|設定名稱|Windows 8.1 和 Windows RT 8.1|Windows RT|Windows Phone 8 和 Windows Phone 8.1|iOS|Android 和 Samsung KNOX Standard|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**允許語音助理**|否|否|否|是|是 (僅限 Samsung KNOX Standard)|
|**允許在鎖定裝置時使用語音助理**|否|否|否|是|否|
|**允許語音撥號**|否|否|否|是|是 (僅限 Samsung KNOX Standard)|
|**允許複製並貼上**|否|否|僅限 Windows Phone 8.1|否|是 (僅限 Samsung KNOX Standard)|
|**允許應用程式之間的剪貼簿共用**|否|否|否|否|是 (僅限 Samsung KNOX Standard)|
|**允許 YouTube**|否|否|否|否|是 (僅限 Samsung KNOX Standard)|

### <a name="see-also"></a>請參閱
[使用 Microsoft Intune 原則管理裝置的設定及功能](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)

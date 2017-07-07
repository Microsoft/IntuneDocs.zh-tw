---
title: "Windows Phone 8.1 原則設定"
description: "Intune 提供一系列您可以在 Windows Phone 8.1 裝置上設定的內建一般設定。 此外，您可以指定 OMA-URI 值，來建立 Intune 未提供使用的自訂設定。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 10/11/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 83f7469c-272e-43f2-8139-b0d7bc34f43f
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 091c8c3867fffa2ba6857f79ae40ed618aaf0b72
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2017
---
# <a name="windows-phone-81-policy-settings-in-microsoft-intune"></a>Microsoft Intune 的 Windows Phone 8.1 原則設定

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Intune 提供一系列您可以在 Windows Phone 8.1 裝置上設定的內建一般設定。 此外，您可以指定開放行動聯盟的統一資源識別項 (OMA-URI) 值，來建立 Intune 未提供使用的自訂設定。

## <a name="general-configuration-settings"></a>一般組態設定

使用 Microsoft Intune **Windows Phone 一般設定原則 (Windows Phone 8.1 和更新版本)**，來設定適用於 Windows Phone 8.1 裝置的下列設定：

-   **行動裝置安全性設定** – 可從預先定義的設定清單中選擇，讓您可以控制裝置上某個功能範圍。

-   **相容與不相容的應用程式** - 指定公司中相容與不相容之應用程式的清單。 Windows Phone 裝置可以封鎖或允許這些應用程式的安裝。

### <a name="applicability-settings"></a>適用性設定

|設定名稱|詳細資料|
|----------------|----------------------------------|
|**套用所有設定至 Windows 10**|啟用此原則中要套用至 Windows 10 Mobile 裝置以及 Windows Phone 8.1 裝置的設定。|

### <a name="password-settings"></a>密碼設定

|設定名稱|詳細資料|
|----------------|------|
|**需要密碼才可解除鎖定行動裝置**|指定使用者是否必須輸入密碼才能存取他們的裝置。|
|**必要的密碼類型**|指定必要密碼的類型，例如只可是英數字元或數字等等。|
|**需要的密碼類型 – 最小字元集數**|指定密碼中必須包含幾種不同的字元集。 總共分為四種字元集：小寫字母、大寫字母、數字與符號。 但針對 iOS 裝置，這會指定密碼中必須包含的符號數。|
|**密碼長度下限**|指定密碼所需的字元數下限。|
|**允許簡單密碼**|指定是否能使用 ‘0000’ 和 ‘1234’ 等簡單密碼。|
|**重複登入失敗多少次之後抹除該裝置**|指定抹除裝置前可輸入錯誤密碼的次數。|
|**在閒置幾分鐘後關閉螢幕**|指定自動鎖定螢幕之前，裝置必須維持閒置的時間。|
|**密碼到期 (天數)**|指定必須變更裝置密碼的天數。|是|是|
|**記住密碼歷程記錄**|指定是否要記住先前使用的密碼以防止使用者再次使用它們。|
|**記住密碼歷程記錄** - **不得重複使用以前用過的密碼**|指定要記住多少先前使用的密碼。|

### <a name="encryption-settings"></a>加密設定

|設定名稱|詳細資料|
|----------------|------|
|**行動裝置需要加密**|需要加密受支援行動裝置上的資料。|

### <a name="system-settings"></a>系統設定

|設定名稱|詳細資料|
|----------------|-----|
|**允許螢幕擷取**|讓使用者擷取螢幕的內容做為映像檔案。|
|**允許提交診斷資料**|可讓裝置將診斷資訊提交到 Microsoft。|

### <a name="cloud-settings--accounts-and-synchronization"></a>雲端設定 – 帳戶和同步處理

|設定名稱|詳細資料|
|----------------|------|
|**允許 Microsoft 帳戶**|可將 Microsoft 帳戶連結到裝置。|

### <a name="email-settings"></a>電子郵件設定

|設定名稱|詳細資料|
|----------------|-----|
|**允許自訂電子郵件帳戶**|可讓裝置連接到非 Microsoft 的電子郵件帳戶。|

### <a name="application-settings---browser"></a>應用程式設定 - 瀏覽器

|設定名稱|詳細資料|
|----------------|-----|
|**允許網頁瀏覽器**|啟用或封鎖裝置的內建網頁瀏覽器。|

### <a name="application-settings---apps"></a>應用程式設定 - 應用程式

|設定名稱|詳細資料|
|----------------|-----|
|**允許應用程式市集**|讓使用者從裝置連接到 App Store。|

### <a name="device-capabilities-settings---hardware"></a>裝置功能設定 - 硬體

|設定名稱|詳細資料|
|----------------|-----|
|**允許相機**|啟用或封鎖裝置的相機。|
|**允許卸除式存放裝置**|允許裝置使用如 SD 記憶卡等的卸除式存放裝置。|
|**允許 Wi-Fi**|啟用或停用裝置的 Wi-Fi 功能。|
|**允許 Wi-Fi 網際網路共用功能**|可以使用裝置的 Wi-Fi 網際網路共用功能。|
|**允許自動連線到免費的 Wi-Fi 熱點**|可讓裝置自動連線到免費 Wi-Fi 熱點並自動接受任何使用條款。|
|**允許 Wi-Fi 熱點回報**|傳送 Wi-Fi 連線的相關資訊，以協助使用者找出附近的連線。|
|**允許使用地理位置**|可讓裝置利用位置資訊。|
|**允許 NFC**|可以使用近距離無線通訊的操作。|
|**允許藍芽**|啟用或停用裝置的藍芽功能。|

### <a name="device-capabilities-settings---features"></a>裝置功能設定 - 功能

|設定名稱|詳細資料|
|----------------|----|
|**允許複製並貼上**|可以在裝置上使用複製及貼上功能。|

### <a name="settings-for-allowed-and-blocked-apps"></a>用於允許和封鎖應用程式的設定
在 **[Allowed and blocked apps]** (允許和封鎖的應用程式) 清單中，藉由使用下列資訊指定您要允許或封鎖的應用程式清單：

> [!NOTE]
> 單一原則只能包含允許或封鎖的應用程式清單。 您不能在相同的原則中同時指定兩者。

|設定名稱|詳細資料|
|----------------|--------------------|
|**封鎖裝置，使其無法開啟列出的應用程式**|列出不受 Intune 管理且不允許使用者安裝和執行的應用程式。|
|**允許裝置只安裝所列的應用程式**|列出允許使用者安裝的應用程式。 使用者無法安裝任何其他應用程式。 自動允許 Intune 所管理的應用程式。|
|**[新增]**|將應用程式新增至選取的清單。 指定您選擇的名稱、應用程式市集中的應用程式 URL，以及應用程式發行者 (選擇性)。 如需更多協助，請參閱本主題稍後的＜如何指定 URL 給應用程式市集＞。
|**匯入應用程式**|匯入逗點分隔值檔案中所指定的應用程式清單。 請在檔案中使用「應用程式名稱, 發行者, 應用程式 URL」的格式。|
|**編輯**|可讓您編輯所選取應用程式的名稱、發行者和 URL。|
|**刪除**|從清單中刪除選取的應用程式。|
> [!IMPORTANT]
> 如果您針對 Windows Phone 8.1 裝置指定允許的應用程式清單，則必須將公司入口網站應用程式新增至此清單，否則將會遭到封鎖。


### <a name="reference-information-for-allowed-and-blocked-apps"></a>用於允許或封鎖應用程式的參考資訊

#### <a name="how-to-specify-urls-to-app-stores"></a>如何指定 URL 給應用程式市集
若要在允許和封鎖的應用程式清單中指定應用程式 URL，請使用下列格式：

從 [Windows Phone 的 [應用程式+遊戲]](http://www.windowsphone.com/store/overview) 頁面中，搜尋您想要使用的應用程式。

開啟應用程式的頁面，然後將 URL 複製到剪貼簿。 您現在可以在允許或封鎖的應用程式清單中使用這個 URL。

**範例：** 在市集中搜尋 Skype 應用程式。 您要使用的 URL 是 **http://www.windowsphone.com/store/app/skype/c3f8e570-68b3-4d6a-bdbb-c0a3f4360a51**。

## <a name="custom-policy-settings"></a>自訂原則設定
使用 Microsoft Intune **Windows Phone 自訂設定原則**來部署 OMA-URI 設定，此設定可用來控制 **Windows Phone 8.1 裝置**上的功能。 這些是許多行動裝置製造商用來控制裝置功能的標準設定。

這項功能可讓您部署無法使用 Intune 一般設定原則來設定的 Windows Phone 設定。 如需可使用這些原則進行設定之設定的資訊，請參閱[透過 Microsoft Intune 原則管理裝置上的設定和功能](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)。

如需建立適用於 Windows Phone 裝置的 OMA-URI 設定的說明，請參閱 [Windows Phone 8.1 MDM 通訊協定文件](http://technet.microsoft.com/library/dn499787.aspx)。

### <a name="general-settings"></a>一般設定

|設定名稱|詳細資料|
|----------------|--------------------|
|**Name**|輸入原則的唯一名稱，有助於您在 Intune 主控台中識別該原則。|
|**說明**|提供可給予原則概觀的說明，以及可協助您找到該說明的其他相關資訊。|

### <a name="oma-uri-settings"></a>OMA-URI 設定

在 [OMA-URI 設定] 區段中，按一下 [新增] 以新增設定。 您也可以編輯或刪除現有的設定。

在 [新增或編輯 OMA-URI 設定] 對話方塊中，指定下列資訊：

|設定名稱|詳細資料|
    |--------|--------------------|
    |**設定名稱**|輸入 OMA-URI 設定的唯一名稱，協助您在設定清單中識別該設定。|
    |**設定描述**|提供可給予設定概觀的說明，以及可協助您找到該說明的其他相關資訊。|
    |**資料類型**|選取您要在其中指定這個 OMA-URI 設定的日期類型。 從下列選項進行選擇：<br /><br />-   **字串**<br />-   **字串 (XML)**<br />-   **日期和時間**<br />-   **整數**<br />-   **浮點數**<br />-   **布林值**|
    |**OMA-URI (區分大小寫)**|指定您想要對其提供設定的 OMA-URI。|
    |**值**|指定要與您先前指定的 OMA-URI 產生關聯的值。|

### <a name="see-also"></a>另請參閱
[使用 Microsoft Intune 原則管理裝置的設定及功能](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)

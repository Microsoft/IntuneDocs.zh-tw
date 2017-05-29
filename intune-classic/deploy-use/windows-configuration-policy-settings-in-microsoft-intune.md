---
title: "Windows 原則設定 | Microsoft Docs"
description: "使用 Intune Windows 一般設定原則 (Windows 8.1 和更新版本) 來設定已註冊之 Windows 8 和 Windows 8.1 裝置的設定。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 10/11/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6982a2bc-aafa-475a-9236-4840b709e5a1
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: d95852c20b98ee86552672cf03364980f06f010a
ms.contentlocale: zh-tw
ms.lasthandoff: 05/23/2017


---

# <a name="windows-policy-settings-in-microsoft-intune"></a>Microsoft Intune 的 Windows 原則設定

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

使用 Microsoft Intune **Windows 一般設定原則 (Windows 8.1 和更新版本)** 來設定已註冊之 Windows 8、Windows 8.1 和 Windows RT 8.1 裝置的下列設定：

## <a name="applicability-settings"></a>適用性設定

|設定名稱|詳細資料|
|----------------|----------------------------------|
|**套用所有設定至 Windows 10**|啟用此原則中的設定以套用至 Windows 10 裝置，以及 Windows 8 和 Windows 8.1 裝置。|

## <a name="security-settings"></a>安全性設定

|設定名稱|詳細資料|
|----------------|------|
|**必要的密碼類型**|指定必要密碼的類型，例如只可包含英數字元，或必須是數字等等。|
|**需要的密碼類型 – 最小字元集數**|指定密碼中必須包含幾種不同的字元集。 總共分為四種字元集：小寫字母、大寫字母、數字與符號。 但針對 iOS 裝置，此設定會指定密碼中必須包含的符號數。|
|**密碼長度下限**|設定密碼的必要長度下限 (以字元為單位)。|
|**重複登入失敗多少次之後抹除該裝置**|如果登入嘗試失敗的數目為此，即抹除裝置。|
|**在非使用狀態幾分鐘後會關閉螢幕**|指定在需要密碼將裝置解鎖之前，裝置必須處於閒置狀態的分鐘數。|
|**密碼到期 (天數)**|指定必須變更裝置密碼的天數。|
|**記住密碼歷程記錄**|指定使用者是否可以設定先前已使用的密碼。|
|**記住密碼歷程記錄** - **不得重複使用以前用過的密碼**|指定裝置記憶的先前使用過密碼數目。|
|**允許圖片密碼和 PIN**|可以在裝置上使用圖片密碼和 PIN。 圖片密碼可讓使用者利用圖片上的手勢登入。 PIN 可讓使用者快速利用 4 位數代碼登入。|

## <a name="encryption-settings"></a>加密設定

|設定名稱|詳細資料|
|----------------|-----|
|**行動裝置上需進行加密**<sup>1</sup>|裝置上的檔案需要加密。|
<sup>1</sup> 執行 Windows 8.1 之裝置的其他資訊

-   若要在執行 Windows 8.1 的裝置上強制加密，您必須在每個裝置上安裝 [2014 年 12 月適用於 Windows 的 MDM 用戶端更新](http://support.microsoft.com/kb/3013816) 。

-   如果您針對 Windows 8.1 裝置啟用此設定，則裝置的所有使用者必須都具有 Microsoft 帳戶。

-   為了進行加密，裝置必須符合 Microsoft [InstantGo](http://blogs.windows.com/bloggingwindows/2014/06/19/instantgo-a-better-way-to-sleep/) 硬體認證需求。

-   當您在裝置上強制加密時，就只能從使用者 Microsoft 帳戶存取修復金鑰，該帳戶是從其 OneDrive 帳戶進行存取的。 您無法代表使用者修復此金鑰。

## <a name="malware-settings"></a>惡意程式碼設定

|設定名稱|詳細資料|
|----------------|-----|
|**需要網路防火牆**|需要 Windows 防火牆已開啟。|
|**啟用 SmartScreen**|需要使用 Windows SmartScreen。|

## <a name="system-settings"></a>系統設定

|設定名稱|詳細資料|
|----------------|-------|
|**需要自動更新**|開啟裝置上的自動更新設定。|
|**需要自動更新 - 自動安裝之更新的最小分類**|選擇將自動安裝的更新分類：<br /><br />-   **重要** – 安裝所有歸為重要分類的更新。<br />-   **建議** – 安裝所有歸為重要或建議分類的更新。|
|**使用者帳戶控制**|需要在裝置上使用使用者帳戶控制 (UAC)。|
|**允許提交診斷資料**|可讓裝置將診斷資訊提交到 Microsoft。|


## <a name="cloud-settings--documents-and-data"></a>雲端設定 – 文件和資料

|設定名稱|詳細資料|
|----------------|------|
|**工作資料夾 URL**|設定工作資料夾的 URL，允許跨裝置同步處理文件。|

## <a name="email-settings"></a>電子郵件設定

|設定名稱|詳細資料|
|----------------|-----|
|**讓 Microsoft 帳戶變成 Windows Mail 應用程式的選用帳戶**|可以不使用 Microsoft 帳戶存取 Windows Mail 應用程式。|

## <a name="application-settings---browser"></a>應用程式設定 - 瀏覽器

|設定名稱|詳細資料|
|----------------|-----|
|**允許自動填入**|可讓使用者變更瀏覽器中的自動完成設定。|
|**允許快顯封鎖程式**|啟用或停用瀏覽器的快顯封鎖程式。|
|**允許外掛程式**|可讓使用者將外掛程式加入 Internet Explorer 中。|
|**允許動態指令碼處理**|可讓瀏覽器執行指令碼，例如 ActiveX 指令碼。|
|**允許詐騙警告**|啟用或停用潛在詐騙網站的警告。|
|**允許內部網路網站可輸入單一文字**|可以使用單一文字來將 Internet Explorer 導向某個網站，例如 Bing。|
|**允許自動偵測內部網路**|協助在 Internet Explorer 中設定內部網站的安全性。|
|**網際網路的安全性等級**|設定網際網路網站的 Internet Explorer 安全性等級。|
|**內部網路的安全性等級**|設定網際網路網站的 Internet Explorer 安全性等級。|
|**信任的網站的安全性等級**|設定信任的網站區域的安全性等級。|
|**限制的網站的安全性等級**|設定受限制的網站區域的安全性等級。|
|**傳送「不要追蹤」標頭**|在 Internet Explorer 中傳送「不要追蹤」標頭給造訪的網站。|
|**允許企業模式功能表存取**|讓使用者從 Internet Explorer 存取企業模式功能表選項。<br>如果您選取此設定，您也可以指定 [記錄報告位置]，其中包含報告的 URL，顯示使用者已開啟企業模式存取的網站。|
|**企業模式網站清單位置**|當啟用企業模式時，指定要使用企業模式的網站清單位置。|

## <a name="device-capabilities-settings---cellular"></a>裝置功能設定 - 行動電話通訊

|設定名稱|詳細資料|
|----------------|----|
|**允許數據漫遊**|可讓裝置在行動電話通訊網路上時進行數據漫遊。|



### <a name="see-also"></a>另請參閱
[使用 Microsoft Intune 原則管理裝置的設定及功能](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)


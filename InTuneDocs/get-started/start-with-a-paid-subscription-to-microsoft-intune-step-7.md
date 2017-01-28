---
title: "自訂公司入口網站 | Microsoft Docs"
description: "Intune 公司入口網站可讓使用者執行一般工作，例如註冊裝置、安裝應用程式，以及尋找 IT 部門資訊。"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 12/13/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: eb4a9f01-f857-4563-ab6f-5d0d7dfa659d
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: d05c9d7a78474c19e142bca94e232289fbfba1d9
ms.openlocfilehash: 818763803055e132d77137329b4a5d09b0ce1110


---

# <a name="customize-the-company-portal"></a>自訂公司入口網站

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Intune 公司入口網站是使用者存取公司資料並可以執行一般工作的位置，如註冊裝置、安裝應用程式，以及找到向 IT 尋求協助的資訊。

Intune 公司入口網站可供使用者存取公司資料和應用程式。 公司入口網站有兩種形式︰

-   **公司入口網站應用程式**：可在您使用 Intune 管理的裝置上使用的應用程式。 深入了解 [Android](/Intune/EndUser/using-your-android-device-with-intune)、[iOS](/Intune/EndUser/using-your-iOS-or-macOS-device-with-intune) 和 [Windows](/Intune/EndUser/using-your-windows-device-with-intune) 適用的公司入口網站應用程式。


- **公司入口網站**：一個網站，讓使用者可以執行大部分他們可從公司入口網站應用程式執行的工作。 Intune 公司入口網站 URL 為 [http://portal.manage.microsoft.com](http://portal.manage.microsoft.com)。 在[使用 Intune 公司入口網站](/Intune/EndUser/using-the-intune-company-portal-website)深入了解此網站。

> [!TIP]
> 當您自訂公司入口網站時，這些組態會同時套用到公司入口網站和公司入口網站應用程式。

使用者可以在公司入口網站中執行的部分工作包括︰

-   註冊裝置
-   檢視其裝置的狀態
-   重設其裝置
-   重設其密碼
-   遠端鎖定其裝置
-   下載組織所部署的軟體
-   連絡 IT 部門以取得支援

## <a name="customize-company-portal-settings"></a>自訂公司入口網站設定
自訂公司入口網站可協助提供您的使用者熟悉且實用的體驗。 以租用戶或服務管理員身分登入 [Microsoft Intune 系統管理員主控台](https://manage.microsoft.com)、選擇 [系統管理] &gt; [公司入口網站]，然後進行公司入口網站設定。

![admin-console-admin-workspace-comp-portal-settings](./media/companyportal.png)

## <a name="company-contact-information-and-privacy-statement"></a>公司連絡人資訊和隱私權聲明
公司名稱顯示為公司入口網站標題。 連絡資訊和詳細資料會在公司入口網站的 [連絡 IT] 畫面中向使用者顯示。 當使用者按一下隱私權連結時，會顯示隱私權聲明。

|欄位名稱|長度上限|詳細資訊|
    |----------|------------------------|----------------|
    |公司名稱|40|這是顯示為公司入口網站標題的名稱。|
    |IT 部門連絡人姓名|40|此姓名會顯示在 [連絡 IT] 頁面中。|
    |IT 部門電話號碼|20|此連絡電話號碼會顯示在 [連絡 IT] 頁面中。|
    |IT 部門電子郵件地址|40|此連絡地址會顯示在 [連絡 IT] 頁面中。 您必須輸入有效的電子郵件地址，格式為 **alias@domainname.com**。|
    |其他資訊|120|顯示在 [連絡 IT] 頁面中。|
    |公司隱私權聲明 URL|79|您可以指定自己的公司隱私權聲明，在使用者從公司入口網站按一下隱私權連結時會顯示該聲明。 您必須使用 https://www.contoso.com 格式輸入有效的 URL。|

## <a name="support-contacts"></a>支援連絡人
支援網站將會顯示在公司入口網站中，讓使用者能夠存取線上支援。

|欄位名稱|長度上限|詳細資訊|
    |----------|------------------------|----------------|
    |支援網站 URL|150|如果想讓使用者參考您的支援網站，請在這裡指定 URL。 這個 URL 必須使用 https://www.contoso.com 的格式。 如果您沒有指定 URL，公司入口網站的 [連絡 IT] 頁面上將不會顯示支援網站的任何內容。|
    |網站名稱|40|這是支援網站的 URL 所顯示的易記名稱。 如果您指定支援網站 URL，但沒有指定易記名稱，則公司入口網站的 [連絡 IT] 頁面上將會顯示 [移到 IT 網站]。|

## <a name="company-branding-customization"></a>公司商標自訂
您可以使用公司標誌、公司名稱、佈景主題色彩和背景自訂您的公司入口網站。

|欄位名稱|詳細資訊|
    |----------|----------------|
    |佈景主題色彩|選取要套用到公司入口網站的佈景主題色彩。|
    |包含公司標誌|啟用此選項時，您可以上傳公司標誌以顯示在公司入口網站中。 您可以上傳兩個標誌：一個會在公司入口網站背景是白色時顯示，另一個則會在公司入口網站背景使用您選取的佈景主題色彩時顯示。 每個標誌必須是 .png 或 .jpg 檔案類型，且最大解析度為 400 x 100 像素，大小則是 750 KB 以下。|
    |選擇 [!INCLUDE[win8_client_2](../includes/win8_client_2_md.md)] 公司入口網站應用程式的背景|這項設定只會影響 [!INCLUDE[win8_client_2](../includes/win8_client_2_md.md)] 公司入口網站應用程式的背景。|


儲存變更之後，您可以使用管理主控台之 [公司入口網站] 頁面下方提供的連結，檢視公司入口網站。 這些連結無法變更。 當使用者登入時，這些連結會顯示您在公司入口網站的訂閱。

>[!div class="step-by-step"]

>[&larr; **建立原則和應用程式**](.\start-with-a-paid-subscription-to-microsoft-intune-step-6.md)       [**註冊裝置** &rarr;](.\start-with-a-paid-subscription-to-microsoft-intune-step-8.md)  



<!--HONumber=Jan17_HO2-->



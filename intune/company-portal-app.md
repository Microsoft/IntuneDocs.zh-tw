---
title: 如何設定公司入口網站應用程式
titleSuffix: Microsoft Intune
description: 了解如何將公司自有商標套用到 Intune 公司入口網站應用程式。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/14/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: dec6f258-ee1b-4824-bf66-29053051a1ae
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 72349a609485096b5abd6eaff3c252a510a978a7
ms.sourcegitcommit: 279f923b1802445e501324a262d14e8bfdddabde
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2018
ms.locfileid: "53738013"
---
# <a name="how-to-configure-the-microsoft-intune-company-portal-app"></a>如何設定 Microsoft Intune 公司入口網站應用程式

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

使用者可以從 Microsoft Intune 公司入口網站存取公司資料及執行一般工作，例如註冊裝置、安裝應用程式，以及尋找向 IT 部門尋求協助的資訊。        

> [!Tip]        
> 當您自訂公司入口網站時，這些組態會同時套用到公司入口網站和公司入口網站應用程式。 請注意，使用者必須或指派 Intune 授權，才能存取「公司入口網站」網站。

自訂公司入口網站可協助提供您的使用者熟悉且實用的體驗。 若要執行此作業，請從 [用戶端應用程式] 工作負載中選擇 [設定] > [公司入口網站品牌]，然後設定必要的設定。  

> [!Note]       
> 如果您使用 Azure Government，應用程式記錄檔會提供給終端使用者，用來決定當他們在起始程序取得問題說明時如何進行共用。 不過，如果您未使用 Azure Government，當使用者在起始程序取得問題說明時，Windows 10 版公司入口網站會將應用程式記錄檔直接傳送給 Microsoft。 應用程式記錄檔傳送給 Microsoft 可以更輕鬆地進行疑難排解並解決問題。 

## <a name="company-information-and-privacy-statement"></a>公司資訊和隱私權聲明        
公司名稱顯示為公司入口網站標題。 當使用者按一下隱私權連結時，會顯示隱私權聲明。

標有星號 (*) 的欄位是必填欄位。       


| 欄位名稱 | 長度上限 | 詳細資訊 |
|---|---|---|
|**公司名稱**| 40 | 這個名稱會顯示為公司入口網站的標題，並以文字形式在 Intune 使用者體驗期間顯示。 |
| **隱私權聲明 URL** |     79     | 您可以指定自己的公司隱私權聲明，在使用者從公司入口網站按一下隱私權連結時會顯示該聲明。 您必須以 `<https://www.contoso.com>` 格式輸入有效的 URL。 |

## <a name="support-information"></a>支援資訊      
輸入貴公司的支援資訊，為您的員工提供 Intune 相關問題的連絡人。          

|欄位名稱|長度上限|詳細資訊|
|---|---|---|
|**連絡人姓名** | 40 | 此姓名會顯示在 [連絡 IT] 頁面中。 |
|**電話號碼** | 20 | 此連絡電話號碼會顯示在 [連絡 IT] 頁面，讓員工能夠連絡您以尋求支援。 |
|**電子郵件地址**| 40 | 此連絡地址會顯示在 [連絡 IT] 頁面中。 您必須輸入有效的電子郵件地址，格式為 `alias@domainname.com`。 |
|**網站名稱**| 40 | 這是支援網站的 URL 所顯示的易記名稱。 若只指定支援網站 URL 而未指定易記名稱，將會在公司入口網站的 [連絡 IT] 頁面上顯示 [移至 IT 部門網站]。 |
|**網站 URL**| 150 | 如果想讓使用者參考您的支援網站，請在這裡指定 URL。 URL 的格式必須為 `https://www.contoso.com`。 如果您沒有指定 URL，公司入口網站的 [連絡 IT] 頁面上將不會顯示支援網站的任何內容。 |
| **其他資訊**| 120 | 顯示在 [連絡 IT] 頁面中。 |


## <a name="company-identity-branding-customization"></a>公司識別商標自訂      
您可以使用公司標誌、公司名稱、佈景主題色彩和背景自訂您的公司入口網站。     

### <a name="theme-color-and-logo-in-the-company-portal"></a>公司入口網站的佈景主題色彩和標誌
將佈景主題色彩套用到公司入口網站。 選取標準色彩，或針對自訂色彩輸入六位數的十六進位碼。

|欄位名稱|詳細資訊|
|---|---|
|**選取標準色彩或輸入六位數的十六進位代碼**| 選擇 [標準] 以視覺方式選取色彩。 選擇 [自訂] 根據十六進位代碼值選取特定色彩。|
|**選擇佈景主題色彩**| 選取要套用到公司入口網站的佈景主題色彩。 您可以從標準色彩中選擇，或輸入特定的十六進位碼。 |
|**顯示**| 選取要顯示**公司標誌和名稱**、**僅限公司標誌**或**僅限公司名稱**。 |
|**上傳您公司的標誌**|您可以上傳公司的標誌，以顯示在您的公司入口網站中。 請注意，文字色彩會自動選擇，以達最佳的對比效果。 您可以上傳透明背景的標誌以達到最佳外觀效果。<p><ul><li>影像大小上限：400 像素 x 400 像素</li><li>檔案大小上限：750KB</li><li>檔案類型：PNG、JPG 或 JPEG</li></ul>|

上傳標誌之後，預覽區會以佈景主題色彩顯示標誌。 如果您選擇顯示公司名稱，它就會在公司入口網站中以黑色或白色顯示，而且會根據您的佈景主題色彩自動選擇，以達最佳的對比效果。 畫面上的預覽區不會顯示公司名稱。 

### <a name="logo-to-use-on-white-or-light-backgrounds"></a>要在白色或淺色背景中使用的標誌
選擇在白色或淺色背景中看起來最佳的標誌。

|欄位名稱|詳細資訊|
|---|---|
|**上傳您的標誌**| 如果您已選擇要顯示公司標誌，就可以使用這個選項。 您可以上傳透明背景的標誌以達到最佳外觀效果。<p><ul><li>影像大小上限：400 像素 x 400 像素</li><li>檔案大小上限：750KB</li><li>檔案類型：PNG、JPG 或 JPEG</li></ul>|

### <a name="brand-image-for-company-portal"></a>公司入口網站的品牌影像

顯示反映您公司品牌的品牌影像。 儲存變更之後，可以選擇刀鋒視窗頂端的 [在 Intune Web 入口網路中預覽您的設定] 來查看您的設定。 請注意，您只能在 iOS 裝置上預覽品牌影像，而無法在 Intune Web 入口網站中進行預覽。 

|欄位名稱|詳細資訊|
|---|---|
|**上傳您的品牌影像**| 此選項可讓您在公司入口網站應用程式中的使用者設定檔頁面上顯示背景影像。<p>*注意*：影像在不同的平台上的顯示可能會不同。<p><ul><li>建議影像寬度：大於 1125 像素，但不小於 640 像素</li><li>影像大小上限：1.3 MB</li><li>檔案類型：PNG、JPG 或 JPEG</li></ul>|

正確的品牌影像可讓公司品牌留下強烈印象，因而加強使用者對公司入口網站的信任。 以下是您擷取、選擇及最佳化公司入口網站影像時可能想要考慮的一些祕訣。 

- 連絡您的行銷或美術部門。 他們可能已有一組經核准的品牌影像。 他們也可協助您視需要最佳化影像。 

- 請同時考慮橫向和直向構圖。 影像在焦點周圍應該有足夠的背景。 影像可能會因裝置大小、方向與平台而有不同的裁剪方式。 

- 避免使用一般內建影像。 影像應該反映您公司的品牌，而且對您的使用者並不陌生。 如果您沒有影像，與其使用對使用者不具任何意義的一般影像，不如不要使用影像。 

- 移除不必要的中繼資料。 影像檔可能隨附中繼資料，例如相機設定檔、地理位置、標題、字幕等。 請使用影像最佳化工具去除這項資訊來維護品質，同時符合檔案大小限制。 

當 Intune 中的品牌影像新增或變更時，使用者可能不會在 iOS 裝置上看到變更，直到「公司入口網站」已在啟動時發現變更，然後重新啟動以顯示品牌影像。 

### <a name="brand-image-examples"></a>品牌影像範例

下列影像顯示範例 iPad 品牌影像：

![範例 iPhone 品牌影像的螢幕擷取畫面](media/company-portal-app/company-portal-app-03.png)

下列影像顯示範例 iPhone 品牌影像：

![範例 iPad 品牌影像的螢幕擷取畫面](media/company-portal-app/company-portal-app-02.png)

## <a name="windows-company-portal-keyboard-shortcuts"></a>Windows 公司入口網站鍵盤快速鍵

終端使用者可以在 Windows 公司入口網站中使用鍵盤快速鍵觸發導覽、應用程式與裝置動作。

您可以在 Windows 公司入口網站應用程式中使用下列鍵盤快速鍵。

| 區域 | 說明 | 鍵盤快速鍵 |
|:------------------:|:--------------:|:-----------------:|
| 導覽功能表 | 導覽 | Alt+M |
|  | 首頁 | Alt+H |
|  | 所有應用程式 | Alt+A |
|  | 已安裝的應用程式 | Alt+I |
|  | 傳送意見反應 | Alt+F |
|  | 我的設定檔 | Alt+U |
|  | 設定 | Alt+T |
| 首頁 - 裝置磚 | 重新命名 | F2 |
|  | 移除 | Ctrl+D 或 Delete |
|  | 檢查存取權 | Ctrl+M 或 F9 |
| 裝置詳細資訊 | 重新命名 | F2 |
|  | 移除 | Ctrl+D 或 Delete |
|  | 檢查存取權 | Ctrl+M 或 F9 |
| 應用程式詳細資料 | 安裝 | Ctrl+I |

使用者也能夠在 Windows「公司入口網站」應用程式中看到可用的捷徑。

![Windows 公司入口網站中可用捷徑的螢幕擷取畫面](media/company-portal-app/company-portal-app-01.png)

## <a name="next-steps"></a>接下來的步驟

- [使用 Microsoft Intune 手動新增 Windows 10 公司入口網站應用程式](store-apps-company-portal-app.md)

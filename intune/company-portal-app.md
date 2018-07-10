---
title: 如何設定公司入口網站應用程式
titleSuffix: Microsoft Intune
description: 了解如何將公司自有商標套用到 Intune 公司入口網站應用程式。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 05/21/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: dec6f258-ee1b-4824-bf66-29053051a1ae
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 4535bdfa9b801c605c70c0a9dad900d76044eab4
ms.sourcegitcommit: c78923b0d5b320322c828b1bbea2deb9062e30d2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/05/2018
ms.locfileid: "37844975"
---
# <a name="how-to-configure-the-microsoft-intune-company-portal-app"></a>如何設定 Microsoft Intune 公司入口網站應用程式

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

使用者可以從 Microsoft Intune 公司入口網站存取公司資料及執行一般工作，例如註冊裝置、安裝應用程式，以及尋找向 IT 部門尋求協助的資訊。        

> [!Tip]        
> 當您自訂公司入口網站時，這些組態會同時套用到公司入口網站和公司入口網站應用程式。       

自訂公司入口網站可協助提供您的使用者熟悉且實用的體驗。 若要執行此作業，請從 [行動應用程式] 工作負載中選擇 [設定] > [公司入口網站品牌]，然後設定必要的設定。  

> [!Note]       
> 當使用者啟動工作流程以取得有關問題的說明時，Windows 10 版公司入口網站現在會將應用程式記錄檔直接傳送給 Microsoft。 這樣可以更輕鬆地進行疑難排解並解決向 Microsoft 提出的問題。  

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


## <a name="company-branding-customization"></a>公司商標自訂       
您可以使用公司標誌、公司名稱、佈景主題色彩和背景自訂您的公司入口網站。     

### <a name="theme-color"></a>佈景主題色彩
將佈景主題色彩套用到公司入口網站。 選取標準色彩，或針對自訂色彩輸入六位數的十六進位碼。

|欄位名稱|詳細資訊|
|---|---|
|**色彩類型**| 選取要套用到公司入口網站的佈景主題色彩。 您可以從標準色彩中選擇，或輸入特定的十六進位碼。 |
|**選擇色彩**或**十六進位色彩代碼**| 選取要套用到公司入口網站的佈景主題色彩。 您可以從標準色彩中選擇，或輸入特定的十六進位碼。 這些選項會根據您選取的 [色彩類型] 提供。  |

### <a name="company-logo"></a>公司標誌
上傳您的公司標誌，使其在 Intune 使用者體驗期間顯示。

|欄位名稱|詳細資訊|
|---|---|
|**顯示公司標誌**|啟用此選項時，您可以上傳公司標誌以顯示在公司入口網站中。 您可以上傳兩個標誌：一個會在公司入口網站背景是白色時顯示，另一個則會在公司入口網站背景使用您選取的佈景主題色彩時顯示。 |
|**上傳要在佈景主題色彩背景中使用的標誌**| 如果您已選擇要顯示公司標誌，就可以使用這個選項。 標誌必須是 .png 或 .jpg 檔案類型，且最大解析度為 400 x 400 像素，大小則是 750 KB 以下。 |
|**上傳要在淺色背景中使用的標誌**| 如果您已選擇要顯示公司標誌，就可以使用這個選項。 標誌必須是 .png 或 .jpg 檔案類型，且最大解析度為 400 x 400 像素，大小則是 750 KB 以下。 |
|**在標誌旁顯示公司名稱**| 選取此選項可在上傳的標誌旁顯示您輸入的公司名稱。 |

儲存變更之後，可以選擇刀鋒視窗頂端的 [在 Intune Web 入口網路中預覽您的設定] 來查看您的設定。

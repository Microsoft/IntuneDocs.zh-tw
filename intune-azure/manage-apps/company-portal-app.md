---
title: "如何設定公司入口網站應用程式"
titleSuffix: Intune Azure preview
description: "Intune Azure 預覽版：了解如何將公司自有商標套用到 Intune 公司入口網站應用程式。 "
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: dec6f258-ee1b-4824-bf66-29053051a1ae
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 153cce3809e24303b8f88a833e2fc7bdd9428a4a
ms.openlocfilehash: 9ebfadd945916b6be8225b9e07d67100e3f91222
ms.lasthandoff: 02/18/2017

---

# <a name="how-to-configure-the-microsoft-intune-company-portal-app"></a>如何設定 Microsoft Intune 公司入口網站應用程式

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

使用者可以從 Microsoft Intune 公司入口網站存取公司資料及執行一般工作，例如註冊裝置、安裝應用程式，以及尋找向 IT 部門尋求協助的資訊。

> [!Tip]
> 當您自訂公司入口網站時，這些組態會同時套用到公司入口網站和公司入口網站應用程式。

自訂公司入口網站可協助提供您的使用者熟悉且實用的體驗。 若要執行此作業，請從**管理應用程式**工作負載中選擇 [設定]  >  [Company Portal Branding] (公司入口網站商標)，然後設定必要的設定。

## <a name="company-contact-information-and-privacy-statement"></a>公司連絡人資訊和隱私權聲明
公司名稱顯示為公司入口網站標題。 連絡資訊及詳細資料會在公司入口網站的 [連絡 IT] 畫面中顯示給使用者。 當使用者按一下隱私權連結時，會顯示隱私權聲明。


|欄位名稱|長度上限|詳細資訊|
|-|-|-|
|**公司名稱**|40|這是顯示為公司入口網站標題的名稱。|
|**IT 部門連絡人姓名**|40|此姓名會顯示在 [連絡 IT] 頁面中。|
|**IT 部門電話號碼**|20|此連絡電話號碼會顯示在 [連絡 IT] 頁面中。|
|IT 部門電子郵件地址|40|此連絡地址會顯示在 [連絡 IT] 頁面中。 您必須輸入有效的電子郵件地址，格式為 **alias@domainname.com**。|
|**其他資訊**|120|顯示在 [連絡 IT] 頁面中。|
|**公司隱私權聲明 URL**|79|您可以指定自己的公司隱私權聲明，在使用者從公司入口網站按一下隱私權連結時會顯示該聲明。 您必須使用 **https://www.contoso.com** 此格式輸入有效的 URL。|

## <a name="support-contacts"></a>支援連絡人
支援網站將會顯示在公司入口網站中，讓使用者能夠存取線上支援。



|欄位名稱|長度上限|詳細資訊|
|-|-|-|
|**支援網站 URL**|150|如果想讓使用者參考您的支援網站，請在這裡指定 URL。 這個 URL 必須使用 **https://www.contoso.com** 的格式。 如果您沒有指定 URL，公司入口網站的 [連絡 IT] 頁面上將不會顯示支援網站的任何內容。|
|**支援網站 URL**|40|這是支援網站的 URL 所顯示的易記名稱。 若只指定支援網站 URL 而未指定易記名稱，將會在公司入口網站的 [連絡 IT] 頁面上顯示 [移至 IT 部門網站]。

## <a name="company-branding-customization"></a>公司商標自訂
您可以使用公司標誌、公司名稱、佈景主題色彩和背景自訂您的公司入口網站。



|欄位名稱|詳細資訊|
|-|-|
|**佈景主題色彩**|選取要套用到公司入口網站的佈景主題色彩。|
|**顯示公司標誌**|啟用此選項時，您可以上傳公司標誌以顯示在公司入口網站中。 您可以上傳兩個標誌：一個會在公司入口網站背景是白色時顯示，另一個則會在公司入口網站背景使用您選取的佈景主題色彩時顯示。 每個標誌必須是 .png 或 .jpg 檔案類型，且最大解析度為 400 x 100 像素，大小則是 750 KB 以下。<br>您也可以在上傳的標誌旁顯示您輸入的公司名稱。|

儲存變更之後，可以選擇 [在 Intune Web 入口網路中預覽您的設定] 來查看您的設定。


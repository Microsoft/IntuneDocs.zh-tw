---
title: 開發中 - Microsoft Intune
titleSuffix: ''
description: 正在開發的 Microsoft Intune 功能
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/29/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3645d07fe9a703f182e05bc9a7f9fbb93c413ddc
ms.sourcegitcommit: dfcf80a91792715404dc021c8684866c8b0a27e1
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2019
ms.locfileid: "65816235"
---
# <a name="in-development-for-microsoft-intune---may-2019"></a>Microsoft Intune 正在開發的項目 - 2019 年 5 月

為了協助您整備及規劃，此頁面會列出正在開發，但尚未發行的 Intune UI 更新及功能。 此外：

- 若我們預期您將需要在變更前先行採取動作，我們會發佈輔助性的 Office 訊息中心貼文。
- 當功能在生產環境中啟動時，無論是作為預覽功能還是正式推出，功能描述都會從此頁面移除，並移到 [[新增功能]](whats-new.md) 頁面。
- 此頁面和 [[新增功能]](whats-new.md) 頁面會定期更新。 請回來查看其他更新。
- 請參閱 [M365 藍圖](https://www.microsoft.com/microsoft-365/roadmap?rtc=2&filters=EMS)以取得策略性的交付時間表。

> [!Note]
> 這些項目會反映 Microsoft 目前針對未來版本中 Intune 功能的預期。 日期和個別的功能可能會產生變更。 並非所有正在開發的項目在此頁面上都具有功能描述。

**RSS 摘要**：將下列 URL 複製並貼上至您的摘要讀取器中，以在本頁更新時收到通知：`https://docs.microsoft.com/api/search/rss?search=%22in+development+-+microsoft+intune%22&locale=en-us`

<!--
## What's coming to Intune in the Azure portal 
## What's coming to Intune apps
## Notices
-->
 
## <a name="intune-in-the-azure-portal"></a>Azure 入口網站中的 Intune


<!-- 1905 start-->


### <a name="baseline-support-for-keyword-search-----3082036-----------"></a>關鍵字搜尋的基準支援  <!-- 3082036         -->
建立或編輯安全性基準設定檔時，您很快就可以使用搜尋功能來篩選主控台中顯示的設定。   

### <a name="reset-and-wipe-devices-in-bulk-by-using-the-graph-api----3295288---"></a>使用圖形 API 大量重設及抹除裝置 <!-- 3295288 -->
您可以使用圖形 API 大量重設及抹除最多 100 部裝置。

<!-- 1904 start-->

### <a name="device-users-can-view-all-managed-apps-theyve-installed-or-tried-to-install----2352913---"></a>裝置使用者可檢視其安裝或嘗試安裝的所有受控應用程式 <!-- 2352913 -->
Windows 的公司入口網站會列出在使用者裝置上所安裝所有受控應用程式，包括必要及可用的應用程式。 使用者將能夠檢視嘗試及正在擱置的應用程式安裝，以及其目前的狀態。 若您的組織沒有將應用程式設為必要或可用，使用者會看見一個訊息，說明沒有安裝任何公司應用程式。 使用者也將能夠根據安裝狀態排序或篩選其應用程式。

### <a name="use-applicability-rules-when-creating-windows-10-device-configuration-profiles----2549910---"></a>在建立 Windows 10 裝置組態設定檔時使用「適用性規則」 <!-- 2549910 -->
您可以建立 Windows 10 裝置組態設定檔 ([裝置設定] > [設定檔] > [建立設定檔] > 針對平台選取 [Windows 10])。 您將能夠建立**適用性規則**，讓設定檔只套用到特定版本。 例如，您可以建立設定檔來啟用某些 BitLocker 設定。 一旦您新增設定檔後，您便可以使用適用性規則，將設定檔設為只套用到執行 Windows 10 企業版的裝置。

適用於： 
- Windows 10 及更新版本



## <a name="notices"></a>通知

[!INCLUDE [Intune notices](./includes/intune-notices.md)]

### <a name="see-also"></a>請參閱
如需近期發展的詳細資料，請參閱 [Microsoft Intune 的新功能](whats-new.md)。



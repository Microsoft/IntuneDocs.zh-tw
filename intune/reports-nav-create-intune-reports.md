---
title: 使用 Intune 資料倉儲
titlesuffix: Microsoft Intune
description: 使用 Intune 資料倉儲來建置報表，以深入了解您的企業行動環境。
keywords: Intune 資料倉儲
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/01/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 57019B11-DF9B-4D8A-95FE-254C75398DDE
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 16913689dcc5b37de73b39387efeb399b307306b
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="use-the-intune-data-warehouse"></a>使用 Intune 資料倉儲

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

使用 Intune 資料倉儲來建置報表，以深入了解您的企業行動環境。 例如，某些報表包含：
-   Intune 中使用者註冊趨勢，以最佳化授權採購
-   應用程式和 OS 版本分解，以檢閱行動裝置的狀態
-   註冊和裝置合規性趨勢，以順暢地轉出原則更新

資料倉儲可讓您存取 Azure 入口網站以外之行動環境的詳細資訊。 您可以使用 Intune 資料倉儲存取：

  -  歷程 Intune 資料
  -  以每日步調重新整理的資料
  -  使用 OData 標準的資料模型

> [!Note]
> 如果使用混合式行動裝置管理 (MDM) 搭配 System Center Configuration Manager 與 Microsoft Intune，您想要從 SCCM 擷取資料。 Intune 資料倉儲只包含 Intune 資料。 您可以針對自訂報表使用 SCCM Power BI 儀表板。 如需詳細資訊，請參閱 "[Announcing the Power BI solution template for System Center Configuration Manager]( https://powerbi.microsoft.com/blog/sccm-solution-template)" (宣告適用於 System Center Configuration Manager 的 Power BI 解決方案範本) 和 [Power BI content for Dynamics 365](https://docs.microsoft.com/dynamics365/unified-operations/dev-itpro/analytics/power-bi-home-page) (Dynamics 365 的 Power BI 內容)。


> [!Important]  
> 您可以使用搶鮮版 (Beta) 來試用最新資料倉儲功能。 若要使用搶鮮版 (Beta)，URL 必須包含查詢參數 `api-version=beta`。 搶鮮版 (Beta) 會先提供功能，再將它們正式推出為支援的服務。 Intune 新增功能時，搶鮮版 (Beta) 可能會變更行為和資料合約。 與搶鮮版 (Beta) 相依的任何自訂程式碼或報告工具都可能會中斷進行中更新。

**後續步驟**

- 取得連結，並使用 Power BI 深入了解。 如需指示，請參閱[使用 Power BI 連線至 Intune 資料倉儲](reports-proc-get-a-link-powerbi.md)。
- 使用您的連結，以 Power BI 建立自訂報表。 如需指示，請參閱[利用 Power BI 的 OData 摘要建立報表](reports-proc-create-with-odata.md)。
- 取得 Intune 資料倉儲 API、資料模型以及實體間之關聯性的詳細資訊<!-- , and an example of creating a custom client to retrieve data,--> 請參閱 [Intune 資料倉儲 API](reports-nav-intune-data-warehouse.md)。
---
title: "利用 Power BI 的 OData 摘要建立報表"
titlesuffix: Microsoft Intune
description: "使用 Power BI Desktop 建立矩形式樹狀結構圖視覺效果，搭配來自 Intune 資料倉儲 API 的互動式篩選。"
keywords: "Intune 資料倉儲"
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/27/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: A2C8A336-29D3-47DF-BB4A-62748339391D
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 850218c33a37738c591be36c778dfe5941bea51b
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/08/2018
---
# <a name="create-a-report-from-the-odata-feed-with-power-bi"></a>利用 Power BI 的 OData 摘要建立報表

本文說明如何使用 Power BI Desktop 建立矩形式樹狀結構圖視覺效果，搭配互動式篩選。 例如，您的財務長可能想要知道公司所擁有的裝置與個人裝置相比較的裝置整體分佈。 矩形式樹狀結構圖提供裝置類型總數的深入解析。 您可以檢視公司所擁有或個人擁有的 iOS、Android 和 Windows 裝置數目。

### <a name="overview-of-creating-the-chart"></a>建立圖表的概觀

若要建立此圖表，您必須：
1. 安裝 Power BI Desktop，如果還沒有的話。
2. 連接至 Intune 資料倉儲資料模型，並擷取模型的目前資料。
3. 建立或管理資料模型關聯性。
4. 建立具有來自 **devices** 資料表之資料的圖表。
5. 建立互動式篩選。
6. 檢視完成的圖表。

### <a name="a-note-about-tables-and-entities"></a>資料表和實體的相關附註

您在 Power BI 中使用資料表。 資料表包含資料欄位。 每個資料欄位具有資料類型。 欄位只能包含資料類型的資料。 資料類型為數字、文字、日期等等。 Power BI 中的資料表會在您載入模型時，填入來自您租用戶的最近歷程記錄資料。 雖然特定資料會隨時間改變，但除非更新了基礎資料模型，否則資料表結構不會改變。

您可能會因為使用詞彙「實體」和「資料表」而感到混淆。 資料模型可以透過 OData 摘要存取。 在 OData 的世界，Power BI 中稱為資料表的容器被稱為「實體」。 這些詞彙都是指保存您資料的相同東西。

## <a name="install-power-bi-desktop"></a>安裝 Power BI Desktop

安裝最新版本的 Power BI Desktop。 您可以從 [PowerBI.microsoft.com](https://powerbi.microsoft.com/desktop) 下載 Power BI Desktop。

## <a name="connect-to-the-odata-feed-for-the-intune-data-warehouse-for-your-tenant"></a>連接到您租用戶之 Intune 資料倉儲的 OData 摘要

> [!Note]  
> 您需要對 Intune 中 [報表] 的權限。 如需詳細資訊，請參閱[授權](reports-api-url.md)。

1. 登入 [Azure 入口網站](https://portal.azure.com)。
2. 選擇 [所有服務] > [Intune]。 [Intune] 位於 [監視 + 管理] 區段。
3. 開啟 [Intune 資料倉儲] 窗格。
4. 複製自訂摘要 URL。 例如：`https://fef.tenant.manage.microsoft.com/ReportingService/DataWarehouseFEService?api-version=beta`
5. 開啟 Power BI Desktop。
6. 選擇 [取得資料] > [Odata 摘要]。
7. 將自訂摘要 URL 貼到 [OData 摘要] 視窗的 URL 方塊中。
8. 選取 [基本]。

    ![OData 摘要](media/reports-create-01-odatafeed.png)

9. 選取 [確定]。
10. 選取 [組織帳戶]，然後使用您的 Intune 認證登入。

    ![組織帳戶認證](media/reports-create-02-org-account.png)

11. 選取 [連線]。 導覽器會開啟並顯示 Intune 資料倉儲中的資料表清單。

    ![導覽器](media/reports-create-02-loadentities.png)

12. 選取 **devices** 和 **ownerTypes** 資料表。  選取 [載入]。 Power BI 將資料載入至模型。

## <a name="create-a-relationship"></a>建立關聯性

您可以匯入多個資料表，分析單一資料表中的資料，也分析資料表之間的相關資料。  Power BI 有一個功能稱為**自動偵測**，它會嘗試為您尋找並建立關聯性。 資料倉儲中的資料表已建置成使用 Power BI 的自動偵測功能。 不過，即使 Power BI 不會自動尋找關聯性，您還是能管理關聯性。

![管理關聯性](media/reports-create-03-managerelationships.png)

1. 選取 [管理關聯性]。
2. 如果 PowerBI 尚未偵測到關聯性，請選取 [自動偵測...]。

關聯性顯示為「從」資料行到「至」資料行。 在此範例中，**devices** 資料表中的資料欄位 **ownerTypeKey**，連結至 **ownerTypes** 資料表中的資料欄位 **ownerTypeKey**。 您可以使用關聯性來查閱 **devices** 資料表中裝置類型代碼的一般名稱。

## <a name="create-a-treemap-visualization"></a>建立矩形式樹狀結構圖視覺效果

矩形式樹狀結構圖會將階層式資料顯示為方塊中的方塊。 階層的每個分支都是一個方塊，包含顯示子分支的較小方塊。 您可以使用 Power BI Desktop 來建立 Intune 資料的矩形式樹狀結構圖。

![視覺效果 > 矩形式樹狀結構圖](media/reports-create-03-treemap.png)

1. 選取圖表類型。 選取 [矩形式樹狀結構圖]。
2. 在資料模型中，尋找 **devices** 資料表。
3. 展開 **devices** 資料表，並在 [欄位] 面板中選取 **manufacturer** 資料欄位。
4. 將 **manufacturer** 資料欄位拖曳到報表畫布上的矩形式樹狀結構圖。
5. 將 **deviceKey** 資料欄位從 **devices** 資料表拖曳到 [視覺效果] 窗格下的 [值] 區段，並放在標示為 [將資料欄位拖曳到這裡] 方塊上。  

您現在已有視覺效果，其可顯示您組織中的裝置製造商分佈。

![具有資料的矩形式樹狀結構圖](media/reports-create-06-treemapwdata.png)

## <a name="add-a-filter"></a>新增篩選

您可以將篩選新增到矩形式樹狀結構圖，以便可以使用您的應用程式回答其他問題。


1. 若要新增篩選，請選取報表畫布，然後選取 [視覺效果] 下的**交叉分析篩選器圖示** (![具有資料的矩形式樹狀結構圖](media/reports-create-slicer.png))。
2. 尋找 **ownerTypes** 資料表，並拖曳 [視覺效果] 面板的 [篩選] 區段下的 **ownerTypeName** 資料欄位。  

   在 devices 資料表下，有一個稱為 **OwnerTypeKey** 的資料欄位，它包含裝置是公司擁有還是個人擁有的代碼。 因為您想要在此篩選中顯示易記名稱，所以請尋找 **ownerTypes** 資料表，並拖曳 **ownerTypeName**。 此範例說明資料模型支援資料表之間的關聯性。

![具有篩選的矩形式樹狀結構圖](media/reports-create-08_ownertype.png)

您現在已有互動式篩選，可用來切換公司所擁有的裝置和個人擁有的裝置。 您可使用此篩選來查看分佈變更。

1. 選取 [公司] 查看公司所擁有的裝置分佈。
2. 選取 [個人] 查看個人擁有的裝置。

## <a name="next-steps"></a>接下來的步驟

 - 在 Power BI 文件中深入了解在 Power BI Desktop [建立和管理關聯性](https://powerbi.microsoft.com/documentation/powerbi-desktop-create-and-manage-relationships/)。
 - 請參閱 [Intune 資料倉儲模型](https://docs.microsoft.com/intune/reports-ref-data-model)。

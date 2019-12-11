---
title: 使用 Power BI 從 OData 摘要建立 Intune 報表
titleSuffix: Microsoft Intune
description: 使用 Power BI Desktop 建立矩形式樹狀結構圖視覺效果，搭配來自 Intune 資料倉儲 API 的互動式篩選。
keywords: Intune 資料倉儲
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/03/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: developer
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: A2C8A336-29D3-47DF-BB4A-62748339391D
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 18815fb671e853bc0463fed750d40b80ccb285fb
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "74784267"
---
# <a name="create-an-intune-report-from-the-odata-feed-with-power-bi"></a>使用 Power BI 從 OData 摘要建立 Intune 報表

本文說明如何使用使用者互動式篩選的 Power BI Desktop，來建立 Intune 資料的樹狀圖視覺效果。 例如，您的 CFO 可能會想要知道裝置的整體分佈如何在公司擁有的裝置和個人裝置之間進行比較。 矩形式樹狀結構圖提供裝置類型總數的深入解析。 您可以檢視公司所擁有或個人擁有的 iOS、Android 和 Windows 裝置數目。

## <a name="overview-of-creating-the-chart"></a>建立圖表的概觀

若要建立此圖表，您將：
1. 安裝 Power BI Desktop，如果還沒有的話。
2. 連接至 Intune 資料倉儲資料模型，並擷取模型的目前資料。
3. 建立或管理資料模型關聯性。
4. 建立具有來自 **devices** 資料表之資料的圖表。
5. 建立互動式篩選。
6. 檢視完成的圖表。

### <a name="a-note-about-tables-and-entities"></a>資料表和實體的相關附註

您在 Power BI 中使用資料表。 資料表包含資料欄位。 每個資料欄位具有資料類型。 欄位只能包含資料類型的資料。 資料類型為數字、文字、日期等等。 Power BI 中的資料表會在您載入模型時，填入來自您租用戶的最近歷程記錄資料。 雖然特定資料會隨時間改變，但除非更新了基礎資料模型，否則資料表結構不會改變。

您可能會因為使用詞彙「實體」  和「資料表」  而感到混淆。 資料模型可透過 OData （開放式資料通訊協定）摘要存取。 在 OData 的世界，Power BI 中稱為資料表的容器被稱為「實體」。 這些詞彙都是指保存您資料的相同東西。 如需 OData 的詳細資訊，請參閱[Odata 總覽](/odata/overview)。

## <a name="install-power-bi-desktop"></a>安裝 Power BI Desktop

安裝最新版本的 Power BI Desktop。 您可以從 [PowerBI.microsoft.com](https://powerbi.microsoft.com/desktop) 下載 Power BI Desktop。

## <a name="connect-to-the-odata-feed-for-the-intune-data-warehouse-for-your-tenant"></a>連接到您租用戶之 Intune 資料倉儲的 OData 摘要

> [!Note]  
> 您需要對 Intune 中 [報表]  的權限。 如需詳細資訊，請參閱[授權](../reports-api-url.md)。

1. 登入 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
2. 選取 [Microsoft Intune - 概觀]  刀鋒視窗右側 [其他工作]  下方的 [資料倉儲] 連結，以開啟 [Intune 資料倉儲]  窗格。
3. 複製自訂摘要 URL。 例如：`https://fef.tenant.manage.microsoft.com/ReportingService/DataWarehouseFEService?api-version=beta`
4. 開啟 Power BI Desktop。
5. 從功能表列中，**選取 [** 檔案] > [**取得資料**] > [ **Odata**摘要]。
6. 將您從先前步驟複製的自訂摘要 URL 貼入 [ **OData**摘要] 視窗的 [URL] 方塊中。
7. 選取 [基本]  。

    ![您租用戶中 Intune 資料倉儲的 OData 摘要](./media/reports-proc-create-with-odata/reports-create-01-odatafeed.png)

8. 選取 [確定]  。
9. 選取 [組織帳戶]  ，然後使用您的 Intune 認證登入。

    ![組織帳戶認證](./media/reports-proc-create-with-odata/reports-create-02-org-account.png)

10. 選取 [連線]  。 導覽器會開啟並顯示 Intune 資料倉儲中的資料表清單。

    ![導覽器螢幕擷取畫面 - 資料倉儲資料表清單](./media/reports-proc-create-with-odata/reports-create-02-loadentities.png)

11. 選取 **devices** 和 **ownerTypes** 資料表。  選取 [載入]  。 Power BI 將資料載入至模型。

## <a name="create-a-relationship"></a>建立關聯性

您可以匯入多個資料表，分析單一資料表中的資料，也分析資料表之間的相關資料。 Power BI 有一個稱為**自動偵測**的功能，它會嘗試為您尋找並建立關聯性。 資料倉儲中的資料表已建置成搭配 Power BI 中的自動偵測功能使用。 不過，即使 Power BI 不會自動尋找關聯性，您還是可以管理關聯性。

![管理資料表之間相關資料的關聯性](./media/reports-proc-create-with-odata/reports-create-03-managerelationships.png)

1. 選取 [管理關聯性]  。
2. 如果 Power BI 尚未偵測到關聯性，請選取 [自動偵測]  。

關聯性顯示為「從」資料行到「至」資料行。 在此範例中，**devices** 資料表中的資料欄位 **ownerTypeKey**，連結至 **ownerTypes** 資料表中的資料欄位 **ownerTypeKey**。 您可以使用關聯性來查閱 **devices** 資料表中裝置類型代碼的一般名稱。

## <a name="create-a-treemap-visualization"></a>建立矩形式樹狀結構圖視覺效果

將階層式資料顯示為方塊中方塊的矩形式樹狀結構圖。 階層的每個分支都是一個方塊，包含顯示子分支的較小方塊。 您可以使用 Power BI desktop 來建立 Intune 租使用者資料的樹狀圖，以顯示裝置製造商類型的相對數量。

![Power BI 矩形式樹狀結構圖視覺效果](./media/reports-proc-create-with-odata/reports-create-03-treemap.png)

1. 在 [**視覺效果**] 窗格中，尋找並選取 [**樹狀圖**]。 **樹狀圖**圖表將會加入至報表畫布。
2. 在 [**欄位**] 窗格中，尋找 [`devices`] 資料表。
3. 展開 [`devices`] 資料表，然後選取 [`manufacturer` 資料] 欄位。
4. 將 [`manufacturer` 資料] 欄位拖曳至 [報表畫布]，然後放在 [**樹狀圖**] 圖表上。
5. 將 [`deviceKey` 資料] 欄位從 [`devices`] 資料表拖曳至 [**視覺效果**] 窗格，並將它放在 [在**此處新增資料欄位**] 方塊中的 [**值**] 區段底下。  

您現在已有視覺效果，其可顯示您組織中的裝置製造商分佈。

![含有資料的矩形式樹狀結構圖 - 裝置製造商分佈](./media/reports-proc-create-with-odata/reports-create-06-treemapwdata.png)

## <a name="add-a-filter"></a>新增篩選

您可以將篩選新增到矩形式樹狀結構圖，以便可以使用您的應用程式回答其他問題。

1. 若要新增篩選，請選取報表畫布，然後選取 [視覺效果]  底下的**交叉分析篩選器圖示** (![具有資料模型和所支援關聯性的矩形式樹狀結構圖](./media/reports-proc-create-with-odata/reports-create-slicer.png))。 空白的交叉分析篩選**器**視覺效果將會出現在畫布上。
2. 在 [**欄位**] 窗格中，尋找 [`ownerTypes`] 資料表。
3. 展開 [`ownerTypes`] 資料表，然後選取 [`ownerTypeName` 資料] 欄位。
4. 將 [`onwerTypeName` 資料] 欄位從 [`ownerTypes`] 資料表拖曳至 [**篩選**] 窗格，並將它放在 [在**此頁面**上標記**新增資料欄位**] 方塊中的 [篩選] 區段底下。  

   在 [`OwnerTypes`] 資料表下，有一個稱為 `OwnerTypeKey`的資料欄位，其中包含裝置是否為公司擁有或個人的資料。 因為您想要在此篩選中顯示易記名稱，所以請尋找 `ownerTypes` 資料表，並將 **ownerTypeName** 拖曳至交叉分析篩選器。 此範例說明資料模型支援資料表之間的關聯性。

![含有篩選的矩形式樹狀結構圖 - 支援資料表之間的關聯性](./media/reports-proc-create-with-odata/reports-create-08_ownertype.png)

您現在已有互動式篩選，可用來切換公司所擁有的裝置和個人擁有的裝置。 您可使用此篩選來查看分佈變更。

1. 選取交叉分析篩選器中的 [**公司**]，以查看公司擁有的裝置散發。
2. 選取交叉分析篩選器內的 [**個人**]，以查看個人擁有的裝置。

## <a name="next-steps"></a>後續步驟

- 在 Power BI 文件中深入了解在 Power BI Desktop [建立和管理關聯性](https://powerbi.microsoft.com/documentation/powerbi-desktop-create-and-manage-relationships/)。
- 請參閱 [Intune 資料倉儲模型](reports-ref-data-model.md)。

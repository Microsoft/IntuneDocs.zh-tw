---
title: 使用 Power BI 連線至資料倉儲
titleSuffix: Microsoft Intune
description: 您可以下載與 Microsoft Power BI 搭配使用的檔案，以載入 Microsoft Intune 租用戶動態產生的互動式報表。
keywords: Intune 資料倉儲
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/07/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: developer
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 5E5A35D3-88F8-441B-8A0B-C5D7A1E5137B
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8d7a5f67dfd8f7256559cb54d873ed48205ad751
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72490420"
---
# <a name="connect-to-the-data-warehouse-with-power-bi"></a>使用 Power BI 連線至資料倉儲

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

您可以使用 Power BI 相容性應用程式來為您的 Intune 租用戶載入動態產生的互動報表。 此外，您可以使用 OData 連結，在 Power BI 中載入您的租用戶資料。 Intune 會將連線設定提供給您的租用戶，讓您可以檢視與下列內容相關的下列範例報表及圖表：  

- 裝置
- 註冊
- 應用程式保護原則
- 相容性原則
- 裝置組態設定檔
- 軟體更新
- 裝置清查記錄

另外還有反白顯示註冊、合規性、裝置組態設定檔和軟體更新的趨勢。 範例圖表和報表會將使用者易記的篩選套用至畫布。 若要使用進階篩選，請參閱 Power BI Desktop 中的 [篩選]  窗格。

下列步驟示範如何下載 Power BI 檔案，以及如何搭配使用 OData 連結與 Power BI。

[!INCLUDE [reports-credential-reqs](../includes/reports-credential-reqs.md)]

## <a name="install-power-bi"></a>安裝 Power BI

安裝最新版本的 [Power BI Desktop](https://aka.ms/intune/datawarehouseapi/installpowerbi)。 如需詳細資訊，請參閱 [Power BI Desktop](https://powerbi.microsoft.com/desktop)

## <a name="load-the-data-and-reports-using-the-power-bi-intune-compliance-data-warehouse-app"></a>使用 Power BI Intune 相容性資料倉儲應用程式載入資料及報表

Power BI [Intune 合規性 (資料倉儲)](https://aka.ms/intune/datawarehouseapi/getpowerbiapp) 應用程式包含您租用戶的資訊，以及一組根據資料倉儲資料模型預先建置的報表。

1. 請瀏覽至 [Intune 合規性 (資料倉儲)](https://aka.ms/intune/datawarehouseapi/getpowerbiapp) 應用程式的 [AppSource]  頁面來開始安裝程序。
2. 按一下 [**立即取得**] 按鈕，然後按一下 [**繼續**]。
3. 當系統提示您安裝 Power BI 應用程式時，請按一下 [**安裝**]。
4. 安裝完成之後，請按一下 [ **Intune 合規性（資料倉儲）** 應用程式] 圖格。
5. 按一下 [連線]  按鈕。 [連接到 Intune 合規性 (資料倉儲)]  對話方塊隨即顯示。
6. 按一下 [登入]  按鈕。
7. 使用使用者帳戶登入，該使用者帳戶應具備擁有您欲檢視其報表租用戶的 Intune 資料倉儲存取權限。
8. 若要查看內含的儀表板，請按一下 [**儀表板**] 索引標籤，然後按一下 [**合規性總覽**] 儀表板
9. 若要查看所有可用的報表，請按一下 [**報表**] 索引標籤，然後按一下 [**合規性**v1.0] 報表。 按一下底部的索引標籤，流覽報表頁面。
10. 若要在稍後輕鬆巡覽至這些報表，請按一下 [相容性 V1.0]  報表旁邊的星號。 這會將報表新增到您 Power BI 我的最愛。

或者，您也可以從 Intune 入口網站安裝應用程式：

1. 登入 Azure 入口網站，並選擇 [監視 + 管理]   > [Intune]  。 您也可以搜尋 Intune 的資源。
2. 請開啟 [設定 Intune 資料倉儲]  刀鋒視窗。
3. 選取 [取得 Power BI 應用程式]  以在瀏覽器中存取及共用為您租用戶預先建置的 Power BI 報表。
4. 遵循上述的步驟 2 至 10。

## <a name="load-the-data-in-power-bi-using-the-odata-link"></a>使用 OData 連結在 Power BI 中載入資料

使用向 Azure AD 驗證的用戶端，OData URL 會連線至資料倉儲 API 中向報告用戶端公開資料模型的 RESTful 端點。 請遵循這些指示，使用 Power BI Desktop 連線並建立您自己的報表。 您不是只能使用 Power BI Desktop，但可以搭配使用最愛的分析工具與 OData URL，但前提是用戶端支援 OAUTH2.0 驗證和 OData 4.0 版標準。

1. 登入 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
2. 在 [總覽] 分頁右側的 [**其他**工作] 區段中，按一下 [**設定 Intune 資料倉儲**]。 將會顯示 [ **Intune 資料倉儲**] 分頁。
3. 從報告刀鋒視窗中擷取自訂摘要 URL，例如：<br>
    `https://fef.{yourinfo}.manage.microsoft.com/ReportingService/DataWarehouseFEService/dates?api-version=v1.0`
4. 開啟 [Power BI Desktop]  。
5. 選擇  **File**  > **取得資料**。 選取 [OData 摘要]  。
6. 選擇 [基本]  。
7. 將 [OData URL]  鍵入或貼入 URL 方塊。
8. 選取 [確定]  。
9. 如果尚未從 Power BI Desktop 用戶端向租用戶的 Azure AD 驗證您，請鍵入您的認證。 若要存取您的資料，您必須使用 OAuth 2.0 向 Azure Active Directory (Azure AD) 進行授權。  
    1. 選取 [組織帳戶]  。  
    2. 鍵入您的使用者名稱和密碼。  
    3. 選取 [登入]  。  
    4. 選取 [連線]  。  
10. 選取 [載入]  。

## <a name="next-steps"></a>後續步驟

您可以找到環境問題的答案，例如上週每日註冊的裝置數目。 您也可以在 Azure 中，使用從刀鋒視窗擷取的 Intune 資料倉儲 Power BI 報表，取得您 Intune 租用戶和用戶端母體的見解。 不過，Intune 會提供許多其他的方式，來延伸或重複使用資料。 Power BI 和 Intune 資料倉儲 API 提供額外的功能，例如：

<!-- - You can use Power BI Desktop to create additional report types with your data. For example, you could create a custom chart representing the ratio of device manufactures in your enterprise. For more information about creating custom reports with Power BI and the Intune Data Warehouse, see `BLOG POST ON POWER BI`. -->
- 已組織您的租用戶資料，協助您從資料中提取深入解析。 如需資料組織方式的詳細資訊，請參閱[資料倉儲資料模型](reports-ref-data-model.md)。
- 您也可以從 RESTful 介面存取資料，並且將資料併入您自己的應用程式。 如需詳細資訊，請參閱[使用 REST 用戶端從資料倉儲 API 取得資料](../reports-proc-data-rest.md)。

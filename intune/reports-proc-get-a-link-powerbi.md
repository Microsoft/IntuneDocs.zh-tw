---
title: "使用 Power BI 連線至資料倉儲 | Microsoft Docs"
description: "您可以下載與 Microsoft Power BI 搭配使用的檔案，以載入 Intune 租用戶的互動式、動態產生的報表。"
keywords: "Intune 資料倉儲"
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/13/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5E5A35D3-88F8-441B-8A0B-C5D7A1E5137B
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: fa7c578cd8dba84910bae9b9f204c8057c76bf6b
ms.sourcegitcommit: 2c7794848777e73d6a9502b4e1000f0b07ac96bc
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/01/2018
---
# <a name="connect-to-the-data-warehouse-with-power-bi"></a>使用 Power BI 連線至資料倉儲

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

您可以下載與 Microsoft Power BI 搭配使用的檔案，以載入 Intune 租用戶的互動式、動態產生的報表。 資料倉儲 Power BI 檔案 (pbix) 包含您租用戶的連線設定，以及下列範例報表和圖表：  

  -  裝置
  -  註冊
  -  應用程式保護原則
  -  相容性原則
  -  裝置組態設定檔
  -  軟體更新
  -  裝置清查記錄

另外還有反白顯示註冊、合規性、裝置組態設定檔和軟體更新的趨勢。 範例圖表和報表會將使用者易記的篩選套用至畫布。 若要使用進階篩選，請參閱 Power BI Desktop 中的 [篩選] 窗格。

下列步驟示範如何下載 Power BI 檔案，以及如何搭配使用 OData 連結與 Power BI。

[!INCLUDE[reports-credential-reqs](./includes/reports-credential-reqs.md)]

## <a name="install-power-bi"></a>安裝 Power BI

安裝最新版本的 Power BI Desktop。 您可以從 [PowerBI.microsoft.com](https://powerbi.microsoft.com/desktop) 下載 Power BI Desktop。

## <a name="load-the-data-and-reports-using-the-power-bi-file-pbix"></a>使用 Power BI 檔案 (pbix) 載入資料和報表

Power BI 檔案 (pbix) 包含您租用戶的連線資訊以及一組根據資料倉儲資料模型的預先建置報表。 在 Power BI Desktop 中開啟檔案，並登入 Azure AD。 報表會從 Intune 租用戶載入資料。

> [!Important]  
> 每個 Power BI 檔案 (pbix) 可能會根據租用戶位置而有所不同。 如果您要管理多個 Intune 租用戶，請務必使用登入該租用戶時從 Azure 入口網站下載的檔案。  

1.  登入 Azure 入口網站，並選擇 [監視 + 管理] > [Intune]。 您也可以搜尋 **Intune** 的資源。  
2.  開啟 [Microsoft Intune 資料倉儲 API (預覽)] 刀鋒視窗。
3.  選取 [Download PowerBI file] (下載 PowerBI 檔案)。 副檔名為 (pbix) 的檔案會下載至您指定的位置。
4.  使用 Power BI 開啟檔案。 「Intune 資料倉儲報表」 即會載入，但可能需要一秒才能取得租用戶資料。
5.  選取 [重新整理] 載入您的租用戶資料以及檢閱報表。
6.  如果尚未使用 Azure Active Directory 認證來驗證 Power BI，Power BI 會提示您提供認證。 選取您的認證時，請選擇 [組織帳戶] 作為驗證方法。

## <a name="load-the-data-in-power-bi-using-the-odata-link"></a>使用 OData 連結在 Power BI 中載入資料

使用向 Azure AD 驗證的用戶端，OData URL 會連線至資料倉儲 API 中向報告用戶端公開資料模型的 RESTful 端點。 請遵循這些指示，使用 Power BI Desktop 連線並建立您自己的報表。 您不是只能使用 Power BI Desktop，但可以搭配使用最愛的分析工具與 OData URL，但前提是用戶端支援 OAUTH2.0 驗證和 OData 4.0 版標準。

1.  登入 Azure 入口網站，並選擇 [監視 + 管理] > [Intune]。 您也可以搜尋 **Intune** 的資源。  
2.  開啟 [Microsoft Intune 資料倉儲 API (預覽)] 刀鋒視窗。
3. 從報告刀鋒視窗中擷取自訂摘要 URL，例如 `https://fef.{yourinfo}.manage.microsoft.com/ReportingService/DataWarehouseFEService/dates?api-version=beta`。
4. 開啟 [Power BI Desktop]。
5. 選擇 [首頁] > [取得資料]。 選取 [OData 摘要]。
6. 選擇 [基本]。
7. 將 [OData URL] 鍵入或貼入 URL 方塊。
8. 選取 [確定]。
9. 如果尚未從 Power BI Desktop 用戶端向租用戶的 Azure AD 驗證您，請鍵入您的認證。 若要存取您的資料，您必須使用 OAuth 2.0 向 Azure Active Directory (Azure AD) 進行授權。  
    1.  選取 [組織帳戶]。  
    2.  鍵入您的使用者名稱和密碼。  
    3.  選取 [登入]。  
    4.  選取 [連線]。  
10. 選取 [載入]。

## <a name="next-steps"></a>接下來的步驟

您可以找到環境問題的答案，例如上週每日註冊的裝置數目。 您可以深入了解使用報表的 Intune 租用戶和用戶端母群體，而報表使用 Azure 中刀鋒視窗所擷取的 Intune 資料倉儲 Power BI 檔案 (pbix)。 不過，Intune 會提供許多其他的方式，來延伸或重複使用資料。 還有更多方式可以使用 Power BI 和 Intune 資料倉儲 API，例如：

<!-- -  You can use Power BI Desktop to create additional report types with your data. For example, you could create a custom chart representing the ratio of device manufactures in your enterprise. For more information about creating custom reports with Power BI and the Intune Data Warehouse, see `BLOG POST ON POWER BI`. -->
 -  已組織您的租用戶資料，協助您從資料中提取深入解析。 如需資料組織方式的詳細資訊，請參閱[資料倉儲資料模型](reports-ref-data-model.md)。
 -  您也可以從 RESTful 介面存取資料，並且將資料併入您自己的應用程式。 如需詳細資訊，請參閱[使用 REST 用戶端從資料倉儲 API 取得資料](reports-proc-data-rest.md)。

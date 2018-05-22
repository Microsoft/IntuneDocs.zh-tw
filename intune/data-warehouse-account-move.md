---
title: 移動您的 Intune 資料倉儲帳戶資料
titlesuffix: Microsoft Intune
description: 了解如何在移動您的帳戶時，備份 Intune 資料倉儲資料。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 05/15/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ee3ccbf9-82fc-4fbf-9d3d-8f05e431d090
ms.reviewer: aanavath
ms.suite: ems
ms.custom: ''
ms.openlocfilehash: f1b2af2723ddb4c89f7f3d6409ced12f7a16883a
ms.sourcegitcommit: 34e96e57af6b861ecdfea085acf3c44cff1f3d43
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2018
---
# <a name="move-your-intune-data-warehouse-account-data"></a>移動您的 Intune 資料倉儲帳戶資料 

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

如果您要求移動帳戶，則表示您想要將資料中心變更成另一個位置。 移動之後，會重設您的資料倉儲，並根據指定的開始移動日期，在新的位置記錄資料。 若要備份先前的資料倉儲資料，請**先**完成下列步驟，然後再移動帳戶。 大部分的資料倉儲資料表格會保留資料 30 天，因此當您移動帳戶之後，這些表格中如有任何的資料差異，也不會保留 30 天。 若要深入了解特定表格的保留期限，請參閱[資料倉儲資料模型](reports-ref-data-model.md)。 

## <a name="back-up-your-data-warehouse-data"></a>備份您的資料倉儲資料 

若要備份資料倉儲資料，您必須使用 Data Warehouse API 將資料倉儲資料儲存至一個 *.csv* 檔案：  

1. 如果您是第一次使用 Data Warehouse API，請依照[使用 REST 用戶端從 Intune Data Warehouse API 取得資料](reports-proc-data-rest.md)提供的一次性程序執行。
2. 使用標題為[使用 PowerShell 存取 Intune 資料倉儲](https://github.com/Microsoft/Intune-Data-Warehouse/tree/master/Samples/PowerShell)的 PowerShell 範例，將您所有的資料下載至 CSV 檔案。 

## <a name="back-up-your-trend-charts-from-the-azure-portal"></a>從 Azure 入口網站備份您的趨勢圖

Azure 入口網站檢視中的某些趨勢圖表會重設。 您可以在 **Graph** 中執行以下的指令碼，即可備份這些圖表：   

### <a name="terms--conditions-acceptance-reports"></a>條款和條件接受報表
1. 在 Azure 入口網站中，依序瀏覽至 [Microsoft Intune] -> [裝置註冊] -> [條款和條件]。
2. 至於每個 [條款和條件]項目，選取 [接受報表]，然後選取 [匯出]。
3. 將報表儲存在本機。
 
### <a name="app-protection-reports"></a>應用程式保護報表  
1. 在 Azure 入口網站中，依序瀏覽至 [Microsoft Intune] -> [行動應用程式] -> [應用程式保護狀態]。
2. 按一下下載圖示 （⤓） 來儲存每個報表。

### <a name="device-configuration-charts"></a>裝置設定圖表 
1. 在 Azure 入口網站中，依序瀏覽至 [Microsoft Intune] -> [DeviceConfiguration]。
2. 使用 Microsoft [Graph Explorer](https://developer.microsoft.com/graph/graph-explorer)，下載圖表背後的資料。 
    - 如需所有裝置的所有裝置組態設定檔部署狀態，請參閱[裝置部署狀態](https://graph.microsoft.com/beta/reports/deviceConfigurationDeviceActivity/content)。

    - 如需所有使用者的所有裝置組態設定檔部署狀態，請參閱[使用者部署狀態](https://graph.microsoft.com/beta/reports/deviceConfigurationUserActivity/content)。

    - 如需設定檔部署狀態，請參閱[提供部署狀態](https://graph.microsoft.com/beta/deviceManagement/deviceConfigurations?$select=id,displayName,lastModifiedDateTime,deviceStatusOverview&$expand=deviceStatusOverview)。
  
    > [!NOTE]
    > 您必須擁有有效的權杖，才能存取裝置組態和部署狀態資訊。

## <a name="device-enrollment-charts"></a>裝置註冊圖表
1. 在 Azure 入口網站中，依序瀏覽至 [Microsoft Intune] -> [DeviceEnrollment]。
2. 使用 Microsoft [Graph Explorer](https://developer.microsoft.com/graph/graph-explorer)，下載圖表背後的資料。
    - 如需註冊狀態，請參閱 
    - 如需本週排名在前的註冊失敗， 
    - 如需註冊狀態，請複製這個[註冊狀態查詢](https://graph.microsoft.com/beta/reports/managedDeviceEnrollmentFailureTrends()/content)並將它貼到 [Graph Explorer](https://developer.microsoft.com/graph/graph-explorer)。
    - 如需本週排名在前的註冊失敗，請複製這個[註冊失敗查詢](https://graph.microsoft.com/beta/reports/managedDeviceEnrollmentTopFailures(period=null)/content)並將它貼到 [Graph Explorer](https://developer.microsoft.com/graph/graph-explorer)。

    > [!NOTE]
    > 您必須擁有有效的驗證權杖，才能存取裝置註冊資料。 

## <a name="after-a-data-warehouse-account-move"></a>移動資料倉儲帳戶之後

移動資料倉儲帳戶之後，您會在 Intune 中看到資料倉儲已重設，而且您的資料現在是儲存到新的位置。 圖表和匯出選項會重設，而且您會看到一則通知，如果按一下這一則通知，會開放一篇文章並解釋為什麼要重設圖表。  

## <a name="data-warehouse-move-example"></a>資料倉儲移動範例 

客戶 X 要求在 1/06/2018 開始移動帳戶。 在回應要求時，客戶會收到一個連結，按一下這個連結就會開啟一個文件，裡面詳細說明如果他們想備份以前的資料倉儲，此時應該採取的步驟。 在 1/06/2018，資料倉儲以及它支援的圖表將會重設，並開始將資料儲存到新的資料中心。 

## <a name="next-steps"></a>接下來的步驟

 - 了解[每週的 Intune 新功能](whats-new.md)。 您也可以了解即將推出的變更、關於服務的重要通知，以及過去版本的相關資訊。
 - 閱讀 [Microsoft Intune 部落格](http://go.microsoft.com/fwlink/?LinkID=273882)。

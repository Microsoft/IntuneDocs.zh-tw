---
title: 監視 Microsoft Intune 中的 Exchange 條件式存取
titlesuffix: ''
description: 透過 Intune Azure 入口網站監視內部部署 Exchange 和 Exchange Online 的條件式存取相容性。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/22/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 5712682d-285b-43fd-9978-3dcfd95ec5f9
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 2ff5686e2d83831259bd21bee164b3c187e1c0ee
ms.sourcegitcommit: fffa64f28278573dc83a846b647315def2108781
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2018
ms.locfileid: "48231350"
---
# <a name="monitor-conditional-access-compliance-for-on-premises-exchange-and-exchange-online-in-intune"></a>在 Intune 中監視內部部署 Exchange 和 Exchange Online 的條件式存取合規性

從 Intune 1704 版本開始，系統管理員可以透過內部部署 Exchange Connector 或 Intune Service to Service Connector (Exchange Online Connector)，查看與 Intune 同步處理的 Exchange ActiveSync 裝置記錄相關的報告資訊。 條件式存取合規性報告提供包含不同同步處理狀態的裝置摘要：

-   **允許**

-   **封鎖**

-   **隔離**

## <a name="to-monitor-conditional-access-compliance"></a>監視條件式存取合規性

1.  移至 [Azure 入口網站](https://portal.azure.com/)，並使用您的 Intune 認證登入。

2.  成功登入之後，您會看到 [Azure 儀表板]。

3.  選擇左功能表中的 [All services] (所有服務)，然後在文字方塊篩選中鍵入 **Intune**。

4.  選擇 [Intune]，您會看到 [Intune 儀表板]。

5.  選擇 [條件式存取]，然後選擇 [概觀]。

6.  選擇圖表上三個區域 ([允許]、[封鎖] 或 [隔離]) 的其中一個，以檢視您的條件式存取相容性報告。

    ![條件式存取儀表板的影像](./media/CA-reporting-intune-1.png)

一旦您選擇三個區域的其中一個，就可以查看有關已允許、封鎖或隔離之裝置的更多詳細資料。

您也可以針對特定裝置向下鑽研，以查看更多詳細資料。 例如，下列影像上所選擇的裝置已被封鎖。 Intune 提供您從 [條件式存取相容性報告] 窗格移除公司資料的選項。

![條件式存取裝置詳細資料報告的影像](./media/CA-reporting-intune-3.png)

在 [裝置詳細資料] 窗格中，您可以檢視更多資訊︰

-   **概觀︰** 您可以查看下列裝置屬性：OS 版本、裝置型號、擁有權、序號、裝置製造商、電話號碼，以及裝置最後一次簽入的時間。

-   **屬性︰** 您可以設定裝置擁有權 (個人或公司)。

-   **硬體︰** 提供您在 [概觀] 上看到的資訊，以及儲存體詳細資料 (總空間和可用空間)、系統機箱、網路詳細資料、網路服務，以及更多的條件式存取封鎖詳細資料。

-   **探索到的應用程式：** 顯示您裝置上所安裝的所有應用程式。 您也可以將已安裝應用程式的清單以 .CSV 格式匯出。

-   **合規性︰** 顯示所有裝置合規性原則詳細資料。

-   **裝置設定︰** 顯示所有裝置設定詳細資料。

-   **Exchange 存取：** 您可以在這裡深入了解套用條件式存取原則之後的裝置狀態。

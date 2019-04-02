---
title: 稽核變更及 Microsoft Intune-Azure 中的事件 |Microsoft Docs
description: 了解如何檢閱記錄 Microsoft Intune 活動的稽核記錄。
keywords: ''
ms.author: dougeby
author: dougeby
manager: dougeby
ms.date: 03/18/2019
ms.topic: troubleshooting
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 6ee841cc-5694-4ba1-8f66-1d58edec30a4
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 93072ba4730de0252f54d93fa1169062d496ce38
ms.sourcegitcommit: 1069b3b1ed593c94af725300aafd52610c7d8f04
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 03/22/2019
ms.locfileid: "58394896"
---
# <a name="use-audit-logs-to-track-and-monitor-events-in-microsoft-intune"></a>使用稽核記錄，來追蹤和監視在 Microsoft Intune 中的事件

稽核記錄包含 Microsoft Intune 中產生變更的活動記錄。 建立、 更新 （編輯）、 刪除、 指派和遠端動作所有建立的系統管理員可以檢閱大部分 Intune 工作負載的稽核事件。 根據預設，所有客戶啟用稽核。 無法停用它。

> [!NOTE]
> 稽核事件會開始錄製在 2017 年 12 月功能版本。 無法使用先前的事件。

## <a name="who-can-access-the-data"></a>誰可以存取資料？

具有下列權限的使用者可以檢閱稽核記錄：

- 全域管理員
- Intune 服務管理員
- 指派了具有**稽核資料** - **讀取**權限之 Intune 角色的系統管理員

## <a name="audit-logs-for-intune-workloads"></a>Intune 工作負載的稽核記錄

您可以檢閱每個 Intune 工作負載監視群組中的稽核記錄：

1. 在 [Azure 入口網站](https://portal.azure.com/)中，選取 [所有服務] > 篩選 [Intune] > 選取 [Intune]。
2. 選擇您想要檢閱稽核記錄檔的工作負載。 例如，選取**裝置**。
3. 底下**監視**，選擇**稽核記錄檔**。

## <a name="route-logs-to-azure-monitor"></a>將記錄路由至 Azure 監視器

稽核記錄檔和操作記錄檔也可以路由至 Azure 監視器。 在 **稽核記錄檔**，選取**匯出資料設定**:

![將記錄檔資料匯出至 Azure 監視器，只要選取 在 Intune 中的 匯出資料設定](./media/audit-logs-export-data-settings.png)

如需此功能的詳細資訊，請參閱[將記錄資料傳送至儲存體、事件中樞或記錄分析](review-logs-using-azure-monitor.md)。

## <a name="review-audit-events"></a>檢閱稽核事件

![若要查看動作和事件發生的日期的 Intune 中選擇的稽核記錄](./media/monitor-audit-logs.png "稽核記錄檔")

稽核記錄具有顯示下列項目的預設清單檢視：

- 發生的日期和時間
- 初始者 (執行者)
- 應用程式名稱
- 活動
- 目標
- Category
- 狀態

若要查看事件的相關具體資訊，請在清單中選取項目：

![取得何人在稽核記錄，在 Intune 中的相關資訊](./media/monitor-audit-log-detail.png "稽核記錄檔詳細資料")

> [!NOTE]
> **初始者 （執行者）** 包含有關誰執行工作，及執行位置。 例如，如果您在 Azure 入口網站內執行 Intune 的活動，則 [應用程式] 一律會列出 [Microsoft Intune portal extension] \(Microsoft Intune 入口網站延伸模組\)，且 [應用程式識別碼] 一律使用相同的 GUID。
> 
> [目標] 區段會列出多個目標及已變更的屬性。  

## <a name="filter-audit-events"></a>篩選稽核事件

每個工作負載都有一個功能表項目，可預先篩選與該窗格相關的稽核事件類別。 個別的篩選條件選項可讓您變更為不同的類別，以及該類別中的事件動作詳細資料。 您可以搜尋 UPN，例如執行該動作的使用者。 日期範圍篩選條件允許 24 個小時、7 天或 30 天的選項。 根據預設，會顯示過去 30 天的稽核事件。

## <a name="use-graph-api-to-retrieve-audit-events"></a>使用 Graph API 來擷取稽核記錄

如需有關使用圖形 API 來取得最多達一年稽核事件的詳細資訊，請參閱[List auditEvents](https://docs.microsoft.com/graph/api/intune-auditing-auditevent-list?view=graph-rest-1.0)。

## <a name="next-steps"></a>後續步驟

[將記錄資料傳送至儲存體、 事件中樞，或記錄分析](review-logs-using-azure-monitor.md)。

[檢閱用戶端應用程式保護記錄](app-protection-policy-settings-log.md)。

---
title: 稽核 Microsoft Intune 中的變更與事件 - Azure | Microsoft Docs
description: 了解如何檢閱記錄 Microsoft Intune 活動的稽核記錄。
keywords: ''
ms.author: dougeby
author: dougeby
manager: dougeby
ms.date: 03/18/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 6ee841cc-5694-4ba1-8f66-1d58edec30a4
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: fd00a0ae4cb6c3b150fe40cfc6cd7b71cfa973f3
ms.sourcegitcommit: 0be25b59c8e386f972a855712fc6ec3deccede86
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72585251"
---
# <a name="use-audit-logs-to-track-and-monitor-events-in-microsoft-intune"></a>使用稽核記錄追蹤與監視 Microsoft Intune 中的事件

稽核記錄包含 Microsoft Intune 中產生變更的活動記錄。 系統管理員可以檢閱大部分 Intune 工作負載之所有建立稽核事件的建立、更新 (編輯)、刪除、指派和遠端動作。 根據預設，所有客戶都啟用稽核。 無法停用。

> [!NOTE]
> 稽核事件從 2017 年 12 月的功能版本起開始記錄。 無法取得在此之前的事件。

## <a name="who-can-access-the-data"></a>誰可以存取資料？

具有下列權限的使用者可以檢閱稽核記錄：

- 全域管理員
- Intune 服務管理員
- 指派了具有**稽核資料** - **讀取**權限之 Intune 角色的系統管理員

## <a name="audit-logs-for-intune-workloads"></a>Intune 工作負載的稽核記錄

您可以檢閱每個 Intune 工作負載監視群組中的稽核記錄：

1. 登入 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
2. 選擇您想要檢閱稽核記錄檔的工作負載。 例如，選取 [裝置]  。
3. 在 [監視]  下，選擇 [稽核記錄檔]  。

## <a name="route-logs-to-azure-monitor"></a>將記錄路由至 Azure 監視器

稽核記錄檔和操作記錄檔也可以路由至 Azure 監視器。 在 [稽核記錄檔]  中，選取 [匯出資料設定]  ：

![選取 Intune 的 [匯出資料設定]，將記錄檔資料匯出至 Azure 監視器](./media/monitor-audit-logs/audit-logs-export-data-settings.png)

> [!NOTE]
> 如需這項功能的詳細資訊，並檢查其使用的必要條件，請參閱[將記錄資料傳送至儲存體、事件中樞或 log analytics](review-logs-using-azure-monitor.md)。

## <a name="review-audit-events"></a>檢閱稽核事件

![選擇 Intune 中的稽核記錄檔查看事件發生時的動作和日期](./media/monitor-audit-logs/monitor-audit-logs.png "稽核記錄檔")

稽核記錄具有顯示下列項目的預設清單檢視：

- 發生的日期和時間
- 初始者 (執行者)
- 應用程式名稱
- 活動
- 目標
- Category
- 狀態

若要查看事件的相關具體資訊，請在清單中選取項目：

![取得誰對 Intune 稽核記錄檔做了什麼事的特定資訊](./media/monitor-audit-logs/monitor-audit-log-detail.png "|::ref2::|")

> [!NOTE]
> **初始者 (執行者)** 包含誰執行了工作以及工作在哪裡執行的資訊。 例如，如果您在 Azure 入口網站內執行 Intune 的活動，則 [應用程式]  一律會列出 [Microsoft Intune portal extension] \(Microsoft Intune 入口網站延伸模組\)  ，且 [應用程式識別碼]  一律使用相同的 GUID。
>
> [目標]  區段會列出多個目標及已變更的屬性。  

## <a name="filter-audit-events"></a>篩選稽核事件

每個工作負載都有一個功能表項目，可預先篩選與該窗格相關的稽核事件類別。 個別的篩選條件選項可讓您變更為不同的類別，以及該類別中的事件動作詳細資料。 您可以根據 UPN (例如，執行該動作的使用者) 來搜尋。 日期範圍篩選條件允許 24 個小時、7 天或 30 天的選項。 根據預設，會顯示過去 30 天的稽核事件。

## <a name="use-graph-api-to-retrieve-audit-events"></a>使用 Graph API 來擷取稽核記錄

如需使用圖形 API 取得最多一年之稽核事件的詳細資料，請參閱 [List auditEvents](https://docs.microsoft.com/graph/api/intune-auditing-auditevent-list?view=graph-rest-1.0) (列出 auditEvents)。

## <a name="next-steps"></a>後續步驟

[將記錄資料傳送至儲存體、事件中樞或 Log Analytics](review-logs-using-azure-monitor.md)。

[檢閱用戶端應用程式保護記錄](../apps/app-protection-policy-settings-log.md)。

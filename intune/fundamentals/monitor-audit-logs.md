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
ms.openlocfilehash: d6af0718f2b926383bb943b6321b4d5839346ce7
ms.sourcegitcommit: df8e2c052fafb2d5d4e9b4fcd831ae0ecf7f8d16
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991985"
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

1. 登入 [Microsoft 端點管理員系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。
2. 選取 [**租使用者管理**] > [ **Audit logs**]。
3. 若要篩選結果，請選取 [**篩選**]，然後使用下列選項來精簡結果。
    - **類別**：例如**合規性**、**裝置**和**角色**。
    - **活動**：此處所列的選項受限於 [**類別**] 底下選擇的選項。
    - **日期範圍**：您可以選擇過去一個月、一周或一天的記錄。
4. 選擇 [套用]  。
4. 選取清單中的專案，以查看活動詳細資料。

## <a name="route-logs-to-azure-monitor"></a>將記錄路由至 Azure 監視器

稽核記錄檔和操作記錄檔也可以路由至 Azure 監視器。 在 [稽核記錄檔]  中，選取 [匯出資料設定]  ：

![選取 Intune 的 [匯出資料設定]，將記錄檔資料匯出至 Azure 監視器](./media/monitor-audit-logs/audit-logs-export-data-settings.png)

> [!NOTE]
> 如需這項功能的詳細資訊，並檢查其使用的必要條件，請參閱[將記錄資料傳送至儲存體、事件中樞或 log analytics](review-logs-using-azure-monitor.md)。

> [!NOTE]
> **初始者 (執行者)** 包含誰執行了工作以及工作在哪裡執行的資訊。 例如，如果您在 Azure 入口網站內執行 Intune 的活動，則 [應用程式]  一律會列出 [Microsoft Intune portal extension] \(Microsoft Intune 入口網站延伸模組\)  ，且 [應用程式識別碼]  一律使用相同的 GUID。
>
> [目標]  區段會列出多個目標及已變更的屬性。  

## <a name="use-graph-api-to-retrieve-audit-events"></a>使用 Graph API 來擷取稽核記錄

如需使用圖形 API 取得最多一年之稽核事件的詳細資料，請參閱 [List auditEvents](https://docs.microsoft.com/graph/api/intune-auditing-auditevent-list?view=graph-rest-1.0) (列出 auditEvents)。

## <a name="next-steps"></a>後續步驟

[將記錄資料傳送至儲存體、事件中樞或 Log Analytics](review-logs-using-azure-monitor.md)。

[檢閱用戶端應用程式保護記錄](../apps/app-protection-policy-settings-log.md)。

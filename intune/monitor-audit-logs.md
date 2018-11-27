---
title: Microsoft Intune 活動的稽核記錄
description: 了解如何檢閱記錄 Microsoft Intune 活動的稽核記錄。
keywords: ''
ms.author: dougeby
author: dougeby
manager: dougeby
ms.date: 02/27/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 6ee841cc-5694-4ba1-8f66-1d58edec30a4
search.appverid: MET150
ms.openlocfilehash: d9ecfa44e2619e5e123c9e8af169b6a8a95ee466
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2018
ms.locfileid: "52183888"
---
# <a name="audit-logs-for-intune-activities"></a>Intune 活動的稽核記錄
稽核記錄提供您在 Microsoft Intune 中產生變更之活動的記錄。 Create、Update (編輯)、Delete 和 Assign 動作或遠端工作會產生您可以檢閱的稽核事件。 您可以檢閱大部分 Intune 工作負載的稽核記錄。 預設會為所有客戶啟用稽核，且無法停用。 從 2017 年 12 月的功能發行日期開始記錄稽核事件；先前的事件都無法使用。

## <a name="who-can-access-the-data"></a>誰可以存取資料？
具有下列權限的使用者可以檢閱稽核記錄：
- 全域管理員
- Intune 服務管理員
- 指派了具有**稽核資料** - **讀取**權限之 Intune 角色的系統管理員

## <a name="audit-logs-for-intune-workloads"></a>Intune 工作負載的稽核記錄
您可以檢閱每個 Intune 工作負載「監視」群組中的稽核記錄。  
1. 登入 [Azure 入口網站](https://portal.azure.com)。
2. 選擇 [All services] (所有服務) > [Intune]。 Intune 位於 [Monitoring + Management] (監視 + 管理) 區段。
3. 在 [Intune] 窗格中，選擇您想要檢閱稽核記錄的工作負載，例如 [裝置]。
4. 在工作負載的 [監視] 群組中，選擇 [稽核記錄檔]。

## <a name="review-audit-events"></a>檢閱稽核事件
![稽核記錄](./media/monitor-audit-logs.png "稽核記錄")

稽核記錄具有顯示下列項目的預設清單檢視：    

- 發生的日期和時間
- 初始者 (執行者)
- 應用程式名稱
- 活動
- 目標
- Category
- 狀態

按一下清單檢視中的項目，就可取得其所有可用詳細資料。

![稽核記錄](./media/monitor-audit-log-detail.png "稽核記錄")

> [!Note]    
> 稽核記錄詳細資料中的 [初始者 (執行者)] 區段提供執行活動人員和執行活動所在位置的相關資訊。 例如，如果您在 Azure 入口網站內的 Intune 中執行活動，[應用程式] 一律會列出 [Microsoft Intune 入口網站擴充]，且 [應用程式識別碼] 一律會使用相同的 GUID。 
>    
> [目標] 區段可以列出多個目標及變更的屬性。  


## <a name="filter-audit-events"></a>篩選稽核事件
每個工作負載都有一個功能表項目，可預先篩選與該窗格相關的稽核事件類別。 個別的篩選條件選項可讓您變更為不同的類別，以及該類別中的事件動作詳細資料。 您可以根據 UPN (例如，執行該動作的使用者) 來搜尋。 日期範圍篩選條件允許 24 個小時、7 天或 30 天的選項。 根據預設，會顯示過去 30 天的稽核記錄。

## <a name="use-graph-api-to-retrieve-audit-events"></a>使用 Graph API 來擷取稽核記錄
如需如何使用 Graph API 來擷取最多達一年稽核記錄的詳細資料，請參閱 [List auditEvents](https://developer.microsoft.com/en-us/graph/docs/api-reference/beta/api/intune_auditing_auditevent_list)。
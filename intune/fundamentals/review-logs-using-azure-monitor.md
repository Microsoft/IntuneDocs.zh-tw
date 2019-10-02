---
title: 使用 Microsoft Intune 將記錄路由傳送到 Azure 監視器 - Azure | Microsoft Docs
description: 使用診斷設定，將 Microsoft Intune 中的稽核記錄和操作記錄傳送至 Azure 儲存體帳戶、事件中樞或 Log Analytics。 選擇您想要保留資料的時間長度，並查看一些適用於不同大小租用戶的估計成本。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 08/28/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: shpate
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 99799f695b9398c455f92220c436c7a6c6d76d56
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2019
ms.locfileid: "71721847"
---
# <a name="send-log-data-to-storage-event-hubs-or-log-analytics-in-intune-preview"></a>將記錄資料傳送至 Intune (預覽) 中的儲存體、事件中樞或 Log Analytics

Microsoft Intune 包含下列內建記錄，可提供您環境的相關資訊：

- **稽核記錄**會顯示 Intune 中所發生之不同事件或工作的詳細資料。
- **作業記錄 (預覽)** 會顯示註冊成功 (或失敗) 的使用者和裝置詳細資料，以及不相容裝置的詳細資料。
- **裝置相容性組織記錄 (預覽)** 會顯示 Intune 中裝置相容性的組織報告，以及不相容裝置的詳細資料。

這些記錄也可傳送至 Azure 監視器服務，包括儲存體帳戶、事件中樞和 Log Analytics。 具體而言，您可以：

* 將 Intune 記錄封存到 Azure 儲存體帳戶以保留資料，或封存一段時間。
* 使用熱門的安全性資訊及事件管理 (SIEM) 工具 (例如 Splunk 和 QRadar)，將 Intune 記錄串流處理到 Azure 事件中樞以供分析。
* 藉由將 Intune 記錄串流處理到事件中樞，以便將它們與您自己的自訂記錄解決方案整合。
* 將 Intune 記錄傳送至 Log Analytics，以啟用與已連線資料相關的豐富視覺效果、監視及警示。

這些功能都屬於 Intune 中的**診斷設定**。

本文示範如何使用**診斷設定**來將記錄資料傳送至不同的服務、提供範例和成本估計，並回答一些常見問題。 啟用此功能之後，系統即會將您的記錄路由傳送到所選 Azure 監視器服務。

## <a name="prerequisites"></a>必要條件

若要使用此功能，您需要：

* Azure 訂用帳戶：如果您沒有 Azure 訂用帳戶，您可以[註冊免費試用](https://azure.microsoft.com/free/)。
* Azure 中的 Microsoft Intune 環境 (租用戶)
* 具備 Intune 租用戶之**全域系統管理員**或 **Intune 服務管理員**身分的使用者。

根據您想要路由傳送稽核記錄資料的位置而定，您需要下列其中一個服務：

* 具有 *ListKeys* 權限的 [Azure 儲存體帳戶](https://docs.microsoft.com/azure/storage/common/storage-account-overview)。 我們建議您使用一般儲存體帳戶，而不是 Blob 儲存體帳戶。 如需儲存體價格資訊，請參閱 [Azure 儲存體價格計算機](https://azure.microsoft.com/pricing/calculator/?service=storage)。 
* 可與協力廠商解決方案整合的 [Azure 事件中樞命名空間](https://docs.microsoft.com/azure/event-hubs/event-hubs-create#create-an-event-hubs-namespace)。
* 可將記錄傳送至 Log Analytics 的 [Azure Log Analytics 工作區](https://docs.microsoft.com/azure/azure-monitor/learn/quick-create-workspace)。

## <a name="send-logs-to-azure-monitor"></a>將記錄傳送至 Azure 監視器

1. 登入 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
2. 在 [監視]  底下，選取 [診斷設定]  。 當您第一次開啟時，請將它設為開啟。 否則，請新增設定。

    ![在 Intune 中開啟 [診斷設定]，以將記錄傳送至 Azure 監視器](./media/review-logs-using-azure-monitor/diagnostics-settings-turn-on.png)

3. 輸入下列內容：

    - **名稱**：輸入診斷設定的名稱。 此設定包含您輸入的所有屬性。 例如，輸入 `Route audit logs to storage account`。
    - **封存至儲存體帳戶**：將記錄資料儲存至 Azure 儲存體帳戶。 如果您想要儲存或封存資料，請使用此選項。

        1. 選取此選項 > [設定]  。 
        2. 從清單中選擇現有的儲存體帳戶 > [確定]  。

    - **串流至事件中樞**：將記錄串流處理至 Azure 事件中樞。 如果您想要使用 Splunk 和 QRadar 之類的 SIEM 工具來分析記錄資料，請選擇此選項。

        1. 選取此選項 > [設定]  。 
        2. 從清單中選擇現有的事件中樞命名空間和原則 > [確定]  。

    - **傳送至 Log Analytics**：將資料傳送至 Azure Log Analytics。 如果您想要針對記錄使用視覺效果、監視和警示，請選擇此選項。

        1. 選取此選項 > [設定]  。 
        2. 建立新的工作區，然後輸入工作區詳細資料。 或者，從清單中選擇現有的工作區 > [確定]  。

            [Azure Log Analytics 工作區](https://docs.microsoft.com/azure/azure-monitor/learn/quick-create-workspace)提供更多有關這些設定的詳細資料。

    - [LOG]   > [AuditLogs]  ：選擇此選項，以將 [Intune 稽核記錄](../monitor-audit-logs.md)傳送至您的儲存體帳戶、事件中樞或 Log Analytics。 稽核記錄會顯示每個在 Intune 中產生變更之工作的歷程，包括進行變更的人員與時間。

      如果您選擇使用儲存體帳戶，則也請輸入您想要保留資料的天數 (保留期)。 若要永久保留資料，將 [保留期 (天數)]  設為 `0` (零)。

    - [LOG]   > [OperationalLogs]  ：作業記錄 (預覽) 會顯示在 Intune 中註冊之使用者和裝置的成功或失敗，以及不符合規範的裝置詳細資料。 選擇此選項，以將註冊記錄傳送至您的儲存體帳戶、事件中樞或 Log Analytics。

      如果您選擇使用儲存體帳戶，則也請輸入您想要保留資料的天數 (保留期)。 若要永久保留資料，將 [保留期 (天數)]  設為 `0` (零)。

      > [!NOTE]
      > 作業記錄目前為預覽狀態。 若要提供意見反應 (包括作業記錄中的資訊)，請移至 [UserVoice](https://microsoftintune.uservoice.com/forums/291681-ideas/suggestions/36613948-diagnostics-settings-feedback)。

    - **LOG** > **DeviceComplianceOrg**:裝置相容性組織記錄 (預覽) 會顯示 Intune 中的裝置相容性組織報告，以及不相容裝置的詳細資料。 選擇此選項，以將相容性記錄傳送至您的儲存體帳戶、事件中樞或記錄分析。

      如果您選擇使用儲存體帳戶，則也請輸入您想要保留資料的天數 (保留期)。 若要永久保留資料，將 [保留期 (天數)]  設為 `0` (零)。
 
      > [!NOTE]
      > 裝置相容性組織記錄目前為預覽狀態。 若要提供意見反應 (包括報告中的資訊)，請移至 [UserVoice](https://microsoftintune.uservoice.com/forums/291681-ideas/suggestions/36613948-diagnostics-settings-feedback)。

    完成時，您的設定會看起來類似下列設定： 

    ![要將 Intune 稽核記錄傳送至 Azure 儲存體帳戶的範例影像](./media/review-logs-using-azure-monitor/diagnostics-settings-example.png)

4. [儲存]  變更。 您的設定會顯示於清單中。 一旦建立之後，您就能選取 [編輯設定]   > [儲存]  來變更設定。

## <a name="use-audit-logs-throughout-intune"></a>在 Intune 中使用稽核記錄

您也可在 Intune 的其他部分中匯出稽核記錄，包括註冊、相容性、設定、裝置、用戶端應用程式等。

例如，若要在使用裝置相容性時匯出稽核記錄：

1. 登入 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
2. 選取 [裝置相容性]   > [監視]   > [稽核記錄]  ：

    ![選擇稽核記錄以將 Intune 資料路由傳送至 Azure 監視器儲存體、事件中樞或分析](./media/review-logs-using-azure-monitor/audit-logs-under-monitor-in-compliance.png)

3. 選取 [匯出資料設定]  。 如果未啟用，您可以開啟 [診斷設定]  。 您也可以選擇傳送記錄的位置，如[將記錄傳送至 Azure 監視器](#send-logs-to-azure-monitor)中所述 (在本文中)。

## <a name="cost-considerations"></a>成本考量

如果您已經有 Microsoft Intune 授權，您需要 Azure 訂用帳戶來設定儲存體帳戶和事件中樞。 Azure 訂用帳戶通常是免費的。 但是，您需要付費才能使用 Azure 資源，包括用於封存的儲存體帳戶和用於串流處理的事件中樞。 資料量和成本會根據租用戶大小而有所不同。

### <a name="storage-size-for-activity-logs"></a>適用於活動記錄的儲存體大小

每個稽核記錄事件都會使用約 2 KB 的資料儲存體。 針對含有 100,000 名使用者的租用戶，您每天可能約有 150 萬個事件。 您每天可能需要約 3 GB 的資料儲存體。 由於寫入通常發生於五分鐘的批次中，因此，您可以預期每月約有 9,000 個寫入作業。

下表顯示根據租用戶大小所進行的成本估計。 它也包含位在美國西部的一般用途 v2 儲存體帳戶，可提供至少一年的資料保留期。 若要取得您針對記錄所預期的資料量估計值，請使用 [Azure 儲存體價格計算機](https://azure.microsoft.com/pricing/details/storage/blobs/)。

**含有 100,000 名使用者的稽核記錄**

| | |
|---|---|
|每天的事件| 150 萬|
|每月估計的資料量| 90 GB|
|每月估計的成本 (USD)| $1.93|
|每年估計的成本 (USD)| $23.12|

**含有 1,000 名使用者的稽核記錄**

| | |
|---|---|
|每天的事件| 15,000|
|每月估計的資料量| 900 MB|
|每月估計的成本 (USD)| $0.02|
|每年估計的成本 (USD)| $0.24|

### <a name="event-hub-messages-for-activity-logs"></a>適用於活動記錄的事件中樞訊息

通常每隔五分鐘就會對事件進行批次處理，並以單一訊息形式傳回，訊息內包含該時間範圍內的所有事件。 事件中樞的訊息大小上限為 256 KB。 如果時間範圍內所有訊息的大小總計超過該資料量，則會傳送多則訊息。

例如，針對超過 100,000 名使用者的大型租用戶，通常每秒大約會發生 18 個事件。 這相當於每五分鐘 5,400 個事件 (300 秒 x 18 個事件)。 每個事件的稽核記錄大約是 2 KB。 這相當於 10.8 MB 的資料。 因此，會在該五分鐘間隔內傳送 43 則訊息到事件中樞。

下表包含每月根據事件資料量，針對美國西部的基本事件中樞所估計的成本。 若要取得您針對記錄所預期的資料量估計值，請使用[事件中樞價格計算機](https://azure.microsoft.com/pricing/details/event-hubs/)。

**含有 100,000 名使用者的稽核記錄**

| | |
|---|---|
|每秒事件數| 18|
|每隔五分鐘的事件數| 5,400|
|每個間隔的資料量| 10.8 MB|
|每個間隔的訊息數| 43|
|每月訊息數| 371,520|
|每月估計的成本 (USD)| $10.83|

**含有 1,000 名使用者的稽核記錄**

| | |
|---|---|
|每秒事件數|0.1 |
|每隔五分鐘的事件數| 52|
|每個間隔的資料量|104 KB |
|每個間隔的訊息數|1 |
|每月訊息數|8,640 |
|每月估計的成本 (USD)|$10.80 |

### <a name="log-analytics-cost-considerations"></a>Log Analytics 成本考量

若要檢閱管理 Log Analytics 工作區的相關成本，請參閱[控制 Log Analytics 中的資料量和保留期來管理成本](https://docs.microsoft.com/azure/log-analytics/log-analytics-manage-cost-storage)。

## <a name="frequently-asked-questions"></a>常見問題集

請取得常見問題的解答，並閱讀 Azure 監視器中任何有關 Intune 記錄的已知問題。

### <a name="which-logs-are-included"></a>包含哪些記錄？

稽核記錄和作業 (預覽) 記錄均可用來使用此功能進行路由傳送。

### <a name="after-an-action-when-do-the-corresponding-logs-show-up-in-the-event-hub"></a>執行某個動作之後，對應的記錄何時會顯示於事件中樞？

記錄通常會在執行動作之後的數分鐘內顯示於事件中樞。 [什麼是 Azure 事件中樞？](https://docs.microsoft.com/azure/event-hubs/)會提供詳細的資訊。

### <a name="after-an-action-when-do-the-corresponding-logs-show-up-in-the-storage-account"></a>執行某個動作之後，對應的記錄何時會顯示於儲存體帳戶？

如果是 Azure 儲存體帳戶，動作執行之後會有 5 到 15 分鐘的延遲。

### <a name="what-happens-if-an-administrator-changes-the-retention-period-of-a-diagnostic-setting"></a>如果系統管理員變更診斷設定的保留期限，會發生什麼事？

新的保留原則會套用到變更之後所收集的記錄。 原則變更之前所收集的記錄不會受到影響。

### <a name="how-much-does-it-cost-to-store-my-data"></a>儲存我的資料需要多少費用？

儲存體成本取決於您記錄的大小與您選擇的保留期間。 如需適用於租用戶的估計成本清單 (取決於所產生的記錄磁碟區)，請參閱[適用於活動記錄的儲存體大小](#storage-size-for-activity-logs) (在本文中)。

### <a name="how-much-does-it-cost-to-stream-my-data-to-an-event-hub"></a>將我的資料串流處理到事件中樞需要多少費用？

串流處理的成本取決於您每分鐘收到的訊息數目。 如需如何根據訊息數目計算成本與估計成本的詳細資訊，請參閱[適用於活動記錄的事件中樞訊息](#event-hub-messages-for-activity-logs) (在本文中)。

### <a name="how-do-i-integrate-intune-audit-logs-with-my-siem-system"></a>如何將 Intune 稽核記錄與 SIEM 系統整合？

使用 Azure 監視器搭配事件中樞來將記錄串流處理到 SIEM 系統。 首先，[將記錄串流處理到事件中樞](https://docs.microsoft.com/azure/active-directory/reports-monitoring/tutorial-azure-monitor-stream-logs-to-event-hub)。 然後，使用已設定的事件中樞來[設定您的 SIEM 工具](https://docs.microsoft.com/azure/active-directory/reports-monitoring/tutorial-azure-monitor-stream-logs-to-event-hub#access-data-from-your-event-hub)。 

### <a name="what-siem-tools-are-currently-supported"></a>目前有哪些產品支援 SIEM 工具？

目前支援 Azure 監視器的是 [Splunk](https://docs.microsoft.com/azure/active-directory/reports-monitoring/tutorial-integrate-activity-logs-with-splunk)、QRadar 及 [Sumo Logic](https://help.sumologic.com/Send-Data/Applications-and-Other-Data-Sources/Azure_Active_Directory) \(英文\) (開啟新網站)。 如需連接器運作方式的詳細資訊，請參閱[將 Azure 監視資料串流至事件中樞以供外部工具取用](https://docs.microsoft.com/azure/azure-monitor/platform/stream-monitoring-data-event-hubs)。

### <a name="can-i-access-the-data-from-an-event-hub-without-using-an-external-siem-tool"></a>我可以在不使用外部 SIEM 工具的情況下，從事件中樞存取資料嗎？

是。 若要從自訂應用程式存取記錄，您可以使用[事件中樞 API](https://docs.microsoft.com/azure/event-hubs/event-hubs-dotnet-standard-getstarted-receive-eph)。

### <a name="what-data-is-stored"></a>系統會儲存哪些資料？

Intune 不會儲存任何透過管線傳送的資料。 Intune 會透過租用戶的授權，將資料路由傳送至 Azure 監視器管線。 如需詳細資訊，請參閱 [Azure 監視器概觀](https://docs.microsoft.com/azure/azure-monitor/overview)。

## <a name="next-steps"></a>後續步驟

* [將活動記錄封存到儲存體帳戶](https://docs.microsoft.com/azure/active-directory/reports-monitoring/quickstart-azure-monitor-route-logs-to-storage-account)
* [將活動記錄路由傳送至事件中樞](https://docs.microsoft.com/azure/active-directory/reports-monitoring/tutorial-azure-monitor-stream-logs-to-event-hub)
* [將活動記錄與 Log Analytics 整合](https://docs.microsoft.com/azure/active-directory/reports-monitoring/howto-integrate-activity-logs-with-log-analytics)

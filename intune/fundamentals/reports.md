---
title: Microsoft Intune reports
titleSuffix: Microsoft Intune
description: Intune 提供使用焦點檢視的特定報表類型，其中包含一致且即時的資料。
keywords: ''
author: erikre
ms.author: erikre
manager: dougeby
ms.date: 11/18/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.assetid: ''
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 05258c5363b43398dee1815bb91c50878803e426
ms.sourcegitcommit: 2fddb293d37453736ffa54692d03eca642f3ab58
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74391938"
---
# <a name="intune-reports"></a>Intune 報告
Microsoft Intune 報表可讓您更有效率且主動地監視組織中端點的健康情況和活動，同時也提供 Intune 中的其他報表資料。 例如，您將能夠看到關於裝置合規性、裝置健康情況和裝置趨勢的報表。 此外，您還可以建立自訂報表來取得更特定的資料。 

> [!NOTE]
> Intune 報表變更會在一段時間逐漸推出，以協助您準備和適應新結構。

報表類型組織成下列焦點區域：
- **營運** - 提供即時、已設定目標的資料，可協助您專注並採取行動。 系統管理員、主題專家和技術支援人員會覺得這些報表很有用。
- **組織** - 提供整體檢視的更廣泛摘要 (例如裝置管理狀態)。 經理和管理員會覺得這些報表很有用。
- **歷程記錄** - 提供一段時間的模式和趨勢。 經理和管理員會覺得這些報表很有用。
- **專家** - 可讓您使用未經處理資料來建立您自己的自訂報表。 管理員會覺得這些報表很有用。

報告架構提供一致且更完整的報告體驗。 可用的報表提供下列功能：
- **搜尋和排序** - 不論資料集多大，您都可以在每個資料行之間搜尋和排序。
- **資料分頁** - 您可以根據分頁來掃描資料 (逐頁瀏覽或跳到特定頁面)。
- **效能** - 您可以快速產生及檢視從大型租用戶建立的報表。
- **匯出** - 您可以快速匯出從大型租用戶產生的報告資料。

### <a name="who-can-access-the-data"></a>誰可以存取資料？

具有下列權限的使用者可以檢閱記錄：

- 全域管理員
- Intune 服務管理員
- 受指派為有**讀取**權限 Intune 角色的系統管理員

## <a name="non-compliant-devices-report-operational"></a>不符合規範裝置報表 (營運)
「不符合規範裝置」報表呈現的資料，通常是供技術支援人員或系統管理員角色用來找出問題並協助補救問題。 這些報表中的資料是即時的，會顯示非預期行為，而且是設計成可採取動作的。 該報表可隨工作負載一起取得，讓您不需瀏覽至作用中工作流程外，就能存取不符合規範裝置。 此報表提供篩選、搜尋、分頁和排序功能。 此外，您也可以向下切入以協助進行疑難排解。

您可以使用下列步驟來檢視**不合規的裝置**報表：

1. 登入 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
2. 選取 [裝置合規性]   > [不合規的裝置]  。

    ![不合規的裝置報表](./media/intune-reports/intune-reports-02.png)

## <a name="device-compliance-report-organizational"></a>裝置合規性報表 (組織)
裝置合規性報表是設計成本質上是廣泛的，且提供更傳統的資料報告檢視，以識別彙總計量。 此報表是設計成搭配大型資料集來使用，以取得完整裝置合規性情況。 例如，裝置合規性的裝置合規性報表會顯示裝置的所有合規性狀態，以提供更廣泛的資料檢視 (不論資料集多大)。 此報表顯示資料列的完整詳細資料，以及方便的彙總計量視覺效果。 您可以藉由對報表套用篩選條件，並選取 [產生報告] 按鈕來產生此報表。 這會重新整理資料，以顯示最新狀態，而且能夠檢視組成彙總資料的個別資料列。 就像新架構中的大部分報表一樣，您可以排序和搜尋這些資料列，以專注於所需的資訊。 

若要查看產生的裝置狀態報表，您可以使用下列步驟：
1. 登入 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
2. 選取 [報表]  來檢視報表摘要。
3. 選取 [裝置合規性]  。
4. 選取 [合規性狀態]  、[OS]  和 [擁有權]  篩選條件，來讓您的報表更精簡。
5. 按一下 [產生報告]  (或 [重新產生]  ) 來取得目前資料。

    ![裝置合規性報表](./media/intune-reports/intune-reports-02a.png)

    > [!NOTE]
    > 此**裝置合規性**報表會提供上次產生報表的時間戳記。 

如需詳細資訊，請參閱[在 Intune 中使用條件式存取強制執行 Microsoft Defender ATP 的合規性](~/protect/advanced-threat-protection.md)。

## <a name="reports-summary"></a>報表摘要 

裝置合規性報表是以 [報告]  工作負載中的摘要報告提供。 使用下列步驟來檢視裝置合規性報表：

1. 登入 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
2. 選取 [報表]  來檢視報表摘要。

    ![Intune 報表摘要](./media/intune-reports/intune-reports-01.png)

## <a name="device-compliance-trend-report-historical"></a>裝置合規性趨勢報表 (歷程記錄)
系統管理員和架構設計師更可能使用裝置合規性趨勢報表來識別裝置合規性的長期趨勢。 報表會顯示一段時間內的彙總資料，對於進行未來投資決策、推動程序改善，或提示調查任何異常狀況很有用。 也可以套用篩選條件來查看特定趨勢。 此報表提供的資料是目前租用戶狀態 (近乎即時) 的快照。 

裝置合規性趨勢的裝置合規性趨勢報表，可以顯示一段時間內裝置合規性狀態的趨勢。 您可以識別合規性尖峰發生的位置，並據此專注您的時間和精力。

您可以使用下列步驟來檢視**趨勢**報表：

1. 登入 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
2. 選取 [報表]   > [趨勢]  ，來檢視裝置合規性在 60 天內的趨勢。

    ![Intune 趨勢報表](./media/intune-reports/intune-reports-03.png)

## <a name="azure-monitor-integration-reports-specialist"></a>Azure 監視器整合報表 (專家)
您可以自訂自己的報表，以取得您想要的資料。 您報表中的資料可以選擇性地透過 [Azure 監視器](https://docs.microsoft.com/azure/azure-monitor/overview)使用 [Log Analytics](reports.md#log-analytics) 和 [Azure 監視器活頁簿](reports.md#workbooks)來取得。 這些解決方案可讓您建立自訂查詢、設定警示，並讓儀表板以您想要的方式顯示裝置合規性資料。 此外，您可以將活動記錄保留在您的 Azure 儲存體帳戶中，使用[安全性資訊與事件管理 (SIEM) 工具](https://docs.microsoft.com/microsoft-365/security/office-365-security/siem-server-integration)來與報表整合，並將該報表與 Azure AD 活動記錄相互關聯。 Azure 監視器活頁簿還能用於針對自訂報告需求匯入儀表板。

> [!NOTE]
> 複雜的報告功能需要 Azure 月租方案。

範例專家報表會在自訂報表中，將裝置擁有權資料與平台註冊資料相互關聯。 然後，此自訂報表可以顯示在 Azure Active Directory 入口網站中的現有儀表板上。

您可以使用下列步驟來建立和檢視自訂報表：

1. 登入 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
2. 選取 [報表]   > [診斷設定]  ，新增[診斷設定](reports.md#diagnostic-settings)。

    ![Intune 報表摘要](./media/intune-reports/intune-reports-04.png)

3. 按一下 [新增診斷設定]  以顯示 [診斷設定]  窗格。 
4. 新增診斷設定的 [名稱]  。 
5. 選取 [傳送至 Log Analytics]  和 [DeviceComplianceOrg]  。

    ![Intune 報表摘要](./media/intune-reports/intune-reports-04a.png)

6. 按一下 **[儲存]** 。
7. 接下來，選取 [Log Analytics]  來使用 [Log Analytics](reports.md#log-analytics) 建立及執行新記錄查詢。

   ![Log Analytics - 記錄查詢](./media/intune-reports/intune-reports-05.png)

8. 選取 [活頁簿]  來使用 [Azure 監視器活頁簿](reports.md#workbooks)建立或開啟互動式報表。

   ![活頁簿 - 互動式報表](./media/intune-reports/intune-reports-07.png)

### <a name="diagnostic-settings"></a>診斷設定
每個 Azure 資源都需要自己的診斷設定。 診斷設定會為資源定義下列項目：

- 傳送至設定中所定義目的地之記錄和計量資料的類別。 可用類別會隨不同資源類型而異。
- 一或多個要傳送記錄的目的地。 目前的目的地包括 Log Analytics 工作區、事件中樞和 Azure 儲存體。
- 儲存在 Azure 儲存體中資料的保留原則。

單一診斷設定可以定義每個目的地的其中一個。 如果您想要將資料傳送至超過一個的特定目的地類型 (例如，兩個不同的 Log Analytics 工作區)，請建立多個設定。 每個資源可以有最多 5 個診斷設定。

如需診斷設定的詳細資訊，請參閱[建立診斷設定以收集 Azure 中的平台記錄和計量](https://docs.microsoft.com/azure/azure-monitor/platform/diagnostic-settings) \(部分機器翻譯\)。

### <a name="log-analytics"></a>記錄分析
Log Analytics 是 Azure 入口網站中撰寫記錄查詢並以互動方式分析查詢結果的主要工具。 即使記錄查詢是用於 Azure 監視器中的其他地方，您通常還是先使用 Log Analytics 撰寫並測試查詢。 如需使用 Log Analytics 和建立記錄查詢的詳細記錄，請參閱 [Azure 監視器中記錄查詢的概觀](https://docs.microsoft.com/azure/azure-monitor/log-query/log-query-overview) \(部分機器翻譯\)。 

### <a name="workbooks"></a>活頁簿
活頁簿將文字、分析查詢、Azure 計量和參數結合成互動式報表。 有相同 Azure 資源存取權的小組成員，都可以編輯活頁簿。 如需活頁簿的詳細資訊，請參閱[使用 Azure 監視器活頁簿建立互動式報表](https://docs.microsoft.com/azure/azure-monitor/app/usage-workbooks) \(部分機器翻譯\)。 此外，您可以使用和參與活頁簿範本。 如需詳細資訊，請參閱 [Azure 監視器活頁簿範本](https://go.microsoft.com/fwlink/?linkid=867045) \(英文\)。

## <a name="next-steps"></a>後續步驟

深入了解下列技術：
- [部落格 - Microsoft Intune 報告架構](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/New-Reporting-Framework-Coming-to-Intune/ba-p/1009553) \(英文\)
- [Azure 監視器](https://docs.microsoft.com/azure/active-directory/reports-monitoring/concept-activity-logs-azure-monitor) \(部分機器翻譯\)
- [什麼是 Log Analytics？](https://docs.microsoft.com/azure/azure-monitor/log-query/log-query-overview#what-is-log-analytics) \(部分機器翻譯\)
- [記錄查詢](https://docs.microsoft.com/azure/azure-monitor/log-query/log-query-overview) \(部分機器翻譯\)
- [開始使用 Azure 監視器 Log Analytics](https://docs.microsoft.com/azure/azure-monitor/log-query/get-started-portal)
- [Azure 監視器活頁簿](https://docs.microsoft.com/azure/azure-monitor/app/usage-workbooks) \(部分機器翻譯\)
- [安全性資訊與事件管理 (SIEM) 工具](https://docs.microsoft.com/microsoft-365/security/office-365-security/siem-server-integration) \(部分機器翻譯\)

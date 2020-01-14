---
title: 在 Microsoft Intune 中檢查安全性基準的成功或失敗狀態 - Azure | Microsoft Docs
description: 在 Microsoft Intune MDM 中，將安全性基準部署至使用者和裝置時，檢查錯誤、衝突及成功狀態。 了解如何使用用戶端記錄和 Intune 中的報告功能來進行疑難排解。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: shpate
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: cbf82c0bef88e4a6d0e790f4b0ecdf73d2731d5d
ms.sourcegitcommit: 9bb1bcd9f1bdd53b470073da956bbd8b0935dfbc
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/31/2019
ms.locfileid: "75556397"
---
# <a name="monitor-security-baseline-and-profiles-in-microsoft-intune"></a>在 Microsoft Intune 中監視安全性基準和設定檔

Intune 提供數個用來監視安全性基準的選項。 您可以監視適用於您使用者和裝置的安全性基準設定檔。 您也可以監視實際的基準，以及任何符合 (或不符合) 建議值的裝置。

本文將逐步引導您進行這兩種監視選項。

[Intune 中的安全性基準](../security-baselines.md)提供有關 Microsoft Intune 安全性基準功能的更多詳細資料。

## <a name="monitor-the-baseline-and-your-devices"></a>監視基準和您的裝置

當您監視基準時，會根據 Microsoft 建議獲得您裝置安全性狀態的見解。 您可在 Intune 主控台中從安全性基準的 [概觀] 窗格內檢視這些見解。  在您第一次指派基準之後，最長需要 24 小時的時間才會顯示資料。 後續變更最長需要六個小時的時間才會出現。

若要檢視基準和裝置的監視資料，請登入 [Microsoft 端點管理員系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。 接下來，選取 [端點安全性]   > [安全性基準]  ，選取基準，然後檢視 [概觀]  窗格。

[概觀]  窗格提供兩種方法來監視狀態：

- **裝置檢視** - 基準的每一個狀態類別中有多少部裝置的摘要。
- **每個類別** - 此檢視顯示基準中的每個類別，並包含每個基準類別之每個狀態群組的裝置百分比。

每部裝置都以下列其中一個狀態表示 (用於「裝置」  檢視和「每個類別」  檢視)：

- **符合基準** - 基準中的所有設定都與所建議設定相符。
- **不符合基準** - 基準中至少有一個設定與所建議設定不符。

  > [!NOTE]
  > 當您建立或編輯基準設定檔時，對預設值或組態設定所做的任何變更，都會造成「不符合基準」狀態出現。 如需判斷已變更之設定的說明，請連絡 Microsoft 支援服務。 

- **設定錯誤** - 至少有一個設定未正確設定。 此狀態表示設定處於衝突、錯誤或擱置狀態。
- **不適用** - 至少有一個設定不適用，且未套用。

### <a name="device-view"></a>裝置檢視

[概觀] 窗格會顯示多少部裝置具有基準特定狀態的圖表式摘要；**已指派 Windows 10 裝置的安全性基準狀態**。

![檢查裝置的狀態](./media/security-baselines-monitor/overview.png)

當裝置具有基準中來自不同類別的不同狀態時，該裝置會以單一狀態表示。 代表裝置的狀態是取自下列優先順序：[設定錯誤]  、[不符合基準]  、[不適用]  、[符合基準]  。

例如，如果裝置具有分類為 [設定錯誤]  的設定，和一或多個分類為 [不符合基準]  的設定，則裝置會分類為 [設定錯誤]  。

您可以按一下圖表，以鑽研及檢視具有各種狀態的裝置清單。 您接著可以從該清單選取個別裝置，以檢視有關個別裝置的詳細資料。 例如：

- 選取 [裝置設定]  > 選取具有 [錯誤] 狀態的設定檔：

  ![檢視設定檔的狀態](./media/security-baselines-monitor/device-configuration-profile-list.png)

- 選取 [錯誤] 設定檔。 隨即會顯示該設定檔中的所有設定及其狀態。 現在，您可以捲動來尋找造成錯誤的設定：

  ![查看造成錯誤的設定](./media/security-baselines-monitor/profile-with-error-status.png)

請使用此報告功能來查看設定檔中造成問題的所有設定。 此外，也取得已部署至裝置之原則和設定檔的更多詳細資料。

> [!NOTE]
> 當屬性在基準中設定為 [未設定]  時，系統會忽略該設定，而不會強制執行任何限制。 該屬性不會顯示在任何報告功能中。

### <a name="per-category-view"></a>每個類別檢視

[概觀] 窗格會顯示基準的每個類別圖表；**依類別排序的安全性基準狀態**。  此檢視會顯示基準中的每個類別，並識別落入每個類別狀態分類的裝置百分比。

![狀態的每個類別檢視](./media/security-baselines-monitor/monitor-baseline-per-category.png)

在 100% 的裝置針對類別報告 [符合基準]  狀態之後，才會顯示該狀態。

您可以依每個資料行排序依類別檢視，方法是選取資料行頂端的上下箭號圖示。

## <a name="monitor-the-profile"></a>監視設定檔

監視設定檔可為您提供裝置部署狀態的深入解析，但不會根據基準建議提供安全性狀態的深入解析。

1. 在 Intune 中，選取 [安全性基準]  > 選取一個基準 > [已建立的設定檔]  。

2. 選取一個設定檔。 在 [概觀]  中，影像會顯示有多少裝置和使用者被指派這個設定檔：

   ![查看有多少裝置和使用者被指派安全性基準設定檔](./media/security-baselines-monitor/existing-profile-overview.png)

3. 在 [管理]   > [屬性]  底下，會顯示基準中的所有設定清單。 您也可以變更這當中任何一個設定：

   ![查看及更新安全性基準設定檔中的設定](./media/security-baselines-monitor/manage-settings.png)

4. 在 [監視]  中，您可以查看個別裝置上設定檔的部署狀態、每個使用者的狀態，以及基準中每個設定的狀態：

   ![查看安全性基準設定檔的各種不同監視選項](./media/security-baselines-monitor/monitor-status-options.png)

## <a name="troubleshoot-using-per-setting-status"></a>使用每個設定的狀態來進行疑難排解

您已部署安全性基準，但部署狀態顯示錯誤。 下列步驟提供您一些有關針對錯誤進行疑難排解的指引。

1. 在 Intune 中，選取 [安全性基準]  > 選取一個基準 > [已建立的設定檔]  。

2. 選取一個設定檔 > 在 [監視]   > [每個設定的狀態]  底下。

3. 表格會顯示所有設定，以及每個設定的狀態。 選取 [錯誤]  資料行或 [衝突]  資料行以查看造成錯誤的設定。

### <a name="mdm-diagnostic-information"></a>MDM 診斷資訊

現在，您已知道發生問題的設定。 下一步就是找出此設定造成錯誤或衝突的原因。

在 Windows 10 裝置上，有一個內建的 MDM 診斷資訊報告。 此報告會包含預設值、目前值、列出原則、顯示原則是否已部署至裝置或使用者等等。 請使用此報告來協助判斷設定造成衝突或錯誤的原因。

1. 在裝置上，移至 [設定]   > [帳戶]   > [存取公司或學校資源]  。

2. 選取帳戶 > [資訊]   > [進階診斷報告]   > [建立報告]  。

3. 選擇 [匯出]  ，然後開啟所產生的檔案。

4. 在報告中，於報告的不同區段中尋找錯誤或衝突設定。

  例如，在 [Enrolled configuration sources and target resources] \(已註冊的設定來源和目標資源\)  區段或 [Unmanaged policies] \(非受控原則\)  區段中尋找。 您可以概略了解它造成錯誤或衝突的原因。

[Windows 10 中診斷 MDM 失敗](https://docs.microsoft.com/windows/client-management/mdm/diagnose-mdm-failures-in-windows-10) \(英文\) 提供有關此內建報告的詳細資訊。

> [!TIP]
> - 有些設定也會列出 GUID。 您可以在本機登錄 (regedit) 中搜尋此 GUID 來尋找任何已設定的值。
> - [事件檢視器] 記錄檔可能也包含一些有關發生問題之設定的錯誤資訊 ([事件檢視器]   > [應用程式及服務記錄檔]   > [Microsoft]   > [Windows]   > [DeviceManagement-Enterprise-Diagnostics-Provider]   > [系統管理]  )。

## <a name="next-steps"></a>後續步驟

[監視裝置設定檔](../configuration/device-profile-monitor.md)及[查看一些常見的問題和解決方式](../configuration/device-profile-troubleshoot.md)。

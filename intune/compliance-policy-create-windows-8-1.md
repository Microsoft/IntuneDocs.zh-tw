---
title: Microsoft Intune 中的 Windows 10 教育設定 - Azure | Microsoft Docs
description: 請參閱 Microsoft Intune 中設定您的 Windows 8.1 和 Windows Phone 8.1 裝置的合規性時，您可以使用的所有設定的清單。 檢查有最小和最大作業系統上，設定密碼限制和長度的合規性上啟用加密資料儲存體和更多功能。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/04/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4ed863378616f8001beab89177c642404287e7d3
ms.sourcegitcommit: 02803863eba37ecf3d8823a7f1cd7c4f8e3bb42c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59424932"
---
# <a name="windows-81-settings-to-mark-devices-as-compliant-or-not-compliant-using-intune"></a>將裝置標記為符合規範或不符合規範使用 Intune 的 Windows 8.1 設定

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

這篇文章列出並描述您可以在 Intune 中的 Windows 8.1 裝置設定的不同的合規性設定。 您的行動裝置管理 (MDM) 解決方案的一部分，請封鎖簡單密碼，請設定 最小值與最高 OS 版本，和其他使用這些設定。

本功能適用於：

- Windows Phone 8.1
- Windows 8.1 及更新版本

身為 Intune 管理員，使用這些合規性設定來協助保護您組織的資源。 若要深入了解合規性原則，以及任何必要條件，請參閱[開始使用裝置合規性](device-compliance-get-started.md)。

## <a name="before-you-begin"></a>開始之前

[建立合規性政策](create-compliance-policy.md#create-the-policy)。 針對**平台**，選取**Windows Phone 8.1**或是**Windows 8.1 和更新版本**。

## <a name="device-properties"></a>裝置內容

- **所需的最小 OS**： 輸入允許的最低版本。 當裝置不符合最小 OS 版本需求時，會回報為不符合規範。 會顯示如何升級的資訊連結。 終端使用者可以選擇升級其裝置，然後便可存取公司資源。
- **允許的最高 OS 版本**： 輸入的最高允許版本。 當裝置使用的 OS 版本比規則中所輸入的版本還新時，系統就會封鎖對公司資源的存取。 系統會要求使用者連絡其 IT 管理員。在您變更規則以允許該 OS 版本之前，裝置無法存取組織資源。

Windows 8.1 電腦會傳回版本 **3**。 如果 Windows 的 OS 版本規則設為 Windows 8.1，則即使裝置具有 Windows 8.1，還是會回報為不相容。

## <a name="system-security"></a>系統安全性

### <a name="password"></a>密碼

- **需要密碼才可解除鎖定行動裝置**：**要求**使用者必須輸入密碼以存取其裝置。
- **簡單密碼**：設定為 [封鎖] 時，使用者將無法建立 **1234** 或 **1111** 之類的簡單密碼。 設定為 [未設定] 時，使用者可以建立 **1234** 或 **1111** 之類的密碼。
- **最小密碼長度**：輸入密碼至少須包含的位數或字元數。

  對於執行 Windows 並使用 Microsoft 帳戶存取的裝置，合規性原則在下列情況下將無法正確評估：
  - 如果最小密碼長度超過八個字元
  - 或者，如果字元集數目下限超過兩個

- **密碼類型**：選擇密碼是否應該只包含**數值**字元，或是應該混合數字和其他字元 (**英數字元**)。
  
  - **密碼中的非英數字元數目**：若將 [需要的密碼類型] 設定為 [英數字元]，則此設定可指定密碼至少須包含的最少字元集數目。 四個字元集為：
    - 小寫字母
    - 大寫字母
    - 符號
    - 數字

    若設定較高的數目，使用者就必須建立較複雜的密碼。 對於使用 Microsoft 帳戶存取的裝置，合規性政策將無法在下列情況中進行正確評估：

    - 如果最小密碼長度超過八個字元
    - 或者，如果字元集數目下限超過兩個

- **停止活動幾分鐘後需要輸入密碼**：輸入在閒置多久後，使用者必須重新輸入密碼。
- **密碼到期 (天數)**：選取密碼到期且必須建立新密碼前的天數。
- **避免重複使用前幾個密碼**：輸入不可使用先前所使用的多少個密碼。

### <a name="encryption"></a>加密

- **在行動裝置上要求加密**：**要求**裝置必須加密以連線至資料存放區資源。

選取 [確定] > [建立] 儲存您的變更。

## <a name="next-steps"></a>後續步驟

- [新增適用於不符合規範的裝置動作](actions-for-noncompliance.md)並[使用篩選器原則的範圍標籤](scope-tags.md)。
- [監視合規性政策](compliance-policy-monitor.md)。
- 請參閱[合規性原則設定適用於 Windows 10 和更新版本](compliance-policy-create-windows.md)裝置。
---
title: Microsoft Intune 中的 Windows 8.1 相容性設定 - Azure | Microsoft Docs
description: 查看您在 Microsoft Intune 中為 Windows 8.1 及 Windows Phone 8.1 裝置設定相容性時可使用的所有設定清單。 檢查最低和最高作業系統上的相容性、設定密碼限制和長度、啟用資料儲存區加密等。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/04/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 322d6f1e23464f1f75cc79346d839a9ccdbd7bc7
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72504652"
---
# <a name="windows-81-settings-to-mark-devices-as-compliant-or-not-compliant-using-intune"></a>使用 Intune，透過 Windows 8.1 設定將裝置標示為相容或不相容

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

本文列出及描述您可在 Intune 中 Windows 8.1 裝置上設定的不同相容性設定。 作為您行動裝置管理 (MDM) 解決方案的一部分，請使用這些設定來封鎖簡易密碼、設定最低或最高 OS 版本等。

本功能適用於：

- Windows Phone 8.1
- Windows 8.1 及更新版本

身為 Intune 管理員，請使用這些相容性設定來協助保護您的組織資源。 若要深入了解相容性原則及其執行的操作，請參閱[開始使用裝置相容性](device-compliance-get-started.md)。

## <a name="before-you-begin"></a>開始之前

[建立合規性政策](create-compliance-policy.md#create-the-policy)。 針對 [平台]  ，選取 [Windows Phone 8.1]  或 [Windows 8.1 及更新版本]  。

## <a name="device-properties"></a>裝置內容

- [所需的最低 OS]  ：輸入允許的最低版本。 當裝置不符合最低 OS 版本需求時，便會回報為不相容。 會顯示如何升級的資訊連結。 終端使用者可以選擇升級其裝置，然後便可存取公司資源。
- [允許的最高 OS 版本]  ：輸入允許的最高版本。 當裝置使用的 OS 版本比規則中所輸入的版本還新時，系統就會封鎖對公司資源的存取。 系統會要求使用者連絡其 IT 管理員。在您變更規則以允許該 OS 版本之前，裝置無法存取組織資源。

Windows 8.1 電腦會傳回版本 **3**。 若針對 Windows 將 OS 版本規則設為 Windows 8.1，則即使裝置具有 Windows 8.1，還是會回報為不相容。

## <a name="system-security"></a>系統安全性

### <a name="password"></a>密碼

- **需要密碼才可解除鎖定行動裝置**：**要求**使用者必須輸入密碼以存取其裝置。
- **簡單密碼**：設定為 [封鎖]  時，使用者將無法建立 **1234** 或 **1111** 之類的簡單密碼。 設定為 [未設定]  時，使用者可以建立 **1234** 或 **1111** 之類的密碼。
- **最小密碼長度**：輸入密碼至少須包含的位數或字元數。

  對於執行 Windows 並使用 Microsoft 帳戶存取的裝置，合規性原則在下列情況下將無法正確評估：
  - 如果最小密碼長度超過八個字元
  - 或者，如果字元集數目下限超過兩個

- **密碼類型**：選擇密碼是否應該只包含**數值**字元，或是應該混合數字和其他字元 (**英數字元**)。
  
  - **密碼中的非英數字元數目**：若將 [需要的密碼類型]  設定為 [英數字元]  ，則此設定可指定密碼至少須包含的最少字元集數目。 四個字元集為：
    - 小寫字母
    - 大寫字母
    - 符號
    - 數字

    若設定較高的數目，使用者就必須建立較複雜的密碼。 對於使用 Microsoft 帳戶存取的裝置，合規性政策將無法在下列情況中進行正確評估：

    - 如果最小密碼長度超過八個字元
    - 或者，如果字元集數目下限超過兩個

- **停止活動幾分鐘後需要輸入密碼**：輸入在閒置多久後，使用者必須重新輸入密碼。
- **密碼到期 (天數)** ：選取密碼到期且必須建立新密碼前的天數。
- **避免重複使用前幾個密碼**：輸入不可使用先前所使用的多少個密碼。

### <a name="encryption"></a>加密

- **在行動裝置上要求加密**：**要求**裝置必須加密以連線至資料存放區資源。

選取 [確定]   > [建立]  儲存您的變更。

## <a name="next-steps"></a>後續步驟

- [為不相容的裝置新增動作](actions-for-noncompliance.md)及[使用範圍標籤篩選原則](../fundamentals/scope-tags.md)。
- [監視您的相容性原則](compliance-policy-monitor.md)。
- 請參閱 [Windows 10 及更新版本裝置的相容性原則設定](compliance-policy-create-windows.md)。
---
title: Microsoft Intune 中的 Windows 8.1 相容性設定 - Azure | Microsoft Docs
description: 查看您在 Microsoft Intune 中為 Windows 8.1 及 Windows Phone 8.1 裝置設定相容性時可使用的所有設定清單。 檢查最低和最高作業系統上的相容性、設定密碼限制和長度、啟用資料儲存區加密等。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/22/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3e074d922078a9772ca67a6ebd99948bc3e64601
ms.sourcegitcommit: 25acfc88b366d2da71c37d354a0238e4f1168325
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2019
ms.locfileid: "72813223"
---
# <a name="windows-81-settings-to-mark-devices-as-compliant-or-not-compliant-using-intune"></a>使用 Intune，透過 Windows 8.1 設定將裝置標示為相容或不相容

本文列出及描述您可在 Intune 中 Windows 8.1 裝置上設定的不同相容性設定。 作為您行動裝置管理 (MDM) 解決方案的一部分，請使用這些設定來封鎖簡易密碼、設定最低或最高 OS 版本等。

本功能適用於：

- Windows Phone 8.1
- Windows 8.1 及更新版本

身為 Intune 管理員，請使用這些相容性設定來協助保護您的組織資源。 若要深入了解相容性原則及其執行的操作，請參閱[開始使用裝置相容性](device-compliance-get-started.md)。

## <a name="before-you-begin"></a>開始之前

[建立合規性政策](create-compliance-policy.md#create-the-policy)。 針對 [平台]  ，選取 [Windows Phone 8.1]  或 [Windows 8.1 及更新版本]  。

## <a name="device-properties"></a>裝置內容

### <a name="operating-system-version"></a>作業系統版本

[Windows Phone 8.1 和更新版本] 
- 行動**裝置的最低 OS 版本**：  
  輸入允許的最低版本。 當裝置不符合最低 OS 版本需求時，便會回報為不相容。 您會看到如何升級的資訊連結。 裝置使用者可以選擇升級其裝置，然後便可存取公司資源。

- 行動**裝置的最高 OS 版本**：  
  輸入允許的最大版本。 當裝置正在使用的 OS 版本比規則中輸入的版本更新時，便會封鎖其對組織資源的存取。 系統會要求裝置使用者連絡其 IT 管理員。 直到規則變更為允許該 OS 版本前，裝置都無法存取組織資源。

**Windows 8.1 及更新版本**
- **最小 OS 版本**：  
  輸入允許的最低版本。 當裝置不符合最低 OS 版本需求時，便會回報為不相容。 您會看到如何升級的資訊連結。 裝置使用者可以選擇升級其裝置，然後便可存取公司資源。

- **最大 OS 版本**：  
  輸入允許的最大版本。 當裝置正在使用的 OS 版本比規則中輸入的版本更新時，便會封鎖其對組織資源的存取。 系統會要求裝置使用者連絡其 IT 管理員。 直到規則變更為允許該 OS 版本前，裝置都無法存取組織資源。

Windows 8.1 電腦會傳回版本 **3**。 若針對 Windows 將 OS 版本規則設為 Windows 8.1，則即使裝置具有 Windows 8.1，還是會回報為不相容。

## <a name="system-security"></a>系統安全性

### <a name="password"></a>密碼

- **需要密碼來解除鎖定行動裝置**：  
  - [未設定]  (預設  ) - 不會評估此設定是否符合規範。
  - [需要]  - 使用者必須輸入密碼，才能存取其裝置。

- **簡單密碼**：  
  - [**未設定**] （*預設*）-使用者可以建立簡單密碼，例如**1234**或**1111**。
  - [封鎖]  - 使用者無法建立 **1234** 或 **1111** 之類的簡單密碼。  

- **密碼長度下限**：  
  輸入使用者密碼中至少必須具有的數字位數或字元數。

  對於執行 Windows 並使用 Microsoft 帳戶存取的裝置，若符合下列任一條件，相容性原則將無法正確進行評估：  
  - 最小密碼長度超過八個字元
  - 字元集數目下限超過兩個

- **密碼類型**：  
  選擇密碼是否應該只包含**數值**字元，或是應該混合數字和其他字元 (**英數字元**)。

  當設定為英*數位*元時，可以使用下列設定。  

  - **密碼中的非英數字元數目**：  
    當 [*密碼類型*] 設定為 [英**數位**元] 時，請指定密碼必須包含的字元集數目下限。 選項包括**0**到**4**組，預設值為**1**。
    
    四個字元集為：
    - 小寫字母
    - 大寫字母
    - 符號
    - 數字

    若設定較高的數目，使用者就必須建立較複雜的密碼。 對於使用 Microsoft 帳戶存取的裝置，若符合下列任一條件，相容性原則將無法正確進行評估：

    - 最小密碼長度超過八個字元
    - 字元集數目下限超過兩個

- **在停止活動最少幾分鐘後必須輸入密碼**：  
  輸入使用者必須重新輸入密碼之前的閒置時間。

- **密碼到期 (天數)** ：  
  選取密碼到期，使用者必須建立新密碼的天數。

- **避免重複使用以前用過的密碼次數**：  
  輸入不得重複使用的舊密碼數。

### <a name="encryption"></a>加密

- **裝置上的資料儲存區加密**：  
  - [未設定]  (預設  )
  - [需要]  - 使用 [需要]  可將裝置上的資料儲存區加密。


<!-- not on phone   
- **Require encryption on mobile device**: **Require** the device to be encrypted to connect to data storage resources.
--> 

## <a name="next-steps"></a>後續步驟

- [為不相容的裝置新增動作](actions-for-noncompliance.md)及[使用範圍標籤篩選原則](../fundamentals/scope-tags.md)。
- [監視您的相容性原則](compliance-policy-monitor.md)。
- 請參閱 [Windows 10 及更新版本裝置的相容性原則設定](compliance-policy-create-windows.md)。
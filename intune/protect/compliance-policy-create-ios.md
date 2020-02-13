---
title: Microsoft Intune 中的 iOS 裝置相容性設定 - Azure | Microsoft Docs
description: 查看您在 Microsoft Intune 中為 iOS 裝置設定相容性時可使用的所有設定清單。 要求電子郵件、檢查越獄或經破解的裝置、設定所允許的最低及最高作業系統、設定任何密碼限制，包括密碼長度和裝置的非使用狀態、限制應用程式等。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/07/2020
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 3cfb8222-d05b-49e3-ae6f-36ce1a16c61d
ms.reviewer: samyada
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e9bcfed67eda96bb4d79317bcc69d21a5f8197bc
ms.sourcegitcommit: 2b905913840d4133a7964fe4f54a58ea6e421e12
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 02/07/2020
ms.locfileid: "77074626"
---
# <a name="ios-settings-to-mark-devices-as-compliant-or-not-compliant-using-intune"></a>使用 Intune，透過 iOS 設定將裝置標示為相容或不相容

本文列出及描述您可在 Intune 中 iOS 裝置上設定的不同相容性設定。 作為您行動裝置管理 (MDM) 解決方案的一部分，請使用這些設定來要求電子郵件、將經破解 (越獄) 的裝置標示為不相容、設定允許的威脅等級、設定要過期的密碼等。

本功能適用於：

- iOS
- iPadOS

身為 Intune 管理員，請使用這些相容性設定來協助保護您的組織資源。 若要深入了解相容性原則及其執行的操作，請參閱[開始使用裝置相容性](device-compliance-get-started.md)。

## <a name="before-you-begin"></a>開始之前

[建立合規性政策](create-compliance-policy.md#create-the-policy)。 針對 [平台]  ，選取 [iOS/iPadOS]  。

## <a name="email"></a>電子郵件

- **需要行動裝置具有受管理的電子郵件設定檔**：  
  - [未設定]  (預設  ) - 不會評估此設定是否符合規範。
  - [需要]  - 裝置若沒有 Intune 管理的電子郵件設定檔，就會視為不符合規範。 當沒有正確地瞄準裝置時，或是使用者手動在該裝置上設定電子郵件帳戶時，裝置便無法具備受控電子郵件設定檔。

  在下列情況中，會將裝置視為不相容：  
  - 指派電子郵件設定檔的對象使用者群組，與相容性原則所瞄準的使用者群組不同。
  - 使用者已在裝置上設定電子郵件帳戶，該帳戶與部署到裝置的 Intune 電子郵件設定檔相符。 由於 Intune 無法覆寫使用者設定的設定檔，因此 Intune 無法管理它。 若要相容，終端使用者必須移除現有的電子郵件設定。 然後 Intune 可以安裝受管理的電子郵件設定檔。  

如需電子郵件設定檔的詳細資料，請參閱[使用 Intune 的電子郵件設定檔設定組織電子郵件存取權限](../configuration/email-settings-configure.md)。

## <a name="device-health"></a>裝置健全狀況

- **破解的裝置**：  
  - [未設定]  (預設  ) - 不會評估此設定是否符合規範。
  - [封鎖]  - 將已破解 (已進行越獄) 的裝置標示為不符合規範。  

- 裝置須等於或低於裝置威脅等級  (iOS 8.0 及更新版本)  ：  
  使用此設定以採用風險評定作為合規性的條件。 選擇允許的威脅等級：  
  - [未設定]  (預設  ) - 不會評估此設定是否符合規範。
  - [安全]  - 此選項最安全，意味著裝置不能有任何威脅。 若在裝置上偵測到任何等級的威脅，便會評估為不相容。
  - [低]  - 若只有低等級的威脅，會將裝置評估為符合規範。 任何較高等級的威脅會使裝置變成不符合規範的狀態。
  - [中]  - 若裝置有低等級或中等級的威脅，會將裝置評估為符合規範。 若在裝置上偵測到高等級的威脅，便會判斷為不相容。
  - [高]  - 此選項最不安全，因為它允許所有威脅等級。 如果此解決方案只用於報告用途，則此設定可能很實用。

## <a name="device-properties"></a>裝置內容

### <a name="operating-system-version"></a>作業系統版本  

- 最低 OS 版本  (iOS 8.0 及更新版本)  ：  
  當裝置不符合最低 OS 版本需求時，便會回報為不相容。 您會看到如何升級的資訊連結。 終端使用者可以選擇升級其裝置。 之後，其即可存取組織資源。

- 最高 OS 版本  (iOS 8.0 及更新版本)  ：  
  當裝置使用的 OS 版本比規則中的版本更新時，便會封鎖其對組織資源的存取。 系統會要求終端使用者連絡其 IT 管理員。 直到規則變更為允許該 OS 版本前，裝置都無法存取組織資源。

- 最低 OS 組建版本  (iOS 8.0 及更新版本)  ：  
  當 Apple 發佈安全性更新時，通常是更新組建編號，而不是 OS 版本。 使用此功能來輸入在裝置上允許的最低組建編號。

- 最高 OS 組建版本  (iOS 8.0 及更新版本)  ：  
  當 Apple 發佈安全性更新時，通常是更新組建編號，而不是 OS 版本。 使用此功能來輸入在裝置上允許的最高組建編號。

## <a name="system-security"></a>系統安全性

### <a name="password"></a>密碼

> [!NOTE]
> 將相容性或設定原則套用至 iOS 裝置之後，系統每 15 分鐘會提示使用者設定密碼。 在設定密碼之前，使用者會一直收到系統提示。 設定好 iOS 裝置的密碼時，加密程式會自動啟動。 裝置會保持加密，直到停用密碼為止。

- **需要密碼來解除鎖定行動裝置**：  
  - [未設定]  (預設  ) - 不會評估此設定是否符合規範。  
  - [需要]  - 使用者必須輸入密碼，才能存取其裝置。 使用密碼的 iOS 裝置會予以加密。

- **簡單密碼**：  
  - [未設定]  (預設)  - 使用者可以建立簡單密碼，例如 **1234** 或 **1111**。
  - [封鎖]  - 使用者無法建立 **1234** 或 **1111** 之類的簡單密碼。 

- **密碼長度下限**：  
  輸入使用者密碼中至少必須具有的數字位數或字元數。  

- **必要的密碼類型**：  
  選擇密碼是否應該只包含**數值**字元，或是應該混合數字和其他字元 (**英數字元**)。

- **密碼中的非英數字元數目**：  
  輸入密碼中必須包含的最少特殊字元 (`&`、`#`、`%`、`!` 等等) 數目。 

  若設定較高的數目，使用者就必須建立較複雜的密碼。

- 螢幕鎖定後到輸入密碼前的最長分鐘數  (iOS 8.0 和更新版本)  ：  
  指定在螢幕鎖定之後多久，使用者必須輸入密碼以存取裝置。 選項包括預設的 [未設定]  、[立即]  和從 [1 分鐘]  到 [4 小時]  。

- **停止活動最多幾分鐘後鎖定螢幕**：  
  輸入裝置在鎖定螢幕之前的閒置時間。 選項包括預設的 [未設定]  、[立即]  和從 [1 分鐘]  到 [15 分鐘]  。

- **密碼到期 (天數)** ：  
  選取密碼到期，必須建立新密碼的天數。 

- 避免重複使用以前用過的密碼次數  (iOS 8.0 及更新版本)  ：   
  輸入不得重複使用的舊密碼數。

### <a name="device-security"></a>裝置安全性

- [受限應用程式]  ：  
  您可以透過將應用程式的套件組合識別碼新增至原則，來限制應用程式。 若裝置安裝了應用程式，則將裝置標示為不相容。

  - [應用程式名稱]  - 輸入使用者易記的名稱來協助您識別套件組合識別碼。
  - [應用程式套件組合識別碼]  - 輸入應用程式提供者指派的唯一套件組合識別碼。 若要尋找套件組合識別碼，請參閱 [How to find the bundle ID for an iOS app](https://support.microsoft.com/help/4294074/how-to-find-the-bundle-id-for-an-ios-app) (如何尋找 iOS 應用程式的套件組合識別碼) (開啟另一個 Microsoft 網站)。  

## <a name="next-steps"></a>後續步驟

- [為不相容的裝置新增動作](actions-for-noncompliance.md)及[使用範圍標籤篩選原則](../fundamentals/scope-tags.md)。
- [監視您的相容性原則](compliance-policy-monitor.md)。
- 請參閱 [macOS 裝置的相容性原則設定](compliance-policy-create-mac-os.md)。

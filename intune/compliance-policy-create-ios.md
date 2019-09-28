---
title: Microsoft Intune 中的 iOS 裝置相容性設定 - Azure | Microsoft Docs
description: 查看您在 Microsoft Intune 中為 iOS 裝置設定相容性時可使用的所有設定清單。 要求電子郵件、檢查越獄或經破解的裝置、設定所允許的最低及最高作業系統、設定任何密碼限制，包括密碼長度和裝置的非使用狀態、限制應用程式等。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/04/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 3cfb8222-d05b-49e3-ae6f-36ce1a16c61d
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: bde1c296abb99e8c0c81b44908e78b204c62388e
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 05/23/2019
ms.locfileid: "71304136"
---
# <a name="ios-settings-to-mark-devices-as-compliant-or-not-compliant-using-intune"></a>使用 Intune，透過 iOS 設定將裝置標示為相容或不相容

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

本文列出及描述您可在 Intune 中 iOS 裝置上設定的不同相容性設定。 作為您行動裝置管理 (MDM) 解決方案的一部分，請使用這些設定來要求電子郵件、將經破解 (越獄) 的裝置標示為不相容、設定允許的威脅等級、設定要過期的密碼等。

本功能適用於：

- iOS

身為 Intune 管理員，請使用這些相容性設定來協助保護您的組織資源。 若要深入了解相容性原則及其執行的操作，請參閱[開始使用裝置相容性](device-compliance-get-started.md)。

## <a name="before-you-begin"></a>開始之前

[建立合規性政策](create-compliance-policy.md#create-the-policy)。 針對 [平台]  ，選取 [iOS]  。

## <a name="email"></a>電子郵件

- [要求行動裝置擁有受控電子郵件設定檔]  ：當設為 [要求]  時，不具備由 Intune 管理電子郵件設定檔的裝置便會視為不相容。 當沒有正確地瞄準裝置時，或是使用者手動在該裝置上設定電子郵件帳戶時，裝置便無法具備受控電子郵件設定檔。 當您選擇 [未設定]   (預設值) 時，則不會評估此設定是否符合規範。

  在下列情況中，會將裝置視為不相容：

  - 指派電子郵件設定檔的對象使用者群組，與相容性原則所瞄準的使用者群組不同。
  - 使用者已在裝置上設定電子郵件帳戶，該帳戶與部署到裝置的 Intune 電子郵件設定檔相符。 由於 Intune 無法覆寫使用者設定的設定檔，因此 Intune 無法管理它。 若要相容，終端使用者必須移除現有的電子郵件設定。 然後 Intune 可以安裝受管理的電子郵件設定檔。

- [選取的電子郵件設定檔必須由 Intune 管理]  ：若選取 [電子郵件帳戶必須由 Intune 管理]  設定，請選擇 [選取]  來輸入 Intune 電子郵件設定檔。 電子郵件設定檔必須位於裝置上。

如需電子郵件設定檔的詳細資料，請參閱[使用 Intune 的電子郵件設定檔設定組織電子郵件存取權限](email-settings-configure.md)。

## <a name="device-health"></a>Device health

- [越獄裝置]  ：選擇 [封鎖]  以將經破解 (越獄) 的裝置標示為不相容。 當您選擇 [未設定]   (預設值) 時，則不會評估此設定是否符合規範。
- [要求裝置位於或低於裝置威脅等級]  (iOS 8.0 及更新版本)：使用此設定，將風險評定作為相容性的條件之一。 當您選擇 [未設定]   (預設值) 時，則不會評估此設定是否符合規範。 若要使用此設定，請選擇允許的威脅等級：
  - **安全**：此選項最安全，意味著裝置不能有任何威脅。 若在裝置上偵測到任何等級的威脅，便會評估為不相容。
  - **低**︰如果只有低等級的威脅，則會將裝置評估為相容。 任何更高等級的威脅都會使裝置處於不相容狀態。
  - **中**︰如果裝置有低等級或中等級的威脅，則會將裝置評估為相容。 若在裝置上偵測到高等級的威脅，便會判斷為不相容。
  - **高**：此選項最不安全，因為它允許所有威脅層級。 如果此解決方案只用於報告用途，則此設定可能很實用。

## <a name="device-properties"></a>裝置內容

- [所需的最低 OS]  (iOS 8.0 及更新版本)：當裝置不符合最低的 OS 版本需求時，便會回報為不相容。 您會看到如何升級的資訊連結。 終端使用者可以選擇升級其裝置。 之後，其即可存取組織資源。
- [允許的最高 OS 版本]  (iOS 8.0 及更新版本)：當裝置所使用 OS 版本比規則中的版本更新時，便會封鎖其對組織資源的存取。 系統會要求終端使用者連絡其 IT 管理員。 直到規則變更為允許該 OS 版本前，裝置都無法存取組織資源。
- [最低 OS 組建版本]  (iOS 8.0 及更新版本)：當 Apple 發佈安全性更新時，通常會更新組建編號，而非 OS 版本。 使用此功能來輸入在裝置上允許的最低組建編號。
- [最高 OS 組建版本]  (iOS 8.0 及更新版本)：當 Apple 發佈安全性更新時，通常會更新組建編號，而非 OS 版本。 使用此功能來輸入在裝置上允許的最高組建編號。

## <a name="system-security"></a>系統安全性

### <a name="password"></a>密碼

> [!NOTE]
> 將相容性或設定原則套用至 iOS 裝置之後，系統每 15 分鐘會提示使用者設定密碼。 在設定密碼之前，使用者會一直收到系統提示。

- **需要密碼才可解除鎖定行動裝置**：**要求**使用者必須輸入密碼以存取其裝置。 使用密碼的 iOS 裝置會予以加密。
- **簡單密碼**：設定為 [封鎖]  時，使用者將無法建立 **1234** 或 **1111** 之類的簡單密碼。 設定為 [未設定]  時，使用者可以建立 **1234** 或 **1111** 之類的密碼。
- **最小密碼長度**：輸入密碼至少須包含的位數或字元數。
- **所需的密碼類型**：選擇密碼是否應該只有**數值**字元，或是否應該混合數字和其他字元 (**英數字元**)。
- [密碼中的非英數字元數]  ：輸入特殊字元的數量下限，例如 `&`、`#`、`%`、`!` 等，其要求密碼中必須包含這些字元。

    若設定較高的數目，使用者就必須建立較複雜的密碼。

- **停止活動幾分鐘後需要輸入密碼**：輸入在閒置多久後，使用者必須重新輸入密碼。
- **密碼到期 (天數)** ：選取密碼到期且必須建立新密碼前的天數。
- **避免重複使用前幾個密碼**：輸入不可使用先前所使用的多少個密碼。

### <a name="device-security"></a>裝置安全性

- **受限應用程式**：您可以將應用程式的套件組合識別碼新增至原則，來限制應用程式。 若裝置安裝了應用程式，則將裝置標示為不相容。

  - **應用程式名稱**：輸入使用者易記的名稱來協助您識別套件組合識別碼。
  - **應用程式套件組合識別碼**：輸入應用程式提供者指派的唯一套件組合識別碼。 若要尋找套件組合識別碼，請參閱 [How to find the bundle ID for an iOS app](https://support.microsoft.com/help/4294074/how-to-find-the-bundle-id-for-an-ios-app) (如何尋找 iOS 應用程式的套件組合識別碼) (開啟另一個 Microsoft 網站)。  

選取 [確定]   > [建立]  儲存您的變更。

## <a name="next-steps"></a>後續步驟

- [為不相容的裝置新增動作](actions-for-noncompliance.md)及[使用範圍標籤篩選原則](scope-tags.md)。
- [監視您的相容性原則](compliance-policy-monitor.md)。
- 請參閱 [macOS 裝置的相容性原則設定](compliance-policy-create-mac-os.md)。

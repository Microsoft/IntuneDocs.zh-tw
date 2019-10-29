---
title: Microsoft Intune 中的 macOS 裝置相容性設定 - Azure | Microsoft Docs
description: 查看您在 Microsoft Intune 中為 macOS 裝置設定相容性時可使用的所有設定清單。 要求 Apple 的系統完整保護、設定密碼限制、要求防火牆、允許門禁等。
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
ms.reviewer: samyada
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 518f0b825b71a9773ed66dd480b329e998f919c4
ms.sourcegitcommit: 25acfc88b366d2da71c37d354a0238e4f1168325
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2019
ms.locfileid: "72813512"
---
# <a name="macos-settings-to-mark-devices-as-compliant-or-not-compliant-using-intune"></a>使用 Intune，透過 macOS 設定將裝置標示為相容或不相容

本文列出及描述您可在 Intune 中 macOS 裝置上設定的不同相容性設定。 作為您行動裝置管理 (MDM) 解決方案的一部分，請使用這些設定來設定最低或最高 OS 版本、設定要過期的密碼等。

本功能適用於：

- macOS

身為 Intune 管理員，請使用這些相容性設定來協助保護您的組織資源。 若要深入了解相容性原則及其執行的操作，請參閱[開始使用裝置相容性](device-compliance-get-started.md)。

## <a name="before-you-begin"></a>開始之前

[建立合規性政策](create-compliance-policy.md#create-the-policy)。 針對 [平台]  ，選取 [macOS]  。

## <a name="device-health"></a>裝置健全狀況

- **需要系統完整性保護**：  
  - [未設定]  (預設  ) - 不會評估此設定是否符合規範。
  - [**需要**]-[要求 macOS 裝置必須啟用[系統完整性保護](https://support.apple.com/HT204899)（開啟 Apple 的網站）]。  

## <a name="device-properties"></a>裝置內容

- **最低 OS 需求**：  
  當裝置不符合最低 OS 版本需求時，便會回報為不相容。 您會看到如何升級的資訊連結。 裝置使用者可以選擇升級其裝置。 之後，其即可存取組織資源。

- **允許的最高作業系統版本**：  
  當裝置使用的 OS 版本比規則中的版本更新時，便會封鎖其對組織資源的存取。 系統會要求裝置使用者連絡其 IT 管理員。 直到規則變更為允許該 OS 版本前，裝置都無法存取組織資源。

- **最低 OS 組建版本**：  
  當 Apple 發佈安全性更新時，通常是更新組建編號，而不是 OS 版本。 使用此功能來輸入在裝置上允許的最低組建編號。

- **最高 OS 組建版本**：  
  當 Apple 發佈安全性更新時，通常是更新組建編號，而不是 OS 版本。 使用此功能來輸入在裝置上允許的最高組建編號。

## <a name="system-security-settings"></a>系統安全性設定

### <a name="password"></a>密碼

- **需要密碼來解除鎖定行動裝置**：  
  - [未設定]  (預設  )
  - [需要]  - 使用者必須輸入密碼，才能存取其裝置。

- **簡單密碼**：  
  - [**未設定**] （*預設*）-使用者可以建立簡單的密碼，例如**1234**或**1111**。
  - [封鎖]  - 使用者無法建立 **1234** 或 **1111** 之類的簡單密碼。

- **密碼長度下限**：  
  輸入使用者密碼中至少必須具有的數字位數或字元數。

- **密碼類型**：選擇密碼是否應該只包含**數值**字元，或是應該混合數字和其他字元 (**英數字元**)。

- **密碼中的非英數字元數目**：  
  輸入密碼中必須包含的最少特殊字元 (`&`、`#`、`%`、`!` 等等) 數目。

  若設定較高的數目，使用者就必須建立較複雜的密碼。

- **在停止活動最少幾分鐘後必須輸入密碼**：  
  輸入使用者必須重新輸入密碼之前的閒置時間。

- **密碼到期 (天數)** ：  
  選取密碼到期，必須建立新密碼的天數。

- **避免重複使用以前用過的密碼次數**：  
  輸入不得重複使用的舊密碼數。
> [!IMPORTANT]
> 如果 macOS 裝置上的密碼需求有變更，會在使用者下次變更其密碼時才生效。 例如，如果您將密碼長度限制設定為八位數，而 macOS 裝置目前有六位數密碼，那麼在下次使用者更新裝置上的密碼之前，該裝置仍符合規範。

### <a name="encryption"></a>加密

- **裝置上的資料儲存區加密**：  
  - [未設定]  (預設  )
  - [需要]  - 使用 [需要]  可將裝置上的資料儲存區加密。

### <a name="device-security"></a>裝置安全性

防火牆會保護裝置免於遭受未經授權的網路存取。 您可以使用防火牆來控制以每個應用程式為基礎的連線。 

- **防火牆**：  
  - [未設定]  (預設  ) - 此設定會保持關閉防火牆，而且允許網路流量 (不封鎖)。
  - [啟用]  - 使用 [啟用]  以協助保護裝置免於未經授權的存取。 啟用此功能可讓您處理連入網際網路連線，並使用隱形模式。 

- **連入連線**：  
  - [未設定]  (預設  ) - 允許連入連線和共用服務。
  - [封鎖]  - 除了基本網際網路服務 (例如 DHCP、Bonjour 和 IPSec) 所需要的連線外，封鎖所有連入網路連線。 此設定也會封鎖所有共用服務，包括螢幕共用、遠端存取、iTunes 音樂共用等。  

- **隱形模式**：  
  - [**未設定**] （*預設*）-此設定會關閉 [隱形模式]。
  - [啟用]  - 關閉隱形模式來防止裝置回應探查要求，因為這些要求可能是由惡意使用者所發出。 啟用時，裝置會繼續回應已授權應用程式的連入要求。  

### <a name="gatekeeper"></a>閘道管理員

如需詳細資訊，請參閱 [macOS 上的門禁](https://support.apple.com/HT202491) (開啟 Apple 網站)。

**允許從這些位置下載的應用程式**：允許從不同的位置將所支援應用程式安裝到您的裝置。 您的位置選項：

- [**未設定**] （*預設*）-[閘道管理員] 選項不會影響相容性或不符合規範。  
- [Mac App Store]  - 僅安裝 Mac App Store 的應用程式。 無法安裝來自協力廠商或已識別開發人員的應用程式。 如果使用者選取閘道管理員來安裝 Mac App Store 以外的應用程式，裝置即視為不符合規範。
- [Mac App Store 和已識別的開發人員]  - 安裝 Mac App Store 及來自已識別開發人員的應用程式。 macOS 會檢查開發人員的身分識別，並執行一些其他檢查來驗證應用程式完整性。 如果使用者選取閘道管理員來安裝這些選項以外的應用程式，裝置即視為不符合規範。
- [任何位置]  - 應用程式可以從任何位置並由任何開發人員安裝。 此選項最不安全。
 

## <a name="next-steps"></a>後續步驟

- [為不相容的裝置新增動作](actions-for-noncompliance.md)及[使用範圍標籤篩選原則](../fundamentals/scope-tags.md)。
- [監視您的相容性原則](compliance-policy-monitor.md)。
- 請參閱 [iOS 裝置的相容性原則設定](compliance-policy-create-ios.md)。
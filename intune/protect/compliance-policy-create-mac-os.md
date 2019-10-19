---
title: Microsoft Intune 中的 macOS 裝置相容性設定 - Azure | Microsoft Docs
description: 查看您在 Microsoft Intune 中為 macOS 裝置設定相容性時可使用的所有設定清單。 要求 Apple 的系統完整保護、設定密碼限制、要求防火牆、允許門禁等。
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
ms.reviewer: muhosabe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: cada774003f73f487f87ed8051115dfcaaae6a20
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72502482"
---
# <a name="macos-settings-to-mark-devices-as-compliant-or-not-compliant-using-intune"></a>使用 Intune，透過 macOS 設定將裝置標示為相容或不相容

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

本文列出及描述您可在 Intune 中 macOS 裝置上設定的不同相容性設定。 作為您行動裝置管理 (MDM) 解決方案的一部分，請使用這些設定來設定最低或最高 OS 版本、設定要過期的密碼等。

本功能適用於：

- macOS

身為 Intune 管理員，請使用這些相容性設定來協助保護您的組織資源。 若要深入了解相容性原則及其執行的操作，請參閱[開始使用裝置相容性](device-compliance-get-started.md)。

## <a name="before-you-begin"></a>開始之前

[建立合規性政策](create-compliance-policy.md#create-the-policy)。 針對 [平台]  ，選取 [macOS]  。

## <a name="device-health"></a>裝置健全狀況

- [要求系統完整保護]  ：[要求]  您的 macOS 裝置啟用[系統完整保護](https://support.apple.com/HT204899) (開啟 Apple 的網站)。 當設為 [未設定]  (預設) 時，便不會針對相容性或非相容性評估此設定。

## <a name="device-properties"></a>裝置內容

- **最低作業系統版本**︰當裝置不符合最低作業系統版本需求時，它會回報為不符合規範。 並顯示如何升級的資訊連結。 終端使用者可以選擇升級其裝置，然後便可存取公司資源。
- **最高作業系統版本**：當裝置使用的作業系統版本高於規則指定的版本時，會封鎖對公司資源的存取。 系統會要求使用者連絡其 IT 管理員。在規則變更為允許該作業系統版本之前，此裝置將無法存取公司資源。
- **最低 OS 組建版本**：當 Apple 發佈安全性更新時，通常是更新組建編號，而不是 OS 版本。 使用此功能來輸入在裝置上允許的最低組建編號。
- **最高 OS 組建版本**：當 Apple 發佈安全性更新時，通常是更新組建編號，而不是 OS 版本。 使用此功能來輸入在裝置上允許的最高組建編號。

## <a name="system-security-settings"></a>系統安全性設定

### <a name="password"></a>密碼

- **需要密碼才可解除鎖定行動裝置**：**要求**使用者必須輸入密碼以存取其裝置。
- **簡單密碼**：設定為 [封鎖]  時，使用者將無法建立 **1234** 或 **1111** 之類的簡單密碼。 設定為 [未設定]  時，使用者可以建立 **1234** 或 **1111** 之類的密碼。
- **最小密碼長度**：輸入密碼至少須包含的位數或字元數。
- **密碼類型**：選擇密碼是否應該只包含**數值**字元，或是應該混合數字和其他字元 (**英數字元**)。
- [密碼中的非英數字元數]  ：輸入特殊字元的數量下限，例如 `&`、`#`、`%`、`!` 等，其要求密碼中必須包含這些字元。

    若設定較高的數目，使用者就必須建立較複雜的密碼。

- **停止活動幾分鐘後需要輸入密碼**：輸入在閒置多久後，使用者必須重新輸入密碼。
- **密碼到期 (天數)** ：選取密碼到期且必須建立新密碼前的天數。
- **避免重複使用前幾個密碼**：輸入不可使用先前所使用的多少個密碼。

    > [!IMPORTANT]
    > 如果 macOS 裝置上的密碼需求有變更，會在使用者下次變更其密碼時才生效。 例如，如果您將密碼長度限制設定為八位數，而 macOS 裝置目前有六位數密碼，那麼在下次使用者更新裝置上的密碼之前，該裝置仍符合規範。

### <a name="encryption"></a>加密

- **對裝置上的資料存放區加密**：選擇 [需要]  來將裝置上的資料存放區加密。

### <a name="device-security"></a>裝置安全性

防火牆會保護裝置免於遭受未經授權的網路存取。 您可以使用防火牆來控制以每個應用程式為基礎的連線。 

- [防火牆]  ：選取 [啟用]  以協助保護裝置不受未經授權的存取。 啟用此功能可讓您處理連入網際網路連線，並使用隱形模式。 [未設定]  (預設值) 會保持關閉防火牆，而且允許網路流量 (不封鎖)。
- [傳入連線]  ：除了基本網際網路服務 (例如 DHCP、Bonjour 和 IPSec) 所需要的連線外，[封鎖]  所有傳入網路連線。 此設定也會封鎖所有共用服務，包括螢幕共用、遠端存取、iTunes 音樂共用等。 [未設定]  (預設值) 允許連入連線和共用服務。
- [隱形模式]  ：[啟用]  隱形模式來防止裝置回應探查要求，因為這些要求可能是由惡意使用者所發出。 啟用時，裝置會繼續回應已授權應用程式的連入要求。 [未設定]  (預設值) 會保持關閉隱形模式。

### <a name="gatekeeper"></a>閘道管理員

如需詳細資訊，請參閱 [macOS 上的門禁](https://support.apple.com/HT202491) (開啟 Apple 網站)。

**允許從這些位置下載的應用程式**：允許從不同的位置將所支援應用程式安裝到您的裝置。 您的位置選項：

- **未設定**：預設值。 閘道管理員選項對是否符合規範沒有任何影響。 
- **Mac App Store**：僅安裝 Mac App Store 的應用程式。 無法安裝來自協力廠商或已識別開發人員的應用程式。 如果使用者選取閘道管理員來安裝 Mac App Store 以外的應用程式，裝置即視為不符合規範。
- **Mac App Store 和已識別的開發人員**：安裝 Mac App Store 及來自已識別開發人員的應用程式。 macOS 會檢查開發人員的身分識別，並執行一些其他檢查來驗證應用程式完整性。 如果使用者選取閘道管理員來安裝這些選項以外的應用程式，裝置即視為不符合規範。
- **任何位置**：應用程式可以從任何位置並由任何開發人員安裝。 此選項最不安全。

選取 [確定]   > [建立]  儲存您的變更。

## <a name="next-steps"></a>後續步驟

- [為不相容的裝置新增動作](actions-for-noncompliance.md)及[使用範圍標籤篩選原則](../fundamentals/scope-tags.md)。
- [監視您的相容性原則](compliance-policy-monitor.md)。
- 請參閱 [iOS 裝置的相容性原則設定](compliance-policy-create-ios.md)。
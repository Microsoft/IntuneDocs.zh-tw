---
title: 適用于 Microsoft Edge 的 Intune 安全性基準設定
titleSuffix: Microsoft Intune
description: Intune 支援的安全性基準設定，用於管理 Microsoft Edge 瀏覽器
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/30/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: shpate
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8f4e56340d871ea5e0bcec7e541a418c32d021d0
ms.sourcegitcommit: 60f0ff6d2efbae0f2ce14b9a9f3f9267309e209b
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73415642"
---
# <a name="microsoft-edge-baseline-settings-for-intune"></a>Intune 的 Microsoft Edge 基準設定

查看 Microsoft Intune 支援的 Microsoft Edge web 瀏覽器基準設定。 Microsoft Edge 基準預設值代表 Microsoft Edge 瀏覽器的建議設定，而且可能不符合其他安全性基準的基準預設值。

> [!NOTE]
> Microsoft Edge 基準處於公開預覽狀態。 

## <a name="microsoft-edge"></a>Microsoft Edge

- **避免略過網站的 Microsoft Defender SmartScreen 提示**  
  **預設**：啟用  
  Microsoft Edge CSP：[瀏覽器/PreventSmartScreenPromptOverride](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-preventsmartscreenpromptoverride)

  此原則設定可讓您決定使用者是否可以覆寫 Microsoft Defender SmartScreen 有關潛在惡意網站的警告。 
  - 如果您啟用此設定，使用者將無法忽略 Microsoft Defender SmartScreen 警告，且會阻止他們繼續前往網站。 
  - 如果您停用或未設定此設定，使用者可以忽略 Microsoft Defender SmartScreen 警告並繼續前往網站。

- **已啟用最低 SSL 版本**  
  **預設**：啟用  

  設定 SSL 的最低支援版本。 如果您將此原則設為 [*未*設定]，Microsoft Edge 會使用預設的最低*TLS 1.0*版本。 當設定為 [*已啟用*] 時，您可以從下列值選取最低版本：

  - TLS 1.0
  - TLS 1.1
  - TLS 1.2

  - **已啟用最低 SSL 版本**  
    **預設值**： TLS 1。2

- **避免略過有關下載的 Microsoft Defender SmartScreen 警告**  
  **預設**：啟用  
  Microsoft Edge CSP：[瀏覽器/PreventSmartScreenPromptOverrideForFiles](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-preventsmartscreenpromptoverrideforfiles)  

  此原則可讓您判斷使用者是否可以覆寫有關未經驗證下載的 Microsoft Defender SmartScreen 警告。
  - 如果您啟用此原則，您組織中的使用者將無法忽略 Microsoft Defender SmartScreen 警告，且無法完成未經驗證的下載。
  - 如果您停用或未設定此原則，使用者可以忽略 Microsoft Defender SmartScreen 警告並完成未驗證的下載。

- **允許使用者從 SSL 警告頁面進行**  
  **預設**：停用  
  Microsoft Edge CSP：[瀏覽器/PreventCertErrorOverrides](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-preventcerterroroverrides)  

  當使用者流覽具有 SSL 錯誤的網站時，Microsoft Edge 會顯示警告頁面。 如果您將此原則設為 [*啟用*] 或 [*未*設定]，使用者可以按一下這些警告頁面。 *停用*此原則時，使用者會遭到封鎖而無法按一下任何警告頁面。 

- **預設的 Adobe Flash 設定**  
  **預設**：啟用  
  Microsoft Edge CSP：[瀏覽器/AllowFlash](https://docs.microsoft.coms/windows/client-management/mdm/policy-csp-browser#browser-allowflash)和[瀏覽器/AllowFlashClickToRun](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-allowflashclicktorun)  

  判斷「PluginsAllowedForUrls」或「PluginsBlockedForUrls」未涵蓋的網站是否可以自動執行 Adobe Flash 外掛程式。 

  - 選取 [BlockPlugins] 以封鎖所有網站上的 Adobe Flash
  - 選取 [ClickToPlay] 以讓 Adobe Flash 執行，但要求使用者按一下預留位置加以啟動。
  
   在任何情況下，' PluginsAllowedForUrls ' 和 ' PluginsBlockedForUrls ' 原則的優先順序會高於 ' DefaultPluginsSetting '。 只有在 ' PluginsAllowedForUrls ' 原則中明確列出的網域才允許自動播放。 
   如果您想要啟用所有網站的自動播放，請考慮將 HTTP://* 和 HTTPs://* 新增至此清單。 
   
   - 如果您將此原則設為 [*未*設定]，使用者可以手動變更此設定。 * 2 = 封鎖 Adobe Flash 外掛程式 * 3 = 按一下以播放先前的 ' 1 ' 選項群組 [允許-全部]，但這項功能現在只能由 ' PluginsAllowedForUrls ' 原則處理。 使用 ' 1 ' 的現有原則將會以隨用隨入模式運作。  
 
  - **預設的 Adobe Flash 設定**  
    **預設值**：封鎖 Adobe Flash 外掛程式

- **為每個網站啟用網站隔離**  
  **預設**：啟用  

  ' SitePerProcess ' 原則可用來防止使用者選擇不使用隔離所有網站的預設行為。 您也可以使用 IsolateOrigins 原則來隔離額外、更精細的來源。

  - 當此原則設定為 [*啟用*] 時，使用者將無法退出宣告每個網站在自己的進程中執行的預設行為。 
  - 如果您使用 [*已停*用] 或 [*未設定*]，使用者可以退出宣告網站隔離。 （例如，在 edge://flags 中使用「停用網站隔離」專案）。停用原則或未設定原則，並不會關閉網站隔離。

- **支援的驗證配置**  
  **預設**：啟用  

  指定支援的 HTTP 驗證配置。 您可以使用下列值來設定原則：「基本」、「摘要」、「ntlm」和「negotiate」。 以逗號分隔多個值。 如果您未設定此原則，則會使用所有四種配置。
 
  - **支援的驗證配置**  
    從下列選項選取： 
    - 基本
    - 摘要
    - NTLM *(預設已選取)*
    - Negotiate *（預設為選取）*

- **啟用將密碼儲存至密碼管理員**  
  **預設**：停用  
  Microsoft Edge CSP：[瀏覽器/AllowPasswordManager](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-allowpasswordmanager)  

  啟用 Microsoft Edge 以儲存使用者密碼。 
  - 如果您啟用此原則，使用者可以將其密碼儲存在 Microsoft Edge 中。 下一次造訪網站時，Microsoft Edge 會自動輸入密碼。 
  - 如果您停用此原則，使用者將無法儲存新密碼，但仍然可以使用先前儲存的密碼。 
  
  當您將此原則設定為 [*啟用*] 或 [*已停用*] 時，使用者將無法在 Microsoft Edge 中變更或覆寫此原則。 
  
  如果您將此設為 [*未*設定]，使用者可以儲存密碼，以及關閉這項功能。

- **控制無法安裝的擴充功能**  
  **預設**：啟用  

  列出使用者無法在 Microsoft Edge 中安裝的特定延伸模組。 當您部署此原則時，會停用此清單上先前安裝的任何延伸模組，而且使用者將無法啟用它們。 如果您從封鎖的延伸模組清單中移除某個專案，該延伸模組會在其先前安裝的任何位置自動重新啟用。
  
  使用 **\*** 來封鎖未明確列在允許清單中的所有延伸模組。 如果此原則設為 [*未*設定]，使用者可以在 Microsoft Edge 中安裝任何延伸模組。 
  
  範例值： extension_id1 extension_id2。  
  <br>
  - **使用者應該防止安裝的延伸模組識別碼（或 * 全部）**  
    選取 [**新增**]，並指定其他延伸模組。 **\*** 預設已選取。

- **設定 Microsoft Defender SmartScreen**  
  **預設**：啟用  
  Microsoft Edge CSP：[瀏覽器/AllowSmartScreen](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-allowsmartscreen)  
  
  此原則設定可讓您設定是否要開啟 Microsoft Defender SmartScreen。 Microsoft Defender SmartScreen 提供警告訊息，協助保護您的使用者免于遭受潛在的網路釣魚詐騙和惡意軟體攻擊。 
  
  - 根據預設，Microsoft Defender SmartScreen 已開啟。 如果您啟用此設定，則會開啟 Microsoft Defender SmartScreen，而且使用者無法將其關閉。
  - 如果您停用此設定，則會關閉 Microsoft Defender SmartScreen，而且使用者無法將其開啟。 
  - 當設定為 [*未*設定] 時，使用者可以選擇是否要使用 Microsoft Defender SmartScreen。 
  
  此原則僅適用于已加入 Microsoft Active Director 網域的 Windows 實例，或是已註冊裝置管理的 Windows 10 專業版或企業實例。

- **允許使用者層級的原生訊息主機（不需要系統管理員許可權即可安裝）**  
  **預設**：停用  

  啟用原生訊息主機的使用者層級安裝。 
  - 如果您停用此原則，Microsoft Edge 將只會使用安裝在系統層級上的原生訊息主機。 根據預設，如果您未設定此原則，Microsoft Edge 會允許使用使用者層級的原生訊息主機。

## <a name="next-steps"></a>後續步驟

[在 Intune 中使用安全性基準](security-baselines.md)

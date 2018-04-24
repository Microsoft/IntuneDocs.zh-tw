---
title: 適用於 Android 的合規性原則設定
description: 本主題說明適用於 Android 裝置的裝置相容性原則設定。
keywords: ''
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 01/23/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: e721c5c7-9678-4f3b-81d4-564da5efd337
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 4bf478225c22597b1645fc7d18e4329560bb1f03
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="compliance-policy-settings-for-android-devices-in-microsoft-intune"></a>Microsoft Intune 中的 Android 裝置的相容性原則設定

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

本主題所述的原則設定適用於執行 Android 4.0 及更新版本，或 Samsung KNOX 4.0 及更新版本的裝置。

如果您正在尋找其他平台的相關資訊，請選取下列其中一項︰
> [!div class="op_single_selector"]
> - [iOS 裝置的法務遵循政策設定](ios-compliance-policy-settings-in-microsoft-intune.md)
> - [Windows 裝置的相容性原則設定](windows-compliance-policy-settings-in-microsoft-intune.md)
> - [Android for Work 裝置的合規性政策設定](afw-compliance-policy-settings-in-microsoft-intune.md)

## <a name="system-security-settings"></a>系統安全性設定
### <a name="password"></a>密碼
- **需要密碼來解除鎖定行動裝置**︰將此項目設為 [是] 時，可要求使用者必須輸入密碼才能存取其裝置。

-  **密碼長度下限**：指定使用者密碼中至少必須含有的數字位數或字元數。

- **密碼品質**︰此設定會偵測裝置是否已設定您所指定的密碼需求。 啟用此設定可要求使用者符合 Android 裝置的特定密碼需求。 從下列選項進行選擇：

  -   **低安全性摸生物特徵辨識**
  -   **必要**
  -   **至少包含數字**
  -   **至少包含字母**
  -   **至少包含英數字元**
  -   **英數字元 (含符號)**

- **在非使用狀態幾分鐘後需要輸入密碼：**指定使用者必須重新輸入密碼之前的閒置時間。

- **密碼到期天數**：選取使用者在經過多少天數之後密碼到期，並必須建立新的密碼。

- **記住密碼歷程記錄**：此設定請搭配 [不得重複使用以前用過的密碼] 一起使用，以限制使用者不得建立之前用過的密碼。

- **不得重複使用以前用過的密碼：**如果已選取 [記住密碼歷程記錄]，請指定不得重複使用的舊密碼數目。

- **當裝置從閒置狀態返回時，需要密碼**：請與 [在非使用狀態幾分鐘後需要輸入密碼] 設定搭配使用。 系統會提示使用者輸入密碼，以存取達到 [在非使用狀態幾分鐘後需要輸入密碼] 設定所指定的非使用中時間的裝置。

### <a name="encryption"></a>加密
- **行動裝置需要加密**︰將此項目設為 [是] 時，可要求裝置必須加密才能連線到資源。 當您設定 [需要密碼來將行動裝置解除鎖定] 的設定時，裝置會加密。

## <a name="device-health-and-security-settings"></a>裝置健全狀況和安全性設定

- **不得破解裝置或刷機**：如果您啟用這個設定，會將遭破解的裝置評估為不符合規範。
- **裝置必須防止從不明來源安裝應用程式 (Android 4.0 或更新版本)**：若要封鎖已啟用 [安全性] > [不明來源] 的裝置，請啟用此設定，並將其設為 [是]。  

>[!IMPORTANT]
>側載應用程式要求將 [不明來源] 設定啟用。 只有當您不會在裝置上側載 Android 應用程式時，才應該強制執行這項法務遵循政策。

- **USB 偵錯需為停用 (Android 4.2 或更新版本)**︰指定是否要偵測已啟用 USB 偵錯選項的裝置。
- **裝置必須已啟用 [掃描裝置的安全性威脅 (Android 4.2-4.4)]**︰指定要在裝置上啟用 [驗證應用程式] 功能。
- **Android 安全性修補程式等級下限 (Android 6.0 或更新版本)**︰指定 Android 的最低修補程式等級。  未至少達此修補程式等級的裝置將視為不相容。 日期的格式必須指定為 YYYY-MM-DD。
- **必須啟用裝置威脅防護**：使用此設定進行來自 Lookout MTP 解決方案的風險評估，以做為相容的條件。 選取允許的最高威脅等級，這會是下列其中一項：

  - **無 (受保護)**：這是最安全的選項。 這表示裝置不能受到任何威脅。 如果在裝置上偵測到任何威脅，則會評估為不符合規範。
  - **低**︰如果只有低等級的威脅，則會將裝置評估為符合規範。 任何更高等級的威脅都會使裝置處於不符合規範狀態。
  - **中**︰如果裝置有低等級或中等級的威脅，則會將裝置評估為符合規範。 如果在裝置上偵測到高等級的威脅，則會判斷為不符合規範。
  - **高**：這是最不安全的選項。 基本上，這會允許所有威脅等級，或許僅在此解決方案的用途只有報告時才適用。

  如需詳細資訊，請參閱[建立 Lookout 裝置合規性原則](create-lookout-device-compliance-policy.md)。

## <a name="device-property-settings"></a>裝置屬性設定

- **最低作業系統版本需求︰**當裝置不符合最低作業系統版本需求時，它會回報為不符合規範。
  會顯示如何升級的資訊連結。 使用者可以選擇升級其裝置，之後便可以存取公司資源。

- **允許的最高作業系統版本**：當裝置使用的作業系統版本高於規則指定的版本時，會封鎖對公司資源的存取，並要求使用者連絡其 IT 系統管理員。在規則變更為允許該 OS 版本之前，此裝置無法用來存取公司資源。

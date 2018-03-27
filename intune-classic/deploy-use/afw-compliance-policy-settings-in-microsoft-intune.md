---
title: Android for Work 的合規性設定
description: 本主題說明適用於 Android 裝置並與 Android for Work 相容的裝置相容性原則設定。
keywords: ''
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 02/03/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: e721c5c7-9678-4f3b-81d4-564da5efd337
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: ab1e43d1cb66bdc6e0fc02324ffd1d8923e61174
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/22/2018
---
# <a name="compliance-policy-settings-for-android-for-work-devices-in-microsoft-intune"></a>Microsoft Intune 中的 Android for Work 裝置的相容性原則設定

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

本主題所述的原則設定適用於 Android for Work 裝置。

如果您正在尋找其他平台的相關資訊，請選取下列其中一項︰
> [!div class="op_single_selector"]
- [Android 的相容性原則設定](android-compliance-policy-settings-in-microsoft-intune.md)
- [iOS 裝置的法務遵循政策設定](ios-compliance-policy-settings-in-microsoft-intune.md)
- [Windows 裝置的相容性原則設定](windows-compliance-policy-settings-in-microsoft-intune.md)

## <a name="system-security-settings"></a>系統安全性設定
### <a name="password"></a>密碼
- **需要密碼來解除鎖定行動裝置︰**將此設定為 [是]，以要求使用者在存取他們的裝置前輸入密碼。

-  **密碼長度下限：**指定使用者密碼中至少必須包含的數字位數或字元數。

- **密碼品質**︰此設定會偵測是否已在裝置上設定您指定的密碼需求。 啟用此設定可要求使用者設定 Android 裝置的特定密碼需求。 從下列選項進行選擇：
  -   **低安全性摸生物特徵辨識**
  - **必要**
  -   **至少包含數字**
  -   **至少包含字母**
  -   **至少包含英數字元**
  -   **英數字元 (含符號)**

- **要求密碼前的閒置分鐘數：**指定使用者必須重新輸入密碼之前的閒置時間。

- **密碼到期 (天數)：**選取使用者密碼到期的天數，到期後他們必須建立新密碼。

- **記住密碼歷程記錄：**此設定請與 [不得重複使用以前用過的密碼] 一起使用，以限制使用者建立以前用過的密碼。

- **不得重複使用以前用過的密碼：**如果已選取 [記住密碼歷程記錄]，請指定不得重複使用的舊密碼數目。

- **裝置從閒置狀態恢復時必須輸入密碼：**這項設定應該與 [在非使用狀態多少分鐘後需要輸入密碼] 設定一起使用。 系統會提示終端使用者輸入密碼，以存取達到 [在非使用狀態幾分鐘後需要輸入密碼] 設定所指定的非使用中時間的裝置。

### <a name="encryption"></a>加密
- **行動裝置需要加密**︰您不需要進行此設定，因為 Android for Work 裝置會強制執行加密。

## <a name="device-health-and-security-settings"></a>裝置健全狀況和安全性設定

- **不得破解裝置或刷機：**如果您啟用這個設定，破解的裝置會評估為不相容。
- **裝置必須防止從不明來源安裝應用程式**︰您不需要進行此設定，因為 Android for Work 裝置一律會限制來自不明來源的安裝。 。  

- **需要停用 USB 偵錯**︰您不需要進行此設定，因為 Android for Work 裝置上已停用 USB 偵錯。

- **Android 安全性修補程式等級下限**︰使用此設定可指定 Android 修補程式等級下限。  未至少達此修補程式等級的裝置將視為不相容。 日期的格式必須指定為︰ YYYY-MM-DD。
- **必須啟用裝置威脅防護**：使用此設定進行來自裝置威脅防護解決方案的風險評估，以作為合規性的條件。 選取允許的最高威脅等級，這會是下列其中一項：

  - **無 (受保護)**：這是最安全的選項。 這表示裝置不能受到任何威脅。 如果在裝置上偵測到任何等級的威脅，則會評估為不相容。
  - **低**︰如果只有低等級的威脅，則會將裝置評估為相容。 任何更高等級的威脅都會使裝置處於不相容狀態。
  - **中**︰如果裝置有低等級或中等級的威脅，則會將裝置評估為相容。 如果在裝置上偵測到高層級的威脅，則會判斷為不相容。
  - **高**：這是最不安全的選項。 基本上，這會允許所有威脅等級，或許僅在此解決方案的用途只有報告時才適用。

  如需詳細資訊，請參閱[建立裝置合規性原則](create-lookout-device-compliance-policy.md)。

## <a name="device-property-settings"></a>裝置屬性設定
- **最低作業系統版本需求︰**當裝置不符合最低作業系統 (OS) 版本需求時，它會回報為不符合規範。
  會顯示如何升級的資訊連結。 終端使用者可以選擇升級其裝置，之後便可以存取公司資源。

- **允許的最高作業系統版本：**當裝置使用的作業系統 (OS) 版本高於規則指定的版本時，會封鎖對公司資源的存取，並要求使用者連絡其 IT 系統管理員。在將規則變更為允許該作業系統版本之前，此裝置無法用來存取公司資源。

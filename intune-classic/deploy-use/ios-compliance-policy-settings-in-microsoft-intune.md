---
title: iOS 裝置的合規性原則設定
description: 本主題說明您可以在 iOS 裝置的合規性政策中設定的規則和設定。
keywords: ''
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 12/15/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4a59d24f-ed58-49b1-b874-b2d4aea3ec76
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 7973dd757c69bc0a63f1ff5d24973acb6086d8a4
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/22/2018
---
# <a name="compliance-policy-settings-for-ios-devices-in-microsoft-intune"></a>Microsoft Intune 中 iOS 裝置的相容性原則設定

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

本主題所述的原則設定適用於執行 iOS 8.0 和更新版本的裝置。

如果您正在尋找其他平台的相關資訊，請選取下列其中一項︰
> [!div class="op_single_selector"]
- [Android 裝置的法務遵循政策設定](android-compliance-policy-settings-in-microsoft-intune.md)
- [Android for Work 的法務遵循政策設定](afw-compliance-policy-settings-in-microsoft-intune.md)
- [Windows 裝置的相容性原則設定](windows-compliance-policy-settings-in-microsoft-intune.md)

## <a name="system-security-settings"></a>系統安全性設定
### <a name="password"></a>密碼
- **需要密碼來解除鎖定行動裝置**︰將此設為 [是] 以要求使用者在存取他們的裝置前輸入密碼。 會加密使用密碼的 iOS 裝置。

- **允許簡單密碼**︰將此設為 [是]，讓使用者建立簡單密碼，例如 **1234** 或 **1111**。

-  **密碼長度下限**：指定使用者密碼中至少必須含有的數字位數或字元數。

- **必要的密碼類型**：指定使用者是否必須建立**英數**密碼或**數值**密碼。

- **字元集數目下限**︰如果您將 [必要的密碼類型] 設定為 [英數]，請使用此設定以指定密碼必須包含的字元集數目下限。 四個字元集為：
  -   小寫字母
  -   大寫字母
  -   符號
  -   數字

  若要將此設定設為較高的數目，使用者必須建立更複雜的密碼。

  針對 iOS 裝置，此設定表示密碼中必須包含的特殊字元數目 (例如 **!**、**#**、**&amp;**)。

- **在非使用狀態幾分鐘後需要輸入密碼**：指定使用者在經過多久閒置時間之後必須重新輸入密碼。

- **密碼到期天數**：選取使用者在經過多少天數之後密碼到期，並必須建立新的密碼。

- **記住密碼歷程記錄**：此設定請與 [不得重複使用以前用過的密碼] 一起使用，以限制使用者建立以前用過的密碼。

- **不得重複使用以前用過的密碼**：如果已選取 [記住密碼歷程記錄]，請指定不得重複使用的舊密碼數目。

- **裝置從閒置狀態恢復時必須輸入密碼**：請搭配使用這項設定與 [在非使用狀態幾分鐘後需要輸入密碼] 設定。 如果裝置達到 [在非使用狀態幾分鐘後需要輸入密碼] 設定所指定的閒置時間，系統會提示使用者輸入密碼，才能存取該裝置。

### <a name="email-profile"></a>電子郵件設定檔
- **必須由 Intune 管理電子郵件帳戶**：將此選項設定為 [是] 時，裝置必須使用部署到裝置的電子郵件設定檔。 在下列情況下，裝置視為不相容︰
  - 電子郵件設定檔部署到合規性政策的目標使用者群組以外的使用者群組。
  - 使用者已經在裝置上設定符合部署到該裝置之 Intune 電子郵件設定檔的電子郵件帳戶。 Intune 無法覆寫使用者所佈建的設定檔，因此也無法加以管理。 若要確保相容，使用者必須移除現有電子郵件設定。 然後 Intune 可以安裝受管理的電子郵件設定檔。

- **選取必須由 Intune 管理的電子郵件設定檔**︰如果已選取 [必須由 Intune 管理電子郵件帳戶] 設定，請選擇 [選取] 以指定 Intune 電子郵件設定檔。 電子郵件設定檔必須在裝置上。

     如需電子郵件設定檔的詳細資訊，請參閱[使用電子郵件設定檔與 Microsoft Intune 來設定公司電子郵件存取權](configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune.md)。

## <a name="device-health-settings"></a>裝置健全狀況設定

- **不得破解裝置或刷機**︰如果您啟用此設定，破解的裝置將不相容。

##  <a name="device-properties"></a>裝置內容
- **最低作業系統版本需求**︰當裝置不符合最低作業系統版本需求時，它會回報為不相容，
並顯示如何升級的資訊連結。 使用者可以選擇升級其裝置， 之後即可存取公司資源。

- **允許的最高作業系統版本**：當裝置使用的作業系統版本高於規則指定的版本時，會封鎖對公司資源的存取，並要求使用者連絡其 IT 系統管理員。在將規則變更為允許該 OS 版本之前，此裝置無法用來存取公司資源。

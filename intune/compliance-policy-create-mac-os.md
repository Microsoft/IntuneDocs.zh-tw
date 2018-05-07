---
title: 在 Microsoft Intune 中建立 macOS 裝置合規性原則 - Azure | Microsoft Docs
description: 建立或設定適用於 macOS裝置的 Microsoft Intune 裝置合規性原則以使用系統完整性保護、設定最低和最高作業系統版本、選擇您的密碼需求，以及加密資料存放區。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/16/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: a797c68ca43a6173a4bac70e914d3f763ce5e6d0
ms.sourcegitcommit: 2773f388f50654366197a95a6838306f70fc18b8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
---
# <a name="add-a-device-compliance-policy-for-macos-devices-with-intune"></a>使用 Intune 為 macOS 裝置新增裝置合規性政策

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune macOS 裝置合規性原則決定 macOS 設備必須符合的規則和設定，才能視為符合規範。 當您使用裝置相容性原則搭配條件式存取時，可以允許或封鎖公司資源的存取。 您也可以取得裝置報表，並針對不相容採取動作。 在 Intune Azure 入口網站中，可以為每個平台建立裝置相容性原則。 若要深入了解合規性原則，以及任何必要條件，請參閱[開始使用裝置合規性](device-compliance-get-started.md)。

下表說明搭配使用合規性政策與條件式存取原則時，不合規設定的管理方式：

---------------------------

| 原則設定 | macOS 10.11 及更新版本 |
| --- | --- |
| **PIN 或密碼設定** | 已修復 |   
| **裝置加密** | 已修復 (藉由設定 PIN 碼) |
| **電子郵件設定檔** | 已隔離 |
|**最低 OS 版本** | 已隔離 |
| **最高 OS 版本** | 已隔離 |

---------------------------

**已補救** = 裝置作業系統強制符合規範。 例如，強制使用者設定 PIN。

**已隔離** = 裝置作業系統不強制符合規範。 (例如，Android 裝置不強制使用者為裝置加密。)裝置不相容時，會採取下列動作︰

- 如果對使用者套用了條件式存取原則，裝置會遭到封鎖。
- 公司入口網站會通知使用者任何合規性問題的相關事項。

## <a name="create-a-device-compliance-policy"></a>建立裝置合規性政策

[!INCLUDE [new-device-compliance-policy](./includes/new-device-compliance-policy.md)]
5. 針對 [平台]，選取 [macOS]。 選擇 [組態設定]，並輸入 [裝置健全狀況]、[裝置屬性]，以及 [系統安全性] 設定。 完成後，請選取 [確定] 和 [建立]。

## <a name="device-health"></a>裝置健全狀況

- **需要系統完整性保護**：**需要**您的 macOS 裝置擁有[系統完整性保護](https://support.apple.com/HT204899)。

## <a name="device-properties"></a>裝置內容

- **最低作業系統版本**︰當裝置不符合最低作業系統版本需求時，它會回報為不符合規範。 並顯示如何升級的資訊連結。 終端使用者可以選擇升級其裝置，然後便可存取公司資源。
- **最高作業系統版本**：當裝置使用的作業系統版本高於規則指定的版本時，會封鎖對公司資源的存取。 系統會要求使用者連絡其 IT 管理員。在規則變更為允許該作業系統版本之前，此裝置將無法存取公司資源。

## <a name="system-security-settings"></a>系統安全性設定

### <a name="password"></a>密碼

- **需要密碼才可解除鎖定行動裝置**：**要求**使用者必須輸入密碼以存取其裝置。
- **簡單密碼**：設定為 [封鎖] 時，使用者將無法建立 **1234** 或 **1111** 之類的簡單密碼。 設定為 [未設定] 時，使用者可以建立 **1234** 或 **1111** 之類的密碼。
- **最小密碼長度**：輸入密碼至少須包含的位數或字元數。
- **密碼類型**：選擇密碼是否應該只包含**數值**字元，或是應該混合數字和其他字元 (**英數字元**)。
- **密碼中的非英數字元數目**：輸入密碼中必須包含的特殊字元 (&、#、%、! 等等) 數目下限。

    若設定較高的數目，使用者就必須建立較複雜的密碼。

- **停止活動幾分鐘後需要輸入密碼**：輸入在閒置多久後，使用者必須重新輸入密碼。
- **密碼到期 (天數)**：選取密碼到期且必須建立新密碼前的天數。
- **避免重複使用前幾個密碼**：輸入不可使用先前所使用的多少個密碼。

    > [!IMPORTANT]
    > 如果 macOS 裝置上的密碼需求有變更，會在使用者下次變更其密碼時才生效。 例如，如果您將密碼長度限制設定為八位數，而 macOS 裝置目前有六位數密碼，那麼在下次使用者更新裝置上的密碼之前，該裝置仍符合規範。

### <a name="encryption"></a>加密

- **對裝置上的資料存放區加密**：選擇 [需要] 來將裝置上的資料存放區加密。

## <a name="assign-user-groups"></a>指派使用者群組

1. 選擇您已設定的原則。 現有的原則位於 [裝置合規性] > [原則]。
2. 選擇原則，然後選擇 [指派]。 您可以包含或排除 Azure Active Directory (AD) 安全性群組。
3. 選擇 [選取的群組] 以查看您的 Azure AD 安全性群組。 選取要套用這項原則的使用者群組，然後選擇 [儲存] 將原則部署給使用者。

> [!TIP]
> 根據預設，裝置每 8 小時會檢查合規性。 但是，使用者可以透過 Intune 公司入口網站應用程式強制執行此程序。

您已對使用者套用此原則。 要套用原則之使用者的裝置將會接受相容性評估。

## <a name="next-steps"></a>接下來的步驟
[將電子郵件自動化，並為不符合規範的裝置新增動作](actions-for-noncompliance.md)  
[監視 Intune 裝置合規性原則](compliance-policy-monitor.md)
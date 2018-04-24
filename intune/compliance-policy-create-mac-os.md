---
title: 在 Microsoft Intune 中建立 macOS 裝置相容性原則
titleSuffix: ''
description: 建立適用於 macOS 裝置的 Microsoft Intune 裝置相容性原則，以便您可以指定裝置必須符合的需求。
keywords: ''
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 02/22/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: d6252680e64067e6d12530e0226632a1c5db7d28
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="create-a-device-compliance-policy-for-macos-devices-with-intune"></a>使用 Intune 為 macOS 裝置建立裝置合規性政策


[!INCLUDE [azure_portal](./includes/azure_portal.md)]

適用於 macOS 的 Intune 裝置相容性原則指定 macOS 設備必須符合的規則和設置，才能視為相容。 您可以使用這些原則與條件式存取來允許或封鎖存取公司資源，並取得裝置報告、針對不相容來採取動作。 在 Intune Azure 入口網站中，為每個平台建立裝置相容性原則。

## <a name="before-you-begin"></a>開始之前

在建立和指派裝置合規性政策之前，請先檢閱 Intune 裝置合規性政策的概念。

- 若要深入了解裝置合規性政策，請參閱[開始使用裝置合規性政策](device-compliance.md)。

> [!IMPORTANT]
> 您需要為每個平台建立裝置合規性政策。 Intune 裝置合規性政策設定會隨平台功能而定，也就是那些透過 MDM 通訊協定公開的設定。

下表說明搭配使用合規性政策與條件式存取原則時，不合規設定的管理方式：


| 原則設定 | macOS 10.11 及更新版本 |
| --- | --- |
| **PIN 或密碼設定** | 已修復 |   
| **裝置加密** | 已修復 (藉由設定 PIN 碼) |
| **電子郵件設定檔** | 已隔離 |
|**最低 OS 版本** | 已隔離 |
| **最高 OS 版本** | 已隔離 |  


**已補救** = 裝置作業系統強制符合規範。 (例如，強制使用者設定 PIN。)

**已隔離** = 裝置作業系統不強制符合規範。 (例如，Android 裝置不強制使用者為裝置加密。)裝置不相容時，會採取下列動作︰

- 如果對使用者套用了條件式存取原則，裝置會遭到封鎖。
- 公司入口網站會通知使用者任何合規性問題的相關事項。

## <a name="macos-compliance-policy-settings"></a>MacOS 合規性政策設定

建立符合 Intune 規範的新裝置時，您可以在不同的類別中設定不同的選項：

- 裝置健全狀況

- 裝置內容

- 系統安全性

### <a name="device-health"></a>裝置健全狀況

- **需要系統完整性保護** - 設為 [必要] 以檢查 macOS 裝置是否啟用系統完整性保護。

### <a name="device-properties"></a>裝置內容

- **最低 OS 版本** - 當裝置不符合最低 OS 版本需求時，會回報為不合規。 並顯示如何升級的資訊連結。 使用者可以選擇升級其裝置， 之後即可存取公司資源。

- **最高 OS 版本** - 當裝置使用的 OS 版本高於規則指定的版本時，會封鎖對公司資源的存取，並要求使用者連絡其 IT 系統管理員。在將規則變更為允許該 OS 版本之前，此裝置無法用來存取公司資源。

### <a name="system-security-settings"></a>系統安全性設定

#### <a name="password"></a>密碼

- **需要密碼以解除鎖定行動裝置** - 設為 [必要]，使用者就必須先輸入密碼才能存取其裝置。

- **簡單密碼** - 設為 [封鎖]，讓使用者無法建立 **1234** 或 **1111** 這樣的簡單密碼。

- **最小密碼長度** - 指定密碼至少須包含的位數或字元數。

- **密碼類型** - 指定使用者必須建立**英數字元**密碼或**數字**密碼。

- **密碼的非英數字元數目** - 若將 [需要的密碼類型] 設為 [英數字元]，請使用此設定指定密碼至少須包含的最少字元集數。 

    > [!NOTE]
    > 若設定較高的數目，使用者就必須建立較複雜的密碼。

    > [!IMPORTANT]
    > 若是 macOS 裝置，此設定是指密碼中必須包含的特殊字元數 (例如 **!** 、**#**、**&amp;** )。

- **停止活動幾分鐘後需要輸入密碼** - 指定在閒置多久後，使用者必須重新輸入密碼。

- **密碼到期 (天數)** - 指定密碼到期前的天數 (1 到 250 之間)，之後就必須建立新密碼。

- **避免重複使用前幾個密碼** - 指定不可重複使用先前使用的多少個密碼。

    > [!IMPORTANT]
    > 如果 macOS 裝置上的密碼需求有變更，會在使用者下次變更其密碼時才生效。 例如，如果您將密碼長度限制設定為八位數，而 macOS 裝置目前有六位數密碼，則在下次使用者更新裝置上的密碼之前，該裝置仍符合規範。

## <a name="to-create-a-device-compliance-policy"></a>建立裝置合規性政策

1. 移至 [Azure 入口網站](https://portal.azure.com)，並使用您的 Intune 認證登入。

2. 成功登入之後，您會看到 [Azure 儀表板]。

3. 選擇左功能表中的 [All services] (所有服務)，然後在文字方塊篩選中鍵入 **Intune**。

4. 選擇 [Intune]，您會看到 [Intune 儀表板]。

5. 選擇 [裝置合規性]，然後選擇 [管理] 下的 [原則]。

6. 選擇 [建立原則]。

7. 輸入名稱及描述，然後選擇要套用此原則的平台。

8. [Mac compliance policy] (Mac 相容性原則) 窗格隨即開啟，選擇裝置相容性設定的分類來指定設定：[系統安全性]、[裝置健全狀況] 和 [裝置屬性]。

10. 完成設定選擇後，請選擇每項裝置合規性設定類別下的 [確定]。

11. 選擇 [確定]，然後選擇 [建立]。

## <a name="assign-user-groups"></a>指派使用者群組

若要將合規性政策指派給使用者，請選擇您先前設定的原則。 現有的原則可以在 [裝置相容性 - 原則] 窗格中找到。

1. 選擇您想要指派給使用者的裝置合規性政策，然後選擇 [指派]。 這會開啟窗格讓您選取 **Azure Active Directory 安全性群組**，並將其指派給原則。

2. 選擇 [選取群組] 會開啟窗格顯示 Azure AD 安全性群組。

3. 選擇 [儲存] 將裝置相容性原則指派給 Azure AD 安全性群組。

4. 將裝置相容性原則指派給群組後，您就可以關閉 [指派] 窗格。

    > [!TIP]
    > 根據預設，裝置每八小時會檢查一次合規性，但使用者可以透過 Intune 公司入口網站應用程式強制執行此程序。

## <a name="next-steps"></a>接下來的步驟

[如何監視裝置合規性政策](compliance-policy-monitor.md)

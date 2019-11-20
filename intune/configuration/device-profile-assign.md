---
title: 在 Microsoft Intune - Azure 中指派裝置設定檔 | Microsoft Docs
description: 使用 Azure 入口網站將裝置設定檔和原則指派給使用者和裝置。 了解如何在 Microsoft Intune 的設定檔指派中排除群組。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/05/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f6f5414d-0e41-42fc-b6cf-e7ad76e1e06d
ms.reviewer: altsou
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 50b91251572e45669f197df7ac4e5ff94caf47a1
ms.sourcegitcommit: 1a7f04c80548e035be82308d2618492f6542d3c0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2019
ms.locfileid: "73755330"
---
# <a name="assign-user-and-device-profiles-in-microsoft-intune"></a>在 Microsoft Intune 中指派使用者和裝置設定檔

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

您可以建立設定檔，而且它會包含您所輸入的所有設定。 下一個步驟是將設定檔部署或「指派」至 Azure Active Directory (Azure AD) 使用者或裝置群組。 獲指派時，使用者和裝置會收到您的設定檔，並套用您所輸入的設定。

本文說明如何指派設定檔，並包含有關在設定檔上使用範圍標籤的一些資訊。

> [!NOTE]  
> 當原則已移除或不再指派給裝置時，設定可能會保留現有的值。 此設定不會還原為預設值。 若要將設定變更為不同的值，請建立新的原則並加以指派。

## <a name="before-you-begin"></a>開始之前

確保您具備指派原則的適當角色。 如需詳細資訊，請參閱[使用 Microsoft Intune 的角色型存取控制 (RBAC)](../fundamentals/role-based-access-control.md)。

## <a name="assign-a-device-profile"></a>指派裝置設定檔

1. 登入 [Microsoft Endpoint Manager 系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。
2. 選取 [裝置]   > [組態設定檔]  。 隨即列出所有設定檔。
3. 選取您想要指派的設定檔 > [指派]  。
4. 選擇 [包含]  群組或 [排除]  群組，然後選取您的群組。 當您選取群組時，會選擇 Azure AD 群組。 若要選取多個群組，請按住 **Ctrl** 鍵，然後選取您的群組。

    ![在設定檔指派中包含或排除群組的選項螢幕擷取畫面](./media/device-profile-assign/group-include-exclude.png)

5. [儲存]  變更。

### <a name="evaluate-how-many-users-are-targeted"></a>評估設定為目標的使用者人數

當您指派設定檔時，您也可以**評估**有多少使用者受到影響。 此功能會計算使用者，但不會計算裝置。

1. 在系統管理中心內，選取 [裝置]   > [組態設定檔]  。
2. 選取設定檔 > [指派]   > [評估]  。 此時會出現一個訊息，向您顯示此設定檔設定為目標的使用者人數。

如果 [評估]  按鈕呈現灰色，請確認該設定檔已指派給一或多個群組。

## <a name="use-scope-tags-or-applicability-rules"></a>使用範圍標籤或適用性規則

當您建立或更新設定檔時，也可以將範圍標籤與適用性規則新增到設定檔。

**範圍標籤**是將政策指派並篩選到特定群組 (例如人力資源或所有 US-NC 員工) 的絕佳方式。 如需詳細資訊，請參閱[針對分散式 IT 使用 RBAC 和範圍標籤](../fundamentals/scope-tags.md)。

在 Windows 10 裝置上，您可以新增**適用性規則**，讓設定檔僅適用於特定 OS 版本或特定 Windows 版本。 [適用性規則](device-profile-create.md#applicability-rules)提供更多資訊。

## <a name="exclude-groups-from-a-profile-assignment"></a>從設定檔指派排除群組

Intune 裝置組態設定檔可讓您從原則指派包含與排除群組。

最佳做法是特別針對您的使用者群組建立並指派原則。 此外，請特別針對您的裝置群組建立並指派不同原則。 如需群組的詳細資訊，請參閱[新增群組來組織使用者與裝置](../fundamentals/groups-add.md)。

當您指派原則時，請在包含和排除群組時使用下表。 核取記號表示支援該指派：

![從設定檔指派包含或排除群組所支援的選項](./media/device-profile-assign/include-exclude-user-device-groups.png)

### <a name="what-you-should-know"></a>您應該知道的事項

- 在下列相同群組類型案例中，排除的優先順序高於包含：

  - 包含使用者群組與排除使用者群組
  - 包含裝置群組與排除裝置群組

  例如，您可以將裝置設定檔指派給 [所有公司使用者]  使用者群組，但排除 [資深管理層]  使用者群組中的成員。 因為這兩個群組都是使用者群組，所以 [所有公司使用者]  會取得原則，但 [資深管理人員]  除外。

- Intune 不會評估使用者對裝置群組關聯性。 如果您將原則指派給混合群組，結果可能不是您想要或預期的。

  例如，您可以將裝置設定檔指派給 [所有使用者]  使用者群組，但排除 [所有個人裝置]  裝置群組。 在此混合群組原則指派中，[所有使用者]  會取得原則。 排除不適用。

  因此，不建議將原則指派給混合群組。

## <a name="next-steps"></a>後續步驟

如需有關監視設定檔以及執行設定檔之裝置的指引，請參閱[監視裝置設定檔](device-profile-monitor.md)。

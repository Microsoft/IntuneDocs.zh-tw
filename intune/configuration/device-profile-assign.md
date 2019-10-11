---
title: 在 Microsoft Intune - Azure 中指派裝置設定檔 | Microsoft Docs
description: 使用 Azure 入口網站將裝置設定檔和原則指派給使用者和裝置。 了解如何在 Microsoft Intune 的設定檔指派中排除群組。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/17/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f6f5414d-0e41-42fc-b6cf-e7ad76e1e06d
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 344ffdfefd8b354c9d2ab31f2d08c2a25456f970
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2019
ms.locfileid: "71724109"
---
# <a name="assign-user-and-device-profiles-in-microsoft-intune"></a>在 Microsoft Intune 中指派使用者和裝置設定檔

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

您可以建立設定檔，而且它會包含您所輸入的所有設定。 下一個步驟是將設定檔部署或「指派」至 Azure Active Directory (Azure AD) 使用者或裝置群組。 獲指派時，使用者和裝置會收到您的設定檔，並套用您所輸入的設定。

本文說明如何指派設定檔，並包含有關在設定檔上使用範圍標籤的一些資訊。

## <a name="assign-a-device-profile"></a>指派裝置設定檔

1. 登入 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
2. 選取 [裝置設定]   > [設定檔]  。 隨即列出所有設定檔。
3. 選取您想要指派的設定檔 > [指派]  。
4. 選擇 [包含]  群組或 [排除]  群組，然後選取您的群組。 當您選取群組時，會選擇 Azure AD 群組。 若要選取多個群組，請按住 **Ctrl** 鍵，然後選取您的群組。

    ![在設定檔指派中包含或排除群組的選項螢幕擷取畫面](./media/device-profile-assign/group-include-exclude.png)

5. [儲存]  變更。

### <a name="evaluate-how-many-users-are-targeted"></a>評估設定為目標的使用者人數

當您指派設定檔時，您也可以**評估**有多少使用者受到影響。 此功能會計算使用者，但不會計算裝置。

1. 在 Intune 中，選取 [裝置設定]   > [設定檔]  。
2. 選取設定檔 > [指派]   > [評估]  。 此時會出現一個訊息，向您顯示此設定檔設定為目標的使用者人數。

如果 [評估]  按鈕呈現灰色，請確認該設定檔已指派給一或多個群組。

## <a name="use-scope-tags-or-applicability-rules"></a>使用範圍標籤或適用性規則

當您建立或更新設定檔時，也可以將範圍標籤和適用性規則新增到設定檔。

**範圍標籤**是將政策指派並篩選到特定群組 (例如人力資源或所有 US-NC 員工) 的絕佳方式。 如需詳細資訊，請參閱[針對分散式 IT 使用 RBAC 和範圍標籤](../fundamentals/scope-tags.md)。

在 Windows 10 裝置上，您可以新增**適用性規則**，讓設定檔僅適用於特定 OS 版本或特定 Windows 版本。 [適用性規則](device-profile-create.md#applicability-rules)有更多資訊。

## <a name="exclude-groups-from-a-profile-assignment"></a>從設定檔指派排除群組

Intune 裝置組態設定檔可讓您從原則指派排除群組。

Intune 不會查看使用者對裝置群組關聯性。 包含使用者群組的同時排除裝置群組可能不會獲得您預期的結果。 在使用者群組對使用者群組和裝置群組對裝置群組案例中，排除的優先順序高於包含。

例如，您可以將裝置設定檔指派給 [所有公司使用者]  使用者群組，但排除 [資深管理層]  使用者群組中的成員。 由於這兩個群組都是使用者群組，因此，會從原則中排除 [資深管理層]  的所有成員，即使他們是 [所有公司使用者]  包含群組的成員也一樣。

使用混合式群組時，包含的優先順序高於排除 (例如使用者群組對裝置群組，或裝置群組對使用者群組)。

例如，您想要將裝置設定檔指派給組織中的所有使用者，但 Kiosk 裝置除外。 您包含**所有使用者**群組，但是排除**所有裝置**群組。 在此情況下，即使使用者的裝置位於 [所有裝置]  群組，所有使用者及其裝置還是會取得政策。

排除只會查看群組的直接成員。 它不會包含與使用者相關聯的裝置。 不過，不含使用者的裝置無法取得原則。 發生此行為的原因是不含使用者的裝置與 [所有使用者]  群組沒有關聯性。

如果您包含**所有裝置**，並排除**所有使用者**，則所有裝置都會收到原則。 在此情況下，目的是要排除此原則中有相關聯使用者的裝置。 不過，它不會排除裝置，因為排除只會比對直屬群組成員。

## <a name="next-steps"></a>後續步驟

如需有關監視設定檔以及執行設定檔之裝置的指引，請參閱[監視裝置設定檔](device-profile-monitor.md)。

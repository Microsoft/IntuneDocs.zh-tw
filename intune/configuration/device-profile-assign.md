---
title: 在 Microsoft Intune - Azure 中指派裝置設定檔 | Microsoft Docs
description: 使用 Microsoft Endpoint Manager 系統管理中心將裝置設定檔和原則指派給使用者和裝置。 了解如何在 Microsoft Intune 的設定檔指派中排除群組。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/18/2020
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
ms.openlocfilehash: c6678c3fbc247ac0595775c0ccc72c7bdb9c55e1
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/20/2020
ms.locfileid: "77513090"
---
# <a name="assign-user-and-device-profiles-in-microsoft-intune"></a>在 Microsoft Intune 中指派使用者和裝置設定檔

您可以建立設定檔，而且它會包含您所輸入的所有設定。 下一個步驟是將設定檔部署或「指派」至 Azure Active Directory (Azure AD) 使用者或裝置群組。 獲指派時，使用者和裝置會收到您的設定檔，並套用您所輸入的設定。

本文說明如何指派設定檔，並包含有關在設定檔上使用範圍標籤的一些資訊。

> [!NOTE]  
> 當設定檔已移除或不再指派給裝置時，可能會發生不同的情況，視設定檔中的設定而定。 這些設定是以 CSP 為基礎，而每個 CSP 可以不同的方式來處理設定檔移除。 例如，設定可能會維持現有的值，而不會還原回預設值。 此行為是由作業系統中的每個 CSP 所控制。 如需 Windows CSP 的清單，請參閱[設定服務提供者 (CSP) 參考](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference) \(部分機器翻譯\)。
>
> 若要將設定變更為不同的值，請建立新的設定檔，將設定設為 [未設定]  ，然後指派設定檔。 套用至裝置之後，使用者應該可以控制將設定變更為其慣用的值。
>
> 進行這些設定時，建議您部署到試驗群組。 如需更多 Intune 首度發行建議，請參閱[建立首度發行計畫](../fundamentals/planning-guide-rollout-plan.md)。

## <a name="before-you-begin"></a>開始之前

確保您具備指派設定檔的適當角色。 如需詳細資訊，請參閱[使用 Microsoft Intune 的角色型存取控制 (RBAC)](../fundamentals/role-based-access-control.md)。

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

**範圍標籤**是將設定檔篩選到特定群組 (例如 `US-NC IT Team` 或 `JohnGlenn_ITDepartment`) 的絕佳方式。 如需詳細資訊，請參閱[針對分散式 IT 使用 RBAC 和範圍標籤](../fundamentals/scope-tags.md)。

在 Windows 10 裝置上，您可以新增**適用性規則**，讓設定檔僅適用於特定 OS 版本或特定 Windows 版本。 [適用性規則](device-profile-create.md#applicability-rules)提供更多資訊。

## <a name="user-groups-vs-device-groups"></a>使用者群組與裝置群組的比較

許多使用者會詢問何時使用使用者群組，以及何時使用裝置群組。 答案取決於您的目標。 以下是一些入門指南。

### <a name="device-groups"></a>裝置群組

如果您想要在裝置上套用設定 (不論登入者為何)，請將設定檔指派給裝置群組。 套用至裝置群組的設定一律會與裝置 (而不是使用者) 搭配使用。

例如：

- 裝置群組適用於管理沒有專用使用者的裝置。 例如，您擁有列印票證的裝置、掃描清查的裝置、由輪班工人共用的裝置、指派給特定倉儲的裝置等等。 將這些裝置放在裝置群組中，並將設定檔指派給此裝置群組。

- 您會建立[裝置韌體設定介面 (DFCI) Intune 設定檔](device-firmware-configuration-interface-windows.md)，以更新 BIOS 中的設定。 例如，您可以將此設定檔設定為停用裝置攝影機，或鎖定開機選項，以防止使用者啟動另一個 OS。 此設定檔是指派給裝置群組的好情節。

- 在某些特定的 Windows 裝置上，無論誰使用該裝置，您始終都希望控制一些 Microsoft Edge 設定。 例如，您想要封鎖所有下載、將所有 cookie 限制在目前的瀏覽工作階段，並刪除瀏覽歷程記錄。 針對此情節，請將這些特定 Windows 裝置放在裝置群組中。 然後，[在 Intune 中建立系統管理範本](administrative-templates-windows.md)、新增這些裝置設定，然後將此設定檔指派給裝置群組。

總而言之，當您不在意誰在裝置上登入或是否有人登入時，請使用裝置群組。 您希望您的設定一律在裝置上。

### <a name="user-groups"></a>使用者群組

套用至使用者群組的設定檔設定一律會與使用者一起使用，並且在登入其許多裝置時，與使用者一起使用。 使用者通常擁有許多裝置，例如工作用的 Surface Pro 和個人的 iOS/iPadOS 裝置。 而且，使用者也可以從這些裝置存取電子郵件和其他組織資源。

例如：

- 您想要為所有使用者的所有裝置上放置一個 [技術支援中心] 圖示。 在此情節中，請將這些使用者放在使用者群組中，並將您的 [技術支援中心] 圖示設定檔指派給這個使用者群組。
- 使用者收到新的組織擁有的裝置。 使用者使用其網域帳戶登入裝置。 裝置會自動在 Azure AD 中註冊，並自動由 Intune 管理。 此設定檔是指派給使用者群組的好情節。
- 每當使用者登入裝置時，您會想要控制應用程式 (例如 OneDrive 或 Office) 中的功能。 在此情節中，請將您的 OneDrive 或 Office 設定檔設定指派給使用者群組。

  例如，您想要封鎖 Office 應用程式中不受信任的 ActiveX 控制項。 您可以[在 Intune 中建立系統管理範本](administrative-templates-windows.md)、進行這項設定，然後將此設定檔指派給使用者群組。

總而言之，當您希望設定和規則一律與使用者一起使用時 (無論他們使用什麼裝置)，請使用使用者群組。

## <a name="exclude-groups-from-a-profile-assignment"></a>從設定檔指派排除群組

Intune 裝置組態設定檔可讓您從設定檔指派包含與排除群組。

最佳做法是特別針對您的使用者群組建立並指派設定檔。 此外，請特別針對您的裝置群組建立並指派不同設定檔。 如需群組的詳細資訊，請參閱[新增群組來組織使用者與裝置](../fundamentals/groups-add.md)。

當您指派設定檔時，請在包含和排除群組時使用下表。 核取記號表示支援該指派：

![從設定檔指派包含或排除群組所支援的選項](./media/device-profile-assign/include-exclude-user-device-groups.png)

### <a name="what-you-should-know"></a>您應該知道的事項

- 在下列相同群組類型案例中，排除的優先順序高於包含：

  - 包含使用者群組與排除使用者群組
  - 包含裝置群組與排除裝置群組

  例如，您可以將裝置設定檔指派給 [所有公司使用者]  使用者群組，但排除 [資深管理層]  使用者群組中的成員。 因為這兩個群組都是使用者群組，所以 [所有公司使用者]  會取得設定檔，但 [資深管理人員]  除外。

- Intune 不會評估使用者對裝置群組關聯性。 如果您將設定檔指派給混合群組，結果可能不是您想要或預期的。

  例如，您可以將裝置設定檔指派給 [所有使用者]  使用者群組，但排除 [所有個人裝置]  裝置群組。 在此混合群組設定檔指派中，[所有使用者]  會取得設定檔。 排除不適用。

  因此，不建議將設定檔指派給混合群組。

## <a name="next-steps"></a>後續步驟

如需有關監視設定檔以及執行設定檔之裝置的指引，請參閱[監視裝置設定檔](device-profile-monitor.md)。

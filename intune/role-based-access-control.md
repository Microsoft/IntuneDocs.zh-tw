---
title: 使用 Microsoft Intune 的角色型存取控制 (RBAC)
description: 了解 RBAC 如何在 Microsoft Intune 中讓您控制誰可以執行動作及變更。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ca3de752-3caa-46a4-b4ed-ee9012ccae8e
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: ee0e6ad7e46abe8da4c1b03e836eb9ba2f5991d0
ms.sourcegitcommit: 4b83697de8add3b90675c576202ef2ecb49d80b2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/13/2019
ms.locfileid: "67044156"
---
# <a name="role-based-access-control-rbac-with-microsoft-intune"></a>使用 Microsoft Intune 的角色型存取控制 (RBAC)

角色型存取控制 (RBAC) 可協助您管理誰可以存取貴組織的資源，以及他們可以使用這些資源執行的動作。  藉由[指派角色](assign-role.md)給您的 Intune 使用者，您可以限制他們能夠看到和變更的內容。 每個角色都有一組權限，用來決定具有該角色之使用者可在組織內存取及變更的內容。

若要建立、編輯或指派角色，您的帳戶必須具備下列其中一項 Azure AD 權限︰
- **全域管理員**
- **Intune 服務管理員** (也稱為**Intune 系統管理員**)

如需 Intune RBAC 的忠告和建議，您可以查看這一系列五個展示範例和逐步解說的影片：[1](https://www.youtube.com/watch?v=5deXLMLcnKY)、[2](https://www.youtube.com/watch?v=38dnMBLuxbQ)、[3](https://www.youtube.com/watch?v=6vqg9cAkMbY)、[4](https://www.youtube.com/watch?v=5yOLajFFMHE)、[5](https://www.youtube.com/watch?v=P5DDvsSF4Wk)。

## <a name="roles"></a>角色
角色可定義一組權限，這些權限會授與給獲指派該角色的使用者。
您可以同時使用內建角色和自訂角色。 內建角色涵蓋一些常見的 Intune 案例。 您可以使用所需的一組確切權限[建立自己的自訂角色](create-custom-role.md)。 有數個 Azure Active Directory 角色具備 Intune 的權限。
若要查看角色，請選擇 [Intune]   > [角色]   > [所有角色]  > 選擇角色。 您會看到下列頁面：

-   **屬性**：角色的名稱、描述、類型、指派和範圍標籤。 
-   **權限**：列出定義角色具有哪些權限的完整切換集。
-   **指派**：定義哪些使用者可以存取哪些使用者/裝置的[角色指派]( assign-role.md)清單。 一個角色可以有多個指派，而一個使用者可以位於多個指派中。

### <a name="built-in-roles"></a>內建角色
您可以將內建角色指派給群組，而無須進行進一步的設定。 您無法刪除或編輯內建角色的名稱、描述、類型或權限。 如需每個內建角色權限的完整清單，請參閱 [Intune RBAC Table](https://gallery.technet.microsoft.com/Intune-RBAC-table-2e3c9a1a) (Intune RBAC 資料表)。

- **技術服務人員**：對使用者和裝置執行遠端工作，並可將應用程式或原則指派給使用者或裝置。
- **Apple 設定檔管理員**：管理相容性原則、組態設定檔、Apple 註冊、公司裝置識別碼，以及安全性基準。
- **唯讀操作員**：檢視使用者、裝置、註冊、設定和應用程式資訊。 無法對 Intune 進行變更。
- **應用程式管理員**：管理行動及受控應用程式、可以讀取裝置資訊，並可檢視裝置組態設定檔。
- **Intune 角色管理員**：管理自訂的 Intune 角色，以及為內建的 Intune 角色新增指派。 這是唯一可為系統管理員指派權限的 Intune 角色。
- **學校管理員**：管理 [Intune 教育版](introduction-intune-education.md)中的 Windows 10 裝置。

### <a name="custom-roles"></a>自訂角色
您可以使用自訂權限來建立自己的角色。 如需自訂角色的詳細資訊，請參閱[建立自訂角色](create-custom-role.md)。

### <a name="azure-active-directory-roles-with-intune-access"></a>具有 Intune 存取權的 Azure Active Directory 角色
| Azure Active Directory 角色 | 所有 Intune 資料 | Intune 稽核資料 |
| --- | :---: | :---: |
| 全域管理員 | 讀取/寫入 | 讀取/寫入 |
| Intune 服務管理員 | 讀取/寫入 | 讀取/寫入 |
| 條件式存取管理員 | 無 | 無 |
| 安全性系統管理員 | 唯讀 | 唯讀 |
| 安全性操作員 | 唯讀 | 唯讀 |
| 安全性讀取者 | 唯讀 | 唯讀 |
| 合規性管理員 | 無 | 唯讀 |
| 相容性資料管理員 | 無 | 唯讀 |

> [!TIP]
> Intune 也會顯示三個 Azure AD 延伸模組：[使用者]  、[群組]  及 [條件式存取]  ，這些都是使用 Azure AD RBAC 來控制的。 此外，**使用者帳戶管理員**只會執行 AAD 使用者/群組活動，並沒有在 Intune 中執行所有活動的完整權限。 如需詳細資訊，請參閱 [RBAC 搭配 Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-assign-admin-roles)。
### <a name="roles-created-in-the-intune-classic-portal"></a>在 Intune 傳統入口網站中建立的角色
只有具有「完整」權限的 Intune「服務管理員」  使用者可從 Intune 傳統入口網站移轉至 Azure 入口網站上的 Intune。 您必須將具有「唯讀」或「技術服務人員」存取權的 Intune **服務管理員**使用者重新指派給 Azure 入口網站中的 Intune 角色，並將它們傳統入口網站中移除。
> [!IMPORTANT]
> 如果您的系統管理員仍需要一個能使用 Intune 來管理電腦的存取途徑，則您可能需要在傳統入口網站中保留「Intune 服務管理員」存取權。

## <a name="role-assignments"></a>角色指派
角色指派定義：

- 哪些使用者指派給角色
- 他們可以看到哪些資源
- 他們可以變更哪些資源。

您可以將自訂角色和內建角色指派給您的使用者。 使用者必須具備 Intune 授權，才能獲指派 Intune 角色。
若要查看角色指派，請選擇 [Intune]   > [角色]   > [所有角色]  > 選擇角色 > 選擇指派。 您會看到下列頁面：

-   **屬性**：指派的名稱、描述、角色、成員、範圍和標籤。
-   **成員**：已列出群組中所有使用者都有權管理 [範圍 (群組)] 中列出的使用者/裝置。
-   **範圍 (群組)** ：這些群組中所有使用者/裝置都可由 [成員] 中的使用者管理。
-   **[範圍 (標籤)](scope-tags.md)** ：[成員] 中使用者可以查看具有相同範圍標籤的資源。

### <a name="multiple-role-assignments"></a>多個角色指派
如果使用者有多個角色指派，則這些角色指派的權限會延伸到不同物件，如下所示：

- 指派權限只會套用到該角色指派 [範圍 (群組)] 中的物件 (例如原則或應用程式)。 指派權限不會套用到其他角色指派中的物件，除非其他指派明確地授與這些權限。
- 其他權限 (例如建立和讀取)，會套用到任何使用者指派中類型相同的所有物件 (例如所有原則或所有應用程式)。
- 不同類型物件 (例如原則或應用程式) 的權限不會彼此套用。 例如，原則之讀取權限不會為使用者指派中的應用程式提供讀取權限。

## <a name="next-steps"></a>後續步驟
- [將角色指派給使用者](assign-role.md)
- [建立自訂角色](create-custom-role.md)

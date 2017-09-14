---
title: "RBAC 搭配 Intune"
titleSuffix: Azure portal
description: "Intune Azure 預覽版︰了解 RBAC 如何讓您控制誰可以執行動作及變更。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 06/21/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ca3de752-3caa-46a4-b4ed-ee9012ccae8e
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: e9dc65389485d2a77e351b5e781824eed0612054
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/09/2017
---
# <a name="role-based-administration-control-rbac-with-intune"></a>以角色為基礎的系統管理 (RBAC) 搭配 Intune

RBAC 可協助您控制誰可以在組織內執行各種 Intune 工作，以及這些工作適用於誰。 您可以利用涵蓋一些常見 Intune 案例的內建角色，或建立自己的角色。 角色的定義包括︰

- **角色定義**：角色的名稱、其所管理的資源，以及針對每個資源授與的權限。
- **成員**：授與權限的使用者群組。
- **範圍**：成員可以管理的使用者或裝置群組。
- **指派**：當定義、成員及範圍設定完成之後，便完成了指派。

![Intune RBAC 範例](./media/intune-rbac-1.PNG)

從新的 Azure 入口網站開始，**Azure Active Directory (Azure AD)** 提供兩個可與 Intune 搭配使用的目錄角色。 這些角色會獲得完整的權限，以在 Intune 中執行所有活動：

- **全域管理員：**具有此角色的使用者可存取 Azure AD 中的所有管理功能，以及與 Azure AD 同盟的服務，例如 Exchange Online、SharePoint Online 及商務用 Skype Online。 註冊 Azure AD 租用戶的人員會變成全域管理員。 只有全域管理員可以指派其他 Azure AD 系統管理員角色。 您的組織可以擁有多個全域管理員。 全域管理員可為任何使用者及其他所有系統管理員重設密碼。

- **Intune 服務管理員：**存在服務時，具有此角色的使用者在 Intune 內具有全域權限。 此外，此角色還提供管理使用者、裝置與建立和管理群組的能力。

- **條件式存取系統管理員：**具有此角色的使用者，只擁有檢視、建立、修改和刪除條件式存取原則的權限。

    > [!IMPORTANT]
    > Intune 服務管理員角色不提供管理 Azure AD 條件式存取設定的能力。

    > [!TIP]
    > Intune 也會顯示三個使用 Azure AD RBAC 控制的 Azure AD 延伸模組：**使用者**、**群組**和**條件式存取**。 此外，**使用者帳戶管理員**只會執行 AAD 使用者/群組活動，並沒有在 Intune 中執行所有活動的完整權限。 如需詳細資料，請參閱 [RBAC 搭配 Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-assign-admin-roles)。

## <a name="roles-created-in-the-intune-classic-portal"></a>在 Intune 傳統入口網站中建立的角色

只有具有「完整」權限的 Intune「服務管理員」使用者可從 Intune 傳統入口網站移轉至 Azure 入口網站上的 Intune。 您需要將具有「唯讀」或「技術支援」存取權的 Intune **服務管理員**使用者重新指派至 Azure 入口網站中的 Intune 角色，並將它們傳統入口網站移除。

> [!IMPORTANT]
> 如果您的系統管理員仍然需要使用 Intune 管理電腦的存取權，您就可能需要在傳統入口網站中保留 Intune「服務管理員」存取權。

## <a name="built-in-roles"></a>內建角色

以下是 Intune 的內建角色。您可以將它們指派給群組而不進一步設定：

- **技術支援人員**：對使用者和裝置執行遠端工作，並可將應用程式或原則指派給使用者或裝置。
- **原則和設定檔管理員**：管理合規性原則、組態設定檔、Apple 註冊和公司裝置識別碼。
- **唯讀操作員**：檢視使用者、裝置、註冊、設定和應用程式資訊， 但無法對 Intune 進行變更。
- **應用程式管理員**：管理行動裝置及受管理的應用程式，並可讀取裝置資訊。

### <a name="to-assign-a-built-in-role"></a>指派內建角色

1. 在 [Intune 角色] 上，選擇您想要指派的內建角色。

2. 在 [<角色名稱> - 內容] 刀鋒視窗中，依序選擇 [管理] 和 [指派]。

    > [!NOTE]
    > 您無法刪除或編輯內建角色

3. 在自訂角色刀鋒視窗中，選擇 [指派]。

4. 在 [角色指派] 刀鋒視窗中，為指派輸入**名稱**及**描述** (非必要)，然後選擇下列項目︰
    - **成員** - 選取包含您要授與權限之使用者的群組。
    - **範圍** - 選取包含上列成員可以管理的使用者群組。
<br></br>
5. 完成之後，請按一下 [確定] 。 新指派會隨即顯示在指派清單中。

### <a name="intune-rbac-table"></a>Intune RBAC 表格

- 下載 [Intune RBAC 表格](https://gallery.technet.microsoft.com/Intune-RBAC-table-2e3c9a1a) \(英文\) 可查看每個角色可以執行之工作的更多詳細資料。

## <a name="custom-roles"></a>自訂角色

您可以建立自訂角色，其中包含特定工作功能所需的任何權限。 例如，如果 IT 部門群組管理應用程式、原則和組態設定檔，您可以將這裡的所有權限一起新增至一個自訂角色。

> [!IMPORTANT]
> 若要建立、編輯或指派角色，您的帳戶必須具備下列其中一項 Azure AD 權限︰
> - **全域管理員**
> - **Intune 服務管理員**

### <a name="to-create-a-custom-role"></a>建立自訂角色

1. 使用您的 Intune 認證登入 [Azure 入口網站](https://portal.azure.com)。

2. 選擇左功能表中的 [更多服務]，然後在文字方塊篩選中輸入 **Intune**。

3. 選擇 [Intune]，隨即開啟 [Intune 儀表板]，然後選擇 [Intune 角色]。

4. 在 [Intune 角色] 刀鋒視窗中，依序選擇 [Intune 角色] 和 [新增自訂]。

5. 在 [新增自訂角色] 刀鋒視窗中輸入新角色的名稱及描述，然後按一下 [權限]。

3. 在 [權限] 刀鋒視窗中，選擇此角色所要使用的權限。 使用 [Intune RBAC 表格](https://gallery.technet.microsoft.com/Intune-RBAC-table-2e3c9a1a) \(英文\) 可協助您決定套用哪些權限。

4. 完成後，請選擇 [確定]。

5. 在 [新增自訂角色] 刀鋒視窗中按一下 [建立]。 新角色會顯示在 [Intune 角色] 刀鋒視窗的清單中。

### <a name="to-assign-a-custom-role"></a>指派自訂角色

1. 在 [Intune 角色] 上，選擇您想要指派的自訂角色。

2. 在 [<角色名稱> - 內容] 刀鋒視窗中，依序選擇 [管理] 和 [指派]。 您也可以在此刀鋒視窗中編輯或刪除現有的角色。

3. 在自訂角色刀鋒視窗中，選擇 [指派]。

4. 在 [角色指派] 刀鋒視窗中，為指派輸入**名稱**及**描述** (非必要)，然後選擇下列項目︰
    - **成員** - 選取包含您要授與權限之使用者的群組。
    - **範圍** - 選取包含上列成員可以管理的使用者群組。
<br></br>
5. 完成之後，請按一下 [確定] 。 新指派會隨即顯示在指派清單中。

## <a name="next-steps"></a>後續步驟

[使用 Intune 技術服務人員角色搭配疑難排解入口網站](help-desk-operators.md)

## <a name="see-also"></a>請參閱

[使用 Azure AD 指派角色](https://docs.microsoft.com/azure/active-directory/active-directory-users-assign-role-azure-portal)

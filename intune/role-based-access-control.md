---
title: RBAC 搭配 Microsoft Intune
description: 了解角色型存取控制 (RBAC) 如何讓您控制誰可以執行動作，並在 Microsoft Intune 中進行變更。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/27/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ca3de752-3caa-46a4-b4ed-ee9012ccae8e
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.openlocfilehash: 745fd366520ba55e54a5b666d47469debb241ab9
ms.sourcegitcommit: e08a26558174be3ea8f3d20646e577f1493ea21a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54831525"
---
# <a name="role-based-administration-control-rbac-with-microsoft-intune"></a>以角色為基礎的系統管理 (RBAC) 搭配 Microsoft Intune

RBAC 可協助您控制誰可以在組織內執行各種 Intune 工作，以及這些工作適用於誰。 您可以利用涵蓋一些常見 Intune 案例的內建角色，或建立自己的角色。 角色的定義包括︰

- **角色定義**：角色的名稱、其所管理的資源，以及針對每個資源授與的權限。
- **成員**：獲授與權限的使用者群組。
- **範圍**：成員可以管理的使用者或裝置群組。
- **指派**：當定義、成員及範圍設定完成之後，即已指派角色。

![Intune RBAC 範例](./media/intune-rbac-1.PNG)

從新的 Azure 入口網站開始，**Azure Active Directory (Azure AD)** 提供兩個可與 Intune 搭配使用的目錄角色。 這些角色會獲得完整的權限，以在 Intune 中執行所有活動：

- **全域管理員：** 具有此角色的使用者可存取 Azure AD 中及與 Azure AD 同盟之服務 (例如 Exchange Online、SharePoint Online 及商務用 Skype Online) 中的所有管理功能。 註冊 Azure AD 租用戶的人員會變成全域管理員。 只有全域管理員可以指派其他 Azure AD 系統管理員角色。 您的組織可以擁有多個全域管理員。 全域管理員可為任何使用者及其他所有系統管理員重設密碼。

- **Intune 服務管理員：** 具有此角色的使用者在 Intune 服務存在時，於此服務內具有全域權限。 此外，除任何取代 Azure 限制以外，此角色提供管理使用者、裝置的能力，並且建立和管理 Intune 群組。

- **條件式存取系統管理員：** 具有此角色的使用者只具備檢視、建立、修改及刪除條件式存取原則的權限。

    > [!IMPORTANT]
    > Intune 服務管理員角色不提供管理 Azure AD 條件式存取設定的能力。
    > 使用者必須具備 Intune 授權，才能獲指派 Intune 角色。

    > [!TIP]
    > Intune 也會顯示三個 Azure AD 延伸模組：[使用者]、[群組]及 [條件式存取]，這些是使用 Azure AD RBAC 來控制的延伸模組。 此外，**使用者帳戶管理員**只會執行 AAD 使用者/群組活動，並沒有在 Intune 中執行所有活動的完整權限。 如需詳細資訊，請參閱 [RBAC 搭配 Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-assign-admin-roles)。

## <a name="roles-created-in-the-intune-classic-portal"></a>在 Intune 傳統入口網站中建立的角色

只有具有「完整」權限的 Intune「服務管理員」使用者可從 Intune 傳統入口網站移轉至 Azure 入口網站上的 Intune。 您必須將具有「唯讀」或「技術服務人員」存取權的 Intune **服務管理員**使用者重新指派給 Azure 入口網站中的 Intune 角色，並將它們傳統入口網站中移除。

> [!IMPORTANT]
> 如果您的系統管理員仍需要一個能使用 Intune 來管理電腦的存取途徑，則您可能需要在傳統入口網站中保留「Intune 服務管理員」存取權。

## <a name="built-in-roles"></a>內建角色

您可以將內建角色指派給群組，而無須進行進一步的設定。 您無法刪除或編輯內建角色。

- **技術服務人員**：對使用者和裝置執行遠端工作，並可將應用程式或原則指派給使用者或裝置。
- **Apple 設定檔管理員**：管理合規性原則、組態設定檔、Apple 註冊和公司裝置識別碼。
- **唯讀操作員**：檢視使用者、裝置、註冊、設定和應用程式資訊。 無法對 Intune 進行變更。
- **應用程式管理員**：管理行動及受控應用程式、可以讀取裝置資訊，並可檢視裝置組態設定檔。
- **Intune 角色管理員**：管理自訂的 Intune 角色，以及為內建的 Intune 角色新增指派。 這是唯一可為系統管理員指派權限的 Intune 角色。
- **學校管理員**：管理 [Intune 教育版](introduction-intune-education.md)的 Windows 10 裝置，並可以採取下列動作： 

    |權限|操作|
    |---|---|
    |稽核資料|讀取|
    |DeviceConfigurations|指派、建立、刪除、讀取、更新|
    |裝置註冊管理員|讀取、更新|
    |受控裝置|讀取、更新<!--, Delete [To be added in 1803]-->|
    |行動裝置應用程式|指派、建立、刪除、讀取、更新|
    |報告|讀取|
    |遠端動作|清除電腦、重新開機、遠端鎖定、淘汰、同步處理裝置、抹除|
    |組織|讀取|

### <a name="to-assign-a-built-in-role"></a>指派內建角色

1. 登入 [Azure 入口網站](https://portal.azure.com)。
2. 選擇 [All services] (所有服務) > [Intune]。 Intune 位於 [Monitoring + Management] (監視 + 管理) 區段。
3. 在 [Intune] 窗格中，選擇 [角色] > [所有角色]。
4. 在 [Intune 角色 - 所有角色] 窗格中，選擇您想要指派的內建角色。

5. 在 [<角色名稱> - 概觀] 窗格中，依序選擇 [管理] 和 [指派]。

6. 在自訂角色窗格中，選擇 [指派]。

7. 在 [角色指派] 窗格上，輸入指派的 [名稱] 並視需要輸入 [描述]。

8. 針對 [成員]，選擇包含您要授與權限之使用者的群組。

9. 針對 [範圍]，選擇包含上述成員可管理之使用者的群組。
<br></br>
10. 完成後，選擇 [確定]。 新指派會隨即顯示在指派清單中。

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

2. 選擇左功能表中的 [All services] (所有服務)，然後在文字方塊篩選中鍵入 **Intune**。

3. 選擇 [Intune] > [角色] > [所有角色] > [新增自訂]。

4. 在 [Add Custom Role] (新增自訂角色) 窗格中，輸入新角色的名稱和描述，然後按一下 [權限]。

5. 在 [權限] 窗格中，選擇此角色所要使用的權限。 使用 [Intune RBAC 表格](https://gallery.technet.microsoft.com/Intune-RBAC-table-2e3c9a1a) \(英文\) 可協助您決定套用哪些權限。

6. 完成後，選擇 [確定]。

7. 在 [Add Custom Role] (新增自訂角色) 窗格中按一下 [建立]。 新角色會顯示在 [Intune 角色 - 所有角色] 窗格的清單中。

### <a name="to-assign-a-custom-role"></a>指派自訂角色

1. 在 [Intune 角色 - 所有角色] 窗格中，選擇您想要指派的自訂角色。

2. 在 [<角色名稱> - 概觀] 窗格中，依序選擇 [管理] 和 [指派]。 您也可以在此窗格中編輯或刪除現有的角色。

3. 在自訂角色窗格中，選擇 [指派]。

4. 在 [角色指派] 窗格上，輸入指派的 [名稱] 並視需要輸入 [描述]。

5. 針對 [成員]，選擇包含您要授與權限之使用者的群組。

6. 針對 [範圍]，選擇包含上述成員可管理之使用者的群組。

7. 完成後，選擇 [確定]。 新指派會隨即顯示在指派清單中。

## <a name="next-steps"></a>後續步驟

[使用 Intune 技術服務人員角色搭配疑難排解入口網站](help-desk-operators.md)

## <a name="see-also"></a>請參閱

[使用 Azure AD 指派角色](https://docs.microsoft.com/azure/active-directory/active-directory-users-assign-role-azure-portal)

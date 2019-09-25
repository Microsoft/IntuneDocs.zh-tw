---
title: 新增使用者並授與權限
titleSuffix: Microsoft Intune
description: 同步處理內部部署使用者和 Azure AD 以及將您 Intune 訂閱的權限授與系統管理員。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/28/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 6e9ec662-465b-4ed4-94c1-cff0fe18f126
ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: fed90635a450ed59827482d2f2c03d17a05d9673
ms.sourcegitcommit: ede86a3cb094c12e3e218b956abb9935bec76902
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/05/2019
ms.locfileid: "71239622"
---
# <a name="add-users-and-grant-administrative-permission-to-intune"></a>新增使用者並授與 Intune 系統管理權限

[!INCLUDE [both-portals](./includes/note-for-both-portals.md)]

身為系統管理員，您可以直接新增使用者，或同步內部部署 Active Directory 中的使用者。 新增之後，使用者便可以註冊裝置，並存取公司資源。 您也可以授與使用者其他權限，包括「全域管理員」  和「服務管理員」  權限。

## <a name="add-users-to-intune"></a>將使用者新增至 Intune
您可以透過 [Microsoft 365 系統管理中心](https://admin.microsoft.com)或 [Azure 入口網站](https://portal.azure.com/#blade/Microsoft_Intune_DeviceSettings/ExtensionLandingBlade/overview)，將使用者手動新增至 Intune 訂閱。 系統管理員可以編輯使用者帳戶來指派 Intune 授權。 您可以在 Microsoft 365 系統管理中心或 Intune Azure 入口網站指派授權。 如需有關使用 Microsoft 365 系統管理中心的詳細資訊，請參閱[個別或大量將使用者新增至 Microsoft 365 系統管理中心](https://support.office.com/article/Add-users-individually-or-in-bulk-to-Office-365-Admin-Help-1970f7d6-03b5-442f-b385-5880b9c256ec)。

### <a name="add-intune-users-in-the-microsoft-365-admin-center"></a>在 Microsoft 365 系統管理中心新增 Intune 使用者
1. 使用全域管理員或使用者管理管理員帳戶登入 [Microsoft 365 系統管理中心](https://admin.microsoft.com)。
2. 在 Office 365 功能表中，選取 [系統管理員]  。
3. 在系統管理中心，選取 [新增使用者]  。

   ![[新增原則] 區段的螢幕擷取畫面](media/office-add-user.png)

4. 指定下列使用者詳細資訊：
   - **名字**
   - **姓氏**
   - **顯示名稱**
   - **使用者名稱** - 儲存在 Azure Active Directory 中用來存取服務的通用主體名稱 (UPN)
   - **位置**
   - **連絡資訊** (選用)
   - **密碼** - 自動產生或指定

     ![[新增使用者] 區段的螢幕擷取畫面](media/office-add-user-details.png)

5. 指派 Intune 授權。 選取 [產品授權]  ，然後選擇產品的授權。 需要包括 Intune 的授權。
6. 選擇 [新增]  建立新的使用者。

### <a name="add-intune-users-in-the-azure-portal"></a>在 Azure 入口網站中新增 Intune 使用者
1. 登入 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
2. 選取 [使用者]   > [所有使用者]  。
3. 在系統管理中心，選取 [新增使用者]  。
   ![[新增使用者] 的螢幕擷取畫面](media/intune-add-user.png)
4. 指定下列使用者詳細資訊：
   - **名稱**
   - **使用者名稱** - Azure Active Directory 入口網站中的新名稱 ![新增名稱和使用者名稱的螢幕擷取畫面](media/intune-add-user-info.png) 選擇 [確定]  繼續。
5. 或者，您也可以指定下列使用者內容：
   - **設定檔** - 工作資訊，包括 [職稱]  和 [部門] 
   - **群組** - 選取要為使用者新增的群組
   - **目錄角色** - 授與使用者系統管理權限，包括 Intune 服務管理員角色。

   選取 [建立]  ，將新的使用者新增至 Intune。
6. 選取 [設定檔]  ，然後為新使用者選擇 [使用位置]  。 在為新的使用者指派 Intune 授權之前，需要使用位置。 選擇 [儲存]  繼續。
    ![使用位置的螢幕擷取畫面](media/intune-add-user-loc.png)
7. 選取 [授權]  ，然後選擇 [指派]  ，為這位使用者指派 Intune 授權。 需要有 Intune 授權，才能註冊裝置或存取公司資源。 選取 [產品]  ，依序選擇授權類型和 [選取]  ，然後選擇 [指派]  。

## <a name="grant-admin-permissions"></a>授與系統管理員權限

將使用者新增到 Intune 訂閱之後，我們建議您將系統管理權限授與幾位使用者。  若要授與系統管理員權限，請遵循下列步驟：

### <a name="give-admin-permissions-in-office-365"></a>在 Office 365 中授與系統管理員權限
1. 使用全域管理員帳戶登入 [Microsoft 365 系統管理中心](https://admin.microsoft.com)。
2. 在 Office 365 功能表中，選取 [系統管理員]  。
3. 在系統管理中心內，選擇 [作用中使用者]  ，然後選擇要授與系統管理員權限的使用者。

4. 在 [角色]  欄中，選擇 [編輯]  。

    ![系統管理使用者的螢幕擷取畫面](./media/office-assign-roles-open.png)

5. 選擇要從可用角色清單中授與的系統管理員權限。
![指派角色的螢幕擷取畫面](./media/office-assign-roles.png)
6. 選擇 [儲存]  。

### <a name="give-admin-permissions-in-the-azure-portal"></a>在 Azure 入口網站中授與系統管理員權限
1. 使用全域管理員帳戶登入 [Azure 入口網站](https://portal.azure.com)。
2. 在 Azure 入口網站中，選擇 [使用者]  ，然後選擇您要授與系統管理員權限的使用者。
3. 選取 [目錄角色]  ，然後選取權限。
  ![目錄角色的螢幕擷取畫面](./media/add-intune-directory-role.png)
4. 選擇 [儲存]  。

### <a name="types-of-administrators"></a>系統管理員類型

將一或多個系統管理員權限指派給使用者。 這些權限會定義使用者的管理範圍及其可以管理的工作。 不同 Microsoft 雲端服務之間的系統管理員權限是共通的，而且某些服務可能不支援部分權限。 Azure 入口網站和 Microsoft 365 系統管理中心皆會列出 Intune 未使用的受限系統管理員角色。 Intune 系統管理員權限包括下列選項：

- **全域管理員** - (Office 365 和 Intune) 存取 Intune 中的所有系統管理功能。 註冊 Intune 的人員將成為全域管理員。全域管理員是唯一可以指派其他管理員角色的管理員。 在組織中可以有一個以上的全域管理員。 我們建議的最佳做法是只讓公司內幾位人員擁有此角色，以降低企業風險。
- **密碼管理員** - (Office 365 和 Intune) 重設密碼、管理服務要求以及監控服務健康狀況。 密碼管理員限於重設使用者的密碼。
- **服務管理員** - (Office 365 和 Intune) 開啟 Microsoft 的支援要求，以及檢視服務儀表板和訊息中心。 除了開啟及讀取支援票證之外，他們擁有「僅檢視」權限。
- **計費管理員** - (Office 365 和 Intune) 進行採購、管理訂閱、管理支援票證以及監控服務健康狀況。
- **使用者管理員** - (Office 365 和 Intune) 重設密碼、監控服務健全狀況、新增和刪除使用者帳戶和管理服務要求。 使用者管理管理員無法刪除全域管理員、建立其他管理員角色，或重設其他管理員的密碼。
- **Intune 服務管理員** - 除了使用 [目錄角色]  選項建立系統管理員之權限以外的所有 Intune 全域管理員權限。

您用來建立 Microsoft Intune 訂閱的帳戶即為全域管理員。 最佳做法是不要使用全域管理員進行日常管理工作。 雖然系統管理員不需要 Intune 授權即可存取 Azure 入口網站上的 Intune，但為執行某些管理工作，例如設定 Exchange 服務連接器則需要 Intune 授權。

若要存取 Microsoft 365 系統管理中心，您的帳戶必須已經設定 [允許登入]  。 在 Azure 入口網站的 [設定檔]  下，將 [封鎖登入]  設定為 [否]  以允許存取。 此狀態與獲得訂閱的授權有所區別。 根據預設，所有使用者帳戶的狀態均為 [已允許]  。 沒有系統管理員權限的使用者可以使用 Microsoft 365 系統管理中心重設 Intune 密碼。

## <a name="sync-active-directory-and-add-users-to-intune"></a>同步處理 Active Directory 並將使用者新增至 Intune
您可以設定目錄同步處理，將使用者帳戶從內部部署 Active Directory 匯入到其中包括 Intune 使用者的 Microsoft Azure Active Directory (Azure AD)。 讓內部部署的 Active Directory 與所有 Azure Active Directory 服務連線，可更易於管理使用者身分識別。 您也可以設定單一登入功能，讓使用者的驗證體驗親切又簡單。 透過連結同一個 [Azure AD 租用戶](https://azure.microsoft.com/documentation/articles/active-directory-aadconnect/)與多個服務，您之前已經同步的使用者帳戶就可用於所有雲端服務。

### <a name="how-to-sync-on-premises-users-with-azure-ad"></a>如何將內部部署使用者與 Azure AD 同步
同步處理使用者帳戶與 Azure AD 唯一需要的工具是 [Azure AD Connect 精靈](https://www.microsoft.com/download/details.aspx?id=47594)。 Azure AD Connect 精靈提供簡單和引導式的體驗，將內部部署身分識別基礎結構連線至雲端。 選擇您的拓撲和需求 (單一或多個目錄、密碼雜湊同步處理、傳遞驗證或同盟)。 此精靈會部署並設定啟動及執行連線所需之所有元件。 包括︰同步處理服務、Active Directory 同盟服務 (AD FS)，以及 Azure AD PowerShell 模組。

> [!TIP]
> Azure AD Connect 包含先前發行為 Dirsync 和 Azure AD Sync 的功能。深入了解[目錄整合](https://technet.microsoft.com/library/jj573653.aspx)。 若要了解將本機目錄的使用者帳戶同步至 Azure AD，請參閱 [Active Directory 與 Azure AD 的相似性](https://technet.microsoft.com/library/dn518177.aspx)。

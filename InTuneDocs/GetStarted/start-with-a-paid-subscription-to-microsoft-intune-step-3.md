---
title: "同步處理 Active Directory 並將使用者新增至 Intune | Microsoft Intune"
description: "同步處理內部部署使用者和 Azure AD 以及將您 Intune 訂閱的權限授與系統管理員"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 11/22/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6e9ec662-465b-4ed4-94c1-cff0fe18f126
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 29b6e5a3d319c741482fcc2b600842e2e42b96e2
ms.openlocfilehash: 33534c685ad3a4ddfd4b605e088132f2b8ff2c36


---


# <a name="sync-active-directory-and-add-users-to-intune"></a>同步處理 Active Directory 並將使用者新增至 Intune
您可以設定目錄同步處理，將使用者帳戶從內部部署 Active Directory 匯入到 Microsoft Azure Active Directory (Azure AD)。 讓內部部署的 Active Directory 與所有 Azure Active Directory 服務連線，可更易於管理使用者身分識別。 您也可以設定單一登入功能，讓使用者的驗證體驗親切又簡單。

為了更方便起見，當您透過相同的 [Azure AD 租用戶](https://azure.microsoft.com/documentation/articles/active-directory-aadconnect/)使用多項服務時，您先前已同步處理的使用者帳戶，可供所有共用相同 Azure AD 租用戶訂用帳戶的雲端式服務使用。

## <a name="synchronize-on-premises-users-with-azure-ad"></a>同步處理內部部署使用者與 Azure AD
同步處理使用者帳戶與 Azure AD 唯一需要的工具是 [Azure AD Connect 精靈](https://www.microsoft.com/download/details.aspx?id=47594)。 Azure AD Connect 精靈提供簡單和引導式的體驗，將內部部署身分識別基礎結構連線至雲端。  請選擇您的拓撲和需求 (單一或多個目錄、密碼同步或同盟)，精靈就會部署並設定讓連線運作所需的一切元件。 包括︰同步處理服務、Active Directory 同盟服務 (AD FS)，以及 Azure AD PowerShell 模組。

> [!TIP]
> Azure AD Connect 包含先前發行為 Dirsync 和 Azure AD Sync 的功能。 深入了解[目錄整合](http://technet.microsoft.com/library/jj573653.aspx)。 若要了解將使用者帳戶從本機目錄同步至 Azure AD 的優點，請參閱 [Active Directory 與 Azure AD 的相似性](http://technet.microsoft.com/library/dn518177.aspx)。

## <a name="grant-administrator-permissions"></a>授與系統管理員權限

若要管理 Intune，您將使用︰
- 兩種類型的系統管理員帳戶
- 具有其他權限的使用者帳戶
- 兩個 Web 架構系統管理主控台/入口網站，授與系統管理員存取權，以存取他們應該管理的項目。

將使用者新增到您的 Intune 訂閱後，建議您將系統管理認證授與幾個使用者帳戶。 您用來指派系統管理認證的主控台，會視您想要指派的系統管理員類型而定：

-   **租用戶系統管理員**：使用 **Microsoft Intune 帳戶入口網站**，指派此類型的系統管理員來管理您的訂閱，包括計費、雲端存放裝置及管理可使用 Intune 的使用者。

-   **服務管理員**：使用 **Microsoft Intune 系統管理員主控台**，指派此類型的系統管理員來進行日常工作，包括管理行動裝置或電腦、部署原則或軟體，以及執行報表。

下列各節將說明這些帳戶和入口網站。

## <a name="administrator-accounts-and-user-accounts-with-special-permissions"></a>系統管理員帳戶和具有特殊權限的使用者帳戶

以下是您會在 Intune 中使用的帳戶及權限。

### <a name="tenant-administrator"></a>租用戶系統管理員
|權限層級|詳細資訊|
|--------------------------|-------------------------|
|租用戶系統管理員會被指派一個系統管理員角色，此角色定義該使用者的系統管理範圍以及他們可以管理的工作。<br /><br />系統管理員角色在不同的 Microsoft 雲端服務之間是共通的，不過某些服務可能不支援部分角色。<br /><br /> Microsoft Intune 使用下列角色：<br /><br />- 全域管理員<br />- 計費管理員<br />- 密碼管理員<br />- 服務支援系統管理員<br />- 使用者管理管理員|依預設，您用來建立 Microsoft Intune 訂閱的帳戶是具有全域管理員角色的租用戶系統管理員。<br /></br>  身為租用戶系統管理員，您可以使用 [!INCLUDE[wit_icp_1](../includes/wit_icp_1_md.md)] 來管理 Intune 的訂閱，以及從 [!INCLUDE[wit_icp_2](../includes/wit_icp_2_md.md)] 指派租用戶系統管理員。<br /><br />使用具有全域管理員角色的租用戶系統管理員可以存取 [!INCLUDE[wit_adminconsole](../includes/wit_adminconsole_md.md)]來指派第一個服務系統管理員。 基於最佳作法，請勿使用租用戶系統管理員來進行日常管理工作。 租用戶系統管理員不需要 Intune 的授權即可存取 [!INCLUDE[wit_icp_2](../includes/wit_icp_2_md.md)]。<br /><br />租用戶系統管理員是 Microsoft 雲端服務之間的共通概念。 當您訂閱 Intune 時，您的服務就是 Microsoft Azure AD 的租用戶。 請參閱[什麼是 Azure AD 目錄？](http://technet.microsoft.com/library/jj573650.aspx)的 Azure AD 租用戶一節。|


### <a name="service-administrator"></a>服務系統管理員
|權限層級|詳細資訊|
|--------------------------|-------------------------|
|服務系統管理員會獲指派下列其中一種權限：<br /><br />**完整存取權**：授與 [!INCLUDE[wit_adminconsole](../includes/wit_adminconsole_md.md)] 所有區域的存取權，而無任何限制。 這也可新增及管理其他服務系統管理員。<br /><br />**唯讀存取權**：授與 [!INCLUDE[wit_adminconsole](../includes/wit_adminconsole_md.md)] 所有區域的讀取權限。 唯讀服務系統管理員無法修改資料，但可以執行報表。<br /><br />**服務台人員 - 群組節點**：授與權限，讓服務管理員只執行一組通常會與服務台人員案例相關聯的工作。 如需此權限集合的資訊，請參閱[根據系統管理員角色自訂 Intune 主控台檢視](/intune/deploy-use/control-what-admins-can-see-in-the-microsoft-intune-admin-console)。|根據預設，Intune 不會指派服務管理員。 反之，您必須使用具有全域管理員角色的租用戶系統管理員來指派訂閱的第一個服務系統管理員。 </br></br> 身為服務管理員，您可以使用 [!INCLUDE[wit_adminconsole](../includes/wit_adminconsole_md.md)] 來管理 Intune 的日常工作。<br /><br />您可以從管理主控台中指派服務系統管理員。 服務管理員需要 Intune 的授權，才能存取管理主控台。|



### <a name="device-enrollment-managers"></a>裝置註冊管理員
|權限層級|詳細資訊|
|--------------------------|-------------------------|
|裝置註冊管理員是標準使用者帳戶，具有可註冊五個以上裝置的其他權限。|每位 [!INCLUDE[wit_firstref](../includes/wit_firstref_md.md)] 使用者預設最多可以註冊五個裝置。 不過，您可以將裝置註冊管理員權限提供給使用者帳戶，然後使用該帳戶來註冊大型公司所擁有裝置的群組。 如果會暫時性地將裝置指派給使用者，或可能以不需要使用者與裝置關聯的資訊站模式提供服務，則這非常實用。|




>[!div class="step-by-step"]

>[&larr; **網域設定**](.\start-with-a-paid-subscription-to-microsoft-intune-step-2.md)     [**管理 Intune 授權** &rarr;](.\start-with-a-paid-subscription-to-microsoft-intune-step-4.md)  



<!--HONumber=Nov16_HO4-->



---
title: "MAM 原則的必要條件 | Microsoft Docs"
description: "本主題說明您在建立行動應用程式管理原則之前設定使用者的先決條件。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 11/29/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7e6a85e7-e007-41b6-9034-64d77f547b87
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: ab6d9b6b296fb4e1fb0aaa9496fede28976728dc
ms.openlocfilehash: 53b86bf579af6af29fd36ce58f9cdf1e92b98abc
ms.lasthandoff: 04/14/2017


---

# <a name="get-ready-to-configure-app-protection-policies-in-the-azure-portal"></a>準備好在 Azure 入口網站中設定應用程式保護原則

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

本主題描述您在 Azure 入口網站中建立應用程式保護原則**之前**，必須完成的必要條件與步驟。

若要了解 Intune 應用程式保護原則如何保護您的公司資料，請參閱[使用應用程式保護原則來保護應用程式和資料](protect-apps-and-data-with-microsoft-intune.md)。

## <a name="what-is-the-azure-portal"></a>什麼是 Azure 入口網站？

Azure 入口網站是建立應用程式保護原則的新管理主控台。 它支援下列 MAM 案例：
- 在 Intune 中註冊的裝置
- 由其他行動裝置管理 (MDM) 解決方案管理的裝置
- 未受任何 MDM 解決方案管理的裝置 (BYOD)

目前，**Intune 系統管理員主控台**和 **Azure 入口網站**皆可讓您設定應用程式保護原則。  請考慮下列事項：

* 您在 **Azure 入口網站**中建立的原則，可支援之前列出的**所有 MAM 案例**。 **Intune 系統管理員主控台**則僅支援針對**由 Intune 註冊及管理的裝置**來建立原則。

* 因為**新的設定**只能新增至 **Azure 入口網站**，所以 Intune 系統管理員主控台中可能不會顯示所有應用程式原則設定。

* 如果您**同時**在 Intune 管理主控台和 Azure 入口網站中建立應用程式保護原則，則會**將 Azure 入口網站中的原則套用至應用程式並部署至使用者**。
    * 在 Intune 管理主控台中建立的應用程式保護原則無法匯入到 Azure 入口網站。  您必須在 Azure 入口網站中重新建立應用程式保護原則。


* 其他**應用程式管理功能** (例如部署應用程式和應用程式設定原則) 目前只可用於 **Intune 系統管理員主控台**。


如果您是 Azure 入口網站的新手，請閱讀[適用於 Microsoft Intune 應用程式保護原則的 Azure 入口網站](azure-portal-for-microsoft-intune-mam-policies.md)，以取得使用 Azure 入口網站的基本知識。

如需如何在 Intune 管理主控台中建立應用程式保護原則的指示，請參閱[在 Microsoft Intune 主控台中設定及部署行動應用程式管理原則](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md)。


##  <a name="supported-platforms"></a>支援的平台
- iOS 8.1 或更新版本
- Android 4 或更新版本
- Windows 10

>[!NOTE]
>從 1703 版開始，可在不含註冊案例的 MAM 中定義 Windows 10 裝置的應用程式保護原則。 如需詳細資訊，請參閱[使用 Windows 資訊保護 (WIP) 保護您的企業資料](https://technet.microsoft.com/itpro/windows/keep-secure/protect-enterprise-data-using-wip)。

##  <a name="supported-apps"></a>支援的應用程式
* **Microsoft 應用程式︰**這些應用程式已內建 Intune App SDK，而在您套用應用程式保護原則之前將不需要進一步處理。
若要查看受支援的 Microsoft 應用程式完整清單，請移至 Microsoft Intune 應用程式合作夥伴頁面上的 [Microsoft Intune mobile application gallery](https://www.microsoft.com/cloud-platform/microsoft-intune-apps) (Microsoft Intune 行動應用程式庫)。 按一下應用程式來查看支援的案例和平台，並查看該應用程式是否支援多重身分識別。

* **您組織的企業營運應用程式**：您必須先準備這些應用程式來包含 Intune App SDK，才能套用應用程式保護原則。

  * 針對 Intune 所管理的裝置，請參閱[決定如何準備應用程式以進行 MAM](decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune.md)。

  * 若是不受管理的裝置 (例如員工擁有的裝置) 或由其他行動裝置管理解決方案所管理的裝置，請參閱[保護未在 Intune 註冊之裝置上的企業營運應用程式和資料](protect-line-of-business-apps-and-data-on-devices-not-enrolled-in-microsoft-intune.md)。

## <a name="prerequisites"></a>必要條件

-   **Microsoft Intune 訂閱**。 使用者需要 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 授權才能取得使用應用程式保護原則的應用程式。
如果您目前使用 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 來管理裝置，表示您已經有 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 訂閱。 如果您已經購買 Enterprise Mobility Suite (EMS) 授權，則您也會擁有 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 訂閱。 如果您正在嘗試 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 以查看 MAM 功能，您可以在 [Microsoft Intune 頁面](https://www.microsoft.com/server-cloud/products/microsoft-intune/)上取得試用帳戶。

    若要檢查您是否擁有 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 訂閱，請移至 Office 入口網站的 [帳單] 頁面。  如果您有訂閱，您在訂閱中應該會看到 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 為 [作用中]。

-   下列作業需要 **Office 365 訂閱**：

  - 將應用程式保護原則套用至具有多重身分識別支援的應用程式。

  - 建立 SharePoint Online 和 Exchange Online 工作帳戶。 不支援 Exchange 內部部署和 SharePoint 內部部署。

-   **針對新式驗證的商務用 Skype Online 設定**。 如需詳細資訊，請參閱[啟用新式驗證](http://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx)。


- Azure Active Directory (Azure AD) 以建立使用者。 當使用者開啟應用程式並輸入公司認證時，Azure AD 便會驗證使用者。

    > [!NOTE]
    > 您必須在 Azure AD 中設定使用者群組。 您無法在 Azure 入口網站中使用 Intune 使用者群組來部署應用程式保護原則。

### <a name="create-users-and-assign-microsoft-intune-licenses"></a>建立使用者及指派 Microsoft Intune 授權

1.  使用您的系統管理員認證登入 [Office 入口網站](http://portal.office.com)。

2.  依照 [Intune 評估指南](https://docs.microsoft.com/intune/understand-explore/get-started-with-a-30-day-trial-of-microsoft-intune)的**完成 Intune 30 天評估步驟**一節所述來新增使用者，然後指派 Intune 授權。 若要讓使用者能夠存取 Office 入口網站、Azure AD 入口網站和 Azure 入口網站，請將 [全域管理員角色] 指派給使用者。

5.  應用程式保護原則會部署到 Azure Active Directory 的使用者群組。 若要建立應用程式保護原則的使用者群組，請遵循[建立群組來組織評估訂閱使用者和裝置](https://docs.microsoft.com/intune/understand-explore/get-started-with-a-30-day-trial-of-microsoft-intune-step-3)中的＜建立使用者群組＞一節所述來建立使用者群組。

### <a name="assign-roles-to-non-global-admin-users"></a>指派角色給非全域系統管理員使用者

全域管理員可以存取 [Azure 入口網站](https://portal.azure.com)。  如果您想讓非全域管理員的使用者能夠設定原則，並執行其他行動裝置應用程式管理工作，請參閱[使用角色指派來管理 Azure 訂用帳戶資源的存取權](https://azure.microsoft.com/documentation/articles/role-based-access-control-configure/)一文。

## <a name="next-steps"></a>後續步驟
[使用 Microsoft Intune 建立及部署應用程式保護原則](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md)


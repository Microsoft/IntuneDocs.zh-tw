---
title: 新增群組來組織使用者和裝置
titleSuffix: Microsoft Intune
description: 依地理位置、部門或硬體特性新增群組來組織使用者和裝置。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 11/20/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f0a2b858-a824-4598-ab81-bdd8e62ac3b3
ms.reviewer: altsou
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 183e8cc5924f6ce1f002225150d808841924e20c
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/20/2020
ms.locfileid: "77514637"
---
# <a name="add-groups-to-organize-users-and-devices"></a>新增群組來組織使用者和裝置

Intune 使用 Azure Active Directory (Azure AD) 群組來管理裝置和使用者。 身為 Intune 管理員，您可以設定群組符合組織的需求。 依地理位置、部門或硬體特性建立群組，來組織使用者或裝置。 使用群組管理大規模的工作。 例如，您可以為許多使用者設定原則，或將應用程式部署到一組裝置。

您可以新增下列群組類型：

- **指派的群組**：將使用者或裝置手動新增至靜態群組。 
- **動態群組** (需要 Azure AD Premium)：根據您建立的運算式，將使用者或裝置自動新增至使用者群組或裝置群組。

  例如，在搭配經理職稱新增某個使用者時，系統會將該使用者自動新增至 [所有經理]  使用者群組。 或者，當裝置具有 iOS/iPadOS 裝置 OS 類型時，系統會將該裝置自動新增至 [所有 iOS/iPadOS 裝置]  裝置群組。

## <a name="add-a-new-group"></a>新增新的群組

使用下列步驟建立新的群組。

1. 登入 [Microsoft 端點管理員系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。
2. 選取 [群組]   > [新增群組]  ：

   ![已選取 [新增群組] 的 Azure 入口網站螢幕擷取畫面](./media/groups-add/groups-add-new.png)

3. 在 [群組類型]  中，請選擇下列其中一個選項：

    - **安全性**：安全性群組能定義可存取資源的人員，且建議用於您 Intune 中的群組。 例如，您可以建立使用者的群組，例如**所有 Charlotte 員工**或**遠端工作者**。 或者，您也可以建立裝置的群組，例如**所有 iOS/iPadOS 裝置**或**所有 Windows 10 學生裝置**。

        > [!TIP]
        > 所建立的使用者和群組也會顯示在 [Microsoft 365 系統管理中心](https://admin.microsoft.com)、Azure Active Directory 管理中心，以及 [Azure 入口網站中的 Microsoft Intune](https://go.microsoft.com/fwlink/?linkid=2090973) 之中。 在您的組織租用戶中，您可以在所有這些區域中建立及管理群組。
        >
        > 如果您的主要角色是裝置管理，我們建議您使用 [Microsoft 端點管理員系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。

    - **Office 365**：透過授與成員存取共用信箱、行事曆、檔案、SharePoint 網站等，來提供共同作業的機會。 此選項也可讓您將群組的存取權授與組織外的人員。 如需詳細資訊，請參閱[了解 Office 365 群組](https://support.office.com/article/learn-about-office-365-groups-b565caa1-5c40-40ef-9915-60fdb2d97fa2)。

4. 為新群組輸入 [群組名稱]  與 [群組描述]  。 請明確描述並包含資訊，使其他人可以知道群組的用途。

    例如，輸入**所有 Windows 10 學生裝置**作為群組名稱，然後輸入**由 Contoso 高中 9-12 年級的學生所使用的所有 Windows 10 裝置**作為群組描述。

5. 輸入 [成員資格類型]  。 選項包括：

    - **已指派**：系統管理員會將使用者或裝置手動指派至此群組，以及手動移除使用者或裝置。
    - **動態使用者**：系統管理員會建立成員資格規則，以自動新增或移除成員。
    - **動態裝置**：系統管理員會建立動態群組規則，以自動新增或移除裝置。

        ![Intune 群組屬性的螢幕擷取畫面](./media/groups-add/groups-add-properties.png)

    如需這些成員資格類型的詳細資訊，以及如何建立動態運算式，請參閱：

    - [使用 Azure AD 建立基本群組並新增成員](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-groups-create-azure-portal)
    - [Azure AD 中群組的動態成員資格規則](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership) \(部分機器翻譯\)

    > [!NOTE]
    > 在此系統管理中心中，當您建立使用者或群組時，您可能不會看到 **Azure Active Directory** 商標。 但那就是您正在使用的服務。

6. 選擇 [建立]  新增新的群組。 您的群組會顯示於清單中。

> [!TIP]
> 您可以考慮一些您可以建立的其他動態使用者和裝置群組，例如：
>
> - Contoso 高中的所有學生
> - 所有 Android Enterprise 裝置
> - 所有 iOS 11 和較舊版本的裝置
> - 行銷
> - 人力資源
> - 所有 Charlotte 員工
> - 所有 WA 員工

## <a name="groups-and-policies"></a>群組和原則

您組織資源的存取權是由您建立的使用者和群組所控制。

當您建立群組時，請考慮您會如何套用[合規性原則](../protect/device-compliance-get-started.md)和[組態設定檔](../configuration/device-profiles.md)。 例如，您可能會有：

- 針對某個裝置作業系統的特定原則。
- 針對您組織中不同角色的特定原則。
- 針對您在 Active Directory 中所定義之組織單位的特定原則。

若要建立您組織的基本合規性需求，您可以建立適用於所有群組和裝置的預設原則。 然後，針對最廣泛的使用者和裝置類別建立更具體的原則。 例如，您可以針對每個裝置作業系統建立電子郵件原則。

如需組態設定檔建議和指引，請參閱[指派原則至使用者群組或裝置群組](../configuration/device-profile-assign.md#user-groups-vs-device-groups)和[設定檔建議](../configuration/device-profile-create.md#recommendations)。

## <a name="see-also"></a>請參閱

- [使用 Microsoft Intune 的角色型存取控制 (RBAC)](role-based-access-control.md)
- [使用 Azure AD 群組來管理資源的存取權](https://docs.microsoft.com/azure/active-directory/active-directory-manage-groups) \(部分機器翻譯\)

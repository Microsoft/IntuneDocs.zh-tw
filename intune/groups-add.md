---
title: 新增群組來組織使用者和裝置
titlesuffix: Microsoft Intune
description: 依地理位置、部門或硬體特性新增群組來組織使用者和裝置。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 06/13/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f0a2b858-a824-4598-ab81-bdd8e62ac3b3
ms.reviewer: amyros
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b6e7d45c4f1c990123e310c8910e9b7bd3cf0ce4
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/02/2019
ms.locfileid: "57235050"
---
# <a name="add-groups-to-organize-users-and-devices"></a>新增群組來組織使用者和裝置
Intune 使用 Azure Active Directory (AD) 群組來管理裝置和使用者。 身為 Intune 管理員，您可以設定群組符合組織的需求。 依地理位置、部門或硬體特性建立群組，來組織使用者或裝置。 使用群組管理大規模的工作。 例如，您可以為許多使用者設定原則，或將應用程式部署到一組裝置。

您可以新增下列群組類型：
- **指派的群組** - 將使用者或裝置手動新增至靜態群組
- **動態群組** - (使用 Azure Active Directory Premium) 讓您動態建置以簡單或進階規則定義的使用者或裝置群組

## <a name="add-a-new-group"></a>新增新的群組

使用下列步驟建立新的群組。
1. 登入 [Azure 入口網站](https://portal.azure.com)。
2. 選擇 [All services] (所有服務) > [Intune]。 Intune 位於 [Monitoring + Management] (監視 + 管理) 區段。
3. 在 [Intune] 窗格中，選擇 [群組]，然後在 [所有群組] 窗格中選擇 [新增群組]。
   ![選取了 [新增群組] 的 Azure 入口網站螢幕擷取畫面](./media/groups-add-new.png)
4. 針對 [群組類型]，請選擇下列其中一個選項：
    - **安全性**：安全性群組是擴展使用者群組時可使用的良好資源。 由於安全性群組會定義誰可存取哪些資源，因此安全性群組可適當轉譯為 Intune 使用者群組。 從 Active Directory 同步處理至 Azure Active Directory 的安全性群組，或者透過 Office 365 系統管理中心或 Azure 入口網站直接在 Azure Active Directory 中建立的安全性群組，都可供您用來在 Intune 中建立使用者群組。
    - **Office 365**

5. 請鍵入新群組的 [名稱]及 [描述]。 這些屬性只會出現在管理入口網站，不會向使用者顯示。

6. 選擇 [成員資格類型]：
   - [已指派] 會建立以手動方式指派成員的群組。 深入了解 [Azure AD 指派的群組](https://docs.microsoft.com/azure/active-directory/active-directory-groups-create-azure-portal)。
   - [動態使用者] 會建立以 [動態查詢] 定義的使用者群組。
   - [動態裝置] 會建立以 [動態查詢] 定義的裝置群組。

   ![Intune 群組屬性的螢幕擷取畫面](./media/groups-add-properties.png)

   Azure AD 讓您根據定義成員資格的規則，建立動態群組。 深入了解[建立以屬性為基礎的動態群組](https://docs.microsoft.com/azure/active-directory/active-directory-groups-dynamic-membership-azure-portal)。

7. 您可以選取 [Enable Office features] (啟用 Office 功能) 讓使用者群組成員存取共用的 Office 365 應用程式。 深入了解 [Office 365 群組](https://support.office.com/article/Learn-about-Office-365-groups-b565caa1-5c40-40ef-9915-60fdb2d97fa2)。
8. 選擇 [建立] 新增新的群組。

## <a name="groups-and-policies"></a>群組和原則

當您建立群組時，請考慮要如何套用[原則](device-compliance-get-started.md)。 例如，您可能會有裝置作業系統特定的原則、您組織中不同角色特定的原則，或您已於 Active Directory 中定義之組織單位特定的原則。 具有適用於 iOS、Android 和 Windows 的個別裝置群組，以及適用於每個組織角色的使用者群組可能會很有用。

您可能也想要建立套用至所有群組和裝置的預設原則，以建立組織的基本相容性需求。 然後，您可以針對最廣泛的使用者和裝置類別建立更具體的原則。 例如，您可以針對每個裝置作業系統建立電子郵件原則。



## <a name="see-also"></a>請參閱
- [利用 Azure Active Directory 群組管理資源的存取權](https://docs.microsoft.com/azure/active-directory/active-directory-manage-groups)
- [Azure 入口網站中的 Intune 傳統群組](groups-get-started.md)

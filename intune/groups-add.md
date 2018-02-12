---
title: "在 Intune 中設定註冊限制"
titlesuffix: Azure portal
description: "在 Intune 中限制不同平台的註冊以及設定裝置註冊限制。 \""
keywords: 
author: arob98
ms.author: angrobe
manager: dougeby
ms.date: 10/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f0a2b858-a824-4598-ab81-bdd8e62ac3b3
ms.reviewer: amyros
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 5e55a96ee1bee5b1f25a4ddf3366f3e7dc94122a
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2018
---
# <a name="add-groups-in-intune"></a>在 Intune 中新增群組
Intune 使用 Azure Active Directory (AD) 群組來管理裝置和使用者。 身為 Intune 管理員，您可以設定群組符合組織的需求。 依地理位置、部門或硬體特性建立群組，來組織使用者或裝置。 使用群組管理大規模的工作。 例如，您可以為許多使用者設定原則，或將應用程式部署到一組裝置。

本主題說明如何新增群組供在 Intune 中使用。

您可以新增下列群組類型：
- **指派的群組** - 將使用者或裝置手動新增至靜態群組
- **動態群組** - (使用 Azure Active Directory Premium) 讓您動態建置以簡單或進階規則定義的使用者或裝置群組

## <a name="add-a-new-group"></a>新增新的群組

使用下列步驟建立新的群組。
1. 在 Azure 入口網站中，移至 [群組]，然後在 [所有群組] 刀鋒視窗中選擇 [新增群組]。
  ![選取了 [新增群組] 的 Azure 入口網站螢幕擷取畫面](./media/groups-add-new.png)
2. 指定新群組的 [名稱] 和 [描述]。 這些屬性只會出現在管理入口網站，不會向使用者顯示。

3. 選擇 [成員資格類型]：
  - [已指派] 會建立以手動方式指派成員的群組。 深入了解 [Azure AD 指派的群組](https://docs.microsoft.com/azure/active-directory/active-directory-groups-create-azure-portal)。
  - [動態使用者] 會建立以 [動態查詢] 定義的使用者群組。
  - [動態裝置] 會建立以 [動態查詢] 定義的裝置群組。

  ![有名稱、描述、成員資格類型、啟用 Office 功能和成員等 Intune 群組屬性的螢幕擷取畫面。](./media/groups-add-properties.png)

  Azure AD 讓您根據定義成員資格的規則，建立動態群組。 深入了解[建立以屬性為基礎的動態群組](https://docs.microsoft.com/azure/active-directory/active-directory-groups-dynamic-membership-azure-portal)。

4. 您可以選取 [Enable Office features] \(啟用 Office 功能) 讓使用者群組成員存取共用的 Office 365 應用程式。 深入了解 [Office 365 群組](https://support.office.com/article/Learn-about-Office-365-groups-b565caa1-5c40-40ef-9915-60fdb2d97fa2)。
5. 選擇 [建立] 新增新的群組。

## <a name="see-also"></a>另請參閱
- [利用 Azure Active Directory 群組管理資源的存取權](https://docs.microsoft.com/azure/active-directory/active-directory-manage-groups)
- [Azure 入口網站中的 Intune 傳統群組](groups-get-started.md)

---
ms.openlocfilehash: 76706fb39c3c5a69cba4fbf3f57c0b58d92e4a27
ms.sourcegitcommit: bccfbf1e3bdc31382189fc4489d337d1a554e6a1
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2019
ms.locfileid: "67559982"
---
<!-- This include is part of the Intune Data Warehouse documentation. -->

## <a name="azure-ad-and-intune-credential-requirements"></a>Azure AD 和 Intune 認證需求

驗證和授權是以 Azure AD 認證和 Intune 角色型存取控制 (RBAC) 為基礎。 租用戶的所有全域管理員和 Intune 服務管理員預設可以存取資料倉儲。 使用 Intune 角色來提供更多使用者的存取權，方法是讓他們存取 **Intune 資料倉儲**資源。

存取 Intune 資料倉儲 (包括應用程式開發介面) 的需求如下：

  - 使用者必須是下列其中一個：
      - Azure AD 全域管理員
      - Intune 服務管理員
      - 對於 **Intune 資料倉儲**資源具有以角色為基礎之存取權的使用者
      - 使用[僅限應用程式驗證](../data-warehouse-app-only-auth.md)的無使用者驗證 

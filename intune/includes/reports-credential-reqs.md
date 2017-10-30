<!-- This include is part of the Intune Data Warehouse documentation. -->

## <a name="azure-ad-and-intune-credential-requirements"></a>Azure AD 和 Intune 認證需求

驗證和授權是以 Azure AD 認證和 Intune 角色型存取控制 (RBAC) 為基礎。 租用戶的所有全域管理員和 Intune 服務管理員預設可以存取資料倉儲。 使用 Intune 角色來提供更多使用者的存取權，方法是讓他們存取**報告資源**。

存取 Intune 資料倉儲 (包括應用程式開發介面) 的需求如下：

  -  必須將 Intune 授權指派給使用者
  -  使用者必須是下列其中一個：
      -  Azure AD 全域管理員
      -  Intune 服務管理員
      -  具有 [報表] 資源之角色型存取權的使用者
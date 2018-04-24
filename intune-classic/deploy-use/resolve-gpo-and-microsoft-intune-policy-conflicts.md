---
title: 解決 GPO 和 Intune 原則衝突
description: 了解如何解決群組原則和 Intune 設定原則之間的衝突。
keywords: ''
author: vhorne
ms.author: victorh
manager: angrobe
ms.date: 12/27/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: e76af5b7-e933-442c-a9d3-3b42c5f5868b
ms.reviewer: owenyen
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: f6d12dd886fe475161e767e63177313a729e170d
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="resolve-group-policy-objects-gpo-and-microsoft-intune-policy-conflicts"></a>解決群組原則物件 (GPO) 和 Microsoft Intune 原則衝突

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Intune 使用原則協助您在的 Windows 電腦上管理設定。 例如，您可以使用原則來控制電腦上的 Windows 防火牆設定。 許多 Intune 設定與您透過 Windows 群組原則所做的設定很類似。 不過，有時候這兩種方法可能彼此衝突。

發生衝突時，除非電腦無法登入網域，否則網域層級的群組原則將優先於 Intune 原則。 在這種情況下，Intune 原則會套用到用戶端電腦。

## <a name="what-to-do-if-you-are-using-group-policy"></a>使用群組原則時的後續動作
請確定您套用的原則均未受群組原則管理。 您可以使用下列一或多種方法，以協助防止衝突：

-   在安裝 Intune 用戶端之前，將您的電腦移到未套用群組原則設定的 Active Directory 組織單位 (OU)。 若 OU 包含已經在 Intune 中註冊但您不想對其套用群組原則設定的電腦，您也可以在這些 OU 上封鎖群組原則繼承。

-   使用安全性群組篩選將 GPO 限制在不由 Intune 管理的電腦上。

-   停用或移除與 Intune 原則衝突的群組原則物件。

如需 Active Directory 和 Windows 群組原則的詳細資訊，請參閱您的 Windows Server 文件。

## <a name="how-to-filter-existing-gpos-to-avoid-conflicts-with-intune-policy"></a>如何篩選現有 GPO 以避免與 Intune 原則發生衝突
如果您已識別與 Intune 原則衝突的 GPO 設定，您可以使用安全性群組篩選，將這些 GPO 限制在不受 Intune 管理的電腦上。

<!--- ### Use WMI filters
WMI filters selectively apply GPOs to computers that satisfy the conditions of a query. To apply a WMI filter, deploy a WMI class instance to all PCs in the enterprise before you enroll any PCs in the Intune service.

#### To apply WMI filters to a GPO

1.  Create a management object file by copying and pasting the following into a text file, and then saving it to a convenient location as **WIT.mof**. The file contains the WMI class instance that you deploy to PCs that you want to enroll in the Intune service.

    ```
    //Beginning of MOF file.
    #pragma classflags("forceupdate")
    #pragma namespace ("\\\\.\\Root")
    instance of __Namespace
    {
       Name = "WindowsIntune";
    };

    #pragma namespace ("\\\\.\\Root\\WindowsIntune")
    [
       Description("This class defines Microsoft Intune common properties")
    ]
    class WindowsIntune_ManagedNode
    {
       [ read, Description("This defines whether Microsoft Intune Policy is enabled"): DisableOverride ToSubClass ]
       boolean WindowsIntunePolicyEnabled;
       [ read, key, Description("This property defines the version." "Example: 1.0"): ToSubClass ]
       string Version;
    };

    instance of WindowsIntune_ManagedNode
    {
       Version = "1.0";
       WindowsIntunePolicyEnabled = 1;
    };
    ```

2.  Use either a startup script or Group Policy to deploy the file. The following is the deployment command for the startup script. The WMI class instance must be deployed before you enroll client PCs in the Intune service.

    **C:/Windows/System32/Wbem/MOFCOMP &lt;path to MOF file&gt;\wit.mof**

3.  Run either of the following commands to create the WMI filters, depending on whether the GPO you want to filter applies to PCs that are managed by using Intune or to PCs that are not managed by using Intune.

    -   For GPOs that apply to PCs that are not managed by using Intune, use the following:

        ```
        Namespace:root\WindowsIntune
        Query:  SELECT WindowsIntunePolicyEnabled FROM WindowsIntune_ManagedNode WHERE WindowsIntunePolicyEnabled=0
        ```

    -   For GPOs that apply to PCs that are managed by Intune, use the following:

        ```
        Namespace:root\WindowsIntune
        Query:  SELECT WindowsIntunePolicyEnabled FROM WindowsIntune_ManagedNode WHERE WindowsIntunePolicyEnabled=1
        ```

4.  Edit the GPO in the Group Policy Management console to apply the WMI filter that you created in the previous step.

    -   For GPOs that should apply only to PCs that you want to manage by using Intune, apply the filter **WindowsIntunePolicyEnabled=1**.

    -   For GPOs that should apply only to PCs that you do not want to manage by using Intune, apply the filter **WindowsIntunePolicyEnabled=0**.

For more information about how to apply WMI filters in Group Policy, see the blog post [Security Filtering, WMI Filtering, and Item-level Targeting in Group Policy Preferences](http://go.microsoft.com/fwlink/?LinkId=177883). --->


您可以僅將 GPO 套用至所選 GPO 之群組原則管理主控台內 **[安全性篩選]** 區域中指定的安全性群組。 依預設，GPO 會套用至 *[已驗證的使用者]*。

-   在 **[Active Directory 使用者和電腦]** 嵌入式管理單元中，建立包含您不想讓 Intune 管理之電腦和使用者帳戶的新安全性群組。 例如，您可能將群組命名為 *Not In Microsoft Intune*。

-   在群組原則管理主控台中，在選取之 GPO 的 [委派] 索引標籤處，以滑鼠右鍵按一下新的安全性群組，委派適當的 [讀取] 和 [套用群組原則] 權限至安全性群組中的使用者和電腦。 ([進階] 對話方塊提供 [套用群組原則]  權限。)

-   然後，將新的安全性群組篩選器套用至選取的 GPO，並移除 **[已驗證的使用者]** 預設篩選器。

必須隨著 Intune 服務中的註冊情形變化來維護新的安全性群組。

### <a name="see-also"></a>另請參閱
[使用 Microsoft Intune 管理 Windows 電腦](manage-windows-pcs-with-microsoft-intune.md)

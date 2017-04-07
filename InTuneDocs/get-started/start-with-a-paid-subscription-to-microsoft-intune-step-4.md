---
title: "指派 Intune 授權 | Microsoft Docs"
description: "為您的 Intune 訂閱指派授權給使用者"
keywords: 
author: lindavr
ms.author: lindavr
manager: angrobe
ms.date: 03/28/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: bb4314ea-88b5-44d3-92ce-4c6aff0587a4
ms.reviewer: amyro
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: c66226b7fc31f91669c4f4f0693ccbd7c679189f
ms.openlocfilehash: b2fc3a3dc47466313a54d2f6aef6b67dff8d7343
ms.lasthandoff: 03/29/2017


---

# <a name="assign-intune-licenses-to-your-user-accounts"></a>將 Intune 授權指派給您的使用者帳戶

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

無論您手動新增使用者，或是從內部部署 Active Directory 同步處理，您必須先指派 Intune 授權給每位使用者，使用者才能在 Intune 中註冊他們的裝置。

## <a name="assign-an-intune-license-in-the-office-365-admin-center"></a>在 Office 365 系統管理中心指派 Intune 授權

您可以使用 [Office 365 入口網站](http://go.microsoft.com/fwlink/p/?LinkId=698854)手動新增雲端式使用者，並將授權指派給雲端式使用者帳戶，以及從您的內部部署 Active Directory 同步處理至 Azure AD 的帳戶。

1.  使用租用戶系統管理員認證登入 [Office 365 入口網站](http://go.microsoft.com/fwlink/p/?LinkId=698854)，然後選擇 [使用者]  >  [作用中使用者]。

2.  選取您想要指派 Intune 使用者授權的使用者帳戶，然後選擇 [產品授權]  >  [編輯]。

3.  將 [Intune] 或 [Enterprise Mobility + Security] 切換為 [開啟]，然後選擇 [儲存]。

4. 使用者帳戶現在已有使用服務並將裝置註冊接受管理所需的權限。

> [!NOTE]
> 使用者必須先註冊裝置，才會顯示在管理主控台中。 此外，您可以一次選取一組使用者來編輯，可以選取以新增或取代所有選取使用者的授權。

## <a name="use-powershell-to-selectively-manage-ems-user-licenses"></a>使用 PowerShell 來選擇性地管理 EMS 使用者授權
使用 Microsoft Enterprise Mobility + Security (原稱為 Enterprise Mobility Suite) 的組織可能會有一些使用者只需要使用 EMS 套件中的 Azure Active Directory Premium 或 Intune 服務。 您可以使用 [Azure Active Directory PowerShell Cmdlet](https://msdn.microsoft.com/library/jj151815.aspx) 指派一項服務或其中一部分的服務。

若要選擇性地指派 EMS 服務的使用者授權，請在已安裝[適用於 Windows PowerShell 的 Windows Azure Active Directory 模組](https://msdn.microsoft.com/library/jj151815.aspx#bkmk_installmodule)的電腦上，以系統管理員身分開啟 PowerShell。 您可以在本機電腦或 ADFS 伺服器上安裝 PowerShell。

您必須建立只適用於所需服務方案的新授權 SKU 定義。 若要這樣做，請停用您不想要套用的方案。 例如，您可能建立不指派 Intune 授權的授權 SKU 定義。 若要查看可用的服務清單，請輸入︰

    (Get-MsolAccountSku | Where {$_.SkuPartNumber -eq "EMS"}).ServiceStatus

您可以執行下列命令，以排除 Intune 服務方案。 您可以使用相同的方法以擴充到整個安全性群組，也可以使用更細微的篩選器。

**範例 1**<br>
在命令列上建立新的使用者，並指派 EMS 授權，而不啟用授權的 Intune 部分︰

    Connect-MsolService

    New-MsolUser -DisplayName “Test User” -FirstName FName -LastName LName -UserPrincipalName user@<TenantName>.onmicrosoft.com –Department DName -UsageLocation US

    $CustomEMS = New-MsolLicenseOptions -AccountSkuId "<TenantName>:EMS" -DisabledPlans INTUNE_A
    Set-MsolUserLicense -UserPrincipalName user@<TenantName>.onmicrosoft.com -AddLicenses <TenantName>:EMS -LicenseOptions $CustomEMS


驗證：

    (Get-MsolUser -UserPrincipalName "user@<TenantName>.onmicrosoft.com").Licenses.ServiceStatus

**範例 2**<br>
對於已獲指派授權的使用者，停用 EMS 授權的 Intune 部分︰

    Connect-MsolService

    $CustomEMS = New-MsolLicenseOptions -AccountSkuId "<TenantName>:EMS" -DisabledPlans INTUNE_A
    Set-MsolUserLicense -UserPrincipalName user@<TenantName>.onmicrosoft.com -LicenseOptions $CustomEMS

驗證：

    (Get-MsolUser -UserPrincipalName "user@<TenantName>.onmicrosoft.com").Licenses.ServiceStatus

![PoSH-AddLic-Verify](./media/posh-addlic-verify.png)

>[!div class="step-by-step"]

>[&larr;**將使用者同步到 Intune**](.\start-with-a-paid-subscription-to-microsoft-intune-step-2.md)     [**組織使用者與裝置**&rarr;](.\start-with-a-paid-subscription-to-microsoft-intune-step-5.md)  


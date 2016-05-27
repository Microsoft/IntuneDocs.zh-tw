---
# required metadata

title: 管理 Intune 授權 | Microsoft Intune
description:
keywords:
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: bb4314ea-88b5-44d3-92ce-4c6aff0587a4

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# 管理 Intune 授權
使用者必須獲得您的 Intune 訂用帳戶的授權，才能登入來使用此服務或註冊裝置以納入管理。 使用者獲得授權時就成為 [!INCLUDE[wit_firstref](../includes/wit_firstref_md.md)] 使用者群組的成員。 此群組包含擁有使用訂閱的授權的所有使用者。 每個使用者授權支援最多註冊五個裝置

## 如何指派 Intune 授權
從內部部署 Active Directory 同步處理使用者帳戶，或透過帳戶入口網站手動將使用者帳戶新增至雲端服務訂用帳戶時，不會自動指派 Intune 授權給他們。 而是在稍後，Intune 租用戶系統管理員必須從帳戶入口網站編輯使用者帳戶，將授權指派給使用者。

當您的訂用帳戶與相關聯的其他雲端服務共用 Azure AD 時，您也可以存取已新增至這些服務的使用者。 在您將授權指派給這些使用者前，他們沒有使用 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 的授權。

> [!TIP]
> 若指派或撤銷 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 授權的選項已停用，表示您的訂用帳戶可能包含大量授權選項，例如在使用 [Enterprise Mobility Suite](https://www.microsoft.com/en-us/server-cloud/enterprise-mobility/overview.aspx) 時可用的選項。 如需如何指派或撤銷授權的詳細資訊，請參閱授權選項的文件。

## 指派 Intune 使用者授權

您可以使用[!INCLUDE[wit_icp_2](../includes/wit_icp_2_md.md)]手動新增雲端式使用者，並將授權指派給雲端式使用者帳戶，以及從內部部署 Active Directory 同步至 Azure AD 的帳戶。

1.  使用您的租用戶系統管理員認證登入 Intune 帳戶入口網站。

2.  選取您想要指派 Intune 使用者授權的使用者帳戶，並啟用使用者帳戶屬性上的 [Microsoft Intune] 核取方塊。

3.  使用者帳戶現在會加入至 Microsoft Intune 使用者群組，以授權使用者使用此服務並註冊裝置以納入管理。

### 使用 PowerShell 來選擇性地管理 EMS 使用者授權
在使用 Microsoft Enterprise Mobility Suite (EMS) 的組織中，使用者在 EMS 封裝中可能只需要 Azure Active Directory Premium 或 Intune 服務。 您可以使用 [Azure Active Directory PowerShell Cmdlet](https://msdn.microsoft.com/library/jj151815.aspx) 指派一個或一部分服務 

若要選擇性地指派 EMS 服務的使用者授權，請在已安裝[適用於 Windows PowerShell 的 Windows Azure Active Directory 模組](https://msdn.microsoft.com/library/jj151815.aspx#bkmk_installmodule)的電腦上，以系統管理員身分開啟 PowerShell。 您可以在本機電腦或 ADFS 伺服器上安裝 PowerShell。

您必須建立只適用於所需服務方案的新授權 SKU 定義。 若要這樣做，請停用您不想要套用的方案。 例如，您可能建立不指派 Intune 授權的授權 SKU 定義。 若要查看可用的服務清單，請輸入︰
 
    (Get-MsolAccountSku | Where {$_.SkuPartNumber -eq "EMS"}).ServiceStatus 

您可以執行下列命令，以排除 Intune 服務方案。 您可以使用相同的方法以擴充到整個安全性群組，也可以使用更細微的篩選器。 

範例 1

    Connect-MsolService 
        
    New-MsolUser -DisplayName “Test User” -FirstName FName -LastName LName -UserPrincipalName user@<TenantName>.onmicrosoft.com –Department DName -UsageLocation US
    
    $CustomEMS = New-MsolLicenseOptions -AccountSkuId "<TenantName>:EMS" -DisabledPlans INTUNE_A
    Set-MsolUserLicense -UserPrincipalName user@<TenantName>.onmicrosoft.com -AddLicenses <TenantName>:EMS -LicenseOptions $CustomEMS 
    

在命令列上建立新的使用者，並指派 EMS 授權，而不啟用授權的 Intune 部分︰

    (Get-MsolUser -UserPrincipalName "user@<TenantName>.onmicrosoft.com").Licenses.ServiceStatus

驗證：

    Connect-MsolService 
    
    Set-MsolUserLicense -UserPrincipalName user@<TenantName>.onmicrosoft.com -RemoveLicenses IAPProdPartnerTest:EMS
    
    $CustomEMS = New-MsolLicenseOptions -AccountSkuId "<TenantName>:EMS" -DisabledPlans INTUNE_A
    Set-MsolUserLicense -UserPrincipalName user@<TenantName>.onmicrosoft.com -AddLicenses <TenantName>:EMS -LicenseOptions $CustomEMS
 
範例 2
 
    (Get-MsolUser -UserPrincipalName "user@<TenantName>.onmicrosoft.com" .Licenses.ServiceStatus

![對於已獲指派授權的使用者，停用 EMS 授權的 Intune 部分︰](./media/posh-addlic-verify.png)

### 驗證：
PoSH-AddLic-Verify 後續步驟
>恭喜！

>您剛完成 Intune 快速入門指南的步驟 4  


<!--HONumber=May16_HO2-->



---
title: "使用 PowerShell 管理 Intune 授權"
description: "使用 PowerShell 管理 Intune 授權"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 02/14/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d2d31c80-c32c-4315-8271-1b0cf9a1f78a
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: d0bd31c07bb1b09893a065c4041d4fcc5015d72b
ms.sourcegitcommit: 22ab1c6a6bfeb4fef9850d12b29829c3fecbbeed
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/12/2018
---
# <a name="manage-intune-licenses-using-powershell"></a>使用 PowerShell 管理 Intune 授權

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

本主題將告訴系統管理員如何使用 PowerShell 來管理 Intune 使用者授權。

如[管理 Intune 授權](/intune/licenses-assign)所述，您必須先指派一份 Intune 訂閱授權給每位使用者，使用者才能登入使用 Intune 服務或註冊其裝置進行管理。 但使用 Microsoft Enterprise Mobility + Security 的組織可能會有一些使用者只需要使用 EMS 套件中的 Azure Active Directory Premium 或 Intune 服務。 您可以使用 [Azure Active Directory PowerShell Cmdlet](https://msdn.microsoft.com/library/jj151815.aspx) 指派一項服務或其中一部分的服務。

若要選擇性地指派 EMS 服務的使用者授權，請在已安裝[適用於 Windows PowerShell 的 Windows Azure Active Directory 模組](https://msdn.microsoft.com/library/jj151815.aspx#bkmk_installmodule)的電腦上，以系統管理員身分開啟 PowerShell。 您可以在本機電腦或 ADFS 伺服器上安裝 PowerShell。

您必須建立只適用於所需服務方案的新授權 SKU 定義。 若要這樣做，請停用您不想要套用的方案。 例如，您可能建立不指派 Intune 授權的授權 SKU 定義。 若要查看可用的服務清單，請輸入︰

    (Get-MsolAccountSku | Where {$\_.SkuPartNumber -eq "EMS"}).ServiceStatus

您可以執行下列命令，以排除 Intune 服務方案。 您可以使用相同的方法以擴充到整個安全性群組，也可以使用更細微的篩選器。

**範例 1** 在命令列上建立新使用者並在不啟用授權中 Intune 部分的情形下指派 EMS 授權：

    Connect-MsolService

    New-MsolUser -DisplayName “Test User” -FirstName FName -LastName LName -UserPrincipalName user@<TenantName>.onmicrosoft.com –Department DName -UsageLocation US

    $CustomEMS = New-MsolLicenseOptions -AccountSkuId "<TenantName>:EMS" -DisabledPlans INTUNE_A
    Set-MsolUserLicense -UserPrincipalName user@<TenantName>.onmicrosoft.com -AddLicenses <TenantName>:EMS -LicenseOptions $CustomEMS


驗證：

    (Get-MsolUser -UserPrincipalName "user@<TenantName>.onmicrosoft.com").Licenses.ServiceStatus

**範例 2**：為已獲指派授權的使用者，停用 EMS 授權中的 Intune 部分：

    Connect-MsolService

    Set-MsolUserLicense -UserPrincipalName user@<TenantName>.onmicrosoft.com -RemoveLicenses IAPProdPartnerTest:EMS

    $CustomEMS = New-MsolLicenseOptions -AccountSkuId "<TenantName>:EMS" -DisabledPlans INTUNE_A
    Set-MsolUserLicense -UserPrincipalName user@<TenantName>.onmicrosoft.com -AddLicenses <TenantName>:EMS -LicenseOptions $CustomEMS

驗證：

    (Get-MsolUser -UserPrincipalName "user@<TenantName>.onmicrosoft.com" .Licenses.ServiceStatus

![PoSH-AddLic-Verify](./media/posh-addlic-verify.png)

### <a name="next-steps"></a>接下來的步驟
恭喜！ 您剛完成 *Intune 快速入門指南*的步驟 4。
>[!div class="step-by-step"]
(/intune/custom-domain-name-configure) [&larr; **將使用者同步至 Intune**](/intune/custom-domain-name-configure)     [**組織使用者和裝置** &rarr;](.\start-with-a-paid-subscription-to-microsoft-intune-step-5.md)  

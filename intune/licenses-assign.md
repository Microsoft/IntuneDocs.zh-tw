---
title: 指派 Microsoft Intune 授權
description: 將授權指派給使用者，讓使用者可以在 Intune 中註冊
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/31/2017
ms.topic: get-started-article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: bb4314ea-88b5-44d3-92ce-4c6aff0587a4
ms.reviewer: amyro
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 8f37c45945df460dabac60e5b06286c940728ba3
ms.sourcegitcommit: 3c4ea8d6809a63042705b5ed4f25ba80f522070e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/11/2018
ms.locfileid: "34051635"
---
# <a name="assign-licenses-to-users-so-they-can-enroll-devices-in-intune"></a>將授權指派給使用者，讓使用者可以在 Intune 中註冊裝置

[!INCLUDE [both-portals](./includes/note-for-both-portals.md)]

無論您手動新增使用者，或是從內部部署 Active Directory 同步處理，您必須先指派 Intune 授權給每位使用者，使用者才能在 Intune 中註冊他們的裝置。 如需授權清單，請參閱[包含 Intune 的授權](licenses.md)。

## <a name="assign-an-intune-license-in-the-office-365-admin-center"></a>在 Office 365 系統管理中心指派 Intune 授權

您可以使用 [Office 365 入口網站](http://go.microsoft.com/fwlink/p/?LinkId=698854)手動新增雲端式使用者，並將授權指派給雲端式使用者帳戶，以及從您的內部部署 Active Directory 同步處理至 Azure AD 的帳戶。

1. 使用租用戶系統管理員認證登入 [Office 365 入口網站](http://go.microsoft.com/fwlink/p/?LinkId=698854)，然後選擇 [使用者]  >  [作用中使用者]。

2. 選取您想要指派 Intune 使用者授權的使用者帳戶，然後選擇 [產品授權]  >  [編輯]。

3. 將 [Intune] 或 [Enterprise Mobility + Security] 切換為 [開啟]，然後選擇 [儲存]。

   ![Office 365 入口網站產品授權區段的螢幕擷取畫面。](./media/office-assign-license.png)

4. 使用者帳戶現在已有使用服務並將裝置註冊接受管理所需的權限。

> [!NOTE]
> 使用者必須先註冊裝置，才會顯示在管理主控台中。 此外，您可以一次選取一組使用者來編輯，可以選取以新增或取代所有選取使用者的授權。

## <a name="assign-an-intune-license-by-using-azure-active-directory"></a>使用 Azure Active Directory 指派 Intune 授權

您也可以使用 Azure Active Directory，將 Intune 授權指派給使用者。 如需詳細資訊，請參閱 [Azure Active Directory 中的授權使用者](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-licensing-group-assignment-azure-portal)一文。 

## <a name="use-school-data-sync-to-assign-licenses-to-users-in-intune-for-education"></a>使用「學校資料同步處理」將授權指派給 Intune 教育版中的使用者
如果您是教育組織，則可以使用「學校資料同步處理」(SDS) 將 Intune 教育版授權指派給同步的使用者。 只要在設定 SDS 設定檔時，選取 [Intune 教育版] 核取方塊即可。  

![SDS 設定檔設定的螢幕擷取畫面](./media/i4e-sds-profile-setup-setting.png)

當您指派 Intune 教育版授權時，請務必一併指派 Intune A Direct 授權。

![產品授權設定的螢幕擷取畫面](./media/i4e-set-licenses.png)

若要深入了解 SDS，請參閱此[學校資料同步處理概觀](https://support.office.com/article/Overview-of-School-Data-Sync-and-Classroom-f3d1147b-4ade-4905-8518-508e729f2e91)。

## <a name="how-user-and-device-licenses-affect-access-to-services"></a>使用者和裝置授權如何影響對服務的存取
* 您指派軟體授權的每個**使用者**，都可以存取及使用線上服務和相關軟體 (包括 System Center 軟體)，以管理應用程式和最多 15 個裝置。
* 您指派裝置軟體授權的每個**裝置**，都可以存取及使用線上服務和相關軟體 (包括 System Center 軟體)，以供任何數目的使用者使用。
* 如果裝置是由多個使用者使用，每個使用者都需要一個裝置軟體授權，或者所有使用者需要一個使用者軟體授權。

## <a name="understanding-the-type-of-licenses-you-have-purchased"></a>了解您已購買的授權類型

Intune 的購買方式決定訂用帳戶資訊：

- 如果您透過 Enterprise 合約購買 Intune，則可以在大量授權入口網站的 [訂用帳戶] 下找到訂用帳戶資訊。
- 如果您透過雲端解決方案提供者購買 Intune，則請洽詢您的轉售商。
- 如果您使用 CC# 或 Invoice 購買 Intune，則授權會以使用者為基礎。




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

---
title: 使用 Microsoft Intune 設定 Windows 裝置的註冊
titleSuffix: ''
description: 設定 Windows 裝置的註冊。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/05/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f94dbc2e-a855-487e-af6e-8d08fabe6c3d
ms.reviewer: spshumwa
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: add92c038e33ba1b5873eb0e9588242f8f3d0f57
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/19/2019
ms.locfileid: "75207429"
---
# <a name="set-up-enrollment-for-windows-devices"></a>設定 Windows 裝置的註冊

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

本文將協助 IT 管理員為其使用者簡化 Windows 註冊。 一旦您[設定 Intune](../fundamentals/setup-steps.md)，使用者以其工作或學校帳戶[登入](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-windows)即可註冊 Windows 裝置。  

身為 Intune 系統管理員，您可以用下列方式來簡化註冊：

- [啟用自動註冊](#enable-windows-10-automatic-enrollment) (需要 Azure AD Premium)
- [CNAME 註冊](#simplify-windows-enrollment-without-azure-ad-premium)
- [啟用大量註冊](../windows-bulk-enroll.md) (需要 Azure AD Premium 與 Windows 設定設計工具)

有兩個因素會決定如何簡化 Windows 裝置註冊：

- **您是否有使用 Azure Active Directory Premium？** <br>[Azure AD Premium](https://docs.microsoft.com/azure/active-directory/active-directory-get-started-premium) 包含在企業行動力 + 安全性和其他授權計劃中。
- **使用者會註冊哪些版本的 Windows 用戶端？** <br>加入工作或學校帳戶即可自動註冊 Windows 10 裝置。 較舊版本則必須使用公司入口網站應用程式進行註冊。

||**Azure AD Premium**|**其他 AD**|
|----------|---------------|---------------|  
|**Windows 10**|[自動註冊](#enable-windows-10-automatic-enrollment) |使用者註冊|
|**舊版 Windows**|使用者註冊|使用者註冊|

可以使用自動註冊的組織，也可以使用 Windows 設定設計工具應用程式來設定[大量註冊裝置](../windows-bulk-enroll.md)。

## <a name="device-enrollment-prerequisites"></a>裝置註冊先決條件

您必須先將授權指派給系統管理員的帳戶，該系統管理員才能向 Intune 註冊裝置以進行管理。 [閱讀如何指派裝置註冊的授權](../fundamentals/licenses-assign.md)

## <a name="multi-user-support"></a>多重使用者的支援

Intune 在下列兩種裝置上可支援多個使用者：

- 執行 Windows 10 Creator 的更新
- 已加入 Azure Active Directory 網域。

當標準使用者使用其 Azure AD 認證登入時，他們會收到指派給其使用者名稱的應用程式和原則。 只有裝置的[主要使用者](../remote-actions/find-primary-user.md)可以針對自助服務案例使用公司入口網站，例如，安裝應用程式及執行裝置動作 (移除、重設)。 針對未獲指派主要使用者的共用 Windows 10 裝置，公司入口網站仍可用來安裝可用的應用程式。

[!INCLUDE [AAD-enrollment](../includes/win10-automatic-enrollment-aad.md)]

## <a name="simplify-windows-enrollment-without-azure-ad-premium"></a>在沒有 Azure AD Premium 的情況下簡化 Windows 註冊
若要簡化註冊，請建立網域名稱伺服器 (DNS) 別名 (CNAME 記錄類型)，將註冊要求重新導向至 Intune 伺服器。 否則，嘗試連線至 Intune 的使用者必須在註冊期間輸入 Intune 伺服器名稱。

**步驟 1：建立 CNAME** (選用)<br>
建立公司網域的 CNAME DNS 資源記錄。 例如，假設公司網站為 contoso.com，您就必須在 DNS 中建立 CNAME，將 EnterpriseEnrollment.contoso.com 重新導向 enterpriseenrollment-s.manage.microsoft.com。

雖然建立 CNAME DNS 項目並非必要，但 CNAME 記錄可以方便使用者進行註冊。 若找不到任何 CNAME 記錄，將會提示使用者手動輸入 MDM 伺服器名稱 enrollment.manage.microsoft.com。

|類型|主機名稱|指向|TTL|
|----------|---------------|---------------|---|
|CNAME|EnterpriseEnrollment.company_domain.com|EnterpriseEnrollment-s.manage.microsoft.com| 1 小時|
|CNAME|EnterpriseRegistration.company_domain.com|EnterpriseRegistration.windows.net|1 小時|

如果公司使用多個 UPN 尾碼，您需要為每個網域名稱建立一個 CNAME，並將其一一指向至 EnterpriseEnrollment-s.manage.microsoft.com。 例如，Contoso 上的使用者使用下列格式作為其電子郵件/UPN：

- name@contoso.com
- name@us.contoso.com
- name@eu.contoso.com

Contoso DNS 系統管理員應該建立下列 CNAME：

|類型|主機名稱|指向|TTL|  
|----------|---------------|---------------|---|
|CNAME|EnterpriseEnrollment.contoso.com|EnterpriseEnrollment-s.manage.microsoft.com|1 小時|
|CNAME|EnterpriseEnrollment.us.contoso.com|EnterpriseEnrollment-s.manage.microsoft.com|1 小時|
|CNAME|EnterpriseEnrollment.eu.contoso.com|EnterpriseEnrollment-s.manage.microsoft.com| 1 小時|

`EnterpriseEnrollment-s.manage.microsoft.com` - 支援從電子郵件的網域名稱辨識網域，重新導向至 Intune 服務

DNS 記錄變更可能需要 72 小時才會傳播完成。 在 DNS 記錄傳播完成之前，您無法在 Intune 中驗證 DNS 變更。

## <a name="additional-endpoints-are-supported-but-not-recommended"></a>支援但不建議使用其他端點
EnterpriseEnrollment-s.manage.microsoft.com 是註冊慣用的 FQDN；但在過去，客戶還會使用其他兩個支援的端點。 EnterpriseEnrollment.manage.microsoft.com (沒有 -s) 和 manage.microsoft.com 會作為自動探索伺服器的目標，但使用者必須在確認訊息上觸控 [確定]。 如果您指向 EnterpriseEnrollment-s.manage.microsoft.com，使用者就不必執行其他確認步驟，因此這是建議的設定

## <a name="alternate-methods-of-redirection-are-not-supported"></a>不支援重新導向的替代方法
不支援使用 CNAME 設定以外的方法。 例如，不支援使用 Proxy 伺服器將 enterpriseenrollment.contoso.com/EnrollmentServer/Discovery.svc 重新導向至 enterpriseenrollment-s.manage.microsoft.com/EnrollmentServer/Discovery.svc 或 manage.microsoft.com/EnrollmentServer/Discovery.svc。

**步驟 2：驗證 CNAME** (選用)<br>
1. 在 [Microsoft 端點管理員系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)中，選擇 [裝置]   > [Windows]   > [Windows 註冊]   > [CNAME 驗證]  。
2. 在 [網域]  方塊中輸入公司網站，然後選擇 [測試]  。

## <a name="tell-users-how-to-enroll-windows-devices"></a>告訴使用者如何註冊 Windows 裝置
告訴使用者如何註冊其 Windows 裝置，以及開始管理之後會發生的情況。

> [!NOTE]
> 使用者必須透過 Microsoft Edge 存取公司入口網站，檢視針對特定 Windows 版本指派的 Windows 應用程式。 其他瀏覽器，包括 Google Chrome、Mozilla Firefox 和 Internet Explorer 均不支援這種篩選。

如需使用者註冊指示，請參閱[在 Intune 註冊 Windows 裝置](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-windows)。 您也可以告訴使用者檢閱[我的 IT 系統管理員可以在我的裝置上看到哪些資訊](https://docs.microsoft.com/intune-user-help/what-can-your-it-administrator-see-when-you-enroll-your-device-in-intune-windows)。

>[!IMPORTANT]
> 如果您未啟用 Auto-MDM 註冊，但您的 Windows 10 裝置已加入至 Azure AD，則會在註冊之後於 Intune 主控台中顯示兩筆記錄。 停止方式是使用相同的帳戶確定具有加入 Azure AD 之裝置的使用者移至 [帳戶]   > [Access work or school] (存取工作或學校)  和 [連線]  。 

如需終端使用者工作的詳細資訊，請參閱[使用 Microsoft Intune 之使用者體驗的相關資源](../fundamentals/end-user-educate.md)。

## <a name="registration-and-enrollment-cnames"></a>登錄和註冊 CNAME
Azure Active Directory 使用不同的 CNAME 註冊 iOS、Android 和 Windows 裝置。 Intune 條件式存取要求裝置必須註冊，也稱為「已加入工作場所」。 如果打算使用條件式存取，您也應該為所擁有的每個公司名稱設定 EnterpriseRegistration CNAME。

| 類型 | 主機名稱 | 指向 | TTL |
| --- | --- | --- | --- |
| 名稱 | EnterpriseRegistration. company_domain.com | EnterpriseRegistration.windows.net | 1 小時|

如需裝置註冊的詳細資訊，請參閱 [Manage device identities using the Azure portal](https://docs.microsoft.com/azure/active-directory/devices/device-management-azure-portal) (使用 Azure 入口網站管理裝置身分識別)

## <a name="windows-10-auto-enrollment-and-device-registration"></a>Windows 10 自動註冊和裝置註冊

此節適用於美國政府雲端客戶。

雖然建立 CNAME DNS 項目並非必要，但 CNAME 記錄可以方便使用者進行註冊。 若找不到任何註冊 CNAME 記錄，將會提示使用者手動輸入 MDM 伺服器名稱 enrollment.manage.microsoft.tw。

| 類型 | 主機名稱 | 指向 | TTL |
| --- | --- | --- | --- |
| CNAME | EnterpriseEnrollment.company_domain.com | EnterpriseEnrollment-s.manage.microsoft.tw | 1 小時|
|CNAME | EnterpriseRegistration.company_domain.com | EnterpriseRegistration.windows.net | 1 小時 |


## <a name="next-steps"></a>後續步驟

- [在 Azure 上使用 Intune 管理 Windows 裝置時的考量](../fundamentals/intune-legacy-pc-client.md)。

---
title: "註冊 Windows 裝置"
titleSuffix: Intune Azure preview
description: "Intune Azure 預覽版︰啟用 Windows 裝置的 Intune 行動裝置管理 (MDM)。"
keywords: 
author: nathbarn
manager: nathbarn
ms.date: 04/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f94dbc2e-a855-487e-af6e-8d08fabe6c3d
ms.reviewer: damionw
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: e5dd7cb5b320df7f443b52a1b502027fa3c4acaf
ms.openlocfilehash: 3c764b269916ae1a9b076617842eb26d7fd13bab
ms.lasthandoff: 04/19/2017


---

# <a name="enroll-windows-devices"></a>註冊 Windows 裝置

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

本主題將協助 IT 系統管理員為其使用者簡化 Windows 註冊。  不需要任何額外的步驟即可註冊 Windows 裝置，但您可以讓使用者更容易註冊。

Intune 的多使用者管理現在支援執行 Windows 10 Creators Update 並加入 Azure Active Directory 網域的裝置。 這表示當不同的標準使用者使用其 Azure AD 認證登入裝置時，將會收到指派給其使用者名稱的任何應用程式和原則。 針對安裝應用程式等自助式案例，使用者目前無法使用公司入口網站來進行。

有兩個因素會決定如何簡化 Windows 裝置註冊：

- **您是否使用 Azure Active Directory Premium？** <br>[Azure AD Premium](https://docs.microsoft.com/azure/active-directory/active-directory-get-started-premium) 隨附於企業行動力 + 安全性和其他授權計劃內。
- **哪些版本的 Windows 用戶端會進行註冊？** <br>加入工作或學校帳戶即可自動註冊 Windows 10 裝置。 較舊版本則必須使用公司入口網站應用程式進行註冊。

||**Azure AD Premium**|**其他 AD**|
|----------|---------------|---------------|  
|**Windows 10**|[自動註冊](#enable-windows-10-automatic-enrollment) |[使用者註冊](#enable-windows-enrollment-without-azure-ad-premium)|
|**舊版 Windows**|[使用者註冊](#enable-windows-enrollment-without-azure-ad-premium)|[使用者註冊](#enable-windows-enrollment-without-azure-ad-premium)|

[!INCLUDE[AAD-enrollment](../includes/win10-automatic-enrollment-aad.md)]

## <a name="enable-windows-enrollment-without-azure-ad-premium"></a>不使用 Azure AD Premium 啟用 Windows 註冊
您可以讓使用者註冊其裝置，而不用 Azure AD Premium 自動註冊。 一旦您指派授權，使用者就可以在將其工作帳戶新增至其個人擁有的裝置，或將其公司擁有的裝置加入您的 Azure AD 之後進行註冊。 建立 DNS 別名 (CNAME 記錄類型) 可讓使用者更輕鬆地註冊裝置。 如果您建立 DNS CNAME 資源記錄，使用者會在 Intune 中進行連線和註冊，而不需要輸入 Intune 伺服器名稱。

**步驟 1：建立 CNAME** (選用)<br>
建立公司網域的 CNAME DNS 資源記錄。 例如，假設公司網站為 contoso.com，您就必須在 DNS 中建立 CNAME，將 EnterpriseEnrollment.contoso.com 重新導向 enterpriseenrollment-s.manage.microsoft.com。

雖然建立 CNAME DNS 項目並非必要，但 CNAME 記錄可以方便使用者進行註冊。 若找不到任何 CNAME 記錄，將會提示使用者手動輸入 MDM 伺服器名稱 enrollment.manage.microsoft.com。

|類型|主機名稱|指向|TTL|  
|----------|---------------|---------------|---|
|CNAME|EnterpriseEnrollment.company_domain.com|EnterpriseEnrollment-s.manage.microsoft.com| 1 小時|

如果您有多個 UPN 尾碼，您需要為每個網域名稱建立一個 CNAME，並將其一一指向至 EnterpriseEnrollment-s.manage.microsoft.com。 例如，如果 Contoso 上的使用者使用 name@contoso.com，但也使用 name@us.contoso.com 和 name@eu.constoso.com 作為他們的電子郵件/UPN，Contoso DNS 系統管理員就必須建立下列 CNAME。

|類型|主機名稱|指向|TTL|  
|----------|---------------|---------------|---|
|CNAME|EnterpriseEnrollment.contoso.com|EnterpriseEnrollment-s.manage.microsoft.com|1 小時|
|CNAME|EnterpriseEnrollment.us.contoso.com|EnterpriseEnrollment-s.manage.microsoft.com|1 小時|
|CNAME|EnterpriseEnrollment.eu.contoso.com|EnterpriseEnrollment-s.manage.microsoft.com| 1 小時|

`EnterpriseEnrollment-s.manage.microsoft.com` – 支援從電子郵件的網域名稱辨識網域，重新導向至 Intune 服務

DNS 記錄變更可能需要 72 小時才會傳播完成。 在 DNS 記錄傳播完成之前，您無法在 Intune 中驗證 DNS 變更。

**步驟 2：驗證 CNAME** (選用)<br>
在 Azure Intune 入口網站中，選擇 [更多服務] > [監視 + 管理] > [Intune]。 在 [Intune] 刀鋒視窗中，選擇 [註冊裝置]  >  [Windows 註冊]。 在 [指定已驗證的網域名稱] 方塊中輸入公司網站中已驗證網域的 URL，然後選擇 [測試自動偵測]。

## <a name="tell-users-how-to-enroll-windows-devices"></a>告訴使用者如何註冊 Windows 裝置
告訴使用者如何註冊其 Windows 裝置，以及開始管理之後會發生的情況。 如需使用者註冊指示，請參閱[在 Intune 註冊 Windows 裝置](https://docs.microsoft.com/intune/enduser/enroll-your-device-in-intune-windows)。 您也可以告訴使用者[我的 IT 系統管理員可以在我的裝置上看到哪些資訊](https://docs.microsoft.com/intune/enduser/what-can-your-it-administrator-see-when-you-enroll-your-device-in-intune-windows)。

如需終端使用者工作的詳細資訊，請參閱[使用 Microsoft Intune 之使用者體驗的相關資源](https://docs.microsoft.com/intune/deploy-use/how-to-educate-your-end-users-about-microsoft-intune)。


---
title: "使用 Microsoft Intune 設定 Windows 裝置管理"
description: "為 Microsoft Intune 的 Windows 裝置啟用行動裝置管理 (MDM)。"
keywords: 
author: NathBarn
manager: angrobe
ms.date: 03/20/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9a18c0fe-9f03-4e84-a4d0-b63821bf5d25
ms.reviewer: damionw
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 9066414bcef1ba312db64aef077db8f8bfbbdb44
ms.sourcegitcommit: 79116d4c7f11bafc7c444fc9f5af80fa0b21224e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/03/2017
---
# <a name="set-up-windows-device-management"></a>設定 Windows 裝置管理

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

本主題將協助 IT 系統管理員為其使用者簡化 Windows 註冊。  不需要任何額外的步驟即可註冊 Windows 裝置，但您可以讓使用者更容易註冊。

有兩個因素會決定如何簡化 Windows 裝置註冊：
- **您是否使用 Azure Active Directory Premium？** <br>[Azure AD Premium](https://docs.microsoft.com/azure/active-directory/active-directory-get-started-premium) 隨附於企業行動力 + 安全性和其他授權計劃內。
- **哪些版本的 Windows 用戶端會進行註冊？** <br>加入工作或學校帳戶即可自動註冊 Windows 10 裝置。 較舊版本則必須使用公司入口網站應用程式進行註冊。

||**Azure AD Premium**|**其他 AD**|
|----------|---------------|---------------|  
|**Windows 10**|[自動註冊](#enable-windows-10-automatic-enrollment) |[使用者註冊](#enable-windows-enrollment-without-automatic-enrollment)|
|**舊版 Windows**|[使用者註冊](#enable-windows-enrollment-without-automatic-enrollment)|[使用者註冊](#enable-windows-enrollment-without-automatic-enrollment)|

[!INCLUDE[AAD-enrollment](../includes/win10-automatic-enrollment-aad.md)]

## <a name="enable-windows-enrollment-without-automatic-enrollment"></a>啟用不使用自動註冊的 Windows 註冊
您可以讓使用者註冊其裝置，而不用 Azure AD Premium 自動註冊。 一旦您指派授權，使用者就可以在將其工作帳戶新增至其個人擁有的裝置，或將其公司擁有的裝置加入您的 Azure AD 之後進行註冊。 建立 DNS 別名 (CNAME 記錄類型) 可讓使用者更輕鬆地註冊裝置。 如果您建立 DNS CNAME 資源記錄，使用者會在 Intune 中進行連線和註冊，而不需要輸入 Intune 伺服器名稱。

**步驟 1：建立 CNAME** (選用)<br>
建立公司網域的 CNAME DNS 資源記錄。 例如，假設公司網站為 contoso.com，您就必須在 DNS 中建立 CNAME，將 EnterpriseEnrollment.contoso.com 重新導向 enterpriseenrollment-s.manage.microsoft.com。

雖然建立 CNAME DNS 項目並非必要，但 CNAME 記錄可以方便使用者進行註冊。 若找不到任何註冊 CNAME 記錄，會提示使用者手動輸入下列 MDM 伺服器名稱：enrollment.manage.microsoft.com。

如果已驗證的網域不止一個，請為每個網域建立一筆 CNAME 記錄。 CNAME 資源記錄必須包含下列資訊：

CNAME 資源記錄必須具有下列資訊：

|類型|主機名稱|指向|TTL|
|--------|-------------|-------------|-------|
|CNAME|EnterpriseEnrollment.company_domain.com|EnterpriseEnrollment-s.manage.microsoft.com |1 小時|
|CNAME|EnterpriseRegistration.company_domain.com|EnterpriseRegistration.windows.net|1 小時|

`EnterpriseEnrollment-s.manage.microsoft.com` – 支援從電子郵件的網域名稱辨識網域，重新導向至 Intune 服務

如果您的公司對使用者認證使用多個網域，請為每個網域建立 CNAME 記錄。

例如，假設公司網站為 contoso.com，您就必須在 DNS 中建立 CNAME，將 EnterpriseEnrollment.contoso.com 重新導向 EnterpriseEnrollment-s.manage.microsoft.com。 DNS 記錄變更可能需要 72 小時才會傳播完成。 在 DNS 記錄傳播完成之前，您無法在 Intune 中驗證 DNS 變更。

**步驟 2：驗證 CNAME** (選用)<br>
在 [Intune 管理主控台](https://manage.microsoft.com)中，選擇 [管理] &gt; [行動裝置管理] &gt; [Windows]。 在 [指定已驗證的網域名稱] 方塊中輸入公司網站中已驗證網域的 URL，然後選擇 [測試自動偵測]。

## <a name="tell-users-how-to-enroll-windows-devices"></a>告訴使用者如何註冊 Windows 裝置
告訴使用者如何註冊其 Windows 裝置，以及開始管理之後會發生的情況。
如需使用者註冊指示，請參閱[在 Intune 註冊 Windows 裝置](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-windows)。 您也可以將使用者送往[我的 IT 系統管理員可以在我的裝置上看到哪些資訊](https://docs.microsoft.com/intune-user-help/what-can-your-it-administrator-see-when-you-enroll-your-device-in-intune-windows)。

如需終端使用者工作的詳細資訊，請參閱[使用 Microsoft Intune 之使用者體驗的相關資源](/intune/end-user-educate)。

### <a name="see-also"></a>請參閱
[Microsoft Intune 中註冊裝置的必要條件](prerequisites-for-enrollment.md)

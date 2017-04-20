---
title: "使用 Microsoft Intune 設定 Windows 裝置管理 | Microsoft Docs"
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
translationtype: Human Translation
ms.sourcegitcommit: 771aed4e1c57171183b9a9ea7d9e0f702dc1859c
ms.openlocfilehash: f6014c5500b05762d123b2285ef859d67382e402
ms.lasthandoff: 04/06/2017


---

# <a name="set-up-windows-device-management"></a>設定 Windows 裝置管理

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

使用下列其中一種方法設定 Windows 裝置註冊︰

- [**使用 Azure Active Directory Premium 自動註冊 Windows 10**](#set-up-windows-10-and-windows-10-mobile-automatic-enrollment-with-azure-active-directory-premium)
 -  這個方法僅適用於 Windows 10 裝置。
 -  您必須擁有 Azure Active Directory Premium 才能使用此方法。
 -  若選擇不啟用自動註冊，請使用 Windows 8.1 及 Windows Phone 8.1 適用的註冊方法。

- [**不使用 Azure AD Premium 自動註冊進行註冊**](#enable-windows-enrollment-without-azure-ad-premium)
 - 若要註冊 Windows 8.1 及 Windows Phone 8.1 裝置，必須使用此方法。
 - 如果您不打算使用 Azure Active Directory (AD) Premium，您可以針對 Windows 8.1 及更新的裝置使用此方法。

[!INCLUDE[AAD-enrollment](../includes/win10-automatic-enrollment-aad.md)]

## <a name="enable-windows-enrollment-without-automatic-enrollment"></a>啟用不使用自動註冊的 Windows 註冊
您可以讓使用者安裝及註冊其裝置，而不用 Azure AD Premium 自動註冊。 當您將授權指派給使用者的帳戶之後，使用者就可以將該帳戶新增至 Windows 裝置，並同意註冊管理中的裝置。 如果您建立 DNS CNAME 資源記錄，使用者會連線並註冊 Intune，而不需要輸入伺服器名稱。

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
在 [Intune 管理主控台](http://manage.microsoft.com)中，選擇 [管理] &gt; [行動裝置管理] &gt; [Windows]。 在 [指定已驗證的網域名稱] 方塊中輸入公司網站中已驗證網域的 URL，然後選擇 [測試自動偵測]。

## <a name="tell-users-how-to-enroll-windows-devices"></a>告訴使用者如何註冊 Windows 裝置
告訴使用者如何註冊其 Windows 裝置，以及開始管理之後會發生的情況。
如需使用者註冊指示，請參閱[在 Intune 註冊 Windows 裝置](https://docs.microsoft.com/intune/enduser/enroll-your-device-in-intune-windows)。 您也可以將使用者送往[我的 IT 系統管理員可以在我的裝置上看到哪些資訊](https://docs.microsoft.com/intune/enduser/what-can-your-it-administrator-see-when-you-enroll-your-device-in-intune-windows)。

如需終端使用者工作的詳細資訊，請參閱[使用 Microsoft Intune 之使用者體驗的相關資源](https://docs.microsoft.com/intune/deploy-use/how-to-educate-your-end-users-about-microsoft-intune)。

### <a name="see-also"></a>請參閱
[Microsoft Intune 中註冊裝置的必要條件](prerequisites-for-enrollment.md)


---
title: "註冊 Windows 裝置"
titleSuffix: Intune Azure preview
description: "Intune Azure 預覽版︰啟用 Windows 裝置的 Intune 行動裝置管理 (MDM)。"
keywords: 
author: nathbarn
manager: nathbarn
ms.date: 03/15/17
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f94dbc2e-a855-487e-af6e-8d08fabe6c3d
ms.reviewer: damionw
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: a95aca706a4996d40e268a80c7c334ebb9854df5
ms.openlocfilehash: 6cbaf8414452f11f0aa97616bbed2cf164b49ac0
ms.lasthandoff: 03/15/2017


---

# <a name="enroll-windows-devices"></a>註冊 Windows 裝置

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

使用下列其中一種方法設定 Windows 裝置註冊︰

- [**自動向 Azure Active Directory Premium 註冊 Windows 10 及 Windows 10 行動裝置版**](#set-up-windows-10-and-windows-10-mobile-automatic-enrollment-with-azure-active-directory-premium)
 -  此方法僅用於 Windows 10 裝置與 Windows 10 行動裝置版裝置。
 -  您必須擁有 Azure Active Directory Premium 才能使用此方法。 否則，請使用 Windows 8.1 及 Windows Phone 8.1 適用的註冊方法。
 -  若選擇不啟用自動註冊，請使用 Windows 8.1 及 Windows Phone 8.1 適用的註冊方法。

- [**透過設定 CNAME 來註冊 Windows 8.1 及 Windows Phone 8.1**](#simplify-enrollment-by-configuring-cname)
 - 若要註冊 Windows 8.1 及 Windows Phone 8.1 裝置，必須使用此方法。
 - 如果您沒有 Azure Active Directory (AD) Premium，也可以使用此方法。


## <a name="prerequisites"></a>必要條件

如果某些下列必要條件尚未在 Intune Azure 預覽版中，則您必須從傳統 Intune 管理主控台進行。

- [設定自訂網域名稱](https://docs.microsoft.com/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-2)
- [將行動裝置管理 (MDM) 授權單位](set-mdm-authority.md)設定為 **Microsoft Intune**
- [設定公司入口網站應用程式](/intune-azure/manage-apps/company-portal-app.md)
- 將授權指派給使用者

[!INCLUDE[AAD-enrollment](../includes/win10-automatic-enrollment-aad.md)]

## <a name="enable-windows-workplace-enrollment"></a>啟用 Windows 工作場所註冊

您可以讓使用者安裝及註冊其裝置，而不用 Azure AD Premium 自動註冊。 如果您建立 DNS CNAME 資源記錄，使用者會連線並註冊 Intune，而不需要輸入伺服器名稱。

1. **建立 CNAME** (選用)<br>
 建立公司網域的 **CNAME** DNS 資源記錄。 例如，假設公司網站為 contoso.com，您就必須在 DNS 中建立 CNAME，將 EnterpriseEnrollment.contoso.com 重新導向 enterpriseenrollment-s.manage.microsoft.com。

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

2.  **驗證 CNAME**<br>在 Azure 入口網站中，選擇 [更多服務] > [監視 + 管理] > [Intune]。 在 [Intune] 刀鋒視窗中，選擇 [註冊裝置]  >  [Windows 註冊]。 在 [指定已驗證的網域名稱] 方塊中輸入公司網站中已驗證網域的 URL，然後選擇 [測試自動偵測]。

3.  **告訴使用者如何註冊其裝置，以及開始管理之後其裝置會有什麼情況。**

    如需使用者註冊指示，請參閱[在 Intune 註冊 Windows 裝置](https://docs.microsoft.com/intune/enduser/enroll-your-device-in-intune-windows)。 您也可以傳送給使用者 [What can my IT admin see on my devic ](https://docs.microsoft.com/intune/enduser/what-can-your-it-administrator-see-when-you-enroll-your-device-in-intune-windows) (我的 IT 系統管理員可看到我裝置上的什麼內容)。

    如需終端使用者工作的詳細資訊，請參閱[使用 Microsoft Intune 之使用者體驗的相關資源](https://docs.microsoft.com/intune/deploy-use/what-to-tell-your-end-users-about-using-microsoft-intune)。

除非您要將公司入口網站部署至裝置，否則不需要進行任何額外的工作。  在管理主控台中可以放心略過步驟 2 和 3。


---
title: "使用 Microsoft Intune 設定 Windows 裝置管理 | Microsoft Docs"
description: "為 Microsoft Intune 的 Windows 裝置啟用行動裝置管理 (MDM)。"
keywords: 
author: staciebarker
manager: stabar
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9a18c0fe-9f03-4e84-a4d0-b63821bf5d25
ms.reviewer: damionw
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 6b99854e17e00a0dd0f91fa82fd1b79d1dfe5663
ms.openlocfilehash: 6277f82483eb8fb7f5a4e4a832a909490ba0050c
ms.lasthandoff: 02/18/2017


---

# <a name="set-up-windows-device-management"></a>設定 Windows 裝置管理

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

使用下列其中一種方法設定 Windows 裝置註冊︰

- [**自動向 Azure Active Directory Premium 註冊 Windows 10 及 Windows 10 行動裝置版**](#set-up-windows-10-and-windows-10-mobile-automatic-enrollment-with-azure-active-directory-premium) 
 -  此方法僅用於 Windows 10 裝置與 Windows 10 行動裝置版裝置。
 -  您必須擁有 Azure Active Directory Premium 才能使用此方法。 否則，請使用 Windows 8.1 及 Windows Phone 8.1 適用的註冊方法。
 -  若選擇不啟用自動註冊，請使用 Windows 8.1 及 Windows Phone 8.1 適用的註冊方法。


- [**透過設定 CNAME 來註冊 Windows 8.1 及 Windows Phone 8.1**](#set-up-windows-81-and-windows-phone-81-enrollment-by-configuring-cname) 
 - 若要註冊 Windows 8.1 及 Windows Phone 8.1 裝置，必須使用此方法。

[!INCLUDE[AAD-enrollment](../includes/win10-automatic-enrollment-aad.md)]

## <a name="set-up-windows-81-and-windows-phone-81-enrollment-by-configuring-cname"></a>透過設定 CNAME 來註冊 Windows 8.1 及 Windows Phone 8.1
您可以讓使用者使用 Intune 公司入口網站來安裝及註冊其裝置。 如果您建立 DNS CNAME 資源記錄，使用者會連線並註冊 Intune，而不需要輸入伺服器名稱。

1. **設定 Intune**<br>
如果尚未這麼做，請將[行動裝置管理 (MDM) 授權單位](prerequisites-for-enrollment.md#step-2-set-mdm-authority)設定為 **Microsoft Intune**，然後設定 MDM，為行動裝置管理做好準備。

2. **建立 CNAME** (選用)<br>
建立公司網域的 **CNAME** DNS 資源記錄。 例如，假設公司網站為 contoso.com，您就必須在 DNS 中建立 CNAME，將 EnterpriseEnrollment.contoso.com 重新導向 enterpriseenrollment-s.manage.microsoft.com。


    雖然建立 CNAME DNS 項目並非必要，但 CNAME 記錄可以方便使用者進行註冊。 若找不到任何註冊 CNAME 記錄，將會提示使用者手動輸入下列 MDM 伺服器名稱：https://enrollment.manage.microsoft.com。


    CNAME 資源記錄必須具有下列資訊：

  |類型|主機名稱|指向|TTL|
  |--------|-------------|-------------|-------|
  |CNAME|EnterpriseEnrollment.company_domain.com|EnterpriseEnrollment-s.manage.microsoft.com |1 小時|
  |CNAME|EnterpriseRegistration.company_domain.com|EnterpriseRegistration.windows.net|1 小時|

  `EnterpriseEnrollment-s.manage.microsoft.com` – 支援從電子郵件的網域名稱辨識網域，重新導向至 Intune 服務

  `EnterpriseRegistration.windows.net` - 支援將使用工作或學校帳戶向 Azure Active Directory 註冊的 Windows 8.1 和 Windows 10 行動裝置版裝置

  如果您的公司對使用者認證使用多個網域，請為每個網域建立 CNAME 記錄。

  例如，假設公司網站為 contoso.com，您就必須在 DNS 中建立 CNAME，將 EnterpriseEnrollment.contoso.com 重新導向 EnterpriseEnrollment-s.manage.microsoft.com。 DNS 記錄變更可能需要 72 小時才會傳播完成。 在 DNS 記錄傳播完成之前，您無法在 Intune 中驗證 DNS 變更。

3.  **驗證 CNAME**<br>在 [Intune 管理主控台](http://manage.microsoft.com)中，選擇 [管理] &gt; [行動裝置管理] &gt; [Windows]。 在 [指定已驗證的網域名稱] 方塊中輸入公司網站中已驗證網域的 URL，然後選擇 [測試自動偵測]。

4.  **告訴使用者如何註冊其裝置，以及開始管理之後會發生的情況。**

    如需使用者註冊指示，請參閱[在 Intune 註冊 Windows 裝置](https://docs.microsoft.com/intune/enduser/enroll-your-device-in-intune-windows)。

    如需終端使用者工作的詳細資訊，請參閱[使用 Microsoft Intune 之使用者體驗的相關資源](https://docs.microsoft.com/intune/deploy-use/what-to-tell-your-end-users-about-using-microsoft-intune)。

如需終端使用者工作的詳細資訊，請參閱下列文章：      - [使用 Microsoft Intune 之終端使用者經驗的相關資源](how-to-educate-your-end-users-about-microsoft-intune.md)
      - [適用於 Windows 裝置的終端使用者指引](../enduser/using-your-windows-device-with-intune.md)

### <a name="see-also"></a>請參閱
[Microsoft Intune 中註冊裝置的必要條件](prerequisites-for-enrollment.md)


---
title: "使用 Microsoft Intune 設定 Windows 裝置管理 | Microsoft Docs"
description: "為 Microsoft Intune 的 Windows 裝置啟用行動裝置管理 (MDM)。"
keywords: 
author: NathBarn
manager: angrobe
ms.date: 02/26/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9a18c0fe-9f03-4e84-a4d0-b63821bf5d25
ms.reviewer: damionw
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 255c3e47464ac7670a971881cf399e8e2bb17044
ms.openlocfilehash: 4acbae2aba4cff21286d45cb7cb1691864c281dc
ms.lasthandoff: 02/28/2017


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

### <a name="step-1-set-up-intune"></a>步驟 1：設定 Intune

如果尚未這麼做，請將[行動裝置管理 (MDM) 授權單位](prerequisites-for-enrollment.md#step-2-set-mdm-authority)設定為 **Microsoft Intune**，然後設定 MDM，為行動裝置管理做好準備。

### <a name="step-2-create-cnames-optional"></a>步驟 2：建立 CNAME (選用)

建立公司網域的 **CNAME** DNS 資源記錄。 例如，假設公司網站為 contoso.com，您就必須在 DNS 中建立 CNAME，將 EnterpriseEnrollment.contoso.com 重新導向 enterpriseenrollment-s.manage.microsoft.com。


   雖然建立 CNAME DNS 項目並非必要，但 CNAME 記錄可以方便使用者進行註冊。 若找不到任何註冊 CNAME 記錄，會提示使用者手動輸入下列 MDM 伺服器名稱：enrollment.manage.microsoft.com。

   CNAME 資源記錄必須具有下列資訊：

  |類型|主機名稱|指向|TTL|
  |--------|-------------|-------------|-------|
  |CNAME|EnterpriseEnrollment.company_domain.com|EnterpriseEnrollment-s.manage.microsoft.com |1 小時|
  |CNAME|EnterpriseRegistration.company_domain.com|EnterpriseRegistration.windows.net|1 小時|

  `EnterpriseEnrollment-s.manage.microsoft.com` – 支援從電子郵件的網域名稱辨識網域，重新導向至 Intune 服務

  `EnterpriseRegistration.windows.net` - 支援將使用工作或學校帳戶向 Azure Active Directory 註冊的 Windows 8.1 和 Windows 10 行動裝置版裝置

  如果您的公司對使用者認證使用多個網域，請為每個網域建立 CNAME 記錄。

  例如，假設公司網站為 contoso.com，您就必須在 DNS 中建立 CNAME，將 EnterpriseEnrollment.contoso.com 重新導向 EnterpriseEnrollment-s.manage.microsoft.com。 DNS 記錄變更可能需要 72 小時才會傳播完成。 在 DNS 記錄傳播完成之前，您無法在 Intune 中驗證 DNS 變更。

### <a name="step-3-verify-cname"></a>步驟 3：驗證 CNAME

在 [Intune 管理主控台](http://manage.microsoft.com)中，選擇 [管理] &gt; [行動裝置管理] &gt; [Windows]。 在 [指定已驗證的網域名稱] 方塊中輸入公司網站中已驗證網域的 URL，然後選擇 [測試自動偵測]。

### <a name="step-4-tell-your-users-how-to-enroll-their-devices-and-what-to-expect-after-theyre-brought-into-management"></a>步驟 4：告訴使用者如何註冊其裝置，以及開始管理之後會發生的情況。

   如需使用者註冊指示，請參閱[在 Intune 註冊 Windows 裝置](https://docs.microsoft.com/intune/enduser/enroll-your-device-in-intune-windows)。

   如需終端使用者工作的詳細資訊，請參閱[如何指導終端使用者使用 Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/what-to-tell-your-end-users-about-using-microsoft-intune) 和[適用於 Windows 裝置的終端使用者指南](../enduser/using-your-windows-device-with-intune.md)。

### <a name="see-also"></a>請參閱
[Microsoft Intune 中註冊裝置的必要條件](prerequisites-for-enrollment.md)


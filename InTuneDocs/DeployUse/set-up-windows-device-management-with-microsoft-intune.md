---
# required metadata

title: 使用 Microsoft Intune 設定 Windows 裝置管理 | Microsoft Intune
description:
keywords:
author: NathBarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 9a18c0fe-9f03-4e84-a4d0-b63821bf5d25

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# 設定 Windows 裝置管理
Intune 可讓您為 Windows 電腦裝置註冊啟用 BYOD (「攜帶您自己的裝置」)，以授權存取公司電子郵件和應用程式。 搭配 Azure Active Directory 一起使用時，還能快速、自動地將新的 Windows 10 裝置納入管理，不必重新安裝電腦的映像即可存取公司資源。 註冊之後，使用者即可登入，並使用 Intune 管理主控台，透過原則、應用程式和設定將他們的裝置設為目標。 您也可以[使用 Microsoft Intune 設定 Windows Phone 管理](set-up-windows-phone-management-with-microsoft-intune.md)，或[使用 Intune 用戶端軟體管理電腦](manage-windows-pcs-with-microsoft-intune.md)。

建立 DNS CNAME 可以協助使用者連線到 Intune 註冊，而無須輸入伺服器名稱。

### 設定 Windows 裝置管理

  1.  建立公司網域的 CNAME DNS 資源記錄。 例如，假設公司網站為 contoso.com，您就必須在 DNS 中建立 CNAME，將 EnterpriseEnrollment.contoso.com 重新導向 EnterpriseEnrollment-s.manage.microsoft.com。 如果已驗證的網域不止一個，請為每個網域建立一筆 CNAME 記錄。CNAME 資源記錄必須包含下列資訊：

  |類型|主機名稱|指向|TTL|
  |--------|-------------|-------------|-------|
  |CNAME|EnterpriseEnrollment.company_domain.com|EnterpriseEnrollment-s.manage.microsoft.com |1 小時|
  |CNAME|EnterpriseRegistration.company_domain.com|EnterpriseRegistration.windows.net|1 小時|

    DNS record changes might take up to 72 hours to propagate. You cannot verify the DNS change in Intune until the DNS record propagates.

    **EnterpriseEnrollment-s.manage.microsoft.com** – Supports a redirect to the Intune service with domain recognition from the email’s domain name

    **EnterpriseRegistration.windows.net** – Supports Windows 8.1 and Windows 10 Mobile devices that will register with Azure Active Directory using their work or school account

  2.  在 [Intune 管理主控台](http://manage.microsoft.com)中，按一下 [系統管理] &gt; [行動裝置管理] &gt; [Windows]
  ![Windows 裝置管理對話方塊](../media/enroll-intune-winenr.png)
  3.  在 [指定驗證的網域名稱] 方塊中，輸入已驗證的公司網站網域的 URL，然後按一下 [測試自動偵測]

### 請參閱
[準備在 Microsoft Intune 中註冊裝置](get-ready-to-enroll-devices-in-microsoft-intune.md)


<!--HONumber=May16_HO2-->



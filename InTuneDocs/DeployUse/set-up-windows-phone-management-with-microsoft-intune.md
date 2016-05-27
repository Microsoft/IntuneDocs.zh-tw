---
# required metadata

title: 使用 Microsoft Intune 設定 Windows 10 行動裝置版和 Windows Phone 管理 | Microsoft Intune
description:
keywords:
author: NathBarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: f5615051-2dd1-453b-9872-d3fdcefb2cb8

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---


# 使用 Microsoft Intune 設定 Windows Phone 和 Windows 10 行動裝置版管理
Windows 10 行動裝置版或 Windows Phone 裝置必須能夠與 Intune 通訊，您才能使用 Microsoft Intune 管理裝置。 為了簡化工作，您可以建立 DNS 記錄，使用者就不需要輸入伺服器位址。 下列步驟說明如何簡化使用者的註冊。  

在大部分情況下，使用者可以從 Windows 市集安裝公司入口網站應用程式。 如果您管理 Windows Phone 8.0 裝置，或需要將公司入口網站部署至 Windows Phone 裝置，您也必須下載並簽署公司入口網站應用程式。 請參閱[設定 Windows Phone 8.0 管理](set-up-windows-phone-8.0-management-with-microsoft-intune.md).

1.  **設定 Intune**
    如果尚未這麼做，請將[行動裝置管理授權單位](get-ready-to-enroll-devices-in-microsoft-intune.md#set-mobile-device-management-authority)設定為 Microsoft Intune 並設定 MDM，為行動裝置管理做好準備。

2.  設定註冊伺服器位址的 DNS 別名 (選用)

    建立 DNS 別名 (CNAME 記錄類型) 可讓使用者更輕鬆地註冊裝置。 如果您不建立 DNS 別名，則使用者必須

  1.  建立公司網域的 CNAME DNS 資源記錄。 例如，假設公司網站為 contoso.com，您就必須在 DNS 中建立 CNAME，其會將 EnterpriseEnrollment.contoso.com 重新導向到 manage.microsoft.com。 如果已驗證的網域不止一個，請為每個網域建立一筆 CNAME 記錄。CNAME 資源記錄必須包含下列資訊：

      |類型|主機名稱|指向|TTL|
      |--------|-------------|-------------|-------|
      |CNAME|EnterpriseEnrollment.company_domain.com|EnterpriseEnrollment-s.manage.microsoft.com |1 小時|
      |CNAME|EnterpriseRegistration.company_domain.com|EnterpriseRegistration.windows.net|1 小時|

      DNS 記錄變更可能需要 72 小時才會傳播完成。 在 DNS 記錄傳播完成之前，您無法在 Intune 中驗證 DNS 變更。

      EnterpriseEnrollment-s.manage.microsoft.com - 支援從電子郵件的網域名稱辨識網域，以重新導向至 Intune 服務

      EnterpriseRegistration.windows.net - 支援將使用工作或學校帳戶向 Azure Active Directory 註冊的 Windows 8.1 和 Windows 10 行動裝置版裝置

    2.  在 [Intune 管理主控台](http://manage.microsoft.com)中，按一下 [系統管理] &gt; [行動裝置管理] &gt; [Windows Phone].

      ![設定 Windows 的行動裝置管理對話方塊](../media/windows-device-enrollment.png)

    3.  在 [指定驗證的網域名稱] 方塊中，輸入已驗證的公司網站網域的 URL，然後按一下 [測試自動偵測].



除非您要將公司入口網站部署至裝置，否則不需要進行任何額外的工作。  在管理主控台中可以放心略過步驟 2、3 和 4。


<!--HONumber=May16_HO1-->



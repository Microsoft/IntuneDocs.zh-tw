---
title: "使用 Microsoft Intune 設定 Windows 裝置管理 | Microsoft Intune"
description: "啟用適用於 Windows 電腦的行動裝置管理 (MDM)，包含使用 Microsoft Intune 的 Windows 10 裝置。"
keywords: 
author: NathBarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9a18c0fe-9f03-4e84-a4d0-b63821bf5d25
ms.reviewer: damionw
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 5f336cf52cbecd93cb7b2850560327e6024302e0
ms.openlocfilehash: 710e34f8f97377bf57a398f74773788df3794654


---

# 設定 Windows 裝置管理
Intune 可讓您為 Windows 電腦裝置註冊啟用 BYOD (「攜帶您自己的裝置」)，以授權存取公司電子郵件和應用程式。 搭配 Azure Active Directory 一起使用時，還能快速、自動地將新的 Windows 10 裝置納入管理，不必重新安裝電腦的映像即可存取公司資源。 註冊之後，使用者即可登入，並使用 Intune 管理主控台，透過原則、應用程式和設定將他們的裝置設為目標。 您也可以[使用 Microsoft Intune 設定 Windows Phone 管理](set-up-windows-phone-management-with-microsoft-intune.md)，或[使用 Intune 用戶端軟體管理電腦](manage-windows-pcs-with-microsoft-intune.md)。

建立 DNS CNAME 可以協助使用者連線到 Intune 註冊，而無須輸入伺服器名稱。

### 設定 Windows 裝置管理

  1.  建立公司網域的 **CNAME** DNS 資源記錄。 例如，假設公司網站為 contoso.com，您就必須在 DNS 中建立 CNAME，將 EnterpriseEnrollment.contoso.com 重新導向 EnterpriseEnrollment-s.manage.microsoft.com。 雖然 CNAME DNS 項目針對 Windows 裝置註冊為選擇性，建議您在必要時建立一或多個記錄，來讓 Windows 裝置註冊程序能夠更順利。 如果找不到任何 CNAME 記錄，則會提示使用者手動輸入 MDM 伺服器名稱。

  如果已驗證的網域不止一個，請為每個網域建立一筆 CNAME 記錄。 CNAME 資源記錄必須包含下列資訊：

  |類型|主機名稱|指向|TTL|
  |--------|-------------|-------------|-------|
  |CNAME|EnterpriseEnrollment.company_domain.com|EnterpriseEnrollment-s.manage.microsoft.com |1 小時|
  |CNAME|EnterpriseRegistration.company_domain.com|EnterpriseRegistration.windows.net|1 小時|

  DNS 記錄變更可能需要 72 小時才會傳播完成。 在 DNS 記錄傳播完成之前，您無法在 Intune 中驗證 DNS 變更。

  **EnterpriseEnrollment-s.manage.microsoft.com** - 支援從電子郵件的網域名稱辨識網域，以重新導向至 Intune 服務

  **EnterpriseRegistration.windows.net** - 支援將使用工作或學校帳戶向 Azure Active Directory 註冊的 Windows 8.1 和 Windows 10 行動裝置版裝置

  2.  在 [Intune 管理主控台](http://manage.microsoft.com)中，按一下 [系統管理] &gt; [行動裝置管理] &gt; [Windows]。
  ![Windows 裝置管理對話方塊](../media/enroll-intune-winenr.png)
  3.  在 [指定驗證的網域名稱] 方塊中輸入公司網站中已驗證網域的 URL，然後按一下 [測試自動偵測]。

### 請參閱
[準備在 Microsoft Intune 中註冊裝置](get-ready-to-enroll-devices-in-microsoft-intune.md)



<!--HONumber=Jul16_HO3-->



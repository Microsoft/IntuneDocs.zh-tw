---
title: "使用 Microsoft Intune 設定 Windows 裝置管理 | Microsoft Intune"
description: "啟用適用於 Windows 電腦的行動裝置管理 (MDM)，包含使用 Microsoft Intune 的 Windows 10 裝置。"
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 08/29/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9a18c0fe-9f03-4e84-a4d0-b63821bf5d25
ms.reviewer: damionw
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: dfc5241376033471a232b059ac07fa4488f05514
ms.openlocfilehash: c405408bd6a1e2b0743566e413436aefbaa7018b


---

# 設定 Windows 裝置管理

Intune 系統管理員有兩種方式可為 Windows 電腦啟用註冊與管理：

- **[使用 Azure Active Directory 自動註冊](#azure-active-directory-enrollment)** - Windows 10 與 Windows 10 行動裝置版使用者將工作或學校帳戶新增至裝置，即可註冊裝置
- **[公司入口網站註冊](#company-portal-app-enrollment)** - Windows 8.1 和更新版本使用者註冊其裝置的方法為下載並安裝公司入口網站應用程式，然後在應用程式中輸入其工作或學校帳戶認證。

[!INCLUDE[AAD-enrollment](../includes/win10-automatic-enrollment-aad.md)]

## 設定公司入口網站應用程式註冊
您可以讓使用者使用 Intune 公司入口網站應用程式安裝並註冊其裝置。 如果您建立 DNS CNAME 資源記錄，使用者會連線並註冊 Intune，而不需要輸入伺服器名稱。

1. **設定 Intune**<br>
如果尚未這麼做，請將[行動裝置管理 (MDM) 授權單位](prerequisites-for-enrollment.md#set-mobile-device-management-authority)設定為 **Microsoft Intune**，然後設定 MDM，為行動裝置管理做好準備。

2. **建立 CNAME** (選用)<br>為公司網域建立 **CNAME** DNS 資源記錄以簡化註冊程序。 雖然建立 CNAME DNS 項目為選擇性作業，但是 CNAME 記錄可讓使用者更輕鬆地註冊。 如果找不到任何註冊 CNAME 記錄，系統會提示使用者手動輸入 MDM 伺服器名稱 `https://manage.microsoft.com`。 CNAME 資源記錄必須具有下列資訊：

  |類型|主機名稱|指向|TTL|
  |--------|-------------|-------------|-------|
  |CNAME|EnterpriseEnrollment.company_domain.com|EnterpriseEnrollment-s.manage.microsoft.com |1 小時|
  |CNAME|EnterpriseRegistration.company_domain.com|EnterpriseRegistration.windows.net|1 小時|

  `EnterpriseEnrollment-s.manage.microsoft.com` – 支援從電子郵件的網域名稱辨識網域，重新導向至 Intune 服務

  `EnterpriseRegistration.windows.net` – 支援將使用工作或學校帳戶向 Azure Active Directory 註冊的 Windows 8.1 和 Windows 10 行動裝置版裝置

  如果您的公司對使用者認證使用多個網域，請為每個網域建立 CNAME 記錄。

  例如，假設公司網站為 contoso.com，您就必須在 DNS 中建立 CNAME，將 EnterpriseEnrollment.contoso.com 重新導向 EnterpriseEnrollment-s.manage.microsoft.com。 DNS 記錄變更可能需要 72 小時才會傳播完成。 在 DNS 記錄傳播完成之前，您無法在 Intune 中驗證 DNS 變更。

3.  **驗證 CNAME**<br>在 [Intune 管理主控台](http://manage.microsoft.com)中，選擇 [管理] &gt; [行動裝置管理] &gt; [Windows]。 在 [指定已驗證的網域名稱] 方塊中輸入公司網站中已驗證網域的 URL，然後選擇 [測試自動偵測]。

  ![Windows 裝置管理對話方塊](../media/enroll-intune-winenr.png)

4.  **選擇性步驟**<br>Windows 10 不需要**新增側載金鑰**步驟。 只有在您將無法在 Windows 市集使用的企業營運 (LOB) 應用程式散發到裝置時，才需要**上傳程式碼簽署憑證**步驟。 [深入了解](set-up-windows-phone-8.0-management-with-microsoft-intune.md)。

6.  **通知使用者**<br>您將必須讓使用者知道如何註冊其裝置，以及開始管理之後會發生的情況：
      - [要告訴使用者之關於使用 Microsoft Intune 的事項](what-to-tell-your-end-users-about-using-microsoft-intune.md)
      - [適用於 Windows 裝置的使用者指南](../enduser/using-your-windows-device-with-intune.md)

### 請參閱
[Microsoft Intune 中註冊裝置的必要條件](prerequisites-for-enrollment.md)



<!--HONumber=Oct16_HO3-->



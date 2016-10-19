---
title: "Microsoft Intune 的網域名稱 | Microsoft Intune"
description: "為 Intune 新增網域名稱"
keywords: 
author: andredm7
manager: swadhwa
ms.date: 10/11/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c3c136f0-330d-432a-a91f-16f7dd097e55
ms.reviewer: damionw
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 38159f6dbcae2eeb4dca47141e60eed12cd7f6ee
ms.openlocfilehash: abcf37e7ec3150b5a2fe4cda910631f83d4c510a


---



# 透過 Microsoft Intune 設定自訂網域名稱

當貴組織註冊 Intune 等的 Microsoft 雲端式服務時，您會取得如下所示的初始網域名稱，且它會裝載在 Azure Active Directory 中：**contoso.onmicrosoft.com**。 在這個範例中，**yourdomain** 是您註冊時選擇的網域名稱，而 **onmicrosoft.com** 則是指派給新增至您訂閱中的帳戶尾碼。

您無法重新命名或移除該初始網域名稱。 不過，您可以新增、驗證或移除自己的自訂網域名稱，以搭配 Intune 使用，這對於您想要保留企業識別很有幫助。

## 新增並驗證您的自訂網域 

1. 移至 [Office 365 管理入口網站](https://portal.office.com/Admin/Default.aspx) 並登入您的系統管理員帳戶。

2. 在瀏覽窗格中，選擇 [設定] &gt; [網域]。

3. 選擇 [新增網域]，然後輸入您的自訂網域名稱。

4. [驗證網域] 對話方塊隨即開啟，提供您在 DNS 主機服務提供者中建立 TXT 記錄用的值。
    - **GoDaddy 使用者**：Office 365 管理入口網站會將您重新導向至 GoDaddy 的登入頁面。 在您輸入認證，並接受網域變更權限合約之後，便會自動建立 TXT 記錄。 您也可以[建立 TXT 記錄](https://support.office.com/en-us/article/Create-DNS-records-at-GoDaddy-for-Office-365-f40a9185-b6d5-4a80-bb31-aa3bb0cab48a?ui=en-US&rs=en-US&ad=US)。
    - **Register.com 使用者**：遵循[逐步指示](https://support.office.com/en-us/article/Create-DNS-records-at-Register-com-for-Office-365-55bd8c38-3316-48ae-a368-4959b2c1684e?ui=en-US&rs=en-US&ad=US#BKMK_verify)以建立 TXT 記錄。

    > [!TIP] 
    > 請務必建立 DNS 別名 (CNAME) 以進行 [Windows 裝置註冊](/Intune/deploy-use/set-up-windows-phone-management-with-microsoft-intune)，同時在 DNS 主機服務提供者中進行變更。

新增並驗證自訂網域的步驟也可以[在 Azure Active Directory 中執行](https://azure.microsoft.com/en-us/documentation/articles/active-directory-add-domain/)。

在混合式雲端案例中，新增自訂網域名稱，並且已驗證您的組織擁有它之後，您可以維持在內部部署 Active Directory 中管理使用者帳戶，然後與 Azure AD 同步。

## 同步處理內部部署使用者與 Azure AD##

1. 在內部部署 Active Directory 中，為自訂網域[新增 UPN 尾碼](https://technet.microsoft.com/en-us/library/cc772007.aspx)。
2. 為您打算匯入的內部部署使用者設定新的 UPN 尾碼。
3. 執行 [Azure AD Connect 同步處理](https://azure.microsoft.com/en-us/documentation/articles/active-directory-aadconnect/)，以便與 Azure AD 整合您的內部部署使用者。
4. 順利同步處理使用者帳戶資訊之後，您便可以使用 [Office 365 管理入口網站](https://portal.office.com/Admin/Default.aspx)來指派 Microsoft Intune 授權。

### 請參閱

[關於 Office 365 中的初始 onmicrosoft.com 網域](https://support.office.com/en-us/article/About-your-initial-onmicrosoft-com-domain-in-Office-365-B9FC3018-8844-43F3-8DB1-1B3A8E9CFD5A?ui=en-US&rs=en-US&ad=US)

[啟動 Microsoft Intune 前的須知事項](what-to-know-before-you-start-microsoft-intune.md)



<!--HONumber=Oct16_HO2-->



---
title: "設定自訂網域名稱 | Microsoft Intune"
description: "針對您的 Intune 訂閱新增自訂網域名稱"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 11/22/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2382f36f-13d8-4a32-81ad-6cfa604889c3
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: eeb85a28ea6f99a0123ec5df3b0d476a678b85cb
ms.openlocfilehash: 26b019b2b4c079daa89d15c783be0abf2b61dfee


---


# <a name="configure-a-custom-domain-name"></a>設定自訂網域名稱

當貴組織註冊像是 Intune 的 Microsoft 雲端式服務時，您會取得如下所示的初始網域名稱，且它會裝載在 Azure Active Directory (AD) 中：**yourdomain.onmicrosoft.com**。 在這個範例中，**yourdomain** 是您註冊時選擇的網域名稱，而 **onmicrosoft.com** 則是指派給新增至您訂閱中的帳戶尾碼。 當您的組織擁有自訂網域時，您可以將 Intune 的執行個體設定為使用該網域，而不訂用帳戶隨附的網域名稱。

建立使用者帳戶或同步處理內部部署 Active Directory 之前，強烈建議您先決定只要使用 .onmicrosoft.com 網域，還是要新增一或多個自訂網域名稱。 新增使用者之前先設定自訂網域，可讓使用者利用他們用來存取其他網域資源的認證登入，有助於簡化訂閱的使用者身分管理。

當您向 Microsoft 訂閱雲端式服務時，該服務的執行個體會變成 Microsoft [Azure AD 租用戶](http://technet.microsoft.com/library/jj573650.aspx#BKMK_WhatIsAnAzureADTenant)，這為您的雲端式服務提供身分識別和目錄服務。 此外，由於將 Intune 設定為使用組織自訂網域名稱的工作，與處理其他 Azure AD 租用戶的工作相同，您可以使用[新增您的網域](https://azure.microsoft.com/documentation/articles/active-directory-add-domain/)中的資訊和程序。

> [!TIP]
> 如需使用自訂網域搭配 Microsoft 雲端式服務的詳細資訊，請參閱 [Azure Active Directory 中的自訂網域名稱的概念式概觀](https://azure.microsoft.com/documentation/articles/active-directory-add-domain-concepts/)。

您無法重新命名或移除該初始網域名稱。 不過，您可以新增、驗證或移除自己的自訂網域名稱，以搭配 Intune 使用，這對於您想要保留企業識別很有幫助。

## <a name="to-add-and-verify-your-custom-domain"></a>新增並驗證您的自訂網域

1. 移至 [Office 365 管理入口網站](https://portal.office.com/Admin/Default.aspx) 並登入您的系統管理員帳戶。

2. 在瀏覽窗格中，選擇 [設定] &gt; [網域]。

3. 選擇 [新增網域]，然後輸入您的自訂網域名稱。

4. [驗證網域] 對話方塊隨即開啟，提供您在 DNS 主機服務提供者中建立 TXT 記錄用的值。
    - **GoDaddy 使用者**：Office 365 管理入口網站會將您重新導向至 GoDaddy 的登入頁面。 在您輸入認證，並接受網域變更權限合約之後，便會自動建立 TXT 記錄。 您也可以[建立 TXT 記錄](https://support.office.com/en-us/article/Create-DNS-records-at-GoDaddy-for-Office-365-f40a9185-b6d5-4a80-bb31-aa3bb0cab48a?ui=en-US&rs=en-US&ad=US)。
    - **Register.com 使用者**：遵循[逐步指示](https://support.office.com/en-us/article/Create-DNS-records-at-Register-com-for-Office-365-55bd8c38-3316-48ae-a368-4959b2c1684e?ui=en-US&rs=en-US&ad=US#BKMK_verify)以建立 TXT 記錄。

    > [!TIP]
    > 請務必建立 DNS 別名 (CNAME) 以進行 [Windows 裝置註冊](/Intune/deploy-use/set-up-windows-phone-management-with-microsoft-intune)，同時在 DNS 主機服務提供者中進行變更。

新增並驗證自訂網域的步驟也可以[在 Azure Active Directory 中執行](https://azure.microsoft.com/en-us/documentation/articles/active-directory-add-domain/)。

深入了解 [Office 365 中的初始 onmicrosoft.com 網域](https://support.office.com/en-us/article/About-your-initial-onmicrosoft-com-domain-in-Office-365-B9FC3018-8844-43F3-8DB1-1B3A8E9CFD5A?ui=en-US&rs=en-US&ad=US)

>[!div class="step-by-step"]

>[&larr; **登入 Intune**](.\start-with-a-paid-subscription-to-microsoft-intune-step-1.md)     [**將使用者新增至 Intune** &rarr;](.\start-with-a-paid-subscription-to-microsoft-intune-step-3.md)  



<!--HONumber=Dec16_HO2-->



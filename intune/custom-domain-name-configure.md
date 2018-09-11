---
title: 設定自訂網域名稱
titlesuffix: Microsoft Intune
description: 針對 Microsoft Intune 訂用帳戶新增自訂網域名稱
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 02/22/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 2382f36f-13d8-4a32-81ad-6cfa604889c3
ms.reviewer: angerobe
ms.suite: ems
ms.custom: intune-classic; get-started
ms.openlocfilehash: cbefc5ae5ef159c3c58a475f01a1513abb46ee90
ms.sourcegitcommit: 18f51ae8291b57562921e40fc364a5a60a59b139
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/09/2018
ms.locfileid: "44254066"
---
# <a name="configure-a-custom-domain-name"></a>設定自訂網域名稱

[!INCLUDE [both-portals](./includes/note-for-both-portals.md)]

本主題將告訴系統管理員如何使用 Microsoft Intune 來建立 DNS CNAME，以簡化和自訂其登入體驗。

當貴組織註冊諸如 Intune 的 Microsoft 雲端式服務時，您會取得裝載在 Azure Active Directory (AD) 中的初始網域名稱，像 **yourdomain.onmicrosoft.com**。 在本例中，**your-domain** 是您註冊時選擇的網域名稱。 **onmicrosoft.com** 是指派給新增至訂閱之帳戶的尾碼。 您可以設定貴組織的自訂網域存取 Intune，而不使用訂閱提供的網域名稱。

建立使用者帳戶或同步處理內部部署 Active Directory 之前，強烈建議您先決定只要使用 .onmicrosoft.com 網域，還是要新增一或多個自訂網域名稱。 先設定自訂網域再新增使用者，可簡化使用者管理。 這會讓使用者用他們存取其他網域資源的認證登入。

當您向 Microsoft 訂閱雲端式服務時，該服務的執行個體會變成 Microsoft [Azure AD 租用戶](http://technet.microsoft.com/library/jj573650.aspx#BKMK_WhatIsAnAzureADTenant)，這為您的雲端式服務提供身分識別和目錄服務。 此外，由於將 Intune 設定為使用組織自訂網域名稱的工作，與處理其他 Azure AD 租用戶的工作相同，您可以使用[新增您的網域](https://azure.microsoft.com/documentation/articles/active-directory-add-domain/)中的資訊和程序。

> [!TIP]
> 若要深入了解自訂網域，請參閱 [Azure Active Directory 中的自訂網域名稱的概念式概觀](https://azure.microsoft.com/documentation/articles/active-directory-add-domain-concepts/)。

您無法重新命名或移除初始的 onmicrosoft.com 網域名稱。 您可以新增、驗證或移除 Intune 使用的自訂網域名稱，以利企業識別。

## <a name="to-add-and-verify-your-custom-domain"></a>新增並驗證您的自訂網域

1. 移至 [Office 365 管理入口網站](https://portal.office.com/Admin/Default.aspx) 並登入您的系統管理員帳戶。

2. 在瀏覽窗格中，選擇 [設定] &gt; [網域]。

3. 選擇 [新增網域]，然後輸入您的自訂網域名稱。 選取 [下一步]。
   ![螢幕擷取畫面：Office 365 系統管理中心，選取 [設定] > [網域]，正在新增新的網域名稱](./media/domain-custom-add.png)
4. [驗證網域] 對話方塊隨即開啟，提供您在 DNS 主機服務提供者中建立 TXT 記錄用的值。
    - **GoDaddy 使用者**：Office 365 管理入口網站會將您重新導向至 GoDaddy 的登入頁面。 在您輸入認證，並接受網域變更權限合約之後，便會自動建立 TXT 記錄。 您也可以[建立 TXT 記錄](https://support.office.com/article/Create-DNS-records-at-GoDaddy-for-Office-365-f40a9185-b6d5-4a80-bb31-aa3bb0cab48a)。
    - **Register.com 使用者**：遵循[逐步指示](https://support.office.com/article/Create-DNS-records-at-Register-com-for-Office-365-55bd8c38-3316-48ae-a368-4959b2c1684e#BKMK_verify)以建立 TXT 記錄。

新增並驗證自訂網域的步驟也可以[在 Azure Active Directory 中執行](https://azure.microsoft.com/documentation/articles/active-directory-add-domain/)。

深入了解 [Office 365 中的初始 onmicrosoft.com 網域](https://support.office.com/article/About-your-initial-onmicrosoft-com-domain-in-Office-365-B9FC3018-8844-43F3-8DB1-1B3A8E9CFD5A)

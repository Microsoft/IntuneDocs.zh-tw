---
title: 設定自訂網域名稱
titleSuffix: Microsoft Intune
description: 針對 Microsoft Intune 訂用帳戶新增自訂網域名稱
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 06/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.assetid: 2382f36f-13d8-4a32-81ad-6cfa604889c3
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8e8d0a38d385e034b948b96a96df2189666362a9
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72505451"
---
# <a name="configure-a-custom-domain-name"></a>設定自訂網域名稱

[!INCLUDE [both-portals](../../intune-classic/includes/note-for-both-portals.md)]

本主題將告訴系統管理員如何使用 Microsoft Intune 來建立 DNS CNAME，以簡化和自訂其登入體驗。

當貴組織註冊諸如 Intune 的 Microsoft 雲端式服務時，您會取得裝載在 Azure Active Directory (AD) 中的初始網域名稱，像 **yourdomain.onmicrosoft.com**。 在本例中，**your-domain** 是您註冊時選擇的網域名稱。 **onmicrosoft.com** 是指派給新增至訂閱之帳戶的尾碼。 您可以設定貴組織的自訂網域存取 Intune，而不使用訂閱提供的網域名稱。

建立使用者帳戶或同步處理內部部署 Active Directory 之前，強烈建議您先決定只要使用 .onmicrosoft.com 網域，還是要新增一或多個自訂網域名稱。 先設定自訂網域再新增使用者，可簡化使用者管理。 設定客戶網域，讓使用者能夠以其用來存取其他網域資源的認證登入。

當您向 Microsoft 訂閱雲端式服務時，該服務的執行個體會變成 Microsoft [Azure AD 租用戶](https://technet.microsoft.com/library/jj573650.aspx#BKMK_WhatIsAnAzureADTenant)，這為您的雲端式服務提供身分識別和目錄服務。 此外，由於將 Intune 設定為使用組織自訂網域名稱的工作，與處理其他 Azure AD 租用戶的工作相同，您可以使用[新增您的網域](https://azure.microsoft.com/documentation/articles/active-directory-add-domain/)中的資訊和程序。

> [!TIP]
> 若要深入了解自訂網域，請參閱 [Azure Active Directory 中的自訂網域名稱的概念式概觀](https://azure.microsoft.com/documentation/articles/active-directory-add-domain-concepts/)。

您無法重新命名或移除初始的 onmicrosoft.com 網域名稱。 您可以新增、驗證或移除與 Intune 搭配使用的自訂網域名稱，以利企業識別。

## <a name="to-add-and-verify-your-custom-domain"></a>新增並驗證您的自訂網域

1. 前往 [Microsoft 365 系統管理中心](https://admin.microsoft.com/)並使用您的系統管理員帳戶登入。

2. 在瀏覽窗格中，選擇 [設定]  &gt; [網域]  。

3. 選擇 [新增網域]  ，然後輸入您的自訂網域名稱。 選取 [下一步]  。
   ![Microsoft 365 系統管理中心的螢幕擷取畫面，其中已選取 [設定] > [網域] 並新增新的網域名稱](./media/custom-domain-name-configure/domain-custom-add.png)
4. [驗證網域]  對話方塊隨即開啟，提供您在 DNS 主機服務提供者中建立 TXT 記錄用的值。
    - **GoDaddy 使用者**：Microsoft 365 系統管理中心會將您重新導向至 GoDaddy 的登入頁面。 在您輸入認證，並接受網域變更權限合約之後，便會自動建立 TXT 記錄。 您也可以[建立 TXT 記錄](https://support.office.com/article/Create-DNS-records-at-GoDaddy-for-Office-365-f40a9185-b6d5-4a80-bb31-aa3bb0cab48a)。
    - **Register.com 使用者**：遵循[逐步指示](https://support.office.com/article/Create-DNS-records-at-Register-com-for-Office-365-55bd8c38-3316-48ae-a368-4959b2c1684e#BKMK_verify)以建立 TXT 記錄。
5. [您可能需要建立其他 DNS 記錄來進行 Intune 註冊](../enrollment/windows-enroll.md#simplify-windows-enrollment-without-azure-ad-premium)。

新增並驗證自訂網域的步驟也可以[在 Azure Active Directory 中執行](https://azure.microsoft.com/documentation/articles/active-directory-add-domain/)。

深入了解 [Office 365 中的初始 onmicrosoft.com 網域](https://support.office.com/article/About-your-initial-onmicrosoft-com-domain-in-Office-365-B9FC3018-8844-43F3-8DB1-1B3A8E9CFD5A)

您可以藉由建立會將註冊重新導向至 Intune 伺服器的 DNS CNAME，來深入了解如何[簡化 Windows 註冊，而不使用 Azure AD Premium](../enrollment/windows-enroll.md#simplify-windows-enrollment-without-azure-ad-premium)。

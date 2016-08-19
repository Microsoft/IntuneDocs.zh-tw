---
title: "設定自訂網域名稱 | Microsoft Intune"
description: "說明針對您的 Intune 訂閱新增自訂網域名稱的程序"
keywords: 
author: Staciebarker
manager: arob98
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2382f36f-13d8-4a32-81ad-6cfa604889c3
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 376e6c1ae229187ab8ec73390f091f1d534365dd
ms.openlocfilehash: f18afc5487fe20ba4a13d938dad78fa6087128d7


---


# 設定自訂網域名稱

根據預設，Intune 會使用您第一次訂閱服務時所建立的 **<domain>.onmicrosoft.com** 網域名稱。 當您的組織擁有自訂網域時，您可以將 Intune 的執行個體設定為使用該網域，而不訂用帳戶隨附的網域名稱。

建立新使用者帳戶或從內部部署 Active Directory 同步處理帳戶之前，強烈建議您先決定是只要使用 .onmicrosoft.com 網域，還是要新增一個或多個自訂網域名稱。 新增使用者之前先設定自訂網域，可讓使用者利用他們用來存取其他網域資源的認證登入，有助於簡化訂閱的使用者身分管理。

當您向 Microsoft 訂閱雲端式服務時，該服務的執行個體會變成 Microsoft [Azure AD 租用戶](http://technet.microsoft.com/library/jj573650.aspx#BKMK_WhatIsAnAzureADTenant)，這為您的雲端式服務提供身分識別和目錄服務。 此外，由於將 Intune 設定為使用組織自訂網域名稱的工作，與處理其他 Azure AD 租用戶的工作相同，您可以使用[新增您的網域](https://azure.microsoft.com/documentation/articles/active-directory-add-domain/)中的資訊和程序。

> [!TIP]
> 如需使用自訂網域搭配 Microsoft 雲端式服務的詳細資訊，請參閱 [Azure Active Directory 中的自訂網域名稱的概念式概觀](https://azure.microsoft.com/documentation/articles/active-directory-add-domain-concepts/)。

### 後續步驟
恭喜！ 您剛完成 *Intune 快速入門指南*的步驟 2。

>[!div class="step-by-step"]

>[&larr; **登入 Intune**](.\start-with-a-paid-subscription-to-microsoft-intune-step-1.md)     [**將使用者新增至 Intune** &rarr;](.\start-with-a-paid-subscription-to-microsoft-intune-step-3.md)  



<!--HONumber=Jul16_HO3-->



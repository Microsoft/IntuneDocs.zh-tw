---
title: "同步處理 Active Directory 並將使用者新增至 Intune | Microsoft Intune"
description: "說明同步內部部署使用者和 Azure AD 以及將您 Intune 訂閱的權限授與系統管理員"
keywords: 
author: Staciebarker
manager: arob98
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6e9ec662-465b-4ed4-94c1-cff0fe18f126
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 376e6c1ae229187ab8ec73390f091f1d534365dd
ms.openlocfilehash: 8aeb23b709b50ccb8ad29868b4bc5ab96faf950f


---


# 同步處理 Active Directory 並將使用者新增至 Intune
您可以設定目錄同步處理，將使用者帳戶從內部部署 Active Directory 匯入到 Microsoft Azure Active Directory (Azure AD)。 讓內部部署的 Active Directory 與所有 Azure Active Directory 服務連線，可更易於管理使用者身分識別。 您也可以設定單一登入功能，讓使用者的驗證體驗親切又簡單。

為了更方便起見，當您透過相同的 [Azure AD 租用戶](http://technet.microsoft.com/library/jj573650.aspx#BKMK_WhatIsAnAzureADTenant)使用多項服務時，您先前已同步處理的使用者帳戶，可供所有共用相同 Azure AD 租用戶訂用帳戶的雲端式服務使用。

## 同步處理內部部署使用者與 Azure AD
同步處理使用者帳戶與 Azure AD 唯一需要的工具是 [Azure AD Connect 精靈](https://www.microsoft.com/download/details.aspx?id=47594)。 Azure AD Connect 精靈提供簡單和引導式的體驗，將內部部署身分識別基礎結構連線至雲端。  請選擇您的拓撲和需求 (單一或多個目錄、密碼同步或同盟)，精靈就會部署並設定讓連線運作所需的一切元件。 包括︰同步處理服務、Active Directory 同盟服務 (AD FS)，以及 Azure AD PowerShell 模組。

> [!TIP]
> Azure AD Connect 包含先前發行為 Dirsync 和 Azure AD Sync 的功能。 深入了解[目錄整合](http://technet.microsoft.com/library/jj573653.aspx)。 若要了解將使用者帳戶從本機目錄同步至 Azure AD 的優點，請參閱 [Active Directory 與 Azure AD 的相似性](http://technet.microsoft.com/library/dn518177.aspx)。

## 授與系統管理員權限
將使用者新增到您的 Intune 訂用帳戶後，建議您將[系統管理認證](administrative-accounts-websites-perms.md)授與幾個使用者帳戶。 您用來指派系統管理認證的主控台，會視您想要指派的系統管理員類型而定：

-   **租用戶系統管理員**：使用 **[!INCLUDE[wit_icp_1](../includes/wit_icp_1_md.md)]**指派這種系統管理員來管理您的訂用帳戶，包括計費、雲端存放裝置及管理使用者 (可使用 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]。

-   **服務系統管理員**：使用 **[!INCLUDE[wit_adminconsole](../includes/wit_adminconsole_md.md)]**指派這種系統管理員進行日常工作，包括管理行動裝置或電腦、部署原則或軟體，以及執行報表。


### 後續步驟
恭喜！ 您剛完成 *Intune 快速入門指南*的步驟 3。

>[!div class="step-by-step"]

>[&larr; **網域設定**](.\start-with-a-paid-subscription-to-microsoft-intune-step-2.md)     [**管理 Intune 授權** &rarr;](.\start-with-a-paid-subscription-to-microsoft-intune-step-4.md)  



<!--HONumber=Jul16_HO3-->



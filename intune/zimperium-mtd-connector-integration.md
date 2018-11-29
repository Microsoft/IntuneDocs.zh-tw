---
title: 整合 Zimperium MTD 與 Microsoft Intune
titleSuffix: ''
description: 如何使用 Microsoft Intune 設定 Zimperium Mobile Threat Defense (MTD) 解決方案，來控制行動裝置對公司資源的存取。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 12/29/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 363fd280-1865-4a61-855b-eb75c3c62753
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 68896a363cab37aabe9a597872da0fe75c44c473
ms.sourcegitcommit: 3903f20cb5686532ccd8c36aa43c5150cee7cca2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2018
ms.locfileid: "52267232"
---
# <a name="integrate-zimperium-with-intune"></a>將 Zimperium 與 Intune 整合

完成下列步驟以將 Zimperium Mobile Threat Defense 解決方案與 Intune 整合。

## <a name="before-you-begin"></a>開始之前

> [!NOTE]
> 下列步驟必須在  [Zimperium MTD 主控台](https://sso.zimperium.com/signon/aad/)中完成。

開始將 Zimperium 與 Intune 整合之前，請確定您有下列訂閱和認證：

-   Microsoft Intune 訂閱

-   可授與下列權限的 Azure Active Directory 管理員認證：

    -   登入及讀取使用者設定檔

    -   以登入的使用者身分存取目錄

    -   讀取目錄資料

    -   將裝置資訊傳送至 Intune

-   用來存取 Zimperium MTD 主控台的系統管理員認證。

### <a name="zimperium-app-authorization"></a>Zimperium 應用程式授權

Zimperium 應用程式授權程序如下：

-   允許 Zimperium 服務將裝置健全狀況狀態的相關資訊傳送回 Intune。

-   將 Zimperium 與 Azure Active Directory (AD) 註冊群組成員資格同步，以填入其裝置的資料庫。

-   允許 Zimperium 管理主控台使用 Azure AD 單一登入 (SSO)。

-   允許 Zimperium 應用程式使用 Azure AD SSO 登入。

## <a name="to-set-up-zimperium-integration"></a>設定 Zimperium 整合

1.  請前往  [Zimperium MTD 主控台](https://sso.zimperium.com/signon/aad/) ，並使用您的認證登入。

2.  從左側功能表中選擇 [管理]。

3.  選擇 [MDM設定] 索引標籤。

4.  選擇 [新增 MDM]，然後從 [MDM 提供者] 清單中選取 [Microsoft Intune]。

5.  當您將 Microsoft Intune 設定為 MDM 服務後，會彈出 [Microsoft Intune 設定] ****  視窗，請為下列各選項選擇 [新增 Azure Active Directory] **** ：**Zimperium zConsole**、**zIPS iOS 及 Android 應用程式**，以授權 Zimperium 透過 Azure AD 單一登入與 Intune 及 Azure AD 通訊。

    > [!IMPORTANT]
    > 您必須新增 Zimperium zConsole、zIPS iOS 和 Android 應用程式以完成與 Intune 整合的程序。

6.  選擇 [接受] ****  以授權 Zimperium 應用程式與 Intune 及 Azure Active Directory 通訊。

7.  將 **Zimperium zConsole** 與 **zIPS iOS 和 Android** 應用程式新增至 Azure AD 後，請新增 Azure AD 安全性群組。 此新增可讓 Zimperium 與服務同步處理 Azure AD 安全性群組。

8.  選擇 [完成] **** 以儲存設定，並啟動第一次 Azure AD 安全性群組同步。

## <a name="next-steps"></a>接下來的步驟

-   [設定 Zimperium 應用程式](mtd-apps-ios-app-configuration-policy-add-assign.md)

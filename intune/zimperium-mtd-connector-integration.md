---
title: "將 Zimperium 與 Intune 整合"
titleSuffix: Intune on Azure
description: "將 Intune 與 Zimperium 整合"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 09/06/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 363fd280-1865-4a61-855b-eb75c3c62753
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 1b4adb2db14c2e1c83be8e7b3644944c1910cb97
ms.sourcegitcommit: d434dfab7ef7a6c4082d675717fa22d5581b4f51
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2017
---
# <a name="integrate-zimperium-with-intune"></a>將 Zimperium 與 Intune 整合

您必須依照以下步驟，將 Zimperium Mobile Threat Defense 解決方案與 Intune 整合。

## <a name="before-you-begin"></a>開始之前

> [!NOTE]
> 以下步驟必須在 [Zimperium MTD 主控台](https://staging2-console.zimperium.com)進行。

開始將 Zimperium 與 Intune 整合之前，請確定您有下列項目：

-   Microsoft Intune 訂閱

-   可授與下列權限的 Azure Active Directory 管理員認證：

    -   登入及讀取使用者設定檔

    -   以登入的使用者身分存取目錄

    -   讀取目錄資料

    -   將裝置資訊傳送至 Intune

-   用來存取 Zimperium MTD 主控台的系統管理員認證。

### <a name="zimperium-app-authorization"></a>Zimperium 應用程式授權

Zimperium 應用程式授權程序包含下列步驟：

-   允許 Zimperium 服務將裝置健全狀況狀態的相關資訊傳送回 Intune。

-   將 Zimperium 與 Azure AD 註冊群組成員資格同步，以填入其裝置的資料庫。

-   允許 Zimperium 管理主控台使用 Azure AD 單一登入 (SSO)。

-   允許 Zimperium 應用程式使用 Azure AD SSO 登入。

## <a name="to-set-up-zimperium-integration"></a>設定 Zimperium 整合

1.  請前往 [Zimperium MTD 主控台](https://staging2-console.zimperium.com)，並使用您的認證登入。

2.  從左側功能表中選擇 [管理]。

3.  選擇 [MDM設定] 索引標籤。

4.  選擇 [新增 MDM]，然後從 [MDM 提供者] 清單中選取 [Microsoft Intune]。

5.  當您將 Microsoft Intune 設為 MDM 服務後，[Microsoft Intune 設定] 視窗隨即快顯，請為以下各選項選擇 [新增 Azure Active Directory]：**Zimperium zConsole**、**zIPS iOS 和 Android 應用程式**，以授權 Zimperium 與 Intune 和 Azure AD 透過 Azure AD 單一登入進行通訊。

    > [!IMPORTANT]
    > 您必須新增 Zimperium zConsole、zIPS iOS 和 Android 應用程式以完成與 Intune 整合的程序。

6.  選擇 [接受] 以授權 Zimperium 應用程式與 Intune 和 Azure Active Directory 進行通訊。

7.  將 **Zimperium zConsole** 及 **zIPS iOS 和 Android** 應用程式新增至 Azure AD 後，必須新增 Azure AD 安全性群組，這樣 Zimperium 才可將 Azure AD 安全性群組與其服務同步。

8.  選擇 [完成] 以儲存設定並啟動第一次 Azure AD 安全性群組同步處理。

## <a name="next-steps"></a>後續步驟

-   [設定 Zimperium 應用程式](mtd-apps-ios-app-configuration-policy-add-assign.md)

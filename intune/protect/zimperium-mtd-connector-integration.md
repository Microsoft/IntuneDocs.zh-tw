---
title: 整合 Zimperium MTD 與 Microsoft Intune
titleSuffix: Microsoft Intune
description: 如何使用 Microsoft Intune 設定 Zimperium Mobile Threat Defense (MTD) 解決方案，來控制行動裝置對公司資源的存取。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 363fd280-1865-4a61-855b-eb75c3c62753
ms.reviewer: davidra
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: d843cf707cf182655d0044dde289caca730ccd6b
ms.sourcegitcommit: 3ace4cba6e2f6fefa9120be3807387a49b200c9b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2019
ms.locfileid: "72810310"
---
# <a name="integrate-zimperium-with-intune"></a>將 Zimperium 與 Intune 整合

完成下列步驟以將 Zimperium Mobile Threat Defense 解決方案與 Intune 整合。

## <a name="before-you-begin"></a>開始之前

在 [Zimperium MTD 主控台](https://www.zimperium.com/platform)中執行下列步驟，會讓 Lookout 的服務連線到已註冊 Intune 的裝置 (使用裝置合規性)，以及尚未註冊的裝置 (使用應用程式防護原則)。

開始將 Zimperium 與 Intune 整合之前，請確定您有下列訂閱和認證：

- Microsoft Intune 訂閱

- 可授與下列權限的 Azure Active Directory 全域管理員管理員認證：

  - 登入及讀取使用者設定檔

  - 以登入的使用者身分存取目錄

  - 讀取目錄資料

  - 將裝置資訊傳送至 Intune

- 用來存取 Zimperium MTD 主控台的系統管理員認證。

### <a name="zimperium-app-authorization"></a>Zimperium 應用程式授權

Zimperium 應用程式授權程序如下：

- 授與 Zimperium 服務權限將裝置健全狀況狀態的相關資訊傳送回 Intune。 若要授與這些權限，您必須使用全域管理員認證。 授與權限是一次性作業。 授與權限之後，每日作業不需要全域管理員認證。

- 將 Zimperium 與 Azure Active Directory (AD) 註冊群組成員資格同步，以填入其裝置的資料庫。

- 允許 Zimperium 管理主控台使用 Azure AD 單一登入 (SSO)。

- 允許 Zimperium 應用程式使用 Azure AD SSO 登入。

如需同意與 Azure Active Directory 應用程式的詳細資訊，請參閱 Azure Active Directory 文章「Azure Active Directory v2.0 端點中的權限及同意」  中的[向目錄管理員要求權限](https://docs.microsoft.com/azure/active-directory/develop/v2-permissions-and-consent#request-the-permissions-from-a-directory-admin)。


## <a name="to-set-up-zimperium-integration"></a>設定 Zimperium 整合

1. 請前往 [Zimperium MTD 主控台](https://www.zimperium.com/platform)，並使用您的認證登入。 若要執行 Zimperium 整合安裝程序，您必須使用具有全域管理員角色的 Azure Active Directory 使用者登入。 這項一次性的安裝作業會使用全域管理員權限授與組織中 Zimperium 應用程式與 Intune 通訊的權限。 

2. 從左側功能表中選擇 [管理]  。

3. 選擇 [MDM設定]  索引標籤。

4. 選擇 [新增 MDM]  ，然後從 [MDM 提供者]  清單中選取 [Microsoft Intune]  。

5. 您將 Microsoft Intune 設定為 MDM 服務後，隨即快顯 [Microsoft Intune 設定]  視窗，請針對每個選項選擇 [新增 Azure Active Directory]  ：**Zimperium zConsole**、**zIPS iOS 和 Android 應用程式**授權 Zimperium 透過 Azure AD 單一登入與 Intune 和 Azure AD 進行通訊。

    > [!IMPORTANT]  
    > 您必須新增 Zimperium zConsole、zIPS iOS 和 Android 應用程式以完成與 Intune 整合的程序。

6. 選擇 [接受]  以授權 Zimperium 應用程式與 Intune 和 Azure Active Directory 進行通訊。

7. 將 **Zimperium zConsole** 與 **zIPS iOS 和 Android** 應用程式新增至 Azure AD 後，請新增 Azure AD 安全性群組。 此新增可讓 Zimperium 與服務同步處理 Azure AD 安全性群組。

8. 選擇 [完成]  以儲存設定並啟動第一次 Azure AD 安全性群組同步處理。

9. 登出 Zimperium MTD 主控台。

## <a name="next-steps"></a>後續步驟

- [針對已註冊的裝置設定 Zimperium 應用程式](mtd-apps-ios-app-configuration-policy-add-assign.md)
- [針對尚未註冊的裝置設定 Zimperiu 行動應用程式](~/protect/mtd-add-apps-unenrolled-devices.md)

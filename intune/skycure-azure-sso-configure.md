---
title: "設定 Skycure 以 Intune 使用 Azure AD 單一登入"
titleSuffix: Intune on Azure
description: "設定 Skycure 以 Intune 使用 Azure AD 單一登入"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 06/09/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e0466ac4-4942-4c4c-b8af-996b597c701d
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: b2d8a79baf65208e87dbe85d8cc934e167710144
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2017
---
# <a name="configure-skycure-to-use-azure-active-directory-single-sign-on-sso"></a>設定 Skycure 使用 Azure Active Directory 單一登入 (SSO)

當您整合 Intune 與 Skycure 時，會使用 Azure AD SSO。 以下是主要優點：

-   **管理員**可以使用相同的認證，而不必在每次登入和登出 Microsoft 入口網站 (Intune、Azure) 及 Skycure 管理主控台時重新輸入認證。

-   **使用者**可以使用相同的 Azure AD 認證，而不必在每次登入和登出 Skycure 應用程式時重新輸入認證。

以下是整合 Skycure 與 Azure Active Directory 單一登入 (SSO) 的步驟。

## <a name="to-retrieve-the-azure-active-directory-tenant-id"></a>擷取 Azure Active Directory 租用戶識別碼

您需要擷取 Azure AD 租用戶識別碼。

1.  移至 [Azure 入口網站](https://portal.azure.com/)，並使用您的認證登入。

2.  您可以看見 [儀表板]，請選擇 [Azure Active Directory]。

    ![Azure AD 儀表板](./media/skycure-sso-1.png)

3.  [Azure Active Directory] 刀鋒視窗隨即開啟，選擇 [屬性]。

    ![Azure AD [屬性] 刀鋒視窗](./media/skycure-sso-2.png)

4.  在 [Azure Active Directory 屬性] 刀鋒視窗中，按一下 [租用戶目錄識別碼] 下方的 [複製] 圖示。

5. 在文字檔中貼上複製的目錄識別碼值，讓您可在稍後使用。 稍後在 Skycure 與 Intune 整合過程中將需用到此目錄識別碼值。

    ![Azure AD 儀表板](./media/skycure-sso-3.png)

## <a name="allow-skycure-to-communicate-with-azure-active-directory"></a>允許 Skycure 與 Azure Active Directory 通訊

1.  在瀏覽器中輸入下列 URL。 輸入您先前複製到文字檔的 Azure Active Directory 租用戶識別碼，而不是 **DIRECTORY_ID**。

        https://login.microsoftonline.com/<DIRECTORY_ID>/oauth2/authorize?client_id=28fd67fdb1794629a8b0dad420b697c7&prompt=admin_consent&redirect_uri=https%3A%2F%2Fmc.skycure.com%2Fapi%2Fexternal%2Fmdm%2Faad_app_consent%2Fmanagement_callback&response_type=code

2.  您需要使用 Azure Active Directory 認證登入。 按一下 [接受] 繼續。

![Azure AD 登入頁面](./media/skycure-sso-4.png)

## <a name="create-an-azure-ad-security-group-for-skycure-optional"></a>建立適用於 Skycure 的 Azure AD 安全性群組 (選擇性)

您可能想要建立專用的使用者群組，其中包含執行 Skycure 的使用者 (例如 Skycure 使用者)。 透過報告分析 Skycure 活動時，這非常有用。

-   深入了解[如何在 Azure AD 中建立群組和新增成員](https://docs.microsoft.com/azure/active-directory/active-directory-groups-create-azure-portal)。

> [!NOTE] 
> 您也可以使用現有的 Azure AD 安全性群組。

## <a name="configure-the-azure-ad-account-to-integrate-intune-with-skycure"></a>設定 Azure AD 帳戶以整合 Intune 與 Skycure

1.  從 [Skycure 管理主控台](https://aad.skycure.com/)，輸入先前儲存於文字檔中的 Azure Active Directory 租用戶識別碼。

![Skycure 管理主控台的 Azure AD 租用戶識別碼欄位](./media/skycure-sso-5.png)

> [!IMPORTANT] 
> Skycure 會藉由查詢 Azure AD 來驗證 Azure AD 租用戶識別碼是否存在，如果 Skycure 找到該識別碼，管理員就可以繼續下一個步驟，此為基本安裝程式。

## <a name="next-steps"></a>後續步驟

[下載 Skycure iOS 應用程式設定原則 (英文)](skycure-ios-app-configuration-policy-download.md)

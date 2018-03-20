---
title: "設定 Skycure 與 Microsoft Intune 整合"
titlesuffix: 
description: "如何使用 Microsoft Intune 設定 Skycure Mobile Threat Defense (MTD) 解決方案，來控制行動裝置對公司資源的存取。"
keywords: 
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 12/21/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 359448d9-2384-42ac-a21c-a25148c20a7b
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 3a09806afae72f60961a94ab27707b4851006cf0
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/08/2018
---
# <a name="set-up-the-skycure-integration-with-intune"></a>設定 Skycure 與 Intune 整合

完成下列步驟以將 Skycure Mobile Threat Defense 解決方案與 Intune 整合。 您必須將 Skycure 應用程式新增至 Azure AD，才能使用單一登入功能。

## <a name="before-you-begin"></a>開始之前

### <a name="azure-ad-account-used-to-integrate-intune-and-skycure"></a>用來整合 Intune 與 Skycure 的 Azure AD 帳戶

-   在開始 Skycure 基本設定程序之前，請確定您已經在 [Skycure 管理主控台](https://aad.skycure.com)中正確設定 Azure AD 帳戶。

### <a name="full-integration-vs-read-only"></a>完整整合與唯讀

Skycure 支援兩種與 Intune 整合的模式：

-   **唯讀整合 (基本設定)：**僅清查來自 Azure Active Directory 的裝置，並將它們填入 Skycure 主控台。
<br>
    -   如果未在 Skycure 管理主控台中選取 [Report the health and risk of devices to Intune] (向 Intune 報告裝置的健全狀況和風險) 和 [Also report security incidents to Intune] (也向 Intune 報告安全性事件) 方塊，則整合將會是唯讀，並因此一律不會變更 Intune 中的裝置狀態 (相容或不相容)。
<br></br>
-   **完整整合：**允許 Skycure 向 Intune 報告裝置的風險和安全性事件詳細資料，這會在兩個雲端服務之間建立雙向通訊。

### <a name="how-the-skycure-apps-are-used-with-azure-ad-and-intune"></a>Skycure 應用程式如何搭配 Azure AD 和 Intune 使用？

-   **iOS 應用程式︰**允許使用者使用 iOS 應用程式登入 Azure AD。

-   **Android 應用程式︰**允許使用者使用 Android 應用程式登入 Azure AD。

-   **管理應用程式︰**這是 Skycure Azure AD 多租用戶應用程式，可啟用與 Intune 的服務對服務通訊。

## <a name="to-set-up-the-read-only-integration-between-intune-and-skycure"></a>設定 Intune 和 Skycure 之間的唯讀整合

> [!IMPORTANT]
> Skycure 系統管理員認證必須是屬於 Azure Active Directory 有效使用者的電子郵件，否則登入將會失敗。 Skycure 會使用 Azure Active Directory，透過單一登入 (SSO) 來驗證它的系統管理員。

1.  移至 [Skycure 管理主控台](https://aad.skycure.com)。

2.  輸入您的「Skycure 系統管理員認證」，然後按一下 [繼續]。

3.  移至 [設定]，選擇 [Intune 整合] 底下的 [基本設定]。

4.  在 [iOS 應用程式] 標籤上，按一下 [新增至 Active Directory]。

    ![Skycure 管理主控台上 iOS 應用程式的影像](./media/skycure-setup-1.png)

5.  隨即會開啟登入頁面。請輸入您的 Intune 認證，然後按一下 [接受]。

    ![iOS 應用程式 Intune 登入提示的影像](./media/skycure-setup-2.png)

6.  一旦將應用程式新增至 Azure AD，您就可以在 Skycure 管理主控台上看到指示，指出應用程式已成功新增至 Azure AD。

    ![iOS 應用程式完成畫面的影像](./media/skycure-setup-3.png)

> [!NOTE]
> 針對 [Skycure Android] 和 [管理] 應用程式重複相同程序。

### <a name="add-an-azure-ad-security-group-into-skycure"></a>將 Azure AD 安全性群組新增至 Skycure

您需要新增包含所有執行 Skycure 之裝置的 Azure AD 安全性群組。

-  輸入並選取所有執行 Skycure 之裝置的安全性群組，然後按一下 [套用變更]。

    ![顯示安全性群組 Skycure 管理主控台設定位置的影像](./media/skycure-setup-4.png)

Skycure 會將執行其 Mobile Threat Defense 服務的裝置，與 Azure AD 安全性群組同步。

![顯示在 Skycure 管理主控台上完成之安全性群組設定的影像](./media/skycure-setup-5.png)

## <a name="set-up-the-full-integration-between-intune-and-skycure"></a>設定 Intune 和 Skycure 之間的完整整合

1.  移至 [Skycure 管理主控台](https://aad.skycure.com)。

2.  輸入您的「Skycure 系統管理員認證」，然後按一下 [繼續]。

3.  移至 [設定]，選擇 [Intune 整合] 底下的 [完整整合]。

4.  選取下列設定：

    a.  向 Intune 報告裝置的健全狀況和風險

    b。  也向 Intune 報告安全性事件

5.  按一下 [套用變更]。

    ![顯示完成之 Skycure 完整整合的影像](./media/skycure-setup-6.png)

## <a name="next-steps"></a>接下來的步驟

[設定 Skycure 應用程式](mtd-apps-ios-app-configuration-policy-add-assign.md)

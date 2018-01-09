---
title: "下載與 Intune 搭配使用的 Skycure iOS 應用程式設定原則"
titlesuffix: Azure portal
description: "下載與 Intune 搭配使用的 Skycure iOS 應用程式設定原則。"
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 12/21/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1bdc2ecf-32d0-4b6a-80b4-dbcdb9909010
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: cbf26b44725f1fa08fbc6766f0560fe91d63d6ca
ms.sourcegitcommit: a3a744ea55f38a360ca9f788c77a5b3018d1add5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/30/2017
---
# <a name="download-skycure-ios-app-configuration-policy"></a>下載 Skycure iOS 應用程式設定原則

## <a name="before-you-begin"></a>開始之前

您需要登入 Skycure 管理主控台，才能執行後續步驟。

> [!TIP] 
> 如果使用 Microsoft Internet Explorer 11 或 Edge，您可能需要使用 InPrivate 模式開啟 Skycure 管理主控台。

## <a name="to-download-the-ios-app-configuration-policy"></a>下載 iOS 應用程式設定原則

1.  移至 [Skycure 管理主控台](https://aad.skycure.com)。

2.  輸入您的「Skycure 系統管理員認證」，然後按一下 [繼續]。

    ![Skycure 管理主控台登入](./media/skycure-ios-app-1.png)

    > [!IMPORTANT] 
    > Skycure 管理員使用者名稱是一個電子郵件帳戶，該帳戶必須是 Azure Active Directory 中有效的使用者帳戶，否則登入將會失敗。 Skycure 會使用 Azure Active Directory，透過單一登入 (SSO) 來驗證它的管理員使用者名稱。

3.  移至 [設定] &gt; [裝置管理整合] &gt; [EMM 整合選項]、選擇 [Microsoft Intune]，然後儲存您的選項。

4.  按一下 [整合安裝檔案] 連結，然後儲存所產生的 \*.zip 檔案。 此 .zip 檔包含 **skycure\_configuration.plist** 檔案，可用來在 Intune 傳統入口網站中建立 iOS 應用程式設定原則。

![Skycure 整合安裝檔案](./media/skycure-ios-app-2.png)

## <a name="next-steps"></a>接下來的步驟

[新增並指派 Skycure 應用程式、Microsoft Authenticator 應用程式和 iOS 設定原則](mtd-apps-ios-app-configuration-policy-add-assign.md)

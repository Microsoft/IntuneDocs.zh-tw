---
title: "下載與 Intune 搭配使用的 Skycure iOS 應用程式設定原則"
titleSuffix: Intune on Azure
description: "下載與 Intune 搭配使用的 Skycure iOS 應用程式設定原則。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 06/21/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1bdc2ecf-32d0-4b6a-80b4-dbcdb9909010
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: ffe1027e90203d4e300a2446f15e72cc5bf53973
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2017
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

4.  按一下 [整合安裝檔案] 連結，然後儲存所產生的 \*.zip 檔案。 此 .zip 檔包含 **skycure\_configuration.plist** 檔案，此檔案將用來在 Intune 傳統主控台中建立 iOS 應用程式設定原則。

![Skycure 整合安裝檔案](./media/skycure-ios-app-2.png)

## <a name="next-steps"></a>後續步驟

[新增並指派 Skycure 應用程式、Microsoft Authenticator 應用程式和 iOS 設定原則](mtd-apps-ios-app-configuration-policy-add-assign.md)

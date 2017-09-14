---
title: "下載 Skycure iOS 應用程式設定原則"
description: "下載 Skycure iOS 應用程式設定原則，以便與已部署至使用者的 Skycure iOS 應用程式搭配使用。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/16/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d211b876-4d3a-473c-999f-843c0a16cd22
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 02fabe879494c5351a6ae333875a8ef5962203cb
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/09/2017
---
# <a name="download-skycure-ios-app-configuration-policy"></a>下載 Skycure iOS 應用程式設定原則

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

##<a name="before-you-begin"></a>開始之前

您需要登入 Skycure 管理主控台，才能執行後續步驟。

> [!TIP] 
> 如果使用 Microsoft Internet Explorer 11 或 Edge，您可能需要使用 InPrivate 模式開啟 Skycure 管理主控台。

## <a name="to-download-the-ios-app-configuration-policy"></a>下載 iOS 應用程式設定原則

1.  移至 [Skycure 管理主控台](https://aad.skycure.com)。

2.  輸入您的「Skycure 系統管理員認證」，然後按一下 [繼續]。

    ![Skycure 管理主控台登入](../media/mtp/skycure-ios-app-1.png)

    > [!IMPORTANT] 
    > Skycure 管理員使用者名稱是一個電子郵件帳戶，該帳戶必須是 Azure Active Directory 中有效的使用者帳戶，否則登入將會失敗。 Skycure 會使用 Azure Active Directory，透過單一登入 (SSO) 來驗證它的管理員使用者名稱。

3.  移至 [設定] &gt; [裝置管理整合] &gt; [EMM 整合選項]、選擇 [Microsoft Intune]，然後儲存您的選項。

2.  按一下 [整合安裝檔案] 連結，然後儲存所產生的 \*.zip 檔案。 此 .zip 檔包含 **skycure\_configuration.plist** 檔案，可用來在 Intune 傳統入口網站中建立 iOS 應用程式設定原則。

![Skycure 整合安裝檔案](../media/mtp/skycure-ios-app-2.png)

## <a name="next-steps"></a>後續步驟

[新增 Skycure 應用程式、Microsoft Authenticator 應用程式和 iOS 設定原則](/intune-classic/deploy-use/add-skycure-apps-microsoft-authenticator-and-ios-app-configuration-policy)

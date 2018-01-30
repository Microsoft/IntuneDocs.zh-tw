---
title: "如何註冊 Windows 8.1 或 Windows RT 8.1 裝置 | Microsoft Docs"
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: dougeby
ms.date: 01/23/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 28984f26-1070-4f7a-877c-669a59375c0c
searchScope:
- User help
ROBOTS: 
ms.reviewer: priyar
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 28b7d99e285762945b746295688fee5d53209b29
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2018
---
# <a name="how-to-enroll-your-windows-81-or-windows-rt-81-device-in-intune"></a>如何在 Intune 註冊 Windows 8.1 或 Windows RT 8.1 裝置

如果您的公司或學校使用 Microsoft Intune，您可以註冊裝置來存取公司電子郵件、檔案和其他資源。 當您註冊裝置時，您的組織可確保公司資料的安全。 若要深入了解註冊，請參閱[如果您安裝公司入口網站應用程式並在 Intune 註冊裝置時，會發生什麼情況？](what-happens-if-you-install-the-company-portal-app-and-enroll-your-device-in-intune-windows.md)和[公司支援人員在您裝置上可看到和不可看到的項目](what-info-can-your-company-see-when-you-enroll-your-device-in-intune.md)。


註冊 Windows 8.1 或 Windows RT 8.1 裝置：

1.  在裝置上點選 [設定] &gt; [電腦設定] &gt; [網路] &gt; [工作場所]。

    ![nav-to-workplace](./media/W81-1-workplacejoin.png)

2.  必要時輸入使用者識別碼的公司或學校電子郵件，然後點選 [加入]。

    如果您的使用者識別碼非必要，就會使用您登入此裝置時所輸入的電子郵件地址。

3.  輸入公司或學校電子郵件的密碼。

    ![type-password](./media/W81-2-workplacesettings_signin.png)

4.  點選 [開啟裝置管理] 下的 [開啟]。

    ![turn-on-device-management](./media/W81-3-dev-mgt-turn-on.png)

5.  在 [Allow apps and services from company support (允許公司支援人員提供應用程式和服務)] 對話方塊中，核取 [我同意] 方塊，然後點選 [開啟]。

    ![turn-on-allow-apps-services](./media/W81-4-agree-allow-apps-services.png)

    當您成功註冊時，就會看見下列畫面。

    ![enrollment-complete](./media/W81-5-enrolled-done.png)

我們也建議您安裝公司入口網站應用程式，它可讓您輕鬆識別並取得與您本身及角色有關的公司應用程式。 公司入口網站應用程式可能已當作註冊程序的一部分加以安裝，這取決於公司設定 Intune 的方式。 如要確認是否有該應用程式，請在應用程式清單中尋找 [公司入口網站]。 如果應用程式清單中找不到 [公司入口網站]，請遵循下列步驟安裝它。

1.  點選 [開始] &gt; [存放區]。

2.  點選 [搜尋]，然後鍵入**公司入口網站**。

3.  在結果清單中，點選 [公司入口網站]。

4.  點選 [安裝] 或 [免費]。 顯示的選項取決於您的公司設定應用程式的方式。

是否仍需要協助？ 請連絡您公司的支援人員。 如需其連絡資訊，請查看[公司入口網站](https://portal.manage.microsoft.com#HelpDeskDialog)。

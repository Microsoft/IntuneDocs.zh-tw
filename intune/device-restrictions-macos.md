---
title: "macOS 的 Intune 裝置限制設定"
titlesuffix: Azure portal
description: "了解 macOS 裝置上可用以控制裝置設定與功能的 Intune 設定。"
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 08/01/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3129cbaf-96c2-4837-8907-ca87a605a496
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 69fc2959c7694a0120efff8653ce8d619f33a9d3
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2018
---
# <a name="macos-device-restriction-settings-in-microsoft-intune"></a>Microsoft Intune 中的 macOS 裝置限制設定

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

使用這些設定可在裝置限制設定檔中管理 macOS 裝置。

## <a name="password"></a>密碼
-   **密碼** - 需要使用者輸入密碼才可存取該裝置。
    -   **必要的密碼類型** - 指定密碼是否只能是數字，或者是否必須為英數字元 (包含字母和數字)。 只有 Mac OS X 10.10.3 版與更新版本才支援這項設定。
    -   **密碼中的非英數字元數目** - 指定密碼中所需的複雜字元數 (**0** 到 **4**)。<br>複雜字元是一種符號，如 **?**
    -   **密碼長度下限** - 輸入使用者必須設定的密碼長度下限 (介於 **4** 到 **16** 個字元之間)。
    -   **簡單密碼** - 允許使用簡單密碼，例如 **0000** 或 **1234**。
    -   **在螢幕鎖定最少幾分鐘後必須輸入密碼**- 指定電腦多長時間沒有活動後，即需要密碼才可解除鎖定。
    -   **沒有活動最久幾分鐘後鎖定螢幕** - 指定電腦必須閒置多長時間，螢幕才會鎖住。
    -   **密碼到期 (天)** - 指定使用者經過多少天後必須變更密碼 (**1** 到 **255** 天)。
    -   **避免重複使用以前用過的密碼** - 指定不可重複使用先前用過之密碼的次數 (**1** 到 **24**)。

## <a name="restricted-apps"></a>受限應用程式

您可以在受限制應用程式清單中，設定下列清單之一︰

**禁止的應用程式**清單 - 列出不允許使用者安裝與執行的應用程式 (並非由 Intune 管理)。
**核准的應用程式**清單 - 列出允許使用者安裝的應用程式。 若要保持相容，使用者絕不能安裝未列出的應用程式。 自動允許 Intune 所管理的應用程式。

若要設定清單，請按一下 [新增]，然後指定您所選的名稱，也可指定應用程式發行者以及應用程式的套件組合識別碼 (例如 *com.apple.calculator*)。

## <a name="domains"></a>Domains

### <a name="unmarked-email-domains"></a>未標記的電子郵件網域

在 [電子郵件網域 URL] 欄位中，將一或多個 URL 新增到清單中。 當使用者接收到來自不是您所設定之網域的電子郵件時，該電子郵件會在 iOS 郵件應用程式中標記為不受信任。


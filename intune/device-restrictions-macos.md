---
title: macOS 的 Microsoft Intune 裝置限制設定
titlesuffix: ''
description: 了解執行 macOS 的裝置上可用以控制裝置設定與功能的 Intune 設定。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/6/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 26d5af15086e422685c7c58c5b8a7d351f9eb854
ms.sourcegitcommit: e8e8164586508f94704a09c2e27950fe6ff184c3
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2018
ms.locfileid: "39321385"
---
# <a name="microsoft-intune-macos-device-restriction-settings"></a>Microsoft Intune macOS 裝置限制設定

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

本文將說明可以為執行 macOS 之裝置設定的 Microsoft Intune 裝置限制設定。

## <a name="password"></a>密碼
-   **密碼** - 需要使用者輸入密碼才可存取該裝置。
    -   **必要的密碼類型** - 指定密碼是否只能是數字，或者是否必須為英數字元 (包含字母和數字)。 只有 Mac OS X 10.10.3 版與更新版本才支援這項設定。
    -   **密碼中的非英數字元數目** - 指定密碼中所需的複雜字元數 (**0** 到 **4**)。<br>複雜字元是一種符號，例如 "**?**"。
    -   **密碼長度下限** - 輸入使用者必須設定的密碼長度下限 (介於 **4** 到 **16** 個字元之間)。
    -   **簡單密碼** - 允許使用簡單密碼，例如 **0000** 或 **1234**。
    -   **在螢幕鎖定最少幾分鐘後必須輸入密碼**- 指定電腦多長時間沒有活動後，即需要密碼才可解除鎖定。
    -   **沒有活動最久幾分鐘後鎖定螢幕** - 指定電腦必須閒置多長時間，螢幕才會鎖住。
    -   **密碼到期 (天)** - 指定使用者經過多少天後必須變更密碼 (**1** 到 **255** 天)。
    -   **避免重複使用以前用過的密碼** - 指定不可重複使用先前用過之密碼的次數 (**1** 到 **24**)。

## <a name="restricted-apps"></a>受限應用程式

您可以在受限制應用程式清單中，設定下列清單之一︰

- **禁止的應用程式**清單 - 列出不允許使用者安裝與執行的應用程式 (並非由 Intune 管理)。 使用者安裝禁止的應用程式並不會受到阻止，但如果已安裝，系統會向您回報。
- **核准的應用程式**清單 - 列出允許使用者安裝的應用程式。 使用者絕不能安裝未列出的應用程式。 自動允許 Intune 所管理的應用程式。 使用者安裝不在核准的清單上的應用程式並不會受到阻止，但如果已安裝，系統會向您回報。

若要設定清單，請按一下 [新增]，然後指定您所選的名稱，也可指定應用程式發行者以及應用程式的套件組合識別碼 (例如 *com.apple.calculator*)。

## <a name="domains"></a>Domains

### <a name="unmarked-email-domains"></a>未標記的電子郵件網域

在 [電子郵件網域 URL] 欄位中，將一或多個 URL 新增到清單中。 當使用者接收到來自不是您所設定之網域的電子郵件時，該電子郵件會在 MacOS 郵件應用程式中標記為不受信任。


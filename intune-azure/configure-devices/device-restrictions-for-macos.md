---
title: "macOS 的 Intune 裝置限制設定"
titleSuffix: Intune Azure preview
description: "Intune Azure 預覽版︰了解 macOS 裝置上可用以控制裝置設定與功能的 Intune 設定。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3129cbaf-96c2-4837-8907-ca87a605a496
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 153cce3809e24303b8f88a833e2fc7bdd9428a4a
ms.openlocfilehash: e6b308547331e20a8373aca56f9a0781dcd210a2
ms.lasthandoff: 02/18/2017


---

# <a name="macos-device-restriction-settings-in-microsoft-intune"></a>Microsoft Intune 中的 macOS 裝置限制設定

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

## <a name="password"></a>密碼
-     **需要密碼** - 需要使用者輸入密碼才可存取該裝置。
    -     **必要的密碼類型** - 指定密碼是否只能是數字，或者是否必須為英數字元 (包含字母和數字)。 只有 Mac OS X 10.10.3 版與更新版本才支援這項設定。
    -     **密碼中的非英數字元數目** - 指定密碼中所需的複雜字元數 (**0** 到 **4**)。<br>複合字元是一種符號，例如 **?**。
    -     **密碼長度下限** - 輸入使用者必須設定的密碼長度下限 (介於 **4** 到 **16** 個字元之間)。
    -     **簡單密碼** - 允許使用簡單密碼，例如 **0000** 或 **1234**。
    -     **在螢幕鎖定最少幾分鐘後必須輸入密碼**- 指定電腦多長時間沒有活動後，即需要密碼才可解除鎖定。
    -     **沒有活動最久幾分鐘後鎖定螢幕** - 指定電腦必須閒置多長時間，螢幕才會鎖住。
    -     **密碼到期 (天)** - 指定使用者經過多少天後必須變更密碼 (**1** 到 **255** 天)。
    -     **避免重複使用以前用過的密碼** - 指定不可重複使用先前用過之密碼的次數 (**1** 到 **24**)。

## <a name="restricted-apps"></a>受限應用程式

您可以在受限制應用程式清單中，設定下列清單之一︰

**禁止的應用程式**清單 - 列出不允許使用者安裝與執行的應用程式 (並非由 Intune 管理)。
**核准的應用程式**清單 - 列出允許使用者安裝的應用程式。 若要保持相容，使用者絕不能安裝未列出的應用程式。 自動允許 Intune 所管理的應用程式。

若要設定清單，請按一下 [新增]，然後指定您所選的名稱，也可指定應用程式發行者以及應用程式的套件組合識別碼 (例如 *com.apple.calculator*)。




---
title: "服務台疑難排解入口網站 | Microsoft Docs"
titleSuffix: Intune Azure preview
description: "服務台人員使用疑難排解入口網站來解決使用者的技術問題"
keywords: 
author: NathBarn
ms.author: NathBarn
manager: angrobe
ms.date: 03/18/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1f39c02a-8d8a-4911-b4e1-e8d014dbce95
ms.reviewer: sumitp
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: e6bc22ccaf8c2c98cd67667f8fe30071ccdbc714
ms.contentlocale: zh-tw
ms.lasthandoff: 05/23/2017

---
# <a name="help-users-with-the-troubleshooting-portal-in-microsoft-intune"></a>使用 Microsoft Intune 中的疑難排解入口網站協助使用者

[!INCLUDE[azure_preview](./includes/azure_preview.md)]

疑難排解入口網站可讓服務台操作員和 Intune 系統管理員檢視使用者與其裝置，並執行工作以解決 Intune 技術問題。

## <a name="add-help-desk-operators"></a>新增服務台操作員
Intune 系統管理員可以將服務台操作員權限指派給使用者。 服務台使用者即可檢視 Intune 入口網站，但是無法檢視或執行疑難排解工作負載以外的系統管理工作。

1. 以 Intune 系統管理員的身分登入 [Azure 入口網站][](https:portal.azure.com)，選取 [更多服務] > [監視 + 管理] > [Intune]。
2. 在左側瀏覽刀鋒視窗中，選取 [Intune 角色]。
3. 在 [Intune 角色] 工作負載上，選取 [服務台操作員]，然後選取 [指派]。
4. 輸入 [指派名稱] (必要)、[指派描述] (選擇性)，然後指派 [成員 (群組)] 和 [範圍 (群組)]。
5. 「服務台操作員」角色的成員現在即可使用疑難排解入口網站。

如需 Intune 角色的詳細資訊，請參閱 [Intune 角色 (RBAC)](role-based-access-control.md)。

## <a name="access-the-troubleshooting-portal"></a>存取疑難排解入口網站

服務台人員和 Intune 系統管理員有兩種方式可以存取疑難排解入口網站：
- 在 [Azure 入口網站][](https://portal.azure.com) 中，選取 [更多服務] > [監視 + 管理] > [Intune]，然後在左側瀏覽刀鋒視窗中，選取 [疑難排解]。 其他工作負載會顯示在左側導覽刀鋒視窗中，但無法使用。

![Intune 疑難排解工作負載 (包含 [選取使用者] 連結) 的螢幕擷取畫面](media/help-desk-user.png)
- 在網頁瀏覽器中開啟 [http://aka.ms/intunetroubleshooting](http://aka.ms/intunetroubleshooting)。 只能看到疑難排解入口網站。

## <a name="use-the-troubleshooting-portal"></a>使用疑難排解入口網站

在疑難排解入口網站中，您可以選取 [選取使用者] 來檢視使用者的資訊。 使用者資訊可協助您了解使用者與其裝置的目前狀態。 疑難排解入口網站會顯示下列 Intune 使用者與裝置詳細資料︰
- 使用者帳戶資訊
- 使用者群組成員資格
- 裝置詳細資訊

服務台使用者也可以在裝置上執行「遠端鎖定」等遠端工作。


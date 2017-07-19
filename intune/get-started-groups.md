---
title: "開始使用群組"
titleSuffix: Intune on Azure
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 06/27/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 39a93fb5-d318-4997-a409-b64549a00e7a
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 04843a918a3c661ab69dfa711f4d22a8feedf5f3
ms.sourcegitcommit: fd2e8f6f8761fdd65b49f6e4223c2d4a013dd6d9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2017
---
# <a name="get-started-with-groups"></a>開始使用群組

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

[](./media/generic-users-groups.png)

Microsoft Intune 使用 Azure Active Directory (Azure AD) 來[管理公司資源存取](https://docs.microsoft.com/azure/active-directory/active-directory-manage-groups)。 這項存取是在目錄中使用角色來控制。 然後 Intune 會管理行動裝置的存取，這樣會允許該群組的成員存取資源。

__如何建立群組？__

1. 登入 [Azure 入口網站](https://portal.azure.com)。
2. 使用 [搜尋資源]，搜尋 [使用者和群組]。
3. 一旦您開啟 [使用者和群組] 刀鋒視窗，請選取 [所有群組]。
4. 在 [使用者和群組 - 所有群組] 刀鋒視窗中，選取 [新增群組] 命令。
5. 在 [群組] 刀鋒視窗中，新增群組的 [名稱] 和 [描述]。
6. 將 [成員資格類型] 設定為 [指派]。 請不要為測試群組 [啟用 Office 功能]。
7. 按一下 **建立**。

如果您已成功建立群組，它應該會出現在 [所有群組] 清單中。 如果未出現，請嘗試建立另一個群組。

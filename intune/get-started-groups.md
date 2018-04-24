---
title: 在 Microsoft Intune 中建立群組
titleSuffix: ''
description: 將使用者組織成群組，以更輕鬆地管理他們可存取的原則和應用程式。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/26/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 39a93fb5-d318-4997-a409-b64549a00e7a
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: d039cfe5509990ff15fe8a1cb476ad44037d60df
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="create-a-group-to-manage-your-users-and-data-access"></a>建立群組來管理您的使用者和資料存取

群組是用來管理您的使用者，以及控制您的員工對公司資源的存取。 這些資源可以是您目錄的一部分，也可以是外部資源，例如 SaaS 應用程式或 SharePoint 網站。

Microsoft Intune 使用 Azure Active Directory (Azure AD) 來管理公司資源存取權。 這項存取是在目錄中使用角色來控制。 然後 Intune 會管理行動裝置的存取，這樣會允許該群組的成員存取資源。

## <a name="how-do-i-create-a-group"></a>如何建立群組？

1. 登入 [Azure 入口網站](https://portal.azure.com)。
2. 選擇 [All services] (所有服務) > [Intune]。 Intune 位於 [Monitoring + Management] (監視 + 管理) 區段。
3. 在您開啟 [Microsoft Intune] 窗格之後，請選取 [群組]。
4. 在 [使用者和群組 - 所有群組] 窗格中，選取 [新增群組] 命令。
5. 在 [群組] 窗格中，選擇 [群組類型]。
5. 新增群組的 [名稱] 和 [描述]。
6. 將 [成員資格類型] 設定為 [指派]。 請不要為測試群組 [啟用 Office 功能]。
7. 選取群組的 [成員]。
7. 按一下 [建立]。

如果您已成功建立群組，它應該會出現在 [所有群組] 清單中。 如果未出現，請嘗試建立另一個群組。

## <a name="next-steps"></a>接下來的步驟

[開始使用原則](get-started-policies.md) - 建立原則，以防止使用者透過其裝置執行未經授權的動作。

## <a name="learn-more"></a>深入了解

* [在 Intune 中使用群組設定註冊限制](groups-add.md)
* [使用 Azure Active Directory 群組來管理公司資源存取權](https://docs.microsoft.com/azure/active-directory/active-directory-manage-groups)

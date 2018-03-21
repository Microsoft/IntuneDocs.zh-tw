---
title: "如何將 Windows 市集應用程式新增至 Microsoft Intune"
titleSuffix: 
description: "了解如何將 Windows 市集應用程式新增至 Microsoft Intune。"
keywords: 
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/06/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 07241b6d-86d8-4abb-83a2-3fc5feae5788
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 2e2280ad72bbd353d80af316cde436e8ffc79d1f
ms.sourcegitcommit: 8a235b7af6ec3932c29a76d0b1aa481d983054bc
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2018
---
# <a name="how-to-add-windows-store-apps-to-microsoft-intune"></a>如何將 Windows 市集應用程式新增至 Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

您必須先將應用程式新增至 Intune，才可以指派、監視、設定或保護它們。 下列步驟可讓您將 Windows 市集應用程式新增至 Microsoft Intune。

1. 登入 [Azure 入口網站](https://portal.azure.com)。
2. 選擇 [All services] (所有服務) > [Intune]。 Intune 位於 [監視 + 管理] 區段。
3. 在 [Intune] 窗格中，選擇 [行動應用程式]。
4. 在**行動應用程式**工作負載中選擇 [管理]  >  [應用程式]。
5. 從應用程式清單上方選擇 [新增]。
6. 在 [新增應用程式] 窗格中，選擇 [Windows] 的 [應用程式類型]，並選擇 [應用程式資訊]。
7. 在 [應用程式資訊] 窗格中，設定下列資訊。 完成設定後，按一下 [確定]。 窗格中某些值會隨所選的應用程式自動填入︰
    - **名稱** - 輸入要顯示在公司入口網站中的應用程式名稱。 確定您使用的所有應用程式名稱都是唯一的。 如果有重複的應用程式名稱，使用者只會在公司入口網站中看到其中一個應用程式。
    - **描述** - 輸入公司入口網站中要向使用者顯示的應用程式描述。
    - **發行者** - 輸入應用程式的發行者名稱。
    - **Appstore URL** - 輸入您要建立之應用程式的應用程式市集 URL。
    - **類別 (選用)** - 選取一或多個內建應用程式類別，或您建立的類別，方便使用者在瀏覽公司入口網站時尋找應用程式。
    - **將此顯示為公司入口網站中的精選應用程式** - 當使用者瀏覽應用程式時，以醒目方式在公司入口網站的主頁面上顯示此應用程式。
    - **資訊 URL** - 選擇是否要輸入包含此應用程式相關資訊的網站 URL。 使用者會在公司入口網站中看到這個 URL。
    - **隱私權 URL** - 選擇是否要輸入包含此應用程式之隱私權資訊的網站 URL。 使用者會在公司入口網站中看到這個 URL。
    - **開發人員** - 選擇是否要輸入應用程式開發人員的姓名。
    - **擁有者** - 選擇是否要輸入此應用程式的擁有者名稱，例如**人力資源部門**。
    - **注意** - 輸入要與此應用程式相關聯的附註。
    - **標誌** -- 上傳將與應用程式建立關聯的圖示。 這是使用者瀏覽公司入口網站時，會隨應用程式一起顯示的圖示。
8. 完成之後，請在 [新增應用程式] 窗格中選擇 [新增]。

您建立的應用程式將會顯示在應用程式清單中，而您可從中將應用程式指派給您選擇的群組。 

## <a name="next-steps"></a>接下來的步驟

- [如何將應用程式指派到群組](apps-deploy.md)
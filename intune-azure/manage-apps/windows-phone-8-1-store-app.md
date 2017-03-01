---
title: "如何將 Windows Phone 8.1 市集應用程式新增至 Intune | Intune Azure 預覽版 | Microsoft Docs"
description: "Intune Azure 預覽版︰了解如何將 Windows Phone 8.1 市集應用程式新增至 Intune。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4a95e575-2c63-4bfc-b9c4-f0a132eef618
ms.reviewer: mghadial
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b4d095506215b775d56d172e9aabae1737757310
ms.openlocfilehash: 4a08e0ac90faa0715172e7c5355b474822536afe
ms.lasthandoff: 02/16/2017

---

# <a name="how-to-add-windows-phone-81-store-apps-to-microsoft-intune"></a>如何將 Windows Phone 8.1 市集應用程式新增至 Microsoft Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]


1. 登入 Azure 入口網站。
2. 選擇 [更多服務]  >  [監視 + 管理]  >  [Intune]。
3. 在 **Intune** 刀鋒視窗上選擇 [管理應用程式]。
4. 在**行動應用程式**工作負載中選擇 [管理]  >  [應用程式]。
5. 從應用程式清單上方選擇 [新增]。
6. 在 [新增應用程式] 刀鋒視窗中選擇 [應用程式資訊]。
7. 在 [編輯應用程式] 刀鋒視窗中設定下列資訊。 完成設定後，按一下 [新增]。 刀鋒視窗中有一些值會隨所選的應用程式自動填入︰
    - **名稱** - 輸入要顯示在公司入口網站中的應用程式名稱。 確定您使用的所有應用程式名稱都是唯一的。 如果有重複的應用程式名稱，使用者只會在公司入口網站中看到其中一個應用程式。
    - **描述** - 輸入應用程式的描述。 使用者會在公司入口網站中看到這個描述。
    - **發行者** - 輸入應用程式的發行者名稱。
    - **App Store URL** - 輸入您要建立之應用程式的 App Store URL。
    - **最小作業系統** - 從清單中選擇應用程式所能安裝的最小作業系統版本。 若將應用程式指派給安裝舊版作業系統的裝置，就不會進行安裝。
    - **類別 (選用)** - 選取一或多個內建應用程式類別，或選取您建立的類別。 這可以讓使用者在瀏覽公司入口網站時，更輕鬆地找到應用程式。
    - **將此顯示為公司入口網站中的精選應用程式** - 當使用者瀏覽應用程式時，以醒目方式在公司入口網站的主頁面上顯示此應用程式。
    - **資訊 URL** - 選擇是否要輸入包含此應用程式相關資訊的網站 URL。 使用者會在公司入口網站中看到這個 URL。
    - **隱私權 URL** - 選擇是否要輸入包含此應用程式之隱私權資訊的網站 URL。 使用者會在公司入口網站中看到這個 URL。
    - **開發人員** - 選擇是否要輸入應用程式開發人員的姓名。
    - **擁有者** - 選擇是否要輸入此應用程式的擁有者名稱，例如**人力資源部門**。
    - **注意** - 輸入要與此應用程式相關聯的附註。
    - **上傳圖示** - 上傳應用程式所要關聯的圖示。 這是使用者瀏覽公司入口網站時，會隨應用程式一起顯示的圖示。
8. 完成之後，請在 [新增應用程式] 刀鋒視窗中選擇 [儲存]。

您建立的應用程式將會顯示在應用程式清單中，而您可從中將應用程式指派給您選擇的群組。 如需協助，請參閱[如何將應用程式指派給群組](/intune-azure/manage-apps/deploy-apps)。

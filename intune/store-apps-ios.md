---
title: 如何將 iOS 市集應用程式新增至 Microsoft Intune
titlesuffix: ''
description: 了解如何將 iOS 市集應用程式新增至 Microsoft Intune。
keywords: Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/06/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: c59514d7-1256-4576-9380-e7a0b85a0378
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 4eaa4b279ab98c6fe41482628937e0f2b0dc70a5
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-add-ios-store-apps-to-microsoft-intune"></a>如何將 iOS 市集應用程式新增至 Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

使用本文中的資訊，協助您將 iOS 市集應用程式新增至 Microsoft Intune。 iOS 市集應用程式就是 Intune 安裝於使用者裝置的應用程式。 使用者是您公司的員工。 會自動更新 iOS 市集應用程式。

>[!NOTE]
>雖然 iOS 裝置的使用者可以移除部分內建的 iOS 應用程式 (如股票和地圖)，但您無法使用 Intune 來重新部署這些應用程式。 如果使用者刪除這些應用程式，則必須移至應用程式市集，並手動重新進行安裝。

## <a name="before-you-start"></a>開始之前

如果應用程式在應用程式市集中是免費的，您只能使用這個方法指派應用程式。 如果您想要使用 Intune 指派付費應用程式，請考慮使用 [iOS 大量採購方案](vpp-apps-ios.md)。

>[!NOTE]
>使用 Microsoft Intune 時，建議的瀏覽器是 Chrome 與 Edge。

1. 登入 [Azure 入口網站](https://portal.azure.com)。
2. 選擇 [All services] (所有服務) > [Intune]。 Intune 位於 [Monitoring + Management] (監視 + 管理) 區段。
3. 在 [Intune] 刀鋒視窗上，選擇 [行動應用程式]。
4. 在 [Mobile Apps] 工作負載中，選擇 [管理] 區段下的 [應用程式]。
5. 選擇 [應用程式] 窗格右側的 [新增]。
6. 在 [應用程式類型] 清單中，選取可用 [市集應用程式] 類型下的 [iOS]。
7. 選擇 [Search the App Store] (搜尋應用程式市集)。
8. 在 [Search the App Store] (搜尋應用程式市集) 刀鋒視窗中，選取 App Store 國家地區設定。
9. 在 [搜尋] 方塊中鍵入名稱 (或部分名稱)。 Intune 會搜尋市集，並傳回一份相關的結果。
10. 請從清單中，選擇您想要的應用程式，然後按一下 [選取]。
11. 在 [新增應用程式] 刀鋒視窗中，選擇 [應用程式資訊] 來設定應用程式。
12. 在 [應用程式資訊] 刀鋒視窗中，新增應用程式資訊。 刀鋒視窗中有一些值會隨所選的應用程式自動填入︰
    - **名稱** - 鍵入要顯示在公司入口網站中的應用程式名稱。 確定您使用的所有應用程式名稱都是唯一的。 如果有重複的應用程式名稱，公司入口網站只會顯示其中一個應用程式給使用者。
    - **描述** - 鍵入公司入口網站中要向使用者顯示的應用程式描述。
    - **發行者** - 鍵入應用程式的發行者名稱。
    - **App Store URL** - 鍵入您要建立之應用程式的 App Store URL。
    - **最小作業系統** - 從清單中選擇應用程式所能安裝的最小作業系統版本。 應用程式不會安裝在舊版作業系統的裝置上。
    - **適用的裝置類型** - 從清單中，選擇應用程式所使用的裝置。
    - **類別** (選用)。 選取一或多個內建應用程式類別，或選取您建立的類別。 類別可以讓使用者在瀏覽公司入口網站時，更輕鬆地找到應用程式。
    - **將此顯示為公司入口網站中的精選應用程式** -- 當使用者瀏覽應用程式時，以醒目方式在公司入口網站的主頁面上顯示此應用程式。
    - **資訊 URL** -- 選擇是否要鍵入包含此應用程式相關資訊的網站 URL。 使用者會在公司入口網站中看到這個 URL。
    - **隱私權 URL** -- 選擇是否要鍵入包含此應用程式之隱私權資訊的網站 URL。 使用者會在公司入口網站中看到這個 URL。
    - **開發人員** -- 選擇是否要鍵入應用程式開發人員的姓名。 這個欄位只有系統管理員看得到，使用者看不到。
    - **擁有者** -- 選擇是否要鍵入此應用程式的擁有者名稱，例如**人力資源部門**。  這個欄位只有系統管理員看得到，使用者看不到。
    - **注意** -- 鍵入要與此應用程式建立關聯的附註。 這個欄位只有系統管理員看得到，使用者看不到。
    - **標誌** -- 上傳將與應用程式建立關聯的圖示。 這是使用者瀏覽公司入口網站時，會隨應用程式一起顯示的圖示。
13. 完成後，請按一下 [新增資訊] 刀鋒視窗上的 [確定]。
14. 按一下 [新增應用程式] 刀鋒視窗上的 [新增]。

您建立的應用程式會顯示在應用程式清單中，而您可從中將應用程式指派給您選擇的群組。

## <a name="next-steps"></a>接下來的步驟

- [如何將應用程式指派到群組](apps-deploy.md)

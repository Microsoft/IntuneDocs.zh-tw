---
title: 將 Windows Phone 8.1 市集應用程式新增至 Microsoft Intune
titleSuffix: ''
description: 本主題說明如何將 Windows Phone 8.1 市集應用程式新增至 Microsoft Intune。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/22/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 4a95e575-2c63-4bfc-b9c4-f0a132eef618
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: d43e0f913020e3e2e8b0ac463d5983447d7c1fa2
ms.sourcegitcommit: 139853f8d6ea61786da7056cfb9024a6459abd70
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/26/2020
ms.locfileid: "76754944"
---
# <a name="add-windows-phone-81-store-apps-to-microsoft-intune"></a>將 Windows Phone 8.1 市集應用程式新增至 Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

在您將應用程式指派給一部裝置或一群使用者之前，必須先將該應用程式新增到 Microsoft Intune。 

## <a name="add-an-app-to-intune"></a>將應用程式新增至 Intune
您可以採取下列步驟，透過 Azure 入口網站，將 Windows Phone 8.1 市集應用程式新增到 Intune：

1. 登入 [Microsoft 端點管理員系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。
2. 選取 [應用程式]   > [所有應用程式]   > [新增]  。
3. 在 [選取應用程式類型]  窗格中，在可用的 [市集應用程式]  類型下，選取 [Windows Phone 8.1 市集應用程式]  。
4. 按一下 [選取]  。<br>
   [新增應用程式]  步驟隨即顯示。
5. 若要針對 Windows Phone 8.1 市集應用程式設定 [應用程式資訊]  ，請瀏覽至 [Microsoft Store](https://www.microsoft.com/store/apps/windows-phone)，並搜尋您想要部署的應用程式。 顯示應用程式頁面，並記下應用程式詳細資料。 
6. 在 [應用程式資訊]  頁面中，新增應用程式詳細資料：
    - **名稱**：輸入要在公司入口網站中顯示的應用程式名稱。 您使用的任何應用程式名稱都必須是唯一的。 如果應用程式名稱重複，則使用者只會在公司入口網站看到一個名稱。
    - **描述**：輸入應用程式的描述。 使用者會在公司入口網站上看到這項描述。
    - **發行者**：輸入應用程式發行者的名稱。
    - **AppStore URL**：輸入您想要建立之應用程式的 App Store URL。
    - **類別**：(選擇性) 選取一或多個內建的應用程式類別，或選取您建立的類別。 這麼做的話，當使用者在瀏覽公司入口網站時，可以更輕鬆地找到應用程式。
    - **將此顯示為公司入口網站中的精選應用程式**：若要在使用者瀏覽應用程式時，於公司入口網站的主頁面上以醒目方式顯示應用程式套件，請選取此選項。
    - **資訊 URL**：(選用) 輸入包含此應用程式相關資訊的網站 URL。 使用者會在公司入口網站中看到這個 URL。
    - **隱私權 URL**：(選擇性) 輸入包含這個應用程式之隱私權資訊的網站 URL。 使用者會在公司入口網站中看到這個 URL。
    - **開發人員**：(選擇性) 輸入應用程式開發人員的姓名。
    - **擁有者**：(選擇性) 輸入此應用程式的擁有者名稱，例如「人力資源部門」  。
    - **附註**：(選擇性) 輸入要與此應用程式建立關聯的任何附註。
    - **標誌**：(選擇性) 上傳將與應用程式建立關聯的圖示。 這是使用者瀏覽公司入口網站時，會隨應用程式一起顯示的圖示。
7. 按一下 [下一步]  以顯示 [範圍標籤]  頁面。
8. 按一下 [選取範圍標籤]  來選擇性地為應用程式新增範圍標籤。 如需詳細資訊，請參閱[針對分散式 IT 使用角色型存取控制 (RBAC) 和範圍標籤](~/fundamentals/scope-tags.md)。
9. 按一下 [下一步]  以顯示 [指派]  頁面。
10. 為應用程式選取群組指派。 如需詳細資訊，請參閱[新增群組來組織使用者與裝置](~/fundamentals/groups-add.md)。 
11. 按一下 [下一步]  以顯示 [檢閱 + 建立]  頁面。 檢閱您針對應用程式所輸入的值和設定。
12. 當您完成時，請按一下 [建立]  以將應用程式新增到 Intune。

您所建立之應用程式的 [概觀]  刀鋒視窗隨即顯示。


您建立的應用程式即會顯示在應用程式清單中，而您可從中將該應用程式指派給所選的群組。

## <a name="next-steps"></a>後續步驟

- [將應用程式指派給群組](apps-deploy.md)

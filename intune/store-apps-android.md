---
title: 將 Android 市集應用程式新增至 Microsoft Intune
titleSuffix: ''
description: 了解如何將 Google Play 商店的 Android 市集應用程式新增到 Microsoft Intune。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/19/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4433000a-23e9-4cad-a818-48c28eedc1f5
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 2391f6ec7de5a9d1b4d544f1ca07fd9f4e58ace8
ms.sourcegitcommit: 4e69a8664c289263490daa4c02bc6b81c33196e5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/20/2018
ms.locfileid: "53642400"
---
# <a name="add-android-store-apps-to-microsoft-intune"></a>將 Android 市集應用程式新增至 Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

在您將應用程式指派給一部裝置或一群使用者之前，必須先將該應用程式新增到 Microsoft Intune。 

## <a name="add-an-app"></a>加入應用程式

您可以採取下列步驟，透過 Azure 入口網站，將 Android 市集應用程式新增至 Intune：

1. 登入 [Azure 入口網站](https://portal.azure.com)。
2. 選取 [所有服務] > [Intune]。  
    Intune 位於 [Monitoring + Management] (監視 + 管理) 區段。
3. 在 [Intune] 窗格中，選取 [用戶端應用程式]。
4. 在 [用戶端應用程式] 工作負載窗格中的 [管理] 下，選取 [應用程式]。
5. 選取 [新增]。
6. 在 [新增應用程式] 窗格中，選取可用 [市集應用程式] 類型下的 [Android]。
7. 若要設定應用程式資訊，請選取 [設定]，然後提供下列資訊。 針對 Android 應用程式，巡覽至 [Google Play 商店](https://play.google.com/store)，並搜尋您想要部署的應用程式。 選取應用程式，並記下應用程式詳細資料。 根據您選擇的應用程式，某些值可能已自動填入。
    - **名稱**：輸入要顯示在公司入口網站中的應用程式名稱。 您使用的任何應用程式名稱都必須是唯一的。 如果應用程式名稱重複，則使用者只會在公司入口網站看到一個名稱。
    - **描述**：輸入應用程式的描述。 使用者會在公司入口網站上看到這項描述。
    - **發行者**：輸入應用程式發行者的名稱。
    - **Appstore URL**：輸入您要建立之應用程式的應用程式市集 URL。
    - **最低作業系統**：在清單中選取能夠安裝應用程式的最早作業系統版本。 若將應用程式指派給安裝舊版作業系統的裝置，就不會進行安裝。
    - **類別**：您可以選擇性地選取一或多個內建應用程式類別，或您自己建立的類別。 這麼做的話，當使用者在瀏覽公司入口網站時，可以更輕鬆地找到應用程式。
    - **將此顯示為公司入口網站中的精選應用程式**：選取此選項，當使用者瀏覽應用程式時，在公司入口網站的主頁面上，以突顯的方式顯示應用程式套件。
    - **資訊 URL**：(選用) 輸入包含此應用程式相關資訊的網站 URL。 使用者會在公司入口網站中看到這個 URL。
    - **隱私權 URL**：(選擇性) 輸入包含這個應用程式之隱私權資訊的網站 URL。 使用者會在公司入口網站中看到這個 URL。
    - **開發人員**：選擇是否要輸入應用程式開發人員的姓名。
    - **擁有者**：選擇是否要輸入此應用程式的擁有者名稱，例如「人力資源部門」。
    - **附註**：選擇是否要輸入與此應用程式相關聯的任何附註。
    - **標誌**：您可以選擇性地上傳要與應用程式建立關聯的圖示。 這是使用者瀏覽公司入口網站時，會隨應用程式一起顯示的圖示。
1. 選取 [確定]。
2. 選取 [新增]。

您建立的應用程式即會顯示在應用程式清單中，而您可從中將該應用程式指派給所選的群組。 

## <a name="next-steps"></a>接下來的步驟

- [將應用程式指派給群組](apps-deploy.md)

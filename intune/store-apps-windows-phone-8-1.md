---
title: 將 Windows Phone 8.1 市集應用程式新增至 Microsoft Intune
titleSuffix: ''
description: 了解如何將 Windows Phone 8.1 Microsoft Store 應用程式新增至 Microsoft Intune。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 09/19/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4a95e575-2c63-4bfc-b9c4-f0a132eef618
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 47861e95a016338447091e4fcaffdda3e199eee7
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2018
ms.locfileid: "52182749"
---
# <a name="add-windows-phone-81-store-apps-to-microsoft-intune"></a>將 Windows Phone 8.1 市集應用程式新增至 Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

在您將應用程式指派給一部裝置或一群使用者之前，必須先將該應用程式新增到 Microsoft Intune。 

## <a name="add-an-app-to-intune"></a>將應用程式新增至 Intune
您可以採取下列步驟，透過 Azure 入口網站，將 Windows Phone 8.1 市集應用程式新增到 Intune：

1. 登入 [Azure 入口網站](https://portal.azure.com)。
2. 選取 [所有服務] > [Intune]。  
    Intune 位於 [Monitoring + Management] (監視 + 管理) 區段。
3. 在 [Intune] 窗格中，選取 [用戶端應用程式]。
4. 在 [用戶端應用程式] 工作負載窗格中的 [管理] 下，選取 [應用程式]。
5. 在 [應用程式] 窗格中，選取 [新增]。
6. 在 [新增應用程式] 窗格的 [應用程式類型] 中，選取 [Windows Phone 8.1]，然後選取 [應用程式資訊]。
7. 在 [應用程式資訊] 窗格中，新增應用程式資訊。 窗格中某些值會隨所選的應用程式自動填入︰
    - **名稱**：輸入要在公司入口網站中顯示的應用程式名稱。 您使用的任何應用程式名稱都必須是唯一的。 如果應用程式名稱重複，則使用者只會在公司入口網站看到一個名稱。
    - **描述**：輸入應用程式的描述。 使用者會在公司入口網站上看到這項描述。
    - **發行者**：輸入應用程式的發行者名稱。
    - **App Store URL**：鍵入您要建立之應用程式的 App Store URL。
    - **類別**：您可以選取一或多個內建的應用程式類別，或您自己建立的類別。 這麼做的話，當使用者在瀏覽公司入口網站時，可以更輕鬆地找到應用程式。
    - **將此顯示為公司入口網站中的精選應用程式**：若選取此選項，當使用者瀏覽應用程式時，應用程式套件會醒目地顯示在公司入口網站的主頁面上。
    - **資訊 URL**：選擇是否要輸入包含此應用程式相關資訊的網站 URL。 使用者會在公司入口網站中看到這個 URL。
    - **隱私權 URL**：選擇是否要輸入包含此應用程式隱私權資訊的網站 URL。 使用者會在公司入口網站中看到這個 URL。
    - **開發人員**：選擇是否要輸入應用程式開發人員的姓名。
    - **擁有者**：您可以選擇性地輸入此應用程式的擁有者名稱 (例如「人力資源部門」)。
    - **注意**：選擇是否要輸入與此應用程式相關聯的任何附註。
    - **標誌**：您可以選擇性地上傳要與應用程式建立關聯的圖示。 這是使用者瀏覽公司入口網站時，會隨應用程式一起顯示的圖示。
8. 選取 [確定]。
9. 選取 [新增]。

您建立的應用程式即會顯示在應用程式清單中，而您可從中將該應用程式指派給所選的群組。

## <a name="next-steps"></a>接下來的步驟

- [將應用程式指派給群組](apps-deploy.md)

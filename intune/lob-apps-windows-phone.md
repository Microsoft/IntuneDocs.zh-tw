---
title: 將 Windows Phone 企業營運應用程式新增至 Microsoft Intune
titlesuffix: ''
description: 了解如何使用 Microsoft Intune 來新增 Windows Phone 企業營運 (LOB) 應用程式。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/11/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: a097b7b2-d01d-454b-954c-da4f3cd0ae86
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 9fa39f212c9979a9986bba5537f0c9a2b5e01c8c
ms.sourcegitcommit: 4e69a8664c289263490daa4c02bc6b81c33196e5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/20/2018
ms.locfileid: "53642637"
---
# <a name="add-a-windows-phone-line-of-business-app-to-microsoft-intune"></a>將 Windows Phone 企業營運應用程式新增至 Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

使用此文章中的資訊，將 Windows Phone 企業營運 (LOB) 應用程式新增至 Microsoft Intune。 LOB 應用程式是您從應用程式安裝檔案新增的應用程式。 這類應用程式通常是在內部撰寫的。 Intune 會將 LOB 應用程式安裝在使用者的裝置上。 

## <a name="step-1-specify-the-software-setup-file"></a>步驟 1：指定軟體安裝檔

1. 登入 [Azure 入口網站](https://portal.azure.com)。
2. 選取 [所有服務] > [Intune]。 Intune 位於 [監視 + 管理] 區段。
3. 在 [Intune] 窗格中，選取 [用戶端應用程式]。
4. 在 [用戶端應用程式] 工作負載中，選取 [管理] > [應用程式]。
5. 從應用程式清單上方，選取 [新增]。
6. 在 [新增應用程式] 窗格中，選取 [企業營運應用程式]。

## <a name="step-2-configure-the-app-package-file"></a>步驟 2：設定應用程式套件檔案

1. 在 [新增應用程式] 窗格中，選取 [應用程式套件檔案]。
2. 在 [應用程式套件檔案] 窗格中，選取 [瀏覽] 按鈕。 然後選取副檔名為 **.xap** 的 Windows Phone 安裝檔案。
3. 完成後，按一下 [確定]。


## <a name="step-3-configure-app-information"></a>步驟 3：設定應用程式資訊

1. 在 [新增應用程式] 窗格中，選取 [應用程式資訊]。
2. 在 [應用程式資訊] 窗格中，設定應用程式資訊。 窗格中某些值會隨著所選的應用程式自動填入。
    - **名稱**：輸入在公司入口網站中顯示的應用程式名稱。 確定您使用的所有應用程式名稱都是唯一的。 如果有重複的應用程式名稱，只有一個應用程式會出現在公司入口網站中。
    - **描述**：輸入應用程式的描述。 此描述會出現在公司入口網站上。
    - **發行者**：輸入應用程式發行者的名稱。
    - **類別**：選取一或多個內建的應用程式類別，或選取您建立的類別。 類別可以讓使用者在瀏覽公司入口網站時，更輕鬆地找到應用程式。
    - **將此顯示為公司入口網站中的精選應用程式**：當使用者瀏覽應用程式時，在公司入口網站的主頁面上，以突顯的方式顯示應用程式。
    - **資訊 URL**：(選擇性) 輸入包含此應用程式相關資訊的網站 URL。 此 URL 會出現在公司入口網站上。
    - **隱私權 URL**：(選擇性) 輸入包含這個應用程式之隱私權資訊的網站 URL。 此 URL 會出現在公司入口網站上。
    - **開發人員**：(選擇性) 輸入應用程式開發人員的姓名。
    - **擁有者**：(選擇性) 輸入此應用程式之擁有者的名稱。 **人力資源部門**就是一個例子。
    - **附註**：輸入要與此應用程式建立關聯的任何附註。
    - **標誌**：上傳與應用程式相關聯的圖示。 這是使用者瀏覽公司入口網站時，會隨應用程式一起顯示的圖示。
3. 完成後，按一下 [確定]。

## <a name="step-4-finish-up"></a>步驟 4：完成

1. 在 [新增應用程式] 窗格中，確認您所設定的資訊正確無誤。
2. 選取 [新增]，將應用程式上傳至 Intune。

## <a name="next-steps"></a>接下來的步驟

- 您所建立的應用程式會出現在應用程式清單中。 您現在可以將它指派給您選擇的群組。 如需協助，請參閱[如何將應用程式指派給群組](apps-deploy.md)。

- 深入了解您可用來監視應用程式屬性和指派的方式。 請參閱[如何監視應用程式資訊和指派](apps-monitor.md)。

- 深入了解您應用程式在 Intune 中的內容。 請參閱[裝置和應用程式生命週期的概觀](introduction-device-app-lifecycles.md)。

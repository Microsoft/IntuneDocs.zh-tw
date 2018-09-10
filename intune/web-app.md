---
title: 將 Web 應用程式新增至 Microsoft Intune
titleSuffix: ''
description: 了解如何將 Web 應用程式新增至 Microsoft Intune。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 05/15/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 5f08752f-0e87-4ad9-a34c-4991b3150775
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: ec483218cb86426b237c40c8831a2f0880847ade
ms.sourcegitcommit: 2d1e89fa5fa721e79648e41fde147a035e7b047d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/31/2018
ms.locfileid: "43347452"
---
# <a name="add-web-apps-to-microsoft-intune"></a>將 Web 應用程式新增至 Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune 支援各種不同的應用程式類型，包括 Web 應用程式。 Web 應用程式是主從式應用程式。 伺服器提供了 Web 應用程式，其中包括 UI、內容和功能。 此外，現代的 Web 裝載平台通常具有安全性、負載平衡以及其他優勢。 Web 應用程式會在網路上進行個別維護。 您可以使用 Microsoft Intune 指向此應用程式類型。 您也可以指派哪些使用者群組可以存取這個應用程式。 

在您可以管理並指派應用程式給使用者之前，請將該應用程式新增至 Intune。 Intune 會在使用者的裝置主畫面上建立 Web 應用程式捷徑。

> [!Note]
> Android 工作設定檔裝置和 macOS 並不支援 Web 應用程式。

## <a name="add-a-web-app-to-intune"></a>將 Web 應用程式新增至 Intune
您可以執行下列動作，將應用程式新增至 Intune 以作為該應用程式的網路捷徑：

1. 登入 [Azure 入口網站](https://portal.azure.com)。
2. 選取 [所有服務] > [Intune]。  
    Intune 位於 [Monitoring + Management] (監視 + 管理) 區段。
3. 在 [Intune] 窗格中，選取 [用戶端應用程式]。
4. 在 [用戶端應用程式] 工作負載窗格中的 [管理] 下，選取 [應用程式]。
5. 在 [應用程式] 窗格中，選取 [新增]。
6. 在 [新增應用程式] 窗格的 [應用程式類型] 下拉式清單中，選取 [Web 連結] 類型。
7. 選取 [設定]。
8. 在 [應用程式資訊] 窗格中，新增下列資訊：
    - **名稱**：輸入要顯示在公司入口網站中的應用程式名稱。 
    
        > [!NOTE]
        > 若您在部署並安裝應用程式之後透過 Intune Azure 入口網站變更應用程式名稱，將無法再使用命令定位應用程式。
    
    - **描述**：輸入應用程式的描述。 使用者會在公司入口網站上看到這項描述。
    - **發行者**：輸入應用程式的發行者名稱。
    - **應用程式 URL**：輸入裝載您要指派之應用程式的網站 URL。
    - **類別**：您可以選取一或多個內建的應用程式類別，或您自己建立的類別。 這麼做的話，當使用者在瀏覽公司入口網站時，可以更輕鬆地找到應用程式。
    - **將此顯示為公司入口網站中的精選應用程式**：若選取此選項，當使用者瀏覽應用程式時，應用程式套件會醒目地顯示在公司入口網站的主頁面上。
    - **必須是受控瀏覽器，才可開啟此連結**：選取此選項時，可將網站或 Web 應用程式的連結指派給使用者，以讓他們在 Intune Managed Browser 中開啟連結。 他們的裝置上必須安裝此瀏覽器。
    - **標誌**：上傳要與應用程式建立關聯的圖示。 這是使用者瀏覽公司入口網站時，會隨應用程式一起顯示的圖示。
9. 選取 [確定]。
10. 在 [新增應用程式] 窗格中，選取 [新增]。

> [!Note]
> 使用者必須將 Intune Widget 新增至主畫面，才能顯示已指派給 Android 裝置的 Web 應用程式。

## <a name="next-steps"></a>接下來的步驟

您建立的應用程式即會顯示在應用程式清單中，而您可從中將該應用程式指派給所選的群組。 如需相關說明，請參閱[將應用程式指派給群組](apps-deploy.md)。 

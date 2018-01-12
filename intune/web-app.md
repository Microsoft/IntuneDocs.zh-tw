---
title: "如何將 Intune Web 應用程式新增到 Intune"
titleSuffix: Azure portal
description: "了解如何將 Web 應用程式新增至 Intune。"
keywords: 
author: erikre
ms.author: erikre
manager: angrobe
ms.date: 12/06/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5f08752f-0e87-4ad9-a34c-4991b3150775
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 6da1441b16a43b5e22bedd9e87970f3388b11b9e
ms.sourcegitcommit: a3a744ea55f38a360ca9f788c77a5b3018d1add5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/30/2017
---
# <a name="how-to-add-web-apps-to-microsoft-intune"></a>如何將 Web 應用程式新增至 Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

在您可以管理並指派應用程式給使用者之前，請將該應用程式新增至 Intune。 Intune 支援各種不同的應用程式類型，包括 Web 應用程式。

> [!Note]
> Android for Work 裝置上並不支援 Web 應用程式。

完成下列步驟以將應用程式新增至 Intune，作為該應用程式於網路上的捷徑：

1. 登入 Azure 入口網站。
2. 使用 [更多資源]，搜尋 **Intune** 並選取它。
3. 在 [Microsoft Intune] 刀鋒視窗上，選取 [行動應用程式]。
4. 在 [行動應用程式] 刀鋒視窗上，選取 [應用程式]。
5. 從應用程式清單上方，選取 [新增]。 [新增應用程式] 刀鋒視窗隨即顯示。
6. 在 [新增應用程式] 刀鋒視窗中，從 [新增類型] 下拉式清單中選取 [Web 應用程式]。
7. 選取 [設定] 選項以顯示 [應用程式資訊] 刀鋒視窗。
8. 在 [應用程式資訊] 刀鋒視窗中，新增下列資訊：
    - **名稱** - 輸入要顯示在公司入口網站中的應用程式名稱。
    - **描述** - 輸入應用程式的描述。 這會對公司入口網站中的使用者顯示。
    - **發行者** - 輸入應用程式的發行者名稱。
    - **應用程式 URL** - 輸入裝載您要指派之應用程式的網站 URL。
    - **類別 (選用)** - 選取一或多個內建應用程式類別，或選取您建立的類別。 此選項可以讓使用者在瀏覽公司入口網站時，更輕鬆地找到應用程式。
    - **將此顯示為公司入口網站中的精選應用程式** - 當使用者瀏覽應用程式時，以醒目方式在公司入口網站的主頁面上顯示此應用程式。
    - **需要受管理的瀏覽器以開啟此連結** - 當您將網站或 Web 應用程式的連結指派給使用者時，他們可以在受 Intune 管理的瀏覽器中開啟該連結。 他們的裝置上必須安裝此瀏覽器。
    - **標誌** -- 上傳與應用程式關聯的標誌。 此標誌是使用者瀏覽公司入口網站時，會隨應用程式一起顯示的標誌。
9. 完成後，請在 [新增資訊] 刀鋒視窗上選取 [確定]。
10. 接著，從 [新增應用程式] 刀鋒視窗選取 [新增]。

您建立的應用程式會顯示在應用程式清單中，而您可從中將該應用程式指派給您選擇的群組。 如需協助，請參閱[如何將應用程式指派給群組](apps-deploy.md)。
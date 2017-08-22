---
title: "如何將 Intune Web 應用程式新增到 Intune"
titleSuffix: Intune on Azure
description: "了解如何將 Web 應用程式新增至 Intune。"
keywords: 
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 05/04/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5f08752f-0e87-4ad9-a34c-4991b3150775
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: f64d60b659d0316cab542cb6005026a353ab0589
ms.sourcegitcommit: 4034ac474bfed358270a32459a2cf2fe02f44e45
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2017
---
# <a name="how-to-add-web-apps-to-microsoft-intune"></a>如何將 Web 應用程式新增至 Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

1. 登入 Azure 入口網站。
2. 選擇 [更多服務]  >  [監視 + 管理]  >  [Intune]。
3. 在 **Intune** 刀鋒視窗上選擇 [管理應用程式]。
4. 在**行動應用程式**工作負載中選擇 [管理]  >  [應用程式]。
5. 從應用程式清單上方選擇 [新增]。
6. 在 [新增應用程式] 刀鋒視窗中選擇 [應用程式資訊]。
7. 在 [編輯應用程式] 刀鋒視窗中設定下列資訊。 完成設定後，按一下 [新增]：
    - **應用程式 URL** - 輸入裝載您要指派之應用程式的網站 URL。
    - **名稱** - 輸入要顯示在公司入口網站中的應用程式名稱。
    - **描述** - 輸入應用程式的描述。 這會對公司入口網站中的使用者顯示。
    - **發行者** - 輸入應用程式的發行者名稱。
    - **類別 (選用)** - 選取一或多個內建應用程式類別，或選取您建立的類別。 這可以讓使用者在瀏覽公司入口網站時，更輕鬆地找到應用程式。
    - **將此顯示為公司入口網站中的精選應用程式** - 當使用者瀏覽應用程式時，以醒目方式在公司入口網站的主頁面上顯示此應用程式。
    - **需要受管理的瀏覽器以開啟此連結** - 當您將網站或 Web 應用程式的連結指派給使用者時，他們只能在 Intune 管理的瀏覽器中開啟連結。 他們的裝置上必須安裝此瀏覽器。
    - **上傳圖示** - 上傳應用程式所要關聯的圖示。 這是使用者瀏覽公司入口網站時，會隨應用程式一起顯示的圖示。
8. 完成之後，請在 [新增應用程式] 刀鋒視窗中選擇 [儲存]。

您建立的應用程式將會顯示在應用程式清單中，而您可從中將應用程式指派給您選擇的群組。 如需協助，請參閱[如何將應用程式指派給群組](apps-deploy.md)。
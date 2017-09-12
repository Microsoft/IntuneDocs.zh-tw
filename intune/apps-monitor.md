---
title: "如何監視應用程式資訊和指派"
titlesuffix: Azure portal
description: "將應用程式指派給使用者或裝置之後，可以使用此資訊協助您監視其狀態。"
keywords: 
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 05/05/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 64e5133d-1e23-4ee6-b556-f5d32c0e95da
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: ddb9b939b695f8612c02a2a25f4670e28c556c44
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/09/2017
---
# <a name="how-to-monitor-app-information-and-assignments-with-microsoft-intune"></a>如何使用 Microsoft Intune 監視應用程式資訊和指派

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Intune 提供了許多方式，可讓您監視您所管理之應用程式的內容，以及它們的指派狀態。

1. 在**行動應用程式**工作負載中選擇 [管理]  >  [應用程式]。
2. 在應用程式清單刀鋒視窗中，選擇您想要查看資訊的應用程式。 您會看到 [<應用程式名稱> 裝置安裝狀態] 刀鋒視窗：![應用程式安裝狀態刀鋒視窗。](./media/monitor-apps.png)

然後，採取下列其中一個動作來深入了解應用程式及其指派。

## <a name="general"></a>一般

- **概觀**：提供應用程式的基本概觀，以及該應用程式所有指派之狀態的相關資訊。 您可以選擇其中一個圖表以開啟 [裝置安裝狀態] 或 [使用者安裝狀態] 刀鋒視窗，以取得更加詳細的資訊。

## <a name="manage"></a>管理

- **內容**：可讓您檢視及變更已選取應用程式的相關資訊。 如需應用程式內容的詳細資訊，請參閱[如何將應用程式新增至 Microsoft Intune](apps-add.md)。
- **指派**：提供此應用程式之指派的相關資訊。 如需詳細資訊，請參閱[如何使用 Microsoft Intune 將應用程式指派給群組](apps-deploy.md)。

## <a name="monitor"></a>監視

- **裝置安裝狀態**：提供您已指派選取應用程式之每個裝置的詳細資訊，包括裝置名稱、作業系統、裝置上一次簽入 Intune 的時間，以及應用程式安裝的狀態。
- **使用者安裝狀態**：提供您已指派選取應用程式之使用者的詳細資訊，包括使用者在其所有裝置上所安裝的應用程式數目，以及所有安裝錯誤的相關資訊。
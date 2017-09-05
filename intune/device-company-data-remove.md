---
title: "透過 Intune 從裝置上移除公司資料"
titleSuffix: Intune on Azure
description: "了解如何透過 Intune，從您管理的裝置上只移除公司資料。"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 08/09/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f021e95f-157f-4e8a-9253-1cff03d6ee3e
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 8074d6e7cc0a061a6708f8c8bfae1a4dfcb6daa3
ms.sourcegitcommit: 10e3ab2aeb79a1fb2243bef2748ccc003fdd4cc7
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2017
---
# <a name="remove-company-data-from-intune-managed-devices"></a>從 Intune 管理的裝置上移除公司資料


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

**移除公司資料**裝置動作只會從 Intune 管理的裝置移除公司資料。 該動作不會從裝置移除個人資料。 移除後，裝置將不再由 Intune 管理，而且也無法再存取公司資源。

## <a name="supported-platforms"></a>支援的平台

- Windows - 支援 (不支援已加入 Azure Active Directory 的 Windows 裝置)
- Windows Phone - 不支援
- iOS - 支援
- macOS - 支援
- Android - 支援

## <a name="how-to-remove-company-data"></a>如何移除公司資料

1. 登入 Azure 入口網站。
2. 選擇 [更多服務]  >  [監視 + 管理]  >  [Intune]。
3. 在 [Intune] 刀鋒視窗中，選擇 [裝置]。
4. 在 [裝置和群組] 刀鋒視窗中選擇 [所有裝置]。
5. 從您管理的裝置清單中，選擇裝置，然後選擇 [移除公司資料] 裝置遠端動作。

## <a name="next-steps"></a>後續步驟

若要查看您剛採取的動作狀態，請在 [裝置和群組] 刀鋒視窗中，選擇 [裝置動作]。

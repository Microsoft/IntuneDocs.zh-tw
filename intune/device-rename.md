---
title: 使用 Microsoft Intune 重新命名 Windows 裝置 - Azure |Microsoft Docs
description: 使用 Microsoft Intune 重新命名 Windows 裝置。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/26/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8dfdc3641d583fc045346034ee8543feff1e7cbf
ms.sourcegitcommit: 1144247aa7f042eb1b99d8fd8dd17b909eae38c5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2019
ms.locfileid: "59567097"
---
# <a name="rename-a-windows-device-in-intune"></a>在 Intune 中重新命名 Windows 裝置


[!INCLUDE [azure_portal](./includes/azure_portal.md)]

**重新命名裝置**動作可讓您重新命名屬公司所有，且已在 Intune 中註冊的 Windows 裝置。 裝置在 Intune 中和裝置上的名稱都會變更。 

這項功能目前不支援重新命名混合式 Azure AD Windows 裝置。

## <a name="rename-a-device"></a>重新命名裝置

1. 登入 [Azure 入口網站](https://portal.azure.com)。
2. 選擇 [所有服務]、篩選 **Intune**，然後選擇 [Microsoft Intune]。
3. 選擇 [裝置] > [所有裝置] > 選擇一個 Windows 裝置 > [更多] > [重新命名裝置]。
4. 在 [重新命名裝置] 刀鋒視窗中，於文字方塊中輸入新名稱。 您可以使用字母、數字和連字號。 名稱必須包含至少一個字母或連字號。
5. 如果要讓裝置在重新命名之後重新啟動，請選擇 [重新命名後重新啟動] 旁邊的 [是]。
6. 選擇 [重新命名]。



## <a name="next-steps"></a>後續步驟

若要查看 [重新命名] 裝置動作的狀態，請檢查裝置的 [概觀] 頁面。

---
title: "使用 Microsoft Intune 重設 Windows 10 裝置 - Azure | Microsoft Docs"
description: "使用 [全新開始] 在 Windows 10 電腦上使用 Microsoft Intune 移除或解除安裝應用程式，包括 OEM 預先安裝的應用程式。 也可以使用 [if user data is retained] (是否保留使用者資料) 設定，保留主資料夾內容。"
keywords: 
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/07/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5aa5cfa3-c483-4099-b40f-578ff8dca425
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: d17c9dc11791f32f0c2c1e7faa88966c112fc6a5
ms.sourcegitcommit: 9cf05d3cb8099e4a238dae9b561920801ad5cdc6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2018
---
# <a name="use-fresh-start-to-reset-windows-10-devices-with-intune"></a>透過 Intune 使用「重新開始」重設 Windows 10 裝置


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

[全新開始] 裝置動作會移除安裝在 Windows 10 電腦上執行建立者更新的任何應用程式。 然後，它會自動將電腦更新至最新版的 Windows。

這個動作有利於移除一般新電腦會有的預先安裝 (OEM) 應用程式。 若要保留使用者的主資料夾內容，只移除應用程式和設定，請使用 `if user data is retained` 設定。

> [!IMPORTANT]
> [全新開始] 會從 Intune 取消註冊裝置，但裝置仍加入 Azure Active Directory。

## <a name="use-fresh-start"></a>使用 [全新開始]

1. 登入 [Azure 入口網站](https://portal.azure.com)。
2. 選擇 [所有服務]，篩選 [Intune]，然後選取 [Microsoft Intune]。
3. 選取 [裝置]，然後選取 [所有裝置]。
4. 從您管理的裝置清單中，選擇 Windows 10 電腦裝置，然後選取 [全新開始]。

## <a name="next-steps"></a>接下來的步驟

若要查看此動作的狀態，請選取 [裝置動作] ([Microsoft Intune] > [裝置])。
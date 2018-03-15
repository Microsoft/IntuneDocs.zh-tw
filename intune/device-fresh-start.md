---
title: "透過 Intune 重設 Windows 10 裝置"
titlesuffix: Azure portal
description: "了解如何使用「重新開始」來重設執行 Intune 的 Windows 10 電腦。"
keywords: 
author: arob98
ms.author: angrobe
manager: dougeby
ms.date: 08/09/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5aa5cfa3-c483-4099-b40f-578ff8dca425
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: c45d3e47c90ca7739b3aa6eee1bf31d787a82264
ms.sourcegitcommit: eac89306d1391a6d3ae1179612b0820b19c2baa6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="use-fresh-start-to-reset-windows-10-devices-with-intune"></a>透過 Intune 使用「重新開始」重設 Windows 10 裝置


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

**重新開始**裝置動作會在執行 Creators Update 的 Windows 10 電腦上移除所有已安裝的應用程式，然後將該電腦自動更新至最新的 Windows 版本。
這個動作可用來協助移除通常會隨新電腦提供之預先安裝的 (OEM) 應用程式。 您可以設定是否在發出此裝置動作時保留使用者資料。 在這種情況下，會移除應用程式和設定，但會保留使用者主資料夾的內容。

## <a name="how-to-use-fresh-start"></a>如何使用重新開始

1. 登入 [Azure 入口網站](https://portal.azure.com)。
2. 選擇 [All services] (所有服務) > [Intune]。 Intune 位於 [監視 + 管理] 區段。
3. 在 [Intune] 窗格中，選擇 [裝置]。
4. 在 [裝置] 窗格中，選擇 [所有裝置]。
5. 從您管理的裝置清單中，選擇 Windows 10 電腦裝置，然後選擇 [重新開始] 裝置遠端動作。

## <a name="next-steps"></a>接下來的步驟

若要查看您剛採取的動作狀態，請在 [裝置] 窗格中，選擇 [裝置動作]。


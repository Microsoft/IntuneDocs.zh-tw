---
title: "使用 Intune 從遠端重新啟動裝置"
titleSuffix: Intune on Azure
description: "了解如何使用重新啟動裝置動作，從遠端重新啟動裝置。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 04/27/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c707e0c4-391a-4bad-9dfd-9a7799c48dd5
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 5278179f22d174de6e97aa990bbe8761d8c8f8f8
ms.sourcegitcommit: ee7f69efe9f32a1d6bdeb1fab73d03dbfe1ae58c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2017
---
# <a name="remotely-restart-devices-with-intune"></a>使用 Intune 從遠端重新啟動裝置


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

**重新啟動**裝置動作會導致您選擇的裝置重新啟動。 重新啟動時不會自動通知裝置擁有者，因此將會遺失工作。

## <a name="supported-platforms"></a>支援的平台

- Windows - 支援 Windows 8.1 和更新版本
- Windows Phone - 支援 Windows Phone 8.1 和更新版本
- iOS - 不支援
- macOS - 不支援
- Android - 不支援

## <a name="how-to-restart-a-device"></a>如何重新啟動裝置

1. 登入 Azure 入口網站。
2. 選擇 [更多服務]  >  [監視 + 管理]  >  [Intune]。
3. 在 [Intune] 刀鋒視窗中，選擇 [裝置]。
4. 在 [裝置和群組] 刀鋒視窗中選擇 [所有裝置]。
5. 從您管理的裝置清單中，選擇裝置，然後選擇 [重新啟動] 裝置遠端動作。

## <a name="next-steps"></a>後續步驟

若要查看您剛採取的動作狀態，請在 [裝置和群組] 刀鋒視窗中，選擇 [裝置動作]。

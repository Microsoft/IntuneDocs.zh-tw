---
title: "使用 Intune 同步裝置"
titlesuffix: Azure portal
description: "了解如何使用 Intune 同步處理裝置以取得最新的原則和動作。"
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 08/09/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 02ad249e-f098-421f-861f-6b2ff733ac7c
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: ab24b147b32c94ba51728c0c223de3e6c92dd215
ms.sourcegitcommit: cf7f7e7c9e9cde5b030cf5fae26a5e8f4d269b0d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/14/2017
---
# <a name="sync-devices-with-intune-to-get-the-latest-policies-and-actions"></a>使用 Intune 同步裝置以取得最新的原則和動作


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

[同步] 裝置動作會強制所選裝置立即使用 Intune 簽入。 當裝置簽入時，會立即收到所有擱置動作或已指派給它的原則。  這個動作可協助您立即驗證和針對您已指派的原則進行疑難排解，不用等到下次排程的簽入。

## <a name="supported-platforms"></a>支援的平台

- Windows - 支援
- Windows Phone - 支援
- iOS - 支援
- macOS - 支援
- Android - 支援

## <a name="how-to-sync-a-device"></a>如何同步裝置

1. 登入 Azure 入口網站。
2. 選擇 [更多服務]  >  [監視 + 管理]  >  [Intune]。
3. 在 [Intune] 刀鋒視窗中，選擇 [裝置]。
4. 在 [裝置和群組] 刀鋒視窗中選擇 [所有裝置]。
5. 從您管理的裝置清單中，選擇裝置，然後選擇 [同步] 遠端動作。
7. 選擇 [是] 確認該動作。

## <a name="next-steps"></a>後續步驟

選擇 [裝置動作] 以查看同步動作的狀態。 

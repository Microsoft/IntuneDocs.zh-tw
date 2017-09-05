---
title: "使用 Intune 將裝置重設成出廠預設值"
titleSuffix: Intune on Azure
description: "了解如何使用 Intune，將您管理的裝置重設成出廠預設值。"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 08/09/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8eff9b53-eef2-4c50-8aee-556bc49d69f2
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: fd7273d6c5f75a675d7b01df4225a96fd3a5f821
ms.sourcegitcommit: 10e3ab2aeb79a1fb2243bef2748ccc003fdd4cc7
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2017
---
# <a name="reset-intune-managed-devices-to-factory-settings"></a>將 Intune 管理的裝置重設成出廠預設值


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

**重設成出廠預設值**會將裝置回復成其預設設定。 這類裝置不再由 Intune 管理，而且公司與個人資料皆會移除。 您無法復原此動作。

## <a name="supported-platforms"></a>支援的平台

- Windows - 支援 Windows 8.1 和更新版本 (非 EAS 管理裝置)
- Windows Phone - 不支援
- iOS - 支援
- macOS - 不支援
- Android - 支援 (不支援 Android for Work)

## <a name="how-to-reset-a-device-to-factory-settings"></a>如何將裝置重設回原廠設定

1. 登入 Azure 入口網站。
2. 選擇 [更多服務]  >  [監視 + 管理]  >  [Intune]。
3. 在 [Intune] 刀鋒視窗中，選擇 [裝置]。
4. 在 [裝置和群組] 刀鋒視窗中選擇 [所有裝置]。
5. 從您管理的裝置清單中，選擇裝置，然後選擇 [重設成出廠預設值] 裝置遠端動作。

## <a name="next-steps"></a>後續步驟

若要查看您剛採取的動作狀態，請在 [裝置和群組] 刀鋒視窗中，選擇 [裝置動作]。

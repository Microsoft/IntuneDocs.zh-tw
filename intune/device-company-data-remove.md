---
title: "透過 Intune 從裝置上移除公司資料"
titleSuffix: Intune on Azure
description: "了解如何透過 Intune，從您管理的裝置上只移除公司資料。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 04/27/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f021e95f-157f-4e8a-9253-1cff03d6ee3e
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 39acd12333e9685f94d23416fb1a61ce93f45476
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2017
---
# <a name="remove-company-data-from-intune-managed-devices"></a>從 Intune 管理的裝置上移除公司資料


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

**移除公司資料**只會從 Intune 管理的裝置上移除公司資料。 裝置上的個人資料不會移除。 這類裝置將不再由 Intune 管理，而且也無法再存取公司資源 (不適用於加入 Azure Active Directory 的 Windows 裝置)。

1. 登入 Azure 入口網站。
2. 選擇 [更多服務]  >  [監視 + 管理]  >  [Intune]。
3. 在 [Intune] 刀鋒視窗中，選擇 [裝置]。
4. 在 [裝置和群組] 刀鋒視窗中選擇 [所有裝置]。
5. 從您管理的裝置清單中，選擇裝置，然後選擇 [移除公司資料] 裝置遠端動作。

若要查看您剛採取的動作狀態，請在 [裝置和群組] 刀鋒視窗中，選擇 [裝置動作]。

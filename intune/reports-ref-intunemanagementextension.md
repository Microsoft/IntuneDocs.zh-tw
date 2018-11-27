---
title: IntuneManagementExtension 實體
titlesuffix: Microsoft Intune
description: Intune 資料倉儲 API 中實體集合的 IntuneManagementExtension 實體類別參考主題。
keywords: Intune 資料倉儲
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/04/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 73DF3B90-6D52-4EF6-AFFD-1873A18C7421
ms.reviewer: dariusz
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.openlocfilehash: 48e08b93468fb177fd3a724e5bcc6758cf262e99
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2018
ms.locfileid: "52189362"
---
# <a name="reference-for-intune-management-extension"></a>Intune 管理延伸模組的參考

**IntuneManagementExtension** 類別包含的行動裝置實體，可追蹤下列資訊：

  -  IntuneManagementExtension 的版本
  -  IntuneManagementExtension 的安裝狀態

## <a name="intunemanagementextensionversion"></a>IntuneManagementExtensionVersion

**IntuneManagementExtensionVersion** 實體會列出 IntuneManagementExtension 使用的所有版本。

| 屬性  | 說明 | 範例 |
|---------|------------|--------|
| ExtensionVersionKey |IntuneManagementExtension 版本的唯一識別碼。 | 1 |
| ExtensionVersion |4 位數的版本號碼。 |1.0.2.0 |

## <a name="intunemanagementextensionhealthstate"></a>IntuneManagementExtensionHealthState

**IntuneManagementExtensionHealthState** 會列出 IntuneManagementExtension 所有可能的健全狀況狀態。

| 屬性  | 說明 | 範例 |
|---------|------------|--------|
| ExtensionStateKey |健全狀況狀態的唯一識別碼。 | 2 |
| ExtensionState |IntuneManagementExtension 的健全狀況狀態。 | Healthy |

## <a name="intunemanagementextension"></a>IntuneManagementExtension

**IntuneManagementExtension** 會列出每部 Windows 10 裝置每日的 IntuneManagementExtension 健全狀況。
保留最近 60 天的資料。 


|      屬性       |                         說明                         | 範例 |
|---------------------|-------------------------------------------------------------|---------|
|       DateKey       |               日期的唯一識別碼。                |   123   |
|      TenantKey      |              租用戶的唯一識別碼。               |   456   |
|      DeviceKey      |              裝置的唯一識別碼。               |   789   |
| ExtensionVersionKey | IntuneManagementExtension 版本的唯一識別碼。 |    1    |
|  ExtensionStateKey  |             健全狀況狀態的唯一識別碼。              |    2    |


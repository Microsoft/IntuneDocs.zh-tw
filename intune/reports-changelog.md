---
title: "Intune 資料倉儲變更記錄檔 | Microsoft Docs"
description: "Intune 資料倉儲 API 中的變更清單。"
keywords: "Intune 資料倉儲"
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 10/19/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: E85DBB2D-67BB-4E10-82D6-E43046B9C43C
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 6d675a36cd5ea4c11d755174bf2b0bbc5d4b18ec
ms.sourcegitcommit: 5279a0bb8c5aef79aa57aa247ad95888ffe5a12b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/08/2017
---
# <a name="change-log-for-the-intune-data-warehouse-api"></a>Intune 資料倉儲 API 的變更記錄檔

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

保持 Intune 資料倉儲更新的最新狀態。

## <a name="1710"></a>1710
_發行日期 2017 年 11 月_

### <a name="user-entity-contains-latest-user-data-in-data-warehouse-data-model----1544273---"></a>使用者實體包含資料倉儲資料模型中的最新使用者資料<!-- 1544273 -->

Intune 資料倉儲資料模型的第一個版本只包含最新的歷程 Intune 資料。 報表製作者無法擷取使用者的目前狀態。 在這項更新中，[**使用者實體**](reports-ref-user.md)會填入最新的使用者資料。

### <a name="new-entities-in-the-in-data-warehouse-data-model----1479526--------"></a>資料倉儲資料模型中的新實體 <!-- 1479526 --><!-- -->

 - 已新增 [**UserDeviceAssociation**](reports-ref-user-device.md) 實體。 **UserDeviceAssociation** 包含您組織中的使用者裝置關聯。
 - 已新增實體 [**IntuneManagementExtension**](reports-ref-intunemanagementextension.md)。 **IntuneManagementExtension** 包含的行動裝置實體，會追蹤版本和安裝狀態等資訊。

## <a name="next-steps"></a>後續步驟
 - 了解[每週的 Intune 新功能](whats-new.md)。 您也可以了解即將推出的變更、關於服務的重要通知，以及過去版本的相關資訊。 
 - 閱讀 [Microsoft Intune 部落格](http://go.microsoft.com/fwlink/?LinkID=273882)。
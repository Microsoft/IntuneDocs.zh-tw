---
title: 監視裝置合規性
titlesuffix: Microsoft Intune
description: 了解如何監視裝置合規性。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/07/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 0790934b-48b9-435b-a8aa-e83ed5b73191
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 0fec00b18bd63986a537549715af84cd44539fbb
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
ms.locfileid: "31830411"
---
# <a name="monitor-device-compliance-in-intune"></a>在 Intune 中監視裝置相容性

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

您可以在 [概觀] 刀鋒視窗中，檢視您**合規性設定檔**的狀態摘要。
您可以互動方式點選各個圖表來向下鑽研詳細資料。 如果您設定了多個的相容性設定檔，您可以在 [原則] 刀鋒視窗的 [管理] > [報表] 下檢視原則狀態。

##  <a name="device-compliance"></a>裝置合規性

裝置相容性報表的摘要檢視，會列出報告處於下列其中一個狀態的裝置數彙總資訊︰

- **相容**：裝置最近已評估，並符合您指定的相容性設定檔設定。
- **不符合規範**︰裝置已被評估及判定為不符合規範。  若設定檔中指定有寬限期，當寬限期一到，裝置就會處於不符合規範的狀態。
- **寬限期**：裝置已被評估及判定為不符合規範。 但在裝置被標示為不相容之前，寬限期仍然適用。

您可以向下鑽研每個區段，深入了解個別裝置及使用者的詳細資料。

## <a name="setting-compliance"></a>設定合規性

設定相容性報表提供每一項相容性設定的詳細資料，例如︰

- 不符合設定規範的裝置數。
- 套用設定的平台。

您可以向下鑽研每項設定，以查看啟用這些設定之設定檔的詳細資訊，以及該設定的值。

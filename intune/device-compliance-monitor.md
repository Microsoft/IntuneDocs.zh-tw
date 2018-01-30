---
title: "如何監視裝置相容性"
titlesuffix: Azure portal
description: "了解如何監視裝置合規性。"
keywords: 
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0790934b-48b9-435b-a8aa-e83ed5b73191
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 9cd8bb0486164dd9dfe020261da9079ea5a68633
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2018
---
# <a name="how-to-monitor-device-compliance-in-intune"></a>如何在 Intune 中監視裝置合規性

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

您可以在 [概觀] 刀鋒視窗中，檢視您**合規性設定檔**的狀態摘要。
您可以互動方式點選各個圖表來向下鑽研詳細資料。 您如有設定多個合規性設定檔，也可以前往原則刀鋒視窗的 [管理] 區段中選擇 [報表]，以檢視每項原則的狀態。  以下列出可用報表的詳細資料。

##  <a name="device-compliance"></a>裝置合規性

裝置合規性報表的摘要檢視會先顯示下列報告項目之一的裝置數彙總資訊︰

- **符合規範**︰裝置最近被評估為合規，並已被判定為符合您指定的合規性設定檔設定。
- **不符合規範**︰裝置已被評估及判定為不符合規範。  若設定檔中指定有寬限期，當寬限期一到，裝置就會處於不符合規範的狀態。
- **寬限期**：裝置已被評估及判定為不符合規範。 但在裝置實際被標示為不符合規範之前，寬限期仍然適用。

您可以向下鑽研每個區段，深入了解個別裝置及使用者的詳細資料。

## <a name="setting-compliance"></a>設定合規性

設定合規性報表提供每一項合規性設定的詳細資料，例如︰

- 不符合設定規範的裝置數。
- 套用設定的平台。

您可以向下鑽研每項設定，以查看啟用這些設定之設定檔的詳細資訊，以及該設定的值。

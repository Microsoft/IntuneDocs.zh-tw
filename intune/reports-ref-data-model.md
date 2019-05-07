---
title: 資料倉儲資料模型
titleSuffix: Microsoft Intune
description: Microsoft Intune 資料倉儲會每日對資料進行抽樣，以提供持續變更中行動環境的歷程檢視。
keywords: Intune 資料倉儲
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 04/10/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 4D04D3D9-4B6C-41CD-AAF8-466AF8FA6032
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5a56c06970e267d8ba604e9d4e53f4a3f315fbcb
ms.sourcegitcommit: af2512a1342d8037a96a61c8cc2c63e107913733
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59533554"
---
# <a name="microsoft-intune-data-warehouse-data-model"></a>Microsoft Intune 資料倉儲資料模型

Intune 資料倉儲會每日對資料進行抽樣，以提供行動裝置之持續變更中環境的歷程檢視。 檢視由在時間上的相關實體所組成。

## <a name="entities-entity-sets"></a>實體：實體集

倉儲會公開下列高階區域中的資料：

  -  啟用應用程式保護的應用程式和使用方式
  -  已註冊的裝置、屬性和清查
  -  應用程式和軟體清查
  -  裝置組態和合規性原則

這些區域包含對您 Intune 環境有意義的實體。 您可在下列主題中找到有關實體集的詳細資訊：

  -  [應用程式](reports-ref-application.md)
  -  [日期](reports-ref-date.md)
  -  [裝置](reports-ref-devices.md)
  -  [Intune 管理延伸模組](reports-ref-intunemanagementextension.md)
  -  [原則](reports-ref-policy.md)
  -  [行動應用程式管理 (MAM)](reports-ref-mobile-app-management.md)
  -  [User](reports-ref-user.md)
  -  [Current User](reports-ref-current-user.md)
  -  [使用者裝置關聯](reports-ref-user-device.md)

## <a name="relationships-star-schema-model"></a>關聯性：星狀結構描述模型

針對您要詢問的問題類型，倉儲會以有意義的關聯性來組織實體。 例如，您可以檢閱內部開發之 Android 應用程式的安裝數量。 資料倉儲結構可讓您深入了解行動環境。 接著，Microsoft Power BI 這類分析工具可以使用資料倉儲資料模型來建立視覺效果和動態儀表板。

實體和關聯性使用星型結構描述模型。 星型結構描述會將時間維度與事實相互關聯。 模型內容中的「事實」是量化度量單位，例如裝置數目、應用程式數目或註冊時間。 事實資料表儲存大量資料。 它們可能變得非常大，因此它們通常將資訊限制在 30 天。 「維度」提供事實的內容。 事實測量發生什麼事，維度則指出發生在誰身上。 維度資料表 (如 **User** 資料表) 比較小，可保存比事實資料表更長時間的資料。 

星型結構描述模型最適合彈性和資料分析，以建立了解您發展中行動環境所需的報表。

## <a name="time-daily-snapshots"></a>時間：每日快照集

倉儲是您 Intune 資料的下游。 Intune 於 UTC 的午夜擷取每日快照集並儲存在倉儲。 快照集的保留持續時間會隨著不同的事實資料表而異。 有些可能保留 7 天，有些可能保留 30 天，或甚至更長的期間。

## <a name="next-steps"></a>後續步驟

 - 若要深入了解資料倉儲如何在 Intune 中追蹤使用者的存留期，請參閱 [Intune 資料倉儲中的使用者存留期表示法](reports-ref-user-timeline.md)。
 - 在[建立第一個資料倉儲](https://www.codeproject.com/Articles/652108/Create-First-Data-WareHouse) \(英文\) 中深入了解使用資料倉儲。
 - 在[匯入資料集以建立新的 Power BI 報表](https://powerbi.microsoft.com/documentation/powerbi-service-create-a-new-report/) \(英文\) 中深入了解使用 Power BI 和資料倉儲。 

---
title: "資料倉儲資料模型 | Microsoft Docs"
description: "Intune 資料倉儲會每日對資料進行抽樣，以提供持續變更中行動環境的歷程檢視。"
keywords: "Intune 資料倉儲"
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 07/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4D04D3D9-4B6C-41CD-AAF8-466AF8FA6032
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 37af15a36ff20b2c13b5fb1157d04a05c40d3216
ms.sourcegitcommit: e9f9fccccef691333143b7523d1b325ee7d1915a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/02/2017
---
# <a name="data-warehouse-data-model"></a>資料倉儲資料模型

Intune 資料倉儲會每日對資料進行抽樣，以提供持續變更中行動環境的歷程檢視。

從您的租用戶中提取的資料會新增至資料倉儲。 倉儲是一組對您要詢問的問題類型有意義的實體和關聯性。 例如，您可以檢閱上週每日內部開發 Android 應用程式的安裝數目，以評估安裝趨勢是否遞增。 資料倉儲結構可讓您深入了解行動環境。 接著，Microsoft Power BI 這類分析工具可以使用資料倉儲資料模型來建立視覺效果和動態儀表板。

Intune 資料倉儲結構會使用星型結構描述模型。 星型結構描述會透過時間維度來組織事實。 模型內容中的「事實」是量化度量單位，例如裝置數目、應用程式數目或註冊時間。 模型內容中的「維度」是一組類別和其階層式關聯性。 例如，日分組為月，而月分組為年。 星型結構描述模型最適合彈性和資料分析，以建立了解您發展中行動環境所需的報表。

倉儲會公開下列高階類別中的資料：
  -  啟用應用程式保護的應用程式和使用方式
  -  已註冊的裝置、屬性和清查
  -  應用程式和軟體清查
  -  裝置組態和合規性原則

**資料模型實體集**

實體集是資料模型中的具名實體集合。 這些集合包含可定義模型中所收集資料的實體。 每個實體集都會提供資料倉儲資料模型的存取點。 您可以找到下列實體類別的詳細資料：

  -  [應用程式](reports-ref-application.md)
  -  [日期](reports-ref-date.md)
  -  [裝置](reports-ref-devices.md)
  -  [原則](reports-ref-policy.md)
  -  [行動應用程式管理 (MAM)](reports-ref-mobile-app-management.md)
  -  [User](reports-ref-user.md)
  -  [使用者裝置關聯](reports-ref-user-device.md)
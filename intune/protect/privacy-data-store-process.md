---
title: Intune 中的資料儲存與處理
titleSuffix: Microsoft Intune
description: 了解如何在 Intune 中儲存及處理個人資料。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/18/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: edb07842-6a16-482e-8c1d-541a29e169a8
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 07a9232203c7d93eb1b9e81b962d2369e77b7421
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72509040"
---
# <a name="data-storage-and-processing-in-intune"></a>Intune 中的資料儲存與處理

在 Intune [收集資料](privacy-data-collect.md)之後，會如下所述繼續儲存及處理該資料。

## <a name="storing-personal-data"></a>儲存個人資料

所有收集的非遙測資料都會透過 Intune 服務來處理，並儲存在下列一或多個儲存位置： 

- SQLAzure 
- 可靠集合 (Service Fabric)  
- Azure 儲存體 

對於監視及提供穩定服務很重要的遙測資料 (服務記錄、效能記錄、錯誤等)，則會傳送至 Microsoft 遙測資料存放區。

### <a name="storage-locations"></a>儲存位置

Microsoft 在全球許多區域提供並執行 Intune 服務。 Intune 會採用系統管理員為客戶資料所選擇的儲存位置。

如需詳細資訊，請參閱[您的資料位於何處？](https://www.microsoft.com/trust-center/privacy/data-location)

### <a name="personal-data-retention"></a>個人資料保留

一般而言，Intune 會保留個人資料，直到使用者從 Intune 管理中移除超過 30 天為止。

使用 Intune 所收集的遙測資料最多會保留 30 天。

稽核記錄最多會保留一年。

## <a name="processing-personal-data"></a>處理個人資料

Intune 透過 ISO 認證系統處理個人資料。 如需詳細資訊，請參閱[服務信任入口網站](https://www.microsoft.com/en-us/TrustCenter/stp)。

### <a name="profiling-and-marketing"></a>分析與行銷

Microsoft Intune 不會使用提供服務時所收集的任何個人資料進行分析或行銷。 

### <a name="restrict-processing-of-personal-data"></a>限制個人資料的處理

若要限制使用者個人資料的處理，您可以透過下列方式刪除使用者帳戶：
1. 匯出使用者個人資料的電子副本，包括
    - 帳戶
    - 服務資料
    - 相關聯的記錄
2. 從 Intune 中刪除使用者帳戶和相關聯的資料。

## <a name="next-steps"></a>後續步驟

深入了解 Intune 如何[保護及共用](privacy-data-secure-share.md)個人資料。 

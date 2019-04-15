---
title: 典型的 Intune 移轉週期運作方式
titleSuffix: Microsoft Intune
description: 本文說明 Microsoft Intune 移轉週期如何運作，並提供您可以如何處理移轉週期的範例。
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 3688b724-9521-4210-bf4d-bcf47d8d4ca0
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3919ae461fbbd5c5c69c1fbe4983cc8468f576c6
ms.sourcegitcommit: 484a898d54f5386fdbce300225aaa3495cecd6b0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/01/2019
ms.locfileid: "59567578"
---
# <a name="typical-migration-cycle"></a>典型的移轉週期

組織通常會以 IT 部門中少部分的使用者為目標，以小型試驗開始其 Intune 移轉。 此外，您的組織可能需要討論像是群組變更意願、使用者數目、複雜度、需求、位置及業務風險等因素，以協助決定移轉的時間範圍。

下列是如何排程目標群組的一個範例︰

  | **移轉的目標群組** | **時間週期 1** | **時間週期 2** | **時間週期 3** | **時間週期 4** | **...**
|:---:|:---:|:---:|:---:|:---:|:---:|
| 有限試驗的 IT 組織 (50 個使用者) | 宣布計劃 | 指示使用者註冊 | 提供期限 | 強制條件式存取 |  |                                                        
| 擴充試驗的 IT 組織 (200 個使用者) |  | 宣布計劃 | 指示使用者註冊 | 提供期限 | 強制條件式存取 |
| 移轉階段 1 精通科技的使用者 (2000) |  |  | 宣布計劃 | 指示使用者註冊 | 提供期限 |
| 移轉階段 2 美國東部 |  |  |  | 宣布計劃 | 指示使用者註冊 |
| 所有地區 |  |  |  |  | 宣布計劃 |

## <a name="customer-migration-case-study"></a>客戶移轉案例研究

### <a name="adatum-corporation"></a>Adatum Corporation

查看 [Adatum Corporation 如何透過協力廠商 MDM 提供者完成移轉至 Intune 的程序 (英文)](https://gallery.technet.microsoft.com/Intune-migration-guide-893a95e3?redir=0)。

## <a name="monitoring-migration"></a>監視移轉

Intune 提供幾種監視移轉的方式：

* Intune 使用者群組檢視

* 一組內建報告

* 主控台內警示

在每個階段之後追蹤有多少個使用者已註冊裝置，您才能：

-   評估溝通計劃的效益。

-   評估強制條件式存取的影響。


## <a name="post-migration"></a>移轉後

移轉到 Intune 之後，請淘汰先前的 MDM 提供者和取消訂閱服務。 此外，還請依照 MDM 提供者的指示，移除任何不必要的基礎結構需求。

---
title: 判斷推出計畫的目標群組和時間範圍
titleSuffix: Microsoft Intune
description: 本文可協助您決定可推出至 Microsoft Intune 的群組以及這些部署的時間範圍。
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 3a63f78f-a7e7-4f44-9288-16b28d5d58ca
ms.reviewer: jeffbu, cgerth
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 777267f10edac5bbdbe23ceb3068d4366a8df7b7
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72509940"
---
# <a name="develop-a-rollout-plan"></a>開發推出計劃

您的推出計劃可識別 Intune 推出的目標組織群組、每個群組的推出時間範圍，以及將使用的註冊方法。

## <a name="targeted-groups-and-timeframes"></a>目標群組與時間範圍

首先，檢閱 Intune 推出及您在[使用案例](planning-guide-scenarios.md)中識別的目標群組。

接下來，判斷每個目標群組的時間範圍。 一般來說，Intune 部署小組與目標群組需要一起討論，以判斷最適合每個群組的推出時間表。 在此類討論中涵蓋的重點包括：
* 群組的更改意願
* 使用者和裝置數目
* 裝置平台的類型
* 需求
* 地理位置
* 商業風險

## <a name="rollout-phases"></a>首展階段
組織通常會選擇先從初始試驗來開始推出 Intune，並先以 IT 部門的一小組使用者為目標。 可擴充試驗，納入更多 IT 使用者並可讓其他組織群組參與。

### <a name="pilot"></a>試驗
推出的第一個階段目標應為試驗使用者。 試驗使用者應該了解他們是新解決方案中的第一批使用者。 他們必須願意提供意見反應以協助改善設定、文件、通知，並為所有其他使用者簡化後續推出的方式。 這些使用者不應該是主管或 VIP。

試驗是讓您測試[挑戰](../planning-guide-deployment-goals.md)並精簡稍早蒐集之[需求](../planning-guide-requirements.md)的好機會。

包含您的[通訊](../planning-guide-communication-plan.md)計劃、[支援](planning-guide-support-plan.md)計劃及[測試和驗證](planning-guide-test-validation.md)以解決任何問題，同時仍將對使用者的影響保持在很小的程度。

### <a name="production-rollout"></a>生產推出
在試驗成功之後，您已準備好開始完整的生產推出，並以其餘組織群組為目標。 一些不同推出群組與階段的範例如下：

- **部門** <br/>每個部門都可以是推出階段的目標。 您一次將整個部門當成目標。 在這類推出中，每個部門的使用者都應以相同方式使用行動裝置，並存取相同的應用程式。 使用者可能會有相同類型的原則。

- **地理位置** <br/>在此方法中，您會針對特定地理位置中的所有使用者進行部署，不論是在同一洲、國家/地區還是相同公司大樓。 這類分階段部署可讓您專注於特定位置的使用者。 這麼做可減少同時部署 Intune 的位置數量，確保提供過程更加[服務周全](#user-assisted-enrollment)的方法。 由於相同的位置，可能會有不同的部門或使用案例，因此可能會同時部署不同的使用案例。

- **平台** <br/>這種類型的部署會同時針對類似平台進行部署。 例如，可能第一個月先進行所有 iOS 裝置的部署，接著進行 Android，之後是 Windows。 這種類型的分階段部署有助於簡化技術服務人員支援，因為技術服務人員一次只需要支援一種平台。

下列為 Intune 推出計畫的範例，包括目標群組和時間表：

| **推出階段** | **7 月** | **8 月** | **9 月** | **10 月** |
|:---:|:---:|:---:|:---:|:---:|
| 有限試驗 | IT (50 位使用者) |  |  |  |                                                         
| 擴充試驗 | IT (200 位使用者)、IT 主管 (10 位使用者) |  |  |  |                                                         
| 生產推出階段 1 |  | 銷售和行銷 (2000 位使用者) |  |  |
| 生產推出階段 2 |  |  | 零售 (1000 位使用者) |  |
| 生產推出階段 3 |  |  |  | 人力資源 (50 位使用者)、財務 (40 位使用者)、主管 (30 位使用者) |

您可以[下載上表的範本](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0)來輸入組織的推出階段。
## <a name="match-rollout-groups-to-enrollment-approaches"></a>使推出群組符合註冊方法

現在，您已經決定要推出 Intune 的目標群組和時間表，下一步是選擇最適合每個群組的 Intune 註冊方式。 您可以使用的不同註冊方法包括：
* 使用者自助
* 協助使用者註冊
* IT 技術諮詢展

### <a name="user-self-service"></a>使用者自助

在此情況下，通常需要使用者遵循其 IT 組織提供的註冊指示，自行註冊自己的裝置。 這個方法是組織最常用的方法，而且比協助使用者註冊的方法更加靈活。

### <a name="user-assisted-enrollment"></a>協助使用者註冊

這又稱為「服務周全」的方法。 IT 小組成員可親自或透過 Skype 協助使用者完成註冊程序。 通常，這種方法多用於主管級員工及其他在註冊程序期間可能需要更多協助的群組。

### <a name="it-tech-fair"></a>IT 技術諮詢展

另一種可讓 Intune 使用者註冊的選項是 IT 技術諮詢展。 在這場活動中，IT 群組會佈置一個 Intune 註冊的協助攤位，使用者可以到這裡來了解 Intune 註冊的資訊、提出問題並獲得註冊程序的協助。 這個選項對 IT 群組和使用者都能帶來好處，尤其是在 Intune 推出初期階段。

在上述 Intune 推出計劃中包含註冊方法的更新範例如下：

| **推出階段** | **7 月** | **8 月** | **9 月** | **10 月** |
|:---:|:---:|:---:|:---:|:---:|
| 有限試驗 |  |  |  |  |
| 自助式 | IT |  |  |  |
| 擴充試驗 |  |  |  |  |
| 自助式 | IT |  |  |  |
| 服務周全方式 | IT 主管 |  |  |  |
| 生產推出階段 1 |  | 行銷、銷售 |  |  |
| 自助式 |  | 銷售與行銷 |  |  |
| 生產推出階段 2 |  |  | 零售 |  |
| 自助式 |  |  | 零售 |  |
| 生產推出階段 3 |  |  |  | 主管、人力資源、財務 |
| 自助式 |  |  |  | 人力資源、財務 |
| 服務周全方式 |  |  |  | 主管 |

## <a name="next-steps"></a>後續步驟

下一節提供[開發 Intune 推出通訊計畫](../planning-guide-communication-plan.md)的指引。

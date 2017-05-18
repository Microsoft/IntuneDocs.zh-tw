---
title: "判斷推出 Intune 的目標群組與時間表 | Microsoft Docs"
description: "本文有助於判斷 Microsoft Intune 僅限雲端實作推出的目標群組與時間表。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 12/20/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3a63f78f-a7e7-4f44-9288-16b28d5d58ca
ms.reviewer: jeffbu, cgerth
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: e10453155343bb7fd91a4fd3874d393ef78d0b1a
ms.openlocfilehash: 2a970badf5ac18a05115a72dc267ee455ba4628d
ms.lasthandoff: 04/25/2017


---

# <a name="develop-an-intune-rollout-plan"></a>開發 Intune 推出計畫

[!INCLUDE[note for both-portals](../includes/note-for-both-portals.md)]

本節將協助您判斷 Intune 推出的目標組織群組、每個群組的推出時間表，以及要使用的註冊方法。

## <a name="determine-intune-rollout-targeted-groups-and-timeframes"></a>判斷推出 Intune 的目標群組與時間表

請務必先識別要推出 Intune 的目標群組。 本指南之前的＜識別 Intune 使用案例＞一節已討論過目標群組。

接著，您必須決定每個群組的 Intune 推出時間表。 一般來說，Intune 部署小組與目標群組需要一起討論，以協助判斷最適合每個群組的推出時間表。

例如，Intune 部署小組可能會探討群組的變更意願、使用者和裝置數目、裝置平台類型、需求、地理位置和商業風險等因素，來決定推出時間表。

組織通常會選擇先從初始試驗來開始推出 Intune，並先以 IT 部門的一小組使用者為目標。 接著，即可擴充試驗，納入更多 IT 使用者並讓其他組織群組參與。 在試驗成功之後，組織即可以其他組織群組為目標，開始完整生產推出。下列為不同推出群組和階段的幾個範例：

-   **試驗：**推出的第一個階段目標應為試驗使用者。 試驗使用者應該了解他們是新方案的第一批使用者，並願意提供意見反應以協助改善設定、文件、通知，並為所有其他使用者簡化後續推出的方式。 這些使用者不應該是主管或 VIP。

-   **部門：**每個部門都可以是推出階段的目標。 在此案例中，我們會一次以整個部門為目標。 在這類推出中，每個階段幾乎都以相同方式使用行動裝置，並存取相同的應用程式。 使用者也幾乎會有相同類型的原則。

-   **地理位置：**這種類型的部署會針對特定地理位置中的所有使用者進行部署，不論是同一洲、國家/地區、區域或相同公司大樓。 這類分階段部署可讓您專注於特定位置的使用者。 這麼做可減少同時部署 Intune 的位置數量，確保進行過程更加[服務周全](#user-assisted-enrollment)。 由於相同的位置，可能會有不同的部門或使用案例，因此可能會同時部署不同的使用案例。

-   **平台：**這種類型的部署會同時針對類似平台進行部署。 例如，可能第一個月先進行所有 iOS 裝置的部署，接著進行 Android，之後是 Windows。 這類分階段部署有助於簡化技術服務人員的支援工作。 技術服務人員一次只需支援單一平台。

下列為 Intune 推出計畫的範例，包括目標群組和時間表：

| **推出階段** | **7 月** | **8 月** | **9 月** | **10 月** |
|:---:|:---:|:---:|:---:|:---:|
| 有限試驗 | IT (50 位使用者) |  |  |  |                                                         
| 擴充試驗 | IT (200 位使用者)、IT 主管 (10 位使用者) |  |  |  |                                                         
| 生產推出階段 1 |  | 銷售和行銷 (2000 位使用者) |  |  |
| 生產推出階段 2 |  |  | 零售 (1000 位使用者) |  |
| 生產推出階段 3 |  |  |  | 人力資源 (50 位使用者)、財務 (40 位使用者)、主管 (30 位使用者) |

## <a name="determine-the-intune-enrollment-approach"></a>決定 Intune 註冊方式

現在，您已經決定要推出 Intune 的目標群組和時間表，下一步是選擇最適合每個群組的 Intune 註冊方式。 組織可以使用不同的註冊方式來推出 Intune。 常見的註冊方法包括使用者自助、協助使用者註冊以及 IT 技術諮詢展。

### <a name="user-self-service"></a>使用者自助

使用這個方法時，通常需要使用者遵循其 IT 組織提供的註冊指示，自行註冊自己的裝置。 這個方法是組織最常用的方法，而且比協助使用者註冊的方法更加靈活。

### <a name="user-assisted-enrollment"></a>協助使用者註冊

這種是「服務周全」的方法，會由 IT 小組成員透過註冊程序親自或透過 Skype 來協助使用者。 通常，這種方法多用於主管級員工及其他在註冊程序期間可能需要更多協助的群組。

### <a name="it-tech-fair"></a>IT 技術諮詢展

另一種可讓 Intune 使用者註冊的選項是 IT 技術諮詢展。 在這場活動中，IT 群組會佈置一個 Intune 註冊的協助攤位，使用者可以到這裡來了解 Intune 註冊的資訊、提出問題並獲得註冊程序的協助。 採用這個選項，對 IT 群組和使用者都能帶來好處，尤其是在 Intune 推出初期階段。

以下是 Intune 推出計畫的範例，其中包含目標群組、時間表和註冊方法：

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
| 自助式 |  |  |  |  |
| 生產推出階段 3 |  |  | 零售 |  |
| 自助式 |  |  |  | 人力資源、財務 |
| 服務周全方式 |  |  |  | 主管 |

## <a name="next-section"></a>下一節

下一節提供[開發 Intune 推出通訊計畫](section-5-develop-a-rollout-communication-plan.md)的指引。


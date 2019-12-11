---
title: 識別使用案例
titleSuffix: Microsoft Intune
description: 本文可協助您識別 Intune 使用案例，以及適用於 Microsoft Intune 僅限雲端實作的次要使用案例。
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
ms.assetid: 4b3c9af9-78da-44d2-8bd2-3f0f8885952d
ms.reviewer: jeffbu, cgerth
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 96ebae46fd4935c3070319f16d35d5b53888e94c
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72505167"
---
# <a name="identify-mobile-device-management-use-case-scenarios"></a>識別行動裝置管理使用案例

若想成功部署 Intune，識別使用案例是規劃程序中很重要的一部分。 使用案例很有用，因為它們可讓您依使用者類型或角色，以及使用者裝置的擁有權 (例如公司或個人)，將使用者區分成可管理的群組。

接下來，我們會討論幾個範例，以協助組織識別 Intune 使用案例、組織群組，以及每個使用案例的相關聯行動裝置平台。

## <a name="device-ownership"></a>裝置擁有權
一開始，您可以先參考組織的 Intune 部署目的與目標，以協助識別部署的主要使用案例。 針對 Intune 部署計畫的範圍，回答下列問題：

- 您是否要支援公司擁有的裝置？

- 您是否要支援個人擁有的裝置？

這些不是單選題。 您可能會發現需要支援兩種形式的裝置擁有權，才能符合組織的目的。 次要使用案例將有助於釐清套用不同裝置管理原則的位置。

### <a name="user-type-or-device-role"></a>使用者類型或裝置角色

決定是否每個使用案例也都包含次要使用案例。 例如，您的組織識別出的需求可能要支援公司使用案例，其中包含以下列使用者類型或裝置角色為基礎的其他次要使用案例：

- 資訊工作者

- 主管

- Kiosk

以下是使用案例和次要使用案例的幾個範例：

| **使用案例** | **次要使用案例** |
|:---:|:---:|
| 公司 | 資訊工作者 |              
| 公司 | 主管 |           
| 公司 | Kiosk |
| BYOD | 資訊工作者 |           
| BYOD | 主管 |

您可以[下載上表的範本](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0)來輸入組織的使用案例和次要使用案例。

## <a name="organizational-groups-for-your-scenarios"></a>您案例的組織群組

現在，您必須識別每個使用案例和次要使用案例的相關聯組織群組。 例如：

| **使用案例** | **次要使用案例** | **組織群組** |
|:---:|:---:|:---:|
| 公司 | 資訊工作者 | 人力資源、財務 |               
| 公司 | 主管 | 人力資源、財務 |            
| 公司 | Kiosk | 零售 |
| BYOD | 資訊工作者 | 行銷、銷售 |            
| BYOD | 主管 | 行銷、銷售 |


## <a name="mobile-device-platforms-for-your-scenarios"></a>您案例的行動裝置平台

下一步是識別每個使用案例的相關聯行動裝置平台。 可能有多個平台。

例如，公司的使用案例可能支援 iOS 和 Android Samsung Knox 裝置平台。 您的 BYOD 原則可能包含對於其他行動裝置平台的支援，例如 Android (非 Samsung Knox) 和 Windows 10 行動裝置版。 以前述範例為基礎，我們已建立行動裝置平台與每個使用案例的關聯性。

| **使用案例** | **次要使用案例** | **群組** | **裝置平台** |   
|:---:|:---:|:---:|:---:|
| 公司 | 資訊工作者 | 人力資源、財務 | iOS |                                                           
| 公司 | 主管 | 人力資源、財務 | iOS |                                                           
| 公司 | Kiosk | 零售 | Android |
| BYOD | 資訊工作者 | 行銷、銷售 | iOS |                                                           
| BYOD | 主管 | 行銷、銷售 | iOS |

## <a name="next-steps"></a>後續步驟

下一節提供[如何識別每個使用案例的 Intune 需求](../planning-guide-requirements.md)的指引。

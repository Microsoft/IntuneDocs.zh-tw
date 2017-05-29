---
title: "識別 Intune 使用案例 | Microsoft Docs"
description: "本文可協助識別 Intune 使用案例，以及適用於 Microsoft Intune 僅限雲端實作的次要使用案例。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 12/20/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4b3c9af9-78da-44d2-8bd2-3f0f8885952d
ms.reviewer: jeffbu, cgerth
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 031820d505e0e9cb007e47a5397934d0e505aed4
ms.contentlocale: zh-tw
ms.lasthandoff: 05/23/2017


---

# <a name="identify-intune-use-case-scenarios"></a>識別 Intune 使用案例

[!INCLUDE[note for both-portals](../includes/note-for-both-portals.md)]

行動裝置管理使用案例會說明使用者類型或角色，以及其裝置的擁有權 (例如公司或個人)。 使用者案例非常實用，因為這些案例可讓您將使用者細分成可管理的群組。 若想成功部署 Intune，識別使用案例是規劃程序中很重要的一部分。

接下來，我們會討論幾個範例，以協助組織識別 Intune 使用案例、組織群組，以及每個使用案例的相關聯行動裝置平台。

## <a name="use-case-scenarios"></a>使用案例

一開始，您可以先參考組織的 Intune 部署目的與目標，以協助識別部署的主要使用案例。 針對 Intune 部署計畫的範圍，您必須回答下列問題：

-   您是否要支援公司擁有的裝置？

-   您是否要支援個人擁有的裝置？

### <a name="sub-use-case-scenarios"></a>次要使用案例

在識別主要使用案例之後，您必須判斷是否每個使用案例也會包含次要使用案例。 例如，組織識別出的需求可能要支援公司使用案例，並包含下列次要使用案例：

-   資訊工作者

-   主管

-   Kiosk

以下是使用案例和次要使用案例的幾個範例。 您也可以使用下表來輸入您組織的使用案例及次要使用案例：

| **使用案例** | **次要使用案例** |
|:---:|:---:|
| 公司 | 資訊工作者 |              
| 公司 | 主管 |           
| 公司 | Kiosk |
| BYOD | 資訊工作者 |           
| BYOD | 主管 |

## <a name="identify-organizational-groups-associated-with-use-case-scenarios"></a>識別與使用案例相關聯的組織群組

現在，您必須識別每個使用案例和次要使用案例的相關聯組織群組。 以下幾個範例包括與使用案例和次要使用案例相關聯的組織群組，您可以作為範本並輸入您組織的資訊：

| **使用案例** | **次要使用案例** | **組織群組** |
|:---:|:---:|:---:|
| 公司 | 資訊工作者 | 人力資源、財務 |               
| 公司 | 主管 | 人力資源、財務 |            
| 公司 | Kiosk | 零售 |
| BYOD | 資訊工作者 | 行銷、銷售 |            
| BYOD | 主管 | 行銷、銷售 |

## <a name="identify-mobile-device-platforms-for-use-case-scenarios"></a>識別使用案例適用的行動裝置平台

現在，您要識別每個使用案例的相關聯行動裝置平台。 比方說，公司的使用案例可能支援 iOS 和 Android Samsung KNOX 裝置平台，而 BYOD 原則可能支援其他行動裝置平台，例如 Android (非 Samsung KNOX) 和 Windows 10 行動裝置版。 下列為每個使用案例的相關聯行動裝置平台範例。 您可以使用下表，輸入與您的組織使用案例相關聯的裝置平台：

| **使用案例** | **次要使用案例** | **群組** | **裝置平台** |   
|:---:|:---:|:---:|:---:|
| 公司 | 資訊工作者 | 人力資源、財務 | iOS |                                                           
| 公司 | 主管 | 人力資源、財務 | iOS |                                                           
| 公司 | Kiosk | 零售 | Android |
| BYOD | 資訊工作者 | 行銷、銷售 | iOS |                                                           
| BYOD | 主管 | 行銷、銷售 | iOS |

## <a name="next-steps"></a>後續步驟

下一節提供[如何識別每個使用案例的 Intune 需求](section-3-determine-use-case-requirements.md)的指引。


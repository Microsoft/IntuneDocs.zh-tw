---
title: "判斷 Intune 使用案例需求 | Microsoft Docs"
description: "本文可協助判斷 Intune 使用案例，以及適用於 Microsoft Intune 僅限雲端實作的次要使用案例需求。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 12/20/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: fd8cb5f7-19f0-4d80-8825-2bafa49624af
ms.reviewer: jeffbu, cgerth
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: f807d6e4b20b98ecf622d1ebdd9db33b132a2e6a
ms.openlocfilehash: 91b25fe35c6a1f8a554d543ca005cc3b482f22d7
ms.lasthandoff: 12/30/2016


---

# <a name="determine-intune-use-case-scenario-requirements"></a>判斷使用案例的需求

[!INCLUDE[note for both-portals](../includes/note-for-both-portals.md)]

在本節中，您會判斷每個使用案例中每個組織群組的需求。 完成此程序可協助您針對其他 Intune 部署規劃領域 (如架構和設計、上架以及推出等)，更妥善進行準備。 此程序亦有助於找出可能的落差以及 Intune 部署專案的相關挑戰。

針對每個使用案例/次要使用案例，以及其相關聯的組織群組和行動裝置平台，您可能會有不同的需求。 例如，針對要向 Intune 註冊的裝置，公司的使用案例需求可能必須使用更嚴格的裝置限制 (例如 6 位 PIN 碼、停用雲端備份)；而「攜帶您自己的裝置」(BYOD) 的使用案例就可以使用較不嚴格的設定 (例如 4 位 PIN 碼、允許雲端備份)。

針對公司的使用案例，您的組織群組也可以有幾組不同的需求 (例如 PIN 碼設定、Wi-Fi 或 VPN 設定檔、部署的應用程式)。 此外，您的需求也可能取決於行動裝置平台的功能 (例如指紋辨識器、電子郵件設定檔) 而定。

以下是一些組織使用案例需求的範例，其中說明每個使用案例/次要使用案例、組織群組和行動裝置平台的不同需求。 您也可以使用下表來輸入您的組織使用案例需求：

| **使用案例** | **次要使用案例** | **群組** | **裝置作業系統平台** | **Requirements** |
|:---:|:---:|:---:|:---:|:---:|
| 公司 | 資訊工作者 | 人力資源、財務 | iOS | 安全電子郵件、裝置設定、設定檔、應用程式 |                                                          
| 公司 | 主管 | 人力資源、財務 | iOS | 安全電子郵件、裝置設定、設定檔、應用程式 |                                                         
| 公司 | Kiosk | 零售 | Android | 裝置設定、設定檔、應用程式 |
| BYOD | 資訊工作者 | 行銷、銷售 | iOS | 安全電子郵件、裝置設定、設定檔、應用程式 |                                                         
| BYOD | 主管 | 行銷、銷售 | iOS | 安全電子郵件、裝置設定、設定檔、應用程式 |

## <a name="examples-of-requirements"></a>需求範例

下列幾個範例可用於上表的「需求」資料行：

- **安全電子郵件**
    - Exchange Online/內部部署的條件式存取
    - Outlook 應用程式保護原則
<br></br>
- **裝置設定**
    - 4、6 個字元 PIN 碼設定
    - 限制雲端備份
<br></br>
- **設定檔**
    - Wi-Fi
    - VPN
    - 電子郵件 (Windows 10 行動裝置版)
<br></br>
- **應用程式**
    - Office 365 與應用程式保護原則
    - 企業營運 (LOB) 與應用程式保護原則

## <a name="next-section"></a>下一節

下一節提供[如何開發 Intune 推出計畫](section-4-develop-a-rollout-plan.md)的指引。


---
title: 決定使用案例的需求
titleSuffix: Microsoft Intune
description: 本文可協助您判斷 Intune 使用案例，以及適用於 Microsoft Intune 僅限雲端實作的次要使用案例需求。
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: fd8cb5f7-19f0-4d80-8825-2bafa49624af
ms.reviewer: jeffbu, cgerth
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 703509c316a22995d26223f6c386de0a2ec66c31
ms.sourcegitcommit: 7c251948811b8b817e9fe590b77f23aed95b2d4e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "67882727"
---
# <a name="determine-use-case-scenario-requirements"></a>決定使用案例的需求

在本節中，您會判斷每個使用案例中每個組織群組的需求。 此程序可協助您準備其他 Intune 部署規劃領域 (如架構和設計、上架以及推出等)。 此程序亦有助於找出可能的落差以及 Intune 部署專案的相關挑戰。

針對每個使用案例與次要使用案例，以及其相關聯的組織群組和行動裝置平台，您可能會有不同的需求。 比方說，您的企業使用案例需求可能需要將裝置註冊到 Intune，但必須使用一組限制更高的裝置設定，例如 6 個字元的 PIN 碼或已停用的雲端備份。 您的「攜帶您自己的裝置」(BYOD) 使用案例可能限制較低，允許 4 個字元的 PIN 碼與雲端備份。

針對公司的使用案例，您的組織群組也可以有幾組不同的需求 (例如 PIN 碼設定、Wi-Fi 或 VPN 設定檔、部署的應用程式)。 您的需求也可能取決於行動裝置平台的功能 (例如指紋辨識器、電子郵件設定檔) 而定。

以下是一些組織使用案例需求的範例，其中說明每個使用案例與次要使用案例、組織群組和行動裝置平台的不同需求。 您也可以使用下表來輸入您的組織使用案例需求：

| **使用案例** | **次要使用案例** | **群組** | **裝置平台** | **需求** |
|:---:|:---:|:---:|:---:|:---:|
| 公司 | 資訊工作者 | 人力資源、財務 | iOS | 安全電子郵件、裝置設定、設定檔、應用程式 |                                                          
| 公司 | 主管 | 人力資源、財務 | iOS | 安全電子郵件、裝置設定、設定檔、應用程式 |                                                         
| 公司 | Kiosk | 零售 | Android | 裝置設定、設定檔、應用程式 |
| BYOD | 資訊工作者 | 行銷、銷售 | iOS | 安全電子郵件、裝置設定、設定檔、應用程式 |                                                         
| BYOD | 主管 | 行銷、銷售 | iOS | 安全電子郵件、裝置設定、設定檔、應用程式 |

您可以[下載上表的範本](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0)來輸入組織的使用案例和子使用案例需求。


## <a name="examples-of-requirements"></a>需求範例

下列幾個範例可用於「需求」資料行：

- **安全電子郵件**
  - Exchange Online / 內部部署的條件式存取
  - Outlook 應用程式保護原則

- **裝置設定**
  - 4、6 個字元 PIN 碼設定
  - 限制雲端備份

- **設定檔**
  - Wi-Fi
  - VPN
  - 電子郵件 (Windows 10 行動裝置版)

- **應用程式**
  - Office 365 與應用程式保護原則
  - 企業營運 (LOB) 與應用程式保護原則

## <a name="next-steps"></a>後續步驟

下一節提供[如何開發 Intune 推出計畫](planning-guide-rollout-plan.md)的指引。

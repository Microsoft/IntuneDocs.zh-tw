---
title: Intune Mobile Threat Defense | Microsoft Docs
description: "根據裝置風險，保護對公司資源的存取。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/01/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 08d87906-8158-4d5e-a49d-ad919efef3d1
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 56cd18e1a5556178d951ec47c6e894d8fc2e6f86
ms.contentlocale: zh-tw
ms.lasthandoff: 05/23/2017


---

# <a name="intune-mobile-threat-defense-connectors"></a>Intune Mobile Threat Defense 連接器

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Intune Mobile Threat Defense 連接器可讓您以所選的 Mobile Threat Defense 廠商，作為合規性政策和條件式存取規則的資訊來源。 這可讓 IT 系統管理員對其公司資源 (例如 Exchange 和 Sharepoint) 新增一層保護，特別是來自受危害之行動裝置的資源。

## <a name="what-problem-does-this-solve"></a>這會解決哪個問題？

公司必須保護機密資料免於遭受新興威脅 (包括實體、應用程式型和網路型威脅) 以及作業系統漏洞的攻擊。
在過去，公司已經主動保護電腦免受攻擊，但行動裝置則不受監視且未受保護。 行動平台具有應用程式隔離和經審核的消費者 App Store 這類內建保護，但這些平台仍然容易受到複雜的攻擊。 現在，多位員工使用裝置進行工作，而且需要存取機密資訊。 裝置必須受到保護，以免受到更複雜的攻擊。

## <a name="how-the-intune-mobile-threat-defense-connectors-work"></a>Intune Mobile Threat Defense 連接器如何運作？

連接器會透過在 Intune 與您選擇的 Mobile Threat Defense 廠商之間建立通訊通道來保護公司資源。 Intune Mobile Threat Defense 合作夥伴提供直覺且易於部署行動裝置的應用程式，而行動裝置會主動掃描並分析威脅資訊以與 Intune 共用，來進行報告或強制執行。 例如，如果連線的 Mobile Threat Defense 應用程式會回報到 Mobile Threat Defense 廠商，而它在您網路上的電話目前連線至易受攔截式攻擊的網路，則這項資訊會與適當的風險層級 (低/中/高) 共用，並分類為適當的風險層級 (低/中/高)；接著可以比較該層級與 Intune 中設定的允許風險層級，來判定危害裝置時是否應該撤銷所選擇特定資源的存取權。

## <a name="sample-scenarios"></a>範例案例

將裝置視為受到 Mobile Threat Defense 解決方案所感染時︰

![Mobile Threat Defense 受感染的裝置](../media/mtp/MTD-image-1.png)

補救裝置時，會授與存取權︰

![Mobile Threat Defense 已授與存取權](../media/mtp/MTD-image-2.png)

## <a name="mobile-threat-defense-partners"></a>Mobile Threat Defense 合作夥伴

了解如何使用下列項目，根據裝置、網路和應用程式風險來保護對公司資源的存取：

- [Lookout](/intune-classic/deploy-use/lookout-mobile-threat-defense-connector)
- [Skycure (英文)](/intune-classic/deploy-use/skycure-mobile-threat-defense-connector)


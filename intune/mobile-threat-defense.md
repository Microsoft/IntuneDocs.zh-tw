---
title: Mobile Threat Defense 與 Microsoft Intune | Microsoft Intune
description: 使用 Intune Mobile Threat Defense (MTD)，與您的 Mobile Threat Defense 夥伴根據裝置的風險來保護公司資源的存取權。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/28/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ac77b590-a7ec-45a0-9516-ebf5243b6210
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 18161e8293ae92420f9437dab18e008e8e57b93a
ms.sourcegitcommit: bee072b61cf8a1b8ad8d736b5f5aa9bc526e07ec
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53816594"
---
# <a name="what-is-mobile-threat-defense-integration-with-intune"></a>Mobile Threat Defense 與 Intune 的整合是什麼？


Intune Mobile Threat Defense 連接器可讓您以所選的 Mobile Threat Defense 廠商，作為合規性政策和條件式存取規則的資訊來源。 這可讓 IT 系統管理員對 Exchange 和 Sharepoint 這類公司資源增添一道保護，特別是防止來自遭盜用之行動裝置的威脅。

## <a name="what-problem-does-this-solve"></a>這會解決哪個問題？

公司必須保護機密資料免於遭受新興威脅 (包括實體、應用程式型和網路型威脅) 以及作業系統漏洞的攻擊。

在過去，公司已經主動保護電腦免受攻擊，但行動裝置則不受監視且未受保護。 行動平台具有應用程式隔離和經審核的消費者 App Store 這類內建保護，但這些平台仍然容易受到複雜的攻擊。 現在，多位員工使用裝置進行工作，而且需要存取機密資訊。 裝置必須受到保護，以免受到更複雜的攻擊。

## <a name="how-do-the-intune-mobile-threat-defense-connectors-work"></a>Intune Mobile Threat Defense 連接器如何運作？

連接器會透過在 Intune 與您選擇的 Mobile Threat Defense 廠商之間建立通訊通道來保護公司資源。 Intune Mobile Threat Defense 合作夥伴提供直覺且易於部署行動裝置的應用程式，而行動裝置會主動掃描並分析威脅資訊以與 Intune 共用，來進行報告或強制執行。 

例如，如果連線的 Mobile Threat Defense 應用程式會回報給 Mobile Threat Defense 廠商，而它在您網路上的電話目前連線至易受攔截式攻擊的網路，則這項資訊會與適當的風險層級 (低/中/高) 共用，並分類為適當的風險層級 (低/中/高)；接著可以比較該層級與 Intune 中設定的允許風險層級，來判定危害裝置時是否應該撤銷所選擇特定資源的存取權。

## <a name="what-data-does-intune-collect-for-mobile-threat-defense"></a>Intune 會收集哪些 Mobile Threat Defense 資料？

如果啟用，Intune 會從個人和公司擁有的裝置收集應用程式清查資訊，供 Mobile Threat Defense (MTD) 提供者擷取，例如 Lookout for Work。 您可以收集 iOS 裝置使用者的應用程式清查。

此服務為選擇性；預設不會共用應用程式清查資訊。 Intune 系統管理員必須在服務設定中啟用 iOS 裝置的應用程式同步，才能共用任何應用程式清查資訊。

**應用程式清查**  
如果您啟用 iOS 裝置的應用程式同步，公司和個人擁有的 iOS 裝置清查都會傳送給您的 MTD 服務提供者。 應用程式清查中的資料包括：

 - 應用程式識別碼
 - 應用程式版本
 - 應用程式簡短版本
 - 應用程式名稱
 - 應用程式套件組合大小
 - 應用程式動態大小
 - 應用程式是否已驗證
 - 應用程式是否受控

## <a name="sample-scenarios"></a>範例案例

將裝置視為受到 Mobile Threat Defense 解決方案所感染時︰

![顯示 Mobile Threat Defense 受感染裝置的圖片](./media/MTD-image-1.png)

補救裝置時，會授與存取權︰

![顯示授與 Mobile Threat Defense 存取權的圖片](./media/MTD-image-2.png)

> [!NOTE] 
> 不支援搭配 Intune 使用多個 Mobile Threat Defense 供應商。 如果您啟用多個 MTD 工具，系統會強制安裝所有 MTD 應用程式並掃描所有裝置是否有潛在威脅。

## <a name="mobile-threat-defense-partners"></a>Mobile Threat Defense 合作夥伴

了解如何使用下列項目，根據裝置、網路和應用程式風險來保護對公司資源的存取：

- [Lookout](lookout-mobile-threat-defense-connector.md)
- [Symantec Endpoint Protection Mobile](skycure-mobile-threat-defense-connector.md)
- [Check Point SandBlast Mobile](checkpoint-sandblast-mobile-mobile-threat-defense-connector.md)
- [Zimperium](zimperium-mobile-threat-defense-connector.md)
- [Pradeo](pradeo-mobile-threat-defense-connector.md)
- [Better Mobile](better-mobile-threat-defense-connector.md)

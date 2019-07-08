---
title: Mobile Threat Defense 與 Microsoft Intune
titleSuffix: Microsoft Intune
description: 使用 Intune Mobile Threat Defense (MTD)，與您的 Mobile Threat Defense 夥伴根據裝置的風險來保護公司資源的存取權。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ac77b590-a7ec-45a0-9516-ebf5243b6210
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0452229d6c1ea2d9e87a302675167d200bd348eb
ms.sourcegitcommit: 6bba9f2ef4d1ec699f5713a4da4f960e7317f1cd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2019
ms.locfileid: "67407163"
---
# <a name="what-is-mobile-threat-defense-integration-with-intune"></a>Mobile Threat Defense 與 Intune 的整合是什麼？
Intune 可整合來自 Mobile Threat Defense 廠商的資料，作為合規性政策和條件式存取規則的資訊來源。 您可以利用這項資訊，藉由封鎖遭入侵行動裝置的存取，來協助保護 Exchange 和 Sharepoint 等公司資源。  

## <a name="what-problem-does-this-solve"></a>這會解決哪個問題？
整合來自 Mobile Threat Defense 廠商的資訊可協助您保護公司資源，以防範影響行動平台的威脅。  

一般而言，公司會主動保護電腦以防範弱點和攻擊，但行動裝置通常不受監視且未受保護。 雖然行動平台具有應用程式隔離和經審核的消費者 App Store 這類內建保護，但這些平台仍然容易受到複雜的攻擊。 隨著愈來愈多的員工使用工作用裝置來存取敏感性資訊，來自 Mobile Threat Defense 廠商的資訊可協助您保護裝置和資源，以防範愈來愈複雜的攻擊。  

## <a name="how-do-the-intune-mobile-threat-defense-connectors-work"></a>Intune Mobile Threat Defense 連接器如何運作？

Intune 使用 Mobile Threat Defense 連接器，在 Intune 與您選擇的 Mobile Threat Defense 廠商之間建立通訊通道。 Intune Mobile Threat Defense 合作夥伴提供直覺且易於部署的行動裝置應用程式。 這些應用程式可主動掃描並分析威脅資訊以與 Intune 共用。 Intune 可以使用此資料來進行報告或強制執行。  

例如：已連線的 Mobile Threat Defense 應用程式會向 Mobile Threat Defense 廠商回報您網路上手機目前連線至易受中間人攻擊的網路。 這項資訊會分類為低、中或高的適當風險層級。 此風險層級接著可與您在 Intune 中設定的允許風險層級進行比較。 根據這項比較，您就可在裝置遭入侵時，撤銷對您所選特定資源的存取權。

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
- [Sophos Mobile](sophos-mtd-connector.md)
- [Wandera Mobile Threat Defense](wandera-mtd-connector.md)

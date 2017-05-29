---
title: "啟動 Intune 移轉活動 | Microsoft Docs"
description: "本文旨在提供如何啟動移轉活動的指引。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/24/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f781b029-50f2-46ee-8ff7-03b4a6719e80
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: e98730105044d2147d9be37002fc20ec2de8eb0e
ms.contentlocale: zh-tw
ms.lasthandoff: 05/23/2017


---

# <a name="phase-2-migration-campaign"></a>階段 2：移轉活動

[!INCLUDE[note for both-portals](../includes/note-for-both-portals.md)]

組織應採用最適合他們需求的移轉方法，並根據其特定需求來調整實作策略。 本指南的其餘部分將提供完成將使用者的裝置註冊到 Intune 所需的工具。

## <a name="keys-to-a-successful-migration"></a>成功移轉的關鍵

這些是從協力廠商 MDM 提供者移轉到 Intune 時學習到的關鍵經驗︰

-   若要盡可能減少使用者停機時間和提高滿意度，溝通是一大關鍵。

-   請務必提供特定且具體的移轉指示。

-   在於 Intune 註冊之前，所有受管理的裝置都必須先從現有的 MDM 提供者取消註冊。

-   請提供使用者由現有的 MDM 提供者所提供關於如何取消註冊其裝置的指引。

-   使用階段性方法。 從一個試驗使用者小組開始，然後逐漸增加更多使用者群組，直到您到達完整部署為止。

-   監視每個週期的支援人員負載和註冊成功數。 在排程中保留時間，確保針對每個群組評估成功準則後再進行下一階段的移轉。 您的試驗部署應該驗證下列各項︰

    -   註冊的成功和失敗率符合期望。

    -   使用者生產力：

        -   公司資源 (例如 VPN、Wi-Fi、電子郵件及憑證) 運作良好。

        -   佈建的應用程式可供存取。

    -   資料安全性：

        -   合規性報告

        -   強制的行動裝置應用程式保護

-   當您滿意第一階段的移轉後，重複執行移轉週期 (如＜典型的移轉週期＞所述) 以進行下一階段。

-   重複階段週期，直到所有使用者都移轉至 Intune 為止。

-   請確定支援人員小組在整個移轉活動期間隨時可支援使用者。 在可預估支援通話的工作負載之前，請執行自願性移轉。

-   在您的支援人員可以處理其餘的使用者數量之前，不要設定註冊的截止日期

> [!IMPORTANT] 
> 不要將 Intune 和現有的協力廠商 MDM 解決方案設為套用對 Exchange 或 SharePoint Online 等資源的存取控制。 此外，裝置一次只能在一個解決方案中註冊。

## <a name="next-steps"></a>後續步驟

[階段 2：溝通計劃](/intune-classic/plan-design/migration-phase2-communication-plan)


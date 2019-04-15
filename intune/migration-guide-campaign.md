---
title: 啟動 Intune 移轉活動
titleSuffix: Microsoft Intune
description: 本文提供如何啟動 Microsoft Intune 移轉活動的指引。
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f781b029-50f2-46ee-8ff7-03b4a6719e80
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: db56bbc180a84e8b3972ffc6473126efd366faa8
ms.sourcegitcommit: 484a898d54f5386fdbce300225aaa3495cecd6b0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/01/2019
ms.locfileid: "59568267"
---
# <a name="phase-2-migration-campaign"></a>階段 2：移轉活動

選擇最符合組織需求的移轉方法，並根據您的特定需求來調整實作策略。 本指南的其餘部分提供完成將使用者的裝置註冊到 Intune 的目標所需的工具。

## <a name="keys-to-a-successful-migration"></a>成功移轉的關鍵

這些是從協力廠商 MDM 提供者成功移轉至 Intune 的關鍵：

-   清晰且有效的溝通可以最大限度地減少使用者的停機時間和不滿程度。

-   請務必提供特定且具體的移轉指示。

-   在 Intune 中進行註冊之前，所有受管理的裝置都必須先從現有的 MDM 提供者取消註冊。

-   請提供使用者由現有的 MDM 提供者所提供之關於如何取消註冊其裝置的指引。

-   使用階段性方法。 從一個試驗使用者小組開始，然後逐漸增加更多使用者群組，直到您到達完整部署為止。

-   監視每個週期的技術服務人員負載和註冊成功數。 在排程中保留時間，確保針對每個群組評估成功準則後再進行下一階段的移轉。 您的試驗部署應該驗證下列各項︰

    -   註冊的成功和失敗率符合期望。

    -   使用者生產力：

        -   公司資源 (例如 VPN、Wi-Fi、電子郵件及憑證) 運作良好。

        -   佈建的應用程式可供存取。

    -   資料安全性：

        -   正進行合規性報告。

        -   會強制執行行動裝置應用程式保護。

當您滿意第一階段的移轉後，重複執行[移轉週期](migration-guide-cycle.md) 以進行下一階段。

-   重複階段週期，直到所有使用者都移轉至 Intune 為止。

-   請確定技術服務小組在整個移轉活動期間隨時可支援使用者。 在可預估支援通話的工作負載之前，請執行自願性移轉。

-   在您的技術服務人員可以處理其餘的使用者數量之前，不要設定註冊的截止日期

> [!IMPORTANT]
> 不要將 Intune 和現有的協力廠商 MDM 解決方案設為套用對 Exchange 或 SharePoint Online 等資源的存取控制。 此外，裝置一次只能在一個解決方案中註冊。

## <a name="next-steps"></a>後續步驟

建立[溝通計劃](migration-guide-communication-plan.md)。

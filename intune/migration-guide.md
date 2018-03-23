---
title: Intune 行動裝置管理移轉指南
titlesuffix: Microsoft Intune
description: 本指南將逐步解說有關從協力廠商 MDM 提供者移轉到 Microsoft Intune 的各種詳細資料。
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: dcfc21f9-1bcd-4371-a46d-f2e18154ec50
ms.reviewer: dagerrit
ms.suite: ems
ms.openlocfilehash: 9bfefff2ef5960b6e52a8a37c2fd31466d16cbff
ms.sourcegitcommit: e30fb2375fb79f67e5c1e4ed7b2c21fb9ca80c59
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2018
---
# <a name="intune-migration-guide"></a>Intune 移轉指南

![Microsoft Intune MDM 移轉指南圖案](./media/MDM-migration-guide-art.PNG)

若要成功移轉至 Microsoft Intune，需要先有一個詳實的計劃，其中通盤考量您目前的行動裝置管理 (MDM) 環境、業務目標和技術需求。 此外，您還需要包含將支援和協作移轉計劃的重要關係人。

本指南將逐步解說有關從協力廠商 MDM 提供者移轉到 Intune 的各種詳細資料。

## <a name="whats-included-in-this-guide"></a>本指南包含哪些內容？

本指南將移轉分成兩個階段，這兩者都包含工作、策略和策略性指南，將協助您逐步完成移轉至 Intune MDM 的端對端程序。

-   [階段 1：準備 Intune 以用於行動裝置管理](migration-guide-prepare.md)

    -   [評估您 MDM 移轉需求](migration-guide-prepare.md#assess-mdm-requirements)

    -   [基本設定](migration-guide-setup.md)

    -   [設定裝置與應用程式管理原則](migration-guide-configure-policies.md)

    -   [設定應用程式保護原則](migration-guide-app-protection-policies.md)

    -   [特殊移轉考量](migration-guide-considerations.md)

-   [階段 2：移轉活動](migration-guide-campaign.md)

    -   [通訊計畫](migration-guide-communication-plan.md)

    -   [使用條件式存取引導使用者採用](migration-guide-drive-adoption.md)

    -   [典型移轉週期](migration-guide-cycle.md)
        -   [監視移轉](migration-guide-cycle.md#monitoring-migration)
        -   [移轉後工作](migration-guide-cycle.md#post-migration)

## <a name="assumptions"></a>假設

-   您已經在概念證明 (PoC) 環境中評估過 Intune，並決定使用它作為組織中的 MDM 解決方案。

-   您已經熟悉 Intune 和其功能。

## <a name="before-you-begin"></a>開始之前

請務必了解新的 Intune 部署可能會與舊的 MDM 部署不同。 不同於傳統的 MDM 服務，Intune 著重在身分識別導向的存取控制，因此不需使用網路 Proxy 設備，對組織周邊網路以外的行動裝置控制公司資料的存取。 Microsoft 透過一套緊密整合的雲端服務 (統稱為「企業用戶端 + 安全性」供應項目)，提供保護雲端本身內之資料服務的解決方案。

-   請檢閱[使用 Intune 的常見方式](common-scenarios.md)。

## <a name="next-steps"></a>接下來的步驟

[階段 1：準備 Intune 以用於行動裝置管理](migration-guide-prepare.md)

---
title: "Intune 行動裝置管理 (MDM) 移轉指南 | Microsoft Docs"
description: "本指南旨在提供客戶與從協力廠商 MDM 提供者移轉到 Microsoft Intune 有關的各種詳細資料。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/24/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: dcfc21f9-1bcd-4371-a46d-f2e18154ec50
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 8da2695c4c6dc8b45559323b83a4bb77167303b7
ms.openlocfilehash: 444cb61ea57b92924a681c564a1a913f4204ea89
ms.lasthandoff: 03/28/2017


---

# <a name="intune-migration-guide"></a>Intune 移轉指南

[!INCLUDE[note for both-portals](../includes/note-for-both-portals.md)]

![Intune MDM 移轉指南圖案](../media/MDM-migration-guide-art.PNG)

要成功移轉至 Intune，首先需要一個通盤考量目前的 MDM 環境、業務目標和技術需求的詳實計劃。 此外，您還需要將支援和協作移轉計劃的重要關係人。

本指南旨在提供您與從協力廠商 MDM 提供者移轉到 Intune 有關的各種詳細資料。

## <a name="whats-included-in-this-guide"></a>本指南包含哪些內容？

本指南包含兩個階段，這兩者都包含工作、策略和策略性指南，將協助您逐步完成移轉至 Intune MDM 的端對端程序。

-   [階段 1：準備 Intune 以用於行動裝置管理 (MDM)](https://docs.microsoft.com/intune/plan-design/migration-phase1-prepare-intune-for-mobile-device-management)

    -   [評估您 MDM 移轉需求](https://docs.microsoft.com/intune/plan-design/migration-phase1-prepare-intune-for-mobile-device-management#assess-mdm-requirements)

    -   [基本設定](https://docs.microsoft.com/intune/plan-design/migration-phase1-basic-setup)

    -   [設定裝置與應用程式管理原則](https://docs.microsoft.com/intune/plan-design/migration-phase1-configure-device-and-app-management-policies)

    -   [設定應用程式保護原則 (選用)](https://docs.microsoft.com/intune/plan-design/migration-phase1-configure-app-protection-policies)

    -   [特殊移轉考量](https://docs.microsoft.com/intune/plan-design/migration-phase1-special-migration-considerations)

-   [階段 2：移轉活動](https://docs.microsoft.com/intune/plan-design/migration-phase2-migration-campaign)

    -   [溝通計劃](https://docs.microsoft.com/intune/plan-design/migration-phase2-communication-plan)

    -   [使用條件式存取引導使用者採用](https://docs.microsoft.com/intune/plan-design/migration-phase2-drive-end-user-adoption-with-conditional-access)
    
    -   [典型的移轉週期](https://docs.microsoft.com/intune/plan-design/migration-phase2-typical-migration-cycle)
        -   [監視移轉](https://docs.microsoft.com/intune/plan-design/migration-phase2-typical-migration-cycle#monitoring-migration)
        -   [移轉後工作](https://docs.microsoft.com/intune/plan-design/migration-phase2-typical-migration-cycle#post-migration)

## <a name="assumptions"></a>假設

-   您已經在概念證明 (PoC) 環境中評估過 Intune，並決定使用它作為組織中的 MDM 解決方案。

-   您已經熟悉 Intune 和其功能。 

> [!NOTE]
> 如果您想在移轉之前更熟悉 Intune，請參閱 [Intune 評估指南](https://docs.microsoft.com/intune/understand-explore/sign-up-for-30-day-trial-microsoft-intune)。

## <a name="before-you-begin"></a>開始之前

請務必了解新的 Intune 部署可能會與舊的 MDM 部署不同。 不同於傳統的 MDM 服務，Intune 著重在身分識別導向的存取控制，因此不需使用網路 Proxy 設備，對組織周邊網路以外的行動裝置控制公司資料的存取。 Microsoft 透過一套緊密整合的雲端服務 (統稱為「企業用戶端 + 安全性」供應項目)，提供保護雲端本身內之資料服務的解決方案。

-   請複習[使用 Intune 的常見方式](https://docs.microsoft.com/intune/understand-explore/common-ways-to-use-intune)，並開始編輯[階段 1：評估 MDM 需求](https://docs.microsoft.com/intune/plan-design/migration-phase1-prepare-intune-for-mobile-device-management#assess-mdm-requirements)中的問題答案。

## <a name="next-steps"></a>後續步驟

[階段 1：準備 Intune 以用於行動裝置管理 (MDM)](https://docs.microsoft.com/intune/plan-design/migration-phase1-prepare-intune-for-mobile-device-management)


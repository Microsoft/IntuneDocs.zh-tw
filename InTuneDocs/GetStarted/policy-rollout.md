---
title: "原則首度發行 | Microsoft Intune"
description: 
keywords: 
author: Nbigman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 390d5adf-86d2-4e23-ba93-1e61e6b1028b
ms.reviewer: tscott
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: d82d0ae4820d2e2141848235b8741abccaec3bc6
ms.openlocfilehash: 8935fbc42d7b406a5bcdbfc4353209b4447ae413


---

# 原則首度發行
本主題提供 Microsoft Intune 中原則階段式首度發行的特定建議事項。 這種方法適用於您在新的 Intune 部署中，將套用的第一個原則，或您加入至現有部署的原則。

如需首度發行階段的一般資訊，請參閱 [Microsoft Intune 部署的首度發行階段](rollout-phases-for-microsoft-intune-deployment.md)。

### 原則首度發行的階段
原則首度發行的階段為︰

-   專案範圍

-   概念證明

-   試驗

-   企業首度發行

-   操作和維護

## 專案範圍
定義 Intune 原則部署的範圍︰

-   針對新實作，這將需要定義所有所需的裝置行為，以及您想要建立使用原則集建立的安全性需求。

-   決定您想要使用這些原則影響的使用者和裝置。

-   設計您的使用者和裝置群組，可讓您適當地套用新原則。

-   判斷是否有會影響您的原則目標的每個作業系統相關聯的限制或需求。

-   考慮原則設計特性，例如要使用的原則類型和範本。

-   無論您正在啟動第一個原則集或是將新的原則加入至現有的原則集，請考慮各種原則如何互動，以及可能會有的裝置行為。 在試驗階段中可以找到原則互動和衝突的問題，但在早期規劃中攔截原則衝突將可簡化試驗的執行。

## 概念證明
在概念證明階段中，在您針對測試用途嚴格設定的裝置和使用者上，於實驗室環境中測試原則部署。

-   讓技術支援人員參與此階段，了解在試驗和生產部署中可能發生的問題。 [Microsoft Intune 的原則疑難排解](/intune/troubleshoot/troubleshoot-policies-in-microsoft-intune)中有提供疑難排解資訊。

-   在此程序時點中，您應該開發試驗和生產使用者的通訊計劃。 計劃應至少包含哪些裝置行為會變更以及何時、變更的商務用途，以及如果使用者或 IT 人員遇到問題時該怎麼辦，提供自助資訊和如何連絡技術支援人員。

## 試驗
在試驗期間，您會將原則部署到測試使用者和裝置的一個小群組。 在 Intune 中試驗原則有特定的考量事項︰

-   測試群組應該是將針對生產首度發行套用原則之群組的代表。

-   教育技術服務人員有關原則中的變更，並確定他們準備好協助測試群組中的使用者。

-   啟動您的試驗使用者通訊計劃。

-   可以先在隔離模式中完成試驗，其中裝置不受限於可能會造成衝突和非預期的行為的其他原則。

-   最終測試必須考慮會套用至相同的裝置的新原則和所有現有原則。

## 企業首度發行

-   根據試驗的結果調整您計劃的原則，以更正原則衝突和非預期的行為。

-   通知企業首度發行排程的技術支援人員。 備妥機制以回應協助要求，並視需要調整首度發行。

-   準備好在發生問題時疑難排解原則。

-   啟動您的生產使用者通訊計劃。

-   以遞增方式將原則套用至其他群組，監視受影響裝置的原則狀態，以及追蹤可能與新原則相關的技術支援人員要求。

## 操作和維護
**作業︰**監視 Intune 主控台，以取得警示和使用者或裝置問題，並檢查原則正根據您的設計執行。

**技術支援人員︰**確保技術服務人員知道會影響使用者經驗之原則的任何變更，因為這些可能會導致支援要求。


### 請參閱
[準備使用 Microsoft Intune 設定行動應用程式管理原則](/intune/deploy-use/get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune)

[Microsoft Intune 的原則疑難排解](/intune/troubleshoot/troubleshoot-policies-in-microsoft-intune)



<!--HONumber=Jun16_HO4-->



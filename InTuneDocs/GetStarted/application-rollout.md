---
title: "應用程式首展 |Microsoft Intune"
description: 
keywords: 
author: Nbigman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0fc32ed3-bcf4-472a-80e7-eb20986f78fa
ms.reviewer: tscott
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: d82d0ae4820d2e2141848235b8741abccaec3bc6
ms.openlocfilehash: 4a237942b4bc1e411cf55bc34c7b86d2249c526e


---

# 應用程式首展
本主題提供特定的建議事項，適用於 Microsoft Intune 中的應用程式階段首展。 如需首度發行階段的一般資訊，請參閱 [Microsoft Intune 部署的首度發行階段](rollout-phases-for-microsoft-intune-deployment.md)。

### 應用程式首展的階段
應用程式首展的階段為：

-   專案範圍

-   概念證明

-   試驗

-   企業首度發行

-   操作和維護

## 專案範圍
請考慮下列事項：

-   應用程式欲啟用的使用者工作。

-   您的使用者及其裝置的應用程式適用性 (可能使用的所有作業系統)。

-   請檢查您選擇的應用程式的安裝程式受 Intune 應用程式散發支援，如[使用 Microsoft Intune 新增應用程式](/intune/deploy-use/add-apps)所述。

-   確定已安裝應用程式散發必要條件。 <!---, as described in [Plan for app deployment in Microsoft Intune](plan-for-app-deployment-in-microsoft-intune.md--->)。

-   判斷應用程式類型受 Intune 支援。

-   檢查您擁有足夠的可用雲端儲存空間以上傳應用程式。 [使用 Microsoft Intune 新增應用程式](/intune/deploy-use/add-apps)中提供購買額外儲存空間的指示。

> [!NOTE]           
> 您可以下載此[行動應用程式規劃範本](https://gallery.technet.microsoft.com/Mobile-app-planning-18689d59)來協助您的首度發行程序。

## 概念證明
在概念證明階段中，在您針對測試用途嚴格測試的裝置和使用者上，於實驗室環境中測試應用程式部署。

-   讓技術支援人員參與此階段，了解在試驗和生產部署中可能發生的問題。 [Microsoft Intune 的應用程式部署問題疑難排解](/intune/troubleshoot/troubleshoot-app-deployment-problems-in-microsoft-intune)中有提供疑難排解資訊。

-   在此程序時點中，您應該開發試驗和生產使用者的通訊計劃。 計劃至少應該包含正在部署哪些應用程式、使用者如何及何時取得它、開發的商務用途，及遇到問題該怎麼辦 (自助資訊和如何連絡技術支援人員)。

## 試驗
在試驗期間，您會將應用程式部署到測試使用者和裝置的一個小群組。 請考慮下列事項：

-   請確定測試群組是代表使用者和裝置，將會在生產首展之後使用應用程式。

-   教育技術服務人員有關應用程式的部署，並確定它們準備好協助測試群組中的使用者。

-   選擇會以一般方式使用應用程式，並且可靠地向試驗系統管理員報告問題的並測試使用者。

-   啟動您的試驗使用者通訊計劃。

## 企業首度發行

-   使用試驗結果來調整您的企業首度發行。

-   通知應用程式首展排程的技術支援人員。 備妥機制以回應協助要求，並視需要調整首展。

-   準備好疑難排解發生的部署問題。

-   啟動您的生產使用者通訊計劃。

-   使用階段性部署應用程式方式，逐漸新增群組以確保首展順利進行。

## 操作和維護
**作業︰**監視您的 Intune 主控台以找出警示和使用者或裝置問題，並確保應用程式散發會根據您的設計運作。

**技術支援人員︰**確定技術支援人員了解可能會導致支援要求的任何應用程式可用性變更。

### 請參閱
[部署 App](/intune/deploy-use/deploy-apps)

[Microsoft Intune 的應用程式部署問題疑難排解](/intune/troubleshoot/troubleshoot-app-deployment-problems-in-microsoft-intune)



<!--HONumber=Jun16_HO4-->



---
title: "判斷部署目的、目標和挑戰 | Microsoft Docs"
description: "本文有助於判斷 Microsoft Intune 僅限雲端實作的部署目的、目標和挑戰。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 12/20/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 24cf9d97-db39-4b95-a664-4aa2e33edb87
ms.reviewer: jeffbu, cgerth
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: d10906ee3fb69458738b31bb1d4252d632a9a0cf
ms.openlocfilehash: 6014527422ea3dae4d1333965ccd9e48e8216afb
ms.lasthandoff: 04/08/2017


---

# <a name="determine-intune-deployment-goals-objectives-and-challenges"></a>判斷部署目的、目標和挑戰

[!INCLUDE[note for both-portals](../includes/note-for-both-portals.md)]

想要擁有良好的部署計畫，第一步就是先識別組織的部署目的、目標，以及潛在的挑戰。 每個組織都是唯一的，因此部署目的、目標和挑戰也都不同。 現在，我們來探討每個領域的詳細資訊。

## <a name="deployment-goals"></a>部署目的

部署目的是組織要實現之 Microsoft Intune 實作的長期成就。 下列為一些組織的 Intune 部署目的範例，以及每項目的之描述和商業價值。

-   **整合 Office 365 並支援使用 Office 行動裝置應用程式**

    -   **描述：**緊密整合 Office 365 以及 Office 行動裝置應用程式和應用程式保護功能的使用。

    -   **商業價值：**使用者可以使用熟悉及偏好的應用程式，確保安全與改善的使用者體驗。

-   **啟用行動裝置上的內部公司服務存取**

    -   **描述：**此為組織的策略方向，目的是保障員工的產能，使其可從所需的位置並使用最適合的裝置進行工作。 此專案應以安全的方式啟用行動產能與公司資料的存取。

    -   **商業價值：**當員工可以靈活地從所需的位置進行工作，企業即可更具競爭力並提供充分獎勵的工作環境。

-   **提供行動裝置的資料保護**

    -   **描述：**當資料儲存在行動裝置上時，就必須防止蓄意及不小心遺失或共用的問題。

    -   **商業價值：**資料保護至關重要，可確保我們保有競爭力，得以用最細緻的服務來對待用戶端與他們的資料。

-   **降低成本**

    -   **描述：**專案應盡可能減少部署和作業成本。

    -    **商業價值：**有效率地使用資源可讓企業在其他領域進行投資、擁有更高的競爭效益，並提供更好的服務給用戶端。

## <a name="deployment-objectives"></a>部署目標

部署目標是組織為了實現其 Microsoft Intune 部署目的可採取的動作。 下列為組織部署目標的幾個範例，以及每個目標的達成方式。

-   **降低裝置管理解決方案的數量**
<br>
    -   **執行：**合併到 Microsoft Intune 這個單一行動裝置管理解決方案，以保護應用程式和裝置的公司資料。
<br></br>
-   **提供 Exchange 和 SharePoint Online 的安全存取**
<br>
    -   **執行：**實作 Exchange 和 SharePoint 的 Microsoft Intune 條件式存取。
<br></br>
-   **避免公司資料受到儲存或轉送至行動裝置上的非公司服務**
<br>
    -   **執行：**實作 Microsoft Office 與 LOB 應用程式的 Microsoft Intune 應用程式保護原則。
<br></br>
-   **提供將公司資料從裝置抹除的功能**
<br>
    -   **執行︰**使用 Microsoft Intune 來註冊和管理裝置，同時提供可在適當情況下執行遠端抹除公司資料和資源的功能。

## <a name="deployment-challenges"></a>部署挑戰

部署挑戰是組織最關切的問題，甚至可能對其部署有負面影響。 有時候，這些挑戰可能與組織在上一個專案遇到的先前問題有關 (因此組織會希望能避免這類問題)，也可能與目前部署投入的新問題有關。 下列為某家公司的 Microsoft Intune 部署挑戰以及避免方法的範例。

-   初始專案範圍未包含整備和終端使用者體驗支援。  這會導致終端使用者採用意願低落，並對解決方案的支援作業造成挑戰。
<br>
    -   **緩和措施：**納入支援訓練，並確認您的部署計畫附有終端使用者體驗的成功標準。
<br></br>
-   缺乏明確定義的目標和成功標準 (導致結果不具體)，亦缺乏發生問題時的因應模式。
<br>
    -   **緩和措施：**在專案範圍的初期定義目的和成功標準，並使用這些資料點來完善其他推出階段。 確定目標符合 SMART (具體、可測量、可實現、實際可行、及時的)，規劃在每個階段測量目標，確保首度發行專案未偏離正軌。
<br></br>
-   疏於建立、驗證及積極共用可引起組織共鳴的明確價值主張，通常會導致採用率不佳和投資回報率 (ROI) 低落。
<br>
    -   **緩和措施：**在您興奮地一頭栽進專案時，請確定您擁有明確定義的目的與目標。 將這些目標納入所有認知和訓練活動，有助於確保使用者了解組織選擇 Intune 的原因。

## <a name="next-steps"></a>後續步驟

現在，您已經識別部署目的、目標和潛在的挑戰，即可前往下一節：[識別使用案例](section-2-identify-use-case-scenarios.md)。


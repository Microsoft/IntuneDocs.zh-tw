---
title: 針對應用程式安裝問題進行疑難排解
titlesuffix: Microsoft Intune
description: 使用 [Microsoft Intune 疑難排解] 窗格，以協助您針對應用程式安裝問題進行疑難排解。
keywords: ''
author: ErikRe
ms.author: erikre
manager: dougeby
ms.date: 07/18/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: b613f364-0150-401f-b9b8-2b09470b34f4
ms.reviewer: mghadial
ms.custom: intune-azure
ms.openlocfilehash: c1c2a37103f8fedc09a70b4387aae3f472dfb636
ms.sourcegitcommit: dc8b6f802cca7895a19ec38bec283d4b3150d213
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/19/2018
ms.locfileid: "39138674"
---
# <a name="troubleshoot-app-installation-issues"></a>針對應用程式安裝問題進行疑難排解

在受 Microsoft Intune MDM 管理的裝置上，應用程式安裝有時可能會失敗。 當這些應用程式安裝失敗時，使用者可能無法輕易地了解失敗的原因，或是對問題進行疑難排解。 Microsoft Intune 提供應用程式安裝失敗詳細資料，可讓技術支援人員和 Intune 系統管理員檢視應用程式資訊，以處理使用者的協助要求。 Intune 中的 [疑難排解] 窗格會提供失敗的詳細資訊，包括使用者裝置上的受控應用程式相關詳細資料。 有關應用程式完整生命週期的詳細資訊，會在 [受控應用程式] 窗格中的每個個別裝置下提供。 您可以檢視安裝問題，例如當應用程式建立、修改、設定目標，以及傳遞至裝置時的問題。 

## <a name="to-review-app-troubleshooting-details"></a>檢視應用程式疑難排解詳細資料

Intune 會根據特定使用者裝置上安裝的應用程式，提供應用程式疑難排解的詳細資料。

1. 登入 [Azure 入口網站](https://portal.azure.com)。
2. 選擇 [All services] (所有服務) > [Intune]。 Intune 位於 [Monitoring + Management] (監視 + 管理) 區段。
3. 在 [Intune] 窗格上，選擇 [疑難排解]。
4. 按一下 [選取使用者] 來選取使用者以進行疑難排解。 [選取使用者] 窗格隨即顯示。
5. 鍵入名稱或電子郵件地址來選取使用者。 按一下窗格底部的 [選取]。 在 [疑難排解] 窗格中，會顯示使用者的疑難排解資訊。 
6. 從 [裝置] 清單中選取要進行疑難排解的裝置。
    ![[Intune 疑難排解] 窗格。](media/troubleshoot-app-install-01.png)
7. 從 [選取的裝置] 窗格中選取 [受控應用程式]。 受控應用程式清單隨即出現。
    ![由 Intune 所管理特定裝置的詳細資料。](media/troubleshoot-app-install-02.png)
8. 從 [安裝狀態] 指示失敗的清單中選取應用程式。
    ![顯示安裝失敗詳細資料的已選取應用程式。](media/troubleshoot-app-install-03.png)

    > [!Note]  
    > 可以將相同的應用程式指派給多個群組，但對於該應用程式有不同的預期動作 (用途)。 例如，如果在應用程式指派期間針對某個使用者排除了該應用程式，則應用程式已解決的用途會顯示 [已排除]。 如需詳細資訊，請參閱[如何解決應用程式用途之間的衝突](apps-deploy.md#how-conflicts-between-app-intents-are-resolved)。<br><br>
    > 目前，Intune 不會根據作業系統平台來篩選出應用程式。

應用程式安裝錯誤詳細資料會指出此問題。 您可以使用這些詳細資料，以決定解決問題所要採取的最佳動作。 如需有關針對應用程式安裝問題進行疑難排解的詳細資訊，請參閱[針對應用程式安裝問題進行疑難排解的錯誤碼](https://blogs.technet.microsoft.com/intunesupport/2018/05/15/error-codes-for-troubleshooting-app-installation-issues) \(英文\)。

> [!Note]  
> 您也可以將瀏覽器指向 [https://aka.ms/intunetroubleshooting](https://aka.ms/intunetroubleshooting)來存取 [疑難排解] 窗格。

## <a name="next-steps"></a>接下來的步驟

- 如需其他 Intune 疑難排解資訊，請參閱[使用疑難排解入口網站來協助公司的使用者](help-desk-operators.md)。 
- 深入了解 Microsoft Intune 的任何已知問題。 如需詳細資訊，請參閱 [Microsoft Intune 中的已知問題](known-issues.md)。
- 需要額外說明嗎？ 請參閱[如何取得 Microsoft Intune 支援](get-support.md)。

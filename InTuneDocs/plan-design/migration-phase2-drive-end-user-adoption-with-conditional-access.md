---
title: "使用條件式存取引導使用者採用 | Microsoft Docs"
description: "本文旨在提供如何使用條件式存取引導使用者註冊 Intune 的見解。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/24/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c2d7ce3f-fe97-4044-ad9e-25ac8fa301c9
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: ab5aa4e12d951d818c5afb4e1ac5e866b05733fb
ms.openlocfilehash: 26d11bc64802005bcce8cc1962d531af6ffe5cd5
ms.lasthandoff: 03/27/2017


---

# <a name="phase-2-drive-end-user-adoption-with-conditional-access"></a>階段 2：使用條件式存取引導使用者採用

[!INCLUDE[note for both-portals](../includes/note-for-both-portals.md)]

使用 Intune 啟用條件式存取功能 (例如封鎖來自未註冊裝置的電子郵件) 有助於推動註冊與合規性，但不是移轉成功的要件。 您的移轉採用目標和安全性需求才是決定成功的關鍵。

## <a name="migration-campaign-with-conditional-access"></a>使用條件式存取的移轉活動

以下是使用條件式存取增強移轉活動的典型方法︰

1.  設定針對所有使用者強制的條件式存取規則，但特別排除需要從舊的 MDM 提供者移轉的使用者。 您可以建立一個 Azure AD 使用者群組，其中包含所有條件式存取排除的使用者。

2.  當使用者移轉時，從條件式存取排除群組中移除他們。

3.  在移轉完成後，將所有條件式存取原則設為除非 Intune 允許否則預設為封鎖。

### <a name="advantages"></a>優點

-   為新的使用者帳戶或不受先前的解決方案管理的使用者帳戶提供存取控制。

-   為先前的解決方案使用者提供移轉寬限期。

-   將生產力的損失降至最低

### <a name="disadvantages"></a>缺點

-   先前的解決方案使用者可能會使用未受管理的裝置存取資源，直到針對這些使用者啟用條件式存取為止。

> [!TIP] 
> 這是眾多方法之一。 您可以選擇較簡單的程序，以延遲所有條件式存取直到使用者已收到每個階段的註冊指示後為止，或是選擇較嚴格的程序，從一開始就強制條件式存取，而且要求所有存取的完整合規性。

-   深入了解[使用 Microsoft Intune 限制電子郵件、Office 365 和其他服務的存取](https://docs.microsoft.com/intune-azure/conditional-access/what-is-conditional-access)。

## <a name="task-list-for-conditional-access"></a>條件式存取的工作清單

### <a name="task-1-get-ready-for-intune-conditional-access"></a>工作 1︰準備好 Intune 條件式存取

-   了解[如何設定條件式存取](https://docs.microsoft.com/intune/deploy-use/restrict-access-to-email-and-o365-services-with-microsoft-intune)。

### <a name="task-2-setup-intune-conditional-access"></a>工作 2︰安裝 Intune 條件式存取

選擇下列其中一個條件式存取原則類型以深入了解︰

-   [Exchange Online 和新 Exchange Online Dedicated](https://docs.microsoft.com/intune/deploy-use/restrict-access-to-exchange-online-with-microsoft-intune)

-   [Exchange 內部部署和舊版 Exchange Online Dedicated](https://docs.microsoft.com/intune/deploy-use/restrict-access-to-exchange-onpremises-with-microsoft-intune)

-   [SharePoint Online](https://docs.microsoft.com/intune/deploy-use/restrict-access-to-sharepoint-online-with-microsoft-intune)

-   [商務用 Skype Online](https://docs.microsoft.com/intune/deploy-use/restrict-access-to-skype-for-business-online-with-microsoft-intune)

-   [Dynamics CRM Online](https://docs.microsoft.com/intune/deploy-use/restrict-access-to-dynamics-crm-online-with-microsoft-intune)

-   [範例電子郵件存取案例](https://docs.microsoft.com/intune/deploy-use/restrict-email-access-example-scenarios)

## <a name="next-steps"></a>後續步驟

[階段 2：典型的移轉週期](https://docs.microsoft.com/intune/plan-design/migration-phase2-typical-migration-cycle)


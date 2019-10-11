---
title: 使用 Intune 設定以應用程式為基礎的條件式存取原則
titleSuffix: Microsoft Intune
description: 了解如何使用 Intune 建立以應用程式為基礎的條件式存取原則。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d1693515-de18-4553-91ef-801976cd3ec7
ms.reviewer: chrisgre
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: d9cbe57d0cf69f036cd36d2c1b95c48b198645e7
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2019
ms.locfileid: "71723082"
---
# <a name="set-up-app-based-conditional-access-policies-with-intune"></a>使用 Intune 設定以應用程式為基礎的條件式存取原則

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

為屬於已核准應用程式清單之一部分的應用程式，設定以應用程式為基礎的條件式存取原則。 已核准應用程式清單包含 Microsoft 已測試的應用程式。

> [!IMPORTANT]
> 本文將逐步解說新增以應用程式為基礎之條件式存取原則的步驟。 從核准的應用程式清單中新增應用程式 (例如 SharePoint Online、Microsoft Teams 和 Microsoft Exchange Online) 時，您可以使用相同的步驟。

## <a name="create-app-based-conditional-access-policies"></a>建立以應用程式為基礎的條件式存取原則
條件式存取是一項 Azure Active Directory (Azure AD) 技術。 從 *Intune* 存取的條件式存取節點，與從 *Azure AD* 存取的節點相同。 這表示您不需要為了設定原則在 Intune 與 Azure AD 之間切換。

> [!IMPORTANT]
> 您需要有 Azure AD Premium 授權，才能從 Intune 入口網站建立條件式存取原則。

### <a name="to-create-an-app-based-conditional-access-policy"></a>建立以應用程式為基礎的條件式存取原則

> [!IMPORTANT]
> 您需要先將 [Intune 應用程式防護原則](../apps/app-protection-policies.md)套用至應用程式，才能使用以應用程式為基礎的條件式存取原則。

1. 在 [Intune 儀表板]  中，選取 [條件式存取]  。

2. 在 [原則]  窗格中，選擇 [新增原則]  來建立新的以應用程式為基礎的條件式存取原則。

4. 在您輸入原則名稱並在 [指派]  區段中設定可用的設定之後，接著選擇 [存取控制]  區段下的 [授與]  。

5. 依序選擇 [需要經過核准的用戶端應用程式]  、[選取]  和 [建立]  儲存新的原則。

## <a name="next-steps"></a>後續步驟
[封鎖沒有新式驗證的應用程式](app-modern-authentication-block.md)

## <a name="see-also"></a>請參閱

[使用應用程式保護原則保護應用程式資料](../apps/app-protection-policies.md)
[Azure Active Directory 中的條件式存取](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access)

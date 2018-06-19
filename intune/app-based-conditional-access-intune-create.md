---
title: 使用 Intune 設定以應用程式為基礎的條件式存取原則
description: 了解如何使用 Intune 建立以應用程式為基礎的條件式存取原則。
keywords: ''
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 05/17/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: d1693515-de18-4553-91ef-801976cd3ec7
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: c505e881fe06d6f4da217533d0507731ac22a29f
ms.sourcegitcommit: 698bd1488be3a269bb88c077eb8d99df6e552a9a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2018
ms.locfileid: "34285019"
---
# <a name="set-up-app-based-conditional-access-policies-with-intune"></a>使用 Intune 設定以應用程式為基礎的條件式存取原則

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

本文描述如何為屬於已核准應用程式清單一部分的應用程式，設定以應用程式為基礎的條件式存取原則。 已核准應用程式清單包含 Microsoft 已測試的應用程式。

> [!IMPORTANT]
> 本文逐步解說新增應用程式為基礎的條件式存取原則的步驟。 請注意，從核准的應用程式清單中新增應用程式，例如 SharePoint Online、Microsoft Teams 和 Microsoft Exchange Online 時，您可以使用相同的步驟。

## <a name="create-app-based-conditional-access-policies-in-azure-ad-workload"></a>在 Azure AD 工作負載中建立以應用程式為基礎的條件式存取原則

IT 系統管理員可以從 Azure AD 工作負載建立以應用程式為基礎的條件式存取原則。 這提供方便性，因此您不需要切換 Azure 與 Intune 工作負載。

> [!IMPORTANT]
> 您必須要有 Azure AD Premium 授權，才能從 Intune Azure 入口網站建立 Azure AD 條件式存取原則。

### <a name="to-create-an-app-based-conditional-access-policy"></a>建立以應用程式為基礎的條件式存取原則

> [!IMPORTANT]
> 您需要先將 [Intune 應用程式保護原則](app-protection-policies.md)套用至應用程式，再使用以應用程式為基礎的條件式存取原則。

1. 在 [Intune 儀表板] 中，選擇 [條件式存取]。

2. 在 [原則] 窗格中，選擇 [新增原則] 來建立以應用程式為基礎的新條件式存取原則。

4. 在您輸入原則名稱並在 [指派] 區段中設定可用的設定之後，接著選擇 [存取控制] 區段下的 [授與]。

5. 依序選擇 [需要經過核准的用戶端應用程式]、[選取] 和 [建立] 儲存新的原則。

## <a name="next-steps"></a>接下來的步驟
[封鎖沒有新式驗證的應用程式](app-modern-authentication-block.md)

### <a name="see-also"></a>另請參閱

[使用應用程式保護原則保護應用程式資料](app-protection-policies.md)
[Azure Active Directory 中的條件式存取](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access)

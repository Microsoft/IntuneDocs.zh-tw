---
title: 使用 Intune 設定以應用程式為基礎的條件式存取原則
titleSuffix: Microsoft Intune
description: 了解如何使用 Intune 建立以應用程式為基礎的條件式存取原則。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/06/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d1693515-de18-4553-91ef-801976cd3ec7
ms.reviewer: elocholi
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 465f8b0001e5e2a049a3ffe12469bdb5057854ec
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "73712833"
---
# <a name="set-up-app-based-conditional-access-policies-with-intune"></a>使用 Intune 設定以應用程式為基礎的條件式存取原則

為屬於已核准應用程式清單之一部分的應用程式，設定以應用程式為基礎的條件式存取原則。 已核准應用程式清單包含 Microsoft 已測試的應用程式。

需要先將 [Intune 應用程式防護原則](../apps/app-protection-policies.md)套用至應用程式，才能使用以應用程式為基礎的條件式存取原則。

> [!IMPORTANT]
> 本文將逐步解說新增以應用程式為基礎之條件式存取原則的步驟。 從核准的應用程式清單中新增應用程式 (例如 SharePoint Online、Microsoft Teams 和 Microsoft Exchange Online) 時，您可以使用相同的步驟。

## <a name="create-app-based-conditional-access-policies"></a>建立以應用程式為基礎的條件式存取原則

條件式存取是一項 Azure Active Directory (Azure AD) 技術。 從 *Intune* 存取的條件式存取節點，與從 *Azure AD* 存取的節點相同。 因為其是相同節點，所以不需要為了設定原則而在 Intune 與 Azure AD 之間切換。

必須擁有 Azure AD Premium 授權，才能從 Microsoft Endpoint Manager 系統管理中心建立條件式存取原則。

### <a name="to-create-an-app-based-conditional-access-policy"></a>建立以應用程式為基礎的條件式存取原則

1. 登入 [Microsoft Endpoint Manager 系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)

2. 選取 [端點安全性]   > [條件式存取]   > [新增原則]  。

3. 輸入原則 [名稱]  ，然後在 [指派]  底下選取 [使用者和群組]  。 使用 [包含] 或 [排除] 選項來針對原則新增群組，並選取 [完成]  。

4. 選取 [雲端應用程式或動作]  ，然後選擇要保護哪些應用程式。 例如，選擇 [選取應用程式]  ，然後選取 [Office 365 SharePoint Online]  和 [Office 365 Exchange Online]  。

   按一下 [完成]  以儲存您的變更。

5. 選取 [條件]   > [用戶端應用程式]  來將原則套用至應用程式和瀏覽器。 例如，選取 [是]  ，然後啟用 [瀏覽器]  和 [行動應用程式及桌面用戶端]  。

   按一下 [完成]  以儲存您的變更。

6. 在 [存取控制]  底下，選取 [授與]  以根據裝置合規性套用條件式存取。 例如，選取 [授與存取權]   > [裝置需要標記為合規]  。

   選擇 [選取]  以儲存您的變更。

7. 針對 [啟用原則]  ，選取 [開啟]  ，然後選取 [建立]  以儲存變更。





## <a name="next-steps"></a>後續步驟
[封鎖沒有新式驗證的應用程式](app-modern-authentication-block.md)

## <a name="see-also"></a>請參閱

[使用應用程式保護原則保護應用程式資料](../apps/app-protection-policies.md)
[Azure Active Directory 中的條件式存取](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access)

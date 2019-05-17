---
title: 在 Intune 上封鎖沒有新式驗證的應用程式
titleSuffix: Microsoft Intune
description: 了解使用 Microsoft Intune 的應用程式和新式驗證 (ADAL)。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 04/03/2019
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.topic: conceptual
ms.technology: ''
ms.assetid: 73db3070-d033-40fb-a8f1-58b9d198021e
ms.reviewer: chrisgre
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9ca96f36f8813d80c7ebb07bfb3bd65f8aa0b392
ms.sourcegitcommit: 71314481e644025c005019b478b4cbeaf2390ea9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/05/2019
ms.locfileid: "59569099"
---
# <a name="block-apps-that-dont-use-modern-authentication-adal"></a>封鎖未使用新式驗證 (ADAL) 的應用程式

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

使用應用程式保護原則的應用程式型條件式存取依賴使用[新式驗證](https://support.office.com/article/Using-Office-365-modern-authentication-with-Office-clients-776c0036-66fd-41cb-8928-5495c0f9168a) (即 OAuth2 實作) 的應用程式。 大部分的最新 Office 行動裝置與傳統型應用程式都使用新式驗證。 不過，還有使用其他驗證方法 (例如基本驗證與表單型驗證) 的協力廠商應用程式與舊版 Office 應用程式。

## <a name="block-access-to-apps"></a>封鎖對應用程式的存取

若要封鎖對未使用新式驗證之應用程式的存取，請使用 Intune 應用程式保護原則來實作條件存取。 如需詳細資訊，請參閱[搭配 Intune 使用應用程式型條件式存取](app-based-conditional-access-intune.md)。

## <a name="additional-information"></a>其他資訊

如需有關 Azure AD 條件式存取的詳細資訊，請參閱下列主題：
- [什麼是 Azure Active Directory 的條件式存取？](https://docs.microsoft.com/azure/active-directory/conditional-access/overview)
- [以應用程式為基礎的條件式存取如何運作](app-based-conditional-access-intune.md#how-app-based-conditional-access-works)
- [為 Azure Active Directory 條件式存取設定 SharePoint Online 與 Exchange Online](https://docs.microsoft.com/azure/active-directory/conditional-access/conditional-access-for-exo-and-spo)

## <a name="next-steps"></a>後續步驟

- [搭配 Intune 使用以應用程式為基礎的條件式存取](app-based-conditional-access-intune.md)

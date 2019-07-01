---
title: 使用條件式存取引導終端使用者採用
titleSuffix: Microsoft Intune
description: 了解如何在 Microsoft Intune 中使用條件式存取來引導註冊。
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: c2d7ce3f-fe97-4044-ad9e-25ac8fa301c9
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2bedaf279d65ee1ed7f8dda4e8d866fb848bade7
ms.sourcegitcommit: 4b83697de8add3b90675c576202ef2ecb49d80b2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/13/2019
ms.locfileid: "67044581"
---
# <a name="drive-end-user-adoption-with-conditional-access-in-microsoft-intune"></a>在 Microsoft Intune 中使用條件式存取引導終端使用者採用

使用 Intune 啟用條件式存取功能 (例如封鎖來自未註冊裝置的電子郵件) 有助於引導註冊與合規性，但不是移轉成功的要件。 您的移轉採用目標和安全性需求才是決定成功的關鍵。

## <a name="migration-campaign-with-conditional-access"></a>使用條件式存取的移轉活動

以下是使用條件式存取來增強移轉活動的典型方法：

1.  設定要針對所有使用者強制執行的條件式存取規則，但特別排除需要從舊的 MDM 提供者移轉的使用者。 您可以建立一個 Azure AD 使用者群組，其中包含所有條件式存取排除的使用者。

2.  當使用者移轉時，從條件式存取排除群組中移除他們。

3.  移轉完成之後，將所有條件式存取原則設定為除非 Intune 允許存取否則預設為封鎖。

### <a name="advantages"></a>優點

-   為新的使用者帳戶或不受先前的解決方案管理的使用者帳戶提供存取控制。

-   為先前的解決方案使用者提供移轉寬限期。

-   將生產力的損失降至最低

### <a name="disadvantages"></a>缺點

-   先前解決方案的使用者可能會使用非受控裝置來存取資源，直到針對那些使用者啟用條件式存取為止。


這是眾多方法之一。 您可以選擇較簡單的流程來延遲所有條件式存取，直到收到每個階段的註冊指示為止，或選擇較嚴格的流程，一開始就強制執行條件式存取，並要求所有存取的完整合規性。

-   深入了解[使用 Microsoft Intune 限制電子郵件、Office 365 和其他服務的存取](conditional-access.md)。

## <a name="task-list-for-conditional-access"></a>條件式存取的工作清單

### <a name="task-1-decide-how-you-are-going-to-implement-conditional-access"></a>工作 1：決定實作條件式存取的方式

[使用條件式存取的常見方式](conditional-access-intune-common-ways-use.md)。

### <a name="task-2-set-up-intune-conditional-access"></a>工作 2：設定 Intune 條件式存取

選擇下列其中一個選項：

-   [在 Azure Active Directory 中設定條件式存取](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)

-   [使用 Intune 安裝內部部署 Exchange Connector](exchange-connector-install.md)

-   [為 Exchange Online 設定以應用程式為基礎的條件式存取原則](app-based-conditional-access-intune-create.md)

-   [為 SharePoint Online 設定以應用程式為基礎的條件式存取原則](app-based-conditional-access-intune-create.md)

-   [封鎖未使用新式驗證 (ADAL) 的應用程式](app-modern-authentication-block.md)

## <a name="next-steps"></a>後續步驟

了解[典型移轉週期](migration-guide-cycle.md)。

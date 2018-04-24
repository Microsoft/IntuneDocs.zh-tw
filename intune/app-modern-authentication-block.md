---
title: 在 Intune 上封鎖沒有新式驗證的應用程式
titleSuffix: Microsoft Intune
description: 了解封鎖未使用新式驗證 (ADAL) 的應用程式。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/02/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 73db3070-d033-40fb-a8f1-58b9d198021e
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 796e64d40ce111edccf6cd6a6e97f1cadf2443e5
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="block-apps-that-do-not-use-modern-authentication-adal"></a>封鎖未使用新式驗證 (ADAL) 的應用程式

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

使用應用程式保護原則之以應用程式為基礎的條件式存取依賴使用[新式驗證](https://support.office.com/article/Using-Office-365-modern-authentication-with-Office-clients-776c0036-66fd-41cb-8928-5495c0f9168a) (即 OAuth2 實作) 的應用程式。 最新的 Office Mobile 和桌面應用程式使用新式驗證，不過還有使用其他驗證方法 (例如基本驗證和表單型驗證) 的協力廠商應用程式和舊版 Office 應用程式。

若要封鎖這些應用程式的存取，建議執行下列動作：

* 設定 ADFS 宣告規則來封鎖非新式驗證通訊協定。 案例 3 提供詳細指示 - [除使用瀏覽器架構的應用程式外，封鎖所有對 O365 的存取](https://technet.microsoft.com/library/dn592182.aspx)。
* 針對 **SharePoint Online**，使用 PowerShell 命令 [Set-SPOTenant](https://technet.microsoft.com/library/fp161390.aspx) 來停用 SharePoint Online 服務中的非新式驗證，以便將舊式驗證通訊協定屬性設為 False：

```
 Set-SPOTenant -LegacyAuthProtocolsEnabled $false
```


>[!IMPORTANT]
>以應用程式為基礎的 CA 不能搭配 Azure Active Directory (Azure AD) 憑證式驗證使用。 您一次只能設定其中一個項目。

### <a name="see-also"></a>另請參閱
[搭配 Intune 使用以應用程式為基礎的條件式存取](app-based-conditional-access-intune.md)

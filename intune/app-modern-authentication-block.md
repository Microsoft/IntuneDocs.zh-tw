---
title: "在 Intune 上封鎖沒有新式驗證的應用程式"
description: 
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 05/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 73db3070-d033-40fb-a8f1-58b9d198021e
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 3fbdb9d6e7e1869aba12b3639b8e887401491a79
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2017
---
# <a name="block-apps-that-do-not-use-modern-authentication-adal"></a>封鎖未使用新式驗證 (ADAL) 的應用程式

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

使用應用程式保護原則之以應用程式為基礎的條件式存取依賴使用[新式驗證](https://support.office.com/article/Using-Office-365-modern-authentication-with-Office-clients-776c0036-66fd-41cb-8928-5495c0f9168a) (即 OAuth2 實作) 的應用程式。 最新的 Office Mobile 和桌面應用程式使用新式驗證，不過還有使用其他驗證方法 (例如基本驗證和表單型驗證) 的協力廠商應用程式和舊版 Office 應用程式。

若要封鎖這些應用程式的存取，建議執行下列動作：

* 設定 ADFS 宣告規則來封鎖非新式驗證通訊協定。 案例 3 提供詳細指示 - [除使用瀏覽器架構的應用程式外，封鎖所有對 O365 的存取](https://technet.microsoft.com/library/dn592182.aspx)。
* 針對 **SharePoint Online**，使用 PowerShell 命令 [Set-SPOTenant](https://technet.microsoft.com/library/fp161390.aspx) 來停用 SharePoint Online 服務中的非新式驗證，以便將舊式驗證通訊協定屬性設為 False：

```
 Set-SPOTenant -LegacyAuthProtocolsEnabled $false

```


>[!IMPORTANT]
>以應用程式為基礎的 CA 不能搭配 Azure Active Directory (Azure AD) 憑證式驗證使用。 您一次只能設定其中一個項目。

### <a name="see-also"></a>請參閱
[搭配 Intune 使用以應用程式為基礎的條件式存取](app-based-conditional-access-intune.md)

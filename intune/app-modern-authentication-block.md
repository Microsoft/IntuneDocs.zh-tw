---
title: 在 Intune 上封鎖沒有新式驗證的應用程式
titleSuffix: Microsoft Intune
description: 了解封鎖未使用新式驗證 (ADAL) 的應用程式。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/19/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 73db3070-d033-40fb-a8f1-58b9d198021e
ms.reviewer: chrisgre
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 0b74559eb0914d87daabaaad52902547ae7c08ac
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2018
ms.locfileid: "52182035"
---
# <a name="block-apps-that-do-not-use-modern-authentication-adal"></a>封鎖未使用新式驗證 (ADAL) 的應用程式

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

使用應用程式保護原則的應用程式型條件式存取依賴使用[新式驗證](https://support.office.com/article/Using-Office-365-modern-authentication-with-Office-clients-776c0036-66fd-41cb-8928-5495c0f9168a) (即 OAuth2 實作) 的應用程式。 大部分的最新 Office 行動裝置與傳統型應用程式都使用新式驗證。 不過，還有使用其他驗證方法 (例如基本驗證與表單型驗證) 的協力廠商應用程式與舊版 Office 應用程式。

若要封鎖對這些應用程式的存取，建議使用下列方法：

* 設定 ADFS 宣告規則來封鎖非新式驗證通訊協定。 案例 3 提供詳細指示 - [除使用瀏覽器架構的應用程式外，封鎖所有對 O365 的存取](https://technet.microsoft.com/library/dn592182.aspx)。
* 針對 **Exchange 與 SharePoint Online**，請使用 Azure Active Directory 條件式存取並為 SharePoint Online 使用 PowerShell Cmdlet Set-SPOTenant。 如需詳細指示，請參閱[為 Azure Active Directory 條件式存取設定 SharePoint Online 與 Exchange Online](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-no-modern-authentication#legacy-authentication-protocols)。


>[!IMPORTANT]
>以應用程式為基礎的 CA 不能搭配 Azure Active Directory (Azure AD) 憑證式驗證使用。 您一次只能設定其中一個項目。

### <a name="see-also"></a>另請參閱
[搭配 Intune 使用以應用程式為基礎的條件式存取](app-based-conditional-access-intune.md)

---
title: "封鎖沒有新式驗證的應用程式 | Microsoft Docs"
description: 
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 10/15/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 098b652c-01e0-45d1-a731-620b0d3dc7c1
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: e55cf608c2e5157feeb40ba20d3988b5b35064db
ms.openlocfilehash: b2d708e35a7993ff7c5e3db170b1025794b33baf
ms.lasthandoff: 02/25/2017


---

# <a name="block-apps-that-do-not-use-modern-authentication-adal"></a>封鎖未使用新式驗證 (ADAL) 的應用程式

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

使用應用程式保護原則之以應用程式為基礎的條件式存取依賴使用[新式驗證](https://support.office.com/en-US/article/Using-Office-365-modern-authentication-with-Office-clients-776c0036-66fd-41cb-8928-5495c0f9168a) (即 OAuth2 實作) 的應用程式。 最新的 Office Mobile 和桌面應用程式使用新式驗證，不過還有使用其他驗證方法 (例如基本驗證和表單型驗證) 的協力廠商應用程式和舊版 Office 應用程式。

若要封鎖這些應用程式的存取，建議執行下列動作：

* 設定 ADFS 宣告規則來封鎖非新式驗證通訊協定。 案例 3 提供詳細指示 - [除使用瀏覽器架構的應用程式外，封鎖所有對 O365 的存取](https://technet.microsoft.com/library/dn592182.aspx)。

>[!IMPORTANT]
>以應用程式為基礎的 CA 不能搭配 Azure Active Directory (Azure AD) 憑證式驗證使用。 您一次只能設定其中一個項目。

### <a name="see-also"></a>請參閱
[只允許 Intune 支援的應用程式存取 O365 服務](allow-policy-managed-apps-access-to-o365.md)


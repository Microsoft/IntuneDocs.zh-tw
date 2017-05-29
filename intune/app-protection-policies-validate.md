---
title: "驗證應用程式保護原則"
titleSuffix: Intune Azure preview
description: "Intune Azure 預覽版︰本主題說明如何測試及驗證您的應用程式保護原則設定正確且正常運作。"
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angerobe
ms.date: 01/23/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 15f8a838-0b69-412b-a42e-c6edb61f0cae
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 26e191965eff482cf97b920e028cdf60d1881d32
ms.contentlocale: zh-tw
ms.lasthandoff: 05/23/2017


---

# <a name="how-to-validate-your-app-protection-policy-setup"></a>如何驗證您的應用程式保護原則設定

[!INCLUDE[azure_preview](./includes/azure_preview.md)]


本主題提供有關如何在設定應用程式保護原則之後檢查問題的資訊。 本指南適用於 Azure 入口網站**預覽版**的應用程式保護原則。

### <a name="checking-for-symptoms"></a>檢查有無徵兆
因為 MAM 是資料保護工具，所以無法讓使用者回報問題。 當 MAM 設定有問題時，因為缺少了應用程式保護，所以使用者存取將不會受到限制，而且也不會察覺到發生問題。 因此建議您先對一小群可以協助仔細測試這些應用程式保護限制的使用者來試驗您的應用程式保護原則，從而驗證您的應用程式保護設定。


### <a name="what-to-check"></a>要檢查的項目

若測試顯示您的應用程式保護原則行為不如預期，建議您檢查下列項目︰

- 這些使用者具備應用程式保護的授權嗎？
- 使用者具備 O365 授權嗎？
- 每個使用者之應用程式保護應用程式的狀態。 可能的應用程式狀態為 [已簽入] 和 [未簽入 (Not checked in)]。

#### <a name="user-app-protection-status"></a>使用者應用程式保護的狀態
1. 在 Azure 入口網站中選擇 [管理應用程式]  >  [監視]  >   [應用程式保護使用者狀態]  >  [使用者]。

2. 從清單中選擇使用者，或是搜尋並選擇使用者，然後選擇 [選取使用者]。 在 [應用程式報告] 資料行頂端會顯示使用者是否具備應用程式保護的授權。 您會在下方看到使用者是否具有 O365 授權，以及使用者所有裝置的應用程式狀態。



### <a name="what-to-do"></a>解決方式
以下是要根據使用者狀態所採取的動作︰

- 若使用者未獲應用程式保護授權，請指派 Intune 授權給使用者。
- 如果使用者不具有 O365 授權，替使用者取得授權。
- 若使用者的應用程式列為 [未簽入]，請確定您為該應用程式設定的應用程式保護原則正確。
- 請確認這些條件會套用到所有需要套用應用程式保原則的使用者。

### <a name="see-also"></a>請參閱

[什麼是 Intune 應用程式保護原則？](app-protection-policies.md)


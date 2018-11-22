---
title: 驗證您的應用程式保護原則設定
titleSuffix: Microsoft Intune
description: 了解如何測試您的應用程式保護原則已正確設定和運作。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/13/2018
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 15f8a838-0b69-412b-a42e-c6edb61f0cae
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 5e0a207d3e845e3983dfe6ce3abbb70fcbbe65cf
ms.sourcegitcommit: 4d5e811d451aeb6307e0f64818e182e471ae1ed4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/13/2018
ms.locfileid: "51618968"
---
# <a name="how-to-validate-your-app-protection-policy-setup"></a>如何驗證您的應用程式保護原則設定

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

驗證應用程式保護原則已正確設定和運作。 本指南適用於 Azure 入口網站的應用程式保護原則。

### <a name="checking-for-symptoms"></a>檢查是否有徵兆
因為 MAM 是資料保護工具，所以無法讓使用者回報問題。 如果應用程式保護設定發生問題，則因為缺少應用程式保護，所以使用者存取將不會受到限制，而且不會知道發生問題。 因此，建議您先對一小群可以協助仔細測試這些應用程式保護限制的使用者試驗您的應用程式保護原則，以驗證您的應用程式保護設定。


### <a name="what-to-check"></a>要檢查的項目

如果測試顯示您的應用程式保護原則行為不如預期，請檢查這些項目︰

- 這些使用者具備應用程式保護的授權嗎？
- 使用者具備 O365 授權嗎？
- 每個使用者之應用程式保護應用程式的狀態。 可能的應用程式狀態為 [已簽入] 和 [未簽入]。

#### <a name="user-app-protection-status"></a>使用者應用程式保護的狀態
1. 登入 [Azure 入口網站](https://portal.azure.com)。
2. 選取 [所有服務] > [Intune]。 Intune 位於 [Monitoring + Management] (監視 + 管理) 區段。
3. 選取 [用戶端應用程式] > [監視器] >  [應用程式保護狀態]，然後選取 [指派的使用者] 圖格。 
4. 在 [應用程式報告] 頁面上，選取 [選取使用者] 以顯示使用者與群組清單。 
5. 從該清單搜尋並選取使用者，然後選擇 [選取使用者]。 在 [應用程式報告] 窗格頂端，您可以看到使用者是否具備應用程式保護的授權。 您也可以看到使用者是否有 O365 授權，以及使用者所有裝置的應用程式狀態。



### <a name="what-to-do"></a>解決方式
以下是要根據使用者狀態所採取的動作︰

- 若使用者未獲應用程式保護授權，請指派 Intune 授權給使用者。
- 如果使用者不具有 O365 授權，為使用者取得授權。
- 如果使用者的應用程式列為 [未簽入]，請確定您為該應用程式設定的應用程式保護原則正確。
- 請確認這些條件會套用到所有需要套用應用程式保原則的使用者。

### <a name="see-also"></a>另請參閱

[什麼是 Intune 應用程式保護原則？](app-protection-policies.md)

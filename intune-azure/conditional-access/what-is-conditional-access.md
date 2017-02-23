---
title: "什麼是條件式存取？ | Intune Azure 預覽版 | Microsoft Docs"
description: "Intune Azure 預覽版︰了解如何在 Microsoft Intune Azure 預覽版中定義使用者與裝置在存取公司資源之前必須符合的條件。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 12/07/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a1973f38-ea55-43eb-a151-505fb34a8afb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 41931f64db969c82f79e007c4be9e68b7caf4ce9
ms.openlocfilehash: 20696fb2dc0126aa224e779738cedb4f95f666e8


---

# <a name="what-is-conditional-access"></a>什麼是條件式存取？


[!INCLUDE[azure_preview](../includes/azure_preview.md)]


本主題會先說明 Enterprise Mobility + Security 的條件式存取，再接著說明 Intune 的條件式存取功能。

Enterprise Mobility + Security (EMS) 的條件式存取運用了 Azure Active Directory Premium 與 Microsoft Intune 的能力讓您一方面能夠擁有保障公司資料安全所需的控制，一方面又能讓您的員工可以從任何裝置達成最佳工作結果。

您可以使用條件式存取定義條件，依據位置、裝置與使用者狀態，以及應用程式的敏感程度來限制對公司資料的存取。

從裝置來看，Intune 與 Azure Active Directory 整合運作可以確保只有受管理及符合規範的裝置可以存取電子郵件及 Office 365 服務。 例如，您可以在 Azure Active Directory 中設定原則，只讓加入網域的電腦或已在行動裝置管理應用程式 (例如 Intune) 中註冊的行動裝置存取 Office 365 服務。 您可以使用 Intune 設定裝置合規性設定檔，以評估裝置的合規性狀態。 合規性狀態會回報給 Azure Active Directory，在使用者嘗試存取您的公司資源時，於 Azure Active Directory 中施行原則時使用。 如需深入了解在 Intune 中裝置的合規性，請參閱[什麼是裝置合規性？](/intune-azure/set-device-compliance/what-is-device-compliance)

雲端應用程式 (例如 Exchange Online) 的條件式存取可以透過 Azure Active Directory 設定。 如需詳細資訊，請參閱這篇[文章](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-conditional-access-azure-portal)。

## <a name="on-premises-conditional-access-in-intune"></a>Intune 中內部部署的條件式存取

在 Intune 中，條件式存取可依據裝置管理與註冊來允許或禁止對 **Exchange 內部部署**的存取。

裝置合規性設定檔設定可用於評估裝置的合規性。 條件式存取會利用這項評估來允許或禁止對 Exchange 內部部署的存取。 當條件式存取與裝置合規性設定檔一起使用時，只有符合規範的裝置可以存取 Exchange 內部部署。 您可以更進一步設定條件式存取，例如允許或禁丄特定平台，或是立即封鎖不是由 Intune 管理的裝置。

裝置合規性設定檔與條件式存取會一併指派給使用者。 所有使用者用於存取 Exchange 內部部署的裝置都必須經過合規性檢查。 請注意，裝置使用者必須具備合規性設定檔指派，其裝置才能接受合規性評估。 若使用者未獲部署合規性政策，便會將其裝視為符合規範，而且會對其套用沒有存取權限的限制。

當裝置不符合條件設定時，將會引導使用者執行註冊裝置及修正裝置不符合規範問題的程序。

## <a name="next-steps"></a>後續步驟

[如何建立 Exchange 內部部署的條件存取原則](create-conditional-access-policy-for-exchange-on-premises.md)

[如何在 Azure Active Directory 中設定條件式存取](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-conditional-access-azure-portal)



<!--HONumber=Feb17_HO1-->



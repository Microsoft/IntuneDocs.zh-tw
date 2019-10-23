---
title: 需要 Intune 裝置註冊的多重要素驗證
titleSuffix: Microsoft Intune
description: 如何在 Azure AD 中針對 Intune 裝置註冊要求多重要素驗證。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 94280c73-c05c-4e72-b0dd-a7cb997782f9
ROBOTS: ''
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 50dbbb19cca9b5c46f0ba8b9d4e16c499534b536
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72503122"
---
# <a name="require-multi-factor-authentication-for-intune-device-enrollments"></a>需要 Intune 裝置註冊的多重要素驗證

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Intune 可以使用 Azure Active Directory (AD) 多重要素驗證 (MFA) 進行裝置註冊，以協助您保護公司資源的安全。

MFA 的運作方式是要求使用下列任兩個或更多個驗證方法：

- 您知道的某種資訊 (通常是密碼或 PIN)。
- 您擁有的某種東西 (不容易複製的信任裝置，例如手機)。
- 您是什麼 (生物特徵辨識，例如指紋)。

iOS、Android、Windows 8.1 或更新版本、Windows Phone 8.1 或者 Windows 10 Mobile 或更新版本的裝置支援 MFA。

當您啟用 MFA 時，終端使用者必須提供兩種形式的認證來註冊裝置。

## <a name="configure-intune-to-require-multi-factor-authentication-at-device-enrollment"></a>設定 Intune 以在裝置註冊時要求多重要素驗證

若要在註冊裝置時要求 MFA，請遵循下列步驟︰

>[!Important]
>您必須將 Azure Active Directory Premium P1 (或以上) 指派給使用者以實施此原則。

>[!Important]
>請不要針對 Microsoft Intune 註冊設定 [以裝置為準的存取規則]  。

1. 使用您的認證登入您的 [Microsoft Azure 入口網站](https://portal.azure.com)。
2. 在入口網站中，移至 [Intune]  ，然後選擇 [條件式存取]  。 從 *Intune* 存取的條件式存取節點，與從 *Azure AD* 存取的節點相同。
4. 選擇 [新增原則]  。
5. 在 [新增]  原則中，鍵入原則的描述性名稱。
6. 在 [指派]  區段中，選擇 [使用者和群組]  。 
7. 在 [使用者和群組]  中，選擇 [選取使用者或群組]  ，並核取 [使用者和群組]  。 接著，選取將接收這個政策的使用者和/或群組，然後選擇 [完成]  。
8. 在 [指派]  區段中，選擇 [雲端應用程式]  。
9. 在 [雲端應用程式]  的 [包含]  索引標籤上，選擇 [選取應用程式]  ，並選擇 [選取]   > [Microsoft Intune 註冊]  ，然後選擇 [完成]  。 藉由選擇 [Microsoft Intune 註冊]  ，條件式存取 MFA 只會套用至裝置的註冊 (一次性 MFA 提示)。
10. 在 [指派]  區段的 [條件]  中，您不需要設定 MFA 的任何設定。
11. 在 [存取控制]  區段中，選擇 [授與]  。
12. 在 [授與]  中，選擇 [授與存取權]  ，然後選取 [需要多重要素驗證]  。 請不要選取 [裝置需要標記為合規]  ，因為在註冊之前無法評估裝置的合規性。 然後選擇 [選取]  。
13. 在 [新增原則]  中，選擇 [啟用原則]   > [開啟]  ，然後選擇 [建立]  。



## <a name="next-steps"></a>後續步驟

終端使用者在註冊其裝置時，現在必須使用第兩種形式的識別進行驗證，例如 PIN、電話或生物特徵辨識。

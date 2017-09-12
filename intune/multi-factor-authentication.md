---
title: "Intune 裝置註冊的多重要素驗證"
titlesuffix: Azure portal
description: "如何在 Azure AD 中針對裝置註冊要求多重要素驗證。"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angerobe
ms.date: 08/10/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 94280c73-c05c-4e72-b0dd-a7cb997782f9
ROBOTS: 
ms.custom: intune-azure
ms.openlocfilehash: 0355c6ca11d7b1221ad7aa833874eba91eea0600
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/09/2017
---
# <a name="multi-factor-authentication-for-intune-device-enrollments"></a>Intune 裝置的註冊的多重要素驗證 | Microsoft Docs

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

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
>請不要針對 Microsoft Intune 註冊設定 [以裝置為準的存取規則]。

1. 使用您的認證登入您的 [Microsoft Azure 入口網站](https://portal.azure.com)。
2. 在入口網站中，選擇 [Azure Active Directory]。
2. 在 [Azure Active Directory] 中，選擇 [管理] > [企業應用程式]。
3. 在 [企業應用程式] 中，選擇 [管理] > [所有應用程式]。 您會看到一份您所管理的所有 Azure 應用程式清單。
3. 從清單中，選擇 [Microsoft Intune 註冊]。
4. 在 [Microsoft Intune 註冊] 中，選擇 [安全性] > [條件式存取]。
5. 選擇 [新增原則]。
6. 在 [新增] 原則中，鍵入原則的描述性名稱。
7. 在 [指派] 區段中，選擇 [使用者和群組]。
8. 在 [使用者和群組] 中，選擇將接收這個原則的使用者或群組，然後選擇 [完成]。
9. 在 [指派] 區段中，選擇 [雲端應用程式]。
10. 在 [雲端應用程式] 的 [包含] 索引標籤上，選擇 [選取應用程式]，並選擇 [選取] > [Microsoft Intune 註冊]，然後選擇 [完成]。
11. 在 [指派] 區段中，選擇 [條件]。
12. 在 [條件] 中，您不需要設定 MFA 的任何設定。
13. 在 [存取控制] 區段中，選擇 [授與]。
14. 在 [授與] 中，選擇 [授與存取權]，然後選取 [需要多重要素驗證]。
    請不要選取 [裝置需要標記為合規]，因為在註冊之前無法評估裝置的合規性。
15. 選擇 [選取]。
16. 在 [新增原則] 中，選擇 [啟用原則] > [開啟]，然後選擇 [建立]。



## <a name="next-steps"></a>後續步驟

終端使用者在註冊其裝置時，現在必須使用第兩種形式的識別進行驗證，例如 PIN、電話或生物特徵辨識。

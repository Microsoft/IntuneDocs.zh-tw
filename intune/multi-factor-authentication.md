---
title: 需要 Intune 裝置註冊的多重要素驗證
titlesuffix: Microsoft Intune
description: 如何在 Azure AD 中針對 Intune 裝置註冊要求多重要素驗證。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 01/10/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 94280c73-c05c-4e72-b0dd-a7cb997782f9
ROBOTS: ''
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 2e48e782a3da5f7b367236218e8ec036a5c1b7f6
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2018
ms.locfileid: "52179706"
---
# <a name="require-multi-factor-authentication-for-intune-device-enrollments"></a>需要 Intune 裝置註冊的多重要素驗證

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

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
>請不要針對 Microsoft Intune 註冊設定 [以裝置為準的存取規則]。

1. 使用您的認證登入您的 [Microsoft Azure 入口網站](https://portal.azure.com)。
2. 在入口網站中，移至 [[Azure Active Directory](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Overview)]。
3. 在 [Azure Active Directory] 的 [安全性] 下，選擇 [[條件式存取](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConditionalAccessBlade/Policies)]。
4. 選擇 [新增原則]。
5. 在 [新增] 原則中，鍵入原則的描述性名稱。
6. 在 [指派] 區段中，選擇 [使用者和群組]。
7. 在 [使用者和群組] 中，選擇 [選取使用者或群組]，並核取 [使用者和群組]。 接著，選取將接收這個政策的使用者和/或群組，然後選擇 [完成]。
8. 在 [指派] 區段中，選擇 [雲端應用程式]。
9. 在 [雲端應用程式] 的 [包含] 索引標籤上，選擇 [選取應用程式]，並選擇 [選取] > [Microsoft Intune 註冊]，然後選擇 [完成]。
10. 在 [指派] 區段的 [條件] 中，您不需要設定 MFA 的任何設定。
11. 在 [存取控制] 區段中，選擇 [授與]。
12. 在 [授與] 中，選擇 [授與存取權]，然後選取 [需要多重要素驗證]。 請不要選取 [裝置需要標記為合規]，因為在註冊之前無法評估裝置的合規性。 然後選擇 [選取]。
13. 在 [新增原則] 中，選擇 [啟用原則] > [開啟]，然後選擇 [建立]。



## <a name="next-steps"></a>接下來的步驟

終端使用者在註冊其裝置時，現在必須使用第兩種形式的識別進行驗證，例如 PIN、電話或生物特徵辨識。

---
title: 保護電子郵件和 Office 365
description: 本主題說明如何使用條件式存取，僅允許符合規範的裝置存取 SharePoint Online 與其他服務上的公司電子郵件和公司資料。
keywords: ''
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 01/03/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: c564d292-b83b-440d-bf08-3f5b299b7a5e
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: e121a3aaf4988bd92c36eb79131b2205263fb309
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="protect-access-to-email-office-365-and-other-services-with-microsoft-intune"></a>使用 Microsoft Intune 限制電子郵件、Office 365 和其他服務的存取

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

您可以使用 Enterprise Mobility + Security (EMS) 的條件式存取，保護公司電子郵件、Office 365 服務 (例如 **Exchange 內部部署**、**Exchange Online**、**Exchange Online Dedicated**、**SharePoint Online**、**商務用 Skype Online**) 以及其他服務的存取。 這項功能可確保只有當裝置符合您透過 Intune 管理主控台或 Azure 傳統入口網站所設定的條件式存取規則時，才能存取公司電子郵件和 Office 365 服務。
## <a name="how-does-conditional-access-work"></a>條件式存取的運作方式
您可以使用合規性原則設定來評估裝置的合規性。 條件式存取原則使用評估來限制或允許對特定服務的存取。 當您使用條件式存取原則搭配裝置相容性原則時，只有符合規範的裝置才能存取服務。 合規性政策和條件式存取原則會部署至使用者。 使用者用來存取服務的所有裝置都會受到檢查是否符合原則。

> [!IMPORTANT]
> 請記住，必須將合規性原則部署至使用裝置的使用者，才能評估裝置的合規性。
> 如果沒有將合規性原則部署至使用者，裝置就被視為符合規範，而不會套用存取限制。

當裝置不符合原則中設定的條件時，將會引導使用者註冊裝置並修正造成裝置不符合規範的問題。

條件式存取的一般流程︰

![此圖顯示用來決定允許或禁止裝置存取服務的決策點](../media/ConditionalAccess4.png)

## <a name="setup-considerations"></a>設定考量

### <a name="licensing"></a>授權

Microsoft Intune 和 Azure Active Directory (Azure AD) Premium 可完美合作，藉由 EMS 條件式存取，提供多種層級的控制，因此，如果您想要使用 Intune 來部署條件式存取原則，必須具備這兩種產品的授權。

**Azure AD Premium 授權**可以獨立服務的形式來購買，或與企業版合約一起購買 (連同 Intune)。 如果您要使用 Intune 來部署條件式存取原則，請務必取得適當的 Azure AD Premium 或 **EMS 授權**。

- 深入了解 [Enterprise Mobility 定價頁面](https://www.microsoft.com/cloud-platform/enterprise-mobility-pricing)或 [Azure Active Directory 定價頁面](https://azure.microsoft.com/pricing/details/active-directory/)。

此外，請確認您已[指派 Azure AD Premium 或 EMS 授權](/intune/licenses-assign)給要套用條件式存取原則的目標使用者。

### <a name="device-compliance-settings"></a>裝置相容性設定

若要設定條件式存取，請設定裝置合規性原則和條件式存取原則。 相容性原則包含密碼、加密及裝置是否已進行 JB 破解等設定。 裝置必須符合這些規則才算相容。

- 深入了解[裝置相容性原則及其運作方式](introduction-to-device-compliance-policies-in-microsoft-intune.md)。

### <a name="conditional-access-policy"></a>條件式存取原則

您可以根據下列資訊，設定條件式存取原則來限制存取︰
- 裝置合規性狀態。
- 在裝置上執行的平台。
- 用來存取服務的應用程式類型。

不同於其他 Intune 原則，您不用部署條件式存取原則。 反之，在您設定原則並選取應該有此原則的使用者之後，此原則就會套用至所有目標使用者。 當使用者成為原則的目標時，他們使用的每個裝置都必須符合規範，才能存取資源。


## <a name="next-steps"></a>接下來的步驟


2. [建立裝置相容性原則](create-a-device-compliance-policy-in-microsoft-intune.md)。

3. 針對下列 Microsoft 雲端服務/產品建立條件式存取原則：

   - [建立 Exchange Online 的條件存取原則](restrict-access-to-exchange-online-with-microsoft-intune.md)
   - [建立 Exchange 內部部署的條件存取原則](restrict-access-to-exchange-onpremises-with-microsoft-intune.md)
   - [建立 Exchange Online Dedicated 的條件存取原則](restrict-access-to-exchange-online-with-microsoft-intune.md)
   - [建立舊版 Exchange Online Dedicated 的條件存取原則](restrict-access-to-exchange-onpremises-with-microsoft-intune.md)
   - [建立 SharePoint Online 的條件式存取原則](restrict-access-to-sharepoint-online-with-microsoft-intune.md)
   - [建立商務用 Skype Online 的條件式存取原則](restrict-access-to-skype-for-business-online-with-microsoft-intune.md)
   - [建立 Dynamics CRM Online 的條件式存取原則](restrict-access-to-dynamics-crm-online-with-microsoft-intune.md)

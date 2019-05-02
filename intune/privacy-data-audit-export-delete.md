---
title: 稽核、匯出或刪除個人資料
description: 了解如何稽核、匯出或刪除個人資料。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/18/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 96990be0-eb1e-43a4-a0e4-09c7dbdc2bf4
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5a253894e400e4b63de40d2d8ef56cefef5b2ca0
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61512795"
---
# <a name="audit-export-or-delete-personal-data-in-intune"></a>在 Intune 中稽核、匯出或刪除個人資料

Intune 管理員可以使用稽核記錄來追蹤與個人資料相關的活動。 管理員也可以匯出及刪除個人資料。

[!INCLUDE [GDPR-related guidance](./includes/gdpr-intro-sentence.md)]

## <a name="audit-personal-data"></a>稽核個人資料

稽核記錄提供租用戶管理員在 Microsoft Intune 中產生變更之活動的記錄。 稽核記錄可用於許多管理活動，通常包括建立、更新 (編輯)、刪除和指派動作。 也可以檢閱產生稽核事件的遠端工作。 這些稽核記錄可能會包含在 Intune 中註冊其裝置的使用者個人資料。  

基於安全性目的，Intune 可能會維護使用者和裝置動作的稽核記錄一年。 這些記錄在一年保留期後會自動刪除。

若要檢閱稽核記錄，請參閱 [Intune 活動的稽核記錄](monitor-audit-logs.md)。 

管理員無法刪除稽核記錄。

這些稽核事件會保留一年。 租用戶管理員可以使用[此支援要求表單](https://privacy.microsoft.com/en-US/privacy-questions?)來要求稽核記錄。

## <a name="export-personal-data"></a>匯出個人資料

管理員可以匯出終端使用者的個人資料 (包括帳戶、服務資料和相關聯記錄)，以符合資料主體權限要求。 您及您的組織會決定是否要為資料主體提供個人資料複本，或您是否有正當商業理由要保留它。 如果您決定提供，您可以為其提供實際文件複本、適當修訂的版本，或您認定適合共用之部分的螢幕擷取畫面。

若要匯出使用者的個人資料，您可以使用： 
- [Intune MDM 裝置] 刀鋒視窗來匯出裝置清單。 您也可以直接複製裝置資料。
- [Export-IntuneData.ps1 指令碼](https://aka.ms/intunedataexport)。

## <a name="delete-end-user-personal-data"></a>刪除終端使用者的個人資料

有三種方式可從 Intune 管理中移除個人資料：
- 從 Azure Active Directory 中刪除使用者
- 將裝置重設為原廠設定
- 使用者自行移除

### <a name="delete-a-user-from-intune"></a>從 Intune 中刪除使用者

若要從 Intune 中刪除終端使用者的個人資料，管理員必須[從 Azure Active Directory (AAD) 中刪除使用者](https://docs.microsoft.com/azure/active-directory/add-users-azure-active-directory.md#delete-users-from-azure-ad)。 從 AAD 中刪除 (實刪除) 使用者時，Intune 會從 AAD 收到刪除訊號，然後自動開始從 Intune 服務中清除該使用者的所有個人資料。 使用者的資訊會在移除動作的 30 天內，從 Intune 服務中刪除。

### <a name="reset-device-to-factory-settings"></a>將裝置重設為原廠設定
重設為原廠設定會將所有的公司和個人資料與設定還原為原廠設定。 這有助於提供裝置給下一個員工。 使用者檔案、使用者安裝的應用程式和非預設設定都會遭到移除，而且此資料會在移除動作的 30 天內，從 Intune 服務中刪除。

### <a name="user-self-removal-from-intune-management"></a>使用者自行從 Intune 管理中移除
使用者可在沒有管理員協助的情況下，從 Intune 管理中移除其 [Android、Apple 或 Windows](https://docs.microsoft.com/intune-user-help/unenroll-your-device-from-intune-android.md) 個人裝置。   

### <a name="retire"></a>淘汰
**淘汰**動作會移除 Intune 佈建的資料 (例如公司應用程式)、Intune 正在管理的應用程式相關資料、原則設定，以及透過 Intune 佈建的電子郵件設定檔。 此動作會將使用者的個人資料保留在裝置上。

### <a name="delete-a-tenant-from-microsoft-intune"></a>從 Microsoft Intune 刪除租用戶

如果 Intune 租用戶客戶取消其 Intune 帳戶，則會在客戶關閉 Intune 帳戶 180 天內刪除所有租用戶資料。 如果 AAD 租用戶與其他 Microsoft 企業訂用帳戶 (Azure、Office 365) 建立關聯，則只會刪除 Intune 客戶資料。 AAD 租用戶資源會保留以供其他訂用帳戶使用。 如果 Intune 帳戶是唯一與 AAD 租用戶建立關聯的訂用帳戶，則會刪除租用戶，並同時刪除所有資源和客戶資料。

### <a name="delete-a-user-in-a-hybrid-mobile-device-management-mdm-environment"></a>刪除混合式行動裝置管理 (MDM) 環境中的使用者
當您有混合式 MDM 環境 (與 Configuration Manager 整合的 Intune) 時，您必須完成下列動作 (依序) 才能完全刪除使用者，並將其從您的本機 Active Directory、Configuration Manager 和 Intune 中完全移除。

1. 從您的本機 Active Directory (AD) 中刪除使用者。 這會防止使用者同步到 Azure AD，以及被 Configuration Manager 探索發現。 
2. 從 Configuration Manager 主控台中刪除使用者，以從 Configuration Manager 中移除使用者和相關聯資料。 在主控台中，移至 [Asset and Compliance] \(資產與合規性\) > [使用者]，以滑鼠右鍵按一下要刪除的使用者，然後按一下 [刪除]。
3. [從 AAD 中刪除使用者](https://docs.microsoft.com/azure/active-directory/add-users-azure-active-directory.md#delete-users-from-azure-ad)，這會同時從 Azure Active Directory 和 Intune 中移除使用者和相關聯資料。 從 AAD 中刪除 (實刪除) 使用者時，Intune 會從 AAD 收到刪除訊號，然後自動開始從 Intune 服務中清除該使用者的所有個人資料。 使用者的資訊會在移除動作的 30 天內，從 Intune 服務中刪除。

> [!Important]
>新混合式 MDM 客戶的上線功能已淘汰。 如需詳細資訊，請參閱 [Move from Hybrid Mobile Device Management to Intune on Azure](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Move-from-Hybrid-Mobile-Device-Management-to-Intune-on-Azure/ba-p/280150) (從混合式行動裝置管理移到 Azure 上的 Intune) 部落格文章。

## <a name="next-steps"></a>後續步驟

了解如何在 Intune 中[稽核、匯出或刪除](privacy-data-audit-export-delete.md)個人資料。

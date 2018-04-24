---
title: Intune 資料倉儲變更記錄檔
titlesuffix: Microsoft Intune
description: Intune 資料倉儲 API 中的變更清單。
keywords: Intune 資料倉儲
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/23/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: E85DBB2D-67BB-4E10-82D6-E43046B9C43C
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 8e11585adf570ba9155861f89688c33ac6cecbeb
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="change-log-for-the-intune-data-warehouse-api"></a>Intune 資料倉儲 API 的變更記錄檔

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

保持 Intune 資料倉儲更新的最新狀態。

## <a name="1801"></a>1801
_發行日期：2018 年 1 月_

### <a name="intune-data-warehouse-application-only-authentication----1867540---"></a>僅限 Intune 資料倉儲應用程式的驗證<!-- 1867540 -->

您可以使用 Azure Active Directory (Azure AD) 來設定應用程式並向 Intune 資料倉儲驗證。 如需詳細資訊，請參閱[僅限 Intune 資料倉儲應用程式的驗證](data-warehouse-app-only-auth.md)。

### <a name="azure-ad-and-intune-credential-requirements----2077525---"></a>Azure AD 和 Intune 認證需求<!-- 2077525 -->

- 存取 Intune 資料倉儲 (包括 API) 時，不再需要指派 Intune 授權給使用者。
- Intune 角色名稱已從**報表**變更為 **Intune 資料倉儲**。 

    如需詳細資訊，請參閱 [Azure AD 和 Intune 認證需求](reports-api-url.md#azure-ad-and-intune-credential-requirements)。

### <a name="odata-query-options----2077711---"></a>OData 查詢選項<!-- 2077711 -->

您可以使用 <code>$select</code> 作為 OData 查詢參數。 目前版本支援下列 OData 查詢參數：<code>$filter</code>、<code>$orderby</code>、<code>$select</code>、<code>$skip</code> 及 <code>$top</code>。 如需詳細資訊，請參閱 [OData 查詢選項](reports-api-url.md#odata-query-options)。

### <a name="new-entities-in-the-in-data-warehouse-data-model----2077804---"></a>資料倉儲資料模型中的新實體 <!-- 2077804 -->

 - 已新增 [**MobileAppDeviceuserInstallStatus**](reports-ref-application.md#mobileappdeviceuserinstallstatus) 實體。 **MobileAppDeviceUserInstallStatus** 代表針對特定裝置或使用者的行動應用程式安裝狀態。
 - 已新增 [**MobileAppInstallState**](reports-ref-application.md#mobileappinstallstate) 實體。 **MobileAppInstallState** 實體代表行動應用程式在被指派至包含裝置或使用者 (或兩者) 的群組之後的安裝狀態。 

## <a name="1710"></a>1710
_發行日期：2017 年 11 月_

### <a name="a-new-entity-collection-named-current-user-is-limited-to-currently-active-user-data----1544273---"></a>名為 Current User 的新實體集合限於目前作用中的使用者資料 <!-- 1544273 -->

**User** 實體集合包含企業中具有所指派授權的所有 Azure Active Directory (Azure AD) 使用者。 這些資料列包含資料收集期間的使用者狀態，即使使用者已經被移除。 例如，某個使用者可能在上個月內被新增到 Intune 然後又被移除。 雖然在報告的時候這個使用者不會出現，但使用者和狀態會出現在資料中。 您可以建立一個報告，其中顯示使用者的歷程記錄在您資料中出現的期間。

相較之下，新的 **Current User** 實體集合只包含尚未被移除的使用者。 **Current User** 實體集合只包含目前作用中的使用者。 如需 **Current User** 實體的詳細資訊，請參閱 [Current User 實體的參考](reports-ref-current-user.md)。

## <a name="1709"></a>1709
_發行日期：2017 年 10 月_

### <a name="user-device-association-entity-collection-added-to-intune-data-warehouse-data-model----1187917---"></a>使用者裝置關聯實體集合已新增至 Intune 資料倉儲資料模型 <!-- 1187917 -->

您現在可以使用使用者裝置關聯資訊 (關聯使用者和裝置實體集合) 來建立報表和資料視覺效果。 資料模型的存取可透過擷取自資料倉儲 Intune 頁面的 Power BI 檔案 (PBIX)、透過 OData 端點，或開發自訂用戶端來存取。 如需詳細資訊，請參閱[使用者裝置關聯](reports-ref-user-device.md)。

### <a name="new-entities-in-the-in-data-warehouse-data-model----1479526--------"></a>資料倉儲資料模型中的新實體 <!-- 1479526 --><!-- -->

 - 已新增 [**UserDeviceAssociation**](reports-ref-user-device.md) 實體。 **UserDeviceAssociation** 包含您組織中的使用者裝置關聯。 您現在可以使用使用者裝置關聯資訊 (關聯使用者和裝置實體集合) 來建立報表和資料視覺效果。  
 - 已新增實體 [**IntuneManagementExtension**](reports-ref-intunemanagementextension.md)。 **IntuneManagementExtension** 包含的行動裝置實體，會追蹤版本和安裝狀態等資訊。

## <a name="next-steps"></a>接下來的步驟
 - 了解[每週的 Intune 新功能](whats-new.md)。 您也可以了解即將推出的變更、關於服務的重要通知，以及過去版本的相關資訊。
 - 閱讀 [Microsoft Intune 部落格](http://go.microsoft.com/fwlink/?LinkID=273882)。

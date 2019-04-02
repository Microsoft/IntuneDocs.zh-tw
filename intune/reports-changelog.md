---
title: Intune 資料倉儲變更記錄檔
titlesuffix: Microsoft Intune
description: 本主題提供 Microsoft Intune 資料倉儲 API 的變更清單。
keywords: Intune 資料倉儲
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/21/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: E85DBB2D-67BB-4E10-82D6-E43046B9C43C
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: d7d69c602471e8508744f2a00008294cbd335204
ms.sourcegitcommit: 93286c22426dcb59191a99e3cf2af4ff6ff16522
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/22/2019
ms.locfileid: "58358253"
---
# <a name="change-log-for-the-intune-data-warehouse-api"></a>Intune 資料倉儲 API 的變更記錄檔

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

保持 Intune 資料倉儲更新的最新狀態。

## <a name="1903"></a>1903
_發行日期：2019 年 3 月_

### <a name="v10-changes-reflecting-back-to-beta"></a>V1.0 變更反映至 beta 版
當 V1.0 1808 引進時，它不一致的顯著區別從 beta 版的 API。 在 1903，這些變更將會反映回 beta 版的 API 版本。 如果您有使用 beta 版的 API 版本的重要報表，我們強烈建議以避免中斷性變更 V1.0 切換這些報表。 請參閱[API 版本資訊](reports-api-url.md)如需詳細資訊，在資料倉儲 API 版本及向後相容性。 

## <a name="1902"></a>1902 
_發行日期：2019 年 2 月_

### <a name="power-bi-compliance-app"></a>Power BI 合規性的應用程式 

存取您在 Power BI Online 中使用的 Intune 資料倉儲[Intune 合規性 （資料倉儲）](https://app.powerbi.com/groups/me/getapps/services/Intune_dw_compliance)應用程式。 使用此 Power BI 應用程式中，您現在可以存取及共用預先建立的報表，不必進行任何設定，而不需離開您的 web 瀏覽器。 

> [!NOTE]
> 有兩個額外的篩選器，您可以套用到 Intune 合規性的應用程式。

#### <a name="add-additional-filters-to-the-intune-compliance-app"></a>Intune 合規性應用程式中新增其他篩選器
1. 開啟[Intune 合規性 （資料倉儲）](https://app.powerbi.com/groups/me/getapps/services/Intune_dw_compliance)您網頁瀏覽器中的應用程式。
2. 按一下 **不符合規範的裝置**，然後選取**不符合規範**中**complianceStatus**篩選器。 
3. 按一下 **不明裝置**，然後選取**尚無法使用**中**complianceStatus**篩選器。 

## <a name="1812"></a>1812 
_發行日期：2018 年 12 月_

### <a name="enrollment-activities-collection-released-to-v10"></a>Enrollment Activities 集合已發行為 v1.0 

v1.0 現在提供 Enrollment Activities 集合。 您可以使用此集合來了解環境中的註冊失敗數量和趨勢。 如需詳細資訊，請參閱 [enrollmentActivities](intune-data-warehouse-collections.md#enrollmentactivities)、[enrollmentEventStatuses](intune-data-warehouse-collections.md#enrollmenteventstatuses)、[enrollmentFailureCategories](intune-data-warehouse-collections.md#enrollmentfailurecategories) 和 [enrollmentFailureReasons](intune-data-warehouse-collections.md#enrollmentfailurereasons)。

## <a name="1808"></a>1808
_發行日期：2018 年 8 月_

### <a name="v10-collections"></a>v1.0 集合  

您現在可以藉由設定查詢參數 `api-version=v1.0` 來使用 Intune 資料倉儲 v1.0 版。 資料倉儲中對集合所進行的更新為附加性質，因此不會破壞現有的案例。

### <a name="enrollment-activities-collection-released-to-beta"></a>Enrollment Activities 集合已發行為搶鮮版 (Beta)

新的 `Enrollment Activities` 集合已發行為搶鮮版 (Beta)。 您可以使用此集合檢視最常見的失敗，來了解您註冊目前進行的狀況。 


## <a name="1805"></a>1805
_2018 年 5 月發行_

### <a name="correction-to-device-count-in-devices-collection"></a>更正**裝置**集合中的裝置計數 

已經針對**裝置**集合做出一個修正，它有可能會降低屬性 `isDeleted` 篩選的裝置總計數。 此下拉式清單是在更正錯誤的結果，這並不是錯誤。 如需有關**裝置**集合的詳細資訊，請參閱[裝置實體的參考](reports-ref-devices.md)。 


## <a name="1801"></a>1801
_發行日期：2018 年 1 月_

### <a name="intune-data-warehouse-application-only-authentication----1867540---"></a>僅限 Intune 資料倉儲應用程式的驗證 <!-- 1867540 -->

您可以使用 Azure Active Directory (Azure AD) 來設定應用程式並向 Intune 資料倉儲驗證。 如需詳細資訊，請參閱[僅限 Intune 資料倉儲應用程式的驗證](data-warehouse-app-only-auth.md)。

### <a name="azure-ad-and-intune-credential-requirements----2077525---"></a>Azure AD 和 Intune 認證需求 <!-- 2077525 -->

- 存取 Intune 資料倉儲 (包括 API) 時，不再需要指派 Intune 授權給使用者。
- Intune 角色名稱已從**報表**變更為 **Intune 資料倉儲**。 

    如需詳細資訊，請參閱 [Azure AD 和 Intune 認證需求](reports-api-url.md#azure-ad-and-intune-credential-requirements)。

### <a name="odata-query-options----2077711---"></a>OData 查詢選項 <!-- 2077711 -->

您可以使用 <code>$select</code> 作為 OData 查詢參數。 目前版本支援下列 OData 查詢參數：<code>$filter</code>、<code>$orderby</code>、<code>$select</code>、<code>$skip</code> 及 <code>$top</code>。 如需詳細資訊，請參閱 [OData 查詢選項](reports-api-url.md#odata-query-options)。

### <a name="new-entities-in-the-in-data-warehouse-data-model----2077804---"></a>資料倉儲資料模型中的新實體 <!-- 2077804 -->

 - 已新增 [**MobileAppDeviceuserInstallStatus**](reports-ref-application.md) 實體。 **MobileAppDeviceUserInstallStatus** 代表針對特定裝置或使用者的行動應用程式安裝狀態。
 - 已新增 [**MobileAppInstallState**](reports-ref-application.md#mobileappinstallstate) 實體。 **MobileAppInstallState** 實體代表行動應用程式在被指派至包含裝置或使用者 (或兩者) 的群組之後的安裝狀態。 

## <a name="1710"></a>1710
_發行日期：2017 年 11 月_

### <a name="a-new-entity-collection-named-current-user-is-limited-to-currently-active-user-data----1544273---"></a>名為 Current User 之新實體集合限於目前作用中的使用者資料 <!-- 1544273 -->

**User** 實體集合包含企業中具有所指派授權的所有 Azure Active Directory (Azure AD) 使用者。 這些資料列包含資料收集期間的使用者狀態，即使使用者已經被移除。 例如，某個使用者可能在上個月內被新增到 Intune 然後又被移除。 雖然在報告的時候這個使用者不會出現，但使用者和狀態會出現在資料中。 您可以建立一個報告，其中顯示使用者的歷程記錄在您資料中出現的期間。

相較之下，新的 **Current User** 實體集合只包含尚未被移除的使用者。 **Current User** 實體集合只包含目前作用中的使用者。 如需 **Current User** 實體的詳細資訊，請參閱 [Current User 實體的參考](reports-ref-current-user.md)。

## <a name="1709"></a>1709
_發行日期：2017 年 10 月_

### <a name="user-device-association-entity-collection-added-to-intune-data-warehouse-data-model----1187917---"></a>使用者裝置關聯實體集合已新增至 Intune 資料倉儲資料模型 <!-- 1187917 -->

您現在可以使用使用者裝置關聯資訊 (關聯使用者和裝置實體集合) 來建立報表和資料視覺效果。 資料模型的存取可透過擷取自資料倉儲 Intune 頁面的 Power BI 檔案 (PBIX)、透過 OData 端點，或開發自訂用戶端來存取。 如需詳細資訊，請參閱[使用者裝置關聯](reports-ref-user-device.md)。

### <a name="new-entities-in-the-in-data-warehouse-data-model----1479526--------"></a>資料倉儲資料模型中的新實體 <!-- 1479526 --><!-- -->

 - 已新增 [**UserDeviceAssociation**](reports-ref-user-device.md) 實體。 **UserDeviceAssociation** 包含您組織中的使用者裝置關聯。 您現在可以使用使用者裝置關聯資訊 (關聯使用者和裝置實體集合) 來建立報表和資料視覺效果。  
 - 已新增實體 [**IntuneManagementExtension**](reports-ref-intunemanagementextension.md)。 **IntuneManagementExtension** 包含的行動裝置實體，會追蹤版本和安裝狀態等資訊。

## <a name="next-steps"></a>後續步驟
 - 了解[每週的 Intune 新功能](whats-new.md)。 您也可以了解即將推出的變更、關於服務的重要通知，以及過去版本的相關資訊。
 - 閱讀 [Microsoft Intune 部落格](https://go.microsoft.com/fwlink/?LinkID=273882)。

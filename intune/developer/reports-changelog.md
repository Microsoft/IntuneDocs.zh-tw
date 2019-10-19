---
title: Intune 資料倉儲變更記錄檔
titleSuffix: Microsoft Intune
description: 本主題提供 Microsoft Intune 資料倉儲 API 的變更清單。
keywords: Intune 資料倉儲
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/23/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: developer
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: E85DBB2D-67BB-4E10-82D6-E43046B9C43C
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: f9740eed3ab727d76a9af4e46642d8279b310fd9
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72490533"
---
# <a name="change-log-for-the-intune-data-warehouse-api"></a>Intune 資料倉儲 API 的變更記錄檔

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

保持 Intune 資料倉儲更新的最新狀態。

## <a name="1903-part-2"></a>1903 (第 2 部分)
_發行日期：2019 年 4 月_

### <a name="beta-changes"></a>搶鮮版 (Beta) 變更

下表會列出 Intune 資料倉儲中最近移除的集合和替換集合。

|    集合                          |    變更     |    其他資訊                                                                                                                                                                                                                                                                                                                                                                 |
|----------------------------------------|---------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    mobileAppDeviceUserInstallStatus    |    移除    |    請改為使用 [mobileAppInstallStatusCounts](intune-data-warehouse-collections.md#mobileappinstallstatuscounts)。                                                                                                                                                                                                                                                                     |
|    enrollmentTypes                     |    移除    |    請改為使用 [deviceEnrollmentTypes](intune-data-warehouse-collections.md#deviceenrollmenttypes)。                                                                                                                                                                                                                                                                                      |
|    mdmStatuses                         |    移除    |    請改為使用 [complianceStates](intune-data-warehouse-collections.md#compliancestates)。                                                                                                                                                                                                                                                                                               |
|    workPlaceJoinStateTypes             |    移除    |    請改為使用 [devices](intune-data-warehouse-collections.md#devices) 中的 `azureAdRegistered` 屬性，以及 [devicePropertyHistories](intune-data-warehouse-collections.md#devicepropertyhistories) 集合。                                                                                                                                                                                                             |
|    clientRegistrationStateTypes        |    移除    |    請改為使用 [deviceRegistrationStates](intune-data-warehouse-collections.md#deviceregistrationstates)。                                                                                                                                                                                                                                                                             |
|    currentUser                         |    移除    |    請改為使用 [users](intune-data-warehouse-collections.md#users)。                                                                                                                                                                                                                                                                                                      |
|    mdmDeviceInventoryHistories         |    移除    |    許多屬性都是冗餘的，或是現在可在 [devicePropertyHistories](intune-data-warehouse-collections.md#devicepropertyhistories) 或 [devices](intune-data-warehouse-collections.md#devices) 集合中找到。 任何尚未與這兩個集合一同列出的 **mdmDeviceInventoryHistories** 屬性都不再提供使用。 請參閱下列詳細資料。    |

下表會列出先前可在 **mdmDeviceInventoryHistories** 集合中找到的舊屬性，以及變更/取代。 任何位於 **mdmDeviceInventoryHistories** 內但未在下方列出的屬性都已移除。

|    舊屬性                |    變更/取代                                                           |
|--------------------------------|---------------------------------------------------------------------------------|
|    cellularTechnology          |    devices 集合中的 cellularTechnology                                     |
|    deviceClientId              |    devices 集合中的 deviceId                                               |
|    deviceManufacturer          |    devices 集合中的 manufacturer                                           |
|    deviceModel                 |    devices 集合中的 model                                                  |
|    deviceName                  |    devices 集合中的 deviceName                                             |
|    deviceOsPlatform            |    devices 集合中的 deviceTypeKey                                          |
|    deviceOsVersion             |    devicePropertyHistories 集合中的 osVersion                              |
|    deviceType                  |    devices 集合中的 deviceTypeKey，參考 deviceTypes 集合    |
|    encryptionState             |    devices 集合中的 encryptionState 屬性                           |
|    exchangeActiveSyncId        |    devices 集合中的 easDeviceId 屬性                               |
|    exchangeDeviceId            |    devices 集合中的 easDeviceId                                            |
|    imei                        |    devices 集合中的 imei                                                   |
|    isSupervised                |    devices 集合中的 isSupervised 屬性                              |
|    jailBroken                  |    devicePropertyHistories 集合中的 jailBroken                             |
|    meid                        |    devices 集合中的 meid 屬性                                      |
|    oem                         |    devices 集合中的 manufacturer                                           |
|    osName                      |    devices 集合中的 deviceTypeKey，參考 deviceTypes 集合    |
|    phoneNumber                 |    devices 集合中的 phoneNumber                                            |
|    platformType                |    devices 集合中的 model                                                  |
|    product                     |    devices 集合中的 deviceTypeKey                                          |
|    productVersion              |    devicePropertyHistories 集合中的 osVersion                              |
|    serialNumber                |    devices 集合中的 serialNumber                                           |
|    storageFree                 |    devices 集合中的 freeStorageSpaceInBytes 屬性                   |
|    storageTotal                |    devices 集合中的 totalStorageSpaceInBytes 屬性                |
|    subscriberCarrierNetwork    |    devices 集合中的 subscriberCarrier 屬性                         |
|    wifimac                     |    devices 集合中的 wiFiMacAddress                                         |

下表會列出 [devicePropertyHistories](intune-data-warehouse-collections.md#devicepropertyhistories) 集合中屬性的變更： 

|    舊屬性                  |    變更/取代                                               |
|----------------------------------|---------------------------------------------------------------------|
|    categoryId                    |    deviceCategoryKey，參考 deviceCategories 集合       |
|    certExpirationDate            |    移除                                                          |
|    clientRegistrationStateKey    |    deviceRegistrationStateKey                                       |
|    createdDate                   |    devices 集合中的 enrolledDateTime                           |
|    deviceTypeKey                 |    devices 集合中的 deviceTypeKey                              |
|    easID                         |    devices 集合中的 easDeviceId                                |
|    enrolledByUser                |    devices 集合中的 userId                                     |
|    enrollmentTypeKey             |    devices 集合中的 deviceEnrollmentTypeKey                    |
|    graphDeviceIsCompliant        |    移除                                                          |
|    graphDeviceIsManaged          |    移除                                                          |
|    lastContact                   |    devices 集合中的 lastSyncDateTime                           |
|    lastContactNotification       |    移除                                                          |
|    lastContactWorkplaceJoin      |    移除                                                          |
|    lastExchangeStatusUtc         |    移除                                                          |
|    lastModifiedDateTimeUTC       |    移除                                                          |
|    lastPolicyUpdateUtc           |    移除                                                          |
|    managementAgentKey            |    managementStateKey                                               |
|    manufacturer                  |    devices 集合中的 manufacturer                               |
|    mdmStatusKey                  |    complianceStateKey，參考 complianceStates 集合    |
|    模型                         |    devices 集合中的 model                                      |
|    osFamily                      |    devices 集合中的 operatingSystem                            |
|    osRevisionNumber              |    devices 集合中的 osVersion                                  |
|    processorArchitecture         |    移除                                                          |
|    referenceId                   |    devices 集合中的 azureAdDeviceId                            |
|    serialNumber                  |    devices 集合中的 serialNumber                               |
|    workplaceJoinStateKey         |    azureAdRegistered                                                |

下表會列出 [devices](intune-data-warehouse-collections.md#devices) 集合中屬性的變更： 

|    舊屬性                  |    變更/取代                                               |
|----------------------------------|---------------------------------------------------------------------|
|    categoryId                    |    deviceCategoryKey，參考 deviceCategories 集合       |
|    certExpirationDate            |    移除                                                          |
|    clientRegistrationStateKey    |    deviceRegistrationStateKey                                       |
|    createdDate                   |    enrolledDateTime                                                 |
|    easId                         |    easDeviceId                                                      |
|    enrolledByUser                |    userId                                                           |
|    enrollmentTypeKey             |    deviceEnrollmentTypeKey                                          |
|    graphDeviceIsCompliant        |    移除                                                          |
|    graphDeviceIsManaged          |    移除                                                          |
|    lastContact                   |    lastSyncDateTime                                                 |
|    lastContactNotification       |    移除                                                          |
|    lastContactWorkplaceJoin      |    移除                                                          |
|    lastExchangeStatusUtc         |    移除                                                          |
|    lastPolicyUpdateUtc           |    移除                                                          |
|    mdmStatusKey                  |    complianceStateKey，參考 complianceStates 集合    |
|    osFamily                      |    operatingSystem                                                  |
|    processorArchitecture         |    移除                                                          |
|    referenceId                   |    azureAdDeviceId                                                  |
|    workplaceJoinStateKey         |    azureAdRegistered                                                |

下表會列出 [enrollmentActivities](intune-data-warehouse-collections.md#enrollmentactivities) 集合中屬性的變更： 

|    舊屬性         |    變更/取代         |
|-------------------------|-------------------------------|
|    enrollmentTypeKey    |    deviceEnrollmentTypeKey    |

下表會列出 [enrollmentActivities](intune-data-warehouse-collections.md#mamapplications) 集合中屬性的變更： 

|    舊屬性       |    變更/取代    |
|-----------------------|--------------------------|
|    applicationKey     |    mamApplicationKey     |
|    applicationName    |    mamApplicationName    |
|    applicationId      |    mamApplicationId      |

下表會列出 [mamApplicationInstances](intune-data-warehouse-collections.md#mamapplicationinstances) 集合中屬性的變更： 

|    舊屬性     |    變更/取代    |
|---------------------|--------------------------|
|    applicationId    |    mamApplicationId      |
|    deviceId         |    mamDeviceId           |
|    deviceType       |    mamDeviceType         |
|    deviceName       |    mamDeviceName         |

下表會列出 [mamCheckins](intune-data-warehouse-collections.md#mamcheckins) 集合中屬性的變更： 

|    舊屬性      |    變更/取代    |
|----------------------|--------------------------|
|    applicationKey    |    mamApplicationKey     |

下表會列出 [users](intune-data-warehouse-collections.md#users) 集合中屬性的變更： 

|    舊屬性             |    變更/取代    |
|-----------------------------|--------------------------|
|    startDateInclusiveUtc    |    移除               |
|    endDateInclusiveUtc      |    移除               |
|    isCurrent                |    移除               |

## <a name="1903"></a>1903
_發行日期：2019 年 3 月_

### <a name="v10-changes-reflecting-back-to-beta"></a>V1.0 變更反映回到搶鮮版 (Beta)
當 V1.0 首次在 V1.0 1808 中引進時，它與搶鮮版 (Beta) API 明顯不同。 在 1903 中，這些變更將會反映回到搶鮮版 (Beta) API 版本。 如果您有使用搶鮮版 (Beta) API 版本的重要報表，強烈建議將這些報表切換到 V1.0 以避免中斷性變更。 請參閱 [API 版本資訊](../reports-api-url.md)以取得資料倉儲 API 版本和回溯相容性的資訊。 

## <a name="1902"></a>1902 
_發行日期：2019 年 2 月_

### <a name="power-bi-compliance-app"></a>Power BI 合規性應用程式 

在 Power BI Online 中使用 [Intune 合規性 (資料倉儲)](https://aka.ms/intune/datawarehouseapi/getpowerbiapp) 應用程式，來存取您的 Intune 資料倉儲。 透過此 Power BI 應用程式中，您現在不需要任何設定也不需要離開網頁瀏覽器即可存取和共用預先建立的報表。 

> [!NOTE]
> 您可以將兩個額外的篩選套用至 Intune 相容性應用程式。

#### <a name="add-additional-filters-to-the-intune-compliance-app"></a>新增額外篩選至 Intune 相容性應用程式
1. 在您的網頁瀏覽器中開啟 [Intune 相容性 (資料倉儲)](https://aka.ms/intune/datawarehouseapi/getpowerbiapp) 應用程式。
2. 按一下 [不相容的裝置]  ，然後在 **complianceStatus** 篩選中選取 [不相容]  。 
3. 按一下 [未知的裝置]  ，然後在 **complianceStatus** 篩選中選取 [尚無法使用]  。 

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
- 已新增 [**MobileAppInstallState**](reports-ref-application.md#mobileappinstallstates) 實體。 **MobileAppInstallState** 實體代表行動應用程式在被指派至包含裝置或使用者 (或兩者) 的群組之後的安裝狀態。 

## <a name="1710"></a>1710
_發行日期：2017 年 11 月_

### <a name="a-new-entity-collection-named-current-user-is-limited-to-currently-active-user-data----1544273---"></a>名為 Current User 之新實體集合限於目前作用中的使用者資料 <!-- 1544273 -->

**User** 實體集合包含企業中具有所指派授權的所有 Azure Active Directory (Azure AD) 使用者。 這些資料列包含資料收集期間的使用者狀態，即使使用者已經被移除。 例如，某個使用者可能在上個月內被新增到 Intune 然後又被移除。 雖然在報告的時候這個使用者不會出現，但使用者和狀態會出現在資料中。 您可以建立一個報告，其中顯示使用者的歷程記錄在您資料中出現的期間。

相較之下，新的 **Current User** 實體集合只包含尚未被移除的使用者。 **Current User** 實體集合只包含目前作用中的使用者。 如需 **Current User** 實體的詳細資訊，請參閱 [Current User 實體的參考](../reports-ref-current-user.md)。

## <a name="1709"></a>1709
_發行日期：2017 年 10 月_

### <a name="user-device-association-entity-collection-added-to-intune-data-warehouse-data-model----1187917---"></a>使用者裝置關聯實體集合已新增至 Intune 資料倉儲資料模型 <!-- 1187917 -->

您現在可以使用使用者裝置關聯資訊 (關聯使用者和裝置實體集合) 來建立報表和資料視覺效果。 資料模型的存取可透過擷取自資料倉儲 Intune 頁面的 Power BI 檔案 (PBIX)、透過 OData 端點，或開發自訂用戶端來存取。 如需詳細資訊，請參閱[使用者裝置關聯](reports-ref-user-device.md)。

### <a name="new-entities-in-the-in-data-warehouse-data-model----1479526--------"></a>資料倉儲資料模型中的新實體 <!-- 1479526 --><!-- -->

- 已新增 [**UserDeviceAssociation**](reports-ref-user-device.md) 實體。 **UserDeviceAssociation** 包含您組織中的使用者裝置關聯。 您現在可以使用使用者裝置關聯資訊 (關聯使用者和裝置實體集合) 來建立報表和資料視覺效果。  
- 已新增實體 [**IntuneManagementExtension**](reports-ref-intunemanagementextension.md)。 **IntuneManagementExtension** 包含的行動裝置實體，會追蹤版本和安裝狀態等資訊。

## <a name="next-steps"></a>後續步驟
- 了解[每週的 Intune 新功能](../fundamentals/whats-new.md)。 您也可以了解即將推出的變更、關於服務的重要通知，以及過去版本的相關資訊。
- 閱讀 [Microsoft Intune 部落格](https://go.microsoft.com/fwlink/?LinkID=273882)。

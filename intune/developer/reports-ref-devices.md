---
title: 裝置 - Intune 資料倉儲
titleSuffix: Microsoft Intune
description: Intune 資料倉儲 API 中的實體集合裝置類別的參考主題。
keywords: Intune 資料倉儲
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/03/2020
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: developer
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 6955E12D-70D7-4802-AE3B-8B276F01FA4F
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 19ecbc632b924dda297b3692cabf5345b4724b30
ms.sourcegitcommit: 47c9af81c385c7e893fe5a85eb79cf08e69e6831
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/25/2020
ms.locfileid: "77575782"
---
# <a name="reference-for-devices-entities"></a>裝置實體的參考

[裝置]  類別包含的行動裝置實體，可追蹤下列資訊：

- 裝置類型
- 裝置註冊和註冊狀態
- 裝置擁有權
- 裝置管理狀態
- Azure AD 裝置成員資格的狀態
- 註冊狀態
- 裝置的歷程資訊
- 裝置上的應用程式清查

## <a name="devicetypes"></a>deviceTypes

**deviceTypes** 實體代表其他資料倉儲實體所參考的裝置類型。 裝置類型通常會描述裝置型號、製造商或兩者的組合。

| 屬性  | 說明 |
|---------|------------|
| deviceTypeID |裝置類別的唯一識別碼 |
| deviceTypeKey |資料倉儲中裝置類型的唯一識別碼 - surrogate 索引鍵 |
| deviceTypeName |裝置類型 |

### <a name="example"></a>範例

| deviceTypeID  | Name | 說明 |
|---------|------------|--------|
| 0 |桌面 |Windows Desktop 裝置 |
| 1 |WindowsRT |WindowsRT 裝置 |
| 2 |WinMO6 |Windows Mobile 6.0 裝置 |
| 3 |Nokia |Nokia 裝置 |
| 4 |WindowsPhone |Windows Phone 裝置 |
| 5 |Mac |Mac 裝置 |
| 6 |WinCE |Windows CE 裝置 |
| 7 |WinEmbedded |Windows Embedded 裝置 |
| 8 |iPhone |iPhone 裝置 |
| 9 |iPad |iPad 裝置 |
| 10 |IPod |iPod 裝置 |
| 11 |Android |使用裝置管理員的受管理 Android 裝置 |
| 12 |ISocConsumer |iSoc 消費者裝置 |
| 14 |MacMDM |使用內建的 MDM 代理程式管理的 Mac OS X 裝置 |
| 15 |HoloLens |HoloLens 裝置 |
| 16 |SurfaceHub |Surface Hub 裝置 |
| 17 |AndroidForWork |使用 Android 設定檔擁有者的受控 Android 裝置 |
| 100 |Blackberry |Blackberry 裝置 |
| 101 |Palm |掌上型裝置 |
| 255 |Unknown |未知的裝置類型 |

## <a name="enrollmentactivities"></a>enrollmentActivities 
**enrollmentActivity** 實體表示裝置註冊的活動。

| 屬性                      | 說明                                                               |
|-------------------------------|---------------------------------------------------------------------------|
| dateKey                       | 記錄此註冊活動的日期索引鍵。               |
| deviceEnrollmentTypeKey       | 註冊類型的索引鍵。                                        |
| deviceTypeKey                 | 裝置類型的索引鍵。                                                |
| enrollmentEventStatusKey      | 指出註冊成功或失敗的狀態索引鍵。    |
| enrollmentFailureCategoryKey  | 註冊失敗類別的索引鍵 (如果註冊失敗的話)。        |
| enrollmentFailureReasonKey    | 註冊失敗原因的索引鍵 (如果註冊失敗的話)。          |
| osVersion                     | 裝置的作業系統版本。                               |
| count                         | 符合上述分類的註冊活動總計數。  |

## <a name="enrollmenteventstatuses"></a>enrollmentEventStatuses 
**enrollmentEventStatus** 實體表示裝置註冊的結果。

| 屬性                   | 說明                                                                       |
|----------------------------|-----------------------------------------------------------------------------------|
| enrollmentEventStatusKey   | 資料倉儲中註冊狀態的唯一識別碼 (surrogate 索引鍵)  |
| enrollmentEventStatusName  | 註冊狀態的名稱。 請參閱下列範例。                            |

### <a name="example"></a>範例

| enrollmentEventStatusName  | 說明                            |
|----------------------------|----------------------------------------|
| 成功                    | 裝置註冊成功         |
| Failed                     | 裝置註冊失敗             |
| 無法使用              | 註冊狀態為無法使用。  |

## <a name="enrollmentfailurecategories"></a>enrollmentFailureCategories 
**EnrollmentFailureCategory** 實體表示裝置註冊失敗的原因。 

| 屬性                       | 說明                                                                                 |
|--------------------------------|---------------------------------------------------------------------------------------------|
| enrollmentFailureCategoryKey   | 資料倉儲中註冊失敗類別的唯一識別碼 (surrogate 索引鍵)  |
| enrollmentFailureCategoryName  | 註冊失敗類別的名稱。 請參閱下列範例。                            |

### <a name="example"></a>範例

| enrollmentFailureCategoryName   | 說明                                                                                                   |
|---------------------------------|---------------------------------------------------------------------------------------------------------------|
| 不適用                  | 註冊失敗類別不適用。                                                            |
| 無法使用                   | 註冊失敗類別無法使用。                                                             |
| Unknown                         | 未知的錯誤。                                                                                                |
| 驗證                  | 驗證失敗。                                                                                        |
| 授權                   | 呼叫已驗證，但未授權註冊。                                                         |
| AccountValidation               | 無法驗證用於註冊的帳戶 (帳戶已封鎖、未啟用註冊)。                      |
| UserValidation                  | 無法驗證使用者 (使用者不存在、遺失授權)。                                           |
| DeviceNotSupported              | 裝置不受行動裝置管理的支援。                                                         |
| InMaintenance                   | 帳戶維護中。                                                                                    |
| BadRequest                      | 用戶端傳送了服務不了解/支援的要求。                                        |
| FeatureNotSupported             | 此註冊所使用的功能不支援此帳戶。                                        |
| EnrollmentRestrictionsEnforced  | 系統管理員所設定的註冊限制封鎖了此註冊。                                          |
| ClientDisconnected              | 用戶端逾時，或終端使用者已中止註冊。                                                        |
| UserAbandonment                 | 終端使用者已放棄註冊。 (終端使用者已開始連線，但未能及時完成)  |

## <a name="enrollmentfailurereasons"></a>enrollmentFailureReasons  
**EnrollmentFailureReason** 實體表示在所指定失敗類別中裝置註冊失敗的更詳細原因。  

| 屬性                     | 說明                                                                               |
|------------------------------|-------------------------------------------------------------------------------------------|
| enrollmentFailureReasonKey   | 資料倉儲中註冊失敗原因的唯一識別碼 (surrogate 索引鍵)  |
| enrollmentFailureReasonName  | 註冊失敗原因的名稱。 請參閱下列範例。                            |

### <a name="example"></a>範例

| enrollmentFailureReasonName      | 說明                                                                                                                                                                                            |
|----------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 不適用                   | 註冊失敗原因不適用。                                                                                                                                                       |
| 無法使用                    | 註冊失敗原因無法使用。                                                                                                                                                        |
| Unknown                          | 未知的錯誤。                                                                                                                                                                                         |
| UserNotLicensed                  | Intune 中找不到使用者，或使用者沒有有效的授權。                                                                                                                                     |
| UserUnknown                      | Intune 無法識別使用者。                                                                                                                                                                           |
| BulkAlreadyEnrolledDevice        | 只有一位使用者可註冊裝置。 此裝置先前已由另一位使用者註冊。                                                                                                                |
| EnrollmentOnboardingIssue        | 尚未設定 Intune 行動裝置管理 (MDM) 授權單位。                                                                                                                                 |
| AppleChallengeIssue              | iOS 管理設定檔安裝已延遲或失敗。                                                                                                                                         |
| AppleOnboardingIssue             | 需要 Apple MDM Push Certificate 才能在 Intune 中註冊。                                                                                                                                       |
| DeviceCap                        | 使用者嘗試註冊超過允許上限的裝置。                                                                                                                                        |
| AuthenticationRequirementNotMet  | Intune 註冊服務無法授權此要求。                                                                                                                                            |
| UnsupportedDeviceType            | 此裝置不符合 Intune 註冊的最低需求。                                                                                                                                  |
| EnrollmentCriteriaNotMet         | 此裝置因為已設定的註冊限制規則而無法註冊。                                                                                                                          |
| BulkDeviceNotPreregistered       | 找不到此裝置的國際行動設備識別碼 (IMEI) 或序號。  若無此識別碼，即會將裝置識別為目前封鎖的個人擁有裝置。  |
| FeatureNotSupported              | 使用者嘗試存取尚未對所有客戶發行，或與您的 Intune 設定不相容的功能。                                                            |
| UserAbandonment                  | 終端使用者已放棄註冊。 (終端使用者已開始連線，但未能及時完成)                                                                                           |
| APNSCertificateExpired           | 無法使用過期的 Apple MDM Push Certificate 來管理 Apple 裝置。                                                                                                                            |
## <a name="ownertypes"></a>ownerTypes

**enrollmentType** 實體會指出裝置為公司所有、個人擁有或未知。 unknown.

| 屬性  | 說明 | 範例 |
|---------|------------|--------|
| ownerTypeID |擁有者類型的唯一識別碼。 | |
| ownerTypeKey |資料倉儲中擁有者類型的唯一識別碼 - Surrogate 索引鍵。 | |
| ownerTypeName |表示裝置的擁有者類型：  <br>公司 - 裝置為企業所有。 <br>個人 - 裝置為個人所有 (BYOD)。  <br>未知 - 無此裝置的相關資訊。 |公司個人未知 |

> [!Note]  
> 針對建立裝置動態群組時 Azure AD 中的 `ownerTypeName`，您需要將篩選值 `deviceOwnership` 設為 `Company`。 如需詳細資訊，請參閱[裝置規則](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership#rules-for-devices)。 

## <a name="managementstates"></a>managementStates

**managementStates** 實體會提供裝置狀態的詳細資訊。 在套用遠端動作的情況下，裝置如進行 JB 破解或刷機，詳細資料會很有幫助。

| 屬性  | 說明 |
|---------|------------|
| managementStateID | 管理狀態的唯一識別碼。 |
| managementStateKey | 資料倉儲中管理狀態的唯一識別碼 - surrogate 索引鍵 |
| managementStateName | 指出套用到此裝置的遠端動作狀態。 |

### <a name="example"></a>範例

| managementStateID  | Name | 說明 |
|---------|------------|--------|
| 0 |受管理 | 使用無擱置遠端動作進行管理。 |
| 1 |RetirePending | 該裝置有擱置的淘汰命令。 |
| 2 |RetireFailed | 裝置上的淘汰命令失敗。 |
| 3 |WipePending | 該裝置有擱置的抹除命令。 |
| 4 |WipeFailed | 裝置上的抹除命令失敗。 |
| 5 |Unhealthy | 狀況不良狀態。 |
| 6 |DeletePending | 該裝置有擱置的刪除命令。 |
| 7 |RetireIssued | 已向裝置發出淘汰命令。 |
| 8 |WipeIssued | 已發出抺除命令。 |
| 9 |WipeCanceled | 已取消抺除命令。 |
| 10 |RetireCanceled | 已取消淘汰命令。 |
| 11 |Discovered | Intune 新探索到的裝置，第一次簽入後就會移至 -Managed- 狀態。 |

## <a name="managementagenttypes"></a>managementAgentTypes

**ManagementAgentType** 實體代表用來管理裝置的代理程式。

| 屬性  | 說明 |
|---------|------------|
| managementAgentTypeID | 管理代理程式類型的唯一識別碼。 |
| managementAgentTypeKey | 資料倉儲中管理代理程式類型的唯一識別碼 - Surrogate 索引鍵。 |
| managementAgentTypeName |指出使用何種代理程式管理裝置。 |

### <a name="example"></a>範例

| ManagementAgentTypeID  | Name | 說明 |
|---------|------------|--------|
| 1 |EAS | 透過 Exchange Active Sync 管理的裝置 |
| 2 |MDM | 使用 MDM 代理程式管理的裝置 |
| 3 |EasMdm | 由 Exchange Active Sync 和 MDM 代理程式管理的裝置 |
| 4 |IntuneClient | Intune 電腦代理程式管理的裝置 |
| 5 |EasIntuneClient | 由 Exchange Active Sync 與 Intune 電腦代理程式管理的裝置 |
| 8 |ConfigManagerClient | 由 Configuration Manager 代理程式管理的裝置 |
| 16 |Unknown | 未知的管理代理程式類型 |

## <a name="devices"></a>devices

**devices** 實體會列出管理下的所有已註冊裝置及其對應的屬性。

|          屬性          |                                                                                       說明                                                                                      |
|:--------------------------:|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
| deviceKey                  | 資料倉儲中裝置的唯一識別碼 - surrogate 索引鍵。                                                                                                               |
| deviceId                   | 裝置的唯一識別碼。                                                                                                                                                     |
| deviceName                 | 允許命名裝置之平台上的裝置名稱。 在其他平台上，Intune 會從其他屬性建立名稱。 此屬性不適用於所有裝置。 |
| deviceTypeKey              | 此裝置的裝置類型屬性索引鍵。                                                                                                                                    |
| deviceRegistrationState    | 此裝置的用戶端註冊狀態屬性索引鍵。                                                                                                                      |
| ownerTypeKey               | 此裝置的擁有者類型屬性索引鍵：公司、個人或未知。                                                                                                    |
| enrolledDateTime           | 裝置註冊的日期與時間。                                                                                                                                         |
| lastSyncDateTime           | 使用 Intune 簽入的最後一部已知裝置。                                                                                                                                              |
| managementAgentKey         | 與此裝置相關聯的管理代理程式索引鍵。                                                                                                                             |
| managementStateKey         | 與此裝置相關聯的管理狀態索引鍵，指出遠端動作的最新狀態，或是否已 JB 破解/刷機。                                                |
| azureADDeviceId            | 此裝置的 Azure deviceID。                                                                                                                                                  |
| azureADRegistered          | 裝置是否已註冊至 Azure Active Directory。                                                                                                                             |
| deviceCategoryKey          | 與此裝置相關聯的類別索引鍵。                                                                                                                                     |
| deviceEnrollmentType       | 與此裝置相關聯的註冊類型索引鍵，指出註冊方法。                                                                                             |
| complianceStateKey         | 與此裝置相關聯的合規性狀態索引鍵。                                                                                                                             |
| osVersion                  | 裝置的作業系統版本。                                                                                                                                                |
| easDeviceId                | 裝置的 Exchange ActiveSync 識別碼。                                                                                                                                                  |
| serialNumber               | SerialNumber                                                                                                                                                                           |
| userId                     | 與裝置相關聯之使用者的唯一識別碼。                                                                                                                           |
| rowLastModifiedDateTimeUTC | 在資料倉儲中最後一次修改此裝置的 UTC 日期和時間。                                                                                                       |
| manufacturer               | 裝置製造商                                                                                                                                                             |
| 模型                      | 裝置的型號                                                                                                                                                                    |
| operatingSystem            | 裝置的作業系統。 Windows、iOS/iPadOS 等等。                                                                                                                                   |
| isDeleted                  | 顯示裝置是否已刪除的二進位檔。                                                                                                                                 |
| androidSecurityPatchLevel  | Android 安全性修補程式等級                                                                                                                                                           |
| MEID                       | MEID                                                                                                                                                                                   |
| isSupervised               | 裝置的受監督狀態                                                                                                                                                               |
| freeStorageSpaceInBytes    | 可用的儲存體 (以位元組為單位)。                                                                                                                                                                 |
| totalStorageSpaceInBytes   | 總儲存體 (以位元組為單位)。                                                                                                                                                                |
| encryptionState            | 裝置的加密狀態。                                                                                                                                                      |
| subscriberCarrier          | 裝置的用戶載波                                                                                                                                                       |
| phoneNumber                | 裝置的電話號碼                                                                                                                                                             |
| IMEI                       | IMEI                                                                                                                                                                                   |
| cellularTechnology         | 裝置的行動電話通訊技術                                                                                                                                                    |
| WiFiMacAddress             | Wi-Fi MAC                                                                                                                                                                              |
| ICCD                       | 積體電路卡識別碼                                                                                                                                                     |

## <a name="devicepropertyhistories"></a>devicePropertyHistories

**devicePropertyHistory** 實體與裝置資料表和每部裝置過去 90 天內每天記錄的每日快照集有相同的內容。 DateKey 資料行會指出每個資料列的日期。

|          屬性          |                                                                                      說明                                                                                     |
|:--------------------------:|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
| dateKey                    | 指出當日的日期資料表參考。                                                                                                                                          |
| deviceKey                  | 資料倉儲中裝置的唯一識別碼 - surrogate 索引鍵。 這是包含 Intune 裝置識別碼之裝置資料表的參考。                               |
| deviceName                 | 允許命名裝置之平台上的裝置名稱。 在其他平台上，Intune 會從其他屬性建立名稱。 此屬性不適用於所有裝置。 |
| deviceRegistrationStateKey | 此裝置的裝置註冊狀態屬性索引鍵。                                                                                                                    |
| ownerTypeKey               | 此裝置的擁有者類型屬性索引鍵：公司、個人或未知。                                                                                                  |
| managementStateKey         | 與此裝置相關聯的管理狀態索引鍵，指出遠端動作的最新狀態，或是否已 JB 破解/刷機。                                                |
| azureADRegistered          | 裝置是否已註冊至 Azure Active Directory。                                                                                                                             |
| complianceStateKey         | 針對 ComplianceState 的索引鍵。                                                                                                                                                            |
| OSVersion                  | 作業系統版本。                                                                                                                                                                          |
| jailBroken                 | 裝置是否已越獄或刷機。                                                                                                                                         |
| deviceCategoryKey          | 此裝置的裝置類別屬性索引鍵。 


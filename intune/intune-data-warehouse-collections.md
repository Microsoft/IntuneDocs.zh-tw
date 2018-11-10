---
title: Intune 資料倉儲集合
titlesuffix: Microsoft Intune
description: Intune 資料倉儲集合提供與資料倉儲 API 相關的詳細資料。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 09/04/2018
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 29f09230-dc56-43db-b599-d961967bda49
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune
ms.openlocfilehash: e54b35d677d34067bfbd0ad6aad86e3dfe17fb90
ms.sourcegitcommit: 222881461a81a93b3843c2ac86a7c24a180158d5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2018
ms.locfileid: "50971477"
---
#  <a name="intune-data-warehouse-collections"></a>Intune 資料倉儲集合

下列 Intune 資料倉儲集合提供資料倉儲 API 實體 v1.0 集合的屬性、描述和範例。 

## <a name="apprevisions"></a>appRevisions
**AppRevision** 實體會列出應用程式的所有版本。

|          屬性          |                                      說明                                      |                範例               |
|:--------------------------:|:-------------------------------------------------------------------------------------:|:------------------------------------:|
| AppKey                     | 應用程式的唯一識別碼。                                                         | 123                                  |
| ApplicationId              | 應用程式的唯一識別碼 - 類似 AppKey，但此金鑰是自然的。        | b66bc706-ffff-7437-0340-032819502773 |
| 修訂                   | 管理員在上傳二進位檔期間提及的版本。                   | 2                                    |
| 標題                      | 應用程式的標題。                                                                     | Excel                                |
| 發佈者                  | 應用程式的發行者。                                                                 | Microsoft                            |
| UploadState                | 應用程式的上傳狀態。                                                              | 1                                    |
| AppTypeKey                 | 下節會說明的 AppType 參考。                            | 1                                    |
| VppProgramTypeKey          | 後文會說明的 VppProgramType 參考。                                        | 30876                                |
| CreationTime               | 此修訂建立的時間。                                            | 11/23/2016 0:00                      |
| ModifiedTime               | 與此修訂相關的任何項目最後一次變更的時間。                            | 11/23/2016 0:00                      |
| Size                       | 二進位檔的大小 (以位元組為單位)。                                                          | 120,392,000                          |
| StartDateInclusiveUTC      | 此應用程式修訂在資料倉儲中建立的 UTC 日期和時間。      | 11/23/2016 0:00                      |
| EndDateExclusiveUTC        | 此應用程式修訂被淘汰的 UTC 日期和時間。                        | 11/23/2016 0:00                      |
| IsCurrent                  | 指出資料倉儲目前是否有此應用程式版本。         | True/False                           |
| RowLastModifiedDateTimeUTC | 在資料倉儲中最後一次修改此應用程式修訂的 UTC 日期和時間。 | 11/23/2016 0:00                      |

## <a name="apptypes"></a>appTypes
**appType** 實體會列出應用程式的安裝來源。

|   屬性  |        說明        |
|:-----------:|:-------------------------:|
| AppTypeID   | 類型識別碼           |
| AppTypeKey  | 索引鍵的 Surrogate 索引鍵 |
| AppTypeName | 應用程式類型                  |

### <a name="example"></a>範例

| AppTypeID |                名稱               |                     說明                     |
|:---------:|:---------------------------------:|:---------------------------------------------------:|
| 0         | Android 市集應用程式               | Android 市集應用程式。                             |
| 1         | Android LOB 應用程式                 | Android 企業營運應用程式。                  |
| 2         | 受控 Android 市集應用程式 (MAM) | 已啟用管理的 Android 市集應用程式。 |
| 3         | iOS 市集應用程式                   | iOS 市集應用程式。                                 |
| 4         | iOS LOB 應用程式                     | iOS 企業營運應用程式。                      |
| 5         | 受控 iOS 市集應用程式 (MAM)     | 已啟用管理的 iOS 市集應用程式。       |
| 6         | O365 專業增強版             | 適用於 Windows 10 的 Office 365 專業增強版套件。     |
| 7         | Web   應用程式                         | Web 應用程式。                                        |
| 8         | Windows Phone 8.1 市集應用程式     | Windows Phone 8.1 市集應用程式。                    |
| 9         | Windows 市集應用程式               | Windows 市集應用程式。                              |
| 10        | Windows LOB 應用程式                | Windows AppX 企業營運應用程式。              |
| 11        | Windows Mobile MSI              | MSI 企業營運應用程式。                      |
| 12        | Windows Phone LOB 應用程式           | Windows Phone 企業營運應用程式。             |

## <a name="compliancepolicystatusdeviceactivities"></a>compliancePolicyStatusDeviceActivities
下表摘要了裝置的合規性政策指派狀態。 其列出各合規性狀態下發現的裝置計數。

|    屬性   |                                                                                      說明                                                                                     |  範例 |
|:-------------:|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|:--------:|
| DateKey       | 日期索引鍵，時間點為建立合規性原則的摘要時。                                                                                                                   | 20161204 |
| Unknown       | 離線或因為其他原因而無法與 Intune 或 Azure AD 通訊的裝置數目。                                                                           | 5        |
| NotApplicable | 不適用由管理員設為目標的裝置合規性原則並不適用的裝置數目。                                                                                     | 201      |
| 符合標準     | 已成功套用一或多個由管理員設為目標的裝置合規性原則的裝置數目。                                                                        | 4083     |
| InGracePeriod | 不符合規範但仍處於由管理員所定義之寬限期內的裝置數目。                                                                                  | 57       |
| NonCompliant  | 無法套用一或多個由管理員設為目標的裝置合規性原則，或是使用者未遵循由管理員設為目標之原則的裝置數目。 | 43       |
|    錯誤      |    無法與 Intune 或 Azure AD 通訊且傳回錯誤訊息的裝置數目。                                                                          |    3     |

## <a name="compliancepolicystatusdeviceperpolicyactivities"></a>compliancePolicyStatusDevicePerPolicyActivities
下表摘要了裝置的合規性政策指派狀態，以各原則及各原則類型為基礎。 其列出指派的各項合規性政策各個合規性狀態下發現的裝置計數。

|      屬性     |                                                                                      說明                                                                                     |  範例 |
|:-----------------:|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|:--------:|
| DateKey           | 日期索引鍵，時間點為建立合規性原則的摘要時。                                                                                                                   | 20161219 |
| PolicyKey         | 建立摘要之合規性原則的索引鍵。                                                                                                                   | 10178    |
| PolicyPlatformKey | 建立摘要之合規性原則平台類型的索引鍵。                                                                                            | 5        |
| Unknown           | 離線或因為其他原因而無法與 Intune 或 Azure AD 通訊的裝置數目。                                                                           | 13       |
| NotApplicable     | 不適用由管理員設為目標的裝置合規性原則並不適用的裝置數目。                                                                                     | 3        |
| 符合標準         | 已成功套用一或多個由管理員設為目標的裝置合規性原則的裝置數目。                                                                        | 45       |
| InGracePeriod     | 不符合規範但仍處於由管理員所定義之寬限期內的裝置數目。                                                                                  | 3        |
| NonCompliant      | 無法套用一或多個由管理員設為目標的裝置合規性原則，或是使用者未遵循由管理員設為目標之原則的裝置數目。 | 7        |
| 錯誤             | 無法與 Intune 或 Azure AD 通訊且傳回錯誤訊息的裝置數目。                                                                             | 3        |
## <a name="compliancestates"></a>complianceStates

|      屬性      |                       說明                      |
|:------------------:|:------------------------------------------------------:|
| complianceStatus   | 具有 mdmStatusKey 之裝置的合規性狀態       |
| complianceStateKey | 比對裝置與合規性狀態的合規性金鑰 |
| complianceStateID  | 比對此合規性狀態的識別碼                |

### <a name="example"></a>範例

|  complianceStatus  |                       說明                      |
|:------------------:|:------------------------------------------------------:|
|    Unknown         |    不明。                                                                        |
|    符合標準       |    相容。                                                                      |
|    不符合標準    |       裝置不符合規範且已封鎖其對公司資源的存取。             |
|    衝突        |    與其他規則發生衝突。                                                      |
|    錯誤           |       錯誤。                                                                       |
|    ConfigManager   |    由 Config Manager 管理。                                                      |
|    InGracePeriod   |       裝置不符合規範，但仍可存取公司資源          |

## <a name="dates"></a>dates
**Date** 實體代表跨多個資料倉儲實體所參考的日期。

|     屬性    |                       說明                      |    範例    |
|:---------------:|:------------------------------------------------------:|:-------------:|
| DateKey         | 資料倉儲中此日期的唯一識別碼。 | 20160703      |
| FullDate        | 此日期以完整日期/時間格式表示。        | 7/3/2016 0:00 |
| DayOfWeek       | 週中的日                                            | 1             |
| DayOfMonth      | 月中的日                                           | 3             |
| DayOfYear       | 年中的日                                            | 185           |
| WeekOfYear      | 年中的週                                           | 28            |
| MonthOfYear     | 年中的月                                      | 7             |
| CalendarQuarter | 日曆季度                                       | 3             |
| CalendarYear    | 日曆年度                                          | 2016          |
| DateKey         | 資料倉儲中此日期的唯一識別碼。 | 20160703      |
| FullDate        | 此日期以完整日期/時間格式表示。        | 7/3/2016 0:00 |
| DayOfWeek       | 週中的日                                            | 1             |
| DayOfMonth      | 月中的日                                           | 3             |
| DayOfYear       | 年中的日                                            | 185           |
| WeekOfYear      | 年中的週                                           | 28            |
| MonthOfYear     | 年中的月                                      | 7             |
| CalendarQuarter | 日曆季度                                       | 3             |
| CalendarYear    | 日曆年度                                          | 2016          |

## <a name="devicecategories"></a>deviceCategories

|      屬性      |                                    說明                                   |                範例               |
|:------------------:|:--------------------------------------------------------------------------------:|:------------------------------------:|
| deviceCategoryID   | 裝置類別的唯一識別碼。                                       | fb415ba2-7c08-41f6-a5e5-685b50da2c4c |
| deviceCategoryKey  | 資料倉儲中裝置類別的唯一識別碼 - surrogate 索引鍵 | 1                                    |
| deviceCategoryName | 裝置類別的顯示名稱。                                            | Smartphones                          |

## <a name="deviceconfigurationprofiledeviceactivities"></a>deviceConfigurationProfileDeviceActivities
**DeviceConfigurationProfileDeviceActivity** 實體列出每日處於成功、擱置、失敗或錯誤狀態的裝置數目。 此數目會反映指派給實體的裝置組態設定檔。 例如，如果裝置的所有其指派原則都處於成功狀態，則會將該天的成功計數器往上加一。 如果裝置獲指派兩個設定檔，一個處於成功狀態，另一個則處於錯誤狀態，該實體會遞增成功計數器，並讓裝置處於錯誤狀態。 實體會列出過去 30 天的特定一天有多少裝置處於哪種狀態。

|  屬性 |                                          說明                                          |  範例 |
|:---------:|:---------------------------------------------------------------------------------------------:|:--------:|
| DateKey   | 資料倉儲中記錄裝置組態設定檔簽入的日期索引鍵。 | 20160703 |
| Pending   | 處於擱置狀態的唯一裝置數目。                                                    | 123      |
| 已成功 | 處於成功狀態的唯一裝置數目。                                                    | 12       |
| 錯誤     | 處於錯誤狀態的唯一裝置數目。                                                      | 10       |
| Failed    | 處於失敗狀態的唯一裝置數目。                                                     | 2        |

## <a name="deviceconfigurationprofileuseractivities"></a>deviceConfigurationProfileUserActivities 
 **DeviceConfigurationProfileUserActivity**  實體會列出每日處於成功、暫止、失敗或錯誤狀態的使用者數目。 此數目會反映指派給實體的裝置組態設定檔。 例如，如果使用者的所有其指派原則都處於成功狀態，則會將該天的成功計數器向上加一。 如果使用者獲指派兩個設定檔，一個處於成功狀態，另一個則處於錯誤狀態，會計算處於錯誤狀態的使用者。  **DeviceConfigurationProfileUserActivity**  實體會列出過去 30 天的任何一天內有多少使用者處於哪種狀態。 

| 屬性  | 說明  | 範例  |
|------------|----------------------------------------------------------------------------------------------|-----------|
| DateKey  | 將裝置組態設定檔簽入記錄在資料倉儲中的日期索引鍵。  | 20160703  |
| Pending  | 處於擱置狀態的唯一使用者數目。  | 123  |
| 已成功  | 處於成功狀態的唯一使用者數目。  | 12  |
| 錯誤  | 處於錯誤狀態的唯一使用者數目。  | 10  |
| Failed  | 處於失敗狀態的唯一使用者數目。  | 2  |

## <a name="devicepropertyhistories"></a>devicePropertyHistories

|          屬性          |                                                                                      說明                                                                                     |
|:--------------------------:|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
| DateKey                    | 指出當日的日期資料表參考。                                                                                                                                          |
| DeviceKey                  | 資料倉儲中裝置的唯一識別碼 - surrogate 索引鍵。 這是包含 Intune 裝置識別碼之裝置資料表的參考。                               |
| DeviceName                 | 允許命名裝置之平台上的裝置名稱。 在其他平台上，Intune 會從其他屬性建立名稱。 此屬性不適用於所有裝置。 |
| DeviceRegistrationStateKey | 此裝置的裝置註冊狀態屬性索引鍵。                                                                                                                    |
| OwnerTypeKey               | 此裝置的擁有者類型屬性索引鍵：公司、個人或未知。                                                                                                  |
| ManagementStateKey         | 與此裝置相關聯的管理狀態索引鍵，指出遠端動作的最新狀態，或是否已 JB 破解/刷機。                                                |
| AzureADRegistered          | 裝置是否已註冊至 Azure Active Directory。                                                                                                                             |
| ComplianceStateKey         | 針對 ComplianceState 的索引鍵。                                                                                                                                                            |
| OSVersion                  | 作業系統版本。                                                                                                                                                                          |
| JB 破解                 | 裝置是否已越獄或刷機。                                                                                                                                         |
| DeviceCategoryKey          | 此裝置的裝置類別屬性索引鍵。                                                                                                                                    |
## <a name="deviceregistrationstates"></a>deviceRegistrationStates
**DeviceRegistrationState** 實體代表其他資料倉儲集合所參考的註冊類型。 

|           屬性          |                                     說明                                     |
|:---------------------------:|:-----------------------------------------------------------------------------------:|
| deviceRegistrationStateID   | 註冊狀態的唯一識別碼                                            |
| deviceRegistrationStateKey  | 資料倉儲中註冊狀態的唯一識別碼 - surrogate 索引鍵 |
| deviceRegistrationStateName | 註冊狀態                                                                  |
|    NotRegistered                     |    未註冊                                                                                                                                                                  |
|    已登錄                        |       已登錄                                                                                                                                                                   |
|    Revoked                           |       此狀態表示 IT 系統管理員已封鎖用戶端，而且該用戶端可被解除封鎖。 裝置在被抹除或淘汰之後，也可能會處於 Revoked 狀態。        |
|    KeyConflict                       |    索引碼衝突                                                                                                                                                                    |
|    ApprovalPending                   |    擱置核准                                                                                                                                                                |
|    CertificateReset                  |    重設憑證                                                                                                                                                               |
|    NotRegisteredPendingEnrollment    |    未註冊、擱置註冊                                                                                                                                               |
|    Unknown                           |    未知的狀態                                                                                                                                                                   |

## <a name="devices"></a>裝置
**Devices** 實體會列出管理下的所有已註冊裝置及其對應的屬性。

|          屬性          |                                                                                       說明                                                                                      |
|:--------------------------:|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
| DeviceKey                  | 資料倉儲中裝置的唯一識別碼 - surrogate 索引鍵。                                                                                                               |
| DeviceId                   | 裝置的唯一識別碼。                                                                                                                                                     |
| DeviceName                 | 允許命名裝置之平台上的裝置名稱。 在其他平台上，Intune 會從其他屬性建立名稱。 此屬性不適用於所有裝置。 |
| DeviceTypeKey              | 此裝置的裝置類型屬性索引鍵。                                                                                                                                    |
| DeviceRegistrationState    | 此裝置的用戶端註冊狀態屬性索引鍵。                                                                                                                      |
| OwnerTypeKey               | 此裝置的擁有者類型屬性索引鍵：公司、個人或未知。                                                                                                    |
| EnrolledDateTime           | 裝置註冊的日期與時間。                                                                                                                                         |
| LastSyncDateTime           | 使用 Intune 簽入的最後一部已知裝置。                                                                                                                                              |
| ManagementAgentKey         | 與此裝置相關聯的管理代理程式索引鍵。                                                                                                                             |
| ManagementStateKey         | 與此裝置相關聯的管理狀態索引鍵，指出遠端動作的最新狀態，或是否已 JB 破解/刷機。                                                |
| AzureADDeviceId            | 此裝置的 Azure deviceID。                                                                                                                                                  |
| AzureADRegistered          | 裝置是否已註冊至 Azure Active Directory。                                                                                                                             |
| DeviceCategoryKey          | 與此裝置相關聯的類別索引鍵。                                                                                                                                     |
| DeviceEnrollmentType       | 與此裝置相關聯的註冊類型索引鍵，指出註冊方法。                                                                                             |
| ComplianceStateKey         | 與此裝置相關聯的合規性狀態索引鍵。                                                                                                                             |
| OSVersion                  | 裝置的作業系統版本。                                                                                                                                                |
| EasDeviceId                | 裝置的 Exchange ActiveSync 識別碼。                                                                                                                                                  |
| SerialNumber               | SerialNumber                                                                                                                                                                           |
| UserId                     | 與裝置相關聯之使用者的唯一識別碼。                                                                                                                           |
| RowLastModifiedDateTimeUTC | 在資料倉儲中最後一次修改此裝置的 UTC 日期和時間。                                                                                                       |
| 製造商               | 裝置製造商                                                                                                                                                             |
| 型號                      | 裝置的型號                                                                                                                                                                    |
| OperatingSystem            | 裝置的作業系統。 Windows、iOS 等。                                                                                                                                   |
| IsDeleted                  | 顯示裝置是否已刪除的二進位檔。                                                                                                                                 |
| AndroidSecurityPatchLevel  | Android 安全性修補程式等級                                                                                                                                                           |
| MEID                       | MEID                                                                                                                                                                                   |
| isSupervised               | 裝置的受監督狀態                                                                                                                                                               |
| FreeStorageSpaceInBytes    | 可用的儲存體 (以位元組為單位)。                                                                                                                                                                 |
| TotalStorageSpaceInBytes   | 總儲存體 (以位元組為單位)。                                                                                                                                                                |
| EncryptionState            | 裝置的加密狀態。                                                                                                                                                      |
| SubscriberCarrier          | 裝置的用戶載波                                                                                                                                                       |
| PhoneNumber                | 裝置的電話號碼                                                                                                                                                             |
| IMEI                       | IMEI                                                                                                                                                                                   |
| CellularTechnology         | 裝置的行動電話通訊技術                                                                                                                                                    |
| WiFiMacAddress             | Wi-Fi MAC                                                                                                                                                                              |


## <a name="devicetypes"></a>deviceTypes
**deviceType** 實體代表其他資料倉儲實體所參考的裝置類型。 裝置類型通常會描述裝置型號、製造商或兩者的組合。

|    屬性    |                                  說明                                 |
|:--------------:|:----------------------------------------------------------------------------:|
| DeviceTypeID   | 裝置類型的唯一識別碼                                       |
| DeviceTypeKey  | 資料倉儲中裝置類型的唯一識別碼 - surrogate 索引鍵 |
| DeviceTypeName | 裝置類型                                                                |

### <a name="example"></a>範例

| deviceTypeID |        名稱       |                      說明                      |
|:------------:|:-----------------:|:-----------------------------------------------------:|
| -1           | 無法使用   | 裝置類型無法使用。                     |
| 0            | 桌面           | Windows 桌面裝置                              |
| 1            | Windows           | Windows 裝置                                      |
| 2            | WinMO6            | Windows Mobile 6.0 裝置                           |
| 3            | Nokia             | Nokia 裝置                                        |
| 4            | WindowsPhone      | Windows Phone 裝置                                |
| 5            | Mac               | Mac 裝置                                          |
| 6            | WinCE             | Windows CE 裝置                                   |
| 7            | WinEmbedded       | Windows Embedded 裝置                             |
| 8            | iPhone            | iPhone 裝置                                       |
| 9            | iPad              | iPad 裝置                                         |
| 10           | IPod              | iPod 裝置                                         |
| 11           | Android           | 使用裝置管理員管理的 Android 裝置   |
| 12           | ISocConsumer      | iSoc 消費者裝置                                |
| 13           | Unix              | Unix 裝置                                         |
| 14           | MacMDM            | 使用內建的 MDM 代理程式管理的 Mac OS X 裝置 |
| 15           | HoloLens          | HoloLens 裝置                                    |
| 16           | SurfaceHub        | Surface Hub 裝置                                  |
| 17           | AndroidForWork    | 使用 Android 設定檔擁有者管理的 Android 裝置  |
| 18           | AndroidEnterprise | Android 企業裝置。                          |
| 100          | Blackberry        | Blackberry 裝置                                   |
| 101          | Palm              | 掌上型裝置                                         |
| 255          | Unknown           | 未知的裝置類型                                 |

## <a name="deviceenrollmenttypes"></a>deviceEnrollmentTypes
**deviceEnrollmentType** 實體會指出裝置的註冊方式。 註冊類型會擷取註冊的方法。 範例會列出不同的註冊類型及其代表的意義。

|         屬性         |                                    說明                                    |
|:------------------------:|:---------------------------------------------------------------------------------:|
| deviceEnrollmentTypeID   | 註冊類型的唯一識別碼。                                       |
| deviceEnrollmentTypeKey  | 資料倉儲中註冊類型的唯一識別碼 - surrogate 索引鍵。 |
| deviceEnrollmentTypeName | 註冊類型名稱。                                                           |

### <a name="example"></a>範例

| enrollmentTypeID |                名稱                |                                        說明                                       |
|:----------------:|:----------------------------------:|:----------------------------------------------------------------------------------------:|
| 0                | Unknown                            | 未收集註冊類型                                                      |
| 1                | UserEnrollment                     | 透過 BYOD 通道的使用者驅動註冊。                                           |
| 2                | DeviceEnrollmentManager            | 搭配裝置註冊管理員帳戶的使用者註冊。                              |
| 3                | AppleBulkWithUser                  | 搭配使用者挑戰的 Apple 大量註冊。 (DEP、Apple Configurator)                   |
| 4                | AppleBulkWithoutUser               | 沒有使用者挑戰的 Apple 大量註冊。   (DEP、Apple Configurator、Mobile Config) |
| 5                | WindowsAzureADJoin                 | Windows 10 Azure AD Join。                                                                |
| 6                | WindowsBulkUserless                | 透過搭配憑證之 ICD 的 Windows 10 大量註冊。                               |
| 7                | WindowsAutoEnrollment              | Windows 10 自動註冊。   (新增工作帳戶)                                    |
| 8                | WindowsBulkAzureDomainJoin         | Windows 10 大量 Azure AD Join。                                                           |
| 9                | WindowsCoManagement                | 由 AutoPilot 或群組原則所觸發的 Windows 10 共同管理。                       |
| 10               | WindowsAzureADJoinsUsingDeviceAuth | 使用裝置驗證的 Windows 10 Azure AD Join。                                            |


## <a name="intunemanagementextensions"></a>intuneManagementExtensions
**intuneManagementExtension** 會列出每部 Windows 10 裝置每日的 **intuneManagementExtension** 健康情況。 保留最近 60 天的資料。

|       屬性      |                          說明                          | 範例 |
|:-------------------:|:-------------------------------------------------------------:|:-------:|
| DateKey             | 日期的唯一識別碼。                                | 123     |
| TenantKey           | 租用戶的唯一識別碼。                              | 456     |
| DeviceKey           | 裝置的唯一識別碼。                              | 789     |
| ExtensionVersionKey | IntuneManagementExtension 版本的唯一識別碼。 | 1       |
| ExtensionStateKey   | 健全狀況狀態的唯一識別碼。                            | 2       |

## <a name="intunemanagementextensionhealthstates"></a>intuneManagementExtensionHealthStates
**IntuneManagementExtensionHealthState** 會列出 **IntuneManagementExtension** 所有可能的健康情況狀態。

|      屬性     |                   說明                  | 範例 |
|:-----------------:|:----------------------------------------------:|:-------:|
| ExtensionStateKey | 健康情況狀態的唯一識別碼。           | 2       |
| ExtensionState    | IntuneManagementExtension 的健康情況狀態。 | Healthy |

## <a name="intunemanagementextensionversions"></a>intuneManagementExtensionVersions
**IntuneManagementExtensionVersion** 實體會列出 **IntuneManagementExtension** 使用的所有版本。

|       屬性      |                          說明                          | 範例 |
|:-------------------:|:-------------------------------------------------------------:|:-------:|
| ExtensionVersionKey | IntuneManagementExtension 版本的唯一識別碼。 | 1       |
| ExtensionVersion    | 4 位數的版本號碼。                                   | 1.0.2.0 |

## <a name="managementagenttypes"></a>managementAgentTypes
**managementAgentType** 實體代表用來管理裝置的代理程式。

|         屬性        |                                       說明                                       |
|:-----------------------:|:---------------------------------------------------------------------------------------:|
| ManagementAgentTypeID   | 管理代理程式類型的唯一識別碼。                                         |
| ManagementAgentTypeKey  | 資料倉儲中管理代理程式類型的唯一識別碼 - Surrogate 索引鍵。 |
| ManagementAgentTypeName | 指出使用何種代理程式管理裝置。                              |

### <a name="example"></a>範例

| ManagementAgentTypeID |                名稱               |                                  說明                                 |
|:---------------------:|:---------------------------------:|:----------------------------------------------------------------------------:|
| 1                     | EAS                               | 透過 Exchange Active Sync 管理的裝置                         |
| 2                     | MDM                               | 使用 MDM 代理程式管理的裝置                                   |
| 3                     | EasMdm                            | 由 Exchange Active Sync 和 MDM 代理程式管理的裝置        |
| 4                     | IntuneClient                      | 由 Intune 電腦代理程式管理的裝置                               |
| 5                     | EasIntuneClient                   | 由 Exchange Active Sync 與 Intune 電腦代理程式管理的裝置 |
| 8                     | ConfigManagerClient               | 由 System Center Configuration Manager 代理程式管理的裝置     |
| 10                    | ConfigurationManagerClientMdm     | 由 Configuration Manager 和 MDM 管理的裝置。                    |
| 11                    | ConfigurationManagerCLientMdmEas  | 由 Configuration Manager、MDM 和 Eas 管理的裝置。               |
| 16                    | Unknown                           | 未知的管理代理程式類型                                              |
| 32                    | Jamf                              | 裝置屬性是從 Jamf 擷取。                               |
| 64                    | GoogleCloudDevicePolicyController |  由 Google CloudDPC 管理的裝置。                                 |

## <a name="managementstates"></a>managementStates
**ManagementState** 實體會提供裝置狀態的詳細資料。 在套用遠端動作的情況下，裝置如進行 JB 破解或刷機，詳細資料會很有幫助。

|       屬性      |                                     說明                                    |
|:-------------------:|:----------------------------------------------------------------------------------:|
| managementStateID   | 管理狀態的唯一識別碼。                                       |
| managementStateKey  | 資料倉儲中管理狀態的唯一識別碼 - surrogate 索引鍵。 |
| managementStateName | 指出套用到此裝置的遠端動作狀態。                 |

### <a name="example"></a>範例

| managementStateID |      名稱      |                                                   說明                                                   |
|:-----------------:|:--------------:|:---------------------------------------------------------------------------------------------------------------:|
| 0                 | 受管理        | 受管理，且沒有擱置的遠端動作。                                                                       |
| 1                 | RetirePending  | 該裝置有擱置的淘汰命令。                                                             |
| 2                 | RetireFailed   | 裝置上的淘汰命令失敗。                                                                      |
| 3                 | WipePending    | 該裝置有擱置的抹除命令。                                                               |
| 4                 | WipeFailed     | 裝置上的抹除命令失敗。                                                                        |
| 5                 | Unhealthy      | 狀況不良狀態。                                                                                              |
| 6                 | DeletePending  | 該裝置有擱置的刪除命令。                                                             |
| 7                 | RetireIssued   | 已向裝置發出淘汰命令。                                                               |
| 8                 | WipeIssued     | 已發出抺除命令。                                                                               |
| 9                 | WipeCanceled   | 已取消抺除命令。                                                                               |
| 10                | RetireCanceled | 已取消淘汰命令。                                                                             |
| 11                | Discovered     | Intune 首次探索到該裝置；在它第一次簽入後，就會被移至 -Managed- 狀態。 |

## <a name="mobileappinstallstates"></a>mobileAppInstallStates
MobileAppInstallState 實體代表行動應用程式在被指派至包含裝置、使用者或兩者的群組之後的安裝狀態。

|       屬性      |                        說明                       |
|:-------------------:|:--------------------------------------------------------:|
| AppInstallStateKey  | 您帳戶之應用程式安裝狀態的唯一識別碼。 |
| AppInstallState     | 應用程式安裝狀態的列舉值。                     |
| AppInstallStateName | 應用程式安裝狀態的名稱。                           |

## <a name="mobileappinstallstatuscounts"></a>mobileAppInstallStatusCounts
透過 Microsoft Intune 使用行動應用程式管理表示指定目標裝置類型的行動裝置應用程式安裝狀態。

|      屬性      |                                                          說明                                                          |
|:------------------:|:-----------------------------------------------------------------------------------------------------------------------------:|
| DateKey            | 記錄應用程式安裝狀態之日期的索引鍵。                                                                     |
| AppKey             | 用來識別 AppRevision 執行個體之行動應用程式的索引鍵。                                                          |
| DeviceTypeKey      | 與行動應用程式相關聯之裝置類型的索引鍵。                                                              |
| AppInstallStateKey | 用來識別 MobileAppInstallState 執行個體之應用程式安裝狀態的索引鍵。                                         |
| ErrorCode          | 由與應用程式之安裝相關的應用程式安裝程式、行動平台或服務所傳回的錯誤碼。 |
| 計數              | 總計數。                                                                                                                  |

## <a name="ownertypes"></a>ownerTypes
**ownerType** 實體會指出裝置為公司所有、個人擁有或未知。

|    屬性   |                                                                                     說明                                                                                    |           範例          |
|:-------------:|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|:--------------------------:|
| ownerTypeID   | 擁有者類型的唯一識別碼。                                                                                                                                               |                            |
| ownerTypeKey  | 資料倉儲中擁有者類型的唯一識別碼 - Surrogate 索引鍵。                                                                                                       |                            |
| ownerTypeName | 表示裝置的擁有者類型：Company - 裝置為企業所有。  Personal - 裝置為個人所有 (BYOD)。   Unknown - 無此裝置的相關資訊。 | Company   Personal Unknown |

## <a name="policies"></a>原則
**Policy** 實體列出裝置組態設定檔、應用程式組態設定檔和合規性原則。 您可以將具有行動裝置管理 (MDM) 的原則指派給企業中的群組。

|          屬性          |                                                                       說明                                                                      |                範例               |
|:--------------------------:|:------------------------------------------------------------------------------------------------------------------------------------------------------:|:------------------------------------:|
| PolicyKey                  | 代表資料倉儲中原則的唯一索引鍵。                                                                                              | 123                                  |
| PolicyId                   | 資料倉儲中原則的唯一識別碼。                                                                                                 | b66bc706-ffff-7437-0340-032819502773 |
| PolicyName                 | 原則的名稱。                                                                                                                                    | "Windows 10 Baseline"                |
| PolicyVersion              | 原則的版本。 編輯或變更原則時，會建立較新版本。                                                             | 1, 2, 3                              |
| IsDeleted                  | 指出是否已更新 [原則] 記錄。  True - 原則具有含已更新欄位的新記錄。  False - 原則的最新記錄。 | True/False                           |
| StartDateInclusiveUTC      | 在資料倉儲中建立原則的 UTC 日期和時間。                                                                              | 11/23/2016 0:00                      |
| DeletedDateUTC             | IsDeleted 變更為 True 的 UTC 日期和時間。                                                                                                   | 11/23/2016 0:00                      |
| RowLastModifiedDateTimeUTC | 在資料倉儲中最後一次修改原則的 UTC 日期和時間。                                                                        | 11/23/2016 0:00                      |

## <a name="policydeviceactivities"></a>policyDeviceActivities
下表列出每日處於成功、擱置、失敗或錯誤狀態的裝置數目。 該數目反映每個原則類型設定檔的資料。 例如，如果裝置的所有其指派原則都處於成功狀態，則會將該天的成功計數器往上加一。 如果裝置獲指派兩個設定檔，一個處於成功狀態，另一個則處於錯誤狀態，該實體會遞增成功計數器，並讓裝置處於錯誤狀態。 **policyDeviceActivity** 實體會列出過去 30 天的任何一天內有多少裝置處於哪種狀態。

|  屬性 |                                           說明                                           |        範例        |
|:---------:|:-----------------------------------------------------------------------------------------------:|:---------------------:|
| DateKey   | 資料倉儲中記錄裝置組態設定檔簽入的日期索引鍵。 | 20160703              |
| Pending   | 處於擱置狀態的唯一裝置數目。                                                    | 123                   |
| 已成功 | 處於成功狀態的唯一裝置數目。                                                    | 12                    |
| PolicyKey | 原則索引鍵，可以與 Policy 聯結以取得 policyName。                                  | Windows 10 基準 |
| 錯誤     | 處於錯誤狀態的唯一裝置數目。                                                      | 10                    |
| Failed    | 處於失敗狀態的唯一裝置數目。                                                     | 2                     |

## <a name="policyplatformtypes"></a>policyPlatformTypes

|        屬性        |                      說明                      |     範例    |
|:----------------------:|:-----------------------------------------------------:|:--------------:|
| PolicyPlatformTypeKey  | 原則平台類型的唯一索引鍵。        | 20170519       |
| PolicyPlatformTypeId   | 原則平台類型的唯一識別碼。 | 1              |
| PolicyPlatformTypeName | 原則平台類型的名稱。              | AndroidForWork |

## <a name="policytypeactivities"></a>policyTypeActivities
**PolicyTypeActivity** 實體列出處於成功、擱置、失敗或錯誤狀態的累積裝置數目。 它會列出與每日裝置組態設定檔、應用程式組態設定檔或相容性原則有關的這些狀態。

|    屬性   |                                          說明                                          |           範例           |
|:-------------:|:---------------------------------------------------------------------------------------------:|:---------------------------:|
| DateKey       | 資料倉儲中記錄裝置組態設定檔簽入的日期索引鍵。 | 20160703                    |
| PolicyKey     | 原則索引鍵，可以與 Policy 聯結以取得 policyName。                                | Windows 10 基準         |
| PolicyTypeKey | 原則索引鍵類型，可以與 PolicyType 聯結以取得原則類型名稱。             | Windows 10 合規性原則 |
| Pending       | 處於擱置狀態的唯一裝置數目。                                                    | 123                         |
| 已成功     | 處於成功狀態的唯一裝置數目。                                                    | 12                          |
| 錯誤         | 處於錯誤狀態的唯一裝置數目。                                                      | 10                          |
| Failed        | 處於失敗狀態的唯一裝置數目。                                                     | 2                           |

## <a name="policytypes"></a>policyTypes
**PolicyType** 實體列出裝置組態設定檔、應用程式組態設定檔和合規性原則的類型。 您可以將具有行動裝置管理 (MDM) 的原則指派給企業中的群組。

|    屬性    |                       說明                      |            範例            |
|:--------------:|:------------------------------------------------------:|:-----------------------------:|
| PolicyTypeId   | 來源系統中原則的唯一識別碼。  | 123                           |
| PolicyTypeKey  | 資料倉儲中原則的唯一識別碼。 | 1                             |
| PolicyTypeName | 原則類型的名稱。                               | Windows 10 合規性原則。 |

## <a name="policyuseractivities"></a>policyUserActivities
下表列出每日處於成功、擱置、失敗或錯誤狀態的使用者數目。 該數目反映每個原則類型設定檔的資料。 例如，如果使用者的所有其指派原則都處於成功狀態，則會將該天的成功計數器向上加一。 如果使用者獲指派兩個設定檔，一個處於成功狀態，另一個則處於錯誤狀態，會計算處於錯誤狀態的使用者。 **PolicyUserActivity** 實體會列出過去 30 天的任何一天內有多少使用者處於哪種狀態。

|  屬性 |                                          說明                                          |       範例       |
|:---------:|:---------------------------------------------------------------------------------------------:|:-------------------:|
| DateKey   | 資料倉儲中記錄裝置組態設定檔簽入的日期索引鍵。 | 20160703            |
| Pending   | 處於擱置狀態的唯一裝置數目。                                                    | 123                 |
| 已成功 | 處於成功狀態的唯一裝置數目。                                                    | 12                  |
| PolicyKey | 原則索引鍵，可以與 Policy 聯結以取得 policyName。                                | Windows 10 基準 |
| 錯誤     | 處於錯誤狀態的唯一裝置數目。                                                      | 10                  |

## <a name="termsandconditions"></a>termsAndConditions
**termsAndConditions** 實體表示指定條款及條件 (T&C) 原則的中繼資料與內容。 T&C 原則的內容會在使用者首次嘗試註冊至 Intune 時呈現給他們，之後則會在系統管理員做出編輯並要求使用者重新接受時呈現。 它們可讓系統管理員傳達佈建，而使用者必須同意才能將裝置註冊到 Intune。

|    屬性        |    說明    |    範例        |
|----------------------------------|-----------------------------------------------------------------------------------------------|-----------------------------------------------------------|
|    termsAndConditionsKey    |    與 ‘userTermsAndConditionsAcceptances’ 集合中之項目對應的索引鍵    |    123    |
|    termsAndCondidionsId    |    此 termsAndConditions 項目的識別碼    |    276edcb7-7440-4339-b6c5-8b6fc556fee6    |
|    termsAndConditionsVersion    |    此條款及條件項目的版本    |    1    |
|    名稱    |    此 termsAndConditions 項目的名稱。        |    Intune 使用規定     |
|    描述    |    這些條款及條件的描述。     |         |
|    title    |    這些條款及條件的標題。     |    裝置管理公司原則        |
|    summaryOfTerms    |    提供給使用者的條款摘要。     |    我同意這些條款及條件。    |
|    termsAndConditionsBodyText    |    這些條款及條件的內文。       |    「裝置加密」強制使用 6 位數 PIN    |
|    isDeleted    |    指出是否已刪除此值的 True 或 False 值。     |    False    |
|    startDateInclusiveUTC    |    這些條款及條件的開始日期。     |    8/23/2018 4:01:34 AM    |
|    endDateEclusiveUTC    |    這些條款及條件的結束日期。     |    12/31/9999 12:00:00 AM    |

## <a name="userdeviceassociations"></a>userDeviceAssociations
**UserDeviceAssociation** 實體包含您組織中的使用者裝置關聯。

|        名稱        |                                             說明                                            |     範例     |
|:------------------:|:--------------------------------------------------------------------------------------------------:|:---------------:|
| UserKey            | 資料倉儲中使用者的唯一識別碼。   (Surrogate 索引鍵)。                            | 123             |
| DeviceKey          | 資料倉儲中裝置的唯一識別碼。                                             | 123             |
| CreatedDateTimeUTC | 建立使用者裝置關聯的日期和時間。 使用 UTC 格式。                     | 11/23/2016 0:00 |
| IsDeleted          | 指出使用者已取消註冊該裝置，且目前已沒有該關聯。 | True/False      |
| EndedDateTimeUTC   | IsDeleted 變更為 True 的 UTC 日期和時間。                                               | 6/23/2017 0:00  |

## <a name="users"></a>使用者
**user** 實體會列出您的企業中具有所指派授權的所有 Azure Active Directory (Azure AD) 使用者。

**user** 實體集合會包含使用者資料。 這些資料列包含資料收集期間的使用者狀態，即使使用者已經被移除。 例如，某個使用者可能在上個月內被新增到 Intune 然後又被移除。 雖然此使用者在報告期間並不存在，但使用者和狀態仍會存在於上個月的資料中。 您可以建立一個報告，其中顯示使用者的歷程記錄在您資料中出現的期間。

|          屬性          |                                                                                                           說明                                                                                                          |                範例               |
|:--------------------------:|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|:------------------------------------:|
| UserKey                    | 資料倉儲中使用者的唯一識別碼 - Surrogate 索引鍵。                                                                                                                                                         | 123                                  |
| UserId                     | 使用者的唯一識別碼 - 與 UserKey 類似，但為自然索引鍵。                                                                                                                                                    | b66bc706-ffff-7437-0340-032819502773 |
| UserEmail                  | 使用者的電子郵件地址。                                                                                                                                                                                                     | John@constoso.com                    |
| UPN                        | 使用者的使用者主體名稱。                                                                                                                                                                                               | John@constoso.com                    |
| DisplayName                | 使用者的顯示名稱。                                                                                                                                                                                                      | John                                 |
| IntuneLicensed             | 指定這位使用者是否獲授權使用 Intune。                                                                                                                                                                              | True/False                           |
| IsDeleted                  | 指出所有使用者的授權是否都已經過期，以及使用者是否因此而自 Intune 中被移除。 針對單一記錄，此旗標不會變更。 相反地，系統會針對新的使用者狀態建立新的記錄。 | True/False                           |
| RowLastModifiedDateTimeUTC | 在資料倉儲中最後一次修改記錄的 UTC 日期和時間                                                                                                                                                 | 11/23/2016 0:00                      |

## <a name="usertermsandconditionsacceptances"></a>userTermsAndConditionsAcceptances
**userTermsAndConditionsAcceptance** 實體表示指定使用者對指定條款及條件 (T&C) 原則的接受狀態。 使用者必須接受最新版本的條款，才能繼續存取公司入口網站。

|    屬性    |    說明    |    範例    |
|-------------------------------|--------------------------------------------------------------------------------|----------------------------|
|    dateKey    |    與 ‘dates’ 集合中之日期值對應的索引鍵。     |    20180823    |
|    userKey    |    與 ‘users’ 集合中之使用者對應的使用者索引鍵。     |    20000    |
|    termsAndConditionsKey    |    與 ‘termsAndConditions’ 集合中之項目對應的索引鍵    |    1    |
|    acceptedDateTimeUTC    |    使用者接受這些條款及條件的時間    |    8/23/2018 4:01:34 AM    |
|    lastModifiedDateTimeUTC    |    最後一次修改此項目的時間。     |    8/23/2018 4:01:34 AM    |

## <a name="vppprogramtypes"></a>vppProgramTypes 
**vppProgramType** 實體會列出應用程式可能的 VPP 方案類型。

|      屬性      |          說明         |
|:------------------:|:----------------------------:|
| VppProgramTypeID   | 類型的識別碼。           |
| VppProgramTypeKey  | 索引鍵的 Surrogate 索引鍵。 |
| VppProgramTypeName | VPP 方案類型。          |

### <a name="example"></a>範例

|             VppProgramID             |         名稱        | 說明                |
|:------------------------------------:|:-------------------:|----------------------------|
| 3DDA2474-470B-4503-9830-2665C21C1945 | Microsoft           | Microsoft 的 VPP 方案。 |
| 00000000-0000-0000-0000-000000000000 | 尚未提供 | 預設值，無 VPP。   |
| B54814E0-68EA-4BA4-8088-B5AAB58E737B | Apple               | Apple 的 VPP 方案。     |

## <a name="next-steps"></a>接下來的步驟

如需 Intune 資料倉儲的詳細資訊，請參閱[資料倉儲資料模型](https://docs.microsoft.com/intune/reports-ref-data-model)。


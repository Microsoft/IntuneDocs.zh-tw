---
title: 裝置 - Intune 資料倉儲
titlesuffix: Microsoft Intune
description: Intune 資料倉儲 API 中的實體集合裝置類別的參考主題。
keywords: Intune 資料倉儲
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/14/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 6955E12D-70D7-4802-AE3B-8B276F01FA4F
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 185cf1061ff4d577fd14af59bbe5fbc38365c3d1
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="reference-for-devices-entities"></a>裝置實體的參考

[裝置] 類別包含的行動裝置實體，可追蹤下列資訊：

  -  裝置類型
  -  裝置註冊和註冊狀態
  -  裝置擁有權
  -  裝置管理狀態
  -  Azure AD 裝置成員資格的狀態
  -  註冊狀態
  -  裝置的歷程資訊
  -  裝置上的應用程式清查

## <a name="devicetypes"></a>DeviceTypes

**DeviceTypes** 實體代表其他資料倉儲實體所參考的裝置類型。 裝置類型通常會描述裝置型號、製造商或兩者的組合。

| 屬性  | 說明 |
|---------|------------|
| DeviceTypeID |裝置類別的唯一識別碼 |
| DeviceTypeKey |資料倉儲中裝置類型的唯一識別碼 - surrogate 索引鍵 |
| DeviceTypeName |裝置類型 |

## <a name="example"></a>範例

| deviceTypeID  | 名稱 | 說明 |
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
| 15 |HoloLens |Holo Lens 裝置 |
| 16 |SurfaceHub |Surface Hub 裝置 |
| 17 |AndroidForWork |使用 Android for Work 設定檔擁有者的受管理 Android 裝置 |
| 100 |Blackberry |Blackberry 裝置 |
| 101 |Palm |掌上型裝置 |
| 255 |Unknown |未知的裝置類型 |

## <a name="clientregistrationstatetypes"></a>ClientRegistrationStateTypes

**ClientRegistrationStateTypes** 實體代表其他資料倉儲資料表所參考的註冊類型。

| 屬性  | 說明 |
|---------|------------|
| clientRegisterationStateID |註冊狀態的唯一識別碼 |
| clientRegisterationStateKey |資料倉儲中註冊狀態的唯一識別碼 - surrogate 索引鍵 |
| clientRegisterationStateName |註冊狀態 |

## <a name="example"></a>範例

| ClientRegisterationStateID  | 名稱 | 說明 |
|---------|------------|--------|
| 0 |NotRegistered |未註冊 |
| 1 |SMSIDConflict |SMS 識別碼衝突 |
| 2 |已登錄 |已登錄 |
| 3 |Revoked |此狀態表示 IT 系統管理員已封鎖用戶端，而且用戶端可被解除封鎖。 裝置在抹除或淘汰之後，也會是 Revoked 狀態。 |
| 4 |KeyConflict |索引碼衝突 |
| 5 |ApprovalPending |擱置核准 |
| 6 |ResetCert |重設憑證 |
| 7 |NotRegisteredPendingEnrollment |未註冊、擱置註冊 |
| 8 |Unknown |未知的狀態 |

## <a name="enrollmenttypes"></a>EnrollmentTypes

**EnrollmentTypes** 實體會指出裝置的註冊方式。 註冊類型會擷取註冊的方法。 範例會列出不同的註冊類型及其代表的意義。

| 屬性  | 說明 |
|---------|------------|
| managementStateID |管理狀態的唯一識別碼。 |
| managementStateKey |資料倉儲中管理狀態的唯一識別碼 - surrogate 索引鍵 |
| managementStateName |指出套用到此裝置的遠端動作狀態。 |

## <a name="example"></a>範例

| enrollmentTypeID  | 名稱 | 說明 |
|---------|------------|--------|
| 0 |Unknown |未收集註冊類型 |
| 1 |UserEnrollment |起始註冊的使用者 |
| 2 |DeviceEnrollment |以無使用者設定檔註冊的裝置 |
| 3 |DeviceEnrollmentWithUDA |以 UDA 設定檔註冊的裝置。 |
| 4 |AzureDomainJoined |使用者透過 Azure Active Directory 起始註冊的裝置 |
| 5 |UserEnrollmentWithServiceAccount |使用者透過服務帳戶起始的註冊 |
| 6 |DepDeviceEnrollment |以無使用者設定檔註冊的 DEP 裝置 |
| 7 |DepDeviceEnrollmentWithUDA |以 UDA 設定檔註冊的 DEP 裝置 |
| 8 |AutoEnrollment |結合 DRS 與 MDM 註冊的 BYOD 案例 |

## <a name="ownertypes"></a>OwnerTypes

**EnrollmentTypes** 實體會指出裝置為公司所有、個人擁有或未知。

| 屬性  | 說明 | 範例 |
|---------|------------|--------|
| ownerTypeID |擁有者類型的唯一識別碼。 | |
| ownerTypeKey |資料倉儲中擁有者類型的唯一識別碼 - Surrogate 索引鍵。 | |
| ownerTypeName |表示裝置的擁有者類型：  <br>公司 - 裝置為企業所有。 <br>個人 - 裝置為個人所有 (BYOD)。  <br>未知 - 無此裝置的相關資訊。 |公司個人未知 |

## <a name="mdmstatuses"></a>MdmStatuses

**MdmStatuses** 實體會指出裝置的合規性狀態。

| 屬性  | 說明 |
|---------|------------|
| MdmStatusID |合規性狀態的唯一識別碼 |
| MdmStatusKey |資料倉儲中合規性狀態的唯一識別碼 - surrogate 索引鍵 | 
| ComplianceStatus |裝置的合規性狀態，必須具有來自下表的其中一個值 | 


## <a name="example"></a>範例

| MdmStatusID  | ComplianceStatus | 說明 |
|---------|------------|--------|
| 0 |Unknown |裝置的合規性狀態不明。 |
| 1 |符合標準 |裝置符合規範。 |
| 2 |不符合標準 |裝置不相容。 |
| 3 |衝突 |裝置的合規性導致衝突。 |
| 4 |錯誤 |讀取裝置的合規性狀態時發生錯誤。 |


## <a name="managementstates"></a>ManagementStates

**ManagementStates** 實體會提供裝置狀態的詳細資訊。 在套用遠端動作的情況下，裝置如進行 JB 破解或刷機，詳細資料會很有幫助。

| 屬性  | 說明 |
|---------|------------|
| managementStateID | 管理狀態的唯一識別碼。 |
| managementStateKey | 資料倉儲中管理狀態的唯一識別碼 - surrogate 索引鍵 |
| managementStateName | 指出套用到此裝置的遠端動作狀態。 |

## <a name="example"></a>範例

| managementStateID  | 名稱 | 說明 |
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

## <a name="workplacejoinstatetypes"></a>WorkPlaceJoinStateTypes

**WorkPlaceJoinStateTypes** 實體代表裝置的 Azure Active Directory Workplace Join 狀態。  註冊工作流程可以使用一或多個憑證進行確認或驗證。 註冊裝置工作場所時，會使用這些憑證來驗證裝置與使用者。 憑證簽發是透過 SCEP (簡單憑證註冊點) 伺服器提供。 實體中的值會指出裝置在經歷此程序時，可能有的各種狀態。 這些狀態中，有些包括因簽發必要憑證 (來自 SCEP 伺服器) 失敗導致 WorkPlace Join 失敗。 如果裝置從未完成此工作流程，則值會設為 [未知]。

| 屬性  | 說明 |
|---------|------------|
| WorkPlaceJoinStateID | 工作場所加入狀態的唯一識別碼 |
| WorkPlaceJoinStateKey | 資料倉儲中工作場所加入狀態的唯一識別碼 - surrogate 索引鍵 |
| WorkPlaceJoinStateName | 工作場所加入狀態 |

## <a name="example"></a>範例

| workPlaceJoinStateID  | 名稱 | 說明 |
|---------|------------|--------|
| 0 |Unknown |如果裝置沒有加入工作場所，即處於未知狀態 |
| 1 |已成功 |成功加入工作場所 |
| 2 |FailureToGetScepMetadata |無法取得 SCEP 中繼資料 |
| 3 |FailureToGetScepChallenge |無法取得 SCEP 查問 |
| 4 |DeviceFailureToInstallScepCommand |無法在裝置上安裝 SCEP 命令 |
| 5 |DeviceFailureToGetCertificate |裝置無法透過 SCEP 取得憑證 |
| 6 |DeviceScepPending |擱置狀態，裝置仍在執行 SCEP |
| 7 |DeviceScepFailed |裝置無法透過 SCEP 安裝憑證 |
| 8 |AADValidationFailed |無法驗證裝置是否存在於 AAD |

## <a name="managementagenttypes"></a>ManagementAgentTypes

**ManagementAgentTypes** 實體代表管理裝置的代理程式。

| 屬性  | 說明 |
|---------|------------|
| ManagementAgentTypeID | 管理代理程式類型的唯一識別碼。 |
| ManagementAgentTypeKey | 資料倉儲中管理代理程式類型的唯一識別碼 - Surrogate 索引鍵。 |
| ManagementAgentTypeName |指出使用何種代理程式管理裝置。 |

## <a name="example"></a>範例

| ManagementAgentTypeID  | 名稱 | 說明 |
|---------|------------|--------|
| 1 |EAS | 透過 Exchange Active Sync 管理的裝置 |
| 2 |MDM | 使用 MDM 代理程式管理的裝置 |
| 3 |EasMdm | 由 Exchange Active Sync 和 MDM 代理程式管理的裝置 |
| 4 |IntuneClient | Intune 電腦代理程式管理的裝置 |
| 5 |EasIntuneClient | 由 Exchange Active Sync 與 Intune 電腦代理程式管理的裝置 |
| 8 |ConfigManagerClient | 由 System Center Configuration Manager 代理程式管理的裝置 |
| 16 |Unknown | 未知的管理代理程式類型 |

## <a name="devices"></a>裝置

**Devices** 實體會列出管理下的所有已註冊裝置及其對應的屬性。

| 屬性  | 說明 |
|---------|------------|
| DeviceKey | 資料倉儲中裝置的唯一識別碼 - surrogate 索引鍵 |
| DeviceId | 裝置的唯一識別碼。 |
| DeviceName | 允許命名裝置之平台上的裝置名稱。 在其他平台上，Intune 會從其他屬性建立名稱。 此屬性不能提供所有裝置使用。 |
| DeviceTypeKey | 此裝置的裝置類型屬性索引鍵。 |
| ClientRegisterationStateKey | 此裝置的用戶端註冊狀態屬性索引鍵。 |
| OwnerTypeKey | 此裝置的擁有者類型屬性索引鍵：公司、個人或未知。 |
| objectSourceKey | 略過這個資料行。 |
| CreatedDate | 裝置的註冊日期。 |
| LastContact | 使用 Intune 簽入的最後一部已知裝置。 |
| LastContactNotification | 上次 Intune 通知使用 Intune 簽入裝置的時間。 |
| LastContactWorkplaceJoin | 時間戳記，指出此裝置最後已知的 Workplace Join 狀態。 |
| ManagementAgentKey | 與此裝置相關聯的管理代理程式索引鍵。 |
| ManagementStateKey | 與此裝置相關聯的管理狀態索引鍵，指出遠端動作的最新狀態，或是否已 JB 破解或刷機。 |
| ReferenceId | Azure Active Directory 中的裝置識別碼。 |
| WorkPlaceJoinStateKey | 與此裝置相關聯的 Workplace Join 狀態索引鍵。 |
| CategoryId | 略過這個資料行。 |
| EnrollmentTypeKey | 與此裝置相關聯的註冊類型索引鍵，指出註冊方法。 |
| CertExpirationDate | MDM 管理憑證的到期日。 |
| MdmStatusKey | MdmStatus 的索引鍵。 |
| OSFamily | 作業系統系列 (Windows、iOS、Android 等等) |
| OSVersion | OS 版本 |
| OSMajorVersion | 作業系統版本的主要版本元件 (major.minor.build.revision)。 |
| OSMinorVersion | 作業系統版本的次要版本元件 (major.minor.build.revision)。 |
| OSBuildNumber | 作業系統版本的組建版本元件 (major.minor.build.revision)。 |
| OSRevisionNumber | 作業系統版本的修訂版本元件 (major.minor.build.revision)。 |
| EasID | 此裝置的 EAS 識別碼，如果裝置受 Exchange Active Sync 管理。 |
| GraphDeviceIsManaged | Intune 在 Azure AD 中設定的最後一個管理狀態。 |
| GraphDeviceIsCompliant | Intune 在 Azure AD 中設定的最後一個合規性狀態。 |
| SerialNumber | 裝置的序號 (如有)。 |
| EnrolledByUser | 註冊此裝置的使用者識別碼，參考使用者資料表中的 userId 資料行。 |
| RowLastModifiedDateTimeUTC | 上次修改此記錄的時間。 |
| ProcessorArchitecture | 處理器架構。 |
| DeviceAction | 最後發出的裝置動作，現在略過。 |
| 製造商 | 裝置製造商。 |
| 型號 | 裝置的型號。 |
| LastPolicyUpdateUtc | 裝置上更新原則的最新時間。 |
| LastExchangeStatusUtc | 裝置上次與 Exchange 同步處理的時間。 |
| IsDeleted | 如果裝置不再繼續受 Intune 管理，即設為 True。 會保留最後的已知狀態。 |

## <a name="devicepropertyhistory"></a>DevicePropertyHistory

**DevicePropertyHistory** 實體與裝置資料表和每部裝置過去 90 天內每天記錄的每日快照集有相同的內容。 DateKey 資料行會指出每個資料列的日期。

| 屬性  | 說明 |
|---------|------------|
| DateKey |指出當日的日期資料表參考。 |
| DeviceKey |資料倉儲中裝置的唯一識別碼 - surrogate 索引鍵 這是包含 Intune 裝置識別碼之裝置資料表的參考。 |
| DeviceName |允許命名裝置之平台上的裝置名稱。 在其他平台上，Intune 會從其他屬性建立名稱。 此屬性不能提供所有裝置使用。 |
| DeviceTypeKey |此裝置的裝置類型屬性索引鍵。 |
| ClientRegisterationStateKey |此裝置的用戶端註冊狀態屬性索引鍵。 |
| OwnerTypeKey |此裝置的擁有者類型屬性索引鍵：公司、個人或未知。 |
| objectSourceKey |略過這個資料行。 |
| CreatedDate |裝置的註冊日期。 |
| LastContact |使用 Intune 簽入的最後一部已知裝置。 |
| LastContactNotification |上次 Intune 通知使用 Intune 簽入裝置的時間。 |
| LastContactWorkplaceJoin |時間戳記，指出此裝置最後已知的 Workplace Join 狀態。 |
| ManagementAgentKey |與此裝置相關聯的管理代理程式索引鍵。 |
| ManagementStateKey |與此裝置相關聯的管理狀態索引鍵，指出遠端動作的最新狀態，或是否已 JB 破解或刷機。 |
| ReferenceId |Azure Active Directory 中的裝置識別碼。 |
| WorkPlaceJoinStateKey |與此裝置相關聯的 Workplace Join 狀態索引鍵。 |
| CategoryId |略過這個資料行。 |
| EnrollmentTypeKey |與此裝置相關聯的註冊類型索引鍵，指出註冊方法。 |
| CertExpirationDate |MDM 管理憑證的到期日。 |
| MdmStatusKey |MdmStatus 的索引鍵。 |
| OSFamily |作業系統系列 (Windows、iOS、Android 等等) |
| OSVersion |作業系統版本。 |
| OSMajorVersion |作業系統版本的主要版本元件 (major.minor.build.revision)。 |
| OSMinorVersion |作業系統版本的次要版本元件 (major.minor.build.revision)。 |
| OSBuildNumber |作業系統版本的組建版本元件 (major.minor.build.revision)。 |
| OSRevisionNumber |作業系統版本的修訂版本元件 (major.minor.build.revision)。 |
| EasID |此裝置的 EAS 識別碼，如果裝置受 Exchange Active Sync 管理。 |
| GraphDeviceIsManaged |Intune 在 Azure AD 中設定的最後一個管理狀態。 |
| GraphDeviceIsCompliant |Intune 在 Azure AD 中設定的最後一個合規性狀態。 |
| SerialNumber |裝置的序號 (如有)。 |
| EnrolledByUser |註冊此裝置的使用者識別碼，參考使用者資料表中的 userId 資料行。 |
| RowLastModifiedDateTimeUTC |上次修改此記錄的時間。 |
| ProcessorArchitecture |處理器架構。 |
| DeviceAction |最後發出的裝置動作，現在略過。 |
| 製造商 |裝置製造商。 |
| 型號 |裝置的型號。 |
| LastPolicyUpdateUtc |裝置上更新原則的最新時間。 |
| LastExchangeStatusUtc |裝置上次與 Exchange 同步處理的時間。 |

## <a name="mdmdeviceinventoryhistories"></a>MdmDeviceInventoryHistories

**MdmDeviceInventoryHistories** 實體包含過去 90 天內 MDM 管理裝置的清查資料每日快照集。 DateKey 資料行指出資料列是哪一天。 部分屬性可能不適合或無法填入所有裝置，詳細資料請參閱此頁面。 如需詳細資訊，請參閱[在 Microsoft Intune 透過清查了解您的裝置](https://docs.microsoft.com/Intune-classic/deploy-use/understand-your-devices-with-inventory-in-microsoft-Intune)。

| 屬性  | 說明 |
|---------|------------|
| DateKey | 指出當日的日期資料表參考。 |
| DeviceKey |資料倉儲中裝置的唯一識別碼 - surrogate 索引鍵 這是包含 Intune 裝置識別碼之裝置資料表的參考。 |
| DeviceModel |裝置的型號。 |
| OS |裝置的作業系統。 |
| DeviceName |允許命名裝置之平台上的裝置名稱。 在其他平台上，Intune 會從其他屬性建立名稱。 此屬性不能提供所有裝置使用。 |
| SoftwareVersion |在大部分情況下，這是作業系統版本，與作業系統版本不同的 Apple 平台除外。 |
| Imei |IMEI 編號 |
| HardwareInventoryTimeUtc |裝置的第一次清查報告。 |
| InventoryModifiedTimeUtc |擷取此快照集時儲存的前次清查。 |
| InventoryReportingTimeUtc |此裝置前次收集的清查。 |
| ExchangeActiveSyncId |Exchange ActiveSync 裝置識別碼。 |
| ComputerSystemDescription |系統描述。 |
| ComputerSystemName |系統名稱。 |
| ComputerSystemManufacturer |系統製造商。 |
| ComputerSystemModel |系統型號。 |
| UserName |使用者名稱。 |
| OSType |作業系統類型。 |
| OSCaption |作業系統標題。 |
| OSName |作業系統名稱。 |
| OSManufacturer |作業系統製造商。 |
| OSProductSuite |作業系統產品套件。 |
| OSProductType |作業系統產品類型。 |
| 地區設定 |作業系統地區設定。 |
| PhysicalMemoryCapacity |實體記憶體容量 (位元組)。 |
| PhysicalMemoryRemovable |實體的卸除式記憶體 (位元組)。 |
| SystemEnclosureChassisTypesInnerText |定義此裝置的系統底座類型。 數字表示下列值：  <br>0 或空白 = 不明   <br>1 = 是桌上型電腦   <br>2 = 是膝上型電腦  <br>3 = 是工作站  <br>4 = 是企業伺服器  <br>100 = 是電話  <br>101 = 是平板電腦  <br>102/103 = 另一種不明類型的行動裝置 |
| SystemEnclosureModel |系統機殼型號。 |
| SystemEnclosureSerialNumber |系統機殼序號。 |
| NetworkAdapterConfigurationText |網路介面卡的設定文字。 |
| MacAddress |MAC 位址。 |
| SmsID |Intune 裝置識別碼。 |
| CertExpiry |MDM 管理憑證的到期日。 |
| DeviceClientAgentVersion |用戶端代理程式版本。 |
| DeviceClientID |裝置用戶端識別碼。 |
| SerialNumber |序號。 |
| DeviceManufacturer |裝置製造商。 |
| DMVersion |DM 版本。 |
| FirmwareVersion |韌體版本。 |
| HardwareVersion |硬體版本。 |
| PlatformType |平台類型。 |
| ProcessorLevel |處理器等級。 |
| ProcessorRevision |處理器修訂。 |
| 產品 |產品。 |
| ProductVersion |產品版本。 |
| OEM |原始設備製造商。 |
| DeviceBuildVersion |裝置組建版本。 |
| Meid |行動設備識別碼。 |
| PhoneNumber |電話號碼。 |
| SubscriberCarrierNetwork |行動電信業者網路名稱。 |
| CellularTechnology |行動電信業者網路類型 (CDMA/GSM)。 |
| Imsi |IMSI 編號。 |
| JB 破解 |如果裝置已 JB 破解或刷機，則為 True。 |
| IsActivationLockEnabled |已啟用 [True Is Activation Lock] (True 為啟用鎖定) |
| DeviceType |裝置類型 |
| IsSupervised |為受監督 |
| DeviceDisplayNumberOfColors |彩色的裝置顯示編號 |
| HorizontalResolution |裝置的水平螢幕解析度 |
| VerticalResolution |裝置的垂直螢幕解析度 |
| StorageFree |可用的儲存體 (位元組) |
| StorageTotal |總儲存體 (位元組) |
| ProgramFree |可用的程式記憶體 (位元組) |
| ProgramTotal |總程式記憶體 (位元組) |
| RemovableStorageFree |可用的抽取式存放裝置 (位元組) |
| RemovableStorageTotal |總抽取式存放裝置 (位元組) |
| DeviceMemoryDeviceCapacity |裝置記憶體容量 |
| DeviceMemoryAvailableDeviceCapacity |裝置記憶體可用容量 |
| DeviceOSVersion |作業系統版本 |
| DeviceOSPlatform |作業系統平台 |
| DeviceOSLanguage |作業系統語言 |
| PasswordMaxAttemptsBeforeWipe |抹除裝置前允許的密碼嘗試次數上限 |
| PasswordMinComplexChars |密碼所需複合字元數下限 |
| PasswordMinLength |密碼所需長度下限 |
| PasswordHistory |密碼 - 不被接受的歷史密碼下限 |
| PasswordEnabled |密碼 - 已啟用？ |
| PasswordExpiration |密碼 - 到期日。 |
| AllowRecoveryPassword |允許密碼復原。 |
| PasswordAutoLockTimeout |密碼 - 自動鎖定逾時。 |
| PasswordType |密碼類型。 |
| BacklightACTimeout |插入電源時的背光逾時。 |
| BacklightBatTimeout |使用電池時的背光逾時。 |
| PowerBackupPercent |電源備份百分比。 |
| BatteryPercent |剩餘的電池百分比。 |
| PlatformID |平台識別碼。 |
| ExchangeDeviceID |Exchange 裝置識別碼。 |
| SmsProcessorDescription |處理器描述。 |
| OwnerEmailAddress |擁有者的電子郵件地址。 |
| DeviceOSName |作業系統名稱。 |
| WifiMac |WIFI Mac 位址。 |
| EthernetMac |乙太網路 MAC 位址。 |
| RequireEncryption |指出裝置是否加密。 |
| ActivationLockBypassCode |啟用鎖定略過碼。 |

## <a name="applicationinventory"></a>ApplicationInventory

**ApplicationInventory** 實體會列出清查收集期間在裝置上找到的應用程式。


|      屬性      |                       說明                        |
|--------------------|----------------------------------------------------------|
|     DeviceKey      |              裝置資料表的參考。               |
|   ApplicationKey   | ? (從 ExchangeDeviceService\DeviceApplication 複製)。 |
|  ApplicationName   | ? (從 ExchangeDeviceService\DeviceApplication 複製)。 |
| ApplicationVersion | ? (從 ExchangeDeviceService\DeviceApplication 複製)。 |
|     BundleSize     | ? (從 ExchangeDeviceService\DeviceApplication 複製)。 |


---
title: 什麼是 Microsoft Intune 裝置註冊
titleSuffix: Microsoft Intune
description: 了解 iOS、Android 及 Windows 裝置註冊。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 4/24/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 6f67fcd2-5682-4f9c-8d74-d4ab69dc978c
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 304e869460a5396a486b6de0cd5c2f549c192b70
ms.sourcegitcommit: 60ed93682a21860e9d99ba1592ede120477f2b4d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72379856"
---
# <a name="what-is-device-enrollment"></a>什麼是裝置註冊？
[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Intune 可讓您管理員工的裝置與應用程式，以及員工存取公司資料的方式。 若要使用這項行動裝置管理 (MDM)，裝置必須先在 Intune 服務中註冊。 裝置會在註冊時收到 MDM 憑證。 這項憑證會用來與 Intune 服務通訊。

在下表中，您可以看到數種註冊員工裝置的方法。 每種方法皆會因裝置擁有權 (個人或公司)、裝置類型 (iOS、Windows、Android) 及管理需求 (重設、親和性、鎖定) 而有所不同。

依預設，所有平台的裝置都可以在 Intune 中註冊。 不過，您可以[依平台限制裝置](enrollment-restrictions-set.md#create-a-device-type-restriction)。

## <a name="ios-enrollment-methods"></a>iOS 註冊方法

| **方法** | **需要重設** | [**使用者親和性**](device-enrollment-program-enroll-ios.md#create-an-apple-enrollment-profile) | **鎖定** | **詳細資料** |
|:---:|:---:|:---:|:---:|:---:|
| | 裝置會在註冊期間抹除。 | 建立每部裝置與使用者的關聯。| 如果會，使用者就無法取消註冊裝置。 | |
|**[BYOD](#bring-your-own-device)** | 否| 是 | 否 | [詳細資訊](apple-mdm-push-certificate-get.md)|
|**[DEM](#device-enrollment-manager)**| 否 |否 |否 | [詳細資訊](device-enrollment-program-enroll-ios.md)|
|**[DEP](#apple-device-enrollment-program)**| 是 | 選用 | 選用|[詳細資訊](device-enrollment-program-enroll-ios.md)|
|**[USB-SA](#usb-sa)**| 是 | 選用 | 否| [詳細資訊](apple-configurator-enroll-ios.md)|
|**[USB-Direct](#usb-direct)**| 否 | 否 | 否|[詳細資訊](apple-configurator-enroll-ios.md)|

## <a name="macos-enrollment-methods"></a>macOS 註冊方法
| **方法** |  **需要重設** |  **使用者親和性** | **鎖定** | **詳細資料**|
|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#bring-your-own-device)** | 否| 是 | 否 | [詳細資訊](macos-enroll.md)|
|**[DEM](#device-enrollment-manager)**| 否 |否 |否  | [詳細資訊](device-enrollment-manager-enroll.md)|
|**[DEP](#apple-device-enrollment-program)**| 是 | 選用 | 選用|[詳細資訊](device-enrollment-program-enroll-macos.md)|

## <a name="windows-enrollment-methods"></a>Windows 註冊方法

| **方法** | **需要重設** | **使用者親和性** | **鎖定** | **詳細資料**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#bring-your-own-device)** | 否 | 是 | 否 | [詳細資訊](windows-enroll.md)|
|**[DEM](#device-enrollment-manager)**| 否 |否 |否 |[詳細資訊](device-enrollment-manager-enroll.md)|
|**自動註冊** | 否 |是 |否 | [詳細資訊](windows-enroll.md#enable-windows-10-automatic-enrollment)|
|**Autopilot** |是 |是 |否 | [詳細資訊](enrollment-autopilot.md)
|**大量註冊** |否 |否 |否 | [詳細資訊](windows-bulk-enroll.md) |
|**共同管理** |否 |是 |否 | [詳細資訊](https://docs.microsoft.com/sccm/core/clients/manage/co-management-overview)
|**GPO** |否 |是 |否 | [詳細資訊](https://docs.microsoft.com/windows/client-management/mdm/enroll-a-windows-10-device-automatically-using-group-policy)

## <a name="android-enrollment-methods"></a>Android 註冊方法

| **個人** | **註冊方法** | **需要重設** | **使用者親和性** | **鎖定** | **詳細資料**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**Android 裝置系統管理員**|**透過公司入口網站起始使用者** | 否 | 是 | 否 | [詳細資訊](https://docs.microsoft.com/intune-user-help/enroll-device-android-company-portal)|
|**Android Enterprise 工作設定檔**|**透過公司入口網站起始使用者**| 否 | 是 | 否 | [詳細資訊](android-work-profile-enroll.md)|


| **公司** | **註冊方法** | **需要重設** | **使用者親和性** | **鎖定** | **詳細資料**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**Android 裝置系統管理員**|**透過公司入口網站起始 [DEM](#device-enrollment-manager)**| 否 | 否 | 否 |[詳細資訊](device-enrollment-manager-enroll.md)|
|**Android 裝置系統管理員**|**透過公司入口網站起始 (預先宣告的 IMEI 或 SN) 使用者**| 否 | 是 | 否 | [詳細資訊](./../corporate-identifiers-add.md)|
|**使用 Zebra Mobility Extensions 的 Android 裝置系統管理員**|**透過公司入口網站起始使用者或 [DEM](#device-enrollment-manager)**| 否 | 如果起始使用者，則為是；如果起始 [DEM](#device-enrollment-manager)，則為否。 | 否 | [詳細資訊](../configuration/android-zebra-mx-overview.md)|
|**Android Enterprise 專用**|**NFC、權杖或 QR 代碼、零觸式**| 是 | 否 | 可透過政策設定 | [詳細資訊](android-kiosk-enroll.md)|
|**Android Enterprise 完全受控**|**NFC、權杖或 QR 代碼、零觸式**| 是 | 是 | 可透過原則設定 | [詳細資訊](android-dedicated-devices-fully-managed-enroll.md)|


## <a name="bring-your-own-device"></a>攜帶您自己的裝置
攜帶您自己的裝置 (BYOD) 包括個人擁有的手機、平板電腦及電腦。 使用者必須安裝並執行公司入口網站應用程式以註冊 BYOD。 此程式可讓使用者存取公司資源，例如電子郵件。

## <a name="corporate-owned-device"></a>公司擁有的裝置
[公司擁有的裝置 (COD)](corporate-identifiers-add.md) 包括手機、平板電腦及電腦，由組織擁有並分配給員工。 COD 註冊支援自動註冊、共用裝置或授權前註冊需求等案例。 常見的 COD 註冊方式是由系統管理員或主管使用裝置註冊管理員 (DEM)。 iOS 裝置可直接透過 Apple 提供的裝置註冊計劃 (DEP) 工具進行註冊。 具備 IMEI 編號的裝置也可被識別並標記為公司所擁有。

### <a name="device-enrollment-manager"></a>裝置註冊管理員
裝置註冊管理員 (DEM) 是特殊的使用者帳戶，可用於註冊及管理公司擁有的多部裝置。 管理員可以安裝公司入口網站，並註冊許多無使用者裝置。 比方說，這些類型的裝置適合銷售點或公用程式應用程式，但對於需要存取電子郵件或公司資源的使用者而言則不適合。 深入了解 [DEM](device-enrollment-manager-enroll.md)。

### <a name="apple-device-enrollment-program"></a>Apple 裝置註冊方案
Apple 裝置註冊計劃 (DEP) 管理功能可讓您「以無線方式」建立原則，並將原則部署至透過 DEP 購買及管理的 iOS 和 macOS 裝置。 當使用者第一次開啟裝置並執行「設定輔助程式」時，即會註冊裝置。 這種方法支援 iOS 受監督模式，接著會使用持定功能來設定裝置。

深入了解 iOS DEP 註冊：

- [選擇註冊 iOS 裝置的方式](ios-enroll.md)
- [使用裝置註冊方案註冊 iOS 裝置](device-enrollment-program-enroll-ios.md)

### <a name="usb-sa"></a>USB-SA
IT 管理員會透過 USB 使用 Apple Configurator，手動準備每部屬公司擁有的裝置，以使用「設定助理」進行註冊。 IT 系統管理員會建立註冊設定檔，並將其匯出至 Apple Configurator。 當使用者收到裝置時，系統接著會提示他們執行設定輔助程式來註冊裝置。 這種方法支援 **iOS 受監督**模式，其接著會啟用下列功能：
- 已鎖定註冊
- Kiosk 模式及其他進階設定與限制

深入了解如如何使用「設定助理」進行 iOS Apple Configurator 註冊：

- [決定 iOS 裝置的註方式](ios-enroll.md)
- [使用 Configurator 及設定助理註冊 iOS 裝置](apple-configurator-enroll-ios.md)

### <a name="usb-direct"></a>USB-Direct
若是 Direct Enrollment，系統管理員必須建立註冊原則並將其匯出至 Apple Configurator，以手動註冊每部裝置。 公司擁有的 USB 連接裝置可直接註冊，而不需抹除。 裝置會以無使用者裝置形式進行管理。 這些裝置不會遭到鎖定或監督，亦不支援條件式存取、越獄偵測或行動應用程式管理。

若要深入了解 iOS 註冊，請參閱︰

- [決定 iOS 裝置的註方式](ios-enroll.md)
- [使用 Configurator 及直接註冊來註冊 iOS 裝置](apple-configurator-enroll-ios.md)

## <a name="mobile-device-cleanup-after-mdm-certificate-expiration"></a>MDM 憑證到期後的行動裝置清除

當行動裝置與 Intune 服務通訊時，會自動更新 MDM 憑證。 若行動裝置遭到抹除，或有一段時間無法與 Intune 服務通訊，便無法更新 MDM 憑證。 當 MDM 憑證過期 180 天後，該裝置便會從 Azure 入口網站上移除。

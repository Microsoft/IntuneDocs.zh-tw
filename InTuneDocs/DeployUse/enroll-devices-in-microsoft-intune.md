---
title: "註冊裝置 | Microsoft Intune"
description: "行動裝置管理 (MDM) 會使用註冊來管理裝置，並允許其存取資源。"
keywords: 
author: NathBarn
manager: angrobe
ms.date: 09/15/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8fc415f7-0053-4aa5-8d2b-03202eca4b87
ms.reviewer: damionw
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: c880bd9dfb998355a18e78af898a96d4cee393f7
ms.openlocfilehash: 145d373edd65d7ba01c696c3b851692a13831dad


---

# 註冊裝置以在 Intune 中管理
您可以向 Microsoft Intune 註冊裝置 (包括 Windows 電腦)，以啟用行動裝置管理 (MDM)。 本主題說明在 Intune 管理中註冊行動裝置的不同方式。 註冊裝置的方式取決於裝置類型、擁有權和需要的管理層級。 「攜帶您自己的裝置」(BYOD) 註冊可讓使用者註冊其個人電話、平板電腦或電腦。 屬公司擁有的裝置 (CYOD) 註冊允許進行遠端抹除、共用裝置或裝置的使用者親和性等管理案例。

如果您使用內部部署或裝載於雲端的 [Exchange ActiveSync](#mobile-device-management-with-exchange-activesync-and-intune)，您可以進行不需要註冊的簡單 Intune 管理。 也可以使用 [Intune 用戶端軟體](#manage-windows-pcs-with-intune)來管理 Windows 電腦。

## 裝置註冊方法概觀

下表顯示 Intune 的註冊方法及其支援的功能。 這些功能包括：
- **抹除**：原廠重設裝置，並移除所有資料。 [淘汰裝置](retire-devices-from-microsoft-intune-management.md)
- **親和性**：將裝置與使用者相關聯。 行動應用程式管理 (MAM) 和公司資料的條件式存取需要此功能。 [使用者親和性](enroll-corporate-owned-ios-devices-in-microsoft-intune.md#using-company-portal-on-dep-or-apple-configurator-enrolled-devices)
- **鎖定**：防止使用者移除受管理的裝置。 iOS 裝置需要受監管模式才能進行鎖定。 [遠端鎖定](retire-devices-from-microsoft-intune-management.md#block-access-a-device)

**iOS 註冊方法**

| **方法** |  **抹除** |  **親和性**    |   **鎖定** | **詳細資料** |
|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#byod)** | 否|    是 |   否 | [其他資訊](prerequisites-for-enrollment.md#set-up-device-management)|
|**[DEM](#dem)**|   否 |否 |否  | [其他資訊](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md)|
|**[DEP](#dep)**|   是 |   選用 |  選用|[其他資訊](ios-device-enrollment-program-in-microsoft-intune.md)|
|**[USB-SA](#usb-sa)**| 是 |   選用 |  否| [其他資訊](ios-setup-assistant-enrollment-in-microsoft-intune.md)|
|**[USB-Direct](#usb-direct)**| 否 |    否  | 否|[其他資訊](ios-direct-enrollment-in-microsoft-intune.md)|

**Windows 註冊方法**

| **方法** |  **抹除** |  **親和性**    |   **鎖定** | **詳細資料**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#byod)** | 是|   是 |   否 | [其他資訊](prerequisites-for-enrollment.md#set-up-device-management)|
|**[DEM](#dem)**|   否 |否 |否  |[其他資訊](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md)|

**Android 註冊方法**

| **方法** |  **抹除** |  **親和性**    |   **鎖定** | **詳細資料**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#byod)** | 否|    是 |   否 | [其他資訊](prerequisites-for-enrollment.md#set-up-device-management)|
|**[DEM](#dem)**|   否 |否 |否  |[其他資訊](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md)|

如需協助您找到正確方法的一連串問題，請參閱[選擇如何註冊裝置](/intune/get-started/choose-how-to-enroll-devices1)。

## BYOD
「攜帶您自己的裝置」使用者會安裝公司入口網站應用程式，並註冊其裝置。 這可以讓使用者連線到公司網路，並加入網域或 Azure Active Directory。 啟用 BYOD 註冊是進行大多數平台之許多 COD 案例的必要條件。 請參閱[裝置註冊的必要條件](prerequisites-for-enrollment.md)。 ([返回表格](#overview-of-device-enrollment-methods))

## 屬公司擁有的裝置
可使用 Intune 主控台管理公司擁有的裝置 (CYOD)。 可直接透過 Apple 提供的工具註冊 iOS 裝置。 系統管理員或管理員可使用裝置註冊管理員來註冊所有裝置類型。 也可以將包含 IMEI 號碼的裝置識別和標記為公司擁有，以啟用 COD 案例。

[註冊公司擁有的裝置](manage-corporate-owned-devices.md)

### DEM
裝置註冊管理員是特殊的 Intune 帳戶，可用來註冊及管理多部屬公司擁有的裝置。 管理員可以安裝公司入口網站，並註冊許多無使用者裝置。 深入了解 [DEM](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md)。 ([返回表格](#overview-of-device-enrollment-methods))

### DEP
Apple 裝置註冊方案 (DEP) 管理可讓您「以無線方式」建立原則，並將原則部署至透過 DEP 購買及管理的 iOS 裝置。 當使用者第一次開啟裝置並執行 iOS Setup Assistant 時，會註冊裝置。 這種方法支援 [iOS 受監督] (iOS Supervised) 模式，其接著會啟用：
  - 已鎖定註冊
  - 條件式存取
  - 破解偵測
  - 行動應用程式管理

深入了解 [DEP](ios-device-enrollment-program-in-microsoft-intune.md)。 ([返回表格](#overview-of-device-enrollment-methods))

### USB-SA
USB 連接的 Setup Assistant 註冊。 系統管理員會建立 Intune 原則，並將它匯出至 Apple Configurator。 屬公司擁有的 USB 連接裝置是使用 Intune 原則所準備。 系統管理員必須手動註冊每個裝置。 使用者會接收其裝置，並且執行 Setup Assistant 以註冊其裝置。 這種方法支援 [iOS 受監督] (iOS Supervised) 模式，其接著會啟用：
  - 條件式存取
  - 破解偵測
  - 行動應用程式管理

深入了解 [使用 Apple Configurator 進行 Setup Assistant 註冊](ios-setup-assistant-enrollment-in-microsoft-intune.md)。 ([返回表格](#overview-of-device-enrollment-methods))

### USB-Direct
直接註冊。 系統管理員會建立 Intune 原則，並將它匯出至 Apple Configurator。 屬公司擁有的 USB 連接裝置可直接註冊，不需要重設成出廠預設值。 系統管理員必須手動註冊每個裝置。 裝置會以無使用者裝置形式進行管理。 它們未鎖定或未受監督，並且不支援條件式存取、破解偵測和行動應用程式管理。 深入了解[使用 Apple Configurator 直接註冊](ios-direct-enrollment-in-microsoft-intune.md)。 ([返回表格](#overview-of-device-enrollment-methods))

## 使用 Exchange ActiveSync 和 Intune 的行動裝置管理
Intune 可使用 EAS MDM 原則來管理未註冊、但連線到 Exchange ActiveSync (EAS) 的行動裝置。 Intune 會使用 Exchange Connector 與內部部署和雲端託管的 EAS 通訊。

[使用 Exchange ActiveSync 和 Intune 的行動裝置管理](mobile-device-management-with-exchange-activesync-and-microsoft-intune.md)


## 使用 Intune 管理 Windows 電腦  
您也可以透過 Intune 用戶端軟體，使用 Microsoft Intune 來管理 Windows 電腦。 使用 Intune 用戶端管理的電腦可以︰

 - 報告軟體和硬體清查
 - 安裝桌面應用程式 (例如 .exe 和 .msi 檔案)
 - 防火牆設定

使用 Intune 用戶端軟體管理的電腦無法抹除，而且無法利用許多 Intune 管理功能，例如條件式存取、VPN 和 Wi-Fi 設定，或憑證和電子郵件組態部署。

[使用 Intune 管理 Windows 電腦](manage-windows-pcs-with-microsoft-intune.md)

##  支援的裝置平台

Intune 可以管理下列裝置平台︰

[!INCLUDE[mdm-supported-devices](../includes/mdm-supported-devices.md)]

## 後續步驟
- [裝置註冊的必要條件](prerequisites-for-enrollment.md)
- [管理公司擁有的裝置](manage-corporate-owned-devices.md)
- [支援的行動裝置和電腦](../get-started/supported-mobile-devices-and-computers.md)



<!--HONumber=Sep16_HO4-->



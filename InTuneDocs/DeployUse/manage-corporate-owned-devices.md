---
# required metadata

title: 管理公司裝置 | Microsoft Intune
description:
keywords:
author: NathBarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 2b60bbff-25e6-489b-9621-c71b4275fa06

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# 使用 Microsoft Intune 註冊公司擁有的裝置
根據裝置、購買方式和組織需求，Intune 可以透過各種不同的方式管理組織或公司所擁有的裝置 (COD)。

## 公司擁有的 iOS 裝置
這些註冊方法適合「選擇您自己的裝置」(CYOD) 案例，其中組織會為使用者購買裝置，但想要保有對裝置的管理。 如果您的組織有購買的 iOS 裝置，您可以預先設定註冊，使得裝置在使用者第一次開啟裝置時即受到管理。 Intune 支援透過 [Apple 的裝置註冊程式 (DEP)](ios-device-enrollment-program-in-microsoft-intune.md) 註冊或使用 Mac 電腦上執行的 Apple Configurator 進行[直接](ios-direct-enrollment-in-microsoft-intune.md)或[設定助理](ios-setup-assistant-enrollment-in-microsoft-intune.md)註冊。

[註冊公司擁有的 iOS 裝置](enroll-corporate-owned-ios-devices-in-microsoft-intune.md)

## 裝置註冊管理員
組織可以使用 Intune，透過稱為裝置註冊管理員帳戶的單一使用者帳戶來管理大量的行動裝置。 建立裝置註冊管理員帳戶後，管理員可以使用該帳戶來註冊多於對一般使用者預設允許的標準五個裝置。 使用裝置註冊管理員來註冊裝置僅適用於特定使用者未使用的裝置。 比方說，這些裝置都適合銷售點或公用程式應用程式，但對於需要電子郵件或公司資源的存取權的使用者而言則不適合。

[使用裝置註冊管理員註冊公司所擁有的裝置](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md)

## 國際行動設備識別 (IMEI)
唯一的國際行動設備識別碼 (IMEI) 號碼是許多行動裝置製造商的通用裝置屬性。 Intune 系統管理員可以匯入公司擁有之裝置的 IMEI 號碼。 當裝置變成由 Intune 管理時，可以將它標記為公司擁有的裝置，並使用適當的原則為目標。

[使用國際行動設備識別碼 (IMEI) 號碼來指定公司擁有的裝置](specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers)

## 公司裝置註冊方法概觀

下表顯示公司裝置的註冊方法與其優點。

**iOS 註冊方法**

| **方法** |  **[重設](#Reset)** |   **[親和性](#Affinity)**   |   **[Locked](#Locked)** |
|:---:|:---:|:---:|:---:|
|**[BYOD](#BYOD)** | 否|    是 |   否 |
|**[DEM](#DEM)**|   否 |否 |否  |
|**[DEP](#DEP)**|   是 |   Opt |   Opt|
|**[USB-SA](#USB-SA)**| 是 |   Opt |   否|
|**[USB-Direct](#USB-Direct)**| 否 |    否  | 否|

**Windows 和 Android 註冊方法**

| **方法** |  **[抹除](#Wipe)** | **[使用者](#User)**   |   **[Locked](#Locked)** |
|:---:|:---:|:---:|:---:|
|**[BYOD](#BYOD)** | 否|    是 |   否 |
|**[DEM](#DEM)**|   否 |否 |否  |

**公司裝置的註冊方法**

### BYOD
「攜帶您自己的裝置。」 使用者安裝公司入口網站應用程式，並註冊其裝置。 使用公司入口網站註冊裝置，將工作場所加入裝置。 需要有 Apple ID，才能使用公司入口網站註冊 iOS 裝置。 BYOD 不需要額外設定公司裝置。 請參閱[設定裝置管理](get-ready-to-enroll-devices-in-microsoft-intune#set-up-device-management.md)的步驟。 ([回到表格](#overview-of corporate-owned-device-enrollment-methods))

### DEM
裝置註冊管理員。 系統管理員會建立 DEM 帳戶。 管理員接著可以安裝公司入口網站，並註冊許多無使用者裝置。 深入了解 [DEM](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md)。 ([回到表格](#overview-of corporate-owned-device-enrollment-methods))

### DEP
Apple 裝置註冊方案。 系統管理員會建立原則，並將原則透過網路部署到使用 DEP 所購買和管理的 iOS 裝置。 使用者執行 iOS Setup Assistant 時，會註冊裝置。 這種方法支援 [iOS 受監督] (iOS Supervised) 模式，其接著會啟用：
  - 已鎖定註冊
  - 條件式存取
  - 破解偵測
  - 行動應用程式管理

深入了解 [DEP](ios-device-enrollment-program-in-microsoft-intune.md)。 ([回到表格](#overview-of corporate-owned-device-enrollment-methods))

### USB-SA
USB 連接的 Setup Assistant 註冊。 系統管理員會建立 Intune 原則，並將它匯出至 Apple Configurator。 USB 連接的裝置是使用 Intune 原則所準備。 系統管理員必須手動註冊每個裝置。 使用者會接收其裝置，並且執行 Setup Assistant 以註冊其裝置。 這種方法支援 [iOS 受監督] (iOS Supervised) 模式，其接著會啟用：
  - 條件式存取
  - 破解偵測
  - 行動應用程式管理

深入了解 [使用 Apple Configurator 進行 Setup Assistant 註冊](ios-setup-assistant-enrollment-in-microsoft-intune.md)。 ([回到表格](#overview-of corporate-owned-device-enrollment-methods))

### USB-Direct
直接註冊。 系統管理員會建立 Intune 原則，並將它匯出至 Apple Configurator。 USB 連接的裝置可直接註冊，不需要重設成出廠預設值。 系統管理員必須手動註冊每個裝置。 裝置會以無使用者裝置形式進行管理。 它們未鎖定或未受監督，並且不支援條件式存取、破解偵測和行動應用程式管理。 深入了解[使用 Apple Configurator 直接註冊](ios-direct-enrollment-in-microsoft-intune.md)。 ([回到表格](#overview-of corporate-owned-device-enrollment-methods))

**公司行動裝置的行為**

### 重設
指定註冊裝置是否需要將裝置重設成出廠預設值、移除裝置中的所有資料，並將它回復為原始狀態。
([回到表格](#overview-of corporate-owned-device-enrollment-methods))

### 親和性
指定註冊方法是否支援將裝置與特定使用者連接的「使用者親和性」。 不論是否有使用者親和性，都可以註冊 “Opt” 裝置。 需要有使用者親和性，才能支援下項項目︰
  - 行動應用程式管理 (MAM) 應用程式
  - 對電子郵件和公司資料進行條件式存取
  - 公司入口網站應用程式

([回到表格](#overview-of corporate-owned-device-enrollment-methods))

### 鎖定
指定是否可以鎖定裝置以防止使用者移除 Intune 原則，以有效地移除裝置不進行管理。 針對 iOS 裝置，鎖定裝置時需要裝置處於受監督模式。
([回到表格](#overview-of corporate-owned-device-enrollment-methods)) ([回到表格](#overview-of corporate-owned-device-enrollment-methods))


<!--HONumber=Jun16_HO3-->



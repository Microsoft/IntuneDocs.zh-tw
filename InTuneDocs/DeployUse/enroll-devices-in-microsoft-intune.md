---
title: "註冊裝置 | Microsoft Intune"
description: "行動裝置管理 (MDM) 會使用註冊來管理裝置，並允許其存取資源。"
keywords: 
author: NathBarn
manager: angrobe
ms.date: 07/18/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8fc415f7-0053-4aa5-8d2b-03202eca4b87
ms.reviewer: damionw
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: a7a0f834df939432910e32e6e635a70f021b37a9
ms.openlocfilehash: 63405b43609eda515656ad397c5c7ff4253a8167


---

# 註冊裝置以在 Intune 中管理
Microsoft Intune 行動裝置管理 (MDM) 會使用註冊來管理裝置，並允許其存取資源。 註冊裝置的方式取決於裝置類型、擁有權和需要的管理層級。 「攜帶您自己的裝置」(BYOD) 和公司擁有的裝置 (CYOD) 案例都需要註冊程序。 不論使用 Exchange ActiveSync 的組織是在內部部署或雲端中託管，都可以進行較少的管理而不需要註冊。 也可以使用 Intune 用戶端軟體來管理 Windows 電腦。

請參閱[選擇如何註冊裝置](/intune/get-started/choose-how-to-enroll-devices1)以取得說明。

###  支援的裝置平台

Intune 可以管理下列裝置平台︰

[!INCLUDE[mdm-supported-devices](../includes/mdm-supported-devices.md)]

## 設定行動裝置管理授權單位
MDM 授權單位會定義有權管理一組裝置的管理服務。 MDM 授權單位選項包括單獨使用 Intune，以及具備 Intune 的 Configuration Manager。 如果您將 Configuration Manager 設定為管理授權單位，就不能使用其他服務管理行動裝置。

>[!IMPORTANT]
> 請仔細考慮要單獨使用 Intune (線上服務) 還是使用具備 Intune 的 System Center Configuration Manager (搭配線上服務的內部部署軟體解決方案) 來管理行動裝置。 設定行動裝置管理授權單位之後便無法再做變更。

1.  在 [Microsoft Intune 管理主控台](http://manage.microsoft.com)中，選擇 [系統管理] &gt; [行動裝置管理]。

2.  在 [工作]  清單中，按一下 [設定行動裝置管理授權單位] 。 [設定 MDM 授權單位]  對話方塊隨即開啟。

    ![[設定 MDM 授權單位] 對話方塊](../media/intune-mdm-authority.png)

3.  Intune 要求您確認是否要以 Intune 做為 MDM 授權單位。 選取核取方塊，然後選擇 [是] 以使用 Microsoft Intune 管理行動裝置。

## 設定 Intune 公司入口網站

Intune 公司入口網站是使用者存取公司資料並可以執行一般工作的位置，如註冊裝置、安裝應用程式，以及找到向 IT 尋求協助的資訊。

> [!TIP]
> 當您自訂公司入口網站時，這些組態會同時套用到公司入口網站和公司入口網站應用程式。

自訂公司入口網站可協助為終端使用者提供熟悉且實用的體驗。 若要這麼做，只要以租用戶或服務管理員身分登入 [Microsoft Intune 管理主控台](https://manage.microsoft.com)，並選擇 [系統管理] &gt; [公司入口網站]，然後進行公司入口網站設定。

![admin-console-admin-workspace-comp-portal-settings](../media/cp_sa_cpsetup.PNG)

## 裝置註冊方法概觀

下表顯示公司裝置的註冊方法與其優點。

**iOS 註冊方法**

| **方法** |  **[抹除](#Wipe)** | **[親和性](#Affinity)**   |   **[Locked](#Lock)** |
|:---:|:---:|:---:|:---:|
|**[BYOD](#BYOD)** | 否|    是 |   否 |
|**[DEM](#DEM)**|   否 |否 |否  |
|**[DEP](#DEP)**|   是 |   Opt |   Opt|
|**[USB-SA](#USB-SA)**| 是 |   Opt |   否|
|**[USB-Direct](#USB-Direct)**| 否 |    否  | 否|

**Windows 和 Android 註冊方法**

| **方法** |  **[抹除](#Wipe)** | **[親和性](#Affinity)**   |   **[Locked](#Lock)** |
|:---:|:---:|:---:|:---:|
|**[BYOD](#BYOD)** | 否|    是 |   否 |
|**[DEM](#DEM)**|   否 |否 |否  |

**裝置的註冊方法**

### BYOD
「攜帶您自己的裝置。」 使用者安裝公司入口網站應用程式，並註冊其裝置。 使用公司入口網站註冊裝置，將工作場所加入裝置。 需要有 Apple ID，才能使用公司入口網站註冊 iOS 裝置。 BYOD 不需要額外設定公司裝置。 請參閱[設定裝置管理](get-ready-to-enroll-devices-in-microsoft-intune.md#set-up-device-management)的步驟。 ([返回表格](#overview-of-device-enrollment-methods))

### DEM
裝置註冊管理員。 系統管理員會建立 DEM 帳戶來管理公司擁有的裝置。 管理員接著可以安裝公司入口網站，並註冊許多無使用者裝置。 深入了解 [DEM](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md)。 ([返回表格](#overview-of-device-enrollment-methods))

### DEP
Apple 裝置註冊方案。 系統管理員會建立原則，並將原則透過網路部署到使用 DEP 所購買和管理之屬公司擁有的 iOS 裝置。 使用者執行 iOS Setup Assistant 時，會註冊裝置。 這種方法支援 [iOS 受監督] (iOS Supervised) 模式，其接著會啟用：
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

**公司行動裝置的行為**

### 抹除
指定註冊裝置是否需要將裝置重設成出廠預設值、移除裝置中的所有資料，並將它回復為原始狀態。
[淘汰裝置](retire-devices-from-microsoft-intune-management.md) ([返回表格](#overview-of-device-enrollment-methods))

### 親和性
指定註冊方法是否支援將裝置與特定使用者連接的「使用者親和性」。 不論是否有使用者親和性，都可以註冊 “Opt” 裝置。 需要有使用者親和性，才能支援下項項目︰
  - 行動應用程式管理 (MAM) 應用程式
  - 對電子郵件和公司資料進行條件式存取
  - 公司入口網站應用程式

[使用者親和性](enroll-corporate-owned-ios-devices-in-microsoft-intune.md#using-company-portal-on-dep-or-apple-configurator-enrolled-devices) ([返回表格](#overview-of-device-enrollment-methods))

### 鎖定
指定是否可以鎖定裝置以防止使用者移除 Intune 原則，以有效地移除裝置不進行管理。 針對 iOS 裝置，鎖定裝置時需要裝置處於受監督模式。
([返回表格](#overview-of-device-enrollment-methods))

## 啟用裝置註冊  
 註冊可讓使用者在其個人裝置上存取公司資源，並讓系統管理員確保這些裝置遵守保護公司資源的原則。 這是使用 Intune 啟用「攜帶您自己的裝置」案例的最佳方式。 系統管理員必須在 Intune 主控台中啟用註冊，可能需要與裝置建立信任關係，並將授權指派給使用者。 接著會註冊裝置，通常由使用者輸入其公司或學校認證完成。 裝置隨後會從 Intune 接收原則，並取得資源的存取權。

[準備好在 Intune 中註冊裝置](get-ready-to-enroll-devices-in-microsoft-intune.md)

## 註冊公司擁有的裝置
可使用 Intune 主控台管理公司擁有的裝置 (CYOD)。 可直接透過 Apple 提供的工具註冊 iOS 裝置。 系統管理員或管理員可使用裝置註冊管理員來註冊所有裝置類型。 也可以將包含 IMEI 號碼的裝置識別和標記為公司擁有，以啟用 COD 案例。

[註冊公司擁有的裝置](manage-corporate-owned-devices.md)

## 使用 Exchange ActiveSync 和 Intune 的行動裝置管理
Intune 可使用 EAS MDM 原則來管理未註冊、但連線到 Exchange ActiveSync (EAS) 的行動裝置。 Intune 會使用 Exchange Connector 與內部部署和雲端託管的 EAS 通訊。

[使用 Exchange ActiveSync 和 Intune 的行動裝置管理](mobile-device-management-with-exchange-activesync-and-microsoft-intune.md)


## 使用 Intune 管理 Windows 電腦  
您也可以使用 Intune Windows PC 用戶端軟體，使用 Microsoft Intune 來管理 Windows 電腦。 使用 Intune 用戶端管理的電腦可以︰

 - 報告軟體和硬體清查
 - 安裝桌面應用程式 (例如 .exe 和 .msi 檔案)
 - 防火牆設定

使用 Intune 用戶端軟體管理的電腦無法選擇性地抹除或淘汰，而且無法利用許多 Intune 管理功能，例如條件式存取、VPN 和 Wi-Fi 設定，或憑證和電子郵件組態部署。

[使用 Intune 管理 Windows 電腦](manage-windows-pcs-with-microsoft-intune.md)



<!--HONumber=Aug16_HO4-->



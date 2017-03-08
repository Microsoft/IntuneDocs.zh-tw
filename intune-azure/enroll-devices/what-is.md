---
title: "什麼是 Microsoft Intune 裝置註冊"
titleSuffix: Intune Azure preview
description: "Intune Azure 預覽版︰了解 iOS、Android 及 Windows 裝置註冊。"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 02/15/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6f67fcd2-5682-4f9c-8d74-d4ab69dc978c
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 153cce3809e24303b8f88a833e2fc7bdd9428a4a
ms.openlocfilehash: 900883ea9e38342cced195f97693447fafd0e73f
ms.lasthandoff: 02/18/2017


---

# <a name="what-is-device-enrollment"></a>什麼是裝置註冊？
[!INCLUDE[azure_preview](../includes/azure_preview.md)]

本主題說明如何註冊，以及向 Intune 管理註冊行動裝置的各種方式。

您在 Intune 註冊的裝置 (包括 Windows 電腦)，從而管理這些裝置。 在 Intune 文件中，我們將此功能稱為「行動裝置管理」(MDM)。 當裝置註冊為行動裝置 (不是電腦) 時，會核發給這些裝置 MDM 憑證，而裝置則可使用此憑證與 Intune 服務通訊。

您的裝置註冊方式取決於裝置類型、擁有權，以及您所需要的管理級。 「攜帶您自己的裝置」(BYOD) 註冊可讓使用者註冊其個人電話、平板電腦或電腦。 屬公司擁有的裝置 (COD) 註冊可執行自動註冊、共用裝置或授權前註冊需求的管理案例。

您若是使用內部部署或裝載於雲端的 Exchange ActiveSync，則不需要註冊就能用一些簡單的 Intune 管理功能。 您可以將 Windows 電腦視為行動裝置加以管理。建議您依照下列步驟採取此做法。 您也可以使用[Intune 用戶端軟體](https://docs.microsoft.com/intune/deploy-use/manage-windows-pcs-with-microsoft-intune)將其視為電腦進行管理。


## <a name="overview-of-device-enrollment-methods"></a>裝置的註冊方法概觀

下表顯示 Intune 註冊方法和每個方法的支援功能與需求。 功能與需求如下所述。 以下是表格中使用的詞彙：

- **抹除** - 指出裝置是否需要先抹除，然後使用者才能註冊裝置。 「抹除」一詞表示將裝置進行原廠重設，這會移除所有資料。 如需詳細資訊，請參閱[對裝置上使用完全抹除或選擇性抹除](/intune-azure/manage-devices/use-full-or-selective-wipe-on-devices-using-microsoft-intune)。
- **親和性**：將裝置與使用者相關聯。 行動應用程式管理 (MAM) 和公司資料的條件式存取需要此功能。 如需詳細資訊，請參閱[使用者親和性](enroll-ios-devices-using-device-enrollment-program.md)。
- **鎖定** - 指出是否防止使用者取消註冊其裝置不進行管理。 使用者可以使用公司入口網站應用程式來取消註冊其在所有平台上的裝置。 他們無法使用原生作業系統功能表來取消註冊。


**iOS 的註冊方法**

| **方法** |    **需要抹除？** |    **同質性**    |    **鎖定** | **詳細資料** |
|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#byod)** | 否|    是 |    否 | 更多資訊即將推出|
|**[DEM](#dem)**|    否 |否 |否    | [詳細資訊](enroll-ios-devices-using-device-enrollment-program.md)|
|**[DEP](#dep)**|    是 |    選用 |    選用|[詳細資訊](enroll-ios-devices-using-device-enrollment-program.md)|
|**[USB-SA](#usb-sa)**|    是 |    選用 |    否| [詳細資訊](enroll-ios-devices-with-apple-configurator-and-setup-assistant.md)|
|**[USB-Direct](#usb-direct)**|    否 |    否    | 否|[詳細資訊](enroll-ios-devices-with-apple-configurator-and-direct-enrollment.md)|



**Windows 的註冊方法**

| **方法** |    **需要抹除？** |    **同質性**    |    **鎖定** | **詳細資料**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#byod)** | 是|    是 |    否 | 更多資訊即將推出|
|**[DEM](#dem)**|    否 |否 |否    |[詳細資訊](enroll-devices-using-device-enrollment-manager.md)|

**Android 的註冊方法**

| **方法** |    **需要抹除？** |    **同質性**    |    **鎖定** | **詳細資料**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#byod)** | 否|    是 |    否 | 更多資訊即將推出|
|**[DEM](#dem)**|    否 |否 |否    |[詳細資訊](enroll-ios-devices-using-device-enrollment-program.md)|


## <a name="byod"></a>BYOD
「攜帶您自己的裝置」使用者會安裝公司入口網站應用程式，並註冊其裝置。 這可以讓使用者連線到公司網路，並加入網域或 Azure Active Directory。 以大多數的平台來說，您皆必須針對許多 COD 案例啟用 BYOD 註冊。 您可以封鎖註冊個人擁有的 iOS 和 Android 裝置。 如需指示，請參閱[設定裝置類型限制](https://docs.microsoft.com/intune-azure/enroll-devices/set-enrollment-restrictions#set-device-type-restrictions)。

## <a name="corporate-owned-devices"></a>屬公司擁有的裝置
您可使用 Azure 入口網站管理公司擁有的裝置 (COD)。 iOS 裝置可直接透過 Apple 提供的工具進行註冊。 系統管理員或管理員可使用裝置註冊管理員來註冊所有裝置類型。 也可以將包含 IMEI 號碼的裝置識別和標記為公司擁有，以啟用 COD 案例。

### <a name="dem"></a>DEM
裝置註冊管理員 (DEM) 是特殊的使用者帳戶，可用於註冊及管理公司擁有的多部裝置。 管理員可以安裝公司入口網站，並註冊許多無使用者裝置。 深入了解 [DEM](enroll-devices-using-device-enrollment-manager.md)。 ([返回表格](#overview-of-device-enrollment-methods))

### <a name="dep"></a>DEP
Apple 裝置註冊方案 (DEP) 管理功能可讓您「以無線方式」建立原則，並將原則部署至透過 DEP 購買及管理的 iOS 裝置。 當使用者第一次開啟裝置並執行 iOS 設定輔助程式時，即會註冊裝置。 這種方法支援 **iOS 受監管**模式，其接著會啟用：

  -    已鎖定註冊
  -    Kiosk 模式及其他進階設定與限制

若要深入了解 iOS 註冊，請參閱︰

- [選擇註冊 iOS 裝置的方式](choose-ios-enrollment-method.md)
- [使用裝置註冊方案註冊 iOS 裝置](enroll-ios-devices-using-device-enrollment-program.md)
- [返回上列表格](#overview-of-device-enrollment-methods)

### <a name="usb-sa"></a>USB-SA
IT 系統管理員會透過 USB 使用 Apple Configurator，手動準備每部屬公司擁有的裝置，以使用設定助理進行註冊。 IT 系統管理員會建立註冊設定檔，並將其匯出至 Apple Configurator。 當使用者收到裝置時，系統會提示他們執行設定助理以註冊裝置。 這種方法支援 **iOS 受監管**模式，其接著會啟用：
  -    已鎖定註冊
  -    Kiosk 模式及其他進階設定與限制

若要深入了解 iOS 註冊，請參閱︰

- [決定 iOS 裝置的註方式](choose-ios-enrollment-method.md)
- [使用 Configurator 及設定助理註冊 iOS 裝置](enroll-ios-devices-with-apple-configurator-and-setup-assistant.md)

### <a name="usb-direct"></a>USB-Direct
若是 Direct Enrollment，系統管理員必須建立註冊原則並將其匯出至 Apple Configurator，以手動註冊每部裝置。 公司擁有的 USB 連接裝置可直接註冊，而不需重設成出廠預設值。 裝置會以無使用者裝置形式進行管理。 這些裝置不會受到鎖定或監管，亦不支援條件式存取、破解偵測和行動應用程式管理。

若要深入了解 iOS 註冊，請參閱︰

- [決定 iOS 裝置的註方式](choose-ios-enrollment-method.md)
- [使用 Configurator 及直接註冊來註冊 iOS 裝置](enroll-ios-devices-with-apple-configurator-and-direct-enrollment.md)

## <a name="mobile-device-management-with-exchange-activesync-and-intune"></a>使用 Exchange ActiveSync 和 Intune 的行動裝置管理
Intune 可使用 EAS MDM 原則來管理未註冊、但連線到 Exchange ActiveSync (EAS) 的行動裝置。 Intune 會使用 Exchange Connector 與內部部署或雲端託管的 EAS 通訊。 更多資訊即將推出。


## <a name="windows-pc-management-with-intune"></a>搭配 Intune 的 Windows PC 管理  
您也可以透過 Intune 用戶端軟體，搭配 Microsoft Intune 來管理 Windows 電腦。 透過 Intune 用戶端管理的電腦可以：

 - 報告軟體和硬體清查
 - 安裝桌面應用程式 (例如 .exe 和 .msi 檔案)
 - 管理防火牆設定

如果電腦是搭配 Intune 用戶端軟體來進行管理，則無法完全將其抹除 (即使可以進行選擇性抹除亦同)。 如果電腦是搭配 Intune 軟體用戶端來進行管理，就無法利用許多 Intune 管理功能，例如條件式存取、VPN 和 Wi-Fi 設定，或憑證和電子郵件組態部署。 更多資訊即將推出。

## <a name="supported-device-platforms-and-browsers"></a>支援的裝置平台與瀏覽器

請參閱 [Intune 支援的裝置與瀏覽器](https://docs.microsoft.com/intune/get-started/supported-mobile-devices-and-computers)

## <a name="mobile-device-cleanup-after-mdm-certificate-expiration"></a>MDM 憑證到期後的行動裝置清除

當行動裝置與 Intune 服務通訊時，會自動更新 MDM 憑證。 若行動裝置 (而不是電腦) 遭抹除，或一段時間無法與 Intune 服務通訊，便無法更新 MDM 憑證。 當 MDM 憑證過期 180 天後，該裝置便會從 Azure 入口網站上移除。


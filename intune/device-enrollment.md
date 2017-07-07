---
title: "什麼是 Microsoft Intune 裝置註冊"
titleSuffix: Intune on Azure
description: "了解 iOS、Android 及 Windows 裝置註冊。"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 05/29/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6f67fcd2-5682-4f9c-8d74-d4ab69dc978c
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 927e2f21aad4ff39c9351bef68eb510e93410c37
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2017
---
# <a name="what-is-device-enrollment"></a>什麼是裝置註冊？
[!INCLUDE[azure_portal](./includes/azure_portal.md)]

本主題說明如何註冊，以及向 Intune 管理註冊行動裝置的各種方式。

您會在 Intune 中註冊裝置的原因，是為了可以管理那些裝置。 在 Intune 文件中，我們將此功能稱為「行動裝置管理」(MDM)。 當裝置在 Intune 中註冊時，會核發給這些裝置 MDM 憑證，然後裝置會使用這些憑證與 Intune 服務通訊。

您的裝置註冊方式取決於裝置類型、擁有權，以及您所需要的管理級。 「攜帶您自己的裝置」(BYOD) 註冊可讓使用者註冊其個人電話、平板電腦或電腦。 屬公司擁有的裝置 (COD) 註冊可執行自動註冊、共用裝置或授權前註冊需求的管理案例。

您若是使用內部部署或裝載於雲端的 Exchange ActiveSync，則不需要註冊就能用一些簡單的 Intune 管理功能。 您可以將 Windows 電腦視為行動裝置加以管理。建議您依照下列步驟採取此做法。


## <a name="overview-of-device-enrollment-methods"></a>裝置的註冊方法概觀

下表提供 Intune 註冊方法的概觀及其功能與需求，如下所述。
**圖例**

- **需要重設**：裝置會在註冊期間重設成出廠預設值。
- **使用者親和性**：將裝置關聯至使用者。 如需詳細資訊，請參閱[使用者親和性](device-enrollment-program-enroll-ios.md)。
- **鎖定**：防止使用者取消註冊裝置。

**iOS 註冊方法**

| **方法** |  **需要重設** |    **使用者親和性**   |   **鎖定** | **詳細資料** |
|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#byod)** | 否|    是 |   否 | [詳細資訊](./apple-mdm-push-certificate-get.md)|
|**[DEM](#dem)**|   否 |否 |否  | [詳細資訊](./device-enrollment-program-enroll-ios.md)|
|**[DEP](#dep)**|   是 |   選用 |  選用|[詳細資訊](./device-enrollment-program-enroll-ios.md)|
|**[USB-SA](#usb-sa)**| 是 |   選用 |  否| [詳細資訊](./apple-configurator-setup-assistant-enroll-ios.md)|
|**[USB-Direct](#usb-direct)**| 否 |    否  | 否|[詳細資訊](./apple-configurator-direct-enroll-ios.md)|

**Windows 的註冊方法**

| **方法** |  **需要重設** |    **使用者親和性**   |   **鎖定** | **詳細資料**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#byod)** | 否 |   是 |   否 | [詳細資訊](windows-enroll.md)|
|**[DEM](#dem)**|   否 |否 |否  |[詳細資訊](device-enrollment-manager-enroll.md)|
|**自動註冊** | 否 |是 |否 | [詳細資訊](./windows-enroll.md#enable-windows-10-automatic-enrollment)|
|**大量註冊** |否 |否 |否 | [詳細資訊](./windows-bulk-enroll.md) |

**Android 的註冊方法**

| **方法** |  **需要重設** |    **使用者親和性**   |   **鎖定** | **詳細資料**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#byod)** | 否|    是 |   否 | [詳細資訊](./android-enroll.md)|
|**[DEM](#dem)**|   否 |否 |否  |[詳細資訊](./device-enrollment-program-enroll-ios.md)|
|**Android for Work**| 否 | 是 | 否| [詳細資訊](./android-enroll.md#enable-enrollment-of-android-for-work-devices) |


## <a name="byod"></a>BYOD
「攜帶您自己的裝置」使用者會安裝並執行公司入口網站應用程式，以註冊其裝置。 此程式可讓使用者存取公司資源，例如電子郵件。

## <a name="corporate-owned-devices"></a>屬公司擁有的裝置
以下是屬公司擁有的裝置 (COD) 註冊案例。 iOS 裝置可直接透過 Apple 提供的工具進行註冊。 系統管理員或管理員可使用裝置註冊管理員來註冊所有裝置類型。 也可以將包含 IMEI 號碼的裝置識別和標記為公司擁有，以啟用 COD 案例。

### <a name="dem"></a>DEM
裝置註冊管理員 (DEM) 是特殊的使用者帳戶，可用於註冊及管理公司擁有的多部裝置。 管理員可以安裝公司入口網站，並註冊許多無使用者裝置。 深入了解 [DEM](./device-enrollment-manager-enroll.md)。

### <a name="dep"></a>DEP
Apple 裝置註冊方案 (DEP) 管理功能可讓您「以無線方式」建立原則，並將原則部署至透過 DEP 購買及管理的 iOS 裝置。 當使用者第一次開啟裝置並執行 iOS 設定輔助程式時，即會註冊裝置。 這種方法支援 **iOS 監督**模式，其接著會啟用下列功能：

  - 已鎖定註冊
  - Kiosk 模式及其他進階設定與限制

深入了解 iOS DEP 註冊：

- [選擇註冊 iOS 裝置的方式](enrollment-method-choose-ios.md)
- [使用裝置註冊方案註冊 iOS 裝置](device-enrollment-program-enroll-ios.md)

### <a name="usb-sa"></a>USB-SA
IT 管理員會透過 USB 使用 Apple Configurator，手動準備每部屬公司擁有的裝置，以使用「設定助理」進行註冊。 IT 系統管理員會建立註冊設定檔，並將其匯出至 Apple Configurator。 當使用者收到裝置時，系統會提示他們執行設定助理以註冊裝置。 這種方法支援 **iOS 監督**模式，其接著會啟用下列功能：
  - 已鎖定註冊
  - Kiosk 模式及其他進階設定與限制

深入了解如如何使用「設定助理」進行 iOS Apple Configurator 註冊：

- [決定 iOS 裝置的註方式](enrollment-method-choose-ios.md)
- [使用 Configurator 及設定助理註冊 iOS 裝置](apple-configurator-setup-assistant-enroll-ios.md)

### <a name="usb-direct"></a>USB-Direct
若是 Direct Enrollment，系統管理員必須建立註冊原則並將其匯出至 Apple Configurator，以手動註冊每部裝置。 公司擁有的 USB 連接裝置可直接註冊，而不需重設成出廠預設值。 裝置會以無使用者裝置形式進行管理。 這些裝置不會受到鎖定或監管，亦不支援條件式存取、破解偵測和行動應用程式管理。

若要深入了解 iOS 註冊，請參閱︰

- [決定 iOS 裝置的註方式](enrollment-method-choose-ios.md)
- [使用 Configurator 及直接註冊來註冊 iOS 裝置](apple-configurator-direct-enroll-ios.md)

## <a name="mobile-device-management-with-exchange-activesync-and-intune"></a>使用 Exchange ActiveSync 和 Intune 的行動裝置管理
針對未註冊但已連接 Exchange ActiveSync (EAS) 的行動裝置，Intune 可以使用 EAS MDM 原則進行管理。 Intune 會使用 Exchange Connector 與內部部署或雲端託管的 EAS 通訊。 更多資訊即將推出。

## <a name="mobile-device-cleanup-after-mdm-certificate-expiration"></a>MDM 憑證到期後的行動裝置清除

當行動裝置與 Intune 服務通訊時，會自動更新 MDM 憑證。 若行動裝置被抹除，或有一段時間無法與 Intune 服務通訊，便無法更新 MDM 憑證。 當 MDM 憑證過期 180 天後，該裝置便會從 Azure 入口網站上移除。

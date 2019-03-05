---
title: Lookout MTD 連接器與 Microsoft Intune | Microsoft Intune
description: 深入了解整合 Intune 與 Lookout Mobile Threat Defense (MTD) 來控制行動裝置對公司資源的存取。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/09/2017
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 3a730a5d-2a90-42b0-aa28-aadfc7a18788
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7115421ea75e96c17ba3ca78773a9368f752d2a7
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/02/2019
ms.locfileid: "57236124"
---
# <a name="lookout-mobile-threat-defense-connector-with-intune"></a>Lookout Mobile Threat Defense 連接器與 Intune

您可以根據由 Lookout (一個與 Microsoft Intune 整合的 Mobile Threat Defense 解決方案) 所進行的風險評估，來控制行動裝置對公司資源的存取。 風險評估是根據 Lookout 服務收集自裝置的遙測，包括︰
- 作業系統漏洞
- 安裝的惡意應用程式
- 惡意網路設定檔

您可以根據透過 Intune 合規性原則所啟用的 Lookout 風險評估，來設定條件式存取原則。 設定可讓您根據偵測到的威脅來允許或封鎖不相容的裝置。

## <a name="how-do-intune-and-lookout-mobile-threat-defense-help-protect-company-resources"></a>Intune 和 Lookout Mobile Threat Defense 如何協助保護公司資源？
已在行動裝置上安裝和執行 Lookout 行動應用程式 (**Lookout for Work**)。 這個應用程式可擷取檔案系統、網路堆疊，以及裝置和應用程式遙測 (如果可用)，然後將其傳送至 Lookout 雲端服務，以評估裝置威脅的裝置風險。 您可以在 Lookout 主控台中變更威脅的風險層級分類，以符合您的需求。  

Intune 中的合規性原則包含根據 Lookout 風險評估的 Lookout Mobile Threat Defense 規則。 啟用此規則時，Intune 會評估裝置是否符合您啟用的原則。

如果裝置發現不相容，則可以封鎖對 Exchange Online 和 SharePoint Online 這類資源的存取。 已封鎖裝置上的使用者會收到解決此問題並重新取得存取權的步驟。 指引是從 Lookout for Work 應用程式來啟動。

## <a name="supported-platforms"></a>支援的平台
在 Intune 中註冊時，Lookout 支援下列平台︰
* **Android 4.1 和更新版本**
* **iOS 8 和更新版本**如需平台和語言支援的其他資訊，請前往 [Lookout 網站](https://personal.support.lookout.com/hc/articles/114094140253)。

## <a name="prerequisites"></a>必要條件
* Microsoft Intune 訂閱
* Azure Active Directory
* Lookout Mobile Endpoint Security 企業訂閱  

如需詳細資訊，請參閱 [Lookout Mobile Endpoint Security](https://www.lookout.com/products/mobile-endpoint-security)

## <a name="sample-scenarios"></a>範例案例

以下是搭配 Intune 使用 Lookout Mobile Threat Defense 時的常見案例。

### <a name="control-access-based-on-threats-from-malicious-apps"></a>根據惡意應用程式的威脅來控制存取權
在裝置上偵測到惡意應用程式 (例如惡意程式碼) 時，您可以在解決威脅之後封鎖裝置執行下列作業︰
* 連線到公司電子郵件
* 使用 OneDrive for Work 應用程式來同步處理公司檔案
* 存取公司應用程式

**於偵測到惡意應用程式時進行封鎖：**

![因惡意應用程式而封鎖存取的原則概念影像](./media/malicious-apps-blocked.png)

**修復後允許存取：**

![顯示修復後授與裝置存取權的概念影像](./media/malicious-apps-unblocked.png)

### <a name="control-access-based-on-threat-to-network"></a>根據網路威脅來控制存取權
偵測到攔截式攻擊等網路威脅，並根據裝置風險保護 Wi-Fi 網路的存取。

**封鎖透過 Wi-Fi 的網路存取：**

![顯示依據網路威脅來封鎖 WiFi 存取的影像](./media/network-wifi-blocked.png)

**修復後允許存取：**

![修復後允許存取的條件式存取概念影像](./media/network-wifi-unblocked.png)
### <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>根據網路威脅來控制 SharePoint Online 的存取權

偵測到攔截式攻擊等網路威脅，並根據裝置風險防止同步處理公司檔案。

**偵測到網路威脅時封鎖 SharePoint Online：**

![封鎖存取 SharePoint Online 的概念影像](./media/network-spo-blocked.png)


**修復後允許存取：**

![修復網路威脅後允許存取的概念影像](./media/network-spo-unblocked.png)

## <a name="next-steps"></a>後續步驟
以下是為了實作此解決方案所必須執行的主要步驟：
1.  [設定 Lookout 整合](lookout-mtd-connector-integration.md)
2.  [在 Intune 中啟用 Lookout Mobile Threat Defense](mtd-connector-enable.md)
3.  [新增並指派 Lookout for Work 應用程式](mtd-apps-ios-app-configuration-policy-add-assign.md)
4.  [設定 Lookout 裝置合規性原則](mtd-device-compliance-policy-create.md)

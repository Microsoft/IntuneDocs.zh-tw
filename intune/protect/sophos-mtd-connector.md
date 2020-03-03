---
title: 搭配 Intune 使用 Sophos Mobile
titleSuffix: Intune on Azure
description: 如何使用 Sophos Mobile 解決方案與 Microsoft Intune 的整合，來控制行動裝置對公司資源的存取。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 04/30/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7d17749353bc3904a3d99210a5d56531d9af9c28
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/20/2020
ms.locfileid: "77514807"
---
# <a name="sophos-mobile-threat-defense-connector-with-intune"></a>Sophos Mobile Threat Defense 與 Intune 的連接器
您可以根據由 Sophos Mobile (與 Microsoft Intune 整合的 Mobile Threat Defense (MTD) 解決方案) 所進行的風險評量，使用條件式存取來控制行動裝置對公司資源的存取。 風險是根據從執行 Sophos Mobile 應用程式之裝置所收集的遙測來評定的。
您可以根據透過 Intune 裝置合規性政策所啟用的 Sophos Mobile 風險評量，來設定條件式存取原則，而您可以根據偵測到的威脅，使用它們來允許或禁止不符合規範的裝置存取公司資源。

## <a name="how-do-intune-and-sophos-mobile-help-protect-your-company-resources"></a>Intune 和 Sophos Mobile 如何協助保護您的公司資源？
適用於 Android 及 iOS/iPadOS 的 Sophos Mobile 應用程式可擷取檔案系統、網路堆疊、裝置和應用程式遙測 (如果可用)，然後將遙測資料傳送至 Sophos Mobile 雲端服務，以評定裝置的行動裝置威脅風險。
Intune 裝置合規性政策包含以 Sophos Mobile 風險評定為基礎的 Sophos Mobile Threat Defense 規則。 啟用此規則時，Intune 會評估裝置是否符合您啟用的原則。 如果發現裝置不相容，則會封鎖使用者對 Exchange Online 和 SharePoint Online 這類公司資源的存取。 使用者也會從安裝在其裝置內的 Sophos Mobile 應用程式收到指導方針，以解決問題並重新取得公司資源的存取權。  

## <a name="sample-scenarios"></a>範例案例
以下是一些常見案例。  
### <a name="control-access-based-on-threats-from-malicious-apps"></a>根據惡意應用程式的威脅來控制存取權
在裝置上偵測到惡意應用程式 (例如惡意程式碼) 時，您可在解決威脅之前封鎖裝置執行下列動作：
- 連線到公司電子郵件
- 使用 OneDrive for Work 應用程式來同步處理公司檔案
- 存取公司應用程式

**於偵測到惡意應用程式時進行封鎖**：
 
![偵測到惡意應用程式的概念影像](./media/sophos-mtd-connector/sophos_malicious_apps_blocked.png)  

**補救後授與存取權**：  
![補救後授與存取權的概念影像](./media/sophos-mtd-connector/sophos_malicious_apps_unblocked.png)

### <a name="control-access-based-on-threat-to-network"></a>依據對網路的威脅性來控制存取  
偵測中間人攻擊等網路威脅，並根據裝置風險保護對 Wi-Fi 網路的存取。  

**封鎖透過 Wi-Fi 的網路存取**：  
![封鎖透過 Wi-Fi 的網路存取](./media/sophos-mtd-connector/sophos_network_wifi_blocked.png)

**補救後授與存取權**：   
![補救後授與存取權](./media/sophos-mtd-connector/sophos_network_wifi_unblocked.png)  

### <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>依據對網路的威脅來控制對 SharePoint Online 的存取  
偵測中間人攻擊等網路威脅，並根據裝置風險防止同步公司檔案。  

**偵測到網路威脅時封鎖 SharePoint Online**：   
![偵測到網路威脅時封鎖 SharePoint Online](./media/sophos-mtd-connector/sophos_network_spo_blocked.png)  

**補救後授與存取權**：  
![Sharepoint 的補救後授與存取權範例](./media/sophos-mtd-connector/sophos_network_spo_unblocked.png)  

## <a name="supported-platforms"></a>支援的平台  
- Android 5.0 及更新版本
- iOS 11.0 和更新版本

## <a name="prerequisites"></a>先決條件  
- Azure Active Directory Premium
- Microsoft Intune 訂閱 
- Sophos Mobile Threat Defense 訂用帳戶

如需詳細資訊，請參閱 [Sophos 網站](https://www.sophos.com/en-us/products/mobile-control.aspx)。

## <a name="next-steps"></a>後續步驟  
- [整合 Sophos 與 Intune](sophos-mtd-connector-integration.md)
- [設定 Sophos 應用程式](mtd-apps-ios-app-configuration-policy-add-assign.md)
- [建立 Sophos 裝置合規性政策](mtd-device-compliance-policy-create.md)
- [啟用 Sophos MTD 連接器](mtd-connector-enable.md)

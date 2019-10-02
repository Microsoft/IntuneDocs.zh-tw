---
title: 搭配 Intune 設定 Wandera Mobile Security
titleSuffix: Intune on Azure
description: 如何設定 Wandera Mobile Security Microsoft 與 Intune 的整合，來控制行動裝置對公司資源的存取。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: f4043ddc2a9f960b30e753c24e0b806e72b6850c
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2019
ms.locfileid: "71728282"
---
# <a name="wandera-mobile-threat-defense-connector-with-intune"></a>Wandera Mobile Threat Defense 與 Intune 的連接器  

您可以依據 Wandera 所執行的風險評定，使用條件式存取控制行動裝置對公司資源的存取。 Wandera 是與 Microsoft Intune 整合的 Mobile Threat Defense (MTD) 解決方案。  風險評估是根據 Wandera 服務收集自裝置的遙測，包括︰
- 作業系統漏洞
- 安裝的惡意應用程式
- 惡意網路設定檔
- 挖礦劫持

您可以設定以 Wandera 風險評定為基礎的條件式存取  原則 (透過 Intune 裝置合規性原則所啟用)。 風險評估原則可讓您根據偵測到的威脅，允許或封鎖不符合規範的裝置存取公司資源。  


## <a name="how-do-intune-and-wandera-mobile-threat-defense-help-protect-your-company-resources"></a>Intune 與 Wandera Mobile Threat Defense 如何協助保護您的公司資源？  

Wandera 的行動裝置應用程式會使用 Microsoft Intune 以無接縫方式安裝。 此應用程式會擷取檔案系統、網路堆疊與裝置和應用程式遙測 (如果可用)。 此資訊會同步到 Wandera 雲端服務以評定裝置的行動裝置威脅風險。 您可以在 Wandera 主控台 RADAR 中設定這些風險等級分類以符合您的需求。

Intune 中的合規性原則包括以 Wandera 風險評定為基礎的 MTD  規則。 啟用此規則時，Intune 會評估裝置是否符合您啟用的原則。

針對不符合規範的應用程式，您可以封鎖對資源 (例如 Office 365) 的存取。 已封鎖裝置上的使用者會從 Wandera 應用程式收到指導方針，以解決問題並重新取得存取權。

## <a name="supported-platforms"></a>支援的平台  

在 Intune 中註冊時，Wandera 支援下列平台︰

- Android 5.0 及更新版本  
- iOS 10.2 與更新版本  

如需有關平台與裝置的詳細資訊，請參閱 [Wandera 網站](https://www.wandera.com/why-wandera/features/device-support/) \(英文\)。

## <a name="prerequisites"></a>必要條件  

- Microsoft Intune 訂閱  
- Azure Active Directory  
- Wandera Mobile Threat Defense (先前稱為 Wandera Secure)  

如需詳細資訊，請參閱 [Wandera Mobile Security](https://www.wandera.com/mobile-security/) \(英文\)。
 
## <a name="sample-scenarios"></a>範例案例

以下是搭配 Intune 使用 Wandera MTD 時的常見案例。

### <a name="control-access-based-on-threats-from-malicious-apps"></a>根據惡意應用程式的威脅來控制存取權  

在裝置上偵測到惡意應用程式時，您可以在解決威脅之前使用常用工具封鎖裝置。 常見封鎖包括：  
- 連線到公司電子郵件  
- 使用 OneDrive for Work 應用程式來同步處理公司檔案  
- 存取公司應用程式  

**於偵測到惡意應用程式時進行封鎖**：

![偵測到惡意應用程式的概念影像](./media/wandera-mtd-connector/wandera-malicious-apps-blocked.png)  

**補救後授與存取權**： 

![修復後授與存取權的概念影像](./media/wandera-mtd-connector/wandera-malicious-apps-unblocked.png)


### <a name="control-access-based-on-threat-to-network"></a>根據網路威脅來控制存取權  

偵測到攔截式攻擊等網路威脅，並根據裝置風險保護對 Wi-Fi 網路的存取。  

**封鎖透過 Wi-Fi 的網路存取**：  

![封鎖透過 Wi-Fi 的網路存取](./media/wandera-mtd-connector/wandera-network-wifi-blocked.png)

**補救後授與存取權**：  

![補救後授與存取](./media/wandera-mtd-connector/wandera-network-wifi-unblocked.png)  

## <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>根據網路威脅來控制 SharePoint Online 的存取權

偵測到攔截式攻擊等網路威脅，並根據裝置風險防止同步處理公司檔案。

**偵測到網路威脅時封鎖 SharePoint Online**：  

![偵測到網路威脅時封鎖 SharePoint Online](./media/wandera-mtd-connector/wandera-network-spo-blocked.png)  


**補救後授與存取權**：  

![SharePoint 的補救後授與存取權範例](./media/wandera-mtd-connector/wandera-network-spo-unblocked.png)  

## <a name="next-steps"></a>後續步驟

- [將 Wandera 與 Intune 整合](wandera-mtd-connector-integration.md)
- [設定 Wandera 應用程式](mtd-apps-ios-app-configuration-policy-add-assign.md)
- [建立 Wandera 裝置合規性政策](mtd-device-compliance-policy-create.md)
- [啟用 Wandera MTD 連接器](mtd-connector-enable.md)
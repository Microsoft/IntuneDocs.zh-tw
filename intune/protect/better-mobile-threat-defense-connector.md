---
title: 搭配 Intune 使用的 Better Mobile Threat Defense 連接器
titleSuffix: Intune on Azure
description: 設定搭配 Intune 使用的 Better Mobile Threat Defense 連接器。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 07/25/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1a52636a140778f6e78bfe081cda40b36ef2354f
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72509647"
---
# <a name="better-mobile-threat-defense-connector-with-intune"></a>搭配 Intune 使用的 Better Mobile Threat Defense 連接器

您可以根據由 Better Mobile (與 Microsoft Intune 整合的 Mobile Threat Defense (MTD) 解決方案) 所進行的風險評量，使用條件式存取來控制行動裝置對公司資源的存取。 風險是根據從執行 Better Mobile 應用程式之裝置所收集的遙測來評定的。

您可以根據透過 Intune 裝置相容性政策所啟用的 Better Mobile 風險評量，來設定條件式存取原則，而您可以根據偵測到的威脅，使用它們來允許或封鎖不符合規範的裝置存取公司資源。

## <a name="how-do-intune-and-better-mobile-help-protect-your-company-resources"></a>Intune 和 Better Mobile 如何協助保護您的公司資源？

已在行動裝置上安裝並執行 Better Mobile 應用程式。 這個應用程式可擷取檔案系統、網路堆疊，以及裝置和應用程式遙測 (如果可用)，然後將資料傳送到 Better Mobile 雲端服務，以評估裝置的行動威脅風險。

Intune 裝置合規性原則包含以 Better Mobile 風險評定為基礎的 Mobile Threat Defense 規則。 啟用此規則時，Intune 會評估裝置是否符合您啟用的原則。 如果發現裝置不相容，則會封鎖使用者對 Exchange Online 和 SharePoint Online 這類公司資源的存取。 使用者也會從安裝在其裝置內的 Better Mobile 應用程式收到指導方針，以解決問題並重新取得公司資源的存取權。

## <a name="sample-scenarios"></a>範例案例

以下是一些常見案例。

### <a name="control-access-based-on-threats-from-malicious-apps"></a>根據惡意應用程式的威脅來控制存取權

在裝置上偵測到惡意應用程式 (例如惡意程式碼) 時，您可在解決威脅之前封鎖裝置執行下列動作：

- 連線到公司電子郵件

- 使用 OneDrive for Work 應用程式來同步處理公司檔案

- 存取公司應用程式

**於偵測到惡意應用程式時進行封鎖：**

![顯示偵測到惡意應用程式的影像](./media/better-mobile-threat-defense-connector/better_mobile_maliciousapps_blocked.png)

**修復後允許存取：**

![偵測到惡意應用程式後授與存取](./media/better-mobile-threat-defense-connector/better_mobile_maliciousapps_unblocked.png)

### <a name="control-access-based-on-threat-to-network"></a>根據網路威脅來控制存取權

偵測到**攔截式攻擊**等網路威脅，並根據裝置風險保護 Wi-Fi 網路的存取。

**封鎖透過 Wi-Fi 的網路存取︰**

![封鎖透過 Wi-Fi 的網路存取](./media/better-mobile-threat-defense-connector/better_mobile_network_wifi_blocked.png)

**修復後允許存取：**

![顯示修復後授與存取權的影像](./media/better-mobile-threat-defense-connector/better_mobile_network_wifi_unblocked.png)

### <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>根據網路威脅來控制 SharePoint Online 的存取權

偵測到**攔截式攻擊**等網路威脅，並根據裝置風險防止同步處理公司檔案。

**偵測到網路威脅時封鎖 SharePoint Online：**

![偵測到網路威脅時封鎖 SharePoint Online](./media/better-mobile-threat-defense-connector/better_mobile_network_spo_blocked.png)

**修復後允許存取：**

![Sharepoint 的補救後授與存取範例](./media/better-mobile-threat-defense-connector/better_mobile_network_spo_unblocked.png)

## <a name="supported-platforms"></a>支援的平台

- **Android 4.1 和更新版本**

- **iOS 8.0 及更新版本**

## <a name="prerequisites"></a>必要條件

- Azure Active Directory Premium

- Microsoft Intune 訂閱

- Better Mobile Threat Defense 訂用帳戶

  - 如需詳細資訊，請參閱 [Better Mobile 網站](https://www.better.mobi/)。

## <a name="next-steps"></a>後續步驟

- [整合 Better Mobile 與 Intune](better-mobile-mtd-connector-integration.md)

- [設定 Better Mobile 應用程式](mtd-apps-ios-app-configuration-policy-add-assign.md)

- [建立 Better Mobile 裝置合規性原則](mtd-device-compliance-policy-create.md)

- [啟用 Better Mobile MTD 連接器](mtd-connector-enable.md)

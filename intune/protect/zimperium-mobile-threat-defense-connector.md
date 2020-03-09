---
title: 搭配 Intune 使用的 Zimperium MTD 連接器
titleSuffix: Intune on Azure
description: 深入了解整合 Intune 與 Zimperium Mobile Threat Defense 來控制行動裝置對公司資源的存取。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/21/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 975d8d84-792a-41ad-925a-4a7f1ae4dcaf
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 32ace832e44f1cb6d334f69a0c1f03cb41515b2f
ms.sourcegitcommit: 045ca42cad6f86024af9a38a380535f42a6b4bef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2020
ms.locfileid: "77782037"
---
# <a name="zimperium-mobile-threat-defense-connector-with-intune"></a>搭配 Intune 使用的 Zimperium Mobile Threat Defense 連接器

您可以根據由 Zimperium (與 Microsoft Intune 整合的 Mobile Threat Defense (MTD) 解決方案) 所進行的風險評量，使用條件式存取來控制行動裝置對公司資源的存取。 風險是根據從執行 Zimperium 應用程式之裝置所收集的遙測來評定的。

您可以根據透過適用於註冊裝置的 Intune 裝置相容性原則所啟用的 Zimperium 風險評定來設定條件式存取原則，然後使用這些原則，以根據所偵測到威脅來允許或封鎖不相容的裝置存取公司資源。 針對未註冊的裝置，您可以使用應用程式保護原則，根據偵測到的威脅來強制執行封鎖或選擇性抹除。

## <a name="how-do-intune-and-zimperium-help-protect-your-company-resources"></a>Intune 和 Zimperium 如何協助您保護您的公司資源？

適用於 Android 及 iOS/iPadOS 的 Zimperium 應用程式可擷取檔案系統、網路堆疊、裝置和應用程式遙測 (如果可用)，然後將遙測資料傳送至 Zimperium 雲端服務，以評定裝置的行動威脅風險。

Intune 裝置合規性政策包含以 Zimperium 風險評定為基礎的 Zimperium Mobile Threat Defense 規則。 啟用此規則時，Intune 會評估裝置是否符合您啟用的原則。 如果發現裝置不相容，則會封鎖使用者對 Exchange Online 和 SharePoint Online 這類公司資源的存取。 使用者也會從安裝在其裝置內的 Zimperium 應用程式收到指導方針，以解決問題並重新取得公司資源的存取權。

## <a name="sample-scenarios"></a>範例案例

下方有一些案例可供您在將 Zimperium 與 Intune 整合時參考：

### <a name="control-access-based-on-threats-from-malicious-apps"></a>根據惡意應用程式的威脅來控制存取權

在裝置上偵測到惡意應用程式 (例如惡意程式碼) 時，您可以封鎖裝置，直到解決威脅為止︰

- 連線到公司電子郵件

- 使用 OneDrive for Work 應用程式來同步處理公司檔案

- 存取公司應用程式

**於偵測到惡意應用程式時進行封鎖：**

![偵測到惡意應用程式的概念影像](./media/zimperium-mobile-threat-defense-connector/Maliciousapps_blocked_Zimperium.png)

**修復後允許存取：**

![修復後授與存取權的概念影像](./media/zimperium-mobile-threat-defense-connector/maliciousapps_unblocked_Zimperium.png)

### <a name="control-access-based-on-threat-to-network"></a>依據對網路的威脅性來控制存取

偵測網路中的「攔截式攻擊」  等威脅，並根據裝置風險保護對 Wi-Fi 網路的存取。

**封鎖透過 Wi-Fi 的網路存取︰**

![封鎖透過 Wi-Fi 的網路存取](./media/zimperium-mobile-threat-defense-connector/network_wifi_blocked_Zimperium.png)

**修復後允許存取：**

![補救後授與存取](./media/zimperium-mobile-threat-defense-connector/network_wifi_unblocked_Zimperium.png)

### <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>依據對網路的威脅來控制對 SharePoint Online 的存取

偵測網路中的「攔截式攻擊」  等威脅，並根據裝置風險防止對公司檔案進行同步處理。

**偵測到網路威脅時封鎖 SharePoint Online：**

![偵測到網路威脅時封鎖 SharePoint Online](./media/zimperium-mobile-threat-defense-connector/network_spo_blocked_Zimperium.png)

**修復後允許存取：**

![Sharepoint 的補救後授與存取範例](./media/zimperium-mobile-threat-defense-connector/network_spo_unblocked_Zimperium.png)

## <a name="supported-platforms"></a>支援的平台

- **Android 4.1 和更新版本**

- **iOS 8 和更新版本**

## <a name="prerequisites"></a>先決條件

- Azure Active Directory Premium

- Microsoft Intune 訂閱

- Zimperium Mobile Threat Defense 訂用帳戶

  - 如需詳細資訊，請參閱 [Zimperium 網站](https://www.zimperium.com/zips-mobile-ips) \(英文\)。

## <a name="next-steps"></a>後續步驟

- [將 Zimperium 與 Intune 整合](zimperium-mtd-connector-integration.md)

- [設定 Zimperium 應用程式](mtd-apps-ios-app-configuration-policy-add-assign.md)

- [建立 Zimperium 裝置合規性政策](mtd-device-compliance-policy-create.md)

- [啟用 Zimperium MTD 連接器](mtd-connector-enable.md)

- [建立 MTD 應用程式保護原則](../protect/mtd-app-protection-policy.md)

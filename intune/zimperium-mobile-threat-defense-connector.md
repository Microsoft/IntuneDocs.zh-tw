---
title: 搭配 Intune 使用的 Zimperium MTD 連接器
titleSuffix: Intune on Azure
description: 深入了解整合 Intune 與 Zimperium Mobile Threat Defense 來控制行動裝置對公司資源的存取。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 12/29/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 975d8d84-792a-41ad-925a-4a7f1ae4dcaf
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: b94b4228f05abd2e7c815797f2f187efb8b303e4
ms.sourcegitcommit: bee072b61cf8a1b8ad8d736b5f5aa9bc526e07ec
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53817240"
---
# <a name="zimperium-mobile-threat-defense-connector-with-intune"></a>搭配 Intune 使用的 Zimperium Mobile Threat Defense 連接器

您可以根據由 Zimperium (與 Microsoft Intune 整合的 Mobile Threat Defense 解決方案) 所進行的風險評定，使用條件式存取來控制行動裝置對公司資源的存取。 風險是根據從執行 Zimperium 應用程式之裝置所收集的遙測來評定的。

您可以根據透過 Intune 裝置合規性政策所啟用的 Zimperium 風險評估，來設定條件式存取原則。 風險評估原則可讓您根據偵測到的威脅，允許或封鎖不符合規範的裝置存取公司資源。

## <a name="how-do-intune-and-zimperium-help-protect-your-company-resources"></a>Intune 和 Zimperium 如何協助您保護您的公司資源？

適用於 Android 及 iOS 的 Zimperium 應用程式可擷取檔案系統、網路堆疊、裝置和應用程式遙測 (如果可用)，然後將遙測資料傳送至 Zimperium 雲端服務，以評定裝置的行動威脅風險。

Intune 裝置合規性政策包含以 Zimperium 風險評定為基礎的 Zimperium Mobile Threat Defense 規則。 啟用此規則時，Intune 會評估裝置是否符合您啟用的原則。 如果發現裝置不相容，則會封鎖使用者對 Exchange Online 和 SharePoint Online 這類公司資源的存取。 使用者也會從安裝在其裝置內的 Zimperium 應用程式收到指導方針，以解決問題並重新取得公司資源的存取權。

## <a name="sample-scenarios"></a>範例案例

下方有一些案例可供您在將 Zimperium 與 Intune 整合時參考：

### <a name="control-access-based-on-threats-from-malicious-apps"></a>根據惡意應用程式的威脅來控制存取權

在裝置上偵測到惡意應用程式 (例如惡意程式碼) 時，您可以封鎖裝置，直到解決威脅為止︰

-   連線到公司電子郵件

-   使用 OneDrive for Work 應用程式來同步處理公司檔案

-   存取公司應用程式

**於偵測到惡意應用程式時進行封鎖：**

![偵測到惡意應用程式的概念影像](./media/Maliciousapps_blocked_Zimperium.png)

**修復後允許存取：**

![修復後授與存取權的概念影像](./media/maliciousapps_unblocked_Zimperium.png)

### <a name="control-access-based-on-threat-to-network"></a>根據網路威脅來控制存取權

偵測網路中 **中間人攻擊** 等威脅，並根據裝置風險保護對 Wi-Fi 網路的存取。

**封鎖透過 Wi-Fi 的網路存取︰**

![封鎖透過 Wi-Fi 的網路存取](./media/network_wifi_blocked_Zimperium.png)

**修復後允許存取：**

![補救後授與存取](./media/network_wifi_unblocked_Zimperium.png)

### <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>根據網路威脅來控制 SharePoint Online 的存取權

偵測網路中 **中間人攻擊** 等威脅，並根據裝置風險防止同步公司檔案。

**偵測到網路威脅時封鎖 SharePoint Online：**

![偵測到網路威脅時封鎖 SharePoint Online](./media/network_spo_blocked_Zimperium.png)

**修復後允許存取：**

![Sharepoint 的補救後授與存取範例](./media/network_spo_unblocked_Zimperium.png)

## <a name="supported-platforms"></a>支援的平台

-   **Android 4.1 和更新版本**

-   **iOS 8 和更新版本**

## <a name="prerequisites"></a>必要條件

-   Azure Active Directory Premium

-   Microsoft Intune 訂閱

-   Zimperium Mobile Threat Defense 訂用帳戶

    -   如需詳細資訊，請參閱 [Zimperium 網站](https://www.zimperium.com/zips-mobile-ips)。

## <a name="next-steps"></a>後續步驟

- [將 Zimperium 與 Intune 整合](zimperium-mtd-connector-integration.md)

- [設定 Zimperium 應用程式](mtd-apps-ios-app-configuration-policy-add-assign.md)

- [建立 Zimperium 裝置合規性政策](mtd-device-compliance-policy-create.md)

- [啟用 Zimperium MTD 連接器](mtd-connector-enable.md)

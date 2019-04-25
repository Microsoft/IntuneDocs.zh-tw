---
title: Symantec 連接器與 Microsoft Intune
titleSuffix: Microsoft Intune
description: 深入了解整合 Intune 與 Symantec Endpoint Protection Mobile 來控制行動裝置對公司資源的存取。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 12/09/2017
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: df4ce3f6-a093-432c-ab86-7a83865e389e
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b3c2cd696e2e8dabbe8c45a5758d1315c4ca31c4
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61506436"
---
# <a name="symantec-endpoint-protection-mobile-connector"></a>Symantec Endpoint Protection Mobile 連接器

您可以根據由 Symantec Endpoint Protection Mobile (SEP Mobile，一個與 Microsoft Intune 整合的行動裝置威脅防護解決方案) 所進行的風險評估，使用條件式存取來控制行動裝置對公司資源的存取。 風險評估是根據收集自執行 SEP Mobile 裝置的遙測，包括︰

-   實體防禦

-   網路防禦

-   應用程式防禦

-   弱點防禦

您可以透過 Intune 裝置合規性政策啟用 SEP Mobile 風險評估，然後使用條件式存取原則，根據偵測到的威脅來允許或封鎖不合規範的裝置存取公司資源。

## <a name="how-do-intune-and-sep-mobile-help-protect-your-company-resources"></a>Intune 和 SEP Mobile 如何協助保護您的公司資源？

適用於 Android 或 iOS 的 SEP Mobile 應用程式可擷取檔案系統、網路堆疊，裝置和應用程式遙測 (如果可用)，然後將它傳送至 Symantec 雲端服務，以評估裝置的行動威脅風險。

Intune 裝置合規性政策包含以 SEP Mobile 風險評估為基礎的 SEP Mobile 規則。 啟用此規則時，Intune 會評估裝置是否符合您啟用的原則。

如果發現裝置不相容，則會封鎖對 Exchange Online 和 SharePoint Online 這類資源的存取。 已封鎖裝置上的使用者會從 SEP Mobile 應用程式收到指導方針，以解決問題並重新取得公司資源的存取權。

Intune 支援兩種與 SEP Mobile 整合的模式：

-   「基本設定」是唯讀模式，允許 Intune 中的裝置看見 SEP Mobile。

-   「完整整合」可讓 SEP Mobile 向 Intune 報告裝置風險和安全性事件詳細資料。

## <a name="sample-scenarios"></a>範例案例

以下是一些常見的案例：

### <a name="control-access-based-on-threats-from-malicious-apps"></a>根據惡意應用程式的威脅來控制存取權

在裝置上偵測到惡意應用程式 (例如惡意程式碼) 時，您可以封鎖裝置，直到解決威脅為止︰

-   連線到公司電子郵件

-   使用 OneDrive for Work 應用程式來同步處理公司檔案

-   存取公司應用程式

**於偵測到惡意應用程式時進行封鎖：**

![偵測到惡意應用程式的概念影像](./media/symantec-arch-1.png)

**修復後允許存取：**

![偵測到惡意應用程式並修復後授與存取權的影像](./media/symantec-arch-2.png)

### <a name="control-access-based-on-threat-to-network"></a>根據網路威脅來控制存取權

偵測網路中的「攔截式攻擊」等威脅，並根據裝置風險保護對 Wi-Fi 網路的存取。

**封鎖透過 Wi-Fi 的網路存取︰**

![封鎖透過 Wi-Fi 的網路存取](./media/symantec-arch-3.png)

**修復後允許存取：**

![補救後授與存取](./media/symantec-arch-4.png)

### <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>根據網路威脅來控制 SharePoint Online 的存取權

偵測網路中的「攔截式攻擊」等威脅，並根據裝置風險防止對公司檔案進行同步處理。

**偵測到網路威脅時封鎖 SharePoint Online：**

![偵測到網路威脅時封鎖 SharePoint Online](./media/symantec-arch-5.png)

**修復後允許存取：**

![Sharepoint 的補救後授與存取範例](./media/symantec-arch-6.png)

## <a name="supported-platforms"></a>支援的平台

-   **Android 4.1 和更新版本**

-   **iOS 8 和更新版本**

## <a name="pre-requisites"></a>必要條件

-   Azure Active Directory Premium

-   Microsoft Intune 訂閱

-   Symantec Endpoint Protection Mobile 訂用帳戶

如需詳細資訊，請參閱 [Symantec 網站](https://www.skycure.com/skycure-microsoft-integration/) \(英文\)。

## <a name="next-steps"></a>後續步驟

以下是整合 Intune 與 SEP Mobile 所需完成的步驟：

- [設定 SEP Mobile 與 Intune 整合](skycure-mtd-connector-integration.md)

- [新增並指派 SEP Mobile 應用程式、Microsoft Authenticator 和 iOS 應用程式設定原則](mtd-apps-ios-app-configuration-policy-add-assign.md)

- [使用 Intune 建立 SEP Mobile 的裝置合規性政策](mtd-device-compliance-policy-create.md)

- [在 Intune 中啟用 SEP Mobile MTD 連接器](mtd-connector-enable.md)

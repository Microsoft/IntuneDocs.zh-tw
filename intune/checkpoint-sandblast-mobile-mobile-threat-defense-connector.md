---
title: Check Point SandBlast MTD 與 Microsoft Intune
titlesuffix: ''
description: 深入了解整合 Intune 與 Check Point SandBlast Mobile Threat Defense 來控制行動裝置對公司資源的存取。
keywords: ''
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 07/03/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 706a4228-9bdf-41e0-b8d1-64c923dd2d2b
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: a0dad532511b87b7856bb2e293707ac5311eb773
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/08/2018
ms.locfileid: "29776000"
---
# <a name="check-point-sandblast-mobile-threat-defense-connector-with-intune"></a>Check Point SandBlast Mobile Threat Defense 連接器與 Intune

您可以根據 Check Point SandBlast Mobile (一個整合了 Microsoft Intune 的行動威脅防禦解決方案) 進行的風險評估，使用條件式存取來控制行動裝置對公司資源的存取。 風險評估的依據是收集自執行 Check Point SandBlast Mobile 應用程式裝置的遙測。

您可以根據透過 Intune 裝置相容性原則啟用的 Check Point SandBlast Mobile 風險評估，設定條件式存取原則。透過該原則，您可以根據偵測到的威脅來允許或封鎖不相容的裝置存取公司資源。

## <a name="how-do-intune-and-check-point-sandblast-mobile-help-protect-your-company-resources"></a>Intune 和 Check Point SandBlast Mobile 如何協助保護您的公司資源？

適用於 Android 及 iOS 的 Check Point SandBlast Mobile 應用程式可擷取檔案系統、網路堆疊，裝置和應用程式遙測 (如果可用)，然後將遙測資料傳送至 Check Point SandBlast Mobile 雲端服務，以評估裝置的行動威脅風險。

Intune 裝置合規性原則包含以 Check Point SandBlast Mobile 風險評估為基礎的 Check Point SandBlast Mobile Threat Defense 規則。 啟用此規則時，Intune 會評估裝置是否符合您啟用的原則。 如果發現裝置不相容，則會封鎖使用者對 Exchange Online 和 SharePoint Online 這類公司資源的存取。 使用者也會從 Check Point SandBlast Mobile 應用程式收到指導方針，以解決問題並重新取得公司資源的存取權。

<!-- ## Sample scenarios 
closing syntax for comment above is missing. Please insert closing syntax at intended location. -->

以下是一些常見的案例：

### <a name="control-access-based-on-threats-from-malicious-apps"></a>根據惡意應用程式的威脅來控制存取權

在裝置上偵測到惡意應用程式 (例如惡意程式碼) 時，您可以封鎖裝置，直到解決威脅為止︰

-   連線到公司電子郵件

-   使用 OneDrive for Work 應用程式來同步處理公司檔案

-   存取公司應用程式

**於偵測到惡意應用程式時進行封鎖：**

![Check Point MTD 於偵測到惡意應用程式時進行封鎖](./media/checkpoint-MTD-2.PNG)

**修復後允許存取：**

![Check Point MTD 授與存取權](./media/checkpoint-MTD-3.PNG)

### <a name="control-access-based-on-threat-to-network"></a>根據網路威脅來控制存取權

偵測網路中的「攔截式攻擊」等威脅，並根據裝置風險保護對 Wi-Fi 網路的存取。

**封鎖透過 Wi-Fi 的網路存取︰**

![Check Point MTD 封鎖透過 Wi-Fi 的網路存取](./media/checkpoint-MTD-4.PNG)

**修復後允許存取：**

![Check Point MTD 授與 Wi-Fi 存取權](./media/checkpoint-MTD-5.PNG)

### <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>根據網路威脅來控制 SharePoint Online 的存取權

偵測網路中的「攔截式攻擊」等威脅，並根據裝置風險防止對公司檔案進行同步處理。

**偵測到網路威脅時封鎖 SharePoint Online：**

![Check Point MTD 封鎖 SharePoint Online 存取](./media/checkpoint-MTD-6.PNG)

**修復後允許存取：**

![Check Point MTD 授與 SharePoint Online 存取權](./media/checkpoint-MTD-7.PNG)

## <a name="supported-platforms"></a>支援的平台

-   **Android 4.1 和更新版本**

-   **iOS 8 和更新版本**

## <a name="pre-requisites"></a>必要條件

-   Azure Active Directory Premium

-   Microsoft Intune 訂閱

-   Check Point SandBlast Mobile Threat Defense 訂閱
    -   如需詳細資訊，請參閱 [Check Point SandBlast 網站](https://www.checkpoint.com/)。

## <a name="next-steps"></a>接下來的步驟

- [整合 Check Point SandBlast 與 Intune](checkpoint-sandblast-mobile-mtd-connector-integration.md)

- [設定 Check Point SandBlast Mobile 應用程式](mtd-apps-ios-app-configuration-policy-add-assign.md)

- [建立 Check Point SandBlast Mobile 裝置相容性原則](mtd-device-compliance-policy-create.md)

- [啟用 Check Point SandBlast Mobile MTD 連接器](mtd-connector-enable.md)

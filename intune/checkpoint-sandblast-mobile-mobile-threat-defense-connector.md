---
title: "Check Point SandBlast 連接器與 Intune"
titlesuffix: Azure portal
description: "整合 Check Point SandBlast 與 Intune"
keywords: 
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 07/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 706a4228-9bdf-41e0-b8d1-64c923dd2d2b
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: d528ee9b72b5b7476845c0051f67f8a6ed887d1c
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2018
---
# <a name="check-point-sandblast-mobile-threat-defense-connector-with-intune"></a>Check Point SandBlast Mobile Threat Defense 連接器與 Intune

您可以根據 Check Point SandBlast Mobile (一個整合了 Microsoft Intune 的行動威脅防禦解決方案) 進行的風險評估，使用條件式存取來控制行動裝置對公司資源的存取。 風險評估的依據是收集自執行 Check Point SandBlast Mobile 應用程式裝置的遙測。

您可以根據透過 Intune 裝置合規性原則啟用的 Check Point SandBlast Mobile 風險評估，設定條件式存取原則。透過該原則，您可以根據偵測到的威脅來允許或封鎖不符合規範的裝置存取公司資源。

## <a name="how-do-intune-and-check-point-sandblast-mobile-help-protect-your-company-resources"></a>Intune 和 Check Point SandBlast Mobile 如何協助保護您的公司資源？

適用於 Android 及 iOS 的 Check Point SandBlast Mobile 應用程式可擷取檔案系統、網路堆疊，裝置和應用程式遙測 (如果可用)，然後將遙測資料傳送至 Check Point SandBlast Mobile 雲端服務，以評估裝置的行動威脅風險。

Intune 裝置合規性原則包含以 Check Point SandBlast Mobile 風險評估為基礎的 Check Point SandBlast Mobile Threat Defense 規則。 啟用此規則時，Intune 會評估裝置是否符合您啟用的原則。 如果發現裝置不符合規範，則會封鎖使用者對 Exchange Online 和 SharePoint Online 這類公司資源的存取。 使用者也會從 Check Point SandBlast Mobile 應用程式收到指導方針，以解決問題並重新取得公司資源的存取權。

<!-- ## Sample scenarios

Here are some common scenarios:

### Control access based on threats from malicious apps

When malicious apps such as malware are detected on devices, you can block devices until the threat is resolved:

-   Connecting to corporate e-mail

-   Syncing corporate files with the OneDrive for Work app

-   Accessing company apps

**Block when malicious apps are detected:**

![Check Point MTD block when malicious apps are detected](./media/checkpoint-MTD-2.PNG)

**Access granted on remediation:**

![Check Point MTD access granted](./media/checkpoint-MTD-3.PNG)

### Control access based on threat to network

Detect threats like **Man-in-the-middle** in network, and protect access to Wi-Fi networks based on the device risk.

**Block network access through Wi-Fi:**

![Check Point MTD block network access through Wi-Fi](./media/checkpoint-MTD-4.PNG)

**Access granted on remediation:**

![Check Point MTD Wi-Fi access granted](./media/checkpoint-MTD-5.PNG)

### Control access to SharePoint Online based on threat to network

Detect threats like **Man-in-the-middle** in network, and prevent synchronization of corporate files based on the device risk.

**Block SharePoint Online when network threats are detected:**

![Check Point MTD block SharePoint Online access](./media/checkpoint-MTD-6.PNG)

**Access granted on remediation:**

![Check Point MTD SharePoint Online access granted](./media/checkpoint-MTD-7.PNG)

## Supported platforms

-   **Android 4.1 and later**

-   **iOS 8 and later**

## Pre-requisites

-   Azure Active Directory Premium

-   Microsoft Intune subscription

-   Check Point SandBlast Mobile Threat Defense subscription
    -   See [CheckPoint SandBlast website](https://www.checkpoint.com/) for more information.

## Next steps

- [Integrate CheckPoint SandBlast with Intune](checkpoint-sandblast-mobile-mtd-connector-integration.md)

- [Set up CheckPoint SandBlast Mobile app](mtd-apps-ios-app-configuration-policy-add-assign.md)

- [Create CheckPoint SandBlast Mobile device compliance policy](mtd-device-compliance-policy-create.md)

- [Enable CheckPoint SandBlast Mobile MTD connector](mtd-connector-enable.md)

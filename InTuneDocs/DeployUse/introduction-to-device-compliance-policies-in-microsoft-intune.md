---
title: "裝置相容性原則 | Microsoft Intune"
description: "本主題說明您必須了解的概念，包括什麼是裝置相容性原則，以及它們的運作方式。"
keywords: 
author: karthikaraman
ms.author: karaman
manager: angrobe
ms.date: 07/18/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0775107a-6662-41c8-9404-be14bbb599f3
ms.reviewer: chrisgre
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 550fbbf94f46eee23e77ebf7f9177148882f28e2
ms.openlocfilehash: a853eb4de5528b3ca219ca844a9df4f3b5ad9224


---

# Microsoft Intune 的裝置相容性原則
## 什麼是相容性原則？
若要保護公司資料，您需要確定用來存取公司應用程式和資料的裝置符合特定規則 (例如使用 PIN 存取裝置)，以及裝置上所儲存資料的加密。 一組這類規則稱為相容性原則。

## 應該如何使用相容性原則？
您可以使用具有條件式存取原則的相容性原則，只允許符合相容性原則規則的裝置存取電子郵件和其他服務。 閱讀[限制存取電子郵件和 O365 服務](restrict-access-to-email-and-o365-services-with-microsoft-intune.md)文章，了解如何搭配使用這兩個原則。

您也可以使用與條件式存取無關的相容性原則。 單獨使用時，會評估目標裝置，並回報其相容性狀態。 例如，您可能想要報告有關未加密的裝置數目，或哪些裝置已進行破解或刷機。 不過，單獨使用時，對公司資源沒有存取限制。

您可以將相容性原則部署到使用者。 將相容性原則部署到使用者時，即會檢查使用者裝置的相容性。
若要深入了解行動裝置在部署之後需要多長的時間才能取得原則，請參閱[管理裝置上的設定和功能](https://docs.microsoft.com/en-us/intune/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies#frequently-asked-questions-about-intune-policies)

下表列出相容性原則支援的裝置類型，以及在將該原則與條件式存取原則搭配使用時如何管理不相容的設定。

-----------------------------

|原則設定| Windows 8.1 及更新版本| Windows Phone 8.1 和更新版本| iOS 8.0 和更新版本|Android 4.0 及更新版本<br/>Samsung KNOX 標準 4.0 及更新版本|
|-----|----|----|----|----|
|**PIN 碼或密碼組態** |已修復|已修復|已修復|已隔離|
|**裝置加密**|N/A|已修復|已修復 (藉由設定 PIN 碼)|已隔離|
|**Jailbroken 或根目錄的裝置**|N/A|N/A|隔離 (非設定)|隔離 (非設定)|
|**電子郵件設定檔**|N/A|N/A|已隔離|N/A|
|**最低 OS 版本**|已隔離|已隔離|已隔離|已隔離|
|**最高 OS 版本**|已隔離| 已隔離| 已隔離| 已隔離|
|**Windows 健全情況證明**|隔離 Windows 10 和 Windows 10 Mobile。<br /><br />設定不適用於 Windows 8.1|N/A|N/A|N/A|

------------------------------

**已修復** = 相容性由裝置作業系統執行 (例如，強制使用者設定 PIN 碼)。  永遠不可能發生設定不相容的情況。

**已隔離** = 裝置作業系統不會強制要求相容性 (例如，Android 裝置不會強制要求使用者加密裝置)。 裝置不相容時，會採取下列動作︰

-   如果使用者是條件式存取原則的目標，則將會封鎖該裝置。

-   公司入口網站將通知使用者有關任何相容性問題。

## 後續步驟
[建立裝置相容性原則](create-a-device-compliance-policy-in-microsoft-intune.md)

[部署和監視裝置相容性原則](deploy-and-monitor-a-device-compliance-policy-in-microsoft-intune.md)

### 請參閱
[限制存取電子郵件和 O365 服務](restrict-access-to-email-and-o365-services-with-microsoft-intune.md)



<!--HONumber=Sep16_HO4-->



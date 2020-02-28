---
title: 防止資料在未受管理的裝置上外洩
titleSuffix: Microsoft Intune
description: 允許在裝置上存取公司資料，並使用 Microsoft Intune 防止資料外洩。
keywords: 資料保護避免外洩裝置 O365 Office 365 的資料
ms.author: dougeby
author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: archived
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: b1512c3a-3bbd-4111-a0df-c874a0a335df
ms.reviewer: pchacon
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0d9e61cbe4f6d6e07c61fe182e639e715996f9ee
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/20/2020
ms.locfileid: "77514433"
---
# <a name="prevent-data-leaks-on-non-managed-devices-using-microsoft-intune"></a>使用 Microsoft Intune 防止資料在非受控裝置上外洩

如果您允許存取 Office 365 所裝載的公司資料，就可以控制使用者如何共用和儲存資料，避免發生蓄意或意外資料外洩的風險。 Microsoft Intune 提供應用程式保護原則，讓您可在使用者擁有的裝置上設定，以保護您的公司資料。 裝置無須在 Intune 服務中註冊。 

透過 Intune 設定的應用程式保護原則也適用於使用非 Microsoft 裝置管理解決方案進行管理的裝置。 裝置上的個人資料不會受影響；只有公司資料會由 IT 部門管理。 

您可以在執行 Windows、iOS 或 Android 的裝置上，為 Office 行動裝置應用程式設定應用程式保護原則，以保護公司資料。 這些原則可讓您設定原則 (例如以應用程式為基礎的 PIN 或公司資料加密) 及其他進階設定，以限制使用者在受管理及未受管理應用程式間使用剪下、複製、貼上及另存新檔功能的方式。 您也可以從遠端抹除公司資料而無須要求使用者註冊裝置。

Intune 應用程式保護原則獨立於裝置管理之外。 不論 Office 行動應用程式應用程式是同時在未受管理和受 Intune 管理裝置上，或是在非 Microsoft MDM 解決方案所管理的裝置上，您都能運用應用程式保護原則加以管理。

## <a name="before-you-begin"></a>開始之前

當您符合下列需求時，可以使用下列行動計劃：

* 您的公司已可安全地轉換到雲端。
* 您的公司使用 Office 365 Exchange Online、SharePoint Online、商務用 OneDrive 或 Yammer。
* 您的公司有 Microsoft 365、Enterprise Mobility + Security (EMS) 或 Azure 資訊安全的授權。
* 您的公司允許使用者從公司擁有或個人擁有的 Windows、iOS 或 Android 裝置存取公司資料。
* 您的公司不想要求在裝置管理服務中註冊個人擁有的裝置。

## <a name="action-plan"></a>動作計劃

針對 iOS/iPadOS 和 Android 裝置：

1. 了解[應用程式保護原則](../apps/app-protection-policy.md)如何運作。
2. 了解如何為 Office 行動裝置應用程式[建立及部署應用程式保護原則](../apps/app-protection-policies.md)。
3. [監視您建立和部署的應用程式保護原則](../apps/app-protection-policies-monitor.md)。

若是 Windows 10 裝置：

1. 了解 [Windows 資訊保護 (WIP) 如何運作](https://docs.microsoft.com/windows/threat-protection/windows-information-protection/protect-enterprise-data-using-wip)。
2. 準備設定[適用於 Windows 10 的應用程式保護原則](../apps/app-protection-policies-configure-windows-10.md)。
3. [使用 Intune 建立及部署 WIP 應用程式保護原則](../apps/windows-information-protection-policy-create.md)。

## <a name="what-to-tell-employees-and-students"></a>員工和學生須知

在情況允許下，分享下列連結以提供其他資訊：

* [當 iOS/iPadOS 應用程式交由應用程式保護原則管理時的行為](../fundamentals/end-user-mam-apps-ios.md)
* [當 Android 應用程式交由應用程式防護原則管理時的行為](../fundamentals/end-user-mam-apps-android.md)

## <a name="next-steps"></a>後續步驟

需要啟用這個案例或其他 EMS 或 Office 365 案例的協助嗎？ 如果您至少有 Microsoft 365、Enterprise Mobility + Security 或 Azure Active Directory Premium 的 150 個授權，請使用 [FastTrack 權益](https://docs.microsoft.com/enterprise-mobility-security/solutions/enterprise-mobility-fasttrack-program)。

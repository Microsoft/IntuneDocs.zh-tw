---
title: 在 Intune 移轉期間設定裝置與應用程式合規性
titleSuffix: Microsoft Intune
description: 本文提供 Microsoft Intune 移轉期間設定裝置合規性和應用程式管理原則的必要步驟。
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 0062d08e-e5b3-4f73-8b64-5ad95adbe945
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 191be009f8d9e6fc448126834ef48f0bc6e2edc4
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72505337"
---
# <a name="configure-device-compliance-and-app-management-policies-when-migrating-to-microsoft-intune"></a>移轉至 Microsoft Intune 時設定裝置合規性和應用程式管理原則

移轉至 Intune 時的主要目標，是在 Intune 中註冊所有裝置，並使它們符合自身原則的規範。 裝置原則不僅可協助您管理公司擁有的單一使用者裝置，還包括個人 (BYOD) 和共用裝置，例如 Kiosk、銷售點的電腦、教室裡多個學生共用的平板電腦或無使用者裝置 (僅限 iOS)。

每個裝置平台可能會提供不同的設定，但 Intune 裝置原則由於提供下列行動裝置管理功能，因而可適用每個裝置平台︰

- 管理每個使用者註冊的裝置數目。

- 管理裝置設定 (例如裝置層級加密、密碼長度、相機使用方式)。

- 提供應用程式、電子郵件設定檔、VPN 設定檔等。

- 評估安全性合規性原則的裝置層級準則。

> [!IMPORTANT]
> 裝置管理原則不會直接指派給個別的裝置或使用者，而是指派給使用者群組。 原則可直接套用到使用者群組，從而套用到使用者的裝置；或原則可套用到裝置群組，從而套用到群組成員。

## <a name="task-list-for-device-compliance-policies"></a>裝置合規性原則的工作清單

### <a name="task-1-add-device-groups-optional"></a>工作 1：新增裝置群組 (選用)

當您需要執行以裝置身分識別 (而非使用者身分識別) 為基礎的管理工作時，可以建立裝置群組。

裝置群組適合用於管理無專任使用者的裝置 (如 Kiosk 裝置)、輪班工作人員共用的裝置，或指派給特定位置的裝置。

在裝置註冊前先設定裝置群組，就能在註冊時使用裝置類別將裝置自動加入群組。 接著它們會自動接收其群組的裝置原則。 [開始使用群組](groups-get-started.md)。

### <a name="task-2-use-resource-access-profiles-wi-fi-vpn-and-email-certificates"></a>工作 2：使用資源存取設定檔 (Wi-Fi、VPN 和電子郵件憑證)

資源存取設定檔會將憑證和存取設定提供給註冊的裝置。 如果您使用憑證式驗證，請[設定憑證](../protect/certificates-configure.md)。

### <a name="task-3-create-and-deploy-device-configuration-profiles"></a>工作 3：建立和部署裝置組態設定檔

您必須建立裝置組態設定檔以強制執行裝置層級設定，例如︰停用相機、App Store、設定單一應用程式模式及主畫面等。 了解[裝置設定檔](../configuration/device-profiles.md)。

#### <a name="directly-import-ios-configuration-profiles-optional"></a>直接匯入 iOS 組態設定檔 (選用)

- **Apple Configurator iOS 設定檔 (iOS 7.1 和更新版本)：** 如果您現有的 MDM 解決方案使用 Apple Configurator 設定檔 (.mobileconfig 檔案)，Intune 可直接將它們匯入為自訂組態原則。

- **iOS 行動應用程式組態原則︰** 如果您現有的 MDM 解決方案使用 iOS 行動應用程式組態原則，只要它們符合 Apple 指定之屬性清單的 XML 格式，Intune 即可直接匯入它們。

- 了解如何新增 [iOS](../configuration/custom-settings-ios.md) 的自訂原則。

### <a name="task-4-create-and-deploy-device-compliance-policies-optional"></a>工作 4：建立和部署裝置合規性原則 (選用)

裝置相容性原則可評估安全性導向設定，並提供顯示裝置是否符合公司標準規範的報告。 這類設定包括：

- PIN 長度

- JB 破解狀態

- OS 版本

請參閱裝置合規性設定的其他資源︰

- 了解[裝置合規性原則](../protect/device-compliance-get-started.md)。

### <a name="task-5-publish-and-deploy-apps"></a>工作 5：發佈和部署應用程式

使用 Intune MDM 時，您可以透過要求應用程式自動安裝或以在公司入口網站提供的方式來提供應用程式。

- [如何新增應用程式](../apps/apps-add.md)。

- [如何部署應用程式](../apps/apps-deploy.md)。

### <a name="task-6-enable-device-enrollment"></a>工作 6：啟用裝置註冊

您必須註冊裝置才能管理裝置。 了解[如何準備好註冊公司擁有和使用者個人的裝置](../enrollment/device-enrollment.md)。

## <a name="next-steps"></a>後續步驟

[設定應用程式保護原則 (選用)](../apps/app-protection-policies.md)。

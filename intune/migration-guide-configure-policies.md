---
title: "在 Intune 移轉期間設定裝置合規性與應用程式管理原則"
description: "本文旨在提供 Intune 移轉期間設定裝置合規性與應用程式管理原則的必要步驟。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 06/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0062d08e-e5b3-4f73-8b64-5ad95adbe945
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 5e848dda6643a28141a8f5f1d0bdc01f2bd9d390
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2017
---
# <a name="configure-device-compliance-and-app-management-policies"></a>設定裝置合規性與應用程式管理原則

[!INCLUDE[note for both-portals](./includes/note-for-both-portals.md)]

移轉至 Intune 時的主要目標，是註冊所有裝置，並使它們符合自身原則的規範。 裝置原則不僅可協助您管理公司擁有的單一使用者裝置，還包括個人 (BYOD) 和共用裝置，例如 Kiosk、銷售點的電腦、教室裡多個學生共用的平板電腦或無使用者裝置 (僅限 iOS)。

每個裝置平台可能會提供不同的設定，但 Intune 裝置原則由於提供下列行動裝置管理功能，因而可適用每個裝置平台︰

-   管理每個使用者註冊的裝置數目。

-   管理裝置設定 (如裝置層級加密、密碼長度、相機使用方式)。

-   提供應用程式、電子郵件設定檔、VPN 設定檔等。

-   評估安全性合規性原則的裝置層級準則。

> [!IMPORTANT]
> 裝置管理原則不會直接指派給個別的裝置或使用者，而是指派給使用者群組。 原則可直接套用到使用者群組，從而套用到使用者裝置；或原則可套用到裝置群組，從而套用到群組成員。

## <a name="task-list-for-device-compliance-policies"></a>裝置合規性原則的工作清單

### <a name="task-1-add-device-groups-optional"></a>工作 1：新增裝置群組 (選用)

當您需要執行以裝置身分識別 (而非使用者身分識別) 為基礎的各種管理工作時，可以建立裝置群組。

裝置群組適合用於管理無專任使用者的裝置 (如 Kiosk 裝置)，或是輪班工作人員共用或指派給特定位置的裝置。

在裝置註冊前先設定裝置群組，就能在註冊時利用裝置類別自動將裝置分組，以自動接收其群組的裝置原則。 [開始使用群組](/intune/groups-get-started)。

### <a name="task-2-use-resource-access-profiles-wi-fi-vpn-and-email-certificates"></a>工作 2︰使用資源存取設定檔 (Wi-Fi、VPN 和電子郵件憑證)

資源存取設定檔會將憑證和存取設定佈建到註冊的裝置。

如先前在＜評估 MDM 需求＞一節所述，如果您使用憑證式驗證，請[設定憑證](/intune/certificates-configure)。

### <a name="task-3-create-and-deploy-device-configuration-profiles"></a>工作 3：建立和部署裝置組態設定檔

您必須建立裝置組態設定檔以強制裝置層級設定，例如︰停用相機、App Store、設定單一應用程式模式及主畫面等。

- 了解[裝置設定檔](/intune/device-profiles)。

####  <a name="direct-import-of-ios-configuration-profiles-optional"></a>直接匯入 iOS 組態設定檔 (選用)

-   **Apple Configurator iOS 設定檔 (iOS 7.1 及更新版本)：**如果您現有的 MDM 解決方案使用 Apple Configurator 設定檔 (.mobileconfig 檔案)，Intune 可直接將它們匯入為自訂組態原則。

-   **iOS 行動應用程式組態原則︰**如果您現有的 MDM 解決方案使用 iOS 行動應用程式組態原則，只要它們符合 Apple 指定之屬性清單的 XML 格式，Intune 即可直接匯入它們。

- 了解如何新增 [iOS](/intune/custom-settings-ios) 的自訂原則

### <a name="task-4-create-and-deploy-device-compliance-policies-optional"></a>工作 4：建立和部署裝置合規性原則 (選用)

裝置合規性原則可評估安全性導向設定，並提供顯示裝置是否符合公司標準規範的報告。 裝置合規性原則可評估類似以下的安全性導向因素：

-   PIN 長度

-   JB 破解狀態

-   作業系統版本

請參閱裝置合規性設定的其他資源︰

-   了解[裝置合規性原則](/intune-classic/deploy-use/introduction-to-device-compliance-policies-in-microsoft-intune)。

-   了解[如何建立裝置合規性原則](/intune-classic/deploy-use/create-a-device-compliance-policy-in-microsoft-intune)。

### <a name="task-5-publish-and-deploy-apps"></a>工作 5︰發佈和部署應用程式

使用 Intune MDM 時，您可以透過要求應用程式自動安裝或以在公司入口網站提供的方式來佈建應用程式。

-   了解[如何新增應用程式](/intune-classic/deploy-use/add-apps)。

-   了解[如何部署應用程式](/intune-classic/deploy-use/deploy-apps)。

### <a name="task-6-enable-device-enrollment"></a>工作 6：啟用裝置註冊

註冊是以在裝置上佈建控制的方式建立管理。 了解[如何準備好註冊公司擁有和使用者個人的裝置](/intune/device-enrollment)。

## <a name="next-steps"></a>後續步驟 

[設定應用程式保護原則 (選用)](migration-guide-app-protection-policies.md)

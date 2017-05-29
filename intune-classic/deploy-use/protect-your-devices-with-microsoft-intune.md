---
title: "使用 Microsoft Intune 保護裝置 | Microsoft Docs"
description: "了解 Intune 可協助您針對未經授權存取和其他威脅保護您裝置的幾個方式。"
keywords: 
author: Robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/21/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 71e0cbf3-2bfb-412e-8a12-8503df08b4cf
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 042c5673c48bb19aacd624028260267670f9846e
ms.contentlocale: zh-tw
ms.lasthandoff: 05/23/2017


---

# <a name="protect-devices-with-microsoft-intune"></a>使用 Microsoft Intune 保護裝置

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Microsoft Intune 提供一組完整的功能，可協助您保護您所管理的裝置和儲存在這些裝置上的資料。 閱讀本主題來了解這些功能的基本概念，並找出深入了解的方法。

## <a name="general-ways-to-protect-all-devices"></a>保護所有裝置的一般方法

### <a name="device-configuration"></a>裝置設定
Intune [設定原則](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)藉由控制多項設定及功能，協助您保護及設定裝置。 例如：
- 您可以限制裝置上的硬體功能使用，例如相機或藍牙。
- 您可以設定相容和不相容的應用程式。 您會在安裝了不相容的應用程式時收到警示 (有些平台能夠實際阻止安裝)。

### <a name="reset-passcodes-when-users-are-locked-out-of-their-devices"></a>當使用者遭到鎖定而無法使用其裝置時重設密碼
保護行動裝置上的公司資料時，第一步就是要求密碼才能使用裝置，因此，您有時必須[重設密碼](use-remote-lock-and-passcode-reset-in-microsoft-intune.md)或協助員工執行這項操作，包括從遠端移除密碼或設定暫時密碼。 如果裝置遺失或遭竊，您也可以[從遠端鎖定裝置](use-remote-lock-and-passcode-reset-in-microsoft-intune.md)。

### <a name="retire-devices-and-remove-data"></a>淘汰裝置並移除資料
當裝置必須[從 Intune 管理中移除](retire-devices-from-microsoft-intune-management.md)時 (例如使用者離開，或裝置遺失或遭竊)，您可能會想從該裝置移除資料。 Intune 提供多種方法，以確保您的公司資料保持安全無虞。

### <a name="require-devices-to-be-compliant"></a>要求裝置符合規定
Intune 提供[裝置法務遵循政策](introduction-to-device-compliance-policies-in-microsoft-intune.md)，可讓您評估 (在某些情況下則為補救) 與您指定規則不相容的裝置。 例如，您可以回報遭破解的 iOS 裝置、裝置是否已加密，或健康情況證明服務是否將 Windows 10 裝置回報為狀況良好。

### <a name="protect-apps-and-the-data-they-use"></a>保護應用裝置及其使用的資料
Intune 為您提供多種功能以協助保護應用程式及其資料。 例如，行動應用程式管理 (MAM) 原則可禁止從受保護的應用程式備份資料、限制複製並貼到其他應用程式的作業、要求有 PIN 才能存取應用程式等。 如需保護應用程式的詳細資料，請參閱[使用 Microsoft Intune 保護應用程式和資料](protect-apps-and-data-with-microsoft-intune.md)

### <a name="add-an-additional-layer-of-protection-to-devices"></a>為裝置多加一層保護
[Multi-Factor Authentication (MFA)](multi-factor-authentication-azure-active-directory.md) 可以更安全地在網路上驗證裝置的使用者。  使用 MFA 時，除了使用者名稱和密碼之外，使用者還必須透過電話或簡訊來確認其身分識別。

## <a name="further-capabilities-for-windows-devices"></a>適用於 Windows 裝置的其他功能

### <a name="control-windows-hello-for-business-settings-on-windows-devices"></a>控制 Windows 裝置上的 Windows Hello 企業版設定
Intune 可讓您與 [Windows Hello 企業版](control-microsoft-passport-settings-on-devices-with-microsoft-intune.md) (原稱為 Microsoft Passport) 整合，這是使用 Active Directory 或 Azure Active Directory 帳戶取代密碼、智慧卡或虛擬智慧卡來登入 Windows 10 和更新版本的替代方法。

## <a name="further-capabilities-for-ios-devices"></a>適用於 iOS 裝置的其他功能

### <a name="bypass-activation-lock-on-ios-devices"></a>在 iOS 裝置上略過啟用鎖定
啟用鎖定是一項協助保護使用者裝置的功能，其方法是在任何人清除或重新啟用裝置之前，要求其先輸入 Apple ID 及密碼。 不過，這可能會導致問題，例如，如果使用者離職卻未移除鎖定。 [iOS 啟用鎖定略過](help-protect-ios-devices-with-activation-lock-bypass-for-microsoft-intune.md)可以移除受監督的 iOS 裝置鎖定，幫助您重新配置或將它們清除。



## <a name="protect-windows-pcs-managed-with-the-intune-client"></a>保護使用 Intune 用戶端管理的 Windows 電腦
對於您未註冊但以 Intune 電腦用戶端軟體管理的 Windows 電腦，Intune 持續支援安全性原則。 若要了解這些原則如何協助保護 Windows 電腦，請參閱[使用原則來協助保護執行 Intune 用戶端軟體的 Windows 電腦](policies-to-protect-windows-pcs-in-microsoft-intune.md)。


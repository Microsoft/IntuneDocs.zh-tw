---
title: 使用 Microsoft Intune 保護裝置
titleSuffix: Microsoft Intune
description: 了解 Intune 可協助您針對未經授權存取和其他威脅保護您裝置的幾個方式。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 07/19/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 19cad6ede0f3d3fb87e067d6bdcdfa5adf0219bf
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2019
ms.locfileid: "71721405"
---
# <a name="protect-devices-with-microsoft-intune"></a>使用 Microsoft Intune 保護裝置

Microsoft Intune 可協助您保護自己所管理的裝置，以及儲存在這些裝置上的資料。

## <a name="device-configuration"></a>裝置設定
Intune [設定原則](../configuration/device-profiles.md)藉由控制多項設定及功能，協助您保護及設定裝置。 例如：

- 您可以限制裝置上的硬體功能使用，例如相機或藍牙。
- 您可以設定相容和不相容的應用程式。 您會在安裝了不相容的應用程式時收到警示 (有些平台能夠實際阻止安裝)。

## <a name="reset-passcodes-when-users-are-locked-out-of-their-devices"></a>當使用者遭到鎖定而無法使用其裝置時重設密碼
保護行動裝置上的公司資料時，第一步就是要求密碼才能使用裝置，因此，您有時必須[重設密碼](../remote-actions/device-passcode-reset.md)或協助員工執行這項操作，包括從遠端移除密碼或設定暫時密碼。 如果裝置遺失或遭竊，您也可以[從遠端鎖定裝置](../remote-actions/device-remote-lock.md)。

## <a name="retire-devices-and-remove-data"></a>淘汰裝置並移除資料
當裝置必須[從 Intune 管理中移除](../remote-actions/devices-wipe.md)時 (例如使用者離開，或裝置遺失或遭竊)，您可能會想從該裝置移除資料。 Intune 提供多種方法，來確保您的公司資料時時安全無虞。

## <a name="require-devices-to-be-compliant"></a>要求裝置符合規定
Intune 提供[裝置法務遵循政策](device-compliance-get-started.md)，可讓您評估 (在某些情況下則為補救) 不符合您指定規則之規範的裝置。 例如，您可取得以下項目的報告：
- 已越獄的 iOS 裝置
- 加密或未加密的裝置
- Window 10 裝置的健康情況 (同運作狀況證明服務判斷)。

## <a name="protect-apps-and-the-data-they-use"></a>保護應用裝置及其使用的資料
Intune 為您提供多種功能以協助保護應用程式及其資料。 例如，行動應用程式管理 (MAM) 原則可以：
- 防止受保護應用程式的資料受到備份
- 限制其他應用程式的複製和貼上
- 要求在存取應用程式時提供 PIN。如需詳細資訊，請參閱[使用 Microsoft Intune 保護應用程式和資料](../apps/app-protection-policy.md)

## <a name="add-an-additional-layer-of-protection-to-devices"></a>為裝置多加一層保護
[Multi-Factor Authentication (MFA)](../enrollment/multi-factor-authentication.md) 可以更安全地在網路上驗證裝置的使用者。  使用 MFA 時，除了使用者名稱和密碼之外，使用者還必須透過電話或簡訊來確認其身分識別。

## <a name="control-windows-hello-for-business-settings-on-windows-devices"></a>控制 Windows 裝置上的 Windows Hello 企業版設定
Intune 可讓您與 [Windows Hello 企業版](windows-hello.md)整合，這是使用 Active Directory 或 Azure Active Directory 帳戶取代密碼、智慧卡或虛擬智慧卡來登入 Windows 10 和更新版本的替代方法。

## <a name="bypass-activation-lock-on-ios-devices"></a>在 iOS 裝置上略過啟用鎖定
「啟用鎖定」是一項能協助保護使用者裝置的功能。 這項功能會要求使用者必須先輸入其 Apple ID 和密碼，才能清除或重新啟用裝置。 不過，這項功能也可能會產生問題，例如使用者離職卻未移除鎖定的狀況。 [iOS 啟用鎖定略過](../remote-actions/device-activation-lock-bypass.md)可以移除受監督的 iOS 裝置鎖定，幫助您重新配置或將它們清除。

## <a name="next-steps"></a>後續步驟

深入了解 [Mobile Threat Defense](mobile-threat-defense.md)

---
title: "保護裝置 | Microsoft Intune"
description: "了解 Intune 可協助您針對未經授權存取和其他威脅保護您裝置的幾個方式。"
keywords: 
author: Robstackmsft
manager: arob98
ms.date: 07/13/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 71e0cbf3-2bfb-412e-8a12-8503df08b4cf
ms.reviewer: mghadial
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: a409d36c1c5fcfd3d81ce0cbdf1f69af4747157a
ms.openlocfilehash: 53201c36e7a210c1c62d3ed3183093ed8e63dc53


---

# 使用 Microsoft Intune 保護裝置
使用 Intune 保護裝置之後，您會想要確定裝置不受到未經授權存取和其他威脅。 以下是 Intune 協助達成這些目標是一些功能。

> [!TIP]
> 本主題並未完整囊括 Intune 可協助保護裝置的一切方法。 例如，您可以使用 Intune 原則來為裝置設定許多安全性設定，例如設定密碼、加密設定和硬體功能，例如藍芽與裝置相機。 若要深入了解這些設定，請參閱[透過 Microsoft Intune 管理裝置上的設定和功能](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)。

## 當使用者遭到鎖定而無法使用其裝置時重設密碼
保護行動裝置上的公司資料時，第一步就是要求密碼才能使用裝置，因此，您有時必須[重設密碼](use-remote-lock-and-passcode-reset-in-microsoft-intune.md)或協助員工執行這項操作，包括從遠端移除密碼或設定暫時密碼。 如果裝置遺失或遭竊，您也可以[從遠端鎖定裝置](use-remote-lock-and-passcode-reset-in-microsoft-intune.md)。

## 為 Windows 裝置多加一層保護
[Multi-Factor Authentication (MFA)](protect-windows-devices-with-multi-factor-authentication.md) 可以更安全地在網路上驗證 Windows 和 Windows Phone 裝置的使用者。  使用 MFA 時，除了使用者名稱和密碼之外，使用者還必須透過電話或簡訊確認其身分識別。

## 控制 Windows 裝置上的 Microsoft Passport 設定
Intune 可讓您與 [Microsoft Passport for Work](control-microsoft-passport-settings-on-devices-with-microsoft-intune.md) 整合，這是使用 Active Directory 或 Azure Active Directory 帳戶取代密碼、智慧卡或虛擬智慧卡來登入 Windows 10 和更新版本的替代方法。

## 在 iOS 裝置上略過啟用鎖定
[啟用鎖定] 是一項協助保護使用者裝置的功能，其方法是在任何人清除或重新啟用裝置之前，要求其先輸入 Apple ID 及密碼。 不過，這可能會導致問題，例如，如果使用者離職卻未移除鎖定。 [iOS 啟用鎖定略過](help-protect-ios-devices-with-activation-lock-bypass-for-microsoft-intune.md)可以移除受監督的 iOS 裝置鎖定，幫助您重新配置或將它們清除。

## 保護使用 Intune 用戶端管理的 Windows 電腦
對於您未註冊但以 Intune 電腦用戶端軟體管理的 Windows 電腦，Intune 持續支援安全性原則。 若要了解這些原則如何協助保護 Windows 電腦，請參閱[使用原則來協助保護執行 Intune 用戶端軟體的 Windows 電腦](policies-to-protect-windows-pcs-in-microsoft-intune.md)。



<!--HONumber=Jul16_HO3-->



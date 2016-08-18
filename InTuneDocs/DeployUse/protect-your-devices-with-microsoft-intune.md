---
title: "保護裝置 | Microsoft Intune"
description: "了解 Intune 可協助您針對未經授權存取和其他威脅保護您裝置的幾個方式。"
keywords: 
author: Robstackmsft
manager: angrobe
ms.date: 07/13/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 71e0cbf3-2bfb-412e-8a12-8503df08b4cf
ms.reviewer: mghadial
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: c999a852b68762002ac94269e27ecbf46c8f9999
ms.openlocfilehash: 3318590eaedc6f0e96fb463dc016d5786eeb38fb


---

# 使用 Microsoft Intune 保護裝置
使用 Intune 管理裝置之後，您會想要確定裝置不受未經授權存取和其他威脅。 以下是 Intune 協助達成這些目標是一些功能。

> [!TIP]
> 本主題並未完整囊括 Intune 可協助保護裝置的一切方法。 例如，您可以使用 Intune 原則來為裝置設定許多安全性設定，例如密碼、加密設定和硬體功能，例如藍牙與裝置的相機。 若要深入了解這些設定，請參閱[透過 Microsoft Intune 管理裝置上的設定和功能](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)。

## 當使用者遭到鎖定而無法使用其裝置時重設密碼
保護行動裝置上之公司資料的第一個步驟，是需要有密碼才能使用該裝置。 有時候您必須[重設密碼](use-remote-lock-and-passcode-reset-in-microsoft-intune.md)或協助員工執行這項操作，這可藉由移除密碼，或從遠端設定新的暫時密碼來完成。 如果裝置遺失或遭竊，您也可以[從遠端鎖定裝置](use-remote-lock-and-passcode-reset-in-microsoft-intune.md)。

## 為 Windows 裝置多加一層保護
[Multi-Factor Authentication (MFA)](protect-windows-devices-with-multi-factor-authentication.md) 可以更安全地在網路上驗證 Windows 和 Windows Phone 裝置的使用者。 使用 MFA 時，除了使用者名稱和密碼之外，使用者還必須透過電話或簡訊來確認其身分識別。

## 控制 Windows 裝置上的 Microsoft Passport 設定
將 Intune 與 [Microsoft Passport for Work](control-microsoft-passport-settings-on-devices-with-microsoft-intune.md) 整合。 這是另一個登入 Windows 10 和更新版本的方法。 Microsoft Passport for Work 使用 Active Directory 或 Azure Active Directory 帳戶取代密碼、智慧卡或虛擬智慧卡。

## 在 iOS 裝置上略過啟用鎖定
[啟用鎖定] 是一項協助保護使用者裝置的功能，其方法是在任何人清除或重新啟動裝置之前，要求其先輸入 Apple ID 及密碼。 不過，如果在使用者離職卻未移除鎖定之類的情況下，這可能會導致問題。 [iOS 啟用鎖定略過](help-protect-ios-devices-with-activation-lock-bypass-for-microsoft-intune.md)可以移除受監督的 iOS 裝置鎖定，讓您得以進行重新配置或將它們清除。

## 保護使用 Intune 用戶端管理的 Windows 電腦
對於您未註冊但以 Intune 電腦用戶端軟體管理的 Windows 電腦，Intune 持續支援安全性原則。 若要了解這些原則如何協助保護 Windows 電腦，請參閱[使用原則來協助保護執行 Intune 用戶端軟體的 Windows 電腦](policies-to-protect-windows-pcs-in-microsoft-intune.md)。



<!--HONumber=Aug16_HO2-->



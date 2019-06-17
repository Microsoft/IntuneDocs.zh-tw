---
title: 設定 Android Enterprise 完全受控裝置的 Intune 註冊
titleSuffix: Microsoft Intune
description: 了解如何在 Intune 中註冊 Android Enterprise 完全受控裝置。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 1/15/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: f1b1197671b54cb5374bd79b6acbeb8137c0135c
ms.sourcegitcommit: cc5d757018d05fc03ac9ea3d30f563df9bfd61ed
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/10/2019
ms.locfileid: "66819885"
---
# <a name="set-up-intune-enrollment-of-android-enterprise-fully-managed-devices-preview"></a>設定 Android Enterprise 完全受控裝置的 Intune 註冊 (預覽)

Android Enterprise 完全受控裝置為與單一使用者建立關聯且為公司擁有的裝置，並僅供工作而非個人用途使用。 管理員可以管理整個裝置，並強制原則控制無法用於工作設定檔，例如：
- 僅允許從受控 Google Play 安裝應用程式
- 禁止解除安裝受控應用程式
- 防止使用者將裝置恢復出廠預設值等。

Intune 可協助您將應用程式及設定部署至 Android Enterprise 裝置，包含 Android Enterprise 完全受控裝置。 如需 Android Enterprise 的特定詳細資料，請參閱 [Android Enterprise requirements](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012) (Android Enterprise 需求)。

## <a name="technical-requirements"></a>技術需求

您必須擁有 Intune 獨立租用戶才能管理 Android Enterprise 完全受控裝置。 在混合 (連接 Configuration Manager) 模式或舊版 Silverlight 管理主控台中，皆無法使用完全受控裝置管理。

裝置必須符合下列需求，才能作為 Android Enterprise 完全受控裝置管理：

- Android OS 5.1 版和更新版本。
- 裝置必須執行具有 Google 行動服務 (GMS) 連線的 Android 組建。 裝置必須有可用的 GMS ，而且必須能夠連線至 GMS。

若符合以上需求，則不限裝置製造商/OEM。

## <a name="set-up-android-enterprise-fully-managed-device-management"></a>設定 Android Enterprise 完全受控裝置管理

若要設定 Android Enterprise 完全受控裝置管理，請遵循下列步驟：

1. 為準備管理行動裝置，您必須[將行動裝置管理 (MDM) 授權單位設定為 **Microsoft Intune**](mdm-authority-set.md)。 此項目只會設定一次，也就是第一次為行動裝置管理設定 Intune 之時。
2. [將 Intune 租用戶帳戶連線至 Android Enterprise 帳戶](connect-intune-android-enterprise.md)。
3. [啟用公司擁有的使用者裝置](#enable-corporate-owned-user-devices)
4. [註冊完全受控裝置](#enroll-the-fully-managed-devices)。

### <a name="enable-corporate-owned-user-devices"></a>啟用公司擁有的使用者裝置

1. 登入 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)，然後選擇 [裝置註冊]   > [Android 註冊]   > [Corporate-owned, fully managed user devices] \(公司擁有的完全受控使用者裝置 (預覽)\)  。
2. 在 [允許使用者註冊公司擁有的使用者裝置]  下，選擇 [是]  。

[!NOTE]
如已定義 Azure AD 條件式存取原則使用「需要標記為合規的裝置」  控制項，並適用於**所有雲端應用程式**、**Android** 和**瀏覽器** - 您必須從此原則排除 **Microsoft Intune** 的雲端應用程式。 這是因為 Android 安裝程式程序在註冊期間會使用 Chrome 的索引標籤來驗證使用者。 如需詳細資訊，請參閱 [Azure AD 條件式存取文件](https://docs.microsoft.com/azure/active-directory/conditional-access/)。

當此項設定為 [是]  時，會提供您 Intune 租用戶的註冊權杖 (隨機字串) 及 QR 代碼。 此單一註冊權杖對您所有的使用者都有效，而且不會到期。 視 Android OS 和裝置的版本而定，您可以使用權杖或 QR 代碼註冊 kiosk 裝置。

## <a name="enroll-the-fully-managed-devices"></a>註冊完全受控裝置
您現在可以[註冊您的完全受控裝置](android-dedicated-devices-fully-managed-enroll.md)。

## <a name="considerations-for-this-preview-feature"></a>此預覽功能的考量
此公開預覽包含一套 Android Enterprise 完全受控解決方案組的核心功能。 我們想了解您使用這項預覽功能的體驗情形，您可使用目前與小組間的任何通訊通道與我們分享 (例如 [UserVoice](https://microsoftintune.uservoice.com/forums/291681-ideas?category_id=210853))。

此預覽支援下列 Android Enterprise 完全受控裝置功能：
- 使用 NFC、權杖項目、QR 代碼及零接觸來註冊裝置
- 為使用者群組設定裝置
- 為使用者群組發佈及設定應用程式


使用這些預覽功能時，請謹記以下事項：
- 預覽中的功能不建議用於任務關鍵性或生產環境部署。 
- 預覽功能會對 Microsoft Intune 生產環境標準實作。 不過，並非所有 Intune 功能皆適用於 Android Enterprise 完全受控使用者裝置。 預覽功能在 Intune 主控台中會清楚地標記著「(預覽)」。 
- 一般 Intune 支援通道會完整支援預覽功能。
- 預覽中不支援使用 Samsung Knox 行動裝置註冊來註冊 Android Enterprise 完全受控裝置。 
- 不支援在 Android Enterprise 完全受控裝置上使用 Intune 公司入口網站應用程式。 
- 預覽中不支援條件式存取、應用程式保護原則、憑證部署等 Intune 功能。 
- 預覽中不支援任何設定檔或應用程式將目標設為裝置群組。 僅支援將目標設為使用者群組。 
- 用來設定電子郵件、WiFi 或 VPN 的第一級 UI 並不存在。 使用應用程式設定原則，進行支援的應用程式組態設定。

## <a name="next-steps"></a>後續步驟
- [新增 Android Enterprise 完全受控裝置設定原則](device-restrictions-android-for-work.md#device-owner-only)
- [設定 Android Enterprise 完全受控裝置的應用程式設定原則](app-configuration-policies-use-android.md)


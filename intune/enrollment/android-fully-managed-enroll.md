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
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: priyar
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: c5cd8c1a1d17ca38c42b6ed6821d20367b147ad6
ms.sourcegitcommit: 73b362173929f59e9df57e54e76d19834f155433
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/27/2019
ms.locfileid: "74562372"
---
# <a name="set-up-intune-enrollment-of-android-enterprise-fully-managed-devices"></a>設定 Android Enterprise 完全受控裝置的 Intune 註冊 

Android Enterprise 完全受控裝置為與單一使用者建立關聯且為公司擁有的裝置，並僅供工作而非個人用途使用。 管理員可以管理整個裝置，並強制原則控制無法用於工作設定檔，例如：
- 僅允許從受控 Google Play 安裝應用程式。
- 禁止解除安裝受控應用程式。
- 防止使用者為裝置恢復出廠預設值等。

Intune 可協助您將應用程式及設定部署至 Android Enterprise 裝置，包含 Android Enterprise 完全受控裝置。 如需 Android Enterprise 的特定詳細資料，請參閱 [Android Enterprise requirements](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012) (Android Enterprise 需求)。

## <a name="technical-requirements"></a>技術需求

您必須擁有 Intune 獨立租用戶才能管理 Android Enterprise 完全受控裝置。 在混合 (連接 Configuration Manager) 模式或舊版 Silverlight 管理主控台中，皆無法使用完全受控裝置管理。

裝置必須符合下列需求，才能作為 Android Enterprise 完全受控裝置管理：

- Android OS 6.0 版和更高版本。
- 裝置必須執行具有 Google 行動服務 (GMS) 連線的 Android 組建。 裝置必須有可用的 GMS ，而且必須能夠連線至 GMS。

若符合以上需求，則不限裝置製造商/OEM。

## <a name="set-up-android-enterprise-fully-managed-device-management"></a>設定 Android Enterprise 完全受控裝置管理

若要設定 Android Enterprise 完全受控裝置管理，請遵循下列步驟：

1. 為準備管理行動裝置，您必須[將行動裝置管理 (MDM) 授權單位設定為 **Microsoft Intune**](../fundamentals/mdm-authority-set.md)。 此項目只會設定一次，也就是第一次為行動裝置管理設定 Intune 之時。
2. [將 Intune 租用戶帳戶連線至 Android Enterprise 帳戶](connect-intune-android-enterprise.md)。
3. [啟用公司擁有的使用者裝置](#enable-corporate-owned-user-devices)
4. [註冊完全受控裝置](#enroll-the-fully-managed-devices)。

### <a name="enable-corporate-owned-user-devices"></a>啟用公司擁有的使用者裝置

1. 登入 [Microsoft 端點管理員系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)，然後選擇 [裝置]   > [Android]   > [Android 註冊]    > [公司擁有、完全受控的使用者裝置]  。
2. 在 [允許使用者註冊公司擁有的使用者裝置]  下，選擇 [是]  。

> [!NOTE]
> 如已定義 Azure AD 條件式存取原則使用「需要標記為合規的裝置」  控制項，並適用於**所有雲端應用程式**、**Android** 和**瀏覽器** - 您必須從此原則排除 **Microsoft Intune** 的雲端應用程式。 這是因為 Android 安裝程式程序在註冊期間會使用 Chrome 的索引標籤來驗證使用者。 如需詳細資訊，請參閱 [Azure AD 條件式存取文件](https://docs.microsoft.com/azure/active-directory/conditional-access/)。

當此項設定為 [是]  時，會提供您 Intune 租用戶的註冊權杖 (隨機字串) 及 QR 代碼。 此單一註冊權杖對您所有的使用者都有效，而且不會到期。 視裝置的 Android OS 和版本而定，您可以使用權杖或 QR 代碼來註冊裝置。

## <a name="enroll-the-fully-managed-devices"></a>註冊完全受控裝置
您現在可以[註冊您的完全受控裝置](android-dedicated-devices-fully-managed-enroll.md)。

## <a name="next-steps"></a>後續步驟
- [新增 Android Enterprise 完全受控裝置設定原則](../configuration/device-restrictions-android-for-work.md#device-owner-only)
- [設定 Android Enterprise 完全受控裝置的應用程式設定原則](../apps/app-configuration-policies-use-android.md)


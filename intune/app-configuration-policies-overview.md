---
title: Microsoft Intune 的應用程式設定原則
titleSuffix: ''
description: 了解在 Microsoft Intune 中如何於 iOS 或 Android 裝置上使用應用程式設定原則。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/08/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 834B4557-80A9-48C0-A72C-C98F6AF79708
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 10dad24ee41f63dcc304d95e9b733f7de3f1b71a
ms.sourcegitcommit: 1b7ee2164ac9490df4efa83c5479344622c181b5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/08/2019
ms.locfileid: "67649032"
---
# <a name="app-configuration-policies-for-microsoft-intune"></a>Microsoft Intune 的應用程式設定原則

使用 Microsoft Intune 中的應用程式設定原則，提供 iOS 或 Android 應用程式的組態設定。 這些組態設定允許使用業界標準的應用程式設定及管理方式來自訂應用程式。 每當應用程式檢查是否有設定原則設定時 (通常是第一次執行時)，便會使用這些設定。

您可以使用包含與排除指派的組合，將應用程式設定原則指派給一群使用者和裝置。 新增應用程式設定原則後，就可以設定指派應用程式設定原則。 當您設定原則指派時，您可以選擇包含與排除要套用原則的使用者群組。 當您選擇要包含一或多個群組時，您可以選擇選取要包含特定群組或選取內建群組。 內建群組包括 [所有使用者]  、[所有裝置]  和 [所有使用者及所有裝置]  。

例如，應用程式組態設定可能需要您指定下列任何詳細資料：

- 自訂連接埠號碼
- 語言設定
- 安全性設定
- 公司標誌等品牌設定

如果使用者改為輸入這些設定，他們可能會做錯而增加技術支援中心的負擔，並拖慢新應用程式的採用速度。

應用程式設定原則可讓您在使用者執行應用程式之前，將組態設定指派給已指派給使用者的原則來去除應用程式設定問題。 這些設定會自動提供，使用者無須採取任何動作。

每當應用程式檢查是否有組態設定時，便會使用這些設定。 一般而言，應用程式會在使用者第一次執行應用程式時檢查是否有組態設定。

對於如何使用 Intune 的應用程式設定，您有兩個選項：
 - **受控裝置** - Intune 以行動裝置管理 (MDM) 提供者身分管理裝置。
 - **受控應用程式** - 在不註冊裝置的情況下管理應用程式。

> [!NOTE]
> 身為 Microsoft Intune 系統管理員，您可以控制在受控裝置上要新增至 Microsoft Office 應用程式的使用者帳戶。 您可以僅允許組織使用者帳戶進行存取，並封鎖已註冊裝置上的個人帳戶。 支援的應用程式會處理應用程式設定和移除，並封鎖未經核准的帳戶。

## <a name="apps-that-support-app-configuration"></a>支援應用程式設定的應用程式

### <a name="managed-devices"></a>受管理的裝置
您可以針對支援應用程式設定的應用程式，使用應用程式設定原則。 若要在 Intune 中支援應用程式設定，必須撰寫應用程式以支援使用由 [Appconfig 社群](https://www.appconfig.org/members) \(英文\) 所定義的應用程式設定。 如需詳細資料，請洽詢您的應用程式廠商。

### <a name="managed-apps"></a>受管理的應用程式
將 Intune App SDK 併入應用程式，或在開發應用程式之後包裝應用程式，就可以準備好企業營運應用程式。 Intune 應用程式 SDK (適用於 iOS 和 Android) 可讓您的應用程式使用 Intune 應用程式保護設定原則。 它會盡力將應用程式開發人員所需的程式碼變更數量減到最少。 如需詳細資訊，請參閱 [Intune App SDK 概觀](app-sdk.md)。

## <a name="graph-api-support-for-app-configuration"></a>應用程式設定的圖形 API 支援

此外，您也可以使用圖形 API 來完成應用程式設定工作。 如需詳細資料，請參閱 [Graph API Reference MAM Targeted Config](https://graph.microsoft.io/docs/api-reference/beta/api/intune_mam_targetedmanagedappconfiguration_create) (以圖形 API 參考 MAM 為目標的設定)。

## <a name="next-steps"></a>後續步驟

### <a name="managed-devices"></a>受管理的裝置

 - 了解如何在 iOS 裝置上使用應用程式設定。  請參閱[為受控 iOS 裝置新增應用程式設定原則](app-configuration-policies-use-ios.md)。
 - 了解如何在 Android 裝置上使用應用程式設定。  請參閱[為受管理的 Android 裝置新增應用程式設定原則](app-configuration-policies-use-android.md)。

### <a name="managed-apps"></a>受管理的應用程式

 - 了解如何在受管理的應用程式上使用應用程式設定。 請參閱[在不註冊裝置的情況下新增受管理應用程式的應用程式設定原則](app-configuration-policies-managed-app.md)。

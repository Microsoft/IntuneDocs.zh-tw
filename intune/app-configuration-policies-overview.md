---
title: "Intune 的應用程式設定原則 | Microsoft Docs"
titlesuffix: Azure portal
description: "了解如何使用 Intune 的應用程式設定原則。"
keywords: 
author: erikre
ms.author: erikre
manager: dougeby
ms.date: 10/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 834B4557-80A9-48C0-A72C-C98F6AF79708
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: d7267de95d36ed0e27c8a720599cc78004cd71d3
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2018
---
# <a name="app-configuration-policies-for-intune"></a>Intune 的應用程式設定原則

使用 Microsoft Intune 中的應用程式設定原則，提供使用者執行 iOS 或 Android 應用程式時的設定。 例如，應用程式可能需要使用者指定：

- 自訂連接埠號碼。
- 語言設定。
- 安全性設定。
- 公司標誌等品牌設定。

若使用者未正確輸入這些設定，可能會增加技術支援中心的負擔，使得採用新應用程式的速度變慢。

應用程式組態原則可讓您在使用者執行應用程式之前，將這些設定指派給使用者來避開這些問題。 這些設定會自動提供，使用者無須採取任何動作。

您不會直接將這些原則部署給使用者與裝置。 而是將原則與應用程式關聯，然後再指派應用程式。 每當應用程式檢查是否有原則設定時 (通常於初次執行時)，都會加以使用。

對於如何使用 Intune 的應用程式設定，您有兩個選項：
 - **受管理的裝置**  
   Intune 以行動裝置管理 (MDM) 提供者身分管理裝置。
 - **受管理的應用程式**  
   在不註冊裝置的情況下管理應用程式。

## <a name="apps-that-support-app-configuration"></a>支援應用程式設定的應用程式

您可以針對支援應用程式設定的應用程式，使用應用程式設定原則。 為了在 Intune 中支援應用程式設定，　必須撰寫應用程式，才能支援使用應用程式設定。 如需詳細資料，請洽詢您的應用程式廠商。

將 Intune App SDK 併入應用程式，或在開發應用程式之後包裝應用程式，就可以準備好企業營運應用程式。 Intune App SDK (適用於 iOS 和 Android) 可啟用應用程式的 Intune 應用程式保護原則。 它會盡力將應用程式開發人員所需的程式碼變更數量減到最少。 如需詳細資訊，請參閱 [Intune App SDK 概觀](app-sdk.md)。

## <a name="graph-api-support-for-app-configuration"></a>應用程式設定的圖形 API 支援

此外，您也可以使用圖形 API 來完成應用程式設定工作。 如需詳細資料，請參閱 [Graph API Reference MAM Targeted Config](https://graph.microsoft.io/docs/api-reference/beta/api/intune_mam_targetedmanagedappconfiguration_create) (以圖形 API 參考 MAM 為目標的設定)。

## <a name="next-steps"></a>接下來的步驟

### <a name="managed-devices"></a>受管理的裝置

 - 了解如何在 iOS 裝置上使用應用程式設定。  請參閱[為受管理的 iOS 裝置新增應用程式設定原則](app-configuration-policies-use-ios.md)。
 - 了解如何在 Android 裝置上使用應用程式設定。  請參閱[為受管理的 Android 裝置新增應用程式設定原則](app-configuration-policies-use-android.md)。

### <a name="managed-apps"></a>受管理的應用程式

 - 了解如何在受管理的應用程式上使用應用程式設定。 請參閱[在不註冊裝置的情況下新增受管理應用程式的應用程式設定原則](app-configuration-policies-managed-app.md)。
---
title: "您的 Android 裝置似乎已加密"
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 05/25/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ba593c08-1a78-4013-8525-b45a948772ec
searchScope: User help
ROBOTS: 
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 269ad7968242f8f5ce7095c9c73347987675e846
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2017
---
# <a name="your-android-device-seems-to-be-encrypted-but-company-portal-says-otherwise"></a>您的 Android 裝置似乎已加密，但公司入口網站的說法不同

當您加密裝置時，使用只有您知道的祕密金鑰來對裝置上的資訊進行編碼，以防止未經授權的人員存取它。 貴組織需要您先加密 Android 裝置才能存取公司檔案、電子郵件或資料，此為確保資訊安全的步驟。

## <a name="common-issues"></a>常見問題

較新版本的 Android (特別從 v7.0 開始) 需要一個啟動密碼來確定您的裝置已完全加密。 不同的裝置製造商對於啟動密碼會有不同的描述與位置。 在大部分的情況下，這稱為「安全啟動」。 

## <a name="solutions"></a>解決方案

### <a name="add-a-startup-pin"></a>新增啟動 PIN

某些 Android 裝置將要求您建立啟動 PIN 以確保裝置的安全。 有許多來自許多不同製造商的 Android 版本。 您可以嘗試在設定應用程式中尋找啟用此選項的位置，藉以修正此問題。 例如，在 Samsung Galaxy S7 中，您可以前往 [設定] > [鎖定螢幕與安全性] > [安全啟動]，來啟用「安全啟動」。  

### <a name="downgrade-your-version-of-android"></a>將您的 Android 版本降級
如果您的裝置提供降級為 Android 6.0+ 的選項，請執行這些動作。 萬一您嘗試將裝置降級，會有資料遺失的風險。 否則，我們建議您連絡您的 IT 管理員以解決此問題。 您可以在[公司入口網站](http://portal.manage.microsoft.com)取得您的 IT 管理員連絡資訊。

## <a name="specific-manufacturer-issues"></a>特定製造商問題

某些版本 7.0+ 的 Android 裝置加密資料的方式與特定 Android 平台標準不一致。 這些裝置可能會看似已經加密，但是 Intune 將使用的方法視為裝置資訊有可能會遭到可實際存取裝置的惡意使用者竊取的風險。

> [!Note]
> Microsoft 會與製造商合作來解決我們在測試時所發現的任何問題，或是使用者回報給我們的任何問題。 有新的資訊可供使用時，我們將更新本文。 

## <a name="known-devices"></a>已知的裝置

### <a name="known-devices-that-can-be-updated-to-fix-this-issue"></a>已知可更新以修正此問題的裝置

如果您擁有下列其中一個裝置，而且未將該裝置更新至最新版的 Android，可能就會遇到此問題。 您可以前往 [設定] > [更新] 來安裝這些裝置的更新。 

- [華為榮耀 8](http://consumer.huawei.com/en/support/mobile-phones/honor8_en-sup.htm)
- [華為 P9](http://consumer.huawei.com/mobile-phones/p9/index.html)

### <a name="known-devices-that-currently-cannot-be-updated-to-fix-this-issue"></a>已知目前無法透過更新來修正此問題的裝置

- [Huawei Mate 8](http://consumer.huawei.com/en/mobile-phones/mate8/index.htm) \(英文\)
- [小米 Mi 智慧型手機](https://xiaomi-mi.com/mi-smartphones/) \(英文\)

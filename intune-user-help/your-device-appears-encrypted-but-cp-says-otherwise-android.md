---
title: "您的 Android 裝置似乎已加密 | Microsoft Docs"
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 11/14/2017
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
ms.openlocfilehash: 04ce17615055d67f38e49158bec806de9f322bfd
ms.sourcegitcommit: dc2595bec05206a826cd10cb834bf6043145c917
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/14/2017
---
# <a name="your-android-device-seems-to-be-encrypted-but-company-portal-says-otherwise"></a>您的 Android 裝置似乎已加密，但公司入口網站的說法不同

當您加密裝置時，請使用只有您知道的祕密金鑰編碼裝置上的資訊。 這可防止未經授權的人員存取它。 許多組織會要求使用者先加密 Android 裝置，才能存取公司的檔案、電子郵件或資料。

## <a name="common-issues"></a>常見問題

較新版本的 Android (特別從 v7.0 開始) 需要一個啟動密碼來確定您的裝置已完全加密。 不同的裝置製造商對於啟動密碼會有不同的描述與位置。 此設定大多稱之為「安全啟動」。 

## <a name="solutions"></a>解決方案

### <a name="add-a-startup-pin"></a>新增啟動 PIN

某些 Android 裝置會要求您建立啟動 PIN 以確保裝置的安全。 有許多來自許多不同製造商的 Android 版本。 您可以嘗試在設定應用程式中尋找啟用此選項的位置，藉以修正此問題。 例如，在 Samsung Galaxy S7 中，您可以前往 [設定] > [鎖定螢幕與安全性] > [安全啟動]，來啟用「安全啟動」。  

### <a name="downgrade-your-version-of-android"></a>將您的 Android 版本降級

如果您的裝置提供降級為 Android 6.0+ 的選項，請執行這些動作。 萬一您嘗試將裝置降級，會有資料遺失的風險。 因此，建議您連絡公司支援人員以解決此問題。 您可以在[公司入口網站](https://portal.manage.microsoft.com)取得您公司支援人員的連絡資訊。

### <a name="encrypt-the-entire-device"></a>加密整部裝置

某些裝置可讓您選擇加密整部裝置，或僅加密已使用的空間。 請選擇加密整部裝置，而非僅加密已使用的空間。 如果您僅加密已使用的空間：

1. [從公司入口網站移除這部裝置](unenroll-your-device-from-intune-android.md)
2. 解密已使用的空間
3. 加密整部裝置
4. 重新註冊裝置

## <a name="specific-manufacturer-issues"></a>特定製造商問題

某些 7.0+ 版 Android 裝置加密資料的方式，與特定 Android 平台標準不一致。 這些裝置看起來像加密過，即使是全新的。 Intune 會辨識這些裝置的加密方法，將裝置的資訊列入有風險。 此風險主要是來自能夠存取實體裝置的使用者懷有惡意。

> [!Note]
> Microsoft 會與製造商合作來解決我們在測試時所發現的任何問題，或是使用者回報給我們的任何問題。 只要有新的資訊，本文會隨時更新。 

## <a name="known-devices"></a>已知的裝置

### <a name="known-devices-that-can-be-updated-to-fix-this-issue"></a>已知可更新以修正此問題的裝置

如果您擁有下列其中一個裝置，而且未將該裝置更新至最新版的 Android，可能就會遇到此問題。 您可以前往 [設定] > [更新] 來安裝這些裝置的更新。 

- [華為榮耀 8](http://consumer.huawei.com/en/support/mobile-phones/honor8_en-sup.htm)
- [華為 P9](http://consumer.huawei.com/en/phones/p9/)

### <a name="known-devices-that-currently-cannot-be-updated-to-fix-this-issue"></a>已知目前無法透過更新來修正此問題的裝置

您無法解決下列裝置的此一問題。 您可能需要使用不同的裝置來存取公司資源。 

- [Huawei Mate 8](https://consumer.huawei.com/en/mobile-phones/mate8/index.htm) \(英文\)
- [OPPO 裝置](http://www.oppo.com/en/smartphones)
- [Vivo 裝置](https://www.vivo.co.in)
- [小米 Mi 智慧型手機](https://xiaomi-mi.com/mi-smartphones/) \(英文\)

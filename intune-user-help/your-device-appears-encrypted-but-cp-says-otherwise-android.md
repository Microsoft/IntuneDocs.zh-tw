---
title: 您的 Android 裝置似乎已加密 | Microsoft Docs
description: 解決公司入口網站和 Microsoft Intune 應用程式中的加密狀態
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 08/14/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ba593c08-1a78-4013-8525-b45a948772ec
searchScope:
- User help
ROBOTS: ''
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: d63ecdb23b107d844c37d7a805247092116618e1
ms.sourcegitcommit: b30a2ba2b67aa2fc3421f0b2f6c5f361a0de612a
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 08/14/2019
ms.locfileid: "69022742"
---
# <a name="device-encrypted-but-apps-say-otherwise"></a>裝置已加密, 但應用程式不然

如果公司入口網站或 Microsoft Intune 應用程式指出您的裝置未加密, 但您確定它是, 請嘗試這篇文章中的步驟。  

## <a name="add-a-startup-pin"></a>新增啟動 PIN

某些 Android 裝置會要求您建立啟動 PIN 以確保裝置的安全。 此設定的位置會在您裝置的 [**設定**] 應用程式中。 設定的名稱和位置可能會有所不同。 例如, 在 Samsung Galaxy S7 上, 此設定稱為「**安全啟動**」。 若要啟用它並建立密碼, 請移至 [**設定** > ] [**鎖定畫面與安全性** > ] [安全] [**啟動**]。  

## <a name="encrypt-the-entire-device"></a>加密整部裝置

本節僅適用于公司入口網站應用程式。 某些裝置可讓您選擇加密整部裝置，或僅加密已使用的空間。 選擇用來加密整部裝置的選項。 如果您選擇只加密已使用的空間:

1. [從公司入口網站移除這部裝置](unenroll-your-device-from-intune-android.md)。
2. 解密已使用的空間。  
3. 加密整部裝置。  
4. 重新註冊裝置。  

## <a name="downgrade-your-version-of-android"></a>將您的 Android 版本降級

本節僅適用于公司入口網站應用程式。 如果您的裝置提供降級為 Android 6.0 與更新版本的選項，請執行這些動作。 若您嘗試將裝置降級，會有資料遺失的風險。 因此，建議您連絡公司支援人員以解決此問題。 在[公司入口網站](https://go.microsoft.com/fwlink/?linkid=2010980)上取得公司支援人員的連絡資訊。  

## <a name="specific-manufacturer-issues"></a>特定製造商問題

某些 7.0 版與更新版本 Android 裝置加密資料的方式，與特定 Android 平台標準不一致。 這些加密方法會將裝置資訊放在風險之下。 因此, 不支援這些裝置。 

如需支援的 Android 裝置的非完整清單, 請參閱[Intune 中支援的作業系統和瀏覽器](https://docs.microsoft.com/intune/supported-devices-browsers#supported-samsung-knox-standard-devices)一文。 如果未列出您的裝置, 請參閱裝置製造商或聯絡支援人員。 

> [!Note]
> Microsoft 會與製造商合作來解決我們在測試時所發現的任何問題，或是使用者回報給我們的任何問題。 只要有新的資訊，本文會隨時更新。 

## <a name="update-devices"></a>更新裝置   

如果您尚未將裝置更新為最新版本的 Android, 請移至裝置的 [**設定**] 應用程式, 然後選取 [**更新**]。  

## <a name="next-steps"></a>後續步驟   
是否仍需要協助？ 請連絡公司支援人員 (可查看[公司入口網站](https://go.microsoft.com/fwlink/?linkid=2010980)以取得連絡資訊)，或是撰寫電子郵件給 <a href="mailto:wintunedroidfbk@microsoft.com?subject=I'm having trouble with enrolling my Android device&body=Describe the issue you're experiencing here.">Microsoft Android 小組</a>。  

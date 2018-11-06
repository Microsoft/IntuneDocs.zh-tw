---
title: 在 Microsoft Intune - Azure 中使用自訂裝置設定 | Microsoft Docs
description: 使用 Microsoft Intune 新增或建立設定檔，以使用 Windows Phone、Windows 8.1、Windows 10 及更新版本、Android、Anndroid Enterprise、macOS 和 iOS 裝置的自訂設定
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/23/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 3106f71b59019a1cf71680c51be6dfcb4ce10b0d
ms.sourcegitcommit: c969b596ec0fec227484c50f210ba4e159e2e533
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2018
ms.locfileid: "49983069"
---
# <a name="create-a-profile-with-custom-settings-in-intune"></a>在 Intune 中使用自訂設定建立設定檔

## <a name="what-are-custom-profiles"></a>什麼是自訂設定檔

Microsoft Intune 包含許多內建設定，可控制裝置上的不同功能。 您也可以建立自訂設定檔。 當您想要使用未內建在 Intune 的裝置設定和功能時，自訂設定檔會很有用。 這些設定檔包含功能和設定，可讓您控制組織中的裝置。 例如，您可以建立自訂設定檔，為每部 iOS 裝置設定相同的功能。

如需組態設定檔的詳細資訊，請參閱[什麼是 Microsoft Intune 裝置設定檔？](device-profiles.md)。 

本文包含相關連結，可建立 Android、Android Enterprise、iOS、macOS 和 Windows 的自訂設定檔。

## <a name="available-platforms"></a>可用的平台

為每個平台設定自訂設定的方式皆不同。 例如，若要控制 Android 與 Windows 裝置上的功能，您可輸入開放行動裝置聯盟統一資源識別項 (OMA-URI) 值。 若是 Apple 裝置，您可以使用 [Apple Configurator](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12) 或 [Apple Profile Manager](https://support.apple.com/profile-manager) 匯入所建立的檔案。

所建立的自訂設定檔與內建設定檔類似，可於下列平台使用：

- [Android](custom-settings-android.md)
- [Android Enterprise](custom-settings-android-for-work.md)
- [iOS](custom-settings-ios.md)
- [macOS](custom-settings-macos.md)
- [Windows 10](custom-settings-windows-10.md)
- [Windows Holographic for Business](custom-settings-windows-holographic.md)
- [Windows Phone 8.1](custom-settings-windows-phone-8-1.md)

## <a name="next-steps"></a>接下來的步驟

選擇您的平台，並開始使用：

- [Android](custom-settings-android.md)
- [Android Enterprise](custom-settings-android-for-work.md)
- [iOS](custom-settings-ios.md)
- [macOS](custom-settings-macos.md)
- [Windows 10](custom-settings-windows-10.md)
- [Windows Holographic for Business](custom-settings-windows-holographic.md)
- [Windows Phone 8.1](custom-settings-windows-phone-8-1.md)
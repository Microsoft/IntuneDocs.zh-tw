---
title: 在 Microsoft Intune - Azure 中使用自訂裝置設定 | Microsoft Docs
description: 新增或建立設定檔，以 Microsoft Intune 來使用 Windows、Android 和 iOS 裝置的自訂設定
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/06/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: ce7c263435f92a041b93dc5d34ffa912c6fa87fb
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31021875"
---
# <a name="create-a-profile-with-custom-settings-in-intune"></a>在 Intune 中使用自訂設定建立設定檔

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune 可能不具備您需要或想要的所有內建設定。 或者，您可能想要使用其他裝置設定檔中可用的設定。 若要新增這些設定，請建立裝置設定檔，然後使用自訂裝置設定來設定設定檔。

本文列出使用自訂設定建立設定檔的基本步驟。 它也包含連結，以便更深入發掘如何使用不同平台建立自訂設定。

## <a name="custom-settings-on-different-platforms"></a>不同平台上的自訂設定
為每個平台設定自訂設定的方式皆不同。 例如，若要控制 Android 與 Windows 裝置上的功能，您可輸入開放行動裝置聯盟統一資源識別項 (OMA-URI) 值。 對於 Apple 裝置來說，您可匯入利用 [Apple Configurator](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12) 所建立的檔案。

## <a name="create-the-profile"></a>建立設定檔

1. 登入 [Azure 入口網站](https://portal.azure.com)。
2. 選取 [All services] (所有服務)，篩選 [Intune]，然後選取 [Microsoft Intune]。
3. 依序選取 [裝置設定]、[設定檔]，然後選擇 [建立設定檔]。
4. 輸入自訂設定檔的 [名稱] 和 [描述]。
5. 從 [平台] 下拉式清單中，選取要套用自訂設定的裝置平台。 您可以選擇下列任何平台：

    - **Android**
    - **Android for Work**
    - **iOS**
    - **macOS**
    - **Windows Phone 8.1**
    - **Windows 8.1 及更新版本**
    - **Windows 10 及更新版本**

6. 從 [設定檔] 類型下拉式清單中選擇 [自訂]。
7. 您可設定的設定會視您選擇的平台而不同。 下列連結提供每個平台自訂設定的更多詳細資料：

    - [Android 設定](custom-settings-android.md)
    - [iOS 設定](custom-settings-ios.md)
    - [macOS 設定](custom-settings-macos.md)
    - [Windows Phone 8.1 設定](custom-settings-windows-phone-8-1.md)
    - [Windows 10 設定](custom-settings-windows-10.md)
    - [Windows Holographic for Business 設定](custom-settings-windows-holographic.md)
    - [Android for Work 設定](custom-settings-android-for-work.md)

8. 完成後，請選取 [建立]。

設定檔隨即建立，並出現在設定檔清單上。 若要將此設定檔指派給群組，請參閱[如何指派裝置設定檔](device-profile-assign.md)。

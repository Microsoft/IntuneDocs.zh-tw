---
title: "如何設定 Intune 自訂裝置設定"
titleSuffix: Intune Azure preview
description: "Intune Azure 預覽版︰了解如何在管理的裝置上使用 Intune 設定自訂設定。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 04/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 42f9b104-c1f6-4dfc-8aa4-1d33e1eaf61f
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: e5dd7cb5b320df7f443b52a1b502027fa3c4acaf
ms.openlocfilehash: dcd876e31d3b5c65d27f317aab1582da1a883646
ms.lasthandoff: 04/19/2017


---

# <a name="how-to-configure-custom-device-settings-in-microsoft-intune"></a>如何在 Microsoft Intune 中設定自訂裝置設定

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

## <a name="when-to-use-custom-settings"></a>使用自訂設定的時機

當 Intune 沒有您想要設定的內建設定時，自訂設定很實用，且可從其他裝置設定檔取得。
為每個平台設定自訂設定的方式皆不同。 例如，對於 Android 與 Windows 裝置來說，您可指定開放行動裝置聯盟統一資源識別項 (OMA-URI) 值，控制裝置上的功能。 對於 Apple 裝置來說，您可匯入利用 [Apple Configurator](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12) 所建立的檔案。

使用本主題中的資訊可深入了解使用自訂設定進行設定檔設定的基本概念，然後可深入閱讀每個平台的主題，以了解裝置專屬內容。

## <a name="create-a-device-profile-containing-custom-settings"></a>建立內含自訂設定的裝置設定檔

1. 登入 Azure 入口網站。
2. 選擇 [更多服務]  >  [其他]  >  [Intune]。
3. 在 [Intune] 刀鋒視窗中，選擇 [裝置設定]。
2. 在 [裝置設定] 刀鋒視窗中，選擇 [管理]  >  [設定檔]。
3. 在設定檔刀鋒視窗中，選擇 [建立設定檔]。
4. 在 [建立設定檔] 刀鋒視窗中，為自訂檔輸入 [名稱] 及[描述]。
5. 從 [平台] 下拉式清單中，選取要套用自訂設定的裝置平台。 您目前可以為自訂裝置設定選擇下列平台之一︰
    - **Android**
    - **iOS**
    - **macOS**
    - **Windows Phone 8.1**
    - **Windows 10 及更新版本**
6. 從 [設定檔] 類型下拉式清單中選擇 [自訂]。
7. 您可設定的設定值取決於您選擇的平台而有所不同。 前往下列主題之一，即可取得每個平台的詳細設定︰
    - [Android 設定](custom-for-android.md)
    - [iOS 設定](custom-for-ios.md)
    - [macOS 設定](custom-for-macos.md)
    - [Windows Phone 8.1 設定](custom-for-windows-phone-8-1.md)
    - [Windows 10 設定](custom-for-windows-10.md)
    - [Android for Work 設定](custom-android-for-work.md)
8. 當您完成時，請返回 [建立設定檔] 刀鋒視窗，然後點擊 [建立]。

隨即會建立設定檔，並會出現在 [設定檔清單] 刀鋒視窗上。
若想繼續，並將此設定檔指派給群組，請參閱[如何指派裝置設定檔](how-to-assign-device-profiles.md)。


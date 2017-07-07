---
title: "設定 Intune 裝置功能設定"
titleSuffix: Intune on Azure
description: "了解如何在管理的裝置上使用 Intune 設定功能。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 06/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 42f9b104-c1f6-4dfc-8aa4-1d33e1eaf61f
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: f286119019bb26d8851c766a9d88ad818d7e600b
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2017
---
# <a name="how-to-configure-device-feature-settings-in-microsoft-intune"></a>如何在 Microsoft Intune 中設定裝置功能設定

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

裝置限制可讓您控制 iOS 和 macOS 裝置上的功能，例如 AirPrint、通知，以及共用的裝置設定。

使用本主題中的資訊，以深入了解設定裝置功能設定檔的相關基本概念，然後深入閱讀每個平台的主題，以了解裝置專屬內容。

## <a name="create-a-device-profile-containing-device-restriction-settings"></a>建立內含裝置限制設定的裝置設定檔

1. 登入 Azure 入口網站。
2. 選擇 [更多服務]  >  [監視 + 管理]  >  [Intune]。
3. 在 [Intune] 刀鋒視窗中，選擇 [裝置設定]。
2. 在 [裝置設定] 刀鋒視窗中，選擇 [管理]  >  [設定檔]。
3. 在設定檔刀鋒視窗中，選擇 [建立設定檔]。
4. 在 [建立設定檔] 刀鋒視窗上，為裝置功能設定檔輸入 [名稱] 及 [描述]。
5. 從 [平台] 下拉式清單中，選取要套用設定的裝置平台。 您目前可為裝置功能選擇下列平台之一︰
    - **iOS**
    - **macOS**
6. 從 [設定檔類型] 下拉式清單中，選擇 [裝置功能]。 
7. 您可設定的設定值取決於您選擇的平台而有所不同。 前往下列主題之一，即可取得每個平台的詳細設定︰
    - [適用於 iOS 和 macOS 裝置的 AirPrint 設定](air-print-settings-ios-macos.md)
    - [適用於 iOS 裝置的 AirPlay 設定](airplay-settings-ios.md)
    - [適用於 iOS 的主畫面配置設定](home-screen-settings-ios.md)
    - [適用於 iOS 的應用程式通知設定](app-notification-settings-ios.md)
    - [適用於 iOS 的共用裝置組態設定](shared-device-settings-ios.md)
    - [適用於 iOS 的網路內容篩選器](web-content-filter-settings-ios.md)

8. 當您完成時，請返回 [建立設定檔] 刀鋒視窗，然後點擊 [建立]。

隨即會建立設定檔，並會出現在 [設定檔清單] 刀鋒視窗上。
若想繼續，並將此設定檔指派給群組，請參閱[如何指派裝置設定檔](device-profile-assign.md)。




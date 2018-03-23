---
title: 執行 iOS 之裝置的 Microsoft Intune 自訂設定
titleSuffix: ''
description: 了解 Microsoft Intune 中可用於 iOS 自訂設定檔的設定。
keywords: ''
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 3/6/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 3c92b8816dd6c5afd96cb8853b6d251ff5befaf4
ms.sourcegitcommit: e30fb2375fb79f67e5c1e4ed7b2c21fb9ca80c59
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2018
---
# <a name="microsoft-intune-custom-device-settings-for-devices-running-ios"></a>執行 iOS 之裝置的 Microsoft Intune 自訂裝置設定

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

使用 Microsoft Intune iOS 自訂設定檔，將使用 [Apple Configurator 工具](https://itunes.apple.com/app/apple-configurator-2/id1037126344?mt=12)所建立的設定指派給 iOS 裝置。 此工具讓您能夠建立許多設定來控制這些裝置的操作，並將它們匯出到組態設定檔。 接著可將此組態設定檔匯入 Intune iOS 自訂設定檔，並將設定指派到組織中的使用者與裝置。

此功能可讓您指派無法使用其他 Intune 設定檔類型設定的 iOS 設定。


1. 請使用[如何在 Microsoft Intune 中設定自訂裝置設定](custom-settings-configure.md)中的指示，即可開始使用。
2. 在 [自訂組態設定檔] 窗格中，設定下列每個設定：

- **自訂組態設定檔名稱** - 提供原則的名稱，其會顯示在裝置以及 Intune 狀態中。
- **組態設定檔** - 瀏覽至使用 Apple Configurator 所建立的組態設定檔。
針對您所指派 iOS 自訂原則之裝置上的 iOS 版本，確認從 Apple Configurator 工具匯出的設定與其相容。 如需如何解決不相容設定的相關資訊，請在 [Apple Developer](https://developer.apple.com/) 網站上搜尋 **組態設定檔參考**和**行動裝置管理通訊協定參考**。

您匯入的檔案會顯示在窗格的 [檔案內容] 區域中。

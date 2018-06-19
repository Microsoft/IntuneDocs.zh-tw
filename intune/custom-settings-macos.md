---
title: 執行 macOS 之裝置的 Microsoft Intune 自訂設定
titleSuffix: ''
description: 了解在 Microsoft Intune 中可用於 macOS 自訂設定檔中的設定。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/6/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 849bf23429ed689ee995784c3a47a802ba7dbf71
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
ms.locfileid: "31832414"
---
# <a name="microsoft-intune-custom-device-settings-for-devices-running-macos"></a>執行 macOS 之裝置的 Microsoft Intune 自訂裝置設定

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

使用 Microsoft Intune macOS 自訂設定檔，將使用 [Apple Configurator 工具](https://itunes.apple.com/app/apple-configurator-2/id1037126344?mt=12)所建立的設定指派給 macOS 裝置。 此工具讓您能夠建立許多設定來控制這些裝置的操作，並將它們匯出到組態設定檔。 接著可將此組態設定檔匯入 Intune macOS 自訂設定檔，並將設定指派到組織中的使用者與裝置。

此功能可讓您指派無法以其他 Intune 設定檔類型設定的 macOS 設定。


1. 請使用[如何在 Microsoft Intune 中設定自訂裝置設定](custom-settings-configure.md)中的指示，即可開始使用。
2. 在 [自訂組態設定檔] 窗格中，設定下列每個設定：

- **自訂組態設定檔名稱** - 提供原則的名稱，其會顯示在裝置以及 Intune 狀態中。
- **組態設定檔** - 瀏覽至使用 Apple Configurator 所建立的組態設定檔。
針對您所指派 macOS 自訂原則之裝置上的 macOS 版本，確認從 Apple Configurator 工具匯出的設定與其相容。 如需如何解決不相容設定的相關資訊，請在 [Apple Developer](https://developer.apple.com/) 網站上搜尋 **組態設定檔參考**和**行動裝置管理通訊協定參考**。

您匯入的檔案會顯示在窗格的 [檔案內容] 區域中。

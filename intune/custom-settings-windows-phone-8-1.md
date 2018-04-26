---
title: 執行 Windows Phone 8.1 之裝置的 Microsoft Intune 自訂設定
titleSuffix: ''
description: 了解可用於 Windows Phone 8.1 自訂設定檔中的設定。
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
ms.openlocfilehash: b21464016dff3396b25861af568fa90d8b7a260f
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="microsoft-intune-custom-device-settings-for-devices-running-windows-phone-81"></a>執行 Windows Phone 8.1 之裝置的 Microsoft Intune 自訂裝置設定

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

使用 Microsoft Intune Windows Phone 8.1 **自訂**設定檔來指派 OMA-URI 設定，以用於控制 Windows Phone 8.1 裝置上的功能。 這些是許多行動裝置製造商用來控制裝置功能的標準設定。

此功能之目的是讓您指派無法使用 Intune 原則設定的設定。

## <a name="custom-policy-settings-for-windows-phone-81-devices"></a>Windows Phone 8.1 裝置的自訂原則設定

1. 請使用[如何在 Microsoft Intune 中設定自訂裝置設定](custom-settings-configure.md)中的指示，即可開始使用。
2. 在 [Custom OMA-URI Settings] (自訂 OMA-URI 設定) 窗格中，選擇 [新增] 以新增一或多個 OMA-URI 設定。
3. 在 [新增資料列] 窗格中，設定每個設定的下列值︰
    - **名稱** - 輸入 OMA-URI 設定的唯一名稱，協助您在設定清單中識別該設定。
    - **描述** - 提供描述概述設定及其他可協助您找到設定的相關資訊。
    - **OMA-URI** - 指定您想要為其提供設定的 OMA-URI。
    - **資料類型** - 選取要用來指定此 OMA-URI 設定的資料類型。 選擇 [字串]、[字串 (XML)]、[日期和時間]、[整數]、[浮點數]、[布林值] 或 [Base64]。
    - **值** - 輸入要與您所輸入之 OMA-URI 建立關聯的值或檔案。

4. 完成設定之後，請按一下 [確定]，然後再視需要新增更多設定。

---
title: "Android 裝置的 Intune 自訂設定"
titleSuffix: Intune Azure preview
description: "Intune Azure 預覽版︰了解可用於 Android 自訂設定檔中的設定。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 05/04/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 494b3892-916e-4b40-9b67-61adec889bdf
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: ff3d3b1596f58213bed2509b1bfd5ae81c63f440
ms.contentlocale: zh-tw
ms.lasthandoff: 05/23/2017


---

# <a name="custom-settings-for-android-devices-in-microsoft-intune"></a>Microsoft Intune 中 Android 裝置的自訂設定

[!INCLUDE[azure_preview](./includes/azure_preview.md)]

使用 Microsoft Intune Android **自訂**設定檔來指派 OMA-URI 設定，以用於控制 Android 裝置上的功能。 這些是許多行動裝置製造商用來控制裝置功能的標準設定。

此功能的目的是讓您指派無法使用 Intune 原則設定的 Android 設定。

## <a name="custom-profile-settings-for-android-devices"></a>Android 裝置的自訂設定檔設定

1. 請使用[如何在 Microsoft Intune 中設定自訂裝置設定](custom-settings-configure.md)中的指示，即可開始使用。
2. 在 [建立設定檔] 刀鋒視窗中選擇 [設定]，可新增一或多個 OMA URI 設定。
3. 在 [編輯資料列] 刀鋒視窗中，為每個設定配置下列值︰
    - **名稱** - 輸入 OMA-URI 設定的唯一名稱，協助您在設定清單中識別該設定。
    - **描述** - 提供描述概述設定及其他可協助您找到設定的相關資訊。
    - **資料類型** - 選取要指定此 OMA-URI 設定的資料類型。 選擇 [字串]、[字串 (XML)]、[日期和時間]、[整數]、[浮點數] 或 [布林值]。
    - **OMA-URI** - 指定您想要為其提供設定的 OMA-URI。
    - **值** - 輸入要與您所輸入之 OMA-URI 相關聯的值。
4. 完成設定之後，請按一下 [確定]，然後再視需要新增更多設定。


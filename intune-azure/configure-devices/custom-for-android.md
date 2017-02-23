---
title: "Android 裝置的 Intune 自訂設定 | Intune Azure 預覽版 | Microsoft Docs"
description: "Intune Azure 預覽版︰了解可用於 Android 自訂設定檔中的設定。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 494b3892-916e-4b40-9b67-61adec889bdf
ms.reviewer: heenamac
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 5ab494a3dd1e1bdea9703ab314574b192c5208ee
ms.openlocfilehash: 3a80a69a27b540b66fb96e098c0b0f66a0854297


---

# <a name="custom-settings-for-android-devices-in-intune-azure-preview"></a>Intune Azure 預覽版中 Android 裝置的自訂設定

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

使用 Microsoft Intune 的 Android **自訂**設定檔來部署 OMA-URI 設定，以控制 Android 裝置上的功能。 這些是許多行動裝置製造商用來控制裝置功能的標準設定。

此功能的目的是讓您部署無法使用 Intune 原則設定的 Android 設定。

## <a name="custom-profile-settings-for-android-devices"></a>Android 裝置的自訂設定檔設定

1. 請使用[如何在 Microsoft Intune 中設定自訂裝置設定](how-to-configure-custom-settings.md)中的指示，即可開始使用。
2. 在 [建立設定檔] 刀鋒視窗中選擇 [設定]，可新增一或多個 OMA URI 設定。
3. 在 [編輯資料列] 刀鋒視窗中，為每個設定配置下列值︰
    - **名稱** - 輸入 OMA-URI 設定的唯一名稱，協助您在設定清單中識別該設定。
    - **描述** - 提供描述概述設定及其他可協助您找到設定的相關資訊。
    - **資料類型** - 選取要指定此 OMA-URI 設定的資料類型。 選擇 [字串]、[字串 (XML)]、[日期和時間]、[整數]、[浮點數] 或 [布林值]。
    - **OMA-URI** - 指定您想要為其提供設定的 OMA-URI。
    - **值** - 輸入要與您所輸入之 OMA-URI 相關聯的值。
4. 完成設定之後，請按一下 [確定]，然後再視需要新增更多設定。



<!--HONumber=Feb17_HO1-->



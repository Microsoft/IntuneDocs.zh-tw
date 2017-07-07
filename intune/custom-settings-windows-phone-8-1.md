---
title: "Windows Phone 8.1 裝置的 Intune 自訂設定"
titleSuffix: Intune on Azure
description: "了解可用於 Windows Phone 8.1 自訂設定檔中的設定。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 05/04/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 21c55041-3821-4a62-9f85-855b97dba269
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: b3dcad95b85d967e48c8b05d655a5e679daa0aee
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2017
---
# <a name="custom-settings-for-windows-phone-81-devices-in-microsoft-intune"></a>Microsoft Intune 中 Windows Phone 8.1 裝置的自訂設定

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

使用 Microsoft Intune Windows Phone 8.1 **自訂**設定檔來指派 OMA-URI 設定，以用於控制 Windows Phone 8.1 裝置上的功能。 這些是許多行動裝置製造商用來控制裝置功能的標準設定。

此功能之目的是讓您指派無法使用 Intune 原則設定的設定。

## <a name="custom-policy-settings-for-windows-phone-81-devices"></a>Windows Phone 8.1 裝置的自訂原則設定

1. 請使用[如何在 Microsoft Intune 中設定自訂裝置設定](custom-settings-configure.md)中的指示，即可開始使用。
2. 在 [建立設定檔] 刀鋒視窗中選擇 [設定]，可新增一或多個 OMA URI 設定。
3. 在 [新增資料列] 刀鋒視窗中，設定每個設定的下列值︰
    - **名稱** - 輸入 OMA-URI 設定的唯一名稱，協助您在設定清單中識別該設定。
    - **描述** - 提供描述概述設定及其他可協助您找到設定的相關資訊。
    - **OMA-URI** - 指定您想要為其提供設定的 OMA-URI。
    - **資料類型** - 選取要指定此 OMA-URI 設定的資料類型。 請從 [字串]、[日期和時間]、[整數]、[浮點數]，或 [布林] 之間選擇。
    - **值** - 輸入要與您所輸入之 OMA-URI 相關聯的值。

4. 完成設定之後，請按一下 [確定]，然後再視需要新增更多設定。

---
title: "iOS 裝置的 Intune 自訂設定 | Intune Azure 預覽版 | Microsoft Docs"
description: "Intune Azure 預覽版︰了解可用於 iOS 自訂設定檔中的設定。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6da8caa8-65c2-4f47-842f-9570dcb1ac22
ms.reviewer: heenamac
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 5ab494a3dd1e1bdea9703ab314574b192c5208ee
ms.openlocfilehash: cfccdbf34437c5ab23cefba5307c53c60573ddb0


---

# <a name="intune-custom-settings-for-ios-devices-in-intune-azure-preview"></a>Intune Azure 預覽版中 iOS 裝置的自訂設定

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

使用 Microsoft Intune iOS 自訂設定檔，可將使用 [Apple Configurator 工具](https://itunes.apple.com/app/apple-configurator-2/id1037126344?mt=12)所建立的設定，部署至 iOS 裝置。 此工具讓您能夠建立許多設定來控制這些裝置的操作，並將它們匯出到組態設定檔。 接著可將此組態設定檔匯入 Intune iOS 自訂設定檔，並將設定指派到組織中的使用者與裝置。

您可利用這項功能，部署無法以其他 Intune 設定檔進行設定的 iOS 設定。


1. 請使用[如何在 Microsoft Intune 中設定自訂裝置設定](how-to-configure-custom-settings.md)中的指示，即可開始使用。
2. 在 [建立設定檔] 刀鋒視窗中，指定下列各項︰

- **自訂組態設定檔名稱** - 提供原則的名稱，其會顯示在裝置以及 Intune 狀態中。
- **組態設定檔** - 瀏覽至使用 Apple Configurator 所建立的組態設定檔。
確定您從 Apple Configurator 工具匯出的設定會與您部署 iOS 自訂原則之裝置上的 iOS 版本相容。 如需如何解決不相容設定的相關資訊，請在 [Apple Developer](https://developer.apple.com/) 網站上搜尋 **組態設定檔參考**和**行動裝置管理通訊協定參考**。

您匯入的檔案將會顯示在刀鋒視窗的 [檔案內容] 區域中。



<!--HONumber=Feb17_HO1-->



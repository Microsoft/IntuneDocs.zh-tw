---
title: "使用 Intune 尋找遺失的 iOS 裝置"
titleSuffix: Intune on Azure
description: "了解如何使用 Intune 尋找遺失或遭竊的 iOS 裝置。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 04/27/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3e544286-12ad-4a3a-86f8-d2cf16940b1f
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 80aa0e5afd1f8862b181d455ff6b545e462f90c9
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2017
---
# <a name="locate-lost-or-stolen-ios-devices-with-intune"></a>使用 Intune 尋找遺失或遭竊的 iOS 裝置


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

**尋找裝置**裝置動作會在地圖上顯示遺失或遭竊 iOS 裝置的位置。 裝置必須是透過 DEP 註冊之公司擁有的 iOS 裝置，且處於受監督模式。 使用此動作之前，必須已將裝置設置為[遺失模式](/intune-azure/manage-devices/lost-mode.md)。

1. 登入 Azure 入口網站。
2. 選擇 [更多服務]  >  [監視 + 管理]  >  [Intune]。
3. 在 [Intune] 刀鋒視窗中，選擇 [裝置]。
4. 在 [裝置和群組] 刀鋒視窗中選擇 [所有裝置]。
5. 從您管理的裝置清單中，選擇 iOS 裝置，然後選擇 [尋找裝置] 遠端動作。
6. 找到裝置之後，它的位置會顯示在 [尋找裝置] 刀鋒視窗上。
    ![尋找裝置刀鋒視窗](./media/locate-device.png)

>[!NOTE]
>基於隱私權之目的，您能將地圖放大的距離將會受到限制。

## <a name="security-and-privacy-information-for-the-lost-mode-and-locate-device-actions"></a>遺失模式的安全性與隱私權資訊以及尋找裝置動作
- 直到您啟用這個動作，裝置位置資訊才會傳送至 Intune。
- 當您使用尋找裝置動作時，裝置的緯度和經度座標會傳送至 Intune，並顯示在 Azure 入口網站中。
- 資料會儲存 24 小時，然後移除。 您無法手動移除位置資料。
- 位置資料在儲存和傳送時皆會加密。
- 當您設定遺失模式時，我們建議您輸入來顯示於鎖定畫面上的訊息，應包含有助於讓找到該裝置的人能夠歸還的資訊。

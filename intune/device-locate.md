---
title: 使用 Microsoft Intune 尋找遺失的 iOS 裝置 - Azure | Micrososft Docs
description: 使用 Microsoft Intune 的尋找裝置功能來尋找遺失或遭竊的 iOS 裝置。 在使用尋找裝置動作時，取得安全性和隱私權資訊的詳細資料。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/05/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 3e544286-12ad-4a3a-86f8-d2cf16940b1f
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: da8bb19db8c2da2d5854c3f991ccce4d124d594c
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="locate-lost-or-stolen-ios-devices-with-intune"></a>使用 Intune 尋找遺失或遭竊的 iOS 裝置

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

使用 [尋找裝置] 動作在地圖上顯示遺失或遭竊的 iOS 裝置位置。 該裝置必須是透過裝置註冊計劃註冊的公司擁有的 iOS 裝置，且處於受監督模式。 使用此動作之前，請先確定該裝置處於[遺失模式](device-lost-mode.md)。

## <a name="supported-platforms"></a>支援的平台

- iOS 9.3 和更新版本

下列系統不支援這項功能： 
- Windows
- Windows Phone
- macOS
- Android

## <a name="locate-a-lost-or-stolen-device"></a>尋找遺失或遭竊的裝置

1. 登入 [Azure 入口網站](https://portal.azure.com)。
2. 選取 [All services] (所有服務)，篩選 [Intune]，然後選取 [Microsoft Intune]。
3. 選取 [裝置]，然後選取 [所有裝置]。
4. 從您管理的裝置清單中，選擇 iOS 裝置，然後選擇 [...More] (...其他)。 然後選擇 [尋找裝置] 遠端動作。
5. 找到位置後，其位置會顯示在 [尋找裝置] 中。
    ![在 Azure 中使用 Intune 尋找裝置的螢幕擷取畫面](./media/locate-device.png)

>[!NOTE]
>基於隱私權之故，您能放大的地圖距離會受到限制。

## <a name="security-and-privacy-information-for-lost-mode-and-locate-device-actions"></a>遺失模式的安全性與隱私權資訊以及尋找裝置動作
- 直到您開啟這個動作，裝置位置資訊才會傳送至 Intune。
- 當您使用尋找裝置動作時，裝置的緯度和經度座標會傳送至 Intune，並顯示在 Azure 入口網站中。
- 資料會儲存 24 小時，然後移除。 您無法手動移除位置資料。
- 位置資料在儲存和傳送時皆會加密。
- 當您設定遺失模式時，您可以自訂在鎖定畫面中顯示的訊息。 在此訊息中，為協助尋找裝置的人員，請務必包含特定的詳細資料以便歸還遺失的裝置。

## <a name="next-steps"></a>接下來的步驟

若要查看啟用中的尋找裝置狀態，請開啟 [裝置]，然後選取 [裝置動作]。

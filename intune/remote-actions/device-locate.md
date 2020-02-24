---
title: 使用 Microsoft Intune 尋找遺失的 iOS/iPadOS 裝置 - Azure | Microsoft Docs
description: 使用 Microsoft Intune 的尋找裝置功能來尋找遺失或遭竊的 iOS/iPadOS 裝置。 在使用尋找裝置動作時，取得安全性和隱私權資訊的詳細資料。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/24/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 3e544286-12ad-4a3a-86f8-d2cf16940b1f
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: dc276a6235fb4951c83b62e3c488145062814728
ms.sourcegitcommit: 51591b862d97904291af7aa53a6eb341b11a761e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/17/2020
ms.locfileid: "77415586"
---
# <a name="locate-lost-or-stolen-iosipados-devices-with-intune"></a>使用 Intune 尋找遺失或遭竊的 iOS/iPadOS 裝置

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

使用 [尋找裝置]  動作在地圖上顯示遺失或遭竊的 iOS/iPadOS 裝置位置。 裝置必須在受監督模式。 使用此動作之前，請先確定該裝置處於[遺失模式](device-lost-mode.md)。

## <a name="supported-platforms"></a>支援的平台

- iOS/iPadOS 9.3 和更新版本

下列系統不支援這項功能： 
- Windows
- Windows Phone
- macOS
- Android

## <a name="locate-a-lost-or-stolen-device"></a>尋找遺失或遭竊的裝置

1. 登入 [Microsoft 端點管理員系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。
3. 選取 [裝置]  ，然後選取 [所有裝置]  。
4. 從您管理的裝置清單中，選擇 iOS/iPadOS 裝置，然後選擇 [...其他]  。 然後選擇 [尋找裝置]  遠端動作。
5. 找到位置後，其位置會顯示在 [尋找裝置]  中。
    ![在 Azure 中使用 Intune 尋找裝置的螢幕擷取畫面](./media/device-locate/locate-device.png)


## <a name="activate-lost-mode-sound-alert-on-an-ios-device"></a>啟動 iOS 裝置上的遺失模式音效警示

如果有人遺失其 iOS/iPadOS 9.3 或更新版本的裝置，您可透過遠端方式觸發裝置以播放警示音效，讓使用者可以找到該裝置。 裝置必須處於[遺失模式](device-lost-mode.md)狀態。

在 [Azure 入口網站中的 Intune](https://aka.ms/intuneportal) 內，選擇 [裝置]   > [所有裝置]  > 選取 iOS/iPadOS 裝置 > [概觀]   > [更多]   > [播放遺失模式音效 (僅限監督)]  。

音效會持續播放，直到使用者停用裝置上的音效，或將裝置從遺失模式中移除為止。


## <a name="security-and-privacy-information-for-lost-mode-and-locate-device-actions"></a>遺失模式的安全性與隱私權資訊以及尋找裝置動作
- 直到您開啟這個動作，裝置位置資訊才會傳送至 Intune。
- 當您使用尋找裝置動作時，裝置的緯度和經度座標可以使用圖形 API 擷取。
- 資料會儲存 24 小時，然後移除。 您無法手動移除位置資料。
- 位置資料在儲存和傳送時皆會加密。
- 當您設定遺失模式時，您可以自訂在鎖定畫面中顯示的訊息。 在此訊息中，為協助尋找裝置的人員，請務必包含特定的詳細資料以便歸還遺失的裝置。

## <a name="next-steps"></a>後續步驟

若要查看啟用中的尋找裝置狀態，請開啟 [裝置]  ，然後選取 [裝置動作]  。

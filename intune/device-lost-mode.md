---
title: "使用 Intune 啟用 iOS 遺失模式"
titlesuffix: Azure portal
description: "了解如何使用 Intune 來啟用遺失或遭竊 iOS 裝置上的遺失模式。"
keywords: 
author: arob98
ms.author: angrobe
manager: dougeby
ms.date: 08/09/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 126a7489-fe3e-43fd-a681-defb2fe0bb66
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: fcdd5e6fa844d4c475462cd0b2a4883f8ff9ba90
ms.sourcegitcommit: eac89306d1391a6d3ae1179612b0820b19c2baa6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="activate-lost-mode-on-ios-devices"></a>啟用 iOS 裝置上的遺失模式


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

**遺失模式**裝置動作可協助您啟用遺失或遭竊 iOS 裝置上的遺失模式。 此模式可讓您指定顯示於裝置鎖定畫面上的訊息及電話號碼。

## <a name="supported-platforms"></a>支援的平台

- Windows - 不支援
- Windows Phone - 不支援
- iOS - 支援受監督且為公司擁有的 iOS 9.3 和更新版本
- macOS - 不支援
- Android - 不支援

## <a name="how-to-activate-lost-mode"></a>如何啟用遺失模式

1. 登入 [Azure 入口網站](https://portal.azure.com)。
2. 選擇 [All services] (所有服務) > [Intune]。 Intune 位於 [監視 + 管理] 區段。
3. 在 [Intune] 刀鋒視窗中，選擇 [裝置]。
4. 在 [裝置] 刀鋒視窗中，選擇 [所有裝置]。
5. 從您管理的裝置清單中，依序選擇 iOS 裝置、[...其他]，然後選擇 [Lost mode] (遺失模式) 遠端動作。
6. 在 [遺失模式] 刀鋒視窗中，啟用遺失模式。 然後，輸入要顯示的訊息並選擇性地輸入連絡人電話號碼。
7. 按一下 [ **確定**]。

當您啟用遺失模式時，就會封鎖裝置的所有使用。 使用者無法存取裝置，直到您停用遺失模式。 啟用遺失模式時，您可以使用**尋找裝置**動作找出裝置所在之處。
若要使用遺失模式，裝置必須是受監督模式中的公司所擁有的 iOS 裝置。

## <a name="security-and-privacy-information-for-the-lost-mode-and-locate-device-actions"></a>遺失模式的安全性與隱私權資訊以及尋找裝置動作
- 直到您開啟這個動作，裝置位置資訊才會傳送至 Intune。
- 當您使用尋找裝置動作時，裝置的緯度和經度座標會傳送至 Intune，並顯示在 Azure 入口網站中。
- 資料會儲存 24 小時，然後移除。 您無法手動移除位置資料。
- 位置資料在儲存和傳送時皆會加密。
- 建議您輸入用來顯示於鎖定畫面上的訊息，應包含有助於讓找到該裝置的人能夠歸還的資訊。

## <a name="next-steps"></a>接下來的步驟

若要查看您剛採取的動作狀態，請在 [裝置] 刀鋒視窗中，選擇 [裝置動作]。


---
title: 使用 Microsoft Intune 啟動 iOS 遺失模式 - Azure | Microsoft Docs
description: 開啟或啟動遺失模式，使用 Microsoft Intune 自訂顯示在遺失或遭竊之 iOS 裝置鎖定畫面中的訊息。 此外，在使用遺失模式動作時，取得安全性和隱私權資訊的詳細資料。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/05/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 126a7489-fe3e-43fd-a681-defb2fe0bb66
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 070256ce5267189731c3565f4332a3bd57c326f5
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="enable-lost-mode-on-ios-devices-with-intune"></a>使用 Intune 在 iOS 裝置上啟用遺失模式

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

**遺失模式**裝置動作可協助您啟用遺失或遭竊 iOS 裝置上的遺失模式。 此模式可讓您輸入顯示於裝置鎖定畫面上的訊息及電話號碼。 若要使用遺失模式，裝置必須是受監督模式中的公司所擁有的 iOS 裝置。

## <a name="supported-platforms"></a>支援的平台

- iOS 9.3 和更新版本

下列系統不支援這項功能： 
- Windows
- Windows Phone
- macOS
- Android

## <a name="enable-lost-mode"></a>啟用遺失模式

1. 登入 [Azure 入口網站](https://portal.azure.com)。
2. 選取 [All services] (所有服務)，篩選 [Intune]，然後選取 [Microsoft Intune]。
3. 選取 [裝置]，然後選取 [所有裝置]。
4. 從您管理的裝置清單中，選擇 iOS 裝置，然後選擇 [...More] (...其他)。 然後選擇 [遺失模式] 遠端動作。
5. 在**遺失模式**中啟用這項功能。 然後，輸入要顯示的訊息及連絡人電話號碼。
6. 按一下 [確定] 以儲存您的變更。

當您啟用遺失模式時，就會封鎖裝置的所有用途。 使用者無法存取裝置，直到您停用遺失模式。 啟用遺失模式時，請使用 [[尋找裝置]](device-locate.md) 動作尋找裝置。

## <a name="security-and-privacy-information-for-the-lost-mode-and-locate-device-actions"></a>遺失模式的安全性與隱私權資訊以及尋找裝置動作
- 直到您開啟這個動作，裝置位置資訊才會傳送至 Intune。
- 當您使用尋找裝置動作時，裝置的緯度和經度座標會傳送至 Intune，並顯示在 Azure 入口網站中。
- 資料會儲存 24 小時，然後移除。 您無法手動移除位置資料。
- 位置資料在儲存和傳送時皆會加密。
- 在您輸入的鎖定螢幕顯示訊息中，請務必包含特定的詳細資料以便歸還遺失的裝置。

## <a name="next-steps"></a>接下來的步驟

若要查看啟用中的遺失模式狀態，請開啟 [裝置]，然後選取 [裝置動作]。
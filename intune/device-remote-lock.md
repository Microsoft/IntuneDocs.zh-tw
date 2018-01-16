---
title: "使用 Intune 從遠端鎖定受管理的裝置"
titlesuffix: Azure portal
description: "了解如何使用 Intune，從遠端鎖定您管理的裝置。"
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 11/21/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3b67f285-229d-4a0f-ae34-0402a20b4518
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 45d27b709ba8d4ff1d8fb4417a217ad008c19c36
ms.sourcegitcommit: 22ab1c6a6bfeb4fef9850d12b29829c3fecbbeed
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/12/2018
---
# <a name="remotely-lock-managed-devices-with-intune"></a>使用 Intune 從遠端鎖定受管理的裝置


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

**遠端鎖定**裝置會鎖定選取的裝置。 裝置擁有者必須使用其密碼才能解除裝置鎖定。 您只可從遠端鎖定具有 PIN 碼或密碼設定的裝置。

## <a name="supported-platforms"></a>支援的平台

- Windows - 不支援
- Windows Phone - 支援 Windows Phone 8.1 和更新版本
- iOS - 支援
- macOS - 支援

    > [!Note]  
    > 設定 6 位數的修復 PIN。 鎖定時，[裝置概觀] 刀鋒視窗會顯示 PIN，直到傳送另一個裝置動作為止。
- Android - 支援

## <a name="how-to-remote-lock-a-device"></a>如何從遠端鎖定裝置

1. 登入 Azure 入口網站。
2. 選擇 [更多服務]  >  [監視 + 管理]  >  [Intune]。
3. 在 [Intune] 刀鋒視窗中，選擇 [裝置]。
4. 在 [裝置和群組] 刀鋒視窗中選擇 [所有裝置]。
5. 從您管理的裝置清單中，選擇裝置，然後選擇 [遠端鎖定] 裝置遠端動作。

## <a name="next-steps"></a>接下來的步驟

若要查看您剛採取的動作狀態，請在 [裝置和群組] 刀鋒視窗中，選擇 [裝置動作]。

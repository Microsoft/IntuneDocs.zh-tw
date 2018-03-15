---
title: "使用 Intune 從遠端鎖定受控裝置"
titlesuffix: Azure portal
description: "了解如何使用 Intune，從遠端鎖定您管理的裝置。"
keywords: 
author: arob98
ms.author: angrobe
manager: dougeby
ms.date: 01/22/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3b67f285-229d-4a0f-ae34-0402a20b4518
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 0a8f3c93507cde4363570a9a39f8b3b1f69c07df
ms.sourcegitcommit: 7e5c4d43cbd757342cb731bf691ef3891b0792b5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2018
---
# <a name="remotely-lock-managed-devices-with-intune"></a>使用 Intune 從遠端鎖定受控裝置


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

**遠端鎖定**裝置會鎖定選取的裝置。 裝置擁有者必須使用其密碼才能解除裝置鎖定。 您只可從遠端鎖定具有 PIN 碼或密碼設定的裝置。

## <a name="supported-platforms"></a>支援的平台

下列平台支援遠端鎖定：

|平台|支援狀態|
|---|---|
|Android|是|
|iOS|是|
|macOS|是|
|Windows 10 Desktop|否|
|Windows 10 Mobile|是|
|Windows Phone|是，Windows Phone 8.1 及更新版本|

> [!NOTE]  
> macOS 裝置要設定 6 位數的修復 PIN。 鎖定時，[裝置概觀] 刀鋒視窗會顯示 PIN，直到傳送另一個裝置動作為止。

## <a name="how-to-remote-lock-a-device"></a>如何從遠端鎖定裝置

1. 登入 [Azure 入口網站](https://portal.azure.com)。
2. 選擇 [All services] (所有服務) > [Intune]。 Intune 位於 [監視 + 管理] 區段。
3. 在 [Intune] 刀鋒視窗中，選擇 [裝置]。
4. 在 [裝置] 刀鋒視窗中，選擇 [所有裝置]。
5. 從您管理的裝置清單中，選擇裝置，然後選擇 [遠端鎖定] 裝置遠端動作。

## <a name="next-steps"></a>後續步驟

若要查看您剛採取的動作狀態，請在 [裝置] 刀鋒視窗中，選擇 [裝置動作]。

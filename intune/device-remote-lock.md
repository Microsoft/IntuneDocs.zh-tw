---
title: 使用 Microsoft Intune 鎖定裝置 - Azure | Micrososft Docs
description: 使用 Microsoft Intune 的遠端鎖定動作，鎖定受 PIN 或密碼保護的裝置。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/07/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 3b67f285-229d-4a0f-ae34-0402a20b4518
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 0aac90c0c6c8a9e44db5a21d5864a2e0930c7ef1
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="remotely-lock-devices-with-intune"></a>使用 Intune 從遠端鎖定裝置

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

[遠端鎖定] 裝置動作會鎖定裝置。 裝置擁有者輸入密碼才能解除鎖定裝置。 您可以從遠端鎖定已設定 PIN 或密碼的裝置。 沒有 PIN 或密碼的裝置無法從遠端鎖定。

## <a name="supported-platforms"></a>支援的平台

下列平台支援 [遠端鎖定]：

- Android
- iOS
- macOS
- Windows 10 Mobile
- Windows Phone 8.1 和更新版本

「不」支援 [遠端鎖定] 的裝置：
- Windows 10 Desktop

> [!NOTE]
> macOS 裝置要設定 6 位數的修復 PIN。 裝置鎖定時，[裝置概觀] 會顯示 PIN，直到傳送另一個裝置動作為止。

## <a name="remote-lock-a-device"></a>遠端鎖定裝置

1. 登入 [Azure 入口網站](https://portal.azure.com)。
2. 選取 [所有服務]，篩選 [Intune]，然後選取 [Microsoft Intune]。
3. 選取 [裝置] > [所有裝置]。
4. 在裝置清單中選取裝置，然後選取 [遠端鎖定] 動作。

## <a name="next-steps"></a>接下來的步驟

- 若要查看此動作的狀態，請選取 [Microsoft Intune] > [裝置] > [裝置動作]。 
- 如需協助您管理裝置的更多動作，請參閱[可用動作](device-management.md)。

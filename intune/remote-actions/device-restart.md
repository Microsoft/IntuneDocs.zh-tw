---
title: 使用 Microsoft Intune 重新啟動裝置 - Azure | Micrososft Docs
description: 在 Azure 入口網站中使用 [重新啟動] 遠端動作，重新啟動使用 Microsoft Intune 的 Windows 和 iOS/iPadOS 裝置。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/21/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: c707e0c4-391a-4bad-9dfd-9a7799c48dd5
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 54fa0f796e96a2487793197cbbbe548fd8490856
ms.sourcegitcommit: 51591b862d97904291af7aa53a6eb341b11a761e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/17/2020
ms.locfileid: "77415625"
---
# <a name="remotely-restart-devices-with-intune"></a>使用 Intune 從遠端重新啟動裝置


[!INCLUDE [azure_portal](../includes/azure_portal.md)]

[重新啟動]  裝置動作會導致您選擇的裝置重新啟動 (在 5 分鐘內)。 重新啟動時不會自動通知裝置擁有者，所以他們可能會遺失工作。

## <a name="supported-platforms"></a>支援的平台

- Windows - 支援 Windows 8.1 和更新版本
- Windows Phone - 支援 Windows Phone 8.1 和更新版本
- Android Kiosk 裝置 - Android 7.0 和更新版本上可支援
- iOS/iPadOS - 支援

    > [!Note]  
    > 此命令需要受監督的裝置和**裝置鎖定**存取權限。 裝置隨即重新啟動。 以密碼鎖定的 iOS/iPadOS 裝置在重新啟動之後，不會重新加入 Wi-Fi 網路。 重新啟動之後，裝置可能無法與伺服器通訊。
- macOS - 不支援
- Android 和 Android 工作設定檔裝置 - 不支援

## <a name="restart-a-device"></a>重新啟動裝置

1. 登入 [Microsoft 端點管理員系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。
3. 選取 [裝置]   > [所有裝置]  。
4. 在您管理的裝置清單中，選取裝置 > [重新啟動]   > [是]  。

## <a name="next-steps"></a>後續步驟

- 若要查看 [重新啟動]  裝置動作的狀態，請選取 [裝置]   > [裝置動作]  。

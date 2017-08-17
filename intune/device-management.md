---
title: "使用 Intune 管理裝置"
titleSuffix: Intune on Azure
description: "了解如何使用 Intune 查看您管理的裝置，以及對這些裝置執行各種動作。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 08/09/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d2412418-d91a-4767-a3d6-bc88bb29caa2
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: e0fc5337b92ac604a448038f685b27623b6153f9
ms.sourcegitcommit: ee7f69efe9f32a1d6bdeb1fab73d03dbfe1ae58c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2017
---
# <a name="what-is-microsoft-intune-device-management"></a>什麼是 Microsoft Intune 裝置管理？


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

**裝置**工作負載可讓您深入了解您所管理的裝置，並讓您從遠端對這些裝置執行工作。 若要存取工作負載︰

1. 登入 Azure 入口網站。
2. 選擇 [更多服務]  >  [監視 + 管理]  >  [Intune]。
3. 在 [Intune] 刀鋒視窗中，選擇 [裝置]。
4. 現在，您可以執行所列的遠端裝置動作。 可用的動作取決於裝置平台和裝置的設定：

## <a name="available-device-actions"></a>可執行的裝置動作

- [檢視裝置清查](device-inventory.md)
- 執行遠端裝置動作：
    - [移除公司資料](device-company-data-remove.md) 
    - [重設為原廠設定](device-factory-reset.md)
    - [遠端鎖定](device-remote-lock.md)
    - [重設密碼](device-passcode-reset.md)
    - [略過啟用鎖定](device-activation-lock-bypass.md)
    - [全新開始](device-fresh-start.md)
    - [遺失模式](device-lost-mode.md)
    - [尋找裝置](device-locate.md)
    - [重新啟動](device-restart.md)
    - [重設 Windows 10 的 PIN 碼](device-windows-pin-reset.md)
    - [Android 遠端控制](device-profile-android-teamviewer.md)
    - [同步裝置](device-sync.md)


## <a name="next-steps"></a>後續步驟

- 選擇 [裝置動作] 查看您管理的裝置上所執行動作的狀態。 
![監視裝置動作](./media/monitor-device-actions.png)

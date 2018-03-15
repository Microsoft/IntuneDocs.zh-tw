---
title: "使用 Microsoft Intune 管理行動裝置"
titleSuffix: 
description: "使用 Intune 檢閱您管理的裝置，以及對這些裝置執行各種動作。"
keywords: 
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/21/2018
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d2412418-d91a-4767-a3d6-bc88bb29caa2
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 2e69f47e841cb44ab646431d5bd81b9c1d874c64
ms.sourcegitcommit: aafed032492c1b5861d7097a335f9bbb29ce3221
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/02/2018
---
# <a name="what-is-microsoft-intune-device-management"></a>什麼是 Microsoft Intune 裝置管理？


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

身為 IT 系統管理員，您必須確保受管理的裝置為您的終端使用者提供作業所需的資源，同時保護該資料遠離風險。

**裝置**工作負載可讓您深入了解您所管理的裝置，並讓您從遠端對這些裝置執行工作。 若要存取工作負載︰

1. 登入 [Azure 入口網站](https://portal.azure.com)。
2. 選擇 [All services] (所有服務) > [Intune]。 Intune 位於 [監視 + 管理] 區段。
3. 在 **Intune** 中選擇 [裝置]。
4. 您可以檢視裝置的相關資訊，並執行下列遠端裝置動作：
    - **概觀** - 您可以管理的已註冊裝置快照集。
    - **所有裝置** - 您可以管理的已註冊裝置清單。 選擇 [篩選] 或 [資料行] 以縮小顯示的資訊範圍。 選取裝置以[檢視裝置清查](device-inventory.md)。
    - **Azure AD 裝置** - 與 Azure Active Directory (AD) 註冊或聯結的裝置清單。 深入了解 [Azure AD 裝置管理](https://docs.microsoft.com/azure/active-directory/device-management-introduction)。
    - **裝置動作** - 在裝置上執行的遠端動作記錄，包括動作、其狀態、起始動作的人員及時間。

        ![監視裝置動作的螢幕擷取畫面](./media/monitor-device-actions.png)

    - **稽核記錄** - 稽核記錄提供您在 Microsoft Intune 中產生變更之活動的記錄。 深入了解[稽核記錄](monitor-audit-logs.md)。
    - **TeamViewer 連接器** - TeamViewer 服務可讓 Intune 管理的 Android 裝置使用者，從他們的 IT 系統管理員處取得遠端協助。 深入了解 [TeamViewer](device-profile-android-teamviewer.md)。
    - **說明及支援** - 進行疑難排解、要求支援，或者檢視 Intune 狀態。  
    
## <a name="available-device-actions"></a>可執行的裝置動作
可用的動作取決於裝置平台和裝置設定。

- [檢視裝置清查](device-inventory.md)
- 執行遠端裝置動作：
    - [移除公司資料](devices-wipe.md#remove-company-data)
    - [重設為原廠設定](devices-wipe.md#factory-reset)
    - [遠端鎖定](device-remote-lock.md)
    - [重設密碼](device-passcode-reset.md)
    - [略過啟用鎖定](device-activation-lock-bypass.md) (僅限 iOS)
    - [全新開始](device-fresh-start.md) (僅限 Windows)
    - [遺失模式](device-lost-mode.md) (僅限 iOS)
    - [尋找裝置](device-locate.md) (僅限 iOS)
    - [重新啟動](device-restart.md) (僅限 Windows)
    - [重設 Windows 10 的 PIN 碼](device-windows-pin-reset.md)
    - [Android 遠端控制](device-profile-android-teamviewer.md)
    - [同步裝置](device-sync.md)


## <a name="next-steps"></a>接下來的步驟

- 選擇 [裝置動作] 查看您管理的裝置上所執行動作的狀態。

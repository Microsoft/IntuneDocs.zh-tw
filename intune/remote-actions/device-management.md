---
title: 使用 Microsoft Intune 來管理裝置 - Azure | Micrososft Docs
description: 檢閱您使用 Microsoft Intune 來管理的裝置，包括將裝置清單匯出成 CSV 格式、檢視已加入 Azure Active Directory 的裝置、檢閱裝置上的動作變更記錄、使用「TeamViewer 連接器」以允許 IT 系統管理員從遠端對 Android 裝置進行疑難排解，以及檢視您可在裝置上執行的所有動作。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 11/14/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d2412418-d91a-4767-a3d6-bc88bb29caa2
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
redirect_url: https://docs.microsoft.com/intune
ms.openlocfilehash: ff82b1ed70d3021c33a166c694e3efe5d10905e0
ms.sourcegitcommit: e4602481a25a5e12379f673dfe801c611f51c35b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2020
ms.locfileid: "75731359"
---
# <a name="what-is-microsoft-intune-device-management"></a>什麼是 Microsoft Intune 裝置管理？

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

身為 IT 系統管理員，您必須確保受控裝置為使用者提供執行其工作所需的資源，同時保護該資料遠離風險。

**裝置**工作負載可讓您深入了解您所管理的裝置，並讓您從遠端對這些裝置執行工作。

## <a name="get-to-your-devices"></a>移至您的裝置

1. 登入 [Microsoft 端點管理員系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。
3. 選取 [裝置]  。 此檢視會顯示有關個別裝置的詳細資訊，以及它們各有哪些功能，包括：

   - [概觀]  會顯示已註冊裝置的視覺化快照集，也會顯示有多少裝置使用不同的平台，包括 Android、iOS 等。
   - [所有裝置]  會顯示您所管理的已註冊裝置清單。

     使用 [匯出]  功能來建立所有裝置的 .csv 清單，增量單位為 10,000 (Internet Explorer) 或 30,000 (Microsoft Edge、Chrome)。

     選取任一裝置來[檢視有關該裝置的其他詳細資料](device-inventory.md)，包括硬體詳細資料、已安裝的應用程式、其合規性原則狀態等。

   - [Azure AD 裝置]  會顯示已向 Azure Active Directory (Azure AD) 註冊或已加入 Azure AD 的裝置清單。 深入了解 [Azure AD 裝置管理](https://docs.microsoft.com/azure/active-directory/device-management-introduction)。
   - [裝置動作]  包含在不同裝置上所執行遠端動作的歷程記錄，包括動作、其狀態、起始動作的人員及時間。

     ![監視裝置動作的螢幕擷取畫面](./media/device-management/monitor-device-actions.png)

   - [稽核記錄]  是在 Intune 中產生變更之活動的記錄。 [稽核記錄](../fundamentals/monitor-audit-logs.md) 可提供更多詳細資料。
   - [TeamViewer 連接器]  是一項服務，可讓 Intune 所管理 Android 裝置的使用者從其 IT 系統管理員處取得遠端協助。 深入了解 [TeamViewer](teamviewer-support.md)。
   - [說明及支援]  提供有關疑難排解提示、要求支援或檢查 Intune 的捷徑。

## <a name="available-device-actions"></a>可執行的裝置動作
可用的動作取決於裝置平台和裝置設定。

- [檢視裝置清查](device-inventory.md)
- 執行遠端裝置動作：
  - [淘汰](devices-wipe.md#retire)
  - [抹除](devices-wipe.md#wipe)
  - [遠端鎖定](device-remote-lock.md)
  - [重設密碼](device-passcode-reset.md)
  - [略過啟用鎖定](device-activation-lock-bypass.md) (僅限 iOS)
  - [全新開始](device-fresh-start.md) (僅限 Windows)
  - [遺失模式](device-lost-mode.md) (僅限 iOS)
  - [尋找裝置](device-locate.md) (僅限 iOS)
  - [重新啟動](device-restart.md) (僅限 Windows)
  - [重設 Windows 10 的 PIN 碼](device-windows-pin-reset.md)
  - [Android 遠端控制](teamviewer-support.md)
  - [同步裝置](device-sync.md)
  - [重新命名裝置](device-rename.md)
  - [傳送自訂通知](custom-notifications.md#send-a-custom-notification-to-a-single-device) (Android、iOS)
  - [BitLocker 金鑰輪替](../protect/encrypt-devices.md#rotate-bitlocker-recovery-keys) (僅限 Windows)

## <a name="next-steps"></a>後續步驟

- 在 [所有裝置]  中，選取裝置以檢視有關該特定裝置的更多詳細資料。
- 選擇 [裝置動作]  查看您管理的裝置上所執行動作的狀態。
